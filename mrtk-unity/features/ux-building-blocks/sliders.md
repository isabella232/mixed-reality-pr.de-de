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
# <a name="sliders"></a><span data-ttu-id="1561a-104">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="1561a-104">Sliders</span></span>

![Schiebereglerbeispiel](../images/slider/MRTK_UX_Slider_Main.jpg)

<span data-ttu-id="1561a-106">Schieberegler sind Benutzeroberflächenkomponenten, mit denen Sie einen Wert kontinuierlich ändern können, indem Sie einen Schieberegler auf einer Spur bewegen. Derzeit kann der Schieberegler "Heften" verschoben werden, indem der Schieberegler direkt oder in der Entfernung angeheftet wird.</span><span class="sxs-lookup"><span data-stu-id="1561a-106">Sliders are UI components that allow you to continuously change a value by moving a slider on a track. Currently the Pinch Slider can be moved by directly grabbing the slider, either directly or at a distance.</span></span> <span data-ttu-id="1561a-107">Schieberegler arbeiten mit AR und VR und verwenden Motion-Controller, Hände oder Geste und Stimme.</span><span class="sxs-lookup"><span data-stu-id="1561a-107">Sliders work on AR and VR, using motion controllers, hands, or Gesture + Voice.</span></span>

## <a name="example-scene"></a><span data-ttu-id="1561a-108">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="1561a-108">Example scene</span></span>

