---
title: Holographic-Remoting hinzufügen
description: Erläutert die Verwendung von Holographic Remoting zum Rendering von holograms in einem hololens über das Netzwerk.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, Holographic Remoting, Remote Rendering, Netzwerk Rendering, hololens, Remote holograms, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 809258d3387b5e45885c0eb207544c176f891a1d
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530306"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a><span data-ttu-id="c1bfe-104">Holographic-Remoting hinzufügen (hololens (erste Generation))</span><span class="sxs-lookup"><span data-stu-id="c1bfe-104">Add Holographic Remoting (HoloLens (first gen))</span></span>

>[!IMPORTANT]
> <span data-ttu-id="c1bfe-105">In diesem Dokument wird die Erstellung einer Host Anwendung für hololens 1 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="c1bfe-106">Die Host Anwendung für **hololens (1st Gen)** muss das nuget-Paketversion **1. x. x** verwenden.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="c1bfe-107">Dies bedeutet, dass für hololens 1 geschriebene Host Anwendungen nicht mit hololens 2 und umgekehrt kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="c1bfe-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c1bfe-108">HoloLens 2</span></span>

<span data-ttu-id="c1bfe-109">Hololens-Entwickler, die Holographic Remoting verwenden, müssen Ihre apps aktualisieren, damit Sie mit hololens 2 kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="c1bfe-110">Hierfür ist eine neue Version des nuget-Pakets "Holographic Remoting" erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="c1bfe-111">Stellen Sie sicher, dass Sie die Version 2.0.0.0 oder höher des Holographic Remoting-nuget-Pakets verwenden, wenn Sie eine Verbindung mit dem Holographic Remoting Player auf hololens 2 herstellen, da andernfalls die Verbindung fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-111">Be sure to use version 2.0.0.0 or above of the Holographic Remoting NuGet package when connecting to the Holographic Remoting Player on HoloLens 2 or the connection will fail.</span></span>

>[!NOTE]
> <span data-ttu-id="c1bfe-112">Anleitungen für hololens 2 finden Sie [hier](holographic-remoting-create-remote-wmr.md).</span><span class="sxs-lookup"><span data-stu-id="c1bfe-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-remote-wmr.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="c1bfe-113">Hinzufügen von Holographic Remoting zu Ihrer Desktop-oder UWP-App</span><span class="sxs-lookup"><span data-stu-id="c1bfe-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="c1bfe-114">Auf dieser Seite wird beschrieben, wie Sie Holographic Remoting zu einer Desktop-oder UWP-app hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="c1bfe-115">Holographic Remoting ermöglicht Ihrer APP das Ziel eines hololens mit Holographic-Inhalten, die auf einem Desktop-PC oder einem UWP-Gerät wie der Xbox One gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-115">Holographic remoting lets your app target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One.</span></span> <span data-ttu-id="c1bfe-116">Sie haben auch Zugriff auf weitere Systemressourcen, sodass Sie die Möglichkeit haben, [in vorhandene](../../design/app-views.md) Desktop-PC-Software zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-116">You also have access to more system resources, making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="c1bfe-117">Eine Remoting-Host-App empfängt einen Eingabedaten Strom von einem hololens, rendert Inhalte in einer virtuellen immersiven Ansicht und streamt Inhalts Frames zurück an hololens.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-117">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="c1bfe-118">Die Verbindung wird mithilfe von Standard-Wi-Fi hergestellt.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-118">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="c1bfe-119">Um Remoting zu verwenden, verwenden Sie ein nuget-Paket, um der Desktop-oder UWP-App Holographic Remoting hinzuzufügen, und schreiben Sie dann Code, um die Verbindung zu verarbeiten und eine immersive Ansicht zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-119">To use remoting, use a NuGet package to add holographic remoting to your desktop or UWP app, then write code to handle the connection and render an immersive view.</span></span> <span data-ttu-id="c1bfe-120">Hilfsbibliotheken sind im Codebeispiel enthalten, das die Aufgabe der Verarbeitung der Geräte Verbindung vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-120">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="c1bfe-121">Eine typische remotingverbindung verfügt über bis zu 50 ms Latenzzeit.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-121">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="c1bfe-122">Die Player-App kann die Latenzzeit in Echtzeit melden.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-122">The player app can report the latency in real time.</span></span>

