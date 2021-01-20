---
title: Koordinatensysteme in DirectX
description: Erfahren Sie mehr über Koordinatensysteme in DirectX und gemischte Realität mit räumlichen Locators, Referenz Frames und räumlichen Ankern.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Gemischte Realität, räumlicher Locator, räumlicher Referenzrahmen, räumliches Koordinatensystem, räumliche Phase, Beispielcode, Bildstabilisierung, räumlicher Anker, räumlicher Anker Speicher, nach Verfolgungs Verlust, Exemplarische Vorgehensweise, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 7cf463e4c3bb9b2fe06c834376eb46e3ee20c1ee
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581071"
---
# <a name="coordinate-systems-in-directx"></a>Koordinatensysteme in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren WinRT-APIs.  Bei neuen nativen App-Projekten wird die Verwendung der **[openxr-API](openxr-getting-started.md)** empfohlen.

[Koordinatensysteme](../../design/coordinate-systems.md) bilden die Grundlage für das räumliche Verständnis von Windows Mixed Reality-APIs.

Die heutigen VR-oder Einzel Raum-VR-Geräte richten ein Primäres Koordinatensystem für den nach verfolgten Speicher ein. Geräte mit gemischter Realität (z. b. hololens) sind für große, nicht definierte Umgebungen konzipiert, und das Gerät ermittelt und erfährt seine Umgebung, während der Benutzer Sie durchläuft. Das Gerät passt sich an, um das Wissen über die Räume des Benutzers ständig zu verbessern, führt jedoch zu Koordinatensystemen, die die Beziehung zwischen der Lebensdauer der apps untereinander ändern. Die gemischte Realität von Windows unterstützt ein breites Spektrum an Geräten, die von sitzenden immersiven Headsets durch weltweit angehängte Referenzrahmen reichen.

