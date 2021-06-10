---
title: Bereitstellen auf Hololens- und WMR-Headsets
description: Dokumentation zum Erstellen und Bereitstellen von Apps auf verschiedenen Geräten.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Visual Studio
ms.openlocfilehash: 1547f0630d307e9e87505890adef4cad366d6c00
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441159"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="57509-104">Bereitstellen auf Hololens- und WMR-Headsets</span><span class="sxs-lookup"><span data-stu-id="57509-104">Deploying to Hololens and WMR headsets</span></span>

<span data-ttu-id="57509-105">Es gibt zwei Möglichkeiten zum Bereitstellen von Anwendungen, die mit MRTK erstellt wurden, auf Ihrem Windows-Gerät: die Universelle Windows-Plattform (UWP) und die eigenständige Plattform.</span><span class="sxs-lookup"><span data-stu-id="57509-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="57509-106">Anwendungen, die für HoloLens 1 oder HoloLens 2 entwickelt wurden, müssen UWP als Ziel verwenden, während Anwendungen, die für WMR-Headsets erstellt wurden, UWP oder eigenständig als Ziel verwenden können.</span><span class="sxs-lookup"><span data-stu-id="57509-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="57509-107">Erstellen und Bereitstellen von MRTK für HoloLens 1, HoloLens 2 und WMR-Headsets (UWP)</span><span class="sxs-lookup"><span data-stu-id="57509-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="57509-108">Anweisungen zum Erstellen und Bereitstellen für **HoloLens 1** und **HoloLens 2** (UWP) finden Sie unter Erstellen Ihrer Anwendung [auf dem Gerät.](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)</span><span class="sxs-lookup"><span data-stu-id="57509-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="57509-109">Mit diesen Schritten können Sie auch für **WMR-Headsets bereitstellen.**</span><span class="sxs-lookup"><span data-stu-id="57509-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="57509-110">Wenn Sie Ihre Anwendung auf Ihrem Gerät in Visual Studio bereitstellen, müssen Sie Visual Studio je nach Gerät etwas anders konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="57509-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="57509-111">Die Konfigurationen lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="57509-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="57509-112">Plattform</span><span class="sxs-lookup"><span data-stu-id="57509-112">Platform</span></span> | <span data-ttu-id="57509-113">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="57509-113">Configuration</span></span> | <span data-ttu-id="57509-114">Aufbau</span><span class="sxs-lookup"><span data-stu-id="57509-114">Architecture</span></span> | <span data-ttu-id="57509-115">Ziel</span><span class="sxs-lookup"><span data-stu-id="57509-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="57509-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="57509-116">HoloLens 2</span></span> | <span data-ttu-id="57509-117">Release oder Master</span><span class="sxs-lookup"><span data-stu-id="57509-117">Release or Master</span></span> | <span data-ttu-id="57509-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="57509-118">ARM64</span></span> | <span data-ttu-id="57509-119">Gerät</span><span class="sxs-lookup"><span data-stu-id="57509-119">Device</span></span> |
| <span data-ttu-id="57509-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="57509-120">HoloLens 1</span></span> | <span data-ttu-id="57509-121">Release oder Master</span><span class="sxs-lookup"><span data-stu-id="57509-121">Release or Master</span></span> | <span data-ttu-id="57509-122">x86</span><span class="sxs-lookup"><span data-stu-id="57509-122">x86</span></span> | <span data-ttu-id="57509-123">Gerät</span><span class="sxs-lookup"><span data-stu-id="57509-123">Device</span></span> |
| <span data-ttu-id="57509-124">WMR-Headsets</span><span class="sxs-lookup"><span data-stu-id="57509-124">WMR Headsets</span></span> | <span data-ttu-id="57509-125">Release oder Master</span><span class="sxs-lookup"><span data-stu-id="57509-125">Release or Master</span></span> | <span data-ttu-id="57509-126">x64</span><span class="sxs-lookup"><span data-stu-id="57509-126">x64</span></span> | <span data-ttu-id="57509-127">Lokaler Computer</span><span class="sxs-lookup"><span data-stu-id="57509-127">Local Machine</span></span> |

