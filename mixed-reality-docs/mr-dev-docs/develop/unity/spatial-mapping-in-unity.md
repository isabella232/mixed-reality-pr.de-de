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
# <a name="spatial-mapping-in-unity"></a>Räumliche Abbildung in Unity

[Mit der räumlichen](../../design/spatial-mapping.md) Zuordnung können Sie Dreiecksgitternetze abrufen, die die Oberflächen in der Welt um ein HoloLens-Gerät darstellen. Sie können Oberflächendaten für die Platzierung, Okklusion und Raumanalyse verwenden, um Ihren Unity-Projekten eine zusätzliche Portion Immersion zu bieten.

Unity bietet vollständige Unterstützung für die räumliche Zuordnung, die Entwicklern auf folgende Weise zur Verfügung steht:

1. Im MixedRealityToolkit verfügbare Räumliche Zuordnungskomponenten, die einen komfortablen und schnellen Pfad für die ersten Schritte mit der räumlichen Zuordnung bereitstellen
2. APIs für die räumliche Zuordnung auf niedrigerer Ebene, die vollständige Kontrolle bieten und komplexere anwendungsspezifische Anpassungen ermöglichen

Um die räumliche Zuordnung in Ihrer App zu verwenden, muss die spatialPerception-Funktion in Ihrem AppxManifest festgelegt werden.

## <a name="device-support"></a>Geräteunterstützung

