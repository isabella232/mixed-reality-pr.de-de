---
title: Leistungsempfehlungen für Unreal
description: Empfehlungen für optimale Leistung von Mixed Reality-Apps in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Leistung, Optimierung, Einstellungen, Dokumentation
ms.openlocfilehash: 64c8cdf4900234a4486cf9b575671321a8430160
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91697235"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="aaac1-104">Leistungsempfehlungen für Unreal</span><span class="sxs-lookup"><span data-stu-id="aaac1-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="aaac1-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="aaac1-105">Overview</span></span>

<span data-ttu-id="aaac1-106">Dieser Artikel baut auf den [Leistungsempfehlungen für Mixed Reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) auf, legt den Schwerpunkt aber auf spezifische Funktionen der Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="aaac1-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="aaac1-107">Sie sollten sich zunächst über Engpässe bei Anwendungen, Analyse und Profilerstellung für Mixed Reality-Apps und allgemeine Leistungsfixes informieren, bevor Sie weiterlesen.</span><span class="sxs-lookup"><span data-stu-id="aaac1-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="aaac1-108">Empfohlenen Unreal-Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="aaac1-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="aaac1-109">Sie finden jede der folgenden Einstellungen unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen).</span><span class="sxs-lookup"><span data-stu-id="aaac1-109">You can find each of the following settings in **Edit > Project Settings** .</span></span>

1. <span data-ttu-id="aaac1-110">Mit dem mobilen VR-Renderer:</span><span class="sxs-lookup"><span data-stu-id="aaac1-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="aaac1-111">Scrollen Sie zum Abschnitt **Project** , wählen Sie **Target Hardware** (Zielhardware) aus, und legen Sie die Zielplattform auf **Mobile/Tablet** fest.</span><span class="sxs-lookup"><span data-stu-id="aaac1-111">Scroll to the **Project** section, select **Target Hardware** , and set the target platform to **Mobile/Tablet**</span></span>

![Zieleinstellung „Mobile“](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="aaac1-113">Verwenden des Forward Renderers:</span><span class="sxs-lookup"><span data-stu-id="aaac1-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="aaac1-114">Dieses Feature eignet sich viel besser für Mixed Reality als die standardmäßige Pipeline beim Deferred Rendering (aufgeschobenen Rendering).</span><span class="sxs-lookup"><span data-stu-id="aaac1-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="aaac1-115">Dies liegt hauptsächlich an der Anzahl der Features, die einzeln deaktiviert werden können.</span><span class="sxs-lookup"><span data-stu-id="aaac1-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="aaac1-116">Weitere Informationen finden Sie in der [Dokumentation zu Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="aaac1-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Vorwärtsrendering](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="aaac1-118">Deaktivieren von Vertex Fogging:</span><span class="sxs-lookup"><span data-stu-id="aaac1-118">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="aaac1-119">Vertex-Fogging wendet an jedem Scheitelpunkt in einem Polygon Nebelberechnungen an und interpoliert die Ergebnisse dann auf der Vorderseite des Polygons.</span><span class="sxs-lookup"><span data-stu-id="aaac1-119">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="aaac1-120">Wenn Ihr Spiel keinen Nebel verwendet, sollten Sie diese Einstellung auswählen, um die Schattierungsleistung zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="aaac1-120">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![Vertex-Fogging-Optionen](images/unreal/performance-recommendations-img-05.png)

4. <span data-ttu-id="aaac1-122">Deaktivieren des Okklusionscullings:</span><span class="sxs-lookup"><span data-stu-id="aaac1-122">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="aaac1-123">Scrollen Sie zum Abschnitt **Engine** , wählen Sie **Rendering** aus, erweitern Sie den Bereich **Culling** , und deaktivieren Sie **Occlusion Culling** .</span><span class="sxs-lookup"><span data-stu-id="aaac1-123">Scroll to the **Engine** section, select **Rendering** , expand the **Culling** section, and uncheck **Occlusion Culling** .</span></span>
        + <span data-ttu-id="aaac1-124">Wenn Sie das Okklusionsculling für das Rendern einer detailreichen Szene benötigen, empfiehlt es sich, unter **Engine > Rendering** die Option **Support Software Occlusion Culling** (Softwareokklusionsculling unterstützen) zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="aaac1-124">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering** .</span></span> <span data-ttu-id="aaac1-125">Dadurch kann Unreal die CPU verwenden und GPU-Okklusionsabfragen vermeiden, die bei HoloLens 2 keine hohe Performance erzielen.</span><span class="sxs-lookup"><span data-stu-id="aaac1-125">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="aaac1-126">Okklusionsculling in der GPU auf mobilen Geräten ist langsam.</span><span class="sxs-lookup"><span data-stu-id="aaac1-126">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="aaac1-127">Im Allgemeinen ist es sinnvoll, dass die GPU sich hauptsächlich um das Rendering kümmert.</span><span class="sxs-lookup"><span data-stu-id="aaac1-127">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="aaac1-128">Wenn Sie vermuten, dass Okklusion die Leistung verbessert, versuchen Sie stattdessen, Softwareokklusion zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="aaac1-128">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="aaac1-129">Beachten Sie, dass das Aktivieren von Softwareokklusion die Leistung auch verschlechtern kann, wenn die CPU durch eine hohe Anzahl von Zeichenaufrufen bereits stark ausgelastet ist.</span><span class="sxs-lookup"><span data-stu-id="aaac1-129">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Deaktivieren des Okklusionscullings](images/unreal/performance-recommendations-img-02.png)

    
