---
title: Bereitstellen auf HoloLens- und WMR-Headsets
description: Dokumentation zum Erstellen und Bereitstellen von Apps auf verschiedenen Geräten.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Visual Studio
ms.openlocfilehash: 137e1b699e9a0cda1e8a454a6c3219b581fa71b4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176377"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="a2482-104">Bereitstellen auf HoloLens- und WMR-Headsets</span><span class="sxs-lookup"><span data-stu-id="a2482-104">Deploying to HoloLens and WMR headsets</span></span>

<span data-ttu-id="a2482-105">Es gibt zwei Möglichkeiten, anwendungen, die mit MRTK erstellt wurden, auf Ihrem Windows-Gerät bereitzustellen: die Universelle Windows-Plattform (UWP) und die eigenständige Plattform.</span><span class="sxs-lookup"><span data-stu-id="a2482-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="a2482-106">Anwendungen, die für HoloLens 1 oder HoloLens 2 erstellt wurden, müssen UWP als Ziel verwenden, während Anwendungen, die für WMR-Headsets erstellt wurden, entweder UWP oder Eigenständig sein können.</span><span class="sxs-lookup"><span data-stu-id="a2482-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="a2482-107">Erstellen und Bereitstellen von MRTK für HoloLens 1, HoloLens 2 und WMR-Headsets (UWP)</span><span class="sxs-lookup"><span data-stu-id="a2482-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="a2482-108">Anweisungen zum Erstellen und Bereitstellen für **HoloLens 1** und **HoloLens 2** (UWP) finden Sie unter [Erstellen Ihrer Anwendung auf dem Gerät.](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)</span><span class="sxs-lookup"><span data-stu-id="a2482-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="a2482-109">Mit diesen Schritten können Sie auch auf **WMR-Headsets** bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="a2482-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="a2482-110">Wenn Sie Ihre Anwendung auf Ihrem Gerät in Visual Studio bereitstellen, müssen Sie Visual Studio je nach Gerät etwas anders konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="a2482-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="a2482-111">Die Konfigurationen sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="a2482-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="a2482-112">Plattform</span><span class="sxs-lookup"><span data-stu-id="a2482-112">Platform</span></span> | <span data-ttu-id="a2482-113">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="a2482-113">Configuration</span></span> | <span data-ttu-id="a2482-114">Aufbau</span><span class="sxs-lookup"><span data-stu-id="a2482-114">Architecture</span></span> | <span data-ttu-id="a2482-115">Target (Ziel)</span><span class="sxs-lookup"><span data-stu-id="a2482-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="a2482-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a2482-116">HoloLens 2</span></span> | <span data-ttu-id="a2482-117">Release oder Master</span><span class="sxs-lookup"><span data-stu-id="a2482-117">Release or Master</span></span> | <span data-ttu-id="a2482-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="a2482-118">ARM64</span></span> | <span data-ttu-id="a2482-119">Gerät</span><span class="sxs-lookup"><span data-stu-id="a2482-119">Device</span></span> |
| <span data-ttu-id="a2482-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="a2482-120">HoloLens 1</span></span> | <span data-ttu-id="a2482-121">Release oder Master</span><span class="sxs-lookup"><span data-stu-id="a2482-121">Release or Master</span></span> | <span data-ttu-id="a2482-122">x86</span><span class="sxs-lookup"><span data-stu-id="a2482-122">x86</span></span> | <span data-ttu-id="a2482-123">Gerät</span><span class="sxs-lookup"><span data-stu-id="a2482-123">Device</span></span> |
| <span data-ttu-id="a2482-124">WMR-Headsets</span><span class="sxs-lookup"><span data-stu-id="a2482-124">WMR Headsets</span></span> | <span data-ttu-id="a2482-125">Release oder Master</span><span class="sxs-lookup"><span data-stu-id="a2482-125">Release or Master</span></span> | <span data-ttu-id="a2482-126">x64</span><span class="sxs-lookup"><span data-stu-id="a2482-126">x64</span></span> | <span data-ttu-id="a2482-127">Lokaler Computer</span><span class="sxs-lookup"><span data-stu-id="a2482-127">Local Machine</span></span> |

