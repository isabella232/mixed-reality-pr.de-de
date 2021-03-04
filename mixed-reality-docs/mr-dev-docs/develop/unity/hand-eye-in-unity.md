---
title: Hand-und Augen Nachverfolgung in Unity
description: Erfahren Sie mehr über die beiden wichtigen Möglichkeiten, um ihre Blicke in Unity, Handgesten und Bewegungs Controllern zu übernehmen.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Gesten, Bewegungs Controller, Unity, Blick, Eingabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 8c1ab88358f4218fadce9b7a2a0dbd179b680eab
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759756"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Hand-und Augen Nachverfolgung in Unity

Hololens 2 hat einige neue und interessante Funktionen eingeführt, wie z. b. die Hand-und Eye-Nachverfolgung.

Die einfachste Möglichkeit, die neue Funktion in Unity nutzen zu können, ist mrtk. Es gibt auch einige Beispiel Szenen, die Ihnen den Einstieg erleichtern.

* [Beginnen Sie mit der Hand in mrtk](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/hand-tracking.md)
* [Einstieg in die Eye-Nachverfolgung in mrtk](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-main.md)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Bausteine, die Hände, Augen und andere in mrtk unterstützen 

Mrtk v2 bietet eine Reihe von UI-Steuerelementen und-Blöcken, die Ihnen helfen, ihre Entwicklung zu beschleunigen.

|  [ ![ Schalt](images/MRTK_Button_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) Fläche [Schaltfläche](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) | [ ![ Begrenzungs](images/MRTK_BoundingBox_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md) Feld des umgebenden Felds [](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md) | Bearbeitungs [Handler für](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/manipulation-handler.md) [ ![ Manipulations Handler](images/MRTK_Manipulation_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/manipulation-handler.md) |
|:--- | :--- | :--- |
| Ein Schaltflächen-Steuerelement, das verschiedene Eingabemethoden unterstützt, einschließlich HoloLens2's-Handgelenk | Standard Benutzeroberfläche zum Bearbeiten von Objekten im 3D-Raum | Skript für die Bearbeitung von Objekten mit einem oder zwei Händen |
|  [ ![ Slate](images/MRTK_Slate_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/slate.md) - [Slate](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/slate.md) | [Tastatur](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/system-keyboard.md) System [ ![ Tastatur](images/MRTK_SystemKeyboard_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/system-keyboard.md) | [ ![ Interactable](images/InteractableExamples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md) - [interactable](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md) |
| 2D-Stilebene, die den Bildlauf mit der Hand Eingabe unterstützt | Beispielskript für die Verwendung der System Tastatur in Unity  | Ein Skript für die Interaktion von Objekten mit visuellen Zuständen und Designunterstützung |
|  [ ![ Solver](images/MRTK_Solver_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) - [Solver](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) | [ ![ Objekt](images/MRTK_ObjectCollection_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-collection.md) [Sammlungsobjekt Auflistung](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-collection.md) | [ ![ ](images/MRTK_Tooltip_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/tooltip.md) QuickInfo [](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/tooltip.md) |
| Verschiedene objektpositionierungsverhaltensweisen, wie z. b. Tag-entlang, Text Sperre, Konstante Ansichts Größe und Oberflächen Magnetismus | Skript für das Layout eines Arrays von Objekten in einer dreidimensionalen Form | Annotation-Benutzeroberfläche mit flexiblem Anker/Pivot-System, das zum bezeichnen von Bewegungs Controllern und Objekten verwendet werden kann. |
|  [ ![ App-Leiste App](images/MRTK_AppBar_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/app-bar.md) [-Leiste](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/app-bar.md) | [ ![ Zeiger](images/MRTK_Pointer_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md) [Zeiger](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md) | QuickInfo [ ![ -Visualisierung](images/MRTK_FingertipVisualization_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/fingertip-visualization.md) [Fingertip-Visualisierung](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/fingertip-visualization.md) |
| Die Benutzeroberfläche für die manuelle Aktivierung des umgebenden Felds. | Weitere Informationen zu verschiedenen Zeiger Typen | Visuelles Element im Fingertipp, das die Zuverlässigkeit der direkten Interaktion verbessert |
|  [ ![ Augen Verfolgung: Ziel](images/mrtk_et_targetselect.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-target-selection.md) Auswahl [Auge Verfolgung: Zielauswahl](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-target-selection.md) | [ ![ Eye Tracking: Navigation im Navigations](images/mrtk_et_navigation.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-navigation.md) Bereich [: Navigation](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-navigation.md) | [ ![ Augen Verfolgung: Heat Map](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [Eye Tracking: Heat Map](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Kombinieren Sie Augen, Stimme und Hand Eingaben, um schnell und unkompliziert holograms in Ihrer Szene auszuwählen. | Erfahren Sie, wie Sie den Text automatisch Scrollen oder basierend auf dem, was Sie sehen, Inhalte mit Fokus vergrößern.| Beispiele für das Protokollieren, laden und visualisieren, was Benutzer in Ihrer APP betrachtet haben |

## <a name="example-scenes"></a>Beispiel Szenen

Erkunden Sie die verschiedenen Arten von Interaktionen und UI-Steuerelementen von mrtk in [dieser Beispiel Szene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

Weitere Beispiel Szenen finden Sie im [Mixed Reality Toolkit GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) unter **Assets/mixedrealitytoolkit. examples/Demos** Folder.

[![Beispiel Szene](images/MRTK_Examples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/example-scenes/hand-interaction-examples.md)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Journey folgen, die wir angelegt haben, befinden Sie sich mitten in der Untersuchung der mrtk Core-Bausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

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
* [Unityengine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [Unityengine. XR. inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
