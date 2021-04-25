---
title: Controller in Windows Mixed Reality
description: Erfahren Sie, wie Sie häufige Probleme mit Controllern in Windows Mixed Reality einrichten, koppeln, verwenden und beheben.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: 66b352696016577ab121520102dd766b030ccf0e
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944631"
---
# <a name="motion-controllers-in-windows-mixed-reality"></a>Motion Controller in Windows Mixed Reality

Motion-Controller sind Hardwareaccessements, mit denen Benutzer in Mixed Reality interagieren können. Ein Vorteil von Motion-Controllern gegenüber Gesten ist, dass die Controller eine präzise Position im Raum haben, die eine differenzierte Interaktion mit digitalen Objekten ermöglicht. Bei Windows Mixed Reality immersiven Headsets sind Motion-Controller die primäre Methode, mit der Benutzer in ihrer Welt Maßnahmen ergreifen.

Windows Mixed Reality Motion-Controller bieten eine präzise und reaktionsfähige Bewegungsnachverfolgung in Ihrem Sichtfeld über die Immersive Headset-Sensoren. Es ist nicht erforderlich, Hardware auf den Wänden in Ihrem Raum zu installieren. Diese Motion-Controller bieten die gleiche einfache Einrichtung und Portabilität wie Windows Mixed Reality immersive Headsets.

Sie können auch einen Xbox-Controller, eine Maus und eine Tastatur verwenden oder [sich nur mit Ihrer Stimme](using-speech-in-wmr.md)bewegen.

## <a name="motion-controller-setup"></a>Einrichtung des Motion-Controllers

Die meisten Headsets sind direkt mit dem Headset gekoppelt, aber einige frühe Headsets erfordern, dass die Motion-Controller mit Bluetooth 4.0 mit Ihrem PC gekoppelt werden. Wenn Sie Ihr immersives Headset zum ersten Mal verbinden, werden Sie während des Setups durch das Einschalten Ihrer Motion-Controller durchlaufen. Wenn Sie sie später jedoch erneut koppeln müssen, wird Folgendes erläutert:

1. Starten Sie **Mixed Reality-Portal** mit angeschlossenen Headsets.  
2. Wählen Sie in der unteren linken Ecke **... > Controller einrichten** aus.
3. Fügen Sie zwei AA-Akkus in jeden Controller ein, und versetzen Sie Ihren Controller in den Kopplungsmodus (siehe Anweisungen im [Abschnitt Zum Koppeln von Motion-Controllern).](controllers-in-wmr.md#pair-motion-controllers)
4. Befolgen Sie die Anweisungen auf dem Bildschirm.

> [!NOTE]
> * Für Controller, die sich direkt an Ihren PC koppeln, müssen Sie sie in den Kopplungsmodus versetzen, indem Sie sie einschalten und dann die Kopplungsschaltfläche im Akkufach drücken, bis die Beleuchtung blinkt.
> * Motion-Controller unterstützen jeweils nur das Koppeln mit einem PC. Wenn Sie sie mit einem anderen Headset verwenden müssen, müssen Sie den Kopplungsprozess durchgehen. Weitere [Informationen finden Sie unter Einrichten Windows Mixed Reality](set-up-windows-mixed-reality.md)

[Hilfe beim Herstellen einer Verbindung](wmr-setup-faq.yml#my-motion-controllers-aren-t-working)

> [!IMPORTANT]
> **Sie haben einen Xbox-Controller?**
> 
> Wenn Sie über einen Bluetooth Xbox-Controller verfügen, koppeln Sie ihn mit Ihrem PC, um ihn mit Ihrem Headset zu verwenden.
> 
> Wenn Sie über einen kabelgebundenen Xbox-Controller verfügen, schließen Sie ihn an Ihren PC an.
> 
> Einige Spiele und Apps verwenden den Xbox-Controller anders als in Mixed Reality. Um den Controller für ein Spiel oder eine App zu verwenden, wählen Sie **Als Gamepad verwenden** App-Leiste aus, oder sagen Sie "Als Gamepad verwenden." Um den Controller wieder zu Mixed Reality zu wechseln, wählen **Sie Als Gamepad verwenden** aus, oder sagen Sie "Mit Anvisieren verwenden".  

## <a name="pair-motion-controllers"></a>Koppeln von Motion-Controllern

Wenn Sie ein Headset verwenden, das einen integrierten Bluetooth-Controller enthält, z. B. Samsung Samsung Samsung+ oder HP Reverb, sollten Ihre Controller bereits gekoppelt sein. Sie können Ihre Controller jedoch weiterhin mithilfe der Setup-App koppeln (sie sollte bereits während der HMD-Einrichtung installiert sein). Sie können es auch aus dem Microsoft Store erhalten.

### <a name="pair-motion-controllers-to-hmd"></a>Koppeln von Motion-Controllern mit HMD

Netzen Sie die Controller ein, indem Sie die Windows-Taste zwei Sekunden lang drücken, bis LEDs einglühen.

Entfernen Sie die Akkuabdeckung von Ihren Controllern, und suchen Sie die kleine Kopplungsschaltfläche am Rand des Controllers. Halten Sie diese Schaltfläche gedrückt, um sie mit Ihrem PC zu koppeln.
    ![Kopplung des Bewegungscontrollers](images/connect_controller.png)

Starten **Mixed Reality-Portal** mit verbundenem Headset.  
Wählen Sie in der linken unteren Ecke **... > Einrichten von Controllern aus.**
Folgen Sie den Anweisungen auf dem Bildschirm.

### <a name="pair-motion-controllers-to-pc"></a>Koppeln von Motion-Controllern mit dem PC

Sie können Ihren Controller mit einem PC koppeln, indem Sie ein weiteres Bluetooth-Gerät hinzufügen.

Schalten Sie die Controller ein, und platzieren Sie sie wie oben beschrieben im Kopplungsmodus.

* Navigieren Sie zu Computereinstellungen.
* Gerät/Bluetooth oder anderes Gerät hinzufügen.

Sobald die Kopplung abgeschlossen ist, sind LEDs eingezogen und hell.

### <a name="common-issues"></a>Häufige Probleme

* Vergewissern Sie sich, dass auf Ihrem PC nur ein Bluetooth-Radio aktiv ist. Wenn Sie über mehrere Bluetooth-Radios verfügen, müssen Sie die anderen Radios in Geräte-Manager deaktivieren.
* Platzieren Sie Ihr Bluetooth-Dongle in einem Port, der eine klare Sichtlinie zu Ihren Controllern hat und weit davon entfernt ist, usb 3.0-Geräte angeschlossen zu haben. USB 3.0 hat bekanntermaßen RF-Interferenzen mit Bluetooth (weitere Informationen finden Sie [in diesem Artikel](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/usb3-frequency-interference-paper.pdf) von Intel). USB 2.0-Anschlüsse funktionieren möglicherweise besser für Ihren Bluetooth-Dongle.
* Stellen Sie sicher, dass Ihr Bluetooth-Dongle nicht an einen USB-Anschluss neben dem USB-Kabel Ihrer HMD angeschlossen ist. Das Headsetkabel hat bekanntermaßen auch Störungen mit Bluetooth-Kabeln verursacht. Schließen Sie den Dongle an den vorderen USB-Anschluss auf Ihrem PC an, um optimale Ergebnisse zu erzielen.
* Stellen Sie für Notebooks sicher, dass WLAN mit einem 5-GHz-Band verbunden ist, um ein optimales Erlebnis zu gewährleisten. Wählen Sie unten rechts das Funknetzwerksymbol aus, und wählen Sie Eigenschaften für das netzwerk aus, das Sie verwenden. Notebooks, die so konzipiert sind, dass sie eine 2,4-GHz-Antenne für Bluetooth- und WLAN-Konnektivität gemeinsam nutzen, sehen eine Überlastung der Daten aufgrund langsamer Netzwerkgeschwindigkeiten oder schlechter Nachverfolgungsleistung des Bewegungscontrollers.
* Ihre Motion-Controller erhalten in regelmäßigen Abständen neue Softwareupdates von Microsoft. Die Controller zeigen ein abwechselndes Muster von Blinklichtern, wenn sie diese neuen Softwareupdates erhalten. Dies ist normal. Warten Sie, bis das Softwareupgrade abgeschlossen ist, bevor Sie die Controller verwenden. Die Controller vibrieren, und ein konstantes Licht ersetzt das abwechselnde Flashmuster, wenn es fertig ist.
* Möglicherweise wird Ihnen mitgeteilt, dass Sie "Das Headset anstäuchen und den Fingerabdruck zum Teleportieren verwenden", bevor die Controller den Updatevorgang beenden. Die Controller sind erst sichtbar oder nutzbar, wenn das Update abgeschlossen ist. Die meisten Updates erfolgen innerhalb von zwei Minuten, aber Updates können bis zu 10 Minuten dauern. Warten Sie, bis das Update abgeschlossen ist, bevor Sie mit dem nächsten Schritt fortfahren.

## <a name="using-controllers"></a>Verwenden von Controllern

Hier erfahren Sie, wie Sie sich in Mixed Reality mit Motion-Controllern, einem Xbox-Gamepad oder einer Maus und Tastatur bewegen.

> [!TIP]
> Um die Eingabe zwischen Mixed Reality und Ihrem Desktop zu wechseln, drücken Sie **die Windows-LOGO-TASTE + Y auf** ihrer PC-Tastatur.

![Schaltflächenzuordnung des Bewegungscontrollers](images/get_to_know_controllers.png)

|  Aufgabe  |  Bewegungscontroller  | Gamepad | Maus und Tastatur |
| --- | --- | --- | --- |
| Teleport | Drücken Sie den Fingerabdruck nach vorn, und zeigen Sie dann den Controller an den Ort, an den Sie wechseln möchten. Geben Sie den Thumbstick frei. | Drücken Sie den linken Fingerabdruck nach vorn, und suchen Sie, wohin Sie wechseln möchten. Geben Sie den Thumbstick frei. | Wählen Sie die rechte Schaltfläche aus, halten Sie sie gedrückt, und zeigen Sie dann mit der Maus, wohin Sie wechseln möchten. Lassen Sie die Schaltfläche los. |
| Select | Zeigen Sie auf den Controller, und ziehen Sie dann den Trigger, oder verwenden Sie das Touchpad. | Sehen Sie sich das Ziel an, und drücken Sie dann A. | Zeigen Sie mit der Maus, und klicken Sie dann mit der linken Maustaste. |
| Öffnen des Startmenüs | Klicken  Sie auf die Windows-Schaltfläche. | Klicken  Sie auf die Xbox-Schaltfläche. | Drücken Sie die **Windows-LOGO-TASTE.** |
| Belassen einer immersiven App | Klicken  Sie auf die Windows-Schaltfläche. Wählen Sie dann im Menü "Schnelle Aktionen" die Option **Mixed Reality home** aus. | Klicken  Sie auf die Xbox-Schaltfläche. Wählen Sie dann im Menü "Schnelle Aktionen" die Startschaltfläche **Mixed Reality** aus. | Drücken Sie die **Windows-Logo-TASTE. Wählen Sie dann im angezeigten Menü Schnellaktionen die Startschaltfläche **Mixed Reality** aus. |
| Rotate | Bewegen Sie den Fingerabdruck nach links oder rechts. | Bewegen Sie den rechten Stick nach links oder rechts. | Nicht verfügbar. |
| Sichern | Bewegen Sie den Thumbstick rückwärts. | Bewegen Sie den linken Stick rückwärts. | Nicht verfügbar. |
| Walk | Drücken Sie den Daumenstick direkt nach unten, und drücken Sie ihn dann in die Richtung, in der Sie gehen möchten. | Pushen Sie den linken Stick direkt nach unten, und drücken Sie ihn in die Richtung, in der Sie gehen möchten. | Nicht verfügbar. |
| Verschieben eines App-Fensters | Zeigen Sie auf die App-Leiste. Ziehen Sie den Trigger, und halten Sie ihn, um das Fenster zu greifen, und verwenden Sie dann den Controller, um es in eine beliebige Richtung zu verschieben. Geben Sie den Trigger frei. | Sehen Sie sich die App-Leiste an, und halten Sie A gedrückt, um das Fenster zu greifen. Verwenden Sie den linken Stick, um das Fenster nebeneinander oder nach oben oder unten zu verschieben. Verwenden Sie die Trigger, um sie näher und weiter zu verschieben. Geben Sie dann A frei. | Zeigen Sie mit der Maus auf die App-Leiste. Klicken Sie mit der linken Maustaste, und halten Sie es gedrückt, um das Fenster zu greifen, und bewegen Sie es dann mit der Maus nebeneinander oder nach oben und unten. Verwenden Sie das Scrollrad, um das Fenster näher oder weiter zu verschieben. Lassen Sie die Maustaste los. |
| Verschieben eines 3D-Objekts | Zeigen Sie auf das -Objekt, und halten Sie dann den Trigger, um ihn zu greifen. Verschieben Sie sie mit dem Controller in eine beliebige Richtung, und geben Sie dann den Trigger frei. | Sehen Sie sich das Objekt an, und halten Sie A gedrückt, um es zu greifen. Verwenden Sie den linken Stick, um das Fenster nebeneinander oder nach oben oder unten zu verschieben. Verwenden Sie die Trigger, um sie näher und weiter zu verschieben. Geben Sie dann A frei. | Zeigen Sie mit der Maus auf das -Objekt. Klicken Sie mit der linken Maustaste, und halten Sie sie gedrückt, um sie zu greifen, und bewegen Sie sie dann mit der Maus nebeneinander oder nach oben und unten.  Verwenden Sie das Scrollrad, um es näher oder weiter zu verschieben. Lassen Sie die Maustaste los. |
| Drehen oder Ändern der Größe eines App-Fensters | Zeigen Sie einen Controller auf die App-Leiste und den anderen Controller an einer beliebigen Stelle im Fenster. Halten Sie beide Trigger fest, und verschieben Sie die Controller dann zusammen oder auseinander, um die Größe zu ändern.  Um zu drehen, verschieben Sie einen Controller zu Ihnen und den anderen weg von Ihnen. Geben Sie die Trigger frei. | Klicken Sie auf der App-Leiste auf **Anpassen.** Sehen Sie sich eine Ecke des Anpassungsrahmens an, und drücken Sie dann A, um ihn auszuwählen. Verwenden Sie den linken Stick, um die Größe des Fensters zu ändern.  | Klicken Sie auf der App-Leiste auf **Anpassen.** Halten Sie eine Ecke des Anpassungsrahmens fest, und verwenden Sie dann die Maus, um die Größe des Fensters zu ändern. |
| Drehen oder Ändern der Größe eines 3D-Objekts | Zeigen Sie beide Controller auf das -Objekt. Halten Sie beide Trigger gedrückt, und verschieben Sie dann die Controller zusammen oder getrennt, um die Größe zu ändern.  Bewegen Sie zum Drehen einen Controller auf Sie zu, und den anderen weg von Ihnen. | Klicken Sie auf der App-Leiste auf **Anpassen,** und verschieben Sie das Objekt mithilfe des linken Sticks. | Klicken Sie auf der App-Leiste auf **Anpassen,** halten Sie das Objekt fest, und bewegen Sie es mit der Maus. |
| Scrollen in einem App-Fenster | Ziehen Sie den Trigger, halten Sie ihn gedrückt, und verschieben Sie dann den Controller nach oben oder unten.  | Verwenden Sie das D-Pad. | Verwenden Sie das Mausrad. |
| Vergrößern oder Verkleinern im App-Fenster | Ziehen Sie beide Trigger, und verschieben Sie dann die Controller näher beieinander oder weiter auseinander. | Ziehen Sie den rechten Trigger, um ihn zu vergrößern, und den linken Trigger zum Verkleinern. | Verwenden Sie das Mausrad, während Sie die STRG-TASTE auf der Tastatur gedrückt halten. |
| Menü öffnen | Klicken Sie auf **die Schaltfläche Menü.** | Klicken Sie auf **die Schaltfläche Menü.** | Klicken Sie mit der rechten Maustaste. |

## <a name="what-do-the-vibrations-and-lights-mean"></a>Was bedeuten vibrations- und lights-Mittelwerte?

Ihr Controller teilt Ihnen mit, was er tut, indem er seine LED-Beleuchtung ein- und blinkt.

|  Wenn Ihr Controller dies tut  |  Dies bedeutet, dass |
| --- | --- |
| LEDs werden ein-/aus- und der Controller lädt einmal | **Aktivieren** |  
| LEDs werden ausgeschaltet, und der Controller lässt zweimal | **Ausschalten** |
| LEDs blinken alle 3 Sekunden | **Schlafen** |
| LEDs werden langsam geimiert, und der Controller lässt einmal | **Wechseln in den Kopplungsmodus** |
| Controller 2017 | **Herstellen einer Verbindung oder Trennen der Verbindung mit Ihrem PC** |
| LEDs werden hell erlichtet | **Controller, die von Headsets nachverfolgt werden** |
| LEDs sind schwach ausgeblendet | **Controller, die nicht vom Headset nachverfolgt werden** |
| Controller vibriert dreimal und schaltet dann aus | **Kritischer Akkustand** |
| Die äußeren und inneren Ringe von LEDs blinken in einem abwechselnden Muster. | **Wird aktualisiert** |

## <a name="updating-motion-controllers-firmware"></a>Aktualisieren der Motion Controller-Firmware

* Wenn ein immersives Headset mit Ihrem PC verbunden ist und neue Controllerfirmware verfügbar ist, wird die Firmware automatisch an Ihre Motion Controller gepusht, wenn sie das nächste Mal eingeschaltet wird.
* Controllerfirmwareupdates werden mit einem Muster der Beleuchtung von LED-Quadranten in einer Kreisbewegung angezeigt und dauern 1-2 Minuten. Firmwareupdates können gelegentlich länger (bis zu 10 Minuten) dauern, was auf eine schlechte Bluetooth-Konnektivität oder Funkinterferenz hindeuten kann.
* Falls das Firmwareupdate unterbrochen wird (Controller ausgeschaltet oder Akku ausgeschaltet), wird es beim nächsten Einschalten erneut versucht.
* Nach Abschluss des Firmwareupdates werden die Controller neu gestartet und die Verbindung wiederhergestellt.
* Beide Controller sollten jetzt verbunden sein. Navigieren Sie zu Mixed Reality-Portal, um den Status Ihrer Controller zu überprüfen.
* Überprüfen Sie, ob Ihre Controller ordnungsgemäß funktionieren:
  * Starten Sie **Mixed Reality-Portal,** und geben Sie Ihr Mixed Reality Home ein.
  * Verschieben Sie Ihre Controller, überprüfen Sie die Nachverfolgung, testen Sie Schaltflächen, und überprüfen Sie, ob die Teleportierung funktioniert. Falls nicht, lesen Sie den Abschnitt zur Problembehandlung für [den Motion-Controller.](motion-controller-problems.md)

## <a name="faq"></a>Häufig gestellte Fragen

### <a name="how-can-i-check-battery-level"></a>Wie kann ich den Akkustand überprüfen?

*A: Der Akkustand befindet sich auf der umgekehrten Seite des virtuellen Modells, es gibt keinen Indikator für den physischen Akkustand. Warten Sie nach dem Einschalten des Controllers einige Sekunden, bis sich der Lesestand stabilisiert hat.*

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Können Sie diese Controller ohne Headset verwenden? Nur für die Eingabe "trigger/etc"?

*A: Nicht für universelle Windows-Anwendungen*

## <a name="filing-motion-controller-feedbackbugs"></a>Einreichen von Feedback/Fehlern für den Motion Controller

Senden Sie uns feedback in Feedback-Hub mithilfe der Kategorie "Mixed Reality -> Input".

## <a name="see-also"></a>Weitere Informationen:

- [HP-Controller in Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
- [HP-Controller in Unreal](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
- [Die Community fragen](https://answers.microsoft.com)
- [Wenden Sie sich an uns, um Support zu erhalten.](https://support.microsoft.com/contactus/)
- [Problembehandlung](troubleshooting-windows-mixed-reality.md)

Haben Sie Probleme mit Ihren Motion-Controllern? [Hilfe erhalten](motion-controller-problems.md)