---
title: Einreichen von Fehlern und Feedback
description: Helfen Sie uns, die gemischte Realität von Windows zu verbessern, indem Sie Feedback mit den richtigen Kategorien in der Feedback-Hub-App einreichen
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: e0fdebf10ef7370964b0831f898dc151b3e243a0
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684331"
---
# <a name="filing-bugs-and-feedback"></a>Einreichen von Fehlern und Feedback

## <a name="why-its-important"></a>Warum es wichtig ist

Das Engineering-Team verwendet den gleichen Mechanismus intern für die Nachverfolgung und Korrektur von Fehlern. Bitte senden Sie uns Feedback-Hub, und melden Sie alle Fehler, die Sie sehen. Wir hören an!

## <a name="before-you-file-feedback"></a>Vor dem Senden von Feedback

Stellen Sie sicher, dass Ihr PC so eingestellt ist, dass wir vollständige Daten für Feedback und Diagnose bereitstellen. Im folgenden wird erläutert, wie Sie die Einstellung auf Ihrem PC überprüfen, bevor Sie Feedback einreichen:
1. Öffnen Sie die Windows- **Einstellungs** -app.
2. Klicken Sie auf **Datenschutz** .
3. Wechseln Sie im linken Bereich zu **Feedback & Diagnose** (Beachten Sie, dass dieses in den letzten Windows Insider-Builds von Windows in **Diagnotics &** .
4. Wählen Sie unter Wählen Sie aus, **wie viele Daten an Microsoft gesendet werden die** Option **voll** , wenn Sie nicht bereits ausgewählt ist.
5. Stellen Sie sicher, dass der PC neu gestartet wird, und wiederholen Sie die Schritte zum reproduzieren Ihres Problems, bevor Sie Feedback

## <a name="how-to-file-feedback-for-windows-mixed-reality-immersive-headsets-on-pc"></a>Vorgehensweise beim Senden von Feedback für die immersiven Windows Mixed Reality-Headsets auf dem PC
1. Stellen Sie sicher, dass das immersive Headset mit Ihrem PC verbunden ist.
2. Starten Sie den **Feedback-Hub** auf dem Desktop mit dem verbundenen HMD.
3. Wechseln Sie im linken Bereich zur **Registerkarte Feedback** . ![Feedback Registerkarte](images/feedback1.png) 
4. Klicken Sie auf **neue Feedback hinzufügen** , um das Feedback einzugeben. ![„Neues Feedback hinzufügen“](images/feedback2.png)
5. Wählen Sie in **welcher Art von Feedback das** **Problem** aus, um das Feedback zu ändern. ![Details und Reproduktions Schritte](images/feedback3.png)
6. Geben Sie einen aussagekräftigen Feedback Titel im Feld zusammen **fassen Ihres Problems** ein.
7. Geben Sie im Feld **Geben Sie weitere** Details Details und Schritte zum Reproduzieren des Problems an.
8. Wählen Sie **gemischte Realität** als oberste Kategorie aus, und wählen Sie dann eine anwendbare Unterkategorie aus:

   | Unterkategorie      | BESCHREIBUNG                                                                           |
   |------------------|---------------------------------------------------------------------------------------|
   | Apps-             | Probleme mit einer bestimmten Anwendung.                                                   |
   | Entwickler        | Probleme beim Erstellen/Ausführen einer APP für gemischte Realität.                               |
   | Sicherungsmedium           | Probleme mit dem HMD selbst.                                                           |
   | Startseite  | Probleme mit ihrer VR-Umgebung: Interaktionen mit der Windows Mixed Reality-Startseite.    |
   | Eingabe            | Probleme mit Eingabemethoden: Bewegungs Controller, Sprache, Gamepad, Maus und Tastatur.|
   | Einrichten           | Alles, was das Einrichten des Geräts verhindert.                           |
   | Alle anderen Probleme | Irgendetwas anderes.                                                                        |


9. Damit wir den Fehler schneller identifizieren und beheben können, ist die Erfassung von Ablauf Verfolgungen und Videos äußerst hilfreich. Klicken Sie zum Starten der Erfassung von Ablauf Verfolgungen auf **Start Erfassung** . Dadurch wird die Erfassung von Ablauf Verfolgungen und eine Video Erfassung Ihres Szenarios mit gemischter Realität begonnen. ![ Erfassung starten](images/feedback4.png)
10. Belassen Sie die Feedback-APP, und führen Sie das unterbrochene Szenario aus. Schließen Sie die Feedback-Hub-APP an dieser Stelle nicht.
11. Nachdem Sie das Szenario abgeschlossen haben, kehren Sie zur Feedback-app zurück, und klicken Sie auf **Erfassung Abbrechen** . Nachdem Sie dies getan haben, sollten Sie sehen, dass eine Datei mit den Ablauf Verfolgungen hinzugefügt wurde.
12. Klicken Sie auf **senden** . ![ Senden](images/feedback5.png)

Dadurch gelangen Sie zur Seite "Danke". An diesem Punkt wurde Ihr Feedback erfolgreich übermittelt. 

Nachdem Sie Ihr Feedback gesendet haben, können Sie andere Personen (z. b. Kollegen, Microsoft-Mitarbeiter, [Forumleser](https://forums.hololens.com/) usw.) problemlos an das Problem **>** weiterleiten, indem Sie auf das Problem klicken und das Symbol " **Freigeben** " verwenden, um eine verkürzte URL zu erhalten, die Sie anderen Benutzern zur Verfügung stellen können, oder eskalieren.

> [!IMPORTANT]
> Stellen Sie vor dem Einreichen eines Fehlers sicher, dass Sie die folgenden Einschränkungen einhalten, damit die Protokolle erfolgreich mit dem Feedback hochgeladen werden.
>    * Auf dem Haupt Laufwerk des Geräts sind mindestens 3 GB freier Speicherplatz verfügbar.
>    * Stellen Sie sicher, dass ein nicht getaktetes Netzwerk verfügbar ist, um Cabs hochzuladen.


## <a name="after-filing-feedback"></a>Nach dem Einreichen von Feedback

Stellen Sie sicher, dass Sie sich nach der Einreichung von Feedback regelmäßig mit dem Feedback-Hub In den meisten Fällen versuchen wir, so bald wie möglich zu antworten. Wenn Sie sich beim Senden von Feedback nicht bereits mit uns in Verbindung setzen, können wir Ihnen mit der Problembehandlung oder weiteren Fragen nur über das comments-System in der Feedback-Hub-Lösung Antworten. Leider werden Benachrichtigungen zu diesem Zeitpunkt nicht außerhalb des feedhubs gesendet.


## <a name="see-also"></a>Siehe auch
* [Problembehandlung](troubleshooting-windows-mixed-reality.md)

