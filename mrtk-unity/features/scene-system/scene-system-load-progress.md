---
title: 'Szenensystem: Ladestatus'
description: Dokumentation zum Laden von Inhalten von Szenen im MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 51b5d4d00d65491a0476068bbdc256ffce67412b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144403"
---
# <a name="monitoring-content-loading"></a><span data-ttu-id="c11f0-104">Überwachen des Ladens von Inhalten</span><span class="sxs-lookup"><span data-stu-id="c11f0-104">Monitoring content loading</span></span>

## <a name="scene-operation-progress"></a><span data-ttu-id="c11f0-105">Status des Szenenvorgangs</span><span class="sxs-lookup"><span data-stu-id="c11f0-105">Scene operation progress</span></span>

<span data-ttu-id="c11f0-106">Wenn Inhalt geladen oder entladen wird, gibt die `SceneOperationInProgress` Eigenschaft TRUE zurück.</span><span class="sxs-lookup"><span data-stu-id="c11f0-106">When content is being loaded or unloaded, the `SceneOperationInProgress` property will return true.</span></span> <span data-ttu-id="c11f0-107">Sie können den Fortschritt dieses Vorgangs über die `SceneOperationProgress` -Eigenschaft überwachen.</span><span class="sxs-lookup"><span data-stu-id="c11f0-107">You can monitor the progress of this operation via the `SceneOperationProgress` property.</span></span>

<span data-ttu-id="c11f0-108">Der `SceneOperationProgress` Wert ist der Durchschnitt aller aktuellen asynchronen Szenenvorgänge.</span><span class="sxs-lookup"><span data-stu-id="c11f0-108">The `SceneOperationProgress` value is the average of all current async scene operations.</span></span> <span data-ttu-id="c11f0-109">Am Anfang eines Inhaltsladevorgangs `SceneOperationProgress` ist 0 (null).</span><span class="sxs-lookup"><span data-stu-id="c11f0-109">At the start of a content load, `SceneOperationProgress` will be zero.</span></span> <span data-ttu-id="c11f0-110">Nach abschluss des Vorgangs `SceneOperationProgress` wird auf 1 festgelegt und bleibt bei 1, bis der nächste Vorgang ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c11f0-110">Once fully completed, `SceneOperationProgress` will be set to 1 and will remain at 1 until the next operation takes place.</span></span> <span data-ttu-id="c11f0-111">Beachten Sie, dass sich nur Vorgänge in der Inhaltsszene auf diese Eigenschaften auswirken.</span><span class="sxs-lookup"><span data-stu-id="c11f0-111">Note that only content scene operations affect these properties.</span></span>

<span data-ttu-id="c11f0-112">Diese Eigenschaften spiegeln den Zustand eines *gesamten Vorgangs* von Anfang bis Ende wider, auch wenn dieser Vorgang mehrere Schritte umfasst:</span><span class="sxs-lookup"><span data-stu-id="c11f0-112">These properties reflect the state of an *entire operation* from start to finish, even if that operation includes multiple steps:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// First do an additive scene load
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
await sceneSystem.LoadContent("ContentScene1");

// Now do a single scene load
// This will result in two actions back-to-back
// First "ContentScene1" will be unloaded
// Then "ContentScene2" will be loaded
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
sceneSystem.LoadContent("ContentScene2", LoadSceneMode.Single)
```

### <a name="progress-examples"></a><span data-ttu-id="c11f0-113">Fortschrittsbeispiele</span><span class="sxs-lookup"><span data-stu-id="c11f0-113">Progress examples</span></span>

<span data-ttu-id="c11f0-114">`SceneOperationInProgress` kann nützlich sein, wenn die Aktivität angehalten werden soll, während Inhalt geladen wird:</span><span class="sxs-lookup"><span data-stu-id="c11f0-114">`SceneOperationInProgress` can be useful if activity should be suspended while content is being loaded:</span></span>

```c#
public class FooManager : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        // Don't update foos while a scene operation is in progress
        if (sceneSystem.SceneOperationInProgress)
        {
            return;
        }

        // Update foos
        ...
    }
    ...
}
```

<span data-ttu-id="c11f0-115">`SceneOperationProgress` kann verwendet werden, um Statusdialogfelder anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="c11f0-115">`SceneOperationProgress` can be used to display progress dialogs:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        if (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
        }
        else
        {
            HideProgressIndicator();
        }
    }
    ...
}
```

