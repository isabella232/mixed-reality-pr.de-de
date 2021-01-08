---
title: Koordinatensysteme in DirectX
description: Erfahren Sie mehr über Koordinatensysteme in DirectX und gemischte Realität mit räumlichen Locators, Referenz Frames und räumlichen Ankern.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: Gemischte Realität, räumlicher Locator, räumlicher Referenzrahmen, räumliches Koordinatensystem, räumliche Phase, Beispielcode, Bildstabilisierung, räumlicher Anker, räumlicher Anker Speicher, nach Verfolgungs Verlust, Exemplarische Vorgehensweise, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 055eff0bb04228cb0a19b9ea208bfc9c00ce2dbe
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006860"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="29d4e-104">Koordinatensysteme in DirectX</span><span class="sxs-lookup"><span data-stu-id="29d4e-104">Coordinate systems in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="29d4e-105">Dieser Artikel bezieht sich auf die älteren WinRT-APIs.</span><span class="sxs-lookup"><span data-stu-id="29d4e-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="29d4e-106">Bei neuen nativen App-Projekten wird die Verwendung der **[openxr-API](openxr-getting-started.md)** empfohlen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="29d4e-107">[Koordinatensysteme](../../design/coordinate-systems.md) bilden die Grundlage für das räumliche Verständnis von Windows Mixed Reality-APIs.</span><span class="sxs-lookup"><span data-stu-id="29d4e-107">[Coordinate systems](../../design/coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="29d4e-108">Die heutigen VR-oder Einzel Raum-VR-Geräte richten ein Primäres Koordinatensystem für den nach verfolgten Speicher ein.</span><span class="sxs-lookup"><span data-stu-id="29d4e-108">Today's seated VR or single-room VR devices establish one primary coordinate system for their tracked space.</span></span> <span data-ttu-id="29d4e-109">Geräte mit gemischter Realität (z. b. hololens) sind für große, nicht definierte Umgebungen konzipiert, und das Gerät ermittelt und erfährt seine Umgebung, während der Benutzer Sie durchläuft.</span><span class="sxs-lookup"><span data-stu-id="29d4e-109">Mixed Reality devices like HoloLens are designed for large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="29d4e-110">Das Gerät passt sich an, um das Wissen über die Räume des Benutzers ständig zu verbessern, führt jedoch zu Koordinatensystemen, die die Beziehung zwischen der Lebensdauer der apps untereinander ändern.</span><span class="sxs-lookup"><span data-stu-id="29d4e-110">The device adapts to continually improving knowledge about the user's rooms, but results in coordinate systems that change their relationship to one another over the apps lifetime.</span></span> <span data-ttu-id="29d4e-111">Die gemischte Realität von Windows unterstützt ein breites Spektrum an Geräten, die von sitzenden immersiven Headsets durch weltweit angehängte Referenzrahmen reichen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-111">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="29d4e-112">Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C + +17-kompatiblen C++/WinRT, wie Sie in der [C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-112">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="29d4e-113">Die Konzepte sind äquivalent zu einem C++/WinRT-Projekt. Sie müssen jedoch den Code übersetzen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-113">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="29d4e-114">Räumliche Koordinatensysteme in Windows</span><span class="sxs-lookup"><span data-stu-id="29d4e-114">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="29d4e-115">Der Kerntyp, der in Bezug auf echte Koordinatensysteme in Windows verwendet wird, ist das <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">spatialcoordinatesystem</a>.</span><span class="sxs-lookup"><span data-stu-id="29d4e-115">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="29d4e-116">Eine Instanz dieses Typs stellt ein beliebiges Koordinatensystem dar, das eine Methode zum erhalten von Transformationsmatrix Daten bereitstellt, die Sie zum Transformieren zwischen zwei Koordinatensystemen verwenden können, ohne die Details der einzelnen Koordinaten zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-116">An instance of this type represents an arbitrary coordinate system, providing a method for getting transformation matrix data that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="29d4e-117">Methoden, die räumliche Informationen zurückgeben, akzeptieren einen spatialcoordinatesystem-Parameter, um Ihnen die Entscheidung über das Koordinatensystem zu ermöglichen, in dem die zurück zugebende Koordinaten am nützlichsten sind.</span><span class="sxs-lookup"><span data-stu-id="29d4e-117">Methods that return spatial information will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="29d4e-118">Räumliche Informationen werden als Punkte, Strahlen oder Volumes in der Benutzerumgebung dargestellt, und die Einheiten für diese Koordinaten sind immer in Meter.</span><span class="sxs-lookup"><span data-stu-id="29d4e-118">Spatial information is represented as points, rays, or volumes in the user's surroundings, and the units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="29d4e-119">Ein spatialcoordinatesystem verfügt über eine dynamische Beziehung mit anderen Koordinatensystemen, einschließlich derjenigen, die die Position des Geräts darstellen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-119">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="29d4e-120">An jedem Punkt kann das Gerät einige Koordinatensysteme und keine anderen suchen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-120">At any point, the device can locate some coordinate systems and not others.</span></span> <span data-ttu-id="29d4e-121">Für die meisten Koordinatensysteme muss Ihre APP bereit sein, Zeiträume zu verarbeiten, in denen Sie nicht gefunden werden können.</span><span class="sxs-lookup"><span data-stu-id="29d4e-121">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="29d4e-122">Die Anwendung sollte spatialcoordinatesystems nicht direkt erstellen, stattdessen sollten Sie über die perception-APIs genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-122">Your application shouldn't create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="29d4e-123">Es gibt drei primäre Quellen für Koordinatensysteme in den perception-APIs, von denen jede einem auf der Seite [Koordinatensysteme](../../design/coordinate-systems.md) beschriebenen Konzept zugeordnet ist:</span><span class="sxs-lookup"><span data-stu-id="29d4e-123">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](../../design/coordinate-systems.md) page:</span></span>
* <span data-ttu-id="29d4e-124">Um einen stationären Verweis Rahmen zu erhalten, erstellen Sie ein <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">spatialstationaryframeofreferenzierungspaar</a> , oder rufen Sie ein aus der aktuellen <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">spatialstageframeofreferenzierung</a>ab.</span><span class="sxs-lookup"><span data-stu-id="29d4e-124">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="29d4e-125">Um einen räumlichen Anker zu erhalten, erstellen Sie ein <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">spatialanchor</a>.</span><span class="sxs-lookup"><span data-stu-id="29d4e-125">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="29d4e-126">Um einen angefügten Frame des Verweises zu erhalten, erstellen Sie ein <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">spatidepanorattachedframeofreferenzierungsverzeichnis</a>.</span><span class="sxs-lookup"><span data-stu-id="29d4e-126">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="29d4e-127">Alle Koordinatensysteme, die von diesen Objekten zurückgegeben werden, sind mit der rechten Hand, mit + y nach oben, + x nach rechts und + z rückwärts.</span><span class="sxs-lookup"><span data-stu-id="29d4e-127">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="29d4e-128">Sie können sich merken, welche Richtung die positive z-Achse zeigt, indem Sie die Finger entweder von Links oder rechts in der positiven x-Richtung zeigen und in die positive y-Richtung hinein.</span><span class="sxs-lookup"><span data-stu-id="29d4e-128">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="29d4e-129">Die Richtung, auf die sich der Ziehpunkt von Ihnen befindet, ist die Richtung, auf die die positive z-Achse für dieses Koordinatensystem zeigt.</span><span class="sxs-lookup"><span data-stu-id="29d4e-129">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="29d4e-130">In der folgenden Abbildung werden diese beiden Koordinatensysteme veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="29d4e-130">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="29d4e-131">![Linke und Rechte Koordinatensysteme](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="29d4e-131">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="29d4e-132">*Linke und Rechte Koordinatensysteme*</span><span class="sxs-lookup"><span data-stu-id="29d4e-132">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="29d4e-133">Verwenden Sie die <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">spatizuweisung</a> -Klasse, um entweder einen angefügten oder einen stationären Verweis Rahmen zu erstellen, der auf der Grundlage der hololens-Position in ein spatialcoordinatesystem Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="29d4e-133">Use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference to bootstrap into a SpatialCoordinateSystem based on the HoloLens position.</span></span> <span data-ttu-id="29d4e-134">Fahren Sie mit dem nächsten Abschnitt fort, um weitere Informationen zu diesem Vorgang zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="29d4e-134">Continue to the next section to learn more about this process.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="29d4e-135">Platzieren von holograms weltweit mithilfe einer räumlichen Phase</span><span class="sxs-lookup"><span data-stu-id="29d4e-135">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="29d4e-136">Das Koordinatensystem für nicht transparente Windows Mixed Reality-immersive Headsets wird mithilfe der statischen <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">spatialstageframeofreferen:: Current</a> -Eigenschaft aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-136">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="29d4e-137">Diese API bietet Folgendes:</span><span class="sxs-lookup"><span data-stu-id="29d4e-137">This API provides:</span></span>

* <span data-ttu-id="29d4e-138">Ein Koordinatensystem</span><span class="sxs-lookup"><span data-stu-id="29d4e-138">A coordinate system</span></span>
* <span data-ttu-id="29d4e-139">Informationen dazu, ob der Player oder mobil ist</span><span class="sxs-lookup"><span data-stu-id="29d4e-139">Information about whether the player is seated or mobile</span></span>
* <span data-ttu-id="29d4e-140">Die Grenze eines sicheren Bereichs zum durchlaufen, wenn der Player mobil ist</span><span class="sxs-lookup"><span data-stu-id="29d4e-140">The boundary of a safe area for walking around if the player is mobile</span></span>
* <span data-ttu-id="29d4e-141">Ein Hinweis darauf, ob das Headset direktional ist.</span><span class="sxs-lookup"><span data-stu-id="29d4e-141">An indication of whether the headset is directional.</span></span> 
* <span data-ttu-id="29d4e-142">Ein Ereignishandler für Aktualisierungen der räumlichen Phase.</span><span class="sxs-lookup"><span data-stu-id="29d4e-142">An event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="29d4e-143">Zuerst erhalten wir die räumliche Phase und abonnieren Updates für Sie:</span><span class="sxs-lookup"><span data-stu-id="29d4e-143">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="29d4e-144">Code für die **Initialisierung räumlicher Phasen**</span><span class="sxs-lookup"><span data-stu-id="29d4e-144">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="29d4e-145">In der OnCurrentChanged-Methode sollte Ihre APP die räumliche Phase überprüfen und die Benutzerumgebung aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="29d4e-145">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience.</span></span> <span data-ttu-id="29d4e-146">In diesem Beispiel stellen wir eine Visualisierung der Stufen Begrenzung und der vom Benutzer angegebenen Startposition sowie den Bereich der Ansicht und den Bereich der Verschiebungs Eigenschaften der Stufe bereit.</span><span class="sxs-lookup"><span data-stu-id="29d4e-146">In this example, we provide a visualization of the stage boundary and the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="29d4e-147">Wir greifen auch auf unser eigenes stationäres Koordinatensystem zurück, wenn eine Phase nicht bereitgestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="29d4e-147">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="29d4e-148">Code für das **Update für räumliche Stufen**</span><span class="sxs-lookup"><span data-stu-id="29d4e-148">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="29d4e-149">Die Reihe der Scheitel Punkte, die die Stufen Begrenzung definieren, werden im Uhrzeigersinn bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="29d4e-149">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="29d4e-150">Die Windows Mixed Reality-Shell zeichnet einen Fence an der Grenze, wenn sich der Benutzer nähert, aber Sie möchten vielleicht den zu verwendbar enden Bereich für Ihre eigenen Zwecke verkleinern.</span><span class="sxs-lookup"><span data-stu-id="29d4e-150">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it, but you may want to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="29d4e-151">Der folgende Algorithmus kann verwendet werden, um die Stufe zu verkleinern.</span><span class="sxs-lookup"><span data-stu-id="29d4e-151">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="29d4e-152">Code für die **phangularisierung in räumlicher Phase**</span><span class="sxs-lookup"><span data-stu-id="29d4e-152">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="29d4e-153">Platzieren von holograms auf der Welt mithilfe eines stationären Frame Rahmens</span><span class="sxs-lookup"><span data-stu-id="29d4e-153">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="29d4e-154">Die [spatialstationaryframeofreferenzierungsklasse](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) stellt einen Frame von Reference dar, der relativ zur Benutzerumgebung [stationär bleibt](../../design/coordinate-systems.md#stationary-frame-of-reference) , wenn der Benutzer sich bewegt.</span><span class="sxs-lookup"><span data-stu-id="29d4e-154">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](../../design/coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="29d4e-155">Dieser Frame des Verweises priorisiert die Stabilität der Koordinaten in der Nähe des Geräts.</span><span class="sxs-lookup"><span data-stu-id="29d4e-155">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="29d4e-156">Eine zentrale Verwendung eines spatialstationaryframeofreferenzierungssystems besteht darin, beim Rendern von holograms als das zugrundeliegende weltweite Koordinatensystem in einer Rendering-Engine zu fungieren.</span><span class="sxs-lookup"><span data-stu-id="29d4e-156">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="29d4e-157">Um eine spatialstationaryframeofreferenzierung abzurufen, verwenden Sie die [spatizuweisung](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) -Klasse und den Aufruf von " [foratestationaryframeofreferenceatcurrentlocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)".</span><span class="sxs-lookup"><span data-stu-id="29d4e-157">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="29d4e-158">Aus dem Windows Holographic-App-Vorlagen Code:</span><span class="sxs-lookup"><span data-stu-id="29d4e-158">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="29d4e-159">Stationäre Verweis Rahmen sind so konzipiert, dass Sie eine am besten geeignete Position relativ zum gesamten Bereich bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-159">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="29d4e-160">Einzelne Positionen innerhalb dieses Bezugsrahmens dürfen leicht abweichen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-160">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="29d4e-161">Dies ist normal, da das Gerät mehr über die Umgebung erfährt.</span><span class="sxs-lookup"><span data-stu-id="29d4e-161">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="29d4e-162">Wenn die genaue Platzierung einzelner Hologramme erforderlich ist, sollte ein spatialanchor verwendet werden, um das einzelne – Hologramm an eine Position in der realen Welt zu verankern, z. b. ein Punkt, den der Benutzer als besonderes Interesse andeutet.</span><span class="sxs-lookup"><span data-stu-id="29d4e-162">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="29d4e-163">Anker Positionen werden nicht abweichen, Sie können jedoch korrigiert werden. der Anker verwendet die korrigierte Position, beginnend im nächsten Frame, nachdem die Korrektur erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="29d4e-163">Anchor positions don't drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="29d4e-164">Platzieren von holograms weltweit mithilfe räumlicher Anker</span><span class="sxs-lookup"><span data-stu-id="29d4e-164">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="29d4e-165">[Räumliche Anker](../../design/coordinate-systems.md#spatial-anchors) sind eine gute Möglichkeit, Hologramme an einer bestimmten Stelle in der realen Welt zu platzieren, wobei das System sicherstellt, dass der Anker im Laufe der Zeit vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="29d4e-165">[Spatial anchors](../../design/coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="29d4e-166">In diesem Thema wird erläutert, wie ein Anker erstellt und verwendet wird und wie mit Anker Daten gearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="29d4e-166">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="29d4e-167">Sie können ein spatialanchor an beliebiger Position und Ausrichtung innerhalb des spatialcoordinatesystem Ihrer Wahl erstellen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-167">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="29d4e-168">Das Gerät muss in der Lage sein, dieses Koordinatensystem zu einem bestimmten Zeitpunkt zu finden, und das System darf den Grenzwert räumlicher Anker nicht erreicht haben.</span><span class="sxs-lookup"><span data-stu-id="29d4e-168">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="29d4e-169">Sobald das Koordinatensystem eines räumalanchors definiert ist, wird es ständig angepasst, um die genaue Position und Ausrichtung der ursprünglichen Position zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="29d4e-169">Once defined, the coordinate system of a SpatialAnchor adjusts continually to keep the precise position and orientation of its initial location.</span></span> <span data-ttu-id="29d4e-170">Anschließend können Sie mit diesem spatialanchor holograms so darstellen, dass Sie in der Benutzerumgebung an diesem exakten Speicherort korrigiert werden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-170">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="29d4e-171">Die Auswirkungen der Anpassungen, die den Anker an Ort halten, werden vergrößert, wenn sich die Entfernung vom Anker vergrößert.</span><span class="sxs-lookup"><span data-stu-id="29d4e-171">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="29d4e-172">Sie sollten das Rendern von Inhalten in Relation zu einem Anker vermeiden, der mehr als ungefähr 3 Meter vom Ursprung dieses Ankers ist.</span><span class="sxs-lookup"><span data-stu-id="29d4e-172">You should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="29d4e-173">Die [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) -Eigenschaft ruft ein Koordinatensystem ab, mit dem Sie Inhalte relativ zum Anker platzieren können, wobei eine Beschleunigung angewendet wird, wenn das Gerät den genauen Speicherort des Ankers anpasst.</span><span class="sxs-lookup"><span data-stu-id="29d4e-173">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="29d4e-174">Verwenden Sie die [rawcoordinatesystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) -Eigenschaft und das zugehörige [rawcoordinatesystemadjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) -Ereignis, um diese Anpassungen selbst zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="29d4e-174">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="29d4e-175">Beibehalten und freigeben räumlicher Anker</span><span class="sxs-lookup"><span data-stu-id="29d4e-175">Persist and share spatial anchors</span></span>

<span data-ttu-id="29d4e-176">Sie können ein spatialanchor lokal mithilfe der [spatialanchorstore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) -Klasse beibehalten und dann in einer zukünftigen App-Sitzung auf demselben hololens-Gerät wiederholen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-176">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="29d4e-177">Mithilfe der <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">räumlichen Anker von Azure</a>können Sie einen permanenten cloudenanchor von einem lokalen spatialanchor erstellen, das Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.</span><span class="sxs-lookup"><span data-stu-id="29d4e-177">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="29d4e-178">Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers über mehrere Geräte hinweg kann jeder Benutzer in Echtzeit Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Standort gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-178">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location in real time.</span></span> 

<span data-ttu-id="29d4e-179">Sie können auch <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">räumliche Azure-Anker</a> für die asynchrone – Hologramm-Persistenz über hololens-, IOS-und Android-Geräte verwenden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-179">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="29d4e-180">Durch die gemeinsame Nutzung eines permanenten clouddiensts können mehrere Geräte im Lauf der Zeit dasselbe persistente Hologramm beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="29d4e-180">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="29d4e-181">Um mit der Einführung von freigegebenen Erfahrungen in der hololens-APP zu beginnen, testen Sie den Schnellstart mit den fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchor hololens</a>.</span><span class="sxs-lookup"><span data-stu-id="29d4e-181">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="29d4e-182">Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">Anker in hololens erstellen und lokalisieren</a>.</span><span class="sxs-lookup"><span data-stu-id="29d4e-182">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="29d4e-183">Exemplarische Vorgehensweisen sind auch für <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android und IOS</a> verfügbar, sodass Sie dieselben Anker auf allen Geräten gemeinsam verwenden können.</span><span class="sxs-lookup"><span data-stu-id="29d4e-183">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="29d4e-184">Erstellen von spatialanchor für Holographic Content</span><span class="sxs-lookup"><span data-stu-id="29d4e-184">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="29d4e-185">In diesem Codebeispiel wurde die Windows Holographic-App-Vorlage so geändert, dass Anker erstellt werden, wenn die **gedrückte** Bewegung erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="29d4e-185">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="29d4e-186">Der Cube wird dann während des Renderpass am Anker platziert.</span><span class="sxs-lookup"><span data-stu-id="29d4e-186">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="29d4e-187">Da mehrere Anker von der Hilfsklasse unterstützt werden, können wir so viele Cubes platzieren, wie wir dieses Codebeispiel verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="29d4e-187">Since multiple anchors are supported by the helper class, we can place as many cubes as we want to use this code sample!</span></span>

> [!NOTE]
> <span data-ttu-id="29d4e-188">Die IDs für Anker sind etwas, das Sie in ihrer App steuern.</span><span class="sxs-lookup"><span data-stu-id="29d4e-188">The IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="29d4e-189">In diesem Beispiel haben wir ein Benennungs Schema erstellt, das auf der Grundlage der Anzahl der Anker basiert, die derzeit in der Auflistung von Ankern der APP gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="29d4e-189">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="29d4e-190">Asynchrones Laden und Zwischenspeichern von spatialanchorstore</span><span class="sxs-lookup"><span data-stu-id="29d4e-190">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="29d4e-191">Sehen wir uns an, wie Sie eine samplespatialanchorhelper-Klasse schreiben, die diese Persistenz behandelt, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="29d4e-191">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="29d4e-192">Speichern einer Auflistung von in-Memory-Ankern, indiziert von einem Platform:: String-Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="29d4e-192">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="29d4e-193">Anker aus dem spatialanchorstore des Systems werden geladen, die von der lokalen Auflistung im Arbeitsspeicher getrennt aufbewahrt werden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-193">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="29d4e-194">Speichern der lokalen in-Memory-Auflistung von Ankern im spatialanchorstore, wenn die App dafür entscheidet.</span><span class="sxs-lookup"><span data-stu-id="29d4e-194">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="29d4e-195">Im folgenden wird beschrieben, wie Sie [spatialanchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) -Objekte im [spatialanchorstore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)speichern.</span><span class="sxs-lookup"><span data-stu-id="29d4e-195">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="29d4e-196">Wenn die Klasse gestartet wird, fordern wir den spatialanchorstore asynchron an.</span><span class="sxs-lookup"><span data-stu-id="29d4e-196">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="29d4e-197">Dies umfasst die System-e/a, da die API den Anker Speicher lädt, und diese API wird asynchron erstellt, sodass die e/a-Vorgänge nicht blockiert werden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-197">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="29d4e-198">Sie erhalten einen spatialanchorstore, den Sie zum Speichern der Anker verwenden können.</span><span class="sxs-lookup"><span data-stu-id="29d4e-198">You'll be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="29d4e-199">Dies ist ein imapview, das Schlüsselwerte, die Zeichen folgen sind, mit Datenwerten, die spatialanchor sind, verknüpft.</span><span class="sxs-lookup"><span data-stu-id="29d4e-199">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="29d4e-200">In unserem Beispielcode speichern wir dies in einer privaten Klassenmember-Variablen, auf die über eine öffentliche Funktion unserer Hilfsklasse zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="29d4e-200">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="29d4e-201">Vergessen Sie nicht, die Suspend/Resume-Ereignisse anzuschließen, um den Anker Speicher zu speichern und zu laden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-201">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="29d4e-202">Inhalt im Anker Speicher speichern</span><span class="sxs-lookup"><span data-stu-id="29d4e-202">Save content to the anchor store</span></span>

<span data-ttu-id="29d4e-203">Wenn das System Ihre APP anhält, müssen Sie Ihre räumlichen Anker im Anker Speicher speichern.</span><span class="sxs-lookup"><span data-stu-id="29d4e-203">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="29d4e-204">Sie können auch die Anker im Anker Speicher zu einem anderen Zeitpunkt speichern, da Sie für die Implementierung Ihrer APP erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="29d4e-204">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="29d4e-205">Wenn Sie bereit sind, die in-Memory-Anker im spatialanchorstore zu speichern, können Sie die Sammlung durchlaufen und versuchen, jede einzelne zu speichern.</span><span class="sxs-lookup"><span data-stu-id="29d4e-205">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="29d4e-206">Inhalt aus dem Anker Speicher laden, wenn die APP fortgesetzt wird</span><span class="sxs-lookup"><span data-stu-id="29d4e-206">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="29d4e-207">Sie können gespeicherte Anker im anchorstore wiederherstellen, indem Sie Sie aus der imapview des Anker Stores in ihren eigenen in-Memory Database von spatialanchor übertragen, wenn Ihre APP fortgesetzt wird, oder zu einem beliebigen Zeitpunkt.</span><span class="sxs-lookup"><span data-stu-id="29d4e-207">You can restore saved anchors in the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors when your app resumes or at any time.</span></span>

<span data-ttu-id="29d4e-208">Um Anker aus dem spatialanchorstore wiederherzustellen, stellen Sie jeden, für den Sie sich interessieren, an ihrer eigenen in-Memory-Sammlung wieder her.</span><span class="sxs-lookup"><span data-stu-id="29d4e-208">To restore anchors from the SpatialAnchorStore, restore each one that you're interested in to your own in-memory collection.</span></span>

<span data-ttu-id="29d4e-209">Sie benötigen eine eigene in-Memory Database von spatialanchor, um Zeichen folgen den spatialanchor zuzuordnen, die Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-209">You need your own in-memory database of SpatialAnchors to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="29d4e-210">In unserem Beispielcode wählen wir die Verwendung eines Windows:: Foundation:: Collections:: IMap zum Speichern der Anker aus, wodurch die Verwendung desselben Schlüssels und Datenwerts für den spatialanchorstore vereinfacht wird.</span><span class="sxs-lookup"><span data-stu-id="29d4e-210">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="29d4e-211">Ein Anker, der wieder hergestellt wird, ist möglicherweise nicht sofort verwendbar.</span><span class="sxs-lookup"><span data-stu-id="29d4e-211">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="29d4e-212">Beispielsweise kann es sich um einen Anker in einem separaten Raum oder in einem anderen Gebäude handeln.</span><span class="sxs-lookup"><span data-stu-id="29d4e-212">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="29d4e-213">Anker, die aus dem anchorstore abgerufen werden, sollten vor deren Verwendung auf die Erreichbarkeit getestet werden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-213">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="29d4e-214">In diesem Beispielcode rufen wir alle Anker aus dem anchorstore ab.</span><span class="sxs-lookup"><span data-stu-id="29d4e-214">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="29d4e-215">Dies ist keine Anforderung. Ihre APP könnte auch eine bestimmte Teilmenge von Ankern auswählen und auswählen, indem Sie Zeichen folgen Schlüsselwerte verwenden, die für Ihre Implementierung von Bedeutung sind.</span><span class="sxs-lookup"><span data-stu-id="29d4e-215">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="29d4e-216">Den Anker Speicher bei Bedarf löschen</span><span class="sxs-lookup"><span data-stu-id="29d4e-216">Clear the anchor store, when needed</span></span>

<span data-ttu-id="29d4e-217">Manchmal müssen Sie den App-Status löschen und neue Daten schreiben.</span><span class="sxs-lookup"><span data-stu-id="29d4e-217">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="29d4e-218">Im folgenden wird erläutert, wie Sie mit dem [spatialanchorstore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)Vorgehen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-218">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="29d4e-219">Mit unserer Hilfsklasse ist es fast unnötig, die Clear-Funktion zu wrappen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-219">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="29d4e-220">Wir entscheiden uns hierfür in unserer Beispiel Implementierung, da unsere Hilfsklasse die Verantwortung für den Besitz der spatialanchorstore-Instanz erhält.</span><span class="sxs-lookup"><span data-stu-id="29d4e-220">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="29d4e-221">Beispiel: Verknüpfen von Anker Koordinatensystemen mit stationären Reference Frame-Koordinatensystemen</span><span class="sxs-lookup"><span data-stu-id="29d4e-221">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="29d4e-222">Nehmen wir an, Sie haben einen Anker, und Sie möchten etwas im Koordinatensystem Ihres Ankers mit dem spatialstationaryreferenceframe verknüpfen, den Sie bereits für Ihre anderen Inhalte verwenden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-222">Let's say you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame you’re already using for your other content.</span></span> <span data-ttu-id="29d4e-223">Sie können [trygettransformto](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) verwenden, um eine Transformation vom Koordinatensystem des Ankers zu der des stationären Referenzrahmens zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="29d4e-223">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to get a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="29d4e-224">Dieser Prozess ist auf zweierlei Weise nützlich:</span><span class="sxs-lookup"><span data-stu-id="29d4e-224">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="29d4e-225">Es gibt Aufschluss darüber, ob die beiden Verweis Frames relativ zueinander verstanden werden können.</span><span class="sxs-lookup"><span data-stu-id="29d4e-225">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="29d4e-226">Wenn dies der Fall ist, stellt Sie eine Transformation bereit, um direkt von einem Koordinatensystem zum anderen zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="29d4e-226">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="29d4e-227">Mit diesen Informationen haben Sie einen Einblick in die räumliche Beziehung zwischen den Objekten zwischen den beiden Referenz Frames.</span><span class="sxs-lookup"><span data-stu-id="29d4e-227">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="29d4e-228">Zum Rendern können Sie häufig bessere Ergebnisse erzielen, indem Sie Objekte entsprechend ihrem ursprünglichen Referenzrahmen oder Anker gruppieren.</span><span class="sxs-lookup"><span data-stu-id="29d4e-228">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="29d4e-229">Führen Sie einen separaten Zeichnungs Durchlauf für jede Gruppe aus.</span><span class="sxs-lookup"><span data-stu-id="29d4e-229">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="29d4e-230">Die Ansichts Matrizen sind für Objekte mit Modell Transformationen, die anfänglich mit demselben Koordinatensystem erstellt werden, genauer.</span><span class="sxs-lookup"><span data-stu-id="29d4e-230">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="29d4e-231">Erstellen von holograms mithilfe eines vom Gerät angefügten Referenzrahmens</span><span class="sxs-lookup"><span data-stu-id="29d4e-231">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="29d4e-232">Es gibt Zeiten, in denen ein – Hologramm geresgt werden soll, das an den Speicherort des Geräts [angehängt bleibt](../../design/coordinate-systems.md#attached-frame-of-reference) , z. b. ein Panel mit Debuginformationen oder eine Informations Meldung, wenn das Gerät nur seine Ausrichtung und nicht seine Position im Raum ermitteln kann.</span><span class="sxs-lookup"><span data-stu-id="29d4e-232">There are times when you want to render a hologram that [remains attached](../../design/coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="29d4e-233">Hierfür wird ein angefügter Verweis Rahmen verwendet.</span><span class="sxs-lookup"><span data-stu-id="29d4e-233">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="29d4e-234">Die spatizuweisung-Klasse "spatichedframeofreferenzierungssysteme" definiert Koordinatensysteme, die relativ zum Gerät und nicht in der realen Welt sind.</span><span class="sxs-lookup"><span data-stu-id="29d4e-234">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems, which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="29d4e-235">Dieser Frame verfügt über eine festgelegte Überschrift in Bezug auf die Benutzerumgebung, die in der Richtung angezeigt wird, die der Benutzer beim Erstellen des Verweis Rahmens aufzeigte.</span><span class="sxs-lookup"><span data-stu-id="29d4e-235">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="29d4e-236">Danach sind alle Ausrichtungen in diesem Verweis Verweis relativ zu dieser festgelegten Überschrift, auch wenn der Benutzer das Gerät dreht.</span><span class="sxs-lookup"><span data-stu-id="29d4e-236">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="29d4e-237">Bei hololens befindet sich der Ursprung des Koordinatensystems dieses Frames im Mittelpunkt der Drehung des Benutzer Kopfes, sodass seine Position nicht von der Kopfdrehung betroffen ist.</span><span class="sxs-lookup"><span data-stu-id="29d4e-237">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="29d4e-238">Ihre APP kann einen Offset relativ zu diesem Punkt angeben, um Hologramme vor dem Benutzer zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="29d4e-238">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="29d4e-239">Verwenden Sie zum Abrufen eines spatizucatorattachedframeofreferenzierers die spatidepcator-Klasse, und nennen Sie "forateattachedframeofreferenceatspatitheiading".</span><span class="sxs-lookup"><span data-stu-id="29d4e-239">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="29d4e-240">Dies gilt für den gesamten Bereich von Windows Mixed Reality-Geräten.</span><span class="sxs-lookup"><span data-stu-id="29d4e-240">This applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="29d4e-241">Verwenden eines mit dem Gerät verbundenen Referenzrahmens</span><span class="sxs-lookup"><span data-stu-id="29d4e-241">Use a reference frame attached to the device</span></span>

<span data-ttu-id="29d4e-242">In diesen Abschnitten wird erläutert, was wir in der Windows Holographic-App-Vorlage geändert haben, um mit dieser API einen mit dem Gerät verknüpften Referenzrahmen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="29d4e-242">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="29d4e-243">Dieses "angefügte" – Hologramm funktioniert zusammen mit stationären oder verankerten holograms und kann auch verwendet werden, wenn die Position des Geräts vorübergehend nicht gefunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="29d4e-243">This "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="29d4e-244">Zuerst haben wir die Vorlage so geändert, dass Sie ein spatidepaseorattachedframeofreferen-Objekt anstelle einer spatialstationaryframeofreferenzierung speichert:</span><span class="sxs-lookup"><span data-stu-id="29d4e-244">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="29d4e-245">Aus **holographictagalongsamplemain. h**:</span><span class="sxs-lookup"><span data-stu-id="29d4e-245">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="29d4e-246">Aus **holographictagalongsamplemain. cpp**:</span><span class="sxs-lookup"><span data-stu-id="29d4e-246">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="29d4e-247">Während des Updates erhalten wir nun das Koordinatensystem am Zeitstempel, der von mit der Frame Vorhersage abgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="29d4e-247">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="29d4e-248">Stellen Sie eine räumliche Zeiger Pose dar, und folgen Sie dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="29d4e-248">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="29d4e-249">Wir möchten, dass unser Beispiel – Hologramm dem [Blick](../../design/gaze-and-commit.md)des Benutzers folgt, ähnlich wie die Holographic Shell dem Blick des Benutzers folgen kann.</span><span class="sxs-lookup"><span data-stu-id="29d4e-249">We want our example hologram to follow the user's [gaze](../../design/gaze-and-commit.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="29d4e-250">Hierfür müssen wir spatialpointerpose aus dem gleichen Zeitstempel erhalten.</span><span class="sxs-lookup"><span data-stu-id="29d4e-250">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="29d4e-251">Diese spatialpointerpose verfügt über die Informationen, die erforderlich sind, um das – Hologramm entsprechend der [aktuellen Überschrift des Benutzers](gaze-in-directx.md)zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="29d4e-251">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="29d4e-252">Für den Benutzerkomfort wird die lineare interpolung ("Lerp") verwendet, um die Änderung an der Position innerhalb eines bestimmten Zeitraums zu glätten.</span><span class="sxs-lookup"><span data-stu-id="29d4e-252">For user comfort, we use linear interpolation ("lerp") to smooth the change in position over a period of time.</span></span> <span data-ttu-id="29d4e-253">Dies ist für den Benutzer besser, als das – Hologramm auf seinen Blick zu sperren.</span><span class="sxs-lookup"><span data-stu-id="29d4e-253">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="29d4e-254">Durch das lerping der Position des "Tag"-entlang des Hologramms können wir das Hologramm auch durch Dämpfen der Bewegung stabilisieren.</span><span class="sxs-lookup"><span data-stu-id="29d4e-254">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement.</span></span> <span data-ttu-id="29d4e-255">Wenn wir diese Dämpfung nicht durchführen, würde der Benutzer den – Hologramm-Jitter sehen, weil er normalerweise als unwahrliche Bewegungen des Benutzer Kopfes angesehen wird.</span><span class="sxs-lookup"><span data-stu-id="29d4e-255">If we didn't do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="29d4e-256">Von **stationaryquadrenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="29d4e-256">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="29d4e-257">Im Fall eines debuggingbereichs können Sie das Hologramm auf der Seite auf einen kleinen Wert zurücksetzen, damit die Ansicht nicht behindert wird.</span><span class="sxs-lookup"><span data-stu-id="29d4e-257">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it doesn't obstruct your view.</span></span> <span data-ttu-id="29d4e-258">Im folgenden finden Sie ein Beispiel dafür, wie Sie dies tun können.</span><span class="sxs-lookup"><span data-stu-id="29d4e-258">Here's an example of how you might do that.</span></span>

<span data-ttu-id="29d4e-259">Für **stationaryquadrenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="29d4e-259">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="29d4e-260">Das Hologramm drehen, um der Kamera zu begegnen</span><span class="sxs-lookup"><span data-stu-id="29d4e-260">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="29d4e-261">Es reicht nicht aus, um das Hologram zu positionieren, was in diesem Fall ein Vierfach ist. Wir müssen auch das Objekt drehen, um dem Benutzer zu begegnen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-261">It isn't enough to position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="29d4e-262">Diese Rotation tritt im Raum der Welt auf, da das – Hologramm durch diese Art des Abbilds ein Teil der Benutzerumgebung bleiben kann.</span><span class="sxs-lookup"><span data-stu-id="29d4e-262">This rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="29d4e-263">Das Ansichts Leerraum-fakboardingvorgang ist nicht so komfortabel, da das – Hologramm in der Anzeige Ausrichtung gesperrt wird. in diesem Fall müssten Sie auch zwischen den linken und rechten Ansichts Matrizen interpolieren, um eine View-Space-Billboard-Transformation zu erhalten, die das Stereo Rendering nicht beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="29d4e-263">View-space billboarding isn't as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices to acquire a view-space billboard transform that doesn't disrupt stereo rendering.</span></span> <span data-ttu-id="29d4e-264">Hier drehen wir die X-und Z-Achsen, um dem Benutzer zu begegnen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-264">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="29d4e-265">Von **stationaryquadrenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="29d4e-265">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="29d4e-266">Rendering des angefügten holograms</span><span class="sxs-lookup"><span data-stu-id="29d4e-266">Render the attached hologram</span></span>

<span data-ttu-id="29d4e-267">In diesem Beispiel wählen wir auch das – Hologramm im Koordinatensystem von spatidepplatorattachedreferenceframe aus, in dem wir das – Hologramm positioniert haben.</span><span class="sxs-lookup"><span data-stu-id="29d4e-267">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="29d4e-268">(Wenn wir uns für das Renderingsystem mit einem anderen Koordinatensystem entschieden hätten, müssten wir eine Transformation vom Koordinatensystem des mit dem Gerät verbundenen Verweis Rahmens an dieses Koordinatensystem abrufen.)</span><span class="sxs-lookup"><span data-stu-id="29d4e-268">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="29d4e-269">Aus **holographictagalongsamplemain:: Rendering**:</span><span class="sxs-lookup"><span data-stu-id="29d4e-269">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="29d4e-270">Das war's.</span><span class="sxs-lookup"><span data-stu-id="29d4e-270">That's it!</span></span> <span data-ttu-id="29d4e-271">Das – Hologramm ist nun eine Position, die zwei Meter vor der Blick Richtung des Benutzers ist.</span><span class="sxs-lookup"><span data-stu-id="29d4e-271">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="29d4e-272">In diesem Beispiel werden auch weitere Inhalte geladen, siehe stationaryquadrenderer. cpp.</span><span class="sxs-lookup"><span data-stu-id="29d4e-272">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="29d4e-273">Behandeln von nach Verfolgungs Verlusten</span><span class="sxs-lookup"><span data-stu-id="29d4e-273">Handling tracking loss</span></span>

<span data-ttu-id="29d4e-274">Wenn das Gerät sich nicht auf der ganzen Welt finden kann, kann der APP-Verlust nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="29d4e-274">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="29d4e-275">Windows Mixed Reality-apps sollten solche Unterbrechungen für das Positions Überwachungssystem verarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="29d4e-275">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="29d4e-276">Diese Unterbrechungen können beobachtet und Antworten erstellt werden, indem das locatabilitychanged-Ereignis im standardspaticator verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="29d4e-276">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="29d4e-277">Aus **appmain:: abbildrfaden:**</span><span class="sxs-lookup"><span data-stu-id="29d4e-277">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="29d4e-278">Wenn Ihre APP ein lochanabilitychanged-Ereignis empfängt, kann Sie das Verhalten nach Bedarf ändern.</span><span class="sxs-lookup"><span data-stu-id="29d4e-278">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="29d4e-279">Beispielsweise kann Ihre APP im positionaltrackinginhibited-Zustand den normalen Betrieb anhalten und ein [Tag-entlang-– Hologramm](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) , das eine Warnmeldung anzeigt, darstellen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-279">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="29d4e-280">Die Vorlage für die Windows Holographic-app enthält bereits einen loaseabilitychanged-Handler, der bereits für Sie erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="29d4e-280">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="29d4e-281">Standardmäßig wird in der Debugkonsole eine Warnung angezeigt, wenn die Positionsüberwachung nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="29d4e-281">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="29d4e-282">Sie können diesem Handler Code hinzufügen, um eine Antwort nach Bedarf in Ihrer APP bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="29d4e-282">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="29d4e-283">Aus **appmain. cpp:**</span><span class="sxs-lookup"><span data-stu-id="29d4e-283">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="29d4e-284">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="29d4e-284">Spatial mapping</span></span>

<span data-ttu-id="29d4e-285">Die APIs für die [räumliche Zuordnung](spatial-mapping-in-directx.md) verwenden Koordinatensysteme, um Modell Transformationen für Oberflächen Netze zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="29d4e-285">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="29d4e-286">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="29d4e-286">See also</span></span>
* [<span data-ttu-id="29d4e-287">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="29d4e-287">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="29d4e-288">Raumanker</span><span class="sxs-lookup"><span data-stu-id="29d4e-288">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* <span data-ttu-id="29d4e-289"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="29d4e-289"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="29d4e-290">Anvisieren mit dem Kopf und mit den Augen in DirectX</span><span class="sxs-lookup"><span data-stu-id="29d4e-290">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="29d4e-291">Hände und Motion-Controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="29d4e-291">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="29d4e-292">Räumliche Abbildung in DirectX</span><span class="sxs-lookup"><span data-stu-id="29d4e-292">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
