---
title: Schieberegler
description: Übersicht über Schieberegler MRTK
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Schieberegler,
ms.openlocfilehash: be19806e0202f6cb3ddcea1a80c2c40811aff4f2
ms.sourcegitcommit: e9661d3bab061f9499134226ef3b87751ec56277
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "112426876"
---
# <a name="sliders"></a>Schieberegler

![Schiebereglerbeispiel](../images/slider/MRTK_UX_Slider_Main.jpg)

Schieberegler sind Benutzeroberflächenkomponenten, mit denen Sie einen Wert kontinuierlich ändern können, indem Sie einen Schieberegler auf einer Spur bewegen. Derzeit kann der Schieberegler "Heften" verschoben werden, indem der Schieberegler direkt oder in der Entfernung angeheftet wird. Schieberegler arbeiten mit AR und VR und verwenden Motion-Controller, Hände oder Geste und Stimme.

## <a name="example-scene"></a>Beispielszene

Beispiele finden Sie in der **SliderExample-Szene** unter `MRTK/Examples/Demos/UX/Slider/Scenes/` .

## <a name="how-to-use-sliders"></a>Verwenden von Schiebereglern

Drag and drop the **PinchSlider** prefab into the scene hierarchy. Wenn Sie einen eigenen Schieberegler ändern oder erstellen möchten, denken Sie daran, folgende Schritte zu unternehmen:

- Stellen Sie sicher, dass Ihr Thumb-Objekt über einen Collider verfügt. Im PinchSlider-Prefab ist der Collider ein `SliderThumb/Button_AnimationContainer/Slider_Button`
- Stellen Sie sicher, dass das Objekt, das den Collider enthält, auch über eine Nahinteraktions-Grabbable-Komponente verfügt, wenn Sie den Schieberegler in der Nähe greifen möchten.

Es wird auch empfohlen, die folgende Hierarchie zu verwenden:

- PinchSlider: Enthält den SliderComponent
  - TouchCollider: Collider, der den gesamten auswählbaren Bereich des Schiebereglers enthält. Aktiviert das Snap-To-Position-Verhalten.
  - SliderThumb: Enthält den verschiebbaren Daumen
  - TrackVisuals: Enthält die Spur und alle anderen Visuals.
  - OtherVisuals: Enthält alle anderen Visuals.

## <a name="slider-events"></a>Schiebereglerereignisse

Schieberegler machen die folgenden Ereignisse verfügbar:

- OnValueUpdated: Wird aufgerufen, wenn sich der Schiebereglerwert ändert.
- OnInteractionStarted: Wird aufgerufen, wenn der Benutzer den Schieberegler greift
- OnInteractionEnded: Wird aufgerufen, wenn der Benutzer den Schieberegler freilässt
- OnHoverEntered: Wird aufgerufen, wenn die Hand bzw. der Controller des Benutzers über den Schieberegler mit der Nah- oder Ferninteraktion geschwebt wird.
- OnHoverExited: Wird aufgerufen, wenn sich die Hand/der Controller des Benutzers nicht mehr in der Nähe des Schiebereglers befindet.

## <a name="configuring-slider-bound-and-axis"></a>Konfigurieren von Schieberegler und Achse

Sie können den Start- und den Endpunkt des Schiebereglers direkt verschieben, indem Sie die Ziehpunkte in der Szene verschieben:

![Schiebereglerkonfiguration](../images/sliders/MRTK_Sliders_Setup.png)

Sie können auch die Achse (im lokalen Raum) des Schiebereglers über das Feld _Schiebereglerachse_ angeben.

Wenn Sie die Ziehpunkte nicht verwenden können, können Sie stattdessen die Start- und Endpunkte des Schiebereglers über die Felder _Schieberegler_ start Distance und _Slider End Distance angeben._ Diese geben die Start-/Endposition des Schiebereglers als Abstand vom Mittelpunkt des Schiebereglers in lokalen Koordinaten an. Dies bedeutet, dass Sie den Schieberegler nach Bedarf so skalieren können, dass er kleiner oder größer ist, ohne die Start- und Endentfernungen aktualisieren zu müssen.

## <a name="inspector-properties"></a>Inspektoreigenschaften

**Thumb Root** Das Gameobject, das den Schiebereglerfinger enthält.

**An Position ausrichten** Gibt an, ob dieser Schieberegler an der angegebenen Position auf dem Schieberegler positioniert wird

**Ist berührbar** Gibt an, ob dieser Schieberegler über Touchereignisse steuerbar ist.

**Thumb Collider** Der Collider, der den Schiebereglerfinger steuert

**Touchfähiger Collider** Der Bereich des Schiebereglers, der berührt oder ausgewählt werden kann, wenn An Position ausrichten true ist.

**Schiebereglerwert** Der Wert des Schiebereglers.

**Verwenden von Schiebereglerschritten** Steuert, ob dieser Schieberegler in Schritten oder kontinuierlich inkrementiert wird.

**Schiebereglerschritte** Die Anzahl der Unterteilungen, in die der Schieberegler aufgeteilt wird, wenn Schiebereglerschrittbereiche verwenden aktiviert ist.

**Nachverfolgen von Visuals** Das Gameobject, das die gewünschten Trackvisu visuals enthält, die sich entlang des Schiebereglers befinden.

**Teilstriche** Das Gameobject, das die gewünschten Teilstriche enthält, die sich entlang des Schiebereglers befinden.

**Visuelle Thumb-Elemente** Das Gameobject, das das gewünschte Thumb-Visual enthält, das den Schieberegler durchläuft.

**Schiebereglerachse** Die Achse, auf der der Schieberegler bewegt wird.

**Schieberegler : Startabstand** An der Stelle, an der der Schieberegler als Abstand vom Mittelpunkt entlang der Schiebereglerachse beginnt, in einheiten des lokalen Raums.

**Schieberegler– Endabstand** An der Stelle, an der die Schiebereglerspur endet, als Abstand vom Mittelpunkt entlang der Schiebereglerachse in einheiten des lokalen Raums.

Wenn der Benutzer den Wert der Schiebereglerachse im Editor aktualisiert, wird die Transformation aktualisiert, wenn Visuelle Elemente nachverfolgen oder Visuelle Teilstriche angegeben werden.
Insbesondere wird ihre lokale Position zurückgesetzt, und ihre lokale Drehung wird auf die Ausrichtung der Schiebereglerachse festgelegt.
Die Skalierung wird nicht geändert.
Wenn Teilstriche über eine Grid Object Collection-Komponente verfügen, werden Layout und CellWidth oder CellHeight entsprechend der Schiebereglerachse aktualisiert.

## <a name="example-slider-configurations"></a>Beispielkonfigurationen für Schieberegler

Kontinuierliche Schieberegler mit fortlaufenden Schiebereglern für Ausrichtung ![ an Position](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)

Schrittschieberegler mit Ausrichtung an Position

![Schrittschieberegler](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

Touchschieberegler

![Touchschieberegler](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)