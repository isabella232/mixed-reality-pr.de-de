---
title: Referenz der Geräteportal-API
description: Bleiben Sie über die Windows Geräteportal-API für HoloLens Entwicklung auf dem laufenden.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, Windows Geräteportal, API, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 6b41c569917150c303da933a75d354f574fb579ba676dac281e9cde2bfc59818
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207838"
---
# <a name="device-portal-api-reference"></a>Referenz der Geräteportal-API

Alles in der [Windows Geräteportal](using-the-windows-device-portal.md) basiert auf REST-APIs, die Sie verwenden können, um auf die Daten zuzugreifen und Ihr Gerät programmgesteuert zu steuern.

## <a name="app-deloyment"></a>App-Deloyment

**/api/app/packagemanager/package (DELETE)**

Deinstalliert eine App.

Parameter
* package: Dateiname des zu deinstallierenden Pakets.

**/api/app/packagemanager/package (POST)**

Installiert eine App

Parameter
* package: Dateiname des zu installierenden Pakets.

Nutzlast
* Mehrteiligen konformen HTTP-Text

**/api/app/packagemanager/packages (GET)**

Ruft die Liste der installierten Apps auf dem System mit Details ab.

Daten zurückgeben
* Liste der installierten Pakete mit Details

**/api/app/packagemanager/state (GET)**

Ruft den Status der app-Installation ab, die gerade ausgeführt wird.

## <a name="dump-collection"></a>Absturzabbildsammlung

**/api/debug/dump/usermode/crashcontrol (DELETE)**

Deaktiviert die Absturzabbildsammlung für eine quergeladene App.

Parameter
* packageFullname: Paketname

**/api/debug/dump/usermode/crashcontrol (GET)**

Ruft Einstellungen für die Absturzabbildsammlung für quergeladene Apps ab.

Parameter
* packageFullname: Paketname

**/api/debug/dump/usermode/crashcontrol (POST)**

Aktiviert und legt Einstellungen für die Speicherabbildsteuerung für eine quergeladene App fest.

Parameter
* packageFullname: Paketname

**/api/debug/dump/usermode/crashdump (DELETE)**

Löscht ein Absturzabbild für eine quergeladene App.

Parameter
* packageFullname: Paketname
* fileName: Speicherabbilddateiname

**/api/debug/dump/usermode/crashdump (GET)**

Ruft ein Absturzabbild für eine quergeladene App ab.

Parameter
* packageFullname: Paketname
* fileName: Speicherabbilddateiname

Daten zurückgeben
* Dumpdatei. Überprüfen mit WinDbg oder Visual Studio

**/api/debug/dump/usermode/dumps (GET)**

Gibt eine Liste aller Absturzabbilder für quergeladene Apps zurück.

Daten zurückgeben
* Liste der Absturzabbilder pro quergeladener App

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

Listet registrierte Anbieter auf.

Daten zurückgeben
* Liste der Anbieter, Anzeigename und GUID

**/api/etw/session/realtime (GET/WebSocket)**

Erstellt eine ETW-Echtzeitsitzung. verwaltet über ein Websocket.

Daten zurückgeben
* ETW-Ereignisse von den aktivierten Anbietern

## <a name="holographic-os"></a>Holographic – Betriebssystem

**/api/holographic/os/etw/customproviders (GET)**

Gibt eine Liste HoloLens bestimmten ETW-Anbieter zurück, die nicht beim System registriert sind.

**/api/holographic/os/services (GET)**

Gibt die Status aller ausgeführten Dienste zurück.

**/api/holographic/os/settings/ipd (GET)**

Ruft die gespeicherte IPD (Interpupillary distance) in Millimetern ab.

**/api/holographic/os/settings/ipd (POST)**

Legt die IPD fest.

Parameter
* ipd: Neuer IPD-Wert, der in Millimetern festgelegt werden soll

**/api/holographic/os/webmanagement/settings/https (GET)**

Abrufen der HTTPS-Anforderungen für das Geräteportal

**/api/holographic/os/webmanagement/settings/https (POST)**

Legt HTTPS-Anforderungen für die Geräteportal

Parameter
* erforderlich: Ja, Nein oder Standard

## <a name="holographic-perception"></a>Holografische Wahrnehmung

**/api/holographic/perception/client (GET/WebSocket)**

Akzeptiert Websocket-Upgrades und führt einen Perception-Client aus, der Updates mit 30 fps sendet.

Parameter
* clientmode: "active" erzwingt den visuellen Nachverfolgungsmodus, wenn er nicht passiv eingerichtet werden kann.

## <a name="holographic-thermal"></a>HolographicOgraphic

