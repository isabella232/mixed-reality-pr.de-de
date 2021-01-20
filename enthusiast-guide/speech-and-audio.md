---
title: FAQ zu Sprache und audiofragen
description: Sprach-und Audioinformationen zu Windows Mixed Reality Problembehandlung, die über die standardmäßige Kundensupport Dokumentation hinausgeht.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, Audioprobleme, Sprachprobleme
ms.openlocfilehash: fff5d661dbe61d4c9364c83e3bd0c6ddb8ab5cc6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581409"
---
# <a name="speech-and-audio-faqs"></a>FAQ zu Sprache und audiofragen

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Ich kann meinen Sound in meinem Headset nicht hören, oder der Sound wird nicht auf meinem Headset, sondern auf meinem Computer abgespielt.

* Wenn Ihr immersives Headset keine integrierten Kopfhörer enthält, verbinden Sie Kopfhörer mit dem Audiojack auf dem Headset. Der Jack befindet sich häufig direkt hinter oder unter dem Headset-Hypervisor oder den-objektiven. Wenden Sie sich an Ihren Headset-Hersteller, wenn Sie ihn nicht finden können.
* Einige Audioheadsets verfügen über physische Schaltflächen, um das Volume zu steuern. Wenn das audiolaufwerk nicht funktioniert, überprüfen Sie, ob das Volume ausgeschaltet oder stumm geschaltet ist.
* Das Audiogerät wechselt zum Windows-Standard Wiedergabe Gerät: 
    * Wenn Sie das Headset ausschalten
    * Den Hypervisor nach oben kippen
    * Schließen Sie die Mixed Reality-Portal-app.
    * Wenn eine APP 15 Minuten lang nicht verwendet wurde. 
    * Sie können diese Einstellung in den **Einstellungen > gemischte Realität > Audiosprache und Sprache ändern.**
* Stellen Sie sicher, dass Ihr audioheadset an den AudioJack angeschlossen ist. Insbesondere das Acer-Headset erfordert möglicherweise mehr Sorgfalt, um sicherzustellen, dass das audioheadset angeschlossen ist.
* Überprüfen Sie, ob das audioheadset/Mikrofon an das Headset und nicht an den PC angeschlossen ist.
* Die Sound-Systemsteuerung in den **Einstellungen > System > Sound** zeigt nur aktivierte audioendpunkte, nicht deaktivierte Endpunkte. Das Headset-Audiogerät wird deaktiviert, wenn Sie das Headset nicht verwenden. Klicken Sie mit der rechten Maustaste in der Systemsteuerung, und wählen Sie "deaktivierte Geräte anzeigen" aus, um es anzuzeigen. Der Gerätename ist "Realtek USB 2.0-Audiodatei", die auf der Seite "Eigenschaften" umbenannt werden kann. Dies ist sowohl für die Wiedergabe-als auch für die Aufzeichnungs Registerkarte möglich.
* Wenn Ihre Audiodatei nicht in Mixed Reality-apps funktioniert, z. b. mit der Netflix-app. Dies kann durch ein bekanntes Problem verursacht werden, bei dem Windows Mixed Reality nicht automatisch entsprechend der Version des Betriebssystems aktualisiert wird. Um dieses Problem zu beheben und die beste gemischte Realität zu erhalten, wechseln Sie zu **Einstellungen > aktualisieren Sie & Sicherheit > Windows Update > suchen Sie nach Updates**.

> [!NOTE]
> * Das räumliche Windows Mixed Reality-Audioformat funktioniert am besten mit den in Ihr immersiven Headset integrierten oder direkt mit ihnen verbundenen Kopfhörern. PCs oder Kopfhörer, die mit dem PC verbunden sind, funktionieren möglicherweise nicht gut für räumliche Audiodaten.
> * Windows Mixed Reality unterstützt keine Bluetooth-Audioheadsets.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Ich sehe plötzliche volumeänderungen, verlorene Audiodaten oder das Roaming

