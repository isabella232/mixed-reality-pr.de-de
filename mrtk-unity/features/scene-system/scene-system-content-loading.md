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
# <a name="scene-system-content-loading"></a>Laden von Szenensysteminhalten

Alle Inhaltsladevorgänge sind asynchron, und standardmäßig ist das laden von Inhalten additiv. Manager- und Beleuchtungsszenen sind nie von Inhaltsladevorgängen betroffen. Informationen zum Überwachen des Ladefortschritts und zur Szenenaktivierung finden Sie unter [Überwachen des Ladens von Inhalten.](scene-system-load-progress.md)

## <a name="loading-content"></a>Laden von Inhalten

Verwenden Sie zum Laden von Inhaltsszenen die `LoadContent` -Methode:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>Laden einer einzelnen Szene

Die Entsprechung einer einzelnen Szenenlast kann über das optionale Argument erreicht `mode` werden. `LoadSceneMode.Single` entlädt zunächst alle geladenen Inhaltsszenen, bevor mit dem Laden fortgefahren wird.

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

## <a name="next--previous-scene-loading"></a>Laden der nächsten/vorherigen Szene

Inhalte können in der Reihenfolge des Buildindexes singly geladen werden. Dies ist nützlich, um Anwendungen zu präsentieren, die Benutzer einzeln durch eine Reihe von Demoszenen führen.

![Aktuelle Szenen im Build in player-Einstellungen](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

Beachten Sie, dass beim Laden von next/prev-Inhalten standardmäßig LoadSceneMode.Single verwendet wird, um sicherzustellen, dass der vorherige Inhalt entladen wird.

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

`PrevContentExists` gibt TRUE zurück, wenn mindestens eine Inhaltsszene mit einem niedrigeren Buildindex als der niedrigste derzeit geladene Buildindex vorhanden ist. `NextContentExists` gibt TRUE zurück, wenn mindestens eine Inhaltsszene einen höheren Buildindex als der höchste aktuell geladene Buildindex auf hat.

Wenn das `wrap` Argument true ist, führt der Inhalt eine Schleife zurück zum ersten/letzten Buildindex. Dadurch entgeht die Notwendigkeit, nach dem nächsten bzw. vorherigen Inhalt zu suchen:

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

Manchmal ist es wünschenswert, Inhaltsszenen in Gruppen zu laden. Beispielsweise kann eine Phase einer Erfahrung aus mehreren Szenen bestehen, die alle gleichzeitig geladen werden müssen, um zu funktionieren. Um dies zu erleichtern, können Sie Ihre Szenen markieren und sie dann laden oder mit diesem Tag entladen.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

Das Laden nach Tag kann auch nützlich sein, wenn Interpreten Elemente in eine Benutzeroberfläche integrieren/entfernen möchten, ohne Skripts ändern zu müssen. Wenn Sie dieses Skript beispielsweise mit den folgenden beiden Sätzen von Tags ausführen, werden unterschiedliche Ergebnisse erzeugt:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>Testen von Inhalten

Szenenname | Szenentag | Von Skript geladen
---|---|---
Debug DebuginPhysics | Gelände | •
StructureTesting | Strukturen | •
Tools für Diess | Vegetation | •
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
