---
title: Hinzufügen eines Offlinemodus für die lokale Sprache-zu-Text-Übersetzung
description: In diesem Kurs lernen Sie, wie Sie der Spracherkennung in Mixed-Reality-Anwendungen den Offlinemodus für die lokale Übersetzung hinzufügen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, Spracherkennung, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 2e7a48dc4bb64eb177e6fa290f4918345c3d642f
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590152"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a>2. Hinzufügen eines Offlinemodus für die lokale Sprache-zu-Text-Übersetzung

In diesem Tutorial fügen Sie die Möglichkeit hinzu, Befehle mithilfe der Azure-Spracherkennung auszuführen, sodass Sie basierend auf dem von Ihnen definierten Wort oder Ausdruck eine Aktion auslösen können.

## <a name="objectives"></a>Ziele

* Erfahren, wie die Azure-Spracherkennung zum Ausführen von Befehlen verwendet werden kann

## <a name="instructions"></a>Anweisungen

Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Wake Word Recognizer (Script)** hinzuzufügen und sie wie folgt zu konfigurieren:

* Geben Sie im Feld **Wake Word** (Wort zum Aufwecken) einen passenden Ausdruck ein, z. B. _Terminal aktivieren_.
* Geben Sie im Feld **Dismiss Word** (Wort zum Schließen) einen passenden Ausdruck ein, z. B. _Terminal schließen_.

![Unity-Editor mit hervorgehobener Skriptkomponente „Lunarcom Wake Word Recognizer“](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> Die Komponente „Lunarcom Wake Word Recognizer (Script)“ ist kein Bestandteil des MRTK. Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.

Wenn Sie jetzt in den Spielmodus wechseln, wie im vorherigen Tutorial, ist der Terminalbereich standardmäßig aktiviert. Sie können ihn jetzt jedoch deaktivieren, indem Sie das Wort zum Schließen aussprechen, **Terminal schließen**:

![Unity-Editor im Spielmodus mit aktivierter Funktion zur Spracherkennung](images/mrlearning-speech/tutorial2-section1-step1-2.png)

Und es erneut aktivieren, indem Sie das Wort zum Aufwecken sprechen **Terminal aktivieren**:

![Unity-Editor im Spielmodus mit aktivem Terminal](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> Die Anwendung muss eine Verbindung mit Azure herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.

> [!TIP]
> Wenn Sie davon ausgehen müssen, dass Sie häufig keine Verbindung mit Azure herstellen können, können Sie außerdem Sprachbefehle mithilfe von MRTK implementieren. Befolgen Sie dazu die Anweisungen unter [Verwenden von Sprachbefehlen](mr-learning-base-09.md).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben die von Azure unterstützten Sprachbefehle implementiert. Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.

Im nächsten Tutorial erfahren Sie, wie Sprache mithilfe von Azure-Sprachübersetzung übersetzt wird.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 3. Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services](mrlearning-speechSDK-ch3.md)
