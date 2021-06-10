---
title: Erste Schritte mit MRTK und XR SDK
description: Landing Page für MRTK mit XR SDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, XRSDK, XR SDK
ms.openlocfilehash: 01aca42ab4e883d26a814a1572d39eda7576ab57
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908383"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="0a3f4-104">Erste Schritte mit MRTK und XR SDK</span><span class="sxs-lookup"><span data-stu-id="0a3f4-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="0a3f4-105">Das XR SDK ist die neue [XR-Pipeline von Unity in Unity 2019.3 und darüber hinaus.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)</span><span class="sxs-lookup"><span data-stu-id="0a3f4-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="0a3f4-106">In Unity 2019 bietet es eine Alternative zur vorhandenen XR-Pipeline.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="0a3f4-107">In Unity 2020 ist dies die einzige XR-Pipeline in Unity.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-107">In Unity 2020, it is the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0a3f4-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0a3f4-108">Prerequisites</span></span>

<span data-ttu-id="0a3f4-109">Um mit dem Mixed Reality Toolkit zu beginnen, führen Sie [die angegebenen](../install-the-tools.md#importing-the-mixed-reality-toolkit) Schritte aus, um MRTK zu einem Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="0a3f4-110">Konfigurieren von Unity für die XR SDK-Pipeline</span><span class="sxs-lookup"><span data-stu-id="0a3f4-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="0a3f4-111">Die XR SDK-Pipeline unterstützt derzeit drei Plattformen: Windows Mixed Reality, Oculus und OpenXR.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="0a3f4-112">In den folgenden Abschnitten werden die Schritte beschrieben, die zum Konfigurieren des XR SDK für jede Plattform erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="0a3f4-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="0a3f4-113">Windows Mixed Reality</span></span>

<span data-ttu-id="0a3f4-114">Wechseln Sie zum **Unity-Paket-Manager,** und installieren Sie das Windows XR-Plug-In-Paket, das Unterstützung für Windows Mixed Reality XR SDK hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="0a3f4-115">Dadurch werden auch einige Abhängigkeitspakete heruntergefahren.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-115">This will pull down a few dependency packages as well.</span></span>

1. <span data-ttu-id="0a3f4-116">Stellen Sie sicher, dass alle folgenden Erfolgreich installiert wurden:</span><span class="sxs-lookup"><span data-stu-id="0a3f4-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="0a3f4-117">XR-Plug-In-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="0a3f4-117">XR Plugin Management</span></span>
   * <span data-ttu-id="0a3f4-118">Windows XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="0a3f4-119">XR Legacy-Eingabehilfen</span><span class="sxs-lookup"><span data-stu-id="0a3f4-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="0a3f4-120">Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).</span><span class="sxs-lookup"><span data-stu-id="0a3f4-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="0a3f4-121">Klicken Sie im Fenster Projekteinstellungen auf die Registerkarte XR-Plug-In-Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="0a3f4-122">Wechseln Sie zu den Universelle Windows-Plattform, und vergewissern Sie sich, Windows Mixed Reality Unter Plug-In-Anbieter die Einstellung "Plug-In-Anbieter" (Plug-In-Anbieter) überprüft ist.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="0a3f4-123">Stellen Sie sicher, dass XR beim Start initialisieren überprüft ist.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="0a3f4-124">(**_Erforderlich für HoloLens-Remoting im Editor, andernfalls optional_**) Wechseln Sie zu den eigenständigen Einstellungen, und vergewissern Windows Mixed Reality unter Plug-In-Anbieter.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="0a3f4-125">Stellen Sie außerdem sicher, dass XR beim Start initialisieren überprüft ist.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-125">Also ensure that Initialize XR on Startup is checked.</span></span>

    ![XR-Plug-In-Verwaltung mit ausgewählter Registerkarte "Eigenständig"](images/xr-management-img-02.png)

7. <span data-ttu-id="0a3f4-127">(**_Optional_**) Klicken Sie unter Windows Mixed Reality XR Plug-In Management (XR-Plug-In-Verwaltung) auf die Registerkarte Windows Mixed Reality, und erstellen Sie ein benutzerdefiniertes Einstellungsprofil, um die Standardwerte zu ändern.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="0a3f4-128">Wenn die Liste der Einstellungen bereits vorhanden ist, muss kein Profil erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-128">If the list of settings are already there, no profile needs to be created.</span></span>

    ![XR-Plug-In-Verwaltung mit ausgewählter Registerkarte "Windows"](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="0a3f4-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="0a3f4-130">Oculus</span></span>

1. <span data-ttu-id="0a3f4-131">Befolgen Sie [den Leitfaden Konfigurieren von Oculus Quest in MRTK mithilfe des XR SDK-Pipelineleitfadens](../supported-devices/oculus-quest-mrtk.md) bis zum Ende.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="0a3f4-132">In diesem Leitfaden werden die Schritte beschrieben, die zum Konfigurieren von Unity und MRTK für die Verwendung der XR SDK-Pipeline für Oculus Quest erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="0a3f4-133">OpenXR (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="0a3f4-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a3f4-134">OpenXR in Unity wird nur unter Unity 2020.2 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
> <span data-ttu-id="0a3f4-135">Außerdem werden nur x64-, ARM- und ARM64-Builds unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-135">It also only supports x64, ARM, and ARM64 builds.</span></span>

1. <span data-ttu-id="0a3f4-136">Befolgen Sie den Leitfaden Verwenden des [Mixed Reality OpenXR-Plug-Ins](/windows/mixed-reality/develop/unity/openxr-getting-started) für Unity, einschließlich der Schritte zum Konfigurieren der XR-Plug-In-Verwaltung und -Optimierung zum Installieren des OpenXR-Plug-Ins in Ihrem Projekt.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="0a3f4-137">Stellen Sie sicher, dass Folgendes erfolgreich installiert wurde:</span><span class="sxs-lookup"><span data-stu-id="0a3f4-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="0a3f4-138">XR-Plug-In-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="0a3f4-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="0a3f4-139">OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="0a3f4-140">Mixed Reality OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="0a3f4-141">Wechseln Sie zu Bearbeiten > Projekteinstellungen.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="0a3f4-142">Klicken Sie im Fenster Projekteinstellungen auf die Registerkarte XR-Plug-In-Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="0a3f4-143">Stellen Sie sicher, dass XR beim Start initialisieren überprüft ist.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="0a3f4-144">(**_Optional_**) Wenn Sie HoloLens 2 auswählen, stellen Sie sicher, dass Sie auf der UWP-Plattform sind, und wählen Sie Microsoft HoloLens Feature Set (Featuresatz) aus.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![Plug-In-Verwaltung : OpenXR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="0a3f4-146">Wenn Sie über ein bereits vorhandenes Projekt verfügen, das MRTK aus UPM verwendet, stellen Sie sicher, dass sich die folgende Zeile in der **link.xml-Datei** befindet, die sich im Ordner MixedRealityToolkit.Generated befindet.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="0a3f4-147">Bei der ersten Veröffentlichung von MRTK und OpenXR werden nur die HoloLens 2 und Windows Mixed Reality Motion-Controller nativ unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="0a3f4-148">Unterstützung für zusätzliche Hardware wird in zukünftigen Releases hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="0a3f4-149">Konfigurieren des MRTK für die XR SDK-Pipeline</span><span class="sxs-lookup"><span data-stu-id="0a3f4-149">Configuring MRTK for the XR SDK pipeline</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="0a3f4-150">Verwenden Sie eines der MRTK-Standardprofile, die alle über die XR-Pipelines von Unity konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-150">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="0a3f4-151">Die vorherigen "DefaultOpenXRConfigurationProfile" und "DefaultXRSDKConfigurationProfile" sind jetzt als veraltet gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-151">The previous "DefaultOpenXRConfigurationProfile" and "DefaultXRSDKConfigurationProfile" are now labeled obsolete.</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="0a3f4-152">Wenn Sie OpenXR verwenden, wählen Sie "DefaultOpenXRConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vornehmen zu können.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-152">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="0a3f4-153">Wenn Sie andere XR-Runtimes in der Konfiguration der XR-Plug-In-Verwaltung wie Windows Mixed Reality oder Oculus verwenden, wählen Sie "DefaultXRSDKConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vornehmen zu können.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-153">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="0a3f4-154">Diese Profile werden bei Bedarf mit den richtigen Systemen und Anbietern eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-154">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="0a3f4-155">Weitere [Informationen zur Profil-](../features/profiles/profiles.md#xr-sdk) und Beispielunterstützung mit dem XR SDK finden Sie in der Dokumentation zu Profilen.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-155">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>
::: moniker-end

<span data-ttu-id="0a3f4-156">Um ein vorhandenes Profil zum XR SDK zu migrieren, sollten die folgenden Dienste und Datenanbieter aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-156">To migrate an existing profile to XR SDK, the following services and data providers should be updated.</span></span>
::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="0a3f4-157">Sie können die neuen Datenanbieter auf der Registerkarte XR SDK in Unity 2019 oder in der Haupt-/Nur-Ansicht in Unity 2020 und darüber anzeigen, wo legacy XR nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-157">You will be able to see the new data providers under the XR SDK tab in Unity 2019, or in the main/only view in Unity 2020+, where legacy XR doesn't exist.</span></span>

![Registerkarte "XR SDK"](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a><span data-ttu-id="0a3f4-159">Kamera</span><span class="sxs-lookup"><span data-stu-id="0a3f4-159">Camera</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="0a3f4-160">Fügen Sie die folgenden Datenanbieter hinzu:</span><span class="sxs-lookup"><span data-stu-id="0a3f4-160">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="0a3f4-161">Von [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="0a3f4-161">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![Legacykameraeinstellungen](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="0a3f4-163">zu</span><span class="sxs-lookup"><span data-stu-id="0a3f4-163">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="0a3f4-164">OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-164">OpenXR Plugin</span></span> | <span data-ttu-id="0a3f4-165">Windows XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-165">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="0a3f4-166">OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-166">OpenXR Plugin</span></span> | <span data-ttu-id="0a3f4-167">Windows XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-167">Windows XR Plugin</span></span> |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![XR SDK-Kameraeinstellungen](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="0a3f4-169">Eingabe</span><span class="sxs-lookup"><span data-stu-id="0a3f4-169">Input</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="0a3f4-170">Fügen Sie die folgenden Datenanbieter hinzu:</span><span class="sxs-lookup"><span data-stu-id="0a3f4-170">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="0a3f4-171">Von [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="0a3f4-171">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![Legacyeingabeeinstellungen](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="0a3f4-173">zu</span><span class="sxs-lookup"><span data-stu-id="0a3f4-173">to</span></span>
::: moniker-end

| <span data-ttu-id="0a3f4-174">OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-174">OpenXR Plugin</span></span> | <span data-ttu-id="0a3f4-175">Windows XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-175">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="0a3f4-176">__OpenXR:__</span><span class="sxs-lookup"><span data-stu-id="0a3f4-176">__OpenXR__:</span></span>

![OpenXR-Eingabeeinstellungen](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="0a3f4-178">__Windows Mixed Reality__:</span><span class="sxs-lookup"><span data-stu-id="0a3f4-178">__Windows Mixed Reality__:</span></span>

![XR SDK-Eingabeeinstellungen](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="0a3f4-180">Grenze</span><span class="sxs-lookup"><span data-stu-id="0a3f4-180">Boundary</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="0a3f4-181">Fügen Sie die folgenden Datenanbieter hinzu:</span><span class="sxs-lookup"><span data-stu-id="0a3f4-181">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="0a3f4-182">Von [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="0a3f4-182">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![Legacy-Begrenzungseinstellungen](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="0a3f4-184">zu</span><span class="sxs-lookup"><span data-stu-id="0a3f4-184">to</span></span>
::: moniker-end

| <span data-ttu-id="0a3f4-185">OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-185">OpenXR Plugin</span></span> | <span data-ttu-id="0a3f4-186">Windows XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-186">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK-Begrenzungseinstellungen](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="0a3f4-188">Räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="0a3f4-188">Spatial awareness</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="0a3f4-189">Fügen Sie die folgenden Datenanbieter hinzu:</span><span class="sxs-lookup"><span data-stu-id="0a3f4-189">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="0a3f4-190">Von [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="0a3f4-190">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![Legacyeinstellungen für räumliche Wahrnehmung](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="0a3f4-192">zu</span><span class="sxs-lookup"><span data-stu-id="0a3f4-192">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="0a3f4-193">OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-193">OpenXR Plugin</span></span> | <span data-ttu-id="0a3f4-194">Windows XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-194">Windows XR Plugin</span></span> |
|---------------|-------------------|
| <span data-ttu-id="0a3f4-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (für UWP)</span><span class="sxs-lookup"><span data-stu-id="0a3f4-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (for UWP)</span></span> | <span data-ttu-id="0a3f4-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (für UWP)</span><span class="sxs-lookup"><span data-stu-id="0a3f4-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (for UWP)</span></span> |
| <span data-ttu-id="0a3f4-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (für Nicht-UWP)</span><span class="sxs-lookup"><span data-stu-id="0a3f4-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (for non-UWP)</span></span> | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="0a3f4-198">OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-198">OpenXR Plugin</span></span> | <span data-ttu-id="0a3f4-199">Windows XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="0a3f4-199">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![Einstellungen für räumliche Wahrnehmung im XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="0a3f4-201">Controllerzuordnungen</span><span class="sxs-lookup"><span data-stu-id="0a3f4-201">Controller mappings</span></span>

<span data-ttu-id="0a3f4-202">Wenn Sie benutzerdefinierte Controllerzuordnungsprofile verwenden, öffnen Sie eines dieser Profile, und führen Sie das Menüelement Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles aus, um sicherzustellen, dass die neuen XR SDK-Controllertypen definiert sind.</span><span class="sxs-lookup"><span data-stu-id="0a3f4-202">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a3f4-203">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0a3f4-203">See also</span></span>

* [<span data-ttu-id="0a3f4-204">Erste Schritte mit der AR-Entwicklung in Unity</span><span class="sxs-lookup"><span data-stu-id="0a3f4-204">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="0a3f4-205">Erste Schritte mit der VR-Entwicklung in Unity</span><span class="sxs-lookup"><span data-stu-id="0a3f4-205">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
