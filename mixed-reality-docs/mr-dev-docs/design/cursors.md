---
title: Cursor
description: Ein Cursor oder Indikator Ihres Ziel Vektor bietet fortlaufendes Feedback für den Benutzer, um zu verstehen, was hololens über seine Absichten versteht.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Hololens (1st Gen), hololens 2, Mixed Reality, Cursors, Zielplattform, Blick, Gesten, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Rays, Input
ms.openlocfilehash: 744e75f4212046b7c237a6c6634a4980e9148b0e
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300085"
---
# <a name="cursors"></a><span data-ttu-id="806bb-104">Cursor</span><span class="sxs-lookup"><span data-stu-id="806bb-104">Cursors</span></span>

![Cursor](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="806bb-106">Ein Cursor liefert Kontinuierliches Feedback, das darauf basiert, dass der Benutzer den aktuellen Fokus an einem bestimmten Zeitpunkt hat.</span><span class="sxs-lookup"><span data-stu-id="806bb-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="806bb-107">Cursor Feedback beinhaltet, welche Bereiche, holograms oder Punkte in der virtuellen Umgebung auf die Eingabe Antworten.</span><span class="sxs-lookup"><span data-stu-id="806bb-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="806bb-108">Obwohl es sich bei dem Cursor um eine digitale Darstellung von handelt, in der das Gerät die Aufmerksamkeit des Benutzers versteht, ist dies nicht dasselbe wie das Ermitteln der Absichten des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="806bb-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="806bb-109">Mit dem Cursor Feedback können Benutzer auch wissen, welche System Antworten erwartet werden.</span><span class="sxs-lookup"><span data-stu-id="806bb-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="806bb-110">Sie können das Feedback verwenden, um seine Absicht an das Gerät zu senden, was die Benutzer Zuverlässigkeit steigert.</span><span class="sxs-lookup"><span data-stu-id="806bb-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="806bb-111">Es gibt drei Arten von Cursorn: **Finger, Ray** und **Head-Gaze**.</span><span class="sxs-lookup"><span data-stu-id="806bb-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="806bb-112">Diese zeigenden Cursor funktionieren mit unterschiedlichen Eingabe Modalitäten für hololens, hololens 2 und immersive Headsets.</span><span class="sxs-lookup"><span data-stu-id="806bb-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="806bb-113">Im folgenden finden Sie Anleitungen dazu, welche Art von Cursor für die einzelnen Typen von Headset-und Interaktions Modellen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="806bb-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="806bb-114">Im Mixed Reality Toolkit (mrtk) haben wir Drag & amp; Drop-cursormodule erstellt, um Sie bei der Erstellung der richtigen Zeige Erfahrung zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="806bb-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="806bb-115">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="806bb-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="806bb-116"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="806bb-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="806bb-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="806bb-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="806bb-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="806bb-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="806bb-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="806bb-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="806bb-120">Finger Cursor</span><span class="sxs-lookup"><span data-stu-id="806bb-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="806bb-121">✔️</span><span class="sxs-lookup"><span data-stu-id="806bb-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="806bb-122">Strahl Cursor</span><span class="sxs-lookup"><span data-stu-id="806bb-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="806bb-123">✔️</span><span class="sxs-lookup"><span data-stu-id="806bb-123">✔️</span></span></td>
        <td><span data-ttu-id="806bb-124">✔️</span><span class="sxs-lookup"><span data-stu-id="806bb-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="806bb-125">Cursor Cursor</span><span class="sxs-lookup"><span data-stu-id="806bb-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="806bb-126">✔️</span><span class="sxs-lookup"><span data-stu-id="806bb-126">✔️</span></span></td>
        <td><span data-ttu-id="806bb-127">✔️</span><span class="sxs-lookup"><span data-stu-id="806bb-127">✔️</span></span></td>
        <td><span data-ttu-id="806bb-128">✔️</span><span class="sxs-lookup"><span data-stu-id="806bb-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="806bb-129">Finger Cursor</span><span class="sxs-lookup"><span data-stu-id="806bb-129">Finger cursor</span></span>

<span data-ttu-id="806bb-130">Der Finger Cursor ist nur auf den hololens 2 verfügbar, um den Interaktionsmodus "[direkte Bearbeitung von Hand](direct-manipulation.md)" zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="806bb-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="806bb-131">Wir haben Ringe an die Tipps beider Index Finger angehängt, um besser zu verstehen, wo der Finger zeigt.</span><span class="sxs-lookup"><span data-stu-id="806bb-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="806bb-132">Die Ring Größe basiert auf der Nähe des Fingers und der UI-Oberfläche, die auf einen kleinen Punkt verkleinert wird, wenn der Finger die Benutzeroberfläche berührt.</span><span class="sxs-lookup"><span data-stu-id="806bb-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="806bb-133">Je näher der Finger, desto kleiner der Ring.</span><span class="sxs-lookup"><span data-stu-id="806bb-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="806bb-134">![Finger Cursor](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="806bb-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="806bb-135">**Visuelle Feedback Zustände von Finger Cursor** 1: der Ring wird auf einen Punkt verkleinert.</span><span class="sxs-lookup"><span data-stu-id="806bb-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="806bb-136">2: der Ring richtet sich nach der Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="806bb-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="806bb-137">3: der Ring ist senkrecht zum Finger Vektor.</span><span class="sxs-lookup"><span data-stu-id="806bb-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="806bb-138">4: kein Ring.</span><span class="sxs-lookup"><span data-stu-id="806bb-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="806bb-139">Strahl Cursor</span><span class="sxs-lookup"><span data-stu-id="806bb-139">Ray cursor</span></span>

<span data-ttu-id="806bb-140">Ray-Cursors werden an das Ende von weit zeigenden Strahlen angehängt, um die Bearbeitung von Objekten zu ermöglichen, die nicht in der Hand reich sind.</span><span class="sxs-lookup"><span data-stu-id="806bb-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="806bb-141">In immersiven Headsets werden die Strahlen von Bewegungs Controllern abgeraten und mit Punkt Cursorn enden.</span><span class="sxs-lookup"><span data-stu-id="806bb-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="806bb-142">In hololens 2 wenden wir das geistige Modell dieser Motion Controller-Strahlen und entworfenen Hand Striche an, die aus den Palmen stammen und in ringförmigen Cursorn enden, die mit fingercursorn konsistent sind, die bei direkter Bearbeitung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="806bb-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="806bb-143">![Strahl Cursor Controller](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="806bb-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="806bb-144">**Strahl Cursor von Bewegungs Controllern**</span><span class="sxs-lookup"><span data-stu-id="806bb-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="806bb-145">![Strahl Cursor Hand](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="806bb-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="806bb-146">**Strahl Cursor von Händen**</span><span class="sxs-lookup"><span data-stu-id="806bb-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="806bb-147">Cursor Cursor</span><span class="sxs-lookup"><span data-stu-id="806bb-147">Head-gaze cursor</span></span>

<span data-ttu-id="806bb-148">Der Head-Gaze-Cursor ist ein Punkt, der an das Ende eines unsichtbaren Kopf Zeigers angefügt wird, der die Position und Drehung des Kopfes verwendet, um zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="806bb-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="806bb-149">Zum Ausführen von Aktionen wird dieser Zeige Cursor mit verschiedenen Commit-Eingaben gekoppelt, wie z. b. Air Tap, Voice Commands, Dwell und Button Press.</span><span class="sxs-lookup"><span data-stu-id="806bb-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="806bb-150">In hololens 2 ist die Kopfzeile am besten mit allen Commit-Eingaben gekoppelt, bei denen es sich nicht um Luft tippen handelt, da es zu Interaktions Konflikten zwischen Luft tippen und fern Strahlen kommt.</span><span class="sxs-lookup"><span data-stu-id="806bb-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="806bb-151">![Cursor Hand des Kopf Zeigers](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="806bb-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="806bb-152">**Cursor Cursor mit Handbewegung**</span><span class="sxs-lookup"><span data-stu-id="806bb-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="806bb-153">![Cursor Stimme für Head-Gaze](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="806bb-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="806bb-154">**Kopf zeiligen Cursor mit Sprachbefehl**</span><span class="sxs-lookup"><span data-stu-id="806bb-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="806bb-155">Empfehlungen für die Cursor Anpassung</span><span class="sxs-lookup"><span data-stu-id="806bb-155">Cursor customization recommendations</span></span>

<span data-ttu-id="806bb-156">Wenn Sie das Verhalten und den Anschein von Cursor Feedback anpassen möchten, finden Sie hier einige Entwurfs Empfehlungen:</span><span class="sxs-lookup"><span data-stu-id="806bb-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="806bb-157">Cursor Skala</span><span class="sxs-lookup"><span data-stu-id="806bb-157">Cursor scale</span></span>

* <span data-ttu-id="806bb-158">Der Cursor sollte nicht größer sein als die verfügbaren Ziele, sodass Benutzer problemlos mit dem Inhalt interagieren und ihn anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="806bb-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="806bb-159">Abhängig von der Umgebung, die Sie erstellen, ist das Skalieren des Cursors, wie der Benutzer aussieht, auch ein wichtiger Aspekt.</span><span class="sxs-lookup"><span data-stu-id="806bb-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="806bb-160">Beispielsweise sollte der Cursor nicht zu klein werden, da der Benutzer nicht mehr zu klein aussieht, sodass er verloren geht.</span><span class="sxs-lookup"><span data-stu-id="806bb-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="806bb-161">Beim Skalieren des Cursors sollten Sie eine weiche Animation darauf anwenden, während Sie skaliert wird, um ihr ein organisches Gefühl zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="806bb-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="806bb-162">Vermeiden Sie das Blockieren von Inhalt.</span><span class="sxs-lookup"><span data-stu-id="806bb-162">Avoid obstructing content.</span></span> <span data-ttu-id="806bb-163">Holograms machen das Erlebnis als unvergesslich, und der Cursor sollte nicht davon entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="806bb-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="806bb-164">Direktionlose Cursor Form</span><span class="sxs-lookup"><span data-stu-id="806bb-164">Directionless cursor shape</span></span>

* <span data-ttu-id="806bb-165">Obwohl es keine Rechte Cursor Form gibt, empfiehlt es sich, eine direktionale Form wie einen "Tor" zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="806bb-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="806bb-166">Ein Cursor, der in einer Richtung zeigt (z. b. ein herkömmlicher Pfeilcursor), kann den Benutzer so verwechseln, dass er immer auf diese Weise aussieht.</span><span class="sxs-lookup"><span data-stu-id="806bb-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="806bb-167">Eine Ausnahme besteht darin, dass der Cursor verwendet wird, um dem Benutzer Interaktions Anweisungen mitzuteilen.</span><span class="sxs-lookup"><span data-stu-id="806bb-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="806bb-168">Wenn z. b. Hologramme im Mixed Reality-Betriebssystem skaliert werden, schließt der Cursor temporär Pfeile ein, die den Benutzer darüber informiert, wie Sie seine Hand verschieben, um das Hologram zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="806bb-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="806bb-169">Aussehen und Gefühl</span><span class="sxs-lookup"><span data-stu-id="806bb-169">Look and feel</span></span>

* <span data-ttu-id="806bb-170">Ein Ring Diagramm oder ein mit einem Tor gegeformter Cursor funktioniert für viele Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="806bb-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="806bb-171">Wählen Sie eine Farbe und eine Form aus, die die von Ihnen erstellten Funktionen am besten repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="806bb-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="806bb-172">Cursor sind besonders anfällig für die [Trennung von Farben](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="806bb-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="806bb-173">Ein kleiner Cursor mit ausgewogener Deckkraft sorgt dafür, dass er informativ ist, ohne die visuelle Hierarchie zu dominieren.</span><span class="sxs-lookup"><span data-stu-id="806bb-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="806bb-174">Sie sollten die Verwendung von Shadowing oder Highlights hinter dem Cursor erkennen, da Sie Inhalte behindern und von der Aufgabe ablendieren können.</span><span class="sxs-lookup"><span data-stu-id="806bb-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="806bb-175">Cursor sollten sich an den Oberflächen in der APP ausrichten und diese umarmen.</span><span class="sxs-lookup"><span data-stu-id="806bb-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="806bb-176">Benutzer haben das Gefühl, dass Sie sehen können, wo Sie aussehen, aber auch, dass das System von Ihrer Umgebung weiß.</span><span class="sxs-lookup"><span data-stu-id="806bb-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="806bb-177">Der Cursor im Mixed Reality-Betriebssystem richtet sich z. b. an den Oberflächen der Benutzer Welt und sorgt so für das Bewusstsein der Welt, auch wenn der Benutzer nicht direkt auf ein Hologram zuschaut.</span><span class="sxs-lookup"><span data-stu-id="806bb-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="806bb-178">Das magnetisch Sperren des Cursors für ein interaktives Element, wenn es dem Benutzer nahe liegt, kann das Vertrauen verbessern, dass der Benutzer mit diesem Element interagiert, wenn eine Auswahl Aktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="806bb-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="806bb-179">Visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="806bb-179">Visual cues</span></span>

* <span data-ttu-id="806bb-180">Wenn Sie sich auf ein einzelnes Hologramm konzentrieren, sollte Ihr Cursor nur dieses – Hologramm ausrichten und die Form ändern, wenn Sie von diesem – Hologramm Weg gehen.</span><span class="sxs-lookup"><span data-stu-id="806bb-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="806bb-181">Dies kann dem Benutzer vermitteln, dass das – Hologramm handlungsfähig ist und mit ihm interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="806bb-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="806bb-182">Wenn Ihre Anwendung eine räumliche Zuordnung verwendet, könnte der Cursor jede sichtbare Oberfläche ausrichten und umarmen.</span><span class="sxs-lookup"><span data-stu-id="806bb-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="806bb-183">Dadurch erhalten die Benutzer Feedback, dass hololens und Ihre Anwendung Ihren Speicherplatz sehen können.</span><span class="sxs-lookup"><span data-stu-id="806bb-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="806bb-184">Dadurch wird die Tatsache verstärkt, dass holograms Real und in unserer Welt sind und die Lücke zwischen Real und Virtual überbrücken.</span><span class="sxs-lookup"><span data-stu-id="806bb-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="806bb-185">Sehen Sie sich an, was der Cursor tun soll, wenn keine holograms oder Oberflächen in der Ansicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="806bb-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="806bb-186">Eine Möglichkeit besteht darin, den Benutzer in einem vordefinierten Abstand vor dem Benutzer zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="806bb-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="806bb-187">Mögliche Aktionen</span><span class="sxs-lookup"><span data-stu-id="806bb-187">Possible actions</span></span>

* <span data-ttu-id="806bb-188">Der Cursor kann durch verschiedene Symbole dargestellt werden, um mögliche Aktionen zu vermitteln, die ein Hologramm ausführen kann, z. b. Skalierung oder Drehung.</span><span class="sxs-lookup"><span data-stu-id="806bb-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="806bb-189">Fügen Sie dem Cursor nur dann zusätzliche Informationen hinzu, wenn er etwas für den Benutzer bedeutet.</span><span class="sxs-lookup"><span data-stu-id="806bb-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="806bb-190">Andernfalls bemerken die Benutzer möglicherweise nicht, dass sich der Status ändert, oder Sie werden durch den Cursor verwirrt.</span><span class="sxs-lookup"><span data-stu-id="806bb-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="806bb-191">Eingabe Status</span><span class="sxs-lookup"><span data-stu-id="806bb-191">Input state</span></span>

* <span data-ttu-id="806bb-192">Der Cursor kann verwendet werden, um den Eingabe Zustand oder die Absicht des Benutzers anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="806bb-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="806bb-193">Beispielsweise könnte ein Symbol angezeigt werden, das dem Benutzer mitteilt, dass das System seinen Hand Zustand hat und die Anwendung weiß, dass Sie bereit sind, Maßnahmen zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="806bb-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="806bb-194">Wir könnten auch den Cursor verwenden, um Benutzern anzuzeigen, dass Sprachbefehle vom System über eine Änderung der momentanen Farbe gehört wurden.</span><span class="sxs-lookup"><span data-stu-id="806bb-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="806bb-195">Die folgenden Cursor Zustände können auf unterschiedliche Weise implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="806bb-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="806bb-196">Sie können diese verschiedenen Zustände implementieren, indem Sie den Cursor wie einen Zustands Automat modellieren.</span><span class="sxs-lookup"><span data-stu-id="806bb-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="806bb-197">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="806bb-197">For example:</span></span>
    * <span data-ttu-id="806bb-198">Im Leerlaufzustand wird der Standard Cursor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="806bb-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="806bb-199">Der Status "bereit" ist, wenn Sie festgestellt haben, dass der Benutzer die Hand hat.</span><span class="sxs-lookup"><span data-stu-id="806bb-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="806bb-200">Der Interaktions Zustand ist, wenn der Benutzer eine bestimmte Interaktion durch nimmt.</span><span class="sxs-lookup"><span data-stu-id="806bb-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="806bb-201">Der Status "mögliche Aktionen" oder "Hover" ist, wenn Sie mögliche Aktionen übermitteln, die für ein Hologram ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="806bb-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="806bb-202">Sie können diese Zustände auch in einer auf der Skin-Sicht basierenden Weise implementieren, um verschiedene Kunst Ressourcen anzuzeigen, wenn Sie verschiedene Zustände erkennen.</span><span class="sxs-lookup"><span data-stu-id="806bb-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="806bb-203">"Cursor frei"</span><span class="sxs-lookup"><span data-stu-id="806bb-203">Going "cursor-free"</span></span>

<span data-ttu-id="806bb-204">Das Entwerfen ohne Cursor wird empfohlen, wenn das Eintauchen eine wichtige Komponente einer-Funktion ist und wenn die Zeige Interaktionen (durchschauen und Gesten) keine hohe Genauigkeit erfordern.</span><span class="sxs-lookup"><span data-stu-id="806bb-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="806bb-205">Das System muss immer noch die normalen Anforderungen eines Cursors erfüllen: die Benutzer erhalten fortlaufend Feedback zum System, das sich auf das Verständnis des Systems hinweist, und unterstützen Sie bei der Kommunikation mit dem System.</span><span class="sxs-lookup"><span data-stu-id="806bb-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="806bb-206">Dies kann durch andere spürbare Zustandsänderungen erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="806bb-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="806bb-207">Cursor im mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="806bb-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="806bb-208">Standardmäßig stellt [mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) eine Cursor-vorfab ([DefaultCursor. Prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) bereit, die denselben visuellen Zustand aufweist wie der System Cursor der Shell.</span><span class="sxs-lookup"><span data-stu-id="806bb-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="806bb-209">Es wird im Eingabeprofil des MRTK unter „Zeiger“ zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="806bb-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="806bb-210">Sie können diesen Cursor für Ihre Benutzeroberflächen ersetzen/anpassen.</span><span class="sxs-lookup"><span data-stu-id="806bb-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="806bb-211">Für die Verwendung von Eye-Tracking-Eingaben bietet mrtk auch den "eyegazecursor", der über eine feine Visualisierung verfügt, um die Ablenkung zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="806bb-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="806bb-212">MRTK – Zeigerprofil</span><span class="sxs-lookup"><span data-stu-id="806bb-212">MRTK - Pointer profile</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [<span data-ttu-id="806bb-213">MRTK – Eingabesystem</span><span class="sxs-lookup"><span data-stu-id="806bb-213">MRTK - Input system</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview)
* [<span data-ttu-id="806bb-214">MRTK – Zeiger</span><span class="sxs-lookup"><span data-stu-id="806bb-214">MRTK - Pointers</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a><span data-ttu-id="806bb-215">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="806bb-215">See also</span></span>

* [<span data-ttu-id="806bb-216">Gesten</span><span class="sxs-lookup"><span data-stu-id="806bb-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="806bb-217">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="806bb-217">Head-gaze and commit</span></span>](gaze-and-commit.md)