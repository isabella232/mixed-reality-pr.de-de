---
title: Zeigen und Ausführen mit den Händen
description: Lernen Sie die Grundlagen des Zeigen-und-Ausführen-Eingabemodells für die Unterstützung von Gesten in Mixed Reality-Anwendungen.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Interaktion, Design, HoloLens, Hände, fern, Zeigen und Ausführen, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, Handstrahlen, Objektmanipulation, MRTK, Mixed Reality Toolkit, DoF, Freiheitsgrade
ms.openlocfilehash: 4ee1fabac763a22006b956e46a908ff4d11e395f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009740"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="a70d9-104">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="a70d9-104">Point and commit with hands</span></span>

![Cursor](images/UX_Hero_HandRay.jpg)

<span data-ttu-id="a70d9-106">Das Zeigen und Ausführen mit den Händen ist ein Eingabemodell, mit dem Benutzer auf 2D- und 3D-Inhalte außerhalb ihrer Reichweite zielen, sie auswählen und sie bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="a70d9-106">Point and commit with hands is an input model that lets users target, select, and manipulate out of reach 2D and 3D content.</span></span> <span data-ttu-id="a70d9-107">Diese „ferne“ Interaktionstechnik gibt es nur in der Mixed Reality-Umgebung, denn Menschen interagieren mit der realen Welt natürlicherweise nicht so.</span><span class="sxs-lookup"><span data-stu-id="a70d9-107">This "far" interaction technique is unique to mixed reality because humans don't naturally interact with the real world that way.</span></span> <span data-ttu-id="a70d9-108">Im Superhelden-Film *X-Men* beispielsweise kann die Figur [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) ferne Objekte mit ihren Händen manipulieren.</span><span class="sxs-lookup"><span data-stu-id="a70d9-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) can manipulate far objects in the distance with his hands.</span></span> <span data-ttu-id="a70d9-109">Dies ist etwas, was Menschen in der Realität nicht können.</span><span class="sxs-lookup"><span data-stu-id="a70d9-109">This isn't something humans can do in reality.</span></span> <span data-ttu-id="a70d9-110">Sowohl in HoloLens (AR) als auch in Mixed Reality (MR) werden Benutzer mit dieser magischen Fähigkeit ausgestattet, um die physische Einschränkung der realen Welt zu durchbrechen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power to break the physical constraint of the real world.</span></span> <span data-ttu-id="a70d9-111">Nicht nur macht diese Art von holografischem Erleben Spaß, es macht Benutzerinteraktionen zugleich effektiver und effizienter.</span><span class="sxs-lookup"><span data-stu-id="a70d9-111">Not only is it a fun holographic experience, but it also makes user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="a70d9-112">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="a70d9-112">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="a70d9-113"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="a70d9-113"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="a70d9-114"><a href="../hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a70d9-114"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="a70d9-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a70d9-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="a70d9-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="a70d9-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="a70d9-117">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="a70d9-117">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="a70d9-118">❌ Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="a70d9-118">❌ Not supported</span></span></td>
     <td><span data-ttu-id="a70d9-119">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="a70d9-119">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="a70d9-120">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="a70d9-120">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="a70d9-121">_„Zeigen und Ausführen mit Händen“_ ist eines der neuen Features, welches das neue bewegliche Handverfolgungssystem verwendet.</span><span class="sxs-lookup"><span data-stu-id="a70d9-121">_"Point and commit with hands"_ is one of the new features that use the new articulated hand-tracking system.</span></span> <span data-ttu-id="a70d9-122">Dieses Eingabemodell ist auch das primäre Eingabemodell bei immersiven Headsets mithilfe von Motion-Controllern.</span><span class="sxs-lookup"><span data-stu-id="a70d9-122">This input model is also the primary input model on immersive headsets by using motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="a70d9-123">Handlichtstrahl</span><span class="sxs-lookup"><span data-stu-id="a70d9-123">Hand rays</span></span>

