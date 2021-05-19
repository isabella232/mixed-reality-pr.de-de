---
title: Teleport-Hotspot
description: Dokumentation zur Teleport Hotspot-Komponente in MRTK
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Teleport-System, Teleport-Hotspot
ms.openlocfilehash: 0cbdad3c038d457109077b742d3f453d63436ae4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144430"
---
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="5e27d-104">Teleport-Hotspot [Experimentell]</span><span class="sxs-lookup"><span data-stu-id="5e27d-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="5e27d-105">Der Teleport-Hotspot ist eine Komponente, die Sie Ihrem Gameobject hinzufügen können, um sicherzustellen, dass sich der Benutzer an einer bestimmten Position und Ausrichtung befindet, wenn er an diesen Ort teleportieren soll.</span><span class="sxs-lookup"><span data-stu-id="5e27d-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="5e27d-106">Verwendung</span><span class="sxs-lookup"><span data-stu-id="5e27d-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="5e27d-107">Erstellen eines Teleport-Hotspots</span><span class="sxs-lookup"><span data-stu-id="5e27d-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="5e27d-108">Um einen Teleport-Hotspot zu erstellen, fügen Sie die TeleportHotspot-Komponente einem Objekt hinzu, das ebenfalls über eine Colliderkomponente verfügt.</span><span class="sxs-lookup"><span data-stu-id="5e27d-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Teleport Hotspot-Komponente](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="5e27d-110">Nun ändert sich die Farbe des Teleportzeigers, wenn er über einen TeleportHotspot geleitet wird.</span><span class="sxs-lookup"><span data-stu-id="5e27d-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="5e27d-111">Wenn die Teleportaktion über den Hotspot abgeschlossen ist, wird der Benutzer zum Mittelpunkt des TeleportHotspots teleportieren.</span><span class="sxs-lookup"><span data-stu-id="5e27d-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="5e27d-112">Wenn das Flag für die Außerkraftsetzungsausrichtung deaktiviert ist, entspricht die Ausrichtung des Benutzers der Ausrichtung des Teleport-Hotspots.</span><span class="sxs-lookup"><span data-stu-id="5e27d-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Beispiel für Teleport-Hotspot](../images/teleport/TeleportHotspotExample.gif)
