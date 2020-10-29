---
title: FAQs zu Motion Controller
description: Erweiterte Windows Mixed Reality-Problembehandlung, die über die standardmäßige Kundensupport Dokumentation hinausgeht.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, Motion Controllers
appliesto:
- Windows 10
ms.openlocfilehash: 2a45f16cfbe62cb1263fcb1a1e7f5c76ea0b9268
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685870"
---
# <a name="motion-controller-faqs"></a>FAQs zu Motion Controller

## <a name="general-questions"></a>Allgemeine Fragen

### <a name="what-do-the-vibrations-and-lights-mean"></a>Was bedeuten die Vibrationen und Lichter?

Der Ansichts Bund der LED und die Haptik geben den Zustand des Bewegungs Controllers an.

| State    | Dem Status zugeordnetes Verhalten | So erreichen Sie den Status | 
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Einschalten**               | LEDs aktivieren und Controller werden einmal vibriert. | Drücken Sie die Windows-Taste auf dem Controller für zwei Sekunden, um den Controller einzuschalten.  | 
| **Ausschalten**              |  LEDs werden ausgeschaltet, und der Controller wird zweimal vibriert. | Drücken Sie die Windows-Taste auf dem Controller vier Sekunden, um den Controller zu deaktivieren.   |
| **Ruhezustand**               |  LEDs werden im Ruhezustand alle drei Sekunden ausgeschaltet und blinkt. | Der Controller wechselt automatisch in den Ruhezustand, wenn er 30 Sekunden lang nicht erreicht wird. Der Controller wird aktiviert, wenn er Bewegung erkennt, es sei denn, das Gerät ist nicht mit dem Host-PC gekoppelt. Klicken Sie auf die Schaltfläche, um Sie in diesem Fall zu aktivieren. |
| **Pairing**                |  LEDs langsam, während Sie sich im Paarmodus befinden, und gehen beim Beenden des Paarmodus solide. Der Controller wird einmal ausgeführt, wenn die Kopplung erfolgreich war, oder dreimal, wenn die Kopplung nicht erfolgreich war und dann ein Timeout auftritt. | Halten Sie die Schaltfläche "Kopplung" in Akku Buchstaben für drei Sekunden gedrückt.     |
| **Der Controller verbindet/trennt die Verbindung mit dem PC.** |  Der Controller vibriert einmal auf der PC-Verbindung oder der Verbindungs Trennung. | Dies geschieht, wenn der Controller nach dem Einschalten erfolgreich eine Verbindung mit dem PC herstellt oder wenn der Controller während der Verwendung die Verbindung mit dem PC trennt.|
| **Niedriger Akku Pegel**      | Die Haptik wird deaktiviert, wenn der Akku niedrig ist (es gibt keine LED-Anzeige). Das Akku Indikator Symbol auf dem Controller Handle im Headset zeigt 1/4 voll, wenn der Akku niedrig ist. | Ersetzen Sie Ihre Batterien. | 
| **Kritischer Akku Pegel** |  Der Controller wird dreimal vibriert, wenn Sie ihn einschalten und dann automatisch ausschalten. Das Symbol für den Akku Indikator wird rot angezeigt. | Ersetzen Sie die Batterie. Wenn das Problem weiterhin besteht, stellen [Sie die Werkseinstellungen des Geräts wieder her](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) .|

### <a name="my-motion-controllers-arent-working-properly"></a>Meine Bewegungs Controller funktionieren nicht ordnungsgemäß.

