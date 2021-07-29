---
title: Anzeigen einer Vorschau Ihrer Arbeit mit Holographic Remoting
description: Verwenden Sie Holographic Remoting im Wiedergabemodus, um eine Vorschau Ihrer Anwendungsänderungen auf einem Gerät anzuzeigen, ohne eine App bereitzustellen.
author: keveleigh
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: Unity, Remoting, holografisches Remoting, holografischer Remotingplayer, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity-Wiedergabemodus
ms.openlocfilehash: 0c71791c80a5e84ee48241baa756064a800e5a41
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757212"
---
# <a name="preview-your-work-with-holographic-remoting"></a>Anzeigen einer Vorschau Ihrer Arbeit mit Holographic Remoting

Sie können Holographic Remoting verwenden, um holografische Inhalte in Echtzeit an HoloLens 2 Daten zu streamen. Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen. 

Eine schnelle Möglichkeit, an Ihrem Unity-Projekt zu arbeiten, ist die Verwendung des "Wiedergabemodus", der Ihre App lokal im Unity-Editor auf Ihrem PC ausführen kann. Unity verwendet Holographic Remoting, um eine schnelle Möglichkeit zum Anzeigen einer Vorschau Ihrer Inhalte auf einem echten HoloLens bieten. Der Wiedergabemodus kann auch mit einem Windows Mixed Reality Headset verwendet werden, das an Ihren Entwicklungs-PC angeschlossen ist.

## <a name="holographic-remoting-setup"></a>Holographic Remoting-Setup

1. Zunächst müssen Sie die [Holographic Remoting Player-App](https://www.microsoft.com/store/productId/9NBLGGH4SV40) aus dem Microsoft Store auf Ihrem Computer HoloLens 2
2. Führen Sie die Holographic Remoting Player-App auf dem HoloLens 2, und Die Versionsnummer und die IP-Adresse für die Verbindung werden angezeigt.
    * Sie benötigen Version 2.4 oder höher, um mit dem OpenXR-Plug-In arbeiten zu können.

    ![Screenshot des Holographic Remoting-Players, der in der HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Unity-Wiedergabemodus mit Holographic Remoting

Mit Holographic Remoting können Sie Ihre App auf dem Computer HoloLens während sie im Unity-Editor auf Ihrem PC ausgeführt wird. Eingaben für Anvieren, Gesten, Sprache und räumliche Zuordnung werden von HoloLens an Ihren PC gesendet. Gerenderte Frames werden dann zurück an ihre HoloLens. Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen.

[!INCLUDE[](includes/unity-play-mode.md)]

Holographic Remoting erfordert einen schnellen PC und eine Wi-Fi Verbindung. Weitere Informationen finden Sie in der [Dokumentation zu Holographic Remoting Player.](../platform-capabilities-and-apis/holographic-remoting-player.md)

Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass Ihre App den [Fokuspunkt ordnungsgemäß fest legt.](focus-point-in-unity.md) Dies hilft Holographic Remoting dabei, Ihre Szene am besten an die Latenz Ihrer Drahtlosverbindung anzupassen.

## <a name="see-also"></a>Weitere Informationen

* [Holographic Remoting-Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
