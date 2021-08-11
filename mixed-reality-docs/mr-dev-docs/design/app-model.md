---
title: App-Modell
description: Windows Mixed Reality verwendet das app-Modell, das von der universellen Windows-Plattform bereitgestellt wird, ein Modell und eine Umgebung für moderne Windows Apps.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, App-Modell, Lebenszyklus, Aussetzen, Fortsetzen, Kachel, Ansichten, Verträge, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5f15f0a2516a21cd6432e7f09df7950f8d832acc77ac77056f5bf1382500024e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221936"
---
# <a name="app-model"></a>App-Modell

Windows Mixed Reality verwendet das App-Modell, das von der [universellen Windows-Plattform](/windows/uwp/get-started/) (UWP) bereitgestellt wird. Dabei handelt es sich um ein Modell und eine Umgebung für moderne Windows Apps. Das UWP-App-Modell definiert, wie Apps sicher installiert, aktualisiert, versioniert und vollständig entfernt werden. Außerdem wird der Anwendungslebenszyklus – Ausführung, Ruhezustand und Beenden von Apps – und die Art und Weise, wie sie den Zustand beibehalten können, bestimmt. Schließlich behandelt das App-Modell die Integration und Interaktion mit dem Betriebssystem, Dateien und anderen Apps.

![2D-Apps, die im Windows Mixed Reality in einem Essensbereich angeordnet sind](images/20160112-055908-hololens-500px.jpg)<br>
*Apps mit einer 2D-Ansicht, die in der Startseite Windows Mixed Reality ist*

## <a name="app-lifecycle"></a>App-Lebenszyklus

Der Lebenszyklus einer Mixed Reality-App umfasst Standardmäßige App-Konzepte wie Platzierung, Start, Beendigung und Entfernung.

### <a name="placement-is-launch"></a>Platzierung wird gestartet

Jede App beginnt in Mixed Reality, indem sie eine App-Kachel (nur [Windows sekundäre](/uwp/api/Windows.UI.StartScreen.SecondaryTile)Kachel) im Windows Mixed Reality [platzieren.](../discover/navigating-the-windows-mixed-reality-home.md) Diese App-Kacheln beginnen bei der Platzierung mit der Ausführung der App. Diese App-Kacheln bleiben an ihrem platzierten Speicherort erhalten, und sie agieren immer dann wie Startatoren, wenn Sie zur App zurückkommen möchten.

![Platzierung setzt eine sekundäre Kachel auf die Welt](images/slide1-600px.png)<br>
*Platzierung setzt eine sekundäre Kachel auf die Welt*

