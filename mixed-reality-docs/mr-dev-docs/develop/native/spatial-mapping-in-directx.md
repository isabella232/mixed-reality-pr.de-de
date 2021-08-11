---
title: Räumliche Abbildung in DirectX
description: Erfahren Sie, wie Sie die räumliche Zuordnung in Ihrer DirectX-App implementieren und wie Sie die Beispielanwendung für räumliche Karten im Universal Windows Platform SDK verwenden.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, räumliche Zuordnung, Umgebung, Interaktion, Directx, WinRT, API, Beispielcode, UWP, SDK, exemplarische Vorgehensweise
ms.openlocfilehash: e7f0735ea28703d3a9f18198901ffa5f06676f78b7b8962bf20824e05f793061
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198846"
---
# <a name="spatial-mapping-in-directx"></a>Räumliche Abbildung in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren nativen WinRT-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API empfohlen.](openxr-getting-started.md)**

In diesem Thema wird beschrieben, wie Sie die räumliche Zuordnung [in](../../design/spatial-mapping.md) Ihrer DirectX-App implementieren, einschließlich einer ausführlichen Erläuterung der Beispielanwendung für räumliche Karten, die mit dem Universal Windows Platform SDK gepackt ist.

In diesem Thema wird Code aus dem UWP-Codebeispiel [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) verwendet.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C++17-kompatiblem C++/WinRT, wie in der holografischen C++-Projektvorlage [verwendet.](creating-a-holographic-directx-project.md)  Die Konzepte sind für ein C++/WinRT-Projekt gleichwertig, obwohl Sie den Code übersetzen müssen.

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Räumliche Abbildung</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a>DirectX-Entwicklung – Übersicht

Bei der Entwicklung nativer Anwendungen für die räumliche Zuordnung werden die APIs im [Windows. Perception.Spatial-Namespace.](/uwp/api/Windows.Perception.Spatial) Diese APIs bieten Ihnen die vollständige Kontrolle über die Funktionalität der räumlichen Zuordnung auf die gleiche Weise, wie APIs für die räumliche Zuordnung von [Unity verfügbar gemacht werden.](../unity/spatial-mapping-in-unity.md)

### <a name="perception-apis"></a>Perception-APIs

Die primären Typen, die für die Entwicklung der räumlichen Zuordnung bereitgestellt werden, lauten wie folgt:
* [SpatialSurfaceObserver stellt](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) Informationen zu Oberflächen in anwendungsspezifischen Raumregionen in der Nähe des Benutzers in Form von SpatialSurfaceInfo-Objekten zur Verfügung.
* [SpatialSurfaceInfo](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) beschreibt eine einzelne bestehende räumliche Oberfläche, einschließlich einer eindeutigen ID, des Begrenzungsvolumens und des Zeitpunkts der letzten Änderung. Sie stellt auf Anforderung asynchron ein SpatialSurfaceMesh-Objekt zur Verfügung.
* [SpatialSurfaceMeshOptions enthält Parameter,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMeshOptions) die zum Anpassen der SpatialSurfaceMesh-Objekte verwendet werden, die von SpatialSurfaceInfo angefordert werden.
* [SpatialSurfaceMesh](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh) stellt die Gitternetzdaten für eine einzelne räumliche Oberfläche dar. Die Daten für Scheitelpunktpositionen, Scheitelpunktnormationen und Dreiecksindizes sind in SpatialSurfaceMeshBuffer-Memberobjekten enthalten.
* [SpatialSurfaceMeshBuffer](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMeshBuffer) umschließt einen einzelnen Typ von Gitternetzdaten.

