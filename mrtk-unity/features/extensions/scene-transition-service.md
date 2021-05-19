---
title: Übersicht über den Scene Transition Service
description: Dokumentation zum Szenenübergang in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, SceneTransition,
ms.openlocfilehash: 5ea76b572b3cddc097e8266d3c31f152b63a13aa
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144287"
---
# <a name="scene-transition-service"></a><span data-ttu-id="b7e46-104">Szenenübergangsdienst</span><span class="sxs-lookup"><span data-stu-id="b7e46-104">Scene transition service</span></span>

<span data-ttu-id="b7e46-105">Diese Erweiterung vereinfacht das Auskommentieren einer Szene, das Anzeigen einer Statusanzeige, das Laden einer Szene und das anschließende Wiederverenkennen.</span><span class="sxs-lookup"><span data-stu-id="b7e46-105">This extension simplifies the business of fading out a scene, displaying a progress indicator, loading a scene, then fading back in.</span></span>

<span data-ttu-id="b7e46-106">Szenenvorgänge werden vom SceneSystem-Dienst gesteuert, aber jeder aufgabenbasierte Vorgang kann verwendet werden, um einen Übergang zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="b7e46-106">Scene operations are driven by the SceneSystem service, but any Task-based operation can be used to drive a transition.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="b7e46-107">Aktivieren der Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e46-107">Enabling the extension</span></span>

<span data-ttu-id="b7e46-108">Um die Erweiterung zu aktivieren, öffnen Sie Ihr RegisteredServiceProvider-Profil.</span><span class="sxs-lookup"><span data-stu-id="b7e46-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="b7e46-109">Klicken Sie auf Neuen Dienstanbieter registrieren, um eine neue Konfiguration hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7e46-109">Click Register a new Service Provider to add a new configuration.</span></span> <span data-ttu-id="b7e46-110">Wählen Sie im Feld Komponententyp die Option SceneTransitionService aus.</span><span class="sxs-lookup"><span data-stu-id="b7e46-110">In the Component Type field, select SceneTransitionService.</span></span> <span data-ttu-id="b7e46-111">Wählen Sie im Feld Konfigurationsprofil das standarde Szenenübergangsprofil aus, das in der Erweiterung enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="b7e46-111">In the Configuration Profile field, select the default scene transition profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="b7e46-112">Profiloptionen</span><span class="sxs-lookup"><span data-stu-id="b7e46-112">Profile options</span></span>

### <a name="use-default-progress-indicator"></a><span data-ttu-id="b7e46-113">Standardfortschrittsanzeige verwenden</span><span class="sxs-lookup"><span data-stu-id="b7e46-113">Use default progress indicator</span></span>

<span data-ttu-id="b7e46-114">Wenn diese Überprüfung aktiviert ist, wird das Standard-Statusanzeige-Prefab verwendet, wenn beim Aufruf von Kein Statusindikatorobjekt bereitgestellt wird. Wenn ein Statusindikatorobjekt bereitgestellt wird, wird der Standardwert `DoSceneTransition.` ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b7e46-114">If checked, the default progress indicator prefab will be used when no progress indicator object is provided when calling `DoSceneTransition.` If a progress indicator object is provided, the default will be ignored.</span></span>

### <a name="use-fade-color"></a><span data-ttu-id="b7e46-115">Verwenden der Ausblenden-Farbe</span><span class="sxs-lookup"><span data-stu-id="b7e46-115">Use fade color</span></span>

<span data-ttu-id="b7e46-116">Wenn diese Überprüfung angezeigt wird, wird vom Übergangsdienst während des Übergangs eine Ausblendung angewendet.</span><span class="sxs-lookup"><span data-stu-id="b7e46-116">If checked, the transition service will apply a fade during your transition.</span></span> <span data-ttu-id="b7e46-117">Diese Einstellung kann zur Laufzeit über die -Eigenschaft des Diensts geändert `UseFadeColor` werden.</span><span class="sxs-lookup"><span data-stu-id="b7e46-117">This setting can be changed at runtime via the service's `UseFadeColor` property.</span></span>

### <a name="fade-color"></a><span data-ttu-id="b7e46-118">Farbe ausblenden</span><span class="sxs-lookup"><span data-stu-id="b7e46-118">Fade color</span></span>

