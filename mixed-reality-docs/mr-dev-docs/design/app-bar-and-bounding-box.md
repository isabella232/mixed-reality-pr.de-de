---
title: Begrenzungsrahmen und App-Leiste
description: Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines holograms angezeigt werden.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, Begrenzungsfeld, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 0f94aa3842afbfbd544716b801c7cb88d7be3abc
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847648"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="da209-104">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="da209-104">Bounding box and App bar</span></span>
<span data-ttu-id="da209-105">![Das Begrenzungs Zeichen ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität.](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="da209-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="da209-106">Was ist das umgebende Feld?</span><span class="sxs-lookup"><span data-stu-id="da209-106">What is the Bounding box?</span></span>

<span data-ttu-id="da209-107">Das Begrenzungs Zeichen ist die Standardschnittstelle für die Objekt Bearbeitung in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="da209-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="da209-108">Diese Funktion bietet dem Benutzer einen visuellen Hinweis darauf, dass das Objekt derzeit anpassbar ist.</span><span class="sxs-lookup"><span data-stu-id="da209-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="da209-109">Bei hololens 2 funktioniert das umgebende Feld mit direkter Hand Manipulation und antwortet auf die Nähe des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="da209-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="da209-110">Es zeigt visuelles Feedback, um dem Benutzer zu helfen, den Abstand zum Objekt zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="da209-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="da209-111">Skalieren eines Objekts</span><span class="sxs-lookup"><span data-stu-id="da209-111">Scaling an object</span></span><br>
        <span data-ttu-id="da209-112">In den Ecken des umgebenden Felds wird dem Benutzer mitgeteilt, dass das Objekt skaliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="da209-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="da209-113">Die Handles folgen einem weit verbreiteten Muster zur Anpassung der Skalierung.</span><span class="sxs-lookup"><span data-stu-id="da209-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="da209-114">Dieser visuelle Hinweis zeigt Benutzern den gesamten Bereich des Objekts an – auch dann, wenn Sie außerhalb eines Anpassungsmodus nicht sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="da209-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="da209-115">Ohne diese Funktion kann ein an ein anderes Objekt oder eine andere Oberfläche angedockte Objekt scheinbar so aussehen, als würde es sich in diesem Bereich befinden.</span><span class="sxs-lookup"><span data-stu-id="da209-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="da209-116">*Video Schleife: Skalieren eines Objekts per Begrenzungs Rahmen*</span><span class="sxs-lookup"><span data-stu-id="da209-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="da209-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="da209-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="da209-118">![Hololens zeigt das Skalieren eines Objekts über ein Begrenzungsfeld an](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="da209-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="da209-119">Drehen eines Objekts</span><span class="sxs-lookup"><span data-stu-id="da209-119">Rotating an object</span></span><br>
        <span data-ttu-id="da209-120">Die vertikalen rechteckigen Anlagen an den Rändern des umgebenden Felds sind Rotations Indikatoren.</span><span class="sxs-lookup"><span data-stu-id="da209-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="da209-121">Dies ermöglicht dem Benutzer eine präzisere Anpassung der platzierten holograms.</span><span class="sxs-lookup"><span data-stu-id="da209-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="da209-122">Sie können nicht nur angepasst und skaliert werden, sondern auch jetzt drehen.</span><span class="sxs-lookup"><span data-stu-id="da209-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="da209-123">*Video Schleife: Drehen eines Objekts über das umgebende Feld*</span><span class="sxs-lookup"><span data-stu-id="da209-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="da209-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="da209-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="da209-125">![Hololens-Sicht der Drehung eines Objekts über das umgebende Feld](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="da209-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="da209-126">Visuelles Feedback in der Nähe von hololens 2</span><span class="sxs-lookup"><span data-stu-id="da209-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="da209-127">Auf hololens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung von tiefen durch den Benutzer unterstützen kann.</span><span class="sxs-lookup"><span data-stu-id="da209-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="da209-128">Ein Ring in der Nähe des fingerabbilds wird angezeigt und herunterskaliert, wenn sich der Fingertipp näher an das Objekt anpasst.</span><span class="sxs-lookup"><span data-stu-id="da209-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="da209-129">Der Ring wird schließlich in einen Punkt konvergiert, wenn der gedrückte Zustand erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="da209-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="da209-130">Diese visuelle Visualisierung unterstützt den Benutzer dabei, zu verstehen, wie weit Sie aus dem-Objekt stammen.</span><span class="sxs-lookup"><span data-stu-id="da209-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="da209-131">*Video Schleife: Beispiel für visuelles Feedback basierend auf der Nähe eines umgebenden Felds*</span><span class="sxs-lookup"><span data-stu-id="da209-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="da209-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="da209-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="da209-133">![Visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="da209-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="da209-134">**Informationen zur Entwicklung von Unity-apps finden Sie im Abschnitt zum umgebenden [Feld im Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="da209-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="da209-135">Was ist die APP-Leiste?</span><span class="sxs-lookup"><span data-stu-id="da209-135">What is the App bar?</span></span>

<span data-ttu-id="da209-136">Die APP-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Grenzen eines holograms angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="da209-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="da209-137">Dieses Muster wird häufig verwendet, um Benutzern das Entfernen und Anpassen von holograms zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="da209-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="da209-138">Die APP-Leiste wurde primär als eine Möglichkeit zum Verwalten von platzierten Objekten in der Umgebung eines Benutzers entwickelt.</span><span class="sxs-lookup"><span data-stu-id="da209-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="da209-139">In Verbindung mit dem umgebenden Feld hat ein Benutzer vollständige Kontrolle darüber, wo und wie Objekte in gemischter Realität ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="da209-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="da209-140">Die APP-Leiste folgt dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="da209-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="da209-141">Da dieses Muster mit Objekten verwendet wird, die in der Welt gesperrt sind, wird die APP-Leiste immer auf der Seite der Objekte angezeigt, die dem Benutzer am nächsten ist, wenn sich der Benutzer um das Objekt bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="da209-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="da209-142">Diese Funktion kann zwar nicht technisch abgerechnet werden, aber das gleiche Ergebnis erzielt.</span><span class="sxs-lookup"><span data-stu-id="da209-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="da209-143">Verhindern, dass die Position eines Benutzers Funktionen sperrt oder blockiert, die andernfalls an einem anderen Speicherort in Ihrer Umgebung verfügbar wären.</span><span class="sxs-lookup"><span data-stu-id="da209-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="da209-144">*Video Schleife: Durchlaufen eines Hologram, der APP-Leiste folgt*</span><span class="sxs-lookup"><span data-stu-id="da209-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="da209-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="da209-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="da209-146">![Durchlaufen eines holograms.</span><span class="sxs-lookup"><span data-stu-id="da209-146">![Walking around a hologram.</span></span> <span data-ttu-id="da209-147">Die APP-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="da209-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="da209-148">Begrenzungsfeld in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="da209-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="da209-149">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts und Prefabs für das umgebende Feld und die APP-Leiste bereit.</span><span class="sxs-lookup"><span data-stu-id="da209-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="da209-150">Sie können ein Begrenzungsfeld hinzufügen, indem Sie das BoundingBox.cs-Skript einem beliebigen Objekt zuweisen.</span><span class="sxs-lookup"><span data-stu-id="da209-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="da209-151">Mrtk-Begrenzungsfeld</span><span class="sxs-lookup"><span data-stu-id="da209-151">MRTK - Bounding Box</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="da209-152">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="da209-152">See also</span></span>

* [<span data-ttu-id="da209-153">Cursor</span><span class="sxs-lookup"><span data-stu-id="da209-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="da209-154">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="da209-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="da209-155">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="da209-155">Button</span></span>](button.md)
* [<span data-ttu-id="da209-156">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="da209-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="da209-157">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="da209-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="da209-158">Manipulation</span><span class="sxs-lookup"><span data-stu-id="da209-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="da209-159">Handmenü</span><span class="sxs-lookup"><span data-stu-id="da209-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="da209-160">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="da209-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="da209-161">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="da209-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="da209-162">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="da209-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="da209-163">Tastatur</span><span class="sxs-lookup"><span data-stu-id="da209-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="da209-164">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="da209-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="da209-165">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="da209-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="da209-166">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="da209-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="da209-167">Shader</span><span class="sxs-lookup"><span data-stu-id="da209-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="da209-168">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="da209-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="da209-169">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="da209-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="da209-170">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="da209-170">Surface magnetism</span></span>](surface-magnetism.md)
