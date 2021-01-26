---
title: Beispiele und Feature-Apps
description: Bleiben Sie bei allen verfügbaren Microsoft-Beispielen und Mixed Reality-Feature-Apps für HoloLens auf dem neuesten Stand.
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Lernen, Beispiele, MRTK, Forschungsmodus, HoloLens 2, QR-Codes, WebRTC, Mixed Reality-Aufnahme, Holographic Remoting, UX-Tools
ms.localizationpriority: high
ms.openlocfilehash: 78cfc726bdffdb461a83bd1e9805d8f0e64b0f01
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583197"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="f6375-104">Beispiele und Feature-Apps</span><span class="sxs-lookup"><span data-stu-id="f6375-104">Samples and feature apps</span></span>

![Abbildung eines Benutzers, der eine HoloLens trägt und ein Hologramm mit Handbewegungen manipuliert.](unreal/images/unreal-developer.jpg)

<span data-ttu-id="f6375-106">Jede Entwicklungs-Journey beginnt mit einem Blick zurück auf das, was andere Entwickler erfolgreich aufgebaut haben – Mixed Reality macht da keinen Unterschied.</span><span class="sxs-lookup"><span data-stu-id="f6375-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="f6375-107">Aktuell sind alle unsere Tutorials und Beispiel-Apps in Unity oder Unreal entwickelt.</span><span class="sxs-lookup"><span data-stu-id="f6375-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="f6375-108">Wenn wir Inhalte für andere Engines und Plattformen entwickeln, finden Sie diese unter der entsprechenden Überschrift im Inhaltsverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="f6375-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="f6375-109">Beispiel-Apps</span><span class="sxs-lookup"><span data-stu-id="f6375-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="f6375-110">Featurebeispiele</span><span class="sxs-lookup"><span data-stu-id="f6375-110">Feature samples</span></span>

<span data-ttu-id="f6375-111">Die unten aufgeführten Featurebeispiele entsprechen bestimmten Implementierungen, die in unserer Dokumentation behandelt werden, und decken eine Reihe von Entwicklungsplattformen und Hardwaregeräten ab.</span><span class="sxs-lookup"><span data-stu-id="f6375-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="research-mode"></a><span data-ttu-id="f6375-112">Forschungsmodus</span><span class="sxs-lookup"><span data-stu-id="f6375-112">Research Mode</span></span>

<span data-ttu-id="f6375-113">Der Forschungsmodus wurde in der HoloLens der 1. Generation eingeführt, um Zugriff auf wesentliche Sensoren des Geräts zu gewähren, insbesondere für Forschungsanwendungen, die nicht für die Bereitstellung vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="f6375-113">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="f6375-114">Die folgenden Beispielanwendungen sind Beispiele für den Zugriff auf und die Aufzeichnung von Forschungsmodus-Datenströmen und die Verwendung der [intrinsischen und extrinsischen Funktionen](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="f6375-114">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="f6375-115">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="f6375-115">Reference article</span></span> | <span data-ttu-id="f6375-116">Beispielanwendung</span><span class="sxs-lookup"><span data-stu-id="f6375-116">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="f6375-117">Forschungsmodus</span><span class="sxs-lookup"><span data-stu-id="f6375-117">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="f6375-118">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="f6375-118">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="f6375-119">Forschungsmodus</span><span class="sxs-lookup"><span data-stu-id="f6375-119">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="f6375-120">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f6375-120">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="f6375-121">QR-Codes</span><span class="sxs-lookup"><span data-stu-id="f6375-121">QR codes</span></span>

<span data-ttu-id="f6375-122">HoloLens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der Position jedes Codes in der realen Welt einrichten.</span><span class="sxs-lookup"><span data-stu-id="f6375-122">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="f6375-123">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="f6375-123">Reference article</span></span> | <span data-ttu-id="f6375-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6375-124">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="f6375-125">QR-Codes</span><span class="sxs-lookup"><span data-stu-id="f6375-125">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="f6375-126">Nachverfolgen von QR-Codes in Unity</span><span class="sxs-lookup"><span data-stu-id="f6375-126">QR code tracking in Unity</span></span>](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a><span data-ttu-id="f6375-127">WebRTC</span><span class="sxs-lookup"><span data-stu-id="f6375-127">WebRTC</span></span>

<span data-ttu-id="f6375-128">Das MixedReality-WebRTC-Projekt ist eine Sammlung von Komponenten, die Entwicklern von Mixed Reality-Apps bei der Integration von Peer-to-Peer-Audio, -Video und Daten-Echtzeitkommunikation in Ihre Anwendungen helfen soll. WebRTC-Komponenten basieren auf dem WebRTC-Protokoll für Echtzeitkommunikation (RTC), das von den meisten modernen Webbrowsern unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="f6375-128">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="f6375-129">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="f6375-129">Reference article</span></span> | <span data-ttu-id="f6375-130">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6375-130">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="f6375-131">WebRTC</span><span class="sxs-lookup"><span data-stu-id="f6375-131">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="f6375-132">WebRTC-Beispiel-Apps</span><span class="sxs-lookup"><span data-stu-id="f6375-132">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="f6375-133">Holographische Mixed Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="f6375-133">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="f6375-134">Mit Mixed Reality-Aufnahme (MRC) wird die „Erste Person“-Erfahrung (Ego-Perspektive) der Vermischung realer mit digitalen Welten als Foto oder Video aufgenommen, wobei Sie das Gesehene mit anderen in Echtzeit teilen können.</span><span class="sxs-lookup"><span data-stu-id="f6375-134">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="f6375-135">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="f6375-135">Reference article</span></span> | <span data-ttu-id="f6375-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6375-136">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="f6375-137">Mixed Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="f6375-137">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="f6375-138">Beispiele für Mixed Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="f6375-138">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="f6375-139">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="f6375-139">Holographic Remoting</span></span>

<span data-ttu-id="f6375-140">Der Holographic Remoting-Player ist eine Begleit-App, die sich mit PC-Apps und -Spielen verbindet, die Holographic Remoting unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f6375-140">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="f6375-141">Holographic Remoting streamt holographische Inhalte in Echtzeit über eine WLAN-Verbindung von einem PC an Ihre Microsoft HoloLens. Es wird von HoloLens (1. Generation) und HoloLens 2 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f6375-141">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="f6375-142">Referenzartikel</span><span class="sxs-lookup"><span data-stu-id="f6375-142">Reference article</span></span> | <span data-ttu-id="f6375-143">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6375-143">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="f6375-144">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="f6375-144">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="f6375-145">Holographic Remoting-Beispiele</span><span class="sxs-lookup"><span data-stu-id="f6375-145">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |