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
# <a name="teleport-hotspot"></a>Teleport-Hotspot

Der Teleport-Hotspot ist eine Komponente, die Sie Ihrem Gameobject hinzufügen können, um sicherzustellen, dass sich der Benutzer an einer bestimmten Position und Ausrichtung befindet, wenn er sich an diesen Ort teleportieren lässt.

## <a name="usage"></a>Verwendung

### <a name="how-to-create-a-teleport-hotspot"></a>Erstellen eines Teleport-Hotspots

Um einen Teleport-Hotspot zu erstellen, fügen Sie die TeleportHotspot-Komponente einem Objekt hinzu, das ebenfalls über eine Colliderkomponente verfügt. 

![Teleport Hotspot-Komponente](../images/teleport/TeleportHotspotComponent.png)

Nun ändert sich die Farbe des Teleportzeigers, wenn er über einen TeleportHotspot geleitet wird. Wenn die Teleportaktion über den Hotspot abgeschlossen ist, wird der Benutzer zum Mittelpunkt des TeleportHotspots teleportieren.

Wenn das Flag für die Außerkraftsetzungsausrichtung deaktiviert ist, entspricht die Ausrichtung des Benutzers der Ausrichtung des Teleport-Hotspots.

![Beispiel für Teleport-Hotspot](../images/teleport/TeleportHotspotExample.gif)
