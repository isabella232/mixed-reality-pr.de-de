---
title: Inhalte von Mixed Reality-Szenen
description: Dokumentation zur Mixed Reality Scene Content Component
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 9980c01b47c3d7d451fda886b4645664f06f204da9967c186382878be947d64f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193226"
---
# <a name="mixed-reality-scene-content"></a>Inhalte von Mixed Reality-Szenen

Beim Hinzufügen von MRTK zu einer Szene wird ein `MixedRealitySceneContent` Gameobject erstellt. Dieses Objekt dient als dedizierter Ort zum Platzieren und Instanziieren Mixed Reality Inhalts, um sicherzustellen, dass es über viele verschiedene Erfahrungen hinweg angemessen skaliert wird. Das Gameobject verfügt über eine entsprechende MixedRealitySceneContent-Monobehavior-Klasse, die über den **Alignment Type-Parameter konfiguriert werden** kann.  Dieser Parameter kann die folgenden Werte übernehmen.

* *AlignWithExperienceScale:* Richtet den Inhalt  basierend auf  der Zielerfahrungsskala und dem Inhaltsoffset aus, die im Experience-Bereich des [Konfigurationsprofils Einstellungen](experience-settings.md)
* *AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.


  ![Mixed Reality im Editor erstellte Szeneninhaltsobjekt](../images/experience-settings/MixedRealitySceneContent.png)
