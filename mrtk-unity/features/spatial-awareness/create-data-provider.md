---
title: Erstellen eines räumlichen Bewusstseins Datenanbieter
description: beschreibt, wie benutzerdefinierte Datenanbieter in MRTK erstellt werden.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 04a0cdbd18f666b6a99c120eb28966234cc8c92d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145152"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a><span data-ttu-id="5a8c9-104">Erstellen eines Systemdatenanbieters für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="5a8c9-104">Creating a spatial awareness system data provider</span></span>

<span data-ttu-id="5a8c9-105">Das Spatial Awareness-System ist ein erweiterbares System zum Bereitstellen von Daten zu realen Umgebungen für Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-105">The Spatial Awareness system is an extensible system for providing applications with data about real world environments.</span></span> <span data-ttu-id="5a8c9-106">Um Unterstützung für eine neue Hardwareplattform oder eine neue Form von Spatial Awareness-Daten hinzuzufügen, ist möglicherweise ein benutzerdefinierter Datenanbieter erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-106">To add support for a new hardware platform or a new form of Spatial Awareness data, a custom data provider may be required.</span></span>

<span data-ttu-id="5a8c9-107">In diesem Artikel wird beschrieben, wie [Sie](../../architecture/systems-extensions-providers.md)benutzerdefinierte Datenanbieter ( auch räumliche Beobachter genannt) für das Spatial Awareness-System erstellen.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-107">This article describes how to create [custom data providers](../../architecture/systems-extensions-providers.md), also called Spatial Observers, for the Spatial Awareness system.</span></span> <span data-ttu-id="5a8c9-108">Der hier gezeigte Beispielcode ist aus der -Klassenimplementierung, die zum Laden von [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) [3D-Gitternetzdaten im Editor nützlich ist.](spatial-object-mesh-observer.md)</span><span class="sxs-lookup"><span data-stu-id="5a8c9-108">The example code shown here is from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class implementation which is [useful for loading 3D mesh data in-editor](spatial-object-mesh-observer.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5a8c9-109">Den vollständigen Quellcode, der in diesem Beispiel verwendet wird, finden Sie im `Assets/MRTK/Providers/ObjectMeshObserver` Ordner .</span><span class="sxs-lookup"><span data-stu-id="5a8c9-109">The complete source code used in this example can be found in the `Assets/MRTK/Providers/ObjectMeshObserver` folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="5a8c9-110">Namespace- und Ordnerstruktur</span><span class="sxs-lookup"><span data-stu-id="5a8c9-110">Namespace and folder structure</span></span>

<span data-ttu-id="5a8c9-111">Datenanbieter können auf zwei Arten verteilt werden:</span><span class="sxs-lookup"><span data-stu-id="5a8c9-111">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="5a8c9-112">Drittanbieter-Add-Ons</span><span class="sxs-lookup"><span data-stu-id="5a8c9-112">Third party add-ons</span></span>
1. <span data-ttu-id="5a8c9-113">Teil des Microsoft Mixed Reality Toolkits</span><span class="sxs-lookup"><span data-stu-id="5a8c9-113">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="5a8c9-114">Der Genehmigungsprozess für die Übermittlung neuer Datenanbieter an das MRTK variiert von Fall zu Fall und wird zum Zeitpunkt des ersten Vorschlags kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-114">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="5a8c9-115">Vorschläge können übermittelt werden, indem ein neues Problem mit dem [ *Funktionsanforderungstyp* erstellt wird.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)</span><span class="sxs-lookup"><span data-stu-id="5a8c9-115">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-on"></a><span data-ttu-id="5a8c9-116">Drittanbieter-Add-On</span><span class="sxs-lookup"><span data-stu-id="5a8c9-116">Third party add-on</span></span>

<span data-ttu-id="5a8c9-117">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="5a8c9-117">**Namespace**</span></span>

<span data-ttu-id="5a8c9-118">Datenanbieter müssen über einen Namespace verfügen, um potenzielle Namenskollisionen zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-118">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="5a8c9-119">Es wird empfohlen, dass der -Namespace die folgenden Komponenten enthält.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-119">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="5a8c9-120">Unternehmensname, der das Add-On erzeugt</span><span class="sxs-lookup"><span data-stu-id="5a8c9-120">Company name producing the add-on</span></span>
- <span data-ttu-id="5a8c9-121">Featurebereich</span><span class="sxs-lookup"><span data-stu-id="5a8c9-121">Feature area</span></span>

<span data-ttu-id="5a8c9-122">Ein Vom Unternehmen Contoso erstellter und ausgelieferter Spatial Awareness-Datenanbieter kann beispielsweise *"Contoso.MixedReality.Toolkit.SpatialAwareness" sein.*</span><span class="sxs-lookup"><span data-stu-id="5a8c9-122">For example, a Spatial Awareness data provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.SpatialAwareness"*.</span></span>

<span data-ttu-id="5a8c9-123">**Ordnerstruktur**</span><span class="sxs-lookup"><span data-stu-id="5a8c9-123">**Folder structure**</span></span>

<span data-ttu-id="5a8c9-124">Es wird empfohlen, den Quellcode für Datenanbieter in einer Ordnerhierarchie zu erstellen, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-124">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Beispiel für die Paketordnerstruktur](../images/spatial-awareness/ExampleProviderFolderStructure.png)

<span data-ttu-id="5a8c9-126">Wenn der Ordner *ContosoSpatialAwareness* die Implementierung des Datenanbieters enthält, enthält der *Ordner Editor* den Inspektor (und jeden anderen codespezifischen Code des Unity-Editors), und der Ordner *Profile* enthält ein oder mehrere vorgefertigte Profile, die skriptfähig sind.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-126">Where the *ContosoSpatialAwareness* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="5a8c9-127">MRTK-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="5a8c9-127">MRTK submission</span></span>

<span data-ttu-id="5a8c9-128">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="5a8c9-128">**Namespace**</span></span>

<span data-ttu-id="5a8c9-129">Wenn ein Systemdatenanbieter für räumliche Wahrnehmung an das [Mixed Reality Toolkit-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity)übermittelt wird, **muss** der Namespace mit Microsoft.MixedReality.Toolkit (z.B. *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver)* beginnen.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-129">If a spatial awareness system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span></span>

 <span data-ttu-id="5a8c9-130">und der Code sollte sich in einem Ordner unter MRTK/Providers (z.B. *MRTK/Providers/ObjectMeshObserver)* befinden.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-130">and the code should be located in a folder beneath MRTK/Providers (ex: *MRTK/Providers/ObjectMeshObserver*).</span></span>

<span data-ttu-id="5a8c9-131">**Ordnerstruktur**</span><span class="sxs-lookup"><span data-stu-id="5a8c9-131">**Folder structure**</span></span>

<span data-ttu-id="5a8c9-132">Der gesamte Code sollte sich in einem Ordner unter MRTK/Providers (z. B. MRTK/Providers/ObjectMeshObserver) befinden.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-132">All code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/ObjectMeshObserver).</span></span>

## <a name="define-the-spatial-data-object"></a><span data-ttu-id="5a8c9-133">Definieren des räumlichen Datenobjekts</span><span class="sxs-lookup"><span data-stu-id="5a8c9-133">Define the spatial data object</span></span>

