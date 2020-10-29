---
title: Gemeinsame Erlebnisse in Unity
description: Verwenden Sie die gleichen holograms zwischen mehreren Benutzern in einer Unity-Anwendung.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Freigabe, Anker, worldanchor, Mr Sharing 250, worldanchortransferbatch, spatialperception, Azure, räumliche Azure-Anker, ASA
ms.openlocfilehash: 324aecdc89b4996625ce93514616c32d2d064ffa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684806"
---
# <a name="shared-experiences-in-unity"></a>Gemeinsame Erlebnisse in Unity

Eine gemeinsame Nutzung ist eine, in der mehrere Benutzer mit jeweils eigenen hololens-, IOS-oder Android-Geräten das gleiche – Hologramm anzeigen und mit diesem interagieren, das an einem festgelegten Punkt positioniert ist. Dies wird durch die räumliche Anker Freigabe erreicht.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um permanente, von der Cloud gesicherte räumliche Anker zu erstellen, die Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.  Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers auf mehreren Geräten kann jeder Benutzer den Inhalt in Relation zu diesem Anker am gleichen physischen Speicherort sehen.  Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.

Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> auch für die asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden.  Durch die gemeinsame Nutzung eines dauerhaften Cloudraumankers können mehrere Geräte dasselbe persistierte Hologramm im Verlauf der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.

Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.

## <a name="local-anchor-transfers"></a>Lokale Anker Übertragungen

In Fällen, in denen Sie keine räumlichen Anker von Azure verwenden können, ermöglichen [lokale Anker Übertragungen](../../out-of-scope/local-anchor-transfers-in-unity.md) einem hololens-Gerät das Exportieren eines Ankers, der von einem zweiten hololens-Gerät importiert werden soll.  Beachten Sie, dass dieser Ansatz weniger robusten Anker als räumliche Azure-Anker bietet und IOS-und Android-Geräte von diesem Ansatz nicht unterstützt werden.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungs Prüfpunkt

Wenn Sie der Unity-Entwicklungs-Prüfpunkt-Journey folgen, die wir festgelegt haben, sind Sie mitten in der Untersuchung der Funktionen und APIs der Mixed Reality-Plattform. Von hier aus können Sie mit dem nächsten Thema fortfahren:

> [!div class="nextstepaction"]
> [Ausrichtbare Kamera](locatable-camera-in-unity.md)

Oder direkt zur Bereitstellung der APP auf einem Gerät oder Emulator wechseln:

> [!div class="nextstepaction"]
> [Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets](../platform-capabilities-and-apis/using-visual-studio.md)

Sie können jederzeit jederzeit zu den [Unity-Entwicklungs Prüfpunkten](unity-development-overview.md#3-platform-capabilities-and-apis) zurückkehren.

## <a name="see-also"></a>Weitere Informationen
* [Gemeinsame Erlebnisse in Mixed Reality](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a>