* Einige apps, wie solche, die über steamvr gestartet werden, können Audiodaten verlieren, wenn sich das Audiogerät ändert, wenn Sie das Mixed Reality-Portal starten oder beenden. Um dies zu beheben, öffnen Sie das Mixed Reality-Portal, und starten Sie die APP neu.
* Wenn ein anderes Multimedia-USB-Gerät (z. b. eine Web-Cam) denselben internen oder externen USB-Hub mit dem Windows Mixed Reality-Headset nutzt, kann der Headset-AudioJack oder die Kopfhörer gelegentlich einen rauschenden Sound oder überhaupt keine Audiodaten aufweisen. Binden Sie Ihr Headset an einen USB-Anschluss, der einen anderen Hub verwendet, oder trennen bzw. deaktivieren Sie Ihr anderes USB-Multimediagerät.
* Wenn Sie eine laute Rausch Blase von ihren verbundenen Hand Hörern bemerken, kann der USB-Hub des PCs möglicherweise nicht genügend Stromversorgung für das Windows Mixed Reality-Headset bereitstellen. Wenn dies auftritt, melden Sie einen [Feedback-Hub](/hololens/hololens-feedback) -Bug, und versuchen Sie Folgendes:
    * Entfernen von Erweiterungs Kabeln
    * Verwenden eines dedizierten, externen USB 3,0-Hubs
    * einen anderen USB-Anschluss auf dem PC

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Mein Bluetooth-audioheadset funktioniert nicht erwartungsgemäß.

Microsoft empfiehlt nicht die Verwendung von Bluetooth-Audioheadsets mit Windows Mixed Reality. Bluetooth-audiodatenperipherie funktioniert nicht gut mit Windows Mixed Reality-sprach-und räumlichen Sound Umgebungen. Bluetooth-Audioheadsets können die Mikrofon Eingabe und die Stereoausgabe nicht gleichzeitig unterstützen, sodass Sie Stereo-oder spatialisierte Sounds nicht hören, wenn Sie es für gamechat oder andere Spracheingaben verwenden. Bluetooth-Audioheadsets können sich auch negativ auf den Bewegungs Controller auswirken.

## <a name="sound-isnt-coming-from-expected-directions"></a>Sound kommt nicht in den erwarteten Richtungen vor

Die Windows Mixed Reality-Startseite bietet räumlichen Sound (Audio, der so aussieht, als ob es von den Anwendungen in Ihrer Startseite stammt). Wenn Sie sich ein-und ausschalten, werden die audiorichtung und-Ebene so geändert, dass Sie den Sinn von Realismus verbessern. Im folgenden finden Sie einige mögliche Gründe für unerwartete Sound Richtungen:

* Wenn Sie Musik von einer Hintergrund fähigen Musik-app (wie Groove Music) in ihrer eigenen Homepage öffnen und wiedergeben und dann eine immersive VR-Erfahrung wie ein Spiel öffnen, wird der Sound von der Musik-app von räumlichem Sound zu Stereo übertragen. Es ist möglicherweise lauter, da zwischen Ihnen und dem Sound kein Abstand mehr besteht.
* Wenn Cortana auf Ihrem PC aktiviert war, bevor Sie Ihr Windows Mixed Reality-Headset verwenden, verlieren Sie möglicherweise den räumlichen Sound, der auf die apps in Ihrer Windows Mixed Reality-Startseite angewendet wird. Um dieses Problem zu beheben, deaktivieren Sie "Cortana in den **Einstellungen > Cortana** auf Ihrem Desktop vor dem Starten von Windows Mixed Reality", oder aktivieren Sie "Windows Sonic for Kopfhörer":
    1. Wechseln Sie in Windows Mixed Reality Home zum Fenster Desktop-App.
    2. Klicken Sie in der Desktop-Taskleiste mit der linken Maustaste auf das Redner Symbol, und wählen Sie es aus der Liste der Audiogeräte aus.
    3. Klicken Sie in der Desktop-Taskleiste mit der rechten Maustaste auf das Redner Symbol, und wählen Sie im Menü "sprechersetup" die Option "Windows-Sound für Kopfhörer"
    4. Wiederholen Sie diese Schritte für alle Ihre Audiogeräte (Endpunkte).

