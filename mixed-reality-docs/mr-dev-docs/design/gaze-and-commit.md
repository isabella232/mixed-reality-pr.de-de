---
title: Anvisieren und Bestätigen
description: Erfahren Sie mehr über das Eingabemodell "Anvieren und Committen", darunter zwei Arten von Anvieren (Anvieren mit dem Kopf und Anvieren mit den Augen) und verschiedene Arten von Commits.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality, Anvisieren, Anvisieren, Interaktion, Design, Blickverfolgung, Kopfverfolgung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: db394ab4aded7136550e8e88eb3d66e06f3eeb92
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196565"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="07492-104">Anvisieren und Bestätigen</span><span class="sxs-lookup"><span data-stu-id="07492-104">Gaze and commit</span></span>

<span data-ttu-id="07492-105">_Anvieren und Committen_ ist ein grundlegendes Eingabemodell, das eng mit der Art und Weise zusammenhängt, wie wir mit der Maus mit unseren Computern interagieren: _Zeigen Sie & klicken Sie auf_.</span><span class="sxs-lookup"><span data-stu-id="07492-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="07492-106">Auf dieser Seite werden zwei Arten von Eingaben zum Anvieren (Anvieren mit dem Kopf und mit den Augen) und verschiedene Arten von Commitaktionen vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="07492-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="07492-107">_Anvieren und Committen_ wird als weit entferntes Eingabemodell mit indirekter Bearbeitung betrachtet.</span><span class="sxs-lookup"><span data-stu-id="07492-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="07492-108">Es wird am besten für die Interaktion mit holografischen Inhalten verwendet, die nicht erreichbar sind.</span><span class="sxs-lookup"><span data-stu-id="07492-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="07492-109">Mixed Reality-Headsets können die Position und Ausrichtung des Kopfes des Benutzers verwenden, um seinen Vektor für die Kopfrichtung zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="07492-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="07492-110">Stellen Sie sich das Anvieren als einen Geleer vor, der direkt zwischen den Augen des Benutzers direkt nach vorn zeigen kann.</span><span class="sxs-lookup"><span data-stu-id="07492-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="07492-111">Dies ist eine ziemlich grobe Annäherung hinsichtlich der Position, die der Benutzer betrachtet.</span><span class="sxs-lookup"><span data-stu-id="07492-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="07492-112">Ihre Anwendung kann diesen Strahl mit virtuellen oder realen Objekten überschneiden und einen Cursor an dieser Position zeichnen, um den Benutzer darüber zu informieren, worauf er abzielt.</span><span class="sxs-lookup"><span data-stu-id="07492-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="07492-113">Neben dem Anverfolgen mit dem Kopf enthalten einige Mixed Reality-Headsets, z. B. HoloLens 2, Eyetrackingsysteme, die einen Anvektor für anverfolgte Augen erzeugen.</span><span class="sxs-lookup"><span data-stu-id="07492-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="07492-114">Dies ermöglicht eine präzisere Messung der Position, die der Benutzer betrachtet.</span><span class="sxs-lookup"><span data-stu-id="07492-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="07492-115">In beiden Fällen stellt das Anvisieren ein wichtiges Signal für die Absicht des Benutzers dar.</span><span class="sxs-lookup"><span data-stu-id="07492-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="07492-116">Je besser das System die beabsichtigten Aktionen des Benutzers interpretieren und vorhersagen kann, desto mehr Benutzerzufriedenheit und Leistung werden verbessert.</span><span class="sxs-lookup"><span data-stu-id="07492-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="07492-117">Im Folgenden finden Sie einige Beispiele dafür, wie Sie als Mixed Reality-Entwickler vom Anvieren mit dem Kopf oder den Augen profitieren können:</span><span class="sxs-lookup"><span data-stu-id="07492-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="07492-118">Ihre App kann das Anvisieren mit den Hologrammen in Ihrer Szene überschneiden, um zu bestimmen, wo die Aufmerksamkeit des Benutzers liegt (genauer mit dem Anvisieren mit den Augen).</span><span class="sxs-lookup"><span data-stu-id="07492-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="07492-119">Ihre App kann Gesten und Controllerdrücke basierend auf dem Anvisieren des Benutzers kanalisieren, wodurch der Benutzer seine Hologramme nahtlos auswählen, aktivieren, greifen, scrollen oder anderweitig interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="07492-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="07492-120">Ihre App kann es dem Benutzer gestatten, Hologramme auf realen Oberflächen zu platzieren, indem er seinen Blickstrahl mit dem Gitternetz der räumlichen Abbildung überschneidet.</span><span class="sxs-lookup"><span data-stu-id="07492-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="07492-121">Ihre App kann wissen, wenn der Benutzer nicht in richtung eines wichtigen Objekts sucht. Dies kann dazu führen, dass Ihre App visuelle und audioorientierte Hinweise zu diesem Objekt gibt.</span><span class="sxs-lookup"><span data-stu-id="07492-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="07492-122">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="07492-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="07492-123"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="07492-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="07492-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="07492-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="07492-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="07492-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="07492-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="07492-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="07492-127">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="07492-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="07492-128">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="07492-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="07492-129">✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</span><span class="sxs-lookup"><span data-stu-id="07492-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="07492-130">➕ Alternative Option</span><span class="sxs-lookup"><span data-stu-id="07492-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="07492-131">Anvisieren mit den Augen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="07492-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="07492-132">❌ Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="07492-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="07492-133">✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</span><span class="sxs-lookup"><span data-stu-id="07492-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="07492-134">❌ Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="07492-134">❌ Not available</span></span></td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="07492-135">Demo zu Designkonzepten für Kopf- und Blickverfolgung</span><span class="sxs-lookup"><span data-stu-id="07492-135">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="07492-136">Wenn Sie Designkonzepte für Kopf- und Blickverfolgung in Aktion sehen möchten, sehen Sie sich die Videodemo **Designing Holograms - Head Tracking and Eye Tracking** (Entwerfen von Hologrammen – Kopfverfolgung und Eyetracking) weiter unten an.</span><span class="sxs-lookup"><span data-stu-id="07492-136">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="07492-137">Wenn Sie fertig sind, fahren Sie fort, um ausführlichere Informationen zu bestimmten Themen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="07492-137">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="07492-138">*Dieses Video wurde aus der App "Entwerfen von Hologrammen" HoloLens 2 aufgenommen. Laden Sie hier herunter, und profitieren Sie [von der vollständigen Erfahrung.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="07492-138">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="gaze"></a><span data-ttu-id="07492-139">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="07492-139">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="07492-140">Mit den Augen oder mit dem Kopf?</span><span class="sxs-lookup"><span data-stu-id="07492-140">Eye- or head-gaze?</span></span>
<span data-ttu-id="07492-141">Bei der Frage, ob Sie das Eingabemodell "Anvieren mit den Augen und Commit" oder "Anvieren mit dem Kopf und Commit" verwenden sollten, gibt es mehrere Überlegungen.</span><span class="sxs-lookup"><span data-stu-id="07492-141">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="07492-142">Wenn Sie für ein immersives Headset oder für HoloLens (1. Generation) entwickeln, ist die Wahl einfach: Anvitieren mit dem Kopf und Commit.</span><span class="sxs-lookup"><span data-stu-id="07492-142">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="07492-143">Wenn Sie für die entwicklung HoloLens 2, wird die Auswahl etwas schwieriger.</span><span class="sxs-lookup"><span data-stu-id="07492-143">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="07492-144">Es ist wichtig, die Vorteile und Herausforderungen zu verstehen, die mit jedem dieser Beiden verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="07492-144">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="07492-145">In der folgenden Tabelle haben wir einige allgemeine Pros und Kontras kompiliert, um das Ziel mit dem Kopf- und dem Anvieren mit den Augen gegenüber zu vergleichen.</span><span class="sxs-lookup"><span data-stu-id="07492-145">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="07492-146">Dies ist noch lange nicht abgeschlossen, und wir empfehlen Ihnen, hier mehr über das Anvieren mit den Augen in Mixed Reality zu erfahren:</span><span class="sxs-lookup"><span data-stu-id="07492-146">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="07492-147">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span><span class="sxs-lookup"><span data-stu-id="07492-147">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="07492-148">[Interaktion mit dem Anvistik-Blick:](eye-gaze-interaction.md)Entwurfsüberlegungen und -empfehlungen bei der Planung der Verwendung von EyeTracking als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="07492-148">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="07492-149"><strong>Zielgruppenadressierung mit den Augen</strong></span><span class="sxs-lookup"><span data-stu-id="07492-149"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="07492-150"><strong>Anvisieren mit dem Kopf</strong></span><span class="sxs-lookup"><span data-stu-id="07492-150"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="07492-151">schnell!</span><span class="sxs-lookup"><span data-stu-id="07492-151">Fast!</span></span></td>
        <td><span data-ttu-id="07492-152">Langsamer</span><span class="sxs-lookup"><span data-stu-id="07492-152">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="07492-153">Geringer Aufwand (abschwächen aller erforderlichen Körperbewegungen)</span><span class="sxs-lookup"><span data-stu-id="07492-153">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="07492-154">Kann ermüdend sein: Mögliche Störungen (z. B. Hängebelastung)</span><span class="sxs-lookup"><span data-stu-id="07492-154">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="07492-155">Erfordert keinen Cursor, aber es wird ein dezentes Feedback empfohlen.</span><span class="sxs-lookup"><span data-stu-id="07492-155">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="07492-156">Erfordert das Anzeigen eines Cursors</span><span class="sxs-lookup"><span data-stu-id="07492-156">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="07492-157">Keine reibungslosen Augenbewegungen– z. B. nicht gut zum Zeichnen</span><span class="sxs-lookup"><span data-stu-id="07492-157">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="07492-158">Kontrollierter und expliziter</span><span class="sxs-lookup"><span data-stu-id="07492-158">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="07492-159">Schwierig für kleine Ziele (z. B. kleine Schaltflächen oder Weblinks)</span><span class="sxs-lookup"><span data-stu-id="07492-159">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="07492-160">Zuverlässige!</span><span class="sxs-lookup"><span data-stu-id="07492-160">Reliable!</span></span> <span data-ttu-id="07492-161">Toller Fallback!</span><span class="sxs-lookup"><span data-stu-id="07492-161">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="07492-162">...</span><span class="sxs-lookup"><span data-stu-id="07492-162">...</span></span></td>
        <td><span data-ttu-id="07492-163">...</span><span class="sxs-lookup"><span data-stu-id="07492-163">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="07492-164">Unabhängig davon, ob Sie das Anvieren mit dem Kopf oder das Anvieren mit den Augen für Ihr Eingabemodell zum Anvieren und Committen verwenden, gibt es jeweils unterschiedliche Entwurfseinschränkungen.</span><span class="sxs-lookup"><span data-stu-id="07492-164">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="07492-165">Diese werden separat in den Artikeln [Anvieren mit](gaze-and-commit-eyes.md) den Augen und Committen und [Anvieren mit](gaze-and-commit-head.md) dem Kopf und Commit behandelt.</span><span class="sxs-lookup"><span data-stu-id="07492-165">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="07492-166">Cursor</span><span class="sxs-lookup"><span data-stu-id="07492-166">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="07492-167">Für das Anvieren mit dem Kopf sollten die meisten Apps einen [Cursor](cursors.md) oder einen anderen akustischen/visuellen Hinweis verwenden, um dem Benutzer Vertrauen in die Interaktion zu geben.</span><span class="sxs-lookup"><span data-stu-id="07492-167">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="07492-168">In der Regel positionieren Sie diesen Cursor in der Welt, wo der Strahl des Anvierens des Kopfes zuerst ein Objekt überschneidet, bei dem es sich um ein Hologramm oder eine reale Oberfläche handeln kann.</span><span class="sxs-lookup"><span data-stu-id="07492-168">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="07492-169">Für das Anvieren mit den Augen empfiehlt es sich im Allgemeinen, *keinen* Cursor anzuzeigen, da dies für den Benutzer schnell ablenkend und nervig werden kann.</span><span class="sxs-lookup"><span data-stu-id="07492-169">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="07492-170">Markieren Sie stattdessen visuelle Ziele, oder verwenden Sie einen schwachen Blickcursor, um die Zuverlässigkeit der Interaktion des Benutzers zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="07492-170">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="07492-171">Weitere Informationen finden Sie in unserer [Entwurfsleitfäden für blickbasierte Eingaben](eye-tracking.md) zu HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="07492-171">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="07492-172">![Ein Beispiel für einen visuellen Cursor zum Anzeigen des Anv](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="07492-172">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="07492-173">*Bild: Beispiel für einen visuellen Cursor zum Anzeigen des Anv*</span><span class="sxs-lookup"><span data-stu-id="07492-173">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="07492-174">Commit</span><span class="sxs-lookup"><span data-stu-id="07492-174">Commit</span></span>
<span data-ttu-id="07492-175">Nachdem wir über verschiedene Möglichkeiten zum _Anvischen_ eines Ziels gesprochen haben, sprechen wir ein wenig mehr über den _Committeil_ beim _Anvischen und Committen._</span><span class="sxs-lookup"><span data-stu-id="07492-175">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="07492-176">Nachdem ein Objekt oder ein Benutzeroberflächenelement als Ziel verwendet wurde, kann der Benutzer mithilfe einer sekundären Eingabe interagieren oder darauf klicken.</span><span class="sxs-lookup"><span data-stu-id="07492-176">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="07492-177">Dies wird als Bestätigungsschritt (Commit) des Eingabemodells bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="07492-177">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="07492-178">Die folgenden Methoden zum Ausführen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="07492-178">The following commit methods are supported:</span></span>
- <span data-ttu-id="07492-179">Handgeste zum Tippen in die Luft (d. h., die Hand vor Ihnen heben und Zeigefinger und Daumen zusammenbringen)</span><span class="sxs-lookup"><span data-stu-id="07492-179">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="07492-180">Sagen _Sie "select"_ oder einen der Sprachbefehle, die als Ziel verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="07492-180">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="07492-181">Drücken einer einzelnen Schaltfläche auf einem [HoloLens-Clicker](/hololens/hololens1-clicker)</span><span class="sxs-lookup"><span data-stu-id="07492-181">Press a single button on a [HoloLens Clicker](/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="07492-182">Klicken Sie auf einem Xbox-Gamepad auf die Schaltfläche "A".</span><span class="sxs-lookup"><span data-stu-id="07492-182">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="07492-183">Klicken Sie auf die Schaltfläche "A" auf einem adaptiven Xbox-Controller.</span><span class="sxs-lookup"><span data-stu-id="07492-183">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="07492-184">Geste "Anv" und "Tippen in die Luft"</span><span class="sxs-lookup"><span data-stu-id="07492-184">Gaze and air tap gesture</span></span>
<span data-ttu-id="07492-185">„In die Luft tippen“ ist eine Tippbewegung mit aufrecht gehaltener Hand</span><span class="sxs-lookup"><span data-stu-id="07492-185">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="07492-186">Um einen Tippen in die Luft zu verwenden, heben Sie den Zeigefinger auf die bereite Position, und heften Sie dann mit dem Daumen zusammen, und heben Sie den Zeigefinger wieder hoch, um es frei zu machen.</span><span class="sxs-lookup"><span data-stu-id="07492-186">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="07492-187">Bei HoloLens (1. Generation) ist Tippen in die Luft die häufigste sekundäre Eingabe.</span><span class="sxs-lookup"><span data-stu-id="07492-187">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="07492-188">![Finger in der bereiten Position](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="07492-188">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="07492-189">**Finger in der bereiten Position**</span><span class="sxs-lookup"><span data-stu-id="07492-189">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="07492-190">![Drücken Sie den Finger nach unten, um zu tippen oder zu klicken.](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="07492-190">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="07492-191&quot;>**Drücken Sie den Finger nach unten, um zu tippen oder zu klicken.**</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-191&quot;>**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id=&quot;07492-192&quot;>Tippen in die Luft ist auch auf HoloLens 2.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-192&quot;>Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id=&quot;07492-193&quot;>Sie wurde von der ursprünglichen Version gelockert.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-193&quot;>It has been relaxed from the original version.</span></span> <span data-ttu-id=&quot;07492-194&quot;>Fast alle Arten von Pinches werden jetzt unterstützt, solange die Hand aufrecht ist und still hält.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-194&quot;>Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id=&quot;07492-195&quot;>Dadurch können Benutzer die Geste viel einfacher erlernen und verwenden.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-195&quot;>This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id=&quot;07492-196&quot;>Dieses neue Tippen in die Luft ersetzt das alte über dieselbe API, sodass vorhandene Anwendungen das neue Verhalten automatisch nach der Neukompilierung für HoloLens 2.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-196&quot;>This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name=&quot;gaze-and-select-voice-command&quot;></a><span data-ttu-id=&quot;07492-197&quot;>Sprachbefehl &quot;Anv&quot; und &quot;Auswählen&quot;</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-197&quot;>Gaze and &quot;Select&quot; voice command</span></span>
<span data-ttu-id=&quot;07492-198&quot;>Sprachbefehle sind eine der wichtigsten Interaktionsmethoden in Mixed Reality.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-198&quot;>Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id=&quot;07492-199&quot;>Es bietet einen leistungsstarken Freihandmechanismus zum Steuern des Systems.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-199&quot;>It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id=&quot;07492-200&quot;>Es gibt verschiedene Arten von Sprachinteraktionsmodellen:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-200&quot;>There are different types of voice interaction models:</span></span>

- <span data-ttu-id=&quot;07492-201&quot;>Der generische Befehl &quot;Select&quot;, der eine Click-Aktuation oder einen Commit als sekundäre Eingabe verwendet.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;07492-201&quot;>The generic &quot;Select&quot; command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id=&quot;07492-202&quot;>Objektbefehle (z. B. &quot;Schließen&quot; oder &quot;Vergrößern") führen einen Commit für eine Aktion als sekundäre Eingabe aus und committen sie.</span><span class="sxs-lookup"><span data-stu-id="07492-202">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="07492-203">Globale Befehle (z. B. "Gehe zu Start") erfordern kein Ziel.</span><span class="sxs-lookup"><span data-stu-id="07492-203">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="07492-204">Konversationsbenutzeroberflächen oder Entitäten wie Cortana verfügen über eine KI-Funktion in natürlicher Sprache.</span><span class="sxs-lookup"><span data-stu-id="07492-204">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="07492-205">Benutzerdefinierte Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="07492-205">Custom voice commands</span></span>

<span data-ttu-id="07492-206">Weitere Informationen zu Details und eine umfassende Liste der verfügbaren Sprachbefehle und deren Verwendung finden Sie in unserer Anleitung zur [Sprachbefehlsführung.](../out-of-scope/voice-design.md)</span><span class="sxs-lookup"><span data-stu-id="07492-206">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="07492-207">Gaze und HoloLens Clicker</span><span class="sxs-lookup"><span data-stu-id="07492-207">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="07492-208">HoloLens Clicker ist das erste Peripheriegerät, das speziell für HoloLens entwickelt wurde.</span><span class="sxs-lookup"><span data-stu-id="07492-208">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="07492-209">Sie ist in der HoloLens Development Edition (1. Generation) enthalten.</span><span class="sxs-lookup"><span data-stu-id="07492-209">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="07492-210">Mit dem HoloLens-Clicker kann ein Benutzer mit minimaler Handbewegung klicken und als sekundäre Eingabe committen.</span><span class="sxs-lookup"><span data-stu-id="07492-210">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="07492-211">Der HoloLens-Clicker stellt über Bluetooth Low Energy (BTLE) eine Verbindung mit HoloLens (1. Generation) oder HoloLens 2 her.</span><span class="sxs-lookup"><span data-stu-id="07492-211">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="07492-212">Weitere Informationen und Anweisungen zum Koppeln des Geräts</span><span class="sxs-lookup"><span data-stu-id="07492-212">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="07492-213">*Abbildung: HoloLens-Clicker*</span><span class="sxs-lookup"><span data-stu-id="07492-213">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens-Klick-Gerät](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="07492-215">Anv und Xbox Wireless Controller</span><span class="sxs-lookup"><span data-stu-id="07492-215">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="07492-216">Der Xbox Wireless Controller führt eine Klickbetätigung als sekundäre Eingabe mithilfe der Schaltfläche "A" aus.</span><span class="sxs-lookup"><span data-stu-id="07492-216">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="07492-217">Das Gerät wird einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen.</span><span class="sxs-lookup"><span data-stu-id="07492-217">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="07492-218">Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Zubehör Anwendung, um Ihren Xbox Wireless Controller zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="07492-218">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="07492-219">Koppeln eines Xbox-Controllers mit Ihrem PC</span><span class="sxs-lookup"><span data-stu-id="07492-219">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="07492-220">*Abbildung: Xbox Wireless Controller*</span><span class="sxs-lookup"><span data-stu-id="07492-220">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Xbox Wireless Controller](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="07492-222">Anving und Xbox Adaptive Controller</span><span class="sxs-lookup"><span data-stu-id="07492-222">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="07492-223">Der Xbox Adaptive Controller wurde hauptsächlich zur Erfüllung der Anforderungen von Gamern mit eingeschränkter Mobilität entwickelt und ist ein einheitlicher Hub für Geräte, mit dem Mixed Reality zugänglicher wird.</span><span class="sxs-lookup"><span data-stu-id="07492-223">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="07492-224">Der Xbox Adaptive Controller führt einen Klick als sekundäre Eingabe aus, indem er die Schaltfläche "A" verwendet.</span><span class="sxs-lookup"><span data-stu-id="07492-224">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="07492-225">Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen.</span><span class="sxs-lookup"><span data-stu-id="07492-225">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="07492-226">Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Zubehör, um Ihren Xbox Adaptive Controller zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="07492-226">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="07492-227">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="07492-227">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="07492-228">*Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="07492-228">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="07492-229">Verbinden Sie externe Geräte wie Switches, Schaltflächen, Einbinder und Halter, um eine benutzerdefinierte Controllererfahrung zu erstellen, die ihre eigene ist.</span><span class="sxs-lookup"><span data-stu-id="07492-229">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="07492-230">Eingaben für Schaltflächen, Thumbsticks und Trigger werden mit Hilfsgeräten gesteuert, die über 3,5-mm-Buchsen und USB-Anschlüsse verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="07492-230">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="07492-231">![Xbox Adaptive Controller-Anschlüsse](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="07492-231">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="07492-232">*Xbox Adaptive Controller-Anschlüsse*</span><span class="sxs-lookup"><span data-stu-id="07492-232">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="07492-233">Anweisungen zum Koppeln des Geräts</span><span class="sxs-lookup"><span data-stu-id="07492-233">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="07492-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Weitere Informationen, die auf der Xbox-Website verfügbar sind</a></span><span class="sxs-lookup"><span data-stu-id="07492-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="07492-235">Zusammengesetzte Gesten</span><span class="sxs-lookup"><span data-stu-id="07492-235">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="07492-236">In die Luft tippen</span><span class="sxs-lookup"><span data-stu-id="07492-236">Air tap</span></span>
<span data-ttu-id="07492-237">Die Tippbewegung in die Luft (und die anderen gesten unten) reagiert nur auf einen bestimmten Tippen.</span><span class="sxs-lookup"><span data-stu-id="07492-237">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="07492-238">Um andere Tippbewegungen wie Menu oder Grasp zu erkennen, muss Ihre Anwendung direkt die Interaktionen auf niedrigerer Ebene verwenden, die oben im Abschnitt mit den beiden wichtigsten Komponentengesten beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="07492-238">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="07492-239"> Tippen und halten Sie </span><span class="sxs-lookup"><span data-stu-id="07492-239">Tap and hold</span></span>
<span data-ttu-id="07492-240">„Halten“ bedeutet einfach, die Position mit dem Finger nach unten beim „In die Luft tippen“ beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="07492-240">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="07492-241">Die Kombination aus Tippen in die Luft und Halten ermöglicht verschiedene komplexere "Klick- und Drag"-Interaktionen in Kombination mit Armbewegungen, z. B. das Aufnehmen eines Objekts anstelle der Aktivierung oder sekundäre Interaktionen mit dem Mausdown, z. B. das Anzeigen eines Kontextmenüs.</span><span class="sxs-lookup"><span data-stu-id="07492-241">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="07492-242">Beim Entwerfen für diese Geste sollte jedoch Vorsicht geboten werden, da Benutzer bei jeder erweiterten Geste anfällig sein können, ihre Handhaltungen zu lockern.</span><span class="sxs-lookup"><span data-stu-id="07492-242">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="07492-243">Manipulation</span><span class="sxs-lookup"><span data-stu-id="07492-243">Manipulation</span></span>
<span data-ttu-id="07492-244">Manipulationsgesten können zum Verschieben, Ändern der Größe oder Drehen eines Hologramms verwendet werden, wenn das Hologramm 1:1 auf die Handbewegungen des Benutzers reagieren soll.</span><span class="sxs-lookup"><span data-stu-id="07492-244">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="07492-245">Eine Verwendungsmöglichkeit für solche 1:1-Bewegungen ist es, den Benutzer in der Umgebung zeichnen oder malen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="07492-245">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="07492-246">Die anfängliche Zielbestimmung für eine Manipulationsgeste sollte durch Anvisieren oder Zeigen erfolgen.</span><span class="sxs-lookup"><span data-stu-id="07492-246">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="07492-247">Sobald das Tippen und Halten beginnt, wird jede Objektbearbeitung durch Handbewegungen verarbeitet, wodurch der Benutzer sich beim Bearbeiten umschauen kann.</span><span class="sxs-lookup"><span data-stu-id="07492-247">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="07492-248">Navigation</span><span class="sxs-lookup"><span data-stu-id="07492-248">Navigation</span></span>
<span data-ttu-id="07492-249">Navigationsgesten funktionieren wie ein virtueller Joystick und können zur Navigation in Widgets der Benutzeroberfläche, z. B. Radialmenüs, verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="07492-249">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="07492-250">Sie tippen und halten, um die Geste zu starten, und bewegen dann Ihre Hand in einem normalisierten 3D-Würfel, der um die erste Betätigung herum angeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="07492-250">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="07492-251">Sie können Ihre Hand entlang der X-, Y- oder Z-Achse von einem Wert von -1 bis 1 bewegen, während 0 der Ausgangspunkt ist.</span><span class="sxs-lookup"><span data-stu-id="07492-251">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="07492-252">Mithilfe der Navigation können geschwindigkeitsbasierte kontinuierliche Gesten zum Scrollen oder Zoomen erstellt werden, ähnlich dem Scrollen bei einer 2D-Benutzeroberfläche durch Klicken mit der mittleren Maustaste und anschließendes Bewegen der Maus nach oben und unten.</span><span class="sxs-lookup"><span data-stu-id="07492-252">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="07492-253">Navigation mit Schienen bezieht sich auf die Fähigkeit, Bewegungen auf einer bestimmten Achse zu erkennen, bis ein bestimmter Schwellenwert auf dieser Achse erreicht ist.</span><span class="sxs-lookup"><span data-stu-id="07492-253">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="07492-254">Dies ist nur nützlich, wenn die Bewegung auf mehr als einer Achse in einer Anwendung durch den Entwickler aktiviert wird, z. B. wenn eine Anwendung so konfiguriert ist, dass Navigationsgesten über die X-, Y-Achse, aber auch die angegebene X-Achse mit Schienen erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="07492-254">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="07492-255">In diesem Fall erkennt das System Handbewegungen über die X-Achse, solange sie innerhalb einer imaginären Schienen (Führungslinie) auf der X-Achse verbleiben, wenn die Handbewegung auch auf der Y-Achse auftritt.</span><span class="sxs-lookup"><span data-stu-id="07492-255">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="07492-256">Innerhalb von 2D-Apps können Benutzer mit vertikalen Navigationsgesten innerhalb der App scrollen, zoomen oder ziehen.</span><span class="sxs-lookup"><span data-stu-id="07492-256">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="07492-257">Dadurch werden virtuelle Fingerberührungen in der App eingeführt, um Gesten für die Toucheingabe desselben Typs zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="07492-257">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="07492-258">Benutzer können auswählen, welche dieser Aktionen ausgeführt werden, indem sie zwischen den Tools auf der Leiste oberhalb der Anwendung umschalten, indem sie entweder die Schaltfläche auswählen oder "<Scrollen/Ziehen/Zoomen> Tool" sagen.</span><span class="sxs-lookup"><span data-stu-id="07492-258">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="07492-259">Weitere Informationen zu zusammengesetzten Gesten</span><span class="sxs-lookup"><span data-stu-id="07492-259">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="07492-260">Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="07492-260">Gesture recognizers</span></span>

<span data-ttu-id="07492-261">Ein Vorteil der Gestenerkennung besteht darin, dass Sie eine Gestenerkennung nur für die Gesten konfigurieren können, die das aktuell als Ziel dienende Hologramm akzeptieren kann.</span><span class="sxs-lookup"><span data-stu-id="07492-261">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="07492-262">Die Plattform unterscheidet nur nach Bedarf nach Bedarf, um diese bestimmten unterstützten Gesten zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="07492-262">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="07492-263">Auf diese Weise kann ein Hologramm, das nur das Tippen in die Luft unterstützt, eine beliebige Zeitspanne zwischen Drücken und Loslassen akzeptieren, während ein Hologramm, das tippen und halten unterstützt, das Tippen auf einen Haltebereich nach dem Schwellenwert für die Wartezeit heraufstufen kann.</span><span class="sxs-lookup"><span data-stu-id="07492-263">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="07492-264">Handerkennung</span><span class="sxs-lookup"><span data-stu-id="07492-264">Hand recognition</span></span>
<span data-ttu-id="07492-265">HoloLens erkennt Handgesten, indem die Position einer oder beider Hände, die für das Gerät sichtbar sind, verfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="07492-265">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="07492-266">HoloLens erkennt Hände, wenn sie sich entweder im Bereitschaftszustand (Handrücken mit nach oben gerichtetem Zeigefinger zu Ihnen gewandt) oder im gedrückten Zustand (Handrücken mit nach unten gerichtetem Zeigefinger zu Ihnen gewandt) befinden.</span><span class="sxs-lookup"><span data-stu-id="07492-266">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="07492-267">Wenn sich die Hände in anderen Posen befinden, ignoriert HoloLens sie.</span><span class="sxs-lookup"><span data-stu-id="07492-267">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="07492-268">Für jede Hand, die HoloLens erkennt, können Sie ohne Ausrichtung und gedrückten Zustand auf ihre Position zugreifen.</span><span class="sxs-lookup"><span data-stu-id="07492-268">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="07492-269">Wenn sich die Hand dem Rand des Gestenrahmens nähert, erhalten Sie auch einen Richtungsvektor, den Sie dem Benutzer zeigen können, damit er weiß, wie er seine Hand bewegen muss, um sie dorthin zurückzubringen, wo sie von HoloLens erkannt werden kann.</span><span class="sxs-lookup"><span data-stu-id="07492-269">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="07492-270">Gestenrahmen</span><span class="sxs-lookup"><span data-stu-id="07492-270">Gesture frame</span></span>
<span data-ttu-id="07492-271">Bei Gesten auf HoloLens muss sich die Hand innerhalb eines Gestenrahmens in einem Bereich befindet, den die Gestenerkennungskameras entsprechend sehen können, von der Stirn bis zur Tante und zwischen den Seiten.</span><span class="sxs-lookup"><span data-stu-id="07492-271">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="07492-272">Benutzer müssen in diesem Erkennungsbereich sowohl für den Erfolg der Aktion als auch für ihren eigenen Komfort trainiert werden.</span><span class="sxs-lookup"><span data-stu-id="07492-272">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="07492-273">Viele Benutzer gehen zunächst davon aus, dass sich der Gestenrahmen innerhalb ihrer Ansicht über HoloLens belassen und die Arme unerbittlich halten muss, um zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="07492-273">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="07492-274">Bei Verwendung des HoloLens-Clickers ist es nicht erforderlich, dass sich die Hände innerhalb des Gestenrahmens befinden.</span><span class="sxs-lookup"><span data-stu-id="07492-274">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="07492-275">Insbesondere bei kontinuierlichen Gesten besteht die Gefahr, dass Benutzer ihre Hände außerhalb des Gestenrahmens bewegen, während sie z. B. während der Geste ein holografisches Objekt bewegen und ihr beabsichtigtes Ergebnis verlieren.</span><span class="sxs-lookup"><span data-stu-id="07492-275">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="07492-276">Sie sollten die folgenden drei Aspekte berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="07492-276">There are three things that you should consider:</span></span>

- <span data-ttu-id="07492-277">Benutzerinformationen zum Vorhandensein des Gestenrahmens und zu den ungefähren Grenzen.</span><span class="sxs-lookup"><span data-stu-id="07492-277">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="07492-278">Dies wird während des HoloLens-Setups vermittelt.</span><span class="sxs-lookup"><span data-stu-id="07492-278">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="07492-279">Benachrichtigen von Benutzern, wenn sich ihre Gesten in der Nähe der Gestenrahmengrenzen innerhalb einer Anwendung befinden, bis zu dem Grad, in dem eine verlorene Geste zu unerwünschten Ergebnissen führt.</span><span class="sxs-lookup"><span data-stu-id="07492-279">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="07492-280">Die Forschung hat die wichtigsten Qualitäten eines solchen Benachrichtigungssystems gezeigt.</span><span class="sxs-lookup"><span data-stu-id="07492-280">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="07492-281">Die HoloLens-Shell bietet ein gutes Beispiel für diese Art von Benachrichtigung: visuelle Elemente am zentralen Cursor, die die Richtung angeben, in der die Begrenzungsüberquerung stattfindet.</span><span class="sxs-lookup"><span data-stu-id="07492-281">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="07492-282">Die Folgen des Überschreitens der Begrenzungen des Gestenrahmens sollten minimiert werden.</span><span class="sxs-lookup"><span data-stu-id="07492-282">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="07492-283">Im Allgemeinen bedeutet dies, dass das Ergebnis einer Geste an der Grenze angehalten und nicht umgekehrt werden sollte.</span><span class="sxs-lookup"><span data-stu-id="07492-283">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="07492-284">Wenn ein Benutzer beispielsweise ein holografisches Objekt über einen Raum bewegt, sollte die Bewegung anhalten, wenn der Gestenrahmen verletzt wird, und nicht an den Ausgangspunkt zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="07492-284">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="07492-285">Der Benutzer kann frustriert sein, kann aber die Grenzen schneller verstehen und muss nicht jedes Mal seine vollständigen beabsichtigten Aktionen neu starten.</span><span class="sxs-lookup"><span data-stu-id="07492-285">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="07492-286">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="07492-286">See also</span></span>
* [<span data-ttu-id="07492-287">Augenbasierte Interaktion</span><span class="sxs-lookup"><span data-stu-id="07492-287">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="07492-288">Blickverfolgung auf HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="07492-288">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="07492-289">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="07492-289">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="07492-290">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="07492-290">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="07492-291">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="07492-291">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="07492-292">Hände – Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="07492-292">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="07492-293">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="07492-293">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="07492-294">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="07492-294">Voice input</span></span>](voice-input.md)