5. <span data-ttu-id="aaac1-131">Deaktivieren der Tiefenschablone:</span><span class="sxs-lookup"><span data-stu-id="aaac1-131">Disabling Depth-Stencil:</span></span>
    * <span data-ttu-id="aaac1-132">Für dieses Feature ist ein zusätzlicher Durchgang erforderlich, was bedeutet, dass es langsam ist.</span><span class="sxs-lookup"><span data-stu-id="aaac1-132">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="aaac1-133">Transparenz ist bei Unreal ebenfalls langsam.</span><span class="sxs-lookup"><span data-stu-id="aaac1-133">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="aaac1-134">Weitere Informationen finden Sie in der [Dokumentation zu Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="aaac1-134">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Tiefenschablone](images/unreal/performance-recommendations-img-06.png)

6. <span data-ttu-id="aaac1-136">In der mobilen Multiansicht:</span><span class="sxs-lookup"><span data-stu-id="aaac1-136">Using mobile multi-view:</span></span>
    * <span data-ttu-id="aaac1-137">Scrollen Sie zum Abschnitt **Engine** , wählen Sie **Rendering** aus, erweitern Sie den Abschnitt **VR** , und aktivieren Sie sowohl **Instanced Stereo** (Instanziiertes Stereo) als auch **Mobile Multi-View** (Mobile Multiansicht).</span><span class="sxs-lookup"><span data-stu-id="aaac1-137">Scroll to the **Engine** section, select **Rendering** , expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View** .</span></span> <span data-ttu-id="aaac1-138">Mobile-HDR sollte deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="aaac1-138">Mobile HDR should be unchecked.</span></span>

![VR-Renderingeinstellungen](images/unreal/performance-recommendations-img-03.png)

7. <span data-ttu-id="aaac1-140">Verringern von überlappenden Schattenkarten:</span><span class="sxs-lookup"><span data-stu-id="aaac1-140">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="aaac1-141">Durch das Verringern der Anzahl der Schattenkarten wird die Leistung verbessert.</span><span class="sxs-lookup"><span data-stu-id="aaac1-141">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="aaac1-142">Im Allgemeinen sollte dieser Wert auf 1 festgelegt werden, es sei denn, es gibt einen sichtbaren Qualitätsverlust.</span><span class="sxs-lookup"><span data-stu-id="aaac1-142">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![Überlappende Schattenkarten](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="aaac1-144">Optionale Einstellungen</span><span class="sxs-lookup"><span data-stu-id="aaac1-144">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="aaac1-145">Mit den folgenden Einstellungen kann möglicherweise die Leistung verbessert werden, aber um den Preis, dass bestimmte Features deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="aaac1-145">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="aaac1-146">Verwenden Sie diese Einstellungen nur, wenn Sie sicher sind, dass Sie die betreffenden Features nicht benötigen.</span><span class="sxs-lookup"><span data-stu-id="aaac1-146">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="aaac1-147">Verringerung der Shaderpermutation bei mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="aaac1-147">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="aaac1-148">Wenn sich Ihre Lichter nicht unabhängig von der Kamera bewegen, können Sie diesen Wert unbedenklich auf 0 festlegen.</span><span class="sxs-lookup"><span data-stu-id="aaac1-148">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="aaac1-149">Der Hauptvorteil besteht darin, dass es dies Unreal ermöglicht, mehrere Shaderpermutationen auszusortieren, sodass die Shaderkompilierung beschleunigt wird.</span><span class="sxs-lookup"><span data-stu-id="aaac1-149">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Verringerung der Shaderpermutation bei mobilen Geräten](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="aaac1-151">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="aaac1-151">See also</span></span>
* [<span data-ttu-id="aaac1-152">Leistungsrichtlinien für die Unreal-Engine auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="aaac1-152">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)