---
title: Häufig gestellte Fragen zu Sprache und Audio
description: Sprach- und Audio Windows Mixed Reality Problembehandlung, die über unsere Standarddokumentation für den Kundensupport hinausgeht.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support, Audioprobleme, Sprachprobleme
ms.openlocfilehash: d1d30cebb40d54d579e978013b9abc60981fa943d43b95a96f358092631b4d27
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208980"
---
# <a name="speech-and-audio-faqs"></a>Häufig gestellte Fragen zu Sprache und Audio

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Ich kann keinen Sound in meinem Headset hören, oder der Sound wird über meinen Computer und nicht über mein Headset abspielt.

* Wenn Ihr immersives Headset keine integrierten Mikrofone enthält, verbinden Sie die Mikrofone mit der Audiobuchse des Headsets. Die Buchse befindet sich häufig direkt hinter oder unter dem Headsetvisor oder den Brillen. Informieren Sie sich bei Ihrem Headsethersteller, wenn Sie es nicht finden.
* Einige Audio-Headsets verfügen über physische Schaltflächen, um das Volume zu steuern. Wenn Audio nicht funktioniert, überprüfen Sie, ob das Volume ausgeschaltet oder stummgeschaltet ist.
* Audio wechselt zu Ihrem Standardgerät für Windows Wiedergabegerät: 
    * Wenn Sie das Headset ausschalten
    * Kippen des Visors nach oben
    * Schließen der Mixed Reality-Portal-App
    * Wenn eine App 15 Minuten lang nicht verwendet wurde. 
    * Sie können diese Einstellung in mixed reality Einstellungen > **Audio > Speech ändern.**
* Stellen Sie sicher, dass Ihr Audio-Headset an die Audiobuchse angeschlossen ist. Insbesondere das Acer-Headset erfordert möglicherweise mehr Sorgfalt, um sicherzustellen, dass das Audio-Headset angeschlossen ist.
* Stellen Sie sicher, dass das Audio-Headset/Mikrofon an das Headset und nicht an den PC angeschlossen ist.
* Der Sound Systemsteuerung in **Einstellungen > System > Sound zeigt** nur aktivierte Audioendpunkte und keine deaktivierten Endpunkte an. Das Headset-Audiogerät wird deaktiviert, wenn Sie das Headset nicht tragen. Klicken Sie zum Anzeigen mit der rechten Maustaste in den Sound Systemsteuerung und wählen Sie "Deaktivierte Geräte anzeigen" aus. Der Gerätename ist "Realtek USB2.0 Audio", der auf der Seite "Eigenschaften" umbenannt werden kann. Sie können dies sowohl für die Registerkarten "Wiedergabe" als auch "Aufzeichnung" tun.
* Wenn Ihre Audiodaten nicht in apps Mixed Reality, z. B. mit der Netflix-App. Dies kann durch ein bekanntes Problem verursacht werden, Windows Mixed Reality nicht automatisch entsprechend der Betriebssystemversion aktualisiert wird. Um dieses Problem zu beheben und die beste Mixed Reality zu erhalten, wechseln Sie zu Einstellungen > Update & Security > Windows Update > Check for Updates (Nach Updates **suchen).**

> [!NOTE]
> * Windows Mixed Reality Audio funktioniert am besten mit In- oder Direkt-Verbindung mit Ihrem immersiven Headset. PC-Lautsprecher oder -Geräte, die mit dem PC verbunden sind, funktionieren möglicherweise nicht gut für räumliche Audiodaten.
> * Windows Mixed Reality unterstützt keine Bluetooth Audio-Headsets.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Ich habe plötzliche Volumeänderungen, verlorene Audiodaten oder Rauschen

