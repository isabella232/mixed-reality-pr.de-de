---
title: Softwareübersicht und Releaseverlauf
description: Eine Übersicht über die wichtigsten Softwarekomponenten für Windows Mixed Reality immersive Headsets und deren Releaseverlauf.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Softwarekomponenten, Releaseverlauf, Versionshinweise, Versionsverlauf
appliesto:
- Windows 10
ms.openlocfilehash: 51c13326d2ad8aebe164e64d0bfc380923a91d1be02cea840cec4addd062533f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219726"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Mixed Reality: Übersicht zur Software und Versionsverlauf

## <a name="introduction-to-mixed-reality-software"></a>Einführung in Mixed Reality Software

Windows Mixed Reality besteht aus den folgenden Hauptkomponenten von Software:

1. **Mixed Reality-Portal**, das die Haupterfahrung Windows Mixed Reality bietet
    * In Windows 10 Versionen 1709 und 1803 ist Mixed Reality-Portal eine wichtige Komponente des Windows 10-Betriebssystems, das über Windows aktualisiert wurde.
    * In Windows 10 Version 1809 und neuer wird Mixed Reality-Portal über die Microsoft Store aktualisiert.
2. Das **Mixed Reality Feature-on-Demand-Paket** (FOD), das bei der ersten Ausführung Mixed Reality-Portal automatisch heruntergeladen und installiert wird. Weitere Informationen zum FOD-Paket finden Sie [hier.](/windows/application-management/manage-windows-mixed-reality)
3. Das Mixed Reality-Headset und der Motion **Controller-Treiber**( auch als HoloLens Sensors-Treiber bezeichnet) ist das Schlüsseltreiberpaket, mit dem Windows Mixed Reality Headsets mit Windows Mixed Reality. Dies wird automatisch über Windows Update heruntergeladen und installiert, wenn Ihr Mixed Reality-Headset zum ersten Mal angeschlossen ist, und wird regelmäßig über Windows Update aktualisiert.
4. Die **Mixed Reality Motion Controller-Modelltreiber enthalten die 3D-Modelle der Mixed Reality-Motion-Controller, die für drittanbieterspezifische Mixed Reality sind. Dies wird automatisch über Windows Update heruntergeladen und installiert, wenn Ihre Mixed Reality-Motion-Controller zum ersten Mal mit Ihrem PC gekoppelt und über Windows Update aktualisiert werden.
5. **Windows 10 Version 1709 (Das Fall Creators Update)** oder eine neuere Version enthält wichtige Betriebssystemkomponenten und -technologien, die die Windows Mixed Reality

Die Windows Mixed Reality in SteamVR erfordert die folgende Software:

6. **SteamVR** wurde von der Valve Corporation entwickelt und gewartet, die Virtual Reality-Apps und -Spiele auf Steam ermöglicht. Weitere Informationen finden Sie [hier](https://go.microsoft.com/fwlink/?linkid=862788).
7. Die **Windows Mixed Reality für die Komponente "SteamVR",** die Eine Brücke zwischen "SteamVR" und Windows Mixed Reality. Weitere Informationen zu dieser Komponente finden Sie [auf der Seite Windows Mixed Reality für SteamVR.](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Verwalten Ihres Windows Mixed Reality Headsets:

8. Die **Geräte-Begleit-App,** die von den einzelnen Headsetherstellern entwickelt und verwaltet wird, bietet eine kurze Einführung in Ihr Windows Mixed Reality Headset. Auf Headsets mit integrierter Bluetooth-Funktion ermöglicht die Device Companion-App das Wiederherstellen von Motion Controllern in der Factory Bluetooth Kopplung. Einige Headsets (z. B. SamsungIgey und Samsung Geräte+) verwenden auch die Geräte-Begleit-App, um Firmwareupdates für Headsets vom Headsethersteller zu liefern. Diese App wird automatisch heruntergeladen, wenn Ihr Headset zum ersten Mal angeschlossen wird, und befindet sich im Windows Startmenü.

## <a name="windows-10-release-notes---may-2020"></a>Windows 10– Mai 2020

Das Windows 10 Update vom **Mai 2020 (v2004)** enthält neue Features für Windows Mixed Reality-Headsets (VR), z. B. die Möglichkeit, Win32-Anwendungen in der Mixed Reality Startumgebung. HoloLens (1. Generation) befindet sich in Long Term Servicing (LTS), und Wartungsupdates werden monatlich veröffentlicht.

Wenn Sie ein Upgrade auf die neueste PC-Version Windows Mixed Reality immersiven Headsets (VR) durchführen, öffnen Sie Einstellungen > **Update & Security,** und wählen Sie Nach **Updates suchen aus.** Auf einem Windows 10-PC können Sie das Windows 10 Update vom Mai **2020** auch manuell installieren, indem Sie Windows [Medienerstellungstool verwenden.](https://www.microsoft.com/software-download/windows10)

**Neueste Version für Desktop:** Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Updates für Windows Mixed Reality immersive Headsets

#### <a name="introducing-the-new-microsoft-edge"></a>Vorstellung des neuen Microsoft Edge

Wie [bereits angekündigt,](/windows/mixed-reality/new-microsoft-edge)haben wir Updates vorgenommen, um die Verwendung des neuen Microsoft Edge-Browsers in Windows Mixed Reality. Die neue Microsoft Edge übernimmt das open-source Chromium projekt, um eine bessere Webkompatibilität für Kunden und eine geringere Fragmentierung des Webs für alle Webentwickler zu schaffen. Es unterstützt auch WebXR, den neuen Standard zum Erstellen immersiver Weberfahrungen für VR-Headsets, statt WebVR.

#### <a name="improved-settings-for-wmr"></a>Verbesserte Einstellungen für WMR

Dank Ihres Feedbacks haben wir auf der Headset-Anzeigeseite Einstellungen hinzugefügt und verdeutlicht:

* **Visuelle Qualität meines Heims:** Das Ändern dieser Einstellungen wirkt sich nur auf die Mixed Reality Startumgebung (Haus an den Klippen und Skyloft) aus:

* **Passen Sie die Detailebene und die Qualität** der Effekte in der Mixed Reality Startumgebung an. Dies ändert einige der Renderingeffekte, die wir im Heim verwenden. Insbesondere die visuelle Qualität verschiedener Materialien (Wood, Concrete, so weiter) wird skaliert, wenn Sie diese Einstellung von niedrig in hoch ändern.

* **Ändern der Auflösung des** App-Fensters: Standardmäßig werden die meisten 2D-Fenster, die im Startfenster gestartet werden, mit einer Auflösung von 720 p gestartet. Sie können zwar die Größe horizontal & vertikal ändern, sie können jedoch auch alle bei 1080p starten lassen. Zuvor war diese Option als Option Sehr hoch (Beta) unter Visuelle Qualität verfügbar. Wir haben sie jetzt entsprechend als separate Einstellung aufgeteilt.

* **Erfahrungsoptionen:** Diese Optionen passen die Mixed Reality-Erfahrung an, um die Last auf Systemen zu reduzieren, bei denen die Hardware mit uneingeschränkten 90 FPS nicht mithalten kann. Sie können diese zusätzlichen Einstellungen explizit aktivieren oder deaktivieren oder die Option Let Windows decide and let our heuristics continue decide when toggle these toggle these on and off (Entscheidung treffen und unsere Heuristiken entscheiden lassen, wann diese aktiviert oder deaktiviert werden) auswählen.

* **Lösung:** Wenn Sie über ein hochauflösendes Headset wie HP Reverb verfügen, wird die Ausführung mit nativer Auflösung oder aus Leistungsgründen mit einer reduzierten Auflösung unterstützt. Frühere Headsets, z.B. samsung Und/oder Samsung, unterstützen nur eine einzelne Auflösung, sodass Sie diese Einstellung auf diesen Headsets nicht ändern können.

* **Bildfrequenz:** Sie können jetzt die Bildfrequenz der Headsetanzeige manuell festlegen oder Windows weiterhin seine Heuristik verwenden lassen, um zu bestimmen, ob 60 Hz oder 90 Hz besser geeignet ist.

* **Kalibrierung:** Wie zuvor können Sie Ihre IPD (Interpupillary Distance) anpassen, wenn sie von Ihrem Headset unterstützt wird.

* **Eingabewechsel:** Schalten Sie das Eingabefokuswechselverhalten (Win+Y) so um, dass es automatisch (basierend auf dem Feedback des Anwesenheitssensors) oder manuell erfolgt.

#### <a name="new-cortana-app"></a>Neue Cortana-App

Dieses Update für Windows enthält die neueste Version der Cortana-App, die derzeit nur in den USA verfügbar ist und bestimmte Mixed Reality-spezifische Befehle wie "Take a picture" und "Take a video" nicht mehr unterstützt. Sie können die neue Cortana verwenden, um Apps zu starten, und sie unterstützt auch neue produktivitätsorientierte Befehle wie "Wann ist meine nächste Besprechung?". oder "Senden Sie eine E-Mail <name> an , an die ich zu spät lauf."
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Zusätzliche Updates in verfügbar in 19041.546 (veröffentlicht im Oktober 2020)

Dieses monatliche Desktopwartungsupdate enthält die folgenden Änderungen für Windows Mixed Reality Geräte: 
* Reduziert Verzerrungen und Abweichungen in Windows Mixed Reality hmd-Displays (Head-Mounted Displays, HMD). 
* Unterstützung für zukünftige HP-Windows Mixed Reality Motion-Controller. 
* Ändert das Verhalten der Einstellung für die 90-Hz-Aktualisierungsrate in Windows Mixed Reality so, dass in bestimmten Fällen, in denen 90 Hz nicht erreicht werden kann, nicht mehr automatisch wieder auf 60 Hz umgeschaltet wird. 

#### <a name="help-us-improve"></a>Helfen Sie uns, uns zu verbessern!

Wir arbeiten ständig daran, die Kompatibilität zu verbessern.  Wenn Sie feststellen, dass Sich Ihre bevorzugte klassische Win32-Anwendung während des Windows Mixed Reality nicht ordnungsgemäß verhält, senden Sie feedback über unsere [Feedback-Hub](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

### <a name="prior-release-notes"></a>Vorherige Versionshinweise

* [Versionshinweise – Mai 2019](release-notes-may-2019.md)
* [Versionshinweise – Oktober 2018](release-notes-october-2018.md)
* [Versionshinweise – April 2018](release-notes-april-2018.md)
* [Versionshinweise – Oktober 2017](release-notes-october-2017.md)
* [Versionshinweise – August 2016](release-notes-august-2016.md)
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Mixed Reality des Headsets und des Motion Controller-Treibers ###

Dieser Treiber wird automatisch über Windows Update heruntergeladen und installiert. Downloadlinks werden jedoch inline bereitgestellt:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, Version 2004 (Update mai 2020) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 23. März 2021  | Kompatibel mit Windows 10 Version 1903 und neuer.<br/><ul><li>Aktualisieren Sie die Wickelrichtung des verdeckten Bereichsgitters, damit HP Reverb G2 mit anderen Headsets konsistent ist.</li><li>Verbesserungen der Visualqualität für die HP Reverb G2-Headsets.</li><li>Windows Mixed Reality der Headsetplattform und zuverlässigkeitsverbesserungen.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10. Dezember 2020  | Kompatibel mit Windows 10 Version 1903 und neuer.<br/><ul><li>Neue Controllerfirmware für den HP Controller, um ein Problem zu beheben, bei dem einige Controller über nicht funktionierende Trigger verfügen.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8. Oktober 2020  | Kompatibel mit Windows 10 Version 1903 und neuer.<br/><ul><li>Offizielle Unterstützung für HP Reverb G2, HP Omnicept und den neuen HP Controller.</li><li>Kleinere Anzeigekorrekturen für HP Reverb- und Samsung-Samsung-Headsets. (Erfordert [Betriebssystem-Build 19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) oder höher oder [Betriebssystem-Builds 18362.1110 und 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) oder höher).</li><li>Verbesserungen am Übergang des Computerleistungszustands vom Ruhezustand zur Reduzierung von SWW 1-4-Fehlern.</li><li>Windows Mixed Reality der Headsetplattform kleinere Korrekturen und Zuverlässigkeitsverbesserungen.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7\. Mai 2020      | Kompatibel mit Windows 10 Version 1903 und neuer.<br/><ul><li>Windows Mixed Reality headset platform minor fixes and reliability improvements (Kleinere Fehlerbehebungen und Zuverlässigkeitsverbesserungen für headset-Plattformen).</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, Version 1903 (Update mai 2019) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14. Oktober 2019      | Kompatibel mit Windows 10, Version 1809 und neuer.<br/><ul><li>Windows Mixed Reality kleinere Fehlerbehebungen für die Headsetplattform.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24. Juni 2019      | Kompatibel mit Windows 10, Version 1809 und neuer.<br/><ul><li>Windows Mixed Reality headset platform and reliability improvements around sleeping computers and power state transitions (Verbesserungen der Headsetplattform und Zuverlässigkeit von Energiesparcomputern und Energiezustandsübergängen).</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1\.Mai 2019      | Kompatibel mit Windows 10, Version 1809 und neuer.<br/><ul><li>Enthält firmware update for 2017 Acer, Asus, Dell, Cin, HP, Hpc, And Mediion Windows Mixed Reality Headsets. Dieses Firmwareupdate verbessert die Kompatibilität und Zuverlässigkeit der Headsetanzeige mit bestimmten Grafikkarten oder Grafiktreibern.</li><li>Windows Mixed Reality headset platform and reliability improvements (Verbesserungen der Headsetplattform und Zuverlässigkeit)</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, Version 1803 (Update april 2018) und Version 1809 (Update von Oktober 2018) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2. Januar 2019      | Kompatibel mit Windows 10, Version 1803 und höher.<br/><ul><li>Jitter- und Stutterkorrekturen für die Headsetnachverfolgung</li><li>Fehlerbehebungen für die Zuverlässigkeit des Taschenlampenmodus</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1. Oktober 2018      | Erste öffentliche Version des Treibers für Windows 10, Version 1809.<br/>Kompatibel mit Windows 10, Version 1803 und höher.<br/><ul><li>Aktiviert neue Windows Mixed Reality Features wie den Taschenlampenmodus in Windows 10, Version 1809</li><li>Verbesserungen der Nachverfolgung und Zuverlässigkeit von Headsets</li><li>Motion Controller-Nachverfolgung und Leistungsverbesserungen</li><li>USB-Leistung und -Verbesserungen</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27. April 2018      | Erste öffentliche Version des Treibers für Windows 10, Version 1803<br/> <ul><li>Verbesserungen der Nachverfolgung und Zuverlässigkeit von Headsets</li><li>Motion Controller-Nachverfolgung und Leistungsverbesserungen</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, Version 1709 (Fall Creators Update) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6. Februar 2018    | <ul><li>Offizielle Unterstützung für 3Glasses Blubur S2 Mixed Reality Headset</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19. Dezember 2017   | <ul><li>Löst hid-Problem, das *zum* Fehlercode 2181038087-7 auf einigen PCs führt.</li><li>Verschiedene Stabilitäts- und Zuverlässigkeitskorrekturen</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5\. Dezember 2017    | <ul><li>Verbesserte Headset-Nachverfolgung</li><li>Verbesserung der Reaktionsfähigkeit des Motion Controller-Touchpads</li><li>Löst ein Problem, bei dem die Treiberinstallation manchmal fehlschlägt</li><li>Verschiedene Stabilitäts- und Zuverlässigkeitskorrekturen</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21. November 2017   | <ul><li>Löst ein Problem, das dazu geführt hat, dass Headsetanzeigen während der Verwendung manchmal schwarz sind</li><li>Löst ein Problem, das manchmal dazu geführt hat, dass Motion Controllers nicht mehr angezeigt werden</li><li>Leistungsverbesserungen des Präsenzsensors für das Dell Visor-Headset</li><li>Verschiedene Stabilitäts- und Zuverlässigkeitskorrekturen</li></ul> |
   | 10.0.16299.1036  | 7. November 2017    | <ul><li>Motion Controller throwing improvements (Bewegungscontroller löst Verbesserungen aus:<ul><li>Die Geschwindigkeit wird jetzt ordnungsgemäß gemeldet, wenn die Positionsgenauigkeit ungefähr ist, sodass Sie jetzt hinter den Kopf werfen können!</li><li>Beispielcode für das Auslösen finden Sie hier im [Unity-Paket](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)"ThrowingStarter". Öffnen sie die Auslösende Szene, um zu beginnen.</li></ul></li><li>Verbesserte Motion Controller-Akkuberichterstellung</li><li>Verschiedene Stabilitäts- und Zuverlässigkeitskorrekturen</li></ul> |
   | 10.0.16299.1012  | 17. Oktober 2017    | Erste öffentliche Version des Treibers                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Mixed Reality Releaseverlauf des Motion Controller-Modelltreibers ###

Dieser Treiber wird auch automatisch über Windows Update heruntergeladen und installiert. Downloadlinks werden jedoch inline bereitgestellt:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, Version 2004 (Update mai 2020)

| Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16. September 2020      | Erste öffentliche Version des Treibers für die neuen HP Motion Controllers. Kompatibel mit Windows 10, Version 1903 und höher. Dieser Treiber ist nur mit neuen HP Motion Controllers kompatibel.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, Version 1803 (Update april 2018) und Version 1809 (Update von Oktober 2018) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1. Oktober 2018      | Erste öffentliche Version des Treibers für Windows 10, Version 1809. Kompatibel mit Windows 10, Version 1803 und höher.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17. April 2018      | Erste öffentliche Version des Treibers für Windows 10, Version 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, Version 1709 (Fall Creators Update) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17. Oktober 2017    | Erste öffentliche Version des Treibers                          |

### <a name="mixed-reality-portal-release-history"></a>Mixed Reality-Portal Releaseverlauf ###

In Windows 10, Version 1809 und neuer wird [Mixed Reality-Portal](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) über die Microsoft Store-App aktualisiert.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, Version 1809 und neuer ####

   | Version            | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 8\. Juni 2021          | <ul><li>Fügt der Hilfe-App Links zur Problembehandlung für häufige Headsetfehler hinzu.</li><li>Behebt ein Problem, bei dem die Begleit-App des Headsetgeräts während der ersten Einrichtung übersprungen werden kann.</li><li>Aktualisiert die Seite mit den Systemanforderungen mit zusätzlichen Informationen für headsets mit hoher Auflösung.</li><li>Aktualisiert den Begrüßungsbildschirm und die Landing Page mit neuen Visuals.</li></ul>  |
   | 2000.21041.1051.0  | 26. April 2021        | <ul><li>Aktualisiert das App-Symbol für Mixed Reality-Portal.</li></ul>  |
   | 2000.20111.1381.0  | 10. Dezember 2020     | <ul><li>Aktualisiert die Landing Page von Mixed Reality-Portal.</li><li>Reduziert Headsetverbindungsfehler während Firmwareupdates. </li></ul>  |
   | 2000.20071.1133.0  | 5\. August 2020        | <ul><li>Unterstützung für [OpenXR](/windows/mixed-reality/openxr) zum Anhalten des Vorschaufensters.</li></ul>  | 
   | 2000.20041.1212.0  | 11. Mai 2020          | <ul><li>Behebt ein Zeitsteuerungsproblem, das zu einem inkonsistenten 15-5-Fehler geführt hat.</li><li>Verbesserte Unterstützung für die Ausführung von Windows Mixed Reality ohne Internetverbindung.</li><li>Verbesserte Unterstützung für das Koppeln von Motion-Controllern über **Setupcontroller.**</li></ul>  | 
   | 2000.20031.1202.0  | 14. April 2020        | <ul><li>Unterstützung für die Registrierung von Informationen, Tipps und Angeboten zu Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | 11. Februar 2020     | <ul><li>Verbesserte Unterstützung für Anwendungen, die [OpenXR](/windows/mixed-reality/openxr) auf Geräten mit dem Update vom Mai 2019 verwenden.</li><li>Behandeln von Problemen mit der Barrierefreiheit und dem Tastaturfokus</li></ul>  | 
   | 2000.19101.1211.0  | 11. November 2019     | <ul><li>Behebt ein Problem, das sie daran hindert, Raumbegrenzungsvisuals umzustellen.</li><li>Es wird ein Problem behoben, das verhindert, dass Sie während der Einrichtung der Raumgrenze ein Headset zentrieren.</li></ul>  | 
   | 2000.19081.1301.0  | 23. September 2019    | <ul><li>Behebt ein Problem, bei dem Headsets mit Hardwareproblemen eine falsche Fehlermeldung angezeigt wurden. Benutzer, die in früheren Versionen einen Fehlercode zwischen 1 und 4 erhalten haben, erhalten jetzt möglicherweise einen spezifischeren Fehlercode für ihren Gerätezustand.</li></ul>  |
   | 2000.19071.1302.0  | 13. August 2019     | <ul><li>Unterstützung für Anwendungen, die [OpenXR](/windows/mixed-reality/openxr) auf Geräten mit dem Update vom Mai 2019 verwenden.</li></ul>  | 
   | 2000.19061.1011.0  | 16. Juli 2019         | <ul><li>Unterstützung für JSON-Konfigurationsoptionen zum Anpassen des App-Verhaltens. Weitere Informationen finden Sie unter https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup .</li></ul>  | 

### <a name="steamvr-release-history"></a>Verlauf der Veröffentlichung von SteamVR ###

Versionshinweise zu Valve für SteamVR finden Sie hier: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality für den Releaseverlauf von SteamVR ###

Unsere Versionshinweise für die Windows Mixed Reality für die Komponente "SteamVR" finden Sie hier:[http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
