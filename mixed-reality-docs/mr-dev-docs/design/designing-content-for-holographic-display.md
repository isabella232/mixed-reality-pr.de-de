---
title: Entwerfen von Inhalten für die holografische Anzeige
description: Erfahren Sie mehr über Entwurfs Richtlinien und bewährte Methoden für die holografische Anzeige auf hololens-Geräten.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Design der Benutzeroberfläche, holografische Anzeige, Inhalts Design, dunkles Design, helle Themen, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Design, Pixel
ms.openlocfilehash: 6bf65b9e40e42f1609b1108b366ac65637fcf106
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759275"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="0a96e-104">Entwerfen von Inhalten für die holografische Anzeige</span><span class="sxs-lookup"><span data-stu-id="0a96e-104">Designing content for holographic display</span></span>

![Ulnar Seitenposition](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="0a96e-106">Beim Entwerfen von Inhalten für Holographic-anzeigen müssen Sie mehrere Elemente beachten, um die bestmögliche Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="0a96e-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="0a96e-107">Wir haben einige unserer unten aufgeführten Empfehlungen aufgelistet, und Sie können mehr über die Merkmale der Holographic-Anzeige auf der Seite [Farbe, hell und Material](color-light-and-materials.md) erfahren.</span><span class="sxs-lookup"><span data-stu-id="0a96e-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="0a96e-108">Herausforderungen mit heller Farbe auf hoher Oberfläche</span><span class="sxs-lookup"><span data-stu-id="0a96e-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="0a96e-109">Basierend auf unseren hololens-Forschungs-und Testzwecken haben wir festgestellt, dass die Verwendung von hellen Farben in einem großen Bereich der Anzeige verschiedene Probleme verursachen kann:</span><span class="sxs-lookup"><span data-stu-id="0a96e-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="0a96e-110">**Augen Müdigkeit**</span><span class="sxs-lookup"><span data-stu-id="0a96e-110">**Eye fatigue**</span></span> 

<span data-ttu-id="0a96e-111">Da die holografische Anzeige Additiv ist, verwenden holograms mit hellen Farben mehr Licht.</span><span class="sxs-lookup"><span data-stu-id="0a96e-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="0a96e-112">Eine helle, voll Tonfarbe in einem großen Bereich der Anzeige kann die Augen Müdigkeit für den Benutzer leicht auslösen.</span><span class="sxs-lookup"><span data-stu-id="0a96e-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="0a96e-113">**Hand Okklusion**</span><span class="sxs-lookup"><span data-stu-id="0a96e-113">**Hand occlusion**</span></span> 

<span data-ttu-id="0a96e-114">Durch eine helle Farbe ist es für den Benutzer schwierig, die Hände bei direkter Interaktion mit Objekten zu sehen.</span><span class="sxs-lookup"><span data-stu-id="0a96e-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="0a96e-115">Da der Benutzer seine Hände nicht sehen kann, ist es schwierig, die Tiefe/Entfernung zwischen der Hand/dem Finger und der Ziel Oberfläche zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="0a96e-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="0a96e-116">Mit dem Finger Cursor kann dieses Problem kompensiert werden, aber es kann auf einer hellen weißen Oberfläche immer noch eine Herausforderung darstellen.</span><span class="sxs-lookup"><span data-stu-id="0a96e-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="0a96e-117">![Die Farb-und Handzeichen-oksion ist ](images/color_handocclusion.jpg)
 *schwierig, um das Hintergrundbild der hellfarbigen Inhalte anzuzeigen* .</span><span class="sxs-lookup"><span data-stu-id="0a96e-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="0a96e-118">**Farb Einheitlichkeit**</span><span class="sxs-lookup"><span data-stu-id="0a96e-118">**Color uniformity**</span></span>

<span data-ttu-id="0a96e-119">Aufgrund der Merkmale von Holographic-anzeigen kann ein großer heller Bereich in der Anzeige zu einem blobbereich werden.</span><span class="sxs-lookup"><span data-stu-id="0a96e-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="0a96e-120">Durch die Verwendung von dunklen Farbschemas können Sie dieses Problem minimieren.</span><span class="sxs-lookup"><span data-stu-id="0a96e-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="0a96e-121">Entwurfs Richtlinien für Farbauswahl</span><span class="sxs-lookup"><span data-stu-id="0a96e-121">Design guidelines for color choices</span></span>

<span data-ttu-id="0a96e-122">**Verwenden Sie die dunkle Farbe für den UI-Hintergrund.**</span><span class="sxs-lookup"><span data-stu-id="0a96e-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="0a96e-123">Mithilfe des dunklen Farbschemas können Sie die Augen Müdigkeit minimieren und die Zuversicht bei direkten Interaktionen verbessern.</span><span class="sxs-lookup"><span data-stu-id="0a96e-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="0a96e-124">![Beispiele für dunkle Farben, die für die Inhalts Hintergrund Beispiele für dunkle Farben verwendet werden, ](images/color_dark_examples.jpg)
 *die für den Inhalts Hintergrund verwendet werden* .</span><span class="sxs-lookup"><span data-stu-id="0a96e-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="0a96e-125">**Semibold oder Fett formatierte Schrift Breite verwenden**</span><span class="sxs-lookup"><span data-stu-id="0a96e-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="0a96e-126">Hololens ermöglicht Ihnen die Anzeige von schönem Text mit hoher Auflösung.</span><span class="sxs-lookup"><span data-stu-id="0a96e-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="0a96e-127">Es wird jedoch empfohlen, schlanke Schrift Gewichtungen, wie z. b. Light oder semilight, zu vermeiden, da die vertikalen Striche in einem kleinen Schrift Grad jitterchen können.</span><span class="sxs-lookup"><span data-stu-id="0a96e-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="0a96e-128">![Die Schrift Breite "Fett" oder "Semibold" (oberer Bereich) verbessert die Lesbarkeit ](images/color_font_examples.jpg)
 *oder das Semibold-Schriftgewicht (oberer Bereich) und verbessert die Lesbarkeit* .</span><span class="sxs-lookup"><span data-stu-id="0a96e-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="0a96e-129">**Verwenden des holographicbackplate-Materials von mrtk**</span><span class="sxs-lookup"><span data-stu-id="0a96e-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="0a96e-130">Das holographicbackplate-Material wird auf mehrere Benutzeroberflächen Panels in der hololens-Shell angewendet.</span><span class="sxs-lookup"><span data-stu-id="0a96e-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="0a96e-131">Eines seiner Features ist ein Iridescence-Effekt, der für Benutzer sichtbar ist, wenn Sie Ihre Position basierend auf dem Panel verschieben.</span><span class="sxs-lookup"><span data-stu-id="0a96e-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="0a96e-132">Die Hintergrundfarbe verschiebt sich ganz leicht über ein vordefiniertes Spektrum, sodass ein ansprechender und dynamischer visueller Effekt entsteht, ohne die Lesbarkeit von Inhalten zu beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="0a96e-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="0a96e-133">Diese feine UMSCHALT Farbe dient auch zur Kompensation geringfügiger Farb Unregelmäßigkeiten.</span><span class="sxs-lookup"><span data-stu-id="0a96e-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="0a96e-134">Herausforderungen mit transparenten oder durchlässigen UI-Backplate</span><span class="sxs-lookup"><span data-stu-id="0a96e-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="0a96e-135">![Transparente Benutzeroberflächen Beispiele ](images/color_transparent_examples.jpg)
 *Beispiele für transparente UI-Backplate*</span><span class="sxs-lookup"><span data-stu-id="0a96e-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="0a96e-136">**Visuelle Komplexität und Barrierefreiheit**</span><span class="sxs-lookup"><span data-stu-id="0a96e-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="0a96e-137">Da Holographic Objects mit der physischen Umgebung in Blend integriert ist, kann der Inhalt oder die Benutzeroberflächen-Lesbarkeit bei transparenten oder durchlässigen Fenstern beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="0a96e-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="0a96e-138">Darüber hinaus kann es bei der Überlagerung transparenter Holographic-Objekte aufgrund der verwirrenden Tiefe schwierig sein, eine Interaktion zwischen den Benutzern zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="0a96e-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="0a96e-139">**Leistung**</span><span class="sxs-lookup"><span data-stu-id="0a96e-139">**Performance**</span></span>

<span data-ttu-id="0a96e-140">Damit transparente oder über lässiges Objekte ordnungsgemäß dargestellt werden, müssen Sie sortiert und mit allen Objekten kombiniert werden, die im Hintergrund vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="0a96e-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="0a96e-141">Das Sortieren von transparenten Objekten hat eine geringe Anzahl von CPU-Kosten. die Kombination hat beträchtliche GPU-Kosten, da die GPU keine ausgeblendete Oberflächen Entfernung durch z-Culling ermöglicht (d. h.</span><span class="sxs-lookup"><span data-stu-id="0a96e-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="0a96e-142">tiefen Tests).</span><span class="sxs-lookup"><span data-stu-id="0a96e-142">depth testing).</span></span> <span data-ttu-id="0a96e-143">Durch das Entfernen ausgeblendeter Oberflächen wird die Anzahl der für das endgültige gerenderte Pixel benötigten Vorgänge erhöht</span><span class="sxs-lookup"><span data-stu-id="0a96e-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="0a96e-144">Dadurch werden die Einschränkungen bei den Füll Raten übereinungen eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="0a96e-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="0a96e-145">**Hologram-Stabilitätsproblem mit der tiefen LSR-Technologie**</span><span class="sxs-lookup"><span data-stu-id="0a96e-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="0a96e-146">Um die Holographic-neuprojektion bzw. – Hologramm-Stabilität zu verbessern, kann eine Anwendung für jeden gerenderten Frame einen tiefen Puffer an das System übermitteln.</span><span class="sxs-lookup"><span data-stu-id="0a96e-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="0a96e-147">Wenn Sie den tiefen Puffer für die neuprojektion verwenden, müssen Sie für jedes geenderten Pixel einen tiefen Puffer mit entsprechender Tiefe schreiben.</span><span class="sxs-lookup"><span data-stu-id="0a96e-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="0a96e-148">Jedes Pixel mit einem tiefen Wert sollte auch einen Farbwert aufweisen.</span><span class="sxs-lookup"><span data-stu-id="0a96e-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="0a96e-149">Wenn die oben genannten Anleitungen nicht befolgt werden, können Bereiche des gerenderten Bilds, die keine gültigen Tiefeninformationen aufweisen, auf eine Weise neu projiziert werden, die Artefakte erzeugt, die häufig als Wellen ähnliche Verzerrung sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="0a96e-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="0a96e-150">Entwurfs Richtlinien für transparente Elemente</span><span class="sxs-lookup"><span data-stu-id="0a96e-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="0a96e-151">**Verwenden von undurchsichtigem UI-Hintergrund**</span><span class="sxs-lookup"><span data-stu-id="0a96e-151">**Use opaque UI background**</span></span>

