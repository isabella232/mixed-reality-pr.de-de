---
title: UsingARFoundation
description: Dokumentation zur Verwendung von ARFoundation in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, AR Core, AR Kit
ms.openlocfilehash: d96c5cab2439b581c0de9d59a1a349abccf34fb5
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852366"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="b5f0d-104">Konfigurieren des MRTK für iOS und Android [Experimentell]</span><span class="sxs-lookup"><span data-stu-id="b5f0d-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="b5f0d-105">Installieren erforderlicher Pakete</span><span class="sxs-lookup"><span data-stu-id="b5f0d-105">Install required packages</span></span>

1. <span data-ttu-id="b5f0d-106">Laden Sie das **Paket Microsoft.MixedReality.Toolkit.Unity.Foundation** von [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) oder dem Unity-Projekt herunter, und [importieren Sie es Paket-Manager](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="b5f0d-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="b5f0d-107">Installieren Sie im Unity Paket-Manager (UPM) die folgenden Pakete:</span><span class="sxs-lookup"><span data-stu-id="b5f0d-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="b5f0d-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="b5f0d-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-109">**Android**</span></span> | <span data-ttu-id="b5f0d-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-110">**iOS**</span></span> | <span data-ttu-id="b5f0d-111">Kommentare</span><span class="sxs-lookup"><span data-stu-id="b5f0d-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="b5f0d-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="b5f0d-112">AR Foundation</span></span>  <br/> <span data-ttu-id="b5f0d-113">Version: 1.5.0 – Preview 6</span><span class="sxs-lookup"><span data-stu-id="b5f0d-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="b5f0d-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="b5f0d-114">AR Foundation</span></span>  <br/> <span data-ttu-id="b5f0d-115">Version: 1.5.0 – Preview 6</span><span class="sxs-lookup"><span data-stu-id="b5f0d-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="b5f0d-116">Für Unity 2018.4 ist dieses Paket als Vorschauversion enthalten.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="b5f0d-117">So zeigen Sie das Paket an: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="b5f0d-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="b5f0d-118">ARCore-XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="b5f0d-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="b5f0d-119">Version: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="b5f0d-119">Version: 2.1.2</span></span> | <span data-ttu-id="b5f0d-120">ARKit XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="b5f0d-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="b5f0d-121">Version: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="b5f0d-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="b5f0d-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="b5f0d-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-123">**Android**</span></span> | <span data-ttu-id="b5f0d-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="b5f0d-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="b5f0d-125">AR Foundation</span></span>  <br/> <span data-ttu-id="b5f0d-126">Version: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="b5f0d-126">Version: 2.1.8</span></span> |  <span data-ttu-id="b5f0d-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="b5f0d-127">AR Foundation</span></span>  <br/> <span data-ttu-id="b5f0d-128">Version: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="b5f0d-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="b5f0d-129">ARCore XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="b5f0d-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="b5f0d-130">Version: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="b5f0d-130">Version: 2.1.11</span></span> | <span data-ttu-id="b5f0d-131">ARKit XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="b5f0d-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="b5f0d-132">Version: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="b5f0d-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="b5f0d-133">**Unity 2020.1.x (derzeit nicht formal unterstützt, nur zu Informationszwecken enthalten)**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="b5f0d-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-134">**Android**</span></span> | <span data-ttu-id="b5f0d-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="b5f0d-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="b5f0d-136">AR Foundation</span></span>  <br/> <span data-ttu-id="b5f0d-137">Version: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="b5f0d-137">Version: 3.1.3</span></span> |  <span data-ttu-id="b5f0d-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="b5f0d-138">AR Foundation</span></span>  <br/> <span data-ttu-id="b5f0d-139">Version: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="b5f0d-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="b5f0d-140">ARCore XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="b5f0d-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="b5f0d-141">Version: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="b5f0d-141">Version: 3.1.4</span></span> | <span data-ttu-id="b5f0d-142">ARKit XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="b5f0d-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="b5f0d-143">Version: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="b5f0d-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="b5f0d-144">Aktualisieren Sie die VON UNITYAR definierten MRTK-Skripts, indem Sie das Menüelement **aufrufen: Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="b5f0d-145">Aktivieren des Unity AR-Kameraeinstellungsanbieters</span><span class="sxs-lookup"><span data-stu-id="b5f0d-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="b5f0d-146">Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="b5f0d-147">Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="b5f0d-148">Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="b5f0d-150">Wählen **Sie Kopieren und anpassen aus,** um das MRTK-Profil zu klonen, um die benutzerdefinierte Konfiguration zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Klonen des MRTK-Profils](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="b5f0d-152">Klicken **Sie neben** dem Kameraprofil auf Klonen.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-152">Select **Clone** next to the Camera Profile.</span></span>

    ![Klonen des MRTK-Kameraprofils](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="b5f0d-154">Navigieren Sie im Inspektorbereich zum Abschnitt Kamerasystem, und erweitern Sie den Abschnitt **Kameraeinstellungsanbieter.**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Erweitern von Einstellungsanbietern](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="b5f0d-156">Klicken **Sie auf Kameraeinstellungsanbieter hinzufügen,** und erweitern Sie den neu hinzugefügten Eintrag **Neue Kameraeinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="b5f0d-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Erweitern des neuen Einstellungsanbieters](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="b5f0d-158">Auswählen des Unity AR-Kameraeinstellungsanbieters</span><span class="sxs-lookup"><span data-stu-id="b5f0d-158">Select the Unity AR Camera Settings provider</span></span>

    ![Auswählen des Unity AR-Einstellungsanbieters](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="b5f0d-160">Weitere Informationen zum Konfigurieren des Unity AR-Kameraeinstellungsanbieters: [Unity AR-Kameraeinstellungsanbieter](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b5f0d-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b5f0d-161">Diese Installation überprüft (wenn die Anwendung gestartet wird), ob sich die AR Foundation-Komponenten in der Szene befinden.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="b5f0d-162">Falls nicht, werden sie automatisch hinzugefügt, damit sie mit ARCore und ARKit funktionieren.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="b5f0d-163">Wenn Sie ein bestimmtes Verhalten festlegen müssen, sollten Sie die benötigten Komponenten selbst hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="b5f0d-164">Weitere Informationen zu AR Foundation-Komponenten und zur Installation finden Sie in dieser [Dokumentation.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)</span><span class="sxs-lookup"><span data-stu-id="b5f0d-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="b5f0d-165">Erstellen einer Szene für Android- und iOS-Geräte</span><span class="sxs-lookup"><span data-stu-id="b5f0d-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="b5f0d-166">Stellen Sie sicher, dass Sie ihrer Szene den UnityAR-Kameraeinstellungsanbieter hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="b5f0d-167">Wechseln der Plattform zu Android oder iOS in den Unity-Buildeinstellungen</span><span class="sxs-lookup"><span data-stu-id="b5f0d-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="b5f0d-168">Wenn Sie die Plattform wechseln, sollte das MRTK-Projektkonfigurationsfenster mit Einstellungen für die ausgewählte Plattform angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="b5f0d-169">Klicken Sie auf Übernehmen, um plattformspezifische Einstellungen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="b5f0d-170">iOS-Projektkonfiguratoreinstellungen</span><span class="sxs-lookup"><span data-stu-id="b5f0d-170">iOS Project Configurator Settings</span></span>

    ![iOS-Projektkonfigurator](../features/images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="b5f0d-172">Nach dem Wechseln der Plattform für Android sind keine weiteren Schritte erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="b5f0d-173">Wenn die Plattform iOS ist, deaktivieren Sie > Projekteinstellungen bearbeiten > Player > Andere Einstellungen, und **deaktivieren Sie** unter dem Header Optimierung die Option Strip Engine Code (Engine-Code löschen).</span><span class="sxs-lookup"><span data-stu-id="b5f0d-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![iOS-Einstellungen](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="b5f0d-175">Das Deaktivieren von Strip Engine Code ist die kurzfristige Lösung für einen Fehler in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span><span class="sxs-lookup"><span data-stu-id="b5f0d-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="b5f0d-176">Wir arbeiten an einer langfristigen Lösung.</span><span class="sxs-lookup"><span data-stu-id="b5f0d-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="b5f0d-177">Erstellen und Ausführen der Szene</span><span class="sxs-lookup"><span data-stu-id="b5f0d-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="b5f0d-178">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b5f0d-178">See also</span></span>

- [<span data-ttu-id="b5f0d-179">Unity AR-Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="b5f0d-179">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
