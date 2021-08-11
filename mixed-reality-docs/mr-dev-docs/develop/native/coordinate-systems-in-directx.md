---
title: Koordinatensysteme in DirectX
description: Erfahren Sie mehr über Koordinatensysteme in DirectX und Mixed Reality mit räumlichen Locators, Bezugsrahmen und Raumankern.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Mixed Reality, räumlicher Locator, Räumlicher Bezugsrahmen, räumliches Koordinatensystem, räumliche Stufe, Beispielcode, Bildunterdräumung, Raumanker, Raumankerspeicher, Nachverfolgungsverlust, exemplarische Vorgehensweise, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 5da521568ef15f0c512984c96846939bd30063d3485709d4b6568dc9b155052a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196448"
---
# <a name="coordinate-systems-in-directx"></a>Koordinatensysteme in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die nativen WinRT-Legacy-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API](openxr-getting-started.md)** empfohlen.

[Koordinatensysteme](../../design/coordinate-systems.md) bilden die Grundlage für räumliches Verständnis, das von Windows Mixed Reality-APIs geboten wird.

Die heute installierten VR- oder Vr-Einzelraumgeräte richten ein primäres Koordinatensystem für ihren nachverfolgten Raum ein. Mixed Reality Geräte wie HoloLens sind für große undefinierte Umgebungen konzipiert, wobei das Gerät seine Umgebung ermittelt und sich mit der Umgebung auskennt, während der Benutzer durchläuft. Das Gerät passt sich an die kontinuierliche Verbesserung des Wissens über die Räume des Benutzers an, führt jedoch zu Koordinatensystemen, die ihre Beziehung zueinander über die Lebensdauer der Apps ändern. Windows Mixed Reality unterstützt ein breites Spektrum von Geräten, von immersiven Headsets mit Plätzen bis hin zu weltweit angeschlossenen Bezugsrahmen.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C++17-kompatiblem C++/WinRT, wie in der [holografischen C++-Projektvorlage](creating-a-holographic-directx-project.md)verwendet.  Die Konzepte sind für ein C++/WinRT-Projekt gleichwertig, aber Sie müssen den Code übersetzen.

## <a name="spatial-coordinate-systems-in-windows"></a>Räumliche Koordinatensysteme in Windows

Der Kerntyp, der verwendet wird, um über reale Koordinatensysteme in Windows zu sprechen, ist <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem.</a> Eine Instanz dieses Typs stellt ein beliebiges Koordinatensystem dar und stellt eine Methode zum Abrufen von Transformationsmatrixdaten bereit, die Sie zum Transformieren zwischen zwei Koordinatensystemen verwenden können, ohne die Details der einzelnen Koordinatensysteme zu verstehen.

Methoden, die räumliche Informationen zurückgeben, akzeptieren einen SpatialCoordinateSystem-Parameter, damit Sie das Koordinatensystem bestimmen können, in dem es für diese Koordinaten am nützlichsten ist, zurückgegeben zu werden. Räumliche Informationen werden als Punkte, Lichtstrahl oder Volumen in der Umgebung des Benutzers dargestellt, und die Einheiten für diese Koordinaten sind immer in Metern.

Ein SpatialCoordinateSystem verfügt über eine dynamische Beziehung zu anderen Koordinatensystemen, einschließlich derer, die die Position des Geräts darstellen. Zu jedem Zeitpunkt kann das Gerät einige Koordinatensysteme und keine anderen koordinatensysteme finden. Für die meisten Koordinatensysteme muss Ihre App für Zeiträume bereit sein, in denen sie nicht gefunden werden können.

