---
title: Übersicht zum Portieren
description: Eine Übersicht über die verschiedenen Portierungsoptionen zum Bringen Ihrer vorhandenen Anwendungen in Mixed Reality für HoloLens und VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Portieren, Unity, Middleware, Engine, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600499"
---
# <a name="porting-overview"></a><span data-ttu-id="cd500-104">Übersicht zum Portieren</span><span class="sxs-lookup"><span data-stu-id="cd500-104">Porting overview</span></span>

<span data-ttu-id="cd500-105">Wenn es um das Portieren oder Aktualisieren Ihrer vorhandenen Projekte für Mixed Reality geht, hängt Ihre Portierungs journey davon ab, ob Ihre App mit Unity oder Unreal Engine erstellt wurde und HoloLens (1. Generation) oder HoloLens 2 oder SteamVR als Ziel hat.</span><span class="sxs-lookup"><span data-stu-id="cd500-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="cd500-106">Diese Übersichtsseite enthält unsere aktuellen Empfehlungen für jede Plattform und jedes Gerät. Achten Sie darauf, sich zu vergewissern, dass sich diese Prozesse immer ändern.</span><span class="sxs-lookup"><span data-stu-id="cd500-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="cd500-107">Richten Sie zunächst Ihr Projektziel basierend auf unseren [Unity-](#unity) und [Unreal-Empfehlungen](#unreal) ein, und folgen Sie dann mindestens einem unserer Portierungsszenarien:</span><span class="sxs-lookup"><span data-stu-id="cd500-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="cd500-108">HoloLens (1. Generation) zum HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cd500-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="cd500-109">Windows Mixed Reality-Headsets</span><span class="sxs-lookup"><span data-stu-id="cd500-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="cd500-110">SteamVR-Apps</span><span class="sxs-lookup"><span data-stu-id="cd500-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="cd500-111">2D-UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="cd500-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="cd500-112">Empfohlene Projektziele</span><span class="sxs-lookup"><span data-stu-id="cd500-112">Recommended project targets</span></span>

<span data-ttu-id="cd500-113">Es ist wichtig, ihre Projekte auf dem neuesten Stand zu halten, unabhängig davon, ob Sie eine App auf ein anderes Zielgerät portieren.</span><span class="sxs-lookup"><span data-stu-id="cd500-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="cd500-114">Unsere aktuellen Empfehlungen finden Sie in den unten aufgeführten enginebasierten Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="cd500-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="cd500-115">Unity</span><span class="sxs-lookup"><span data-stu-id="cd500-115">Unity</span></span>

<span data-ttu-id="cd500-116">Unsere aktuelle Empfehlung für die Unity-Entwicklung mit Mixed Reality ist **Unity 2019 LTS unter Verwendung des Legacy-XR-Pakets.**</span><span class="sxs-lookup"><span data-stu-id="cd500-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="cd500-117">Wenn Ihr Projekt das Mixed Reality Toolkit verwendet, überprüfen Sie, ob Sie die neueste Version verwenden, die derzeit **MRTK-Unity 2.5** ist.</span><span class="sxs-lookup"><span data-stu-id="cd500-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="cd500-118">Während das XR SDK mit dieser Version von Unity verfügbar ist, ist Azure Spatial Anchors derzeit nicht mit diesem Setup kompatibel.</span><span class="sxs-lookup"><span data-stu-id="cd500-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="cd500-119">Diese Empfehlung wird mit einer zukünftigen Version des Azure Spatial Anchors-Pakets für Unity aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="cd500-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span>
> 
> * <span data-ttu-id="cd500-120">Wenn Sie Azure Spatial Anchors nicht benötigen, können Sie [Ihr Unity-Projekt für XR konfigurieren](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) und [mit MRTK und dem XR SDK beginnen.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)</span><span class="sxs-lookup"><span data-stu-id="cd500-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span></span>
> 
> * <span data-ttu-id="cd500-121">Wenn Sie derzeit das XR SDK in Ihrem Projekt verwenden und Azure Spatial Anchors verwenden möchten, deinstallieren Sie das XR SDK, und installieren Sie das Legacy-XR-Paket neu, um Ihre Projekteinstellungen wie zu ändern.</span><span class="sxs-lookup"><span data-stu-id="cd500-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>

### <a name="unreal"></a><span data-ttu-id="cd500-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="cd500-122">Unreal</span></span>

<span data-ttu-id="cd500-123">Unsere aktuelle Empfehlung für die Unreal-Entwicklung mit Mixed Reality ist **Unreal Engine 4.26**.</span><span class="sxs-lookup"><span data-stu-id="cd500-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="cd500-124">Wenn Ihr Projekt die Mixed Reality Toolkit UX Tools verwendet, stellen Sie sicher, dass Sie die neueste Version verwenden, die derzeit **UXT 0.10** ist.</span><span class="sxs-lookup"><span data-stu-id="cd500-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="cd500-125">Portierungsszenarien</span><span class="sxs-lookup"><span data-stu-id="cd500-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="cd500-126">Unity-Apps für HoloLens (1. Generation) HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cd500-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="cd500-127">Wenn Sie über eine vorhandene HoloLens-Unity-Anwendung (1. Generation) verfügen, die Sie zu einem HoloLens 2 portieren möchten, befolgen Sie die Anweisungen in unserem [HoloLens-Portierungsartikel.](./porting-hl1-hl2.md)</span><span class="sxs-lookup"><span data-stu-id="cd500-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="cd500-128">Windows Mixed Reality-Headsets</span><span class="sxs-lookup"><span data-stu-id="cd500-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="cd500-129">Wenn Sie Inhalte für andere Geräte erstellt haben, z. B. Oculus Rift oder HP Reverb G2, müssen Sie anbieterspezifische VR SDKs und potenziell Eingabezuordnungs-APIs neu auszuweisen.</span><span class="sxs-lookup"><span data-stu-id="cd500-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="cd500-130">Informationen zu Unity- und Unreal-Portierungsszenarien finden Sie in unserem Leitfaden zum [Portieren immersiver Apps.](porting-guides.md)</span><span class="sxs-lookup"><span data-stu-id="cd500-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="cd500-131">SteamVR-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="cd500-131">SteamVR applications</span></span>

<span data-ttu-id="cd500-132">Informationen zu allen SteamVR-Funktionen, die Sie für Windows Mixed Reality Headsets aktualisieren möchten, finden Sie in unserem Leitfaden zur Aktualisierung von [SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)</span><span class="sxs-lookup"><span data-stu-id="cd500-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="cd500-133">Universelle 2D-Windows-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="cd500-133">2D Universal Windows applications</span></span>

<span data-ttu-id="cd500-134">Wenn Sie über eine vorhandene 2D-UWP-App verfügen, die Sie entweder zu einem Windows Mixed Reality immersiven Headset oder HoloLens portieren möchten, befolgen Sie unsere Anweisungen [zum Portieren von 2D-UWP-Apps für Windows Mixed Reality](building-2d-apps.md) Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="cd500-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>