---
title: 'MRTK-Einführung: Verwenden allgemeiner räumlicher Interaktionen'
description: Verwenden des Mixed Reality-Toolkits Unity für grundlegende Interaktionen für HoloLens 2, HoloLens, Windows Mixed Reality und Open VR.
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality-Toolkit, Windows Mixed Reality, Entwurf, Beispiel-App, Steuerelemente, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.localizationpriority: high
ms.openlocfilehash: 8b9af843dc059ef4d50aa5508356c7aeed968a4e
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2021
ms.locfileid: "98248085"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a>MRTK-Einführung Verwenden des Mixed Reality-Toolkits Unity für gängige räumliche Interaktionen

![MRTK](images/MRTK101/MRTK101Cover.png)

Erfahren Sie, wie Sie das MRTK nutzen, um einige der am häufigsten verwendeten Interaktionsmuster in Mixed Reality umzusetzen.

- Wie lassen sich Eingabeinteraktionen im Unity-Editor simulieren?
- Wie lässt sich ein Objekt greifen und bewegen?
- Wie wird die Größe eines Objekts geändert?
- Wie lässt sich ein Objekt präzise bewegen oder drehen?
- Wie lässt man ein Objekt auf Eingabeereignisse reagieren?
- Wie wird visuelles Feedback implementiert?
- Wie kann Audiofeedback hinzugefügt werden?
- Wie werden Prefabs für Schaltflächen im HoloLens 2-Stil verwendet?
- Wie lässt man sich von einem Objekt folgen?
- Wie erreicht man, dass ein Objekt sich einem zuwendet?

> [!NOTE]
> Dieser Artikel wurde mit den Änderungen im [MRTK v2.5.1-Release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1) aktualisiert.