<span data-ttu-id="a70d9-124">In HoloLens 2 haben wir einen Lichtstrahl erzeugt, der aus der Mitte der Handfläche des Benutzers schießt.</span><span class="sxs-lookup"><span data-stu-id="a70d9-124">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="a70d9-125">Dieser Lichtstrahl wird als Erweiterung der Hand behandelt.</span><span class="sxs-lookup"><span data-stu-id="a70d9-125">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="a70d9-126">Ein ringförmiger Cursor befindet sich am Ende des Strahls, um den Punkt anzugeben, an dem der Strahl das Zielobjekt schneidet.</span><span class="sxs-lookup"><span data-stu-id="a70d9-126">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="a70d9-127">Das Objekt, auf dem der Cursor landet, kann dann gestische Befehle von der Hand empfangen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-127">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="a70d9-128">Dieser grundlegende gestische Befehl wird mit dem Daumen und dem Zeigefinger ausgelöst, um das Tippen in die Luft auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-128">This basic gestural command is triggered by using the thumb and index finger to do the air-tap action.</span></span> <span data-ttu-id="a70d9-129">Mithilfe des Handstrahls zum Zeigen und dem Tippen in die Luft zum Ausführen kann der Benutzer eine Schaltfläche oder einen Link aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a70d9-129">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="a70d9-130">Mit weiteren zusammengesetzten Gesten können Benutzer durch Webinhalte navigieren und 3D-Objekte aus der Entfernung bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="a70d9-130">With more composite gestures, users can navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="a70d9-131">Das visuelle Design des Handlichtstrahls sollte auch auf die Zustände beim Zeigen und Ausführen reagieren, wie nachstehend beschrieben und gezeigt:</span><span class="sxs-lookup"><span data-stu-id="a70d9-131">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="a70d9-132">![Zeigen mit Handstrahlen](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-132">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="a70d9-133">**Status „Zeigen“**</span><span class="sxs-lookup"><span data-stu-id="a70d9-133">**Pointing state**</span></span><br>
        <span data-ttu-id="a70d9-134">Im Status *Zeigen* ist der Lichtstrahl eine gestrichelte Linie, und der Cursor hat die Form eines Rings.</span><span class="sxs-lookup"><span data-stu-id="a70d9-134">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a70d9-135">![Ausführen mit Handstrahlen](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-135">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="a70d9-136">**Status „Ausführen“**</span><span class="sxs-lookup"><span data-stu-id="a70d9-136">**Commit state**</span></span><br>
        <span data-ttu-id="a70d9-137">Im Status *Ausführen* wird der Lichtstrahl zu einer durchgezogenen Linie, und der Cursor wird auf einen Punkt verkleinert.</span><span class="sxs-lookup"><span data-stu-id="a70d9-137">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a><span data-ttu-id="a70d9-138">Übergang zwischen nah und fern</span><span class="sxs-lookup"><span data-stu-id="a70d9-138">Transition between near and far</span></span>

