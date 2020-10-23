---
title: Fragen zur Headset-Konnektivität
description: Erweiterte Windows Mixed Reality-Headset-Konnektivitätsprobleme, die über die Standard Support Dokumentation für Kunden
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, Headset
appliesto:
- Windows 10
ms.openlocfilehash: abdd0f04443e110f1eb19a31fb3d77e2f3bde929
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434552"
---
# <a name="headset-connectivity-faqs"></a>Fragen zur Headset-Konnektivität

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Der Computer verfügt nicht über einen HDMI-und/oder-anzeigeport.

Möglicherweise müssen Sie einen Adapter verwenden. [Hier](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) finden Sie eine Liste der unterstützten Adapter.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Kann ich USB-oder HDMI-und/oder DisplayPort-Erweiterungs Kabel mit Windows Mixed Reality-Headsets verwenden?
Windows Mixed Reality-Headsets unterstützen nicht offiziell die Verwendung von USB-, HDMI-oder DisplayPort-Erweiterungs Kabeln. Die Verwendung dieser Kabel kann sich aufgrund von Abweichungen in der resultierenden Signalintegrität und der Busleistung zwischen dem USB-Controller des PCs und dem Mixed Reality-Headset erheblich auf die gemischte Realität auswirken. Wenn in der Headset-Anzeige kurz ein blauer Bildschirm angezeigt wird, wird das schwarze und gemischte Reality-Portal neu gestartet bzw. die Enumeration während der Verwendung vollständig deaktiviert, oder wenn sich das Headset-audiobild ausschneidet oder es in eine glitplizierung wechselt, oder wenn das Headset zwischen schwarz und der richtigen Anzeige flistet, versuchen Sie, Ihr Headset ohne Erweiterungs Kabel

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Ich erhalte den Fehler "Ihr Anzeige Kabel überprüfen".

* Wenn Sie einen Adapter zum Verbinden Ihres Headsets mit Ihrem PC verwenden, stellen Sie sicher, dass Sie Windows Mixed Reality unterstützen (der Adapter muss 4K-fähig sein). Versuchen Sie außerdem, den Adapter mit dem PC zu verbinden, bevor Sie das Headset mit dem Adapter verbinden.
* Versuchen Sie, einen anderen Port für den HDMI-und/oder DisplayPort zu verwenden.
* Stellen Sie eine Verbindung zwischen Ihrem Headset und einem Display Port 1,2 oder höher bzw. "HDMI 1,4" oder höher her. Stellen Sie sicher, dass der Port mit der fortschrittlichsten Grafikkarte auf Ihrem PC übereinstimmt.
* Wenn Ihr PC über integrierte und diskrete Grafiken verfügt, stellen Sie sicher, dass Sie den Port "HDMI" und/oder "Display Port" auf Ihrer aktiven Grafikkarte verwenden. Dies bedeutet möglicherweise, dass Sie Ihre PC-Anzeige mit einem nicht--HDMI-Port verbinden müssen.
* Wenn Ihr PC über integrierte und diskrete Grafiken verfügt und die integrierte Grafik älter ist und Windows Mixed Reality nicht unterstützt, versuchen Sie, die integrierte GPU zu deaktivieren.
* Verbinden Sie einen PC-Monitor mit dem Port "HDMI" und/oder "Display Port" Ihres PCs. Stellen Sie sicher, dass Ihre Grafiktreiber auf dem neuesten Stand sind. Laden Sie die von AMD, NVIDIA oder Intel direkt herunter, und installieren Sie Sie, da Sie wahrscheinlich neuer als die in Windows Update veröffentlichten sind.
* Wenn Sie einen externen Monitor an einem HDMI-Port angeschlossen haben, versuchen Sie stattdessen, ihn an einen DisplayPort zu binden, und verwenden Sie den HDMI-Port für das Headset.
* Stellen Sie sicher, dass Sie das HDMI-Kabel Ihres Headsets an einen "HDMI"-Port auf Ihrem PC und nicht an den Port "HDMI in" angeschlossen haben.
* Die Anzeige Kabelverbindung kann möglicherweise nicht von Windows erkannt werden. Öffnen Sie die Geräte-Manager, und überprüfen Sie, ob das Headset unter "Monitore" aufgeführt ist. Wenn dies nicht der gibt, wählen Sie **Aktion > auf Hardwareänderungen über**prüfen. 

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Eine Meldung besagt "Put on your Headset", aber ich habe mein Headset

