---
title: QR-Codes in Unreal
description: Leitfaden zur Verwendung von QR-Codes in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, QR-Codes, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: f2f06e9aa8d458d58dc8551ab6cd726622c30d4c
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354410"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="4fe00-104">QR-Codes in Unreal</span><span class="sxs-lookup"><span data-stu-id="4fe00-104">QR codes in Unreal</span></span>

<span data-ttu-id="4fe00-105">HoloLens 2 kann QR-Codes in der Außenwelt mithilfe der Webcam sehen und gibt sie mithilfe eines Koordinatensystems an jeder Position von Codes in der Realwelt als Hologramme wieder.</span><span class="sxs-lookup"><span data-stu-id="4fe00-105">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="4fe00-106">Über einzelne QR-Codes hinaus kann HoloLens 2 Hologramme außerdem an der gleichen Position auf mehreren Geräten rendern, um eine gemeinsame Erfahrung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="4fe00-106">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="4fe00-107">Achten Sie darauf, die bewährten Methoden für das Hinzufügen von QR-Codes zu Ihren Anwendungen zu befolgen:</span><span class="sxs-lookup"><span data-stu-id="4fe00-107">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="4fe00-108">Ruhezonen</span><span class="sxs-lookup"><span data-stu-id="4fe00-108">Quiet zones</span></span>
- <span data-ttu-id="4fe00-109">Beleuchtung und Hintergrund</span><span class="sxs-lookup"><span data-stu-id="4fe00-109">Lighting and backdrop</span></span>
- <span data-ttu-id="4fe00-110">Größe, Abstand und Winkelposition</span><span class="sxs-lookup"><span data-stu-id="4fe00-110">Size, distance, and angular position</span></span>