Wenn Sie eine Anwendung mit diesen APIs entwickeln, sieht Ihr grundlegender Programmablauf wie folgt aus (wie in der unten beschriebenen Beispielanwendung gezeigt):
- **Einrichten von SpatialSurfaceObserver**
  - Rufen [Sie RequestAccessAsync auf,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver)um sicherzustellen, dass der Benutzer ihrer Anwendung die Berechtigung erteilt hat, die Räumliche Zuordnungsfunktionen des Geräts zu verwenden.
  - Instanziieren Sie ein SpatialSurfaceObserver-Objekt.
  - Rufen [Sie SetBoundingVolumes auf,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) um die Bereiche des Raums anzugeben, in denen Sie Informationen zu räumlichen Oberflächen wünschen. Sie können diese Regionen in Zukunft ändern, indem Sie diese Funktion erneut aufrufen. Jeder Bereich wird mithilfe eines [SpatialBoundingVolume angegeben.](/uwp/api/Windows.Perception.Spatial.SpatialBoundingVolume)
  - Registrieren Sie sich [für das ObservedSurfacesChanged-Ereignis,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) das immer dann ausspricht, wenn neue Informationen zu den räumlichen Oberflächen in den von Ihnen angegebenen Raumregionen verfügbar sind.
- **Verarbeiten von ObservedSurfacesChanged-Ereignissen**
  - Rufen Sie in Ihrem Ereignishandler [GetObservedSurfaces](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) auf, um eine Karte von SpatialSurfaceInfo-Objekten zu empfangen. Mithilfe dieser Karte können Sie Ihre Datensätze aktualisieren, welche räumlichen Oberflächen in der Umgebung [des Benutzers vorhanden sind.](../../design/spatial-mapping.md#mesh-caching)
  - Für jedes SpatialSurfaceInfo-Objekt können Sie [TryGetBounds](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) abfragen, um die räumlichen Ausmaße der Oberfläche zu bestimmen, die in einem Raumkoordinatensystem Ihrer Wahl ausgedrückt werden. [](../../design/coordinate-systems.md)
  - Wenn Sie eine räumliche Oberfläche anfordern möchten, rufen Sie [TryComputeLatestMeshAsync auf.](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) Sie können Optionen angeben, die die Dichte von Dreiecken und das Format der zurückgegebenen Gitternetzdaten angeben.
- **Empfangs- und Prozessgitternetz**
  - Jeder Aufruf von TryComputeLatestMeshAsync gibt asynchron ein SpatialSurfaceMesh-Objekt zurück.
  - Über dieses Objekt können Sie auf die enthaltenen SpatialSurfaceMeshBuffer-Objekte zugreifen, wodurch Sie auf die Dreiecksindizes, Scheitelpunktpositionen und Scheitelpunktnormle des Gittermodells zugreifen können, wenn Sie sie anfordern. Diese Daten werden in einem Format vorliegen, das direkt mit den [Direct3D 11-APIs](/windows/win32/api/d3d11/nf-d3d11-id3d11device-createbuffer) kompatibel ist, die zum Rendern von Gittern verwendet werden.
  - Von hier aus kann Ihre [](../../design/spatial-mapping.md#mesh-processing) Anwendung optional die Gitternetzdaten analysieren oder verarbeiten und für Rendering und physikalische [Raycasting und Kollisionen verwenden.](../../design/spatial-mapping.md#raycasting-and-collision) [](../../design/spatial-mapping.md#rendering)
  - Ein wichtiges Zu beachtende Detail ist, dass Sie eine Skala auf die Vertexpositionen des Gitters anwenden müssen (z. B. im Vertex-Shader, der zum Rendern der Gitternetze verwendet wird), um sie aus den optimierten Ganzzahleinheiten, in denen sie im Puffer gespeichert sind, in Meter zu konvertieren. Sie können diese Skalierung abrufen, indem Sie [VertexPositionScale aufrufen.](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh)

### <a name="troubleshooting"></a>Problembehandlung
* Vergessen Sie nicht, Gittermodell-Vertexpositionen in Ihrem Vertex-Shader mithilfe der von [SpatialSurfaceMesh.VertexPositionScale zurückgegebenen Skala zu skalieren.](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Exemplarische Vorgehensweise für code sample spatial mapping (Codebeispiel für räumliche Zuordnung)

Das [Holographic Spatial Mapping-Codebeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) enthält Code, mit dem Sie mit dem Laden von Oberflächengittern in Ihre App beginnen können, einschließlich der Infrastruktur zum Verwalten und Rendern von Oberflächengittern.

Nun erfahren Sie, wie Sie Ihrer DirectX-App eine Funktion für die Oberflächenzuordnung hinzufügen. Sie können diesen Code [](creating-a-holographic-directx-project.md) zu Ihrem Windows Holographic-App-Vorlagenprojekt hinzufügen, oder Sie können den Code durch das oben genannte Codebeispiel durchsuchen. Dieses Codebeispiel basiert auf der Windows Holographic-App-Vorlage.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Einrichten Ihrer App für die Verwendung der spatialPerception-Funktion

Ihre App kann die Räumliche Zuordnungsfunktion verwenden. Dies ist erforderlich, da das räumliche Netz eine Darstellung der Umgebung des Benutzers ist, die als private Daten betrachtet werden kann. Deklarieren Sie diese Funktion in der Datei package.appxmanifest für Ihre App. Ein Beispiel:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

Die Funktion stammt aus dem **uap2-Namespace.** Um Zugriff auf diesen Namespace in Ihrem Manifest zu erhalten, fügen Sie ihn als *xlmns-Attribut* in das &lt; Package> ein. Ein Beispiel:

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Überprüfen der Unterstützung für räumliche Zuordnungsfeatures

Windows Mixed Reality unterstützt eine Vielzahl von Geräten, einschließlich Geräten, die keine räumliche Zuordnung unterstützen. Wenn Ihre App die räumliche Zuordnung verwenden kann oder die räumliche Zuordnung verwenden muss, um Funktionen zur Verfügung zu stellen, sollte sie überprüfen, ob die räumliche Zuordnung unterstützt wird, bevor sie versucht, sie zu verwenden. Wenn ihre Mixed Reality-App z. B. eine räumliche Zuordnung erfordert, sollte eine Meldung angezeigt werden, die diesen Effekt hat, wenn ein Benutzer versucht, sie auf einem Gerät ohne räumliche Zuordnung zu verwenden. Oder Ihre App kann eine eigene virtuelle Umgebung statt der Umgebung des Benutzers rendern und so eine Umgebung bereitstellen, die dem ähnelt, was geschieht, wenn die räumliche Zuordnung verfügbar wäre. In jedem Fall ermöglicht diese API Ihrer App, sich darüber im Klaren zu sein, wenn sie keine räumlichen Zuordnungsdaten abrufen und nicht in der richtigen Weise reagiert.

Um das aktuelle Gerät auf Unterstützung für räumliche Zuordnungen zu überprüfen, stellen Sie zunächst sicher, dass der UWP-Vertrag mindestens ebene 4 ist, und rufen Sie dann SpatialSurfaceObserver::IsSupported() auf. Dies wird im Kontext des [Holographic Spatial Mapping-Codebeispiels](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) wie hier erklärt. Der Support wird direkt vor dem Anfordern des Zugriffs überprüft.

Die SpatialSurfaceObserver::IsSupported()-API ist ab SDK-Version 15063 verfügbar. Wenn erforderlich, sollten Sie Ihr Projekt der Plattformversion 15063 neu zu geben, bevor Sie diese API verwenden.

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

Wenn der UWP-Vertrag kleiner als Ebene 4 ist, sollte die App so fortfahren, als wäre das Gerät in der Lage, räumliche Zuordnungen zu erstellen.

### <a name="request-access-to-spatial-mapping-data"></a>Anfordern des Zugriffs auf räumliche Zuordnungsdaten

Ihre App muss die Berechtigung für den Zugriff auf räumliche Zuordnungsdaten anfordern, bevor sie versucht, Oberflächenbeobachter zu erstellen. Hier sehen Sie ein Beispiel, das auf unserem Codebeispiel für die Oberflächenzuordnung basiert. Weitere Details finden Sie weiter unten auf dieser Seite:

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>Erstellen eines Oberflächenbeobachter

Der **namespace Windows::P erception::Spatial::Surfaces** enthält die [SpatialSurfaceObserver-Klasse,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) die ein oder mehrere Volumes beobachtet, die Sie in einem [SpatialCoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem)angeben. Verwenden Sie eine [SpatialSurfaceObserver-Instanz,](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) um in Echtzeit auf Oberflächengitterdaten zu zugreifen.

Von **AppMain.h:**

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Wie im vorherigen Abschnitt erwähnt, müssen Sie Zugriff auf räumliche Zuordnungsdaten anfordern, bevor Ihre App sie verwenden kann. Dieser Zugriff wird automatisch auf der HoloLens.

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

Als Nächstes müssen Sie den Oberflächenbeobachter konfigurieren, um ein bestimmtes Begrenzungsvolumen zu beobachten. Hier sehen wir ein Feld mit einer Länge von 20 x 20 x 5 Metern, das am Ursprung des Koordinatensystems zentriert ist.

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

Sie können stattdessen mehrere begrenzungsgebundene Volumes festlegen.

*Dies ist pseudocode:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

Es ist auch möglich, andere begrenzungsgebundene Formen zu verwenden, z. B. ein Ansichtsfrustum oder ein Begrenzungsfeld, das nicht an der Achse ausgerichtet ist.

*Dies ist pseudocode:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Wenn Ihre App etwas anderes tun muss, wenn keine Oberflächenzuordnungsdaten verfügbar sind, können Sie Code schreiben, um auf  den Fall zu reagieren, dass [SpatialPerceptionAccessStatus](/uwp/api/Windows.Perception.Spatial.SpatialPerceptionAccessStatus) nicht zulässig ist. Dies ist beispielsweise auf PCs mit angefügten immersiven Geräten nicht zulässig, da diese Geräte keine Hardware für die räumliche Zuordnung haben. Für diese Geräte sollten Sie sich stattdessen auf die räumliche Phase verlassen, um Informationen zur Umgebung und Gerätekonfiguration des Benutzers zu erhalten.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Initialisieren und Aktualisieren der Surface Mesh-Auflistung

Wenn der Oberflächenbeobachter erfolgreich erstellt wurde, können wir unsere Oberflächengitternetz-Sammlung weiter initialisieren. Hier verwenden wir die Pullmodell-API, um den aktuellen Satz beobachteter Oberflächen sofort zu erhalten:

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

Es ist auch ein Pushmodell verfügbar, um Oberflächengittermodelldaten zu erhalten. Sie können Ihre App so entwerfen, dass sie nur das Pullmodell verwendet, wenn Sie sich dafür entscheiden. In diesem Fall fragen Sie daten so oft ab – z. B. einmal pro Frame – oder während eines bestimmten Zeitraums, z. B. während der Spieleinrichtung. Wenn ja, benötigen Sie den obigen Code.

In unserem Codebeispiel haben wir uns entschieden, die Verwendung beider Modelle zu veranschaulichen. Hier abonnieren wir ein Ereignis, um aktuelle Surface Mesh-Daten zu empfangen, wenn das System eine Änderung erkennt.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Unser Codebeispiel ist auch so konfiguriert, dass es auf diese Ereignisse reagiert. Im Folgenden wird erläutert, wie wir dies tun.

**HINWEIS:** Dies ist möglicherweise nicht die effizienteste Methode für Ihre App, um Meshdaten zu verarbeiten. Dieser Code wurde aus Gründen der Übersichtlichkeit geschrieben und ist nicht optimiert.

Die Surface Mesh-Daten werden in einer schreibgeschützten Karte bereitgestellt, in der [SpatialSurfaceInfo-Objekte](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) mit [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) als Schlüsselwerte gespeichert werden.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Um diese Daten zu verarbeiten, suchen wir zuerst nach Schlüsselwerten, die nicht in unserer Sammlung enthalten sind. Details dazu, wie die Daten in unserer Beispiel-App gespeichert werden, werden später in diesem Thema vorgestellt.

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

Wir müssen auch Oberflächengitternetze entfernen, die sich in unserer Surface Mesh-Sammlung befinden, aber nicht mehr in der Systemsammlung sind. Dazu müssen wir etwas tun, das dem Gegenteil von dem ähnelt, was wir gerade zum Hinzufügen und Aktualisieren von Gitternetzen gezeigt haben. wir durchlaufen die Sammlung unserer App und überprüfen, ob sich die **guid** in der Systemsammlung befindet. Wenn sie sich nicht in der Systemsammlung befindet, entfernen wir sie aus unserer.

Über unseren Ereignishandler in AppMain.cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

Die Implementierung der Meshbereinigung in RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Abrufen und Verwenden von Surface Mesh-Datenpuffern

Das Abrufen der Surface Mesh-Informationen war so einfach wie das Abrufen einer Datensammlung und das Verarbeiten von Updates für diese Sammlung. Im Folgenden wird ausführlich erläutert, wie Sie die Daten verwenden können.

In unserem Codebeispiel haben wir uns entschieden, die Oberflächengitternetze für das Rendering zu verwenden. Dies ist ein häufiges Szenario zum Verdecken von Hologrammen hinter realen Oberflächen. Sie können auch die Gitternetze rendern oder verarbeitete Versionen rendern, um dem Benutzer zu zeigen, welche Bereiche des Raumes gescannt werden, bevor Sie mit der Bereitstellung von App- oder Spielfunktionen beginnen.

Im Codebeispiel wird der Prozess gestartet, wenn Surface Mesh-Updates vom Ereignishandler empfangen werden, den wir im vorherigen Abschnitt beschrieben haben. Die wichtige Codezeile in dieser Funktion ist der Aufruf zum Aktualisieren des *Oberflächengitternetzes:* Zu diesem Zeitpunkt haben wir die Gitternetzinformationen bereits verarbeitet, und wir sind im Begriff, den Scheitelpunkt und die Indexdaten für die Verwendung nach Bedarf abzurufen.

Über RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

Unser Beispielcode ist so konzipiert, dass die Datenklasse **SurfaceMesh** die Verarbeitung und das Rendern von Gitternetzdaten übernimmt. Diese Gitternetze sind das, wofür **realtimeSurfaceMeshRenderer** tatsächlich eine Karte speichert. Jeder verfügt über einen Verweis auf spatialSurfaceMesh, von dem er stammt, sodass Sie ihn jederzeit verwenden können, wenn Sie auf den Gitterpunkt oder Indexpuffer zugreifen oder eine Transformation für das Gitternetz abrufen müssen. Vorerst kennzeichnen wir das Gitternetz, dass ein Update erforderlich ist.

Über SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

Wenn das Gitternetz das nächste Mal aufgefordert wird, sich selbst zu zeichnen, wird zuerst das Flag überprüft. Wenn ein Update erforderlich ist, werden der Scheitelpunkt und die Indexpuffer auf der GPU aktualisiert.

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

Zunächst werden die Rohdatenpuffer ermittelt:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Anschließend erstellen wir Direct3D-Gerätepuffer mit den Gitternetzdaten, die vom HoloLens bereitgestellt werden:

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**HINWEIS:** Die im vorherigen Codeausschnitt verwendete CreateDirectXBuffer-Hilfsfunktion finden Sie im Codebeispiel für die Surface-Zuordnung: SurfaceMesh.cpp, GetDataFromIBuffer.h. Jetzt ist die Erstellung der Geräteressource abgeschlossen, und das Gitternetz wird als geladen betrachtet und kann aktualisiert und gerendert werden.

### <a name="update-and-render-surface-meshes"></a>Aktualisieren und Rendern von Oberflächengitternetzen

Unsere SurfaceMesh-Klasse verfügt über eine spezielle Updatefunktion. Jedes [SpatialSurfaceMesh](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh) verfügt über eine eigene Transformation, und unser Beispiel verwendet das aktuelle Koordinatensystem für unseren **SpatialStationaryReferenceFrame,** um die Transformation zu erhalten. Anschließend wird der Modellkonstantenpuffer auf der GPU aktualisiert.

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

Wenn Es an der Zeit ist, Oberflächengitternetze zu rendern, führen wir vor dem Rendern der Sammlung einige Vorbereitungen durch. Wir richten die Shaderpipeline für die aktuelle Renderingkonfiguration ein, und wir richten die Eingabeassemblierungsphase ein. Die Holografische Kamerahilfsklasse **CameraResources.cpp** hat den Ansichts-/Projektionskonstantenpuffer bereits eingerichtet.

Über **RealtimeSurfaceMeshRenderer::Render**:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

Sobald dies erfolgt ist, durchlaufen wir unsere Gitternetze und weisen jedes Gitternetz an, sich selbst zu zeichnen. **HINWEIS:** Dieser Beispielcode ist nicht für die Verwendung von Frustum-Culling optimiert. Sie sollten dieses Feature jedoch in Ihre App einschließen.

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

Die einzelnen Gittermodelle sind für das Einrichten des Vertex- und Indexpuffers, des Schritts und des Modelltransformationskonstantenpuffers verantwortlich. Wie beim drehenden Würfel in der Windows Holographic-App-Vorlage rendern wir mithilfe von Instanziierung in stereoskopische Puffer.

Über **SurfaceMesh::D raw:**

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>Renderingoptionen mit Surface Mapping

Das Surface Mapping-Codebeispiel bietet Code für das rein verdeckungsbasierte Rendering von Oberflächengitternetzdaten und für das Rendern von Oberflächengitternetzdaten auf dem Bildschirm. Welcher Pfad Sie auswählen – oder beides – hängt von Ihrer Anwendung ab. In diesem Dokument werden beide Konfigurationen durchlaufen.

**Rendern von Verdeckungspuffern für holografische Effekte**

Löschen Sie zunächst die Renderzielansicht für die aktuelle virtuelle Kamera.

Über AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Dies ist ein Vorrenderingdurchlauf. Hier erstellen wir einen Verdeckungspuffer, indem wir den Gitternetzrenderer bitten, nur die Tiefe zu rendern. In dieser Konfiguration fügen wir keine Renderzielansicht an, und der Gitternetzrenderer legt die Pixel-Shaderstufe auf **nullptr** fest, sodass die GPU keine Pixel zeichnet. Die Geometrie wird in den Tiefenpuffer gerastet, und die Grafikpipeline wird dort beendet.

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

Wir können Hologramme mit einem zusätzlichen Tiefentest für den Verdeckungspuffer der Oberflächenzuordnung zeichnen. In diesem Codebeispiel rendern wir Pixel auf dem Cube in einer anderen Farbe, wenn sie sich hinter einer Oberfläche befinden.

Über AppMain.cpp:

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

Basierend auf Code aus SpecialEffectPixelShader.hlsl:

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**Hinweis:** Informationen zur **GatherDepthLess-Routine** finden Sie im Codebeispiel für die Oberflächenzuordnung: SpecialEffectPixelShader.hlsl.

**Rendern von Oberflächengitternetzdaten für die Anzeige**

Wir können auch einfach die Oberflächengitternetze in die Stereoanzeigepuffer zeichnen. Wir haben uns dafür entschieden, vollständige Gesichter mit Beleuchtung zu zeichnen, aber Sie können wireframe zeichnen, Gittermodelle vor dem Rendern verarbeiten, eine Texturkarte anwenden usw.

Hier weist unser Codebeispiel den Gitternetzrenderer an, die Auflistung zu zeichnen. Dieses Mal geben wir keinen reinen Tiefendurchlauf an, sondern fügen einen Pixelshader an und schließen die Renderingpipeline mit den Zielen ab, die wir für die aktuelle virtuelle Kamera angegeben haben.

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>Siehe auch
* [Erstellen eines holographischen DirectX-Projekts](creating-a-holographic-directx-project.md)
* [Windows. Perception.Spatial-API](/uwp/api/Windows.Perception.Spatial)