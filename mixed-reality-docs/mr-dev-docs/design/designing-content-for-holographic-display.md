---
title: Entwerfen von Inhalten für die holografische Anzeige
description: Erfahren Sie mehr über Entwurfsrichtlinien und bewährte Methoden für die holografische Anzeige auf HoloLens-Geräten.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI-Design, holografische Anzeige, Inhaltsdesign, dunkles Design, helles Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Design, Pixel
ms.openlocfilehash: 2c68acb5478bfbd438c8bbb9dd2f8d9686bcefc5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600319"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="6e009-104">Entwerfen von Inhalten für die holografische Anzeige</span><span class="sxs-lookup"><span data-stu-id="6e009-104">Designing content for holographic display</span></span>

![Ulnar-Seitenposition](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="6e009-106">Beim Entwerfen von Inhalten für holografische Displays gibt es mehrere Elemente, die Sie berücksichtigen müssen, um die beste Erfahrung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="6e009-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="6e009-107">Wir haben einige unserer Empfehlungen unten aufgelistet, und Sie können mehr über die Merkmale von holografischen Displays auf der Seite [Farbe, Licht und Materialien](color-light-and-materials.md) erfahren.</span><span class="sxs-lookup"><span data-stu-id="6e009-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="6e009-108">Herausforderungen mit hellem Farbton auf einer großen Oberfläche</span><span class="sxs-lookup"><span data-stu-id="6e009-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="6e009-109">Basierend auf unseren HoloLens-Erfahrungsforschungen und -Tests haben wir festgestellt, dass die Verwendung von hellen Farben in einem großen Bereich der Anzeige mehrere Probleme verursachen kann:</span><span class="sxs-lookup"><span data-stu-id="6e009-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="6e009-110">**Augenermüdung**</span><span class="sxs-lookup"><span data-stu-id="6e009-110">**Eye fatigue**</span></span> 

<span data-ttu-id="6e009-111">Da die holografische Anzeige additiv ist, verwenden Hologramme mit hellen Farben mehr Licht.</span><span class="sxs-lookup"><span data-stu-id="6e009-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="6e009-112">Helle, volltonige Farbe in einem großen Bereich der Anzeige kann für den Benutzer leicht zu Sehmüdigkeit führen.</span><span class="sxs-lookup"><span data-stu-id="6e009-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="6e009-113">**Handverdecken**</span><span class="sxs-lookup"><span data-stu-id="6e009-113">**Hand occlusion**</span></span> 

<span data-ttu-id="6e009-114">Helle Farben erschweren es dem Benutzer, seine Hände zu sehen, wenn er direkt mit Objekten interagiert.</span><span class="sxs-lookup"><span data-stu-id="6e009-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="6e009-115">Da der Benutzer seine Hände nicht sehen kann, wird es schwierig, die Tiefe/Entfernung zwischen der Hand/dem Finger und der Zieloberfläche zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="6e009-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="6e009-116">Der Fingercursor hilft dabei, dieses Problem zu kompensieren, kann aber auf einer weißen Oberfläche immer noch eine Herausforderung darstellen.</span><span class="sxs-lookup"><span data-stu-id="6e009-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="6e009-117">![Farbe und Handver occlusion Schwierig, die Hand auf der farbigen ](images/color_handocclusion.jpg)
 *Inhalts-Hintergrundbaustein zu sehen*</span><span class="sxs-lookup"><span data-stu-id="6e009-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="6e009-118">**Farbeinheitlichkeit**</span><span class="sxs-lookup"><span data-stu-id="6e009-118">**Color uniformity**</span></span>

<span data-ttu-id="6e009-119">Aufgrund der Merkmale von holografischen Displays kann ein großer, heller Bereich auf der Anzeige zu Blotogramm werden.</span><span class="sxs-lookup"><span data-stu-id="6e009-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="6e009-120">Mithilfe von dunklen Farbschemas können Sie dieses Problem minimieren.</span><span class="sxs-lookup"><span data-stu-id="6e009-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="6e009-121">Entwurfsrichtlinien für Farboptionen</span><span class="sxs-lookup"><span data-stu-id="6e009-121">Design guidelines for color choices</span></span>

<span data-ttu-id="6e009-122">**Verwenden der dunklen Farbe für den Ui-Hintergrund**</span><span class="sxs-lookup"><span data-stu-id="6e009-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="6e009-123">Mithilfe des dunklen Farbschemas können Sie die Augenmüdigkeit minimieren und die Konfidenz bei direkten Handinteraktionen verbessern.</span><span class="sxs-lookup"><span data-stu-id="6e009-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="6e009-124">![Beispiele für dunkle Farbe, die für den Inhaltshintergrund verwendet wird Beispiele für dunkle ](images/color_dark_examples.jpg)
 *Farbe, die für den Inhaltshintergrund verwendet wird*</span><span class="sxs-lookup"><span data-stu-id="6e009-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="6e009-125">**Verwenden der Schriftgewichtung "semibold" oder "bold"**</span><span class="sxs-lookup"><span data-stu-id="6e009-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="6e009-126">HoloLens ermöglicht es Ihrer Erfahrung, hochwertigen, hochauflösenden Text zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="6e009-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="6e009-127">Es wird jedoch empfohlen, schlanke Schriftgewichtungen wie hell oder halb hell zu vermeiden, da die vertikalen Striche in kleinem Schriftgrad jittern können.</span><span class="sxs-lookup"><span data-stu-id="6e009-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="6e009-128">![Fett oder halb fett formatiert (oberer Bereich) verbessert die Lesbarkeit Fett oder halb fett ](images/color_font_examples.jpg)
 *Schriftgrad (oberer Bereich) verbessert die Lesbarkeit.*</span><span class="sxs-lookup"><span data-stu-id="6e009-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="6e009-129">**Verwenden des HolographicBackplate-Materials des MRTK**</span><span class="sxs-lookup"><span data-stu-id="6e009-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="6e009-130">Das HolographicBackplate-Material wird auf mehrere Benutzeroberflächenpanels in der HoloLens-Shell angewendet.</span><span class="sxs-lookup"><span data-stu-id="6e009-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="6e009-131">Eines der Features ist ein irideneffekt, der für Benutzer sichtbar ist, wenn sie ihre Position basierend auf dem Panel verschieben.</span><span class="sxs-lookup"><span data-stu-id="6e009-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="6e009-132">Die Hintergrundfarbe verschiebt sich subtly über ein vordefiniertes Spektrum, wodurch ein ansprechender und dynamischer visueller Effekt ohne Beeinträchtigung der Lesbarkeit von Inhalten erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="6e009-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="6e009-133">Diese geringfügige Farbverschiebung dient auch dazu, kleinere Farbverschädigte zu kompensieren.</span><span class="sxs-lookup"><span data-stu-id="6e009-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="6e009-134">Herausforderungen bei transparenten oder transparenten UI-Hintergrundbausteinen</span><span class="sxs-lookup"><span data-stu-id="6e009-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="6e009-135">![Beispiele für transparente ](images/color_transparent_examples.jpg)
 *BenutzeroberflächenBeispiele für eine transparente Ui-Backplate*</span><span class="sxs-lookup"><span data-stu-id="6e009-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="6e009-136">**Visuelle Komplexität und Barrierefreiheit**</span><span class="sxs-lookup"><span data-stu-id="6e009-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="6e009-137">Da holografische Objekte mit der physischen Umgebung kombiniert werden, kann der Inhalt oder die Lesbarkeit der Benutzeroberfläche in transparenten oder transparenten Fenstern beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="6e009-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="6e009-138">Wenn transparente holografische Objekte übereinander überlagert werden, kann dies außerdem die Interaktion des Benutzers aufgrund der verwirrenden Tiefe erschweren.</span><span class="sxs-lookup"><span data-stu-id="6e009-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="6e009-139">**Leistung**</span><span class="sxs-lookup"><span data-stu-id="6e009-139">**Performance**</span></span>

<span data-ttu-id="6e009-140">Damit transparente oder transparente Objekte ordnungsgemäß gerendert werden können, müssen sie sortiert und mit allen Objekten kombiniert werden, die im Hintergrund vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="6e009-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="6e009-141">Das Sortieren von transparenten Objekten hat geringfügige CPU-Kosten, und das Mischen hat erhebliche GPU-Kosten, da die GPU die Entfernung verborgener Oberflächen nicht über Z-Culling (d. h.</span><span class="sxs-lookup"><span data-stu-id="6e009-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="6e009-142">Tiefentests).</span><span class="sxs-lookup"><span data-stu-id="6e009-142">depth testing).</span></span> <span data-ttu-id="6e009-143">Wenn das Entfernen ausgeblendeter Oberflächen nicht erlaubt wird, erhöht sich die Anzahl der Vorgänge, die für das endgültige gerenderte Pixel erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="6e009-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="6e009-144">Dies führt zu einer stärkeren Einschränkung der Druckfüllrate.</span><span class="sxs-lookup"><span data-stu-id="6e009-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="6e009-145">**Hologrammstabilitätsproblem mit Tiefen-LSR-Technologie**</span><span class="sxs-lookup"><span data-stu-id="6e009-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="6e009-146">Um die holografische Neuprojektion oder Hologrammstabilität zu verbessern, kann eine Anwendung für jeden gerenderten Frame einen Tiefenpuffer an das System übermitteln.</span><span class="sxs-lookup"><span data-stu-id="6e009-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="6e009-147">Wenn Sie den Tiefenpuffer für die Neuprojektion verwenden, müssen Sie einen Tiefenpuffer für jedes gerenderte Farbpixel in einer entsprechenden Tiefe schreiben.</span><span class="sxs-lookup"><span data-stu-id="6e009-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="6e009-148">Jedes Pixel mit einem Tiefenwert sollte auch einen Farbwert haben.</span><span class="sxs-lookup"><span data-stu-id="6e009-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="6e009-149">Wenn die obige Anleitung nicht befolgt wird, können Bereiche des gerenderten Bilds, die keine gültigen Tiefeninformationen enthalten, auf eine Weise neu projiziert werden, die Artefakte erzeugt, die häufig als wellenbasierte Verzerrung sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="6e009-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="6e009-150">Entwurfsrichtlinien für transparente Elemente</span><span class="sxs-lookup"><span data-stu-id="6e009-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="6e009-151">**Verwenden des Hintergrunds der nicht transparenten Benutzeroberfläche**</span><span class="sxs-lookup"><span data-stu-id="6e009-151">**Use opaque UI background**</span></span>

