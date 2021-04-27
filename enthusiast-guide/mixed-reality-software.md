---
title: Softwareübersicht und Releaseverlauf
description: Eine Übersicht über die wichtigsten Softwarekomponenten für Windows Mixed Reality, immersive Headsets und deren Releaseverlauf.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Softwarekomponenten, Releaseverlauf, Versionshinweise, Versionsverlauf
appliesto:
- Windows 10
ms.openlocfilehash: 5e6cdcbc7d91a6c1fadb519f94fc0339bdd39ca7
ms.sourcegitcommit: 229c33afab7c70341982f48962028aad13956356
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "108069204"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Mixed Reality: Übersicht zur Software und Versionsverlauf

## <a name="introduction-to-mixed-reality-software"></a>Einführung in Mixed Reality Software

Windows Mixed Reality besteht aus den folgenden Hauptkomponenten der Software:

1. **Mixed Reality-Portal**, das die wichtigsten Windows Mixed Reality bietet
    * In Windows 10 Versionen 1709 und 1803 ist Mixed Reality-Portal eine wichtige Komponente des Windows 10 Betriebssystems, das über Windows Update aktualisiert wurde.
    * In Windows 10 Version 1809 und höher wird Mixed Reality-Portal über die Microsoft Store-App aktualisiert.
2. Das **Mixed Reality Feature-on-Demand-Paket** (FOD), das bei der ersten Ausführung Mixed Reality-Portal automatisch heruntergeladen und installiert wird. Weitere Informationen zum FOD-Paket finden Sie [hier.](/windows/application-management/manage-windows-mixed-reality)
3. Der **Mixed Reality Headset- und Motion Controller-Treiber**, auch als HoloLens Sensors-Treiber bezeichnet, ist das Schlüsseltreiberpaket, mit dem Windows Mixed Reality Headsets mit Windows Mixed Reality arbeiten können. Dies wird automatisch über Windows Update heruntergeladen und installiert, wenn Ihr Mixed Reality Headset zum ersten Mal angeschlossen ist, und wird regelmäßig über Windows Update
4. Die **Mixed Reality Motion Controller-Modelltreiber enthalten die 3D-Modelle der Mixed Reality Motion-Controller und werden für Mixed Reality-Funktionen von Drittanbietern benötigt. Dies wird automatisch über Windows Update heruntergeladen und installiert, wenn Ihre Mixed Reality Motion-Controller zum ersten Mal mit Ihrem PC gekoppelt werden, und wird über Windows Update
5. **Windows 10 Version 1709 (Fall Creator es Update) oder höher** enthält wichtige Betriebssystemkomponenten und -technologien, die Windows Mixed Reality

Für die Verwendung von Windows Mixed Reality in SteamVR ist die folgende Software erforderlich:

6. **SteamVR,** entwickelt und verwaltet von der Valve Corporation, die Virtual Reality-Apps und -Spiele auf Steam ermöglicht. Weitere Informationen finden Sie [hier](https://go.microsoft.com/fwlink/?linkid=862788).
7. Die **Windows Mixed Reality für die Komponente "SteamVR",** die Eine Brücke zwischen "SteamVR" und Windows Mixed Reality. Weitere Informationen zu dieser Komponente finden Sie [auf der Seite Windows Mixed Reality für SteamVR.](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Verwalten Ihres Windows Mixed Reality Headsets:

8. Die **Geräte-Begleit-App,** die von den einzelnen Headsetherstellern entwickelt und verwaltet wird, bietet eine kurze Einführung in Ihr Windows Mixed Reality Headset. Auf Headsets mit integrierter Bluetooth-Funktion ermöglicht die Device Companion-App die Wiederherstellung von Motion Controllern in der Bluetooth-Kopplung ihrer Factory. Einige Headsets (z. B. SamsungIgey und Samsung Geräte+) verwenden auch die Geräte-Begleit-App, um Firmwareupdates für Headsets vom Headsethersteller zu liefern. Diese App wird automatisch heruntergeladen, wenn Ihr Headset zum ersten Mal angeschlossen wird, und befindet sich im Windows-Startmenü.

## <a name="windows-10-release-notes---may-2020"></a>Windows 10– Mai 2020

Das **Windows 10-Update vom Mai 2020 (v2004)** enthält neue Features für Windows Mixed Reality-Headsets (VR), z. B. die Möglichkeit, Win32-Anwendungen im Mixed Reality Startumgebung. HoloLens (1. Generation) befindet sich in Long Term Servicing (LTS), und Wartungsupdates werden monatlich veröffentlicht.

Wenn Sie ein Upgrade auf die neueste PC-Version Windows Mixed Reality IMMERSIVE Headsets (VR) durchführen, öffnen Sie Einstellungen > **Update & Security,** und wählen Sie **Nach Updates suchen aus.** Auf einem Windows 10-PC können Sie das Windows 10 Update vom Mai **2020** auch manuell installieren, indem Sie das [Windows-Medienerstellungstool verwenden.](https://www.microsoft.com/software-download/windows10)

**Neueste Version für Desktop:** Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Updates für Windows Mixed Reality immersive Headsets

#### <a name="introducing-the-new-microsoft-edge"></a>Einführung in die Microsoft Edge

Wie [bereits angekündigt,](/windows/mixed-reality/new-microsoft-edge)haben wir Updates vorgenommen, um die Unterstützung mithilfe des neuen Microsoft Edge-Browsers in Windows Mixed Reality. Die neue Microsoft Edge übernimmt das Chromium-Open-Source-Projekt, um eine bessere Webkompatibilität für Kunden und eine geringere Fragmentierung des Webs für alle Webentwickler zu schaffen. Es unterstützt auch WebXR, den neuen Standard zum Erstellen immersiver Weberfahrungen für VR-Headsets anstelle von WebVR.

#### <a name="improved-settings-for-wmr"></a>Verbesserte Einstellungen für WMR

Dank Ihres Feedbacks haben wir einstellungen auf der Headset-Anzeigeseite hinzugefügt und verdeutlicht:

* **Visuelle Qualität meines Hauses:** Das Ändern dieser Einstellungen wirkt sich nur auf die Mixed Reality Startumgebung Umgebung (Haus an den Klippen und Skyitatt) aus:

* **Anpassen des Detailgrads und der Qualität von Effekten im Mixed Reality Startumgebung** – dies ändert einige der Renderingeffekte, die wir im Home-Bereich verwenden. Insbesondere die visuelle Qualität verschiedener Materialien (Wood, Concrete usw.) wird skaliert, wenn Sie diese Einstellung von niedrig in hoch ändern.

* Ändern der Auflösung des **App-Fensters:** Standardmäßig werden die meisten 2D-Fenster, die in der Startseite gestartet werden, mit einer Auflösung von 720 p gestartet. Sie können die Größe manuell horizontal & vertikal ändern, aber Sie können auch entscheiden, dass sie alle stattdessen mit 1080p gestartet werden. Zuvor war diese Option unter Visuelle Qualität als Option Sehr hoch (Beta) verfügbar. Wir haben es jetzt entsprechend als separate Einstellung aufgeteilt.

* **Erfahrungsoptionen:** Diese Optionen passen die Mixed Reality-Erfahrung an, um die Auslastung von Systemen zu reduzieren, bei denen die Hardware mit uneingeschränkten 90 Fps nicht schritthalten kann. Sie können diese zusätzlichen Einstellungen explizit aktivieren oder deaktivieren oder Windows entscheiden lassen und unsere Heuristik weiterhin entscheiden lassen, wann diese ein- und ausgeschaltet werden sollen.

* **Lösung:** Wenn Sie über ein hochauflösendes Headset wie HP Reverb verfügen, wird die Ausführung mit der nativen Auflösung oder mit einer reduzierten Auflösung aus Leistungsgründen unterstützt. Frühere Headsets wie Samsung Odyssey und Odyssey+ unterstützen nur eine einzige Auflösung, sodass Sie diese Einstellung auf diesen Headsets nicht ändern können.

* **Bildfrequenz:** Sie können jetzt manuell die Bildfrequenz der Headsetanzeige festlegen oder windows weiterhin seine Heuristik verwenden lassen, um zu bestimmen, ob 60 Hz oder 90 Hz besser geeignet sind.

* **Kalibrierung:** Wie zuvor können Sie Ihre IPD (Interpupillary Distance) anpassen, wenn sie von Ihrem Headset unterstützt wird.

* **Eingabewechsel:** Schalten Sie das Verhalten des Eingabefokuswechsels (Win+Y) so um, dass es automatisch (basierend auf dem Feedback des Anwesenheitssensors) oder manuell erfolgt.

#### <a name="new-cortana-app"></a>Neue Cortana-App

Dieses Update für Windows enthält die neueste Version der Cortana-App, die derzeit nur in den USA verfügbar ist und bestimmte Mixed Reality-spezifische Befehle wie "Take a picture" und "Take a video" nicht mehr unterstützt. Sie können die neue Cortana-App verwenden, um Apps zu starten, und sie unterstützt auch neue produktivitätsorientierte Befehle wie "Wann ist meine nächste Besprechung?" oder "Senden Sie eine E-Mail <name> an , an die ich zu spät lauf."
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Zusätzliche Updates in verfügbar in 19041.546 (veröffentlicht im Oktober 2020)

Dieses monatliche Desktopwartungsupdate enthält die folgenden Änderungen für Windows Mixed Reality Geräte: 
* Reduziert Verzerrungen und Abweichungen in Windows Mixed Reality hmd-Displays (Head-Mounted Displays, HMD). 
* Unterstützung für zukünftige HP-Windows Mixed Reality Motion-Controller. 
* Ändert das Verhalten der Einstellung für die 90-Hz-Aktualisierungsrate in Windows Mixed Reality so, dass in bestimmten Fällen, in denen 90 Hz nicht erreicht werden kann, nicht mehr automatisch wieder auf 60 Hz umgeschaltet wird. 

#### <a name="help-us-improve"></a>Helfen Sie uns, uns zu verbessern!

Wir arbeiten ständig daran, die Kompatibilität zu verbessern.  Wenn Sie feststellen, dass Sich Ihre bevorzugte klassische Win32-Anwendung nicht ordnungsgemäß verhält, während sie sich in Windows Mixed Reality, senden Sie Feedback über unsere [Feedback-Hub](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

### <a name="prior-release-notes"></a>Vorherige Versionshinweise

* [Versionshinweise – Mai 2019](release-notes-may-2019.md)
* [Versionshinweise – Oktober 2018](release-notes-october-2018.md)
* [Versionshinweise – April 2018](release-notes-april-2018.md)
* [Versionshinweise – Oktober 2017](release-notes-october-2017.md)
* [Versionshinweise – August 2016](release-notes-august-2016.md)
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Mixed Reality des Headsets und des Motion Controller-Treibers ###

Dieser Treiber wird automatisch heruntergeladen und über Windows Update installiert. Downloadlinks werden jedoch inline bereitgestellt:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, Version 2004 (Update mai 2020) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 23. März 2021  | Kompatibel mit Windows 10, Version 1903 und höher.<br/><ul><li>Aktualisieren Sie die Ziehreihenfolge des verborgenen Bereichsgitters für HP Reverb G2, um mit anderen Headsets konsistent zu sein.</li><li>Verbesserungen der Visualqualität für die HP Reverb G2-Headsets.</li><li>Windows Mixed Reality Headsetplattform und Zuverlässigkeitsverbesserungen.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10. Dezember 2020  | Kompatibel mit Windows 10, Version 1903 und höher.<br/><ul><li>Neue Controllerfirmware für den HP Controller, um ein Problem zu beheben, bei dem einige Controller nicht funktionierende Trigger aufweisen.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8. Oktober 2020  | Kompatibel mit Windows 10, Version 1903 und höher.<br/><ul><li>Offizielle Unterstützung für HP Reverb G2, HP Omnicept und den neuen HP Controller.</li><li>Kleinere Anzeigekorrekturen für HP Reverb- und Samsung Odyssey+-Headsets. (Erfordert [Betriebssystembuild 19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) oder höher oder [Betriebssystembuilds 18362.1110 und 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) oder höher).</li><li>Verbesserungen beim Übergang des Computerstromzustands aus dem Energiesparmodus, um SWW 1-4-Fehler zu reduzieren.</li><li>Windows Mixed Reality headset platform minor fixes and reliability improvements (Kleinere Fehlerbehebungen und Zuverlässigkeitsverbesserungen für headset-Plattformen).|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7\. Mai 2020      | Kompatibel mit Windows 10, Version 1903 und höher.<br/><ul><li>Windows Mixed Reality der Headsetplattform kleinere Korrekturen und Zuverlässigkeitsverbesserungen.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, Version 1903 (Update mai 2019) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14. Oktober 2019      | Kompatibel mit Windows 10, Version 1809 und neueren.<br/><ul><li>Windows Mixed Reality kleinere Fehlerbehebungen für die Headsetplattform.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24. Juni 2019      | Kompatibel mit Windows 10, Version 1809 und neueren.<br/><ul><li>Windows Mixed Reality headset platform and reliability improvements around sleeping computers and power state transitions (Verbesserungen bei der Headsetplattform und -zuverlässigkeit bei Computern im Betriebszustand und bei Energiestatusübergängen).</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1\.Mai 2019      | Kompatibel mit Windows 10, Version 1809 und neueren.<br/><ul><li>Enthält Firmwareupdates für 2017 Acer, Asus, Dell, Hp, Hp, Hp und Windows Mixed Reality Headsets. Dieses Firmwareupdate verbessert die Kompatibilität und Zuverlässigkeit der Headsetanzeige mit bestimmten Grafikkarten oder Grafiktreibern.</li><li>Windows Mixed Reality der Headsetplattform und zuverlässigkeitsverbesserungen</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, Version 1803 (Update april 2018) und Version 1809 (Update vom Oktober 2018) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2. Januar 2019      | Kompatibel mit Windows 10 Version 1803 und neuer.<br/><ul><li>Korrekturen für Headset-Nachverfolgungs-Jitter und -Bereinigungen</li><li>Fehlerbehebungen für die Zuverlässigkeit des Taschenlampenmodus</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1. Oktober 2018      | Erste öffentliche Version des Treibers für Windows 10, Version 1809.<br/>Kompatibel mit Windows 10, Version 1803 und höher.<br/><ul><li>Aktiviert neue Windows Mixed Reality Features wie den Taschenlampenmodus in Windows 10, Version 1809</li><li>Verbesserungen der Nachverfolgung und Zuverlässigkeit von Headsets</li><li>Motion Controller-Nachverfolgung und Leistungsverbesserungen</li><li>USB-Leistung und -Verbesserungen</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27. April 2018      | Erste öffentliche Version des Treibers für Windows 10, Version 1803<br/> <ul><li>Verbesserungen der Nachverfolgung und Zuverlässigkeit von Headsets</li><li>Motion Controller-Nachverfolgung und Leistungsverbesserungen</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, version 1709 (Fall Creators Update) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6. Februar 2018    | <ul><li>Offizielle Unterstützung für 3Glasses Blubur S2 Mixed Reality Headset</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19. Dezember 2017   | <ul><li>Löst hid-Problem, das *zum* Fehlercode 2181038087-7 auf einigen PCs führt.</li><li>Verschiedene Korrekturen für Stabilität und Zuverlässigkeit</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5\. Dezember 2017    | <ul><li>Verbesserte Headsetnachverfolgung</li><li>Verbesserungen der Reaktionsfähigkeit des Motion Controller-Touchpads</li><li>Löst ein Problem, bei dem die Treiberinstallation manchmal fehlschlägt.</li><li>Verschiedene Korrekturen für Stabilität und Zuverlässigkeit</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21. November 2017   | <ul><li>Löst ein Problem, das dazu geführt hat, dass Headsetanzeigen während der Verwendung manchmal schwarz werden</li><li>Löst ein Problem, das manchmal dazu geführt hat, dass Motion Controller nicht mehr</li><li>Leistungsverbesserungen des Anwesenheitssensors für das Dell Visor-Headset</li><li>Verschiedene Korrekturen für Stabilität und Zuverlässigkeit</li></ul> |
   | 10.0.16299.1036  | 7. November 2017    | <ul><li>Motion Controller throwing improvements (Bewegungscontroller löst Verbesserungen aus:<ul><li>Die Geschwindigkeit wird jetzt ordnungsgemäß gemeldet, wenn die Positionsgenauigkeit ungefähr ist, sodass Sie jetzt hinter dem Kopf auslösen können!</li><li>Beispielcode für das Auslösen finden Sie hier im Unity-Paket "ThrowingStarter". [](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/) Öffnen Sie die Auslösen-Szene, um zu beginnen.</li></ul></li><li>Verbesserte Berichterstellung für Motion Controller-Akkus</li><li>Verschiedene Korrekturen für Stabilität und Zuverlässigkeit</li></ul> |
   | 10.0.16299.1012  | 17. Oktober 2017    | Erste öffentliche Version des Treibers                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Mixed Reality Releaseverlauf des Motion Controller-Modelltreibers ###

Dieser Treiber wird auch automatisch über Windows Update heruntergeladen und installiert, downloadlinks werden jedoch inline bereitgestellt:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, Version 2004 (Update mai 2020)

| Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16. September 2020      | Erste öffentliche Version des Treibers für die neuen HP Motion Controllers. Kompatibel mit Windows 10, Version 1903 und höher. Dieser Treiber ist nur mit neuen HP Motion Controllers kompatibel.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, Version 1803 (Update vom April 2018) und Version 1809 (Update von Oktober 2018) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1. Oktober 2018      | Erste öffentliche Version des Treibers für Windows 10, Version 1809. Kompatibel mit Windows 10, Version 1803 und höher.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17. April 2018      | Erste öffentliche Version des Treibers für Windows 10, Version 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, version 1709 (Fall Creators Update) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17. Oktober 2017    | Erste öffentliche Version des Treibers                          |

### <a name="mixed-reality-portal-release-history"></a>Mixed Reality-Portal des Releaseverlaufs ###

In Windows 10, Version 1809 und [neueren](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) Version wird Mixed Reality-Portal über die Microsoft Store aktualisiert.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, Version 1809 und neuer ####

   | Version            | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21041.1051.0  | 26. April 2020        | <ul><li>Aktualisiert das App-Symbol für Mixed Reality-Portal.</li></ul>  |
   | 2000.20111.1381.0  | 10. Dezember 2020        | <ul><li>Aktualisiert die Landing Page des Mixed Reality-Portal.</li><li>Reduziert Headset-Konnektivitätsfehler während Firmwareupdates. </li></ul>  |
   | 2000.20071.1133.0  | 5\. August 2020        | <ul><li>Unterstützung für [OpenXR zum](/windows/mixed-reality/openxr) Anhalten des Vorschaufensters.</li></ul>  | 
   | 2000.20041.1212.0  | 11. Mai 2020          | <ul><li>Behebt ein Zeitsteuerungsproblem, das zu einem inkonsistenten 15-5-Fehler führt.</li><li>Verbesserte Unterstützung für die Ausführung Windows Mixed Reality ohne Internetverbindung.</li><li>Verbesserte Unterstützung für das Koppeln von Motion-Controllern über **Setupcontroller.**</li></ul>  | 
   | 2000.20031.1202.0  | 14. April 2020        | <ul><li>Unterstützung für die Registrierung von Informationen, Tipps und Angeboten zu Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | 11. Februar 2020     | <ul><li>Verbesserte Unterstützung für Anwendungen, die [OpenXR](/windows/mixed-reality/openxr) auf Geräten mit dem Update vom Mai 2019 verwenden.</li><li>Behandeln von Problemen mit der Barrierefreiheit und dem Tastaturfokus</li></ul>  | 
   | 2000.19101.1211.0  | 11. November 2019     | <ul><li>Es wird ein Problem behoben, das verhindert, dass Sie Raumbegrenzungsvisuals umstellen können.</li><li>Es wird ein Problem behoben, das verhindert, dass Sie während der Einrichtung der Raumgrenze ein Headset zentrieren.</li></ul>  | 
   | 2000.19081.1301.0  | 23. September 2019    | <ul><li>Behebt ein Problem, bei dem Headsets mit Hardwareproblemen eine falsche Fehlermeldung angezeigt wurden. Benutzer, die in früheren Versionen einen Fehlercode zwischen 1 und 4 erhalten haben, erhalten jetzt möglicherweise einen spezifischeren Fehlercode für ihren Gerätezustand.</li></ul>  |
   | 2000.19071.1302.0  | 13. August 2019     | <ul><li>Unterstützung für Anwendungen, die [OpenXR](/windows/mixed-reality/openxr) auf Geräten mit dem Update vom Mai 2019 verwenden.</li></ul>  | 
   | 2000.19061.1011.0  | 16. Juli 2019         | <ul><li>Unterstützung für JSON-Konfigurationsoptionen zum Anpassen des App-Verhaltens. Weitere Informationen finden Sie unter https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup .</li></ul>  | 

### <a name="steamvr-release-history"></a>Verlauf der Veröffentlichung von SteamVR ###

Versionshinweise zu Valve für SteamVR finden Sie hier: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality für den Releaseverlauf von SteamVR ###

Unsere Versionshinweise für die Windows Mixed Reality für die Komponente "SteamVR" finden Sie hier: [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
