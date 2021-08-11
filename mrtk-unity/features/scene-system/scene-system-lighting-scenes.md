---
title: 'Szenensystem: Beleuchtung von Szenen'
description: Dokumentation zur Beleuchtung in der Szene.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 407813f52044d3405e5045f64817d87c4f3e4b59ddfd87308586ac2d81924674
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202568"
---
# <a name="lighting-scene-operations"></a>Beleuchtungsszenenvorgänge

Die in Ihrem Profil definierte Standardbeleuchtungsszene wird beim Start geladen. Diese Beleuchtungsszene bleibt geladen, bis `SetLightingScene` aufgerufen wird.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>Lichteinstellungsübergänge

`transitionType` steuert den Stil des Übergangs zur neuen Beleuchtungsszene.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

Die verfügbaren Stile sind:

Typ | BESCHREIBUNG | Duration
--- | --- | ---
Keine | Vorherige Beleuchtungsszene wird entladen, neue Beleuchtungsszene wird geladen. Kein Übergang. | Wird ignoriert.
FadeToBlack | Die vorherige Beleuchtungsszene wird in Schwarz ausgeblendet. Neue Beleuchtungsszene wird geladen und dann von Schwarz ausgeblendet. Nützlich für reibungslose Übergänge zwischen Standorten. | Verwendet
Überblenden | Die vorherige Beleuchtungsszene wird ausgeblendet, wenn eine neue Beleuchtungsszene einblendet. Nützlich für reibungslose Übergänge zwischen Beleuchtungssetups am gleichen Standort. | Verwendet

Beachten Sie, dass einige Beleuchtungseinstellungen während Übergängen nicht interpoliert werden können. Wenn Sie einen reibungslosen visuellen Übergang wünschen, müssen diese Einstellungen zwischen den Beleuchtungsszenen konsistent bleiben.

Einstellung | Smooth FadeToBlack-Übergang | Smooth CrossFade Transition
--- | --- | ---
Skybox | Nein | Nein
Benutzerdefinierte Reflektionen | Nein | Nein
Sonnenlicht– Echtzeitschatten | Ja | Nein
