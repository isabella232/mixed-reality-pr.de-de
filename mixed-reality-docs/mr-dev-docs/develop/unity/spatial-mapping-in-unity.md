---
title: Räumliche Abbildung in Unity
description: Erfahren Sie, wie Sie rendering und colliding mit der realen Geometrie um Sie herum in Unity Mixed Reality-Apps verwenden und verwalten.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, räumliche Zuordnung, Renderer, Collider, Mesh, Scannen, Komponente, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 62e4c4fad725dbe58773035b0bb47f1911098217
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905707"
---
# <a name="spatial-mapping-in-unity"></a>Räumliche Abbildung in Unity

[Mit der räumlichen Zuordnung](../../design/spatial-mapping.md) können Sie Dreiecksgitternetze abrufen, die die Oberflächen auf der Welt um ein HoloLens Gerät darstellen. Sie können Oberflächendaten für platzierungs-, verdeckungs- und raumanalyse verwenden, um Ihren Unity-Projekten eine zusätzliche Immersion zu verleihen.

Unity bietet vollständige Unterstützung für räumliche Zuordnungen, die Entwicklern auf folgende Weise zur Stehen kommen:

1. Im MixedRealityToolkit verfügbare Räumliche Zuordnungskomponenten, die einen bequemen und schnellen Pfad für die ersten Schritte mit der räumlichen Zuordnung bereitstellen
2. Räumliche Zuordnungs-APIs auf niedrigerer Ebene, die vollständige Kontrolle bieten und eine komplexere anwendungsspezifische Anpassung ermöglichen

Um die räumliche Zuordnung in Ihrer App zu verwenden, muss die SpatialPerception-Funktion in Ihrem AppxManifest festgelegt werden.

## <a name="device-support"></a>Geräteunterstützung

