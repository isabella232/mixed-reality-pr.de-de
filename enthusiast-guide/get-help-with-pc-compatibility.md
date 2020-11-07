---
title: Hilfe zur PC-Kompatibilität in Windows Mixed Reality
description: Hilfe Ressourcen für PC-Kompatibilitätsprobleme bei der Arbeit mit Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
appliesto:
- Windows 10
ms.openlocfilehash: 5b24edd88a55bedea2d288f27363714cbfe768b4
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340588"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Hilfe zur PC-Kompatibilität in Windows Mixed Reality

Wenn Sie Windows Mixed Reality einrichten oder die [Windows Mixed Reality PC Check](https://www.microsoft.com/p/windows-mixed-reality-pc-check/9nzvl19n7cnc?rtc=1#activetab=pivot:overviewtab) -App auf Ihrem Computer ausführen, erhalten Sie einen Bericht darüber, ob Ihr PC für die Ausführung bereit ist. Wir haben bestimmte Details zu den in den folgenden Abschnitten aufgeführten Abschnitten herausgestellt.

Bevor Sie fortfahren, stellen Sie sicher, dass Ihr Computer die Mindestanforderungen für die [PC-Hardware Kompatibilität](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) erfüllt, um gemischte Realität auszuführen.

## <a name="youre-good-to-go"></a>Das ist schon alles!

Gute Neuigkeiten: Ihr PC kann Windows Mixed Reality ausführen! Beachten Sie, dass es immer noch Abweichungen zwischen Computer Hardware und-Konfiguration gibt. die gemischte Realität ist daher auf jedem PC möglicherweise nicht identisch.

## <a name="supports-some-features"></a>Unterstützt einige Features

Ihr PC ist in der Lage, einige Windows Mixed Reality-Umgebungen auszuführen, bietet jedoch möglicherweise keine bestmögliche Erfahrung. Mögliche Nachteile sind das Einschließen von Grafiken, Leistungseinbußen für apps und Spiele, wobei einige Anwendungen und Spiele überhaupt nicht ausgeführt werden können. Wir haben Meldungen aufgelistet, die möglicherweise angezeigt werden, und wie Sie im folgenden beschrieben werden:

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Dieser PC verfügt über eine integrierte Grafikkarte mit einem RAM mit einem Kanal.

Integrierte Grafikkarten bieten die beste Windows Mixed Reality-Darstellung auf PCs mit Dual-Channel-RAM. Wenn Leistungsprobleme auftreten, führen Sie eine der folgenden Aktionen aus:

* Installieren Sie eine [kompatible diskrete Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines).
* Installieren Sie einen zusätzlichen RAM-Stick, um Dual-Channel-RAM zu erstellen.
* Wechseln Sie zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Dieser PC verfügt über eine Hybrid Grafik Konfiguration mit einem inkompatiblen PCIe-Link.

PCIe steht für die *Verbindung der Peripheriekomponenten, Express*. Dies ist die Verbindung, die von einem PC für die Kommunikation mit einer Grafikkarte verwendet wird. Ihre Konfiguration funktioniert möglicherweise, aber wenn Probleme auftreten, müssen Sie zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)wechseln.

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Der Grafiktreiber dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality

Versuchen Sie, einen neuen Grafiktreiber mithilfe von Windows Update herunterzuladen, indem Sie auf **Start > Einstellungen > Update & Sicherheit klicken > nach Updates suchen** , oder auf der Website Ihres PC-Herstellers oder Grafikkartenherstellers.

> [!div class="nextstepaction"]
> [Suchen nach Updates](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Wenn dies nicht funktioniert, müssen Sie eine [kompatible Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) hinzufügen oder zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)wechseln.

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Der Prozessor dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality

Der Prozessor Ihres PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality, da er nicht über genügend Kerne verfügt. Wenn Windows Mixed Reality nicht ordnungsgemäß ausgeführt wird, ersetzen Sie den Prozessor durch einen [kompatiblen](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) Computer, oder wechseln Sie zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Dieser PC verfügt möglicherweise nicht über eine kompatible USB-Konfiguration.

Wenn Probleme bei der Ausführung von Windows Mixed Reality auftreten, versuchen Sie Folgendes:

* Anschließen Sie das Headset an einen anderen USB-Anschluss, falls verfügbar.
* Wenn dies nicht funktioniert, deinstallieren Sie den aktuellen USB-Treiber Ihres PCs, und installieren Sie dann einen Microsoft-Treiber neu:

1. Wählen Sie **Start** aus, und geben Sie dann "Geräte-Manager" in das **Suchfeld** ein.
2. Wählen Sie **Geräte-Manager** aus den Ergebnissen aus.
3. Erweitern Sie die Kategorie für universelle serielle Buscontroller, sehen Sie sich die aufgeführten Geräte an, und deinstallieren Sie alle inkompatiblen Treiber.
    * Wenn die Liste ein Element "erweiterbares Host Controller" enthält, das nicht "Microsoft" am Ende des Geräte namens enthält, ist dieser Treiber nicht kompatibel mit Windows Mixed Reality. Sie müssen Sie deinstallieren. Zum Deinstallieren eines Treibers klicken Sie in der Liste mit der rechten Maustaste auf das Gerät, und wählen Sie **Gerät deinstallieren** Aktivieren Sie das Kontrollkästchen **Treibersoftware für dieses Gerät löschen** , und wählen Sie dann **deinstallieren** aus.
    * Wenn die Liste ein Element "erweiterbares Host Controller" enthält, das "etron" im Namen enthält, ist der USB-Controller nicht kompatibel mit Windows Mixed Reality. Sie müssen einen anderen USB-Anschluss auf dem PC verwenden oder einen anderen USB 3,0-Host Controller erwerben.
4. Starten Sie Ihren PC neu.
5. Kehren Sie zu Geräte-Manager zurück, und suchen Sie das Extensible Host Controller-Element erneut. Wenn Sie jetzt "Microsoft" am Ende des Geräte namens sehen, können Sie loslegen. Wenn nicht, wiederholen Sie die Schritte zur Deinstallation, um alle zusätzlichen nicht-Microsoft-Versionen des Treibers zu entfernen.

* Wenn dies immer noch nicht funktioniert, fügen Sie dem PC eine PCIe-USB-Karte hinzu.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Auf diesem PC ist Bluetooth 4,0 für Controller nicht vorhanden.

2018 und neuere Windows Mixed Reality-Headsets verfügen bereits über das integrierte Bluetooth, aber wenn Sie über ein älteres Headset verfügen, ist Bluetooth 4,0 für gemischte Reality-Motion-Controller erforderlich. Sie können Windows Mixed Reality weiterhin mit einem Xbox-Controller oder mit einer Maus und Tastatur verwenden, oder Sie können einen USB-Bluetooth-Adapter verwenden, um Motion-Controller mit Ihrem PC zu verbinden. [Empfohlene Adapter anzeigen](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>Abhängig von Ihrem Headset benötigen Sie möglicherweise einen Bluetooth-Adapter für die Verwendung von Motion-Controllern.

Für einige Headsets ist Bluetooth integriert, sodass Controller direkt mit den Headsets gekoppelt werden können. Andere erfordern ein Bluetooth-Radio im PC (oder ein separates Dongle) zur Verwendung von Bewegungs Controllern. Weitere Informationen finden Sie auf [der Seite Empfohlene Adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) .

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Dieser PC verfügt über keinen selbst gestützten USB-Anschluss.

Ein selbstgesteuerter USB 3,0-Port ist erforderlich, um ein Windows Mixed Reality-Headset zu verbinden. Stellen Sie eine Verbindung zwischen einem USB 3,0-Computer und dem PC her, und verwenden Sie diesen zum Verbinden Ihres Headsets.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>Die Grafikkarte dieses PCs funktioniert nicht mit Windows Mixed Reality

Die Grafikkarte dieses PCs ist nicht kompatibel mit Windows Mixed Reality. Sie müssen eine [kompatible Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) hinzufügen oder zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)wechseln.

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>Der Grafiktreiber dieses PCs funktioniert nicht mit Windows Mixed Reality

