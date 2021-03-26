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
# <a name="teleport-hotspot-experimental"></a>Teleport-Hotspot [experimentell]

Der Teleport-Hotspot ist eine Komponente, die Sie Ihrem gameobject hinzufügen können, um sicherzustellen, dass sich der Benutzer an einer bestimmten Position und Ausrichtung befindet, wenn er an diesen Speicherort teleportieren soll.

## <a name="usage"></a>Verwendung

### <a name="how-to-create-a-teleport-hotspot"></a>Erstellen eines Teleport-Hotspots

Um einen Teleport-Hotspot zu erstellen, fügen Sie die teleporthotspot-Komponente einem Objekt hinzu, das auch über eine Collider-Komponente verfügt. 

![Teleport-Hotspot-Komponente](../images/teleport/TeleportHotspotComponent.png)

Nun ändert sich der Indikator des Teleport-Zeigers, wenn er über einen teleporthotspot geleitet wird. Wenn die teleportaktion über den Hotspot abgeschlossen ist, wird der Benutzer in den Mittelpunkt des teleporthotspot-Vorgangs übertragen.

Wenn das Flag zur Überschreibungs Ausrichtung deaktiviert ist, entspricht die Ausrichtung des Benutzers dem des Teleport-Hotspots.

![Beispiel für teleporthotspot](../images/teleport/TeleportHotspotExample.gif)
