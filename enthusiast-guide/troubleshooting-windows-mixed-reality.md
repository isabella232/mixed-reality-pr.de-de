---
title: Problembehandlung bei Windows Mixed Reality
description: Erweiterte Windows Mixed Reality-Problembehandlung, die über die standardmäßige Kundensupport Dokumentation hinausgeht.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support
ms.openlocfilehash: bf972c70f46ad9045005b953e28831df3ee9906e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685710"
---
# <a name="troubleshooting-windows-mixed-reality-faqs"></a>Problembehandlung bei Windows Mixed Reality (FAQs)

## <a name="understanding-common-installation-error-messages"></a>Grundlegendes zu allgemeinen Installations Fehlermeldungen

### <a name="your-pc-cant-run-windows-mixed-reality"></a>"Ihr PC kann Windows Mixed Reality nicht ausführen"

Der PC erfüllt nicht die [Mindestanforderungen](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für die Durchführung von Windows Mixed Reality. Dies kann daran liegen, dass die Hardware Einrichtung des Computers nicht mit Windows Mixed Reality kompatibel ist oder dass Sie ein [Update auf die neueste Version von Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq)durchzuführen haben. 

Beachten Sie, dass Windows Mixed Reality einen Grafikkartentreiber erfordert, der mindestens WDDM 2,2 unterstützt. Stellen Sie daher sicher, dass Sie über das neueste Treiberupdate des Herstellers verfügen. Wenn das Setup von Windows Mixed Reality besagt, dass Ihre Grafikkarte die Anforderungen nicht erfüllt, und Sie meinen, dass das Headset an die richtige Karte angeschlossen ist.

### <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Sie sind fast da – dieser PC erfüllt nicht die Mindestanforderungen für die Durchführung von Windows Mixed Reality".

Ihr PC erfüllt nicht die [Mindestanforderungen](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) , die für die bestmögliche Verwendung in Windows Mixed Reality erforderlich sind. Ihr PC ist möglicherweise in der Lage, ein immersives Headset auszuführen, kann jedoch möglicherweise nicht in der Lage sein, bestimmte Anwendungen auszuführen oder Probleme mit der Leistung zu haben.

Beachten Sie, dass Windows Mixed Reality einen Grafikkartentreiber erfordert, der mindestens WDDM 2,2 unterstützt. Stellen Sie daher sicher, dass Sie über das neueste Treiberupdate des Herstellers verfügen. Wenn das Setup von Windows Mixed Reality besagt, dass Ihre Grafikkarte die Anforderungen nicht erfüllt, und Sie meinen, dass das Headset an die richtige Karte angeschlossen ist.

### <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Bevor Sie Windows Mixed Reality einrichten können, muss Ihr Administrator es für Ihre Organisation aktivieren. Weitere Informationen "

Sie befinden sich wahrscheinlich in einem im Unternehmen verwalteten Netzwerk, und Ihre Organisation verwendet Windows Server Update Services (WSUS) oder andere Richtlinien, die den Download blockieren können. Wenden Sie sich an die IT-Abteilung oder den Systemadministrator Ihrer Organisation, um [Windows Mixed Reality zu aktivieren](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable).

### <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"Wir konnten die Mixed-Reality-Software nicht herunterladen

* Manchmal kann ein ausstehendes Update den gemischten Reality-Software Download blockieren. Wechseln Sie zu **Einstellungen > aktualisieren Sie & Sicherheits > Windows Update** , und vergewissern Sie sich, dass Windows Update aktiviert ist. Anschließend können Sie alle Updates herunterladen und installieren, die auf die Installation warten. Wenn Sie beim Ausführen dieser Schritte einen Fehler mit Windows Update erhalten, finden Sie [hier](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)Weitere Informationen.
* Stellen Sie sicher, dass Ihr PC mit dem Internet verbunden ist und über mindestens 2 GB freien Speicherplatz verfügt. Überprüfen Sie den Netzwerkstatus unter: **Einstellungen > Netzwerk & Internet > Status** . Wenn Sie keine Verbindung mit dem Internet herstellen können, finden Sie [hier](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues) Hilfe.  
* Starten Sie den PC neu, und versuchen Sie es erneut. 

Wenn die vorherigen Lösungen nicht funktionieren, versuchen Sie Folgendes:
* Wenn die Wi-Fi-Netzwerkverbindung auf "getaktet" festgelegt ist, ändern Sie Sie in " [nicht gemessen"](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq). Wechseln Sie zum Deaktivieren einer getakteten Verbindung zu **Einstellungen > Netzwerk & Internet > Status > Verbindungs Eigenschaften ändern > als** getaktete Verbindung festlegen, und wählen Sie "aus".  
* Wenn Sie vor kurzem ein Update installiert haben, kann dies zu Problemen führen. Es wird nicht empfohlen, alle installierten Updates zu entfernen, insbesondere Sicherheitsupdates, die Ihren PC schützen, aber manchmal kann das aktuelle Update durch das Entfernen des aktuellsten Updates leichter ermittelt werden. Dazu ist Folgendes erforderlich: 
    * Wechseln Sie zu **Einstellungen > aktualisieren Sie & Sicherheit > den installierten Update Verlauf anzeigen > Updates deinstallieren** .
    * Wählen Sie das zuletzt installierte Update aus, und deinstallieren Sie es.
    * Wenn Sie gefragt werden, ob Sie dieses Update wirklich deinstallieren möchten? Antworten Sie auf "Ja". Wenn Sie einen Fehler erhalten, wenn Sie diese Schritte ausführen, finden Sie [hier](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)Weitere Informationen. 
    * Starten Sie den PC neu, und versuchen Sie es erneut. 
    * Wenn Windows Mixed Reality ordnungsgemäß installiert wird, installieren Sie die neuesten Updates unter **Einstellungen > Windows Update > nach Updates suchen, und prüfen Sie** , ob Windows Mixed Reality weiterhin funktionsfähig ist. Wenn Sie nicht ordnungsgemäß installiert ist, installieren Sie die neuesten Updates, und wenden Sie sich an den Windows-Support. 

### <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Es ist ein Fehler aufgetreten, und wir konnten Windows Mixed Reality nicht starten"
* Entfernen Sie die beiden Kabel des Headsets vom PC.
* Starten Sie den PC neu.
* Wechseln Sie zu **Einstellungen > aktualisieren Sie & Sicherheits > Windows Update** , und stellen Sie sicher, dass Windows Update aktiviert ist. Anschließend können Sie alle wartenden Updates herunterladen und installieren.
* Stellen Sie erneut eine Verbindung mit dem PC her, und wiederholen Sie dann das Setup.

Wenn die oben genannten Schritte nicht funktionieren, deinstallieren Sie Windows Mixed Reality, und installieren Sie es anschließend neu:
* Wechseln Sie zu **Einstellungen > gemischte Realität > deinstallieren** , und wählen Sie "deinstallieren" aus. 
* Starten Sie Ihren PC neu. 
* Wenn Sie den Setup Vorgang erneut starten möchten, können Sie Ihr Headset einfach an Ihren PC anschließen.
    

## <a name="troubleshooting-setup-questions"></a>Problembehandlung bei Setup Fragen 

### <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>Der Xbox-Controller funktioniert nicht mit Windows Mixed Reality.

* Stellen Sie sicher, dass Ihr Controller eingeschaltet, vollständig abgerechnet und mit dem PC verbunden ist.
* Ersetzen Sie die Batterie des Controllers.
* Wenn Sie einen Bluetooth-Controller verwenden, wechseln Sie zu **Einstellungen > Geräte > Bluetooth & andere Geräte** auf Ihrem PC, und stellen Sie sicher, dass Sie gekoppelt sind (Sie sollten auf der Seite aufgeführt sein).

### <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>Ich kann die Eingabe (Controller, Gamepad, Maus/Tastatur) nicht in Windows Mixed Reality leiten.

Wenn Sie das Headset einfügen, sollte die Eingabe automatisch über den Anwesenheits Sensor Ihres Headsets in ihre gemischte Realität gewechselt werden. Ein blauer Balken sollte auf Ihrem Desktop angezeigt werden:

![Windows-Desktop mit Eingaben, die an das Headset geleitet werden](images/1050px-windowsy.png)

Wenn die Eingabe nicht automatisch ein-und ausgeschaltet wird, müssen Sie die Eingabe manuell in Ihr Headset umschalten. Hierzu können Sie **Windows-Taste + Y** auf der Tastatur eingeben (und dasselbe, um die Eingabe zurück zum Desktop zu wechseln).

### <a name="when-i-plug-in-my-headset-nothing-happens-the-mixed-reality-portal-doesnt-open"></a>Wenn ich mein Headset Anfüge, passiert nichts. Das Mixed Reality-Portal wird nicht geöffnet.
Mixed Reality Portal, die APP, die Sie durch das Windows Mixed Reality-Setup führt, ist so konzipiert, dass Sie automatisch geöffnet wird, wenn Sie ein kompatibles Headset einbinden. Wenn er nicht geöffnet ist, wechseln Sie zu Start, und geben Sie "Mixed Reality Portal" in das Suchfeld ein, um die APP dort zu öffnen. Wenn Sie das Mixed Reality-Portal nicht finden, bedeutet dies möglicherweise, dass Sie ein [Update auf die neueste Version von Windows durch](https://support.microsoft.com/en-us/help/12373/windows-update-faq)führen müssen.

### <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Gewusst wie zwischen "sitzend und stehend" und "alle Erfahrungen" wählen?

Wenn Sie die Option "sitzend und am Ende" auswählen, verwenden Sie das Headset ohne Begrenzung. Sie können sich im standbymenü befinden, aber Sie müssen anderweitig an einem Ort bleiben, da Sie keine Begrenzung haben, um physische Hindernisse zu vermeiden. Einige apps können so entworfen werden, dass Sie mit einer Grenze arbeiten, sodass Sie Sie möglicherweise nicht verwenden können oder wenn Sie Sie ohne Begrenzung verwenden. Weitere Informationen finden Sie unter "Was ist eine Grenze und warum sollte ich eine erstellen?" unten finden Sie weitere Informationen.

Wenn Sie "Alle Benutzeroberflächen" auswählen, richten Sie eine Grenze ein, und Sie können apps und Benutzeroberflächen verwenden, die mit einer Grenze und denjenigen arbeiten, für die Sie nicht erforderlich sind. 

### <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-into-the-windows-mixed-reality-home"></a>Erlernen gemischter Realität wurde beim ersten Start nicht ausgeführt, und ich ging direkt in die Windows Mixed Reality-Startseite.

Sie können die Lernfunktion erneut ausführen, indem Sie die [Schritte zur erneuten Ausführen](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience)befolgen. 


## <a name="boundary-setup-and-other-questions"></a>Einrichten von Grenzen und andere Fragen

### <a name="whats-a-boundary-and-why-should-i-create-one"></a>Was ist eine Grenze, und warum sollte ich eine erstellen?

Eine Grenze definiert den Bereich, in dem Sie sich bewegen können, während Sie Ihr Windows Mixed Reality-immersives Headset verwenden. Da Sie Ihre Umgebung nicht sehen können, während Sie Ihr Headset verwenden, ist es wichtig, dass Sie eine Grenze erstellen, die Sie bei der Vermeidung von Hindernissen unterstützt. Die Grenze sieht in gemischter Realität wie eine weiße Kontur aus und wird angezeigt, wenn Sie in der Nähe sind. Wenn Sie Sie sehen, verlangsamen Sie Ihre Bewegungen, und vermeiden Sie das Überschreiten der Grenze oder das erweitern ihrer Glieder.

Der Bereich innerhalb der Grenze sollte frei von Möbeln, kleinen Glüh Anlagen, Ceiling-Fans usw. sein, sodass Sie sich nicht mit einem Blick auf die-oder-Fahrt kümmern können. [Erfahren Sie mehr über Integrität und Sicherheit in Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort).

### <a name="how-do-i-create-a-boundary"></a>Gewusst wie eine Grenze erstellen?

Wenn Sie Ihr Headset zum ersten Mal einrichten, führt die Setup-app (Mixed Reality-Portal) Sie durch die Schritte zum Erstellen einer Grenze. Sie können jedoch jederzeit eine erstellen. Dazu ist Folgendes erforderlich:
1. Wählen Sie **> Mixed Reality-Portal** auf Ihrem Desktop starten aus. 
2. Öffnen Sie "Menu".
3. Wählen Sie "Setup ausführen" aus, um eine neue Grenze zu erstellen.

Wenn eine andere Person Ihr Headset verwendet, sollten Sie sicherstellen, dass Sie die Grenze verstehen und wie Sie Sie verwenden können. Wenn Sie Ihr Headset an einen neuen Speicherort verschieben, müssen Sie eine neue Grenze einrichten, die für diesen Bereich funktioniert.

### <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Ich erhalte eine Fehlermeldung, wenn ich versuche, eine Grenze zu erstellen.

* Beim Erstellen einer Grenze sollten Sie nicht zu nahe an einer Wand oder einer anderen Behinderung werden.
* Stellen Sie sicher, dass Sie Ihr Headset an der Taillenhöhe halten und den Computer bei der Ablauf Verfolgung der Grenze sehen.
* Stellen Sie sicher, dass der Sensor nicht blockiert ist und ausreichend Licht ist.
* Der Speicherplatz, den Sie verfolgen, muss größer als drei Quadratmeter sein.
* Der Speicherplatz darf nicht zu groß oder zu kompliziert sein. Halten Sie sich auf eine einfache geometrische Form, ohne große Mengen an drehen und Umdrehungen zu haben.
* Überspringen Sie bei der Ablauf Verfolgung nicht Ihren eigenen Pfad.
* Wenn Sie in einer Ecke hängen bleiben, beginnen Sie erneut.

### <a name="during-start-up-of-mixed-reality-im-stuck-at-the-step-turn-your-head-side-to-side-and-then-at-the-floor"></a>Während des Starts von Mixed Reality hängen Sie mit dem Schritt "legen Sie die Seite auf Seite und dann im Boden" ab.

Mit diesem Schritt kann Ihr Headset Ihren Speicherplatz erkennen und vorhandene virtuelle Oberflächen und Grenzen wiederherstellen. Wenn Sie Ihr Headset einfügen, kann dieser Scanvorgang bis zu 10 Sekunden dauern. Nach Abschluss des Vorgangs befinden Sie sich entweder in der gemischten Realität, oder Sie werden aufgefordert, die Grenze erneut einzurichten.

Wenn der Scanvorgang länger als 10 Sekunden dauert, könnte ein Problem mit dem near-Sensor im Headset auftreten:
1. Überprüfen Sie, ob der Aufkleber aus dem near-Sensor entfernt wurde. Der Near-Sensor befindet sich in dem Headset, in dem sich der Mittelpunkt der Stirnseite befindet.
2. Überprüfen Sie, ob Ihr near-Sensor die Eingabe für das Headset umschaltet: mit dem Finger decken Sie den Near-Sensor mehrmals ab, und erkennen Sie ihn mehrmals, um zu überprüfen, ob die Eingabe zum Headset wechselt. Am oberen Rand des PCs sollte das Banner **Windows-Taste + Y** angezeigt werden. Sie können die Eingabe jederzeit manuell in das Headset umschalten, indem Sie auf der Tastatur **Windows-Taste + Y** eingeben.

### <a name="i-see-a-message-that-says-my-boundary-cant-be-found-what-should-i-do"></a>Ich sehe eine Meldung, die besagt, dass meine Grenze nicht gefunden werden kann.   Wie sollte ich vorgehen?

Windows Mixed Reality kann Probleme beim Identifizieren Ihrer vorhandenen Grenze haben. Sie können eine neue Grenze erstellen, oder Sie können Ihr Gerät im Modus "sitzend und stehend" verwenden. 

### <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Ich sehe eine Meldung, die besagt, dass "verlorene Nachverfolgung" oder "Wir haben keine Grenze für diesen Raum".

Sie müssen eine neue Grenze erstellen. Dazu ist Folgendes erforderlich:
* Wählen Sie **> Mixed Reality-Portal starten** aus.
* Wählen Sie "Setup ausführen" aus.

### <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>Die Grenze ist immer sichtbar. Wie kann ich es tun?

Die Grenze wird angezeigt, wenn Sie in der Nähe sind. Wenn Ihre Grenze Abschnitte enthält, die eine schmale oder unregelmäßige Form aufweisen, kann es passieren, dass Sie sich in der Nähe befinden und Sie eher als gewünscht erscheinen. Um dieses Problem zu beheben, versuchen Sie erneut, die Grenze mithilfe einer größeren und regulären Form zu erstellen. Dazu ist Folgendes erforderlich:
* Wählen Sie **> Mixed Reality-Portal starten** aus.
* Wählen Sie "Setup ausführen" aus.

### <a name="how-can-i-turn-off-the-boundary-temporarily"></a>Wie kann ich die Grenze vorübergehend deaktivieren?

* Wählen Sie **> Mixed Reality-Portal starten** aus.
* Öffnen Sie "Menu". 
* Legen Sie "Boundary" auf "Off" (aus). Stellen Sie sicher, dass Sie an einem Ort bleiben, während die Grenze deaktiviert ist.


## <a name="problems-in-windows-mixed-reality-home"></a>Probleme bei der Windows Mixed Reality-Startseite

### <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>Meine Controller werden nicht in meiner Windows Mixed Reality-Startseite angezeigt.

Stellen Sie sicher, dass Ihre Controller über vollständige Akkus verfügen und dass Sie mithilfe von Bluetooth ordnungsgemäß gekoppelt werden. Verwenden Sie die Windows-Schaltfläche, und schalten Sie die Controller ein. Wenn Ihre Controller immer noch nicht angezeigt werden, versuchen Sie, jeden Controller im Menü "Einstellungen" unter **Geräte > Bluetooth** zu koppeln und erneut zu koppeln.

### <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height-or-it-is-slanted"></a>Die Etage meiner Windows Mixed Reality-Startseite scheint sich nicht in der richtigen Höhe zu befinden, oder Sie ist schlank.

Wählen Sie **> Raum Anpassung starten** aus, die gestartet wird, sobald Sie die APP auf der ganzen Welt platzieren, um bei der Ausführung Ihres Headsets Änderungen vorzunehmen. In dieser APP werden Sie angewiesen, den Touchpad (Motion Controller) oder das Richtungs Pad (Gamepad) zu verwenden, um die Bodenhöhe anzupassen. Wenn die Etage korrekt ist, verwenden Sie die Windows-Schaltfläche, um zur Startseite zurückzukehren.

### <a name="my-headset-has-stopped-tracking"></a>Mein Headset hat die Überwachung beendet.

Stellen Sie sicher, dass die Lichter eingeschaltet sind und dass die in-out-nach Verfolgungs Kameras nicht an der Vorderseite Ihres Headsets blockiert werden. Wenn die Nachverfolgung verloren geht, kann es einige Sekunden dauern, bis der Vorgang fortgesetzt wird. Wenn die Nachverfolgung nicht fortgesetzt wird, versuchen Sie, das Windows Mixed Reality-Portal neu zu starten. Weitere Informationen finden Sie unter nach [Verfolgen der Problem](tracking.md) Behandlung.

### <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop-screen"></a>Ich kann auf meinem Desktop Bildschirm keine Vorschauversion anzeigen, was ich in meinem Headset sehe.

Das Mixed Reality-Portal verfügt am unteren Bildschirmrand über eine **Wiedergabe** Schaltfläche, über die Sie auf dem Bildschirm Ihres Desktops eine Vorschau anzeigen können, was Sie in Ihrem Headset sehen. Aber aus Leistungsgründen ist diese Funktion nur auf PCs verfügbar, die unter Windows Mixed Reality Ultra (90Hz) ausgeführt werden.

## <a name="headset-connectivity-issues"></a>Konnektivitätsprobleme

### <a name="my-computer-does-not-have-an-hdmi-port"></a>Der Computer verfügt über keinen HDMI-Port.
Wenn Ihr Computer nicht über einen Codec-Port verfügt, aber über einen Display Port (DP)-, Mini Display Port (miniDP)-oder USB-c-Port (USB-c) für die Ausgabe von Videos verfügt, müssen Sie möglicherweise einen [unterstützten Adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)verwenden.

### <a name="can-i-use-usb-or-hdmi-extension-cables-with-windows-mixed-reality-headsets"></a>Kann ich USB-oder HDMI-Erweiterungs Kabel mit Windows Mixed Reality-Headsets verwenden?
Die Verwendung von USB-oder HDMI-Erweiterungs Kabeln wird von Windows Mixed Reality-Headsets nicht offiziell unterstützt. Die Verwendung dieser Kabel kann sich aufgrund von Abweichungen in der resultierenden Signalintegrität und der Busleistung zwischen dem USB-Controller des PCs und dem Mixed Reality-Headset erheblich auf die gemischte Realität auswirken. Wenn in der Headset-Anzeige kurz ein blauer Bildschirm angezeigt wird, können Sie in schwarz und gemischtes Reality-Portal Neustarts oder vollständige Aufzählung während der Verwendung anzeigen, oder wenn sich das Headset-audiobild ausschneidet oder es in eine glitplizierung wechselt, oder wenn das Headset zwischen schwarz und der richtigen Anzeige Flimmern.

### <a name="i-am-getting-a-check-your-display-cable-error"></a>Ich erhalte den Fehler "Ihr Anzeige Kabel überprüfen".

* Wenn Sie einen Adapter zum Verbinden Ihres Headsets mit Ihrem PC verwenden, stellen Sie sicher, dass Windows Mixed Reality unterstützt wird. Versuchen Sie außerdem, den Adapter mit dem PC zu verbinden, bevor Sie das HMD mit dem Adapter verbinden.
* Wenn Ihr PC sowohl über integrierte als auch diskrete Grafiken verfügt, stellen Sie sicher, dass Sie den HDMI-Port auf Ihrer aktiven Grafikkarte verwenden. In einigen Fällen bedeutet dies möglicherweise, dass Sie Ihre PC-Anzeige mit einem nicht-HDMI-Port verbinden müssen.
* Wenn Ihr PC über integrierte und diskrete Grafiken verfügt und die integrierte Grafik älter ist und Windows Mixed Reality nicht unterstützt, versuchen Sie, die integrierte GPU zu deaktivieren.
* Verbinden Sie einen PC-Monitor mit dem HDMI-Port Ihres PCs. Stellen Sie sicher, dass Ihre Grafiktreiber auf dem neuesten Stand sind. Laden Sie die von AMD, NVIDIA oder Intel direkt herunter, und installieren Sie Sie, da Sie wahrscheinlich neuer als die in Windows Update veröffentlichten sind.
* Stellen Sie sicher, dass Sie das-HDMI-Kabel Ihres Headsets an einen- **HDMI** -Port auf Ihrem PC und nicht an den Port "HDMI" angeschlossen haben.
* Die Anzeige Kabelverbindung kann möglicherweise nicht von Windows erkannt werden. Öffnen Sie die Geräte-Manager, und überprüfen Sie, ob das Headset unter "Monitore" aufgeführt ist. Wenn dies nicht der gibt, wählen Sie **Aktion > auf Hardwareänderungen über** prüfen. 

### <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>Ich sehe eine Meldung mit dem Hinweis "Put on your Headset", auch wenn mein Headset vorhanden ist.

Wenn Sie Ihr Headset einfügen, benötigt Windows Mixed Reality möglicherweise einige Sekunden, um den Speicherplatz neu zu laden. Wenn diese Nachricht nicht entfernt wird, stellen Sie sicher, dass der Schutz Aufkleber aus dem near-Sensor entfernt wurde, der sich auf der Innenseite des Headsets zwischen den objektiven befindet. Wenn das Problem hierdurch nicht behoben wird, wenden Sie sich an Ihren Headset-Hersteller.

### <a name="a-message-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>Eine Meldung mit dem Hinweis "Verbinden Sie Ihr Headset", obwohl ich mein Headset angeschlossen habe.

1. Stellen Sie sicher, dass die USB-und die-HDMI-Kabel des Headsets mit den richtigen Ports auf Ihrem PC verbunden sind. Im folgenden wird erläutert, wie die richtigen Ports identifiziert werden:
    * USB 3,0-Ports verfügen über ein spezielles Logo mit der Markierung "SS" ("SuperSpeed"). Der innere Bereich des Ports ist normalerweise blau, während ältere USB 2,0-Ports in der Regel Schwarz oder weiß im Inneren sind.
    * Wenn Ihr Computer über zwei HDMI-Ports verfügt, verwenden Sie den Computer, der eine Verbindung mit der Grafikkarte herstellt, nicht die Hauptplatine des Computers. Es ist nicht immer offensichtlich, welches ist, obwohl sich diskrete Ports häufig in einem Erweiterungs Slot auf dem Computer befinden. Wenn Sie einen Port ausprobieren und dies nicht funktioniert, versuchen Sie es noch mal.
2. Entfernen Sie die USB-und die-HDMI-Kabel von Ihrem Headset, um sicherzustellen, dass Sie sicher verbunden sind. Wenn Sie das USB-Kabel einfügen, versuchen Sie nicht, während des Einfügens des USB-Kabels anzuhalten.
3. Öffnen Sie Geräte-Manager, und vergewissern Sie sich, dass Ihr Headset unter "Mixed Reality Devices" aufgeführt ist. Doppelklicken Sie unter "gemischte Reality-Geräte" auf Ihr Headset, und vergewissern Sie sich, dass der Gerätestatus "dieses Gerät funktioniert ordnungsgemäß" angezeigt wird. Gelbe Ausrufezeichen auf Geräten, die in Geräte-Manager aufgeführt sind, zeigen Fehler an, die von den mit Ihrem PC verbundenen Geräten gemeldet wurden.
    * Wenn "hololens Sensors" mit einem gelben Ausrufezeichen in Geräte-Manager aufgeführt ist, doppelklicken Sie auf das Gerät. Wenn **"Code 10: die Treiber für dieses Gerät sind nicht installiert" angezeigt wird. Es sind keine kompatiblen Treiber für dieses Gerät vorhanden** . Befolgen Sie die [Anweisungen](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset) , um den Headset-Treiber manuell zu installieren.
    * Wenn Sie auf Ihrem PC mehrere Mixed-Reality-Headsets verwenden und den Mixed Reality-Headset-Treiber manuell installiert haben, kann das manuelle Treiberupdate in einigen Fällen nur für das mit der Zeit verbundene Headset und nicht für Ihre anderen Headsets verwendet werden. In diesem Fall wird **"Code 31: dieses Gerät funktioniert nicht ordnungsgemäß ausgeführt, da die für dieses Gerät erforderlichen Treiber nicht geladen werden können. (Code 31). Die angeforderte ALPC-Nachricht ist in Geräte-Manager nicht mehr verfügbar** . Klicken Sie in Geräte-Manager mit der rechten Maustaste auf Ihr Headset unter "gemischte Reality-Geräte", und wählen Sie "Gerät deinstallieren" aus. Wählen Sie "OK" aus, um das Headset zu bestätigen und dann wieder zu entfernen.
4. Wenn Sie die partielle Enumeration des Headsets sehen (eine Reihe von USB-Geräten aufzählen, aber nichts unter "Mixed Reality-Headsets" in Geräte-Manager), testen Sie einen extern betriebenen USB 3,0-Hub.
5. Wechseln Sie zur Website des Headset-Herstellers, und aktualisieren Sie die Treiber und die Firmware für Ihr Headset.
6. Verbinden Sie Ihr Headset mit einem anderen PC, und öffnen Sie Geräte-Manager. Auch wenn dieser PC nicht vollständig mit Windows Mixed Reality kompatibel ist, können Sie überprüfen, ob Ihr Headset aufzählt. Wenn Ihr Headset nicht auf mehreren PCs aufzählt, kann ein Hardwareproblem auftreten.

**Hinweis für Surface-Benutzer:** Frühere Versionen der USB-Hub-Firmwareupdates für Surface-Dock und Surface Book sind nicht mit Mixed Reality-Headsets kompatibel. Wenn Sie die Meldung "Connect your Headset on a Surface PC" erhalten, überprüfen Sie, ob von Geräten **der Fehler "Code 10: das Gerät kann nicht gestartet werden"** in Geräte-Manager angezeigt wird. Entfernen Sie in [diesem Fall den in Konflikt stehenden Treiber](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Dies ist nur einmal erforderlich.

**Hinweis für Windows 10 N-Benutzer:** Wenn auf Ihrem PC Windows 10 N ausgeführt wird, wird **der Fehler "Code 28: die Installationsklasse ist nicht vorhanden oder ist ungültig"** in Geräte-Manager nach dem Plug in Ihr Mixed Reality-Headset angezeigt. N-Editionen von Windows 10 werden von der gemischten Realität von Windows nicht unterstützt. Befolgen Sie diese [Anweisungen](troubleshooting-windows-mixed-reality.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) , um weitere Informationen zu finden.

### <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Eine Meldung lautet: "Überprüfen Sie das USB-Kabel" oder "unzureichende USB-Geschwindigkeit".

* Stellen Sie sicher, dass Sie einen unterstützten USB 3,0-Port auf Ihrem PC verwenden:
    * Stellen Sie sicher, dass das USB-Kabel Ihres Headsets vollständig angeschlossen ist.
    * Führen [Sie die Windows Mixed Reality PC Check](https://aka.ms/pccheckapp) -App aus, um sicherzustellen, dass der USB 3,0-Controller Ihres PCs unterstützt wird.
    * Testen Sie jeden der anderen USB 3,0-Ports auf Ihrem PC. Einige PCs verfügen über mehr als einen USB 3,0-Controller.
    * Trennen Sie vorübergehend alle USB-Geräte, die mit dem PC verbunden sind, und verbinden Sie Ihr Headset.
    * Auf benutzerdefinierten PCs, auch wenn ein Port als USB 3,0-Port gekennzeichnet sein kann, ist er möglicherweise mit einem USB 2,0-Controller verbunden. Öffnen Sie bei geöffneter Verbindung Geräte-Manager, suchen Sie das Gerät, und klicken Sie mit der Maustaste auf eines der Geräte, die in Ihrem Headset aufgelistet sind. wechseln Sie dann zu **anzeigen > Geräte nach Verbindung**
* Testen Sie Ihr Headset auf einem anderen PC. Wenn der andere PC nicht vollständig mit Windows Mixed Reality kompatibel ist, checken Sie Geräte-Manager ein, um festzustellen, ob die Meldung "unzureichende USB-Geschwindigkeit" angezeigt wird. Wenn Ihr Headset nicht ordnungsgemäß auf mehreren PCs aufgelistet ist, könnte Ihr Headset fehlerhaft sein.

### <a name="the-mixed-reality-portal-did-not-launch-automatically-after-i-plugged-in-my-headset"></a>Das Mixed Reality-Portal wurde nicht automatisch gestartet, nachdem ich mein Headset angeschlossen habe.

Das Headset wurde aufgrund eines zugrunde liegenden Problems möglicherweise nicht ordnungsgemäß erkannt. Versuchen Sie, das Mixed Reality-Portal manuell zu starten, und suchen Sie nach Fehlermeldungen, die angezeigt werden. 

### <a name="my-headset-stopped-working-after-putting-my-pc-to-sleep-in-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Mein Headset funktioniert nicht mehr, nachdem ich meinen PC in den Ruhezustand versetzt oder den PC neu gestartet habe.

1. Öffnen Sie Geräte-Manager, und vergewissern Sie sich, dass Ihr Headset unter "Mixed Reality Devices" aufgeführt ist.
2. Doppelklicken Sie unter "gemischte Reality-Geräte" auf Ihr Headset, und vergewissern Sie sich, dass der Gerätestatus "dieses Gerät funktioniert ordnungsgemäß" angezeigt wird.
3. Wenn die Fehlermeldung "Code 43" mit dem Hinweis angezeigt wird, dass das Gerät nicht mehr funktioniert, oder wenn Ihr Headset nicht unter "gemischte Reality-Geräte" aufgeführt ist, lösen Sie das USB-Kabel Ihres Headsets aus, und geben Sie es erneut ein. Microsoft untersucht ein potenzielles Problem mit der Software-/treiberinteroperabilität, das möglicherweise zu diesem Fehler führt. Dieses Problem wirkt sich auf eine kleine Anzahl von PCs aus, und es wird erwartet, dass Sie in einem zukünftigen Update des Mixed Reality-Headset-Treibers aufgelöst werden.

### <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Mein Headset bewirkt, dass mein PC eine Fehlerüberprüfung (blauer Bildschirm) generiert, wenn der PC in den Standbymodus versetzt wird oder sich im Ruhezustand befindet.

Microsoft untersucht ein potenzielles Problem mit der Software-/treiberinteroperabilität, das möglicherweise dazu führt, dass eine geringe Anzahl von PCs eine "9F"-Fehlerüberprüfung (blauer Bildschirm) erzeugt, wenn der PC in den Standbymodus versetzt oder in den Ruhe Zustands Modus versetzt wird. Dieses Problem wird in einem zukünftigen Update des Mixed Reality-Headset-Treibers gelöst.

### <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Der Headset-Treiber wurde nicht automatisch installiert, als ich das Headset angeschlossen habe.

Auf neuen PCs oder PCs mit einer neu installierten Kopie von Windows 10 könnte der Headset-Treiber hinter anderen Windows-Updates in die Warteschlange eingereiht werden und wird möglicherweise nicht sofort installiert. Wenn Sie über eine "N"-Edition von Windows verfügen, müssen Sie zu einer regulären Edition von Windows 10 wechseln, damit Windows Mixed Reality verwendet werden kann. So installieren Sie es manuell:

1. Wechseln Sie zu **Start > Geräte-Manager** , und suchen Sie unter "andere Geräte" nach einem Gerät "hololens Sensors" mit einem gelben Ausrufezeichen: ![ Ansicht der Geräte-Manager hololens-Sensoren](images/hololenssensors.png)
2. Klicken Sie mit der rechten Maustaste auf das Gerät, und wählen Sie Eigenschaften Wenn die Eigenschaften des Geräts die **Treiber für dieses Gerät lesen nicht installiert sind (Code 28)** , schließen Sie das Fenster, und fahren Sie fort. Wenn eine andere Meldung vorhanden ist, führen Sie die Schritte zur Problembehandlung auf den restlichen Seiten der Seite aus.
![Code 28 von hololens-Sensoren in Geräte-Manager](images/code28.png)
3. Klicken Sie erneut mit der rechten Maustaste auf das Gerät, und wählen Sie "Treiber aktualisieren...". und dann nach der Aktualisierung des Geräts "automatisch nach aktualisierter Treibersoftware suchen" angezeigt wird, wird Ihr Headset in Geräte-Manager unter "gemischte Reality-Geräte" angezeigt: das ![ Gerät mit gemischter Realität wird in Geräte-Manager](images/mixedrealitydevices.png)

Wenn die manuelle Installation nicht funktioniert oder Sie den Treiber nicht unter anderen Geräten finden, müssen Sie den vorhandenen Treiber wahrscheinlich deinstallieren und neu installieren. Gehen Sie dafür folgendermaßen vor:
1. Wechseln Sie zu **Start > Geräte-Manager** , und suchen Sie unter "gemischte Reality-Geräte" nach Ihrem Headset. Der Gerätestatus sollte darauf hinweisen, dass das Gerät ordnungsgemäß funktioniert.
2. Klicken Sie mit der rechten Maustaste auf das Gerät, und wählen Sie "Gerät deinstallieren"
3. Aktivieren Sie im angezeigten Popup Fenster das Kontrollkästchen "Treibersoftware für dieses Gerät löschen", und wählen Sie dann "deinstallieren" aus.
4. Wenn dies abgeschlossen ist, lösen Sie das Headset von Ihrem PC aus, und binden Sie es wieder ein. Windows Update wird jetzt ein neuer Treiber heruntergeladen und installiert.

### <a name="troubleshooting-flowchart"></a>Flussdiagramm zur Problembehandlung

![Herstellen einer Verbindung mit Ihrem Headset/Überprüfen Ihres USB](images/hmd-connectivity2.jpg)


## <a name="mixed-reality-headset-display-problems"></a>Probleme beim Anzeigen von Mixed Reality-Headset ##

### <a name="my-headset-displays-are-black"></a>Meine Headset-Anzeige ist schwarz.

* Überprüfen Sie die Leistung und Stabilität Ihres PCs:
    * Verwenden Sie den Task-Manager, um festzustellen, ob Prozesse die CPU-, GPU-und/oder Festplattenlaufwerke Ihres PCs durchlaufen.
    * Sehen Sie sich die Anwendungs-und System Ereignisprotokolle in Windows (mit Ereignisanzeige) an, um zu ermitteln, ob Sie über eine APP verfügen, die häufig abstürzt und Windows-Fehlerberichterstattung (wer)-Berichte erzeugt.
    * Überprüfen Sie Windows Update, um sicherzustellen, dass Ihre Version von Windows aktuell ist. Sie müssen möglicherweise mehrmals "nach Updates suchen" auswählen.
* Überprüfen der APP-und Spiel Stabilität:
    * Stellen Sie sicher, dass Ihr PC die minimalen Systemanforderungen erfüllt, um beliebige Apps/Spiele auszuführen, die nicht ordnungsgemäß ausgeführt werden.    
    * Stellen Sie sicher, dass Ihre GPU-Treiber Version aktuell ist, und überprüfen Sie, ob neue Leistungs-und Kompatibilitätsprobleme und Regressionen für neue Treiber vorliegen.
    * Wenn Sie steamvr-apps und Spiele verwenden, stellen Sie sicher, dass steamvr und Windows Mixed Reality for steamvr-Komponenten auf dem neuesten Stand sind.
* Überprüfen der Kompatibilität des HDMI-Adapters
    * Stellen Sie sicher, dass das HDMI-Kabel vollständig angeschlossen ist.
    * Wenn Sie einen HDMI-Adapter verwenden (z. b. einen Mini Display Port für den HDMI-Adapter), stellen Sie sicher, dass er mit Windows Mixed Reality kompatibel ist. Der Adapter muss die Unterstützung von HDMI 2,0 unterstützen, und es gibt zahlreiche ältere Adapter, die nur 1080p unterstützen. Weitere Informationen finden Sie unter [Empfohlene Adapter für Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
    * Die Plug-in-Reihenfolge ist wichtig. Verbinden Sie den HDMI-Adapter mit Ihrem PC, bevor Sie das Headset mit dem Adapter verbinden, insbesondere, wenn Sie einen USB-C-zu-HDMI-Adapter verwenden. 
    * Entfernen Sie Erweiterungs Kabel, wenn Sie Sie verwenden.
* Grafikkarten-und Treiber Kompatibilität überprüfen:
    * Testen Sie den HDMI-Port Ihres PCs mit einem PC-Monitor. Einige PCs verfügen möglicherweise über mehr als einen HDMI-Port, und nicht alle können aktiv sein.
    * Wenn Ihr PC sowohl über eine integrierte Grafikverarbeitungseinheit (igpu) als auch über eine diskrete Grafikverarbeitungseinheit (dGPU) verfügt, stellen Sie sicher, dass Sie mit dem HDMI-Port von dGPU verbunden sind.<br> ![HDMI-Ports](images/HP_HDMI_Ports_s.png)
    * Überprüfen Sie die Version des GPU-Treibers. Stellen Sie sicher, dass Sie aktuell ist, aber berücksichtigen Sie auch neue Leistungs-und Kompatibilitätsprobleme und Regressionen bei brandneuen Treibern.
    * Wenn Sie Gemischte Realität auf einem Laptop verwenden und einen neueren Grafiktreiber von der Website des Grafikkartenherstellers installiert haben, versuchen Sie, ein Downgrade auf den neuesten Grafikkartentreiber durchführen, der auf der Website des PC-Herstellers bereitgestellt wurde, oder auf Windows Update.
    * Wenn Sie über mehrere PC-Monitore verfügen, die mit dem PC verbunden sind, versuchen Sie vorübergehend, alle Computer mit Ausnahme eines PCs zu trennen.
    * Wenn Sie eine benutzerdefinierte Aktualisierungsrate für Ihren PC-Monitor festgelegt haben, versuchen Sie vorübergehend, eine standardmäßige Aktualisierungsrate, z. b. 60Hz, wiederherzustellen.
    * Wenn Sie Ihre Grafikkarte vor kurzem geändert haben, ohne Windows neu zu installieren, überprüfen Sie, ob der Headset-Monitor weiterhin den richtigen Treiber installiert hat. Vergewissern Sie sich, dass Ihr Headset angeschlossen ist, dass in Geräte-Manager unter dem Knoten Monitore der Eintrag "Mixed Reality Headset" aufgeführt ist.
    * Wenn Ihr PC über eine NVIDIA-Grafikkarte verfügt, stellen Sie sicher, dass NVIDIA die 3D-Vision Software deaktiviert ist.
    * Auf einigen Grafikkarten (besonders ältere Grafikkarten) unterstützt der HDMI-Port möglicherweise nicht die Verwendung von "HDMI 2,0" oder ist nicht vollständig kompatibel mit Windows Mixed Reality. Versuchen Sie, den Display Port der Grafikkarte mit einem [aktiven Display Port 1,2-to-HDMI 2,0-Adapter zu](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) verwenden.
    * HP Omen-PCs mit der HP-Produktnummer 1rj99ea # Abu verfügen über die für Windows Mixed Reality kompatiblen HDMI-Ports. Um dies zu überprüfen, öffnen Sie den "HP Support Assistant", und die Produktnummer wird im unteren Bereich der APP aufgelistet.
    * Wenn Ihr PC eine Grafikkarte der AMD-Grafikkarte hat und Sie ein Samsung Mixed Reality-Headset verwenden, müssen Sie die Firmware Ihres Headsets auf Version 1.0.8 oder höher aktualisieren, um den HDMI-Port Ihrer Grafikkarte mit dem Headset zu verwenden.
    * Wenn Sie ein Surface Book 2 verwenden, stellen Sie sicher, dass Sie den [USB-C-USB-Adapter](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)verwenden.
* Überprüfen Sie, ob ein Mixed Reality-Headset Hardwareproblem vorliegt:
    * Um Hardwareprobleme mit dem Mixed Reality-Headset zu bestätigen oder auszuschließen, versuchen Sie, Ihr Mixed Reality-Headset mit einem anderen PC zu verbinden. 
    * Überprüfen Sie zunächst die Probleme mit der PC-Kompatibilität und des Setups, da die Symptome sehr ähnlich sind.
* Stellen Sie sicher, dass das USB-Kabel an einen USB-3,0 oder einen schnelleren Port angeschlossen ist. Auf USB 3,0-Ports wird SS (Super Geschwindigkeit) neben Ihnen geschrieben. Sie sind häufig (aber nicht immer) blau gefärbt.        

Wenn dies hilfreich ist, finden Sie unten im Abschnitt zur Problembehandlung für den Headset Black Screen.

![Schwarz Bildschirm/nichts sehen](images/hmd-connectivity.jpg)

### <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Meine Headset-Anzeige wird nach einiger Verwendung gelegentlich schwarz.

* Versuchen Sie, alle USB-Suspend-oder Energiesparfunktionen zu deaktivieren, die Ihr PC möglicherweise besitzt. Beispiel: [USB selektive Suspend](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend) in Windows-Energieoptionen, die Einstellung "das Ausschalten dieses Geräts durch den Computer zulassen, um Energie zu sparen" in Geräte-Manager und alle USB-Energiespareinstellungen in der Firmware Ihres PCs.
* Trennen Sie vorübergehend alle anderen USB-Geräte und Peripheriegeräte, die mit dem PC verbunden sind.
* Überprüfen Sie die Version des GPU-Treibers. Stellen Sie sicher, dass Sie aktuell ist, aber berücksichtigen Sie auch neue Leistungs-und Kompatibilitätsprobleme und Regressionen bei brandneuen Treibern.

### <a name="one-of-the-displays-on-my-headset-is-black"></a>Eine der anzeigen auf meinem Headset ist schwarz.

* Wenn Sie einen HDMI-Adapter verwenden, stellen Sie sicher, dass er den Wert von HDMI 2,0 unterstützt.
* Entfernen Sie alle USB-und HDMI-Erweiterungs Kabel, die Sie möglicherweise verwenden.
* Stellen Sie sicher, dass Ihr Grafiktreiber auf dem neuesten Stand ist.
* Probieren Sie das Mixed Reality-Headset auf einem anderen PC aus.

### <a name="my-headset-displays-turn-blue-for-a-moment-and-then-mixed-reality-portal-reinitializes"></a>Mein Headset zeigt einen Moment, und das gemischte Reality-Portal wird erneut initialisiert.

Dies weist normalerweise auf ein Problem mit der Zuverlässigkeit der USB-Controller auf Ihrem PC hin:
* Testen Sie einen anderen USB-Anschluss. Ihr PC verfügt möglicherweise über mehrere USB 3,0-Controller.
* Entfernen Sie alle Erweiterungs Kabel (falls zutreffend).
* Versuchen Sie, alle anderen USB-Geräte von Ihrem PC zu entstecken.
* Verbinden Sie einen extern betriebenen USB 3,0-Hub mit Ihrem PC, und verbinden Sie Ihr Headset mit dem Hub.
* Wenn Sie einen Desktop-PC verwenden, sollten Sie eine USB 3,0 PCIe-Karte erwerben, um Ihrem PC einen weiteren USB-Controller hinzuzufügen.

### <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>Mein Headset bewirkt, dass mein PC während des Starts einen schwarzen Bildschirm anzeigt.

Auf einigen PCs ist das Einschalten Ihres Headsets vor dem Einschalten oder beim Neustart des PCs möglicherweise beeinträchtigt. Ihr PC könnte auswählen, dass das Headset als "primärer Monitor" angezeigt wird, um den Status des PC-Starts anzuzeigen, oder es kann verhindert werden, dass er ordnungsgemäß gestartet wird und/oder einen Fehlercode erzeugt. Das Verhalten hängt größtenteils von der Marke und dem Modell des PCs und/oder der Marke und dem Modell der Grafikkarte ab. So beheben Sie dieses Problem:
* Verbinden Sie Ihr Headset mit einem anderen Port auf Ihrer Grafikkarte (möglicherweise müssen Sie einen Adapter verwenden, um die anderen Ports zu verwenden).
* Stellen Sie sicher, dass die BIOS/UEFI-Firmware Ihres PCs auf dem neuesten Stand ist (aber aktualisieren Sie die BIOS/UEFI-Firmware Ihres PCs nur, wenn Sie dies tun).

### <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Der PC oder das Headset zeigt Flimmern, Flash oder bleiben bei der Verwendung eines Surface-PCs schwarz.

* Stellen Sie sicher, dass Sie einen HDMI-Adapter verwenden, der HDMI 2,0 unterstützt. Viele ältere HDMI-Adapter unterstützen nur eine 1080p-Auflösung, die für Mixed Reality-Headsets unzureichend ist.
* Stellen Sie sicher, dass Ihr Grafiktreiber auf dem neuesten Stand ist. Zusätzlich zum Überprüfen Windows Update können Sie die Website des PC-Herstellers auf einen aktualisierten Grafiktreiber überprüfen.
* Einige Oberflächen Geräte sind mit Windows Mixed Reality nicht kompatibel. Erfahren Sie mehr über die [Oberflächen Kompatibilität und Anforderungen](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface).

### <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>Meine Headset-Anzeige funktioniert nach dem Herunterfahren und Durchführen eines schnellen Starts nicht mehr.

Entfernen Sie das HDMI-Kabel und das USB-Kabel vom Headset, und binden Sie Sie dann wieder ein.

### <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Meine Headset-Anzeige ist sehr viel schimig, aber das Vorschaufenster des gemischten Reality-Portals erscheint in Ordnung.

* Stellen Sie sicher, dass die Systemressourcen Ihres PCs (CPU, Arbeitsspeicher und Festplatte) verfügbar und nicht durch eine andere APP oder einen anderen Prozess abgepackt werden.
* Aktualisieren Sie Ihren Grafiktreiber.

### <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Ich erhalte den Fehler "die Installationsklasse ist nicht vorhanden oder ungültig" in Geräte-Manager.

Wenn in Geräte-Manager "hololens-Sensoren" mit einem gelben Ausrufezeichen angezeigt wird, doppelklicken Sie auf das Gerät, um weitere Informationen zu erhalten. Wenn die Meldung "die Treiber für dieses Gerät sind nicht installiert" angezeigt wird, wird eine Meldung angezeigt. (Code 28)--die Installationsklasse ist nicht vorhanden oder ungültig. "Dies liegt in der Regel daran, dass auf Ihrem PC [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)ausgeführt wird. Beachten Sie, dass die n-Editionen von Windows 10 Windows Mixed Reality nicht unterstützen, und Sie müssen eine nicht-N-Version von Windows 10 installieren.

### <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Meine WMR-Umgebung ist gezittert oder Verzögerungen, wenn ich meinen Kopf bewege und eine doppelte Vision anzeigt.

Auf einem Laptop mit integrierter Grafik und einer NVIDIA-GPU tritt nach einem bestimmten Zeitraum ein Fehler auf, der dazu führt, dass ein vorheriger Frame nach dem nächsten Frame angezeigt wird. Dies führt zu einer doppelten Sicht. Das Problem scheint für Treiber nach dem NVIDIA-Grafiktreiber 436,48 zu sein.  Durch die Installation dieses Treibers wird das Problem behoben, bis NVIDIA das Problem in den aktualisierten Treibern löst. Eine direkte Installation des nVidia-Grafik Treibers 436,48 finden Sie unter [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

### <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>Wenn ich mein Headset verwende, treten Probleme auf.
Allgemeine Informationen über den Komfort in Windows Mixed Reality finden Sie unter [Windows Mixed Reality-immersives Headset-Integrität,-Sicherheit und-Komfort](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort). Weitere Informationen zu Ihrem speziellen Headset finden Sie unter dem Headset-Hersteller.

### <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Wie kann ich in meinem Headset eine klarere Ansicht erhalten?
Passen Sie die Anpassung Ihres Headsets an. Passen Sie die Position auf der Vorderseite an, indem Sie Sie nach oben oder nach unten oder nach links und rechts verschieben, und passen Sie die Bänder so an, dass Sie sich

Wenn Ihr Headset dies unterstützt, können Sie auch seine Kalibrierungs Einstellungen anpassen. Wenn das Headset über einen Knopf zum Anpassen der Kalibrierung verfügt, verwenden Sie diesen. Wenn dies nicht der Fall ist, wechseln Sie zu **Einstellungen > gemischte Realität > visuelle Qualität** , und passen Sie die Kalibrierung dort an. Weitere Informationen zur Kalibrierung für ihr bestimmtes Gerät finden Sie bei Ihrem Headset-Hersteller.

## <a name="mixed-reality-portal-error-messages-and-problems"></a>Fehlermeldungen und Probleme im Mixed Reality-Portal

### <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Ich habe die Fehlermeldung "etwas ist falsch" angezeigt, oder es treten Probleme im Mixed Reality-Portal auf.

Windows Mixed Reality neu starten:
1. Trennen Sie beide Headset-Kabel von Ihrem PC.
2. Starten Sie Ihren PC neu.
3. Verbinden Sie Ihr Headset erneut.

Wenn dies nicht funktioniert, stellen Sie sicher, dass Ihr PC Ihr Headset erkennt:
1. Wählen Sie Starten.
2. Geben Sie "Geräte-Manager" in das Suchfeld ein, und wählen Sie es in der Liste aus. 
3. Erweitern Sie "gemischte Reality-Geräte", und überprüfen Sie, ob Ihr Headset aufgeführt ist. 

Wenn Sie nicht aufgeführt ist, versuchen Sie Folgendes:
1. Anschließen Sie das Headset an verschiedene Ports auf dem PC, falls verfügbar.
2. Überprüfen Sie, ob die neuesten Software Updates Windows Update.
3. Deinstallieren und Neuinstallieren von Windows Mixed Reality:
    1. Trennen Sie beide Headset-Kabel von Ihrem PC.
    2. Wählen Sie **Einstellungen > gemischte Realität > deinstallieren** aus.
    3. Wählen Sie **Einstellungen > Geräte > Bluetooth & andere Geräte** aus, um Ihre Bewegungs Controller zu entkoppeln. Wählen Sie jeden Controller aus, und wählen Sie dann "Gerät entfernen" aus.
    4. Anschließen Sie Ihr Headset wieder an Ihren PC, um Windows Mixed Reality neu zu installieren.
    
### <a name="im-getting-a-check-your-usb-cable-error-message"></a>Ich erhalte die Fehlermeldung "Ihr USB-Kabel überprüfen".

Stellen Sie eine Verbindung zwischen Ihrem Headset und einem anderen USB-Anschluss her (und stellen Sie sicher, dass es sich um einen USB-USB 3,0 Versuchen Sie außerdem, alle Extender oder Hubs zwischen dem Headset und dem Computer zu entfernen.

### <a name="im-getting-a-check-your-display-cable-error-message"></a>Ich erhalte die Fehlermeldung "Ihr Anzeige Kabel überprüfen".

Probieren Sie Folgendes aus:
* Stellen Sie eine Verbindung zwischen Ihrem Headset und einem Display Port 1,2 oder höher bzw. "HDMI 1,4" oder höher her. Stellen Sie sicher, dass der Port mit der fortschrittlichsten Grafikkarte auf Ihrem PC übereinstimmt.
* Wenn Sie einen Adapter verwenden, stellen Sie sicher, dass er 4K-fähig ist.
* Versuchen Sie, einen anderen HDMI-Port zu verwenden.
* Wenn Sie einen externen Monitor an einem HDMI-Port angeschlossen haben, versuchen Sie stattdessen, ihn an einen DisplayPort zu binden, und verwenden Sie den HDMI-Port für das Headset.


## <a name="something-went-wrong-error-codes-and-how-to-resolve-them"></a>Fehlercodes "etwas schief gegangen" und deren Behebung

| **Windows 10-Fehlercodes** (Version 1809/Versionen 1709, 1803) | **Fehlermeldung und Vorschläge zur Problembehandlung**                    |
|-------------------------------------------------------------|--------------------------------------------------------------------|
|   1-4 / 2197815297-4  | **Überprüfen Sie das Anzeige Kabel: Stellen Sie sicher, dass das Anzeige Kabel Ihres Headsets ordnungsgemäß angeschlossen ist.** <br/><br/><ol start="1"><li>Entfernen Sie die USB-und die-HDMI-Kabel Ihres Headsets, und binden Sie Sie dann wieder ein.</li><li>Überprüfen Sie Geräte-Manager, und vergewissern Sie sich, dass unter "Monitore" der Monitor "Mixed Reality Headset" vorhanden ist.</li><li>Stellen Sie sicher, dass Ihre Grafiktreiber auf dem neuesten Stand sind (von der Website Ihres Grafikkartenherstellers).</li><li>Wenn Sie einen Adapter zum Verbinden Ihres Headsets verwenden, stellen Sie sicher, dass [Windows Mixed Reality unterstützt](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)wird.</li><li>Wenn Ihre Grafikkarte sowohl Display Port-als auch HDMI-Ports aufweist, verwenden Sie den Display Port-Port auf Ihrer Grafikkarte, und verwenden Sie einen unterstützten gemischten Reality-Display-to-HDMI-Adapter.</li><li>Testen Sie einen anderen USB 3,0-Port auf Ihrem PC</li></ol> |
|   1-5 / 2197815297-5  | **Überprüfen Sie das Anzeige Kabel: Ihre Headset-Anzeige konnte nicht ordnungsgemäß initialisiert werden. Versuchen Sie, Ihren PC neu zu starten und das Headset erneut zu verbinden.**<br/><br/>Windows sieht ihren Headset-Monitor, aber Windows Mixed Reality hat Probleme bei der Kommunikation mit den anzeigen auf dem Mixed Reality-Headset. So beheben Sie dieses Problem:<br/><ol start="1"><li>Stellen Sie sicher, dass Ihre Grafiktreiber auf dem neuesten Stand sind (von der Website Ihres Grafikkartenherstellers).</li><li>Wenn Sie einen Adapter zum Verbinden Ihres Headsets verwenden, stellen Sie sicher, dass [Windows Mixed Reality unterstützt](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)wird.</li><li>Wenn Ihre Grafikkarte sowohl Display Port-als auch HDMI-Ports aufweist, verwenden Sie den Display Port-Port auf Ihrer Grafikkarte, und verwenden Sie einen unterstützten gemischten Reality-Display-to-HDMI-Adapter.</li><li>Versuchen Sie, den PC neu zu starten.</li></ol> |
|   7-1, 7-2, 7-3/2181038087-1, 2181038087-2, 2181038087-3  | **Bei Windows Mixed Reality treten Probleme beim Herstellen der Verbindung mit Ihrem Headset auf. Versuchen Sie, das Headset zu entstecken und es wieder in den Hintergrund zu überspringen.**<br/><br/>Das Mixed Reality-Headset konnte nicht vollständig initialisiert werden. Dies ist wahrscheinlich ein vorübergehender Fehler. Entfernen Sie Ihr Headset, und binden Sie es wieder ein, um dieses Problem zu beheben.
|   7-4 / 2181038087-4  | **Bei Windows Mixed Reality treten Probleme beim Herstellen der Verbindung mit Ihrem Headset auf. Versuchen Sie, das Headset zu entstecken und es wieder in den Hintergrund zu überspringen.**<br/><br/>Der Mixed Reality-Headset-Treiber konnte die Überwachungskameras auf dem Headset nicht initialisieren. Dies ist wahrscheinlich ein vorübergehender Fehler. Entfernen Sie das Headset, und schließen Sie es erneut ein, um dieses Problem zu beheben.
|   7-5 / 2181038087-5  | **Bei Windows Mixed Reality treten Probleme beim Herstellen der Verbindung mit Ihrem Headset auf. Versuchen Sie, Ihr Headset an einen anderen USB-Anschluss zu binden, und wiederholen Sie vorübergehend alle anderen USB-Geräte, die mit Ihrem PC verbunden sind.**<br/><br/>Die gemischte Windows-Realität hat die Synchronisierung zwischen den Zeitstempeln für den gemischten Reality-Kamera Rahmen und Ihren PC-Zeitstempeln verloren Dies kann ein vorübergehender Fehler oder ein Hinweis auf Probleme mit der USB-Signalintegrität sein. So beheben Sie dieses Problem:</li><li>Deinstallieren Sie vorübergehend alle USB-Geräte und Peripheriegeräte, entfernen Sie alle Erweiterungs Kabel, und binden Sie nur Ihr Headset ein.</li><li>Deaktivieren Sie alle USB-Suspend-/stromspeicherungs-Features auf Ihrem PC, wie z. b. selektive Suspend in den Windows-Energieoptionen, "zulassen, dass der Computer dieses Gerät ausschalten kann, um Energie zu sparen" in Geräte-Manager und alle USB-Energiespareinstellungen in der Firmware Ihres PCs.</li></ul>
|   7-6 / 2181038087-6  | **Es liegt ein Problem mit der Headset-Firmware vor. Versuchen Sie, das Headset zu entstecken und es wieder in den Hintergrund zu überspringen.** <br/><br/>Hierbei kann es sich um einen vorübergehenden Fehler handeln. Versuchen Sie, das Headset zu deaktivieren und erneut zu erstellen. Wenn dies nicht funktioniert:</li><li>Überprüfen Sie Windows Updates, um sicherzustellen, dass der neueste verfügbare Headset-Treiber ausgeführt wird.</li><li>Testen Sie Ihr Headset auf einem anderen PC. Wenn die gleiche Fehlermeldung angezeigt wird, muss Ihr Headset gewartet werden.</li></ul>
|   7-7 / 2181038087-7  | **Bei Windows Mixed Reality treten Probleme beim Herstellen der Verbindung mit Ihrem Headset auf. Versuchen Sie, Ihr Headset an einen anderen USB-Anschluss zu binden, und wiederholen Sie vorübergehend alle anderen USB-Geräte, die mit Ihrem PC verbunden sind.**<br/><br/>Der Mixed Reality-Headset-Treiber konnte die Firmware auf dem Headset nicht initialisieren. Hierbei kann es sich um einen vorübergehenden Fehler handeln. Versuchen Sie, das Headset zu deaktivieren und erneut zu erstellen. Wenn dies nicht funktioniert:<li>Temporäres deinstallösen von USB-Geräten und Peripheriegeräten, die Sie nicht benötigen, um Windows Mixed Reality auszuführen.</li><li>Überprüfen Sie Windows Updates, um sicherzustellen, dass Sie den neuesten verfügbaren Headset-Treiber ausführen.</li></ul>
|   7-11 / 2181038087-11 | **Ihre CPU ist zu alt, um mit Windows Mixed Reality kompatibel zu sein.**<br/><br/>Die Kompatibilitätsprüfung Ihres PCs ist fehlgeschlagen, da der CPU-Wert des AVX-Anweisungs Satzes fehlt, der für die Mixed Reality Motion-Controller erforderlich ist Sie benötigen einen [Windows Mixed Reality-kompatiblen PC](https://www.microsoft.com/en-us/windows/view-all-devices?col=wmr-pcs#icons).
|   7-12 / 2181038087-12 | **Ihr Headset ist mit einem inkompatiblen USB-Controller verbunden. Versuchen Sie, Ihr Headset an einen anderen USB-Anschluss zu binden, falls verfügbar. Oder versuchen Sie, einen Microsoft-USB-Treiber anstelle von nicht kompatiblen Treibern zu installieren.**<br/><br/>Ihr Headset kann an einen USB-Anschluss angeschlossen werden, der mit einem nicht-Microsoft-USB-Controller Treiber verbunden ist. Diese USB 3,0-Controller Treiber haben oft nicht die Möglichkeit, den [containerid-Deskriptor](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-containerids-in-windows)zu lesen und zu verarbeiten, der die unterschiedlichen Teile des Mixed Reality-Headsets in einer zusammenhängenden Einheit aggregiert (um Audioinhalte der richtigen Kopfhörer wiederzugeben, die richtigen Anzeige Videos auszuspielen und Verfolgungs Daten von den richtigen Sensoren abzurufen). So ändern Sie den USB-Controller Treiber <ol start="1"><li>Starten Sie Geräte-Manager.</li><li>Erweitern Sie die Kategorie für universelle serielle Buscontroller, und klicken Sie mit der rechten Maustaste, um den Treiber für jedes Element zu deinstallieren, das den Text "Extensible Host Controller" enthält **und** nicht "Microsoft" im Namen enthält.</li><li>Wählen Sie "Treibersoftware für dieses Gerät löschen" aus, um sicherzustellen, dass die alten Treiber entfernt werden.</li><li>Vergewissern Sie sich, dass jedes Element, das den Text "Extensible Host Controller" enthält, am Ende "Microsoft" enthält.</li><li>Plug-in für den HMD.</li></ol>Wenn das Problem zeitweilig auftritt, antwortet der HMD möglicherweise nicht ordnungsgemäß auf Befehle des HMD-Treibers. Um den Fehler zu beheben, entfernen Sie den HMD für 30 oder mehr Sekunden, und verbinden Sie ihn dann wieder. | 
|   7-13 / 2181038087-13 | **Ihr Headset ist mit einem inkompatiblen USB-Controller verbunden. Versuchen Sie, Ihr Headset an einen anderen USB-Anschluss zu binden, falls verfügbar. Andernfalls müssen Sie einen neuen USB 3,0-Controller installieren.**<br/><br/>Windows Mixed Reality kann die Zeitstempel des gemischten Reality-Kamera Rahmens nicht mit Ihren PC-Zeitstempeln synchronisieren. Dies ist höchstwahrscheinlich auf einen nicht kompatiblen USB 3,0-Host Controller zurückzuführen, der ITP (Isochronous Timestamp-Pakete) nicht unterstützt. Wenden Sie sich an Ihren PC-Hersteller, um festzustellen, ob ITP aktiviert werden kann, oder wechseln Sie zu einem anderen USB-Host Controller mit ITP |
|   7-14 / 2181038087-14 | **Bei Windows Mixed Reality treten Probleme beim Herstellen der Verbindung mit Ihrem Headset auf. Versuchen Sie, das Headset zu entstecken und es wieder in den Hintergrund zu überspringen.**<br/><br/>Bei Windows Mixed Reality treten Probleme beim Initialisieren des Anwesenheits Sensors auf dem Mixed Reality-Headset auf. In Geräte-Manager zeigt das Headset die Fehlermeldung "targethread konnte den Anwesenheits Sensor nicht initialisieren". So beheben Sie dieses Problem:<br/><ol start="1"><li>Entfernen Sie das Headset, und binden Sie es wieder ein. Stellen Sie sicher, dass das USB-Kabel vollständig angeschlossen ist.</li><li>Testen Sie einen anderen USB-Anschluss auf Ihrem PC.</li><li>Testen Sie Ihr Headset auf einem anderen PC, um festzustellen, ob das Headset vollständig in Geräte-Manager auf diesem PC aufzählt.</li><li>Überprüfen Sie, ob andere widersprüchliche versteckte Treiber auf Ihrem PC installiert sind, z. b. über die Tastatur oder Maus. (Suchen Sie nach allen versteckten Geräten in Geräte-Manager mit einem Fragezeichen Logo.)</li><li>Wenn Sie ein Samsung Mixed Reality-Headset mit Windows 10, Version 1709 oder Version 1803 verwenden, befolgen Sie die Anweisungen für den Fehlercode 2181038087-12, um zu überprüfen, ob auf dem USB 3,0-Controller ein nicht-Microsoft-USB-Controller-Treiber ausgeführt wird.</li></ol> |
|   7-15 / 2181038087-15 | **Windows Mixed Reality hat erkannt, dass ein inkompatibler winusb-Treiber installiert ist.**<br/><br/><ol start="1"><li>Stellen Sie sicher, dass der winusb-Treiber auf Ihrem PC in Windows enthalten ist und dass alle USB-Treiber von Drittanbietern die Kopie von winusb auf Ihrem PC nicht überschrieben haben.</li><li>Wenn das Problem weiterhin besteht, müssen Sie möglicherweise die Windows-Installation wiederherstellen oder neu installieren.</li></ol> |
|   13-11/-            | Im Mixed Reality-Portal ist ein App-Registrierungsproblem bei Windows aufgetreten. Überprüfen Sie das Anwendungs Ereignisprotokoll (mithilfe Ereignisanzeige), um festzustellen, ob weitere Details vorhanden sind. |
|   14-1/-            | Beim Mixed Reality-Portal treten Probleme beim Initialisieren des Grafik-und Kompositions Stapels auf. So beheben Sie dieses Problem:<ul><li>Desktopfenster-Manager (DWM, eine Schlüsselkomponente des Windows-Grafik Stapels) stürzt möglicherweise ab. Überprüfen Sie das Anwendungs Ereignisprotokoll (mithilfe Ereignisanzeige), um festzustellen, ob dies auftritt.</li><li>Versuchen Sie eine saubere Deinstallation Ihres Grafik Treibers, und installieren Sie dann den neuesten Grafiktreiber von der Website des Grafikkartenherstellers.</li></ul> |
|   14-2/C0001160-101  | **Es ist ein Problem beim Herstellen einer Verbindung mit Ihrem Headset aufgetreten. Versuchen Sie, eventuell verwendete Erweiterungs Kabel zu entfernen, und stellen Sie sicher, dass Sie das Headset mit dem richtigen Port für Ihre Grafikkarte verbunden haben. Wenn Sie Adapter verwenden, stellen Sie sicher, dass Sie mit gemischter Realität kompatibel sind. Wenn weiterhin Probleme auftreten, versuchen Sie, ihren Grafiktreiber zu aktualisieren.**<br/><br/>Die gemischte Realitäts Anzeige und der Kompositions Stapel konnten nicht initialisiert werden. Die Grafikkarte oder der Grafikkartentreiber Ihres PCs ist möglicherweise nicht kompatibel mit Windows Mixed Reality. So überprüfen Sie Folgendes: <ul><li>Überprüfen Sie, ob Ihr PC die minimalen Systemanforderungen für Windows Mixed Reality erfüllt.</li><li>Wenn Sie Dell-Inspiron 5577-PCs unter Windows 10, Version 1809 oder höher verwenden, wird dieser Fehler möglicherweise aufgrund eines Konflikts mit der nach Verarbeitungs Funktion von Dell-TrueColor-Grafiken angezeigt. Um dieses Problem zu umgehen, verwenden Sie die TrueColor-APP von Dell, um die TrueColor-Funktion zu deaktivieren, und versuchen Sie dann erneut, das Mixed Reality-Portal auszuführen.</li><li>Installieren Sie auf einem Desktop-PC den neuesten Grafiktreiber von der Website des Grafikkartenherstellers. Installieren Sie auf einem Laptop den neuesten Grafiktreiber für Ihr Make-und Model-Element auf der Website des Laptop Herstellers.</li><li>Wenn Sie über Drittanbieter Grafiken verfügen oder Software/Zubehör anzeigen, deinstallieren Sie diese apps und Treiber vorübergehend.</li><li>Wählen Sie "erneut versuchen", um festzustellen, ob es sich um ein vorübergehendes Problem handelt</li></ul> |
|   14-3/-             | **Es ist ein Problem beim Herstellen einer Verbindung mit Ihrem Headset aufgetreten. Versuchen Sie, eventuell verwendete Erweiterungs Kabel zu entfernen, und stellen Sie sicher, dass Sie das Headset mit dem richtigen Port für Ihre Grafikkarte verbunden haben. Wenn Sie Adapter verwenden, stellen Sie sicher, dass Sie mit gemischter Realität kompatibel sind. Wenn weiterhin Probleme auftreten, versuchen Sie, ihren Grafiktreiber zu aktualisieren.** <br/><br/><ul><li>Wenn Sie benutzerdefinierte Modi oder Aktualisierungs Raten für Ihren PC-Monitor verwenden, versuchen Sie, die Aktualisierungs Raten auf 60Hz festzulegen.</li><li>Stellen Sie sicher, dass alle von Ihnen verwendeten Adapter Windows Mixed Reality unterstützen.</li><li>Versuchen Sie, den neuesten Grafiktreiber von der Website des Grafikkartenherstellers zu installieren.</li><li>Klicken Sie auf "erneut versuchen", um festzustellen, ob es sich um ein vorübergehendes Problem</li></ul> |
| 14-4/-             | **Es ist ein Problem beim Herstellen einer Verbindung mit Ihrem Headset aufgetreten. Versuchen Sie, eventuell verwendete Erweiterungs Kabel zu entfernen, und stellen Sie sicher, dass Sie das Headset mit dem richtigen Port für Ihre Grafikkarte verbunden haben. Wenn Sie Adapter verwenden, stellen Sie sicher, dass Sie mit gemischter Realität kompatibel sind. Wenn weiterhin Probleme auftreten, versuchen Sie, ihren Grafiktreiber zu aktualisieren.** <br/><br/><ul><li>Auf Ihrem PC sind möglicherweise mehr PC-Monitore verbunden, als von dem Grafikadapter unterstützt werden können. Trennen Sie alle außer dem primären PC-Monitor.</li><li>Stellen Sie sicher, dass alle von Ihnen verwendeten Adapter Windows Mixed Reality unterstützen.</li><li>Installieren Sie den neuesten Grafiktreiber von der Website des Grafikkartenherstellers.</li><li>Klicken Sie auf "erneut versuchen", um festzustellen, ob es sich um ein vorübergehendes Problem</li></ul> |
|   15-5/-             | **Das Mixed Reality-Portal hat die Synchronisierung mit den wichtigsten gemischten Reality-und Windows-Komponenten, von denen es abhängt**<br/><br/><ul><li>Dies kann auf ein Leistungsproblem mit dem PC zurückzuführen sein. Stellen Sie sicher, dass die CPU, die GPU und die HDD nicht im Task-Manager gepeckt sind.</li><li>Trennen Sie vorübergehend alle anderen USB-Geräte von Ihrem PC.</li><li>Starten Sie Ihren PC neu.</li></ul> |
|   -/H0002000-0    | **Das Betriebssystem Ihres PCs wurde für Windows Mixed Reality in einen nicht übereinstimmenden Zustand versetzt.**<br/><br/>Überprüfen Sie Windows Updates auf Updates. |
|   -/S0002261-101, S0002361-101 | **Ein Problem mit einer Mixed Reality Shell-Komponente verhindert, dass das gemischte Reality-Portal ordnungsgemäß gestartet wird.**<br/><br/><ul><li>Öffnen Sie das Anwendungsprotokoll mithilfe Ereignisanzeige auf Ihrem PC, um zu dem Zeitpunkt, zu dem Sie versucht haben, Windows Mixed Reality zu starten, nach Anwendungs abstürzen zu suchen.</li><li>Stellen Sie sicher, dass Ihr Grafiktreiber auf dem neuesten Stand ist.</li><li>Der verwendete HDMI-Adapter ist nicht kompatibel mit Windows Mixed Reality. Weitere [Informationen finden Sie](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)unter unterstützter und empfohlener HDMI-zu-Mini-Anzeige Port (DP).</li></ul> |


## <a name="motion-controller-problems"></a>Bewegungs Controller Probleme

### <a name="my-motion-controllers-arent-working-properly"></a>Meine Bewegungs Controller funktionieren nicht ordnungsgemäß.

Wenn Ihre [Bewegungs Controller](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) nicht funktionieren, keine Verbindung herstellen oder wenn Sie kein Image der Controller sehen, wenn Sie Ihr Headset verwenden, versuchen Sie Folgendes:
1. Stellen Sie sicher, dass Ihre Controller eingeschaltet sind. Um diese zu aktivieren, drücken Sie die Windows-Taste für zwei Sekunden.
2. Stellen Sie sicher, dass die Controller vollständig abgerechnet werden, und ersetzen Sie die Akkus, wenn Sie nicht sind.
3. Schalten Sie die Controller ein-und ausschalten, während Sie diese vor Ihnen halten. Drücken Sie die Windows-Taste vier Sekunden, um einen Controller zu deaktivieren, und halten Sie ihn zwei Sekunden lang wieder gedrückt, um ihn zu aktivieren. 
4. Wählen Sie **Einstellungen > Geräte > Bluetooth & andere Geräte** auf Ihrem PC aus, und stellen Sie sicher, dass die Controller als paarweise aufgeführt sind. Wenn dies nicht der Fall ist, müssen Sie [Sie koppeln.](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) 
5. Stellen Sie sicher, dass die Motion-Controller als "verbunden" angezeigt werden. "Paarweise" bedeutet nicht notwendigerweise, dass die Controller mit dem PC verbunden sind. Controller sollten unter der Kategorie "Maus, Tastatur & Pen" angezeigt werden. Bewegungs Controller unter "andere Geräte" haben den paarungsprozess nicht bestanden und sind nicht funktionsfähig. Überprüfen der Motion Controllers-LEDs: hell leuchtende Controller sind paarweise gekoppelt und verbunden, dimly-Licht Controller sind nicht verbunden.
6. Wechseln Sie zu **Start > Mixed Reality-Portal** auf Ihrem PC, und wählen Sie "Menü" aus. Ihre Motion-Controller werden zusammen mit einer Statusmeldung angezeigt:
    * Bereit – die Controller sind alle festgelegt.
    * Verlorene Nachverfolgung – das gemischte Reality-Portal kann Ihre Controller nicht finden. Halten Sie diese vor dem Headset, und starten Sie Sie neu, indem Sie die Windows-Taste vier Sekunden lang drücken, und dann erneut 2 Sekunden.
    * Niedrige Akkukapazität – ersetzen Sie die Controller-Akkus.
7. Wenn Sie einen externen USB-Bluetooth-Adapter verwenden, stellen Sie sicher, dass er an einen schwarzen USB 2,0-Port angeschlossen ist. Außerdem sollte Sie so weit wie möglich von anderen drahtlos-und USB-Speich erwerken angeschlossen werden, einschließlich des USB-Verbindungs-Connector für Ihr Headset. 
8. Vergewissern Sie sich, dass nur ein Bluetooth-Radio im PC angezeigt wird, indem Sie mit der rechten Maustaste auf das Windows-Startmenü klicken und Geräte-Manager auswählen. Erweitern Sie den Abschnitt Bluetooth, und suchen Sie nach einem Adapter. Wenn Sie die Desktop-PC-Konfiguration mit dem integrierten Optionsfeld verwenden, überprüfen Sie, ob eine externe Antenne angeschlossen ist. Wenn keine externe Antenne verbunden ist, kann dies zu nach Verfolgungs Problemen führen. Oder verwenden Sie einen externen Bluetooth-Dongle (USB), deaktivieren Sie die interne Bluetooth-Funktion, und wiederholen Sie die Kopplung und Verbindung.
9. Schließen Sie das Fenster Bluetooth-Einstellungen, wenn es geöffnet ist. Wenn Sie im Hintergrund geöffnet ist, werden viele zusätzliche Aufrufe an das Bluetooth-Protokoll durchgeführt.
10. Überprüfen Sie die virtuelle Akku Ebene auf dem Motion-Controller. In gemischter Realität schalten Sie die Controller ein, und Sie können ein Akku Symbol sehen. Wenn Sie rot ist, ersetzen Sie die Batterie. Bei der Akku Berichterstattung wird in der Regel nach dem Verbinden eines Controllers die tatsächliche Ebene überschritten. Warten Sie ca. 15 Sekunden, damit sich der Akku Pegel stabilisiert, und lesen Sie dann die Ebene.
11. Entfernen Sie Bluetooth-Kopfhörer und-Sprecher in den **Einstellungen > Geräte > Bluetooth & anderen Geräten** , und schalten Sie die Geräte aus. Verwenden Sie den Head Phone Jack oder die integrierten Referenten Ihres Mixed Reality-Headsets, um das beste Audioerlebnis zu erzielen.
12. Wenn Sie über andere Bluetooth-Geräte verfügen, die mit Ihrem PC gekoppelt sind, wie z. b. Kopfhörer oder Gamepads, entfernen Sie einige davon. Wählen Sie **Einstellungen > Geräte > Bluetooth & andere Geräte auf Ihrem PC aus** , wählen Sie die Geräte aus, und wählen Sie dann "Gerät entfernen" aus.
13. Entfernen Sie das USB-Kabel auf Ihrem Headset, und binden Sie es wieder in den PC ein, um die Controller Funktionalität auf dem PC neu zu starten.
14. Controller Leuchten blinken, wenn Sie ein Firmwareupdate durchlaufen. Warten Sie, bis das Firmwareupdate fertiggestellt ist und die Controller in gemischter Realität angezeigt werden.
15. Stellen Sie sicher, dass Ihr PC mit einem 5-GHz-WLAN verbunden ist. Wenn Ihr Laptop mit einem Netzwerk mit 2,4 GHz WiFi verbunden ist, wird die Bluetooth-Verbindung normalerweise gemeinsam genutzt. Dies kann sich je nach Produkt Entwurf negativ auf die WiFi-oder Bluetooth-Leistung auswirken. Ändern Sie das bevorzugte Band in den Netzwerkadapter Einstellungen in 5 GHz. Wenn Ihr Netzwerk 5 GHz nicht unterstützt, kann ein Bluetooth-Dongle anstelle der internen Bluetooth-Funktion verwendet werden.
16. Wenn die Bluetooth-Einstellungen Motion-Controller bereits gekoppelt haben, erkennt Windows die neuen Geräte erst, wenn diese entfernt werden (wenn Sie mit einem bestimmten Ring hinzugefügt wurden, können Sie nur mit diesem Dongle entfernt werden).
17. Wenn Ihr PC über eine integrierte Bluetooth-Verbindung verfügt und Verbindungsprobleme auftreten, versuchen Sie stattdessen, einen USB-Bluetooth-Adapter zu verwenden. Zu diesem Zweck müssen Sie das integrierte Bluetooth-Radio in Geräte-Manager deaktivieren und dann Ihre anderen Bluetooth-Geräte mit dem neuen Adapter koppeln.

### <a name="motion-controller-troubleshooting-flowchart"></a>Flussdiagramm zur Problembehandlung von Motion Controller

![Problembehandlung bei Flussdiagrammen für Bewegungs Controller](images/motion-controllers.jpg)

### <a name="my-controller-is-stuck-in-an-infinite-reboot-buzzing-after-leds-cycle"></a>Der Controller befindet sich in einem unendlichen Neustart (wird nach dem LEDs-Zyklen gebuhlt).

Dies ist ein kritischer Akku Indikator. Stellen Sie also sicher, dass auf dem Gerät neue Akkus vorhanden sind. Wenn das Problem weiterhin auftritt, führen Sie die [Geräte Wiederherstellung](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) aus, um den Controller auf die Werkseinstellungen zurückzusetzen

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Ich versuche, meine Controller zu koppeln, aber Sie werden nie im Menü "Hinzufügen eines neuen Geräts" in den Bluetooth-Einstellungen angezeigt.

Stellen Sie fest, dass die Controller nicht bereits gekoppelt sind, entfernen Sie Sie, und versuchen Sie es noch mal. Wenn das Problem weiterhin auftritt, starten Sie den PC neu, und wiederholen Wenn dies nicht möglich ist, lesen Sie die häufig gestellten Fragen zu [Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)

### <a name="wi-fi-speeds-becomes-slow-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi-Geschwindigkeiten werden in meinem Notebook langsam, wenn Bewegungs Controller eingeschaltet werden.

Ihr Notebook kann seine Wi-Fi-Antenne für Bluetooth freigeben, wenn eine Verbindung mit dem 2,4-GHz-Zugriffspunkt besteht. Überprüfen Sie den Geräte-Manager, wenn Sie die Band Einstellung auf 5 GHz umstellen können. Wenn ein Netzwerk mit 5 GHz nicht verfügbar ist und die Leistung stark beeinträchtigt wird, sollten Sie eine Bluetooth-Ring Ausführung in Erwägung gezogen.

![Die Auswahl Einstellungen für WiFi-Band können über den Geräte-Manager gefunden werden](images/wifi5ghz.png)

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>Der zweite Controller benötigt lange Zeit, um die Verbindung wiederherzustellen.

Bei einigen älteren Intel-Radios tritt dieses Problem auf, wenn Bewegungs Controller gleichzeitig eingeschaltet werden. Vermeiden Sie das Einschalten von Controllern gleichzeitig.

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Mein Qualcomm-Bluetooth-Radio kann nach einem PC-Absturz keine Controller koppeln.

Qualcomm (QCA) für Bluetooth-Funk Treiber vor 10.0.0.448 kann nach einem Windows-Absturz zu einem ungültigen Status führen. Schalten Sie den PC vollständig aus, um dieses Problem zu umgehen. 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Ich sehe eine schlechte Controller Verfolgung mit "Marvell Radio".

Wechseln Sie zu **Geräte-Manager > Bluetooth > Marvell Avastar Bluetooth Radio Adapter > Properties > Driver** , und stellen Sie sicher, dass Sie Driver 15.68.9210.47 oder höher verwenden.

### <a name="the-mixed-reality-portal-is-working-but-my-motion-controllers-are-tracking-poorly-controllers-keep-flying-away-shaking-etc"></a>Das gemischte Reality-Portal funktioniert, aber die Motion-Controller werden unzureichend nachverfolgt (Controller werden immer weiter Weg, schütteln usw.).

1. Einige Beleuchtungsbedingungen können sich auf die Nachverfolgung auswirken. Stellen Sie sicher, dass Sie nicht für direktes Sonnenlicht verfügbar sind und dass Sie nicht über viele Point Light-Quellen für Ihren HMD verfügen (z. b. Zeichen folgen mit Lichtern wie eine Weihnachts Struktur). 
2. Überprüfen Sie die [Bluetooth-FAQs](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Diese Symptome werden im Allgemeinen durch Fehler bei der Kommunikation zwischen dem Controller und dem Host-PC verursacht und weisen auf eine schlechte Bluetooth-Link Qualität hin.

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Motion Controller-LEDs sind nicht beleuchtet, aber die Schaltflächen und der Finger Stick funktionieren weiterhin im Mixed Reality-Portal.

Der Verschiebe Cache für Motion Controller ist möglicherweise beschädigt. Um den Cache zu löschen, führen Sie den folgenden Befehl an einer Administrator Eingabeaufforderung aus:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Auf diesen Ordner kann in Windows Explorer nicht zugegriffen werden. er kann nur über eine Administrator Eingabeaufforderung geändert werden. Nachdem Sie den Ordner gelöscht haben, starten Sie den PC neu, und verbinden Sie Ihre Bewegungs Controller erneut, um die Kalibrierungs Dateien wiederherzustellen.

### <a name="motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Bewegungs Controller werden nicht in den steamvr-apps und spielen angezeigt.

Wenn Sie in der Lage sind, ihre Motion-Controller im Klippe-Haus, aber nicht in den steamvr-apps und-spielen anzuzeigen, ist der Motion Controller-Modell Treiber möglicherweise nicht ordnungsgemäß installiert. Dieser Treiber wird automatisch über Windows Update heruntergeladen und installiert. Wenn Sie jedoch auf einem PC mit Unternehmensrichtlinien arbeiten oder wenn Windows Update anderweitig eingeschränkt ist, müssen Sie diesen möglicherweise manuell installieren. So überprüfen Sie, ob der Motion Controller-Modell Treiber ordnungsgemäß installiert ist
1. Aktivieren Sie beide Motion-Controller, und stellen Sie sicher, dass Sie in der App "Einstellungen" unter **Geräte > Bluetooth & anderen Geräten** als "verbunden" angezeigt werden. Wenn Sie nicht als "paarweise" angezeigt werden, koppeln Sie [Sie](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality).
2. Öffnen Sie Geräte-Manager, und suchen Sie unter "Bluetooth" nach "Motion Controller-Left" und "Motion Controller-right".
3. Wählen Sie ein Gerät aus, und wechseln Sie dann zu **> Geräte nach Verbindung anzeigen** .
4. Nun sehen Sie eine Übersicht über die Rollup der Motion Controller-Bluetooth-Geräte in Ihrem Bluetooth-Radio. Unter dem gleichen Knoten wie die beiden Motion-Controller sollten zwei "Bluetooth HID Device"-Geräte sein, und unter jedem Bluetooth-Gerät sollten Geräte mit dem Namen "Motion Controller" (mit grauen Symbolen) angezeigt werden.
5. Doppelklicken Sie auf die Geräte "Motion Controller" und dann auf die Registerkarte **Treiber** . Vergewissern Sie sich, dass die aufgeführte Treiber Version einer [dieser Treiberversionen des Motion Controller-Modells](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history)entspricht.

Wenn Sie den Motion Controller-Modell Treiber manuell herunterladen und installieren möchten, besuchen Sie [Diese Seite](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) , und suchen Sie nach der Treiber Version, die Ihrer Version von Windows 10 entspricht. Installationsanweisungen finden Sie auf der Downloadseite.

### <a name="the-motion-controllers-firmware-update-takes-significantly-longer-than-two-minutes"></a>Das Firmwareupdate der Motion-Controller dauert deutlich länger als zwei Minuten.

Überprüfen Sie die [Bluetooth-FAQs](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Schlechte Bluetooth-Link Qualität ist in der Regel die Ursache für diese Probleme.

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Ich habe gerade neue Akkus eingefügt, aber die virtuelle Akku Ebene des Controllers weist nicht den vollständigen Grad auf.

Die Akku Ebene des Bewegungs Controllers ist auf AA-Akkus optimiert. Einige Akkus mit niedriger Spannung können nicht als vollständig gemeldet werden, obwohl Sie vollständig abgerechnet werden.

### <a name="my-controller-does-not-vibrate-when-battery-is-low"></a>Der Controller wächst nicht, wenn die Akkukapazität niedrig ist.

Die Haptik ist deaktiviert, wenn der Akku Pegel niedrig ist. Ersetzen Sie Ihre Batterien.

### <a name="my-device-vibrated-three-times-and-then-shutdown"></a>Mein Gerät wurde dreimal vibriert und dann heruntergefahren.

Ihre Akkus laufen niedrig und erreichen den Schwellenwert für die Grenze. Ersetzen Sie Ihre Batterien.

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Der Touchpad meines Samsung Motion Controller ist offline oder verfügt über eine unzustellbare Stelle.

Dabei handelt es sich wahrscheinlich um einen Hardwarefehler, und Sie sollten sich für einen Austausch oder Austausch an Ihren Händler oder Gerätehersteller wenden.

### <a name="the-controller-isnt-working-correctly-and-i-cant-update-the-device"></a>Der Controller funktioniert nicht ordnungsgemäß, und ich kann das Gerät nicht aktualisieren.

Stellen Sie Sie in den Werk Zuständen wieder her (Sie benötigen neue Akkus):
1. Entfernen Sie die Controller, und schalten Sie Sie aus.
2. Öffnen Sie die Batterieabdeckung.
3. Fügen Sie Ihre neuen Akkus ein.
4. Halten Sie die Schaltfläche "Kopplung" gedrückt (die Registerkarte unten unter den Akkus).
5. Schalten Sie den Controller beim halten der Schaltfläche "Kopplung" ein, indem Sie die Windows-Schaltfläche fünf Sekunden lang gedrückt halten (beide Schaltflächen werden gedrückt).
6. Geben Sie die Schaltflächen frei, und warten Sie auf den Einschalten des Controllers. Dieser Vorgang dauert bis zu 15 Sekunden, und es gibt keine Indikatoren, wenn die Geräte Wiederherstellung stattfindet. Wenn Geräte direkt auf der Schaltflächen Freigabe einschalten, wurde die Schaltflächen Sequenz der Wiederherstellung nicht registriert, und Sie müssen den Vorgang wiederholen.
7. Wechseln Sie zu **Einstellungen > Bluetooth > andere Geräte** , und wählen Sie "Motion Controller-Left" oder "Motion Controller-right" und "Remove Device") aus, um alte Controller Zuordnungen aus den Bluetooth-Einstellungen zu entfernen. 
8. Koppeln Sie den Controller erneut mit dem PC.
9. Nachdem eine Verbindung mit dem Host und HMD hergestellt wurde, wird das Gerät auf die neueste verfügbare Firmware aktualisiert.

### <a name="lights-and-indicators"></a>Beleuchtung und Indikatoren

Der Ansichts Bund der LED und die Haptik geben den Zustand des Bewegungs Controllers an.

| State    | Ursache für den Status | Licht-und Schwingungsverhalten, das dem Zustand zugeordnet ist |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Einschalten**               | Drücken Sie die Windows-Taste auf dem Controller für zwei Sekunden, um den Controller einzuschalten.       | LEDs aktivieren und Controller werden einmal vibriert. |
| **Ausschalten**              | Drücken Sie die Windows-Taste auf dem Controller vier Sekunden, um den Controller zu deaktivieren.      | LEDs werden ausgeschaltet, und der Controller wird zweimal vibriert. |
| **Ruhezustand**               | Der Controller wechselt automatisch in den Ruhezustand, wenn er sich 30 Sekunden lang nicht bewegt. Der Controller wird automatisch aktiviert, wenn er eine Bewegung erkennt, außer wenn das Gerät nicht mit dem Host-PC gekoppelt ist. In diesem Fall ist ein Schaltflächen-Press zum Aktivieren erforderlich. | LEDs werden im Ruhezustand alle drei Sekunden ausgeschaltet und blinkt. |
| **Pairing**                | Halten Sie die Schaltfläche "Kopplung" in Akku Buchstaben für drei Sekunden gedrückt.     | LEDs langsam, während Sie sich im Paarmodus befinden, und gehen beim Beenden des Paarmodus solide. Der Controller wird einmal skaliert, wenn die Kopplung erfolgreich war, oder dreimal, wenn die Kopplung nicht erfolgreich ist und ein Timeout auftritt. |
| **Der Controller verbindet/trennt die Verbindung mit dem PC.** | Der Controller stellt nach dem Einschalten erfolgreich eine Verbindung mit dem PC her, oder der Controller trennt sich während der Verwendung aus irgendeinem Grund mit dem PC.| Der Controller vibriert einmal auf der PC-Verbindung oder der Verbindungs Trennung. |
| **Niedriger Akku Pegel**      | Der Akku Pegel ist niedrig.| Wenn die Akkukapazität gering ist, gibt es keine LED-oder Vibrations Anzeige. Es ist ein Akku Indikator Symbol auf dem Handle der Controller Darstellung im Headset vorhanden. Wenn die Akkukapazität gering ist, wird im Indikator Symbol 1/4 vollständig angezeigt. |
| **Kritischer Akku Pegel** | Beim Einschalten, wenn der Akku Pegel "kritisch" ist. "Critical" Akku Level bedeutet, dass die Stromversorgung unzureichend ist und der Controller automatisch ausgeschaltet wird.| Der Controller wird dreimal vibriert, wenn Sie ihn einschalten und dann automatisch ausschalten. Wenn Sie sich diesen Status nähern, wird das Symbol für den Akku Indikator rot angezeigt. |


### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Wie kann ich erkennen, ob ich Bluetooth-Technologie verwende?

Motion-Controller verwenden die gleiche Bluetooth-Technologie auf vielen consumergeräten und sind für die Arbeit mit der Bluetooth-Funktion auf dem neuesten PC konzipiert. So überprüfen Sie, ob Ihr PC über ein Bluetooth-Radio verfügt (wenn das Gerät die gemischte Reality-Kompatibilitätsprüfung überschritten hat): 
* Klicken Sie mit der rechten Maustaste auf das Windows-Startmenü, und wählen Sie Geräte-Manager aus. 
* Erweitern Sie den Abschnitt Bluetooth, und suchen Sie nach einem Adapter. 
* Wenn Ihr PC nicht über Bluetooth verfügt, empfiehlt es sich, den [plugbaren USB-USB-Bluetooth 4,0 Low Energy Micro-Adapter](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom)zu erhalten.
![Screenshot eines Beispiel Geräte-Manager. Der Adapter ist das Bluetooth-Radio.](images/devicemanagerbtadapterpic.png) 


### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-motion-controllers"></a>Mein PC verfügt über Bluetooth-Technologie, aber ich habe Probleme mit den Motion-Controllern.

Motion-Controller sollten mit anderen Bluetooth-Tastaturen,-Mäusen und Spiel Controllern arbeiten, aber das Verhalten variiert abhängig vom Modell der Tastatur, der Maus oder des Spiel Controllers, den Sie verwenden. Im folgenden finden Sie einige Möglichkeiten, um die Leistung zu verbessern:
* Wenn Ihr Computer über Bluetooth verfügt, Sie aber weiterhin Probleme mit den Motion-Controllern haben, empfiehlt es sich, Ihr Bluetooth-Radio durch den steckbaren externen Bluetooth-Adapter zu ersetzen, der an USB angeschlossen ist Beachten Sie, dass Sie jeweils nur einen Bluetooth-Funk Adapter aktiv haben können. Wenn Sie ein externes Radio zusätzlich zu einem vorhandenen Radio anschließen, müssen Sie das vorhandene Bluetooth-Radio in Geräte-Manager deaktivieren (Klicken Sie mit der rechten Maustaste auf den Adapter, und wählen Sie "Gerät deaktivieren"), und verwenden Sie alle vorherigen Bluetooth-Geräte.
* Wenn Sie einen USB-Bluetooth-Adapter verwenden, verbinden Sie ihn mit einem USB 2,0-Port (2,0 Ports sind schwarz und sind nicht als "SS" gekennzeichnet), falls verfügbar. Der Port sollte physisch von folgenden getrennt getrennt werden:
    - der HMD-USB-Connector
    - Flash Laufwerke
    - Festplatten
    - bei drahtlosen USB-Empfängern, wie z. b. bei Tastaturen/Mäusen, wird der USB-Bluetooth-Adapter so weit wie möglich von diesen anderen Connectors an die gegenüberliegende Seite des Computers angeschlossen.
* Installieren Sie keine Drittanbieter Software.
* Schließen Sie das Fenster Bluetooth-Einstellungen, wenn es geöffnet ist. Wenn Sie es im Hintergrund geöffnet belassen, werden viele zusätzliche Aufrufe an das Bluetooth-Protokoll durchgeführt.
* Deaktivieren Sie die Einstellung "Benachrichtigung zum Herstellen einer Verbindung mit dem SWIFT-paar anzeigen" unter Bluetooth & anderen Geräten, um die Aktivität zum Überprüfen der Radio Aktivierung
* Wenn Sie eine interne Bluetooth-Karte verwenden, stellen Sie sicher, dass Sie eine externe Bluetooth-Antenne verwenden. 
  * Fehlende externe Bluetooth-Antennen in diesem Fall können nach Verfolgungs Problemen führen. 
  * Wenn dies nicht funktioniert, verwenden Sie nach dem Deaktivieren des internen Bluetooth einen externen Bluetooth-Dongle (USB).
* In den Bluetooth-Einstellungen ist es wichtig, dass das Gerät unter der Kategorie "Maus, Tastatur & Pen" angezeigt wird. Wenn unter "andere Geräte" angezeigt wird, entkoppeln und koppeln Sie das Gerät.
* Entfernen Sie Bluetooth-Kopfhörer und-Sprecher, und schalten Sie Sie aus. Diese werden in der gemischten Realität von Windows nicht unterstützt. Sie können den Head Phone Jack oder die integrierten Referenten Ihres Mixed Reality-Headsets verwenden, um die beste Audiodarstellung zu erzielen.

### <a name="how-can-i-pair-my-motion-controllers-to-a-windows-mixed-reality-headset-with-built-in-bluetooth-radio-or-return-them-to-their-factory-pairing"></a>Wie kann ich meine Motion-Controller mit einem Windows Mixed Reality-Headset mit integrierter Bluetooth-Funk Funk Kopplung koppeln oder Sie an Ihre Werks Kopplung zurückgeben?

Einige Windows Mixed Reality-Headsets, einschließlich der Tools "Acer Ojo 500" und "Samsung Odyssee +", verfügen über integrierte Bluetooth-Radios für die Verwendung mit Motion-Controllern. Die Motion-Controller, die mit diesen Headsets geliefert werden, sind mit dem Headset von der Factory vorab gekoppelt, und es ist nicht erforderlich, dass Ihr PC über ein separates Bluetooth-Radio verfügt. Diese Motion-Controller _können_ manuell mit dem Bluetooth-Radio Ihres PCs gekoppelt werden, z. b. für die Verwendung mit Windows Mixed Reality-Headsets, die nicht über integrierte Bluetooth-Radios verfügen. Führen Sie die Geräte Begleit Anwendung des Headsets aus (z. b. die app "Acer Ojo 500" oder die app "Samsung HMD Odyssee + Setup", die bei der erstmaligen Anmeldung des Headsets automatisch installiert wird), um die Bewegungs Controller an Ihre Factory-Kopplung zurückzugeben, und befolgen Sie die Anweisungen für Motion Controller-Kopplung.


## <a name="performance-questions"></a>Fragen zur Leistung

### <a name="how-can-i-tell-if-the-windows-mixed-reality-headset-is-rendering-at-60hz-or-90hz-framerate"></a>Wie kann ich erkennen, ob das Windows Mixed Reality-Headset bei 60Hz oder 90Hz Framerate rendert?

Überprüfen Sie die Registerkarte **Leistung des Geräte Portals >** . 

**Hinweis** : Wenn Sie über ein diskretes GPU mit 2,0-Ports und eine CPU mit vier oder mehr physischen Kernen verfügen, sollten Sie 90 Hz erhalten. Wenn Ihre GPU nur über die Ausgabe "HDMI 1,4" verfügt, können Sie als Problem Umgehung einen DisplayPort für den [2,0 HDMI-Adapter](https://holodocswiki.com/wiki/Recommended_adapters_for_Windows_Mixed_Reality_Capable_PCs) verwenden. 

**Hinweis** : die **> für die visuelle Qualität** wirkt sich nur auf das Rendering der Windows Mixed Reality-Umgebung aus.

### <a name="what-do-i-do-if-my-pc-appears-to-be-running-slowly"></a>Was kann ich tun, wenn mein PC langsam ausgeführt wird?

Das System kann aus vielen Gründen träge sein, und in den meisten Fällen wird dies nach wenigen Sekunden untersucht. Wenn dieses Problem über einen längeren Zeitraum auftritt:
1. Schließen Sie die gesamte nicht verwendete Anwendung auf dem Desktop.
2. Stellen Sie sicher, dass Ihr Laptop an eine Stromquelle angeschlossen ist.
3. Stellen Sie sicher, dass der PC nicht aufwärmt.
4. Verringern Sie die visuelle Qualität in Ihrer Windows Mixed Reality-Startseite.
5. Stellen Sie sicher, dass Sie über die neuesten Grafiktreiber für Ihren PC verfügen (Weitere Informationen finden Sie im Abschnitt Grafiktreiber).

### <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Der PC wird beim Ausführen der gemischten Realität erwärmt. Gewusst wie bleiben Sie dabei cool?

1. Stellen Sie sicher, dass der Akku belastet und die Stromquelle angeschlossen ist.
2. Stellen Sie sicher, dass die Fans, die auf dem PC Luft-oder ausgehenden, nicht blockiert werden.
3. Verwenden Sie den PC in einer relativ kalten Umgebung.
4. Stellen Sie sicher, dass keine Wärmequellen (z. b. Sun oder Heat Vents) auf dem PC angezeigt werden.

### <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Meine visuellen Elemente sind choppy, werden langsam geladen oder sind nicht gut geeignet.
* Stellen Sie sicher, dass Ihr Headset an der richtigen Grafikkarte auf Ihrem PC angeschlossen ist. Einige PCs verfügen sowohl über integrierte als auch diskrete Grafikkarten. Die diskrete Karte bietet im Allgemeinen die beste Leistung. [Erfahren Sie mehr über PC-Hardware](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).
* Schließen Sie nicht verwendete Anwendungen auf Ihrem Desktop.
* Stellen Sie sicher, dass Ihr Headset passend ist (verschieben Sie es nach unten und nach links und rechts zum Anpassen).
* Passen Sie die visuellen Einstellungen Ihres Headsets in den **Einstellungen > gemischte Realität > die Headset-Anzeige** an. Wenn "visuelle Qualität" auf "automatisch" festgelegt ist, wählen wir die beste gemischte Realität für Ihren PC aus. Legen Sie "visuelle Qualität" auf "hoch" fest, um ein visuelles Detail zu erhalten. Wenn Ihre visuellen Elemente in einem choppy-Wert vorliegen, können Sie eine niedrigere Einstellung auswählen.
* Versuchen Sie, die Kalibrierung Ihres Headsets anzupassen. Die Linsen sollten angepasst werden, damit Sie mit dem interpupillary Distance (IPD), dem Abstand zwischen ihren Schülern, identisch sind. Wenn Sie Ihre IPD nicht kennen, sollte optomezyst in der Lage sein, Sie für Sie zu messen. Es gibt auch Websites, mit denen IPD gemessen werden soll. Wenn Sie Ihre IPD kennen, verwenden Sie den Kalibrierungs Knopf Ihres Headsets, um Anpassungen vorzunehmen. Wenn das Headset keinen Kalibrierungs Knopf hat, wählen Sie **Einstellungen > gemischte Realität > Headset-Anzeige** aus, und passen Sie das "kalibrierungssteuerelement" an.


## <a name="tracking-system-problems"></a>System Probleme beim Nachverfolgen

### <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>Das System kann die Grenze nicht finden, und es wird eine Setup Benutzeroberfläche angezeigt.

Dies bedeutet, dass das Überwachungssystem Ihre Umgebung nicht erkennen konnte. Wenn Sie sich in einer neuen Umgebung befinden, müssen Sie die [Grenze](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)einrichten. Wenn Sie das Gerät zuvor in dieser Umgebung verwendet haben und eine Grenze eingerichtet haben:
* Stellen Sie sicher, dass der Raum genug hell ist.
* Stellen Sie sicher, dass Sie das Gerät übertragen und sich den Raum angesehen haben. Das Gerät muss Ihre Umgebung überwachen, um zu wissen, wo es sich befindet. Die Grenzen werden nicht angezeigt, wenn Sie sich auf einem Schreibtisch oder einer Tabelle befinden.
* Entfernen Sie das Gerät, schließen Sie Windows Mixed Reality, und schließen Sie das Gerät erneut ein.
* In Ihrer Umgebung wurde möglicherweise etwas geändert, das vom Gerät nicht mehr erkannt wird. Versuchen Sie, eine neue Grenze einzurichten.

Wenn das Problem durch diese Schritte nicht behoben werden kann, löschen Sie die Umgebungs Daten, und richten Sie die Grenze erneut ein.

### <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>Das System stellt mir die Benutzeroberfläche zur Verfügung, die mich auffordert, Setup für alle Benutzeroberflächen auszuwählen, und ich sehe die Grenzen.

Es dauert zu lange, bis die Grenzen des Geräts gefunden werden. Sie können diese Meldung umgehen, indem Sie die Option auswählen, eine Grenze zu verwenden, und Sie werden zu Ihrem Windows Mixed Reality-Home mit ihren Grenzen gelangen.

### <a name="i-frequently-see-a-message-saying-ive-lost-my-bounds"></a>Ich sehe häufig eine Meldung, die besagt, dass ich meine Begrenzungen verloren habe.

Das Überwachungssystem verfügt über eine schwierige Zeit Verfolgung und Identifizierung Ihrer Umgebung. In diesem Zustand kann das Gerät ihre Grenzen nicht mehr anzeigen, und das Headset wechselt zu 3DOF, damit Sie nicht mehr auf die Dinge in der realen Welt stoßen können, bis es ihre Grenzen wiederfindet. So beheben Sie dieses Problem:
1. Stellen Sie sicher, dass der Raum genug hell ist.
2. Führen Sie das Setup erneut aus, wenn Sie den Raum vor kurzem erneut erstellt oder neu modelliert haben.
3. Entfernen Sie das Gerät, schließen Sie Windows Mixed Reality, und schließen Sie es wieder ein.
4. Löschen Sie die Umgebungs Daten, und richten Sie das Gerät erneut ein.
5. Wenn die Nachricht weiterhin besteht, wenden Sie sich an den Kundensupport.

### <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Ich kann sehen, aber ich kann nicht übersetzt werden (ich bin in 3DOF stecken).

Dies bedeutet, dass das Überwachungssystem keine Pose generieren kann, oder die Anwendung die Verwendung neuer posiingdaten zum Rendering beendet hat. Überprüfen Sie Folgendes:
* Stellen Sie sicher, dass der Raum genug hell ist.
* Stellen Sie sicher, dass für den Raum genügend Details zur Verfolgung vorhanden sind.
* Entfernen Sie das Gerät, schließen Sie Windows Mixed Reality, und schließen Sie das Gerät erneut ein.
* Wenden Sie sich an den Kundensupport, wenn die Meldung weiterhin

### <a name="the-view-in-the-hmd-is-completely-frozen"></a>Die Ansicht im HMD ist vollständig fixiert.

Dies bedeutet in der Regel, dass die Anwendung oder eine Komponente auf Systemebene fehlgeschlagen ist. Versuchen Sie Folgendes:
1. Klicken Sie auf die Schaltfläche "Home", um die Anwendung zu verlassen.
2. Entfernen Sie das Gerät, schließen Sie die MRP, und schließen Sie das Gerät wieder ein.
3. Starten Sie den PC neu.

### <a name="i-frequently-see-a-black-border-around-the-edges-of-the-view-in-the-hmd-sometimes-it-looks-like-im-looking-down-a-tunnel"></a>Ich sehe häufig einen schwarzen Rahmen um die Ränder der Ansicht im HMD. Manchmal sieht es so aus, als würde ich einen Tunnel suchen.

Dies bedeutet, dass die Anwendung nicht in der Lage ist, die Framerate auf Ihrem PC zu erreichen, und dass das System alte Frames verwendet, um die Ansicht im HMD zu erzeugen. Da Anwendungen nur den Teil der Welt Rendering, wenn Sie nicht konstant ihre Frameraten erreichen, versucht das System, die Welt aus einer vorherigen Sicht zu Rendering, und gibt die fehlenden Details mit schwarz aus. Wenn dies häufig auftritt:
1. Schließen oder beenden Sie alle nicht benötigten Programme, um Arbeitsspeicher und CPU freizugeben.
2. Reduzieren Sie die Detaileinstellungen in Ihrer Anwendung.
3. Reduzieren Sie die Detaileinstellungen in den Windows Mixed Reality-Einstellungen.

### <a name="the-view-in-the-hmd-is-jittering-and-stuttering-a-lot"></a>Die Ansicht in der HMD ist JITing und wird sehr viel zu einer großen Menge.

Dies kann verschiedene Gründe haben. Die Hauptursachen sind, dass das System keinen Inhalt für das Headset renderingfähig ist, oder das Überwachungssystem hat Probleme. Überprüfen Sie Folgendes:
1. Stellen Sie sicher, dass Ihr PC nicht unter Ressourcenkonflikten liegt. Öffnen Sie den Task-Manager, und stellen Sie sicher, dass Ihre computeressourcen kostenlos sind (z. b. 80% CPU Free, 400MB RAM und Datenträger-e/a unter 80%)
2. Stellen Sie sicher, dass Sie über die neuesten Grafiktreiber für die Hardware verfügen. Weitere Informationen finden Sie im Abschnitt Grafiktreiber.
3. Stellen Sie sicher, dass der Raum genug hell ist.
4. Entfernen Sie das Gerät, schließen Sie Windows Mixed Reality, und schließen Sie das Gerät erneut ein.
5. Starten Sie Ihren PC neu.
6. Wenn das Problem weiterhin besteht, wenden Sie sich an den Kundensupport.

### <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-before-returning-to-normal"></a>Die Welt wurde kurz vor der Rückkehr zur normalen Umgebung kurz geblinkt und möglicherweise gekippt oder geflippt.

Dies kann darauf zurückzuführen sein, dass eine APP oder eine Komponente auf Systemebene auf einen schwerwiegenden Fehler oder einen temporären Mangel an Arbeitsspeicher oder CPU-Ressourcen stößt. Überprüfen Sie Folgendes:
1. Öffnen Sie den Task-Manager, und stellen Sie sicher, dass Sie über mindestens 20% CPU-und 400 MB Arbeitsspeicher verfügen (z. b. 80% CPU-frei, 400 MB RAM und Datenträger-e/a unter 80%).
2. Öffnen Sie "Ereignisanzeige", und wechseln Sie zu **Windows-Protokolle > Anwendungs-und Fehler** Ereignis Einträge zum Zeitpunkt der Sperrung. Überprüfen Sie, ob Prozesse abgestürzt sind.
3. Starten Sie den PC neu, wenn das Problem weiterhin besteht.

### <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>Die Welt wurde kurz nach unten gedreht und wieder normal zurückgegeben.

Dies wird in der Regel durch Fehler beim Abrufen von Sensordaten aus dem Headset verursacht, um die Verfolgungs Algorithmen zu informieren. Wenn dies häufig auftritt:
1. Anschließen Sie das Headset an einen anderen USB 3,0-Port.
2. Anschließen Sie das Headset direkt in den PC und nicht in einen USB 3,0-Hub.
3. Wenn das Problem weiterhin besteht, wenden Sie sich an den Kundensupport.

### <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-fine-in-windows-mixed-reality"></a>Die Welt ist gekippt, aber ich kann in der gemischten Realität von Windows problemlos navigieren und Sie durchlaufen.

Dies wird in der Regel dadurch verursacht, dass Sensordaten Fehler in den auf Ihrem PC gespeicherten Umgebungs Daten aufgezeichnet werden. Dies kann dazu führen, dass die gemischte Windows-Realität (manchmal auch dauerhaft) gekippt erscheint. Probieren Sie Folgendes aus:
1. Entfernen Sie den HMD, schließen Sie Windows Mixed Reality, und schließen Sie das Headset wieder ein.
2. Starten Sie den PC neu.
3. Löschen Sie die Umgebungs Daten.

## <a name="webvr-questions"></a>Fragen zu webvr

### <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Warum werden meine Controller nicht angezeigt, wenn Sie den VR-Inhalt von Edge anzeigen?

Nicht alle webvr-Inhalte werden zur Unterstützung von Bewegungs Controllern erstellt. Webvr ermöglicht Entwicklern von Inhalten, verschiedene Arten von Eingaben zu unterstützen, z. b. Spiele Controller oder Bewegungs Controller. Wenn Ihre Controller an einem Standort nicht angezeigt werden, ist die Unterstützung von Motion Controller wahrscheinlich nicht vorhanden.

### <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Warum kann ich die Maus nicht in einer immersiven webvr-Ansicht verwenden?

Dies ist ein optionales Feature der webvr-Spezifikation. Diese Funktion wird nicht von allen Browsern unterstützt, und nicht alle webvr-Inhalte werden zur Unterstützung von Maus Eingaben erstellt. Webvr ermöglicht Inhalts Entwicklern die Unterstützung verschiedener Eingabetypen, z. b. Maus, Tastatur, Spiele Controller oder Bewegungs Controller. Das Verhalten der Maus Eingaben variiert je nach Browser. Innerhalb von Microsoft Edge müssen Website Autoren sicherstellen, dass Sie "pointerlock" verwenden, wenn Sie dem Headset präsentieren, damit die Maus Eingaben funktioniert.

### <a name="why-does-my-controller-look-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Warum sieht der Controller wie ein "Vive/Oculus" aus, hat eine seltsame Ausrichtung, oder die Schaltflächen sind falsch zugeordnet?

Die Website verfügt wahrscheinlich nicht über vollständige Motion Controller-Unterstützung.

### <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardiannew-york-times-etc-from-edge-in-vr"></a>Warum kann ich keine Videos zu 360-Grad-Videos von YouTube/Facebook/Vimeo/der Wächter/New York-Zeiten usw. von Edge in VR anzeigen?

Ebenso wie jede andere Webanwendung oder der Standard-Standard hat der Autor die Möglichkeit, Sie zu implementieren. Es gibt eine webvr-Spezifikation, die es Websites ermöglicht, VR-Erlebnisse direkt aus dem Browser zu starten, und die Autoren dieser Websites haben diese Spezifikation zu diesem Zeitpunkt nicht implementiert. Möglicherweise können apps auf einigen Plattformen heruntergeladen werden, die die Anzeige von VR-Inhalten von diesen Anbietern ermöglichen.

### <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Warum kann ich VR aus Firefox oder Chrome nicht eingeben?

Webvr wird zurzeit nur von Windows Mixed Reality-Geräten in Edge unterstützt.

### <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Warum wird bei der Eingabe von VR von einer Website ein leerer Bildschirm in meinem Headset angezeigt?

Die-Website hat möglicherweise keine Unterstützung für multigpu-Computer (einschließlich hybridgpu-Laptops) implementiert. Versuchen Sie Folgendes:
* Laden Sie die Seite neu.
* Binden Sie das Headset auf Desktop Computern an denselben Grafikadapter wie den Monitor, der Microsoft Edge anzeigt. Verbinden Sie beide mit der höher gestützten Grafikkarte, nicht mit dem integrierten Grafikadapter.

### <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Beim Beenden von VR beim Anschauen eines Videos von Edge wird der Sound weiterhin abgespielt, aber das Fenster Edge ist ausgegraut.

Dies ist ein bekanntes Problem beim Ausführen von webvr von Edge in der gemischten Realität cliffhouse. Um dieses Problem zu beheben, drücken Sie auf der Tastatur die Tastenkombination, anstatt die Windows-Taste zu drücken, um die webvr-Oberfläche zu beenden, oder aktivieren Sie das ausgelöerte Rand Fenster, indem Sie es auswählen und das Video beenden

### <a name="can-i-use-webvr-on-the-hololens"></a>Kann ich webvr auf den hololens verwenden?

Microsoft hat an dieser Stelle noch nichts über webvr in den hololens angekündigt.

### <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Warum wird meine Ansicht beim Anzeigen von webvr-Inhalten von Edge auf der Floor-Ebene angezeigt?

Die Website unterstützt Windows Mixed Reality-Headsets nicht ordnungsgemäß. Dieses Problem können Sie folgendermaßen umgehen:
1. Platzieren Sie das Headset in der Etage Ihres Leerraums.
2. Navigieren Sie zur webvr-Seite mithilfe von Microsoft Edge auf Ihrem Desktop (nicht innerhalb gemischter Realität).
3. Klicken Sie auf die Schaltfläche auf der Webseite, um VR einzugeben.
4. Warten Sie 5-10 Sekunden, bis die Leistung vollständig in den immersiven Modus wechselt.
5. Wählen Sie das Headset aus, und platzieren Sie es auf dem Kopf.

### <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>Die Anzeige ist bei einigen webvr-Erfahrungen sehr gering.

Die Websites unterstützen keine großen Lösungen mit hoher Auflösung. So umgehen Sie dieses Problem:
* Wenn Sie webvr über den Desktop starten (im Gegensatz zum von der gemischten Realität cliffhouse), stellen Sie sicher, dass das Fenster vor der Eingabe von VR maximiert ist.
* Vermeiden Sie das Ändern der Größe des Microsoft Edge-Fensters, nachdem Sie VR eingegeben haben.

### <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Warum wird die webvr-immersive Ansicht beendet, wenn ich Browser Registerkarten ändere?

Dieses Verhalten wird erwartet. Aus Sicherheitsgründen kann nur die Registerkarte Active Browser auf verbundene Headsets zugreifen.

### <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Warum kann ich Audiodaten zu einem bestimmten webvr-Erlebnis nicht hören?

Die Website verwendet möglicherweise das Format der OGG-Audiodatei, das Microsoft Edge derzeit nicht unterstützt.

Sie können fehlerhafte Websites direkt an das Microsoft Edge-Browser Team in der [Problem](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)Verfolgung oder per Twitter über [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)Berichten.

### <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Warum funktioniert das haptische Feedback nicht in webvr mit Motion-Controllern?

Microsoft Edge unterstützt zurzeit keine Haptik in den webvr-Gamepad-API-Erweiterungen.


## <a name="steamvr-questions"></a>Fragen zu steamvr

### <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-immersive-headset"></a>Wie kann ich steamvr-Spiele in meinem Windows Mixed Reality-immersiven Headset abspielen?

Sie müssen Windows Mixed Reality für steamvr auf Ihrem PC installieren und steamvr einrichten:
* [Herunterladen und Installieren von steamvr](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe).
* Starten Sie steamvr. Das Tutorial "steamvr" sollte automatisch gestartet werden.
* Verbinden Sie Ihr Headset mit Ihrem PC, und schalten Sie die Motion-Controller ein.
* Nachdem die Windows Mixed Reality-Startseite geladen und ihre Controller sichtbar sind, öffnen Sie die app "Steam" auf Ihrem Desktop.
* Verwenden Sie die app "Steam", um ein steamvr-Spiel aus ihrer Dampf Bibliothek zu starten. Zum Starten von steamvr-spielen, ohne Ihr Headset zu beenden, können Sie diese unter Windows Mixed Reality **Start > alle apps** finden und starten. 

### <a name="i-get-a-message-that-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Ich erhalte eine Meldung mit dem Hinweis "für die Verwendung von steamvr mit Windows Mixed Reality müssen Sie die neueste Windows Update" oder "Windows-Entwicklermodus erforderlich" installieren.

1. Stellen Sie sicher, dass auf Ihrem PC die neueste Version von Windows 10 ausgeführt wird. Um dies zu überprüfen, wechseln Sie zu **Einstellungen > System >** Info. Stellen Sie unter "Windows-Spezifikationen" sicher, dass "OS Build" 16299,64 oder höher ist.
2. Stellen Sie sicher, dass keine Updates vorhanden sind, die auf den Download oder die Installation warten. Wechseln Sie zu **Einstellungen > aktualisieren Sie & Sicherheits > Windows Update** , und wählen Sie "nach Updates suchen". Sie müssen möglicherweise mehrmals nach Updates suchen, um die Suche nach Updates fortzusetzen, bis keine weiteren Updates verfügbar sind, und dann Ihren PC neu starten.

### <a name="steamvr-is-crashing-after-updating-windows"></a>Steamvr stürzt nach dem Aktualisieren von Windows ab.

Einige ältere Versionen von Windows Mixed Reality für steamvr sind nicht mehr mit Windows kompatibel. Sie haben möglicherweise eine alte Version von Windows Mixed Reality für steamvr. So stellen Sie sicher, dass Sie auf dem neuesten Stand sind:
1. Wechseln Sie in der Dampf Bibliothek zu **Software > Windows Mixed Reality for steamvr** .
2. Klicken Sie mit der rechten Maustaste, und wechseln Sie zu "Eigenschaften".
3. Wählen Sie die Registerkarte "Aktualisieren" aus, und wählen Sie "diese Anwendung immer auf dem neuesten standhalten" aus.
4. Erzwingen Sie die Aktualisierung, indem Sie auf die Registerkarte "lokale Dateien" klicken und "Integrität von Anwendungs Dateien überprüfen" auswählen.
5. Starten Sie Steam und steamvr neu.

Wenn steamvr nach dem Aktualisieren immer noch abgestürzt ist, haben Sie möglicherweise zwei Installationen von Windows Mixed Reality für steamvr auf Ihrem Computer. So überprüfen Sie, ob dies der Fall ist:
1. Suchen Sie nach%LocalAppData%\openvr\openvrpaths.vrpath, und öffnen Sie Sie im Editor.
2. Suchen Sie in den Abschnitten "externe Treiber" nach mehreren Einträgen für "mixedrealityvrdriver". 
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Wenn mehrere Einträge angezeigt werden, entfernen Sie den älteren der beiden Einträge. Beachten Sie Folgendes: Wenn Sie nur einen Eintrag haben, sollte am Ende der Zeile kein Komma mehr vorhanden sein, z. b.:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Speichern Sie die Datei, und schließen Sie sie.
5. Starten Sie Steam und steamvr neu.

### <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Meine Controller funktionieren in steamvr nicht erwartungsgemäß.

1. Schließen Sie steamvr.
2. Kehren Sie zurück zur Mixed Reality-Startseite, und vergewissern Sie sich, dass Ihre Controller erwartungsgemäß funktionieren.
3. Starten Sie die Verwendung von "steamvr" erneut, und ihre Controller sollten wieder normal sein.
4. Wenn weiterhin Probleme auftreten, senden Sie Feedback über den [Windows-Feedback-Hub](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) unter der Kategorie Gemischte Realität, und fügen Sie in der Zusammenfassung steamvr ein.

Beachten Sie, dass Sie Ihre Bewegungs Controller in verschiedenen Spielen unterschiedlich verwenden. Hier sind einige Grundlagen für den Einstieg:
* Um das Steam-Dashboard zu öffnen, klicken Sie auf den linken Finger Stick.
* Um ein steamvr-Spiel zu beenden und zum Windows Mixed Reality-Start zurückzukehren, drücken Sie die Windows-Taste. Wählen Sie dann die Schaltfläche Mixed Reality, die auf dem Bildschirm angezeigt wird.

### <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Meine linken und rechten Controller werden in "steamvr" umgekehrt.

Starten Sie das Spiel mit ihren Controllern, und schalten Sie dann die linke Seite ein, gefolgt von der rechten Seite.

### <a name="my-games-are-running-slowly"></a>Meine Spiele werden langsam ausgeführt.

1. Vergewissern Sie sich, dass Ihr PC die Spezifikationen für steamvr in Windows Mixed Reality erfüllt.
2. Vergewissern Sie sich, dass Ihr PC die Spezifikationen für das von Ihnen wiedergegebene steamvr-Spiel erfüllt.
2. Wählen Sie im Mixed Reality-Portal auf Ihrem Desktop "anhalten", um die Desktop Vorschau zu stoppen.
3. Befolgen Sie die obigen Anweisungen, um sicherzustellen, dass Sie Windows 10 Build 16299,64 oder höher ausführen.
4. Stellen Sie sicher, dass Ihr PC über die neuesten Grafiktreiber verfügt.
5. Überprüfen Sie im Task-Manager, welche anderen Prozesse möglicherweise auf Ihrem PC ausgeführt werden und Ressourcen verbrauchen.
6. Überprüfen Sie, ob der Stream ein Spiel im Hintergrund herunterlädt. Dies kann Ressourcen verbrauchen und das Ausführen von spielen erleichtern.
7. Es gibt ein bekanntes Leistungsproblem, das sich auf eine kleine Klasse von apps auswirkt, die nicht über ein sichtbares Fenster verfügen, z. b. "steamvr Home". Die meisten apps fallen nicht in diese Kategorie, und eine Korrektur wird in einem zukünftigen Update verfügbar sein.

Wenn noch unerwartete Leistungsprobleme auftreten, senden Sie uns Feedback über den Windows-Feedback-Hub. Befolgen Sie die Anweisungen, um eine Ablauf Verfolgung für die [steamvr-Leistung einzuschließen](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr). 

### <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>"Steamvr" zeigt einen compositorfehler an (z. b. "Fehler beim freigegebenen IPC Compositor Connect-Fehler (400)").

Es gibt ein bekanntes Problem, das auftreten kann, wenn sich Ihr Headset und der primäre Monitor auf zwei verschiedenen Video Adaptern befinden. Fügen Sie den Monitor an denselben Adapter wie Ihr Headset an, und konfigurieren Sie diesen Monitor so, dass er der primäre Monitor in den **Einstellungen app > System > angezeigt** wird.

### <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Der Inhalt von "steamvr" wird an der falschen Stelle angezeigt, z. b. unterhalb oder oberhalb des Kopfes.

Position zurücksetzen: 
1. Klicken Sie auf den Finger Stick des linken Controllers, um das "steamvr-Dashboard" zu aktivieren.
2. Wählen Sie die Schaltfläche "Einstellungen" aus.
3. Wählen Sie "Position an Position zurücksetzen".

### <a name="my-steam-app-closed-unexpectedly"></a>Meine Dampf-App wurde unerwartet geschlossen.

Die Steam-APP wird geschlossen, wenn Sie den PC-Bildschirm sperren, das Headset entfernen, Benutzer wechseln oder wenn Ihr PC in den Standbymodus wechselt.


## <a name="speech-and-audio-problems"></a>Sprach-und Audioprobleme

### <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Ich kann meinen Sound in meinem Headset nicht hören, oder der Sound wird nicht auf meinem Headset, sondern auf meinem Computer abgespielt.

* Wenn Ihr immersives Headset nicht über integrierte Kopfhörer verfügt, müssen Sie sich mit dem audiowagen auf dem Headset verbinden. Der Jack befindet sich häufig direkt hinter oder unter dem Headset-Hypervisor oder den-objektiven. Wenden Sie sich an Ihren Headset-Hersteller, wenn Sie ihn nicht finden können.
* Einige Audioheadsets verfügen über physische Schaltflächen, um das Volume zu steuern. Wenn das audiolaufwerk nicht funktioniert, überprüfen Sie, ob das Volume ausgeschaltet oder stumm geschaltet ist.
* Windows Mixed Reality ist für die Wiedergabe von Sound über Ihr immersives Headset konzipiert, wenn das gemischte Reality-Portal ausgeführt wird und Sie über Kopfhörer verfügen. Wenn Sie das Headset ausschalten oder den Hypervisor nach oben drehen, schließen Sie die Anwendung "Mixed Reality Portal", oder wenn diese APP nicht 15 Minuten lang verwendet wurde, wechselt das Audiogerät zu Ihrem standardmäßigen Windows-Wiedergabe Gerät. Sie können diese Einstellung in den **Einstellungen > gemischte Realität > Audiosprache und Sprache ändern.**
* Stellen Sie sicher, dass Ihr audioheadset vollständig an den AudioJack angeschlossen ist. Insbesondere das Acer-Headset erfordert möglicherweise mehr Sorgfalt, um sicherzustellen, dass das audioheadset vollständig angeschlossen ist.
* Überprüfen Sie, ob das audioheadset/Mikrofon an das Headset und nicht an den PC angeschlossen ist.
* In der Windows Sound-Systemsteuerung werden nur aktivierte audioendpunkte, nicht deaktivierte Endpunkte angezeigt. Das Headset-Audiogerät wird deaktiviert, wenn Sie das Headset nicht verwenden. Sie müssen also mit der rechten Maustaste in der Systemsteuerung klicken und "deaktivierte Geräte anzeigen" auswählen, um es anzuzeigen. der Gerätename ist "Realtek USB 2.0-Audiodatei". Nachdem Sie dies getan haben, können Sie den Namen auf der Seite "Properties" (Eigenschaften) so ändern, dass Sie leichter erkannt werden. Dies ist sowohl für die Wiedergabe-als auch für die Aufzeichnungs Registerkarte möglich.
* Wenn Ihre Audiodatei nicht in Mixed Reality-Apps (z. b. Netflix) funktioniert, wird dies möglicherweise durch ein bekanntes Problem verursacht, bei dem Windows Mixed Reality nicht automatisch entsprechend der Version des Betriebssystems aktualisiert wird. Um dieses Problem zu beheben und die beste gemischte Realität zu erhalten, wechseln Sie zu **Einstellungen > aktualisieren Sie & Sicherheit > Windows Update > suchen Sie nach Updates** .

**Hinweis:** Das räumliche Windows Mixed Reality-Audioformat funktioniert am besten mit den in Ihr immersiven Headset integrierten oder direkt mit ihnen verbundenen Kopfhörern. PCs oder Kopfhörer, die mit dem PC verbunden sind, funktionieren möglicherweise nicht gut für räumliche Audiodaten.

**Hinweis:** Windows Mixed Reality unterstützt keine Bluetooth-Audioheadsets.

### <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Ich sehe plötzliche volumeänderungen, verlorene Audiodaten oder das Roaming.

* Einige Anwendungen, einschließlich vieler Anwendungen, die über steamvr gestartet werden, können das Audiogerät verlieren, wenn sich das Audiogerät ändert, wenn Sie das Mixed Reality-Portal starten oder beenden. Starten Sie die APP neu, nachdem Sie die Mixed Reality-Portal-app geöffnet haben, um dies zu korrigieren.
* Wenn ein anderes Multimedia-USB-Gerät (z. b. eine Web-Cam) denselben internen oder externen USB-Hub mit dem Windows Mixed Reality-Headset gemeinsam nutzt, kann der AudioJack/-Kopfhörer des Headsets gelegentlich einen rauschenden Sound oder überhaupt keine Audiodaten enthalten. Binden Sie Ihr Headset an einen USB-Anschluss, der einen anderen Hub verwendet, oder trennen bzw. deaktivieren Sie Ihr anderes USB-Multimediagerät.
* Wenn Sie eine laute Rausch Blase von den mit dem Headset verbundenen PCs bemerken, ist es möglich, dass der USB-Hub des PCs nicht genügend Strom für das Windows Mixed Reality-Headset bereitstellen kann. Wenn dies der Fall ist, wird sofort ein [Feedback-Hub](https://docs.microsoft.com/hololens/hololens-feedback) -Fehler ausgegeben. Problem Umgehungen, die dazu beitragen können, die Verwendung eines dedizierten, externen USB-3,0-Hubs oder eines anderen USB-Ports auf dem PC zu unterstützen.

### <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Mein Bluetooth-audioheadset funktioniert nicht wie erwartet.

Microsoft empfiehlt nicht die Verwendung von Bluetooth-Audioheadsets mit Windows Mixed Reality. Bluetooth-audiodatenperipherale funktionieren nicht gut für Windows Mixed Reality-sprach-und räumliche Audiofunktionen, und Bluetooth-Audioheadsets können nicht gleichzeitig Mikrofon-und Stereo Ausgaben unterstützen, sodass Sie Stereo-oder spatialized Sound nicht hören, wenn Sie es für gamechat oder andere Spracheingaben verwenden. Bluetooth-Audioheadsets können sich auch negativ auf den Bewegungs Controller auswirken. 

### <a name="sound-isnt-coming-from-expected-directions"></a>Sound kommt nicht aus erwarteten Richtungen.

Die Windows Mixed Reality-Startseite bietet räumlichen Sound (Audio, der so aussieht, als ob es sich um die apps in Ihrer Startseite handelt). Wenn Sie sich ein-und auslagern, werden die audiorichtung und-Ebene so geändert, dass Sie den Sinn von Realismus erhöhen. Im folgenden finden Sie einige Gründe für unerwartete Sound Richtungen: 
* Wenn Sie Musik aus einer Hintergrund fähigen Musik-app (wie Groove Music) in ihrer eigenen Homepage öffnen und wiedergeben und dann eine immersive VR-Erfahrung (wie ein Spiel) öffnen, wird der Sound aus der Musik-app von räumlichem Sound zu Stereo übertragen. Es wird möglicherweise lauter als zuvor angezeigt, da zwischen Ihnen und dem Sound kein Abstand mehr besteht.
* Wenn Cortana auf Ihrem Host-PC aktiviert war, bevor Sie Ihr Windows Mixed Reality-Headset verwenden, verlieren Sie möglicherweise den räumlichen Sound, der auf die apps in Ihrer Windows Mixed Reality-Startseite angewendet wird. Um dieses Problem zu beheben, deaktivieren Sie "Cortana in den **Einstellungen > Cortana** auf Ihrem Desktop vor dem Starten von Windows Mixed Reality", oder aktivieren Sie "Windows Sonic for Kopfhörer" im Fenster "Desktop-App" in der Windows Mixed Reality-Homepage:
    1. Klicken Sie in der Desktop-Taskleiste mit der linken Maustaste auf das Redner Symbol, und wählen Sie es aus der Liste der Audiogeräte aus.
    2. Klicken Sie in der Desktop-Taskleiste mit der rechten Maustaste auf das Redner Symbol, und wählen Sie im Menü "sprechersetup" die Option "Windows-Sound für Kopfhörer"
    3. Wiederholen Sie diese Schritte für alle Ihre Audiogeräte (Endpunkte).

### <a name="speech-commands-are-not-working-as-expected"></a>Sprachbefehle funktionieren nicht erwartungsgemäß.

* Um Sprachbefehle verwenden zu können, müssen sprach-und Spracheinstellungen auf Ihrem PC auf eine Sprache festgelegt werden, die [in Windows Mixed Reality unterstützt](https://support.microsoft.com/en-us/help/4039262/windows-10-mixed-reality-setup-faq#Languages)wird. Um die Einstellungen für die Windows-Spracherkennung und-Sprache zu überprüfen, wählen Sie **Einstellungen > Zeit & Sprache > Region & Sprache** und **Einstellungen >** Sprache & Sprache >.
* Wenn Ihr Headset nicht über ein integriertes Mikrofon verfügt, müssen Sie dem Headset oder Ihrem PC Kopfhörer mit einem Mikrofon anfügen. Wenn Sie die Mikrofon Eingabe bei der Nutzung automatisch zu Ihrem Headset wechseln möchten, wechseln Sie zu **Einstellungen > gemischte Realität > Audiosprache und sprach** Eingabe, und aktivieren Sie die Option "Wenn ich mein Headset trage, zu" Headset mic "wechseln.
* Einige Audioheadsets verfügen über eine physische Schaltfläche, um das Mikrofon zu stumm schalten und zu entstumm schalten. Wenn Sprachbefehle nicht funktionieren, überprüfen Sie, ob Ihr Mikrofon stumm geschaltet ist.
* Audioheadsets mit einem Mikrofon, das sich aus dem Earbud-Kabel unterscheidet, sind für Sprachbefehle in Umgebungen mit Umgebungsgeräuschen nicht gut geeignet.
* Cortana kann langsam sein, wenn Sie zum ersten Mal in einer gemischten Reality-Portal Sitzung aufgerufen wird. Wechseln Sie zu **Einstellungen > Cortana > sprechen Sie mit Cortana,** und stellen Sie sicher, dass "Cortana auf Hey Cortana Antworten" aktiviert ist.
* Auf einigen PCs ist der Standardwert für die sprach Erfassung für Ihr mit dem Headset verbundenes Mikrofon möglicherweise zu niedrig festgelegt. Wenn Sie unzuverlässige Sprachbefehle oder Diktat Verhalten haben, können Sie versuchen, die Problembehandlung für die Mikrofon Einrichtung auszuführen. Sie können diese Problembehandlung über die **Einstellungen > Zeit & Sprache > Sprache** erreichen. Wählen Sie dann im Abschnitt "Mikrofon" den Abschnitt "Get Started" (starten) aus. Verwenden Sie hierzu die Desktop-app in der Windows Mixed Reality-Startseite, und verwenden Sie das Headset, um das Mikrofon zu beeinflussen, das Sie für Windows Mixed Reality verwenden. Wählen Sie den entsprechenden Endpunkt im Problembehandlungs-Assistenten aus.

### <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Ich habe nur ein audioheadset und möchte es für Desktop und mein Headset verwenden.

Wenn Sie nur über ein audioheadset verfügen und über kein Headset mit integrierter Kopfzeile verfügen, verbinden Sie das audioheadset mit dem Host-PC anstatt mit dem Headset. Deaktivieren Sie dann in den MRP-Einstellungen die Option "zu Headset-audiowechsel wechseln".

### <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Ich möchte zu Dolby Atmos für Kopfhörer wechseln.

Windows Mixed Reality-Umgebungen und ihre Anwendungen verwenden Windows Sonic für die räumliche Audiotechnologie für Kopfhörer, die für gemischte Realität angepasst ist. Andere räumliche Audiotechnologien wie Dolby Atmos für Kopfhörer können auf Vollbildanwendungen wie steamvr-Spiele angewendet werden, aber nicht auf die Windows Mixed Reality Shell-Umgebungen und-Anwendungen (z. b. das Platzieren eines Webbrowsers an der Wand des Klippe-oder des Sky-Loft), die mithilfe von Windows-Sonic für den räumlichen Sound und die Akustik von Kopfhörern entwickelt wurden.


## <a name="questions-about-desktop-in-mixed-reality"></a>Fragen zum Desktop in gemischter Realität

### <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Gewusst wie in gemischter Realität auf My PC Desktop zugreifen?
Mithilfe der Desktop-App können Sie in gemischter Realität auf Ihren PC-Desktop zugreifen. Starten Sie ihn in der Schaltfläche "Headset von **Windows" > alle apps > Desktop** . 

### <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Wie können mehrere Monitore in gemischter Realität angezeigt werden?
Standardmäßig schaltet die Desktop-App automatisch ein, um den Monitor mit dem Fokus anzuzeigen. Wenn Sie alle Monitore in gemischter Realität anzeigen möchten: 
* Klicken Sie in der oberen linken Ecke der APP auf das Symbol "Monitor".
* Deaktivieren Sie "Monitor automatisch wechseln".
* Wählen Sie den Monitor aus, den Sie anzeigen möchten.
* Starten Sie eine andere Instanz der Desktop-App.
* Wählen Sie den Monitor aus, der für diese Instanz angezeigt werden soll. 
* Wiederholen Sie den Vorgang für alle physischen Monitore. Beachten Sie, dass Sie den Monitor bei jedem Neustart von Mixed Reality erneut für jede Desktop-App auswählen müssen. 

### <a name="my-desktop-app-only-shows-a-black-screen"></a>Meine Desktop-App zeigt nur einen schwarzen Bildschirm an.
Wenn Ihr PC über eine NVIDIA Hybrid GPU verfügt, kann das Problem dadurch verursacht werden, dass NVIDIA-Gerät die runtimebroker.exe auf der diskreten GPU anstelle der integrierten GPU ausführen kann. Um dieses Problem zu beheben, befolgen Sie die Anweisungen unter "[Gewusst wie Erstellen von Optimus-Einstellungen für ein neues Programm](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)". zum Hinzufügen von C:\windows\system32\runtimebroker.exe und erzwingen der Durchführung auf dem Prozessor "integrierte Grafiken". 


## <a name="other-questions"></a>Weitere Fragen

### <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-getting-stuck"></a>Mein Samsung Odyssee-oder Odyssee + Headset-Firmwareupdate bleibt hängen.

Samsung besitzt und veröffentlicht mit den Geräte begleitenden Apps "Samsung HMD Odyssee Setup" und "Samsung HMD Odyssee + Setup" die durch die Geräte bereitgestellten Headset-Firmware-Updates. Weitere Informationen und Hilfe bei Problemen mit der Aktualisierung von Samsung-Firmware finden Sie unter Samsung-Kundendienst.

Wenn der Firmwareupdate nicht mehr als fünf Minuten ausgeführt wird, wird der Vorgang nicht fortgesetzt:
* Entfernen Sie alle anderen USB-Geräte vorübergehend, und wiederholen Sie das Firmwareupdate.
* Verbinden Sie Ihr Samsung-Headset mit einem anderen USB 3,0-Port auf Ihrem PC.
* Deaktivieren und/oder deinstallieren installierter Software, die Firmwareupdates beeinträchtigen kann, wie z. b. die aorus-App Center von Gigabyte.
* Verwenden Sie einen anderen PC, um das Update für die Samsung-Headset-Firmware auszuführen.

### <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Mein Wi-Fi verlangsamt sich, wenn ich Windows Mixed Reality verwende.

Wenn Sie eine WLAN-Verbindung mit 2,4 GHz verwenden, verlangsamen Ihre Bewegungs Controller möglicherweise das WLAN. Probieren Sie einen der folgenden Lösungsschritte aus:
* Wechseln Sie zu einer WLAN-Verbindung mit 5 GHz, sofern verfügbar. [Weitere Informationen](https://support.microsoft.com/en-us/help/4000461)
* Verwenden Sie einen separaten Bluetooth-Adapter, um Ihre Motion-Controller mit Ihrem PC zu verbinden. Siehe [Empfohlene Adapter](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

### <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Ich habe eine Meldung mit dem anbinden und Berechnen des PCs. Warum?

Wenn Sie einen Laptop verwenden, funktioniert Windows Mixed Reality am besten, wenn der PC vollständig abgerechnet und angeschlossen ist. 

### <a name="what-is-the-experience-options-setting"></a>Was ist die Einstellung der Erfahrungs Optionen?

Mithilfe der Einstellung für die Optionen für die **Anzeige (Einstellungen > gemischte Realität > Headset-Anzeige > Optionen** ) können Sie die Windows Mixed Reality-Leistungseinstellungen ändern. Dies ermöglicht es Ihnen, die bestmögliche Leistung für die Hardwarekonfiguration für eine Reihe von Inhalten auszuwählen. Die 90Hz-Umgebung ist für alle Systeme verfügbar, aber Sie können versuchen, automatisch zu versuchen, die gewünschte Einstellung anzuzeigen. Im folgenden finden Sie die folgenden Optionen:
* Automatisch: in Windows Mixed Reality wird die beste Leistung für Ihre Hardwarekonfiguration festgestellt. Für die meisten Benutzer ist dies die beste Wahl, mit der Sie beginnen können.
* 60Hz: legt die Aktualisierungsrate auf 60Hz fest und deaktiviert bestimmte Features, wie z. b. Video Erfassung und Vorschau im Mixed Reality-Portal.
* 90Hz: legt die Aktualisierungsrate auf 90Hz fest.

### <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Welche Sprachen werden in Windows Mixed Reality unterstützt?

Windows Mixed Reality ist in den folgenden Sprachen verfügbar. Wenn Ihr PC auf eine andere Sprache festgelegt ist, können Sie Windows Mixed Reality weiterhin verwenden, aber die Schnittstelle wird in englischer Sprache (USA) angezeigt, und Sprachbefehle und Diktat sind nicht verfügbar.

* Chinesisch (Vereinfacht, China)
* Englisch (Australien)
* Englisch (Kanada)
* Englisch (Großbritannien)
* Englisch (USA)
* Französisch (Kanada)
* Französisch (Frankreich)
* Deutsch (Deutschland)
* Italienisch (Italien)
* Japanisch (Japan)
* Spanisch (Mexiko)
* Spanisch (Spanien)

Die Windows Mixed Reality-Bildschirmtastatur ist nur in englischer Sprache (USA). Um Text in einer anderen Sprache einzugeben, verwenden Sie eine physische Tastatur, die mit Ihrem PC verbunden ist. Sie können auch in einer der oben aufgeführten unterstützten Windows Mixed Reality-Sprachen Diktat verwenden – Wählen Sie einfach Mikrofon auf der Bildschirmtastatur aus.

Windows Mixed Reality ist auch in den folgenden Sprachen ohne Sprachbefehle oder Diktat Features verfügbar:

* Chinesisch (traditionell) (Taiwan und Hongkong)
* Niederländisch (Niederlande)
* Koreanisch (Korea)
* Russisch (Russische Föderation)

### <a name="i-have-questions-about-my-headset-hardware"></a>Ich habe Fragen zu meiner Headset-Hardware.

Weitere Informationen zu Ihrem Headset finden Sie unter dem Hersteller. Möglicherweise gibt es ein Produkthandbuch, oder Sie können die Website des Herstellers ausprobieren.


## <a name="how-to-uninstall-windows-mixed-reality"></a>Deinstallieren von Windows Mixed Reality

### <a name="how-do-i-uninstall-windows-mixed-reality"></a>Gewusst wie deinstallieren Sie Windows Mixed Reality?

1. Trennen Sie das Headset von Ihrem PC.
2. Schließen Sie das gemischte Reality-Portal.
2. Wechseln Sie zu  **Start > Einstellungen > gemischte Realität** , und wählen Sie "deinstallieren" aus.

Wenn Sie bereit sind, Ihr Headset erneut zu verwenden, binden Sie es ein, und das Mixed Reality-Portal führt Sie durch das Setup.

### <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>Ich erhalte die Meldung "Wir konnten die Windows Mixed Reality nicht deinstallieren".

Dies bedeutet, dass einige Dateien, einschließlich Informationen über Ihre Umgebung, möglicherweise weiterhin auf dem Computer angezeigt werden. Dies kann zu Problemen führen, wenn Sie Windows Mixed Reality später neu installieren. Sie können alle verbleibenden Windows Mixed Reality-Informationen manuell von Ihrem PC entfernen, indem Sie die Registrierung ändern und Windows PowerShell verwenden, um Befehle auszuführen. _Wenn Sie die Registrierung falsch ändern, können schwerwiegende Probleme auftreten. Stellen Sie sicher, dass Sie diese Schritte sorgfältig ausführen. Um zusätzlichen Schutz zu erhalten, sichern Sie Ihre Registrierung, bevor Sie Sie ändern, damit Sie Sie wiederherstellen können, wenn ein Problem vorliegt occurrs._ Weitere Informationen finden Sie unter [Sichern und Umordnen der Registrierung in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

So deinstallieren Sie Windows Mixed Reality mithilfe der folgenden Befehle:
1. Starten Sie Ihren PC neu.
2. Geben Sie im **Suchfeld den Suchbegriff** "regedit" ein, und klicken Sie dann auf **Ja** .
3. Entfernen Sie die folgenden Registrierungs Werte:
   <ul>
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>, und löschen Sie dann <b>firstranunwar</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic\sprachlos andaudio,</b>und löschen Sie dann <b>preferdesktopspeaker</b> und <b>preferdesktopmic</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore &gt; Settings\holographic</b>und DELETE <b>disablespeechinput</b>. Hinweis: die Registrierungs Elemente in HHKEY_CURRENT_USER müssen für jedes Benutzerkonto auf dem PC gelöscht werden, auf dem Windows Mixed Reality verwendet wurde.</li> 
    <li><b>HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\perceptionsimulationextensions</b>, und löschen Sie dann <b>DeviceID</b> und den <b>Modus</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>, und löschen Sie dann <b>ondevicelearningabgeschlossene</b>.</li> 
   </ul>
4. Entfernen Sie die folgenden Registrierungsschlüssel: <ul>
   <li> <b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holosi</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\holosi</b></li> 
   <li> <b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore \settings\holographicpreferences</b></li><br/></ul>
5. Schließen Sie den Registrierungs-Editor.
6. Navigieren Sie zu **c:\users\benutzername\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** , und löschen Sie dann **RoomBounds.json** . Wiederholen Sie diesen Schritt für jeden Benutzer, der Windows Mixed Reality verwendet hat.
7. Öffnen Sie admin cmd prompt, und navigieren Sie zu **c:\programdata\windowsholographicdevices\spatialstore\hololenssensoren** . Löschen Sie dann den Inhalt des Ordners für die **headtracking-Daten** (aber nicht den Ordner selbst).
8. Geben Sie "PowerShell" in das **Suchfeld** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell** , und wählen Sie dann **als Administrator ausführen** aus.
9. Führen Sie in Windows PowerShell die folgenden Schritte aus: <ul>
   <li>Kopieren und fügen Sie Folgendes an der Eingabeaufforderung ein, und drücken Sie dann die EINGABETASTE: <b>dismus/Online/Get-Capabilities</b></li> 
   <li>Kopieren Sie die Funktions Identität, die mit "analog. Holographic. Desktop" beginnt (wenn Sie&#39;t ist, bedeutet dies, dass dieses Element&#39;t installiert ist. Fahren Sie in diesem Fall mit Schritt 10 fort.)</li> 
   <li>Kopieren und fügen Sie die folgende Eingabeaufforderung ein, und drücken Sie dann die EINGABETASTE: <b>/Online/Remove-Capability/CapabilityName: die Funktions Identität, die Sie im letzten Schritt kopiert</b> haben.</li>
   </ul>
10. Starten Sie den PC neu.




