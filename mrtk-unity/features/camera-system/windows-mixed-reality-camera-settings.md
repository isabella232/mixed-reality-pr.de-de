---
title: Windows Mixed Reality-Kameraeinstellungen
description: Dokumentation zur Verwendung Windows Mixed Reality Kamera im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Kamera,
ms.openlocfilehash: 94e00f47dc565af0824ef6acf5c08a9e99d4529f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145166"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="7ed88-104">Windows Mixed Reality Anbieter von Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="7ed88-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="7ed88-105">Der Windows Mixed Reality Anbieter von Kameraeinstellungen bestimmt den Gerätetyp, auf dem die Anwendung ausgeführt wird, und wendet die entsprechenden Konfigurationseinstellungen basierend auf der Anzeige (transparent oder nicht transparent) an.</span><span class="sxs-lookup"><span data-stu-id="7ed88-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="7ed88-106">Aktivieren des Anbieters für Windows Mixed Reality Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="7ed88-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="7ed88-107">In den folgenden Schritten wird davon ausgegangen, dass das MixedRealityToolkit-Objekt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7ed88-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="7ed88-108">Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="7ed88-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="7ed88-109">Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="7ed88-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="7ed88-111">Navigieren Sie im Bereich Inspektor zum Abschnitt Kamerasystem, und erweitern Sie den Abschnitt Anbieter für **Kameraeinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="7ed88-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![Erweitern von Einstellungsanbietern](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="7ed88-113">Klicken Sie auf **Kameraeinstellungsanbieter hinzufügen,** und erweitern Sie den neu hinzugefügten Eintrag **Neue Kameraeinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="7ed88-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![Erweitern des neuen Einstellungsanbieters](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="7ed88-115">Wählen Sie den Anbieter Windows Mixed Reality Kameraeinstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="7ed88-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![Auswählen Windows Mixed Reality Einstellungsanbieters](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="7ed88-117">Wenn Sie die Standardprofile des Microsoft Mixed Reality Toolkits verwenden, ist der Anbieter Windows Mixed Reality Kameraeinstellungen bereits aktiviert und konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="7ed88-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="7ed88-118">Konfigurieren des Anbieters für Windows Mixed Reality Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="7ed88-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="7ed88-119">Die Windows Mixed Reality Kameraeinstellungen unterstützt auch ein Profil.</span><span class="sxs-lookup"><span data-stu-id="7ed88-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="7ed88-120">Dieses Profil bietet die folgenden Optionen:</span><span class="sxs-lookup"><span data-stu-id="7ed88-120">This profile provides the following options:</span></span>

![Konfiguration der kameraeinstellungen Windows Mixed Reality](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="7ed88-122">Rendern der Mixed Reality-Aufnahme von der Foto-/Videokamera</span><span class="sxs-lookup"><span data-stu-id="7ed88-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="7ed88-123">Mit dieser Einstellung auf HoloLens 2 können Sie hologrammausrichtung in Ihren Mixed Reality-Erfassungen aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7ed88-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="7ed88-124">Wenn diese Option aktiviert ist, stellt die Plattform der App eine zusätzliche HolographicCamera zur Verfügung, wenn ein Mixed Reality-Aufnahmefoto oder -video aufgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="7ed88-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="7ed88-125">Diese HolographicCamera bietet Ansichtsmatrizen, die der Position der Foto-/Videokamera entspricht, und stellt Projektionsmatrizen mithilfe des Sichtfelds der Foto-/Videokamera zur Anwendung.</span><span class="sxs-lookup"><span data-stu-id="7ed88-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="7ed88-126">Dadurch wird sichergestellt, dass Hologramme, z. B. Handgitter, in der Videoausgabe sichtbar ausgerichtet bleiben.</span><span class="sxs-lookup"><span data-stu-id="7ed88-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="7ed88-127">HoloLens 2-Methode für die Neuprojektion</span><span class="sxs-lookup"><span data-stu-id="7ed88-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="7ed88-128">Legt die anfängliche Methode für die HoloLens 2 fest.</span><span class="sxs-lookup"><span data-stu-id="7ed88-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="7ed88-129">Die Standardempfehlung ist die Verwendung einer Tiefenumprojektion, da alle Teile der Szene unabhängig voneinander basierend auf ihrer Entfernung vom Benutzer stabilisiert werden.</span><span class="sxs-lookup"><span data-stu-id="7ed88-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="7ed88-130">Wenn Hologramme weiterhin instabil erscheinen, stellen Sie sicher, dass alle Objekte ihre Tiefe ordnungsgemäß an den Tiefenpuffer übermittelt haben.</span><span class="sxs-lookup"><span data-stu-id="7ed88-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="7ed88-131">Dies ist manchmal eine Shadereinstellung.</span><span class="sxs-lookup"><span data-stu-id="7ed88-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="7ed88-132">Wenn die Tiefe ordnungsgemäß übermittelt zu werden scheint und die Instabilität weiterhin vorhanden ist, versuchen Sie die automatische planare Stabilität, die den Tiefenpuffer verwendet, um eine Stabilitätsebene zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="7ed88-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="7ed88-133">Wenn eine App nicht genügend Tiefendaten übermitteln kann, damit eine dieser Optionen verwendet werden kann, wird eine planare Neuprojektion als Fallback bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7ed88-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="7ed88-134">Diese Methode basiert auf den von einer App bereitgestellten Fokuspunktdaten über [SetFocusPointForFrame.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)</span><span class="sxs-lookup"><span data-stu-id="7ed88-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="7ed88-135">Um die Neuprojektionsmethode zur Laufzeit zu aktualisieren, greifen Sie wie `WindowsMixedRealityReprojectionUpdater` hier beschrieben auf zu:</span><span class="sxs-lookup"><span data-stu-id="7ed88-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="7ed88-136">Dies muss nur einmal aktualisiert werden, und der Wert wird für alle nachfolgenden Frames wiederverwendet.</span><span class="sxs-lookup"><span data-stu-id="7ed88-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="7ed88-137">Wenn die Methode häufig aktualisiert wird, empfiehlt es sich, das Ergebnis zwischenspeichern anstatt `EnsureComponent` es häufig auf aufruft.</span><span class="sxs-lookup"><span data-stu-id="7ed88-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ed88-138">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7ed88-138">See also</span></span>

- [<span data-ttu-id="7ed88-139">Kamerasystemübersicht</span><span class="sxs-lookup"><span data-stu-id="7ed88-139">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="7ed88-140">Erstellen eines Kameraeinstellungsanbieters</span><span class="sxs-lookup"><span data-stu-id="7ed88-140">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
- [<span data-ttu-id="7ed88-141">Rendern Mixed Reality-Aufnahme von der PV-Kamera</span><span class="sxs-lookup"><span data-stu-id="7ed88-141">Rendering Mixed Reality Capture from the PV camera</span></span>](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="7ed88-142">Holografische Neuprojektion</span><span class="sxs-lookup"><span data-stu-id="7ed88-142">Holographic reprojection</span></span>](/windows/mixed-reality/hologram-stability#reprojection)