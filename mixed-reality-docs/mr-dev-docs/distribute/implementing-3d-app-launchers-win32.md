---
title: Implementieren von 3D-App-Startprogrammen (Win32-Apps)
description: Erfahren Sie, wie Sie 3D-App-Starter und-Logos für Win32-VR-apps und-Spiele für das Windows Mixed Reality-Startmenü und die Home-Umgebung erstellen.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Logo, Symbol, Modellierung, Start Programm, 3D-Start Programm, Kachel, Live Cube, Win32, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Manifest
ms.openlocfilehash: 5a3e38de54aad1fceb4804003043c87dddab61c4
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757817"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="d4ba7-104">Implementieren von 3D-App-Startprogrammen (Win32-Apps)</span><span class="sxs-lookup"><span data-stu-id="d4ba7-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="d4ba7-105">Diese Funktion ist nur für PCs verfügbar, auf denen die neuesten [Windows-Insider](https://insider.windows.com) -Flüge (RS5), Build 17704 und höher ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="d4ba7-106">Der [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) -Startpunkt ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-106">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="d4ba7-107">Standardmäßig müssen Sie in der Liste "alle apps" im Windows Mixed Reality-Startmenü die immersiven Win32 VR-apps und Spiele starten.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-107">By default, you need to launch immersive Win32 VR apps and games from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="d4ba7-108">Wenn Sie die Anweisungen in diesem Artikel befolgen, um ein 3D-App-Startfeld zu implementieren, können Sie die immersive Win32-VR-Umgebung im Windows Mixed Reality-Startmenü und in der Home-Umgebung starten.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-108">If you follow the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="d4ba7-109">Dies gilt nur für immersive Win32-VR-Erlebnisse, die außerhalb von Steam verteilt sind.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-109">This is only true for immersive Win32 VR experiences distributed outside of Steam.</span></span> <span data-ttu-id="d4ba7-110">Bei der durch die Verwendung von [Steam verteilten](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)VR-Umgebung haben wir [die Windows Mixed Reality für steamvr Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) zusammen mit den neuesten Windows Insider RS5-Flügen aktualisiert, damit die steamvr-Titel im Windows Mixed Reality-Startmenü in der Liste "alle apps" automatisch mithilfe eines Standard Start Programms angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-110">For VR experiences [distributed through Steam](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="d4ba7-111">Anders ausgedrückt: die in diesem Artikel beschriebene Methode ist für die steamvr-Titel unnötig und wird von der Windows Mixed Reality for steamvr Beta-Funktionalität überschrieben.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="d4ba7-112">Erstellung eines 3D-App-Start Programms</span><span class="sxs-lookup"><span data-stu-id="d4ba7-112">3D app launcher creation process</span></span>

<span data-ttu-id="d4ba7-113">Zum Erstellen eines 3D-App-Start Programms sind drei Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="d4ba7-113">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="d4ba7-114">Entwurf und Konzept</span><span class="sxs-lookup"><span data-stu-id="d4ba7-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="d4ba7-115">Modellieren und exportieren</span><span class="sxs-lookup"><span data-stu-id="d4ba7-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="d4ba7-116">Integration in Ihre Anwendung (dieser Artikel)</span><span class="sxs-lookup"><span data-stu-id="d4ba7-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="d4ba7-117">3D-Ressourcen, die als Launcher für Ihre Anwendung verwendet werden sollen, sollten mithilfe der [Windows Mixed Reality Authoring Guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt werden, um die Kompatibilität zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="d4ba7-118">Assets, die diese Erstellungs Spezifikation nicht erfüllen, werden nicht in der Windows Mixed Reality-Startseite gerendert.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-118">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="d4ba7-119">Konfigurieren des 3D-Start Programms</span><span class="sxs-lookup"><span data-stu-id="d4ba7-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="d4ba7-120">Win32-Anwendungen werden in der Liste "alle apps" im Windows Mixed Reality-Startmenü angezeigt, wenn Sie ein 3D-App-Startfeld für Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="d4ba7-121">Erstellen Sie hierzu eine XML- [Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) -XML-Datei, die auf das 3D-App-Startfeld verweist, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="d4ba7-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="d4ba7-122">Erstellen einer Ressource für ein **3D-App-Start** Programm (siehe [modellieren und exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="d4ba7-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="d4ba7-123">Erstellen Sie ein **[visuelles Element Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="d4ba7-124">Sie können mit dem [folgenden Beispiel](#sample-visual-elements-manifest)beginnen.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="d4ba7-125">Weitere Informationen finden Sie in der Dokumentation zum vollständigen [visuellen Element Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) .</span><span class="sxs-lookup"><span data-stu-id="d4ba7-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="d4ba7-126">Aktualisieren Sie **Square150x150Logo** und **Square70x70Logo** mit einem PNG/JPG/GIF für Ihre APP.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="d4ba7-127">Diese werden für das 2D-Logo der app in der Windows Mixed Reality all apps-Liste und für das Startmenü auf dem Desktop verwendet.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="d4ba7-128">Der Dateipfad basiert auf dem Ordner, der das Manifest der visuellen Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-128">The file path is based on the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="d4ba7-129">Sie müssen immer noch ein Desktop-Start Menü Symbol für Ihre APP über die Standardmechanismen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="d4ba7-130">Dies kann entweder direkt in der ausführbaren Datei oder in der von Ihnen erstellten Verknüpfung erfolgen.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-130">This can either be directly in the executable or in the shortcut you create.</span></span> <span data-ttu-id="d4ba7-131">Beispielsweise über IShellLink:: Abort.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-131">For example, via IShellLink::SetIconLocation.</span></span>
        * <span data-ttu-id="d4ba7-132">*Optional:* Sie können eine "Resources. pri"-Datei verwenden, wenn Sie möchten, dass für MRT mehrere assetgrößen für verschiedene Auflösungs Skalen und Designs mit hohem Kontrast bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-132">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="d4ba7-133">Aktualisieren Sie den **Pfad von mixedrealitymodel** , sodass er auf den GLB für das 3D-App-Startfeld verweist.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-133">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="d4ba7-134">Speichern Sie die Datei mit dem gleichen Namen wie die ausführbare Datei mit der Erweiterung ".VisualElementsManifest.xml", und speichern Sie Sie im selben Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-134">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="d4ba7-135">Beispielsweise wird für die ausführbare Datei "contoso.exe" die zugehörige XML-Datei mit dem Namen "contoso.visualelementsmanifest.xml" benannt.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-135">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="d4ba7-136">Fügen Sie dem Desktop Windows-Startmenü **eine Verknüpfung** zu Ihrer Anwendung hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-136">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="d4ba7-137">Im [folgenden](#sample-app-launcher-shortcut-creation) Beispiel finden Sie ein Beispiel für eine C++-Implementierung.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-137">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="d4ba7-138">Erstellen Sie die Datei unter%ALLUSERSPROFILE%\Microsoft\Windows\Start menu\programme (Machine) oder%APPDATA%\Microsoft\Windows\Start menu\programme (User).</span><span class="sxs-lookup"><span data-stu-id="d4ba7-138">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="d4ba7-139">Wenn ein Update das Manifest der visuellen Elemente oder die darin referenzierten Ressourcen ändert, sollte der Updater oder Installer die Verknüpfung aktualisieren, sodass das Manifest neu analysiert und zwischengespeicherte Objekte aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-139">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="d4ba7-140">*Optional:* Wenn die Desktop Verknüpfung nicht direkt auf die exe-Datei der Anwendung zeigt (z. b., wenn Sie einen benutzerdefinierten Protokollhandler wie "MyApp://" aufruft), findet das Startmenü nicht automatisch die VisualElementsManifest.xml Datei der app.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-140">*Optional:* If your desktop shortcut doesn't point directly to your application’s EXE (for example, if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="d4ba7-141">Um dieses Problem zu beheben, sollte in der Verknüpfung der Dateipfad des visuellen Element Manifests mithilfe von System. appusermodel. visualelementsmanifesthintpath () angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-141">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="d4ba7-142">Dies kann in der Verknüpfung mit denselben Techniken wie System.AppUserModel.ID festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-142">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="d4ba7-143">Sie müssen System.AppUserModel.ID nicht verwenden, aber Sie können dies tun, wenn die Verknüpfung mit der expliziten Anwendungs Benutzer Modell-ID der Anwendung abgeglichen werden soll, wenn eine solche verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-143">You aren't required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="d4ba7-144">Ein C++-Beispiel finden Sie im Abschnitt zur [Erstellung von Beispielen](#sample-app-launcher-shortcut-creation) für das App-Start Programm.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-144">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="d4ba7-145">Beispiel für visuelle Element Manifeste</span><span class="sxs-lookup"><span data-stu-id="d4ba7-145">Sample Visual Elements Manifest</span></span>

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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="d4ba7-146">Beispiel Erstellung für App-Start Programm Verknüpfung</span><span class="sxs-lookup"><span data-stu-id="d4ba7-146">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="d4ba7-147">Der folgende Beispielcode zeigt, wie Sie eine Verknüpfung in C++ erstellen können, einschließlich der Überschreibung der Pfad zur XML-Datei des visuellen Elements.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-147">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="d4ba7-148">Beachten Sie, dass die außer Kraft Setzung nur in Fällen erforderlich ist, in denen Ihre Verknüpfung nicht direkt auf die dem Manifest zugeordnete exe-Datei verweist (die Verknüpfung verwendet beispielsweise einen benutzerdefinierten Protokollhandler wie "MyApp://").</span><span class="sxs-lookup"><span data-stu-id="d4ba7-148">Note the override is only required in cases where your shortcut doesn't point directly to the EXE associated with the manifest (for example, your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="d4ba7-149">Blutprobe. Lnk-Verknüpfungs Erstellung (C++)</span><span class="sxs-lookup"><span data-stu-id="d4ba7-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="d4ba7-150">Blutprobe. URL-Start Programm Verknüpfung</span><span class="sxs-lookup"><span data-stu-id="d4ba7-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="d4ba7-151">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d4ba7-151">See also</span></span>

* <span data-ttu-id="d4ba7-152">[Gemischtes Reality-Modell Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) mit einem 3D-App-Start Programm.</span><span class="sxs-lookup"><span data-stu-id="d4ba7-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="d4ba7-153">Entwurfsanleitung für 3D-App-Startprogramm</span><span class="sxs-lookup"><span data-stu-id="d4ba7-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="d4ba7-154">Erstellen von 3D-Modellen für die Verwendung in der Windows Mixed Reality-Startseite</span><span class="sxs-lookup"><span data-stu-id="d4ba7-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="d4ba7-155">Implementieren von 3D-App-launchern (UWP-Apps)</span><span class="sxs-lookup"><span data-stu-id="d4ba7-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="d4ba7-156">Navigieren auf der Startseite von Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d4ba7-156">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
