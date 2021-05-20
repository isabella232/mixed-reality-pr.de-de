---
title: Anvisieren mit dem Kopf und Ausführen
description: Beginnen Sie mit dem Eingabemodell mit dem Anvisieren mit dem Kopf und dem Commit, einschließlich Zielsizing, Platzierung und Stabilität.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, Anvisierten, Anvisierten, Interaktion, Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Ziel, Fokus, Glättung
ms.openlocfilehash: 74f963a6b450d1fb7f1302886a01c12cf79ce28a
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196515"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="7b236-104">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="7b236-104">Head-gaze and commit</span></span>

<span data-ttu-id="7b236-105">_Anvität mit dem Kopf_ und [](gaze-and-commit.md) Commit ist ein Sonderfall des Eingabemodells zum Anvieren und Commiten, bei dem ein Objekt mit der Kopfrichtung des Benutzer als Ziel verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7b236-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="7b236-106">Sie können auf das Ziel mit einer sekundären Eingabe wie dem Tippen auf die Handgestenbewegung oder dem Sprachbefehl "Select" (Auswählen) agieren.</span><span class="sxs-lookup"><span data-stu-id="7b236-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="7b236-107">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="7b236-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7b236-108"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="7b236-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="7b236-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7b236-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7b236-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7b236-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7b236-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="7b236-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7b236-112">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="7b236-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="7b236-113">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="7b236-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="7b236-114">✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</span><span class="sxs-lookup"><span data-stu-id="7b236-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="7b236-115">➕ Alternative Option</span><span class="sxs-lookup"><span data-stu-id="7b236-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="7b236-116">Demo zu Designkonzepten für Kopf- und Blickverfolgung</span><span class="sxs-lookup"><span data-stu-id="7b236-116">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="7b236-117">Wenn Sie die Designkonzepte für Kopf- und Blickverfolgung in Aktion sehen möchten, sehen Sie sich die Videodemo **Designing Holograms - Head Tracking and Eye Tracking** (Entwerfen von Hologrammen – Kopfverfolgung und Eyetracking) weiter unten an.</span><span class="sxs-lookup"><span data-stu-id="7b236-117">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="7b236-118">Wenn Sie fertig sind, fahren Sie fort, um ausführlichere Informationen zu bestimmten Themen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7b236-118">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="7b236-119">*Dieses Video wurde aus der App "Entwerfen von Hologrammen" HoloLens 2 aufgenommen. Laden Sie hier herunter, und profitieren Sie [von der vollständigen Erfahrung.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="7b236-119">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="7b236-120">Skalieren von Zielen und Feedback</span><span class="sxs-lookup"><span data-stu-id="7b236-120">Target sizing and feedback</span></span>

<span data-ttu-id="7b236-121">Der Anvisierungsvektor mit dem Kopf wurde wiederholt als für die Zieladressierung verwendet werden können, funktioniert aber häufig am besten für die Bruttozieladressierung – das Abrufen größerer Ziele.</span><span class="sxs-lookup"><span data-stu-id="7b236-121">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="7b236-122">Minimale Zielgrößen von 1 bis 1,5 Grad ermöglichen in den meisten Szenarien erfolgreiche Benutzeraktionen, obwohl Ziele von 3 Grad häufig eine höhere Geschwindigkeit ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="7b236-122">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="7b236-123">Die Größe, auf die der Benutzer ausgerichtet ist, ist im Wesentlichen ein 2D-Bereich, auch für 3D-Elemente – die Projektion, auf die sie ausgerichtet sind, sollte der zielfähige Bereich sein.</span><span class="sxs-lookup"><span data-stu-id="7b236-123">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="7b236-124">Es ist hilfreich, einen wichtigen Hinweis darauf zu geben, dass ein Element "aktiv" ist (dass der Benutzer es als Ziel hat).</span><span class="sxs-lookup"><span data-stu-id="7b236-124">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="7b236-125">Dies kann z. B. sichtbare "Hover"-Effekte, Audiohighlights oder Klicks oder eine klare Ausrichtung eines Cursors mit einem Element umfassen.</span><span class="sxs-lookup"><span data-stu-id="7b236-125">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="7b236-126">![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7b236-126">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="7b236-127">*Optimale Zielgröße bei 2-Meter-Entfernung*</span><span class="sxs-lookup"><span data-stu-id="7b236-127">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="7b236-128">![Beispiel für die Hervorhebung eines anvisierten Objekts](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7b236-128">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="7b236-129">*Beispiel für die Hervorhebung eines anvisierten Objekts*</span><span class="sxs-lookup"><span data-stu-id="7b236-129">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="7b236-130">Zielpositionierung</span><span class="sxs-lookup"><span data-stu-id="7b236-130">Target placement</span></span>

<span data-ttu-id="7b236-131">Benutzer finden benutzeroberflächenelemente häufig nicht, die sich in ihrem Sichtfeld entweder zu hoch oder niedrig befinden.</span><span class="sxs-lookup"><span data-stu-id="7b236-131">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="7b236-132">Die meiste Aufmerksamkeit liegt auf Bereichen um ihren Hauptfokus, die ungefähr auf Augenebene liegt.</span><span class="sxs-lookup"><span data-stu-id="7b236-132">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="7b236-133">Die Positionierung der meisten Ziele in einem vernünftigen Bereich auf Augenhöhe kann helfen.</span><span class="sxs-lookup"><span data-stu-id="7b236-133">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="7b236-134">Angesichts der Tatsache, dass Benutzer sich jederzeit auf einen relativ kleinen visuellen Bereich konzentrieren (der Aufmerksamkeitskegel des Sehens beträgt ungefähr 10 Grad), kann das Gruppieren von Ui-Elementen in dem Maße, in dem sie konzeptionell miteinander verknüpft sind, Aufmerksamkeitsverkettungsverhalten von Element zu Element verwenden, während ein Benutzer den Blick durch einen Bereich bewegt.</span><span class="sxs-lookup"><span data-stu-id="7b236-134">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="7b236-135">Beachten Sie beim Entwerfen der Benutzeroberfläche die potenziellen großen Unterschiede beim Sichtfeld zwischen HoloLens und immersiven Headsets.</span><span class="sxs-lookup"><span data-stu-id="7b236-135">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="7b236-136">![Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg).</span><span class="sxs-lookup"><span data-stu-id="7b236-136">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="7b236-137">*Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer*.</span><span class="sxs-lookup"><span data-stu-id="7b236-137">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="7b236-138">Verbessern des Verhaltens bei der Zielbestimmung</span><span class="sxs-lookup"><span data-stu-id="7b236-138">Improving targeting behaviors</span></span>

<span data-ttu-id="7b236-139">Wenn die Absicht des Benutzers, auf etwas abzuzielen, bestimmt oder eng angenähert werden kann, kann es hilfreich sein, Interaktionsversuche nahezu ausgelassen zu akzeptieren, als wären sie korrekt ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="7b236-139">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="7b236-140">Hier sind einige erfolgreiche Methoden, die in Mixed Reality-Erfahrungen integriert werden können:</span><span class="sxs-lookup"><span data-stu-id="7b236-140">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="7b236-141">Stabilisierung beim Anvisieren mit dem Kopf („Gravitationsbrunnen“)</span><span class="sxs-lookup"><span data-stu-id="7b236-141">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="7b236-142">Dies sollte die meiste Zeit oder die ganze Zeit aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="7b236-142">This should be turned on most or all of the time.</span></span> <span data-ttu-id="7b236-143">Mit dieser Technik werden die natürlichen Kopf- und Sprechbewegungen entfernt, die Benutzer aufgrund des Aussehens und Sprechverhaltens möglicherweise haben.</span><span class="sxs-lookup"><span data-stu-id="7b236-143">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="7b236-144">Algorithmen für die engste Verbindung</span><span class="sxs-lookup"><span data-stu-id="7b236-144">Closest link algorithms</span></span>

<span data-ttu-id="7b236-145">Diese Algorithmen funktionieren am besten in Bereichen mit wenig interaktivem Inhalt.</span><span class="sxs-lookup"><span data-stu-id="7b236-145">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="7b236-146">Wenn es eine hohe Wahrscheinlichkeit gibt, dass Sie bestimmen können, mit welchem Benutzer versucht wurde, zu interagieren, können Sie seine Zielfähigkeiten ergänzen, indem Sie ein gewisses Maß an Absicht annehmen.</span><span class="sxs-lookup"><span data-stu-id="7b236-146">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="7b236-147">Backdating- und Postdating-Aktionen</span><span class="sxs-lookup"><span data-stu-id="7b236-147">Backdating and postdating actions</span></span>

<span data-ttu-id="7b236-148">Dieser Mechanismus ist hilfreich bei Aufgaben, die Geschwindigkeit erfordern.</span><span class="sxs-lookup"><span data-stu-id="7b236-148">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="7b236-149">Wenn ein Benutzer eine Reihe von Ziel- und Aktivierungsreaktivierungen schnell durchgeht, ist es hilfreich, eine Absicht anzunehmen.</span><span class="sxs-lookup"><span data-stu-id="7b236-149">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="7b236-150">Es ist auch hilfreich, verpasste Schritte zuzulassen, um auf Ziele zu reagieren, die der Benutzer vor oder nach dem Tippen leicht im Fokus hatte (50 ms vorher/nach waren in frühen Tests wirksam).</span><span class="sxs-lookup"><span data-stu-id="7b236-150">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="7b236-151">Glättung</span><span class="sxs-lookup"><span data-stu-id="7b236-151">Smoothing</span></span>

<span data-ttu-id="7b236-152">Dieser Mechanismus ist nützlich für das Verschieben von Bewegungen, wodurch das leichte Jittern und Wackeln aufgrund natürlicher Kopfbewegungsmerkmale reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="7b236-152">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="7b236-153">Beim Glätten über Pfadbewegungen, glätten Sie nach Größe und Entfernung von Bewegungen und nicht im Laufe der Zeit.</span><span class="sxs-lookup"><span data-stu-id="7b236-153">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="7b236-154">Magnetismus</span><span class="sxs-lookup"><span data-stu-id="7b236-154">Magnetism</span></span>

<span data-ttu-id="7b236-155">Dieser Mechanismus kann als allgemeinere Version von Algorithmen für nahe bezogene Verknüpfungen bezeichnet werden– das Zeichnen eines Cursors in Richtung eines Ziels oder das einfache Erhöhen von Trefferboxen, ob sichtbar oder nicht, da Benutzer wahrscheinliche Ziele nähern, indem sie ein gewisses Wissen über das interaktive Layout verwenden, um die Benutzerabsicht besser zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="7b236-155">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="7b236-156">Dies kann für kleine Ziele leistungsfähig sein.</span><span class="sxs-lookup"><span data-stu-id="7b236-156">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="7b236-157">Fokusbindung</span><span class="sxs-lookup"><span data-stu-id="7b236-157">Focus stickiness</span></span>

<span data-ttu-id="7b236-158">Bei der Bestimmung, welchen interaktiven Elementen in der Nähe der Fokus zu geben ist, sorgt die Fokushaftigkeit für eine Verzerrung des Elements, das gerade fokussiert ist.</span><span class="sxs-lookup"><span data-stu-id="7b236-158">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="7b236-159">Dies trägt dazu bei, das Verhalten bei einem erratischen Fokuswechsel zu reduzieren, wenn das Gleiten an einem Mittelpunkt zwischen zwei Elementen mit natürlichem Rauschen vor sich geht.</span><span class="sxs-lookup"><span data-stu-id="7b236-159">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b236-160">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7b236-160">See also</span></span>

* [<span data-ttu-id="7b236-161">Augenbasierte Interaktion</span><span class="sxs-lookup"><span data-stu-id="7b236-161">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="7b236-162">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="7b236-162">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="7b236-163">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="7b236-163">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7b236-164">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="7b236-164">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="7b236-165">Hände – Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="7b236-165">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="7b236-166">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="7b236-166">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="7b236-167">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="7b236-167">Voice input</span></span>](voice-input.md)