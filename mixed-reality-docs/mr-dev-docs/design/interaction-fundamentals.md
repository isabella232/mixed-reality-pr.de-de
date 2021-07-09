---
title: Instinktive Interaktionen
description: Lernen Sie die Philosophie der einfachen, instinktiven Interaktionen kennen, die in der gesamten Mixed Reality-Plattform verwurzelt ist.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Anvisieren, Zielbestimmung, Interaktion, Entwurf, HoloLens, MMR, kombiniert, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens
ms.openlocfilehash: 55e23ac2fb802af599fb9cc7d771d89d6ba36c47
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196415"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="b0baa-104">Einführung in instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="b0baa-104">Introducing instinctual interactions</span></span>

![Fernmanipulation mit den Händen](images/04_InteractionFundamentals.png)

<span data-ttu-id="b0baa-106">Die Philosophie der einfachen, instinktiven Interaktionen ist in der gesamten Mixed Reality-Plattform (MR) verwurzelt.</span><span class="sxs-lookup"><span data-stu-id="b0baa-106">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="b0baa-107">Wir haben drei Schritte unternommen, um sicherzustellen, dass Anwendungsdesigner und -entwickler ihren Kunden einfache und intuitive Interaktionen bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="b0baa-107">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="b0baa-108">Zunächst haben wir dafür gesorgt, dass unsere Sensoren und Eingabetechnologien zu multimodalen Interaktionsmodellen kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="b0baa-108">First, we've made sure our sensors and input technologies combine into multimodal interaction models.</span></span> <span data-ttu-id="b0baa-109">Diese Interaktionsmodelle umfassen das Hand- und Eyetracking sowie Eingaben in natürlicher Sprache.</span><span class="sxs-lookup"><span data-stu-id="b0baa-109">These interaction models include hand and eye tracking along with natural language input.</span></span> <span data-ttu-id="b0baa-110">Basierend auf unseren Studien ist das kombinierte Entwerfen und Entwickeln in einem multimodalen Framework – und nicht die Fokussierung auf einzelne Eingaben – der Schlüssel zur Realisierung instinktiver Erfahrungen.</span><span class="sxs-lookup"><span data-stu-id="b0baa-110">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="b0baa-111">Zweitens haben wir erkannt, dass viele Entwickler auf mehrere HoloLens-Geräte ausgerichtet sind, z. B. HoloLens 2 und HoloLens (1. Generation) oder HoloLens und VR.</span><span class="sxs-lookup"><span data-stu-id="b0baa-111">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span> <span data-ttu-id="b0baa-112">Deshalb haben wir unsere Interaktionsmodelle so konzipiert, dass sie geräteübergreifend funktionieren, auch wenn die Eingabetechnologie von Gerät zu Gerät variiert.</span><span class="sxs-lookup"><span data-stu-id="b0baa-112">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span> <span data-ttu-id="b0baa-113">So verwenden z. B. die ferne Interaktion bei einem Windows Immersive Headset mit einem 6DoF-Controller und HoloLens 2 jeweils dieselben Angebote und Muster.</span><span class="sxs-lookup"><span data-stu-id="b0baa-113">For example, far interaction on a Windows Immersive headset with a 6DoF controller and HoloLens 2 both use identical affordances and patterns.</span></span> <span data-ttu-id="b0baa-114">Dies erleichtert die geräteübergreifende Entwicklung und bietet Benutzerinteraktionen, die sich natürlich anfühlen.</span><span class="sxs-lookup"><span data-stu-id="b0baa-114">This makes it easy for cross-device application development and provides a natural feel to user interactions.</span></span> 

<span data-ttu-id="b0baa-115">Wir haben zwar erkannt, dass Mixed Reality (MR) Tausende von effektiven, ansprechenden und einzigartigen Interaktionen bietet, aber wir haben festgestellt, dass der bewusste Einsatz eines einzelnen umfassenden Interaktionsmodells in einer Anwendung der beste Weg ist, um sicherzustellen, dass Benutzer erfolgreich sind und ein großartiges Erlebnis haben.</span><span class="sxs-lookup"><span data-stu-id="b0baa-115">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="b0baa-116">Zu diesem Zweck haben wir drei Punkte in diese Interaktionsanleitung einbezogen:</span><span class="sxs-lookup"><span data-stu-id="b0baa-116">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="b0baa-117">Diese Anleitung um die drei primären Interaktionsmodelle und die für jedes einzelne Modell erforderlichen Komponenten und Muster.</span><span class="sxs-lookup"><span data-stu-id="b0baa-117">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="b0baa-118">Zusätzliche Anleitungen zu weiteren Vorteilen, die unsere Plattform bietet.</span><span class="sxs-lookup"><span data-stu-id="b0baa-118">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="b0baa-119">Allgemeine Anleitungen zur Auswahl des geeigneten Interaktionsmodells für Ihr Entwicklungsszenario.</span><span class="sxs-lookup"><span data-stu-id="b0baa-119">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="basic-hand-tracking-and-instinctual-interactions-demo"></a><span data-ttu-id="b0baa-120">Demo zu grundlegendem Handtracking und instinktiven Interaktionen</span><span class="sxs-lookup"><span data-stu-id="b0baa-120">Basic hand tracking and instinctual interactions demo</span></span>

<span data-ttu-id="b0baa-121">Sehen Sie sich unten unsere Videodemo **Entwerfen von Hologrammen: Kopf- und Eyetracking** an, und fahren Sie dann mit spezifischeren Themen fort:</span><span class="sxs-lookup"><span data-stu-id="b0baa-121">Check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below, then move on to more specific topics:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

<span data-ttu-id="b0baa-122">*Dieses Video wurde aus der HoloLens 2-App „Entwerfen von Hologrammen“ aufgenommen. Laden Sie die vollständige Erfahrung [hier](https://aka.ms/dhapp) herunter, und genießen Sie sie.*</span><span class="sxs-lookup"><span data-stu-id="b0baa-122">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="b0baa-123">Kombinierte Interaktionsmodelle</span><span class="sxs-lookup"><span data-stu-id="b0baa-123">Multimodal interaction models</span></span>

<span data-ttu-id="b0baa-124">Ausgehend von unseren Studien und dem Feedback von Kunden haben wir festgestellt, dass drei primäre Interaktionsmodelle für die meisten Mixed Reality-Umgebungen geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="b0baa-124">Based on our research and feedback from customers, we've discovered that three primary interaction models suit most mixed reality experiences.</span></span> <span data-ttu-id="b0baa-125">In vielerlei Hinsicht ist das Interaktionsmodell das mentale Modell des Benutzers zur Durchführung eines Workflows.</span><span class="sxs-lookup"><span data-stu-id="b0baa-125">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="b0baa-126">Jedes dieser Interaktionsmodelle ist für eine Reihe von Kundenanforderungen optimiert und ist bei richtiger Anwendung benutzerfreundlich, leistungsstark und praktikabel.</span><span class="sxs-lookup"><span data-stu-id="b0baa-126">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="b0baa-127">Das folgende Diagramm stellt eine vereinfachte Übersicht dar.</span><span class="sxs-lookup"><span data-stu-id="b0baa-127">The chart below is a simplified overview.</span></span> <span data-ttu-id="b0baa-128">Ausführliche Informationen zur Verwendung der einzelnen Interaktionsmodelle sind auf den folgenden Seiten mit Bildern und Codebeispielen verknüpft.</span><span class="sxs-lookup"><span data-stu-id="b0baa-128">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b0baa-129"><strong>Modell</strong></span><span class="sxs-lookup"><span data-stu-id="b0baa-129"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="b0baa-130"><strong>Beispielszenarien</strong></span><span class="sxs-lookup"><span data-stu-id="b0baa-130"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="b0baa-131"><strong>Eignung</strong></span><span class="sxs-lookup"><span data-stu-id="b0baa-131"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="b0baa-132"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="b0baa-132"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b0baa-133"><a href="hands-and-tools.md">Hände und Motion-Controller</a></span><span class="sxs-lookup"><span data-stu-id="b0baa-133"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="b0baa-134">3D-Raumerlebnisse, z. B. räumliches Layout und räumlicher Entwurf, Inhaltsmanipulation oder Simulation.</span><span class="sxs-lookup"><span data-stu-id="b0baa-134">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="b0baa-135">Ideal für neue Benutzer, kombiniert mit Stimme, Eyetracking oder Anvisieren mit dem Kopf.</span><span class="sxs-lookup"><span data-stu-id="b0baa-135">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="b0baa-136">Niedrige Lernkurve.</span><span class="sxs-lookup"><span data-stu-id="b0baa-136">Low learning curve.</span></span> <span data-ttu-id="b0baa-137">Konsistente Benutzererfahrung für Handtracking und Controller mit 6 Freiheitsgraden.</span><span class="sxs-lookup"><span data-stu-id="b0baa-137">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="b0baa-138">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b0baa-138">HoloLens 2</span></span><br><span data-ttu-id="b0baa-139">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="b0baa-139">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b0baa-140"><a href="hands-free.md">Freihändig</a></span><span class="sxs-lookup"><span data-stu-id="b0baa-140"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="b0baa-141">Kontextbezogene Erfahrungen, bei denen die Hände eines Benutzers beschäftigt sind, z. B. praxisnahes Lernen und Wartung.</span><span class="sxs-lookup"><span data-stu-id="b0baa-141">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="b0baa-142">Gewisser Lernaufwand erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b0baa-142">Some learning required.</span></span> <span data-ttu-id="b0baa-143">Das Gerät ist gut für Stimme und natürliche Sprache geeignet, wenn die Hände nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="b0baa-143">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="b0baa-144">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b0baa-144">HoloLens 2</span></span><br><span data-ttu-id="b0baa-145">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="b0baa-145">HoloLens (1st gen)</span></span><br><span data-ttu-id="b0baa-146">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="b0baa-146">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b0baa-147"><a href="gaze-and-commit.md">Anvisieren und Ausführen</a></span><span class="sxs-lookup"><span data-stu-id="b0baa-147"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="b0baa-148">Durchklickumgebungen, beispielsweise 3D-Präsentationen und Demos.</span><span class="sxs-lookup"><span data-stu-id="b0baa-148">Click-through experiences, for example, 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="b0baa-149">Erfordert Training für HMDs, aber nicht für mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="b0baa-149">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="b0baa-150">Ideal für verfügbare Controller.</span><span class="sxs-lookup"><span data-stu-id="b0baa-150">Best for accessible controllers.</span></span> <span data-ttu-id="b0baa-151">Ideal für HoloLens (1. Generation).</span><span class="sxs-lookup"><span data-stu-id="b0baa-151">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="b0baa-152">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b0baa-152">HoloLens 2</span></span><br><span data-ttu-id="b0baa-153">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="b0baa-153">HoloLens (1st gen)</span></span><br><span data-ttu-id="b0baa-154">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="b0baa-154">Immersive headsets</span></span><br><span data-ttu-id="b0baa-155">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="b0baa-155">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="b0baa-156">Zum Vermeiden von Lücken in der erlebten Benutzerinteraktion besteht das beste Vorgehen darin, die Anleitung für ein bestimmtes Modell von Anfang bis Ende zu befolgen.</span><span class="sxs-lookup"><span data-stu-id="b0baa-156">To avoid gaps in the user interaction experience, it's best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="b0baa-157">Die folgenden Abschnitte führen durch die Schritte zur Auswahl und Implementierung eines dieser Interaktionsmodelle.</span><span class="sxs-lookup"><span data-stu-id="b0baa-157">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-youll-understand-our-guidance-on"></a><span data-ttu-id="b0baa-158">Am Ende dieser Seite werden Sie unsere Anleitung zu Folgendem verstehen:</span><span class="sxs-lookup"><span data-stu-id="b0baa-158">By the end of this page, you'll understand our guidance on:</span></span>
 
* <span data-ttu-id="b0baa-159">Auswählen eines Interaktionsmodells für Ihren Kunden</span><span class="sxs-lookup"><span data-stu-id="b0baa-159">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="b0baa-160">Implementieren des Interaktionsmodells</span><span class="sxs-lookup"><span data-stu-id="b0baa-160">Implementing the interaction model</span></span>
* <span data-ttu-id="b0baa-161">Wechseln zwischen Interaktionsmodellen</span><span class="sxs-lookup"><span data-stu-id="b0baa-161">Transitioning between interaction models</span></span>
* <span data-ttu-id="b0baa-162">Entwerfen der nächsten Schritte</span><span class="sxs-lookup"><span data-stu-id="b0baa-162">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="b0baa-163">Auswählen eines Interaktionsmodells für Ihren Kunden</span><span class="sxs-lookup"><span data-stu-id="b0baa-163">Choose an interaction model for your customer</span></span>

<span data-ttu-id="b0baa-164">In der Regel haben Entwickler und Ersteller die Arten von Interaktionen, die Ihre Kunden ausführen können, bereits durchdacht.</span><span class="sxs-lookup"><span data-stu-id="b0baa-164">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="b0baa-165">Um einen kundenorientierten Ansatz für den Entwurf zu fördern, empfehlen wir Ihnen die folgende Anleitung zur Auswahl des für Ihren Kunden optimierten Interaktionsmodells.</span><span class="sxs-lookup"><span data-stu-id="b0baa-165">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="b0baa-166">Gründe zum Befolgen dieser Anleitung</span><span class="sxs-lookup"><span data-stu-id="b0baa-166">Why follow this guidance?</span></span>

* <span data-ttu-id="b0baa-167">Wir testen unsere Interaktionsmodelle nach objektiven und subjektiven Kriterien, wie physischer und kognitiver Leistung, Intuitivität und Erlernbarkeit.</span><span class="sxs-lookup"><span data-stu-id="b0baa-167">We test our interaction models for objective and subjective criteria, including physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="b0baa-168">Da die Interaktion unterschiedlich verläuft, können sich auch die visuellen/akustischen Angebote sowie das Objektverhalten zwischen Interaktionsmodellen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="b0baa-168">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="b0baa-169">Die Kombination von Komponenten verschiedener Interaktionsmodelle birgt das Risiko konkurrierender Angebote, z. B. simultane Handstrahlen und ein Cursor zum Anvisieren mit dem Kopf.</span><span class="sxs-lookup"><span data-stu-id="b0baa-169">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="b0baa-170">Dies kann Benutzer überfordern und verwirren.</span><span class="sxs-lookup"><span data-stu-id="b0baa-170">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="b0baa-171">Hier folgen einige Beispiele dazu, wie Angebote und Verhaltensweisen für die einzelnen Interaktionsmodelle optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="b0baa-171">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="b0baa-172">Neue Benutzer haben häufig ähnliche Fragen, z. B. _„Woher weiß ich, dass das System funktioniert?“_ , _„Woher weiß ich, über welche Möglichkeiten ich verfüge?“_ und _„Woher weiß ich, ob es verstanden hat, was ich gerade getan habe?“_ .</span><span class="sxs-lookup"><span data-stu-id="b0baa-172">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b0baa-173"><strong>Modell</strong></span><span class="sxs-lookup"><span data-stu-id="b0baa-173"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="b0baa-174"><strong>Woher weiß ich, dass es funktioniert?</strong></span><span class="sxs-lookup"><span data-stu-id="b0baa-174"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="b0baa-175"><strong>Woher weiß ich, über welche Möglichkeiten ich verfüge?</strong></span><span class="sxs-lookup"><span data-stu-id="b0baa-175"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="b0baa-176"><strong>Woher weiß ich, was ich gerade getan habe?</strong></span><span class="sxs-lookup"><span data-stu-id="b0baa-176"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b0baa-177"><a href="hands-and-tools.md">Hände und Motion-Controller</a></span><span class="sxs-lookup"><span data-stu-id="b0baa-177"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="b0baa-178">Ich sehe ein Handgittermodell, ein Fingerspitzenangebot oder Hand-/Controllerstrahlen.</span><span class="sxs-lookup"><span data-stu-id="b0baa-178">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="b0baa-179">Es werden greifbare Ziehpunkte oder ein Begrenzungsrahmen angezeigt, wenn die Hand sich in der Nähe des Objekts befindet.</span><span class="sxs-lookup"><span data-stu-id="b0baa-179">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="b0baa-180">Ich höre Töne und sehe Animationen beim Greifen und Loslassen.</span><span class="sxs-lookup"><span data-stu-id="b0baa-180">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b0baa-181"><a href="gaze-and-commit.md">Anvisieren mit dem Kopf und Ausführen</a></span><span class="sxs-lookup"><span data-stu-id="b0baa-181"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="b0baa-182">Ich sehe einen Cursor in der Mitte meines Sichtfelds.</span><span class="sxs-lookup"><span data-stu-id="b0baa-182">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="b0baa-183">Der Cursor wechselt den Zustand, wenn er sich über bestimmten Objekten befindet.</span><span class="sxs-lookup"><span data-stu-id="b0baa-183">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="b0baa-184">Ich sehe/höre beim Agieren visuelle und akustische Bestätigungen.</span><span class="sxs-lookup"><span data-stu-id="b0baa-184">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="b0baa-185"><a href="hands-free.md">Freihändig (Anvisieren mit dem Kopf und Verweilen)</a></span><span class="sxs-lookup"><span data-stu-id="b0baa-185"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="b0baa-186">Ich sehe einen Cursor in der Mitte meines Sichtfelds.</span><span class="sxs-lookup"><span data-stu-id="b0baa-186">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="b0baa-187">Ich sehe eine Statusanzeige, wenn ich über einem interaktionsfähigen Objekt verweile.</span><span class="sxs-lookup"><span data-stu-id="b0baa-187">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="b0baa-188">Ich sehe/höre beim Agieren visuelle und akustische Bestätigungen.</span><span class="sxs-lookup"><span data-stu-id="b0baa-188">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b0baa-189"><a href="hands-free.md">Freihändig (Sprachbefehle)</a></span><span class="sxs-lookup"><span data-stu-id="b0baa-189"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="b0baa-190">Ich sehe eine Anzeige zur Spracherkennung und Untertitel, die zeigen, was das System gehört hat.</span><span class="sxs-lookup"><span data-stu-id="b0baa-190">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="b0baa-191">Ich erhalte Sprachansagen und Hinweise.</span><span class="sxs-lookup"><span data-stu-id="b0baa-191">I get voice prompts and hints.</span></span> <span data-ttu-id="b0baa-192">Wenn ich Folgendes sage: Was kann ich sagen?</span><span class="sxs-lookup"><span data-stu-id="b0baa-192">When I say: "What can I say?"</span></span> <span data-ttu-id="b0baa-193">Ich sehe ein Feedback.</span><span class="sxs-lookup"><span data-stu-id="b0baa-193">I see feedback.</span></span></td>
        <td><span data-ttu-id="b0baa-194">Ich sehe/höre visuelle und akustische Bestätigungen, wenn ich einen Befehl erteile, oder erhalte bei Bedarf die Benutzerumgebung zur Mehrdeutigkeitsvermeidung.</span><span class="sxs-lookup"><span data-stu-id="b0baa-194">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="b0baa-195">Nachfolgend sind Fragen aufgeführt, die Teams (gemäß unserer Erfahrung) bei der Auswahl eines Interaktionsmodells geholfen haben:</span><span class="sxs-lookup"><span data-stu-id="b0baa-195">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="b0baa-196">Q:  Möchten meine Benutzer Hologramme berühren und präzise holografische Eingriffe durchführen?</span><span class="sxs-lookup"><span data-stu-id="b0baa-196">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="b0baa-197">A:  In diesem Fall sollten Sie das Interaktionsmodell für Hände und Motion-Controller für die Präzisionszielbestimmung und für Eingriffe ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="b0baa-197">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="b0baa-198">Q:  Müssen meine Benutzer für reale Aufgaben die Hände frei haben?</span><span class="sxs-lookup"><span data-stu-id="b0baa-198">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="b0baa-199">A:  In diesem Fall sollten Sie sich das Interaktionsmodell „Freihändig“ ansehen, das durch blick- und sprachbasierte Interaktionen eine großartige freihändige Umgebung bietet.</span><span class="sxs-lookup"><span data-stu-id="b0baa-199">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="b0baa-200">Q:  Haben meine Benutzer Zeit, Interaktionen für meine MR-Anwendung zu erlernen, oder sind Interaktionen mit einer möglichst geringen Lernkurve erforderlich?</span><span class="sxs-lookup"><span data-stu-id="b0baa-200">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="b0baa-201">A:  Wir empfehlen das Modell für Hände und Motion-Controller für die flachste Lernkurve und intuitivste Interaktion, sofern die Benutzer ihre Hände zur Interaktion nutzen können.</span><span class="sxs-lookup"><span data-stu-id="b0baa-201">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users can use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="b0baa-202">Q:  Verwenden meine Benutzer Motion-Controller zum Zeigen und Bearbeiten?</span><span class="sxs-lookup"><span data-stu-id="b0baa-202">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="b0baa-203">A:  Das Modell für Hände und Motion-Controller enthält alle Anleitungen für ein großartiges Erlebnis mit den Motion-Controllern.</span><span class="sxs-lookup"><span data-stu-id="b0baa-203">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="b0baa-204">Q:  Verwenden meine Benutzer einen Controller für Barrierefreiheit oder einen herkömmlichen Bluetooth-Controller, z. B. ein Klick-Gerät?</span><span class="sxs-lookup"><span data-stu-id="b0baa-204">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="b0baa-205">A:  Wir empfehlen das Modell „Anvisieren mit dem Kopf und Ausführen“ für alle nicht nachverfolgten Controller.</span><span class="sxs-lookup"><span data-stu-id="b0baa-205">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="b0baa-206">Es wurde für Benutzer entwickelt, um ein ganzheitliches Erlebnis mit einem einfachen Mechanismus für „Anvisieren und Ausführen“ zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="b0baa-206">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="b0baa-207">Q: Können meine Benutzer in einer Umgebung nur durch „Durchklicken“ voranschreiten (z. B. wie bei einer 3D-Diashow), anstatt durch kompakte Layouts von Steuerelementen der Benutzeroberfläche zu navigieren?</span><span class="sxs-lookup"><span data-stu-id="b0baa-207">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="b0baa-208">A:  Wenn Benutzer nicht viele Komponenten einer Benutzeroberfläche steuern müssen, bietet „Anvisieren mit dem Kopf und Ausführen“ eine erlernbare Option, bei der sich Benutzer nicht um die Zielbestimmung kümmern müssen.</span><span class="sxs-lookup"><span data-stu-id="b0baa-208">A:  If users don't need to control a lot of UI, Head-gaze and commit offers a learnable option where users don't have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="b0baa-209">Q:  Verwenden meine Benutzer sowohl HoloLens (1. Generation) als auch HoloLens 2/Immersive Windows Mixed Reality-Headsets (VR)?</span><span class="sxs-lookup"><span data-stu-id="b0baa-209">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="b0baa-210">A:  Da „Anvisieren mit dem Kopf und Ausführen“ das Interaktionsmodell für HoloLens (1. Generation) ist, empfehlen wir Entwicklern, die HoloLens (1. Generation) unterstützen, „Anvisieren mit dem Kopf und Ausführen“ nur alle Features oder Modi zu verwenden, die Benutzer auf einem HoloLens-Headset (1. Generation) erleben können.</span><span class="sxs-lookup"><span data-stu-id="b0baa-210">A:  Since Head-gaze and commit are the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="b0baa-211">Weitere Informationen zur Erstellung einer großartigen Umgebung für mehrere HoloLens-Generationen finden Sie unter *Wechseln zwischen Interaktionsmodellen*.</span><span class="sxs-lookup"><span data-stu-id="b0baa-211">See the next section on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="b0baa-212">Q: Wie sieht es mit mobilen Benutzern, die einen großen Raum abdecken oder sich zwischen verschiedenen Räumen bewegen, im Vergleich mit Benutzern aus, die dazu neigen, in einem einzelnen Raum zu arbeiten?</span><span class="sxs-lookup"><span data-stu-id="b0baa-212">Q: What about users who are mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="b0baa-213">A:  Für diese Benutzer ist jedes der Interaktionsmodelle geeignet.</span><span class="sxs-lookup"><span data-stu-id="b0baa-213">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="b0baa-214">Weitere Anleitungen zum App-Design sind [bald verfügbar](../out-of-scope/news.md).</span><span class="sxs-lookup"><span data-stu-id="b0baa-214">More guidance specific to app design [coming soon](../out-of-scope/news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="b0baa-215">Wechseln zwischen Interaktionsmodellen</span><span class="sxs-lookup"><span data-stu-id="b0baa-215">Transitioning interaction models</span></span>
<span data-ttu-id="b0baa-216">Es kann auch vorkommen, dass Ihre Anwendungsfälle die Verwendung mehrerer Interaktionsmodelle erfordern.</span><span class="sxs-lookup"><span data-stu-id="b0baa-216">There are also use cases that might require using more than one interaction model.</span></span> <span data-ttu-id="b0baa-217">Beim „Erstellungsablauf“ Ihrer Anwendung wird z. B. das Interaktionsmodell _„Hände und Motion-Controller“_ verwendet, aber Sie möchten einen Freihandmodus für Außendiensttechniker verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0baa-217">For example, your application's creation flow uses the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span> <span data-ttu-id="b0baa-218">Wenn Ihre Umgebung mehrere Interaktionsmodelle erfordert, haben die Benutzer möglicherweise Schwierigkeiten beim Übergang von einem Modell zum anderen, insbesondere, wenn sie noch nicht mit Mixed Reality vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="b0baa-218">If your experience does require multiple interaction models, users might have difficulty transitioning from one model to another, especially when they're new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="b0baa-219">Wir arbeiten ständig an weiteren Anleitungen, die Entwicklern und Designern zur Verfügung stehen werden und sie über das Wie, Wann und Warum für den Einsatz mehrerer MR-Interaktionsmodelle informieren sollen.</span><span class="sxs-lookup"><span data-stu-id="b0baa-219">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="b0baa-220">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b0baa-220">See also</span></span>
* [<span data-ttu-id="b0baa-221">Komfort</span><span class="sxs-lookup"><span data-stu-id="b0baa-221">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="b0baa-222">Augenbasierte Interaktion</span><span class="sxs-lookup"><span data-stu-id="b0baa-222">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="b0baa-223">Blickverfolgung auf HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b0baa-223">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="b0baa-224">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="b0baa-224">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b0baa-225">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="b0baa-225">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="b0baa-226">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="b0baa-226">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b0baa-227">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="b0baa-227">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="b0baa-228">Hände – Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="b0baa-228">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="b0baa-229">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="b0baa-229">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b0baa-230">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="b0baa-230">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="b0baa-231">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="b0baa-231">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="b0baa-232">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="b0baa-232">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="b0baa-233">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="b0baa-233">Voice input</span></span>](voice-input.md)


