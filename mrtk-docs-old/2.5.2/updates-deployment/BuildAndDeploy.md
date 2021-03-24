---
title: BuildAndDeploy
description: Dokumentation zum Erstellen und Bereitstellen von Apps auf verschiedenen Geräten.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Visual Studio, Android, iOS
ms.openlocfilehash: 3256296c1fd13ad051d2c75805c49ec555e8977d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686462"
---
# <a name="building-and-deploying-mrtk"></a><span data-ttu-id="92168-104">Erstellen und Bereitstellen von MRTK</span><span class="sxs-lookup"><span data-stu-id="92168-104">Building and deploying MRTK</span></span>

<span data-ttu-id="92168-105">Um eine App auf einem Gerät als eigenständige App (für HoloLens, Android, iOS usw.) auszuführen, muss der Schritt zum Erstellen und Bereitstellen im Unity-Projekt ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="92168-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="92168-106">Das Entwickeln und Bereitstellen einer App, die MRTK verwendet, ist wie das Entwickeln und Bereitstellen jeder anderen Unity-App.</span><span class="sxs-lookup"><span data-stu-id="92168-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="92168-107">Es gibt keine MRTK-spezifischen Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="92168-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="92168-108">Im Folgenden finden Sie ausführliche Schritte zum Erstellen und Bereitstellen einer Unity-App für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="92168-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span>  <span data-ttu-id="92168-109">Weitere Informationen zum Erstellen für andere Plattformen finden Sie unter [Veröffentlichen von Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span><span class="sxs-lookup"><span data-stu-id="92168-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a><span data-ttu-id="92168-110">Erstellen und Bereitstellen von MRTK für HoloLens 1 und HoloLens 2 (UWP)</span><span class="sxs-lookup"><span data-stu-id="92168-110">Building and deploying MRTK to HoloLens 1 and HoloLens 2 (UWP)</span></span>

<span data-ttu-id="92168-111">Anweisungen zum Erstellen und Bereitstellen für HoloLens 1 und HoloLens 2 (UWP) finden Sie unter [Erstellen Ihrer Anwendung auf dem Gerät](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="92168-111">Instructions on how to build and deploy for HoloLens 1 and HoloLens 2 (UWP) can be found at [building your application to device](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span>

<span data-ttu-id="92168-112">**Tipp:** Beim Erstellen für WMR, HoloLens 1 oder HoloLens 2 wird empfohlen, dass die Buildeinstellungen „SDK-Zielversion“ und „Minimale Plattformversion“ wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="92168-112">**Tip:** When building for WMR, HoloLens 1, or HoloLens 2, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Fenster „Build“ (Erstellen)](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="92168-114">Die anderen Einstellungen können unterschiedlich sein (z. b. Buildkonfiguration/Architektur/Buildtyp, und andere können in der Visual Studio-Projektmappe immer geändert werden).</span><span class="sxs-lookup"><span data-stu-id="92168-114">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="92168-115">Stellen Sie sicher, dass in der Dropdownliste „SDK-Zielversion“ die Option „10.0.18362.0“ enthalten ist. Sollte diese fehlen, muss [das neueste Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) installiert werden.</span><span class="sxs-lookup"><span data-stu-id="92168-115">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="92168-116">Unity 2019.3 und HoloLens</span><span class="sxs-lookup"><span data-stu-id="92168-116">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="92168-117">Wenn eine HoloLens-App als 2D-Bereich auf dem Gerät angezeigt wird, stellen Sie sicher, dass die folgenden Einstellungen in Unity 2019.3.x konfiguriert wurden, bevor Sie Ihre UWP-App bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="92168-117">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="92168-118">Bei Verwendung von Legacy-XR:</span><span class="sxs-lookup"><span data-stu-id="92168-118">If using the legacy XR:</span></span>

1. <span data-ttu-id="92168-119">Navigieren Sie zu „Bearbeiten > Projekteinstellungen, Player“.</span><span class="sxs-lookup"><span data-stu-id="92168-119">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="92168-120">Stellen Sie sicher, dass unter **XR-Einstellungen** auf der Registerkarte „UWP“ die Option **Virtuelle Realität unterstützt** aktiviert ist, und dass das **Windows Mixed Reality** SDK zu den SDKs hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="92168-120">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="92168-121">Erstellen und Bereitstellen in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="92168-121">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="92168-122">Bei Verwendung des XR-Plug-Ins:</span><span class="sxs-lookup"><span data-stu-id="92168-122">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="92168-123">Befolgen Sie die Schritte unter [Erste Schritte mit XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md).</span><span class="sxs-lookup"><span data-stu-id="92168-123">Follow the steps found in [Getting Started with XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md)</span></span>
1. <span data-ttu-id="92168-124">Stellen Sie sicher, dass das Konfigurationsprofil **DefaultXRSDKConfigurationProfile** ist.</span><span class="sxs-lookup"><span data-stu-id="92168-124">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="92168-125">Navigieren Sie zu **Bearbeiten > Projekteinstellungen, XR-Plug-In-Verwaltung**, und vergewissern Sie sich, dass **Windows Mixed Reality** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="92168-125">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="92168-126">Erstellen und Bereitstellen in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="92168-126">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="92168-127">Wenn Sie Unity 2019.3.x verwenden, wählen Sie **ARM64** und nicht **ARM** als Buildarchitektur in Visual Studio aus.</span><span class="sxs-lookup"><span data-stu-id="92168-127">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="92168-128">Mit den Unity-Standardeinstellungen in Unity 2019.3.x wird eine Unity-App nicht auf einer HoloLens bereitgestellt, wenn ARM aufgrund eines Unity-Fehlers ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="92168-128">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="92168-129">Dies kann mit der [Problemverfolgung von Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2) nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="92168-129">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="92168-130">Wenn die ARM-Architektur erforderlich ist, navigieren Sie zu **Bearbeiten > Projekteinstellungen, Player**, und deaktivieren Sie im Menü **Weitere Einstellungen** die Option **Grafikaufträge**.</span><span class="sxs-lookup"><span data-stu-id="92168-130">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="92168-131">Durch das Deaktivieren von **Grafikaufträge** kann die App mithilfe der ARM-Buildarchitektur für Unity 2019.3.x bereitgestellt werden, doch empfohlen wird ARM64.</span><span class="sxs-lookup"><span data-stu-id="92168-131">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a><span data-ttu-id="92168-132">Entwickeln und Bereitstellen von MRTK für ein Windows Mixed Reality-Headset</span><span class="sxs-lookup"><span data-stu-id="92168-132">Building and deploying MRTK to a Windows Mixed Reality Headset</span></span>

<span data-ttu-id="92168-133">Das Windows Mixed Reality-Headset (WMR) kann für universelle Windows-Plattform- (UWP) und eigenständige Builds verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="92168-133">The Windows Mixed Reality (WMR) headset can be used for Universal Windows Platform (UWP) and Standalone builds.</span></span>  <span data-ttu-id="92168-134">Ein eigenständiger Build für ein WMR-Headset erfordert die folgenden zusätzlichen Schritte:</span><span class="sxs-lookup"><span data-stu-id="92168-134">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="92168-135">Das XR SDK von Unity unterstützt auch native WMR in eigenständigen Builds, erfordert aber kein SteamVR- oder WMR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="92168-135">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="92168-136">Diese Schritte sind für die Legacy-XR von Unity erforderlich.</span><span class="sxs-lookup"><span data-stu-id="92168-136">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="92168-137">Installieren von [Steam](https://store.steampowered.com/about/).</span><span class="sxs-lookup"><span data-stu-id="92168-137">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="92168-138">Installieren von [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="92168-138">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="92168-139">Installieren des [WMR-Plug-Ins](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="92168-139">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="92168-140">Verwenden des WMR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="92168-140">How to use WMR plugin</span></span>

1. <span data-ttu-id="92168-141">Öffnen Sie Steam, und suchen Sie nach dem Windows Mixed Reality-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="92168-141">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="92168-142">Stellen Sie sicher, dass SteamVR geschlossen ist, bevor Sie das WMR-Plug-In starten.</span><span class="sxs-lookup"><span data-stu-id="92168-142">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="92168-143">Durch das Starten des WMR-Plug-Ins wird auch SteamVR gestartet.</span><span class="sxs-lookup"><span data-stu-id="92168-143">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="92168-144">Stellen Sie sicher, dass das WMR-Headset angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="92168-144">Make sure the WMR headset is plugged in.</span></span>

    ![WMR-Plug-In-Suche](../features/images/build-deploy/wmr/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="92168-146">Wählen Sie für das Windows Mixed Reality für SteamVR-Plug-In **Starten** aus.</span><span class="sxs-lookup"><span data-stu-id="92168-146">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR-Plug-In](../features/images/build-deploy/wmr/WMRPlugin.png)

    - <span data-ttu-id="92168-148">SteamVR und das WMR-Plug-In werden gestartet, und ein neues Fenster mit dem Nachverfolgungsstatus für das WMR-Headset wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="92168-148">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="92168-149">Weitere Informationen finden Sie in der [Dokumentation zu Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="92168-149">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Darstellung des WMR-Starts](../features/images/build-deploy/wmr/WMRPluginActive.png)

1. <span data-ttu-id="92168-151">Navigieren Sie in Unity bei geöffneter MRTK-Szene zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="92168-151">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="92168-152">Erstellen der Szene</span><span class="sxs-lookup"><span data-stu-id="92168-152">Build the scene</span></span>
    - <span data-ttu-id="92168-153">Wählen Sie **Offene Szene hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="92168-153">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="92168-154">Stellen Sie sicher, dass die Plattform **Eigenständig** ist.</span><span class="sxs-lookup"><span data-stu-id="92168-154">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="92168-155">Wählen Sie **Build** aus.</span><span class="sxs-lookup"><span data-stu-id="92168-155">Select **Build**</span></span>
    - <span data-ttu-id="92168-156">Wählen Sie den Speicherort für den neuen Build im Datei-Explorer aus.</span><span class="sxs-lookup"><span data-stu-id="92168-156">Choose the location for the new build in File Explorer</span></span>

    ![Einstellungen für eigenständigen Build](../features/images/build-deploy/wmr/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="92168-158">Eine neue ausführbare Unity-Datei wird erstellt, um Ihre App zu starten. Wählen Sie die ausführbare Unity-Datei im Datei-Explorer aus.</span><span class="sxs-lookup"><span data-stu-id="92168-158">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity-Datei-Explorer](../features/images/build-deploy/wmr/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="92168-160">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="92168-160">See also</span></span>

- [<span data-ttu-id="92168-161">Android- und iOS-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="92168-161">Android and iOS Support</span></span>](../features/cross-platform/UsingARFoundation.md)
- [<span data-ttu-id="92168-162">Leap Motion-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="92168-162">Leap Motion Support</span></span>](../features/cross-platform/LeapMotionMRTK.md)
- [<span data-ttu-id="92168-163">Erkennen von Plattformfunktionen</span><span class="sxs-lookup"><span data-stu-id="92168-163">Detecting Platform Capabilities</span></span>](../features/cross-platform/DetectingPlatformCapabilities.md)
