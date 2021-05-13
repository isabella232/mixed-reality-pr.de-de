---
title: GettingStartedWithMRTKAndXRSDK
description: Landing Page für MRTK mit XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, XRSDK,
ms.openlocfilehash: fe50de31ae24b415738db64073822b2aff061636
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850426"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="f3447-104">Erste Schritte mit MRTK und XR SDK</span><span class="sxs-lookup"><span data-stu-id="f3447-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="f3447-105">Das XR SDK ist die [neue XR-Pipeline von Unity in Unity 2019.3 und darüber hinaus.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)</span><span class="sxs-lookup"><span data-stu-id="f3447-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="f3447-106">In Unity 2019 bietet es eine Alternative zur vorhandenen XR-Pipeline.</span><span class="sxs-lookup"><span data-stu-id="f3447-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="f3447-107">In Unity 2020 wird es die einzige XR-Pipeline in Unity.</span><span class="sxs-lookup"><span data-stu-id="f3447-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f3447-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f3447-108">Prerequisites</span></span>

<span data-ttu-id="f3447-109">Um mit dem Mixed Reality Toolkit zu beginnen, führen Sie [die angegebenen Schritte](../install-the-tools.md#importing-the-mixed-reality-toolkit) aus, um einem Projekt MRTK hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f3447-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="f3447-110">Konfigurieren von Unity für die XR SDK-Pipeline</span><span class="sxs-lookup"><span data-stu-id="f3447-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="f3447-111">Die XR SDK-Pipeline unterstützt derzeit drei Plattformen: Windows Mixed Reality, Oculus und OpenXR.</span><span class="sxs-lookup"><span data-stu-id="f3447-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="f3447-112">In den folgenden Abschnitten werden die Schritte beschrieben, die zum Konfigurieren des XR SDK für jede Plattform erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f3447-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="f3447-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f3447-113">Windows Mixed Reality</span></span>

<span data-ttu-id="f3447-114">Wechseln Sie zum **unity-Paket-Manager,** und installieren Sie das Windows XR-Plug-In-Paket, das Unterstützung für Windows Mixed Reality im XR SDK hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="f3447-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="f3447-115">Dadurch werden auch einige Abhängigkeitspakete abgerufen.</span><span class="sxs-lookup"><span data-stu-id="f3447-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="f3447-116">Stellen Sie sicher, dass alle folgenden erfolgreich installiert wurden:</span><span class="sxs-lookup"><span data-stu-id="f3447-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="f3447-117">XR-Plug-In-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="f3447-117">XR Plugin Management</span></span>
   * <span data-ttu-id="f3447-118">Windows XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="f3447-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="f3447-119">XR Legacy Input Helpers</span><span class="sxs-lookup"><span data-stu-id="f3447-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="f3447-120">Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).</span><span class="sxs-lookup"><span data-stu-id="f3447-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="f3447-121">Klicken Sie im Fenster Projekteinstellungen auf die Registerkarte XR-Plug-In-Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="f3447-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="f3447-122">Wechseln Sie zu den Universelle Windows-Plattform-Einstellungen, und stellen Sie sicher, dass Windows Mixed Reality unter Plug-In-Anbieter aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="f3447-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="f3447-123">Stellen Sie sicher, dass XR beim Start initialisieren aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="f3447-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="f3447-124">(**_Erforderlich für HoloLens-Remoting im Editor, andernfalls optional_**) Wechseln Sie zu den eigenständigen Einstellungen, und vergewissern Windows Mixed Reality unter Plug-In-Anbieter.</span><span class="sxs-lookup"><span data-stu-id="f3447-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="f3447-125">Stellen Sie außerdem sicher, dass XR beim Start initialisieren überprüft ist.</span><span class="sxs-lookup"><span data-stu-id="f3447-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![XR-Plug-In-Verwaltung mit ausgewählter Registerkarte "Eigenständig"](images/xr-management-img-02.png)

