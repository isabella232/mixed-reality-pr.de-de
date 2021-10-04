---
title: Häufig gestellte Fragen zur Headsetkonnektivität
description: Problembehandlung Windows Mixed Reality Headsetkonnektivität mit Headsetkonnektivität, die über unsere Standarddokumentation für den Kundensupport hinausgeht.
author: qianwen
ms.author: v-qianwen
ms.date: 09/30/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support, Headset
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 47c726c5beeac0463fe4286bd7a949e4e4d4cc45
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436612"
---
# <a name="headset-connectivity-faqs"></a>Häufig gestellte Fragen zur Headsetkonnektivität

## <a name="my-headset-will-not-wake-up"></a>Mein Headset wird nicht reaktivieren

Wenn Ihr Headset imAktiv ist und das Klicken auf die Aktivierungsschaltfläche nicht funktioniert, starten Sie Ihren PC neu.

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Mein Computer verfügt nicht über einen DISPLAY- und/oder Display-Port.

Möglicherweise müssen Sie einen Adapter verwenden. Hier [finden](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) Sie eine Liste der unterstützten Adapter.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Kann ich USB- oder SPEED- und/oder DisplayPort-Erweiterungskabel mit Windows Mixed Reality Headsets verwenden?

Windows Mixed Reality Headsets unterstützen die Verwendung von USB-, DISPLAYPORT- oder DisplayPort-Erweiterungskabeln nicht offiziell. Wenn Sie diese Kabel verwenden, kann die Mixed Reality-Erfahrung aufgrund von Abweichungen bei der Signalintegrität und der Busleistung zwischen dem USB-Controller Ihres PCs und dem Mixed Reality beeinträchtigt werden. Versuchen Sie, Ihr Headset ohne Erweiterungskabel zu verwenden, wenn:

* Die Headsetanzeige zeigt kurz einen blauen Bildschirm an und wird dann schwarz und Mixed Reality-Portal während der Verwendung neu gestartet oder vollständig aufzählt.
* Das Headsetaudio schneidet aus oder wird störungsig
* Das Headset flackert zwischen schwarzer und korrekter Anzeige

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Ich habe den Fehler "Überprüfen Des Anzeigekabels".

* Wenn Sie Adapter verwenden, um Ihr Headset mit Ihrem PC zu verbinden, stellen Sie sicher, dass diese Windows Mixed Reality und 4K-fähig sind. Versuchen Sie außerdem, den Adapter mit dem PC zu verbinden, bevor Sie das Headset mit dem Adapter verbinden.
* Versuchen Sie, einen anderen DISPLAY- oder DisplayPort-Port zu verwenden.
* Verbinden Ihres Headsets auf einen DisplayPort 1.2 oder höher oder AUF 1.4 oder höher. Stellen Sie sicher, dass der Port der erweiterten Grafikkarte auf Ihrem PC entspricht.
* Wenn auf Ihrem PC sowohl integrierte als auch diskrete Grafiken enthalten sind, stellen Sie sicher, dass Sie auf Ihrer aktiven Grafikkarte den PORT bzw. displayport verwenden. Dies kann bedeuten, dass Sie Ihre PC-Anzeige mit einem Nicht-PCI-Port verbinden müssen.
* Wenn Ihr PC sowohl integrierte als auch diskrete Grafiken hat und die integrierten Grafiken älter sind und keine Unterstützung Windows Mixed Reality, deaktivieren Sie die integrierte GPU.
* Verbinden Sie einen PC-Monitor an den PORT DES PC oder displayport an. Stellen Sie sicher, dass Ihre Grafiktreiber auf dem neuesten Stand sind. Laden Sie die Treiber direkt von AMD, Nvidia oder Intel herunter, und installieren Sie sie, da sie wahrscheinlich neuer sind als das, was in Windows Update veröffentlicht wird.
* Wenn Sie über einen externen Monitor verfügen, der an einen PORT vom Typ PROGRAMM angeschlossen ist, versuchen Sie, ihn stattdessen in einen DisplayPort zu verkabeln, und verwenden Sie den PORTS-Port für Ihr Headset.
* Stellen Sie sicher, dass Sie das ADAPTER-Kabel Ihres Headsets an einen "OUT"-Anschluss ihres PCs angeschlossen haben, nicht an einen PORT vom Typ "BEI in".
* Windows kann die Anzeigekabelverbindung möglicherweise nicht erkennen. Öffnen Sie die Geräte-Manager, und sehen Sie, ob das Headset unter "Monitore" aufgeführt ist. Falls nicht, wählen Sie **Aktion > Auf Hardwareänderungen überprüfen aus.**

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Eine Meldung mit dem Text "Put on your headset" (Headset setzen), aber ich habe mein Headset ein.

