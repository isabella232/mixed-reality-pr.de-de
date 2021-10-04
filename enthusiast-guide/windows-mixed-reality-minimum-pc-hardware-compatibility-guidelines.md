---
title: Windows Mixed Reality Richtlinien für die PC-Kompatibilität
description: Übersichtsdiagramm mit den Mindestanforderungen an das PC-System für die Kompatibilität mit Windows Mixed Reality.
author: qianw211
ms.author: v-qianwen
ms.date: 09/22/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Ultra, kompatibel, Kompatibilität, Systemanforderungen, PC
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: af3228e76bc9ce54ef877b67e8e85a3bde25e140
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436731"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality mindestens erforderliche Richtlinien für die PC-Hardwarekompatibilität

![Herobild der PC-Kompatibilität](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>Features und Erfahrungen

Windows 10 und Windows 11 Windows Mixed Reality verschiedene Headsets auf einer Vielzahl von PC-Hardwarekomponenten.  Die Leistung Ihres PCs bestimmt, welche Erfahrungen Sie haben können.
Mit PCs mit höherem End erhalten Sie einige zusätzliche Funktionen und Features:

* Ansprechendere Visuals und eine höhere Aktualisierungsrate.
* Weitere Apps und Erfahrungen– einschließlich der grafikintensivsten Spiele.
* Ein "Spiegel"-Fenster auf Ihrem Desktop, das zeigt, was In Mixed Reality angezeigt wird.
* Zeichnen Sie Videos und Fotos Ihrer Mixed Reality-Erfahrungen auf, und teilen Sie sie.

## <a name="minimum-pc-hardware-guidelines"></a>Richtlinien für die PC-Hardware

Überprüfen Sie, ob Ihr PC Windows Mixed Reality kann, indem Sie die unten angegebenen Hardwarerichtlinien lesen und die [Mixed Reality-Portal](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) ausführen.

Denken Sie daran, dass Ihre Leistung abhängig von Ihrer genauen Einrichtung variiert. Sie müssen auch sicherstellen, dass Ihr [](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) PC über die richtigen Ports für das Windows Mixed Reality immersive Headset verfügt, das Sie verwenden.

>[!NOTE]
>Richtlinien für Entwicklungs-PCs sind höher als die richtlinien für Die PCs von Kunden, auf denen Mixed Reality-Apps ausgeführt werden. Wenn Sie Mixed Reality-Entwickler sind, finden Sie [weitere Informationen unter Empfohlene Entwicklungs-PC-Spezifikationen.](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)

## <a name="mixed-reality-portal-app"></a>Mixed Reality-Portal-App

[Mixed Reality-Portal](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) ist die beste Möglichkeit, um sicherzustellen, dass Ihr PC bereit für die Ausführung Windows Mixed Reality.

Nach dem Ausführen der App erhalten Sie eine der folgenden Meldungen:

* **Sie können losgehen.**  Ihr PC ist bereit zum Ausführen von Mixed Reality-Spielen und -Erfahrungen.
* **Unterstützt einige Features.** Ihr PC kann einige Mixed Reality-Erfahrungen ausführen.
* **Mixed Reality kann nicht ausgeführt werden.** Dieser PC erfüllt nicht die Mindestanforderungen, die für die Ausführung von Windows Mixed Reality.

Anschließend erhalten Sie eine Analyse Ihres PCs mit der erforderlichen Hardware, den Treibern und dem Betriebssystem.
![Screenshot der Windows Mixed Reality PC-Überprüfung](images/screenshot-mr-pc-check.jpg)

| Symbol | Bedeutung |
| --- | --- |
| <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /> | Ihr PC übergibt das erforderliche Element. |
| <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /> | Möglicherweise gibt es probleme mit Ihrem PC für die angegebenen Anforderungen. Wenn Probleme auft kommen, müssen Sie möglicherweise Probleme mit Ihrem PC beheben oder ein Upgrade durchführen. 
| <img alt="Error" width="30" height="30" src="images/glyph-error.png" /> | Ihr PC erfüllt nicht die Anforderungen für das angegebene Element. |

 [Hilfe zu Mixed Reality-Portal Ergebnissen](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>Kompatibilitätsrichtlinien

> [!IMPORTANT]
> Wir werden diese Richtlinien für die PC-Kompatibilität aktualisieren und möglicherweise Windows Mixed Reality aktualisieren. Überprüfen Sie regelmäßig die aktuellen Richtlinien und Anforderungen.

### <a name="high-resolution-headset-requirements"></a>Anforderungen an high-resolution headset

Aufgrund der höheren Auflösung gelten die folgenden Anforderungen für die HP Reverb G1-, G2- und Omnicept-Produktlinien, um eine optimale Erfahrung mit 90 Hz und vollständiger Auflösung sicherzustellen:

- Intel Core i5, i7, Intel Xeon E3-1240 v5, gleichwertig oder besser. AMD Amd Amd 5 äquivalent oder besser.  
- NVIDIA GeForce GTX 1080, AMD Amd RX 5700, gleichwertig oder besser  
- Arbeitsspeicher: 8 GB RAM oder mehr  
- 1x Anzeigeport 1.3  
- 1x USB 3.0 Typ-C mit Stromversorgung (oder enthaltener Netzadapter) 
- Windows 10 Update mai 2019 oder höher  
 
**Alle anderen WMR-kompatiblen Headsets** <br>
Beachten Sie für alle anderen HMDs die folgenden Anforderungen:

| | Windows Mixed Reality PCs mit 90Hz | Windows Mixed Reality-PCs mit 60Hz |
| --- | --- | --- |
| Betriebssystem | Windows 10 Fall Creators Update (RS3) oder höher: Home, Pro, Business, Education. <br/>    (<b>Hinweis:</b>Nicht unterstützt für N Versionen oder Windows 10 Pro im S-Modus) |
| Prozessor | Intel Core i5 4590 (4. Generation), Quad-Core (oder besser) <br> AMD Amd Amd 5 1400 mit 3,4 GHz (Desktop), Quad-Core (oder besser) | Intel Core i5 7200U (mobil der 7. Generation), Dual-Core mit Intel Hyper-Threading Technology aktiviert (oder besser) <br> AMD Amd Amd 5 1400 mit 3,4 GHz (Desktop), Quad-Core (oder besser) |
| RAM | 8 GB DDR3 (oder besser) | 8 GB DDR3 Dual Channel (oder besser) |
| Freier Speicherplatz | Mindestens 10 GB | Mindestens 10 GB |
| Grafikkarte| <ul> <li>NVIDIA GTX 1060 (oder höher) DX12-fähige diskrete GPU </li> <li>AMD RX 470/570 (oder höher) DX12-fähige diskrete GPU </li> </ul> <br> <b>Hinweis:</b> GPU muss in einem PCIe 3.0 x4+ Link-Slot gehostet werden |  <ul>  <li>Integrierte integrierte INTEL HD Graphics 620 (oder höher) DX12-fähige integrierte GPU <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(überprüfen Sie,</a> ob Ihr Modell größer ist)</li> <li>NVIDIA MX150 (oder höher) diskrete GPU</li> <li>Nvidia GeForce GTX 1050 discrete GPU</li> <li>Nvidia 965M diskrete GPU</li> <li>AMD Amd RX 460/560</li> </ul> <b>Hinweis:</b> Ältere Intel GPUs wie HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx und 6xxx werden nicht unterstützt. |
| Grafiktreiber | Windows Display Driver Model (WDDM) 2.2 |  |
| [Grafikanzeigeport](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | DECODER 2.0 oder DisplayPort 1.2 | DECODER 1.4 oder DisplayPort 1.2 |
| Anzeige | Verbundene externe oder integrierte VGA-Anzeige (800x600) (oder besser) | 
| [USB-Konnektivität](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | USB 3.0 | |
| Bluetooth Konnektivität (für [Motion-Controller)](controllers-in-wmr.md) | Bluetooth 4.0 | |
| Erwartete Headset-Framerate | 90 Hz | 60 Hz |
| Power | USB 3.0-Anschlüsse | USB 3.0-Anschlüsse |

**Weitere Informationen:**

* Größere Laptops mit Bildschirmen von mindestens 15" bieten die besten Ergebnisse.
* Hybride Grafikkonfigurationen sind nur mit Windows Mixed Reality 90Hz kompatibel. Die diskrete Grafikkarte in jeder Hybridkonfiguration muss alle Anforderungen erfüllen, die in den Windows Mixed Reality für diskrete Grafikkarten aufgeführt sind.
* Wenn Sie über eine diskrete Grafikkarte verfügen, die mit Windows Mixed Reality 90Hz ausgeführt werden soll, aber standardmäßig eine Aktualisierungsrate von 60Hz (60 Frames pro Sekunde) verwendet wird, verwenden Sie einen DisplayPort-to-GRAPHICS 2.0-Adapter in voller Größe, um Ihr Headset einstecken und eine Aktualisierungsrate von 90Hz zu aktivieren.
* Unterschiedliche Headsets erfordern möglicherweise unterschiedliche [Hardwareports.](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) Stellen Sie daher sicher, dass Ihr PC über die richtigen Ports oder erforderlichen Adapter verfügt, um eine Verbindung mit Ihrem Headset herzustellen.

>[!NOTE]
>Diskrete und integrierte Grafikhardware, die die mindestens bestätigten Spezifikationen nicht erfüllt, wurde für Windows Mixed Reality nicht getestet, bestätigt oder optimiert und funktioniert möglicherweise nicht ordnungsgemäß oder überhaupt nicht.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality und Surface

Für eine optimale Windows Mixed Reality-Erfahrung auf einem Surface-Gerät empfehlen wir das neueste SurfaceBook (15), das mindestens mit nvidia GeForce GTX 1060 GB und 16 GB RAM konfiguriert ist.  Diese Konfiguration unterstützt alle Windows Mixed Reality Features und wurde auf Windows Mixed Reality.  Die neuesten Surface Book (13.5), Surface Studio, Surface Laptop und Surface Pro (2017) unterstützen alle einige Windows Mixed Reality-Features, wenn sie mit einer Intel Core i5-CPU (oder besser) und mindestens 8 GB RAM konfiguriert sind.

**Anforderungen:**

* Surface-Produkte erfordern Treiberupdates, damit sie mit den Windows Mixed Reality. Diese Treiber können auf Ihrer Surface installiert werden, indem Sie Einstellungen > update and security > Check for Updates (Nach Updates **suchen) gehen.**
* Surface-Produkte [](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) erfordern einen Adapter vom Videoport (Mini DisplayPort oder USB-C, je nach Surface-PC) bis zu Windows Mixed Reality HEADSETs. Die neueste Version des Surface Mini-DisplayPort to ANTIVIRUS AV Adapters ist mit ANTIVIRUS 2.0 kompatibel (die ältere Version ist nicht). Auf ähnliche Weise ist der <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">Surface USB-C-to-ADAPTER</a> auch mit DENEN 2.0 kompatibel.

## <a name="see-also"></a>Siehe auch

* [Die Community fragen](https://answers.microsoft.com)
* [Wenden Sie sich an uns, um Support zu erhalten.](https://support.microsoft.com/contactus/)
* [Empfohlene Adapter für Windows Mixed Reality PCs](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
