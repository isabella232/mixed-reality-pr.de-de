---
title: Beobachter von Gittermodellen für räumliche Objekte
description: Dokumentation zum Spatial Mesh Observer in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144456"
---
# <a name="configuring-mesh-observers-for-the-editor"></a><span data-ttu-id="de2dc-104">Konfigurieren von Mesh-Beobachtern für den Editor</span><span class="sxs-lookup"><span data-stu-id="de2dc-104">Configuring mesh observers for the editor</span></span>

<span data-ttu-id="de2dc-105">Eine praktische Möglichkeit zum Bereitstellen von Umgebungsnetzdaten im Unity-Editor ist die Verwendung der [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="de2dc-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="de2dc-106">Der *Spatial Object Mesh Observer* ist ein editorbasierter Datenanbieter für das Spatial [Awareness-System,](spatial-awareness-getting-started.md) mit dem 3D-Modelldaten importiert werden können, um ein räumliches Gittermodell darzustellen.</span><span class="sxs-lookup"><span data-stu-id="de2dc-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="de2dc-107">Eine häufige Verwendung des *Spatial Object Mesh-Beobachters* ist das Importieren von Daten, die über einen Microsoft HoloLens gescannt werden, um zu testen, wie sich eine Umgebung an verschiedene Umgebungen innerhalb von Unity anpasst.</span><span class="sxs-lookup"><span data-stu-id="de2dc-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="de2dc-108">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="de2dc-108">Getting started</span></span>

<span data-ttu-id="de2dc-109">Dieser Leitfaden führt Sie durch das Einrichten eines *Spatial Object Mesh-Beobachters.*</span><span class="sxs-lookup"><span data-stu-id="de2dc-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="de2dc-110">Es gibt drei wichtige Schritte, um dieses Feature zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="de2dc-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="de2dc-111">Hinzufügen eines *Spatial Object Mesh-Beobachters* zum Systemprofil für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="de2dc-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="de2dc-112">Festlegen des Environment Mesh Data-Objekts</span><span class="sxs-lookup"><span data-stu-id="de2dc-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="de2dc-113">Konfigurieren der restlichen Mesh Observer-Profileigenschaften</span><span class="sxs-lookup"><span data-stu-id="de2dc-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="de2dc-114">Einrichten eines Beobachterprofils für *ein räumliches Objektgittermodell*</span><span class="sxs-lookup"><span data-stu-id="de2dc-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="de2dc-115">Wählen Sie das gewünschte *Mixed Reality Toolkit-Konfigurationsprofil* aus, oder wählen Sie das Mixed Reality *Toolkit-Objekt* in der Szene aus.</span><span class="sxs-lookup"><span data-stu-id="de2dc-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="de2dc-116">Öffnen oder erweitern Sie die Registerkarte *Spatial Awareness System (System für räumliche Wahrnehmung).*</span><span class="sxs-lookup"><span data-stu-id="de2dc-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="de2dc-117">Klicken Sie auf die Schaltfläche *"Räumlichen Beobachter hinzufügen".*</span><span class="sxs-lookup"><span data-stu-id="de2dc-117">Click on *"Add Spatial Observer"* button</span></span>

    ![Hinzufügen eines räumlichen Beobachters](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="de2dc-119">Wählen Sie den Typ *SpatialObjectMeshObserver* aus.</span><span class="sxs-lookup"><span data-stu-id="de2dc-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![Wählen Sie Spatial Object Mesh Observer aus.](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="de2dc-121">Wählen Sie das gewünschte *Spatial Mesh-Objekt aus.*</span><span class="sxs-lookup"><span data-stu-id="de2dc-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="de2dc-122">Standardmäßig wird der Beobachter mit einem Beispielmodell konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="de2dc-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="de2dc-123">Dieses Modell wurde mit einem Microsoft HoloLens erstellt, aber es ist [möglich, ein neues Scannetzobjekt](#acquiring-environment-scans)zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="de2dc-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="de2dc-124">Konfigurieren der restlichen Mesh Observer-Profileigenschaften</span><span class="sxs-lookup"><span data-stu-id="de2dc-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![Wählen Sie das Mesh-Objekt aus.](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="de2dc-126">Profilhinweise zum Beobachter für räumliches Objektgittermodell</span><span class="sxs-lookup"><span data-stu-id="de2dc-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="de2dc-127">Da der *Spatial Object Mesh Observer* Daten aus einem 3D-Modell lädt, werden einige der standarden Gittermodellbeobachtereinstellungen, die unten beschrieben sind, nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="de2dc-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="de2dc-128">**Updateintervall**</span><span class="sxs-lookup"><span data-stu-id="de2dc-128">**Update Interval**</span></span>

<span data-ttu-id="de2dc-129">Der  *Spatial Object Mesh Observer* sendet alle Gittermodelle an eine Anwendung, wenn das Modell geladen wird.</span><span class="sxs-lookup"><span data-stu-id="de2dc-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="de2dc-130">Es werden keine Zeitdeltata zwischen Updates simuliert.</span><span class="sxs-lookup"><span data-stu-id="de2dc-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="de2dc-131">Eine Anwendung kann die Mesh-Ereignisse durch Aufrufen von und [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) erneut [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) empfangen.</span><span class="sxs-lookup"><span data-stu-id="de2dc-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="de2dc-132">**Is Stationärer Beobachter**</span><span class="sxs-lookup"><span data-stu-id="de2dc-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="de2dc-133">Der *Spatial Object Mesh Observer* betrachtet alle 3D-Gittermodellobjekte als stationär und ignoriert den Ursprung.</span><span class="sxs-lookup"><span data-stu-id="de2dc-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="de2dc-134">**Observer Shape and Extents**</span><span class="sxs-lookup"><span data-stu-id="de2dc-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="de2dc-135">Der  *Spatial Object Mesh Observer* sendet das gesamte 3D-Gittermodell an die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="de2dc-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="de2dc-136">Beobachterform und -ausdrungen werden nicht berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="de2dc-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="de2dc-137">**Detail- und Dreiecksebene/Kubische Verbrauchsmessung**</span><span class="sxs-lookup"><span data-stu-id="de2dc-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="de2dc-138">Der Observer versucht beim Senden der Gittermodelle an die Anwendung nicht, 3D-Modell-LODs zu finden.</span><span class="sxs-lookup"><span data-stu-id="de2dc-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="de2dc-139">Abrufen von Umgebungsscans</span><span class="sxs-lookup"><span data-stu-id="de2dc-139">Acquiring environment scans</span></span>

<span data-ttu-id="de2dc-140">In diesem Abschnitt werden zusätzliche Informationen zum Erstellen und Sammeln von *Spatial Mesh-Objektdateien* für die Verwendung mit *dem Spatial Object Mesh Observer beschrieben.*</span><span class="sxs-lookup"><span data-stu-id="de2dc-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="de2dc-141">Windows-Geräteportal</span><span class="sxs-lookup"><span data-stu-id="de2dc-141">Windows Device Portal</span></span>

<span data-ttu-id="de2dc-142">Die [Windows-Geräteportal](/windows/mixed-reality/using-the-windows-device-portal) kann verwendet werden, um das räumliche Gitternetz als OBJ-Datei von einem Microsoft HoloLens herunterladen.</span><span class="sxs-lookup"><span data-stu-id="de2dc-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="de2dc-143">Scannen durch einfaches Gehen und Anzeigen der gewünschten Umgebung mit einer HoloLens</span><span class="sxs-lookup"><span data-stu-id="de2dc-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="de2dc-144">Stellen Sie mithilfe der -Anwendung eine Verbindung mit hololens Windows-Geräteportal</span><span class="sxs-lookup"><span data-stu-id="de2dc-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="de2dc-145">Navigieren Sie zur *Seite "3D-Ansicht".*</span><span class="sxs-lookup"><span data-stu-id="de2dc-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="de2dc-146">Klicken Sie im *Abschnitt Räumliche* Zuordnung auf *die Schaltfläche* Aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="de2dc-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="de2dc-147">Klicken Sie im *Abschnitt Räumliche* Zuordnung auf die *Schaltfläche* Speichern, um die OBJ-Datei auf dem PC zu speichern.</span><span class="sxs-lookup"><span data-stu-id="de2dc-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="de2dc-148">**HoloToolkit-ROOM-Dateien**</span><span class="sxs-lookup"><span data-stu-id="de2dc-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="de2dc-149">Viele Entwickler haben HoloToolkit zuvor verwendet, um Umgebungen zu überprüfen und RAUM-Dateien zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="de2dc-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="de2dc-150">Das Mixed Reality Toolkit unterstützt jetzt das Importieren dieser Dateien als GameObjects in Unity und deren Verwendung als *Spatial Mesh-Objekte* im Beobachter.</span><span class="sxs-lookup"><span data-stu-id="de2dc-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="de2dc-151">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="de2dc-151">See also</span></span>

- [<span data-ttu-id="de2dc-152">Profiles</span><span class="sxs-lookup"><span data-stu-id="de2dc-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="de2dc-153">Mixed Reality Toolkit-Profilkonfigurationshandbuch</span><span class="sxs-lookup"><span data-stu-id="de2dc-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="de2dc-154">Erste Schritte mit räumlichem Bewusstsein</span><span class="sxs-lookup"><span data-stu-id="de2dc-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="de2dc-155">Konfigurieren von Gitternetzbeobachtern auf dem Gerät</span><span class="sxs-lookup"><span data-stu-id="de2dc-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="de2dc-156">Konfigurieren von Mesh-Beobachtern per Code</span><span class="sxs-lookup"><span data-stu-id="de2dc-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="de2dc-157">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="de2dc-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)