---
title: Entwurfsanleitung für 3D-App-Startprogramm
description: Ein 3D-App-Startfeld ist ein "physisches" Objekt im gemischten Reality-Haus des Benutzers, das Sie auswählen können, um eine APP zu starten.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, 3D-App-Start Programm, immersives Headset, Live Cube, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP, Win32, Beleuchtung, Farbe
ms.openlocfilehash: 2edb09e47da5bcbae34a37f004853002f3f65cf3
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757728"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="b8b94-104">Entwurfsanleitung für 3D-App-Startprogramm</span><span class="sxs-lookup"><span data-stu-id="b8b94-104">3D app launcher design guidance</span></span>

<span data-ttu-id="b8b94-105">Wenn Sie ein Windows Mixed Reality immersive-Headset (VR) einfügen, geben Sie das Windows Mixed Reality Home ein.</span><span class="sxs-lookup"><span data-stu-id="b8b94-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home.</span></span> <span data-ttu-id="b8b94-106">Die Startseite wird als Haus auf einer Klippe dargestellt, die von den Bergen und Wasser umgeben ist, aber Sie können [auch andere Umgebungen auswählen und sogar eigene Umgebungen erstellen](../design/add-custom-home-environments.md).</span><span class="sxs-lookup"><span data-stu-id="b8b94-106">The home is visualized as a house on a cliff surrounded by mountains and water, but you can [choose other environments and even create your own](../design/add-custom-home-environments.md)).</span></span> <span data-ttu-id="b8b94-107">Innerhalb des Speicherplatzes kann ein Benutzer die 3D-Objekte und-apps, für die Sie sich interessieren, anordnen und organisieren.</span><span class="sxs-lookup"><span data-stu-id="b8b94-107">Within the home's space, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="b8b94-108">Ein **3D-App-** Startfeld ist ein "physisches" Objekt im gemischten Reality-Haus des Benutzers, das Sie auswählen können, um eine APP zu starten.</span><span class="sxs-lookup"><span data-stu-id="b8b94-108">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="b8b94-109">![Beispiel: floaty Bird 3D-App-Startfeld](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8b94-109">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="b8b94-110">*Beispiel für floaty Bird 3D-App-Startfeld (fiktive APP)*</span><span class="sxs-lookup"><span data-stu-id="b8b94-110">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="b8b94-111">Erstellung eines 3D-App-Start Programms</span><span class="sxs-lookup"><span data-stu-id="b8b94-111">3D app launcher creation process</span></span>

<span data-ttu-id="b8b94-112">Zum Erstellen eines 3D-App-Start Programms sind drei Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="b8b94-112">There are 3 steps to creating a 3D app launcher:</span></span>

