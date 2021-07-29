---
title: Übersicht über Holographic Remoting
description: Erfahren Sie, was Holographic Remoting ist und wie es Für Ihren Entwicklungsprozess von Vorteil sein kann.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Learn, Tutorial, Erste Schritte, holografisches Remoting, Desktop, Vorschau
ms.openlocfilehash: 6eb3b9e9fe8811ab4666ef1beda0e48668bedbe6
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757394"
---
# <a name="holographic-remoting-overview"></a>Übersicht über Holographic Remoting

Wenn Sie Ihrer PC-App oder Ihrem Pc-Spiel Unterstützung für Holographic Rendering hinzufügen, kann die App holografische Inhalte in Echtzeit an Ihre HoloLens 2 streamen. Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen. Anvisiert, Geste, Stimme und räumliche Zuordnungseingaben werden von Ihrem HoloLens 2 an Ihren PC gesendet, Inhalte werden in einer virtuellen immersiven Ansicht mit den größeren Systemressourcen des PCs gerendert, und die gerenderten Frames werden dann an Ihre HoloLens 2 zurückgesendet. Holographic Remoting ist auch für Windows Mixed Reality immersive Headsets verfügbar.

Sie fügen Holographic Remoting über ein NuGet-Paket zu Ihrer Desktop- oder UWP-App hinzu, und die Verbindung erfolgt über Standard-WLAN. Zusätzlicher Code ist erforderlich, der die Verbindung verarbeitet und in einer immersiven Ansicht rendert. Eine typische Remotingverbindung hat eine Latenz von bis zu 50 ms. Ihr Gerät zeigt den gestreamten Inhalt mithilfe einer Player-App an, die die Latenz in Echtzeit melden kann.

Als Unity-Entwickler können Sie Holographic Remoting auch verwenden, indem Sie Ihre App im Unity-Editor im Wiedergabemodus ausführen.

## <a name="see-also"></a>Weitere Informationen
* [Holographic Remoting-Player](holographic-remoting-player.md)
* [Schreiben einer Holographic Remoting-Remote-App mit Windows Mixed Reality-APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs](holographic-remoting-create-remote-openxr.md)
* [Tutorial: Erste Schritte mit Holographic Remoting für PCs](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Erstellen einer Holographic Remoting-PC-Anwendung](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
