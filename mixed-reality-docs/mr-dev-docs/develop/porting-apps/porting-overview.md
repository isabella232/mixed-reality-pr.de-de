---
title: Übersicht zum Portieren
description: Eine Übersicht über die verschiedenen Portierungsoptionen zum Bringen Ihrer vorhandenen Anwendungen in Mixed Reality für HoloLens und VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Portieren, Unity, Middleware, Engine, UWP, Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042271"
---
# <a name="porting-overview"></a><span data-ttu-id="8ef30-104">Übersicht zum Portieren</span><span class="sxs-lookup"><span data-stu-id="8ef30-104">Porting overview</span></span>

<span data-ttu-id="8ef30-105">Wenn es um das Portieren oder Aktualisieren Ihrer vorhandenen Projekte für Mixed Reality geht, hängt Ihre Portierungs journey davon ab, ob Ihre App mit Unity oder Unreal Engine erstellt wurde und HoloLens (1. Generation) oder HoloLens 2 oder SteamVR als Ziel hat.</span><span class="sxs-lookup"><span data-stu-id="8ef30-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="8ef30-106">Diese Übersichtsseite enthält unsere aktuellen Empfehlungen für jede Plattform und jedes Gerät. Achten Sie darauf, sich zu vergewissern, dass sich diese Prozesse immer ändern.</span><span class="sxs-lookup"><span data-stu-id="8ef30-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="8ef30-107">Richten Sie zunächst Ihr Projektziel basierend auf unseren [Unity-](#unity) und [Unreal-Empfehlungen](#unreal) ein, und folgen Sie dann mindestens einem unserer Portierungsszenarien:</span><span class="sxs-lookup"><span data-stu-id="8ef30-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="8ef30-108">HoloLens (1. Generation) zum HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8ef30-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="8ef30-109">Immersive Headsets (VR)</span><span class="sxs-lookup"><span data-stu-id="8ef30-109">Immersive VR headsets</span></span>](#immersive-vr-headsets)
- [<span data-ttu-id="8ef30-110">2D-UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="8ef30-110">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="8ef30-111">Empfohlene Projektziele</span><span class="sxs-lookup"><span data-stu-id="8ef30-111">Recommended project targets</span></span>

<span data-ttu-id="8ef30-112">Es ist wichtig, ihre Projekte auf dem neuesten Stand zu halten, unabhängig davon, ob Sie eine App auf ein anderes Zielgerät portieren.</span><span class="sxs-lookup"><span data-stu-id="8ef30-112">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="8ef30-113">Unsere aktuellen Empfehlungen finden Sie in den unten aufgeführten enginebasierten Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="8ef30-113">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="8ef30-114">Unity</span><span class="sxs-lookup"><span data-stu-id="8ef30-114">Unity</span></span>

<span data-ttu-id="8ef30-115">Aktuelle Anleitungen zu den empfohlenen Unity- und MRTK-Versionen finden Sie auf der Seite [Auswählen einer Unity-Version.](../unity/choosing-unity-version.md)</span><span class="sxs-lookup"><span data-stu-id="8ef30-115">See the [Choosing a Unity version](../unity/choosing-unity-version.md) page for up-to-date guidance on the recommended Unity and MRTK versions.</span></span>

### <a name="unreal"></a><span data-ttu-id="8ef30-116">Unreal</span><span class="sxs-lookup"><span data-stu-id="8ef30-116">Unreal</span></span>

<span data-ttu-id="8ef30-117">Aktuelle Anleitungen zu den empfohlenen Unreal- und MRTK-Versionen finden Sie auf der Seite [Einrichten Ihres Unreal-Projekts.](../unreal/unreal-project-setup.md)</span><span class="sxs-lookup"><span data-stu-id="8ef30-117">See the [Setting up your Unreal project](../unreal/unreal-project-setup.md) page for up-to-date guidance on the recommended Unreal and MRTK versions.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="8ef30-118">Portierungsszenarien</span><span class="sxs-lookup"><span data-stu-id="8ef30-118">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="8ef30-119">Unity-Apps für HoloLens (1. Generation) HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8ef30-119">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="8ef30-120">Wenn Sie über eine vorhandene HoloLens-Unity-Anwendung (1. Generation) verfügen, die Sie zu einem HoloLens 2 portieren möchten, befolgen Sie die Anweisungen in unserem [HoloLens-Portierungsartikel.](./porting-hl1-hl2.md)</span><span class="sxs-lookup"><span data-stu-id="8ef30-120">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="immersive-vr-headsets"></a><span data-ttu-id="8ef30-121">Immersive Headsets (VR)</span><span class="sxs-lookup"><span data-stu-id="8ef30-121">Immersive VR headsets</span></span>

<span data-ttu-id="8ef30-122">Wenn Sie Inhalte für andere VR-Geräte erstellt haben, müssen Sie alle anbieterspezifischen VR SDKs und potenziell Eingabezuordnungs-APIs neu auszuweisen.</span><span class="sxs-lookup"><span data-stu-id="8ef30-122">If you've built content for other VR devices, you'll need to retarget any vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="8ef30-123">Informationen zu Unity- und Unreal-Portierungsszenarien finden Sie in unserem Leitfaden zum [Portieren immersiver Apps.](porting-guides.md)</span><span class="sxs-lookup"><span data-stu-id="8ef30-123">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

<span data-ttu-id="8ef30-124">Informationen zu den SteamVR-Funktionen, die Sie für Windows Mixed Reality Headsets aktualisieren möchten, finden Sie in unserem Leitfaden zur Aktualisierung von [SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)</span><span class="sxs-lookup"><span data-stu-id="8ef30-124">For SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="8ef30-125">Universelle 2D-Windows-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="8ef30-125">2D Universal Windows applications</span></span>

<span data-ttu-id="8ef30-126">Wenn Sie über eine vorhandene 2D-UWP-App verfügen, die Sie entweder zu einem Windows Mixed Reality immersiven Headset oder HoloLens portieren möchten, befolgen Sie unsere Anweisungen zum Portieren von [2D-UWP-Apps für Windows Mixed Reality](building-2d-apps.md) Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="8ef30-126">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>