<span data-ttu-id="0a96e-152">Standardmäßig werden von transparenten oder durchlässigen Objekten keine tiefen geschrieben, um eine ordnungsgemäße Mischung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="0a96e-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="0a96e-153">Zu den Möglichkeiten, dieses Problem zu beheben, gehören die Verwendung von nicht transparenten Objekten, das sicherstellen, dass die übergreifenden Objekte nahe bei nicht transparenten Objekten angezeigt werden (z. b. eine durchlässige Schaltfläche vor einem nicht transparenten Backplate), das Erzwingen von durchlässigen Objekten, um Tiefe (nicht in allen Szenarien zutreffend) und das Rendern von Proxy Objekten zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="0a96e-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="0a96e-154">Lösungen in mrtk-Unity: https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="0a96e-154">Solutions within MRTK-Unity: https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="0a96e-155">Durch die Verwendung eines soliden und nicht transparenten Backplate können wir die Zuverlässigkeit und Interaktion gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="0a96e-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="0a96e-156">**Minimieren der Anzahl der betroffenen Pixel**</span><span class="sxs-lookup"><span data-stu-id="0a96e-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="0a96e-157">Wenn das Projekt transparente Objekte verwenden muss, versuchen Sie, die Anzahl der betroffenen Pixel zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="0a96e-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="0a96e-158">Wenn ein Objekt z. b. nur unter bestimmten Bedingungen (z. b. einem Additiven Glanzeffekt) sichtbar ist, deaktivieren Sie das Objekt, wenn es vollständig unsichtbar ist (anstatt die Additiv Farbe auf schwarz festzulegen).</span><span class="sxs-lookup"><span data-stu-id="0a96e-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="0a96e-159">Für einfache 2D-Formen, die mit einem Quad mit einer Alpha Maske erstellt wurden, sollten Sie stattdessen eine Gitterdarstellung der Form mit einem nicht transparenten Shader erstellen.</span><span class="sxs-lookup"><span data-stu-id="0a96e-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="0a96e-160">Beispiele für dunkle Benutzeroberflächen in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="0a96e-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="0a96e-161">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** bietet viele Beispiele für Benutzeroberflächen Bausteine, die auf den dunklen Farbschemas basieren.</span><span class="sxs-lookup"><span data-stu-id="0a96e-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="0a96e-162">Near-Menü</span><span class="sxs-lookup"><span data-stu-id="0a96e-162">Near Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/near-menu.md)
* [<span data-ttu-id="0a96e-163">Dialogfeld</span><span class="sxs-lookup"><span data-stu-id="0a96e-163">Dialog</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/dialog.md)
* [<span data-ttu-id="0a96e-164">Hand Menü</span><span class="sxs-lookup"><span data-stu-id="0a96e-164">Hand Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md)

