---
title: Schreiben einer Holographic Remoting-Remote-app (openxr)
description: Durch das Erstellen einer Holographic Remoting Remote-app, die auf einem Remote Computer gerendert wird, kann auf hololens 2 gestreamt werden. In diesem Artikel wird beschrieben, wie dies erreicht werden kann.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, nuget
ms.openlocfilehash: 7e46c67e7dac08759890fa66d540379991414aad
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469503"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a><span data-ttu-id="0abe1-105">Schreiben einer Holographic Remoting-Remote-App mithilfe der openxr-API</span><span class="sxs-lookup"><span data-stu-id="0abe1-105">Writing a Holographic Remoting remote app using the OpenXR API</span></span>

>[!IMPORTANT]
><span data-ttu-id="0abe1-106">In diesem Dokument wird die Erstellung einer Remote Anwendung für hololens 2-und Windows Mixed Reality-Headsets mithilfe der [openxr-API](../native/openxr.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0abe1-106">This document describes the creation of a remote application for HoloLens 2 and Windows Mixed Reality headsets using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="0abe1-107">Für Remote Anwendungen für **hololens (1st Gen)** muss das nuget-Paketversion **1. x. x** verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0abe1-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="0abe1-108">Dies bedeutet, dass für hololens 2 geschriebene Remote Anwendungen nicht mit hololens 1 und umgekehrt kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="0abe1-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="0abe1-109">Die Dokumentation für hololens 1 finden Sie [hier](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="0abe1-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="0abe1-110">Wenn Sie eine Holographic Remoting-Remote-app erstellen, können Remote Inhalte, die auf einem Remote Computer gerendert werden, an hololens 2 und immersive Geräte wie Windows Mixed Reality-Headsets gestreamt werden.</span><span class="sxs-lookup"><span data-stu-id="0abe1-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2 and immersive devices like Windows Mixed Reality headsets.</span></span> <span data-ttu-id="0abe1-111">In diesem Artikel wird beschrieben, wie dies erreicht werden kann.</span><span class="sxs-lookup"><span data-stu-id="0abe1-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="0abe1-112">Sämtlicher Code auf dieser Seite und in den Arbeitsprojekten finden Sie im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)".</span><span class="sxs-lookup"><span data-stu-id="0abe1-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="0abe1-113">Holographic Remoting ermöglicht einer APP das Ausrichten von hololens 2-und Windows Mixed Reality-Headsets mit Holographic-Inhalten, die auf einem Desktop-PC oder auf einem UWP-Gerät wie der Xbox One gerendert werden, und ermöglicht so den Zugriff auf mehr Systemressourcen und ermöglicht die Integration von Remote- [immersiven Ansichten](../../design/app-views.md) in vorhandene Desktop-PCs.</span><span class="sxs-lookup"><span data-stu-id="0abe1-113">Holographic remoting allows an app to target HoloLens 2 and Windows Mixed Reality headsets with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="0abe1-114">Eine Remote-app empfängt einen Eingabedaten Strom von hololens 2, rendert Inhalte in einer virtuellen immersiven Ansicht und streamt Inhalts Frames zurück an hololens 2.</span><span class="sxs-lookup"><span data-stu-id="0abe1-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="0abe1-115">Die Verbindung wird mithilfe von Standard-Wi-Fi hergestellt.</span><span class="sxs-lookup"><span data-stu-id="0abe1-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="0abe1-116">Holographic-Remoting wird mithilfe eines nuget-Pakets zu einer Desktop-oder UWP-app hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0abe1-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="0abe1-117">Zusätzlicher Code ist erforderlich, der die Verbindung verarbeitet und in einer immersiven Ansicht rendert.</span><span class="sxs-lookup"><span data-stu-id="0abe1-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="0abe1-118">Eine typische remotingverbindung verfügt über bis zu 50 ms Latenzzeit.</span><span class="sxs-lookup"><span data-stu-id="0abe1-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="0abe1-119">Die Player-App kann die Latenzzeit in Echtzeit melden.</span><span class="sxs-lookup"><span data-stu-id="0abe1-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0abe1-120">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0abe1-120">Prerequisites</span></span>

<span data-ttu-id="0abe1-121">Ein guter Ausgangspunkt ist eine funktionierende openxr-basierte Desktop-oder UWP-app.</span><span class="sxs-lookup"><span data-stu-id="0abe1-121">A good starting point is a working OpenXR based Desktop or UWP app.</span></span> <span data-ttu-id="0abe1-122">Weitere Informationen finden Sie [unter Getting Started with openxr](../native/openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="0abe1-122">For details see [Getting started with OpenXR](../native/openxr-getting-started.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="0abe1-123">Jede APP, die Holographic Remoting verwendet, sollte für die Verwendung eines [Multithread-Apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="0abe1-123">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="0abe1-124">Die Verwendung eines [Single Thread-Apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) wird unterstützt, führt jedoch zu einer nicht optimalen Leistung und kann während der Wiedergabe möglicherweise zu einem stutor werden.</span><span class="sxs-lookup"><span data-stu-id="0abe1-124">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="0abe1-125">Bei Verwendung von C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) ist ein Multithread-Apartment der Standard.</span><span class="sxs-lookup"><span data-stu-id="0abe1-125">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="0abe1-126">Holen Sie sich das Holographic Remoting-nuget-Paket.</span><span class="sxs-lookup"><span data-stu-id="0abe1-126">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="0abe1-127">Die folgenden Schritte sind erforderlich, um das nuget-Paket einem Projekt in Visual Studio hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0abe1-127">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="0abe1-128">Öffnen Sie das Projekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0abe1-128">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="0abe1-129">Klicken Sie mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **nuget-Pakete verwalten aus.**</span><span class="sxs-lookup"><span data-stu-id="0abe1-129">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="0abe1-130">Klicken Sie im angezeigten Bereich auf **Durchsuchen** , und suchen Sie nach "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="0abe1-130">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="0abe1-131">Wählen Sie **Microsoft. Holographic. Remoting. openxr** aus, stellen Sie sicher, dass die neueste Version **2. x. x** ausgewählt ist, und klicken Sie auf **Installieren**.</span><span class="sxs-lookup"><span data-stu-id="0abe1-131">Select **Microsoft.Holographic.Remoting.OpenXr**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="0abe1-132">Wenn das Dialogfeld **Vorschau** angezeigt wird, klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="0abe1-132">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="0abe1-133">Das nächste Dialogfeld, das angezeigt wird, ist die Lizenzvereinbarung.</span><span class="sxs-lookup"><span data-stu-id="0abe1-133">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="0abe1-134">Klicken Sie auf **ich** Stimme zu, um den Lizenzvertrag zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="0abe1-134">Click on **I Accept** to accept the license agreement.</span></span>
7. <span data-ttu-id="0abe1-135">Wiederholen Sie die Schritte 3 bis 6 für die folgenden nuget-Pakete: openxr. Headers, openxr. Loader</span><span class="sxs-lookup"><span data-stu-id="0abe1-135">Repeat the steps 3 to 6 for the following NuGet Packages: OpenXR.Headers, OpenXR.Loader</span></span>

>[!NOTE]
><span data-ttu-id="0abe1-136">Version **1. x. x** des nuget-Pakets ist weiterhin für Entwickler verfügbar, die auf hololens 1 abzielen möchten.</span><span class="sxs-lookup"><span data-stu-id="0abe1-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="0abe1-137">Weitere Informationen finden [Sie unter Hinzufügen von Holographic Remoting (hololens (1st Gen))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="0abe1-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="select-the-holographic-remoting-openxr-runtime"></a><span data-ttu-id="0abe1-138">Wählen Sie das Holographic-Remoting openxr Runtime aus.</span><span class="sxs-lookup"><span data-stu-id="0abe1-138">Select the Holographic Remoting OpenXR runtime</span></span>

<span data-ttu-id="0abe1-139">Der erste Schritt, den Sie in Ihrer Remote-app ausführen müssen, ist die Auswahl der Holographic-Remoting-openxr-Laufzeit, die Teil des nuget-Pakets Microsoft. Holographic. Remoting. openxr ist.</span><span class="sxs-lookup"><span data-stu-id="0abe1-139">The first step you need to do in your remote app is to select the Holographic Remoting OpenXR runtime which is part of the Microsoft.Holographic.Remoting.OpenXr NuGet package.</span></span> <span data-ttu-id="0abe1-140">Hierfür können Sie die ```XR_RUNTIME_JSON``` Umgebungsvariable auf den Pfad der RemotingXR.jsDatei in der APP festlegen.</span><span class="sxs-lookup"><span data-stu-id="0abe1-140">You can do this by setting the ```XR_RUNTIME_JSON``` environment variable to the path of the RemotingXR.json file within your app.</span></span> <span data-ttu-id="0abe1-141">Diese Umgebungsvariable wird vom openxr-Loader verwendet, um die System Standard-openxr-Laufzeit nicht zu verwenden, sondern zur "Holographic Remoting openxr Runtime" umzuleiten.</span><span class="sxs-lookup"><span data-stu-id="0abe1-141">This environment variable is used by the OpenXR loader to not use the system default OpenXR runtime but instead redirect to the Holographic Remoting OpenXR runtime.</span></span> <span data-ttu-id="0abe1-142">Wenn Sie das nuget-Paket Microsoft. Holographic. Remoting. openxr verwenden, wird der RemotingXR.jsfür die Datei während der Kompilierung automatisch in den Ausgabeordner kopiert. Daher sieht die openxr-Lauf Zeitauswahl in der Regel wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="0abe1-142">When using the Microsoft.Holographic.Remoting.OpenXr NuGet package the RemotingXR.json file is automatically copied during compilation to the output folder, thus the OpenXR runtime selection typically looks as follows.</span></span>

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a><span data-ttu-id="0abe1-143">Erstellen einer xrinstance mit Holographic Remoting-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="0abe1-143">Create XrInstance with Holographic Remoting Extension</span></span>

<span data-ttu-id="0abe1-144">Der erste Schritt, den eine typische openxr-app ausführen soll, besteht darin, openxr-Erweiterungen auszuwählen und eine xrinstance-Instanz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0abe1-144">The first step a typical OpenXR app is supposed to do is to select OpenXR extensions and create a XrInstance.</span></span> <span data-ttu-id="0abe1-145">Die openxr Core-Spezifikation bietet keine Remoting-spezifische API.</span><span class="sxs-lookup"><span data-stu-id="0abe1-145">The OpenXR core specification does not provide any remoting specific API.</span></span> <span data-ttu-id="0abe1-146">Aus diesem Grund führt Holographic Remoting die eigene openxr-Erweiterung namens ein ```XR_MSFT_holographic_remoting``` .</span><span class="sxs-lookup"><span data-stu-id="0abe1-146">For that reason Holographic Remoting introduces it's own OpenXR extension named ```XR_MSFT_holographic_remoting```.</span></span> <span data-ttu-id="0abe1-147">Stellen Sie sicher, dass beim Aufrufen von xrkreateinstance der ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` in xrinstancecreateinfo enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="0abe1-147">Ensure that when you call xrCreateInstance the ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` is included in the XrInstanceCreateInfo.</span></span>

>[!TIP]
><span data-ttu-id="0abe1-148">Standardmäßig wird der gerenderte Inhalt Ihrer app nur an den Holographic Remoting-Player gestreamt, der entweder auf einem hololens 2 oder auf einem Windows Mixed Reality-Headsets ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0abe1-148">By default the rendered content of your app is only streamed to the Holographic Remoting player either running on a HoloLens 2 or on a Windows Mixed Reality headsets.</span></span> <span data-ttu-id="0abe1-149">Um den gerenderten Inhalt auf dem Remote-PC auch über eine SwapChain eines Fensters anzuzeigen, bietet Holographic Remoting eine zweite openxr-Erweiterung mit dem Namen ```XR_MSFT_holographic_remoting_frame_mirroring``` .</span><span class="sxs-lookup"><span data-stu-id="0abe1-149">To also display the rendered content on the remote PC, via a swap-chain of a window for instance, Holographic Remoting provides a second OpenXR extension named ```XR_MSFT_holographic_remoting_frame_mirroring```.</span></span> <span data-ttu-id="0abe1-150">Stellen Sie sicher, dass diese Extension auch mit aktivieren, ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` Falls Sie diese Funktion verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="0abe1-150">Ensure to also enable this extension using ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in case you want to use that functionality.</span></span>

>[!IMPORTANT]
><span data-ttu-id="0abe1-151">Weitere Informationen zur API für die Holographic Remoting openxr-Erweiterung finden Sie in der [Spezifikation](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) , die im [GitHub-Repository "Holographic Remoting Samples](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" zu finden ist.</span><span class="sxs-lookup"><span data-stu-id="0abe1-151">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="connect-to-the-device"></a><span data-ttu-id="0abe1-152">Verbindung mit dem Gerät herstellen</span><span class="sxs-lookup"><span data-stu-id="0abe1-152">Connect to the device</span></span>

<span data-ttu-id="0abe1-153">Nachdem Ihre Remote-app die xrinstance erstellt und die xrsystemid über xrgetsystem abgefragt hat, kann eine Verbindung mit dem Player Gerät hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="0abe1-153">After your remote app has created the XrInstance and queried the XrSystemId via xrGetSystem a connection to the player device can be established.</span></span>

>[!WARNING]
> <span data-ttu-id="0abe1-154">Das Holographic-Remoting openxr Runtime kann nur gerätespezifische Daten bereitstellen, z. b. Ansichts Konfigurationen oder Umgebungs Blend-Modi, nachdem eine Verbindung hergestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="0abe1-154">The Holographic Remoting OpenXR runtime is only able to provide device specific data such as view configurations or environment blend modes after a connection has been established.</span></span> <span data-ttu-id="0abe1-155">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` und verfügen ```xrGetSystemProperties``` über Standardwerte, die Sie in der Regel erhalten, wenn Sie eine Verbindung mit einem Player herstellen, der auf einem hololens 2 ausgeführt wird, bevor eine vollständige Verbindung hergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="0abe1-155">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews```, ```xrGetViewConfigurationProperties```, ```xrEnumerateEnvironmentBlendModes```, and ```xrGetSystemProperties``` will give you default values, matching what you would typically get if you connect to a player running on a HoloLens 2, before being fully connected.</span></span>
<span data-ttu-id="0abe1-156">Es wird dringend empfohlen, diese Methoden nicht aufzurufen, bevor eine Verbindung hergestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="0abe1-156">It is strongly recommended to not call these methods before a connection has been established.</span></span> <span data-ttu-id="0abe1-157">Der Vorschlag ist die Verwendung dieser Methoden, nachdem die xrsession erfolgreich erstellt wurde und der Sitzungszustand mindestens XR_SESSION_STATE_READY ist.</span><span class="sxs-lookup"><span data-stu-id="0abe1-157">The suggestion is use these methods after the XrSession has been successfully created and the session state is at least XR_SESSION_STATE_READY.</span></span>

<span data-ttu-id="0abe1-158">Allgemeine Eigenschaften wie z. b. Max. Bitrate, audiofähig, Videocodec oder tiefe Puffer Datenstrom Auflösung können ```xrRemotingSetContextPropertiesMSFT``` wie folgt konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="0abe1-158">General properties such as max bitrate, audio enabled, video codec, or depth buffer stream resolution can be configured via ```xrRemotingSetContextPropertiesMSFT``` as follows.</span></span>

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

<span data-ttu-id="0abe1-159">Die Verbindung kann auf zwei Arten erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="0abe1-159">The connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="0abe1-160">Die Remote-app stellt eine Verbindung zum Player her, der auf dem Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0abe1-160">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="0abe1-161">Der Player, der auf dem Gerät ausgeführt wird, stellt eine Verbindung zur Remote-app her</span><span class="sxs-lookup"><span data-stu-id="0abe1-161">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="0abe1-162">Um eine Verbindung zwischen der Remote-app und dem Player-Gerät herzustellen, geben Sie die-Methode an, die ```xrRemotingConnectMSFT``` den Hostnamen und den Port über die  ```XrRemotingConnectInfoMSFT``` Struktur angibt.</span><span class="sxs-lookup"><span data-stu-id="0abe1-162">To establish a connection from the remote app to the player device call the ```xrRemotingConnectMSFT``` method specifying the hostname and port via the  ```XrRemotingConnectInfoMSFT``` structure.</span></span> <span data-ttu-id="0abe1-163">Der von Holographic Remoting Player verwendete Port ist **8265**.</span><span class="sxs-lookup"><span data-stu-id="0abe1-163">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

<span data-ttu-id="0abe1-164">Das Lauschen auf eingehende Verbindungen in der Remote-app kann durch Aufrufen der- ```xrRemotingListenMSFT``` Methode erfolgen.</span><span class="sxs-lookup"><span data-stu-id="0abe1-164">Listening for incoming connections on the remote app can be done by calling the ```xrRemotingListenMSFT``` method.</span></span> <span data-ttu-id="0abe1-165">Der Handshake-und der transportport können über die-Struktur angegeben werden ```XrRemotingListenInfoMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="0abe1-165">Both the handshake port and transport port can be specified via the ```XrRemotingListenInfoMSFT``` structure.</span></span> <span data-ttu-id="0abe1-166">Der Handshake-Port wird für den ersten Handshake verwendet.</span><span class="sxs-lookup"><span data-stu-id="0abe1-166">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="0abe1-167">Die Daten werden dann über den transportport gesendet.</span><span class="sxs-lookup"><span data-stu-id="0abe1-167">The data is then send over the transport port.</span></span> <span data-ttu-id="0abe1-168">Standardmäßig werden **8265** und **8266** verwendet.</span><span class="sxs-lookup"><span data-stu-id="0abe1-168">By default **8265** and **8266** are used.</span></span>

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

<span data-ttu-id="0abe1-169">Der Verbindungsstatus muss getrennt werden, wenn Sie ```xrRemotingConnectMSFT``` oder aufruft ```xrRemotingListenMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="0abe1-169">The connection state must be disconnected when you call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT```.</span></span> <span data-ttu-id="0abe1-170">Der Verbindungsstatus kann jederzeit abgerufen werden, nachdem Sie eine xrinstance erstellt und für die xrsystemid mithilfe von abgefragt haben ```xrRemotingGetConnectionStateMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="0abe1-170">You can get the connection state at any point after you have created a XrInstance and queried for the XrSystemId via ```xrRemotingGetConnectionStateMSFT```.</span></span>

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

<span data-ttu-id="0abe1-171">Folgende Verbindungszustände sind verfügbar:</span><span class="sxs-lookup"><span data-stu-id="0abe1-171">Available connection states are:</span></span>
- <span data-ttu-id="0abe1-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="0abe1-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span></span>
- <span data-ttu-id="0abe1-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span><span class="sxs-lookup"><span data-stu-id="0abe1-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span></span>
- <span data-ttu-id="0abe1-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="0abe1-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span></span>

>[!IMPORTANT]
> <span data-ttu-id="0abe1-175">```xrRemotingConnectMSFT``` oder ```xrRemotingListenMSFT``` muss aufgerufen werden, bevor versucht wird, eine xrsession über xrkreatesession zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0abe1-175">```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` must be called before trying to create a XrSession via xrCreateSession.</span></span> <span data-ttu-id="0abe1-176">Wenn Sie versuchen, eine xrsession-Sitzung zu erstellen, während der Verbindungsstatus ist, ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` wird die Sitzungs Erstellung erfolgreich ausgeführt, aber der Sitzungszustand wird sofort in XR_SESSION_STATE_LOSS_PENDING übergehen.</span><span class="sxs-lookup"><span data-stu-id="0abe1-176">If you try to create a XrSession while the connection state is ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session creation will succeed but the session state will immediately transition to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="0abe1-177">Die Implementierung von Holographic Remoting ```xrCreateSession``` unterstützt das warten auf das Herstellen einer Verbindung.</span><span class="sxs-lookup"><span data-stu-id="0abe1-177">Holographic Remoting's implementation of ```xrCreateSession``` supports waiting for a connection to be established.</span></span> <span data-ttu-id="0abe1-178">Sie können einen-Aufrufvorgang ```xrRemotingConnectMSFT``` oder ```xrRemotingListenMSFT``` direkt gefolgt von einem-Befehl durchlaufen ```xrCreateSession``` , der blockiert und darauf wartet, dass eine Verbindung hergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="0abe1-178">You can call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` immediately followed by a call to ```xrCreateSession``` which will block and wait for a connection to be established.</span></span> <span data-ttu-id="0abe1-179">Das Timeout ist auf 10 Sekunden korrigiert.</span><span class="sxs-lookup"><span data-stu-id="0abe1-179">The timeout is fixed to 10 seconds.</span></span> <span data-ttu-id="0abe1-180">Wenn innerhalb dieses Zeitraums eine Verbindung hergestellt werden kann, wird die xrsession-Erstellung erfolgreich ausgeführt, und der Sitzungs Status wechselt zu XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="0abe1-180">If a connection can be established within this time the XrSession creation will succeed and the session state will transition to XR_SESSION_STATE_READY.</span></span> <span data-ttu-id="0abe1-181">Für den Fall, dass keine Verbindung hergestellt werden kann, ist auch die Sitzungs Erstellung erfolgreich, aber es erfolgt sofort zu XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="0abe1-181">In case no connection can be established the session creation also succeeds but immediately transitions to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="0abe1-182">Im Allgemeinen ist der Verbindungsstatus ein paar mit dem xrsession-Zustand.</span><span class="sxs-lookup"><span data-stu-id="0abe1-182">In general the connection state is couple with the XrSession state.</span></span> <span data-ttu-id="0abe1-183">Jede Änderung des Verbindungsstatus wirkt sich auch auf den Sitzungs Status aus.</span><span class="sxs-lookup"><span data-stu-id="0abe1-183">Any change to the connection state also affects the session state.</span></span> <span data-ttu-id="0abe1-184">Wenn beispielsweise der Verbindungsstatus von `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` in ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` den Sitzungs Status wechselt, wechselt ebenfalls zu XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="0abe1-184">For instance, if the connection state switches from `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` to ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session state will transition to XR_SESSION_STATE_LOSS_PENDING as well.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="0abe1-185">Behandeln von Remoting-spezifischen Ereignissen</span><span class="sxs-lookup"><span data-stu-id="0abe1-185">Handling Remoting specific events</span></span>

<span data-ttu-id="0abe1-186">Das Holographic-Remoting openxr Runtime macht drei Ereignisse verfügbar, die für die Überwachung des Zustands einer Verbindung wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="0abe1-186">The Holographic Remoting OpenXR runtime exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="0abe1-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Wird ausgelöst, wenn eine Verbindung mit dem Gerät erfolgreich hergestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="0abe1-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Triggered when a connection to the device has been successfully established.</span></span>
2) <span data-ttu-id="0abe1-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Wird ausgelöst, wenn eine etablierte Verbindung geschlossen wird oder keine Verbindung hergestellt werden konnte.</span><span class="sxs-lookup"><span data-stu-id="0abe1-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Triggered if an established connection is closed or a connection could not be established.</span></span>
3) <span data-ttu-id="0abe1-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Beim lauschen auf eingehende Verbindungen wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="0abe1-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: When listening for incoming connections starts.</span></span>

<span data-ttu-id="0abe1-190">Diese Ereignisse werden in einer Warteschlange platziert, und Ihre Remote-app muss mit Regularität über die Warteschlange lesen ```xrPollEvent``` .</span><span class="sxs-lookup"><span data-stu-id="0abe1-190">These events are placed in a queue and your remote app must read from the queue with regularity via ```xrPollEvent```.</span></span>

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="0abe1-191">Vorschau der lokal gestreuten Inhalte</span><span class="sxs-lookup"><span data-stu-id="0abe1-191">Preview streamed content locally</span></span>

<span data-ttu-id="0abe1-192">Zum Anzeigen desselben Inhalts in der Remote-app, die an das Gerät gesendet wird, ```XR_MSFT_holographic_remoting_frame_mirroring``` kann die Erweiterung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0abe1-192">To display the same content in the remote app that is send to the device the ```XR_MSFT_holographic_remoting_frame_mirroring``` extension can be used.</span></span> <span data-ttu-id="0abe1-193">Mit dieser Erweiterung können Sie eine Textur an den xrendframe übermitteln.</span><span class="sxs-lookup"><span data-stu-id="0abe1-193">With this extension you can submit a texture to xrEndFrame.</span></span> <span data-ttu-id="0abe1-194">Dies erfolgt mithilfe der- ```XrRemotingFrameMirrorImageInfoMSFT``` Struktur, die wie folgt mit xrframedinfo verkettet ist.</span><span class="sxs-lookup"><span data-stu-id="0abe1-194">This is done by using the ```XrRemotingFrameMirrorImageInfoMSFT``` structure which is chained to the XrFrameEndInfo as follows.</span></span>

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

<span data-ttu-id="0abe1-195">Im obigen Beispiel wird eine DX11-Swap-Chain-Textur verwendet, und das Fenster wird unmittelbar nach dem xrendframe-Rückruf dargestellt.</span><span class="sxs-lookup"><span data-stu-id="0abe1-195">The example above uses a DX11 swap-chain texture and presents the window immediately after the call to xrEndFrame.</span></span> <span data-ttu-id="0abe1-196">Die Verwendung ist nicht auf die Texturen der Austausch Kette beschränkt, und es ist keine zusätzliche GPU-Synchronisierung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0abe1-196">The usage is not restricted to swap-chain textures and no additional GPU synchronization is required.</span></span> <span data-ttu-id="0abe1-197">Ausführliche Informationen zur Verwendung und zu Einschränkungen finden Sie in der [Erweiterungs Spezifikation](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span><span class="sxs-lookup"><span data-stu-id="0abe1-197">For details on usage and constraints check out the [extension specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span></span>
<span data-ttu-id="0abe1-198">Wenn Ihre Remote-app DX12 verwendet, verwenden Sie XrRemotingFrameMirrorImageD3D12MSFT anstelle von XrRemotingFrameMirrorImageD3D11MSFT.</span><span class="sxs-lookup"><span data-stu-id="0abe1-198">If your remote app is using DX12 use XrRemotingFrameMirrorImageD3D12MSFT instead of XrRemotingFrameMirrorImageD3D11MSFT.</span></span>

## <a name="see-also"></a><span data-ttu-id="0abe1-199">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0abe1-199">See Also</span></span>
* [<span data-ttu-id="0abe1-200">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="0abe1-200">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="0abe1-201">Einrichten einer sicheren Verbindung mit Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="0abe1-201">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="0abe1-202">Problembehandlung und Einschränkungen für Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="0abe1-202">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="0abe1-203">Holographic Remoting-Software – Lizenzbedingungen</span><span class="sxs-lookup"><span data-stu-id="0abe1-203">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="0abe1-204">Datenschutzerklärung von Microsoft</span><span class="sxs-lookup"><span data-stu-id="0abe1-204">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
