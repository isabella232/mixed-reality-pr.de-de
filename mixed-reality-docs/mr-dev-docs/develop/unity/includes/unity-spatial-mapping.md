---
ms.openlocfilehash: 271116683c94e051f61b78c0db3974ee843afdbd
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905708"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="spatial-awareness-system"></a>System für die räumliche Wahrnehmung

Informationen zum Einrichten verschiedener [](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) Raumgitternetzbeobachter finden Sie im MrTK unter Erste Schritte mit räumlichem Bewusstsein.

Informationen zu Beobachtern auf Dem Gerät finden Sie im Leitfaden [Konfigurieren von Gitternetzbeobachtern für](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/configuring-spatial-awareness-mesh-observer) Geräte.

Informationen zum Verstehen von Szenenbeobachtern finden Sie im [Beobachterhandbuch zu Szenenverständnis.](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding)

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="armeshmanager"></a>ARMeshManager

Die ARFoundation von Unity stellt eine ARMeshManager-Komponente für die integrierte Visualisierung räumlicher Gitternetze zur Verfügung. Weitere [Informationen zur Verwendung finden Sie](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/mesh-manager.html) in der Unity-Dokumentation.

## <a name="xrmeshsubsystem"></a>XRMeshSubsystem

Wenn Sie lieber direkt mit dem [XRMeshSubsystem](https://docs.unity3d.com/ScriptReference/XR.XRMeshSubsystem.html) von Unity arbeiten möchten, finden Sie weitere Informationen zur Verwendung in der [Unity-Dokumentation.](https://docs.unity3d.com/Manual/xrsdk-meshing.html)

## <a name="windows-xr-plugin"></a>Windows XR-Plug-In

Windows Das XR-Plug-In bietet einige zusätzliche Erweiterungsmethoden zum Konfigurieren des XRMeshSubsystems, z. B. das Festlegen einer Begrenzungskugel oder den Zugriff auf die zugrunde liegende Plattformgitternetzdarstellung. Alle diese anderen Erweiterungen finden Sie [in der Unity-Dokumentation.](https://docs.unity3d.com/Packages/com.unity.xr.windowsmr@5.3/api/UnityEngine.XR.WindowsMR.WindowsMRExtensions.html)

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Erste Schritte mit den integrierten Komponenten der räumlichen Zuordnung von Unity

Unity bietet zwei Komponenten zum einfachen Hinzufügen von räumlicher Zuordnung zu Ihrer App: **Spatial Mapping Renderer** und **Spatial Mapping Collider.**

### <a name="spatial-mapping-renderer"></a>Renderer für räumliche Zuordnung

Der Renderer für räumliche Zuordnung ermöglicht die Visualisierung des Gitters für räumliche Zuordnungen.

![Spatial Mapping Renderer in Unity](../images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Spatial Mapping Collider

Der Spatial Mapping Collider ermöglicht holografische Inhaltsinteraktion (oder Zeicheninteraktion, z. B. Physik) mit dem Gitternetz der räumlichen Zuordnung.

![Spatial Mapping Collider in Unity](../images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Verwenden der integrierten Räumlichen Zuordnungskomponenten

Sie können Ihrer App beide Komponenten hinzufügen, wenn Sie sowohl physische Oberflächen visualisieren als auch mit ihnen interagieren möchten.

So verwenden Sie diese beiden Komponenten in Ihrer Unity-App:

1. Wählen Sie ein GameObject in der Mitte des Bereichs aus, in dem Sie Gitternetze für räumliche Oberflächen erkennen möchten.
2. Fügen Sie im Inspektorfenster **komponente**  >  **XR**  >  **Spatial Mapping Collider oder** Spatial Mapping   **Renderer hinzu.**

Weitere Informationen zur Verwendung dieser Komponenten finden Sie auf der <a href="https://docs.unity3d.com/2018.4/Documentation/Manual/SpatialMappingComponents.html" target="_blank">Unity-Dokumentationswebsite.</a>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Über die integrierten Räumlichen Zuordnungskomponenten hinausgehen

Diese Komponenten machen es einfach, mit Drag & Drop mit der räumlichen Zuordnung zu beginnen. Wenn Sie weiter gehen möchten, gibt es zwei Hauptpfade, die Sie erkunden können:

* Informationen zur eigenen Gitternetzverarbeitung auf niedrigerer Ebene finden Sie im folgenden Abschnitt zur Skript-API für die räumliche Zuordnung auf niedriger Ebene.
* Informationen zur Gitternetzanalyse auf höherer Ebene finden Sie im abschnitt unten zur SpatialUnderstanding-Bibliothek in [MixedRealityToolkit.](https://github.com/microsoft/MixedRealityToolkit/tree/master/SpatialUnderstanding)

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Verwenden der Unity-API für die räumliche Zuordnung auf niedriger Ebene

Wenn Sie mehr Kontrolle benötigen, als die Komponenten Spatial Mapping Renderer und Spatial Mapping Collider bieten, verwenden Sie die low-level Spatial Mapping-APIs.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typen:** *SurfaceObserver,* *SurfaceChange,* *SurfaceData,* *SurfaceId*

Wir haben den vorgeschlagenen Ablauf für eine Anwendung beschrieben, die die APIs für die räumliche Zuordnung in den folgenden Abschnitten verwendet.

### <a name="set-up-the-surfaceobservers"></a>Einrichten der SurfaceObserver

Instanziieren Sie ein SurfaceObserver-Objekt für jeden anwendungsdefinierten Raumbereich, für den Sie Räumliche Zuordnungsdaten benötigen.

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

Geben Sie den Bereich des Speicherplatzes an, für den jedes SurfaceObserver-Objekt Daten bereitstellen soll, indem Sie SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox oder SetVolumeAsFrustum aufrufen. Sie können den Bereich des Raumes in Zukunft neu definieren, indem Sie eine dieser Methoden erneut aufrufen.

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Wenn Sie SurfaceObserver.Update() aufrufen, müssen Sie einen Handler für jede räumliche Oberfläche im Raumbereich des SurfaceObserver bereitstellen, für den das Raumzuordnungssystem über neue Informationen verfügt. Der Handler empfängt für eine räumliche Oberfläche:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>Behandeln von Oberflächenänderungen

Es gibt mehrere Hauptfälle, die behandelt werden müssen: hinzugefügt und aktualisiert, die denselben Codepfad verwenden und entfernt werden können.

* In den hinzugefügten und aktualisierten Fällen fügen wir das GameObject hinzu, das dieses Gitternetz darstellt, oder erhalten es aus dem Wörterbuch. Wir erstellen eine SurfaceData-Struktur mit den erforderlichen Komponenten, rufen dann RequestMeshDataAsync auf, um das GameObject mit den Gitterdaten zu füllen, und positionieren es dann in der Szene.
* Im entfernten Fall entfernen wir das GameObject, das dieses Gitternetz darstellt, aus dem Wörterbuch und zerstören es.

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

### <a name="handling-data-ready"></a>Verarbeiten von Daten bereit

Der OnDataReady-Handler empfängt ein SurfaceData-Objekt. Die worldAnchor-, MeshFilter- und (optional) MeshCollider-Objekte, die sie enthalten, spiegeln den aktuellen Zustand der zugeordneten räumlichen Oberfläche wider. Optional können Sie die [](../../../design/spatial-mapping.md#mesh-processing) Gittermodelldaten analysieren und/oder verarbeiten, indem Sie auf den Mesh-Member des MeshFilter-Objekts zugreifen. Rendern Sie die räumliche Oberfläche mit dem neuesten Gitternetz, und verwenden Sie sie (optional) für physikalische Kollisionen und Raycasts. Es ist wichtig zu bestätigen, dass der Inhalt von SurfaceData nicht NULL ist.

### <a name="start-processing-on-updates"></a>Starten der Verarbeitung von Updates

SurfaceObserver.Update() sollte bei einer Verzögerung aufgerufen werden, nicht bei jedem Frame.

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while (true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```