>[!NOTE]
><span data-ttu-id="c1bfe-123">Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C + +17-kompatiblen C++/WinRT, wie Sie in der [C++ Holographic-Projektvorlage](../native/creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-123">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="c1bfe-124">Die Konzepte sind äquivalent zu einem C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-124">The concepts are equivalent for a C++/WinRT project, though you'll need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="c1bfe-125">Remoting-nuget-Pakete</span><span class="sxs-lookup"><span data-stu-id="c1bfe-125">Get the remoting NuGet packages</span></span>

<span data-ttu-id="c1bfe-126">Führen Sie die folgenden Schritte aus, um das nuget-Paket für Holographic Remoting zu erhalten und einen Verweis aus dem Projekt hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="c1bfe-126">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="c1bfe-127">Wechseln Sie zu Ihrem Projekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-127">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="c1bfe-128">Klicken Sie mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **nuget-Pakete verwalten aus.**</span><span class="sxs-lookup"><span data-stu-id="c1bfe-128">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="c1bfe-129">Wählen Sie im angezeigten Panel die Option **Durchsuchen** aus, und suchen Sie dann nach "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="c1bfe-129">In the panel that appears, selecct **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="c1bfe-130">Wählen Sie " **Microsoft. Holographic. Remoting** " und "selecct **install**" aus.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-130">Select **Microsoft.Holographic.Remoting** and selecct **Install**.</span></span>
5. <span data-ttu-id="c1bfe-131">Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="c1bfe-132">Wählen Sie **Ich akzeptiere** aus, wenn das Dialogfeld Lizenzvertrag angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-132">Select **I Accept** when the license agreement dialog appears.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="c1bfe-133">Erstellen der holographicstreamerhilfsprogramme</span><span class="sxs-lookup"><span data-stu-id="c1bfe-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="c1bfe-134">Zunächst müssen Sie der Klasse, die Remoting verarbeiten soll, eine Instanz von holographicstreamerhilfsprogramme hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-134">First, we need to add an instance of HolographicStreamerHelpers to the class that will handle remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="c1bfe-135">Außerdem müssen Sie den Verbindungsstatus nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-135">You'll also need to track connection state.</span></span> <span data-ttu-id="c1bfe-136">Wenn Sie die Vorschau darstellen möchten, benötigen Sie eine Textur, in die Sie kopiert werden können.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-136">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="c1bfe-137">Außerdem benötigen Sie einige Dinge, wie z. b. eine Verbindungs Zustands Sperre, eine Möglichkeit, die IP-Adresse von hololens zu speichern, usw.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-137">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="c1bfe-138">Initialisieren von holographicstreamerhilfsprogramme und verbinden mit hololens</span><span class="sxs-lookup"><span data-stu-id="c1bfe-138">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="c1bfe-139">Zum Herstellen einer Verbindung mit einem hololens-Gerät erstellen Sie eine Instanz von holographicstreamerhilfsprogramme, und stellen Sie eine Verbindung mit der Ziel-IP-Adresse her</span><span class="sxs-lookup"><span data-stu-id="c1bfe-139">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="c1bfe-140">Sie müssen die Video Frame Größe so festlegen, dass Sie mit der hololens-Anzeigebreite und-Höhe übereinstimmt, da die Holographic Remoting-Bibliothek erwartet, dass die Encoder-und decoderauflösungen genau übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-140">You'll need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

<span data-ttu-id="c1bfe-141">Die Geräte Verbindung ist asynchron.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-141">The device connection is asynchronous.</span></span> <span data-ttu-id="c1bfe-142">Ihre APP muss Ereignishandler für Connect-, Disconnect-und Frame Send-Ereignisse bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-142">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="c1bfe-143">Das onconnected-Ereignis kann die Benutzeroberfläche aktualisieren, das Rendering starten usw.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-143">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="c1bfe-144">In unserem Desktop Codebeispiel aktualisieren wir den Fenstertitel mit der Meldung "Connected" (verbunden).</span><span class="sxs-lookup"><span data-stu-id="c1bfe-144">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="c1bfe-145">Das ongetrennte-Ereignis kann die erneute Verbindung, Aktualisierungen der Benutzeroberfläche usw. verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-145">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="c1bfe-146">In diesem Beispiel wird die Verbindung wieder hergestellt, wenn ein vorübergehender Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-146">In this example, we reconnect if there's a transient failure.</span></span>

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

<span data-ttu-id="c1bfe-147">Wenn die Remoting-Komponente bereit ist, einen Frame zu senden, bietet Ihre APP die Möglichkeit, eine Kopie davon im sendframeevent zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-147">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="c1bfe-148">Hier kopieren wir den Frame in eine Austausch Kette, damit wir ihn in einem Vorschaufenster anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-148">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a><span data-ttu-id="c1bfe-149">Holographic-Inhalt Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="c1bfe-149">Render holographic content</span></span>

<span data-ttu-id="c1bfe-150">Zum Rendering von Inhalten mithilfe von Remoting richten Sie eine virtuelle iframeworkview innerhalb Ihrer Desktop-oder UWP-App ein und verarbeiten holografische Frames aus Remoting.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-150">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="c1bfe-151">Alle Windows Holographic-APIs werden in dieser Ansicht auf die gleiche Weise verwendet, Sie werden aber etwas anders eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-151">All of the Windows Holographic APIs are used the same way by this view, but it's set up slightly differently.</span></span>

<span data-ttu-id="c1bfe-152">Anstatt Sie selbst zu erstellen, stammen die Holographic Space-und Speech-Komponenten von ihrer holographikremumughelpers-Klasse:</span><span class="sxs-lookup"><span data-stu-id="c1bfe-152">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="c1bfe-153">Anstatt eine Update Schleife in einer Run-Methode zu verwenden, stellen Sie Tick-Updates aus der Hauptschleife ihrer Desktop-oder UWP-App bereit.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-153">Instead of using an update loop in a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="c1bfe-154">Dies ermöglicht es Ihrer Desktop-oder UWP-APP, die Kontrolle über die Nachrichtenverarbeitung zu behalten.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-154">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="c1bfe-155">Die Tick ()-Methode der Holographic-App-Ansicht schließt eine Iterationen der Update-, Draw-, Present-Schleife ab.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-155">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

<span data-ttu-id="c1bfe-156">Die Holographic App View Update-, Rendering-und Present-Schleife sind identisch mit der Ausführung auf hololens, mit der Ausnahme, dass Sie Zugriff auf eine viel größere Menge an Systemressourcen auf Ihrem Desktop-PC haben.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-156">The holographic app view update, render, and present loop are exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="c1bfe-157">Sie können viele weitere Dreiecke darstellen, mehr Zeichnungs Pässe haben, mehr Physik durchführen und x64-Prozesse zum Laden von Inhalten verwenden, die mehr als 2 GB RAM erfordern.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-157">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="c1bfe-158">Trennen und Beenden der Remote Sitzung</span><span class="sxs-lookup"><span data-stu-id="c1bfe-158">Disconnect and end the remote session</span></span>

<span data-ttu-id="c1bfe-159">So trennen Sie die Verbindung, z. b. wenn der Benutzer auf eine UI-Schaltfläche klickt, um die Verbindung zu trennen (), für die holographicstreamerhilfsprogramme.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-159">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a><span data-ttu-id="c1bfe-160">Remoting Player</span><span class="sxs-lookup"><span data-stu-id="c1bfe-160">Get the remoting player</span></span>

<span data-ttu-id="c1bfe-161">Der Windows Holographic Remoting Player wird im Windows App Store als Endpunkt für Remoting-Host-apps angeboten, mit denen eine Verbindung hergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-161">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="c1bfe-162">Um den Windows Holographic Remoting Player zu erhalten, besuchen Sie den Windows App Store aus ihren hololens, suchen Sie nach Remoting, und laden Sie die APP herunter.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-162">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="c1bfe-163">Der Remoting Player enthält ein Feature zum Anzeigen von Statistiken auf dem Bildschirm, was beim Debuggen von Remoting-Host-apps hilfreich sein kann.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-163">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="c1bfe-164">Hinweise und Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c1bfe-164">Notes and resources</span></span>

<span data-ttu-id="c1bfe-165">In der Ansicht der Holographic-app muss die APP über das Direct3D-Gerät bereitgestellt werden, das zum Initialisieren des Holographic-Raums verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-165">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="c1bfe-166">Ihre APP sollte dieses Direct3D-Gerät verwenden, um den Vorschau Rahmen zu kopieren und anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-166">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="c1bfe-167">**Code Beispiel:** Ein vollständiges [Holographic Remoting-Codebeispiel](https://github.com/Microsoft/HoloLensCompanionKit) ist verfügbar, das eine Holographic-Anwendungs Ansicht enthält, die mit Remoting-und Remoting-Host Projekten für Desktop Win32, UWP DirectX und UWP mit XAML kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-167">**Code sample:** A complete [Holographic Remoting code sample](https://github.com/Microsoft/HoloLensCompanionKit) is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> 

<span data-ttu-id="c1bfe-168">**Debughinweis:** Die Holographic Remoting-Bibliothek kann Ausnahmen der ersten Chance auslösen.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-168">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="c1bfe-169">Diese Ausnahmen sind möglicherweise in Debugsitzungen sichtbar, abhängig von den Visual Studio-Ausnahme Einstellungen, die zu diesem Zeitpunkt aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-169">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="c1bfe-170">Diese Ausnahmen werden intern von der Holographic Remoting-Bibliothek abgefangen und können ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="c1bfe-170">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
