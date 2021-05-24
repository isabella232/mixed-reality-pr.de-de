---
title: Vom OpenXR-Plug-In unterstützte Features in Unity
description: Entdecken Sie die Features, die OpenXR für die Mixed Reality-Entwicklung in Unity unterstützt.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte
ms.openlocfilehash: e622cd617ccf67c0877b9064efe791743e4c34b6
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333372"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Mixed Reality von OpenXR unterstützte Features in Unity

Das **Mixed Reality OpenXR-Plug-In-Paket** ist eine Erweiterung des **OpenXR-Plug-Ins** von Unity und unterstützt eine Reihe von Features für HoloLens 2 und Windows Mixed Reality Headsets. Stellen Sie vor dem Fortfahren sicher, dass Ihr Unity-Projekt [für OpenXR konfiguriert ist.](openxr-getting-started.md)

## <a name="whats-supported"></a>Unterstützte Funktionen

Die folgenden Features werden derzeit unterstützt:

* Unterstützt UWP-Anwendungen für HoloLens 2 und optimiert für HoloLens 2 Anwendungsmodell.
* Unterstützt Win32 VR-Anwendungen für Windows Mixed Reality Headset mit aktuellen Controllerprofilen und holografischem App-Remoting.
* Weltweite Skalierungsnachverfolgung mit Ankern und ungebundenem Speicherplatz.
* [Ankerspeicher-API zum Beibehalten von Ankern](spatial-anchors-in-unity.md) HoloLens 2 lokalen Speichers.
* [Bewegungscontroller und Handinteraktionen,](#motion-controller-and-hand-interactions)einschließlich des neuen HP Reverb G2-Controllers.
* Artikulierte Handverfolgung mithilfe von 26 Eingaben für Fugen und Fugenradius.
* Interaktion mit dem Blick auf HoloLens 2.
* Suchen der Foto-/Videokamera (PV) HoloLens 2.
* Mixed Reality-Aufnahme 3rd eye rendering through PV camera (3. Augenrendering durch PV-Kamera).
* Unterstützt ["Play" für HoloLens 2 Holographic Remoting-App,](unity-play-mode.md#holographic-remoting-in-unity-editor-play-mode)sodass Entwickler Skripts debuggen können, ohne auf dem Gerät erstellen und bereitstellen zu müssen.
* Kompatibel mit MRTK Unity 2.5.3 und neuer über [die MRTK OpenXR-Anbieterunterstützung.](openxr-getting-started.md#using-mrtk-with-openxr-support)
* Kompatibel mit Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) oder höher.
* (Hinzugefügt in 0.1.3) Unterstützt [die Desktop-App Holographic Remoting](holographic-remoting-desktop.md) aus einer erstellten und bereitgestellten eigenständigen Windows-App.
* (Hinzugefügt in 0.1.4) Unterstützt qr code tracking on HoloLens2 through SpatialGraphNode (Unterstützung der [QR-Codenachverfolgung](#qr-codes) auf HoloLens2 über SpatialGraphNode)
* (Hinzugefügt in 0.2.0) Unterstützt **Anchor** in Holographic Remoting
* (Hinzugefügt in 0.2.0) Unterstützt sowohl Handverbindungen als auch **Handgitternetznachverfolgung**
* (Hinzugefügt in 0.2.0) Unterstützt **ARPlaneSubsystems** für die Ebenenerkennung und das Platzieren von Hologrammen mit **ARRaycastManager.**
* (0.9.0) Unterstützt **XRMeshSubsystem** und **ARMeshManager** für die räumliche Zuordnung.
* (Hinzugefügt in 0.9.0) Unterstützt das Azure Spatial Anchors SDK für Windows-Plug-In. Weitere Informationen finden Sie im [Azure Spatial Anchors-Beispielprojekt Mixed Reality + OpenXR auf GitHub.](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)
* (Hinzugefügt in 0.9.1) Unterstützt Holographic Remoting für Desktop-Apps aus einer erstellten und bereitgestellten Windows-UWP-App.
* (Hinzugefügt in 0.9.4) Unterstützt die ARM-Plattform zusätzlich zu ARM64 für HoloLens 2 Anwendung.

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

Die Von inputFeatureUsages **PointerPosition,** **PointerRotation,** **PointerVelocity** und **PointerAngularVelocity** bereitgestellten Posen stellen alle die OpenXR-Zielpose dar.  Diese InputFeatureUsages sind nicht in enthaltenen C#-Dateien definiert. Daher müssen Sie Ihre eigenen InputFeatureUsages wie folgt definieren:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptik

Informationen zur Verwendung von Haptik im XR-Eingabesystem von Unity finden Sie im [Unity-Handbuch für Unity XR Input – Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="qr-codes"></a>QR-Codes

HoloLens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der Position jedes Codes in der realen Welt einrichten. Weitere Informationen finden Sie in unserer Dokumentation zur [QR-Codeverfolgung.](../platform-capabilities-and-apis/qr-code-tracking.md)  Greifen Sie bei Verwendung des OpenXR-Plug-Ins [ `SpatialGraphNodeId` von der QR-API ab,](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) und verwenden Sie die `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API, um den QR-Code zu suchen.

Zu Referenzzwecken finden Sie auf GitHub ein Beispielprojekt für die [QR-Nachverfolgung](https://github.com/yl-msft/QRTracking) mit ausführlicheren Erläuterungen zur Verwendung der [ `SpatialGraphNode` API.](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie eine Unity-App auf HoloLens 2 anhalten und fortsetzen, kann die App nicht ordnungsgemäß fortgesetzt werden, was zu vier rotierenden Punkten in der HoloLens-Ansicht führt.

* Legen Sie den **Tiefenübermittlungsmodus** in den OpenXR-Projekteinstellungen als Problemumgehung auf **Keine** fest.
