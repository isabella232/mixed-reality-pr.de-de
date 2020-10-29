---
title: Bereitstellen auf Gerät in Unreal
description: Leitfaden für die Bereitstellung auf dem Gerät in Unreal für hololens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Mixed Reality, Bereitstellung auf Gerät, PC, Dokumentation
appliesto:
- HoloLens 2
ms.openlocfilehash: abd5e5c28ec5e66c4f73df8edf5e0ac0212d170a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684790"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="a1802-104">Bereitstellen auf Gerät in Unreal</span><span class="sxs-lookup"><span data-stu-id="a1802-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="a1802-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="a1802-105">Overview</span></span>
<span data-ttu-id="a1802-106">Es gibt zwei Möglichkeiten, eine Unreal-Anwendung auf hololens 2 bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="a1802-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="a1802-107">Direkt aus dem Unreal-Editor</span><span class="sxs-lookup"><span data-stu-id="a1802-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="a1802-108">Als Paket, das über das Geräte Portal hochgeladen wird</span><span class="sxs-lookup"><span data-stu-id="a1802-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="a1802-109">Für beide Optionen müssen Sie die hololens einrichten, damit das [Geräte Portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) für die Entwicklung verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="a1802-109">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="a1802-110">Bereitstellen auf einem Gerät über den Unreal-Editor</span><span class="sxs-lookup"><span data-stu-id="a1802-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="a1802-111">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche **starten** .</span><span class="sxs-lookup"><span data-stu-id="a1802-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="a1802-112">Anfänglich ist die hololens-Geräte Option ausgegraut.</span><span class="sxs-lookup"><span data-stu-id="a1802-112">Initially, the HoloLens device option will be grayed out.</span></span>

![Startmenü Optionen](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="a1802-114">Öffnen Sie die **Geräte-Manager** .</span><span class="sxs-lookup"><span data-stu-id="a1802-114">Open the **Device Manager** .</span></span> <span data-ttu-id="a1802-115">Beachten Sie, dass Ihre hololens nicht automatisch in der Geräteliste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a1802-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="a1802-116">Erweitern Sie den Abschnitt **nicht aufgelisteten Gerät hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="a1802-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="a1802-117">Wählen Sie **hololens** als **Plattform** aus.</span><span class="sxs-lookup"><span data-stu-id="a1802-117">Select **HoloLens** as your **Platform** .</span></span>

5. <span data-ttu-id="a1802-118">Geben Sie die IP-Adresse und die Port Informationen Ihrer Geräte als Geräte Bezeichner getrennt durch einen Doppelpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="a1802-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="a1802-119">Beispiel: "127.0.0.1:10080" (bei Verbindung über USB).</span><span class="sxs-lookup"><span data-stu-id="a1802-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="a1802-120">Verwenden Sie die Anmelde Informationen für den Benutzernamen Ihres Geräte Portals.</span><span class="sxs-lookup"><span data-stu-id="a1802-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="a1802-121">Schließen **Sie** den Geräte-Manager, und schließen Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="a1802-121">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="a1802-122">Im Falle eines Fehlers (z. b. falsche Adresse, Benutzername oder Kennwort) wird eine Meldung in das Ausgabeprotokoll ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="a1802-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![Hinzufügen eines nicht aufgelisteten Geräts](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="a1802-124">Klicken Sie erneut auf den Dropdown Pfeil neben der Schaltfläche " **Start** ". dieses Mal sollte das von Ihnen soeben hinzugefügte hololens-Gerät angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a1802-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="a1802-125">Wählen Sie das hololens-Gerät zum Erstellen und Bereitstellen Ihrer hololens aus.</span><span class="sxs-lookup"><span data-stu-id="a1802-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="a1802-126">Das Erstellen für das Gerät erfordert möglicherweise die Neukompilierung von Shadern (insbesondere bei der ersten Ausführung). Dies kann einige Zeit in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="a1802-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="a1802-127">Lassen Sie das Gerät erst wieder in den Standbymodus wechseln, wenn die app ausgeführt wird (möglicherweise müssen Sie es verwenden).</span><span class="sxs-lookup"><span data-stu-id="a1802-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="a1802-128">Andernfalls tritt bei der shaderkompilierung ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="a1802-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="a1802-129">Bereitstellen auf einem Gerät über das Geräte Portal</span><span class="sxs-lookup"><span data-stu-id="a1802-129">Deploying to device via device portal</span></span>

<span data-ttu-id="a1802-130">Ausführliche Anweisungen zum [Verpacken und Bereitstellen einer APP](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) finden Sie im letzten Abschnitt der Reihe "Getting Started with Unreal Tutorial".</span><span class="sxs-lookup"><span data-stu-id="a1802-130">You can find detailed instructions on [packaging and deploying an app](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="a1802-131">Nächster Entwicklungs Prüfpunkt</span><span class="sxs-lookup"><span data-stu-id="a1802-131">Next Development Checkpoint</span></span>

<span data-ttu-id="a1802-132">Wenn Sie die unechte Development Checkpoint Journey befolgen, befinden wir uns in der Mitte der Bereitstellungs Phase.</span><span class="sxs-lookup"><span data-stu-id="a1802-132">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="a1802-133">Von hier aus können Sie mit dem Hinzufügen erweiterter Dienste fortfahren:</span><span class="sxs-lookup"><span data-stu-id="a1802-133">From here, you can proceed to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a1802-134">Erweiterte Dienste</span><span class="sxs-lookup"><span data-stu-id="a1802-134">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="a1802-135">Sie können jederzeit jederzeit zu den [unechten Entwicklungs Prüfpunkten](unreal-development-overview.md#4-deploying-to-a-device) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a1802-135">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-deploying-to-a-device) at any time.</span></span>
