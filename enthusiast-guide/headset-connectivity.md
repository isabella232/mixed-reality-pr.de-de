---
title: Häufig gestellte Fragen zur Headsetkonnektivität
description: Headsetkonnektivität Windows Mixed Reality Problembehandlung bei der Headsetkonnektivität, die über unsere Standarddokumentation zur Kundenunterstützung hinausgeht.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support, Headset
appliesto:
- Windows 10
ms.openlocfilehash: 2d46275fd86eedbe93a81bc97c156f29794e8c42
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143231"
---
# <a name="headset-connectivity-faqs"></a>Häufig gestellte Fragen zur Headsetkonnektivität

## <a name="my-headset-will-not-wake-up"></a>Mein Headset wird nicht aktiviert

Wenn Sich Ihr Headset im Ruhezustand befindet und das Klicken auf die Aktivierungsschaltfläche nicht funktioniert, starten Sie Ihren PC neu.

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Mein Computer verfügt nicht über einen PORTS und/oder Anzeigeport.

Möglicherweise müssen Sie einen Adapter verwenden. Hier [](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) finden Sie eine Liste der unterstützten Adapter.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Kann ich USB- oder USB- und/oder DisplayPort-Erweiterungskabel mit Windows Mixed Reality Headsets verwenden?

Windows Mixed Reality Headsets unterstützen die Verwendung von USB-, KABEL- oder DisplayPort-Erweiterungskabeln nicht offiziell. Wenn Sie diese Kabel verwenden, kann die Mixed Reality aufgrund von Abweichungen bei der Signalintegrität und der Busleistung zwischen dem USB-Controller Ihres PCs und dem Mixed Reality Headset beeinträchtigt werden. Versuchen Sie, Ihr Headset ohne Erweiterungskabel zu verwenden, wenn:

* Die Headsetanzeige zeigt kurz einen blauen Bildschirm an und wird dann schwarz und Mixed Reality-Portal wird während der Verwendung neu gestartet oder vollständig aufzählt.
* Die Audiowiedergabe des Headsets schneidet ab oder wird zu einer Störung.
* Das Headset flackert zwischen Schwarz und der richtigen Anzeige

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Ich erhalte den Fehler "Überprüfen des Anzeigekabels".

* Wenn Sie Adapter verwenden, um Ihr Headset mit Ihrem PC zu verbinden, stellen Sie sicher, dass sie Windows Mixed Reality unterstützen und 4K-fähig sind. Versuchen Sie außerdem, den Adapter mit dem PC zu verbinden, bevor Sie das Headset mit dem Adapter verbinden.
* Versuchen Sie es mit einem anderen PORTS oder DisplayPort-Port.
* Verbinden Sie Ihr Headset mit einem DisplayPort 1.2 oder höher oder MIT 1.4 oder höher. Stellen Sie sicher, dass der Port der erweiterten Grafikkarte auf Ihrem PC entspricht.
* Wenn Ihr PC sowohl über integrierte als auch diskrete Grafiken verfügt, stellen Sie sicher, dass Sie auf Ihrer aktiven Grafikkarte den PORT PCI oder DisplayPort verwenden. Dies kann bedeuten, dass Sie Ihre PC-Anzeige mit einem Nicht-PCI-Port verbinden müssen.
* Wenn Ihr PC sowohl integrierte als auch diskrete Grafiken hat und die integrierten Grafiken älter sind und keine Unterstützung Windows Mixed Reality, deaktivieren Sie die integrierte GPU.
* Verbinden Sie einen PC-Monitor mit dem PORT DES PC oder DisplayPort. Stellen Sie sicher, dass Ihre Grafiktreiber auf dem neuesten Stand sind. Laden Sie die Treiber direkt von AMD, Nvidia oder Intel herunter, und installieren Sie sie, da sie wahrscheinlich neuer als das sind, was in der Windows Update.
* Wenn Sie über einen externen Monitor verfügen, der an einen PORT vom Typ PROGRAMM angeschlossen ist, versuchen Sie, ihn stattdessen in einen DisplayPort zu verkabeln, und verwenden Sie den PORTS-Port für Ihr Headset.
* Stellen Sie sicher, dass Sie das ADAPTER-Kabel Ihres Headsets an einen "OUT"-Anschluss ihres PCs angeschlossen haben, nicht an einen PORT vom Typ "BEI in".
* Windows kann die Anzeigekabelverbindung möglicherweise nicht erkennen. Öffnen Sie die Geräte-Manager, und sehen Sie, ob das Headset unter "Monitore" aufgeführt ist. Wenn nicht, wählen Sie **Aktion > Auf Hardwareänderungen überprüfen aus.**

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Eine Meldung mit dem Text "Put on your headset" (Headset setzen), aber ich habe mein Headset ein.

