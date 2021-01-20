---
title: Start Geste
description: Erfahren Sie, wie Sie mit der Start Bewegung das Startmenü auf hololens und in Windows Mixed Reality-immersiven Headsets aufzurufen.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Gemischte Realität, Gesten, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Bloom
ms.openlocfilehash: d0f3bd81cab945a01a523806ebaf4546752d74c1
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583230"
---
# <a name="start-gesture"></a><span data-ttu-id="13eef-104">Start Geste</span><span class="sxs-lookup"><span data-stu-id="13eef-104">Start gesture</span></span>

<span data-ttu-id="13eef-105">Die Start Geste ist eine Handbewegung, mit der das Startmenü aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="13eef-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="13eef-106">Dies entspricht dem Drücken der Windows-Taste auf den Tastaturen, der Xbox-Schaltfläche auf Xbox-Controllern oder der Windows-Schaltfläche auf immersiven Headset-Motion-Controllern.</span><span class="sxs-lookup"><span data-stu-id="13eef-106">It's the equivalent of pressing the Windows key on keyboards, the Xbox button on Xbox controllers, or the Windows button on immersive headset motion controllers.</span></span> <span data-ttu-id="13eef-107">Achten Sie besonders auf die Gesten der reservierten Systeme auf jedem gemischten Reality-Gerät, um Konflikte beim Entwerfen von Interaktionen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="13eef-107">Pay special attention to reserved system gestures on each Mixed Reality device to prevent conflicts when you're designing interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="13eef-108">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="13eef-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="13eef-109"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="13eef-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="13eef-110"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="13eef-110"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="13eef-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="13eef-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="13eef-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="13eef-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="13eef-113">Blüte</span><span class="sxs-lookup"><span data-stu-id="13eef-113">Bloom</span></span></td>
        <td><span data-ttu-id="13eef-114">✔️</span><span class="sxs-lookup"><span data-stu-id="13eef-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="13eef-115">Handgelenk Taste</span><span class="sxs-lookup"><span data-stu-id="13eef-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="13eef-116">✔️</span><span class="sxs-lookup"><span data-stu-id="13eef-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="13eef-117">Eye-und Palmen Pfeil nach oben</span><span class="sxs-lookup"><span data-stu-id="13eef-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="13eef-118">✔️</span><span class="sxs-lookup"><span data-stu-id="13eef-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="13eef-119">Blüte</span><span class="sxs-lookup"><span data-stu-id="13eef-119">Bloom</span></span>

<span data-ttu-id="13eef-120">Wir haben "Bloom" entworfen, um das Startmenü in hololens (1st Gen) aufzurufen. Dies ist eine symbolische Geste, die eine Blüten Blüte imitiert.</span><span class="sxs-lookup"><span data-stu-id="13eef-120">We designed “Bloom” to bring up the start menu in HoloLens (1st gen), which is a symbolic gesture mimicking a flower blossom.</span></span> <span data-ttu-id="13eef-121">Es ist eine besondere Interaktion, eine einfache Verwendung und eine schnelle Erinnerung.</span><span class="sxs-lookup"><span data-stu-id="13eef-121">It's distinctive for sure-footed interaction, easy of use, and quick to recall.</span></span> <span data-ttu-id="13eef-122">Wenn Sie die Geste verwenden möchten, halten Sie Ihre Hand an Ihre Hand, um die Hand zu öffnen, und öffnen Sie dann die Hand, indem Sie Ihre Finger verteilen.</span><span class="sxs-lookup"><span data-stu-id="13eef-122">To use the gesture, hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="13eef-123">![Schließen der Blüte](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="13eef-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="13eef-124">**Schritt 1: überschreiten der Hand.**</span><span class="sxs-lookup"><span data-stu-id="13eef-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13eef-125">![Geöffnet, geöffnet](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="13eef-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="13eef-126">**Schritt 2: überschreiten der handbreiten Verteilung**</span><span class="sxs-lookup"><span data-stu-id="13eef-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="13eef-127">Start Geste</span><span class="sxs-lookup"><span data-stu-id="13eef-127">Start gesture</span></span>

<span data-ttu-id="13eef-128">In hololens 2 wurde die Blüte Bewegung durch eine virtuelle Handgelenk Schaltfläche ersetzt, die für Benutzer besser instanzieller ist.</span><span class="sxs-lookup"><span data-stu-id="13eef-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button, which is more instinctual for users.</span></span> <span data-ttu-id="13eef-129">Wenn die Benutzer die Schaltfläche auf dem Handgelenk anzeigt, können Sie sie intuitiv erreichen und mit der anderen Seite drücken.</span><span class="sxs-lookup"><span data-stu-id="13eef-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="13eef-130">![Handgelenk Taste](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="13eef-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="13eef-131">**Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**</span><span class="sxs-lookup"><span data-stu-id="13eef-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13eef-132">![Handgelenk Taste drücken](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="13eef-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="13eef-133">**Schritt 2: Klicken Sie auf das Handgelenk.**</span><span class="sxs-lookup"><span data-stu-id="13eef-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a><span data-ttu-id="13eef-134">Einstufige Start Geste</span><span class="sxs-lookup"><span data-stu-id="13eef-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="13eef-135">Damit die einstufige Start Geste funktioniert:</span><span class="sxs-lookup"><span data-stu-id="13eef-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="13eef-136">Sie müssen ein Update auf das Update von November 2019 (Build 18363,1039) oder höher durch haben.</span><span class="sxs-lookup"><span data-stu-id="13eef-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="13eef-137">Die Augen müssen auf dem Gerät so kalibriert werden, dass die Eye-Nachverfolgung ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="13eef-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="13eef-138">Wenn Sie keine Umkreis Punkte um das Start Symbol sehen, wenn Sie es betrachten, werden die Augen nicht auf dem Gerät gekalibriert.</span><span class="sxs-lookup"><span data-stu-id="13eef-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="13eef-139">Sie können auch die Start Geste nur mit einer Hand verwenden.</span><span class="sxs-lookup"><span data-stu-id="13eef-139">You can also use the Start gesture with only one hand.</span></span> <span data-ttu-id="13eef-140">Halten Sie Ihre Hand mit Ihrer Hand, und sehen Sie sich das **Start Symbol** auf Ihrem inneren Handgelenk an.</span><span class="sxs-lookup"><span data-stu-id="13eef-140">Hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="13eef-141">**Wenn Sie das Symbol gedrückt halten**, können Sie den Ziehpunkt und den Finger des Indexes zusammenhalten.</span><span class="sxs-lookup"><span data-stu-id="13eef-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="13eef-142">![Handgelenk Taste](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="13eef-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="13eef-143">**Schritt 1: Palme zum Anzeigen der Schaltfläche "Handgelenk"**</span><span class="sxs-lookup"><span data-stu-id="13eef-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13eef-144">![Handgelenk Schaltfläche](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="13eef-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="13eef-145">**Schritt 2: Augenblick auf die Schaltfläche und dann auf die Schaltfläche**</span><span class="sxs-lookup"><span data-stu-id="13eef-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="13eef-146">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="13eef-146">See also</span></span>

* [<span data-ttu-id="13eef-147">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="13eef-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="13eef-148">Augenblick</span><span class="sxs-lookup"><span data-stu-id="13eef-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="13eef-149">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="13eef-149">Voice input</span></span>](voice-input.md)