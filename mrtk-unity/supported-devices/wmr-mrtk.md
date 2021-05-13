---
title: Bereitstellen auf Hololens- und WMR-Geräten
description: Dokumentation zum Erstellen und Bereitstellen von Apps auf verschiedenen Geräten.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Visual Studio
ms.openlocfilehash: ec66c6ccb8cf1c702fed804230f5cf3ca0526139
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852372"
---
# <a name="building-and-deploying-mrtk-uwp"></a><span data-ttu-id="20dce-104">Erstellen und Bereitstellen von MRTK (UWP)</span><span class="sxs-lookup"><span data-stu-id="20dce-104">Building and deploying MRTK (UWP)</span></span>

<span data-ttu-id="20dce-105">Um eine App auf einem Gerät als eigenständige App (für HoloLens, Android, iOS usw.) auszuführen, muss der Schritt zum Erstellen und Bereitstellen im Unity-Projekt ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="20dce-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="20dce-106">Das Entwickeln und Bereitstellen einer App, die MRTK verwendet, ist wie das Entwickeln und Bereitstellen jeder anderen Unity-App.</span><span class="sxs-lookup"><span data-stu-id="20dce-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="20dce-107">Es gibt keine MRTK-spezifischen Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="20dce-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="20dce-108">Im Folgenden finden Sie ausführliche Schritte zum Erstellen und Bereitstellen einer Unity-App für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="20dce-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span> <span data-ttu-id="20dce-109">Weitere Informationen zum Erstellen für andere Plattformen finden Sie unter [Veröffentlichen von Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span><span class="sxs-lookup"><span data-stu-id="20dce-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="20dce-110">Erstellen und Bereitstellen von MRTK für HoloLens 1, HoloLens 2 und WMR-Headsets (UWP)</span><span class="sxs-lookup"><span data-stu-id="20dce-110">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="20dce-111">Anweisungen zum Erstellen und Bereitstellen für **HoloLens 1** und **HoloLens 2** (UWP) finden Sie unter Erstellen Ihrer Anwendung [auf dem Gerät.](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)</span><span class="sxs-lookup"><span data-stu-id="20dce-111">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="20dce-112">Mit diesen Schritten können Sie auch für **WMR-Headsets bereitstellen.**</span><span class="sxs-lookup"><span data-stu-id="20dce-112">These steps also allow you to deploy to **WMR headsets**.</span></span>

<span data-ttu-id="20dce-113">**Tipp:** Beim Erstellen für HoloLens 1, HoloLens 2 oder WMR wird empfohlen, dass die Buildeinstellungen "Ziel-SDK-Version" und "Mindestplattformversion" wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="20dce-113">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![Fenster „Build“ (Erstellen)](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="20dce-115">Die anderen Einstellungen können unterschiedlich sein (z. b. Buildkonfiguration/Architektur/Buildtyp, und andere können in der Visual Studio-Projektmappe immer geändert werden).</span><span class="sxs-lookup"><span data-stu-id="20dce-115">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="20dce-116">Stellen Sie sicher, dass in der Dropdownliste „SDK-Zielversion“ die Option „10.0.18362.0“ enthalten ist. Sollte diese fehlen, muss [das neueste Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) installiert werden.</span><span class="sxs-lookup"><span data-stu-id="20dce-116">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="20dce-117">Unity 2019.3 und HoloLens</span><span class="sxs-lookup"><span data-stu-id="20dce-117">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="20dce-118">Wenn eine HoloLens-App als 2D-Bereich auf dem Gerät angezeigt wird, stellen Sie sicher, dass die folgenden Einstellungen in Unity 2019.3.x konfiguriert wurden, bevor Sie Ihre UWP-App bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="20dce-118">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="20dce-119">Bei Verwendung von Legacy-XR:</span><span class="sxs-lookup"><span data-stu-id="20dce-119">If using the legacy XR:</span></span>

1. <span data-ttu-id="20dce-120">Navigieren Sie zu „Bearbeiten > Projekteinstellungen, Player“.</span><span class="sxs-lookup"><span data-stu-id="20dce-120">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="20dce-121">Stellen Sie sicher, dass unter **XR-Einstellungen** auf der Registerkarte „UWP“ die Option **Virtuelle Realität unterstützt** aktiviert ist, und dass das **Windows Mixed Reality** SDK zu den SDKs hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="20dce-121">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="20dce-122">Erstellen und Bereitstellen in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="20dce-122">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="20dce-123">Bei Verwendung des XR-Plug-Ins:</span><span class="sxs-lookup"><span data-stu-id="20dce-123">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="20dce-124">Befolgen Sie die Schritte unter [Erste Schritte mit XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md).</span><span class="sxs-lookup"><span data-stu-id="20dce-124">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="20dce-125">Stellen Sie sicher, dass das Konfigurationsprofil **DefaultXRSDKConfigurationProfile** ist.</span><span class="sxs-lookup"><span data-stu-id="20dce-125">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="20dce-126">Navigieren Sie zu **Bearbeiten > Projekteinstellungen, XR-Plug-In-Verwaltung**, und vergewissern Sie sich, dass **Windows Mixed Reality** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="20dce-126">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="20dce-127">Erstellen und Bereitstellen in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="20dce-127">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="20dce-128">Wenn Sie Unity 2019.3.x verwenden, wählen Sie **ARM64** und nicht **ARM** als Buildarchitektur in Visual Studio aus.</span><span class="sxs-lookup"><span data-stu-id="20dce-128">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="20dce-129">Mit den Unity-Standardeinstellungen in Unity 2019.3.x wird eine Unity-App nicht auf einer HoloLens bereitgestellt, wenn ARM aufgrund eines Unity-Fehlers ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="20dce-129">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="20dce-130">Dies kann mit der [Problemverfolgung von Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2) nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="20dce-130">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="20dce-131">Wenn die ARM-Architektur erforderlich ist, navigieren Sie zu **Bearbeiten > Projekteinstellungen, Player**, und deaktivieren Sie im Menü **Weitere Einstellungen** die Option **Grafikaufträge**.</span><span class="sxs-lookup"><span data-stu-id="20dce-131">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="20dce-132">Durch das Deaktivieren von **Grafikaufträge** kann die App mithilfe der ARM-Buildarchitektur für Unity 2019.3.x bereitgestellt werden, doch empfohlen wird ARM64.</span><span class="sxs-lookup"><span data-stu-id="20dce-132">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-standalone"></a><span data-ttu-id="20dce-133">Erstellen und Bereitstellen von MRTK (eigenständig)</span><span class="sxs-lookup"><span data-stu-id="20dce-133">Building and deploying MRTK (Standalone)</span></span>

<span data-ttu-id="20dce-134">Eigenständige MrTK-Builds können auf WMR-Headsets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="20dce-134">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="20dce-135">Ein eigenständiger Build für ein WMR-Headset erfordert die folgenden zusätzlichen Schritte:</span><span class="sxs-lookup"><span data-stu-id="20dce-135">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="20dce-136">Das XR SDK von Unity unterstützt auch native WMR in eigenständigen Builds, erfordert aber kein SteamVR- oder WMR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="20dce-136">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="20dce-137">Diese Schritte sind für die Legacy-XR von Unity erforderlich.</span><span class="sxs-lookup"><span data-stu-id="20dce-137">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="20dce-138">Installieren von [Steam](https://store.steampowered.com/about/).</span><span class="sxs-lookup"><span data-stu-id="20dce-138">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="20dce-139">Installieren von [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="20dce-139">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="20dce-140">Installieren des [WMR-Plug-Ins](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).</span><span class="sxs-lookup"><span data-stu-id="20dce-140">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="20dce-141">Verwenden des WMR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="20dce-141">How to use WMR plugin</span></span>

1. <span data-ttu-id="20dce-142">Öffnen Sie Steam, und suchen Sie nach dem Windows Mixed Reality-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="20dce-142">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="20dce-143">Stellen Sie sicher, dass SteamVR geschlossen ist, bevor Sie das WMR-Plug-In starten.</span><span class="sxs-lookup"><span data-stu-id="20dce-143">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="20dce-144">Durch das Starten des WMR-Plug-Ins wird auch SteamVR gestartet.</span><span class="sxs-lookup"><span data-stu-id="20dce-144">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="20dce-145">Stellen Sie sicher, dass das WMR-Headset angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="20dce-145">Make sure the WMR headset is plugged in.</span></span>

    ![WMR-Plug-In-Suche](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="20dce-147">Wählen Sie für das Windows Mixed Reality für SteamVR-Plug-In **Starten** aus.</span><span class="sxs-lookup"><span data-stu-id="20dce-147">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR-Plug-In](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="20dce-149">SteamVR und das WMR-Plug-In werden gestartet, und ein neues Fenster mit dem Nachverfolgungsstatus für das WMR-Headset wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="20dce-149">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="20dce-150">Weitere Informationen finden Sie in der [Dokumentation zu Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="20dce-150">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![Darstellung des WMR-Starts](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="20dce-152">Navigieren Sie in Unity bei geöffneter MRTK-Szene zu **Datei > Buildeinstellungen**.</span><span class="sxs-lookup"><span data-stu-id="20dce-152">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="20dce-153">Erstellen der Szene</span><span class="sxs-lookup"><span data-stu-id="20dce-153">Build the scene</span></span>
    - <span data-ttu-id="20dce-154">Wählen Sie **Offene Szene hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="20dce-154">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="20dce-155">Stellen Sie sicher, dass die Plattform **Eigenständig** ist.</span><span class="sxs-lookup"><span data-stu-id="20dce-155">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="20dce-156">Wählen Sie **Build** aus.</span><span class="sxs-lookup"><span data-stu-id="20dce-156">Select **Build**</span></span>
    - <span data-ttu-id="20dce-157">Wählen Sie den Speicherort für den neuen Build im Datei-Explorer aus.</span><span class="sxs-lookup"><span data-stu-id="20dce-157">Choose the location for the new build in File Explorer</span></span>

    ![Einstellungen für eigenständigen Build](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="20dce-159">Eine neue ausführbare Unity-Datei wird erstellt, um Ihre App zu starten. Wählen Sie die ausführbare Unity-Datei im Datei-Explorer aus.</span><span class="sxs-lookup"><span data-stu-id="20dce-159">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![Unity-Datei-Explorer](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="20dce-161">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="20dce-161">See also</span></span>

- [<span data-ttu-id="20dce-162">Android- und iOS-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="20dce-162">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="20dce-163">Leap Motion-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="20dce-163">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="20dce-164">Erkennen von Plattformfunktionen</span><span class="sxs-lookup"><span data-stu-id="20dce-164">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)