Wenn Sie Ihr Headset einfügen, benötigt Windows Mixed Reality möglicherweise einige Sekunden, um den Speicherplatz neu zu laden. Wenn diese Nachricht nicht entfernt wird, stellen Sie sicher, dass der Schutz Aufkleber aus dem near-Sensor entfernt wurde, der sich auf der Innenseite des Headsets zwischen den objektiven befindet. Wenn das Problem hierdurch nicht behoben wird, wenden Sie sich an Ihren Headset-Hersteller.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Eine Meldung besagt "Connect your Headset", aber ich habe mein Headset angeschlossen.

1. Stellen Sie sicher, dass die Kabel-und/oder Display Port-Kabel des Headsets mit den richtigen Ports auf Ihrem PC verbunden sind. Im folgenden wird erläutert, wie die richtigen Ports identifiziert werden:
    * USB 3,0-Ports verfügen über ein spezielles Logo mit der Markierung "SS" ("SuperSpeed"). Der innere Bereich des Ports ist normalerweise blau, während ältere USB 2,0-Ports in der Regel Schwarz oder weiß im Inneren sind.
    * Wenn Ihr Computer über zwei-und/oder DisplayPort-Ports verfügt, verwenden Sie den Computer, der eine Verbindung mit der Grafikkarte herstellt, nicht die Hauptplatine des Computers. Es ist nicht immer offensichtlich, welches ist, obwohl sich diskrete Ports häufig in einem Erweiterungs Slot auf dem Computer befinden. Wenn Sie einen Port ausprobieren und dies nicht funktioniert, versuchen Sie es noch mal.
2. Deinstalportieren Sie die USB-und die-und-oder DisplayPort-Kabel von Ihrem Headset, um sicherzustellen, dass Sie sicher verbunden sind. Wenn Sie das USB-Kabel einfügen, versuchen Sie nicht, während des Einfügens des USB-Kabels anzuhalten.
3. Öffnen Sie Geräte-Manager, und vergewissern Sie sich, dass Ihr Headset unter "Mixed Reality Devices" aufgeführt ist. Wenn Sie Ihr Headset auswählen, sollte der Gerätestatus "dieses Gerät funktioniert ordnungsgemäß" lauten. Gelbe Ausrufezeichen auf Geräten in Geräte-Manager Fehler anzeigen.
    * Wenn "hololens Sensors" mit einem gelben Ausrufezeichen in Geräte-Manager aufgeführt ist, wählen Sie das Gerät aus. Wenn "Code 10: die Treiber für dieses Gerät sind nicht installiert" angezeigt wird. Es sind keine kompatiblen Treiber für dieses Gerät vorhanden ", [Installieren Sie den Headset-Treiber manuell](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset).
    * Wenn Sie auf Ihrem PC mehrere gemischte Reality-Headsets verwenden und den Mixed Reality-Headset-Treiber manuell installiert haben, gilt die manuelle Treiber Aktualisierung möglicherweise nur für das mit dem Zeitpunkt verbundene Headset, nicht aber für andere Headsets. In diesem Fall wird "Code 31: dieses Gerät funktioniert nicht ordnungsgemäß ausgeführt, da die für dieses Gerät erforderlichen Treiber nicht geladen werden können. (Code 31). Die angeforderte ALPC-Nachricht ist in Geräte-Manager nicht mehr verfügbar. Klicken Sie in **Geräte-Manager > Mixed Reality-Geräte**mit der rechten Maustaste auf Ihr Headset, und wählen Sie "Gerät deinstallieren" aus. Wählen Sie "OK" aus, um das Headset zu bestätigen und dann wieder zu entfernen.
