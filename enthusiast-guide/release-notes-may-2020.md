---
title: Versionshinweise – Mai 2020
description: Bleiben Sie auf dem neuesten Stand zu den Windows Mixed Reality Versionshinweisen für das Update Windows 10 Mai 2020.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Versionshinweise, Version, Windows 10, Build, 19h1, os, Mai 2020
ms.openlocfilehash: 462fcbfa10cfff8df23c970fd54ee0754a4d9472
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439165"
---
# <a name="windows-10-release-notes---may-2020"></a>Windows 10 Anmerkungen zu dieser Version – Mai 2020

Das Windows 10 Update vom **Mai 2020 (v2004)** enthält neue Features für Windows Mixed Reality Headsets (VR), z. B. die Möglichkeit, Win32-Anwendungen im Mixed Reality Startumgebung zu starten. HoloLens (1. Generation) befindet sich in Long Term Servicing (LTS), wobei Wartungsupdates monatlich veröffentlicht werden.

Wenn Sie ein Upgrade auf die neueste PC-Version für Windows Mixed Reality immersive Headsets (VR) durchführen, öffnen **Sie Einstellungen > Update & Security,** und wählen Sie Nach Updates **suchen** aus. Auf einem Windows 10 PC können Sie das Windows 10 Update vom **Mai 2020** auch manuell installieren, indem Sie das [tool zum Erstellen von Windows Medien](https://www.microsoft.com/software-download/windows10)verwenden.

**Neuestes Release für Desktop:** Windows 10 v2004 (10.0.19041.264)

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Updates für Windows Mixed Reality immersive Headsets

### <a name="introducing-the-new-microsoft-edge"></a>Vorstellung des neuen Microsoft Edge

Wie [bereits angekündigt,](/windows/mixed-reality/new-microsoft-edge)haben wir Updates vorgenommen, um die Unterstützung mithilfe des neuen Microsoft Edge-Browsers in Windows Mixed Reality zu verbessern. Die neue Microsoft Edge übernimmt das Chromium Open-Source-Projekt, um eine bessere Webkompatibilität für Kunden und eine geringere Fragmentierung des Webs für alle Webentwickler zu schaffen. Es unterstützt auch WebXR, den neuen Standard zum Erstellen immersiver Weberfahrungen für VR-Headsets anstelle von WebVR.

### <a name="improved-settings-for-wmr"></a>Verbesserte Einstellungen für WMR

Dank Ihres Feedbacks haben wir Einstellungen auf der Headset-Anzeigeseite hinzugefügt und verdeutlicht:

* **Visuelle Qualität meines Hauses:** Das Ändern dieser Einstellungen wirkt sich nur auf die Mixed Reality Startumgebung Umgebung (Haus an den Klippen und Skyitatt) aus:

* **Passen Sie den Detailgrad und die Qualität der Effekte im Mixed Reality Startumgebung** an. Dies ändert einige der Renderingeffekte, die wir im Home-Bereich verwenden. Insbesondere die visuelle Qualität verschiedener Materialien (Wood, Concrete usw.) wird skaliert, wenn Sie diese Einstellung von niedrig in hoch ändern.

* Ändern der Auflösung des **App-Fensters:** Standardmäßig werden die meisten 2D-Fenster, die in der Startseite gestartet werden, mit einer Auflösung von 720 p gestartet. Sie können die Größe manuell horizontal & vertikal ändern, aber Sie können auch entscheiden, dass sie alle stattdessen mit 1080p gestartet werden. Zuvor war diese Option unter Visuelle Qualität als Option Sehr hoch (Beta) verfügbar. Wir haben es jetzt entsprechend als separate Einstellung aufgeteilt.

* **Erfahrungsoptionen:** Diese Optionen passen die Mixed Reality-Erfahrung an, um die Auslastung von Systemen zu reduzieren, bei denen die Hardware mit uneingeschränkten 90 Fps nicht schritthalten kann. Sie können diese zusätzlichen Einstellungen explizit aktivieren oder deaktivieren, oder Wählen Sie Let Windows decide (Entscheiden Windows), und lassen Sie unsere Heuristik weiter entscheiden, wann diese ein- und ausgeschaltet werden sollen.

* **Lösung:** Wenn Sie über ein hochauflösendes Headset wie HP Reverb verfügen, wird die Ausführung mit der nativen Auflösung oder mit einer reduzierten Auflösung aus Leistungsgründen unterstützt. Frühere Headsets wie Samsung Odyssey und Odyssey+ unterstützen nur eine einzige Auflösung, sodass Sie diese Einstellung auf diesen Headsets nicht ändern können.

* **Bildfrequenz:** Sie können jetzt manuell die Bildfrequenz der Headsetanzeige festlegen oder weiterhin Windows die Heuristik verwenden, um zu bestimmen, ob 60 Hz oder 90 Hz besser geeignet sind.

* **Kalibrierung:** Wie zuvor können Sie Ihre IPD (Interpupillary Distance) anpassen, wenn sie von Ihrem Headset unterstützt wird.

* **Eingabewechsel:** Schalten Sie das Verhalten des Eingabefokuswechsels (Win+Y) automatisch (basierend auf Feedback des Präsenzsensors) oder manuell um.

### <a name="new-cortana-app"></a>Neue Cortana-App

Dieses Update für Windows enthält die neueste Version der Cortana-App, die derzeit nur auf Englisch (USA) verfügbar ist und bestimmte Mixed Reality-spezifische Befehle wie "Aufnahme eines Bilds" und "Video aufnehmen" nicht mehr unterstützt. Sie können die neue Cortana verwenden, um Apps zu starten, und sie unterstützt auch neue produktivitätsorientierte Befehle wie "Wann ist meine nächste Besprechung?" oder "Send an email to \< name \> that I'm running late".
    
### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Zusätzliche Updates in verfügbar in 19041.546 (veröffentlicht im Oktober 2020)

Dieses monatliche Desktopwartungsupdate umfasst die folgenden Änderungen für Windows Mixed Reality Geräte: 
* Reduziert Verzerrungen und Abweichungen in Windows Mixed Reality HMD (Head-Mounted Displays). 
* Fügt Unterstützung für zukünftige HP Windows Mixed Reality Motion-Controller hinzu. 
* Ändert das Verhalten der Einstellung für die 90-Hz-Aktualisierungsrate in Windows Mixed Reality so, dass in bestimmten Fällen nicht mehr automatisch auf 60 Hz zurückgeschaltet wird, wenn 90 Hz nicht erreicht werden können. 

### <a name="help-us-improve"></a>Helfen Sie uns bei der Verbesserung!

Wir versuchen ständig, die Kompatibilität zu verbessern.  Wenn Sich Ihre bevorzugte klassische Win32-Anwendung in Windows Mixed Reality nicht richtig verhält, senden Sie Feedback über unsere [Feedback-Hub](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

## <a name="prior-release-notes"></a>Anmerkungen zu früheren Versionen

* [Versionshinweise – Mai 2019](release-notes-may-2019.md)
* [Versionshinweise – Oktober 2018](release-notes-october-2018.md)
* [Versionshinweise – April 2018](release-notes-april-2018.md)
* [Versionshinweise – Oktober 2017](release-notes-october-2017.md)
* [Versionshinweise – August 2016](release-notes-august-2016.md)
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [Unterstützung für immersive Headsets (externer Link)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens-Unterstützung (externer Link)](https://support.microsoft.com/products/hololens)
* [Installieren der Tools](/windows/mixed-reality/develop/install-the-tools)
* [Geben Sie uns Feedback](/windows/mixed-reality/give-us-feedback)