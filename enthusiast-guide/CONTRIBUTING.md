---
title: Beitragende Anweisungen
description: Erfahren Sie mehr über die grundlegenden Schritte und Richtlinien für den Beitrag zum Windows Mixed Reality-Enthusiasten-Handbuch. Wir freuen uns über Ihr Feedback, Änderungen, Ergänzungen und Hilfe.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: 78f1a66ea6e853e55b8020747abea22a1dc686e5
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684443"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Beitrag zum Mixed Reality-Enthusiasten-Leitfaden

Vielen Dank für Ihr Interesse am begeisterten Leitfaden. Wir freuen uns über Ihr Feedback, Änderungen, Ergänzungen und Hilfe bei der Verbesserung unserer Dokumente. Auf dieser Seite werden die grundlegenden Schritte und Richtlinien für den Beitrag behandelt.

> [!IMPORTANT]
> Für alle Repositorys, die in „docs.microsoft.com“ veröffentlichen, gilt der [Microsoft Open Source-Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/). Weitere Informationen finden Sie in den [häufig gestellten Fragen zum Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/faq/). Sie können sich mit Ihren Fragen oder Kommentaren auch an [opencode@microsoft.com](mailto:opencode@microsoft.com) wenden.<br>
>
> Für kleinere Korrekturen oder Klarstellungen zu Dokumentation und Codebeispielen in öffentlichen Repositorys gelten die [Nutzungsbestimmungen zu docs.microsoft.com](https://docs.microsoft.com/legal/termsofuse). Neue oder signifikante Änderungen haben einen Kommentar im Pull Request zur Folge, in dem wir Sie bitten, online eine Lizenzvereinbarung für Beiträge (Contribution License Agreement, CLA) zu übermitteln. Dies gilt, wenn Sie kein Mitarbeiter von Microsoft sind. Sie müssen das Onlineformular ausfüllen, damit wir Ihren Pull Request annehmen können.

## <a name="how-to-make-a-change"></a>So nehmen Sie eine Änderung vor

| Führe diese Schritte aus, um eine Änderung an den Dokumenten vorzuschlagen: | Screenshots |
| :------------------- | :--------: |
| 1. Wenn Sie eine docs.Microsoft.com-Seite anzeigen, klicken Sie oben rechts auf der Seite auf die Schaltfläche **Bearbeiten** .  Du wirst zur entsprechenden Markdown-Quelldatei im [GitHub-Repository](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) geleitet. | ![Bearbeitungs Schaltfläche](images/edit_button.jpg) |
| 2. Wenn Sie noch nicht über ein GitHub-Konto verfügen, klicken Sie oben rechts auf **registrieren** , und erstellen Sie ein neues Konto. | ![Schaltfläche "Anmelden"](images/signup-for-github-button.png)|
| 3. Klicken Sie auf der entsprechenden GitHub-Seite, die geöffnet wird, auf Bearbeiten (das Stift Symbol). | ![Stift Schaltfläche](images/pencil_button.jpg)|
| 4. verwenden Sie im Bereich "Datei bearbeiten" die markdown-Sprache, um Änderungen am Inhalt vorzunehmen. ([Schreiben von markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/))| ![Datei bearbeiten](images/edit-in-github.png)|
| 5. Klicken Sie auf Vorschau der Änderungen, um sicherzustellen, dass die Formatierung erwartungsgemäß aussieht | ![Vorschau der Änderungen](images/edit-in-github.png)|
| 6. Wenn Sie fertig sind, Scrollen Sie zum unteren Rand der Seite, und klicken Sie auf "Datei Änderung vorschlagen". Daraufhin wird die Seite "Änderungen werden verglichen" angezeigt, auf der Sie Ihre Änderungen überprüfen können. Klicken Sie dann auf die Schaltfläche "Create Pull Request", um die Änderungen zu übermitteln. An diesem Punkt sind Sie fertig! | ![Änderung vorschlagen](images/propose.jpg)|

Nachdem Sie Änderungen (über eine Pull Request) übermittelt haben, werden Sie von einem Mitglied des Dokumentationsteams geprüft. Wenn Ihre Anforderung akzeptiert wird, werden Updates in veröffentlicht [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide) .

* Zur internen Überprüfung können Sie Ihre Änderungen unter sehen [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .

## <a name="working-with-branches"></a>Arbeiten mit Verzweigungen

Das [GitHub-Repository für gemischte Realität](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) verwendet zwei übergeordnete Haupt Verzweigungen: [Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master), dieser Inhalt kann auf der [Stagingsite](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)überprüft werden und [Live](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live), um Inhalte zu erhalten, die auf der [Live Website](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide)angezeigt werden.

Wenn Sie Beiträge leisten, senden Sie Ihren Pull Request (PR) an den **masterb** Ranch. Diese Verzweigung kann auf der Stagingsite angezeigt werden und sollte nur Beiträge enthalten, die für die Liveveröffentlichung bereit sind. Sie können auch einen Branch mit Ihrem eigenen eindeutigen branchnamen erstellen und übermitteln, der in der Stagingsite ausgewählt und angezeigt werden kann. (Die **Live** Verzweigung ist nur für die Verwendung durch die Inhalts Administratoren zulässig.)

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>Verwenden von Problemen zur Bereitstellung von Feedback zum Windows Mixed Reality-Enthusiasten-Leitfaden

Wenn Sie Feedback bereitstellen oder auf ein Problem hinweisen möchten, anstatt die eigentlichen Dokumentationsseiten direkt zu ändern, [Erstellen Sie ein Problem](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) , und die Besitzer der Inhalte können das Problem rechtzeitig beheben.

Stellen Sie sicher, dass Sie den Thementitel und die URL einschließen, wenn Sie ein Problem in Bezug auf eine bestimmte Seite erstellen.

Vielen Dank für Ihre Unterstützung für diesen Inhalt!
