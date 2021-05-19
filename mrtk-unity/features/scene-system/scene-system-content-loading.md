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
# <a name="content-scene-loading"></a>Laden von Inhaltsszenen

Alle Inhaltsladevorgänge sind asynchron, und standardmäßig ist das ladende Inhalt additiv. Manager- und Beleuchtungsszenen sind nie von Ladevorgängen für Inhalte betroffen. Informationen zum Überwachen des Ladefortschritts und der Szenenaktivierung finden Sie unter [Überwachen des Ladens von Inhalten.](scene-system-load-progress.md)

## <a name="loading-content"></a>Laden von Inhalt

Verwenden Sie zum Laden von Inhaltsszenen die `LoadContent` -Methode:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>Laden einer einzelnen Szene

Das Äquivalent einer einzelnen Szenenlast kann über das optionale Argument erreicht `mode` werden. `LoadSceneMode.Single` entlädt zunächst alle geladenen Inhaltsszenen, bevor mit dem Laden fortfahren.

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

## <a name="next--previous-scene-loading"></a>Nächstes/vorheriges Laden der Szene

Der Inhalt kann in der Reihenfolge des Buildindexes eningly geladen werden. Dies ist nützlich, um Anwendungen zu präsentieren, die Benutzer 1:1 durch eine Reihe von Demoszenen nehmen.

![Aktuelle Szenen im Build in player-Einstellungen](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

Beachten Sie, dass next/prev content loading standardmäßig LoadSceneMode.Single verwendet, um sicherzustellen, dass der vorherige Inhalt entladen wird.

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

`PrevContentExists` gibt TRUE zurück, wenn mindestens eine Inhaltsszene über einen niedrigeren Buildindex als der niedrigste aktuell geladene Buildindex verfügt. `NextContentExists` gibt TRUE zurück, wenn mindestens eine Inhaltsszene über einen höheren Buildindex als der höchste derzeit geladene Buildindex verfügt.

Wenn das `wrap` Argument true ist, wird der Inhalt zum ersten/letzten Buildindex zurück loopt. Dadurch ist es nicht mehr notwendig, nach dem nächsten bzw. vorherigen Inhalt zu prüfen:

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

## <a name="loading-by-tag"></a>Laden nach Tag

![Laden von Inhaltsszenen nach Tag](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

Manchmal ist es wünschenswert, Inhaltsszenen in Gruppen zu laden. Beispielsweise kann eine Phase einer Erfahrung aus mehreren Szenen bestehen, die alle gleichzeitig geladen werden müssen, um zu funktionieren. Um dies zu ermöglichen, können Sie Ihre Szenen markieren und dann mit diesem Tag laden oder entladen.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

Das Laden nach Tag kann auch nützlich sein, wenn Eindungs- und Entfernungselemente in eine Beerfahrung integriert/entfernt werden sollen, ohne Skripts ändern zu müssen. Wenn Sie dieses Skript beispielsweise mit den folgenden beiden Tags ausführen, werden unterschiedliche Ergebnisse erzeugt:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>Testen von Inhalten

Szenenname | Szenentag | Vom Skript geladen
---|---|---
DebugGenInPhysics | Gelände | •
StructureTesting | Strukturen | •
Tools | Vegetation | •
Mountain | Gelände | •
Cabin | Strukturen | •
Strukturen | Vegetation | •

### <a name="final-content"></a>Endgültiger Inhalt

Szenenname | Szenentag | Von Skript geladen
---|---|---
Debug DebuginPhysics | DoNotInclude |
StructureTesting | DoNotInclude |
Tools für Diess | DoNotInclude |
Mountain | Gelände | •
Cabin | Strukturen | •
Strukturen | Vegetation | •

---

## <a name="editor-behavior"></a>Editor-Verhalten

Sie können all diese Vorgänge im Editor und im Wiedergabemodus ausführen, indem Sie den Dienstinspektor des Szenensystems [verwenden.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) Im Bearbeitungsmodus erfolgt das Laden von Szenen sofort, während Sie im Wiedergabemodus den Ladefortschritt beobachten und [Aktivierungstoken](scene-system-load-progress.md) verwenden können.

![Szenensystem im Inspektor mit hervorgehobener Inhaltsladung](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
