---
title: Leistungsempfehlungen für Unreal
description: Erfahren Sie, wie Sie mit unseren empfohlenen Unreal-Projekteinstellungen die beste Leistung in Ihren Mixed Reality-Apps erzielen.
author: hferrone
ms.author: safarooq
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Leistung, Optimierung, Einstellungen, Dokumentation
ms.openlocfilehash: e956f12d27c826cff35e0b65957060953073a28b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583060"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="53aff-104">Leistungsempfehlungen für Unreal</span><span class="sxs-lookup"><span data-stu-id="53aff-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="53aff-105">Die Unreal Engine besitzt zahlreiche Funktionen, die die Leistung einer App steigern können, die alle auf der unter [Leistungsempfehlungen für Mixed Reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) dargelegten Diskussion basieren.</span><span class="sxs-lookup"><span data-stu-id="53aff-105">Unreal Engine has several features that can increase an apps performance, all based on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span> <span data-ttu-id="53aff-106">Sie sollten sich zunächst über Engpässe bei Anwendungen, Analyse und Profilerstellung für Mixed Reality-Apps und allgemeine Leistungsfixes informieren, bevor Sie weiterlesen.</span><span class="sxs-lookup"><span data-stu-id="53aff-106">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="53aff-107">Empfohlenen Unreal-Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="53aff-107">Recommended Unreal project settings</span></span>

