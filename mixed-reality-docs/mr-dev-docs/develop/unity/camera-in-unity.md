---
title: Kamera Einrichtung in Unity
description: Erfahren Sie, wie Sie die Hauptkamera von Unity für die Windows Mixed Reality-Entwicklung einrichten und verwenden, um Holographic Rendering durchzuführen.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Holographic-Rendering, Holographic, immersive, Fokuspunkt, tiefen Puffer, nur Ausrichtung, Positional, nicht transparent, transparent, Clip, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636298"
---
# <a name="camera-setup-in-unity"></a>Kamera Einrichtung in Unity

Wenn Sie ein Mixed Reality-Headset durch tragen, wird es zur Mitte ihrer Holographic World. Die Unity- [Kamera](https://docs.unity3d.com/Manual/class-Camera.html) Komponente verarbeitet das stereorenderingrendering automatisch und folgt der Bewegung und Drehung des Kopfes. Sie sollten jedoch die unten beschriebenen Kameraeinstellungen festlegen, um die visuelle Qualität und die [Stabilität des Hologramms](../platform-capabilities-and-apis/hologram-stability.md)vollständig zu optimieren.

## <a name="hololens-vs-vr-immersive-headsets"></a>Hololens im Vergleich zu den von VR immersiven Headsets

Die Standardeinstellungen für die Unity-Kamera-Komponente gelten für herkömmliche 3D-Anwendungen, die einen Skybox-ähnlichen Hintergrund benötigen, da Sie nicht über eine reale Welt verfügen.

* Bei der Ausführung auf einem **[immersiven Headset](../../discover/immersive-headset-hardware-details.md)** Rendern Sie alles, was dem Benutzer angezeigt wird, und Sie möchten die Skybox wahrscheinlich behalten.
* Wenn Sie jedoch auf einem **Holographic-Headset** wie [hololens](/hololens/hololens2-hardware)ausgeführt werden, sollte die reale Welt hinter der von der Kamera gerendert werden. Legen Sie den Kamera Hintergrund auf "transparent" (in hololens, schwarz rendert als transparent) anstelle einer Skybox-Textur fest:
    1. Wählen Sie die Hauptkamera im Hierarchie Panel aus.
    2. Suchen Sie im Inspektor-Panel die Kamera Komponente, und ändern Sie die Dropdown Liste Flag Löschen von Skybox in voll Tonfarbe.
    3. Wählen Sie die Hintergrund Farbauswahl aus, und ändern Sie die RGBA-Werte in (0,0).
        1. Wenn Sie diese Einstellung aus dem Code festlegen, können Sie Unity [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>Kamerasetup

Je nachdem, welche Art von Benutzeroberflächen Sie entwickeln, ist die Hauptkamera immer die primäre Stereo-renderingkomponente, die an die von Ihrem Gerät angefügte Anzeige angeschlossen ist. Es ist einfacher, Ihre APP zu entwerfen, wenn Sie sich die Anfangsposition des Benutzers als (X: 0, Y: 0, Z: 0) vorstellen. Da die Hauptkamera die Bewegung des Benutzers nachverfolgt, kann die Startposition des Benutzers festgelegt werden, indem die Startposition der Hauptkamera festgelegt wird.

Die zentrale Entscheidung, die Sie treffen müssen, ist, ob Sie für hololens oder für VR-immersive Headsets entwickeln. Sobald dies der Fall ist, fahren Sie mit dem jeweiligen Einrichtungs Abschnitt fort.

### <a name="hololens-camera-setup"></a>Hololens-Kamera-Setup

Bei hololens-apps müssen Sie Anker für alle Objekte verwenden, die Sie in der Szene Umgebung sperren möchten. Es wird empfohlen, unbegrenzten Speicherplatz zur Maximierung der Stabilität und zum Erstellen von Ankern in mehreren Räumen zu verwenden.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>Einrichtung der VR-Kamera

Windows Mixed Reality unterstützt Apps über eine Vielzahl von [Skalierungs](../../design/coordinate-systems.md#mixed-reality-experience-scales)Möglichkeiten hinweg, von ausgerichteten und skalierbaren apps bis hin zu hochskalierbaren apps. Auf hololens können Sie weitere apps erstellen und Apps erstellen, mit denen Benutzer mehr als 5 Meter durchlaufen können, indem Sie eine ganze Etage eines Builds und darüber hinaus untersuchen.

Der erste Schritt beim Aufbau einer gemischten Realität in Unity besteht darin, zu bestimmen [, welche Benutzer](../../design/coordinate-systems.md) Oberfläche Ihre APP als Ziel hat:

* [Ausrichtung oder sitzender Maßstab](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [Die Position oder die Raum Skala](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [Weltweit skalieren](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>Raum-oder Steh Erfahrung

> [!NOTE]
> Wenn Sie für HL2 erstellen, empfiehlt es sich, eine benutzerfreundliche Oberfläche zu erstellen, oder Sie sollten die Verwendung von [Szenen](../platform-capabilities-and-apis/scene-understanding-sdk.md) Informationen in Erwägung gezogen haben.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>Sitzender Erfahrungs

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>Einrichten des Kamera Hintergrunds

Wenn Sie mrtk verwenden, wird der Hintergrund der Kamera automatisch konfiguriert und verwaltet. Für das XR SDK oder ältere WSA-Projekte empfiehlt es sich, den Hintergrund der Kamera auf hololens auf "Solid Black" festzulegen und die Skybox für VR beizubehalten.

## <a name="using-multiple-cameras"></a>Verwenden mehrerer Kameras

Wenn in der Szene mehrere Kamerakomponenten vorhanden sind, weiß Unity, welche Kamera für das stereorenrendering verwendet werden soll, je nachdem, welches gameobject über das maincamera-Tag verfügt. In Legacy XR wird dieses Tag auch verwendet, um die Head-Nachverfolgung zu synchronisieren. Im XR SDK wird die Head-Nachverfolgung durch ein an die Kamera angefügtes trackedtargedriver-Skript gesteuert.

## <a name="sharing-depth-buffers"></a>Freigeben von tiefen Puffern

Durch die Freigabe des tiefen Puffers Ihrer APP für die einzelnen Frames erhält Ihre APP einen von zwei Verb esse ungen in der – Hologramm-Stabilität, basierend auf der Art des von Ihnen Renderns:

* **VR-immersive Headsets** können bei der Bereitstellung eines tiefen Puffers die neuprojektion von Positionen durchführen, wobei die Hologramme sowohl an der Position als auch an der Ausrichtung für die mitediction angepasst werden.
* **Hololens-Headsets** haben einige verschiedene Methoden. Hololens 1 wählt automatisch einen [Fokuspunkt](focus-point-in-unity.md) aus, wenn ein tiefen Puffer bereitgestellt wird. Dadurch wird die – Hologramm-Stabilität entlang der Ebene optimiert, die den meisten Inhalt überschneidet. Hololens 2 stabilisiert Inhalte mithilfe der [tiefen LSR (siehe Hinweise)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>Verwenden von Clipping-Ebenen

Das Rendern von Inhalten zu nahe am Benutzer kann in gemischter Realität unbequem sein. Sie können die [Near-und Far-Clip-Plane](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) in der Kamera Komponente anpassen.

1. Wählen Sie die **Hauptkamera** im **Hierarchie** Panel aus.
2. Suchen Sie **im Inspektor** -Panel nach den **Ausschneide Flächen** der **Kamera** Komponente, und ändern Sie das Textfeld **in der Nähe** von **0,3** in **0,85**. Inhalte, die noch enger gerendert werden, können zu Benutzer Unannehmlichkeiten führen und sollten gemäß den [Richtlinien für die renderentfernungs](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)

## <a name="recentering-the-camera"></a>Wiedergeben der Kamera

Wenn Sie eine Umgebung mit [sitzender Skalierung](../../design/coordinate-systems.md)entwickeln, können Sie den Welt Ursprung von Unity an der aktuellen Hauptposition des Benutzers wiederholen, indem Sie den **[XR aufrufen. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** -Methode in der Legacy-Version XR oder der **[xrinputsubsystem. tryrecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** -Methode im XR SDK.

## <a name="teleportation"></a>Teleportation

Diese Funktion ist in der Regel für die VR-Oberfläche reserviert:

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Neuprojektions Modi

Sowohl hololens als auch immersive Headsets werden jeden Frame, der von der APP gerendert wird, neu projektet, um die tatsächliche Kopfzeile des Benutzers bei der Ausgabe von Phots anzupassen.

Standardmäßig:

* **VR-immersive Headsets** übernimmt die neuprojektion von positionellen, wenn die APP einen tiefen Puffer für einen bestimmten Frame bereitstellt. Mit immersiven Headsets werden Ihre Hologramme auch an der Position und Ausrichtung angepasst. Wenn kein tiefen Puffer bereitgestellt wird, korrigiert das System nur die Fehleinstellungen in der Ausrichtung.
* **Holographic-Headsets** wie hololens 2 kümmern sich um die neuprojektion von positionellen, unabhängig davon, ob die APP ihren tiefen Puffer bereitstellt. Eine positionelle neuprojektion ist ohne tiefen Puffer in hololens möglich, da das Rendering häufig geringer ist, wenn ein stabiler Hintergrund von der realen Welt bereitgestellt wird.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Journey folgen, die wir angelegt haben, befinden Sie sich mitten in der Untersuchung der mrtk Core-Bausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Anvisieren](gaze-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch

* [Hologrammstabilität](../platform-capabilities-and-apis/hologram-stability.md)
* [Skalierungsmöglichkeiten](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Räumliche Phase](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Verfolgbarkeitsverlust in Unity](tracking-loss-in-unity.md)
* [Raumanker](../../design/spatial-anchors.md)
* [Persistenz in Unity](persistence-in-unity.md)
* [Gemeinsame Erlebnisse in Unity](shared-experiences-in-unity.md)
* [Azure Spatial Anchors](/azure/spatial-anchors)
* [Azure Spatial Anchor SDK für Unity](/dotnet/api/Microsoft.Azure.SpatialAnchors)