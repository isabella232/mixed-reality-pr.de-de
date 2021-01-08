---
title: Anvisieren mit dem Kopf und Ausführen
description: Beginnen Sie mit den ersten Schritten mit dem Haupt-und Commit-Eingabe Modell, einschließlich der Größenanpassung, Platzierung und Stabilisierung des Ziels.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Gemischte Realität, Blick, Blick auf die Ausrichtung, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Ziel, Fokus, Glättung
ms.openlocfilehash: 13a040a8309d084fcfdbfa91cbd9d63b595b004a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009450"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="e56ec-104">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="e56ec-104">Head-gaze and commit</span></span>

<span data-ttu-id="e56ec-105">Der _Kopf-und Commit-_ Vorgang ist ein Sonderfall des "Blick"- [und](gaze-and-commit.md) "Commit"-Eingabe Modells, bei dem ein Objekt mit der Benutzer Kopfzeile verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e56ec-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="e56ec-106">Sie können das Ziel mit einer sekundären Eingabe, wie z. b. dem Befehl "Handbewegung Air Tap" oder "Select", für das Ziel handeln.</span><span class="sxs-lookup"><span data-stu-id="e56ec-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="e56ec-107">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="e56ec-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e56ec-108"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="e56ec-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="e56ec-109"><a href="../hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e56ec-109"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e56ec-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e56ec-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e56ec-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="e56ec-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e56ec-112">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="e56ec-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="e56ec-113">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="e56ec-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="e56ec-114">✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</span><span class="sxs-lookup"><span data-stu-id="e56ec-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="e56ec-115">➕ Alternative Option</span><span class="sxs-lookup"><span data-stu-id="e56ec-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="e56ec-116">Skalieren von Zielen und Feedback</span><span class="sxs-lookup"><span data-stu-id="e56ec-116">Target sizing and feedback</span></span>

