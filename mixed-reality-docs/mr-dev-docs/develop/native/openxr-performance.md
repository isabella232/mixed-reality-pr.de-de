---
title: OpenXR – Leistung
description: Debuggen Sie die GPU-Leistung Ihrer openxr-Anwendungen.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, DirectX, Native, Native APP, benutzerdefiniertes Modul, Middleware, Leistung, Optimierung, GPU-Debugging, renderdoc, pix
ms.openlocfilehash: 7199b29067094d402348f00a9d26b93cf7e5393e
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613174"
---
# <a name="openxr-performance"></a><span data-ttu-id="7db94-104">OpenXR – Leistung</span><span class="sxs-lookup"><span data-stu-id="7db94-104">OpenXR performance</span></span>

<span data-ttu-id="7db94-105">Auf hololens 2 gibt es eine Reihe von Möglichkeiten, Kompositions Daten über zu übermitteln `xrEndFrame` , was zu einer Nachbearbeitung und spürbaren Leistungseinbußen führen kann.</span><span class="sxs-lookup"><span data-stu-id="7db94-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>
<span data-ttu-id="7db94-106">Um eine schlechte Leistung zu vermeiden, [senden `XrCompositionProjectionLayer` Sie eine einzelne](openxr-best-practices.md#use-a-single-projection-layer) mit den folgenden Merkmalen:</span><span class="sxs-lookup"><span data-stu-id="7db94-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="7db94-107">Verwenden eines Textur Arrays vorhandenes SwapChain</span><span class="sxs-lookup"><span data-stu-id="7db94-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="7db94-108">Verwenden des Haupt Farb-vorhandenes SwapChain-Formats</span><span class="sxs-lookup"><span data-stu-id="7db94-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="7db94-109">Empfohlene Anzeige Dimensionen verwenden</span><span class="sxs-lookup"><span data-stu-id="7db94-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="7db94-110">Legen Sie das Flag nicht fest. `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`</span><span class="sxs-lookup"><span data-stu-id="7db94-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="7db94-111">Legen `XrCompositionLayerDepthInfoKHR` `minDepth` Sie auf 0,0 f und `maxDepth` auf 1.0 f fest.</span><span class="sxs-lookup"><span data-stu-id="7db94-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="7db94-112">Für eine bessere Leistung sollten Sie Folgendes beachten:</span><span class="sxs-lookup"><span data-stu-id="7db94-112">For better performance, consider:</span></span>
* [<span data-ttu-id="7db94-113">Verwenden des 16-Bit-Tiefen Formats</span><span class="sxs-lookup"><span data-stu-id="7db94-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="7db94-114">Erstellen von instanziierten zeichnen-aufrufen</span><span class="sxs-lookup"><span data-stu-id="7db94-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