Alle Inhalte auf dieser Seite können im Unity-Editor mit der Eingabesimulation von MRTK getestet werden. Wenn Sie dies noch nicht getan haben, befolgen Sie das [MRTK-Installationshandbuch (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html), um die neueste Version von MRTK zu installieren.

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a>Wie lassen sich Eingabeinteraktionen im Unity-Editor simulieren?

MRTK unterstützt die Simulation von Eingaben im Editor. Starten Sie Ihre Szene, indem Sie auf die Wiedergabeschaltfläche von Unity klicken, und verwenden Sie dann die folgenden Tasten, um Eingaben zu simulieren:
- Drücken Sie die Tasten W, A, S, D, um die Kamera zu bewegen.
- Halten Sie die rechte Maustaste gedrückt, und bewegen Sie die Maus, um sich umzusehen.
- Drücken Sie die Leertaste (rechte Hand) oder die linke Umschalttaste (linke Hand), um die simulierten Hände aufzurufen
- Drücken Sie die Taste T oder Y, um simulierte Hände in der Ansicht zu halten.
- Drücken Sie Q oder E (horizontal) bzw. R oder F (vertikal), um die simulierten Hände zu drehen

Weitere Informationen zur Eingabesimulation finden Sie in der [MRTK-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).

## <a name="how-to-grab-and-move-an-object"></a>Wie lässt sich ein Objekt greifen und bewegen?

Fügen Sie die Skripts **ObjectManipulator.cs** und **NearInteractionGrabbable.cs** an, um ein Objekt greifbar zu machen. ObjectManipulator unterstützt sowohl nahe als auch ferne Interaktionen. Sie können ein Objekt durch die Eingabe mittels artikuliertem Hand-Tracking (nah), Handstrahl (fern), den Strahl des Motion Controllers (fern), den Anvisier-Cursor von HoloLens 2 und Tippen in die Luft (fern) greifen und bewegen.

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a>Wie wird die Größe eines Objekts geändert?
**ObjectManipulator.cs** unterstützt die beidhändige Skalierung/Drehung. Das Skript funktioniert mit verschiedenen Eingabetypen, wie z. B. der Handeingabe von HoloLens 2, der Eingabe durch Anvisieren und Gesten von HoloLens 1 und der Motion Controller-Eingabe des immersiven Headsets für Windows Mixed Reality.

- [Weitere Informationen zum Objekt-Manipulator finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Wie lässt sich ein Objekt präzise bewegen oder drehen?
Weisen Sie einem Objekt **BoundsControl.cs** zu, um Bounding Box (Begrenzungsrahmen) zu verwenden, wobei es sich um die Oberfläche zum Skalieren und Drehen von Objekten handelt. Standardmäßig werden blaue Ziehpunkte und Drahtlinien im Stil von HoloLens 1 angezeigt. Um näherungsbasierte animierte Ziehpunkte im HoloLens 2-Stil zu verwenden, müssen Sie Prefabs und Materialien zuweisen. 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [Weitere Informationen zum Bounds-Steuerelement finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a>Wie lässt man ein Objekt auf Eingabeereignisse reagieren?
Weisen Sie einem Objekt **PointerHandler.cs** zu. Im Inspektor können Sie die Ereignisse OnPointerDown(), OnPointerUp(), OnPointerClicked() und OnPointerDragged() verwenden. Um diese Ereignisse in einem Skript zu verwenden, implementieren Sie **IMixedRealityPointerHandler**.

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Weitere Informationen zum Eingabesystem finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Wie wird visuelles Feedback implementiert?
Weisen Sie einem Objekt **Interactable.cs** zu. Fügen Sie im Inspektor Zielobjekte hinzu, und erstellen Sie ein neues Design. Mithilfe der Designprofile von Interactable können Sie allen verfügbaren Interaktionszuständen auf einfache Weise visuelles Feedback hinzufügen.

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable stellt verschiedene Arten von Designs zur Verfügung, einschließlich des Shader-Designs, mit dem Sie die Eigenschaften des Shaders pro Interaktionszustand steuern können.

- [Weitere Informationen zu Interactable finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Ein weiterer wichtiger Baustein für visuelles Feedback ist der **MRTK-Standardshader**. Mit dem MRTK-Standardshader können Sie auf einfache Weise visuelle Feedbackeffekte hinzufügen, wie das Licht beim Draufzeigen und Näherungslicht. Da der MRTK-Standardshader weniger Berechnungen als der Unity-Standardshader ausführt, können Sie ein leistungsstarkes Verhalten erreichen.

Erstellen Sie ein neues Material, und wählen Sie den Shader „Mixed Reality Toolkit > Standard“ aus. Alternativ können Sie eins der vorhandenen Materialien auswählen, die den MRTK-Standardshader verwenden.

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Weitere Informationen zum MRTK-Standardshader finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Wie kann Audiofeedback hinzugefügt werden?
Fügen Sie einem Objekt **AudioSource** hinzu. Weisen Sie dann in den Skripts, die Eingabeereignisse verfügbar machen (z. B. Interactable.cs oder PointerHandler.cs) das Objekt mit AudioSource dem Ereignis zu, und wählen Sie **AudioSource.PlayOneShot()** aus. Sie können eigene Audioclips verwenden oder einen aus den Audioressourcen des MRTK auswählen.

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a>Wie werden Prefabs für Schaltflächen im HoloLens 2-Stil verwendet?
MRTK bietet verschiedene Arten von Schaltflächen im Shellformat (OS) von HoloLens 2, einschließlich visuellem Feedback wie Näherungslicht, Stauchungsrahmen und einem Ripple-Effekt auf der Schaltflächen-Oberfläche, die das Vertrauen des Benutzers verbessern.

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

Legen Sie eins der **Prefabs für eine drückbare Schaltfläche im HoloLens 2-Stil** per Drag & Drop in Ihrer Szene ab. Das Prefab verwendet Interactable.cs, das oben vorgestellt wurde. Sie können in Interactable verfügbar gemachte Ereignisse wie OnClick() verwenden, um Aktionen auszulösen.

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Weitere Informationen zu Schaltflächen-Prefabs finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a>Wie lässt man sich von einem Objekt folgen?
Weisem Sie einem Objekt das Skript **RadialView.cs** oder **Follow.cs** zu. Es ist Teil der Solver-Reihe von Skripts, die Ihnen verschiedene Arten von Objektpositionierung im 3D-Raum ermöglichen. **SolverHandler.cs** wird automatisch hinzugefügt.
Unten finden Sie ein Beispiel der RadialView-Konfiguration, um ein „Hinterhertrotten“-Folgeverhalten zu erreichen, ähnlich wie das Startmenü in der HoloLens-Shell. Sie können die minimale/maximale Entfernung und den minimalen/maximalen Ansichtswinkel angeben. Im Beispiel unten ist die Positionierung des Objekts zwischen 0,4 m und 0,8 m in einem Bereich von 15 ° dargestellt. Passen Sie die Werte für die Lerp-Zeit an, um das Aktualisieren der Position schneller oder langsamer erfolgen zu lassen.

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Weitere Informationen zu Solvern finden Sie in der MRTK-Dokumentation.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a>Wie erreicht man, dass ein Objekt sich einem zuwendet?
Weisen Sie einem Objekt das **Billboard.cs**-Skript zu. Das Objekt ist Ihnen immer zugewendet, unabhängig von Ihrer Position. Sie können die Pivotachsenoption angeben.

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Sind Sie bereit, beeindruckende Erlebnisse für Mixed Reality zu gestalten? Besuchen Sie die unten angegebenen Seiten, und erfahren Sie mehr über MRTK und Mixed Reality.

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong-Yoon-Park</b><br>UX-Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [MRTK – Installationshandbuch (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK-Dokumentationsportal (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Portierungsrichtlinie HoloToolkit zu MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
