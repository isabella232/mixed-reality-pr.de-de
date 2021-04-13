---
title: Übersicht zum Portieren
description: Eine Übersicht über die verschiedenen Portierungs Optionen, um Ihre vorhandenen Anwendungen in die gemischte Realität für hololens und VR zu bringen.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: portieren, Unity, Middleware, Engine, UWP, Win32
ms.openlocfilehash: 5b89d3448a7baf12cc76dd3677140fcf6e297ee2
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299785"
---
# <a name="porting-overview"></a><span data-ttu-id="bb132-104">Übersicht zum Portieren</span><span class="sxs-lookup"><span data-stu-id="bb132-104">Porting overview</span></span>

<span data-ttu-id="bb132-105">Wenn Sie Ihre vorhandenen Projekte für gemischte Realität portieren oder aktualisieren, hängt ihre Portierung davon ab, ob Ihre APP mit Unity oder Unreal Engine erstellt wurde, und zielt auf hololens (1st Gen) oder hololens 2 oder steamvr ab.</span><span class="sxs-lookup"><span data-stu-id="bb132-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="bb132-106">Diese Übersichtsseite enthält unsere aktuellen Empfehlungen für jede Plattform und jedes Gerät. Stellen Sie sicher, dass Sie den Vorgang erneut durchlaufen, da sich diese Prozesse immer ändern.</span><span class="sxs-lookup"><span data-stu-id="bb132-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="bb132-107">Richten Sie zuerst das Projektziel basierend auf unseren [Unity](#unity) -und [Unreal](#unreal) -Empfehlungen ein, und folgen Sie dann einem oder mehreren unserer Portierungs Szenarien:</span><span class="sxs-lookup"><span data-stu-id="bb132-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="bb132-108">Hololens (1. Gen) bis hololens 2</span><span class="sxs-lookup"><span data-stu-id="bb132-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="bb132-109">Windows Mixed Reality-Headsets</span><span class="sxs-lookup"><span data-stu-id="bb132-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="bb132-110">Steamvr-apps</span><span class="sxs-lookup"><span data-stu-id="bb132-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="bb132-111">2D UWP-apps</span><span class="sxs-lookup"><span data-stu-id="bb132-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="bb132-112">Empfohlene Projektziele</span><span class="sxs-lookup"><span data-stu-id="bb132-112">Recommended project targets</span></span>

<span data-ttu-id="bb132-113">Es ist wichtig, Ihre Projekte auf dem neuesten Stand zu halten, unabhängig davon, ob Sie eine APP auf ein anderes Zielgerät portieren.</span><span class="sxs-lookup"><span data-stu-id="bb132-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="bb132-114">Unsere aktuellen Empfehlungen finden Sie in den unten aufgeführten Engine-basierten Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="bb132-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="bb132-115">Unity</span><span class="sxs-lookup"><span data-stu-id="bb132-115">Unity</span></span>

<span data-ttu-id="bb132-116">Unsere aktuelle Empfehlung für die Unity-Entwicklung mit gemischter Realität ist **Unity 2019 LTS mit dem alten XR-Paket**.</span><span class="sxs-lookup"><span data-stu-id="bb132-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="bb132-117">Wenn Ihr Projekt das Mixed Reality Toolkit verwendet, überprüfen Sie, ob Sie die neueste Version verwenden, die zurzeit **mrtk-Unity 2,5** ist.</span><span class="sxs-lookup"><span data-stu-id="bb132-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="bb132-118">Obwohl das XR SDK mit dieser Version von Unity verfügbar ist, ist Azure Spatial Anchor zurzeit mit diesem Setup nicht kompatibel.</span><span class="sxs-lookup"><span data-stu-id="bb132-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="bb132-119">Diese Empfehlung wird mit einer zukünftigen Version des Azure Spatial Anchor-Pakets für Unity aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="bb132-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span>
> 
> * <span data-ttu-id="bb132-120">Wenn Sie keine räumlichen Azure-Anker benötigen, können Sie [Ihr Unity-Projekt für XR konfigurieren und die](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) ersten Schritte [mit dem mrtk-und XR SDK durchsetzen](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span><span class="sxs-lookup"><span data-stu-id="bb132-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span></span>
> 
> * <span data-ttu-id="bb132-121">Wenn Sie zurzeit das XR SDK in Ihrem Projekt verwenden und Azure Spatial Anchor verwenden möchten, deinstallieren Sie das SDK SDK, und installieren Sie das Legacy-XR-Paket erneut, um Ihre Projekteinstellungen wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="bb132-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>

### <a name="unreal"></a><span data-ttu-id="bb132-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="bb132-122">Unreal</span></span>

<span data-ttu-id="bb132-123">Unsere aktuelle Empfehlung für die Unreal-Entwicklung mit gemischter Realität ist **Unreal Engine 4,26**.</span><span class="sxs-lookup"><span data-stu-id="bb132-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="bb132-124">Wenn Ihr Projekt die Mixed Reality Toolkit-UX-Tools verwendet, stellen Sie sicher, dass Sie die neueste Version verwenden, die derzeit **UXT 0,10** ist.</span><span class="sxs-lookup"><span data-stu-id="bb132-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="bb132-125">Portieren von Szenarien</span><span class="sxs-lookup"><span data-stu-id="bb132-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="bb132-126">Hololens (1. Gen) Unity-apps auf hololens 2</span><span class="sxs-lookup"><span data-stu-id="bb132-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="bb132-127">Wenn Sie über eine vorhandene Unity-Anwendung hololens (1st Gen) verfügen, die Sie auf einen hololens 2 portieren möchten, befolgen Sie die Anweisungen in unserem [Artikel zum Portieren von hololens](./porting-hl1-hl2.md).</span><span class="sxs-lookup"><span data-stu-id="bb132-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="bb132-128">Windows Mixed Reality-Headsets</span><span class="sxs-lookup"><span data-stu-id="bb132-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="bb132-129">Wenn Sie Inhalte für andere Geräte (z. b. den Oculus-oder HP-Reverb) erstellt haben, müssen Sie herstellerspezifische VR-SDBs und möglicherweise APIs für die Eingabe Zuordnung neu zuweisen.</span><span class="sxs-lookup"><span data-stu-id="bb132-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="bb132-130">Informationen zu Unity-und Unreal-Portierungs Szenarien finden Sie in unserem [Leitfaden zum Portieren von immersiven apps](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="bb132-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="bb132-131">Steamvr-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="bb132-131">SteamVR applications</span></span>

<span data-ttu-id="bb132-132">Informationen zu den von Ihnen für Windows Mixed Reality-Headsets zu aktualisierenden Funktionen von steamvr finden Sie in unserem [Handbuch zum Aktualisieren von steamvr](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="bb132-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="bb132-133">2D universelle Windows-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="bb132-133">2D Universal Windows applications</span></span>

<span data-ttu-id="bb132-134">Wenn Sie über eine vorhandene 2D-UWP-App verfügen, die Sie entweder in ein Windows Mixed Reality-immersives Headset oder hololens portieren möchten, befolgen Sie die Anweisungen unter [Portieren von 2D-UWP-Apps für Windows Mixed Reality](building-2d-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="bb132-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>