## <a name="speech-commands-are-not-working-as-expected"></a>Sprachbefehle funktionieren nicht erwartungsgemäß.

* Um Sprachbefehle verwenden zu können, müssen sprach-und Spracheinstellungen auf Ihrem PC auf eine Sprache festgelegt werden, die [in Windows Mixed Reality unterstützt](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages)wird. Um die Einstellungen für die Windows-Spracherkennung und-Sprache zu überprüfen, wählen Sie **Einstellungen > Zeit & Sprache > Region & Sprache** und **Einstellungen >** Sprache & Sprache >.
* Wenn Ihr Headset nicht über ein integriertes Mikrofon verfügt, müssen Sie dem Headset oder Ihrem PC Kopfhörer mit einem Mikrofon anfügen. Wenn Sie die Mikrofon Eingabe bei der Nutzung automatisch zu Ihrem Headset wechseln möchten, wechseln Sie zu **Einstellungen > gemischte Realität > Audiosprache und sprach** Eingabe, und aktivieren Sie die Option "Wenn ich mein Headset trage, zu" Headset mic "wechseln.
* Einige Audioheadsets verfügen über eine physische Schaltfläche, um das Mikrofon zu stumm schalten und zu entstumm schalten. Wenn Sprachbefehle nicht funktionieren, überprüfen Sie, ob Ihr Mikrofon stumm geschaltet ist.
* Audioheadsets mit einem Mikrofon, das sich aus dem Earbud-Kabel unterscheidet, sind für Sprachbefehle in Umgebungen mit Umgebungsgeräuschen nicht gut geeignet.
* Cortana kann langsam sein, wenn Sie zum ersten Mal in einer gemischten Reality-Portal Sitzung aufgerufen wird. Wechseln Sie zu **Einstellungen > Cortana > sprechen Sie mit Cortana,** und stellen Sie sicher, dass "Cortana auf Hey Cortana Antworten" aktiviert ist.
* Auf einigen PCs ist der Standardwert für die sprach Erfassung für Ihr mit dem Headset verbundenes Mikrofon möglicherweise zu niedrig festgelegt. Führen Sie die Problembehandlung für die Mikrofon Einrichtung aus, wenn unzuverlässige Sprachbefehle oder Diktat Muster angezeigt werden:
    1. Wechseln Sie zur Desktop-app in der Windows Mixed Reality-Startseite, und verwenden Sie das Headset (um das Mikrofon zu beeinflussen, das Sie für Windows Mixed Reality verwenden).
    2. Wechseln Sie zu **Einstellungen > Zeit & Sprache > Sprache**.
    3. Wählen Sie im Abschnitt "Mikrofon" den Abschnitt "Get Started" aus.
    4. Wählen Sie den entsprechenden Endpunkt im Problembehandlungs-Assistenten aus.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Ich habe nur ein audioheadset und möchte es für Desktop und mein Headset verwenden.

Wenn Sie nur über ein audioheadset verfügen und nicht über ein Headset mit integrierten Kopfhörern verfügen, verbinden Sie das audioheadset anstelle des Headsets mit dem PC. Deaktivieren Sie dann in den Einstellungen des Mixed Reality-Portals die Option "zu Headset-audiowechsel wechseln".

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Ich möchte zu Dolby Atmos für Kopfhörer wechseln

Windows Mixed Reality-Umgebungen und ihre Apps verwenden Windows Sonic für die Verwendung von Benutzeroberflächen-Technologien für räumliche Daten, die an gemischte Realität angepasst werden. Andere räumliche Audiotechnologien wie Dolby Atmos für Kopfhörer können auf Vollbildanwendungen wie steamvr-Spiele angewendet werden, aber nicht auf die Windows Mixed Reality Shell-Umgebungen und-Apps (z. b. das Platzieren eines Webbrowsers an der Wand des Klippe-oder des Sky-Loft), die mit Windows-Sonic für den räumlichen Sound und die Akustik von Audiodaten entworfen wurden.