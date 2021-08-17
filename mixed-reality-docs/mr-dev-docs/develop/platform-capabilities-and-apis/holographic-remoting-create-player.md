---
title: Schreiben eines benutzerdefinierten Holographic Remoting-Players (C++)
description: Erstellen Sie eine benutzerdefinierte Hologaphic Remoting-App, um inhalte, die auf einem Remotecomputer gerendert wurden, auf Ihrem Computer HoloLens 2.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 7/30/2021
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, NuGet, App-Manifest, Playerkontext, Remote-App, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 37388dc9cbf70cb7fccd742fb45e1e29c0ceb971
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184731"
---
# <a name="writing-a-custom-holographic-remoting-player-app-c"></a>Schreiben einer benutzerdefinierten Holographic Remoting-Player-App (C++)

>[!IMPORTANT]
>In diesem Dokument wird die Erstellung einer benutzerdefinierten Playeranwendung für HoloLens 2. Benutzerdefinierte Player, die für HoloLens 2 sind nicht kompatibel mit Remoteanwendungen, die für HoloLens 1 geschrieben wurden. Dies impliziert, dass beide Anwendungen NuGet Paketversion **2.x.x verwenden müssen.**

Indem Sie eine benutzerdefinierte Holographic Remoting-Player-App erstellen, [](../../design/app-views.md) können Sie eine benutzerdefinierte Anwendung erstellen, die immersive Ansichten von auf einem Remotecomputer auf Ihrem Computer HoloLens 2. Den ganzen Code auf dieser Seite und funktionierende Projekte finden Sie im [GitHub-Repository Holographic Remoting samples (Holographic Remoting-Beispiele).](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)

Mit einem Holographic Remoting-Player kann [](rendering.md) Ihre App holografische Inhalte anzeigen, die auf einem Desktop-PC oder UWP-Gerät wie dem Xbox One mit Zugriff auf weitere Systemressourcen gerendert werden. Eine Holographic Remoting-Player-App streamt Eingabedaten an eine Holographic Remoting-Remoteanwendung und empfängt eine immersive Ansicht als Video- und Audiostream zurück. Die Verbindung wird mithilfe von STANDARD-WLAN hergestellt. Um eine Player-App zu erstellen, verwenden Sie ein NuGet, um Holographic Remoting Ihrer UWP-App hinzuzufügen. Schreiben Sie dann Code, um die Verbindung zu verarbeiten und eine immersive Ansicht anzuzeigen. 

## <a name="prerequisites"></a>Voraussetzungen

Ein guter Ausgangspunkt ist eine funktionierende DirectX-basierte UWP-App, die bereits auf die Windows Mixed Reality-API zielt. Weitere Informationen finden Sie unter [Übersicht über die DirectX-Entwicklung.](../native/directx-development-overview.md) Wenn Sie über keine vorhandene App verfügen und von Grund auf neu beginnen möchten, ist die [holografische C++-Projektvorlage](../native/creating-a-holographic-directx-project.md) ein guter Ausgangspunkt.

>[!IMPORTANT]
>Jede App, die Holographic Remoting verwendet, sollte für die Verwendung eines [Multithread-Apartments erstellen.](/windows/win32/com/multithreaded-apartments) Die Verwendung eines [Singlethread-Apartment](/windows/win32/com/single-threaded-apartments) wird unterstützt, führt jedoch zu einer suboptimaler Leistung und möglicherweise zu Einembruch während der Wiedergabe. Bei Verwendung von C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) ist ein Multithread-Apartment die Standardeinstellung.

## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic Remoting-Paket NuGet

Die folgenden Schritte sind erforderlich, um das paket NuGet einem Projekt in Visual Studio.
1. Öffnen Sie das Projekt in Visual Studio.
2. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen **Sie manage NuGet Packages... (Pakete verwalten) aus.**
3. Wählen Sie im angezeigten Bereich **Durchsuchen** aus, und suchen Sie dann nach "Holographic Remoting".
4. Wählen **Sie Microsoft.Holographic.Remoting** aus, stellen Sie sicher, dass Sie die neueste **Version von 2.x.x auswählen,** und wählen Sie **Installieren aus.**
5. Wenn das **Dialogfeld Vorschau** angezeigt wird, wählen Sie **OK aus.**
6. Wählen Sie **Ich stimme zu** aus, wenn das Dialogfeld lizenzvertrag angezeigt wird.

