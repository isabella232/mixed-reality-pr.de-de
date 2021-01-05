---
title: Visualisierung räumlicher Netze
description: Erfahren Sie, wie Geräte physische Umgebungen mithilfe räumlicher Netze verstehen.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Gemischte Realität, hololens, UI-Steuerelemente, Interaktion, UI, UX, UX-Entwurf, räumliche Benutzeroberfläche, räumliche Interaktion, 3D-Benutzeroberfläche, 3D-UX, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: ffa13da6762b803ba2a3f370308ac2af65164ecf
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848188"
---
# <a name="spatial-mesh"></a><span data-ttu-id="73e98-104">Raum-Mesh</span><span class="sxs-lookup"><span data-stu-id="73e98-104">Spatial mesh</span></span>

![Raum-Mesh](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="73e98-106">Benutzer erfahren, wie ein Gerät die physische Umgebung durch eine räumliche Mesh-Visualisierung wahrnimmt und versteht.</span><span class="sxs-lookup"><span data-stu-id="73e98-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="73e98-107">Die richtige räumliche Gitter Visualisierung kann bei der Bereitstellung räumlichen Kontexts eine reizvolle und magische Darstellung schaffen.</span><span class="sxs-lookup"><span data-stu-id="73e98-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="73e98-108">Entwurfsrichtlinie</span><span class="sxs-lookup"><span data-stu-id="73e98-108">Design guideline</span></span>

<span data-ttu-id="73e98-109">Es ist wichtig, dass der Benutzer den Fokus auf Inhalte hat und mit ihm interagiert.</span><span class="sxs-lookup"><span data-stu-id="73e98-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="73e98-110">Die fortlaufende Visualisierung des räumlichen Netzes im Hintergrund kann ablenkend sein.</span><span class="sxs-lookup"><span data-stu-id="73e98-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="73e98-111">Es wird empfohlen, die Umgebung sparsam zu visualisieren, entweder nur einmal beim ersten Start oder wenn der Benutzer deutlich anzeigt, dass er das Umgebungs Netz durch Ziel und Luft tippen anzeigen soll.</span><span class="sxs-lookup"><span data-stu-id="73e98-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="73e98-112">Dieses Verhalten können Sie im Mixed Reality-Portal beobachten.</span><span class="sxs-lookup"><span data-stu-id="73e98-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="73e98-113">Visualisierung räumlicher Netze in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="73e98-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="73e98-114">Mrtk bietet mehrere Materialien für die Visualisierung räumlicher Netze.</span><span class="sxs-lookup"><span data-stu-id="73e98-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="73e98-115">**MRTK_Wireframe. Matt, MRTK_Wireframe. Matt**: statisches Standard Mesh-Material, das die Gitter Kontur ohne Animation anzeigt.</span><span class="sxs-lookup"><span data-stu-id="73e98-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="73e98-116">Dieses Material ist für Debuggingzwecke nützlich, da es die gesamten räumlichen Gitter Geometrien anzeigt.</span><span class="sxs-lookup"><span data-stu-id="73e98-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="73e98-117">Dies wird jedoch nicht für die Produktion empfohlen.</span><span class="sxs-lookup"><span data-stu-id="73e98-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="73e98-118">**MRTK_SurfaceReconstruction. Matt**: dieses Material bietet einen animierten Pulse-Effekt auf das räumliche Mesh.</span><span class="sxs-lookup"><span data-stu-id="73e98-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="73e98-119">Sie können dieses Material verwenden, um die Umgebung zu einem bestimmten Zeitpunkt oder in der Eingabe des Benutzers in der Luft Eingabe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="73e98-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="73e98-120">Beispiele hierfür finden Sie in der **pulseshaderexamples. unity** -Szene.</span><span class="sxs-lookup"><span data-stu-id="73e98-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="73e98-121">Weitere Informationen finden Sie unter [mrtk-Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) und [mrtk-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span><span class="sxs-lookup"><span data-stu-id="73e98-121">For more information, see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="73e98-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="73e98-122">See also</span></span>

* [<span data-ttu-id="73e98-123">Cursor</span><span class="sxs-lookup"><span data-stu-id="73e98-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="73e98-124">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="73e98-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="73e98-125">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="73e98-125">Button</span></span>](button.md)
* [<span data-ttu-id="73e98-126">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="73e98-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="73e98-127">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="73e98-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="73e98-128">Manipulation</span><span class="sxs-lookup"><span data-stu-id="73e98-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="73e98-129">Handmenü</span><span class="sxs-lookup"><span data-stu-id="73e98-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="73e98-130">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="73e98-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="73e98-131">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="73e98-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="73e98-132">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="73e98-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="73e98-133">Tastatur</span><span class="sxs-lookup"><span data-stu-id="73e98-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="73e98-134">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="73e98-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="73e98-135">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="73e98-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="73e98-136">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="73e98-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="73e98-137">Shader</span><span class="sxs-lookup"><span data-stu-id="73e98-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="73e98-138">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="73e98-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="73e98-139">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="73e98-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="73e98-140">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="73e98-140">Surface magnetism</span></span>](surface-magnetism.md)
