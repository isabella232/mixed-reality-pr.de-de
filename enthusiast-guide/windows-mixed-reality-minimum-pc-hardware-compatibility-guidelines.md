---
title: Windows Mixed Reality PC-Kompatibilitätsrichtlinien
description: Übersichtsdiagramm mit den Mindestanforderungen an das PC-System für die Kompatibilität mit Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Ultra, kompatibel, Kompatibilität, Systemanforderungen, PC
appliesto:
- Windows 10
ms.openlocfilehash: e73b00dcf8d6974f06c22c3b0ab0771a8e1a5969
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143335"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality mindestens erforderliche Richtlinien für die PC-Hardwarekompatibilität

## <a name="features-and-experiences"></a>Features und Erfahrungen

Windows 10 unterstützt Windows Mixed Reality verschiedenen Headsets auf einer Vielzahl von PC-Hardwarekomponenten.  Die Leistung Ihres PCs bestimmt, welche Erfahrungen Sie haben können.
Mit PCs mit höherem End erhalten Sie einige zusätzliche Funktionen und Features:

* Ansprechendere Visuals und eine höhere Aktualisierungsrate.
* Weitere Apps und Erfahrungen– einschließlich der grafikintensivsten Spiele.
* Ein "Spiegel"-Fenster auf Ihrem Desktop, das zeigt, was In Mixed Reality angezeigt wird.
* Zeichnen Sie Videos und Fotos Ihrer Mixed Reality-Erfahrungen auf, und teilen Sie sie.

## <a name="minimum-pc-hardware-guidelines"></a>Richtlinien für die PC-Hardware

Überprüfen Sie, ob Ihr PC Windows Mixed Reality kann, indem Sie die unten angegebenen Hardwarerichtlinien lesen und die [Mixed Reality-Portal](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) ausführen.

Denken Sie daran, dass Ihre Leistung abhängig von Ihrer genauen Einrichtung variiert. Sie müssen auch sicherstellen, dass Ihr [](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) PC über die richtigen Ports für das Windows Mixed Reality immersive Headset verfügt, das Sie verwenden.

>[!NOTE]
>Richtlinien für Entwicklungs-PCs sind höher als die für PCs von Kunden, auf denen Mixed Reality-Apps ausgeführt werden. Wenn Sie Mixed Reality-Entwickler sind, finden Sie [weitere Informationen unter Empfohlene Entwicklungs-PC-Spezifikationen.](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)

## <a name="mixed-reality-portal-app"></a>Mixed Reality-Portal-App

[Mixed Reality-Portal](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) ist die beste Möglichkeit, um sicherzustellen, dass Ihr PC bereit für die Ausführung Windows Mixed Reality.

Nach dem Ausführen der App erhalten Sie eine der folgenden Meldungen:

* **Sie können losgehen.**  Ihr PC ist bereit zum Ausführen von Mixed Reality-Spielen und -Erfahrungen.
* **Unterstützt einige Features.** Ihr PC kann einige Mixed Reality-Erfahrungen ausführen.
* **Mixed Reality kann nicht ausgeführt werden.** Dieser PC erfüllt nicht die Mindestanforderungen, die zum Ausführen von Windows Mixed Reality.

Anschließend erhalten Sie eine Analyse Ihres PCs mit der erforderlichen Hardware, den Treibern und dem Betriebssystem.
![Screenshot der PC-Überprüfung für Windows Mixed Reality](images/screenshot-mr-pc-check.jpg)