| Funktion | [HoloLens (1. Generation)](/hololens/hololens1-hardware) | [HoloLens 2](/hololens/hololens2-hardware) | [Immersive Headsets](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| Räumliche Abbildung | ✔️ | ✔️ | ❌ |

## <a name="setting-the-spatialperception-capability"></a>Festlegen der SpatialPerception-Funktion

Damit eine App räumliche Zuordnungsdaten nutzen kann, muss die SpatialPerception-Funktion aktiviert sein.

Aktivieren der SpatialPerception-Funktion:

1. Öffnen Sie im Unity-Editor den Bereich **"Player Einstellungen"** (> Project Einstellungen > Player bearbeiten).
2. Wählen Sie auf der Registerkarte **"Windows Store" aus.**
3. Erweitern Sie **"Publishing Einstellungen",** und überprüfen Sie die Funktion **"SpatialPerception"** in der Liste **"Funktionen".**

> [!NOTE]
> Wenn Sie Ihr Unity-Projekt bereits in eine Visual Studio Projektmappe exportiert haben, müssen Sie entweder in einen neuen Ordner exportieren oder [diese Funktion im AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)manuell festlegen.

Für die räumliche Zuordnung ist außerdem maxVersionTested von mindestens 10.0.10586.0 erforderlich:

1. Klicken Sie in Visual Studio im Projektmappen-Explorer mit der rechten Maustaste auf **Package.appxmanifest,** und wählen Sie **Code anzeigen** aus.
2. Suchen Sie die Zeile, die **TargetDeviceFamily** angibt, und ändern Sie **MaxVersionTested="10.0.10240.0"** in **MaxVersionTested="10.0.10586.0"**
3. **Speichern Sie** package.appxmanifest.

## <a name="how-to-add-mapping-in-unity"></a>Hinzufügen von Zuordnungen in Unity

[!INCLUDE[](includes/unity-spatial-mapping.md)]

## <a name="higher-level-mesh-analysis-spatial-understanding"></a>Gitternetzanalyse auf höherer Ebene: Räumliches Verständnis

> [!CAUTION]
> Spatial Understanding wurde zugunsten von [Scene Understanding](../../design/scene-understanding.md)als veraltet bezeichnet.

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> ist eine Sammlung von Hilfsprogrammcode für die holografische Entwicklung, die auf holografischen APIs von Unity basiert.

### <a name="spatial-understanding"></a>Räumliches Verständnis

Beim Platzieren von Hologrammen in der physischen Welt ist es oft wünschenswert, über das Gitternetz und die Oberflächenebenen der räumlichen Zuordnung hinauszugehen. Wenn die Platzierung prozedural erfolgt, ist ein höheres Maß an Umgebungsverständnis wünschenswert. Dies erfordert in der Regel Entscheidungen darüber, was Boden, Decken und Wände sind. Sie haben auch die Möglichkeit, eine Optimierung anhand einer Reihe von Platzierungseinschränkungen zu erstellen, um die besten physischen Positionen für holografische Objekte zu bestimmen.

Während der Entwicklung von Young Conker und Fragmenten stand Asobo Studio vor diesem Problem, indem er einen Raumlöser entwickelte. Jedes dieser Spiele hatte spielspezifische Anforderungen, aber sie teilten die Kerntechnologie für räumliches Verständnis. Die HoloToolkit.SpatialUnderstanding-Bibliothek kapselt diese Technologie, sodass Sie schnell leere Räume auf den Wänden finden, Objekte an der Obergrenze platzieren, die Position von Zeichen identifizieren und unzählige andere Abfragen zum räumlichen Verständnis finden können.

Der gesamte Quellcode ist enthalten, sodass Sie ihn an Ihre Anforderungen anpassen und Ihre Verbesserungen mit der Community teilen können. Der Code für den C++-Solver wurde in eine UWP-DLL umschlossen und für Unity mit einem Dropdown-Prefab im MixedRealityToolkit verfügbar gemacht.

### <a name="understanding-modules"></a>Grundlegendes zu Modulen

Es gibt drei primäre Schnittstellen, die vom Modul verfügbar gemacht werden: Topologie für einfache Oberflächen- und räumliche Abfragen, Form für die Objekterkennung und der Objektplatzierungs-Solver für die einschränkungsbasierte Platzierung von Objektsätzen. Beide Methoden werden im Folgenden beschrieben. Zusätzlich zu den drei primären Modulschnittstellen kann eine Raycast-Schnittstelle verwendet werden, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes, wasserdichtes Playspace-Gitter kann kopiert werden.

### <a name="ray-casting"></a>RayCasting

Nach Abschluss des Raumscans werden Intern Bezeichnungen für Oberflächen wie Boden, Decken und Wände generiert. Die `PlayspaceRaycast` Funktion nimmt einen Strahl entgegen und gibt zurück, wenn der Strahl mit einer bekannten Oberfläche kollidiert, und wenn ja, Informationen über diese Oberfläche in Form eines `RaycastResult` .

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

Intern wird der Raycast mit der berechneten 8-Cm-Cubevoxeldarstellung des Playspace berechnet. Jedes Voxel enthält eine Reihe von Oberflächenelementen mit verarbeiteten Topologiedaten (auch als Surfel bezeichnet). Die in der überschneideten Voxelzelle enthaltenen Surfel werden verglichen und die beste Übereinstimmung zum Suchen der Topologieinformationen verwendet. Diese Topologiedaten enthalten die Bezeichnungen, die in Form der Enumeration "SurfaceTypes" zurückgegeben werden, sowie die Oberfläche der überschneideten Oberfläche.

Im Unity-Beispiel gibt der Cursor jeden Frame einen Strahl um. Zuerst für die Collider von Unity. Zweitens im Verhältnis zur Weltdarstellung des Moduls. Und schließlich noch mal Benutzeroberflächenelemente. In dieser Anwendung erhält die Benutzeroberfläche Priorität, neben dem Ergebnis des Verständnisses und schließlich die Collider von Unity. SurfaceType wird als Text neben dem Cursor gemeldet.

![Der Oberflächentyp wird neben dem Cursor bezeichnet.](images/su-raycastresults-300px.jpg)<br>
*Der Oberflächentyp wird neben dem Cursor bezeichnet.*

### <a name="topology-queries"></a>Topologieabfragen

Innerhalb der DLL verarbeitet der Topologie-Manager die Bezeichnung der Umgebung. Wie bereits erwähnt, werden viele daten in Surfels gespeichert, die in einem Voxelvolume enthalten sind. Darüber hinaus wird die PlaySpaceInfos-Struktur verwendet, um Informationen über den Playspace zu speichern, einschließlich der Weltausrichtung (weitere Details dazu unten), Boden- und Deckenhöhe. Heuristiken werden zum Bestimmen von Boden, Decken und Wänden verwendet. Beispielsweise wird die größte und niedrigste horizontale Oberfläche mit einer Fläche von mehr als 1 m2 als Bodenbelag betrachtet.

> [!NOTE]
> Der Kamerapfad während des Scanvorgangs wird auch in diesem Prozess verwendet.

Eine Teilmenge der Abfragen, die vom Topologie-Manager verfügbar gemacht werden, wird über die DLL verfügbar gemacht. Die verfügbar gemachten Topologieabfragen sind wie folgt.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Jede der Abfragen verfügt über eine Reihe von Parametern, die für den Abfragetyp spezifisch sind. Im folgenden Beispiel gibt der Benutzer die mindeste Höhe & Breite des gewünschten Volumens, die minimale Platzierungshöhe über dem Boden und die mindeste Menge an Plätzen vor dem Volume an. Alle Messungen sind in Metern.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Jede dieser Abfragen verwendet ein vorab zugeordnetes Array von "TopologyResult"-Strukturen. Der Parameter "locationCount" gibt die Länge des übergebenen Arrays an. Der Rückgabewert gibt die Anzahl der zurückgegebenen Standorte an. Diese Zahl ist nie größer als der übergebene parameter "locationCount".

"TopologyResult" enthält die Mittlere Position des zurückgegebenen Volumes, die Ausrichtungsrichtung (d. h. normal) und die Abmessungen des gefundenen Raums.

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
> Im Unity-Beispiel wird jede dieser Abfragen mit einer Schaltfläche im Bereich der virtuellen Benutzeroberfläche verknüpft. Im Beispiel werden die Parameter für jede dieser Abfragen hart in sinnvolle Werte einkodiert. Weitere Beispiele finden Sie unter SpaceVisualizer.cs im Beispielcode.

### <a name="shape-queries"></a>Shape-Abfragen

In der DLL verwendet das Shape-Analyseprogramm ("ShapeAnalyzer_W") die Topologieanalyse, um benutzerdefinierte Formen abzugleichen, die vom Benutzer definiert werden. Das Unity-Beispiel definiert eine Reihe von Formen und macht die Ergebnisse über das In-App-Abfragemenü auf der Registerkarte "Form" verfügbar. Die Absicht besteht darin, dass der Benutzer seine eigenen Objektformabfragen definieren und diese nach Bedarf für seine Anwendung verwenden kann.

Die Formanalyse funktioniert nur auf horizontalen Oberflächen. Eine Couch wird z. B. durch die flache Oberfläche des Platzes und die flache Oberseite der Couch definiert. Die Formabfrage sucht nach zwei Oberflächen mit einer bestimmten Größe, Höhe und einem bestimmten Seitenbereich, wobei die beiden Oberflächen ausgerichtet und verbunden sind. Mithilfe der APIs-Terminologie sind der Couchplatz und die Rückseite Formkomponenten, und die Ausrichtungsanforderungen sind Einschränkungen für Formkomponenten.

Eine Beispielabfrage, die im Unity-Beispiel (ShapeDefinition.cs) für "sittable"-Objekte definiert ist, lautet wie folgt.

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

Jede Formabfrage wird durch einen Satz von Formkomponenten definiert, die jeweils einen Satz von Komponenteneinschränkungen und eine Reihe von Shape-Einschränkungen aufweisen, die Abhängigkeiten zwischen den Komponenten auflisten. Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponentendefinition und keine Formeinschränkungen zwischen Komponenten (da es nur eine Komponente gibt).

Im Gegensatz dazu weist die Couchform zwei Formkomponenten und vier Formeinschränkungen auf. Komponenten werden anhand ihres Indexes in der Komponentenliste des Benutzers identifiziert (in diesem Beispiel 0 und 1).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Wrapperfunktionen werden im Unity-Modul bereitgestellt, um benutzerdefinierte Formdefinitionen einfach zu erstellen. Die vollständige Liste der Komponenten- und Shape-Einschränkungen finden Sie in "SpatialUnderstandingDll.cs" in den Strukturen "ShapeComponentConstraint" und "ShapeConstraint".

![Rechteckform befindet sich auf dieser Oberfläche.](images/su-shapequery-300px.jpg)<br>
*Rechteckform befindet sich auf dieser Oberfläche.*

### <a name="object-placement-solver"></a>Objektplatzierungs-Solver

Der Objektplatzierungs-Solver kann verwendet werden, um ideale Positionen im physischen Raum zu identifizieren, um Ihre Objekte zu platzieren. Der Solver findet die am besten geeignete Position, wenn die Objektregeln und -einschränkungen gelten. Darüber hinaus bleiben Objektabfragen erhalten, bis das Objekt mit Solver_RemoveObject- oder Solver_RemoveAllObjects-Aufrufen entfernt wird, was eine eingeschränkte Platzierung mehrerer Objekte ermöglicht. Objektplatzierungsabfragen bestehen aus drei Teilen: platzierungstyp mit Parametern, einer Liste von Regeln und einer Liste von Einschränkungen. Verwenden Sie die folgende API, um eine Abfrage auszuführen.

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

Diese Funktion nimmt einen Objektnamen, eine Platzierungsdefinition und eine Liste von Regeln und Einschränkungen an. Die C#-Wrapper stellen Konstruktionshilfsfunktionen bereit, um die Erstellung von Regeln und Einschränkungen zu vereinfachen. Die Platzierungsdefinition enthält den Abfragetyp, d. h. einen der folgenden.

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

Jeder Platzierungstyp verfügt über einen Satz von Parametern, die für den Typ eindeutig sind. Die ObjectPlacementDefinition-Struktur enthält eine Reihe von statischen Hilfsfunktionen zum Erstellen dieser Definitionen. Um z. B. einen Ort zu finden, an dem ein Objekt auf dem Boden abgestellt werden kann, können Sie die folgende Funktion verwenden. public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) Zusätzlich zum Platzierungstyp können Sie eine Reihe von Regeln und Einschränkungen bereitstellen. Regeln können nicht verletzt werden. Mögliche Platzierungsstandorte, die den Typ und die Regeln erfüllen, werden dann anhand des Satzes von Einschränkungen optimiert, um den optimalen Platzierungsstandort auszuwählen. Jede der Regeln und Einschränkungen kann von den bereitgestellten statischen Erstellungsfunktionen erstellt werden. Nachfolgend finden Sie ein Beispiel für eine Regel- und Einschränkungskonstruktionsfunktion.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

