---
title: QR-Codes in Unreal
description: Erfahren Sie, wie QR-Codes in Unreal-Mixed Reality-Anwendungen eingerichtet, verwendet und nachverfolgt werden.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, QR-Codes, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: d9f23bacf31b310da6d49e74de2153b50e642c7d
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582659"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="7331d-104">QR-Codes in Unreal</span><span class="sxs-lookup"><span data-stu-id="7331d-104">QR codes in Unreal</span></span>

<span data-ttu-id="7331d-105">HoloLens 2 kann QR-Codes in der Außenwelt mithilfe der Webcam sehen und gibt sie an jeder Position von Codes in der Realwelt als Hologramme wieder.</span><span class="sxs-lookup"><span data-stu-id="7331d-105">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms at each code's real-world position.</span></span> <span data-ttu-id="7331d-106">HoloLens 2 kann Hologramme außerdem an der gleichen Position auf mehreren Geräten rendern, um eine gemeinsame Erfahrung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="7331d-106">HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="7331d-107">Achten Sie darauf, die bewährten Methoden für das Hinzufügen von QR-Codes zu Ihren Anwendungen zu befolgen:</span><span class="sxs-lookup"><span data-stu-id="7331d-107">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="7331d-108">Ruhezonen</span><span class="sxs-lookup"><span data-stu-id="7331d-108">Quiet zones</span></span>
- <span data-ttu-id="7331d-109">Beleuchtung und Hintergrund</span><span class="sxs-lookup"><span data-stu-id="7331d-109">Lighting and backdrop</span></span>
- <span data-ttu-id="7331d-110">Größe, Abstand und Winkelposition</span><span class="sxs-lookup"><span data-stu-id="7331d-110">Size, distance, and angular position</span></span>

<span data-ttu-id="7331d-111">Achten Sie besonders auf [Umgebungsaspekte](/hololens/hololens-environment-considerations), wenn in Ihrer App QR-Codes platziert werden.</span><span class="sxs-lookup"><span data-stu-id="7331d-111">Pay special attention to the [environment considerations](/hololens/hololens-environment-considerations) when QR codes are being placed in your app.</span></span> <span data-ttu-id="7331d-112">Weitere Informationen zu jedem dieser Themen und Anweisungen zum Herunterladen des erforderlichen NuGet-Pakets finden Sie im Dokument zum [Nachverfolgen von QR-Codes](../platform-capabilities-and-apis/qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="7331d-112">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

> [!CAUTION]
> <span data-ttu-id="7331d-113">QR-Codes sind die einzige Art von Bildern, die von HoloLens standardmäßig nachverfolgt werden können – das Modul **UARTrackedImage** von Unreal wird von HoloLens nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7331d-113">QR codes are the only type of images that can be tracked by HoloLens out of the box - Unreal's **UARTrackedImage** module isn't supported on HoloLens.</span></span> <span data-ttu-id="7331d-114">Wenn Sie benutzerdefinierte Bilder nachverfolgen müssen, können Sie auf die [Webcam](unreal-hololens-camera.md) des Geräts zugreifen und Bilder mithilfe einer Drittanbieterbibliothek zur Bilderkennung verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="7331d-114">If you need to track custom images, you can access the device's [webcam](unreal-hololens-camera.md) and process images using a third party image recognition library.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="7331d-115">Aktivieren der QR-Erkennung</span><span class="sxs-lookup"><span data-stu-id="7331d-115">Enabling QR detection</span></span>

<span data-ttu-id="7331d-116">Da HoloLens 2 die Webcam verwenden muss, um QR-Codes zu sehen, müssen Sie diese in den Projekteinstellungen aktivieren:</span><span class="sxs-lookup"><span data-stu-id="7331d-116">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="7331d-117">Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), scrollen Sie zum Abschnitt **Platforms** (Plattformen), und wählen Sie **HoloLens** aus.</span><span class="sxs-lookup"><span data-stu-id="7331d-117">Open **Edit > Project Settings**, scroll to the **Platforms** section, and select **HoloLens**.</span></span>
    + <span data-ttu-id="7331d-118">Klappen Sie den Abschnitt **Capabilities** (Funktionen) auf, und aktivieren Sie **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="7331d-118">Expand the **Capabilities** section and check **Webcam**.</span></span>  
