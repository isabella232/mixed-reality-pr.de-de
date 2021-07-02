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
# <a name="teleport-hotspot"></a>Teleport-Hotspot

Der Teleport-Hotspot ist eine Komponente, die Sie Ihrem Gameobject hinzufügen können, um sicherzustellen, dass sich der Benutzer an einer bestimmten Position und Ausrichtung befindet, wenn er an diesen Standort teleportieren kann.

## <a name="usage"></a>Verwendung

### <a name="how-to-create-a-teleport-hotspot"></a>Erstellen eines Teleport-Hotspots

Um einen Teleport-Hotspot zu erstellen, fügen Sie die TeleportHotspot-Komponente einem Objekt hinzu, das auch über eine Colliderkomponente verfügt. 

![Teleport Hotspot-Komponente](../images/teleport/TeleportHotspotComponent.png)

Jetzt ändert sich die Farbe des Teleportzeigers, wenn er über einen TeleportHotspot geleitet wird. Wenn die Teleportaktion über den Hotspot abgeschlossen ist, wird der Benutzer zum Mittelpunkt des TeleportHotspots teleportiert.

Wenn das Flag für die Überschreibungsausrichtung deaktiviert ist, wird die Ausrichtung des Benutzers mit der Ausrichtung des Teleport-Hotspots übereinstimmen.

![Beispiel für Teleport-Hotspot](../images/teleport/TeleportHotspotExample.gif)
