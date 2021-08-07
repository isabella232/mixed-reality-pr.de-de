---
title: Häufig gestellte Fragen zur Headsetkonnektivität
description: Headsetkonnektivität Windows Mixed Reality Problembehandlung bei der Headsetkonnektivität, die über unsere Standarddokumentation für den Kundensupport hinausgeht.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support, Headset
appliesto:
- Windows 10
ms.openlocfilehash: ed8708d39953e79d445f3794d335d9a9451c9bf9fe8c2fca1feb792ee3f9b2a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189222"
---
# <a name="headset-connectivity-faqs"></a>Häufig gestellte Fragen zur Headsetkonnektivität

## <a name="my-headset-will-not-wake-up"></a>Mein Headset wird nicht aktiviert

Wenn Sich Ihr Headset im Ruhezustand befindet und das Klicken auf die Aktivierungsschaltfläche nicht funktioniert, starten Sie Ihren PC neu.

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Mein Computer verfügt nicht über einen PORTS und/oder Anzeigeport.

Möglicherweise müssen Sie einen Adapter verwenden. Eine Liste der unterstützten Adapter finden Sie [hier.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Kann ich USB- oder USB- und/oder DisplayPort-Erweiterungskabel mit Windows Mixed Reality Headsets verwenden?

Windows Mixed Reality Headsets unterstützen die Verwendung von USB-, CSV- oder DisplayPort-Erweiterungskabeln nicht offiziell. Wenn Sie diese Kabel verwenden, kann die Mixed Reality aufgrund von Abweichungen bei der Signalintegrität und der Busleistung zwischen dem USB-Controller Ihres PCs und dem Mixed Reality Headset beeinträchtigt werden. Versuchen Sie, Ihr Headset ohne Erweiterungskabel zu verwenden, wenn:

* Die Headsetanzeige zeigt kurz einen blauen Bildschirm an und wird dann schwarz und Mixed Reality-Portal wird während der Verwendung neu gestartet oder vollständig aufzählt.
* Die Audiowiedergabe des Headsets schneidet ab oder wird zu einer Störung.
* Das Headset flackert zwischen Schwarz und der richtigen Anzeige

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Ich erhalte den Fehler "Überprüfen des Anzeigekabels".

* Wenn Sie Adapter verwenden, um Ihr Headset mit Ihrem PC zu verbinden, stellen Sie sicher, dass sie Windows Mixed Reality unterstützen und 4K-fähig sind. Versuchen Sie außerdem, den Adapter mit dem PC zu verbinden, bevor Sie das Headset mit dem Adapter verbinden.
* Versuchen Sie es mit einem anderen PORTS oder DisplayPort-Port.
* Verbinden Ihr Headset an ein DisplayPort 1.2 oder höher oder an EIN DISPLAYPort 1.4 oder höher. Stellen Sie sicher, dass der Port der erweiterten Grafikkarte auf Ihrem PC entspricht.
* Wenn Ihr PC sowohl integrierte als auch diskrete Grafiken enthält, stellen Sie sicher, dass Sie den PORTS oder DisplayPort auf Ihrer aktiven Grafikkarte verwenden. Dies kann bedeuten, dass Sie Ihre PC-Anzeige mit einem Nicht-PCI-Port verbinden müssen.
* Wenn Ihr PC sowohl integrierte als auch diskrete Grafiken enthält und die integrierten Grafiken älter sind und Windows Mixed Reality nicht unterstützen, versuchen Sie, die integrierte GPU zu deaktivieren.
* Verbinden einen PC-Monitor an den PORTS VON IHREM PC oder DisplayPort an. Stellen Sie sicher, dass Ihre Grafiktreiber auf dem neuesten Stand sind. Laden Sie die Treiber direkt von AMD, Nvidia oder Intel herunter, und installieren Sie sie, da sie wahrscheinlich neuer als das sind, was in Windows Update veröffentlicht wird.
* Wenn Sie über einen externen Monitor verfügen, der an einen PORTS angeschlossen ist, versuchen Sie stattdessen, ihn an einen DisplayPort zu anschließen, und verwenden Sie den PORTS-Port für Ihr Headset.
* Stellen Sie sicher, dass Sie das KABEL-Kabel Ihres Headsets an einen "AUS"-Port auf Ihrem PC angeschlossen haben, nicht an einen "KABEL in"-Port.
* Windows kann die Anzeigekabelverbindung möglicherweise nicht erkennen. Öffnen Sie die Geräte-Manager, und prüfen Sie, ob das Headset unter "Monitore" aufgeführt ist. Falls nicht, wählen Sie **Aktion > Nach Hardwareänderungen suchen** aus.

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Die Meldung "Put on your headset", aber ich habe mein Headset eingeschaltet.

Wenn Sie Ihr Headset ansetzen, benötigen Windows Mixed Reality möglicherweise einige Sekunden, um Ihren Platz neu zu laden. Wenn diese Meldung nicht mehr angezeigt wird, stellen Sie sicher, dass der Schutzaufsatz vom Näherungssensor im Inneren des Headsets zwischen den Brillen entfernt wurde. Wenden Sie sich an den Hersteller Ihres Headsets, wenn das Problem weiterhin besteht.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>In einer Meldung wird "Verbinden Ihr Headset" angezeigt, aber ich habe mein Headset angeschlossen.

- Stellen Sie sicher, dass die USB- und DIE DISPLAYPort-Kabel des Headsets mit den richtigen Anschlüssen auf Ihrem PC verbunden sind. So identifizieren Sie die richtigen Ports:

    - USB 3.0-Anschlüsse verfügen über ein spezielles Logo mit der Markierung "SS" (was auf "SuperSpeed" hinweist). Die Innenseite des Ports ist normalerweise blau, aber ältere USB 2.0-Anschlüsse sind in der Regel schwarz oder weiß im Inneren.
    - Wenn Ihr Computer über zwei PORTS VOM- oder DisplayPort-Port verfügt, verwenden Sie den Port, der eine Verbindung mit der Grafikkarte herstellt, und nicht mit der Hauptplatine des Computers. Es ist nicht immer offensichtlich, was ist, obwohl diskrete Ports sich häufig in einem Erweiterungsslot auf dem Computer befinden. Wenn Sie einen Port ausprobieren und er nicht funktioniert, versuchen Sie es mit dem anderen Port.

- Trennen Sie die USB- und DIE USB- oder DisplayPort-Kabel von Ihrem Headset, und schließen Sie sie an, um sicherzustellen, dass sie sicher verbunden sind. Wenn Sie das USB-Kabel anschließen, sollten Sie versuchen, beim Einfügen des USB-Kabels nicht anzuhalten.
- Probieren Sie einen extern betriebenen USB 3.0-Hub aus, wenn Sie eine partielle Enumeration des Headsets sehen, z. B. eine Reihe von USB-Geräten, die aufzählen, aber nichts unter "Mixed Reality Headsets" in Geräte-Manager.
- Wechseln Sie zur Website des Headsetherstellers, und aktualisieren Sie die Treiber und firmware für Ihr Headset.
- Verbinden Sie Ihr Headset auf einen anderen PC, und öffnen Sie Geräte-Manager. Auch wenn dieser PC nicht vollständig mit Windows Mixed Reality kompatibel ist, können Sie überprüfen, ob Ihr Headset aufzählt. Wenn Ihr Headset nicht auf mehreren PCs aufzählt, kann es zu einem Hardwareproblem kommen.

> [!NOTE]
> Für Surface-Benutzer: Frühere Versionen der Surface Dock- und Surface Book USB Hub-Firmwareupdatesoftware sind nicht mit Mixed Reality Headsets kompatibel. Wenn auf einem Surface-PC die Meldung "Verbinden Ihrem Headset" angezeigt wird, überprüfen Sie, ob ein Gerät in Geräte-Manager den Fehler "Code 10: The device can't start" (Code 10: Das Gerät kann nicht gestartet werden) meldet. Entfernen Sie in diesem Falle [den in Konflikt geratenen Treiber](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Dies sollte nur einmal erforderlich sein.

Hinweis für Windows 10-N-Benutzer: Wenn auf Ihrem PC Windows 10 N ausgeführt wird, wird der Fehler "Code 28: The install class isn't present or is invalid" (Code 28: Die Installationsklasse ist nicht vorhanden oder ungültig) in Geräte-Manager angezeigt, nachdem Sie Ihr Mixed Reality Headset angeschlossen haben. N Editionen von Windows 10 werden von Windows Mixed Reality nicht unterstützt. Befolgen Sie diese [Anweisungen,](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) um weitere Informationen zu erhalten.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>In einer Meldung wird "Usb-Kabel überprüfen" oder "Unzureichende USB-Geschwindigkeit" angezeigt.

* Stellen Sie sicher, dass Sie einen unterstützten USB 3.0-Anschluss auf Ihrem PC verwenden:

    * Stellen Sie sicher, dass das USB-Kabel Ihres Headsets vollständig angeschlossen ist.
    * Führen Sie das [Windows Mixed Reality-Portal](install-windows-mixed-reality.md#launch-mixed-reality-portal) aus, um sicherzustellen, dass der USB 3.0-Controller Ihres PCs unterstützt wird.
    * Verbinden Ihr Headset an die anderen USB 3.0-Anschlüsse auf Ihrem PC. Einige PCs verfügen über mehrere USB 3.0-Controller.
    * Trennen Sie vorübergehend alle USB-Geräte, die an Ihren PC angeschlossen sind, und verbinden Sie nur Ihr Headset.
    * Auch wenn ein Port auf benutzerdefinierten PCs als USB 3.0-Anschluss gekennzeichnet werden kann, kann er mit einem USB 2.0-Controller verbunden sein. Wenn Ihr Headset verbunden ist, öffnen Sie Geräte-Manager, suchen Sie eines der Geräte, die über Ihr Headset aufzählt, und klicken Sie darauf, und navigieren Sie dann zu View > Devices by connection (Anzeigen **> Geräte nach Verbindung).**
* Testen Sie Ihr Headset auf einem anderen PC. Wenn dieser andere PC nicht vollständig mit Windows Mixed Reality kompatibel ist, überprüfen Sie Geräte-Manager, ob die Meldung "Unzureichende USB-Geschwindigkeit" angezeigt wird. Wenn es nicht ordnungsgemäß auf mehreren PCs aufzählt, ist Ihr Headset möglicherweise fehlerhaft.
* Entfernen Sie alle Extender oder Hubs zwischen dem Headset und dem Computer.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>Die Mixed Reality-Portal wurde nicht gestartet, nachdem ich mein Headset angeschlossen habe.

Ihr Headset wurde aufgrund eines zugrunde liegenden Problems möglicherweise nicht ordnungsgemäß erkannt. Starten Sie die Mixed Reality-Portal manuell, und suchen Sie nach angezeigten Fehlermeldungen.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Mein Headset funktioniert nicht mehr, wenn mein PC in den Standbymodus oder Ruhezustand wechselt oder wenn mein PC mit angeschlossenem Headset neu gestartet wird

1. Öffnen Sie Geräte-Manager, und vergewissern Sie sich, dass Ihr Headset unter "Mixed Reality Geräte" aufgeführt ist.
2. Wählen Sie unter "Mixed Reality Geräte" Ihr Headset aus, und vergewissern Sie sich, dass der Gerätestatus "Dieses Gerät funktioniert ordnungsgemäß" angibt.
3. Wenn der Fehler "Code 43" mit dem Hinweis angezeigt wird, dass das Gerät nicht mehr funktioniert, oder wenn Ihr Headset nicht unter "Mixed Reality Geräte" aufgeführt ist, trennen Sie das USB-Kabel Ihres Headsets, und ziehen Sie es erneut. Microsoft untersucht ein potenzielles Problem mit der Interoperabilität von Software/Treibern, das zu diesem Fehler führen kann. Dieses Problem betrifft eine kleine Anzahl von PCs und wird voraussichtlich in einem zukünftigen Update des Mixed Reality Headsettreibers behoben.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Mein Headset bewirkt, dass mein PC eine Fehlerüberprüfung (Blaubildschirm) generiert, wenn ich meinen PC in den Ruhezustand versetzt oder sich im Ruhezustand befindet.

Stellen Sie sicher, dass Sie den Treiber 10.0.19041.2034 oder neuer nutzen.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Der Headsettreiber wurde nicht automatisch installiert, wenn ich das Headset angeschlossen habe.

Auf neuen PCs oder PCs mit einer neu installierten Kopie von Windows 10 kann der Headsettreiber hinter anderen Windows Updates in die Warteschlange eingereiht und möglicherweise nicht sofort installiert werden.

1. Wechseln **Sie** zu Start > Geräte-Manager , und suchen Sie unter "Mixed Reality Geräte" für Ihr Headset. Der Gerätestatus sollte "Das Gerät funktioniert ordnungsgemäß" angeben.
2. Klicken Sie mit der rechten Maustaste auf das Gerät, und wählen Sie "Treiber aktualisieren" aus.

Wenn dies nicht funktioniert hat, versuchen Sie, den Treiber zu deinstallieren:

1. Wechseln **Sie** zu Start > Geräte-Manager , und suchen Sie unter "Mixed Reality Geräte" für Ihr Headset. Der Gerätestatus sollte "Das Gerät funktioniert ordnungsgemäß" angeben.
2. Klicken Sie mit der rechten Maustaste auf das Gerät, und wählen Sie "Gerät deinstallieren" aus.
3. Aktivieren Sie im neuen Popupfenster, das angezeigt wird, das Kontrollkästchen "Treibersoftware für dieses Gerät löschen", und wählen Sie dann "Deinstallieren" aus.
4. Wenn dies abgeschlossen ist, trennen Sie das Headset von Ihrem PC, und schließen Sie es wieder an. Windows Das Update lädt jetzt einen neuen Treiber herunter und installiert diesen.

Hinweis: Wenn Sie über eine N-Edition von Windows verfügen, müssen Sie zu einer regulären Edition von Windows 10 wechseln, um Windows Mixed Reality verwenden zu können.