<br>

---

## <a name="see-also"></a><span data-ttu-id="0a96e-165">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0a96e-165">See also</span></span>

* [<span data-ttu-id="0a96e-166">Farbe, Licht und Materialien</span><span class="sxs-lookup"><span data-stu-id="0a96e-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="0a96e-167">Cursor</span><span class="sxs-lookup"><span data-stu-id="0a96e-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="0a96e-168">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="0a96e-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="0a96e-169">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="0a96e-169">Button</span></span>](button.md)
* [<span data-ttu-id="0a96e-170">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="0a96e-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="0a96e-171">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="0a96e-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="0a96e-172">Manipulation</span><span class="sxs-lookup"><span data-stu-id="0a96e-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0a96e-173">Handmenü</span><span class="sxs-lookup"><span data-stu-id="0a96e-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="0a96e-174">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="0a96e-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="0a96e-175">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="0a96e-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="0a96e-176">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="0a96e-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="0a96e-177">Tastatur</span><span class="sxs-lookup"><span data-stu-id="0a96e-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="0a96e-178">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="0a96e-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="0a96e-179">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="0a96e-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="0a96e-180">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="0a96e-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="0a96e-181">Shader</span><span class="sxs-lookup"><span data-stu-id="0a96e-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="0a96e-182">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="0a96e-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="0a96e-183">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="0a96e-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="0a96e-184">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="0a96e-184">Surface magnetism</span></span>](surface-magnetism.md)
