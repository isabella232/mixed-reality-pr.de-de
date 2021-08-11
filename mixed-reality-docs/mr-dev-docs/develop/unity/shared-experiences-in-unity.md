---
title: Gemeinsame Erlebnisse in Unity
description: Erfahren Sie, wie Sie dieselben Hologramme für mehrere Benutzer in einer Unity-Anwendung mit Azure Spatial Anchors.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure Spatial Anchors, ASA, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: b9fdd09740dc6197c46a2d017f61e97898f213cd44bb504cbbf306f6a7ae21ec
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195922"
---
# <a name="shared-experiences-in-unity"></a>Gemeinsame Erlebnisse in Unity

Mit einer gemeinsamen Benutzererfahrung können mehrere Benutzer, die jeweils über ein eigenes HoloLens-, iOS- oder Android-Gerät verfügen, dasselbe Hologramm gemeinsam anzeigen und mit diesem interagieren. Hologramme werden an einem festen Punkt im Raum durch räumliche Ankerfreigabe positioniert.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

<a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> dauerhafte cloudbasierte Raumanker erstellen, die Ihre App dann auf mehreren HoloLens, iOS- und Android-Geräten finden kann.  Indem ein gemeinsamer Raumanker auf mehreren Geräten gemeinsam verwendet wird, kann jeder Benutzer Inhalte sehen, die relativ zu diesem Anker an derselben physischen Position gerendert werden. 

Sie können azure Spatial Anchors <a href="/azure/spatial-anchors/overview" target="_blank">auch für asynchrone</a> Hologrammpersistenz auf HoloLens, iOS- und Android-Geräten verwenden.  Durch die Gemeinsame Nutzung eines permanenten cloudbasierten Raumankers können mehrere Geräte dasselbe persistente Hologramm im Laufe der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Probieren Sie die fünfminütigen Schnellstartanleitungen zu Azure Spatial Anchors Unity aus, um mit dem Erstellen gemeinsamer Erfahrungen in <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity zu beginnen.</a>

Nachdem Azure Spatial Anchors eingerichtet wurde, können Sie Anker in <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity erstellen und suchen.</a>

## <a name="local-anchor-transfers"></a>Lokale Ankerübertragungen

In Situationen, in denen Sie Azure Spatial Anchors nicht verwenden [können,](../../out-of-scope/local-anchor-transfers-in-unity.md) ermöglichen lokale Ankerübertragungen einem HoloLens-Gerät das Exportieren eines Ankers, sodass ein zweiter HoloLens importieren kann.  Dieser Ansatz wird auf iOS- und Android-Geräten nicht unterstützt und bietet weniger stabile Ankerrückrufe als Azure Spatial Anchors.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie den weg zur Unity-Entwicklung gehen, den wir entwickelt haben, sind Sie gerade dabei, die Funktionen und APIs Mixed Reality Plattform zu erkunden. Von hier aus können Sie mit dem nächsten Abschnitt fortfahren:

> [!div class="nextstepaction"]
> [Ausrichtbare Kamera](locatable-camera-in-unity.md)

Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:

> [!div class="nextstepaction"]
> [Bereitstellen für HoloLens oder Windows Mixed Reality immersive Headsets](../platform-capabilities-and-apis/using-visual-studio.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-advanced-features) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Gemeinsame Erlebnisse in Mixed Reality](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK für Unity</a>