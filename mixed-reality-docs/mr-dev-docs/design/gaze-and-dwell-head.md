---
title: Anvisieren mit dem Kopf und Verweilen
description: Übersicht über das Eingabemodell „Anvisieren mit dem Kopf und Verweilen“
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Gemischte Realität, Blick, wohnen, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, UX, Richtlinien, Listenansicht
ms.openlocfilehash: 060d78ec629905ac9f2134851998ec131d85f0cd
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847367"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="28ef5-104">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="28ef5-104">Head-gaze and dwell</span></span>

<span data-ttu-id="28ef5-105">Wenn die Hände mit Werkzeugen und Gegenständen beschäftigt sind, können Gesten mühsam oder unmöglich sein.</span><span class="sxs-lookup"><span data-stu-id="28ef5-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="28ef5-106">Sprachbefehle können wie Gesten in bestimmten Kontexten unzuverlässig sein, z. B. unter zu lauten Umgebungsbedingungen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="28ef5-107">Darüber hinaus ist der Einsatz der Stimme zur Steuerung von Computern nicht überall üblich, aber seine Bedeutung nimmt sicherlich zu.</span><span class="sxs-lookup"><span data-stu-id="28ef5-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="28ef5-108">„Anvisieren mit dem Kopf und Verweilen“ bietet den bekanntesten und einfach zu bedienenden Mechanismus für das freihändige Heads-Up-Arbeiten mit der HoloLens.</span><span class="sxs-lookup"><span data-stu-id="28ef5-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="28ef5-109">Darüber hinaus ist das Modell „Anvisieren mit dem Kopf und Verweilen“ unabhängig von Störgeräuschen und Ruheeinschränkungen in der Betriebssystemumgebung zu 100 % zuverlässig.</span><span class="sxs-lookup"><span data-stu-id="28ef5-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="28ef5-110">Szenarien</span><span class="sxs-lookup"><span data-stu-id="28ef5-110">Scenarios</span></span>

<span data-ttu-id="28ef5-111">In Szenarien, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind, eignet sich der Kopf-und die Ansprechpartner hervorragend.</span><span class="sxs-lookup"><span data-stu-id="28ef5-111">Head-gaze and dwell is great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="28ef5-112">Die Funktion ist auch nützlich, wenn die Stimme aufgrund von Umwelt-oder sozialen Einschränkungen nicht 100% zuverlässig ist oder nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="28ef5-112">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span> <span data-ttu-id="28ef5-113">Ein gutes Beispiel ist eine Person, die eine HoloLens trägt, um Referenzinformationen bei der Reparatur eines Fahrzeugmotors zu überlagern.</span><span class="sxs-lookup"><span data-stu-id="28ef5-113">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="28ef5-114">Die Hände sind mit Werkzeugen beschäftigt oder stützen den eigenen Körper, während sich die Person in den Motorraum lehnt.</span><span class="sxs-lookup"><span data-stu-id="28ef5-114">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="28ef5-115">Der Garagenbereich ist laut, mit einem ständigen Klopfen und Knarren der Werkzeuge, wodurch sich die Verwendung von Sprachbefehlen schwierig gestaltet.</span><span class="sxs-lookup"><span data-stu-id="28ef5-115">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="28ef5-116">In der Kopfzeile und im Leben kann die Person, die die hololens verwendet, sicher in Ihrem Referenzmaterial navigieren, ohne den Workflow zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-116">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="28ef5-117">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="28ef5-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="28ef5-118"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="28ef5-118"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="28ef5-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="28ef5-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="28ef5-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="28ef5-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="28ef5-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="28ef5-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="28ef5-122">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="28ef5-122">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="28ef5-123">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="28ef5-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="28ef5-124">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="28ef5-124">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="28ef5-125">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="28ef5-125">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="28ef5-126">Entwurfsprinzipien</span><span class="sxs-lookup"><span data-stu-id="28ef5-126">Design principles</span></span>

