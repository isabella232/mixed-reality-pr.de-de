---
title: Anzeigen einer Vorschau Ihrer Arbeit mit Holographic Remoting
description: Verwenden Sie Holographic Remoting im Wiedergabemodus, um eine Vorschau ihrer Anwendungsänderungen auf einem Gerät anzuzeigen, ohne eine App bereitzustellen.
author: keveleigh
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: Unity, Remoting, holografisches Remoting, holografischer Remotingplayer, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity-Wiedergabemodus
ms.openlocfilehash: cd9dca9d1ddf17b78e8c317fa3a58093c9b5837de379510148c6e645b31120ca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226232"
---
# <a name="preview-your-work-with-holographic-remoting"></a>Anzeigen einer Vorschau Ihrer Arbeit mit Holographic Remoting

Sie können Holographic Remoting verwenden, um holografische Inhalte in Echtzeit an Ihre HoloLens 2 zu streamen. Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen. 

Eine schnelle Möglichkeit, an Ihrem Unity-Projekt zu arbeiten, ist die Verwendung des "Wiedergabemodus", der Ihre App lokal im Unity-Editor auf Ihrem PC ausführt. Unity verwendet Holographic Remoting, um eine schnelle Möglichkeit zum Anzeigen einer Vorschau Ihrer Inhalte auf einem echten HoloLens Gerät bereitzustellen. Der Wiedergabemodus kann auch mit einem Windows Mixed Reality Headset verwendet werden, das an Ihren Entwicklungs-PC angefügt ist.

## <a name="holographic-remoting-setup"></a>Holographic Remoting-Setup

1. Zunächst müssen Sie [die Holographic Remoting Player-App](https://www.microsoft.com/store/productId/9NBLGGH4SV40) über die Microsoft Store auf Ihrem HoloLens 2
2. Führen Sie die Holographic Remoting Player-App auf dem HoloLens 2 aus, und Sie sehen die Versionsnummer und die IP-Adresse für die Verbindungsherstellung.
    * Sie benötigen Version 2.4 oder höher, um mit dem OpenXR-Plug-In arbeiten zu können.

    ![Screenshot des holografischen Remoting-Players, der im HoloLens](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Unity-Wiedergabemodus mit Holographic Remoting

Mit Holographic Remoting können Sie Ihre App auf dem HoloLens erleben, während sie im Unity-Editor auf Ihrem PC ausgeführt wird. Eingaben für Anvieren, Gesten, Stimmen und räumliche Zuordnungen werden von Ihrem HoloLens an Ihren PC gesendet. Gerenderte Frames werden dann an Ihre HoloLens zurückgesendet. Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen.

[!INCLUDE[](includes/unity-play-mode.md)]

Holographic Remoting erfordert einen schnellen PC und Wi-Fi Verbindung. Weitere Informationen finden Sie in der [Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-player.md) Player-Dokumentation.

Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass Ihre App den [Fokuspunkt](focus-point-in-unity.md)ordnungsgemäß festlegt. Dies hilft Holographic Remoting dabei, Ihre Szene am besten an die Latenz Ihrer Funkverbindung anzupassen.

## <a name="see-also"></a>Weitere Informationen

* [Holographic Remoting-Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
