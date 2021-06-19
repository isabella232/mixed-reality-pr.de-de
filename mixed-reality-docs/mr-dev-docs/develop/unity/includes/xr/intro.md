---
ms.openlocfilehash: ca3589364fb27c3f8087572113f09e48d30e087e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394574"
---
# <a name="openxr"></a>[<span data-ttu-id="6a28f-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="6a28f-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="6a28f-102">Das Mixed Reality OpenXR-Plug-In ist **die Empfehlung von Microsoft** für Unity 2020 LTS oder höher.</span><span class="sxs-lookup"><span data-stu-id="6a28f-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="6a28f-103">Da neue Features in Zukunft entwickelt werden, werden sie in Zukunft nur noch im Mixed Reality OpenXR-Plug-Ins enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="6a28f-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="6a28f-104">Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen bereit.</span><span class="sxs-lookup"><span data-stu-id="6a28f-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="6a28f-105">Dadurch können Sie raycasting-Code schreiben, der sich dann über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt.</span><span class="sxs-lookup"><span data-stu-id="6a28f-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6a28f-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="6a28f-106">Prerequisites</span></span> 

* <span data-ttu-id="6a28f-107">Neueste [Tools für HoloLens 2 Entwicklung](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="6a28f-107">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="6a28f-108">Neueste Unity 2020.3 LTS(wir empfehlen 2020.3.8f1 oder höher)</span><span class="sxs-lookup"><span data-stu-id="6a28f-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="6a28f-109">Mindestversionen</span><span class="sxs-lookup"><span data-stu-id="6a28f-109">Minimum versions</span></span>

<span data-ttu-id="6a28f-110">Die Anweisungen auf dieser Seite richten Sie mit den neuesten und besten Unity- und OpenXR-Anforderungen ein, die unten aufgeführt sind:</span><span class="sxs-lookup"><span data-stu-id="6a28f-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="6a28f-111">Neuestes Unity OpenXR-Plug-In (wir empfehlen 1.2 oder höher)</span><span class="sxs-lookup"><span data-stu-id="6a28f-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="6a28f-112">Neueste Mixed Reality OpenXR-Plug-In(wir empfehlen Version 1.0.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="6a28f-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="6a28f-113">**(Optional)** Neuestes MRTK(wir empfehlen Version 2.7 oder höher)</span><span class="sxs-lookup"><span data-stu-id="6a28f-113">**(Optional)** Latest MRTK, (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="6a28f-114">**(Optional)** Neuestes Universelles Renderpipelinepaket (wir empfehlen Version 10.5.1 oder höher)</span><span class="sxs-lookup"><span data-stu-id="6a28f-114">**(Optional)** Latest Universal Render Pipeline package, (we recommend version 10.5.1 or later)</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="6a28f-115">Wenn Sie VR-Anwendungen auf einem Windows-PC erstellen, ist das Mixed Reality OpenXR-Plug-In nicht unbedingt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6a28f-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="6a28f-116">Sie sollten das Plug-In jedoch installieren, wenn Sie die Controllerzuordnung für HP Reverb G2-Controller anpassen oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.</span><span class="sxs-lookup"><span data-stu-id="6a28f-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="6a28f-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="6a28f-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="6a28f-118">Microsoft empfiehlt nicht die Verwendung des Windows XR-Plug-Ins für neue Projekte in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="6a28f-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="6a28f-119">Wenn Sie jedoch Unity 2019 verwenden und AR Foundation 2.0 für die Kompatibilität mit ARCore-/ARKit-Geräten benötigen, ermöglicht dieses Plug-In diese Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="6a28f-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6a28f-120">Die Verwendung dieses Plug-Ins in Unity 2019 unterstützt azure Spatial Anchors nicht.</span><span class="sxs-lookup"><span data-stu-id="6a28f-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="6a28f-121">Legacy-XR</span><span class="sxs-lookup"><span data-stu-id="6a28f-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="6a28f-122">Wenn Sie noch unity 2019 oder früher verwenden, empfiehlt Microsoft die Verwendung der älteren integrierten XR-Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="6a28f-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="6a28f-123">Das Windows XR-Plug-In ist zwar in Unity 2019 funktionsfähig, wird jedoch nicht empfohlen, da Azure Spatial Anchors nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="6a28f-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>