<span data-ttu-id="b7e46-119">Steuert die Farbe des Fade-Effekts.</span><span class="sxs-lookup"><span data-stu-id="b7e46-119">Controls the color of the fade effect.</span></span> <span data-ttu-id="b7e46-120">Alpha wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b7e46-120">Alpha is ignored.</span></span> <span data-ttu-id="b7e46-121">Diese Einstellung kann zur Laufzeit vor einem Übergang über die -Eigenschaft des Diensts geändert `FadeColor` werden.</span><span class="sxs-lookup"><span data-stu-id="b7e46-121">This setting can be changed at runtime prior to a transition via the service's `FadeColor` property.</span></span>

### <a name="fade-targets"></a><span data-ttu-id="b7e46-122">Ausblenden von Zielen</span><span class="sxs-lookup"><span data-stu-id="b7e46-122">Fade targets</span></span>

<span data-ttu-id="b7e46-123">Steuert, welche Kameras einen Einblendeffekt haben, der auf sie angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="b7e46-123">Controls which cameras will have a fade effect applied to them.</span></span> <span data-ttu-id="b7e46-124">Diese Einstellung kann zur Laufzeit über die -Eigenschaft des Diensts geändert `FadeTargets` werden.</span><span class="sxs-lookup"><span data-stu-id="b7e46-124">This setting can be changed at runtime via the service's `FadeTargets` property.</span></span>

<span data-ttu-id="b7e46-125">Einstellung</span><span class="sxs-lookup"><span data-stu-id="b7e46-125">Setting</span></span> | <span data-ttu-id="b7e46-126">Zielkameras</span><span class="sxs-lookup"><span data-stu-id="b7e46-126">Targeted Cameras</span></span>
--- | --- | ---
<span data-ttu-id="b7e46-127">Main</span><span class="sxs-lookup"><span data-stu-id="b7e46-127">Main</span></span> | <span data-ttu-id="b7e46-128">Wendet den Ausblendeffekt auf die Hauptkamera an.</span><span class="sxs-lookup"><span data-stu-id="b7e46-128">Applies fade effect to the main camera.</span></span>
<span data-ttu-id="b7e46-129">Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="b7e46-129">UI</span></span> | <span data-ttu-id="b7e46-130">Wendet den Ausblendeffekt auf Kameras auf der Ui-Ebene an.</span><span class="sxs-lookup"><span data-stu-id="b7e46-130">Applies fade effect to cameras on the UI layer.</span></span> <span data-ttu-id="b7e46-131">(Wirkt sich nicht auf die Überlagerungsbenutzeroberfläche aus)</span><span class="sxs-lookup"><span data-stu-id="b7e46-131">(Does not affect overlay UI)</span></span>
<span data-ttu-id="b7e46-132">Alles</span><span class="sxs-lookup"><span data-stu-id="b7e46-132">All</span></span> | <span data-ttu-id="b7e46-133">Gilt sowohl für Haupt- als auch für Benutzeroberflächenkameras.</span><span class="sxs-lookup"><span data-stu-id="b7e46-133">Applies to both main and UI cameras.</span></span>
<span data-ttu-id="b7e46-134">Benutzerdefiniert</span><span class="sxs-lookup"><span data-stu-id="b7e46-134">Custom</span></span> | <span data-ttu-id="b7e46-135">Gilt für einen benutzerdefinierten Satz von Kameras, die über bereitgestellt werden. `SetCustomFadeTargetCameras`</span><span class="sxs-lookup"><span data-stu-id="b7e46-135">Applies to a custom set of cameras provided via `SetCustomFadeTargetCameras`</span></span>

### <a name="fade-out-time--fade-in-time"></a><span data-ttu-id="b7e46-136">Ausblendzeit/Einblendungszeit</span><span class="sxs-lookup"><span data-stu-id="b7e46-136">Fade out time / fade in time</span></span>

