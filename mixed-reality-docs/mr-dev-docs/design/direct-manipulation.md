---
title: Direkte Manipulation mit den Händen
description: Erfahren Sie mehr über direkte Manipulation, ein Eingabemodell, bei dem Benutzer Hologramme direkt mit den Händen berühren.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Anvisieren, Zielen per Anvisieren, Interaktion, Design, Eingabe, Hände nah beieinander, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit, Taste, Collider, Begrenzungsrahmen, 2D, instinktive Gesten
ms.openlocfilehash: 7a689f887bfd358b0d6e0826d41ef409bf887042
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600469"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="60e36-104">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="60e36-104">Direct manipulation with hands</span></span>

![Schaltfläche](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="60e36-106">Die direkte Manipulation ist ein Eingabemodell, bei dem Hologramme direkt mit den Händen berührt werden.</span><span class="sxs-lookup"><span data-stu-id="60e36-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="60e36-107">Die Idee hinter diesem Konzept ist, dass sich Objekte wie in der realen Welt verhalten.</span><span class="sxs-lookup"><span data-stu-id="60e36-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="60e36-108">Schaltflächen können einfach durch Drücken aktiviert werden, Objekte können durch Greifen aufgenommen werden und 2D-Inhalte verhalten sich wie ein virtueller Touchscreen.</span><span class="sxs-lookup"><span data-stu-id="60e36-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="60e36-109">Die direkte Manipulation ist angebotsbasiert, d. h. benutzerfreundlich.</span><span class="sxs-lookup"><span data-stu-id="60e36-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="60e36-110">Es gibt keine symbolischen Gesten, die den Benutzern vermittelt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="60e36-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="60e36-111">Alle Interaktionen basieren auf einem visuellen Element, das Sie berühren oder greifen können.</span><span class="sxs-lookup"><span data-stu-id="60e36-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="60e36-112">Sie gilt als „nahes“ Eingabemodell, d. h. es wird am besten für die Interaktion mit Inhalten verwendet, die innerhalb der Reichweite der Arme liegen.</span><span class="sxs-lookup"><span data-stu-id="60e36-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="60e36-113">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="60e36-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="60e36-114"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="60e36-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="60e36-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="60e36-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="60e36-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="60e36-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="60e36-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="60e36-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="60e36-118">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="60e36-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="60e36-119">❌ Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="60e36-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="60e36-120">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="60e36-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="60e36-121">➕ Unterstützt.</span><span class="sxs-lookup"><span data-stu-id="60e36-121">➕ Supported.</span></span>  <span data-ttu-id="60e36-122">Für die Benutzeroberfläche empfehlen wir stattdessen <a href="point-and-commit.md">Zeigen und Ausführen mit den Händen</a>.</span><span class="sxs-lookup"><span data-stu-id="60e36-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="60e36-123">Die direkte Manipulation ist ein primäres Eingabemodell für HoloLens 2 und nutzt das neue artikulierte Handtracking-System.</span><span class="sxs-lookup"><span data-stu-id="60e36-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="60e36-124">Das Eingabemodell ist auch bei immersiven Headsets über Motion-Controller verfügbar, wird aber nicht als primäre Möglichkeit zur Interaktion außerhalb der Objektmanipulation empfohlen.</span><span class="sxs-lookup"><span data-stu-id="60e36-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="60e36-125">Die direkte Manipulation ist bei HoloLens (1. Generation) nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="60e36-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="basic-hand-tracking-and-instinctual-interactions-demo"></a><span data-ttu-id="60e36-126">Demo zu grundlegendem Handtracking und instinktiven Interaktionen</span><span class="sxs-lookup"><span data-stu-id="60e36-126">Basic hand tracking and instinctual interactions demo</span></span>

<span data-ttu-id="60e36-127">Wenn Sie die Entwurfskonzepte für Kopf- und Eyetracking in Aktion sehen möchten, sehen Sie sich unten unsere Videodemo **Entwerfen von Hologrammen: Kopf- und Eyetracking** an.</span><span class="sxs-lookup"><span data-stu-id="60e36-127">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="60e36-128">Wenn Sie fertig sind, fahren Sie mit einem ausführlicheren Einblick in bestimmte Themen fort.</span><span class="sxs-lookup"><span data-stu-id="60e36-128">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

<span data-ttu-id="60e36-129">*Dieses Video wurde aus der HoloLens 2-App „Entwerfen von Hologrammen“ aufgenommen. Laden Sie die vollständige Erfahrung [hier](https://aka.ms/dhapp) herunter, und genießen Sie sie.*</span><span class="sxs-lookup"><span data-stu-id="60e36-129">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="collidable-fingertip"></a><span data-ttu-id="60e36-130">Kollisionsfähige Fingerspitze</span><span class="sxs-lookup"><span data-stu-id="60e36-130">Collidable fingertip</span></span>

<span data-ttu-id="60e36-131">Bei HoloLens 2 werden die Hände des Benutzers als Skelettmodelle der linken und rechten Hand erkannt und interpretiert.</span><span class="sxs-lookup"><span data-stu-id="60e36-131">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="60e36-132">Um die Idee, Hologramme direkt mit den Händen zu berühren, zu implementieren, könnten idealerweise fünf Collider an fünf Fingerspitzen der einzelnen Handskelettmodelle angefügt werden.</span><span class="sxs-lookup"><span data-stu-id="60e36-132">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="60e36-133">Aufgrund der fehlenden taktilen Rückmeldung können jedoch 10 kollisionsfähige Fingerspitzen unerwartete und unvorhersehbare Kollisionen mit Hologrammen verursachen.</span><span class="sxs-lookup"><span data-stu-id="60e36-133">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="60e36-134">Wir empfehlen, nur einen Collider an jedem Zeigefinger anzufügen.</span><span class="sxs-lookup"><span data-stu-id="60e36-134">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="60e36-135">Die kollisionsfähigen Zeigefingerspitzen können trotzdem als aktive Berührungspunkte für verschiedene Touchgesten dienen, die andere Finger einbeziehen.</span><span class="sxs-lookup"><span data-stu-id="60e36-135">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="60e36-136">Zu den Touchgesten gehören das Drücken mit einem Finger, das Tippen mit einem Finger, das Drücken mit zwei Fingern und das Drücken mit fünf Fingern, wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="60e36-136">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="60e36-137">![Kollisionsfähige Fingerspitze](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-137">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="60e36-138">**Kollisionsfähige Fingerspitze**</span><span class="sxs-lookup"><span data-stu-id="60e36-138">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-139">![Drücken mit einem Finger](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-139">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="60e36-140">**Drücken mit einem Finger**</span><span class="sxs-lookup"><span data-stu-id="60e36-140">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-141">![Tippen mit einem Finger](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-141">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="60e36-142">**Tippen mit einem Finger**</span><span class="sxs-lookup"><span data-stu-id="60e36-142">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-143">![Drücken mit fünf Fingern](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-143">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="60e36-144">**Drücken mit fünf Fingern**</span><span class="sxs-lookup"><span data-stu-id="60e36-144">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="60e36-145">Kugel-Collider</span><span class="sxs-lookup"><span data-stu-id="60e36-145">Sphere collider</span></span>

<span data-ttu-id="60e36-146">Anstelle einer zufälligen generischen Form wird empfohlen, einen Kugel-Collider zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="60e36-146">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="60e36-147">Anschließend können Sie diesen visuell rendern, um bessere Hinweise für die Zielbestimmung im Nahbereich zu bieten.</span><span class="sxs-lookup"><span data-stu-id="60e36-147">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="60e36-148">Der Durchmesser der Kugel muss der Dicke des Zeigefingers entsprechen, um die Genauigkeit bei der Toucheingabe zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="60e36-148">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="60e36-149">Die Variable für die Fingerdicke lässt sich durch den Aufruf der Hand-API einfacher abrufen.</span><span class="sxs-lookup"><span data-stu-id="60e36-149">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="60e36-150">Fingerspitzencursor</span><span class="sxs-lookup"><span data-stu-id="60e36-150">Fingertip cursor</span></span>

<span data-ttu-id="60e36-151">Zusätzlich zum Rendern einer kollisionsfähigen Kugel an der Zeigefingerspitze haben wir einen erweiterten Fingerspitzencursor entwickelt, um ein besseres Erlebnis bei der Bestimmung nahegelegener Ziele zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="60e36-151">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="60e36-152">Es handelt sich um einen ringförmigen Cursor, der an der Zeigefingerspitze angebracht ist.</span><span class="sxs-lookup"><span data-stu-id="60e36-152">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="60e36-153">Entsprechend der Nähe reagiert er hinsichtlich Ausrichtung und Größe dynamisch auf ein Ziel, wie unten beschrieben:</span><span class="sxs-lookup"><span data-stu-id="60e36-153">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="60e36-154">Wenn sich ein Zeigefinger auf ein Hologramm zubewegt, befindet sich der Cursor immer parallel zur Oberfläche des Hologramms und verkleinert seine Größe.</span><span class="sxs-lookup"><span data-stu-id="60e36-154">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="60e36-155">Sobald der Finger die Oberfläche berührt, schrumpft der Cursor zu einem Punkt und gibt ein Toucheingabeereignis aus.</span><span class="sxs-lookup"><span data-stu-id="60e36-155">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="60e36-156">Mit interaktiven Feedback können Benutzer eine hohe Genauigkeit bei Aufgaben zur Zielbestimmung im Nahbereich erreichen, z. B. das Auslösen eines Hyperlinks oder das Drücken einer Schaltfläche, wie nachfolgend veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="60e36-156">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="60e36-157">![Fingerspitzencursor – fern](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-157">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="60e36-158">**Fingerspitzencursor – fern**</span><span class="sxs-lookup"><span data-stu-id="60e36-158">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-159">![Fingerspitzencursor – nah](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-159">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="60e36-160">**Fingerspitzencursor – nah**</span><span class="sxs-lookup"><span data-stu-id="60e36-160">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-161">![Fingerspitzencursor – Kontakt](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-161">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="60e36-162">**Fingerspitzencursor – Kontakt**</span><span class="sxs-lookup"><span data-stu-id="60e36-162">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="60e36-163">Begrenzungsrahmen mit Näherungsshader</span><span class="sxs-lookup"><span data-stu-id="60e36-163">Bounding box with proximity shader</span></span>

<span data-ttu-id="60e36-164">Das Hologramm selbst erfordert auch die Fähigkeit, sowohl visuelles als auch akustisches Feedback zu liefern, um den Mangel an taktilem Feedback auszugleichen.</span><span class="sxs-lookup"><span data-stu-id="60e36-164">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="60e36-165">Dazu erstellen wir das Konzept eines Begrenzungsrahmens mit einem Näherungsshader.</span><span class="sxs-lookup"><span data-stu-id="60e36-165">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="60e36-166">Ein Begrenzungsrahmen ist ein minimaler volumetrischer Bereich, der ein 3D-Objekt umgibt.</span><span class="sxs-lookup"><span data-stu-id="60e36-166">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="60e36-167">Der Begrenzungsrahmen verfügt über einen interaktiven Renderingmechanismus, der als Näherungsshader bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="60e36-167">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="60e36-168">Der Näherungsshader verhält sich wie folgt:</span><span class="sxs-lookup"><span data-stu-id="60e36-168">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="60e36-169">![Hover (fern) mit visuellem Feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-169">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="60e36-170">**Hover (fern)**</span><span class="sxs-lookup"><span data-stu-id="60e36-170">**Hover (far)**</span></span><br>
       <span data-ttu-id="60e36-171">Wenn sich der Zeigefinger innerhalb eines Bereichs befindet, wird ein Fingerspitzenspotlight auf die Oberfläche des Begrenzungsrahmens gerichtet.</span><span class="sxs-lookup"><span data-stu-id="60e36-171">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-172">![Hover (nah) mit visuellem Feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-172">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="60e36-173">**Hover (nah)**</span><span class="sxs-lookup"><span data-stu-id="60e36-173">**Hover (near)**</span></span><br>
        <span data-ttu-id="60e36-174">Wenn sich die Fingerspitze der Oberfläche nähert, schrumpft das Spotlight.</span><span class="sxs-lookup"><span data-stu-id="60e36-174">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-175">![Kontakt beginnt](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-175">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="60e36-176">**Kontakt beginnt**</span><span class="sxs-lookup"><span data-stu-id="60e36-176">**Contact begins**</span></span><br>
       <span data-ttu-id="60e36-177">Sobald die Fingerspitze die Oberfläche berührt, wechselt der gesamte Begrenzungsrahmen die Farbe oder erzeugt einen visuellen Effekt, um den Toucheingabezustand zu reflektieren.</span><span class="sxs-lookup"><span data-stu-id="60e36-177">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-178">![Kontakt endet](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-178">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="60e36-179">**Kontakt endet**</span><span class="sxs-lookup"><span data-stu-id="60e36-179">**Contact ends**</span></span><br>
       <span data-ttu-id="60e36-180">Es kann auch ein Soundeffekt aktiviert werden, um das visuelle Feedback der Toucheingabe zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="60e36-180">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="60e36-181">Drückbare Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="60e36-181">Pressable button</span></span>

<span data-ttu-id="60e36-182">Mit einer kollisionsfähigen Fingerspitze sind die Benutzer jetzt bereit, mit einer grundlegenden holografischen Benutzeroberflächenkomponente, z. B. einer drückbaren Schaltfläche, zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="60e36-182">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="60e36-183">Eine drückbare Schaltfläche ist eine holografische Schaltfläche, die auf einen direkten Fingerdruck angepasst ist.</span><span class="sxs-lookup"><span data-stu-id="60e36-183">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="60e36-184">Da es an taktilem Feedback mangelt, setzt eine drückbare Schaltfläche wiederum einige Mechanismen ein, um auf dem taktilen Feedback basierende Probleme zu beheben.</span><span class="sxs-lookup"><span data-stu-id="60e36-184">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="60e36-185">Der erste Mechanismus ist ein Begrenzungsrahmen mit einem Näherungsshader, wie er im vorherigen Abschnitt beschrieben wurde.</span><span class="sxs-lookup"><span data-stu-id="60e36-185">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="60e36-186">Er vermittelt Benutzern ein besseres Gefühl von Nähe, wenn sie sich einer Schaltfläche nähern und mit ihr Kontakt aufnehmen können.</span><span class="sxs-lookup"><span data-stu-id="60e36-186">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="60e36-187">Der zweite Mechanismus ist die Absenkung.</span><span class="sxs-lookup"><span data-stu-id="60e36-187">The second mechanism is depression.</span></span> <span data-ttu-id="60e36-188">Absenkung erzeugt ein Gefühl des Niederdrückens, nachdem eine Fingerspitze die Schaltfläche berührt hat.</span><span class="sxs-lookup"><span data-stu-id="60e36-188">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="60e36-189">Der Mechanismus stellt sicher, dass sich die Schaltfläche mit der Fingerspitze eng entlang der Tiefenachse bewegt.</span><span class="sxs-lookup"><span data-stu-id="60e36-189">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="60e36-190">Die Schaltfläche kann ausgelöst werden, wenn sie eine gewählte Tiefe erreicht (beim Drücken) oder die Tiefe wieder verlässt (beim Loslassen), nachdem sie passiert wurde.</span><span class="sxs-lookup"><span data-stu-id="60e36-190">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="60e36-191">Der Soundeffekt sollte hinzugefügt werden, um das Feedback zu verbessern, wenn die Schaltfläche ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="60e36-191">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="60e36-192">![Drückbare Schaltfläche – fern](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-192">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="60e36-193">**Finger ist weit entfernt**</span><span class="sxs-lookup"><span data-stu-id="60e36-193">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-194">![Drückbare Schaltfläche – nah](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-194">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="60e36-195">**Finger nähert sich**</span><span class="sxs-lookup"><span data-stu-id="60e36-195">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-196">![Drückbare Schaltfläche – Kontakt beginnt](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-196">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="60e36-197">**Kontakt beginnt**</span><span class="sxs-lookup"><span data-stu-id="60e36-197">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-198">![Drückbare Schaltfläche – Drücken](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-198">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="60e36-199">**Nach unten drücken**</span><span class="sxs-lookup"><span data-stu-id="60e36-199">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="60e36-200">2D-Tafel – Interaktion</span><span class="sxs-lookup"><span data-stu-id="60e36-200">2D slate interaction</span></span>

<span data-ttu-id="60e36-201">Eine 2D-[Tafel](slate.md) ist ein holografischer Container, der zum Hosten von 2D-App-Inhalten verwendet wird (z. B. ein Webbrowser).</span><span class="sxs-lookup"><span data-stu-id="60e36-201">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="60e36-202">Das Konzept für die Interaktion mit einer 2D-Tafel durch direkte Manipulation ist das gleiche wie für die Interaktion mit einem physischen Touchscreen.</span><span class="sxs-lookup"><span data-stu-id="60e36-202">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="60e36-203">So interagieren Sie mit dem Tafelkontakt</span><span class="sxs-lookup"><span data-stu-id="60e36-203">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="60e36-204">![Toucheingabe](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-204">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="60e36-205">**Toucheingabe**</span><span class="sxs-lookup"><span data-stu-id="60e36-205">**Touch**</span></span><br>
       <span data-ttu-id="60e36-206">Verwenden Sie einen Zeigefinger, um einen Link oder eine Schaltfläche zu drücken.</span><span class="sxs-lookup"><span data-stu-id="60e36-206">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-207">![Scrollen](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-207">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="60e36-208">**Scrollen**</span><span class="sxs-lookup"><span data-stu-id="60e36-208">**Scroll**</span></span><br>
        <span data-ttu-id="60e36-209">Verwenden Sie einen Zeigefinger, um einen Tafelinhalt nach oben und unten zu scrollen.</span><span class="sxs-lookup"><span data-stu-id="60e36-209">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-210">![Zoomen](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-210">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="60e36-211">**Zoomen**</span><span class="sxs-lookup"><span data-stu-id="60e36-211">**Zoom**</span></span><br>
       <span data-ttu-id="60e36-212">Die zwei Zeigefinger des Benutzers werden verwendet, um den Tafelinhalt entsprechend der relativen Bewegung der Finger zu vergrößern oder zu verkleinern.</span><span class="sxs-lookup"><span data-stu-id="60e36-212">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="60e36-213">So bearbeiten Sie die eigentliche 2D-Tafel</span><span class="sxs-lookup"><span data-stu-id="60e36-213">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="60e36-214">![Grafik mit der Darstellung des Features zum Greifen und Ziehen](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-214">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="60e36-215">**Verschieben**</span><span class="sxs-lookup"><span data-stu-id="60e36-215">**Move**</span></span><br>
       <span data-ttu-id="60e36-216">Bewegen Sie Ihre Hände in Richtung von Ecken und Kanten, um die nächstgelegenen Manipulationsangebote zu enthüllen.</span><span class="sxs-lookup"><span data-stu-id="60e36-216">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="60e36-217">Greifen Sie die Hololeiste im oberen Bereich der 2D-Tafel, mit der Sie die gesamte Tafel verschieben können.</span><span class="sxs-lookup"><span data-stu-id="60e36-217">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-218">![Grafik mit Darstellung der Skalierungsfunktion](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-218">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="60e36-219">**Skalierung**</span><span class="sxs-lookup"><span data-stu-id="60e36-219">**Scale**</span></span><br>
        <span data-ttu-id="60e36-220">Greifen Sie die Manipulationsangebote, und führen Sie über die Eckenangebote eine einheitliche Skalierung aus.</span><span class="sxs-lookup"><span data-stu-id="60e36-220">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-221">![Neuanordnen](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-221">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="60e36-222">**Neuanordnen**</span><span class="sxs-lookup"><span data-stu-id="60e36-222">**Reflow**</span></span><br>
       <span data-ttu-id="60e36-223">Greifen Sie die Manipulationsangebote, und führen Sie über die Eckenangebote die Neuanordnung aus.</span><span class="sxs-lookup"><span data-stu-id="60e36-223">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="60e36-224">3D-Objektbearbeitung</span><span class="sxs-lookup"><span data-stu-id="60e36-224">3D object manipulation</span></span>

<span data-ttu-id="60e36-225">Bei HoloLens 2 können Benutzer ihre Hände in die Lage versetzen, holografische 3D-Objekte zu steuern und zu bearbeiten, indem sie auf die einzelnen 3D-Objekte einen Begrenzungsrahmen anwenden.</span><span class="sxs-lookup"><span data-stu-id="60e36-225">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="60e36-226">Der Begrenzungsrahmen sorgt durch seinen Näherungsshader für eine bessere Tiefenwahrnehmung.</span><span class="sxs-lookup"><span data-stu-id="60e36-226">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="60e36-227">Mit dem Begrenzungsrahmen gibt es zwei Konstruktionsansätze für die 3D-Objektbearbeitung.</span><span class="sxs-lookup"><span data-stu-id="60e36-227">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="60e36-228">Angebotsbasierte Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="60e36-228">Affordance-based manipulation</span></span>

<span data-ttu-id="60e36-229">Angebotsbasierte Bearbeitung gestattet es Ihnen, das 3D-Objekt durch einen Begrenzungsrahmen zusammen mit dem diesen umgebenden Bearbeitungsangeboten zu manipulieren.</span><span class="sxs-lookup"><span data-stu-id="60e36-229">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="60e36-230">![Grafik mit der Darstellung von Begrenzungsrahmen und Verschiebefeature eines Objekts](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-230">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="60e36-231">**Verschieben**</span><span class="sxs-lookup"><span data-stu-id="60e36-231">**Move**</span></span><br>
       <span data-ttu-id="60e36-232">Sobald sich die Hand eines Benutzers in der Nähe eines 3D-Objekts befindet, werden der Begrenzungsrahmen und das nächstgelegene Angebot angezeigt.</span><span class="sxs-lookup"><span data-stu-id="60e36-232">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="60e36-233">Benutzer können den Begrenzungsrahmen greifen, um das gesamte Objekt zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="60e36-233">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-234">![Grafik mit der Darstellung eines Benutzers, der die Kante eines Objekts greift, um es zu drehen](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-234">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="60e36-235">**Drehen**</span><span class="sxs-lookup"><span data-stu-id="60e36-235">**Rotate**</span></span><br>
        <span data-ttu-id="60e36-236">Benutzer können zum Drehen die Eckenangebote greifen.</span><span class="sxs-lookup"><span data-stu-id="60e36-236">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-237">![Grafik mit der Darstellung eines Benutzers, der die Ecke eines Objekts greift, um es zu skalieren](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-237">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="60e36-238">**Skalierung**</span><span class="sxs-lookup"><span data-stu-id="60e36-238">**Scale**</span></span><br>
       <span data-ttu-id="60e36-239">Benutzer können die Eckenangebote greifen, um eine einheitliche Skalierung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="60e36-239">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="60e36-240">Bearbeitung ohne Angebot</span><span class="sxs-lookup"><span data-stu-id="60e36-240">Non-affordance-based manipulation</span></span>

<span data-ttu-id="60e36-241">Bei der Bearbeitung ohne Angebot werden dem Begrenzungsrahmen keine Angebote angefügt.</span><span class="sxs-lookup"><span data-stu-id="60e36-241">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="60e36-242">Benutzer können den Begrenzungsrahmen nur anzeigen und dann direkt mit ihm interagieren.</span><span class="sxs-lookup"><span data-stu-id="60e36-242">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="60e36-243">Wenn der Begrenzungsrahmen mit einer Hand gegriffen wird, sind Verschiebung und Drehung des Objekts der Bewegung und Ausrichtung der Hand zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="60e36-243">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="60e36-244">Wenn das Objekt mit zwei Händen gegriffen wird, kann der Benutzer Verschiebung, Drehung und Skalierung entsprechend der relativen Bewegung der beiden Hände vornehmen.</span><span class="sxs-lookup"><span data-stu-id="60e36-244">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="60e36-245">Bestimmte Bearbeitungen erfordern Präzision.</span><span class="sxs-lookup"><span data-stu-id="60e36-245">Specific manipulation requires precision.</span></span> <span data-ttu-id="60e36-246">Wir empfehlen, dass Sie **angebotsbasierter Bearbeitung** verwenden, da sie ein hohes Maß an Granularität bietet.</span><span class="sxs-lookup"><span data-stu-id="60e36-246">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="60e36-247">Für eine flexible Bearbeitung empfehlen wir Ihnen, **eine angebotsfreie Bearbeitung** zu verwenden, da sie sofortige und spielerische Umgebungen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="60e36-247">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="60e36-248">Instinktive Gesten</span><span class="sxs-lookup"><span data-stu-id="60e36-248">Instinctual gestures</span></span>

<span data-ttu-id="60e36-249">Mit HoloLens (1. Generation) haben wir den Benutzern eine Reihe vordefinierter Gesten vermittelt, z. B. „Öffnen“ und „In die Luft tippen“.</span><span class="sxs-lookup"><span data-stu-id="60e36-249">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="60e36-250">Bei HoloLens 2 werden die Benutzer nicht aufgefordert, sich symbolische Gesten zu merken.</span><span class="sxs-lookup"><span data-stu-id="60e36-250">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="60e36-251">Alle erforderlichen Benutzergesten, mit denen der Benutzer mit Hologrammen und Inhalten interagieren muss, sind instinktiv.</span><span class="sxs-lookup"><span data-stu-id="60e36-251">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="60e36-252">Um instinktive Gesten zu erreichen, müssen Benutzer durch den Entwurf von Benutzeroberflächenangeboten dazu angeleitet werden, Gesten auszuführen.</span><span class="sxs-lookup"><span data-stu-id="60e36-252">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="60e36-253">Wenn wir den Benutzer z. B. bestärken, ein Objekt oder einen Kontrollpunkt durch Zusammenführen von zwei Fingern zu greifen, sollte das Objekt oder der Kontrollpunkt klein sein.</span><span class="sxs-lookup"><span data-stu-id="60e36-253">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="60e36-254">Wenn wir möchten, dass der Benutzer mit fünf Fingern greift, sollte das Objekt oder der Kontrollpunkt relativ groß sein.</span><span class="sxs-lookup"><span data-stu-id="60e36-254">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="60e36-255">Ähnlich wie bei Tasten schränkt eine kleine Taste Benutzer darauf ein, sie mit einem einzelnen Finger zu drücken.</span><span class="sxs-lookup"><span data-stu-id="60e36-255">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="60e36-256">Eine große Taste ermutigt Benutzer, sie mit der Handfläche zu drücken.</span><span class="sxs-lookup"><span data-stu-id="60e36-256">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="60e36-257">![Grafik, die einen Benutzer zeigt, der ein kleines Objekt greift, um es zu bewegen](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-257">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="60e36-258">**Kleines Objekt**</span><span class="sxs-lookup"><span data-stu-id="60e36-258">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-259">![Grafik, die einen Benutzer zeigt, der ein mittelgroßes Objekt greift, um es zu bewegen](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-259">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="60e36-260">**Mittelgroßes Objekt**</span><span class="sxs-lookup"><span data-stu-id="60e36-260">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="60e36-261">![Grafik, die einen Benutzer zeigt, der ein großes Objekt greift, um es zu bewegen](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="60e36-261">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="60e36-262">**Großes Objekt**</span><span class="sxs-lookup"><span data-stu-id="60e36-262">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="60e36-263">Symmetrisches Design zwischen Händen und Controllern mit 6 Freiheitsgraden</span><span class="sxs-lookup"><span data-stu-id="60e36-263">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="60e36-264">Sie haben vielleicht bemerkt, dass es Interaktionsparallelen gibt, die wir zwischen Händen in AR und Motion-Controllern in VR ziehen können.</span><span class="sxs-lookup"><span data-stu-id="60e36-264">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="60e36-265">Beide Eingabemethoden können verwendet werden, um direkte Bearbeitungen in ihrer jeweiligen Umgebung auszulösen.</span><span class="sxs-lookup"><span data-stu-id="60e36-265">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="60e36-266">In HoloLens 2 funktioniert das Greifen und Ziehen mit den Händen aus nächster Nähe weitgehend so, wie die Taste zum Greifen an den WMR-Motion-Controllern.</span><span class="sxs-lookup"><span data-stu-id="60e36-266">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="60e36-267">Dies bietet den Benutzern die vertraute Interaktion zwischen den beiden Plattformen, die sich als nützlich erweisen kann, falls Sie sich jemals dazu entscheiden, Ihre Anwendung zwischen den Plattformen zu portieren.</span><span class="sxs-lookup"><span data-stu-id="60e36-267">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="60e36-268">Optimieren mit Eyetracking</span><span class="sxs-lookup"><span data-stu-id="60e36-268">Optimize with eye tracking</span></span>

<span data-ttu-id="60e36-269">Direkte Bearbeitung kann sich magisch anfühlen, wenn sie wie beabsichtigt funktioniert.</span><span class="sxs-lookup"><span data-stu-id="60e36-269">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="60e36-270">Sie kann aber auch zu Enttäuschungen führen, wenn Sie Ihre Hand nicht mehr bewegen können, ohne unbeabsichtigt ein Hologramm zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="60e36-270">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="60e36-271">Das Eyetracking hilft potenziell, die Absicht des Benutzers besser zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="60e36-271">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="60e36-272">**Wann**: Reduzieren der unbeabsichtigten Auslösung einer Bearbeitungsreaktion.</span><span class="sxs-lookup"><span data-stu-id="60e36-272">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="60e36-273">Das Eyetracking ermöglicht ein besseres Verständnis dafür, womit sich ein Benutzer gerade beschäftigt.</span><span class="sxs-lookup"><span data-stu-id="60e36-273">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="60e36-274">Stellen Sie sich z. B. vor, Sie lesen einen holografischen Text (mit Anweisungen) durch, wenn Sie rübergreifen, um Ihr reales Arbeitsgerät aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="60e36-274">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="60e36-275">Dabei bewegen Sie Ihre Hand versehentlich über einige interaktive holografische Schaltflächen, die Sie vorher noch nicht einmal bemerkt haben.</span><span class="sxs-lookup"><span data-stu-id="60e36-275">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="60e36-276">Beispielsweise lagen sie möglicherweise außerhalb des Sichtfelds des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="60e36-276">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="60e36-277">Wenn der Benutzer ein Hologramm eine Weile nicht betrachtet hat, aber ein Toucheingabe- oder Greifereignis dafür erkannt wurde, ist die Interaktion wahrscheinlich nicht beabsichtigt.</span><span class="sxs-lookup"><span data-stu-id="60e36-277">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="60e36-278">**Welche**:  Abgesehen von der Behandlung falsch positiver Aktivierungen umfasst ein weiteres Beispiel die bessere Identifizierung, welche Hologramme zu greifen oder zu drücken sind, da der genaue Schnittpunkt aus Ihrer Sicht möglicherweise nicht eindeutig ist, insbesondere wenn mehrere Hologramme nahe beieinander positioniert sind.</span><span class="sxs-lookup"><span data-stu-id="60e36-278">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="60e36-279">Während das Eyetracking bei HoloLens 2 Einschränkungen aufweisen kann, wie genau es Ihr Anvisieren mit dem Kopf bestimmen kann, ist dies bei nahen Interaktionen aufgrund von Tiefenunterschieden bei der Interaktion mit der Handeingabe möglicherweise hilfreich.</span><span class="sxs-lookup"><span data-stu-id="60e36-279">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="60e36-280">Das bedeutet, dass es manchmal schwierig ist, festzustellen, ob sich Ihre Hand hinter oder vor einem Hologramm befindet, um z. B. ein Widget für die Bearbeitung präzise zu greifen.</span><span class="sxs-lookup"><span data-stu-id="60e36-280">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="60e36-281">**Wohin**: Verwenden Sie Informationen darüber, was sich ein Benutzer ansieht, mit schnell auslösenden Gesten.</span><span class="sxs-lookup"><span data-stu-id="60e36-281">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="60e36-282">Greifen Sie ein Hologramm, und werfen Sie es grob in Richtung Ihres beabsichtigten Ziels.</span><span class="sxs-lookup"><span data-stu-id="60e36-282">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="60e36-283">Obwohl dies manchmal funktioniert, können schnell ausgeführte Handgesten zu sehr ungenauen Zielen führen.</span><span class="sxs-lookup"><span data-stu-id="60e36-283">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="60e36-284">Das Eyetracking (Blickverfolgung) könnte die Genauigkeit der Geste verbessern.</span><span class="sxs-lookup"><span data-stu-id="60e36-284">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="60e36-285">Bearbeitung im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="60e36-285">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="60e36-286">Mit dem **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie mithilfe des Skripts **ObjectManipulator** ganz einfach ein gängiges Bearbeitungsverhalten erzielen.</span><span class="sxs-lookup"><span data-stu-id="60e36-286">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="60e36-287">Mit ObjectManipulator können Sie Objekte direkt mit der Hand oder dem Handlichtstrahl greifen und verschieben.</span><span class="sxs-lookup"><span data-stu-id="60e36-287">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="60e36-288">Außerdem wird die Bearbeitung mit beiden Händen zum Skalieren und Rotieren eines Objekts unterstützt.</span><span class="sxs-lookup"><span data-stu-id="60e36-288">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="60e36-289">MRTK – Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="60e36-289">MRTK - Manipulation</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator)

---

## <a name="see-also"></a><span data-ttu-id="60e36-290">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="60e36-290">See also</span></span>

* [<span data-ttu-id="60e36-291">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="60e36-291">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="60e36-292">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="60e36-292">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="60e36-293">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="60e36-293">Instinctual interactions</span></span>](interaction-fundamentals.md)