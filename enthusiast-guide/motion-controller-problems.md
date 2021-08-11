---
title: Häufig gestellte Fragen zu Motion Controller
description: Controller Windows Mixed Reality Problembehandlung, die über unsere Standarddokumentation zur Kundenunterstützung hinausgeht.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support, Motion-Controller
appliesto:
- Windows 10
ms.openlocfilehash: e477ed07e20fb06e270c9a6e13e20defecfc6328896983ed12c4b79ea2197e44
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219745"
---
# <a name="motion-controller-faqs"></a>Häufig gestellte Fragen zu Motion Controller

## <a name="what-do-the-vibrations-and-lights-mean"></a>Was bedeuten Schwingungen und Licht?

Led-Ring und Haptik geben den Zustand des Motion-Controllers an.

| State    | Dem Zustand zugeordnetes Verhalten | Abrufen/Aussteigen des Zustands |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Einschalten**               | LEDs werden eingeschaltet, und der Controller vibriert einmal. | Halten Sie die Windows-Taste auf dem Controller zwei Sekunden lang gedrückt, um den Controller zu aktivieren.  |
| **Ausschalten**              |  LEDs werden ausgeschaltet, und der Controller vibriert zweimal. | Halten Sie die Windows-Taste auf dem Controller vier Sekunden lang gedrückt, um den Controller zu deaktivieren.   |
| **Schlafen**               |  LEDs werden im Ruhezustand alle drei Sekunden deaktiviert und blinken. | Der Controller wechselt automatisch in den Ruhezustand, wenn er 30 Sekunden lang bewegungslos ist. Der Controller wird aktiviert, wenn er Bewegung erkennt, es sei denn, das Gerät ist nicht mit dem Host-PC gekoppelt. Drücken Sie die Schaltfläche, um sie in diesem Fall zu reaktiven. |
| **Paarung**                |  LEDs werden im Kopplungsmodus langsam geimt und beim Beenden des Kopplungsmodus voll. Der Controller vibriert einmal, wenn die Kopplung erfolgreich war, oder dreimal, wenn die Kopplung nicht erfolgreich war, und dann tritt ein Times out auf. | Drücken Und halten Sie die Kopplungsschaltfläche im Akkufall drei Sekunden lang gedrückt.     |
| **Controller stellt eine Verbindung mit dem PC her bzw. trennt die Verbindung mit dem PC.** |  Der Controller vibriert einmal über die PC-Verbindung oder die Trennung. | Tritt ein, wenn der Controller erfolgreich eine Verbindung mit dem PC herstellt, nachdem Sie ihn eingeschaltet haben, oder wenn der Controller während der Verwendung die Verbindung mit dem PC trennt.|
| **Niedriger Akkustand**      | Haptik ist deaktiviert, wenn der Akku niedrig ist (es gibt keine LED-Anzeige). Das Akkuindikatorsymbol auf dem Controllerhandle im Headset zeigt 1/4 voll an, wenn der Akku niedrig ist. | Ersetzen Sie Ihre Akkus. | 
| **Kritischer Akkustand** |  Der Controller vibriert dreimal, wenn Sie ihn einschalten, und schaltet ihn dann automatisch aus. Das Akkuindikatorsymbol wird rot. | Ersetzen Sie die Akkus. Wenn das Problem weiterhin besteht, [stellen Sie das Gerät auf die Werkseinstellungen wieder](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) her.|

## <a name="my-motion-controllers-arent-working-properly"></a>Meine Motion-Controller funktionieren nicht ordnungsgemäß.

Wenn Ihre [Motion-Controller](controllers-in-wmr.md) nicht funktionieren, keine Verbindung herstellen oder ein Bild der Controller anzeigen, wenn Sie Ihr Headset umschließen:

1. Stellen Sie sicher, dass Ihre Controller aktiviert sind. Um sie zu aktivieren, drücken und halten Sie die Windows Zwei Sekunden lang gedrückt.
2. Stellen Sie sicher, dass die Controller vollständig in Rechnung gestellt werden, und ersetzen Sie die Akkus, falls dies nicht der Fall ist.
3. Schalten Sie die Controller aus und wieder ein, während Sie sie vor Sich halten. Halten Sie die schaltfläche Windows vier Sekunden lang gedrückt, um einen Controller zu deaktivieren. Drücken Sie , und halten Sie es zwei Sekunden lang erneut, um es zu aktivieren.
4. Überprüfen Sie, ob Ihre Motion-Controller [ordnungsgemäß gekoppelt](controllers-in-wmr.md#pair-motion-controllers)sind.
5. Überprüfen Sie die LEDs der Motion-Controller: Hell beleuchtete Controller sind gekoppelt und verbunden, schwach leuchtete Controller sind nicht verbunden.
6. Wechseln **Sie** zu Start > Mixed Reality-Portal auf Ihrem PC, und wählen Sie "Menü" aus. Ihre Motion-Controller sollten zusammen mit einer Statusmeldung aufgeführt werden:
    * Bereit: Die Controller sind alle festgelegt.
    * Verlorene Nachverfolgung: Mixed Reality-Portal können Ihre Controller nicht finden. Halten Sie sie vor Ihrem Headset, und starten Sie sie neu, indem Sie vier Sekunden lang die schaltfläche Windows und dann zwei Sekunden lang erneut drücken.
    * Niedrige Akkukapazität: Ersetzen Sie die Controllerakkus.
7. Wenn Sie einen externen USB Bluetooth Adapter verwenden, stellen Sie sicher, dass er an einen USB 2.0-Anschluss angeschlossen ist (diese sind häufig, aber nicht immer schwarz). Es sollte auch so weit wie möglich von anderen Funksendern oder USB-Speichersticks angeschlossen werden, einschließlich des USB-Anschlusses für Ihr Headset. 
8. Wechseln Sie zu **Geräte-Manager > Bluetooth,** und suchen Sie nach einem Adapter, um zu überprüfen, ob nur ein Bluetooth Radio auf dem PC vorhanden ist. Wenn Sie die Desktop-PC-Konfiguration mit integriertem Radio verwenden, überprüfen Sie, ob eine externe Antenne verbunden ist. Wenn keine externe Antenne verbunden ist, kann dies zu Nachverfolgungsproblemen führen. Alternativ können Sie einen externen Bluetooth Dongle (USB) verwenden, die interne Bluetooth-Funktion deaktivieren und das Koppeln und Verbinden wiederholen.
9. Wenn das Bluetooth Einstellungsfenster im Hintergrund geöffnet ist, werden viele zusätzliche Aufrufe an das Bluetooth-Protokoll durchgeführt. Schließen Sie es.
10. Überprüfen Sie den virtuellen Akkustand auf dem Motion Controller, indem Sie die Controller in Mixed Reality umschalten, um das Akkusymbol anzuzeigen. Warten Sie ungefähr 15 Sekunden, bevor Sie die Ebene lesen, da die gemeldete Ebene unmittelbar nach dem Herstellen der Verbindung mit einem Controller höher als die tatsächliche Ebene ist. Ersetzen Sie die Akkus, wenn das Symbol rot ist.
11. Entfernen Sie Bluetooth Geräte und Lautsprecher in **Einstellungen > Geräte > Bluetooth & anderen Geräten,** und deaktivieren Sie die Geräte. Verwenden Sie die Kabelbuchse oder die integrierten Lautsprecher auf Ihrem Mixed Reality-Headset, um ein optimales Audioerlebnis zu gewährleisten.
12. Entfernen Sie andere Bluetooth Geräte, die mit Ihrem PC gekoppelt werden können, z. B. Brillen oder Gamepads. Wechseln Sie zu **Einstellungen > Geräte > Bluetooth & anderen Geräten,** wählen Sie die Geräte und dann "Gerät entfernen" aus.
13. Trennen Sie das USB-Kabel an Ihrem Headset, und schließen Sie es wieder an den PC an, um Windows Mixed Reality neu zu starten.
14. Controllerlichter blinken, wenn sie einem Firmwareupdate unterzogen werden. Warten Sie, bis das Update abgeschlossen ist, und die Controller sollten in Mixed Reality angezeigt werden.
15. Stellen Sie sicher, dass Ihr PC mit einem Wi-Fi Netzwerk mit 5 GHz verbunden ist. Wenn Ihr Laptop mit einem Wi-Fi-Netzwerk mit 2,4 GHz verbunden ist, wird in der Regel die Bluetooth Verbindung freigegeben. Dies kann sich je nach Produktentwurf negativ auf Wi-Fi oder Bluetooth Leistung auswirken. Ändern Sie das bevorzugte Band in den Netzwerkadaptereinstellungen auf 5 GHz. Wenn Ihr Netzwerk 5 GHz nicht unterstützt, kann anstelle der internen Bluetooth Funktion ein Bluetooth Dongle verwendet werden.
16. Wenn ihre Bluetooth-Einstellungen bereits mit Motion-Controllern gekoppelt sind, werden Windows die neuen Geräte erst ermitteln, wenn diese entfernt wurden. Wenn sie mit einem bestimmten Dongle hinzugefügt wurden, können sie nur mit diesem Dongle entfernt werden.
17. Wenn Ihr PC über integrierte Bluetooth verfügt und Verbindungsprobleme auftreten, versuchen Sie, einen USB-Bluetooth-Adapter zu verwenden. Deaktivieren Sie hierzu das integrierte Bluetooth Radio in Geräte-Manager, und koppeln Sie dann Ihre anderen Bluetooth Geräte mit dem neuen Adapter.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>Meine Controller jittern, hängen bleiben oder flackern und verschwinden in Mixed Reality

* Wenn Ihr PC mit WLAN mit 2,4 GHz ausgeführt wird, wechseln Sie zu WLAN mit 5 GHz. 
* Wenn Sie einen externen Bluetooth Adapter verwenden, stellen Sie sicher, dass er an einen USB 2.0-Anschluss angeschlossen ist (der häufig, aber nicht immer schwarz ist), und zwar unabhängig von anderen Funksendern oder USB-Speichersticks.
* Führen Sie die Bluetooth-Problembehandlung in **Einstellungen > Update & Security > Troubleshoot > Bluetooth aus.**

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Mein Controller bleibt in einem unendlichen Neustart hängen

Dies ist ein kritischer Akkuindikator. Legen Sie neue Akkus in das Gerät ein, und setzen [Sie den Controller auf die Werkseinstellungen zurück,](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)wenn das Problem weiterhin besteht.

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>Die Mixed Reality-Portal funktioniert, aber meine Controller werden schlecht nachverfolgt (verwaschen, verwaschen usw.).

1. Beleuchtungsbedingungen können sich auf die Nachverfolgung auswirken. Stellen Sie sicher, dass Sie nicht für direkte Strahle verfügbar sind und nur minimale Punktlichtquellen für Ihre HMD sichtbar sind (z. B. Zeichenfolgen von Beleuchtungen wie eine Strahlbaumstruktur).
2. Diese Symptome werden durch Fehler bei der Kommunikation zwischen dem Controller und dem Host-PC verursacht und weisen auf eine schlechte Bluetooth Linkqualität hin. Weitere Informationen finden Sie unter [Fragen zu Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Motion-Controller-LEDs werden nicht leuchtet, aber die Schaltflächen und der Fingerabdruck funktionieren weiterhin in Mixed Reality-Portal

Der Motion Controller-Kalibrierungscache ist möglicherweise beschädigt. Führen Sie den folgenden Befehl an einer Administratoreingabeaufforderung aus, um den Cache zu löschen:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Auf diesen Ordner kann in Windows Explorer nicht zugegriffen werden und kann nur über eine Administratoreingabeaufforderung geändert werden. Nachdem Sie den Ordner gelöscht haben, starten Sie Ihren PC neu, und verbinden Sie die Motion Controller erneut, um die Kalibrierungsdateien wiederherzustellen.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Mein Controller sieht wie ein Vive-/Oculus-Controller aus, weist eine ungewöhnliche Ausrichtung auf, oder die Schaltflächen sind falsch zugeordnet.

Die Website verfügt wahrscheinlich nicht über vollständige Motion Controller-Unterstützung.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Meine Motion-Controller werden nicht in SteamVR-Apps und -Spielen angezeigt.

Stellen Sie zunächst sicher, dass die Akkus Ihres Controllers in Rechnung gestellt werden. Die Controller funktionieren nicht, wenn die Akkus nicht mehr in der Bzw. in der 2000er-30-Jahre sind.

Wenn Sie Ihre Controller in der Haus an den Klippen, aber nicht in Denk-Apps und -Spielen sehen können, ist der Motion Controller-Modelltreiber möglicherweise nicht ordnungsgemäß installiert. So überprüfen Sie, ob der Motion Controller-Modelltreiber ordnungsgemäß installiert ist:

1. Schalten Sie beide Motion-Controller ein. Überprüfen Sie, ob Ihre Motion-Controller [ordnungsgemäß gekoppelt sind.](controllers-in-wmr.md#pair-motion-controllers)
2. Wechseln Sie **zu Geräte-Manager > Human Interface Devices,und** suchen Sie nach "Motion controller".
3. Doppelklicken Sie auf jedes Motion Controller-Gerät, und wechseln Sie zur Registerkarte "Treiber". Vergewissern Sie sich, dass die aufgeführte Treiberversion einer dieser [Versionen entspricht.](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history)
4. Wenn die Treiberversion nicht passt oder Sie kein Gerät mit dem Namen "Motion Controller" finden, führen Sie Windows Update aus.  Dadurch wird der Treiber automatisch heruntergeladen und installiert. Wenn Sie sich auf einem PC mit Unternehmensrichtlinien oder Windows Update anderweitig eingeschränkt sind, müssen Sie den Motion Controller-Modelltreiber möglicherweise manuell installieren. Besuchen Sie hierzu diese Seite, [und](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) suchen Sie nach der Treiberversion, die Ihrer Controllerhardware entspricht. Installationsanweisungen finden Sie auf der Downloadseite.

## <a name="the-controller-firmware-update-takes-longer-than-two-minutes"></a>Das Firmwareupdate des Controllers dauert länger als zwei Minuten.

Sehen Sie sich [Bluetooth Abschnitt fragen an.](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) Eine schlechte Bluetooth Linkqualität führt in der Regel zu diesen Problemen.

## <a name="i-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Ich habe neue Akkus eingefügt, aber der virtuelle Akkustand des Controllers gibt nicht den vollständigen Akkustand an.

Der Akkustand des Bewegungscontrollers ist auf AA-Akkus optimiert. Einige Akkus mit niedriger Spannung werden möglicherweise nicht als voll bezeichnet, obwohl sie vollständig aufgeladen sind.

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Das Touchpad meines Samsung-Motion-Controllers ist nicht zentriert oder hat einen unorten Ort.

Dies ist wahrscheinlich ein Hardwarefehler, und Sie sollten zu Ihrem Einzelhändler oder Gerätehersteller zurückwechseln, um einen Austausch oder Austausch zu erhalten.

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>Wie kann ich die Controller in den Factoryeinstellungen wiederherstellen?

Stellen Sie sie auf werksseitig wiederherstellen (Sie benötigen neue Akkus):

1. Trennen Sie die Controller, und stellen Sie sie aus.
2. Öffnen Sie die Akkuabdeckung.
3. Fügen Sie Ihre neuen Akkus ein.
4. Halten Sie die Kopplungsschaltfläche gedrückt (die Registerkarte unten unter den Akkus).
5. Wenn Sie die Kopplungsschaltfläche gedrückt halten, können Sie den Controller einschalten, indem Sie die Windows fünf Sekunden lang gedrückt halten (halten Sie beide Schaltflächen gedrückt).
6. Lassen Sie die Schaltflächen frei, und warten Sie, bis der Controller einschalten kann. Dies dauert bis zu 15 Sekunden, und es gibt keine Indikatoren, wenn die Gerätewiederherstellung erfolgt. Wenn das Gerät sofort beim Losschalten einschaltet, wurde die Sequenz der Wiederherstellungsschaltfläche nicht registriert, und Sie müssen es erneut versuchen.
7. Wenn die Controller mit Ihrem PC gekoppelt wurden, wechseln Sie zu **Einstellungen > Bluetooth >** anderen Geräten, und wählen Sie "Motion Controller" und "Remove device" (Gerät entfernen) aus, um Controllerzuordnungen aus Bluetooth entfernen.
8. [Koppeln Sie die](controllers-in-wmr.md#pair-motion-controllers) Controller erneut mit dem Headset oder PC.
9. Nach dem Herstellen der Verbindung mit dem Host und headset wird das Gerät auf die neueste verfügbare Firmware aktualisiert.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>Kann ich meinen Xbox-Controller mit meinem PC koppeln, damit ich ihn im Headset verwenden kann?

Sie können einen xbox Bluetooth controller koppeln, um ihn mit Ihrem Headset zu verwenden, indem Sie diese [Anweisungen befolgen.](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)

Wenn Sie über einen kabelgebundenen Xbox-Controller verfügen, schließen Sie ihn an Ihren PC an.

Einige Spiele und Apps verwenden den Xbox-Controller anders als in Mixed Reality. Um den Controller für ein Spiel oder eine App zu verwenden, wählen Sie "Als Gamepad verwenden" in der App-Leiste aus, oder sagen Sie "Als Gamepad verwenden". Um den Controller wieder zu Mixed Reality zu wechseln, wählen Sie erneut "Als Gamepad verwenden" aus, oder sagen Sie "Mit Anvisieren verwenden". 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Gewusst wie neue Controller koppeln, wenn Windows Mixed Reality auf meinem PC bereits eingerichtet ist

Wenn Sie Ihre Controller mit Ihrem Headset koppeln, verwenden Sie die Begleit-App (die [Mixed Reality-Portal](install-windows-mixed-reality.md#launch-mixed-reality-portal) kann Ihnen helfen, eine Begleit-App zu finden, um sie zu starten, oder Eine Liste der Begleit-Apps, aus denen Sie auswählen können).

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>Wie kann ich meine Controller an die Factorykopplung zurückgeben?

Führen Sie die Begleit-App des Headsets aus, und befolgen Sie die Anweisungen für die Motion Controller-Kopplung, um die Motion-Controller wieder in die Werkskopplung oder mit einem Windows Mixed Reality-Headset mit integriertem Bluetooth-Radio zu koppeln. Beispielsweise wird die App "Acer OJO 500" oder die App "Samsung HMDIgeny+ Setup" automatisch installiert, wenn das Headset zum ersten Mal angeschlossen wird.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>Meine Motion-Controller sind nicht mit meinem PC gekoppelt

* Wenn die Controller nicht ein aktivieren, fügen Sie neue Akkus ein. Wenn dies nicht behoben wird, stellen Sie die Werkseinstellungen des Geräts wieder wieder auf, indem Sie das Gerät einschalten, während Sie die Kopplungstasten halten. Weitere Informationen finden Sie in den Schritten [zur Gerätewiederherstellung.](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)
* Wenn die Controller während der Verwendung eines externen Bluetooth-Adapters ein-/aus aktivieren, stellen Sie sicher, dass der Adapter an einen USB 2.0-Anschluss angeschlossen ist (der häufig, aber nicht immer schwarz ist), weg von anderen Funkverteilern oder USB-Flashlaufwerken. Wenn es immer noch nicht funktioniert, führen Sie die Problembehandlung für Bluetooth in Einstellungen > Update & Security > Problembehandlung > Bluetooth.
* Wenn Sie einen Qualcomm-Adapter verwenden und der PC gerade abgestürzt ist, starten Sie den PC neu.
* Versuchen Sie, die Motion-Controller, die nicht gekoppelt sind, nach und nach neu zu starten, und starten Sie dann den PC neu.
* Der Motion Controller-Cache ist möglicherweise beschädigt. Informationen zum Beheben dieses Problems finden Sie in den [folgenden Schritten.](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)
* Wenn das Problem durch Schritte behoben wird, wenden Sie sich an den Hersteller.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Meine gekoppelten Controller werden nicht in der Mixed Reality-Portal

* Halten Sie die Controller vor Ihrem Headset, und starten Sie sie neu, indem Sie die Windows vier Sekunden lang und dann erneut für zwei Sekunden drücken.
* Wenn Ihre Controller als verbunden anzeigen, entpaaren Sie sie, und gehen Sie den [Kopplungsprozess erneut](controllers-in-wmr.md#pair-motion-controllers) durch.
* Wenn die Controller-LEDs gleichzeitig mit einem Quadranten von Licht ein- und ausgeschaltet werden, wird ein Firmwareupdate durchlaufen. Warten Sie, bis das Update abgeschlossen ist, und die Controller sollten in der Mixed Reality.
* Wenn ein externer Bluetooth-Adapter verwendet wird, stellen Sie sicher, dass der Adapter an einen USB 2.0-Anschluss (schwarz) angeschlossen ist, der von anderen Funksendern oder USB 3.0-Geräten entfernt ist.
* Wenn der PC gerade abgestürzt ist und ein Qualcomm-Adapter verwendet wird, funktioniert ein Zurücksetzen möglicherweise nicht. Um dies zu beheben, trennen Sie die Stromversorgung von der Rückseite des Computers (oder halten Sie den Netzschalter 10 Sekunden lang gedrückt), und starten Sie den PC neu.
* Führen Sie die Bluetooth Problembehandlung in Einstellungen > **Update & Security > Troubleshoot > Bluetooth**.  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Ich versuche, meine Controller zu koppeln, aber sie werden nie im Menü "Neues Gerät hinzufügen" in den Bluetooth angezeigt.

Überprüfen Sie, ob Controller noch nicht gekoppelt sind. Entfernen Sie die Dateien, und versuchen Sie es erneut. Starten Sie den PC neu, wenn das Problem weiterhin besteht. Wenn dies fehlschlägt, finden Sie [weitere Informationen Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

Hinweis: Wenn eine andere Gruppe von Motion-Controllern mit Ihrem PC gekoppelt ist, müssen Sie diese Controller entkopplungen, bevor Sie neue Kopplungen erstellen. Wenn Sie eine Gruppe von Motion-Controllern mit Ihrem aktuellen PC gekoppelt und dann mit einem zweiten PC gekoppelt haben, müssen Sie die Kopplung wieder mit dem aktuellen PC koppeln, bevor Sie sie erneut verwenden.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Wie kann ich feststellen, ob ich eine Bluetooth

Motion-Controller verwenden dieselbe Bluetooth-Technologie wie viele Consumergeräte und sind für die Verwendung der Bluetooth-Funktion konzipiert, die in jedem aktuellen PC enthalten ist. Ihr PC sollte über Bluetooth verfügen, wenn er die Mixed Reality-Kompatibilitätsprüfung bestanden hat. So überprüfen Sie dies:

* Öffnen Sie "Geräte-Manager".
* Erweitern Sie Bluetooth Abschnitt , und suchen Sie nach einem Adapter.

![Screenshot einer Beispiel-Geräte-Manager. Der Adapter ist das Bluetooth Funkgerät.](images/devicemanagerbtadapterpic.png)

Wenn Ihr PC nicht über Bluetooth, verwenden Sie pluggable USB Bluetooth 4.0 Low Energy Micro Adapter.

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi in meinem Notebook verlangsamt, wenn Motion Controller eingeschaltet sind

Ihr Notebook kann seine Wi-Fi an Bluetooth, wenn es mit einem 2,4-GHz-Zugriffspunkt verbunden ist. Überprüfen Sie Geräte-Manager, ob Sie die Bandeinstellung auf 5 GHz umschalten können. Wenn ein 5-GHz-Netzwerk nicht verfügbar ist und die Leistung stark beeinträchtigt ist, sollten Sie einen Bluetooth verwenden.

![Einstellungen für die WLAN-Bandauswahl finden Sie im Geräte-Manager.](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>Mein PC verfügt über Bluetooth-Technologie, aber ich habe Probleme mit meinen Controllern.

Motion-Controller sollten mit anderen Bluetooth Tastaturen, Mausen und Gamecontrollern funktionieren. Die Benutzererfahrung hängt vom Modell der Tastatur, Maus oder des Spielcontrollers ab, den Sie verwenden. Hier sind einige Dinge, die Sie tun können, um die Leistung zu verbessern:

* Wenn Ihr Computer Bluetooth aber weiterhin Probleme mit den Motion-Controllern haben, sollten Sie das Bluetooth-Radio durch einen austauschbaren externen Bluetooth-Adapter ersetzen, der an USB angeschlossen ist. Sie können nur einen Bluetooth gleichzeitig aktiv haben. Wenn Sie ein externes Radio zusammen mit einem vorhandenen Radio einstecken, müssen Sie ihr vorhandenes Radio Bluetooth in Geräte-Manager. Klicken Sie mit der rechten Maustaste auf den Adapter, und wählen Sie "Gerät deaktivieren" aus, und entppeln/koppeln Sie alle Ihre vorherigen Bluetooth Geräte.
* Wenn Sie einen USB-Bluetooth-Adapter verwenden, verbinden Sie ihn mit einem USB 2.0-Anschluss (2.0-Ports sind häufig schwarz und werden nicht als "SS" bezeichnet), sofern verfügbar. Der Port sollte physisch von Folgenden getrennt werden:
    - HMD-USB-Anschluss
    - Flashlaufwerke
    - Festplatten
    - DRAHTLOSE USB-Empfänger wie bei Tastaturen/Mauszeigen Im Idealfall schließen Sie den USB-Bluetooth-Adapter so weit wie möglich von diesen anderen Anschlüssen an die gegenüberliegende Seite des Computers an.
* Schließen Sie Bluetooth Fenster "Einstellungen", wenn es geöffnet ist. Wenn sie im Hintergrund geöffnet wird, werden viele zusätzliche Aufrufe an das Bluetooth ausgeführt.
* Wenn Ihr Headset mit Ihrem PC gekoppelt ist, verwenden Sie den Windows Bluetooth-Treiberstapel, und installieren Sie keine Drittanbieter-Bluetooth Treiberstapel. Drittanbietersoftware funktioniert möglicherweise nicht ordnungsgemäß.
* Deaktivieren Sie die Einstellung "Benachrichtigung zum Herstellen einer Verbindung mit Schnelle Kopplung anzeigen" unter "Bluetooth & anderen Geräten", um die Aktivität der Host-Funkscans zu reduzieren.
* Wenn Sie eine interne Bluetooth-Karte verwenden, stellen Sie sicher, dass Sie eine externe antenne Bluetooth verwenden, oder es kann zu Problemen mit der Nachverfolgung von Problemen kommt. Wenn dies nicht funktioniert, verwenden Sie einen externen Bluetooth Dongle (USB), nachdem Sie die interne Bluetooth.
* Das Gerät sollte in den Einstellungen unter der Kategorie "Maus, Tastatur & Stift" Bluetooth werden. Wenn sie sich unter "Andere Geräte" befindet, entppeln Sie das Gerät, und koppeln Sie es.
* Entfernen, Entfernen und Ausschalten von Bluetooth und Lautsprechern. Diese werden mit der -Windows Mixed Reality. Verwenden Sie die Sprechbuchse oder die integrierten Lautsprecher auf Ihrem Mixed Reality Headset, um die beste Audioerfahrung zu bieten.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>Mein zweiter Controller benötigt lange, um die Verbindung wiederherzustellen.

Bei einigen älteren Intel-Radios kommt es zu diesem Problem, wenn Motion-Controller gleichzeitig eingeschaltet werden. Vermeiden Sie das gleichzeitige Ein-/Aus-Netzen von Controllern.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>My Qualcomm Bluetooth radio cannot pair controllers after a PC crash (Mein Qualcomm-Bluetooth kann controller nach einem PC-Absturz nicht koppeln)

Qualcomm (QCA) Bluetooth Funktreiber vor 10.0.0.448 kann nach einem abstürzen Windows sein. Deaktivieren Sie den PC vollständig, um dieses Problem zu umgehen.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Ich habe eine schlechte Controllernachverfolgung mit dem Radio "Solll"

Wechseln Sie zu Geräte-Manager > Bluetooth > Optionsadapter Bluetooth **Optionsadapter > Properties > Driver (>-Treiber),** und stellen Sie sicher, dass Sie den Treiber 15.68.9210.47 oder höher verwenden.
