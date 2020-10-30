---
title: Häufig gestellte Fragen (FAQ) zum Verwenden von Windows Mixed Reality
description: Hier erhalten Sie Antworten auf häufig gestellte Fragen bei der Arbeit mit Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: cf02ccfc92d80ee1d1a8f6ca3d4ab55650f4a62c
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044439"
---
# <a name="using-windows-mixed-reality-faq"></a>Häufig gestellte Fragen (FAQ) zum Verwenden von Windows Mixed Reality

Wenn Sie Hilfe bei der Verwendung des Windows Mixed Reality-immersiven Headsets benötigen, lesen Sie diese Themen, um allgemeine Informationen und Problembehandlung zu erhalten.

Benötigen Sie weitere Unterstützung? Informationen zur erweiterten Problembehandlung finden Sie in diesem Artikel.

## <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Ich sehe eine Meldung, die besagt, dass "verlorene Nachverfolgung" oder "Wir haben keine Grenze für diesen Raum".

Wählen Sie **> Mixed Reality-Portal** auf Ihrem Desktop starten aus. Wählen Sie **Menü** aus, und wählen Sie dann **Setup ausführen** , um eine neue Grenze zu erstellen. Windows Mixed Reality unterstützt mehrere Standorte und identifiziert den Platz, in dem Sie sich beim Start befinden, solange sich der Raum nicht signifikant geändert hat.  


## <a name="i-cant-hear-any-sound-or-the-sound-is-coming-from-my-computer-instead-of-my-headset"></a>Ich kann keinen Sound hören, oder der Sound stammt von meinem Computer anstatt von meinem Headset.

Wenn Ihr immersives Headset nicht über integrierte Kopfhörer verfügt, müssen Sie sich mit dem audiowagen auf dem Headset verbinden. (Der Jack befindet sich häufig direkt hinter dem Headset-Hypervisor oder den-linken. wenden Sie sich an Ihren Headset-Hersteller, wenn Sie Probleme beim Auffinden haben.) 

Einige Audioheadsets verfügen über physische Schaltflächen, um das Volume zu steuern. Wenn der audiovorgang nicht funktioniert, überprüfen Sie, ob das Volume ausgeschaltet oder stumm geschaltet ist.

Windows Mixed Reality ist für die Wiedergabe von Sound über Ihr immersives Headset konzipiert, wenn Sie es verwenden und über Kopfhörer verfügen. Wenn Sie das Headset ausschalten oder den Hypervisor kippen, wechselt das Audiogerät zu Ihrem standardmäßigen Windows-Wiedergabe Gerät. Sie können diese Einstellung in den **Einstellungen > gemischte Realität > Audiosprache und Sprache** ändern.

> [!NOTE]
> * Das räumliche Windows Mixed Reality-Audioformat funktioniert am besten mit den in Ihr immersiven Headset integrierten oder direkt mit ihnen verbundenen Kopfhörern. PCs oder Kopfhörer, die mit dem PC verbunden sind, funktionieren möglicherweise nicht gut für räumliche Audiodaten.
> * Windows Mixed Reality unterstützt keine Bluetooth-Audioheadsets.

## <a name="speech-commands-arent-working"></a>Sprachbefehle funktionieren nicht

