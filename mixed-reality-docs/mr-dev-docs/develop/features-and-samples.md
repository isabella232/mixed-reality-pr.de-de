---
title: Beispiele und Feature-Apps
description: Bleiben Sie bei allen verfügbaren Microsoft-Beispielen und Mixed Reality-Feature-Apps für HoloLens auf dem neuesten Stand.
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Lernen, Beispiele, MRTK, Forschungsmodus, HoloLens 2, QR-Codes, WebRTC, Mixed Reality-Aufnahme, Holographic Remoting, UX-Tools
ms.localizationpriority: high
ms.openlocfilehash: 78a9e343fde4a6cbc23268f0be353577498d67b6
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906896"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="ab57d-104">Beispiele und Feature-Apps</span><span class="sxs-lookup"><span data-stu-id="ab57d-104">Samples and feature apps</span></span>

![Abbildung eines Benutzers, der eine HoloLens trägt und ein Hologramm mit Handbewegungen manipuliert.](unreal/images/unreal-developer.jpg)

<span data-ttu-id="ab57d-106">Jede Entwicklungs-Journey beginnt mit einem Blick zurück auf das, was andere Entwickler erfolgreich aufgebaut haben – Mixed Reality macht da keinen Unterschied.</span><span class="sxs-lookup"><span data-stu-id="ab57d-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="ab57d-107">Aktuell sind alle unsere Tutorials und Beispiel-Apps in Unity oder Unreal entwickelt.</span><span class="sxs-lookup"><span data-stu-id="ab57d-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="ab57d-108">Wenn wir Inhalte für andere Engines und Plattformen entwickeln, finden Sie diese unter der entsprechenden Überschrift im Inhaltsverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="ab57d-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="ab57d-109">Beispiel-Apps</span><span class="sxs-lookup"><span data-stu-id="ab57d-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="ab57d-110">Featurebeispiele</span><span class="sxs-lookup"><span data-stu-id="ab57d-110">Feature samples</span></span>

<span data-ttu-id="ab57d-111">Die unten aufgeführten Featurebeispiele entsprechen bestimmten Implementierungen, die in unserer Dokumentation behandelt werden, und decken eine Reihe von Entwicklungsplattformen und Hardwaregeräten ab.</span><span class="sxs-lookup"><span data-stu-id="ab57d-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="openxr"></a><span data-ttu-id="ab57d-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ab57d-112">OpenXR</span></span>

<span data-ttu-id="ab57d-113">Entwickler, die für Unity 2020 entwickeln, um HoloLens 2- oder Mixed Reality-Anwendungen zu erstellen, können das OpenXR-Plug-In anstelle des WindowsXR-Plug-Ins verwenden, um eine bessere plattformübergreifende Kompatibilität zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="ab57d-113">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span> <span data-ttu-id="ab57d-114">Das Mixed Reality OpenXR-Plug-In funktioniert auch gut mit dem neuesten Mixed Reality Toolkit 2.7.</span><span class="sxs-lookup"><span data-stu-id="ab57d-114">The Mixed Reality OpenXR Plugin also works well with latest Mixed Reality Toolkit 2.7.</span></span>

<br>

| <span data-ttu-id="ab57d-115">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="ab57d-115">Reference article</span></span> | <span data-ttu-id="ab57d-116">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ab57d-116">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="ab57d-117">Verwenden des OpenXR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="ab57d-117">Using the OpenXR plugin</span></span>](./unity/xr-project-setup.md) | [<span data-ttu-id="ab57d-118">Mixed Reality OpenXR mit Unity-Beispielen</span><span class="sxs-lookup"><span data-stu-id="ab57d-118">Mixed Reality OpenXR with Unity samples</span></span>](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| <span data-ttu-id="ab57d-119">–</span><span class="sxs-lookup"><span data-stu-id="ab57d-119">N/A</span></span> | [<span data-ttu-id="ab57d-120">OpenXR MRTK-Basisprojekt für Unity</span><span class="sxs-lookup"><span data-stu-id="ab57d-120">OpenXR MRTK Base Unity project</span></span>](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a><span data-ttu-id="ab57d-121">Forschungsmodus</span><span class="sxs-lookup"><span data-stu-id="ab57d-121">Research Mode</span></span>

