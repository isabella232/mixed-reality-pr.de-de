---
title: Software Übersicht und releaseverlauf
description: Eine Übersicht über die wichtigsten Softwarekomponenten für Windows Mixed Reality, immersive Headsets und ihren releaseverlauf.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Software Components, releaseverlauf, Versions Hinweise, Versionsverlauf
appliesto:
- Windows 10
ms.openlocfilehash: b06bd835f1e2562e01bfb7bf240747919f422e8c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009250"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Mixed Reality: Übersicht zur Software und Versionsverlauf

## <a name="introduction-to-mixed-reality-software"></a>Einführung in Mixed Reality Software

Windows Mixed Reality besteht aus den folgenden wichtigen Softwarekomponenten:

1. **Mixed Reality-Portal**, das die Haupt Darstellung von Windows Mixed Reality bietet
    * In den Windows 10-Versionen 1709 und 1803 ist das Mixed Reality-Portal eine wichtige Komponente des Windows 10-Betriebssystems, das über Windows Update aktualisiert wird.
    * In Windows 10, Version 1809 und höher, wird das Mixed Reality-Portal über die Microsoft Store-APP aktualisiert.
2. Das **Mixed Reality Feature-on-Demand-Paket** (FOD), das automatisch heruntergeladen und installiert wird, während der erste Testlauf des Mixed Reality-Portals. Weitere Informationen zum FOD-Paket finden Sie [hier](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality) .
3. Der **Mixed Reality-Headset und der Motion Controller-Treiber**, auch als "hololens Sensors"-Treiber bezeichnet, ist das Schlüssel Treiber Paket, mit dem Windows Mixed Reality-Headsets mit Windows Mixed Reality arbeiten kann. Diese wird automatisch heruntergeladen und installiert, wenn das Mixed Reality-Headset zum ersten Mal angeschlossen ist, und wird über Windows Update regelmäßig Windows Update aktualisiert.
4. Die * * Mixed Reality Motion Controller-Modell Treiber enthalten die 3D-Modelle der Mixed Reality-Bewegungs Controller und sind für die gemischte Realität von Drittanbietern erforderlich. Diese wird automatisch heruntergeladen und installiert, wenn Sie zum ersten Mal mit Ihrem PC kombiniert werden, und zwar Windows Update, und wird über Windows Update
5. **Windows 10, Version 1709 (das Update des Fall Erstellers) oder eine neuere Version** enthält wichtige Betriebssystemkomponenten und-Technologien, die Windows Mixed Reality ermöglichen.

Die Verwendung von Windows Mixed Reality in steamvr erfordert die folgende Software:

6. **Steamvr**, entwickelt und verwaltet von der Ventil Corporation, die Virtual Reality-apps und Spiele im Stream ermöglicht. Weitere Informationen finden Sie [hier](https://go.microsoft.com/fwlink/?linkid=862788).
7. Die **Windows Mixed Reality for steamvr** -Komponente, die steamvr mit Windows Mixed Reality Bridges. Weitere Informationen zu dieser Komponente finden Sie [auf der Seite Windows Mixed Reality for steamvr](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) .

Verwalten des Windows Mixed Reality-Headsets:

8. Die **Geräte Begleit-App**, die von jedem der Headset-Hersteller entwickelt und verwaltet wird, bietet eine kurze Einführung in Ihr Windows Mixed Reality-Headset. Auf den Headsets mit integrierter Bluetooth-Funktion ermöglicht die Geräte Begleit-APP die Wiederherstellung von Bewegungs Controllern für Ihre Werks-Bluetooth-Kopplung. Einige Headsets (z. b. Samsung Odyssee und Samsung Odyssee und höher) verwenden auch die Geräte Begleit-APP, um die Headset-Firmwareupdates vom Headset-Hersteller bereitzustellen. Diese APP wird automatisch heruntergeladen, wenn Ihr Headset zum ersten Mal angeschlossen ist, und befindet sich im Windows-Startmenü.

## <a name="windows-10-release-notes---may-2020"></a>Anmerkungen zu dieser Version von Windows 10-Mai 2020

Das **Windows 10-Update von Mai 2020 (V2004)** enthält neue Features für Windows Mixed Reality (VR)-Headsets, wie z. b. die Möglichkeit zum Starten von Win32-Anwendungen in der Mixed Reality-Startseite. Hololens (1st Gen) ist eine langfristige Wartung (LTS), wobei Wartungsupdates monatlich veröffentlicht werden müssen.

Wenn Sie ein Upgrade auf die neueste PC-Version für Windows Mixed Reality-(VR)-Headsets durchführen, öffnen Sie **Einstellungen > aktualisieren Sie & Sicherheit** , und wählen Sie **nach Updates suchen**. Auf einem Windows 10-PC können Sie das **Windows 10-Update von Mai 2020** auch manuell mithilfe des [Windows Media-Erstellungs Tools](https://www.microsoft.com/software-download/windows10)installieren.

**Neueste Version für Desktop**: Windows 10 V2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Updates für Windows Mixed Reality-immersive Headsets

#### <a name="introducing-the-new-microsoft-edge"></a>Einführung in den neuen Microsoft Edge

Wie [bereits angekündigt](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge), haben wir Aktualisierungen vorgenommen, um die Unterstützung für die Verwendung des neuen Microsoft Edge-Browsers in Windows Mixed Reality zu verbessern. Der neue Microsoft Edge übernimmt das Projekt "Chromium Open Source", um eine bessere webkompatibilität für Kunden und weniger Fragmentierung des Internets für alle Webentwickler zu erzielen. Es unterstützt auch webxr, den neuen Standard zum Erstellen von immersiven Webumgebungen für VR-Headsets anstelle von webvr.

#### <a name="improved-settings-for-wmr"></a>Verbesserte Einstellungen für WMR

Dank Ihres Feedbacks haben wir die Einstellungen auf der Seite für die Headset-Anzeige hinzugefügt und verdeutlicht:

* Die **visuelle Qualität meiner zu Hause** ändernden Einstellungen wirkt sich nur auf die gemischte Umgebung in der Praxis aus ("Klippe House" und "SkyLoft"):

* **Anpassung der Detail-und Qualitäts Qualität in der Mixed Reality-Startseite** : Hierdurch werden einige der in der Startseite verwendeten renderingauswirkungen geändert. Insbesondere die visuelle Qualität unterschiedlicher Materialien (Holz, konkrete usw.) wird skaliert, wenn Sie diese Einstellung von "niedrig" in "hoch" ändern.

* **Ändern der Auflösung von App** -Fenstern: Standardmäßig werden die meisten 2D-Fenster, die auf der Startseite gestartet werden, mit einer 720-p-Auflösung gestartet Obwohl Sie die Größe der Dateien & vertikal manuell ändern können, können Sie Sie auch dazu verwenden, dass Sie stattdessen bei 1080p gestartet werden. Zuvor war diese Option in der visuellen Qualität als sehr hohe (Beta-) Option verfügbar. Wir haben ihn entsprechend als separate Einstellung aufgeteilt.

* **Optionen** für die Verwendung: Diese Optionen passen die gemischte Realität an, um die Last auf 90 Systemen zu reduzieren Sie können diese zusätzlichen Einstellungen explizit aktivieren bzw. deaktivieren, oder Sie können Windows entscheiden lassen und unsere Heuristik weiterhin entscheiden, wann diese ein-und ausgeschaltet werden soll.

* **Lösung** : Wenn Sie über ein hochauflösende Headset wie den HP-Reverb verfügen, unterstützen wir die Ausführung bei der systemeigenen Auflösung oder bei einer reduzierten Auflösung aus Leistungsgründen. Frühere Headsets, wie z. b. Samsung Odyssee und Odyssee, unterstützen nur eine einzige Lösung, sodass Sie diese Einstellung auf diesen Headsets nicht ändern können.

* **Framerate** : Sie können nun die Framerate der Headset-Anzeige manuell festlegen oder die Heuristik von Windows verwenden, um zu bestimmen, ob 60 Hz oder 90 Hz besser geeignet ist.

* **Kalibrierung** : wie zuvor können Sie Ihre IPD (interpupilläre Entfernung) anpassen, wenn Sie von Ihrem Headset unterstützt wird.

* **Eingabe wechseln** : Schalten Sie das Verhalten des Eingabefokus Schaltens (Win + Y) so um, dass es automatisch (basierend auf dem Anwesenheits Sensor-Feedback) oder manuell erfolgt.

#### <a name="new-cortana-app"></a>Neue Cortana-App

Dieses Update für Windows enthält die neueste Version der Cortana-APP, die zurzeit nur auf Englisch ist und einige gemischte, gemischte Befehle wie "Bild nehmen" und "Video nehmen" nicht mehr unterstützt. Sie können die neue Cortana zum Starten von Apps verwenden, und Sie unterstützt auch neue produktivitätsorientierte Befehle wie "Wann ist meine nächste Besprechung?". oder "Senden Sie eine e-Mail an <name> , dass ich später ausführe."
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Weitere Updates in 19041,546 verfügbar (veröffentlicht im Oktober 2020)

Dieses Desktop-Update für die monatliche Wartung umfasst die folgenden Änderungen für Windows Mixed Reality-Geräte: 
* Verringert die Verzerrung und die Abweichungen in Windows Mixed Reality (HMD). 
* Fügt Unterstützung für bevorstehende HP Windows Mixed Reality Motion-Controller hinzu. 
* Ändert das Verhalten der 90-Hz-Einstellung für die Aktualisierungsrate in Windows Mixed Reality so, dass in bestimmten Fällen nicht mehr automatisch zu 60 Hz gewechselt wird, wenn 90 Hz nicht erreicht werden kann. 

#### <a name="help-us-improve"></a>Helfen Sie uns bei der Verbesserung!

Wir werden kontinuierlich darauf achten, die Kompatibilität zu verbessern.  Wenn Sie feststellen, dass sich Ihre bevorzugte klassische Win32-Anwendung in Windows Mixed Reality nicht ordnungsgemäß verhält, übermitteln Sie Feedback über unseren [Feedback-Hub](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

### <a name="prior-release-notes"></a>Vorherige Anmerkungen zu dieser Version

* [Anmerkungen zu dieser Version-Mai 2019](release-notes-may-2019.md)
* [Versionshinweise – Oktober 2018](release-notes-october-2018.md)
* [Anmerkungen zu dieser Version-April 2018](release-notes-april-2018.md)
* [Versionshinweise – Oktober 2017](release-notes-october-2017.md)
* [Versionshinweise – August 2016](release-notes-august-2016.md)
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Verlauf von Mixed Reality-Headset und Motion Controller-Treiber Releases ###

Dieser Treiber wird automatisch über Windows Update heruntergeladen und installiert. Download Links werden jedoch Inline bereitgestellt:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, Version 2004 (Mai 2020 Update) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10. Dezember 2020  | Kompatibel mit Windows 10, Version 1903 und höher.<br/><ul><li>Neue Controller Firmware für den HP-Controller, um ein Problem zu beheben, bei dem einige Controller nicht funktionsfähige Trigger aufweisen.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8. Oktober 2020  | Kompatibel mit Windows 10, Version 1903 und höher.<br/><ul><li>Offizielle Unterstützung für den HP-Reverb G2, HP omnicept und den neuen HP-Controller.</li><li>Kleinere Anzeige Korrekturen für HP Reverb und Samsung Odyssee + Headsets. (Erfordert den [OS-Build 19041,546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) oder höher oder [Betriebssystem-Builds 18362,1110 und 18363,1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) oder höher).</li><li>Verbesserungen an der Umstellung des Computer Energie Zustands aus dem Standbymodus, um Fehler beim Austauschen von 1-4 WS</li><li>Windows Mixed Reality-Headset-Plattform kleinere Korrekturen und Zuverlässigkeitsverbesserungen.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7\. Mai 2020      | Kompatibel mit Windows 10, Version 1903 und höher.<br/><ul><li>Windows Mixed Reality-Headset-Plattform kleinere Korrekturen und Zuverlässigkeitsverbesserungen.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, Version 1903 (Mai 2019 Update) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14. Oktober 2019      | Kompatibel mit Windows 10, Version 1809 und höher.<br/><ul><li>Kleinere Korrekturen der Windows Mixed Reality-Headset-Plattform.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24. Juni 2019      | Kompatibel mit Windows 10, Version 1809 und höher.<br/><ul><li>Windows Mixed Reality-Headset-Plattform und Zuverlässigkeitsverbesserungen bei inaktiven Computern und Energie Zustands Übergängen.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1\.Mai 2019      | Kompatibel mit Windows 10, Version 1809 und höher.<br/><ul><li>Enthält ein Firmwareupdate für 2017 Acer, Asus, Dell, Fujitsu, HP, Lenovo und Media on Windows Mixed Reality-Headsets. Dieses Firmwareupdate verbessert die Kompatibilität und Zuverlässigkeit der Headset-Anzeige mit bestimmten Grafikadaptern oder Grafiktreibern.</li><li>Windows Mixed Reality-Headset-Plattform und Zuverlässigkeitsverbesserungen</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, Version 1803 (Update April 2018) und Version 1809 (Update vom Oktober 2018) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2. Januar 2019      | Kompatibel mit Windows 10, Version 1803 und höher.<br/><ul><li>Fehler Behebungs Jitter und ruckeln-Korrekturen</li><li>Zuverlässigkeits Korrekturen im Taschen Taschen Modus</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1. Oktober 2018      | Anfängliche öffentliche Version des Treibers für Windows 10, Version 1809.<br/>Kompatibel mit Windows 10, Version 1803 und höher.<br/><ul><li>Ermöglicht neue Windows Mixed Reality-Features, z. b. den Taschen Taschen Modus, in Windows 10, Version 1809</li><li>Verbesserungen bei der Leistung der Headset</li><li>Verbesserungen der Bewegungs Controller Verfolgung und-Leistung</li><li>USB-Leistung und Verbesserungen</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27. April 2018      | Anfängliche öffentliche Version des Treibers für Windows 10, Version 1803<br/> <ul><li>Verbesserungen bei der Leistung der Headset</li><li>Verbesserungen der Bewegungs Controller Verfolgung und-Leistung</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, Version 1709 (Fall Creators Update) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6. Februar 2018    | <ul><li>Offizieller Support für 3gläser blubur S2 Mixed Reality-Headset</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19. Dezember 2017   | <ul><li>Löst das HID-Problem auf, was zu einem *falschen* Fehlercode 2181038087-7 auf einigen PCs geführt hat.</li><li>Verschiedene Korrekturen der Stabilität und Zuverlässigkeit</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5\. Dezember 2017    | <ul><li>Verbesserte Headset-Nachverfolgung</li><li>Verbesserungen der Touchpad-Reaktionsfähigkeit</li><li>Löst Probleme auf, bei denen die Treiberinstallation manchmal fehlschlägt</li><li>Verschiedene Korrekturen der Stabilität und Zuverlässigkeit</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21. November 2017   | <ul><li>Löst ein Problem auf, das zu den Headset-anzeigen führt, manchmal während der Verwendung schwarz.</li><li>Löst ein Problem, das manchmal dazu führt, dass Bewegungs Controller verschwinden.</li><li>Verbesserungen der Anwesenheits Sensorleistung für das Dell Visor-Headset</li><li>Verschiedene Korrekturen der Stabilität und Zuverlässigkeit</li></ul> |
   | 10.0.16299.1036  | 7. November 2017    | <ul><li>Motion Controller löst die mechanischen Verbesserungen:<ul><li>Die Geschwindigkeit wird nun ordnungsgemäß gemeldet, wenn die Positionsgenauigkeit annähernd ist, sodass Sie jetzt hinter ihren Kopf wechseln können!</li><li>Einen Beispielcode für das Auslösen finden Sie im Unity [-Paket "](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)throwingstarter". Öffnen Sie die auslösende Szene, um loszulegen.</li></ul></li><li>Verbesserte Berichterstellung für Motion Controller-Akku</li><li>Verschiedene Korrekturen der Stabilität und Zuverlässigkeit</li></ul> |
   | 10.0.16299.1012  | 17. Oktober 2017    | Anfängliche öffentliche Freigabe des Treibers                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Releaseverwaltung des Mixed Reality-Modell Treibers ###

Dieser Treiber wird auch automatisch über Windows Update heruntergeladen und installiert. Download Links werden jedoch Inline bereitgestellt:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, Version 2004 (Mai 2020 Update)

| Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16. September 2020      | Anfängliche öffentliche Freigabe des Treibers für die neuen HP Motion-Controller. Kompatibel mit Windows 10, Version 1903 und höher. Dieser Treiber ist nur mit neuen HP Motion-Controllern kompatibel.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, Version 1803 (Update April 2018) und Version 1809 (Update vom Oktober 2018) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1. Oktober 2018      | Anfängliche öffentliche Version des Treibers für Windows 10, Version 1809. Kompatibel mit Windows 10, Version 1803 und höher.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17. April 2018      | Anfängliche öffentliche Version des Treibers für Windows 10, Version 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, Version 1709 (Fall Creators Update) ####

   | Version          | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17. Oktober 2017    | Anfängliche öffentliche Freigabe des Treibers                          |

### <a name="mixed-reality-portal-release-history"></a>Verlauf der Veröffentlichung im Mixed Reality-Portal ###

In Windows 10, Version 1809 und höher, wird das [Mixed Reality-Portal](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) über die Microsoft Store-APP aktualisiert.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, Version 1809 und höher ####

   | Version            | Veröffentlichungsdatum          | Wichtige Änderungen                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.20071.1133.0  | 5\. August 2020        | <ul><li>Unterstützung für [openxr](https://docs.microsoft.com/windows/mixed-reality/openxr) zum Anhalten des Vorschaufensters.</li></ul>  | 
   | 2000.20041.1212.0  | 11. Mai 2020          | <ul><li>Behandelt ein Zeit Steuerungs Problem, das zu einem inkonsistenten 15-5-Fehler geführt hat.</li><li>Verbesserte Unterstützung für die Ausführung von Windows Mixed Reality ohne Internetverbindung.</li><li>Verbesserte Unterstützung für die Kopplung von Bewegungs Controllern über **Setup Controller**.</li></ul>  | 
   | 2000.20031.1202.0  | 14. April 2020        | <ul><li>Unterstützung für die Registrierung von Informationen, Tipps und angeboten über Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | 11. Februar 2020     | <ul><li>Verbesserte Unterstützung für Anwendungen mit [openxr](https://docs.microsoft.com/windows/mixed-reality/openxr) auf Geräten mit dem Update von Mai 2019.</li><li>Adressiert Probleme mit Barrierefreiheit und Tastaturfokus</li></ul>  | 
   | 2000.19101.1211.0  | 11. November 2019     | <ul><li>Behandelt ein Problem, das das Umschalten von visuellen Raum Begrenzungs Elementen verhindert.</li><li>Behandelt ein Problem, das verhindert, dass Sie ein Headset beim Einrichten der Raum Begrenzung überschreiben.</li></ul>  | 
   | 2000.19081.1301.0  | 23. September 2019    | <ul><li>Es wird ein Problem behoben, bei dem bei Geräten mit Hardwareproblemen eine falsche Fehlermeldung angezeigt wurde. Benutzer, die in früheren Versionen einen 1-4-Fehlercode erhalten haben, erhalten nun möglicherweise einen spezifischeren Fehlercode für den Gerätezustand.</li></ul>  |
   | 2000.19071.1302.0  | 13. August 2019     | <ul><li>Unterstützung für Anwendungen mit [openxr](https://docs.microsoft.com/windows/mixed-reality/openxr) auf Geräten mit dem Update von Mai 2019.</li></ul>  | 
   | 2000.19061.1011.0  | 16. Juli 2019         | <ul><li>Unterstützung für JSON-Konfigurationsoptionen zum Anpassen des App-Verhaltens. Weitere Informationen finden Sie unter https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup .</li></ul>  | 

### <a name="steamvr-release-history"></a>Verlauf der steamvr-Version ###

Die Anmerkungen zu dieser Version von "steamvr" finden Sie hier: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality für den Verlauf der steamvr-Version ###

Die Anmerkungen zu dieser Version von Windows Mixed Reality for steamvr finden Sie hier: [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
