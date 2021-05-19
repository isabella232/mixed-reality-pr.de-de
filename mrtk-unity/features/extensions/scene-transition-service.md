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
# <a name="scene-transition-service"></a>Szenenübergangsdienst

Diese Erweiterung vereinfacht das Auskommentieren einer Szene, das Anzeigen einer Statusanzeige, das Laden einer Szene und das anschließende Wiederverenkennen.

Szenenvorgänge werden vom SceneSystem-Dienst gesteuert, aber jeder aufgabenbasierte Vorgang kann verwendet werden, um einen Übergang zu ermöglichen.

## <a name="enabling-the-extension"></a>Aktivieren der Erweiterung

Um die Erweiterung zu aktivieren, öffnen Sie Ihr RegisteredServiceProvider-Profil. Klicken Sie auf Neuen Dienstanbieter registrieren, um eine neue Konfiguration hinzuzufügen. Wählen Sie im Feld Komponententyp die Option SceneTransitionService aus. Wählen Sie im Feld Konfigurationsprofil das standarde Szenenübergangsprofil aus, das in der Erweiterung enthalten ist.

## <a name="profile-options"></a>Profiloptionen

### <a name="use-default-progress-indicator"></a>Standardfortschrittsanzeige verwenden

Wenn diese Überprüfung aktiviert ist, wird das Standard-Statusanzeige-Prefab verwendet, wenn beim Aufruf von Kein Statusindikatorobjekt bereitgestellt wird. Wenn ein Statusindikatorobjekt bereitgestellt wird, wird der Standardwert `DoSceneTransition.` ignoriert.

### <a name="use-fade-color"></a>Verwenden der Ausblenden-Farbe

Wenn diese Überprüfung angezeigt wird, wird vom Übergangsdienst während des Übergangs eine Ausblendung angewendet. Diese Einstellung kann zur Laufzeit über die -Eigenschaft des Diensts geändert `UseFadeColor` werden.

### <a name="fade-color"></a>Farbe ausblenden

Steuert die Farbe des Fade-Effekts. Alpha wird ignoriert. Diese Einstellung kann zur Laufzeit vor einem Übergang über die -Eigenschaft des Diensts geändert `FadeColor` werden.

### <a name="fade-targets"></a>Ausblenden von Zielen

Steuert, welche Kameras einen Einblendeffekt haben, der auf sie angewendet wird. Diese Einstellung kann zur Laufzeit über die -Eigenschaft des Diensts geändert `FadeTargets` werden.

Einstellung | Zielkameras
--- | --- | ---
Main | Wendet den Ausblendeffekt auf die Hauptkamera an.
Benutzeroberfläche | Wendet den Ausblendeffekt auf Kameras auf der Ui-Ebene an. (Wirkt sich nicht auf die Überlagerungsbenutzeroberfläche aus)
Alles | Gilt sowohl für Haupt- als auch für Benutzeroberflächenkameras.
Benutzerdefiniert | Gilt für einen benutzerdefinierten Satz von Kameras, die über bereitgestellt werden. `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>Ausblendzeit/Einblendungszeit

Standardeinstellungen für die Dauer einer Einblendung beim Eingeben/Beenden eines Übergangs. Diese Einstellungen können zur Laufzeit über die Eigenschaften und des Diensts geändert `FadeOutTime` `FadeInTime` werden.

### <a name="camera-fader-type"></a>Kamerafadertyp

Welche `ICameraFader` Klasse zum Anwenden eines Blendeffekts auf Kameras verwendet werden soll. Die `CameraFaderQuad` Standardklasse instanziiert ein Quader mit einem transparenten Material vor der Zielkamera in der Nähe der Clipebene. Ein anderer Ansatz kann die Verwendung eines Posteffektsystems sein.

## <a name="using-the-extension"></a>Verwenden der Erweiterung

Sie verwenden den Übergangsdienst, indem Sie Aufgaben übergeben, die ausgeführt werden, während die Kamera ausgeblendet wird.

### <a name="using-scene-system-tasks"></a>Verwenden von Szenensystemaufgaben

In den meisten Fällen verwenden Sie aufgaben, die vom SceneSystem-Dienst bereitgestellt werden:

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

### <a name="using-custom-tasks"></a>Verwenden von benutzerdefinierten Aufgaben

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

Eine Statusanzeige ist alles, was die -Schnittstelle `IProgressIndicator` implementiert. Dies kann in Form eines Begrüßungsbildschirms, eines 3D-Tagalong-Ladeindikators oder eines anderen Indikators, der Feedback zum Fortschritt des Übergangs liefert, verwendet werden.

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
