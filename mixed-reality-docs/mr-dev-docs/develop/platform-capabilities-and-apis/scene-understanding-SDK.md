---
title: Scene understanding SDK
description: Erfahren Sie, wie Sie das Scene Understanding SDK installieren und verwenden, einschließlich Komponenten, Gitternetzen und Objekten in Mixed Reality-Apps.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Scene Understanding, Spatial Mapping, Windows Mixed Reality, Unity
ms.openlocfilehash: dee561e49a9457aa35c44037f4573caaefd00f2a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449729"
---
# <a name="scene-understanding-sdk-overview"></a>Übersicht über das Scene Understanding SDK

Scene Understanding transformiert die Sensordaten der unstrukturierten Umgebung, die ihr Mixed Reality Gerät erfasst und in eine leistungsfähige abstrakte Darstellung umwandelt. Das SDK fungiert als Kommunikationsschicht zwischen Ihrer Anwendung und der Scene Understanding-Runtime. Es soll vorhandene Standardkonstrukte imitieren, z. B. 3D-Szenendiagramme für 3D-Darstellungen und 2D-Rechtecke und -Bereiche für 2D-Anwendungen. Während die Scene Understanding-Konstrukte konkreten Frameworks zugeordnet werden, ist SceneUnderstanding im Allgemeinen frameworkunabhängig und ermöglicht die Interoperabilität zwischen verschiedenen Frameworks, die damit interagieren. Mit der Weiterentwicklung von Scene Understanding besteht die Rolle des SDK darin, sicherzustellen, dass neue Darstellungen und Funktionen in einem einheitlichen Framework weiterhin verfügbar gemacht werden. In diesem Dokument werden zunächst konzepte auf hoher Ebene vorgestellt, die Ihnen helfen, sich mit der Entwicklungsumgebung/-verwendung vertraut zu machen und dann eine ausführlichere Dokumentation für bestimmte Klassen und Konstrukte bereitzustellen.

## <a name="where-do-i-get-the-sdk"></a>Wo erhalte ich das SDK?

Das SceneUnderstanding SDK kann über das [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md)heruntergeladen werden.

**Hinweis:** Die neueste Version hängt von Vorschaupaketen ab, und Sie müssen Vorabversionspakete aktivieren, um sie anzuzeigen.

Für Version 0.5.2022-rc und höher unterstützt Scene Understanding Sprachprojektionen für C# und C++, sodass Anwendungen Anwendungen für Win32- oder UWP-Plattformen entwickeln können. Ab dieser Version unterstützt SceneUnderstanding die Unity-Unterstützung im Editor, die den SceneObserver aussperrt, der ausschließlich für die Kommunikation mit HoloLens2 verwendet wird. 

SceneUnderstanding erfordert Windows SDK Version 18362 oder höher. 

## <a name="conceptual-overview"></a>Konzeptionelle Übersicht

### <a name="the-scene"></a>Die Szene

