---
title: Controller in Windows Mixed Reality
description: Erfahren Sie, wie Sie Controller in Windows Mixed Reality einrichten und verwenden.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: f349f4bbc2cadd511515783504562052f1d58ed3
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725391"
---
# <a name="motion-controllers-in-windows-mixed-reality"></a>Motion Controller in Windows Mixed Reality

Bewegungs Controller sind Hardware Zubehör, mit denen Benutzer in gemischter Realität interagieren können. Ein Vorteil von Bewegungs Controllern gegenüber Gesten besteht darin, dass die Controller eine genaue Position im Raum aufweisen und eine differenzierte Interaktion mit digitalen Objekten ermöglichen. Für Windows Mixed Reality-immersive Headsets sind Bewegungs Controller die primäre Methode, mit der Benutzer in ihrer Welt Maßnahmen ergreifen können.

Windows Mixed Reality Motion Controllers bieten mithilfe der immersiven Headset-Sensoren eine präzise und reaktionsfähige Bewegungs Nachverfolgung in ihrer Ansicht. Es ist nicht erforderlich, Hardware an den Wänden in Ihrem Bereich zu installieren. Diese Motion-Controller bieten dieselbe einfache Einrichtung und Portabilität wie Windows Mixed Reality (immersive Headsets).

Sie können auch einen Xbox-Controller, eine Maus und Tastatur verwenden oder mit [nur ihrer Stimme](using-speech-in-wmr.md)umgehen.

## <a name="motion-controller-setup"></a>Motion Controller-Setup

Die meisten Headsets sind direkt mit dem Headset gekoppelt, aber einige frühe Headsets erfordern, dass die Motion-Controller mit dem PC mit Bluetooth 4,0 gekoppelt werden. Wenn Sie Ihr immersives Headset zum ersten Mal verbinden, werden Sie durch das Einschalten der Motion-Controller während des Setups gelangen. Wenn Sie diese später erneut koppeln müssen, gehen Sie wie folgt vor:

1. Starten Sie das **Mixed Reality-Portal** mit dem verbundenen Headset.  
2. Wählen Sie in der unteren linken Ecke **... > einrichten von Controllern**.
3. Fügen Sie zwei AA-Akkus in jeden Controller ein, und versetzen Sie den Controller in den Paarmodus (Weitere Informationen finden Sie im [Abschnitt zum paar Motion](controllers-in-wmr.md#pair-motion-controllers)
4. Befolgen Sie die Anweisungen auf dem Bildschirm.

> [!NOTE]
> * Bei Controllern, die direkt mit Ihrem PC gekoppelt werden, müssen Sie Sie in den Paarmodus versetzen, indem Sie Sie einschalten und dann auf die Schaltfläche Kopplung innerhalb des Akku Depots drücken, bis die Beleuchtung blinkt.
> * Bewegungs Controller unterstützen nur einen PC gleichzeitig. Wenn Sie diese mit einem anderen Headset verwenden müssen, müssen Sie den paarweise Vorgang durchlaufen. Siehe [Einrichten von Windows Mixed Reality](set-up-windows-mixed-reality.md)

[Hilfe beim Herstellen einer Verbindung](wmr-setup-faq.md#my-motion-controllers-arent-working)

> [!IMPORTANT]
> **Haben Sie einen Xbox-Controller?**
> 
> Wenn Sie über einen Bluetooth Xbox-Controller verfügen, koppeln Sie ihn mit Ihrem PC, um ihn mit Ihrem Headset zu verwenden.
> 
> Wenn Sie über einen kabelgebundenen Xbox-Controller verfügen, können Sie ihn an Ihren PC anschließen.
> 
> Einige Spiele und Apps verwenden den Xbox-Controller anders als in gemischter Realität. Wenn Sie den Controller für ein Spiel oder eine APP verwenden möchten, wählen Sie in der APP-Leiste die Option **als Gamepad verwenden** aus, oder sagen Sie "als Gamepad verwenden". Um den Controller wieder in die gemischte Realität zu wechseln, wählen Sie **als Gamepad verwenden** aus, oder wählen Sie "mit Blick verwenden" aus.  

## <a name="pair-motion-controllers"></a>Paar Bewegungs Controller

Wenn Sie ein Headset verwenden, das einen integrierten Bluetooth-Controller enthält, z. b. Samsung Odyssee + oder HP-Reverb, sollten ihre Controller bereits gekoppelt sein. Sie können Ihre Controller aber trotzdem mithilfe der Setup-App koppeln (Sie muss bereits während der Einrichtung des HMD installiert sein. Sie können es auch aus dem Microsoft Store erhalten.)

### <a name="pair-motion-controllers-to-hmd"></a>Kombinieren von Bewegungs Controllern mit HMD

Schalten Sie die Controller durch Drücken der Windows-Taste 2 Sekunden lang hoch, bis die LEDs leuchten.

Entfernen Sie die Batterieabdeckung von ihren Controllern, und suchen Sie die Schaltfläche kleine Kopplung am Rand des Controllers. Halten Sie diese Schaltfläche gedrückt, um mit Ihrem PC zu koppeln.
    ![Bewegung Controller Kopplung](images/connect_controller.png)

Starten Sie das **Mixed Reality-Portal** mit dem verbundenen Headset.  
Wählen Sie in der unteren linken Ecke **... > einrichten von Controllern**.
Folgen Sie den Anweisungen auf dem Bildschirm.

### <a name="pair-motion-controllers-to-pc"></a>Kombinieren von Bewegungs Controllern zum PC

Sie können Ihren Controller mit einem PC koppeln, indem Sie ein weiteres Bluetooth-Gerät hinzufügen.

Schalten Sie die Controller ein, und platzieren Sie Sie wie oben beschrieben in den paarweise.

* Navigieren zu Computer Einstellungen
* Gerät/Bluetooth oder anderes Gerät hinzufügen.

Nachdem die Kopplung vollständig ist, sind LEDs einleuchtend und hell.

### <a name="common-issues"></a>Häufige Probleme

* Vergewissern Sie sich, dass auf Ihrem PC nur ein Bluetooth-radioaktiv ist. Wenn Sie über mehr als ein Bluetooth-Radio verfügen, müssen Sie die anderen Radios in Geräte-Manager deaktivieren.
* Platzieren Sie Ihr Bluetooth-Dongle an einem Port, der über eine klare Sichtlinie an Ihre Controller und weit von USB 3,0-Geräten angeschlossen ist. USB 3,0 weist eine RF-Beeinträchtigung mit Bluetooth auf (Weitere Informationen finden Sie in [diesem Dokument](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/usb3-frequency-interference-paper.pdf) von Intel). USB-2,0-Ports funktionieren möglicherweise besser für das Bluetooth-Dongle.
* Stellen Sie sicher, dass Ihr Bluetooth-Dongle nicht an einem USB-Anschluss neben dem USB-Kabel Ihres HMD angeschlossen ist. Das Headset-Kabel hat bekanntermaßen auch Störungen mit Bluetooth-Dongles zur Ursache. Verbinden Sie den Ring an den Front-USB-Anschluss auf Ihrem PC, um optimale Ergebnisse zu erzielen.
* Stellen Sie für Notebooks sicher, dass WiFi mit einem 5-GHz-Band verbunden ist, um optimale Ergebnisse zu erzielen. Wählen Sie das Drahtlos Netzwerk Symbol unten rechts aus, und wählen Sie Eigenschaften für das Netzwerk aus, das Sie verwenden. Notebooks, die für die Verwendung einer 2,4 GHz-Antenne für Bluetooth-und WiFi-Konnektivität entwickelt wurden, werden die Datenüberlastung von langsamen Netzwerkgeschwindigkeiten oder eine schlechte Überwachung der Bewegungs Controller Leistung erkennen.
* Ihre Motion-Controller erhalten regelmäßig neue Software Updates von Microsoft. Die Controller zeigen ein Abwechselndes Muster mit blinkenden Lichtern an, wenn diese neuen Software Updates empfangen werden. Dies ist normal. Warten Sie, bis das Software Upgrade fertiggestellt ist, bevor Sie die Controller verwenden. Die Controller werden vibrieren, und ein konstantes Licht ersetzt das abwechselnde Flash Muster, wenn es ausgeführt wird.
* Sie werden möglicherweise aufgefordert, das Headset zu verwenden und den Fingerabdruck zum teleportieren zu verwenden, bevor die Controller den Aktualisierungs Vorgang beenden. Die Controller sind erst sichtbar oder verwendbar, wenn die Aktualisierung abgeschlossen ist. Die meisten Updates erfolgen innerhalb von zwei Minuten, Updates können jedoch bis zu 10 Minuten dauern. Warten Sie, bis das Update fertiggestellt ist, und fahren Sie mit dem nächsten Schritt fort.

## <a name="using-controllers"></a>Verwenden von Controllern

Im folgenden wird erläutert, wie Sie in gemischter Realität mit Bewegungs Controllern, einem Xbox Gamepad oder einer Maus und Tastatur umgehen.

> [!TIP]
> Um die Eingabe zwischen gemischter Realität und Ihrem Desktop zu wechseln, drücken Sie die **Windows-Taste + Y** auf der PC-Tastatur.

![Tasten Zuordnung für Motion Controller](images/get_to_know_controllers.png)

|  Aufgabe  |  Bewegungscontroller  | Gamepad | Maus und Tastatur |
| --- | --- | --- | --- |
| Teleport | Drücken Sie den Fingerabdruck, und zeigen Sie dann auf den gewünschten Controller. Geben Sie den Finger Stick frei. | Drücken Sie den linken Finger Stick vorwärts, und sehen Sie sich an, wohin Sie navigieren möchten. Geben Sie den Finger Stick frei. | Wählen Sie die Rechte Schaltfläche aus, und halten Sie sie gedrückt. Geben Sie die Schaltfläche frei. |
| Select | Zeigen Sie auf den Controller, und ziehen Sie dann den-Server per Pull oder das Touchpad. | Schauen Sie sich das Ziel an, und drücken Sie dann ein. | Zeigen Sie die Maus, und klicken Sie dann mit der linken Maustaste. |
| Öffnen des Startmenüs | Drücken Sie die **Windows** -Taste. | Klicken Sie auf die Schaltfläche **Xbox** . | Drücken Sie die **Windows-Logo-Taste**. |
| Immersive app verlassen | Drücken Sie die **Windows** -Taste. Wählen Sie dann im Menü schnell Aktionen die Option **gemischte Reality-Startseite** aus. | Klicken Sie auf die Schaltfläche **Xbox** . Wählen Sie dann im Menü schnell Aktionen die Schaltfläche **Mixed Reality Home** aus. | Drücken Sie die Taste * * Windows-Taste. Wählen Sie dann im angezeigten Menü schnell Aktionen die Start Schaltfläche **Mixed Reality** aus. |
| Rotate | Verschieben Sie den Finger Stick nach links oder rechts. | Verschieben Sie den rechten Stift nach links oder rechts. | Nicht verfügbar. |
| Sichern | Verschieben Sie den Finger Stick abwärts. | Verschiebt den linken Rand nach hinten. | Nicht verfügbar. |
| Walk | Schieben Sie den Finger Stick direkt nach unten, und drücken Sie ihn in der Richtung, die Sie durchlaufen möchten. | Bewegen Sie den linken Stapel nach unten, und drücken Sie ihn in der Richtung, die Sie durchlaufen möchten. | Nicht verfügbar. |
| Verschieben eines App-Fensters | Zeigen Sie auf der APP-Leiste. Ziehen Sie den-Vorgang per Pull, um das Fenster zu erfassen, und verschieben Sie ihn dann mit dem Controller in eine beliebige Richtung. Geben Sie den Trigger frei. | Schauen Sie sich die APP-Leiste an, und halten Sie dann eine gedrückt, um das Fenster zu erfassen. Verwenden Sie den linken Strich, um das Fenster nebeneinander oder nach oben oder unten zu verschieben. Verwenden Sie die Trigger, um Sie näher und weiter Weg zu verschieben. Geben Sie dann eine frei. | Zeigen Sie mit der Maus auf die APP-Leiste. Halten Sie das Fenster mit der linken Maustaste gedrückt, und bewegen Sie es mit der Maus nebeneinander oder nach oben oder nach unten. Verwenden Sie das Mausrad, um das Fenster näher oder weiter Weg zu verschieben. Lassen Sie die Maustaste los. |
| Verschieben eines 3D-Objekts | Zeigen Sie auf das Objekt, und halten Sie den-und den-Wert, um ihn zu erfassen. Verschieben Sie Sie in eine beliebige Richtung mit dem Controller, und geben Sie dann den Trigger frei. | Schauen Sie sich das Objekt an, und halten Sie es gedrückt, um es zu erfassen. Verwenden Sie den linken Strich, um das Fenster nebeneinander oder nach oben oder unten zu verschieben. Verwenden Sie die Trigger, um Sie näher und weiter Weg zu verschieben. Geben Sie dann eine frei. | Zeigen Sie mit der Maus auf das-Objekt. Halten Sie die Maustaste gedrückt, und halten Sie sie gedrückt. verwenden Sie dann die Maus, um sie nebeneinander oder nach oben oder unten zu verschieben.  Verwenden Sie das Mausrad, um es näher oder weiter zu verschieben. Lassen Sie die Maustaste los. |
| Drehen oder Ändern der Größe eines App-Fensters | Zeigen Sie einen Controller auf der APP-Leiste und an einem anderen Controller an einer beliebigen Stelle im Fenster an. Halten Sie beide Trigger gedrückt, und verschieben Sie die Controller zum Ändern der Größe.  Um sich zu drehen, verschieben Sie einen Controller auf Sie und den anderen Weg von Ihnen. Geben Sie die Trigger frei. | Wählen Sie in der APP-Leiste die Option **Anpassen** aus. Betrachten Sie eine Ecke des Anpassungs Rahmens, und drücken Sie dann eine, um Sie auszuwählen. Verwenden Sie den linken Strich, um die Größe des Fensters zu ändern.  | Wählen Sie in der APP-Leiste die Option **Anpassen** aus. Wählen Sie eine Ecke des Anpassungs Rahmens aus, halten Sie sie gedrückt, und verwenden Sie die Maus, um die Größe des Fensters zu ändern. |
| Drehen oder Ändern der Größe eines 3D-Objekts | Zeigen Sie beide Controller auf das-Objekt. Halten Sie beide Trigger gedrückt, und verschieben Sie die Controller zum Ändern der Größe.  Um sich zu drehen, verschieben Sie einen Controller auf Sie und den anderen Weg von Ihnen. | Wählen Sie in der APP-Leiste **Anpassen** aus, und verschieben Sie das Objekt dann mit dem linken Stick. | Wählen Sie in der APP-Leiste **Anpassen** aus, und wählen Sie dann das Objekt aus, und verwenden Sie die Maus, um es zu verschieben. |
| Scrollen in einem App-Fenster | Pull und halten Sie den-Modus, und verschieben Sie den Controller dann nach oben oder unten.  | Verwenden Sie das D-Pad. | Verwenden Sie das Mausrad. |
| Vergrößern oder verkleinern im App-Fenster | Ziehen Sie beide Trigger, und verschieben Sie die Controller dann näher beieinander oder weiter auseinander. | Ziehen Sie den rechten Auslösers zum Vergrößern und den linken Auslösers. | Verwenden Sie das Mausrad, während Sie die STRG-Taste gedrückt halten. |
| Menü öffnen | Drücken Sie die **Menü** Schaltfläche. | Drücken Sie die **Menü** Schaltfläche. | Klicken Sie mit der rechten Maustaste. |

## <a name="what-do-the-vibrations-and-lights-mean"></a>Was bedeuten die Vibrationen und Lichter?

Ihr Controller kommuniziert damit, was er tut, indem er seine LED-Leuchten vibriert und blinbt.

|  Wenn Ihr Controller dies durchführt  |  Dies bedeutet Folgendes |
| --- | --- |
| LEDs einschalten, und der Controller wird einmal vibriert. | **Aktivieren** |  
| LEDs werden ausgeschaltet, und der Controller wird zweimal vibriert. | **Ausschalten** |
| LEDs blinken alle drei Sekunden | **Ruhezustand** |
| LEDs langsam, und der Controller wird einmal vibriert. | **Wechseln in den Paarmodus** |
| Der Controller wird einmal vibriert. | **Herstellen einer Verbindung mit Ihrem PC oder Trennen der Verbindung** |
| LEDs sind hell beleuchtet | **Controller, die von Headset verfolgt werden** |
| LEDs werden dimly beleuchtet | **Controller, die nicht von Headset verfolgt werden** |
| Der Controller wird dreimal vibriert und ausgeschaltet. | **Kritischer Akku Pegel** |
| Die äußeren und inneren Ringe von LEDs blinken in einem abwechselnden Muster | **Wird aktualisiert** |

## <a name="updating-motion-controllers-firmware"></a>Aktualisieren der Motion Controller-Firmware

* Wenn ein immersives Headset mit dem PC verbunden ist und eine neue Controller Firmware verfügbar ist, wird die Firmware bei Ihrer nächsten Aktivierung automatisch an die Motion-Controller übermittelt.
* Controller-Firmwareupdates werden mit einem Muster der Beleuchtung von LED-Quadranten in Zirkel Bewegung und 1-2 Minuten angezeigt. Firmwareupdates können gelegentlich bis zu 10 Minuten dauern. Dies deutet auf eine schlechte Bluetooth-Konnektivität oder einen Funk Eingriff hin.
* Für den Fall, dass das Firmwareupdate unterbrochen wird (ausgeschalteten Controller oder Akku läuft), wird der Vorgang beim nächsten Einschalten erneut versucht.
* Nachdem das Firmwareupdate abgeschlossen ist, werden die Controller neu gestartet und die Verbindung wieder hergestellt.
* Beide Controller sollten jetzt verbunden werden. Navigieren Sie zum Mixed Reality-Portal, um den Status Ihrer Controller zu überprüfen.
* Überprüfen Sie, ob Ihre Controller ordnungsgemäß funktionieren
  * Starten Sie das **Mixed Reality-Portal** , und geben Sie Ihr Mixed Reality-Start
  * Verschieben Sie Ihre Controller, und überprüfen Sie die Nachverfolgung, Test Schaltflächen und überprüfen Sie, ob die Wenn dies nicht der Fall ist, lesen Sie [den Abschnitt Problembehandlung für Motion Controller](motion-controller-problems.md) .

## <a name="faq"></a>Häufig gestellte Fragen

### <a name="how-can-i-check-battery-level"></a>Wie kann ich den Akku Pegel überprüfen?

*A: die Akku Ebene befindet sich auf umgekehrter Seite des virtuellen Modells, es gibt keinen Indikator für die physische Akku Ebene. Warten Sie nach dem Einschalten des Controllers einige Sekunden, bis der Lesevorgang stabilisiert wurde.*

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Können Sie diese Controller ohne ein Headset verwenden? Nur für die Eingabe des Joysticks/Auslösers/usw.

*A: nicht für universelle Windows-Anwendungen*

## <a name="filing-motion-controller-feedbackbugs"></a>Einreichen von Feedback/Fehlern in Motion Controller

Geben Sie uns Feedback im Feedback-Hub mit der Kategorie "Mixed Reality-> Input".

## <a name="see-also"></a>Weitere Informationen

- [HP-Controller in Unity](https://docs.microsoft.com/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
- [HP-Controller in Unreal](https://docs.microsoft.com/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
- [Die Community fragen](https://answers.microsoft.com)
- [Kontaktieren Sie uns zur Unterstützung](https://support.microsoft.com/contactus/)
- [Problembehandlung](troubleshooting-windows-mixed-reality.md)

Haben Sie Probleme mit ihren Motion-Controllern? [Hilfe erhalten](motion-controller-problems.md)