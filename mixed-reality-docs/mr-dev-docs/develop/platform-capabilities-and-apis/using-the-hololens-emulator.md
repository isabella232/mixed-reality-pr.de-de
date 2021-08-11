---
title: Verwendung des HoloLens-Emulators
description: Erfahren Sie, wie Sie den HoloLens-Emulator zum Testen von Mixed Reality-Apps auf Ihrem PC ohne eine physische HoloLens verwenden.
author: hamalawi
ms.author: moelhama
ms.date: 05/11/2021
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, Emulator
ms.openlocfilehash: 3fcf69c7f4e4e2bc92ef3c31dccbd1224ad3051e8a922666deb801dd6f40c4ab
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188739"
---
# <a name="using-the-hololens-emulator"></a>Verwendung des HoloLens-Emulators

Mit dem HoloLens-Emulator, der das HoloLens-Entwicklungstoolset umfasst, können Sie holografische Apps auf Ihrem PC ohne eine physische HoloLens testen. Der Emulator verwendet einen virtuellen Hyper-V-Computer, was bedeutet, dass die Eingaben von Benutzern und der Umgebung, die normalerweise von den Sensoren der HoloLens erfasst werden, von Ihrer Tastatur, Maus oder dem Xbox-Controller simuliert werden. Sie brauchen Ihre Projekte nicht einmal für die Ausführung auf dem Emulator zu ändern, die App weiß nicht, dass sie nicht auf einer realen HoloLens ausgeführt wird.

Wenn Sie Anwendungen für immersive Windows Mixed Reality-Headsets (VR) oder Spiele für Desktop-PCs entwickeln möchten, testen Sie den [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md), mit dem Sie Desktop-Headsets simulieren können.

## <a name="hololens-2-emulator-overview"></a>HoloLens 2-Emulator – Übersicht

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/HoloLens-2-Emulator-Overview/player?format=ny]

## <a name="installing-the-hololens-emulator"></a>Installieren des HoloLens-Emulators
Lade den HoloLens-Emulator herunter.

