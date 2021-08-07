---
title: 'Szenensystem: Ladestatus'
description: Dokumentation zum Laden von Inhalten von Szenen in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 1d2382e11092b20aca5bf8480ade521ffb94a70a325540e70487d7f581e8cf15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186616"
---
# <a name="monitoring-content-loading"></a>Überwachen des Ladens von Inhalten

## <a name="scene-operation-progress"></a>Status des Szenenvorgangs

Wenn Inhalt geladen oder entladen wird, gibt die `SceneOperationInProgress` Eigenschaft TRUE zurück. Sie können den Fortschritt dieses Vorgangs über die `SceneOperationProgress` -Eigenschaft überwachen.

Der `SceneOperationProgress` Wert ist der Durchschnitt aller aktuellen asynchronen Szenenvorgänge. Am Anfang eines Inhaltsladevorgangs `SceneOperationProgress` ist 0 (null). Nach abschluss des Vorgangs `SceneOperationProgress` wird auf 1 festgelegt und bleibt bei 1, bis der nächste Vorgang ausgeführt wird. Beachten Sie, dass diese Eigenschaften nur von Inhaltsszenenvorgängen beeinflusst werden.

Diese Eigenschaften spiegeln den Zustand eines *gesamten Vorgangs* von Anfang bis Ende wider, auch wenn dieser Vorgang mehrere Schritte umfasst:

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

### <a name="progress-examples"></a>Fortschrittsbeispiele

`SceneOperationInProgress` kann nützlich sein, wenn die Aktivität angehalten werden soll, während Inhalt geladen wird:

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

`SceneOperationProgress` kann verwendet werden, um Statusdialogfelder anzuzeigen:

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

## <a name="monitoring-with-actions"></a>Überwachen mit Aktionen

Das Szenensystem bietet mehrere Aktionen, mit denen Sie informiert werden, wenn Szenen geladen oder entladen werden. Jede Aktion leitet den Namen der betroffenen Szene weiter.

Wenn ein Lade- oder Entladevorgang mehrere Szenen umfasst, werden die relevanten Aktionen einmal pro betroffener Szene aufgerufen. Sie werden auch alle gleichzeitig aufgerufen, wenn der Lade- oder Entladevorgang *vollständig abgeschlossen ist.* Aus diesem Grund wird empfohlen, *OnWillUnload-Aktionen* zu verwenden, um Inhalte zu erkennen, die zerstört *werden,* anstatt *OnUnloaded-Aktionen* zu verwenden, um zerstörte Inhalte nach dem Fakt zu erkennen.

Da *OnLoaded-Aktionen* nur aufgerufen werden, wenn alle Szenen aktiviert und vollständig geladen werden, ist die Verwendung von *OnLoaded-Aktionen* zum Erkennen und Verwenden neuer Inhalte garantiert sicher.

Action | Beim Aufruf | Inhaltsszenen | Beleuchtungsszenen | Manager-Szenen
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | Unmittelbar vor dem Laden einer Inhaltsszene | • | |  
`OnContentLoaded` | Nachdem alle Inhaltsszenen in einem Ladevorgang vollständig geladen und aktiviert wurden | • | |
`OnWillUnloadContent` | Unmittelbar vor dem Entladen einer Inhaltsszene | • | |
`OnContentUnloaded` | Nachdem alle Inhaltsszenen in einem Entladevorgang vollständig entladen wurden | • | |
`OnWillLoadLighting` | Unmittelbar vor dem Laden einer Beleuchtungsszene | | • |
`OnLightingLoaded` | Nachdem eine Beleuchtungsszene vollständig geladen und aktiviert wurde| | • |
`OnWillUnloadLighting` | Unmittelbar vor dem Entladen einer Beleuchtungsszene | | • |
`OnLightingUnloaded` | Nach dem vollständigen Entladen einer Beleuchtungsszene | | • |
`OnWillLoadScene` | Unmittelbar vor dem Laden einer Szene | • | • | •
`OnSceneLoaded` | Nachdem alle Szenen in einem Vorgang vollständig geladen und aktiviert wurden | • | • | •
`OnWillUnloadScene` | Unmittelbar vor dem Entladen einer Szene | • | • | •
`OnSceneUnloaded` | Nach dem vollständigen Entladen einer Szene |  • | • | •

### <a name="action-examples"></a>Aktionsbeispiele

Ein weiteres Fortschrittsdialogbeispiel mit Aktionen und einer Coroutine anstelle von Update:

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

## <a name="controlling-scene-activation"></a>Steuern der Szenenaktivierung

Inhaltsszenen werden standardmäßig so festgelegt, dass sie beim Laden aktiviert werden. Wenn Sie die Szenenaktivierung manuell steuern möchten, können Sie eine `SceneActivationToken` an eine beliebige Methode zum Laden von Inhalten übergeben. Wenn mehrere Inhaltsszenen von einem einzelnen Vorgang geladen werden, gilt dieses Aktivierungstoken für alle Szenen.

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

## <a name="checking-which-content-is-loaded"></a>Überprüfen des geladenen Inhalts

Die `ContentSceneNames` -Eigenschaft stellt ein Array verfügbarer Inhaltsszenen in der Reihenfolge des Buildindexes bereit. Sie können überprüfen, ob diese Szenen über geladen `IsContentLoaded(string contentName)` werden.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
