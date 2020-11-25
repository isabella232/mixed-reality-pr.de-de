---
title: 'Tutorials zu Azure Speech-Diensten: 3 Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services'
description: In diesem Kurs erfahren Sie, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, Spracherkennung, Windows 10, Sprachübersetzung
ms.localizationpriority: high
ms.openlocfilehash: 1139da69b27352b996d57184e21e9d6291d26fce
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679919"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services

In diesem Tutorial fügen Sie Ihrem Projekt Sprachübersetzung hinzu, die es Ihnen ermöglicht, Ihre Sprache in drei verschiedene Sprachen zu übersetzen und zu transkribieren.

## <a name="objectives"></a>Ziele

* Erlernen der Integration von Azure-Sprachübersetzung

## <a name="instructions"></a>Anweisungen

Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Translation Recognizer (Script)** hinzuzufügen und sie wie folgt zu konfigurieren:

* Ändern Sie die **Zielsprache** in eine Sprache Ihrer Wahl, z. B. _Deutsch_

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> Die Komponente „Lunarcom Translation Recognizer (Script)“ ist kein Bestandteil des MRTK. Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.

Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Sprachübersetzung testen, indem Sie zuerst auf die Satellitenschaltfläche klicken. Falls Ihr Computer über ein Mikrofon verfügt, wird Ihre Sprache dann, wenn Sie etwas sagen, in die gewählte Sprache übersetzt und im Terminalbereich transkribiert:

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> Die Anwendung muss eine Verbindung mit Azure herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Ihr Projekt kann nun die von Ihnen gesprochenen Wörter erfolgreich in verschiedene Sprachen übersetzen. Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 4. Einrichten des Verständnisses von Absichten und natürlicher Sprache](mrlearning-speechSDK-ch4.md)
