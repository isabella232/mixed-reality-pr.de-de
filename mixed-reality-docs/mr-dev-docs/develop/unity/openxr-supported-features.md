---
title: Unterstützte Features des OpenXR-Plug-Ins in Unity
description: Entdecken Sie die Features, die OpenXR für die Mixed Reality-Entwicklung in Unity unterstützt.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality Headsets, Learn, Tutorial, Erste Schritte
ms.openlocfilehash: e6756df7f082e56b029b6e82e06d960ba39ed04a
ms.sourcegitcommit: aca5fddb98fbbd9aa22bdf8174d7fdcdb9d4c08a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2021
ms.locfileid: "107894000"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Mixed Reality von OpenXR unterstützte Features in Unity

Das **Mixed Reality OpenXR-Plug-In-Paket** ist eine Erweiterung des **OpenXR-Plug-Ins** von Unity und unterstützt eine Reihe von Features für HoloLens 2 und Windows Mixed Reality Headsets. Bevor Sie fortfahren, stellen Sie sicher, dass Ihr Unity-Projekt [für OpenXR konfiguriert](openxr-getting-started.md)ist.

## <a name="whats-supported"></a>Unterstützte Funktionen

Die folgenden Features werden derzeit unterstützt:

* Unterstützt UWP-Anwendungen für HoloLens 2 und optimiert für HoloLens 2 Anwendungsmodell.
* Unterstützt Win32 VR-Anwendungen für Windows Mixed Reality Headset mit aktuellen Controllerprofilen und Holographic App Remoting.
* World scale tracking using Anchors and Unbounded space (Weltskalierungsnachverfolgung mit Anchors und ungebundenem Speicherplatz).
* [Ankerspeicher-API zum Beibehalten](spatial-anchors-in-unity.md) von Ankern in HoloLens 2 lokalen Speicher.
* [Bewegungscontroller und Handinteraktionen,](#motion-controller-and-hand-interactions)einschließlich des neuen HP Reverb G2-Controllers.
* Artikulierte Handverfolgung mithilfe von 26 Fugen und Radiuseingaben.
* Interaktion mit dem Anv mit den Augen auf HoloLens 2.
* Suchen von Foto-/Videokameras (PV) auf HoloLens 2.
* Mixed Reality-Aufnahme mithilfe des Renderings des dritten Auges über die PV-Kamera.
* Unterstützt ["Play" zum HoloLens 2 mit der Holographic Remoting-App,](#holographic-remoting-in-unity-editor-play-mode)sodass Entwickler Skripts debuggen können, ohne auf dem Gerät zu erstellen und bereitzustellen.
* Kompatibel mit MRTK Unity 2.5.3 und neuer über [MRTK OpenXR-Anbieterunterstützung.](openxr-getting-started.md#using-mrtk-with-openxr-support)
* Kompatibel mit Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) oder höher.
* (Hinzugefügt in 0.1.3) Unterstützt [Holographic Remoting für Desktop-Apps](holographic-remoting-desktop.md) aus einer erstellten und bereitgestellten eigenständigen Windows-App.
* (Hinzugefügt in 0.1.4) Unterstützt [die QR-Codenachverfolgung](#qr-codes) auf HoloLens2 über SpatialGraphNode.
* (Hinzugefügt in 0.2.0) Unterstützt **Anker** in Holographic Remoting
* (Hinzugefügt in 0.2.0) Unterstützt sowohl **Hand- als auch Handgitternachverfolgung.**
* (Hinzugefügt in 0.2.0) Unterstützt **ARPlaneSubsystems** für die Erkennung von Ebenen und das Platzieren von Hologrammen **mithilfe von ARRaycastManager.**
* (0.9.0) Unterstützt **XRMeshSubsystem** und **ARMeshManager** für die räumliche Zuordnung.
* (Hinzugefügt in 0.9.0) Unterstützt das Azure Spatial Anchors SDK für Windows-Plug-In. Weitere Informationen finden Sie im Mixed Reality [+ OpenXR Azure Spatial Anchors-Beispielprojekt auf GitHub.](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)
* (Hinzugefügt in 0.9.1) Unterstützt die Desktop-App Holographic Remoting aus einer erstellten und bereitgestellten Windows-UWP-App.

## <a name="holographic-remoting-setup"></a>Holographic Remoting-Setup

1. Zunächst müssen Sie die [Holographic Remoting Player-App](https://www.microsoft.com/store/productId/9NBLGGH4SV40) aus dem Microsoft Store auf Ihrem Computer HoloLens 2
2. Führen Sie die Holographic Remoting Player-App auf HoloLens 2, und Die Versionsnummer und die IP-Adresse für die Verbindung werden angezeigt.
    * Sie benötigen Version 2.4 oder höher, um mit dem OpenXR-Plug-In arbeiten zu können.

    ![Screenshot des Holographic Remoting-Players, der in HoloLens ausgeführt wird](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic Remoting im Wiedergabemodus des Unity-Editors

Das Erstellen eines UWP-Unity Visual Studio projekts und das anschließende Packen und Bereitstellen auf einem HoloLens 2 gerät kann einige Zeit dauern. Eine Lösung besteht in der Aktivierung des Holographic Editor-Remotingfeatures, mit dem Sie Ihr C#-Skript mithilfe des Modus "Play" direkt auf ein HoloLens 2 Gerät über Ihr Netzwerk debuggen können. Dieses Szenario vermeidet den Mehraufwand für das Erstellen und Bereitstellen eines UWP-Pakets auf einem Remotegerät.

1. Führen Sie die Schritte unter [Holographic Remoting setup (Holographic Remoting-Setup) aus.](#holographic-remoting-setup)
2. Öffnen **Sie Bearbeiten -> Projekteinstellungen,** navigieren Sie zu **XR-Plug-In-Verwaltung,** und aktivieren Sie das Windows Mixed Reality **Featuresatz:**

    ![Screenshot des Im Unity-Editor geöffneten Fensters "Projekteinstellungen" mit hervorgehobener XR-Plug-In-Verwaltung](images/openxr-features-img-02.png)

3. Erweitern Sie den Abschnitt **Features** unter **OpenXR,** und wählen Sie **Alle anzeigen** aus.
4. Aktivieren Sie das **Kontrollkästchen Holographic Editor Remoting,** und geben Sie die IP-Adresse ein, die Sie aus der Holographic Remoting-App erhalten:

    ![Screenshot des im Unity-Editor geöffneten Bereichs "Projekteinstellungen" mit hervorgehobenen Features](images/openxr-features-img-03.png)

Jetzt können Sie auf die Schaltfläche "Wiedergabe" klicken, um Ihre Unity-App in der Holographic Remoting-App auf Ihrer HoloLens wiederzugeben. Sie können auch [Visual Studio an Unity anfügen,](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) um C#-Skripts im Wiedergabemodus zu debuggen.

> [!NOTE]
> Ab Version 0.1.0 unterstützt die Holographic Remoting-Runtime Anchors nicht mehr, und ARAnchorManager-Funktionen funktionieren nicht über Remoting.  Dieses Feature wird in zukünftigen Versionen veröffentlicht.

## <a name="motion-controller-and-hand-interactions"></a>Bewegungscontroller und Handinteraktionen

Informationen zu den Grundlagen zu Mixed Reality-Interaktionen in Unity finden Sie im [Unity-Handbuch für Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). In dieser Unity-Dokumentation werden die Zuordnungen von controllerspezifischen Eingaben zu **generalisierbareren InputFeatureUsage-Funktionen,** die Identifizierung und Kategorisierung verfügbarer XR-Eingaben, das Lesen von Daten aus diesen Eingaben und vieles mehr behandelt.

Das Mixed Reality OpenXR-Plug-In stellt zusätzliche Eingabeinteraktionsprofile bereit, die **standardmäßigen InputFeatureUsage-Funktionen** zugeordnet sind, wie unten beschrieben:

| InputFeatureUsage | HP Reverb G2 Controller (OpenXR) | HoloLens Hand (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Schalter : Klicken Sie auf | |
| Trigger (trigger) | Trigger  | |
| Griff | Griff | Tippen in die Luft oder Anzippen |
| primaryButton | [X/A] – Drücken | In die Luft tippen |
| secondaryButton | [Y/B] – Drücken Sie | |
| gripButton | Greifer – Drücken | |
| triggerButton | Trigger – Drücken | |
| menuButton | Menü | |

### <a name="aim-and-grip-poses"></a>Ziel- und Greif-Posen

Sie haben über OpenXR-Eingabeinteraktionen Zugriff auf zwei Sätze von Posen:

* Der Greif stellt zum Rendern von Objekten in der Hand dar.
* Das Ziel ist es, auf die Welt zu zeigen.

Weitere Informationen zu diesem Entwurf und den Unterschieden zwischen den beiden Posen finden Sie unter [OpenXR Specification - Input Subpaths ( OpenXR-Spezifikation : Eingabeunterpfade](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)).

Von inputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** und **DeviceAngularVelocity** bereitgestellte Posen stellen alle die OpenXR-Greifposition dar.  InputFeatureUsages im Zusammenhang mit Greifposen sind in [CommonUsages von](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity definiert.

Die Von inputFeatureUsages **PointerPosition,** **PointerRotation,** **PointerVelocity** und **PointerAngularVelocity** bereitgestellten Posen stellen alle die OpenXR-Zielpose dar.  Diese InputFeatureUsages sind in eingeschlossenen C#-Dateien nicht definiert, daher müssen Sie Ihre eigenen InputFeatureUsages wie folgt definieren:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptik

Informationen zur Verwendung von Haptik im XR-Eingabesystem von Unity finden Sie im [Unity-Handbuch für Unity XR Input – Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="qr-codes"></a>QR-Codes

HoloLens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der Position jedes Codes in der realen Welt einrichten. Weitere Informationen finden Sie in unserer Dokumentation zur [QR-Codeverfolgung.](../platform-capabilities-and-apis/qr-code-tracking.md)  Greifen Sie bei Verwendung des OpenXR-Plug-Ins [ `SpatialGraphNodeId` von der QR-API ab,](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) und verwenden Sie die `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API, um den QR-Code zu suchen.

Zu Referenzzwecken finden Sie auf GitHub ein Beispielprojekt für die [QR-Nachverfolgung](https://github.com/yl-msft/QRTracking) mit ausführlicheren Erläuterungen zur Verwendung der [ `SpatialGraphNode` API.](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)

## <a name="whats-coming-soon"></a>Was ist in Kürze verfügbar?

Die folgenden Probleme und fehlenden Features sind mit Mixed Reality OpenXR-Plug-In **Version 0.9.2** bekannt. Wir arbeiten daran und werden fixes und neue Features in zukünftigen Releases veröffentlichen.

* **ARM64** ist die einzige unterstützte Plattform für HoloLens 2-Apps. Die **ARM-Plattform** wird in einem zukünftigen Release veröffentlicht.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie eine Unity-App auf HoloLens 2 anhalten und fortsetzen, kann die App nicht ordnungsgemäß fortgesetzt werden, was zu vier rotierenden Punkten in der HoloLens-Ansicht führt.

* Legen Sie den **Tiefenübermittlungsmodus** in den OpenXR-Projekteinstellungen als Problemumgehung auf **Keine** fest.
