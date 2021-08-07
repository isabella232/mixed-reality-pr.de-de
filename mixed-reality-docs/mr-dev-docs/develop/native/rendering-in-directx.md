---
title: Rendern in DirectX
description: Erfahren Sie, wie Sie Inhalte in DirectX-Anwendungen aktualisieren und rendern, um Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, Rendering, 3D-Grafiken, HolographicFrame, Renderschleife, Updateschleife, exemplarische Vorgehensweise, Beispielcode, Direct3D
ms.openlocfilehash: 2c3dd32f5782d6096c6560ec6db55ef1cc7bb533dddb0a4b5fe87cd91bb2f81b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209448"
---
# <a name="rendering-in-directx"></a>Rendern in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren nativen WinRT-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API empfohlen.](openxr-getting-started.md)**

Windows Mixed Reality basiert auf DirectX, um umfangreiche, 3D-grafische Benutzeroberflächen für Benutzer zu erzeugen. Die Renderingabstraktion befindet sich direkt über DirectX, wodurch Apps über die Position und Ausrichtung von holografischen Szenenbeobachtern, die vom System vorhergesagt werden, eine Vorhersage erhalten. Der Entwickler kann dann seine Hologramme basierend auf jeder Kamera suchen, damit die App diese Hologramme in verschiedenen räumlichen Koordinatensystemen rendern kann, während sich der Benutzer bewegt.

Hinweis: In dieser exemplarischen Vorgehensweise wird das holografische Rendering in Direct3D 11 beschrieben. Eine Direct3D 12 Windows Mixed Reality-App-Vorlage wird auch mit der Mixed Reality-App-Vorlagenerweiterung bereitgestellt.

## <a name="update-for-the-current-frame"></a>Update für den aktuellen Frame

Um den Anwendungsstatus für Hologramme zu aktualisieren, wird die App einmal pro Frame:
* Hier erhalten <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">Sie einen HolographicFrame</a> aus dem Anzeigeverwaltungssystem.
* Aktualisieren Sie die Szene mit der aktuellen Vorhersage, wo sich die Kameraansicht befindet, wenn das Rendern abgeschlossen ist. Beachten Sie, dass es mehrere Kamera für die holografische Szene geben kann.

Zum Rendern in holografischen Kameraansichten wird die App einmal pro Frame:
* Rendern Sie für jede Kamera die Szene für den aktuellen Frame, indem Sie die Kameraansicht und Projektionsmatrizen aus dem System verwenden.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Erstellen eines neuen holografischen Rahmens und Erhalten der Vorhersage

Der <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame enthält</a> Informationen, die die App aktualisieren und den aktuellen Frame rendern muss. Die App beginnt jeden neuen Frame, indem sie die **CreateNextFrame-Methode** aufruft. Wenn diese Methode aufgerufen wird, werden Vorhersagen mithilfe der neuesten verfügbaren Sensordaten getroffen und im **CurrentPrediction-Objekt gekapselt.**

Für jeden gerenderten Frame muss ein neues Frameobjekt verwendet werden, da es nur für einen bestimmten Zeitpunkt gültig ist. Die **CurrentPrediction-Eigenschaft** enthält Informationen wie die Kameraposition. Die Informationen werden auf den genauen Zeitpunkt extrapoliert, zu dem der Frame für den Benutzer sichtbar sein soll.

Der folgende Code wurde aus **AppMain::Update entfernt:**

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Verarbeiten von Kameraupdates

Hintergrundpuffer können sich von Frame zu Frame ändern. Ihre App muss den Hintergrundpuffer für jede Kamera überprüfen und Ressourcenansichten und Tiefenpuffer nach Bedarf frei geben und neu erstellen. Beachten Sie, dass die Gruppe von Posen in der Vorhersage die autoritative Liste der Kameras ist, die im aktuellen Rahmen verwendet werden. In der Regel verwenden Sie diese Liste, um die Gruppe von Kameras zu iterieren.

Über **AppMain::Update:**

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

Über **DeviceResources::EnsureCameraResources:**

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Das Koordinatensystem, das als Grundlage für das Rendering verwendet werden soll

