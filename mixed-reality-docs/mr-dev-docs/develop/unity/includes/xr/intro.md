---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603713"
---
# <a name="openxr"></a>[<span data-ttu-id="77aa5-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="77aa5-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="77aa5-102">Das Mixed Reality OpenXR-Plug-In ist **die Empfehlung** von Microsoft für **Unity 2020 LTS** oder höher.</span><span class="sxs-lookup"><span data-stu-id="77aa5-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for **Unity 2020 LTS** or later.</span></span> <span data-ttu-id="77aa5-103">Da neue Features in Zukunft entwickelt werden, werden sie in Zukunft nur noch in das OpenXR-Plug-In Mixed Reality enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="77aa5-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="77aa5-104">Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="77aa5-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="77aa5-105">Auf diese Weise können Sie Raycastcode schreiben, sobald er sich über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt.</span><span class="sxs-lookup"><span data-stu-id="77aa5-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="77aa5-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="77aa5-106">Prerequisites</span></span> 

* <span data-ttu-id="77aa5-107">Neueste [Tools für HoloLens 2 Entwicklung](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="77aa5-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="77aa5-108">Neueste Unity 2020.3 LTS: Version 2020.3.8f1 oder höher</span><span class="sxs-lookup"><span data-stu-id="77aa5-108">Latest Unity 2020.3 LTS: version 2020.3.8f1 or later</span></span>

### <a name="recommended-package-versions"></a><span data-ttu-id="77aa5-109">Empfohlene Paketversionen</span><span class="sxs-lookup"><span data-stu-id="77aa5-109">Recommended package versions</span></span>

<span data-ttu-id="77aa5-110">Die Anweisungen auf dieser Seite richten Sie mit den grundlegenden Unity OpenXR-Paketen ein, die zum Bereitstellen HoloLens 2 oder Windows Mixed Reality erforderlich sind:</span><span class="sxs-lookup"><span data-stu-id="77aa5-110">The instructions in this page will set you up with the core Unity OpenXR packages required to deploy HoloLens 2 or Windows Mixed Reality apps:</span></span>

* <span data-ttu-id="77aa5-111">Unity OpenXR-Plug-In: Version 1.2 oder höher</span><span class="sxs-lookup"><span data-stu-id="77aa5-111">Unity OpenXR plugin: version 1.2 or later</span></span>
* <span data-ttu-id="77aa5-112">Mixed Reality OpenXR-Plug-In: Version 1.0.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="77aa5-112">Mixed Reality OpenXR plugin: version 1.0.0 or later</span></span>

<span data-ttu-id="77aa5-113">Wenn Sie die folgenden Pakete in Ihrem Projekt verwenden, müssen Sie sicherstellen, dass Sie mindestens die unten aufgeführten Mindestversionen verwenden:</span><span class="sxs-lookup"><span data-stu-id="77aa5-113">If you use the following packages in your project, you will need to ensure that you use at least the minimum versions listed below:</span></span>

* <span data-ttu-id="77aa5-114">MRTK: Version 2.7.2 oder höher</span><span class="sxs-lookup"><span data-stu-id="77aa5-114">MRTK: version 2.7.2 or later</span></span>
* <span data-ttu-id="77aa5-115">AR Foundation: Version 4.1.1 oder höher</span><span class="sxs-lookup"><span data-stu-id="77aa5-115">AR Foundation: version 4.1.1 or later</span></span>
* <span data-ttu-id="77aa5-116">Universal Render Pipeline (URP): Version 10.5.1 oder höher</span><span class="sxs-lookup"><span data-stu-id="77aa5-116">Universal Render Pipeline (URP): version 10.5.1 or later</span></span>
* <span data-ttu-id="77aa5-117">Azure Spatial Anchors: Version 2.10 oder höher</span><span class="sxs-lookup"><span data-stu-id="77aa5-117">Azure Spatial Anchors: version 2.10 or later</span></span>
* <span data-ttu-id="77aa5-118">Azure Remote Rendering: Version 1.0.15 oder höher</span><span class="sxs-lookup"><span data-stu-id="77aa5-118">Azure Remote Rendering: version 1.0.15 or later</span></span>

> [!NOTE]
> <span data-ttu-id="77aa5-119">Wenn Sie VR-Anwendungen auf einem Windows PC erstellen, ist Mixed Reality OpenXR-Plug-In nicht zwingend erforderlich.</span><span class="sxs-lookup"><span data-stu-id="77aa5-119">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not strictly required.</span></span> <span data-ttu-id="77aa5-120">Sie sollten das Plug-In jedoch installieren, wenn Sie Eingabebindungen für HP Reverb G2-Controller einrichten oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.</span><span class="sxs-lookup"><span data-stu-id="77aa5-120">However, you'll want to install the plugin if you're setting up input bindings for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="77aa5-121">Windows Xr</span><span class="sxs-lookup"><span data-stu-id="77aa5-121">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="77aa5-122">Microsoft empfiehlt nicht die Verwendung des Windows XR-Plug-Ins für neue Projekte in Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="77aa5-122">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>  <span data-ttu-id="77aa5-123">Stattdessen sollten Sie das OpenXR Mixed Reality-Plug-In verwenden.</span><span class="sxs-lookup"><span data-stu-id="77aa5-123">Instead, you should use the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="77aa5-124">Wenn Sie jedoch Unity 2019 verwenden und AR Foundation 2.0 für die Kompatibilität mit ARCore/ARKit-Geräten benötigen, ermöglicht dieses Plug-In diese Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="77aa5-124">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="77aa5-125">Die Verwendung dieses Plug-Ins in Unity 2019 ist nicht mit Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="77aa5-125">Using this plugin in Unity 2019 is not compatible with Azure Spatial Anchors.</span></span>

# <a name="legacy-xr"></a>[<span data-ttu-id="77aa5-126">Legacy-XR</span><span class="sxs-lookup"><span data-stu-id="77aa5-126">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="77aa5-127">Wenn Sie noch unity **2019** oder früher verwenden, empfiehlt Microsoft die Verwendung der **älteren integrierten XR-Unterstützung.**</span><span class="sxs-lookup"><span data-stu-id="77aa5-127">If you're still on **Unity 2019** or earlier, Microsoft recommends using the **Legacy Built-in XR support**.</span></span>

<span data-ttu-id="77aa5-128">Das Windows XR-Plug-In ist zwar in Unity 2019 funktionsfähig, wird jedoch nicht empfohlen, da dieses Plug-In nicht mit Azure Spatial Anchors unter Unity 2019 kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="77aa5-128">While the Windows XR plugin is functional on Unity 2019, it's not recommended because this plugin is not compatible with Azure Spatial Anchors on Unity 2019.</span></span>

<span data-ttu-id="77aa5-129">Wenn Sie ein neues Projekt starten, empfiehlt es sich, [stattdessen Unity 2020](../../choosing-unity-version.md) zu installieren und das OpenXR Mixed Reality-Plug-In zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="77aa5-129">If you're starting a new project, we recommend [installing Unity 2020 instead](../../choosing-unity-version.md) and using the Mixed Reality OpenXR plugin.</span></span>