7. <span data-ttu-id="f3447-127">(**_Optional_**) Klicken Sie unter Windows Mixed Reality XR Plug-In Management (XR-Plug-In-Verwaltung) auf die Registerkarte Windows Mixed Reality, und erstellen Sie ein benutzerdefiniertes Einstellungsprofil, um die Standardwerte zu ändern.</span><span class="sxs-lookup"><span data-stu-id="f3447-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="f3447-128">Wenn die Liste der Einstellungen bereits vorhanden ist, muss kein Profil erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="f3447-128">If the list of settings are already there, no profile needs to be created.</span></span>

![XR-Plug-In-Verwaltung mit ausgewählter Registerkarte "Windows"](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="f3447-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="f3447-130">Oculus</span></span>

1. <span data-ttu-id="f3447-131">Befolgen Sie [den Leitfaden Konfigurieren von Oculus Quest in MRTK mithilfe der XR SDK-Pipeline](../supported-devices/oculus-quest-mrtk.md) bis zum Ende.</span><span class="sxs-lookup"><span data-stu-id="f3447-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="f3447-132">In diesem Leitfaden werden die Schritte beschrieben, die zum Konfigurieren von Unity und MRTK für die Verwendung der XR SDK-Pipeline für Oculus Quest erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f3447-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="f3447-133">OpenXR (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="f3447-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3447-134">OpenXR in Unity wird nur unter Unity 2020.2 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3447-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="f3447-135">Derzeit werden auch nur x64- und ARM64-Builds unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3447-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="f3447-136">Befolgen Sie den Leitfaden Verwenden des [Mixed Reality OpenXR-Plug-Ins](/windows/mixed-reality/develop/unity/openxr-getting-started) für Unity, einschließlich der Schritte zum Konfigurieren der XR-Plug-In-Verwaltung und -Optimierung zum Installieren des OpenXR-Plug-Ins in Ihrem Projekt.</span><span class="sxs-lookup"><span data-stu-id="f3447-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="f3447-137">Stellen Sie sicher, dass Folgendes erfolgreich installiert wurde:</span><span class="sxs-lookup"><span data-stu-id="f3447-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="f3447-138">XR-Plug-In-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="f3447-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="f3447-139">OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="f3447-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="f3447-140">Mixed Reality OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="f3447-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="f3447-141">Wechseln Sie zu Bearbeiten > Projekteinstellungen.</span><span class="sxs-lookup"><span data-stu-id="f3447-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="f3447-142">Klicken Sie im Fenster Projekteinstellungen auf die Registerkarte XR-Plug-In-Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="f3447-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="f3447-143">Stellen Sie sicher, dass XR beim Start initialisieren überprüft ist.</span><span class="sxs-lookup"><span data-stu-id="f3447-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="f3447-144">(**_Optional_**) Wenn Sie HoloLens 2 als Ziel verwenden, stellen Sie sicher, dass Sie sich auf der UWP-Plattform befindet, und wählen Sie Microsoft HoloLens Featuresatz aus.</span><span class="sxs-lookup"><span data-stu-id="f3447-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Plug-In-Verwaltung Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="f3447-146">Wenn Sie über ein bereits vorhandenes Projekt verfügen, das MRTK von UPM verwendet, stellen Sie sicher, dass sich die folgende Zeile in der **link.xml-Datei** im Ordner MixedRealityToolkit.Generated befindet.</span><span class="sxs-lookup"><span data-stu-id="f3447-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="f3447-147">Bei der ersten Veröffentlichung von MRTK und OpenXR werden nur die HoloLens 2 artikulierten Hände und Windows Mixed Reality Motion-Controller nativ unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3447-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="f3447-148">Unterstützung für zusätzliche Hardware wird in zukünftigen Releases hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="f3447-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="f3447-149">Konfigurieren von MRTK für die XR SDK-Pipeline</span><span class="sxs-lookup"><span data-stu-id="f3447-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="f3447-150">Wenn Sie OpenXR verwenden, wählen Sie "DefaultOpenXRConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="f3447-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="f3447-151">Wenn Sie andere XR-Runtimes in der Konfiguration der XR-Plug-In-Verwaltung wie Windows Mixed Reality oder Oculus verwenden, wählen Sie "DefaultXRSDKConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="f3447-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="f3447-152">Diese Profile werden bei Bedarf mit den richtigen Systemen und Anbietern eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="f3447-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="f3447-153">Weitere Informationen zur Profil- und Beispielunterstützung mit dem XR SDK finden Sie in der Dokumentation zu [Profilen.](../features/profiles/profiles.md#xr-sdk)</span><span class="sxs-lookup"><span data-stu-id="f3447-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="f3447-154">Um ein vorhandenes Profil zum XR SDK zu migrieren, sollten die folgenden Dienste und Datenanbieter aktualisiert werden:</span><span class="sxs-lookup"><span data-stu-id="f3447-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="f3447-155">Kamera</span><span class="sxs-lookup"><span data-stu-id="f3447-155">Camera</span></span>

<span data-ttu-id="f3447-156">Von [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="f3447-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Legacykameraeinstellungen](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="f3447-158">zu</span><span class="sxs-lookup"><span data-stu-id="f3447-158">to</span></span>

| <span data-ttu-id="f3447-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f3447-159">OpenXR</span></span> | <span data-ttu-id="f3447-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f3447-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="f3447-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**und**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="f3447-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![XR SDK-Kameraeinstellungen](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="f3447-163">Eingabe</span><span class="sxs-lookup"><span data-stu-id="f3447-163">Input</span></span>

<span data-ttu-id="f3447-164">Von [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="f3447-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Legacyeingabeeinstellungen](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="f3447-166">zu</span><span class="sxs-lookup"><span data-stu-id="f3447-166">to</span></span>

| <span data-ttu-id="f3447-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f3447-167">OpenXR</span></span> | <span data-ttu-id="f3447-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f3447-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="f3447-169">__OpenXR:__</span><span class="sxs-lookup"><span data-stu-id="f3447-169">__OpenXR__:</span></span>

![OpenXR-Eingabeeinstellungen](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="f3447-171">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="f3447-171">__Windows Mixed Reality__:</span></span>

![XR SDK-Eingabeeinstellungen](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="f3447-173">Grenze</span><span class="sxs-lookup"><span data-stu-id="f3447-173">Boundary</span></span>

<span data-ttu-id="f3447-174">Von [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="f3447-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Legacy-Begrenzungseinstellungen](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="f3447-176">zu</span><span class="sxs-lookup"><span data-stu-id="f3447-176">to</span></span>

| <span data-ttu-id="f3447-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f3447-177">OpenXR</span></span> | <span data-ttu-id="f3447-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f3447-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK-Begrenzungseinstellungen](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="f3447-180">Räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="f3447-180">Spatial awareness</span></span>

<span data-ttu-id="f3447-181">Von [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="f3447-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Legacyeinstellungen für räumliche Wahrnehmung](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="f3447-183">zu</span><span class="sxs-lookup"><span data-stu-id="f3447-183">to</span></span>

| <span data-ttu-id="f3447-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f3447-184">OpenXR</span></span> | <span data-ttu-id="f3447-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f3447-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="f3447-186">In Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="f3447-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Einstellungen für räumliche Wahrnehmung im XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="f3447-188">Controllerzuordnungen</span><span class="sxs-lookup"><span data-stu-id="f3447-188">Controller mappings</span></span>

<span data-ttu-id="f3447-189">Wenn Sie benutzerdefinierte Controllerzuordnungsprofile verwenden, öffnen Sie eines davon, und führen Sie das Menüelement Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles aus, um sicherzustellen, dass die neuen XR SDK-Controllertypen definiert sind.</span><span class="sxs-lookup"><span data-stu-id="f3447-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3447-190">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f3447-190">See also</span></span>

* [<span data-ttu-id="f3447-191">Erste Schritte mit der AR-Entwicklung in Unity</span><span class="sxs-lookup"><span data-stu-id="f3447-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="f3447-192">Erste Schritte mit der VR-Entwicklung in Unity</span><span class="sxs-lookup"><span data-stu-id="f3447-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)