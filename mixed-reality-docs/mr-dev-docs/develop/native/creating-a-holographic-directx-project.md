---
title: Erstellen eines holographischen DirectX-Projekts
description: Erfahren Sie, wie Sie eine neue holografische DirectX-App basierend auf der Windows Mixed Reality-App-Vorlage erstellen.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, holografische App, neue App, UWP-App, Vorlagen-App, Hologramme, neues Projekt, exemplarische Vorgehensweise, Herunterladen, Beispielcode, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 7de7d73ec1e5fd8abde6d4822c86628e090fdf0cf89769fc9ef21311ff1aff15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200161"
---
# <a name="creating-a-holographic-directx-project"></a>Erstellen eines holographischen DirectX-Projekts

> [!NOTE]
> Dieser Artikel bezieht sich auf die nativen WinRT-Legacy-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API](openxr-getting-started.md)** empfohlen.

Eine holografische App, die Sie für eine HoloLens erstellen, ist eine <a href="/windows/uwp/get-started/universal-application-platform-guide" target="_blank">UWP-App (Universal Windows Platform).</a>  Wenn Sie desktop Windows Mixed Reality Headsets als Ziel verwenden, können Sie eine UWP-App oder eine Win32-App erstellen.

Die Holografische UWP-App-Vorlage DirectX 11 ähnelt der Vorlage der DirectX 11-UWP-App. Die Vorlage enthält eine Programmschleife, eine **DeviceResources-Klasse** zum Verwalten des Direct3D-Geräts und des Direct3D-Kontexts sowie eine vereinfachte Inhaltsrendererklasse. Es verfügt auch über eine <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView,</a>genau wie jede andere UWP-App.

Die Mixed Reality-App verfügt jedoch über einige zusätzliche Funktionen, die in einer typischen Direct3D-UWP-App nicht vorhanden sind. Die Windows Mixed Reality-App-Vorlage kann folgende Möglichkeiten haben:
* Verarbeiten sie Direct3D-Geräteressourcen, die holografischen Kameras zugeordnet sind.
* Abrufen von Kamerarückpuffern aus dem System. Erstellen Sie im Fall von Direct3D12 holografische Backpufferressourcen, und verwalten Sie die Ressourcenlebensdauer.
* Behandeln sie die Eingabe des [Anverweises,](../../design/gaze-and-commit.md) und erkennen Sie eine [Geste.](../../design/gaze-and-commit.md#composite-gestures)
* Wechseln Sie in den Vollbild-Stereorenderingmodus.

## <a name="how-do-i-get-started"></a>Wie fange ich an?

Installieren Sie zunächst [die Tools,](../install-the-tools.md)indem Sie die Anweisungen zum Herunterladen von Visual Studio 2019 und der Windows Mixed Reality-App-Vorlagen befolgen. Die Mixed Reality-App-Vorlagen sind im Visual Studio Marketplace als [Webdownload](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)oder durch Installation als Erweiterung über die Visual Studio-Benutzeroberfläche verfügbar.

Jetzt können Sie Ihre DirectX 11 Windows Mixed Reality-App erstellen! Um den Beispielinhalt zu entfernen, kommentieren Sie die **DRAW_SAMPLE_CONTENT** Präprozessordirektive in *pch.h* aus.

## <a name="creating-a-uwp-project"></a>Erstellen eines UWP-Projekts

Sobald die Tools installiert sind,](.. /install-the-tools.md) können Sie dann ein holografisches DirectX-UWP-Projekt erstellen.

