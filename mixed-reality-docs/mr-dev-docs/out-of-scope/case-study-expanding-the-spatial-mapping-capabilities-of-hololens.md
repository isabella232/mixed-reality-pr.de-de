---
title: 'Fallstudie: Erweitern der Räumlichen Zuordnungsfunktionen HoloLens'
description: Beim Erstellen unserer ersten Apps für Microsoft HoloLens waren wir gespannt darauf, wie weit wir die Grenzen der räumlichen Zuordnung auf dem Gerät verschieben konnten.
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, räumliche Zuordnung
ms.openlocfilehash: f0438990c39570f9188e2e150a8cbe7907d72f7e2be260c72e41646565b8d89e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210446"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Fallstudie: Erweitern der Räumlichen Zuordnungsfunktionen HoloLens

Beim Erstellen unserer ersten Apps für Microsoft HoloLens waren wir gespannt darauf, wie weit wir die Grenzen der räumlichen Zuordnung auf dem Gerät verschieben konnten. Jeff Evertt, Softwareentwickler bei Microsoft Studio, erklärt, wie eine neue Technologie entwickelt wurde, ohne dass mehr Kontrolle darüber benötigt wird, wie Hologramme in der realen Umgebung eines Benutzers platziert werden.

> [!NOTE]
> HoloLens 2 implementiert eine neue [Scene Understanding Runtime,](../design/scene-understanding.md)die Mixed Reality Entwicklern eine strukturierte, grundlegende Umgebungsdarstellung bietet, die die Entwicklung für benutzerorientierte Anwendungen intuitiv macht. 

## <a name="watch-the-video"></a>Video ansehen

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Über die räumliche Zuordnung hinaus

