---
title: Visualisierung räumlicher Netze
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Gemischte Realität, hololens, UI-Steuerelemente, Interaktion, UI, UX, UX-Entwurf, räumliche Benutzeroberfläche, räumliche Interaktion, 3D-Benutzeroberfläche, 3D-UX, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: ec887f73b8561e0a91740d612227411683707364
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703296"
---
# <a name="spatial-mesh"></a><span data-ttu-id="430b9-103">Raum-Mesh</span><span class="sxs-lookup"><span data-stu-id="430b9-103">Spatial mesh</span></span>

![Raum-Mesh](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="430b9-105">Durch die Visualisierung räumlicher Netze kann der Benutzer erfahren, wie ein Gerät die physische Umgebung erkennt und versteht.</span><span class="sxs-lookup"><span data-stu-id="430b9-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="430b9-106">Zusätzlich zur Bereitstellung von räumlichem Kontext kann die richtige räumliche Gitter Visualisierung eine reizvolle und magische Darstellung schaffen.</span><span class="sxs-lookup"><span data-stu-id="430b9-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="430b9-107">Entwurfsrichtlinie</span><span class="sxs-lookup"><span data-stu-id="430b9-107">Design guideline</span></span>
<span data-ttu-id="430b9-108">Da es wichtig ist, dass der Benutzer auf Inhalte fokussiert und mit ihm interagiert, kann das fortlaufende und wiederholte visualisieren des räumlichen Netzes im Hintergrund ablenkend sein.</span><span class="sxs-lookup"><span data-stu-id="430b9-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="430b9-109">Es wird empfohlen, die Umgebung sparsam zu visualisieren. Dies geschieht entweder nur einmal beim ersten Start oder wenn der Benutzer klar ist, dass das Umgebungs Netz durch Ziel-und Luftbild Speicher angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="430b9-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="430b9-110">Dieses Verhalten kann in der hololens-Shell beobachtet werden.</span><span class="sxs-lookup"><span data-stu-id="430b9-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="430b9-111">Visualisierung räumlicher Netze in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="430b9-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="430b9-112">Mrtk bietet mehrere Materialien für die Visualisierung räumlicher Netze.</span><span class="sxs-lookup"><span data-stu-id="430b9-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="430b9-113">**MRTK_Wireframe. Matt, MRTK_Wireframe. Matt**: statisches Standard Mesh-Material, das die Gitter Kontur ohne Animation anzeigt.</span><span class="sxs-lookup"><span data-stu-id="430b9-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="430b9-114">Dieses Material ist für Debuggingzwecke nützlich, da es die gesamten räumlichen Gitter Geometrien anzeigt.</span><span class="sxs-lookup"><span data-stu-id="430b9-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="430b9-115">Dies wird jedoch nicht für die Produktion empfohlen.</span><span class="sxs-lookup"><span data-stu-id="430b9-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="430b9-116">**MRTK_SurfaceReconstruction. Matt**: dieses Material bietet einen animierten Pulse-Effekt auf das räumliche Mesh.</span><span class="sxs-lookup"><span data-stu-id="430b9-116">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="430b9-117">Sie können dieses Material verwenden, um die Umgebung zu einem bestimmten Zeitpunkt ihrer Umgebung oder in der Eingabe des Benutzers zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="430b9-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="430b9-118">Beispiele hierfür finden Sie in der **pulseshaderexamples. unity** -Szene.</span><span class="sxs-lookup"><span data-stu-id="430b9-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="430b9-119">Weitere Informationen finden Sie unter [mrtk-Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) und [mrtk-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) .</span><span class="sxs-lookup"><span data-stu-id="430b9-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="430b9-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="430b9-120">See also</span></span>

* [<span data-ttu-id="430b9-121">Cursor</span><span class="sxs-lookup"><span data-stu-id="430b9-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="430b9-122">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="430b9-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="430b9-123">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="430b9-123">Button</span></span>](button.md)
* [<span data-ttu-id="430b9-124">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="430b9-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="430b9-125">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="430b9-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="430b9-126">Manipulation</span><span class="sxs-lookup"><span data-stu-id="430b9-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="430b9-127">Handmenü</span><span class="sxs-lookup"><span data-stu-id="430b9-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="430b9-128">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="430b9-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="430b9-129">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="430b9-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="430b9-130">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="430b9-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="430b9-131">Tastatur</span><span class="sxs-lookup"><span data-stu-id="430b9-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="430b9-132">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="430b9-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="430b9-133">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="430b9-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="430b9-134">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="430b9-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="430b9-135">Shader</span><span class="sxs-lookup"><span data-stu-id="430b9-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="430b9-136">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="430b9-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="430b9-137">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="430b9-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="430b9-138">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="430b9-138">Surface magnetism</span></span>](surface-magnetism.md)
