---
title: Verwenden von SteamVR mit Windows Mixed Reality
description: Hier erfahren Sie, wie Sie Aufsatz-Headsets Windows Mixed Reality Controller mit kompatiblen PCs einrichten und spielen.
author: qianw211
ms.author: v-qianwen
ms.date: 9/23/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Spiele, SteamVR, Steam, Systemanforderungen
ms.openlocfilehash: b06c5e0b9918a5277a2c31e391dbdbc1ef740110
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436714"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Verwenden von SteamVR mit Windows Mixed Reality

Windows Mixed Reality für SteamVR ermöglicht Benutzern das Ausführen von SteamVR-Umgebungen auf Windows Mixed Reality immersive Headsets. Nach der Installation der Windows Mixed Reality für SteamVR können Benutzer ihre bevorzugten Anwendungen vom Desktop oder aus der Bibliothek "Steam" starten und sie direkt auf ihrem Headset Windows wiedererspielen.

## <a name="get-your-pc-ready"></a>Bereiten Sie Ihren PC vor.

* Stellen Sie sicher, dass keine Updates ausstehen: Wählen **Sie > Einstellungen > Update & Security > Windows Update starten aus.** Wenn Updates verfügbar sind, wählen Sie **Jetzt installieren aus.** Wenn keine Updates verfügbar sind, wählen Sie **Nach Updates suchen** aus, und installieren Sie dann alle neuen Updates.
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

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>Einrichten von Windows Mixed Reality für SteamVR in einer Umgebung ohne Internetzugang