Versionen:
* [HoloLens 2-Emulator (Windows Holographic, Version 21H1 mit Update aus Juli 2021)](https://go.microsoft.com/fwlink/?linkid=2167725).
* [HoloLens-Emulator (erste Generation) und holografische Projektvorlagen](https://go.microsoft.com/fwlink/?linkid=2065980).

Versionsanmerkungen und ältere Builds des HoloLens-Emulators finden Sie auf der Seite [HoloLens-Emulator – Archiv](hololens-emulator-archive.md).

### <a name="hololens-emulator-system-requirements"></a>HoloLens-Emulator – Systemanforderungen

Der HoloLens-Emulator verwendet Hyper-V mit RemoteFx (Emulator der ersten Generation) oder GPU-PV (HoloLens 2-Emulator) für Grafiken mit Hardwarebeschleunigung. Um den Emulator zu verwenden, stellen Sie sicher, dass Ihr PC die folgenden Hardwareanforderungen erfüllt:
* Windows 10 Pro, Enterprise oder Education – 64-Bit
    >[!NOTE]
    >Windows 10 Home-Edition unterstützt Hyper-V oder den HoloLens-Emulator nicht.  
    >Der HoloLens 2-Emulator benötigt das Windows 10 October 2018 Update oder höher.
* 64-Bit-CPU
* CPU mit vier Kernen (oder mehrere CPUs mit insgesamt vier Kernen)
* Mindestens 8 GB RAM
* Im BIOS müssen die folgenden Features [unterstützt und aktiviert sein](/archive/blogs/iftekhar/enable-hardware-settings-in-bios-to-run-hyper-v):
   * Hardwareunterstützte Virtualisierung
   * Adressübersetzung der zweiten Ebene (Second Level Address Translation, SLAT)
   * Hardwarebasierte Datenausführungsverhinderung (Data Execution Prevention, DEP)
* GPU-Anforderungen
   * DirectX 11.0 oder höher
   * Grafiktreiber für WDDM 1.2 oder höher (erste Generation)
   * Grafiktreiber für WDDM 2.5 (HoloLens 2-Emulator)
   * Der Emulator funktioniert möglicherweise mit einem nicht unterstützten Grafikprozessor, ist aber langsamer

Wenn Ihr System die oben aufgeführten Anforderungen erfüllt, **vergewissern Sie sich, dass das Feature „Hyper-V“ auf Ihrem System aktiviert ist**. Wechseln sie auf Ihrem Windows 10-Computer zu **Systemsteuerung > Programme > Programme und Features > Windows-Features aktivieren oder deaktivieren**, und überprüfen Sie, ob **Hyper-V** aktiviert ist.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Bereitstellen von Apps für den HoloLens-Emulator

1. Laden Sie Ihre Anwendungslösung in Visual Studio.
    >[!NOTE]
    >Wenn Sie Unity verwenden, erstellen Sie Ihr Projekt in Unity, und laden Sie dann die erstellte Lösung wie gewohnt in Visual Studio.
2. Stellen Sie für den HoloLens-Emulator (erste Generation) sicher, dass die Plattform auf **x86** eingestellt ist. Stellen Sie für den HoloLens 2-Emulator sicher, dass die Plattform auf **x86** oder **x64** eingestellt ist.
3. Wählen Sie die Version des **HoloLens-Emulators** für das gewünschte Zielgerät für das Debugging aus.
4. Wechseln Sie zu **Debuggen > Debuggen starten** oder drücken Sie **F5**, um den Emulator zu starten und Ihre Anwendung für das Debuggen bereitzustellen.

Der Emulator kann beim ersten Start eine Minute oder länger benötigen. Es wird empfohlen, den Emulator während der Debugsitzung geöffnet zu lassen, damit Sie Anwendungen schnell im Emulator bereitstellen können.

## <a name="basic-emulator-input"></a>Grundlegende Emulatoreingabe

Die Steuerung des Emulators ist mit vielen gängigen 3D-Videospielen vergleichbar. Es sind Eingabeoptionen über die Tastatur, Maus oder den Xbox-Controller verfügbar. Sie steuern den Emulator, indem Sie die Aktionen eines simulierten Benutzers durch Tragen einer HoloLens steuern. Ihre Aktionen bewegen den simulierten Benutzer in der Umgebung. Anwendungen, die im Emulator ausgeführt werden, reagieren wie auf einem echten Gerät.

Der Cursor der HoloLens (erste Generation) folgt der Kopfbewegung und -drehung. Im HoloLens 2-Emulator folgt der Cursor der Handbewegung und der Ausrichtung.

* **Nach vorne, hinten, links und rechts gehen**: Verwenden Sie die Tasten W, A, S und D auf Ihrer Tastatur oder den linken Stick eines Xbox-Controllers.
* **Nach oben, unten, links und rechts sehen**: Auswählen und mit der Maus ziehen; verwenden Sie die Pfeiltasten auf Ihrer Tastatur oder den rechten Stick eines Xbox-Controllers.
* **Tippbewegung in die Luft**: Klicken Sie mit der rechten Maustaste, drücken Sie die Eingabetaste auf Ihrer Tastatur, oder verwenden Sie die Taste A eines Xbox-Controllers.
* **Öffnen/Systemgeste**: Drücken Sie die Windows-Taste oder die F2-Taste auf Ihrer Tastatur, oder drücken Sie die B-Taste eines Xbox-Controllers.
* **Handbewegung zum Scrollen**: Halten Sie die ALT-Taste und die rechte Maustaste gleichzeitig gedrückt, und ziehen Sie die Maus nach oben oder unten. Halten Sie auf einem Xbox-Controller den rechten Auslöser und die A-Taste gedrückt, und bewegen Sie den rechten Stift nach oben und unten.
* **Handbewegung und Ausrichtung** (nur HoloLens 2-Emulator): Halten Sie die ALT-Taste gedrückt, und ziehen Sie die Maus nach oben oder unten, links oder rechts, um die Hand zu bewegen. Alternativ können Sie die Pfeiltasten und Q oder E verwenden, um die Hand zu drehen und anzuwinkeln. Bei einem Xbox-Controller halten Sie den linken oder rechten Bumper gedrückt, und verwenden Sie den linken Stick, um die Hand nach links, rechts, vorne und hinten zu bewegen, den rechten Stick, um die Hand zu drehen. Bewegen Sie das Dpad nach oben oder unten, um die Hand zu heben oder zu senken.

Besitzen Sie ein immersives Headset für Windows Mixed Reality?  Vom HoloLens 2-Emulator (Windows Holographic, Version 2004) an können Sie Ihr immersives Headset für Windows Mixed Reality und die Motion-Controller für die Steuerung und die stereoskopische Darstellung des HoloLens 2-Emulators verwenden.  Weitere Informationen finden Sie unter [Verwenden eines immersiven Headsets für Windows Mixed Reality und des Motion-Controllers mit dem Hololens 2-Emulator](#using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator)

## <a name="anatomy-of-the-hololens-2-emulator"></a>Aufbau des HoloLens 2-Emulators

### <a name="main-window"></a>Hauptfenster

![Hauptfenster des HoloLens 2-Emulators](images/emulator2-900px.png)

### <a name="toolbar"></a>Symbolleiste

Rechts neben dem Hauptfenster befindet sich die Symbolleiste des Emulators. Die Symbolleiste enthält die folgenden Schaltflächen:
* ![Schließen-Symbol](images/emulator-close.png) **Schließen**: Schließt den Emulator.
* ![Minimieren-Symbol](images/emulator-minimize.png) **Minimieren**: Minimiert das Emulatorfenster.
* ![Simulation-Symbol](images/emulator-simulation-panel.png) **Systemsteuerung der Simulation**: Blenden Sie die [Systemsteuerung der Simulation](#simulation-control-panel) zum Konfigurieren und Steuern der [Eingabe für den Emulator](#basic-emulator-input) ein oder aus.
* ![Bildschirmgröße anpassen-Symbol](images/emulator-fit.png) **Bildschirmgröße anpassen**: Passt den Emulator an den Bildschirm an.
* ![Zoom-Symbol](images/emulator-zoom.png) **Zoom**: Vergrößern und verkleinern Sie den Emulator.
* ![Hilfe anfordern-Symbol](images/emulator-help.png) **Hilfe**: Öffnen Sie die Hilfe zum Emulator.
* ![Geräteportal öffnen-Symbol](images/emulator-deviceportal.png) **Geräteportal öffnen**: Öffnen Sie das Windows-Geräteportal für das HoloLens-Betriebssystem im Emulator.
* ![Tools-Symbol](images/emulator-tools.png) **Tools**: Öffnen Sie den Bereich für **zusätzliche Tools**.

### <a name="simulation-control-panel"></a>Systemsteuerung der Simulation

Mithilfe der Systemsteuerung der Simulation können Sie die aktuelle Position und Ausrichtung des simulierten Benutzers und der simulierten Eingabegeräte anzeigen. Sie ermöglicht es Ihnen auch, sowohl simulierte Eingaben, wie das Ein- und Ausblenden einer oder beider Hände, als auch Geräte zur Steuerung simulierter Eingaben, wie Tastatur, Maus und Gamepad Ihres PCs, zu konfigurieren.

![Systemsteuerung der Simulation](images/emulator-simulation-control-panel.png)

* Um die Systemsteuerung der Simulation ein- oder auszublenden, wählen Sie die Symbolleistenschaltfläche aus, oder drücken Sie F7 auf der Tastatur.
* Bewegen Sie den Mauszeiger über ein Steuerelement oder Feld, um eine QuickInfo anzuzeigen, die zugehörige Tastatur-, Maus- und Gamepad-Steuerelemente enthält.
* Um eine Hand ein- oder auszublenden, schalten Sie den entsprechenden Schalter unter der linken oder rechten Hand um.
* Verwenden Sie zum Steuern der Hand entweder die linke oder rechte ALT-Taste auf Ihrer Tastatur oder den linken oder rechten Bumper des Gamepads.
* Wenn Sie alle Eingaben an eine oder beide Hände leiten möchten, wählen Sie die Markierungstaste unter dem Umschalter aus. Dies bewirkt das gleiche wie das Halten der ALT-Taste für die Hand.
* Wählen Sie zum Steuern der Richtung des Anvisierens mit den Augen den Pushpin im Bereich „Eyes“ (Augen); dies bewirkt das gleiche wie das Halten der Y-Taste auf der Tastatur.
* Wählen Sie zum Laden einer Raumaufzeichnung die Schaltfläche „Load“ (Laden) im Abschnitt „Recording“ (Aufzeichnung) aus. Weitere Informationen finden Sie unter [simulierte Räume](#simulated-rooms).
* Um die Geschwindigkeit anzupassen, mit der sich der simulierte Benutzer oder die simulierten Eingabegeräte als Reaktion auf die Eingabe von Tastatur, Maus oder Gamepad bewegen oder drehen, wählen Sie das Zahnradsymbol neben „Input settings“ (Eingabeeinstellungen) aus, und passen Sie die Schieberegler an.
* Standardmäßig steuert die Tastatureingabe den simulierten Benutzer und die simulierte Eingabe. Damit die Tastatureingabe Ihres PCs an die HoloLens weitergeleitet wird, deaktivieren Sie das Kontrollkästchen „Use Keyboard for Simulation“ (Tastatur für Simulation verwenden). F4 ist die Tastenkombination für diese Einstellung.
* Wenn der Simulationsbereich bereits angezeigt wird, drücken Sie F8, um den Tastaturfokus dorthin zu verschieben.
* Wählen Sie die Schaltfläche am unteren Rand des Bereichs aus, oder drücken Sie F9 auf Ihrer Tastatur, um den Simulationsbereich beim Emulatorfenster auszudocken.  Wenn Sie das Fenster schließen oder erneut F9 drücken, kehrt das Fenster zum Emulator zurück.
* Die Systemsteuerung der Simulation kann als separate Anwendung gestartet werden, sodass Sie sich mit dem HoloLens 2-Emulator, einem HoloLens 2-Gerät oder der Windows Mixed Reality-Simulation verbinden und dieses steuern können, indem Sie „PerceptionSimulationInput.exe“ unter „%ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\“ ausführen.

### <a name="account-tab"></a>Registerkarte „Account“ (Konto)

Auf der Registerkarte „Account“ (Konto) können Sie den Emulator für die Anmeldung mit einem Microsoft-Konto konfigurieren. Dies ist beim Testen von APIs hilfreich, bei denen der Benutzer mit einem Konto angemeldet sein muss. Das Umschalten dieser Option erfordert, dass Sie den HoloLens-Emulator vollständig schließen und neu starten, damit die Einstellung wirksam wird. Wenn diese Option aktiviert ist, werden Sie bei späteren Starts des Emulators zur Anmeldung aufgefordert, genau wie ein Benutzer beim ersten Start der HoloLens. Um Ihre Anmeldeinformationen über die Tastatur Ihres PCs einzugeben, deaktivieren Sie zunächst „Use Keyboard for Simulation“ (Tastatur für Simulation verwenden) in der Systemsteuerung für die Simulation, oder drücken Sie F4 auf Ihrer Tastatur, um die Tastatureinstellung zu aktivieren oder zu deaktivieren.

### <a name="optional-settings-tab"></a>Registerkarte „Optional Settings“ (Optionale Einstellungen)

Auf der Registerkarte „Optional Settings“ (Optionale Einstellungen) wird ein Steuerelement angezeigt, mit dem hardwarebeschleunigte Grafiken aktiviert oder deaktiviert werden können. Hardwarebeschleunigte Grafiken werden standardmäßig verwendet, wenn sie vom Treiber für die Grafikkarte Ihres PCs unterstützt werden. Wenn der Treiber Ihrer Grafikkarte „GPU-PV“ nicht unterstützt, wird diese Option nicht angezeigt.

### <a name="diagnostics-tab"></a>Registerkarte „Diagnostics“ (Diagnose)

Auf der Registerkarte „Diagnostics“ (Diagnose) wird die IP-Adresse des Emulators in Form eines Links zum Windows-Geräteportal sowie der Status der virtuellen GPU angezeigt.

### <a name="network-tab"></a>Registerkarte „Network“ (Netzwerk)

Auf der Registerkarte „Network“ (Netzwerk) werden die Netzwerkadapterdetails für den Emulator sowie die Netzwerkadapterdetails für den Hostcomputer angezeigt. Diese Registerkarte wird für den HoloLens 2-Emulator nur angezeigt, wenn Sie den Emulator unter Windows 10 May 2019 Update oder neuer ausführen.

### <a name="nat-configuration-tab"></a>Registerkarte „NAT Configuration“ (NAT-Konfiguration)

Diese Registerkarte wird nur angezeigt, wenn Sie den Emulator unter Windows 10 May 2019 Update oder neuer ausführen.

Der Emulator verwendet die Netzwerkverbindung Ihres PCs und befindet sich hinter einem NAT.  Diese Registerkarte ermöglicht es Ihnen, Ports von Ihrem Hostcomputer dem Emulator zuzuordnen, wodurch Remotegeräte eine Verbindung zu Anwendungen und Diensten herstellen können, die im Emulator ausgeführt werden.

Wenn Sie z. B. von einem Remotecomputer aus auf das Geräteportal auf dem Emulator zugreifen möchten:

1. Fügen Sie einen Eintrag für den internen Port 80 (der Port, an dem das Geräteportal lauscht) hinzu, indem Sie in der Tabelle auf eine freie Zeile doppelklicken.  Geben Sie für andere Anwendungen die Portnummer ein, an der diese Anwendung lauscht.
2. Wählen Sie einen beliebigen externen Port aus.  In diesem Beispiel verwenden wir Port 8080 als externen Port.
3. Wählen Sie das Protokoll aus.  Die Standardeinstellung ist „TCP“.  Da das Geräteportal TCP verwendet, übernehmen wir die Standardeinstellung.
4. Klicken Sie auf „Änderungen übernehmen“, um die Zuordnung zu aktivieren.  Der „Status“ wechselt von „Ausstehend“ zu „Aktiv“.
5. Öffnen Sie auf dem Remotecomputer einen Browser, und navigieren Sie zu (IP-des-PCs-der-den-Emulator-ausführt):8080.  Die Geräteportalschnittstelle wird angezeigt.  Die IP-Adresse, die Sie auf einem Remotecomputer verwenden, muss die IP-Adresse des Computers sein, auf dem der Emulator ausgeführt wird, und nicht die IP-Adresse des Emulators selbst.  Sie können die IP-Adresse auf verschiedene Weise abrufen, z. B. über die App „Einstellungen“ auf dem PC in der Kategorie „Netzwerk und Internet“, über „ipconfig“ über eine Eingabeaufforderung und über die Registerkarte „Netzwerk“ im Dialogfeld für Emulatortools, indem Sie nach dem Eintrag für den Desktopadapter suchen.

Beachten Sie außerdem, dass Sie den Emulator, wenn Sie eine Portzuordnung für das Geräteportal hinzufügen, mit dem in der Emulatorinstallation enthaltenen Perception Simulation Control-Tool oder mit den Perception Simulation-APIs remote steuern können, indem Sie sich mit der IP-Adresse des Hostcomputers und dem externen Port des Geräteportals verbinden, wie z. B. 8080 im obigen Beispiel.  Wenn Sie die Perception Simulation Control verwenden, um eine Verbindung zum Emulator herzustellen und ihn remote zu steuern, geben Sie nur die IP-Adresse des PCs und den konfigurierten Port an.  Fügen Sie nicht „https://“ ein.

Standardmäßig sind keine Portzuordnungen eingerichtet.  Alle von Ihnen konfigurierten Zuordnungen sind beim Start des HoloLens 2-Emulators persistent und werden automatisch aktiviert, wenn der Emulator vollständig gestartet wurde.

Verwenden Sie die Schaltfläche „Exportieren“, um Ihre Zuordnungen in einer Datei zu speichern.  Sie können diese Datei dann mit anderen Teammitgliedern teilen, die über die Schaltfläche „Importieren“ automatisch dieselben Zuordnungen konfigurieren können.

![Registerkarte „NAT Configuration“ (NAT-Konfiguration) des HoloLens-Emulators](images/emulator-natconfig-500px.png)

### <a name="updates-tab"></a>Registerkarte „Updates“

Diese Registerkarte wird nur angezeigt, wenn Sie den Emulator unter Windows 10 May 2019 Update oder neuer ausführen.

Beim Start prüft der Emulator auf neue Versionen.  Wenn eine neue Version verfügbar ist, zeigt der Emulator eine Eingabeaufforderung an, die die von Ihnen verwendete Version zusammen mit der verfügbaren Version anzeigt und fragt, ob Sie ein Update durchführen möchten.  Wenn Sie „Ja“ auswählen, wird das Installationsprogramm für die neue Version heruntergeladen.

Auf der Registerkarte „Updates“ können Sie steuern, ob der Emulator nach neuen Versionen sucht, indem Sie das Kontrollkästchen „Automatically check for updates“ (Automatisch nach Updates suchen) auf dieser Registerkarte aktivieren.  Es ermöglicht Ihnen auch, andere verfügbare Emulator-Versionen anzuzeigen und herunterzuladen, beginnend mit dem Update vom September 2019.  Für andere als die aktuell aktive Version steht ein Link für den Download zur Verfügung.  Wenn Sie auf diesen Link klicken, wird das Installationsprogramm für diese Version heruntergeladen.

![Registerkarte „Updates“ des HoloLens-Emulators](images/emulator-updates-500px.png)

### <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Verwenden eines immersiven Headsets für Windows Mixed Reality und des Motion-Controllers mit dem Hololens 2-Emulator

Vom HoloLens 2-Emulator (Windows Holographic, Version 2004) an können Sie ein immersives Headset für Windows Mixed Reality und die Motion-Controller für die stereoskopische Darstellung im HoloLens 2-Emulator und die Interaktion mit ihm verwenden.  Dadurch können Sie ohne ein HoloLens 2-Gerät schnellere, natürlichere Bewegungen mit Kopf und Händen machen.  Dies stellt keinen vollständigen Ersatz für ein HoloLens 2-Gerät dar, vielmehr besteht der Zweck in der Vermittlung einer besseren Erfahrung jenseits der Interaktion mit dem Emulator über Tastatur, Maus und Gamepad in einem 2D-Desktopfenster.  So aktivieren Sie diese Funktion:

1. Sorgen Sie dafür, dass Windows Mixed Reality auf Ihrem PC konfiguriert und Ihr immersives Headset für Windows Mixed Reality angeschlossen ist.
2. Starten Sie den HoloLens 2-Emulator
3. Öffnen Sie den Simulationsbereich, indem Sie auf die Schaltfläche auf der Symbolleiste klicken oder F7 drücken.
4. Scrollen Sie im Bereich nach unten.
5. Aktivieren Sie das Feld mit der Beschriftung „Use HMD for simulation“ (HMD für die Simulation verwenden)
6. Windows Mixed Reality wird gestartet, und die Emulator-Anzeige ändert sich geringfügig.  Ohne Headset platziert der Emulator beide Augen in der Kopfmitte und zeigt nur ein Auge an.  Mit einem Headset generiert der Emulator eine echte stereoskopische Ausgabe, gibt aber nur das Bild für ein Auge im Desktopfenster wieder, während für das Headset beide Augen gerendert werden.
7. Aktivieren Sie optional einen oder beide Motion-Controller.  Die Controllereingabe wird im Emulator der Handeingabe zugeordnet.  Ziehen Sie beispielsweise zum Tippen den Auslöser am Motion-Controller.  Verwenden Sie für Bewegungen den Ministick.  Eine vollständige Liste der Steuerelemente finden Sie unter [Erweiterte Eingabe für HoloLens-Emulator und Mixed Reality-Simulator](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)

Haben Sie Probleme, die Inhalte in Ihrem Headset zu sehen?

- Wenn die Anzeige sowohl im Headset als auch im Mixed Reality Portal leer ist, Sie aber Inhalte im Fenster des HoloLens 2-Emulators auf dem Desktop sehen können, überprüfen Sie, ob die Hardware-Grafikbeschleunigung im Emulator aktiviert ist.  Für die Unterstützung von immersiven Headsets für Windows Mixed Reality ist es erforderlich, dass die Hardware-Grafikbeschleunigung im Emulator aktiviert ist.
- Wenn Sie Inhalte im Headset sehen, die Hologramme aber verschwommen sind oder Sie ein Doppelbild sehen, verwenden Sie die folgenden Schritte, um die Stereoansicht für Ihre Augen anzupassen:

1. Deaktivieren Sie vorübergehend „Use HMD for simulation“ (HMD für die Simulation verwenden).
2. Starten Sie den Registrierungs-Editor (regedit.exe)
3. Navigieren Sie zu „HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation“
4. Erstellen Sie einen neuen DWORD-Wert mit dem Namen „EnableEyePoseControl“, und legen Sie seinen Wert auf 1 fest.
5. Aktivieren Sie „Use HMD for simulation“ (HMD für die Simulation verwenden) im Emulator.
6. Wenn Inhalte im Headset angezeigt werden, verwenden Sie die Pfeiltasten, um die Augendrehung anzupassen.  Halten Sie die linke ALT-Taste zum Anpassen des linken und die rechte ALT-Taste zum Anpassen des rechten Auges gedrückt.  Verwenden Sie ‚Q‘ und ‚E‘ zum Anpassen der Drehung für jedes Auge, wobei Sie jeweils die ALT-Taste für das entsprechende Auge gedrückt halten.  Verwenden Sie die Tasten „+“ und „-“, um den Abstand zwischen den Augen zu ändern.  (Beachten Sie, dass +/- auf der Zehnertastatur nicht funktioniert.  Verwenden Sie die Schaltflächen auf der Haupttastatur.)
7. Wenn die Stereodarstellung richtig angezeigt wird, drücken Sie ‚S‘, um die Änderungen zu speichern.  Die neue Konfiguration wird für zukünftige Starts des Emulators gespeichert.
8. Wenn Sie die Änderungen verwerfen und die vorherige Konfiguration wiederherstellen möchten, drücken Sie „L“, um die Standardkonfiguration oder die vorherige Konfiguration zu laden.
9. Ändern Sie den Wert von „EnableEyePoseControl“ in der Registrierung in „0“, und führen Sie die Option „Use HMD for simulation“ (HMD für die Simulation verwenden) aus.

Wenn Sie eine Konfiguration gespeichert haben und sie entfernen möchten, können Sie den Wert „DisplayConfiguration“ unter „HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation“ löschen.  Wenn Sie derzeit das Headset mit dem Emulator verwenden, müssen Sie die Option „Use HMD for simulation“ (HMD für die Simulation verwenden) deaktivieren und wieder einschalten, damit diese Änderung wirksam wird.

## <a name="anatomy-of-the-hololens-first-gen-emulator"></a>Aufbau des HoloLens-Emulators (erste Generation)

### <a name="main-window"></a>Hauptfenster

Beim Starten des Emulators wird ein Fenster mit dem HoloLens-Betriebssystem angezeigt.

![Hauptfenster des HoloLens-Emulators](images/emulator-890px.png)

### <a name="toolbar"></a>Symbolleiste

Rechts neben dem Hauptfenster befindet sich die Symbolleiste des Emulators. Die Symbolleiste enthält die folgenden Schaltflächen:
* ![Schließen-Symbol](images/emulator-close.png) **Schließen**: Schließt den Emulator.
* ![Minimieren-Symbol](images/emulator-minimize.png) **Minimieren**: Minimiert das Emulatorfenster.
* ![Benutzereingabe-Symbol](images/emulator-control.png) **Benutzereingabe**: Maus und Tastatur werden verwendet, um die [Benutzereingaben für den Emulator](#basic-emulator-input) zu simulieren.
* ![Tastatur- und Mauseingabe-Symbol](images/emulator-input.png) **Tastatur- und Mauseingabe**: Tastatur- und Mauseingaben werden als Tastatur- und Mausereignisse direkt an das HoloLens-Betriebssystem übergeben, als ob Sie eine Bluetooth-Tastatur und -Maus angeschlossen hätten.
* ![Bildschirmgröße anpassen-Symbol](images/emulator-fit.png) **Bildschirmgröße anpassen**: Passt den Emulator an den Bildschirm an.
* ![Zoom-Symbol](images/emulator-zoom.png) **Zoom**: Vergrößert und verkleinert den Emulator.
* ![Hilfe anfordern-Symbol](images/emulator-help.png) **Hilfe**: Öffnet die Hilfe zum Emulator.
* ![Geräteportal öffnen-Symbol](images/emulator-deviceportal.png) **Geräteportal öffnen**: Öffnen Sie das Windows-Geräteportal für das HoloLens-Betriebssystem im Emulator.
* ![Tools-Symbol](images/emulator-tools.png) **Tools**: Öffnen Sie den Bereich für **zusätzliche Tools**.

### <a name="simulation-tab"></a>Registerkarte „Simulation“

Die Standardregisterkarte im Bereich **Additional Tools** (Zusätzliche Tools) ist die Registerkarte **Simulation**.

![Bereich „Additional Tools“ (Zusätzliche Tools) des HoloLens-Emulators](images/emulator-simulation-500px.png)

Die Registerkarte „Simulation“ zeigt den aktuellen Zustand der simulierten Sensoren an, mit denen das HoloLens-Betriebssystem im Emulator gesteuert wird. Wenn Sie den Mauszeiger über einen beliebigen Wert auf der Registerkarte „Simulation“ bewegen, wird eine QuickInfo angezeigt, die beschreibt, wie Sie diesen Wert steuern können.

### <a name="room-tab"></a>Registerkarte „Room“ (Raum)

Der Emulator simuliert die Eingaben für die Umgebung in Form des Gittermodells für die räumliche Abbildung aus simulierten Räumen. Auf dieser Registerkarte können Sie anstelle des Standardraums den zu ladenden Raum auswählen.

![Registerkarte „Rooms“ (Räume) des HoloLens-Emulators](images/emulator-room-500px.png)

Weitere Informationen finden Sie unter [simulierte Räume](#simulated-rooms).

### <a name="account-tab"></a>Registerkarte „Account“ (Konto)

Auf der Registerkarte „Account“ (Konto) können Sie den Emulator für die Anmeldung mit einem Microsoft-Konto konfigurieren. Dies ist beim Testen von APIs hilfreich, bei denen der Benutzer mit einem Konto angemeldet sein muss. Nachdem Sie das Kontrollkästchen auf dieser Seite aktiviert haben, werden Sie bei späteren Starts des Emulators zur Anmeldung aufgefordert, genau wie ein Benutzer beim ersten Start der HoloLens.

## <a name="simulated-rooms"></a>Simulierte Räume

Simulierte Räume sind hilfreich, um Ihre Anwendung in mehreren Umgebungen zu testen. Zusammen mit dem Emulator werden mehrere Räume ausgeliefert. Sobald Sie die Emulation installiert haben, finden Sie diese unter „%ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(version)\Plugins\Rooms“. Alle diese Räume wurden in realen Umgebungen mit einer HoloLens erfasst:

* **DefaultRoom.xef**: Ein kleines Wohnzimmer mit Fernseher, Couchtisch und zwei Sofas. Beim Starten des Emulators wird dieser Raum standardmäßig geladen.
* **Bedroom1.xef**: Ein kleines Schlafzimmer mit einem Schreibtisch.
* **Bedroom2.xef**: Ein Schlafzimmer mit einem Doppelbett, einer Kommode, Nachttischen und einem begehbaren Kleiderschrank.
* **GreatRoom.xef**: Ein großer offener Raum mit großem Wohnzimmer, Esstisch und Küche.
* **LivingRoom.xef**: Ein Wohnzimmer mit Kamin, Sofa, Sesseln und einem Couchtisch mit Vase.

Sie können auch eigene Räume aufzeichnen, die Sie im Emulator verwenden können, indem Sie die Seite „Simulation“ des [Windows-Geräteportals](using-the-windows-device-portal.md) für Ihre HoloLens (erste Generation) verwenden.

Im Emulator sehen Sie nur die von Ihnen gerenderten Hologramme. Den simulierten Raum hinter den Hologrammen können Sie jedoch nicht sehen. Dies steht im Gegensatz zur tatsächlichen HoloLens, bei der beides kombiniert zu sehen ist. Wenn Sie den simulierten Raum im HoloLens-Emulator anzeigen möchten, müssen Sie Ihre Anwendung aktualisieren, um das Gittermodell für die räumliche Abbildung in der Szene darzustellen.

## <a name="known-issues"></a>Bekannte Probleme

* Wenn Sie den HoloLens 2-Emulator deinstallieren, bleibt das Datenträgerimage (Flash.vhdx) möglicherweise auf der Festplatte im Ordner „Windows Kits\10\emulation\HoloLens\<build number>“ zurück.  Diese Datei kann gefahrlos gelöscht werden.
* Die Hardware-Grafikbeschleunigung kann auf einigen Systemen mit AMD- oder Intel-Grafik zu Abstürzen von Holographic-Apps führen.  Durch das Deaktivieren der Hardware-Grafikbeschleunigung im Fenster „Extras“ des Emulators wird dieses Problem umgangen.
* Nach der Installation der neuesten Windows-Updates ab Juli 2020 ist die Hardwaregrafikbeschleunigung im HoloLens-Emulator (erste Generation) möglicherweise nicht mehr verfügbar.
Die für die Hardwaregrafikbeschleunigung erforderliche RemoteFX-Komponente wurde als veraltet markiert und wird in einer zukünftigen Windows-Version entfernt.  Um die Hardwaregrafikbeschleunigung erneut zu aktivieren, verwenden Sie das PowerShell-Cmdlet [Enable-VMRemoteFXPhysicalVideoAdapter](/powershell/module/hyper-v/enable-vmremotefxphysicalvideoadapter).  Weitere Informationen finden Sie in der [Dokumentation zur Außerbetriebsetzung und zum Entfernen der RemoteFX-Unterstützung in Windows](https://support.microsoft.com/help/4570006/update-to-disable-and-remove-the-remotefx-vgpu-component).

## <a name="troubleshooting"></a>Problembehandlung

Möglicherweise wird bei der Installation des Emulators eine Fehlermeldung angezeigt, dass Sie *Visual Studio 2015 Update 1 und die UWP-Tools Version 1.2* benötigen. Es gibt drei mögliche Ursachen für diesen Fehler:
* Sie verfügen nicht über eine ausreichend aktuelle Version von Visual Studio (Visual Studio 2019, Visual Studio 2017 oder Visual Studio 2015 Update 1 oder höher). Installieren Sie zur Behebung dieses Problems die neueste Version von Visual Studio.
* Sie verfügen über eine neuere Version von Visual Studio, aber Sie haben nicht die UWP-Tools (universelle Windows-Plattform) installiert. Dies ist ein optionales Feature für Visual Studio. Für HoloLens (erste Generation) benötigen Sie die UWP-Tools für Visual Studio 2015 oder Visual Studio 2017.

Möglicherweise wird auch ein Fehler bei der Installation des Emulators auf einer Nicht-Pro/-Enterprise/-Education-SKU von Windows angezeigt, oder wenn Sie das Hyper-V-Feature nicht aktiviert haben.
* Eine vollständige Liste der Anforderungen finden Sie oben im Abschnitt [Systemanforderungen](#hololens-emulator-system-requirements).
* Stellen Sie außerdem sicher, dass das Hyper-V-Feature auf Ihrem System aktiviert ist.

Wenn Ihre Installation erfolgreich abgeschlossen wurde, der HoloLens-Emulator jedoch nicht als Option für die Bereitstellung und das Debuggen zur Verfügung steht:
* Ihre Visual Studio-Projektkonfiguration ist auf x86 (HoloLens erste Generation), x86 oder x64 (HoloLens 2-Emulator) eingestellt.
* Wenn Sie Visual Studio 2019 verwenden, ist das Plattformtoolset in Ihrer Projektkonfiguration auf „v142“ festgelegt.

Wenn Ihre Installation erfolgreich abgeschlossen wurde, Visual Studio jedoch beim Starten des HoloLens-Emulators einen Fehler anzeigt:
* Ausführen von Visual Studio als Administrator
* Wenn Sie nur Visual Studio 2019 installiert haben, vergewissern Sie sich, dass der Registrierungswert „KitsRoot10“ unter „HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots“ auf Ihren 32-Bit-Ordner für „Program Files“ zeigt (beispielsweise „C:\Program Files (x86)\Windows Kits\10“).  Wenn dies nicht der Fall ist, deinstallieren Sie den HoloLens-Emulator, ändern Sie den Registrierungswert in Ihren 32-Bit-Ordner für „Program Files“, und installieren Sie dann den HoloLens-Emulator erneut.  Dieses Problem wird in Visual Studio 2019 16.0.3 behandelt.

Wenn der Emulator beim Start ein Fehlerdialogfeld „Ungültige Bytecodierung“ anzeigt:
* Löschen Sie alle Dateien in „%localappdata%\Microsoft\XDE\HCS“ und versuchen Sie es erneut.

Wenn Ihre Liste der Debugziele in Visual Studio leer ist (z. B. ist „Start“ die einzige Option) und Sie alle oben genannten Schritte zur Problembehandlung ausgeführt haben:
* Löschen Sie den Ordner „ConfigurationCache“ in „%localappdata%\Microsoft\VisualStudio\\<*Installations-ID*>\CoreCon“ und versuchen Sie es erneut.

Wenn Ihr System beim Starten des Emulators hängen bleibt, deaktivieren Sie die Hardwarebeschleunigung für Emulatorgrafiken.
* Erstellen Sie in der Registrierung einen DWORD-Wert namens „DisableGPU“ unter „HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0“, und legen Sie seinen Wert auf 1 fest.

## <a name="see-also"></a>Siehe auch
* [Erweiterte Eingabe für HoloLens-Emulator und Mixed Reality-Simulator](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens-Emulator – Softwareverlauf](hololens-emulator-archive.md)
* [Räumliche Abbildung in Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Räumliche Abbildung in DirectX](../../develop/native/spatial-mapping-in-directx.md)