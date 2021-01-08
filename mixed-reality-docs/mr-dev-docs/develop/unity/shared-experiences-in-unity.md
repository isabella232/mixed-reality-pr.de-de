---
title: Gemeinsame Erlebnisse in Unity
description: Erfahren Sie, wie Sie die gleichen holograms zwischen mehreren Benutzern in einer Unity-Anwendung mit räumlichen Azure-Ankern gemeinsam verwenden.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Sharing, Anchor, worldanchor, Mr Sharing 250, worldanchortransferbatch, spatialperception, Azure, Azure Spatial Anchor, ASA, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset
ms.openlocfilehash: a82439d5676bf4bcb7898a33aafc29b43e91a49f
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98031956"
---
# <a name="shared-experiences-in-unity"></a>Gemeinsame Erlebnisse in Unity

Eine gemeinsame Nutzung ermöglicht es mehreren Benutzern, die jeweils über ein eigenes hololens-, IOS-oder Android-Gerät verfügen, das gleiche Hologram anzuzeigen und mit Ihnen zu interagieren. Holograms werden über die räumliche Anker Freigabe an einem bestimmten Punkt im Bereich positioniert.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Räumliche Azure-Anker</a> erstellen dauerhafte, cloudgestützte räumliche Anker, die Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.  Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers auf mehreren Geräten kann jeder Benutzer den Inhalt in Relation zu diesem Anker am gleichen physischen Speicherort sehen. 

Sie können auch <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">räumliche Azure-Anker</a> für die asynchrone – Hologramm-Persistenz über hololens-, IOS-und Android-Geräte verwenden.  Durch die gemeinsame Nutzung eines permanenten clouddiensts können mehrere Geräte im Lauf der Zeit dasselbe persistente Hologramm beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.

Nachdem Azure Spatial Anchor eingerichtet wurde, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.

## <a name="local-anchor-transfers"></a>Lokale Anker Übertragungen

In Fällen, in denen Sie keine räumlichen Anker von Azure verwenden können, ermöglichen [lokale Anker Übertragungen](../../out-of-scope/local-anchor-transfers-in-unity.md) einem hololens-Gerät das Exportieren eines Ankers, sodass ein zweiter hololens ihn importieren kann.  Diese Vorgehensweise wird auf IOS-und Android-Geräten nicht unterstützt und bietet weniger robusten Anker als Anker als räumliche Azure-Anker.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen. Von hier aus können Sie mit dem nächsten Abschnitt fortfahren:

> [!div class="nextstepaction"]
> [Ausrichtbare Kamera](locatable-camera-in-unity.md)

Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:

> [!div class="nextstepaction"]
> [Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets](../platform-capabilities-and-apis/using-visual-studio.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-platform-capabilities-and-apis) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Gemeinsame Erlebnisse in Mixed Reality](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a>
