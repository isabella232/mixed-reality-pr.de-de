---
title: Scene Understanding SDK
description: Erfahren Sie, wie Sie das Scene Understanding SDK, einschließlich Komponenten, Meshes und Objekten, in Mixed Reality-apps installieren und verwenden.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Szenen Verständnis, räumliche Zuordnung, Windows Mixed Reality, Unity
ms.openlocfilehash: 748ec444bfcbabb534f391a889fcc16c7671bf7d
ms.sourcegitcommit: 753f0ee94cf86be645cad8efd60f1b43ac529c96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2021
ms.locfileid: "98758370"
---
# <a name="scene-understanding-sdk-overview"></a>Übersicht über das Szene Verständnis von SDK

Mit dem Einblick in die Szene werden die unstrukturierten Umgebungs Sensordaten transformiert, die ihr gemischtes Reality-Gerät erfasst und in eine leistungsstarke abstrakte Darstellung konvertiert. Das SDK fungiert als Kommunikationsschicht zwischen Ihrer Anwendung und der Szene zur Laufzeit. Sie ist darauf ausgerichtet, vorhandene standardkonstrukte wie 3D-Szenen Diagramme für 3D-Darstellungen und 2D-Rechtecke und Panels für 2D-Anwendungen zu imitieren. Die Konstrukte der Konstrukte sind zwar mit konkreten Frameworks vertraut, aber im Allgemeinen ist das Framework agnostisch eine Interoperabilität zwischen verschiedenen Frameworks, die mit ihr interagieren. Wenn das Verständnis von Szenen weiterentwickelt wird, besteht die Rolle des SDK darin, dass neue Darstellungen und Funktionen weiterhin in einem vereinheitlichten Framework verfügbar gemacht werden. In diesem Dokument werden zunächst allgemeine Konzepte vorgestellt, die Ihnen helfen, sich mit der Entwicklungsumgebung und-Nutzung vertraut zu machen und dann eine ausführlichere Dokumentation für bestimmte Klassen und Konstrukte bereitzustellen.

## <a name="where-do-i-get-the-sdk"></a>Wo erhalte ich das SDK?

Das sceneunderstanding SDK kann über nuget heruntergeladen werden.

[Sceneunderstanding-SDK](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

**Hinweis:** die neueste Version hängt von den Vorschau Paketen ab, und Sie müssen die Vorabversion von Paketen aktivieren, um Sie anzuzeigen.

Bei Version 0.5.2022-RC und höher unterstützt Szenen Verständnis sprach Projektionen für c# und C++, mit denen Anwendungen Anwendungen für Win32-oder UWP-Plattformen entwickeln können. Ab dieser Version unterstützt sceneunderstanding die Unterstützung von Unity im Editor, die den sceneobserver verwendet, der ausschließlich für die Kommunikation mit HoloLens2 verwendet wird. 

Sceneunderstanding erfordert Windows SDK-Version 18362 oder höher. 

Wenn Sie das SDK in einem Unity-Projekt verwenden, verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity) , um das Paket in Ihrem Projekt zu installieren.

## <a name="conceptual-overview"></a>Konzeptionelle Übersicht

### <a name="the-scene"></a>Die Szene