<span data-ttu-id="a2482-128">**Tipp:** Beim Erstellen für HoloLens 1, HoloLens 2 oder WMR wird empfohlen, dass die Buildeinstellungen "Ziel-SDK-Version" und "Mindestplattformversion" wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="a2482-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Fenster „Build“ (Erstellen)](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="a2482-130">Die anderen Einstellungen können unterschiedlich sein (z. b. Buildkonfiguration/Architektur/Buildtyp, und andere können in der Visual Studio-Projektmappe immer geändert werden).</span><span class="sxs-lookup"><span data-stu-id="a2482-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="a2482-131">Stellen Sie sicher, dass in der Dropdownliste „SDK-Zielversion“ die Option „10.0.18362.0“ enthalten ist. Sollte diese fehlen, muss [das neueste Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) installiert werden.</span><span class="sxs-lookup"><span data-stu-id="a2482-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20192020-and-hololens"></a><span data-ttu-id="a2482-132">Unity 2019/2020 und HoloLens</span><span class="sxs-lookup"><span data-stu-id="a2482-132">Unity 2019/2020 and HoloLens</span></span>

<span data-ttu-id="a2482-133">Wenn eine HoloLens-App als 2D-Panel auf dem Gerät angezeigt wird, stellen Sie sicher, dass die folgenden Einstellungen in Unity konfiguriert wurden, bevor Sie Ihre UWP-App bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="a2482-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity before deploying your UWP app:</span></span>

<span data-ttu-id="a2482-134">Bei Verwendung der älteren integrierten XR-Unterstützung (nur Unity 2019):</span><span class="sxs-lookup"><span data-stu-id="a2482-134">If using the legacy built-in XR support (Unity 2019 only):</span></span>

1. <span data-ttu-id="a2482-135">Navigieren Sie zu „Bearbeiten > Projekteinstellungen, Player“.</span><span class="sxs-lookup"><span data-stu-id="a2482-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="a2482-136">Stellen Sie sicher, dass unter **XR-Einstellungen** auf der Registerkarte „UWP“ die Option **Virtuelle Realität unterstützt** aktiviert ist, und dass das **Windows Mixed Reality** SDK zu den SDKs hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a2482-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="a2482-137">Erstellen und Bereitstellen in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a2482-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="a2482-138">Bei Verwendung der OpenXR- oder Windows XR-Plug-Ins:</span><span class="sxs-lookup"><span data-stu-id="a2482-138">If using the OpenXR or Windows XR plugins:</span></span>