1. <span data-ttu-id="b8b94-113">Entwerfen und entwerfen (dieser Artikel)</span><span class="sxs-lookup"><span data-stu-id="b8b94-113">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="b8b94-114">Modellieren und exportieren</span><span class="sxs-lookup"><span data-stu-id="b8b94-114">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="b8b94-115">Integration in Ihre Anwendung:</span><span class="sxs-lookup"><span data-stu-id="b8b94-115">Integrating it into your application:</span></span>
    * [<span data-ttu-id="b8b94-116">UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="b8b94-116">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="b8b94-117">Win32-Apps</span><span class="sxs-lookup"><span data-stu-id="b8b94-117">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="b8b94-118">Entwurfskonzepte</span><span class="sxs-lookup"><span data-stu-id="b8b94-118">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="b8b94-119">Fantastisch, aber schon vertraut</span><span class="sxs-lookup"><span data-stu-id="b8b94-119">Fantastic yet familiar</span></span>

<span data-ttu-id="b8b94-120">Die Windows Mixed Reality-Umgebung, in der sich Ihr App-Startfeld befindet, ist Teil vertraut, Teil fantastisch/Sci-Fi.</span><span class="sxs-lookup"><span data-stu-id="b8b94-120">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="b8b94-121">Die besten Launcher befolgen die Regeln dieser Welt.</span><span class="sxs-lookup"><span data-stu-id="b8b94-121">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="b8b94-122">Stellen Sie sich vor, wie Sie ein vertrautes, repräsentatives Objekt von Ihrer APP aus erstellen, aber einige der Regeln der tatsächlichen Realität übernehmen können.</span><span class="sxs-lookup"><span data-stu-id="b8b94-122">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="b8b94-123">Magic führt dazu.</span><span class="sxs-lookup"><span data-stu-id="b8b94-123">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="b8b94-124">Intuitiven</span><span class="sxs-lookup"><span data-stu-id="b8b94-124">Intuitive</span></span>

<span data-ttu-id="b8b94-125">Wenn Sie sich Ihr App-Startfeld ansehen, sollte der Zweck zum Starten Ihrer APP offensichtlich sein und keine Verwirrung verursachen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-125">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="b8b94-126">Stellen Sie sich z. b. vor, dass Ihr Start Programm ein offensichtlich-genug repräsentativ für Ihre APP ist, dass Sie nicht mit einem Teil der Einrichtung im Klippe-Haus verwechselt wird.</span><span class="sxs-lookup"><span data-stu-id="b8b94-126">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="b8b94-127">Ihr App-Start Programm sollte Personen einladen, Sie zu berühren bzw. auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-127">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="b8b94-128">![Beispiel: neues Hinweis 3D-App-Startfeld](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8b94-128">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="b8b94-129">*Neues Hinweis Beispiel für 3D-App-Start Programm (fiktive APP)*</span><span class="sxs-lookup"><span data-stu-id="b8b94-129">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="b8b94-130">Start Skala</span><span class="sxs-lookup"><span data-stu-id="b8b94-130">Home scale</span></span>

<span data-ttu-id="b8b94-131">3D-App-Launcher Leben im Klippe-Haus, und ihre Standardgröße sollte mit den anderen "physischen" Objekten im Raum Sinn machen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-131">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="b8b94-132">Wenn Sie das Start Programm anordnen, beispielsweise eine Hausanlage oder einige Möbel, sollte es sich in der eigenen Größe fühlen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-132">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="b8b94-133">Ein guter Ausgangspunkt ist, zu sehen, wie es 30 Kubikzentimeter aussieht, aber denken Sie daran, dass Benutzer es bei Bedarf zentral hoch-oder Herunterskalieren können.</span><span class="sxs-lookup"><span data-stu-id="b8b94-133">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="b8b94-134">Eigen fähig</span><span class="sxs-lookup"><span data-stu-id="b8b94-134">Own-able</span></span>

<span data-ttu-id="b8b94-135">Das App-Start Programm sollte sich wie ein Objekt erweisen, das eine Person im Raum haben würde.</span><span class="sxs-lookup"><span data-stu-id="b8b94-135">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="b8b94-136">Sie werden sich praktisch durch diese Dinge umgeben, sodass das Start Programm so aussehen sollte, wie etwas, was der Benutzer als wünschenswert erachtet hat</span><span class="sxs-lookup"><span data-stu-id="b8b94-136">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="b8b94-137">![Beispiel: Astro Warp 3D-App-Startfeld](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8b94-137">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="b8b94-138">*Beispiel für ein Beispiel für die Astro Warp 3D-app (fiktive APP)*</span><span class="sxs-lookup"><span data-stu-id="b8b94-138">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="b8b94-139">Unerkannt</span><span class="sxs-lookup"><span data-stu-id="b8b94-139">Recognizable</span></span>

<span data-ttu-id="b8b94-140">Ihr 3D-App-Startfeld sollte den Benutzern, die Sie sehen, umgehend die "Marke Ihrer APP" ausdrücken.</span><span class="sxs-lookup"><span data-stu-id="b8b94-140">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="b8b94-141">Wenn Sie in Ihrer APP über ein Sternzeichen oder ein besonders identifizierbares Objekt verfügen, empfiehlt es sich, dieses als wesentlichen Bestandteil des Entwurfs zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b8b94-141">If you have a star character or an especially identifiable object in your app, we recommend using that as a significant part of your design.</span></span> <span data-ttu-id="b8b94-142">In einer Mixed Reality-Welt zeichnet ein Objekt von Benutzern mehr Interesse als nur ein Logo allein.</span><span class="sxs-lookup"><span data-stu-id="b8b94-142">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="b8b94-143">Erkennbare Objekte kommunizieren schnell und eindeutig.</span><span class="sxs-lookup"><span data-stu-id="b8b94-143">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="b8b94-144">Volumetrische</span><span class="sxs-lookup"><span data-stu-id="b8b94-144">Volumetric</span></span>

<span data-ttu-id="b8b94-145">Ihre APP verdient mehr als nur Ihr Logo auf eine flache Ebene zu bringen und Sie täglich Aufrufs.</span><span class="sxs-lookup"><span data-stu-id="b8b94-145">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="b8b94-146">Das Start Programm sollte sich wie ein spannendes, 3D-Objekt im Bereich des Benutzers fühlen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-146">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="b8b94-147">Eine gute Vorgehensweise besteht darin, sich zu vorstellen, dass Ihre APP in der Tages Parade der Macy-Tage eine Sprechblase enthalten würde.</span><span class="sxs-lookup"><span data-stu-id="b8b94-147">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="b8b94-148">Fragen Sie sich, was wirklich Menschen ist, die sich in der Straße befinden?</span><span class="sxs-lookup"><span data-stu-id="b8b94-148">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="b8b94-149">Was ist für alle Anzeige Winkel großartig?</span><span class="sxs-lookup"><span data-stu-id="b8b94-149">What would look great from all viewing angles?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b8b94-150">![Nur Logo nur ](images/20171016-140436-mixedreality-640px.jpg) *Logo*</span><span class="sxs-lookup"><span data-stu-id="b8b94-150">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b8b94-151">![Besser erkennbar durch ein Zeichen, das ](images/20171016-140557-mixedreality-640px.jpg) *mit einem Zeichen besser erkennbar* ist</span><span class="sxs-lookup"><span data-stu-id="b8b94-151">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="b8b94-152">![Flacher Ansatz, nicht überraschend, ist ein flacher ](images/20171016-155101-mixedreality-640px.jpg) *Ansatz, nicht überraschend, ist flach*</span><span class="sxs-lookup"><span data-stu-id="b8b94-152">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b8b94-153">![Volumetric-Ansatz zeigt Ihren app- ](images/20171016-161407-mixedreality-640px.jpg) *volumetriansatz besser an und zeigt Ihre APP besser* an</span><span class="sxs-lookup"><span data-stu-id="b8b94-153">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a><span data-ttu-id="b8b94-154">Tipps für gute 3D-Modelle</span><span class="sxs-lookup"><span data-stu-id="b8b94-154">Tips for good 3D models</span></span>

* <span data-ttu-id="b8b94-155">Wenn Sie Dimensionen für das App-Start Programm planen, sollten Sie ungefähr einen 30 cm-Cube durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-155">When planning dimensions for your app launcher, shoot for roughly a 30-cm cube.</span></span> <span data-ttu-id="b8b94-156">Also ein Größenverhältnis von 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="b8b94-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="b8b94-157">Modelle müssen unter 10.000 Polygone liegen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="b8b94-158">Weitere Informationen zu Dreiecks Zählungen und Ebenen der Details (LODs)</span><span class="sxs-lookup"><span data-stu-id="b8b94-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="b8b94-159">Testen Sie auf einem immersiven Headset.</span><span class="sxs-lookup"><span data-stu-id="b8b94-159">Test on an immersive headset.</span></span>
* <span data-ttu-id="b8b94-160">Builddetails in der Geometrie des Modells, soweit möglich – verlassen Sie sich nicht auf Texturen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="b8b94-161">Erstellen einer "wasserdichten" geschlossenen Geometrie.</span><span class="sxs-lookup"><span data-stu-id="b8b94-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="b8b94-162">Keine Lücken, die nicht in modelliert werden.</span><span class="sxs-lookup"><span data-stu-id="b8b94-162">No holes that aren't modeled in.</span></span>
* <span data-ttu-id="b8b94-163">Verwenden Sie natürliche Materialien in Ihrem Objekt.</span><span class="sxs-lookup"><span data-stu-id="b8b94-163">Use natural materials in your object.</span></span> <span data-ttu-id="b8b94-164">Stellen Sie sich vor, Sie erstellen Sie in der Praxis.</span><span class="sxs-lookup"><span data-stu-id="b8b94-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="b8b94-165">Stellen Sie sicher, dass Ihr Modell in unterschiedlichen Entfernungen und Größen gut funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b8b94-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="b8b94-166">Wenn Ihr Modell einsatzbereit ist, lesen Sie die [Richtlinien zum Exportieren von Assets](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="b8b94-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="b8b94-167">![Modell mit geringfügigen Details in der Textur](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8b94-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="b8b94-168">*Modell mit geringfügigen Details in der Textur*</span><span class="sxs-lookup"><span data-stu-id="b8b94-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="b8b94-169">Was Sie vermeiden sollten</span><span class="sxs-lookup"><span data-stu-id="b8b94-169">What to avoid</span></span>

* <span data-ttu-id="b8b94-170">Verwenden Sie keine kontrastreichen Details oder kleine, ausgelastete Muster und Texturen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="b8b94-171">Verwenden Sie Thin Geometry nicht – es funktioniert nicht gut in einer Entfernung und ist falsch.</span><span class="sxs-lookup"><span data-stu-id="b8b94-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="b8b94-172">Lassen Sie Teile des Modells nicht zu viel über das Größenverhältnis von 1:1:1 hinaus erweitern.</span><span class="sxs-lookup"><span data-stu-id="b8b94-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="b8b94-173">Es werden Skalierungsprobleme entstehen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-173">It will create scaling problems.</span></span>

<span data-ttu-id="b8b94-174">![Vermeiden Sie Muster mit hohem Kontrast und geringer Auslastung](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8b94-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="b8b94-175">*Vermeiden Sie große Kontraste, kleine, ausgelastete Muster*</span><span class="sxs-lookup"><span data-stu-id="b8b94-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="b8b94-176">Vorgehensweise beim Behandeln von Typen</span><span class="sxs-lookup"><span data-stu-id="b8b94-176">How to handle type</span></span>

* <span data-ttu-id="b8b94-177">Es wird empfohlen, dass Ihr Typ ungefähr 1/3 ihres App-Start Programms (oder mehr) annimmt.</span><span class="sxs-lookup"><span data-stu-id="b8b94-177">We recommend your type takes up about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="b8b94-178">Der Typ ist das wichtigste, das den Benutzern eine Vorstellung gibt, dass es sich bei Ihrem Start Programm tatsächlich um ein Start Programm handelt, sodass es sehr schön ist.</span><span class="sxs-lookup"><span data-stu-id="b8b94-178">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s substantial.</span></span>
* <span data-ttu-id="b8b94-179">Vermeiden Sie einen Super weiten Typ – versuchen Sie, ihn innerhalb der Grenzen der Kerndimensionen der App-Launcher (mehr oder weniger) zu halten.</span><span class="sxs-lookup"><span data-stu-id="b8b94-179">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="b8b94-180">Der flattype kann funktionieren, kann jedoch in bestimmten Winkeln und in bestimmten Umgebungen schwierig angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b8b94-180">Flat type can work, but it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="b8b94-181">Möglicherweise sollten Sie ein solides Objekt oder einen Hintergrund dahinter ablegen, um dies zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-181">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="b8b94-182">Das Hinzufügen von Dimensionen zu Ihrem Typ ist in 3D gut.</span><span class="sxs-lookup"><span data-stu-id="b8b94-182">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="b8b94-183">Das Schattieren der Seiten des Typs unterscheidet sich durch die Lesbarkeit.</span><span class="sxs-lookup"><span data-stu-id="b8b94-183">Shading the sides of the type a different, darker color can help with readability.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b8b94-184">![Ein flacher Typ ohne einen Hintergrund kann in bestimmten Winkeln nicht angezeigt werden, und in bestimmten Umgebungen ](images/flattype-640px.png) *kann der flache Typ ohne einen Hintergrund in bestimmten Winkeln und in bestimmten Umgebungen schwierig angezeigt werden* .</span><span class="sxs-lookup"><span data-stu-id="b8b94-184">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b8b94-185">![Der Typ mit einem integrierten Hintergrund kann gut funktionieren, wenn ](images/flattypeandbkg-640px.png) *ein integrierter Hintergrund* funktionsfähig ist.</span><span class="sxs-lookup"><span data-stu-id="b8b94-185">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b8b94-186">![Der Typ "extrudiert" kann gut funktionieren, wenn Sie die Seiten mit dem ](images/20171016-160221-mixedreality-640px.jpg) *Typ "extrudiert" gut funktionieren, wenn Sie die Seiten schattieren*</span><span class="sxs-lookup"><span data-stu-id="b8b94-186">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="b8b94-187">**Typfarben, die funktionieren**</span><span class="sxs-lookup"><span data-stu-id="b8b94-187">**Type colors that work**</span></span>

* <span data-ttu-id="b8b94-188">White</span><span class="sxs-lookup"><span data-stu-id="b8b94-188">White</span></span>
* <span data-ttu-id="b8b94-189">Schwarz</span><span class="sxs-lookup"><span data-stu-id="b8b94-189">Black</span></span>
* <span data-ttu-id="b8b94-190">Helle halb satte Farbe</span><span class="sxs-lookup"><span data-stu-id="b8b94-190">Bright semi-saturated color</span></span>

<span data-ttu-id="b8b94-191">![Typfarben, die funktionieren.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8b94-191">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="b8b94-192">*Typfarben, die funktionieren*</span><span class="sxs-lookup"><span data-stu-id="b8b94-192">*Type colors that work*</span></span>

### <a name="colors-to-avoid"></a><span data-ttu-id="b8b94-193">Zu vermeide Farben</span><span class="sxs-lookup"><span data-stu-id="b8b94-193">Colors to avoid</span></span>

<span data-ttu-id="b8b94-194">Typfarben, die Probleme verursachen, sind:</span><span class="sxs-lookup"><span data-stu-id="b8b94-194">Type colors that cause trouble include:</span></span>

* <span data-ttu-id="b8b94-195">Mitteltöne</span><span class="sxs-lookup"><span data-stu-id="b8b94-195">Mid-tones</span></span>
* <span data-ttu-id="b8b94-196">Grau</span><span class="sxs-lookup"><span data-stu-id="b8b94-196">Gray</span></span>
* <span data-ttu-id="b8b94-197">Über satte Farben oder nicht satte Farben</span><span class="sxs-lookup"><span data-stu-id="b8b94-197">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="b8b94-198">![Typfarben, die Probleme verursachen.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8b94-198">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="b8b94-199">*Typfarben, die Probleme verursachen*</span><span class="sxs-lookup"><span data-stu-id="b8b94-199">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="b8b94-200">Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="b8b94-200">Lighting</span></span>

<span data-ttu-id="b8b94-201">Die Beleuchtung für das App-Start Programm stammt aus der Umgebung "Klippe House".</span><span class="sxs-lookup"><span data-stu-id="b8b94-201">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="b8b94-202">Stellen Sie sicher, dass Sie das Start Programm an mehreren Stellen im ganzen Haus testen, damit es in Licht und Schatten gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="b8b94-202">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="b8b94-203">Die gute Nachricht ist, dass Sie, wenn Sie den anderen Entwurfs Leit Faden in diesem Dokument befolgt haben, das Start Programm für die meisten Beleuchtung im Klippe-Haus in guter Form aufweisen sollte.</span><span class="sxs-lookup"><span data-stu-id="b8b94-203">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="b8b94-204">Ein guter Ausgangspunkt, um zu testen, wie das Start Programm in den verschiedenen Lichtern in der Umgebung aussieht, sind Studio, der Medienraum, an einer beliebigen Stelle außerhalb und auf der Rückseite (der konkrete Bereich mit dem Rasen).</span><span class="sxs-lookup"><span data-stu-id="b8b94-204">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="b8b94-205">Ein weiterer guter Test besteht darin, den halblicht-und Halbschatten zu platzieren und zu sehen, wie er aussieht.</span><span class="sxs-lookup"><span data-stu-id="b8b94-205">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="b8b94-206">![Stellen Sie sicher, dass das Start Programm sowohl in Beleuchtung als auch in Schatten angezeigt wird.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8b94-206">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="b8b94-207">*Stellen Sie sicher, dass das Start Programm in Licht und Schatten gut aussieht*</span><span class="sxs-lookup"><span data-stu-id="b8b94-207">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="b8b94-208">Texturierung</span><span class="sxs-lookup"><span data-stu-id="b8b94-208">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="b8b94-209">Erstellen von Texturen</span><span class="sxs-lookup"><span data-stu-id="b8b94-209">Authoring your textures</span></span>

<span data-ttu-id="b8b94-210">Das Endformat des 3D-App-Start Programms ist eine. GLB-Datei, die mithilfe der PBR-Pipeline (physisch basiertes Rendering) erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="b8b94-210">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="b8b94-211">Dies kann ein kniffliger Prozess sein. jetzt ist es ein guter Zeitpunkt, einen technischen Künstler zu verwenden, wenn Sie dies noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="b8b94-211">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="b8b94-212">Wenn Sie ein mutiger DIY sind und sich die Zeit nehmen, sich mit der [PBR-Terminologie](https://wiki.polycount.com/wiki/PBR) vertraut zu machen und zu erfahren, was im Hintergrund passiert, bevor Sie beginnen, können Sie häufige Fehler vermeiden.</span><span class="sxs-lookup"><span data-stu-id="b8b94-212">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="b8b94-213">![Beispiel: neue Notiz-App](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="b8b94-213">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="b8b94-214">*Neues Hinweis Beispiel für 3D-App-Start Programm (fiktive APP)*</span><span class="sxs-lookup"><span data-stu-id="b8b94-214">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="recommended-authoring-tool"></a><span data-ttu-id="b8b94-215">Empfohlenes Authoring Tool</span><span class="sxs-lookup"><span data-stu-id="b8b94-215">Recommended authoring tool</span></span>

<span data-ttu-id="b8b94-216">Es wird empfohlen, den [Substanz Maler](https://www.allegorithmic.com/products/substance-painter) von allethmic zu verwenden, um Ihre endgültige Datei zu verfassen.</span><span class="sxs-lookup"><span data-stu-id="b8b94-216">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="b8b94-217">Wenn Sie nicht mit der Erstellung von PBR-Shadern in der Inhalts Malerin vertraut sind, finden Sie hier ein [Tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="b8b94-217">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="b8b94-218">(Alternativ kann [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/)oder [marthset](https://www.marmoset.co/toolbag/) auch verwendet werden, wenn Sie mit einer der beiden vertraut sind.)</span><span class="sxs-lookup"><span data-stu-id="b8b94-218">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="b8b94-219">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="b8b94-219">Best practices</span></span>

* <span data-ttu-id="b8b94-220">Wenn das App-Start Programmobjekt für PBR erstellt wurde, sollte es einfach sein, es für die Umgebung "Felsen Umgebung" zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="b8b94-220">If your app launcher object was authored for PBR, it should be straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="b8b94-221">Unser Shader erwartet einen Metal/roughness-Workflow – der Unreal PBR-Shader ist ein schließende Fax.</span><span class="sxs-lookup"><span data-stu-id="b8b94-221">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="b8b94-222">Beachten Sie beim Exportieren der Texturen die [empfohlenen Textur Größen](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) .</span><span class="sxs-lookup"><span data-stu-id="b8b94-222">When exporting your textures, keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="b8b94-223">Stellen Sie sicher, dass Sie die Objekte für die Echtzeitbeleuchtung erstellen – Dies bedeutet Folgendes:</span><span class="sxs-lookup"><span data-stu-id="b8b94-223">Make sure to build your objects for real-time lighting—this means:</span></span>
  * <span data-ttu-id="b8b94-224">Vermeiden gebackener Schatten – oder gezeichnete Schatten</span><span class="sxs-lookup"><span data-stu-id="b8b94-224">Avoid baked shadows – or painted shadows</span></span>
  * <span data-ttu-id="b8b94-225">Vermeiden Sie eine gebackenes Beleuchtung in den Texturen</span><span class="sxs-lookup"><span data-stu-id="b8b94-225">Avoid baked lighting in the textures</span></span>
  * <span data-ttu-id="b8b94-226">Verwenden Sie eines der Pakete zur Erstellung von PBR-Materialien, um die richtigen Zuordnungen für den Shader zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b8b94-226">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="b8b94-227">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b8b94-227">See also</span></span>

* [<span data-ttu-id="b8b94-228">Erstellen von 3D-Modellen für die Verwendung in der Mixed Reality-Startseite</span><span class="sxs-lookup"><span data-stu-id="b8b94-228">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="b8b94-229">Implementieren von 3D-App-Startprogrammen (UWP-Apps)</span><span class="sxs-lookup"><span data-stu-id="b8b94-229">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="b8b94-230">Implementieren von 3D-App-Startprogrammen (Win32-Apps)</span><span class="sxs-lookup"><span data-stu-id="b8b94-230">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
