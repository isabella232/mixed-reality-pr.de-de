---
title: HoloLens-Foto-/Videokamera in Unreal
description: Erfahren Sie, wie Sie die Foto- und Videokamera von HoloLens für die Mixed Reality-Aufnahme und die Objektlokalisierung in Unreal verwenden.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Kamera, PV-Kamera, MRC, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 15eba0c992d6d3d8895314f1a6128ace18c02483
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010060"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="7be33-104">HoloLens-Foto-/Videokamera in Unreal</span><span class="sxs-lookup"><span data-stu-id="7be33-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="7be33-105">Die HoloLens weist eine Foto-/Videokamera (FV-Kamera) auf dem Visor auf, die sowohl für die Mixed Reality-Aufnahme (Mixed Reality Capture, MRC) als auch zum Lokalisieren von Objekten im Weltbereich von Unreal anhand von Pixelkoordinaten im Kamerabild verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="7be33-105">The HoloLens has a Photo/Video (PV) Camera on the visor that can be used for both Mixed Reality Capture (MRC) and locating objects in Unreal world space from pixel coordinates in the camera frame.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7be33-106">Die PV-Kamera wird nicht mit Holographic Remoting unterstützt, aber es ist möglich, eine mit Ihrem PC verbundene Webcam zu verwenden, um die PV-Kamerafunktion von HoloLens zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="7be33-106">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="7be33-107">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="7be33-107">Next Development Checkpoint</span></span>

<span data-ttu-id="7be33-108">Wenn Sie der Unity-Entwicklungs-Journey folgen, die wir entworfen haben, befinden Sie sich mitten im Kennenlernen der Mixed Reality-Plattformfunktionen und APIs.</span><span class="sxs-lookup"><span data-stu-id="7be33-108">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="7be33-109">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="7be33-109">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7be33-110">QR-Codes</span><span class="sxs-lookup"><span data-stu-id="7be33-110">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="7be33-111">Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:</span><span class="sxs-lookup"><span data-stu-id="7be33-111">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7be33-112">Bereitstellung auf Gerät</span><span class="sxs-lookup"><span data-stu-id="7be33-112">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="7be33-113">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#3-platform-capabilities-and-apis) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="7be33-113">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7be33-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7be33-114">See also</span></span>

* [<span data-ttu-id="7be33-115">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="7be33-115">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="7be33-116">Mixed Reality-Aufnahme für Entwickler</span><span class="sxs-lookup"><span data-stu-id="7be33-116">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
