---
title: Anvisieren mit dem Kopf und mit den Augen in DirectX
description: Erfahren Sie, wie Sie Raycastingdaten aus dem Anverfolgen mit dem Kopf und der Blickverfolgung in nativen DirectX-Apps anfordern, verwenden und entpacken.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: Anvisiert mit den Augen, anvisierter Kopf, Blickverfolgung, Blickverfolgung, Directx, Eingabe, Hologramme, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 0e32c9f24b56d938b5c6f9cbdf28e9959b190abc22591a26d1dfcfa0af2f5f4d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193206"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>Eingabe zum Anvischen mit dem Kopf und Anvischen mit den Augen in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die nativen WinRT-Legacy-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API](openxr-getting-started.md)** empfohlen.

In Windows Mixed Reality wird die Eingabe des Anvischens mit den Augen und dem Kopf verwendet, um zu bestimmen, was der Benutzer ansieht. Sie können die Daten verwenden, um primäre Eingabemodelle wie [anviben mit dem Kopf und Commit](../../design/gaze-and-commit.md)zu steuern und Kontext für verschiedene Interaktionstypen bereitzustellen. Es gibt zwei Arten von Anvisierungsvektoren, die über die API verfügbar sind: Anvieren mit dem Kopf und Anvieren mit den Augen.  Beide werden als dreidimensionaler Strahl mit Ursprung und Richtung bereitgestellt. Anwendungen können dann raycast in ihre Szenen oder die reale Welt übertragen und bestimmen, was der Benutzer als Ziel verwendet.

**Das Anvischen** mit dem Kopf stellt die Richtung dar, in der der Kopf des Benutzers gezeigt wird. Stellen Sie sich das Anvischen mit dem Kopf als Position und Vorwärtsrichtung des Geräts selbst vor, wobei die Position als Mittelpunkt zwischen den beiden Anzeigen angezeigt wird. Das Anv mit dem Kopf ist auf allen Mixed Reality Geräten verfügbar.

**Das Anvieren** mit den Augen stellt die Richtung dar, in die die Augen des Benutzers blicken. Der Ursprung befindet sich zwischen den Augen des Benutzers.  Es ist auf Mixed Reality Geräten verfügbar, die ein Eyetrackingsystem enthalten.

Sowohl der Lichtstrahl des Kopf- als auch des Anvisierens mit den Augen ist über die  [SpatialPointerPose-API](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) zugänglich. Rufen Sie [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) auf, um ein neues SpatialPointerPose-Objekt zum angegebenen Zeitstempel und [Koordinatensystem](coordinate-systems-in-directx.md)zu empfangen. Dieses SpatialPointerPose enthält den Ursprung und die Richtung des Anvisierens mit dem Kopf. Sie enthält auch einen Ursprung und eine Richtung für das Anverfolgen mit den Augen, wenn eye tracking verfügbar ist.

### <a name="device-support"></a>Geräteunterstützung

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Feature</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
</tr>
<tr>
     <td>Anvisieren mit dem Kopf</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>Anväuten mit den Augen</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>Verwenden des Anvierens mit dem Kopf

Um auf das Anvisieren mit dem Kopf zuzugreifen, rufen Sie  [zunächst SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) auf, um ein neues SpatialPointerPose-Objekt zu empfangen. Übergeben Sie die folgenden Parameter.
 - Ein [SpatialCoordinateSystem, das](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) das Koordinatensystem darstellt, das Sie für das Anvieren mit dem Kopf benötigen. Dies wird durch die *variable coordinateSystem* im folgenden Code dargestellt. Weitere Informationen finden Sie in unserem [Entwicklerhandbuch für Koordinatensysteme.](coordinate-systems-in-directx.md)
 - Ein [Zeitstempel,](/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) der die genaue Zeit der angeforderten Kopfpose darstellt.  In der Regel verwenden Sie einen Zeitstempel, der der Uhrzeit entspricht, zu der der aktuelle Frame angezeigt wird. Sie können diesen vorhergesagten Anzeigezeitstempel aus einem  [HolographicFramePrediction-Objekt](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) abrufen, auf das über den aktuellen [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)zugegriffen werden kann.  Dieses HolographicFramePrediction-Objekt wird durch die *Vorhersagevariable* im folgenden Code dargestellt.

 Sobald Sie über ein gültiges SpatialPointerPose verfügen, sind die Kopfposition und die Vorwärtsrichtung als Eigenschaften zugänglich.  Der folgende Code zeigt, wie Sie darauf zugreifen.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>Verwenden des Anvierens mit den Augen

