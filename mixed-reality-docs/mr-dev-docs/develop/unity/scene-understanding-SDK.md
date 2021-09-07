---
title: Scene understanding SDK
description: Erfahren Sie, wie Sie das Scene Understanding SDK installieren und verwenden, einschließlich Komponenten, Gitternetzen und Objekten in Mixed Reality-Apps.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Scene Understanding, Spatial Mapping, Windows Mixed Reality, Unity
ms.openlocfilehash: d7547e1517583e3822a9ac9b54cbf0557cd7780c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2021
ms.locfileid: "123246299"
---
# <a name="scene-understanding-sdk-overview"></a>Übersicht über das Scene Understanding SDK

Scene Understanding transformiert die Sensordaten der unstrukturierten Umgebung, die ihr Mixed Reality Gerät erfasst und in eine leistungsfähige abstrakte Darstellung umwandelt. Das SDK fungiert als Kommunikationsschicht zwischen Ihrer Anwendung und der Scene Understanding-Runtime. Es soll vorhandene Standardkonstrukte imitieren, z. B. 3D-Szenendiagramme für 3D-Darstellungen und 2D-Rechtecke und -Bereiche für 2D-Anwendungen. Während die Scene Understanding-Konstrukte konkreten Frameworks zugeordnet werden, ist SceneUnderstanding im Allgemeinen frameworkunabhängig und ermöglicht die Interoperabilität zwischen verschiedenen Frameworks, die damit interagieren. Mit der Weiterentwicklung von Scene Understanding besteht die Rolle des SDK darin, sicherzustellen, dass neue Darstellungen und Funktionen innerhalb eines einheitlichen Frameworks weiterhin verfügbar gemacht werden. In diesem Dokument werden zunächst konzepte auf hoher Ebene vorgestellt, die Ihnen helfen, sich mit der Entwicklungsumgebung/-verwendung vertraut zu machen und dann eine ausführlichere Dokumentation für bestimmte Klassen und Konstrukte bereitzustellen.

## <a name="where-do-i-get-the-sdk"></a>Wo erhalte ich das SDK?

Das SceneUnderstanding SDK kann über das [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md)heruntergeladen werden.
<!--Unity Note-->
**Hinweis:** Die neueste Version hängt von Vorschaupaketen ab, und Sie müssen Vorabversionspakete aktivieren, um sie anzuzeigen.

Für Version 0.5.2022-rc und höher unterstützt Scene Understanding Sprachprojektionen für C# und C++, sodass Anwendungen Anwendungen für Win32- oder UWP-Plattformen entwickeln können. Ab dieser Version unterstützt SceneUnderstanding die Unity-Unterstützung im Editor, die den SceneObserver nicht mehr unterstützt, der ausschließlich für die Kommunikation mit HoloLens2 verwendet wird. 
<!-- Unity Note: Since C++ is mentioned, it's not strictly Unity. Not sure about the C#. -->
SceneUnderstanding erfordert Windows SDK Version 18362 oder höher. 

## <a name="conceptual-overview"></a>Konzeptionelle Übersicht

### <a name="the-scene"></a>Die Szene

