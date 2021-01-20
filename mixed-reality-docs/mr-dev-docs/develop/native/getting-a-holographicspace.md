---
title: Abrufen eines HolographicSpace-Objekts
description: Erfahren Sie, wie Sie die holographicspace-API für Holographic Rendering und räumliche Eingaben in ihren Mixed Reality-Apps verwenden.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, holographicspace, corewindow, räumliche Eingabe, Rendering, Austausch Kette, Holographic Frame, Update Schleife, Spiel Schleife, Frame der Referenz, loerability, Beispielcode, Exemplarische Vorgehensweise, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 215c3cbacd4c7975d05b3a1b3f3992c9198642f7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580915"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="e45a7-104">Abrufen eines HolographicSpace-Objekts</span><span class="sxs-lookup"><span data-stu-id="e45a7-104">Getting a HolographicSpace</span></span>

> [!NOTE]
> <span data-ttu-id="e45a7-105">Dieser Artikel bezieht sich auf die älteren WinRT-APIs.</span><span class="sxs-lookup"><span data-stu-id="e45a7-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="e45a7-106">Bei neuen nativen App-Projekten wird die Verwendung der **[openxr-API](openxr-getting-started.md)** empfohlen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="e45a7-107">Die <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">holographicspace</a> -Klasse ist Ihr Portal in der Holographic World.</span><span class="sxs-lookup"><span data-stu-id="e45a7-107">The <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="e45a7-108">Es steuert das immersive Rendering, stellt Kameradaten bereit und ermöglicht den Zugriff auf APIs für räumliche Argumente.</span><span class="sxs-lookup"><span data-stu-id="e45a7-108">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="e45a7-109">Sie erstellen einen für das <a href="/api/windows.ui.core.corewindow" target="_blank">corewindow</a> ihrer UWP-APP oder das HWND ihrer Win32-app.</span><span class="sxs-lookup"><span data-stu-id="e45a7-109">You'll create one for your UWP app's <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="e45a7-110">Einrichten des Holographic-Raums</span><span class="sxs-lookup"><span data-stu-id="e45a7-110">Set up the holographic space</span></span>

