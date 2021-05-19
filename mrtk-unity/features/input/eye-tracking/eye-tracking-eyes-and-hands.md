---
title: 'Eyetracking (Blickverfolgung): Augen und Hände'
description: Verwenden von Eye targeting als primärer Zeiger in Kombination mit Handbewegungen im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: c9d5f23610d821aa1e50a3217a4be736601dc14d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143996"
---
# <a name="eyes--hand-interaction"></a><span data-ttu-id="d69ae-104">Interaktion von Augen und Hand</span><span class="sxs-lookup"><span data-stu-id="d69ae-104">Eyes + hand interaction</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="d69ae-105">Unterstützung von _Blick- und Handbewegungen_ (Anvieren mit den Augen & Handgesten)</span><span class="sxs-lookup"><span data-stu-id="d69ae-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="d69ae-106">Auf dieser Seite wird erläutert, wie Sie eye targeting als primären Zeiger in Kombination mit Handbewegungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="d69ae-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="d69ae-107">In unseren [MRTK-Eyetracking-Demos](../../example-scenes/eye-tracking-examples-overview.md)beschreiben wir mehrere Beispiele für die Verwendung von Augen und Händen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="d69ae-107">In our [MRTK eye tracking demos](../../example-scenes/eye-tracking-examples-overview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="d69ae-108">[Auswahl:](eye-tracking-target-selection.md)Betrachten Sie die entfernte holografische Schaltfläche, und führen Sie einfach eine Geste aus, um sie schnell auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="d69ae-108">[Selection](eye-tracking-target-selection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="d69ae-109">**Positionierung (in diesem Artikel):** Bewegen Sie ein Hologramm in fluently über Ihre Szene, indem Sie es einfach betrachten, indem Sie ihren Zeigefinger und den Daumen zusammendrücken, um es zu greifen und es dann mit der Hand zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="d69ae-109">**Positioning (this article)**: Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="d69ae-110">[Navigation:](eye-tracking-navigation.md)Sehen Sie sich einfach eine Position an, an der Sie zoomen möchten, heften Sie den Zeigefinger und den Daumen zusammen, und _ziehen_ Sie die Hand auf Sie, um sie zu vergrößern.</span><span class="sxs-lookup"><span data-stu-id="d69ae-110">[Navigation](eye-tracking-navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="d69ae-111">Beachten Sie, dass MRTK zurzeit so konzipiert ist, dass handgestrahlte Lichtstrahle im Abstand als priorisierte Fokuszeiger fungieren.</span><span class="sxs-lookup"><span data-stu-id="d69ae-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="d69ae-112">Dies bedeutet, dass die Zeiger für den Kopf und das Anvieren mit den Augen automatisch unterdrückt werden, sobald eine Hand erkannt wird, und wieder sichtbar wird, nachdem sie "Auswählen" gesagt haben.</span><span class="sxs-lookup"><span data-stu-id="d69ae-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="d69ae-113">Dies ist jedoch möglicherweise nicht die Art und Weise, wie Sie in einer Entfernung interagieren möchten, und bevorzugen stattdessen eine einfache Interaktion _mit anvisieren und committen,_ unabhängig davon, ob Die Hände in Ihrer Ansicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="d69ae-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="d69ae-114">Deaktivieren des Handstrahls</span><span class="sxs-lookup"><span data-stu-id="d69ae-114">How to disable the hand ray</span></span>

<span data-ttu-id="d69ae-115">Um den Handstrahlzeiger zu deaktivieren, entfernen Sie einfach _"DefaultControllerPointer"_ in der MrTK-Konfigurationseinstellung _Input -> Pointer._</span><span class="sxs-lookup"><span data-stu-id="d69ae-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="d69ae-116">Um Augen und Hände wie oben in Ihrer App beschrieben zu verwenden, stellen Sie außerdem sicher, dass Sie alle Anforderungen für die Verwendung von [Eyetracking](eye-tracking-basic-setup.md)erfüllen.</span><span class="sxs-lookup"><span data-stu-id="d69ae-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](eye-tracking-basic-setup.md).</span></span>

![Entfernen des Handstrahls](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="d69ae-118">Sie können sich auch ansehen, wie das Eingabeprofil _EyeTrackingDemoPointerProfile_ aus dem Eye tracking-Beispielpaket als Referenz eingerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="d69ae-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="d69ae-119">So halten Sie den Anvzeiger immer an</span><span class="sxs-lookup"><span data-stu-id="d69ae-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="d69ae-120">Um zu vermeiden, dass die Zeiger für den Kopf oder das Anvisierten mit den Augen automatisch unterdrückt werden, sobald eine Hand erkannt wird, kann der Anvisierten [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) angegeben werden, um zu steuern, ob sie ein- oder ausgeschaltet werden soll.</span><span class="sxs-lookup"><span data-stu-id="d69ae-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="d69ae-121">Informationen finden Sie unter [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md).</span><span class="sxs-lookup"><span data-stu-id="d69ae-121">See [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span></span>

---
[<span data-ttu-id="d69ae-122">Zurück zu "Eye tracking in the MixedRealityToolkit" (Blickverfolgung im MixedRealityToolkit)</span><span class="sxs-lookup"><span data-stu-id="d69ae-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
