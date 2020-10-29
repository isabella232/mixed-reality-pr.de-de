---
title: Verwaltetes Debuggen mit Unity IL2CPP
description: In diesem Artikel wird beschrieben, wie Sie einen verwalteten Debugger in Ihrem Unity IL2CPP-UWP-Projekt ausführen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, Debugging, il2cpp
ms.openlocfilehash: 970d3000df995e7c6e331a41d10e25dc5aa370a8
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684619"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="341c3-104">Verwaltetes Debuggen mit Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="341c3-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="341c3-105">Führen Sie die folgenden Schritte aus, um einen verwalteten Debugger an Ihren Unity IL2CPP UWP-Build anzufügen.</span><span class="sxs-lookup"><span data-stu-id="341c3-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="341c3-106">Dieses Handbuch wurde ursprünglich für hololens und hololens 2 entwickelt.</span><span class="sxs-lookup"><span data-stu-id="341c3-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="341c3-107">Sie müssen sich in einem Netzwerk befinden, das [Multicast](https://en.wikipedia.org/wiki/Multicast)unterstützt.</span><span class="sxs-lookup"><span data-stu-id="341c3-107">You will need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
1. <span data-ttu-id="341c3-108">Stellen Sie sicher, dass **internetclientserver** und **privatenetworkclientserver** in Unity unter den Funktionen der UWP-Veröffentlichungs Einstellungen eingeglichen werden.</span><span class="sxs-lookup"><span data-stu-id="341c3-108">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![Funktionen der UWP-Veröffentlichungs Einstellungen](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="341c3-110">Konfigurieren Sie die Unity-UWP-Buildeinstellungen:</span><span class="sxs-lookup"><span data-stu-id="341c3-110">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="341c3-111">Development Build</span><span class="sxs-lookup"><span data-stu-id="341c3-111">Development Build</span></span>
    - <span data-ttu-id="341c3-112">Skriptdebugging</span><span class="sxs-lookup"><span data-stu-id="341c3-112">Script Debugging</span></span>
    - <span data-ttu-id="341c3-113">Auf verwalteten Debugger warten (optional)</span><span class="sxs-lookup"><span data-stu-id="341c3-113">Wait for Managed Debugger (optional)</span></span>

    ![UWP-Buildeinstellungen](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="341c3-115">Erstellen Sie in Unity.</span><span class="sxs-lookup"><span data-stu-id="341c3-115">Build in Unity.</span></span>
1. <span data-ttu-id="341c3-116">Erstellen Sie die Visual Studio-Projekt Mappe, und stellen Sie Sie auf Ihrem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="341c3-116">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="341c3-117">Sie sollten mit den **Debug** -oder **Releasekonfigurationen** erstellen.</span><span class="sxs-lookup"><span data-stu-id="341c3-117">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="341c3-118">Die **Master** Konfiguration deaktiviert den Unity-Profiler und kann ein optimales Debuggen verhindern.</span><span class="sxs-lookup"><span data-stu-id="341c3-118">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="341c3-119">Überprüfen Sie optional das **Internet (Client & Server)** und **private Netzwerke (Client & Server)** in der Liste der Funktionen in "Package. appxmanifest" in der Projekt Mappe.</span><span class="sxs-lookup"><span data-stu-id="341c3-119">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="341c3-120">Starten Sie die APP auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="341c3-120">Start the app on your device.</span></span> <span data-ttu-id="341c3-121">Stellen Sie sicher, dass das Gerät mit dem Netzwerk verbunden ist, das mit dem PC verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="341c3-121">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="341c3-122">Stellen Sie sicher, dass das Gerät nicht über USB mit dem PC verbunden **ist** .</span><span class="sxs-lookup"><span data-stu-id="341c3-122">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="341c3-123">Wechseln Sie zur Visual Studio-Projekt Mappe, die erstellt wird, wenn Sie auf ein Skript in Unity doppelklicken, in dem Sie die c#-Skripts anzeigen und bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="341c3-123">Go to the Visual Studio solution that's created when you double-click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="341c3-124">Debug-> Unity-Debugger anfügen.</span><span class="sxs-lookup"><span data-stu-id="341c3-124">Debug -> Attach Unity Debugger.</span></span>

    ![Unity-Debugger anhängen](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="341c3-126">Wählen Sie in der Liste Ihr Gerät aus, und klicken Sie auf "OK"</span><span class="sxs-lookup"><span data-stu-id="341c3-126">Select your device in the list and click "OK" to attach.</span></span>

    ![Geräteliste](images/il2cpp-debugging-machines.png)