Ihr Mixed Reality-Gerät integriert ständig Informationen darüber, was es in Ihrer Umgebung sieht. Scene Understanding trichtert alle diese Datenquellen und erzeugt eine einzelne kohäsive Abstraktion. Scene Understanding generiert Szenen, bei denen es sich um eine Komposition von [SceneObjects](scene-understanding-SDK.md#sceneobjects) handelt, die eine Instanz eines einzelnen Objekts darstellen (z. B. eine Wand/Hänge/Etage). Szenenobjekte selbst sind eine Komposition von [SceneComponents), die präzisere Teile darstellen, aus denen dieses SceneObject besteht. Beispiele für Komponenten sind Quads und Gitternetze, aber in Zukunft könnten Begrenzungsfelder, Kollisionsgitternetze, Metadaten usw. dargestellt werden.

Der Prozess der Konvertierung der rohen Sensordaten in eine Szene ist ein potenziell kostspieliger Vorgang, der bei großen Bereichen (~50 x 50 m) sekundenlang dauern kann (~10 x 10 m) und daher nicht vom Gerät ohne Anwendungsanforderung berechnet wird. Stattdessen wird die Szenengenerierung von Ihrer Anwendung bei Bedarf ausgelöst. Die SceneObserver-Klasse verfügt über statische Methoden, die eine Szene berechnen oder deserialisieren können, mit denen Sie dann aufzählen/interagieren können. Die Aktion "Compute" wird bei Bedarf ausgeführt und auf der CPU ausgeführt, jedoch in einem separaten Prozess (der Mixed Reality-Treiber). Während wir jedoch Compute in einem anderen Prozess durchführen, werden die resultierenden Szenendaten in Ihrer Anwendung im Scene-Objekt gespeichert und verwaltet. 

Im Folgenden finden Sie ein Diagramm, das diesen Prozessfluss veranschaulicht und Beispiele für zwei Anwendungen zeigt, die mit der Scene Understanding-Runtime verbunden sind. 

![Prozessdiagramm](images/SU-ProcessFlow.png)

Auf der linken Seite befindet sich ein Diagramm der Mixed Reality-Runtime, die immer aktiv ist und in einem eigenen Prozess ausgeführt wird. Diese Runtime ist für die Durchführung von Gerätenachverfolgung, räumlicher Zuordnung und anderen Vorgängen verantwortlich, die Scene Understanding verwendet, um die Welt um Sie herum zu verstehen und zu verstehen. Auf der rechten Seite des Diagramms werden zwei theoretische Anwendungen gezeigt, die Scene Understanding nutzen. Die erste Anwendung arbeitet mit MRTK zusammen, das intern das Scene Understanding SDK verwendet, die zweite App berechnet und verwendet zwei separate Szeneninstanzen. Alle drei Szenen in diesem Diagramm generieren unterschiedliche Instanzen der Szenen. Der Treiber verfolgt den globalen Zustand, der von Anwendungen gemeinsam genutzt wird, und Szenenobjekte in einer Szene nicht in einer anderen Szene. Scene Understanding bietet einen Mechanismus, der im Laufe der Zeit nachverfolgt werden kann, aber dies erfolgt mithilfe des SDK. Der Nachverfolgungscode wird bereits im SDK im Prozess Ihrer App ausgeführt.

Da jede Szene ihre Daten im Arbeitsspeicher Ihrer Anwendung speichert, können Sie davon ausgehen, dass die gesamte Funktion des Scene-Objekts oder seine internen Daten immer im Prozess Ihrer Anwendung ausgeführt werden.

### <a name="layout"></a>Layout

Für die Arbeit mit Scene Understanding kann es hilfreich sein, zu wissen und zu verstehen, wie die Laufzeit Komponenten logisch und physisch darstellt. Die Szene stellt Daten mit einem bestimmten Layout dar, das als einfach ausgewählt wurde, während eine zugrunde liegende Struktur beibehalten wird, die zukünftige Anforderungen erfüllen kann, ohne dass größere Revisionen erforderlich sind. Die Szene speichert dazu alle Komponenten (Bausteine für alle Szenenobjekte) in einer flachen Liste und definiert Hierarchie und Komposition über Verweise, in denen bestimmte Komponenten auf andere verweisen.

Unten sehen Sie ein Beispiel für eine -Struktur in ihrer flachen und logischen Form.

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

Nachdem Sie nun das logische Layout von Szenen verstanden haben, können wir nun das Konzept von SceneComponents und ihre Verwendung zum Erstellen von Hierarchien darstellen. SceneComponents sind die präzisesten Zerlegungen in SceneUnderstanding, die einen einzelnen Kern darstellen, z. B. ein Gitternetz oder ein Quader oder ein Begrenzungsfeld. SceneComponents sind Dinge, die unabhängig aktualisiert werden können und von anderen SceneComponents referenziert werden können. Daher verfügen sie über eine einzelne globale Eigenschaft mit einer eindeutigen ID, die diesen Typ von Nachverfolgungs-/Verweismechanismus ermöglicht. IDs werden für die logische Zusammensetzung der Szenenhierarchie und objektpersistenz verwendet (das Aktualisieren einer Szene relativ zu einer anderen). 

Wenn Sie jede neu berechnete Szene als eindeutig behandeln und einfach alle darin enthaltenen Daten aufzählen, sind die IDs für Sie weitgehend transparent. Wenn Sie jedoch planen, Komponenten über mehrere Updates nachzuverfolgen, verwenden Sie die IDs, um SceneComponents zwischen Szenenobjekten zu indizieren und zu suchen.

### <a name="sceneobjects"></a>SceneObjects

Ein SceneObject ist ein SceneComponent, das eine Instanz eines "Dings" darstellt, z. B. eine Wand, einen Boden, eine Obergrenze usw. ausgedrückt durch die Kind-Eigenschaft. SceneObjects sind geometrisch und verfügen daher über Funktionen und Eigenschaften, die ihre Position im Raum darstellen, jedoch keine geometrische oder logische Struktur enthalten. Stattdessen verweisen SceneObjects auf andere SceneComponents, insbesondere SceneQuads und SceneMeshes, die die verschiedenen Darstellungen bereitstellen, die vom System unterstützt werden. Wenn eine neue Szene berechnet wird, zählt Ihre Anwendung höchstwahrscheinlich die SceneObjects der Szene auf, um das zu verarbeiten, was sie interessiert.

SceneObjects kann eine der folgenden Funktionen aufweisen:

<table>
<tr>
<th>SceneObjectKind</th> <th>Beschreibung</th>
</tr>
<tr><td>Hintergrund</td><td>Das SceneObject ist bekannt dafür, dass es <b>sich nicht</b> um eine der anderen erkannten Arten von Szenenobjekten handelt. Diese Klasse sollte nicht mit Unknown verwechselt werden, wobei Background bekanntermaßen nicht "Wall", "Floor", "ceiling" usw. ist. während unbekannt noch nicht kategorisiert ist.</b></td></tr>
<tr><td>Wall</td><td>Eine physische Wand. Es wird davon ausgegangen, dass Es sich um wähnbare Umgebungsstrukturen handelt.</td></tr>
<tr><td>Etage</td><td>Etagen sind alle Oberflächen, auf denen sie begehbar sind. Hinweis: Dies sind keine Etagen. Beachten Sie auch, dass Die Etagen eine beliebige begehbare Oberfläche annehmen und daher keine explizite Annahme einer einzelnen Etage besteht. Strukturen auf mehreren Ebenen, Rampen usw. sollte alle als Floor klassifiziert werden.</td></tr>
<tr><td>Ceiling</td><td>Die obere Oberfläche eines Raumes.</td></tr>
<tr><td>Plattform</td><td>Eine große flache Oberfläche, auf der Sie Hologramme platzieren können. Diese stellen in der Regel Tabellen, Arbeitsflächen und andere große horizontale Oberflächen dar.</td></tr>
<tr><td>World</td><td>Eine reservierte Bezeichnung für geometrische Daten, die von der Bezeichnung unabhängig sind. Das Gitternetz, das durch Festlegen des EnableWorldMesh-Updateflags generiert wird, wird als world klassifiziert.</td></tr>
<tr><td>Unbekannt</td><td>Dieses Szenenobjekt muss noch klassifiziert und einer Art zugewiesen werden. Dies sollte nicht mit Background verwechselt werden, da es sich bei diesem Objekt um etwas handelt, hat das System noch keine stark genug klassifizierung dafür eingerichtet.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

Eine SceneMesh ist eine SceneComponent, die die Geometrie beliebiger geometrischer Objekte mithilfe einer Dreiecksliste annähert. SceneMeshes werden in verschiedenen Kontexten verwendet. Sie können Komponenten der wasserdichten Zellstruktur oder als WorldMesh darstellen, das das der Szene zugeordnete Gitternetz für die ungebundene räumliche Zuordnung darstellt. Die index- und vertex-Daten, die mit jedem Gitternetz bereitgestellt werden, verwenden das gleiche vertraute Layout wie die [Scheitelpunkt- und Indexpuffer,](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) die zum Rendern von Dreiecksgittern in allen modernen Rendering-APIs verwendet werden. In Scene Understanding verwenden Gitternetze 32-Bit-Indizes und müssen möglicherweise in Blöcke für bestimmte Rendering-Engines unterteilt werden.

#### <a name="winding-order-and-coordinate-systems"></a>Windingreihenfolge und Koordinatensysteme

Von allen von Scene Understanding erzeugten Gitternetzen wird erwartet, dass sie Gitternetze in einem Right-Handed Koordinatensystem zurückgeben, indem sie im Uhrzeigersinn gewunden werden. 

Hinweis: Betriebssystembuilds vor .191105 weisen möglicherweise einen bekannten Fehler auf, bei dem "World"-Gitternetze in Counter-Clockwise Wickelreihenfolge zurückgegeben wurden, die anschließend behoben wurde.

### <a name="scenequad"></a>SceneQuad

Ein SceneQuad ist eine SceneComponent, die 2d-Oberflächen darstellt, die die 3D-Welt einnehmen. SceneQuads können ähnlich wie ARKit ARPlaneAnchor oder ARCore Planes verwendet werden, bieten jedoch eine allgemeinere Funktionalität als 2D-Canvass, die von flachen Apps oder einer erweiterten Benutzererfahrung verwendet werden können. 2D-spezifische APIs werden für Quader bereitgestellt, die die Verwendung von Platzierung und Layout vereinfachen. Die Entwicklung (mit Ausnahme des Renderings) mit Quadern sollte sich eher wie die Arbeit mit 2D-Canvass als mit 3D-Gitternetzen anfühlen.

#### <a name="scenequad-shape"></a>SceneQuad-Form

SceneQuads definieren eine umgrenzte rechteckige Oberfläche in 2d. SceneQuads stellen jedoch Oberflächen mit beliebigen und potenziell komplexen Formen dar (z. B. eine donutförmige Tabelle). Um die komplexe Form der Oberfläche eines Quaders darzustellen, können Sie die GetSurfaceMask-API verwenden, um die Form der Oberfläche in einem von Ihnen bereitgestellten Bildpuffer zu rendern. Wenn das SceneObject mit dem Quader ebenfalls über ein Gitternetz verfügt, sollten die Gittergitterdreiecke diesem gerenderten Bild entsprechen. Beide stellen die echte Geometrie der Oberfläche dar, entweder in 2d- oder 3d-Koordinaten.

## <a name="scene-understanding-sdk-details-and-reference"></a>Details und Referenz zum Scene Understanding SDK

> [!NOTE] 
> Beachten Sie bei der Verwendung von MRTK, dass Sie mit MRTKs interagieren [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) und daher diesen Abschnitt in den meisten Fällen überspringen können. Weitere Informationen finden Sie in der [MRTK Scene Understanding-Dokumentation.](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding)

Der folgende Abschnitt hilft Ihnen, sich mit den Grundlagen von SceneUnderstanding vertraut zu machen. Dieser Abschnitt sollte Ihnen die Grundlagen bieten. An diesem Punkt sollten Sie über genügend Kontext verfügen, um die Beispielanwendungen zu durchsuchen, um zu sehen, wie SceneUnderstanding ganzheitlicher verwendet wird.

### <a name="initialization"></a>Initialisierung

Der erste Schritt beim Arbeiten mit SceneUnderstanding besteht darin, dass Ihre Anwendung einen Verweis auf ein Scene-Objekt erhält. Dies kann auf zwei Arten erfolgen: Eine Szene kann entweder vom Treiber berechnet werden, oder eine vorhandene Szene, die in der Vergangenheit berechnet wurde, kann deserimetrisiert werden. Letzteres ist nützlich für die Arbeit mit SceneUnderstanding während der Entwicklung, bei der Anwendungen und Erfahrungen schnell ohne ein Mixed Reality-Gerät prototypiert werden können.

Szenen werden mithilfe eines SceneObservers berechnet. Vor dem Erstellen einer Szene sollte Ihre Anwendung Ihr Gerät abfragen, um sicherzustellen, dass es SceneUnderstanding unterstützt, sowie Benutzerzugriff für Informationen anfordern, die SceneUnderstanding benötigt.

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Wenn RequestAccessAsync() nicht aufgerufen wird, schlägt das Berechnen einer neuen Szene fehl. Als Nächstes berechnen wir eine neue Szene, die auf dem Mixed Reality Headset basiert und einen Radius von 10 Metern hat.

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

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>Initialisierung aus Daten (auch bekannt als . PC-Pfad)

Szenen können zwar für die direkte Nutzung berechnet werden, sie können aber auch zur späteren Verwendung in serialisierter Form berechnet werden. Dies hat sich als nützlich für die Entwicklung erwiesen, da Entwickler damit Scene Understanding ohne geräteloses Arbeiten und Testen testen können. Die Serialisierung einer Szene ist nahezu identisch mit der Berechnung. Die Daten werden an Ihre Anwendung zurückgegeben, anstatt lokal vom SDK deserialisiert zu werden. Sie können es dann selbst deserialisieren oder zur zukünftigen Verwendung speichern.

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

Nachdem Ihre Anwendung nun über eine Szene verfügt, wird ihre Anwendung SceneObjects betrachten und mit ihnen interagieren. Dazu greifen Sie auf die **SceneObjects-Eigenschaft** zu:

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

### <a name="component-update-and-refinding-components"></a>Komponentenaktualisierung und Neusuche von Komponenten

Es gibt eine weitere Funktion, die Komponenten in der Szene mit dem Namen ***FindComponent abruft.*** Diese Funktion ist nützlich, wenn Nachverfolgungsobjekte aktualisiert und in späteren Szenen gefunden werden. Der folgende Code berechnet eine neue Szene relativ zu einer vorherigen Szene und sucht dann den Boden in der neuen Szene.

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

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>Zugreifen auf Gitternetze und Quader aus Szenenobjekten

Sobald SceneObjects gefunden wurde, möchte Ihre Anwendung höchstwahrscheinlich auf die Daten zugreifen, die in den Quadern/Gitternetzen enthalten sind, aus denen sie besteht. Auf diese Daten wird mit den Eigenschaften ***Quads** _ und _ *_Meshes_** zugegriffen. Mit dem folgenden Code werden alle Quader und Gitternetze des Floor-Objekts aufzählt.

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

Beachten Sie, dass es sich um das SceneObject handelt, das über die Transformation verfügt, die relativ zum Ursprung der Szene ist. Dies liegt daran, dass das SceneObject eine Instanz eines "Dings" darstellt und im Raum veranladbar ist, die Quader und Gitternetze Geometrie darstellen, die relativ zu ihrem übergeordneten Element transformiert wird. Es ist möglich, dass separate SceneObjects auf dieselben SceneMesh/SceneQuad SceneComponents verweisen, und es ist auch möglich, dass ein SceneObject über mehr als eine SceneMesh/SceneQuad verfügt.

### <a name="dealing-with-transforms"></a>Umgang mit Transformationen

Scene Understanding hat einen absichtlichen Versuch unternommen, sich beim Umgang mit Transformationen an herkömmlichen 3D-Szenendarstellungen auszurichten. Jede Szene ist daher auf ein einzelnes Koordinatensystem beschränkt, ähnlich wie die meisten gängigen 3D-Umgebungsdarstellungen. SceneObjects geben jeweils ihre Position relativ zu diesem Koordinatensystem an. Wenn Ihre Anwendung mit Szenen zu tun hat, die die Grenze des von einem einzelnen Ursprung bereitgestellten Objekts ausdehnen, kann sie SceneObjects in SpatialAnchors verankern oder mehrere Szenen generieren und zusammenführen. Der Einfachheit halber gehen wir jedoch davon aus, dass sich wässrige Szenen in ihrem eigenen Ursprung befinden, der durch eine NodeId lokalisiert ist, die durch Scene.OriginSpatialGraphNodeId definiert wird.

Der folgende Unity-Code zeigt beispielsweise, wie Sie Windows Perception- und Unity-APIs verwenden, um Koordinatensysteme zusammen auszurichten. Ausführliche Informationen zu den Windows Perception-APIs finden Sie unter [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) und [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) und [Mixed Reality nativen Objekte in Unity,](/windows/mixed-reality/unity-xrdevice-advanced) um Details zum Abrufen eines SpatialCoordinateSystem zu erhalten, das dem Ursprung von Unity entspricht.

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

Jede `SceneObject` verfügt über eine Transformation, die dann auf dieses Objekt angewendet wird. In Unity konvertieren wir in rechtshändige Koordinaten und weisen lokale Transformationen zu:

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

Quads wurden entwickelt, um 2D-Platzierungsszenarien zu unterstützen, und sollten als Erweiterungen für 2D-Canvas-UX-Elemente gedacht werden. Während Quads Komponenten von SceneObjects sind und in 3D gerendert werden können, gehen die Quad-APIs selbst davon aus, dass Quads 2D-Strukturen sind. Sie bieten Informationen wie "extent", "shape" und "provide APIs for placement".

Quader verfügen über rechteckige Kästchen, stellen aber beliebig formatierte 2D-Oberflächen dar. Um die Platzierung auf diesen 2D-Oberflächen zu ermöglichen, die mit den 3D-Umgebungsquads interagieren, bieten Quads Hilfsprogramme, um diese Interaktion zu ermöglichen. Scene Understanding bietet derzeit zwei solche Funktionen: **FindCentermostPlacement** und **GetSurfaceMask.** FindCentermostPlacement ist eine high-level-API, die eine Position auf dem Quader sucht, an der ein Objekt platziert werden kann, und versucht, den besten Speicherort für Ihr Objekt zu finden, wodurch sichergestellt wird, dass der von Ihnen bereitgestellte Begrenzungsfeld auf der zugrunde liegenden Oberfläche verbleibt.

> [!NOTE]
> Die Koordinaten der Ausgabe sind relativ zum Quader im "Quad space", wobei die linke obere Ecke (x = 0, y = 0) ist, genau wie bei anderen Rect-Typen von Fenstern. Berücksichtigen Sie dies unbedingt, wenn Sie mit den Ursprüngen Ihrer eigenen Objekte arbeiten. 

Im folgenden Beispiel wird gezeigt, wie Sie die ortsmittelbarste Position finden und ein Hologramm am Quader ankert.

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

Die Schritte 1 bis 4 hängen stark von Ihrem spezifischen Framework bzw. Ihrer Implementierung ab, die Designs sollten jedoch ähnlich sein. Es ist wichtig zu beachten, dass der Quader einfach eine umgrenzte 2D-Ebene darstellt, die im Raum lokalisiert ist. Wenn Ihre Engine/Ihr Framework weiß, wo sich das Quad befindet, und Ihre Objekte relativ zum Quader stammen, werden Ihre Hologramme in Bezug auf die reale Welt korrekt angeordnet. 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>Mesh

Gittermodelle stellen geometrische Darstellungen von Objekten oder Umgebungen dar. Ähnlich wie [bei der räumlichen Zuordnung](../../design/spatial-mapping.md)verwenden Gitterindex- und Vertexdaten, die mit jedem Raumoberflächengitternetz bereitgestellt werden, das gleiche vertraute Layout wie die Scheitelpunkt- und Indexpuffer, die zum Rendern von Dreiecksgitternetzen in allen modernen Rendering-APIs verwendet werden. Scheitelpunktpositionen werden im Koordinatensystem des `Scene` bereitgestellt. Die spezifischen APIs, die zum Verweisen auf diese Daten verwendet werden, lauten wie folgt:

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

Die Index-/Scheitelpunktpuffer müssen >= index/vertex counts sein, können aber andernfalls beliebig dimensioniert werden, um eine effiziente Speicherwiederverwendung zu ermöglichen.

### <a name="collidermesh"></a>ColliderMesh

Szenenobjekte ermöglichen den Zugriff auf Mesh- und Collidermeshdaten über die Eigenschaften Meshes und ColliderMeshes. Diese Gitternetze stimmen immer überein, was bedeutet, dass der i'th-Index der Meshes-Eigenschaft die gleiche Geometrie wie der i'th-Index der ColliderMeshes-Eigenschaft darstellt. Wenn die Laufzeit bzw. das Objekt Collidergitternetze unterstützt, erhalten Sie garantiert das niedrigste Polygon und die höchste Näherung der Reihenfolge, und es empfiehlt sich, ColliderMeshes überall dort zu verwenden, wo Ihre Anwendung Collider verwenden würde. Wenn das System keine Collider unterstützt, ist das in ColliderMeshes zurückgegebene Mesh-Objekt dasselbe Objekt wie das Gittermodell, das Arbeitsspeichereinschränkungen reduziert.

## <a name="developing-with-scene-understanding"></a>Entwickeln mit Szenenverständnis

An diesem Punkt sollten Sie die grundlegenden Bausteine der Szene verstehen, die Laufzeit und SDK verstehen. Der Großteil der Leistungsfähigkeit und Komplexität liegt in Zugriffsmustern, der Interaktion mit 3D-Frameworks und Tools, die auf diesen APIs geschrieben werden können, um komplexere Aufgaben wie räumliche Planung, Raumanalyse, Navigation, Physik usw. auszuführen. Wir hoffen, diese in Beispielen erfassen zu können, die Sie hoffentlich in die richtige Richtung führen sollten, um Ihre Szenarien zu optimieren. Wenn es Beispiele oder Szenarien gibt, die wir nicht behandeln, teilen Sie uns dies mit, und wir versuchen, die benötigten Informationen zu dokumentieren bzw. einen Prototyp zu erstellen.

### <a name="where-can-i-get-sample-code"></a>Wo erhalte ich Beispielcode?

Scene Understanding-Beispielcode für Unity finden Sie auf unserer [Unity-Beispielseite.](https://github.com/sceneunderstanding-microsoft/unitysample) Mit dieser Anwendung können Sie mit Ihrem Gerät kommunizieren und die verschiedenen Szenenobjekte rendern, oder Sie können eine serialisierte Szene auf Ihrem PC laden und Scene Understanding ohne Gerät erleben.

### <a name="where-can-i-get-sample-scenes"></a>Wo finde ich Beispielszenen?

Wenn Sie über eine HoloLens2 verfügen, können Sie jede von Ihnen erfasste Szene speichern, indem Sie die Ausgabe von ComputeSerializedAsync in einer Datei speichern und nach Beholholen deserialisieren. 

Wenn Sie kein HoloLens2-Gerät haben, aber mit Scene Understanding spielen möchten, müssen Sie eine vorab erfasste Szene herunterladen. Das Scene Understanding-Beispiel wird derzeit mit serialisierten Szenen bereitgestellt, die heruntergeladen und nach Behebung verwendet werden können. Sie finden sie hier:

[Szenenverständnis von Beispielszenen](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>Siehe auch

* [Räumliche Abbildung](../../design/spatial-mapping.md)
* [Grundlegendes zu Szenen](../../design/scene-understanding.md)
* [Unity-Beispiel](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)