---
title: Verwenden des Windows-Geräteportals
description: Erfahren Sie, wie Sie Ihr Gerät remote über WLAN oder USB mithilfe des Windows-Geräteportals konfigurieren und verwalten.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Windows-Geräteportal, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: c354a6f7c3afd6164182f915c39bbf1ce306ef39
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583239"
---
# <a name="using-the-windows-device-portal"></a>Verwenden des Windows-Geräteportals

<table>
<tr>
<th>Feature</th><th style="width:150px"><a href="/hololens/hololens1-hardware">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px">
</tr><tr>
<td> Windows-Geräteportal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Mit dem Windows-Geräteportal für HoloLens können Sie Ihr Gerät remote über eine WLAN- oder USB-Verbindung konfigurieren und verwalten. Das Geräteportal ist ein Webserver auf der HoloLens, mit dem Sie über einen Webbrowser auf dem PC eine Verbindung herstellen können. Das Geräteportal enthält viele Tools, die Ihnen helfen, ihre HoloLens zu verwalten und ihre Apps zu debuggen und zu optimieren.

Diese Dokumentation befasst sich speziell mit dem Windows-Geräteportal für HoloLens. Informationen zum Verwenden des Windows-Geräteportals für Desktop (einschließlich Windows Mixed Reality) finden Sie unter [Windows-Geräteportal (Übersicht)](/windows/uwp/debug-test-perf/device-portal).

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Einrichten von HoloLens zur Verwendung des Windows-Geräteportals

