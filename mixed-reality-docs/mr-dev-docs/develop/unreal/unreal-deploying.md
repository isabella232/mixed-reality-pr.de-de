---
title: Bereitstellen auf Gerät in Unreal
description: Erfahren Sie alles, was Sie über die Bereitstellung Ihrer Mixed Reality-Unreal-Apps für hololens 2 mithilfe des Editors oder Geräte Portals wissen müssen.
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Mixed Reality, bereitstellen auf Geräten, PCs, Dokumentationen, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
appliesto:
- HoloLens 2
ms.openlocfilehash: 24b2c013e1c9f25f54be9a6fefec8a86846c1746
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009750"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="4cd67-104">Bereitstellen auf Gerät in Unreal</span><span class="sxs-lookup"><span data-stu-id="4cd67-104">Deploy to device in Unreal</span></span>

<span data-ttu-id="4cd67-105">Es gibt zwei Möglichkeiten, eine Unreal-Anwendung auf hololens 2 bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="4cd67-105">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="4cd67-106">Direkt aus dem Unreal-Editor</span><span class="sxs-lookup"><span data-stu-id="4cd67-106">Directly from the Unreal editor</span></span>
* <span data-ttu-id="4cd67-107">Als Paket, das über das Geräte Portal hochgeladen wird</span><span class="sxs-lookup"><span data-stu-id="4cd67-107">As a package uploaded via the device portal</span></span>

<span data-ttu-id="4cd67-108">Für beide Optionen müssen Sie die hololens einrichten, damit das [Geräte Portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) für die Entwicklung verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="4cd67-108">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="4cd67-109">Bereitstellen auf einem Gerät über den Unreal-Editor</span><span class="sxs-lookup"><span data-stu-id="4cd67-109">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="4cd67-110">Wählen Sie den Dropdown Pfeil neben der Schaltfläche **Start** aus.</span><span class="sxs-lookup"><span data-stu-id="4cd67-110">Select the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="4cd67-111">Anfänglich ist die hololens-Geräte Option ausgegraut.</span><span class="sxs-lookup"><span data-stu-id="4cd67-111">Initially, the HoloLens device option will be grayed out.</span></span>

![Startmenü Optionen](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="4cd67-113">Öffnen Sie die **Geräte-Manager** , und beachten Sie, dass Ihre hololens nicht automatisch in der Geräteliste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4cd67-113">Open the **Device Manager** and note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="4cd67-114">Erweitern Sie den Abschnitt **nicht aufgelisteten Gerät hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="4cd67-114">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="4cd67-115">Wählen Sie **hololens** als **Plattform** aus.</span><span class="sxs-lookup"><span data-stu-id="4cd67-115">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="4cd67-116">Geben Sie die IP-Adresse und die Port Informationen Ihrer Geräte als Geräte Bezeichner getrennt durch einen Doppelpunkt ein.</span><span class="sxs-lookup"><span data-stu-id="4cd67-116">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="4cd67-117">Beispiel: "127.0.0.1:10080" (bei Verbindung über USB).</span><span class="sxs-lookup"><span data-stu-id="4cd67-117">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="4cd67-118">Verwenden Sie die Anmelde Informationen für den Benutzernamen Ihres Geräte Portals.</span><span class="sxs-lookup"><span data-stu-id="4cd67-118">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="4cd67-119">Schließen **Sie** den Geräte-Manager, und schließen Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="4cd67-119">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="4cd67-120">Wenn ein Fehler vorliegt, z. b. falsche Adresse oder Benutzer Anmelde Informationen, wird eine Nachricht in das Ausgabeprotokoll gedruckt.</span><span class="sxs-lookup"><span data-stu-id="4cd67-120">If there's an error, such as wrong address or user credentials, a message will print to the Output Log.</span></span>

![Hinzufügen eines nicht aufgelisteten Geräts](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="4cd67-122">Klicken Sie erneut auf den Dropdown Pfeil neben der Schaltfläche " **Start** ". dieses Mal sollte das von Ihnen soeben hinzugefügte hololens-Gerät angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4cd67-122">Select the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="4cd67-123">Wählen Sie das hololens-Gerät zum Erstellen und Bereitstellen Ihrer hololens aus.</span><span class="sxs-lookup"><span data-stu-id="4cd67-123">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="4cd67-124">Das Erstellen für das Gerät erfordert möglicherweise die Neukompilierung von Shadern (insbesondere bei der ersten Ausführung). Dies kann einige Zeit in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="4cd67-124">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="4cd67-125">Lassen Sie das Gerät erst wieder in den Standbymodus wechseln, wenn die app ausgeführt wird (möglicherweise müssen Sie es verwenden).</span><span class="sxs-lookup"><span data-stu-id="4cd67-125">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="4cd67-126">Andernfalls tritt bei der shaderkompilierung ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="4cd67-126">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="4cd67-127">Bereitstellen auf einem Gerät über das Geräte Portal</span><span class="sxs-lookup"><span data-stu-id="4cd67-127">Deploying to device via device portal</span></span>

<span data-ttu-id="4cd67-128">Ausführliche Anweisungen zum Verpacken und Bereitstellen einer App finden Sie in der [Unreal-tutorialreihe](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span><span class="sxs-lookup"><span data-stu-id="4cd67-128">You can find detailed instructions on packaging and deploying an app in the [Unreal tutorial series](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="4cd67-129">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="4cd67-129">Next Development Checkpoint</span></span>

<span data-ttu-id="4cd67-130">Wenn Sie der unwirklichen Entwicklungs Journey folgen, die wir gerade angelegt haben, befinden Sie sich in der Mitte der Bereitstellungs Phase.</span><span class="sxs-lookup"><span data-stu-id="4cd67-130">If you're following the Unreal development journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="4cd67-131">Von hier aus können Sie weiterhin erweiterte Dienste hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="4cd67-131">From here, you can continue to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4cd67-132">Erweiterte Dienste</span><span class="sxs-lookup"><span data-stu-id="4cd67-132">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="4cd67-133">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="4cd67-133">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
