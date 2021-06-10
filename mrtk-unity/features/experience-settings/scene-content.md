---
title: SceneContent
description: Dokumentation zur Mixed Reality Scene Content Component
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: fb4f575b6846695de07decb49146a59d3da843e0
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647854"
---
# <a name="mixed-reality-scene-content"></a>Mixed Reality Szeneninhalt

Beim Hinzufügen von MRTK zu einer Szene wird ein `MixedRealitySceneContent` Gameobject erstellt. Dieses Objekt dient als dedizierter Ort zum Platzieren und Instanziieren Mixed Reality Inhalts, um sicherzustellen, dass es über viele verschiedene Erfahrungen hinweg angemessen skaliert wird. Das Gameobject verfügt über eine entsprechende MixedRealitySceneContent-Monobehavior-Klasse, die über den **Alignment Type-Parameter konfiguriert werden** kann.  Dieser Parameter kann die folgenden Werte übernehmen.

* *AlignWithExperienceScale:* Richtet den Inhalt  basierend auf  der Zielerfahrungsskala und dem Inhaltsoffset aus, die in den Einstellungen für die Benutzererfahrung des [Konfigurationsprofils festgelegt sind.](experience-settings.md)
* *AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.


  ![Mixed Reality im Editor erstellte Szeneninhaltsobjekt](../images/experience-settings/MixedRealitySceneContent.png)