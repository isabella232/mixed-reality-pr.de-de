---
title: Interaktionsfähiges Objekt
description: Erfahren Sie, wie Sie Ereignisse Auslösers, visuelle Hinweise bereitstellen und mit Objekten in ihren gemischten Reality-Anwendungen interagieren.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Gemischte Realität, Steuerelemente, Interaktion, Cues, UI, UX, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Audio
ms.openlocfilehash: 0e9f4dc09e3c4a4c38ffeb1a9042f39996918e36
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300465"
---
# <a name="interactable-object"></a><span data-ttu-id="40ae4-104">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="40ae4-104">Interactable object</span></span>

![Objekte mit Interaktivität](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="40ae4-106">Eine Schaltfläche ist lange eine Metapher, die zum Auslösen eines Ereignisses in der 2D-abstrakten Welt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="40ae4-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="40ae4-107">In der dreidimensionalen Mixed Reality-Welt müssen wir nicht mehr auf diese Abstraktions Welt beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="40ae4-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="40ae4-108">Dabei kann es sich um ein Objekt handeln, das ein **Objekt** ist, das ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="40ae4-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="40ae4-109">Ein Objekt mit Interaktionen kann alles von einem Kaffeebecher in einer Tabelle bis zu einer Sprechblase in Midair sein.</span><span class="sxs-lookup"><span data-stu-id="40ae4-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="40ae4-110">Wir verwenden weiterhin herkömmliche Schaltflächen in bestimmten Situationen, z. b. in der Dialogfeld Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="40ae4-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="40ae4-111">Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.</span><span class="sxs-lookup"><span data-stu-id="40ae4-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="40ae4-112">Wichtige Eigenschaften des Interaktionen-Objekts</span><span class="sxs-lookup"><span data-stu-id="40ae4-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="40ae4-113">Visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="40ae4-113">Visual cues</span></span>

<span data-ttu-id="40ae4-114">Visuelle Hinweise sind Sinnes Hinweise von Licht, die im Auge genommen werden und während der visuellen Wahrnehmung vom visuellen System verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="40ae4-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="40ae4-115">Da das visuelle System in vielen Arten, insbesondere bei Menschen, dominant ist, stellen visuelle Hinweise eine große Informationsquelle dar, in der die Welt wahrgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="40ae4-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="40ae4-116">Da die Holographic-Objekte in gemischter Realität mit der realen Umgebung kombiniert werden, kann es schwierig sein, die Objekte zu verstehen, mit denen Sie interagieren können.</span><span class="sxs-lookup"><span data-stu-id="40ae4-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="40ae4-117">Für alle Objekte, die sich in der Benutzersprache befinden, ist es wichtig, für jeden Eingabe Zustand differenzierte visuelle Hinweise bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="40ae4-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="40ae4-118">Dadurch kann der Benutzer verstehen, welcher Teil ihrer Benutzeroberflächen Interaktionen ist, und der Benutzer wird mit einer konsistenten Interaktions Methode vertraut.</span><span class="sxs-lookup"><span data-stu-id="40ae4-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="40ae4-119">Weite Interaktionen</span><span class="sxs-lookup"><span data-stu-id="40ae4-119">Far interactions</span></span>

<span data-ttu-id="40ae4-120">Für alle Objekte, die der Benutzer mit dem Blick auf "Blick", "Hand Strahl" und "Bewegungs Controller" interagieren kann, empfiehlt sich die Verwendung eines anderen visuellen Objekts für diese drei Eingabe Zustände:</span><span class="sxs-lookup"><span data-stu-id="40ae4-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="40ae4-121">![Interactable-Objekt mit Standardzustand](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="40ae4-122">**Standardzustand (Überwachung)**</span><span class="sxs-lookup"><span data-stu-id="40ae4-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="40ae4-123">Der standardmäßige Leerlauf Status des Objekts.</span><span class="sxs-lookup"><span data-stu-id="40ae4-123">Default idle state of the object.</span></span>
    <span data-ttu-id="40ae4-124">Der Cursor befindet sich nicht im-Objekt.</span><span class="sxs-lookup"><span data-stu-id="40ae4-124">The cursor isn't on the object.</span></span> <span data-ttu-id="40ae4-125">Hand wird nicht erkannt.</span><span class="sxs-lookup"><span data-stu-id="40ae4-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="40ae4-126">![Interactable-Objekt mit Ziel-und Hover-Zustand](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="40ae4-127">**Zielzustand (Hover)**</span><span class="sxs-lookup"><span data-stu-id="40ae4-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="40ae4-128">, Wenn das Objekt mit dem Cursor Cursor, der fingernähe oder dem Bewegungs Controller Zeiger ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="40ae4-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="40ae4-129">Der Cursor befindet sich auf dem-Objekt.</span><span class="sxs-lookup"><span data-stu-id="40ae4-129">The cursor is on the object.</span></span> <span data-ttu-id="40ae4-130">Hand ist erkannt, bereit.</span><span class="sxs-lookup"><span data-stu-id="40ae4-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="40ae4-131">![Interactable-Objekt mit gedrücktem Zustand](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="40ae4-132">**Gedrückter Zustand**</span><span class="sxs-lookup"><span data-stu-id="40ae4-132">**Pressed state**</span></span><br>
        <span data-ttu-id="40ae4-133">Wenn das Objekt mit einer Tastenkombination gedrückt wird, drücken Sie die Schaltfläche "auswählen" von Finger oder Motion Controller.</span><span class="sxs-lookup"><span data-stu-id="40ae4-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="40ae4-134">Der Cursor befindet sich auf dem-Objekt.</span><span class="sxs-lookup"><span data-stu-id="40ae4-134">The cursor is on the object.</span></span> <span data-ttu-id="40ae4-135">Hand ist erkannt, Air tippt.</span><span class="sxs-lookup"><span data-stu-id="40ae4-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="40ae4-136">Sie können Techniken wie z. b. Hervorhebung oder Skalierung verwenden, um visuelle Hinweise für den Eingabe Zustand des Benutzers bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="40ae4-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="40ae4-137">In gemischter Realität finden Sie Beispiele für die Visualisierung verschiedener Eingabe Zustände im Startmenü und mit den Schaltflächen der APP-Leiste.</span><span class="sxs-lookup"><span data-stu-id="40ae4-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="40ae4-138">Diese Zustände sehen auf einer **Holographic-Schaltfläche** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="40ae4-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="40ae4-139">![Holographic-Schaltfläche im Standardzustand](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="40ae4-140">**Standardzustand (Überwachung)**</span><span class="sxs-lookup"><span data-stu-id="40ae4-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="40ae4-141">![Holographic-Schaltfläche im Ziel-und Hover-Zustand](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="40ae4-142">**Zielzustand (Hover)**</span><span class="sxs-lookup"><span data-stu-id="40ae4-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="40ae4-143">![Holographic-Schaltfläche im gedrückten Zustand](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="40ae4-144">**Gedrückter Zustand**</span><span class="sxs-lookup"><span data-stu-id="40ae4-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="40ae4-145">Near Interaktionen (Direct)</span><span class="sxs-lookup"><span data-stu-id="40ae4-145">Near interactions (direct)</span></span> 

<span data-ttu-id="40ae4-146">Hololens 2 unterstützt die Eingabe von Handgelenk Nachverfolgung, mit der Sie mit Objekten interagieren können.</span><span class="sxs-lookup"><span data-stu-id="40ae4-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="40ae4-147">Ohne haptisches Feedback und eine perfekte Tiefe Wahrnehmung kann es schwierig sein, zu wissen, wie weit die Hand von einem Objekt entfernt ist oder ob Sie es berühren.</span><span class="sxs-lookup"><span data-stu-id="40ae4-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="40ae4-148">Es ist wichtig, genügend visuelle Hinweise bereitzustellen, um den Status des Objekts zu übermitteln, insbesondere den Zustand ihrer Hände basierend auf diesem Objekt.</span><span class="sxs-lookup"><span data-stu-id="40ae4-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="40ae4-149">Verwenden Sie visuelles Feedback, um die folgenden Zustände zu kommunizieren:</span><span class="sxs-lookup"><span data-stu-id="40ae4-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="40ae4-150">**Default (Observation)**: standardmäßiger Leerlauf Status des Objekts.</span><span class="sxs-lookup"><span data-stu-id="40ae4-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="40ae4-151">**Hover**: Wenn eine Hand sich in der Nähe eines Hologramms befindet, ändern Sie die visuellen Elemente, um zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="40ae4-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="40ae4-152">**Entfernung und Punkt der Interaktion**: Wenn die Hand ein Hologramm nähert, entwerfen Sie Feedback, um den projizierten Interaktionspunkt zu kommunizieren, und wie weit das Objekt den Finger hat.</span><span class="sxs-lookup"><span data-stu-id="40ae4-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="40ae4-153">**Kontakt beginnt**: Ändern der visuellen Elemente (hell, Farbe), um zu kommunizieren, dass eine Fingereingabe aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="40ae4-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="40ae4-154">**Verstanden**: Ändern von visuellen Elementen (hell, Farbe), wenn das Objekt erfasst wird</span><span class="sxs-lookup"><span data-stu-id="40ae4-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="40ae4-155">**Kontakt Ende**: Ändern der visuellen Elemente (hell, Farbe), wenn die Fingereingabe beendet wurde</span><span class="sxs-lookup"><span data-stu-id="40ae4-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="40ae4-156">![Hover (weit)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="40ae4-157">**Hover (weit)**</span><span class="sxs-lookup"><span data-stu-id="40ae4-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="40ae4-158">Hervorhebung basierend auf der Nähe der Hand.</span><span class="sxs-lookup"><span data-stu-id="40ae4-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="40ae4-159">![Hover (in der Nähe)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="40ae4-160">**Hover (in der Nähe)**</span><span class="sxs-lookup"><span data-stu-id="40ae4-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="40ae4-161">Die Größenänderungen werden basierend auf der Entfernung zur Hand hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="40ae4-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="40ae4-162">![Berühren/drücken](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="40ae4-163">**Berühren/drücken**</span><span class="sxs-lookup"><span data-stu-id="40ae4-163">**Touch / press**</span></span><br>
        <span data-ttu-id="40ae4-164">Feedback zu Visual Plus-Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="40ae4-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="40ae4-165">![Gespür](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="40ae4-166">**Gespür**</span><span class="sxs-lookup"><span data-stu-id="40ae4-166">**Grasp**</span></span><br>
        <span data-ttu-id="40ae4-167">Feedback zu Visual Plus-Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="40ae4-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="40ae4-168">Eine [Schaltfläche in hololens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) ist ein Beispiel dafür, wie die verschiedenen Eingabe Interaktions Zustände visualisiert werden:</span><span class="sxs-lookup"><span data-stu-id="40ae4-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="40ae4-169">![Standard](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="40ae4-170">**Standard**</span><span class="sxs-lookup"><span data-stu-id="40ae4-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="40ae4-171">![Darauf zeigen (Hover)](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="40ae4-172">**Darauf zeigen (Hover)**</span><span class="sxs-lookup"><span data-stu-id="40ae4-172">**Hover**</span></span><br>
        <span data-ttu-id="40ae4-173">Zeigen Sie einen near-basierten Beleuchtungs Effekt an.</span><span class="sxs-lookup"><span data-stu-id="40ae4-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="40ae4-174">![Toucheingabe](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="40ae4-175">**Toucheingabe**</span><span class="sxs-lookup"><span data-stu-id="40ae4-175">**Touch**</span></span><br>
        <span data-ttu-id="40ae4-176">Ripple-Effekt anzeigen.</span><span class="sxs-lookup"><span data-stu-id="40ae4-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="40ae4-177">![Tastenkombination](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="40ae4-178">**Tastenkombination**</span><span class="sxs-lookup"><span data-stu-id="40ae4-178">**Press**</span></span><br>
        <span data-ttu-id="40ae4-179">Verschieben Sie die Vorderseite.</span><span class="sxs-lookup"><span data-stu-id="40ae4-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="40ae4-180">Der visuelle Hinweis "Ring" auf hololens 2</span><span class="sxs-lookup"><span data-stu-id="40ae4-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="40ae4-181">Auf hololens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung von tiefen durch den Benutzer unterstützen kann.</span><span class="sxs-lookup"><span data-stu-id="40ae4-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="40ae4-182">Ein Ring in der Nähe des fingerabbilds wird angezeigt und herunterskaliert, wenn sich der Fingertipp näher an das Objekt anpasst.</span><span class="sxs-lookup"><span data-stu-id="40ae4-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="40ae4-183">Der Ring wird schließlich in einen Punkt konvergiert, wenn der gedrückte Zustand erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="40ae4-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="40ae4-184">Diese visuelle Visualisierung unterstützt den Benutzer dabei, zu verstehen, wie weit Sie aus dem-Objekt stammen.</span><span class="sxs-lookup"><span data-stu-id="40ae4-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="40ae4-185">*Video Schleife: Beispiel für visuelles Feedback basierend auf der Nähe eines umgebenden Felds*</span><span class="sxs-lookup"><span data-stu-id="40ae4-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="40ae4-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="40ae4-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="40ae4-187">![Visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="40ae4-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="40ae4-188">Audiohinweise</span><span class="sxs-lookup"><span data-stu-id="40ae4-188">Audio cues</span></span>

<span data-ttu-id="40ae4-189">Bei direkter Hand Interaktion kann das richtige Audiofeedback die Benutzer Leistung erheblich verbessern.</span><span class="sxs-lookup"><span data-stu-id="40ae4-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="40ae4-190">Verwenden Sie Audiofeedback, um die folgenden Hinweise zu kommunizieren:</span><span class="sxs-lookup"><span data-stu-id="40ae4-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="40ae4-191">**Kontakt beginnt**: Sound abspielen, wenn der Fingerabdruck beginnt</span><span class="sxs-lookup"><span data-stu-id="40ae4-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="40ae4-192">**Kontakt** Ende: Sound am Touchscreen abspielen</span><span class="sxs-lookup"><span data-stu-id="40ae4-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="40ae4-193">**Beginn**: Sound abspielen, wenn der Start beginnt</span><span class="sxs-lookup"><span data-stu-id="40ae4-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="40ae4-194">Aufnahme **Ende**: Sound wiedergeben, wenn der Griff endet</span><span class="sxs-lookup"><span data-stu-id="40ae4-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="40ae4-195">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="40ae4-195">Voice commanding</span></span><br>
        <span data-ttu-id="40ae4-196">Bei allen Objekt übergreifenden Objekten ist es wichtig, Alternative Interaktions Optionen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="40ae4-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="40ae4-197">Standardmäßig wird empfohlen, dass [sprach](../out-of-scope/voice-design.md) Befehle für alle Objekte unterstützt werden, die interacbar sind.</span><span class="sxs-lookup"><span data-stu-id="40ae4-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="40ae4-198">Um die Auffindbarkeit zu verbessern, können Sie auch eine QuickInfo für den Hover-Zustand bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="40ae4-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="40ae4-199">*Bild: QuickInfo für den Voice-Befehl*</span><span class="sxs-lookup"><span data-stu-id="40ae4-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![Sprachbefehl](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a><span data-ttu-id="40ae4-201">Größenempfehlungen</span><span class="sxs-lookup"><span data-stu-id="40ae4-201">Sizing recommendations</span></span>

<span data-ttu-id="40ae4-202">Um sicherzustellen, dass alle austauschbaren Objekte problemlos berührt werden können, sollten Sie sicherstellen, dass die Interaktionen eine minimale Größe basierend auf der Entfernung des Benutzers erfüllt.</span><span class="sxs-lookup"><span data-stu-id="40ae4-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="40ae4-203">Der visuelle Winkel wird häufig in Grad des visuellen Bogens gemessen. Der visuelle Winkel basiert auf der Entfernung zwischen den Augen des Benutzers und dem Objekt und bleibt konstant, während sich die physische Größe des Ziels möglicherweise ändert, wenn sich der Abstand vom Benutzer ändert.</span><span class="sxs-lookup"><span data-stu-id="40ae4-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="40ae4-204">Um die erforderliche physische Größe eines Objekts basierend auf der Entfernung des Benutzers zu bestimmen, versuchen Sie, einen visuellen Winkel Rechner wie [diesen](https://elvers.us/perception/visualAngle/)zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="40ae4-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="40ae4-205">Im folgenden finden Sie die Empfehlungen für die Mindestgröße von Interaktionen-Inhalten.</span><span class="sxs-lookup"><span data-stu-id="40ae4-205">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="40ae4-206">Zielgröße für direkte Interaktion</span><span class="sxs-lookup"><span data-stu-id="40ae4-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="40ae4-207">Entfernung</span><span class="sxs-lookup"><span data-stu-id="40ae4-207">Distance</span></span> | <span data-ttu-id="40ae4-208">Anzeige Winkel</span><span class="sxs-lookup"><span data-stu-id="40ae4-208">Viewing angle</span></span> | <span data-ttu-id="40ae4-209">Size</span><span class="sxs-lookup"><span data-stu-id="40ae4-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="40ae4-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="40ae4-210">45 cm</span></span>  | <span data-ttu-id="40ae4-211">nicht kleiner als 2 °</span><span class="sxs-lookup"><span data-stu-id="40ae4-211">no smaller than 2°</span></span> | <span data-ttu-id="40ae4-212">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="40ae4-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="40ae4-213">![Zielgröße für direkte Interaktion](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="40ae4-214">*Zielgröße für direkte Interaktion*</span><span class="sxs-lookup"><span data-stu-id="40ae4-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="40ae4-215">Zielgröße für Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="40ae4-215">Target size for buttons</span></span>

<span data-ttu-id="40ae4-216">Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass ausreichend Speicherplatz vorhanden ist, um ein Symbol und potenziell einen Text zu enthalten.</span><span class="sxs-lookup"><span data-stu-id="40ae4-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="40ae4-217">Entfernung</span><span class="sxs-lookup"><span data-stu-id="40ae4-217">Distance</span></span> | <span data-ttu-id="40ae4-218">Mindestgröße</span><span class="sxs-lookup"><span data-stu-id="40ae4-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="40ae4-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="40ae4-219">45 cm</span></span>  | <span data-ttu-id="40ae4-220">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="40ae4-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="40ae4-221">![Zielgröße für die Schaltflächen](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="40ae4-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="40ae4-222">*Zielgröße für die Schaltflächen*</span><span class="sxs-lookup"><span data-stu-id="40ae4-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="40ae4-223">Zielgröße für die Hand Strahl-oder Blick Interaktion</span><span class="sxs-lookup"><span data-stu-id="40ae4-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="40ae4-224">Entfernung</span><span class="sxs-lookup"><span data-stu-id="40ae4-224">Distance</span></span> | <span data-ttu-id="40ae4-225">Anzeige Winkel</span><span class="sxs-lookup"><span data-stu-id="40ae4-225">Viewing angle</span></span> | <span data-ttu-id="40ae4-226">Size</span><span class="sxs-lookup"><span data-stu-id="40ae4-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="40ae4-227">2 Mio.</span><span class="sxs-lookup"><span data-stu-id="40ae4-227">2 m</span></span>  | <span data-ttu-id="40ae4-228">nicht kleiner als 1 °</span><span class="sxs-lookup"><span data-stu-id="40ae4-228">no smaller than 1°</span></span> | <span data-ttu-id="40ae4-229">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="40ae4-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="40ae4-230">![Zielgröße für die Hand Strahl-oder Blick Interaktion](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="40ae4-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="40ae4-231">*Zielgröße für die Hand Strahl-oder Blick Interaktion*</span><span class="sxs-lookup"><span data-stu-id="40ae4-231">*Target size for hand ray or gaze interaction*</span></span>

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="40ae4-232">Interactable-Objekt in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="40ae4-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="40ae4-233">In **[mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie das Skript [**interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) verwenden, damit Objekte auf verschiedene Typen von Eingabe Interaktions Zuständen reagieren.</span><span class="sxs-lookup"><span data-stu-id="40ae4-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="40ae4-234">Es unterstützt verschiedene Arten von Designs, mit denen Sie visuelle Zustände definieren können, indem Sie Objekteigenschaften wie z. b. Farbe, Größe, Material und Shader steuern.</span><span class="sxs-lookup"><span data-stu-id="40ae4-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="40ae4-235">Interaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="40ae4-235">Interactable</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [<span data-ttu-id="40ae4-236">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="40ae4-236">Button</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [<span data-ttu-id="40ae4-237">Beispiel Szenen für Hand Interaktion</span><span class="sxs-lookup"><span data-stu-id="40ae4-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="40ae4-238">Der Standard-Shader von mixedrealitytoolkit bietet verschiedene Optionen, wie z. b. **near Light** , mit denen Sie visuelle und Audiohinweise erstellen können.</span><span class="sxs-lookup"><span data-stu-id="40ae4-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>

* [<span data-ttu-id="40ae4-239">MRTK-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="40ae4-239">MRTK Standard Shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="40ae4-240">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="40ae4-240">See also</span></span>

* [<span data-ttu-id="40ae4-241">Cursor</span><span class="sxs-lookup"><span data-stu-id="40ae4-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="40ae4-242">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="40ae4-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="40ae4-243">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="40ae4-243">Button</span></span>](button.md)
* [<span data-ttu-id="40ae4-244">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="40ae4-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="40ae4-245">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="40ae4-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="40ae4-246">Manipulation</span><span class="sxs-lookup"><span data-stu-id="40ae4-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="40ae4-247">Handmenü</span><span class="sxs-lookup"><span data-stu-id="40ae4-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="40ae4-248">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="40ae4-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="40ae4-249">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="40ae4-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="40ae4-250">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="40ae4-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="40ae4-251">Tastatur</span><span class="sxs-lookup"><span data-stu-id="40ae4-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="40ae4-252">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="40ae4-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="40ae4-253">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="40ae4-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="40ae4-254">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="40ae4-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="40ae4-255">Shader</span><span class="sxs-lookup"><span data-stu-id="40ae4-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="40ae4-256">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="40ae4-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="40ae4-257">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="40ae4-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="40ae4-258">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="40ae4-258">Surface magnetism</span></span>](surface-magnetism.md)