---

## <a name="monitoring-with-actions"></a><span data-ttu-id="c11f0-116">Überwachen mit Aktionen</span><span class="sxs-lookup"><span data-stu-id="c11f0-116">Monitoring with actions</span></span>

<span data-ttu-id="c11f0-117">Das Szenensystem bietet mehrere Aktionen, mit denen Sie informiert werden, wenn Szenen geladen oder entladen werden.</span><span class="sxs-lookup"><span data-stu-id="c11f0-117">The Scene System provides several actions to let you know when scenes are being loaded or unloaded.</span></span> <span data-ttu-id="c11f0-118">Jede Aktion leitet den Namen der betroffenen Szene weiter.</span><span class="sxs-lookup"><span data-stu-id="c11f0-118">Each action relays the name of the affected scene.</span></span>

<span data-ttu-id="c11f0-119">Wenn ein Lade- oder Entladevorgang mehrere Szenen umfasst, werden die relevanten Aktionen einmal pro betroffener Szene aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="c11f0-119">If a load or unload operation involves multiple scenes, the relevant actions will be invoked once per affected scene.</span></span> <span data-ttu-id="c11f0-120">Sie werden auch alle gleichzeitig aufgerufen, wenn der Lade- oder Entladevorgang *vollständig abgeschlossen ist.*</span><span class="sxs-lookup"><span data-stu-id="c11f0-120">They are also invoked all at once when the load or unload operation is *fully completed.*</span></span> <span data-ttu-id="c11f0-121">Aus diesem Grund wird empfohlen, *OnWillUnload-Aktionen* zu verwenden, um Inhalte zu erkennen, die zerstört *werden,* anstatt *OnUnloaded-Aktionen* zu verwenden, um zerstörte Inhalte nach dem Fakt zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="c11f0-121">For this reason it's recommended that you use *OnWillUnload* actions to detect content that *will* be destroyed, as opposed to using *OnUnloaded* actions to detect destroyed content after the fact.</span></span>

<span data-ttu-id="c11f0-122">Auf der Kehrseite, da *OnLoaded-Aktionen* nur aufgerufen werden, wenn alle Szenen aktiviert und vollständig geladen werden, ist die Verwendung von *OnLoaded-Aktionen* zum Erkennen und Verwenden neuer Inhalte garantiert sicher.</span><span class="sxs-lookup"><span data-stu-id="c11f0-122">On the flip side, because *OnLoaded* actions are only invoked when all scenes are activated and fully loaded, using *OnLoaded* actions to detect and use new content is guaranteed to be safe.</span></span>