Sobald die Platzierung abgeschlossen ist (es sei [](app-model.md#protocols) denn, die Platzierung wurde von einer App zum Starten der App gestartet), beginnt der Start der App. Windows Mixed Reality können eine begrenzte Anzahl von Apps gleichzeitig ausführen. Sobald Sie eine App platzieren und starten, werden andere aktive Apps möglicherweise angehalten. Angehaltene Apps hinterlassen einen Screenshot des letzten Zustands der App auf ihrer App-Kachel, unabhängig davon, wo Sie sie platziert haben. Weitere Informationen zur Behandlung von Lebensläufen und anderen Lebenszyklusereignissen finden Sie unter Windows 10 [UWP-App-Lebenszyklus.](/windows/uwp/launch-resume/app-lifecycle)

![Nach dem Platzieren einer Kachel startet die App die Ausführung des Statusdiagramms für die ](images/slide2-500px.png) ![ ausgeführte, angehaltene oder nicht ausgeführte App.](images/ic576232-500px.png)<br>
*Links: Nach dem Platzieren einer Kachel wird die App gestartet. Rechts: Statusdiagramm für ausgeführte, angehaltene oder nicht ausgeführte Apps.*

### <a name="remove-is-closeterminate-process"></a>Remove is close/terminate process

Wenn Sie eine platzierte App-Kachel aus der Welt entfernen, werden die zugrunde liegenden Prozesse geschlossen. Dies kann hilfreich sein, um sicherzustellen, dass Ihre App beendet wird oder eine problematische App neu gestartet wird.

### <a name="app-suspensiontermination"></a>App-Unterbrechung/-Beendigung

In der [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)kann der Benutzer mehrere Einstiegspunkte für eine App erstellen, indem er Ihre App über den Startmenü startet und die App-Kachel auf der ganzen Welt platziert. Jede App-Kachel verhält sich wie ein anderer Einstiegspunkt und verfügt über eine separate Kachelinstanz im System. Eine Abfrage für [SecondaryTile.FindAllAsync](/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) führt zu einem **SecondaryTile** für jede App-Instanz.

Wenn eine UWP-App angehalten wird, wird ein Screenshot des aktuellen Zustands angezeigt.

![Screenshots für angehaltene Apps](images/slide9-800px.png)<br>
*Screenshots für angehaltene Apps*

Ein wichtiger Unterschied zu anderen Windows 10-Shells ist, wie die App über die [Ereignisse CoreApplication.Resuming](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) und [CoreWindow.Activated](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) über die Aktivierung einer App-Instanz informiert wird.

|  Szenario |  Wird fortgesetzt  |  Aktiviert | 
|----------|----------|----------|
|  Starten Sie eine neue Instanz der App über Startmenü  |   |  **Aktiviert mit** einer neuen [TileId](/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Starten Sie die zweite Instanz der App über Startmenü  |   |  **Aktiviert mit** einer neuen **TileId** | 
|  Wählen Sie die Instanz der App aus, die derzeit nicht aktiv ist.  |   |  **Aktiviert mit** der **TileId,** die der Instanz zugeordnet ist | 
|  Wählen Sie eine andere App und dann die zuvor aktive Instanz aus.  |  **Resuming raised (Fortsetzen ausgelöst)**  |  | 
|  Wählen Sie eine andere App aus, und wählen Sie dann die Instanz aus, die zuvor inaktiv war.  |  **Resuming raised (Fortsetzen ausgelöst)**  |  Anschließend aktiviert **mit der** **TileId,** die der Instanz zugeordnet ist | 

### <a name="extended-execution"></a>Erweiterte Ausführung

Manchmal muss Ihre App weiterhin im Hintergrund arbeiten oder Audio wieder geben. [Hintergrundaufgaben](/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) sind auf HoloLens.

![Apps können im Hintergrund ausgeführt werden.](images/slide10-800px.png)<br>
*Apps können im Hintergrund ausgeführt werden.*

## <a name="app-views"></a>App-Ansichten

Wenn Ihre App aktiviert wird, können Sie auswählen, welche Art von Ansicht Sie anzeigen möchten. Für **CoreApplication** einer App gibt es immer [](/uwp/api/Windows.UI.ViewManagement.ApplicationView) eine primäre App-Ansicht und eine beliebige Anzahl weiterer App-Ansichten, die Sie erstellen möchten. Auf dem Desktop können Sie sich eine App-Ansicht als Fenster einbilden. Unsere Mixed Reality-App-Vorlagen erstellen ein Unity-Projekt, bei dem die primäre App-Ansicht immersive [ist.](app-views.md) 

Ihre App kann eine zusätzliche 2D-App-Ansicht mithilfe von Technologien wie XAML erstellen, um Windows 10 Wie z. B. In-App-Käufe zu verwenden. Wenn Ihre App als UWP-App für andere Windows 10 gestartet wurde, ist Ihre primäre Ansicht 2D. Sie können jedoch in Mixed Reality "auftaufen", indem Sie eine weitere App-Ansicht hinzufügen, die immersiver ist, um eine Umgebung volumetrisch zu zeigen. Imagine Erstellen einer Fotoanzeige-App in XAML, bei der die Bildschirmpräsentationsschaltfläche zu einer immersiven App-Ansicht wechselt, die Fotos aus der App auf der ganzen Welt und oberflächenübergreifend zeigt.

![Die ausgeführte App kann eine 2D-Ansicht oder eine immersive Ansicht haben.](images/slide3-800px.png)<br>
*Die ausgeführte App kann eine 2D-Ansicht oder eine immersive Ansicht haben.*

### <a name="creating-an-immersive-view"></a>Erstellen einer immersiven Ansicht

Mixed Reality-Apps erstellen eine immersive Ansicht, die mit dem [HolographicSpace-Typ erreicht](/uwp/api/windows.graphics.holographic.holographicspace) wird.

Eine rein immersive App sollte beim Start immer eine immersive Ansicht erstellen, auch wenn sie über den Desktop gestartet wird. Immersive Ansichten werden immer im Headset gezeigt, unabhängig davon, wo sie erstellt wurden. Wenn Sie eine immersive Ansicht aktivieren, wird die Mixed Reality-Portal angezeigt, und der Benutzer wird an seiner Headset-Schaltung geanleitungt.

Eine App, die mit einer 2D-Ansicht auf dem Desktopmonitor beginnt, kann eine sekundäre immersive Ansicht erstellen, um Inhalte im Headset anzuzeigen. Ein Beispiel hierfür ist ein 2D Edge-Fenster auf dem Monitor, das ein 360-Grad-Video im Headset zeigt.

![Apps, die in der immersiven Ansicht ausgeführt werden, sind die einzigen sichtbaren Apps.](images/slide4-800px.png)<br>
*Eine App, die in einer immersiven Ansicht ausgeführt wird, ist die einzige sichtbare App.*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>2D-Ansicht in Windows Mixed Reality Startseite

Alles andere als eine immersive Ansicht wird in Ihrer Welt als 2D-Ansicht gerendert.

Eine App kann sowohl auf dem Desktopmonitor als auch im Headset über 2D-Ansichten verfügen. Eine neue 2D-Ansicht wird in derselben Shell platziert wie die Ansicht, die sie erstellt hat, entweder auf dem Monitor oder im Headset. Derzeit ist es für eine App oder einen Benutzer nicht möglich, eine 2D-Ansicht zwischen dem Mixed Reality und dem Monitor zu verschieben.

![Apps, die in der 2D-Ansicht ausgeführt werden, teilen sich den Raum in der gemischten Welt mit anderen Apps.](images/slide5-800px.png)<br>
*Apps, die in einer 2D-Ansicht ausgeführt werden, teilen sich den Bereich mit anderen Apps.*

### <a name="placement-of-additional-app-tiles"></a>Platzierung zusätzlicher App-Kacheln

Sie können mit den APIs für sekundäre Kacheln so viele Apps mit einer 2D-Ansicht in Ihrer Welt platzieren, wie [Sie möchten.](/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles) Diese "angeheftete" Kacheln werden als Begrüßungsbildschirme angezeigt, die Benutzer platzieren müssen und später zum Starten Ihrer App verwenden können. Windows Mixed Reality unterstützt derzeit nicht das Rendern von 2D-Kachelinhalten als Livekacheln.

![Apps können mehrere Platzierungen mithilfe sekundärer Kacheln haben.](images/slide6-800px.png)<br>
*Apps können mehrere Platzierungen mithilfe sekundärer Kacheln haben.*

### <a name="switching-views"></a>Wechseln von Ansichten

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Wechseln von der 2D-XAML-Ansicht zur immersiven Ansicht

Wenn die App XAML verwendet, wird die erste Ansicht der App von XAML [IFrameworkViewSource](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) kontrolliert. Die App muss zur immersiven Ansicht wechseln, bevor **CoreWindow** aktiviert wird, um sicherzustellen, dass die App direkt in der immersiven Umgebung gestartet wird.

Verwenden [Sie CoreApplication.CreateNewView](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) und [ApplicationViewSwitcher.SwitchAsync,](/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) um sie zur aktiven Ansicht zu machen.

> [!NOTE]
>* Geben Sie beim Wechsel von der XAML-Ansicht zur immersiven Ansicht nicht das [Flag ApplicationViewSwasyncOptions.ConsolidateViews](/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) für **SwitchAsync** an, oder die Tafel, die die App gestartet hat, wird aus der Welt entfernt.
>* **SwitchAsync** sollte mithilfe des [Verteilers aufgerufen](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) werden, der der Ansicht zugeordnet ist, in die Sie wechseln.
>* Sie müssen **SwitchAsync** wieder zur XAML-Ansicht wechseln, wenn Sie eine virtuelle Tastatur starten müssen oder eine andere App aktivieren möchten.

![Apps können zwischen 2D-Ansichten und immersiven Ansichten wechseln Wenn eine App in eine immersive Ansicht wechselt, werden die gemischte Welt und ](images/slide7-600px.png) ![ andere Apps nicht mehr angezeigt.](images/slide8-600px.png)<br>
*Links: Apps können zwischen der 2D-Ansicht und der immersiven Ansicht wechseln. Richtig: Wenn eine App in eine immersive Ansicht eingedrappt wird, Windows Mixed Reality zu Hause und andere Apps nicht mehr angezeigt.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Wechseln von der immersiven Ansicht zurück zu einer XAML-Tastaturansicht

Ein häufiger Grund für das Hin- und Herwechseln zwischen Ansichten ist das Anzeigen einer Tastatur in einer Mixed Reality-App. Die Shell kann die Systemtastatur nur anzeigen, wenn die App eine 2D-Ansicht zeigt. Wenn die App Texteingaben erhalten muss, kann sie eine benutzerdefinierte XAML-Ansicht mit einem Texteingabefeld bereitstellen, zu ihr wechseln und dann nach Abschluss der Eingabe wieder zurückwechseln.

Wie im vorherigen Abschnitt können Sie **ApplicationViewSwitcher.SwitchAsync** verwenden, um von Ihrer immersiven Ansicht zurück zu einer XAML-Ansicht zu wechseln.

## <a name="app-size"></a>App-Größe

2D-App-Ansichten werden immer in einer festen virtuellen Tafel angezeigt. Dadurch zeigen alle 2D-Ansichten genau die gleiche Menge an Inhalten an. Im Folgenden finden Sie einige weitere Details zur Größe der 2D-Ansicht Ihrer App:
* Das Seitenverhältnis der App wird beim Ändern der Größe beibehalten.
* [App-Auflösung und Skalierungsfaktor](../develop/porting-apps/building-2d-apps.md#2d-app-view-resolution-and-scale-factor) werden durch Ändern der Größe nicht geändert.
* Apps können ihre tatsächliche Größe weltweit nicht abfragen.

![2D-Apps werden mit festen Fenstergrößen angezeigt.](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Apps mit einer 2D-Ansicht werden mit festen Fenstergrößen angezeigt.*

## <a name="app-tiles"></a>App-Kacheln

Der Startmenü verwendet die kleine Standardkachel und die mittlere Kachel für Stecknadeln und die Liste **Alle Apps** in Mixed Reality. 

![Die Startmenü für Windows Mixed Reality](images/start-500px.png)<br>
*Die Startmenü für Windows Mixed Reality*

## <a name="app-to-app-interactions"></a>Interaktionen zwischen App und App

Wenn Sie Apps erstellen, haben Sie Zugriff auf die umfangreiche App-zu-App-Kommunikationsmechanismen, die auf dem Windows 10. Viele der neuen Protokoll-APIs und Dateiregistrierungen funktionieren perfekt für HoloLens, um app-Start und -Kommunikation zu ermöglichen. 

Bei Desktop-Headsets kann die App, die einer bestimmten Dateierweiterung oder einem bestimmten Protokoll zugeordnet ist, eine Win32-App sein, die nur auf dem Desktopmonitor oder in der Desktop-Slate angezeigt werden kann.

### <a name="protocols"></a>Protokolle

HoloLens unterstützt app-to-app-Start über die [Windows.System.Startprogramm-APIs.](/uwp/api/Windows.System.Launcher)

Beim Starten einer anderen Anwendung sind einige Dinge zu berücksichtigen:

* Bei einem nicht modalen Start, z. B. [LaunchUriAsync,](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)muss der Benutzer die App platzieren, bevor er mit ihr interagiert.

* Bei einem modalen Start, z. B. über [LaunchUriForResultsAsync,](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)wird die modale App über dem Fenster platziert.

* Windows Mixed Reality können Anwendungen nicht über exklusive Ansichten überlagern. Um die gestartete App anzuzeigen, Windows benutzer zurück zur Welt, um die Anwendung anzuzeigen.

### <a name="file-pickers"></a>Dateiauswahl

HoloLens unterstützt sowohl [FileOpenPicker- als](/uwp/api/Windows.Storage.Pickers.FileOpenPicker) [auch FileSavePicker-Verträge.](/uwp/api/Windows.Storage.Pickers.FileSavePicker) Allerdings ist keine App vorinstalliert, die die Dateiauswahlverträge erfüllt. Diese Apps – OneDrive z. B. – können über das -Microsoft Store.

Wenn Sie mehr als eine Dateiauswahl-App installiert haben, wird keine Mehrdeutigenzbenutzeroberfläche für die Auswahl der app angezeigt, die gestartet werden soll. Stattdessen wird die erste installierte Dateiauswahl ausgewählt. Beim Speichern einer Datei wird der Dateiname generiert, der den Zeitstempel enthält. Dieses kann vom Benutzer nicht geändert werden.

Standardmäßig werden die folgenden Erweiterungen lokal unterstützt:

|  App  |  Erweiterungen | 
|----------|----------|
|  Fotos  |  bmp, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>App-Verträge und Windows Mixed Reality Erweiterungen

Mit App-Verträgen und Erweiterungspunkten können Sie Ihre App registrieren, um von tieferen Betriebssystemfeatures wie der Verarbeitung einer Dateierweiterung oder der Verwendung von Hintergrundaufgaben zu profitieren. Dies ist eine Liste der unterstützten und nicht unterstützten Verträge und Erweiterungspunkte auf HoloLens.

|  Vertrag oder Erweiterung  |  Unterstützt? | 
|----------|----------|
| [Kontobildanbieter (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#account_picture_provider) | Nicht unterstützt | 
| [Alarm](/previous-versions/windows/apps/hh464906(v=win.10)#alarm) | Nicht unterstützt | 
| [App Service](/previous-versions/windows/apps/hh464906(v=win.10)#app_service) | Unterstützt, aber nicht voll funktionsfähig | 
| [Terminanbieter](/previous-versions/windows/apps/hh464906(v=win.10)#appointmnets_provider) | Nicht unterstützt | 
| [Automatische Wiedergabe (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#autoplay) | Nicht unterstützt | 
| [Hintergrundaufgaben (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#background_tasts) | Teilweise unterstützt (nicht alle Trigger funktionieren) | 
| [Updateaufgabe (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#update_task) | Unterstützt | 
| [Zwischengespeicherter Dateiupdatevertrag](/previous-versions/windows/apps/hh464906(v=win.10)#cached_file_updater) | Unterstützt | 
| [Kameraeinstellungen (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#camera_settings) | Nicht unterstützt | 
| [Dial-Protokoll](/previous-versions/windows/apps/hh464906(v=win.10)#dial_protocol) | Nicht unterstützt | 
| [Dateiaktivierung (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#file_activation) | Unterstützt | 
| [Vertrag für "Auswahl 'Datei öffnen'"](/previous-versions/windows/apps/hh464906(v=win.10)#file_open_picker_contract) | Unterstützt | 
| [Vertrag für "Auswahl 'Datei speichern'"](/previous-versions/windows/apps/hh464906(v=win.10)#file_save_picker_contract) | Unterstützt | 
| [Aufruf des Sperrbildschirms](/previous-versions/windows/apps/hh464906(v=win.10)#lock_screen_call) | Nicht unterstützt | 
| [Medienwiedergabe](/previous-versions/windows/apps/hh464906(v=win.10)#media_playback) | Nicht unterstützt | 
| [Wiedergeben auf-Vertrag](/previous-versions/windows/apps/hh464906(v=win.10)#playto_contract) | Nicht unterstützt | 
| [Vorinstallierte Konfigurationsaufgabe](/previous-versions/windows/apps/hh464906(v=win.10)#preinstalled_config_task) | Nicht unterstützt | 
| [Print 3D Workflow](/previous-versions/windows/apps/hh464906(v=win.10)#print_3d_workflow) | Unterstützt | 
| [Einstellungen für Druckaufgabe (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#print_task_settings) | Nicht unterstützt | 
| [URI-Aktivierung (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#protocol_activation) | Unterstützt | 
| [Eingeschränkter Start](/previous-versions/windows/apps/hh464906(v=win.10)#restricted_launch) | Nicht unterstützt | 
| [Suchvertrag](/previous-versions/windows/apps/hh464906(v=win.10)#search_contract) | Nicht unterstützt | 
| [Einstellungen-Vertrag](/previous-versions/windows/apps/hh464906(v=win.10)#settings_contract) | Nicht unterstützt | 
| [Freigabevertrag](/previous-versions/windows/apps/hh464906(v=win.10)#share_contract) | Nicht unterstützt | 
| [SSL/Zertifikate (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#ssl_certificates) | Unterstützt | 
| [Webkontoanbieter](/previous-versions/windows/apps/hh464906(v=win.10)#web_account_provider) | Unterstützt | 

## <a name="app-file-storage"></a>App-Dateispeicher

Der gesamte Speicher wird über den [namespace Windows.Storage](/uwp/api/Windows.Storage). HoloLens unterstützt keine App-Speichersynchronisierung/-roaming. Weitere Informationen finden Sie in der folgenden Dokumentation:

* [Dateien, Ordner und Bibliotheken](/windows/uwp/files/index)
* [Speichern und Abrufen von Einstellungen und anderen App-Daten](/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Bekannte Ordner

Ausführliche Informationen zu UWP-Apps finden Sie unter [KnownFolders.](/uwp/api/Windows.Storage.KnownFolders)

<table>
<tr>
<th> Eigenschaft</th><th> Unterstützt auf HoloLens</th><th> Unterstützt auf immersiven Headsets</th><th> Beschreibung</th>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Ordner App Captures ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Ordner Camera Roll ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Dokumentbibliothek ab. Die Dokumentbibliothek ist nicht für die allgemeine Verwendung vorgesehen.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Musik Bibliothek ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Ordner Objects 3D ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Bildbibliothek ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Wiedergabelisten</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Wiedergabelistenordner ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">Savedpictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Ordner Saved Pictures ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosBibliothek</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Videos-Bibliothek ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">Heimnetzgruppe</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den Ordner HomeGroup ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den Ordner der Medienservergeräte (Digital Living Network Alliance (DLNA)) ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den aufgezeichneten Aufrufordner ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den Ordner für Wechselmedien ab.</td>
</tr>
</table>

## <a name="app-package"></a>App-Paket

Mit Windows 10 richten Sie sich nicht mehr auf ein Betriebssystem, sondern [auf eine oder mehrere Gerätefamilien](/windows/uwp/get-started/universal-application-platform-guide#device-families)aus. Eine Gerätefamilie identifiziert die APIs, Systemmerkmale und Verhaltensweisen, die Sie auf allen Geräten innerhalb der Gerätefamilie erwarten können. Außerdem wird bestimmt, auf welchen Geräten Ihre App über die [Microsoft Store](../distribute/submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)installiert werden kann.

* Um sowohl Desktop-Headsets als auch HoloLens als Ziel zu verwenden, richten Sie Ihre App auf die **Windows. Universelle** Gerätefamilie.
* Um nur Desktop-Headsets als Ziel zu verwenden, richten Sie Ihre App auf die **Windows. Desktopgerätefamilie.**
* Um nur HoloLens als Ziel zu verwenden, richten Sie Ihre App an die **Windows. Holographic** device family (Holographic-Gerätefamilie).

## <a name="see-also"></a>Siehe auch

* [App-Ansichten](app-views.md)
* [Aktualisieren von 2D-UWP-Apps für Mixed Reality](../develop/porting-apps/building-2d-apps.md)
* [Entwurfsanleitung für 3D-App-Startprogramm](../distribute/3d-app-launcher-design-guidance.md)
* [Implementieren von 3D-App-Launchern](../distribute/implementing-3d-app-launchers.md)