- <span data-ttu-id="7331d-119">Ferner müssen Sie die Nachverfolgung von QR-Codes abonnieren, indem Sie [ein ARSessionConfig-Objekt hinzufügen](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="7331d-119">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a><span data-ttu-id="7331d-120">Einrichten eines nachverfolgten QR-Codes</span><span class="sxs-lookup"><span data-stu-id="7331d-120">Setting up a tracked QR code</span></span>

<span data-ttu-id="7331d-121">QR-Codes werden über das AR-Geometrienachverfolgungssystem von Unreal als nachverfolgtes Bild bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7331d-121">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="7331d-122">Damit dies funktioniert, müssen Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="7331d-122">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="7331d-123">Eine Blaupause eines Akteurs erstellen und eine **ARTrackableNotify**-Komponente hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="7331d-123">Create an Actor Blueprint and add an **ARTrackableNotify** component:</span></span>

![QR: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="7331d-125">**ARTrackableNotify** auswählen und den Abschnitt **Events** (Ereignisse) im Bereich **Details** aufklappen:</span><span class="sxs-lookup"><span data-stu-id="7331d-125">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel:</span></span>

![QR: Ereignisse](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="7331d-127">Klicken Sie neben **On Add Tracked Geometry** (Beim Hinzufügen von nachverfolgter Geometrie) auf **+** , um dem Ereignisdiagramm den Knoten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7331d-127">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="7331d-128">Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="7331d-128">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Knoten zu On Add Tracked Geometry hinzufügen](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a><span data-ttu-id="7331d-130">Verwenden eines nachverfolgten QR-Codes</span><span class="sxs-lookup"><span data-stu-id="7331d-130">Using a tracked QR code</span></span>

<span data-ttu-id="7331d-131">Das Ereignisdiagramm in der folgenden Abbildung zeigt, wie das **OnUpdateTrackedImage**-Ereignis dazu verwendet wird, einen Punkt in der Mitte eines QR-Codes zu rendern und dessen Daten auszugeben.</span><span class="sxs-lookup"><span data-stu-id="7331d-131">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

<span data-ttu-id="7331d-132">Das geschieht bei diesem Vorgang:</span><span class="sxs-lookup"><span data-stu-id="7331d-132">Here's what's going on:</span></span>
1. <span data-ttu-id="7331d-133">Zunächst wird das nachverfolgte Bild in einen **ARTrackedQRCode** umgewandelt, um zu prüfen, ob es sich bei dem aktuellen aktualisierten Bild um einen QR-Code handelt.</span><span class="sxs-lookup"><span data-stu-id="7331d-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="7331d-134">Die codierten Daten werden aus der **QRCode**-Variable abgerufen.</span><span class="sxs-lookup"><span data-stu-id="7331d-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="7331d-135">Sie können den oberen linken Punkt des QR-Codes aus der Position von **GetLocalToWorldTransform** und seine Abmessungen mit **GetEstimateSize** abrufen.</span><span class="sxs-lookup"><span data-stu-id="7331d-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="7331d-136">Ferner können Sie [das Koordinatensystem für einen QR-Code in Code abrufen](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code).</span><span class="sxs-lookup"><span data-stu-id="7331d-136">You can also [get the coordinate system for a QR code](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="7331d-137">Ermitteln der eindeutigen ID</span><span class="sxs-lookup"><span data-stu-id="7331d-137">Finding the unique ID</span></span>

<span data-ttu-id="7331d-138">Jeder QR-Code weist eine eindeutige GUID-ID auf, die Sie auf diese Weise herausfinden können:</span><span class="sxs-lookup"><span data-stu-id="7331d-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="7331d-139">Ziehen und Ablegen des **As ARTracked QRCode**-Stifts und Suchen nach **Get Unique ID** (Eindeutige ID abrufen).</span><span class="sxs-lookup"><span data-stu-id="7331d-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR: GUID](images/unreal-qr-guid.PNG)

<span data-ttu-id="7331d-141">Mit QR-Codes passiert eine Menge hinter den Kulissen, daher ist diese Erörterung nicht abschließend.</span><span class="sxs-lookup"><span data-stu-id="7331d-141">There's a lot going on behind the scenes with QR codes, so you're not at the end of the road.</span></span> <span data-ttu-id="7331d-142">Folgen Sie unbedingt den folgenden Links, um mehr über die inneren Vorgänge zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="7331d-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7331d-143">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="7331d-143">Next Development Checkpoint</span></span>

<span data-ttu-id="7331d-144">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der Mixed Reality-Plattformfunktionen und APIs.</span><span class="sxs-lookup"><span data-stu-id="7331d-144">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="7331d-145">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="7331d-145">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7331d-146">WinRT</span><span class="sxs-lookup"><span data-stu-id="7331d-146">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="7331d-147">Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:</span><span class="sxs-lookup"><span data-stu-id="7331d-147">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7331d-148">Bereitstellung auf Gerät</span><span class="sxs-lookup"><span data-stu-id="7331d-148">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="7331d-149">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#3-advanced-features) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="7331d-149">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7331d-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7331d-150">See also</span></span>
* [<span data-ttu-id="7331d-151">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="7331d-151">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="7331d-152">Hologramme</span><span class="sxs-lookup"><span data-stu-id="7331d-152">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="7331d-153">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="7331d-153">Coordinate systems</span></span>](../../design/coordinate-systems.md)