Wenn Sie Ihr Headset anlasten, Windows Mixed Reality einige Sekunden zum erneuten Laden des Speicherplatzes benötigt. Wenn diese Nachricht nicht entfernt wird, stellen Sie sicher, dass der Schutzsticker aus dem Näherungssensor innerhalb des Headsets zwischen den Brillen entfernt wurde. Wenden Sie sich an ihren Headsethersteller, wenn das Problem weiterhin besteht.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Eine Meldung mit dem Text "Connect your headset" (Headset verbinden), aber ich habe mein Headset angeschlossen

- Stellen Sie sicher, dass die USB- und DISPLAYPORT-Kabel des Headsets mit den richtigen Anschlüssen auf Ihrem PC verbunden sind. So identifizieren Sie die richtigen Ports:

    - USB 3.0-Anschlüsse verfügen über ein spezielles Logo mit der Markierung "SS" (was auf "SuperSpeed" hinweist). Die Innenseite des Ports ist normalerweise blau, aber ältere USB 2.0-Anschlüsse sind in der Regel schwarz oder weiß im Inneren.
    - Wenn Ihr Computer über zwei PORTS VOM- oder DisplayPort-Port verfügt, verwenden Sie den Port, der eine Verbindung mit der Grafikkarte herstellt, und nicht mit der Hauptplatine des Computers. Es ist nicht immer offensichtlich, was ist, obwohl diskrete Ports sich häufig in einem Erweiterungsslot auf dem Computer befinden. Wenn Sie einen Port ausprobieren und er nicht funktioniert, versuchen Sie es mit dem anderen Port.

- Trennen Sie die USB- und DIE USB- oder DisplayPort-Kabel von Ihrem Headset, und schließen Sie sie an, um sicherzustellen, dass sie sicher verbunden sind. Wenn Sie das USB-Kabel anschließen, sollten Sie versuchen, beim Einfügen des USB-Kabels nicht anzuhalten.
- Probieren Sie einen extern betriebenen USB 3.0-Hub aus, wenn Sie eine partielle Enumeration des Headsets sehen, z. B. eine Reihe von USB-Geräten, die aufzählen, aber nichts unter "Mixed Reality Headsets" in Geräte-Manager.
- Wechseln Sie zur Website des Headsetherstellers, und aktualisieren Sie die Treiber und firmware für Ihr Headset.
- Verbinden Sie Ihr Headset mit einem anderen PC, und öffnen Sie Geräte-Manager. Auch wenn dieser PC nicht vollständig mit Windows Mixed Reality kompatibel ist, können Sie überprüfen, ob Ihr Headset aufzählt. Wenn Ihr Headset nicht auf mehreren PCs aufzählt, kann es zu einem Hardwareproblem kommen.