<span data-ttu-id="53aff-108">Sie finden jede der folgenden Einstellungen unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen).</span><span class="sxs-lookup"><span data-stu-id="53aff-108">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="53aff-109">Mit dem mobilen VR-Renderer:</span><span class="sxs-lookup"><span data-stu-id="53aff-109">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="53aff-110">Scrollen Sie zum Abschnitt **Project**, wählen Sie **Target Hardware** (Zielhardware) aus, und legen Sie die Zielplattform auf **Mobile/Tablet** fest.</span><span class="sxs-lookup"><span data-stu-id="53aff-110">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="53aff-112">Verwenden des Forward Renderers:</span><span class="sxs-lookup"><span data-stu-id="53aff-112">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="53aff-113">Der Forward Renderer eignet sich aufgrund der Anzahl von Funktionen, die einzeln deaktiviert werden können, wesentlich besser für Mixed Reality als die standardmäßige verzögerte Renderingpipeline.</span><span class="sxs-lookup"><span data-stu-id="53aff-113">Forward Renderer is much better for Mixed Reality than the default Deferred rendering pipeline because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="53aff-114">Weitere Informationen finden Sie in der [Dokumentation zu Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="53aff-114">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Vorwärtsrendering](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="53aff-116">In der mobilen Multiansicht:</span><span class="sxs-lookup"><span data-stu-id="53aff-116">Using mobile multi-view:</span></span>
    * <span data-ttu-id="53aff-117">Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Abschnitt **VR**, und aktivieren Sie sowohl **Instanced Stereo** (Instanziiertes Stereo) als auch **Mobile Multi-View** (Mobile Multiansicht).</span><span class="sxs-lookup"><span data-stu-id="53aff-117">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="53aff-118">Mobile-HDR sollte deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="53aff-118">Mobile HDR should be unchecked.</span></span>

![VR-Renderingeinstellungen](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="53aff-120">**[Nur OpenXR]** Stellen Sie sicher, dass **Standard** oder **D3D12** als **Standard-RHI** ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="53aff-120">**[OpenXR only]** Ensure **Default** or **D3D12** is the selected **Default RHI**:</span></span>
    * <span data-ttu-id="53aff-121">Wenn Sie **D3D11** auswählen, wirkt sich dies negativ auf die Leistung aus, da die Plattform einen zusätzlichen Renderdurchlauf ausführt.</span><span class="sxs-lookup"><span data-stu-id="53aff-121">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="53aff-122">**D3D12** sollte zusätzlich zur Vermeidung des zusätzlichen Renderdurchlaufs Leistungsverbesserungen beim Rendering bewirken.</span><span class="sxs-lookup"><span data-stu-id="53aff-122">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![Standard-RHI](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="53aff-124">Deaktivieren von Vertex Fogging:</span><span class="sxs-lookup"><span data-stu-id="53aff-124">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="53aff-125">Vertex-Fogging wendet an jedem Scheitelpunkt in einem Polygon Nebelberechnungen an und interpoliert die Ergebnisse dann auf der Vorderseite des Polygons.</span><span class="sxs-lookup"><span data-stu-id="53aff-125">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="53aff-126">Wenn Ihr Spiel keinen Nebel verwendet, empfehlen wir, Vertex Fogging zu deaktivieren, um die Schattierungsleistung zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="53aff-126">If your game does not use fog, we recommend disabling Vertex Fogging to increase shading performance.</span></span>

![Vertex-Fogging-Optionen](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="53aff-128">Deaktivieren des Okklusionscullings:</span><span class="sxs-lookup"><span data-stu-id="53aff-128">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="53aff-129">Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Bereich **Culling**, und deaktivieren Sie **Occlusion Culling**.</span><span class="sxs-lookup"><span data-stu-id="53aff-129">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="53aff-130">Wenn Sie das Okklusionsculling für das Rendern einer detailreichen Szene benötigen, empfiehlt es sich, unter **Engine > Rendering** die Option **Support Software Occlusion Culling** (Softwareokklusionsculling unterstützen) zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="53aff-130">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="53aff-131">Die Arbeit lässt Unreal von der CPU erledigen und vermeidet GPU-Okklusionsabfragen, deren Leistung auf HoloLens 2 schlecht ist.</span><span class="sxs-lookup"><span data-stu-id="53aff-131">Unreal will do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="53aff-132">Okklusionsculling in der GPU auf mobilen Geräten ist langsam.</span><span class="sxs-lookup"><span data-stu-id="53aff-132">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="53aff-133">Im Allgemeinen ist es sinnvoll, dass die GPU sich hauptsächlich um das Rendering kümmert.</span><span class="sxs-lookup"><span data-stu-id="53aff-133">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="53aff-134">Wenn Sie vermuten, dass Okklusion die Leistung verbessert, versuchen Sie stattdessen, Softwareokklusion zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="53aff-134">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> 

> [!NOTE]
> <span data-ttu-id="53aff-135">Das Aktivieren von Softwareokklusion kann die Leistung auch verschlechtern, wenn die CPU durch eine hohe Anzahl von Zeichenaufrufen bereits stark ausgelastet ist.</span><span class="sxs-lookup"><span data-stu-id="53aff-135">Enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Deaktivieren des Okklusionscullings](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="53aff-137">Durchlauf zum Deaktivieren der benutzerdefinierten Tiefenschablone:</span><span class="sxs-lookup"><span data-stu-id="53aff-137">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="53aff-138">Für das Deaktivieren der benutzerdefinierten Tiefenschablone ist ein zusätzlicher Durchgang erforderlich, was bedeutet, dass es langsam ist.</span><span class="sxs-lookup"><span data-stu-id="53aff-138">Disabling Custom Depth-Stencil requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="53aff-139">Transparenz ist bei Unreal ebenfalls langsam.</span><span class="sxs-lookup"><span data-stu-id="53aff-139">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="53aff-140">Weitere Informationen finden Sie in der [Dokumentation zu Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="53aff-140">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Tiefenschablone](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="53aff-142">Verringern von überlappenden Schattenkarten:</span><span class="sxs-lookup"><span data-stu-id="53aff-142">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="53aff-143">Durch das Verringern der Anzahl der Schattenkarten wird die Leistung verbessert.</span><span class="sxs-lookup"><span data-stu-id="53aff-143">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="53aff-144">Im Allgemeinen sollten Sie die Eigenschaft auf 1 festlegen, es sei denn, es gibt einen sichtbaren Qualitätsverlust.</span><span class="sxs-lookup"><span data-stu-id="53aff-144">Generally, you should set the property to 1 unless there's a visible quality loss.</span></span> 

![Überlappende Schattenkarten](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="53aff-146">Optionale Einstellungen</span><span class="sxs-lookup"><span data-stu-id="53aff-146">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="53aff-147">Mit den folgenden Einstellungen kann möglicherweise die Leistung verbessert werden, aber um den Preis, dass bestimmte Features deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="53aff-147">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="53aff-148">Verwenden Sie diese Einstellungen nur, wenn Sie sicher sind, dass Sie die betreffenden Features nicht benötigen.</span><span class="sxs-lookup"><span data-stu-id="53aff-148">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="53aff-149">Verringerung der Shaderpermutation bei mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="53aff-149">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="53aff-150">Wenn sich Ihre Lichter nicht unabhängig von der Kamera bewegen, können Sie den Eigenschaftswert unbedenklich auf 0 festlegen.</span><span class="sxs-lookup"><span data-stu-id="53aff-150">If your lights don't move independently of the camera, then you can safely set the property value to 0.</span></span> <span data-ttu-id="53aff-151">Der Hauptvorteil besteht darin, dass es dies Unreal ermöglicht, mehrere Shaderpermutationen auszusortieren, sodass die Shaderkompilierung beschleunigt wird.</span><span class="sxs-lookup"><span data-stu-id="53aff-151">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Verringerung der Shaderpermutation bei mobilen Geräten](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="53aff-153">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="53aff-153">See also</span></span>

* [<span data-ttu-id="53aff-154">Leistungsrichtlinien für die Unreal-Engine auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="53aff-154">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)