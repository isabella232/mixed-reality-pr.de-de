---
title: Artikulierte Hand- und Blickverfolgung in Unity
description: Erfahren Sie mehr über die beiden wichtigsten Möglichkeiten zum Ergreifen von Aktionen beim Anvieren in Unity, Handgesten und Motion-Controller.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Gesten, Motion-Controller, Unity, Anvisiert, Eingabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 005b817574e6d3600b9c43e443432203418b58a2258e2938614cc549ab7539c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223836"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Artikulierte Hand- und Blickverfolgung in Unity

HoloLens 2 wurden einige neue und interessante Funktionen eingeführt, z. B. artikulierte Hand- und Blickverfolgung.

Die einfachste Möglichkeit, die neue Funktion in Unity zu nutzen, ist MRTK. Es gibt auch einige Beispielszenen, die Ihnen den Einstieg erleichtern.

* [Erste Schritte mit artikulierter Hand im MRTK](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [Erste Schritte mit Eye Tracking in MRTK](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Bausteine zur Unterstützung von Händen, Augen und anderen Personen im MRTK

MRTK v2 bietet eine Reihe von Ui-Steuerelementen und Bausteinen, die Ihnen helfen, Ihre Entwicklung zu beschleunigen.

|  [![Schaltfläche](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [Schaltfläche](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | [ ![ Begrenzungsfeld](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) [begrenzungsfeld](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) | [ ![ Manipulation Handler](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) [Manipulation Handler](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| Ein Schaltflächensteuerelement, das verschiedene Eingabemethoden unterstützt, einschließlich der artikulierten Hand von HoloLens2 | Standard Benutzeroberfläche zum Bearbeiten von Objekten im 3D-Raum | Skript zum Manipulieren von Objekten mit einer oder zwei Händen. |
|  [![Slate](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [Slate](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [![Systemtastatur](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) [Systemtastatur](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [![Interaktionsfähig](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [Interaktionsfähig](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| 2D-Stilebene, die Scrollen mit artikulierten Handeingaben unterstützt | Beispielskript für die Verwendung der Systemtastatur in Unity  | Ein Skript, um Objekte interaktionsfähig zu machen, mit visuellen Zuständen und Designunterstützung. |
|  [![Solver](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [Solver](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [![Objektsammlung](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) [Objektsammlung](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [![QuickInfo](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [QuickInfo](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| Verschiedene Objektpositionierungsverhalten, z. B. Tag-Along, Body-Lock, konstante Ansichtsgröße und Oberflächen-Magnetismus | Skript für das Layout eines Arrays von Objekten in einer dreidimensionalen Form | Anmerkungsbenutzeroberfläche mit flexiblem Anker-/Pivotsystem, das zum Bezeichnen von Motion-Controllern und -Objekten verwendet werden kann. |
|  [![App-Leiste](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [App-Leiste](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [![ Zeiger](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [Zeiger](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [![Fingerspitzenvisualisierung](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [Fingerspitzenvisualisierung](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| Benutzeroberfläche für die manuelle Aktivierung von Bounding Box | Erfahren Sie mehr über verschiedene Typen von Zeigern. | Visuelles Erscheinungsbild auf der Fingerspitze, wodurch die Zuverlässigkeit für die direkte Interaktion verbessert wird |
|  [![Eyetracking: Zielauswahl](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [Eyetracking: Zielauswahl](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [![Eyetracking: Navigation](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [Eyetracking: Navigation](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) |
| Kombinieren von Augen, Stimmen und Handeingaben, um Hologramme schnell und mühelos in Ihrer gesamten Szene auszuwählen | Erfahren Sie, wie Sie basierend auf dem, was Sie sich ansehen, Text automatisch scrollen oder fokussierte Inhalte vergrößern.| Beispiele für protokollieren, laden und visualisieren, was Benutzer in Ihrer App betrachtet haben |

## <a name="example-scenes"></a>Beispielszenen

Erkunden Sie die verschiedenen Arten von Interaktionen und Benutzeroberflächen-Steuerelementen des MRTK in [dieser Beispielszene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples).

Weitere Beispielszenen finden Sie in [Mixed Reality Toolkit GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) im Ordner **Assets/MixedRealityToolkit.Examples/Demos.**

[![Beispielszene](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, befinden Sie sich in der Mitte der MRTK-Kernbausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Räumliche Zuordnung](spatial-mapping-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch

* [Augenbasierte Interaktion](../../design/eye-gaze-interaction.md)
* [Blickverfolgung auf HoloLens 2](../../design/eye-tracking.md)
* [Anvisieren und Ausführen](../../design/gaze-and-commit.md)
* [Hände – Direkte Manipulation](../../design/direct-manipulation.md)
* [Hände – Gesten](../../design/gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](../../design/point-and-commit.md)
* [Instinktive Interaktionen](../../design/interaction-fundamentals.md)
* [Motion-Controller](../../design/motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)