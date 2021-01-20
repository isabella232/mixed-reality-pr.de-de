---
title: FAQs anzeigen FAQs
description: Anzeigen der Windows Mixed Reality-Problembehandlung für Probleme mit der Headset-Anzeige
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support
appliesto:
- Windows 10
ms.openlocfilehash: f448cafe3d0952ada63d545e44b58001779a1470
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580510"
---
# <a name="headset-display-faqs"></a>FAQs anzeigen FAQs

## <a name="my-headset-displays-are-black"></a>Meine Headset-Anzeige ist schwarz.

* Überprüfen Sie die Leistung und Stabilität Ihres PCs:
    * Verwenden Sie den Task-Manager, um festzustellen, ob Prozesse die CPU-, GPU-oder Festplattenlaufwerke Ihres PCs als maxout verwenden.
    * Überprüfen Sie die Protokolle "Anwendung" und "System" in **Ereignisanzeige > Windows-Protokollen** , um festzustellen, ob eine APP abstürzen und Windows-Fehlerberichterstattung (wer)-Berichte erstellt.
    * Überprüfen Sie Windows Update, um sicherzustellen, dass Ihre Version von Windows aktuell ist. Sie müssen möglicherweise mehrmals "nach Updates suchen" auswählen.
* Überprüfen der APP-und Spiel Stabilität:
    * Stellen Sie sicher, dass Ihr PC die minimalen Systemanforderungen für jede APP oder jedes Spiel erfüllt, die nicht ordnungsgemäß ausgeführt wird.
    * Stellen Sie sicher, dass Ihre GPU-Treiber Version aktuell ist, und überprüfen Sie, ob neue Leistungs-und Kompatibilitätsprobleme und Regressionen für neue Treiber vorliegen.
    * Wenn Sie steamvr-apps und Spiele verwenden, stellen Sie sicher, dass die Komponente "steamvr" und "Windows Mixed Reality for steamvr" auf dem neuesten Stand sind.
