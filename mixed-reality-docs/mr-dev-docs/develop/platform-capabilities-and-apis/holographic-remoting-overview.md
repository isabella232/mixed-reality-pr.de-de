---
title: Übersicht über Holographic Remoting
description: Erfahren Sie, was Holographic Remoting ist und wie es Von Vorteil für Ihren Entwicklungsprozess sein kann.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte, holografisches Remoting, Desktop, Vorschau
ms.openlocfilehash: 1b20590429b7df209e805ed8e94de5a6010bdbb609edc10fc5854cd4df86f64c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217116"
---
# <a name="holographic-remoting-overview"></a>Übersicht über Holographic Remoting

Wenn Sie Ihrer PC-App oder Ihrem Spiel Unterstützung für Holographic Rendering hinzufügen, kann die App holografische Inhalte in Echtzeit an HoloLens 2 Daten streamen. Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen. Anvisierten, Gesten, Stimmen und räumlichen Zuordnungseingaben werden von Ihrer HoloLens 2 an Ihren PC gesendet, Inhalte werden in einer virtuellen immersiven Ansicht mithilfe der größeren Systemressourcen des PCs gerendert, und die gerenderten Frames werden dann an Ihre HoloLens 2. Holographic Remoting ist auch für immersive Headsets Windows Mixed Reality verfügbar.

Sie fügen Holographic Remoting über ein NuGet-Paket zu Ihrer Desktop- oder UWP-App hinzu, und die Verbindung erfolgt über wlan-standard. Zusätzlicher Code ist erforderlich, der die Verbindung verarbeitet und in einer immersiven Ansicht rendert. Eine typische Remotingverbindung hat eine Latenz von bis zu 50 ms. Ihr Gerät zeigt den gestreamten Inhalt mithilfe einer "Player"-App an, die die Latenzzeit in Echtzeit melden kann.

Wenn Sie Unity-Entwickler sind, können Sie Holographic Remoting auch verwenden, indem Sie Ihre App im Unity-Editor im Wiedergabemodus ausführen.

## <a name="see-also"></a>Weitere Informationen
* [Holographic Remoting-Player](holographic-remoting-player.md)
* [Schreiben einer Holographic Remoting-Remote-App mit Windows Mixed Reality-APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs](holographic-remoting-create-remote-openxr.md)
* [Tutorial: Erste Schritte mit DEM HOLOGRAPHIC REMOTING-PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Erstellen einer Holographic Remoting-PC-Anwendung](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
