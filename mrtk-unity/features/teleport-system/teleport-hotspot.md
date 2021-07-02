---
title: Teleport-Hotspot
description: Dokumentation zur Teleport Hotspot-Komponente in MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Teleport-System, Teleport-Hotspot
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 01ae900800c4a13ca7bafc3391ff51b752a95ae0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176206"
---
# <a name="teleport-hotspot"></a><span data-ttu-id="118ed-104">Teleport-Hotspot</span><span class="sxs-lookup"><span data-stu-id="118ed-104">Teleport hotspot</span></span>

<span data-ttu-id="118ed-105">Der Teleport-Hotspot ist eine Komponente, die Sie Ihrem Gameobject hinzufügen können, um sicherzustellen, dass sich der Benutzer an einer bestimmten Position und Ausrichtung befindet, wenn er an diesen Standort teleportieren kann.</span><span class="sxs-lookup"><span data-stu-id="118ed-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="118ed-106">Verwendung</span><span class="sxs-lookup"><span data-stu-id="118ed-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="118ed-107">Erstellen eines Teleport-Hotspots</span><span class="sxs-lookup"><span data-stu-id="118ed-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="118ed-108">Um einen Teleport-Hotspot zu erstellen, fügen Sie die TeleportHotspot-Komponente einem Objekt hinzu, das auch über eine Colliderkomponente verfügt.</span><span class="sxs-lookup"><span data-stu-id="118ed-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Teleport Hotspot-Komponente](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="118ed-110">Jetzt ändert sich die Farbe des Teleportzeigers, wenn er über einen TeleportHotspot geleitet wird.</span><span class="sxs-lookup"><span data-stu-id="118ed-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="118ed-111">Wenn die Teleportaktion über den Hotspot abgeschlossen ist, wird der Benutzer zum Mittelpunkt des TeleportHotspots teleportiert.</span><span class="sxs-lookup"><span data-stu-id="118ed-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="118ed-112">Wenn das Flag für die Überschreibungsausrichtung deaktiviert ist, wird die Ausrichtung des Benutzers mit der Ausrichtung des Teleport-Hotspots übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="118ed-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Beispiel für Teleport-Hotspot](../images/teleport/TeleportHotspotExample.gif)
