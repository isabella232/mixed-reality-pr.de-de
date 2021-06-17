---
title: Interaktionsfähiges Objekt
description: Erfahren Sie, wie Sie Ereignisse auslösen, visuelle Hinweise bereitstellen und mit Objekten in Ihren Mixed Reality-Anwendungen interagieren.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, Steuerelemente, Interaktion, Hinweise, Ui, ux, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Audio
ms.openlocfilehash: b25c25a6dd48bcc85a556787099734d147d18df2
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110217"
---
# <a name="interactable-object"></a><span data-ttu-id="3f593-104">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="3f593-104">Interactable object</span></span>

![Interaktivierbare Objekte](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="3f593-106">Eine Schaltfläche ist seit langem eine Metapher zum Auslösen eines Ereignisses in der abstrakten 2D-Welt.</span><span class="sxs-lookup"><span data-stu-id="3f593-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="3f593-107">In der dreidimensionalen Mixed Reality-Welt müssen wir uns nicht mehr auf diese Abstraktionswelt beschränken.</span><span class="sxs-lookup"><span data-stu-id="3f593-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="3f593-108">Alles kann ein **interaktionsfähiges Objekt** sein, das ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="3f593-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="3f593-109">Ein interaktives Objekt kann alles sein, von einer Kaffeetasse auf einem Tisch bis hin zu einem Luftblasen in der Luft.</span><span class="sxs-lookup"><span data-stu-id="3f593-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="3f593-110">In bestimmten Situationen, z. B. auf der Benutzeroberfläche des Dialogfelds, werden weiterhin herkömmliche Schaltflächen verwendet.</span><span class="sxs-lookup"><span data-stu-id="3f593-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="3f593-111">Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.</span><span class="sxs-lookup"><span data-stu-id="3f593-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="3f593-112">Wichtige Eigenschaften des interaktivierbaren Objekts</span><span class="sxs-lookup"><span data-stu-id="3f593-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="3f593-113">Visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="3f593-113">Visual cues</span></span>

<span data-ttu-id="3f593-114">Visuelle Hinweise sind sensorische Hinweise von Licht, die vom Auge empfangen und während der visuellen Wahrnehmung vom visuellen System verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="3f593-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="3f593-115">Da das visuelle System bei vielen Arten, insbesondere menschen, vorherrschend ist, stellen visuelle Hinweise eine große Informationsquelle für die Wahrnehmung der Welt dar.</span><span class="sxs-lookup"><span data-stu-id="3f593-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="3f593-116">Da die holografischen Objekte mit der realen Umgebung in Mixed Reality kombiniert werden, kann es schwierig sein, zu verstehen, mit welchen Objekten Sie interagieren können.</span><span class="sxs-lookup"><span data-stu-id="3f593-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="3f593-117">Für alle interaktiven Objekte in Ihrer Benutzeroberfläche ist es wichtig, für jeden Eingabezustand differenzierte visuelle Hinweise bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="3f593-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="3f593-118">Dies hilft dem Benutzer zu verstehen, welcher Teil Ihrer Benutzeroberfläche interagierbar ist, und macht den Benutzer mithilfe einer konsistenten Interaktionsmethode sicher.</span><span class="sxs-lookup"><span data-stu-id="3f593-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="3f593-119">Far-Interaktionen</span><span class="sxs-lookup"><span data-stu-id="3f593-119">Far interactions</span></span>

<span data-ttu-id="3f593-120">Für alle Objekte, die Der Benutzer mit Anvieren, Handstrahl und Dem Strahl des Bewegungscontrollers interagieren kann, empfiehlt es sich, unterschiedliche visuelle Hinweise für diese drei Eingabezustände zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="3f593-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="3f593-121">![Interaktivierbares Objekt mit Standardzustand](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="3f593-122">**Standardzustand (Beobachtung)**</span><span class="sxs-lookup"><span data-stu-id="3f593-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="3f593-123">Standardzustand des Objekts im Leerlauf.</span><span class="sxs-lookup"><span data-stu-id="3f593-123">Default idle state of the object.</span></span>
    <span data-ttu-id="3f593-124">Der Cursor befindet sich nicht im -Objekt.</span><span class="sxs-lookup"><span data-stu-id="3f593-124">The cursor isn't on the object.</span></span> <span data-ttu-id="3f593-125">Hand wird nicht erkannt.</span><span class="sxs-lookup"><span data-stu-id="3f593-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3f593-126">![Interaktivierbares Objekt mit Ziel- und Mauszeigerzustand](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="3f593-127">**Zielzustand (Hover)**</span><span class="sxs-lookup"><span data-stu-id="3f593-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="3f593-128">Wenn das Objekt mit dem Anvisierten cursor, finger proximity oder motion controller es pointer (Zeiger des Bewegungscontrollers) als Ziel verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3f593-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="3f593-129">Der Cursor befindet sich im -Objekt.</span><span class="sxs-lookup"><span data-stu-id="3f593-129">The cursor is on the object.</span></span> <span data-ttu-id="3f593-130">Hand wird erkannt, bereit.</span><span class="sxs-lookup"><span data-stu-id="3f593-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3f593-131">![Interaktivierbares Objekt mit gedrücktem Zustand](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="3f593-132">**Gedrückter Zustand**</span><span class="sxs-lookup"><span data-stu-id="3f593-132">**Pressed state**</span></span><br>
        <span data-ttu-id="3f593-133">Wenn das Objekt mit einer Geste zum Tippen in die Luft gedrückt wird, drücken Sie den Finger oder die Auswahlschaltfläche des Bewegungscontrollers.</span><span class="sxs-lookup"><span data-stu-id="3f593-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="3f593-134">Der Cursor befindet sich im -Objekt.</span><span class="sxs-lookup"><span data-stu-id="3f593-134">The cursor is on the object.</span></span> <span data-ttu-id="3f593-135">Die Hand wird erkannt, die Luft wird angetippt.</span><span class="sxs-lookup"><span data-stu-id="3f593-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="3f593-136">Sie können Techniken wie Hervorhebung oder Skalierung verwenden, um visuelle Hinweise für den Eingabezustand des Benutzers bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="3f593-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="3f593-137">In Mixed Reality finden Sie Beispiele für die Visualisierung verschiedener Eingabezustände auf dem Startmenü und mit Schaltflächen auf der App-Leiste.</span><span class="sxs-lookup"><span data-stu-id="3f593-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="3f593-138">Diese Zustände sehen auf einer **holografischen Schaltfläche** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3f593-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="3f593-139">![Holografische Schaltfläche im Standardzustand](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="3f593-140">**Standardzustand (Beobachtung)**</span><span class="sxs-lookup"><span data-stu-id="3f593-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3f593-141">![Holografische Schaltfläche im Ziel- und Mauszeigerzustand](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="3f593-142">**Zielzustand (Hover)**</span><span class="sxs-lookup"><span data-stu-id="3f593-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3f593-143">![Holografische Schaltfläche im gedrückten Zustand](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="3f593-144">**Gedrückter Zustand**</span><span class="sxs-lookup"><span data-stu-id="3f593-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="3f593-145">Nahinteraktionen (direkt)</span><span class="sxs-lookup"><span data-stu-id="3f593-145">Near interactions (direct)</span></span> 

<span data-ttu-id="3f593-146">HoloLens 2 unterstützt artikulierte Eingaben zur Handnachverfolgung, mit denen Sie mit Objekten interagieren können.</span><span class="sxs-lookup"><span data-stu-id="3f593-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="3f593-147">Ohne haptisches Feedback und perfekte Tiefenerkennung kann es schwierig sein zu erkennen, wie weit ihre Hand von einem Objekt entfernt ist oder ob Sie es berühren.</span><span class="sxs-lookup"><span data-stu-id="3f593-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="3f593-148">Es ist wichtig, genügend visuelle Hinweise bereitzustellen, um den Zustand des Objekts zu kommunizieren, insbesondere den Zustand Ihrer Hände basierend auf diesem Objekt.</span><span class="sxs-lookup"><span data-stu-id="3f593-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="3f593-149">Verwenden Sie visuelles Feedback, um die folgenden Zustände zu kommunizieren:</span><span class="sxs-lookup"><span data-stu-id="3f593-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="3f593-150">**Standard (Beobachtung):** Standard-Leerlaufzustand des Objekts.</span><span class="sxs-lookup"><span data-stu-id="3f593-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="3f593-151">**Zeigen** Sie auf : Wenn sich eine Hand in der Nähe eines Hologramms befindet, ändern Sie visuals, um zu kommunizieren, dass die Hand hologrammadressiert ist.</span><span class="sxs-lookup"><span data-stu-id="3f593-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="3f593-152">**Abstand und Interaktionspunkt:** Wenn sich die Hand einem Hologramm nähert, entwerfen Sie Feedback, um den projizierten Interaktionspunkt zu kommunizieren und wie weit der Finger vom Objekt entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="3f593-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="3f593-153">**Kontakt beginnt:** Ändern von Visuals (Hell, Farbe), um zu kommunizieren, dass eine Berührung aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="3f593-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="3f593-154">**Verstanden:** Visuals (Hell, Farbe) ändern, wenn das Objekt erfasst wird</span><span class="sxs-lookup"><span data-stu-id="3f593-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="3f593-155">**Kontakt endet:** Visuals ändern (Hell, Farbe), wenn die Berührung beendet wurde</span><span class="sxs-lookup"><span data-stu-id="3f593-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="3f593-156">![Zeigen mit dem Mauszeiger (weit)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="3f593-157">**Zeigen mit dem Mauszeiger (weit)**</span><span class="sxs-lookup"><span data-stu-id="3f593-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="3f593-158">Hervorhebung basierend auf der Nähe der Hand.</span><span class="sxs-lookup"><span data-stu-id="3f593-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3f593-159">![Bewegen des Mauszeigers (nah)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="3f593-160">**Bewegen des Mauszeigers (nah)**</span><span class="sxs-lookup"><span data-stu-id="3f593-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="3f593-161">Heben Sie Größenänderungen basierend auf dem Abstand zur Hand hervor.</span><span class="sxs-lookup"><span data-stu-id="3f593-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="3f593-162">![Toucheingabe/Drücken](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="3f593-163">**Toucheingabe/Drücken**</span><span class="sxs-lookup"><span data-stu-id="3f593-163">**Touch / press**</span></span><br>
        <span data-ttu-id="3f593-164">Visuelles und Audiofeedback.</span><span class="sxs-lookup"><span data-stu-id="3f593-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3f593-165">![Begreifen](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="3f593-166">**Begreifen**</span><span class="sxs-lookup"><span data-stu-id="3f593-166">**Grasp**</span></span><br>
        <span data-ttu-id="3f593-167">Visuelles und Audiofeedback.</span><span class="sxs-lookup"><span data-stu-id="3f593-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="3f593-168">Eine [Schaltfläche auf HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) ist ein Beispiel dafür, wie die verschiedenen Eingabeinteraktionszustände visualisiert werden:</span><span class="sxs-lookup"><span data-stu-id="3f593-168">A [button on HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3f593-169">![Standard](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="3f593-170">**Standard**</span><span class="sxs-lookup"><span data-stu-id="3f593-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3f593-171">![Darauf zeigen (Hover)](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="3f593-172">**Darauf zeigen (Hover)**</span><span class="sxs-lookup"><span data-stu-id="3f593-172">**Hover**</span></span><br>
        <span data-ttu-id="3f593-173">Zeigen Sie einen näherungsbasierten Beleuchtungseffekt an.</span><span class="sxs-lookup"><span data-stu-id="3f593-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="3f593-174">![Toucheingabe](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="3f593-175&quot;>**Toucheingabe**</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3f593-175&quot;>**Touch**</span></span><br>
        <span data-ttu-id=&quot;3f593-176&quot;>Show effect (Effekt &quot;Welleneffekt anzeigen").</span><span class="sxs-lookup"><span data-stu-id="3f593-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3f593-177">![Tastenkombination](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="3f593-178">**Presse**</span><span class="sxs-lookup"><span data-stu-id="3f593-178">**Press**</span></span><br>
        <span data-ttu-id="3f593-179">Verschieben Sie die Vorderseite.</span><span class="sxs-lookup"><span data-stu-id="3f593-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="3f593-180">Der visuelle Hinweis "Ring" auf HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3f593-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="3f593-181">Auf HoloLens 2 gibt es einen zusätzlichen visuellen Hinweis, der dem Benutzer bei der Wahrnehmung der Tiefe helfen kann.</span><span class="sxs-lookup"><span data-stu-id="3f593-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="3f593-182">Ein Ring in der Nähe der Fingerspitze wird nach oben angezeigt und herunterskaliert, wenn sich die Fingerspitze dem Objekt nähert.</span><span class="sxs-lookup"><span data-stu-id="3f593-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="3f593-183">Der Ring konvergiert schließlich zu einem Punkt, wenn der gedrückte Zustand erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="3f593-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="3f593-184">Dieses visuelle Erscheinungsbild hilft dem Benutzer zu verstehen, wie weit er vom Objekt entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="3f593-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="3f593-185">*Videoschleife: Beispiel für visuelles Feedback basierend auf der Nähe zu einem Begrenzungsfeld*</span><span class="sxs-lookup"><span data-stu-id="3f593-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3f593-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3f593-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="3f593-187">![Visuelles Feedback zur Handnähe](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="3f593-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="3f593-188">Audiohinweise</span><span class="sxs-lookup"><span data-stu-id="3f593-188">Audio cues</span></span>

<span data-ttu-id="3f593-189">Bei direkten Handinteraktionen kann das richtige Audiofeedback die Benutzerfreundlichkeit erheblich verbessern.</span><span class="sxs-lookup"><span data-stu-id="3f593-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="3f593-190">Verwenden Sie Audiofeedback, um die folgenden Hinweise zu kommunizieren:</span><span class="sxs-lookup"><span data-stu-id="3f593-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="3f593-191">**Kontakt beginnt:** Sound wiedergeben, wenn die Berührung beginnt</span><span class="sxs-lookup"><span data-stu-id="3f593-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="3f593-192">**Kontakt endet:** Sound auf Touch-Ende wiedergeben</span><span class="sxs-lookup"><span data-stu-id="3f593-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="3f593-193">**Greifen beginnt:** Sound wiedergeben, wenn der Grabbing gestartet wird</span><span class="sxs-lookup"><span data-stu-id="3f593-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="3f593-194">**Ende der Nahme:** Sound wiedergeben, wenn die Grabbing-Klammer endet</span><span class="sxs-lookup"><span data-stu-id="3f593-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="3f593-195">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="3f593-195">Voice commanding</span></span><br>
        <span data-ttu-id="3f593-196">Für alle interaktivierbaren Objekte ist es wichtig, alternative Interaktionsoptionen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="3f593-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="3f593-197">Standardmäßig wird empfohlen, [sprachgesteuerte Befehle](../out-of-scope/voice-design.md) für alle Objekte zu unterstützen, die interaktiv sind.</span><span class="sxs-lookup"><span data-stu-id="3f593-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="3f593-198">Um die Auffindbarkeit zu verbessern, können Sie auch während des Mauszeigerzustands eine QuickInfo bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3f593-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="3f593-199">*Bild: QuickInfo für den Sprachbefehl*</span><span class="sxs-lookup"><span data-stu-id="3f593-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![Sprachbefehle](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a><span data-ttu-id="3f593-201">Größenempfehlungen</span><span class="sxs-lookup"><span data-stu-id="3f593-201">Sizing recommendations</span></span>

<span data-ttu-id="3f593-202">Um sicherzustellen, dass alle interagierbaren Objekte problemlos berührt werden können, empfiehlt es sich, sicherzustellen, dass das interaktionsfähige Objekt basierend auf der Entfernung, die er vom Benutzer platziert wird, eine Mindestgröße erfüllt.</span><span class="sxs-lookup"><span data-stu-id="3f593-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="3f593-203">Der visuelle Winkel wird häufig in Grad des visuellen Bogens gemessen. Der visuelle Winkel basiert auf dem Abstand zwischen den Augen des Benutzers und dem Objekt und bleibt konstant, während sich die physische Größe des Ziels ändern kann, wenn sich der Abstand zum Benutzer ändert.</span><span class="sxs-lookup"><span data-stu-id="3f593-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="3f593-204">Um die erforderliche physische Größe eines Objekts basierend auf der Entfernung vom Benutzer zu bestimmen, versuchen Sie, einen visuellen Winkelrechner wie diesen [zu verwenden.](https://elvers.us/perception/visualAngle/)</span><span class="sxs-lookup"><span data-stu-id="3f593-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="3f593-205">Im Folgenden finden Sie die Empfehlungen für die Mindestgröße von interaktionsfähigem Inhalt.</span><span class="sxs-lookup"><span data-stu-id="3f593-205">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="3f593-206">Zielgröße für direkte Handinteraktion</span><span class="sxs-lookup"><span data-stu-id="3f593-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="3f593-207">Entfernung</span><span class="sxs-lookup"><span data-stu-id="3f593-207">Distance</span></span> | <span data-ttu-id="3f593-208">Betrachtungswinkel</span><span class="sxs-lookup"><span data-stu-id="3f593-208">Viewing angle</span></span> | <span data-ttu-id="3f593-209">Size</span><span class="sxs-lookup"><span data-stu-id="3f593-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="3f593-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="3f593-210">45 cm</span></span>  | <span data-ttu-id="3f593-211">nicht kleiner als 2°</span><span class="sxs-lookup"><span data-stu-id="3f593-211">no smaller than 2°</span></span> | <span data-ttu-id="3f593-212">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="3f593-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="3f593-213">![Zielgröße für direkte Handinteraktion](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="3f593-214">*Zielgröße für direkte Handinteraktion*</span><span class="sxs-lookup"><span data-stu-id="3f593-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="3f593-215">Zielgröße für Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="3f593-215">Target size for buttons</span></span>

<span data-ttu-id="3f593-216">Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass ausreichend Platz für ein Symbol und möglicherweise text vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3f593-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="3f593-217">Entfernung</span><span class="sxs-lookup"><span data-stu-id="3f593-217">Distance</span></span> | <span data-ttu-id="3f593-218">Mindestgröße</span><span class="sxs-lookup"><span data-stu-id="3f593-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="3f593-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="3f593-219">45 cm</span></span>  | <span data-ttu-id="3f593-220">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="3f593-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="3f593-221">![Zielgröße für die Schaltflächen](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="3f593-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="3f593-222">*Zielgröße für die Schaltflächen*</span><span class="sxs-lookup"><span data-stu-id="3f593-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="3f593-223">Zielgröße für Handstrahl- oder Anvizeinteraktion</span><span class="sxs-lookup"><span data-stu-id="3f593-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="3f593-224">Entfernung</span><span class="sxs-lookup"><span data-stu-id="3f593-224">Distance</span></span> | <span data-ttu-id="3f593-225">Betrachtungswinkel</span><span class="sxs-lookup"><span data-stu-id="3f593-225">Viewing angle</span></span> | <span data-ttu-id="3f593-226">Size</span><span class="sxs-lookup"><span data-stu-id="3f593-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="3f593-227">2 m</span><span class="sxs-lookup"><span data-stu-id="3f593-227">2 m</span></span>  | <span data-ttu-id="3f593-228">nicht kleiner als 1°</span><span class="sxs-lookup"><span data-stu-id="3f593-228">no smaller than 1°</span></span> | <span data-ttu-id="3f593-229">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="3f593-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="3f593-230">![Zielgröße für Handstrahl- oder Anvizeinteraktion](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f593-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="3f593-231">*Zielgröße für Handstrahl- oder Anvizeinteraktion*</span><span class="sxs-lookup"><span data-stu-id="3f593-231">*Target size for hand ray or gaze interaction*</span></span>

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="3f593-232">Interagierbares Objekt im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="3f593-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="3f593-233">In **[MRTK können](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Sie das Skript [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) verwenden, um Objekte auf verschiedene Typen von Eingabeinteraktionszuständen reagieren zu lassen.</span><span class="sxs-lookup"><span data-stu-id="3f593-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="3f593-234">Es unterstützt verschiedene Arten von Designs, mit denen Sie visuelle Zustände definieren können, indem Sie Objekteigenschaften wie Farbe, Größe, Material und Shader steuern.</span><span class="sxs-lookup"><span data-stu-id="3f593-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="3f593-235">Interaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="3f593-235">Interactable</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* <span data-ttu-id="3f593-236">[Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="3f593-236">[Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)</span></span>
* [<span data-ttu-id="3f593-237">Handinteraktionsbeispiele (Szene)</span><span class="sxs-lookup"><span data-stu-id="3f593-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="3f593-238">Der Standard-Shader von MixedRealityToolkit  bietet verschiedene Optionen, z. B. näherungslicht, das Ihnen hilft, visuelle und Audio-Hinweise zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3f593-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>

* [<span data-ttu-id="3f593-239">MRTK-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="3f593-239">MRTK Standard Shader</span></span>](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="3f593-240">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3f593-240">See also</span></span>

* [<span data-ttu-id="3f593-241">Cursor</span><span class="sxs-lookup"><span data-stu-id="3f593-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="3f593-242">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="3f593-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="3f593-243">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="3f593-243">Button</span></span>](button.md)
* [<span data-ttu-id="3f593-244">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="3f593-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="3f593-245">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="3f593-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="3f593-246">Manipulation</span><span class="sxs-lookup"><span data-stu-id="3f593-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3f593-247">Handmenü</span><span class="sxs-lookup"><span data-stu-id="3f593-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="3f593-248">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="3f593-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="3f593-249">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="3f593-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="3f593-250">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="3f593-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="3f593-251">Tastatur</span><span class="sxs-lookup"><span data-stu-id="3f593-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="3f593-252">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="3f593-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="3f593-253">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="3f593-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="3f593-254">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="3f593-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="3f593-255">Shader</span><span class="sxs-lookup"><span data-stu-id="3f593-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="3f593-256">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="3f593-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="3f593-257">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="3f593-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="3f593-258">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="3f593-258">Surface magnetism</span></span>](surface-magnetism.md)