<span data-ttu-id="28ef5-127">**Vermeiden Sie „Anvisieren als Waffe“**</span><span class="sxs-lookup"><span data-stu-id="28ef5-127">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="28ef5-128">„Anvisieren mit dem Kopf und Verweilen“ erfordert ein intuitives visuelles Feedback, aber zu viel Feedback kann beklemmend wirken.</span><span class="sxs-lookup"><span data-stu-id="28ef5-128">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="28ef5-129">Das Feedback sollte einem Benutzer helfen, seine Zielsetzungen zu erkennen, ihn aber nicht automatisch gegen seine Absicht auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-129">The feedback should help a user know what they're targeting, but not autoselect it against their intent.</span></span> <span data-ttu-id="28ef5-130">Beim Lesen von Text, Symbolen und Bezeichnungen müssen Sie den Benutzern Zeit zum Aufnehmen der Informationen geben, bevor Sie diese auswählen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-130">When reading text, icons, and labels, you need to provide users time to absorb the information before selecting.</span></span>
    
<span data-ttu-id="28ef5-131">**Informationen zur Geschwindigkeit**</span><span class="sxs-lookup"><span data-stu-id="28ef5-131">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="28ef5-132">Verweilinteraktionen können je nach Auswirkung der Navigation unterschiedliche Timer aufweisen – häufiger verwendete Funktionen profitieren in der Regel von schnelleren Füllzeiten, während konsequentere Funktionen von längeren Füllzeiten profitieren können.</span><span class="sxs-lookup"><span data-stu-id="28ef5-132">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="28ef5-133">Bei der Verwendung eines Fülleffekts zur Darstellung dieser Timer können Animationskurven der Füllfarbe das Gefühl schnellerer Füllzeiten positiv beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-133">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="28ef5-134">Es sollte erwogen werden, dem Benutzer die Möglichkeit zu bieten, sich für eine schnelle, mittlere und langsame Füllgeschwindigkeit zu entscheiden.</span><span class="sxs-lookup"><span data-stu-id="28ef5-134">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="28ef5-135">**Vermeiden von Jo-Jo-Effekten**</span><span class="sxs-lookup"><span data-stu-id="28ef5-135">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="28ef5-136">Der "Yo-Yo"-Effekt ist ein unangenehmes Kopf Verschiebungs Muster, das auftritt, wenn die Steuerelemente "Content Placement" und "Head-Do/Dwell" Benutzer immer wieder nach oben und unten suchen</span><span class="sxs-lookup"><span data-stu-id="28ef5-136">The yo-yo effect is an uncomfortable head movement pattern that happens when the content placement and head-gaze/dwell controls forces people to look up and down repeatedly.</span></span> <span data-ttu-id="28ef5-137">Beispielsweise wird in einem Listen Navigationsbereich mit der Schaltfläche "Kopf-und Weitergabe" am unteren Rand eine Schleife von "-Look down" angezeigt, um zu leben, nach Ergebnissen zu suchen, zu verweilen usw.</span><span class="sxs-lookup"><span data-stu-id="28ef5-137">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, and so on.</span></span> <span data-ttu-id="28ef5-138">Das resultierende Muster ist nicht sehr unbequem. Daher empfiehlt es sich, Navigations Steuerelemente an einem zentralisierten Speicherort zu platzieren, der weniger hin und her erfordert.</span><span class="sxs-lookup"><span data-stu-id="28ef5-138">The resulting pattern is uncomfortable, so we recommend placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="28ef5-139">Die Platzierung von Schaltflächen, die auf Ihren Effekten basieren, wird für den Komfort wichtig.</span><span class="sxs-lookup"><span data-stu-id="28ef5-139">Placement of dwell buttons based on their effects becomes important for comfort.</span></span>
<span data-ttu-id="28ef5-140">s</span><span class="sxs-lookup"><span data-stu-id="28ef5-140">s</span></span>
<br>

