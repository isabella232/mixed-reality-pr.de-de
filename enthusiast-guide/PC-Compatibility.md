---
title: Windows Mixed Reality-PC-Check-App
description: Erfahren Sie, wie Sie die Windows Mixed Reality PC Check-App suchen und verwenden, um die Kompatibilität Ihres PCs zu testen, bevor Sie ein Windows Mixed Reality-Headset erwerben.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, kompatibel, Kompatibilität, PC, Systemanforderungen
appliesto:
- Windows 10
ms.openlocfilehash: 464a2709600f7fff076053026797ce809b8fbf73
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340628"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality-PC-Check-App

Die **[Windows Mixed Reality PC Check](windows-mixed-reality-pc-check-app.md)** -APP ist die beste Möglichkeit, um sicherzustellen, dass Ihr PC für die Durchführung von Windows Mixed Reality bereit ist.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Nachdem Sie die app ausgeführt haben, erhalten Sie eine der folgenden Meldungen:

* **Das ist schon alles.** Ihr PC verfügt über die Möglichkeiten, Windows Mixed Reality auszuführen.
* **Sie sind fast da.** Diese PCs können Windows Mixed Reality ausführen, einige Features sind jedoch möglicherweise eingeschränkt.
* **Gemischte Realität kann nicht ausgeführt werden.** Dieser PC erfüllt nicht die Mindestanforderungen für die Durchführung von Windows Mixed Reality.

