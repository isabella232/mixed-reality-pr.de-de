---
title: Von openxr-Plug-in unterstützte Funktionen in Unity
description: Entdecken Sie die Features, die openxr für die Entwicklung gemischter Realität in Unity unterstützt.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, Mixed Reality, mrtk, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, erlernen, Tutorial, Getting Started
ms.openlocfilehash: 1fbc03fe446d9e9619348618c6d0b9aab828fe1a
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105937426"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Gemischte Funktionen von openxr unterstützten Funktionen in Unity

Das **gemischte openxr-Plug** -in für die Realität ist eine Erweiterung des Unity **openxr-Plug** -ins und unterstützt eine Reihe von Features für hololens 2-und Windows Mixed Reality-Headsets. Bevor Sie fortfahren, stellen Sie sicher, dass Ihr Unity-Projekt [für openxr konfiguriert](openxr-getting-started.md)ist.

## <a name="whats-supported"></a>Unterstützte Funktionen

Die folgenden Funktionen werden derzeit unterstützt:

* Unterstützt UWP-Anwendungen für hololens 2 und optimiert für das hololens 2-Anwendungsmodell.
* Unterstützt Win32-VR-Anwendungen für Windows Mixed Reality-Headset mit den neuesten Controller Profilen und Holographic App-Remoting.
* Welt weite Nachverfolgung mithilfe von Ankern und unbeschränktes Raum.
* [Anker-Speicher-API zum Beibehalten von Ankern](spatial-anchors-in-unity.md) an hololens 2 lokalen Speicher.
* [Motion Controller und Hand Interaktionen](#motion-controller-and-hand-interactions), einschließlich des neuen HP-Reverb-G2-Controllers.
* Handgelenk Verfolgung mithilfe von 26 Gelenken und gemeinsamen RADIUS-Eingaben.
* Interaktion mit Blick auf hololens 2.
* Auffinden von Foto/Video-Kamera (PV) auf hololens 2.
* Transformation für gemischte Realität mithilfe von Dritt-Rendering durch PV-Kamera.
* Unterstützt ["Play" in hololens 2 mit der Holographic Remoting-App](#holographic-remoting-in-unity-editor-play-mode), sodass Entwickler Skripts debuggen können, ohne auf dem Gerät zu entwickeln und bereitzustellen.
* Kompatibel mit mrtk Unity 2.5.3 und neuer über die [Unterstützung von mrtk openxr-Anbietern](openxr-getting-started.md#using-mrtk-with-openxr-support).
* Kompatibel mit Unity [arfoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) oder höher.
* (In 0.1.3 hinzugefügt) Unterstützt die [Desktop-App Holographic Remoting](holographic-remoting-desktop.md) aus einer erstellten und bereitgestellten eigenständigen Windows-app.
* (In 0.1.4 hinzugefügt) Unterstützt die [QR-Code Überwachung](#qr-codes) auf HoloLens2 über spatialgraphnode
* (In 0.2.0 hinzugefügt) Unterstützt **Anker** in Holographic Remoting
* (In 0.2.0 hinzugefügt) Unterstützt sowohl **Handgelenke als auch Hand Gitter Verfolgung**
* (In 0.2.0 hinzugefügt) Unterstützt **arplanesubsystems** für die Ebenenerkennung und das Platzieren von – Hologramm mithilfe von **arraycastmanager**.

## <a name="holographic-remoting-setup"></a>Holographic Remoting-Setup

1. Zunächst müssen Sie [die Holographic Remoting Player-App](https://www.microsoft.com/store/productId/9NBLGGH4SV40) aus dem Microsoft Store auf den hololens 2 installieren.
2. Führen Sie die Holographic Remoting Player-App auf hololens 2 aus, und Sie sehen die Versionsnummer und IP-Adresse, mit der Sie eine Verbindung herstellen.
    * Sie benötigen v 2.4 oder höher, um mit dem openxr-Plug-in zu arbeiten.

    ![Screenshot des Holographic-Remoting-Players, der in den hololens ausgeführt wird](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic-Remoting im Unity-Editor-Wiedergabemodus

Das Erstellen eines UWP Unity-Projekts in Visual Studio Project und das anschließende Verpacken und Bereitstellen des Projekts auf einem hololens 2-Gerät kann einige Zeit in Anspruch nehmen. Eine Lösung besteht darin, das Feature "Holographic Editor Remoting" zu aktivieren, mit dem Sie Ihr c#-Skript mit dem Modus "wiedergeben" direkt auf ein hololens 2-Gerät über Ihr Netzwerk Debuggen können. In diesem Szenario wird der Aufwand für das entwickeln und Bereitstellen eines UWP-Pakets auf dem Remote Gerät vermieden.

1. Befolgen Sie die Schritte in [Holographic Remoting-Setup](#holographic-remoting-setup) .
2. Öffnen Sie die **Projekteinstellungen für die > bearbeiten**, navigieren Sie zu der **XR-Plug-in-Verwaltung**, und aktivieren Sie das Kontrollkästchen **Windows Mixed Reality Feature Set** :

    ![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-in-Verwaltung](images/openxr-features-img-02.png)

3. Erweitern Sie unter **openxr** den Abschnitt **Features** , und wählen Sie **Alle anzeigen** aus.
4. Aktivieren Sie das Kontrollkästchen "Remoting" für das **Holographic Editor** , und geben Sie die IP-Adresse ein, die Sie aus der Holographic Remoting

    ![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit hervorgehobenen Features](images/openxr-features-img-03.png)

Nun können Sie auf die Schaltfläche "Wiedergabe" klicken, um Ihre Unity-app in der Holographic Remoting-App auf Ihren hololens wiederzugeben. Sie können auch [Visual Studio an Unity anfügen](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) , um c#-Skripts im Wiedergabemodus zu debuggen.

> [!NOTE]
> Ab Version 0.1.0 unterstützt die Holographic Remoting Runtime keine Anker, und aranchormanager-Funktionen können nicht durch Remoting verwendet werden.  Diese Funktion wird in zukünftigen Versionen veröffentlicht.

## <a name="motion-controller-and-hand-interactions"></a>Bewegungs Controller und Hand Interaktionen

Informationen zu den Grundlagen von Mixed Reality-Interaktionen in Unity finden Sie in der [Unity-Anleitung für](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)Unity. In dieser Unity-Dokumentation werden die Zuordnungen von Controller spezifischen Eingaben zu stärker verallgemeinerbaren **inputfeatureusage** s behandelt, und es wird erläutert, wie verfügbare XR-Eingaben identifiziert und kategorisiert werden können, wie Daten aus diesen Eingaben gelesen werden und vieles mehr.

Das Mixed Reality openxr-Plug-in bietet zusätzliche Eingabe Interaktions Profile, die Standard **inputfeatureusage** s zugeordnet sind, wie im folgenden beschrieben:

| Input featureusage | HP-Reverb-G2-Controller (openxr) | Hololens-Hand (openxr) |
| ---- | ---- | ---- |
| primary2DAxis | Steuern | |
| primary2DAxisClick | Joystick Klick | |
| Trigger (trigger) | Trigger  | |
| Hand | Hand | Luft tippen oder drücken |
| primarybutton | [X/A]-drücken | In die Luft tippen |
| secondarybutton | [J/B]-drücken | |
| gripbutton | Ziehpunkt-drücken | |
| Triggerbutton | Auslösung: Drücken Sie | |
| -menubutton- | Menü | |

### <a name="aim-and-grip-poses"></a>Ziele und Zieh Punkt

Sie haben Zugriff auf zwei Gruppen von Posen durch openxr-Eingabe Interaktionen:

* Der Ziehpunkt für das Rendern von Objekten in der Hand.
* Das Ziel für den Verweis auf die Welt.

Weitere Informationen zu diesem Entwurf und den Unterschieden zwischen den beiden Posen finden Sie in den [unter Pfaden für openxr Specification-Input](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Die von den inputfeatureages **deviceposition**, **devicerotations**, **de vicevelocity** und **deviceangularvelocity** bereitgestellten Posen stellen die openxr-Zieh Punkt **Darstellung dar.** Inputfeatureverwendungen im Zusammenhang mit Ziehpunkt-Posen werden in Unity- [Common-Ages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)definiert.

Die von der Eingabe **Funktion "pointerposition**", " **pointerrotation**", " **pointervelocity**" und " **pointerangularvelocity** " bereitgestellten Posen stellen das openxr- **Ziel** dar. Diese inputfeatureusages sind nicht in enthaltenen c#-Dateien definiert, daher müssen Sie Ihre eigene inputfeatureusages wie folgt definieren:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptik

Informationen zur Verwendung von Haptik im XR-Eingabe System von Unity finden Sie im [Unity-Handbuch für Unity-Eingabe-und-Haptik](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="qr-codes"></a>QR-Codes

HoloLens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der Position jedes Codes in der realen Welt einrichten. Weitere Informationen finden Sie in der Dokumentation zur [QR-Code](../platform-capabilities-and-apis/qr-code-tracking.md) -Nachverfolgung.  Wenn Sie das openxr-Plug-in verwenden, rufen Sie den [ `SpatialGraphNodeId` von der QR-API ab](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) , und verwenden `Microsoft.MixedReality.OpenXR.SpatialGraphNode` Sie die API zum Suchen des QR-Codes

Als Referenz haben wir ein [Beispiel Projekt für QR-Nachverfolgung auf GitHub](https://github.com/yl-msft/QRTracking) mit einer ausführlicheren Verwendungs Erklärung für die [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="whats-coming-soon"></a>Bald verfügbar

Die folgenden Probleme und fehlenden Features sind mit der **Version 0.1.0** des openxr-Plug-ins von Mixed Reality bekannt. Wir arbeiten an diesen und veröffentlichen Korrekturen und neue Features in zukünftigen Versionen.

* Die Unterstützung von **räumlichen Azure-Ankern** wird in einer zukünftigen Version angezeigt.
* **ARM64** ist die einzige unterstützte Plattform für hololens 2-apps. Die **Arm** -Plattform wird in einer zukünftigen Version angezeigt.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie eine Unity-App auf hololens 2 aussetzen und fortsetzen, kann die APP nicht ordnungsgemäß fortgesetzt werden, was zu vier Drehungs Punkten in der hololens-Ansicht führt.

* Festlegen des tiefen Übermittlungs **Modus** auf " **None** " in den openxr-Projekteinstellungen als Problem Umgehung
