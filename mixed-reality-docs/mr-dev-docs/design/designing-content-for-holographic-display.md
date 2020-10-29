---
title: Entwerfen von Inhalten für die holografische Anzeige
description: Entwurfs Richtlinien und bewährte Methoden für die holografische Anzeige
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Design der Benutzeroberfläche, holografische Anzeige, Inhalts Design, dunkles Design, helles Design
ms.openlocfilehash: 627ffdd0a413ad3140c29e9b1c7bb69c9dc249cf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686110"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="c0431-104">Entwerfen von Inhalten für die holografische Anzeige</span><span class="sxs-lookup"><span data-stu-id="c0431-104">Designing content for holographic display</span></span>

![Ulnar Seitenposition](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="c0431-106">Beim Entwerfen von Inhalten für Holographic-anzeigen müssen Sie mehrere Elemente beachten, um die bestmögliche Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="c0431-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="c0431-107">Wir haben einige unserer unten aufgeführten Empfehlungen aufgelistet, und Sie können mehr über die Merkmale der Holographic-Anzeige auf der Seite [Farbe, hell und Material](color-light-and-materials.md) erfahren.</span><span class="sxs-lookup"><span data-stu-id="c0431-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="c0431-108">Herausforderungen mit heller Farbe auf hoher Oberfläche</span><span class="sxs-lookup"><span data-stu-id="c0431-108">Challenges with bright color on a large surface</span></span> 
<span data-ttu-id="c0431-109">Basierend auf unserer Recherche und dem Testen verschiedener Arten von hololens-Erfahrungen haben wir festgestellt, dass die Verwendung von hellen Farben in einem großen Bereich der Anzeige verschiedene Probleme verursachen kann:</span><span class="sxs-lookup"><span data-stu-id="c0431-109">Based on our user research and testing on various types of HoloLens experiences, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="c0431-110">**Augen Müdigkeit**</span><span class="sxs-lookup"><span data-stu-id="c0431-110">**Eye fatigue**</span></span> 

<span data-ttu-id="c0431-111">Da die holografische Anzeige Additiv ist, verwendet die helle Farbe zum Anzeigen von holograms mehr Licht.</span><span class="sxs-lookup"><span data-stu-id="c0431-111">Since holographic display is additive, bright color uses more light to display holograms.</span></span> <span data-ttu-id="c0431-112">Eine helle, voll Tonfarbe in einem großen Bereich der Anzeige kann die Augen Müdigkeit für den Benutzer leicht auslösen.</span><span class="sxs-lookup"><span data-stu-id="c0431-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="c0431-113">**Hand Okklusion**</span><span class="sxs-lookup"><span data-stu-id="c0431-113">**Hand occlusion**</span></span> 

<span data-ttu-id="c0431-114">Durch eine helle Farbe ist es für den Benutzer schwierig, die Hände bei direkter Interaktion mit Objekten zu sehen.</span><span class="sxs-lookup"><span data-stu-id="c0431-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="c0431-115">Da der Benutzer seine Hände nicht sehen kann, ist es schwierig, die Tiefe/Entfernung zwischen der Hand/dem Finger und der Ziel Oberfläche zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="c0431-115">Since the user cannot see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="c0431-116">Mit dem Finger Cursor kann dieses Problem kompensiert werden, aber es kann auf einer hellen weißen Oberfläche immer noch eine Herausforderung darstellen.</span><span class="sxs-lookup"><span data-stu-id="c0431-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="c0431-117">![Die Farb-und Handzeichen-oksion ist ](images/color_handocclusion.jpg)
 *schwierig, um das Hintergrundbild der hellfarbigen Inhalte anzuzeigen* .</span><span class="sxs-lookup"><span data-stu-id="c0431-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="c0431-118">**Farb Einheitlichkeit**</span><span class="sxs-lookup"><span data-stu-id="c0431-118">**Color uniformity**</span></span>

<span data-ttu-id="c0431-119">Aufgrund der Merkmale von Holographic-anzeigen kann ein großer heller Bereich in der Anzeige zu einem blobbereich werden.</span><span class="sxs-lookup"><span data-stu-id="c0431-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="c0431-120">Durch die Verwendung von dunklen Farbschemas können Sie dieses Problem minimieren.</span><span class="sxs-lookup"><span data-stu-id="c0431-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines"></a><span data-ttu-id="c0431-121">Entwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="c0431-121">Design guidelines</span></span>

<span data-ttu-id="c0431-122">**Verwenden Sie die dunkle Farbe für den UI-Hintergrund.**</span><span class="sxs-lookup"><span data-stu-id="c0431-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="c0431-123">Mithilfe des dunklen Farbschemas können Sie die Augen Müdigkeit minimieren und die Zuversicht bei direkten Interaktionen verbessern.</span><span class="sxs-lookup"><span data-stu-id="c0431-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="c0431-124">![Beispiele für dunkle Benutzeroberflächen Beispiele für ](images/color_dark_examples.jpg)
 *dunkle Farben, die für den Inhalts Hintergrund verwendet werden*</span><span class="sxs-lookup"><span data-stu-id="c0431-124">![Dark UI examples](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="c0431-125">**Semibold oder Fett formatierte Schrift Breite verwenden**</span><span class="sxs-lookup"><span data-stu-id="c0431-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="c0431-126">Hololens ermöglicht Ihnen die Anzeige von schönem Text mit hoher Auflösung.</span><span class="sxs-lookup"><span data-stu-id="c0431-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="c0431-127">Es wird jedoch empfohlen, schlanke Schriftart Gewichtungen, wie z. b. Light oder semilight, zu vermeiden, da die vertikalen Striche in einem kleinen Schrift Grad Jitter sind.</span><span class="sxs-lookup"><span data-stu-id="c0431-127">However, it is recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="c0431-128">![Dunkle UI-Beispiele ](images/color_font_examples.jpg)
 *Fett oder Semibold Schrift Breite (oberer Bereich) verbessert die Lesbarkeit*</span><span class="sxs-lookup"><span data-stu-id="c0431-128">![Dark UI examples](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="c0431-129">**Verwenden des holographicbackplate-Materials von mrtk**</span><span class="sxs-lookup"><span data-stu-id="c0431-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="c0431-130">Das holographicbackplate-Material wird auf mehrere Benutzeroberflächen Panels in der hololens-Shell angewendet.</span><span class="sxs-lookup"><span data-stu-id="c0431-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="c0431-131">Eine seiner Features ist ein Iridescence-Effekt, der für Benutzer sichtbar ist, wenn Sie Ihre Position in Bezug auf den Bereich verschieben.</span><span class="sxs-lookup"><span data-stu-id="c0431-131">One of its features is an iridescence effect that is visible to users as they shift their position in relation to the panel.</span></span> <span data-ttu-id="c0431-132">Die Hintergrundfarbe verschiebt sich ganz leicht über ein vordefiniertes Spektrum, sodass ein ansprechender und dynamischer visueller Effekt entsteht, ohne die Lesbarkeit von Inhalten zu beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="c0431-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="c0431-133">Diese feine UMSCHALT Farbe dient auch zur Kompensation geringfügiger Farb Unregelmäßigkeiten.</span><span class="sxs-lookup"><span data-stu-id="c0431-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="c0431-134">Herausforderungen mit transparenten oder durchlässigen UI-Backplate</span><span class="sxs-lookup"><span data-stu-id="c0431-134">Challenges with transparent or translucent UI backplate</span></span> 
<span data-ttu-id="c0431-135">![Transparente Benutzeroberflächen Beispiele ](images/color_transparent_examples.jpg)
 *Beispiele für transparente UI-Backplate*</span><span class="sxs-lookup"><span data-stu-id="c0431-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="c0431-136">**Visuelle Komplexität und Barrierefreiheit**</span><span class="sxs-lookup"><span data-stu-id="c0431-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="c0431-137">Da Holographic-Objekte mit der physischen Umgebung kombiniert werden, kann die Lesbarkeit des Inhalts oder der Benutzeroberfläche im transparenten oder durchlässigen Fenster beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="c0431-137">Since holographic objects are blended with the physical environment, the legibility of the content or UI on the transparent or translucent window could be degraded.</span></span> <span data-ttu-id="c0431-138">Darüber hinaus kann es bei der Überlagerung transparenter Holographic-Objekte aufgrund der verwirrenden Tiefe schwierig sein, eine Interaktion zwischen den Benutzern zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c0431-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="c0431-139">**Leistung**</span><span class="sxs-lookup"><span data-stu-id="c0431-139">**Performance**</span></span>

<span data-ttu-id="c0431-140">Damit transparente oder über lässiges Objekte ordnungsgemäß dargestellt werden, müssen Sie sortiert und mit allen Objekten kombiniert werden, die im Hintergrund vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="c0431-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects which exist in the background.</span></span> <span data-ttu-id="c0431-141">Das Sortieren von transparenten Objekten hat eine geringe Anzahl von CPU-Kosten. die Kombination hat beträchtliche GPU-Kosten, da die GPU die ausgeblendete Oberflächen Entfernung durch z-Culling (d. h.</span><span class="sxs-lookup"><span data-stu-id="c0431-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it does not allow the GPU to perform hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="c0431-142">tiefen Tests).</span><span class="sxs-lookup"><span data-stu-id="c0431-142">depth testing).</span></span> <span data-ttu-id="c0431-143">Wenn Sie das Entfernen ausgeblendeter Oberflächen nicht zulassen, erhöht sich die Anzahl der Vorgänge, die für das endgültige gerenderte Pixel berechnet werden müssen, und erhöht somit den Druck von Füll Raten Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="c0431-143">Not allowing hidden surface removal increases the number of operations that need to be computed for the final rendered pixel, and thus puts more pressure on fill rate constraints.</span></span>

<span data-ttu-id="c0431-144">**Hologram-Stabilitätsproblem mit der tiefen LSR-Technologie**</span><span class="sxs-lookup"><span data-stu-id="c0431-144">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="c0431-145">Um die Holographic-neuprojektion bzw. – Hologramm-Stabilität zu verbessern, kann eine Anwendung für jeden gerenderten Frame einen tiefen Puffer an das System übermitteln.</span><span class="sxs-lookup"><span data-stu-id="c0431-145">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="c0431-146">Bei der Verwendung des tiefen Puffers für die neuprojektion besteht eine Regel darin, dass für jedes dargestellte Farbpixel ein entsprechender tiefen Wert in den tiefen Puffer geschrieben werden muss (und jedes Pixel mit einem tiefen Wert auch einen Farbwert aufweisen sollte).</span><span class="sxs-lookup"><span data-stu-id="c0431-146">When using the depth buffer for reprojection one rule is that for every color pixel rendered a corresponding depth value must be written to the depth buffer (and any pixel with a depth value should also have color value).</span></span> <span data-ttu-id="c0431-147">Wenn die oben genannten Anleitungen nicht befolgt werden, können Bereiche des gerenderten Bilds, die keine gültigen Tiefeninformationen aufweisen, auf eine Weise neu projiziert werden, die Artefakte erzeugt (häufig als Wellen ähnliche Verzerrung sichtbar).</span><span class="sxs-lookup"><span data-stu-id="c0431-147">If the above guidance is not followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts (often visible as a wave-like distortion).</span></span>


## <a name="design-guidelines"></a><span data-ttu-id="c0431-148">Entwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="c0431-148">Design guidelines</span></span>
<span data-ttu-id="c0431-149">**Verwenden von undurchsichtigem UI-Hintergrund**</span><span class="sxs-lookup"><span data-stu-id="c0431-149">**Use opaque UI background**</span></span>

<span data-ttu-id="c0431-150">Standardmäßig werden von transparenten oder durchlässigen Objekten keine tiefen geschrieben, um eine ordnungsgemäße Mischung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c0431-150">By default, transparent or translucent objects do not write depth to allow for proper blending.</span></span> <span data-ttu-id="c0431-151">Zu den Möglichkeiten, dieses Problem zu beheben, gehören die Verwendung von nicht transparenten Objekten, das sicherstellen, dass die übergreifenden Objekte nahe bei nicht transparenten Objekten angezeigt werden (z. b. eine durchlässige Schaltfläche vor einem nicht transparenten Backplate), das Erzwingen von durchlässigen Objekten, um Tiefe zu schreiben (in allen Szenarien nicht zutreffend), oder das Rendern von Proxy Objekten</span><span class="sxs-lookup"><span data-stu-id="c0431-151">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="c0431-152">Lösungen in mrtk-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="c0431-152">Solutions within MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="c0431-153">Durch die Verwendung eines soliden und nicht transparenten Backplate können wir die Zuverlässigkeit und Interaktion gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="c0431-153">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="c0431-154">**Minimieren der Anzahl der betroffenen Pixel**</span><span class="sxs-lookup"><span data-stu-id="c0431-154">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="c0431-155">Wenn das Projekt transparente Objekte verwenden muss, versuchen Sie, die Anzahl der betroffenen Pixel zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="c0431-155">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="c0431-156">Wenn ein Objekt z. b. nur unter bestimmten Bedingungen (wie z. b. einem Additiven Glanzeffekt) sichtbar ist, deaktivieren Sie das Objekt, wenn es vollständig unsichtbar ist (anstatt die Additiv Farbe auf schwarz festzulegen).</span><span class="sxs-lookup"><span data-stu-id="c0431-156">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it is fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="c0431-157">Für einfache 2D-Formen, die mit einem Quad mit einer Alpha Maske erstellt wurden, sollten Sie stattdessen eine Gitterdarstellung der Form mit einem nicht transparenten Shader erstellen.</span><span class="sxs-lookup"><span data-stu-id="c0431-157">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="c0431-158">Beispiele für dunkle Benutzeroberflächen in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="c0431-158">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="c0431-159">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** bietet viele Beispiele für Benutzeroberflächen Bausteine, die auf den dunklen Farbschemas basieren.</span><span class="sxs-lookup"><span data-stu-id="c0431-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="c0431-160">Near-Menü</span><span class="sxs-lookup"><span data-stu-id="c0431-160">Near Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [<span data-ttu-id="c0431-161">Dialogfeld</span><span class="sxs-lookup"><span data-stu-id="c0431-161">Dialog</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [<span data-ttu-id="c0431-162">Hand Menü</span><span class="sxs-lookup"><span data-stu-id="c0431-162">Hand Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="c0431-163">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c0431-163">See also</span></span>
* [<span data-ttu-id="c0431-164">Farbe, Licht und Materialien</span><span class="sxs-lookup"><span data-stu-id="c0431-164">Color, light and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="c0431-165">Cursor</span><span class="sxs-lookup"><span data-stu-id="c0431-165">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c0431-166">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="c0431-166">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="c0431-167">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="c0431-167">Button</span></span>](button.md)
* [<span data-ttu-id="c0431-168">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="c0431-168">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c0431-169">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="c0431-169">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c0431-170">Manipulation</span><span class="sxs-lookup"><span data-stu-id="c0431-170">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c0431-171">Handmenü</span><span class="sxs-lookup"><span data-stu-id="c0431-171">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="c0431-172">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="c0431-172">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="c0431-173">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="c0431-173">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="c0431-174">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="c0431-174">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="c0431-175">Tastatur</span><span class="sxs-lookup"><span data-stu-id="c0431-175">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="c0431-176">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="c0431-176">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="c0431-177">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="c0431-177">Slate</span></span>](slate.md)
* [<span data-ttu-id="c0431-178">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="c0431-178">Slider</span></span>](slider.md)
* [<span data-ttu-id="c0431-179">Shader</span><span class="sxs-lookup"><span data-stu-id="c0431-179">Shader</span></span>](shader.md)
* [<span data-ttu-id="c0431-180">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="c0431-180">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c0431-181">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="c0431-181">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="c0431-182">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="c0431-182">Surface magnetism</span></span>](surface-magnetism.md)
