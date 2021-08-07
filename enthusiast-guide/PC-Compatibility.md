---
title: Windows Mixed Reality PC Check-App
description: Hier erfahren Sie, wie Sie die app Windows Mixed Reality PC Check finden und verwenden, um die Kompatibilität Ihres PCs zu testen, bevor Sie ein Windows Mixed Reality Headset erwerben.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, kompatibel, Kompatibilität, PC, Systemanforderungen
appliesto:
- Windows 10
ms.openlocfilehash: 463e7dfc2c95ed9efc70a87ebbb0dac08b134251401a1114f3b9a364aa197073
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188044"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality PC Check-App

Die **[app Windows Mixed Reality PC Check](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** ist die beste Möglichkeit, um sicherzustellen, dass Ihr PC für die Ausführung Windows Mixed Reality bereit ist. Die app Windows Mixed Reality PC Check funktioniert nur auf PCs, auf Windows 10 Version 1607 installiert ist. Um Ihre Version von Windows zu überprüfen, geben Sie in der Suchleiste "winver" ein, und führen Sie den Befehl aus. Bei Windows 10 Versionen vor 1607 wird die App weiterhin im Store angezeigt, aber Sie erhalten einen Fehler, wenn Sie versuchen, sie zu installieren.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Nach dem Ausführen der App erhalten Sie eine der folgenden Meldungen:

* **Sie können loslassen.** Ihr PC verfügt über die Benötigten, um Windows Mixed Reality auszuführen.
* **Sie sind fast da.** Dieser PC kann Windows Mixed Reality ausgeführt werden, aber einige Features sind möglicherweise eingeschränkt.
* **Mixed Reality kann nicht ausgeführt werden.** Dieser PC erfüllt nicht die Mindestanforderungen, die für die Ausführung Windows Mixed Reality erforderlich sind.

Anschließend erhalten Sie eine Analyse Ihres PCs anhand der erforderlichen Hardware, Treiber und des Betriebssystems.
![Screenshot der PC-Überprüfung Windows Mixed Reality](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Symbol</th><th>Bedeutung</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Ihr PC übergibt das erforderliche Element.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Für die angegebene Anforderung können Probleme mit Ihrem PC auftreten. Wenn Probleme auftreten, müssen Sie möglicherweise Probleme mit Ihrem PC beheben oder ein Upgrade durchführen.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Ihr PC erfüllt nicht die Anforderungen für das angegebene Element.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Abrufen von Hilfe zu Windows Mixed Reality PC-Überprüfungsergebnissen

Sie erhalten einen Kompatibilitätsbericht, wenn Sie Windows Mixed Reality einrichten oder die app Windows Mixed Reality PC Check auf Ihrem Computer ausführen. Im Folgenden finden Sie einige Details dazu, was Ihnen möglicherweise angezeigt wird.

### <a name="youre-good-to-go"></a>![Sie können loslassen.](images/glyph-succeeded.png)

Gute Nachrichten: Ihr PC kann Windows Mixed Reality ausgeführt werden. Beachten Sie, dass die Computerhardware und -konfiguration immer noch variieren. Die Mixed Reality-Erfahrung ist möglicherweise nicht auf jedem PC identisch.

>[!NOTE]
>Wenn eine Meldung mit dem Hinweis angezeigt wird, dass diese Hardwarekonfiguration möglicherweise mit Windows Mixed Reality funktioniert, aber noch nicht getestet wurde, können beim Ausführen von Windows Mixed Reality für lange Sitzungen Leistungsprobleme auftreten.

### <a name="youre-nearly-there"></a>![Sie sind fast da.](images/glyph-warning.png)

Ihr PC sollte in der Lage sein, Windows Mixed Reality auszuführen, bietet aber möglicherweise nicht die bestmögliche Benutzererfahrung. Grafiken können verzögert werden, einige Apps und Spiele werden möglicherweise nicht gut ausgeführt, und einige werden möglicherweise überhaupt nicht ausgeführt.

Hier sind die Meldungen, die Ihnen möglicherweise angezeigt werden, und was sie zu tun haben:

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Dieser PC verfügt über eine integrierte Grafikkarte mit Einkanal-RAM

Integrierte Grafikkarten bieten die beste Windows Mixed Reality auf PCs mit Dualchannel-RAM. Bei Leistungsproblemen:

* Installieren Sie eine [kompatible diskrete Grafikkarte.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* Installieren Sie einen zusätzlichen RAM-Stick, um dualen Kanal-RAM zu erstellen.
* Wechseln Sie zu einem [kompatiblen PC.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Dieser PC verfügt über eine Hybridgrafikkonfiguration mit einem inkompatiblen PCIe-Link.

PCIe steht für *Peripheral Component Interconnect Express*. Dies ist die Verbindung, die ein PC für die Kommunikation mit einer Grafikkarte verwendet. Ihre Konfiguration funktioniert möglicherweise, aber wenn Probleme auftreten, müssen Sie zu einem [kompatiblen PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)wechseln.

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Der Grafiktreiber dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality

Wenn Probleme auftreten, laden Sie einen neuen Grafiktreiber herunter, indem Sie Windows Update **(> Einstellungen > Update & Security > Nach Updates suchen)** herunterladen oder zur Website Ihres PC-Herstellers oder Grafikkartenherstellers wechseln.

Wenn dies nicht funktioniert, müssen Sie eine [kompatible Grafikkarte](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) hinzufügen oder zu einem [kompatiblen PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)wechseln.

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Der Prozessor dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality

Der Prozessor dieses PCs funktioniert möglicherweise nicht gut mit Windows Mixed Reality, da er nicht über genügend Kerne verfügt. Wenn Windows Mixed Reality nicht gut ausgeführt wird, aktualisieren Sie auf einen [kompatiblen](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) , oder wechseln Sie zu einem [kompatiblen PC.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Dieser PC hat möglicherweise keine kompatible USB-Konfiguration.

Wenn beim Ausführen von Windows Mixed Reality Probleme auftreten:

* Schließen Sie Ihr Headset an einen anderen USB-Anschluss an, falls verfügbar.
* Wenn dies nicht funktioniert, deinstallieren Sie den aktuellen USB-Treiber Ihres PCs, und installieren Sie dann einen Microsoft-Treiber neu:

1. Wählen Sie **Starten** aus, und geben Sie dann **"Geräte-Manager"** in das Suchfeld ein.
1. Wählen Sie in den Ergebnissen **Geräte-Manager** aus.
1. Erweitern Sie die Kategorie für universelle serielle Bus-Controller, sehen Sie sich die aufgeführten Geräte an, und deinstallieren Sie alle inkompatiblen Treiber. 
 * Wenn die Liste am Ende des Gerätenamens ein Element "eXtensible Host Controller" ohne "Microsoft" enthält, ist der Treiber nicht mit Windows Mixed Reality kompatibel. Sie müssen es deinstallieren. Klicken Sie zum Deinstallieren eines Treibers mit der rechten Maustaste auf das Gerät in der Liste, und wählen **Sie Gerät deinstallieren** aus. Aktivieren Sie das Kontrollkästchen **Treibersoftware für dieses Gerät löschen,** und wählen Sie dann **Deinstallieren aus.**
 * Wenn die Liste ein Element "eXtensible Host Controller" enthält, das "E untereinander" im Namen enthält, ist dieser USB-Controller nicht mit Windows Mixed Reality kompatibel. Sie müssen einen anderen USB-Anschluss auf dem PC verwenden oder einen anderen USB 3.0-Hostcontroller erwerben.
1. Starten Sie Ihren PC neu. 
1. Kehren Sie zu Geräte-Manager zurück, und suchen Sie das Element eXtensible Host Controller erneut. Wenn am Ende des Gerätenamens jetzt "Microsoft" angezeigt wird, können Sie losgehen. Wenn dies nicht der Fall ist, wiederholen Sie die Deinstallationsschritte, um zusätzliche Nicht-Microsoft-Versionen des Treibers zu entfernen.
* Wenn dies immer noch nicht funktioniert, fügen Sie Ihrem PC eine PCIe-USB-Karte hinzu.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Dieser PC verfügt nicht über Bluetooth 4.0 für Controller.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Dieser PC verfügt nicht über einen selbst betriebenen USB-Anschluss.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Dieser PC sollte funktionieren, aber Sie verfügen über die beste Erfahrung mit einem leistungsstarken Intel®prozessor.

### <a name="cant-run-mixed-reality"></a>![Mixed Reality kann nicht ausgeführt werden](images/glyph-error.png)

 [Abrufen von Hilfe zu Windows Mixed Reality PC-Überprüfungsergebnissen](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
