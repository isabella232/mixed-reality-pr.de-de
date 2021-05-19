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
# <a name="teleport-hotspot-experimental"></a>Teleport-Hotspot [Experimentell]

Der Teleport-Hotspot ist eine Komponente, die Sie Ihrem Gameobject hinzufügen können, um sicherzustellen, dass sich der Benutzer an einer bestimmten Position und Ausrichtung befindet, wenn er an diesen Ort teleportieren soll.

## <a name="usage"></a>Verwendung

### <a name="how-to-create-a-teleport-hotspot"></a>Erstellen eines Teleport-Hotspots

Um einen Teleport-Hotspot zu erstellen, fügen Sie die TeleportHotspot-Komponente einem Objekt hinzu, das ebenfalls über eine Colliderkomponente verfügt. 

![Teleport Hotspot-Komponente](../images/teleport/TeleportHotspotComponent.png)

Nun ändert sich die Farbe des Teleportzeigers, wenn er über einen TeleportHotspot geleitet wird. Wenn die Teleportaktion über den Hotspot abgeschlossen ist, wird der Benutzer zum Mittelpunkt des TeleportHotspots teleportieren.

Wenn das Flag für die Außerkraftsetzungsausrichtung deaktiviert ist, entspricht die Ausrichtung des Benutzers der Ausrichtung des Teleport-Hotspots.

![Beispiel für Teleport-Hotspot](../images/teleport/TeleportHotspotExample.gif)
