---
title: Schaltfläche
description: Erfahren Sie, wie Sie eine sofortige Aktion mit Schaltflächen auslösen, die eine der grundlegenden Komponenten von Mixed Reality ist.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality, Steuerelemente, Interaktion, Benutzeroberfläche, Benutzeroberfläche, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Schaltfläche
ms.openlocfilehash: ddad8b23950bddd03dd4024497c212d1cc950fb0
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600369"
---
# <a name="button"></a><span data-ttu-id="6caad-104">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="6caad-104">Button</span></span>

![Schaltfläche](images/UX_Hero_Button.jpg)

<span data-ttu-id="6caad-106">Mit einer Schaltfläche können Benutzer sofortige Aktionen in einer Mixed Reality-Umgebung auslösen.</span><span class="sxs-lookup"><span data-stu-id="6caad-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="6caad-107">In HoloLens 2 weisen Schaltflächen visuelle Hinweise und Möglichkeiten auf, die dazu beitragen, das Vertrauen in die Interaktion mit Benutzern zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="6caad-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="6caad-108">![Schaltfläche mit lichter Näherungseffekt](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="6caad-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="6caad-109">**Näherungslicht**</span><span class="sxs-lookup"><span data-stu-id="6caad-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6caad-110">![Ausgewählte Schaltfläche mit hervorgehobener Fokuseffekt](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="6caad-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="6caad-111">**Fokusmarker**</span><span class="sxs-lookup"><span data-stu-id="6caad-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="6caad-112">![Gedrückte Schaltfläche mit angezeigter Komprimierungseffekt](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="6caad-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="6caad-113">**Komprimieren von Gittern**</span><span class="sxs-lookup"><span data-stu-id="6caad-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6caad-114">![Schaltfläche, die gedrückt wird, mit angezeigter Triggerimpfeffekt](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="6caad-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="6caad-115">**Pulse on trigger**</span><span class="sxs-lookup"><span data-stu-id="6caad-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="6caad-116">Schaltfläche im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="6caad-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="6caad-117">**[MRTK für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** bietet verschiedene Arten von Schaltflächenpräfabs, einschließlich Schaltflächen im Shellstil für HoloLens 2 und HoloLens (1. Generation).</span><span class="sxs-lookup"><span data-stu-id="6caad-117">**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="6caad-118">Das Prefab der HoloLens 2-Schaltfläche enthält mehrere detaillierte Angebot, die das Vertrauen der Benutzer verbessern:</span><span class="sxs-lookup"><span data-stu-id="6caad-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="6caad-119">Näherungsbasierte Hervorhebung</span><span class="sxs-lookup"><span data-stu-id="6caad-119">Proximity-based highlight</span></span>
* <span data-ttu-id="6caad-120">Komprimieren von Frontboxen</span><span class="sxs-lookup"><span data-stu-id="6caad-120">Compressing front cage</span></span>
* <span data-ttu-id="6caad-121">Pulse-Effekt auf Trigger.</span><span class="sxs-lookup"><span data-stu-id="6caad-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="6caad-122">Weitere Anweisungen und angepasste Beispiele finden Sie unter [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) – Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="6caad-122">Check out the [MRTK - Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="6caad-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6caad-123">See also</span></span>

* [<span data-ttu-id="6caad-124">Cursor</span><span class="sxs-lookup"><span data-stu-id="6caad-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6caad-125">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="6caad-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="6caad-126">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="6caad-126">Button</span></span>](button.md)
* [<span data-ttu-id="6caad-127">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="6caad-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6caad-128">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="6caad-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="6caad-129">Manipulation</span><span class="sxs-lookup"><span data-stu-id="6caad-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6caad-130">Handmenü</span><span class="sxs-lookup"><span data-stu-id="6caad-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="6caad-131">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="6caad-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="6caad-132">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="6caad-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="6caad-133">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="6caad-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="6caad-134">Tastatur</span><span class="sxs-lookup"><span data-stu-id="6caad-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="6caad-135">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="6caad-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="6caad-136">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="6caad-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="6caad-137">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="6caad-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="6caad-138">Shader</span><span class="sxs-lookup"><span data-stu-id="6caad-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="6caad-139">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="6caad-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="6caad-140">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="6caad-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="6caad-141">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="6caad-141">Surface magnetism</span></span>](surface-magnetism.md)