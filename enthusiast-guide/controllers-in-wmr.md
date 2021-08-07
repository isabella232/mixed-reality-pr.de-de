---
title: Controller in Windows Mixed Reality
description: Hier erfahren Sie, wie Sie häufige Probleme mit Controllern in der Anwendung einrichten, koppeln, verwenden und Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: bc5983706d75d6c66bb8de375b38f2ebe0d3f0aba0d90be5ef1e39d5a6949743
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187988"
---
# <a name="motion-controllers-in-windows-mixed-reality"></a>Motion Controller in Windows Mixed Reality

Motion-Controller sind Hardwareaccessures, mit denen Benutzer in Mixed Reality interagieren können. Ein Vorteil von Bewegungscontrollern gegenüber Gesten ist, dass die Controller eine präzise Position im Raum haben, was eine präzise Interaktion mit digitalen Objekten ermöglicht. Für Windows Mixed Reality immersive Headsets sind Motion Controller die primäre Methode, mit der Benutzer in ihrer Welt Maßnahmen ergreifen.

Windows Mixed Reality Motion-Controller bieten eine präzise und reaktionsfähige Bewegungsnachverfolgung in Ihrem Sichtbereich über die Sensoren des immersiven Headsets. Es ist nicht erforderlich, Hardware an den Wänden in Ihrem Raum zu installieren. Diese Motion-Controller bieten die gleiche Einfache Einrichtung und Portabilität wie Windows Mixed Reality immersive Headsets.

Sie können auch einen Xbox-Controller, eine Maus und eine Tastatur verwenden oder sich einfach mit [Ihrer Stimme bewegen.](using-speech-in-wmr.md)

## <a name="motion-controller-setup"></a>Einrichtung des Bewegungscontrollers

Die meisten Headsets werden direkt mit dem Headset vorab gekoppelt, aber einige frühe Headsets erfordern, dass die Motion-Controller mit Ihrem PC mit Bluetooth 4.0 gekoppelt werden. Wenn Sie Ihr immersives Headset zum ersten Mal verbinden, werden Sie während des Setups durch das Einschalten Ihrer Motion-Controller gehen. Wenn Sie sie später jedoch erneut koppeln müssen, sehen Sie sich wie hier an:

1. Starten **Mixed Reality-Portal** mit verbundenem Headset.  
2. Wählen Sie in der linken unteren Ecke **... > Einrichten von Controllern aus.**
3. Fügen Sie zwei AA-Akkus in jeden Controller ein, und setzen Sie Ihren Controller in den Kopplungsmodus (siehe Anweisungen im Abschnitt ["Paarbewegungscontroller".](controllers-in-wmr.md#pair-motion-controllers)
4. Befolgen Sie die Anweisungen auf dem Bildschirm.

> [!NOTE]
> * Bei Controllern, die direkt mit Ihrem PC koppeln, müssen Sie sie in den Kopplungsmodus bringen, indem Sie sie einschalten und dann die Kopplungsschaltfläche im Akkudeku drücken, bis die Beleuchtung blinkt.
> * Motion-Controller unterstützen nur die Kopplung mit einem PC gleichzeitig. Wenn Sie sie mit einem anderen Headset verwenden müssen, müssen Sie den Kopplungsprozess durchgehen. Weitere [Informationen finden Sie Windows Mixed Reality](set-up-windows-mixed-reality.md)

[Hilfe beim Herstellen einer Verbindung](wmr-setup-faq.yml#my-motion-controllers-aren-t-working)

> [!IMPORTANT]
> **Sie haben einen Xbox-Controller?**
> 
> Wenn Sie über einen Bluetooth Xbox-Controller verfügen, koppeln Sie ihn mit Ihrem PC, um ihn mit Ihrem Headset zu verwenden.
> 
> Wenn Sie über einen kabelgebundenen Xbox-Controller verfügen, schließen Sie ihn an Ihren PC an.
> 
> Einige Spiele und Apps verwenden den Xbox-Controller anders als in Mixed Reality. Um den Controller für ein Spiel oder eine App zu verwenden, wählen Sie **Als Gamepad verwenden** App-Leiste aus, oder sagen Sie "Als Gamepad verwenden". Um den Controller wieder zu Mixed Reality zu wechseln, wählen **Sie Als Gamepad verwenden** aus, oder sagen Sie "Mit Anvisieren verwenden".  

## <a name="pair-motion-controllers"></a>Koppeln von Motion-Controllern

Wenn Sie ein Headset verwenden, das einen integrierten Bluetooth-Controller enthält, z. B. Samsung Samsung Oder HP Reverb, sollten Ihre Controller bereits gekoppelt sein. Sie können Ihre Controller jedoch weiterhin mithilfe der Setup-App koppeln (sie sollte bereits während der HMD-Einrichtung installiert sein). Sie können es auch aus dem Microsoft Store erhalten.

### <a name="pair-motion-controllers-to-hmd"></a>Koppeln von Motion-Controllern mit HMD

Stellen Sie die Controller ein, indem Sie Windows zwei Sekunden lang drücken, bis LEDs einglühen.

Entfernen Sie die Akkuabdeckung von Ihren Controllern, und suchen Sie die kleine Kopplungsschaltfläche am Rand des Controllers. Halten Sie diese Schaltfläche gedrückt, um sie mit Ihrem PC zu koppeln.
    ![Kopplung des Bewegungscontrollers](images/connect_controller.png)

Starten **Mixed Reality-Portal** mit verbundenem Headset.  
Wählen Sie in der linken unteren Ecke **... > Einrichten von Controllern aus.**
Folgen Sie den Anweisungen auf dem Bildschirm.

### <a name="pair-motion-controllers-to-pc"></a>Koppeln von Motion-Controllern mit dem PC

Sie können Ihren Controller mit einem PC koppeln, indem Sie ein weiteres Bluetooth-Gerät hinzufügen.

Stellen Sie die Controller ein, und platzieren Sie sie wie oben beschrieben in den Kopplungsmodus.

* Navigieren Sie zu Computereinstellungen.
* Gerät/Hinzufügen Bluetooth oder eines anderen Geräts.

Sobald die Kopplung abgeschlossen ist, sind die LEDs voll und hell.

### <a name="common-issues"></a>Häufige Probleme

* Vergewissern Sie sich, dass nur ein Bluetooth auf Ihrem PC aktiv ist. Wenn Sie über mehr als ein Bluetooth verfügen, müssen Sie die anderen Radios in der Geräte-Manager.
* Platzieren Sie Bluetooth an einem Port, der eine klare Sichtlinie zu Ihren Controllern hat und weit von USB 3.0-Geräten entfernt ist. USB 3.0 ist bekannt, dass rf interferenz mit Bluetooth [(weitere](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/usb3-frequency-interference-paper.pdf) Informationen finden Sie in diesem Artikel von Intel). USB 2.0-Anschlüsse funktionieren möglicherweise besser für Ihre Bluetooth Dongle.
* Stellen Sie sicher, Bluetooth nicht an einen USB-Anschluss neben dem USB-Kabel Ihres HMD angeschlossen ist. Es ist bekannt, dass das Headsetkabel auch Störungen mit Bluetooth verursacht. Schließen Sie den Dongle an den front-USB-Anschluss ihres PCs an, um optimale Ergebnisse zu erzielen.
* Stellen Sie für Notebooks sicher, dass wlan mit dem 5-GHz-Band verbunden ist, um die bestmögliche Benutzererfahrung zu bieten. Wählen Sie das Drahtlosnetzwerksymbol unten rechts aus, und wählen Sie Eigenschaften für das netzwerk, das Sie verwenden. Notebooks, die eine 2,4-GHz-Antenne für Bluetooth- und WLAN-Konnektivität gemeinsam nutzen, erkennen eine Datenüberlastung durch langsame Netzwerkgeschwindigkeiten oder eine schlechte Überwachungsleistung des Bewegungscontrollers.
* Ihre Motion-Controller erhalten regelmäßig neue Softwareupdates von Microsoft. Die Controller zeigen ein abwechselndes Muster von Blinklichtern, wenn sie diese neuen Softwareupdates erhalten. Dies ist normal. Warten Sie, bis das Softwareupgrade abgeschlossen ist, bevor Sie die Controller verwenden. Die Controller vibrieren, und ein konstantes Licht ersetzt das abwechselnde Flashmuster, wenn es fertig ist.
* Möglicherweise wird Ihnen mitgeteilt, dass Sie "Das Headset anstäuchen und den Fingerabdruck zum Teleportieren verwenden", bevor die Controller den Updatevorgang beenden. Die Controller sind erst sichtbar oder nutzbar, wenn das Update abgeschlossen ist. Die meisten Updates erfolgen innerhalb von zwei Minuten, aber Updates können bis zu 10 Minuten dauern. Warten Sie, bis das Update abgeschlossen ist, bevor Sie mit dem nächsten Schritt fortfahren.

## <a name="using-controllers"></a>Verwenden von Controllern

Hier erfahren Sie, wie Sie sich in Mixed Reality mit Motion-Controllern, einem Xbox-Gamepad oder einer Maus und Tastatur bewegen.

> [!TIP]
> Um die Eingabe zwischen Mixed Reality und Ihrem Desktop zu wechseln, drücken Sie Windows LOGO-TASTE **+ Y auf** ihrer PC-Tastatur.

![Schaltflächenzuordnung des Bewegungscontrollers](images/get_to_know_controllers.png)

|  Aufgabe  |  Bewegungscontroller  | Gamepad | Maus und Tastatur |
| --- | --- | --- | --- |
| Teleport | Drücken Sie den Stick nach vorn, und zeigen Sie den Controller an die Stelle, an der Sie wechseln möchten. Geben Sie den Thumbstick frei. | Drücken Sie den linken Fingerabdruck nach vorn, und suchen Sie, wohin Sie wechseln möchten. Geben Sie den Thumbstick frei. | Wählen Sie die rechte Schaltfläche aus, halten Sie sie gedrückt, und zeigen Sie dann mit der Maus, wohin Sie wechseln möchten. Lassen Sie die Schaltfläche los. |
| Select | Zeigen Sie auf den Controller, und ziehen Sie dann den Trigger, oder verwenden Sie das Touchpad. | Sehen Sie sich das Ziel an, und drücken Sie dann A. | Zeigen Sie mit der Maus, und klicken Sie dann mit der linken Maustaste. |
| Öffnen des Startmenüs | Klicken Sie auf **Windows** Schaltfläche. | Klicken Sie auf **die Xbox-Schaltfläche.** | Drücken Sie die **Windows-Taste.** |
| Verlassen einer immersiven App | Klicken Sie auf **Windows** Schaltfläche. Wählen Sie dann **im Menü "Schnelle Aktionen"** mixed reality home aus. | Klicken Sie auf **die Xbox-Schaltfläche.** Wählen Sie dann **im Menü für schnelle Aktionen die Mixed Reality-Startschaltfläche** aus. | Drücken Sie die Taste **Windows Logo. Wählen Sie dann im **angezeigten Menü** Schnellaktionen die Mixed Reality-Startschaltfläche aus. |
| Rotate | Bewegen Sie den Fingerabdruck nach links oder rechts. | Bewegen Sie den rechten Stick nach links oder rechts. | Nicht verfügbar. |
| Sichern | Bewegen Sie den Thumbstick rückwärts. | Bewegen Sie den linken Stick rückwärts. | Nicht verfügbar. |
| Walk | Drücken Sie den Daumenstick direkt nach unten, und drücken Sie ihn in die Richtung, in der Sie die Schritte unternehmen möchten. | Pushen Sie den linken Stick direkt nach unten, und drücken Sie ihn in die Richtung, in der Sie gehen möchten. | Nicht verfügbar. |
| Verschieben eines App-Fensters | Zeigen Sie auf die App-Leiste. Ziehen Sie den Trigger, und halten Sie ihn, um das Fenster zu greifen, und verwenden Sie dann den Controller, um es in eine beliebige Richtung zu verschieben. Geben Sie den Trigger frei. | Sehen Sie sich die App-Leiste an, und halten Sie dann A gedrückt, um das Fenster zu greifen. Verwenden Sie den linken Stick, um das Fenster nebeneinander oder nach oben oder unten zu verschieben. Verwenden Sie die Trigger, um sie näher und weiter zu verschieben. Geben Sie anschließend A frei. | Zeigen Sie mit der Maus auf die App-Leiste. Klicken Sie mit der linken Maustaste, halten Sie gedrückt, um das Fenster zu greifen, und bewegen Sie es dann mit der Maus nebeneinander oder nach oben und unten. Verwenden Sie das Scrollrad, um das Fenster näher oder weiter zu verschieben. Lassen Sie die Maustaste los. |
| Verschieben eines 3D-Objekts | Zeigen Sie auf das Objekt, und halten Sie dann den Trigger an, um es zu greifen. Verschieben Sie ihn mit dem Controller in eine beliebige Richtung, und geben Sie dann den Trigger frei. | Sehen Sie sich das Objekt an, und halten Sie dann A gedrückt, um es zu greifen. Verwenden Sie den linken Stick, um das Fenster nebeneinander oder nach oben oder unten zu verschieben. Verwenden Sie die Trigger, um sie näher und weiter zu verschieben. Geben Sie anschließend A frei. | Zeigen Sie mit der Maus auf das Objekt. Klicken Sie mit der linken Maustaste, halten Sie ihn gedrückt, und bewegen Sie ihn dann mit der Maus nebeneinander oder nach oben und unten.  Verwenden Sie das Scrollrad, um es näher oder weiter zu verschieben. Lassen Sie die Maustaste los. |
| Drehen oder Ändern der Größe eines App-Fensters | Zeigen Sie einen Controller an der App-Leiste und den anderen Controller an einer beliebigen Stelle im Fenster. Halten Sie beide Trigger gedrückt, und verschieben Sie dann die Controller zusammen oder getrennt, um die Größe zu ändern.  Um zu drehen, verschieben Sie einen Controller auf Sie und den anderen weg von Ihnen. Geben Sie die Trigger frei. | Wählen Sie auf der App-Leiste **Anpassen** aus. Sehen Sie sich eine Ecke des Anpassungsrahmens an, und drücken Sie dann A, um ihn auszuwählen. Verwenden Sie den linken Stick, um die Größe des Fensters zu ändern.  | Wählen Sie auf der App-Leiste **Anpassen** aus. Halten Sie eine Ecke des Anpassungsrahmens fest, und verwenden Sie dann die Maus, um die Größe des Fensters zu ändern. |
| Drehen oder Ändern der Größe eines 3D-Objekts | Zeigen Sie beide Controller auf das -Objekt. Halten Sie beide Trigger gedrückt, und verschieben Sie dann die Controller zusammen oder getrennt, um die Größe zu ändern.  Um zu drehen, verschieben Sie einen Controller auf Sie und den anderen weg von Ihnen. | Klicken Sie auf der App-Leiste auf **Anpassen,** und verschieben Sie das Objekt mithilfe des linken Sticks. | Klicken Sie auf der App-Leiste auf **Anpassen,** halten Sie das Objekt fest, halten Sie es fest, und bewegen Sie es mit der Maus. |
| Scrollen in einem App-Fenster | Ziehen Sie den Trigger, halten Sie ihn gedrückt, und verschieben Sie dann den Controller nach oben oder unten.  | Verwenden Sie das D-Pad. | Verwenden Sie das Mausrad. |
| Vergrößern oder Verkleinern im App-Fenster | Ziehen Sie beide Trigger, und verschieben Sie dann die Controller näher beieinander oder weiter auseinander. | Ziehen Sie den rechten Trigger, um ihn zu vergrößern, und den linken Trigger zum Verkleinern. | Verwenden Sie das Mausrad, während Sie die STRG-TASTE auf der Tastatur gedrückt halten. |
| Menü öffnen | Klicken Sie auf die Schaltfläche **Menü.** | Klicken Sie auf die Schaltfläche **Menü.** | Klicken Sie mit der rechten Maustaste. |

## <a name="what-do-the-vibrations-and-lights-mean"></a>Was bedeuten Schwingungen und Licht?

Ihr Controller kommuniziert Ihnen, was er tut, indem er seine LED-Beleuchtung vibriert und blinkt.

|  Wenn ihr Controller dies tut  |  Bedeutung |
| --- | --- |
| LEDs werden eingeschaltet, und der Controller vibriert einmal. | **Aktivieren** |  
| LEDs werden ausgeschaltet, und der Controller vibriert zweimal | **Ausschalten** |
| LEDs blinken alle 3 Sekunden | **Schlafen** |
| LEDs werden langsam geimt, und der Controller vibriert einmal | **Wechseln in den Kopplungsmodus** |
| Controller vibriert einmal | **Herstellen einer Verbindung oder Trennen von Ihrem PC** |
| LEDs sind hell erlichtet | **Controller, die per Headset nachverfolgt werden** |
| LEDs sind schwach ausgelichtet | **Controller, die nicht von Headsets nachverfolgt werden** |
| Controller vibriert dreimal und schaltet dann aus | **Kritischer Akkustand** |
| Die äußeren und inneren Ringe von LEDs blinken in einem abwechselnden Muster. | **Wird aktualisiert** |

## <a name="updating-motion-controllers-firmware"></a>Aktualisieren der Motion Controller-Firmware

* Wenn ein immersives Headset mit Ihrem PC verbunden ist und neue Controllerfirmware verfügbar ist, wird die Firmware automatisch an Ihre Motion Controller gepusht, wenn sie das nächste Mal eingeschaltet wird.
* Controllerfirmwareupdates werden mit einem Muster der Beleuchtung von LED-Quadranten in einer Kreisbewegung angezeigt und dauern 1-2 Minuten. Firmwareupdates können gelegentlich länger (bis zu 10 Minuten) dauern, was auf eine schlechte Bluetooth Konnektivität oder Funkinterferenz hindeuten kann.
* Falls das Firmwareupdate unterbrochen wird (Controller ausgeschaltet oder Akku ausgeschaltet), wird es beim nächsten Einschalten erneut versucht.
* Nach Abschluss des Firmwareupdates werden die Controller neu gestartet und die Verbindung wiederhergestellt.
* Beide Controller sollten jetzt verbunden sein. Navigieren Sie zu Mixed Reality-Portal, um den Status Ihrer Controller zu überprüfen.
* Überprüfen Sie, ob Ihre Controller ordnungsgemäß funktionieren:
  * Starten Sie **Mixed Reality-Portal,** und geben Sie Ihr Mixed Reality Home ein.
  * Verschieben Sie Ihre Controller, überprüfen Sie die Nachverfolgung, testen Sie Schaltflächen, und überprüfen Sie, ob die Teleportierung funktioniert. Wenn dies nicht dere ist, lesen Sie [den Abschnitt zur Problembehandlung für den Motion-Controller.](motion-controller-problems.md)

## <a name="faq"></a>Häufig gestellte Fragen

### <a name="how-can-i-check-battery-level"></a>Wie kann ich den Akkustand überprüfen?

*A: Der Akkustand befindet sich auf der umgekehrten Seite des virtuellen Modells, es gibt keinen Indikator für den physischen Akkustand. Warten Sie nach dem Einschalten des Controllers einige Sekunden, bis sich der Lesestand stabilisiert hat.*

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Können Sie diese Controller ohne Headset verwenden? Nur für die Eingabe "10/trigger/etc"?

*A: Nicht für universelle Windows Anwendungen*

## <a name="filing-motion-controller-feedbackbugs"></a>Einreichen von Feedback/Fehlern für den Motion Controller

Senden Sie uns feedback in Feedback-Hub mithilfe der Kategorie "Mixed Reality -> Input".

## <a name="see-also"></a>Weitere Informationen

- [HP-Controller in Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
- [HP-Controller in Unreal](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
- [Die Community fragen](https://answers.microsoft.com)
- [Wenden Sie sich an uns, um Support zu erhalten.](https://support.microsoft.com/contactus/)
- [Problembehandlung](troubleshooting-windows-mixed-reality.md)

Haben Sie Probleme mit Ihren Motion-Controllern? [Hilfe erhalten](motion-controller-problems.md)