**/api/holographic/solar/stage (GET)**

Abrufen der wärmeren Stufe des Geräts (0 normal, 1 warm, 2 kritisch)

## <a name="map-manager"></a>Zuordnungs-Manager

**/api/holographic/mapmanager/mapFiles (GET)**

Ruft die Liste der verfügbaren Zuordnungsdateien (MAPX) ab.

**/api/holographic/mapmanager/anchorFiles (GET)**

Ruft die Liste der verfügbaren Ankerdateien (.ancx) ab.

**/api/holographic/mapmanager/srdbFiles (GET)**

Ruft die Liste der verfügbaren räumlichen Datenbankdateien (SRDB) ab.

**/api/holographic/mapmanager/getanchors (GET)**

Ruft die Liste der persistenten Anker für den aktuellen Benutzer ab. 

### <a name="downloaduploaddelete-files"></a>Herunterladen/Hochladen/Löschen von Dateien
**/api/holographic/mapmanager/download (GET)**

Lädt eine Zuordnungs-, Anker- oder raumbezogene Datenbankdatei herunter. Die Datei muss zuvor hochgeladen oder exportiert worden sein.

Parameter
* FileName: Name der herunterzuladenden Datei.

Beispiel: 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

**/api/holographic/mapmanager/upload (POST)**

Lädt eine Karten-, Anker- oder raumbezogene Datenbankdatei hoch. Nachdem eine Datei hochgeladen wurde, kann sie später importiert werden, damit sie vom System verwendet werden kann.

Parameter
* file: Name der hochzuladenden Datei.

Beispiel:
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

**/api/holographic/mapmanager/delete (POST)**

Löscht eine Karten-, Anker- oder raumbezogene Datenbankdatei. Die Datei muss zuvor hochgeladen oder exportiert worden sein.

Parameter
* FileName: Name der zu löschenden Datei.

Beispiel: 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a>Exportieren

**/api/holographic/mapmanager/export (POST)**

Exportiert die karte, die derzeit vom System verwendet wird. Nach dem Exportieren kann es heruntergeladen werden. 

Beispiel: 
```
$.post("/api/holographic/mapmanager/export")
```

**/api/holographic/mapmanager/exportanchors (POST)**

Exportiert die karte, die derzeit vom System verwendet wird. Nach dem Exportieren kann es heruntergeladen werden. Beispiel: 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

**/api/holographic/mapmanager/exportmapandanchors (POST)**

Exportiert die Karte und die Anker, die derzeit vom System verwendet werden. Sobald sie exportiert wurden, können sie heruntergeladen werden. Beispiel: 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**

Exportiert die derzeit vom System verwendete Kartendatenbank und die Datenbank für räumliche Nachbauung. Nachdem sie exportiert wurden, können sie heruntergeladen werden. 

Beispiel: 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a>Importieren

**/api/holographic/mapmanager/import (POST)**

Gibt dem System an, welche Zuordnung derzeit verwendet werden soll. Kann für Dateien aufgerufen werden, die exportiert oder hochgeladen wurden.

Parameter
* FileName: Name der zu verwendenden Zuordnung. 

Beispiel: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importanchors (POST)**

Gibt dem System an, welche Anker derzeit verwendet werden sollen. Kann für Dateien aufgerufen werden, die exportiert oder hochgeladen wurden.

Parameter
* FileName: Name der zu verwendenden Anker. 

Beispiel: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importsmapalmappingdb (POST)**

Gibt für das System an, welche Datenbank für räumliche Vererbung derzeit verwendet werden soll. Kann für Dateien aufgerufen werden, die exportiert oder hochgeladen wurden.

Parameter
* FileName: Name der zu verwendenden räumlichen Zuordnungs-Db. 

Beispiel: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a>Sonstiges

**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**

Setzen Sie die Karte, die Anker und die datenbank der räumlichen Erneuerung des Systems zurück.

Beispiel: 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

**/api/holographic/mapmanager/status (GET)**

Ruft den Status des Systems ab, einschließlich der Karten-, Anker- und räumlichen Nachstellungsdatenbankdateien, die zuletzt importiert wurden. 


## <a name="mixed-reality-capture"></a>Mixed Reality Capture

**/api/holographic/mrc/file (GET)**

Lädt eine Mixed Reality-Datei vom Gerät herunter. Verwenden Sie den Abfrageparameter op=stream für das Streaming.

Parameter
* filename: Name der zu erhaltenden Videodatei, hexadezimal64-codiert
* op: stream

**/api/holographic/mrc/file (DELETE)**

