---
title: Schaltfläche
description: Erfahren Sie, wie Sie mit Schaltflächen, die eine der grundlegenden Komponenten von Mixed Reality sind, eine sofortige Aktion auslöst.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Gemischte Realität, Steuerelemente, Interaktion, UI, UX, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Schaltfläche
ms.openlocfilehash: b4e8388c4e3ea855c191cbdfc06621018274ff86
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847593"
---
# <a name="button"></a><span data-ttu-id="5e57c-104">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="5e57c-104">Button</span></span>

![Schaltfläche](images/UX_Hero_Button.jpg)

<span data-ttu-id="5e57c-106">Mit einer Schaltfläche können Ihre Benutzer sofort Aktionen in gemischter Realität auslöst.</span><span class="sxs-lookup"><span data-stu-id="5e57c-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="5e57c-107">In hololens 2 haben Schaltflächen visuelle Hinweise und Kosten, die zur Steigerung der Interaktion mit Benutzern beitragen.</span><span class="sxs-lookup"><span data-stu-id="5e57c-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="5e57c-108">![Schaltfläche mit angezeidem Näherungs Lichteffekt](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="5e57c-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="5e57c-109">**Near Light**</span><span class="sxs-lookup"><span data-stu-id="5e57c-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5e57c-110">![Ausgewählte Schaltfläche mit Fokus Hervorhebungs Effekt](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="5e57c-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="5e57c-111">**Fokus Hervorhebung**</span><span class="sxs-lookup"><span data-stu-id="5e57c-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="5e57c-112">![Die Schaltfläche wird mit dem Komprimierungs Käfig Effekt angezeigt.](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="5e57c-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="5e57c-113">**Komprimieren von Cage**</span><span class="sxs-lookup"><span data-stu-id="5e57c-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5e57c-114">![Die Schaltfläche wird mit dem angezeigten Triggereffekt gedrückt.](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="5e57c-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="5e57c-115">**Pulse on-Triggern**</span><span class="sxs-lookup"><span data-stu-id="5e57c-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="5e57c-116">Schaltfläche im mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="5e57c-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="5e57c-117">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** bietet verschiedene Typen von Schaltflächen-Prefabs, einschließlich Schaltflächen im shellstil für hololens 2 und hololens (1. Gen).</span><span class="sxs-lookup"><span data-stu-id="5e57c-117">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="5e57c-118">Die Prefab-Schaltfläche "hololens 2" enthält mehrere ausführliche Kosten, die zur Verbesserung der Benutzer Zuverlässigkeit beitragen:</span><span class="sxs-lookup"><span data-stu-id="5e57c-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="5e57c-119">Near-based-Hervorhebung</span><span class="sxs-lookup"><span data-stu-id="5e57c-119">Proximity-based highlight</span></span>
* <span data-ttu-id="5e57c-120">Komprimieren des Front-Käfigs</span><span class="sxs-lookup"><span data-stu-id="5e57c-120">Compressing front cage</span></span>
* <span data-ttu-id="5e57c-121">Pulse Effect on-Triggern.</span><span class="sxs-lookup"><span data-stu-id="5e57c-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="5e57c-122">Weitere Anweisungen und angepasste Beispiele finden Sie in der [mrtk-Schaltfläche](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) .</span><span class="sxs-lookup"><span data-stu-id="5e57c-122">Check out the [MRTK - Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="5e57c-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5e57c-123">See also</span></span>

* [<span data-ttu-id="5e57c-124">Cursor</span><span class="sxs-lookup"><span data-stu-id="5e57c-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="5e57c-125">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="5e57c-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="5e57c-126">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="5e57c-126">Button</span></span>](button.md)
* [<span data-ttu-id="5e57c-127">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="5e57c-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="5e57c-128">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="5e57c-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="5e57c-129">Manipulation</span><span class="sxs-lookup"><span data-stu-id="5e57c-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5e57c-130">Handmenü</span><span class="sxs-lookup"><span data-stu-id="5e57c-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="5e57c-131">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="5e57c-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="5e57c-132">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="5e57c-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5e57c-133">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="5e57c-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="5e57c-134">Tastatur</span><span class="sxs-lookup"><span data-stu-id="5e57c-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="5e57c-135">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="5e57c-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="5e57c-136">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="5e57c-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="5e57c-137">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="5e57c-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="5e57c-138">Shader</span><span class="sxs-lookup"><span data-stu-id="5e57c-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="5e57c-139">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="5e57c-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="5e57c-140">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="5e57c-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="5e57c-141">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="5e57c-141">Surface magnetism</span></span>](surface-magnetism.md)
