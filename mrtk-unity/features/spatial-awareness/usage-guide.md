---
title: UsingGuide
description: beschreibt die wichtigsten Mechanismen und APIs zum programmgesteuerten Konfigurieren des Systems für räumliche Wahrnehmung.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 3a4b6ce17b87dba6155a9e020e41c800fd8ab86bc1b507e77e680fe9ec9a6687
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204122"
---
# <a name="configuring-mesh-observers-via-code"></a>Konfigurieren von Mesh-Beobachtern über Code

In diesem Artikel werden einige der wichtigsten Mechanismen und APIs zum programmgesteuerten Konfigurieren des [Spatial Awareness-Systems](spatial-awareness-getting-started.md) und der zugehörigen *Mesh Observer-Datenanbieter* erläutert.

## <a name="accessing-mesh-observers"></a>Zugreifen auf Mesh-Beobachter

Mesh Observer-Klassen, die die -Schnittstelle implementieren, [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) stellen plattformspezifische Gitternetzdaten für das Spatial Awareness-System bereit. Mehrere Beobachter können im Profil räumliche Wahrnehmung konfiguriert werden.

Der Zugriff auf die Datenanbieter des Spatial Awareness-Systems ist größtenteils identisch mit jedem anderen Mixed Reality Toolkit-Dienst. Der Dienst für räumliche Wahrnehmung muss in die Schnittstelle für den Zugriff über die APIs umgeformt werden, die dann verwendet [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) `GetDataProvider<T>` werden können, um zur Laufzeit direkt auf die Mesh Observer-Objekte zuzugreifen.

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

Das `CoreServices.GetSpatialAwarenessSystemDataProvider<T>()` Hilfsmuster vereinfacht dieses Zugriffsmuster, wie unten gezeigt.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a>Starten und Beenden der Gitternetzüberwachung

Eine der häufigsten Aufgaben beim Umgang mit dem Spatial Awareness-System besteht darin, das Feature zur Laufzeit dynamisch zu deaktivieren bzw. zu aktivieren. Dies erfolgt pro Beobachter über die [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) APIs und [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) .

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

Diese Codefunktionalität kann auch über den direkten Zugriff über das Spatial Awareness-System vereinfacht werden.

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a>Starten und Beenden der gesamten Gitternetzüberwachung

Es ist im Allgemeinen praktisch, alle Gitternetzüberwachungen in der Anwendung zu starten/zu beenden. Dies kann über die hilfreichen Spatial Awareness-System-APIs und erreicht [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) werden.

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a>Aufzählen und Zugreifen auf die Gitternetze

Der Zugriff auf die Gitternetze kann pro Observer erfolgen und dann über die API durch die Gitternetze aufzählen, die diesem Mesh-Beobachter bekannt [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) sind.

Wenn sie im Editor ausgeführt wird, können Sie verwenden, [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) um das Objekt in einer `Mesh` Medienobjektdatei zu speichern.

Wenn sie auf einem Gerät ausgeführt wird, stehen viele Community- und Store-Plug-Ins zur Verfügung, um die `MeshFilter` Daten in einen Modelldateityp zu serialisieren([OBJ-Beispiel](http://wiki.unity3d.com/index.php/ObjExporter)).

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Loop through all known Meshes
foreach (SpatialAwarenessMeshObject meshObject in observer.Meshes.Values)
{
    Mesh mesh = meshObject.Filter.mesh;
    // Do something with the Mesh object
}
```

## <a name="showing-and-hiding-the-spatial-mesh"></a>Anzeigen und Ausblenden des räumlichen Gitters

Es ist möglich, Gitternetze programmgesteuert mithilfe des folgenden Beispielcodes auszublenden/anzuzeigen:

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a>Registrieren für Mesh-Beobachtungsereignisse

Komponenten können implementieren `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` und sich dann beim Spatial Awareness-System registrieren, um Mesh-Beobachtungsereignisse zu empfangen.

Das `DemoSpatialMeshHandler` Skript (Assets/MRTK/Examples/Demos/SpatialAwareness/Scripts) ist ein nützliches Beispiel und Ausgangspunkt für das Lauschen auf Mesh Observer-Ereignisse.

Dies ist ein vereinfachtes Beispiel des *DemoSpatialMeshHandler-Skripts* und des Mesh Observation-Ereignisses, das lauscht.

```c#
// Simplify type
using SpatialAwarenessHandler = IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>;

public class MyMeshObservationExample : MonoBehaviour, SpatialAwarenessHandler
{
    private void OnEnable()
    {
        // Register component to listen for Mesh Observation events, typically done in OnEnable()
        CoreServices.SpatialAwarenessSystem.RegisterHandler<SpatialAwarenessHandler>(this);
    }

    private void OnDisable()
    {
        // Unregister component from Mesh Observation events, typically done in OnDisable()
        CoreServices.SpatialAwarenessSystem.UnregisterHandler<SpatialAwarenessHandler>(this);
    }

    public virtual void OnObservationAdded(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationUpdated(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationRemoved(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }
}
```

## <a name="see-also"></a>Siehe auch

- [Erste Schritte für räumliche Wahrnehmung](spatial-awareness-getting-started.md)
- [Konfigurieren des Spatial Awareness Mesh-Beobachters](configuring-spatial-awareness-mesh-observer.md)
- [Dokumentation zur Spatial Awareness-API](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
