---
title: Begrenzungsrahmen und App-Leiste
description: Die App-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Grenzen eines Hologramms angezeigt werden.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, Begrenzungsfeld, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5c437b303ec5462179a1ddf43687aa1653419b08
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110097"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="65057-104">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="65057-104">Bounding box and App bar</span></span>
<span data-ttu-id="65057-105">![Bounding ist die Standardschnittstelle für die Objektbearbeitung in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="65057-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="65057-106">Was ist das Begrenzungsfeld?</span><span class="sxs-lookup"><span data-stu-id="65057-106">What is the Bounding box?</span></span>

<span data-ttu-id="65057-107">Bounding ist die Standardschnittstelle für die Objektbearbeitung in Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="65057-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="65057-108">Dieses Feature gibt dem Benutzer einen visuellen Hinweis, dass das Objekt derzeit anpassbar ist.</span><span class="sxs-lookup"><span data-stu-id="65057-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="65057-109">Auf HoloLens 2 arbeitet der Begrenzungsfeld mit direkter Handbearbeitung und reagiert auf die Nähe des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="65057-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="65057-110">Es zeigt visuelles Feedback, das dem Benutzer hilft, den Abstand zum Objekt zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="65057-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="65057-111">Skalieren eines Objekts</span><span class="sxs-lookup"><span data-stu-id="65057-111">Scaling an object</span></span><br>
        <span data-ttu-id="65057-112">Die Ecken des Begrenzungsfelds informieren den Benutzer darüber, dass das Objekt skaliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="65057-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="65057-113">Die Handles folgen einem weit verbreiteten Muster zum Anpassen der Skalierung.</span><span class="sxs-lookup"><span data-stu-id="65057-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="65057-114">Dieser visuelle Hinweis zeigt Benutzern den gesamten Bereich des Objekts an – auch wenn er außerhalb eines Anpassungsmodus nicht sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="65057-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="65057-115">Ohne diese Funktion scheint sich ein Objekt, das an einem anderen Objekt oder einer anderen Oberfläche gezippt ist, so zu verhalten, als ob es sich um ein Objekt herum gab, das nicht dort sein sollte.</span><span class="sxs-lookup"><span data-stu-id="65057-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="65057-116">*Videoschleife: Skalieren eines Objekts über ein Begrenzungsfeld*</span><span class="sxs-lookup"><span data-stu-id="65057-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="65057-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="65057-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="65057-118">![HoloLens-Ansicht zum Skalieren eines Objekts über ein Begrenzungsfeld](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="65057-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="65057-119">Drehen eines Objekts</span><span class="sxs-lookup"><span data-stu-id="65057-119">Rotating an object</span></span><br>
        <span data-ttu-id="65057-120">Die vertikalen rechteckigen Ränder an den Rändern des Begrenzungsfelds sind Drehungsindikatoren.</span><span class="sxs-lookup"><span data-stu-id="65057-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="65057-121">Dies ermöglicht dem Benutzer eine feiner anpassung an die platzierten Hologramme.</span><span class="sxs-lookup"><span data-stu-id="65057-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="65057-122">Sie können nicht nur anpassen und skalieren, sondern sich jetzt auch drehen.</span><span class="sxs-lookup"><span data-stu-id="65057-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="65057-123">*Videoschleife: Drehen eines Objekts über ein Begrenzungsfeld*</span><span class="sxs-lookup"><span data-stu-id="65057-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="65057-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="65057-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="65057-125">![HoloLens-Ansicht zum Drehen eines Objekts über ein Begrenzungsfeld](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="65057-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="65057-126">Visuelles Feedback zur Nähe zu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="65057-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="65057-127">Auf HoloLens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung der Tiefe des Benutzers unterstützen kann.</span><span class="sxs-lookup"><span data-stu-id="65057-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="65057-128">Ein Ring in der Nähe ihrer Fingerspitze wird angezeigt und skaliert herunter, wenn sich die Fingerspitze dem Objekt nähert.</span><span class="sxs-lookup"><span data-stu-id="65057-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="65057-129">Der Ring konvergiert schließlich zu einem Punkt, wenn der gedrückte Zustand erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="65057-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="65057-130">Dieses visuelle Modell hilft dem Benutzer zu verstehen, wie weit er vom Objekt entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="65057-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="65057-131">*Videoschleife: Beispiel für visuelles Feedback basierend auf der Nähe zu einem Begrenzungsfeld*</span><span class="sxs-lookup"><span data-stu-id="65057-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="65057-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="65057-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="65057-133">![Visuelles Feedback zur Nähe](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="65057-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="65057-134">**Informationen zur Entwicklung von Unity-Apps finden Sie unter [Begrenzungsfeld im Mixed Reality Toolkit-Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**</span><span class="sxs-lookup"><span data-stu-id="65057-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="65057-135">Was ist die App-Leiste?</span><span class="sxs-lookup"><span data-stu-id="65057-135">What is the App bar?</span></span>

<span data-ttu-id="65057-136">Die App-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Grenzen eines Hologramms angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="65057-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="65057-137">Dieses Muster wird häufig verwendet, damit Benutzer Hologramme entfernen und anpassen können.</span><span class="sxs-lookup"><span data-stu-id="65057-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="65057-138">Die App-Leiste wurde hauptsächlich als Möglichkeit zum Verwalten platzierter Objekte in der Umgebung eines Benutzers entworfen.</span><span class="sxs-lookup"><span data-stu-id="65057-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="65057-139">In Kombination mit dem Begrenzungsfeld hat ein Benutzer die vollständige Kontrolle darüber, wo und wie Objekte in Mixed Reality ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="65057-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="65057-140">Die App-Leiste folgt dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="65057-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="65057-141">Da dieses Muster mit Objekten verwendet wird, die in der Welt gesperrt sind, wird die App-Leiste immer auf der Objektseite angezeigt, die dem Benutzer am nächsten ist, wenn sich ein Benutzer um das Objekt bewegt.</span><span class="sxs-lookup"><span data-stu-id="65057-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="65057-142">Dieses Feature ist technisch gesehen zwar nicht versiert, erzielt aber effektiv das gleiche Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="65057-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="65057-143">Verhindern, dass die Position eines Benutzers Funktionen verdecken oder blockieren kann, die andernfalls an einem anderen Ort in seiner Umgebung verfügbar wären.</span><span class="sxs-lookup"><span data-stu-id="65057-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="65057-144">*Videoschleife: Wenn Sie ein Hologramm umgehen, folgt die App-Leiste.*</span><span class="sxs-lookup"><span data-stu-id="65057-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="65057-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="65057-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="65057-146">![Gehen Sie ein Hologramm um.</span><span class="sxs-lookup"><span data-stu-id="65057-146">![Walking around a hologram.</span></span> <span data-ttu-id="65057-147">Die App-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="65057-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="65057-148">Begrenzungsfeld im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="65057-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="65057-149">**[MRTK stellt](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Skripts und Prefabs für das Begrenzungsfeld und die App-Leiste zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="65057-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="65057-150">Sie können ein Begrenzungsfeld hinzufügen, indem Sie das BoundingBox.cs-Skript einem beliebigen Objekt zuweisen.</span><span class="sxs-lookup"><span data-stu-id="65057-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="65057-151">MRTK – Begrenzungsfeld</span><span class="sxs-lookup"><span data-stu-id="65057-151">MRTK - Bounding Box</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a><span data-ttu-id="65057-152">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="65057-152">See also</span></span>

* [<span data-ttu-id="65057-153">Cursor</span><span class="sxs-lookup"><span data-stu-id="65057-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="65057-154">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="65057-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="65057-155">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="65057-155">Button</span></span>](button.md)
* [<span data-ttu-id="65057-156">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="65057-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="65057-157">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="65057-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="65057-158">Manipulation</span><span class="sxs-lookup"><span data-stu-id="65057-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="65057-159">Handmenü</span><span class="sxs-lookup"><span data-stu-id="65057-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="65057-160">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="65057-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="65057-161">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="65057-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="65057-162">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="65057-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="65057-163">Tastatur</span><span class="sxs-lookup"><span data-stu-id="65057-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="65057-164">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="65057-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="65057-165">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="65057-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="65057-166">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="65057-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="65057-167">Shader</span><span class="sxs-lookup"><span data-stu-id="65057-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="65057-168">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="65057-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="65057-169">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="65057-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="65057-170">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="65057-170">Surface magnetism</span></span>](surface-magnetism.md)