Löscht eine Mixed Reality-Aufzeichnung vom Gerät.

Parameter
* filename: Name der zu löschenden Datei, hexadezimal64-codiert

**/api/holographic/mrc/files (GET)**

Gibt die Liste der auf dem Gerät gespeicherten Mixed Reality-Dateien zurück.

**/api/holographic/mrc/photo (POST)**

Aufnahme eines Mixed Reality-Fotos und Erstellen einer Datei auf dem Gerät

Parameter
* holo: Hologramme erfassen: true oder false (Standardwert ist FALSE)
* pv : PV-Kamera erfassen: true oder false (Standardwert ist FALSE)
* RenderFromCamera: (nur HoloLens 2) rendern aus der Perspektive der Foto-/Videokamera: true oder false (Standardwert true)

**/api/holographic/mrc/settings (GET)**

Ruft die Standardmäßige Mixed Reality-Erfassungseinstellungen ab.

**/api/holographic/mrc/settings (POST)**

Legt die Standardeinstellungen für Mixed Reality-Erfassungen fest.  Einige dieser Einstellungen werden auf die MRC-Foto- und Videoaufnahme des Systems angewendet.

**/api/holographic/mrc/status (GET)**

Ruft den Zustand der Mixed Reality-Erfassung innerhalb des Windows Geräteportal.

***Antwort***

Die Antwort enthält eine JSON-Eigenschaft, die angibt, Windows Geräteportal Video aufzeichnen oder nicht.

``` javascript
{"IsRecording" : boolean}
```

**/api/holographic/mrc/thumbnail (GET)**

Ruft das Miniaturbild für die angegebene Datei ab.

Parameter
* filename: Name (hexadezimal64-codiert) der Datei, für die die Miniaturansicht angefordert wird

**/api/holographic/mrc/video/control/start (POST)**

Startet eine Mixed Reality-Aufzeichnung

Parameter
* holo: Hologramme erfassen: true oder false (Standardwert ist FALSE)
* pv : PV-Kamera erfassen: true oder false (Standardwert ist FALSE)
* mic: Mikrofon erfassen: true oder false (Standardwert ist FALSE)
* loopback: App-Audio erfassen: true oder false (Standardwert ist FALSE)
* RenderFromCamera: (nur HoloLens 2) rendern aus der Perspektive der Foto-/Videokamera: true oder false (Standardwert true)
* vstab: (nur HoloLens 2) Video stabilization: true oder false (Standardwert true)
* vstabbuffer: (nur HoloLens 2) Latenz des Puffers für die Videostabilisierung: 0 bis 30 Frames (Standardwert: 15 Frames)

**/api/holographic/mrc/video/control/stop (POST)**

Beendet die aktuelle Mixed Reality-Aufzeichnung

## <a name="mixed-reality-streaming"></a>Mixed Reality Streaming

> [!CAUTION]
> Aufgrund der Loopbackisolation können Sie keine Verbindung mit Mixed Reality Streaming aus einer App auf einem Gerät herstellen.

HoloLens unterstützt die Livevorschau von Mixed Reality über den blockierten Download einer fragmentierten MP4-Datei.

Mixed Reality-Streams verwenden denselben Parametersatz, um zu steuern, was erfasst wird:
* holo: Hologramme erfassen: true oder false
* pv : PV-Kamera erfassen: true oder false
* mic: Mikrofon erfassen: true oder false
* loopback: App-Audio erfassen: true oder false

Wenn keines dieser Angaben angegeben ist, werden Hologramme, Foto-/Videokameras und App-Audiodaten erfasst.<br>
Falls ein Parameter angegeben ist: Die nicht angegebenen Parameter werden standardmäßig auf FALSE festgelegt.

Optionale Parameter (nur HoloLens 2)
* RenderFromCamera: Rendern aus der Perspektive der Foto-/Videokamera: true oder false (Standardwert true)
* vstab : Videostabilisierung aktivieren: true oder false (Standardwert ist FALSE)
* vstabbuffer: Latenz des Puffers für die Videostabilisierung: 0 bis 30 Frames (Standardwert: 15 Frames)

**/api/holographic/stream/live.mp4 (GET)**

Ein 1280x720p-30Fps-Stream mit 5 MBit.

**/api/holographic/stream/live_high.mp4 (GET)**

Ein 1280x720p-30Fps-Stream mit 5 MBit.

**/api/holographic/stream/live_med.mp4 (GET)**

Ein 854x480p 30fps-Stream mit 2,5 MBit.

**/api/holographic/stream/live_low.mp4 (GET)**

Ein 428x240p 15fps-Stream mit 0,6 MBit.