<span data-ttu-id="e56ec-117">Der Kopf Zeilenvektor wurde wiederholt angezeigt, um für die fein Ausrichtung geeignet zu sein. er eignet sich jedoch oft am besten für das anvisieren von größeren Zielen.</span><span class="sxs-lookup"><span data-stu-id="e56ec-117">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="e56ec-118">Die minimalen Zielgrößen von 1 Grad bis 1,5 Grad ermöglichen in den meisten Szenarien erfolgreiche Benutzeraktionen, obwohl Ziele von 3 Grad häufig eine höhere Geschwindigkeit ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e56ec-118">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="e56ec-119">Die Größe, auf die der Benutzer ausgerichtet ist, ist tatsächlich ein 2D-Bereich, auch bei 3D-Elementen, und die Projektion, mit der er konfrontiert ist, sollte der Zielbereich sein.</span><span class="sxs-lookup"><span data-stu-id="e56ec-119">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="e56ec-120">Das Bereitstellen eines hervorragenden Anweisungs Elements, dass ein Element "aktiv" ist (das der Benutzer als Ziel verwendet), ist hilfreich.</span><span class="sxs-lookup"><span data-stu-id="e56ec-120">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="e56ec-121">Dies kann z. b. z. b. sichtbare "Hover"-Effekte, audiohighlights oder Klicks oder eine klare Ausrichtung eines Cursors mit einem Element umfassen.</span><span class="sxs-lookup"><span data-stu-id="e56ec-121">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="e56ec-122">![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e56ec-122">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="e56ec-123">*Optimale Zielgröße bei 2-Meter-Entfernung*</span><span class="sxs-lookup"><span data-stu-id="e56ec-123">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="e56ec-124">![Beispiel für die Hervorhebung eines anvisierten Objekts](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e56ec-124">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="e56ec-125">*Beispiel für die Hervorhebung eines anvisierten Objekts*</span><span class="sxs-lookup"><span data-stu-id="e56ec-125">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="e56ec-126">Zielpositionierung</span><span class="sxs-lookup"><span data-stu-id="e56ec-126">Target placement</span></span>

<span data-ttu-id="e56ec-127">Benutzer können häufig keine Benutzeroberflächen Elemente finden, die sich entweder zu hoch oder zu niedrig im Sichtfeld befinden.</span><span class="sxs-lookup"><span data-stu-id="e56ec-127">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="e56ec-128">Der größte Teil ihrer Aufmerksamkeit liegt am Ende der Bereiche, die sich in der Nähe des Hauptfokus befinden.</span><span class="sxs-lookup"><span data-stu-id="e56ec-128">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="e56ec-129">Die Positionierung der meisten Ziele in einem vernünftigen Bereich auf Augenhöhe kann helfen.</span><span class="sxs-lookup"><span data-stu-id="e56ec-129">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="e56ec-130">Angesichts der Tendenz, dass sich Benutzer jederzeit auf einen relativ kleinen visuellen Bereich konzentrieren können (der Teilnehmer ist ungefähr 10 Grad), kann das Gruppieren von Benutzeroberflächen Elementen zu dem Grad, den Sie konzeptionell verknüpft haben, das Verhalten der Aufmerksamkeit Verkettung von Item zu Item verwenden, wenn ein Benutzer den Blick durch einen Bereich verschiebt.</span><span class="sxs-lookup"><span data-stu-id="e56ec-130">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="e56ec-131">Beachten Sie beim Entwerfen der Benutzeroberfläche die potenziellen großen Unterschiede beim Sichtfeld zwischen HoloLens und immersiven Headsets.</span><span class="sxs-lookup"><span data-stu-id="e56ec-131">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="e56ec-132">![Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg).</span><span class="sxs-lookup"><span data-stu-id="e56ec-132">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="e56ec-133">*Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer*.</span><span class="sxs-lookup"><span data-stu-id="e56ec-133">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="e56ec-134">Verbessern des Verhaltens bei der Zielbestimmung</span><span class="sxs-lookup"><span data-stu-id="e56ec-134">Improving targeting behaviors</span></span>

<span data-ttu-id="e56ec-135">Wenn der Benutzer beabsichtigt ist, etwas zu erreichen, kann es hilfreich sein, und es kann hilfreich sein, die Near-Fehler Interaktion zu akzeptieren, als ob Sie ordnungsgemäß als Ziel festgelegt wurden.</span><span class="sxs-lookup"><span data-stu-id="e56ec-135">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="e56ec-136">Hier sind einige der erfolgreichen Methoden, die in gemischte Realität integriert werden können:</span><span class="sxs-lookup"><span data-stu-id="e56ec-136">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="e56ec-137">Stabilisierung beim Anvisieren mit dem Kopf („Gravitationsbrunnen“)</span><span class="sxs-lookup"><span data-stu-id="e56ec-137">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="e56ec-138">Dies sollte in den meisten Fällen oder in der Zeit aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="e56ec-138">This should be turned on most or all of the time.</span></span> <span data-ttu-id="e56ec-139">Durch diese Vorgehensweise werden die natürlichen Kopf-und Hals jittoren entfernt, die Benutzer möglicherweise auch aufgrund der Betrachtung und des Sprech Verhaltens Verhalten haben.</span><span class="sxs-lookup"><span data-stu-id="e56ec-139">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="e56ec-140">Algorithmen für die engste Verbindung</span><span class="sxs-lookup"><span data-stu-id="e56ec-140">Closest link algorithms</span></span>

<span data-ttu-id="e56ec-141">Diese Algorithmen funktionieren am besten in Bereichen mit interaktiven Inhalten mit geringer Dichte.</span><span class="sxs-lookup"><span data-stu-id="e56ec-141">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="e56ec-142">Wenn eine hohe Wahrscheinlichkeit besteht, dass Sie bestimmen können, mit welchem Benutzer Sie interagieren wollten, können Sie die Ziel Fähigkeiten ergänzen, indem Sie eine gewisse Absicht annehmen.</span><span class="sxs-lookup"><span data-stu-id="e56ec-142">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="e56ec-143">Sicherungs-und postdating-Aktionen</span><span class="sxs-lookup"><span data-stu-id="e56ec-143">Backdating and postdating actions</span></span>

<span data-ttu-id="e56ec-144">Dieser Mechanismus ist hilfreich bei Aufgaben, die Geschwindigkeit erfordern.</span><span class="sxs-lookup"><span data-stu-id="e56ec-144">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="e56ec-145">Wenn ein Benutzer mit der Geschwindigkeit eine Reihe von Ziel-und Aktivierungs Manövern durchläuft, ist es sinnvoll, eine beabsichtigte Absicht anzunehmen.</span><span class="sxs-lookup"><span data-stu-id="e56ec-145">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="e56ec-146">Außerdem ist es hilfreich, die Ausführung von versäumten Schritten für Ziele zu ermöglichen, auf die sich der Benutzer vor oder nach dem tippen etwas ausgewirkt hat (50 ms vor/nach war in frühen Tests wirksam).</span><span class="sxs-lookup"><span data-stu-id="e56ec-146">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="e56ec-147">Glättung</span><span class="sxs-lookup"><span data-stu-id="e56ec-147">Smoothing</span></span>

<span data-ttu-id="e56ec-148">Dieser Mechanismus ist nützlich für die Bewegung von Bewegungen und reduziert die leichte Jitter und wackeln aufgrund natürlicher Kopf Verschiebungs Merkmale.</span><span class="sxs-lookup"><span data-stu-id="e56ec-148">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="e56ec-149">Bei der Glättung von bewegungsbewegungen durch die Größe und die Entfernung von Bewegungen und nicht über die Zeit.</span><span class="sxs-lookup"><span data-stu-id="e56ec-149">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="e56ec-150">Magnetismus</span><span class="sxs-lookup"><span data-stu-id="e56ec-150">Magnetism</span></span>

<span data-ttu-id="e56ec-151">Dieser Mechanismus kann sich als allgemeinere Version der nächstgelegenen Verknüpfungs Algorithmen vorstellen: das Zeichnen eines Cursors in Richtung eines Ziels oder das einfache erhöhen der Treffer Felder, egal ob sichtbar oder nicht, wenn Benutzer wahrscheinliche Ziele erreichen, indem Sie einige Kenntnisse des interaktiven Layouts verwenden, um die Benutzer Absicht besser zu betrachten.</span><span class="sxs-lookup"><span data-stu-id="e56ec-151">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="e56ec-152">Dies kann für kleine Ziele leistungsstark sein.</span><span class="sxs-lookup"><span data-stu-id="e56ec-152">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="e56ec-153">Fokusbindung</span><span class="sxs-lookup"><span data-stu-id="e56ec-153">Focus stickiness</span></span>

<span data-ttu-id="e56ec-154">Wenn Sie bestimmen, welche interaktiven Elemente in der Nähe bereitgestellt werden sollen, wird der Fokus auf festgelegt, und der Fokus ist für das Element, das derzeit fokussiert ist.</span><span class="sxs-lookup"><span data-stu-id="e56ec-154">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="e56ec-155">Dies trägt dazu bei, das Verhalten von erratischen Fokus Wechselverhalten zu verringern, wenn Sie in einem Mittelpunkt zwischen zwei Elementen mit natürlichem Rauschen schweben</span><span class="sxs-lookup"><span data-stu-id="e56ec-155">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="e56ec-156">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e56ec-156">See also</span></span>

* [<span data-ttu-id="e56ec-157">Augenbasierte Interaktion</span><span class="sxs-lookup"><span data-stu-id="e56ec-157">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="e56ec-158">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="e56ec-158">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="e56ec-159">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="e56ec-159">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e56ec-160">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="e56ec-160">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="e56ec-161">Hände – Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="e56ec-161">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="e56ec-162">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e56ec-162">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="e56ec-163">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="e56ec-163">Voice input</span></span>](voice-input.md)



