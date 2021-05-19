---
title: Räumliche Wahrnehmung
description: beschreibt räumliche Wahrnehmung im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 776033dbb4736ccaa44cdb683c4fce284758a51c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144462"
---
# <a name="spatial-awareness"></a><span data-ttu-id="56dae-104">Räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="56dae-104">Spatial Awareness</span></span>

![Räumliche Wahrnehmung](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="56dae-106">Das Spatial Awareness-System bietet umgebungsbezogenes Bewusstsein in Mixed Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="56dae-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="56dae-107">Bei der Einführung in Microsoft HoloLens bot Spatial Awareness eine Sammlung von Gittern, die die Geometrie der Umgebung darstellen, die überzeugende Interaktionen zwischen Hologrammen und der realen Welt ermöglichte.</span><span class="sxs-lookup"><span data-stu-id="56dae-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="56dae-108">Derzeit wird das Mixed Reality Toolkit nicht mit Spatial Understanding-Algorithmen wie ursprünglich im HoloToolkit gepackt.</span><span class="sxs-lookup"><span data-stu-id="56dae-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="56dae-109">Spatial Understanding umfasst im Allgemeinen das Transformieren von Spatial Mesh-Daten, um vereinfachte und/oder gruppierte Gitterdaten wie Ebenen, Wand, Boden, Decken usw. zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dae-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="56dae-110">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="56dae-110">Getting started</span></span>

<span data-ttu-id="56dae-111">Zum Hinzufügen von Unterstützung für räumliche Wahrnehmung sind zwei Hauptkomponenten des Mixed Reality Toolkits erforderlich: das Spatial Awareness-System und ein unterstützter Plattformanbieter.</span><span class="sxs-lookup"><span data-stu-id="56dae-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="56dae-112">[Aktivieren](#enable-the-spatial-awareness-system) des Spatial Awareness-Systems</span><span class="sxs-lookup"><span data-stu-id="56dae-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="56dae-113">[Registrieren und](#register-observers) [Konfigurieren eines](configuring-spatial-awareness-mesh-observer.md) oder mehrere räumliche Beobachter zum Bereitstellen von Gitternetzdaten</span><span class="sxs-lookup"><span data-stu-id="56dae-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="56dae-114">[Erstellen und Bereitstellen auf](#build-and-deploy) einer Plattform, die räumliche Wahrnehmung unterstützt</span><span class="sxs-lookup"><span data-stu-id="56dae-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="56dae-115">Aktivieren des Systems für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="56dae-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="56dae-116">Das Spatial Awareness-System wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungskomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="56dae-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="56dae-117">Führen Sie die folgenden Schritte aus, um das *Spatial Awareness-System im* *MixedRealityToolkit-Profil zu* aktivieren oder zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="56dae-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="56dae-118">Das Mixed Reality Toolkit enthält einige vorkonfigurierte Standardprofile.</span><span class="sxs-lookup"><span data-stu-id="56dae-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="56dae-119">Bei einigen davon ist das Spatial Awareness-System standardmäßig aktiviert oder deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="56dae-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="56dae-120">Die Absicht dieser Vorkonfiguration, insbesondere für deaktivierte, besteht in der Vermeidung des visuellen Aufwands beim Berechnen und Rendern der Gitternetze.</span><span class="sxs-lookup"><span data-stu-id="56dae-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="56dae-121">Profil</span><span class="sxs-lookup"><span data-stu-id="56dae-121">Profile</span></span> | <span data-ttu-id="56dae-122">Standardmäßig aktiviertes System</span><span class="sxs-lookup"><span data-stu-id="56dae-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="56dae-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span><span class="sxs-lookup"><span data-stu-id="56dae-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="56dae-124">False</span><span class="sxs-lookup"><span data-stu-id="56dae-124">False</span></span> |
| <span data-ttu-id="56dae-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span><span class="sxs-lookup"><span data-stu-id="56dae-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="56dae-126">False</span><span class="sxs-lookup"><span data-stu-id="56dae-126">False</span></span> |
| <span data-ttu-id="56dae-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span><span class="sxs-lookup"><span data-stu-id="56dae-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="56dae-128">True</span><span class="sxs-lookup"><span data-stu-id="56dae-128">True</span></span> |

1. <span data-ttu-id="56dae-129">Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus, um es im Inspektorbereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="56dae-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="56dae-131">Navigieren Sie zum Abschnitt *Spatial Awareness System ,* und aktivieren Sie *Räumliches Wahrnehmungssystem aktivieren.*</span><span class="sxs-lookup"><span data-stu-id="56dae-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![Aktivieren der räumlichen Wahrnehmung](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="56dae-133">Wählen Sie den gewünschten Implementierungstyp für das Spatial Awareness-System aus.</span><span class="sxs-lookup"><span data-stu-id="56dae-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="56dae-134">Der [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) ist die standardmäßig bereitgestellte .</span><span class="sxs-lookup"><span data-stu-id="56dae-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![Auswählen der Spatial Awareness System-Implementierung](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="56dae-136">Registrieren von Beobachtern</span><span class="sxs-lookup"><span data-stu-id="56dae-136">Register observers</span></span>

<span data-ttu-id="56dae-137">Dienste im Mixed Reality Toolkit können [über Datenanbieter Dienste](../../architecture/systems-extensions-providers.md) verfügen, die den Hauptdienst durch plattformspezifische Daten- und Implementierungssteuerelemente ergänzen.</span><span class="sxs-lookup"><span data-stu-id="56dae-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="56dae-138">Ein Beispiel hierfür ist das Mixed Reality Eingabesystem, das [über mehrere Datenanbieter](../input/input-providers.md) verfügt, um Controller- und andere zugehörige Eingabeinformationen von verschiedenen plattformspezifischen APIs abzurufen.</span><span class="sxs-lookup"><span data-stu-id="56dae-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="56dae-139">Das Spatial Awareness-System ist ähnlich, da Datenanbieter das System mit Gitterdaten über die reale Welt bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="56dae-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="56dae-140">Für das Profil räumliche Wahrnehmung muss mindestens ein Spatial Observer registriert sein.</span><span class="sxs-lookup"><span data-stu-id="56dae-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="56dae-141">Räumliche Beobachter sind im Allgemeinen plattformspezifische Komponenten, die als Anbieter für die Erkennung verschiedener Arten von Meshdaten von einem plattformspezifischen Endpunkt (d. h.</span><span class="sxs-lookup"><span data-stu-id="56dae-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="56dae-142">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="56dae-142">HoloLens).</span></span>

1. <span data-ttu-id="56dae-143">Öffnen oder Erweitern des *Profils "Spatial Awareness System"*</span><span class="sxs-lookup"><span data-stu-id="56dae-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![Spatial Awareness System Profile](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="56dae-145">Klicken Sie auf die Schaltfläche *"Räumlichen Beobachter hinzufügen".*</span><span class="sxs-lookup"><span data-stu-id="56dae-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="56dae-146">Auswählen des gewünschten *Implementierungstyps für räumliche Beobachter*</span><span class="sxs-lookup"><span data-stu-id="56dae-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![Auswählen der Spatial Observer-Implementierung](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="56dae-148">[Ändern der Konfigurationseigenschaften für den Beobachter](configuring-spatial-awareness-mesh-observer.md) nach Bedarf</span><span class="sxs-lookup"><span data-stu-id="56dae-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="56dae-149">Benutzer von `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profile) haben das Spatial Awareness-System für die Windows Mixed Reality Plattform vorkonfiguriert, die die [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) -Klasse verwendet.</span><span class="sxs-lookup"><span data-stu-id="56dae-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="56dae-150">Erstellen und Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="56dae-150">Build and deploy</span></span>

<span data-ttu-id="56dae-151">Sobald das Spatial Awareness-System mit den gewünschten Beobachtern konfiguriert wurde, kann das Projekt erstellt und auf der Zielplattform bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="56dae-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56dae-152">Wenn sie auf Windows Mixed Reality Zielplattform (z. B. HoloLens) abzielen, ist es wichtig, sicherzustellen, dass die Spatial Perception-Funktion aktiviert ist, um das Spatial [Awareness-System](/windows/mixed-reality/spatial-mapping-in-unity) auf dem Gerät zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="56dae-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="56dae-153">Einige Plattformen, einschließlich Microsoft HoloLens, bieten Unterstützung für die Remoteausführung innerhalb von Unity.</span><span class="sxs-lookup"><span data-stu-id="56dae-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="56dae-154">Dieses Feature ermöglicht schnelle Entwicklung und Tests, ohne dass der Build- und Bereitstellungsschritt erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="56dae-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="56dae-155">Stellen Sie sicher, dass Sie abschließende Akzeptanztests mit einer erstellten und bereitgestellten Version der Anwendung durchführen, die auf der Zielhardware und -plattform ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="56dae-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="56dae-156">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="56dae-156">Next steps</span></span>

<span data-ttu-id="56dae-157">Nachdem Sie die oben beschriebenen Verfahren zum Aktivieren des Spatial Awareness-Systems durchgeführt haben, kann das System ausführlicher konfiguriert und gesteuert werden.</span><span class="sxs-lookup"><span data-stu-id="56dae-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="56dae-158">Informationen zum Konfigurieren von Beobachtern im Inspektor:</span><span class="sxs-lookup"><span data-stu-id="56dae-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="56dae-159">Konfigurieren von Beobachtern für bei der Gerätenutzung</span><span class="sxs-lookup"><span data-stu-id="56dae-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="56dae-160">Konfigurieren von Beobachtern für die Verwendung im Editor</span><span class="sxs-lookup"><span data-stu-id="56dae-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="56dae-161">Informationen zum Steuern und Erweitern von Beobachtern über Code:</span><span class="sxs-lookup"><span data-stu-id="56dae-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="56dae-162">Konfigurieren von Beobachtern über Code</span><span class="sxs-lookup"><span data-stu-id="56dae-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="56dae-163">Erstellen eines benutzerdefinierten Beobachters</span><span class="sxs-lookup"><span data-stu-id="56dae-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="56dae-164">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="56dae-164">See also</span></span>

- [<span data-ttu-id="56dae-165">Dokumentation zur Spatial Awareness-API</span><span class="sxs-lookup"><span data-stu-id="56dae-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="56dae-166">Übersicht über spatial mapping WMR</span><span class="sxs-lookup"><span data-stu-id="56dae-166">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="56dae-167">Räumliche Zuordnung in Unity WMR</span><span class="sxs-lookup"><span data-stu-id="56dae-167">Spatial Mapping in Unity WMR</span></span>](/windows/mixed-reality/spatial-mapping-in-unity)