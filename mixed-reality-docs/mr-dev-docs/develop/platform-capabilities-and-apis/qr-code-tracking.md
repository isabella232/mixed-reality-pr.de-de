---
title: Nachverfolgen von QR-Codes
description: Erfahren Sie, wie Sie QR-Codes erkennen, Webcam-Funktionen hinzufügen und Koordinatensysteme in Mixed Reality-Apps auf HoloLens 2 verwalten.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: VR, LBE, standortbezogene Unterhaltung, VR-Arcade, Arcade, immersiv, QR, QR-Code, hololens2
ms.openlocfilehash: 9d3a5d9696fbf875b2e6a890ed837efc055a9e6e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394334"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="59df9-104">Nachverfolgen von QR-Codes</span><span class="sxs-lookup"><span data-stu-id="59df9-104">QR code tracking</span></span>

<span data-ttu-id="59df9-105">HoloLens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der Position jedes Codes in der realen Welt einrichten.</span><span class="sxs-lookup"><span data-stu-id="59df9-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="59df9-106">Sobald Sie die Webcam Ihres Geräts aktiviert haben, können Sie QR-Codes in den neuesten Versionen Ihrer Unreal- oder Unity-Projekte erkennen.</span><span class="sxs-lookup"><span data-stu-id="59df9-106">Once you enable your device's webcam, you'll be able to recognize QR codes in the latest versions of your Unreal or Unity projects.</span></span> <span data-ttu-id="59df9-107">Bevor Sie mit der Produktion [](#best-practices-for-qr-code-detection) arbeiten, empfehlen wir Ihnen, die bewährten Methoden zu verwenden, die wir am Ende des Artikels beschrieben haben.</span><span class="sxs-lookup"><span data-stu-id="59df9-107">Before going to production, we recommend following the [best practices](#best-practices-for-qr-code-detection) we've laid at the end of the article.</span></span>

## <a name="device-support"></a><span data-ttu-id="59df9-108">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="59df9-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="59df9-109">Funktion</span><span class="sxs-lookup"><span data-stu-id="59df9-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="59df9-110"><a href="/hololens/hololens1-hardware">HoloLens (1. Generation)</a></span><span class="sxs-lookup"><span data-stu-id="59df9-110"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="59df9-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="59df9-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="59df9-112"><a href="../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="59df9-112"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="59df9-113">QR-Code-Erkennung</span><span class="sxs-lookup"><span data-stu-id="59df9-113">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="59df9-114">️</span><span class="sxs-lookup"><span data-stu-id="59df9-114">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="59df9-115">✔️</span><span class="sxs-lookup"><span data-stu-id="59df9-115">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="59df9-116">✔️</span><span class="sxs-lookup"><span data-stu-id="59df9-116">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="59df9-117">Die QR-Code Nachverfolgung mit immersiven Windows Mixed Reality-Headsets auf Desktop-PCs wird unter Windows 10, Version 2004 und höher, unterstützt.</span><span class="sxs-lookup"><span data-stu-id="59df9-117">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="59df9-118">Verwenden Sie die Microsoft.MixedReality.QRCodeWatcher.IsSupported()-API, um zu bestimmen, ob die Funktion auf dem aktuellen Gerät unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="59df9-118">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="59df9-119">Abrufen des QR-Pakets</span><span class="sxs-lookup"><span data-stu-id="59df9-119">Getting the QR package</span></span>