Die folgende Objektplatzierungsabfrage sucht nach einem Ort, an dem ein halber Meter Cube am Rand einer Oberfläche platziert werden kann, weit weg von anderen zuvor platzierten Objekten und in der Nähe der Mitte des Raumes.

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

Bei Erfolg wird eine "ObjectPlacementResult"-Struktur zurückgegeben, die die Platzierungsposition, Dimensionen und Ausrichtung enthält. Darüber hinaus wird die Platzierung der internen Liste der platzierten Objekte der DLL hinzugefügt. Nachfolgende Platzierungsabfragen berücksichtigen dieses Objekt. Die Datei "LevelSolver.cs" im Unity-Beispiel enthält weitere Beispielabfragen.

![Ergebnisse der Objektplatzierung](images/su-objectplacement-1000px.jpg)<br>
*Abbildung 3: Die blauen Felder, in die das Ergebnis von drei Abfragen auf dem Boden gestellt wird, ohne die Kamerapositionsregeln zu ändern*

Bei der Lösung für die Platzierung von mehreren Objekten, die für ein Ebenen- oder Anwendungsszenario erforderlich sind, lösen Sie zuerst die Hebung und große Objekte, um die Wahrscheinlichkeit zu maximieren, dass ein Raum gefunden werden kann. Die Platzierungsreihenfolge ist wichtig. Wenn Objektplatzierungen nicht gefunden werden können, versuchen Sie es mit weniger eingeschränkten Konfigurationen. Eine Reihe von Fallbackkonfigurationen ist entscheidend für die Unterstützung von Funktionen in vielen Raumkonfigurationen.

