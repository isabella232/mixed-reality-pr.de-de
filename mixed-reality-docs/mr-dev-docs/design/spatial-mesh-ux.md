---
title: Visualisierung räumlicher Gitternetze
description: Erfahren Sie mehr über Entwurfsrichtlinien und das Verständnis der physischen Umgebung mit der Visualisierung räumlicher Gitternetze im MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Mixed Reality, HoloLens, UI-Steuerelemente, Interaktion, Ui, UX, UX-Design, räumliche Benutzeroberfläche, räumliche Interaktion, 3D-BENUTZEROBERFLÄCHE, 3D-Benutzeroberfläche, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5bdcba60f38ac67bbf0f394337735f4a2d4ec423
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600629"
---
# <a name="spatial-mesh"></a><span data-ttu-id="c204a-104">Raum-Mesh</span><span class="sxs-lookup"><span data-stu-id="c204a-104">Spatial mesh</span></span>

![Raum-Mesh](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="c204a-106">Benutzer erfahren, wie ein Gerät die physische Umgebung mithilfe der Visualisierung räumlicher Gitternetze wahrnimmt und versteht.</span><span class="sxs-lookup"><span data-stu-id="c204a-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="c204a-107">Die richtige Visualisierung des räumlichen Gitternetzes kann eine ansprechende und magische Erfahrung schaffen und gleichzeitig räumlichen Kontext bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c204a-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="c204a-108">Entwurfsrichtlinie</span><span class="sxs-lookup"><span data-stu-id="c204a-108">Design guideline</span></span>

<span data-ttu-id="c204a-109">Es ist wichtig, dem Benutzer die Möglichkeit zu geben, sich auf Inhalte zu konzentrieren und mit ihnen zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="c204a-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="c204a-110">Die kontinuierliche Visualisierung des räumlichen Gitters im Hintergrund kann ablenkend sein.</span><span class="sxs-lookup"><span data-stu-id="c204a-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="c204a-111">Es wird empfohlen, die Umgebung nur einmal beim ersten Start zu visualisieren, oder wenn der Benutzer deutlich anzeigt, dass er das Umgebungsgitternetz anzeigen möchte, indem er den Bereich anzielt und tippt.</span><span class="sxs-lookup"><span data-stu-id="c204a-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="c204a-112">Sie können dieses Verhalten im Mixed Reality-Portal beobachten.</span><span class="sxs-lookup"><span data-stu-id="c204a-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="c204a-113">Visualisierung räumlicher Gitternetze im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="c204a-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="c204a-114">MRTK stellt mehrere Materialien für die Visualisierung räumlicher Gitternetze bereit.</span><span class="sxs-lookup"><span data-stu-id="c204a-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="c204a-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat:** Standardmäßiges statisches räumliches Gitternetzmaterial, das die Gitternetzgliederungen ohne Animation anzeigt.</span><span class="sxs-lookup"><span data-stu-id="c204a-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="c204a-116">Dieses Material ist für Debugzwecke nützlich, da es die gesamten Geometrien des räumlichen Gitternetzes anzeigt.</span><span class="sxs-lookup"><span data-stu-id="c204a-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="c204a-117">Es wird jedoch nicht für die Produktion empfohlen.</span><span class="sxs-lookup"><span data-stu-id="c204a-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="c204a-118">**MRTK_SurfaceReconstruction.mat:** Dieses Material gibt Ihnen einen animierten Pulse-Effekt auf das räumliche Netz.</span><span class="sxs-lookup"><span data-stu-id="c204a-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="c204a-119">Sie können dieses Material verwenden, um die Umgebung zu einem bestimmten Zeitpunkt oder in der Eingabe des Benutzers zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="c204a-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="c204a-120">Beispiele finden Sie unter **PulseShaderExamples.unity scene (PulseShaderExamples.unity-Szene).**</span><span class="sxs-lookup"><span data-stu-id="c204a-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* <span data-ttu-id="c204a-121">Weitere Informationen finden Sie unter [MRTK – Räumliche Wahrnehmung](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) und [MRTK – Pulse Shader](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).</span><span class="sxs-lookup"><span data-stu-id="c204a-121">For more information, see [MRTK - Spatial Awareness](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) and [MRTK - Pulse Shader](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="c204a-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c204a-122">See also</span></span>

* [<span data-ttu-id="c204a-123">Cursor</span><span class="sxs-lookup"><span data-stu-id="c204a-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c204a-124">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="c204a-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="c204a-125">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="c204a-125">Button</span></span>](button.md)
* [<span data-ttu-id="c204a-126">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="c204a-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c204a-127">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="c204a-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c204a-128">Manipulation</span><span class="sxs-lookup"><span data-stu-id="c204a-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c204a-129">Handmenü</span><span class="sxs-lookup"><span data-stu-id="c204a-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="c204a-130">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="c204a-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="c204a-131">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="c204a-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="c204a-132">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="c204a-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="c204a-133">Tastatur</span><span class="sxs-lookup"><span data-stu-id="c204a-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="c204a-134">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="c204a-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="c204a-135">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="c204a-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="c204a-136">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="c204a-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="c204a-137">Shader</span><span class="sxs-lookup"><span data-stu-id="c204a-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="c204a-138">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="c204a-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c204a-139">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="c204a-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="c204a-140">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="c204a-140">Surface magnetism</span></span>](surface-magnetism.md)