Ihre Anwendung sollte SpatialCoordinateSystems nicht direkt erstellen, sondern über die Perception-APIs genutzt werden. Es gibt drei primäre Quellen von Koordinatensystemen in den Perception-APIs, die jeweils einem Konzept zugeordnet sind, das auf der Seite [Koordinatensysteme](../../design/coordinate-systems.md) beschrieben wird:
* Um einen stationären Verweisrahmen abzurufen, erstellen Sie einen <a href="/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference,</a> oder rufen Sie einen aus dem aktuellen <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>ab.
* Um einen Raumanker zu erhalten, erstellen Sie einen <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.
* Um einen angefügten Verweisrahmen abzurufen, erstellen Sie einen <a href="/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.

Alle koordinatensysteme, die von diesen Objekten zurückgegeben werden, sind rechtshändig, mit +y nach oben, +x nach rechts und +z rückwärts. Sie können sich merken, in welche Richtung die positiven Z-Achsenpunkte zeigen, indem Sie die Finger der linken oder rechten Hand in die positive x-Richtung zeigen und sie in die positive y-Richtung curlingen. Die Richtung, in der Ihre Thumb points entweder auf Sie oder weg von Ihnen zeigen, ist die Richtung, in der die positiven Z-Achsenpunkte für dieses Koordinatensystem zeigen. Die folgende Abbildung zeigt diese beiden Koordinatensysteme.

![Linke und rechte Koordinatensysteme](images/left-hand-right-hand.gif)<br>
*Linke und rechte Koordinatensysteme*

Verwenden Sie die <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator-Klasse,</a> um basierend auf der HoloLens Position einen angefügten oder einen stationären Bezugsrahmen für bootstrap in ein SpatialCoordinateSystem zu erstellen. Fahren Sie mit dem nächsten Abschnitt fort, um mehr über diesen Prozess zu erfahren.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Platzieren von Hologrammen in der Welt mithilfe einer räumlichen Phase

Auf das Koordinatensystem für nicht transparente Windows Mixed Reality immersive Headsets wird über die statische <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current-Eigenschaft</a> zugegriffen. Diese API bietet:

* Ein Koordinatensystem
* Informationen darüber, ob der Spieler auf dem Platz oder mobil ist
* Die Grenze eines sicheren Bereichs für das Gehen, wenn der Spieler mobil ist
* Ein Hinweis darauf, ob das Headset richtungsgerichtet ist. 
* Ein Ereignishandler für Aktualisierungen der räumlichen Phase.

Zunächst erhalten wir die räumliche Phase und abonnieren Updates für sie: 

Code für **die Initialisierung der räumlichen Phase**

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

In der OnCurrentChanged-Methode sollte Ihre App die räumliche Phase untersuchen und die Spielererfahrung aktualisieren. In diesem Beispiel stellen wir eine Visualisierung der Stufengrenze und der vom Benutzer angegebenen Startposition sowie des Ansichtsbereichs und des Bewegungseigenschaftenbereichs der Stufe bereit. Wir greifen auch auf unser eigenes, stationäres Koordinatensystem zurück, wenn keine Phase bereitgestellt werden kann.


Code für **die Aktualisierung der räumlichen Phase**

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

Die Scheitelpunkte, die die Stufengrenze definieren, werden im Uhrzeigersinn bereitgestellt. Die Windows Mixed Reality Shell zeichnet einen Umgrenzungsrand an der Grenze, wenn sich der Benutzer ihm nähert, aber Sie möchten den begehbaren Bereich für Ihre eigenen Zwecke dreieckig machen. Der folgende Algorithmus kann verwendet werden, um die Phase zu triangulieren.


Code für **räumliche Phasentriangularisierung**

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Platzieren von Hologrammen in der Welt mithilfe eines stationären Bezugsrahmens

