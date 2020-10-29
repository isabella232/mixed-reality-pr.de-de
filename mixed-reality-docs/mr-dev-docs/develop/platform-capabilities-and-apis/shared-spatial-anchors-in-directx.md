---
title: Gemeinsame Raumanker in DirectX
description: Erläutert, wie zwei hololens-Geräte synchronisiert werden, indem räumliche Anker gemeinsam genutzt werden.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Hololens, synchronisieren, räumlicher Anker, Übertragung, Multiplayer, Ansicht, Szenario, Exemplarische Vorgehensweise, Beispielcode, Azure, räumliche Azure-Anker, ASA
ms.openlocfilehash: 2d6485e46a9802e1ee7e5adc12d6e0d026c79ae9
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684910"
---
# <a name="shared-experiences-in-directx"></a>Gemeinsam genutzte Umgebungen in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren WinRT-APIs.  Bei neuen nativen App-Projekten wird die Verwendung der **[openxr-API](../native/openxr-getting-started.md)** empfohlen.

Eine gemeinsame Nutzung ist eine, in der mehrere Benutzer mit jeweils eigenen hololens-, IOS-oder Android-Geräten das gleiche – Hologramm anzeigen und mit diesem interagieren, das an einem festgelegten Punkt positioniert ist. Dies wird durch die räumliche Anker Freigabe erreicht.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um permanente, von der Cloud gesicherte räumliche Anker zu erstellen, die Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.  Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers auf mehreren Geräten kann jeder Benutzer den Inhalt in Relation zu diesem Anker am gleichen physischen Speicherort sehen.  Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.

Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> auch für die asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden.  Durch die gemeinsame Nutzung eines dauerhaften Cloudraumankers können mehrere Geräte dasselbe persistierte Hologramm im Verlauf der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Um mit der Einführung von freigegebenen Erfahrungen in der hololens-APP zu beginnen, testen Sie den Schnellstart mit den fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchor hololens</a>.

Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">Anker in hololens erstellen und lokalisieren</a>.  Exemplarische Vorgehensweisen sind auch für <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android und IOS</a> verfügbar, sodass Sie dieselben Anker auf allen Geräten gemeinsam verwenden können.

## <a name="local-anchor-transfers"></a>Lokale Anker Übertragungen

In Fällen, in denen Sie keine räumlichen Anker von Azure verwenden können, ermöglichen [lokale Anker Übertragungen](../../out-of-scope/local-anchor-transfers-in-directx.md) einem hololens-Gerät das Exportieren eines Ankers, der von einem zweiten hololens-Gerät importiert werden soll.  Beachten Sie, dass dieser Ansatz weniger robusten Anker als räumliche Azure-Anker bietet und IOS-und Android-Geräte von diesem Ansatz nicht unterstützt werden.

## <a name="see-also"></a>Weitere Informationen
* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchor SDK für hololens</a>