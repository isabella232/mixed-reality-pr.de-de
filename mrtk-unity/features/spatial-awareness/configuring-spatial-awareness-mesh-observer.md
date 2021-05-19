---
title: Konfigurieren des Beobachters von Gittermodellen für räumliche Wahrnehmung
description: Konfigurieren des out-of-box Spatial Mesh Observer in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 0d71a32d76624698e78b8123f427ddefc08f3d0b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144967"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="c80c9-104">Konfigurieren von Gitternetzbeobachtern für das Gerät</span><span class="sxs-lookup"><span data-stu-id="c80c9-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="c80c9-105">Dieser Leitfaden führt Sie durch die Konfiguration des vorkonfigurieren Spatial Mesh Observer in MRTK, der die Windows Mixed Reality unterstützt (d. h.</span><span class="sxs-lookup"><span data-stu-id="c80c9-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="c80c9-106">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="c80c9-106">HoloLens).</span></span> <span data-ttu-id="c80c9-107">Die vom Mixed Reality Toolkit bereitgestellte Standardimplementierung ist die [WindowsMixedRealitySpatialMeshObserver-Klasse.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="c80c9-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="c80c9-108">Viele der Eigenschaften in diesem Artikel gelten jedoch für andere [benutzerdefinierte Observer-Implementierungen.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="c80c9-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="c80c9-109">Profileinstellungen</span><span class="sxs-lookup"><span data-stu-id="c80c9-109">Profile settings</span></span>

<span data-ttu-id="c80c9-110">Die folgenden beiden Elemente müssen zuerst definiert werden, wenn Sie ein Spatial Mesh Observer-Profil für das [Spatial Awareness-System konfigurieren.](spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="c80c9-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="c80c9-111">Die konkrete Implementierung des Beobachtertyps</span><span class="sxs-lookup"><span data-stu-id="c80c9-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="c80c9-112">Liste der unterstützten Plattformen zum Ausführen dieses Beobachters</span><span class="sxs-lookup"><span data-stu-id="c80c9-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="c80c9-113">Alle Beobachter müssen die [IMixedRealitySpatialAwarenessObserver-Schnittstelle](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) erweitern.</span><span class="sxs-lookup"><span data-stu-id="c80c9-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Mesh Observer– Allgemeine Einstellungen Plattformtypen](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="c80c9-115">Allgemeine Einstellungen</span><span class="sxs-lookup"><span data-stu-id="c80c9-115">General settings</span></span>

![Allgemeine Einstellungen der Mesh Observer-Einstellungen – Allgemeine Einstellungen](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="c80c9-117">**Startverhalten**</span><span class="sxs-lookup"><span data-stu-id="c80c9-117">**Startup Behavior**</span></span>

<span data-ttu-id="c80c9-118">Das Startverhalten gibt an, ob die Ausführung des Beobachters beginnt, wenn er zum ersten Mal instanziiert wird.</span><span class="sxs-lookup"><span data-stu-id="c80c9-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="c80c9-119">Die zwei Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="c80c9-119">The two options are:</span></span>

* <span data-ttu-id="c80c9-120">*Automatischer Start:* Der Standardwert, bei dem der Beobachter den Vorgang nach der Initialisierung startet.</span><span class="sxs-lookup"><span data-stu-id="c80c9-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="c80c9-121">*Manueller Start:* Der Beobachter wartet darauf, zum Start geleitet zu werden</span><span class="sxs-lookup"><span data-stu-id="c80c9-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="c80c9-122">Wenn Sie *den manuellen Start verwenden,* müssen sie zur Laufzeit über den Code fortgesetzt [und angehalten werden.](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="c80c9-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="c80c9-123">**Updateintervall**</span><span class="sxs-lookup"><span data-stu-id="c80c9-123">**Update Interval**</span></span>

<span data-ttu-id="c80c9-124">Die Zeit in Sekunden zwischen Anforderungen an die Plattform zum Aktualisieren der Räumlichen Gitternetzdaten.</span><span class="sxs-lookup"><span data-stu-id="c80c9-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="c80c9-125">Typische Werte liegen im Bereich von 0,1 und 5,0 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="c80c9-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="c80c9-126">**Ist stationärer Beobachter**</span><span class="sxs-lookup"><span data-stu-id="c80c9-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="c80c9-127">Gibt an, ob der Beobachter stationär bleiben oder mit dem Benutzer verschoben und aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="c80c9-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="c80c9-128">True gibt an, dass die *Beobachterform* mit dem durch *Beobachtungsumfang definierten* Volume beim Start am Ursprung verbleibt.</span><span class="sxs-lookup"><span data-stu-id="c80c9-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="c80c9-129">False gibt an, dass der Beobachterbereich dem Kopf des Benutzers als Ursprung der Form folgt.</span><span class="sxs-lookup"><span data-stu-id="c80c9-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="c80c9-130">Es werden keine Gitternetzdaten für einen physischen Bereich außerhalb des Beobachterbereichs berechnet, wie in diesen Eigenschaften definiert: *Is Stationary Observer*, *Observer Shape*\* und *Observation Extents*.</span><span class="sxs-lookup"><span data-stu-id="c80c9-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="c80c9-131">**Beobachterform**</span><span class="sxs-lookup"><span data-stu-id="c80c9-131">**Observer Shape**</span></span>

<span data-ttu-id="c80c9-132">Die Beobachterform definiert den Volumetyp, den der Gitternetzbeoblicker beim Beobachten von Gitternetzen verwendet.</span><span class="sxs-lookup"><span data-stu-id="c80c9-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="c80c9-133">Folgende Optionen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="c80c9-133">The supported options are:</span></span>

* <span data-ttu-id="c80c9-134">*Achsenbündiger Würfel:* Rechteckige Form, die an den Achsen des Weltkoordinatensystems ausgerichtet bleibt, wie beim Anwendungsstart bestimmt.</span><span class="sxs-lookup"><span data-stu-id="c80c9-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="c80c9-135">*Vom Benutzer ausgerichteter Cube:* Rechteckige Form, die gedreht wird, um das lokale Koordinatensystem des Benutzers auszurichten.</span><span class="sxs-lookup"><span data-stu-id="c80c9-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="c80c9-136">*Sphere:* Ein sphärisches Volume mit einem Mittelpunkt am Ursprung des Weltraums.</span><span class="sxs-lookup"><span data-stu-id="c80c9-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="c80c9-137">Der X-Wert der *Eigenschaft Observation Extents* wird als Radius der Kugel verwendet.</span><span class="sxs-lookup"><span data-stu-id="c80c9-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="c80c9-138">**Beobachtungsumfang**</span><span class="sxs-lookup"><span data-stu-id="c80c9-138">**Observation Extents**</span></span>

<span data-ttu-id="c80c9-139">Die Beobachtungsumfang definieren den Abstand zum Beobachtungspunkt, der beobachtet wird.</span><span class="sxs-lookup"><span data-stu-id="c80c9-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="c80c9-140">Physikalische Einstellungen</span><span class="sxs-lookup"><span data-stu-id="c80c9-140">Physics settings</span></span>

![Mesh Observer – Physikalische Einstellungen](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="c80c9-142">**Physikalische Schicht**</span><span class="sxs-lookup"><span data-stu-id="c80c9-142">**Physics Layer**</span></span>

<span data-ttu-id="c80c9-143">Die physikalische Schicht, auf der räumliche Gittergitterobjekte platziert werden, um mit den Unity-Systemen "Physics" und "RayCast" zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="c80c9-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="c80c9-144">Das Mixed Reality Toolkit reserviert standardmäßig *Schicht 31* für die Verwendung durch Beobachter der räumlichen Wahrnehmung.</span><span class="sxs-lookup"><span data-stu-id="c80c9-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="c80c9-145">**Neuberechnung von Normalitäten**</span><span class="sxs-lookup"><span data-stu-id="c80c9-145">**Recalculate Normals**</span></span>

<span data-ttu-id="c80c9-146">Gibt an, ob der Gitternetzbeowacher die Normalitäten des Gitternetzes nach der Beobachtung neu berechnet.</span><span class="sxs-lookup"><span data-stu-id="c80c9-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="c80c9-147">Diese Einstellung ist verfügbar, um sicherzustellen, dass Anwendungen Gitternetze empfangen, die gültige Normaldaten auf Plattformen enthalten, die sie nicht mit Gitternetzen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c80c9-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="c80c9-148">Ebene der Detaileinstellungen</span><span class="sxs-lookup"><span data-stu-id="c80c9-148">Level of detail settings</span></span>

![Mesh Observer Level of Detail Settings](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="c80c9-150">**Detailebene**</span><span class="sxs-lookup"><span data-stu-id="c80c9-150">**Level of Detail**</span></span>

<span data-ttu-id="c80c9-151">Gibt die Detailebene (LOD) der räumlichen Gitternetzdaten an.</span><span class="sxs-lookup"><span data-stu-id="c80c9-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="c80c9-152">Derzeit definierte Werte sind "Coarse", "Fine" und "Custom".</span><span class="sxs-lookup"><span data-stu-id="c80c9-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="c80c9-153">*Grob:* Wirkt sich weniger auf die Anwendungsleistung aus und ist eine hervorragende Wahl für die Navigations-/Ebenensuche.</span><span class="sxs-lookup"><span data-stu-id="c80c9-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="c80c9-154">*Mittel:* Ausgeglichene Einstellung ist häufig nützlich für Umgebungen, die die Umgebung kontinuierlich sowohl nach großen Merkmalen, Etagen und Wänden als auch nach Verdeckungsdetails durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="c80c9-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="c80c9-155">*Gut:* Im Allgemeinen hat dies einen höheren Einfluss auf die Anwendungsleistung und ist eine hervorragende Option für Verdeckungsgitternetze.</span><span class="sxs-lookup"><span data-stu-id="c80c9-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="c80c9-156">*Benutzerdefiniert:* Erfordert, dass die Anwendung die Eigenschaft *Dreiecke/Kubische Verbrauchsmessung* angibt und Anwendungen ermöglicht, die Genauigkeit im Vergleich zur Leistungsbeeinträchtigung des Beobachters für räumliche Gitternetze zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="c80c9-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="c80c9-157">Es ist nicht garantiert, dass alle Werte für *Dreiecke/Kubikmeter* von allen Plattformen berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="c80c9-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="c80c9-158">Experimente und Profilerstellung werden dringend empfohlen, wenn Sie eine benutzerdefinierte LOD verwenden.</span><span class="sxs-lookup"><span data-stu-id="c80c9-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="c80c9-159">**Dreiecke pro Kubikmeter**</span><span class="sxs-lookup"><span data-stu-id="c80c9-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="c80c9-160">Gültig, wenn die *Einstellung Benutzerdefiniert* für die **Eigenschaft Detailebene** verwendet wird und die Dreiecksdichte für das räumliche Gitternetz angibt.</span><span class="sxs-lookup"><span data-stu-id="c80c9-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="c80c9-161">Anzeigeeinstellungen</span><span class="sxs-lookup"><span data-stu-id="c80c9-161">Display settings</span></span>

![Mesh Observer-Anzeigeeinstellungen](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="c80c9-163">**Anzeigeoption**</span><span class="sxs-lookup"><span data-stu-id="c80c9-163">**Display Option**</span></span>

<span data-ttu-id="c80c9-164">Gibt an, wie räumliche Gitternetze vom Beobachter angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="c80c9-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="c80c9-165">Diese Werte werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="c80c9-165">Supported values are:</span></span>

* <span data-ttu-id="c80c9-166">*Keine:* Observer rendert das Gitternetz nicht</span><span class="sxs-lookup"><span data-stu-id="c80c9-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="c80c9-167">*Sichtbar:* Gitternetzdaten werden mithilfe des *sichtbaren Materials* angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c80c9-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="c80c9-168">*Okklusion:* Gitternetzdaten verdecken Elemente in der Szene mithilfe des *Okklusionsmaterials.*</span><span class="sxs-lookup"><span data-stu-id="c80c9-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![Auswählen der Spatial Awareness-Systemimplementierung](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="c80c9-170">Raumbeobachter [können zur Laufzeit über Code fortgesetzt/angehalten werden.](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="c80c9-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="c80c9-171">Wenn *Sie die Anzeigeoption* auf *Keine festlegen,* **wird die** Ausführung des Beobachters NICHT verhindern.</span><span class="sxs-lookup"><span data-stu-id="c80c9-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="c80c9-172">Wenn Sie alle Beobachter beenden möchten, müssen Anwendungen alle Beobachter über anhalten. [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="c80c9-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="c80c9-173">**Sichtbares Material**</span><span class="sxs-lookup"><span data-stu-id="c80c9-173">**Visible Material**</span></span>

<span data-ttu-id="c80c9-174">Gibt das Material an, das beim Visualisieren des räumlichen Gitters verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c80c9-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="c80c9-175">**Okklusionsmaterial**</span><span class="sxs-lookup"><span data-stu-id="c80c9-175">**Occlusion Material**</span></span>

<span data-ttu-id="c80c9-176">Gibt das Material an, das verwendet werden soll, damit das räumliche Netz Hologramme verdecken kann.</span><span class="sxs-lookup"><span data-stu-id="c80c9-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="c80c9-177">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c80c9-177">See also</span></span>

* [<span data-ttu-id="c80c9-178">Spatial Awareness System</span><span class="sxs-lookup"><span data-stu-id="c80c9-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="c80c9-179">Konfigurieren des Systems für räumliche Wahrnehmung über Code</span><span class="sxs-lookup"><span data-stu-id="c80c9-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="c80c9-180">Dokumentation zur IMixedRealitySpatialAwarenessObserver-API</span><span class="sxs-lookup"><span data-stu-id="c80c9-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="c80c9-181">Dokumentation zur IMixedRealitySpatialAwarenessMeshObserver-API</span><span class="sxs-lookup"><span data-stu-id="c80c9-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="c80c9-182">BaseSpatialObserver-API-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="c80c9-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
