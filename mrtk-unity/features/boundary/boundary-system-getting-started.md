---
title: Übersicht über das Begrenzungssystem
description: Landing Page für das Begrenzungssystem in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, Boundary System,
ms.openlocfilehash: fd70479e5183e9a7557de5c5a532cc87161be017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177086"
---
# <a name="boundary-system-overview"></a><span data-ttu-id="b9c7b-104">Übersicht über das Begrenzungssystem</span><span class="sxs-lookup"><span data-stu-id="b9c7b-104">Boundary system overview</span></span>

<span data-ttu-id="b9c7b-105">Das Begrenzungssystem bietet Unterstützung für die Visualisierung von Virtual Reality-Begrenzungskomponenten in Mixed Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="b9c7b-106">Grenzen definieren den Bereich, in dem Benutzer sich sicher bewegen können, während sie ein VR-Headset verwenden.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="b9c7b-107">Grenzen sind eine wichtige Komponente einer Mixed Reality-Umgebung, um Benutzern zu helfen, unsichtbare Hindernisse zu vermeiden, während sie ein VR-Headset tragen.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="b9c7b-108">Viele Virtual Reality-Plattformen bieten eine automatische Anzeige, z. B. eine weiße Kontur, die der virtuellen Welt überlagert wird, wenn sich der Benutzer oder sein Controller der Grenze nähert.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="b9c7b-109">Das Boundary System des Mixed Reality Toolkits erweitert dieses Feature, um die Anzeige eines Umrisses des nachverfolgten Bereichs, einer Bodenebene und anderer Features zu ermöglichen, die verwendet werden können, um benutzern zusätzliche Informationen zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="b9c7b-110">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="b9c7b-110">Getting started</span></span>

<span data-ttu-id="b9c7b-111">Das Hinzufügen von Unterstützung für Grenzen erfordert zwei Hauptkomponenten des Mixed Reality Toolkits: das Boundary System und eine Virtual Reality-Plattform, die mit einer Grenze konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="b9c7b-112">[Aktivieren](#enable-boundary-system) des Begrenzungssystems</span><span class="sxs-lookup"><span data-stu-id="b9c7b-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="b9c7b-113">[Konfigurieren der](#configure-boundary-visualization) Begrenzungsvisualisierung</span><span class="sxs-lookup"><span data-stu-id="b9c7b-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="b9c7b-114">[Erstellen und Bereitstellen](#build-and-deploy) auf einer VR-Plattform mit einer konfigurierten Grenze</span><span class="sxs-lookup"><span data-stu-id="b9c7b-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="b9c7b-115">Aktivieren des Begrenzungssystems</span><span class="sxs-lookup"><span data-stu-id="b9c7b-115">Enable boundary system</span></span>

<span data-ttu-id="b9c7b-116">Das Boundary System wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungskomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="b9c7b-117">Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="b9c7b-118">Die für andere Dienstregistrierungen erforderlichen Schritte können unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="b9c7b-119">Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK– Konfigurierte Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="b9c7b-121">Navigieren Sie im Inspektorbereich zum Abschnitt Begrenzungssystem, und aktivieren Sie Aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![Aktivieren des Begrenzungssystems](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="b9c7b-123">Wählen Sie die Implementierung des Begrenzungssystems aus.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="b9c7b-124">Die vom MRTK bereitgestellte Standardklassenimplementierung ist die [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="b9c7b-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![Auswählen der Implementierung des Begrenzungssystems](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="b9c7b-126">Alle Boundary System-Implementierungen müssen die [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="b9c7b-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="b9c7b-127">Konfigurieren der Begrenzungsvisualisierung</span><span class="sxs-lookup"><span data-stu-id="b9c7b-127">Configure boundary visualization</span></span>

<span data-ttu-id="b9c7b-128">Das [Begrenzungssystem verwendet ein Konfigurationsprofil,](configuring-boundary-visualization.md) um anzugeben, welche Begrenzungskomponenten angezeigt werden sollen, und um deren Darstellung zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![Optionen für die Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="b9c7b-130">Benutzer des Standardprofils (Assets/MRTK/SDK/Profiles) haben das Begrenzungssystem vorkonfiguriert, um eine Bodenebene, den Wiedergabebereich und den nachverfolgten Bereich `DefaultMixedRealityBoundaryVisualizationProfile` anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="b9c7b-131">Erstellen und Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="b9c7b-131">Build and deploy</span></span>

<span data-ttu-id="b9c7b-132">Nachdem das Begrenzungssystem mit den gewünschten Visualisierungsoptionen konfiguriert wurde, kann das Projekt auf der Zielplattform bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="b9c7b-133">Der Unity-Wiedergabemodus ermöglicht die Visualisierung der konfigurierten Grenze im Editor.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="b9c7b-134">Dieses Feature ermöglicht schnelle Entwicklung und Tests, ohne dass der Build- und Bereitstellungsschritt erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="b9c7b-135">Stellen Sie sicher, dass Sie abschließende Akzeptanztests mit einer erstellten und bereitgestellten Version der Anwendung durchführen, die auf der Zielhardware und -plattform ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="b9c7b-136">Zugreifen auf das Begrenzungssystem über Code</span><span class="sxs-lookup"><span data-stu-id="b9c7b-136">Accessing boundary system via code</span></span>

<span data-ttu-id="b9c7b-137">Wenn aktiviert und konfiguriert, kann über die statische CoreServices-Hilfsklasse auf das Boundary System zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="b9c7b-138">Der Verweis kann dann verwendet werden, um die Begrenzungsparameter dynamisch zu ändern und auf zugehörige GameObjects zu zugreifen, die vom System verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="b9c7b-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="b9c7b-139">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b9c7b-139">See also</span></span>

- [<span data-ttu-id="b9c7b-140">Dokumentation zur Begrenzungs-API</span><span class="sxs-lookup"><span data-stu-id="b9c7b-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="b9c7b-141">Konfigurieren der Begrenzungsvisualisierung</span><span class="sxs-lookup"><span data-stu-id="b9c7b-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
