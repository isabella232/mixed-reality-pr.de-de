---
title: Kamerasystemübersicht
description: Landing Page für kamerasystem in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Kamera,
ms.openlocfilehash: e3b7caacaa9baa67fd81f6d32f3fd8c9f123e66d
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121288"
---
# <a name="camera-system"></a><span data-ttu-id="64e76-104">Kamerasystem</span><span class="sxs-lookup"><span data-stu-id="64e76-104">Camera system</span></span>

<span data-ttu-id="64e76-105">Das Kamerasystem ermöglicht es dem Microsoft Mixed Reality Toolkit, die Kamera der Anwendung für die Verwendung in Mixed Reality-Anwendungen zu konfigurieren und zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="64e76-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="64e76-106">Mithilfe des Kamerasystems können Anwendungen geschrieben werden, um sowohl nicht transparente (z. B. virtuelle Realität) als auch transparente (z.B. Microsoft HoloLens)-Geräte zu unterstützen, ohne Code schreiben zu müssen, um zwischen den einzelnen Anzeigetypen zu unterscheiden und diese zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="64e76-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="64e76-107">Aktivieren des Kamerasystems</span><span class="sxs-lookup"><span data-stu-id="64e76-107">Enabling the camera system</span></span>

<span data-ttu-id="64e76-108">Das Kamerasystem wird vom MixedRealityToolkit-Objekt (oder einer anderen Dienstregistrierungskomponente) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="64e76-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="64e76-109">Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus.</span><span class="sxs-lookup"><span data-stu-id="64e76-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="64e76-110">Die für andere Dienstregistrierungen erforderlichen Schritte können unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="64e76-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="64e76-111">Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="64e76-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK– Konfigurierte Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="64e76-113">Navigieren Sie im Inspektorbereich zum Abschnitt Kamerasystem, und stellen Sie sicher, dass **Kamerasystem** aktivieren aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="64e76-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![Aktivieren des Kamerasystems](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="64e76-115">Wählen Sie die Implementierung des Kamerasystems aus.</span><span class="sxs-lookup"><span data-stu-id="64e76-115">Select the camera system implementation.</span></span> <span data-ttu-id="64e76-116">Die vom MRTK bereitgestellte Standardklassenimplementierung ist `MixedRealityCameraSystem` .</span><span class="sxs-lookup"><span data-stu-id="64e76-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![Auswählen der Kamerasystemimplementierung](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="64e76-118">Auswählen des gewünschten Konfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="64e76-118">Select the desired configuration profile</span></span>

    ![Auswählen des Kamerasystemprofils](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="64e76-120">Konfigurieren des Kamerasystems</span><span class="sxs-lookup"><span data-stu-id="64e76-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="64e76-121">Einstellungsanbieter</span><span class="sxs-lookup"><span data-stu-id="64e76-121">Settings providers</span></span>

![Kameraeinstellungsanbieter](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="64e76-123">Kameraeinstellungsanbieter ermöglichen die plattformspezifische Konfiguration der Kamera.</span><span class="sxs-lookup"><span data-stu-id="64e76-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="64e76-124">Diese Einstellungen können benutzerdefinierte Konfigurationsschritte und/oder Komponenten umfassen.</span><span class="sxs-lookup"><span data-stu-id="64e76-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="64e76-125">Anbieter können hinzugefügt werden, indem Sie auf die **Schaltfläche Add Camera Settings Provider (Anbieter für Kameraeinstellungen hinzufügen)** klicken.</span><span class="sxs-lookup"><span data-stu-id="64e76-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="64e76-126">Sie können entfernt werden, indem Sie auf die Schaltfläche rechts vom **-** Anbieternamen klicken.</span><span class="sxs-lookup"><span data-stu-id="64e76-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="64e76-127">Nicht für alle Plattformen ist ein Kameraeinstellungsanbieter erforderlich.</span><span class="sxs-lookup"><span data-stu-id="64e76-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="64e76-128">Wenn es keine Anbieter gibt, die mit der Plattform kompatibel sind, auf der die Anwendung ausgeführt wird, werden vom Microsoft Mixed Reality Toolkit grundlegende Standardwerte angewendet.</span><span class="sxs-lookup"><span data-stu-id="64e76-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="64e76-129">Anzeigeeinstellungen</span><span class="sxs-lookup"><span data-stu-id="64e76-129">Display settings</span></span>

![Kameraanzeigeeinstellungen](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="64e76-131">Anzeigeeinstellungen werden sowohl für nicht transparente (z.B. Virtual Reality) als auch für transparente (z. B. Microsoft HoloLens) Anzeige angegeben.</span><span class="sxs-lookup"><span data-stu-id="64e76-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="64e76-132">Die Kamera wird zur Laufzeit mithilfe dieser Einstellungen konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="64e76-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="64e76-133">**Near Clip**</span><span class="sxs-lookup"><span data-stu-id="64e76-133">**Near Clip**</span></span>

<span data-ttu-id="64e76-134">Die nahe Clipebene ist die nächstgelegene ( in Metern) , die ein virtuelles Objekt der Kamera am nächsten liegt und weiterhin gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="64e76-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="64e76-135">Für einen größtmöglichen Benutzerfreundlichkeit empfiehlt es sich, diesen Wert größer als 0 (null) zu machen.</span><span class="sxs-lookup"><span data-stu-id="64e76-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="64e76-136">Das vorherige Bild enthält Werte, die sich auf einer Vielzahl von Geräten als bewertigend herausbilden.</span><span class="sxs-lookup"><span data-stu-id="64e76-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="64e76-137">**Far Clip**</span><span class="sxs-lookup"><span data-stu-id="64e76-137">**Far Clip**</span></span>

<span data-ttu-id="64e76-138">Die entfernte Clipebene ist die weiteste in Metern, die ein virtuelles Objekt für die Kamera sein und noch gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="64e76-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="64e76-139">Für transparente Geräte wird empfohlen, dass dieser Wert relativ nahe ist, um den realen Raum nicht zu überschreiten und die immersiven Qualitäten der Anwendung zu unterbricht.</span><span class="sxs-lookup"><span data-stu-id="64e76-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="64e76-140">**Flags löschen**</span><span class="sxs-lookup"><span data-stu-id="64e76-140">**Clear Flags**</span></span>

<span data-ttu-id="64e76-141">Der Clear Flags-Wert gibt an, wie die Anzeige beim Gezeichneten gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="64e76-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="64e76-142">Bei Virtual Reality-Erfahrungen wird dieser Wert am häufigsten auf Skybox festgelegt.</span><span class="sxs-lookup"><span data-stu-id="64e76-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="64e76-143">Bei transparenten Anzeigen wird empfohlen, dies auf Color (Farbe) zu setzen.</span><span class="sxs-lookup"><span data-stu-id="64e76-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="64e76-144">**Hintergrundfarbe**</span><span class="sxs-lookup"><span data-stu-id="64e76-144">**Background Color**</span></span>

<span data-ttu-id="64e76-145">Wenn die Clear-Flags nicht auf Skybox festgelegt sind, wird die Hintergrundfarbeigenschaft angezeigt.</span><span class="sxs-lookup"><span data-stu-id="64e76-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="64e76-146">**Qualitätseinstellungen**</span><span class="sxs-lookup"><span data-stu-id="64e76-146">**Quality Settings**</span></span>

<span data-ttu-id="64e76-147">Der Wert für die Qualitätseinstellungen gibt die Grafikqualität an, die Unity beim Rendern der Szene verwenden soll.</span><span class="sxs-lookup"><span data-stu-id="64e76-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="64e76-148">Die Qualitätsstufe ist eine Einstellung auf Projektebene und nicht spezifisch für eine Kamera.</span><span class="sxs-lookup"><span data-stu-id="64e76-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="64e76-149">Weitere Informationen finden Sie im Artikel [Qualität](https://docs.unity3d.com/Manual/class-QualitySettings.html) in der Unity-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="64e76-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="64e76-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="64e76-150">See also</span></span>

- [<span data-ttu-id="64e76-151">Dokumentation zur Kamerasystem-API</span><span class="sxs-lookup"><span data-stu-id="64e76-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="64e76-152">Erstellen eines Kameraeinstellungsanbieters</span><span class="sxs-lookup"><span data-stu-id="64e76-152">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