<span data-ttu-id="4fe00-111">Achten Sie besonders auf [Umgebungsaspekte](../../environment-considerations-for-hololens.md), wenn in Ihrer App QR-Codes platziert werden.</span><span class="sxs-lookup"><span data-stu-id="4fe00-111">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="4fe00-112">Weitere Informationen zu jedem dieser Themen und Anweisungen zum Herunterladen des erforderlichen NuGet-Pakets finden Sie im Dokument zum [Nachverfolgen von QR-Codes](../platform-capabilities-and-apis/qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="4fe00-112">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

> [!CAUTION]
> <span data-ttu-id="4fe00-113">QR-Codes sind die einzige Art von Bildern, die von HoloLens standardmäßig nachverfolgt werden können – das Modul **UARTrackedImage** von Unreal wird von HoloLens nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4fe00-113">QR codes are the only type of images that can be tracked by HoloLens out of the box - Unreal's **UARTrackedImage** module isn't supported on HoloLens.</span></span> <span data-ttu-id="4fe00-114">Wenn Sie benutzerdefinierte Bilder nachverfolgen müssen, können Sie auf die [Webcam](unreal-hololens-camera.md) des Geräts zugreifen und Bilder mithilfe einer Drittanbieterbibliothek zur Bilderkennung verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="4fe00-114">If you need to track custom images, you can access the device's [webcam](unreal-hololens-camera.md) and process images using a third party image recognition library.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="4fe00-115">Aktivieren der QR-Erkennung</span><span class="sxs-lookup"><span data-stu-id="4fe00-115">Enabling QR detection</span></span>
<span data-ttu-id="4fe00-116">Da HoloLens 2 die Webcam verwenden muss, um QR-Codes zu sehen, müssen Sie diese in den Projekteinstellungen aktivieren:</span><span class="sxs-lookup"><span data-stu-id="4fe00-116">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="4fe00-117">Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), scrollen Sie zum Abschnitt **Platforms** (Plattformen), und klicken Sie auf **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="4fe00-117">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="4fe00-118">Klappen Sie den Abschnitt **Capabilities** (Funktionen) auf, und aktivieren Sie **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="4fe00-118">Expand the **Capabilities** section and check **Webcam**.</span></span>  
- <span data-ttu-id="4fe00-119">Ferner müssen Sie die Nachverfolgung von QR-Codes abonnieren, indem Sie [ein ARSessionConfig-Objekt hinzufügen](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="4fe00-119">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

[!INCLUDE[](includes/tabs-qr-codes.md)]

## <a name="setting-up-a-tracked-qr-code"></a><span data-ttu-id="4fe00-120">Einrichten eines nachverfolgten QR-Codes</span><span class="sxs-lookup"><span data-stu-id="4fe00-120">Setting up a tracked QR code</span></span>

<span data-ttu-id="4fe00-121">QR-Codes werden über das AR-Geometrienachverfolgungssystem von Unreal als nachverfolgtes Bild bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4fe00-121">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="4fe00-122">Damit dies funktioniert, müssen Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="4fe00-122">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="4fe00-123">Eine Blaupause eines Akteurs erstellen und eine **ARTrackableNotify**-Komponente hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="4fe00-123">Create an Actor Blueprint and add an **ARTrackableNotify** component:</span></span>

![QR: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="4fe00-125">**ARTrackableNotify** auswählen und den Abschnitt **Events** (Ereignisse) im Bereich **Details** aufklappen:</span><span class="sxs-lookup"><span data-stu-id="4fe00-125">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel:</span></span>

![QR: Ereignisse](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="4fe00-127">Klicken Sie neben **On Add Tracked Geometry** (Beim Hinzufügen von nachverfolgter Geometrie) auf **+** , um dem Ereignisdiagramm den Knoten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="4fe00-127">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="4fe00-128">Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="4fe00-128">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Knoten zu On Add Tracked Geometry hinzufügen](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a><span data-ttu-id="4fe00-130">Verwenden eines nachverfolgten QR-Codes</span><span class="sxs-lookup"><span data-stu-id="4fe00-130">Using a tracked QR code</span></span>
<span data-ttu-id="4fe00-131">Das Ereignisdiagramm in der folgenden Abbildung zeigt, wie das **OnUpdateTrackedImage**-Ereignis dazu verwendet wird, einen Punkt in der Mitte eines QR-Codes zu rendern und dessen Daten auszugeben.</span><span class="sxs-lookup"><span data-stu-id="4fe00-131">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

![QR: Renderbeispiel](images/unreal-qr-render.PNG)

<span data-ttu-id="4fe00-133">Das geschieht bei diesem Vorgang:</span><span class="sxs-lookup"><span data-stu-id="4fe00-133">Here's what's going on:</span></span>
1. <span data-ttu-id="4fe00-134">Zunächst wird das nachverfolgte Bild in einen **ARTrackedQRCode** umgewandelt, um zu prüfen, ob es sich bei dem aktuellen aktualisierten Bild um einen QR-Code handelt.</span><span class="sxs-lookup"><span data-stu-id="4fe00-134">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="4fe00-135">Die codierten Daten werden aus der **QRCode**-Variable abgerufen.</span><span class="sxs-lookup"><span data-stu-id="4fe00-135">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="4fe00-136">Sie können den oberen linken Punkt des QR-Codes aus der Position von **GetLocalToWorldTransform** und seine Abmessungen mit **GetEstimateSize** abrufen.</span><span class="sxs-lookup"><span data-stu-id="4fe00-136">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="4fe00-137">Ferner können Sie [das Koordinatensystem für einen QR-Code in Code abrufen](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code).</span><span class="sxs-lookup"><span data-stu-id="4fe00-137">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="4fe00-138">Ermitteln der eindeutigen ID</span><span class="sxs-lookup"><span data-stu-id="4fe00-138">Finding the unique ID</span></span>
<span data-ttu-id="4fe00-139">Jeder QR-Code weist eine eindeutige GUID-ID auf, die Sie auf diese Weise herausfinden können:</span><span class="sxs-lookup"><span data-stu-id="4fe00-139">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="4fe00-140">Ziehen und Ablegen des **As ARTracked QRCode**-Stifts und Suchen nach **Get Unique ID** (Eindeutige ID abrufen).</span><span class="sxs-lookup"><span data-stu-id="4fe00-140">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR: GUID](images/unreal-qr-guid.PNG)

<span data-ttu-id="4fe00-142">Mit QR-Codes passiert eine Menge hinter den Kulissen, daher ist diese Erörterung nicht abschließend.</span><span class="sxs-lookup"><span data-stu-id="4fe00-142">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="4fe00-143">Folgen Sie unbedingt den folgenden Links, um mehr über die inneren Vorgänge zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="4fe00-143">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="4fe00-144">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="4fe00-144">Next Development Checkpoint</span></span>

<span data-ttu-id="4fe00-145">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der Mixed Reality-Plattformfunktionen und APIs.</span><span class="sxs-lookup"><span data-stu-id="4fe00-145">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="4fe00-146">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="4fe00-146">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4fe00-147">WinRT</span><span class="sxs-lookup"><span data-stu-id="4fe00-147">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="4fe00-148">Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:</span><span class="sxs-lookup"><span data-stu-id="4fe00-148">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4fe00-149">Bereitstellung auf Gerät</span><span class="sxs-lookup"><span data-stu-id="4fe00-149">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="4fe00-150">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#3-platform-capabilities-and-apis) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="4fe00-150">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fe00-151">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4fe00-151">See also</span></span>
* [<span data-ttu-id="4fe00-152">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="4fe00-152">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="4fe00-153">Hologramme</span><span class="sxs-lookup"><span data-stu-id="4fe00-153">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="4fe00-154">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="4fe00-154">Coordinate systems</span></span>](../../design/coordinate-systems.md)