**Store der erforderlichen Medien auf einem portablen Speichergerät**
1. Installieren Sie Wie oben Windows Mixed Reality MitHilfe von [Steam auf](http://store.steampowered.com/about/) einem PC mit vollständigem Internetzugriff Die Installation von [SteamVR](https://store.steampowered.com/app/250820/SteamVR/) und Windows Mixed Reality für [SteamVR.](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)
2. Öffnen Sie in Steam den Abschnitt Bibliothek, und suchen Sie nach dem Teil mit der Bezeichnung "Tools".
3. Klicken Sie nach der Installation von SteamVR mit der rechten Maustaste auf den Eintrag "SteamVR", und klicken Sie im angezeigten Popupmenü auf den Eintrag "Eigenschaften".
4. Ein neues Fenster mit mehreren Registerkarten wird geöffnet. Wählen Sie die Registerkarte "LOKALE DATEIEN" aus, und klicken Sie auf die Schaltfläche mit der Bezeichnung "LOKALE DATEIEN DURCHSUCHEN".
5. Das Verzeichnis, das die "SteamVR Runtime" enthält, wird geöffnet. Kopieren Sie dieses gesamte Verzeichnis (mit dem Namen "DriveVR") auf ein portables Medium Ihrer Wahl (z. B. einen USB-Stick).
6. Gehen Sie genauso vor, Windows Mixed Reality für SteamVR und alle Mit SteamVR kompatiblen Apps verwenden, die Sie auf dem Ziel-PC installieren möchten.

**Ausführen von "SteamVR" auf dem Ziel-PC**
1. Nachdem Sie das portable Speichergerät an den Ziel-PC anschließen, verschieben Sie die Ordner "DriveVR", "MixedRealityVRDriver" und andere Ordner an einen geeigneten Ort auf dem Ziel-PC.
![Auf dem Ziel-PC installierte "SteamVR" und "Windows Mixed Reality for SteamVR"](images/steamvr-install-files.png)

2. Öffnen Sie eine Eingabeaufforderung, um sicherzustellen, dass sich "SteamVR" und "MixedRealityVRDriver" im selben Ordner befinden. Für dieses Beispiel gehen wir davon aus, dass sich der enthaltende Ordner unter *C:\VrVRInstall befindet.* In diesem Fall sollten Sie an der Eingabeaufforderung Folgenden ausführen:
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
(Wenn Sie eine 32-Bit-Version von Windows ausführen, sollte stattdessen der Teil des `win64` obigen Pfads `win32` sein.)

Dadurch kann die Runtime die Windows Mixed Reality für den Driver "SteamVR" in Ihrer benutzerdefinierten Installation finden.

4. Zum Ausführen von SteamVR sollten Sie auf die Datei "vrstartup.exe" doppelklicken, die sich unter *SteamVR\bin\win64\vrstartup.exe* befindet, oder *SteamVR\bin\win32\vrstartup.exe,* wenn auf dem Ziel-PC eine 32-Bit-Version von Windows.

Weitere Informationen und Problembehandlung finden Sie auf der [Dokumentationsseite zuWorks.](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)

## <a name="play-steamvr-games"></a>Play SteamVR-Spiele

1. Verbinden Ihr Headset an Ihren PC an, und schalten Sie die Motion-Controller ein.
2. Nachdem das Windows Mixed Reality geladen wurde und Ihre Controller sichtbar sind, öffnen Sie die App "Steam" auf Ihrem Desktop.
3. Verwenden Sie die "Steam"-App, um ein Game "SteamVR" aus Ihrer Bibliothek "Steam" zu starten.

**Tipp:** Verwenden Sie die Desktop-App (**Start > Desktop**), um Ihre PC-Desktops innerhalb des Desktops zu sehen und mit ihnen Windows Mixed Reality zu interagieren, um Dies zu starten.

## <a name="using-motion-controllers-with-steamvr"></a>Verwenden von Motion-Controllern mit SteamVR

Sie verwenden Ihre Motion-Controller unterschiedlich in verschiedenen Spielen. Hier sind einige Grundlagen für den Einstieg:

* Drücken Sie zum Öffnen des Dashboards "Dashboard" direkt nach unten auf den linken oder rechten Fingerabdruck.
* Klicken Sie auf die Schaltfläche "Windows" , um ein Game vom Windows Mixed Reality zu beenden und zum startenden Windows zurückzukehren.

## <a name="changing-the-resolution"></a>Ändern der Auflösung

Sie können den Schieberegler Anwendungsauflösung jederzeit im Fenster "-> Einstellungen ->-Anwendungen" anpassen, wenn Sie Spiele mit einer höheren Auflösung spielen möchten. **Wenn Sie einen Multiplikator mit höherer Auflösung verwenden, können Sie davon ausgehen, dass ihr PC durch das Spiel stärker belastet wird. Wenn Sie den Multiplikator erhöhen und eine beeinträchtigte Leistung sehen, ändern Sie den Schieberegler auf die Standardebene, und starten Sie das Spiel neu, um sicherzustellen, dass die Änderung wirksam wird.![Anpassen der Anwendungsauflösung](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>Verwenden mehrerer Headsets

Wenn Sie VR-Fan sind, können Sie regelmäßig mehrere VR-Headsets auf demselben PC verwenden. Wenn dies der Fall ist, sollten Sie beachten, dass beim Windows Mixed Reality headset immer Die Spiele von SteamVR mit dem Windows Mixed Reality gestartet werden. Wenn Sie Die Spiele von "SteamVR" auf einem anderen Headset starten möchten, müssen Sie zunächst das Headset Windows Mixed Reality entkabeln, bevor Sie fortfahren.

## <a name="preview-programs"></a>Vorschauprogramme

Wir veröffentlichen regelmäßige Updates, um die Leistung, Zuverlässigkeit und allgemeine Erfahrung der Verwendung von SteamVR auf Windows Mixed Reality immersive Headsets zu verbessern. Auch wenn keines dieser Vorschauprogramme erforderlich ist, empfehlen wir Ihnen, ihnen bei treten, wenn Sie Updates früher und häufiger erhalten möchten (und uns Feedback zu diesen Updates geben! ).

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality für SteamVR Beta

Windows Mixed Reality für SteamVR ist die Komponente, die Sie aus dem "Steam Store" installieren, mit derEntsprechungs-Headsets verwendet Windows Mixed Reality können.  Updates für diese "Brücke" werden regelmäßig veröffentlicht, und Die Installation erfolgt automatisch durch Steam.

Wenn Sie häufiger Updates erhalten möchten, empfehlen wir Ihnen, an unserer öffentlichen Betaversion teil zu nehmen.  Updates werden zuerst an unsere Beta-Zielgruppe gehen, und wir nutzen ihr Feedback, um sicherzustellen, dass die Updates von hoher Qualität sind, bevor sie für alle Benutzer veröffentlicht werden.  Wenn Sie nicht in unserem Betaprogramm sind, erhalten Sie letztendlich alle gleichen Korrekturen und Features, aber nachdem sie von unseren Betabenutzern getestet wurden.

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

Windows Mixed Reality ist Teil von Windows 10 und Windows 11.  Viele Fixes und Features, die sich auf Die Benutzer von SteamVR auswirken, sind mit dem Windows ausgestattet.  Wenn Sie die neuesten Windows 10 und Windows 11 Preview-Builds ausprobieren möchten, empfehlen wir Ihnen, am [Windows Insider Program teil zu nehmen.](https://insider.windows.com)

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>Aktivieren der Neuprojektion von Bewegungen für SteamVR-Apps

Windows Mixed Reality für SmoothVR verfügt über eine experimentelle Funktion für die Neuprojektion von Bewegungen, um eine reibungslosere 90 FPS-Neuprojektion zu ermöglichen.

Wenn die Neuprojektion von Bewegungen aktiviert ist, rendern alle Videos von "Motion VR" nominell mit einer Bildfrequenz von 1/2 (45 fps anstelle von 90 FPS), während Windows Mixed Reality für SteamVR von der GPU generierte Bewegungsvektoren verwendet, um den nächsten Frame zu extrapolieren. Bei Spielen mit Dem-Video-60 FPS und mehr auf einem bestimmten PC sollte dies zu einer soliden FPS-Erfahrung mit 90 FPS mit gelegentlichen Artefakten führen und gleichzeitig ein komfortables Erlebnis gewährleisten.

Die verfügbaren Bewegungs-Reprojection-Modi lauten wie folgt:

* **Einstellung für "Pro-App":** Ermöglicht es Ihnen, die Neuprojektion von Bewegungen über die Ui des Einstellungen zu steuern. Sie können dann die Datei "StreamVR Einstellungen öffnen, zu Video > Per-Application Video Einstellungen wechseln und eine Option für "Motion Smoothing" (Bewegungsglättung) auswählen.
* **Auto:** Ermöglicht das automatische Aktivieren der Neuprojektion von Bewegungen, wenn ein Spiel zu langsam gerendert wird, um 90 FPS zu verwalten. Wenn ein Spiel beginnt, 90 FPS zu verwalten oder mit dem Rendern bei weniger als 45 FPS beginnt, wird die Bewegungs-Neuprojektion deaktiviert. Die asynchrone rotationsbezogene Neuprojektion ist immer aktiviert.
* **Bewegungsvektor:** Erzwingt, dass die Anwendung immer mit halber Framerate mit einer Neuprojektion des Bewegungsvektors ausgeführt wird.
* **Keine:** Deaktiviert die Neuprojektion von Bewegungen.

**Erwartete visuelle Artifacts** 

1. Wenn Sie eine Anwendungsauflösung von mehr als 150 % verwenden, kann es zu unscharf werden. Bei der Neuprojektion von Bewegung wird empfohlen, einen Wert unter 150 % zu verwenden.
2. Ränder mit starkem Kontrast oder Text, insbesondere bei HuDs oder Menüs im Spiel, können aufgrund von Disokklusion vorübergehend verzerrt oder verzerrt aussehen.
3. Die Erfahrung von "50-60 FPS" auf Ihrem PC ist bei Vielen anderen Spielen, die nicht zuverlässig auf 50 bis 60 FPS treffen, weiterhin schlecht.
4. Es wurde gemeldet, dass einige Spiele mit einer Geschwindigkeit von 50 % oder mit erhöhter Latenz (Verzögerung) ausgeführt werden. Melden Sie diese Spiele über die [Windows-Feedback-Hub](filing-feedback.md) anweisungen unten.

Anfänglich verfügen wir über experimentelle Unterstützung für NVidia-GPUs der letzten Generation. Wir iterieren und verbessern unsere Unterstützung für die Neuprojektion von Bewegungen für mehr GPUs, und wir freuen uns auf Ihr Feedback.

**Unterstützte GPUs:** Nvidia GeForce GTX1060, AMD RX470 oder besser, mit Windows Mixed Reality kompatiblen Grafiktreibern installiert.

So aktivieren Sie die Neuprojektion von Bewegungen:

1. Stellen Sie sicher, dass Sie sich mithilfe der obigen Windows Mixed Reality **für Die Betaversion** von SteamVR entschieden haben.
2. Öffnen Sie das Dashboard "SteamVR".
3. Klicken Sie auf der linken Seite auf die Schaltfläche mit dem Windows Mixed Reality Logo, um Windows Mixed Reality **für die Datei "SteamVR"** Einstellungen.
4. Wählen Sie auf der angezeigten Benutzeroberfläche die Registerkarte Grafiken aus.
5. Wählen Sie "Auto" für "Default SteamVR app motion reprojection mode" aus, um die automatische Neuprojektion von Bewegungen zu aktivieren.

![Aktivieren des LSR& LSR-Indikators mit EinstellungenUX](images/settingsux-enable-lsr.gif)

**Motion Reprojection Indicator**

Der Bewegungs-Reprojection-Indikator hilft bei der Diagnose von Problemen mit dem experimentellen Feature für die automatische Bewegungs-Neuprojektion. Wenn sie auf TRUE festgelegt ist, sehen Sie einen Indikator in der oberen linken Ecke Ihrer Headsetanzeige während der automatischen Bewegungs-Neuprojektion. Die Farbe und Position dieses Indikators entsprechen dem aktuellen Bewegungs-Neuprojektionsmodus. Beispiele finden Sie im folgenden Diagramm.

![mvLSR-Indikator](images/mvLSRIndicator.png)

Grün = Die Neuprojektion der Bewegung ist deaktiviert, da die Anwendung mit voller Framerate gerendert werden kann.

Cyan = Motion Reprojection ist ein on, da die Anwendung CPU-gebunden ist.

Blau = Die Neuprojektion der Bewegung ist ein on, da die Anwendung gpu-gebunden ist.

Rot = Die Neuprojektion der Bewegung ist deaktiviert, da die Anwendung mit weniger als halber Framerate ausgeführt wird. Versuchen Sie, super sampling zu reduzieren, wenn aktiviert.

Green + Cyan + Blue = Motion Reprojection befindet sich im Halbbildratenmodus, oder die Anwendung hat eine Erneute Projektion der Bewegung angefordert.

## <a name="sharing-feedback-on-steamvr"></a>Teilen von Feedback zu SteamVR

Ihr Feedback ist von unschätzbarem Wert, wenn es um die Verbesserung der Windows Mixed Reality von SteamVR geht. Übermitteln Sie alle Feedbacks und Fehler über [Windows-Feedback-Hub](filing-feedback.md). Befolgen Sie diese Vorschläge, um uns dabei zu helfen, Ihr Feedback am besten zu erhalten:

1. Geben Feedback-Hub unter "Welche Art von Feedback ist das?" an, dass Sie ein neues Problem melden. -Abschnitt oben.
2. Wählen Sie **Mixed Reality** Kategorie und die **Unterkategorie Apps** aus.
3. Geben Sie das Wort "SteamVR" in die Problemzusammenfassung ein. Dies hilft uns, Ihr Feedback zu finden.
4. Beschreiben Sie, welches Game oder welche Anwendung Von Ihnen verwendet wurde, als Sie auf das Problem bzw. die Anwendung bzw. die Anwendung bzw. die Sie bzw. die sie beim Auft kommen.
5. Fügen Sie Ihrem Feedback einen Bericht des Systems "SteamVR" an. Dadurch werden weitere Protokolle angezeigt, mit denen wir Ihr Problem diagnostizieren können.
    1. Wählen Sie im Fenster "SteamVR" (die kleinen Fenster, in denen der Controllerstatus angezeigt wird) den Titel aus, um das Menü zu öffnen.
    2. Wählen Sie "Systembericht erstellen" aus.
    3. Speichern In Datei.
    4. Fügen Sie die generierte Datei direkt an ihren Feedback-Hub an.
6. Wenn Sie Feedback zur Leistung von SteamVR erhalten, sammeln Sie eine Mixed Reality Leistungsverfolgung: 
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
