---
title: Veröffentlichen im Microsoft Store
description: Erfahren Sie, wie Sie Ihre Unreal-Mixed Reality-Anwendungen für den Microsoft Store verpacken, zertifizieren und sie dort veröffentlichen können.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Dokumentation, Leitfäden, Features, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Veröffentlichen, Verteilung, Microsoft Store
ms.openlocfilehash: 41f081f11cdb9ac2fdf96a81bb761a1321d1776f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010020"
---
# <a name="publishing-to-the-microsoft-store"></a>Veröffentlichen im Microsoft Store

Wenn Sie bereit sind, ihre Unreal-App zu veröffentlichen, müssen Sie ein paar Projekteinstellungen aktualisieren, bevor Sie sie an den Microsoft Store senden. Alle diese Einstellungen verfügen über Standardwerte, sollten aber für die Produktion geändert werden, damit die Anwendung optimal dargestellt wird.

## <a name="project-settings-for-the-store-packaging"></a>Projekteinstellungen für die Store-Verpackung

1. Wählen Sie zunächst **Projekteinstellungen > Beschreibung** aus, und aktualisieren Sie die Spiel- und Herausgeberinformationen: 
    * Der **Spielname** wird in der App-Kachel auf der HoloLens angezeigt.
    * Der **Distinguished Name des Unternehmens** wird beim Generieren des Projektzertifikats verwendet und sollte folgendes Format aufweisen: 
        * **CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:

![Screenshot des Unreal-Editors mit dem in den Projekteinstellungen erweiterten Abschnitt „Beschreibung“.](images/unreal-publishing-img-01.png)

2. Erweitern Sie den Abschnitt **HoloLens** der Projekteinstellungen, und aktualisieren Sie die Verpackungsressourcen.  Diese Ressourcennamen werden auf der Store-Seite der Anwendung angezeigt:

![Screenshot des Unreal-Editors mit dem in den Projekteinstellungen erweiterten Abschnitt „Verpacken“.](images/unreal-publishing-img-02.png)

3. Erweitern Sie den Abschnitt **Bilder**, und aktualisieren Sie die standardmäßigen Store-Bilder mit Texturen, die die Store-App darstellen.  Aktivieren Sie optional das Kontrollkästchen **3D-Logo**, um eine GLB-Datei hochzuladen, die beim Starten der Anwendung als 3D-Live Cube verwendet werden soll:

![Screenshot des Unreal-Editors mit dem in den Projekteinstellungen erweiterten Abschnitt „Bilder“.](images/unreal-publishing-img-03.png)

4. Wählen Sie zuletzt **Neu generieren** aus, um ein Signaturzertifikat aus dem Projektnamen und dem Distinguished Name des Unternehmens zu generieren.  
    * Legen Sie eine **Kachel-Hintergrundfarbe** fest, die anstelle von transparenten Pixeln in den Store-Bildern angezeigt wird.
    * Erweitern Sie die Dropdownliste, und aktivieren Sie **Windows Store-Umgebung für den Einzelhandel verwenden**, damit die Ausführung auf im Einzelhandel gesperrten, nicht für Entwicklung entsperrten Geräten, erfolgen kann.

![Screenshot des Unreal-Editors mit dem in den Projekteinstellungen erweiterten Abschnitt „Zertifikatgenerierung“.](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a>Optionaler App-Installer

Eine App-Installer-Datei kann aus **Projekteinstellungen > HoloLens** erstellt und dann zum Verteilen der Anwendung außerhalb des Stores verwendet werden.  Aktivieren Sie das Kontrollkästchen **App-Installer erstellen**, und legen Sie eine URL oder einen Netzwerkpfad fest, wo Sie das appxbundle des Spiels speichern möchten.  

![Screenshot des Unreal-Editors mit dem in den Projekteinstellungen erweiterten Abschnitt „App-Installer“.](images/unreal-publishing-img-05.png)

Wenn die App verpackt wird, werden sowohl „appxbundle“ als auch „appinstaller“ generiert.  Laden Sie das appxbundle in die Installations-URL hoch, und starten Sie dann appinstaller, um die App von dem Netzwerkspeicherort aus zu installieren.

## <a name="windows-app-certification-kit"></a>Zertifizierungskit für Windows-Apps

Der Lieferumfang des Windows 10 SDKs umfasst das Zertifizierungskit für Windows-Apps (WACK), um häufige Probleme zu überprüfen, die das Hochladen eines Pakets in den Store beeinträchtigen könnten.  Sie finden das WACK im Verzeichnis für Windows-Kits, in der Regel unter folgendem Pfad: 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. Nachdem Ihre appx-Datei für die Veröffentlichung gepackt wurde, führen Sie **appcertui.exe** aus, und befolgen Sie die Anweisungen zum Überprüfen der appx:

![Screenshot der App, die zur Validierung im Zertifizierungskit für Windows-Apps ausgewählt wird.](images/unreal-publishing-img-06.png)

2. Wählen Sie **Store-App überprüfen** aus:

![Screenshot der Überprüfungsauswahl im Zertifizierungskit für Windows-Apps.](images/unreal-publishing-img-07.png)

3. Suchen Sie im oberen Abschnitt nach der appx, und wählen Sie **Weiter** aus:

![Screenshot der Testauswahl im Zertifizierungskit für Windows-Apps.](images/unreal-publishing-img-08.png)

4. Wählen Sie **Weiter** aus, um die Tests auszuführen und einen Bericht zu erstellen:
    * Alle verfügbaren Tests, die auf dem Host-PC ausgeführt werden können, sind standardmäßig aktiviert.

![Screenshot des Überprüfungsstatus der App im Zertifizierungskit für Windows-Apps.](images/unreal-publishing-img-09.png)

5. Warten Sie, bis die Tests abgeschlossen sind. Sobald der Vorgang abgeschlossen ist, wird im letzten Fenster ein „Bestanden“- oder „Fehler“-Ergebnis angezeigt, das im gespeicherten Bericht überprüft werden kann.

![Screenshot der Ergebnisse des Abschlussberichts im Zertifizierungskit für Windows-Apps.](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a>Bekannter WACK-Fehler bei Version 4.25

Das Windows Mixed Reality-Plug-In für Unreal 4.25 besteht das WACK nicht, weil einige x64-Binärdateien beim Verpacken für HoloLens eingeschlossen werden. Der Fehler sieht wie folgt aus:

![Screenshot eines fehlgeschlagenen Ergebnisses wegen Binary Analyzer und unterstützter APIs aus dem Zertifizierungskit für Windows-Apps.](images/unreal-publishing-img-11.png)

So beheben Sie das Problem:
1. Navigieren Sie zum Stamm der Unreal-Installation oder des Quellverzeichnisses, indem Sie ein Unreal-Projekt öffnen und in der Taskleiste mit der rechten Maustaste auf das Unreal-Symbol klicken.
2. Klicken Sie mit der rechten Maustaste auf „UE4Editor“, wählen Sie „Eigenschaften“ aus, und navigieren Sie zum Pfad im Eintrag **Speicherort**:

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. Ändern Sie in **WindowsMixedRealityHMD.Build.cs** **Zeile 32** von:

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

in:

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. Schließen Sie Unreal, öffnen Sie das Projekt erneut, und verpacken Sie es erneut für HoloLens.  Führen Sie WACK erneut aus, und der Fehler sollte nicht mehr angezeigt werden. 

## <a name="see-also"></a>Siehe auch

* [Senden einer App an den Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Zertifizierungskit für Windows-Apps](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [Manuelles Erstellen einer App-Installer-Datei](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)