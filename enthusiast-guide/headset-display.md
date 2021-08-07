---
title: Häufig gestellte Fragen zur Headsetanzeige
description: Anzeigen Windows Mixed Reality Behandlung von Problemen mit der Headsetanzeige, die über unsere Standarddokumentation für den Support von Kunden hinausgehen.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support
appliesto:
- Windows 10
ms.openlocfilehash: 811b5160c739c8b19fde737e7a61bcef84e0cf60a87927adbe21241e229f3f22
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189389"
---
# <a name="headset-display-faqs"></a>Häufig gestellte Fragen zur Headsetanzeige

## <a name="my-headset-displays-are-black"></a>Meine Headsetanzeigen sind schwarz

* Überprüfen Sie die Leistung und Stabilität Ihres PCs:
    * Verwenden Sie die Task-Manager, um festzustellen, ob prozesse die CPU- oder GPU-Auslastung Ihres PCs oder die Laufwerke auf dem Datenträger maximal erreichen.
    * Überprüfen Sie die Protokolle "Anwendung" und "System" in **Ereignisanzeige > Windows-Protokollen,** um festzustellen, ob eine App abstürzt und Windows-Fehlerberichterstattung (WER)-Berichte generiert.
    * Überprüfen Sie Windows Update, um sicherzustellen, dass Ihre Version von Windows aktuell ist. Möglicherweise müssen Sie mehrmals "Nach Updates suchen" auswählen.
* Überprüfen der App- und Spielstabilität:
    * Stellen Sie sicher, dass Ihr PC die Mindestsystemanforderungen einer App oder eines Spiels erfüllt, die nicht ordnungsgemäß ausgeführt werden.
    * Stellen Sie sicher, dass ihre GPU-Treiberversion aktuell ist, und überprüfen Sie, ob neue Leistungs- und Kompatibilitätsprobleme und Regressionen bei neuen Treibern auftreten.
    * Wenn Sie SteamVR-Apps und -Spiele verwenden, stellen Sie sicher, dass SteamVR und die Windows Mixed Reality für die SteamVR-Komponenten auf dem neuesten Stand sind.
