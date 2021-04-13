---
title: Gettingstartedwithmrtkandxrsdk
description: Landing Page für mrtk mit xrsdk
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, hololens, hololens 2, Mixed Reality, Development, mrtk, xrsdk,
ms.openlocfilehash: d5ab9bf51828c84759b72e87e1c41f885c7d6738
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300413"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="70927-104">Einführung in das mrtk-und XR SDK</span><span class="sxs-lookup"><span data-stu-id="70927-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="70927-105">Das XR SDK ist die [neue Pipeline Pipeline von Unity in Unity 2019,3 und](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)höher.</span><span class="sxs-lookup"><span data-stu-id="70927-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="70927-106">In Unity 2019 bietet es eine Alternative zu der vorhandenen Pipeline Pipeline.</span><span class="sxs-lookup"><span data-stu-id="70927-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="70927-107">In Unity 2020 wird es zur einzigen Pipeline Pipeline in Unity.</span><span class="sxs-lookup"><span data-stu-id="70927-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="70927-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="70927-108">Prerequisites</span></span>

<span data-ttu-id="70927-109">Um mit dem Mixed Reality Toolkit zu beginnen, führen Sie [die angegebenen Schritte](../install-the-tools.md#importing-the-mixed-reality-toolkit) aus, um mrtk einem Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="70927-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="70927-110">Konfigurieren von Unity für die XR SDK-Pipeline</span><span class="sxs-lookup"><span data-stu-id="70927-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="70927-111">Die XR SDK-Pipeline unterstützt derzeit drei Plattformen: Windows Mixed Reality, oculus und openxr.</span><span class="sxs-lookup"><span data-stu-id="70927-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="70927-112">In den folgenden Abschnitten werden die erforderlichen Schritte zum Konfigurieren des XR SDK für jede Plattform behandelt.</span><span class="sxs-lookup"><span data-stu-id="70927-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="70927-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="70927-113">Windows Mixed Reality</span></span>

<span data-ttu-id="70927-114">Wechseln Sie in **den Paket-Manager von Unity** , und installieren Sie das Windows-XR-Plug-in-Paket, das die Unterstützung für Windows Mixed Reality auf dem</span><span class="sxs-lookup"><span data-stu-id="70927-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="70927-115">Hierdurch werden auch einige Abhängigkeits Pakete abgerufen.</span><span class="sxs-lookup"><span data-stu-id="70927-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="70927-116">Stellen Sie sicher, dass Folgendes installiert ist:</span><span class="sxs-lookup"><span data-stu-id="70927-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="70927-117">XR-Plug-in</span><span class="sxs-lookup"><span data-stu-id="70927-117">XR Plugin Management</span></span>
   * <span data-ttu-id="70927-118">Windows-XR-Plugin</span><span class="sxs-lookup"><span data-stu-id="70927-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="70927-119">XR-Legacy-Eingabe Hilfen</span><span class="sxs-lookup"><span data-stu-id="70927-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="70927-120">Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).</span><span class="sxs-lookup"><span data-stu-id="70927-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="70927-121">Klicken Sie im Fenster "Projekteinstellungen" auf die Registerkarte "XR-Plug-in-Verwaltung".</span><span class="sxs-lookup"><span data-stu-id="70927-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="70927-122">Wechseln Sie zu den universelle Windows-Plattform Einstellungen, und vergewissern Sie sich, dass Windows Mixed Reality unter Plug-in-Anbieter aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="70927-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="70927-123">Vergewissern Sie sich, dass beim Start die Option XR initialisieren aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="70927-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="70927-124">(**_Erforderlich für in-Editor-hololens-Remoting, andernfalls optional_**) Wechseln Sie zu den eigenständigen Einstellungen, und stellen Sie sicher, dass Windows Mixed Reality unter Plug-in-Anbieter aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="70927-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="70927-125">Vergewissern Sie sich außerdem, dass beim Start die Option XR initialisieren aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="70927-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![Verwaltung von XR-Plug-ins mit ausgewählter Registerkarte](images/xr-management-img-02.png)