---

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="28ef5-141">Richtlinien und bewährte Methoden für die Benutzerumgebung</span><span class="sxs-lookup"><span data-stu-id="28ef5-141">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="28ef5-142">Zielgrößen</span><span class="sxs-lookup"><span data-stu-id="28ef5-142">Target sizes</span></span>

<span data-ttu-id="28ef5-143">Um auf einfache Weise zugänglich zu sein, müssen die Haupt-und zielziele groß genug sein, um sich bequem anzusehen, und einen der Kopf-und Endwerte für den vorgesehenen Zeitpunkt auf dem Ziel halten.</span><span class="sxs-lookup"><span data-stu-id="28ef5-143">To be easily accessible, head-gaze and dwell targets need to be large enough to look at comfortably, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="28ef5-144">Wir empfehlen eine minimale Zielgröße von 2 Grad, um die komfortablere Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-144">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="28ef5-145">Visuelles Feedback</span><span class="sxs-lookup"><span data-stu-id="28ef5-145">Visual feedback</span></span>

<span data-ttu-id="28ef5-146">Wenn Sie eine radiale Füllung zur Darstellung des Timers für das Verweilen verwenden, beginnen Sie in der Mitte der Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="28ef5-146">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="28ef5-147">Eine konsistente Reaktion ist weniger irritierend als vollständig unterschiedliche Richtungen auf verschiedenen Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-147">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="28ef5-148">Diese Regel kann jedoch für direktionale Interaktionen (z. b. Navigations nach oben/unten/links/rechts usw.) getrennt werden.</span><span class="sxs-lookup"><span data-stu-id="28ef5-148">This rule can be broken though for directional interactions (for example, nav up/down/left/right, and so on).</span></span> <span data-ttu-id="28ef5-149">Microsoft Dynamics 365-Handbücher machen z. B. eine Ausnahme, wenn WEITER/ZURÜCK von links nach rechts ausgefüllt werden.</span><span class="sxs-lookup"><span data-stu-id="28ef5-149">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="28ef5-150">Denken Sie daran, radiale Füllflächen von außen zu umschließen, für Szenarien wie das Umschalten auf eine Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="28ef5-150">Consider inverting radial fill from outside, for scenarios like toggling off a button.</span></span> <span data-ttu-id="28ef5-151">Das gegenläufige Gefühl beim Drücken einer Schaltfläche ist ein angenehmes visuelles Muster, das beibehalten werden sollte.</span><span class="sxs-lookup"><span data-stu-id="28ef5-151">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="28ef5-152">Schrittweise Offenlegung</span><span class="sxs-lookup"><span data-stu-id="28ef5-152">Progressive disclosure</span></span>

