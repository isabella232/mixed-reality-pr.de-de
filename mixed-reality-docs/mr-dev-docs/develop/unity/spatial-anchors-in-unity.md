---
title: Räumliche Anker in Unity
description: Erfahren Sie, wie Sie räumliche Anker in Unity-Anwendungen mit gemischter Realität erstellen, speichern und abrufen.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, räumliche Anker, Anker Speicher, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623620"
---
# <a name="spatial-anchors-in-unity"></a>Räumliche Anker in Unity

Räumliche Anker sparen holograms im realen Raum zwischen Anwendungs Sitzungen. Nachdem Sie im Anker Speicher der hololens gespeichert wurden, können Sie gefunden und in verschiedene Sitzungen geladen werden. Sie sind ein idealer Fall Back, wenn keine Internetverbindung besteht.

> [!IMPORTANT]
> Lokale Anker werden auf dem Gerät gespeichert, während Azure-Raumanker in der Cloud gespeichert werden. Wenn Sie Azure Cloud Services zum Speichern Ihrer Anker verwenden möchten, verfügen wir über ein Dokument, in dem Sie durch den Integrationsprozess für [Azure-Raumanker](../mixed-reality-cloud-services.md#azure-spatial-anchors) geführt werden. Beachten Sie, dass Sie sowohl lokale als auch Azure-Anker im selben Projekt haben können, ohne dass Konflikte auftreten.

## <a name="understanding-anchors"></a>Grundlegendes zu Anker

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a>Verwenden des anchorstores

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Prüf Punkt Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, dass Sie die Grundbausteine der gemischten Realität erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Räumliche Abbildung](spatial-mapping-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Weitere Informationen
* [Dauerhaftigkeit räumlicher Anker](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a>
* [Skalierungsmöglichkeiten](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Räumliche Phase](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Verfolgbarkeitsverlust in Unity](tracking-loss-in-unity.md)
* [Raumanker](../../design/spatial-anchors.md)
* [Gemeinsame Erlebnisse in Unity](shared-experiences-in-unity.md)