<span data-ttu-id="b7e46-137">Standardeinstellungen für die Dauer einer Einblendung beim Eingeben/Beenden eines Übergangs.</span><span class="sxs-lookup"><span data-stu-id="b7e46-137">Default settings for the duration of a fade on entering / exiting a transition.</span></span> <span data-ttu-id="b7e46-138">Diese Einstellungen können zur Laufzeit über die Eigenschaften und des Diensts geändert `FadeOutTime` `FadeInTime` werden.</span><span class="sxs-lookup"><span data-stu-id="b7e46-138">These settings can be changed at runtime via the service's `FadeOutTime` and `FadeInTime` properties.</span></span>

### <a name="camera-fader-type"></a><span data-ttu-id="b7e46-139">Kamerafadertyp</span><span class="sxs-lookup"><span data-stu-id="b7e46-139">Camera fader type</span></span>

<span data-ttu-id="b7e46-140">Welche `ICameraFader` Klasse zum Anwenden eines Blendeffekts auf Kameras verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b7e46-140">Which `ICameraFader` class to use for applying a fade effect to cameras.</span></span> <span data-ttu-id="b7e46-141">Die `CameraFaderQuad` Standardklasse instanziiert ein Quader mit einem transparenten Material vor der Zielkamera in der Nähe der Clipebene.</span><span class="sxs-lookup"><span data-stu-id="b7e46-141">The default `CameraFaderQuad` class instantiates a quad with a transparent material in front of the target camera close to the clip plane.</span></span> <span data-ttu-id="b7e46-142">Ein anderer Ansatz kann die Verwendung eines Posteffektsystems sein.</span><span class="sxs-lookup"><span data-stu-id="b7e46-142">Another approach might be to use a post effects system.</span></span>

## <a name="using-the-extension"></a><span data-ttu-id="b7e46-143">Verwenden der Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e46-143">Using the extension</span></span>

<span data-ttu-id="b7e46-144">Sie verwenden den Übergangsdienst, indem Sie Aufgaben übergeben, die ausgeführt werden, während die Kamera ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="b7e46-144">You use the transition service by passing Tasks that are run while the camera is faded out.</span></span>

### <a name="using-scene-system-tasks"></a><span data-ttu-id="b7e46-145">Verwenden von Szenensystemaufgaben</span><span class="sxs-lookup"><span data-stu-id="b7e46-145">Using scene system tasks</span></span>

<span data-ttu-id="b7e46-146">In den meisten Fällen verwenden Sie aufgaben, die vom SceneSystem-Dienst bereitgestellt werden:</span><span class="sxs-lookup"><span data-stu-id="b7e46-146">In most cases you will be using Tasks supplied by the SceneSystem service:</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Runs LoadContent task
    // Fades back in
    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}
```

### <a name="using-custom-tasks"></a><span data-ttu-id="b7e46-147">Verwenden von benutzerdefinierten Aufgaben</span><span class="sxs-lookup"><span data-stu-id="b7e46-147">Using custom tasks</span></span>

<span data-ttu-id="b7e46-148">In anderen Fällen möchten Sie möglicherweise einen Übergang durchführen, ohne tatsächlich eine Szene zu laden:</span><span class="sxs-lookup"><span data-stu-id="b7e46-148">In other cases you may want to perform a transition without actually loading a scene:</span></span>

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Resets scene
    // Fades back in
    await transition.DoSceneTransition(
            () => ResetScene()
        );
}

private async Task ResetScene()
{
    // Go through all enemies in the current scene and move them back to starting positions
}
```

<span data-ttu-id="b7e46-149">Oder Sie möchten eine Szene laden, ohne den SceneSystem-Dienst zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="b7e46-149">Or you may want to load a scene without using the SceneSystem service:</span></span>

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Loads scene using Unity's scene manager
    // Fades back in
    await transition.DoSceneTransition(
            () => LoadScene("TestScene1")
        );
}

