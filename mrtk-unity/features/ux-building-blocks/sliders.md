---
title: Schieberegler
description: Übersicht über Schieberegler MRTK
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Schieberegler,
ms.openlocfilehash: de95201f381a148defe668ead03c16fac5b3ba4ff3674487057f9227cbe6efba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209534"
---
# <a name="sliders"></a>Schieberegler

![Beispiel für Schieberegler](../images/slider/MRTK_UX_Slider_Main.jpg)

Schieberegler sind Benutzeroberflächenkomponenten, mit denen Sie einen Wert kontinuierlich ändern können, indem Sie einen Schieberegler auf eine Spur verschieben. Derzeit kann der Schieberegler zum Anheften bewegt werden, indem der Schieberegler direkt oder in einer Entfernung gepackt wird. Schieberegler arbeiten mit AR und VR mit Motion-Controllern, Händen oder Geste + Stimme.

## <a name="example-scene"></a>Beispielszene

Beispiele finden Sie in der **SliderExample-Szene** unter `MRTK/Examples/Demos/UX/Slider/Scenes/` .

## <a name="how-to-use-sliders"></a>Verwenden von Schiebereglern

Drag and drop the **PinchSlider** prefab into the scene hierarchy. Wenn Sie einen eigenen Schieberegler ändern oder erstellen möchten, denken Sie daran, Folgendes zu tun:

- Stellen Sie sicher, dass ihr Thumb-Objekt über einen Collider verfügt. Im PinchSlider-Prefab ist der Collider eingeschaltet. `SliderThumb/Button_AnimationContainer/Slider_Button`
- Stellen Sie sicher, dass das Objekt, das den Collider enthält, auch über eine Near Interaction Grabbable-Komponente verfügt, wenn Sie den Schieberegler in der Nähe greifen möchten.

Es wird auch empfohlen, die folgende Hierarchie zu verwenden.

- PinchSlider : Enthält den SliderComponent
  - TouchCollider: Collider, der den gesamten auswählbaren Bereich des Schiebereglers enthält. Aktiviert das Verhalten "An Position ausrichten".
  - SliderThumb: Enthält den verschiebbaren Daumen
  - TrackVisuals: Enthält die Spur und alle anderen Visuals
  - OtherVisuals: Enthält alle anderen Visuals

## <a name="slider-events"></a>Schiebereglerereignisse

Schieberegler machen die folgenden Ereignisse verfügbar:

- OnValueUpdated: Wird immer dann aufgerufen, wenn sich der Schiebereglerwert ändert.
- OnInteractionStarted: Wird aufgerufen, wenn der Benutzer den Schieberegler greift
- OnInteractionEnded: Wird aufgerufen, wenn der Benutzer den Schieberegler freigibt.
- OnHoverEntered: Wird aufgerufen, wenn die Hand/der Controller des Benutzers mithilfe einer Nah- oder Ferninteraktion auf den Schieberegler zusteuert.
- OnHoverExited: Wird aufgerufen, wenn sich die Hand/der Controller des Benutzers nicht mehr in der Nähe des Schiebereglers befindet.

## <a name="configuring-slider-bound-and-axis"></a>Konfigurieren der Begrenzung und Achse des Schiebereglers

Sie können die Start- und Endpunkte des Schiebereglers direkt verschieben, indem Sie die Ziehpunkte in der Szene verschieben:

![Schiebereglerkonfiguration](../images/sliders/MRTK_Sliders_Setup.png)

Sie können auch die Achse (im lokalen Raum) des Schiebereglers über das Feld _Schiebereglerachse_ angeben.

Wenn Sie die Handles nicht verwenden können, können Sie stattdessen die Start- und Endpunkte des Schiebereglers über die Felder Startabstand des _Schiebereglers_ und _Schieberegler-Endentfernung_ angeben. Diese geben die Start-/Endposition des Schiebereglers als Abstand vom Mittelpunkt des Schiebereglers in lokalen Koordinaten an. Das bedeutet, dass Sie nach dem Festlegen der Start- und Endentfernungen des Schiebereglers den Schieberegler so skalieren können, dass er kleiner oder größer ist, ohne die Start- und Endentfernungen aktualisieren zu müssen.

## <a name="inspector-properties"></a>Inspektoreigenschaften

**Thumb Root** Das Gameobject, das den Schieberegler enthält.

**An Position ausrichten** Gibt an, ob dieser Schieberegler an der angegebenen Position auf dem Schieberegler ausgerichtet wird oder nicht.

**Ist touchierbar** Gibt an, ob dieser Schieberegler über Touchereignisse steuerbar ist.

**Thumb Collider** Der Collider, der den Schieberegler steuert

**Touchierbarer Collider** Der Bereich des Schiebereglers, der berührt oder ausgewählt werden kann, wenn An Position ausrichten true ist.

**Schiebereglerwert** Der Wert des Schiebereglers.

**Verwenden von Schieberegler-Schrittbereichen** Steuert, ob dieser Schieberegler schrittweise oder kontinuierlich erhöht wird.

**Schiebereglerschritte** Anzahl der Unterbereiche, in die der Schieberegler aufgeteilt wird, wenn Schiebereglerschrittbereiche verwenden aktiviert ist.

**Nachverfolgen von Visuals** Das Gameobject, das die gewünschten Trackvisuals enthält, die entlang des Schiebereglers verläuft.

**Teilstriche** Das Gameobject, das die gewünschten Teilstriche enthält, die entlang des Schiebereglers verläuft.

**Daumenvisuals** Das Gameobject, das das gewünschte Daumenvisual enthält, das entlang des Schiebereglers verläuft.

**Schiebereglerachse** Die Achse, auf der sich der Schieberegler bewegt.

**Startabstand des Schiebereglers** An der Stelle, an der die Schiebereglerspur beginnt, als Abstand vom Mittelpunkt entlang der Schiebereglerachse in lokalen Raumeinheiten.

**Endabstand des Schiebereglers** An der Stelle, an der die Schiebereglerspur endet, als Abstand von der Mitte entlang der Schiebereglerachse in lokalen Raumeinheiten.

Wenn der Benutzer den Wert der Schiebereglerachse im Editor aktualisiert, wird die Transformation aktualisiert, wenn Visuals nachverfolgen oder Visuelle Teilstriche angegeben sind.
Insbesondere wird die lokale Position zurückgesetzt, und die lokale Drehung wird so festgelegt, dass sie der Ausrichtung der Schiebereglerachse entspricht.
Ihre Skalierung wird nicht geändert.
Wenn Teilstriche über eine Grid Object Collection-Komponente verfügen, werden Layout und CellWidth oder CellHeight entsprechend der Schiebereglerachse aktualisiert.

## <a name="example-slider-configurations"></a>Beispielkonfigurationen für Schieberegler

Kontinuierliche Schieberegler mit Andocken zum Positionieren ![ von fortlaufenden Schiebereglern](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)

Schrittschieberegler mit Ausrichtung an Position

![Schrittschieberegler](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

Touchschieberegler

![Touchschieberegler](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)
