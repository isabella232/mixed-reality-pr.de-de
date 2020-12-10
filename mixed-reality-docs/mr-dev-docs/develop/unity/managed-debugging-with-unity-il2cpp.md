---
title: Verwaltetes Debuggen mit Unity IL2CPP
description: In diesem Artikel wird beschrieben, wie Sie einen verwalteten Debugger in Ihrem Unity IL2CPP-UWP-Projekt ausführen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, Debugging, il2cpp, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010241"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="4944e-104">Verwaltetes Debuggen mit Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="4944e-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="4944e-105">Führen Sie die folgenden Schritte aus, um einen verwalteten Debugger an Ihren Unity IL2CPP UWP-Build für hololens und hololens 2 anzufügen.</span><span class="sxs-lookup"><span data-stu-id="4944e-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="4944e-106">Sie müssen sich in einem Netzwerk befinden, das [Multicast](https://en.wikipedia.org/wiki/Multicast)unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4944e-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="4944e-107">Wechseln Sie zu den Funktionen für die **UWP-Veröffentlichungs Einstellungen** , und überprüfen Sie **internetclientserver** und **privatenetworkclientserver**:</span><span class="sxs-lookup"><span data-stu-id="4944e-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Funktionen der UWP-Veröffentlichungs Einstellungen](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="4944e-109">Konfigurieren Sie die Unity-UWP-Buildeinstellungen:</span><span class="sxs-lookup"><span data-stu-id="4944e-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="4944e-110">Development Build</span><span class="sxs-lookup"><span data-stu-id="4944e-110">Development Build</span></span>
    - <span data-ttu-id="4944e-111">Skriptdebugging</span><span class="sxs-lookup"><span data-stu-id="4944e-111">Script Debugging</span></span>
    - <span data-ttu-id="4944e-112">Auf verwalteten Debugger warten (optional)</span><span class="sxs-lookup"><span data-stu-id="4944e-112">Wait for Managed Debugger (optional)</span></span>

    ![UWP-Buildeinstellungen](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="4944e-114">Erstellen Sie in Unity.</span><span class="sxs-lookup"><span data-stu-id="4944e-114">Build in Unity.</span></span>
5. <span data-ttu-id="4944e-115">Erstellen Sie die Visual Studio-Projekt Mappe, und stellen Sie Sie auf Ihrem Gerät bereit.</span><span class="sxs-lookup"><span data-stu-id="4944e-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="4944e-116">Sie sollten mit den **Debug** -oder **Releasekonfigurationen** erstellen.</span><span class="sxs-lookup"><span data-stu-id="4944e-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="4944e-117">Die **Master** Konfiguration deaktiviert den Unity-Profiler und kann ein optimales Debuggen verhindern.</span><span class="sxs-lookup"><span data-stu-id="4944e-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="4944e-118">Überprüfen Sie optional das **Internet (Client & Server)** und **private Netzwerke (Client & Server)** in der Liste der Funktionen in "Package. appxmanifest" in der Projekt Mappe.</span><span class="sxs-lookup"><span data-stu-id="4944e-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="4944e-119">Stellen Sie sicher, dass Ihr Gerät mit dem gleichen Netzwerk wie Ihr PC verbunden ist, und starten Sie die APP auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="4944e-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="4944e-120">Stellen Sie sicher, dass das Gerät nicht über USB mit dem PC verbunden **ist** .</span><span class="sxs-lookup"><span data-stu-id="4944e-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="4944e-121">Doppelklicken Sie auf eines Ihrer Skripts in Unity, und wechseln Sie zur Visual Studio-Projekt Mappe, die geöffnet wird, um Sie anzuzeigen und zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="4944e-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="4944e-122">Debug-> Unity-Debugger anfügen.</span><span class="sxs-lookup"><span data-stu-id="4944e-122">Debug -> Attach Unity Debugger.</span></span>

    ![Unity-Debugger anhängen](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="4944e-124">Wählen Sie in der Liste Ihr Gerät aus, und klicken Sie auf "OK"</span><span class="sxs-lookup"><span data-stu-id="4944e-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Geräteliste](images/il2cpp-debugging-machines.png)