Ihr gemischtes Reality-Gerät integriert ständig Informationen zu den in Ihrer Umgebung angezeigten Informationen. In der Szene werden alle diese Datenquellen verstanden und eine einzelne, zusammenhängende Abstraktion erzeugt. Szenen Verständnis generiert Szenen, bei denen es sich um eine Komposition von [sceneobjects](scene-understanding-SDK.md#sceneobjects) handelt, die eine Instanz eines einzelnen Objekts darstellen (z. b. eine Wand/Ceiling/Floor). Szenen Objekte selbst sind eine Komposition von [scenecomponents, die präziseste Teile darstellen, die dieses sceneobject bilden. Beispiele für Komponenten sind Quads und Meshes, aber in der Zukunft könnten Begrenzungs Felder, Kollisions Netze, Metadaten usw. darstellen.

Der Prozess der Umstellung der Rohdaten des Sensors in eine Szene ist ein potenziell kostspieliger Vorgang, bei dem mittlere Leerräume (~ 10X 10m) für große Leerzeichen (~ 50X 50 Mio.) auf Minuten und somit nicht vom Gerät ohne Anwendungsanforderung berechnet werden. Stattdessen wird die Szenen Generierung von Ihrer Anwendung Bedarfs gesteuert ausgelöst. Die sceneobserver-Klasse verfügt über statische Methoden, die eine Szene berechnen oder deserialisieren können, die Sie dann auflisten/mit der Sie interagieren können. Die "Compute"-Aktion wird Bedarfs gesteuert ausgeführt und wird auf der CPU ausgeführt, aber in einem separaten Prozess (dem Mixed Reality-Treiber). Während wir in einem anderen Prozess berechnen, werden die resultierenden Szenen Daten jedoch in der Anwendung im Scene-Objekt gespeichert und verwaltet. 

Das folgende Diagramm veranschaulicht den Prozessfluss und zeigt Beispiele für zwei Anwendungen an, die mit der Laufzeitumgebung vertraut sind. 

![Prozessdiagramm](images/SU-ProcessFlow.png)

Auf der linken Seite befindet sich ein Diagramm der Mixed Reality-Laufzeit, die immer eingeschaltet ist und in einem eigenen Prozess ausgeführt wird. Diese Laufzeit ist für die Durchführung von Geräte Nachverfolgung, räumlicher Zuordnung und anderen Vorgängen zuständig, die von der Szene verstanden werden, um die Welt zu verstehen und zu verstehen. Auf der rechten Seite des Diagramms zeigen wir zwei theoretische Anwendungen, die das Verständnis von Szenen nutzen. Die erste Anwendung stellt mit mrtk eine Schnittstelle dar, die intern das Scene Understanding SDK verwendet, die zweite App berechnet und verwendet zwei separate Szenen Instanzen. In allen drei Szenen in diesem Diagramm werden unterschiedliche Instanzen der Kulissen generiert. der Treiber verfolgt keinen globalen Status, der von Anwendungen gemeinsam genutzt wird, und Szenen Objekte in einer Szene werden nicht in einer anderen Szene gefunden. Der Einblick in die Szene bietet einen Mechanismus, mit dem Sie die Zeit nachverfolgen können, dies erfolgt jedoch mit dem SDK. Der Überwachungs Code wird im SDK bereits im Prozess der app ausgeführt.

Da jede Szene Ihre Daten im Speicherbereich Ihrer Anwendung speichert, können Sie davon ausgehen, dass alle Funktionen des Szene Objekts oder der internen Daten immer im Prozess ihrer Anwendung ausgeführt werden.

### <a name="layout"></a>Layout

Um mit der Darstellung von Szenen zu arbeiten, kann es hilfreich sein zu wissen und zu verstehen, wie die Laufzeit Komponenten logisch und physisch darstellt. Die Szene stellt Daten mit einem bestimmten Layout dar, das als einfach gewählt wurde, während eine zugrunde liegende Struktur beibehalten wird, die für zukünftige Anforderungen geeignet ist, ohne dass größere Revisionen erforderlich sind. In der Szene werden alle Komponenten (Bausteine für alle Szene Objekte) in einer flachen Liste gespeichert, und die Hierarchie und Komposition werden durch Verweise definiert, bei denen bestimmte Komponenten auf andere verweisen.

Im folgenden finden Sie ein Beispiel für eine Struktur in der flachen und logischen Form.

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

In dieser Abbildung wird der Unterschied zwischen dem physischen und dem logischen Layout der Szene hervorgehoben. Auf der linken Seite sehen wir das hierarchische Layout der Daten, die Ihre Anwendung beim Auflisten der Szene sieht. Auf der rechten Seite sehen wir, dass die Szene aus 12 unterschiedlichen Komponenten besteht, auf die bei Bedarf einzeln zugegriffen werden kann. Bei der Verarbeitung einer neuen Szene erwarten wir, dass Anwendungen diese Hierarchie logisch durchlaufen. bei der Überwachung zwischen Szenen Aktualisierungen sind einige Anwendungen jedoch möglicherweise nur für bestimmte Komponenten interessant, die von zwei Szenen gemeinsam genutzt werden.

## <a name="api-overview"></a>API-Übersicht

Der folgende Abschnitt enthält eine allgemeine Übersicht über die Konstrukte in der Szene. In diesem Abschnitt erfahren Sie, wie Szenen dargestellt werden und für welche Komponenten die verschiedenen Komponenten verwendet werden. Im nächsten Abschnitt werden konkrete Codebeispiele und zusätzliche Details bereitgestellt, die in dieser Übersicht ausgeblendet sind.

Alle unten beschriebenen Typen befinden sich im- `Microsoft.MixedReality.SceneUnderstanding` Namespace.

### <a name="scenecomponents"></a>Scenecomponents

Nachdem Sie nun das logische Layout von Szenen verstanden haben, können wir nun das Konzept der scenecomponents und deren Verwendung zum Verfassen der Hierarchie vorstellen. Scenecomponents sind die präzisesten Zusammensetzungen in sceneunderstanding, die ein einzelnes Kernstück darstellen, z. b. ein Mesh-oder ein Quad-oder ein Begrenzungsfeld. Scenecomponents sind Dinge, die unabhängig voneinander aktualisiert werden können und von anderen scenecomponents referenziert werden können. Daher verfügen Sie über eine einzelne globale Eigenschaft, die eine eindeutige ID für diese Art von Nachverfolgung/Verweis Mechanismus zulässt. IDs werden sowohl für die logische Komposition der Szenen Hierarchie als auch für die Objekt Persistenz verwendet (der Vorgang der Aktualisierung einer Szene relativ zu einer anderen). 

Wenn Sie jede neu berechnete Szene als unterschiedlich behandeln und einfach alle darin enthaltenen Daten auflisten, sind die IDs größtenteils für Sie transparent. Wenn Sie jedoch planen, Komponenten über mehrere Updates zu verfolgen, verwenden Sie die IDs, um scenecomponents zwischen Szene Objekten zu indizieren und zu suchen.

### <a name="sceneobjects"></a>Sceneobjects

Ein sceneobject ist eine scenecomponent, die eine Instanz eines "Thing" darstellt (z. b. eine Wand, eine Fläche, eine Obergrenze usw.). ausgedrückt durch ihre Kind-Eigenschaft. Sceneobjects sind geometrisch und verfügen daher über Funktionen und Eigenschaften, die ihre Position im Raum darstellen, Sie enthalten jedoch keine geometrische oder logische Struktur. Stattdessen verweisen sceneobjects auf andere scenecomponents, insbesondere scenequads und scenemesches, die die unterschiedlichen Darstellungen bereitstellen, die vom System unterstützt werden. Wenn eine neue Szene berechnet wird, listet Ihre Anwendung wahrscheinlich die sceneobjects der Szene auf, um zu verarbeiten, was Sie interessiert.

Sceneobjects können eine der folgenden Möglichkeiten aufweisen:

<table>
<tr>
<th>Sceneobjectkind</th> <th>BESCHREIBUNG</th>
</tr>
<tr><td>Hintergrund</td><td>Das sceneobject-Objekt ist bekannt, dass es sich <b>nicht</b> um eines der anderen erkannten Arten von Szenen Objekten handelt. Diese Klasse sollte nicht mit unknown verwechselt werden, wenn der Hintergrund bekanntermaßen nicht "Wall/Floor/Ceiling" ist usw... Obwohl Unknown noch nicht kategorisiert ist.</b></td></tr>
<tr><td>Wall</td><td>Eine physische Wand. Wände werden als unveränderbare Umgebungs Strukturen angesehen.</td></tr>
<tr><td>Etage</td><td>Die Ebenen sind beliebige Oberflächen, auf denen eine durchlaufen werden kann. Hinweis: die Treppe ist nicht "Floors". Beachten Sie auch, dass die Böden eine beliebige über-und-Oberfläche annehmen und daher keine explizite Annahme eines Singular ist. Strukturen mit mehreren Ebenen, Rampen usw.... sollten alle als Floor klassifiziert werden.</td></tr>
<tr><td>Ceiling</td><td>Die Oberfläche eines Raums.</td></tr>
<tr><td>Plattform</td><td>Eine große flache Oberfläche, auf der Sie holograms platzieren können. Diese stellen tendenziell Tabellen, Countertops und andere große horizontale Flächen dar.</td></tr>
<tr><td>World</td><td>Eine reservierte Bezeichnung für geometrische Daten, die für die Bezeichnung agnostisch ist. Das Mesh, das durch Festlegen des enableworldmesh-UpdateFlags generiert wird, würde als Welt klassifiziert werden.</td></tr>
<tr><td>Unbekannt</td><td>Dieses Scene-Objekt muss noch klassifiziert und zugewiesen werden. Dies sollte nicht mit dem Hintergrund verwechselt werden, da es sich bei diesem Objekt um beliebige Elemente handeln könnte.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

Eine scenemesh ist eine scenecomponent, die die Geometrie willkürlicher geometrischer Objekte mithilfe einer Dreiecks Liste angleicht. Scenemesches werden in verschiedenen Kontexten verwendet, Sie können Komponenten der wasserdichten Zellstruktur oder als worldmesh darstellen, das das ungebundene räumliche zustrukturnetz darstellt, das der Szene zugeordnet ist. Die für jedes Mesh bereitgestellten Index-und Vertex-Daten verwenden dasselbe vertraute Layout wie der [Scheitelpunkt und die Index Puffer](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) , die zum Rendern von Dreiecksnetzen in allen modernen renderingapis verwendet werden. In der Szene ist es erforderlich, dass die Netze 32-Bit-Indizes verwenden und möglicherweise in Blöcke für bestimmte renderingengines aufgeteilt werden.

#### <a name="winding-order-and-coordinate-systems"></a>Sortieren von Reihenfolge und Koordinatensystemen

Alle Netzen, die von der Szene verstanden werden, werden voraussichtlich in einem Right-Handed Koordinatensystem mithilfe der Reihenfolge im Uhrzeigersinn zurückgeben. 

Hinweis: Betriebssystem-Builds vor. 191105 verfügen möglicherweise über einen bekannten Fehler, bei dem "World"-Netzen in Counter-Clockwise Sortierreihenfolge zurückgegeben werden, die anschließend korrigiert wurde.

### <a name="scenequad"></a>Scenequad

Eine scenequad ist eine scenecomponent, die 2D-Oberflächen darstellt, die die 3D--Welt belegen. Scenequads können ähnlich wie Arkit arplaneanchor oder Arcore-Ebenen verwendet werden, bieten jedoch eine höhere Funktionalität als 2D-canvasen, die von flachen Apps oder einer erweiterten UX verwendet werden. 2D-spezifische APIs werden für Quads bereitgestellt, mit denen die Platzierung und das Layout einfach zu verwenden sind, und die Entwicklung (mit Ausnahme des Renderings) mit Quads sollte eher dem Arbeiten mit 2D-kanvasen als 3D--Meshes ähneln.

#### <a name="scenequad-shape"></a>Scenequad-Form

Scenequads definieren eine begrenzte rechteckige Oberfläche in 2D. Scenequads stellen jedoch Oberflächen mit beliebigen und potenziell komplexen Formen dar (z. b. eine ringförmige Tabelle). Wenn Sie die komplexe Form der Oberfläche eines viervieres darstellen möchten, können Sie die getsurfacemask-API verwenden, um die Form der Oberfläche auf einem von Ihnen bereitgestellten Bild Puffer zu Renderern. Wenn das sceneobject mit dem Quad auch ein Mesh hat, sollte der Gitter Dreiecke diesem gerenderten Bild entsprechen, beide stellen eine echte Geometrie der Oberfläche dar, entweder in 2D-oder 3D--Koordinaten.

## <a name="scene-understanding-sdk-details-and-reference"></a>Scene Understanding SDK-Details und-Referenz

Im folgenden Abschnitt wird erläutert, wie Sie mit den Grundlagen von sceneunderstanding vertraut werden. In diesem Abschnitt werden die Grundlagen erläutert. zu diesem Zeitpunkt sollten Sie über genügend Kontext verfügen, um die Beispielanwendungen zu durchsuchen und zu sehen, wie sceneunderstanding ganzheitlich genutzt wird.

### <a name="initialization"></a>Initialisierung

Der erste Schritt bei der Arbeit mit sceneunderstanding besteht darin, dass Ihre Anwendung auf ein Szene Objekt verweist. Dies kann auf zwei Arten erfolgen: eine Szene kann entweder vom Treiber berechnet werden, oder eine vorhandene Szene, die in der Vergangenheit berechnet wurde, kann deserialisiert werden. Letzteres ist für die Arbeit mit sceneunderstanding während der Entwicklung nützlich, bei der Anwendungen und Erfahrungen schnell ohne ein gemischtes Reality-Gerät prototypisiert werden können.

Szenen werden mithilfe eines sceneobserver berechnet. Bevor Sie eine Szene erstellen, sollte Ihre Anwendung Ihr Gerät Abfragen, um sicherzustellen, dass Sie sceneunderstanding unterstützt, sowie den Benutzer Zugriff auf Informationen anfordern, die von sceneunderstanding benötigt werden.

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Wenn requestaccessasync () nicht aufgerufen wird, tritt beim Berechnen einer neuen Szene ein Fehler auf. Als Nächstes berechnen wir eine neue Szene, die auf dem Mixed Reality-Headset liegt und über einen Radius von 10 Metern verfügt.

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

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>Initialisierung von Daten (auch als bezeichnet). der PC-Pfad)