>[!NOTE]
>Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C + +17-kompatiblen C++/WinRT, wie Sie in der [C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.  Die Konzepte sind äquivalent zu einem C++/WinRT-Projekt. Sie müssen jedoch den Code übersetzen.

## <a name="spatial-coordinate-systems-in-windows"></a>Räumliche Koordinatensysteme in Windows

Der Kerntyp, der in Bezug auf echte Koordinatensysteme in Windows verwendet wird, ist das <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">spatialcoordinatesystem</a>. Eine Instanz dieses Typs stellt ein beliebiges Koordinatensystem dar, das eine Methode zum erhalten von Transformationsmatrix Daten bereitstellt, die Sie zum Transformieren zwischen zwei Koordinatensystemen verwenden können, ohne die Details der einzelnen Koordinaten zu verstehen.

Methoden, die räumliche Informationen zurückgeben, akzeptieren einen spatialcoordinatesystem-Parameter, um Ihnen die Entscheidung über das Koordinatensystem zu ermöglichen, in dem die zurück zugebende Koordinaten am nützlichsten sind. Räumliche Informationen werden als Punkte, Strahlen oder Volumes in der Benutzerumgebung dargestellt, und die Einheiten für diese Koordinaten sind immer in Meter.

Ein spatialcoordinatesystem verfügt über eine dynamische Beziehung mit anderen Koordinatensystemen, einschließlich derjenigen, die die Position des Geräts darstellen. An jedem Punkt kann das Gerät einige Koordinatensysteme und keine anderen suchen. Für die meisten Koordinatensysteme muss Ihre APP bereit sein, Zeiträume zu verarbeiten, in denen Sie nicht gefunden werden können.

Die Anwendung sollte spatialcoordinatesystems nicht direkt erstellen, stattdessen sollten Sie über die perception-APIs genutzt werden. Es gibt drei primäre Quellen für Koordinatensysteme in den perception-APIs, von denen jede einem auf der Seite [Koordinatensysteme](../../design/coordinate-systems.md) beschriebenen Konzept zugeordnet ist:
* Um einen stationären Verweis Rahmen zu erhalten, erstellen Sie ein <a href="/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">spatialstationaryframeofreferenzierungspaar</a> , oder rufen Sie ein aus der aktuellen <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">spatialstageframeofreferenzierung</a>ab.
* Um einen räumlichen Anker zu erhalten, erstellen Sie ein <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">spatialanchor</a>.
* Um einen angefügten Frame des Verweises zu erhalten, erstellen Sie ein <a href="/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">spatidepanorattachedframeofreferenzierungsverzeichnis</a>.

Alle Koordinatensysteme, die von diesen Objekten zurückgegeben werden, sind mit der rechten Hand, mit + y nach oben, + x nach rechts und + z rückwärts. Sie können sich merken, welche Richtung die positive z-Achse zeigt, indem Sie die Finger entweder von Links oder rechts in der positiven x-Richtung zeigen und in die positive y-Richtung hinein. Die Richtung, auf die sich der Ziehpunkt von Ihnen befindet, ist die Richtung, auf die die positive z-Achse für dieses Koordinatensystem zeigt. In der folgenden Abbildung werden diese beiden Koordinatensysteme veranschaulicht.

![Linke und Rechte Koordinatensysteme](images/left-hand-right-hand.gif)<br>
*Linke und Rechte Koordinatensysteme*

Verwenden Sie die <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">spatizuweisung</a> -Klasse, um entweder einen angefügten oder einen stationären Verweis Rahmen zu erstellen, der auf der Grundlage der hololens-Position in ein spatialcoordinatesystem Bootstrap. Fahren Sie mit dem nächsten Abschnitt fort, um weitere Informationen zu diesem Vorgang zu erhalten.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Platzieren von holograms weltweit mithilfe einer räumlichen Phase

Das Koordinatensystem für nicht transparente Windows Mixed Reality-immersive Headsets wird mithilfe der statischen <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">spatialstageframeofreferen:: Current</a> -Eigenschaft aufgerufen. Diese API bietet Folgendes:

* Ein Koordinatensystem
* Informationen dazu, ob der Player oder mobil ist
* Die Grenze eines sicheren Bereichs zum durchlaufen, wenn der Player mobil ist
* Ein Hinweis darauf, ob das Headset direktional ist. 
* Ein Ereignishandler für Aktualisierungen der räumlichen Phase.

Zuerst erhalten wir die räumliche Phase und abonnieren Updates für Sie: 

Code für die **Initialisierung räumlicher Phasen**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

In der OnCurrentChanged-Methode sollte Ihre APP die räumliche Phase überprüfen und die Benutzerumgebung aktualisieren. In diesem Beispiel stellen wir eine Visualisierung der Stufen Begrenzung und der vom Benutzer angegebenen Startposition sowie den Bereich der Ansicht und den Bereich der Verschiebungs Eigenschaften der Stufe bereit. Wir greifen auch auf unser eigenes stationäres Koordinatensystem zurück, wenn eine Phase nicht bereitgestellt werden kann.


Code für das **Update für räumliche Stufen**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

Die Reihe der Scheitel Punkte, die die Stufen Begrenzung definieren, werden im Uhrzeigersinn bereitgestellt. Die Windows Mixed Reality-Shell zeichnet einen Fence an der Grenze, wenn sich der Benutzer nähert, aber Sie möchten vielleicht den zu verwendbar enden Bereich für Ihre eigenen Zwecke verkleinern. Der folgende Algorithmus kann verwendet werden, um die Stufe zu verkleinern.


Code für die **phangularisierung in räumlicher Phase**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Platzieren von holograms auf der Welt mithilfe eines stationären Frame Rahmens

Die [spatialstationaryframeofreferenzierungsklasse](/uwp/api/Windows.Perception.Spatial.SpatialStationaryFrameOfReference) stellt einen Frame von Reference dar, der relativ zur Benutzerumgebung [stationär bleibt](../../design/coordinate-systems.md#stationary-frame-of-reference) , wenn der Benutzer sich bewegt. Dieser Frame des Verweises priorisiert die Stabilität der Koordinaten in der Nähe des Geräts. Eine zentrale Verwendung eines spatialstationaryframeofreferenzierungssystems besteht darin, beim Rendern von holograms als das zugrundeliegende weltweite Koordinatensystem in einer Rendering-Engine zu fungieren.

Um eine spatialstationaryframeofreferenzierung abzurufen, verwenden Sie die [spatizuweisung](/uwp/api/Windows.Perception.Spatial.SpatialLocator) -Klasse und den Aufruf von " [foratestationaryframeofreferenceatcurrentlocation](/uwp/api/Windows.Perception.Spatial.SpatialLocator)".

Aus dem Windows Holographic-App-Vorlagen Code:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Stationäre Verweis Rahmen sind so konzipiert, dass Sie eine am besten geeignete Position relativ zum gesamten Bereich bereitstellen. Einzelne Positionen innerhalb dieses Bezugsrahmens dürfen leicht abweichen. Dies ist normal, da das Gerät mehr über die Umgebung erfährt.
* Wenn die genaue Platzierung einzelner Hologramme erforderlich ist, sollte ein spatialanchor verwendet werden, um das einzelne – Hologramm an eine Position in der realen Welt zu verankern, z. b. ein Punkt, den der Benutzer als besonderes Interesse andeutet. Anker Positionen werden nicht abweichen, Sie können jedoch korrigiert werden. der Anker verwendet die korrigierte Position, beginnend im nächsten Frame, nachdem die Korrektur erfolgt ist.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Platzieren von holograms weltweit mithilfe räumlicher Anker

[Räumliche Anker](../../design/coordinate-systems.md#spatial-anchors) sind eine gute Möglichkeit, Hologramme an einer bestimmten Stelle in der realen Welt zu platzieren, wobei das System sicherstellt, dass der Anker im Laufe der Zeit vorhanden ist. In diesem Thema wird erläutert, wie ein Anker erstellt und verwendet wird und wie mit Anker Daten gearbeitet wird.

Sie können ein spatialanchor an beliebiger Position und Ausrichtung innerhalb des spatialcoordinatesystem Ihrer Wahl erstellen. Das Gerät muss in der Lage sein, dieses Koordinatensystem zu einem bestimmten Zeitpunkt zu finden, und das System darf den Grenzwert räumlicher Anker nicht erreicht haben.

Sobald das Koordinatensystem eines räumalanchors definiert ist, wird es ständig angepasst, um die genaue Position und Ausrichtung der ursprünglichen Position zu erhalten. Anschließend können Sie mit diesem spatialanchor holograms so darstellen, dass Sie in der Benutzerumgebung an diesem exakten Speicherort korrigiert werden.

Die Auswirkungen der Anpassungen, die den Anker an Ort halten, werden vergrößert, wenn sich die Entfernung vom Anker vergrößert. Sie sollten das Rendern von Inhalten in Relation zu einem Anker vermeiden, der mehr als ungefähr 3 Meter vom Ursprung dieses Ankers ist.

Die [CoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) -Eigenschaft ruft ein Koordinatensystem ab, mit dem Sie Inhalte relativ zum Anker platzieren können, wobei eine Beschleunigung angewendet wird, wenn das Gerät den genauen Speicherort des Ankers anpasst.

Verwenden Sie die [rawcoordinatesystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) -Eigenschaft und das zugehörige [rawcoordinatesystemadjusted](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) -Ereignis, um diese Anpassungen selbst zu verwalten.

### <a name="persist-and-share-spatial-anchors"></a>Beibehalten und freigeben räumlicher Anker

Sie können ein spatialanchor lokal mithilfe der [spatialanchorstore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore) -Klasse beibehalten und dann in einer zukünftigen App-Sitzung auf demselben hololens-Gerät wiederholen.

Mithilfe der <a href="/azure/spatial-anchors/overview" target="_blank">räumlichen Anker von Azure</a>können Sie einen permanenten cloudenanchor von einem lokalen spatialanchor erstellen, das Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.  Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers über mehrere Geräte hinweg kann jeder Benutzer in Echtzeit Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Standort gerendert werden. 

Sie können auch <a href="/azure/spatial-anchors/overview" target="_blank">räumliche Azure-Anker</a> für die asynchrone – Hologramm-Persistenz über hololens-, IOS-und Android-Geräte verwenden.  Durch die gemeinsame Nutzung eines permanenten clouddiensts können mehrere Geräte im Lauf der Zeit dasselbe persistente Hologramm beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Um mit der Einführung von freigegebenen Erfahrungen in der hololens-APP zu beginnen, testen Sie den Schnellstart mit den fünfminütigen <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchor hololens</a>.

Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">Anker in hololens erstellen und lokalisieren</a>.  Exemplarische Vorgehensweisen sind auch für <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android und IOS</a> verfügbar, sodass Sie dieselben Anker auf allen Geräten gemeinsam verwenden können.

### <a name="create-spatialanchors-for-holographic-content"></a>Erstellen von spatialanchor für Holographic Content

In diesem Codebeispiel wurde die Windows Holographic-App-Vorlage so geändert, dass Anker erstellt werden, wenn die **gedrückte** Bewegung erkannt wird. Der Cube wird dann während des Renderpass am Anker platziert.

Da mehrere Anker von der Hilfsklasse unterstützt werden, können wir so viele Cubes platzieren, wie wir dieses Codebeispiel verwenden möchten.

> [!NOTE]
> Die IDs für Anker sind etwas, das Sie in ihrer App steuern. In diesem Beispiel haben wir ein Benennungs Schema erstellt, das auf der Grundlage der Anzahl der Anker basiert, die derzeit in der Auflistung von Ankern der APP gespeichert sind.

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Asynchrones Laden und Zwischenspeichern von spatialanchorstore

Sehen wir uns an, wie Sie eine samplespatialanchorhelper-Klasse schreiben, die diese Persistenz behandelt, einschließlich:
* Speichern einer Auflistung von in-Memory-Ankern, indiziert von einem Platform:: String-Schlüssel.
* Anker aus dem spatialanchorstore des Systems werden geladen, die von der lokalen Auflistung im Arbeitsspeicher getrennt aufbewahrt werden.
* Speichern der lokalen in-Memory-Auflistung von Ankern im spatialanchorstore, wenn die App dafür entscheidet.

Im folgenden wird beschrieben, wie Sie [spatialanchor](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) -Objekte im [spatialanchorstore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)speichern.

Wenn die Klasse gestartet wird, fordern wir den spatialanchorstore asynchron an. Dies umfasst die System-e/a, da die API den Anker Speicher lädt, und diese API wird asynchron erstellt, sodass die e/a-Vorgänge nicht blockiert werden.

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

Sie erhalten einen spatialanchorstore, den Sie zum Speichern der Anker verwenden können. Dies ist ein imapview, das Schlüsselwerte, die Zeichen folgen sind, mit Datenwerten, die spatialanchor sind, verknüpft. In unserem Beispielcode speichern wir dies in einer privaten Klassenmember-Variablen, auf die über eine öffentliche Funktion unserer Hilfsklasse zugegriffen werden kann.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>Vergessen Sie nicht, die Suspend/Resume-Ereignisse anzuschließen, um den Anker Speicher zu speichern und zu laden.

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>Inhalt im Anker Speicher speichern

Wenn das System Ihre APP anhält, müssen Sie Ihre räumlichen Anker im Anker Speicher speichern. Sie können auch die Anker im Anker Speicher zu einem anderen Zeitpunkt speichern, da Sie für die Implementierung Ihrer APP erforderlich sind.

Wenn Sie bereit sind, die in-Memory-Anker im spatialanchorstore zu speichern, können Sie die Sammlung durchlaufen und versuchen, jede einzelne zu speichern.

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Inhalt aus dem Anker Speicher laden, wenn die APP fortgesetzt wird

Sie können gespeicherte Anker im anchorstore wiederherstellen, indem Sie Sie aus der imapview des Anker Stores in ihren eigenen in-Memory Database von spatialanchor übertragen, wenn Ihre APP fortgesetzt wird, oder zu einem beliebigen Zeitpunkt.

Um Anker aus dem spatialanchorstore wiederherzustellen, stellen Sie jeden, für den Sie sich interessieren, an ihrer eigenen in-Memory-Sammlung wieder her.

Sie benötigen eine eigene in-Memory Database von spatialanchor, um Zeichen folgen den spatialanchor zuzuordnen, die Sie erstellen. In unserem Beispielcode wählen wir die Verwendung eines Windows:: Foundation:: Collections:: IMap zum Speichern der Anker aus, wodurch die Verwendung desselben Schlüssels und Datenwerts für den spatialanchorstore vereinfacht wird.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Ein Anker, der wieder hergestellt wird, ist möglicherweise nicht sofort verwendbar. Beispielsweise kann es sich um einen Anker in einem separaten Raum oder in einem anderen Gebäude handeln. Anker, die aus dem anchorstore abgerufen werden, sollten vor deren Verwendung auf die Erreichbarkeit getestet werden.

<br>

>[!NOTE]
>In diesem Beispielcode rufen wir alle Anker aus dem anchorstore ab. Dies ist keine Anforderung. Ihre APP könnte auch eine bestimmte Teilmenge von Ankern auswählen und auswählen, indem Sie Zeichen folgen Schlüsselwerte verwenden, die für Ihre Implementierung von Bedeutung sind.

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>Den Anker Speicher bei Bedarf löschen

Manchmal müssen Sie den App-Status löschen und neue Daten schreiben. Im folgenden wird erläutert, wie Sie mit dem [spatialanchorstore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)Vorgehen.

Mit unserer Hilfsklasse ist es fast unnötig, die Clear-Funktion zu wrappen. Wir entscheiden uns hierfür in unserer Beispiel Implementierung, da unsere Hilfsklasse die Verantwortung für den Besitz der spatialanchorstore-Instanz erhält.

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Beispiel: Verknüpfen von Anker Koordinatensystemen mit stationären Reference Frame-Koordinatensystemen

Nehmen wir an, Sie haben einen Anker, und Sie möchten etwas im Koordinatensystem Ihres Ankers mit dem spatialstationaryreferenceframe verknüpfen, den Sie bereits für Ihre anderen Inhalte verwenden. Sie können [trygettransformto](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem) verwenden, um eine Transformation vom Koordinatensystem des Ankers zu der des stationären Referenzrahmens zu erhalten:

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

Dieser Prozess ist auf zweierlei Weise nützlich:
1. Es gibt Aufschluss darüber, ob die beiden Verweis Frames relativ zueinander verstanden werden können.
2. Wenn dies der Fall ist, stellt Sie eine Transformation bereit, um direkt von einem Koordinatensystem zum anderen zu wechseln.

Mit diesen Informationen haben Sie einen Einblick in die räumliche Beziehung zwischen den Objekten zwischen den beiden Referenz Frames.

Zum Rendern können Sie häufig bessere Ergebnisse erzielen, indem Sie Objekte entsprechend ihrem ursprünglichen Referenzrahmen oder Anker gruppieren. Führen Sie einen separaten Zeichnungs Durchlauf für jede Gruppe aus. Die Ansichts Matrizen sind für Objekte mit Modell Transformationen, die anfänglich mit demselben Koordinatensystem erstellt werden, genauer.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Erstellen von holograms mithilfe eines vom Gerät angefügten Referenzrahmens

Es gibt Zeiten, in denen ein – Hologramm geresgt werden soll, das an den Speicherort des Geräts [angehängt bleibt](../../design/coordinate-systems.md#attached-frame-of-reference) , z. b. ein Panel mit Debuginformationen oder eine Informations Meldung, wenn das Gerät nur seine Ausrichtung und nicht seine Position im Raum ermitteln kann. Hierfür wird ein angefügter Verweis Rahmen verwendet.

Die spatizuweisung-Klasse "spatichedframeofreferenzierungssysteme" definiert Koordinatensysteme, die relativ zum Gerät und nicht in der realen Welt sind. Dieser Frame verfügt über eine festgelegte Überschrift in Bezug auf die Benutzerumgebung, die in der Richtung angezeigt wird, die der Benutzer beim Erstellen des Verweis Rahmens aufzeigte. Danach sind alle Ausrichtungen in diesem Verweis Verweis relativ zu dieser festgelegten Überschrift, auch wenn der Benutzer das Gerät dreht.

Bei hololens befindet sich der Ursprung des Koordinatensystems dieses Frames im Mittelpunkt der Drehung des Benutzer Kopfes, sodass seine Position nicht von der Kopfdrehung betroffen ist. Ihre APP kann einen Offset relativ zu diesem Punkt angeben, um Hologramme vor dem Benutzer zu positionieren.

Verwenden Sie zum Abrufen eines spatizucatorattachedframeofreferenzierers die spatidepcator-Klasse, und nennen Sie "forateattachedframeofreferenceatspatitheiading".

Dies gilt für den gesamten Bereich von Windows Mixed Reality-Geräten.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Verwenden eines mit dem Gerät verbundenen Referenzrahmens

In diesen Abschnitten wird erläutert, was wir in der Windows Holographic-App-Vorlage geändert haben, um mit dieser API einen mit dem Gerät verknüpften Referenzrahmen zu aktivieren. Dieses "angefügte" – Hologramm funktioniert zusammen mit stationären oder verankerten holograms und kann auch verwendet werden, wenn die Position des Geräts vorübergehend nicht gefunden werden kann.

Zuerst haben wir die Vorlage so geändert, dass Sie ein spatidepaseorattachedframeofreferen-Objekt anstelle einer spatialstationaryframeofreferenzierung speichert:

Aus **holographictagalongsamplemain. h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Aus **holographictagalongsamplemain. cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Während des Updates erhalten wir nun das Koordinatensystem am Zeitstempel, der von mit der Frame Vorhersage abgerufen wurde.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Stellen Sie eine räumliche Zeiger Pose dar, und folgen Sie dem Benutzer.

Wir möchten, dass unser Beispiel – Hologramm dem [Blick](../../design/gaze-and-commit.md)des Benutzers folgt, ähnlich wie die Holographic Shell dem Blick des Benutzers folgen kann. Hierfür müssen wir spatialpointerpose aus dem gleichen Zeitstempel erhalten.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Diese spatialpointerpose verfügt über die Informationen, die erforderlich sind, um das – Hologramm entsprechend der [aktuellen Überschrift des Benutzers](gaze-in-directx.md)zu positionieren.

Für den Benutzerkomfort wird die lineare interpolung ("Lerp") verwendet, um die Änderung an der Position innerhalb eines bestimmten Zeitraums zu glätten. Dies ist für den Benutzer besser, als das – Hologramm auf seinen Blick zu sperren. Durch das lerping der Position des "Tag"-entlang des Hologramms können wir das Hologramm auch durch Dämpfen der Bewegung stabilisieren. Wenn wir diese Dämpfung nicht durchführen, würde der Benutzer den – Hologramm-Jitter sehen, weil er normalerweise als unwahrliche Bewegungen des Benutzer Kopfes angesehen wird.

Von **stationaryquadrenderer::P ositionhologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>Im Fall eines debuggingbereichs können Sie das Hologramm auf der Seite auf einen kleinen Wert zurücksetzen, damit die Ansicht nicht behindert wird. Im folgenden finden Sie ein Beispiel dafür, wie Sie dies tun können.

Für **stationaryquadrenderer::P ositionhologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>Das Hologramm drehen, um der Kamera zu begegnen

Es reicht nicht aus, um das Hologram zu positionieren, was in diesem Fall ein Vierfach ist. Wir müssen auch das Objekt drehen, um dem Benutzer zu begegnen. Diese Rotation tritt im Raum der Welt auf, da das – Hologramm durch diese Art des Abbilds ein Teil der Benutzerumgebung bleiben kann. Das Ansichts Leerraum-fakboardingvorgang ist nicht so komfortabel, da das – Hologramm in der Anzeige Ausrichtung gesperrt wird. in diesem Fall müssten Sie auch zwischen den linken und rechten Ansichts Matrizen interpolieren, um eine View-Space-Billboard-Transformation zu erhalten, die das Stereo Rendering nicht beeinträchtigt. Hier drehen wir die X-und Z-Achsen, um dem Benutzer zu begegnen.

Von **stationaryquadrenderer:: Update**:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>Rendering des angefügten holograms

In diesem Beispiel wählen wir auch das – Hologramm im Koordinatensystem von spatidepplatorattachedreferenceframe aus, in dem wir das – Hologramm positioniert haben. (Wenn wir uns für das Renderingsystem mit einem anderen Koordinatensystem entschieden hätten, müssten wir eine Transformation vom Koordinatensystem des mit dem Gerät verbundenen Verweis Rahmens an dieses Koordinatensystem abrufen.)

Aus **holographictagalongsamplemain:: Rendering**:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

Das ist alles! Das – Hologramm ist nun eine Position, die zwei Meter vor der Blick Richtung des Benutzers ist.

>[!NOTE]
>In diesem Beispiel werden auch weitere Inhalte geladen, siehe stationaryquadrenderer. cpp.

## <a name="handling-tracking-loss"></a>Behandeln von nach Verfolgungs Verlusten

Wenn das Gerät sich nicht auf der ganzen Welt finden kann, kann der APP-Verlust nachverfolgt werden. Windows Mixed Reality-apps sollten solche Unterbrechungen für das Positions Überwachungssystem verarbeiten können. Diese Unterbrechungen können beobachtet und Antworten erstellt werden, indem das locatabilitychanged-Ereignis im standardspaticator verwendet wird.

Aus **appmain:: abbildrfaden:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Wenn Ihre APP ein lochanabilitychanged-Ereignis empfängt, kann Sie das Verhalten nach Bedarf ändern. Beispielsweise kann Ihre APP im positionaltrackinginhibited-Zustand den normalen Betrieb anhalten und ein [Tag-entlang-– Hologramm](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) , das eine Warnmeldung anzeigt, darstellen.

Die Vorlage für die Windows Holographic-app enthält bereits einen loaseabilitychanged-Handler, der bereits für Sie erstellt wurde. Standardmäßig wird in der Debugkonsole eine Warnung angezeigt, wenn die Positionsüberwachung nicht verfügbar ist. Sie können diesem Handler Code hinzufügen, um eine Antwort nach Bedarf in Ihrer APP bereitzustellen.

Aus **appmain. cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>Räumliche Abbildung

Die APIs für die [räumliche Zuordnung](spatial-mapping-in-directx.md) verwenden Koordinatensysteme, um Modell Transformationen für Oberflächen Netze zu erhalten.

## <a name="see-also"></a>Weitere Informationen
* [Koordinatensysteme](../../design/coordinate-systems.md)
* [Raumanker](../../design/spatial-anchors.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)