### <a name="room-scanning-process"></a>Raumscanprozess

Während die vom HoloLens bereitgestellte Räumliche Zuordnungslösung so konzipiert ist, dass sie generisch genug ist, um die Anforderungen der gesamten Bandbreite von Problemräumen zu erfüllen, wurde das Spatial Understanding-Modul entwickelt, um die Anforderungen von zwei bestimmten Spielen zu unterstützen. Die Lösung basiert auf einem bestimmten Prozess und einer Reihe von Annahmen, die unten zusammengefasst sind.

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

Benutzergesteuertes Playspace "Zeichnen": Während der Überprüfungsphase bewegt sich der Benutzer und sieht sich die Spielgeschwindigkeit an, wobei die Bereiche, die einbezogen werden sollten, effektiv zeichnen. Das generierte Gitternetz ist wichtig, um benutzerfeedback während dieser Phase bereitzustellen. Gebäudeeinrichtung für Gebäude oder Büro: Die Abfragefunktionen sind für flache Oberflächen und Wände in rechten Winkeln konzipiert. Dies ist eine weiche Einschränkung. Während der Überprüfungsphase wird jedoch eine Primärachsenanalyse durchgeführt, um das Gitternetz-Mosaik entlang der Haupt- und Nebenachse zu optimieren. Die enthaltene Datei SpatialUnderstanding.cs verwaltet den Überprüfungsphasenprozess. Sie ruft die folgenden Funktionen auf.

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