Szenen können für den direkten Verbrauch berechnet werden, Sie können jedoch auch in serialisierter Form für die spätere Verwendung berechnet werden. Dies hat sich als nützlich für die Entwicklung bewährt, da Entwickler damit arbeiten können, ohne dass ein Gerät benötigt wird. Der Vorgang der Serialisierung einer Szene ist nahezu identisch mit dem berechnen, die Daten werden an Ihre Anwendung zurückgegeben, anstatt lokal vom SDK deserialisiert zu werden. Sie können Sie dann selbst deserialisieren oder zur späteren Verwendung speichern.

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

### <a name="sceneobject-enumeration"></a>Sceneobject-Enumeration

Nun, da Ihre Anwendung eine Szene hat, wird Ihre Anwendung mit sceneobjects beschäftigt und interagiert. Dies erfolgt durch den Zugriff auf die **sceneobjects** -Eigenschaft:

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

### <a name="component-update-and-refinding-components"></a>Komponenten Update und neusuchen von Komponenten

Es gibt eine weitere Funktion, die Komponenten in der Szene abruft, die als **_findComponent_* _ bezeichnet werden. Diese Funktion ist nützlich, wenn Überwachungs Objekte aktualisiert und in späteren Szenen gefunden werden. Mit dem folgenden Code wird eine neue Szene in Relation zu einer vorherigen Szene berechnet und dann die Fläche in der neuen Szene gefunden.

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

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>Zugreifen auf Meshes und Quads von Szenen Objekten