<span data-ttu-id="5a8c9-134">Der erste Schritt beim Erstellen eines Datenanbieters für räumliche Wahrnehmung ist die Bestimmung des Datentyps (z. B. Gitternetze oder Ebenen), die für Anwendungen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-134">The first step in creating a Spatial Awareness data provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="5a8c9-135">Alle räumlichen Datenobjekte müssen die [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) -Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-135">All spatial data objects must implement the [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.</span></span>

<span data-ttu-id="5a8c9-136">Die Mixed Reality Toolkit-Grundlage stellt die folgenden räumlichen Objekte bereit, die in neuen Datenanbietern verwendet oder erweitert werden können.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-136">The Mixed Reality Toolkit foundation provides the following spatial objects that can be used or extended in new data providers.</span></span>

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a><span data-ttu-id="5a8c9-137">Implementieren des Datenanbieters</span><span class="sxs-lookup"><span data-stu-id="5a8c9-137">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="5a8c9-138">Angeben der Schnittstellen- und/oder Basisklassenvererbung</span><span class="sxs-lookup"><span data-stu-id="5a8c9-138">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="5a8c9-139">Alle Spatial Awareness-Datenanbieter müssen die [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) -Schnittstelle implementieren, die die minimal erforderliche Funktionalität des Spatial Awareness-Systems angibt.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-139">All Spatial Awareness data providers must implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, which specifies the minimum functionality required by the Spatial Awareness system.</span></span> <span data-ttu-id="5a8c9-140">Die MRTK-Grundlage enthält die [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) -Klasse, die eine Standardimplementierung dieser erforderlichen Funktionalität bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-140">The MRTK foundation includes the [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class which provides a default implementation of this required functionality.</span></span>

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> <span data-ttu-id="5a8c9-141">Die [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) -Schnittstelle wird von der [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) -Klasse verwendet, um anzugeben, dass sie Unterstützung für die SpatialAwarenessMesh-Funktion bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-141">The [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface is used by the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class to indicate that it provides support for the SpatialAwarenessMesh capability.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="5a8c9-142">Anwenden des MixedRealityDataProvider-Attributs</span><span class="sxs-lookup"><span data-stu-id="5a8c9-142">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="5a8c9-143">Ein wichtiger Schritt beim Erstellen eines Datenanbieters für räumliche Wahrnehmung ist das Anwenden des [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) -Attributs auf die -Klasse.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-143">A key step in creating a Spatial Awareness data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="5a8c9-144">Mit diesem Schritt können Sie das Standardprofil und die Plattformen für den Datenanbieter festlegen, wenn sie im Profil räumliche Wahrnehmung sowie name, folder path usw. ausgewählt sind.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-144">This step enables setting the default profile and platform(s) for the data provider, when selected in the Spatial Awareness profile as well as Name, folder path, and more.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="5a8c9-145">Implementieren der IMixedRealityDataProvider-Methoden</span><span class="sxs-lookup"><span data-stu-id="5a8c9-145">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="5a8c9-146">Nachdem die -Klasse definiert wurde, besteht der nächste Schritt darin, die Implementierung der [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) -Schnittstelle bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-146">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="5a8c9-147">Die [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) -Klasse stellt über die [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) -Klasse nur leere Implementierungen für [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) -Methoden bereit.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-147">The [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides only an empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="5a8c9-148">Die Details dieser Methoden sind im Allgemeinen datenanbieterspezifisch.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-148">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="5a8c9-149">Folgende Methoden sollten vom Datenanbieter implementiert werden:</span><span class="sxs-lookup"><span data-stu-id="5a8c9-149">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="5a8c9-150">Implementieren der Datenanbieterlogik</span><span class="sxs-lookup"><span data-stu-id="5a8c9-150">Implement the data provider logic</span></span>

<span data-ttu-id="5a8c9-151">Der nächste Schritt besteht darin, die Logik des Datenanbieters hinzuzufügen, indem die spezifische Datenanbieterschnittstelle implementiert wird, z. [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) B. .</span><span class="sxs-lookup"><span data-stu-id="5a8c9-151">The next step is to add the logic of the data provider by implementing the specific data provider interface, for example [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver).</span></span> <span data-ttu-id="5a8c9-152">Dieser Teil des Datenanbieters ist in der Regel plattformspezifisch.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-152">This portion of the data provider will typically be platform specific.</span></span>

### <a name="observation-change-notifications"></a><span data-ttu-id="5a8c9-153">Benachrichtigungen zu Beobachtungsänderungen</span><span class="sxs-lookup"><span data-stu-id="5a8c9-153">Observation change notifications</span></span>

<span data-ttu-id="5a8c9-154">Damit Anwendungen auf Änderungen im Verständnis der Umgebung des Geräts reagieren können, löst der Datenanbieter Benachrichtigungsereignisse aus, wie in der [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) -Schnittstelle definiert.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-154">To allow applications to respond to changes in the device's understanding of the environment, the data provider raises notification events as defined in the [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span></span>

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 <span data-ttu-id="5a8c9-155">Der folgende Code aus den Beispielen veranschaulicht das [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) Auslösen und Ereignis, wenn Meshdaten hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-155">The following code from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) examples demonstrates raising and event when mesh data is added.</span></span>

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> <span data-ttu-id="5a8c9-156">Die [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) -Klasse gibt keine `OnObservationUpdated` Ereignisse aus, da das 3D-Modell nur einmal geladen wird.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-156">The [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class does not raise `OnObservationUpdated` events since the 3D model is only loaded once.</span></span> <span data-ttu-id="5a8c9-157">Die Implementierung in der -Klasse stellt ein Beispiel für das [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) Auslösen eines `OnObservationUpdated` Ereignisses für ein beobachtetes Gitternetz bereit.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-157">The implementation in the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class provides an example of raising an `OnObservationUpdated` event for an observed mesh.</span></span>

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="5a8c9-158">Hinzufügen der Unity Profiler-Instrumentierung</span><span class="sxs-lookup"><span data-stu-id="5a8c9-158">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="5a8c9-159">Leistung ist in Mixed Reality-Anwendungen von entscheidender Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-159">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="5a8c9-160">Jede Komponente erhöht den Mehraufwand, den Anwendungen berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-160">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="5a8c9-161">Zu diesem Zweck ist es wichtig, dass alle Anbieter räumlicher Wahrnehmungsdaten die Unity Profiler-Instrumentierung in inneren Schleifen und häufig verwendeten Codepfaden enthalten.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-161">To this end, it is important that all spatial awareness data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="5a8c9-162">Es wird empfohlen, das Muster zu implementieren, das vom MRTK beim Instrumentieren benutzerdefinierter Anbieter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-162">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="5a8c9-163">Der Name, der zum Identifizieren des Profilermarkers verwendet wird, ist willkürlich.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-163">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="5a8c9-164">Das MRTK verwendet das folgende Muster.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-164">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="5a8c9-165">"[product] className.methodName – optionaler Hinweis"</span><span class="sxs-lookup"><span data-stu-id="5a8c9-165">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="5a8c9-166">Es wird empfohlen, dass benutzerdefinierte Datenanbieter ein ähnliches Muster befolgen, um die Identifizierung bestimmter Komponenten und Methoden bei der Analyse von Ablaufverfolgungen zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-166">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="5a8c9-167">Erstellen des Profils und Inspektors</span><span class="sxs-lookup"><span data-stu-id="5a8c9-167">Create the profile and inspector</span></span>

<span data-ttu-id="5a8c9-168">Im Mixed Reality Toolkit werden Datenanbieter mithilfe der Profile [konfiguriert.](../profiles/profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5a8c9-168">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="5a8c9-169">Definieren des Profils</span><span class="sxs-lookup"><span data-stu-id="5a8c9-169">Define the profile</span></span>

<span data-ttu-id="5a8c9-170">Der Profilinhalt sollte die zugänglichen Eigenschaften des Datenanbieters spiegeln (z. B. Updateintervall).</span><span class="sxs-lookup"><span data-stu-id="5a8c9-170">Profile contents should mirror the accessible properties of the data provider (ex: update interval).</span></span> <span data-ttu-id="5a8c9-171">Alle vom Benutzer konfigurierbaren Eigenschaften, die in jeder Schnittstelle definiert sind, sollten im Profil enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-171">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

<span data-ttu-id="5a8c9-172">Basisklassen werden empfohlen, wenn ein neuer Datenanbieter einen vorhandenen Anbieter erweitert.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-172">Base classes are encouraged if a new data provider extends an existing provider.</span></span> <span data-ttu-id="5a8c9-173">Beispielsweise erweitert das , um Kunden die Bereitstellung eines [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) 3D-Modells zu ermöglichen, das als Umgebungsdaten verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-173">For example, the [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) extends the [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) to enable customers to provide a 3D model to be used as the environment data.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

<span data-ttu-id="5a8c9-174">Das -Attribut kann auf die Profilklasse angewendet werden, damit Kunden über das Menü Create Assets Mixed Reality Toolkit Profiles (Erstellen von Ressourcen `CreateAssetMenu`   >    >  **Mixed Reality Toolkitprofile)** eine Profilinstanz erstellen  >   können.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-174">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="5a8c9-175">Implementieren des Inspektors</span><span class="sxs-lookup"><span data-stu-id="5a8c9-175">Implement the inspector</span></span>

<span data-ttu-id="5a8c9-176">Profilinspektoren sind die Benutzeroberfläche zum Konfigurieren und Anzeigen von Profilinhalten.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-176">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="5a8c9-177">Jeder Profilinspektor sollte die -Klasse [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) erweitern.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-177">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="5a8c9-178">Das `CustomEditor` -Attribut informiert Unity über den Typ des Assets, auf das der Inspektor angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-178">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="5a8c9-179">Erstellen von Assemblydefinitionen</span><span class="sxs-lookup"><span data-stu-id="5a8c9-179">Create assembly definition(s)</span></span>

<span data-ttu-id="5a8c9-180">Das Mixed Reality Toolkit verwendet Assemblydefinitionsdateien[(ASMDEF-Dateien),](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)um Abhängigkeiten zwischen Komponenten anzugeben und Unity bei der Reduzierung der Kompilierungszeit zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-180">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="5a8c9-181">Es wird empfohlen, Assemblydefinitionsdateien für alle Datenanbieter und deren Editor-Komponenten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-181">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="5a8c9-182">Bei Verwendung [der Ordnerstruktur](#namespace-and-folder-structure) im früheren Beispiel gibt es zwei ASMDEF-Dateien für den Datenanbieter ContosoSpatialAwareness.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-182">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoSpatialAwareness data provider.</span></span>

<span data-ttu-id="5a8c9-183">Die erste Assemblydefinition ist für den Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-183">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="5a8c9-184">In diesem Beispiel heißt sie ContosoSpatialAwareness und befindet sich im Ordner *ContosoSpatialAwareness des Beispiels.*</span><span class="sxs-lookup"><span data-stu-id="5a8c9-184">For this example, it will be called ContosoSpatialAwareness and will be located in the example's *ContosoSpatialAwareness* folder.</span></span> <span data-ttu-id="5a8c9-185">Diese Assemblydefinition muss eine Abhängigkeit von Microsoft.MixedReality.Toolkit und allen anderen Assemblys angeben, von denen sie abhängt.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-185">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="5a8c9-186">Die ContosoInputEditor-Assemblydefinition gibt den Profilinspektor und jeden editorspezifischen Code an.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-186">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="5a8c9-187">Diese Datei muss sich im Stammordner des Editorcodes befinden.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-187">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="5a8c9-188">In diesem Beispiel befindet sich die Datei im Ordner *ContosoSpatialAwareness\Editor.*</span><span class="sxs-lookup"><span data-stu-id="5a8c9-188">In this example, the file will be located in the *ContosoSpatialAwareness\Editor* folder.</span></span> <span data-ttu-id="5a8c9-189">Diese Assemblydefinition enthält einen Verweis auf die ContosoSpatialAwareness-Assembly sowie:</span><span class="sxs-lookup"><span data-stu-id="5a8c9-189">This assembly definition will contain a reference to the ContosoSpatialAwareness assembly as well as:</span></span>

- <span data-ttu-id="5a8c9-190">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="5a8c9-190">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="5a8c9-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="5a8c9-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="5a8c9-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="5a8c9-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="5a8c9-193">Registrieren des Datenanbieters</span><span class="sxs-lookup"><span data-stu-id="5a8c9-193">Register the data provider</span></span>

<span data-ttu-id="5a8c9-194">Nach der Erstellung kann der Datenanbieter beim Spatial Awareness-System registriert werden, das in der Anwendung verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-194">Once created, the data provider can be registered with the Spatial Awareness system to be used in the application.</span></span>

![Auswählen des Raumobjektgittermodell-Beobachters](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="5a8c9-196">Verpacken und Verteilen</span><span class="sxs-lookup"><span data-stu-id="5a8c9-196">Packaging and distribution</span></span>

<span data-ttu-id="5a8c9-197">Datenanbieter, die als Drittanbieterkomponenten verteilt werden, verfügen über die spezifischen Details der Paketierung und Verteilung, die dem Entwickler überlassen werden.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-197">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="5a8c9-198">Wahrscheinlich ist die gängigste Lösung die Generierung eines UNITY-Pakets und die Verteilung über den Unity Asset Store.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-198">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="5a8c9-199">Wenn ein Datenanbieter als Teil des Microsoft Mixed Reality Toolkit-Pakets übermittelt und akzeptiert wird, packt und verteilt das Microsoft MRTK-Team ihn im Rahmen der MRTK-Angebote.</span><span class="sxs-lookup"><span data-stu-id="5a8c9-199">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a8c9-200">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5a8c9-200">See also</span></span>

- [<span data-ttu-id="5a8c9-201">System für die räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="5a8c9-201">Spatial awareness system</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="5a8c9-202">`IMixedRealitySpatialAwarenessObject` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5a8c9-202">`IMixedRealitySpatialAwarenessObject` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [<span data-ttu-id="5a8c9-203">`BaseSpatialAwarenessObject`-Klasse</span><span class="sxs-lookup"><span data-stu-id="5a8c9-203">`BaseSpatialAwarenessObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [<span data-ttu-id="5a8c9-204">`SpatialAwarenessMeshObject`-Klasse</span><span class="sxs-lookup"><span data-stu-id="5a8c9-204">`SpatialAwarenessMeshObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [<span data-ttu-id="5a8c9-205">`SpatialAwarenessPlanarObject`-Klasse</span><span class="sxs-lookup"><span data-stu-id="5a8c9-205">`SpatialAwarenessPlanarObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [<span data-ttu-id="5a8c9-206">`IMixedRealitySpatialAwarenessObserver` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5a8c9-206">`IMixedRealitySpatialAwarenessObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [<span data-ttu-id="5a8c9-207">`BaseSpatialObserver`-Klasse</span><span class="sxs-lookup"><span data-stu-id="5a8c9-207">`BaseSpatialObserver` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [<span data-ttu-id="5a8c9-208">`IMixedRealitySpatialAwarenessMeshObserver` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5a8c9-208">`IMixedRealitySpatialAwarenessMeshObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [<span data-ttu-id="5a8c9-209">`IMixedRealityDataProvider` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5a8c9-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="5a8c9-210">`IMixedRealityCapabilityCheck` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5a8c9-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
