---
title: Material Empfehlungen in Unreal
description: Übersicht über Materialien in der Unreal Engine.
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Entwicklung, Material, Dokumentation, Guides, Features, holograms, Spieleentwicklung
ms.openlocfilehash: bfce6e6bf8acd58821dba1213e1f1ab571d85a0c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684547"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="70f47-104">Material Empfehlungen in Unreal</span><span class="sxs-lookup"><span data-stu-id="70f47-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="70f47-105">Material kann die Leistung in der Unreal Engine ausmachen oder unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="70f47-105">Materials can make or break performance in Unreal Engine.</span></span> <span data-ttu-id="70f47-106">Diese Seite fungiert als Schnellstart für die grundlegenden Einstellungen, die Sie verwenden sollten, um die bestmögliche Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="70f47-106">This page acts as a quick-start on the basic settings you should be using in order to get the best performance.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="70f47-107">Verwenden von customizeduvs</span><span class="sxs-lookup"><span data-stu-id="70f47-107">Using CustomizedUVs</span></span>

<span data-ttu-id="70f47-108">Wenn Sie benutzerdefinierte Benutzerkonten in Ihrem Material bereitstellen müssen, sollten Sie stattdessen customizeduvs verwenden, anstatt die UV-Struktur des Textur Knotens direkt zu ändern.</span><span class="sxs-lookup"><span data-stu-id="70f47-108">If you need to provide tiling of UVs on your material, you should use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="70f47-109">Mit customizeduvs kann eine UV-Manipulation in den Vertex-Shadern statt im Pixel-Shader erfolgen.</span><span class="sxs-lookup"><span data-stu-id="70f47-109">CustomizedUVs allow UV manipulation to happen in the Vertex shaders rather than Pixel shader.</span></span> 

![Material Einstellungen in Unreal](images/unreal-materials-img-01c.png)