<span data-ttu-id="c11f0-123">Aktion</span><span class="sxs-lookup"><span data-stu-id="c11f0-123">Action</span></span> | <span data-ttu-id="c11f0-124">Wenn sie aufgerufen wird</span><span class="sxs-lookup"><span data-stu-id="c11f0-124">When it's invoked</span></span> | <span data-ttu-id="c11f0-125">Inhaltsszenen</span><span class="sxs-lookup"><span data-stu-id="c11f0-125">Content Scenes</span></span> | <span data-ttu-id="c11f0-126">Beleuchtungsszenen</span><span class="sxs-lookup"><span data-stu-id="c11f0-126">Lighting Scenes</span></span> | <span data-ttu-id="c11f0-127">Manager-Szenen</span><span class="sxs-lookup"><span data-stu-id="c11f0-127">Manager Scenes</span></span>
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | <span data-ttu-id="c11f0-128">Direkt vor dem Laden einer Inhaltsszene</span><span class="sxs-lookup"><span data-stu-id="c11f0-128">Just prior to a content scene load</span></span> | <span data-ttu-id="c11f0-129">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-129">•</span></span> | |  
`OnContentLoaded` | <span data-ttu-id="c11f0-130">Nachdem alle Inhaltsszenen in einem Ladevorgang vollständig geladen und aktiviert wurden</span><span class="sxs-lookup"><span data-stu-id="c11f0-130">After all content scenes in a load operation have been fully loaded and activated</span></span> | <span data-ttu-id="c11f0-131">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-131">•</span></span> | |
`OnWillUnloadContent` | <span data-ttu-id="c11f0-132">Direkt vor einem Vorgang zum Entladen einer Inhaltsszene</span><span class="sxs-lookup"><span data-stu-id="c11f0-132">Just prior to a content scene unload operation</span></span> | <span data-ttu-id="c11f0-133">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-133">•</span></span> | |
`OnContentUnloaded` | <span data-ttu-id="c11f0-134">Nachdem alle Inhaltsszenen in einem Entladevorgang vollständig entladen wurden</span><span class="sxs-lookup"><span data-stu-id="c11f0-134">After all content scenes in an unload operation have been fully unloaded</span></span> | <span data-ttu-id="c11f0-135">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-135">•</span></span> | |
`OnWillLoadLighting` | <span data-ttu-id="c11f0-136">Direkt vor dem Laden einer Beleuchtungsszene</span><span class="sxs-lookup"><span data-stu-id="c11f0-136">Just prior to a lighting scene load</span></span> | | <span data-ttu-id="c11f0-137">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-137">•</span></span> |
`OnLightingLoaded` | <span data-ttu-id="c11f0-138">Nachdem eine Beleuchtungsszene vollständig geladen und aktiviert wurde</span><span class="sxs-lookup"><span data-stu-id="c11f0-138">After a lighting scene has been fully loaded and activated</span></span>| | <span data-ttu-id="c11f0-139">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-139">•</span></span> |
`OnWillUnloadLighting` | <span data-ttu-id="c11f0-140">Direkt vor dem Entladen einer Beleuchtungsszene</span><span class="sxs-lookup"><span data-stu-id="c11f0-140">Just prior to a lighting scene unload</span></span> | | <span data-ttu-id="c11f0-141">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-141">•</span></span> |
`OnLightingUnloaded` | <span data-ttu-id="c11f0-142">Nachdem eine Beleuchtungsszene vollständig entladen wurde</span><span class="sxs-lookup"><span data-stu-id="c11f0-142">After a lighting scene has been fully unloaded</span></span> | | <span data-ttu-id="c11f0-143">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-143">•</span></span> |
`OnWillLoadScene` | <span data-ttu-id="c11f0-144">Direkt vor dem Laden einer Szene</span><span class="sxs-lookup"><span data-stu-id="c11f0-144">Just prior to a scene load</span></span> | <span data-ttu-id="c11f0-145">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-145">•</span></span> | <span data-ttu-id="c11f0-146">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-146">•</span></span> | <span data-ttu-id="c11f0-147">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-147">•</span></span>
`OnSceneLoaded` | <span data-ttu-id="c11f0-148">Nachdem alle Szenen in einem Vorgang vollständig geladen und aktiviert wurden</span><span class="sxs-lookup"><span data-stu-id="c11f0-148">After all scenes in an operation are fully loaded and activated</span></span> | <span data-ttu-id="c11f0-149">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-149">•</span></span> | <span data-ttu-id="c11f0-150">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-150">•</span></span> | <span data-ttu-id="c11f0-151">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-151">•</span></span>
`OnWillUnloadScene` | <span data-ttu-id="c11f0-152">Direkt vor dem Entladen einer Szene</span><span class="sxs-lookup"><span data-stu-id="c11f0-152">Just prior to a scene unload</span></span> | <span data-ttu-id="c11f0-153">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-153">•</span></span> | <span data-ttu-id="c11f0-154">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-154">•</span></span> | <span data-ttu-id="c11f0-155">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-155">•</span></span>
`OnSceneUnloaded` | <span data-ttu-id="c11f0-156">Nach dem vollständigen Entladen einer Szene</span><span class="sxs-lookup"><span data-stu-id="c11f0-156">After a scene is fully unloaded</span></span> |  <span data-ttu-id="c11f0-157">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-157">•</span></span> | <span data-ttu-id="c11f0-158">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-158">•</span></span> | <span data-ttu-id="c11f0-159">•</span><span class="sxs-lookup"><span data-stu-id="c11f0-159">•</span></span>