Der Grafiktreiber dieses PCs funktioniert nicht mit Windows Mixed Reality. Versuchen Sie, einen neuen Grafiktreiber mithilfe von Windows Update herunterzuladen, indem Sie auf **Start > Einstellungen > Update & Sicherheit klicken > auf Updates überprüfen** oder auf die Website Ihres PC-Herstellers oder Grafikkartenherstellers klicken.

> [!div class="nextstepaction"]
> [Suchen nach Updates](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Wenn dies nicht funktioniert, müssen Sie eine [kompatible Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) hinzufügen oder zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)wechseln.

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>Der Prozessor dieses PCs funktioniert nicht mit Windows Mixed Reality

Der Prozessor des PCs unterstützt keine AVX/popcnt-Anweisungen. Zum Ausführen von Windows Mixed Reality müssen Sie es durch eine [kompatible Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) ersetzen oder zu einem kompatiblen PC wechseln.

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Dieser PC verfügt nicht über genügend freien Speicherplatz, um Windows Mixed Reality auszuführen.

Für Windows Mixed Reality sind 10 GB freier Speicherplatz für Setup und optimale Leistung erforderlich. Löschen Sie Speicherplatz auf dem Laufwerk, und versuchen Sie dann erneut, die Einstellungen zu starten.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Auf diesem PC wird eine Edition von Windows ausgeführt, die Windows Mixed Reality nicht unterstützt.

Windows Mixed Reality funktioniert unter Windows 10 Home und Windows 10 pro. Sie müssen eine dieser Editionen installieren, um Windows Mixed Reality zu verwenden.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Auf diesem PC wird nicht die neueste Version von Windows 10 ausgeführt.

Für Windows Mixed Reality ist das Windows 10 Fall Creators Update erforderlich. [Aktualisieren Sie Ihren PC](https://support.microsoft.com/help/4028685) , und wiederholen Sie den Vorgang.

### <a name="this-pc-has-no-usb-30-port"></a>Dieser PC hat keinen USB 3,0-Port.

Sie benötigen einen USB 3,0-Port, um ein Windows Mixed Reality-Headset zu verbinden. Wenn Sie einen Desktop-PC verwenden, fügen Sie eine PCIe-USB-Karte hinzu. Wenn Sie einen Laptop verwenden, müssen Sie zu einem [kompatiblen PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)wechseln.

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Sie können diese APP nicht über Remote Desktop ausführen.

Um Windows Mixed Reality verwenden zu können, benötigen Sie einen PC mit einem verbundenen Monitor. Wenn Sie einen virtuellen Computer verwenden oder über keinen Monitor verfügen, versuchen Sie, einen virtuellen Anzeige Adapter zu verwenden. Dabei handelt es sich um ein Gerät, das in den Display Port des PCs eingebunden und eine Computer Anzeige emuliert.

## <a name="getting-the-best-performance"></a>Erzielen der besten Leistung

Einige Hardware Konfigurationen können bei Windows Mixed Reality zu Leistungsproblemen führen. Bei Problemen wie dem langsamen Laden, der visuellen Darstellung von visuellen Elementen oder der schlechten visuellen Qualität sollten Sie diese häufig auftretenden Korrekturen ausprobieren:

* Schließen Sie alle geöffneten apps, die auf Ihrem PC-Desktop ausgeführt werden.
* Wenn Sie einen USB-C-oder DisplayPort für den HDMI-Adapter verwenden, versuchen Sie es mit einem anderen. Empfohlene Adapter anzeigen
* Wenn zusätzliche Monitore mit der Grafikkarte des PCs verbunden sind, trennen Sie Sie.
* Versuchen Sie, einige unterschiedliche Mixed Reality-Apps aus dem Windows Store herunterzuladen – einige funktionieren möglicherweise besser mit der Einrichtung Ihres Computers.

> [!NOTE]
> Wenn eine Meldung angezeigt wird, die besagt, dass diese Hardwarekonfiguration möglicherweise mit Windows Mixed Reality funktioniert, aber noch nicht getestet wurde, können einige Leistungsprobleme auftreten, wenn Windows Mixed Reality für lange Sitzungen ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen

* [Die Community fragen](https://answers.microsoft.com)
* [Kontaktieren Sie uns zur Unterstützung](https://support.microsoft.com/contactus/)
* [Problembehandlung](troubleshooting-windows-mixed-reality.md)