<span data-ttu-id="70f47-111">Weitere Details zu den Materialien finden Sie in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) und in den bewährten Beispielen in den folgenden Screenshots:</span><span class="sxs-lookup"><span data-stu-id="70f47-111">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="70f47-112">[ ![ Empfohlene Material Einstellungen in der ](images/unreal-materials-img-01.png) von Unreal ](images/unreal-materials-img-01.png#lightbox) 
 *empfohlenen Material Einrichtung*</span><span class="sxs-lookup"><span data-stu-id="70f47-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="70f47-113">[ ![ Nicht empfohlene Material Einstellungen in Unreal ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 *Non-Recommended Material Setup*</span><span class="sxs-lookup"><span data-stu-id="70f47-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="70f47-114">Ändern des Blend-Modus</span><span class="sxs-lookup"><span data-stu-id="70f47-114">Changing Blend Mode</span></span>

<span data-ttu-id="70f47-115">Sie sollten den Blend-Modus auf "undurchsichtig" festlegen, es sei denn, es gibt einen starken Grund dafür.</span><span class="sxs-lookup"><span data-stu-id="70f47-115">You should set blend mode to opaque unless there is a strong reason to do otherwise.</span></span> <span data-ttu-id="70f47-116">Maskierte und durchlässiges Material sind langsam.</span><span class="sxs-lookup"><span data-stu-id="70f47-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="70f47-117">Weitere Details zu den Materialien finden Sie in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="70f47-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Ändern des Blend-Modus](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="70f47-119">Aktualisieren der Beleuchtung für mobile Geräte</span><span class="sxs-lookup"><span data-stu-id="70f47-119">Updating lighting for mobile</span></span>

<span data-ttu-id="70f47-120">Die vollständige Genauigkeit sollte deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="70f47-120">Full precision should be turned off.</span></span> <span data-ttu-id="70f47-121">Lightmap-Beleuchtung kann durch das Einschalten von direktionalen Informationen abgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="70f47-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="70f47-122">Wenn diese Option deaktiviert ist, ist die Beleuchtung aus lightmaps flach, aber günstiger.</span><span class="sxs-lookup"><span data-stu-id="70f47-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Mobile Material Einstellungen in Unreal](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="70f47-124">Anpassen der vorwärts Schattierung</span><span class="sxs-lookup"><span data-stu-id="70f47-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="70f47-125">Diese Optionen verbessern die visuelle Genauigkeit auf Kosten der Leistung.</span><span class="sxs-lookup"><span data-stu-id="70f47-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="70f47-126">Sie sollten für maximale Leistung ausgeschaltet werden.</span><span class="sxs-lookup"><span data-stu-id="70f47-126">They should be turned off for maximum performance.</span></span>

![Weiterleiten von Schattierungs Material-Einstellungen in Unreal](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="70f47-128">Festlegen der Material Durchlässigkeit</span><span class="sxs-lookup"><span data-stu-id="70f47-128">Setting material translucency</span></span>

<span data-ttu-id="70f47-129">Gibt an, dass das lichtdurchlässiges Material nicht von der Blüte oder von DOF beeinflusst werden soll.</span><span class="sxs-lookup"><span data-stu-id="70f47-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="70f47-130">Da beide Effekte in Mr selten vorkommen, sollte diese Einstellung standardmäßig auf ON festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="70f47-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![Einstellung "Mobile separate Transluzenz" in Unreal](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="70f47-132">Optionale Einstellungen</span><span class="sxs-lookup"><span data-stu-id="70f47-132">Optional settings</span></span>

<span data-ttu-id="70f47-133">Die folgenden Einstellungen können die Leistung verbessern, aber beachten Sie, dass Sie bestimmte Funktionen deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="70f47-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="70f47-134">Verwenden Sie diese Einstellungen nur, wenn Sie sicher sind, dass Sie die betreffenden Features nicht benötigen.</span><span class="sxs-lookup"><span data-stu-id="70f47-134">Only use these settings if you are sure you don't need the features in question.</span></span>

![Optionale Material Einstellungen in Unreal](images/unreal-materials-img-06.jpg)

<span data-ttu-id="70f47-136">Wenn Ihr Material keine Reflektionen oder glänzen erfordert, kann das Festlegen dieser Option zu einer enormen Leistungssteigerung führt.</span><span class="sxs-lookup"><span data-stu-id="70f47-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="70f47-137">Bei internen Tests ist es so schnell wie "nicht beleuchtet", während Beleuchtungs Informationen bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="70f47-137">In internal testing, it is as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="70f47-138">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="70f47-138">Best practices</span></span>

<span data-ttu-id="70f47-139">Die folgenden Einstellungen sind nicht "Einstellungen", wie Sie bewährte Methoden im Zusammenhang mit Materialien sind.</span><span class="sxs-lookup"><span data-stu-id="70f47-139">The following are not "settings" as much as they are best practices related to Materials.</span></span>

<span data-ttu-id="70f47-140">Wenn Sie Parameter erstellen, bevorzugen Sie die Verwendung von "statischen Parametern", sofern möglich.</span><span class="sxs-lookup"><span data-stu-id="70f47-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="70f47-141">Statische Switches können verwendet werden, um einen vollständigen Branch eines Materials ohne Lauf Zeit Kosten zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="70f47-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="70f47-142">Instanzen können unterschiedliche Werte aufweisen, sodass eine vorlagenbasierte shadereinrichtung ohne Leistungseinbußen möglich ist.</span><span class="sxs-lookup"><span data-stu-id="70f47-142">Instances can have different values, making it possible to have a templated shader setup with no performance loss.</span></span> <span data-ttu-id="70f47-143">Der Nachteil ist jedoch, dass dadurch viele Permutationen erstellt werden, die eine große Shader-Neukompilierung bewirken.</span><span class="sxs-lookup"><span data-stu-id="70f47-143">The downside, however, is that this creates many permutations that will cause a lot of shader recompilation.</span></span> <span data-ttu-id="70f47-144">Versuchen Sie, die Anzahl der statischen Parameter im Material und die Anzahl der Permutationen dieser statischen Parameter zu minimieren, die tatsächlich verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="70f47-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are actually used.</span></span> <span data-ttu-id="70f47-145">Weitere Informationen zum Rendern von Materialparametern finden Sie in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span><span class="sxs-lookup"><span data-stu-id="70f47-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![Bewährte Methoden für Material Einstellungen](images/unreal-materials-img-07.jpg)

<span data-ttu-id="70f47-147">Beim Erstellen von Material Instanzen sollte die-Einstellung für die **Material Instanz-Konstante** über die dynamische Material Instanz bevorzugt werden.</span><span class="sxs-lookup"><span data-stu-id="70f47-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="70f47-148">Die **materialinstanzkonstante** ist ein instanziziertes Material, das nur einmal vor der Laufzeit berechnet.</span><span class="sxs-lookup"><span data-stu-id="70f47-148">**Material Instance Constant** is an instanced Material that calculates only once, prior to runtime.</span></span>

<span data-ttu-id="70f47-149">Die über den Inhalts Browser erstellte Material Instanz (mit der **rechten Maustaste auf > Create Material instance** ) ist eine Material Instanz-Konstante.</span><span class="sxs-lookup"><span data-stu-id="70f47-149">The material instance created via the Content Browser ( **right-click > Create Material Instance** ) is a Material Instance Constant.</span></span> <span data-ttu-id="70f47-150">Die dynamische Material Instanz wird über Code erstellt.</span><span class="sxs-lookup"><span data-stu-id="70f47-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="70f47-151">Weitere Informationen zu Material Instanzen finden Sie in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span><span class="sxs-lookup"><span data-stu-id="70f47-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![Erstellen von Material Instanzen in Unreal](images/unreal-materials-img-08.png)

<span data-ttu-id="70f47-153">Beobachten Sie die Komplexität ihrer Materialien/Shader.</span><span class="sxs-lookup"><span data-stu-id="70f47-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="70f47-154">Sie können die Kosten für Ihr Material auf verschiedenen Plattformen anzeigen, indem Sie auf das Platt Form Statistik-Symbol klicken.</span><span class="sxs-lookup"><span data-stu-id="70f47-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="70f47-155">Weitere Informationen zu Materialien finden Sie auch in der [Unreal Engine-Dokumentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="70f47-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Erstellen von dynamischen Einstellungen für Material Instanzen in Unreal](images/unreal-materials-img-09.png)

<span data-ttu-id="70f47-157">Sie erhalten einen kurzen Überblick über die relative Komplexität Ihres Shaders über den Shader-Komplexitäts [Ansichtsmodus](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span><span class="sxs-lookup"><span data-stu-id="70f47-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="70f47-158">Hotkey im Ansichtsmodus: alt + 8</span><span class="sxs-lookup"><span data-stu-id="70f47-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="70f47-159">Konsolen Befehl: ViewMode shaderkomplexität</span><span class="sxs-lookup"><span data-stu-id="70f47-159">Console command: viewmode shadercomplexity</span></span>

![Komplexität von Material in Unreal](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="70f47-161">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="70f47-161">See also</span></span>
* [<span data-ttu-id="70f47-162">Mobile Materialien</span><span class="sxs-lookup"><span data-stu-id="70f47-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="70f47-163">Ansichtsmodi</span><span class="sxs-lookup"><span data-stu-id="70f47-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="70f47-164">Material Instanzen</span><span class="sxs-lookup"><span data-stu-id="70f47-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