Ihr Mixed Reality-Gerät integriert ständig Informationen darüber, was es in Ihrer Umgebung sieht. Scene Understanding trichtert alle diese Datenquellen und erzeugt eine einzelne kohäsive Abstraktion. Scene Understanding generiert Szenen, bei denen es sich um eine Komposition von [SceneObjects](scene-understanding-SDK.md#sceneobjects) handelt, die eine Instanz eines einzelnen Objekts darstellen (z. B. eine Wand/Hänge/Etage). Szenenobjekte selbst sind eine Komposition von [SceneComponents), die präzisere Teile darstellen, aus denen dieses SceneObject besteht. Beispiele für Komponenten sind Quads und Gitternetze, aber in Zukunft könnten Begrenzungsfelder, Kollisionsgitternetze, Metadaten usw. dargestellt werden.

Der Prozess der Konvertierung der rohen Sensordaten in eine Szene ist ein potenziell kostspieliger Vorgang, der bei großen Bereichen (~50 x 50 m) sekundenlang dauern kann (~10 x 10 m) und daher nicht vom Gerät ohne Anwendungsanforderung berechnet wird. Stattdessen wird die Szenengenerierung bei Bedarf von Ihrer Anwendung ausgelöst. Die SceneObserver-Klasse verfügt über statische Methoden, die eine Szene berechnen oder deserialisieren können, mit denen Sie dann aufzählen/interagieren können. Die Computeaktion wird bei Bedarf ausgeführt und auf der CPU, jedoch in einem separaten Prozess (der Mixed Reality Driver) ausgeführt. Während wir jedoch in einem anderen Prozess berechnen, werden die resultierenden Szenendaten in Ihrer Anwendung im Scene-Objekt gespeichert und verwaltet. 

Im Folgenden finden Sie ein Diagramm, das diesen Prozessfluss veranschaulicht und Beispiele für zwei Anwendungen zeigt, die mit der Scene Understanding-Runtime verbunden sind. 

![Prozessdiagramm](images/SU-ProcessFlow.png)

Auf der linken Seite befindet sich ein Diagramm der Mixed Reality-Runtime, die immer aktiv ist und in einem eigenen Prozess ausgeführt wird. Diese Runtime ist für die Ausführung von Gerätenachverfolgung, räumlicher Zuordnung und anderen Vorgängen verantwortlich, die Scene Understanding verwendet, um die Welt um Sie herum zu verstehen und zu verstehen. Auf der rechten Seite des Diagramms werden zwei theoretische Anwendungen gezeigt, die Scene Understanding nutzen. Die ersten Anwendungsschnittstellen mit MRTK<!--Unity Note-->, das das Scene Understanding SDK intern verwendet, berechnet die zweite App und verwendet zwei separate Szeneninstanzen. Alle drei Szenen in diesem Diagramm generieren unterschiedliche Instanzen der Szenen. Der Treiber verfolgt den globalen Zustand, der von Anwendungen gemeinsam genutzt wird, und Szenenobjekte in einer Szene nicht in einer anderen Szene. Scene Understanding bietet einen Mechanismus zum Nachverfolgen im Laufe der Zeit, aber dies erfolgt mithilfe des SDK. Der Nachverfolgungscode wird bereits im SDK im Prozess Ihrer App ausgeführt.

Da jede Szene ihre Daten im Arbeitsspeicher Ihrer Anwendung speichert, können Sie davon ausgehen, dass alle Funktionen des Scene-Objekts oder seine internen Daten immer im Prozess Ihrer Anwendung ausgeführt werden.

### <a name="layout"></a>Layout

Für die Arbeit mit Scene Understanding kann es hilfreich sein, zu wissen und zu verstehen, wie die Laufzeit Komponenten logisch und physisch darstellt. Die Szene stellt Daten mit einem bestimmten Layout dar, das als einfach ausgewählt wurde, während eine zugrunde liegende Struktur beibehalten wird, die zukünftige Anforderungen erfüllen kann, ohne dass größere Revisionen erforderlich sind. Die Szene speichert dazu alle Komponenten (Bausteine für alle Szenenobjekte) in einer flachen Liste und definiert Hierarchie und Komposition über Verweise, in denen bestimmte Komponenten auf andere verweisen.

Unten sehen Sie ein Beispiel für eine Struktur in ihrer flachen und logischen Form.

<table>
<tr><th>Logisches Layout</th><th>Physisches Layout</th></tr>
<tr>
<td>
<ul>
  Szene
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

In dieser Abbildung wird der Unterschied zwischen dem physischen und logischen Layout der Szene hervorgehoben. Auf der linken Seite sehen wir das hierarchische Layout der Daten, die Ihrer Anwendung beim Aufzählen der Szene angezeigt werden. Auf der rechten Seite sehen wir, dass die Szene aus 12 unterschiedlichen Komponenten besteht, auf die bei Bedarf einzeln zugegriffen werden kann. Bei der Verarbeitung einer neuen Szene erwarten wir, dass Anwendungen diese Hierarchie logisch durchgehen. Bei der Nachverfolgung zwischen Szenenupdates sind einige Anwendungen jedoch möglicherweise nur an bestimmten Komponenten interessiert, die von zwei Szenen gemeinsam genutzt werden.

## <a name="api-overview"></a>API-Übersicht

Der folgende Abschnitt bietet eine allgemeine Übersicht über die Konstrukte in Scene Understanding. In diesem Abschnitt erfahren Sie, wie Szenen dargestellt werden und wofür die verschiedenen Komponenten verwendet werden. Der nächste Abschnitt enthält konkrete Codebeispiele und zusätzliche Details, die in dieser Übersicht erläutert werden.

Alle unten beschriebenen Typen befinden sich im `Microsoft.MixedReality.SceneUnderstanding` -Namespace.

### <a name="scenecomponents"></a>SceneComponents

Nachdem Sie nun das logische Layout von Szenen verstanden haben, können wir das Konzept von SceneComponents und deren Verwendung zur Erstellung von Hierarchien vorstellen. SceneComponents sind die präzisesten Zerlegungen in SceneUnderstanding, die einen einzelnen Kern darstellen, z. B. ein Gitternetz oder ein Quader oder ein Begrenzungsfeld. SceneComponents sind Dinge, die unabhängig aktualisiert werden können und von anderen SceneComponents referenziert werden können. Daher verfügen sie über eine einzelne globale Eigenschaft, eine eindeutige ID, die diesen Typ von Nachverfolgungs-/Verweismechanismus ermöglicht. IDs werden für die logische Zusammensetzung der Szenenhierarchie und objektpersistenz (das Aktualisieren einer Szene relativ zu einer anderen) verwendet.

Wenn Sie jede neu berechnete Szene als eindeutig behandeln und einfach alle darin enthaltenen Daten aufzählen, sind IDs für Sie weitgehend transparent. Wenn Sie jedoch planen, Komponenten über mehrere Updates nachzuverfolgen, verwenden Sie die IDs, um SceneComponents zwischen Szenenobjekten zu indizieren und zu suchen.

### <a name="sceneobjects"></a>SceneObjects

Ein SceneObject ist ein SceneComponent, das eine Instanz eines "Dings" darstellt, z. B. eine Wand, einen Boden, eine Obergrenze usw. ausgedrückt durch die Kind-Eigenschaft. SceneObjects sind geometrisch und verfügen daher über Funktionen und Eigenschaften, die ihre Position im Raum darstellen, jedoch keine geometrische oder logische Struktur enthalten. Stattdessen verweisen SceneObjects auf andere SceneComponents, insbesondere SceneQuads und SceneMeshes, die die verschiedenen Darstellungen bereitstellen, die vom System unterstützt werden. Wenn eine neue Szene berechnet wird, zählt Ihre Anwendung höchstwahrscheinlich die SceneObjects der Szene auf, um das zu verarbeiten, was sie interessiert.

SceneObjects kann eine der folgenden Funktionen aufweisen:

<table>
<tr>
<th>SceneObjectKind</th> <th>BESCHREIBUNG</th>
</tr>
<tr><td>Hintergrund</td><td>Das SceneObject ist bekannt dafür, dass es <b>sich nicht</b> um eine der anderen erkannten Arten von Szenenobjekten handelt. Diese Klasse sollte nicht mit Unknown verwechselt werden, wobei Background bekanntermaßen nicht "Wall", "Floor", "ceiling" usw. ist. während unbekannt noch nicht kategorisiert ist.</b></td></tr>
<tr><td>Wall</td><td>Eine physische Wand. Es wird davon ausgegangen, dass es sich bei den Wänden um wähnbare Umgebungsstrukturen handelt.</td></tr>
<tr><td>Etage</td><td>Etagen sind alle Oberflächen, auf denen sie begehbar sind. Hinweis: Es handelt sich nicht um Etagen. Beachten Sie auch, dass Die Etagen eine beliebige begehbare Oberfläche annehmen und daher keine explizite Annahme einer einzelnen Etage besteht. Strukturen auf mehreren Ebenen, Rampen usw.... sollte alle als Floor klassifiziert werden.</td></tr>
<tr><td>Ceiling</td><td>Die obere Oberfläche eines Raumes.</td></tr>
<tr><td>Plattform</td><td>Eine große flache Oberfläche, auf der Sie Hologramme platzieren können. Diese stellen tendenziell Tabellen, Gegenspitzen und andere große horizontale Oberflächen dar.</td></tr>
<tr><td>World</td><td>Eine reservierte Bezeichnung für geometrische Daten, die nicht beschriftungsunabhängig ist. Das Gitternetz, das durch Festlegen des EnableWorldMesh-Updateflags generiert wird, wird als World klassifiziert.</td></tr>
<tr><td>Unknown</td><td>Dieses Szenenobjekt muss noch klassifiziert und einer Art zugewiesen werden. Dies sollte nicht mit Background verwechselt werden, da dieses Objekt etwas sein könnte, das System hat einfach noch keine stark genug Klassifizierung dafür erstellt.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

Ein SceneMesh ist eine SceneComponent, die der Geometrie beliebiger geometrischer Objekte mithilfe einer Dreiecksliste ungefährt. SceneMeshes werden in verschiedenen Kontexten verwendet. sie können Komponenten der wasserdichten Zellenstruktur oder als WorldMesh darstellen, das das der Szene zugeordnete Gitternetz für die ungebundene räumliche Abbildung darstellt. Die index- und vertex-Daten, die mit jedem Gitternetz bereitgestellt werden, verwenden das gleiche vertraute Layout wie die Scheitelpunkt- und Indexpuffer, die zum Rendern von [Dreiecksgittern](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) in allen modernen Rendering-APIs verwendet werden. In Scene Understanding verwenden Gitternetze 32-Bit-Indizes und müssen möglicherweise für bestimmte Rendering-Engines in Brüche zerlegt werden.

#### <a name="winding-order-and-coordinate-systems"></a>Wickelrichtungs- und Koordinatensysteme

Von allen Gittern, die von Scene Understanding erzeugt werden, wird erwartet, dass sie Gitternetze in einem Right-Handed Koordinatensystem mit der Wickelrichtung im Uhrzeigersinn zurückgeben. 

Hinweis: Betriebssystem-Builds vor .191105 weisen möglicherweise einen bekannten Fehler auf, bei dem "World"-Gitternetze in einer Counter-Clockwise-Wickelrichtung zurückgeben, die anschließend behoben wurde.

### <a name="scenequad"></a>SceneQuad

Ein SceneQuad ist eine SceneComponent, die 2d-Oberflächen darstellt, die die 3D-Welt einnehmen. SceneQuads können ähnlich wie ARKit ARPlaneAnchor- oder ARCore-Ebenen verwendet werden, bieten jedoch eine erweiterte Funktionalität als 2D-Canvases, die von flachen Apps oder erweiterter UX verwendet werden können. 2D-spezifische APIs werden für Quads bereitgestellt, die die Platzierung und das Layout einfach zu verwenden machen, und die Entwicklung (mit Ausnahme des Renderings) mit Quads sollte sich eher der Arbeit mit 2d-Canvases als 3D-Gittern anfühlen.

#### <a name="scenequad-shape"></a>SceneQuad-Form

SceneQuads definieren eine begrenzungsbegrenzete rechteckige Oberfläche in 2d. SceneQuads stehen jedoch für Oberflächen mit beliebigen und potenziell komplexen Formen (z. B. einer donutförmigen Tabelle). Um die komplexe Form der Oberfläche eines Quads zu darstellen, können Sie die GetSurfaceMask-API verwenden, um die Form der Oberfläche in einem von Ihnen bereitgestellten Bildpuffer zu rendern. Wenn das SceneObject, das über das Quad verfügt, auch über ein Gitternetz verfügt, sollten die Gitterdreiecke diesem gerenderten Bild entsprechen. Beide stellen eine echte Geometrie der Oberfläche dar, entweder in 2d- oder 3d-Koordinaten.

## <a name="scene-understanding-sdk-details-and-reference"></a>Scene understanding SDK details and reference (Szenenverständnis der SDK-Details und Referenz)

> [!NOTE] 
> <!--Unity Note-->Beachten Sie bei der Verwendung des MRTK, dass Sie mit MRTK interagieren und daher diesen Abschnitt in den [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) meisten Fällen überspringen können. Weitere Informationen finden Sie in der [DOKUMENTATION zu MRTK Scene Understanding.](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding)

Der folgende Abschnitt hilft Ihnen, sich mit den Grundlagen von SceneUnderstanding vertraut zu machen. In diesem Abschnitt sollten die Grundlagen beschrieben werden. An diesem Punkt sollten Sie über genügend Kontext verfügen, um die Beispielanwendungen zu durchsuchen und zu sehen, wie SceneUnderstanding holistisch verwendet wird.

### <a name="initialization"></a>Initialisierung

Der erste Schritt bei der Arbeit mit SceneUnderstanding ist, dass Ihre Anwendung auf ein Szenenobjekt verweist. Dies kann auf zwei Arten erfolgen: Eine Szene kann entweder vom Treiber berechnet werden, oder eine vorhandene Szene, die in der Vergangenheit berechnet wurde, kann deseriiert werden. Letzteres ist nützlich für die Arbeit mit SceneUnderstanding während der Entwicklung, bei der Anwendungen und Erfahrungen ohne Mixed Reality-Gerät schnell prototypiert werden können.

Szenen werden mithilfe eines SceneObservers berechnet. Vor dem Erstellen einer Szene sollte Ihre Anwendung Ihr Gerät abfragen, um sicherzustellen, dass es SceneUnderstanding unterstützt, und Benutzerzugriff für Informationen anfordern, die SceneUnderstanding benötigt.
<!--Unity Note-->
```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Wenn RequestAccessAsync() nicht aufgerufen wird, wird beim Berechnen einer neuen Szene ein Fehler ausgelöst. Als Nächstes berechnen wir eine neue Szene, die auf dem Mixed Reality Headset basiert und einen Radius von 10 Metern hat.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>Initialisierung aus Daten (auch als bezeichnet). PC-Pfad)

Obwohl Szenen für den direkten Verbrauch berechnet werden können, können sie auch zur späteren Verwendung in serialisierter Form berechnet werden. Dies hat sich als nützlich für die Entwicklung erwiesen, da Entwickler damit in Scene Understanding arbeiten und testen können, ohne dass ein Gerät benötigt wird. Das Serialisieren einer Szene ist nahezu identisch mit der Berechnung. Die Daten werden an Ihre Anwendung zurückgegeben, anstatt lokal vom SDK deserialisiert zu werden. Sie können sie dann selbst deserialisieren oder zur zukünftigen Verwendung speichern.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a>SceneObject-Enumeration

Nachdem Ihre Anwendung nun über eine Szene verfügt, betrachtet ihre Anwendung SceneObjects und interagiert damit. Dies erfolgt durch Zugriff auf die **SceneObjects-Eigenschaft:**

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a>Komponentenupdate und -neufinden von Komponenten

Es gibt eine weitere Funktion, die Komponenten in der Szene mit dem Namen ***FindComponent abruft.*** Diese Funktion ist nützlich, wenn Sie Nachverfolgungsobjekte aktualisieren und in späteren Szenen suchen. Der folgende Code berechnet eine neue Szene relativ zu einer vorherigen Szene und findet dann den Boden in der neuen Szene.

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>Zugreifen auf Gitter und Quader von Szenenobjekten

Sobald SceneObjects gefunden wurde, möchte Ihre Anwendung höchstwahrscheinlich auf die Daten zugreifen, die in den Quads/Meshes enthalten sind, aus denen sie besteht. Auf diese Daten wird mit den Eigenschaften ***Quads** _ und _ *_Meshes_** zugegriffen. Mit dem folgenden Code werden alle Quads und Gitter des Bodenobjekts aufzählt.

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

Beachten Sie, dass es das SceneObject ist, das über die Transformation verfügt, die relativ zum Ursprung der Szene ist. Dies liegt daran, dass das SceneObject eine Instanz eines "Objekts" darstellt und im Raum verwendbar ist, die Quads und Gitternetze die Geometrie darstellen, die relativ zu ihrem übergeordneten Element transformiert wird. Es ist möglich, dass separate SceneObjects auf die gleichen SceneMesh/SceneQuad SceneComponents verweisen, und es ist auch möglich, dass ein SceneObject über mehr als ein SceneMesh/SceneQuad verfügt.

### <a name="dealing-with-transforms"></a>Umgang mit Transformationen

Scene Understanding hat beim Umgang mit Transformationen bewusst versucht, sich an herkömmlichen 3D-Szenendarstellungen auszurichten. Jede Szene ist daher ähnlich wie die gängigsten 3D-Umgebungsdarstellungen auf ein einzelnes Koordinatensystem beschränkt. SceneObjects stellen jeweils ihre Position relativ zu diesem Koordinatensystem zur Verfügung. Wenn Ihre Anwendung Szenen verwendet, die den Grenzwert eines einzelnen Ursprungs überschreiten, kann sie SceneObjects in SpatialAnchors verankern oder mehrere Szenen generieren und zusammenführen. Der Einfachheit halber wird jedoch davon ausgegangen, dass wasserdichte Szenen in ihrem eigenen Ursprung vorhanden sind, der durch eine durch Scene.OriginSpatialGraphNodeId definierte NodeId lokalisiert wird.
<!--Unity Note-->
Der folgende Unity-Code zeigt beispielsweise, wie Sie Windows Perception- und Unity-APIs verwenden, um Koordinatensysteme zusammen auszurichten. Unter [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) und [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) finden Sie Details zu den Windows Perception-APIs und Mixed Reality native Objekte [in Unity,](/windows/mixed-reality/unity-xrdevice-advanced) um Details zum Abrufen eines SpatialCoordinateSystem zu erhalten, das dem Ursprung der Welt von Unity entspricht.

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

Jede `SceneObject` verfügt über eine Transformation, die dann auf dieses Objekt angewendet wird. In Unity konvertieren wir in rechtshändige Koordinaten und weisen lokale Transformationen wie hier zu:

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a>Viereck

Quads wurden entwickelt, um 2D-Platzierungsszenarien zu unterstützen, und sollten als Erweiterungen für 2D-Canvas-UX-Elemente gedacht werden. Während Quads Komponenten von SceneObjects sind und in 3D gerendert werden können, gehen die Quad-APIs selbst davon aus, dass Quads 2D-Strukturen sind. Sie bieten Informationen wie Umfang, Form und APIs für die Platzierung.

Quads verfügen über rechteckige Blöcke, stellen jedoch beliebig förmige 2D-Oberflächen dar. Um die Platzierung auf diesen 2D-Oberflächen zu ermöglichen, die mit den 3D-Umgebungs-Quads interagieren, bieten Hilfsprogramme, um diese Interaktion zu ermöglichen. Derzeit bietet Scene Understanding zwei solche Funktionen: **FindCentermostPlacement** und **GetSurfaceMask.** FindCentermostPlacement ist eine api auf hoher Ebene, die eine Position auf dem Quader findet, an der ein Objekt platziert werden kann, und versucht, die beste Position für Ihr Objekt zu finden, um sicherzustellen, dass das von Ihnen bereitgestellte Begrenzungsfeld auf der zugrunde liegenden Oberfläche bleibt.

> [!NOTE]
> Die Koordinaten der Ausgabe sind relativ zum Quad im "Quad-Bereich", bei dem die obere linke Ecke (x = 0, y = 0) ist, wie es bei anderen Fenster-Rect-Typen der Wäre. Berücksichtigen Sie dies unbedingt, wenn Sie mit den Ursprüngen Ihrer eigenen Objekte arbeiten. 

Das folgende Beispiel zeigt, wie Sie die zentriertste positionierbare Position finden und ein Hologramm am Quader verankern.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

Die Schritte 1 bis 4 hängen stark von Ihrem jeweiligen Framework bzw. Ihrer Implementierung ab, die Designs sollten jedoch ähnlich sein. Beachten Sie, dass das Quad einfach eine 2D-Begrenzungsebene darstellt, die im Raum lokalisiert ist. Wenn Ihre Engine/Ihr Framework weiß, wo sich das Quad befindet, und Ihre Objekte relativ zum Quader rooten, werden Ihre Hologramme im Hinblick auf die reale Welt korrekt gefunden. 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>Mesh

Gitternetze stellen geometrische Darstellungen von Objekten oder Umgebungen dar. Ähnlich [wie](../../design/spatial-mapping.md)bei der räumlichen Zuordnung verwenden Gitternetzindex- und Vertexdaten, die mit jedem Gitternetz für räumliche Oberflächen bereitgestellt werden, das gleiche vertraute Layout wie die Scheitelpunkt- und Indexpuffer, die zum Rendern von Dreiecksgittern in allen modernen Rendering-APIs verwendet werden. Scheitelpunktpositionen werden im Koordinatensystem von `Scene` bereitgestellt. Die spezifischen APIs, die verwendet werden, um auf diese Daten zu verweisen, lauten wie folgt:

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

Der folgende Code enthält ein Beispiel für das Generieren einer Dreiecksliste aus der Gitternetzstruktur:

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

Die Index-/Scheitelpunktpuffer müssen >= Index-/Scheitelpunktanzahl angegeben werden. Andernfalls können sie beliebig dimensioniert werden, um eine effiziente Speicherwiederverwendung zu ermöglichen.

### <a name="collidermesh"></a>ColliderMesh

Szenenobjekte ermöglichen den Zugriff auf Gitter- und Collidermeshdaten über die Eigenschaften Meshes und ColliderMeshes. Diese Gitternetze werden immer übereinstimmen, was bedeutet, dass der i'th-Index der Meshes-Eigenschaft die gleiche Geometrie wie der i'th-Index der ColliderMeshes-Eigenschaft darstellt. Wenn die Laufzeit bzw. das Objekt Collidergitter unterstützt, erhalten Sie garantiert das niedrigste Polygon und die höchste Näherung, und es ist eine bewährte Methode, ColliderMeshes überall dort zu verwenden, wo Ihre Anwendung Collider verwenden würde. Wenn das System keine Collider unterstützt, ist das in ColliderMeshes zurückgegebene Mesh-Objekt dasselbe Objekt wie das Gittermodell, das Arbeitsspeichereinschränkungen reduziert.

## <a name="developing-with-scene-understanding"></a>Entwickeln mit Szenenverständnis

An diesem Punkt sollten Sie die Kernbausteine der Szene verstehen, die Runtime und SDK verstehen. Der Großteil der Leistung und Komplexität liegt in Zugriffsmustern, der Interaktion mit 3D-Frameworks und Tools, die auf diesen APIs geschrieben werden können, um komplexere Aufgaben wie räumliche Planung, Raumanalyse, Navigation, Physik und so weiter auszuführen. Wir hoffen, diese in Beispielen erfassen zu können, die Sie hoffentlich in die richtige Richtung führen sollten, um Ihre Szenarien ins Leben zu bringen. Wenn es Beispiele oder Szenarien gibt, die wir nicht adressieren, teilen Sie uns dies mit, und wir versuchen, zu dokumentieren, was Sie benötigen.

### <a name="where-can-i-get-sample-code"></a>Wo kann ich Beispielcode erhalten?
<!--Unity Note-->
Scene Understanding-Beispielcode für Unity finden Sie auf unserer [Unity-Beispielseite.](https://github.com/sceneunderstanding-microsoft/unitysample) Mit dieser Anwendung können Sie mit Ihrem Gerät kommunizieren und die verschiedenen Szenenobjekte rendern, oder Sie können eine serialisierte Szene auf Ihrem PC laden und Scene Understanding ohne Gerät erleben.

### <a name="where-can-i-get-sample-scenes"></a>Wo erhalte ich Beispielszenen?

Wenn Sie über eine HoloLens2 verfügen, können Sie jede erfasste Szene speichern, indem Sie die Ausgabe von ComputeSerializedAsync in einer Datei speichern und sie nach Belieben deserialisieren. 

Wenn Sie nicht über ein HoloLens2-Gerät verfügen, aber mit Scene Understanding spielen möchten, müssen Sie eine vorab erfasste Szene herunterladen. Das Scene Understanding-Beispiel enthält derzeit serialisierte Szenen, die heruntergeladen und nach Belieben verwendet werden können. Sie finden sie hier:

[Scene Understanding-Beispielszenen](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>Siehe auch

* [Räumliche Abbildung](../../design/spatial-mapping.md)
* [Grundlegendes zu Szenen](../../design/scene-understanding.md)
* [Unity-Beispiel](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)