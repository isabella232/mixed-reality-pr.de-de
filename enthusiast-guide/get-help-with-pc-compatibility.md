---
title: Hilfe zur PC-Kompatibilität
description: Bleiben Sie auf dem neuesten Stand mit Ressourcen zum Lösen von PCs-Kompatibilitätsproblemen bei der Arbeit mit Windows Mixed Reality-Anwendungen und-Geräten.
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: 28b377108fdb51d7f922710e579d62e7103ef765
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580529"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Hilfe zur PC-Kompatibilität in Windows Mixed Reality

Wenn Sie Windows Mixed Reality einrichten oder das [Mixed Reality-Portal](install-windows-mixed-reality.md)verwenden, erhalten Sie einen Bericht darüber, ob Ihr PC der Aufgabe entspricht. Wir haben bestimmte Details zu den in den folgenden Abschnitten aufgeführten Abschnitten herausgestellt.

Bevor Sie fortfahren, sollten Sie die am häufigsten beschriebenen Korrekturen unten durchführen: 

> [!div class="checklist"]
> * Stellen Sie sicher, dass Ihr Computer die Mindestanforderungen für die [PC-Hardware Kompatibilität](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) erfüllt
> * Überprüfen Sie, ob die [Grafikkarte und der Prozessor](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) kompatibel sind
> * Überprüfen der Liste der [empfohlenen Adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
> * Aktualisieren Sie den Grafiktreiber, indem **Sie > Einstellungen starten > Update & Sicherheit auswählen > nach Updates suchen** . 

Wenn Sie Kontakt aufnehmen möchten, können Sie [die Community Fragen](https://answers.microsoft.com), sich [an den Support wenden](https://support.microsoft.com/contactus/)oder die Informationen zur [Problem](troubleshooting-windows-mixed-reality.md) Behandlung übernehmen.

## <a name="youre-good-to-go"></a>Das ist schon alles!

Wenn Ihnen die Meldung angezeigt wird, dass **Sie sich für eine gute Nachricht interessieren** , kann Ihr PC Windows Mixed Reality ausführen! Es gibt immer noch Abweichungen zwischen Computer Hardware und Konfiguration, sodass die gemischte Realität möglicherweise auf jedem PC nicht identisch ist.

## <a name="supports-some-features"></a>Unterstützt einige Features

Wenn Sie sehen, dass die Meldung **unterstützt einige Features enthält** , kann Ihr PC einige gemischte Umgebungen in Windows ausführen, aber möglicherweise nicht die bestmögliche Erfahrung bieten. Mögliche Nachteile sind das Einschließen von Grafiken, Leistungseinbußen und einige Anwendungen und Spiele, die Sie überhaupt nicht ausführen können. Wir haben Meldungen aufgelistet, die möglicherweise angezeigt werden, und wie Sie im folgenden beschrieben werden:

* [Dieser PC verfügt über eine integrierte Grafikkarte mit einem RAM mit einem Kanal.](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [Dieser PC verfügt über eine Hybrid Grafik Konfiguration mit einem inkompatiblen PCIe-Link.](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [Der Grafiktreiber dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [Der Prozessor dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [Dieser PC verfügt möglicherweise nicht über eine kompatible USB-Konfiguration.](#this-pc-might-not-have-a-compatible-usb-configuration)
* [Auf diesem PC ist Bluetooth 4,0 für Controller nicht vorhanden.](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [Abhängig von Ihrem Headset benötigen Sie möglicherweise einen Bluetooth-Adapter für die Verwendung von Motion-Controllern.](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [Dieser PC verfügt über keinen selbst gestützten USB-Anschluss.](#this-pc-doesnt-have-a-self-powered-usb-port)
* [Die Grafikkarte dieses PCs funktioniert nicht mit Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [Der Grafiktreiber dieses PCs funktioniert nicht mit Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [Der Prozessor dieses PCs funktioniert nicht mit Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [Dieser PC verfügt nicht über genügend freien Speicherplatz, um Windows Mixed Reality auszuführen.](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [Auf diesem PC wird eine Edition von Windows ausgeführt, die Windows Mixed Reality nicht unterstützt.](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [Auf diesem PC wird nicht die neueste Version von Windows 10 ausgeführt.](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [Dieser PC hat keinen USB 3,0-Port.](#this-pc-has-no-usb-30-port)
* [Sie können diese APP nicht über Remote Desktop ausführen.](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Dieser PC verfügt über eine integrierte Grafikkarte mit einem RAM mit einem Kanal.

Integrierte Grafikkarten bieten die beste Windows Mixed Reality-Darstellung auf PCs mit Dual-Channel-RAM. Bei Leistungsproblemen:

> [!div class="checklist"]
> * Installieren einer [kompatiblen diskreten Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * Installieren eines zusätzlichen RAM-Sticks zum Erstellen von Dual-Channel-RAM
> * Zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) wechseln

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Dieser PC verfügt über eine Hybrid Grafik Konfiguration mit einem inkompatiblen PCIe-Link.

PCIe steht für die Standort *übergreifende Interconnect*-Verbindung Express, bei der es sich um die Verbindung handelt, die ein PC für die Kommunikation mit einer Grafikkarte verwendet. Ihre Konfiguration funktioniert möglicherweise, aber wenn Probleme auftreten, müssen Sie zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)wechseln.

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Der Grafiktreiber dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality

Versuchen Sie, mit Windows Update einen neuen Grafiktreiber herunterzuladen:

> [!div class="checklist"]
> * Auswählen **von Start > Einstellungen > aktualisieren & Sicherheit > suchen nach Updates** oder wechseln zur Website Ihres PC-oder Grafikkartenherstellers
> * [Suchen nach Updates](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Wenn dies nicht funktioniert, müssen Sie Folgendes ausführen:

> [!div class="checklist"]
> * Hinzufügen einer [kompatiblen Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) wechseln

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Der Prozessor dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality

Der Prozessor Ihres PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality, da er nicht über genügend Kerne verfügt. Wenn die gemischte Realität von Windows nicht ordnungsgemäß ausgeführt wird:

> [!div class="checklist"]
> * Ersetzen des Prozessors durch einen [kompatiblen](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 
> * Zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) wechseln

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Dieser PC verfügt möglicherweise nicht über eine kompatible USB-Konfiguration.

Bei Problemen mit der Ausführung von Windows Mixed Reality:

> [!div class="checklist"]
> * In der [Dokumentation zu den empfohlenen Adaptern](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) finden Sie Lösungen für häufige Kompatibilitätsprobleme
> * Verwenden Sie ggf. einen [externen USB-Hub](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) .

Wenn die Probleme weiterhin bestehen:

> [!div class="checklist"]
> * Binden Sie Ihr Headset an einen anderen USB-Anschluss, falls vorhanden.
> * Wenn dies nicht funktioniert, deinstallieren Sie den aktuellen USB-Treiber Ihres PCs, und installieren Sie dann einen Microsoft-Treiber neu:

1. Wählen Sie **Start** aus, und geben Sie dann "Geräte-Manager" in das **Suchfeld** ein.
2. Wählen Sie **Geräte-Manager** aus den Ergebnissen aus.
3. Erweitern Sie die Kategorie für universelle serielle Buscontroller, sehen Sie sich die aufgeführten Geräte an, und deinstallieren Sie alle inkompatiblen Treiber.
    * Wenn die Liste ein Element "erweiterbares Host Controller" enthält, das nicht "Microsoft" am Ende des Geräte namens enthält, ist dieser Treiber nicht kompatibel mit Windows Mixed Reality. Sie müssen Sie deinstallieren. Zum Deinstallieren eines Treibers klicken Sie in der Liste mit der rechten Maustaste auf das Gerät, und wählen Sie **Gerät deinstallieren** Aktivieren Sie das Kontrollkästchen **Treibersoftware für dieses Gerät löschen** , und wählen Sie dann **deinstallieren** aus.
    * Wenn die Liste ein Element "erweiterbares Host Controller" enthält, das "etron" im Namen enthält, ist der USB-Controller nicht kompatibel mit Windows Mixed Reality. Sie müssen einen anderen USB-Anschluss auf dem PC verwenden oder einen anderen USB 3,0-Host Controller erwerben.
4. Starten Sie Ihren PC neu.
5. Kehren Sie zu Geräte-Manager zurück, und suchen Sie das Extensible Host Controller-Element erneut. Wenn Sie jetzt "Microsoft" am Ende des Geräte namens sehen, können Sie loslegen. Wenn nicht, wiederholen Sie die Schritte zur Deinstallation, um alle zusätzlichen nicht-Microsoft-Versionen des Treibers zu entfernen.

> [!div class="checklist"]
> * Wenn dies immer noch nicht funktioniert, fügen Sie dem PC eine PCIe-USB-Karte hinzu.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Auf diesem PC ist Bluetooth 4,0 für Controller nicht vorhanden.

2018 und neuere Windows Mixed Reality-Headsets verfügen bereits über das integrierte Bluetooth, aber wenn Sie über ein älteres Headset verfügen, ist Bluetooth 4,0 für Mixed Reality Motion-Controller erforderlich. Sie können [Windows Mixed Reality weiterhin mit einem Xbox-Controller](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset), einer [Maus und einer Tastatur](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)oder einem [USB-Bluetooth-Adapter verwenden, um Motion-Controller](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) mit Ihrem PC zu verbinden. [Empfohlene Adapter anzeigen](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>Abhängig von Ihrem Headset benötigen Sie möglicherweise einen Bluetooth-Adapter für die Verwendung von Motion-Controllern.

Für einige Headsets ist Bluetooth integriert, sodass Controller direkt mit den Headsets gekoppelt werden können. Andere erfordern ein Bluetooth-Radio im PC (oder ein separates Dongle) zur Verwendung von Bewegungs Controllern. Weitere Informationen finden Sie auf der Seite [Empfohlene Adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) .

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Dieser PC verfügt über keinen selbst gestützten USB-Anschluss.

Ein selbstgesteuerter USB 3,0-Port ist erforderlich, um ein Windows Mixed Reality-Headset zu verbinden. Stellen Sie eine Verbindung zwischen einem [USB 3,0-](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) Computer und dem PC her, und verwenden Sie diesen zum Verbinden Ihres Headsets.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>Die Grafikkarte dieses PCs funktioniert nicht mit Windows Mixed Reality

Die Grafikkarte dieses PCs ist nicht kompatibel mit Windows Mixed Reality. Folgendes ist erforderlich:

> [!div class="checklist"]
> * Hinzufügen einer [kompatiblen Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) wechseln

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>Der Grafiktreiber dieses PCs funktioniert nicht mit Windows Mixed Reality

Der Grafiktreiber dieses PCs funktioniert nicht mit Windows Mixed Reality. Versuchen Sie, mit Windows Update einen neuen Grafiktreiber herunterzuladen:

> [!div class="checklist"]
> * Auswählen **von Start > Einstellungen > aktualisieren & Sicherheit > suchen nach Updates** oder wechseln zur Website Ihres PC-oder Grafikkartenherstellers
> * [Suchen nach Updates](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Wenn dies nicht funktioniert, müssen Sie Folgendes ausführen:

> [!div class="checklist"]
> * Hinzufügen einer [kompatiblen Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) wechseln

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>Der Prozessor dieses PCs funktioniert nicht mit Windows Mixed Reality

Der Prozessor des PCs unterstützt keine AVX/popcnt-Anweisungen. Zum Ausführen von Windows Mixed Reality müssen Sie folgende Schritte ausführen:

> [!div class="checklist"]
> * Ersetzen Sie Sie durch eine [kompatible Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) . 
> * Zu einem [kompatiblen PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) wechseln

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Dieser PC verfügt nicht über genügend freien Speicherplatz, um Windows Mixed Reality auszuführen.

Für Windows Mixed Reality sind 10 GB freier Speicherplatz für Setup und optimale Leistung erforderlich. Löschen Sie Speicherplatz auf dem Laufwerk, und versuchen Sie dann erneut, die Einstellungen zu starten.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Auf diesem PC wird eine Edition von Windows ausgeführt, die Windows Mixed Reality nicht unterstützt.

Windows Mixed Reality funktioniert unter [Windows 10 Home](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) und [Windows 10 pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab). Sie müssen eine dieser Editionen installieren, um Windows Mixed Reality zu verwenden.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Auf diesem PC wird nicht die neueste Version von Windows 10 ausgeführt.

Für Windows Mixed Reality ist das Windows 10 Fall Creators Update erforderlich. [Aktualisieren Sie Ihren PC](https://support.microsoft.com/help/4028685) , und wiederholen Sie den Vorgang.

### <a name="this-pc-has-no-usb-30-port"></a>Dieser PC hat keinen USB 3,0-Port.

Sie benötigen einen USB 3,0-Port, um ein Windows Mixed Reality-Headset zu verbinden. Wenn Sie einen Desktop-PC verwenden, fügen Sie eine PCIe-USB-Karte hinzu. Für Laptops müssen Sie zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)wechseln.

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Sie können diese APP nicht über Remote Desktop ausführen.

Um Windows Mixed Reality verwenden zu können, benötigen Sie einen PC mit einem verbundenen Monitor. Wenn Sie einen virtuellen Computer verwenden oder über keinen Monitor verfügen, versuchen Sie, einen virtuellen Anzeige Adapter zu verwenden. Dabei handelt es sich um ein Gerät, das in den Display Port des PCs eingebunden und eine Computer Anzeige emuliert.

## <a name="getting-the-best-performance"></a>Erzielen der besten Leistung

Einige Hardware Konfigurationen können bei Windows Mixed Reality zu Leistungsproblemen führen. Bei Problemen wie dem langsamen Laden, der visuellen Darstellung von visuellen Elementen oder der schlechten visuellen Qualität sollten Sie diese häufig auftretenden Korrekturen ausprobieren:

* Schließen Sie alle geöffneten apps, die auf Ihrem PC-Desktop ausgeführt werden
* Wenn Sie einen USB-C-oder DisplayPort für den HDMI-Adapter verwenden, versuchen Sie es mit einem anderen. Empfohlene Adapter anzeigen
* Wenn zusätzliche Monitore mit der Grafikkarte des PCs verbunden sind, trennen Sie Sie.
* Versuchen Sie, einige andere Mixed Reality-Apps aus dem Windows Store herunterzuladen – einige können besser mit der Einrichtung Ihres Computers arbeiten
* Sehen Sie sich unsere Dokumentation zu den [Leistungs Fragen](performance-questions.md) an

Wenn weiterhin Leistungsprobleme auftreten, aktualisieren Sie die folgenden [Windows Mixed Reality](set-up-windows-mixed-reality.md) -Einstellungen für eine optimale Benutzerumgebung:

* Erfahrung
* Lösung
* Framerate
* Kalibrierung

> [!NOTE]
> Wenn eine Meldung angezeigt wird, die besagt, dass diese Hardwarekonfiguration möglicherweise mit Windows Mixed Reality funktioniert, aber noch nicht getestet wurde, können einige Leistungsprobleme auftreten, wenn Windows Mixed Reality für lange Sitzungen ausgeführt wird.

## <a name="working-with-steamvr"></a>Arbeiten mit steamvr

Das genießen von Spielen von steamvr ist eine hervorragend Möglichkeit, alles zu nutzen, was von VR angeboten werden muss. Sie sollten jedoch sicherstellen, dass Sie [die beste Leistung](performance-questions.md) von Ihrem immersiven Gerät erhalten. Nachdem Sie " [Steam](https://store.steampowered.com/about)" installiert haben:

* Befolgen Sie die Anweisungen zur Verwendung von " [steamvr" mit Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md) .
* Installieren der [steamvr-Leistungs Test](https://store.steampowered.com/app/323910/SteamVR_Performance_Test) -apps

## <a name="next-vr-checkpoint"></a>Nächster VR-Prüfpunkt

Wenn Sie die von uns festgelegte VR-Journey befolgen, sind Sie fast bereit, ein Gerät zu kaufen. Von hier aus können Sie mit dem letzten Vorgang fortfahren, bevor Sie den Prüfpunkt erwerben:

> [!div class="nextstepaction"]
> [Häufig gestellte Fragen](before-you-buy-faqs.md)

Oder Sie gelangen direkt in den Abschnitt "erste Schritte":

> [!div class="nextstepaction"]
> [Einrichten von Windows Mixed Reality](set-up-windows-mixed-reality.md)

Sie können jederzeit zur [VR-Journey](vr-journey.md) zurückkehren.