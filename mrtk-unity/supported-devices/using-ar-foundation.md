---
title: Verwenden von AR Foundation
description: Dokumentation zur Verwendung von ARFoundation in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 0f02eb94d95c2900348adaa9e1a02c3e54832a96
ms.sourcegitcommit: 62beb626b2db6ce7df86014bd22bf1946b8906b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2021
ms.locfileid: "110207450"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="2d433-104">Konfigurieren des MRTK für iOS und Android [Experimentell]</span><span class="sxs-lookup"><span data-stu-id="2d433-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="2d433-105">Installieren erforderlicher Pakete</span><span class="sxs-lookup"><span data-stu-id="2d433-105">Install required packages</span></span>

1. <span data-ttu-id="2d433-106">Laden Sie das **Paket Microsoft.MixedReality.Toolkit.Unity.Foundation** von [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) oder dem Unity-Projekt herunter, und [importieren Sie es Paket-Manager](../configuration/usingupm.md)</span><span class="sxs-lookup"><span data-stu-id="2d433-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="2d433-107">Installieren Sie im Unity Paket-Manager (UPM) die folgenden Pakete:</span><span class="sxs-lookup"><span data-stu-id="2d433-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="2d433-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="2d433-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="2d433-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="2d433-109">**Android**</span></span> | <span data-ttu-id="2d433-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="2d433-110">**iOS**</span></span> | <span data-ttu-id="2d433-111">Kommentare</span><span class="sxs-lookup"><span data-stu-id="2d433-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="2d433-112">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2d433-112">AR Foundation</span></span>  <br/> <span data-ttu-id="2d433-113">Version: 1.5.0 – Preview 6</span><span class="sxs-lookup"><span data-stu-id="2d433-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="2d433-114">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2d433-114">AR Foundation</span></span>  <br/> <span data-ttu-id="2d433-115">Version: 1.5.0 – Preview 6</span><span class="sxs-lookup"><span data-stu-id="2d433-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="2d433-116">Für Unity 2018.4 ist dieses Paket als Vorschauversion enthalten.</span><span class="sxs-lookup"><span data-stu-id="2d433-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="2d433-117">So zeigen Sie das Paket an: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="2d433-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="2d433-118">ARCore-XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="2d433-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="2d433-119">Version: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="2d433-119">Version: 2.1.2</span></span> | <span data-ttu-id="2d433-120">ARKit XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="2d433-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="2d433-121">Version: 2.1.2</span><span class="sxs-lookup"><span data-stu-id="2d433-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="2d433-122">**Unity 2019.4.x**</span><span class="sxs-lookup"><span data-stu-id="2d433-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="2d433-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="2d433-123">**Android**</span></span> | <span data-ttu-id="2d433-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="2d433-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="2d433-125">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2d433-125">AR Foundation</span></span>  <br/> <span data-ttu-id="2d433-126">Version: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="2d433-126">Version: 2.1.8</span></span> |  <span data-ttu-id="2d433-127">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2d433-127">AR Foundation</span></span>  <br/> <span data-ttu-id="2d433-128">Version: 2.1.8</span><span class="sxs-lookup"><span data-stu-id="2d433-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="2d433-129">ARCore XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="2d433-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="2d433-130">Version: 2.1.11</span><span class="sxs-lookup"><span data-stu-id="2d433-130">Version: 2.1.11</span></span> | <span data-ttu-id="2d433-131">ARKit XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="2d433-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="2d433-132">Version: 2.1.9</span><span class="sxs-lookup"><span data-stu-id="2d433-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="2d433-133">**Unity 2020.1.x (derzeit nicht formal unterstützt, nur zu Informationszwecken enthalten)**</span><span class="sxs-lookup"><span data-stu-id="2d433-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="2d433-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="2d433-134">**Android**</span></span> | <span data-ttu-id="2d433-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="2d433-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="2d433-136">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2d433-136">AR Foundation</span></span>  <br/> <span data-ttu-id="2d433-137">Version: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="2d433-137">Version: 3.1.3</span></span> |  <span data-ttu-id="2d433-138">AR Foundation</span><span class="sxs-lookup"><span data-stu-id="2d433-138">AR Foundation</span></span>  <br/> <span data-ttu-id="2d433-139">Version: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="2d433-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="2d433-140">ARCore XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="2d433-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="2d433-141">Version: 3.1.4</span><span class="sxs-lookup"><span data-stu-id="2d433-141">Version: 3.1.4</span></span> | <span data-ttu-id="2d433-142">ARKit XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="2d433-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="2d433-143">Version: 3.1.3</span><span class="sxs-lookup"><span data-stu-id="2d433-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="2d433-144">Aktualisieren Sie die VON UNITYAR definierten MRTK-Skripts, indem Sie das Menüelement **aufrufen: Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span><span class="sxs-lookup"><span data-stu-id="2d433-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![Update Scripting Defines](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="2d433-146">Aktivieren des Unity AR-Kameraeinstellungsanbieters</span><span class="sxs-lookup"><span data-stu-id="2d433-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="2d433-147">In den folgenden Schritten wird davon ausgegangen, dass das MixedRealityToolkit-Objekt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2d433-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="2d433-148">Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="2d433-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="2d433-149">Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="2d433-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="2d433-151">Wählen **Sie Kopieren und Anpassen aus,** um das MRTK-Profil zu klonen, um die benutzerdefinierte Konfiguration zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2d433-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![Klonen des MRTK-Profils](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="2d433-153">Klicken **Sie neben** dem Kameraprofil auf Klonen.</span><span class="sxs-lookup"><span data-stu-id="2d433-153">Select **Clone** next to the Camera Profile.</span></span>

    ![Klonen des MRTK-Kameraprofils](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="2d433-155">Navigieren Sie im Inspektorbereich zum Abschnitt Kamerasystem, und erweitern Sie den Abschnitt **Kameraeinstellungsanbieter.**</span><span class="sxs-lookup"><span data-stu-id="2d433-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Erweitern von Einstellungsanbietern](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="2d433-157">Klicken **Sie auf Kameraeinstellungsanbieter hinzufügen,** und erweitern Sie den neu hinzugefügten Eintrag **Neue Kameraeinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="2d433-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Neuen Einstellungsanbieter erweitern](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="2d433-159">Auswählen des Unity AR-Kameraeinstellungsanbieters</span><span class="sxs-lookup"><span data-stu-id="2d433-159">Select the Unity AR Camera Settings provider</span></span>

    ![Auswählen des Unity AR-Einstellungsanbieters](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="2d433-161">Weitere Informationen zum Konfigurieren des Unity AR-Kameraeinstellungsanbieters: [Unity AR-Kameraeinstellungsanbieter](../features/camera-system/unity-ar-camera-settings.md).</span><span class="sxs-lookup"><span data-stu-id="2d433-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2d433-162">Diese Installation überprüft (wenn die Anwendung gestartet wird), ob sich die AR Foundation-Komponenten in der Szene befinden.</span><span class="sxs-lookup"><span data-stu-id="2d433-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="2d433-163">Falls nicht, werden sie automatisch hinzugefügt, damit sie mit ARCore und ARKit funktionieren.</span><span class="sxs-lookup"><span data-stu-id="2d433-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="2d433-164">Wenn Sie ein bestimmtes Verhalten festlegen müssen, sollten Sie die benötigten Komponenten selbst hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2d433-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="2d433-165">Weitere Informationen zu AR Foundation-Komponenten und zur Installation finden Sie in dieser [Dokumentation.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)</span><span class="sxs-lookup"><span data-stu-id="2d433-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="2d433-166">Erstellen einer Szene für Android- und iOS-Geräte</span><span class="sxs-lookup"><span data-stu-id="2d433-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="2d433-167">Stellen Sie sicher, dass Sie ihrer Szene den UnityAR-Kameraeinstellungsanbieter hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="2d433-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="2d433-168">Wechseln der Plattform zu Android oder iOS in den Unity-Buildeinstellungen</span><span class="sxs-lookup"><span data-stu-id="2d433-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="2d433-169">Stellen Sie sicher, dass der zugeordnete XR-Plug-In-Verwaltungsanbieter aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2d433-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="2d433-170">iOS-XR-Plug-In-Verwaltung:  ![ XR-Plug-In-Verwaltung iOS](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="2d433-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="2d433-171">Erstellen und Ausführen der Szene</span><span class="sxs-lookup"><span data-stu-id="2d433-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="2d433-172">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2d433-172">See also</span></span>

- [<span data-ttu-id="2d433-173">Unity AR-Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="2d433-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