4. Wenn Sie die partielle Enumeration des Headsets sehen (eine Reihe von USB-Geräten aufzählen, aber nichts unter "Mixed Reality-Headsets" in Geräte-Manager), testen Sie einen extern betriebenen USB 3,0-Hub.
5. Wechseln Sie zur Website des Headset-Herstellers, und aktualisieren Sie die Treiber und die Firmware für Ihr Headset.
6. Verbinden Sie Ihr Headset mit einem anderen PC, und öffnen Sie Geräte-Manager. Auch wenn dieser PC nicht vollständig mit Windows Mixed Reality kompatibel ist, können Sie überprüfen, ob Ihr Headset aufzählt. Wenn Ihr Headset nicht auf mehreren PCs aufzählt, kann ein Hardwareproblem auftreten.

Hinweis für Surface-Benutzer: frühere Versionen der USB-Hub-Firmwareupdate-Software für Surface-Sticks sind nicht mit Mixed Reality-Headsets kompatibel. Wenn Sie die Meldung "Connect your Headset on a Surface PC" erhalten, überprüfen Sie, ob von Geräten der Fehler "Code 10: das Gerät kann nicht gestartet werden" in Geräte-Manager angezeigt wird. Entfernen Sie in [diesem Fall den in Konflikt stehenden Treiber](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Dies ist nur einmal erforderlich.

Hinweis für Windows 10 n-Benutzer: Wenn auf Ihrem PC Windows 10 n ausgeführt wird, wird die Fehlermeldung "Code 28: die Installationsklasse ist nicht vorhanden oder ungültig" angezeigt, nachdem Sie Ihr Mixed Reality-Headset in Geräte-Manager. N Editionen von Windows 10 werden von der gemischten Realität von Windows nicht unterstützt. Befolgen Sie diese [Anweisungen](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) , um weitere Informationen zu finden.

Diese Informationen werden auch in einem [Flussdiagramm zur Problem](headset-connectivity-flowchart.md)Behandlung angezeigt.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Eine Meldung lautet: "Überprüfen Sie das USB-Kabel" oder "unzureichende USB-Geschwindigkeit".

* Stellen Sie sicher, dass Sie einen unterstützten USB 3,0-Port auf Ihrem PC verwenden:
    * Stellen Sie sicher, dass das USB-Kabel Ihres Headsets vollständig angeschlossen ist.
    * Führen Sie das [Windows Mixed Reality-Portal](install-windows-mixed-reality.md#launch-mixed-reality-portal) aus, um sicherzustellen, dass der USB 3,0-Controller Ihres PCs unterstützt wird
    * Verbinden Sie Ihr Headset mit den anderen USB 3,0-Ports auf Ihrem PC. Einige PCs verfügen über mehr als einen USB 3,0-Controller.
    * Trennen Sie vorübergehend alle USB-Geräte, die mit dem PC verbunden sind, und verbinden Sie Ihr Headset.
    * Auf benutzerdefinierten PCs, auch wenn ein Port als USB 3,0-Port gekennzeichnet sein kann, ist er möglicherweise mit einem USB 2,0-Controller verbunden. Öffnen Sie bei geöffneter Verbindung Geräte-Manager, suchen Sie das Gerät, und klicken Sie mit der Maustaste auf eines der Geräte, die in Ihrem Headset aufgelistet sind. wechseln Sie dann zu **anzeigen > Geräte nach Verbindung**
* Testen Sie Ihr Headset auf einem anderen PC. Wenn der andere PC nicht vollständig mit Windows Mixed Reality kompatibel ist, checken Sie Geräte-Manager ein, um festzustellen, ob die Meldung "unzureichende USB-Geschwindigkeit" angezeigt wird. Wenn Sie auf mehreren PCs nicht ordnungsgemäß aufgelistet wird, könnte das Headset fehlerhaft sein.
* Entfernen Sie alle Extender oder Hubs zwischen dem Headset und dem Computer.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>Das Mixed Reality-Portal konnte nicht gestartet werden, nachdem ich mein Headset angeschlossen habe.

Das Headset wurde aufgrund eines zugrunde liegenden Problems möglicherweise nicht ordnungsgemäß erkannt. Starten Sie das Mixed Reality-Portal manuell, und suchen Sie nach Fehlermeldungen, die angezeigt werden. 

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Mein Headset funktioniert nicht mehr, wenn mein PC in den Standbymodus oder den Ruhe Zustands Modus wechselt oder wenn ich meinen PC mit dem angefügten Headset neu startet.

1. Öffnen Sie Geräte-Manager, und vergewissern Sie sich, dass Ihr Headset unter "Mixed Reality Devices" aufgeführt ist.
2. Wählen Sie unter "gemischte Reality-Geräte" Ihr Headset aus, und vergewissern Sie sich, dass der Gerätestatus "dieses Gerät funktioniert ordnungsgemäß" angezeigt wird.
3. Wenn die Fehlermeldung "Code 43" mit dem Hinweis angezeigt wird, dass das Gerät nicht mehr funktioniert, oder wenn Ihr Headset nicht unter "gemischte Reality-Geräte" aufgeführt ist, lösen Sie das USB-Kabel Ihres Headsets aus, und geben Sie es erneut ein. Microsoft untersucht ein potenzielles Problem mit der Software-/treiberinteroperabilität, das möglicherweise zu diesem Fehler führt. Dieses Problem wirkt sich auf eine kleine Anzahl von PCs aus, und es wird erwartet, dass Sie in einem zukünftigen Update des Mixed Reality-Headset-Treibers aufgelöst werden.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Mein Headset bewirkt, dass mein PC eine Fehlerüberprüfung (blauer Bildschirm) generiert, wenn der PC in den Standbymodus versetzt wird oder sich im Ruhezustand befindet.
Stellen Sie sicher, dass Sie sich auf dem 10.0.18362.1062-Treiber oder neuer befinden.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Der Headset-Treiber wurde nicht automatisch installiert, als ich das Headset angeschlossen habe.

Auf neuen PCs oder PCs mit einer neu installierten Kopie von Windows 10 könnte der Headset-Treiber hinter anderen Windows-Updates in die Warteschlange eingereiht werden und wird möglicherweise nicht sofort installiert. So installieren Sie es manuell:
1. Wechseln Sie zu **Start > Geräte-Manager** , und suchen Sie unter "andere Geräte" nach einem Gerät "hololens Sensors" mit einem gelben Ausrufezeichen: ![ Ansicht der Geräte-Manager hololens-Sensoren](images/hololenssensors.png)
2. Klicken Sie mit der rechten Maustaste auf das Gerät, und wählen Sie Eigenschaften Wenn die Eigenschaften des Geräts "die Treiber für dieses Gerät sind nicht installiert (Code 28)" gelesen werden, schließen Sie das Fenster, und fahren Sie fort. Wenn eine andere Meldung vorhanden ist, führen Sie die Schritte zur Problembehandlung auf den restlichen Seiten der Seite aus.
![Code 28 von hololens-Sensoren in Geräte-Manager](images/code28.png)
3. Klicken Sie erneut mit der rechten Maustaste auf das Gerät, und wählen Sie "Treiber aktualisieren...". und dann nach der Aktualisierung des Geräts "automatisch nach aktualisierter Treibersoftware suchen" angezeigt wird, wird Ihr Headset in Geräte-Manager unter "gemischte Reality-Geräte" angezeigt: das ![ Gerät mit gemischter Realität wird in Geräte-Manager](images/mixedrealitydevices.png)

Wenn die manuelle Installation nicht funktioniert oder Sie den Treiber nicht unter anderen Geräten finden, müssen Sie den vorhandenen Treiber wahrscheinlich deinstallieren und neu installieren. Gehen Sie dafür folgendermaßen vor:
1. Wechseln Sie zu **Start > Geräte-Manager** , und suchen Sie unter "gemischte Reality-Geräte" nach Ihrem Headset. Der Gerätestatus sollte darauf hinweisen, dass das Gerät ordnungsgemäß funktioniert.
2. Klicken Sie mit der rechten Maustaste auf das Gerät, und wählen Sie "Gerät deinstallieren".
3. Aktivieren Sie im angezeigten Popup Fenster das Kontrollkästchen "Treibersoftware für dieses Gerät löschen", und wählen Sie dann "deinstallieren" aus.
4. Wenn dies abgeschlossen ist, lösen Sie das Headset von Ihrem PC aus, und binden Sie es wieder ein. Windows Update wird jetzt ein neuer Treiber heruntergeladen und installiert.

Hinweis: Wenn Sie über eine N-Edition von Windows verfügen, müssen Sie zu einer regulären Edition von Windows 10 wechseln, damit Windows Mixed Reality verwendet werden kann.