Windows Mixed Reality Kann Ihre App verschiedene Koordinatensysteme [erstellen,](coordinate-systems-in-directx.md)z. B. angefügte und festliche Referenzframes zum Nachverfolgen von Orten in der physischen Welt. Ihre App kann dann diese Koordinatensysteme verwenden, um zu erfahren, wo Hologramme für jeden Frame gerendert werden. Wenn Sie Koordinaten von einer API anfordern, übergeben Sie immer das <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem,</a> in dem diese Koordinaten ausgedrückt werden sollen.

Über **AppMain::Update:**

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Diese Koordinatensysteme können dann verwendet werden, um Beim Rendern des Inhalts in Ihrer Szene Stereoansichtsmatrizen zu generieren.

Von **CameraResources::UpdateViewProjectionBuffer:**

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Verarbeiten der Eingabe von Anving und Gesten

[Anving](gaze-in-directx.md) [und](hands-and-motion-controllers-in-directx.md) Handeingaben sind nicht zeitbasierte Eingaben und müssen in der **StepTimer-Funktion nicht aktualisiert** werden. Diese Eingabe ist jedoch etwas, das die App jeden Frame betrachten muss.

### <a name="process-time-based-updates"></a>Verarbeiten zeitbasierter Updates

Jede Echtzeit-Rendering-App benötigt eine Möglichkeit, zeitbasierte Updates zu verarbeiten. Die Windows Holographic-App-Vorlage verwendet eine **StepTimer-Implementierung,** ähnlich der StepTimer-Implementierung, die in der DirectX 11-UWP-App-Vorlage bereitgestellt wird. Diese StepTimer-Beispiel-Hilfsklasse kann feste Zeitschrittupdates, variable Zeitschrittupdates bereitstellen, und der Standardmodus ist variable Zeitschritte.

Für holografisches Rendering haben wir uns dafür entschieden, nicht zu viel in die Timerfunktion zu setzen, da Sie sie als festen Zeitschritt konfigurieren können. Es kann mehr als einmal pro Frame oder gar nicht für einige Frames aufgerufen werden, und unsere holografischen Datenaktualisierungen sollten einmal pro Frame geschehen.


Über **AppMain::Update:**

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Positionieren und Drehen von Hologrammen in Ihrem Koordinatensystem

Wenn Sie in einem einzelnen Koordinatensystem arbeiten, wie dies bei der Vorlage mit dem **SpatialStationaryReferenceFrame** der Fall ist, ist dieser Prozess nicht anders als sonst in 3D-Grafiken. Hier drehen wir den Würfel und legen die Modellmatrix basierend auf der Position im stationären Koordinatensystem fest.

Von **SpinningCubeRenderer::Update:**

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

**Beachten Sie erweiterte Szenarien:** Der sich drehende Würfel ist ein einfaches Beispiel für die Position eines Hologramms innerhalb eines einzelnen Referenzrahmens. Es ist auch möglich, mehrere [SpatialCoordinateSystems](coordinate-systems-in-directx.md) gleichzeitig im gleichen gerenderten Frame zu verwenden.

### <a name="update-constant-buffer-data"></a>Aktualisieren konstanter Pufferdaten

Modelltransformationen für Inhalte werden wie gewohnt aktualisiert. Sie haben nun gültige Transformationen für das Koordinatensystem berechnet, das Sie rendern werden.

Von **SpinningCubeRenderer::Update:**

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

Wie sieht es mit Ansichts- und Projektionstransformationen aus? Um optimale Ergebnisse zu erzielen, möchten wir warten, bis wir für unsere Zeichnen-Aufrufe fast bereit sind, bevor wir diese erhalten.

## <a name="render-the-current-frame"></a>Rendern des aktuellen Frames

