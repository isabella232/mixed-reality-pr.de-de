---
title: Verwenden von SteamVR mit Windows Mixed Reality
description: Erfahren Sie, wie Sie Aufsatz- und Controller-Headsets Windows Mixed Reality kompatible pCs einrichten und spielen.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Spiele, SteamVR, Steam, Systemanforderungen
ms.openlocfilehash: 0d79b0c2079875b32387d616e77c5f497ab4aa59
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110150"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Verwenden von SteamVR mit Windows Mixed Reality

Windows Mixed Reality für SteamVR ermöglicht Benutzern das Ausführen von SteamVR-Umgebungen auf Windows Mixed Reality immersive Headsets. Nach der Installation der Windows Mixed Reality für SteamVR können Benutzer ihre bevorzugten Anwendungen vom Pc oder aus der Bibliothek "Steam" starten und sie direkt auf ihrem Windows-Headset wieder geben.

## <a name="get-your-pc-ready"></a>Bereiten Sie Ihren PC vor.

* Stellen Sie sicher, dass keine Updates ausstehen: Wählen **Sie Start > Settings > Update & Security > Windows Update** aus. Wenn Updates verfügbar sind, wählen Sie **Jetzt installieren aus.** Wenn keine Updates verfügbar sind, wählen Sie **Nach Updates suchen** aus, und installieren Sie dann alle neuen Updates.
* Die PC-Anforderungen variieren für die Apps und Inhalte in Steam. Sehen Sie sich die Mindestanforderungen pro Titel an. Ein PC mit einer GTX 1070-Grafikkarte (oder gleichwertig) und einem Intel® Core™ i7-Prozessor sollte eine gute Erfahrung für eine vielzahl von Titeln bieten.
* Richten Sie [Windows Mixed Reality](set-up-windows-mixed-reality.md) ein, falls sie noch nicht vorhanden sind. 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>Einrichten von Windows Mixed Reality für SteamVR