<span data-ttu-id="ab57d-122">Der Forschungsmodus wurde in der HoloLens der 1. Generation eingeführt, um Zugriff auf wesentliche Sensoren des Geräts zu gewähren, insbesondere für Forschungsanwendungen, die nicht für die Bereitstellung vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="ab57d-122">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="ab57d-123">Die folgenden Beispielanwendungen sind Beispiele für den Zugriff auf und die Aufzeichnung von Forschungsmodus-Datenströmen und die Verwendung der [intrinsischen und extrinsischen Funktionen](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="ab57d-123">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="ab57d-124">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="ab57d-124">Reference article</span></span> | <span data-ttu-id="ab57d-125">Beispielanwendung</span><span class="sxs-lookup"><span data-stu-id="ab57d-125">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="ab57d-126">Forschungsmodus</span><span class="sxs-lookup"><span data-stu-id="ab57d-126">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="ab57d-127">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="ab57d-127">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="ab57d-128">Forschungsmodus</span><span class="sxs-lookup"><span data-stu-id="ab57d-128">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="ab57d-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ab57d-129">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="ab57d-130">QR-Codes</span><span class="sxs-lookup"><span data-stu-id="ab57d-130">QR codes</span></span>

<span data-ttu-id="ab57d-131">HoloLens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der Position jedes Codes in der realen Welt einrichten.</span><span class="sxs-lookup"><span data-stu-id="ab57d-131">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="ab57d-132">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="ab57d-132">Reference article</span></span> | <span data-ttu-id="ab57d-133">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ab57d-133">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="ab57d-134">QR-Codes</span><span class="sxs-lookup"><span data-stu-id="ab57d-134">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="ab57d-135">Nachverfolgen von QR-Codes in Unity</span><span class="sxs-lookup"><span data-stu-id="ab57d-135">QR code tracking in Unity</span></span>](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a><span data-ttu-id="ab57d-136">Grundlegendes zu Szenen</span><span class="sxs-lookup"><span data-stu-id="ab57d-136">Scene understanding</span></span>

<span data-ttu-id="ab57d-137">Szenenverständnis bietet Mixed Reality-Entwicklern eine strukturierte, allgemeine Umgebungsdarstellung, die die Entwicklung für umgebungssensible Anwendungen intuitiv macht.</span><span class="sxs-lookup"><span data-stu-id="ab57d-137">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="ab57d-138">Das Szenenverständnis erreicht dies durch die Kombination der Leistung vorhandener Mixed Reality-Runtimes wie der hochgenauen, aber weniger strukturierten räumlichen Abbildung mit neuen KI-gesteuerten Runtimes.</span><span class="sxs-lookup"><span data-stu-id="ab57d-138">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured spatial mapping and new AI driven runtimes.</span></span>

<br>

| <span data-ttu-id="ab57d-139">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="ab57d-139">Reference article</span></span> | <span data-ttu-id="ab57d-140">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ab57d-140">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="ab57d-141">Grundlegendes zu Szenen</span><span class="sxs-lookup"><span data-stu-id="ab57d-141">Scene understanding</span></span>](../design/scene-understanding.md) | [<span data-ttu-id="ab57d-142">Beispiele für Mixed Reality-Szenenverständnis</span><span class="sxs-lookup"><span data-stu-id="ab57d-142">Mixed Reality Scene Understanding samples</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a><span data-ttu-id="ab57d-143">WebRTC</span><span class="sxs-lookup"><span data-stu-id="ab57d-143">WebRTC</span></span>

<span data-ttu-id="ab57d-144">Das MixedReality-WebRTC-Projekt ist eine Sammlung von Komponenten, die Entwicklern von Mixed Reality-Apps bei der Integration von Peer-to-Peer-Audio, -Video und Daten-Echtzeitkommunikation in Ihre Anwendungen helfen soll. WebRTC-Komponenten basieren auf dem WebRTC-Protokoll für Echtzeitkommunikation (RTC), das von den meisten modernen Webbrowsern unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="ab57d-144">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="ab57d-145">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="ab57d-145">Reference article</span></span> | <span data-ttu-id="ab57d-146">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ab57d-146">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="ab57d-147">WebRTC</span><span class="sxs-lookup"><span data-stu-id="ab57d-147">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="ab57d-148">WebRTC-Beispiel-Apps</span><span class="sxs-lookup"><span data-stu-id="ab57d-148">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="ab57d-149">Holographische Mixed Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="ab57d-149">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="ab57d-150">Mit Mixed Reality-Aufnahme (MRC) wird die „Erste Person“-Erfahrung (Ego-Perspektive) der Vermischung realer mit digitalen Welten als Foto oder Video aufgenommen, wobei Sie das Gesehene mit anderen in Echtzeit teilen können.</span><span class="sxs-lookup"><span data-stu-id="ab57d-150">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="ab57d-151">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="ab57d-151">Reference article</span></span> | <span data-ttu-id="ab57d-152">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ab57d-152">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="ab57d-153">Mixed Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="ab57d-153">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="ab57d-154">Beispiele für Mixed Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="ab57d-154">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="ab57d-155">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="ab57d-155">Holographic Remoting</span></span>

<span data-ttu-id="ab57d-156">Der Holographic Remoting-Player ist eine Begleit-App, die sich mit PC-Apps und -Spielen verbindet, die Holographic Remoting unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ab57d-156">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="ab57d-157">Holographic Remoting streamt holographische Inhalte in Echtzeit über eine WLAN-Verbindung von einem PC an Ihre Microsoft HoloLens. Es wird von HoloLens (1. Generation) und HoloLens 2 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ab57d-157">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="ab57d-158">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="ab57d-158">Reference article</span></span> | <span data-ttu-id="ab57d-159">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ab57d-159">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="ab57d-160">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="ab57d-160">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="ab57d-161">Holographic Remoting-Beispiele</span><span class="sxs-lookup"><span data-stu-id="ab57d-161">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |