---
title: Gemeinsame Erlebnisse in Unity
description: Erfahren Sie, wie Sie die gleichen Hologramme für mehrere Benutzer in einer Unity-Anwendung mit Azure Spatial Anchors freigeben.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure Spatial Anchors, ASA, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset
ms.openlocfilehash: f7725c8282d1b5a93d555ac0f55ee936b910ff6c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244182"
---
# <a name="shared-experiences-in-unity"></a>Gemeinsame Erlebnisse in Unity

Eine gemeinsame Benutzeroberfläche ermöglicht es mehreren Benutzern, jeweils mit ihren eigenen HoloLens-, iOS- oder Android-Geräten, gemeinsam das gleiche Hologramm anzuzeigen und mit ihnen zu interagieren. Hologramme werden durch räumliche Ankerfreigabe an einem festen Punkt im Raum positioniert.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

### <a name="automated-with-world-locking-tools"></a>Automatisiert mit World Locking Tools

Wie bei lokalen Ankern können die World Locking Tools eine Gruppe von Azure Spatial Anchors verwenden, um ganze Koordinatenräume relativ zur physischen Welt zu sperren, anstatt einzelne Anker zum Sperren einzelner Objekte zu verwenden. Die Welt, die den gesamten Raum sperrt, bietet nicht nur eine Umgebung, die für ein präzises Layout anfälliger ist, sondern auch effizienter sowohl in der Entwicklerzeit als auch in den Laufzeitressourcen.

Weitere Informationen und Beispiele zur Nutzung von Azure Spatial Anchors, um Koordinatensysteme für HoloLens-, Android- und iOS-Geräte freizugeben sowie Leerzeichen sitzungsübergreifend zu speichern, finden Sie in der [Dokumentation zu den World Locking Tools](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLT_ASA.html).

### <a name="manual-configuration-of-azure-spatial-anchors"></a>Manuelle Konfiguration von Azure Spatial Anchors

<a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> dauerhafte cloudbasierte Raumanker erstellen, die Ihre App auf mehreren HoloLens-, iOS- und Android-Geräten finden kann.  Durch die gemeinsame Nutzung eines gemeinsamen Raumankers auf mehreren Geräten kann jeder Benutzer sehen, dass Inhalte relativ zu diesem Anker an demselben physischen Ort gerendert werden.

Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> auch für asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden.  Durch die gemeinsame Nutzung eines permanenten Cloudraumankers können mehrere Geräte das gleiche persistente Hologramm im Laufe der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Probieren Sie die fünfminütigen <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity-Schnellstarts</a>aus, um mit dem Erstellen von freigegebenen Erfahrungen in Unity zu beginnen.

Sobald Azure Spatial Anchors eingerichtet ist, können Sie <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und suchen.</a>

## <a name="local-anchor-transfers"></a>Lokale Ankerübertragungen

In Situationen, in denen Sie Azure Spatial Anchors nicht verwenden können, ermöglichen [lokale Ankerübertragungen](../../out-of-scope/local-anchor-transfers-in-unity.md) einem HoloLens Gerät, einen Anker zu exportieren, sodass ein zweiter HoloLens ihn importieren kann.  Dieser Ansatz wird auf iOS- und Android-Geräten nicht unterstützt und bietet weniger stabile Ankerrückrufe als Azure Spatial Anchors.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, erkunden Sie die Mixed Reality Plattformfunktionen und APIs. Von hier aus können Sie mit dem nächsten Abschnitt fortfahren:

> [!div class="nextstepaction"]
> [Ausrichtbare Kamera](locatable-camera-in-unity.md)

Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:

> [!div class="nextstepaction"]
> [Bereitstellen in HoloLens oder Windows Mixed Reality immersiven Headsets](../platform-capabilities-and-apis/using-visual-studio.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-advanced-features) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Gemeinsame Erlebnisse in Mixed Reality](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK für Unity</a>