<table>
<tr>
<th>Symbol</th><th>Bedeutung</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Ihr PC übergibt das erforderliche Element.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Möglicherweise gibt es probleme mit Ihrem PC für die gegebene Anforderung. Wenn Probleme auft kommen, müssen Sie möglicherweise Probleme mit Ihrem PC beheben oder ein Upgrade durchführen.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Ihr PC erfüllt nicht die Anforderungen für das angegebene Element.</td>
</tr>
</table>

 [Erhalten von Hilfe zu Mixed Reality-Portal Ergebnissen](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>Kompatibilitätsrichtlinien

> [!IMPORTANT]
> Wir werden diese Richtlinien für die PC-Kompatibilität aktualisieren und möglicherweise Windows Mixed Reality aktualisieren. Überprüfen Sie regelmäßig die aktuellen Richtlinien und Anforderungen.

### <a name="high-resolution-headset-requirements"></a>Anforderungen an high-resolution headset

Aufgrund der höheren Auflösung gelten die folgenden Anforderungen für die HP Reverb G1-, G2- und Omnicept-Produktlinien, um eine optimale Auflösung mit 90 Hz und vollständiger Auflösung sicherzustellen:

<ul>
<li> Intel Core i5, i7, Intel Intel E3-1240 v5, gleichwertig oder besser. AMD Amd Amd 5 äquivalent oder besser. </li>
<li> NVIDIA GeForce GTX 1080, AMD Amd RX 5700, gleichwertig oder besser </li>
<li> Arbeitsspeicher: 8 GB RAM oder mehr </li>
<li> 1x Anzeigeport 1.3 </li>
<li> 1x USB 3.0 Typ-C mit Stromversorgung (oder enthaltener Netzadapter)</li>
<li> Windows 10 Update vom Mai 2019 oder höher </li>
</ul>

**Alle anderen WMR-kompatiblen Headsets** <br>
Beachten Sie für alle anderen HMDs die folgenden Anforderungen:

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 90Hz-PCs</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 60Hz-PCs</th>
</tr><tr>
    <td style="vertical-align: middle">Betriebssystem</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 Fall Creators Update (RS3) oder höher: Home, Pro, Business, Education.<br/>    (<b>Hinweis:</b>Nicht unterstützt für N Versionen oder Windows 10 Pro im S-Modus)</td>
</tr><tr>
    <td style="vertical-align: middle">Prozessor</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (4. Generation), Quad-Core (oder besser) <br>AMD Amd Amd 5 1400 mit 3,4 GHz (Desktop), Quad-Core (oder besser)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (mobil der 7. Generation), Dual-Core mit aktivierter Intel Hyper-Threading Technology (oder besser) <br>AMD Amd Amd 5 1400 mit 3,4 GHz (Desktop), Quad-Core (oder besser)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 (oder besser)</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 Dual Channel (oder besser)</td>
</tr><tr>
    <td style="vertical-align: middle">Freier Speicherplatz</td>
    <td style="vertical-align: middle; text-align: center;">Mindestens 10 GB</td>
    <td style="vertical-align: middle; text-align: center;">Mindestens 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">Grafikkarte</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul>
            <li>NVIDIA GTX 1060 (oder höher) DX12-fähige diskrete GPU</li>
            <li>AMD RX 470/570 (oder höher) DX12-fähige diskrete GPU </li>
            </ul>
            <b>Hinweis:</b> GPU muss in einem PCIe 3.0 x4+ Link-Slot gehostet werden </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>Integrierte Intel HD Graphics 620 (oder höher) DX12-fähige integrierte GPU <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(überprüfen Sie, ob Ihr Modell größer ist)</a></li>
        <li>NVIDIA MX150 (oder höher) diskrete GPU</li>
        <li>Nvidia GeForce GTX 1050 Diskrete GPU</li>
        <li>Diskrete NVIDIA 965M-GPU</li>
        <li>AMD Rx Rx 460/560</li>
        </ul>
        <b>Hinweis:</b> Ältere Intel-GPUs wie HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx und 6xxx werden nicht unterstützt.
    </td>
</tr><tr>
    <td style="vertical-align: middle">Grafiktreiber</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows Display Driver Model (WDDM) 2.2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Grafikanzeigeport</a></td>
    <td style="vertical-align: middle; text-align: center;">MSI 2.0 oder DisplayPort 1.2</td>
    <td style="vertical-align: middle; text-align: center;">MSI 1.4 oder DisplayPort 1.2</td>
</tr><tr>
    <td style="vertical-align: middle">Anzeige</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Verbundene externe oder integrierte VGA-Anzeige (800 x 600) (oder höher)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">USB-Konnektivität</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 </td>
</tr><tr>
    <td style="vertical-align: middle">Bluetooth-Konnektivität (für <a href="controllers-in-wmr.md">Motion-Controller)</a></td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4.0</td>
</tr><tr>
    <td style="vertical-align: middle">Erwartete Headsetframerate</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">Power</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0-Anschlüsse</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0-Anschlüsse</td>
</tr>
</table>

**Weitere Informationen:**

* Größere Laptops mit Bildschirmen von mindestens 15" bieten die beste Lösung.
* Hybridgrafikkonfigurationen sind nur mit Windows Mixed Reality 90Hz kompatibel. Der diskrete Grafikkarte in einer beliebigen Hybridkonfiguration muss alle Anforderungen erfüllen, die in den Windows Mixed Reality Richtlinien für diskrete Grafikkarten aufgeführt sind.
* Wenn Sie über eine diskrete Grafikkarte verfügen, die Windows Mixed Reality 90Hz ausgeführt werden sollte, aber standardmäßig eine Aktualisierungsrate von 60Hz (60 Frames pro Sekunde) aufwies, verwenden Sie einen Full-Size DisplayPort to DEBIT 2.0-Adapter, um Ihr Headset einzustecken und eine Aktualisierungsrate von 90Hz zu aktivieren.
* Verschiedene Headsets erfordern möglicherweise unterschiedliche [Hardwareports.](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) Stellen Sie daher sicher, dass Ihr PC über die richtigen Ports oder adapters verfügt, um eine Verbindung mit Ihrem Headset herzustellen.

>[!NOTE]
>Diskrete und integrierte Grafikhardware, die nicht den mindestens bestätigten Spezifikationen entspricht, wurde nicht getestet, bestätigt oder für Windows Mixed Reality optimiert und funktioniert möglicherweise nicht ordnungsgemäß oder überhaupt nicht.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality und Surface

Für die beste Windows Mixed Reality auf einem Surface-Gerät empfehlen wir das neueste SurfaceBook (15"), das mindestens mit NVIDIA GeForce GTX 1060 GB und 16 GB RAM konfiguriert ist.  Diese Konfiguration unterstützt alle Windows Mixed Reality Features und wurde auf Windows Mixed Reality getestet.  Die neuesten Surface Book (13.5"), Surface Studio, Surface Laptop und Surface Pro (2017) unterstützen alle einige Windows Mixed Reality Features, wenn sie mit einer Intel Core i5-CPU (oder höher) und mindestens 8 GB RAM konfiguriert sind.

**Anforderungen:**

* Surface-Produkte erfordern Treiberupdates, um mit Windows Mixed Reality kompatibel zu sein. Diese Treiber können auf Ihrer Oberfläche installiert werden, indem Sie zu **Einstellungen > Update und Sicherheit > Nach Updates suchen.**
* Surface-Produkte erfordern einen [Adapter](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) vom Videoport (Mini DisplayPort oder USB-C, abhängig vom Surface-PC) bis ZUEGE 2.0 für Windows Mixed Reality Headsets. Die neueste Version des Surface-Mini-DisplayPort mit DEM AV-Adapter IST mit DER VERSION 2.0 kompatibel (die ältere Version ist nicht). Auf ähnliche Weise ist der <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">Surface USB-C-to-ADAPTER</a> auch mit DEM STANDARD 2.0 kompatibel.

## <a name="see-also"></a>Weitere Informationen

* [Die Community fragen](https://answers.microsoft.com)
* [Wenden Sie sich an uns, um Support zu erhalten.](https://support.microsoft.com/contactus/)
* [Empfohlene Adapter für Windows Mixed Reality PCs](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
