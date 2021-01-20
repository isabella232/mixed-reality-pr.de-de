---
title: Kamera in Unity
description: Erfahren Sie, wie Sie die Hauptkamera von Unity für die Windows Mixed Reality-Entwicklung einrichten und verwenden, um Holographic Rendering durchzuführen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Holographic-Rendering, Holographic, immersive, Fokuspunkt, tiefen Puffer, nur Ausrichtung, Positional, nicht transparent, transparent, Clip, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: ba42e8a384f62dddcf7b8e685859ddeff7b666bb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581126"
---
# <a name="camera-in-unity"></a>Kamera in Unity

Wenn Sie ein Mixed Reality-Headset durch tragen, wird es zur Mitte ihrer Holographic World. Die Unity- [Kamera](https://docs.unity3d.com/Manual/class-Camera.html) Komponente verarbeitet das stereorenderingrendering automatisch und folgt der Bewegung und Drehung des Kopfes. Sie sollten jedoch die unten beschriebenen Kameraeinstellungen festlegen, um die visuelle Qualität und die [Stabilität des Hologramms](../platform-capabilities-and-apis/hologram-stability.md)vollständig zu optimieren.

## <a name="setup"></a>Einrichten

1. Wechseln Sie zum Abschnitt **andere Einstellungen** der **Windows Store-Player-Einstellungen** .
2. Wählen Sie **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity als **Windows Holographic** aufgeführt werden kann.
3. **Unterstützte virtuelle Realität** auswählen

>[!NOTE]
>Diese Einstellungen müssen in jeder Szene der APP auf die Kamera angewendet werden.
>
>Wenn Sie in Unity eine neue Szene erstellen, enthält diese standardmäßig ein Hauptkamera-gameobject in der Hierarchie, die die Kamera Komponente enthält, aber die unten aufgeführten Einstellungen sind nicht ordnungsgemäß angewendet.

## <a name="holographic-vs-immersive-headsets"></a>Holographic im Vergleich zu immersiven Headsets

Die Standardeinstellungen für die Unity-Kamera-Komponente gelten für herkömmliche 3D-Anwendungen, die einen Skybox-ähnlichen Hintergrund benötigen, da Sie nicht über eine reale Welt verfügen.

* Bei der Ausführung auf einem **[immersiven Headset](../../discover/immersive-headset-hardware-details.md)** Rendern Sie alles, was dem Benutzer angezeigt wird, und Sie möchten die Skybox wahrscheinlich behalten.
* Wenn Sie jedoch auf einem **Holographic-Headset** wie [hololens](/hololens/hololens1-hardware)ausgeführt werden, sollte die reale Welt hinter der von der Kamera gerendert werden. Legen Sie den Kamera Hintergrund auf "transparent" (in hololens, schwarz rendert als transparent) anstelle einer Skybox-Textur fest:
    1. Wählen Sie die Hauptkamera im Hierarchie Panel aus.
    2. Suchen Sie im Inspektor-Panel die Kamera Komponente, und ändern Sie die Dropdown Liste Flag Löschen von Skybox in voll Tonfarbe.
    3. Wählen Sie die Hintergrund Farbauswahl aus, und ändern Sie die RGBA-Werte in (0,0).

Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset durch das Überprüfen von [holographicsettings. isdisplayopisch](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)durch ein immersives oder Holographic ist.

## <a name="positioning-the-camera"></a>Positionieren der Kamera

Es ist einfacher, Ihre APP zu entwerfen, wenn Sie sich die Anfangsposition des Benutzers als (X: 0, Y: 0, Z: 0) vorstellen. Da die Hauptkamera die Bewegung des Benutzers nachverfolgt, kann die Startposition des Benutzers festgelegt werden, indem die Startposition der Hauptkamera festgelegt wird.

1. Auswählen der Hauptkamera im Hierarchie Panel
2. Suchen Sie im Inspektor-Panel die Transformations Komponente, und ändern Sie die Position von (x: 0, y: 1, z:-10) in (x: 0, y: 0, z: 0).

   ![Kamera im Inspektor-Bereich in Unity](images/maincamera-350px.png)  
   *Kamera im Inspektor-Bereich in Unity*

## <a name="clip-planes"></a>Clip Flächen

Das Rendern von Inhalten zu nahe am Benutzer kann in gemischter Realität unbequem sein. Sie können die [Near-und Far-Clip-Plane](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) in der Kamera Komponente anpassen.

1. Wählen Sie die Hauptkamera im Hierarchie Panel aus.
2. Suchen Sie im Inspektor-Panel nach den Ausschneide Flächen der Kamera Komponente, und ändern Sie das Textfeld in der Nähe von 0,3 in 0,85. Inhalte, die noch enger gerendert werden, können zu Benutzer Unannehmlichkeiten führen und sollten gemäß den [Richtlinien für die renderentfernungs](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)

## <a name="multiple-cameras"></a>Mehrere Kameras

Wenn in der Szene mehrere Kamerakomponenten vorhanden sind, weiß Unity, welche Kamera für das stereorendern und die Head-Nachverfolgung verwendet werden soll, je nachdem, welches gameobject über das maincamera-Tag verfügt.

## <a name="recentering-a-seated-experience"></a>Wiedergeben eines sitzenden Erlebnisses

Wenn Sie eine Umgebung mit [sitzender Skalierung](../../design/coordinate-systems.md)entwickeln, können Sie den Welt Ursprung von Unity an der aktuellen Hauptposition des Benutzers wiederholen, indem Sie den **[XR aufrufen. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** -Methode.

## <a name="reprojection-modes"></a>Neuprojektions Modi

Sowohl hololens als auch immersive Headsets werden jeden Frame, der von der APP gerendert wird, neu projektet, um die tatsächliche Kopfzeile des Benutzers bei der Ausgabe von Phots anzupassen.

Standardmäßig:

* **Immersive Headsets** kümmern sich um die neuprojektion von positionellen, wenn die APP einen tiefen Puffer für einen bestimmten Frame bereitstellt. Mit immersiven Headsets werden Ihre Hologramme auch an der Position und Ausrichtung angepasst. Wenn kein tiefen Puffer bereitgestellt wird, korrigiert das System nur die Fehleinstellungen in der Ausrichtung.
* **Holographic-Headsets** wie hololens kümmern sich um die neuprojektion von positionellen, unabhängig davon, ob die APP ihren tiefen Puffer bereitstellt.  Eine positionelle neuprojektion ist ohne tiefen Puffer in hololens möglich, da das Rendering häufig geringer ist, wenn ein stabiler Hintergrund von der realen Welt bereitgestellt wird.

Wenn Sie wissen, dass Sie eine [nur-Orientierung-](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) Umgebung mit ordnungsgemäß gesperrtem Inhalt (z. b. 360-Grad-Videoinhalt) entwickeln, können Sie den Modus für die neuprojektion explizit auf die Ausrichtung festlegen, indem Sie [holographicsettings. reprojectionmode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) auf [holographikreprojectionmode. orientationonly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)festlegen.

## <a name="sharing-your-depth-buffers-with-windows"></a>Freigeben von tiefen Puffern mit Windows

Durch die Freigabe des tiefen Puffers Ihrer APP für die einzelnen Frames erhält Ihre APP einen von zwei Verb esse ungen in der – Hologramm-Stabilität, basierend auf der Art des von Ihnen Renderns:

* **Immersive Headsets** können bei der Bereitstellung eines tiefen Puffers die neuprojektion von Positionen durchführen, wobei die Hologramme sowohl an der Position als auch an der Ausrichtung für die mitediction angepasst werden.
* **Holographic-Headsets** haben einige verschiedene Methoden. Hololens 1 wählt automatisch einen [Fokuspunkt](focus-point-in-unity.md) aus, wenn ein tiefen Puffer bereitgestellt wird. Dadurch wird die – Hologramm-Stabilität entlang der Ebene optimiert, die den meisten Inhalt überschneidet. Hololens 2 stabilisiert Inhalte mithilfe der [tiefen LSR (siehe Hinweise)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

So legen Sie fest, ob Ihre Unity-APP einen tiefen Puffer für Windows bereitstellt:

1. Wechseln Sie zu **Edit**  >  **Project Settings**  >  **Player**  >  **universelle Windows-Plattform Tab**  >  **XR Settings**.
2. Erweitern Sie das **Windows Mixed Reality SDK** -Element.
3. Aktivieren oder deaktivieren Sie das Kontrollkästchen **Tiefe Puffer Freigabe aktivieren** .  Die Aktivierung der tiefen Puffer Freigabe ist in neuen Projekten standardmäßig aktiviert, da diese Funktion Unity hinzugefügt wurde und für ältere Projekte, die aktualisiert wurden, standardmäßig deaktiviert wird.

Ein tiefen Puffer kann die visuelle Qualität verbessern, solange Windows die normalisierten pro-Pixel-tiefen Werte in ihrem tiefen Puffer mithilfe der Near-und Far-Ebenen, die Sie in Unity auf der Hauptkamera festgelegt haben, genauer zuordnen lässt.  Wenn Ihr renderingwert auf typische Weise handle-Werte übergibt, sollten Sie in der Regel in Ordnung sein, obwohl die übergreifende Renderingvorgänge, die in den tiefen Puffer schreiben, während Sie bis zu vorhandenen Farbpixeln zeigen, die neuprojektion verwirren können.  Wenn Sie wissen, dass Ihre Renderingdurchläufen viele der abschließenden tiefen Pixel mit ungenauen tiefen Werten belassen, erhalten Sie wahrscheinlich eine bessere visuelle Qualität, indem Sie die Option "Tiefe Puffer Freigabe aktivieren" deaktivieren.

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit"></a>Automatisches Einrichten von Szenen und Kameras mit Mixed Reality Toolkit 

Befolgen Sie die [Schritt-für-Schritt](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) -Anleitung zum Hinzufügen von Mixed Reality Toolkit zu Ihrem Unity-Projekt, und das Projekt wird automatisch konfiguriert. Sie können das Projekt auch ohne mrtk manuell konfigurieren, indem Sie das Handbuch im Abschnitt unten durchführen.

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
* [Mixedrealitytoolkit Hauptkamera. Prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)