>[!IMPORTANT]
><a name="idl"></a>Das ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` -Paket im NuGet enthält eine ausführliche Dokumentation für die API, die von Holographic Remoting verfügbar gemacht wird.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Ändern des Package.appxmanifest der Anwendung

Um die Anwendung über die vom Microsoft.Holographic.AppRemoting.dll-Paket NuGet, müssen die folgenden Schritte für das Projekt erforderlich sein:

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die **Datei Package.appxmanifest,** und wählen Sie **Öffnen mit... aus.**
2. Wählen Sie **XML-Editor (Text) und** dann **OK aus.**
3. Fügen Sie der Datei die folgenden Zeilen hinzu, und speichern Sie sie.
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>Erstellen des Playerkontexts

Im ersten Schritt sollte die Anwendung einen Playerkontext erstellen.

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>Holographic Remoting funktioniert, indem die Windows Mixed Reality-Runtime, die Teil von Windows ist, durch eine Remoting-spezifische Laufzeit ersetzt wird. Dies erfolgt während der Erstellung des Playerkontexts. Aus diesem Grund kann jeder Aufruf einer beliebigen Windows Mixed Reality-API vor dem Erstellen des Playerkontexts zu unerwartetem Verhalten führen. Es wird empfohlen, den Playerkontext so früh wie möglich zu erstellen, bevor sie mit einer beliebigen Mixed Reality werden. Kombinieren Sie objekte, die vor dem Aufruf von über eine Windows Mixed Reality-API erstellt oder abgerufen wurden, niemals mit Objekten, die ```PlayerContext::Create``` anschließend erstellt oder abgerufen wurden.

Als Nächstes kann HolographicSpace durch Aufrufen von [HolographicSpace.CreateForCoreWindow erstellt werden.](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>Verbinden zur Remote-App

Sobald die Player-App zum Rendern von Inhalten bereit ist, kann eine Verbindung mit der Remote-App hergestellt werden.

Die Verbindung kann auf eine der folgenden Arten hergestellt werden:
1) Die Player-App, die auf HoloLens 2 mit der Remote-App verbindet.
2) Die Remote-App stellt eine Verbindung mit der Player-App auf dem HoloLens 2.

Um eine Verbindung zwischen der Player-App und der Remote-App herzustellen, rufen Sie die -Methode im Playerkontext unter Angabe ```Connect``` des Hostnamens und Ports auf. Der Standardport ist **8265.**

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>Wie bei jeder C++/WinRT-API ```Connect``` kann eine winrt::hresult_error auslösen, die behandelt werden muss.

Das Lauschen auf eingehende Verbindungen in der Player-App kann durch Aufrufen der -Methode ```Listen``` erfolgen. Sowohl der Handshakeport als auch der Transportport können während dieses Aufrufs angegeben werden. Der Handshakeport wird für den ersten Handshake verwendet. Die Daten werden dann über den Transportport gesendet. Standardmäßig werden die **Portnummer 8265** und **8266** verwendet.

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>Behandeln von verbindungsbezogenen Ereignissen

Macht ```PlayerContext``` drei Ereignisse verfügbar, um den Zustand der Verbindung zu überwachen.
1) OnConnected: Wird ausgelöst, wenn erfolgreich eine Verbindung mit der Remote-App hergestellt wurde.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected: Wird ausgelöst, wenn eine hergestellte Verbindung beendet wird oder keine Verbindung hergestellt werden konnte.
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>Mögliche ```ConnectionFailureReason``` Werte sind in der Datei ```Microsoft.Holographic.AppRemoting.idl``` [dokumentiert.](#idl)

3) OnListening: Beim Lauschen auf eingehende Verbindungen wird gestartet.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Darüber hinaus kann der Verbindungsstatus mithilfe der ```ConnectionState``` -Eigenschaft im Playerkontext abgefragt werden.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Anzeigen des remote gerenderten Frames

Um den remote gerenderten Inhalt anzuzeigen, rufen Sie auf, ```PlayerContext::BlitRemoteFrame``` während Ein [HolographicFrame gerendert wird.](/uwp/api/windows.graphics.holographic.holographicframe) 

```BlitRemoteFrame``` erfordert, dass der Hintergrundpuffer für den aktuellen HolographicFrame als Renderziel gebunden ist. Der Hintergrundpuffer kann von [holographicCameraRenderingParameters über](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) die [Direct3D11BackBuffer-Eigenschaft empfangen](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) werden.

Kopiert beim ```BlitRemoteFrame``` Aufgerufenen den zuletzt empfangenen Frame aus der Remoteanwendung in den BackBuffer des HolographicFrame. Darüber hinaus wird der Fokuspunktsatz festgelegt, wenn die Remoteanwendung während des Renderns des Remoteframes einen Fokuspunkt angegeben hat.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` überschreibt möglicherweise den Fokuspunkt für den aktuellen Frame. 
>- Um einen Fallbackfokuspunkt anzugeben, rufen [Sie HolographicCameraRenderingParameters::SetFocusPoint vor](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` auf. 
>- Um den Remotefokuspunkt zu überschreiben, rufen [Sie HolographicCameraRenderingParameters::SetFocusPoint nach](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` auf.

Bei Erfolg gibt ```BlitRemoteFrame``` ```BlitResult::Success_Color``` zurück. Andernfalls wird die Fehlergrund zurückgegeben:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: Fehler, da kein Remoteframe verfügbar ist.
- ```BlitResult::Failed_NoCamera```: Fehler, da keine Kamera vorhanden ist.
- ```BlitResult::Failed_RemoteFrameTooOld```: Fehler, weil der Remoteframe zu alt ist (siehe PlayerContext::BlitRemoteFrameTimeout-Eigenschaft).

>[!IMPORTANT]
> Ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0) ist es mit einem benutzerdefinierten Player möglich, die Tiefenumprojektion über Holographic Remoting zu verwenden.