## <a name="networking"></a>Netzwerk

**/api/networking/ipconfig (GET)**

Ruft die aktuelle IP-Konfiguration ab.

## <a name="os-information"></a>Betriebssysteminformationen

**/api/os/info (GET)**

Ruft Betriebssysteminformationen ab.

**/api/os/machinename (GET)**

Ruft den Computernamen ab.

**/api/os/machinename (POST)**

Legt den Computernamen fest.

Parameter
* name: Neuer Computername, hexadezimal64-codiert, der auf festgelegt werden soll

## <a name="perception-simulation-control"></a>Perception Simulation Control

**/api/holographic/simulation/control/mode (GET)**

Verwenden des Simulationsmodus

**/api/holographic/simulation/control/mode (POST)**

Festlegen des Simulationsmodus

Parameter
* mode : Simulationsmodus: Standard, Simulation, Remote, Legacy

**/api/holographic/simulation/control/stream (DELETE)**

Löscht einen Steuerungsstream.

**/api/holographic/simulation/control/stream (GET/WebSocket)**

Öffnen Sie eine Websocketverbindung für einen Steuerungsstream.

**/api/holographic/simulation/control/stream (POST)**

Erstellen Sie einen Steuerungsdatenstrom (Priorität ist erforderlich), oder posten Sie Daten in einen erstellten Stream (streamId erforderlich). Es wird erwartet, dass die gesendeten Daten vom Typ "application/octet-stream" sind.

**/api/holographic/simulation/display/stream (GET/WebSocket)**

Fordern Sie einen Simulationsvideostream mit dem Inhalt an, der im Simulationsmodus auf der Systemanzeige gerendert wird.  Zunächst wird ein einfacher Formatdeskriptorheader gesendet, gefolgt von H.264-codierten Texturen, denen jeweils ein Header vorangestellt ist, der den Augenindex und die Texturgröße angibt.

## <a name="perception-simulation-playback"></a>Wiedergabe der Wahrnehmungssimulation

**/api/holographic/simulation/playback/file (DELETE)**

Löscht eine Aufzeichnung.

Parameter
* recording: Name der zu löschenden Aufzeichnung.

**/api/holographic/simulation/playback/file (POST)**

Hochladen einer Aufzeichnung.

**/api/holographic/simulation/playback/files (GET)**

Alle Aufzeichnungen erhalten.

**/api/holographic/simulation/playback/session (GET)**

Hiermit wird der aktuelle Wiedergabezustand einer Aufzeichnung erhalten.

Parameter
* recording: Name der Aufzeichnung.

**/api/holographic/simulation/playback/session/file (DELETE)**

Entladen einer Aufzeichnung.

Parameter
* recording: Name der zu entladenden Aufzeichnung.

**/api/holographic/simulation/playback/session/file (POST)**

Laden sie eine Aufzeichnung.

Parameter
* recording: Name der zu ladenden Aufzeichnung.

**/api/holographic/simulation/playback/session/files (GET)**

Hiermit werden alle geladenen Aufzeichnungen erhalten.

**/api/holographic/simulation/playback/session/pause (POST)**

Anhalten einer Aufzeichnung.

Parameter
* recording: Name der Aufzeichnung.

**/api/holographic/simulation/playback/session/play (POST)**

Wiedergabe einer Aufzeichnung.

Parameter
* recording: Name der Aufzeichnung.

**/api/holographic/simulation/playback/session/stop (POST)**

Beenden Sie eine Aufzeichnung.

Parameter
* recording: Name der Aufzeichnung.

**/api/holographic/simulation/playback/session/types (GET)**

Hiermit werden die Datentypen in einer geladenen Aufzeichnung angezeigt.

Parameter
* recording: Name der Aufzeichnung.

## <a name="perception-simulation-recording"></a>Aufzeichnung der Wahrnehmungssimulation

**/api/holographic/simulation/recording/start (POST)**

Starten Sie eine Aufzeichnung. Nur eine einzelne Aufzeichnung kann gleichzeitig aktiv sein. Eine der Haupt-, Hände-, spatialMapping- oder Umgebungs- muss festgelegt werden.

Parameter
* head: Legen Sie auf 1 fest, um Hauptdaten zu erfassen.
* hands: Legen Sie auf 1 fest, um Handdaten zu erfassen.
* spatialMapping: Legen Sie auf 1 fest, um die räumliche Zuordnung zu erfassen.
* environment: Legen Sie auf 1 fest, um Umgebungsdaten aufzeichnen.
* name: Name der Aufzeichnung.
* singleSpatialMappingFrame: Legen Sie auf 1 fest, um nur einen einzelnen räumlichen Zuordnungsrahmen aufzuzeichnen.