<span data-ttu-id="1561a-109">Beispiele finden Sie in der **SliderExample-Szene** unter `MRTK/Examples/Demos/UX/Slider/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="1561a-109">You can find examples in the **SliderExample** scene under `MRTK/Examples/Demos/UX/Slider/Scenes/`.</span></span>

## <a name="how-to-use-sliders"></a><span data-ttu-id="1561a-110">Verwenden von Schiebereglern</span><span class="sxs-lookup"><span data-stu-id="1561a-110">How to use sliders</span></span>

<span data-ttu-id="1561a-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span><span class="sxs-lookup"><span data-stu-id="1561a-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span></span> <span data-ttu-id="1561a-112">Wenn Sie einen eigenen Schieberegler ändern oder erstellen möchten, denken Sie daran, folgende Schritte zu unternehmen:</span><span class="sxs-lookup"><span data-stu-id="1561a-112">If you want to modify or create your own slider, remember to do the following:</span></span>

- <span data-ttu-id="1561a-113">Stellen Sie sicher, dass Ihr Thumb-Objekt über einen Collider verfügt.</span><span class="sxs-lookup"><span data-stu-id="1561a-113">Make sure your that your thumb object has a collider on it.</span></span> <span data-ttu-id="1561a-114">Im PinchSlider-Prefab ist der Collider ein `SliderThumb/Button_AnimationContainer/Slider_Button`</span><span class="sxs-lookup"><span data-stu-id="1561a-114">In the PinchSlider prefab, the collider is on `SliderThumb/Button_AnimationContainer/Slider_Button`</span></span>
- <span data-ttu-id="1561a-115">Stellen Sie sicher, dass das Objekt, das den Collider enthält, auch über eine Nahinteraktions-Grabbable-Komponente verfügt, wenn Sie den Schieberegler in der Nähe greifen möchten.</span><span class="sxs-lookup"><span data-stu-id="1561a-115">Make sure that the object containing the collider also has a Near Interaction Grabbable component on it, if you want to be able to grab the slider near.</span></span>

<span data-ttu-id="1561a-116">Es wird auch empfohlen, die folgende Hierarchie zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="1561a-116">We also recommend using the following hierarchy</span></span>

- <span data-ttu-id="1561a-117">PinchSlider: Enthält den SliderComponent</span><span class="sxs-lookup"><span data-stu-id="1561a-117">PinchSlider - Contains the sliderComponent</span></span>
  - <span data-ttu-id="1561a-118">TouchCollider: Collider, der den gesamten auswählbaren Bereich des Schiebereglers enthält.</span><span class="sxs-lookup"><span data-stu-id="1561a-118">TouchCollider - Collider containing the entire selectable area of the slider.</span></span> <span data-ttu-id="1561a-119">Aktiviert das Snap-To-Position-Verhalten.</span><span class="sxs-lookup"><span data-stu-id="1561a-119">Enables the Snap To Position behavior.</span></span>
  - <span data-ttu-id="1561a-120">SliderThumb: Enthält den verschiebbaren Daumen</span><span class="sxs-lookup"><span data-stu-id="1561a-120">SliderThumb - Contains the movable thumb</span></span>
  - <span data-ttu-id="1561a-121">TrackVisuals: Enthält die Spur und alle anderen Visuals.</span><span class="sxs-lookup"><span data-stu-id="1561a-121">TrackVisuals - Containing the track and any other visuals</span></span>
  - <span data-ttu-id="1561a-122">OtherVisuals: Enthält alle anderen Visuals.</span><span class="sxs-lookup"><span data-stu-id="1561a-122">OtherVisuals - Containing any other visuals</span></span>

## <a name="slider-events"></a><span data-ttu-id="1561a-123">Schiebereglerereignisse</span><span class="sxs-lookup"><span data-stu-id="1561a-123">Slider events</span></span>

<span data-ttu-id="1561a-124">Schieberegler machen die folgenden Ereignisse verfügbar:</span><span class="sxs-lookup"><span data-stu-id="1561a-124">Sliders expose the following events:</span></span>

- <span data-ttu-id="1561a-125">OnValueUpdated: Wird aufgerufen, wenn sich der Schiebereglerwert ändert.</span><span class="sxs-lookup"><span data-stu-id="1561a-125">OnValueUpdated - Called whenever the slider value changes</span></span>
- <span data-ttu-id="1561a-126">OnInteractionStarted: Wird aufgerufen, wenn der Benutzer den Schieberegler greift</span><span class="sxs-lookup"><span data-stu-id="1561a-126">OnInteractionStarted - Called when the user grabs the slider</span></span>
- <span data-ttu-id="1561a-127">OnInteractionEnded: Wird aufgerufen, wenn der Benutzer den Schieberegler freilässt</span><span class="sxs-lookup"><span data-stu-id="1561a-127">OnInteractionEnded - Called when the user releases the slider</span></span>
- <span data-ttu-id="1561a-128">OnHoverEntered: Wird aufgerufen, wenn die Hand bzw. der Controller des Benutzers über den Schieberegler mit der Nah- oder Ferninteraktion geschwebt wird.</span><span class="sxs-lookup"><span data-stu-id="1561a-128">OnHoverEntered - Called when the user's hand / controller hovers over the slider, using either near or far interaction.</span></span>
- <span data-ttu-id="1561a-129">OnHoverExited: Wird aufgerufen, wenn sich die Hand/der Controller des Benutzers nicht mehr in der Nähe des Schiebereglers befindet.</span><span class="sxs-lookup"><span data-stu-id="1561a-129">OnHoverExited - Called when the user's hand / controller is no longer near the slider.</span></span>

## <a name="configuring-slider-bound-and-axis"></a><span data-ttu-id="1561a-130">Konfigurieren von Schieberegler und Achse</span><span class="sxs-lookup"><span data-stu-id="1561a-130">Configuring slider bound and axis</span></span>

<span data-ttu-id="1561a-131">Sie können den Start- und den Endpunkt des Schiebereglers direkt verschieben, indem Sie die Ziehpunkte in der Szene verschieben:</span><span class="sxs-lookup"><span data-stu-id="1561a-131">You can directly move the starting and end points of the slider by moving the handles in the Scene:</span></span>

![Schiebereglerkonfiguration](../images/sliders/MRTK_Sliders_Setup.png)

<span data-ttu-id="1561a-133">Sie können auch die Achse (im lokalen Raum) des Schiebereglers über das Feld _Schiebereglerachse_ angeben.</span><span class="sxs-lookup"><span data-stu-id="1561a-133">You can also specify the axis (in local space) of the slider via the _Slider Axis_ field</span></span>

<span data-ttu-id="1561a-134">Wenn Sie die Ziehpunkte nicht verwenden können, können Sie stattdessen die Start- und Endpunkte des Schiebereglers über die Felder _Schieberegler_ start Distance und _Slider End Distance angeben._</span><span class="sxs-lookup"><span data-stu-id="1561a-134">If you cannot use the handles, you can instead specify the start and end points of the slider via the _Slider Start Distance_ and _Slider End Distance_ fields.</span></span> <span data-ttu-id="1561a-135">Diese geben die Start-/Endposition des Schiebereglers als Abstand vom Mittelpunkt des Schiebereglers in lokalen Koordinaten an.</span><span class="sxs-lookup"><span data-stu-id="1561a-135">These specify start / end position of slider as a distance from the slider's center, in local coordinates.</span></span> <span data-ttu-id="1561a-136">Dies bedeutet, dass Sie den Schieberegler nach Bedarf so skalieren können, dass er kleiner oder größer ist, ohne die Start- und Endentfernungen aktualisieren zu müssen.</span><span class="sxs-lookup"><span data-stu-id="1561a-136">This means that once you set the slider start and end distances as you want them, you can scale the slider to be smaller or larger without needing to update the start and end distances.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="1561a-137">Inspektoreigenschaften</span><span class="sxs-lookup"><span data-stu-id="1561a-137">Inspector properties</span></span>

<span data-ttu-id="1561a-138">**Thumb Root** Das Gameobject, das den Schiebereglerfinger enthält.</span><span class="sxs-lookup"><span data-stu-id="1561a-138">**Thumb Root** The gameobject that contains the slider thumb.</span></span>

<span data-ttu-id="1561a-139">**An Position ausrichten** Gibt an, ob dieser Schieberegler an der angegebenen Position auf dem Schieberegler positioniert wird</span><span class="sxs-lookup"><span data-stu-id="1561a-139">**Snap To Position** Whether or not this slider snaps to the designated position on the slider</span></span>

<span data-ttu-id="1561a-140">**Ist berührbar** Gibt an, ob dieser Schieberegler über Touchereignisse steuerbar ist.</span><span class="sxs-lookup"><span data-stu-id="1561a-140">**Is Touchable** Whether or not this slider is controllable via touch events</span></span>

<span data-ttu-id="1561a-141">**Thumb Collider** Der Collider, der den Schiebereglerfinger steuert</span><span class="sxs-lookup"><span data-stu-id="1561a-141">**Thumb Collider** The collider that controls the slider thumb</span></span>

<span data-ttu-id="1561a-142">**Touchfähiger Collider** Der Bereich des Schiebereglers, der berührt oder ausgewählt werden kann, wenn An Position ausrichten true ist.</span><span class="sxs-lookup"><span data-stu-id="1561a-142">**Touchable Collider** The area of the slider that can be touched or selected when Snap To Position is true.</span></span>

<span data-ttu-id="1561a-143">**Schiebereglerwert** Der Wert des Schiebereglers.</span><span class="sxs-lookup"><span data-stu-id="1561a-143">**Slider Value** The value of the slider.</span></span>

<span data-ttu-id="1561a-144">**Verwenden von Schiebereglerschritten** Steuert, ob dieser Schieberegler in Schritten oder kontinuierlich inkrementiert wird.</span><span class="sxs-lookup"><span data-stu-id="1561a-144">**Use Slider Step Divisions** Controls whether this slider is increments in steps or continuously.</span></span>

<span data-ttu-id="1561a-145">**Schiebereglerschritte** Die Anzahl der Unterteilungen, in die der Schieberegler aufgeteilt wird, wenn Schiebereglerschrittbereiche verwenden aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="1561a-145">**Slider Step Divisions** Number of subdivisions the slider is split into when Use Slider Step Divisions is enabled.</span></span>

<span data-ttu-id="1561a-146">**Nachverfolgen von Visuals** Das Gameobject, das die gewünschten Trackvisu visuals enthält, die sich entlang des Schiebereglers befinden.</span><span class="sxs-lookup"><span data-stu-id="1561a-146">**Track Visuals** The gameobject that contains the desired track visuals that goes along the slider.</span></span>

<span data-ttu-id="1561a-147">**Teilstriche** Das Gameobject, das die gewünschten Teilstriche enthält, die sich entlang des Schiebereglers befinden.</span><span class="sxs-lookup"><span data-stu-id="1561a-147">**Tick Marks** The gameobject that contains the desired tick marks that goes along the slider.</span></span>

<span data-ttu-id="1561a-148">**Visuelle Thumb-Elemente** Das Gameobject, das das gewünschte Thumb-Visual enthält, das den Schieberegler durchläuft.</span><span class="sxs-lookup"><span data-stu-id="1561a-148">**Thumb Visuals** The gameobject that contains the desired thumb visual that goes along the slider.</span></span>

<span data-ttu-id="1561a-149">**Schiebereglerachse** Die Achse, auf der der Schieberegler bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="1561a-149">**Slider Axis** The axis the slider moves along.</span></span>

<span data-ttu-id="1561a-150">**Schieberegler : Startabstand** An der Stelle, an der der Schieberegler als Abstand vom Mittelpunkt entlang der Schiebereglerachse beginnt, in einheiten des lokalen Raums.</span><span class="sxs-lookup"><span data-stu-id="1561a-150">**Slider Start Distance** Where the slider track starts, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="1561a-151">**Schieberegler– Endabstand** An der Stelle, an der die Schiebereglerspur endet, als Abstand vom Mittelpunkt entlang der Schiebereglerachse in einheiten des lokalen Raums.</span><span class="sxs-lookup"><span data-stu-id="1561a-151">**Slider End Distance** Where the slider track ends, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="1561a-152">Wenn der Benutzer den Wert der Schiebereglerachse im Editor aktualisiert, wird die Transformation aktualisiert, wenn Visuelle Elemente nachverfolgen oder Visuelle Teilstriche angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="1561a-152">When user updates the slider axis value in editor then if Track Visuals or Tick Visuals are specified then their transform is updated.</span></span>
<span data-ttu-id="1561a-153">Insbesondere wird ihre lokale Position zurückgesetzt, und ihre lokale Drehung wird auf die Ausrichtung der Schiebereglerachse festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1561a-153">Specifically, their local position is reset and their local rotation is set to match the Slider Axis orientation.</span></span>
<span data-ttu-id="1561a-154">Die Skalierung wird nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="1561a-154">Their scale isn't modified.</span></span>
<span data-ttu-id="1561a-155">Wenn Teilstriche über eine Grid Object Collection-Komponente verfügen, werden Layout und CellWidth oder CellHeight entsprechend der Schiebereglerachse aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="1561a-155">If Tick Marks have a Grid Object Collection component then the Layout and CellWidth or CellHeight is updated accordingly to match the Slider Axis.</span></span>

## <a name="example-slider-configurations"></a><span data-ttu-id="1561a-156">Beispielkonfigurationen für Schieberegler</span><span class="sxs-lookup"><span data-stu-id="1561a-156">Example Slider Configurations</span></span>

<span data-ttu-id="1561a-157">Kontinuierliche Schieberegler mit fortlaufenden Schiebereglern für Ausrichtung ![ an Position](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span><span class="sxs-lookup"><span data-stu-id="1561a-157">Continuous Sliders with Snap To Position ![Continuous Sliders](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span></span>

<span data-ttu-id="1561a-158">Schrittschieberegler mit Ausrichtung an Position</span><span class="sxs-lookup"><span data-stu-id="1561a-158">Step Sliders with Snap To Position</span></span>

![Schrittschieberegler](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

<span data-ttu-id="1561a-160">Touchschieberegler</span><span class="sxs-lookup"><span data-stu-id="1561a-160">Touch Sliders</span></span>

![Touchschieberegler](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)