---
title: Teleporthotspot
description: Dokumentation zur teleporthotspot-Komponente in mrtk
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity, hololens, hololens 2, gemischte Realität, Entwicklung, mrtk, teleportsystem, Teleport-Hotspot
ms.openlocfilehash: 986105dd771c38b1e26fd9f86df90224110591a4
ms.sourcegitcommit: 4be6f36df9063ccfdce2662e299accc7406b6779
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/25/2021
ms.locfileid: "105582962"
---
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="17953-104">Teleport-Hotspot [experimentell]</span><span class="sxs-lookup"><span data-stu-id="17953-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="17953-105">Der Teleport-Hotspot ist eine Komponente, die Sie Ihrem gameobject hinzufügen können, um sicherzustellen, dass sich der Benutzer an einer bestimmten Position und Ausrichtung befindet, wenn er an diesen Speicherort teleportieren soll.</span><span class="sxs-lookup"><span data-stu-id="17953-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="17953-106">Verwendung</span><span class="sxs-lookup"><span data-stu-id="17953-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="17953-107">Erstellen eines Teleport-Hotspots</span><span class="sxs-lookup"><span data-stu-id="17953-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="17953-108">Um einen Teleport-Hotspot zu erstellen, fügen Sie die teleporthotspot-Komponente einem Objekt hinzu, das auch über eine Collider-Komponente verfügt.</span><span class="sxs-lookup"><span data-stu-id="17953-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![Teleport-Hotspot-Komponente](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="17953-110">Nun ändert sich der Indikator des Teleport-Zeigers, wenn er über einen teleporthotspot geleitet wird.</span><span class="sxs-lookup"><span data-stu-id="17953-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="17953-111">Wenn die teleportaktion über den Hotspot abgeschlossen ist, wird der Benutzer in den Mittelpunkt des teleporthotspot-Vorgangs übertragen.</span><span class="sxs-lookup"><span data-stu-id="17953-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="17953-112">Wenn das Flag zur Überschreibungs Ausrichtung deaktiviert ist, entspricht die Ausrichtung des Benutzers dem des Teleport-Hotspots.</span><span class="sxs-lookup"><span data-stu-id="17953-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![Beispiel für teleporthotspot](../images/teleport/TeleportHotspotExample.gif)