```BlitResult``` kann auch ```BlitResult::Success_Color_Depth``` unter den folgenden Bedingungen zurückgeben:

- Die Remote-App hat über [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer einen Tiefenpuffer gebunden.](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
- Die benutzerdefinierte Player-App hat vor dem Aufruf von einen gültigen Tiefenpuffer ```BlitRemoteFrame``` gebunden.

Wenn diese Bedingungen erfüllt sind, wird die Remotetiefe in den aktuell gebundenen ```BlitRemoteFrame``` lokalen Tiefenpuffer eingelitt. Anschließend können Sie zusätzliche lokale Inhalte rendern, die eine Tiefenschnittmenge mit dem remote gerenderten Inhalt haben. Darüber hinaus können Sie den lokalen Tiefenpuffer über [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) in Ihrem benutzerdefinierten Player commiten, um eine Tiefenreprojektion für remote und lokal gerenderten Inhalt zu erhalten. Weitere [Informationen finden Sie unter Depth Reprojection](hologram-stability.md#reprojection) (Tiefenprojektion).

### <a name="projection-transform-mode"></a>Projektionstransformationsmodus

Ein Problem, das bei verwendung der Tiefenumwandlung über Holographic Remoting auftrat, ist, dass der Remoteinhalt mit einer anderen Projektionstransformation gerendert werden kann als lokaler Inhalt, der direkt von Ihrer benutzerdefinierten Player-App gerendert wird. Ein häufiger Verwendungsfall ist die Angabe verschiedener Werte für die nah- und ferne Ebene (über [HolographicCamera::SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) und [HolographicCamera::SetFarPlaneDistance)](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)auf Spieler- und Remoteseite. In diesem Fall ist nicht klar, ob die Projektionstransformation auf spielerseitiger Seite die Entfernungen der remoten Nah-/Fernebene oder die lokalen Abstände widerspiegeln soll.

Ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0) können Sie den Projektionstransformationsmodus über ```PlayerContext::ProjectionTransformConfig``` steuern. Diese Werte werden unterstützt:

- ```Local``` - [HolographicCameraPose::P rojectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) gibt eine Projektionstransformation zurück, die die von Ihrer benutzerdefinierten Player-App auf der HolographicCamera festgelegten Entfernungen in der Nah-/Fernebene widerspiegelt.
- ```Remote``` – Projektionstransformation spiegelt die von der Remote-App angegebenen Entfernungen in der Nah-/Fernebene wider.
- ```Merged``` – Entfernungen der Nah-/Fernebene von Ihrer Remote-App und Ihrer benutzerdefinierten Player-App werden zusammengeführt. Dies erfolgt standardmäßig, indem der Mindestwert der Entfernungen in der Näherungsebene und der höchstwert der Entfernungen der Fernebene verwendet wird. Für den Fall, dass entweder die Remoteseite oder die lokale Seite invertiert wird, z. B. weit <, werden die Entfernungen der remoten nah/fernen Ebene gekippt.

## <a name="optional-set-blitremoteframetimeout"></a>Optional: Legen Sie BlitRemoteFrameTimeout fest. <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout```wird ab Version [2.0.9 unterstützt.](holographic-remoting-version-history.md#v2.0.9) 

Die -Eigenschaft gibt an, wie lange ein ```PlayerContext::BlitRemoteFrameTimeout``` Remoteframe wiederverwendet wird, wenn kein neuer Remoteframe empfangen wird. 

Ein häufiger Verwendungsfall besteht im Aktivieren des BlitRemoteFrame-Timeouts, um einen leeren Bildschirm anzuzeigen, wenn für einen bestimmten Zeitraum keine neuen Frames empfangen werden. Wenn diese Option aktiviert ist, kann der Rückgabetyp der Methode auch verwendet werden, um zu einem lokal gerenderten ```BlitRemoteFrame``` Fallbackinhalt zu wechseln. 

Um das Timeout zu aktivieren, legen Sie den Eigenschaftswert auf eine Dauer von mehr als 100 ms fest. Um das Timeout zu deaktivieren, legen Sie die -Eigenschaft auf 0 duration fest. Wenn das Timeout aktiviert ist und während der festgelegten Dauer kein Remoteframe empfangen wird, kann BlitRemoteFrame nicht verwendet werden, und es wird eine Rückgabe angezeigt, bis ein neuer Remoteframe ```Failed_RemoteFrameTooOld``` empfangen wird.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Optional: Statistik zum letzten Remoteframe

Zum Diagnostizieren von Leistungs- oder Netzwerkproblemen können Statistiken zum letzten Remoteframe über die -Eigenschaft abgerufen ```PlayerContext::LastFrameStatistics``` werden. Statistiken werden während des Aufrufs von [HolographicFrame::P resentUsingCurrentPrediction aktualisiert.](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Weitere Informationen finden Sie in der ```PlayerFrameStatistics``` Dokumentation in der ```Microsoft.Holographic.AppRemoting.idl``` [Datei](#idl).

## <a name="optional-custom-data-channels"></a>Optional: Benutzerdefinierte Datenkanäle

Benutzerdefinierte Datenkanäle können verwendet werden, um Benutzerdaten über die bereits eingerichtete Remotingverbindung zu senden. Weitere [Informationen finden Sie unter Benutzerdefinierte](holographic-remoting-custom-data-channels.md) Datenkanäle.

## <a name="see-also"></a>Weitere Informationen
* [Übersicht über Holographic Remoting](holographic-remoting-overview.md)
* [Schreiben einer Holographic Remoting-Remote-App mit Windows Mixed Reality APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs](holographic-remoting-create-remote-openxr.md)
* [Benutzerdefinierte Holographic Remoting-Datenkanäle](holographic-remoting-custom-data-channels.md)
* [Einrichten einer sicheren Verbindung mit Holographic Remoting](holographic-remoting-secure-connection.md)
* [Problembehandlung und Einschränkungen bei Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)