<span data-ttu-id="a70d9-139">Anstatt spezifische Gesten wie „Zeigen mit dem Zeigefinger“ zum Lenken des Strahls zu verwenden, haben wir den Strahl so ausgelegt, dass er aus der Mitte der Handfläche des Benutzers entspringt.</span><span class="sxs-lookup"><span data-stu-id="a70d9-139">Instead of using specific gestures like "pointing with index finger" to direct the ray, we designed the ray to comout out from the center of the users' palm.</span></span> <span data-ttu-id="a70d9-140">Auf diese Weise haben wir die fünf Finger für stärker manipulative Gesten wie Zusammendrücken und Greifen freigestellt.</span><span class="sxs-lookup"><span data-stu-id="a70d9-140">This way, we've released and reserved the Five Fingers for more manipulative gestures like pinch and grab.</span></span> <span data-ttu-id="a70d9-141">Mit diesem Entwurf erstellen wir nur ein mentales Modell. Derselbe Satz von Gesten wird für nahe und ferne Interaktionen verwendet.</span><span class="sxs-lookup"><span data-stu-id="a70d9-141">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="a70d9-142">So können Sie die gleiche Greifgeste zum Bearbeiten von Objekten aus unterschiedlichen Entfernungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="a70d9-142">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="a70d9-143">Der Aufruf des Lichtstrahls erfolgt automatisch und basiert auf der Entfernung, wie folgt:</span><span class="sxs-lookup"><span data-stu-id="a70d9-143">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="a70d9-144">![Manipulation in der Nähe](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-144">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="a70d9-145">**Manipulation in der Nähe**</span><span class="sxs-lookup"><span data-stu-id="a70d9-145">**Near manipulation**</span></span><br>
        <span data-ttu-id="a70d9-146">Wenn sich ein Objekt in Armeslänge befindet (ungefähr 50 cm), wird der Lichtstrahl automatisch deaktiviert und regt so die Interaktion aus der Nähe an.</span><span class="sxs-lookup"><span data-stu-id="a70d9-146">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a70d9-147">![Manipulation in der Ferne](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-147">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="a70d9-148">**Manipulation in der Ferne**</span><span class="sxs-lookup"><span data-stu-id="a70d9-148">**Far manipulation**</span></span><br>
        <span data-ttu-id="a70d9-149">Wenn das Objekt mehr als 50 cm entfernt ist, wird der Lichtstrahl aktiviert.</span><span class="sxs-lookup"><span data-stu-id="a70d9-149">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="a70d9-150">Der Übergang sollte reibungslos und nahtlos erfolgen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-150">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="a70d9-151">2D-Tafel – Interaktion</span><span class="sxs-lookup"><span data-stu-id="a70d9-151">2D slate interaction</span></span>

<span data-ttu-id="a70d9-152">Eine 2D-Tafel ist ein holografischer Container, der 2D-App-Inhalte hostet (z. B. einen Webbrowser).</span><span class="sxs-lookup"><span data-stu-id="a70d9-152">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="a70d9-153">Das Entwurfskonzept für die ferne Interaktion mit einer 2D-Tafel verwendet den Handlichtstrahl zum Zielen und das Tippen in die Luft zum Auswählen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-153">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="a70d9-154">Nach dem Zielen mit dem Handlichtstrahl kann der Benutzer in die Luft tippen, um einen Link oder eine Schaltfläche auszulösen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-154">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="a70d9-155">Sie können eine Hand zum „Tippen in die Luft und Ziehen“ verwenden, um den Inhalt einer Tafel nach oben und unten zu scrollen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-155">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="a70d9-156">Mit der relativen Bewegung und der Verwendung von zwei Händen zum „Tippen in die Luft und Ziehen“ können Sie den Inhalt der Tafel vergrößern und verkleinern.</span><span class="sxs-lookup"><span data-stu-id="a70d9-156">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="a70d9-157">Wenn Sie mit dem Handlichtstrahl in die Ecken und auf die Kanten zielen, wird das naheliegendste Bearbeitungsangebot angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a70d9-157">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="a70d9-158">Mit den Bearbeitungsangeboten „Greifen und Ziehen“ kann der Benutzer über das Eckenangebot eine einheitliche Skalierung ausführen und über das Kantenangebot die Tafel neu formatieren.</span><span class="sxs-lookup"><span data-stu-id="a70d9-158">By "grab and drag" manipulation affordances, users can do uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="a70d9-159">Durch Greifen und Ziehen der Hololeiste im oberen Bereich der 2D-Tafel kann der Benutzer die gesamte Tafel verschieben.</span><span class="sxs-lookup"><span data-stu-id="a70d9-159">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="a70d9-160">![2D-Tafel – Interaktion „Klicken“](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-160">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="a70d9-161">**Klicken**</span><span class="sxs-lookup"><span data-stu-id="a70d9-161">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a70d9-162">![2D-Tafel – Interaktion „Scrollen“](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-162">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="a70d9-163">**Scrollen**</span><span class="sxs-lookup"><span data-stu-id="a70d9-163">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a70d9-164">![2D-Tafel – Interaktion „Zoomen“](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-164">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="a70d9-165">**Zoomen**</span><span class="sxs-lookup"><span data-stu-id="a70d9-165">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="a70d9-166">**So bearbeiten Sie die 2D-Tafel**</span><span class="sxs-lookup"><span data-stu-id="a70d9-166">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="a70d9-167">Der Benutzer zeigt mit dem Handlichtstrahl in die Ecken oder auf die Kanten, um das naheliegendste Bearbeitungsangebot anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-167">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="a70d9-168">Durch das Anwenden einer Bearbeitungsgeste kann der Benutzer über das Eckenangebot eine einheitliche Skalierung und über das Kantenangebot eine Formatierung der Tafel vornehmen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-168">By applying a manipulation gesture on the affordance, users can do uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="a70d9-169">Durch das Anwenden einer Bearbeitungsgeste auf die Hololeiste im oberen Bereich der 2D-Tafel kann der Benutzer die gesamte Tafel verschieben.</span><span class="sxs-lookup"><span data-stu-id="a70d9-169">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="a70d9-170">3D-Objektbearbeitung</span><span class="sxs-lookup"><span data-stu-id="a70d9-170">3D object manipulation</span></span>

<span data-ttu-id="a70d9-171">Bei der direkten Bearbeitung hat der Benutzer zwei Möglichkeiten zum Bearbeiten von 3D-Objekten: angebotsbasierte Bearbeitung und Bearbeitung ohne Angebot.</span><span class="sxs-lookup"><span data-stu-id="a70d9-171">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="a70d9-172">Beim Modell „Zeigen und Ausführen“ kann der Benutzer genau die gleichen Aufgaben mithilfe des Handlichtstrahls ausführen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-172">In the point and commit model, users can achieve exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="a70d9-173">Es ist kein zusätzlicher Lernaufwand erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a70d9-173">No extra learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="a70d9-174">Angebotsbasierte Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="a70d9-174">Affordance-based manipulation</span></span>

<span data-ttu-id="a70d9-175">Der Benutzer verwendet den Handlichtstrahl zum Zeigen und Anzeigen des Begrenzungsrahmens und der Bearbeitungsangebote.</span><span class="sxs-lookup"><span data-stu-id="a70d9-175">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="a70d9-176">Der Benutzer kann die Bearbeitungsgeste auf den Begrenzungsrahmen anwenden, um das gesamte Objekt zu verschieben, auf die Kantenangebote, um das Objekt zu drehen, und auf die Eckenangebote, um eine einheitliche Skalierung vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-176">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="a70d9-177">![3D-Objektbearbeitung – Verschieben aus größerer Entfernung](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-177">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="a70d9-178">**Verschieben**</span><span class="sxs-lookup"><span data-stu-id="a70d9-178">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a70d9-179">![3D-Objektbearbeitung – Drehen aus größerer Entfernung](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-179">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="a70d9-180">**Drehen**</span><span class="sxs-lookup"><span data-stu-id="a70d9-180">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a70d9-181">![3D-Objektbearbeitung – Skalieren aus größerer Entfernung](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-181">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="a70d9-182">**Skalieren**</span><span class="sxs-lookup"><span data-stu-id="a70d9-182">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="a70d9-183">Bearbeitung ohne Angebot</span><span class="sxs-lookup"><span data-stu-id="a70d9-183">Non-affordance-based manipulation</span></span>

<span data-ttu-id="a70d9-184">Der Benutzer zeigt mit dem Handlichtstrahl, um den Begrenzungsrahmen anzuzeigen, und wendet dann direkt Bearbeitungsgesten darauf an.</span><span class="sxs-lookup"><span data-stu-id="a70d9-184">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="a70d9-185">Mit einer Hand sind Verschiebung und Drehung des Objekts der Bewegung und Ausrichtung der Hand zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="a70d9-185">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="a70d9-186">Mit zwei Händen kann der Benutzer Verschiebung, Drehung und Skalierung entsprechend der relativen Bewegung der beiden Hände vornehmen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-186">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="a70d9-187">Instinktive Gesten</span><span class="sxs-lookup"><span data-stu-id="a70d9-187">Instinctual gestures</span></span>

<span data-ttu-id="a70d9-188">Das Konzept der instinktiven Gesten für „Zeigen und Ausführen“ entspricht dem für die [direkte Bearbeitung mit den Händen](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="a70d9-188">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="a70d9-189">Die Gesten, die der Benutzer bei einem 3D-Objekt ausführt, werden über das Design der Benutzeroberflächenangebote gesteuert.</span><span class="sxs-lookup"><span data-stu-id="a70d9-189">The gestures users do on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="a70d9-190">Ein kleiner Steuerpunkt beispielsweise kann den Benutzer motivieren, Daumen und Zeigefinger zusammenzuführen, während ein anderer Benutzer möglicherweise alle fünf Finger verwenden möchte, um ein größeres Objekt zu greifen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-190">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to use all Five Fingers to grab a larger object.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="a70d9-191">![Instinktive Gesten – Kleines Objekt aus größerer Entfernung](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-191">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="a70d9-192">**Kleines Objekt**</span><span class="sxs-lookup"><span data-stu-id="a70d9-192">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a70d9-193">![Instinktive Gesten – Mittelgroßes Objekt aus größerer Entfernung](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-193">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="a70d9-194">**Mittelgroßes Objekt**</span><span class="sxs-lookup"><span data-stu-id="a70d9-194">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a70d9-195">![Instinktive Gesten – Großes Objekt aus größerer Entfernung](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-195">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="a70d9-196">**Großes Objekt**</span><span class="sxs-lookup"><span data-stu-id="a70d9-196">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="a70d9-197">Symmetrisches Design für Händen und Controller mit 6 Freiheitsgraden</span><span class="sxs-lookup"><span data-stu-id="a70d9-197">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="a70d9-198">Das Konzept des Zeigens und Ausführens für die ferne Interaktion wurde für das Mixed Reality-Portal (MRP) erstellt und definiert.</span><span class="sxs-lookup"><span data-stu-id="a70d9-198">The concept of point and commit for far interaction was created and defined for the Mixed Reality Portal (MRP).</span></span> <span data-ttu-id="a70d9-199">In diesem Szenario trägt ein Benutzer ein immersives Headset und interagiert mit 3D-Objekten über Motion Controller.</span><span class="sxs-lookup"><span data-stu-id="a70d9-199">In this scenario, a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="a70d9-200">Zum Zeigen auf und Bearbeiten von fernen Objekten schießen die Motion-Controller einen Lichtstrahl ab.</span><span class="sxs-lookup"><span data-stu-id="a70d9-200">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="a70d9-201">zum Ausführen weiterer unterschiedlicher Aktionen gibt es Tasten auf den Controllern.</span><span class="sxs-lookup"><span data-stu-id="a70d9-201">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="a70d9-202">Wir wenden das Interaktionsmodell des Lichtstrahls an und haben diese mit beiden Händen verbunden.</span><span class="sxs-lookup"><span data-stu-id="a70d9-202">We apply the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="a70d9-203">Bei diesem symmetrischen Entwurf braucht der Benutzer, der sich mit MRP auskennt, kein anderes Interaktionsmodell für das Zeigen auf und Bearbeiten von fernen Objekten zu lernen, wenn er HoloLen 2 verwendet (und umgekehrt).</span><span class="sxs-lookup"><span data-stu-id="a70d9-203">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLens 2, and the other way around.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="a70d9-204">![Symmetrischer Entwurf für Lichtstrahlen mit Controllern](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-204">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="a70d9-205">**Controllerlichtstrahlen**</span><span class="sxs-lookup"><span data-stu-id="a70d9-205">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a70d9-206">![Symmetrischer Entwurf für Lichtstrahlen mit Händen](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="a70d9-206">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="a70d9-207">**Handlichtstrahl**</span><span class="sxs-lookup"><span data-stu-id="a70d9-207">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a70d9-208">Handlichtstrahl in MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="a70d9-208">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="a70d9-209">Standardmäßig stellt das MRTK einen vorkonfigurierten Handlichtstrahl ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) zur Verfügung, der den gleichen visuellen Status wie der System-Handlichtstrahl der Shell aufweist.</span><span class="sxs-lookup"><span data-stu-id="a70d9-209">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="a70d9-210">Es wird im Eingabeprofil des MRTK unter „Zeiger“ zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="a70d9-210">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="a70d9-211">In einem immersiven Headset werden dieselben Strahlen für die Motion-Controller verwendet.</span><span class="sxs-lookup"><span data-stu-id="a70d9-211">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="a70d9-212">MRTK – Zeigerprofil</span><span class="sxs-lookup"><span data-stu-id="a70d9-212">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="a70d9-213">MRTK – Eingabesystem</span><span class="sxs-lookup"><span data-stu-id="a70d9-213">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="a70d9-214">MRTK – Zeiger</span><span class="sxs-lookup"><span data-stu-id="a70d9-214">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a><span data-ttu-id="a70d9-215">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a70d9-215">See also</span></span>
* [<span data-ttu-id="a70d9-216">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="a70d9-216">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a70d9-217">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="a70d9-217">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a70d9-218">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="a70d9-218">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a70d9-219">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="a70d9-219">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a70d9-220">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="a70d9-220">Instinctual interactions</span></span>](interaction-fundamentals.md)