* Überprüfen Sie die KOMPATIBILITÄT des ADAPTERS MIT DEM ADAPTER:
    * Stellen Sie sicher, dass das CABLE-Kabel vollständig angeschlossen ist.
    * Stellen Sie bei Verwendung eines ADAPTERs (z. B. mini displayport to INTEGRAL) sicher, dass er mit Windows Mixed Reality kompatibel ist. Der Adapter muss ETHERNET 2.0 unterstützen, und es gibt viele ältere Adapter, die nur 1080p unterstützen. Informationen zu Windows Mixed Reality finden [Sie unter Empfohlene Adapter.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
    * Die Plug-Reihenfolge kann wichtig sein. Verbinden den ADAPTER an Ihren PC, bevor Sie das Headset mit dem Adapter verbinden, insbesondere, wenn Sie einen USB-C-zu-ADAPTER verwenden.
    * Entfernen Sie Erweiterungskabel, wenn Sie sie verwenden.
* Überprüfen Sie die Kompatibilität von Grafikkarte und Treiber:
    * Testen Sie den PORT PORT IHRES PCs mit einem PC-Monitor. Einige PCs verfügen möglicherweise über mehr als einen PORTS, und nicht alle sind möglicherweise aktiv.
    * Wenn Ihr PC über eine integrierte Grafikverarbeitungseinheit (iGPU) und eine diskrete Grafikverarbeitungseinheit (dGPU) verfügt, stellen Sie sicher, dass Sie an den PORTS Ihrer dGPU angeschlossen sind.
    * Überprüfen Sie ihre GPU-Treiberversion. Stellen Sie sicher, dass sie aktuell ist, aber achten Sie auch auf neue Leistungs- und Kompatibilitätsprobleme und Regressionen bei ganz neuen Treibern.
    * Wenn Sie Mixed Reality auf einem Laptop verwenden und einen neueren Grafiktreiber von der Website des Grafikkartenherstellers installiert haben, versuchen Sie, einen Downgrade auf den neuesten Grafikkartentreiber auf der Website Ihres PC-Herstellers oder auf Windows Update durchführen.
    * Wenn Sie mehrere PCs mit Ihrem PC verbunden haben, versuchen Sie vorübergehend, alle Monitore bis auf einen PC zu trennen.
    * Wenn Sie eine benutzerdefinierte Aktualisierungsrate für Ihren PC-Monitor festgelegt haben, versuchen Sie vorübergehend, auf eine Standardaktualisierungsrate wie 60 Hz zurückzusetzen.
    * Wenn Sie Ihre Grafikkarte vor Kurzem geändert haben, ohne Windows neu zu installieren, überprüfen Sie, ob auf dem Headsetmonitor immer noch der richtige Treiber installiert ist. Vergewissern Sie sich bei angeschlossenen Headsets, dass "Mixed Reality Headset" unter dem Knoten Monitore in Geräte-Manager aufgeführt ist.
    * Wenn Ihr PC über eine Nvidia-Grafikkarte verfügt, stellen Sie sicher, dass die 3D Vision-Software von Nvidia deaktiviert ist.
    * Auf einigen Grafikkarten (insbesondere bei älteren Karten) unterstützt der PORTS UNTER Umständen NICHT DIE VERSION 2.0 oder ist nicht vollständig kompatibel mit Windows Mixed Reality. Versuchen Sie, den DisplayPort-Adapter Ihrer Grafikkarte mit einem [DisplayPort 1.2-adapter zu EINEM 2.0-Adapter zu](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)verwenden.
    * HP Omen-PCs mit der HP-Produktnummer 1RJ99EA#PORTS verfügen über PORTS, die nicht mit Windows Mixed Reality kompatibel sind (öffnen Sie den "HP Support Assistant", und die Nummer wird unten in der App aufgeführt).
    * Wenn Ihr PC über eine Grafikkarte der AMD R9-Serie verfügt und Sie ein Samsung Mixed Reality Headset verwenden, aktualisieren Sie die Firmware Ihres Headsets auf Version 1.0.8 oder höher, um den PORTS-Port Ihrer Grafikkarte mit dem Headset zu verwenden.
    * Wenn Sie eine Surface Book 2 verwenden, stellen Sie sicher, dass Sie den [Adapter Surface USB-C to ETHERNET](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)verwenden.
* Suchen Sie nach einem Hardwareproblem mit Mixed Reality Headsets:
    * Um Hardwareprobleme mit Ihrem Headset zu bestätigen oder auszuschließen, verbinden Sie Ihr Mixed Reality Headset mit einem anderen PC.
    * Überprüfen Sie zunächst, ob Pc-Kompatibilitäts- und Setupprobleme vorliegen, da die Symptome ähnlich sind.
* Stellen Sie sicher, dass das USB-Kabel an einen USB 3.0- oder schnelleren Anschluss angeschlossen ist. Usb 3.0-Anschlüsse verfügen über SS (Super Speed) daneben und sind häufig blau farbig.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Meine Headsetanzeige wird nach einiger Verwendung gelegentlich schwarz

* Deaktivieren Sie alle USB-Anschalt- oder Energiesparfunktionen auf Ihrem PC. Beispiel: in **Einstellungen > System > Power & Sleep > USB selective [suspend](/windows-hardware/drivers/usbcon/usb-selective-suspend)**, die Einstellung "Allow the computer to turn off this device to save power" (Computer das Ausschalten dieses Geräts zum Speichern von Strom erlauben) in Geräte-Manager und alle USB-Energiespareinstellungen in der Firmware Ihres PCs.
* Trennen Sie vorübergehend alle anderen USB-Geräte und Peripheriegeräte, die mit Ihrem PC verbunden sind.
* Überprüfen Sie, ob ihre GPU-Treiberversion aktuell ist, und überprüfen Sie, ob neue Leistungs- und Kompatibilitätsprobleme und Regressionen bei neuen Treibern auftreten.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>Eines der Displays auf meinem Headset ist schwarz.

* Wenn Sie einen ETHERNET-Adapter verwenden, stellen Sie sicher, dass ER DIE UNTERSTÜTZUNG von ETHERNET 2.0 unterstützt.
* Entfernen Sie alle USB- und USB-Erweiterungskabel, die Sie möglicherweise verwenden.
* Stellen Sie sicher, dass der Grafiktreiber aktuell ist.
* Probieren Sie das Mixed Reality Headset auf einem anderen PC aus.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>Mein Headset wird blau angezeigt und wird dann Mixed Reality-Portal erneut initialisiert.

Dies weist in der Regel auf ein gelegentliches Problem mit der Zuverlässigkeit des USB-Controllers auf Ihrem PC hin:

* Probieren Sie einen anderen USB-Anschluss aus. Ihr PC verfügt möglicherweise über mehrere USB 3.0-Controller.
* Entfernen Sie alle Erweiterungskabel (falls zutreffend).
* Trennen Sie alle anderen USB-Geräte von Ihrem PC.
* Verbinden einen extern betriebenen USB 3.0-Hub an Ihren PC an, und verbinden Sie Ihr Headset mit dem Hub.
* Wenn Sie einen Desktop-PC verwenden, sollten Sie eine USB 3.0 PCIe-Karte erwerben, um Ihrem PC einen weiteren USB-Controller hinzuzufügen.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>Mein Headset bewirkt, dass mein PC beim Starten hängt oder einen schwarzen Bildschirm zeigt.

Auf einigen PCs kann der Startprozess beeinträchtigt werden, wenn Ihr Headset vor dem Einschalten oder Neustart des PCs angeschlossen bleibt. Ihr PC könnte das Headset als "primärer Monitor" auswählen, um den Pc-Startfortschritt anzuzeigen, nicht ordnungsgemäß zu starten oder "hängen zu bleiben" oder einen Pingfehlercode zu erzeugen. Das Verhalten hängt von der Marke und dem Modell des PCs oder der Marke und dem Modell der Grafikkarte ab. So beheben Sie dieses Problem:

* Verbinden Ihr Headset an einen anderen Port auf der Grafikkarte (möglicherweise müssen Sie einen Adapter verwenden, um die anderen Ports zu verwenden).
* Stellen Sie sicher, dass die BIOS-/UEFI-Firmware Ihres PCs auf dem neuesten Stand ist (aktualisieren Sie jedoch nur die BIOS-/UEFI-Firmware Ihres PCs, wenn Sie damit vertraut sind).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Mein PC oder Headset zeigt Flackern, Flash oder Schwarz an, wenn ein Surface-PC verwendet wird

* Stellen Sie sicher, dass Sie einen ETHERNET-Adapter verwenden, der ETHERNET 2.0 unterstützt. Viele ältere HALT-Adapter unterstützen nur eine Auflösung von 1080p, was für Mixed Reality Headsets nicht ausreicht.
* Stellen Sie sicher, dass Ihr Grafiktreiber auf dem neuesten Stand ist. Überprüfen Sie Windows Update und die Website des PC-Herstellers auf einen aktualisierten Grafiktreiber.
* Einige Surface-Geräte sind mit Windows Mixed Reality nicht kompatibel. Erfahren Sie mehr über [Surface-Kompatibilität und -Anforderungen.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>Meine Headsetanzeige funktioniert nach dem Herunterfahren und schnellem Starten nicht mehr.

Trennen Sie das KABELKABEL und das USB-Kabel vom Headset, und schließen Sie es dann wieder an.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Meine Headsetanzeigen sind geschnitten, aber das Vorschaufenster Mixed Reality-Portal wird gut angezeigt.

* Stellen Sie sicher, dass die Systemressourcen Ihres PCs (CPU, Arbeitsspeicher und Festplatte) verfügbar sind und nicht von einer anderen App oder einem anderen Prozess genutzt werden.
* Aktualisieren Sie den Grafiktreiber.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Ich erhalte den Fehler "Die Installationsklasse ist nicht vorhanden oder ungültig" in Geräte-Manager

Wenn "HoloLens Sensors" mit einem gelben Ausrufezeichen in Geräte-Manager angezeigt wird, wählen Sie das Gerät aus, um weitere Details anzuzeigen. Wenn eine Meldung mit dem Hinweis angezeigt wird, dass die Treiber für dieses Gerät nicht installiert sind. (Code 28)--Die Installationsklasse ist nicht vorhanden oder ungültig." Liegt in der Regel daran, dass auf Ihrem PC [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)ausgeführt wird. N Editionen von Windows 10 unterstützen Windows Mixed Reality nicht, und Sie müssen eine Nicht-N-Version von Windows 10 installieren.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Meine WMR-Umgebung ist jittery oder stuttert, wenn ich meinen Kopf ziehe und doppelsichtige Bilder anzeigt

Auf einem Laptop mit integrierter Grafik und einer Nvidia-GPU tritt nach einem bestimmten Zeitraum ein Fehler auf, der dazu führt, dass ein vorheriger Frame nach dem nächsten Frame angezeigt wird. Dies führt zu doppelter Sehkraft, je schneller Sie den Kopf in einem Gähn, einer Tonhöhe oder einer Rollbewegung bewegen. Das Problem scheint bei Treibern nach Nvidia-Grafiktreiber 436.48 zu sein.  Durch die Installation dieses Treibers wird das Problem behoben, bis Nvidia das Problem in den aktualisierten Treibern löst. Eine direkte Installation des Nvidia-Grafiktreibers 436.48 finden Sie unter [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

## <a name="im-uncomfortable-in-my-headset"></a>Ich bin in meinem Headset unermesslich

Allgemeine Informationen zum Komfort in Windows Mixed Reality finden Sie unter [Windows Mixed Reality Immersive Headset Health, Safety und Komfort.](wmr-health-safety-comfort.md) Ausführliche Informationen zu Ihrem spezifischen Headset finden Sie beim Hersteller des Headsets.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Wie erhalte ich eine klarere Ansicht in meinem Headset?

Versuchen Sie, die Passform Ihres Headsets anzupassen. Bewegen Sie es nach oben und unten oder links und rechts auf Ihrem Gesicht, und passen Sie die Bänder so an, dass es sich ansUgnen anfühlt.

Wenn Ihr Headset über einen Regler zum Anpassen der Kalibrierung verfügt, passen Sie seine Kalibrierungseinstellungen an. Andernfalls wechseln Sie zu **Einstellungen > Mixed Reality > Visuelle Qualität,** und passen Sie die Kalibrierung dort an. Weitere Informationen zur Kalibrierung für Ihr spezifisches Gerät finden Sie bei Ihrem Headsethersteller.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Ich sehe häufig einen schwarzen Rahmen um die Ansicht im Headset. Manchmal sieht es so aus, als würde ich einen Tunnel herunterspüren.

Dies bedeutet, dass die Anwendung nicht in der Lage ist, die Bildfrequenz auf Ihrem PC zu drücken, und das System alte Frames verwendet, um die Ansicht im Headset zu rendern. Da Anwendungen nur den Teil der Welt rendern, den Sie betrachten, versucht das System, die Welt aus einer früheren Sicht zu rendern, und füllt die fehlenden Details mit Schwarz aus, wenn sie nicht konsistent ihre Frameraten erreicht haben. Wenn dies häufig der Fall ist:

1. Schließen oder beenden Sie alle nicht benötigten Programme, um Arbeitsspeicher und CPU freizugeben.
2. Reduzieren Sie die Detaileinstellungen in Ihrer Anwendung.
3. Wechseln Sie zu **Einstellungen > Mixed Reality > Headset-Anzeige,** um die Detailmenge zu reduzieren, die im Windows Mixed Reality Home angezeigt wird.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>Die Ansicht im Headset ist sehr jitternd und stupend.

Das System kann möglicherweise keine Inhalte auf dem Headset rendern, oder beim Nachverfolgungssystem treten Probleme auf:

1. Öffnen Sie Task-Manager, um sicherzustellen, dass Ihr PC über genügend Computeressourcen verfügt. Sie sollten 80 % der CPU-freien, 400 MB RAM und Datenträger-E/A unter 80 % haben.
2. Stellen Sie sicher, dass Sie über die neuesten Grafiktreiber für Ihre Hardware verfügen. Weitere Informationen finden Sie im [Abschnitt grafiktreiber](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Stellen Sie sicher, dass der Raum über genügend Licht verfügt.
4. Trennen Sie das Gerät, schließen Sie Windows Mixed Reality, und schließen Sie es erneut ein.
5. Starten Sie Ihren PC neu.
6. Wenn das Problem weiterhin besteht, wenden Sie sich an den [Kundensupport.](https://support.microsoft.com/)