Damit Ihre Benutzer eine Eingabe mit den Augen verwenden können, muss jeder Benutzer bei der ersten Verwendung des Geräts eine [Eyetracking-Benutzer-Kalibrierung](/hololens/hololens-calibration) durchlaufen. Die API zum Anvcken mit den Augen ähnelt dem Anvimen mit dem Kopf.
Es verwendet dieselbe [SpatialPointerPose-API,](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) die einen Rayursprung und eine Richtung bereitstellt, die Sie für Ihre Szene raycasten können.  Der einzige Unterschied besteht darin, dass Sie die Eyetracking explizit aktivieren müssen, bevor Sie sie verwenden:
1. Fordern Sie die Benutzerberechtigung für die Verwendung von Eyetracking in Ihrer App an.
2. Aktivieren Sie die Funktion "Eingabe anv" in Ihrem Paketmanifest.

### <a name="requesting-access-to-eye-gaze-input"></a>Anfordern des Zugriffs auf die Eingabe mit den Augen

Wenn Ihre App gestartet wird, rufen Sie [EyePose::RequestAccessAsync](/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) auf, um Zugriff auf eye tracking anzufordern. Das System fordert den Benutzer bei Bedarf auf und gibt [GazeInputAccessStatus::Allowed](/uwp/api/windows.ui.input.gazeinputaccessstatus) zurück, sobald der Zugriff gewährt wurde. Dies ist ein asynchroner Aufruf, sodass eine zusätzliche Verwaltung erforderlich ist. Im folgenden Beispiel wird ein getrennter std::thread ausgelöst, um auf das Ergebnis zu warten, das in einer Membervariablen namens *m_isEyeTrackingEnabled* gespeichert wird.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
Das Starten eines getrennten Threads ist nur eine Option für die Verarbeitung asynchroner Aufrufe. Sie können auch die neue [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) Funktionalität verwenden, die von C++/WinRT unterstützt wird.
Im Folgenden finden Sie ein weiteres Beispiel für die Aufforderung zur Benutzerberechtigung:
-   Mit EyesPose::IsSupported() kann die Anwendung den Berechtigungsdialog nur auslösen, wenn ein Eyetracker vorhanden ist.
-   GazeInputAccessStatus m_gazeInputAccessStatus; Dies soll verhindern, dass die Berechtigungsaufforderung immer wieder angezeigt wird.

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a>Deklarieren der *Eingabefunktion "Anvieren"*

Doppelklicken Sie *in* Projektmappen-Explorer auf die Datei appxmanifest.  Navigieren Sie dann zum Abschnitt *Funktionen,* und überprüfen Sie die Funktion *"Eingabe anv anv".* 

![Eingabefunktion "Anv"](images/gaze-input-capability.png)

Dadurch werden dem Abschnitt *Package* in der Datei appxmanifest die folgenden Zeilen hinzugefügt:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Abrufen des Strahls mit den Augen