<span data-ttu-id="28ef5-153">„Schrittweise Offenlegung“ bedeutet, dass nur so viele Details angezeigt werden, wie in den einzelnen Phasen einer Interaktion relevant sind.</span><span class="sxs-lookup"><span data-stu-id="28ef5-153">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="28ef5-154">Für "Dwell" bedeutet dies, dass das "Dwell"-Ziel bei der Hervorhebung (z. b. in einem Listen Steuerelement) offen</span><span class="sxs-lookup"><span data-stu-id="28ef5-154">For dwell, that means the dwell target is revealed on highlight (for example, in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="28ef5-155">Überdimensionale Ziele</span><span class="sxs-lookup"><span data-stu-id="28ef5-155">Oversized targets</span></span>

<span data-ttu-id="28ef5-156">Der Verweilbereich kann größer als das inaktive Symbol sein, um die Verwendung zu erleichtern, wie die Schaltfläche „Zurück“ in Microsoft Dynamics 365-Handbüchern.</span><span class="sxs-lookup"><span data-stu-id="28ef5-156">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="28ef5-157">Vermeiden von Flimmern durch verzögertes Feedback</span><span class="sxs-lookup"><span data-stu-id="28ef5-157">Prevent flickering with delayed feedback</span></span>

<span data-ttu-id="28ef5-158">Verwenden Sie eine kurze Verzögerung, bevor Sie mit dem visuellen Feedback beginnen, um ein Flimmern zu vermeiden, wenn ein Benutzer ein Verweilziel überquert.</span><span class="sxs-lookup"><span data-stu-id="28ef5-158">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="28ef5-159">Halten Sie für Schaltflächen, mit denen häufig interagiert wird, die Verzögerung kurz, damit die Anwendung reaktiv ist.</span><span class="sxs-lookup"><span data-stu-id="28ef5-159">For buttons interacted with frequently, keep the delay short so the application feels reactive.</span></span>
* <span data-ttu-id="28ef5-160">Für Schaltflächen, die nur selten behandelt werden, kann eine längere Verzögerung sinnvoll sein, um die Schnittstelle zu vermeiden, die twitlapp ist.</span><span class="sxs-lookup"><span data-stu-id="28ef5-160">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>

<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="28ef5-161">Muster der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="28ef5-161">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="28ef5-162">Schaltflächen mit häufiger Interaktion</span><span class="sxs-lookup"><span data-stu-id="28ef5-162">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="28ef5-163">Schaltflächen mit hoher Frequenz sind Schaltflächen, die in der Regel in einer Anwendung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="28ef5-163">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="28ef5-164">Ein gutes Beispiel hierfür sind die Schaltflächen „Weiter“ und „Zurück“ in Microsoft Dynamics 365-Handbüchern.</span><span class="sxs-lookup"><span data-stu-id="28ef5-164">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="28ef5-165">**Empfehlungen**</span><span class="sxs-lookup"><span data-stu-id="28ef5-165">**Recommendations**</span></span><br>
  * <span data-ttu-id="28ef5-166">Die Schaltflächen mit hoher Frequenz sollten groß sein, und es ist einfacher, mit dem Kopf zu erreichen</span><span class="sxs-lookup"><span data-stu-id="28ef5-166">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="28ef5-167">Bleiben Sie in der Nähe der Augen, um eine ergonomische Überlastung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="28ef5-167">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="28ef5-168">*Bild: Microsoft Dynamics 365 Guides Schaltfläche "weiter"*</span><span class="sxs-lookup"><span data-stu-id="28ef5-168">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Schaltfläche "Microsoft Dynamics 365 Guides Next"](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="28ef5-170">Schaltflächen mit seltener Interaktion</span><span class="sxs-lookup"><span data-stu-id="28ef5-170">Low frequency buttons</span></span>

<span data-ttu-id="28ef5-171">Schaltflächen mit niedriger Frequenz sind Schaltflächen, die in der gesamten Anwendung nicht so häufig behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="28ef5-171">Low frequency buttons are buttons that aren't interacted with as regularly throughout the application.</span></span> <span data-ttu-id="28ef5-172">Ein gutes Beispiel könnte eine Schaltfläche für den Zugriff auf das Einstellungsmenü oder eine Schaltfläche zum Löschen der gesamten Arbeit sein.</span><span class="sxs-lookup"><span data-stu-id="28ef5-172">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="28ef5-173">Versuchen Sie, diese Schaltflächen von häufig genutzten Pfaden zum Anvisieren mit dem Kopf fernzuhalten, um eine versehentliche Aktivierung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="28ef5-173">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="28ef5-174">Bestätigungen</span><span class="sxs-lookup"><span data-stu-id="28ef5-174">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="28ef5-175">Wenn eine Aktion erhebliche Auswirkungen hat, z. b. das Berechnen von Geld, das Löschen von Arbeit oder das Starten eines langen Prozesses, ist es hilfreich, sicherzustellen, dass eine Person eine Schaltfläche auswählen wollte.</span><span class="sxs-lookup"><span data-stu-id="28ef5-175">When an action has significant impact, like charging money, deleting work, or starting a long process, it's useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="28ef5-176">**Empfehlungen**</span><span class="sxs-lookup"><span data-stu-id="28ef5-176">**Recommendations**</span></span><br>
  * <span data-ttu-id="28ef5-177">Auswahlhervorhebung auf Hauptschaltfläche anzeigen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-177">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="28ef5-178">Verweilziel gleichzeitig mit der Auswahlhervorhebung anzeigen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-178">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="28ef5-179">Verweilziel für die sekundäre Schaltfläche beim Anvisieren mit dem Kopf anzeigen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-179">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="28ef5-180">*Bild: Microsoft Dynamics 365-Führungslinien Bestätigungs Dialogfeld*</span><span class="sxs-lookup"><span data-stu-id="28ef5-180">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Bestätigungs Dialogfeld für Microsoft Dynamics 365-Anleitungen](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="28ef5-182">Umschalter</span><span class="sxs-lookup"><span data-stu-id="28ef5-182">Toggle buttons</span></span>

<span data-ttu-id="28ef5-183">Umschalter erfordern eine differenzierte Logik, um ordnungsgemäß zu funktionieren.</span><span class="sxs-lookup"><span data-stu-id="28ef5-183">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="28ef5-184">Wenn eine Person auf eine UMSCHALT Fläche klickt und Sie aktiviert, muss Sie die Schaltfläche Beenden und dann zurückkehren, um die vergabelogik neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="28ef5-184">When a person dwells on a toggle button and activates it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="28ef5-185">Es ist wichtig, dass umschaltbare Schaltflächen den Zustand "aktiv" und "inaktiv" aufweisen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-185">It's important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="28ef5-186">Listenansichten</span><span class="sxs-lookup"><span data-stu-id="28ef5-186">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="28ef5-187">Listenansichten stellen eine besondere Herausforderung für Kopf-und eingabeeingaben dar.</span><span class="sxs-lookup"><span data-stu-id="28ef5-187">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="28ef5-188">Personen können den Inhalt scannen, ohne dass Sie sich so fühlen müssen, dass Sie die zielziele kippen müssen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-188">People can scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="28ef5-189">**Empfehlungen**</span><span class="sxs-lookup"><span data-stu-id="28ef5-189">**Recommendations**</span></span><br>
  * <span data-ttu-id="28ef5-190">Lassen Sie die ganze Zeile hervorheben, wenn Sie in den Kopf-und Ausgangspunkt steht</span><span class="sxs-lookup"><span data-stu-id="28ef5-190">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="28ef5-191">Zeigt nur das Ziel an, wenn die Zeile hervorgehoben wird, um das visuelle Rauschen zu verringern.</span><span class="sxs-lookup"><span data-stu-id="28ef5-191">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="28ef5-192">Sie sollten klar und konsistent mit der Position von "Dwell Targets" sein.</span><span class="sxs-lookup"><span data-stu-id="28ef5-192">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="28ef5-193">Zeigen Sie nicht alle Ziele auf einmal an, um sich wiederholende Benutzeroberflächen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="28ef5-193">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="28ef5-194">Verwenden Sie das gleiche Muster so oft wie möglich, um die Benutzerfreundlichkeit der UX zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="28ef5-194">Reuse the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="28ef5-195">*Abbildung: Liste der Microsoft Dynamics 365-Leitfäden*</span><span class="sxs-lookup"><span data-stu-id="28ef5-195">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Liste der Microsoft Dynamics 365-Leitfäden](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="28ef5-197">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="28ef5-197">See also</span></span>

* [<span data-ttu-id="28ef5-198">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="28ef5-198">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="28ef5-199">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="28ef5-199">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="28ef5-200">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="28ef5-200">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="28ef5-201">Hände – Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="28ef5-201">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="28ef5-202">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="28ef5-202">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="28ef5-203">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="28ef5-203">Voice input</span></span>](voice-input.md)