<span data-ttu-id="6e009-152">Standardmäßig schreiben transparente oder durchsichtige Objekte keine Tiefe, um eine ordnungsgemäße Mischung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="6e009-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="6e009-153">Zu den Möglichkeiten, dieses Problem zu beheben, gehören die Verwendung von nicht transparenten Objekten, das Sicherstellen, dass durchsichtige Objekte in der Nähe von nicht transparenten Objekten angezeigt werden (z. B. eine durchscheinende Schaltfläche vor einer nicht transparenten Hintergrundbaustein), das Erzwingen der Schreibtiefe durchscheinender Objekte (nicht in allen Szenarien anwendbar) oder das Rendern von Proxyobjekten, die nur tiefen Werte am Ende des Rahmens beitragen.</span><span class="sxs-lookup"><span data-stu-id="6e009-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="6e009-154">Lösungen in MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="6e009-154">Solutions within MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="6e009-155">Durch die Verwendung einer soliden und nicht transparenten Backplate können wir Lesbarkeit und Interaktionsvertrauen sichern.</span><span class="sxs-lookup"><span data-stu-id="6e009-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="6e009-156">**Minimieren der Anzahl der betroffenen Pixel**</span><span class="sxs-lookup"><span data-stu-id="6e009-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="6e009-157">Wenn Ihr Projekt transparente Objekte verwenden muss, versuchen Sie, die Anzahl der betroffenen Pixel zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="6e009-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="6e009-158">Wenn ein Objekt beispielsweise nur unter bestimmten Bedingungen (z. B. einem additiven Leuchteffekt) sichtbar ist, deaktivieren Sie das Objekt, wenn es vollständig unsichtbar ist (anstatt die additive Farbe auf Schwarz zu setzen).</span><span class="sxs-lookup"><span data-stu-id="6e009-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="6e009-159">Für einfache 2D-Formen, die mit einem Quad mit einer Alphamaske erstellt werden, sollten Sie stattdessen eine Gitternetzdarstellung der Form mit einem nicht transparenten Shader erstellen.</span><span class="sxs-lookup"><span data-stu-id="6e009-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="6e009-160">Beispiele für dunkle Benutzeroberflächen im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="6e009-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="6e009-161">**[MRTK bietet](https://github.com/Microsoft/MixedRealityToolkit-Unity)** viele Beispiele für Benutzeroberflächenbausteinen, die auf den dunklen Farbschemas basieren.</span><span class="sxs-lookup"><span data-stu-id="6e009-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="6e009-162">Menü "Nah"</span><span class="sxs-lookup"><span data-stu-id="6e009-162">Near Menu</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [<span data-ttu-id="6e009-163">Dialogfeld</span><span class="sxs-lookup"><span data-stu-id="6e009-163">Dialog</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [<span data-ttu-id="6e009-164">Handmenü</span><span class="sxs-lookup"><span data-stu-id="6e009-164">Hand Menu</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a><span data-ttu-id="6e009-165">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6e009-165">See also</span></span>

* [<span data-ttu-id="6e009-166">Farbe, Licht und Materialien</span><span class="sxs-lookup"><span data-stu-id="6e009-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="6e009-167">Cursor</span><span class="sxs-lookup"><span data-stu-id="6e009-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6e009-168">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="6e009-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="6e009-169">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="6e009-169">Button</span></span>](button.md)
* [<span data-ttu-id="6e009-170">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="6e009-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6e009-171">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="6e009-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="6e009-172">Manipulation</span><span class="sxs-lookup"><span data-stu-id="6e009-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6e009-173">Handmenü</span><span class="sxs-lookup"><span data-stu-id="6e009-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="6e009-174">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="6e009-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="6e009-175">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="6e009-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="6e009-176">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="6e009-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="6e009-177">Tastatur</span><span class="sxs-lookup"><span data-stu-id="6e009-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="6e009-178">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="6e009-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="6e009-179">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="6e009-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="6e009-180">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="6e009-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="6e009-181">Shader</span><span class="sxs-lookup"><span data-stu-id="6e009-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="6e009-182">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="6e009-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="6e009-183">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="6e009-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="6e009-184">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="6e009-184">Surface magnetism</span></span>](surface-magnetism.md)