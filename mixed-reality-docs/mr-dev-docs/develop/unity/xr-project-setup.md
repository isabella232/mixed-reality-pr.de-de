---
title: Einrichten der XR-Konfiguration
description: Bleiben Sie über die neuesten Unity XR-Konfigurationsempfehlungen für die HoloLens-Anwendungsentwicklung auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: df7c5039c6cdcfa1e39dc96f0829611dd5209772
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394564"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="1fb79-104">Einrichten der XR-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="1fb79-104">Setting up your XR configuration</span></span>

<span data-ttu-id="1fb79-105">Wenn Sie ein neues Unity-Projekt starten, stehen Ihnen drei verschiedene Optionen zur Verfügung, um Ihre XR-Anforderungen zu erfüllen:</span><span class="sxs-lookup"><span data-stu-id="1fb79-105">When you start a new Unity project, you have three different options for handling your XR needs:</span></span> 
* <span data-ttu-id="1fb79-106">OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="1fb79-106">OpenXR plugin</span></span>
* <span data-ttu-id="1fb79-107">Windows XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="1fb79-107">Windows XR plugin</span></span>
* <span data-ttu-id="1fb79-108">Legacy-XR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="1fb79-108">Legacy XR plugin</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="1fb79-109">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="1fb79-109">Setting up your project with MRTK</span></span>

<span data-ttu-id="1fb79-110">MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="1fb79-110">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="1fb79-111">MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="1fb79-111">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="1fb79-112">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.</span><span class="sxs-lookup"><span data-stu-id="1fb79-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1fb79-113">Probieren Sie unsere MRTK-Tutorials aus</span><span class="sxs-lookup"><span data-stu-id="1fb79-113">Try out our MRTK tutorials</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

<span data-ttu-id="1fb79-114">Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="1fb79-114">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

### <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="1fb79-115">Verwenden von MRTK mit OpenXR-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="1fb79-115">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="1fb79-116">MRTK-Unity Release 2.7 bietet bessere Unterstützung für das Mixed Reality OpenXR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="1fb79-116">MRTK-Unity 2.7 release provides better supports for the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="1fb79-117">Öffnen Sie das [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) erneut, um das Mixed Reality Toolkit zu installieren, sofern noch nicht erfolgt.</span><span class="sxs-lookup"><span data-stu-id="1fb79-117">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="1fb79-118">OpenXR-Unterstützung ist im **Foundation-Paket** enthalten.</span><span class="sxs-lookup"><span data-stu-id="1fb79-118">OpenXR support is in the **Foundation** package.</span></span>

<span data-ttu-id="1fb79-119">[Ausführlichere Informationen zur Migration zu OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="1fb79-119">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="1fb79-120">Stellen Sie beim Upgrade von einer früheren Version von MRTK vor **2.5.3** sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:</span><span class="sxs-lookup"><span data-stu-id="1fb79-120">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="1fb79-121">Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer gestartet haben.</span><span class="sxs-lookup"><span data-stu-id="1fb79-121">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="1fb79-122">Manuelle Einrichtung ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="1fb79-122">Manual setup without MRTK</span></span>

<span data-ttu-id="1fb79-123">Während Microsoft und die Community OpenSource-Tools wie das [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) erstellt haben, mit denen die WMR-Umgebung automatisch eingerichtet wird, möchten viele Entwickler ihre Erfahrungen von Grund auf erstellen.</span><span class="sxs-lookup"><span data-stu-id="1fb79-123">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]
