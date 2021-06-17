---
title: Objektsammlung
description: Die Objektsammlung ist ein Layoutsteuerfeld, mit dem Sie ein Array von Objekten in einer vordefinierten dreidimensionalen Form strukturieren können.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Steuerelemente, Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, Objektsammlung, 2D, 3D, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: fd5629f58e092b33410c833885037582ba5ca4a1
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110139"
---
# <a name="object-collection"></a><span data-ttu-id="a2866-104">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="a2866-104">Object collection</span></span>

![Objektsammlung, die im Periodensystem der Elements-App verwendet wird](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="a2866-106">Die Objektsammlung ist ein Layoutsteuerfeld, mit dem Sie ein Array von Objekten in einer vordefinierten dreidimensionalen Form strukturieren können.</span><span class="sxs-lookup"><span data-stu-id="a2866-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="a2866-107">Es unterstützt verschiedene Oberflächenstile: \*\*Ebene, Zylinder, Kugel und **radiale**.</span><span class="sxs-lookup"><span data-stu-id="a2866-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="a2866-108">Sie können den Radius und die Größe der Objekte und den Abstand zwischen ihnen anpassen.</span><span class="sxs-lookup"><span data-stu-id="a2866-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="a2866-109">Die Objektsammlung unterstützt alle Objekte aus Unity – sowohl 2D als auch 3D.</span><span class="sxs-lookup"><span data-stu-id="a2866-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="a2866-110">Im Mixed Reality **[Toolkit](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)** haben wir Unity-Skripts und Beispiele erstellt, mit denen Sie eine Objektsammlung erstellen können.</span><span class="sxs-lookup"><span data-stu-id="a2866-110">In the **[Mixed Reality Toolkit](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="a2866-111">Beispiele für Objektsammlungen</span><span class="sxs-lookup"><span data-stu-id="a2866-111">Object collection examples</span></span>

<span data-ttu-id="a2866-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) ist eine Beispiel-App, die die Funktionsweise der Objektsammlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="a2866-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="a2866-113">Sie verwendet die Objektsammlung, um 3D-Chemieelementfelder in verschiedenen Formen zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="a2866-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="a2866-114">![Beispiele für Objektsammlungen in der Periodentabelle der Elements-App](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a2866-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="a2866-115">*Beispiele für Objektsammlungen, die im Periodensystem der Beispiel-App "Elemente" gezeigt werden*</span><span class="sxs-lookup"><span data-stu-id="a2866-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="a2866-116">3D-Objekte</span><span class="sxs-lookup"><span data-stu-id="a2866-116">3D objects</span></span>

<span data-ttu-id="a2866-117">Sie können die Objektsammlung verwenden, um importierte 3D-Objekte zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a2866-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="a2866-118">Das folgende Beispiel zeigt eine Ebene und ein Zylinderlayout einiger 3D-Designobjekte.</span><span class="sxs-lookup"><span data-stu-id="a2866-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="a2866-119">![Beispiele für Ebenen- und zylindrische Layouts von 3D-Objekten](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a2866-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="a2866-120">*Beispiele für Ebenen- und zylindrische Layouts von 3D-Objekten*</span><span class="sxs-lookup"><span data-stu-id="a2866-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="a2866-121">2D-Objekte</span><span class="sxs-lookup"><span data-stu-id="a2866-121">2D objects</span></span>

<span data-ttu-id="a2866-122">Sie können auch 2D-Bilder mit Objektsammlung verwenden.</span><span class="sxs-lookup"><span data-stu-id="a2866-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="a2866-123">Die folgenden Beispiele veranschaulichen, wie 2D-Bilder in einem Raster angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="a2866-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Beispiel für 2D-Bilder mit Objektsammlung](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="a2866-125">![Beispiele für die Verwendung der Objektsammlung mit 2D-Bildern](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="a2866-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="a2866-126">*Beispiele für die Verwendung der Objektsammlung mit 2D-Bildern*</span><span class="sxs-lookup"><span data-stu-id="a2866-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a2866-127">Objektsammlung in MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="a2866-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="a2866-128">MRTK – Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="a2866-128">MRTK - Object collection</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)

<br>

---

## <a name="see-also"></a><span data-ttu-id="a2866-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a2866-129">See also</span></span>

* [<span data-ttu-id="a2866-130">Cursor</span><span class="sxs-lookup"><span data-stu-id="a2866-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a2866-131">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="a2866-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a2866-132">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="a2866-132">Button</span></span>](button.md)
* [<span data-ttu-id="a2866-133">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="a2866-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a2866-134">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="a2866-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a2866-135">Manipulation</span><span class="sxs-lookup"><span data-stu-id="a2866-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a2866-136">Handmenü</span><span class="sxs-lookup"><span data-stu-id="a2866-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a2866-137">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="a2866-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a2866-138">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="a2866-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a2866-139">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="a2866-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a2866-140">Tastatur</span><span class="sxs-lookup"><span data-stu-id="a2866-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a2866-141">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="a2866-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a2866-142">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="a2866-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="a2866-143">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="a2866-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="a2866-144">Shader</span><span class="sxs-lookup"><span data-stu-id="a2866-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="a2866-145">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="a2866-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a2866-146">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="a2866-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a2866-147">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="a2866-147">Surface magnetism</span></span>](surface-magnetism.md)