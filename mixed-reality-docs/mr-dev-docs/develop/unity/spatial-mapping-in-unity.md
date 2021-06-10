---
title: Räumliche Abbildung in Unity
description: Erfahren Sie, wie Sie rendering und colliding mit der realen Geometrie um Sie herum in Unity Mixed Reality-Apps verwenden und verwalten.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, räumliche Abbildung, Renderer, Collider, Gitter, Scannen, Komponente, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: fa571a13ce192b29b2a35033b55061f3ffb707da
ms.sourcegitcommit: ec80ef1e496bf0b17a161735535517e87ffdd364
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "110351778"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="b7d6e-104">Räumliche Abbildung in Unity</span><span class="sxs-lookup"><span data-stu-id="b7d6e-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="b7d6e-105">[Mit der räumlichen](../../design/spatial-mapping.md) Zuordnung können Sie Dreiecksgitternetze abrufen, die die Oberflächen in der Welt um ein HoloLens-Gerät darstellen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-105">[spatial mapping](../../design/spatial-mapping.md) lets you retrieve triangle meshes that represent the surfaces in the world around a HoloLens device.</span></span> <span data-ttu-id="b7d6e-106">Sie können Oberflächendaten für die Platzierung, Okklusion und Raumanalyse verwenden, um Ihren Unity-Projekten eine zusätzliche Portion Immersion zu bieten.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-106">You can use surface data for placement, occlusion, and room analysis to give your Unity projects an extra dose of immersion.</span></span>

<span data-ttu-id="b7d6e-107">Unity bietet vollständige Unterstützung für die räumliche Zuordnung, die Entwicklern auf folgende Weise zur Verfügung steht:</span><span class="sxs-lookup"><span data-stu-id="b7d6e-107">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>

1. <span data-ttu-id="b7d6e-108">Im MixedRealityToolkit verfügbare Räumliche Zuordnungskomponenten, die einen komfortablen und schnellen Pfad für die ersten Schritte mit der räumlichen Zuordnung bereitstellen</span><span class="sxs-lookup"><span data-stu-id="b7d6e-108">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="b7d6e-109">APIs für die räumliche Zuordnung auf niedrigerer Ebene, die vollständige Kontrolle bieten und komplexere anwendungsspezifische Anpassungen ermöglichen</span><span class="sxs-lookup"><span data-stu-id="b7d6e-109">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application-specific customization</span></span>

<span data-ttu-id="b7d6e-110">Um die räumliche Zuordnung in Ihrer App zu verwenden, muss die spatialPerception-Funktion in Ihrem AppxManifest festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-110">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="b7d6e-111">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="b7d6e-111">Device support</span></span>

