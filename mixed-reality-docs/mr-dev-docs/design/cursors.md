---
title: Cursor
description: Ein Cursor oder Indikator ihres Zielvektors gibt dem Benutzer fortlaufendEs Feedback, um zu verstehen, was HoloLens über ihre Absichten versteht.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1. Generation), HoloLens 2, Mixed Reality, Cursor, Ziel, Anvisiert, Gesten, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Lichtstrahl, Eingabe
ms.openlocfilehash: 829d7b3f766f848228946ee0a623f9f3013adca3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600379"
---
# <a name="cursors"></a><span data-ttu-id="7547e-104">Cursor</span><span class="sxs-lookup"><span data-stu-id="7547e-104">Cursors</span></span>

![Cursor](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="7547e-106">Ein Cursor liefert kontinuierliches Feedback, je nach dem Ort, an dem das Headset der Meinung ist, dass ein Benutzer zu einem bestimmten Zeitpunkt den aktuellen Fokus hat.</span><span class="sxs-lookup"><span data-stu-id="7547e-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="7547e-107">Cursorfeedback umfasst, welcher Bereich, Hologramm oder Punkt in der virtuellen Umgebung auf Eingaben reagiert.</span><span class="sxs-lookup"><span data-stu-id="7547e-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="7547e-108">Obwohl der Cursor eine digitale Darstellung der Stelle ist, an der das Gerät die Aufmerksamkeit des Benutzers versteht, ist dies nicht dasselbe wie das Bestimmen der Absichten des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="7547e-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="7547e-109">Das Cursorfeedback informiert Benutzer auch darüber, welche Systemantworten zu erwarten sind.</span><span class="sxs-lookup"><span data-stu-id="7547e-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="7547e-110">Sie können das Feedback verwenden, um ihre Absicht an das Gerät zu übermitteln, wodurch das Vertrauen der Benutzer erhöht wird.</span><span class="sxs-lookup"><span data-stu-id="7547e-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="7547e-111">Es gibt drei Arten von Cursorn: **Finger, Strahl** und **Anvistik mit dem Kopf.**</span><span class="sxs-lookup"><span data-stu-id="7547e-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="7547e-112">Diese zeigenden Cursor funktionieren mit verschiedenen Eingabemodalitäten auf HoloLens, HoloLens 2 und immersiven Headsets.</span><span class="sxs-lookup"><span data-stu-id="7547e-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="7547e-113">Im Folgenden wird erläutert, welcher Cursortyp für die einzelnen Headset- und Interaktionsmodelltypen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="7547e-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="7547e-114">Im Mixed Reality Toolkit (MRTK) haben wir Drag & Drop-Cursormodule erstellt, mit deren Hilfe Sie die richtige Pointing-Erfahrung erstellen können.</span><span class="sxs-lookup"><span data-stu-id="7547e-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="7547e-115">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="7547e-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7547e-116"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="7547e-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="7547e-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7547e-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7547e-118"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7547e-118"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7547e-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="7547e-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7547e-120">Fingercursor</span><span class="sxs-lookup"><span data-stu-id="7547e-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="7547e-121">✔️</span><span class="sxs-lookup"><span data-stu-id="7547e-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="7547e-122">Ray cursor (Raycursor)</span><span class="sxs-lookup"><span data-stu-id="7547e-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="7547e-123">✔️</span><span class="sxs-lookup"><span data-stu-id="7547e-123">✔️</span></span></td>
        <td><span data-ttu-id="7547e-124">✔️</span><span class="sxs-lookup"><span data-stu-id="7547e-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7547e-125">Cursor mit dem Kopf</span><span class="sxs-lookup"><span data-stu-id="7547e-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="7547e-126">✔️</span><span class="sxs-lookup"><span data-stu-id="7547e-126">✔️</span></span></td>
        <td><span data-ttu-id="7547e-127">✔️</span><span class="sxs-lookup"><span data-stu-id="7547e-127">✔️</span></span></td>
        <td><span data-ttu-id="7547e-128">✔️</span><span class="sxs-lookup"><span data-stu-id="7547e-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="7547e-129">Fingercursor</span><span class="sxs-lookup"><span data-stu-id="7547e-129">Finger cursor</span></span>

<span data-ttu-id="7547e-130">Der Fingercursor ist nur auf dem HoloLens 2, um den Interaktionsmodus "Direkte Bearbeitung[mit Händen"](direct-manipulation.md)zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="7547e-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="7547e-131">Wir haben Ringe an die Spitzen beider Zeigefinger angefügt, um besser zu verstehen, wo der Finger zeigen soll.</span><span class="sxs-lookup"><span data-stu-id="7547e-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="7547e-132">Die Ringgröße basiert auf der Nähe des Fingers zur Benutzeroberflächenoberfläche, die auf einen kleinen Punkt verkleinert wird, wenn der Finger die Benutzeroberfläche berührt.</span><span class="sxs-lookup"><span data-stu-id="7547e-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="7547e-133">Je näher der Finger, desto kleiner der Ring.</span><span class="sxs-lookup"><span data-stu-id="7547e-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="7547e-134">![Fingercursor](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="7547e-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="7547e-135">**Visuelle Feedbackzustände des Fingercursors** 1: Der Ring wird auf einen Punkt verkleinert.</span><span class="sxs-lookup"><span data-stu-id="7547e-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="7547e-136">2: Der Ring wird an der Oberfläche ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="7547e-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="7547e-137">3: Der Ring ist senkrecht zum Fingervektor.</span><span class="sxs-lookup"><span data-stu-id="7547e-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="7547e-138">4: Kein Ring.</span><span class="sxs-lookup"><span data-stu-id="7547e-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="7547e-139">Ray cursor (Raycursor)</span><span class="sxs-lookup"><span data-stu-id="7547e-139">Ray cursor</span></span>

<span data-ttu-id="7547e-140">Ray cursors attach to the end of far pointing ray to allow manipulation of objects that are out-reach.</span><span class="sxs-lookup"><span data-stu-id="7547e-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="7547e-141">Bei immersiven Headsets werden die Lichtstrahle von Motion-Controllern entfernt und enden mit Punktcursorn.</span><span class="sxs-lookup"><span data-stu-id="7547e-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="7547e-142">In HoloLens 2 wenden wir das mentale Modell dieser Motion Controller-Lichtstrahle und entworfenen Handlichtlichter an, die von den Handflächen stammen und in ringförmigen Cursorn enden, die mit Fingercursorn konsistent sind, die bei der direkten Manipulation verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7547e-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="7547e-143">![Ray cursor controller (Raycursorcontroller)](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="7547e-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="7547e-144">**Raycursor von Motion-Controllern**</span><span class="sxs-lookup"><span data-stu-id="7547e-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="7547e-145">![Ray-Cursorhand](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="7547e-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="7547e-146">**Ray cursors of hands (Raycursor der Hände)**</span><span class="sxs-lookup"><span data-stu-id="7547e-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="7547e-147">Cursor mit dem Kopf</span><span class="sxs-lookup"><span data-stu-id="7547e-147">Head-gaze cursor</span></span>

<span data-ttu-id="7547e-148">Der Cursor mit dem Kopf ist ein Punkt, der an das Ende eines unsichtbaren Vektors zum Anvieren mit dem Kopf angefügt wird, der die Position und Drehung des Kopfs verwendet, um zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="7547e-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="7547e-149">Um Aktionen auszuführen, wird dieser zeigende Cursor mit verschiedenen Commiteingaben gekoppelt, z. B. Tippen in die Luft, Sprachbefehle, Verweildauer und Tastendruck.</span><span class="sxs-lookup"><span data-stu-id="7547e-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="7547e-150">In HoloLens 2 ist das Anvieren mit dem Kopf am besten mit commit-Eingaben gekoppelt, bei denen es sich nicht um Tippen in die Luft handelt, da es zu Interaktionskonflikten zwischen dem Tippen in die Luft und fernen Handstrahl kommt.</span><span class="sxs-lookup"><span data-stu-id="7547e-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="7547e-151">![Cursorhand zum Anvingen mit dem Kopf](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="7547e-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="7547e-152">**Cursor mit Dem Kopf mit der Hand**</span><span class="sxs-lookup"><span data-stu-id="7547e-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="7547e-153">![Cursorstimme mit dem Kopf](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="7547e-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="7547e-154">**Cursor mit Dem Kopf anvauf mit Sprachbefehl**</span><span class="sxs-lookup"><span data-stu-id="7547e-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="7547e-155">Empfehlungen zur Cursoranpassung</span><span class="sxs-lookup"><span data-stu-id="7547e-155">Cursor customization recommendations</span></span>

<span data-ttu-id="7547e-156">Wenn Sie das Verhalten und die Darstellung des Cursorfeedbacks anpassen möchten, finden Sie hier einige Entwurfsempfehlungen:</span><span class="sxs-lookup"><span data-stu-id="7547e-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="7547e-157">Cursorskalieren</span><span class="sxs-lookup"><span data-stu-id="7547e-157">Cursor scale</span></span>

* <span data-ttu-id="7547e-158">Der Cursor sollte nicht größer als die verfügbaren Ziele sein, sodass Benutzer problemlos mit dem Inhalt interagieren und diesen anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="7547e-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="7547e-159">Abhängig von der Umgebung, die Sie erstellen, ist auch das Skalieren des Cursors während des Durchsendens des Benutzers ein wichtiger Aspekt.</span><span class="sxs-lookup"><span data-stu-id="7547e-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="7547e-160">Wenn der Benutzer z. B. weiter in Ihrer Benutzeroberfläche nachsieht, sollte der Cursor nicht zu klein werden, damit er verloren geht.</span><span class="sxs-lookup"><span data-stu-id="7547e-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="7547e-161">Erwägen Sie beim Skalieren des Cursors, eine weiche Animation darauf zu anwenden, während er skaliert wird, um ihm ein biofarbenes Gefühl zu verleihen.</span><span class="sxs-lookup"><span data-stu-id="7547e-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="7547e-162">Vermeiden Sie das Verhindern von Inhalten.</span><span class="sxs-lookup"><span data-stu-id="7547e-162">Avoid obstructing content.</span></span> <span data-ttu-id="7547e-163">Hologramme machen die Erfahrung einprägsam, und der Cursor sollte sie nicht weg nehmen.</span><span class="sxs-lookup"><span data-stu-id="7547e-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="7547e-164">Richtungslose Cursorform</span><span class="sxs-lookup"><span data-stu-id="7547e-164">Directionless cursor shape</span></span>

* <span data-ttu-id="7547e-165">Obwohl es keine rechte Cursorform gibt, wird empfohlen, eine richtungslose Form wie einen Torus zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7547e-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="7547e-166">Ein Cursor, der in eine bestimmte Richtung zeigt (z. B. ein herkömmlicher Pfeilcursor), kann den Benutzer verwirren, immer so zu suchen.</span><span class="sxs-lookup"><span data-stu-id="7547e-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="7547e-167">Eine Ausnahme ist die Verwendung des Cursors, um dem Benutzer Interaktionsanweisungen zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="7547e-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="7547e-168">Wenn Sie beispielsweise Hologramme im Mixed Reality-Betriebssystem skalieren, enthält der Cursor vorübergehend Pfeile, die den Benutzer anweisen, seine Hand zum Skalieren des Hologramms zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="7547e-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="7547e-169">Aussehen und Fühl</span><span class="sxs-lookup"><span data-stu-id="7547e-169">Look and feel</span></span>

* <span data-ttu-id="7547e-170">Ein donut- oder torusförmiger Cursor funktioniert für viele Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="7547e-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="7547e-171">Wählen Sie eine Farbe und Form aus, die die von Ihnen erstellten Erfahrungen am besten darstellt.</span><span class="sxs-lookup"><span data-stu-id="7547e-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="7547e-172">Cursor sind besonders anfällig für die [Farbtrennung.](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)</span><span class="sxs-lookup"><span data-stu-id="7547e-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="7547e-173">Ein kleiner Cursor mit ausgeglichener Deckkraft sorgt dafür, dass er informativ bleibt, ohne die visuelle Hierarchie zu überbeenden.</span><span class="sxs-lookup"><span data-stu-id="7547e-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="7547e-174">Seien Sie sich über die Verwendung von Schatten oder Highlights hinter dem Cursor auskennend, da sie den Inhalt verhinderen und von der aufgabe in der Hand ablenken können.</span><span class="sxs-lookup"><span data-stu-id="7547e-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="7547e-175">Cursor sollten an den Oberflächen in Ihrer App ausgerichtet und darauf ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="7547e-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="7547e-176">Benutzer werden das Gefühl haben, dass das System sehen kann, wo sie suchen, aber auch, dass das System seine Umgebung kennt.</span><span class="sxs-lookup"><span data-stu-id="7547e-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="7547e-177">Beispielsweise richtet sich der Cursor im Mixed Reality-Betriebssystem an den Oberflächen der Welt des Benutzers aus und schafft so ein Gefühl des Bewusstseins über die Welt, auch wenn der Benutzer nicht direkt auf ein Hologramm blickt.</span><span class="sxs-lookup"><span data-stu-id="7547e-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="7547e-178">Das magnetisch sperrende Sperren des Cursors auf ein interaktives Element in der Nähe des Benutzers kann dazu beitragen, die Sicherheit zu erhöhen, dass der Benutzer mit diesem Element interagiert, wenn er eine Auswahlaktion verwendet.</span><span class="sxs-lookup"><span data-stu-id="7547e-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="7547e-179">Visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="7547e-179">Visual cues</span></span>

* <span data-ttu-id="7547e-180">Wenn Sich Ihre Erfahrung auf ein einzelnes Hologramm konzentriert, sollte der Cursor nur dieses Hologramm ausrichten und anordnen und die Form ändern, wenn Sie von diesem Hologramm wegschauen.</span><span class="sxs-lookup"><span data-stu-id="7547e-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="7547e-181">Dies kann dem Benutzer vermitteln, dass das Hologramm umsetzbar ist und mit ihm interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="7547e-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="7547e-182">Wenn Ihre Anwendung die räumliche Zuordnung verwendet, kann der Cursor jede angezeigte Oberfläche ausrichten und besingen.</span><span class="sxs-lookup"><span data-stu-id="7547e-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="7547e-183">Dadurch erhalten die Benutzer Feedback, dass HoloLens und Ihre Anwendung ihren Raum sehen können.</span><span class="sxs-lookup"><span data-stu-id="7547e-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="7547e-184">Dies verstärkt die Tatsache, dass Hologramme real und in unserer Welt sind, und hilft dabei, die Lücke zwischen real und virtuell zu schließen.</span><span class="sxs-lookup"><span data-stu-id="7547e-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="7547e-185">Sie haben eine Vorstellung davon, was der Cursor tun soll, wenn keine Hologramme oder Oberflächen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7547e-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="7547e-186">Die Platzierung in einem vordefinierten Abstand vor dem Benutzer ist eine Option.</span><span class="sxs-lookup"><span data-stu-id="7547e-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="7547e-187">Mögliche Aktionen</span><span class="sxs-lookup"><span data-stu-id="7547e-187">Possible actions</span></span>

* <span data-ttu-id="7547e-188">Der Cursor kann durch verschiedene Symbole dargestellt werden, um mögliche Aktionen zu vermitteln, die ein Hologramm ausführen kann, z. B. Skalierung oder Drehung.</span><span class="sxs-lookup"><span data-stu-id="7547e-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="7547e-189">Fügen Sie dem Cursor nur zusätzliche Informationen hinzu, wenn dies für den Benutzer etwas bedeutet.</span><span class="sxs-lookup"><span data-stu-id="7547e-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="7547e-190">Andernfalls bemerken Benutzer die Statusänderungen möglicherweise nicht oder werden durch den Cursor verwirrend.</span><span class="sxs-lookup"><span data-stu-id="7547e-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="7547e-191">Eingabezustand</span><span class="sxs-lookup"><span data-stu-id="7547e-191">Input state</span></span>

* <span data-ttu-id="7547e-192">Wir können den Cursor verwenden, um den Eingabezustand oder die Absicht des Benutzers anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7547e-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="7547e-193">Beispielsweise könnten wir ein Symbol anzeigen, das dem Benutzer den Handzustand zeigt und die Anwendung weiß, dass er bereit ist, Maßnahmen zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="7547e-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="7547e-194">Wir könnten auch den Cursor verwenden, um Benutzern zu zeigen, dass Sprachbefehle vom System durch eine momentäre Farbänderung gehört wurden.</span><span class="sxs-lookup"><span data-stu-id="7547e-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="7547e-195">Die folgenden Cursorzustände können auf unterschiedliche Weise implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="7547e-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="7547e-196">Sie können diese verschiedenen Zustände implementieren, indem Sie den Cursor wie einen Zustandscomputer modellieren.</span><span class="sxs-lookup"><span data-stu-id="7547e-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="7547e-197">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7547e-197">For example:</span></span>
    * <span data-ttu-id="7547e-198">Im Leerlaufzustand wird der Standardcursor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7547e-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="7547e-199">Der Status Bereit ist , wenn Sie die Hand des Benutzers an der bereiten Position erkannt haben.</span><span class="sxs-lookup"><span data-stu-id="7547e-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="7547e-200">Der Interaktionszustand ist, wenn der Benutzer eine bestimmte Interaktion vor sich hat.</span><span class="sxs-lookup"><span data-stu-id="7547e-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="7547e-201">Der Status "Mögliche Aktionen" oder der Zustand des Mauszeigers ist , wenn Sie mögliche Aktionen vermitteln, die für ein Hologramm ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="7547e-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="7547e-202">Sie können diese Zustände auch auf eine skinfähige Weise implementieren, um verschiedene Objekte für Dies zu zeigen, wenn Sie unterschiedliche Zustände erkennen.</span><span class="sxs-lookup"><span data-stu-id="7547e-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="7547e-203">"Cursorfrei"</span><span class="sxs-lookup"><span data-stu-id="7547e-203">Going "cursor-free"</span></span>

<span data-ttu-id="7547e-204">Das Entwerfen ohne Cursor wird empfohlen, wenn das Gefühl der Immersion eine wichtige Komponente einer Erfahrung ist und wenn das Zeigen von Interaktionen (durch Anvieren und Gesten) keine große Genauigkeit erfordert.</span><span class="sxs-lookup"><span data-stu-id="7547e-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="7547e-205">Das System muss weiterhin die normalen Anforderungen eines Cursors erfüllen: Benutzer erhalten kontinuierliches Feedback zum Systemverständnis ihrer Punkte und unterstützen sie bei der Kommunikation ihrer Absichten mit dem System.</span><span class="sxs-lookup"><span data-stu-id="7547e-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="7547e-206">Dies kann durch andere merkliche Zustandsänderungen erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="7547e-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="7547e-207">Cursor im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="7547e-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="7547e-208">Standardmäßig stellt [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) ein Cursorprefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) bereit, das den gleichen visuellen Zustand wie der Systemcursor der Shell hat.</span><span class="sxs-lookup"><span data-stu-id="7547e-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="7547e-209">Es wird im Eingabeprofil des MRTK unter „Zeiger“ zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="7547e-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="7547e-210">Sie können diesen Cursor für Ihre Benutzeroberfläche ersetzen/anpassen.</span><span class="sxs-lookup"><span data-stu-id="7547e-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="7547e-211">Für die Erfahrung mit Blickverfolgungseingaben stellt MRTK auch EyeGazeCursor bereit, das über ein dezentes Visuelles verfügt, um die Ablenkung zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="7547e-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="7547e-212">MRTK – Zeigerprofil</span><span class="sxs-lookup"><span data-stu-id="7547e-212">MRTK - Pointer profile</span></span>](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [<span data-ttu-id="7547e-213">MRTK – Eingabesystem</span><span class="sxs-lookup"><span data-stu-id="7547e-213">MRTK - Input system</span></span>](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [<span data-ttu-id="7547e-214">MRTK – Zeiger</span><span class="sxs-lookup"><span data-stu-id="7547e-214">MRTK - Pointers</span></span>](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a><span data-ttu-id="7547e-215">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7547e-215">See also</span></span>

* [<span data-ttu-id="7547e-216">Gesten</span><span class="sxs-lookup"><span data-stu-id="7547e-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="7547e-217">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="7547e-217">Head-gaze and commit</span></span>](gaze-and-commit.md)