Wenn Sie Ihr Headset anstürden, Windows Mixed Reality einige Sekunden zum erneuten Laden des Speicherplatzes benötigt. Wenn diese Nachricht nicht entfernt wird, stellen Sie sicher, dass der Schutzsticker aus dem Näherungssensor innerhalb des Headsets zwischen den Brillen entfernt wurde. Wenden Sie sich an ihren Headsethersteller, wenn das Problem weiterhin besteht.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Eine Meldung mit dem Verbinden Headset, aber ich habe mein Headset angeschlossen.

- Stellen Sie sicher, dass die USB- und DISPLAYPORT-Kabel des Headsets mit den richtigen Anschlüssen auf Ihrem PC verbunden sind. So identifizieren Sie die richtigen Ports:

    - USB 3.0-Anschlüsse verfügen über ein spezielles Logo mit einer "SS"-Markierung (die auf "SuperSpeed" hinweist). Der Anschluss ist normalerweise blau, ältere USB 2.0-Anschlüsse sind jedoch in der Regel schwarz oder weiß.
    - Wenn Ihr Computer über zwei TCP- oder DisplayPort-Ports verfügt, verwenden Sie den Port, der eine Verbindung mit der Grafikkarte herstellt, nicht die Hauptplatine des Computers. Es ist nicht immer offensichtlich, was ist, obwohl diskrete Ports sich häufig in einem Erweiterungsslot auf dem Computer befinden. Wenn Sie einen Port ausprobieren und er nicht funktioniert, versuchen Sie es mit dem anderen Port.

- Trennen Sie die USB- und DISPLAYPORT-Kabel von Ihrem Headset, und schließen Sie sie an, um sicherzustellen, dass sie sicher verbunden sind. Wenn Sie das USB-Kabel anschließen, sollten Sie versuchen, beim Einlegen des USB-Kabels nicht anzuhalten.
- Testen Sie einen extern betriebenen USB 3.0-Hub, wenn sie eine partielle Enumeration des Headsets sehen, z. B. eine Reihe von USB-Geräten, die aufzählen, aber nichts unter "Mixed Reality Headsets" in Geräte-Manager.
- Wechseln Sie zur Website des Headsetherstellers, und aktualisieren Sie die Treiber und firmware für Ihr Headset.
- Verbinden Sie Ihr Headset auf einen anderen PC, und öffnen Sie Geräte-Manager. Auch wenn dieser PC nicht vollständig kompatibel mit Windows Mixed Reality ist, können Sie überprüfen, ob Ihr Headset aufzählt. Wenn Ihr Headset nicht auf mehreren PCs aufzählt, kann es ein Hardwareproblem geben.