<span data-ttu-id="57509-128">**Tipp:** Beim Erstellen für HoloLens 1, HoloLens 2 oder WMR wird empfohlen, dass die Buildeinstellungen "Ziel-SDK-Version" und "Mindestplattformversion" wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="57509-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Fenster „Build“ (Erstellen)](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="57509-130">Die anderen Einstellungen können unterschiedlich sein (z. b. Buildkonfiguration/Architektur/Buildtyp, und andere können in der Visual Studio-Projektmappe immer geändert werden).</span><span class="sxs-lookup"><span data-stu-id="57509-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="57509-131">Stellen Sie sicher, dass in der Dropdownliste „SDK-Zielversion“ die Option „10.0.18362.0“ enthalten ist. Sollte diese fehlen, muss [das neueste Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) installiert werden.</span><span class="sxs-lookup"><span data-stu-id="57509-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="57509-132">Unity 2019.3 und HoloLens</span><span class="sxs-lookup"><span data-stu-id="57509-132">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="57509-133">Wenn eine HoloLens-App als 2D-Bereich auf dem Gerät angezeigt wird, stellen Sie sicher, dass die folgenden Einstellungen in Unity 2019.3.x konfiguriert wurden, bevor Sie Ihre UWP-App bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="57509-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="57509-134">Bei Verwendung von Legacy-XR:</span><span class="sxs-lookup"><span data-stu-id="57509-134">If using the legacy XR:</span></span>

