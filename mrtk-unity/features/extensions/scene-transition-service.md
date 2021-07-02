---
title: Szenenübergangsdienst
description: Dokumentation zum Szenenübergang in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, SceneTransition,
ms.openlocfilehash: b645012a055f693fdac794b79e24fd20154fdb65
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176208"
---
# <a name="scene-transition-service"></a>Szenenübergangsdienst

Diese Erweiterung vereinfacht das Auskommentieren einer Szene, das Anzeigen einer Statusanzeige, das Laden einer Szene und das anschließende Wiederverenkennen.

Szenenvorgänge werden vom SceneSystem-Dienst gesteuert, aber jeder aufgabenbasierte Vorgang kann verwendet werden, um einen Übergang zu ermöglichen.

## <a name="enabling-the-extension"></a>Aktivieren der Erweiterung

Um die Erweiterung zu aktivieren, öffnen Sie Ihr RegisteredServiceProvider-Profil. Klicken Sie auf Neuen Dienstanbieter registrieren, um eine neue Konfiguration hinzuzufügen. Wählen Sie im Feld Komponententyp die Option SceneTransitionService aus. Wählen Sie im Feld Konfigurationsprofil das standarde Szenenübergangsprofil aus, das in der Erweiterung enthalten ist.

## <a name="profile-options"></a>Profiloptionen

### <a name="use-default-progress-indicator"></a>Standardfortschrittsanzeige verwenden

Wenn diese Aktiviert ist, wird das Standard-Statusanzeige-Prefab verwendet, wenn beim Aufrufen von Kein Statusindikatorobjekt bereitgestellt wird. Wenn ein Statusindikatorobjekt bereitgestellt wird, wird der Standardwert `DoSceneTransition.` ignoriert.

### <a name="use-fade-color"></a>Verwenden der Farbe "Ausblenden"

Wenn diese Überprüfung angezeigt wird, wird vom Übergangsdienst während des Übergangs eine Ausblendung angewendet. Diese Einstellung kann zur Laufzeit über die -Eigenschaft des Diensts geändert `UseFadeColor` werden.

### <a name="fade-color"></a>Farbe ausblenden

Steuert die Farbe des Fade-Effekts. Alpha wird ignoriert. Diese Einstellung kann zur Laufzeit vor einem Übergang über die -Eigenschaft des Diensts geändert `FadeColor` werden.

### <a name="fade-targets"></a>Ausblenden von Zielen

Steuert, auf welche Kameras ein Fadeneffekt angewendet wird. Diese Einstellung kann zur Laufzeit über die -Eigenschaft des Diensts geändert `FadeTargets` werden.

Einstellung | Zielkameras
--- | --- | ---
Main | Wendet den Fade-Effekt auf die Hauptkamera an.
Benutzeroberfläche | Wendet einen Fadeneffekt auf Kameras auf der Benutzeroberflächenebene an. (Wirkt sich nicht auf die Überlagerungsbenutzeroberfläche aus))
Alle | Gilt sowohl für Hauptkameras als auch für Benutzeroberflächenkameras.
Benutzerdefiniert | Gilt für einen benutzerdefinierten Satz von Kameras, die über bereitgestellt werden. `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>Ausblendzeit/Zeit einblenden

Standardeinstellungen für die Dauer einer Ausblendung beim Eingeben/Beenden eines Übergangs. Diese Einstellungen können zur Laufzeit über die Eigenschaften und des Diensts `FadeOutTime` `FadeInTime` geändert werden.

### <a name="camera-fader-type"></a>Kamerablendertyp

Welche `ICameraFader` Klasse zum Anwenden eines Fadeneffekts auf Kameras verwendet werden soll. Die Standardklasse instanziiert ein Quader mit einem transparenten Material vor der Zielkamera in der Nähe `CameraFaderQuad` der Clipebene. Ein anderer Ansatz könnte die Verwendung eines Post-Effects-Systems sein.

## <a name="using-the-extension"></a>Verwenden der Erweiterung

Sie verwenden den Übergangsdienst, indem Sie Aufgaben übergeben, die ausgeführt werden, während die Kamera ausgeblendet ist.

### <a name="using-scene-system-tasks"></a>Verwenden von Szenensystemaufgaben

In den meisten Fällen verwenden Sie vom SceneSystem-Dienst bereitgestellte Aufgaben:

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

### <a name="using-custom-tasks"></a>Verwenden benutzerdefinierter Aufgaben

In anderen Fällen möchten Sie möglicherweise einen Übergang durchführen, ohne tatsächlich eine Szene zu laden:

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

Oder Sie möchten eine Szene laden, ohne den SceneSystem-Dienst zu verwenden:

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

### <a name="using-multiple-tasks"></a>Verwenden mehrerer Aufgaben

Sie können auch mehrere Aufgaben zur Verfügung haben, die in der reihenfolgengeordneten Ausführung ausgeführt werden:

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

## <a name="using-the-progress-indicator"></a>Verwenden der Statusanzeige

Eine Statusanzeige ist alles, was die -Schnittstelle `IProgressIndicator` implementiert. Dies kann in Form eines Begrüßungsbildschirms, eines 3D-Tagalong-Ladeindikators oder eines anderen Indikators, der Feedback zum Übergangsfortschritt liefert, verwendet werden.

Wenn im SceneTransitionService-Profil überprüft wird, wird eine Statusanzeige `UseDefaultProgressIndicator` instanziiert, wenn ein Übergang beginnt. Für die Dauer des Übergangs können auf die Eigenschaften und dieses Indikators über die Methoden und des `Progress` `Message` Diensts `SetProgressValue` zugegriffen `SetProgressMessage` werden.

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

Alternativ können Sie beim Aufrufen `DoSceneTransition` von ihre eigene Statusanzeige über das optionale Argument `progressIndicator` angeben. Dadurch wird die Standardfortschrittsanzeige überschrieben.
