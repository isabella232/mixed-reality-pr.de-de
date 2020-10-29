---
title: HoloLens-Foto-/Videokamera in Unreal
description: Leitfaden für die Verwendung der HoloLens-Foto-/Videokamera in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Kamera, FV-Kamera, MRC
ms.openlocfilehash: e66583d46d64361621303e36a5fbcc209300f5d8
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91697220"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="0d44a-104">HoloLens-Foto-/Videokamera in Unreal</span><span class="sxs-lookup"><span data-stu-id="0d44a-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="0d44a-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="0d44a-105">Overview</span></span>

<span data-ttu-id="0d44a-106">HoloLens verfügt über eine Foto-/Videokamera (FV), die einerseits für die Mixed Reality-Aufnahme (Mixed Reality Capture, MRC) und andererseits von einer App zum Zugriff auf visuelle Elemente der realen Welt verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="0d44a-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="0d44a-107">Rendering von der FV-Kamera für MRC</span><span class="sxs-lookup"><span data-stu-id="0d44a-107">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="0d44a-108">Dafür ist **Unreal Engine 4.25** oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0d44a-108">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="0d44a-109">Das System und benutzerdefinierte MRC-Rekorder erstellen Mixed Reality-Aufnahmen, indem sie die FV-Kamera mit Hologrammen kombinieren, die von der immersiven App gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="0d44a-109">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="0d44a-110">Standardmäßig wird für die Mixed-Reality-Aufnahme die holografische Ausgabe des rechten Auges verwendet.</span><span class="sxs-lookup"><span data-stu-id="0d44a-110">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="0d44a-111">Wenn eine immersive App hingegen [von der FV-Kamera rendert](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), wird stattdessen diese verwendet.</span><span class="sxs-lookup"><span data-stu-id="0d44a-111">If an immersive app chooses to [render from the PV Camera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="0d44a-112">Dies ermöglicht eine bessere Abstimmung zwischen der realen Welt und den Hologrammen im MRC-Video.</span><span class="sxs-lookup"><span data-stu-id="0d44a-112">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="0d44a-113">So abonnieren Sie das Rendering von der FV-Kamera:</span><span class="sxs-lookup"><span data-stu-id="0d44a-113">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="0d44a-114">Rufen Sie **SetEnabledMixedRealityCamera** und **ResizeMixedRealityCamera** auf.</span><span class="sxs-lookup"><span data-stu-id="0d44a-114">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="0d44a-115">Verwenden Sie die Werte **Size X** (Größe X) und **Size Y** (Größe Y), um die Videoabmessungen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="0d44a-115">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Dritte Kamera](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="0d44a-117">Unreal verarbeitet dann Anforderungen von MRC, aus der Perspektive der FV-Kamera zu rendern.</span><span class="sxs-lookup"><span data-stu-id="0d44a-117">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="0d44a-118">Nur wenn [Mixed Reality Capture](../../mixed-reality-capture.md) (Mixed Reality-Aufnahme) ausgelöst wird, wird die App aufgefordert, aus der Perspektive der Foto-/Videokamera zu rendern.</span><span class="sxs-lookup"><span data-stu-id="0d44a-118">Only when [Mixed Reality Capture](../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="0d44a-119">Verwenden der FV-Kamera</span><span class="sxs-lookup"><span data-stu-id="0d44a-119">Using the PV Camera</span></span>

<span data-ttu-id="0d44a-120">Die Webcam-Textur kann im Spiel zur Laufzeit abgerufen werden, dies muss jedoch im Editor unter **Edit > Project Settings** (Bearbeiten > Projekteinstellungen) aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="0d44a-120">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings** :</span></span>
1. <span data-ttu-id="0d44a-121">Wechseln Sie zu **Platforms > HoloLens > Capabilities** (Plattformen > HoloLens > Funktionen), und aktivieren Sie **Webcam** .</span><span class="sxs-lookup"><span data-stu-id="0d44a-121">Go to **Platforms > HoloLens > Capabilities** and check **Webcam** .</span></span>
    * <span data-ttu-id="0d44a-122">Verwenden Sie die Funktion **StartCameraCapture** , um die Webcam zur Laufzeit zu nutzen, und die Funktion **StopCameraCapture** , um die Aufzeichnung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="0d44a-122">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Kamera: Starten/Beenden](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="0d44a-124">Rendern eines Bilds</span><span class="sxs-lookup"><span data-stu-id="0d44a-124">Rendering an image</span></span>
<span data-ttu-id="0d44a-125">So wird das Kamerabild gerendert:</span><span class="sxs-lookup"><span data-stu-id="0d44a-125">To render the camera image:</span></span>
1. <span data-ttu-id="0d44a-126">Erstellen Sie auf der Grundlage eines Materials im Projekt eine dynamische Materialinstanz, die im Screenshot unten den Namen **PVCamMat** trägt.</span><span class="sxs-lookup"><span data-stu-id="0d44a-126">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="0d44a-127">Legen Sie die dynamische Materialinstanz auf eine **Material Instance Dynamic Object Reference** -Variable (Materialinstanz mit dynamischem Objektverweis) fest.</span><span class="sxs-lookup"><span data-stu-id="0d44a-127">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="0d44a-128">Legen Sie das Material des Objekts in der Szene, das den Kamerafeed rendern soll, auf diese neue dynamische Materialinstanz fest.</span><span class="sxs-lookup"><span data-stu-id="0d44a-128">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="0d44a-129">Starten Sie einen Timer, der dazu verwendet wird, das Kamerabild an das Material zu binden.</span><span class="sxs-lookup"><span data-stu-id="0d44a-129">Start a timer that will be used to bind the camera image to the material.</span></span>

![Kamera: Rendern](images/unreal-camera-render.PNG)

4. <span data-ttu-id="0d44a-131">Erstellen Sie eine neue Funktion für diesen Timer (in diesem Fall: **MaterialTimer** ), und rufen Sie **GetARCameraImage** auf, um die Textur von der Webcam abzurufen.</span><span class="sxs-lookup"><span data-stu-id="0d44a-131">Create a new function for this timer, in this case **MaterialTimer** , and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="0d44a-132">Ist diese Textur gültig, legen Sie im Shader einen Texturparameter auf dieses Bild fest.</span><span class="sxs-lookup"><span data-stu-id="0d44a-132">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="0d44a-133">Falls nicht, starten Sie den Materialtimer erneut.</span><span class="sxs-lookup"><span data-stu-id="0d44a-133">Otherwise, start the material timer again.</span></span>

![Kameratextur von Webcam](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="0d44a-135">Achten Sie darauf, dass das Material über einen Parameter verfügt, der mit dem Namen in **SetTextureParameterValue** übereinstimmt, der an einen Farbeintrag gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="0d44a-135">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="0d44a-136">Ohne dies kann das Kamerabild nicht ordnungsgemäß angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0d44a-136">Without this, the camera image can't be properly displayed.</span></span>

![Kamera: Textur](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a><span data-ttu-id="0d44a-138">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="0d44a-138">Next Development Checkpoint</span></span>

<span data-ttu-id="0d44a-139">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der Mixed Reality-Plattformfunktionen und APIs.</span><span class="sxs-lookup"><span data-stu-id="0d44a-139">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="0d44a-140">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="0d44a-140">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0d44a-141">QR-Codes</span><span class="sxs-lookup"><span data-stu-id="0d44a-141">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="0d44a-142">Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:</span><span class="sxs-lookup"><span data-stu-id="0d44a-142">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0d44a-143">Bereitstellung auf Gerät</span><span class="sxs-lookup"><span data-stu-id="0d44a-143">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="0d44a-144">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#3-platform-capabilities-and-apis) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="0d44a-144">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d44a-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0d44a-145">See also</span></span>
* [<span data-ttu-id="0d44a-146">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="0d44a-146">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="0d44a-147">Mixed Reality-Aufnahme für Entwickler</span><span class="sxs-lookup"><span data-stu-id="0d44a-147">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