Nachdem sceneobjects gefunden wurde, möchte Ihre Anwendung höchstwahrscheinlich auf die Daten zugreifen, die in den Quads/Meshes enthalten sind, aus denen Sie besteht. Der Zugriff auf diese Daten erfolgt über die Eigenschaften " _*_Quads_*_ " und " _*_Meshes_*_ ". Mit dem folgenden Code werden alle Quads und Netzen des Floor-Objekts aufgelistet.

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

Beachten Sie, dass es sich um das sceneobject-Objekt mit der Transformation handelt, die relativ zum Ursprung der Szene ist. Der Grund hierfür ist, dass das sceneobject-Objekt eine Instanz eines "Thing" darstellt und im Raum einstellbar ist, die Quads und die Netzen eine Geometrie darstellen, die relativ zu ihrem übergeordneten Element transformiert wird. Es ist möglich, dass separate sceneobjects auf die gleichen scenemesh/scenequad scenecomponents verweisen, und es ist auch möglich, dass ein sceneobject-Objekt über mehr als eine scenemesh/scenequad verfügt.

### <a name="dealing-with-transforms"></a>Umgang mit Transformationen

Das Verständnis der Szene hat beim Umgang mit Transformationen einen absichtlichen Versuch unternommen, an herkömmlichen 3D-Szenen Darstellungen auszurichten. Daher ist jede Szene auf ein einzelnes Koordinatensystem beschränkt, ähnlich wie die gängigsten 3D-Umwelt Darstellungen. Sceneobjects stellen jeweils ihren Speicherort relativ zu diesem Koordinatensystem bereit. Wenn Ihre Anwendung mit Szenen beschäftigt ist, die das Limit eines einzelnen Ursprungs überschreiten, können Sie sceneobjects an spatialanchor anfügen oder mehrere Szenen generieren und zusammen zusammenführen, aber aus Gründen der Einfachheit gehen wir davon aus, dass die wasserdichten Szenen in Ihrem eigenen Ursprung vorhanden sind, der durch eine durch Scene. originspatialgraphnodeid definierte NodeId lokalisiert wird.

