---
title: Verwenden von webxr mit Windows Mixed Reality
description: Erlernen Sie die Grundlagen der Verwendung und Entwicklung für webxr-Anwendungen, die auf Windows Mixed Reality-immersiven Headsets ausgeführt werden.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: Webxr, winmr, webar, webvr, windowsmixedreality, hololens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web AR, 360, 360 Video, 360 Videos, 360 Photo, 360 Fotos, 360 Content, immersives Web, immersiveweb, IW
ms.openlocfilehash: e49f5f2422c9802f94b63943f8a38949a2969f83
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006940"
---
# <a name="webxr-overview"></a><span data-ttu-id="62de3-104">Übersicht über webxr</span><span class="sxs-lookup"><span data-stu-id="62de3-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="62de3-105">Was ist webxr?</span><span class="sxs-lookup"><span data-stu-id="62de3-105">What is WebXR</span></span>

<span data-ttu-id="62de3-106">Die **webxr-Geräte-API** ist für den Zugriff auf die Geräte der **virtuellen Realität (VR)** und der **erweiterten Realität (AR)** , einschließlich **Sensoren** und auf dem **Web** **eingebundenes anzeigen** .</span><span class="sxs-lookup"><span data-stu-id="62de3-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="62de3-107">Die webxr-Geräte-API ist zurzeit auf Microsoft Edge verfügbar, und die Chrome-Version 79 und höhere Versionen unterstützen webxr als Standard.</span><span class="sxs-lookup"><span data-stu-id="62de3-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="62de3-108">Den neuesten Browser-Support Status für webxr finden Sie unter [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="62de3-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="62de3-109">Erfahren Sie mehr über die [gemischte Windows-Realität und den neuen Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in den [Neuerungen](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) .</span><span class="sxs-lookup"><span data-stu-id="62de3-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="62de3-110">Anzeigen von webxr</span><span class="sxs-lookup"><span data-stu-id="62de3-110">Viewing WebXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62de3-111">Microsoft Edge (Legacy) unterstützt nur webvr, eine veraltete API, die in den aktuellen Browsern nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="62de3-111">Microsoft Edge (Legacy) only supports WebVR, a deprecated API that is not available in current browsers.</span></span> <span data-ttu-id="62de3-112">Der neue Windows Server **[-Edge-Browser](../../whats-new/new-microsoft-edge.md)** unterstützt jedoch webxr und ist für die VR-Prototypen in Windows Mixed Reality verfügbar.</span><span class="sxs-lookup"><span data-stu-id="62de3-112">However, the new **[Chromium-based Edge browser](../../whats-new/new-microsoft-edge.md)** supports WebXR and is available for VR prototyping in Windows Mixed Reality.</span></span> <span data-ttu-id="62de3-113">Webvr ist nicht im neuen, auf dem Server verwendeten Edge-Browser verfügbar.</span><span class="sxs-lookup"><span data-stu-id="62de3-113">WebVR will not be available in the new Chromium-based Edge browser.</span></span>
> 
> <span data-ttu-id="62de3-114">Wenn Sie noch heute eine Methode zum Prototypen von webxr auf hololens 2 suchen, informieren Sie sich in [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span><span class="sxs-lookup"><span data-stu-id="62de3-114">If you're looking for a way to prototype WebXR on HoloLens 2 today, check out [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>

<span data-ttu-id="62de3-115">Um zu testen, ob Ihr Browser webxr unterstützt, können Sie in Ihrem Browser zu [webxr-Beispielen](https://immersive-web.github.io/webxr-samples/) navigieren.</span><span class="sxs-lookup"><span data-stu-id="62de3-115">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="62de3-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="62de3-116">See Also</span></span>

* [<span data-ttu-id="62de3-117">Webxr-Geräte-API-Spezifikation</span><span class="sxs-lookup"><span data-stu-id="62de3-117">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="62de3-118">Dokumentation zur webxr-Geräte-API</span><span class="sxs-lookup"><span data-stu-id="62de3-118">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="62de3-119">Immersiveweb. dev</span><span class="sxs-lookup"><span data-stu-id="62de3-119">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="62de3-120">Webxr-Beispiele</span><span class="sxs-lookup"><span data-stu-id="62de3-120">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="62de3-121">Windows Mixed Reality und die neue Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="62de3-121">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="62de3-122">Immersives Web-W3C GitHub</span><span class="sxs-lookup"><span data-stu-id="62de3-122">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="62de3-123">[WebGL-API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="62de3-123">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="62de3-124">[Gamepad-API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) -und [Gamepad-Erweiterungen](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="62de3-124">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="62de3-125">Umgang mit verlorenem Kontext in WebGL</span><span class="sxs-lookup"><span data-stu-id="62de3-125">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="62de3-126">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="62de3-126">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="62de3-127">glTF</span><span class="sxs-lookup"><span data-stu-id="62de3-127">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="62de3-128">Verwenden von Babylon.js zum Erstellen von webxr-Erfahrungen</span><span class="sxs-lookup"><span data-stu-id="62de3-128">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="62de3-129">Immersive Web-Community-Gruppe</span><span class="sxs-lookup"><span data-stu-id="62de3-129">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