* Überprüfen der Kompatibilität des HDMI-Adapters
    * Stellen Sie sicher, dass das HDMI-Kabel vollständig angeschlossen ist.
    * Wenn Sie einen HDMI-Adapter verwenden (z. b. einen Mini Display Port für den HDMI-Adapter), stellen Sie sicher, dass er mit Windows Mixed Reality kompatibel ist. Der Adapter muss die Unterstützung von HDMI 2,0 unterstützen, und es gibt zahlreiche ältere Adapter, die nur 1080p unterstützen. Weitere Informationen finden Sie unter [Empfohlene Adapter für Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * Die Plug-in-Reihenfolge ist wichtig. Verbinden Sie den HDMI-Adapter mit Ihrem PC, bevor Sie das Headset mit dem Adapter verbinden, insbesondere, wenn Sie einen USB-C-zu-HDMI-Adapter verwenden.
    * Entfernen Sie Erweiterungs Kabel, wenn Sie Sie verwenden.
* Grafikkarten-und Treiber Kompatibilität überprüfen:
    * Testen Sie den HDMI-Port Ihres PCs mit einem PC-Monitor. Einige PCs verfügen möglicherweise über mehr als einen HDMI-Port, und nicht alle können aktiv sein.
    * Wenn Ihr PC über eine integrierte Grafikverarbeitungseinheit (igpu) und eine diskrete Grafikverarbeitungseinheit (dGPU) verfügt, stellen Sie sicher, dass Sie mit dem-HDMI-Port Ihres dGPU verbunden sind.
    * Überprüfen Sie die Version des GPU-Treibers. Stellen Sie sicher, dass Sie aktuell ist, aber berücksichtigen Sie auch neue Leistungs-und Kompatibilitätsprobleme und Regressionen bei brandneuen Treibern.
    * Wenn Sie Gemischte Realität auf einem Laptop verwenden und einen neueren Grafiktreiber von der Website des Grafikkartenherstellers installiert haben, versuchen Sie, ein Downgrade auf den neuesten Grafikkartentreiber durchführen, der auf der Website des PC-Herstellers bereitgestellt wurde, oder auf Windows Update.
    * Wenn Sie über mehrere PCs verfügen, die mit dem PC verbunden sind, versuchen Sie, alle bis auf einen PC-Monitor vorübergehend zu trennen.
    * Wenn Sie eine benutzerdefinierte Aktualisierungsrate für Ihren PC-Monitor festgelegt haben, versuchen Sie vorübergehend, eine standardmäßige Aktualisierungsrate, z. b. 60 Hz, wiederherzustellen.
    * Wenn Sie Ihre Grafikkarte vor kurzem geändert haben, ohne Windows neu zu installieren, überprüfen Sie, ob der Headset-Monitor weiterhin den richtigen Treiber installiert hat. Vergewissern Sie sich, dass Ihr Headset angeschlossen ist, dass in Geräte-Manager unter dem Knoten Monitore der Eintrag "Mixed Reality Headset" aufgeführt ist.
    * Wenn Ihr PC über eine NVIDIA-Grafikkarte verfügt, stellen Sie sicher, dass NVIDIA die 3D-Vision Software deaktiviert ist.
    * Auf einigen Grafikkarten (besonders ältere Karten) unterstützt der HDMI-Port möglicherweise nicht die Verwendung von "HDMI 2,0" oder ist nicht vollständig kompatibel mit Windows Mixed Reality. Versuchen Sie, den Display Port Ihrer Grafikkarte mit einem [Display Port 1,2-to-HDMI 2,0-Adapter zu](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)verwenden.
    * HP Omen-PCs mit der HP-Produktnummer 1rj99ea # Abu verfügen über die in Windows Mixed Reality inkompatiblen HDMI-Ports (Öffnen Sie den "HP Support Assistant", und die Nummer wird im unteren Bereich der APP aufgelistet).
    * Wenn Ihr PC über eine Grafikkarte der AMD-Serie mit der Grafikkarte AMD verfügt und Sie ein Samsung Mixed Reality-Headset verwenden, aktualisieren Sie die Firmware Ihres Headsets auf Version 1.0.8 oder höher, um den HDMI-Port Ihrer Grafikkarte mit dem Headset zu verwenden.
    * Wenn Sie ein Surface Book 2 verwenden, stellen Sie sicher, dass Sie den [USB-C-USB-Adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)verwenden.
* Überprüfen Sie, ob ein Mixed Reality-Headset Hardwareproblem vorliegt:
    * Um Hardwareprobleme mit Ihrem Headset zu bestätigen oder auszuschließen, verbinden Sie Ihr Mixed Reality-Headset mit einem anderen PC.
    * Überprüfen Sie zunächst die Probleme mit der PC-Kompatibilität und des Setups, da die Symptome ähnlich sind.
* Stellen Sie sicher, dass das USB-Kabel an einen USB-3,0 oder einen schnelleren Port angeschlossen ist. USB-3,0-Ports verfügen über SS (Super Geschwindigkeit) neben Ihnen und werden oft blau gefärbt.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Meine Headset-Anzeige wird nach einiger Verwendung gelegentlich schwarz.

* Versuchen Sie, alle USB-Suspend-oder Energiespar Features auf Ihrem PC zu deaktivieren. Beispielsweise können Sie in " **Einstellungen" > System > Energie & Energiesparmodus > " [USB-Selektierungs](/windows-hardware/drivers/usbcon/usb-selective-suspend)** Vorgang" zulassen, dass der Computer dieses Gerät ausschalten, um Energie zu sparen "in Geräte-Manager und alle USB-Energiespareinstellungen in der Firmware Ihres PCs.
* Trennen Sie vorübergehend alle anderen USB-Geräte und Peripheriegeräte, die mit dem PC verbunden sind.
* Überprüfen Sie, ob die Version des GPU-Treibers aktuell ist, und überprüfen Sie, ob neue Leistungs-und Kompatibilitätsprobleme aufgetreten sind.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>Eine der anzeigen auf meinem Headset ist schwarz.

* Wenn Sie einen HDMI-Adapter verwenden, stellen Sie sicher, dass er den Wert von HDMI 2,0 unterstützt.
* Entfernen Sie alle USB-und HDMI-Erweiterungs Kabel, die Sie möglicherweise verwenden.
* Stellen Sie sicher, dass Ihr Grafiktreiber aktuell ist.
* Probieren Sie das Mixed Reality-Headset auf einem anderen PC aus.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>Mein Headset zeigt Turn Blue an, und das Mixed Reality-Portal wird erneut initialisiert.

Dies weist normalerweise auf ein Problem mit der Zuverlässigkeit der USB-Controller auf Ihrem PC hin:

* Testen Sie einen anderen USB-Anschluss. Ihr PC verfügt möglicherweise über mehrere USB 3,0-Controller.
* Entfernen Sie alle Erweiterungs Kabel (falls zutreffend).
* Entfernen Sie alle anderen USB-Geräte von Ihrem PC.
* Verbinden Sie einen extern betriebenen USB 3,0-Hub mit Ihrem PC, und verbinden Sie Ihr Headset mit dem Hub.
* Wenn Sie einen Desktop-PC verwenden, sollten Sie eine USB 3,0 PCIe-Karte erwerben, um Ihrem PC einen weiteren USB-Controller hinzuzufügen.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>Mein Headset bewirkt, dass mein PC während des Starts einen schwarzen Bildschirm anzeigt.

Auf einigen PCs ist das Einschalten Ihres Headsets vor dem Einschalten oder beim Neustart des PCs möglicherweise beeinträchtigt. Der PC könnte das Headset als "primärer Monitor" auswählen, um den Status des PC-Starts anzuzeigen, nicht ordnungsgemäß zu starten oder zu einem Fehlercode zu führen. Das Verhalten hängt von der Marke und dem Modell des PCs oder der Marke und dem Modell der Grafikkarte ab. So beheben Sie dieses Problem:

* Verbinden Sie Ihr Headset mit einem anderen Port auf Ihrer Grafikkarte (möglicherweise müssen Sie einen Adapter verwenden, um die anderen Ports zu verwenden).
* Stellen Sie sicher, dass die BIOS/UEFI-Firmware Ihres PCs auf dem neuesten Stand ist (aber aktualisieren Sie die BIOS/UEFI-Firmware Ihres PCs nur, wenn Sie dies tun).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Der PC oder das Headset zeigt Flimmern, Flash oder bleiben bei der Verwendung eines Surface-PCs schwarz aus.

* Stellen Sie sicher, dass Sie einen HDMI-Adapter verwenden, der HDMI 2,0 unterstützt. Viele ältere HDMI-Adapter unterstützen nur eine 1080p-Auflösung, die für Mixed Reality-Headsets unzureichend ist.
* Stellen Sie sicher, dass Ihr Grafiktreiber auf dem neuesten Stand ist. Überprüfen Sie Windows Update und die Website des PC-Herstellers nach einem aktualisierten Grafiktreiber.
* Einige Oberflächen Geräte sind mit Windows Mixed Reality nicht kompatibel. Erfahren Sie mehr über [Oberflächen Kompatibilität und-Anforderungen](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface).

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>Meine Headset-Anzeige funktioniert nach dem Herunterfahren und Durchführen eines schnellen Starts nicht mehr

Entfernen Sie das HDMI-Kabel und das USB-Kabel vom Headset, und binden Sie Sie dann wieder ein.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Meine Headset-Anzeige ist nicht verfügbar, aber das Vorschaufenster des gemischten Reality-Portals erscheint gut.

* Stellen Sie sicher, dass die Systemressourcen Ihres PCs (CPU, Arbeitsspeicher und Festplatte) verfügbar sind und nicht von einer anderen APP oder einem anderen Prozess genutzt werden.
* Aktualisieren Sie Ihren Grafiktreiber.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Ich erhalte den Fehler "die Installationsklasse ist nicht vorhanden oder ungültig" in Geräte-Manager

Wenn in Geräte-Manager "hololens-Sensoren" mit einem gelben Ausrufezeichen angezeigt wird, wählen Sie das Gerät aus, um weitere Details zu erhalten. Wenn die Meldung "die Treiber für dieses Gerät sind nicht installiert" angezeigt wird, wird eine Meldung angezeigt. (Code 28): die Installationsklasse ist nicht vorhanden oder ungültig. "Dies liegt in der Regel daran, dass auf Ihrem PC [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)ausgeführt wird. N Editionen von Windows 10 unterstützen Windows Mixed Reality nicht, und Sie müssen eine nicht-N-Version von Windows 10 installieren.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Meine WMR-Umgebung ist gezittert oder Verzögerungen, wenn ich meinen Kopf bewege und eine doppelte Vision anzeigt.

Auf einem Laptop mit integrierter Grafik und einer NVIDIA-GPU tritt nach einem bestimmten Zeitraum ein Fehler auf, der dazu führt, dass ein vorheriger Frame nach dem nächsten Frame angezeigt wird. Dies führt zu einer doppelten Sicht. Das Problem scheint für Treiber nach dem NVIDIA-Grafiktreiber 436,48 zu sein.  Durch die Installation dieses Treibers wird das Problem behoben, bis NVIDIA das Problem in den aktualisierten Treibern löst. Eine direkte Installation des nVidia-Grafik Treibers 436,48 finden Sie unter [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

## <a name="im-uncomfortable-in-my-headset"></a>Ich bin in meinem Headset unbequem

Allgemeine Informationen über den Komfort in Windows Mixed Reality finden Sie unter [Windows Mixed Reality-immersives Headset-Integrität,-Sicherheit und-Komfort](wmr-health-safety-comfort.md). Weitere Informationen zu Ihrem speziellen Headset finden Sie unter dem Headset-Hersteller.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Wie kann ich in meinem Headset eine klarere Ansicht erhalten?

Passen Sie die Anpassung Ihres Headsets an. Verschieben Sie das Feld nach oben und unten oder nach links und rechts auf dem Gesicht, und passen Sie die Bänder an

Wenn Ihr Headset über einen Knopf zum Anpassen der Kalibrierung verfügt, passen Sie die Kalibrierungs Einstellungen an. Wenn dies nicht der Fall ist, wechseln Sie zu **Einstellungen > gemischte Realität > visuelle Qualität** , und passen Sie die Kalibrierung dort an. Weitere Informationen zur Kalibrierung für ihr bestimmtes Gerät finden Sie bei Ihrem Headset-Hersteller.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Ich sehe häufig einen schwarzen Rahmen um die Ansicht im Headset. Manchmal ist es so, als ob ich einen Tunnel Suche.

Dies bedeutet, dass die Anwendung nicht in der Lage ist, die Framerate auf Ihrem PC zu erreichen, und dass das System alte Frames verwendet, um die Ansicht im Headset zu Rendering. Da Anwendungen nur den Teil der Welt Rendering, wenn Sie nicht konstant ihre Frameraten erreichen, versucht das System, die Welt aus einer vorherigen Sicht zu erzeugen, und gibt die fehlenden Details schwarz aus. Wenn dies häufig auftritt:

1. Schließen oder beenden Sie alle nicht benötigten Programme, um Arbeitsspeicher und CPU freizugeben.
2. Reduzieren Sie die Detaileinstellungen in Ihrer Anwendung.
3. Wechseln Sie zu **Einstellungen > gemischte Realität > der Headset-Anzeige** , um die Detail Menge zu reduzieren, die in der Windows Mixed Reality-Startseite angezeigt wird.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>Die Ansicht im Headset ist Jittering und wird sehr viel

Das System ist möglicherweise nicht in der Lage, Inhalte für das Headset zu Renderingsystem, oder das Überwachungssystem kann Probleme haben:

1. Öffnen Sie den Task-Manager, um sicherzustellen, dass Ihr PC über ausreichend Compute-Ressourcen verfügt. Sie sollten über 80% CPU-Auslastung, 400 MB RAM und Datenträger-e/a unter 80% verfügen.
2. Stellen Sie sicher, dass Sie über die neuesten Grafiktreiber für die Hardware verfügen. Weitere Informationen finden Sie im [Abschnitt Grafiktreiber](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Stellen Sie sicher, dass der Raum genug hell ist.
4. Entfernen Sie das Gerät, schließen Sie Windows Mixed Reality, und schließen Sie es wieder ein.
5. Starten Sie Ihren PC neu.
6. Wenn das Problem weiterhin besteht, wenden Sie sich an den [Kundensupport](https://support.microsoft.com/).