Der folgende Unity-Code zeigt beispielsweise, wie Sie die Windows-perception-und Unity-APIs verwenden, um Koordinatensysteme gleich abzustimmen. Ausführliche Informationen zum Abrufen eines spatialcoordinatesystem, das dem Welt [Ursprung von Unity](//windows/mixed-reality/unity-xrdevice-advanced) entspricht, finden Sie unter [spatialcoordinatesystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem) und [spatialgraphinteroppreview](//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) .

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

Jede `SceneObject` verfügt über eine Transformation, die dann auf das Objekt angewendet wird. In Unity konvertieren wir in Rechte übergebene Koordinaten und weisen lokale Transformationen wie folgt zu:

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

### <a name="quad"></a>Quad

Die Quads wurden zur Unterstützung von 2D-Platzierungs Szenarios entwickelt und sollten sich als Erweiterungen für 2D-Canvas-UX-Elemente vorstellen. Obwohl es sich bei den Quads um Komponenten von sceneobjects handelt, die in 3D gerendert werden können, werden die Quad-APIs selbst annehmen, dass die Quad- Sie bieten Informationen wie Block, Form und Bereitstellen von APIs für die Platzierung.

Die Unterbrechungen haben rechteckige Blöcke, stellen aber beliebig geformte 2D-Oberflächen dar. Um die Platzierung auf diesen 2D-Oberflächen zu ermöglichen, die mit der 3D-Umgebung interagieren, bieten Sie Hilfsprogramme, um diese Interaktion zu ermöglichen. Das grundlegendes Verständnis von Szenen bietet derzeit zwei Funktionen, _ *findcentermustplacement** und **getsurfakemask**. Findcentermostplacement ist eine API auf hoher Ebene, die eine Position auf dem Quad sucht, an der ein Objekt platziert werden kann, und versucht, den optimalen Speicherort für das Objekt zu finden, das sicherstellt, dass das von Ihnen bereitgestellte Begrenzungsfeld auf der zugrunde liegenden Oberfläche bleibt.

> [!NOTE]
> Die Koordinaten der Ausgabe sind relativ zum Quad in "Quad-Space", wobei die obere linke Ecke (x = 0, y = 0) ist, ebenso wie bei anderen Windows-Rect-Typen. Berücksichtigen Sie dies, wenn Sie mit den Ursprüngen ihrer eigenen Objekte arbeiten. 

Im folgenden Beispiel wird gezeigt, wie Sie den am häufigsten ersetzbaren Speicherort suchen und ein – Hologramm für das Vierfache verankern.

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

Die Schritte 1-4 sind stark von Ihrem speziellen Framework/der Implementierung abhängig, die Designs sollten jedoch ähnlich sein. Es ist wichtig zu beachten, dass das Vierfache eine begrenzte 2D-Ebene darstellt, die im Raum lokalisiert wird. Wenn Ihr Modul/Framework weiß, wo das Vierfache ist, und die Objekte in Relation zum Quad Hogen, werden Ihre Hologramme in Bezug auf die reale Welt ordnungsgemäß gefunden. 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>Mesh

Meshes stellen geometrische Darstellungen von Objekten oder Umgebungen dar. Ähnlich wie bei der [räumlichen Zuordnung](../../design/spatial-mapping.md)verwendet Mesh-Index-und Vertex-Daten, die für jedes räumliche Oberflächen Mesh bereitgestellt werden, dasselbe vertraute Layout wie der Scheitelpunkt und die Index Puffer, die zum Rendern von Dreiecksnetzen in allen modernen Rendering-APIs verwendet werden. Vertex-Positionen werden im Koordinatensystem von bereitgestellt `Scene` . Die spezifischen APIs, die zum Verweisen auf diese Daten verwendet werden, lauten wie folgt:

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

Der folgende Code enthält ein Beispiel für das Erstellen einer Dreiecks Liste aus der Mesh-Struktur:

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

Der Index/Scheitelpunkt Puffer muss >= der Index/Scheitelpunkt Anzahl sein, kann aber auch willkürlich skaliert werden, um eine effiziente Arbeitsspeicher Wiederverwendung zu ermöglichen.

### <a name="collidermesh"></a>Collidermesh

Szene Objekte ermöglichen den Zugriff auf Mesh-und Collider-Mesh-Daten über die Eigenschaften Meshes und collidermeshes. Diese Meshs Stimmen immer überein, was bedeutet, dass der Index der ' Netzen '-Eigenschaft die gleiche Geometrie darstellt wie der Index ' Index ' der ' collidermeshes '-Eigenschaft. Wenn die Runtime/das Objekt Collider-Meshes unterstützt, erhalten Sie garantiert das niedrigste Polygon mit der höchsten anordnen, und es wird empfohlen, collidermeshes zu verwenden, wenn die Anwendung Kollisionen verwenden würde. Wenn das System keine Kollisionen unterstützt, ist das in collidermeshes zurückgegebene Mesh-Objekt dasselbe Objekt wie das Mesh, das Speicher Einschränkungen reduziert.

## <a name="developing-with-scene-understanding"></a>Entwickeln mit Szenen Verständnis

An diesem Punkt sollten Sie die wichtigsten Bausteine der Szene verstehen, die Laufzeit und SDK versteht. Der größte Teil der Leistungsfähigkeit und Komplexität liegt in Zugriffs Mustern, der Interaktion mit 3D-Frameworks und Tools, die zusätzlich zu diesen APIs verfasst werden können, um erweiterte Aufgaben wie räumliche Planung, Raumanalyse, Navigation, Physik usw. auszuführen. Wir hoffen, diese Beispiele in Beispielen zu erfassen, die Sie in die richtige Richtung bringen sollten, um Ihre Szenarios zu glänzen. Wenn es Beispiele oder Szenarios gibt, die wir nicht behandeln, informieren Sie uns, und wir versuchen, das Dokument/den Prototyp zu dokumentieren.

### <a name="where-can-i-get-sample-code"></a>Wo kann ich Beispielcode erhalten?

Szeneninformationen zum Beispielcode für Unity finden Sie auf unserer Seite mit der [Unity-Beispielseite](https://github.com/sceneunderstanding-microsoft/unitysample) . Diese Anwendung ermöglicht Ihnen die Kommunikation mit Ihrem Gerät und das Rendering der verschiedenen Szenen Objekte, oder Sie können eine serialisierte Szene auf Ihren PC laden und das Verständnis von Szenen ohne Gerät ermöglichen.

### <a name="where-can-i-get-sample-scenes"></a>Wo kann ich Beispiel Szenen erhalten?

Wenn Sie über eine HoloLens2 verfügen, können Sie jede Szene speichern, die Sie erfasst haben, indem Sie die Ausgabe von "computeserializedasync" in der Datei speichern und Sie in ihrer eigenen Weise deserialisieren. 

Wenn Sie nicht über ein HoloLens2-Gerät verfügen, aber mit Szenen Verständnis experimentieren möchten, müssen Sie eine vorab erfasste Szene herunterladen. Das Beispiel für Szenen Verständnis wird derzeit in serialisierten Szenen geliefert, die Sie herunterladen und in ihrer eigenen Weise verwenden können. Sie finden Sie hier:

[Szenen Einblick in Beispiel Szenen](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>Siehe auch

* [Räumliche Abbildung](../../design/spatial-mapping.md)
* [Grundlegendes zu Szenen](../../design/scene-understanding.md)
* [Unity-Beispiel](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)