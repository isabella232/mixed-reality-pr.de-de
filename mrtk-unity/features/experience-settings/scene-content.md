---
title: Mixed Reality von Szeneninhalten
description: Dokumentation zur Mixed Reality Scene Content Component
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 7ed81352537bec799721b49c4e2d3d55066c5316
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177346"
---
# <a name="mixed-reality-scene-content"></a>Mixed Reality von Szeneninhalten

Beim Hinzufügen von MRTK zu einer Szene wird ein `MixedRealitySceneContent` Gameobject erstellt. Dieses Objekt dient als dedizierter Ort zum Platzieren und Instanziieren Mixed Reality Inhalts, um sicherzustellen, dass es über viele verschiedene Erfahrungen hinweg angemessen skaliert wird. Das Gameobject verfügt über eine entsprechende MixedRealitySceneContent-Monobehavior-Klasse, die über den **Alignment Type-Parameter konfiguriert werden** kann.  Dieser Parameter kann die folgenden Werte übernehmen.

* *AlignWithExperienceScale:* Richtet den Inhalt  basierend auf  der Zielerfahrungsskala und dem Inhaltsoffset aus, die im Experience-Bereich des [Konfigurationsprofils Einstellungen](experience-settings.md)
* *AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.


  ![Mixed Reality im Editor erstellte Szeneninhaltsobjekt](../images/experience-settings/MixedRealitySceneContent.png)
