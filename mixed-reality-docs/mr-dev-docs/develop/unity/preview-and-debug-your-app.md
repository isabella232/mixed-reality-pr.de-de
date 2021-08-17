---
title: Anzeigen einer Vorschau und Debuggen Ihrer App mit Holographic Remoting und dem Wiedergabemodus
description: Verwenden des Holographic Remoting- und Wiedergabemodus zum Anzeigen der Vorschau und zum Debuggen Ihrer App
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Learn, Tutorial, erste Schritte, holografisches Remoting, Desktop, Vorschau, Debuggen
ms.openlocfilehash: fe15d55037f09c47fe1e8a1dd996d0c69480f7b2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203844"
---
# <a name="preview-and-debug-your-app-using-holographic-remoting-and-play-mode"></a>Anzeigen einer Vorschau und Debuggen Ihrer App mit holografischem Remoting und Wiedergabemodus

In diesem Artikel wird der folgende Anwendungsfall für Holographic Remoting erläutert: 

- **Sie möchten ihre App während des Entwicklungsprozesses in der Vorschau anzeigen und debuggen:** Sie können Ihre App lokal im Unity-Editor auf Ihrem PC im Wiedergabemodus ausführen und die Benutzeroberfläche an Ihre HoloLens streamen. Dies bietet eine Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen. Diese Art von App wird als _Holographic Remoting Play Mode Preview-App_ bezeichnet. Eingaben vom HoloLens – Anvisiert anvisiert, Geste, Stimme und räumliche Zuordnung – werden an den PC gesendet, wo Inhalte in einer virtuellen immersiven Ansicht gerendert werden. Die gerenderten Frames werden dann an die HoloLens gesendet. 

Weitere Informationen zu Holographic Remoting finden Sie unter [Übersicht über Holographic Remoting.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Beachten Sie, dass Sie holografisches Remoting auch verwenden können, wenn Sie möchten, dass [die Ressourcen eines PCs Ihre App mit Strom nutzen,](use-pc-resources.md) anstatt sich auf die HoloLens-On-Board-Ressourcen zu verlassen.

## <a name="set-up-holographic-remoting"></a>Einrichten von Holographic Remoting

Um Holographic Remoting zu verwenden, müssen Sie die [Holographic Remoting Player-App](../platform-capabilities-and-apis/holographic-remoting-player.md) über die Microsoft Store auf Ihrem HoloLens installieren. Wie unten erläutert, werden ihnen nach dem Herunterladen und Ausführen der App die Versionsnummer und die IP-Adresse angezeigt, mit der eine Verbindung hergestellt werden soll. **Sie benötigen v2.4 oder höher, um mit dem OpenXR-Plug-In zu arbeiten.**

Holographic Remoting erfordert einen schnellen PC und Wi-Fi Verbindung. Weitere Informationen finden Sie im oben verlinkten Holographic Remoting Player-Artikel.

![Screenshot des holografischen Remoting-Players, der im HoloLens](images/openxr-features-img-01.png)

[!INCLUDE[](includes/unity-play-mode.md)]

## <a name="see-also"></a>Weitere Informationen
* [Holographic Remoting-Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Tutorial: Erste Schritte mit PC Holographic Remoting](tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Erstellen einer Holographic Remoting-PC-Anwendung](tutorials/mr-learning-pc-holographic-remoting-02.md)