| <span data-ttu-id="b7d6e-112">Funktion</span><span class="sxs-lookup"><span data-stu-id="b7d6e-112">Feature</span></span> | [<span data-ttu-id="b7d6e-113">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="b7d6e-113">HoloLens (first gen)</span></span>](/hololens/hololens1-hardware) | [<span data-ttu-id="b7d6e-114">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b7d6e-114">HoloLens 2</span></span>](/hololens/hololens2-hardware) | [<span data-ttu-id="b7d6e-115">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="b7d6e-115">Immersive headsets</span></span>](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| <span data-ttu-id="b7d6e-116">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="b7d6e-116">Spatial mapping</span></span> | <span data-ttu-id="b7d6e-117">✔️</span><span class="sxs-lookup"><span data-stu-id="b7d6e-117">✔️</span></span> | <span data-ttu-id="b7d6e-118">✔️</span><span class="sxs-lookup"><span data-stu-id="b7d6e-118">✔️</span></span> | ❌ |

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="b7d6e-119">Festlegen der SpatialPerception-Funktion</span><span class="sxs-lookup"><span data-stu-id="b7d6e-119">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="b7d6e-120">Damit eine App räumliche Zuordnungsdaten nutzen kann, muss die SpatialPerception-Funktion aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-120">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="b7d6e-121">Aktivieren der SpatialPerception-Funktion:</span><span class="sxs-lookup"><span data-stu-id="b7d6e-121">How to enable the SpatialPerception capability:</span></span>

1. <span data-ttu-id="b7d6e-122">Öffnen Sie im Unity-Editor den **Bereich "Playereinstellungen"** (Bearbeiten > Projekteinstellungen > Player).</span><span class="sxs-lookup"><span data-stu-id="b7d6e-122">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="b7d6e-123">Wählen Sie auf der **Registerkarte "Windows Store" aus.**</span><span class="sxs-lookup"><span data-stu-id="b7d6e-123">Select on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="b7d6e-124">Erweitern **Sie "Veröffentlichungseinstellungen",** und überprüfen Sie die **Funktion "SpatialPerception"** in der **Liste "Funktionen".**</span><span class="sxs-lookup"><span data-stu-id="b7d6e-124">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

> [!NOTE]
> <span data-ttu-id="b7d6e-125">Wenn Sie Ihr Unity-Projekt bereits in eine Visual Studio-Projektmappe exportiert haben, müssen Sie entweder in einen neuen Ordner exportieren oder diese Funktion manuell im [AppxManifest in](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-125">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="b7d6e-126">Für die räumliche Zuordnung ist außerdem ein MaxVersionTested-Objekt von mindestens 10.0.10586.0 erforderlich:</span><span class="sxs-lookup"><span data-stu-id="b7d6e-126">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>

1. <span data-ttu-id="b7d6e-127">Klicken Visual Studio mit der rechten Maustaste auf **Package.appxmanifest** im Projektmappen-Explorer und wählen Sie **Code anzeigen aus.**</span><span class="sxs-lookup"><span data-stu-id="b7d6e-127">In Visual Studio, right-click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="b7d6e-128">Suchen Sie die Zeile mit **TargetDeviceFamily,** und ändern Sie **MaxVersionTested="10.0.10240.0"** in **MaxVersionTested="10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="b7d6e-128">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="b7d6e-129">**Speichern** Sie package.appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-129">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="b7d6e-130">Erste Schritte mit den integrierten Komponenten der räumlichen Zuordnung von Unity</span><span class="sxs-lookup"><span data-stu-id="b7d6e-130">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="b7d6e-131">Unity bietet zwei Komponenten zum einfachen Hinzufügen von räumlicher Zuordnung zu Ihrer App: **Spatial Mapping Renderer** und **Spatial Mapping Collider.**</span><span class="sxs-lookup"><span data-stu-id="b7d6e-131">Unity offers two components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="b7d6e-132">Renderer für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="b7d6e-132">Spatial Mapping Renderer</span></span>

<span data-ttu-id="b7d6e-133">Der Renderer für räumliche Zuordnung ermöglicht die Visualisierung des Gitters für räumliche Zuordnungen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-133">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Spatial Mapping Renderer in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="b7d6e-135">Spatial Mapping Collider</span><span class="sxs-lookup"><span data-stu-id="b7d6e-135">Spatial Mapping Collider</span></span>

<span data-ttu-id="b7d6e-136">Der Spatial Mapping Collider ermöglicht holografische Inhaltsinteraktion (oder Zeicheninteraktion, z. B. Physik) mit dem Gitternetz der räumlichen Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-136">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Spatial Mapping Collider in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="b7d6e-138">Verwenden der integrierten Räumlichen Zuordnungskomponenten</span><span class="sxs-lookup"><span data-stu-id="b7d6e-138">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="b7d6e-139">Sie können Ihrer App beide Komponenten hinzufügen, wenn Sie sowohl physische Oberflächen visualisieren als auch mit ihnen interagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-139">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="b7d6e-140">So verwenden Sie diese beiden Komponenten in Ihrer Unity-App:</span><span class="sxs-lookup"><span data-stu-id="b7d6e-140">To use these two components in your Unity app:</span></span>

1. <span data-ttu-id="b7d6e-141">Wählen Sie ein GameObject in der Mitte des Bereichs aus, in dem Sie Gitternetze für räumliche Oberflächen erkennen möchten.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-141">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="b7d6e-142">Fügen Sie im Inspektorfenster **komponente**  >  **XR**  >  **Spatial Mapping Collider oder** Spatial Mapping **Renderer hinzu.**</span><span class="sxs-lookup"><span data-stu-id="b7d6e-142">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="b7d6e-143">Weitere Informationen zur Verwendung dieser Komponenten finden Sie auf der <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity-Dokumentationswebsite.</a></span><span class="sxs-lookup"><span data-stu-id="b7d6e-143">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="b7d6e-144">Über die integrierten Räumlichen Zuordnungskomponenten hinausgehen</span><span class="sxs-lookup"><span data-stu-id="b7d6e-144">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="b7d6e-145">Diese Komponenten machen es einfach, mit Drag & Drop mit der räumlichen Zuordnung zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-145">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span>  <span data-ttu-id="b7d6e-146">Wenn Sie weiter gehen möchten, gibt es zwei Hauptpfade, die Sie erkunden können:</span><span class="sxs-lookup"><span data-stu-id="b7d6e-146">When you want to go further, there are two main paths to explore:</span></span>

* <span data-ttu-id="b7d6e-147">Informationen zur eigenen Gitternetzverarbeitung auf niedrigerer Ebene finden Sie im folgenden Abschnitt zur Skript-API für die räumliche Zuordnung auf niedriger Ebene.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-147">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="b7d6e-148">Informationen zur Gitternetzanalyse auf höherer Ebene finden Sie im abschnitt unten zur SpatialUnderstanding-Bibliothek in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit.</a></span><span class="sxs-lookup"><span data-stu-id="b7d6e-148">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="b7d6e-149">Verwenden der Unity Spatial Mapping-API auf niedriger Ebene</span><span class="sxs-lookup"><span data-stu-id="b7d6e-149">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="b7d6e-150">Wenn Sie mehr Kontrolle benötigen, als die Komponenten Spatial Mapping Renderer und Spatial Mapping Collider bieten, verwenden Sie die low-level Spatial Mapping-APIs.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-150">If you need more control than the Spatial Mapping Renderer and Spatial Mapping Collider components offer, use the low-level Spatial Mapping APIs.</span></span>

<span data-ttu-id="b7d6e-151">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="b7d6e-151">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="b7d6e-152">**Typen:** *SurfaceObserver,* *SurfaceChange,* *SurfaceData,* *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="b7d6e-152">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="b7d6e-153">Wir haben den vorgeschlagenen Ablauf für eine Anwendung beschrieben, die die APIs für die räumliche Zuordnung in den folgenden Abschnitten verwendet.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-153">We've outlined the suggested flow for an application that uses the spatial mapping APIs in the sections below.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="b7d6e-154">Einrichten der SurfaceObserver</span><span class="sxs-lookup"><span data-stu-id="b7d6e-154">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="b7d6e-155">Instanziieren Sie ein SurfaceObserver-Objekt für jeden anwendungsdefinierten Raumbereich, für den Sie räumliche Zuordnungsdaten benötigen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-155">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

<span data-ttu-id="b7d6e-156">Geben Sie den Bereich des Speicherplatzes an, für den jedes SurfaceObserver-Objekt Daten bereitstellen soll, indem Sie Entweder SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox oder SetVolumeAsFrustum aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-156">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="b7d6e-157">Sie können den Bereich des Raumes in Zukunft neu definieren, indem Sie einfach eine dieser Methoden erneut aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-157">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="b7d6e-158">Wenn Sie SurfaceObserver.Update() aufrufen, müssen Sie einen Handler für jede räumliche Oberfläche im Raumbereich des SurfaceObserver bereitstellen, für den das Raumzuordnungssystem neue Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-158">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="b7d6e-159">Der Handler empfängt für eine räumliche Oberfläche:</span><span class="sxs-lookup"><span data-stu-id="b7d6e-159">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a><span data-ttu-id="b7d6e-160">Behandeln von Oberflächenänderungen</span><span class="sxs-lookup"><span data-stu-id="b7d6e-160">Handling Surface Changes</span></span>

<span data-ttu-id="b7d6e-161">Es gibt mehrere Hauptfälle, die behandelt werden müssen: hinzugefügt und aktualisiert, die denselben Codepfad verwenden und entfernt werden können.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-161">There are several main cases to handle - added and updated, which can use the same code path, and removed.</span></span>

* <span data-ttu-id="b7d6e-162">In den hinzugefügten und aktualisierten Fällen fügen wir das GameObject hinzu, das dieses Gitternetz darstellt, rufen es aus dem Wörterbuch ab, erstellen eine SurfaceData-Struktur mit den erforderlichen Komponenten und rufen dann RequestMeshDataAsync auf, um das GameObject mit den Gitterdaten und der Position in der Szene zu füllen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-162">In the added and updated cases, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="b7d6e-163">Im entfernten Fall entfernen wir das GameObject, das dieses Gitternetz darstellt, aus dem Wörterbuch und zerstören es.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-163">In the removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects =
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    switch (changeType)
    {
        case SurfaceChange.Added:
        case SurfaceChange.Updated:
            if (!spatialMeshObjects.ContainsKey(surfaceId))
            {
                spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                spatialMeshObjects[surfaceId].transform.parent = this.transform;
                spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
            }
            GameObject target = spatialMeshObjects[surfaceId];
            SurfaceData sd = new SurfaceData(
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                true
            );

            SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
            break;
        case SurfaceChange.Removed:
            var obj = spatialMeshObjects[surfaceId];
            spatialMeshObjects.Remove(surfaceId);
            if (obj != null)
            {
                GameObject.Destroy(obj);
            }
            break;
        default:
            break;
    }
}
```

### <a name="handling-data-ready"></a><span data-ttu-id="b7d6e-164">Verarbeiten von Daten bereit</span><span class="sxs-lookup"><span data-stu-id="b7d6e-164">Handling Data Ready</span></span>

<span data-ttu-id="b7d6e-165">Der OnDataReady-Handler empfängt ein SurfaceData-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="b7d6e-166">Die enthaltenen Objekte WorldAnchor, MeshFilter und (optional) MeshCollider spiegeln den aktuellen Zustand der zugeordneten räumlichen Oberfläche wider.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-166">The WorldAnchor, MeshFilter, and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="b7d6e-167">Optional können Sie die [](../../design/spatial-mapping.md#mesh-processing) Gittermodelldaten analysieren und/oder verarbeiten, indem Sie auf den Mesh-Member des MeshFilter-Objekts zugreifen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-167">Optionally, analyze and/or [process](../../design/spatial-mapping.md#mesh-processing) the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="b7d6e-168">Rendern Sie die räumliche Oberfläche mit dem neuesten Gitternetz, und verwenden Sie sie (optional) für physikalische Kollisionen und Raycasts.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="b7d6e-169">Es ist wichtig zu bestätigen, dass der Inhalt von SurfaceData nicht NULL ist.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-169">It's important to confirm that the contents of the SurfaceData aren't null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="b7d6e-170">Starten der Verarbeitung von Updates</span><span class="sxs-lookup"><span data-stu-id="b7d6e-170">Start processing on updates</span></span>

<span data-ttu-id="b7d6e-171">SurfaceObserver.Update() sollte bei einer Verzögerung aufgerufen werden, nicht bei jedem Frame.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while(true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```

## <a name="higher-level-mesh-analysis-spatial-understanding"></a><span data-ttu-id="b7d6e-172">Gitternetzanalyse auf höherer Ebene: Räumliches Verständnis</span><span class="sxs-lookup"><span data-stu-id="b7d6e-172">Higher-level mesh analysis: Spatial Understanding</span></span>

> [!CAUTION]
> <span data-ttu-id="b7d6e-173">Spatial Understanding wurde zugunsten von Scene Understanding als veraltet [bezeichnet.](../../design/scene-understanding.md)</span><span class="sxs-lookup"><span data-stu-id="b7d6e-173">Spatial Understanding has been deprecated in favor of [Scene Understanding](../../design/scene-understanding.md).</span></span>

<span data-ttu-id="b7d6e-174">Das <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> ist eine Sammlung von Hilfsprogrammcode für die holografische Entwicklung, die auf den holografischen APIs von Unity basiert.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-174">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of utility code for holographic development built on Unity's holographic APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="b7d6e-175">Räumliches Verständnis</span><span class="sxs-lookup"><span data-stu-id="b7d6e-175">Spatial Understanding</span></span>

<span data-ttu-id="b7d6e-176">Wenn Hologramme in der physischen Welt platziert werden, ist es oft wünschenswert, über die Gitter- und Oberflächenebenen der räumlichen Zuordnung hinaus zu gehen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-176">When placing holograms in the physical world, it's often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="b7d6e-177">Wenn die Platzierung prozedural erfolgt, ist ein höheres Maß an Umgebungsverständnis wünschenswert.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-177">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="b7d6e-178">Dies erfordert in der Regel Entscheidungen darüber, was Boden, Decke und Wand sind.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-178">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="b7d6e-179">Sie haben auch die Möglichkeit, mit einer Reihe von Platzierungseinschränkungen zu optimieren, um die besten physischen Standorte für holografische Objekte zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-179">You also have the ability to optimize against a set of placement constraints to determine the most best physical locations for holographic objects.</span></span>

<span data-ttu-id="b7d6e-180">Während der Entwicklung von Young Conker und Fragmenten stand Asobo Studio diesem Problem gegenüber, indem es einen Raum-Solver entwickelt hat.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-180">During development of Young Conker and Fragments, Asobo Studios faced this problem head on by developing a room solver.</span></span> <span data-ttu-id="b7d6e-181">Jedes dieser Spiele hatte spielspezifische Anforderungen, aber es wurde eine gemeinsame Technologie für räumliches Verständnis genutzt.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-181">Each of these games had game-specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="b7d6e-182">Die HoloToolkit.SpatialUnderstanding-Bibliothek kapselt diese Technologie, sodass Sie schnell leere Räume an den Wänden finden, Objekte an der Decke platzieren, platzierte Zeichen erkennen und unzählige andere Abfragen des räumlichen Verständnisses finden können.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-182">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="b7d6e-183">Der ganze Quellcode ist enthalten, sodass Sie ihn an Ihre Anforderungen anpassen und Ihre Verbesserungen für die Community freigeben können.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-183">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="b7d6e-184">Der Code für den C++-Solver wurde in eine UWP-DLL umschlossen und für Unity mit einem Drop in Prefab verfügbar gemacht, das im MixedRealityToolkit enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-184">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="b7d6e-185">Grundlegendes zu Modulen</span><span class="sxs-lookup"><span data-stu-id="b7d6e-185">Understanding Modules</span></span>

<span data-ttu-id="b7d6e-186">Es gibt drei primäre Schnittstellen, die vom Modul verfügbar gemacht werden: Topologie für einfache Oberflächen- und räumliche Abfragen, Form für die Objekterkennung und der Objektplatzierungs-Solver für die einschränkungsbasierte Platzierung von Objektsätzen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-186">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint-based placement of object sets.</span></span> <span data-ttu-id="b7d6e-187">Beide Methoden werden im Folgenden beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-187">Each of these is described below.</span></span> <span data-ttu-id="b7d6e-188">Zusätzlich zu den drei primären Modulschnittstellen kann eine Raycastschnittstelle verwendet werden, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes wasserdichtes Playspacenetz kann kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-188">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="b7d6e-189">RayCasting</span><span class="sxs-lookup"><span data-stu-id="b7d6e-189">Ray Casting</span></span>

<span data-ttu-id="b7d6e-190">Nach Abschluss des Raumscans werden Bezeichnungen für Oberflächen wie Boden, Decke und Wand intern generiert.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-190">After the room scan is completed, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="b7d6e-191">Die Funktion nimmt einen Strahl und gibt zurück, wenn der Strahl mit einer bekannten Oberfläche kollidiert, und wenn ja, Informationen über diese Oberfläche `PlayspaceRaycast` in Form eines `RaycastResult` .</span><span class="sxs-lookup"><span data-stu-id="b7d6e-191">The `PlayspaceRaycast` function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a `RaycastResult`.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology,
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface,
                    //  but vertical surface that looks like a
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="b7d6e-192">Intern wird der Raycast anhand der berechneten 8 cm großen voxelbasierten Voxeldarstellung des Playspace berechnet.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-192">Internally, the raycast is computed against the computed 8-cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="b7d6e-193">Jedes Voxel enthält eine Reihe von Oberflächenelementen mit verarbeiteten Topologiedaten (auch bekannt als Surfel).</span><span class="sxs-lookup"><span data-stu-id="b7d6e-193">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="b7d6e-194">Die in der überschneidenden Voxelzelle enthaltenen Surfel werden verglichen, und die beste Übereinstimmung wird zum Suchen der Topologieinformationen verwendet.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-194">The surfels contained within the intersected voxel cell is compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="b7d6e-195">Diese Topologiedaten enthalten die Bezeichnungen, die in Form der Enumeration "SurfaceTypes" zurückgegeben werden, sowie die Oberfläche der überschneidenden Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-195">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="b7d6e-196">Im Unity-Beispiel wirft der Cursor einen Strahl in jeden Frame.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-196">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="b7d6e-197">Zuerst gegen die Collider von Unity.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-197">First, against Unity’s colliders.</span></span> <span data-ttu-id="b7d6e-198">Zweitens gegen die Weltdarstellung des Understanding-Moduls.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-198">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="b7d6e-199">Und schließlich wieder Benutzeroberflächenelemente.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-199">And finally, again UI elements.</span></span> <span data-ttu-id="b7d6e-200">In dieser Anwendung erhält die Benutzeroberfläche Priorität, als Nächstes das Verständnisergebnis und schließlich die Collider von Unity.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-200">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="b7d6e-201">SurfaceType wird als Text neben dem Cursor gemeldet.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-201">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="b7d6e-202">![Der Oberflächentyp wird neben dem Cursor bezeichnet.](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b7d6e-202">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="b7d6e-203">*Surface type (Oberflächentyp) wird neben dem Cursor bezeichnet.*</span><span class="sxs-lookup"><span data-stu-id="b7d6e-203">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="b7d6e-204">Topologieabfragen</span><span class="sxs-lookup"><span data-stu-id="b7d6e-204">Topology Queries</span></span>

<span data-ttu-id="b7d6e-205">Innerhalb der DLL übernimmt der Topologie-Manager die Bezeichnung der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-205">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="b7d6e-206">Wie bereits erwähnt, werden viele der Daten in Surfel gespeichert, die in einem Voxelvolumen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-206">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="b7d6e-207">Darüber hinaus wird die "PlaySpaceInfos"-Struktur verwendet, um Informationen zum Playspace zu speichern, einschließlich der Ausrichtung der Welt (weitere Details dazu unten), der Höhe des Bodens und der Decke.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-207">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="b7d6e-208">Heuristiken werden zum Bestimmen von Boden, Decke und Wand verwendet.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-208">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="b7d6e-209">Beispielsweise wird die größte und niedrigste horizontale Oberfläche mit einer Fläche von mehr als 1 m2 als Boden betrachtet.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-209">For example, the largest and lowest horizontal surface with greater than 1-m2 surface area is considered the floor.</span></span>

> [!NOTE]
> <span data-ttu-id="b7d6e-210">In diesem Prozess wird auch der Kamerapfad während des Scanvorgangs verwendet.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-210">The camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="b7d6e-211">Eine Teilmenge der vom Topologie-Manager verfügbar gemachten Abfragen wird über die DLL verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-211">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="b7d6e-212">Die verfügbar gemachten Topologieabfragen lauten wie folgt.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-212">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="b7d6e-213">Jede der Abfragen verfügt über eine Reihe von Parametern, die für den Abfragetyp spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-213">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="b7d6e-214">Im folgenden Beispiel gibt der Benutzer die Mindesthöhe & Breite des gewünschten Volumes, die mindeste Platzierungshöhe über dem Boden und die Mindestmenge an Belägen vor dem Volume an.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-214">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="b7d6e-215">Alle Messungen werden in Metern durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-215">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="b7d6e-216">Jede dieser Abfragen nimmt ein vorab zugeordnetes Array von "TopologyResult"-Strukturen an.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-216">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="b7d6e-217">Der Parameter "locationCount" gibt die Länge des übergebenen Arrays an.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-217">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="b7d6e-218">Der Rückgabewert gibt die Anzahl der zurückgegebenen Speicherorte an.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-218">The return value reports the number of returned locations.</span></span> <span data-ttu-id="b7d6e-219">Diese Zahl ist nie größer als der übergebene "locationCount"-Parameter.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-219">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="b7d6e-220">Das "TopologyResult" enthält die Mittelpunktposition des zurückgegebenen Volumes, die Ausrichtungsrichtung (d. h. normal) und die Abmessungen des gefundenen Raums.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-220">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult
{
    DirectX::XMFLOAT3 position;
    DirectX::XMFLOAT3 normal;
    float width;
    float length;
};
```

> [!NOTE]
> <span data-ttu-id="b7d6e-221">Im Unity-Beispiel wird jede dieser Abfragen mit einer Schaltfläche im Bereich der virtuellen Benutzeroberfläche verknüpft.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-221">In the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="b7d6e-222">Im Beispiel werden die Parameter für jede dieser Abfragen mit angemessenen Werten hartkodiert.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-222">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="b7d6e-223">Weitere Beispiele finden Sie unter SpaceVisualizer.cs im Beispielcode.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-223">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="b7d6e-224">Formabfragen</span><span class="sxs-lookup"><span data-stu-id="b7d6e-224">Shape Queries</span></span>

<span data-ttu-id="b7d6e-225">In der DLL verwendet das Shape-Analyseprogramm ("ShapeAnalyzer_W") die Topologieanalyse, um mit benutzerdefinierten Formen zu übereinstimmen, die vom Benutzer definiert wurden.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-225">In the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="b7d6e-226">Das Unity-Beispiel definiert eine Reihe von Formen und macht die Ergebnisse über das Abfragemenü in der App auf der Registerkarte Form verfügbar. Die Absicht ist, dass der Benutzer seine eigenen Objektformabfragen definieren und diese nach Bedarf von seiner Anwendung verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-226">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="b7d6e-227">Die Formanalyse funktioniert nur auf horizontalen Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-227">The shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="b7d6e-228">Eine Couch wird z. B. durch die flache Seatoberfläche und die flache Oberseite der Couch zurück definiert.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-228">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="b7d6e-229">Die Shape-Abfrage sucht nach zwei Oberflächen mit einer bestimmten Größe, Höhe und einem bestimmten Seitenbereich, bei denen die beiden Oberflächen ausgerichtet und verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-229">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="b7d6e-230">Unter Verwendung der APIs-Terminologie sind der Couchplatz und die Rückseite Formkomponenten, und die Ausrichtungsanforderungen sind Shape-Komponenteneinschränkungen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-230">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="b7d6e-231">Eine im Unity-Beispiel (ShapeDefinition.cs) definierte Beispielabfrage für "sittable"-Objekte lautet wie folgt.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-231">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="b7d6e-232">Jede Shape-Abfrage wird durch einen Satz von Formkomponenten definiert, die jeweils eine Reihe von Komponenteneinschränkungen und eine Reihe von Shape-Einschränkungen aufweisen, die Abhängigkeiten zwischen den Komponenten auflisten.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-232">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="b7d6e-233">Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponentendefinition und keine Shape-Einschränkungen zwischen Komponenten (da es nur eine Komponente gibt).</span><span class="sxs-lookup"><span data-stu-id="b7d6e-233">This example includes three constraints in a single component definition and no shape constraints between components (as there's only one component).</span></span>

<span data-ttu-id="b7d6e-234">Im Gegensatz dazu verfügt die Form "Couch" über zwei Formkomponenten und vier Formeinschränkungen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-234">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="b7d6e-235">Komponenten werden durch ihren Index in der Komponentenliste des Benutzers identifiziert (in diesem Beispiel 0 und 1).</span><span class="sxs-lookup"><span data-stu-id="b7d6e-235">Components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="b7d6e-236">Wrapperfunktionen werden im Unity-Modul zur einfachen Erstellung benutzerdefinierter Shape-Definitionen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-236">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="b7d6e-237">Die vollständige Liste der Komponenten- und Formeinschränkungen finden Sie in "SpatialUnderstandingDll.cs" in den Strukturen "ShapeComponentConstraint" und "ShapeConstraint".</span><span class="sxs-lookup"><span data-stu-id="b7d6e-237">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="b7d6e-238">![Rechteckform befindet sich auf dieser Oberfläche](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b7d6e-238">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="b7d6e-239">*Rechteckform befindet sich auf dieser Oberfläche*</span><span class="sxs-lookup"><span data-stu-id="b7d6e-239">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="b7d6e-240">Objektplatzierungs-Solver</span><span class="sxs-lookup"><span data-stu-id="b7d6e-240">Object Placement Solver</span></span>

<span data-ttu-id="b7d6e-241">Der Objektplatzierungs-Solver kann verwendet werden, um ideale Positionen im physischen Raum zu identifizieren, an dem Ihre Objekte platzieren werden.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-241">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="b7d6e-242">Der Solver findet die am besten passende Position, wenn die Objektregeln und Einschränkungen gegeben sind.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-242">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="b7d6e-243">Darüber hinaus bleiben Objektabfragen bestehen, bis das Objekt mit "Solver_RemoveObject"- oder "Solver_RemoveAllObjects"-Aufrufen entfernt wird, wodurch eine eingeschränkte Platzierung mit mehreren Objekten ermöglicht wird.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-243">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="b7d6e-244">Objektplatzierungsabfragen bestehen aus drei Teilen: Platzierungstyp mit Parametern, einer Liste von Regeln und einer Liste von Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-244">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="b7d6e-245">Verwenden Sie die folgende API, um eine Abfrage auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-245">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="b7d6e-246">Diese Funktion verwendet einen Objektnamen, eine Platzierungsdefinition und eine Liste von Regeln und Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-246">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="b7d6e-247">Die C#-Wrapper stellen Konstruktionshilfefunktionen zur Verfügung, um die Regel- und Einschränkungskonstruktion zu einfach zu machen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-247">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="b7d6e-248">Die Platzierungsdefinition enthält den Abfragetyp, d. &a. eine der folgenden Typen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-248">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
{
    Place_OnFloor,
    Place_OnWall,
    Place_OnCeiling,
    Place_OnShape,
    Place_OnEdge,
    Place_OnFloorAndCeiling,
    Place_RandomInAir,
    Place_InMidAir,
    Place_UnderFurnitureEdge,
};
```

<span data-ttu-id="b7d6e-249">Jeder Der Platzierungstypen verfügt über einen Satz von Parametern, die für den Typ eindeutig sind.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-249">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="b7d6e-250">Die "ObjectPlacementDefinition"-Struktur enthält eine Reihe statischer Hilfsfunktionen zum Erstellen dieser Definitionen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-250">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="b7d6e-251">Sie können beispielsweise die folgende Funktion verwenden, um einen Ort zu finden, an dem sie ein Objekt auf dem Boden platzieren können.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-251">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="b7d6e-252">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) Zusätzlich zum Platzierungstyp können Sie eine Reihe von Regeln und Einschränkungen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-252">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="b7d6e-253">Regeln können nicht verletzt werden.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-253">Rules cannot be violated.</span></span> <span data-ttu-id="b7d6e-254">Mögliche Platzierungsstandorte, die den Typ und die Regeln erfüllen, werden dann für den Satz von Einschränkungen optimiert, um den optimalen Platzierungsort auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-254">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="b7d6e-255">Jede der Regeln und Einschränkungen kann von den bereitgestellten statischen Erstellungsfunktionen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-255">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="b7d6e-256">Eine Beispielfunktion für die Regel- und Einschränkungskonstruktion finden Sie unten.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-256">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="b7d6e-257">Die folgende Objektplatzierungsabfrage sucht nach einem Ort, an dem sie einen halb meter langen Würfel am Rand einer Oberfläche platzieren kann, weg von anderen zuvor platzierenden Objekten und in der Nähe der Mitte des Raumes.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-257">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules =
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints =
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f),
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="b7d6e-258">Bei Erfolg wird eine ObjectPlacementResult-Struktur zurückgegeben, die position, dimensions und orientation enthält.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-258">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions, and orientation is returned.</span></span> <span data-ttu-id="b7d6e-259">Darüber hinaus wird die Platzierung der internen Liste der platzierten Objekte der DLL hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-259">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="b7d6e-260">Bei nachfolgenden Platzierungsabfragen wird dieses Objekt berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-260">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="b7d6e-261">Die Datei "LevelSolver.cs" im Unity-Beispiel enthält weitere Beispielabfragen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-261">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="b7d6e-262">![Ergebnisse der Objektplatzierung](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b7d6e-262">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="b7d6e-263">*Abbildung 3: Die blauen Felder zeigen, wie sich das Ergebnis aus Abfragen vom Dreierort im Boden mit Weg von Kamerapositionsregeln ergeben kann.*</span><span class="sxs-lookup"><span data-stu-id="b7d6e-263">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="b7d6e-264">Lösen Sie beim Lösen der Platzierungsposition mehrerer Objekte, die für ein Ebenen- oder Anwendungsszenario erforderlich sind, zuerst die Lösung für Bzw. große Objekte, um die Wahrscheinlichkeit zu maximieren, dass ein Raum gefunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-264">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="b7d6e-265">Die Platzierungs reihenfolge ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-265">Placement order is important.</span></span> <span data-ttu-id="b7d6e-266">Wenn Objektplatzierungen nicht gefunden werden können, versuchen Sie weniger eingeschränkte Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-266">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="b7d6e-267">Eine Reihe von Fallbackkonfigurationen ist entscheidend für die Unterstützung von Funktionen für viele Raumkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-267">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="b7d6e-268">Raumscanprozess</span><span class="sxs-lookup"><span data-stu-id="b7d6e-268">Room Scanning Process</span></span>

<span data-ttu-id="b7d6e-269">Die von HoloLens bereitgestellte Räumliche Zuordnungslösung ist so konzipiert, dass sie generisch genug ist, um die Anforderungen der gesamten Gamut der Problemräume zu erfüllen, aber das Spatial Understanding-Modul wurde erstellt, um die Anforderungen von zwei bestimmten Spielen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-269">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="b7d6e-270">Die Lösung ist um einen bestimmten Prozess und eine Reihe von Annahmen strukturiert, die unten zusammengefasst sind.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-270">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="b7d6e-271">Benutzergesteuertes "Malen" des Playspace: Während der Überprüfungsphase bewegt sich der Benutzer und sieht sich die Spielgeschwindigkeit an, um die Bereiche effektiv zu malen, die eingeschlossen werden sollten.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-271">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas, which should be included.</span></span> <span data-ttu-id="b7d6e-272">Das generierte Gitternetz ist wichtig, um während dieser Phase Benutzerfeedback zu geben.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-272">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="b7d6e-273">Einrichtung von Heim- oder Bürogebäuden: Die Abfragefunktionen sind auf flache Oberflächen und Wände in rechten Winkeln ausgelegt.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-273">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="b7d6e-274">Dies ist eine weiche Einschränkung.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-274">This is a soft limitation.</span></span> <span data-ttu-id="b7d6e-275">Während der Überprüfungsphase wird jedoch eine Primäre Achsenanalyse abgeschlossen, um das Gitternetz-Mosaik entlang der Haupt- und Nebenachse zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-275">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="b7d6e-276">Die enthaltene Datei SpatialUnderstanding.cs verwaltet den Überprüfungsphasenprozess.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-276">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="b7d6e-277">Sie ruft die folgenden Funktionen auf.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-277">It calls the following functions.</span></span>

```txt
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan –
    Called each frame to update the scanning process. The camera position and
    orientation is passed in and is used for the playspace painting process,
    described above.

GeneratePlayspace_RequestFinish –
    Called to finalize the playspace. This will use the areas “painted” during
    the scan phase to define and lock the playspace. The application can query
    statistics during the scanning phase as well as query the custom mesh for
    providing user feedback.

Import_UnderstandingMesh –
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by
    the module and placed on the understanding prefab will periodically query the
    custom mesh generated by the process. In addition, this is done once more
    after scanning has been finalized.
```

<span data-ttu-id="b7d6e-278">Der Scanfluss, der vom Verhalten "SpatialUnderstanding" gesteuert wird, ruft InitScan und dann UpdateScan für jeden Frame auf.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-278">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="b7d6e-279">Wenn die Statistikabfrage eine angemessene Abdeckung meldet, kann der Benutzer requestFinish aufrufen, um das Ende der Überprüfungsphase anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-279">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="b7d6e-280">UpdateScan wird weiterhin aufgerufen, bis sein Rückgabewert angibt, dass die DLL die Verarbeitung abgeschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-280">UpdateScan continues to be called until its return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="b7d6e-281">Grundlegendes zu Mesh</span><span class="sxs-lookup"><span data-stu-id="b7d6e-281">Understanding Mesh</span></span>

<span data-ttu-id="b7d6e-282">Die grundlegende DLL speichert den Playspace intern als Raster mit Voxelcubes mit einer Größe von 8 cm.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-282">The understanding dll internally stores the playspace as a grid of 8 cm sized voxel cubes.</span></span> <span data-ttu-id="b7d6e-283">Während des ersten Teils der Überprüfung wird eine Primäre Komponentenanalyse abgeschlossen, um die Achsen des Raums zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-283">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="b7d6e-284">Intern speichert es seinen Voxelraum, der an diesen Achsen ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-284">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="b7d6e-285">Ein Gitternetz wird ungefähr jede Sekunde generiert, indem die Isosurface aus dem Voxelvolumen extrahiert wird.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-285">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

<span data-ttu-id="b7d6e-286">![Generiertes Gitternetz, das aus dem Voxelvolumen erzeugt wird](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="b7d6e-286">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="b7d6e-287">*Generiertes Gitternetz, das aus dem Voxelvolumen erzeugt wird*</span><span class="sxs-lookup"><span data-stu-id="b7d6e-287">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="b7d6e-288">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="b7d6e-288">Troubleshooting</span></span>

* <span data-ttu-id="b7d6e-289">Stellen Sie sicher, dass Sie die [SpatialPerception-Funktion festgelegt](#setting-the-spatialperception-capability) haben.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-289">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="b7d6e-290">Wenn die Nachverfolgung verloren geht, entfernt das nächste OnSurfaceChanged-Ereignis alle Gitternetze.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-290">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="b7d6e-291">Spatial Mapping im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="b7d6e-291">Spatial Mapping in Mixed Reality Toolkit</span></span>

<span data-ttu-id="b7d6e-292">Weitere Informationen zur Verwendung von Spatial Mapping mit Mixed Reality Toolkit finden Sie im Abschnitt räumliche Wahrnehmung [der](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-292">For more information on using Spatial Mapping with Mixed Reality Toolkit, see the [spatial awareness section](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) of the MRTK docs.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b7d6e-293">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="b7d6e-293">Next Development Checkpoint</span></span>

<span data-ttu-id="b7d6e-294">Wenn Sie den weg zur Unity-Entwicklung folgen, den wir festgelegt haben, sind Sie gerade dabei, die MRTK-Kernbausteine zu erkunden.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-294">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="b7d6e-295">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="b7d6e-295">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7d6e-296">Text</span><span class="sxs-lookup"><span data-stu-id="b7d6e-296">Text</span></span>](text-in-unity.md)

<span data-ttu-id="b7d6e-297">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="b7d6e-297">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7d6e-298">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="b7d6e-298">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="b7d6e-299">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="b7d6e-299">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7d6e-300">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b7d6e-300">See also</span></span>

* [<span data-ttu-id="b7d6e-301">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="b7d6e-301">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="b7d6e-302">Koordinatensysteme in Unity</span><span class="sxs-lookup"><span data-stu-id="b7d6e-302">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="b7d6e-303"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="b7d6e-303"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="b7d6e-304"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="b7d6e-304"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="b7d6e-305"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="b7d6e-305"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="b7d6e-306"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="b7d6e-306"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
