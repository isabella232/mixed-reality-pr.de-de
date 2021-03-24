---
title: Direkte Manipulation mit den Händen
description: Erfahren Sie mehr über direkte Manipulation, ein Eingabemodell, bei dem Benutzer Hologramme direkt mit den Händen berühren.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Anvisieren, Zielen per Anvisieren, Interaktion, Design, Eingabe, Hände nah beieinander, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit, Taste, Collider, Begrenzungsrahmen, 2D, instinktive Gesten
ms.openlocfilehash: 8316452b8308e159612a81d097c352cf1d935362
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "101759322"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="8fc5f-104">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="8fc5f-104">Direct manipulation with hands</span></span>

![Schaltfläche](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="8fc5f-106">Die direkte Manipulation ist ein Eingabemodell, bei dem Hologramme direkt mit den Händen berührt werden.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="8fc5f-107">Die Idee hinter diesem Konzept ist, dass sich Objekte wie in der realen Welt verhalten.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="8fc5f-108">Schaltflächen können einfach durch Drücken aktiviert werden, Objekte können durch Greifen aufgenommen werden und 2D-Inhalte verhalten sich wie ein virtueller Touchscreen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="8fc5f-109">Die direkte Manipulation ist angebotsbasiert, d. h. benutzerfreundlich.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="8fc5f-110">Es gibt keine symbolischen Gesten, die den Benutzern vermittelt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="8fc5f-111">Alle Interaktionen basieren auf einem visuellen Element, das Sie berühren oder greifen können.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="8fc5f-112">Sie gilt als „nahes“ Eingabemodell, d. h. es wird am besten für die Interaktion mit Inhalten verwendet, die innerhalb der Reichweite der Arme liegen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="8fc5f-113">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="8fc5f-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="8fc5f-114"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="8fc5f-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="8fc5f-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8fc5f-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="8fc5f-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="8fc5f-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="8fc5f-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8fc5f-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="8fc5f-118">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="8fc5f-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="8fc5f-119">❌ Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="8fc5f-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="8fc5f-120">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="8fc5f-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="8fc5f-121">➕ Unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-121">➕ Supported.</span></span>  <span data-ttu-id="8fc5f-122">Für die Benutzeroberfläche empfehlen wir stattdessen <a href="point-and-commit.md">Zeigen und Ausführen mit den Händen</a>.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="8fc5f-123">Die direkte Manipulation ist ein primäres Eingabemodell für HoloLens 2 und nutzt das neue artikulierte Handtracking-System.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="8fc5f-124">Das Eingabemodell ist auch bei immersiven Headsets über Motion-Controller verfügbar, wird aber nicht als primäre Möglichkeit zur Interaktion außerhalb der Objektmanipulation empfohlen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="8fc5f-125">Die direkte Manipulation ist bei HoloLens (1. Generation) nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="8fc5f-126">Kollisionsfähige Fingerspitze</span><span class="sxs-lookup"><span data-stu-id="8fc5f-126">Collidable fingertip</span></span>

<span data-ttu-id="8fc5f-127">Bei HoloLens 2 werden die Hände des Benutzers als Skelettmodelle der linken und rechten Hand erkannt und interpretiert.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="8fc5f-128">Um die Idee, Hologramme direkt mit den Händen zu berühren, zu implementieren, könnten idealerweise fünf Collider an fünf Fingerspitzen der einzelnen Handskelettmodelle angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="8fc5f-129">Aufgrund der fehlenden taktilen Rückmeldung können jedoch 10 kollisionsfähige Fingerspitzen unerwartete und unvorhersehbare Kollisionen mit Hologrammen verursachen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-129">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="8fc5f-130">Wir empfehlen, nur einen Collider an jedem Zeigefinger anzufügen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-130">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="8fc5f-131">Die kollisionsfähigen Zeigefingerspitzen können trotzdem als aktive Berührungspunkte für verschiedene Touchgesten dienen, die andere Finger einbeziehen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="8fc5f-132">Zu den Touchgesten gehören das Drücken mit einem Finger, das Tippen mit einem Finger, das Drücken mit zwei Fingern und das Drücken mit fünf Fingern, wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="8fc5f-132">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8fc5f-133">![Kollisionsfähige Fingerspitze](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-133">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-134">**Kollisionsfähige Fingerspitze**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-134">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-135">![Drücken mit einem Finger](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-135">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="8fc5f-136">**Drücken mit einem Finger**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-136">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-137">![Tippen mit einem Finger](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-137">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-138">**Tippen mit einem Finger**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-138">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-139">![Drücken mit fünf Fingern](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-139">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-140">**Drücken mit fünf Fingern**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-140">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="8fc5f-141">Kugel-Collider</span><span class="sxs-lookup"><span data-stu-id="8fc5f-141">Sphere collider</span></span>

<span data-ttu-id="8fc5f-142">Anstelle einer zufälligen generischen Form wird empfohlen, einen Kugel-Collider zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-142">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="8fc5f-143">Anschließend können Sie diesen visuell rendern, um bessere Hinweise für die Zielbestimmung im Nahbereich zu bieten.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-143">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="8fc5f-144">Der Durchmesser der Kugel muss der Dicke des Zeigefingers entsprechen, um die Genauigkeit bei der Toucheingabe zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-144">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="8fc5f-145">Die Variable für die Fingerdicke lässt sich durch den Aufruf der Hand-API einfacher abrufen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-145">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="8fc5f-146">Fingerspitzencursor</span><span class="sxs-lookup"><span data-stu-id="8fc5f-146">Fingertip cursor</span></span>

<span data-ttu-id="8fc5f-147">Zusätzlich zum Rendern einer kollisionsfähigen Kugel an der Zeigefingerspitze haben wir einen erweiterten Fingerspitzencursor entwickelt, um ein besseres Erlebnis bei der Bestimmung nahegelegener Ziele zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-147">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="8fc5f-148">Es handelt sich um einen ringförmigen Cursor, der an der Zeigefingerspitze angebracht ist.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-148">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="8fc5f-149">Entsprechend der Nähe reagiert er hinsichtlich Ausrichtung und Größe dynamisch auf ein Ziel, wie unten beschrieben:</span><span class="sxs-lookup"><span data-stu-id="8fc5f-149">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="8fc5f-150">Wenn sich ein Zeigefinger auf ein Hologramm zubewegt, befindet sich der Cursor immer parallel zur Oberfläche des Hologramms und verkleinert seine Größe.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-150">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="8fc5f-151">Sobald der Finger die Oberfläche berührt, schrumpft der Cursor zu einem Punkt und gibt ein Toucheingabeereignis aus.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-151">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="8fc5f-152">Mit interaktiven Feedback können Benutzer eine hohe Genauigkeit bei Aufgaben zur Zielbestimmung im Nahbereich erreichen, z. B. das Auslösen eines Hyperlinks oder das Drücken einer Schaltfläche, wie nachfolgend veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-152">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="8fc5f-153">![Fingerspitzencursor – fern](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-153">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-154">**Fingerspitzencursor – fern**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-154">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-155">![Fingerspitzencursor – nah](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-155">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="8fc5f-156">**Fingerspitzencursor – nah**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-156">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-157">![Fingerspitzencursor – Kontakt](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-157">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-158">**Fingerspitzencursor – Kontakt**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-158">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="8fc5f-159">Begrenzungsrahmen mit Näherungsshader</span><span class="sxs-lookup"><span data-stu-id="8fc5f-159">Bounding box with proximity shader</span></span>

<span data-ttu-id="8fc5f-160">Das Hologramm selbst erfordert auch die Fähigkeit, sowohl visuelles als auch akustisches Feedback zu liefern, um den Mangel an taktilem Feedback auszugleichen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-160">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="8fc5f-161">Dazu erstellen wir das Konzept eines Begrenzungsrahmens mit einem Näherungsshader.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-161">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="8fc5f-162">Ein Begrenzungsrahmen ist ein minimaler volumetrischer Bereich, der ein 3D-Objekt umgibt.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-162">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="8fc5f-163">Der Begrenzungsrahmen verfügt über einen interaktiven Renderingmechanismus, der als Näherungsshader bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-163">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="8fc5f-164">Der Näherungsshader verhält sich wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8fc5f-164">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8fc5f-165">![Hover (fern) mit visuellem Feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-165">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-166">**Hover (fern)**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-166">**Hover (far)**</span></span><br>
       <span data-ttu-id="8fc5f-167">Wenn sich der Zeigefinger innerhalb eines Bereichs befindet, wird ein Fingerspitzenspotlight auf die Oberfläche des Begrenzungsrahmens gerichtet.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-167">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-168">![Hover (nah) mit visuellem Feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-168">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="8fc5f-169">**Hover (nah)**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-169">**Hover (near)**</span></span><br>
        <span data-ttu-id="8fc5f-170">Wenn sich die Fingerspitze der Oberfläche nähert, schrumpft das Spotlight.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-170">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-171">![Kontakt beginnt](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-171">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-172">**Kontakt beginnt**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-172">**Contact begins**</span></span><br>
       <span data-ttu-id="8fc5f-173">Sobald die Fingerspitze die Oberfläche berührt, wechselt der gesamte Begrenzungsrahmen die Farbe oder erzeugt einen visuellen Effekt, um den Toucheingabezustand zu reflektieren.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-173">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-174">![Kontakt endet](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-174">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-175">**Kontakt endet**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-175">**Contact ends**</span></span><br>
       <span data-ttu-id="8fc5f-176">Es kann auch ein Soundeffekt aktiviert werden, um das visuelle Feedback der Toucheingabe zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-176">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="8fc5f-177">Drückbare Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="8fc5f-177">Pressable button</span></span>

<span data-ttu-id="8fc5f-178">Mit einer kollisionsfähigen Fingerspitze sind die Benutzer jetzt bereit, mit einer grundlegenden holografischen Benutzeroberflächenkomponente, z. B. einer drückbaren Schaltfläche, zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-178">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="8fc5f-179">Eine drückbare Schaltfläche ist eine holografische Schaltfläche, die auf einen direkten Fingerdruck angepasst ist.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-179">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="8fc5f-180">Da es an taktilem Feedback mangelt, setzt eine drückbare Schaltfläche wiederum einige Mechanismen ein, um auf dem taktilen Feedback basierende Probleme zu beheben.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-180">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="8fc5f-181">Der erste Mechanismus ist ein Begrenzungsrahmen mit einem Näherungsshader, wie er im vorherigen Abschnitt beschrieben wurde.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-181">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="8fc5f-182">Er vermittelt Benutzern ein besseres Gefühl von Nähe, wenn sie sich einer Schaltfläche nähern und mit ihr Kontakt aufnehmen können.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-182">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="8fc5f-183">Der zweite Mechanismus ist die Absenkung.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-183">The second mechanism is depression.</span></span> <span data-ttu-id="8fc5f-184">Absenkung erzeugt ein Gefühl des Niederdrückens, nachdem eine Fingerspitze die Schaltfläche berührt hat.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-184">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="8fc5f-185">Der Mechanismus stellt sicher, dass sich die Schaltfläche mit der Fingerspitze eng entlang der Tiefenachse bewegt.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-185">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="8fc5f-186">Die Schaltfläche kann ausgelöst werden, wenn sie eine gewählte Tiefe erreicht (beim Drücken) oder die Tiefe wieder verlässt (beim Loslassen), nachdem sie passiert wurde.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-186">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="8fc5f-187">Der Soundeffekt sollte hinzugefügt werden, um das Feedback zu verbessern, wenn die Schaltfläche ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-187">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8fc5f-188">![Drückbare Schaltfläche – fern](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-188">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-189">**Finger ist weit entfernt**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-189">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-190">![Drückbare Schaltfläche – nah](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-190">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="8fc5f-191">**Finger nähert sich**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-191">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-192">![Drückbare Schaltfläche – Kontakt beginnt](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-192">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-193">**Kontakt beginnt**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-193">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-194">![Drückbare Schaltfläche – Drücken](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-194">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-195">**Nach unten drücken**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-195">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="8fc5f-196">2D-Tafel – Interaktion</span><span class="sxs-lookup"><span data-stu-id="8fc5f-196">2D slate interaction</span></span>

<span data-ttu-id="8fc5f-197">Eine 2D-[Tafel](slate.md) ist ein holografischer Container, der zum Hosten von 2D-App-Inhalten verwendet wird (z. B. ein Webbrowser).</span><span class="sxs-lookup"><span data-stu-id="8fc5f-197">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="8fc5f-198">Das Konzept für die Interaktion mit einer 2D-Tafel durch direkte Manipulation ist das gleiche wie für die Interaktion mit einem physischen Touchscreen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-198">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="8fc5f-199">So interagieren Sie mit dem Tafelkontakt</span><span class="sxs-lookup"><span data-stu-id="8fc5f-199">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8fc5f-200">![Toucheingabe](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-200">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-201">**Toucheingabe**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-201">**Touch**</span></span><br>
       <span data-ttu-id="8fc5f-202">Verwenden Sie einen Zeigefinger, um einen Link oder eine Schaltfläche zu drücken.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-202">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-203">![Scrollen](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-203">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="8fc5f-204">**Scrollen**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-204">**Scroll**</span></span><br>
        <span data-ttu-id="8fc5f-205">Verwenden Sie einen Zeigefinger, um einen Tafelinhalt nach oben und unten zu scrollen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-205">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-206">![Zoomen](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-207">**Zoomen**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-207">**Zoom**</span></span><br>
       <span data-ttu-id="8fc5f-208">Die zwei Zeigefinger des Benutzers werden verwendet, um den Tafelinhalt entsprechend der relativen Bewegung der Finger zu vergrößern oder zu verkleinern.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-208">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="8fc5f-209">So bearbeiten Sie die eigentliche 2D-Tafel</span><span class="sxs-lookup"><span data-stu-id="8fc5f-209">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8fc5f-210">![Grafik mit der Darstellung des Features zum Greifen und Ziehen](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-210">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-211">**Verschieben**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-211">**Move**</span></span><br>
       <span data-ttu-id="8fc5f-212">Bewegen Sie Ihre Hände in Richtung von Ecken und Kanten, um die nächstgelegenen Manipulationsangebote zu enthüllen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-212">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="8fc5f-213">Greifen Sie die Hololeiste im oberen Bereich der 2D-Tafel, mit der Sie die gesamte Tafel verschieben können.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-213">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-214">![Grafik mit Darstellung der Skalierungsfunktion](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-214">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="8fc5f-215">**Skalierung**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-215">**Scale**</span></span><br>
        <span data-ttu-id="8fc5f-216">Greifen Sie die Manipulationsangebote, und führen Sie über die Eckenangebote eine einheitliche Skalierung aus.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-216">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-217">![Neuanordnen](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-217">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-218">**Neuanordnen**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-218">**Reflow**</span></span><br>
       <span data-ttu-id="8fc5f-219">Greifen Sie die Manipulationsangebote, und führen Sie über die Eckenangebote die Neuanordnung aus.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-219">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="8fc5f-220">3D-Objektbearbeitung</span><span class="sxs-lookup"><span data-stu-id="8fc5f-220">3D object manipulation</span></span>

<span data-ttu-id="8fc5f-221">Bei HoloLens 2 können Benutzer ihre Hände in die Lage versetzen, holografische 3D-Objekte zu steuern und zu bearbeiten, indem sie auf die einzelnen 3D-Objekte einen Begrenzungsrahmen anwenden.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-221">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="8fc5f-222">Der Begrenzungsrahmen sorgt durch seinen Näherungsshader für eine bessere Tiefenwahrnehmung.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-222">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="8fc5f-223">Mit dem Begrenzungsrahmen gibt es zwei Konstruktionsansätze für die 3D-Objektbearbeitung.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-223">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="8fc5f-224">Angebotsbasierte Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="8fc5f-224">Affordance-based manipulation</span></span>

<span data-ttu-id="8fc5f-225">Angebotsbasierte Bearbeitung gestattet es Ihnen, das 3D-Objekt durch einen Begrenzungsrahmen zusammen mit dem diesen umgebenden Bearbeitungsangeboten zu manipulieren.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-225">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="8fc5f-226">![Grafik mit der Darstellung von Begrenzungsrahmen und Verschiebefeature eines Objekts](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-226">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-227">**Verschieben**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-227">**Move**</span></span><br>
       <span data-ttu-id="8fc5f-228">Sobald sich die Hand eines Benutzers in der Nähe eines 3D-Objekts befindet, werden der Begrenzungsrahmen und das nächstgelegene Angebot angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-228">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="8fc5f-229">Benutzer können den Begrenzungsrahmen greifen, um das gesamte Objekt zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-229">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-230">![Grafik mit der Darstellung eines Benutzers, der die Kante eines Objekts greift, um es zu drehen](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-230">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="8fc5f-231">**Drehen**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-231">**Rotate**</span></span><br>
        <span data-ttu-id="8fc5f-232">Benutzer können zum Drehen die Eckenangebote greifen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-232">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-233">![Grafik mit der Darstellung eines Benutzers, der die Ecke eines Objekts greift, um es zu skalieren](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-233">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-234">**Skalierung**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-234">**Scale**</span></span><br>
       <span data-ttu-id="8fc5f-235">Benutzer können die Eckenangebote greifen, um eine einheitliche Skalierung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-235">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="8fc5f-236">Bearbeitung ohne Angebot</span><span class="sxs-lookup"><span data-stu-id="8fc5f-236">Non-affordance-based manipulation</span></span>

<span data-ttu-id="8fc5f-237">Bei der Bearbeitung ohne Angebot werden dem Begrenzungsrahmen keine Angebote angefügt.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-237">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="8fc5f-238">Benutzer können den Begrenzungsrahmen nur anzeigen und dann direkt mit ihm interagieren.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-238">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="8fc5f-239">Wenn der Begrenzungsrahmen mit einer Hand gegriffen wird, sind Verschiebung und Drehung des Objekts der Bewegung und Ausrichtung der Hand zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-239">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="8fc5f-240">Wenn das Objekt mit zwei Händen gegriffen wird, kann der Benutzer Verschiebung, Drehung und Skalierung entsprechend der relativen Bewegung der beiden Hände vornehmen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-240">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="8fc5f-241">Bestimmte Bearbeitungen erfordern Präzision.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-241">Specific manipulation requires precision.</span></span> <span data-ttu-id="8fc5f-242">Wir empfehlen, dass Sie **angebotsbasierter Bearbeitung** verwenden, da sie ein hohes Maß an Granularität bietet.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-242">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="8fc5f-243">Für eine flexible Bearbeitung empfehlen wir Ihnen, **eine angebotsfreie Bearbeitung** zu verwenden, da sie sofortige und spielerische Umgebungen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-243">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="8fc5f-244">Instinktive Gesten</span><span class="sxs-lookup"><span data-stu-id="8fc5f-244">Instinctual gestures</span></span>

<span data-ttu-id="8fc5f-245">Mit HoloLens (1. Generation) haben wir den Benutzern eine Reihe vordefinierter Gesten vermittelt, z. B. „Öffnen“ und „In die Luft tippen“.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-245">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="8fc5f-246">Bei HoloLens 2 werden die Benutzer nicht aufgefordert, sich symbolische Gesten zu merken.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-246">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="8fc5f-247">Alle erforderlichen Benutzergesten, mit denen der Benutzer mit Hologrammen und Inhalten interagieren muss, sind instinktiv.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-247">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="8fc5f-248">Um instinktive Gesten zu erreichen, müssen Benutzer durch den Entwurf von Benutzeroberflächenangeboten dazu angeleitet werden, Gesten auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-248">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="8fc5f-249">Wenn wir den Benutzer z. B. bestärken, ein Objekt oder einen Kontrollpunkt durch Zusammenführen von zwei Fingern zu greifen, sollte das Objekt oder der Kontrollpunkt klein sein.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-249">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="8fc5f-250">Wenn wir möchten, dass der Benutzer mit fünf Fingern greift, sollte das Objekt oder der Kontrollpunkt relativ groß sein.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-250">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="8fc5f-251">Ähnlich wie bei Tasten schränkt eine kleine Taste Benutzer darauf ein, sie mit einem einzelnen Finger zu drücken.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-251">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="8fc5f-252">Eine große Taste ermutigt Benutzer, sie mit der Handfläche zu drücken.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-252">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="8fc5f-253">![Grafik, die einen Benutzer zeigt, der ein kleines Objekt greift, um es zu bewegen](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-253">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-254">**Kleines Objekt**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-254">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-255">![Grafik, die einen Benutzer zeigt, der ein mittelgroßes Objekt greift, um es zu bewegen](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-255">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="8fc5f-256">**Mittelgroßes Objekt**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-256">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8fc5f-257">![Grafik, die einen Benutzer zeigt, der ein großes Objekt greift, um es zu bewegen](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fc5f-257">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="8fc5f-258">**Großes Objekt**</span><span class="sxs-lookup"><span data-stu-id="8fc5f-258">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="8fc5f-259">Symmetrisches Design zwischen Händen und Controllern mit 6 Freiheitsgraden</span><span class="sxs-lookup"><span data-stu-id="8fc5f-259">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="8fc5f-260">Sie haben vielleicht bemerkt, dass es Interaktionsparallelen gibt, die wir zwischen Händen in AR und Motion-Controllern in VR ziehen können.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-260">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="8fc5f-261">Beide Eingabemethoden können verwendet werden, um direkte Bearbeitungen in ihrer jeweiligen Umgebung auszulösen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-261">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="8fc5f-262">In HoloLens 2 funktioniert das Greifen und Ziehen mit den Händen aus nächster Nähe weitgehend so, wie die Taste zum Greifen an den WMR-Motion-Controllern.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-262">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="8fc5f-263">Dies bietet den Benutzern die vertraute Interaktion zwischen den beiden Plattformen, die sich als nützlich erweisen kann, falls Sie sich jemals dazu entscheiden, Ihre Anwendung zwischen den Plattformen zu portieren.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-263">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="8fc5f-264">Optimieren mit Eyetracking</span><span class="sxs-lookup"><span data-stu-id="8fc5f-264">Optimize with eye tracking</span></span>

<span data-ttu-id="8fc5f-265">Direkte Bearbeitung kann sich magisch anfühlen, wenn sie wie beabsichtigt funktioniert.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-265">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="8fc5f-266">Sie kann aber auch zu Enttäuschungen führen, wenn Sie Ihre Hand nicht mehr bewegen können, ohne unbeabsichtigt ein Hologramm zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-266">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="8fc5f-267">Das Eyetracking hilft potenziell, die Absicht des Benutzers besser zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-267">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="8fc5f-268">**Wann**: Reduzieren der unbeabsichtigten Auslösung einer Bearbeitungsreaktion.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-268">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="8fc5f-269">Das Eyetracking ermöglicht ein besseres Verständnis dafür, womit sich ein Benutzer gerade beschäftigt.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-269">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="8fc5f-270">Stellen Sie sich z. B. vor, Sie lesen einen holografischen Text (mit Anweisungen) durch, wenn Sie rübergreifen, um Ihr reales Arbeitsgerät aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-270">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="8fc5f-271">Dabei bewegen Sie Ihre Hand versehentlich über einige interaktive holografische Schaltflächen, die Sie vorher noch nicht einmal bemerkt haben.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-271">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="8fc5f-272">Beispielsweise lagen sie möglicherweise außerhalb des Sichtfelds des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-272">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="8fc5f-273">Wenn der Benutzer ein Hologramm eine Weile nicht betrachtet hat, aber ein Toucheingabe- oder Greifereignis dafür erkannt wurde, ist die Interaktion wahrscheinlich nicht beabsichtigt.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-273">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="8fc5f-274">**Welche**:  Abgesehen von der Behandlung falsch positiver Aktivierungen umfasst ein weiteres Beispiel die bessere Identifizierung, welche Hologramme zu greifen oder zu drücken sind, da der genaue Schnittpunkt aus Ihrer Sicht möglicherweise nicht eindeutig ist, insbesondere wenn mehrere Hologramme nahe beieinander positioniert sind.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-274">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="8fc5f-275">Während das Eyetracking bei HoloLens 2 Einschränkungen aufweisen kann, wie genau es Ihr Anvisieren mit dem Kopf bestimmen kann, ist dies bei nahen Interaktionen aufgrund von Tiefenunterschieden bei der Interaktion mit der Handeingabe möglicherweise hilfreich.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-275">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="8fc5f-276">Das bedeutet, dass es manchmal schwierig ist, festzustellen, ob sich Ihre Hand hinter oder vor einem Hologramm befindet, um z. B. ein Widget für die Bearbeitung präzise zu greifen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-276">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="8fc5f-277">**Wohin**: Verwenden Sie Informationen darüber, was sich ein Benutzer ansieht, mit schnell auslösenden Gesten.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-277">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="8fc5f-278">Greifen Sie ein Hologramm, und werfen Sie es grob in Richtung Ihres beabsichtigten Ziels.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-278">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="8fc5f-279">Obwohl dies manchmal funktioniert, können schnell ausgeführte Handgesten zu sehr ungenauen Zielen führen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-279">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="8fc5f-280">Das Eyetracking (Blickverfolgung) könnte die Genauigkeit der Geste verbessern.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-280">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="8fc5f-281">Bearbeitung im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="8fc5f-281">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="8fc5f-282">Mit dem **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie mithilfe des Skripts **ObjectManipulator** ganz einfach ein gängiges Bearbeitungsverhalten erzielen.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-282">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="8fc5f-283">Mit ObjectManipulator können Sie Objekte direkt mit der Hand oder dem Handlichtstrahl greifen und verschieben.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-283">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="8fc5f-284">Außerdem wird die Bearbeitung mit beiden Händen zum Skalieren und Rotieren eines Objekts unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8fc5f-284">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="8fc5f-285">MRTK – Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="8fc5f-285">MRTK - Manipulation</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-manipulator.md)

---

## <a name="see-also"></a><span data-ttu-id="8fc5f-286">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8fc5f-286">See also</span></span>

* [<span data-ttu-id="8fc5f-287">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="8fc5f-287">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8fc5f-288">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="8fc5f-288">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="8fc5f-289">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="8fc5f-289">Instinctual interactions</span></span>](interaction-fundamentals.md)