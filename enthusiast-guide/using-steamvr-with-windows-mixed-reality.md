---
title: Verwenden von SteamVR mit Windows Mixed Reality
description: Erfahren Sie, wie Sie Auf Windows Mixed Reality Headsets und Controllern mit kompatiblen PCs Ein- und Wiedergabe von SteamVR-Spielen ausführen.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Spiele, SteamVR, Steam, Systemanforderungen
ms.openlocfilehash: 641f2b7db890229b88c0614b6b2bc2e3e88ec309
ms.sourcegitcommit: 65f58055c831d58a3d38fb333f09b323ee2ac9b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2021
ms.locfileid: "112064119"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Verwenden von SteamVR mit Windows Mixed Reality

Windows Mixed Reality für SteamVR ermöglicht Benutzern das Ausführen von SteamVR-Erfahrungen auf Windows Mixed Reality immersiven Headsets. Nach der Installation der Windows Mixed Reality für SteamVR können Benutzer ihre bevorzugten SteamVR-Anwendungen über ihren Desktop oder ihre Steam-Bibliothek starten und direkt auf ihrem Windows-Headset wiedergeben.

## <a name="get-your-pc-ready"></a>Bereiten Sie Ihren PC vor.

* Stellen Sie sicher, dass keine Updates ausstehen: Wählen Sie **Start > Settings > Update & Security > Windows Update aus.** Wenn Updates verfügbar sind, wählen **Sie Jetzt installieren** aus. Wenn keine Updates verfügbar sind, wählen **Sie Nach Updates suchen** aus, und installieren Sie dann alle neuen Updates.
* Die PC-Anforderungen variieren für die Apps und Inhalte auf Steam. Sehen Sie sich die Mindestanforderungen pro Titel an. Ein PC mit einer GTX 1070-Grafikkarte (oder einem entsprechenden Prozessor) und einem Intel® Core™ i7-Prozessor sollte eine gute Erfahrung für eine vielzahl von Titeln bieten.
* Richten Sie [Windows Mixed Reality](set-up-windows-mixed-reality.md) ein, sofern noch nicht erfolgt. 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>Einrichten Windows Mixed Reality für SteamVR

