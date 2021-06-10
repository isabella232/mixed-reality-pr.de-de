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
# <a name="mixed-reality-scene-content"></a><span data-ttu-id="f276a-104">Mixed Reality Szeneninhalt</span><span class="sxs-lookup"><span data-stu-id="f276a-104">Mixed Reality Scene Content</span></span>

<span data-ttu-id="f276a-105">Beim Hinzufügen von MRTK zu einer Szene wird ein `MixedRealitySceneContent` Gameobject erstellt.</span><span class="sxs-lookup"><span data-stu-id="f276a-105">When adding MRTK to a scene, a `MixedRealitySceneContent` gameobject is created.</span></span> <span data-ttu-id="f276a-106">Dieses Objekt dient als dedizierter Ort zum Platzieren und Instanziieren Mixed Reality Inhalts, um sicherzustellen, dass es über viele verschiedene Erfahrungen hinweg angemessen skaliert wird.</span><span class="sxs-lookup"><span data-stu-id="f276a-106">This object serves as a dedicated place to place and instantiate Mixed Reality content to ensure that it scales appropriately across many different experiences.</span></span> <span data-ttu-id="f276a-107">Das Gameobject verfügt über eine entsprechende MixedRealitySceneContent-Monobehavior-Klasse, die über den **Alignment Type-Parameter konfiguriert werden** kann. </span><span class="sxs-lookup"><span data-stu-id="f276a-107">The gameobject has an equivalent **MixedRealitySceneContent** monobehavior, which can be configured via the **Alignment Type** parameter.</span></span> <span data-ttu-id="f276a-108">Dieser Parameter kann die folgenden Werte übernehmen.</span><span class="sxs-lookup"><span data-stu-id="f276a-108">This parameter can take on the following values.</span></span>

* <span data-ttu-id="f276a-109">*AlignWithExperienceScale:* Richtet den Inhalt  basierend auf  der Zielerfahrungsskala und dem Inhaltsoffset aus, die in den Einstellungen für die Benutzererfahrung des [Konfigurationsprofils festgelegt sind.](experience-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f276a-109">*AlignWithExperienceScale* - Aligns the content based on the **Target Experience Scale** and **Content Offset** set in the configuration profile's [Experience Settings](experience-settings.md)</span></span>
* <span data-ttu-id="f276a-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span><span class="sxs-lookup"><span data-stu-id="f276a-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span></span>


  ![Mixed Reality im Editor erstellte Szeneninhaltsobjekt](../images/experience-settings/MixedRealitySceneContent.png)