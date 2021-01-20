---
title: App-Modell
description: Windows Mixed Reality verwendet das vom universelle Windows-Plattform bereitgestellte App-Modell, ein Modell und eine Umgebung für moderne Windows-apps.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, App-Modell, Lebenszyklus, aussetzen, fortsetzen, Kachel, Sichten, Verträge, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 941c0f3f81596e8465157121462b4150cefd8ac2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583214"
---
# <a name="app-model"></a>App-Modell

Windows Mixed Reality verwendet das vom [universelle Windows-Plattform](/windows/uwp/get-started/) (UWP) bereitgestellte App-Modell, das ein Modell und eine Umgebung für moderne Windows-Apps ist. Das UWP-App-Modell definiert, wie apps sicher installiert, aktualisiert, versioniert und vollständig entfernt werden. Außerdem wird der Lebenszyklus der Anwendung gesteuert, wie apps ausgeführt, in den Standbymodus versetzt und angehalten werden, und wie Sie den Zustand beibehalten können. Schließlich deckt das App-Modell die Integration und Interaktion mit dem Betriebssystem, Dateien und anderen apps ab.

![2D-apps, die in der Windows Mixed Reality-Startseite in einem Frühstücksbereich angeordnet sind](images/20160112-055908-hololens-500px.jpg)<br>
*Apps mit einer 2D-Ansicht, die in der Windows Mixed Reality-Startseite angeordnet ist*

## <a name="app-lifecycle"></a>App-Lebenszyklus

Der Lebenszyklus einer Mixed Reality-App umfasst standardmäßige App-Konzepte wie z. b. Platzierung, Start, Beendigung und Entfernung.

### <a name="placement-is-launch"></a>Platzierung ist Start

Jede APP startet in gemischter Realität, indem eine APP-Kachel (nur eine [sekundäre Windows-Kachel](/uwp/api/Windows.UI.StartScreen.SecondaryTile)) in der [Windows Mixed Reality-Startseite](../discover/navigating-the-windows-mixed-reality-home.md)platziert wird. Diese APP-Kacheln werden bei der Platzierung mit dem Ausführen der APP gestartet. Diese APP-Kacheln bleiben erhalten und bleiben an der Position, an der Sie sich befinden, und fungieren wie Launcher, wenn Sie zur APP zurückkehren möchten.

![Platzierung stellt eine sekundäre Kachel weltweit](images/slide1-600px.png)<br>
*Platzierung stellt eine sekundäre Kachel weltweit*

