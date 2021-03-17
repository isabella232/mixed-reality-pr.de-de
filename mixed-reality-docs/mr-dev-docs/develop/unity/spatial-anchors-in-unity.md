---
title: Räumliche Anker in Unity
description: Erfahren Sie, wie Sie räumliche Anker in Unity-Anwendungen mit gemischter Realität erstellen, speichern und abrufen.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, räumliche Anker, Anker Speicher, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623620"
---
# <a name="spatial-anchors-in-unity"></a><span data-ttu-id="52973-104">Räumliche Anker in Unity</span><span class="sxs-lookup"><span data-stu-id="52973-104">Spatial Anchors in Unity</span></span>

<span data-ttu-id="52973-105">Räumliche Anker sparen holograms im realen Raum zwischen Anwendungs Sitzungen.</span><span class="sxs-lookup"><span data-stu-id="52973-105">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="52973-106">Nachdem Sie im Anker Speicher der hololens gespeichert wurden, können Sie gefunden und in verschiedene Sitzungen geladen werden. Sie sind ein idealer Fall Back, wenn keine Internetverbindung besteht.</span><span class="sxs-lookup"><span data-stu-id="52973-106">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52973-107">Lokale Anker werden auf dem Gerät gespeichert, während Azure-Raumanker in der Cloud gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="52973-107">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="52973-108">Wenn Sie Azure Cloud Services zum Speichern Ihrer Anker verwenden möchten, verfügen wir über ein Dokument, in dem Sie durch den Integrationsprozess für [Azure-Raumanker](../mixed-reality-cloud-services.md#azure-spatial-anchors) geführt werden.</span><span class="sxs-lookup"><span data-stu-id="52973-108">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="52973-109">Beachten Sie, dass Sie sowohl lokale als auch Azure-Anker im selben Projekt haben können, ohne dass Konflikte auftreten.</span><span class="sxs-lookup"><span data-stu-id="52973-109">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="understanding-anchors"></a><span data-ttu-id="52973-110">Grundlegendes zu Anker</span><span class="sxs-lookup"><span data-stu-id="52973-110">Understanding Anchors</span></span>

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a><span data-ttu-id="52973-111">Verwenden des anchorstores</span><span class="sxs-lookup"><span data-stu-id="52973-111">Using the AnchorStore</span></span>

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="52973-112">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="52973-112">Next Development Checkpoint</span></span>

<span data-ttu-id="52973-113">Wenn Sie der Unity-Entwicklungs Prüf Punkt Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, dass Sie die Grundbausteine der gemischten Realität erkunden.</span><span class="sxs-lookup"><span data-stu-id="52973-113">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="52973-114">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="52973-114">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="52973-115">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="52973-115">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="52973-116">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="52973-116">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="52973-117">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="52973-117">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="52973-118">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="52973-118">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="52973-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="52973-119">See Also</span></span>
* [<span data-ttu-id="52973-120">Dauerhaftigkeit räumlicher Anker</span><span class="sxs-lookup"><span data-stu-id="52973-120">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="52973-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="52973-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="52973-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a></span><span class="sxs-lookup"><span data-stu-id="52973-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="52973-123">Skalierungsmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="52973-123">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="52973-124">Räumliche Phase</span><span class="sxs-lookup"><span data-stu-id="52973-124">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="52973-125">Verfolgbarkeitsverlust in Unity</span><span class="sxs-lookup"><span data-stu-id="52973-125">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="52973-126">Raumanker</span><span class="sxs-lookup"><span data-stu-id="52973-126">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="52973-127">Gemeinsame Erlebnisse in Unity</span><span class="sxs-lookup"><span data-stu-id="52973-127">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)