1. Schalten Sie die HoloLens ein, und setzen Sie sie auf.
2. Verwenden Sie die [Startgeste](/hololens/hololens2-basic-usage#start-gesture) für HoloLens2 oder die [Öffnengeste](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) auf HoloLens (1. Gen), um das Hauptmenü zu starten. 
3. Visieren Sie die Kachel **Einstellungen** an, und führen Sie ein [In die Luft-Tippen](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) auf HoloLens (1. Gen) aus. Sie können sie auf HoloLens 2 ebenfalls auswählen, indem Sie [sie berühren oder einen Handstrahl verwenden](/hololens/hololens2-basic-usage). 
4. Wählen Sie das Menüelement **Aktualisieren** aus.
5. Wählen Sie das Menüelement **Für Entwickler** aus.
6. Aktivieren Sie den **Entwicklermodus**.

> [!IMPORTANT]
> Wenn Sie sich im Mehrbenutzermodus befinden und kein Administrator sind, wird die Option zum Wechsel in den Entwicklermodus möglicherweise grau angezeigt. Vergewissern Sie sich, dass Sie **[Administrator für das Gerät](/hololens/security-adminless-os)** sind.

7. [Scrollen Sie nach unten](../../design/gaze-and-commit.md#composite-gestures), und aktivieren Sie **Geräteportal**.
8. Wenn Sie das Windows-Geräteportal einrichten, damit Sie Apps auf dieser HoloLens per USB oder WLAN bereitstellen können, wählen Sie **Koppeln** aus, um [eine Kopplungs-PIN zu erstellen](using-visual-studio.md). Verlassen Sie die Einstellungen-App, wenn das PIN-Popupfenster angezeigt wird, bis Sie die PIN während Ihrer ersten Bereitstellung in Visual Studio eingeben.

![Aktivieren des Entwicklermodus in der App „Einstellungen“ für Windows Holographic](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a>Herstellen einer WLAN-Verbindung

1. [Verbinden Sie die HoloLens mit dem WLAN](/hololens/hololens-network).
2. Suchen Sie die IP-Adresse Ihres Geräts mit einem dieser Verfahren:
   * Wechseln Sie zu **Einstellungen > Netzwerk und Internet > WLAN > Erweiterte Optionen**.
   * Wechseln Sie zu **Einstellungen > Netzwerk und Internet**, und wählen Sie **Hardware-Eigenschaften** aus.

![Einstellungen für HoloLens 2](images/using-windows-portal-img-02.jpg)

3. Navigieren Sie in einem Webbrowser auf Ihrem PC zu https://<IHRE_HOLOLENS_IP_ADRESSE>
   * Im Browser wird die folgende Meldung angezeigt: „Es besteht ein Problem mit dem Sicherheitszertifikat dieser Website“, da es sich bei dem an das Geräteportal ausgegebenen Zertifikat um ein Testzertifikat handelt. Sie können diesen Zertifikatfehler vorerst ignorieren und fortfahren.

## <a name="connecting-over-usb"></a>Herstellen einer USB-Verbindung

1. [Installieren Sie die Tools](../install-the-tools.md), um sicherzustellen, dass auf dem PC Visual Studio mit den Windows 10-Entwicklertools installiert ist, um USB-Verbindungen zu aktivieren.

> [!IMPORTANT]
> Wenn bei der USB-Konnektivität Probleme auftreten, überprüfen Sie, ob die optionale Komponente für die USB-Gerätekonnektivität als Teil ihres **[Visual Studio-Toolpaket](../install-the-tools.md#installation-checklist)** installiert ist.

2. Verbinden Sie Ihre HoloLens mit einem Micro-USB-Kabel für HoloLens (1. Gen) oder USB-C für HoloLens 2.
3. Navigieren Sie in einem Webbrowser auf Ihrem PC zu [https://127.0.0.1:10080](https://127.0.0.1:10080).

### <a name="moving-files-over-usb"></a>Verschieben von Dateien über USB

Sie können Dateien ohne zusätzliches Setup von Ihrem PC auf Ihre HoloLens verschieben.
1. Verbinden Sie Ihren PC mit einem USB-Kabel mit Ihrer HoloLens
2. Ziehen Sie Ihre Dateien auf Ihrem Desktop auf **PC\\[Name_Ihres_HoloLens_Geräts]\Internal Storage**
3. Öffnen Sie das **Startmenü**, und wählen Sie auf Ihrer HoloLens **Alle Apps > Datei-Explorer** aus.

> [!NOTE]
> Möglicherweise müssen Sie in der linken Seite des Bereichs **Dieses Gerät** auswählen, um von „Zuletzt verwendet“ fort zu navigieren und Ihre Dateien anzuzeigen. 

## <a name="connecting-to-an-emulator"></a>Herstellen einer Verbindung mit einem Emulator

Sie können das Geräteportal auch mit dem Emulator verwenden. Verwenden Sie die [Symbolleiste](using-the-hololens-emulator.md), um die Verbindung mit dem Geräteportal herzustellen. Wählen Sie dieses Symbol aus: ![Geräteportal öffnen-Symbol](images/emulator-deviceportal.png) **Geräteportal öffnen**: Öffnen Sie das Windows-Geräteportal für das HoloLens-Betriebssystem im Emulator.

## <a name="creating-a-username-and-password"></a>Erstellen eines Benutzernamens und Kennworts

![Einrichten des Zugriffs auf das Windows-Geräteportal](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Einrichten des Zugriffs auf das Windows-Geräteportal*

Wenn Sie das erste Mal eine Verbindung der HoloLens mit dem Geräteportal herstellen, müssen Sie einen Benutzernamen und ein Kennwort erstellen.
1. Geben Sie in einem Webbrowser auf dem PC die IP-Adresse der HoloLens ein. Die Seite „Set up access“ (Zugriff einrichten) wird geöffnet.
2. Wählen Sie **Request pin** (PIN anfordern) aus, oder tippen Sie darauf, und betrachten Sie die HoloLens-Anzeige, um die generierte PIN abzurufen.
3. Geben Sie die PIN im Textfeld **PIN displayed on your device** (Auf Ihrem Gerät angezeigte PIN) ein.
4. Geben Sie den Benutzernamen ein, den Sie zum Herstellen der Verbindung mit dem Geräteportal verwenden möchten. Dabei muss es sich nicht um den Namen eines Microsoft-Kontos (MSA) oder einen Domänennamen handeln.
5. Geben Sie ein Kennwort ein, und bestätigen Sie es. Das Kennwort muss mindestens sieben Zeichen lang sein. Es muss kein MSA- oder Domänenkennwort sein.
6. Klicken Sie auf **Koppeln**, um auf der HoloLens eine Verbindung mit dem Windows-Geräteportal herzustellen.

Wenn Sie den Benutzernamen oder das Kennwort ändern möchten, können Sie diesen Vorgang jederzeit wiederholen, indem Sie die Seite für Gerätesicherheit besuchen. Navigieren Sie hierzu zu https://<IHRE_HOLOLENS_IP_ADRESSE>/devicepair.htm.

## <a name="security-certificate"></a>Sicherheitszertifikat

Wenn im Browser eine Meldung zu einem Zertifikatfehler angezeigt wird, können Sie diesen beheben, indem Sie eine Vertrauensstellung mit dem Gerät erstellen.

Jede HoloLens generiert ein selbstsigniertes Zertifikat für die SSL-Verbindung. Standardmäßig wird dieses Zertifikat vom Webbrowser des PC nicht als vertrauenswürdig angesehen, und Sie erhalten möglicherweise eine Meldung zu einem Zertifikatfehler. Sie können eine sichere Verbindung mit dem Gerät herstellen, indem Sie dieses Zertifikat von der HoloLens herunterladen (über USB oder ein vertrauenswürdiges WLAN-Netzwerk) und es auf dem PC als vertrauenswürdig einstufen.
1. **Vergewissern Sie sich, dass Sie sich in einem sicheren Netzwerk (USB-Verbindung oder vertrauenswürdiges WLAN-Netzwerk) befinden**.
2. Laden Sie das Zertifikat dieses Geräts von der Seite „Sicherheit“ im Geräteportal herunter.
   * Navigieren Sie zu: https://<IHRE_HOLOLENS_IP_ADRESSE>/devicepair.htm
   * Öffnen Sie den Knoten für „System“ > „Einstellungen“. 
   * Scrollen Sie nach unten bis zur Gerätesicherheit, und wählen Sie die Schaltfläche „Download this device's certificate“ (Zertifikat dieses Geräts herunterladen) aus.
3. Installieren Sie das Zertifikat im Speicher „Vertrauenswürdige Stammzertifizierungsstellen“ auf Ihrem PC.
   * Geben Sie im Windows-Menü „Computerzertifikate verwalten“ ein, und starten Sie das Applet.
   * Klappen Sie den Ordner **Vertrauenswürdige Stammzertifizierungsstellen** auf.
   * Wählen Sie den Ordner **Zertifikate** aus.
   * Wählen Sie im Menü „Aktion“ „Alle Aufgaben“ > „Importieren...“ aus.
   * Führen Sie den Zertifikatimport-Assistenten mit der Zertifikatdatei aus, die Sie vom Geräteportal heruntergeladen haben.
4. Starten Sie den Browser neu.

>[!NOTE]
> Dieses Zertifikat wird nur für das Gerät als vertrauenswürdig eingestuft, und der Benutzer muss den Prozess erneut durchlaufen, wenn für das Gerät ein Flash ausgeführt wird.

## <a name="sideloading-applications"></a>Querladen von Anwendungen

### <a name="installing-a-certificate"></a>Installieren eines Zertifikats

1. Navigieren Sie im Windows-Geräteportal zu der Seite **App-Manager**
2. Wählen Sie im Abschnitt „Apps bereitstellen“ die Option **Zertifikat installieren** aus
3. Wählen Sie unter „Zum Signieren des App-Pakets verwendete Zertifikatdatei (CER) auswählen“ die Option „Datei auswählen“ aus, und navigieren Sie zu dem Zertifikat, das dem App-Paket zugeordnet ist, das Sie querladen möchten
4. Wählen Sie **Installieren** aus, um die Installation zu starten.

![Screenshot der im Windows-Geräte Portal geöffneten Seite „App-Manager“](images/sideloading-1.png)

### <a name="installing-an-app"></a>Installieren einer App

> [!NOTE]
> Damit eine App erfolgreich über das Geräteportal installiert werden kann, muss sie mit einem Zertifikat signiert sein. Dieses Zertifikat muss auf dem Gerät installiert werden, bevor Sie versuchen, die App zu installieren. Einzelheiten dazu finden Sie im [vorherigen Abschnitt](#installing-a-certificate).

1. Wenn Sie [ein App-Paket in Visual Studio erstellt haben](using-visual-studio.md), können Sie es aus den generierten Dateien per Remotezugriff auf Ihrem Gerät installieren:

![Screenshot des Dateiinhalts des App-Pakets](images/sideloading-2.png)

2. Navigieren Sie im Windows-Geräteportal zu der Seite **App-Manager**
3. Wählen Sie im Bereich **Apps bereitstellen** **Lokaler Speicher** aus
4. Wählen Sie unter „Anwendungspaket auswählen“ die Option „Datei auswählen“ aus, und navigieren Sie zu dem App-Paket, das Sie querladen möchten.
5. Aktivieren Sie die entsprechenden Kontrollkästchen, wenn Sie im Rahmen der App-Installation optionale oder Frameworkpakete installieren möchten, und wählen Sie **Weiter** aus:

![Screenshot der im Windows-Geräte Portal geöffneten Seite „App-Manager“ mit hervorgehobener Registerkarte „Lokaler Speicher“](images/sideloading-3.png)

6. Wählen Sie **Installieren** aus, um die Installation zu starten.
 
![Screenshot der im Windows-Geräte Portal geöffneten Seite „App-Manager“ nach erfolgreich abgeschlossener Installation](images/sideloading-4.png) 

Sobald die Installation abgeschlossen ist, gehen Sie zurück zur Seite **Alle Apps** auf Ihrer HoloLens, und starten Sie Ihre neu installierte Anwendung!

## <a name="device-portal-pages"></a>Seiten des Geräteportals

### <a name="home"></a>Start

![Windows-Geräteportal-Startseite auf Microsoft HoloLens](images/using-windows-portal-img-04.png)<br>
*Windows-Geräteportal-Startseite auf Microsoft HoloLens*

Die Geräteportalsitzung beginnt auf der Startseite. Der Zugriff auf andere Seiten erfolgt über die Navigationsleiste links von der Startseite.

Die Symbolleiste am oberen Rand der Seite ermöglicht den Zugriff auf häufig verwendete Status und Features.
* **Online**: Gibt an, ob das Gerät mit dem WLAN verbunden ist.
* **Herunterfahren**: Schaltet das Gerät aus.
* **Neu starten**: Schaltet das Gerät aus und wieder ein.
* **Sicherheit**: Öffnet die Seite „Device Security“.
* **Cool**: Gibt die Temperatur des Geräts an.
* **A/C**: Gibt an, ob das Gerät angeschlossen ist und geladen wird.
* **Hilfe**: Öffnet die Seite mit der Dokumentation der REST-Schnittstelle.

Auf der Startseite werden die folgenden Informationen angezeigt:
* **Gerätestatus**: Überwacht die Integrität des Geräts und meldet schwerwiegende Fehler.
* **Windows-Informationen**: Zeigt den Namen der HoloLens und die derzeit installierte Version von Windows an.
* **Einstellungen**: Dieser Abschnitt enthält die folgenden Einstellungen:
   * **IPD**: Legt den Pupillenabstand (Interpupillary Distance, IPD) fest. Dies ist der Abstand in Millimeter zwischen dem Mittelpunkt der Pupillen des Benutzers, wenn dieser geradeaus blickt. Die Einstellung wird sofort wirksam. Der Standardwert wurde beim Einrichten des Geräts automatisch berechnet.
   * **Gerätename**: Weisen Sie der HoloLens einen Namen zu. Starten Sie das Gerät nach dem Ändern dieses Werts neu, damit die Änderung wirksam wird. Nach dem Klicken auf **Speichern** wird ein Dialogfeld mit der Frage angezeigt, ob Sie das Gerät sofort oder später neu starten möchten.
   * **Standbymoduseinstellungen**: Hier legen Sie die Wartezeit fest, bevor das Gerät in den Ruhezustand wechselt, wenn es angeschlossen ist und wenn es mit Akkustrom betrieben wird.

### <a name="3d-view"></a>3D View

![Seite „3D-Ansicht“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-05.png)<br>
*Seite „3D-Ansicht“ im Windows-Geräteportal auf Microsoft HoloLens*

Auf der Seite „3D View“ können Sie erkennen, wie die HoloLens Ihre Umgebung interpretiert. Navigieren Sie mit der Maus in der Ansicht:
* Drehen: Linksklick + Bewegen der Maus
* Schwenken: Rechtsklick + Bewegen der Maus
* Zoomen: Drehen des Mausrads
* **Nachverfolgungsoptionen**
   * Wenn Sie **Force visual tracking** markieren, aktivieren Sie die fortlaufende visuelle Nachverfolgung. 
   * Mit **Anhalten** wird die visuelle Nachverfolgung angehalten.
* **Ansichtsoptionen**: Legt Optionen für die 3D-Ansicht fest:
  * **Nachverfolgung**: Gibt an, ob die visuelle Überwachung aktiv ist.
  * **Boden anzeigen**: Zeigt eine schachbrettartige Bodenfläche an.
  * **Frustum anzeigen**: Zeigt das Frustum der Ansicht an.
  * **Stabilisierungsebene anzeigen**: Zeigt die Ebene an, die von der HoloLens für die Bewegungsstabilisierung verwendet wird.
  * **Gittermodell anzeigen**: Zeigt das Gittermodell zur räumlichen Abbildung an, mit dessen Hilfe Ihre Umgebung dargestellt wird.
  * **Raumanker anzeigen**: Zeigt Raumanker für die aktive App an. Wählen Sie die Schaltfläche „Aktualisieren“ aus, um die Anker abzurufen und zu aktualisieren.
  * **Details anzeigen**: Zeigt die Änderung von Handpositionen, der Kopfdrehungsquaternionen und des Geräteursprungsvektors in Echtzeit an.
  * **Vollbild-Schaltfläche**: Mit dieser Schaltfläche wird die 3D-Ansicht im Vollbildmodus angezeigt. Drücken Sie die ESC-Taste, um die Vollbildansicht zu beenden.
* **Oberflächenrekonstruktion**: Klicken oder tippen Sie auf **Aktualisieren**, um das aktuelle Gittermodell für die räumliche Abbildung des Geräts anzuzeigen. Ein vollständiger Durchlauf kann etwas Zeit in Anspruch nehmen (bis zu mehreren Sekunden). Das Gitter wird in der 3D-Ansicht nicht automatisch aktualisiert. Sie müssen **Aktualisieren** auswählen, um das aktuelle Gitter vom Gerät abzurufen. Wählen Sie **Speichern** aus, um das aktuelle Spatial-Mapping-Gitter als OBJ-Datei auf dem PC zu speichern.
* **Raumanker**: Wählen Sie „Aktualisieren“ aus, um die Raumanker für die aktive App anzuzeigen oder zu aktualisieren.

### <a name="map-manager"></a>Zuordnungs-Manager

Mit dem Zuordnungs-Manager können Sie Zuordnungen geräteübergreifend freigeben, die zum Einrichten von gemeinsamen Erfahrungen für Kunden von standortbasiertem Entertainment verwendet werden können. Das Tool ermöglicht das Importieren und Exportieren von Systemzuordnungen und Ankern.  

Melden Sie sich für den Zugriff auf den Zuordnungs-Manager beim Geräteportal an, und wählen Sie **Mixed Reality > Zuordnungs-Manager** aus: 

![Seite des Zuordnungs-Managers im Windows-Geräteportal](images/using-windows-portal-img-06.png)
*Seite des Zuordnungs-Managers im Windows-Geräteportal auf Microsoft HoloLens*

#### <a name="exporting-and-importing-maps"></a>Exportieren und Importieren von Zuordnungen

Wählen Sie zum Exportieren von Zuordnungen **Systemzuordnung und Anker exportieren** aus. Dies kann eine Zeit lang dauern, rechnen mit einer Wartezeit von 30–60 Sekunden, während die Zuordnung exportiert wird. Nachdem der Vorgang abgeschlossen ist, wird die Datei in Ihrem Browser heruntergeladen.  

Zum Importieren von Zuordnungen und Ankern wählen Sie **Upload a map file** (Zuordnungsdatei hochladen) bzw. **Upload an anchor file** (Ankerdatei hochladen) aus, und wählen Sie eine bereits exportierte Zuordnungs- oder Ankerdatei aus. Die hochgeladene Zuordnungs- oder Ankerdatei kann von einem beliebigen anderen HoloLens-Gerät stammen. 

> [!NOTE]
> Auf HoloLens ist es außerdem möglich, die Datenbank für räumliche Abbildung zu importieren und exportieren. Dies funktioniert jedoch nicht auf anderen Geräten als HoloLens.  


### <a name="mixed-reality-capture"></a>Mixed Reality Capture

![Seite „Mixed Reality-Aufnahme“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-07.png)<br>
*Seite „Mixed Reality-Aufnahme“ im Windows-Geräteportal auf Microsoft HoloLens*

Auf der Seite „Mixed Reality Capture“ können Sie Mediendatenströme von der HoloLens speichern.
* **Capture Settings** (Aufnahmeeinstellungen): Steuern Sie die erfassten Mediendatenströme, indem Sie die folgenden Einstellungen aktivieren:
  * **Hologramme**: Erfasst die holografischen Inhalte im Videostream. Hologramme werden in Mono und nicht in Stereo gerendert.
  * **PV-Kamera**: Erfasst den Videodatenstrom der Foto-/Videokamera.
  * **Mic Audio** (Mikrofon-Audio): Erfasst Audioaufnahmen vom Mikrofonarray.
  * **App-Audio**: Erfasst Audioaufnahmen von der derzeit ausgeführten App.
  * **Render from Camera** (Aus Kamerasicht rendern): Richtet die Aufnahme so aus, dass sie aus der Perspektive der Foto-/Videokamera erfolgt, falls dies [von der ausgeführten App unterstützt wird](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (nur HoloLens 2).
  * **Live preview quality** (Qualität der Livevorschau): Wählen Sie die Bildschirmauflösung, Bildfrequenz und Streamingrate für die Livevorschau aus.
* **Audio Settings** (Audioeinstellungen, nur HoloLens 2):
  * **Audio Media Category** (Audiomedienkategorie): Wählen Sie die Kategorie für die Verwendung des Mikrofons aus. **Default** (Standard) enthält Hintergrundgeräusche, während bei **Communications** die Unterdrückung von Hintergrundgeräuschen angewendet wird.
  * **App Audio Gain** (App-Audioverstärkung): Die auf die App-Audiolautstärke angewendete Verstärkung.
  * **Mic Audio Gain** (Mikrofonaudioverstärkung): Die auf die Mikrofon-Audiolautstärke angewendete Verstärkung.
* **Photo and Video Settings** (Foto- und Videoeinstellungen, HoloLens 2-Version 2004 oder höher):
  * **Capture Profile** (Aufnahmeprofil): Wählen Sie das bei der Aufnahme von Fotos und Videos verwendete Profil aus. Nach dem Profil richtet sich, welche Auflösungen und Bildfrequenzen verfügbar sind.
  * **Photo Resolution** (Fotoauflösung): Die Auflösung des aufgenommenen Fotos.
  * **Video Resolution and Frame-rate** (Videoauflösung und Bildfrequenz): Die Auflösung und Bildfrequenz für die Videoaufnahme.
  * **Video Stabilization Buffer** (Videostabilisierungspuffer): Die bei der Videoaufnahme verwendete Puffergröße. Je höher der Wert ist, desto besser können schnelle Bewegungen kompensiert werden.
* Wählen Sie die Schaltfläche **Live preview** aus, oder tippen Sie darauf, um den Aufnahmedatenstrom anzuzeigen. Mit **Stop live preview** (Livevorschau beenden) wird der Aufnahmedatenstrom beendet.
* Wählen Sie **Aufzeichnen** aus, oder tippen Sie darauf, um die Aufzeichnung des Mixed-Reality-Datenstroms mit den angegebenen Einstellungen zu starten. Mit **Aufnahme beenden** wird die Aufzeichnung beendet und gespeichert.
* Wählen Sie **Take photo** aus, oder tippen Sie darauf, um ein Standbild des Aufnahmedatenstroms zu erstellen.
* Wählen Sie **Standardeinstellungen wiederherstellen** aus, oder tippen Sie darauf, um die Standardeinstellungen für Audio, Fotos und Videos wiederherzustellen.
* **Videos und Fotos**: Zeigt eine Liste der auf dem Gerät aufgenommenen Videos und Fotos an.

Alle Einstellungen auf dieser Seite beziehen sich auf Aufnahmen, die mithilfe des Windows-Geräteportals erstellt wurden. Einige gelten darüber hinaus für System-MRC, darunter das Startmenü, Hardwaretasten, globale Sprachbefehle, Miracast und benutzerdefinierte MRC-Recorder.

|  Einstellung  |  Gilt für System-MRC  |  Gilt für benutzerdefinierte MRC-Recorder |
|----------|----------|----------|
|  Holograms  |  Nein  |  Nein |
|  PV camera  |  Nein  |  Nein |
|  Mic Audio  |  Nein  |  Nein |
|  App Audio  |  Nein  |  Nein |
|  Render from Camera  |  Ja    |  Ja (kann überschrieben werden) |
|  Live preview quality  |  Nein  |  Nein |
|  Audio Media Category  |  Ja  |  Nein |
|  App Audio Gain  |  Ja  |  Ja (kann überschrieben werden) |
|  Mic Audio Gain  |  Ja  |  Ja (kann überschrieben werden) |
|  Capture Profile  |  Ja  |  Nein |
|  Photo Resolution  |  Ja  |  Nein |
|  Video Resolution and Frame-rate  |  Ja  |  Nein |
|  Video Stabilization Buffer  |  Ja  |  Ja (kann überschrieben werden) |

> [!NOTE]
> Es bestehen [Einschränkungen für gleichzeitige Mixed Reality-Aufnahmen](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):
> * Wenn eine App versucht, auf die Foto-/Videokamera zuzugreifen, während das Windows-Geräteportal ein Video aufzeichnet, wird die Videoaufzeichnung beendet.
>   * Hololens 2 beendet die Videoaufzeichnung nicht, wenn die App auf die Foto-/Videokamera im SharedReadOnly-Modus zugreift.
> * Wenn eine App die Foto-/Videokamera aktiv verwendet, kann das Windows-Geräteportal ein Foto oder ein Video aufnehmen.
> * Livestreaming:
>   * HoloLens (1. Gen) hindert während eines Livestreams vom Windows-Geräteportal Apps am Zugriff auf die Foto-/Videokamera.
>   * HoloLens (1. Gen) kann keine Livestreams durchführen, wenn eine App die Foto-/Videokamera aktiv verwendet.
>   * Hololens 2 beendet das Livestreaming automatisch, wenn eine App versucht, im ExclusiveControl-Modus auf die Foto-/Videokamera zuzugreifen.
>   * HoloLens 2 kann einen Livestream starten, während eine App die Foto-/Videokamera aktiv verwendet.

### <a name="performance-tracing"></a>Leistungsüberwachung

![Seite „Leistungsüberwachung“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-08.png)<br>
*Seite „Leistungsüberwachung“ im Windows-Geräteportal auf Microsoft HoloLens*

Zeichnen Sie [Windows Performance Recorder](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) (WPR)-Leistungsüberwachungen von Ihrer HoloLens auf.
* **Verfügbare Profile**: Wählen Sie in der Dropdownliste das WPR-Profil aus, und wählen Sie **Starten** aus, oder tippen Sie darauf, um die Ablaufverfolgung zu starten.
* **Benutzerdefinierte Profile**: Wählen Sie **Durchsuchen** aus, oder tippen Sie darauf, um ein WPR-Profil vom PC auszuwählen. Wählen Sie **Hochladen und starten** aus, oder tippen Sie darauf, um die Ablaufverfolgung zu starten.

Zum Beenden der Überwachung wählen Sie den Link „Beenden“ aus. Lassen Sie diese Seite geöffnet, bis der Download der Ablaufverfolgungsdatei abgeschlossen ist.

Aufgezeichnete ETL-Dateien können in [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10)) für die Analyse geöffnet werden.

### <a name="processes"></a>Prozesse

![Seite „Prozesse“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-09.png)<br>
*Seite „Prozesse“ im Windows-Geräteportal auf Microsoft HoloLens*

Zeigt Details zu derzeit ausgeführten Prozessen an. Diese umfassen Apps und Systemprozesse.

### <a name="system-performance"></a>Systemleistung

![Seite „Systemleistung“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-10.png)<br>
*Seite „Systemleistung“ im Windows-Geräteportal auf Microsoft HoloLens*

Zeigt Echtzeitgraphen mit Informationen zur Systemdiagnose an, z. B. Stromverbrauch, Bildfrequenz und CPU-Last.

Die folgenden Metriken sind verfügbar:
* **SoC power** (SoC-Leistungsaufnahme): Augenblickliche Leistungsaufnahme des System-on-a-Chip, gemittelt über eine Minute
* **System power** (System-Leistungsaufnahme): Augenblickliche Leistungsaufnahme des Systems, gemittelt über eine Minute
* **Bildfrequenz**: Bilder pro Sekunde, übersprungene VBlanks pro Sekunde und aufeinanderfolgende übersprungene VBlanks
* **GPU**: Auslastung des GPU-Moduls in Prozent der Gesamtverfügbarkeit
* **CPU**: Verfügbarkeit in Prozent
* **E/A**: Lese- und Schreibvorgänge
* **Netzwerk**: Empfangen und gesendet
* **Arbeitsspeicher**: Gesamter Arbeitsspeicher, genutzter Arbeitsspeicher, zugesicherter Arbeitsspeicher, ausgelagerter Arbeitsspeicher und nicht ausgelagerter Arbeitsspeicher

### <a name="apps"></a>Apps-

![Seite „Apps“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-11.png)<br>
*Seite „Apps“ im Windows-Geräteportal auf Microsoft HoloLens*

Verwaltet die Apps, die auf der HoloLens installiert sind.
* **Installierte Apps**: Entfernen und Starten von Apps.
* **Ausgeführte Apps**: Listet Apps auf, die derzeit ausgeführt werden.
* **App installieren**: Wählen Sie in einem Ordner auf dem Computer oder im Netzwerk App-Pakete für die Installation aus.
* **Abhängigkeit**: Hier fügen Sie Abhängigkeiten für die zu installierende App hinzu.
* **Bereitstellen**: Die ausgewählte App und Abhängigkeiten auf der HoloLens bereitstellen.

### <a name="app-crash-dumps"></a>App Crash Dumps (Absturzabbilder für Apps)

![Seite „App Crash Dumps“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-12.png)<br>
*Seite „App Crash Dumps“ im Windows-Geräteportal auf Microsoft HoloLens*

Auf dieser Seite können Sie Absturzabbilder für die quergeladenen Apps erfassen. Aktivieren Sie das Kontrollkästchen **Crash Dumps Enabled** für jede App, für die Sie Absturzabbilder erfassen möchten. Kehren Sie zum Erfassen von Absturzabbildern zu dieser Seite zurück. Speicherabbilddateien können [zum Debuggen in Visual Studio geöffnet](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files) werden.

### <a name="file-explorer"></a>Datei-Explorer

![Seite „Datei-Explorer“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-13.png)<br>
*Seite „Datei-Explorer“ im Windows-Geräteportal auf Microsoft HoloLens*

Verwenden Sie den Datei-Explorer, um nach Dateien zu suchen, sie hochzuladen und herunterzuladen. Sie können mit Dateien im Ordner „Dokumente“, im Ordner „Bilder“ und in den lokalen Speicherordnern der Apps arbeiten, die Sie aus Visual Studio oder dem Geräteportal bereitgestellt haben.

### <a name="kiosk-mode"></a>Kioskmodus

>[!NOTE]
>Der Kioskmodus ist nur in der [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features) verfügbar.

![Seite „Kioskmodus“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-14.png)

Aktuelle Anweisungen zum Aktivieren des Kioskmodus über das Windows-Geräteportal finden Sie im Artikel [Einrichten von HoloLens im Kioskmodus](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) im Windows IT Pro Center.

### <a name="logging"></a>Protokollierung

![Seite „Protokollierung“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-15.png)<br>
*Seite „Protokollierung“ im Windows-Geräteportal auf Microsoft HoloLens*

Verwaltet die Echtzeit-Ereignisablaufverfolgung für Windows (ETW) auf der HoloLens.

Aktivieren Sie **Hide Providers** (Anbieter ausblenden), um nur die Liste der **Ereignisse** anzuzeigen.
* **Registrierte Anbieter**: Wählen Sie den ETW-Anbieter und die Ablaufverfolgungsebene aus. Für die Ablaufverfolgungsebene wird einer der folgenden Werte festgelegt:
   1. Abnormal exit or termination
   2. Severe errors
   3. Warnungen
   4. Non-error warnings

Wählen Sie **Aktivieren** aus, oder tippen Sie darauf, um die Ablaufverfolgung zu starten. Der Anbieter wird der Liste **Aktivierte Anbieter** hinzugefügt.
* **Benutzerdefinierte Anbieter**: Wählen Sie einen benutzerdefinierten ETW-Anbieter und die Ablaufverfolgungsebene aus. Identifizieren Sie den Anbieter anhand seiner GUID. Fügen Sie keine Klammern in die GUID ein.
* **Aktivierte Anbieter**: Listet die aktivierten Anbieter auf. Wählen Sie einen Anbieter aus der Dropdownliste aus, und klicken oder tippen Sie auf **Deaktivieren**, um die Ablaufverfolgung zu beenden. Klicken oder tippen Sie auf **Beenden**, um sämtliche Ablaufverfolgung anzuhalten.
* **Providers history** (Anbieterverlauf): Zeigt die ETW-Anbieter an, die während der aktuellen Sitzung aktiviert wurden. Klicken oder tippen Sie auf **Aktivieren**, um einen Anbieter zu aktivieren, der deaktiviert war. Klicken oder tippen Sie auf **Löschen**, um den Verlauf zu löschen.
* **Ereignisse**: Listet-ETW-Ereignisse der ausgewählten Anbieter im Tabellenformat auf. Diese Tabelle wird in Echtzeit aktualisiert. Klicken Sie unter der Tabelle auf die Schaltfläche **Löschen**, um alle ETW-Ereignisse aus der Tabelle zu löschen. Hierdurch werden keine Anbieter deaktiviert. Sie können auf **In Datei speichern** klicken, um die derzeit erfassten ETW-Ereignisse in eine lokale CSV-Datei zu exportieren.
* **Filter**: Ermöglicht Ihnen, die erfassten ETW-Ereignisse nach ID, Schlüsselwort, Ebene, Name des Anbieters, Name der Aufgabe oder Text zu filtern. Sie können mehrere Kriterien kombinieren:
   1. Für Kriterien, die sich auf die gleiche Eigenschaft beziehen, werden Ereignisse angezeigt, die einem der Kriterien genügen können.
   2. Für Kriterien, die sich auf eine andere Eigenschaft beziehen, müssen die Ereignisse allen Kriterien genügen

Beispielsweise können Sie die Kriterien *(Name der Aufgabe enthält ‚Foo‘ oder ‚Bar‘) UND (Text enthält ‚Fehler‘ oder ‚Warnung‘ )* angeben

### <a name="simulation"></a>Simulation

![Seite „Simulation“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-16.png)<br>
*Seite „Simulation“ im Windows-Geräteportal auf Microsoft HoloLens*

Ermöglicht Ihnen das Aufzeichnen und Wiedergeben von Eingabedaten für Testzwecke.
* **Capture room** (Raum erfassen): Wird verwendet, um eine Datei für einen simulierten Raum herunterzuladen, die das Spatial-Mapping-Gitter für die Umgebung des Benutzers enthält. Benennen Sie den Raum, und klicken Sie auf **Aufnahme**, um die Daten als XEF-Datei auf dem PC zu speichern. Diese Raumdatei kann in den HoloLens-Emulator geladen werden.
* **Aufzeichnung**: Markieren Sie die aufzuzeichnenden Datenströme, benennen Sie die Aufzeichnung, und klicken oder tippen Sie auf **Aufzeichnen**, um die Aufzeichnung zu starten. Führen Sie mit der HoloLens Aktionen aus, und klicken Sie dann auf **Beenden**, um die Daten als XEF-Datei auf dem PC zu speichern. Diese Datei kann im HoloLens-Emulator oder auf dem Gerät geladen werden.
* **Wiedergabe**: Klicken oder tippen Sie auf **Upload recording** (Aufzeichnung hochladen), um auf dem PC eine XEF-Datei auszuwählen und die Daten an die HoloLens zu senden.
* **Steuerungsmodus**: Wählen Sie in der Dropdownliste **Standard** oder **Simulation** aus, und klicken oder tippen Sie auf die Schaltfläche **Festlegen**, um den Modus der HoloLens auszuwählen. Durch Auswahl von „Simulation“ werden die realen Sensoren auf der HoloLens deaktiviert und stattdessen hochgeladene simulierte Daten verwendet. Wenn Sie zu „Simulation“ wechseln, reagiert die HoloLens nicht auf den realen Benutzer, bis Sie zurück zu „Standard“ wechseln.

### <a name="networking"></a>Netzwerk

![Seite „Netzwerk“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-17.png)<br>
*Seite „Netzwerk“ im Windows-Geräteportal auf Microsoft HoloLens*

Verwaltet die WLAN-Verbindungen der HoloLens.
* **WLAN-Adapter**: Wählen Sie mithilfe der Dropdown-Steuerelemente einen WLAN-Adapter und ein Profil aus. Klicken oder tippen Sie auf **Verbinden**, um den ausgewählten Adapter zu verwenden.
* **Verfügbare Netzwerke**: Listet die WLAN-Netzwerke auf, mit denen die HoloLens eine Verbindung herstellen kann. Klicken oder tippen Sie auf **Aktualisieren**, um die Liste zu aktualisieren.
* **IP-Konfiguration**: Zeigt die IP-Adresse und andere Details der Netzwerkverbindung an.

### <a name="virtual-input"></a>Virtual Input

![Seite „Virtual Input“ im Windows-Geräteportal auf Microsoft HoloLens](images/using-windows-portal-img-18.png)<br>
*Seite „Virtual Input“ im Windows-Geräteportal auf Microsoft HoloLens*

Sendet die Tastatureingabe vom Remotecomputer an die HoloLens.

Klicken oder tippen Sie auf den Bereich unter **Virtual keyboard** (virtuelle Tastatur), um das Senden von Tastatureingaben an die HoloLens zu aktivieren. Geben Sie im Textfeld **Eingabetext** Text ein, und klicken oder tippen Sie auf **Senden**, um die Tastatureingaben an die aktive App zu senden.

## <a name="device-portal-rest-apis"></a>REST-APIs des Geräteportals

Alle Komponenten im Windows-Geräteportal basieren auf [REST-APIs](device-portal-api-reference.md), die Sie optional für den Zugriff auf die Daten und die programmatische Steuerung des Geräts verwenden können.

## <a name="troubleshooting"></a>Problembehandlung

### <a name="how-to-fix-the-its-lonely-here-message"></a>Beheben der Meldung „It's lonely here“ (Es ist einsam hier)

> [!NOTE]
> Der Wechsel von einer HoloLens 2 zu einer HoloLens (1. Generation) kann dazu führen, dass die Seiten vereinzeln, wenn sie vor der Verwendung auf der HoloLens (1. Generation) auf der HoloLens 2 verwendet worden waren.

![Meldung „It's lonely here“ auf der Seite des Geräteportals](images/using-windows-portal-img-19.png)

1. Wählen Sie im Menü oben links **Layout zurücksetzen** aus:

![Auswählen von „Layout zurücksetzen“ im Menü des Geräteportals](images/using-windows-portal-img-20.png)

2. Klicken Sie unter der Überschrift **Arbeitsbereich zurücksetzen** auf **Layout zurücksetzen**. Die Portalseite wird automatisch aktualisiert und zeigt Ihre Inhalte an.

![Auswählen von „Layout zurücksetzen“ auf der Seite „Arbeitsbereich zurücksetzen“](images/using-windows-portal-img-21.png)