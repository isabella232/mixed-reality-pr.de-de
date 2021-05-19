---
title: 'Szenensystem: Laden von Inhalt'
description: Dokumentation zum Laden des Szenensystems mit MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: f310b3687a6773404c7a998a3764163daf159857
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145142"
---
# <a name="content-scene-loading"></a><span data-ttu-id="09645-104">Laden von Inhaltsszenen</span><span class="sxs-lookup"><span data-stu-id="09645-104">Content scene loading</span></span>

<span data-ttu-id="09645-105">Alle Inhaltsladevorgänge sind asynchron, und standardmäßig ist das ladende Inhalt additiv.</span><span class="sxs-lookup"><span data-stu-id="09645-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="09645-106">Manager- und Beleuchtungsszenen sind nie von Ladevorgängen für Inhalte betroffen.</span><span class="sxs-lookup"><span data-stu-id="09645-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="09645-107">Informationen zum Überwachen des Ladefortschritts und der Szenenaktivierung finden Sie unter [Überwachen des Ladens von Inhalten.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="09645-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="09645-108">Laden von Inhalt</span><span class="sxs-lookup"><span data-stu-id="09645-108">Loading content</span></span>

<span data-ttu-id="09645-109">Verwenden Sie zum Laden von Inhaltsszenen die `LoadContent` -Methode:</span><span class="sxs-lookup"><span data-stu-id="09645-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="09645-110">Laden einer einzelnen Szene</span><span class="sxs-lookup"><span data-stu-id="09645-110">Single scene loading</span></span>

<span data-ttu-id="09645-111">Das Äquivalent einer einzelnen Szenenlast kann über das optionale Argument erreicht `mode` werden.</span><span class="sxs-lookup"><span data-stu-id="09645-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="09645-112">`LoadSceneMode.Single` entlädt zunächst alle geladenen Inhaltsszenen, bevor mit dem Laden fortfahren.</span><span class="sxs-lookup"><span data-stu-id="09645-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

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

## <a name="next--previous-scene-loading"></a><span data-ttu-id="09645-113">Nächstes/vorheriges Laden der Szene</span><span class="sxs-lookup"><span data-stu-id="09645-113">Next / previous scene loading</span></span>

<span data-ttu-id="09645-114">Der Inhalt kann in der Reihenfolge des Buildindexes eningly geladen werden.</span><span class="sxs-lookup"><span data-stu-id="09645-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="09645-115">Dies ist nützlich, um Anwendungen zu präsentieren, die Benutzer 1:1 durch eine Reihe von Demoszenen nehmen.</span><span class="sxs-lookup"><span data-stu-id="09645-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![Aktuelle Szenen im Build in player-Einstellungen](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="09645-117">Beachten Sie, dass next/prev content loading standardmäßig LoadSceneMode.Single verwendet, um sicherzustellen, dass der vorherige Inhalt entladen wird.</span><span class="sxs-lookup"><span data-stu-id="09645-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

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

<span data-ttu-id="09645-118">`PrevContentExists` gibt TRUE zurück, wenn mindestens eine Inhaltsszene über einen niedrigeren Buildindex als der niedrigste aktuell geladene Buildindex verfügt.</span><span class="sxs-lookup"><span data-stu-id="09645-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="09645-119">`NextContentExists` gibt TRUE zurück, wenn mindestens eine Inhaltsszene über einen höheren Buildindex als der höchste derzeit geladene Buildindex verfügt.</span><span class="sxs-lookup"><span data-stu-id="09645-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="09645-120">Wenn das `wrap` Argument true ist, wird der Inhalt zum ersten/letzten Buildindex zurück loopt.</span><span class="sxs-lookup"><span data-stu-id="09645-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="09645-121">Dadurch ist es nicht mehr notwendig, nach dem nächsten bzw. vorherigen Inhalt zu prüfen:</span><span class="sxs-lookup"><span data-stu-id="09645-121">This removes the need to check for next / previous content:</span></span>

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

## <a name="loading-by-tag"></a><span data-ttu-id="09645-122">Laden nach Tag</span><span class="sxs-lookup"><span data-stu-id="09645-122">Loading by tag</span></span>

![Laden von Inhaltsszenen nach Tag](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="09645-124">Manchmal ist es wünschenswert, Inhaltsszenen in Gruppen zu laden.</span><span class="sxs-lookup"><span data-stu-id="09645-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="09645-125">Beispielsweise kann eine Phase einer Erfahrung aus mehreren Szenen bestehen, die alle gleichzeitig geladen werden müssen, um zu funktionieren.</span><span class="sxs-lookup"><span data-stu-id="09645-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="09645-126">Um dies zu ermöglichen, können Sie Ihre Szenen markieren und dann mit diesem Tag laden oder entladen.</span><span class="sxs-lookup"><span data-stu-id="09645-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="09645-127">Das Laden nach Tag kann auch nützlich sein, wenn Eindungs- und Entfernungselemente in eine Beerfahrung integriert/entfernt werden sollen, ohne Skripts ändern zu müssen.</span><span class="sxs-lookup"><span data-stu-id="09645-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="09645-128">Wenn Sie dieses Skript beispielsweise mit den folgenden beiden Tags ausführen, werden unterschiedliche Ergebnisse erzeugt:</span><span class="sxs-lookup"><span data-stu-id="09645-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="09645-129">Testen von Inhalten</span><span class="sxs-lookup"><span data-stu-id="09645-129">Testing content</span></span>

<span data-ttu-id="09645-130">Szenenname</span><span class="sxs-lookup"><span data-stu-id="09645-130">Scene Name</span></span> | <span data-ttu-id="09645-131">Szenentag</span><span class="sxs-lookup"><span data-stu-id="09645-131">Scene Tag</span></span> | <span data-ttu-id="09645-132">Vom Skript geladen</span><span class="sxs-lookup"><span data-stu-id="09645-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="09645-133">DebugGenInPhysics</span><span class="sxs-lookup"><span data-stu-id="09645-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="09645-134">Gelände</span><span class="sxs-lookup"><span data-stu-id="09645-134">Terrain</span></span> | <span data-ttu-id="09645-135">•</span><span class="sxs-lookup"><span data-stu-id="09645-135">•</span></span>
<span data-ttu-id="09645-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="09645-136">StructureTesting</span></span> | <span data-ttu-id="09645-137">Strukturen</span><span class="sxs-lookup"><span data-stu-id="09645-137">Structures</span></span> | <span data-ttu-id="09645-138">•</span><span class="sxs-lookup"><span data-stu-id="09645-138">•</span></span>
<span data-ttu-id="09645-139">Tools</span><span class="sxs-lookup"><span data-stu-id="09645-139">VegetationTools</span></span> | <span data-ttu-id="09645-140">Vegetation</span><span class="sxs-lookup"><span data-stu-id="09645-140">Vegetation</span></span> | <span data-ttu-id="09645-141">•</span><span class="sxs-lookup"><span data-stu-id="09645-141">•</span></span>
<span data-ttu-id="09645-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="09645-142">Mountain</span></span> | <span data-ttu-id="09645-143">Gelände</span><span class="sxs-lookup"><span data-stu-id="09645-143">Terrain</span></span> | <span data-ttu-id="09645-144">•</span><span class="sxs-lookup"><span data-stu-id="09645-144">•</span></span>
<span data-ttu-id="09645-145">Cabin</span><span class="sxs-lookup"><span data-stu-id="09645-145">Cabin</span></span> | <span data-ttu-id="09645-146">Strukturen</span><span class="sxs-lookup"><span data-stu-id="09645-146">Structures</span></span> | <span data-ttu-id="09645-147">•</span><span class="sxs-lookup"><span data-stu-id="09645-147">•</span></span>
<span data-ttu-id="09645-148">Strukturen</span><span class="sxs-lookup"><span data-stu-id="09645-148">Trees</span></span> | <span data-ttu-id="09645-149">Vegetation</span><span class="sxs-lookup"><span data-stu-id="09645-149">Vegetation</span></span> | <span data-ttu-id="09645-150">•</span><span class="sxs-lookup"><span data-stu-id="09645-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="09645-151">Endgültiger Inhalt</span><span class="sxs-lookup"><span data-stu-id="09645-151">Final content</span></span>

<span data-ttu-id="09645-152">Szenenname</span><span class="sxs-lookup"><span data-stu-id="09645-152">Scene Name</span></span> | <span data-ttu-id="09645-153">Szenentag</span><span class="sxs-lookup"><span data-stu-id="09645-153">Scene Tag</span></span> | <span data-ttu-id="09645-154">Von Skript geladen</span><span class="sxs-lookup"><span data-stu-id="09645-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="09645-155">Debug DebuginPhysics</span><span class="sxs-lookup"><span data-stu-id="09645-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="09645-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="09645-156">DoNotInclude</span></span> |
<span data-ttu-id="09645-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="09645-157">StructureTesting</span></span> | <span data-ttu-id="09645-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="09645-158">DoNotInclude</span></span> |
<span data-ttu-id="09645-159">Tools für Diess</span><span class="sxs-lookup"><span data-stu-id="09645-159">VegetationTools</span></span> | <span data-ttu-id="09645-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="09645-160">DoNotInclude</span></span> |
<span data-ttu-id="09645-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="09645-161">Mountain</span></span> | <span data-ttu-id="09645-162">Gelände</span><span class="sxs-lookup"><span data-stu-id="09645-162">Terrain</span></span> | <span data-ttu-id="09645-163">•</span><span class="sxs-lookup"><span data-stu-id="09645-163">•</span></span>
<span data-ttu-id="09645-164">Cabin</span><span class="sxs-lookup"><span data-stu-id="09645-164">Cabin</span></span> | <span data-ttu-id="09645-165">Strukturen</span><span class="sxs-lookup"><span data-stu-id="09645-165">Structures</span></span> | <span data-ttu-id="09645-166">•</span><span class="sxs-lookup"><span data-stu-id="09645-166">•</span></span>
<span data-ttu-id="09645-167">Strukturen</span><span class="sxs-lookup"><span data-stu-id="09645-167">Trees</span></span> | <span data-ttu-id="09645-168">Vegetation</span><span class="sxs-lookup"><span data-stu-id="09645-168">Vegetation</span></span> | <span data-ttu-id="09645-169">•</span><span class="sxs-lookup"><span data-stu-id="09645-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="09645-170">Editor-Verhalten</span><span class="sxs-lookup"><span data-stu-id="09645-170">Editor behavior</span></span>

<span data-ttu-id="09645-171">Sie können all diese Vorgänge im Editor und im Wiedergabemodus ausführen, indem Sie den Dienstinspektor des Szenensystems [verwenden.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="09645-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="09645-172">Im Bearbeitungsmodus erfolgt das Laden von Szenen sofort, während Sie im Wiedergabemodus den Ladefortschritt beobachten und [Aktivierungstoken](scene-system-load-progress.md) verwenden können.</span><span class="sxs-lookup"><span data-stu-id="09645-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![Szenensystem im Inspektor mit hervorgehobener Inhaltsladung](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
