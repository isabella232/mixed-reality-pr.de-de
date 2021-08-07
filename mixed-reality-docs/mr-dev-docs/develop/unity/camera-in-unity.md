---
title: Kameraeinrichtung in Unity
description: Erfahren Sie, wie Sie die Unity-Hauptkamera für die entwicklung Windows Mixed Reality holografisches Rendering einrichten und verwenden.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, holographic rendering, holographic, immersive, focus point, depth buffer, orientation-only, positional, opaque, transparent, clip, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 1ac8c16e7bdd6b85b05c837e1a27fbd1e4cf4489ccb03d10ea5e952b2656cbe8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212293"
---
# <a name="camera-setup-in-unity"></a>Kameraeinrichtung in Unity

Wenn Sie ein Mixed Reality-Headset tragen, wird es zum Mittelpunkt Ihrer holografischen Welt. Die [Unity-Kamerakomponente](https://docs.unity3d.com/Manual/class-Camera.html) verarbeitet automatisch stereodarstellungsspezifisches Rendering und folgt Ihrer Kopfbewegung und Drehung. Um jedoch die visuelle Qualität und Hologrammstabilität vollständig zu [optimieren,](../platform-capabilities-and-apis/hologram-stability.md)sollten Sie die unten beschriebenen Kameraeinstellungen festlegen.

## <a name="hololens-vs-vr-immersive-headsets"></a>HoloLens im Vergleich zu immersiven VR-Headsets

Die Standardeinstellungen für die Unity-Kamerakomponente gelten für herkömmliche 3D-Anwendungen, die einen Skybox-einheitlichen Hintergrund benötigen, da sie keine reale Welt haben.

* Wenn Sie auf einem **[immersiven Headset](../../discover/immersive-headset-hardware-details.md)** ausführen, rendern Sie alles, was dem Benutzer angezeigt wird, und daher sollten Sie die Skybox behalten.
* Wenn Sie jedoch auf einem **holografischen** Headset wie HoloLens [ausführen,](/hololens/hololens2-hardware)sollte die reale Welt hinter allem erscheinen, was die Kamera rendert. Legen Sie den Kamerahintergrund auf transparent (in HoloLens, schwarz wird als transparent gerendert) und nicht auf eine Skybox-Textur fest:
    1. Auswählen der Hauptkamera im Hierarchiebereich
    2. Suchen Sie im Inspektorbereich nach der Kamerakomponente, und ändern Sie die Dropdownliste Flags löschen von Skybox in Solid Color.
    3. Wählen Sie die Hintergrundfarbauswahl aus, und ändern Sie die RGBA-Werte in (0, 0, 0, 0).
        1. Wenn Sie dies über Code festlegen, können Sie Unity verwenden. [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>Kamerasetup

Unabhängig davon, welche Art von Erfahrung Sie entwickeln, ist die Hauptkamera immer die primäre Stereo-Renderingkomponente, die an die am Kopf angeschlossene Anzeige Ihres Geräts angefügt ist. Es ist einfacher, Ihre App zu gestalten, wenn Sie sich die Anfangsposition des Benutzers als (X: 0, Y: 0, Z: 0) vorstellen. Da die Hauptkamera die Bewegung des Kopfs des Benutzers nachverfolgt, kann die Anfangsposition des Benutzers durch Festlegen der Anfangsposition der Hauptkamera festgelegt werden.

Die zentrale Wahl, die Sie treffen müssen, ist, ob Sie für immersive Headsets HoloLens VR entwickeln. Sobald Sie dies haben, fahren Sie mit dem Setupabschnitt ab, der angewendet wird.

### <a name="hololens-camera-setup"></a>HoloLens der Kameraeinrichtung

Für HoloLens-Apps müssen Sie Anker für alle Objekte verwenden, die Sie für die Szenenumgebung sperren möchten. Es wird empfohlen, ungebundenen Raum zu verwenden, um die Stabilität zu maximieren und Anker in mehreren Räumen zu erstellen.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>VR-Kameraeinrichtung

Windows Mixed Reality unterstützt Apps für eine Vielzahl [](../../design/coordinate-systems.md#mixed-reality-experience-scales)von Benutzererfahrungsskalieren, von Apps mit ausrichtungs- und platzskalierten Apps bis hin zu Raum-Apps. Auf HoloLens können Sie weiter gehen und weltweit Apps erstellen, mit denen Benutzer mehr als 5 Meter laufen und eine ganze Etage eines Gebäudes und darüber hinaus erkunden können.

Der erste Schritt beim Erstellen einer Mixed Reality-Erfahrung in Unity besteht in der Bestimmung, für welche Benutzererfahrung [Ihre](../../design/coordinate-systems.md) App verwendet werden soll:

* [Ausrichtung oder skalierungsbasierte Ausrichtung](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [Stehend oder Raummaßstab](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [Weltweit](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>Raumskala- oder Stehenderfahrungen

> [!NOTE]
> Wenn Sie für HL2 erstellen, empfiehlt es sich, eine Erfahrung auf Augenhöhe zu erstellen, oder erwägen Sie die Verwendung von [Scene Understanding,](../platform-capabilities-and-apis/scene-understanding-sdk.md) um den Boden Ihrer Szene zu verstehen.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>Besendung

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>Einrichten des Kamerahintergrunds

Wenn Sie MRTK verwenden, wird der Hintergrund der Kamera automatisch konfiguriert und verwaltet. Für XR SDK- oder Legacy-WSA-Projekte empfiehlt es sich, den Hintergrund der Kamera auf dem HoloLens auf solid black zu setzen und die Skybox für VR zu behalten.

## <a name="using-multiple-cameras"></a>Verwenden mehrerer Kameras

Wenn mehrere Kamerakomponenten in der Szene enthalten sind, weiß Unity, welche Kamera für stereodarstellung verwendet werden soll, je nachdem, welches GameObject über das MainCamera-Tag verfügt. In Legacy-XR wird dieses Tag auch verwendet, um die Nachverfolgung des Kopfs zu synchronisieren. Im XR SDK wird die Kopfverfolgung durch ein trackedPoseDriver-Skript gesteuert, das an die Kamera angefügt ist.

## <a name="sharing-depth-buffers"></a>Freigeben von Tiefenpuffern

Wenn Sie den Tiefenpuffer Ihrer App für Windows jeden Frame freigeben, erhalten Sie für Ihre App je nach Art des Headsets, für das Sie rendern möchten, eine von zwei Boosts für die Hologrammstabilität:

* **Immersive VR-Headsets** können eine positionsbezogene Neuprojektion übernehmen, wenn ein Tiefenpuffer bereitgestellt wird, und Ihre Hologramme so anpassen, dass sie an Position und Ausrichtung falsch ausgerichtet sind.
* **HoloLens Headsets** haben verschiedene Methoden. HoloLens 1 wählt automatisch einen [](focus-point-in-unity.md) Fokuspunkt aus, wenn ein Tiefenpuffer bereitgestellt wird, um die Hologrammstabilität entlang der Ebene zu optimieren, die den meisten Inhalt überschneidet. HoloLens 2 der Inhalt mithilfe der [Tiefen-LSR (siehe Hinweise) stabilisiert.](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>Verwenden von Clippingebenen

Das Rendern von Inhalten, die dem Benutzer zu nahe sind, kann in Mixed Reality unermesslich sein. Sie können die [nah- und fernen Clipebenen der](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) Kamerakomponente anpassen.

1. Auswählen der **Hauptkamera** im **Hierarchiebereich**
2. Suchen Sie **im Inspektorbereich** nach der **Kamerakomponente** **Clipping Planes,** und ändern Sie das Textfeld **Near** (Nah) von **0.3** in **0.85.** Inhalte, die noch näher gerendert werden, können zu Benutzerbeschwerden führen und sollten nach den Richtlinien für die [Renderentfernung vermieden werden.](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)

## <a name="recentering-the-camera"></a>Aktuelles Verwenden der Kamera

Wenn Sie eine besenskalierte Benutzeroberfläche [erstellen,](../../design/coordinate-systems.md)können Sie den Ursprung von Unity an der aktuellen Kopfposition des Benutzers verbessern, indem Sie **[XR aufrufen. InputTracking.Recenter-Methode](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** in legacy XR oder der **[XRInputSubsystem.TryRecenter-Methode](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** im XR SDK.

## <a name="teleportation"></a>Teleportation

Dieses Feature ist in der Regel für VR-Funktionen reserviert:

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Reprojection-Modi

Sowohl HoloLens headsets als auch immersive Headsets pro je nach Frame, den Ihre App rendert, werden neu projiziert, um die tatsächliche Kopfposition des Benutzers anzupassen, wenn Photonen ausgegeben werden.

Standardmäßig:

* **Immersive VR-Headsets** übernehmen die neu projizierte Position, wenn die App einen Tiefenpuffer für einen bestimmten Frame bietet. Immersive Headsets passen Ihre Hologramme auch an positions- und ausrichtungsverfehlte Einstellungen an. Wenn kein Tiefenpuffer bereitgestellt wird, korrigiert das System nur Fehlausrichtungen in der Ausrichtung.
* **Holografische Headsets** wie HoloLens 2 sorgen für eine positionsbezogene Neuprojektion, unabhängig davon, ob die App ihren Tiefenpuffer zur Verfügung stellt oder nicht. Eine positionsbezogene Neuprojektion ist ohne Tiefenpuffer auf dem HoloLens da das Rendering oft mit einem stabilen Hintergrund, der von der realen Welt bereitgestellt wird, nur eine spärliche Darstellung auftrat.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie den Weg zur Unity-Entwicklung, den wir ihnen auf den Weg geben, folgen, sind Sie gerade dabei, die MRTK-Kernbausteine zu erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Anvisieren](gaze-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch

* [Hologrammstabilität](../platform-capabilities-and-apis/hologram-stability.md)
* [Erfahrungsskala](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Räumliche Stufe](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Verfolgbarkeitsverlust in Unity](tracking-loss-in-unity.md)
* [Raumanker](../../design/spatial-anchors.md)
* [Persistenz in Unity](persistence-in-unity.md)
* [Gemeinsame Erlebnisse in Unity](shared-experiences-in-unity.md)
* [Azure Spatial Anchors](/azure/spatial-anchors)
* [Azure Spatial Anchors SDK für Unity](/dotnet/api/Microsoft.Azure.SpatialAnchors)