---
title: Übersicht über Holographic Remoting
description: Erfahren Sie, was Holographic Remoting ist und wie es Von Vorteil für Ihren Entwicklungsprozess sein kann.
author: hferrone
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte, holografisches Remoting, Desktop, Vorschau
ms.openlocfilehash: 52b69f942797b1f0a6a9bcc5276a49d4d2cebba5
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184601"
---
# <a name="holographic-remoting-overview"></a>Übersicht über Holographic Remoting

Sie können Holographic Remoting verwenden, um holografische Inhalte in Echtzeit an HoloLens Daten zu streamen. Dafür gibt es zwei Hauptmöglichkeiten, und es ist wichtig, den Unterschied zu verstehen:

1. (Unity oder **Unreal):** Sie möchten ihre App während des Entwicklungsprozesses in der Vorschau anzeigen und debuggen: Sie können Ihre App lokal im Unity-Editor auf Ihrem PC im Wiedergabemodus ausführen und die Erfahrung an Ihre HoloLens. Dies bietet eine Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen. Diese Art von App wird als _Holographic Remoting Play Mode Preview-App bezeichnet._

    - [Erfahren Sie mehr über die Vorschau und das Debuggen Ihrer App in Unity.](../unity/preview-and-debug-your-app.md)

    - [Erfahren Sie mehr über die Vorschau und das Debuggen Ihrer App in Unreal.](../unreal/unreal-streaming.md)

1. (Unity, Unreal oder C++): Sie möchten, dass die Ressourcen eines PCs Ihre App nutzen, anstatt sich auf die **HoloLens-On-Board-Ressourcen** zu verlassen: Sie können eine App erstellen und erstellen, die über Holographic Remoting-Funktionen verfügt. Der Benutzer sieht die App auf dem HoloLens, aber die App wird tatsächlich auf einem PC ausgeführt, wodurch sie die leistungsstärkeren Ressourcen des PCs nutzen kann. Dies kann besonders hilfreich sein, wenn Ihre App über hochauflösungsbasierte Ressourcen oder Modelle verfügt und die Bildfrequenz nicht darunter liegt. Diese Art von App wird als _Holographic Remoting-Remote-App bezeichnet._

    - [Weitere Informationen zur Verwendung von PC-Ressourcen in Unity](../unity/use-pc-resources.md)

    - [Weitere Informationen zur Verwendung von PC-Ressourcen in Unreal](../unreal/unreal-streaming.md)

    - [Schreiben einer Holographic Remoting-Remote-App mit Windows Mixed Reality-APIs (C++)](holographic-remoting-create-remote-wmr.md)

    - [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs (C++)](holographic-remoting-create-remote-openxr.md)

In beiden Fällen werden Eingaben der HoloLens – Anvieren, Gesten, Stimme und räumliche Abbildung – an den PC gesendet, Inhalte werden in einer virtuellen immersiven Ansicht gerendert, und die gerenderten Frames werden dann an die HoloLens. 

## <a name="see-also"></a>Weitere Informationen

* [Holographic Remoting-Player](holographic-remoting-player.md)
* [Tutorial: Erste Schritte mit holografischem PC-Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Erstellen einer Holographic Remoting-PC-Anwendung](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
