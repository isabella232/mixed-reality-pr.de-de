---
title: Freihändig
description: Erfahren Sie mehr über die Schwierigkeiten, die Benutzer mit einer Hand-und Controller Schnittstelle haben können, und über verschiedene Freihand freie Alternativen.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality, Hands-Free, Gaze, Blick auf das Ziel, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Spracheingabe, Benutzerfreundlichkeit
ms.openlocfilehash: 7f4d3a0ec8d2e7435f54164006a8bd122b1ebcba
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702136"
---
# <a name="hands-free"></a><span data-ttu-id="79b41-104">Freihändig</span><span class="sxs-lookup"><span data-stu-id="79b41-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="79b41-105">Szenarien</span><span class="sxs-lookup"><span data-stu-id="79b41-105">Scenarios</span></span>

<span data-ttu-id="79b41-106">Wie in der [Übersicht über das Interaktionsmodell](interaction-fundamentals.md)erläutert, stellen Sie nach der Identifizierung Ihrer Benutzer und ihrer Ziele selbst fest, welche Umgebungs-oder situations Probleme bei der Ausführung ihrer Aufgaben auftreten können.</span><span class="sxs-lookup"><span data-stu-id="79b41-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="79b41-107">Beispielsweise müssen viele Benutzer ihre Hand haben, um Ihre tatsächlichen Ziele zu erreichen, und Sie haben Schwierigkeiten beim interagieren mit einer auf der Hand-und Controller basierten Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="79b41-107">For example, many users need to use their hands to accomplish their real-world goals, and they will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="79b41-108">Zu den spezifischen Szenarien gehören:</span><span class="sxs-lookup"><span data-stu-id="79b41-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="79b41-109">Führung durch eine Aufgabe, während die Hände des Benutzers beschäftigt sind</span><span class="sxs-lookup"><span data-stu-id="79b41-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="79b41-110">Nachschlagen in der Dokumentation, während die Hände des Benutzers beschäftigt sind</span><span class="sxs-lookup"><span data-stu-id="79b41-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="79b41-111">Ermüden der Hände</span><span class="sxs-lookup"><span data-stu-id="79b41-111">Hand fatigue</span></span>
* <span data-ttu-id="79b41-112">Handschuhe, die nicht nachverfolgt werden können</span><span class="sxs-lookup"><span data-stu-id="79b41-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="79b41-113">Tragen von Gegenständen in den Händen</span><span class="sxs-lookup"><span data-stu-id="79b41-113">Carrying something in their hands</span></span>
* <span data-ttu-id="79b41-114">Soziale Unbekümmertheit zum Durchführen von großen Handgesten</span><span class="sxs-lookup"><span data-stu-id="79b41-114">Social awkwardness to perform large hand gestures</span></span>
* <span data-ttu-id="79b41-115">Beengte Raumverhältnisse</span><span class="sxs-lookup"><span data-stu-id="79b41-115">Tight spaces</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="79b41-116">Hände freie Modalitäten</span><span class="sxs-lookup"><span data-stu-id="79b41-116">Hands-free modalities</span></span>

### <a name="voice-input"></a>[<span data-ttu-id="79b41-117">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="79b41-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="79b41-118">Die Verwendung Ihrer Stimme für die Befehls-und Steuerungsmöglichkeiten einer Schnittstelle bietet eine bequeme Möglichkeit, die Hände frei zu betreiben und Verknüpfungen zu verwenden, um mehrere Schritte bei Bedarf flexibel zu überspringen.</span><span class="sxs-lookup"><span data-stu-id="79b41-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to flexibly skip multiple steps if desired.</span></span> <span data-ttu-id="79b41-119">Mit der Spracheingabe kann der Benutzer einfach den Namen einer beliebigen Schaltfläche mit dem Namen "Loud" lesen, um ihn zu aktivieren _("anzeigen, sagen Sie")_ und sich mit einem Digital Agent abgleichen, der Aufgaben für Sie erledigen kann.</span><span class="sxs-lookup"><span data-stu-id="79b41-119">With voice input, the user can simply read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>


### <a name="gaze-and-dwell"></a>[<span data-ttu-id="79b41-120">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="79b41-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="79b41-121">In einigen praktischen Situationen ist die Verwendung Ihrer Stimme nicht ideal oder gar nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="79b41-121">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="79b41-122">Laute Factory-Umgebungen, Datenschutz oder soziale Standards können Einschränkungen aufweisen.</span><span class="sxs-lookup"><span data-stu-id="79b41-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="79b41-123">Mit dem "Eye + Dwell"-Modell kann der Benutzer durch eine APP navigieren, ohne dass zusätzliche Eingaben von der Augen-oder Kopfzeile entfernt werden: der Benutzer wird einfach im Ziel angezeigt (mit seinen Köpfen oder Augen), und er wird für einen Moment darauf gewartet, ihn zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="79b41-123">The gaze + dwell model allows the user to navigate an app without any additional input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="79b41-124">Weitere Informationen zu den einzelnen Entwurfs Überlegungen für "Blick" und "Wohnen" finden Sie unter " [Eye-Eye](gaze-and-dwell-eyes.md) " und "Wohnen" und " [Kopf-](gaze-and-dwell-head.md)und neben schauen"</span><span class="sxs-lookup"><span data-stu-id="79b41-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="79b41-125">Wechsel in und aus der Praxis freie Umstellung</span><span class="sxs-lookup"><span data-stu-id="79b41-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="79b41-126">In diesen Szenarien kann es von einer absoluten Anforderung bis zum Ende der Interaktion mit holograms für die Befehls-und Navigationsmöglichkeiten reichen, dass es sich um eine absolute Anforderung zum vollständigen betreiben der Anwendung handelt.</span><span class="sxs-lookup"><span data-stu-id="79b41-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="79b41-127">Wenn die Anforderung der Anwendung ist, dass Sie immer mit der Hand frei verwendet wird, egal ob mithilfe von "Dwell", benutzerdefinierten Sprachbefehlen oder mit dem Befehl "Select", dann stellen Sie sicher, dass Sie die entsprechenden Unternehmen in Ihrer Benutzeroberfläche vornehmen.</span><span class="sxs-lookup"><span data-stu-id="79b41-127">If the requirement of the application is that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="79b41-128">Wenn Ihr Ziel Benutzer in der Lage sein muss, nach eigenem Ermessen von Hand zu Hand zu wechseln, ist es wichtig, dass Sie die folgenden Prinzipien berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="79b41-128">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="79b41-129">Gehen Sie davon aus, dass der Benutzer bereits im Modus ist, zu dem gewechselt werden soll.</span><span class="sxs-lookup"><span data-stu-id="79b41-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="79b41-130">Wenn sich der Benutzer beispielsweise auf der Werks Seite befindet, sehen Sie sich einen Video Verweis auf den hololens an und beschließt, einen Schraubendreher zu starten, um die Arbeit zu starten. er würde höchstwahrscheinlich in Hand arbeiten arbeiten, ohne den Schrauben Strich zum Drücken einer Schaltfläche ablegen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="79b41-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="79b41-131">Sie sollte in der Lage sein, eine sprach Sitzung mit einem Voice-Befehl aufzurufen, eine bereits sichtbare Benutzeroberfläche zu finden, um zu beginnen, oder das Wort "Select".</span><span class="sxs-lookup"><span data-stu-id="79b41-131">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="79b41-132">Der Benutzer sollte folgende Möglichkeiten haben:</span><span class="sxs-lookup"><span data-stu-id="79b41-132">The user should have the ability to:</span></span> 
* <span data-ttu-id="79b41-133">Wechseln Sie in die Hände frei, während Sie kostenlos</span><span class="sxs-lookup"><span data-stu-id="79b41-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="79b41-134">Wechseln Sie zur Hand.</span><span class="sxs-lookup"><span data-stu-id="79b41-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="79b41-135">Wechseln zum Controller mithilfe eines Controllers</span><span class="sxs-lookup"><span data-stu-id="79b41-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="79b41-136">Erstellen von redundanten Möglichkeiten zum Wechseln von Modi</span><span class="sxs-lookup"><span data-stu-id="79b41-136">Create redundant ways to switch modes</span></span>
<span data-ttu-id="79b41-137">Beim ersten Prinzip geht es um den Zugriff, bei dem zweiten Prinzip um die Verfügbarkeit.</span><span class="sxs-lookup"><span data-stu-id="79b41-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="79b41-138">Es darf nicht nur eine Möglichkeit zum Wechseln in einen und aus einem Modus kommen.</span><span class="sxs-lookup"><span data-stu-id="79b41-138">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="79b41-139">Einige Beispiele sind:</span><span class="sxs-lookup"><span data-stu-id="79b41-139">Some examples would be:</span></span> 
* <span data-ttu-id="79b41-140">Eine Schaltfläche zum Starten von sprach Interaktionen</span><span class="sxs-lookup"><span data-stu-id="79b41-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="79b41-141">Ein Sprachbefehl für den Übergang zu, Verwendung von Head-Gaze und wohnen</span><span class="sxs-lookup"><span data-stu-id="79b41-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="79b41-142">Hinzufügen eines Bindestrichs</span><span class="sxs-lookup"><span data-stu-id="79b41-142">Add a dash of drama</span></span>
<span data-ttu-id="79b41-143">Ein Modusschalter ist ein großer Unternehmen, und es ist wichtig, dass Sie, wenn diese Übergänge eintreten, ein expliziter, sogar ein dramatischer Switch ist, damit der Benutzer weiß, was passiert ist.</span><span class="sxs-lookup"><span data-stu-id="79b41-143">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="79b41-144">Benutzerfreundlichkeit</span><span class="sxs-lookup"><span data-stu-id="79b41-144">Usability checklist</span></span>

<span data-ttu-id="79b41-145">**Kann der Benutzer alles durchführen, und alles, was für das Ende von Hand ist.**</span><span class="sxs-lookup"><span data-stu-id="79b41-145">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="79b41-146">Jede austauschbare Tabelle sollte auf die Hand frei zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="79b41-146">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="79b41-147">Stellen Sie sicher, dass alle benutzerdefinierten Gesten ersetzt werden, z. b. das Ändern der Größe, das platzieren, das Schwenken, das Tippen usw.</span><span class="sxs-lookup"><span data-stu-id="79b41-147">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="79b41-148">Stellen Sie sicher, dass der Benutzer jederzeit über eine sichere Kontrolle über das vorhanden sein von Benutzeroberflächen, die Platzierung und Ausführlichkeit verfügt.</span><span class="sxs-lookup"><span data-stu-id="79b41-148">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="79b41-149">So erhalten Sie die Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="79b41-149">Getting UI out of the way</span></span>
    * <span data-ttu-id="79b41-150">Adressieren der Benutzeroberfläche, die nicht in der Ansicht angezeigt wird (FOV)</span><span class="sxs-lookup"><span data-stu-id="79b41-150">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="79b41-151">Wie viel ich sehe, wo, wann</span><span class="sxs-lookup"><span data-stu-id="79b41-151">How much I see, where, when</span></span>

<span data-ttu-id="79b41-152">**Werden die Mechanismen der Interaktion mit den richtigen Kosten für die Interaktion gelehrt und verstärkt?**</span><span class="sxs-lookup"><span data-stu-id="79b41-152">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="79b41-153">Versteht der Benutzer...</span><span class="sxs-lookup"><span data-stu-id="79b41-153">Does the user understand ...</span></span>
* <span data-ttu-id="79b41-154">... In welchem Modus befinden Sie sich?</span><span class="sxs-lookup"><span data-stu-id="79b41-154">... What mode they are in?</span></span>
* <span data-ttu-id="79b41-155">... Was können Sie in diesem Modus tun?</span><span class="sxs-lookup"><span data-stu-id="79b41-155">... What they can do in this mode?</span></span>
* <span data-ttu-id="79b41-156">... Was ist der aktuelle Zustand?</span><span class="sxs-lookup"><span data-stu-id="79b41-156">... What is the current state?</span></span>
* <span data-ttu-id="79b41-157">... Wie können Sie übergehen?</span><span class="sxs-lookup"><span data-stu-id="79b41-157">... How they can transition out?</span></span>
    
<span data-ttu-id="79b41-158">**Ist die Benutzeroberfläche für die Hände frei optimiert?**</span><span class="sxs-lookup"><span data-stu-id="79b41-158">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="79b41-159">Beispiel: das Verb bauen von Strukturen ist nicht in typische 2D-Muster integriert.</span><span class="sxs-lookup"><span data-stu-id="79b41-159">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="79b41-160">Beispiel: die sprach Ausrichtung ist besser mit der Objekt Hervorhebung.</span><span class="sxs-lookup"><span data-stu-id="79b41-160">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="79b41-161">Beispiel: sprach Interaktionen sind besser mit Untertiteln, die eingeschaltet werden müssen</span><span class="sxs-lookup"><span data-stu-id="79b41-161">Example: Voice interactions are better with captions that need to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="79b41-162">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="79b41-162">See also</span></span>
* [<span data-ttu-id="79b41-163">Blickverfolgung auf HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="79b41-163">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="79b41-164">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="79b41-164">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="79b41-165">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="79b41-165">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="79b41-166">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="79b41-166">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="79b41-167">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="79b41-167">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="79b41-168">Hände – Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="79b41-168">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="79b41-169">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="79b41-169">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="79b41-170">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="79b41-170">Voice input</span></span>](voice-input.md)