Sobald Sie Zugriff auf ET erhalten haben, können Sie jeden Frame mit den Augen anvieren.
Rufen Sie wie beim Anvisieren mit dem Kopf [das SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) ab, indem Sie [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit einem gewünschten Zeitstempel und Koordinatensystem aufrufen. SpatialPointerPose enthält über die Eigenschaft ["Eyes"](/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) ein [EyesPose-Objekt.](/uwp/api/windows.perception.people.eyespose) Dies ist nur dann ungleich NULL, wenn eye tracking aktiviert ist. Von dort aus können Sie überprüfen, ob der Benutzer auf dem Gerät über eine Eyetracking-Kalibrierung verfügt, indem Sie [EyePose::IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)aufrufen.  Verwenden Sie [](/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) als Nächstes die Gaze-Eigenschaft, um [spatialRay](/uwp/api/windows.perception.spatial.spatialray) abzurufen, das die Position und Richtung des Anverweises mit den Augen enthält. Die Gaze-Eigenschaft kann manchmal NULL sein. Überprüfen Sie daher, ob dies der Fall ist. Dies kann vorkommen, wenn ein kalibrierter Benutzer seine Augen vorübergehend schließt.

Der folgende Code zeigt, wie Sie auf den Strahl mit den Augen zugreifen.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a>Fallback, wenn eye tracking nicht verfügbar ist

Wie in unserer Dokumentation zum [Eyetrackingentwurf](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available)erwähnt, sollten Designer und Entwickler auf Fälle achten, in denen eye tracking-Daten möglicherweise nicht verfügbar sind.

Es gibt verschiedene Gründe dafür, dass Daten nicht verfügbar sind:
* Ein Benutzer, der nicht kalibriert wird
* Ein Benutzer hat der App den Zugriff auf seine Blickverfolgungsdaten verweigert.
* Temporäre Interferenzen, z. B. Wischgeschädigungen auf dem HoloLens Oder das Gesicht, das die Augen des Benutzers verdeckt. 

Einige der APIs wurden bereits in diesem Dokument erwähnt. Im Folgenden finden Sie eine Zusammenfassung, wie Sie erkennen können, dass eye tracking als Kurzübersicht verfügbar ist: 

* Überprüfen Sie, ob das System die Blickverfolgung überhaupt unterstützt. Rufen Sie die folgende *Methode* auf: [Windows. Perception.People.EyesPose.IsSupported()](/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* Überprüfen Sie, ob der Benutzer kalibriert ist. Rufen Sie die folgende *Eigenschaft* auf: [Windows. Perception.People.EyesPose.IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)   

* Überprüfen Sie, ob der Benutzer Ihrer App die Berechtigung zum Verwenden seiner Eyetrackingdaten erteilt hat: Rufen Sie den aktuellen _"GazeInputAccessStatus"_ ab. Ein Beispiel hierfür wird unter Anfordern des Zugriffs auf [anv Eingabe](/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)erläutert. 

Sie können auch überprüfen, ob Ihre Eyetrackingdaten nicht veraltet sind, indem Sie ein Timeout zwischen empfangenen Aktualisierungen der Eyetrackingdaten und andernfalls ein Fallback zum Anverfolgen mit dem Kopf hinzufügen, wie unten beschrieben.   
Weitere Informationen finden Sie in unseren Überlegungen zum [Fallbackentwurf.](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available)

<br>

## <a name="correlating-gaze-with-other-inputs"></a>Korrelieren des Anvierens mit anderen Eingaben

Manchmal stellen Sie fest, dass Sie ein [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) benötigen, das einem Ereignis in der Vergangenheit entspricht. Wenn der Benutzer z. B. einen Air Tap-Versuch macht, möchte Ihre App möglicherweise wissen, was er sich ansieht. Zu diesem Zweck wäre die einfache Verwendung von [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit der vorhergesagten Framezeit aufgrund der Latenz zwischen der Verarbeitung der Systemeingabe und der Anzeigezeit ungenau. Wenn sie das Anvisieren mit den Augen als Ziel verwenden, bewegen sich unsere Augen auch vor dem Abschließen einer Commitaktion weiter. Dies ist weniger ein Problem bei einem einfachen Tippen in die Luft, wird aber wichtiger, wenn lange Sprachbefehle mit schnellen Augenbewegungen kombiniert werden. Eine Möglichkeit, dieses Szenario zu behandeln, besteht darin, einen zusätzlichen Aufruf von  [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)mithilfe eines historischen Zeitstempels vorzunehmen, der dem Eingabeereignis entspricht.  

Für Eingaben, die den SpatialInteractionManager durchlaufen, gibt es jedoch eine einfachere Methode. [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) verfügt über eine eigene [TryGetAtTimestamp-Funktion.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) Der Aufruf von , der ein perfekt korreliertes [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) ohne das Erraten bereitstellt. Weitere Informationen zum Arbeiten mit SpatialInteractionSourceStates finden Sie in der Dokumentation [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) .

<br>

## <a name="calibration"></a>Kalibrierung

Damit die Blickverfolgung korrekt funktioniert, muss jeder Benutzer eine [Eyetracking-Benutzer-Kalibrierung](/hololens/hololens-calibration)durchlaufen. Dadurch kann das Gerät das System anpassen, um eine komfortablere und qualitativ hochwertigere Anzeige für den Benutzer zu gewährleisten und gleichzeitig eine genaue Blickverfolgung sicherzustellen. Entwickler müssen nichts am Ende tun, um die Benutzerkalibrierung zu verwalten. Das System stellt sicher, dass der Benutzer unter den folgenden Umständen aufgefordert wird, das Gerät zu kalibrieren:
* Der Benutzer verwendet das Gerät zum ersten Mal
* Der Benutzer hat sich zuvor von dem Kalibrierungsvorgang abgemeldet
* Der Kalibrierungsvorgang war bei der letzten Verwendung des Geräts durch den Benutzer nicht erfolgreich

Entwickler sollten sicherstellen, dass sie eine angemessene Unterstützung für Benutzer bereitstellen, bei denen Eyetrackingdaten möglicherweise nicht verfügbar sind. Weitere Informationen zu Überlegungen zu Fallbacklösungen finden Sie unter [Eyetracking auf HoloLens 2](../../design/eye-tracking.md).

<br>

## <a name="see-also"></a>Siehe auch

* [Kalibrierung](/hololens/hololens-calibration)
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md)
* [Anv mit den Augen HoloLens 2](../../design/eye-tracking.md)
* [Eingabemodell "Anvieren und Committen"](../../design/gaze-and-commit.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Spracheingabe in DirectX](voice-input-in-directx.md)