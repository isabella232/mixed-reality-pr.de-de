---
title: Häufig gestellte Fragen zur Headsetanzeige
description: Anzeigen Windows Mixed Reality Problembehandlung für Headset-Anzeigeprobleme, die über unsere Standarddokumentation für den Kundensupport hinausgehen.
author: qianw211
ms.author: v-qianwen
ms.date: 09/30/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 5a7c7979c9d93d917633cbfed23dc82597368a43
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436680"
---
# <a name="headset-display-faqs"></a>Häufig gestellte Fragen zur Headsetanzeige

## <a name="my-headset-displays-are-black"></a>Meine Headsetanzeigen sind schwarz

* Überprüfen Sie die Leistung und Stabilität Ihres PCs:
    * Verwenden Sie Task-Manager, um zu sehen, ob Prozesse die CPU-, GPU- oder Datenträgerlaufwerke Ihres PCs maximal nutzen.
    * Überprüfen Sie die Protokolle "Anwendung" und "System" in **Ereignisanzeige > Windows-Protokollen,** um zu überprüfen, ob eine App abstürzt und Windows-Fehlerberichterstattung (WER)-Berichte generiert.
    * Überprüfen Windows Update, um sicherzustellen, dass Ihre version Windows ist. Möglicherweise müssen Sie mehrmals auf "Nach Updates suchen" klicken.
* Überprüfen der Stabilität von Apps und Spielen:
    * Stellen Sie sicher, dass Ihr PC die Mindestsystemanforderungen von Apps oder Spielen erfüllt, die nicht ordnungsgemäß ausgeführt werden.
    * Stellen Sie sicher, dass Ihre GPU-Treiberversion auf dem neuesten Stand ist, und überprüfen Sie, ob neue Leistungs- und Kompatibilitätsprobleme und Regressionen bei neuen Treibern vorgeprüft wurden.
    * Wenn Sie Die Apps und Spiele von SteamVR verwenden, stellen Sie sicher, dass Die Komponenten von Windows Mixed Reality Für Dies sind Dies ist auf dem neuesten Stand.