private async Task LoadScene(string sceneName)
{
    AsyncOperation asyncOp = SceneManager.LoadSceneAsync(sceneName, LoadSceneMode.Additive);
    while (!asyncOp.isDone)
    {
        await Task.Yield();
    }
}
```

### <a name="using-multiple-tasks"></a><span data-ttu-id="b7e46-150">Verwenden mehrerer Aufgaben</span><span class="sxs-lookup"><span data-stu-id="b7e46-150">Using multiple tasks</span></span>

<span data-ttu-id="b7e46-151">Sie können auch mehrere Aufgaben zur Verfügung haben, die in der reihenfolgengeordneten Ausführung ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="b7e46-151">You can also supply multiple tasks, which will be executed in order:</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Sets time scale to 0
    // Fades out audio to 0
    // Loads TestScene1
    // Fades in audio to 1
    // Sets time scale to 1
    // Fades back in
    await transition.DoSceneTransition(
            () => SetTimescale(0f),
            () => FadeAudio(0f, 1f),
            () => sceneSystem.LoadContent("TestScene1"),
            () => FadeAudio(1f, 1f),
            () => SetTimescale(1f)
        );
}

private async Task SetTimescale(float targetTime)
{
    Time.timeScale = targetTime;
    await Task.Yield();
}

private async Task FadeAudio(float targetVolume, float duration)
{
    float startTime = Time.realtimeSinceStartup;
    float startVolume = AudioListener.volume;
    while (Time.realtimeSinceStartup < startTime + duration)
    {
        AudioListener.volume = Mathf.Lerp(startVolume, targetVolume, Time.realtimeSinceStartup - startTime / duration);
        await Task.Yield();
       }
       AudioListener.volume = targetVolume;
}
```

## <a name="using-the-progress-indicator"></a><span data-ttu-id="b7e46-152">Verwenden der Statusanzeige</span><span class="sxs-lookup"><span data-stu-id="b7e46-152">Using the progress indicator</span></span>

<span data-ttu-id="b7e46-153">Eine Statusanzeige ist alles, was die -Schnittstelle `IProgressIndicator` implementiert.</span><span class="sxs-lookup"><span data-stu-id="b7e46-153">A progress indicator is anything that implements the `IProgressIndicator` interface.</span></span> <span data-ttu-id="b7e46-154">Dies kann in Form eines Begrüßungsbildschirms, eines 3D-Tagalong-Ladeindikators oder eines anderen Indikators, der Feedback zum Fortschritt des Übergangs liefert, verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b7e46-154">This can take the form of a splash screen, a 3D tagalong loading indicator, or anything else that provides feedback about transition progress.</span></span>

<span data-ttu-id="b7e46-155">Wenn im SceneTransitionService-Profil überprüft wird, wird eine Statusanzeige `UseDefaultProgressIndicator` instanziiert, wenn ein Übergang beginnt.</span><span class="sxs-lookup"><span data-stu-id="b7e46-155">If `UseDefaultProgressIndicator` is checked in the SceneTransitionService profile, a progress indicator will be instantiated when a transition begins.</span></span> <span data-ttu-id="b7e46-156">Für die Dauer des Übergangs können auf die Eigenschaften und dieses Indikators über die Methoden und des `Progress` `Message` Diensts `SetProgressValue` zugegriffen `SetProgressMessage` werden.</span><span class="sxs-lookup"><span data-stu-id="b7e46-156">For the duration of the transition this indicator's `Progress` and `Message` properties can be accessed via that service's `SetProgressValue` and `SetProgressMessage` methods.</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    ListenToSceneTransition(sceneSystem, transition);

    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}

private async void ListenToSceneTransition(IMixedRealitySceneSystem sceneSystem, ISceneTransitionService transition)
{
    transition.SetProgressMessage("Starting transition...");

    while (transition.TransitionInProgress)
    {
        if (sceneSystem.SceneOperationInProgress)
        {
            transition.SetProgressMessage("Loading scene...");
            transition.SetProgressValue(sceneSystem.SceneOperationProgress);
        }
        else
        {
            transition.SetProgressMessage("Finished loading scene...");
            transition.SetProgressValue(1);
        }

        await Task.Yield();
    }
}
```

<span data-ttu-id="b7e46-157">Alternativ können Sie beim Aufrufen `DoSceneTransition` von ihre eigene Statusanzeige über das optionale Argument `progressIndicator` angeben.</span><span class="sxs-lookup"><span data-stu-id="b7e46-157">Alternatively, when calling `DoSceneTransition` you can supply your own progress indicator via the optional `progressIndicator` argument.</span></span> <span data-ttu-id="b7e46-158">Dadurch wird die Standardfortschrittsanzeige überschrieben.</span><span class="sxs-lookup"><span data-stu-id="b7e46-158">This will override the default progress indicator.</span></span>
