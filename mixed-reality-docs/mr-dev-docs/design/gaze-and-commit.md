---
title: Anvisieren und Bestätigen
description: Erfahren Sie mehr über das Eingabe Modell für den Blick und das Commit, einschließlich zwei Arten von Blick (Kopf-und Augenblick) und verschiedene Commit-Typen.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Gemischte Realität, Blick, Blick auf das Ziel, Interaktion, Entwurf, Augen Verfolgung, Head-Tracking, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: bfbf58ad065f91b27208d36ba63672ee5c28dfdd
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582332"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="1d964-104">Anvisieren und Bestätigen</span><span class="sxs-lookup"><span data-stu-id="1d964-104">Gaze and commit</span></span>

<span data-ttu-id="1d964-105">" _Blick" und "Commit_ " ist ein grundlegendes Eingabe Modell, das eng mit der Interaktion mit unseren Computern verknüpft ist, indem Sie die Maus: Punkt- _& klicken_.</span><span class="sxs-lookup"><span data-stu-id="1d964-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="1d964-106">Auf dieser Seite stellen wir zwei Arten von Blick Eingaben (Head-and-Eye-Eye) und verschiedene Typen von COMMIT-Aktionen vor.</span><span class="sxs-lookup"><span data-stu-id="1d964-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="1d964-107">Der _Blick und der Commit_ werden als ein weit reichtes Eingabe Modell mit indirekter Bearbeitung betrachtet.</span><span class="sxs-lookup"><span data-stu-id="1d964-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="1d964-108">Es eignet sich am besten für die Interaktion mit Holographic Content, der nicht erreichbar ist.</span><span class="sxs-lookup"><span data-stu-id="1d964-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="1d964-109">Gemischte Reality-Headsets können die Position und Ausrichtung des Benutzer Kopfes verwenden, um den Kopf Richtung Vektor zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="1d964-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="1d964-110">Betrachten Sie den Blick als ein Laser, das direkt zwischen den Augen des Benutzers zeigt.</span><span class="sxs-lookup"><span data-stu-id="1d964-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="1d964-111">Dies ist eine ziemlich grobe Annäherung hinsichtlich der Position, die der Benutzer betrachtet.</span><span class="sxs-lookup"><span data-stu-id="1d964-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="1d964-112">Die Anwendung kann diesen Strahl mit virtuellen oder echten Objekten überschneiden und einen Cursor an dieser Stelle zeichnen, um dem Benutzer mitzuteilen, was er als Ziel hat.</span><span class="sxs-lookup"><span data-stu-id="1d964-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="1d964-113">Zusätzlich zu den Köpfen können einige gemischte Reality-Headsets, wie hololens 2, Eye Tracking-Systeme einschließen, die einen Blick Vektor liefern.</span><span class="sxs-lookup"><span data-stu-id="1d964-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="1d964-114">Dies ermöglicht eine präzisere Messung der Position, die der Benutzer betrachtet.</span><span class="sxs-lookup"><span data-stu-id="1d964-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="1d964-115">In beiden Fällen stellt der Blick ein wichtiges Signal für die Absicht des Benutzers dar.</span><span class="sxs-lookup"><span data-stu-id="1d964-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="1d964-116">Umso besser kann das System die beabsichtigten Aktionen des Benutzers interpretieren und Vorhersagen, desto mehr Benutzer Zufriedenheit und Leistung werden verbessert.</span><span class="sxs-lookup"><span data-stu-id="1d964-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="1d964-117">Im folgenden finden Sie einige Beispiele für die Art und Weise, wie Sie als Entwickler mit gemischter Realität von der Kopf-oder dem Augenblick profitieren können:</span><span class="sxs-lookup"><span data-stu-id="1d964-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="1d964-118">Ihre APP kann den Blick mit den holograms in Ihrer Szene überschneiden, um zu bestimmen, an welcher Stelle die Aufmerksamkeit des Benutzers (genauer mit dem Augenblick) liegt.</span><span class="sxs-lookup"><span data-stu-id="1d964-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="1d964-119">Ihre APP kann Gesten und Controller-Pressen basierend auf dem Blick des Benutzers leiten, sodass der Benutzer ihre Hologramme nahtlos auswählen, aktivieren, erfassen, Scrollen oder anderweitig interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="1d964-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="1d964-120">Ihre APP ermöglicht dem Benutzer das Platzieren von holograms auf realen Oberflächen, indem er seinen Blick Strahl mit dem räumlichen Mapping-Gitter schneidet.</span><span class="sxs-lookup"><span data-stu-id="1d964-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="1d964-121">Ihre APP kann wissen, wenn der Benutzer nicht in der Richtung eines wichtigen Objekts sucht, was dazu führen kann, dass Ihre APP visuelle und Audiohinweise zum Umwandeln des Objekts erhält.</span><span class="sxs-lookup"><span data-stu-id="1d964-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="1d964-122">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="1d964-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1d964-123"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="1d964-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="1d964-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1d964-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1d964-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1d964-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1d964-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="1d964-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1d964-127">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="1d964-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="1d964-128">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="1d964-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="1d964-129">✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</span><span class="sxs-lookup"><span data-stu-id="1d964-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="1d964-130">➕ Alternative Option</span><span class="sxs-lookup"><span data-stu-id="1d964-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="1d964-131">Anvisieren mit den Augen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="1d964-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="1d964-132">❌ Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="1d964-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="1d964-133">✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</span><span class="sxs-lookup"><span data-stu-id="1d964-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="1d964-134">❌ Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="1d964-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="1d964-135">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="1d964-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="1d964-136">Augen-oder Haupt Blick?</span><span class="sxs-lookup"><span data-stu-id="1d964-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="1d964-137">Bei der Frage, ob Sie das Eingabe Modell "Eye-Eye und Commit" oder "Head-Gaze und Commit" verwenden sollten, müssen Sie mehrere Aspekte berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="1d964-137">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="1d964-138">Wenn Sie für ein immersives Headset oder hololens (1. Generation) entwickeln, ist die Wahl einfach: Head-Gaze und Commit.</span><span class="sxs-lookup"><span data-stu-id="1d964-138">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="1d964-139">Wenn Sie für hololens 2 entwickeln, wird die Auswahl etwas erschwert.</span><span class="sxs-lookup"><span data-stu-id="1d964-139">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="1d964-140">Es ist wichtig, sich mit den Vorteilen und Herausforderungen vertraut zu machen, die in den einzelnen Komponenten enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="1d964-140">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="1d964-141">Wir haben einige umfassende pro-und-con in der nachfolgenden Tabelle kompiliert, um die Zielvorgabe für das Ziel zu vergleichen.</span><span class="sxs-lookup"><span data-stu-id="1d964-141">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="1d964-142">Dieser Vorgang ist weit von der Fertigstellung entfernt, und wir empfehlen, dass Sie hier mehr über die Ausrichtung des Augenblicks erfahren:</span><span class="sxs-lookup"><span data-stu-id="1d964-142">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="1d964-143">[Eye Tracking on hololens 2](eye-tracking.md): Allgemeine Einführung in unsere neue Funktion für die Augen Verfolgung auf hololens 2, einschließlich einiger Entwickler Anleitungen.</span><span class="sxs-lookup"><span data-stu-id="1d964-143">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="1d964-144">[Interaktion](eye-gaze-interaction.md)mit Blick auf das Auge: Entwurfs Überlegungen und Empfehlungen bei der Planung der Verwendung von Eye Tracking als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="1d964-144">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="1d964-145"><strong>Ziel Ausrichtung</strong></span><span class="sxs-lookup"><span data-stu-id="1d964-145"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="1d964-146"><strong>Anvisieren mit dem Kopf</strong></span><span class="sxs-lookup"><span data-stu-id="1d964-146"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1d964-147">Schnelle!</span><span class="sxs-lookup"><span data-stu-id="1d964-147">Fast!</span></span></td>
        <td><span data-ttu-id="1d964-148">Voran</span><span class="sxs-lookup"><span data-stu-id="1d964-148">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1d964-149">Niedriger Aufwand (kaum Text Bewegungen notwendig)</span><span class="sxs-lookup"><span data-stu-id="1d964-149">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="1d964-150">Mögliche Unannehmlichkeiten (z. b. Hals Belastung)</span><span class="sxs-lookup"><span data-stu-id="1d964-150">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1d964-151">Erfordert keinen Cursor, aber es wird ein feines Feedback empfohlen.</span><span class="sxs-lookup"><span data-stu-id="1d964-151">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="1d964-152">Erfordert, dass ein Cursor angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1d964-152">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1d964-153">Keine Smooth Eye-Bewegungen – z. b. nicht gut zum Zeichnen</span><span class="sxs-lookup"><span data-stu-id="1d964-153">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="1d964-154">Kontrollierter und expliziter</span><span class="sxs-lookup"><span data-stu-id="1d964-154">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1d964-155">Schwierig für kleine Ziele (z. b. kleine Schaltflächen oder Weblinks)</span><span class="sxs-lookup"><span data-stu-id="1d964-155">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="1d964-156">Zuverlässiges!</span><span class="sxs-lookup"><span data-stu-id="1d964-156">Reliable!</span></span> <span data-ttu-id="1d964-157">Großartiger Fallback!</span><span class="sxs-lookup"><span data-stu-id="1d964-157">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1d964-158">...</span><span class="sxs-lookup"><span data-stu-id="1d964-158">...</span></span></td>
        <td><span data-ttu-id="1d964-159">...</span><span class="sxs-lookup"><span data-stu-id="1d964-159">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="1d964-160">Unabhängig davon, ob Sie den Kopf-oder Augenblick für das Eingabe Modell von Blick und Commit verwenden, sind jeweils unterschiedliche Sätze von Entwurfs Einschränkungen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1d964-160">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="1d964-161">Diese werden separat in den Artikeln " [Eye-Blick" und "Commit](gaze-and-commit-eyes.md) " und " [Head-Blick" und "Commit](gaze-and-commit-head.md) " behandelt.</span><span class="sxs-lookup"><span data-stu-id="1d964-161">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="1d964-162">Cursor</span><span class="sxs-lookup"><span data-stu-id="1d964-162">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1d964-163">Für den Kopf Blick sollten die meisten apps einen [Cursor](cursors.md) oder eine andere Auditory-/Visualisierungs-oder visuelle Anzeige verwenden, um dem Benutzer die Gewissheit zu verschaffen, mit welchem Element er interagiert.</span><span class="sxs-lookup"><span data-stu-id="1d964-163">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="1d964-164">In der Regel positionieren Sie diesen Cursor in der Welt, in der der Head-Blick Strahl zuerst ein Objekt schneidet, das ein Hologramm oder eine reale Oberfläche sein kann.</span><span class="sxs-lookup"><span data-stu-id="1d964-164">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="1d964-165">Für den Augenblick empfiehlt es sich im allgemeinen *nicht* , einen Cursor anzuzeigen, da dies für den Benutzer schnell ablenkend und lästig werden kann.</span><span class="sxs-lookup"><span data-stu-id="1d964-165">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="1d964-166">Markieren Sie stattdessen visuelle Ziele, oder verwenden Sie einen schwachen Augen Cursor, um sicherzustellen, womit der Benutzer interagieren soll.</span><span class="sxs-lookup"><span data-stu-id="1d964-166">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="1d964-167">Weitere Informationen finden Sie in unserem [Entwurfs Leit Faden für die Augen basierte Eingabe](eye-tracking.md) auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="1d964-167">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="1d964-168">![Ein Beispiel für einen visuellen Cursor zum Anzeigen des Blicks](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d964-168">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="1d964-169">*Bild: ein visueller Beispiel Cursor zum Anzeigen des Blicks*</span><span class="sxs-lookup"><span data-stu-id="1d964-169">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="1d964-170">Commit</span><span class="sxs-lookup"><span data-stu-id="1d964-170">Commit</span></span>
<span data-ttu-id="1d964-171">Nachdem Sie über verschiedene Möglichkeiten zum _betrachten_ eines Ziels gesprochen haben, sprechen wir etwas über den _Commit_ -Teil im _Blick und Commit_.</span><span class="sxs-lookup"><span data-stu-id="1d964-171">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="1d964-172">Nachdem ein Objekt oder ein UI-Element als Ziel verwendet wurde, kann der Benutzer mit einer sekundären Eingabe interagieren oder darauf klicken.</span><span class="sxs-lookup"><span data-stu-id="1d964-172">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="1d964-173">Dies wird als Bestätigungsschritt (Commit) des Eingabemodells bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="1d964-173">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="1d964-174">Die folgenden Methoden zum Ausführen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="1d964-174">The following commit methods are supported:</span></span>
- <span data-ttu-id="1d964-175">Tippen Sie auf die Handbewegung, und bringen Sie den Finger und den Ziehpunkt des Indexes ein.</span><span class="sxs-lookup"><span data-stu-id="1d964-175">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="1d964-176">Sagen _Sie "Select"_ oder einen der Ziel Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="1d964-176">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="1d964-177">Eine einzelne Schaltfläche auf einem [hololens-Clicker](/hololens/hololens1-clicker) drücken</span><span class="sxs-lookup"><span data-stu-id="1d964-177">Press a single button on a [HoloLens Clicker](/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="1d964-178">Schaltfläche "A" auf einem Xbox Gamepad drücken</span><span class="sxs-lookup"><span data-stu-id="1d964-178">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="1d964-179">Schaltfläche "A" auf einem adaptiven Xbox-Controller drücken</span><span class="sxs-lookup"><span data-stu-id="1d964-179">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="1d964-180">Bewegung für Blick und Luft tippen</span><span class="sxs-lookup"><span data-stu-id="1d964-180">Gaze and air tap gesture</span></span>
<span data-ttu-id="1d964-181">„In die Luft tippen“ ist eine Tippbewegung mit aufrecht gehaltener Hand</span><span class="sxs-lookup"><span data-stu-id="1d964-181">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="1d964-182">Um eine Luft Abzweigung zu verwenden, heben Sie den Finger für den Index an der Position auf, und drücken Sie dann mit dem Ziehpunkt, und erhöhen Sie den Finger für den Index auf Release.</span><span class="sxs-lookup"><span data-stu-id="1d964-182">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="1d964-183">Bei hololens (1. Generation) ist Air Tap die häufigste sekundäre Eingabe.</span><span class="sxs-lookup"><span data-stu-id="1d964-183">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="1d964-184">![Finger an der Ready-Position](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d964-184">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="1d964-185">**Finger an der Ready-Position**</span><span class="sxs-lookup"><span data-stu-id="1d964-185">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="1d964-186">![Drücken Sie die nach-unten-Taste, um auf](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d964-186">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="1d964-187">**Drücken Sie die nach-unten-Taste, um auf**</span><span class="sxs-lookup"><span data-stu-id="1d964-187">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="1d964-188">Air Tap ist auch auf hololens 2 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1d964-188">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="1d964-189">Es wurde von der ursprünglichen Version gelockert.</span><span class="sxs-lookup"><span data-stu-id="1d964-189">It has been relaxed from the original version.</span></span> <span data-ttu-id="1d964-190">Fast alle Arten von Pinches werden jetzt unterstützt, solange die Hand gleich ist und weiterhin ist.</span><span class="sxs-lookup"><span data-stu-id="1d964-190">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="1d964-191">Dies erleichtert es Benutzern, die Geste zu erlernen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="1d964-191">This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id="1d964-192">Diese neue Luftlinie ersetzt die alte durch dieselbe API, sodass vorhandene Anwendungen das neue Verhalten automatisch nach der Neukompilierung für hololens 2 aufweisen.</span><span class="sxs-lookup"><span data-stu-id="1d964-192">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="1d964-193">"Stimme" und "Select"-Befehl</span><span class="sxs-lookup"><span data-stu-id="1d964-193">Gaze and "Select" voice command</span></span>
<span data-ttu-id="1d964-194">Voice-Befehle sind eine der primären Interaktions Methoden in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="1d964-194">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="1d964-195">Es bietet einen leistungsstarken Mechanismus zur Steuerung des Systems.</span><span class="sxs-lookup"><span data-stu-id="1d964-195">It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="1d964-196">Es gibt verschiedene Typen von sprach Interaktions Modellen:</span><span class="sxs-lookup"><span data-stu-id="1d964-196">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="1d964-197">Der generische SELECT-Befehl, der eine Klick-oder einen Commit als sekundäre Eingabe verwendet.</span><span class="sxs-lookup"><span data-stu-id="1d964-197">The generic "Select" command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="1d964-198">Objekt Befehle (z. b. "Close" oder "make it Bigger") führen eine Aktion als sekundäre Eingabe aus und führen Sie aus.</span><span class="sxs-lookup"><span data-stu-id="1d964-198">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="1d964-199">Für globale Befehle (z. b. "Gehe zu Start") ist kein Ziel erforderlich.</span><span class="sxs-lookup"><span data-stu-id="1d964-199">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="1d964-200">Benutzeroberflächen für die Konversation oder Entitäten wie Cortana verfügen über eine künstliche Ki-Sprache.</span><span class="sxs-lookup"><span data-stu-id="1d964-200">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="1d964-201">Benutzerdefinierte Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="1d964-201">Custom voice commands</span></span>

<span data-ttu-id="1d964-202">Weitere Informationen zu Details und eine umfassende Liste der verfügbaren Sprachbefehle und deren Verwendung finden Sie in unserem Leitfaden für die [sprach Befehlsführung](../out-of-scope/voice-design.md) .</span><span class="sxs-lookup"><span data-stu-id="1d964-202">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="1d964-203">Blick und hololens Clicker</span><span class="sxs-lookup"><span data-stu-id="1d964-203">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1d964-204">Der hololens-Clicker ist das erste Peripheriegerät, das speziell für hololens erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="1d964-204">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="1d964-205">Es ist in der Entwicklungs Edition von hololens (1st Gen) enthalten.</span><span class="sxs-lookup"><span data-stu-id="1d964-205">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="1d964-206">Der hololens-Clicker ermöglicht dem Benutzer das Klicken mit minimaler Handbewegung und das Commit als sekundäre Eingabe.</span><span class="sxs-lookup"><span data-stu-id="1d964-206">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="1d964-207">Der hololens-Clicker stellt mithilfe von Bluetooth Low Energy (btle) eine Verbindung mit hololens (1 St Gen) oder hololens 2 her.</span><span class="sxs-lookup"><span data-stu-id="1d964-207">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="1d964-208">Weitere Informationen und Anweisungen zum Koppeln des Geräts</span><span class="sxs-lookup"><span data-stu-id="1d964-208">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="1d964-209">*Image: hololens Clicker*</span><span class="sxs-lookup"><span data-stu-id="1d964-209">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens-Klick-Gerät](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="1d964-211">Blick und Xbox Wireless Controller</span><span class="sxs-lookup"><span data-stu-id="1d964-211">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1d964-212">Der Xbox Wireless-Controller führt mit der Schaltfläche "a" eine Klick-und eine sekundäre Eingabe durch.</span><span class="sxs-lookup"><span data-stu-id="1d964-212">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="1d964-213">Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen.</span><span class="sxs-lookup"><span data-stu-id="1d964-213">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="1d964-214">Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Accessories-Anwendung, um Ihren Xbox Wireless-Controller zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="1d964-214">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="1d964-215">Koppeln eines Xbox-Controllers mit Ihrem PC</span><span class="sxs-lookup"><span data-stu-id="1d964-215">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="1d964-216">*Bild: Xbox Wireless Controller*</span><span class="sxs-lookup"><span data-stu-id="1d964-216">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Xbox Wireless Controller](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="1d964-218">Blick und adaptiver Xbox-Controller</span><span class="sxs-lookup"><span data-stu-id="1d964-218">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="1d964-219">Der Xbox Adaptive Controller ist in erster Linie für die Bedürfnisse von Spielern mit eingeschränkter Mobilität konzipiert und stellt einen einheitlichen Hub für Geräte dar, mit denen gemischte Realität leichter zugänglich gemacht werden kann.</span><span class="sxs-lookup"><span data-stu-id="1d964-219">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="1d964-220">Der Xbox Adaptive Controller führt mit der Schaltfläche "a" eine Klick-und eine sekundäre Eingabe durch.</span><span class="sxs-lookup"><span data-stu-id="1d964-220">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="1d964-221">Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen.</span><span class="sxs-lookup"><span data-stu-id="1d964-221">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="1d964-222">Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Accessories-Anwendung, um den adaptiven Xbox-Controller zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="1d964-222">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="1d964-223">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d964-223">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="1d964-224">*Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="1d964-224">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="1d964-225">Verbinden Sie externe Geräte, wie z. b. Switches, Schaltflächen, bereit Stellungen und Joystick, um eine benutzerdefinierte Controller-benutzerdefinierte Controller Darstellung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1d964-225">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="1d964-226">Schaltflächen-, fingerstick-und triggereingaben werden mit Hilfsgeräten gesteuert, die über 3,5-mm-und USB-Ports verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="1d964-226">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="1d964-227">![Xbox Adaptive Controller-Anschlüsse](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d964-227">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="1d964-228">*Xbox Adaptive Controller-Anschlüsse*</span><span class="sxs-lookup"><span data-stu-id="1d964-228">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="1d964-229">Anweisungen zum Koppeln des Geräts</span><span class="sxs-lookup"><span data-stu-id="1d964-229">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="1d964-230"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Weitere Informationen, die auf der Xbox-Website verfügbar sind</a></span><span class="sxs-lookup"><span data-stu-id="1d964-230"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="1d964-231">Zusammengesetzte Gesten</span><span class="sxs-lookup"><span data-stu-id="1d964-231">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="1d964-232">In die Luft tippen</span><span class="sxs-lookup"><span data-stu-id="1d964-232">Air tap</span></span>
<span data-ttu-id="1d964-233">Die Luft tippen Bewegung (und die anderen Gesten unten) reagiert nur auf eine bestimmte Tap.</span><span class="sxs-lookup"><span data-stu-id="1d964-233">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="1d964-234">Um andere Abzweigungen zu erkennen, wie z. b. Menu oder grasp, muss Ihre Anwendung direkt die Interaktionen auf niedrigerer Ebene verwenden, die im obigen Abschnitt mit zwei wichtigen Komponenten Gesten beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="1d964-234">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="1d964-235"> Tippen und halten Sie </span><span class="sxs-lookup"><span data-stu-id="1d964-235">Tap and hold</span></span>
<span data-ttu-id="1d964-236">„Halten“ bedeutet einfach, die Position mit dem Finger nach unten beim „In die Luft tippen“ beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="1d964-236">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="1d964-237">Die Kombination von Air Tap und Hold ermöglicht verschiedene komplexere "klicken und ziehen"-Interaktionen, wenn Sie mit Arm-Bewegung kombiniert werden, wie z. b. das Auswählen eines Objekts, anstatt es zu aktivieren oder um sekundäre Interaktionen wie das zeigen eines Kontextmenüs zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="1d964-237">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="1d964-238">Beim Entwerfen dieser Geste sollte jedoch Vorsicht geboten werden, da Benutzer anfällig sein können, um Ihre handhaltungen während der erweiterten Bewegung zu lockern.</span><span class="sxs-lookup"><span data-stu-id="1d964-238">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="1d964-239">Manipulation</span><span class="sxs-lookup"><span data-stu-id="1d964-239">Manipulation</span></span>
<span data-ttu-id="1d964-240">Manipulations Gesten können zum Verschieben, Ändern der Größe oder Drehen eines holograms verwendet werden, wenn das – Hologramm 1:1 auf die Handbewegungen des Benutzers reagieren soll.</span><span class="sxs-lookup"><span data-stu-id="1d964-240">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="1d964-241">Eine Verwendungsmöglichkeit für solche 1:1-Bewegungen ist es, den Benutzer in der Umgebung zeichnen oder malen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="1d964-241">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="1d964-242">Die anfängliche Zielbestimmung für eine Manipulationsgeste sollte durch Anvisieren oder Zeigen erfolgen.</span><span class="sxs-lookup"><span data-stu-id="1d964-242">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="1d964-243">Wenn Tap und Hold gestartet werden, wird jede Objekt Bearbeitung von Handbewegungen behandelt, wodurch der Benutzer beim Bearbeiten nicht mehr untersucht wird.</span><span class="sxs-lookup"><span data-stu-id="1d964-243">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="1d964-244">Navigation</span><span class="sxs-lookup"><span data-stu-id="1d964-244">Navigation</span></span>
<span data-ttu-id="1d964-245">Navigationsgesten funktionieren wie ein virtueller Joystick und können zur Navigation in Widgets der Benutzeroberfläche, z. B. Radialmenüs, verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1d964-245">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="1d964-246">Sie tippen und halten, um die Geste zu starten, und bewegen dann Ihre Hand in einem normalisierten 3D-Würfel, der um die erste Betätigung herum angeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="1d964-246">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="1d964-247">Sie können Ihre Hand entlang der X-, Y-oder Z-Achse von einem Wert von-1 in 1 bewegen, wobei 0 der Ausgangspunkt ist.</span><span class="sxs-lookup"><span data-stu-id="1d964-247">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="1d964-248">Mithilfe der Navigation können geschwindigkeitsbasierte kontinuierliche Gesten zum Scrollen oder Zoomen erstellt werden, ähnlich dem Scrollen bei einer 2D-Benutzeroberfläche durch Klicken mit der mittleren Maustaste und anschließendes Bewegen der Maus nach oben und unten.</span><span class="sxs-lookup"><span data-stu-id="1d964-248">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="1d964-249">Navigation mit Rails bezieht sich auf die Fähigkeit, Bewegungen auf einer bestimmten Achse zu erkennen, bis ein bestimmter Schwellenwert auf dieser Achse erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="1d964-249">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="1d964-250">Dies ist nur nützlich, wenn die Bewegung in mehr als einer Achse durch den Entwickler in einer Anwendung aktiviert ist, z. b. Wenn eine Anwendung so konfiguriert ist, dass Navigations Gesten über die x-, Y-Achse, aber auch die x-Achse mit Rails erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="1d964-250">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="1d964-251">In diesem Fall erkennt das System Handbewegungen über die x-Achse, solange Sie auf der x-Achse innerhalb eines imaginären Rails (Handbuchs) bleiben, wenn die Handbewegung auch auf der Y-Achse auftritt.</span><span class="sxs-lookup"><span data-stu-id="1d964-251">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="1d964-252">Innerhalb von 2D-Apps können Benutzer mit vertikalen Navigationsgesten innerhalb der App scrollen, zoomen oder ziehen.</span><span class="sxs-lookup"><span data-stu-id="1d964-252">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="1d964-253">Dadurch werden virtuelle Fingerberührungen in der App eingeführt, um Gesten für die Toucheingabe desselben Typs zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="1d964-253">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="1d964-254">Benutzer können auswählen, welche dieser Aktionen durchgeführt werden, indem Sie zwischen den Tools auf der Leiste oberhalb der Anwendung wechseln, indem Sie entweder die Schaltfläche auswählen oder die Option "<Scrollmodus/Drag & Zoom> Tools" verwenden.</span><span class="sxs-lookup"><span data-stu-id="1d964-254">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="1d964-255">Weitere Informationen zu zusammengesetzten Gesten</span><span class="sxs-lookup"><span data-stu-id="1d964-255">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="1d964-256">Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="1d964-256">Gesture recognizers</span></span>

<span data-ttu-id="1d964-257">Ein Vorteil bei der Verwendung der Gestenerkennung besteht darin, dass Sie eine Gestenerkennung nur für die Gesten konfigurieren können, die das derzeit zielgerichtete – Hologramm annehmen kann.</span><span class="sxs-lookup"><span data-stu-id="1d964-257">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="1d964-258">Die Plattform ist nur bei Bedarf eindeutig, um die unterstützten Gesten unterscheiden zu können.</span><span class="sxs-lookup"><span data-stu-id="1d964-258">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="1d964-259">Auf diese Weise kann ein – Hologramm, das nur Air Tap unterstützt, jede Zeitspanne zwischen dem Drücken und dem Release akzeptieren, während ein – Hologramm, das sowohl Tap als auch Hold unterstützt, die Abzweigung nach dem Schwellenwert für die Aufbewahrungszeit auf einen Halt herauf Stufen kann.</span><span class="sxs-lookup"><span data-stu-id="1d964-259">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="1d964-260">Handerkennung</span><span class="sxs-lookup"><span data-stu-id="1d964-260">Hand recognition</span></span>
<span data-ttu-id="1d964-261">HoloLens erkennt Handgesten, indem die Position einer oder beider Hände, die für das Gerät sichtbar sind, verfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="1d964-261">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="1d964-262">HoloLens erkennt Hände, wenn sie sich entweder im Bereitschaftszustand (Handrücken mit nach oben gerichtetem Zeigefinger zu Ihnen gewandt) oder im gedrückten Zustand (Handrücken mit nach unten gerichtetem Zeigefinger zu Ihnen gewandt) befinden.</span><span class="sxs-lookup"><span data-stu-id="1d964-262">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="1d964-263">Wenn sich die Hände in anderen Posen befinden, werden Sie von hololens ignoriert.</span><span class="sxs-lookup"><span data-stu-id="1d964-263">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="1d964-264">Für jede Hand, die hololens erkennt, können Sie ohne Ausrichtung und gedrücktem Zustand auf seine Position zugreifen.</span><span class="sxs-lookup"><span data-stu-id="1d964-264">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="1d964-265">Wenn sich die Hand dem Rand des Gestenrahmens nähert, erhalten Sie auch einen Richtungsvektor, den Sie dem Benutzer zeigen können, damit er weiß, wie er seine Hand bewegen muss, um sie dorthin zurückzubringen, wo sie von HoloLens erkannt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1d964-265">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="1d964-266">Gestenrahmen</span><span class="sxs-lookup"><span data-stu-id="1d964-266">Gesture frame</span></span>
<span data-ttu-id="1d964-267">Für Gesten in hololens muss sich die Hand innerhalb eines Gesten Rahmens befinden, der sich in einem Bereich befindet, der von der Bewegung zur Gesten Messung von der Nase bis zur Taille und von der Schulter aus angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1d964-267">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="1d964-268">Benutzer müssen in diesem Bereich geschult werden, um den Erfolg der Aktion und ihren eigenen Komfort zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="1d964-268">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="1d964-269">Viele Benutzer werden anfänglich davon ausgehen, dass sich der Gesten Rahmen in der Ansicht über hololens befinden muss</span><span class="sxs-lookup"><span data-stu-id="1d964-269">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="1d964-270">Wenn Sie das hololens-Clicker verwenden, ist es nicht erforderlich, dass sich die Hände innerhalb des Gesten Rahmens befinden.</span><span class="sxs-lookup"><span data-stu-id="1d964-270">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="1d964-271">Insbesondere bei fortlaufenden Gesten besteht das Risiko, dass Benutzer ihre Hände außerhalb des Gesten Rahmens bewegen, während Sie sich in der Mitte der Bewegung befinden, wenn Sie z. b. ein Holographic-Objekt verschieben und das gewünschte Ergebnis verlieren.</span><span class="sxs-lookup"><span data-stu-id="1d964-271">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="1d964-272">Sie sollten die folgenden drei Aspekte berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="1d964-272">There are three things that you should consider:</span></span>

- <span data-ttu-id="1d964-273">Benutzer Bildung für das vorhanden sein und die ungefähren Grenzen des Gesten Rahmens.</span><span class="sxs-lookup"><span data-stu-id="1d964-273">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="1d964-274">Dies wird während der hololens-Einrichtung vermittelt.</span><span class="sxs-lookup"><span data-stu-id="1d964-274">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="1d964-275">Benachrichtigen von Benutzern, wenn ihre Gesten die Gesten Rahmen Begrenzungen innerhalb einer Anwendung nähern oder unterbrechen, bis zu dem Ausmaß, in dem eine verlorene Bewegung zu unerwünschten Ergebnissen führt.</span><span class="sxs-lookup"><span data-stu-id="1d964-275">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="1d964-276">Research hat die Hauptqualitäten eines solchen Benachrichtigungs Systems aufgezeigt.</span><span class="sxs-lookup"><span data-stu-id="1d964-276">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="1d964-277">Die hololens-Shell stellt ein gutes Beispiel für diese Art von Benachrichtigung dar: Visual, auf dem zentralen Cursor, der die Richtung angibt, in der der Begrenzungs Übergang stattfindet.</span><span class="sxs-lookup"><span data-stu-id="1d964-277">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="1d964-278">Die Folgen des Überschreitens der Begrenzungen des Gestenrahmens sollten minimiert werden.</span><span class="sxs-lookup"><span data-stu-id="1d964-278">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="1d964-279">Im Allgemeinen bedeutet dies, dass das Ergebnis einer Geste an der Grenze angehalten und nicht umgekehrt werden soll.</span><span class="sxs-lookup"><span data-stu-id="1d964-279">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="1d964-280">Wenn ein Benutzer beispielsweise ein Holographic-Objekt über einen Raum verschiebt, sollte die Bewegung angehalten werden, wenn der Gesten Rahmen verletzt wird und nicht an den Ausgangspunkt zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1d964-280">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="1d964-281">Der Benutzer kann einige Frustrationen erkennen, aber die Grenzen vielleicht besser verstehen und nicht jedes Mal die vollständigen beabsichtigten Aktionen neu starten.</span><span class="sxs-lookup"><span data-stu-id="1d964-281">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="1d964-282">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1d964-282">See also</span></span>
* [<span data-ttu-id="1d964-283">Augenbasierte Interaktion</span><span class="sxs-lookup"><span data-stu-id="1d964-283">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="1d964-284">Blickverfolgung auf HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1d964-284">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="1d964-285">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="1d964-285">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="1d964-286">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="1d964-286">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1d964-287">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="1d964-287">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="1d964-288">Hände – Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="1d964-288">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="1d964-289">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="1d964-289">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="1d964-290">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="1d964-290">Voice input</span></span>](voice-input.md)