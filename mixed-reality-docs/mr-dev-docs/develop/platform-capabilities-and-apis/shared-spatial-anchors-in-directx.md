---
title: Gemeinsame Raumanker in DirectX
description: Erfahren Sie, wie Sie zwei HoloLens-Geräte synchronisieren, indem Sie lokale und Azure-Raumanker in DirectX-Anwendungen freigeben.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, Synchronisieren, Raumanker, Übertragung, Multiplayer, Ansicht, Szenario, exemplarische Vorgehensweise, Beispielcode, Azure, Azure Spatial Anchors, ASA
ms.openlocfilehash: 6b1b98539c05849064f1c33ed859bc925ed5fd31
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244318"
---
<!--Unity Note: No Unity specific content in this article. -->
# <a name="shared-experiences-in-directx"></a>Gemeinsame Erfahrungen in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren nativen WinRT-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API](../native/openxr-getting-started.md)** empfohlen.

Eine gemeinsame Benutzeroberfläche ist eine, bei der mehrere Benutzer mit ihren eigenen HoloLens,iOS- oder Android-Geräten gemeinsam das gleiche Hologramm anzeigen und mit ihnen interagieren. Das Hologramm wird mithilfe der Räumlichen Ankerfreigabe an einem festen Punkt im Raum positioniert.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> verwenden, um dauerhafte cloudbasierte Raumanker zu erstellen, die Ihre App dann auf mehreren HoloLens-, iOS- und Android-Geräten finden kann.  Durch die gemeinsame Nutzung eines gemeinsamen Raumankers auf mehreren Geräten kann jeder Benutzer sehen, dass Inhalte relativ zu diesem Anker an demselben physischen Ort gerendert werden.  Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.

Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> auch für asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden.  Durch die gemeinsame Nutzung eines permanenten Cloudraumankers können mehrere Geräte das gleiche persistente Hologramm im Laufe der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Probieren Sie die fünfminütige <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens-Schnellstartanleitung</a>aus, um mit dem Erstellen von freigegebenen Erfahrungen in Ihrer HoloLens-App zu beginnen.

Sobald Sie mit Azure Spatial Anchors ausgeführt werden, können Sie <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">Anker auf HoloLens erstellen und suchen.</a>  Exemplarische Vorgehensweisen sind auch für <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android und iOS</a> verfügbar, sodass Sie dieselben Anker auf allen Geräten freigeben können.

## <a name="local-anchor-transfers"></a>Lokale Ankerübertragungen

In Situationen, in denen Sie Azure Spatial Anchors nicht verwenden können, ermöglichen [lokale Ankerübertragungen](../../out-of-scope/local-anchor-transfers-in-directx.md) einem HoloLens Gerät, einen Anker zu exportieren, der von einem zweiten HoloLens Gerät importiert werden soll.  Dieser Ansatz bietet weniger stabile Ankerrückrufe als Azure Spatial Anchors, und iOS- und Android-Geräte werden von diesem Ansatz nicht unterstützt.

## <a name="see-also"></a>Siehe auch

* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK für HoloLens</a>