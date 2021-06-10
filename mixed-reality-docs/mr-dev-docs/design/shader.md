---
title: Shader
description: Erfahren Sie, wie der Mixed Reality Toolkit Standard-Shader verschiedene Arten von visuellen Effekten bereitstellt, die mit Hologrammen in Ihren Mixed Reality-Apps verwendet werden können.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality, Steuerelemente, Interaktion, Benutzeroberfläche, Benutzeroberfläche, Shader, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, visuelle Effekte
ms.openlocfilehash: 9a60c5065ddb5bcf410bb43b318575da50f7ccf8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600179"
---
# <a name="shader"></a><span data-ttu-id="bf663-104">Shader</span><span class="sxs-lookup"><span data-stu-id="bf663-104">Shader</span></span>

![Shader](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="bf663-106">Da holografische Objekte mit physischen Objekten in der realen Umgebung kombiniert werden, ist es wichtig, dem Benutzer visuelle Hinweise bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="bf663-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="bf663-107">Der Mixed Reality Toolkit Standard-Shader bietet verschiedene Arten von visuellen Effekten für die Verwendung mit Hologrammen.</span><span class="sxs-lookup"><span data-stu-id="bf663-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="bf663-108">Das Schattierungssystem verwendet einen einzelnen, flexiblen Shader, um visuelle Elemente zu erzielen, die dem Standard-Shader von Unity ähneln.</span><span class="sxs-lookup"><span data-stu-id="bf663-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="bf663-109">Der Shader implementiert [Fluent Design System Prinzipien](https://www.microsoft.com/design/fluent/#/) und bleibt auf Mixed Reality-Geräten performant.</span><span class="sxs-lookup"><span data-stu-id="bf663-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="bf663-110">Beispiele für visuelle Effekte mit dem STANDARD-Shader MRTK (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="bf663-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="bf663-111">![Verschieben](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf663-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="bf663-112">**Näherungslicht**</span><span class="sxs-lookup"><span data-stu-id="bf663-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="bf663-113">![Drehen](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf663-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="bf663-114">**Rahmenlicht**</span><span class="sxs-lookup"><span data-stu-id="bf663-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="bf663-115">Standard-Shader im MRTK für Unity</span><span class="sxs-lookup"><span data-stu-id="bf663-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="bf663-116">MRTK – Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="bf663-116">MRTK - Standard shader</span></span>](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="bf663-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bf663-117">See also</span></span>

* [<span data-ttu-id="bf663-118">Cursor</span><span class="sxs-lookup"><span data-stu-id="bf663-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="bf663-119">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="bf663-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="bf663-120">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="bf663-120">Button</span></span>](button.md)
* [<span data-ttu-id="bf663-121">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="bf663-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="bf663-122">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="bf663-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="bf663-123">Manipulation</span><span class="sxs-lookup"><span data-stu-id="bf663-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="bf663-124">Handmenü</span><span class="sxs-lookup"><span data-stu-id="bf663-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="bf663-125">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="bf663-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="bf663-126">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="bf663-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="bf663-127">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="bf663-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="bf663-128">Tastatur</span><span class="sxs-lookup"><span data-stu-id="bf663-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="bf663-129">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="bf663-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="bf663-130">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="bf663-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="bf663-131">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="bf663-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="bf663-132">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="bf663-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="bf663-133">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="bf663-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="bf663-134">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="bf663-134">Surface magnetism</span></span>](surface-magnetism.md)