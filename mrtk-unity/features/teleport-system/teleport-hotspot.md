---
title: Teleport-Hotspot
description: Dokumentation zur Teleport Hotspot-Komponente in MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Teleport-System, Teleport-Hotspot
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 2d6160570b43ca931d46f4ec04c604b53b18d731
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647040"
---
# <a name="teleport-hotspot"></a><span data-ttu-id="2e41d-104">Teleport-Hotspot</span><span class="sxs-lookup"><span data-stu-id="2e41d-104">Teleport Hotspot</span></span>

<span data-ttu-id="2e41d-105">Der Teleport-Hotspot ist eine Komponente, die Sie Ihrem Gameobject hinzufügen können, um sicherzustellen, dass sich der Benutzer an einer bestimmten Position und Ausrichtung befindet, wenn er sich an diesen Ort teleportieren lässt.</span><span class="sxs-lookup"><span data-stu-id="2e41d-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="2e41d-106">Verwendung</span><span class="sxs-lookup"><span data-stu-id="2e41d-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="2e41d-107">Erstellen eines Teleport-Hotspots</span><span class="sxs-lookup"><span data-stu-id="2e41d-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="2e41d-108">Um einen Teleport-Hotspot zu erstellen, fügen Sie die TeleportHotspot-Komponente einem Objekt hinzu, das ebenfalls über eine Colliderkomponente verfügt.</span><span class="sxs-lookup"><span data-stu-id="2e41d-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Teleport Hotspot-Komponente](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="2e41d-110">Nun ändert sich die Farbe des Teleportzeigers, wenn er über einen TeleportHotspot geleitet wird.</span><span class="sxs-lookup"><span data-stu-id="2e41d-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="2e41d-111">Wenn die Teleportaktion über den Hotspot abgeschlossen ist, wird der Benutzer zum Mittelpunkt des TeleportHotspots teleportieren.</span><span class="sxs-lookup"><span data-stu-id="2e41d-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="2e41d-112">Wenn das Flag für die Außerkraftsetzungsausrichtung deaktiviert ist, entspricht die Ausrichtung des Benutzers der Ausrichtung des Teleport-Hotspots.</span><span class="sxs-lookup"><span data-stu-id="2e41d-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Beispiel für Teleport-Hotspot](../images/teleport/TeleportHotspotExample.gif)
