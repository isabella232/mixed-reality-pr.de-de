---
title: Erste Schritte mit räumlichem Bewusstsein
description: beschreibt räumliche Wahrnehmung im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 46bb78bc4e2574fd4da14f19edf52624b7b301c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176716"
---
# <a name="spatial-awareness-getting-started"></a><span data-ttu-id="9079f-104">Erste Schritte mit räumlichem Bewusstsein</span><span class="sxs-lookup"><span data-stu-id="9079f-104">Spatial awareness getting started</span></span>

![Räumliche Wahrnehmung](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="9079f-106">Das Spatial Awareness-System bietet umgebungsbezogenes Bewusstsein in Mixed Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="9079f-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="9079f-107">Bei der Einführung in Microsoft HoloLens bot Spatial Awareness eine Sammlung von Gittern, die die Geometrie der Umgebung darstellen, die überzeugende Interaktionen zwischen Hologrammen und der realen Welt ermöglichte.</span><span class="sxs-lookup"><span data-stu-id="9079f-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="9079f-108">Derzeit wird das Mixed Reality Toolkit nicht mit Spatial Understanding-Algorithmen wie ursprünglich im HoloToolkit gepackt.</span><span class="sxs-lookup"><span data-stu-id="9079f-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="9079f-109">Spatial Understanding umfasst im Allgemeinen das Transformieren von Spatial Mesh-Daten, um vereinfachte und/oder gruppenvernetzte Daten wie Ebenen, Wände, Boden, Decken usw. zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9079f-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="9079f-110">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="9079f-110">Getting started</span></span>

<span data-ttu-id="9079f-111">Zum Hinzufügen von Unterstützung für spatial awareness sind zwei Hauptkomponenten des Mixed Reality Toolkits erforderlich: das Spatial Awareness-System und ein unterstützter Plattformanbieter.</span><span class="sxs-lookup"><span data-stu-id="9079f-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="9079f-112">[Aktivieren](#enable-the-spatial-awareness-system) des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="9079f-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="9079f-113">[Registrieren](#register-observers) und [Konfigurieren eines](configuring-spatial-awareness-mesh-observer.md) oder mehrere räumlicher Beobachter zum Bereitstellen von Gitternetzdaten</span><span class="sxs-lookup"><span data-stu-id="9079f-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="9079f-114">[Erstellen und Bereitstellen auf](#build-and-deploy) einer Plattform, die räumliche Wahrnehmung unterstützt</span><span class="sxs-lookup"><span data-stu-id="9079f-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="9079f-115">Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="9079f-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="9079f-116">Das Spatial Awareness-System wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungskomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="9079f-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="9079f-117">Führen Sie die folgenden Schritte aus, um das *Spatial Awareness-System im* *MixedRealityToolkit-Profil zu* aktivieren oder zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="9079f-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="9079f-118">Das Mixed Reality Toolkit enthält einige vorkonfigurierte Standardprofile.</span><span class="sxs-lookup"><span data-stu-id="9079f-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="9079f-119">Für einige davon ist das Spatial Awareness-System standardmäßig aktiviert oder deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="9079f-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="9079f-120">Die Absicht dieser Vorkonfiguration, insbesondere für deaktivierte, besteht in der Vermeidung des visuellen Aufwands beim Berechnen und Rendern der Gitternetze.</span><span class="sxs-lookup"><span data-stu-id="9079f-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="9079f-121">Profil</span><span class="sxs-lookup"><span data-stu-id="9079f-121">Profile</span></span> | <span data-ttu-id="9079f-122">Standardmäßig aktiviertes System</span><span class="sxs-lookup"><span data-stu-id="9079f-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="9079f-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span><span class="sxs-lookup"><span data-stu-id="9079f-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="9079f-124">Falsch</span><span class="sxs-lookup"><span data-stu-id="9079f-124">False</span></span> |
| <span data-ttu-id="9079f-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span><span class="sxs-lookup"><span data-stu-id="9079f-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="9079f-126">Falsch</span><span class="sxs-lookup"><span data-stu-id="9079f-126">False</span></span> |
| <span data-ttu-id="9079f-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span><span class="sxs-lookup"><span data-stu-id="9079f-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="9079f-128">Richtig</span><span class="sxs-lookup"><span data-stu-id="9079f-128">True</span></span> |

1. <span data-ttu-id="9079f-129">Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus, um es im Inspektorbereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="9079f-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![MRTK– Konfigurierte Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="9079f-131">Navigieren Sie zum Abschnitt *Spatial Awareness System,* und aktivieren Sie *Enable Spatial Awareness System (Raumbewusstseinssystem aktivieren).*</span><span class="sxs-lookup"><span data-stu-id="9079f-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![Aktivieren der räumlichen Wahrnehmung](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="9079f-133">Wählen Sie den gewünschten Implementierungstyp des Spatial Awareness-Systems aus.</span><span class="sxs-lookup"><span data-stu-id="9079f-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="9079f-134">ist [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) die bereitgestellte Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="9079f-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![Auswählen der Spatial Awareness-Systemimplementierung](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="9079f-136">Registrieren von Beobachtern</span><span class="sxs-lookup"><span data-stu-id="9079f-136">Register observers</span></span>

<span data-ttu-id="9079f-137">Dienste im Mixed Reality Toolkit können [](../../architecture/systems-extensions-providers.md) über Datenanbieter verfügen, die den Hauptdienst durch plattformspezifische Daten und Implementierungssteuerungen ergänzen.</span><span class="sxs-lookup"><span data-stu-id="9079f-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="9079f-138">Ein Beispiel hierfür ist das Mixed Reality Input [](../input/input-providers.md) System, das über mehrere Datenanbieter verfügt, um Controller- und andere zugehörige Eingabeinformationen von verschiedenen plattformspezifischen APIs zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9079f-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="9079f-139">Das Spatial Awareness-System ist ähnlich, da Datenanbieter dem System Gitternetzdaten über die reale Welt liefern.</span><span class="sxs-lookup"><span data-stu-id="9079f-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="9079f-140">Für das Profil "Räumliche Wahrnehmung" muss mindestens ein Spatial Observer registriert sein.</span><span class="sxs-lookup"><span data-stu-id="9079f-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="9079f-141">Raumbeobachter sind in der Regel plattformspezifische Komponenten, die als Anbieter für die Suche nach verschiedenen Arten von Gitterdaten von einem plattformspezifischen Endpunkt (d. h.</span><span class="sxs-lookup"><span data-stu-id="9079f-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="9079f-142">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="9079f-142">HoloLens).</span></span>

1. <span data-ttu-id="9079f-143">Öffnen oder Erweitern des *Profils "Spatial Awareness System"*</span><span class="sxs-lookup"><span data-stu-id="9079f-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![Profil des Spatial Awareness-Systems](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="9079f-145">Klicken Sie auf *die Schaltfläche "Räumlichen Beobachter hinzufügen".*</span><span class="sxs-lookup"><span data-stu-id="9079f-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="9079f-146">Auswählen des gewünschten *Implementierungstyps für räumliche Beobachter*</span><span class="sxs-lookup"><span data-stu-id="9079f-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![Auswählen der Spatial Observer-Implementierung](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="9079f-148">[Ändern von Konfigurationseigenschaften auf dem Beobachter](configuring-spatial-awareness-mesh-observer.md) nach Bedarf</span><span class="sxs-lookup"><span data-stu-id="9079f-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="9079f-149">Benutzer von `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) verfügen über ein vorkonfiguriertes Spatial Awareness-System für die Windows Mixed Reality-Plattform, die die -Klasse [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) verwendet.</span><span class="sxs-lookup"><span data-stu-id="9079f-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="9079f-150">Erstellen und Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="9079f-150">Build and deploy</span></span>

<span data-ttu-id="9079f-151">Sobald das Spatial Awareness-System mit den gewünschten Beobachtern konfiguriert wurde, kann das Projekt erstellt und auf der Zielplattform bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="9079f-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9079f-152">Wenn sie auf die Windows Mixed Reality-Plattform (z. B. HoloLens) abzielen, ist es wichtig sicherzustellen, dass die Spatial [Perception-Funktion](/windows/mixed-reality/spatial-mapping-in-unity) aktiviert ist, um das Spatial Awareness-System auf dem Gerät zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="9079f-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="9079f-153">Einige Plattformen, einschließlich Microsoft HoloLens, bieten Unterstützung für die Remoteausführung innerhalb von Unity.</span><span class="sxs-lookup"><span data-stu-id="9079f-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="9079f-154">Dieses Feature ermöglicht schnelle Entwicklung und Tests, ohne dass der Build- und Bereitstellungsschritt erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="9079f-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="9079f-155">Stellen Sie sicher, dass Sie abschließende Akzeptanztests mit einer erstellten und bereitgestellten Version der Anwendung durchführen, die auf der Zielhardware und -plattform ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9079f-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9079f-156">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="9079f-156">Next steps</span></span>

<span data-ttu-id="9079f-157">Nachdem Sie die oben beschriebenen Verfahren zum Aktivieren des Spatial Awareness-Systems durchgeführt haben, kann das System ausführlicher konfiguriert und gesteuert werden.</span><span class="sxs-lookup"><span data-stu-id="9079f-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="9079f-158">Informationen zum Konfigurieren von Beobachtern im Inspektor:</span><span class="sxs-lookup"><span data-stu-id="9079f-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="9079f-159">Konfigurieren von Beobachtern für bei der Gerätenutzung</span><span class="sxs-lookup"><span data-stu-id="9079f-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="9079f-160">Konfigurieren von Beobachtern für die Verwendung im Editor</span><span class="sxs-lookup"><span data-stu-id="9079f-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="9079f-161">Informationen zum Steuern und Erweitern von Beobachtern über Code:</span><span class="sxs-lookup"><span data-stu-id="9079f-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="9079f-162">Konfigurieren von Beobachtern über Code</span><span class="sxs-lookup"><span data-stu-id="9079f-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="9079f-163">Erstellen eines benutzerdefinierten Beobachters</span><span class="sxs-lookup"><span data-stu-id="9079f-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="9079f-164">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9079f-164">See also</span></span>

- [<span data-ttu-id="9079f-165">Dokumentation zur Spatial Awareness-API</span><span class="sxs-lookup"><span data-stu-id="9079f-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="9079f-166">Übersicht über spatial mapping WMR</span><span class="sxs-lookup"><span data-stu-id="9079f-166">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="9079f-167">Räumliche Zuordnung in Unity WMR</span><span class="sxs-lookup"><span data-stu-id="9079f-167">Spatial Mapping in Unity WMR</span></span>](/windows/mixed-reality/spatial-mapping-in-unity)