Anschließend erhalten Sie eine Analyse Ihres PCs mit der erforderlichen Hardware, den Treibern und dem Betriebssystem.
![Screenshot der Windows Mixed Reality-PC-Überprüfung](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Symbol</th><th>Bedeutung</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Der PC übergibt das erforderliche Element.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Möglicherweise gibt es für die jeweilige Anforderung Probleme mit Ihrem PC. Wenn Probleme auftreten, müssen Sie möglicherweise eine Problembehandlung oder einen Upgrade Ihres PCs durchführen.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Der PC erfüllt die Anforderungen für das angegebene Element nicht.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Hilfe zu den Ergebnissen der Windows Mixed Reality-PC-Prüfung

Wenn Sie Windows Mixed Reality einrichten oder die Windows Mixed Reality-PC-Check-App auf Ihrem Computer ausführen, erhalten Sie einen Bericht darüber, ob Ihr PC bereit ist, ihn auszuführen. Im folgenden finden Sie einige Details dazu, was möglicherweise angezeigt wird.

### <a name="youre-good-to-go"></a>![Das ist schon alles!](images/glyph-succeeded.png)

Gute Neuigkeiten – auf Ihrem PC kann Windows Mixed Reality ausgeführt werden. Beachten Sie aber, dass es immer noch Abweichungen zwischen Computer Hardware und Konfiguration gibt. die gemischte Realität ist daher auf jedem PC möglicherweise nicht identisch.

>[!NOTE]
>Wenn eine Meldung angezeigt wird, die besagt, dass diese Hardwarekonfiguration möglicherweise mit Windows Mixed Reality funktioniert, aber noch nicht getestet wurde, können einige Leistungsprobleme auftreten, wenn Windows Mixed Reality für lange Sitzungen ausgeführt wird.

### <a name="youre-nearly-there"></a>![Sie sind fast da.](images/glyph-warning.png)

Ihr PC sollte in der Lage sein, Windows Mixed Reality auszuführen, bietet jedoch möglicherweise nicht die beste Möglichkeit. Grafiken können verzögert werden, einige apps und Spiele funktionieren möglicherweise nicht gut, und einige werden möglicherweise gar nicht ausgeführt.

Im folgenden finden Sie die Nachrichten, die Sie möglicherweise sehen, und was Sie zu tun haben:

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Dieser PC verfügt über eine integrierte Grafikkarte mit einem RAM mit einem Kanal.

Integrierte Grafikkarten bieten die beste Windows Mixed Reality-Darstellung auf PCs mit Dual-Channel-RAM. Wenn Leistungsprobleme auftreten, führen Sie eine der folgenden Aktionen aus:

* Installieren Sie eine [kompatible diskrete Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Installieren Sie einen zusätzlichen RAM-Stick, um Dual-Channel-RAM zu erstellen.
* Wechseln Sie zu einem [kompatiblen PC](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Dieser PC verfügt über eine Hybrid Grafik Konfiguration mit einem inkompatiblen PCIe-Link.

PCIe steht für die *Verbindung der Peripheriekomponenten, Express*. Dies ist die Verbindung, die von einem PC für die Kommunikation mit einer Grafikkarte verwendet wird. Ihre Konfiguration funktioniert möglicherweise, aber wenn Probleme auftreten, müssen Sie zu einem [kompatiblen PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)wechseln.

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Der Grafiktreiber dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality

Wenn Probleme auftreten, versuchen Sie, einen neuen Grafiktreiber mithilfe Windows Update herunterzuladen ( **Starten Sie > Einstellungen > aktualisieren & Sicherheit > suchen Sie nach Updates** ), oder wechseln Sie zur Website Ihres PC-Herstellers bzw. Grafikkartenherstellers.

Wenn dies nicht funktioniert, müssen Sie eine [kompatible Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) hinzufügen oder zu einem [kompatiblen PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)wechseln.

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Der Prozessor dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality

Der Prozessor dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality, da er nicht über genügend Kerne verfügt. Wenn Windows Mixed Reality nicht ordnungsgemäß ausgeführt wird, ersetzen Sie den Prozessor durch einen [kompatiblen](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) Computer, oder wechseln Sie zu einem [kompatiblen PC](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Dieser PC verfügt möglicherweise nicht über eine kompatible USB-Konfiguration.

Wenn Probleme bei der Ausführung von Windows Mixed Reality auftreten, versuchen Sie Folgendes:

* Anschließen Sie das Headset an einen anderen USB-Anschluss, falls verfügbar.
* Wenn dies nicht funktioniert, deinstallieren Sie den aktuellen USB-Treiber Ihres PCs, und installieren Sie dann einen Microsoft-Treiber neu:

1. Wählen Sie **Start** aus, und geben Sie dann **"Geräte-Manager"** in das Suchfeld ein.
1. Wählen Sie **Geräte-Manager** aus den Ergebnissen aus.
1. Erweitern Sie die Kategorie für universelle serielle Buscontroller, sehen Sie sich die aufgeführten Geräte an, und deinstallieren Sie alle inkompatiblen Treiber. 
 * Wenn die Liste ein Element "erweiterbares Host Controller" enthält, das nicht "Microsoft" am Ende des Geräte namens enthält, ist dieser Treiber nicht kompatibel mit Windows Mixed Reality. Sie müssen Sie deinstallieren. Zum Deinstallieren eines Treibers klicken Sie in der Liste mit der rechten Maustaste auf das Gerät, und wählen Sie **Gerät deinstallieren** Aktivieren Sie das Kontrollkästchen **Treibersoftware für dieses Gerät löschen** , und wählen Sie dann **deinstallieren** aus.
 * Wenn die Liste ein Element "erweiterbares Host Controller" enthält, das "etron" im Namen enthält, ist der USB-Controller nicht kompatibel mit Windows Mixed Reality. Sie müssen einen anderen USB-Anschluss auf dem PC verwenden oder einen anderen USB 3,0-Host Controller erwerben.
1. Starten Sie Ihren PC neu. 
1. Kehren Sie zu Geräte-Manager zurück, und suchen Sie das Extensible Host Controller-Element erneut. Wenn Sie jetzt "Microsoft" am Ende des Geräte namens sehen, können Sie loslegen. Wenn nicht, wiederholen Sie die Schritte zur Deinstallation, um alle zusätzlichen nicht-Microsoft-Versionen des Treibers zu entfernen.
* Wenn dies immer noch nicht funktioniert, fügen Sie dem PC eine PCIe-USB-Karte hinzu.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Dieser PC verfügt nicht über Bluetooth 4,0 für Controller.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Dieser PC verfügt über keinen selbst gestützten USB-Anschluss.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Dieser PC sollte funktionieren, aber Sie haben die beste Leistung bei einem hochleistungsfähigen Intel®-Prozessor.

### <a name="cant-run-mixed-reality"></a>![Gemischte Realität kann nicht ausgeführt werden](images/glyph-error.png)

 [Hilfe zu den Ergebnissen der Windows Mixed Reality-PC-Prüfung](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