1. [Laden Sie Download und Installation von SteamVR herunter, und installieren Sie es.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. Wenn Sie fertig sind, starten Sie "SteamVR". Das Tutorial zu "SteamVR" sollte automatisch gestartet werden.

> **Hinweis:** Stellen Sie für die erweiterte Problembehandlung Ihres SteamVR-Setups sicher, dass die folgenden Softwarekomponenten installiert sind:
> 1. Installieren [Sie Steam,](http://store.steampowered.com/about/) **und melden Sie sich** **an, oder erstellen Sie ein neues Konto.**
> 2. Installieren [Sie "SteamVR".](https://store.steampowered.com/app/250820/SteamVR/) Wenn Ihr Headset angeschlossen ist, starten Sie Steam, und Es sollte ein Dialogfeld angezeigt werden, in dem Sie aufgefordert werden, SteamVR zu installieren. Befolgen Sie die Anweisungen im Dialogfeld, um es zu installieren.
    * Wenn das Popup nicht angezeigt wird, installieren Sie NavigVR, indem Sie zum *Abschnitt Extras* Ihrer Bibliothek *navigieren.* Suchen Sie in der Liste nach "SteamVR", klicken Sie mit der rechten Maustaste, und wählen Sie *"Install Game" (Spiel installieren) aus.*
> 3. Installieren [Windows Mixed Reality für SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>Einrichten von Windows Mixed Reality für SteamVR in einer Umgebung ohne Internetzugriff

**Speichern der erforderlichen Medien auf einem portablen Speichergerät**
1. Installieren Sie Wie oben Windows Mixed Reality MitHilfe von [Steam auf](http://store.steampowered.com/about/) einem PC mit vollständigem Internetzugriff Die Installation von [SteamVR](https://store.steampowered.com/app/250820/SteamVR/) und das Windows Mixed Reality für [SteamVR.](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)
2. Öffnen Sie in Steam den Abschnitt Bibliothek, und suchen Sie nach dem Teil mit der Bezeichnung "Tools".
3. Klicken Sie nach der Installation von SteamVR mit der rechten Maustaste auf den Eintrag "SteamVR", und klicken Sie im angezeigten Popupmenü auf den Eintrag "Eigenschaften".
4. Ein neues Fenster mit mehreren Registerkarten wird geöffnet. Wählen Sie die Registerkarte "LOKALE DATEIEN" aus, und klicken Sie auf die Schaltfläche mit der Bezeichnung "LOKALE DATEIEN DURCHSUCHEN".
5. Das Verzeichnis, das die "SteamVR Runtime" enthält, wird geöffnet. Kopieren Sie dieses gesamte Verzeichnis (mit dem Namen "DriveVR") auf ein portables Medium Ihrer Wahl (z. B. einen USB-Stick).
6. Gehen Sie genauso vor, Windows Mixed Reality für SteamVR und alle Mit SteamVR kompatiblen Apps verwenden, die Sie auf dem Ziel-PC installieren möchten.

**Ausführen von "SteamVR" auf dem Ziel-PC**
1. Nachdem Sie das portable Speichergerät an den Ziel-PC anschließen, verschieben Sie die Ordner "DriveVR", "MixedRealityVRDriver" und andere Ordner an einen geeigneten Ort auf dem Ziel-PC.
![Auf dem Ziel-PC Windows Mixed Reality Dies sind die Vor- und Windows Mixed Reality von SteamVR, die auf dem Ziel-PC installiert sind.](images/steamvr-install-files.png)

2. Öffnen Sie eine Eingabeaufforderung, um sicherzustellen, dass sich "SteamVR" und "MixedRealityVRDriver" im selben Ordner befinden. Für dieses Beispiel gehen wir davon aus, dass sich der enthaltende Ordner unter *C:\VrVRInstall befindet.* In diesem Fall sollten Sie an der Eingabeaufforderung Folgenden ausführen:
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
(Wenn Sie eine 32-Bit-Version von Windows ausführen, sollte stattdessen der Teil des obigen `win64` Pfads `win32` sein.)

Dadurch kann die Runtime die Windows Mixed Reality für den Driver "SteamVR" in Ihrer benutzerdefinierten Installation finden.

4. Zum Ausführen von SteamVR sollten Sie auf die Datei "vrstartup.exe" unter *SteamVR\bin\win64\vrstartup.exe* oderSteamVR\bin\win32\vrstartup.exe *doppelklicken,* wenn auf dem Ziel-PC eine 32-Bit-Version von Windows ausgeführt wird.

Weitere Informationen und Problembehandlung finden Sie auf der [Dokumentationsseite zuWorks.](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)

## <a name="play-steamvr-games"></a>Play SteamVR-Spiele

1. Verbinden Sie Ihr Headset mit Ihrem PC, und schalten Sie die Motion-Controller ein.
2. Nachdem das Windows Mixed Reality geladen wurde und Ihre Controller sichtbar sind, öffnen Sie die App "Steam" auf Ihrem Desktop.
3. Verwenden Sie die "Steam"-App, um ein Game "SteamVR" aus Ihrer Bibliothek "Steam" zu starten.

**Tipp:** Verwenden Sie die Desktop-App **(Start > Desktop),** um Ihre PC-Desktops innerhalb der App Windows Mixed Reality.

## <a name="using-motion-controllers-with-steamvr"></a>Verwenden von Motion-Controllern mit SteamVR

Sie verwenden Ihre Motion-Controller unterschiedlich in verschiedenen Spielen. Hier sind einige Grundlagen für den Einstieg:

* Drücken Sie zum Öffnen des Dashboards "Dashboard" direkt nach unten auf den linken oder rechten Fingerabdruck.
* Klicken Sie auf die Windows-Schaltfläche, um ein Game vom Windows Mixed Reality zu beenden und zur Startseite zurückzukehren.

## <a name="changing-the-resolution"></a>Ändern der Auflösung

Sie können den Anwendungsauflösungs-Schieberegler im Fenster "Einstellungen -> –> Anwendungen" jederzeit anpassen, wenn Sie Spiele mit einer höheren Auflösung spielen möchten. **Wenn Sie einen Multiplikator mit höherer Auflösung verwenden, können Sie davon ausgehen, dass ihr PC durch das Spiel stärker belastet wird. Wenn Sie den Multiplikator erhöhen und eine beeinträchtigte Leistung sehen, ändern Sie den Schieberegler auf die Standardebene, und starten Sie das Spiel neu, um sicherzustellen, dass die Änderung wirksam wird.![Anpassen der Anwendungsauflösung](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>Verwenden mehrerer Headsets

Wenn Sie VR-Fan sind, können Sie regelmäßig mehrere VR-Headsets auf demselben PC verwenden. Wenn dies der Fall ist, beachten Sie, dass beim Windows Mixed Reality headset immer die Spiele von "SteamVR" mit dem Windows Mixed Reality gestartet werden. Wenn Sie Die Spiele von "SteamVR" auf einem anderen Headset starten möchten, müssen Sie zunächst das Headset Windows Mixed Reality entkabeln, bevor Sie fortfahren.

## <a name="preview-programs"></a>Vorschauprogramme

Wir veröffentlichen regelmäßige Updates, um die Leistung, Zuverlässigkeit und allgemeine Erfahrung der Verwendung von SteamVR auf Windows Mixed Reality immersive Headsets zu verbessern. Auch wenn keines dieser Vorschauprogramme erforderlich ist, empfehlen wir Ihnen, ihnen bei treten, wenn Sie Updates früher und häufiger erhalten möchten (und uns Feedback zu diesen Updates geben! ).

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality für SteamVR Beta

Windows Mixed Reality für SteamVR ist die Komponente, die Sie aus demSpeicher installieren, mit derEntsprechungs-Windows Mixed Reality kann.  Updates für diese "Brücke" werden regelmäßig veröffentlicht, und Die Installation erfolgt automatisch durch Steam.

Wenn Sie häufiger Updates erhalten möchten, empfehlen wir Ihnen, an unserer öffentlichen Betaversion teil zu nehmen.  Updates gehen zuerst an unsere Beta-Zielgruppe, und wir nutzen ihr Feedback, um sicherzustellen, dass die Updates von hoher Qualität sind, bevor sie für alle Benutzer veröffentlicht werden.  Wenn Sie nicht in unserem Betaprogramm sind, erhalten Sie schließlich alle gleichen Korrekturen und Features, aber nachdem sie von unseren Betabenutzern getestet wurden.

So werden Sie beitreten:

  1. Verwenden Sie in Steam die Dropdownliste unter dem Menü **Bibliothek,** um nach **Software zu filtern.**
  2. Klicken Sie in der Liste mit der rechten Maustaste **auf Windows Mixed Reality für SteamVR,** und wählen Sie **Eigenschaften aus.**
  3. Wählen Sie die **Registerkarte Betas** aus.
  4. Aktivieren Sie **"Beta – öffentliche Betaversion",** und wählen Sie **Schließen aus, um** dies zu bestätigen. Das Feld beta access code (Betazugriffscode) sollte leer gelassen werden.
  
### <a name="steamvr-beta"></a>SteamVR Beta

SteamVR wird von Ventilen erstellt und freigegeben und ist für alle Headsets von SteamVR üblich.  Es folgt einem ähnlichen Modell der Veröffentlichung von Updates für Betamitglieder vor der Veröffentlichung für alle Benutzer.

So werden Sie beitreten:

  1. Verwenden Sie in "Steam" die Dropdownliste im Menü **Bibliothek,** um nach **Tools zu filtern.**
  2. Klicken Sie in der Liste mit der rechten Maustaste **auf SteamVR,** und wählen Sie **Eigenschaften aus.**
  3. Wählen Sie die **Registerkarte Betas** aus.
  4. Aktivieren Sie **"Beta – öffentliche Betaversion",** und wählen Sie **Schließen aus, um** dies zu bestätigen.  Das Feld beta access code (Betazugriffscode) sollte leer gelassen werden. ![ Wechseln Sie im Dialogfeld "Eigenschaften" für "SteamVR" zur Betaversion von "SteamVR".](images/steamvr-beta.png)

### <a name="windows-insider-program"></a>Windows-Insider-Programm

Windows Mixed Reality ist Teil der Windows 10.  Viele Korrekturen und Features, die sich auf Die Benutzer von SteamVR auswirken, sind im Windows-Betriebssystem verfügbar.  Wenn Sie die neuesten Vorschauversionen Windows 10 testen möchten, empfehlen wir Ihnen, am Windows-Insider [teilnehmen.](https://insider.windows.com)

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>Aktivieren der Neuprojektion von Bewegungen für SteamVR-Apps

Windows Mixed Reality für SmoothVR verfügt über eine experimentelle Funktion für die Neuprojektion von Bewegungen, um eine reibungslosere 90 FPS-Neuprojektion zu ermöglichen.

Wenn die Neuprojektion von Bewegungen aktiviert ist, rendern alle Videos von "Motion VR" nominell mit einer Bildfrequenz von 1/2 (45 fps anstelle von 90 FPS), während Windows Mixed Reality für SteamVR von der GPU generierte Bewegungsvektoren verwendet, um den nächsten Frame zu extrapolieren. Bei Spielen mit Dem-Video-60 FPS und mehr auf einem bestimmten PC sollte dies zu einer soliden FPS-Erfahrung mit 90 FPS mit gelegentlichen Artefakten führen und gleichzeitig ein komfortables Erlebnis gewährleisten.

Die verfügbaren Bewegungs-Umprojektionsmodi lauten wie folgt:

* **Einstellung für "Pro-App":Ermöglicht** ihnen das Steuern der Neuprojektion von Bewegungen über die Ui der Einstellungen für "SteamVR". Sie können dann "StreamVR-Einstellungen" öffnen, zu Video > Per-Application Videoeinstellungen wechseln und eine Option für "Motion Smoothing" (Bewegungsglättung) auswählen.
* **Auto:** Ermöglicht das automatische Aktivieren der Neuprojektion von Bewegungen, wenn ein Spiel zu langsam gerendert wird, um 90 FPS zu verwalten. Wenn ein Spiel mit der Beibehaltung von 90 FPS beginnt oder mit dem Rendern bei weniger als 45 FPS beginnt, wird die Neuprojektion der Bewegung deaktiviert. Die asynchrone rotationsbezogene Neuprojektion ist immer aktiviert.
* **Bewegungsvektor:** Erzwingt, dass die Anwendung immer mit halber Framerate mit einer Neuprojektion des Bewegungsvektors ausgeführt wird.
* **Keine:** Deaktiviert die Neuprojektion von Bewegungen.

**Erwartete visuelle Artefakte** 

1. Wenn Sie eine Anwendungsauflösung von mehr als 150 % verwenden, kann es zu unscharf werden. Bei der Neuprojektion von Bewegung wird empfohlen, einen Wert unter 150 % zu verwenden.
2. Ränder mit starkem Kontrast oder Text, insbesondere bei HuDs oder Menüs im Spiel, können aufgrund von Disokklusion vorübergehend verzerrt oder verzerrt aussehen.
3. Die Erfahrung von "50-60 FPS" auf Ihrem PC ist bei Vielen anderen Spielen, die nicht zuverlässig auf 50 bis 60 FPS treffen, weiterhin schlecht.
4. Es wurde gemeldet, dass einige Spiele mit einer Geschwindigkeit von 50 % oder mit erhöhter Latenz (Verzögerung) ausgeführt werden. Melden Sie diese Spiele über die [Windows-Feedback-Hub](filing-feedback.md) anweisungen unten.

Anfänglich verfügen wir über experimentelle Unterstützung für NVidia-GPUs der letzten Generation. Wir iterieren und verbessern unsere Unterstützung für die Neuprojektion von Bewegungen für mehr GPUs, und wir freuen uns auf Ihr Feedback.

**Unterstützte GPUs:** Nvidia GeForce GTX1060, AMD RX470 oder besser, mit Windows Mixed Reality kompatiblen Grafiktreibern installiert.

So aktivieren Sie die Neuprojektion von Bewegungen:

1. Stellen Sie anhand der obigen Anweisungen sicher, dass Sie sich für Windows Mixed Reality **für Die Betaversion von SteamVR** entschieden haben.
2. Öffnen Sie das Dashboard "SteamVR".
3. Klicken Sie auf der linken Seite auf die Schaltfläche mit dem Windows Mixed Reality Logo, um Windows Mixed Reality **für Die Einstellungen von "Vr" zu** öffnen.
4. Wählen Sie auf der angezeigten Benutzeroberfläche die Registerkarte Grafik aus.
5. Wählen Sie "Auto" für "Default SteamVR app motion reprojection mode" aus, um die automatische Neuprojektion von Bewegungen zu aktivieren.

![Aktivieren des LSR& LSR-Indikators mit EinstellungenUX](images/settingsux-enable-lsr.gif)

**Motion Reprojection Indicator**

Der Indikator für die Neuprojektion von Bewegungen hilft bei der Diagnose von Problemen mit der experimentellen Automatischen Bewegungs-Neuprojektion. Wenn sie auf TRUE festgelegt ist, wird links oben auf der Headsetanzeige während der automatischen Bewegungs-Neuprojektion ein Indikator angezeigt. Die Farbe und Position dieses Indikators entsprechen dem aktuellen Bewegungs-Reprojektionsmodus. Beispiele finden Sie im folgenden Diagramm.

![mvLSR-Indikator](images/mvLSRIndicator.png)

Grün = Die Neuprojektion der Bewegung ist deaktiviert, da die Anwendung mit voller Framerate gerendert werden kann.

Cyan = Motion Reprojection ist ein on, da die Anwendung CPU-gebunden ist.

Blau = Die Neuprojektion der Bewegung ist ein on, da die Anwendung gpu-gebunden ist.

Rot = Die Neuprojektion der Bewegung ist deaktiviert, da die Anwendung mit weniger als halber Framerate ausgeführt wird. Versuchen Sie, super sampling zu reduzieren, wenn aktiviert.

Green + Cyan + Blue = Motion Reprojection befindet sich im Halbbildratemodus oder die von der Anwendung angeforderte Bewegungsprojektion.

## <a name="sharing-feedback-on-steamvr"></a>Teilen von Feedback zu SteamVR

Ihr Feedback ist von unschätzbarem Wert, wenn es um die Verbesserung der Windows Mixed Reality von SteamVR geht. Übermitteln Sie alle Feedbacks und Fehler über [Windows-Feedback-Hub](filing-feedback.md). Befolgen Sie diese Vorschläge, um uns dabei zu helfen, Ihr Feedback am besten zu erhalten:

1. Geben Feedback-Hub unter "Welche Art von Feedback ist das?" ein neues Problem an. -Abschnitt oben.
2. Wählen Sie **Mixed Reality** Kategorie und die **Unterkategorie Apps** aus.
3. Geben Sie das Wort "SteamVR" in die Problemzusammenfassung ein. Dies hilft uns, Ihr Feedback zu finden.
4. Beschreiben Sie, welches Spiel oder welche Anwendung Von Ihnen verwendet wurde, als Sie auf das Problem bzw. die Anwendung bzw. die Anwendung bzw. die Sie bzw. die sie beim Beheben des Problems bzw. der Anwendung bzw. des Problems
5. Fügen Sie Ihrem Feedback einen Bericht des Systems "SteamVR" an. Dadurch werden weitere Protokolle angezeigt, mit denen wir Ihr Problem diagnostizieren können.
    1. Wählen Sie im Fenster "SteamVR" (die kleinen Fenster, in denen der Controllerstatus angezeigt wird) den Titel aus, um das Menü zu öffnen.
    2. Wählen Sie "Systembericht erstellen" aus.
    3. Speichern In Datei.
    4. Fügen Sie die generierte Datei direkt an ihren Feedback-Hub an.
6. Wenn Sie Feedback zur Leistung von SteamVR erhalten, sammeln Sie eine Mixed Reality Performance-Ablaufverfolgung: 
    1. Wählen Sie die **Schaltfläche Mein Problem neu** erstellen aus.
    2. Wählen Sie in der Dropdownliste neben "Include data about" (Daten zu enthalten) **Mixed Reality Performance (Leistung) aus.**
    3. Stellen Sie sicher, dass das Spiel ausgeführt wird, und wählen **Sie Erfassung starten aus.**
    4. Verbringen Sie einige Sekunden mit dem Spiel, um die Ablaufverfolgung zu erfassen. Erfassen Sie die Ablaufverfolgung nicht länger als 10 bis 15 Sekunden, oder sie ist zu groß, um sie zu übermitteln.
    5. Wählen Sie **Erfassung beenden aus.**
7. Wählen **Sie Senden** aus, nachdem Sie die restlichen Felder ausgefüllt haben.

Wenn Sie Fragen oder Kommentare teilen möchten, können Sie uns auch über unser [Forum zu Erhalten.](http://steamcommunity.com/app/719950/discussions/)

## <a name="see-also"></a>Siehe auch

* [Problembehandlung für SteamVR mit Windows Mixed Reality](steamvr-questions.md)
* [Verwenden von Spielen und Apps in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Verwenden von HP-Controllern in Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [Verwenden von HP-Controllern in Unreal](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [Einreichen von Bugs und Feedback](filing-feedback.md)