Wenn Ihre [Bewegungs Controller](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) nicht funktionieren, keine Verbindung herstellen oder wenn Sie kein Image der Controller sehen, wenn Sie Ihr Headset verwenden, versuchen Sie Folgendes:
1. Stellen Sie sicher, dass Ihre Controller eingeschaltet sind. Um diese zu aktivieren, drücken Sie die Windows-Taste für zwei Sekunden.
2. Stellen Sie sicher, dass die Controller vollständig abgerechnet werden, und ersetzen Sie die Akkus, wenn Sie nicht sind.
3. Schalten Sie die Controller ein-und ausschalten, während Sie diese vor Ihnen halten. Drücken Sie die Windows-Taste vier Sekunden, um einen Controller zu deaktivieren, und halten Sie ihn zwei Sekunden lang wieder gedrückt, um ihn zu aktivieren. 
4. Wenn Ihre Controller mit Ihrem PC gekoppelt sind, wechseln Sie zu **Einstellungen > Geräte > Bluetooth & andere Geräte** , oder wechseln Sie zu **Geräte-Manager > menschlichen Schnittstellen Geräte > Motion Controller** . Stellen Sie sicher, dass die Controller als paarweise aufgeführt sind. Wenn dies nicht der Fall ist, koppeln [Sie Sie](motion-controller-problems.md#how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc). 
5. Stellen Sie sicher, dass die Motion-Controller als "verbunden" angezeigt werden. "Paarweise" bedeutet nicht notwendigerweise, dass die Controller mit dem PC verbunden sind. Controller sollten unter der Kategorie "Maus, Tastatur & Pen" angezeigt werden. Bewegungs Controller unter "andere Geräte" haben den paarungsprozess nicht bestanden und sind nicht funktionsfähig. Überprüfen der Motion Controllers-LEDs: hell leuchtende Controller sind paarweise gekoppelt und verbunden, dimly-Licht Controller sind nicht verbunden.
6. Wechseln Sie zu **Start > Mixed Reality-Portal** auf Ihrem PC, und wählen Sie "Menü" aus. Ihre Motion-Controller werden zusammen mit einer Statusmeldung angezeigt:
    * Bereit – die Controller sind alle festgelegt.
    * Verlorene Nachverfolgung – das gemischte Reality-Portal kann Ihre Controller nicht finden. Halten Sie diese vor dem Headset, und starten Sie Sie neu, indem Sie die Windows-Taste vier Sekunden lang drücken, und dann zwei Sekunden.
    * Niedrige Akkukapazität – ersetzen Sie die Controller-Akkus.
7. Wenn Sie einen externen USB-Bluetooth-Adapter verwenden, stellen Sie sicher, dass er an einen USB 2,0-Port angeschlossen ist (Sie sind häufig, jedoch nicht immer schwarz). Außerdem sollte Sie so weit wie möglich von anderen drahtlos Sendern oder USB-Speich erwerken angeschlossen werden, einschließlich des USB-Verbindungs-Connector für Ihr Headset. 
8. Um sicherzustellen, dass nur ein Bluetooth-Radio auf dem PC vorhanden ist, wechseln Sie zu **Geräte-Manager > Bluetooth** , und suchen Sie nach einem Adapter. Wenn Sie die Desktop-PC-Konfiguration mit dem integrierten Optionsfeld verwenden, überprüfen Sie, ob eine externe Antenne angeschlossen ist. Wenn keine externe Antenne verbunden ist, kann dies zu nach Verfolgungs Problemen führen. Oder verwenden Sie einen externen Bluetooth-Dongle (USB), deaktivieren Sie die interne Bluetooth-Funktion, und wiederholen Sie die Kopplung und Verbindung.
9. Wenn das Fenster Bluetooth-Einstellungen im Hintergrund geöffnet ist, werden viele zusätzliche Aufrufe an das Bluetooth-Protokoll durchgeführt. Schließen Sie es.
10. Überprüfen Sie die virtuelle Akku Ebene auf dem Bewegungs Controller, indem Sie die Controller in gemischter Realität einschalten, um das Akku Symbol anzuzeigen. Warten Sie ungefähr 15 Sekunden, bevor Sie die Ebene lesen, da die gemeldete Ebene unmittelbar nach dem Verbinden eines Controllers höher als die tatsächliche Ebene ist. Ersetzen Sie die Akkus, wenn das Symbol rot ist. 
11. Entfernen Sie Bluetooth-Kopfhörer und-Sprecher in den **Einstellungen > Geräte > Bluetooth & anderen Geräten** , und schalten Sie die Geräte aus. Verwenden Sie den Head Phone Jack oder die integrierten Referenten Ihres Mixed Reality-Headsets, um das beste Audioerlebnis zu erzielen.
12. Entfernen Sie andere Bluetooth-Geräte, die mit Ihrem PC gekoppelt werden können, z. b. Kopfhörer oder Gamepads. Wechseln Sie zu **Einstellungen > Geräte > Bluetooth & andere Geräte** , wählen Sie die Geräte aus, und klicken Sie dann auf "Gerät entfernen".
13. Entfernen Sie das USB-Kabel auf Ihrem Headset, und binden Sie es wieder in den PC ein, um Windows Mixed Reality neu zu starten.
14. Controller Leuchten blinken, wenn Sie ein Firmwareupdate durchlaufen. Warten Sie, bis das Update fertiggestellt ist und die Controller in gemischter Realität angezeigt werden.
15. Stellen Sie sicher, dass Ihr PC mit einem 5-GHz-WLAN verbunden ist. Wenn Ihr Laptop mit einem Netzwerk mit 2,4 GHz WiFi verbunden ist, wird die Bluetooth-Verbindung normalerweise gemeinsam genutzt. Dies kann sich je nach Produkt Entwurf negativ auf die WiFi-oder Bluetooth-Leistung auswirken. Ändern Sie das bevorzugte Band in den Netzwerkadapter Einstellungen in 5 GHz. Wenn Ihr Netzwerk 5 GHz nicht unterstützt, kann ein Bluetooth-Dongle anstelle der internen Bluetooth-Funktion verwendet werden.
16. Wenn die Bluetooth-Einstellungen Motion-Controller bereits gekoppelt haben, erkennt Windows die neuen Geräte erst, wenn diese entfernt werden (wenn Sie mit einem bestimmten Ring hinzugefügt wurden, können Sie nur mit diesem Dongle entfernt werden).
17. Wenn Ihr PC über eine integrierte Bluetooth-Verbindung verfügt und Verbindungsprobleme auftreten, versuchen Sie es mit einem USB-Bluetooth-Adapter. Deaktivieren Sie hierzu das integrierte Bluetooth-Radio in Geräte-Manager, und koppeln Sie Ihre anderen Bluetooth-Geräte mit dem neuen Adapter.

### <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>Meine Controller Jitter, bleiben hängen oder Flimmern und verschwinden in gemischter Realität. 

* Wenn Ihr PC mit 2,4 GHz WiFi ausgeführt wird, wechseln Sie zu 5 GHz WiFi. 
* Wenn Sie einen externen Bluetooth-Adapter verwenden, stellen Sie sicher, dass er an einen USB 2,0-Port angeschlossen ist (häufig, aber nicht immer, schwarz), von anderen drahtlos Sendern oder USB-Flash Laufwerken. 
* Führen Sie die Bluetooth-Problembehandlung unter **Einstellungen > aktualisieren & Sicherheit > Problembehandlung > Bluetooth** aus. 

### <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Der Controller befindet sich in einem unendlichen Neustart.

Dies ist ein kritischer Akku Indikator. Versetzen Sie neue Akkus in das Gerät, und [setzen Sie den Controller auf die Werkseinstellungen zurück](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings), falls das Problem weiterhin besteht.

### <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>Das gemischte Reality-Portal funktioniert, aber meine Controller sind schlecht nachverfolgt (Weg Weg, schütteln usw.).

1. Beleuchtungsbedingungen können sich auf die Nachverfolgung auswirken. Stellen Sie sicher, dass Sie nicht für direktes Sonnenlicht verfügbar sind und dass Sie nicht über viele Point Light-Quellen für Ihren HMD verfügen (z. b. Zeichen folgen mit Lichtern wie eine Weihnachts Struktur). 
2. Diese Symptome werden im Allgemeinen durch Fehler bei der Kommunikation zwischen dem Controller und dem Host-PC verursacht und weisen auf eine schlechte Bluetooth-Link Qualität hin. Siehe [Fragen zu Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Motion Controller-LEDs sind nicht beleuchtet, aber die Schaltflächen und der Finger Stick funktionieren weiterhin im Mixed Reality-Portal.

Der Verschiebe Cache für Motion Controller ist möglicherweise beschädigt. Um den Cache zu löschen, führen Sie den folgenden Befehl an einer Administrator Eingabeaufforderung aus:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Auf diesen Ordner kann in Windows Explorer nicht zugegriffen werden. er kann nur über eine Administrator Eingabeaufforderung geändert werden. Nachdem Sie den Ordner gelöscht haben, starten Sie den PC neu, und verbinden Sie Ihre Bewegungs Controller erneut, um die Kalibrierungs Dateien wiederherzustellen.

### <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Der Controller sieht wie ein "Vive/Oculus" aus, hat eine seltsame Ausrichtung, oder die Schaltflächen sind falsch zugeordnet.

Die Website verfügt wahrscheinlich nicht über vollständige Motion Controller-Unterstützung.

### <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Meine Bewegungs Controller werden nicht in den steamvr-apps und spielen angezeigt.

Stellen Sie zunächst sicher, dass die Akkus Ihres Controllers in Rechnung gestellt werden. Die Controller sind nicht funktionsfähig, wenn die Akkus nicht aktiv sind oder nicht. 

Wenn Sie Ihre Controller im Klippe-Haus, aber nicht in den steamvr-apps und-spielen sehen können, ist der Motion Controller-Modell Treiber möglicherweise nicht ordnungsgemäß installiert. So überprüfen Sie, ob der Motion Controller-Modell Treiber ordnungsgemäß installiert ist
1. Aktivieren Sie beide Motion-Controller. Wenn Ihre Controller mit Ihrem PC gekoppelt sind, wechseln Sie zu **Einstellungen > Geräte > Bluetooth & andere Geräte** , oder wechseln Sie zu **Geräte-Manager > menschlichen Schnittstellen Geräte > Motion Controller** . Stellen Sie sicher, dass Sie als "verbunden" angezeigt werden. Wenn Sie nicht als "paarweise" angezeigt werden, koppeln Sie [Sie](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality).
2. Wechseln Sie zu **Geräte-Manager > Bluetooth** , und suchen Sie nach "Motion Controller".
3. Wählen Sie das Gerät aus, und wechseln Sie dann zu **> Geräte nach Verbindung anzeigen** .
4. Wechseln Sie zu **System Einstellungen > Geräte > Bluetooth & anderen Geräten > anderen** Geräten, um festzustellen, ob Sie sichtbar sind. Es gibt zwei Geräte vom Typ "Bluetooth HID Device", und unter jedem Bluetooth-Gerät sollten Geräte mit dem Namen "Motion Controller" (mit grauen Symbolen) im selben Knoten wie der Bewegungs Controller verwendet werden.
5. Doppelklicken Sie auf jedes "Motion Controller"-Gerät, und navigieren Sie zur Registerkarte "Treiber". Vergewissern Sie sich, dass die aufgeführte Treiber Version einer [dieser Versionen](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history)entspricht.
6. Wenn dies nicht der Fall ist, führen Sie Windows Update aus, mit dem der Treiber automatisch heruntergeladen und installiert wird. Wenn Sie sich auf einem PC mit Unternehmensrichtlinien befinden oder Windows Update anderweitig eingeschränkt ist, müssen Sie möglicherweise den Motion Controller-Modell Treiber manuell installieren. Besuchen Sie hierzu [Diese Seite](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) , und suchen Sie nach der Treiber Version, die Ihrer Version von Windows 10 entspricht. Installationsanweisungen finden Sie auf der Downloadseite.

### <a name="the-controller-firmware-update-takes-significantly-longer-than-two-minutes"></a>Die Aktualisierung des Controller-Firmwareupdates dauert deutlich länger als zwei Minuten.

Überprüfen Sie den [Abschnitt Bluetooth-Fragen](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Die schlechte Qualität von Bluetooth-Verbindungen verursacht diese Probleme in der Regel.

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Ich habe gerade neue Akkus eingefügt, aber die virtuelle Akku Ebene des Controllers weist nicht den vollständigen Grad auf.

Die Akku Ebene des Bewegungs Controllers ist auf AA-Akkus optimiert. Einige Akkus mit niedriger Spannung können nicht als vollständig gemeldet werden, obwohl Sie vollständig abgerechnet werden.

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Der Touchpad meines Samsung Motion Controller ist offline oder verfügt über eine unzustellbare Stelle.

Dabei handelt es sich wahrscheinlich um einen Hardwarefehler, und Sie sollten sich für einen Austausch oder Austausch an Ihren Händler oder Gerätehersteller wenden.

### <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>Wie kann ich die Controller in den Werkseinstellungen wiederherstellen?

Stellen Sie Sie in den Werks Bedingungen wieder her (Sie benötigen neue Akkus):
1. Entfernen Sie die Controller, und schalten Sie Sie aus.
2. Öffnen Sie die Batterieabdeckung.
3. Fügen Sie Ihre neuen Akkus ein.
4. Halten Sie die Schaltfläche "Kopplung" gedrückt (die Registerkarte unten unter den Akkus).
5. Schalten Sie den Controller beim halten der Schaltfläche "Kopplung" ein, indem Sie die Windows-Schaltfläche fünf Sekunden lang gedrückt halten (beide Schaltflächen werden gedrückt).
6. Geben Sie die Schaltflächen frei, und warten Sie auf den Einschalten des Controllers. Dieser Vorgang dauert bis zu 15 Sekunden, und es gibt keine Indikatoren, wenn die Geräte Wiederherstellung stattfindet. Wenn Geräte direkt auf der Schaltflächen Freigabe einschalten, wurde die Schaltflächen Sequenz der Wiederherstellung nicht registriert, und Sie müssen den Vorgang wiederholen.
7. Wenn die Controller mit Ihrem PC gekoppelt wurden, wechseln Sie zu **Einstellungen > Bluetooth > andere Geräte** , und wählen Sie "Motion Controller" und "Gerät entfernen" aus, um die Controller Zuordnungen aus den Bluetooth-Einstellungen zu entfernen. 
8. Koppeln Sie [die Controller](set-up-windows-mixed-reality.md#if-you-need-to-pair-your-motion-controllers-with-your-pc) erneut mit dem Headset oder PC.
9. Nachdem eine Verbindung mit dem Host und dem Headset hergestellt wurde, wird das Gerät auf die neueste verfügbare Firmware aktualisiert.

### <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>Kann ich meinen Xbox-Controller mit meinem PC koppeln, damit ich ihn im Headset verwenden kann?

Sie können einen Bluetooth Xbox Controller für die Verwendung mit Ihrem Headset koppeln, indem Sie [diese Anweisungen](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)befolgen. 

Wenn Sie über einen kabelgebundenen Xbox-Controller verfügen, können Sie ihn an Ihren PC anschließen.

Bei manchen Spielen und Apps wird der Xbox-Controller anders verwendet als in gemischter Realität. Wenn Sie den Controller für ein Spiel oder eine APP verwenden möchten, wählen Sie in der APP-Leiste die Option "als Gamepad verwenden" aus, oder sagen Sie "verwenden als Gamepad". Um den Controller wieder in die gemischte Realität zu wechseln, wählen Sie "als Gamepad verwenden" erneut aus, oder sagen Sie "mit Blick verwenden". 



## <a name="if-your-motion-controllers-are-paired-to-your-headset"></a>Wenn Ihre Motion-Controller mit Ihrem Headset gekoppelt sind:

### <a name="should-i-pair-my-controllers-to-a-windows-mixed-reality-headset-that-has-built-in-bluetooth-radio"></a>Sollte ich meine Controller mit einem Windows Mixed Reality-Headset koppeln, das über eine integrierte Bluetooth Radio-Anwendung verfügt?

Einige Windows Mixed Reality-Headsets, einschließlich der Tools "Acer Ojo 500" und "Samsung Odyssee +", verfügen über integrierte Bluetooth-Radios für die Verwendung mit Motion-Controllern. Die Motion-Controller, die mit diesen Headsets geliefert werden, sind mit dem Headset von der Factory vorab gekoppelt, und es ist nicht erforderlich, dass Ihr PC über ein separates Bluetooth-Radio verfügt. Diese Motion-Controller _können_ manuell mit dem Bluetooth-Radio Ihres PCs gekoppelt werden, z. b. für die Verwendung mit Windows Mixed Reality-Headsets, die nicht über integrierte Bluetooth-Radios verfügen. 

### <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Gewusst wie neue Controller koppeln, wenn Windows Mixed Reality bereits auf meinem PC eingerichtet ist?
Wenn Sie Ihre Controller mit Ihrem Headset koppeln, verwenden Sie die Begleit-app (das [Mixed Reality-Portal](install-windows-mixed-reality.md#launch-mixed-reality-portal) kann Ihnen helfen, eine begleitende APP zu finden, die Sie auswählen können, oder eine Liste der begleitenden apps zu erhalten, aus denen Sie auswählen können).

### <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Meine gekoppelten Controller werden im Mixed Reality-Portal nicht angezeigt. 

* Halten Sie die Controller vor dem Headset, und starten Sie Sie neu, indem Sie die Windows-Taste vier Sekunden lang drücken, und dann zwei Sekunden lang wieder. 
* Wenn in **Geräte-Manager > Personal Interface-Geräte** "Motion Controller" angezeigt wird, durchlaufen Sie den paarweise Vorgang erneut. 
* Wenn es sich bei den Controller-LEDs um das Durchlaufen eines Quadranten und Ausschalten eines Quadranten und ausschalten handelt, wird ein Firmwareupdate durchgeführt. Warten Sie, bis das Update fertiggestellt ist und die Controller in gemischter Realität angezeigt werden. 
* Wenn ein externer Bluetooth-Adapter verwendet wird, stellen Sie sicher, dass der Adapter an einen USB 2,0-Port angeschlossen ist (der häufig, aber nicht immer schwarz ist), von anderen drahtlos Sendern oder USB 3,0-Geräten entfernt. 
* Wenn der PC gerade abgestürzt ist und ein Qualcomm-Adapter verwendet wird, funktioniert die zurück Setzung möglicherweise nicht. Um dieses Problem zu beheben, können Sie die Stromversorgung von der Rückseite des Computers entfernen (oder wenn Sie auf einem Laptop den Netzschalter 10 Sekunden gedrückt halten) und den PC neu starten. 
* Führen Sie die Bluetooth-Problembehandlung unter **Einstellungen > aktualisieren & Sicherheit > Problembehandlung > Bluetooth** aus.  

### <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>Wie kann ich meine Controller an Ihre Werks Kopplung zurückgeben?

Führen Sie die Geräte Begleit Anwendung des Headsets aus (z. b. die app "Acer Ojo 500" oder die app "Samsung HMD Odyssee + Setup", die bei der erstmaligen Anmeldung des Headsets automatisch installiert wird), um die Bewegungs Controller an Ihre Factory-Kopplung zurückzugeben, und befolgen Sie die Anweisungen für Motion Controller-Kopplung.



## <a name="if-your-motion-controllers-are-paired-to-your-pc"></a>**Wenn Ihre Motion-Controller mit Ihrem PC gekoppelt sind:**

### <a name="my-motion-controllers-are-not-pairing"></a>Meine Bewegungs Controller sind nicht paarkopplung. 

* Wenn die Controller nicht eingeschaltet werden, fügen Sie neue Akkus ein. Wenn dies nicht behoben wird, stellen Sie das Gerät in den Werkseinstellungen wieder her, indem Sie das Gerät einschalten, während Sie die paarschaltflächen gedrückt halten. Weitere Informationen finden Sie in den [Schritten zur Geräte Wiederherstellung](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) . 
* Wenn die Controller eingeschaltet sind und Sie einen externen Bluetooth-Adapter verwenden, stellen Sie sicher, dass der Adapter an einen USB 2,0-Port angeschlossen ist (häufig, aber nicht immer, schwarz), von anderen drahtlos Sendern oder USB-Flash Laufwerken. Wenn dies immer noch nicht funktioniert, führen Sie die Bluetooth-Problembehandlung unter Einstellungen > aktualisieren & Sicherheit > Problembehandlung > Bluetooth aus. 
* Wenn Sie einen Qualcomm-Adapter verwenden und der PC gerade abgestürzt ist, starten Sie den PC neu. 
* Versuchen Sie, die Motion-Controller, die nicht paargleich sind, nacheinander neu zu starten, und starten Sie dann den PC neu. 
* Der Motion Controller-Cache ist möglicherweise beschädigt. Informationen zum Beheben dieses Problems finden Sie in den folgenden [Schritten](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal). 
* Wenn das Problem mit keinem dieser Schritte behoben werden kann, wenden Sie sich an den Hersteller. 

### <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Meine gekoppelten Controller werden im Mixed Reality-Portal nicht angezeigt. 

* Halten Sie die Controller vor dem Headset, und starten Sie Sie neu, indem Sie die Windows-Taste vier Sekunden lang drücken, und dann zwei Sekunden lang wieder. 
* Wenn Ihre Controller in den **Einstellungen > Bluetooth & anderen Geräten** als verbunden angezeigt werden, entkoppeln Sie diese, und durchlaufen Sie den paarweise Vorgang erneut. 
* Wenn es sich bei den Controller-LEDs um das Durchlaufen eines Quadranten und Ausschalten eines Quadranten und ausschalten handelt, wird ein Firmwareupdate durchgeführt. Warten Sie, bis das Update fertiggestellt ist und die Controller in gemischter Realität angezeigt werden. 
* Wenn ein externer Bluetooth-Adapter verwendet wird, stellen Sie sicher, dass der Adapter an einen USB 2,0-Port angeschlossen ist (normalerweise schwarz), von anderen drahtlos Sendern oder USB 3,0-Geräten entfernt. 
* Wenn der PC gerade abgestürzt ist und ein Qualcomm-Adapter verwendet wird, funktioniert die zurück Setzung möglicherweise nicht. Um dieses Problem zu beheben, können Sie die Stromversorgung von der Rückseite des Computers entfernen (oder wenn Sie auf einem Laptop den Netzschalter 10 Sekunden gedrückt halten) und den PC neu starten. 
* Führen Sie die Bluetooth-Problembehandlung unter **Einstellungen > aktualisieren & Sicherheit > Problembehandlung > Bluetooth** aus.  

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Ich versuche, meine Controller zu koppeln, aber Sie werden nie im Menü "Hinzufügen eines neuen Geräts" in den Bluetooth-Einstellungen angezeigt.

Stellen Sie fest, dass die Controller nicht bereits gekoppelt sind. Wenn Sie dies tun, entfernen Sie Sie, und versuchen Sie es erneut. Starten Sie den PC neu, wenn das Problem weiterhin besteht. Wenn dies nicht möglich ist, finden Sie weitere [Informationen zu Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

### <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Gewusst wie neue Controller koppeln, wenn Windows Mixed Reality bereits auf meinem PC eingerichtet ist?

1. Fügen Sie zwei AA-Akkus in jeden Controller ein. Legen Sie die Akku Abdeckung noch nicht wieder ein.
2. Drücken Sie die Windows-Taste für zwei Sekunden, um die einzelnen Controller zu aktivieren. Sie werden sich bei der Aktivierung tummeln.
3. Versetzen Sie die Controller in den Paarmodus. Die Schaltfläche "Kopplung" befindet sich innerhalb des Akku Depots (siehe dieses [Bild](set-up-windows-mixed-reality.md#if-you-need-to-pair-your-motion-controllers-with-your-pc)). Halten Sie sie gedrückt, bis die Controller Beleuchtung blinkt.
4. Wechseln Sie zu **Einstellungen > Geräte > Bluetooth & andere Geräte** , und **fügen Sie dann Bluetooth oder ein anderes Gerät > Bluetooth hinzu** . Wenn die Controller angezeigt werden, wählen Sie diese zum Koppeln aus.

Hinweis: Wenn ein anderer Satz von Bewegungs Controllern mit Ihrem PC gekoppelt ist, müssen Sie diese Controller vor dem Koppeln der neuen Controller entkoppeln. Wenn Sie einen Satz von Bewegungs Controllern mit dem aktuellen PC gekoppelt haben und diese dann mit einem zweiten PC gekoppelt haben, müssen Sie die Verbindung mit dem aktuellen PC koppeln und erneut koppeln, bevor Sie ihn wieder verwenden.

### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Wie kann ich erkennen, ob ich Bluetooth-Technologie verwende?

Motion-Controller verwenden die gleiche Bluetooth-Technologie auf vielen consumergeräten und sind für die Arbeit mit der Bluetooth-Funktion auf dem neuesten PC konzipiert. Der PC sollte über Bluetooth Radio verfügen, wenn er die Kompatibilitätsprüfung mit gemischter Realität überschritten hat. So überprüfen Sie dies: 
* Öffnen Sie "Geräte-Manager". 
* Erweitern Sie den Abschnitt Bluetooth, und suchen Sie nach einem Adapter. 

![Screenshot eines Beispiel Geräte-Manager. Der Adapter ist das Bluetooth-Radio.](images/devicemanagerbtadapterpic.png) 

Wenn Ihr PC nicht über Bluetooth verfügt, empfiehlt es sich, den [plugbaren USB Bluetooth Bluetooth 4,0 Low Energy Micro-Adapter](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom)zu erhalten.

### <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi wird auf meinem Notebook verlangsamt, wenn Bewegungs Controller eingeschaltet werden.

Ihr Notebook kann seine WLAN-Antenne für Bluetooth freigeben, wenn eine Verbindung mit einem Zugriffspunkt mit 2,4 GHz besteht. Aktivieren Sie Geräte-Manager, wenn Sie die Band Einstellung auf 5 GHz umstellen können. Wenn ein Netzwerk mit 5 GHz nicht verfügbar ist und die Leistung stark beeinträchtigt ist, sollten Sie die Verwendung eines Bluetooth-Dongle in Erwägung gezogen.

![Die Auswahl Einstellungen für WiFi-Band können über den Geräte-Manager gefunden werden](images/wifi5ghz.png)

### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>Mein PC verfügt über Bluetooth-Technologie, aber ich habe Probleme mit meinen Controllern.

Motion-Controller sollten mit anderen Bluetooth-Tastaturen,-Mäusen und Spiel Controllern arbeiten, aber das Verhalten variiert abhängig vom Modell der Tastatur, der Maus oder des Spiel Controllers, den Sie verwenden. Im folgenden finden Sie einige Möglichkeiten, um die Leistung zu verbessern:
* Wenn Ihr Computer über Bluetooth verfügt, Sie aber weiterhin Probleme mit den Motion-Controllern haben, empfiehlt es sich, Ihr Bluetooth-Radio durch einen steckbaren externen Bluetooth-Adapter zu ersetzen, der an USB angeschlossen ist Es kann jeweils nur ein Bluetooth-Funk Adapter aktiv sein. Wenn Sie ein externes Radio zusätzlich zu einem vorhandenen Radio anschließen, müssen Sie das vorhandene Bluetooth-Radio in Geräte-Manager deaktivieren (Klicken Sie mit der rechten Maustaste auf den Adapter, und wählen Sie "Gerät deaktivieren"), und verwenden Sie alle ihrer vorherigen Bluetooth-Geräte erneut.
* Wenn Sie einen USB-Bluetooth-Adapter verwenden, verbinden Sie ihn mit einem USB 2,0-Port (2,0 Ports sind häufig schwarz und sind nicht als "SS" gekennzeichnet), falls verfügbar. Der Port sollte physisch von folgenden getrennt getrennt werden:
    - der HMD-USB-Connector
    - Flash Laufwerke
    - Festplatten
    - bei drahtlosen USB-Empfängern, wie z. b. bei Tastaturen/Mäusen, wird der USB-Bluetooth-Adapter so weit wie möglich von diesen anderen Connectors an die gegenüberliegende Seite des Computers angeschlossen.
* Schließen Sie das Fenster Bluetooth-Einstellungen, wenn es geöffnet ist. Wenn Sie es im Hintergrund geöffnet belassen, werden viele zusätzliche Aufrufe an das Bluetooth-Protokoll durchgeführt.
* Wenn Ihr Headset mit Ihrem PC gekoppelt ist, verwenden Sie den Windows Bluetooth-Treiber Stapel, und installieren Sie keine Bluetooth-Treiber Stapel von Drittanbietern. Drittanbieter Software funktioniert möglicherweise nicht ordnungsgemäß.
* Deaktivieren Sie die Einstellung "Benachrichtigung zum Herstellen einer Verbindung mit dem SWIFT-paar anzeigen" unter "Bluetooth-& andere Geräte", um die Aktivität für das Radio Scannen von
* Wenn Sie eine interne Bluetooth-Karte verwenden, stellen Sie sicher, dass Sie eine externe Bluetooth-Antenne verwenden oder dass Probleme bei der Überwachung auftreten. Wenn dies nicht funktioniert, verwenden Sie nach dem Deaktivieren des internen Bluetooth einen externen Bluetooth-Dongle (USB).
* Das Gerät sollte in den Bluetooth-Einstellungen unter der Kategorie "Maus, Tastatur & Pen" angezeigt werden. Wenn Sie sich unter "andere Geräte" befindet, entkoppeln und koppeln Sie das Gerät.
* Hiermit können Sie Bluetooth-Kopfhörer und-Sprecher entfernen, entkoppeln und ausschalten. Diese werden in der gemischten Realität von Windows nicht unterstützt. Verwenden Sie den Head Phone Jack oder die integrierten Referenten Ihres Mixed Reality-Headsets, um das beste Audioerlebnis zu erzielen.

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>Der zweite Controller benötigt lange Zeit, um die Verbindung wiederherzustellen.

Bei einigen älteren Intel-Radios tritt dieses Problem auf, wenn Bewegungs Controller gleichzeitig eingeschaltet werden. Vermeiden Sie das Einschalten von Controllern gleichzeitig.

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Mein Qualcomm-Bluetooth-Radio kann nach einem PC-Absturz keine Controller koppeln.

Qualcomm (QCA) für Bluetooth-Funk Treiber vor 10.0.0.448 kann nach einem Windows-Absturz zu einem ungültigen Status führen. Schalten Sie den PC vollständig aus, um dieses Problem zu umgehen. 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Ich sehe eine schlechte Controller Verfolgung mit "Marvell Radio".

Wechseln Sie zu **Geräte-Manager > Bluetooth > Marvell Avastar Bluetooth Radio Adapter > Properties > Driver** , und stellen Sie sicher, dass Sie Driver 15.68.9210.47 oder höher verwenden.
