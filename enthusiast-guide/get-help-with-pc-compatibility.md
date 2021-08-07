---
title: Hilfe zur PC-Kompatibilität
description: Halten Sie sich über Ressourcen zum Beheben von PC-Kompatibilitätsproblemen auf dem Laufenden, wenn Sie mit Windows Mixed Reality Anwendungen und Geräten arbeiten.
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: cd5598147823670d1aa00eddda844bea21d7da262339624613f3724cbc5157fa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189212"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Hilfe zur PC-Kompatibilität in Windows Mixed Reality

Wenn Sie Windows Mixed Reality einrichten oder die [Mixed Reality-Portal](install-windows-mixed-reality.md)verwenden, erhalten Sie einen Bericht darüber, ob Ihr PC der Aufgabe entspricht. Wir haben spezifische Details zu den Informationen aufgeführt, die in den folgenden Abschnitten angezeigt werden können.

Bevor Sie weitergehen, probieren Sie die gängigsten Fehlerbehebungen unten aus: 

> [!div class="checklist"]
> * Stellen Sie sicher, dass Ihr Computer die Mindestanforderungen an die [PC-Hardwarekompatibilität](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) erfüllt.
> * Überprüfen Sie, ob [Die Grafikkarte und der Prozessor](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) kompatibel sind.
> * Überprüfen sie die Liste mit den [empfohlenen Adaptern.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
> * Aktualisieren Sie Ihren Grafiktreiber, indem Sie > Einstellungen > **Update & Security > Nach Updates suchen** auswählen. 

Wenn Sie Kontakt aufnehmen möchten, können Sie sich an [die Community wenden,](https://answers.microsoft.com)sich an den [Support wenden](https://support.microsoft.com/contactus/)oder die Informationen [zur Problembehandlung](troubleshooting-windows-mixed-reality.md) durchgehen.

## <a name="youre-good-to-go"></a>Sie können loslassen.

Gute Nachrichten: Wenn Sie die Meldung **You're good to go (Sie können los geht)** sehen, kann Ihr PC Windows Mixed Reality ausgeführt werden. Es gibt immer noch Unterschiede zwischen Computerhardware und -konfiguration, sodass die Mixed Reality Erfahrung möglicherweise nicht auf jedem PC identisch ist.

## <a name="supports-some-features"></a>Unterstützt einige Features

Wenn die Meldung **Supports some features (Unterstützt einige Features)** angezeigt wird, kann Ihr PC einige Windows Mixed Reality Funktionen ausführen, bietet aber möglicherweise nicht die bestmögliche Benutzererfahrung. Mögliche Nachteile sind verzögerte Grafiken, Leistungstreffer und einige Anwendungen und Spiele, die Sie überhaupt nicht ausführen können. Wir haben meldungen aufgelistet, die Ihnen möglicherweise angezeigt werden, und wie Sie dies weiter unten tun können:

* [Dieser PC verfügt über eine integrierte Grafikkarte mit Einkanal-RAM](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [Dieser PC verfügt über eine Hybridgrafikkonfiguration mit einem inkompatiblen PCIe-Link.](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [Der Grafiktreiber dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [Der Prozessor dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [Dieser PC hat möglicherweise keine kompatible USB-Konfiguration.](#this-pc-might-not-have-a-compatible-usb-configuration)
* [Dieser PC verfügt nicht über Bluetooth 4.0 für Controller.](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [Abhängig von Ihrem Headset benötigen Sie möglicherweise einen Bluetooth Adapter, um Motion-Controller zu verwenden.](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [Dieser PC verfügt nicht über einen selbst betriebenen USB-Anschluss.](#this-pc-doesnt-have-a-self-powered-usb-port)
* [Die Grafikkarte dieses PCs funktioniert nicht mit Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [Der Grafiktreiber dieses PCs funktioniert nicht mit Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [Der Prozessor dieses PCs funktioniert nicht mit Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [Dieser PC hat nicht genügend freien Speicherplatz, um Windows Mixed Reality](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [Auf diesem PC wird eine Edition von Windows ausgeführt, die Windows Mixed Reality](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [Auf diesem PC wird nicht die neueste Version von Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [Dieser PC verfügt über keinen USB 3.0-Anschluss.](#this-pc-has-no-usb-30-port)
* [Sie können diese App nicht über Remotedesktop ausführen.](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Dieser PC verfügt über eine integrierte Grafikkarte mit Einkanal-RAM

Integrierte Grafikkarten bieten die beste Windows Mixed Reality auf PCs mit Dualchannel-RAM. Bei Leistungsproblemen:

> [!div class="checklist"]
> * Installieren einer [kompatiblen diskreten Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * Installieren eines zusätzlichen RAM-Sticks zum Erstellen von Dual-Channel-RAM
> * Wechseln zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Dieser PC verfügt über eine Hybridgrafikkonfiguration mit einem inkompatiblen PCIe-Link.

PCIe steht für *Peripheral Component Interconnect Express*. Dies ist die Verbindung, die ein PC für die Kommunikation mit einer Grafikkarte verwendet. Ihre Konfiguration funktioniert möglicherweise, aber wenn Probleme auftreten, müssen Sie zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)wechseln.

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Der Grafiktreiber dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality

Versuchen Sie, einen neuen Grafiktreiber mithilfe von Windows Update herunterzuladen, indem Sie:

> [!div class="checklist"]
> * Wählen Sie **Start > Einstellungen > Update & Security > Check for updates (Nach Updates suchen)** aus, oder besuchen Sie die Website Ihres PC- oder Grafikkartenherstellers.
> * [Suchen nach Updates](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Wenn dies nicht funktioniert, müssen Sie:

> [!div class="checklist"]
> * Hinzufügen einer [kompatiblen Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Wechseln zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Der Prozessor dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality

Der Prozessor Ihres PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality, da er nicht über genügend Kerne verfügt. Wenn Windows Mixed Reality nicht gut ausgeführt wird:

> [!div class="checklist"]
> * Ersetzen des Prozessors durch einen [kompatiblen](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) Prozessor 
> * Wechseln zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Dieser PC hat möglicherweise keine kompatible USB-Konfiguration.

Bei Problemen beim Ausführen von Windows Mixed Reality:

> [!div class="checklist"]
> * Informationen zu Lösungen für häufige Kompatibilitätsprobleme finden Sie in der Dokumentation zu [empfohlenen Adaptern.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
> * Ziehen Sie die Verwendung eines [externen USB-Hubs in](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) Betracht.

Wenn die Probleme weiterhin bestehen:

> [!div class="checklist"]
> * Schließen Sie Ihr Headset an einen anderen USB-Anschluss an, sofern verfügbar.
> * Wenn dies nicht funktioniert, deinstallieren Sie den aktuellen USB-Treiber Ihres PCs, und installieren Sie dann einen Microsoft-Treiber neu:

1. Wählen Sie **Starten** aus, und geben Sie dann "Geräte-Manager" in das **Suchfeld** ein.
2. Wählen Sie in den Ergebnissen **Geräte-Manager** aus.
3. Erweitern Sie die Kategorie für universelle serielle Bus-Controller, sehen Sie sich die aufgeführten Geräte an, und deinstallieren Sie alle inkompatiblen Treiber.
    * Wenn die Liste ein Element "eXtensible Host Controller" enthält, das am Ende des Gerätenamens nicht "Microsoft" enthält, ist dieser Treiber nicht mit Windows Mixed Reality kompatibel. Sie müssen es deinstallieren. Klicken Sie zum Deinstallieren eines Treibers mit der rechten Maustaste auf das Gerät in der Liste, und wählen **Sie Gerät deinstallieren** aus. Aktivieren Sie das Kontrollkästchen **Treibersoftware für dieses Gerät löschen,** und wählen Sie dann **Deinstallieren aus.**
    * Wenn die Liste ein Element "eXtensible Host Controller" enthält, das "E untereinander" im Namen enthält, ist dieser USB-Controller nicht mit Windows Mixed Reality kompatibel. Sie müssen einen anderen USB-Anschluss auf dem PC verwenden oder einen anderen USB 3.0-Hostcontroller erwerben.
4. Starten Sie Ihren PC neu.
5. Kehren Sie zu Geräte-Manager zurück, und suchen Sie das Element eXtensible Host Controller erneut. Wenn am Ende des Gerätenamens jetzt "Microsoft" angezeigt wird, können Sie losgehen. Wenn dies nicht der Fall ist, wiederholen Sie die Deinstallationsschritte, um zusätzliche Nicht-Microsoft-Versionen des Treibers zu entfernen.

> [!div class="checklist"]
> * Wenn dies immer noch nicht funktioniert, fügen Sie Ihrem PC eine PCIe-USB-Karte hinzu.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Dieser PC verfügt nicht über Bluetooth 4.0 für Controller.

2018 und neuere Windows Mixed Reality Headsets verfügen bereits über die integrierte Bluetooth, aber wenn Sie über ein älteres Headset verfügen, ist Bluetooth 4.0 für Mixed Reality-Motion-Controller erforderlich. Sie können [weiterhin Windows Mixed Reality mit einem Xbox-Controller,](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)einer Maus und [Tastatur](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)oder einem [USB-Bluetooth-Adapter verwenden, um Motion-Controller](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) mit Ihrem PC zu verbinden. [Weitere Informationen finden Sie unter Empfohlene Adapter.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>Abhängig von Ihrem Headset benötigen Sie möglicherweise einen Bluetooth Adapter, um Motion-Controller zu verwenden.

Einige Headsets haben Bluetooth integriert, sodass Controller direkt mit den Headsets gekoppelt werden können. Andere benötigen ein Bluetooth Funkgerät auf dem PC (oder einen separaten Dongle), um Motion-Controller zu verwenden. Weitere Informationen finden Sie auf der Seite [empfohlene Adapter.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters)

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Dieser PC verfügt nicht über einen selbst betriebenen USB-Anschluss.

Ein selbst betriebener USB 3.0-Anschluss ist erforderlich, um ein Windows Mixed Reality Headset zu verbinden. Verbinden einen [usb 3.0-Hub](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) mit Stromversorgung auf dem PC an, und verwenden Sie diesen, um Ihr Headset zu verbinden.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>Die Grafikkarte dieses PCs funktioniert nicht mit Windows Mixed Reality

Die Grafikkarte dieses PCs ist nicht mit Windows Mixed Reality kompatibel. Folgendes ist erforderlich:

> [!div class="checklist"]
> * Hinzufügen einer [kompatiblen Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Wechseln zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>Der Grafiktreiber dieses PCs funktioniert nicht mit Windows Mixed Reality

Der Grafiktreiber dieses PCs funktioniert nicht mit Windows Mixed Reality. Versuchen Sie, einen neuen Grafiktreiber mithilfe von Windows Update herunterzuladen, indem Sie:

> [!div class="checklist"]
> * Wählen Sie **Start > Einstellungen > Update & Security > Check for updates (Nach Updates suchen)** aus, oder besuchen Sie die Website Ihres PC- oder Grafikkartenherstellers.
> * [Suchen nach Updates](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Wenn dies nicht funktioniert, müssen Sie:

> [!div class="checklist"]
> * Hinzufügen einer [kompatiblen Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Wechseln zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>Der Prozessor dieses PCs funktioniert nicht mit Windows Mixed Reality

Der Prozessor dieses PCs unterstützt keine AVX-/Popcnt-Anweisungen. Um Windows Mixed Reality ausführen zu können, müssen Sie:

> [!div class="checklist"]
> * Ersetzen Sie sie durch eine [kompatible Grafikkarte.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Wechseln zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Dieser PC hat nicht genügend freien Speicherplatz, um Windows Mixed Reality

Windows Mixed Reality erfordert 10 GB freien Speicherplatz, um die Einrichtung und die beste Leistung zu erzielen. Löschen Sie speicherplatzauf Ihrem Laufwerk, und versuchen Sie dann, die Einrichtung von Anfang an erneut zu starten.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Auf diesem PC wird eine Edition von Windows ausgeführt, die Windows Mixed Reality

Windows Mixed Reality funktioniert mit [Windows 10 Home](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) und [Windows 10 Pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab). Sie müssen eine dieser Editionen installieren, um Windows Mixed Reality verwenden zu können.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Auf diesem PC wird nicht die neueste Version von Windows 10

Windows Mixed Reality erfordert die Windows 10 Fall Creators Update. [Aktualisieren Sie Ihren PC,](https://support.microsoft.com/help/4028685) und versuchen Sie es erneut.

### <a name="this-pc-has-no-usb-30-port"></a>Dieser PC verfügt über keinen USB 3.0-Anschluss.

Sie benötigen einen USB 3.0-Anschluss, um ein Windows Mixed Reality Headset zu verbinden. Wenn Sie einen Desktop-PC verwenden, fügen Sie eine PCIe-USB-Karte hinzu. Für Laptops müssen Sie zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)wechseln.

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Sie können diese App nicht über Remotedesktop ausführen.

Um Windows Mixed Reality verwenden zu können, benötigen Sie einen PC mit angeschlossener Überwachung. Wenn Sie einen virtuellen Computer verwenden oder keinen Monitor haben, versuchen Sie es mit einem virtuellen Anzeigeadapter. Dies ist ein Gerät, das an den DisplayPort des PCs angeschlossen ist und eine Computeranzeige emuliert.

## <a name="getting-the-best-performance"></a>Erzielen der besten Leistung

Einige Hardwarekonfigurationen können zu Leistungsproblemen bei Windows Mixed Reality führen. Probieren Sie bei Problemen wie langsames Laden, abgeschrägte Visuals oder schlechte visuelle Qualität die folgenden häufigen Fehlerbehebungen aus:

* Schließen Sie alle geöffneten Apps, die auf Ihrem PC-Desktop ausgeführt werden.
* Wenn Sie einen USB-C- oder DisplayPort-Adapter für DEN ADAPTER VERWENDEN, versuchen Sie es mit einem anderen Adapter. Weitere Informationen finden Sie unter Empfohlene Adapter.
* Wenn zusätzliche Monitore mit der Grafikkarte des PCs verbunden sind, trennen Sie sie.
* Versuchen Sie, verschiedene Mixed Reality-Apps aus dem Windows Store herunterzuladen– einige funktionieren möglicherweise besser mit der Einrichtung Ihres Computers.
* Sehen Sie sich unsere [Dokumentation zu Leistungsfragen](performance-questions.md) an.

Wenn weiterhin Leistungsprobleme auftreten, aktualisieren [](set-up-windows-mixed-reality.md) Sie die folgenden Windows Mixed Reality-Einstellungen, um eine optimale Benutzererfahrung zu erzielen:

* Erfahrung
* Lösung
* Bildfrequenz
* Kalibrierung

> [!NOTE]
> Wenn eine Meldung mit dem Hinweis angezeigt wird, dass diese Hardwarekonfiguration möglicherweise mit Windows Mixed Reality funktioniert, aber noch nicht getestet wurde, können beim Ausführen von Windows Mixed Reality für lange Sitzungen Leistungsprobleme auftreten.

## <a name="working-with-steamvr"></a>Arbeiten mit SteamVR

Spiele von SteamVR sind eine hervorragende Möglichkeit, alles zu erleben, was VR zu bieten hat. Sie müssen jedoch sicherstellen, dass Sie [die beste Leistung](performance-questions.md) ihres immersiven Geräts erzielen. Nachdem Sie [Steam](https://store.steampowered.com/about)installiert haben:

* Befolgen Sie die Anweisungen für die [Verwendung von SteamVR mit Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)
* Installieren der [SteamVR-Leistungstest-Apps](https://store.steampowered.com/app/323910/SteamVR_Performance_Test)

## <a name="next-vr-checkpoint"></a>Nächster VR-Prüfpunkt

Wenn Sie die von uns festgelegte VR-Journey verfolgen, sind Sie fast bereit, ein Gerät zu kaufen. Von hier aus können Sie mit dem letzten fortfahren, bevor Sie den Prüfpunkt kaufen:

> [!div class="nextstepaction"]
> [Häufig gestellte Fragen zum Kauf](before-you-buy-faqs.md)

Alternativ können Sie direkt mit dem Abschnitt erste Schritte beginnen:

> [!div class="nextstepaction"]
> [Einrichten von Windows Mixed Reality](set-up-windows-mixed-reality.md)

Sie können jederzeit zur [VR-Journey](vr-journey.md) zurückkehren.