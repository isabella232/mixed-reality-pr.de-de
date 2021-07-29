---
title: Windows Mixed Reality Richtlinien für die PC-Kompatibilität
description: Übersichtsdiagramm, in dem die Mindestanforderungen an das PC-System für die Kompatibilität mit Windows Mixed Reality aufgeführt sind.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Ultra, kompatibel, Kompatibilität, Systemanforderungen, PC
appliesto:
- Windows 10
ms.openlocfilehash: b7c2b4b84440e7cdd22c2c0cd7d5f9830d55625f
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757032"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality Mindestrichtlinien für die PC-Hardwarekompatibilität

![Herobild zur PC-Kompatibilität](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>Features und Funktionen

Windows 10 unterstützt Windows Mixed Reality auf verschiedenen Headsets für eine Vielzahl von PC-Hardware.  Die Leistungsfähigkeit Ihres PCs bestimmt, welche Erfahrungen Sie haben können.
Mit PCs mit höheren Enden erhalten Sie einige zusätzliche Funktionen und Features:

* Präzise visuelle Elemente und eine höhere Aktualisierungsrate.
* Weitere Apps und Erfahrungen– einschließlich der grafikintensivsten Spiele.
* Ein "Spiegel"-Fenster auf Ihrem Desktop, das anzeigt, was in Mixed Reality angezeigt wird.
* Zeichnen Sie Videos und Fotos Ihrer Mixed Reality-Erfahrungen auf, und teilen Sie sie.

## <a name="minimum-pc-hardware-guidelines"></a>Richtlinien für die PC-Hardware

Überprüfen Sie anhand der unten aufgeführten Hardwarerichtlinien und ausführen der Mixed Reality-Portal-App, ob Ihr PC [Windows Mixed Reality](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) ausführen kann.

Denken Sie daran, dass Ihre Leistung je nach Ihrem genauen Setup variiert. Sie müssen auch sicherstellen, dass Ihr PC über die [richtigen Ports](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) für das Windows Mixed Reality immersive Headset verfügt, das Sie verwenden.

>[!NOTE]
>Richtlinien für Entwicklungs-PCs sind höher als die richtlinien für Consumer-PCs, auf denen Mixed Reality-Apps ausgeführt werden. Wenn Sie Mixed Reality-Entwickler sind, [finden Sie weitere Informationen unter Empfohlene PC-Spezifikationen](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)für die Entwicklung.

## <a name="mixed-reality-portal-app"></a>Mixed Reality-Portal-App

[Mixed Reality-Portal](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) ist die beste Möglichkeit, um sicherzustellen, dass Ihr PC für die Ausführung Windows Mixed Reality bereit ist.

Nach dem Ausführen der App erhalten Sie eine der folgenden Meldungen:

* **Sie können loslassen.**  Ihr PC ist bereit, Mixed Reality-Spiele und -Erfahrungen auszuführen.
* **Unterstützt einige Features.** Auf Ihrem PC können einige Mixed Reality-Erfahrungen ausgeführt werden.
* **Mixed Reality kann nicht ausgeführt werden.** Dieser PC erfüllt nicht die Mindestanforderungen, die für die Ausführung Windows Mixed Reality erforderlich sind.

Anschließend erhalten Sie eine Analyse Ihres PCs anhand der erforderlichen Hardware, Treiber und des Betriebssystems.
![Screenshot der PC-Überprüfung Windows Mixed Reality](images/screenshot-mr-pc-check.jpg)

<table>
<tr>
<th>Symbol</th><th>Bedeutung</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Ihr PC übergibt das erforderliche Element.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Für die angegebene Anforderung können Probleme mit Ihrem PC auftreten. Wenn Probleme auftreten, müssen Sie ihren PC möglicherweise beheben oder aktualisieren.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Ihr PC erfüllt nicht die Anforderungen für das angegebene Element.</td>
</tr>
</table>

 [Hilfe zu Mixed Reality-Portal Ergebnissen](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>Kompatibilitätsrichtlinien

> [!IMPORTANT]
> Wir werden diese Windows Mixed Reality PC-Kompatibilitätsrichtlinien aktualisieren und ggf. ergänzen. Überprüfen Sie regelmäßig die neuesten Richtlinien und Anforderungen.

### <a name="high-resolution-headset-requirements"></a>Headsetanforderungen mit hoher Auflösung

Aufgrund der höheren Auflösung gelten die folgenden Anforderungen für die Hp Reverb G1-, G2- und Omnicept-Produktreihen, um eine optimale Auflösung von 90 Hz und vollständiger Auflösung sicherzustellen:

<ul>
<li> Intel Core i5, i7, Intel Xeon E3-1240 v5, gleichwertig oder höher. AMD Amd- 5-Äquivalent oder höher. </li>
<li> NVIDIA GeForce GTX 1080, AMD Rx Rx 5700, gleichwertig oder höher </li>
<li> Arbeitsspeicher: 8 GB RAM oder mehr </li>
<li> 1x Anzeigeport 1.3 </li>
<li> 1x USB 3.0 Type-C with power delivery (or included power adapter) (1x USB 3.0 Type-C with power delivery (oder im Lieferumfang enthaltener Netzadapter)</li>
<li> Windows 10 Update Mai 2019 oder höher </li>
</ul>

**Alle anderen WMR-kompatiblen Headsets** <br>
Beachten Sie für alle anderen HMDs die folgenden Anforderungen:

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality PCs mit 90Hz</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 60-Hz-PCs</th>
</tr><tr>
    <td style="vertical-align: middle">Betriebssystem</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 Fall Creators Update (RS3) oder höher: Home, Pro, Business, Education.<br/>    (<b>Hinweis:</b>Wird für N Versionen oder Windows 10 Pro im S Modus nicht unterstützt)</td>
</tr><tr>
    <td style="vertical-align: middle">Prozessor</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (4. Generation), Quad-Core (oder höher) <br>AMD Amd Editions 5 1400 3,4 GHz (Desktop), Quad-Core (oder höher)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (mobil der 7. Generation), Dual-Core mit Intel Hyper-Threading Technology enabled (oder besser) <br>AMD Amd Editions 5 1400 3,4 GHz (Desktop), Quad-Core (oder höher)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 (oder höher)</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 Dual Channel (oder höher)</td>
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
        <li>Nvidia 965M diskrete GPU</li>
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
    <td style="vertical-align: middle">Bluetooth Konnektivität (für <a href="controllers-in-wmr.md">Motion-Controller)</a></td>
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
* Wenn Sie über eine diskrete Grafikkarte verfügen, die Windows Mixed Reality 90Hz ausgeführt werden sollte, aber standardmäßig eine Aktualisierungsrate von 60Hz (60 Frames pro Sekunde) aufwies, verwenden Sie einen Full-Size DisplayPort to INTRANET 2.0-Adapter, um Ihr Headset einzustecken und eine Aktualisierungsrate von 90Hz zu aktivieren.
* Verschiedene Headsets erfordern möglicherweise unterschiedliche [Hardwareports.](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) Stellen Sie daher sicher, dass Ihr PC über die richtigen Ports oder adapters verfügt, um eine Verbindung mit Ihrem Headset herzustellen.

>[!NOTE]
>Diskrete und integrierte Grafikhardware, die die mindestens bestätigten Spezifikationen nicht erfüllt, wurde für Windows Mixed Reality nicht getestet, bestätigt oder optimiert und funktioniert möglicherweise nicht ordnungsgemäß oder überhaupt nicht.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality und Surface

Für die beste Windows Mixed Reality-Erfahrung auf einem Surface-Gerät empfehlen wir das neueste SurfaceBook (15), das mindestens mit nvidia GeForce GTX 1060 GB und 16 GB RAM konfiguriert ist.  Diese Konfiguration unterstützt alle Windows Mixed Reality Features und wurde auf Windows Mixed Reality.  Die neuesten Surface Book (13.5), Surface Studio, Surface Laptop und Surface Pro (2017) unterstützen alle einige Windows Mixed Reality-Features, wenn sie mit einer Intel Core i5-CPU (oder besser) und mindestens 8 GB RAM konfiguriert sind.

**Anforderungen:**

* Surface-Produkte erfordern Treiberupdates, damit sie mit der Windows Mixed Reality. Diese Treiber können auf Ihrer Surface installiert werden, indem Sie Einstellungen > update and security > Check for Updates (Nach Updates **suchen) gehen.**
* Surface-Produkte [](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) erfordern einen Adapter vom Videoport (Mini DisplayPort oder USB-C, je nach Surface-PC) bis zu DEN 2.0 für Windows Mixed Reality Headsets. Die neueste Version des Surface Mini-DisplayPort to ANTIVIRUS AV Adapters ist kompatibel mit ANTIVIRUS 2.0 (die ältere Version ist dies nicht). Auf ähnliche Weise ist der <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">Surface USB-C-to-ADAPTER</a> auch mit DENEN 2.0 kompatibel.

## <a name="see-also"></a>Siehe auch

* [Die Community fragen](https://answers.microsoft.com)
* [Wenden Sie sich an uns, um Support zu erhalten.](https://support.microsoft.com/contactus/)
* [Empfohlene Adapter für Windows Mixed Reality PCs](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
