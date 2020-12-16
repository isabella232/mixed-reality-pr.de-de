---
title: Gemeinsame Raumanker in DirectX
description: Erläutert, wie zwei hololens-Geräte synchronisiert werden, indem räumliche Anker gemeinsam genutzt werden.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Hololens, synchronisieren, räumlicher Anker, Übertragung, Multiplayer, Ansicht, Szenario, Exemplarische Vorgehensweise, Beispielcode, Azure, räumliche Azure-Anker, ASA
ms.openlocfilehash: 4e41975a18c28cb2228b20ebb5d3a445774cca44
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530330"
---
# <a name="shared-experiences-in-directx"></a>Gemeinsam genutzte Umgebungen in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren WinRT-APIs.  Bei neuen nativen App-Projekten wird die Verwendung der **[openxr-API](../native/openxr-getting-started.md)** empfohlen.

Ein gemeinsam genutzter Vorgang ist eine, in der mehrere Benutzer mit ihren eigenen hololens-, IOS-oder Android-Geräten zusammen das gleiche Hologram anzeigen und mit ihnen interagieren. Das – Hologramm ist an einem bestimmten Punkt im Raum mithilfe der räumlichen Anker Freigabe positioniert.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um permanente, von der Cloud gesicherte räumliche Anker zu erstellen, die Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.  Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers auf mehreren Geräten kann jeder Benutzer den Inhalt in Relation zu diesem Anker am gleichen physischen Speicherort sehen.  Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.

Sie können auch <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">räumliche Azure-Anker</a> für die asynchrone – Hologramm-Persistenz über hololens-, IOS-und Android-Geräte verwenden.  Durch die gemeinsame Nutzung eines permanenten clouddiensts können mehrere Geräte im Lauf der Zeit dasselbe persistente Hologramm beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Um mit der Einführung von freigegebenen Erfahrungen in der hololens-APP zu beginnen, testen Sie den Schnellstart mit den fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchor hololens</a>.

Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">Anker in hololens erstellen und lokalisieren</a>.  Exemplarische Vorgehensweisen sind auch für <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android und IOS</a> verfügbar, sodass Sie dieselben Anker auf allen Geräten gemeinsam verwenden können.

## <a name="local-anchor-transfers"></a>Lokale Anker Übertragungen

In Fällen, in denen Sie keine räumlichen Anker von Azure verwenden können, ermöglichen [lokale Anker Übertragungen](../../out-of-scope/local-anchor-transfers-in-directx.md) einem hololens-Gerät das Exportieren eines Ankers, der von einem zweiten hololens-Gerät importiert werden soll.  Diese Vorgehensweise bietet weniger robusten Anker als die räumlichen Azure-Anker, und IOS-und Android-Geräte werden von diesem Ansatz nicht unterstützt.

## <a name="see-also"></a>Weitere Informationen
* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchor SDK für hololens</a>