1. <span data-ttu-id="a2482-139">Befolgen Sie die Schritte unter [Erste Schritte mit XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md).</span><span class="sxs-lookup"><span data-stu-id="a2482-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="a2482-140">Stellen Sie sicher, dass das Konfigurationsprofil **DefaultXRSDKConfigurationProfile** ist.</span><span class="sxs-lookup"><span data-stu-id="a2482-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="a2482-141">Navigieren Sie zu **Bearbeiten > Projekteinstellungen, XR-Plug-In-Verwaltung**, und vergewissern Sie sich, dass **Windows Mixed Reality** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="a2482-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="a2482-142">Erstellen und Bereitstellen in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a2482-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="a2482-143">Wenn Sie Unity 2019.3.x verwenden, wählen Sie **ARM64** und nicht **ARM** als Buildarchitektur in Visual Studio aus.</span><span class="sxs-lookup"><span data-stu-id="a2482-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="a2482-144">Mit den Unity-Standardeinstellungen in Unity 2019.3.x wird eine Unity-App nicht auf einer HoloLens bereitgestellt, wenn ARM aufgrund eines Unity-Fehlers ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="a2482-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span>
>
> <span data-ttu-id="a2482-145">Wenn die ARM-Architektur erforderlich ist, navigieren Sie zu **Bearbeiten > Projekteinstellungen, Player**, und deaktivieren Sie im Menü **Weitere Einstellungen** die Option **Grafikaufträge**.</span><span class="sxs-lookup"><span data-stu-id="a2482-145">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="a2482-146">Durch das Deaktivieren von **Grafikaufträge** kann die App mithilfe der ARM-Buildarchitektur für Unity 2019.3.x bereitgestellt werden, doch empfohlen wird ARM64.</span><span class="sxs-lookup"><span data-stu-id="a2482-146">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>
>
> <span data-ttu-id="a2482-147">Dieses Problem wurde in Unity 2019.4 und Unity 2020.3 behoben.</span><span class="sxs-lookup"><span data-stu-id="a2482-147">This issue was fixed in Unity 2019.4 and Unity 2020.3.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="a2482-148">Erstellen und Bereitstellen von MRTK für WMR-Headsets (eigenständig)</span><span class="sxs-lookup"><span data-stu-id="a2482-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="a2482-149">Eigenständige Builds von MRTK können auf WMR-Headsets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a2482-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="a2482-150">Ein eigenständiger Build für ein WMR-Headset erfordert die folgenden zusätzlichen Schritte:</span><span class="sxs-lookup"><span data-stu-id="a2482-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="a2482-151">Das XR SDK von Unity unterstützt auch native WMR in eigenständigen Builds, erfordert aber kein SteamVR- oder WMR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="a2482-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="a2482-152">Diese Schritte sind für die Legacy-XR von Unity erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a2482-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="a2482-153">Installieren von [Steam](https://store.steampowered.com/about/).</span><span class="sxs-lookup"><span data-stu-id="a2482-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="a2482-154">Installieren von [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="a2482-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="a2482-155">Installieren des [WMR-Plug-Ins](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="a2482-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="a2482-156">Verwenden des WMR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="a2482-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="a2482-157">Öffnen Sie Steam, und suchen Sie nach dem Windows Mixed Reality-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="a2482-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="a2482-158">Stellen Sie sicher, dass SteamVR geschlossen ist, bevor Sie das WMR-Plug-In starten.</span><span class="sxs-lookup"><span data-stu-id="a2482-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="a2482-159">Durch das Starten des WMR-Plug-Ins wird auch SteamVR gestartet.</span><span class="sxs-lookup"><span data-stu-id="a2482-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="a2482-160">Stellen Sie sicher, dass das WMR-Headset angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="a2482-160">Make sure the WMR headset is plugged in.</span></span>

    ![WMR-Plug-In-Suche](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="a2482-162">Wählen Sie für das Windows Mixed Reality für SteamVR-Plug-In **Starten** aus.</span><span class="sxs-lookup"><span data-stu-id="a2482-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR-Plug-In](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="a2482-164">SteamVR und das WMR-Plug-In werden gestartet, und ein neues Fenster mit dem Nachverfolgungsstatus für das WMR-Headset wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a2482-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="a2482-165">Weitere Informationen finden Sie in der [Dokumentation zu Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="a2482-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Darstellung des WMR-Starts](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="a2482-167">Navigieren Sie in Unity bei geöffneter MRTK-Szene zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="a2482-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="a2482-168">Erstellen der Szene</span><span class="sxs-lookup"><span data-stu-id="a2482-168">Build the scene</span></span>
    - <span data-ttu-id="a2482-169">Wählen Sie **Offene Szene hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="a2482-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="a2482-170">Stellen Sie sicher, dass die Plattform **Eigenständig** ist.</span><span class="sxs-lookup"><span data-stu-id="a2482-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="a2482-171">Wählen Sie **Build** aus.</span><span class="sxs-lookup"><span data-stu-id="a2482-171">Select **Build**</span></span>
    - <span data-ttu-id="a2482-172">Wählen Sie den Speicherort für den neuen Build im Datei-Explorer aus.</span><span class="sxs-lookup"><span data-stu-id="a2482-172">Choose the location for the new build in File Explorer</span></span>

    ![Einstellungen für eigenständigen Build](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="a2482-174">Eine neue ausführbare Unity-Datei wird erstellt, um Ihre App zu starten. Wählen Sie die ausführbare Unity-Datei im Datei-Explorer aus.</span><span class="sxs-lookup"><span data-stu-id="a2482-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity-Datei-Explorer](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="a2482-176">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a2482-176">See also</span></span>

- [<span data-ttu-id="a2482-177">Android- und iOS-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="a2482-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="a2482-178">Leap Motion-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="a2482-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="a2482-179">Erkennen von Plattformfunktionen</span><span class="sxs-lookup"><span data-stu-id="a2482-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)