Der Scanflow, der durch das Verhalten "SpatialUnderstanding" gesteuert wird, ruft InitScan und dann Jeden Frame aktualisierenScan auf. Wenn die Statistikabfrage eine angemessene Abdeckung meldet, kann der Benutzer "RequestFinish" aufrufen, um das Ende der Überprüfungsphase anzugeben. UpdateScan wird weiterhin aufgerufen, bis der Rückgabewert angibt, dass die DLL die Verarbeitung abgeschlossen hat.

### <a name="understanding-mesh"></a>Grundlegendes zu Mesh

Die Understanding-DLL speichert den Playspace intern als Raster mit Voxelcubes mit einer Größe von 8 cm. Während des ersten Teils der Überprüfung wird eine primäre Komponentenanalyse abgeschlossen, um die Achsen des Raumes zu bestimmen. Intern speichert er seinen Voxelbereich, der an diesen Achsen ausgerichtet ist. Ein Gitternetz wird ungefähr jede Sekunde generiert, indem die Isosurface aus dem Voxelvolume extrahiert wird.

![Generiertes Netz, das aus dem Voxelvolume erzeugt wird](images/su-custommesh.jpg)<br>
*Generiertes Netz, das aus dem Voxelvolume erzeugt wird*

## <a name="troubleshooting"></a>Problembehandlung

* Stellen Sie sicher, dass Sie die [SpatialPerception-Funktion](#setting-the-spatialperception-capability) festgelegt haben.
* Wenn die Nachverfolgung verloren geht, entfernt das nächste OnSurfaceChanged-Ereignis alle Gitternetze.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Räumliche Zuordnung im Mixed Reality Toolkit

Weitere Informationen zur Verwendung der räumlichen Zuordnung mit Mixed Reality Toolkit finden Sie im [Abschnitt räumliche Wahrnehmung](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) der MRTK-Dokumentation.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, befinden Sie sich in der Mitte der MRTK-Kernbausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

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
