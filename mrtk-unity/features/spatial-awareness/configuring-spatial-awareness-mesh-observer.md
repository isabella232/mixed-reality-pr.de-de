---
title: Konfigurieren von Gitternetzbeobachtern für das Gerät
description: Konfigurieren des out-of-box Spatial Mesh Observer in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281939"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="2e168-104">Konfigurieren von Gitternetzbeobachtern für das Gerät</span><span class="sxs-lookup"><span data-stu-id="2e168-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="2e168-105">Dieser Leitfaden führt Sie durch die Konfiguration des vorkonfigurieren Spatial Mesh Observer in MRTK, der die Windows Mixed Reality unterstützt (d. h.</span><span class="sxs-lookup"><span data-stu-id="2e168-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="2e168-106">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="2e168-106">HoloLens).</span></span> <span data-ttu-id="2e168-107">Die vom Mixed Reality Toolkit bereitgestellte Standardimplementierung ist die [WindowsMixedRealitySpatialMeshObserver-Klasse.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="2e168-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="2e168-108">Viele der Eigenschaften in diesem Artikel gelten jedoch für andere [benutzerdefinierte Observer-Implementierungen.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="2e168-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="2e168-109">Profileinstellungen</span><span class="sxs-lookup"><span data-stu-id="2e168-109">Profile settings</span></span>

<span data-ttu-id="2e168-110">Die folgenden beiden Elemente müssen zuerst definiert werden, wenn Sie ein Spatial Mesh Observer-Profil für das [Spatial Awareness-System konfigurieren.](spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2e168-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="2e168-111">Die konkrete Implementierung des Beobachtertyps</span><span class="sxs-lookup"><span data-stu-id="2e168-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="2e168-112">Liste der unterstützten Plattformen zum Ausführen dieses Beobachters</span><span class="sxs-lookup"><span data-stu-id="2e168-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="2e168-113">Alle Beobachter müssen die [IMixedRealitySpatialAwarenessObserver-Schnittstelle](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) erweitern.</span><span class="sxs-lookup"><span data-stu-id="2e168-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Mesh Observer– allgemeine Einstellungen Plattformtypen](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="2e168-115">Allgemeine Einstellungen</span><span class="sxs-lookup"><span data-stu-id="2e168-115">General settings</span></span>

![Allgemeine Einstellungen für Mesh Observer Einstellungen Genral](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="2e168-117">**Startverhalten**</span><span class="sxs-lookup"><span data-stu-id="2e168-117">**Startup Behavior**</span></span>

<span data-ttu-id="2e168-118">Das Startverhalten gibt an, ob die Ausführung des Beobachters beginnt, wenn er zum ersten Mal instanziiert wird.</span><span class="sxs-lookup"><span data-stu-id="2e168-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="2e168-119">Die zwei Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="2e168-119">The two options are:</span></span>

* <span data-ttu-id="2e168-120">*Automatischer Start:* Der Standardwert, bei dem der Beobachter den Vorgang nach der Initialisierung startet.</span><span class="sxs-lookup"><span data-stu-id="2e168-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="2e168-121">*Manueller Start:* Der Beobachter wartet darauf, dass er zum Starten geleitet wird.</span><span class="sxs-lookup"><span data-stu-id="2e168-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="2e168-122">Wenn Sie *den manuellen Start verwenden,* müssen sie zur Laufzeit über den Code fortgesetzt [und angehalten werden.](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="2e168-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="2e168-123">**Updateintervall**</span><span class="sxs-lookup"><span data-stu-id="2e168-123">**Update Interval**</span></span>

<span data-ttu-id="2e168-124">Die Zeit in Sekunden zwischen Anforderungen an die Plattform zum Aktualisieren der Räumlichen Gitternetzdaten.</span><span class="sxs-lookup"><span data-stu-id="2e168-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="2e168-125">Typische Werte liegen im Bereich von 0,1 und 5,0 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="2e168-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="2e168-126">**Is Stationärer Beobachter**</span><span class="sxs-lookup"><span data-stu-id="2e168-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="2e168-127">Gibt an, ob der Beobachter unverändert bleiben oder mit dem Benutzer verschieben und aktualisieren soll.</span><span class="sxs-lookup"><span data-stu-id="2e168-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="2e168-128">True gibt an, dass *die Observer-Form* mit durch *Observation Extents definiertem* Volume beim Start am Ursprung verbleibt.</span><span class="sxs-lookup"><span data-stu-id="2e168-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="2e168-129">False gibt an, dass der Beobachterbereich dem Kopf des Benutzers als Ursprung der Form folgt.</span><span class="sxs-lookup"><span data-stu-id="2e168-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="2e168-130">Es werden keine Gitternetzdaten für einen physischen Bereich außerhalb des Beobachterbereichs berechnet, wie durch diese Eigenschaften definiert: *Is Stationary Observer,\*\*Observer Shape*\* und *Observation Extents*.</span><span class="sxs-lookup"><span data-stu-id="2e168-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="2e168-131">**Observer-Form**</span><span class="sxs-lookup"><span data-stu-id="2e168-131">**Observer Shape**</span></span>

<span data-ttu-id="2e168-132">Die Beobachterform definiert den Volumetyp, den der Gitternetzbeobachter beim Beobachten von Gittern verwendet.</span><span class="sxs-lookup"><span data-stu-id="2e168-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="2e168-133">Die folgenden Optionen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="2e168-133">The supported options are:</span></span>

* <span data-ttu-id="2e168-134">*Achsenbündiger Würfel:* Rechteckige Form, die an den Achsen des Weltkoordinatensystems ausgerichtet bleibt, wie beim Anwendungsstart festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2e168-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="2e168-135">*Vom Benutzer ausgerichteter Würfel:* Rechteckige Form, die gedreht wird, um sie am lokalen Koordinatensystem des Benutzers auszurichten.</span><span class="sxs-lookup"><span data-stu-id="2e168-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="2e168-136">*Kugel:* Ein pherisches Volume mit einem Mittelpunkt am Ursprung des Weltraums.</span><span class="sxs-lookup"><span data-stu-id="2e168-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="2e168-137">Der X-Wert der *Eigenschaft Observation Extents* wird als Radius der Kugel verwendet.</span><span class="sxs-lookup"><span data-stu-id="2e168-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="2e168-138">**Beobachtungs-Extents**</span><span class="sxs-lookup"><span data-stu-id="2e168-138">**Observation Extents**</span></span>

<span data-ttu-id="2e168-139">Die Beobachtungsdweite definiert den Abstand vom Beobachtungspunkt, an dem Gitternetze beobachtet werden.</span><span class="sxs-lookup"><span data-stu-id="2e168-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="2e168-140">Physikalische Einstellungen</span><span class="sxs-lookup"><span data-stu-id="2e168-140">Physics settings</span></span>

![Mesh Observer Physics Einstellungen](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="2e168-142">**Physikschicht**</span><span class="sxs-lookup"><span data-stu-id="2e168-142">**Physics Layer**</span></span>

<span data-ttu-id="2e168-143">Die physikalische Schicht, auf der räumliche Gitternetzobjekte platziert werden, um mit den Unity-Systemen Für Physik und RayCast zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="2e168-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="2e168-144">Das Mixed Reality Toolkit reserviert *standardmäßig Ebene 31* für die Verwendung durch Beobachter des räumlichen Bewusstseins.</span><span class="sxs-lookup"><span data-stu-id="2e168-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="2e168-145">**Neuberechnung von Normals**</span><span class="sxs-lookup"><span data-stu-id="2e168-145">**Recalculate Normals**</span></span>

<span data-ttu-id="2e168-146">Gibt an, ob der Gitternetzbeobachter die Normalen des Gitters nach der Beobachtung neu berechnet.</span><span class="sxs-lookup"><span data-stu-id="2e168-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="2e168-147">Diese Einstellung ist verfügbar, um sicherzustellen, dass Anwendungen Gitternetze empfangen, die gültige Normaldaten auf Plattformen enthalten, die sie nicht mit Gittern zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="2e168-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="2e168-148">Detailebeneneinstellungen</span><span class="sxs-lookup"><span data-stu-id="2e168-148">Level of detail settings</span></span>

![Mesh Observer Level of Detail Einstellungen](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="2e168-150">**Detailebene**</span><span class="sxs-lookup"><span data-stu-id="2e168-150">**Level of Detail**</span></span>

<span data-ttu-id="2e168-151">Gibt die Detailebene (LEVEL of Detail, LOD) der räumlichen Gitterdaten an.</span><span class="sxs-lookup"><span data-stu-id="2e168-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="2e168-152">Aktuell definierte Werte sind "Coarse", "Fine" und "Custom".</span><span class="sxs-lookup"><span data-stu-id="2e168-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="2e168-153">*Grob:* Wirkt sich weniger auf die Anwendungsleistung aus und ist eine hervorragende Wahl für die Navigations-/Ebenensuche.</span><span class="sxs-lookup"><span data-stu-id="2e168-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="2e168-154">*Mittel:* Eine ausgeglichene Einstellung ist häufig nützlich für Erfahrungen, bei denen die Umgebung ständig sowohl nach großen Merkmalen, Bodenbelägen und Wänden als auch nach Verschlussdetails durchsucht wird.</span><span class="sxs-lookup"><span data-stu-id="2e168-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="2e168-155">*Fein:* In der Regel wird eine höhere Auswirkung auf die Anwendungsleistung abverfolgen und ist eine hervorragende Option für Okklusionsgitter.</span><span class="sxs-lookup"><span data-stu-id="2e168-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="2e168-156">*Benutzerdefiniert:* Erfordert, dass die Anwendung die *Eigenschaft Dreiecke/kubische* Verbrauchsmessung anknt und Anwendungen ermöglicht, die Genauigkeit im Vergleich zu den Leistungseinwirkungen des Raumgitterbeobachters zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="2e168-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="2e168-157">Es ist nicht garantiert, dass alle *Werte für Dreiecke/kubische* Zähler von allen Plattformen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2e168-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="2e168-158">Experimentieren und Profilerstellung wird dringend empfohlen, wenn Sie eine benutzerdefinierte LOD verwenden.</span><span class="sxs-lookup"><span data-stu-id="2e168-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="2e168-159">**Dreiecke pro kubischer Verbrauchsmessung**</span><span class="sxs-lookup"><span data-stu-id="2e168-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="2e168-160">Gültig, wenn die *Einstellung Benutzerdefiniert* für die **Eigenschaft Detailebene verwendet** wird, und gibt die Dreiecksdichte für das räumliche Netz an.</span><span class="sxs-lookup"><span data-stu-id="2e168-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="2e168-161">Anzeigeeinstellungen</span><span class="sxs-lookup"><span data-stu-id="2e168-161">Display settings</span></span>

![Gitternetzbeobachteranzeige Einstellungen](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="2e168-163">**Anzeigeoption**</span><span class="sxs-lookup"><span data-stu-id="2e168-163">**Display Option**</span></span>

<span data-ttu-id="2e168-164">Gibt an, wie räumliche Gitternetze vom Beobachter angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="2e168-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="2e168-165">Diese Werte werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="2e168-165">Supported values are:</span></span>

* <span data-ttu-id="2e168-166">*Keine:* Observer rendert das Gitternetz nicht</span><span class="sxs-lookup"><span data-stu-id="2e168-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="2e168-167">*Sichtbar:* Gitternetzdaten werden mithilfe des sichtbaren *Materials angezeigt.*</span><span class="sxs-lookup"><span data-stu-id="2e168-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="2e168-168">*Okklusion:* Gitternetzdaten verdecken Elemente in der Szene mithilfe des *Okklusionsmaterials.*</span><span class="sxs-lookup"><span data-stu-id="2e168-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![Auswählen der Spatial Awareness-Systemimplementierung](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="2e168-170">Raumbeobachter [können zur Laufzeit über Code fortgesetzt/angehalten werden.](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="2e168-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="2e168-171">Wenn *Sie die Anzeigeoption* auf *Keine festlegen,* **wird die** Ausführung des Beobachters NICHT verhindern.</span><span class="sxs-lookup"><span data-stu-id="2e168-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="2e168-172">Wenn Sie alle Beobachter beenden möchten, müssen Anwendungen alle Beobachter über anhalten. [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="2e168-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="2e168-173">**Sichtbares Material**</span><span class="sxs-lookup"><span data-stu-id="2e168-173">**Visible Material**</span></span>

<span data-ttu-id="2e168-174">Gibt das Material an, das beim Visualisieren des räumlichen Gitters verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="2e168-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="2e168-175">**Okklusionsmaterial**</span><span class="sxs-lookup"><span data-stu-id="2e168-175">**Occlusion Material**</span></span>

<span data-ttu-id="2e168-176">Gibt das Material an, das verwendet werden soll, damit das räumliche Netz Hologramme verdecken kann.</span><span class="sxs-lookup"><span data-stu-id="2e168-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e168-177">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2e168-177">See also</span></span>

* [<span data-ttu-id="2e168-178">Spatial Awareness System</span><span class="sxs-lookup"><span data-stu-id="2e168-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="2e168-179">Konfigurieren des Systems für räumliche Wahrnehmung über Code</span><span class="sxs-lookup"><span data-stu-id="2e168-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="2e168-180">Dokumentation zur IMixedRealitySpatialAwarenessObserver-API</span><span class="sxs-lookup"><span data-stu-id="2e168-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="2e168-181">IMixedRealitySpatialAwarenessMeshObserver-API-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="2e168-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="2e168-182">BaseSpatialObserver-API-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="2e168-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