**/api/holographic/simulation/recording/status (GET)**

Abrufen des Aufzeichnungszustands.

**/api/holographic/simulation/recording/stop (GET)**

Beenden Sie die aktuelle Aufzeichnung. Die Aufzeichnung wird als Datei zurückgegeben.

## <a name="performance-data"></a>Leistungsdaten

**/api/resourcemanager/processes (GET)**

Gibt die Liste der ausgeführten Prozesse mit Details zurück.

Daten zurückgeben
* JSON mit Einer Liste von Prozessen und Details für jeden Prozess

**/api/resourcemanager/systemperf (GET)**

Gibt Systemleistungsstatistiken (E/A-Lese-/Schreibzugriff, Speicherstatistiken usw.) zurück.

Daten zurückgeben
* JSON mit Systeminformationen: CPU, GPU, Arbeitsspeicher, Netzwerk, E/A

## <a name="power"></a>Leistung

**/api/power/battery (GET)**

Ruft den aktuellen Akkuzustand ab.

**/api/power/state (GET)**

Überprüft, ob sich das System im Energiesparzustand befindet.

## <a name="remote-control"></a>Remotesteuerung

**/api/control/restart (POST)**

Startet das Zielgerät neu.

**/api/control/shutdown (POST)**

Herunterfahren des Zielgeräts

## <a name="task-manager"></a>Task-Manager

**/api/taskmanager/app (DELETE)**

Beendet eine moderne App

Parameter
* package: Vollständiger Name des App-Pakets, hex64-codiert
* forcestop : Erzwingen, dass alle Prozesse beendet werden (=yes)

**/api/taskmanager/app (POST)**

Startet eine moderne App

Parameter
* appid: PRAID der zu startden App, hex64-codiert
* package: Vollständiger Name des App-Pakets, hex64-codiert

## <a name="wifi-management"></a>WLAN-Verwaltung

**/api/wifi/interfaces (GET)**

Listet Drahtlosnetzwerkschnittstellen auf.

Daten zurückgeben
* Liste der Drahtlosschnittstellen mit Details (GUID, Beschreibung usw.)

**/api/wifi/network (DELETE)**

Löscht ein Profil, das einem Netzwerk auf einer angegebenen Schnittstelle zugeordnet ist.

Parameter
* schnittstelle: Netzwerkschnittstellen-GUID
* profile : Profilname

**/api/wifi/networks (GET)**

Listet Drahtlosnetzwerke auf der angegebenen Netzwerkschnittstelle auf.

Parameter
* schnittstelle: Netzwerkschnittstellen-GUID

Daten zurückgeben
* Liste der Drahtlosnetzwerke auf der Netzwerkschnittstelle mit Details

**/api/wifi/network (POST)**

Stellt eine Verbindung mit einem Netzwerk auf der angegebenen Schnittstelle her oder trennt diese.

Parameter
* schnittstelle: Netzwerkschnittstellen-GUID
* ssid: ssid, hex64-codiert, zum Herstellen einer Verbindung mit
* op: Verbinden oder Trennen
* createprofile: ja oder nein
* key: gemeinsam verwendeter Schlüssel, hex64-codiert

## <a name="windows-performance-recorder"></a>Windows Performance Recorder

**/api/wpr/customtrace (POST)**

Lädt ein WPR-Profil hoch und startet die Ablaufverfolgung mithilfe des hochgeladenen Profils.

Nutzlast
* Mehrteiligen konformen HTTP-Text

Daten zurückgeben
* Gibt den WPR-Sitzungsstatus zurück.

**/api/wpr/status (GET)**

Ruft den Status der WPR-Sitzung ab.

Daten zurückgeben
* WPR-Sitzungsstatus.

**/api/wpr/trace (GET)**

Beendet eine WPR-Ablaufverfolgungssitzung (Performance)

Daten zurückgeben
* Gibt die ETL-Ablaufverfolgungsdatei zurück.

**/api/wpr/trace (POST)**

Startet eine WPR-Ablaufverfolgungssitzung (Performance)

Parameter
* profile: Profilname. Verfügbare Profile werden in perfprofiles/profiles.json gespeichert.

Daten zurückgeben
* Gibt beim Start den WPR-Sitzungsstatus zurück.

## <a name="see-also"></a>Siehe auch
* [Verwenden des Windows-Geräteportals](using-the-windows-device-portal.md)
* [Geräteportal Api-Referenz (Core API Reference, UWP)](/windows/uwp/debug-test-perf/device-portal-api-core)