Das Rendern auf Windows Mixed Reality sich nicht wesentlich vom Rendern auf einem 2D-Mono-Display, aber es gibt einige Unterschiede:
* Holografische Framevorhersagen sind wichtig. Je näher die Vorhersage an der Vorhersage liegt, wenn Ihr Frame dargestellt wird, desto besser sehen Ihre Hologramme aus.
* Windows Mixed Reality steuert die Kameraansichten. Rendern Sie in jedem, da der holografische Rahmen sie später für Sie präsentiert.
* Es wird empfohlen, Stereorendering mithilfe von Instanzzeichnungen in ein Renderzielarray zu erstellen. Die holografische App-Vorlage verwendet den empfohlenen Ansatz der Instanzzeichnung in ein Renderzielarray, das eine Renderzielansicht auf einem **Texture2DArray verwendet.**
* Wenn Sie rendern möchten, ohne Stereo-Instancing zu verwenden, müssen Sie zwei RenderTargetViews ohne Array erstellen, eine für jedes Auge. Jedes RenderTargetViews-Objekt verweist auf einen der beiden Slices im **Texture2DArray,** das der App vom System bereitgestellt wird. Dies wird nicht empfohlen, da es in der Regel langsamer als die Verwendung der -Instancing ist.

### <a name="get-an-updated-holographicframe-prediction"></a>Erhalten einer aktualisierten HolographicFrame-Vorhersage

Durch das Aktualisieren der Framevorhersage wird die Effektivität der Bildstabilisierung verbessert. Sie erhalten eine genauere Positionierung von Hologrammen aufgrund der kürzeren Zeit zwischen der Vorhersage und dem Zeitpunkt, zu dem der Frame für den Benutzer sichtbar ist. Im Idealfall aktualisieren Sie Ihre Framevorhersage direkt vor dem Rendering.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Rendern für jede Kamera

Schleife der Kamera, die in der Vorhersage dargestellt wird, und Rendern für jede Kamera in diesem Satz.

**Einrichten des Renderingpasses**

Windows Mixed Reality verwendet stereoaktives Rendering, um die Tiefe zu verbessern und stereoaktiv zu rendern, sodass sowohl die linke als auch die rechte Anzeige aktiv sind. Beim Stereodarstellungsrendering gibt es einen Offset zwischen den beiden Anzeigen, den das Gehirn als tatsächliche Tiefe abstimmen kann. In diesem Abschnitt wird das Stereo-Rendering mithilfe von Instancing mithilfe von Code aus der Windows Holographic-App-Vorlage behandelt.

Jede Kamera verfügt über ein eigenes Renderziel (Hintergrundpuffer) und Ansichts- und Projektionsmatrizen im holografischen Raum. Ihre App muss alle anderen kamerabasierten Ressourcen , z. B. den Tiefenpuffer, pro Kamera erstellen. In der Windows Holographic-App-Vorlage stellen wir eine Hilfsklasse zum Bündeln dieser Ressourcen in DX::CameraResources zur Verfügung. Beginnen Sie mit dem Einrichten der Renderzielansichten:

Aus **AppMain::Render:**

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

**Verwenden der Vorhersage zum Erhalten der Ansichts- und Projektionsmatrizen für die Kamera**

Die Ansichts- und Projektionsmatrizen für jede holografische Kamera ändern sich mit jedem Frame. Aktualisieren Sie die Daten im konstanten Puffer für jede holografische Kamera. Tun Sie dies, nachdem Sie die Vorhersage aktualisiert haben, und bevor Sie Zeichnen-Aufrufe für diese Kamera machen.

Aus **AppMain::Render:**

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

Hier zeigen wir, wie die Matrizen aus der Kamerapose erworben werden. Während dieses Vorgangs erhalten wir auch den aktuellen Viewport für die Kamera. Beachten Sie, wie wir ein Koordinatensystem bereitstellen: Dies ist das gleiche Koordinatensystem, das wir zum Verstehen des Anvierens verwendet haben, und es ist dasselbe, das wir zum Positionieren des sich drehenden Würfels verwendet haben.


Von **CameraResources::UpdateViewProjectionBuffer:**

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

Der Viewport sollte für jeden Frame festgelegt werden. Ihr Vertex-Shader (zumindest) benötigt im Allgemeinen Zugriff auf die Ansichts-/Projektionsdaten.


Von **CameraResources::AttachViewProjectionBuffer:**

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

**Rendern Sie in den Kamera-Hintergrundpuffer, und führen Sie einen Commit für den Tiefenpuffer aus:**