Während wir an [Fragmenten](https://www.microsoft.com/p/fragments/9nblggh5ggm8) und [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)arbeiteten, haben wir zwei der ersten Spiele für HoloLens festgestellt, dass wir bei der prozeduralen Platzierung von Hologrammen in der physischen Welt ein höheres Verständnis der Umgebung des Benutzers benötigen. Jedes Spiel hatte seine eigenen spezifischen Platzierungsanforderungen: In Fragmenten wollten wir beispielsweise zwischen verschiedenen Oberflächen unterscheiden können , z. B. dem Boden oder einer Tabelle, um Hinweise an relevanten Stellen zu platzieren. Wir wollten auch Oberflächen identifizieren können, auf denen holografische Zeichen in Lebensgröße zu sehen sind, z. B. eine Couch oder einen Sessel. In Young Conker wollten wir, dass Conker und seine Kollegen erhöhte Oberflächen im Raum eines Spielers als Plattformen verwenden können.

[Asobo Studio,](https://www.asobostudio.com/index.html)unser Entwicklungspartner für diese Spiele, stand vor diesem Problem und hat eine Technologie entwickelt, die die Funktionen der räumlichen HoloLens. Dadurch könnten wir den Raum eines Spielers analysieren und Oberflächen wie Wände, Tabellen, Tafeln und Boden identifizieren. Außerdem haben sie uns die Möglichkeit gegeben, einen Satz von Einschränkungen zu optimieren, um die beste Platzierung für holografische Objekte zu bestimmen.

## <a name="the-spatial-understanding-code"></a>Der Code für räumliches Verständnis

Wir haben den ursprünglichen Code von Asobo verwendet und eine Bibliothek erstellt, die diese Technologie kapselt. Microsoft und Asobo haben diesen Code nun als Open-Source-Code erstellt und im [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) zur Verfügung gestellt, damit Sie ihn in Ihren eigenen Projekten verwenden können. Der ganze Quellcode ist enthalten, sodass Sie ihn an Ihre Anforderungen anpassen und Ihre Verbesserungen für die Community freigeben können. Der Code für den C++-Solver wurde in eine UWP-DLL umschlossen und für Unity mit einem Dropdown-Prefab verfügbar gemacht, das [in MixedRealityToolkit enthalten ist.](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)

Im Unity-Beispiel sind viele nützliche Abfragen enthalten, mit denen Sie leere Räume auf Wänden finden, Objekte an der Decke oder auf großen Räumen auf dem Boden platzieren, Orte identifizieren können, an denen Zeichen platziert werden können, und eine Vielzahl anderer Abfragen des räumlichen Verständnisses.

Die von HoloLens bereitgestellte Räumliche Zuordnungslösung ist so konzipiert, dass sie generisch genug ist, um die Anforderungen der gesamten Gamut der Problemräume zu erfüllen. Das Modul spatial understanding wurde jedoch entwickelt, um die Anforderungen von zwei bestimmten Spielen zu unterstützen. Daher ist die Lösung um einen bestimmten Prozess und eine Reihe von Annahmen strukturiert:
* **Playspace mit fester Größe:** Der Benutzer gibt die maximale Playspacegröße im Init-Aufruf an.
* **Einmaliger Überprüfungsprozess:** Der Prozess erfordert eine diskrete Überprüfungsphase, in der der Benutzer den Playspace definiert. Abfragefunktionen funktionieren erst, nachdem der Scan abgeschlossen wurde.
* **Benutzergesteuertes Playspace "Painting":** Während der Überprüfungsphase bewegt sich der Benutzer und sieht sich im Playspace um, um effektiv die Bereiche zu malen, die eingeschlossen werden sollen. Das generierte Gitternetz ist wichtig, um während dieser Phase Benutzerfeedback zu geben.
* **Einrichtung von Heim- oder Bürogebäuden:** Die Abfragefunktionen sind für flache Oberflächen und Wände in rechten Winkeln konzipiert. Dies ist eine weiche Einschränkung. Während der Überprüfungsphase wird jedoch eine Primäre Achsenanalyse abgeschlossen, um das Gitternetz-Mosaik entlang der Haupt- und Nebenachse zu optimieren.

### <a name="room-scanning-process"></a>Raumscanprozess

Wenn Sie das Spatial Understanding-Modul laden, scannen Sie zunächst Ihren Raum, damit alle nutzbaren Oberflächen wie Boden, Decke und Wand identifiziert und bezeichnet werden. Während des Scanvorgangs sehen Sie sich Ihren Raum an und zeichnen die Bereiche, die in die Überprüfung einbezogen werden sollen.

Das Gitternetz, das in dieser Phase zu sehen ist, ist ein wichtiges visuelles Feedback, das Benutzer darüber informiert, welche Teile des Raums gescannt werden. Die DLL für das Spatial Understanding-Modul speichert den Playspace intern als Raster von Voxelcubes mit einer Größe von 8 cm. Während des ersten Teils der Überprüfung wird eine Primäre Komponentenanalyse abgeschlossen, um die Achsen des Raums zu bestimmen. Intern speichert er seinen Voxelraum, der an diesen Achsen ausgerichtet ist. Ein Gitternetz wird ungefähr jede Sekunde generiert, indem die Isosurface aus dem Voxelvolumen extrahiert wird.

![Gitternetz für räumliche Abbildung in Weiß und Grundlegendes zum Playspacegitter in Grün](images/spatial-mapping-500px.png)

Gitternetz für räumliche Abbildung in Weiß und Grundlegendes zum Playspacegitter in Grün



Die enthaltene Datei SpatialUnderstanding.cs verwaltet den Überprüfungsphasenprozess. Sie ruft die folgenden Funktionen auf:
* **SpatialUnderstanding_Init**: Wird zu Beginn einmal aufgerufen.
* **GeneratePlayspace_InitScan**: Gibt an, dass die Überprüfungsphase beginnen soll.
* **GeneratePlayspace_UpdateScan_DynamicScan**: Jeder Frame wird aufgerufen, um den Überprüfungsprozess zu aktualisieren. Die Kameraposition und -ausrichtung wird übergeben und für den oben beschriebenen Playspace-Zeichenprozess verwendet.
* **GeneratePlayspace_RequestFinish**: Wird aufgerufen, um den Playspace zu finalisieren. Dadurch werden die während der Überprüfungsphase "gestrichenen" Bereiche verwendet, um den Playspace zu definieren und zu sperren. Die Anwendung kann Statistiken während der Überprüfungsphase abfragen und das benutzerdefinierte Gitternetz abfragen, um Benutzerfeedback zu geben.
* **Import_UnderstandingMesh**: Während des Scanvorgangs wird das vom Modul bereitgestellte und im grundlegenden Prefab platzierte **SpatialUnderstandingCustomMesh-Verhalten** in regelmäßigen Abständen das vom Prozess generierte benutzerdefinierte Gitternetz abfragen. Darüber hinaus erfolgt dies erneut, nachdem die Überprüfung abgeschlossen wurde.

Der Scanfluss, gesteuert durch das **SpatialUnderstanding-Verhalten,** ruft **InitScan** und dann **UpdateScan für jeden Frame** auf. Wenn die Statistikabfrage eine angemessene Abdeckung meldet, kann der Benutzer airtap aufrufen, um **RequestFinish aufrufen,** um das Ende der Überprüfungsphase anzugeben. **UpdateScan** wird weiterhin aufgerufen, bis der Rückgabewert angibt, dass die DLL die Verarbeitung abgeschlossen hat.

## <a name="the-queries"></a>Die Abfragen

Nachdem die Überprüfung abgeschlossen ist, können Sie auf drei verschiedene Arten von Abfragen in der Schnittstelle zugreifen:
* **Topologieabfragen:** Hierbei handelt es sich um schnelle Abfragen, die auf der Topologie des gescannten Raums basieren.
* **Formabfragen:** Diese verwenden die Ergebnisse Ihrer Topologieabfragen, um horizontale Oberflächen zu finden, die gut zu benutzerdefinierten Formen passen, die Sie definieren.
* **Objektplatzierungsabfragen:** Dies sind komplexere Abfragen, die den am besten passenden Speicherort basierend auf einem Satz von Regeln und Einschränkungen für das Objekt finden.

Zusätzlich zu den drei primären Abfragen gibt es eine Raycastingschnittstelle, die verwendet werden kann, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes wasserdichtes Raumgitternetz kann kopiert werden.

### <a name="topology-queries"></a>Topologieabfragen

Innerhalb der DLL übernimmt der Topologie-Manager die Bezeichnung der Umgebung. Wie bereits erwähnt, werden viele der Daten in Surfel gespeichert, die in einem Voxelvolumen enthalten sind. Darüber hinaus wird die **PlaySpaceInfos-Struktur** verwendet, um Informationen über den Playspace zu speichern, einschließlich der Weltausrichtung (weitere Details dazu unten), des Bodens und der Höhe der Decke.

Heuristiken werden zum Bestimmen von Boden, Decke und Wand verwendet. Beispielsweise wird die größte und niedrigste horizontale Oberfläche mit einer Fläche von mehr als 1 m2 als Boden betrachtet. Beachten Sie, dass der Kamerapfad während des Scanvorgangs auch in diesem Prozess verwendet wird.

Eine Teilmenge der vom Topologie-Manager verfügbar gemachten Abfragen wird über die DLL verfügbar gemacht. Die verfügbar gemachten Topologieabfragen lauten wie folgt:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Jede der Abfragen verfügt über eine Reihe von Parametern, die für den Abfragetyp spezifisch sind. Im folgenden Beispiel gibt der Benutzer die Mindesthöhe & Breite des gewünschten Volumes, die Mindestplatzierungshöhe über dem Boden und die Mindestanzahl von Belägen vor dem Volume an. Alle Messungen werden in Metern durchgeführt.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Jede dieser Abfragen nimmt ein vorab zugeordnetes Array von **TopologyResult-Strukturen** an. Der **locationCount-Parameter** gibt die Länge des übergebenen Arrays an. Der Rückgabewert gibt die Anzahl der zurückgegebenen Speicherorte an. Diese Zahl ist nie größer als der übergebene **locationCount-Parameter.**

Das **TopologyResult** enthält die Mittelpunktposition des zurückgegebenen Volumes, die Ausrichtungsrichtung (d. h. normal) und die Abmessungen des gefundenen Raums.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Beachten Sie, dass im Unity-Beispiel jede dieser Abfragen mit einer Schaltfläche im Bereich der virtuellen Benutzeroberfläche verknüpft ist. Im Beispiel werden die Parameter für jede dieser Abfragen mit angemessenen Werten hartkodiert. Weitere Beispiele finden Sie unter *SpaceVisualizer.cs* im Beispielcode.

### <a name="shape-queries"></a>Formen von Abfragen

Innerhalb der DLL verwendet das Shape-Analyseprogramm (**ShapeAnalyzer_W**) die Topologieanalyse, um mit benutzerdefinierten Formen zu übereinstimmen, die vom Benutzer definiert wurden. Das Unity-Beispiel verfügt über einen vordefinierten Satz von Formen, die im Abfragemenü auf der Registerkarte Form angezeigt werden.

Beachten Sie, dass die Formanalyse nur auf horizontalen Oberflächen funktioniert. Eine Couch wird z. B. durch die flache Seatoberfläche und die flache Oberseite der Couch zurück definiert. Die Shape-Abfrage sucht nach zwei Oberflächen mit einer bestimmten Größe, Höhe und einem bestimmten Seitenbereich, bei denen die beiden Oberflächen ausgerichtet und verbunden sind. Unter Verwendung der APIs-Terminologie sind der Couchplatz und die obere Rückseite der Couch Formkomponenten, und die Ausrichtungsanforderungen sind Einschränkungen für Formkomponenten.

Eine im Unity-Beispiel definierte Beispielabfrage (**ShapeDefinition.cs**) für "sittable"-Objekte lautet wie folgt:




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

Jede Formabfrage wird durch einen Satz von Formkomponenten definiert, die jeweils über eine Reihe von Komponenteneinschränkungen und eine Reihe von Shape-Einschränkungen verfügen, die Abhängigkeiten zwischen den Komponenten auflisten. Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponentendefinition und keine Shape-Einschränkungen zwischen Komponenten (da es nur eine Komponente gibt).

Im Gegensatz dazu verfügt die Form "Couch" über zwei Formkomponenten und vier Formeinschränkungen. Beachten Sie, dass Komponenten durch ihren Index in der Komponentenliste des Benutzers identifiziert werden (in diesem Beispiel 0 und 1).




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Wrapperfunktionen werden im Unity-Modul zur einfachen Erstellung benutzerdefinierter Shape-Definitionen bereitgestellt. Die vollständige Liste der Komponenten- und Formeinschränkungen finden Sie in **SpatialUnderstandingDll.cs** in den **Strukturen ShapeComponentConstraint** und **ShapeConstraint.**

![Das blaue Rechteck hebt die Ergebnisse der Abfrage der Form des Chefs hervor.](images/chair-shape-query-500px.png)

Das blaue Rechteck hebt die Ergebnisse der Abfrage der Form des Chefs hervor.



### <a name="object-placement-solver"></a>Objektplatzierungs-Solver

Objektplatzierungsabfragen können verwendet werden, um ideale Positionen im physischen Raum zu identifizieren, an dem Ihre Objekte gespeichert werden. Der Solver findet die Am besten passende Position, wenn die Objektregeln und Einschränkungen gegeben sind. Darüber hinaus bleiben Objektabfragen bestehen,  bis das Objekt  mit Solver_RemoveObject oder Solver_RemoveAllObjects entfernt wird, wodurch eine eingeschränkte Platzierung mit mehreren Objekten ermöglicht wird.

Objektplatzierungsabfragen bestehen aus drei Teilen: Platzierungstyp mit Parametern, eine Liste von Regeln und eine Liste von Einschränkungen. Verwenden Sie die folgende API, um eine Abfrage auszuführen:




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
Diese Funktion verwendet einen Objektnamen, eine Platzierungsdefinition und eine Liste von Regeln und Einschränkungen. Die C#-Wrapper stellen Konstruktionshilfefunktionen zur Verfügung, um die Regel- und Einschränkungskonstruktion zu einfach zu machen. Die Platzierungsdefinition enthält den Abfragetyp, d.&a; eine der folgenden:




```
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

Jeder Der Platzierungstypen verfügt über einen Satz von Parametern, die für den Typ eindeutig sind. Die **ObjectPlacementDefinition-Struktur** enthält eine Reihe statischer Hilfsfunktionen zum Erstellen dieser Definitionen. Sie können beispielsweise die folgende Funktion verwenden, um einen Ort zu finden, an dem sie ein Objekt auf dem Boden platzieren können: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Zusätzlich zum Platzierungstyp können Sie eine Reihe von Regeln und Einschränkungen bereitstellen. Regeln können nicht verletzt werden. Mögliche Platzierungsstandorte, die den Typ und die Regeln erfüllen, werden dann für den Satz von Einschränkungen optimiert, um den optimalen Platzierungsort auszuwählen. Jede der Regeln und Einschränkungen kann von den bereitgestellten statischen Erstellungsfunktionen erstellt werden. Unten finden Sie eine Beispielregel und eine Einschränkungskonstruktionsfunktion.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

Die folgende Objektplatzierungsabfrage sucht nach einem Ort, an dem sie einen halb meter langen Würfel am Rand einer Oberfläche platzieren kann, weg von anderen zuvor platzierenden Objekten und in der Nähe der Mitte des Raumes.




```
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

Bei Erfolg wird eine **ObjectPlacementResult-Struktur** zurückgegeben, die position, dimensions und orientation enthält. Darüber hinaus wird die Platzierung der internen Dll-Liste platzierter Objekte hinzugefügt. Bei nachfolgenden Platzierungsabfragen wird dieses Objekt berücksichtigt. Die **Datei LevelSolver.cs** im Unity-Beispiel enthält weitere Beispielabfragen.

![Die blauen Felder zeigen das Ergebnis von drei "Place On Floor"-Abfragen mit Regeln für "Weg von der Kameraposition".](images/away-from-camera-position-500px.png)

Die blauen Felder zeigen das Ergebnis von drei "Place On Floor"-Abfragen mit Regeln für "Weg von der Kameraposition".


**Tipps:**
* Wenn Sie die Platzierungsposition mehrerer Objekte lösen, die für ein Ebenen- oder Anwendungsszenario erforderlich sind, lösen Sie zuerst Dies ist eine Lösung für große objekte, um die Wahrscheinlichkeit zu maximieren, dass ein Raum gefunden werden kann.
* Die Platzierungs reihenfolge ist wichtig. Wenn Objektplatzierungen nicht gefunden werden können, versuchen Sie weniger eingeschränkte Konfigurationen. Eine Reihe von Fallbackkonfigurationen ist entscheidend für die Unterstützung von Funktionen für viele Raumkonfigurationen.

### <a name="ray-casting"></a>Raycasting

Zusätzlich zu den drei primären Abfragen kann eine Raycastschnittstelle verwendet werden, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes wasserdichtes Playspacenetz kann kopiert werden. Nachdem der Raum gescannt und abgeschlossen wurde, werden Bezeichnungen intern für Oberflächen wie Boden, Decke und Wand generiert. Die **PlayspaceRaycast-Funktion** nimmt einen Strahl und gibt zurück, wenn der Strahl mit einer bekannten Oberfläche kollidiert, und wenn ja, Informationen über diese Oberfläche in Form eines **RaycastResult.** 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

Intern wird der Raycast anhand der berechneten 8cm-Voxeldarstellung des Playspace berechnet. Jedes Voxel enthält eine Reihe von Oberflächenelementen mit verarbeiteten Topologiedaten (auch bekannt als Surfel). Die in der überschneidenden Voxelzelle enthaltenen Surfel werden verglichen, und die beste Übereinstimmung wird zum Suchen der Topologieinformationen verwendet. Diese Topologiedaten enthalten die Bezeichnungen, die in Form der **SurfaceTypes-Enumeration** zurückgegeben werden, sowie den Oberflächenbereich der überschneidenden Oberfläche.

Im Unity-Beispiel wirft der Cursor einen Strahl in jeden Frame. Zuerst gegen die Collider von Unity. zweitens, gegen die Weltdarstellung des Understanding-Moduls; und schließlich für die Benutzeroberflächenelemente. In dieser Anwendung erhält die Benutzeroberfläche Priorität, dann das Verstehen des Ergebnisses und schließlich die Collider von Unity. SurfaceType **wird** als Text neben dem Cursor gemeldet.

![Raycastergebnisberichts-Schnittmenge mit dem Boden.](images/raycast-result-500px.jpg)

Raycastergebnisberichts-Schnittmenge mit dem Boden.


## <a name="get-the-code"></a>Abrufen des Codes

Der Open-Source-Code ist im [MixedRealityToolkit verfügbar.](https://github.com/Microsoft/MixedRealityToolkit-Unity) Teilen Sie uns dies in HoloLens [Entwicklerforen mit,](https://forums.hololens.com/) wenn Sie den Code in einem Projekt verwenden. Wir können nicht warten, um zu sehen, was Sie damit tun!

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt ist</b> ein Software Engineering-Lead, der seit HoloLens von der Inkubation bis zur Entwicklungserfahrung an HoloLens gearbeitet hat. Bevor HoloLens, hat er an der Xbox Kinect und in der Spielebranche auf einer Vielzahl von Plattformen und Spielen gearbeitet. Jeff ist sehr an Derktik, Grafiken und Dingen mit blinkenden Lichtbuckeln geerbt. Er lernt gerne neue Dinge und arbeitet an Software, Hardware und insbesondere an dem Bereich, in dem sich die beiden überschneiden.</td>
</tr>
</table>



## <a name="see-also"></a>Siehe auch
* [Räumliche Abbildung](../design/spatial-mapping.md)
* [Grundlegendes zu Szenen](../design/scene-understanding.md)
* [Raumabtastvisualisierung](../design/room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: Lektionen aus der Frontline HoloLens Entwicklung](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
