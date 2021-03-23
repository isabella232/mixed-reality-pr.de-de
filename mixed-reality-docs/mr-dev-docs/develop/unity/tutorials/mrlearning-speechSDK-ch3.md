---
title: Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services
description: In diesem Kurs erfahren Sie, wie Sie Ihren Mixed Reality-Anwendungen die Sprachübersetzung von Azure Cognitive Services hinzufügen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, Spracherkennung, Windows 10, Sprachübersetzung
ms.localizationpriority: high
ms.openlocfilehash: bcc966b63f4c3e5bb9e6d6a38dc7f0312b288402
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590142"
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
