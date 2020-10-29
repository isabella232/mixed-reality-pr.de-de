---
title: Visualisierung räumlicher Netze
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Gemischte Realität, hololens, UI-Steuerelemente, Interaktion, UI, UX, UX-Entwurf, räumliche Benutzeroberfläche, räumliche Interaktion, 3D-Benutzeroberfläche, 3D-UX
ms.openlocfilehash: 2c811edc14fbcc7c917fe9fa724f1cab23179a96
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686091"
---
# <a name="spatial-mesh"></a><span data-ttu-id="09095-103">Raum-Mesh</span><span class="sxs-lookup"><span data-stu-id="09095-103">Spatial mesh</span></span>

![Raum-Mesh](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="09095-105">Durch die Visualisierung räumlicher Netze kann der Benutzer erfahren, wie ein Gerät die physische Umgebung erkennt und versteht.</span><span class="sxs-lookup"><span data-stu-id="09095-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="09095-106">Zusätzlich zur Bereitstellung von räumlichem Kontext kann die richtige räumliche Gitter Visualisierung eine reizvolle und magische Darstellung schaffen.</span><span class="sxs-lookup"><span data-stu-id="09095-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="09095-107">Entwurfsrichtlinie</span><span class="sxs-lookup"><span data-stu-id="09095-107">Design guideline</span></span>
<span data-ttu-id="09095-108">Da es wichtig ist, dass der Benutzer auf Inhalte fokussiert und mit ihm interagiert, kann das fortlaufende und wiederholte visualisieren des räumlichen Netzes im Hintergrund ablenkend sein.</span><span class="sxs-lookup"><span data-stu-id="09095-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="09095-109">Es wird empfohlen, die Umgebung sparsam zu visualisieren. Dies geschieht entweder nur einmal beim ersten Start oder wenn der Benutzer klar ist, dass das Umgebungs Netz durch Ziel-und Luftbild Speicher angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="09095-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="09095-110">Dieses Verhalten kann in der hololens-Shell beobachtet werden.</span><span class="sxs-lookup"><span data-stu-id="09095-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="09095-111">Visualisierung räumlicher Netze in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="09095-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="09095-112">Mrtk bietet mehrere Materialien für die Visualisierung räumlicher Netze.</span><span class="sxs-lookup"><span data-stu-id="09095-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="09095-113">**MRTK_Wireframe. Matt, MRTK_Wireframe. Matt** : statisches Standard Mesh-Material, das die Gitter Kontur ohne Animation anzeigt.</span><span class="sxs-lookup"><span data-stu-id="09095-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat** : Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="09095-114">Dieses Material ist für Debuggingzwecke nützlich, da es die gesamten räumlichen Gitter Geometrien anzeigt.</span><span class="sxs-lookup"><span data-stu-id="09095-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="09095-115">Dies wird jedoch nicht für die Produktion empfohlen.</span><span class="sxs-lookup"><span data-stu-id="09095-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="09095-116">**MRTK_SurfaceReconstruction. Matt** : dieses Material bietet einen animierten Pulse-Effekt auf das räumliche Mesh.</span><span class="sxs-lookup"><span data-stu-id="09095-116">**MRTK_SurfaceReconstruction.mat** : This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="09095-117">Sie können dieses Material verwenden, um die Umgebung zu einem bestimmten Zeitpunkt ihrer Umgebung oder in der Eingabe des Benutzers zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="09095-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="09095-118">Beispiele hierfür finden Sie in der **pulseshaderexamples. unity** -Szene.</span><span class="sxs-lookup"><span data-stu-id="09095-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="09095-119">Weitere Informationen finden Sie unter [mrtk-Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) und [mrtk-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) .</span><span class="sxs-lookup"><span data-stu-id="09095-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="09095-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="09095-120">See also</span></span>

* [<span data-ttu-id="09095-121">Cursor</span><span class="sxs-lookup"><span data-stu-id="09095-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="09095-122">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="09095-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="09095-123">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="09095-123">Button</span></span>](button.md)
* [<span data-ttu-id="09095-124">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="09095-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="09095-125">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="09095-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="09095-126">Manipulation</span><span class="sxs-lookup"><span data-stu-id="09095-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="09095-127">Handmenü</span><span class="sxs-lookup"><span data-stu-id="09095-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="09095-128">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="09095-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="09095-129">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="09095-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="09095-130">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="09095-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="09095-131">Tastatur</span><span class="sxs-lookup"><span data-stu-id="09095-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="09095-132">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="09095-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="09095-133">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="09095-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="09095-134">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="09095-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="09095-135">Shader</span><span class="sxs-lookup"><span data-stu-id="09095-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="09095-136">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="09095-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="09095-137">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="09095-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="09095-138">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="09095-138">Surface magnetism</span></span>](surface-magnetism.md)