So erstellen Sie ein neues Projekt in Visual Studio 2019:
1. Starten Sie **Visual Studio**.
2. Wählen Sie im **abschnitt Erste Schritte** auf der rechten Seite die Option Neues **Projekt erstellen** aus.
3. Wählen Sie in den Dropdownmenüs im Dialogfeld **Neues Projekt erstellen** die Optionen **C++,** **Windows Mixed Reality** und **UWP** aus.
4. Wählen Sie **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)** aus.
   ![Screenshot der UWP-App-Projektvorlage "Holographic DirectX 11 C++/WinRT" in Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Holographic DirectX 11 C++/WinRT UWP-App-Projektvorlage in Visual Studio 2019*
   >[!IMPORTANT]
   >Stellen Sie sicher, dass der Name der Projektvorlage "(C++/WinRT)" enthält.  Falls nicht, ist eine ältere Version der Holographic-Projektvorlagen installiert.  Um die neuesten Projektvorlagen zu erhalten, [installieren Sie sie](../install-the-tools.md) als Erweiterung für Visual Studio 2019.
5. Wählen Sie **Weiter** aus.
5. Füllen Sie die Textfelder **Project Namen** und **Speicherort** aus, und wählen oder tippen Sie auf **Erstellen.** Das Holographic-App-Projekt wird erstellt.
6. Stellen Sie für entwicklungsziele nur HoloLens 2 sicher, dass **die Zielversion** und **die Mindestversion** auf **Windows 10 Version 1903** festgelegt sind.  Wenn Sie auch HoloLens (1. Generation) oder Desktop-Windows Mixed Reality Headsets als Ziel verwenden, können Sie **die Mindestversion** auf **Windows 10, Version 1809** festlegen. Dies erfordert einige <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">versionsadaptive Überprüfungen</a> im Code, wenn neue Features von HoloLens 2 verwendet werden.
   ![Screenshot der Einstellung Windows 10, Version 1903 als Ziel- und Mindestversion](images/new-uwp-project.png)<br>
   *Festlegen **Windows 10 Version 1903** als Ziel- und Mindestversion*
   >[!IMPORTANT]
   >Wenn **Windows 10, Version 1903,** nicht als Option angezeigt wird, ist nicht das neueste Windows 10 SDK installiert.  Damit diese Option angezeigt wird, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">installieren Sie Version 10.0.18362.0 oder höher des Windows 10 SDK.</a>

So erstellen Sie ein neues Projekt in Visual Studio 2017:
1. Starten Sie **Visual Studio**.
2. Zeigen Sie im Menü **Datei** auf **Neu,** und wählen Sie im Kontextmenü **Project** aus. Das Dialogfeld **Neues Projekt** wird geöffnet.
3. Erweitern Sie auf der linken Seite **Installiert,** und erweitern Sie den **Knoten Visual C++** Sprache.
4. Navigieren Sie zum Knoten **Windows Universal > Holographic,** und wählen Sie **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)** aus.
   ![Screenshot der UWP-App-Projektvorlage "Holographic DirectX 11 C++/WinRT" in Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)<br>
   *Holographic DirectX 11 C++/WinRT UWP-App-Projektvorlage in Visual Studio 2017*
   >[!IMPORTANT]
   >Stellen Sie sicher, dass der Name der Projektvorlage "(C++/WinRT)" enthält.  Falls nicht, ist eine ältere Version der Holographic-Projektvorlagen installiert.  Um die neuesten Projektvorlagen zu erhalten, [installieren Sie sie](../install-the-tools.md) als Erweiterung für Visual Studio 2017.
5. Füllen Sie die Textfelder **Name** und **Speicherort** aus, und wählen oder tippen Sie auf **OK.** Das Holographic-App-Projekt wird erstellt.
6. Stellen Sie für entwicklungsziele nur HoloLens 2 sicher, dass **die Zielversion** und **die Mindestversion** auf **Windows 10 Version 1903** festgelegt sind.  Wenn Sie auch HoloLens (1. Generation) oder Desktop-Windows Mixed Reality Headsets als Ziel verwenden, können Sie **die Mindestversion** auf **Windows 10, Version 1809** festlegen. Dies erfordert einige <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">versionsadaptive Überprüfungen</a> im Code, wenn neue Features von HoloLens 2 verwendet werden.
   ![Screenshot der Einstellung Windows 10, Version 1903 als Ziel- und Mindestversion](images/new-uwp-project.png)<br>
   *Festlegen **Windows 10 Version 1903** als Ziel- und Mindestversion*
   >[!IMPORTANT]
   >Wenn **Windows 10, Version 1903,** nicht als Option angezeigt wird, ist nicht das neueste Windows 10 SDK installiert.  Damit diese Option angezeigt wird, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">installieren Sie Version 10.0.18362.0 oder höher des Windows 10 SDK.</a>

