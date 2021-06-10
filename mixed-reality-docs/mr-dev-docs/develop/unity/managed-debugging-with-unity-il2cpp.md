---
title: Verwaltetes Debuggen mit Unity
description: In diesem Artikel wird beschrieben, wie Sie einen verwalteten Debugger in Ihrem Unity IL2CPP-UWP-Projekt ausführen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, Debuggen, il2cpp, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP
ms.openlocfilehash: 8e3967971220fa453f4e60639bd08f2554a8dd7e
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547079"
---
# <a name="managed-debugging-with-unity"></a><span data-ttu-id="dbcca-104">Verwaltetes Debuggen mit Unity</span><span class="sxs-lookup"><span data-stu-id="dbcca-104">Managed debugging with Unity</span></span>

<span data-ttu-id="dbcca-105">Führen Sie die folgenden Schritte aus, um einen verwalteten Debugger an Ihren Unity IL2CPP-UWP-Build für HoloLens HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="dbcca-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="dbcca-106">Sie müssen sich in einem Netzwerk mit [Multicast unterstützen.](https://en.wikipedia.org/wiki/Multicast)</span><span class="sxs-lookup"><span data-stu-id="dbcca-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="dbcca-107">Wechseln Sie zu **UWP Publishing Settings Capabilities (Funktionen für UWP-Veröffentlichungseinstellungen),** und aktivieren Sie **InternetClientServer** und **PrivateNetworkClientServer:**</span><span class="sxs-lookup"><span data-stu-id="dbcca-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![Funktionen für UWP-Veröffentlichungseinstellungen](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="dbcca-109">Konfigurieren Sie die Unity-UWP-Buildeinstellungen:</span><span class="sxs-lookup"><span data-stu-id="dbcca-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="dbcca-110">Development Build</span><span class="sxs-lookup"><span data-stu-id="dbcca-110">Development Build</span></span>
    - <span data-ttu-id="dbcca-111">Skriptdebugging</span><span class="sxs-lookup"><span data-stu-id="dbcca-111">Script Debugging</span></span>
    - <span data-ttu-id="dbcca-112">Warten auf verwalteten Debugger (optional)</span><span class="sxs-lookup"><span data-stu-id="dbcca-112">Wait for Managed Debugger (optional)</span></span>

    ![UWP-Buildeinstellungen](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="dbcca-114">Erstellen Sie in Unity.</span><span class="sxs-lookup"><span data-stu-id="dbcca-114">Build in Unity.</span></span>
5. <span data-ttu-id="dbcca-115">Erstellen Und bereitstellen Sie über die Visual Studio Lösung auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="dbcca-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="dbcca-116">Sie sollten mit den Debug- **oder** **Releasekonfigurationen** erstellen.</span><span class="sxs-lookup"><span data-stu-id="dbcca-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="dbcca-117">Die **Masterkonfiguration** deaktiviert den Unity-Profiler und kann ein optimales Debuggen verhindern.</span><span class="sxs-lookup"><span data-stu-id="dbcca-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="dbcca-118">Überprüfen Sie optional **internet (Client & Server)** und **private Netzwerke (Client & Server)** in der Liste der Funktionen in Package.appxmanifest in der Lösung.</span><span class="sxs-lookup"><span data-stu-id="dbcca-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="dbcca-119">Stellen Sie sicher, dass Ihr Gerät mit demselben Netzwerk wie Ihr PC verbunden ist, und starten Sie die App auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="dbcca-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="dbcca-120">Stellen Sie sicher, dass **das Gerät nicht** über USB mit Ihrem PC verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="dbcca-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="dbcca-121">Doppelklicken Sie auf eines Ihrer Skripts in Unity, und wechseln Sie zur Visual Studio, die zum Anzeigen und Bearbeiten geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="dbcca-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="dbcca-122">Debuggen – > Unity-Debugger anfügen.</span><span class="sxs-lookup"><span data-stu-id="dbcca-122">Debug -> Attach Unity Debugger.</span></span>

    ![Unity-Debugger anhängen](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="dbcca-124">Wählen Sie Ihr Gerät in der Liste aus, und klicken Sie zum Anfügen auf "OK".</span><span class="sxs-lookup"><span data-stu-id="dbcca-124">Select your device in the list and click "OK" to attach.</span></span>

    ![Geräteliste](images/il2cpp-debugging-machines.png)