Es empfiehlt sich, zu überprüfen, ob **TryGetViewTransform** erfolgreich war, bevor Sie versuchen, die Ansichts-/Projektionsdaten zu verwenden, da Ihre App für diesen Frame nicht rendern kann, wenn das Koordinatensystem nicht lösbar ist (z. B. wenn die Nachverfolgung unterbrochen wurde). Die Vorlage ruft **Render** für den drehenden Cube nur auf, wenn die **CameraResources-Klasse** ein erfolgreiches Update angibt.

Windows Mixed Reality enthält Funktionen für die [Bildstabilität,](../platform-capabilities-and-apis/hologram-stability.md) um Hologramme an der Position zu halten, an der ein Entwickler oder Benutzer sie in der Welt positioniert. Die Bildstabilität hilft dabei, die Latenz in einer Renderingpipeline auszublenden, um die besten holografischen Erfahrungen für Benutzer sicherzustellen. Ein Fokuspunkt kann angegeben werden, um die Bildunterstärkung noch weiter zu verbessern, oder ein Tiefenpuffer kann bereitgestellt werden, um eine optimierte Bildstabilität in Echtzeit zu berechnen.

Um optimale Ergebnisse zu erzielen, sollte Ihre App mithilfe der <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer-API</a> einen Tiefenpuffer bereitstellen. Windows Mixed Reality können dann Geometrieinformationen aus dem Tiefenpuffer verwenden, um die Bildstabilität in Echtzeit zu optimieren. Die Windows Holographic-App-Vorlage committet standardmäßig den Tiefenpuffer der App und hilft dabei, die Hologrammstabilität zu optimieren.

Über **AppMain::Render:**

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
>Windows verarbeitet Ihre Tiefentextur auf der GPU, daher muss es möglich sein, Ihren Tiefenpuffer als Shaderressource zu verwenden. Die id3D11Texture2D, die Sie erstellen, sollte in einem typlosen Format vorliegen und als Shaderressourcenansicht gebunden werden. Im Folgenden finden Sie ein Beispiel für das Erstellen einer Tiefentextur, die für die Bildinstabilisierung festgelegt werden kann.

Code für **die Erstellung von Tiefenpufferressourcen für CommitDirect3D11DepthBuffer:**

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

**Zeichnen holografischer Inhalte**

Die Windows Holographic-App-Vorlage rendert Inhalte in Stereo, indem die empfohlene Technik verwendet wird, instanzierte Geometrie in ein Texture2DArray der Größe 2 zu zeichnen. Sehen wir uns den Instanziierungsteil und die Funktionsweise auf Windows Mixed Reality an.

Von **SpinningCubeRenderer::Render**:

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

Jede Instanz greift auf eine andere Ansichts-/Projektionsmatrix aus dem Konstantenpuffer zu. Hier ist die konstante Pufferstruktur, die nur ein Array von zwei Matrizen ist.

Aus **VertexShaderShared.hlsl**, enthalten durch **VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

Der Renderzielarrayindex muss für jedes Pixel festgelegt werden. Im folgenden Codeausschnitt wird output.viewId der **SV_RenderTargetArrayIndex** Semantik zugeordnet. Dies erfordert Unterstützung für ein optionales Direct3D 11.3-Feature, mit dem die Indexsemantik des Renderzielarrays in jeder Shaderphase festgelegt werden kann.

Über **VPRTVertexShader.hlsl**:

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

Aus **VertexShaderShared.hlsl**, enthalten durch **VPRTVertexShader.hlsl**:

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

