---
title: Unity-Wiedergabemodus
description: Erfahren Sie, wie Sie den Wiedergabemodus im Unity-Editor verwenden, um eine Vorschau Ihrer Anwendungsänderungen auf einem Gerät anzuzeigen, ohne eine App bereitzustellen.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, Remoting, holografisches Remoting, Holographic Remoting-Player, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity-Wiedergabemodus
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547101"
---
# <a name="unity-play-mode"></a>Unity-Wiedergabemodus

Eine schnelle Möglichkeit, an Ihrem Unity-Projekt zu arbeiten, ist die Verwendung des "Wiedergabemodus", der Ihre App lokal im Unity-Editor auf Ihrem PC ausführt. Unity verwendet Holographic Remoting, um eine schnelle Möglichkeit zum Anzeigen einer Vorschau Ihrer Inhalte auf einem echten HoloLens-Gerät bereitzustellen. Der Wiedergabemodus kann auch mit einem Windows Mixed Reality Headset verwendet werden, das an Ihren Entwicklungs-PC angefügt ist.

## <a name="holographic-remoting-setup"></a>Holographic Remoting-Setup

1. Zunächst müssen Sie [die Holographic Remoting Player-App](https://www.microsoft.com/store/productId/9NBLGGH4SV40) über die Microsoft Store auf Ihrem HoloLens 2
2. Führen Sie die Holographic Remoting Player-App auf HoloLens 2 aus, und Sie sehen die Versionsnummer und die IP-Adresse für die Verbindungsherstellung.
    * Sie benötigen Version 2.4 oder höher, um mit dem OpenXR-Plug-In arbeiten zu können.

    ![Screenshot des Holographic Remoting-Players, der in holoLens ausgeführt wird](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic Remoting im Wiedergabemodus des Unity-Editors

Das Erstellen eines UWP-Unity-Projekts in Visual Studio Projekt und das anschließende Packen und Bereitstellen auf einem HoloLens 2 Gerät kann einige Zeit in Anspruch nehmen. Eine Lösung besteht darin, das Remotingfeature des Holographic Editor zu aktivieren, mit dem Sie Ihr C#-Skript im Wiedergabemodus direkt auf einem HoloLens 2 Gerät über Ihr Netzwerk debuggen können. In diesem Szenario wird der Mehraufwand für das Erstellen und Bereitstellen eines UWP-Pakets auf einem Remotegerät vermieden.

1. Führen Sie die Schritte unter [Holographic Remoting setup (Holographic Remoting-Setup)](#holographic-remoting-setup) aus.
2. Öffnen Sie **windows > XR > OpenXR Editor Remoting**:

    ![Screenshot: Geöffneter Bereich "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/openxr-features-img-02.png)

3. Geben Sie die IP-Adresse ein, die Sie aus der Holographic Remoting-App erhalten, und wählen **Sie Editor-Remoting aktivieren** aus.

    ![Screenshot: Geöffneter Bereich "Projekteinstellungen" im Unity-Editor mit hervorgehobenen Features](images/openxr-features-img-03.png)

Jetzt können Sie auf die Schaltfläche "Wiedergeben" klicken, um Ihre Unity-App in der Holographic Remoting-App auf Ihrer HoloLens wiederzugeben. Sie können auch [Visual Studio an Unity anfügen,](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) um C#-Skripts im Wiedergabemodus zu debuggen.

> [!NOTE]
> Ab Version 0.1.0 unterstützt die Holographic Remoting-Runtime Anchors nicht mehr, und ARAnchorManager-Funktionen funktionieren nicht über Remoting.  Dieses Feature wird in zukünftigen Versionen veröffentlicht.

## <a name="unity-play-mode-with-holographic-remoting"></a>Unity-Wiedergabemodus mit Holographic Remoting

Mit Holographic Remoting können Sie Ihre App auf der HoloLens erleben, während sie im Unity-Editor auf Ihrem PC ausgeführt wird. Eingaben für Anvieren, Gesten, Stimmen und räumliche Zuordnungen werden von Ihrer HoloLens an Ihren PC gesendet. Gerenderte Frames werden dann an Ihre HoloLens zurückgesendet. Dies ist eine hervorragende Möglichkeit, Ihre App schnell zu debuggen, ohne ein vollständiges Projekt zu erstellen und bereitzustellen.

[!INCLUDE[](includes/unity-play-mode.md)]

Holographic Remoting erfordert einen schnellen PC und Wi-Fi Verbindung. Weitere Informationen finden Sie in der [Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-player.md) Player-Dokumentation.

Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass Ihre App den [Fokuspunkt](focus-point-in-unity.md)ordnungsgemäß festlegt. Dies hilft Holographic Remoting dabei, Ihre Szene am besten an die Latenz Ihrer Funkverbindung anzupassen.

## <a name="see-also"></a>Weitere Informationen

* [Holographic Remoting-Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