> [!NOTE]
> Für Surface-Benutzer: Frühere Versionen der Surface Dock- und Surface Book-Firmwareupdatesoftware sind nicht kompatibel mit Mixed Reality Headsets. Wenn Sie auf einem Surface-PC die Meldung "Verbinden Your Headset" erhalten, überprüfen Sie, ob geräte einen Fehler "Code 10: The device can't start" (Code 10: Das Gerät kann nicht gestartet werden) in Geräte-Manager. Wenn ja, [entfernen Sie den in Konflikt stehenden Treiber](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Sie sollten dies nur einmal tun.

Hinweis für Windows 10-N- und Windows 11-N-Benutzer: Wenn auf Ihrem PC Windows 10-N oder Windows 11-N ausgeführt wird, wird in Geräte-Manager nach dem Anschließen ihres Mixed Reality-Headsets der Fehler "Code 28: Die Installationsklasse ist nicht vorhanden oder ungültig" angezeigt. N Editionen von Windows 10 und Windows 11 werden von der Windows Mixed Reality. Befolgen Sie [diese Anweisungen,](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) um weitere Informationen zu erhalten.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Eine Meldung mit dem Text "Check your USB cable" (USB-Kabel überprüfen) oder "Insufficient USB speed" (Nicht genügend USB-Geschwindigkeit)

* Stellen Sie sicher, dass Sie einen unterstützten USB 3.0-Anschluss auf Ihrem PC verwenden:

    * Stellen Sie sicher, dass das USB-Kabel Ihres Headsets immer angeschlossen ist.
    * Führen Sie [das Windows Mixed Reality-Portal](install-windows-mixed-reality.md#launch-mixed-reality-portal) aus, um sicherzustellen, dass der USB 3.0-Controller Ihres PCs unterstützt wird.
    * Verbinden Ihr Headset an die anderen USB 3.0-Anschlüsse auf Ihrem PC an. Einige PCs verfügen über mehr als einen USB 3.0-Controller.
    * Trennen Sie vorübergehend alle USB-Geräte, die an Ihren PC angeschlossen sind, und verbinden Sie nur Ihr Headset.
    * Auf benutzerdefinierten PCs ist ein Port zwar als USB 3.0-Anschluss gekennzeichnet, kann aber mit einem USB 2.0-Controller verbunden sein. Wenn Ihr Headset verbunden ist, öffnen Sie Geräte-Manager, suchen Sie eines der Geräte, die über Ihr Headset aufzählt sind, und klicken Sie mit nur einem Klick darauf, und wechseln Sie dann zu Ansicht > **Geräte nach Verbindung.**
* Testen Sie Ihr Headset auf einem anderen PC. Wenn dieser andere PC nicht vollständig mit Windows Mixed Reality kompatibel ist, überprüfen Sie Geräte-Manager, ob die Meldung "Unzureichende USB-Geschwindigkeit" angezeigt wird. Wenn sie auf mehreren PCs nicht ordnungsgemäß aufzählt, kann Ihr Headset fehlerhaft sein.
* Entfernen Sie alle Extender oder Hubs zwischen dem Headset und dem Computer.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>Der Mixed Reality-Portal wurde nicht gestartet, nachdem ich mein Headset angeschlossen habe.

Ihr Headset wurde aufgrund eines zugrunde liegenden Problems möglicherweise nicht ordnungsgemäß erkannt. Starten Sie Mixed Reality-Portal manuell, und suchen Sie nach allen angezeigten Fehlermeldungen.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Mein Headset funktioniert nicht mehr, wenn mein PC in den Ruhe- oder Ruhezustandsmodus übergeht oder wenn mein PC mit angeschlossenen Headsets neu gestartet wird

1. Öffnen Geräte-Manager, und vergewissern Sie sich, dass Ihr Headset unter "Mixed Reality aufgeführt ist.
2. Wählen Sie Ihr Headset unter "Mixed Reality Geräte" aus, und vergewissern Sie sich, dass der Gerätestatus "Dieses Gerät funktioniert ordnungsgemäß" angibt.
3. Wenn der Fehler "Code 43" angezeigt wird, dass das Gerät nicht mehr funktioniert, oder wenn Ihr Headset nicht unter "Mixed Reality devices" (Mixed Reality-Geräte) aufgeführt ist, trennen Sie das USB-Kabel Ihres Headsets, und ziehen Sie es wieder ein. Microsoft untersucht ein potenzielles Software-/Treiber-Interoperabilitätsproblem, das zu diesem Fehler führen kann. Dieses Problem betrifft eine kleine Anzahl von PCs und wird voraussichtlich in einem zukünftigen Update des Mixed Reality-Headsettreibers behoben.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Mein Headset bewirkt, dass mein PC eine Fehlerüberprüfung (blauer Bildschirm) generiert, wenn ich meinen PC in den Ruhezustand oder im Ruhezustandsmodus einsetze.

Stellen Sie sicher, dass Sie den Treiber 10.0.19041.2034 oder neuer haben.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Der Headsettreiber wurde nicht automatisch installiert, wenn ich das Headset angeschlossen habe.

Auf neuen PCs oder PCs mit einer neu installierten Kopie von Windows 10 oder Windows 11 könnte der Headset-Treiber hinter anderen Windows-Updates in die Warteschlange gestellt werden und nicht sofort installiert werden.

1. Wechseln Sie **zu Start > Geräte-Manager,** und suchen Sie unter "Mixed Reality Geräte" für Ihr Headset. Der Gerätestatus sollte angeben, dass das Gerät ordnungsgemäß funktioniert.
2. Klicken Sie mit der rechten Maustaste auf das Gerät, und wählen Sie "Treiber aktualisieren" aus.

Wenn dies nicht funktioniert hat, versuchen Sie, den Treiber zu deinstallieren:

1. Wechseln Sie **zu Start > Geräte-Manager,** und suchen Sie unter "Mixed Reality Geräte" für Ihr Headset. Der Gerätestatus sollte angeben, dass das Gerät ordnungsgemäß funktioniert.
2. Klicken Sie mit der rechten Maustaste auf das Gerät, und wählen Sie "Gerät deinstallieren" aus.
3. Aktivieren Sie im neuen Popupfenster, das angezeigt wird, das Kontrollkästchen "Treibersoftware für dieses Gerät löschen", und wählen Sie dann "Deinstallieren" aus.
4. Wenn dies abgeschlossen ist, trennen Sie das Headset von Ihrem PC, und schließen Sie es wieder ein. Windows Das Update wird jetzt einen neuen Treiber herunterladen und installieren.

Hinweis: Wenn Sie über eine N Edition von Windows verfügen, müssen Sie zu einer regulären Edition von Windows 10 oder Windows 11 wechseln, um Windows Mixed Reality.