### <a name="action-examples"></a><span data-ttu-id="c11f0-160">Aktionsbeispiele</span><span class="sxs-lookup"><span data-stu-id="c11f0-160">Action examples</span></span>

<span data-ttu-id="c11f0-161">Ein weiteres Statusdialogfeldbeispiel mit Aktionen und einer Coroutine anstelle von Update:</span><span class="sxs-lookup"><span data-stu-id="c11f0-161">Another progress dialog example using actions and a coroutine instead of Update:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private bool displayingProgress = false;

    private void Start()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
        sceneSystem.OnWillLoadContent += HandleSceneOperation;
        sceneSystem.OnWillUnloadContent += HandleSceneOperation;
    }

    private void HandleSceneOperation (string sceneName)
    {
        // This may be invoked multiple times per frame - once per scene being loaded or unloaded.
        // So filter the events appropriately.
        if (displayingProgress)
        {
            return;
        }

        displayingProgress = true;
        StartCoroutine(DisplayProgress());
    }

    private IEnumerator DisplayProgress()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        while (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
            yield return null;
        }

        HideProgressIndicator();
        displayingProgress = false;
    }

    ...
}
```

---

## <a name="controlling-scene-activation"></a><span data-ttu-id="c11f0-162">Steuern der Szenenaktivierung</span><span class="sxs-lookup"><span data-stu-id="c11f0-162">Controlling scene activation</span></span>

<span data-ttu-id="c11f0-163">Inhaltsszenen sind standardmäßig so festgelegt, dass sie beim Laden aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="c11f0-163">By default content scenes are set to activate when loaded.</span></span> <span data-ttu-id="c11f0-164">Wenn Sie die Szenenaktivierung manuell steuern möchten, können Sie eine `SceneActivationToken` an eine beliebige Methode zum Laden von Inhalten übergeben.</span><span class="sxs-lookup"><span data-stu-id="c11f0-164">If you want to control scene activation manually, you can pass a `SceneActivationToken` to any content load method.</span></span> <span data-ttu-id="c11f0-165">Wenn mehrere Inhaltsszenen von einem einzelnen Vorgang geladen werden, gilt dieses Aktivierungstoken für alle Szenen.</span><span class="sxs-lookup"><span data-stu-id="c11f0-165">If multiple content scenes are being loaded by a single operation, this activation token will apply to all scenes.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

SceneActivationToken activationToken = new SceneActivationToken();

// Load the content and pass the activation token
sceneSystem.LoadContent(new string[] { "ContentScene1", "ContentScene2", "ContentScene3" }, LoadSceneMode.Additive, activationToken);

// Wait until all users have joined the experience
while (!AllUsersHaveJoinedExperience())
{
    await Task.Yield();
}

// Let scene system know we're ready to activate all scenes
activationToken.AllowSceneActivation = true;

// Wait for all scenes to be fully loaded and activated
while (sceneSystem.SceneOperationInProgress)
{
    await Task.Yield();
}

// Proceed with experience
```

---

## <a name="checking-which-content-is-loaded"></a><span data-ttu-id="c11f0-166">Überprüfen des geladenen Inhalts</span><span class="sxs-lookup"><span data-stu-id="c11f0-166">Checking which content is loaded</span></span>

<span data-ttu-id="c11f0-167">Die `ContentSceneNames` -Eigenschaft stellt ein Array verfügbarer Inhaltsszenen in der Reihenfolge des Buildindexes bereit.</span><span class="sxs-lookup"><span data-stu-id="c11f0-167">The `ContentSceneNames` property provides an array of available content scenes in order of build index.</span></span> <span data-ttu-id="c11f0-168">Sie können überprüfen, ob diese Szenen über geladen `IsContentLoaded(string contentName)` werden.</span><span class="sxs-lookup"><span data-stu-id="c11f0-168">You can check whether these scenes are loaded via `IsContentLoaded(string contentName)`.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
