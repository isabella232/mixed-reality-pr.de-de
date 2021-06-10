---
title: Interaktionsfähiges Objekt
description: Erfahren Sie, wie Sie Ereignisse auslösen, visuelle Hinweise bereitstellen und mit Objekten in Ihren Mixed Reality-Anwendungen interagieren.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, Steuerelemente, Interaktion, Hinweise, Ui, ux, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Audio
ms.openlocfilehash: 8a68006d68b985f8d26a3d1a11e4d52fcfb5acb5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600439"
---
# <a name="interactable-object"></a><span data-ttu-id="2216e-104">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="2216e-104">Interactable object</span></span>

![Interagierbare Objekte](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="2216e-106">Eine Schaltfläche ist schon lange eine Symbolmetapher, die zum Auslösen eines Ereignisses in der abstrakten 2D-Welt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2216e-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="2216e-107">In der dreidimensionalen Mixed Reality-Welt müssen wir uns nicht mehr auf diese Welt der Abstraktion beschränken.</span><span class="sxs-lookup"><span data-stu-id="2216e-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="2216e-108">Alles kann ein **interaktionsfähiges Objekt sein,** das ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="2216e-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="2216e-109">Ein interaktionsfähiges Objekt kann von einer Kaffeetasse auf einem Tisch bis zu einem Sprechblasen in der Luft sein.</span><span class="sxs-lookup"><span data-stu-id="2216e-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="2216e-110">In bestimmten Fällen, z. B. in der Dialogbenutzeroberfläche, werden weiterhin herkömmliche Schaltflächen verwendet.</span><span class="sxs-lookup"><span data-stu-id="2216e-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="2216e-111">Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.</span><span class="sxs-lookup"><span data-stu-id="2216e-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="2216e-112">Wichtige Eigenschaften des interagierbaren Objekts</span><span class="sxs-lookup"><span data-stu-id="2216e-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="2216e-113">Visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="2216e-113">Visual cues</span></span>

<span data-ttu-id="2216e-114">Visuelle Hinweise sind sensorische Hinweise vom Licht, die vom Auge empfangen und während der visuellen Wahrnehmung vom visuellen System verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="2216e-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="2216e-115">Da das visuelle System in vielen Arten, insbesondere bei Menschen, dominant ist, sind visuelle Hinweise eine große Informationsquelle für die Wahrnehmung der Welt.</span><span class="sxs-lookup"><span data-stu-id="2216e-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="2216e-116">Da die holografischen Objekte mit der realen Umgebung in Mixed Reality kombiniert werden, kann es schwierig sein, zu verstehen, mit welchen Objekten Sie interagieren können.</span><span class="sxs-lookup"><span data-stu-id="2216e-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="2216e-117">Für alle interagierenden Objekte in Ihrer Erfahrung ist es wichtig, für jeden Eingabezustand differenzierte visuelle Hinweise zu bieten.</span><span class="sxs-lookup"><span data-stu-id="2216e-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="2216e-118">Dies hilft dem Benutzer zu verstehen, welcher Teil Ihrer Benutzeroberfläche interagierbar ist, und macht den Benutzer mithilfe einer konsistenten Interaktionsmethode sicher.</span><span class="sxs-lookup"><span data-stu-id="2216e-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="2216e-119">Ferninteraktionen</span><span class="sxs-lookup"><span data-stu-id="2216e-119">Far interactions</span></span>

<span data-ttu-id="2216e-120">Für alle Objekte, die der Benutzer mit dem Anvisieren, dem Handstrahl und dem Ray des Bewegungscontrollers interagieren kann, wird empfohlen, für diese drei Eingabezustände unterschiedliche visuelle Hinweise zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="2216e-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="2216e-121">![Interagierbares Objekt mit Standardzustand](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="2216e-122">**Standardzustand (Beobachtung)**</span><span class="sxs-lookup"><span data-stu-id="2216e-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="2216e-123">Standard-Leerlaufzustand des Objekts.</span><span class="sxs-lookup"><span data-stu-id="2216e-123">Default idle state of the object.</span></span>
    <span data-ttu-id="2216e-124">Der Cursor befindet sich nicht auf dem -Objekt.</span><span class="sxs-lookup"><span data-stu-id="2216e-124">The cursor isn't on the object.</span></span> <span data-ttu-id="2216e-125">Hand wird nicht erkannt.</span><span class="sxs-lookup"><span data-stu-id="2216e-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2216e-126">![Interagierbares Objekt mit Ziel- und Hoverzustand](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="2216e-127">**Zielzustand (Hover)**</span><span class="sxs-lookup"><span data-stu-id="2216e-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="2216e-128">Wenn das Objekt mit dem Anvitätscursor, der Fingernähe oder dem Bewegungscontrollerzeiger als Ziel verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2216e-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="2216e-129">Der Cursor befindet sich auf dem -Objekt.</span><span class="sxs-lookup"><span data-stu-id="2216e-129">The cursor is on the object.</span></span> <span data-ttu-id="2216e-130">Hand ist erkannt, bereit.</span><span class="sxs-lookup"><span data-stu-id="2216e-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2216e-131">![Interagierbares Objekt mit gedrückter Zustand](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="2216e-132">**Gedrückter Zustand**</span><span class="sxs-lookup"><span data-stu-id="2216e-132">**Pressed state**</span></span><br>
        <span data-ttu-id="2216e-133">Wenn das Objekt mit einer Tippbewegung in die Luft gedrückt wird, drücken Sie den Finger, oder drücken Sie die Auswahltaste des Bewegungscontrollers.</span><span class="sxs-lookup"><span data-stu-id="2216e-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="2216e-134">Der Cursor befindet sich auf dem -Objekt.</span><span class="sxs-lookup"><span data-stu-id="2216e-134">The cursor is on the object.</span></span> <span data-ttu-id="2216e-135">Hand wird erkannt, Luft angetippt.</span><span class="sxs-lookup"><span data-stu-id="2216e-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="2216e-136">Sie können Techniken wie Hervorhebung oder Skalierung verwenden, um visuelle Hinweise für den Eingabezustand des Benutzers zu bieten.</span><span class="sxs-lookup"><span data-stu-id="2216e-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="2216e-137">In Mixed Reality finden Sie Beispiele für die Visualisierung verschiedener Eingabezustände auf dem Startmenü und mit App-Leistenschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="2216e-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="2216e-138">Diese Zustände sehen auf einer **holografischen** Schaltfläche wie hier aus:</span><span class="sxs-lookup"><span data-stu-id="2216e-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="2216e-139">![Holographic-Schaltfläche im Standardzustand](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="2216e-140">**Standardzustand (Beobachtung)**</span><span class="sxs-lookup"><span data-stu-id="2216e-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2216e-141">![Holografische Schaltfläche im Ziel- und Hoverzustand](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="2216e-142">**Zielzustand (Hover)**</span><span class="sxs-lookup"><span data-stu-id="2216e-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2216e-143">![Holografische Schaltfläche im gedrückten Zustand](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="2216e-144">**Gedrückter Zustand**</span><span class="sxs-lookup"><span data-stu-id="2216e-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="2216e-145">Near interactions (direct) (Nahinteraktionen (direkt))</span><span class="sxs-lookup"><span data-stu-id="2216e-145">Near interactions (direct)</span></span> 

<span data-ttu-id="2216e-146">HoloLens 2 unterstützt artikulierte Handtrackingeingaben, mit denen Sie mit Objekten interagieren können.</span><span class="sxs-lookup"><span data-stu-id="2216e-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="2216e-147">Ohne feedbacktisches Feedback und perfekte Tiefenempfinden kann es schwierig sein zu erkennen, wie weit Ihre Hand von einem Objekt entfernt ist oder ob Sie sie berühren.</span><span class="sxs-lookup"><span data-stu-id="2216e-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="2216e-148">Es ist wichtig, genügend visuelle Hinweise zum Kommunizieren des Zustands des Objekts, insbesondere des Zustands Ihrer Hände basierend auf diesem Objekt, zu geben.</span><span class="sxs-lookup"><span data-stu-id="2216e-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="2216e-149">Verwenden Sie visuelles Feedback, um die folgenden Zustände zu kommunizieren:</span><span class="sxs-lookup"><span data-stu-id="2216e-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="2216e-150">**Standard (Beobachtung):** Standardmäßiger Leerlaufzustand des Objekts.</span><span class="sxs-lookup"><span data-stu-id="2216e-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="2216e-151">**Hover:** Wenn sich eine Hand in der Nähe eines Hologramms befindet, ändern Sie visuals, um zu kommunizieren, dass die Hand auf Hologramm zielt.</span><span class="sxs-lookup"><span data-stu-id="2216e-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="2216e-152">**Abstand und Interaktionspunkt:** Wenn sich die Hand einem Hologramm nähert, entwerfen Sie Feedback, um den projizierten Interaktionspunkt und die Entfernung des Fingers zum Objekt zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="2216e-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="2216e-153">**Kontakt beginnt:** Visuelle Elemente (Hell, Farbe) ändern, um zu kommunizieren, dass eine Berührung erfolgt ist</span><span class="sxs-lookup"><span data-stu-id="2216e-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="2216e-154">**Verstanden:** Visuelle Elemente (Licht, Farbe) ändern, wenn das Objekt erfasst wird</span><span class="sxs-lookup"><span data-stu-id="2216e-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="2216e-155">**Kontakt endet:** Visuelle Elemente (Hell, Farbe) ändern, wenn die Berührung beendet wurde</span><span class="sxs-lookup"><span data-stu-id="2216e-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="2216e-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="2216e-157">**Hover (Far)**</span><span class="sxs-lookup"><span data-stu-id="2216e-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="2216e-158">Hervorhebung basierend auf der Nähe der Hand.</span><span class="sxs-lookup"><span data-stu-id="2216e-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2216e-159">![Hover (Near) (Hover (Nah))](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="2216e-160">**Hover (Near) (Hover (Nah))**</span><span class="sxs-lookup"><span data-stu-id="2216e-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="2216e-161">Hervorheben von Größenänderungen basierend auf dem Abstand zur Hand.</span><span class="sxs-lookup"><span data-stu-id="2216e-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="2216e-162">![Touch/Drücken](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="2216e-163">**Touch/Drücken**</span><span class="sxs-lookup"><span data-stu-id="2216e-163">**Touch / press**</span></span><br>
        <span data-ttu-id="2216e-164">Visuelles Feedback und Audiofeedback.</span><span class="sxs-lookup"><span data-stu-id="2216e-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2216e-165">![Begreifen](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="2216e-166">**Begreifen**</span><span class="sxs-lookup"><span data-stu-id="2216e-166">**Grasp**</span></span><br>
        <span data-ttu-id="2216e-167">Visuelles Feedback und Audiofeedback.</span><span class="sxs-lookup"><span data-stu-id="2216e-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="2216e-168">Eine [Schaltfläche auf HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) ist ein Beispiel dafür, wie die verschiedenen Eingabeinteraktionszustände visualisiert werden:</span><span class="sxs-lookup"><span data-stu-id="2216e-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2216e-169">![Standard](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="2216e-170">**Standard**</span><span class="sxs-lookup"><span data-stu-id="2216e-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2216e-171">![Darauf zeigen (Hover)](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="2216e-172">**Darauf zeigen (Hover)**</span><span class="sxs-lookup"><span data-stu-id="2216e-172">**Hover**</span></span><br>
        <span data-ttu-id="2216e-173">Zeigen Sie einen näherungsbasierten Beleuchtungseffekt an.</span><span class="sxs-lookup"><span data-stu-id="2216e-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="2216e-174">![Toucheingabe](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="2216e-175">**Toucheingabe**</span><span class="sxs-lookup"><span data-stu-id="2216e-175">**Touch**</span></span><br>
        <span data-ttu-id="2216e-176">Anzeigen des Effekts "Show".</span><span class="sxs-lookup"><span data-stu-id="2216e-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2216e-177">![Tastenkombination](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="2216e-178">**Presse**</span><span class="sxs-lookup"><span data-stu-id="2216e-178">**Press**</span></span><br>
        <span data-ttu-id="2216e-179">Verschieben Sie die vordere Platte.</span><span class="sxs-lookup"><span data-stu-id="2216e-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="2216e-180">Der visuelle Hinweis "ring" auf HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2216e-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="2216e-181">Auf HoloLens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung der Tiefe des Benutzers unterstützen kann.</span><span class="sxs-lookup"><span data-stu-id="2216e-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="2216e-182">Ein Ring in der Nähe ihrer Fingerspitze wird angezeigt und skaliert herunter, wenn sich die Fingerspitze dem Objekt nähert.</span><span class="sxs-lookup"><span data-stu-id="2216e-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="2216e-183">Der Ring konvergiert schließlich zu einem Punkt, wenn der gedrückte Zustand erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="2216e-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="2216e-184">Dieses visuelle Modell hilft dem Benutzer zu verstehen, wie weit er vom Objekt entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="2216e-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="2216e-185">*Videoschleife: Beispiel für visuelles Feedback basierend auf der Nähe zu einem Begrenzungsfeld*</span><span class="sxs-lookup"><span data-stu-id="2216e-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="2216e-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="2216e-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="2216e-187">![Visuelles Feedback zur Nähe](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="2216e-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="2216e-188">Audio-Hinweise</span><span class="sxs-lookup"><span data-stu-id="2216e-188">Audio cues</span></span>

<span data-ttu-id="2216e-189">Bei direkten Handinteraktionen kann das richtige Audiofeedback die Benutzerfreundlichkeit erheblich verbessern.</span><span class="sxs-lookup"><span data-stu-id="2216e-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="2216e-190">Verwenden Sie Audiofeedback, um die folgenden Hinweise zu kommunizieren:</span><span class="sxs-lookup"><span data-stu-id="2216e-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="2216e-191">**Kontakt beginnt:** Sound wiedererlangen, wenn die Berührung beginnt</span><span class="sxs-lookup"><span data-stu-id="2216e-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="2216e-192">**Kontakt endet:** Sound auf Touch-End wiedererlangen</span><span class="sxs-lookup"><span data-stu-id="2216e-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="2216e-193">**Grab beginnt:** Sound beim Starten des Greifs wiedererlangen</span><span class="sxs-lookup"><span data-stu-id="2216e-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="2216e-194">**Greifende:** Sound wiedererlangen, wenn der Greif beendet wird</span><span class="sxs-lookup"><span data-stu-id="2216e-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="2216e-195">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="2216e-195">Voice commanding</span></span><br>
        <span data-ttu-id="2216e-196">Für alle interagierbaren Objekte ist es wichtig, alternative Interaktionsoptionen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="2216e-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="2216e-197">Standardmäßig wird empfohlen, [Sprachbefehle](../out-of-scope/voice-design.md) für alle Objekte zu unterstützen, die interagierbar sind.</span><span class="sxs-lookup"><span data-stu-id="2216e-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="2216e-198">Um die Aufmittelbarkeit zu verbessern, können Sie auch eine QuickInfo während des Hoverzustands bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2216e-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="2216e-199">*Abbildung: QuickInfo für den Sprachbefehl*</span><span class="sxs-lookup"><span data-stu-id="2216e-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![Sprachbefehle](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a><span data-ttu-id="2216e-201">Größenempfehlungen</span><span class="sxs-lookup"><span data-stu-id="2216e-201">Sizing recommendations</span></span>

<span data-ttu-id="2216e-202">Um sicherzustellen, dass alle interaktiven Objekte leicht berührt werden können, wird empfohlen, sicherzustellen, dass die interaktive -Datei eine Mindestgröße erfüllt, die auf dem Abstand basiert, den sie vom Benutzer entfernt hat.</span><span class="sxs-lookup"><span data-stu-id="2216e-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="2216e-203">Der visuelle Winkel wird häufig in Grad des visuellen Bogens gemessen. Der visuelle Winkel basiert auf dem Abstand zwischen den Augen des Benutzers und dem Objekt und bleibt konstant, während sich die physische Größe des Ziels ändern kann, wenn sich der Abstand zum Benutzer ändert.</span><span class="sxs-lookup"><span data-stu-id="2216e-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="2216e-204">Um die erforderliche physische Größe eines Objekts basierend auf der Entfernung zum Benutzer zu bestimmen, versuchen Sie, einen Rechner für den visuellen Winkel wie [diesen](https://elvers.us/perception/visualAngle/)zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2216e-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="2216e-205">Im Folgenden finden Sie die Empfehlungen für die Mindestgröße interaktiver Inhalte.</span><span class="sxs-lookup"><span data-stu-id="2216e-205">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="2216e-206">Zielgröße für direkte Handinteraktion</span><span class="sxs-lookup"><span data-stu-id="2216e-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="2216e-207">Entfernung</span><span class="sxs-lookup"><span data-stu-id="2216e-207">Distance</span></span> | <span data-ttu-id="2216e-208">Betrachtungswinkel</span><span class="sxs-lookup"><span data-stu-id="2216e-208">Viewing angle</span></span> | <span data-ttu-id="2216e-209">Size</span><span class="sxs-lookup"><span data-stu-id="2216e-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="2216e-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="2216e-210">45 cm</span></span>  | <span data-ttu-id="2216e-211">nicht kleiner als 2°</span><span class="sxs-lookup"><span data-stu-id="2216e-211">no smaller than 2°</span></span> | <span data-ttu-id="2216e-212">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="2216e-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="2216e-213">![Zielgröße für direkte Handinteraktion](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="2216e-214">*Zielgröße für direkte Handinteraktion*</span><span class="sxs-lookup"><span data-stu-id="2216e-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="2216e-215">Zielgröße für Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="2216e-215">Target size for buttons</span></span>

<span data-ttu-id="2216e-216">Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass genügend Platz für ein Symbol und möglicherweise Text vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2216e-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="2216e-217">Entfernung</span><span class="sxs-lookup"><span data-stu-id="2216e-217">Distance</span></span> | <span data-ttu-id="2216e-218">Mindestgröße</span><span class="sxs-lookup"><span data-stu-id="2216e-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="2216e-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="2216e-219">45 cm</span></span>  | <span data-ttu-id="2216e-220">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="2216e-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="2216e-221">![Zielgröße für die Schaltflächen](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="2216e-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="2216e-222">*Zielgröße für die Schaltflächen*</span><span class="sxs-lookup"><span data-stu-id="2216e-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="2216e-223">Zielgröße für die Interaktion mit Handstrahl oder Anvize</span><span class="sxs-lookup"><span data-stu-id="2216e-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="2216e-224">Entfernung</span><span class="sxs-lookup"><span data-stu-id="2216e-224">Distance</span></span> | <span data-ttu-id="2216e-225">Betrachtungswinkel</span><span class="sxs-lookup"><span data-stu-id="2216e-225">Viewing angle</span></span> | <span data-ttu-id="2216e-226">Size</span><span class="sxs-lookup"><span data-stu-id="2216e-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="2216e-227">2 m</span><span class="sxs-lookup"><span data-stu-id="2216e-227">2 m</span></span>  | <span data-ttu-id="2216e-228">nicht kleiner als 1°</span><span class="sxs-lookup"><span data-stu-id="2216e-228">no smaller than 1°</span></span> | <span data-ttu-id="2216e-229">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="2216e-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="2216e-230">![Zielgröße für die Interaktion mit Handstrahl oder Anvize](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="2216e-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="2216e-231">*Zielgröße für die Interaktion mit Handstrahl oder Anvize*</span><span class="sxs-lookup"><span data-stu-id="2216e-231">*Target size for hand ray or gaze interaction*</span></span>

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="2216e-232">Interaktivierbares Objekt im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="2216e-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="2216e-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie das Skript [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) verwenden, damit Objekte auf verschiedene Arten von Eingabeinteraktionszuständen reagieren.</span><span class="sxs-lookup"><span data-stu-id="2216e-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="2216e-234">Es unterstützt verschiedene Arten von Designs, mit denen Sie visuelle Zustände definieren können, indem Sie Objekteigenschaften wie Farbe, Größe, Material und Shader steuern.</span><span class="sxs-lookup"><span data-stu-id="2216e-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="2216e-235">Interaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="2216e-235">Interactable</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* <span data-ttu-id="2216e-236">[Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="2216e-236">[Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)</span></span>
* [<span data-ttu-id="2216e-237">Szene mit Beispielen für Die Handinteraktion</span><span class="sxs-lookup"><span data-stu-id="2216e-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="2216e-238">Der Standard-Shader von MixedRealityToolkit bietet verschiedene Optionen, z. B. **Näherungslicht,** mit dem Sie visuelle und Audiohinweise erstellen können.</span><span class="sxs-lookup"><span data-stu-id="2216e-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>

* [<span data-ttu-id="2216e-239">MRTK-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="2216e-239">MRTK Standard Shader</span></span>](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="2216e-240">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2216e-240">See also</span></span>

* [<span data-ttu-id="2216e-241">Cursor</span><span class="sxs-lookup"><span data-stu-id="2216e-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="2216e-242">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="2216e-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="2216e-243">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="2216e-243">Button</span></span>](button.md)
* [<span data-ttu-id="2216e-244">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="2216e-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="2216e-245">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="2216e-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="2216e-246">Manipulation</span><span class="sxs-lookup"><span data-stu-id="2216e-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2216e-247">Handmenü</span><span class="sxs-lookup"><span data-stu-id="2216e-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="2216e-248">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="2216e-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="2216e-249">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="2216e-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="2216e-250">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="2216e-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="2216e-251">Tastatur</span><span class="sxs-lookup"><span data-stu-id="2216e-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="2216e-252">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="2216e-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="2216e-253">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="2216e-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="2216e-254">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="2216e-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="2216e-255">Shader</span><span class="sxs-lookup"><span data-stu-id="2216e-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="2216e-256">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="2216e-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="2216e-257">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="2216e-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="2216e-258">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="2216e-258">Surface magnetism</span></span>](surface-magnetism.md)