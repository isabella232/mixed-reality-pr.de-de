---
title: Schaltfläche
description: Eine Schaltfläche ermöglicht dem Benutzer das unmittelbare Auslösen einer Aktion. Es ist eine der grundlegenden Komponenten in gemischter Realität.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Gemischte Realität, Steuerelemente, Interaktion, UI, UX, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Schaltfläche
ms.openlocfilehash: c5e52bef8604ba4874b7f4b055107ec0db6b3683
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702856"
---
# <a name="button"></a><span data-ttu-id="e9d04-105">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="e9d04-105">Button</span></span>

![Schaltfläche](images/UX_Hero_Button.jpg)

<span data-ttu-id="e9d04-107">Eine Schaltfläche ermöglicht dem Benutzer das unmittelbare Auslösen einer Aktion.</span><span class="sxs-lookup"><span data-stu-id="e9d04-107">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="e9d04-108">Es ist eine der grundlegenden Komponenten in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="e9d04-108">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="e9d04-109">In hololens 2 bietet eine Schaltfläche viele visuelle Hinweise und Kosten, um die Interaktion des Benutzers zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="e9d04-109">In HoloLens 2, a button has many visual cues and affordances to increase the user's interaction confidence.</span></span> 


:::row:::
    :::column:::
       <span data-ttu-id="e9d04-110">![Verschieben](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="e9d04-110">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="e9d04-111">**Near Light**</span><span class="sxs-lookup"><span data-stu-id="e9d04-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e9d04-112">![Drehen](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="e9d04-112">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="e9d04-113">**Fokus Hervorhebung**</span><span class="sxs-lookup"><span data-stu-id="e9d04-113">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e9d04-114">![Verschieben](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="e9d04-114">![Move](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="e9d04-115">**Komprimieren von Cage**</span><span class="sxs-lookup"><span data-stu-id="e9d04-115">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e9d04-116">![Drehen](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="e9d04-116">![Rotate](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="e9d04-117">**Pulse on-Triggern**</span><span class="sxs-lookup"><span data-stu-id="e9d04-117">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="e9d04-118">Schaltfläche im mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="e9d04-118">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="e9d04-119">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** bietet verschiedene Typen von Schaltflächen-Prefabs.</span><span class="sxs-lookup"><span data-stu-id="e9d04-119">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs.</span></span> <span data-ttu-id="e9d04-120">Sie finden Schaltflächen im shellstil für hololens 2 und hololens (1. Gen) sowie angepasste Beispiele.</span><span class="sxs-lookup"><span data-stu-id="e9d04-120">You can find shell-style buttons for HoloLens 2 and HoloLens (1st gen) as well as customized examples.</span></span> <span data-ttu-id="e9d04-121">Hololens 2 Button Prefab enthält viele ausführliche Kosten, die zur Verbesserung des Vertrauens des Benutzers beitragen.</span><span class="sxs-lookup"><span data-stu-id="e9d04-121">HoloLens 2 button prefab contains a lot of detailed affordances that help improve the user's confidence.</span></span> <span data-ttu-id="e9d04-122">Sie enthält eine near-basierte Hervorhebung, Komprimierung des Front-Käfigs und einen Pulse-Effekt auf den Triggern.</span><span class="sxs-lookup"><span data-stu-id="e9d04-122">It includes proximity-based highlight, compressing front cage, and a pulse effect on trigger.</span></span>

* [<span data-ttu-id="e9d04-123">Mrtk-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="e9d04-123">MRTK - Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)



<br>

---


## <a name="see-also"></a><span data-ttu-id="e9d04-124">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e9d04-124">See also</span></span>

* [<span data-ttu-id="e9d04-125">Cursor</span><span class="sxs-lookup"><span data-stu-id="e9d04-125">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e9d04-126">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="e9d04-126">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="e9d04-127">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="e9d04-127">Button</span></span>](button.md)
* [<span data-ttu-id="e9d04-128">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="e9d04-128">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e9d04-129">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="e9d04-129">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e9d04-130">Manipulation</span><span class="sxs-lookup"><span data-stu-id="e9d04-130">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e9d04-131">Handmenü</span><span class="sxs-lookup"><span data-stu-id="e9d04-131">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="e9d04-132">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="e9d04-132">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="e9d04-133">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="e9d04-133">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e9d04-134">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="e9d04-134">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="e9d04-135">Tastatur</span><span class="sxs-lookup"><span data-stu-id="e9d04-135">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="e9d04-136">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="e9d04-136">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="e9d04-137">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="e9d04-137">Slate</span></span>](slate.md)
* [<span data-ttu-id="e9d04-138">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="e9d04-138">Slider</span></span>](slider.md)
* [<span data-ttu-id="e9d04-139">Shader</span><span class="sxs-lookup"><span data-stu-id="e9d04-139">Shader</span></span>](shader.md)
* [<span data-ttu-id="e9d04-140">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="e9d04-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="e9d04-141">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="e9d04-141">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="e9d04-142">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="e9d04-142">Surface magnetism</span></span>](surface-magnetism.md)
