---
title: Augen und Hände
description: Verwenden der Blickadressierung als primärer Zeiger in Kombination mit Handbewegungen im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: ff464c6f2381a9df020a9ccf807672d4463d662c
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175114"
---
# <a name="eyes-and-hands"></a><span data-ttu-id="32061-104">Augen und Hände</span><span class="sxs-lookup"><span data-stu-id="32061-104">Eyes and hands</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="32061-105">Unterstützung von _Blick- und Handbewegungen_ (anv & Handgesten)</span><span class="sxs-lookup"><span data-stu-id="32061-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="32061-106">Auf dieser Seite wird erläutert, wie Sie die Blickadressierung als primären Zeiger in Kombination mit Handbewegungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="32061-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="32061-107">In unseren [MRTK-Eyetracking-Demos](../../example-scenes/eye-tracking-examples-overview.md)beschreiben wir mehrere Beispiele für die Verwendung von Augen und Händen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="32061-107">In our [MRTK eye tracking demos](../../example-scenes/eye-tracking-examples-overview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="32061-108">[Auswahl:](eye-tracking-target-selection.md)Sehen Sie sich die entfernte holografische Schaltfläche an, und führen Sie einfach eine Heftbewegung aus, um sie schnell auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="32061-108">[Selection](eye-tracking-target-selection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="32061-109">**Positionierung (dieser Artikel):** Bewegen Sie ein Hologramm fluently über Ihre Szene, indem Sie es einfach an sehen, den Zeigefinger und den Zeigefinger zusammendrippen, um es zu greifen und es dann mit der Hand zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="32061-109">**Positioning (this article)**: Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="32061-110">[Navigation:](eye-tracking-navigation.md)Sehen Sie sich einfach eine Position an, an der  Sie zoomen möchten, heften Sie den Zeigefinger und den Zeigefinger zusammen, und ziehen Sie Ihre Hand zu Ihnen, um sie zu vergrößern.</span><span class="sxs-lookup"><span data-stu-id="32061-110">[Navigation](eye-tracking-navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="32061-111">Beachten Sie, dass MRTK derzeit so konzipiert ist, dass Handlichtlichter aus der Entfernung als priorisierte Fokuszeder fungieren.</span><span class="sxs-lookup"><span data-stu-id="32061-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="32061-112">Dies bedeutet, dass die Anvitätszeigen mit dem Kopf und den Augen automatisch unterdrückt werden, sobald eine Hand erkannt wird, und nach dem Sagen von "Auswählen" wieder sichtbar wird.</span><span class="sxs-lookup"><span data-stu-id="32061-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="32061-113">Dies ist jedoch möglicherweise nicht die Art und Weise, wie  Sie aus der Entfernung interagieren möchten und stattdessen eine einfache "Anvisieren und Commit"-Interaktion bevorzugen, unabhängig vom Vorhandensein der Hände in Ihrer Ansicht.</span><span class="sxs-lookup"><span data-stu-id="32061-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="32061-114">Deaktivieren des Handstrahls</span><span class="sxs-lookup"><span data-stu-id="32061-114">How to disable the hand ray</span></span>

<span data-ttu-id="32061-115">Um den Handstrahlzeiger zu deaktivieren, entfernen Sie einfach _den "DefaultControllerPointer"_ in der _Konfigurationseinstellung Input -> Pointer_ MRTK.</span><span class="sxs-lookup"><span data-stu-id="32061-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="32061-116">Um Augen und Hände wie oben in Ihrer App beschrieben zu verwenden, stellen Sie außerdem sicher, dass Sie alle Anforderungen für die Verwendung von [Eyetracking erfüllen.](eye-tracking-basic-setup.md)</span><span class="sxs-lookup"><span data-stu-id="32061-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](eye-tracking-basic-setup.md).</span></span>

![Entfernen des Handstrahls](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="32061-118">Sie können auch überprüfen, wie das Eingabeprofil _EyeTrackingDemoPointerProfile_ aus dem EyeTracking-Beispielpaket als Referenz eingerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="32061-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="32061-119">So halten Sie den Anvingzeiger immer auf</span><span class="sxs-lookup"><span data-stu-id="32061-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="32061-120">Um zu vermeiden, dass die Anvitätszeigen mit dem Kopf oder den Augen automatisch unterdrückt werden, sobald eine Hand erkannt wird, kann der Anvitäts-Parameter angegeben werden, um zu steuern, ob er ein- oder [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) ausgeschaltet werden soll.</span><span class="sxs-lookup"><span data-stu-id="32061-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="32061-121">Informationen finden Sie unter [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md).</span><span class="sxs-lookup"><span data-stu-id="32061-121">See [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span></span>

---
[<span data-ttu-id="32061-122">Zurück zu "Eye tracking in the MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="32061-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