* Einige Apps, z. B. die apps, die überStreamVR gestartet wurden, können Audiodaten verlieren oder hängen bleiben, wenn sich das Audiogerät ändert, wenn Sie die App starten oder Mixed Reality-Portal. Um dies zu korrigieren, öffnen Sie die Mixed Reality-Portal, und starten Sie die App neu.
* Wenn ein anderes Multimedia-USB-Gerät (z. B. eine Web-Webcam) den gleichen internen oder externen USB-Hub mit dem Windows Mixed Reality-Headset teilt, kann die Headset-Audiobuchse oder die Headset-Audiobuchse gelegentlich einen tobenden Sound oder gar keine Audiodaten haben. Schließen Sie Ihr Headset an einen USB-Anschluss an, der einen anderen Hub verwendet, oder trennen/deaktivieren Sie Ihr anderes USB-Multimediagerät.
* Wenn Sie einen lauten Rauschen von Ihren verbundenen Anschlüssen bemerken, kann der USB-Hub des PCs möglicherweise nicht genügend Energie für das Windows Mixed Reality bereitstellen. Wenn dies der Fall ist, melden Sie [Feedback-Hub](/hololens/hololens-feedback) Fehler, und versuchen Sie:
    * Entfernen von Erweiterungskabeln
    * Verwenden eines dedizierten, extern betriebenen USB 3.0 HUB
    * einen anderen USB-Anschluss auf dem PC

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Mein Bluetooth Audio-Headset funktioniert nicht wie erwartet

Microsoft empfiehlt nicht die Verwendung Bluetooth Audio-Headsets mit Windows Mixed Reality. Bluetooth Audio-Peripheriegeräte funktionieren nicht gut mit Windows Mixed Reality Sprach- und Raumklangerfahrungen. Bluetooth Audio-Headsets können nicht gleichzeitig Mikrofoneingabe und Stereoausgabe unterstützen, sodass Sie stereo- oder spatialisierten Sound nicht hören, wenn Sie ihn für Gamechat oder andere Spracheingaben verwenden. Bluetooth Audio-Headsets können sich auch negativ auf die Benutzererfahrung Ihres Bewegungscontrollers auswirken.

## <a name="sound-isnt-coming-from-expected-directions"></a>Sound kommt nicht aus den erwarteten Richtungen

Das Windows Mixed Reality Home enthält räumlichen Sound (Audio, das so klingt, als ob es aus den Anwendungen stammt, die sich in Ihrer Startseite befinden). Wenn Sie sich umdrehen und sich von jeder App näher oder weiter bewegen, ändern sich die Soundrichtung und -ebene, um das Gefühl von Realismus zu erhöhen. Im Folgenden finden Sie einige mögliche Gründe für unerwartete Soundrichtungen:

* Wenn Sie Musik aus einer hintergrundfähigen Musik-App (z.B. Groove-Musik) in Ihrem Haus öffnen und dann eine immersive VR-Umgebung wie ein Spiel öffnen, überkreuzt sich der Sound aus der Musik-App von räumlichem Sound zu Stereo. Es kann lauter erscheinen, da kein Abstand mehr zwischen Ihnen und dem Sound besteht.
* Wenn Sie Cortana pc aktiviert hatten, bevor Sie Ihr Windows Mixed Reality-Headset verwendet haben, verlieren Sie möglicherweise den räumlichen Sound, der auf die Apps in Ihrem Windows Mixed Reality angewendet wird. Um dieses Problem zu beheben, deaktivieren Sie "Let Cortana respond to Hey Cortana" in **Einstellungen > Cortana** on your desktop before start Windows Mixed Reality (Lassen Sie Cortana auf Hey Cortana reagieren), bevor Sie Windows Mixed Reality starten, oder aktivieren Sie "Windows Sonic für Kopfhörer":
    1. Wechseln Sie zum Fenster Desktop-App in Windows Mixed Reality Start.
    2. Klicken Sie mit der linken Maustaste auf das Lautsprechersymbol auf der Taskleiste Desktop, und wählen Sie es aus der Liste der Audiogeräte aus.
    3. Klicken Sie mit der rechten Maustaste auf das Lautsprechersymbol in der Desktop-Taskleiste, und wählen Sie im Menü "Speaker setup" (Sprechereinrichtung) die Option "Windows Sonic für Kopfhörer" aus.
    4. Wiederholen Sie diese Schritte für alle Ihre Audiogeräte (Endpunkte).

