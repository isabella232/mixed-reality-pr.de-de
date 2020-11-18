---
title: Leistungsempfehlungen für Unreal
description: Empfehlungen für optimale Leistung von Mixed Reality-Apps in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Leistung, Optimierung, Einstellungen, Dokumentation
ms.openlocfilehash: 21bd3ee9fb7db23eab9365e41adfd0033aa0046e
ms.sourcegitcommit: 520c69eb761ad6083b36f448bbcfab89e343e40d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549127"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="d558e-104">Leistungsempfehlungen für Unreal</span><span class="sxs-lookup"><span data-stu-id="d558e-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="d558e-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="d558e-105">Overview</span></span>

<span data-ttu-id="d558e-106">Dieser Artikel baut auf den [Leistungsempfehlungen für Mixed Reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) auf, legt den Schwerpunkt aber auf spezifische Funktionen der Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="d558e-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="d558e-107">Sie sollten sich zunächst über Engpässe bei Anwendungen, Analyse und Profilerstellung für Mixed Reality-Apps und allgemeine Leistungsfixes informieren, bevor Sie weiterlesen.</span><span class="sxs-lookup"><span data-stu-id="d558e-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="d558e-108">Empfohlenen Unreal-Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="d558e-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="d558e-109">Sie finden jede der folgenden Einstellungen unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen).</span><span class="sxs-lookup"><span data-stu-id="d558e-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="d558e-110">Mit dem mobilen VR-Renderer:</span><span class="sxs-lookup"><span data-stu-id="d558e-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="d558e-111">Scrollen Sie zum Abschnitt **Project**, wählen Sie **Target Hardware** (Zielhardware) aus, und legen Sie die Zielplattform auf **Mobile/Tablet** fest.</span><span class="sxs-lookup"><span data-stu-id="d558e-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="d558e-113">Verwenden des Forward Renderers:</span><span class="sxs-lookup"><span data-stu-id="d558e-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="d558e-114">Dieses Feature eignet sich viel besser für Mixed Reality als die standardmäßige Pipeline beim Deferred Rendering (aufgeschobenen Rendering).</span><span class="sxs-lookup"><span data-stu-id="d558e-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="d558e-115">Dies liegt hauptsächlich an der Anzahl der Features, die einzeln deaktiviert werden können.</span><span class="sxs-lookup"><span data-stu-id="d558e-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="d558e-116">Weitere Informationen finden Sie in der [Dokumentation zu Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="d558e-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Vorwärtsrendering](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="d558e-118">In der mobilen Multiansicht:</span><span class="sxs-lookup"><span data-stu-id="d558e-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="d558e-119">Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Abschnitt **VR**, und aktivieren Sie sowohl **Instanced Stereo** (Instanziiertes Stereo) als auch **Mobile Multi-View** (Mobile Multiansicht).</span><span class="sxs-lookup"><span data-stu-id="d558e-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="d558e-120">Mobile-HDR sollte deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="d558e-120">Mobile HDR should be unchecked.</span></span>

![VR-Renderingeinstellungen](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="d558e-122">Stellen Sie sicher, dass **Standard** oder **D3D12** als **Standard-RHI**, ausgewählt ist, wenn OpenXR verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d558e-122">Ensure **Default** or **D3D12** is the selected **Default RHI** when using OpenXR.</span></span>
    * <span data-ttu-id="d558e-123">Wenn Sie **D3D11** auswählen, wirkt sich dies negativ auf die Leistung aus, da die Plattform einen zusätzlichen Renderdurchlauf ausführt.</span><span class="sxs-lookup"><span data-stu-id="d558e-123">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="d558e-124">**D3D12** sollte zusätzlich zur Vermeidung des zusätzlichen Renderdurchlaufs Leistungsverbesserungen beim Rendering bewirken.</span><span class="sxs-lookup"><span data-stu-id="d558e-124">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![Standard-RHI](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="d558e-126">Deaktivieren von Vertex Fogging:</span><span class="sxs-lookup"><span data-stu-id="d558e-126">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="d558e-127">Vertex-Fogging wendet an jedem Scheitelpunkt in einem Polygon Nebelberechnungen an und interpoliert die Ergebnisse dann auf der Vorderseite des Polygons.</span><span class="sxs-lookup"><span data-stu-id="d558e-127">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="d558e-128">Wenn Ihr Spiel keinen Nebel verwendet, sollten Sie diese Einstellung auswählen, um die Schattierungsleistung zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="d558e-128">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![Vertex-Fogging-Optionen](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="d558e-130">Deaktivieren des Okklusionscullings:</span><span class="sxs-lookup"><span data-stu-id="d558e-130">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="d558e-131">Scrollen Sie zum Abschnitt **Engine**, wählen Sie **Rendering** aus, erweitern Sie den Bereich **Culling**, und deaktivieren Sie **Occlusion Culling**.</span><span class="sxs-lookup"><span data-stu-id="d558e-131">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="d558e-132">Wenn Sie das Okklusionsculling für das Rendern einer detailreichen Szene benötigen, empfiehlt es sich, unter **Engine > Rendering** die Option **Support Software Occlusion Culling** (Softwareokklusionsculling unterstützen) zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d558e-132">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="d558e-133">Dadurch kann Unreal die CPU verwenden und GPU-Okklusionsabfragen vermeiden, die bei HoloLens 2 keine hohe Performance erzielen.</span><span class="sxs-lookup"><span data-stu-id="d558e-133">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="d558e-134">Okklusionsculling in der GPU auf mobilen Geräten ist langsam.</span><span class="sxs-lookup"><span data-stu-id="d558e-134">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="d558e-135">Im Allgemeinen ist es sinnvoll, dass die GPU sich hauptsächlich um das Rendering kümmert.</span><span class="sxs-lookup"><span data-stu-id="d558e-135">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="d558e-136">Wenn Sie vermuten, dass Okklusion die Leistung verbessert, versuchen Sie stattdessen, Softwareokklusion zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d558e-136">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="d558e-137">Beachten Sie, dass das Aktivieren von Softwareokklusion die Leistung auch verschlechtern kann, wenn die CPU durch eine hohe Anzahl von Zeichenaufrufen bereits stark ausgelastet ist.</span><span class="sxs-lookup"><span data-stu-id="d558e-137">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Deaktivieren des Okklusionscullings](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="d558e-139">Durchlauf zum Deaktivieren der benutzerdefinierten Tiefenschablone:</span><span class="sxs-lookup"><span data-stu-id="d558e-139">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="d558e-140">Für dieses Feature ist ein zusätzlicher Durchgang erforderlich, was bedeutet, dass es langsam ist.</span><span class="sxs-lookup"><span data-stu-id="d558e-140">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="d558e-141">Transparenz ist bei Unreal ebenfalls langsam.</span><span class="sxs-lookup"><span data-stu-id="d558e-141">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="d558e-142">Weitere Informationen finden Sie in der [Dokumentation zu Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="d558e-142">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Tiefenschablone](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="d558e-144">Verringern von überlappenden Schattenkarten:</span><span class="sxs-lookup"><span data-stu-id="d558e-144">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="d558e-145">Durch das Verringern der Anzahl der Schattenkarten wird die Leistung verbessert.</span><span class="sxs-lookup"><span data-stu-id="d558e-145">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="d558e-146">Im Allgemeinen sollte dieser Wert auf 1 festgelegt werden, es sei denn, es gibt einen sichtbaren Qualitätsverlust.</span><span class="sxs-lookup"><span data-stu-id="d558e-146">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![Überlappende Schattenkarten](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="d558e-148">Optionale Einstellungen</span><span class="sxs-lookup"><span data-stu-id="d558e-148">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="d558e-149">Mit den folgenden Einstellungen kann möglicherweise die Leistung verbessert werden, aber um den Preis, dass bestimmte Features deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="d558e-149">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="d558e-150">Verwenden Sie diese Einstellungen nur, wenn Sie sicher sind, dass Sie die betreffenden Features nicht benötigen.</span><span class="sxs-lookup"><span data-stu-id="d558e-150">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="d558e-151">Verringerung der Shaderpermutation bei mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="d558e-151">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="d558e-152">Wenn sich Ihre Lichter nicht unabhängig von der Kamera bewegen, können Sie diesen Wert unbedenklich auf 0 festlegen.</span><span class="sxs-lookup"><span data-stu-id="d558e-152">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="d558e-153">Der Hauptvorteil besteht darin, dass es dies Unreal ermöglicht, mehrere Shaderpermutationen auszusortieren, sodass die Shaderkompilierung beschleunigt wird.</span><span class="sxs-lookup"><span data-stu-id="d558e-153">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Verringerung der Shaderpermutation bei mobilen Geräten](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="d558e-155">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d558e-155">See also</span></span>
* [<span data-ttu-id="d558e-156">Leistungsrichtlinien für die Unreal-Engine auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="d558e-156">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)