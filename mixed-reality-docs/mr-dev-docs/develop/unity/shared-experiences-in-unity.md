---
title: Gemeinsame Erlebnisse in Unity
description: Verwenden Sie die gleichen holograms zwischen mehreren Benutzern in einer Unity-Anwendung.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Sharing, Anchor, worldanchor, Mr Sharing 250, worldanchortransferbatch, spatialperception, Azure, Azure Spatial Anchor, ASA, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset
ms.openlocfilehash: c9f432a2ef26e28a2329f9fd191f680a4148ca7e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678459"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="ae414-104">Gemeinsame Erlebnisse in Unity</span><span class="sxs-lookup"><span data-stu-id="ae414-104">Shared experiences in Unity</span></span>

<span data-ttu-id="ae414-105">Eine gemeinsame Nutzung ist eine, in der mehrere Benutzer mit jeweils eigenen hololens-, IOS-oder Android-Geräten das gleiche – Hologramm anzeigen und mit diesem interagieren, das an einem festgelegten Punkt positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="ae414-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="ae414-106">Dies wird durch die räumliche Anker Freigabe erreicht.</span><span class="sxs-lookup"><span data-stu-id="ae414-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="ae414-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="ae414-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="ae414-108">Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um permanente, von der Cloud gesicherte räumliche Anker zu erstellen, die Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.</span><span class="sxs-lookup"><span data-stu-id="ae414-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="ae414-109">Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers auf mehreren Geräten kann jeder Benutzer den Inhalt in Relation zu diesem Anker am gleichen physischen Speicherort sehen.</span><span class="sxs-lookup"><span data-stu-id="ae414-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="ae414-110">Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.</span><span class="sxs-lookup"><span data-stu-id="ae414-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="ae414-111">Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> auch für die asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden.</span><span class="sxs-lookup"><span data-stu-id="ae414-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="ae414-112">Durch die gemeinsame Nutzung eines dauerhaften Cloudraumankers können mehrere Geräte dasselbe persistierte Hologramm im Verlauf der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="ae414-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="ae414-113">Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.</span><span class="sxs-lookup"><span data-stu-id="ae414-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="ae414-114">Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.</span><span class="sxs-lookup"><span data-stu-id="ae414-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="ae414-115">Lokale Anker Übertragungen</span><span class="sxs-lookup"><span data-stu-id="ae414-115">Local anchor transfers</span></span>

<span data-ttu-id="ae414-116">In Fällen, in denen Sie keine räumlichen Anker von Azure verwenden können, ermöglichen [lokale Anker Übertragungen](../../out-of-scope/local-anchor-transfers-in-unity.md) einem hololens-Gerät das Exportieren eines Ankers, der von einem zweiten hololens-Gerät importiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="ae414-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="ae414-117">Beachten Sie, dass dieser Ansatz weniger robusten Anker als räumliche Azure-Anker bietet und IOS-und Android-Geräte von diesem Ansatz nicht unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="ae414-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="ae414-118">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="ae414-118">Next Development Checkpoint</span></span>

<span data-ttu-id="ae414-119">Wenn Sie der Unity-Entwicklungs-Prüfpunkt-Journey folgen, die wir festgelegt haben, sind Sie mitten in der Untersuchung der Funktionen und APIs der Mixed Reality-Plattform.</span><span class="sxs-lookup"><span data-stu-id="ae414-119">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="ae414-120">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="ae414-120">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae414-121">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="ae414-121">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="ae414-122">Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:</span><span class="sxs-lookup"><span data-stu-id="ae414-122">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae414-123">Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets</span><span class="sxs-lookup"><span data-stu-id="ae414-123">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="ae414-124">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-platform-capabilities-and-apis) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="ae414-124">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae414-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ae414-125">See also</span></span>
* [<span data-ttu-id="ae414-126">Gemeinsame Erlebnisse in Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ae414-126">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="ae414-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="ae414-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="ae414-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a></span><span class="sxs-lookup"><span data-stu-id="ae414-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
