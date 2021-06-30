---
title: Übersicht über das Begrenzungssystem
description: Landing page for boundary system in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Begrenzungssystem,
ms.openlocfilehash: 405a2d06be5d929d5c276fc8cd7ab36b6b3cf68c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121358"
---
# <a name="boundary-system"></a><span data-ttu-id="328dc-104">Begrenzungssystem</span><span class="sxs-lookup"><span data-stu-id="328dc-104">Boundary system</span></span>

<span data-ttu-id="328dc-105">Das Begrenzungssystem bietet Unterstützung für die Visualisierung von Virtual Reality-Begrenzungskomponenten in Mixed Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="328dc-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="328dc-106">Grenzen definieren den Bereich, in dem sich Benutzer sicher bewegen können, während sie ein VR-Headset tragen.</span><span class="sxs-lookup"><span data-stu-id="328dc-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="328dc-107">Grenzen sind eine wichtige Komponente einer Mixed Reality-Erfahrung, mit der Benutzer ungesehene Hindernisse beim Tragen eines VR-Headsets vermeiden können.</span><span class="sxs-lookup"><span data-stu-id="328dc-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="328dc-108">Viele Virtual Reality-Plattformen bieten eine automatische Anzeige, z. B. einen weißen Umriss, der auf der virtuellen Welt überlagert wird, wenn sich der Benutzer oder sein Controller der Grenze nähert.</span><span class="sxs-lookup"><span data-stu-id="328dc-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="328dc-109">Das Begrenzungssystem des Mixed Reality Toolkits erweitert dieses Feature, um die Anzeige einer Gliederung des nachverfolgten Bereichs, einer Bodenebene und anderer Features zu ermöglichen, die verwendet werden können, um Benutzern zusätzliche Informationen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="328dc-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="328dc-110">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="328dc-110">Getting started</span></span>

<span data-ttu-id="328dc-111">Das Hinzufügen von Unterstützung für Grenzen erfordert zwei Hauptkomponenten des Mixed Reality Toolkits: das Begrenzungssystem und eine Virtual Reality-Plattform, die mit einer Grenze konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="328dc-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="328dc-112">[Aktivieren](#enable-boundary-system) des Begrenzungssystems</span><span class="sxs-lookup"><span data-stu-id="328dc-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="328dc-113">[Konfigurieren](#configure-boundary-visualization) der Begrenzungsvisualisierung</span><span class="sxs-lookup"><span data-stu-id="328dc-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="328dc-114">[Erstellen und Bereitstellen](#build-and-deploy) auf einer VR-Plattform mit einer konfigurierten Grenze</span><span class="sxs-lookup"><span data-stu-id="328dc-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="328dc-115">Aktivieren des Begrenzungssystems</span><span class="sxs-lookup"><span data-stu-id="328dc-115">Enable boundary system</span></span>

<span data-ttu-id="328dc-116">Das Begrenzungssystem wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungsstellenkomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="328dc-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="328dc-117">In den folgenden Schritten wird davon ausgegangen, dass das MixedRealityToolkit-Objekt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="328dc-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="328dc-118">Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="328dc-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="328dc-119">Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="328dc-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="328dc-121">Navigieren Sie im Bereich Inspector (Inspektor) zum Abschnitt Boundary System (Begrenzungssystem), und aktivieren Sie Enable (Aktivieren).</span><span class="sxs-lookup"><span data-stu-id="328dc-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![Aktivieren des Begrenzungssystems](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="328dc-123">Wählen Sie die Implementierung des Begrenzungssystems aus.</span><span class="sxs-lookup"><span data-stu-id="328dc-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="328dc-124">Die vom MRTK bereitgestellte Standardklassenimplementierungen sind : [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="328dc-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![Auswählen der Implementierung des Begrenzungssystems](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="328dc-126">Alle Implementierungen des Begrenzungssystems müssen die [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="328dc-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="328dc-127">Konfigurieren der Begrenzungsvisualisierung</span><span class="sxs-lookup"><span data-stu-id="328dc-127">Configure boundary visualization</span></span>

<span data-ttu-id="328dc-128">Das [Begrenzungssystem verwendet ein Konfigurationsprofil,](configuring-boundary-visualization.md) um anzugeben, welche Begrenzungskomponenten angezeigt werden sollen, und um deren Darstellung zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="328dc-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![Optionen für die Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="328dc-130">Benutzer des `DefaultMixedRealityBoundaryVisualizationProfile` Standardprofils (Assets/MRTK/SDK/Profile) haben das Begrenzungssystem vorkonfiguriert, um eine Bodenebene, den Spielbereich und den nachverfolgten Bereich anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="328dc-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="328dc-131">Erstellen und Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="328dc-131">Build and deploy</span></span>

<span data-ttu-id="328dc-132">Nachdem das Begrenzungssystem mit den gewünschten Visualisierungsoptionen konfiguriert wurde, kann das Projekt auf der Zielplattform bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="328dc-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="328dc-133">Der Unity-Wiedergabemodus ermöglicht die Visualisierung der konfigurierten Grenze im Editor.</span><span class="sxs-lookup"><span data-stu-id="328dc-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="328dc-134">Dieses Feature ermöglicht schnelle Entwicklung und Tests, ohne dass der Build- und Bereitstellungsschritt erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="328dc-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="328dc-135">Stellen Sie sicher, dass Sie abschließende Akzeptanztests mit einer erstellten und bereitgestellten Version der Anwendung durchführen, die auf der Zielhardware und -plattform ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="328dc-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="328dc-136">Zugreifen auf das Begrenzungssystem über Code</span><span class="sxs-lookup"><span data-stu-id="328dc-136">Accessing boundary system via code</span></span>

<span data-ttu-id="328dc-137">Wenn diese Option aktiviert und konfiguriert ist, kann über die statische Hilfsklasse CoreServices auf das Begrenzungssystem zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="328dc-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="328dc-138">Der Verweis kann dann verwendet werden, um die Boundary-Parameter dynamisch zu ändern und auf verwandte GameObjects zuzugreifen, die vom System verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="328dc-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="328dc-139">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="328dc-139">See also</span></span>

- [<span data-ttu-id="328dc-140">Dokumentation zur Begrenzungs-API</span><span class="sxs-lookup"><span data-stu-id="328dc-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="328dc-141">Konfigurieren der Begrenzungsvisualisierung</span><span class="sxs-lookup"><span data-stu-id="328dc-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