* Überprüfen Sie die KOMPATIBILITÄT des ADAPTERs FÜR DEN ADAPTER:
    * Stellen Sie sicher, dass das ADAPTER-Kabel in der richtigen Weise angeschlossen ist.
    * Wenn Sie einen ADAPTER VOM TYP VERWENDEN (z. B. einen Mini DisplayPort zu EINEM ADAPTER), stellen Sie sicher, dass er mit dem Windows Mixed Reality. Der Adapter muss DIE VERSION 2.0 unterstützen, und es gibt viele ältere Adapter, die nur 1080p unterstützen. Weitere [Informationen finden Sie unter Empfohlene Adapter Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * Die Reihenfolge der Plug-Ins kann wichtig sein. Verbinden sie den ADAPTER an Ihren PC an, bevor Sie das Headset mit dem Adapter verbinden. Dies gilt insbesondere, wenn Sie einen USB-C-to-PCI-Adapter verwenden.
    * Versuchen Sie, Erweiterungskabel zu entfernen, wenn Sie sie verwenden.
* Überprüfen Sie die Kompatibilität von Grafikkarten und Treibern:
    * Testen Sie den PCI-Port Ihres PCs mit einem PC-Monitor. Einige PCs verfügen möglicherweise über mehr als einenCS-Port, und nicht alle sind aktiv.
    * Wenn Ihr PC über eine integrierte Grafikverarbeitungseinheit (iGPU) und eine diskrete Grafikverarbeitungseinheit (dGPU) verfügt, stellen Sie sicher, dass Sie an den PORT DES-Ports Ihrer dGPU angeschlossen sind.
    * Überprüfen Sie ihre GPU-Treiberversion. Stellen Sie sicher, dass es sich um eine aktuelle Version der Version von Geht, aber achten Sie auch auf neue Leistungs- und Kompatibilitätsprobleme und Regressionen bei ganz neuen Treibern.
    * Wenn Sie Mixed Reality auf einem Laptop verwenden und einen neueren Grafiktreiber von der Website des Grafikkartenherstellers installiert haben, versuchen Sie es mit einem Downgrade auf den neuesten Grafikkartentreiber, der auf der Website Ihres PC-Herstellers oder auf Windows Update bereitgestellt wird.
    * Wenn Sie mehrere PCs-Monitore mit Ihrem PC verbunden haben, versuchen Sie vorübergehend, die Verbindung mit nur einem PC-Monitor zu trennen.
    * Wenn Sie eine benutzerdefinierte Aktualisierungsrate für Ihren PC-Monitor festgelegt haben, versuchen Sie vorübergehend, auf eine Standardaktualisierungsrate wie 60 Hz zurück zu setzen.
    * Wenn Sie Ihre Grafikkarte vor Kurzem geändert haben, ohne Windows installieren, überprüfen Sie, ob auf dem Headsetmonitor immer noch der richtige Treiber installiert ist. Vergewissern Sie sich bei angeschlossenen Headsets, dass "Mixed Reality Headset" unter dem Knoten Monitore in der Geräte-Manager.
    * Wenn Ihr PC über eine Nvidia-Grafikkarte verfügt, stellen Sie sicher, dass die 3D Vision-Software von Nvidia deaktiviert ist.
    * Auf einigen Grafikkarten (insbesondere bei älteren Karten) unterstützt der PORTS DEST-Ports möglicherweise KEINES 2.0 oder ist möglicherweise nicht vollständig kompatibel mit Windows Mixed Reality. Versuchen Sie, den DisplayPort Ihrer Grafikkarte mit einem [DisplayPort 1.2-to-PORTS 2.0-Adapter zu verwenden.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
    * HP Omen-PCs mit HP-Produktnummer 1RJ99EA#TCP verfügen über PORTS, die nicht mit Windows Mixed Reality kompatibel sind (öffnen Sie den "HP Support Assistant", und die Nummer wird unten in der App aufgeführt).
    * Wenn Ihr PC über eine GRAFIKKARTE der AMD R9-Serie verfügt und Sie ein Samsung Mixed Reality-Headset verwenden, aktualisieren Sie die Firmware Ihres Headsets auf Version 1.0.8 oder neuer, um den PORTS-Port Ihrer Grafikkarte mit dem Headset zu verwenden.
    * Wenn Sie ein -Surface Book 2 verwenden, stellen Sie sicher, dass Sie den [Surface USB-C-to-PORTS-Adapter verwenden.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Überprüfen Sie, ob Mixed Reality Headset-Hardwareproblem behoben wurde:
    * Um Hardwareprobleme mit Ihrem Headset zu bestätigen oder auszuschließen, verbinden Sie Mixed Reality Headset mit einem anderen PC.
    * Überprüfen Sie zunächst, ob PC-Kompatibilitäts- und Setupprobleme auftreten, da die Symptome ähnlich sind.
* Stellen Sie sicher, dass das USB-Kabel an einen USB 3.0- oder schnelleren Anschluss angeschlossen ist. Neben USB 3.0-Anschlüssen ist SS (Super Speed) und häufig blau farbig.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Mein Headset-Display wird nach einiger Verwendung gelegentlich schwarz

* Versuchen Sie, alle USB-Aus- oder Energiesparfeatures auf Ihrem PC zu deaktivieren. Beispiel: **in Einstellungen > System > Power & Sleep > USB [selective suspend](/windows-hardware/drivers/usbcon/usb-selective-suspend)**, der Einstellung "Allow the computer to turn this device to save power" in Geräte-Manager sowie alle USB-Einstellungen zum Einsparen in der Firmware Ihres PCs.
* Trennen Sie vorübergehend alle anderen USB-Geräte und Peripheriegeräte, die mit Ihrem PC verbunden sind.
* Überprüfen Sie, ob Ihre GPU-Treiberversion zuletzt verwendet wurde, und überprüfen Sie, ob neue Leistungs- und Kompatibilitätsprobleme und Regressionen bei neuen Treibern vorgeprüft wurden.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>Eines der Displays auf meinem Headset ist schwarz

* Wenn Sie einen ADAPTER VOM TYP 2.0 verwenden, stellen Sie sicher, dass er DIE 2.0 unterstützt.
* Entfernen Sie alle USB- und STICK-Erweiterungskabel, die Sie möglicherweise verwenden.
* Stellen Sie sicher, dass Ihr Grafiktreiber aktuell ist.
* Testen Sie Mixed Reality Headset auf einem anderen PC.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>Mein Headset wird blau angezeigt und Mixed Reality-Portal erneut initialisiert

Dies weist in der Regel auf ein gelegentliches Problem mit der Zuverlässigkeit des USB-Controllers auf Ihrem PC hin:

* Testen Sie einen anderen USB-Anschluss. Ihr PC kann über mehrere USB 3.0-Controller verfügen.
* Entfernen Sie alle Erweiterungskabel (falls zutreffend).
* Trennen Sie alle anderen USB-Geräte von Ihrem PC.
* Verbinden einen extern betriebenen USB 3.0-Hub an Ihren PC an, und verbinden Sie Ihr Headset mit dem Hub.
* Wenn Sie einen Desktop-PC verwenden, sollten Sie eine USB 3.0-PCIe-Karte kaufen, um Ihrem PC einen weiteren USB-Controller hinzuzufügen.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>Mein Headset bewirkt, dass mein PC beim Starten hängt oder einen schwarzen Bildschirm zeigt

Auf einigen PCs kann es sein, dass der Startvorgang des PCs beeinträchtigt wird, wenn Ihr Headset vor dem Einschalten oder neustarten angeschlossen ist. Ihr PC könnte die Headsetanzeigen als "primären Monitor" auswählen, um den Pc-Startfortschritt zu zeigen, nicht ordnungsgemäß zu starten oder "hängen" zu lassen oder einen Beepingfehlercode zu erzeugen. Das Verhalten hängt vom PC-Hersteller und -Modell oder vom Hersteller und Modell der Grafikkarte ab. So beheben Sie dieses Problem:

* Verbinden Headset an einen anderen Port auf Ihrer Grafikkarte an (möglicherweise müssen Sie einen Adapter verwenden, um die anderen Ports zu verwenden).
* Stellen Sie sicher, dass die BIOS-/UEFI-Firmware Ihres PCs auf dem neuesten Stand ist (aktualisieren Sie jedoch nur die BIOS-/UEFI-Firmware Ihres PCs, wenn Sie damit zufrieden sind).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Mein PC oder Headset zeigt flackern, blinken oder schwarz bleiben, wenn ein Surface-PC verwendet wird.

* Stellen Sie sicher, dass Sie einen ADAPTER vom Typ ADAPTER verwenden, der DIE 2.0 unterstützt. Viele ältere ADAPTER vom TypADAPTER unterstützen nur eine Auflösung von 1080p, was für Mixed Reality headsets nicht ausreicht.
* Stellen Sie sicher, dass Ihr Grafiktreiber auf dem neuesten Stand ist. Überprüfen Windows Update und die Website des PC-Herstellers, um einen aktualisierten Grafiktreiber zu erhalten.
* Einige Surface-Geräte sind nicht kompatibel mit Windows Mixed Reality. Erfahren Sie mehr über [Surface-Kompatibilität und -Anforderungen.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>Mein Headset-Display funktioniert nicht, nachdem ich heruntergefahren bin und einen schnellen Start ausgeführt habe.

Trennen Sie das ADAPTER-Kabel und das USB-Kabel vom Headset, und schließen Sie sie dann wieder ein.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Meine Headset-Displays sind abgesengt, aber Mixed Reality-Portal Vorschaufenster des Headsets ist in Ordnung.

* Stellen Sie sicher, dass die Systemressourcen Ihres PCs (CPU, Arbeitsspeicher und Festplatte) verfügbar sind und nicht von einer anderen App oder einem anderen Prozess verbraucht werden.
* Aktualisieren Sie den Grafiktreiber.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Ich habe den Fehler "The install class is not present or is invalid" (Die Installationsklasse ist nicht vorhanden oder ungültig) in Geräte-Manager

Wenn "HoloLens Sensors" mit einem gelben Ausrufezeichen in der Geräte-Manager angezeigt wird, wählen Sie das Gerät aus, um weitere Details zu erhalten. Wenn eine Meldung mit dem Folgenden angezeigt wird: "Die Treiber für dieses Gerät sind nicht installiert. (Code 28) - The install class isn't present or is invalid". Dies liegt in der Regel daran, dass auf Ihrem PC Windows 10 [N ausgeführt wird.](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017) N Editionen von Windows 10 und Windows 11 unterstützen Windows Mixed Reality nicht, und Sie müssen eine Nicht-N-Version von Windows 10 oder Windows 11 installieren.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Meine WMR-Umgebung ist jittery odertters, wenn ich meinen Kopf bewegen und doppeltes Sehen anzeigt.

Auf einem Laptop mit integrierter Grafik und einer Nvidia-GPU tritt nach einer Bestimmten Zeit ein Fehler auf, der anscheinend dazu führt, dass ein vorheriger Frame nach dem nächsten Frame angezeigt wird. Dies führt dazu, dass Sie den Kopf schneller in einer Yaw-, Pitch- oder Rollbewegung bewegen. Das Problem scheint bei Treibern nach Nvidia Graphics Driver 436.48 zu sein.  Durch die Installation dieses Treibers wird das Problem behoben, bis Nvidia das Problem in den aktualisierten Treibern löst. Eine direkte Installation des Nvidia-Grafiktreibers 436.48 finden Sie unter [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

## <a name="im-uncomfortable-in-my-headset"></a>Ich bin in meinem Headset

Allgemeine Informationen zum Komfort in der Windows Mixed Reality finden Sie Windows Mixed Reality Integrität, Sicherheit und Komfort des immersiven [Headsets.](wmr-health-safety-comfort.md) Weitere Informationen zu Ihrem spezifischen Headset finden Sie beim Hersteller des Headsets.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Wie kann ich eine klarere Ansicht in meinem Headset erhalten?

Versuchen Sie, die Anpassung Ihres Headsets anzupassen. Bewegen Sie sie auf Ihrem Gesicht nach oben und unten oder links und rechts, und passen Sie die Bänder so an, dass es sich anstappt.

Wenn Ihr Headset über einen Regler verfügt, um die Kalibrierung anzupassen, passen Sie die Kalibrierungseinstellungen an. Falls nicht, wechseln Sie zu Mixed Reality Einstellungen > und > visual quality (Visuelle **Qualität),** und passen Sie die Kalibrierung dort an. Weitere Informationen zur Kalibrierung für Ihr spezifisches Gerät finden Sie bei Ihrem Headsethersteller.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Im Headset wird häufig ein schwarzer Rahmen um die Ansicht angezeigt. Manchmal sieht es so aus, als würde ich einen Tunnel herunterspüren.

Dies bedeutet, dass die Anwendung nicht in der Lage ist, die Bildfrequenz auf Ihrem PC zu drücken, und das System alte Frames verwendet, um die Ansicht im Headset zu rendern. Da Anwendungen nur den Teil der Welt rendern, den Sie betrachten, versucht das System, die Welt aus einer früheren Sicht zu rendern, und füllt die fehlenden Details mit Schwarz aus, wenn sie nicht konsistent ihre Frameraten erreicht haben. Wenn dies häufig der Fall ist:

1. Schließen oder beenden Sie alle nicht benötigten Programme, um Arbeitsspeicher und CPU freizugeben.
2. Reduzieren Sie die Detaileinstellungen in Ihrer Anwendung.
3. Wechseln Sie zu **Einstellungen > Mixed Reality > Headset-Anzeige,** um die Detailmenge zu reduzieren, die im Windows Mixed Reality Home angezeigt wird.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>Die Ansicht im Headset ist sehr jitternd und stupend.

Das System kann möglicherweise keine Inhalte auf dem Headset rendern, oder das Nachverfolgungssystem kann Probleme haben:

1. Öffnen Sie Task-Manager, um sicherzustellen, dass Ihr PC über genügend Computeressourcen verfügt. Sie sollten 80 % der CPU-freien, 400 MB RAM und Datenträger-E/A unter 80 % haben.
2. Stellen Sie sicher, dass Sie über die neuesten Grafiktreiber für Ihre Hardware verfügen. Weitere Informationen finden Sie im [Abschnitt grafiktreiber](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Stellen Sie sicher, dass der Raum über genügend Licht verfügt.
4. Trennen Sie das Gerät, schließen Sie Windows Mixed Reality, und schließen Sie es erneut ein.
5. Starten Sie Ihren PC neu.
6. Wenn das Problem weiterhin besteht, wenden Sie sich an den [Kundensupport.](https://support.microsoft.com/)