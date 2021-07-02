---
title: Laden von Szenensysteminhalten
description: Dokumentation zum Laden des Szenensystems mit MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: c6bc6474afd50fe265853e53c0f29009d816cf51
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177586"
---
# <a name="scene-system-content-loading"></a><span data-ttu-id="210de-104">Laden von Szenensysteminhalten</span><span class="sxs-lookup"><span data-stu-id="210de-104">Scene system content loading</span></span>

<span data-ttu-id="210de-105">Alle Inhaltsladevorgänge sind asynchron, und standardmäßig ist das laden von Inhalten additiv.</span><span class="sxs-lookup"><span data-stu-id="210de-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="210de-106">Manager- und Beleuchtungsszenen sind nie von Inhaltsladevorgängen betroffen.</span><span class="sxs-lookup"><span data-stu-id="210de-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="210de-107">Informationen zum Überwachen des Ladefortschritts und zur Szenenaktivierung finden Sie unter [Überwachen des Ladens von Inhalten.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="210de-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="210de-108">Laden von Inhalten</span><span class="sxs-lookup"><span data-stu-id="210de-108">Loading content</span></span>

<span data-ttu-id="210de-109">Verwenden Sie zum Laden von Inhaltsszenen die `LoadContent` -Methode:</span><span class="sxs-lookup"><span data-stu-id="210de-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="210de-110">Laden einer einzelnen Szene</span><span class="sxs-lookup"><span data-stu-id="210de-110">Single scene loading</span></span>

<span data-ttu-id="210de-111">Die Entsprechung einer einzelnen Szenenlast kann über das optionale Argument erreicht `mode` werden.</span><span class="sxs-lookup"><span data-stu-id="210de-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="210de-112">`LoadSceneMode.Single` entlädt zunächst alle geladenen Inhaltsszenen, bevor mit dem Laden fortgefahren wird.</span><span class="sxs-lookup"><span data-stu-id="210de-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// ContentScene1, ContentScene2 and ContentScene3 will be loaded additively
await sceneSystem.LoadContent("ContentScene1");
await sceneSystem.LoadContent("ContentScene2");
await sceneSystem.LoadContent("ContentScene3");

// ContentScene1, ContentScene2 and ContentScene3 will be unloaded
// SingleContentScene will be loaded additively
await sceneSystem.LoadContent("SingleContentScene", LoadSceneMode.Single);
```

## <a name="next--previous-scene-loading"></a><span data-ttu-id="210de-113">Laden der nächsten/vorherigen Szene</span><span class="sxs-lookup"><span data-stu-id="210de-113">Next / previous scene loading</span></span>

<span data-ttu-id="210de-114">Inhalte können in der Reihenfolge des Buildindexes singly geladen werden.</span><span class="sxs-lookup"><span data-stu-id="210de-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="210de-115">Dies ist nützlich, um Anwendungen zu präsentieren, die Benutzer einzeln durch eine Reihe von Demoszenen führen.</span><span class="sxs-lookup"><span data-stu-id="210de-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![Aktuelle Szenen im Build in player-Einstellungen](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="210de-117">Beachten Sie, dass beim Laden von next/prev-Inhalten standardmäßig LoadSceneMode.Single verwendet wird, um sicherzustellen, dass der vorherige Inhalt entladen wird.</span><span class="sxs-lookup"><span data-stu-id="210de-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested && sceneSystem.NextContentExists)
{
    await sceneSystem.LoadNextContent();
}

if (prevSceneRequested && sceneSystem.PrevContentExists)
{
    await sceneSystem.LoadPrevContent();
}
```

<span data-ttu-id="210de-118">`PrevContentExists` gibt TRUE zurück, wenn mindestens eine Inhaltsszene mit einem niedrigeren Buildindex als der niedrigste derzeit geladene Buildindex vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="210de-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="210de-119">`NextContentExists` gibt TRUE zurück, wenn mindestens eine Inhaltsszene einen höheren Buildindex als der höchste aktuell geladene Buildindex auf hat.</span><span class="sxs-lookup"><span data-stu-id="210de-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="210de-120">Wenn das `wrap` Argument true ist, führt der Inhalt eine Schleife zurück zum ersten/letzten Buildindex.</span><span class="sxs-lookup"><span data-stu-id="210de-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="210de-121">Dadurch entgeht die Notwendigkeit, nach dem nächsten bzw. vorherigen Inhalt zu suchen:</span><span class="sxs-lookup"><span data-stu-id="210de-121">This removes the need to check for next / previous content:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested)
{
    await sceneSystem.LoadNextContent(true);
}

if (prevSceneRequested)
{
    await sceneSystem.LoadPrevContent(true);
}
```

## <a name="loading-by-tag"></a><span data-ttu-id="210de-122">Laden nach Tag</span><span class="sxs-lookup"><span data-stu-id="210de-122">Loading by tag</span></span>

![Laden von Inhaltsszenen nach Tag](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="210de-124">Manchmal ist es wünschenswert, Inhaltsszenen in Gruppen zu laden.</span><span class="sxs-lookup"><span data-stu-id="210de-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="210de-125">Beispielsweise kann eine Phase einer Erfahrung aus mehreren Szenen bestehen, die alle gleichzeitig geladen werden müssen, um zu funktionieren.</span><span class="sxs-lookup"><span data-stu-id="210de-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="210de-126">Um dies zu erleichtern, können Sie Ihre Szenen markieren und sie dann laden oder mit diesem Tag entladen.</span><span class="sxs-lookup"><span data-stu-id="210de-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="210de-127">Das Laden nach Tag kann auch nützlich sein, wenn Interpreten Elemente in eine Benutzeroberfläche integrieren/entfernen möchten, ohne Skripts ändern zu müssen.</span><span class="sxs-lookup"><span data-stu-id="210de-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="210de-128">Wenn Sie dieses Skript beispielsweise mit den folgenden beiden Sätzen von Tags ausführen, werden unterschiedliche Ergebnisse erzeugt:</span><span class="sxs-lookup"><span data-stu-id="210de-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="210de-129">Testen von Inhalten</span><span class="sxs-lookup"><span data-stu-id="210de-129">Testing content</span></span>

<span data-ttu-id="210de-130">Szenenname</span><span class="sxs-lookup"><span data-stu-id="210de-130">Scene Name</span></span> | <span data-ttu-id="210de-131">Szenentag</span><span class="sxs-lookup"><span data-stu-id="210de-131">Scene Tag</span></span> | <span data-ttu-id="210de-132">Von Skript geladen</span><span class="sxs-lookup"><span data-stu-id="210de-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="210de-133">Debug DebuginPhysics</span><span class="sxs-lookup"><span data-stu-id="210de-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="210de-134">Gelände</span><span class="sxs-lookup"><span data-stu-id="210de-134">Terrain</span></span> | <span data-ttu-id="210de-135">•</span><span class="sxs-lookup"><span data-stu-id="210de-135">•</span></span>
<span data-ttu-id="210de-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="210de-136">StructureTesting</span></span> | <span data-ttu-id="210de-137">Strukturen</span><span class="sxs-lookup"><span data-stu-id="210de-137">Structures</span></span> | <span data-ttu-id="210de-138">•</span><span class="sxs-lookup"><span data-stu-id="210de-138">•</span></span>
<span data-ttu-id="210de-139">Tools für Diess</span><span class="sxs-lookup"><span data-stu-id="210de-139">VegetationTools</span></span> | <span data-ttu-id="210de-140">Vegetation</span><span class="sxs-lookup"><span data-stu-id="210de-140">Vegetation</span></span> | <span data-ttu-id="210de-141">•</span><span class="sxs-lookup"><span data-stu-id="210de-141">•</span></span>
<span data-ttu-id="210de-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="210de-142">Mountain</span></span> | <span data-ttu-id="210de-143">Gelände</span><span class="sxs-lookup"><span data-stu-id="210de-143">Terrain</span></span> | <span data-ttu-id="210de-144">•</span><span class="sxs-lookup"><span data-stu-id="210de-144">•</span></span>
<span data-ttu-id="210de-145">Cabin</span><span class="sxs-lookup"><span data-stu-id="210de-145">Cabin</span></span> | <span data-ttu-id="210de-146">Strukturen</span><span class="sxs-lookup"><span data-stu-id="210de-146">Structures</span></span> | <span data-ttu-id="210de-147">•</span><span class="sxs-lookup"><span data-stu-id="210de-147">•</span></span>
<span data-ttu-id="210de-148">Strukturen</span><span class="sxs-lookup"><span data-stu-id="210de-148">Trees</span></span> | <span data-ttu-id="210de-149">Vegetation</span><span class="sxs-lookup"><span data-stu-id="210de-149">Vegetation</span></span> | <span data-ttu-id="210de-150">•</span><span class="sxs-lookup"><span data-stu-id="210de-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="210de-151">Endgültiger Inhalt</span><span class="sxs-lookup"><span data-stu-id="210de-151">Final content</span></span>

<span data-ttu-id="210de-152">Szenenname</span><span class="sxs-lookup"><span data-stu-id="210de-152">Scene Name</span></span> | <span data-ttu-id="210de-153">Szenentag</span><span class="sxs-lookup"><span data-stu-id="210de-153">Scene Tag</span></span> | <span data-ttu-id="210de-154">Von Skript geladen</span><span class="sxs-lookup"><span data-stu-id="210de-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="210de-155">Debug DebuginPhysics</span><span class="sxs-lookup"><span data-stu-id="210de-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="210de-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="210de-156">DoNotInclude</span></span> |
<span data-ttu-id="210de-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="210de-157">StructureTesting</span></span> | <span data-ttu-id="210de-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="210de-158">DoNotInclude</span></span> |
<span data-ttu-id="210de-159">Tools für Diess</span><span class="sxs-lookup"><span data-stu-id="210de-159">VegetationTools</span></span> | <span data-ttu-id="210de-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="210de-160">DoNotInclude</span></span> |
<span data-ttu-id="210de-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="210de-161">Mountain</span></span> | <span data-ttu-id="210de-162">Gelände</span><span class="sxs-lookup"><span data-stu-id="210de-162">Terrain</span></span> | <span data-ttu-id="210de-163">•</span><span class="sxs-lookup"><span data-stu-id="210de-163">•</span></span>
<span data-ttu-id="210de-164">Cabin</span><span class="sxs-lookup"><span data-stu-id="210de-164">Cabin</span></span> | <span data-ttu-id="210de-165">Strukturen</span><span class="sxs-lookup"><span data-stu-id="210de-165">Structures</span></span> | <span data-ttu-id="210de-166">•</span><span class="sxs-lookup"><span data-stu-id="210de-166">•</span></span>
<span data-ttu-id="210de-167">Strukturen</span><span class="sxs-lookup"><span data-stu-id="210de-167">Trees</span></span> | <span data-ttu-id="210de-168">Vegetation</span><span class="sxs-lookup"><span data-stu-id="210de-168">Vegetation</span></span> | <span data-ttu-id="210de-169">•</span><span class="sxs-lookup"><span data-stu-id="210de-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="210de-170">Editor-Verhalten</span><span class="sxs-lookup"><span data-stu-id="210de-170">Editor behavior</span></span>

<span data-ttu-id="210de-171">Sie können all diese Vorgänge im Editor und im Wiedergabemodus ausführen, indem Sie den Dienstinspektor des Szenensystems [verwenden.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="210de-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="210de-172">Im Bearbeitungsmodus erfolgt das Laden von Szenen sofort, während Sie im Wiedergabemodus den Ladefortschritt beobachten und [Aktivierungstoken](scene-system-load-progress.md) verwenden können.</span><span class="sxs-lookup"><span data-stu-id="210de-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![Szenensystem im Inspektor mit hervorgehobener Inhaltsladung](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
