---
title: Übersicht über das Kamerasystem
description: Landing page for camera system in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Kamera,
ms.openlocfilehash: cfb40b00d81133ad40e0e4d7a7b2ad87ee645e36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177043"
---
# <a name="camera-system-overview"></a><span data-ttu-id="abe4c-104">Übersicht über das Kamerasystem</span><span class="sxs-lookup"><span data-stu-id="abe4c-104">Camera system overview</span></span>

<span data-ttu-id="abe4c-105">Das Kamerasystem ermöglicht es dem Microsoft Mixed Reality Toolkit, die Kamera der Anwendung für die Verwendung in Mixed Reality-Anwendungen zu konfigurieren und zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="abe4c-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="abe4c-106">Mithilfe des Kamerasystems können Anwendungen geschrieben werden, um sowohl nicht transparente (z. B. virtual reality) als auch transparente (z. B. Microsoft HoloLens) Geräte zu unterstützen, ohne Code schreiben zu müssen, um zwischen den einzelnen Anzeigetypen zu unterscheiden und diese zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="abe4c-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="abe4c-107">Aktivieren des Kamerasystems</span><span class="sxs-lookup"><span data-stu-id="abe4c-107">Enabling the camera system</span></span>

<span data-ttu-id="abe4c-108">Das Kamerasystem wird vom MixedRealityToolkit-Objekt (oder einer anderen Dienstregistrierungskomponente) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="abe4c-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="abe4c-109">Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus.</span><span class="sxs-lookup"><span data-stu-id="abe4c-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="abe4c-110">Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="abe4c-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="abe4c-111">Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="abe4c-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="abe4c-113">Navigieren Sie im Bereich Inspector zum Abschnitt kamerasystem, und stellen Sie sicher, dass **Kamerasystem aktivieren** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="abe4c-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![Aktivieren des Kamerasystems](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="abe4c-115">Wählen Sie die Kamerasystemimplementierung aus.</span><span class="sxs-lookup"><span data-stu-id="abe4c-115">Select the camera system implementation.</span></span> <span data-ttu-id="abe4c-116">Die vom MRTK bereitgestellte Standardklassenimplementierungen sind `MixedRealityCameraSystem` .</span><span class="sxs-lookup"><span data-stu-id="abe4c-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![Auswählen der Kamerasystemimplementierung](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="abe4c-118">Auswählen des gewünschten Konfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="abe4c-118">Select the desired configuration profile</span></span>

    ![Auswählen des Kamerasystemprofils](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="abe4c-120">Konfigurieren des Kamerasystems</span><span class="sxs-lookup"><span data-stu-id="abe4c-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="abe4c-121">Einstellungen-Anbieter</span><span class="sxs-lookup"><span data-stu-id="abe4c-121">Settings providers</span></span>

![Kamera-Einstellungen-Anbieter](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="abe4c-123">Anbieter von Kameraeinstellungen ermöglichen die plattformspezifische Konfiguration der Kamera.</span><span class="sxs-lookup"><span data-stu-id="abe4c-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="abe4c-124">Diese Einstellungen können benutzerdefinierte Konfigurationsschritte und/oder Komponenten enthalten.</span><span class="sxs-lookup"><span data-stu-id="abe4c-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="abe4c-125">Anbieter können hinzugefügt werden, indem Sie auf die Schaltfläche **Kamera Einstellungen Anbieter hinzufügen** klicken.</span><span class="sxs-lookup"><span data-stu-id="abe4c-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="abe4c-126">Sie können entfernt werden, indem Sie rechts neben **-** dem Anbieternamen auf die Schaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="abe4c-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="abe4c-127">Nicht für alle Plattformen ist ein Anbieter für Kameraeinstellungen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="abe4c-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="abe4c-128">Wenn es keine Anbieter gibt, die mit der Plattform kompatibel sind, auf der die Anwendung ausgeführt wird, wendet das Microsoft Mixed Reality Toolkit grundlegende Standardwerte an.</span><span class="sxs-lookup"><span data-stu-id="abe4c-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="abe4c-129">Anzeigeeinstellungen</span><span class="sxs-lookup"><span data-stu-id="abe4c-129">Display settings</span></span>

![Kameraanzeige Einstellungen](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="abe4c-131">Anzeigeeinstellungen werden sowohl für nicht transparente (z. B. Virtual Reality) als auch für transparente (z. B. Microsoft HoloLens) Anzeigen angegeben.</span><span class="sxs-lookup"><span data-stu-id="abe4c-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="abe4c-132">Die Kamera wird zur Laufzeit mithilfe dieser Einstellungen konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="abe4c-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="abe4c-133">**Near Clip**</span><span class="sxs-lookup"><span data-stu-id="abe4c-133">**Near Clip**</span></span>

<span data-ttu-id="abe4c-134">Die nahe Clipebene ist in Metern die nächstgelegene, die ein virtuelles Objekt zur Kamera haben und dennoch gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="abe4c-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="abe4c-135">Für den größtmöglichen Benutzerfreundlichkeit wird empfohlen, diesen Wert größer als 0 (null) zu machen.</span><span class="sxs-lookup"><span data-stu-id="abe4c-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="abe4c-136">Die vorherige Abbildung enthält Werte, die sich auf einer Vielzahl von Geräten als vertraut erwiesen haben.</span><span class="sxs-lookup"><span data-stu-id="abe4c-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="abe4c-137">**Far Clip**</span><span class="sxs-lookup"><span data-stu-id="abe4c-137">**Far Clip**</span></span>

<span data-ttu-id="abe4c-138">Die weit entfernte Clipebene ist in Metern die am weitesten entfernte, die ein virtuelles Objekt für die Kamera sein und weiterhin gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="abe4c-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="abe4c-139">Für transparente Geräte wird empfohlen, dass dieser Wert relativ nahe beieinander liegt, da er den realen Raum nicht übermäßig überschreitet und die immersiven Qualitäten der Anwendung unterbricht.</span><span class="sxs-lookup"><span data-stu-id="abe4c-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="abe4c-140">**Flags löschen**</span><span class="sxs-lookup"><span data-stu-id="abe4c-140">**Clear Flags**</span></span>

<span data-ttu-id="abe4c-141">Der Wert clear flags gibt an, wie die Anzeige beim Zeichnen gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="abe4c-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="abe4c-142">Für Virtual Reality-Umgebungen wird dieser Wert am häufigsten auf Skybox festgelegt.</span><span class="sxs-lookup"><span data-stu-id="abe4c-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="abe4c-143">Für transparente Anzeigen wird empfohlen, diese auf Farbe festzulegen.</span><span class="sxs-lookup"><span data-stu-id="abe4c-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="abe4c-144">**Hintergrundfarbe**</span><span class="sxs-lookup"><span data-stu-id="abe4c-144">**Background Color**</span></span>

<span data-ttu-id="abe4c-145">Wenn die clear-Flags nicht auf Skybox festgelegt sind, wird die Eigenschaft für die Hintergrundfarbe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="abe4c-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="abe4c-146">**Quality Einstellungen**</span><span class="sxs-lookup"><span data-stu-id="abe4c-146">**Quality Settings**</span></span>

<span data-ttu-id="abe4c-147">Der Wert der Qualitätseinstellungen gibt die Grafikqualität an, die Unity beim Rendern der Szene verwenden soll.</span><span class="sxs-lookup"><span data-stu-id="abe4c-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="abe4c-148">Die Qualitätsstufe ist eine Einstellung auf Projektebene und nicht spezifisch für eine Kamera.</span><span class="sxs-lookup"><span data-stu-id="abe4c-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="abe4c-149">Weitere Informationen finden Sie im Artikel [Qualität](https://docs.unity3d.com/Manual/class-QualitySettings.html) in der Unity-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="abe4c-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="abe4c-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="abe4c-150">See also</span></span>

- [<span data-ttu-id="abe4c-151">Dokumentation zur Kamerasystem-API</span><span class="sxs-lookup"><span data-stu-id="abe4c-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="abe4c-152">Erstellen eines Kamera-Einstellungen-Anbieters</span><span class="sxs-lookup"><span data-stu-id="abe4c-152">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
