---
title: Shader
description: Der Standard-Shader von Mixed Reality Toolkit bietet verschiedene Typen von visuellen Effekten, die mit holograms verwendet werden können.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Gemischte Realität, Steuerelemente, Interaktion, UI, UX, Shader, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, visuelle Effekte
ms.openlocfilehash: 08701fb48d633f7de75b74b5e44655c3a01fade8
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848244"
---
# <a name="shader"></a><span data-ttu-id="58e6e-104">Shader</span><span class="sxs-lookup"><span data-stu-id="58e6e-104">Shader</span></span>

![Shader](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="58e6e-106">Da Holographic-Objekte in der realen Umgebung mit physischen Objekten kombiniert werden, ist es wichtig, den Benutzern visuelle Hinweise bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="58e6e-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="58e6e-107">Der Standard-Shader von Mixed Reality Toolkit bietet verschiedene Typen von visuellen Effekten für die Verwendung mit holograms.</span><span class="sxs-lookup"><span data-stu-id="58e6e-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="58e6e-108">Das Schattierungs System verwendet einen einzelnen, flexiblen Shader, um visuelle Elemente zu erzielen, die dem Standard-Shader von Unity ähneln.</span><span class="sxs-lookup"><span data-stu-id="58e6e-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="58e6e-109">Der Shader implementiert [fließende Entwurfs System Prinzipien](https://www.microsoft.com/design/fluent/#/) und bleibt auf gemischten Reality-Geräten leistungsfähig.</span><span class="sxs-lookup"><span data-stu-id="58e6e-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="58e6e-110">Beispiele für visuelle Effekte mit dem mrtk-Standard-Shader (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="58e6e-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="58e6e-111">![Verschieben](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="58e6e-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="58e6e-112">**Near Light**</span><span class="sxs-lookup"><span data-stu-id="58e6e-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="58e6e-113">![Drehen](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="58e6e-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="58e6e-114">**Rahmen hell**</span><span class="sxs-lookup"><span data-stu-id="58e6e-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="58e6e-115">Standard-Shader in mrtk für Unity</span><span class="sxs-lookup"><span data-stu-id="58e6e-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="58e6e-116">Mrtk-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="58e6e-116">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

<br>

---

## <a name="see-also"></a><span data-ttu-id="58e6e-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="58e6e-117">See also</span></span>

* [<span data-ttu-id="58e6e-118">Cursor</span><span class="sxs-lookup"><span data-stu-id="58e6e-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="58e6e-119">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="58e6e-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="58e6e-120">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="58e6e-120">Button</span></span>](button.md)
* [<span data-ttu-id="58e6e-121">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="58e6e-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="58e6e-122">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="58e6e-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="58e6e-123">Manipulation</span><span class="sxs-lookup"><span data-stu-id="58e6e-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="58e6e-124">Handmenü</span><span class="sxs-lookup"><span data-stu-id="58e6e-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="58e6e-125">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="58e6e-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="58e6e-126">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="58e6e-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="58e6e-127">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="58e6e-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="58e6e-128">Tastatur</span><span class="sxs-lookup"><span data-stu-id="58e6e-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="58e6e-129">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="58e6e-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="58e6e-130">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="58e6e-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="58e6e-131">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="58e6e-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="58e6e-132">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="58e6e-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="58e6e-133">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="58e6e-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="58e6e-134">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="58e6e-134">Surface magnetism</span></span>](surface-magnetism.md)
