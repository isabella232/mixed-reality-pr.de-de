---
title: Gemeinsame Erlebnisse in Unity
description: Erfahren Sie, wie Sie die gleichen holograms zwischen mehreren Benutzern in einer Unity-Anwendung mit räumlichen Azure-Ankern gemeinsam verwenden.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Sharing, Anchor, worldanchor, Mr Sharing 250, worldanchortransferbatch, spatialperception, Azure, Azure Spatial Anchor, ASA, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset
ms.openlocfilehash: 4d24f3690f4d4b1fc206dbd2b5e0aa5afad6c34c
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226339"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="1c8b1-104">Gemeinsame Erlebnisse in Unity</span><span class="sxs-lookup"><span data-stu-id="1c8b1-104">Shared experiences in Unity</span></span>

<span data-ttu-id="1c8b1-105">Eine gemeinsame Nutzung ermöglicht es mehreren Benutzern, die jeweils über ein eigenes hololens-, IOS-oder Android-Gerät verfügen, das gleiche Hologram anzuzeigen und mit Ihnen zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-105">A shared experience lets multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="1c8b1-106">Holograms werden über die räumliche Anker Freigabe an einem bestimmten Punkt im Bereich positioniert.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-106">Holograms are positioned at a fixed point in space through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="1c8b1-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="1c8b1-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="1c8b1-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Räumliche Azure-Anker</a> erstellen dauerhafte, cloudgestützte räumliche Anker, die Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="1c8b1-109">Durch die gemeinsame Nutzung eines gemeinsamen räumlichen Ankers auf mehreren Geräten kann jeder Benutzer den Inhalt in Relation zu diesem Anker am gleichen physischen Speicherort sehen.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span> 

<span data-ttu-id="1c8b1-110">Sie können auch <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">räumliche Azure-Anker</a> für die asynchrone – Hologramm-Persistenz über hololens-, IOS-und Android-Geräte verwenden.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-110">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="1c8b1-111">Durch die gemeinsame Nutzung eines permanenten clouddiensts können mehrere Geräte im Lauf der Zeit dasselbe persistente Hologramm beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-111">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="1c8b1-112">Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-112">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="1c8b1-113">Nachdem Azure Spatial Anchor eingerichtet wurde, können Sie <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-113">Once Azure Spatial Anchors is set up, you can <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="1c8b1-114">Lokale Anker Übertragungen</span><span class="sxs-lookup"><span data-stu-id="1c8b1-114">Local anchor transfers</span></span>

<span data-ttu-id="1c8b1-115">In Fällen, in denen Sie keine räumlichen Anker von Azure verwenden können, ermöglichen [lokale Anker Übertragungen](../../out-of-scope/local-anchor-transfers-in-unity.md) einem hololens-Gerät das Exportieren eines Ankers, sodass ein zweiter hololens ihn importieren kann.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-115">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor so that a second HoloLens can import it.</span></span>  <span data-ttu-id="1c8b1-116">Diese Vorgehensweise wird auf IOS-und Android-Geräten nicht unterstützt und bietet weniger robusten Anker als Anker als räumliche Azure-Anker.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-116">This approach is not supported on iOS and Android devices, and provides less robust anchor recall than Azure Spatial Anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="1c8b1-117">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="1c8b1-117">Next Development Checkpoint</span></span>

<span data-ttu-id="1c8b1-118">Wenn Sie der Unity-Entwicklungs Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-118">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="1c8b1-119">Von hier aus können Sie mit dem nächsten Abschnitt fortfahren:</span><span class="sxs-lookup"><span data-stu-id="1c8b1-119">From here, you can continue to the next section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c8b1-120">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="1c8b1-120">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="1c8b1-121">Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:</span><span class="sxs-lookup"><span data-stu-id="1c8b1-121">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c8b1-122">Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets</span><span class="sxs-lookup"><span data-stu-id="1c8b1-122">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="1c8b1-123">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-advanced-features) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-123">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c8b1-124">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1c8b1-124">See also</span></span>
* [<span data-ttu-id="1c8b1-125">Gemeinsame Erlebnisse in Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1c8b1-125">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="1c8b1-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="1c8b1-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="1c8b1-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a></span><span class="sxs-lookup"><span data-stu-id="1c8b1-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