Um Sprachbefehle verwenden zu können, müssen die Sprach-und Spracheinstellungen Ihres PCs auf eine [unterstützte Windows Mixed Reality-Region und-Sprache](wmr-setup-faq.md#what-languages-are-supported-in-windows-mixed-reality)festgelegt werden. Wählen Sie zum Überprüfen Ihrer Windows-Region und-Sprache **Einstellungen > Uhrzeit & Sprache > Region & Sprache** aus. Wählen Sie zum Überprüfen der sprachsprache **Einstellungen > Zeit & Sprache > Sprache** aus.

Wenn Ihr Headset nicht über eine integrierte MIC verfügt, fügen Sie Kopfhörer mit einem MIC an das Headset oder Ihren PC an. Wenn der MIC-Eingabe automatisch auf Ihr Headset umgestellt werden soll, wenn Ihre Kopfhörer direkt damit verbunden sind, wählen Sie **Einstellungen > gemischte Realität > Audiosprache und sprach** Eingabe aus, und stellen Sie sicher, dass beim Übertragen des Headsets die Option " **Headset mic** " aktiviert ist.

Einige Audioheadsets verfügen über eine physische Schaltfläche, um das Mikrofon zu stumm schalten und zu entstumm schalten. Wenn Sprachbefehle nicht funktionieren, überprüfen Sie, ob Ihre MIC stumm ist.

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>Die Grenze ist immer sichtbar. Wie kann ich es tun?

Wenn Sie sich in der Nähe der Grenze befinden, wird Sie angezeigt. Wenn Ihre Grenze Abschnitte enthält, die eine schmale oder unregelmäßige Form aufweisen, kann es passieren, dass Sie sich in der Nähe der – befinden und damit – häufiger als gewünscht erscheinen. Um dieses Problem zu beheben, versuchen Sie erneut, die Grenze zu erstellen, indem Sie eine größere und eine reguläre Form verwenden. Wählen Sie **> Mixed Reality-Portal** auf Ihrem Desktop starten aus, und wählen Sie dann **Setup ausführen** aus. 

Sie können die Grenze auch temporär aus dem Mixed Reality-Portal deaktivieren: Wählen Sie **Menü** aus, und schalten Sie dann die Begrenzung mit der UMSCHALT Fläche aus. Wenn die Grenze ausgeschaltet ist, müssen Sie an einer Stelle bleiben, um Hindernisse zu vermeiden.

## <a name="im-having-trouble-with-my-motion-controllers"></a>Ich habe Probleme mit den Motion-Controllern

Wenn Ihre Motion-Controller nicht ordnungsgemäß funktionieren, keine Verbindung herstellen oder wenn Sie kein Image der Controller sehen, wenn Sie Ihr Headset verwenden, versuchen Sie Folgendes:

* Stellen Sie sicher, dass Ihre Controller eingeschaltet sind. Um diese zu aktivieren, drücken Sie die **Windows** -Taste für 2 Sekunden.
* Wählen Sie **> Mixed Reality-Portal** auf Ihrem PC starten aus, und wählen Sie dann das **Menü** aus, in dem die Motion-Controller aufgeführt sind, sowie eine Statusmeldung:
    * Bereit – die Controller sind alle festgelegt.
    * Verlorene Nachverfolgung – das gemischte Reality-Portal kann Ihre Controller nicht finden. Halten Sie diese vor dem Headset, und starten Sie Sie neu, indem Sie die **Windows** -Taste vier Sekunden lang drücken, und dann erneut 2 Sekunden.
    * Niedrige Akkukapazität – ersetzen Sie die Controller-Akkus.
* Wenn Sie Wi-Fi verwenden, versuchen Sie, Ihren PC mit einem 5-GHz-Wi-Fi Netzwerk zu verbinden, um drahtlose Störungen zu verringern. 
* Wählen Sie für neuere Paare, die direkt mit den Controllern gekoppelt sind, die Option **"..."** aus. im **Mixed Reality-Portal** , und wählen Sie **Controller einrichten** aus. Dadurch gelangen Sie zur Headset-APP, um die Controller mit dem Headset zu koppeln.  
* Für ältere Headsets, die nicht über integrierte Bluetooth verfügen, damit die Controller direkt paarweise gekoppelt werden:  
    * Wählen Sie Einstellungen > Geräte > Bluetooth & andere Geräte auf Ihrem PC aus, und stellen Sie sicher, dass die Controller als paarweise aufgeführt sind.Wenn dies nicht der Fall ist, müssen Sie Sie koppeln. 
    * Wenn Sie über andere Bluetooth-Geräte verfügen, die mit Ihrem PC gekoppelt sind (z. b. Kopfhörer oder Gamepads), entfernen Sie einige. Wählen Sie **Einstellungen > Geräte > Bluetooth & andere Geräte** auf Ihrem PC aus, wählen Sie die Geräte aus, und wählen Sie dann **Gerät entfernen** aus.
    * Entfernen Sie Bluetooth-Kopfhörer und-Sprecher in den **Einstellungen > Geräte > Bluetooth & anderen Geräten** , und schalten Sie die Geräte aus. 
    * Wenn Sie einen USB-Bluetooth-Adapter verwenden, stellen Sie sicher, dass er an einen schwarzen USB 2,0-Port angeschlossen ist und so weit wie möglich von allen anderen drahtlos-und USB-Speich erwerken angeschlossen ist, einschließlich des USB-Anschlusses für Ihr Headset. 
    * Wenn Ihr PC über eine integrierte Bluetooth-Verbindung verfügt und Verbindungsprobleme auftreten, versuchen Sie stattdessen, einen USB-Bluetooth-Adapter zu verwenden. (Zu diesem Zweck müssen Sie auch Ihr integriertes Bluetooth-Radio in [Geräte-Manager](https://support.microsoft.com/help/4026149)deaktivieren und dann Ihre anderen Bluetooth-Geräte mit dem neuen Adapter koppeln.)
* Wenn die Einstellungs-APP auf der Seite Bluetooth & andere Geräte geöffnet ist, schließen Sie Sie.

## <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>Wenn ich mein Headset verwende, treten Probleme auf.

Allgemeine Informationen über den Komfort in Windows Mixed Reality finden Sie unter [Windows Mixed Reality-immersives Headset-Integrität,-Sicherheit und-Komfort](wmr-health-safety-comfort.md). Weitere Informationen zu Ihrem speziellen Headset finden Sie unter dem Headset-Hersteller.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Meine visuellen Elemente sind choppy, werden langsam geladen oder sind nicht gut geeignet.

Wenn Ihre visuellen Elemente mit gemischter Realität nicht optimal aussehen, versuchen Sie Folgendes:

* Stellen Sie sicher, dass Ihr Headset an der richtigen Grafikkarte auf Ihrem PC angeschlossen ist. Einige PCs verfügen sowohl über integrierte als auch diskrete Grafikkarten. Die diskrete Karte bietet im Allgemeinen die beste Leistung. [Erfahren Sie mehr über PC-Hardware](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Schließen Sie nicht verwendete apps auf Ihrem Desktop.
* Passen Sie die Anpassung Ihres Headsets an: Verschieben Sie Sie nach unten und nach links und nach rechts, und stellen Sie sicher, dass Sie passend ist.
* Passen Sie die visuellen Einstellungen Ihres Headsets an ( **Einstellungen > gemischte Realität > Headset-Anzeige** ). Wenn die **visuelle Qualität** auf **automatisch** festgelegt ist, wählen wir die beste gemischte Realität für Ihren PC aus. Legen Sie die **visuelle Qualität** auf " **hoch** " fest, um die Visualisierung ausführlicher zu gestalten. Wenn Ihre visuellen Elemente in einem choppy-Wert vorliegen, können Sie eine niedrigere Einstellung auswählen.
* Versuchen Sie, die Kalibrierung Ihres Headsets anzupassen. Die Linsen sollten angepasst werden, damit Sie mit dem interpupillary Distance (IPD), dem Abstand zwischen ihren Schülern, identisch sind. Wenn Sie Ihre IPD nicht kennen, sollte optomezyst in der Lage sein, Sie für Sie zu messen. Es gibt auch Websites, mit denen IPD gemessen werden soll. Wenn Sie Ihre IPD kennen, verwenden Sie den Kalibrierungs Knopf Ihres Headsets, um Anpassungen vorzunehmen. Wenn das Headset keinen Kalibrierungs Knopf hat, wählen Sie **Einstellungen > gemischte Realität > der Headset-Anzeige** aus, und passen Sie das Kalibrierungs Steuerelement an.

## <a name="i-have-questions-about-my-headset-hardware"></a>Ich habe Fragen zu meiner Headset-Hardware

Weitere Informationen zu Ihrem Headset finden Sie unter dem Hersteller. Möglicherweise gibt es ein Produkthandbuch, oder Sie können die Website des Herstellers ausprobieren.

## <a name="the-floor-in-mixed-reality-seems-to-be-in-the-wrong-spot"></a>Der Boden in gemischter Realität scheint sich an der falschen Stelle zu befinden.

Wenn die Etage ausgeschaltet ist (z. b. Wenn Sie unverankert sind), wählen Sie **> Raum Anpassung starten** aus, während Sie das Headset zum vornehmen von Änderungen verwenden.

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Ich habe eine Meldung mit dem anbinden und Berechnen des PCs. Warum?

Wenn Sie einen Laptop verwenden, funktioniert Windows Mixed Reality am besten, wenn der PC vollständig abgerechnet und angeschlossen ist.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Gewusst wie deinstallieren Sie Windows Mixed Reality?

Wählen Sie **> Einstellungen starten > gemischte Realität** aus, und wählen Sie dann **deinstallieren** aus. Stellen Sie sicher, dass Sie Ihr Headset von Ihrem PC trennen und das Mixed Reality-Portal schließen, bevor Sie deinstallieren.

Wenn Sie bereit sind, Ihr Headset erneut zu verwenden, binden Sie es ein, und das Mixed Reality-Portal führt Sie durch das Setup.

> [!NOTE]
> Wenn eine Meldung mit dem Hinweis "das Entfernen von Windows Mixed Reality konnte nicht beendet werden" angezeigt wird, sind einige Dateien, einschließlich Informationen über Ihre Umgebung, möglicherweise weiterhin auf dem Computer. Dies kann zu Problemen führen, wenn Sie Windows Mixed Reality später erneut installieren.
> 
> Informationen dazu, wie Sie alle verbleibenden Windows Mixed Reality-Informationen manuell von Ihrem PC entfernen, finden Sie in **[diesem Artikel](installation_errors.md)** .

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Meine Wi-Fi verlangsamt sich, wenn ich Windows Mixed Reality verwende

Wenn Sie eine Wi-Fi Verbindung mit 2,4 GHz verwenden, verlangsamen Ihre Bewegungs Controller möglicherweise das WLAN. Probieren Sie einen der folgenden Lösungsschritte aus:

<!-- TODO: Use Windows Mixed Reality PC hardware guidelines interlink -->
* Wechseln Sie zu einer Wi-Fi Verbindung mit 5 GHz, sofern verfügbar. [Weitere Informationen](https://support.microsoft.com/help/4000461)
* Verwenden Sie einen separaten Bluetooth-Adapter, um Ihre Motion-Controller mit Ihrem PC zu verbinden. [Empfohlene Adapter anzeigen](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

## <a name="what-is-the-experience-options-setting"></a>Was ist die Einstellung der Erfahrungs Optionen?

Mit der Einstellung für die Options Optionen ( **Einstellungen > gemischte Realität > > Optionen für die Anzeige Optionen** ) haben Sie die Möglichkeit, die Windows Mixed Reality-Leistungseinstellungen zu ändern. Dies ermöglicht es Ihnen, die bestmögliche Leistung für die Hardwarekonfiguration für eine Reihe von Inhalten auszuwählen. Die 90Hz-Umgebung ist für alle Systeme verfügbar, Sie sollten jedoch zunächst automatisch testen, um festzustellen, welche Einstellung Sie bevorzugen.

Im folgenden finden Sie die folgenden Optionen:

* Automatische oder Windows-Entscheidung: Windows Mixed Reality bestimmt die beste Leistung für Ihre Hardwarekonfiguration. Für die meisten Benutzer ist dies die beste Wahl, mit der Sie beginnen können.
* 60Hz: legt die Aktualisierungsrate auf 60Hz fest und deaktiviert bestimmte Features, wie z. b. Video Erfassung und Vorschau im Mixed Reality-Portal.
* 90Hz: legt die Aktualisierungsrate auf 90Hz fest, wenn Ihr Headset mit dieser Geschwindigkeit ausgeführt werden kann. Wenn bei den Kabel Problemen die Ausführung des Headsets bei 90Hz verhindert wird, wird möglicherweise ein Fehler beim Start angezeigt, wenn dieser Modus ausgewählt ist. 

## <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>Ich sehe eine Meldung mit dem Hinweis "Put on your Headset", auch wenn mein Headset vorhanden ist.

Wenn Sie Ihr Headset einfügen, benötigt Windows Mixed Reality ein wenig Zeit, um Ihren Speicherplatz neu zu laden. Dies kann einige Zeit dauern. Wenn diese Nachricht nicht entfernt wird, stellen Sie sicher, dass der Schutz Aufkleber aus dem near-Sensor, der sich im Inneren des Headsets befindet, zwischen den objektiven entfernt wurde. Wenn der Aufkleber entfernt wurde und weiterhin Probleme auftreten, wenden Sie sich an Ihren Headset-Hersteller. Wenn Sie auf der Tastatur auf " **Win + Y** " drücken, wird das Headset manuell ausgelöst, wenn der Near-Sensor nicht automatisch ausgelöst wird. 

Benötigen Sie weitere Unterstützung? Informationen zur erweiterten Problembehandlung finden Sie in [diesem Artikel](troubleshooting-windows-mixed-reality.md).

## <a name="see-also"></a>Weitere Informationen
* [Die Community fragen](https://answers.microsoft.com)
* [Kontaktieren Sie uns zur Unterstützung](https://support.microsoft.com/contactus/)