Die Vorlage generiert ein Projekt mit <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT,</a>einer C++17-Sprachprojektion der Windows Runtime-APIs, die jeden standardkonformen C++17-Compiler unterstützt.  Das Projekt zeigt, wie Sie einen weltweit gesperrten Cube erstellen, der 2 Meter vom Benutzer platziert wird. Der Benutzer kann auf den Controller [tippen](../../design/gaze-and-commit.md#composite-gestures) oder eine Schaltfläche drücken, um den Würfel an einer anderen Position zu platzieren, die vom [Anvisierten](../../design/gaze-and-commit.md)des Benutzers angegeben wird. Sie können dieses Projekt ändern, um eine beliebige Mixed Reality-App zu erstellen.

Sie können ein neues Projekt auch mithilfe der **holografischen Visual C#-Projektvorlage** erstellen, die auf SharpDX basiert.  Wenn Ihr holografisches C#-Projekt nicht mit der Windows Holographic-App-Vorlage begonnen hat, müssen Sie die Datei ms.fxcompile.targets aus einem Windows Mixed Reality C#-Vorlagenprojekt kopieren und in die Datei your.csproj importieren, um HLSL-Dateien zu kompilieren, die Sie Ihrem Projekt hinzufügen. Eine Direct3D 12-Vorlage wird auch in der Windows Mixed Reality-App-Vorlagenerweiterung für Visual Studio bereitgestellt.

Unter [Verwenden von Visual Studio zum Bereitstellen und Debuggen](../platform-capabilities-and-apis/using-visual-studio.md) erfahren Sie, wie Sie das Beispiel erstellen und auf Ihrem HoloLens, PC mit angefügtem immersivem Gerät oder einem Emulator bereitstellen.

In den restlichen Anweisungen unten wird davon ausgegangen, dass Sie C++ verwenden, um Ihre App zu erstellen.

### <a name="uwp-app-entry-point"></a>Einstiegspunkt für die UWP-App

Ihre holografische UWP-App beginnt in der **wWinMain-Funktion** in AppView.cpp. Die **wWinMain-Funktion** erstellt die <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> der App und startet die <a href="/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> damit.

Aus **AppView.cpp:**

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

Ab diesem Zeitpunkt verarbeitet die AppView-Klasse die Interaktion mit Windows grundlegenden Eingabeereignissen, CoreWindow-Ereignissen und Messaging usw. Außerdem wird der von Ihrer App verwendete HolographicSpace erstellt.

## <a name="creating-a-win32-project"></a>Erstellen eines Win32-Projekts

Die einfachste Möglichkeit zum Erstellen eines holografischen Win32-Projekts besteht darin, das <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32-Beispiel</a>anzupassen.

Dieses Win32-Beispiel verwendet <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT,</a>eine C++17-Sprachprojektion der Windows Runtime-APIs, die jeden standardkonformen C++17-Compiler unterstützt.  Das Projekt zeigt, wie Sie einen weltweit gesperrten Cube erstellen, der 2 Meter vom Benutzer platziert wird. Der Benutzer kann eine Schaltfläche auf dem Controller drücken, um den Würfel an einer anderen Position zu platzieren, die vom [Anvisierten](../../design/gaze-and-commit.md)des Benutzers angegeben wird. Sie können dieses Projekt ändern, um eine beliebige Mixed Reality-App zu erstellen.

### <a name="win32-app-entry-point"></a>Win32-App-Einstiegspunkt

Ihre holografische Win32-App wird in der **wWinMain-Funktion** in AppMain.cpp gestartet. Die **wWinMain-Funktion** erstellt das HWND der App und startet die Nachrichtenschleife.

Über **AppMain.cpp:**

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

Ab diesem Zeitpunkt verarbeitet die AppMain-Klasse die Interaktion mit grundlegenden Fenstermeldungen usw. Außerdem wird der von Ihrer App verwendete HolographicSpace erstellt.

## <a name="render-holographic-content"></a>Rendern von holografischem Inhalt

Der Ordner **Content** des Projekts enthält Klassen zum Rendern von Hologrammen im [holografischen Raum](getting-a-holographicspace.md). Das Standard hologramm in der Vorlage ist ein rotierender Würfel, der 2 Meter vom Benutzer entfernt platziert wird. Das Zeichnen dieses Cubes wird in **SpinningCubeRenderer.cpp** implementiert, das über die folgenden Schlüsselmethoden verfügt:

|  Methode  |  Erklärung | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Lädt Shader und erstellt das Cubegitternetz. | 
|  `PositionHologram` |  Platziert das Hologramm an der Von der bereitgestellten <a href="/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>angegebenen Position. | 
|  `Update` |  Dreht den Cube und legt die Modellmatrix fest. | 
|  `Render` |  Rendert einen Frame mithilfe der Vertex- und Pixel-Shader. | 

Der **Shader-Unterordner** enthält vier Standardmäßige Shaderimplementierungen:

|  Shader  |  Erläuterung | 
|----------|----------|
|  `GeometryShader.hlsl` |  Ein Pass-Through, bei dem die Geometrie unverändert bleibt. | 
|  `PixelShader.hlsl` |  Durchläuft die Farbdaten. Die Farbdaten werden interpoliert und einem Pixel im Rasterungsschritt zugewiesen. | 
|  `VertexShader.hlsl` |  Einfacher Shader für die Scheitelpunktverarbeitung auf der GPU. | 
|  `VPRTVertexShader.hlsl` |  Einfacher Shader für die Scheitelpunktverarbeitung auf der GPU, die für Windows Mixed Reality-Rendering optimiert ist. | 

`VertexShaderShared.hlsl` enthält gemeinsamen Code, der von `VertexShader.hlsl` und gemeinsam verwendet `VPRTVertexShader.hlsl` wird.

Hinweis: Die Direct3D 12-App-Vorlage enthält auch `ViewInstancingVertexShader.hlsl` . Diese Variante verwendet optionale D3D12-Features, um Stereobilder effizienter zu rendern.

Die Shader werden kompiliert, wenn das Projekt erstellt und in der **SpinningCubeRenderer::CreateDeviceDependentResources-Methode geladen** wird.

## <a name="interact-with-your-holograms"></a>Interagieren mit Hologrammen

Benutzereingaben werden in der **SpatialInputHandler-Klasse** verarbeitet, die eine <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager-Instanz</a> erhält und das <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed-Ereignis abonniert.</a> Dies ermöglicht die Erkennung der Geste zum Tippen in die Luft und anderer räumlicher Eingabeereignisse.

## <a name="update-holographic-content"></a>Aktualisieren von holografischem Inhalt

Ihre Mixed Reality-App wird in einer Spielschleife aktualisiert, die standardmäßig in der **Update-Methode** in implementiert `AppMain.cpp` ist. Die **Update-Methode** aktualisiert Szenenobjekte wie den sich drehenden Würfel und gibt ein <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame-Objekt</a> zurück, das verwendet wird, um aktuelle Ansichts- und Projektionsmatrizen zu erhalten und die Auslagerungskette zu präsentieren.

Die **Render-Methode** in verwendet den HolographicFrame und rendert den aktuellen Frame für jede holografische Kamera entsprechend der aktuellen App und des räumlichen `AppMain.cpp` <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank"></a> Positionierungszustands.

## <a name="notes"></a>Hinweise

Die Windows Mixed Reality-App-Vorlage unterstützt jetzt die Kompilierung mit aktiviertem Spectre-Entschärfungsflag (/Qspectre). Stellen Sie sicher, dass Sie die spectre-entschärften Versionen der Microsoft Visual C++-Laufzeitbibliotheken (MSVC) installieren, bevor Sie eine Konfiguration mit aktivierter Spectre-Entschärfung kompilieren. Um die spectre-entschärften C++-Bibliotheken zu installieren, starten Sie die Visual Studio-Installer und wählen **Ändern aus.** Navigieren Sie **zu Einzelne Komponenten,** und suchen Sie nach "spectre". Aktivieren Sie die Kontrollkästchen für die Zielplattformen und MSVC Version, für die Sie  spectre-entschärften Code kompilieren müssen, und klicken Sie auf Ändern, um die Installation zu starten.

## <a name="see-also"></a>Siehe auch
* [Abrufen eines HolographicSpace-Objekts](getting-a-holographicspace.md)
* <a href="/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Rendern in DirectX](rendering-in-directx.md)
* [Verwenden von Visual Studio zum Bereitstellen und Debuggen](../platform-capabilities-and-apis/using-visual-studio.md)
* [Verwendung des HoloLens-Emulators](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Verwenden von XAML mit holographischen DirectX-Apps](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)