Wenn Sie Ihre vorhandenen instanzierten Zeichnungstechniken mit dieser Methode zum Zeichnen in ein Stereorenderingzielarray verwenden möchten, zeichnen Sie doppelt so viele Instanzen wie gewohnt. Dividieren Sie **input.instId im** Shader durch 2, um die ursprüngliche Instanz-ID abzurufen, die in einen Puffer von Objektdaten indiziert werden kann (z. B.): `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Wichtiger Hinweis zum Rendern von Stereoinhalten auf HoloLens

Windows Mixed Reality unterstützt die Möglichkeit, den Renderzielarrayindex aus einer beliebigen Shaderphase festzulegen. Normalerweise ist dies eine Aufgabe, die aufgrund der Art und Weise, wie die Semantik für Direct3D 11 definiert ist, nur in der Geometry Shader-Phase ausgeführt werden konnte. Hier sehen Sie ein vollständiges Beispiel für das Einrichten einer Renderingpipeline, bei der nur die Vertex- und Pixel-Shaderstufen festgelegt sind. Der Shadercode ist wie oben beschrieben.

Von **SpinningCubeRenderer::Render**:

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Wichtiger Hinweis zum Rendern auf Geräten ohne HoloLens

Das Festlegen des Renderzielarrayindexes im Vertex-Shader erfordert, dass der Grafiktreiber ein optionales Direct3D 11.3-Feature unterstützt, das HoloLens unterstützt. Ihre App kann genau diese Technik für das Rendering sicher implementieren, und alle Anforderungen für die Ausführung auf dem Microsoft HoloLens werden erfüllt.

Es kann auch der Fall sein, dass Sie den HoloLens Emulator verwenden möchten, der ein leistungsstarkes Entwicklungstool für Ihre holografische App sein kann und Windows Mixed Reality immersive Headset-Geräte unterstützt, die an Windows 10 PCs angefügt sind. Die Unterstützung für den nicht HoloLens Renderingpfad – für alle Windows Mixed Reality – ist ebenfalls in die Windows Holographic-App-Vorlage integriert. Im Vorlagencode finden Sie Code, mit dem Ihre holografische App auf dem ENTWICKLUNGS-PC auf der GPU ausgeführt werden kann. So überprüft die **DeviceResources-Klasse** diese optionale Featureunterstützung.

Über **DeviceResources::CreateDeviceResources:**

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Um das Rendering ohne dieses optionale Feature zu unterstützen, muss Ihre App einen Geometrie-Shader verwenden, um den Index des Renderzielarrays festzulegen. Dieser Codeausschnitt wird *nach* **VSSetConstantBuffers** und *vor* **PSSetShader** im Codebeispiel im vorherigen Abschnitt hinzugefügt, in dem erläutert wird, wie Stereo auf HoloLens gerendert wird.

Von **SpinningCubeRenderer::Render**:

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

**HLSL HINWEIS:** In diesem Fall müssen Sie auch einen leicht geänderten Vertex-Shader laden, der den Renderzielarrayindex mithilfe einer immer zulässigen Shadersemantik wie TEXCOORD0 an den Geometry-Shader übergibt. Der geometry-Shader muss keine Arbeit erledigen. der Geometrie-Shader der Vorlage durchläuft alle Daten, mit Ausnahme des Renderzielarrayindexes, der zum Festlegen der SV_RenderTargetArrayIndex Semantik verwendet wird.

App-Vorlagencode für **GeometryShader.hlsl:**

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint instId         : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint rtvId          : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a>Anzahl

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Aktivieren des holografischen Rahmens zum Darstellen der Swapkette

Mit Windows Mixed Reality steuert das System die Swapkette. Das System verwaltet dann die Darstellung von Frames für jede holografische Kamera, um eine hochwertige Benutzererfahrung sicherzustellen. Außerdem wird ein Viewportupdate für jeden Frame für jede Kamera zur Optimierung von Systemaspekten wie bildstabiler oder Mixed Reality-Aufnahme. Daher ruft eine holografische App, die DirectX verwendet, **Present** in einer DXGI-Swapkette nicht auf. Stattdessen verwenden Sie die <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame-Klasse,</a> um alle Swapchains für einen Frame darzustellen, sobald Sie mit dem Zeichnen fertig sind.

Über **DeviceResources::P Resent:**

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

Standardmäßig wartet diese API, bis der Frame abgeschlossen ist, bevor er zurückgegeben wird. Holografische Apps sollten warten, bis der vorherige Frame abgeschlossen ist, bevor sie mit der Arbeit an einem neuen Frame beginnen, da dies die Latenz reduziert und bessere Ergebnisse aus holografischen Framevorhersagen ermöglicht. Dies ist keine harte Regel. Wenn Das Rendern von Frames länger als eine Bildschirmaktualisierung dauert, können Sie diese Wartezeit deaktivieren, indem Sie den HolographicFramePresentWaitBehavior-Parameter an <a href="/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>übergeben. In diesem Fall würden Sie wahrscheinlich einen asynchronen Renderingthread verwenden, um eine kontinuierliche Auslastung der GPU aufrechtzuerhalten. Die Aktualisierungsrate des HoloLens Geräts beträgt 60 Hz, wobei ein Frame eine Dauer von ca. 16 ms hat. Geräte mit immersivem Headset können zwischen 60 hz und 90 Hz reichen. Beim Aktualisieren der Anzeige bei 90 Hz hat jeder Frame eine Dauer von ca. 11 ms.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Behandeln von DeviceLost-Szenarien in Zusammenarbeit mit HolographicFrame

DirectX 11-Apps möchten in der Regel das HRESULT überprüfen, das von der **Present-Funktion** der DXGI-Swapkette zurückgegeben wird, um zu ermitteln, ob ein **DeviceLost-Fehler** aufgetreten ist. Die <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame-Klasse</a> behandelt dies für Sie. Überprüfen Sie das zurückgegebene <a href="/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult,</a> um herauszufinden, ob Sie das Direct3D-Gerät und gerätebasierte Ressourcen freigeben und neu erstellen müssen.

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

Wenn das Direct3D-Gerät verloren gegangen ist und Sie es neu erstellt haben, müssen Sie <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> anweisen, mit der Verwendung des neuen Geräts zu beginnen. Die Swapkette wird für dieses Gerät neu erstellt.

Über **DeviceResources::InitializeUsingHolographicSpace:**

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

Sobald Ihr Frame angezeigt wird, können Sie zur Hauptprogrammschleife zurückkehren und zulassen, dass er mit dem nächsten Frame fortzufahren ist.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>Hybridgrafik-PCs und Mixed Reality-Anwendungen

Windows 10 Creators Update PCs können sowohl mit diskreten **als auch** mit integrierten GPUs konfiguriert werden. Bei diesen Computertypen wählen Windows den Adapter aus, mit dem das Headset verbunden ist. Anwendungen müssen sicherstellen, dass das directX-Gerät, das es erstellt, denselben Adapter verwendet.

Der allgemeine Direct3D-Beispielcode veranschaulicht das Erstellen eines DirectX-Geräts mithilfe des Standardhardwareadapters, der auf einem Hybridsystem möglicherweise nicht mit dem für das Headset verwendeten identisch ist.

Um Probleme zu umgehen, verwenden Sie die <a href="/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a> aus <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() oder <a href="/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId(). Diese adapterId kann dann verwendet werden, um den richtigen DXGIAdapter mit IDXGIFactory4.EnumAdapterByLuid auszuwählen.

Über **DeviceResources::InitializeUsingHolographicSpace:**

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

Code zum **Aktualisieren von DeviceResources::CreateDeviceResources zur Verwendung von IDXGIAdapter**

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

**Hybridgrafik und Media Foundation**

Die Verwendung von Media Foundation auf Hybridsystemen kann zu Problemen führen, bei denen Video nicht gerendert wird oder die Videotextur beschädigt ist, da Media Foundation standardmäßig ein Systemverhalten verwendet. In einigen Szenarien ist das Erstellen einer separaten ID3D11Device erforderlich, um Multithreading zu unterstützen, und die richtigen Erstellungsflags sind festgelegt.

Beim Initialisieren von ID3D11Device muss D3D11_CREATE_DEVICE_VIDEO_SUPPORT Flag als Teil der D3D11_CREATE_DEVICE_FLAG definiert werden. Nachdem das Gerät und der Kontext erstellt wurden, rufen <a href="/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">Sie SetMultithreadProtected</a> auf, um Multithreading zu aktivieren. Verwenden Sie zum Zuordnen des Geräts zur Zuordnen des GERÄTs zum <a href="/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">16.</a> <a href="/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank"></a>

Code zum **Zuordnen einer ID3D11Device zu EINEMDXGIDeviceManager:**

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a>Siehe auch
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md)
* [Verwendung des HoloLens-Emulators](../platform-capabilities-and-apis/using-the-hololens-emulator.md)