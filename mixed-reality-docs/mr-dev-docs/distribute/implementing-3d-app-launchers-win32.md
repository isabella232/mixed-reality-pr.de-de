---
title: Implementieren von 3D-App-Startprogrammen (Win32-Apps)
description: Erfahren Sie, wie Sie 3D-App-Start- und Logos für Win32 VR-Apps und -Spiele für die Startmenü-Umgebung erstellen.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Logo, Symbol, Modellierung, Startprogramm, 3D-Startprogramm, Kachel, Livecube, Win32, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Manifest
ms.openlocfilehash: 60eb4f543f287e833033c8e1852e2a85c6040d3c76455aadaca4b37c0a632573
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198766"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementieren von 3D-App-Startprogrammen (Win32-Apps)

> [!NOTE]
> Dieses Feature ist nur für PCs verfügbar, auf denen die neuesten [Windows Insider-Flüge](https://insider.windows.com) (RS5), Build 17704 und neuer, ausgeführt werden.

Das [Windows Mixed Reality ist](../discover/navigating-the-windows-mixed-reality-home.md) der Ausgangspunkt, an dem Benutzer landen, bevor sie Anwendungen starten. Standardmäßig müssen Sie immersive Win32 VR-Apps und -Spiele von außerhalb des Headsets starten und werden nicht in der Liste "Alle Apps" auf dem Windows Mixed Reality Startmenü. Wenn Sie die Anweisungen in diesem Artikel befolgen, um ein 3D-App-Startfeld zu implementieren, kann Ihre immersive Win32 VR-Umgebung über die Windows Mixed Reality Startmenü und die Startumgebung gestartet werden.

Dies gilt nur für immersive Win32 VR-Umgebungen, die außerhalb von Steam verteilt sind. Für VR-Erfahrungen, die über [Steam](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)verteilt werden, haben wir die Windows Mixed Reality für [Die Betaversion von TesterVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) zusammen mit den neuesten Windows Insider RS5-Flügen aktualisiert, sodass die Titel von "Windows Mixed Reality Startmenü" in der Liste "Alle Apps" automatisch mit einem Standardstartprogramm angezeigt werden. Anders ausgedrückt: Die in diesem Artikel beschriebene Methode ist für die Titel von SteamVR nicht erforderlich und wird von der Windows Mixed Reality Für Die Beta-Funktionalität von SteamVR überschrieben.

## <a name="3d-app-launcher-creation-process"></a>Erstellungsprozess für das 3D-App-Startfeld

Es gibt drei Schritte zum Erstellen eines 3D-App-Startfelds:
1. [Entwerfen und Entwerfen](3d-app-launcher-design-guidance.md)
2. [Modellierung und Export](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrieren in Ihre Anwendung (dieser Artikel)

3D-Objekte, die als Starthilfen für Ihre [](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) Anwendung verwendet werden sollen, sollten mithilfe Windows Mixed Reality Richtlinien für die Erstellung von Anwendungen zur Sicherstellung der Kompatibilität verfasst werden. Objekte, die diese Erstellungsspezifikation nicht erfüllen, werden nicht im Windows Mixed Reality gerendert.

## <a name="configuring-the-3d-launcher"></a>Konfigurieren des 3D-Startfelds

Win32-Anwendungen werden in der Liste "Alle Apps" auf dem Windows Mixed Reality Startmenü angezeigt, wenn Sie ein 3D-App-Startfeld für sie erstellen. Erstellen Sie hierzu eine XML-Datei für das [Visual Elements-Manifest,](/previous-versions/windows/apps/dn393983(v=win.10)) die auf die 3D-App Startprogramm, indem Sie die folgenden Schritte ausführen:

1. Erstellen Sie eine **3D-App Startprogramm-Asset-GLB-Datei** (siehe [Modellierung und Export](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Erstellen Sie **[ein Manifest für visuelle Elemente](/previous-versions/windows/apps/dn393983(v=win.10))** für Ihre Anwendung.
    1. Sie können mit dem folgenden [Beispiel beginnen.](#sample-visual-elements-manifest)  Weitere Informationen finden Sie in der vollständigen Dokumentation zum [Visual Elements-Manifest.](/previous-versions/windows/apps/dn393983(v=win.10))
    2. Aktualisieren **Sie Square150x150Logo** und **Square70x70Logo** mit PNG/JPG/GIF für Ihre App.
        * Diese werden für das 2D-Logo der App in der Liste Windows Mixed Reality Alle Apps und für das Startmenü auf dem Desktop verwendet.
        * Der Dateipfad basiert auf dem Ordner, der das Manifest für visuelle Elemente enthält.
        * Sie müssen weiterhin ein Desktopsymbol für das Startmenü für Ihre App über die Standardmechanismen bereitstellen. Dies kann entweder direkt in der ausführbaren Datei oder in der von Ihnen erstellten Verknüpfung enthalten sein. Beispielsweise über IShellLink::SetIconLocation.
        * *Optional:* Sie können die Datei resources.pri verwenden, wenn Sie möchten, dass MRT mehrere Ressourcengrößen für verschiedene Auflösungsskalen und Designs mit hohem Kontrast bereitstellen soll.
    3. Aktualisieren Sie **den MixedRealityModel-Pfad** so, dass er auf den GLB für Ihre 3D-App Startprogramm
    4. Speichern Sie die Datei mit dem gleichen Namen wie die ausführbare Datei mit der Erweiterung ".VisualElementsManifest.xml", und speichern Sie sie im gleichen Verzeichnis. Für die ausführbare Datei "contoso.exe" heißt die zugehörige XML-Datei beispielsweise "contoso.visualelementsmanifest.xml".
3. **Fügen Sie ihrer** Anwendung eine Verknüpfung zum Desktop hinzu, Windows Startmenü zu öffnen. Eine [C++-Beispielimplementierung](#sample-app-launcher-shortcut-creation) finden Sie im folgenden Beispiel. 
    * Erstellen Sie es in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (Computer) oder %APPDATA%\Microsoft\Windows\Start Menu\Programs (Benutzer).
    * Wenn ein Update das Manifest der visuellen Elemente oder die Objekte ändert, auf die es verweist, sollte der Updater oder das Installationsprogramm die Verknüpfung so aktualisieren, dass das Manifest neu erstellt und zwischengespeicherte Objekte aktualisiert werden.
4. *Optional:* Wenn Ihre Desktopverknüpfung nicht direkt auf die EXE-Datei Ihrer Anwendung zeigt (z. B. wenn sie einen benutzerdefinierten Protokollhandler wie "myapp://" aufruft), findet das Startmenü nicht automatisch die VisualElementsManifest.xml-Datei der App. Um dies zu beheben, sollte die Verknüpfung den Dateipfad des Visual Elements-Manifests mit system.AppUserModel.VisualElementsManifestHintPath () angeben. Dies kann in der Verknüpfung mit den gleichen Techniken festgelegt werden wie System.AppUserModel.ID. Sie müssen System.AppUserModel.ID verwenden, aber sie können dies tun, wenn die Verknüpfung mit der expliziten Anwendungsbenutzermodell-ID der Anwendung übereinstimmen soll, wenn eine verwendet wird.  Ein [C++-Beispiel finden](#sample-app-launcher-shortcut-creation) Sie unten im Abschnitt erstellen von Verknüpfungen für das App-Startfeld.

### <a name="sample-visual-elements-manifest"></a>Beispielmanifest für visuelle Elemente

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>Erstellen von Beispielverknüpfungen für das App-Startfeld

Der folgende Beispielcode zeigt, wie Sie eine Verknüpfung in C++ erstellen können, einschließlich des Überschreibens des Pfads zur XML-Datei des Visual Elements-Manifests. Beachten Sie, dass die Außerkraftsetzung nur in Fällen erforderlich ist, in denen ihre Verknüpfung nicht direkt auf die exe-Datei zeigt, die dem Manifest zugeordnet ist (ihre Verknüpfung verwendet z. B. einen benutzerdefinierten Protokollhandler wie "myapp://").

#### <a name="sample-lnk-shortcut-creation-c"></a>Beispiel. Erstellen von LNK-Verknüpfungen (C++)

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>Beispiel. URL-Startfeldverknüpfung 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>Siehe auch

* [Beispiel eines Mixed Reality-Modells,](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) das ein 3D-App-Startfeld enthält.
* [Entwurfsanleitung für 3D-App-Startprogramm](3d-app-launcher-design-guidance.md)
* [Erstellen von 3D-Modellen für die Verwendung im Windows Mixed Reality Home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementieren von 3D-App-Startern (UWP-Apps)](implementing-3d-app-launchers.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)