<span data-ttu-id="e45a7-111">Das Erstellen des Holographic Space-Objekts ist der erste Schritt beim Erstellen der Windows Mixed Reality-app.</span><span class="sxs-lookup"><span data-stu-id="e45a7-111">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="e45a7-112">Herkömmliche Windows-apps werden in einer Direct3D-Swap-Kette gerenttet, die für das Kern Fenster ihrer Anwendungs Ansicht erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="e45a7-112">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="e45a7-113">Diese austauschkette wird in der Holographic-Benutzeroberfläche als Slate angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e45a7-113">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="e45a7-114">Erstellen Sie einen holografischen Raum für das Kern Fenster anstelle einer Swapkette, um die Anwendungs Ansicht anstelle eines 2D-Slate zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e45a7-114">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="e45a7-115">Durch das präsentieren von Holographic Frames, die von diesem holografischen Raum erstellt werden, wird Ihre APP in den Vollbild-Rendermodus versetzt.</span><span class="sxs-lookup"><span data-stu-id="e45a7-115">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="e45a7-116">Suchen Sie für eine **UWP-App** , [die mit der *Holographic DirectX 11-app (universelle Windows-Vorlage)* beginnt](creating-a-holographic-directx-project.md), in der **SetWindow** -Methode in appview. cpp nach diesem Code:</span><span class="sxs-lookup"><span data-stu-id="e45a7-116">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="e45a7-117">Wenn Sie eine Win32- **App** entwickeln, [die mit dem *basichologram* Win32](creating-a-holographic-directx-project.md#creating-a-win32-project)-Beispiel beginnt, sehen Sie sich unter " **App:: kreatewindowandholographicspace** " einen HWND-Beispiel an.</span><span class="sxs-lookup"><span data-stu-id="e45a7-117">If you're building a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an HWND example.</span></span> <span data-ttu-id="e45a7-118">Anschließend können Sie es in ein immersives HWND konvertieren, indem Sie einen zugeordneten <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">holographicspace</a>erstellen:</span><span class="sxs-lookup"><span data-stu-id="e45a7-118">You can then convert it into an immersive HWND by creating an associated <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>

```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="e45a7-119">Nachdem Sie einen holographicspace für das UWP-corewindow oder das Win32-HWND erhalten haben, kann der holographicspace Holographic-Kameras verarbeiten, Koordinatensysteme erstellen und Holographic-Rendering durchführen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-119">Once you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, the HolographicSpace can handle holographic cameras, create coordinate systems, and do holographic rendering.</span></span> <span data-ttu-id="e45a7-120">Der aktuelle holografische Raum wird an mehreren Stellen in der DirectX-Vorlage verwendet:</span><span class="sxs-lookup"><span data-stu-id="e45a7-120">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="e45a7-121">Die **deviceresources** -Klasse muss einige Informationen aus dem holographicspace-Objekt zum Erstellen des Direct3D-Geräts erhalten.</span><span class="sxs-lookup"><span data-stu-id="e45a7-121">The **DeviceResources** class needs to get some information from the HolographicSpace object to create the Direct3D device.</span></span> <span data-ttu-id="e45a7-122">Dies ist die DXGI-Adapter-ID, die der Holographic-Anzeige zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="e45a7-122">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="e45a7-123">Die <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">holographicspace</a> -Klasse verwendet das Direct3D 11-Gerät Ihrer APP zum Erstellen und verwalten Geräte basierter Ressourcen, z. b. die Back Puffer für jede holografische Kamera.</span><span class="sxs-lookup"><span data-stu-id="e45a7-123">The <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="e45a7-124">Wenn Sie wissen möchten, was diese Funktion im Hintergrund vornimmt, finden Sie Sie in deviceresources. cpp.</span><span class="sxs-lookup"><span data-stu-id="e45a7-124">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="e45a7-125">Die Funktion **deviceresources:: initializeusingholographicspace** zeigt, wie Sie den Adapter abrufen, indem Sie die LUID – suchen und einen Standard Adapter auswählen, wenn kein bevorzugter Adapter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="e45a7-125">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="e45a7-126">Die Hauptklasse der APP verwendet den Holographic-Speicherplatz aus **appview:: SetWindow** oder **App:: kreatewindowandholographicspace** für Updates und Rendering.</span><span class="sxs-lookup"><span data-stu-id="e45a7-126">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="e45a7-127">In den folgenden Abschnitten werden Funktionsnamen aus der Vorlage wie **appview:: SetWindow** erwähnt, die voraussetzen, dass Sie von der Holographic UWP-App-Vorlage aus begonnen haben. die Code Ausschnitte, die Sie sehen, gelten gleichermaßen für UWP-und Win32-apps.</span><span class="sxs-lookup"><span data-stu-id="e45a7-127">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="e45a7-128">Als nächstes betrachten wir den Setup Prozess, für den **setholographicspace** in der appmain-Klasse verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="e45a7-128">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="e45a7-129">Kamera Ereignisse abonnieren, Kamera Ressourcen erstellen und entfernen</span><span class="sxs-lookup"><span data-stu-id="e45a7-129">Subscribe to camera events, create, and remove camera resources</span></span>

<span data-ttu-id="e45a7-130">Der Holographic-Inhalt Ihrer APP befindet sich in seinem holografischen Raum und wird über eine oder mehrere Holographic-Kameras angezeigt, die verschiedene Perspektiven in der Szene darstellen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-130">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras, which represent different perspectives on the scene.</span></span> <span data-ttu-id="e45a7-131">Nun, da Sie über den Holographic-Raum verfügen, können Sie Daten für Holographic-Kameras empfangen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-131">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="e45a7-132">Ihre APP muss auf **cameraadded** -Ereignisse reagieren, indem Sie alle für diese Kamera spezifischen Ressourcen erstellt.</span><span class="sxs-lookup"><span data-stu-id="e45a7-132">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera.</span></span> <span data-ttu-id="e45a7-133">Ein Beispiel für eine solche Ressource ist die Ansicht für das Renderziel des hinterpuffers.</span><span class="sxs-lookup"><span data-stu-id="e45a7-133">An example of such a resource is your back buffer render target view.</span></span> <span data-ttu-id="e45a7-134">Sie können diesen Code in der **deviceresources:: setholographicspace** -Funktion sehen, die von **appview:: SetWindow** aufgerufen wird, bevor die APP Holographic Frames erstellt:</span><span class="sxs-lookup"><span data-stu-id="e45a7-134">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="e45a7-135">Ihre APP muss auch auf die **camerareverschoten** Ereignisse reagieren, indem Sie Ressourcen freigibt, die für diese Kamera erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="e45a7-135">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="e45a7-136">Aus **deviceresources:: CSpace**:</span><span class="sxs-lookup"><span data-stu-id="e45a7-136">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="e45a7-137">Die Ereignishandler müssen einige Aufgaben durchführen, um die reibungslose Ausführung des Holographic-Renderings und das Rendering Ihrer APP zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="e45a7-137">The event handlers must complete some work to keep holographic rendering flowing smoothly, and your app rendering at all.</span></span> <span data-ttu-id="e45a7-138">Lesen Sie den Code und die Kommentare für die Details: Sie können in ihrer Hauptklasse nach **oncameraadded** und **oncamerareverschoden** Code suchen, um zu verstehen, wie die **m_cameraResources** Map von **deviceresources** verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="e45a7-138">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="e45a7-139">Zurzeit konzentrieren wir uns auf appmain und das Setup, damit Ihre APP über Holographic-Kameras informiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="e45a7-139">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="e45a7-140">Vor diesem Hintergrund ist es wichtig, die folgenden beiden Anforderungen zu berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="e45a7-140">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="e45a7-141">Für den Ereignishandler " **cameraadded** " kann die APP asynchron ausgeführt werden, um das Erstellen von Ressourcen und das Laden von Assets für die neue Holographic-Kamera abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-141">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="e45a7-142">Apps, die mehr als einen Frame zum Ausführen dieser Arbeit benötigen, sollten eine Verzögerung anfordern und die Verzögerung nach dem asynchronen Laden vervollständigen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-142">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously.</span></span> <span data-ttu-id="e45a7-143">Eine [ppl-Aufgabe](/cpp/parallel/concrt/parallel-patterns-library-ppl) kann verwendet werden, um asynchrone Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-143">A [PPL task](/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="e45a7-144">Ihre APP muss sicherstellen, dass Sie sofort an die Kamera gerehehbt, wenn Sie den Ereignishandler verlässt oder wenn Sie die Verzögerung abschließt.</span><span class="sxs-lookup"><span data-stu-id="e45a7-144">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="e45a7-145">Das Beenden des Ereignis Handlers oder das Abschließen der Verzögerung weist das System darauf hin, dass Ihre APP nun bereit ist, Holographic Frames mit dieser Kamera zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-145">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="e45a7-146">Wenn die APP ein Ereignis vom Typ " **camerareverschobe** " empfängt, muss Sie alle Verweise auf den Hintergrund Puffer freigeben und die Funktion sofort beenden.</span><span class="sxs-lookup"><span data-stu-id="e45a7-146">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="e45a7-147">Dies schließt renderzielsichten und alle anderen Ressourcen ein, die möglicherweise einen Verweis auf die [idxgiresource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)enthalten.</span><span class="sxs-lookup"><span data-stu-id="e45a7-147">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="e45a7-148">Außerdem muss die APP sicherstellen, dass der Hintergrund Puffer nicht als Renderziel angefügt wird, wie in **cameraresources:: releaseresourcesforbackbuffer** gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e45a7-148">The app must also ensure that the back buffer isn't attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="e45a7-149">Um die Dinge zu beschleunigen, kann Ihre APP den Hintergrund Puffer freigeben und dann eine Aufgabe starten, um alle anderen Löschvorgänge für die Kamera asynchron abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-149">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other tear down work for the camera.</span></span> <span data-ttu-id="e45a7-150">Die Vorlage für die Holographic-app enthält eine ppl-Aufgabe, die Sie zu diesem Zweck verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e45a7-150">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="e45a7-151">Wenn Sie bestimmen möchten, wann eine hinzugefügte oder entfernte Kamera im Frame angezeigt wird, verwenden Sie die Eigenschaften **holographicframe** [addedkameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) und [removedkameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .</span><span class="sxs-lookup"><span data-stu-id="e45a7-151">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="e45a7-152">Erstellen eines Bezugsrahmens für den Holographic-Inhalt</span><span class="sxs-lookup"><span data-stu-id="e45a7-152">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="e45a7-153">Der Inhalt Ihrer APP muss in einem [räumlichen Koordinatensystem](coordinate-systems-in-directx.md) positioniert werden, das im holographicspace gerendert werden soll.</span><span class="sxs-lookup"><span data-stu-id="e45a7-153">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="e45a7-154">Das System stellt zwei primäre Frame Frames bereit, mit denen Sie ein Koordinatensystem für die Hologramme einrichten können.</span><span class="sxs-lookup"><span data-stu-id="e45a7-154">The system provides two primary frames of reference, which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="e45a7-155">Es gibt zwei Arten von Bezugs Frames in Windows Holographic: Verweis Rahmen, die an das Gerät angeschlossen sind, und Bezugsrahmen, die stationär bleiben, wenn das Gerät die Umgebung des Benutzers durchläuft.</span><span class="sxs-lookup"><span data-stu-id="e45a7-155">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="e45a7-156">In der Holographic-App-Vorlage wird standardmäßig ein stationärer Verweis Rahmen verwendet. Dies ist eine der einfachsten Möglichkeiten zum Rendering von weltweit gesperrten holograms.</span><span class="sxs-lookup"><span data-stu-id="e45a7-156">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="e45a7-157">Stationäre Verweis Rahmen sind so konzipiert, dass Positionen in der Nähe des aktuellen Speicher Orts des Geräts stabilisiert werden.</span><span class="sxs-lookup"><span data-stu-id="e45a7-157">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="e45a7-158">Dies bedeutet, dass die Koordinaten, die sich weiter vom Gerät unterscheiden, relativ zur Benutzerumgebung geringfügig abweichen können, da das Gerät mehr über den Platz herum erfährt.</span><span class="sxs-lookup"><span data-stu-id="e45a7-158">This means that coordinates further from the device can drift slightly relative to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="e45a7-159">Es gibt zwei Möglichkeiten, einen stationären Frame des Verweises zu erstellen: das Koordinatensystem aus der [räumlichen Phase](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)abzurufen oder den standardspaticator zu verwenden. <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank"></a></span><span class="sxs-lookup"><span data-stu-id="e45a7-159">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="e45a7-160">Wenn Sie eine Windows Mixed Reality-App für immersive Headsets erstellen, wird als Ausgangspunkt die [räumliche Phase](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)empfohlen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-160">If you're creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage).</span></span> <span data-ttu-id="e45a7-161">Die räumliche Phase enthält außerdem Informationen zu den Funktionen des immersiven Headsets, das vom Player getragen wird.</span><span class="sxs-lookup"><span data-stu-id="e45a7-161">The spatial stage also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="e45a7-162">Hier wird gezeigt, wie der <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">standardzuordnerstandard</a>verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e45a7-162">Here, we show how to use the default <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="e45a7-163">Der räumliche Serverlocatorpunkt stellt das Windows Mixed Reality-Gerät dar und verfolgt die Bewegung des Geräts und stellt Koordinatensysteme bereit, die relativ zum Speicherort verstanden werden können.</span><span class="sxs-lookup"><span data-stu-id="e45a7-163">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="e45a7-164">Aus **appmain:: onholographicdisplayisavailablechanged**:</span><span class="sxs-lookup"><span data-stu-id="e45a7-164">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="e45a7-165">Erstellen Sie den stationären Verweis Rahmen einmal, wenn die APP gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="e45a7-165">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="e45a7-166">Dies ist analog zum Definieren eines Weltkoordinaten Systems, wobei der Ursprung an der Position des Geräts platziert wird, wenn die APP gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="e45a7-166">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="e45a7-167">Dieser Referenzrahmen bewegt sich nicht mit dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="e45a7-167">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="e45a7-168">Aus **appmain:: abbildrfaden**:</span><span class="sxs-lookup"><span data-stu-id="e45a7-168">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="e45a7-169">Alle Verweis Rahmen sind Schwerpunkte ausgerichtet, was bedeutet, dass die y-Achse in Bezug auf die Benutzerumgebung "aufwärts" zeigt.</span><span class="sxs-lookup"><span data-stu-id="e45a7-169">All reference frames are gravity aligned, meaning that the y-axis points "up" in relation to the user's environment.</span></span> <span data-ttu-id="e45a7-170">Da Windows "rechtsseitige" Koordinatensysteme verwendet, stimmt die Richtung der – z-Achse mit der Vorwärtsrichtung überein, mit der das Gerät beim Erstellen des Verweis Rahmens konfrontiert wird.</span><span class="sxs-lookup"><span data-stu-id="e45a7-170">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="e45a7-171">Wenn Ihre APP eine exakte Platzierung einzelner holograms erfordert, verwenden Sie einen <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">spatialanchor</a> , um das einzelne – Hologramm an eine Position in der realen Welt zu verankern.</span><span class="sxs-lookup"><span data-stu-id="e45a7-171">When your app requires precise placement of individual holograms, use a <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="e45a7-172">Verwenden Sie z. b. einen räumlichen Anker, wenn der Benutzer einen Punkt angibt, der ein besonderes Interesse sein soll.</span><span class="sxs-lookup"><span data-stu-id="e45a7-172">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="e45a7-173">Anker Positionen werden nicht abweichen, Sie können jedoch angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="e45a7-173">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="e45a7-174">Wenn ein Anker angepasst wird, wird seine Position standardmäßig vor dem Abschluss der Korrektur in die nächsten Frames hineingebracht.</span><span class="sxs-lookup"><span data-stu-id="e45a7-174">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="e45a7-175">Abhängig von Ihrer Anwendung können Sie in diesem Fall die Anpassung auf andere Weise verarbeiten (indem Sie Sie z. b. verzögern, bis das – Hologramm nicht mehr in der Ansicht ist).</span><span class="sxs-lookup"><span data-stu-id="e45a7-175">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="e45a7-176">Die <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">rawcoordinatesystem</a> -Eigenschaft und die <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">rawcoordinatesystemadjusted</a> -Ereignisse ermöglichen diese Anpassungen.</span><span class="sxs-lookup"><span data-stu-id="e45a7-176">The <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="e45a7-177">Reagieren auf geänderte Ereignisse bei der Ereignis Änderung</span><span class="sxs-lookup"><span data-stu-id="e45a7-177">Respond to locatability changed events</span></span>

<span data-ttu-id="e45a7-178">Das Rendern von Welt gesperrten holograms erfordert, dass sich das Gerät selbst in der Welt finden muss.</span><span class="sxs-lookup"><span data-stu-id="e45a7-178">Rendering world-locked holograms requires the device to locate itself in the world.</span></span> <span data-ttu-id="e45a7-179">Dies ist möglicherweise aufgrund von Umgebungsbedingungen nicht immer möglich, und wenn dies der Fall ist, kann der Benutzer einen visuellen Hinweis auf die nach Verfolgungs Unterbrechung erwarten.</span><span class="sxs-lookup"><span data-stu-id="e45a7-179">This may not always be possible because of environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="e45a7-180">Diese visuelle Anzeige muss mithilfe von Verweis Frames gerendert werden, die mit dem Gerät verbunden sind, anstatt auf der ganzen Welt.</span><span class="sxs-lookup"><span data-stu-id="e45a7-180">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="e45a7-181">Ihre APP kann anfordern, dass Sie benachrichtigt werden, wenn die Nachverfolgung aus irgendeinem Grund unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="e45a7-181">Your app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="e45a7-182">Registrieren Sie sich für das loaufgeräterchanged-Ereignis, um zu erkennen, wann sich das Gerät in der Welt finden kann.</span><span class="sxs-lookup"><span data-stu-id="e45a7-182">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="e45a7-183">Aus **appmain:: abbildrfaden:**</span><span class="sxs-lookup"><span data-stu-id="e45a7-183">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="e45a7-184">Verwenden Sie dieses Ereignis dann, um zu bestimmen, wann holograms nicht auf der ganzen Welt gerendert werden können.</span><span class="sxs-lookup"><span data-stu-id="e45a7-184">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="e45a7-185">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e45a7-185">See also</span></span>
* [<span data-ttu-id="e45a7-186">Rendern in DirectX</span><span class="sxs-lookup"><span data-stu-id="e45a7-186">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="e45a7-187">Koordinatensysteme in DirectX</span><span class="sxs-lookup"><span data-stu-id="e45a7-187">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)