Sobald die Platzierung abgeschlossen ist (es sei denn, die Platzierung wurde von einer [App zum](app-model.md#protocols) Starten der APP gestartet), wird die APP gestartet. Windows Mixed Reality kann eine begrenzte Anzahl von apps gleichzeitig ausführen. Sobald Sie eine APP platzieren und starten, können andere aktive apps angehalten werden. Angehaltene apps hinterlassen einen Screenshot des letzten Zustands der APP auf der APP-Kachel, wo Sie sie platziert haben. Weitere Informationen zur Behandlung von Fortsetzung und anderen Lebenszyklus Ereignissen finden Sie unter [Windows 10 UWP-App-Lebenszyklus](/windows/uwp/launch-resume/app-lifecycle).

![Nach dem Platzieren einer Kachel wird die Ausführung des ](images/slide2-500px.png) ![ Status Diagramms für die APP gestartet, angehalten oder wird nicht ausgeführt.](images/ic576232-500px.png)<br>
*Left: nach dem Platzieren einer Kachel wird die Ausführung der APP gestartet. Right: Status Diagramm für die Ausführung, angehaltene oder nicht laufende app.*

### <a name="remove-is-closeterminate-process"></a>Entfernen des Vorgangs zum Schließen/beenden

Wenn Sie eine platzierte App-Kachel aus der Welt entfernen, werden die zugrunde liegenden Prozesse geschlossen. Dies kann hilfreich sein, um sicherzustellen, dass Ihre APP beendet oder eine problematische APP neu gestartet wird.

### <a name="app-suspensiontermination"></a>App-Aussetzung/Beendigung

In der [Windows Mixed Reality-Startseite](../discover/navigating-the-windows-mixed-reality-home.md)kann der Benutzer mehrere Einstiegspunkte für eine APP erstellen, indem er die APP über das Startmenü startet und die APP-Kachel auf der Welt platziert. Jede APP-Kachel verhält sich als ein anderer Einstiegspunkt und verfügt über eine separate Kachel Instanz im System. Eine Abfrage für [secondarytile. findallasync](/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) führt zu einer **secondarytile** für jede app-Instanz.

Wenn eine UWP-App angehalten wird, wird ein Screenshot mit dem aktuellen Status erstellt.

![Screenshots werden für angehaltene apps angezeigt.](images/slide9-800px.png)<br>
*Screenshots werden für angehaltene apps angezeigt.*

Ein wichtiger Unterschied von anderen Windows 10-Shells ist, wie die APP über das [coreapplication. resuming](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) -Ereignis und das [corewindow. aktivierte](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) -Ereignis über die Aktivierung einer app-Instanz informiert wird.

|  Szenario |  Wird fortgesetzt  |  Aktiviert | 
|----------|----------|----------|
|  Starten einer neuen Instanz der APP über das Startmenü  |   |  **Aktiviert** mit einer neuen [tileid](/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Starten Sie eine zweite Instanz der APP über das Startmenü.  |   |  **Aktiviert** mit einer neuen **tileid** | 
|  Wählen Sie die Instanz der APP aus, die zurzeit nicht aktiv ist.  |   |  **Aktiviert** mit der **tileid** , die der Instanz zugeordnet ist. | 
|  Wählen Sie eine andere App aus, und wählen Sie die zuvor aktive Instanz aus.  |  Fort **setzen ausgelöst**  |  | 
|  Wählen Sie eine andere App aus, und wählen Sie die Instanz aus, die zuvor inaktiv war  |  Fort **setzen ausgelöst**  |  Wird dann mit der **tileid** **aktiviert** , die der Instanz zugeordnet ist. | 

### <a name="extended-execution"></a>Erweiterte Ausführung

Manchmal muss Ihre APP weiterhin im Hintergrund arbeiten oder Audioinhalte abspielen. [Hintergrundaufgaben](/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) sind auf hololens verfügbar.

![Apps können im Hintergrund ausgeführt werden.](images/slide10-800px.png)<br>
*Apps können im Hintergrund ausgeführt werden.*

## <a name="app-views"></a>App-Ansichten

Wenn Ihre App aktiviert ist, können Sie auswählen, welche Art von Ansicht angezeigt werden soll. Für die **coreapplication** einer APP gibt es immer eine primäre [App-Ansicht](/uwp/api/Windows.UI.ViewManagement.ApplicationView) und eine beliebige Anzahl weiterer App-Ansichten, die Sie erstellen möchten. Auf dem Desktop können Sie sich eine App-Ansicht als Fenster vorstellen. Unsere Mixed Reality-App-Vorlagen erstellen ein Unity-Projekt, in dem die primäre App-Ansicht [immersiv](app-views.md)ist. 

Ihre APP kann eine zusätzliche 2D-App-Ansicht mithilfe von Technologie wie XAML erstellen, um Windows 10-Funktionen wie z.b. in-App-Käufe zu verwenden. Wenn Ihre APP als UWP-App für andere Windows 10-Geräte gestartet wurde, ist Ihre primäre Ansicht 2D. Sie können sich jedoch in gemischter Realität "anblenden", indem Sie eine weitere App-Ansicht hinzufügen, die sich in der Praxis auf eine Art zeigt. Stellen Sie sich vor, Sie möchten eine Foto-Viewer-app in XAML entwickeln, in der die Schaltfläche "Bild-Viewer" in eine immersive App-Ansicht gewechselt wird, die Fotos von der APP

![Die laufende App kann eine 2D-Ansicht oder eine immersive Ansicht haben.](images/slide3-800px.png)<br>
*Die laufende App kann eine 2D-Ansicht oder eine immersive Ansicht haben.*

### <a name="creating-an-immersive-view"></a>Erstellen einer immersiven Ansicht

Mixed Reality-Apps erstellen eine immersive Ansicht, die mit dem [holographicspace](/uwp/api/windows.graphics.holographic.holographicspace) -Typ erreicht wird.

Eine APP, die rein immersiv ist, sollte beim Start immer eine immersive Ansicht erstellen, auch wenn Sie vom Desktop gestartet wird. Immersive Sichten werden immer im Headset angezeigt, unabhängig davon, wo Sie von erstellt wurden. Wenn Sie eine immersive Ansicht aktivieren, wird das Mixed Reality-Portal angezeigt, und der Benutzer wird aufgefordert, das Headset zu platzieren.

Eine APP, die mit einer 2D-Ansicht auf dem Desktop Monitor beginnt, kann eine sekundäre immersive Ansicht erstellen, um Inhalte im Headset anzuzeigen. Ein Beispiel hierfür ist ein 2D-Edge-Fenster auf dem Bildschirm, in dem ein 360-Grad-Video im Headset angezeigt wird.

![Apps, die in der immersiven Ansicht ausgeführt werden, sind das einzige sichtbare](images/slide4-800px.png)<br>
*Eine APP, die in einer immersiven Ansicht ausgeführt wird, ist die einzige Sichtbarkeit.*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>2D-Ansicht in der Windows Mixed Reality-Startseite

Alles andere als eine immersive Ansicht wird als 2D-Ansicht in ihrer Welt gerendert.

Eine APP kann über 2D-Ansichten sowohl auf dem Desktop Monitor als auch im Headset verfügen. Eine neue 2D-Ansicht wird in derselben Shell wie die Ansicht platziert, von der Sie erstellt wurde, entweder auf dem Monitor oder im Headset. Es ist derzeit nicht möglich, dass eine APP oder ein Benutzer eine 2D-Ansicht zwischen der Mixed Reality-Startseite und dem Monitor verschiebt.

![Apps, die in der 2D-Ansicht ausgeführt werden, teilen den Raum in der gemischten Welt mit anderen apps.](images/slide5-800px.png)<br>
*Apps, die in einer 2D-Ansicht ausgeführt werden, teilen den Speicherplatz mit anderen apps*

### <a name="placement-of-additional-app-tiles"></a>Platzierung zusätzlicher App-Kacheln

Mit den [sekundären Kachel-APIs](/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)können Sie beliebig viele apps mit einer 2D-Ansicht in ihrer Welt platzieren. Diese "fixierten" Kacheln werden als Begrüßungs Bildschirme angezeigt, die Benutzer platzieren müssen, und können Sie später verwenden, um Ihre APP zu starten. Windows Mixed Reality unterstützt derzeit nicht das Rendern von 2D-Kachel Inhalten als Live-Kacheln.

![Apps können über mehrere Platzierungs Plätze mit sekundären Kacheln verfügen](images/slide6-800px.png)<br>
*Apps können über mehrere Platzierungs Plätze mit sekundären Kacheln verfügen*

### <a name="switching-views"></a>Wechseln von Ansichten

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Wechseln von der 2D-XAML-Ansicht zur immersiven Ansicht

Wenn die APP XAML verwendet, steuert die XAML- [iframeworkviewsource](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) die erste Ansicht der app. Die APP muss vor dem Aktivieren von **corewindow** zur immersiven Ansicht gewechselt werden, um sicherzustellen, dass die APP direkt im immersiven Verfahren gestartet wird.

Verwenden Sie [coreapplication. kreatenewview](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) und [applicationviewswitcher. switchasync](/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) , um die aktive Ansicht zu erstellen.

> [!NOTE]
>* Geben Sie das [applicationviewswitchingoptions. konsolidateviews](/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) -Flag nicht an **switchasync** an, wenn Sie von der XAML-Ansicht zur immersiven Ansicht wechseln, oder wenn der Slate, der die APP gestartet hat, von der Welt entfernt wird.
>* **Switchasync** sollte mithilfe des [Dispatchers](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) aufgerufen werden, der der Ansicht zugeordnet ist, in die Sie wechseln.
>* Wenn Sie eine virtuelle Tastatur starten oder eine andere APP aktivieren möchten, müssen Sie in der XAML-Ansicht zurück **switchasync** ausführen.

![Apps können zwischen 2D-Ansichten und immersiven Ansichten wechseln ](images/slide7-600px.png) ![ , wenn eine app in eine immersive Ansicht wechselt, die gemischte Welt und andere apps verschwinden.](images/slide8-600px.png)<br>
*Left: Apps können zwischen der 2D-Ansicht und der immersiven Ansicht wechseln. Right: Wenn eine app in eine immersive Ansicht wechselt, werden die Windows Mixed Reality-Startseite und andere apps nicht mehr angezeigt.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Wechseln von der immersiven Ansicht zurück zu einer XAML-Ansicht der Tastatur

Ein häufiger Grund für den Wechsel zwischen Sichten besteht darin, eine Tastatur in einer Mixed Reality-App anzuzeigen. Die Shell kann die System Tastatur nur anzeigen, wenn die APP eine 2D-Ansicht anzeigt. Wenn die APP Texteingaben erhalten muss, kann Sie eine benutzerdefinierte XAML-Ansicht mit einem Texteingabefeld bereitstellen, zu dieser wechseln und dann nach Abschluss der Eingabe wieder zurück wechseln.

Wie im vorherigen Abschnitt können Sie " **applicationviewswitcher. switchasync** " verwenden, um von ihrer immersiven Ansicht zurück zu einer XAML-Ansicht zu wechseln.

## <a name="app-size"></a>App-Größe

2D-App-Ansichten werden immer in einem fixierten virtuellen Slate-Element angezeigt. Dadurch wird in allen 2D-Ansichten genau dieselbe Menge an Inhalten angezeigt. Im folgenden finden Sie weitere Details zur Größe der 2D-Ansicht Ihrer APP:
* Das Seitenverhältnis der APP wird bei der Größenänderung beibehalten.
* APP [-Auflösung und Skalierungsfaktor](../develop/porting-apps/building-2d-apps.md#2d-app-view-resolution-and-scale-factor) werden durch die Größenänderung nicht geändert.
* Apps können Ihre tatsächliche Größe weltweit nicht Abfragen.

![2D-apps werden mit fester Fenstergröße angezeigt.](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Apps mit einer 2D-Ansicht werden mit fester Fenstergröße angezeigt*

## <a name="app-tiles"></a>App-Kacheln

Das Startmenü verwendet die standardmäßige kleine Kachel und die mittlere Kachel für Pins und die Liste **alle apps** in gemischter Realität. 

![Das Startmenü für Windows Mixed Reality](images/start-500px.png)<br>
*Das Startmenü für Windows Mixed Reality*

## <a name="app-to-app-interactions"></a>APP-zu-app-Interaktionen

Beim Erstellen von apps haben Sie Zugriff auf die für Windows 10 verfügbaren leistungsfähigen APP-zu-app-Kommunikationsmechanismen. Viele der neuen Protokoll-APIs und Datei Registrierungen funktionieren perfekt auf hololens, um das Starten und die Kommunikation der APP zu ermöglichen. 

Bei Desktop-Headsets kann die APP, die einer bestimmten Dateierweiterung oder einem Protokoll zugeordnet ist, eine Win32-APP sein, die nur auf dem Desktop Monitor oder dem Desktop-Slate angezeigt werden kann.

### <a name="protocols"></a>Protokolle

Hololens unterstützt das Starten der APP-App über das [Windows.System. ](/uwp/api/Windows.System.Launcher)Start Programm-APIs.

Beim Starten einer anderen Anwendung müssen einige Punkte berücksichtigt werden:

* Beim Ausführen eines nicht modalen Starts, z. b. [launchuriasync](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), muss der Benutzer die APP platzieren, bevor er mit der Anwendung interagiert.

* Wenn Sie einen modalen Start durchführen, z. b. über [launchuriforresultasync](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), wird die modale App oberhalb des Fensters platziert.

* Windows Mixed Reality kann Anwendungen nicht auf exklusive Ansichten überlagern. Um die gestartete App anzuzeigen, führt Windows den Benutzer zur Anzeige der Anwendung zurück.

### <a name="file-pickers"></a>Datei-Picker

Hololens unterstützt sowohl [fileopenpicker](/uwp/api/Windows.Storage.Pickers.FileOpenPicker) -als auch [filesavepicker](/uwp/api/Windows.Storage.Pickers.FileSavePicker) -Verträge. Allerdings ist keine app vorinstalliert, mit der die Dateiauswahl Verträge erfüllt werden. Diese apps (z. b. onedrive) können vom Microsoft Store installiert werden.

Wenn Sie mehr als eine Dateiauswahl-App installiert haben, wird Ihnen keine Benutzeroberfläche für die Mehrdeutigkeit angezeigt, mit der Sie auswählen können, welche App gestartet werden soll. Stattdessen wird die erste installierte Dateiauswahl ausgewählt. Beim Speichern einer Datei wird der Dateiname generiert, der den Zeitstempel enthält. Dieses kann vom Benutzer nicht geändert werden.

Standardmäßig werden die folgenden Erweiterungen lokal unterstützt:

|  App  |  Erweiterungen | 
|----------|----------|
|  Fotos  |  BMP, GIF, JPG, PNG, AVI, MOV, MP4, WMV | 
|  Microsoft Edge  |  htm, HTML, PDF, SVG, XML | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>App-Verträge und Windows Mixed Reality-Erweiterungen

App-Verträge und Erweiterungs Punkte ermöglichen es Ihnen, Ihre APP zu registrieren, um tiefere Betriebssystemfunktionen zu nutzen, wie z. b. eine Dateierweiterung oder Hintergrundaufgaben. Dies ist eine Liste der unterstützten und nicht unterstützten Verträge und Erweiterungs Punkte auf hololens.

|  Vertrag oder Erweiterung  |  Unterstützt? | 
|----------|----------|
| [Konto Bild Anbieter (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#account_picture_provider) | Nicht unterstützt | 
| [Alarm](/previous-versions/windows/apps/hh464906(v=win.10)#alarm) | Nicht unterstützt | 
| [App Service](/previous-versions/windows/apps/hh464906(v=win.10)#app_service) | Unterstützt, aber nicht voll funktionsfähig | 
| [Termin Anbieter](/previous-versions/windows/apps/hh464906(v=win.10)#appointmnets_provider) | Nicht unterstützt | 
| [AutoPlay (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#autoplay) | Nicht unterstützt | 
| [Hintergrundaufgaben (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#background_tasts) | Teilweise unterstützt (nicht alle Trigger funktionieren) | 
| [Task aktualisieren (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#update_task) | Unterstützt | 
| [Updater-Vertrag für zwischengespeicherte Dateien](/previous-versions/windows/apps/hh464906(v=win.10)#cached_file_updater) | Unterstützt | 
| [Kameraeinstellungen (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#camera_settings) | Nicht unterstützt | 
| [Dial-Protokoll](/previous-versions/windows/apps/hh464906(v=win.10)#dial_protocol) | Nicht unterstützt | 
| [Datei Aktivierung (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#file_activation) | Unterstützt | 
| [Datei Öffnungs Auswahl-Vertrag](/previous-versions/windows/apps/hh464906(v=win.10)#file_open_picker_contract) | Unterstützt | 
| [Dateispeicher Auswahl-Vertrag](/previous-versions/windows/apps/hh464906(v=win.10)#file_save_picker_contract) | Unterstützt | 
| [Sperrbildschirm](/previous-versions/windows/apps/hh464906(v=win.10)#lock_screen_call) | Nicht unterstützt | 
| [Medienwiedergabe](/previous-versions/windows/apps/hh464906(v=win.10)#media_playback) | Nicht unterstützt | 
| [Wiedergabe für Vertrag](/previous-versions/windows/apps/hh464906(v=win.10)#playto_contract) | Nicht unterstützt | 
| [Vorinstallierter Konfigurations Task](/previous-versions/windows/apps/hh464906(v=win.10)#preinstalled_config_task) | Nicht unterstützt | 
| [3D-Workflow drucken](/previous-versions/windows/apps/hh464906(v=win.10)#print_3d_workflow) | Unterstützt | 
| [Druckaufgaben Einstellungen (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#print_task_settings) | Nicht unterstützt | 
| [URI-Aktivierung (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#protocol_activation) | Unterstützt | 
| [Eingeschränkter Start](/previous-versions/windows/apps/hh464906(v=win.10)#restricted_launch) | Nicht unterstützt | 
| [Such Vertrag](/previous-versions/windows/apps/hh464906(v=win.10)#search_contract) | Nicht unterstützt | 
| [Einstellungs Vertrag](/previous-versions/windows/apps/hh464906(v=win.10)#settings_contract) | Nicht unterstützt | 
| [Freigabe Vertrag](/previous-versions/windows/apps/hh464906(v=win.10)#share_contract) | Nicht unterstützt | 
| [SSL/Zertifikate (Erweiterung)](/previous-versions/windows/apps/hh464906(v=win.10)#ssl_certificates) | Unterstützt | 
| [Webkonto Anbieter](/previous-versions/windows/apps/hh464906(v=win.10)#web_account_provider) | Unterstützt | 

## <a name="app-file-storage"></a>App-Dateispeicher

Der gesamte Speicher erfolgt über den [Windows. Storage-Namespace](/uwp/api/Windows.Storage). Hololens unterstützt keine Synchronisierung/Roaming von App Storage. Weitere Informationen finden Sie in der folgenden Dokumentation:

* [Dateien, Ordner und Bibliotheken](/windows/uwp/files/index)
* [Speichern und Abrufen von Einstellungen und anderen App-Daten](/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Bekannte Ordner

Ausführliche Informationen zu UWP-apps finden Sie unter [KnownFolders](/uwp/api/Windows.Storage.KnownFolders) .

<table>
<tr>
<th> Eigenschaft</th><th> Unterstützt auf hololens</th><th> Unterstützt auf immersiven Headsets</th><th> BESCHREIBUNG</th>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">Apperfassungen</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Ordner App-Erfassungen ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">Cameraroll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Ordner für die Kamera Registrierung ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">Documentslibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Dokumentbibliothek ab. Die Bibliothek "Dokumente" ist nicht für die allgemeine Verwendung vorgesehen.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Musikbibliothek ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den 3D-Ordner der Objekte ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">Pictureslibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Bilderbibliothek ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Wiedergabelisten</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Wiedergabelisten Ordner ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">Savedpictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft den Ordner "gespeicherte Bilder" ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">Videoslibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Ruft die Video Bibliothek ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">Heimnetzgruppe</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den HomeGroup-Ordner ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">Mediaserverdevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den Ordner von Media Server (DLNA)-Geräten ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">Recordedcalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den Ordner "aufgezeichnete Aufrufe" ab.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Ruft den Ordner für Wechsel Geräte ab.</td>
</tr>
</table>

## <a name="app-package"></a>App-Paket

Mit Windows 10 richten Sie nicht mehr ein Betriebssystem ein, sondern verwenden [Ihre APP stattdessen für eine oder mehrere Gerätefamilien](/windows/uwp/get-started/universal-application-platform-guide#device-families). Eine Gerätefamilie identifiziert die APIs, Systemmerkmale und Verhaltensweisen, die Sie auf allen Geräten innerhalb der Gerätefamilie erwarten können. Außerdem wird die Gruppe von Geräten bestimmt, auf denen Ihre APP aus dem [Microsoft Store](../distribute/submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)installiert werden kann.

* Wenn Sie sowohl Desktop-Headsets als auch hololens als Ziel haben, richten Sie Ihre APP auf die Windows-Anwendung **Universelle** Gerätefamilie.
* Um nur Desktop-Headsets als Ziel zu erhalten, richten Sie Ihre APP auf die **Windows. Desktop-** Gerätefamilie aus.
* Um nur hololens als Ziel zu erreichen, richten Sie Ihre APP auf die **Windows. Holographic** -Gerätefamilie aus.

## <a name="see-also"></a>Weitere Informationen

* [App-Ansichten](app-views.md)
* [Aktualisieren von 2D-UWP-Apps für Mixed Reality](../develop/porting-apps/building-2d-apps.md)
* [Entwurfsanleitung für 3D-App-Startprogramm](../distribute/3d-app-launcher-design-guidance.md)
* [Implementieren von 3D-App-Launchern](../distribute/implementing-3d-app-launchers.md)