## <a name="speech-commands-are-not-working-as-expected"></a>Sprachbefehle funktionieren nicht wie erwartet

* Um Sprachbefehle verwenden zu können, müssen die Sprach- und Spracheinstellungen auf Ihrem PC auf eine Sprache festgelegt werden, die [in Windows Mixed Reality.](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages) Wählen Windows Sie Einstellungen > Time **& language > Region &** language und Einstellungen > Time & Language > Speech aus, um Ihre Sprach- und Spracheinstellungen für Einstellungen > zu **überprüfen.**
* Wenn Ihr Headset nicht über ein integriertes Mikrofon verfügen, müssen Sie die Mikrofone mit einem Mikrofon an das Headset oder an Ihren PC anfügen. Damit die Mikrofoneingabe automatisch zu Ihrem Headset wechselt, wenn Sie es tragen, wechseln Sie zu **Einstellungen > Mixed Reality > Audio und** Sprache, und aktivieren Sie "Wenn ich mein Headset verschleiede, wechseln Sie zum Headset-Mikrofon".
* Einige Audio-Headsets verfügen über eine physische Schaltfläche zum Stummschalten und Entmuten des Mikrofons. Wenn Sprachbefehle nicht funktionieren, überprüfen Sie, ob Ihr Mikrofon stummgeschaltet ist.
* Audio headsets with a microphone that dangles from the earbud cable don't well for voice commands in environments with ambient noise.
* Cortana kann langsam sein, wenn sie zum ersten Mal in einer Mixed Reality-Portal wird. Wechseln Sie **zu Einstellungen > Cortana > Talk to Cortana,** und stellen Sie sicher, dass "Let Cortana respond to Hey Cortana" aktiviert ist.
* Auf einigen PCs ist der Standard-Spracherfassungsgewinn für Ihr mit dem Headset verbundenes Mikrofon möglicherweise zu niedrig festgelegt. Wenn unzuverlässige Sprachbefehle oder Diktate angezeigt werden, führen Sie die Problembehandlung für das Mikrofonsetup aus:
    1. Wechseln Sie zur Desktop-App im Windows Mixed Reality, während Sie das Headset verwenden (um sich auf das Mikrofon zu auswirken, das Sie für Windows Mixed Reality).
    2. Wechseln Sie **zu Einstellungen > Time & Language > Speech**.
    3. Wählen Sie "Erste Schritte" im Abschnitt "Mikrofon" aus.
    4. Wählen Sie im Problembehandlungs-Assistenten den entsprechenden Endpunkt aus.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Ich habe nur ein Audio-Headset und möchte es sowohl für Desktop als auch für mein Headset verwenden.

Wenn Sie nur über ein Audio-Headset verfügen und kein Headset mit integrierten Mikrofonen haben, verbinden Sie das Audio-Headset mit dem PC anstelle des Headsets. Deaktivieren Sie dann "Switch to headset audio" (Zu Headset-Audio wechseln) in Mixed Reality-Portal Einstellungen.

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Ich möchte zu "Dolby Atmos for Headphones

Windows Mixed Reality-Umgebungen und ihre Apps verwenden Windows Sonic für Kopfhörer räumliche Audiotechnologie, die für Mixed Reality-Umgebungen angepasst ist. Andere Räumliche Audiotechnologien wie Dolby Atmos for Headphones können für Vollbild-Apps wieStreamVR-Spiele, aber nicht für die Windows Mixed Reality-Shellumgebungen und -Apps (z. B. das Platzieren eines Webbrowsers an der Wand der Haus an den Klippen oder skyBereich) angewendet werden, die mit Windows Sonic für Kopfhörer-Raumklang und Akustik entworfen wurden.