| Funktion | [HoloLens (1. Generation)](/hololens/hololens1-hardware) | [HoloLens 2](/hololens/hololens2-hardware) | [Immersive Headsets](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| Räumliche Abbildung | ✔️ | ✔️ | ❌ |

## <a name="setting-the-spatialperception-capability"></a>Festlegen der SpatialPerception-Funktion

Damit eine App räumliche Zuordnungsdaten nutzen kann, muss die SpatialPerception-Funktion aktiviert sein.

Aktivieren der SpatialPerception-Funktion:

1. Öffnen Sie im Unity-Editor den **Bereich "Playereinstellungen"** (Bearbeiten > Projekteinstellungen > Player).
2. Wählen Sie auf der **Registerkarte "Windows Store" aus.**
3. Erweitern **Sie "Veröffentlichungseinstellungen",** und überprüfen Sie die **Funktion "SpatialPerception"** in der **Liste "Funktionen".**

> [!NOTE]
> Wenn Sie Ihr Unity-Projekt bereits in eine Visual Studio-Projektmappe exportiert haben, müssen Sie entweder in einen neuen Ordner exportieren oder diese Funktion manuell im [AppxManifest in](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)Visual Studio.

Für die räumliche Zuordnung ist außerdem ein MaxVersionTested-Objekt von mindestens 10.0.10586.0 erforderlich:

1. Klicken Visual Studio mit der rechten Maustaste auf **Package.appxmanifest** im Projektmappen-Explorer und wählen Sie **Code anzeigen aus.**
2. Suchen Sie die Zeile mit **TargetDeviceFamily,** und ändern Sie **MaxVersionTested="10.0.10240.0"** in **MaxVersionTested="10.0.10586.0"**
3. **Speichern** Sie package.appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Erste Schritte mit den integrierten Komponenten der räumlichen Zuordnung von Unity

Unity bietet zwei Komponenten zum einfachen Hinzufügen von räumlicher Zuordnung zu Ihrer App: **Spatial Mapping Renderer** und **Spatial Mapping Collider.**

### <a name="spatial-mapping-renderer"></a>Renderer für räumliche Zuordnung

Der Renderer für räumliche Zuordnung ermöglicht die Visualisierung des Gitters für räumliche Zuordnungen.

![Spatial Mapping Renderer in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Spatial Mapping Collider

Der Spatial Mapping Collider ermöglicht holografische Inhaltsinteraktion (oder Zeicheninteraktion, z. B. Physik) mit dem Gitternetz der räumlichen Zuordnung.

![Spatial Mapping Collider in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Verwenden der integrierten Räumlichen Zuordnungskomponenten

Sie können Ihrer App beide Komponenten hinzufügen, wenn Sie sowohl physische Oberflächen visualisieren als auch mit ihnen interagieren möchten.

So verwenden Sie diese beiden Komponenten in Ihrer Unity-App:

1. Wählen Sie ein GameObject in der Mitte des Bereichs aus, in dem Sie Gitternetze für räumliche Oberflächen erkennen möchten.
2. Fügen Sie im Inspektorfenster **komponente**  >  **XR**  >  **Spatial Mapping Collider oder** Spatial Mapping **Renderer hinzu.**

Weitere Informationen zur Verwendung dieser Komponenten finden Sie auf der <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity-Dokumentationswebsite.</a>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Über die integrierten Räumlichen Zuordnungskomponenten hinausgehen

Diese Komponenten machen es einfach, mit Drag & Drop mit der räumlichen Zuordnung zu beginnen.  Wenn Sie weiter gehen möchten, gibt es zwei Hauptpfade, die Sie erkunden können:

* Informationen zur eigenen Gitternetzverarbeitung auf niedrigerer Ebene finden Sie im folgenden Abschnitt zur Skript-API für die räumliche Zuordnung auf niedriger Ebene.
* Informationen zur Gitternetzanalyse auf höherer Ebene finden Sie im abschnitt unten zur SpatialUnderstanding-Bibliothek in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit.</a>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Verwenden der Unity Spatial Mapping-API auf niedriger Ebene

Wenn Sie mehr Kontrolle benötigen, als die Komponenten Spatial Mapping Renderer und Spatial Mapping Collider bieten, verwenden Sie die low-level Spatial Mapping-APIs.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typen:** *SurfaceObserver,* *SurfaceChange,* *SurfaceData,* *SurfaceId*

Wir haben den vorgeschlagenen Ablauf für eine Anwendung beschrieben, die die APIs für die räumliche Zuordnung in den folgenden Abschnitten verwendet.

### <a name="set-up-the-surfaceobservers"></a>Einrichten der SurfaceObserver

Instanziieren Sie ein SurfaceObserver-Objekt für jeden anwendungsdefinierten Raumbereich, für den Sie räumliche Zuordnungsdaten benötigen.

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

Geben Sie den Bereich des Speicherplatzes an, für den jedes SurfaceObserver-Objekt Daten bereitstellen soll, indem Sie Entweder SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox oder SetVolumeAsFrustum aufrufen. Sie können den Bereich des Raumes in Zukunft neu definieren, indem Sie einfach eine dieser Methoden erneut aufrufen.

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Wenn Sie SurfaceObserver.Update() aufrufen, müssen Sie einen Handler für jede räumliche Oberfläche im Raumbereich des SurfaceObserver bereitstellen, für den das Raumzuordnungssystem neue Informationen enthält. Der Handler empfängt für eine räumliche Oberfläche:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>Behandeln von Oberflächenänderungen

Es gibt mehrere Hauptfälle, die behandelt werden müssen: hinzugefügt und aktualisiert, die denselben Codepfad verwenden und entfernt werden können.

* In den hinzugefügten und aktualisierten Fällen fügen wir das GameObject hinzu, das dieses Gitternetz darstellt, rufen es aus dem Wörterbuch ab, erstellen eine SurfaceData-Struktur mit den erforderlichen Komponenten und rufen dann RequestMeshDataAsync auf, um das GameObject mit den Gitterdaten und der Position in der Szene zu füllen.
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

Der OnDataReady-Handler empfängt ein SurfaceData-Objekt. Die enthaltenen Objekte WorldAnchor, MeshFilter und (optional) MeshCollider spiegeln den aktuellen Zustand der zugeordneten räumlichen Oberfläche wider. Optional können Sie die [](../../design/spatial-mapping.md#mesh-processing) Gittermodelldaten analysieren und/oder verarbeiten, indem Sie auf den Mesh-Member des MeshFilter-Objekts zugreifen. Rendern Sie die räumliche Oberfläche mit dem neuesten Gitternetz, und verwenden Sie sie (optional) für physikalische Kollisionen und Raycasts. Es ist wichtig zu bestätigen, dass der Inhalt von SurfaceData nicht NULL ist.

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
    while(true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```

## <a name="higher-level-mesh-analysis-spatial-understanding"></a>Gitternetzanalyse auf höherer Ebene: Räumliches Verständnis

> [!CAUTION]
> Spatial Understanding wurde zugunsten von Scene Understanding als veraltet [bezeichnet.](../../design/scene-understanding.md)

Das <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> ist eine Sammlung von Hilfsprogrammcode für die holografische Entwicklung, die auf den holografischen APIs von Unity basiert.

### <a name="spatial-understanding"></a>Räumliches Verständnis

Wenn Hologramme in der physischen Welt platziert werden, ist es oft wünschenswert, über die Gitter- und Oberflächenebenen der räumlichen Zuordnung hinaus zu gehen. Wenn die Platzierung prozedural erfolgt, ist ein höheres Maß an Umgebungsverständnis wünschenswert. Dies erfordert in der Regel Entscheidungen darüber, was Boden, Decke und Wand sind. Sie haben auch die Möglichkeit, mit einer Reihe von Platzierungseinschränkungen zu optimieren, um die besten physischen Standorte für holografische Objekte zu bestimmen.

Während der Entwicklung von Young Conker und Fragmenten stand Asobo Studio diesem Problem gegenüber, indem es einen Raum-Solver entwickelt hat. Jedes dieser Spiele hatte spielspezifische Anforderungen, aber es wurde eine gemeinsame Technologie für räumliches Verständnis genutzt. Die HoloToolkit.SpatialUnderstanding-Bibliothek kapselt diese Technologie, sodass Sie schnell leere Räume an den Wänden finden, Objekte an der Decke platzieren, platzierte Zeichen erkennen und unzählige andere Abfragen des räumlichen Verständnisses finden können.

Der ganze Quellcode ist enthalten, sodass Sie ihn an Ihre Anforderungen anpassen und Ihre Verbesserungen für die Community freigeben können. Der Code für den C++-Solver wurde in eine UWP-DLL umschlossen und für Unity mit einem Drop in Prefab verfügbar gemacht, das im MixedRealityToolkit enthalten ist.

### <a name="understanding-modules"></a>Grundlegendes zu Modulen

Es gibt drei primäre Schnittstellen, die vom Modul verfügbar gemacht werden: Topologie für einfache Oberflächen- und räumliche Abfragen, Form für die Objekterkennung und der Objektplatzierungs-Solver für die einschränkungsbasierte Platzierung von Objektsätzen. Beide Methoden werden im Folgenden beschrieben. Zusätzlich zu den drei primären Modulschnittstellen kann eine Raycastschnittstelle verwendet werden, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes wasserdichtes Playspacenetz kann kopiert werden.

### <a name="ray-casting"></a>RayCasting

Nach Abschluss des Raumscans werden Bezeichnungen für Oberflächen wie Boden, Decke und Wand intern generiert. Die Funktion nimmt einen Strahl und gibt zurück, wenn der Strahl mit einer bekannten Oberfläche kollidiert, und wenn ja, Informationen über diese Oberfläche `PlayspaceRaycast` in Form eines `RaycastResult` .

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

Intern wird der Raycast anhand der berechneten 8 cm großen voxelbasierten Voxeldarstellung des Playspace berechnet. Jedes Voxel enthält eine Reihe von Oberflächenelementen mit verarbeiteten Topologiedaten (auch bekannt als Surfel). Die in der überschneidenden Voxelzelle enthaltenen Surfel werden verglichen, und die beste Übereinstimmung wird zum Suchen der Topologieinformationen verwendet. Diese Topologiedaten enthalten die Bezeichnungen, die in Form der Enumeration "SurfaceTypes" zurückgegeben werden, sowie die Oberfläche der überschneidenden Oberfläche.

Im Unity-Beispiel wirft der Cursor einen Strahl in jeden Frame. Zuerst gegen die Collider von Unity. Zweitens gegen die Weltdarstellung des Understanding-Moduls. Und schließlich wieder Benutzeroberflächenelemente. In dieser Anwendung erhält die Benutzeroberfläche Priorität, als Nächstes das Verständnisergebnis und schließlich die Collider von Unity. SurfaceType wird als Text neben dem Cursor gemeldet.

![Der Oberflächentyp wird neben dem Cursor bezeichnet.](images/su-raycastresults-300px.jpg)<br>
*Surface type (Oberflächentyp) wird neben dem Cursor bezeichnet.*

### <a name="topology-queries"></a>Topologieabfragen

Innerhalb der DLL übernimmt der Topologie-Manager die Bezeichnung der Umgebung. Wie bereits erwähnt, werden viele der Daten in Surfel gespeichert, die in einem Voxelvolumen enthalten sind. Darüber hinaus wird die "PlaySpaceInfos"-Struktur verwendet, um Informationen zum Playspace zu speichern, einschließlich der Ausrichtung der Welt (weitere Details dazu unten), der Höhe des Bodens und der Decke. Heuristiken werden zum Bestimmen von Boden, Decke und Wand verwendet. Beispielsweise wird die größte und niedrigste horizontale Oberfläche mit einer Fläche von mehr als 1 m2 als Boden betrachtet.

> [!NOTE]
> In diesem Prozess wird auch der Kamerapfad während des Scanvorgangs verwendet.

Eine Teilmenge der vom Topologie-Manager verfügbar gemachten Abfragen wird über die DLL verfügbar gemacht. Die verfügbar gemachten Topologieabfragen lauten wie folgt.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Jede der Abfragen verfügt über eine Reihe von Parametern, die für den Abfragetyp spezifisch sind. Im folgenden Beispiel gibt der Benutzer die Mindesthöhe & Breite des gewünschten Volumes, die mindeste Platzierungshöhe über dem Boden und die Mindestmenge an Belägen vor dem Volume an. Alle Messungen werden in Metern durchgeführt.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Jede dieser Abfragen nimmt ein vorab zugeordnetes Array von "TopologyResult"-Strukturen an. Der Parameter "locationCount" gibt die Länge des übergebenen Arrays an. Der Rückgabewert gibt die Anzahl der zurückgegebenen Speicherorte an. Diese Zahl ist nie größer als der übergebene "locationCount"-Parameter.

Das "TopologyResult" enthält die Mittelpunktposition des zurückgegebenen Volumes, die Ausrichtungsrichtung (d. h. normal) und die Abmessungen des gefundenen Raums.

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
> Im Unity-Beispiel wird jede dieser Abfragen mit einer Schaltfläche im Bereich der virtuellen Benutzeroberfläche verknüpft. Im Beispiel werden die Parameter für jede dieser Abfragen mit angemessenen Werten hartkodiert. Weitere Beispiele finden Sie unter SpaceVisualizer.cs im Beispielcode.

### <a name="shape-queries"></a>Formabfragen

In der DLL verwendet das Shape-Analyseprogramm ("ShapeAnalyzer_W") die Topologieanalyse, um mit benutzerdefinierten Formen zu übereinstimmen, die vom Benutzer definiert wurden. Das Unity-Beispiel definiert eine Reihe von Formen und macht die Ergebnisse über das Abfragemenü in der App auf der Registerkarte Form verfügbar. Die Absicht ist, dass der Benutzer seine eigenen Objektformabfragen definieren und diese nach Bedarf von seiner Anwendung verwenden kann.

Die Formanalyse funktioniert nur auf horizontalen Oberflächen. Eine Couch wird z. B. durch die flache Seatoberfläche und die flache Oberseite der Couch zurück definiert. Die Shape-Abfrage sucht nach zwei Oberflächen mit einer bestimmten Größe, Höhe und einem bestimmten Seitenbereich, bei denen die beiden Oberflächen ausgerichtet und verbunden sind. Unter Verwendung der APIs-Terminologie sind der Couchplatz und die Rückseite Formkomponenten, und die Ausrichtungsanforderungen sind Shape-Komponenteneinschränkungen.

Eine im Unity-Beispiel (ShapeDefinition.cs) definierte Beispielabfrage für "sittable"-Objekte lautet wie folgt.

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

Jede Shape-Abfrage wird durch einen Satz von Formkomponenten definiert, die jeweils eine Reihe von Komponenteneinschränkungen und eine Reihe von Shape-Einschränkungen aufweisen, die Abhängigkeiten zwischen den Komponenten auflisten. Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponentendefinition und keine Shape-Einschränkungen zwischen Komponenten (da es nur eine Komponente gibt).

Im Gegensatz dazu verfügt die Form "Couch" über zwei Formkomponenten und vier Formeinschränkungen. Komponenten werden durch ihren Index in der Komponentenliste des Benutzers identifiziert (in diesem Beispiel 0 und 1).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Wrapperfunktionen werden im Unity-Modul zur einfachen Erstellung benutzerdefinierter Shape-Definitionen bereitgestellt. Die vollständige Liste der Komponenten- und Formeinschränkungen finden Sie in "SpatialUnderstandingDll.cs" in den Strukturen "ShapeComponentConstraint" und "ShapeConstraint".

![Rechteckform befindet sich auf dieser Oberfläche](images/su-shapequery-300px.jpg)<br>
*Rechteckform befindet sich auf dieser Oberfläche*

### <a name="object-placement-solver"></a>Objektplatzierungs-Solver

Der Objektplatzierungs-Solver kann verwendet werden, um ideale Positionen im physischen Raum zu identifizieren, an dem Ihre Objekte platzieren werden. Der Solver findet die am besten passende Position, wenn die Objektregeln und Einschränkungen gegeben sind. Darüber hinaus bleiben Objektabfragen bestehen, bis das Objekt mit "Solver_RemoveObject"- oder "Solver_RemoveAllObjects"-Aufrufen entfernt wird, wodurch eine eingeschränkte Platzierung mit mehreren Objekten ermöglicht wird. Objektplatzierungsabfragen bestehen aus drei Teilen: Platzierungstyp mit Parametern, einer Liste von Regeln und einer Liste von Einschränkungen. Verwenden Sie die folgende API, um eine Abfrage auszuführen.

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

Diese Funktion verwendet einen Objektnamen, eine Platzierungsdefinition und eine Liste von Regeln und Einschränkungen. Die C#-Wrapper stellen Konstruktionshilfefunktionen zur Verfügung, um die Regel- und Einschränkungskonstruktion zu einfach zu machen. Die Platzierungsdefinition enthält den Abfragetyp, d. &a. eine der folgenden Typen.

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

Jeder Der Platzierungstypen verfügt über einen Satz von Parametern, die für den Typ eindeutig sind. Die "ObjectPlacementDefinition"-Struktur enthält eine Reihe statischer Hilfsfunktionen zum Erstellen dieser Definitionen. Sie können beispielsweise die folgende Funktion verwenden, um einen Ort zu finden, an dem sie ein Objekt auf dem Boden platzieren können. public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) Zusätzlich zum Platzierungstyp können Sie eine Reihe von Regeln und Einschränkungen bereitstellen. Regeln können nicht verletzt werden. Mögliche Platzierungsstandorte, die den Typ und die Regeln erfüllen, werden dann für den Satz von Einschränkungen optimiert, um den optimalen Platzierungsort auszuwählen. Jede der Regeln und Einschränkungen kann von den bereitgestellten statischen Erstellungsfunktionen erstellt werden. Eine Beispielfunktion für die Regel- und Einschränkungskonstruktion finden Sie unten.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

Die folgende Objektplatzierungsabfrage sucht nach einem Ort, an dem sie einen halb meter langen Würfel am Rand einer Oberfläche platzieren kann, weg von anderen zuvor platzierenden Objekten und in der Nähe der Mitte des Raumes.

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

Bei Erfolg wird eine ObjectPlacementResult-Struktur zurückgegeben, die position, dimensions und orientation enthält. Darüber hinaus wird die Platzierung der internen Liste der platzierten Objekte der DLL hinzugefügt. Bei nachfolgenden Platzierungsabfragen wird dieses Objekt berücksichtigt. Die Datei "LevelSolver.cs" im Unity-Beispiel enthält weitere Beispielabfragen.

![Ergebnisse der Objektplatzierung](images/su-objectplacement-1000px.jpg)<br>
*Abbildung 3: Die blauen Felder zeigen, wie sich das Ergebnis aus Abfragen vom Dreierort im Boden mit Weg von Kamerapositionsregeln ergeben kann.*

Lösen Sie beim Lösen der Platzierungsposition mehrerer Objekte, die für ein Ebenen- oder Anwendungsszenario erforderlich sind, zuerst die Lösung für Bzw. große Objekte, um die Wahrscheinlichkeit zu maximieren, dass ein Raum gefunden werden kann. Die Platzierungs reihenfolge ist wichtig. Wenn Objektplatzierungen nicht gefunden werden können, versuchen Sie weniger eingeschränkte Konfigurationen. Eine Reihe von Fallbackkonfigurationen ist entscheidend für die Unterstützung von Funktionen für viele Raumkonfigurationen.

### <a name="room-scanning-process"></a>Raumscanprozess

Die von HoloLens bereitgestellte Räumliche Zuordnungslösung ist so konzipiert, dass sie generisch genug ist, um die Anforderungen der gesamten Gamut der Problemräume zu erfüllen, aber das Spatial Understanding-Modul wurde erstellt, um die Anforderungen von zwei bestimmten Spielen zu unterstützen. Die Lösung ist um einen bestimmten Prozess und eine Reihe von Annahmen strukturiert, die unten zusammengefasst sind.

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

Benutzergesteuertes "Malen" des Playspace: Während der Überprüfungsphase bewegt sich der Benutzer und sieht sich die Spielgeschwindigkeit an, um die Bereiche effektiv zu malen, die eingeschlossen werden sollten. Das generierte Gitternetz ist wichtig, um während dieser Phase Benutzerfeedback zu geben. Einrichtung von Heim- oder Bürogebäuden: Die Abfragefunktionen sind auf flache Oberflächen und Wände in rechten Winkeln ausgelegt. Dies ist eine weiche Einschränkung. Während der Überprüfungsphase wird jedoch eine Primäre Achsenanalyse abgeschlossen, um das Gitternetz-Mosaik entlang der Haupt- und Nebenachse zu optimieren. Die enthaltene Datei SpatialUnderstanding.cs verwaltet den Überprüfungsphasenprozess. Sie ruft die folgenden Funktionen auf.

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

Der Scanfluss, der vom Verhalten "SpatialUnderstanding" gesteuert wird, ruft InitScan und dann UpdateScan für jeden Frame auf. Wenn die Statistikabfrage eine angemessene Abdeckung meldet, kann der Benutzer requestFinish aufrufen, um das Ende der Überprüfungsphase anzugeben. UpdateScan wird weiterhin aufgerufen, bis sein Rückgabewert angibt, dass die DLL die Verarbeitung abgeschlossen hat.

### <a name="understanding-mesh"></a>Grundlegendes zu Mesh

Die grundlegende DLL speichert den Playspace intern als Raster mit Voxelcubes mit einer Größe von 8 cm. Während des ersten Teils der Überprüfung wird eine Primäre Komponentenanalyse abgeschlossen, um die Achsen des Raums zu bestimmen. Intern speichert es seinen Voxelraum, der an diesen Achsen ausgerichtet ist. Ein Gitternetz wird ungefähr jede Sekunde generiert, indem die Isosurface aus dem Voxelvolumen extrahiert wird.

![Generiertes Gitternetz, das aus dem Voxelvolumen erzeugt wird](images/su-custommesh.jpg)<br>
*Generiertes Gitternetz, das aus dem Voxelvolumen erzeugt wird*

## <a name="troubleshooting"></a>Problembehandlung

* Stellen Sie sicher, dass Sie die [SpatialPerception-Funktion festgelegt](#setting-the-spatialperception-capability) haben.
* Wenn die Nachverfolgung verloren geht, entfernt das nächste OnSurfaceChanged-Ereignis alle Gitternetze.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Spatial Mapping im Mixed Reality Toolkit

Weitere Informationen zur Verwendung von Spatial Mapping mit Mixed Reality Toolkit finden Sie im Abschnitt räumliche Wahrnehmung [der](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) MRTK-Dokumentation.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie den weg zur Unity-Entwicklung folgen, den wir festgelegt haben, sind Sie gerade dabei, die MRTK-Kernbausteine zu erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch

* [Koordinatensysteme](../../design/coordinate-systems.md)
* [Koordinatensysteme in Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