1. <span data-ttu-id="57509-135">Navigieren Sie zu „Bearbeiten > Projekteinstellungen, Player“.</span><span class="sxs-lookup"><span data-stu-id="57509-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="57509-136">Stellen Sie sicher, dass unter **XR-Einstellungen** auf der Registerkarte „UWP“ die Option **Virtuelle Realität unterstützt** aktiviert ist, und dass das **Windows Mixed Reality** SDK zu den SDKs hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="57509-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="57509-137">Erstellen und Bereitstellen in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="57509-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="57509-138">Bei Verwendung des XR-Plug-Ins:</span><span class="sxs-lookup"><span data-stu-id="57509-138">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="57509-139">Befolgen Sie die Schritte unter [Erste Schritte mit XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md).</span><span class="sxs-lookup"><span data-stu-id="57509-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="57509-140">Stellen Sie sicher, dass das Konfigurationsprofil **DefaultXRSDKConfigurationProfile** ist.</span><span class="sxs-lookup"><span data-stu-id="57509-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="57509-141">Navigieren Sie zu **Bearbeiten > Projekteinstellungen, XR-Plug-In-Verwaltung**, und vergewissern Sie sich, dass **Windows Mixed Reality** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="57509-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="57509-142">Erstellen und Bereitstellen in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="57509-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="57509-143">Wenn Sie Unity 2019.3.x verwenden, wählen Sie **ARM64** und nicht **ARM** als Buildarchitektur in Visual Studio aus.</span><span class="sxs-lookup"><span data-stu-id="57509-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="57509-144">Mit den Unity-Standardeinstellungen in Unity 2019.3.x wird eine Unity-App nicht auf einer HoloLens bereitgestellt, wenn ARM aufgrund eines Unity-Fehlers ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="57509-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="57509-145">Dies kann mit der [Problemverfolgung von Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2) nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="57509-145">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="57509-146">Wenn die ARM-Architektur erforderlich ist, navigieren Sie zu **Bearbeiten > Projekteinstellungen, Player**, und deaktivieren Sie im Menü **Weitere Einstellungen** die Option **Grafikaufträge**.</span><span class="sxs-lookup"><span data-stu-id="57509-146">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="57509-147">Durch das Deaktivieren von **Grafikaufträge** kann die App mithilfe der ARM-Buildarchitektur für Unity 2019.3.x bereitgestellt werden, doch empfohlen wird ARM64.</span><span class="sxs-lookup"><span data-stu-id="57509-147">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="57509-148">Erstellen und Bereitstellen von MRTK für WMR-Headsets (eigenständig)</span><span class="sxs-lookup"><span data-stu-id="57509-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="57509-149">Eigenständige MRTK-Builds können auf WMR-Headsets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="57509-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="57509-150">Ein eigenständiger Build für ein WMR-Headset erfordert die folgenden zusätzlichen Schritte:</span><span class="sxs-lookup"><span data-stu-id="57509-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="57509-151">Das XR SDK von Unity unterstützt auch native WMR in eigenständigen Builds, erfordert aber kein SteamVR- oder WMR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="57509-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="57509-152">Diese Schritte sind für die Legacy-XR von Unity erforderlich.</span><span class="sxs-lookup"><span data-stu-id="57509-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="57509-153">Installieren von [Steam](https://store.steampowered.com/about/).</span><span class="sxs-lookup"><span data-stu-id="57509-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="57509-154">Installieren von [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="57509-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="57509-155">Installieren des [WMR-Plug-Ins](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="57509-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="57509-156">Verwenden des WMR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="57509-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="57509-157">Öffnen Sie Steam, und suchen Sie nach dem Windows Mixed Reality-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="57509-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="57509-158">Stellen Sie sicher, dass SteamVR geschlossen ist, bevor Sie das WMR-Plug-In starten.</span><span class="sxs-lookup"><span data-stu-id="57509-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="57509-159">Durch das Starten des WMR-Plug-Ins wird auch SteamVR gestartet.</span><span class="sxs-lookup"><span data-stu-id="57509-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="57509-160">Stellen Sie sicher, dass das WMR-Headset angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="57509-160">Make sure the WMR headset is plugged in.</span></span>

    ![WMR-Plug-In-Suche](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="57509-162">Wählen Sie für das Windows Mixed Reality für SteamVR-Plug-In **Starten** aus.</span><span class="sxs-lookup"><span data-stu-id="57509-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR-Plug-In](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="57509-164">SteamVR und das WMR-Plug-In werden gestartet, und ein neues Fenster mit dem Nachverfolgungsstatus für das WMR-Headset wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="57509-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="57509-165">Weitere Informationen finden Sie in der [Dokumentation zu Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="57509-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Darstellung des WMR-Starts](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="57509-167">Navigieren Sie in Unity bei geöffneter MRTK-Szene zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="57509-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="57509-168">Erstellen der Szene</span><span class="sxs-lookup"><span data-stu-id="57509-168">Build the scene</span></span>
    - <span data-ttu-id="57509-169">Wählen Sie **Offene Szene hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="57509-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="57509-170">Stellen Sie sicher, dass die Plattform **Eigenständig** ist.</span><span class="sxs-lookup"><span data-stu-id="57509-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="57509-171">Wählen Sie **Build** aus.</span><span class="sxs-lookup"><span data-stu-id="57509-171">Select **Build**</span></span>
    - <span data-ttu-id="57509-172">Wählen Sie den Speicherort für den neuen Build im Datei-Explorer aus.</span><span class="sxs-lookup"><span data-stu-id="57509-172">Choose the location for the new build in File Explorer</span></span>

    ![Einstellungen für eigenständigen Build](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="57509-174">Eine neue ausführbare Unity-Datei wird erstellt, um Ihre App zu starten. Wählen Sie die ausführbare Unity-Datei im Datei-Explorer aus.</span><span class="sxs-lookup"><span data-stu-id="57509-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity-Datei-Explorer](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="57509-176">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="57509-176">See also</span></span>

- [<span data-ttu-id="57509-177">Android- und iOS-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="57509-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="57509-178">Leap Motion-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="57509-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="57509-179">Erkennen von Plattformfunktionen</span><span class="sxs-lookup"><span data-stu-id="57509-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)