1. [Laden Sie SteamVR herunter, und installieren Sie es.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. Wenn Sie fertig sind, starten Sie SteamVR. Das Tutorial zu SteamVR sollte automatisch gestartet werden.

> **Hinweis:** Stellen Sie für die erweiterte Problembehandlung ihres SteamVR-Setups sicher, dass die folgenden Softwarekomponenten installiert sind:
> 1. Installieren Sie [Steam,](http://store.steampowered.com/about/) und **melden Sie sich an,** oder **erstellen Sie ein neues Konto.**
> 2. Installieren Sie [SteamVR](https://store.steampowered.com/app/250820/SteamVR/). Wenn Ihr Headset angeschlossen ist, starten Sie Steam, und Es sollte ein Dialogfeld angezeigt werden, in dem Sie zur Installation von SteamVR aufgefordert werden. Befolgen Sie die Anweisungen im Dialogfeld, um es zu installieren.
    * Wenn das Popup nicht angezeigt wird, installieren Sie SteamVR, indem Sie zum Abschnitt *Extras* Ihrer *Bibliothek* navigieren. Suchen Sie In der Liste nach SteamVR, klicken Sie mit der rechten Maustaste, und wählen *Sie Spiel installieren* aus.
> 3. Installieren Sie [Windows Mixed Reality für SteamVR.](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>Einrichten Windows Mixed Reality für SteamVR in einer Umgebung ohne Internetzugriff

**Speichern der erforderlichen Medien auf einem portablen Speichergerät**
1. Installieren Sie [SteamVR](https://store.steampowered.com/app/250820/SteamVR/) und [Windows Mixed Reality für SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) wie oben beschrieben [mitHilfe](http://store.steampowered.com/about/) von Steam auf einem PC mit vollständigem Internetzugriff.
2. Öffnen Sie in Steam den Abschnitt Bibliothek, und suchen Sie nach dem Teil mit der Bezeichnung "Tools".
3. Klicken Sie nach der Installation von SteamVR mit der rechten Maustaste auf den Eintrag "SteamVR", und klicken Sie im daraufhin angezeigten Popupmenü auf den Eintrag "Eigenschaften".
4. Ein neues Fenster mit mehreren Registerkarten wird geöffnet. Wählen Sie die Registerkarte "LOKALE DATEIEN" aus, und klicken Sie auf die Schaltfläche mit der Bezeichnung "LOKALE DATEIEN DURCHSUCHEN".
5. Das Verzeichnis, das die SteamVR Runtime enthält, wird geöffnet. Kopieren Sie dieses gesamte Verzeichnis (mit dem Namen "SteamVR") auf ein portables Medium Ihrer Wahl (z. B. ein USB-Stick).
6. Verwenden Sie dasselbe mit Windows Mixed Reality für SteamVR und allen Mit SteamVR kompatiblen Apps, die Sie auf dem Ziel-PC installieren möchten.

**Ausführen von SteamVR auf dem Ziel-PC**
1. Nachdem Sie das portable Speichergerät an den Ziel-PC angeschlossen haben, verschieben Sie die Ordner "SteamVR", "MixedRealityVRDriver" und andere Ordner an einen geeigneten Ort auf dem Ziel-PC.
2. Stellen Sie sicher, dass sich SteamVR und MixedRealityVRDriver im selben Ordner befinden, laden [ Siesteamvr-add-wmr-driver.bat](scripts/steamvr-add-wmr-driver.bat) in den enthaltenden Ordner herunter, und doppelklicken Sie darauf. Dadurch kann die Runtime die Windows Mixed Reality für den SteamVR-Treiber in Ihrer benutzerdefinierten Installation finden.
![SteamVR und Windows Mixed Reality für Auf dem Ziel-PC installiertes SteamVR](images/steamvr-install-files.png)
3. Zum Ausführen von SteamVR sollten Sie auf die Datei "vrstartup.exe" doppelklicken, die sich unter *SteamVR\bin\win64\vrstartup.exe* befindet, oder *SteamVR\bin\win32\vrstartup.exe,* wenn auf dem Ziel-PC eine 32-Bit-Version von Windows ausgeführt wird.

Weitere Informationen und Problembehandlung finden Sie auf der [Dokumentationsseite zu Steamworks.](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)

## <a name="play-steamvr-games"></a>Play SteamVR games

1. Verbinden Sie Ihr Headset mit Ihrem PC, und aktivieren Sie Ihre Motion-Controller.
2. Nachdem die Windows Mixed Reality Home geladen wurde und Ihre Controller sichtbar sind, öffnen Sie die Steam-App auf Ihrem Desktop.
3. Verwenden Sie die Steam-App, um ein SteamVR-Spiel aus Ihrer Steam-Bibliothek zu starten.

**Tipp:** Verwenden Sie zum Starten von SteamVR-Spielen ohne Das Headset die Desktop-App (**Start > Desktop**), um Ihren PC-Desktop innerhalb Windows Mixed Reality anzuzeigen und mit ihnen zu interagieren.

## <a name="using-motion-controllers-with-steamvr"></a>Verwenden von Motion Controllers mit SteamVR

Sie verwenden Ihre Motion-Controller in verschiedenen Spielen unterschiedlich. Im Folgenden finden Sie einige Grundlegendes zu den ersten Schritte:

* Um das Dashboard "Steam" zu öffnen, drücken Sie direkt nach unten auf dem linken oder rechten Daumenstick.
* Klicken Sie auf die Windows-Schaltfläche, um ein SteamVR-Spiel zu beenden und zum Windows Mixed Reality Home zurückzukehren.

## <a name="changing-the-resolution"></a>Ändern der Auflösung

Sie können den Schieberegler "Anwendungsauflösung" jederzeit im Fenster "SteamVR -> Settings -> Applications" anpassen, wenn Sie Spiele mit höherer Auflösung spielen möchten. **Wenn Sie einen Multiplikator mit höherer Auflösung verwenden, können Sie davon ausgehen, dass das Spiel auf Ihrem PC mehr Belastungen mit sich bringen wird. Wenn Sie den Multiplikator erhöhen und eine beeinträchtigte Leistung feststellen, ändern Sie den Schieberegler auf die Standardebene, und starten Sie das Spiel neu, um sicherzustellen, dass die Änderung wirksam wird.![Anpassen der Anwendungsauflösung](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>Verwenden mehrerer Headsets

Wenn Sie VR-Fan sind, können Sie regelmäßig mehrere VR-Headsets auf demselben PC verwenden. Wenn dies der Fall ist, beachten Sie Folgendes: Wenn ein Windows Mixed Reality Headset angeschlossen ist, werden die SteamVR-Spiele immer auf dem Windows Mixed Reality Headset gestartet. Wenn Sie SteamVR-Spiele auf einem anderen Headset starten möchten, trennen Sie zuerst das Windows Mixed Reality Headset, bevor Sie fortfahren.

## <a name="preview-programs"></a>Vorschauprogramme

Wir veröffentlichen regelmäßige Updates, um die Leistung, Zuverlässigkeit und allgemeine Erfahrung der Verwendung von SteamVR auf Windows Mixed Reality immersiven Headsets zu verbessern. Obwohl keines dieser Vorschauprogramme erforderlich ist, empfehlen wir Ihnen, diese zu verwenden, wenn Sie updates früher und häufiger erhalten möchten (und uns Feedback zu diesen Updates geben! ).

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality für Die Betaversion von SteamVR

Windows Mixed Reality für SteamVR ist die Komponente, die Sie aus dem Steam Store installieren, mit der SteamVR mit Ihrem Windows Mixed Reality Headset arbeiten kann.  Updates für diese "Bridge" werden regelmäßig veröffentlicht, und Diese werden von Steam automatisch installiert.

Wenn Sie häufiger Updates erhalten möchten, empfehlen wir Ihnen, unserer öffentlichen Betaversion beizutreten.  Updates gehen zuerst an unsere Beta-Zielgruppe, und wir verwenden ihr Feedback, um sicherzustellen, dass die Updates eine hohe Qualität aufweisen, bevor sie für alle Benutzer veröffentlicht werden.  Wenn Sie nicht in unserem Betaprogramm sind, erhalten Sie schließlich die gleichen Fixes und Features, aber nachdem sie von unseren Betabenutzern getestet wurden.

So treten Sie hinzu:

  1. Verwenden Sie in Steam das Dropdownmenü im Menü **Bibliothek,** um nach **Software** zu filtern.
  2. Klicken Sie in der Liste mit der rechten Maustaste auf **Windows Mixed Reality für SteamVR,** und wählen Sie **Eigenschaften** aus.
  3. Wählen Sie die Registerkarte **Betas** aus.
  4. Aktivieren Sie **"beta - public beta",** und wählen Sie **Schließen** aus, um dies zu bestätigen. Das Feld Betazugriffscode sollte leer gelassen werden.
  
### <a name="steamvr-beta"></a>SteamVR Beta

SteamVR wird von Valve erstellt und freigegeben und ist für alle SteamVR-Headsets üblich.  Es folgt einem ähnlichen Modell der Freigabe von Updates für Betamitglieder, bevor sie für alle Benutzer veröffentlicht werden.

So treten Sie hinzu:

  1. Verwenden Sie in Steam das Dropdownmenü im Menü **Bibliothek,** um nach **Extras** zu filtern.
  2. Klicken Sie in der Liste mit der rechten Maustaste auf **SteamVR,** und wählen Sie **Eigenschaften** aus.
  3. Wählen Sie die Registerkarte **Betas** aus.
  4. Aktivieren Sie **"beta - public beta",** und wählen Sie **Schließen** aus, um dies zu bestätigen.  Das Feld Betazugriffscode sollte leer gelassen werden. ![ Wechseln Sie im Eigenschaftendialogfeld für SteamVR zur Betaversion von SteamVR.](images/steamvr-beta.png)

### <a name="windows-insider-program"></a>Windows-Insider-Programm

Windows Mixed Reality ist Teil von Windows 10.  Viele Fixes und Features, die sich auf Die Benutzer von SteamVR auswirken, sind mit dem Windows-Betriebssystem ausgestattet.  Wenn Sie die neuesten Windows 10-Vorschaubuilds ausprobieren möchten, empfehlen wir Ihnen, am [Windows-Insider-Programm](https://insider.windows.com)teilzunehmen.

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>Aktivieren der Bewegungsreprojektion für SteamVR-Apps

Windows Mixed Reality für SteamVR verfügt über eine experimentelle Funktion zur Bewegungsreprojektion, um die 90 FPS-Neuprojektion reibungsloser zu gestalten.

Wenn die Neuprojektion von Bewegung aktiviert ist, werden alle Vr-Spiele von Steam nominell mit einer Bildfrequenz von 1/2 gerendert (45 fps anstelle von 90 FPS), während Windows Mixed Reality für SteamVR bewegungsvektoren verwendet, die von der GPU generiert werden, um den nächsten Frame zu extrapolieren. Für SteamVR-Spiele, die zuverlässig 60 FPS+ auf einem bestimmten PC erreicht haben, sollte dies zu einer soliden FPS-Erfahrung von 90 FPS mit gelegentlichen Artefakten führen und gleichzeitig eine komfortable Erfahrung gewährleisten.

Die verfügbaren Bewegungsreprojektionsmodi sind wie folgt:

* Einstellung für **"SteamVR pro App":** Ermöglicht ihnen das Steuern der Bewegungsreprojektion über die Benutzeroberfläche der SteamVR-Einstellungen. Sie können dann Die SteamVR-Einstellungen öffnen, zu Video > Per-Application Videoeinstellungen wechseln und eine Option für "Bewegungsglättung" auswählen.
* **Automatisch:** Ermöglicht die erneute Bewegungsprojektion, um automatisch zu aktivieren, wenn ein Spiel zu langsam gerendert wird, um 90 FPS beizubehalten. Wenn ein Spiel beginnt, 90 FPS beizubehalten, oder mit dem Rendern bei weniger als 45 FPS beginnt, wird die Bewegungsreprojektion deaktiviert. Die asynchrone Rotationsreprojektion ist immer aktiviert.
* **Bewegungsvektor:** Erzwingt, dass die Anwendung immer mit halber Framerate mit Einer-Bewegung-Vektor-Neuprojektion ausgeführt wird.
* **Keine:** Deaktiviert die Neuprojektion von Bewegungen.

**Erwartete visuelle Artefakte** 

1. Wenn Sie eine Anwendungsauflösung von mehr als 150 % verwenden, kann es zu unscharf werden. Bei der Neuprojektion von Bewegungen wird empfohlen, einen Wert unter 150 % zu verwenden.
2. Ränder oder Text mit starkem Kontrast, insbesondere bei HuDs oder Menüs im Spiel, können aufgrund von Disokklusion vorübergehend verzerrt oder verzerrt aussehen.
3. Die Erfahrung von "SteamVR Home" und vielen anderen Spielen, die auf Ihrem PC nicht zuverlässig auf 50 bis 60 FPS treffen, ist mit diesem Modus weiterhin schlecht.
4. Es wurde gemeldet, dass einige Spiele mit einer Geschwindigkeit von 50 % oder mit erhöhter Latenz (Verzögerung) ausgeführt werden. Melden Sie diese Spiele über die [Windows-Feedback-Hub](filing-feedback.md) anweisungen unten.

Anfänglich verfügen wir über experimentelle Unterstützung für NVidia-GPUs der letzten Generation. Wir iterieren und verbessern unsere Unterstützung für die Neuprojektion von Bewegungen für weitere GPUs, und wir freuen uns auf Ihr Feedback.

**Unterstützte GPUs:** Nvidia GeForce GTX1060, AMD RX470 oder besser, mit Windows Mixed Reality kompatiblen Grafiktreibern installiert.

So aktivieren Sie die Neuprojektion von Bewegungen:

1. Stellen Sie anhand der obigen Anweisungen sicher, dass Windows Mixed Reality **für Die Betaversion von SteamVR** verwendet haben.
2. Öffnen Sie das Dashboard "SteamVR".
3. Klicken Sie auf der linken Seite auf die Schaltfläche mit dem Windows Mixed Reality Logo, um Windows Mixed Reality **für Die Einstellungen von "SteamVR" zu** öffnen.
4. Wählen Sie auf der angezeigten Benutzeroberfläche die Registerkarte Grafiken aus.
5. Wählen Sie "Auto" für "Default SteamVR app motion reprojection mode" aus, um die automatische Neuprojektion von Bewegungen zu aktivieren.

![Aktivieren des LSR& LSR-Indikators mit EinstellungenUX](images/settingsux-enable-lsr.gif)

**Motion Reprojection Indicator**

Der Bewegungs-Reprojection-Indikator hilft bei der Diagnose von Problemen mit der experimentellen Automatischen Bewegungs-Neuprojektion. Wenn der Wert auf TRUE festgelegt ist, wird links oben auf der Headsetanzeige während der automatischen Bewegungs-Neuprojektion ein Indikator angezeigt. Die Farbe und Position dieses Indikators entsprechen dem aktuellen Bewegungs-Neuprojektionsmodus. Beispiele finden Sie im folgenden Diagramm.

![mvLSR-Indikator](images/mvLSRIndicator.png)

Grün = Neuprojektion der Bewegung ist deaktiviert, da die Anwendung mit voller Framerate gerendert werden kann.

Cyan = Motion Reprojection ist ein on, da die Anwendung CPU-gebunden ist.

Blue = Motion Reprojection ist ein on, da die Anwendung GPU-gebunden ist.

Rot = Erneutes Projektieren von Bewegung ist deaktiviert, da die Anwendung mit weniger als halber Framerate ausgeführt wird. Versuchen Sie, super sampling zu reduzieren, wenn aktiviert.

Green + Cyan + Blue = Motion Reprojection befindet sich im Halbbildratemodus oder die von der Anwendung angeforderte Bewegungsprojektion.

## <a name="sharing-feedback-on-steamvr"></a>Teilen von Feedback zu SteamVR

Ihr Feedback ist von unschätzbarem Wert, wenn es um die Verbesserung der Windows Mixed Reality von SteamVR geht. Übermitteln Sie alle Feedbacks und Fehler über [Windows-Feedback-Hub](filing-feedback.md). Befolgen Sie diese Vorschläge, um uns dabei zu helfen, Ihr Feedback am besten zu erhalten:

1. Geben Feedback-Hub in der Meldung "Welche Art von Feedback ist das?" an, dass Sie ein neues Problem melden. -Abschnitt oben.
2. Wählen Sie **Mixed Reality** Kategorie und die **Unterkategorie Apps** aus.
3. Geben Sie das Wort "SteamVR" in die Problemzusammenfassung ein. Dies hilft uns, Ihr Feedback zu finden.
4. Beschreiben Sie, welches Spiel oder welche Anwendung Von Ihnen verwendet wurde, als Sie auf das Problem bzw. die Anwendung bzw. die Anwendung bzw. die Sie bzw. die sie beim Beheben des Problems bzw. der Anwendung bzw. der Anwendung
5. Fügen Sie Ihrem Feedback einen Bericht des Systems "SteamVR" an. Dies bietet weitere Protokolle, mit denen wir Ihr Problem diagnostizieren können.
    1. Wählen Sie im Fenster "SteamVR" (die kleinen Fenster, in denen der Controllerstatus angezeigt wird) den Titel aus, um das Menü zu öffnen.
    2. Wählen Sie "Systembericht erstellen" aus.
    3. Speichern In Datei.
    4. Fügen Sie die generierte Datei direkt an ihren Feedback-Hub an.
6. Wenn Sie Feedback zur Leistung von SteamVR erhalten, sammeln Sie eine Mixed Reality Performance-Ablaufverfolgung: 
    1. Wählen Sie die **Schaltfläche Mein Problem neu** erstellen aus.
    2. Wählen Sie in der Dropdownliste neben "Include data about" (Daten zu enthalten) **Mixed Reality Performance (Leistung) aus.**
    3. Stellen Sie sicher, dass das Spiel ausgeführt wird, und wählen **Sie Erfassung starten aus.**
    4. Nehmen Sie sich einige Sekunden Zeit, um das Spiel zu spielen, um die Ablaufverfolgung zu erfassen. Erfassen Sie die Ablaufverfolgung nicht länger als 10 bis 15 Sekunden, oder sie ist zu groß, um sie zu übermitteln.
    5. Wählen Sie **Erfassung beenden aus.**
7. Wählen **Sie Senden** aus, nachdem Sie die restlichen Felder ausgefüllt haben.

Wenn Sie Fragen oder Kommentare zu teilen haben, können Sie uns auch über unser [Forum zu Erhalten.](http://steamcommunity.com/app/719950/discussions/)

## <a name="see-also"></a>Siehe auch

* [Problembehandlung für SteamVR mit Windows Mixed Reality](steamvr-questions.md)
* [Verwenden von Spielen und Apps in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Verwenden von HP-Controllern in Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [Verwenden von HP-Controllern in Unreal](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [Einreichen von Bugs und Feedback](filing-feedback.md)