7. <span data-ttu-id="70927-127">(**_Optional_**) Klicken Sie unter "XR Plug-in Management" auf die Registerkarte Windows Mixed Reality, und erstellen Sie ein benutzerdefiniertes Einstellungs Profil, um die Standardwerte zu</span><span class="sxs-lookup"><span data-stu-id="70927-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="70927-128">Wenn die Liste der Einstellungen bereits vorhanden ist, muss kein Profil erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="70927-128">If the list of settings are already there, no profile needs to be created.</span></span>

![XR-Plugin-Verwaltung mit ausgewählter Windows-Registerkarte](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="70927-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="70927-130">Oculus</span></span>

1. <span data-ttu-id="70927-131">Befolgen Sie die Anweisungen im Leitfaden zum [Konfigurieren von Oculus Quest in mrtk mithilfe des Pipelines](../features/cross-platform/oculus-quest-mrtk.md) für das XR-SDK.</span><span class="sxs-lookup"><span data-stu-id="70927-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../features/cross-platform/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="70927-132">In diesem Leitfaden werden die Schritte beschrieben, die erforderlich sind, um Unity und mrtk für die Verwendung der XR SDK-Pipeline für die Oculus Quest zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="70927-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="70927-133">Openxr (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="70927-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70927-134">Openxr in Unity wird nur in Unity 2020,2 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="70927-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="70927-135">Derzeit werden nur x64-und ARM64-Builds unterstützt.</span><span class="sxs-lookup"><span data-stu-id="70927-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="70927-136">Befolgen Sie die Anweisungen unter [Verwenden des gemischten Reality openxr-Plug-Ins für Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , einschließlich der Schritte zum Konfigurieren der Verwaltung und Optimierung von XR-Plug-Ins für die Installation des openxr-Plug-Ins für Ihr Projekt</span><span class="sxs-lookup"><span data-stu-id="70927-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="70927-137">Stellen Sie sicher, dass Folgendes erfolgreich installiert wurde:</span><span class="sxs-lookup"><span data-stu-id="70927-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="70927-138">XR-Plug-in</span><span class="sxs-lookup"><span data-stu-id="70927-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="70927-139">Openxr-Plugin</span><span class="sxs-lookup"><span data-stu-id="70927-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="70927-140">Mixed Reality openxr-Plug-in</span><span class="sxs-lookup"><span data-stu-id="70927-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="70927-141">Wechseln Sie zu Edit > Project Settings.</span><span class="sxs-lookup"><span data-stu-id="70927-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="70927-142">Klicken Sie im Fenster "Projekteinstellungen" auf die Registerkarte "XR-Plug-in-Verwaltung".</span><span class="sxs-lookup"><span data-stu-id="70927-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="70927-143">Vergewissern Sie sich, dass beim Start die Option XR initialisieren aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="70927-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="70927-144">(**_Optional_**) Wenn Sie auf hololens 2 abzielen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform befinden, und wählen Sie "Microsoft hololens Feature</span><span class="sxs-lookup"><span data-stu-id="70927-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Plug-in-Management öffnen XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="70927-146">Wenn Sie über ein bereits vorhandenes Projekt verfügen, das mrtk aus UPM verwendet, stellen Sie sicher, dass sich die folgende Zeile in der **link.xml** -Datei befindet, die sich im Ordner "mixedrealitytoolkit. generated" befindet.</span><span class="sxs-lookup"><span data-stu-id="70927-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="70927-147">Für die erste Version von mrtk und openxr werden nur die "hololens 2"-und Windows Mixed Reality-Bewegungs Controller nativ unterstützt.</span><span class="sxs-lookup"><span data-stu-id="70927-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="70927-148">Unterstützung für zusätzliche Hardware wird in zukünftigen Versionen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="70927-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="70927-149">Konfigurieren von mrtk für die XR SDK-Pipeline</span><span class="sxs-lookup"><span data-stu-id="70927-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="70927-150">Wenn Sie openxr verwenden, wählen Sie "defaultoperxrconfigurationprofile" als aktives Profil aus, oder Klonen Sie es, um Anpassungen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="70927-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="70927-151">Wenn Sie andere XR-Laufzeiten in der Konfigurations Konfiguration des XR-Plug-Ins verwenden, wie z. b. Windows Mixed Reality oder Oculus, wählen Sie "defaultxrsdkconfigurationprofile" als aktives Profil aus, oder Klonen Sie es, um Anpassungen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="70927-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="70927-152">Diese Profile werden bei Bedarf mit den richtigen Systemen und Anbietern eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="70927-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="70927-153">Weitere Informationen zur Profil-und Beispiel Unterstützung mit dem XR SDK finden Sie in der Dokumentation zu [Profilen](../features/profiles/profiles.md#xr-sdk) .</span><span class="sxs-lookup"><span data-stu-id="70927-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="70927-154">Um ein vorhandenes Profil zu dem XR SDK zu migrieren, sollten die folgenden Dienste und Datenanbieter aktualisiert werden:</span><span class="sxs-lookup"><span data-stu-id="70927-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="70927-155">Kamera</span><span class="sxs-lookup"><span data-stu-id="70927-155">Camera</span></span>

<span data-ttu-id="70927-156">Von [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="70927-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Ältere Kameraeinstellungen](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="70927-158">in</span><span class="sxs-lookup"><span data-stu-id="70927-158">to</span></span>

| <span data-ttu-id="70927-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="70927-159">OpenXR</span></span> | <span data-ttu-id="70927-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="70927-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="70927-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**und**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="70927-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![XR SDK-Kameraeinstellungen](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="70927-163">Eingabe</span><span class="sxs-lookup"><span data-stu-id="70927-163">Input</span></span>

<span data-ttu-id="70927-164">Von [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="70927-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Ältere Eingabeeinstellungen](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="70927-166">in</span><span class="sxs-lookup"><span data-stu-id="70927-166">to</span></span>

| <span data-ttu-id="70927-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="70927-167">OpenXR</span></span> | <span data-ttu-id="70927-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="70927-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="70927-169">__Openxr__:</span><span class="sxs-lookup"><span data-stu-id="70927-169">__OpenXR__:</span></span>

![Openxr-Eingabeeinstellungen](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="70927-171">__Gemischte Windows-Realität__:</span><span class="sxs-lookup"><span data-stu-id="70927-171">__Windows Mixed Reality__:</span></span>

![XR SDK-Eingabeeinstellungen](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="70927-173">Grenze</span><span class="sxs-lookup"><span data-stu-id="70927-173">Boundary</span></span>

<span data-ttu-id="70927-174">Von [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="70927-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Legacy Begrenzungs Einstellungen](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="70927-176">in</span><span class="sxs-lookup"><span data-stu-id="70927-176">to</span></span>

| <span data-ttu-id="70927-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="70927-177">OpenXR</span></span> | <span data-ttu-id="70927-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="70927-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK-Begrenzungs Einstellungen](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="70927-180">Räumliches Bewusstsein</span><span class="sxs-lookup"><span data-stu-id="70927-180">Spatial awareness</span></span>

<span data-ttu-id="70927-181">Von [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="70927-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Legacy Einstellungen für räumliche Informationen](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="70927-183">in</span><span class="sxs-lookup"><span data-stu-id="70927-183">to</span></span>

| <span data-ttu-id="70927-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="70927-184">OpenXR</span></span> | <span data-ttu-id="70927-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="70927-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="70927-186">In Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="70927-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Einstellungen für das XR SDK für räumliche Informationen](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="70927-188">Controller Zuordnungen</span><span class="sxs-lookup"><span data-stu-id="70927-188">Controller mappings</span></span>

<span data-ttu-id="70927-189">Wenn Sie benutzerdefinierte Controller zuordnungsprofile verwenden, öffnen Sie eine von Ihnen, und führen Sie den Menüeintrag Mixed Reality Toolkit-> Utilities-> Update-> Controller Mapping Profiles aus, um sicherzustellen, dass die neuen XR SDK-Controller Typen definiert sind.</span><span class="sxs-lookup"><span data-stu-id="70927-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="70927-190">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="70927-190">See also</span></span>

* [<span data-ttu-id="70927-191">Ersten Einstieg in die Entwicklung von aren in Unity</span><span class="sxs-lookup"><span data-stu-id="70927-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="70927-192">Einstieg in die VR-Entwicklung in Unity</span><span class="sxs-lookup"><span data-stu-id="70927-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)