Die [SpatialStationaryFrameOfReference-Klasse](/uwp/api/Windows.Perception.Spatial.SpatialStationaryFrameOfReference) stellt einen Bezugsrahmen dar, der relativ zur Umgebung des Benutzers [stationär bleibt,](../../design/coordinate-systems.md#stationary-frame-of-reference) während sich der Benutzer bewegt. Dieser Referenzrahmen priorisiert, die Koordinaten in der Nähe des Geräts stabil zu halten. Eine wichtige Verwendung von SpatialStationaryFrameOfReference besteht darin, beim Rendern von Hologrammen als zugrunde liegendes Weltkoordinatensystem innerhalb einer Rendering-Engine zu fungieren.

Um einen SpatialStationaryFrameOfReference abzurufen, verwenden Sie die [SpatialLocator-Klasse,](/uwp/api/Windows.Perception.Spatial.SpatialLocator) und rufen [Sie CreateStationaryFrameOfReferenceAtCurrentLocation](/uwp/api/Windows.Perception.Spatial.SpatialLocator)auf.

Über den Vorlagencode der Windows Holographic-App:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Stationäre Bezugsrahmen sind so konzipiert, dass sie eine optimale Position relativ zum Gesamtraum bereitstellen. Einzelne Positionen innerhalb dieses Bezugsrahmens dürfen leicht abweichen. Dies ist normal, da das Gerät mehr über die Umgebung lernt.
* Wenn eine präzise Platzierung einzelner Hologramme erforderlich ist, sollte ein SpatialAnchor verwendet werden, um das einzelne Hologramm an einer Position in der realen Welt zu verankern, z. B. an einem Punkt, den der Benutzer als von besonderem Interesse angibt. Ankerpositionen driften nicht, können aber korrigiert werden. Der Anker verwendet die korrigierte Position ab dem nächsten Frame, nachdem die Korrektur erfolgt ist.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Platzieren von Hologrammen in der Welt mithilfe von Raumankern

[Raumanker](../../design/coordinate-systems.md#spatial-anchors) sind eine hervorragende Möglichkeit, Hologramme an einem bestimmten Ort in der realen Welt zu platzieren, wobei das System sicherstellt, dass der Anker im Laufe der Zeit aktiv bleibt. In diesem Thema wird erläutert, wie sie einen Anker erstellen und verwenden und wie Sie mit Ankerdaten arbeiten.

Sie können einen SpatialAnchor an einer beliebigen Position und Ausrichtung im SpatialCoordinateSystem Ihrer Wahl erstellen. Das Gerät muss in der Lage sein, dieses Koordinatensystem im Moment zu finden, und das System darf die Grenze der Raumanker nicht erreicht haben.

Nach der Definition wird das Koordinatensystem eines SpatialAnchor kontinuierlich angepasst, um die genaue Position und Ausrichtung seiner ursprünglichen Position beizubehalten. Anschließend können Sie diesen SpatialAnchor verwenden, um Hologramme zu rendern, die in der Umgebung des Benutzers an genau dieser Position fixiert angezeigt werden.

Die Auswirkungen der Anpassungen, die den Anker beibehalten, werden vergrößert, wenn der Abstand zum Anker zunimmt. Sie sollten das Rendern von Inhalten relativ zu einem Anker vermeiden, der mehr als 3 Meter vom Ursprung dieses Ankers entfernt ist.

Die [CoordinateSystem-Eigenschaft](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) ruft ein Koordinatensystem ab, mit dem Sie Inhalte relativ zum Anker platzieren können, wobei die Beschleunigung angewendet wird, wenn das Gerät die genaue Position des Ankers anpasst.

Verwenden Sie die [RawCoordinateSystem-Eigenschaft](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) und das entsprechende [RawCoordinateSystemAdjusted-Ereignis,](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) um diese Anpassungen selbst zu verwalten.

### <a name="persist-and-share-spatial-anchors"></a>Beibehalten und Freigeben von Raumankern

Sie können einen SpatialAnchor lokal mithilfe der [SpatialAnchorStore-Klasse](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore) beibehalten und dann in einer zukünftigen App-Sitzung auf demselben HoloLens Gerät abrufen.

Mithilfe von <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>können Sie einen permanenten Cloudanker aus einem lokalen SpatialAnchor erstellen, den Ihre App dann auf mehreren HoloLens-, iOS- und Android-Geräten finden kann.  Durch die Gemeinsame Nutzung eines gemeinsamen Raumankers auf mehreren Geräten kann jeder Benutzer sehen, dass Inhalte relativ zu diesem Anker in Echtzeit an demselben physischen Ort gerendert werden. 

Sie können <a href="/azure/spatial-anchors/overview" target="_blank">azure Spatial Anchors</a> auch für asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden.  Durch die gemeinsame Nutzung eines permanenten Cloudraumankers können mehrere Geräte das gleiche persistente Hologramm im Laufe der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

Probieren Sie die fünfminütige <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens-Schnellstartanleitung</a>aus, um mit dem Erstellen von freigegebenen Erfahrungen in Ihrer HoloLens-App zu beginnen.

Sobald Sie mit Azure Spatial Anchors ausgeführt werden, können Sie <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">Anker auf HoloLens erstellen und suchen.</a>  Exemplarische Vorgehensweisen sind auch für <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android und iOS</a> verfügbar, sodass Sie dieselben Anker auf allen Geräten freigeben können.

### <a name="create-spatialanchors-for-holographic-content"></a>Erstellen von SpatialAnchors für holografische Inhalte

Für dieses Codebeispiel haben wir die Vorlage Windows Holographic-App geändert, um Anker zu erstellen, wenn die **Geste Gedrückt** erkannt wird. Der Cube wird dann während des Renderdurchlaufs am Anker platziert.

Da mehrere Anker von der Hilfsklasse unterstützt werden, können wir so viele Cubes platzieren, wie wir dieses Codebeispiel verwenden möchten!

> [!NOTE]
> Die IDs für Anker sind etwas, das Sie in Ihrer App steuern. In diesem Beispiel haben wir ein Benennungsschema erstellt, das auf der Anzahl von Ankern basiert, die derzeit in der Ankersammlung der App gespeichert sind.

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Asynchrones Laden und Zwischenspeichern von SpatialAnchorStore

Sehen wir uns an, wie Sie eine SampleSpatialAnchorHelper-Klasse schreiben, die diese Persistenz behandelt, einschließlich:
* Speichern einer Auflistung von In-Memory-Ankern, indiziert durch einen Platform::String-Schlüssel.
* Laden von Ankern aus dem SpatialAnchorStore des Systems, der von der lokalen In-Memory-Sammlung getrennt bleibt.
* Speichern der lokalen In-Memory-Sammlung von Ankern im SpatialAnchorStore, wenn die App dies vorschließt.

So speichern Sie [SpatialAnchor-Objekte](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) im [SpatialAnchorStore.](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)

Wenn die -Klasse gestartet wird, fordern wir SpatialAnchorStore asynchron an. Dies umfasst System-E/A, wenn die API den Ankerspeicher lädt, und diese API wird asynchron, sodass die E/A nicht blockiert wird.

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

Sie erhalten einen SpatialAnchorStore, den Sie zum Speichern der Anker verwenden können. Dies ist eine IMapView, die Schlüsselwerte zuzuordnen, die Zeichenfolgen sind, mit Datenwerten, die SpatialAnchors sind. In unserem Beispielcode speichern wir dies in einer privaten Klassenmembervariablen, auf die über eine öffentliche Funktion unserer Hilfsklasse zugegriffen werden kann.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>Vergessen Sie nicht, die Ereignisse zum Anhalten/Fortsetzen zu verknüpfen, um den Ankerspeicher zu speichern und zu laden.

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

### <a name="save-content-to-the-anchor-store"></a>Speichern von Inhalten im Ankerspeicher

Wenn das System Ihre App anbricht, müssen Sie Ihre Raumanker im Ankerspeicher speichern. Sie können auch an anderer Stelle Anker im Ankerspeicher speichern, da sie für die Implementierung Ihrer App erforderlich sind.

Wenn Sie versuchen möchten, die In-Memory-Anker im SpatialAnchorStore zu speichern, können Sie eine Schleife durch Ihre Sammlung erstellen und versuchen, diese zu speichern.

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Laden von Inhalten aus dem Ankerspeicher, wenn die App fortgesetzt wird

Sie können gespeicherte Anker im AnchorStore wiederherstellen, indem Sie sie aus der IMapView des Ankerspeichers in Ihre eigene In-Memory-Datenbank von SpatialAnchors übertragen, wenn Ihre App fortgesetzt wird oder zu einem beliebigen Zeitpunkt.

Um Anker aus SpatialAnchorStore wiederherzustellen, stellen Sie jeden gewünschten In-Memory-Speicher wieder her.

Sie benötigen eine eigene In-Memory-Datenbank von SpatialAnchors, um den von Ihnen erstellten SpatialAnchors Zeichenfolgen zuzuordnen. In unserem Beispielcode verwenden wir eine Windows::Foundation::Collections::IMap, um die Anker zu speichern, wodurch es einfach ist, denselben Schlüssel und Datenwert für SpatialAnchorStore zu verwenden.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Ein wiederhergestellter Anker kann möglicherweise nicht sofort entfernt werden. Beispielsweise kann es sich um einen Anker in einem separaten Raum oder ganz in einem anderen Gebäude handelt. Aus AnchorStore abgerufene Anker sollten vor der Verwendung auf Locatability getestet werden.

<br>

>[!NOTE]
>In diesem Beispielcode rufen wir alle Anker aus AnchorStore ab. Dies ist keine Voraussetzung. Ihre App könnte ebenso gut eine bestimmte Teilmenge von Ankern auswählen, indem Sie Zeichenfolgenschlüsselwerte verwenden, die für Ihre Implementierung von Bedeutung sind.

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

### <a name="clear-the-anchor-store-when-needed"></a>Löschen des Ankerspeichers bei Bedarf

Manchmal müssen Sie den App-Status löschen und neue Daten schreiben. So gehen Sie mit [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)vor.

Mit unserer Hilfsklasse ist es fast unnötig, die Clear-Funktion zu umschließen. Wir wählen dies in unserer Beispielimplementierung aus, da unsere Hilfsklasse die Verantwortung für den Besitz der SpatialAnchorStore-Instanz erhält.

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Beispiel: Beziehung zwischen Ankerkoordinatensystemen und koordinatensystemen für einen ortsbezogenen Referenzrahmen

Angenommen, Sie verfügen über einen Anker und möchten etwas im Koordinatensystem Ihres Ankers mit dem SpatialStationaryReferenceFrame in Beziehung setzen, den Sie bereits für Ihre anderen Inhalte verwenden. Sie können [TryGetTransformTo](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem) verwenden, um eine Transformation vom Koordinatensystem des Ankers in das des stationären Bezugsrahmens abzurufen:

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

Dieser Prozess ist für Sie auf zwei Arten nützlich:
1. Sie erfahren, ob die beiden Verweisframes relativ zueinander verstanden werden können, und.
2. Wenn ja, erhalten Sie eine Transformation, um direkt von einem Koordinatensystem zum anderen zu wechseln.

Mit diesen Informationen haben Sie ein Verständnis der räumlichen Beziehung zwischen Objekten zwischen den beiden Bezugsrahmen.

Für das Rendering können Sie häufig bessere Ergebnisse erzielen, indem Sie Objekte entsprechend ihrem ursprünglichen Referenzrahmen oder Anker gruppieren. Führen Sie einen separaten Zeichnungsdurchlauf für jede Gruppe aus. Die Ansichtsmatrizen sind genauer für Objekte mit Modelltransformationen, die anfänglich mit demselben Koordinatensystem erstellt werden.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Erstellen von Hologrammen mithilfe eines an ein Gerät angefügten Bezugsrahmens

Es gibt Zeiten, in denen Sie ein Hologramm rendern möchten, das an den Standort des Geräts [angefügt bleibt,](../../design/coordinate-systems.md#attached-frame-of-reference) z. B. ein Panel mit Debuginformationen oder eine Informationsmeldung, wenn das Gerät nur seine Ausrichtung und nicht seine Position im Raum bestimmen kann. Zu diesem Zweck verwenden wir einen angefügten Referenzrahmen.

Die SpatialLocatorAttachedFrameOfReference-Klasse definiert Koordinatensysteme, die relativ zum Gerät und nicht zur realen Welt sind. Dieser Frame weist eine feste Überschrift relativ zur Umgebung des Benutzers auf, die in die Richtung zeigt, in der der Benutzer beim Erstellen des Bezugsrahmens zu sehen war. Von nun an sind alle Ausrichtungen in diesem Bezugsrahmen relativ zu dieser festen Überschrift, selbst wenn der Benutzer das Gerät dreht.

Für HoloLens befindet sich der Ursprung des Koordinatensystems dieses Rahmens in der Mitte der Drehung des Kopfes des Benutzers, sodass seine Position nicht von der Kopfdrehung beeinflusst wird. Ihre App kann einen Offset relativ zu diesem Punkt angeben, um Hologramme vor dem Benutzer zu positionieren.

Um einen SpatialLocatorAttachedFrameOfReference abzurufen, verwenden Sie die SpatialLocator-Klasse, und rufen Sie CreateAttachedFrameOfReferenceAtCurrentHeading auf.

Dies gilt für die gesamte Palette von Windows Mixed Reality Geräten.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Verwenden eines an das Gerät angefügten Referenzrahmens

In diesen Abschnitten wird erläutert, was wir in der Windows Holographic-App-Vorlage geändert haben, um mithilfe dieser API einen an ein Gerät angefügten Referenzrahmen zu aktivieren. Dieses "angefügte" Hologramm funktioniert zusammen mit stationären oder verankerten Hologrammen und kann auch verwendet werden, wenn das Gerät seine Position auf der Welt vorübergehend nicht finden kann.

Zunächst haben wir die Vorlage so geändert, dass anstelle von SpatialStationaryFrameOfReference ein SpatialLocatorAttachedFrameOfReference gespeichert wird:

Aus **HolographicTagAlongSampleMain.h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Aus **HolographicTagAlongSampleMain.cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Während des Updates rufen wir nun das Koordinatensystem zu dem Zeitstempel ab, der von mit der Framevorhersage abgerufen wurde.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Abrufen einer räumlichen Zeigerpose und Befolgen des Anvierens des Benutzers

Wir möchten, dass unser Beispiel holografischem Hologramm dem [Anvieren](../../design/gaze-and-commit.md)des Benutzers folgt, ähnlich wie die holografische Shell dem Anvieren des Benutzers folgen kann. Dazu müssen wir SpatialPointerPose aus dem gleichen Zeitstempel abrufen.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Dieses SpatialPointerPose enthält die Informationen, die zum Positionieren des Hologramms gemäß der [aktuellen Überschrift des Benutzers](gaze-in-directx.md)erforderlich sind.

Aus Gründen der Benutzerfreundlichkeit verwenden wir die lineare Interpolation ("lerp"), um die Änderung der Position über einen bestimmten Zeitraum zu glätten. Dies ist für den Benutzer komfortabler als das Sperren des Hologramms für das Anvieren. DasLernen der Position des Hologramms mit Tags ermöglicht es uns auch, das Hologramm zu stabiler zu machen, indem wir die Bewegung entstützen. Wenn wir dies nicht tun würden, würde der Benutzer die Hologramm-Jitter aufgrund dessen sehen, was normalerweise als nicht wahrnehmbare Bewegungen des Kopfes des Benutzers angesehen wird.

Von **StationaryQuadRenderer::P ositionHologram**:

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
>Im Falle eines Debugbereichs können Sie das Hologramm ein wenig auf der Seite neu positionieren, damit es Ihre Ansicht nicht beeinträchtigt. Hier sehen Sie ein Beispiel dafür, wie Sie dies tun können.

Für **StationaryQuadRenderer::P ositionHologram:**

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

### <a name="rotate-the-hologram-to-face-the-camera"></a>Drehen des Hologramms für die Kamera

Es reicht nicht aus, das Hologramm zu positionieren, was in diesem Fall ein Quader ist. Wir müssen auch das -Objekt drehen, um dem Benutzer zu begegnen. Diese Drehung findet im Weltraum statt, da diese Art der Umdrehung es dem Hologramm ermöglicht, ein Teil der Umgebung des Benutzers zu bleiben. Die Darstellung des Ansichtsbereichs ist nicht so komfortabel, da das Hologramm für die Anzeigeausrichtung gesperrt wird. In diesem Fall müssten Sie auch zwischen den linken und rechten Ansichtsmatrizen interpolieren, um eine Ansichtsraum-Renderingtransformation zu erhalten, die das Stereorendering nicht beeinträchtigt. Hier drehen wir uns auf der X- und Z-Achse, um dem Benutzer zu begegnen.

Von **StationaryQuadRenderer::Update**:

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

### <a name="render-the-attached-hologram"></a>Rendern des angefügten Hologramms

In diesem Beispiel wird auch das Hologramm im Koordinatensystem des SpatialLocatorAttachedReferenceFrame gerendert, in dem wir das Hologramm positioniert haben. (Wenn wir uns entschieden hätten, mit einem anderen Koordinatensystem zu rendern, müssten wir eine Transformation vom Koordinatensystem des vom Gerät angefügten Referenzrahmens zu diesem Koordinatensystem abrufen.)

Aus **HolographicTagAlongSampleMain::Render**:

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

Das ist alles! Das Hologramm "verfolgt" nun eine Position, die 2 Meter vor der Anverfolgrichtung des Benutzers liegt.

>[!NOTE]
>In diesem Beispiel werden auch zusätzliche Inhalte geladen. Weitere Informationen finden Sie unter StationaryQuadRenderer.cpp.

## <a name="handling-tracking-loss"></a>Behandeln von Nachverfolgungsverlusten

Wenn sich das Gerät nicht auf der Welt befindet, wird der Verlust der App nachzuverfolgen. Windows Mixed Reality Apps sollten in der Lage sein, solche Störungen für das Positionsverfolgungssystem zu bewältigen. Diese Unterbrechungen können mithilfe des LocatabilityChanged-Ereignisses auf dem Standardmäßigen SpatialLocator beobachtet und Antworten erstellt werden.

Über **AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Wenn Ihre App ein LocatabilityChanged-Ereignis empfängt, kann sie das Verhalten bei Bedarf ändern. Beispielsweise kann Ihre App im Zustand PositionalTrackingInhibited den normalen Betrieb anhalten und ein [Tag-along-Hologramm](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) rendern, das eine Warnmeldung anzeigt.

Die Windows Holographic-App-Vorlage enthält einen LocatabilityChanged-Handler, der bereits für Sie erstellt wurde. Standardmäßig wird in der Debugkonsole eine Warnung angezeigt, wenn die Positionsnachverfolgung nicht verfügbar ist. Sie können diesem Handler Code hinzufügen, um bei Bedarf eine Antwort von Ihrer App bereitzustellen.

Über **AppMain.cpp:**

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

Die [](spatial-mapping-in-directx.md) RAUMZUORDNUNGS-APIs verwenden Koordinatensysteme, um Modelltransformationen für Oberflächengittermodelle abzurufen.

## <a name="see-also"></a>Weitere Informationen
* [Koordinatensysteme](../../design/coordinate-systems.md)
* [Raumanker](../../design/spatial-anchors.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)