<span data-ttu-id="59df9-120">Sie können das NuGet-Paket für die QR-Code-Erkennung [hier](https://nuget.org/Packages/Microsoft.MixedReality.QR) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="59df9-120">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="using-openxr"></a><span data-ttu-id="59df9-121">Verwenden von OpenXR</span><span class="sxs-lookup"><span data-stu-id="59df9-121">Using OpenXR</span></span>

<span data-ttu-id="59df9-122">Wenn Sie das OpenXR-Plug-In verwenden, greifen Sie von der [ `SpatialGraphNodeId` QR-API,](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) und verwenden Sie die `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API, um den QR-Code zu finden.</span><span class="sxs-lookup"><span data-stu-id="59df9-122">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="59df9-123">Als Referenz finden Sie ein [Beispielprojekt für](https://github.com/yl-msft/QRTracking) die QR-Nachverfolgung auf GitHub mit einer ausführlicheren Erläuterung der Verwendung für die [ `SpatialGraphNode` API.](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)</span><span class="sxs-lookup"><span data-stu-id="59df9-123">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="59df9-124">Erkennen von QR-Codes</span><span class="sxs-lookup"><span data-stu-id="59df9-124">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="59df9-125">Hinzufügen der Webcamfunktion</span><span class="sxs-lookup"><span data-stu-id="59df9-125">Adding the webcam capability</span></span>

<span data-ttu-id="59df9-126">Sie müssen Ihrem Manifest die Funktion `webcam` hinzufügen, um QR-Codes erkennen zu können.</span><span class="sxs-lookup"><span data-stu-id="59df9-126">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="59df9-127">Diese Funktion ist erforderlich, da die Daten innerhalb der erkannten Codes in der Umgebung des Benutzers möglicherweise vertrauliche Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="59df9-127">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="59df9-128">Die Berechtigung kann durch den Aufruf von `QRCodeWatcher.RequestAccessAsync()` angefordert werden:</span><span class="sxs-lookup"><span data-stu-id="59df9-128">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="59df9-129">_C#:_</span><span class="sxs-lookup"><span data-stu-id="59df9-129">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="59df9-130">_C++:_</span><span class="sxs-lookup"><span data-stu-id="59df9-130">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="59df9-131">Vor dem Erstellen eines QRCodeWatcher-Objekts muss die Berechtigung angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="59df9-131">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="59df9-132">Zwar ist die Funktion `webcam` für die QR-Code-Erkennung erforderlich, die Erkennung erfolgt jedoch mithilfe der Überwachungskameras des Geräts.</span><span class="sxs-lookup"><span data-stu-id="59df9-132">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="59df9-133">Dies bietet ein breiteres Sichtfeld für die Erkennung und längere Batterielaufzeiten im Vergleich mit der Erkennung über die Foto/Videokamera (FV) des Geräts.</span><span class="sxs-lookup"><span data-stu-id="59df9-133">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="59df9-134">Erkennen von QR-Codes in Unity</span><span class="sxs-lookup"><span data-stu-id="59df9-134">Detecting QR codes in Unity</span></span>

<span data-ttu-id="59df9-135">Sie können die API zur QR-Code-Erkennung in Unity ohne den Import des MRTK nutzen, wenn Sie das NuGet-Paket mithilfe von [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) installieren.</span><span class="sxs-lookup"><span data-stu-id="59df9-135">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="59df9-136">Wenn Sie ein Gefühl für die Funktion erwerben möchten, laden Sie die [Unity-Beispiel-App](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) herunter.</span><span class="sxs-lookup"><span data-stu-id="59df9-136">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="59df9-137">Die Beispiel-App enthält Beispiele zum Anzeigen eines holografischen Quadrats über QR-Codes und zugeordneten Daten wie GUID, physischer Größe, Zeitstempel und decodierten Daten.</span><span class="sxs-lookup"><span data-stu-id="59df9-137">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="59df9-138">Erkennen von QR-Codes in C++</span><span class="sxs-lookup"><span data-stu-id="59df9-138">Detecting QR codes in C++</span></span>

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="59df9-139">Abrufen des Koordinatensystems für einen QR-Code</span><span class="sxs-lookup"><span data-stu-id="59df9-139">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="59df9-140">Jeder erkannte QR-Code macht ein [räumliches Koordinatensystem verfügbar](../../design/coordinate-systems.md), das am QR-Code in der linken oberen Ecke des Schnellerkennungsquadrats oben links ausgerichtet ist:</span><span class="sxs-lookup"><span data-stu-id="59df9-140">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![QR-Code-Koordinatensystem](images/Qr-coordinatesystem.png) 

<span data-ttu-id="59df9-142">Wenn Sie das QR-SDK direkt verwenden, zeigt die Z-Achse zum Papier (nicht dargestellt) – bei der Konvertierung in Unity-Koordinaten zeigt die Z-Achse aus dem Papier heraus und ist linkshändig.</span><span class="sxs-lookup"><span data-stu-id="59df9-142">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="59df9-143">Das SpatialCoordinateSystem eines QR-Codes wird wie dargestellt ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="59df9-143">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="59df9-144">Sie können das Koordinatensystem von der Plattform abrufen, indem Sie <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> aufrufen und die SpatialGraphNodeId des Codes übergeben.</span><span class="sxs-lookup"><span data-stu-id="59df9-144">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="59df9-145">Der unten abgebildete C++-Code zeigt, wie ein Rechteck erstellt und mithilfe des Koordinatensystems des QR-Codes platziert wird:</span><span class="sxs-lookup"><span data-stu-id="59df9-145">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="59df9-146">Sie können die physische Größe verwenden, um das QR-Rechteck zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="59df9-146">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="59df9-147">Das Koordinatensystem kann verwendet werden, um den QR-Code zu zeichnen oder Hologramme an die Position anzufügen:</span><span class="sxs-lookup"><span data-stu-id="59df9-147">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="59df9-148">Insgesamt kann Ihr *QRCodeAddedHandler* etwa so aussehen:</span><span class="sxs-lookup"><span data-stu-id="59df9-148">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="59df9-149">Bewährte Methoden für die Erkennung von QR-Codes</span><span class="sxs-lookup"><span data-stu-id="59df9-149">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="59df9-150">Stille Zonen um QR-Codes herum</span><span class="sxs-lookup"><span data-stu-id="59df9-150">Quiet zones around QR Codes</span></span>

<span data-ttu-id="59df9-151">Um ordnungsgemäß gelesen zu werden, erfordern QR-Codes einen Rand, der alle Seiten des Codes umgibt.</span><span class="sxs-lookup"><span data-stu-id="59df9-151">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="59df9-152">Dieser Rand darf keine gedruckten Inhalte enthalten und sollte vier Module (ein einzelnes schwarzes Quadrat im Code) breit sein.</span><span class="sxs-lookup"><span data-stu-id="59df9-152">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="59df9-153">Die [QR-Spezifikation](https://www.qrcode.com/en/howto/code.html) enthält weitere Informationen zu stillen Zonen.</span><span class="sxs-lookup"><span data-stu-id="59df9-153">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="59df9-154">Beleuchtung und Hintergrund</span><span class="sxs-lookup"><span data-stu-id="59df9-154">Lighting and backdrop</span></span>
<span data-ttu-id="59df9-155">Die Erkennungsqualität von QR-Code reagiert auf wechselnde Beleuchtungs- und Hintergrundverhältnisse.</span><span class="sxs-lookup"><span data-stu-id="59df9-155">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="59df9-156">Drucken Sie in einer hell beleuchteten Szene einen schwarzen Code auf einem grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="59df9-156">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="59df9-157">Drucken Sie andernfalls einen schwarzen QR-Code auf einem weißen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="59df9-157">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="59df9-158">Wenn der Hintergrund des Codes dunkel ist, probieren Sie einen schwarzen Code auf Grau,wenn Ihre Erkennungsrate niedrig ist.</span><span class="sxs-lookup"><span data-stu-id="59df9-158">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="59df9-159">Wenn der Hintergrund relativ hell ist, sollte ein gewöhnlicher Code gut funktionieren.</span><span class="sxs-lookup"><span data-stu-id="59df9-159">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="59df9-160">Größe von QR-Codes</span><span class="sxs-lookup"><span data-stu-id="59df9-160">Size of QR codes</span></span>
<span data-ttu-id="59df9-161">Windows Mixed Reality-Geräte funktionieren nicht mit QR-Codes, deren Seiten kleiner als jeweils 5 cm sind.</span><span class="sxs-lookup"><span data-stu-id="59df9-161">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="59df9-162">Bei QR-Code mit einer Kantenlänge zwischen 5 und 10 cm müssen Sie recht nah herangehen, um den Code zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="59df9-162">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="59df9-163">Die Erkennung von Codes in dieser Größe dauert außerdem länger.</span><span class="sxs-lookup"><span data-stu-id="59df9-163">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="59df9-164">Die genaue Zeit, die zum Erkennen von Codes benötigt wird, hängt nicht nur von der Größe der QR-Codes ab, sondern auch von der Entfernung des Codes.</span><span class="sxs-lookup"><span data-stu-id="59df9-164">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="59df9-165">Näher an den Code heranzugehen, hilft dabei, Größenprobleme zu beheben.</span><span class="sxs-lookup"><span data-stu-id="59df9-165">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="59df9-166">Abstand und Winkelposition gegenüber dem QR-Code</span><span class="sxs-lookup"><span data-stu-id="59df9-166">Distance and angular position from the QR code</span></span>
<span data-ttu-id="59df9-167">Die Überwachungskameras besitzen eine eingeschränkte Detailauflösung.</span><span class="sxs-lookup"><span data-stu-id="59df9-167">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="59df9-168">Bei kleinen Codes – < 10 cm Kantenlänge – müssen Sie recht nah an den Code herangehen.</span><span class="sxs-lookup"><span data-stu-id="59df9-168">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="59df9-169">Für einen QR-Code der Version 1 mit einer Breite zwischen 10 und 25 cm liegt der Mindestabstand für die Erkennung zwischen 0,15 und 0,5 m.</span><span class="sxs-lookup"><span data-stu-id="59df9-169">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="59df9-170">Der Erkennungsabstand für die Größe nimmt linear zu, hängt aber auch von der QR-Version oder Modulgröße ab.</span><span class="sxs-lookup"><span data-stu-id="59df9-170">The detection distance for size increases linearly, but also depends on QR version or module size.</span></span> <span data-ttu-id="59df9-171">Je höher die Version, desto kleiner sind die Module, die nur von einer näheren Position erkannt werden können.</span><span class="sxs-lookup"><span data-stu-id="59df9-171">The higher the version, the smaller the modules, which can only be detected from a closer position.</span></span> <span data-ttu-id="59df9-172">Sie können auch Micro-QR-Codes ausprobieren, wenn die Entfernung der Erkennung länger sein soll.</span><span class="sxs-lookup"><span data-stu-id="59df9-172">You can also try micro QR codes if you want the distance of detection to be longer.</span></span> <span data-ttu-id="59df9-173">Die QR-Erkennung funktioniert in einem Winkelbereich von += 45°, um sicherzustellen, dass die Auflösung zum Erkennen des Codes ausreicht.</span><span class="sxs-lookup"><span data-stu-id="59df9-173">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59df9-174">Stellen Sie immer sicher, dass genügend Kontrast und ein ordnungsgemäßer Rahmen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="59df9-174">Always make sure you have enough contrast and a proper border.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="59df9-175">QR-Codes mit Logos</span><span class="sxs-lookup"><span data-stu-id="59df9-175">QR codes with logos</span></span>
<span data-ttu-id="59df9-176">QR-Codes mit Logos wurden nicht getestet und werden zurzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="59df9-176">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="59df9-177">Verwalten von QR-Codedaten</span><span class="sxs-lookup"><span data-stu-id="59df9-177">Managing QR code data</span></span>
<span data-ttu-id="59df9-178">Windows Mixed Reality-Geräte erkennen QR-Codes auf der Systemebene im Treiber.</span><span class="sxs-lookup"><span data-stu-id="59df9-178">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="59df9-179">Wenn das Gerät neu gestartet wird, sind die erkannten QR-Codes verschwunden und werden beim nächsten Mal wieder als neue Objekte erkannt.</span><span class="sxs-lookup"><span data-stu-id="59df9-179">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="59df9-180">Wir empfehlen, Ihre App so zu konfigurieren, dass QR-Codes, die älter als ein bestimmter Zeitstempel sind, ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="59df9-180">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="59df9-181">Aktuell unterstützt die API das Bereinigen des QR-Codeverlaufs nicht.</span><span class="sxs-lookup"><span data-stu-id="59df9-181">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="59df9-182">Platzierung von QR-Codes im Raum</span><span class="sxs-lookup"><span data-stu-id="59df9-182">QR code placement in a space</span></span>
<span data-ttu-id="59df9-183">Empfehlungen zur Platzierung von QR-Codes finden Sie unter [Umgebungsüberlegungen für HoloLens](/hololens/hololens-environment-considerations).</span><span class="sxs-lookup"><span data-stu-id="59df9-183">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="59df9-184">QR-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="59df9-184">QR API reference</span></span>

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a><span data-ttu-id="59df9-185">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="59df9-185">See also</span></span>
* [<span data-ttu-id="59df9-186">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="59df9-186">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="59df9-187"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="59df9-187"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>