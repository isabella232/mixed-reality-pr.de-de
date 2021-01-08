---
title: Unity-Wiedergabemodus
description: Erfahren Sie, wie Sie den Wiedergabemodus im Unity-Editor verwenden, um die Änderungen an der Anwendung auf einem Gerät anzuzeigen, ohne eine APP bereitzustellen.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Remoting, Holographic Remoting, Holographic Remoting Player, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity-Wiedergabemodus
ms.openlocfilehash: 9f6c2cafd08fca8a5d60f3fcf5832ee74762e173
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009840"
---
# <a name="unity-play-mode"></a>Unity-Wiedergabemodus

Eine schnelle Möglichkeit, an Ihrem Unity-Projekt zu arbeiten, ist die Verwendung des "Wiedergabemodus", bei dem Ihre APP lokal im Unity-Editor auf Ihrem PC ausgeführt wird. Unity verwendet Holographic Remoting, um eine schnelle Möglichkeit zum Anzeigen einer Vorschau Ihrer Inhalte auf einem echten hololens-Gerät bereitzustellen. Der Wiedergabemodus kann auch mit einem Windows Mixed Reality-Headset verwendet werden, das an ihren Entwicklungs-PC angeschlossen ist.

## <a name="unity-play-mode-with-holographic-remoting"></a>Unity-Wiedergabemodus mit Holographic-Remoting

Mit Holographic Remoting können Sie Ihre APP auf den hololens erleben, während Sie im Unity-Editor auf Ihrem PC ausgeführt wird. Eingaben, Gesten, Stimme und räumliche zuordnungseingaben werden von ihren hololens an Ihren PC gesendet. Gerenderte Frames werden dann zurück an Ihre hololens gesendet. Dies ist eine gute Möglichkeit, Ihre APP schnell zu debuggen, ohne ein vollständiges Projekt zu entwickeln und bereitzustellen.
1. Wechseln Sie auf Ihren hololens zum **Microsoft Store** , und installieren Sie die **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** -app.
2. Starten Sie auf Ihren hololens die **Holographic Remoting Player** -app.
3. Wechseln Sie in Unity zum Menü " **Fenster** ", erweitern Sie das Untermenü " **XR** ", und wählen Sie **Holographic Emulation** aus.
4. Festlegen des **Emulations Modus** auf **Remote-zu-Gerät**.
5. Geben Sie für **Remote Computer** die IP-Adresse der hololens ein.
6. Wählen Sie **Verbinden** aus. Der **Verbindungs Status** sollte in **verbunden** angezeigt werden, und der Bildschirm wechselt in den hololens leer.
7. Wählen Sie die **Wiedergabe** Schaltfläche, um den Wiedergabemodus zu starten, und erleben Sie die APP auf Ihren hololens

Holographic Remoting erfordert eine schnelle PC-und Wi-Fi Verbindung. Weitere Informationen finden Sie in der Dokumentation zu [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) .

Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass Ihre APP den [Fokuspunkt](focus-point-in-unity.md)ordnungsgemäß festlegt. Dies hilft Holographic Remoting bei der optimalen Anpassung Ihrer Szene an die Latenz Ihrer drahtlosen Verbindung.

## <a name="see-also"></a>Weitere Informationen
* [Holographic Remoting-Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
