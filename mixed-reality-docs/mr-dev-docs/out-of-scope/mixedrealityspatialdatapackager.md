---
title: Mixed Reality Spatial Data Packager-Dokumentation
description: Das Mixed Reality Spatial Data Packager-Tool ist jetzt veraltet und funktioniert auf keiner Plattform mehr. Stattdessen wird das Karten-Manager-Tool empfohlen.
author: hferrone
ms.author: v-hferrone
ms.date: 08/03/2020
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 914e22c4e80385c93696ebd978000978e1e03f57706d466bdbb3cfcd5843f69e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213164"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Mixed Reality Spatial Data Packager-Dokumentation

>[!NOTE]
> VERALTET 
> 
> Seit dem 1.8.2020 ist dieses Tool veraltet und funktioniert auf keiner Plattform mehr. Es wird empfohlen, stattdessen [das Karten-Manager-Tool](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) in Geräteportal zu verwenden. 
> 
> Dieses Tool und sein Betrieb werden wie bensent angeboten. Sie kann ohne vorherige Ankündigung geändert werden und ist möglicherweise nicht mit zukünftigen Windows oder Windows Mixed Reality HMD-Releases kompatibel. 


## <a name="download"></a>Herunterladen
 Laden [Sie MixedRealitySpatialDataPackager hier herunter.](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Mixed Reality Spatial Data Packager</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>Schnellstart

Das Mixed Reality Spatial Data Packager-Tool kopiert die räumlichen Daten einer Ziel-App über einen zweistufigen Export- und Importvorgang von einem PC auf einen anderen. Das Tool muss mit Administratorrechten ausgeführt werden und löscht die vorhandenen räumlichen Daten beim Import. Beim Export bleiben die vorhandenen räumlichen Daten intakt.

Wichtige Anforderungen und Einschränkungen:

1. Das Tool muss mit Administratorrechten ausgeführt werden. 
2. Möglicherweise müssen Sie den PC neu starten, wenn Mixed Reality-Portal nach dem Ausführen des Tools instabil ist.
3. Das Tool wird nicht ausgeführt, wenn Versionskonflikte oder Inkompatibilitäten räumlicher Daten auftreten.
4. Tool löscht vorhandene räumliche Daten beim Import
5. Wenn beim Importvorgang ein Fehler auftritt, können vorherige Daten nur wiederhergestellt werden, wenn sie zuvor durch den Export sichern wurden.
6. Qualität der Importfunktionalität abhängig vom "schreibgeschützten" Modus für räumliche Kartendaten
***

## <a name="mapping-best-practices"></a>Bewährte Methoden für die Zuordnung

1. Vorhandene Zuordnungen aus dem Systemsteuerung löschen (Einstellungen -> Mixed Reality -> Environment -> Löschen von Umgebungsdaten)
2. Stellen Sie eine ausreichende Beleuchtung für eine gute Nachverfolgung sicher, und versuchen Sie, die gleiche Beleuchtung zu erhalten, wenn Sie den gesperrten Kartenmodus ausführen.
3. Halten Sie nach Möglichkeit den dynamischen Beleuchtungsbereich niedrig, indem Sie Bereiche mit hoher Lichtstärke neben dunklen, überschattenden Bereichen vermeiden.
4. Minimieren Sie leere, texturlose Oberflächen, z. B. platzieren Sie eine Reihe verschiedener Poster auf weißen Wänden.
5. Zuordnen des Raums ohne dynamische Objekte in der Szene, z. B. verschiebende Personen
6. Sperren der Karte beim Import (verfügbar über Insider Preview)
7. Entsperren der Karte und erneutes Einscannen der Umgebung, wenn die Nachverfolgung der Qualität beeinträchtigt wird und/oder Änderungen an der Umgebung vorgenommen werden (Beleuchtung oder Änderungen am Objektlayout)
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Ausführen Mixed Reality Spatial Data Packager mit begleitbezogenem Skript

Wir haben eine MRSpatialPackagerHelperScript.ps1, mit der der Kartenpaketierer die Tools ausgeführt wird. 


Die Skriptparameter sind unten definiert:

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>PowerShell-Skript – Beispielverwendung und -ausgabe

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a>Exportieren mit MixedRealitySpatialDataPackager.exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

Beim Exportieren von Karten vom Gerät werden zwei mapx-Dateien generiert: het.mapx und sa.mapx. Während des Exportvorgangs werden alle Raumanker entfernt, mit Ausnahme der angegebenen App und der vom Benutzer erstellten Grenze (sofern vorhanden). Der Name der Quellpaketfamilie muss mit einer vorhandenen installierten App übereinstimmen, da die EXE-Datei nicht ausgeführt werden kann.

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a>Importieren mit MixedRealitySpatialDataPackager.exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
Import löscht die vorhandenen räumlichen Daten und ersetzt sie durch die Daten aus dem angegebenen Verzeichnis. Die Eingabe des App-Namens gibt den Paketnamen der Ziel-App an, für die wie die Raumanker importiert werden sollen, und die Zielbenutzer-SID gibt den Benutzer an, der Zugriff auf die importierten Raumanker haben soll. Der Name der Zielpaketfamilie und die Benutzer-SIDs müssen mit den vorhandenen Werten auf dem PC übereinstimmen, da die EXE-Datei anderell fehlschlägt.


***
## <a name="error-messages"></a>Fehlermeldungen
Darüber hinaus werden die fehlermeldungen unten angegebenen Fehler auch mit einem HRESULT begleitet.

### <a name="if-there-was-an-error-invalid-arguments"></a>Wenn ein Fehler bei ungültigen Argumenten aufgetreten ist
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Wenn die ausführbare Datei nicht im Administratormodus ausgeführt wurde
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Wenn beim Aktivieren oder Deaktivieren des Treibers ein Fehler aufgetreten ist
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Wenn beim Überprüfen der Version der räumlichen Datenbank ein Fehler aufgetreten ist
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Wenn beim Überprüfen des Paketfamiliennamens für die Ziel-Import/Export-App ein Fehler aufgetreten ist
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Wenn beim Überprüfen der Benutzer-SID ein Fehler aufgetreten ist
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Wenn ein Fehler im Zusammenhang mit dem Ziel oder den räumlichen Quelldatendateien aufgetreten ist
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>Wenn beim Starten und Beenden von Spectrum/SharedRealitySvc ein Fehler aufgetreten ist
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```