> [!NOTE]
> Für Surface-Benutzer: Frühere Versionen der Surface Dock- und Surface Book USB Hub-Firmwareupdatesoftware sind mit Mixed Reality Headsets nicht kompatibel. Wenn auf einem Surface-PC die Meldung "Connect your headset" (Headset verbinden) angezeigt wird, überprüfen Sie, ob ein Gerät den Fehler "Code 10: Das Gerät kann nicht gestartet werden" in Geräte-Manager meldet. Entfernen Sie in diesem Falle [den in Konflikt geratenen Treiber](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Dies sollte nur einmal erforderlich sein.

Hinweis für Windows 10-N-Benutzer: Wenn auf Ihrem PC Windows 10 N ausgeführt wird, wird in Geräte-Manager nach dem Anschließen ihres Mixed Reality Headsets der Fehler "Code 28: The install class isn't present or is invalid" (Code 28: Die Installationsklasse ist nicht vorhanden oder ungültig) angezeigt. N Editionen von Windows 10 werden von Windows Mixed Reality nicht unterstützt. Befolgen Sie diese [Anweisungen,](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) um weitere Informationen zu erhalten.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Eine Meldung mit dem Text "Check your USB cable" (USB-Kabel überprüfen) oder "Insufficient USB speed" (Nicht genügend USB-Geschwindigkeit)

* Stellen Sie sicher, dass Sie einen unterstützten USB 3.0-Anschluss auf Ihrem PC verwenden:

    * Stellen Sie sicher, dass das USB-Kabel Ihres Headsets immer angeschlossen ist.
    * Führen Sie [das Windows Mixed Reality-Portal](install-windows-mixed-reality.md#launch-mixed-reality-portal) aus, um sicherzustellen, dass der USB 3.0-Controller Ihres PCs unterstützt wird.
    * Verbinden Sie Ihr Headset mit den anderen USB 3.0-Anschlüssen auf Ihrem PC. Einige PCs verfügen über mehr als einen USB 3.0-Controller.
    * Trennen Sie vorübergehend alle USB-Geräte, die an Ihren PC angeschlossen sind, und verbinden Sie nur Ihr Headset.
    * Auf benutzerdefinierten PCs ist ein Port zwar als USB 3.0-Anschluss gekennzeichnet, kann aber mit einem USB 2.0-Controller verbunden sein. Wenn Ihr Headset verbunden ist, öffnen Sie Geräte-Manager, suchen Sie eines der Geräte, die über Ihr Headset aufzählt sind, und klicken Sie mit nur einem Klick darauf, und wechseln Sie dann zu Ansicht > Geräte nach **Verbindung.**
* Testen Sie Ihr Headset auf einem anderen PC. Wenn dieser andere PC nicht vollständig mit Windows Mixed Reality kompatibel ist, überprüfen Sie Geräte-Manager, ob die Meldung "Unzureichende USB-Geschwindigkeit" angezeigt wird. Wenn sie auf mehreren PCs nicht ordnungsgemäß aufzählt, kann Ihr Headset fehlerhaft sein.
* Entfernen Sie alle Extender oder Hubs zwischen dem Headset und dem Computer.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>Die Mixed Reality-Portal gestartet, nachdem ich mein Headset angeschlossen habe

Ihr Headset wurde aufgrund eines zugrunde liegenden Problems möglicherweise nicht ordnungsgemäß erkannt. Starten Sie Mixed Reality-Portal manuell, und suchen Sie nach fehlermeldungen, die angezeigt werden.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Mein Headset funktioniert nicht mehr, wenn mein PC in den Ruhe- oder Ruhezustandsmodus übergeht oder wenn mein PC mit angeschlossenen Headsets neu gestartet wird

1. Öffnen Geräte-Manager, und vergewissern Sie sich, dass Ihr Headset unter "Mixed Reality aufgeführt ist.
2. Wählen Sie Ihr Headset unter "Mixed Reality Geräte" aus, und vergewissern Sie sich, dass der Gerätestatus "Dieses Gerät funktioniert ordnungsgemäß" anzeigt.
3. Wenn der Fehler "Code 43" angezeigt wird, dass das Gerät nicht mehr funktioniert, oder wenn Ihr Headset nicht unter "Mixed Reality devices" (Mixed Reality-Geräte) aufgeführt ist, trennen Sie das USB-Kabel Ihres Headsets, und ziehen Sie es wieder an. Microsoft untersucht ein potenzielles Problem mit der Interoperabilität von Software/Treibern, das zu diesem Fehler führen kann. Dieses Problem betrifft eine kleine Anzahl von PCs und wird voraussichtlich in einem zukünftigen Update des Mixed Reality Headsettreibers behoben.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Mein Headset bewirkt, dass mein PC eine Fehlerüberprüfung (Blaubildschirm) generiert, wenn ich meinen PC in den Ruhezustand versetzt oder sich im Ruhezustand befindet.

Stellen Sie sicher, dass Sie den Treiber 10.0.19041.2034 oder neuer nutzen.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Der Headsettreiber wurde nicht automatisch installiert, wenn ich das Headset angeschlossen habe.

Auf neuen PCs oder PCs mit einer neu installierten Kopie von Windows 10 kann der Headsettreiber hinter anderen Windows-Updates in die Warteschlange eingereiht und möglicherweise nicht sofort installiert werden.

1. Wechseln **Sie** zu Start > Geräte-Manager , und suchen Sie unter "Mixed Reality Geräte" für Ihr Headset. Der Gerätestatus sollte darauf hinweisen, dass "Das Gerät ordnungsgemäß funktioniert".
2. Klicken Sie mit der rechten Maustaste auf das Gerät, und wählen Sie "Treiber aktualisieren" aus.

Wenn dies nicht funktioniert hat, versuchen Sie, den Treiber zu deinstallieren:

1. Wechseln **Sie** zu Start > Geräte-Manager , und suchen Sie unter "Mixed Reality Geräte" für Ihr Headset. Der Gerätestatus sollte darauf hinweisen, dass "Das Gerät ordnungsgemäß funktioniert".
2. Klicken Sie mit der rechten Maustaste auf das Gerät, und wählen Sie "Gerät deinstallieren" aus.
3. Aktivieren Sie im neuen Popupfenster, das angezeigt wird, das Kontrollkästchen "Treibersoftware für dieses Gerät löschen", und wählen Sie dann "Deinstallieren" aus.
4. Wenn dies abgeschlossen ist, trennen Sie das Headset von Ihrem PC, und schließen Sie es wieder an. Windows Update lädt jetzt einen neuen Treiber herunter und installiert diesen.

Hinweis: Wenn Sie über eine N Edition von Windows verfügen, müssen Sie zu einer regulären Edition von Windows 10 wechseln, um Windows Mixed Reality verwenden zu können.