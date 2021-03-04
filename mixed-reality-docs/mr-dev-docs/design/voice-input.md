---
title: Spracheingabe
description: Die Spracheingabe ist eine Kern Eingabe für hololens und Windows Mixed Reality-immersive Headsets. Voice kann für Befehle, Diktat, Cortana usw. verwendet werden.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, Voice, Cortana, Speech, Input, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Blick
ms.openlocfilehash: cc1ecd7d236748c3c4de77678e6f67c69a2c1af1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759141"
---
# <a name="voice-input"></a><span data-ttu-id="2a0df-105">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="2a0df-105">Voice input</span></span>

![Spracheingabe](images/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="2a0df-107">Die Stimme ist eine der wichtigsten Formen der Eingabe für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2a0df-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="2a0df-108">Damit können Sie ein – Hologramm direkt aufrufen, ohne [Handgesten](gaze-and-commit.md#composite-gestures)verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="2a0df-109">Die Spracheingabe kann eine natürliche Art sein, Ihre Absichten zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="2a0df-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="2a0df-110">Voice eignet sich besonders gut für die Durchführung komplexer Schnittstellen, da Benutzer mit einem Befehl die Möglichkeit haben, die Verwendung von Netz Menüs zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="2a0df-111">Die Spracheingabe wird von [derselben Engine](/windows/uwp/design/input/speech-recognition) unterstützt, die Sprache in allen _universellen Windows-apps_ unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2a0df-111">Voice input is powered by the [same engine](/windows/uwp/design/input/speech-recognition) that supports speech in all _Universal Windows Apps_.</span></span> <span data-ttu-id="2a0df-112">Bei hololens funktioniert die Spracherkennung immer in der Windows-Anzeige Sprache, die in ihren Geräteeinstellungen konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="2a0df-112">On HoloLens, speech recognition will always function in the Windows display language configured in your device Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="2a0df-113">Sprach-und Blick</span><span class="sxs-lookup"><span data-stu-id="2a0df-113">Voice and gaze</span></span>

<span data-ttu-id="2a0df-114">Wenn Sie Sprachbefehle verwenden, ist Head-oder Eye-Eye der typische Ziel Mechanismus, egal ob mit einem Cursor "Select" oder der Kanal für Ihren Befehl an eine Anwendung, die Sie sich ansehen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-114">When you're using voice commands, head or eye gaze is the typical targeting mechanism, whether with a cursor to "select" or to channel your command to an application you're looking at.</span></span> <span data-ttu-id="2a0df-115">Möglicherweise ist es nicht einmal erforderlich, einen Cursor Cursor anzuzeigen _("Weitere_ Informationen" anzeigen).</span><span class="sxs-lookup"><span data-stu-id="2a0df-115">It may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="2a0df-116">Einige Sprachbefehle benötigen überhaupt kein Ziel, z. b. "Gehe zu Start" oder "Hey Cortana".</span><span class="sxs-lookup"><span data-stu-id="2a0df-116">Some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="2a0df-117">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="2a0df-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2a0df-118"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="2a0df-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="2a0df-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2a0df-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2a0df-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2a0df-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2a0df-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="2a0df-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2a0df-122">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="2a0df-122">Voice input</span></span></td>
        <td><span data-ttu-id="2a0df-123">✔️</span><span class="sxs-lookup"><span data-stu-id="2a0df-123">✔️</span></span></td>
        <td><span data-ttu-id="2a0df-124">✔️</span><span class="sxs-lookup"><span data-stu-id="2a0df-124">✔️</span></span></td>
        <td><span data-ttu-id="2a0df-125">✔️ (mit Mikrofon)</span><span class="sxs-lookup"><span data-stu-id="2a0df-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="2a0df-126">Der Befehl "Select"</span><span class="sxs-lookup"><span data-stu-id="2a0df-126">The "select" command</span></span>

<span data-ttu-id="2a0df-127">**HoloLens (1. Generation)**</span><span class="sxs-lookup"><span data-stu-id="2a0df-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="2a0df-128">Auch wenn Sie Ihrer APP keine Sprachunterstützung hinzufügen, können Ihre Benutzer holograms aktivieren, indem Sie einfach den System Sprachbefehl "Select" sagen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="2a0df-129">Dies verhält sich wie eine [Luft](gaze-and-commit.md#composite-gestures) Abzweigung in hololens, das Drücken der Schaltfläche "auswählen" auf dem [hololens-Clicker](/hololens/hololens1-clicker)oder das Drücken des Auslösers auf einem [Windows Mixed Reality Motion Controller](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="2a0df-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="2a0df-130">Sie werden einen Sound hören und sehen, dass eine QuickInfo mit "Select" als Bestätigung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2a0df-130">You'll hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="2a0df-131">"Select" wird durch einen Algorithmus für die Schlüsselwort Erkennung mit niedrigem Energieverbrauch aktiviert. Dies bedeutet, dass Sie dies jederzeit mit minimalen Auswirkungen auf die Akku Lebensdauer sagen können.</span><span class="sxs-lookup"><span data-stu-id="2a0df-131">"Select" is enabled by a low-power keyword detection algorithm, which means you can say it anytime with minimal battery life impact.</span></span> <span data-ttu-id="2a0df-132">Sie können sogar "Select" mit ihren Händen auf der Seite sagen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-132">You can even say "select" with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="2a0df-133">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="2a0df-133">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="2a0df-134">Wenn Sie den Befehl "Select" in hololens 2 verwenden möchten, müssen Sie zuerst den Cursor Cursor zur Verwendung als Zeiger verwenden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-134">To use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="2a0df-135">Der Befehl zur Eingabe ist leicht zu merken, einfach "Select".</span><span class="sxs-lookup"><span data-stu-id="2a0df-135">The command to bring it up is easy to remember--just say, "select".</span></span><br><br>
        <span data-ttu-id="2a0df-136">Um den Modus zu beenden, verwenden Sie die Hände erneut, indem Sie tippen, eine Schaltfläche mit Ihren Fingern nähern oder die System Bewegung verwenden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-136">To exit the mode, use your hands again by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br> 
        <span data-ttu-id="2a0df-137">*Bild: "Select", um den Voice-Befehl für die Auswahl zu verwenden*</span><span class="sxs-lookup"><span data-stu-id="2a0df-137">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Ein Benutzer kann "Select" (auswählen) verwenden, um den Voice-Befehl für eine Auswahl zu verwenden.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a><span data-ttu-id="2a0df-139">Hallo, Cortana</span><span class="sxs-lookup"><span data-stu-id="2a0df-139">Hey Cortana</span></span>

<span data-ttu-id="2a0df-140">Sie können auch "Hey Cortana" sagen, um Cortana zu einem beliebigen Zeitpunkt zu machen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-140">You can say "Hey Cortana" to bring up Cortana at any time.</span></span> <span data-ttu-id="2a0df-141">Sie müssen nicht warten, bis Sie angezeigt wird, um Ihre Frage zu beantworten oder Ihnen eine Anweisung zu geben.</span><span class="sxs-lookup"><span data-stu-id="2a0df-141">You don't have to wait for her to appear to continue asking her your question or giving her an instruction.</span></span> <span data-ttu-id="2a0df-142">Beispielsweise: "Hey Cortana, was ist das Wetter?"</span><span class="sxs-lookup"><span data-stu-id="2a0df-142">For example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="2a0df-143">als einzelner Satz.</span><span class="sxs-lookup"><span data-stu-id="2a0df-143">as a single sentence.</span></span> <span data-ttu-id="2a0df-144">Weitere Informationen zu Cortana und ihren Möglichkeiten finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="2a0df-144">For more information about Cortana and what you can do, ask her!</span></span> <span data-ttu-id="2a0df-145">Sagen Sie: "Hey Cortana, was kann ich sagen?"</span><span class="sxs-lookup"><span data-stu-id="2a0df-145">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="2a0df-146">und Sie werden eine Liste der funktionierenden und vorgeschlagenen Befehle abrufen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-146">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="2a0df-147">Wenn Sie sich bereits in der Cortana-App befinden, wählen Sie das **?**</span><span class="sxs-lookup"><span data-stu-id="2a0df-147">If you're already in the Cortana app, select the **?**</span></span> <span data-ttu-id="2a0df-148">Symbol auf der Rand Leiste, um das gleiche Menü zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-148">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="2a0df-149">**Hololens-spezifische Befehle**</span><span class="sxs-lookup"><span data-stu-id="2a0df-149">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="2a0df-150">Was kann ich sagen?</span><span class="sxs-lookup"><span data-stu-id="2a0df-150">"What can I say?"</span></span>
* <span data-ttu-id="2a0df-151">"Gehe zu Start"-anstelle von " [Bloom](system-gesture.md#bloom) ", um zum [Startmenü](../discover/navigating-the-windows-mixed-reality-home.md#start-menu) zu gelangen</span><span class="sxs-lookup"><span data-stu-id="2a0df-151">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="2a0df-152">"Starten <app> "</span><span class="sxs-lookup"><span data-stu-id="2a0df-152">"Launch <app>"</span></span>
* <span data-ttu-id="2a0df-153">" <app> Hier verschieben"</span><span class="sxs-lookup"><span data-stu-id="2a0df-153">"Move <app> here"</span></span>
* <span data-ttu-id="2a0df-154">"Bild nehmen"</span><span class="sxs-lookup"><span data-stu-id="2a0df-154">"Take a picture"</span></span>
* <span data-ttu-id="2a0df-155">"Aufzeichnung starten"</span><span class="sxs-lookup"><span data-stu-id="2a0df-155">"Start recording"</span></span>
* <span data-ttu-id="2a0df-156">"Aufzeichnung anhalten"</span><span class="sxs-lookup"><span data-stu-id="2a0df-156">"Stop recording"</span></span>
* <span data-ttu-id="2a0df-157">"Hand Strahl anzeigen"</span><span class="sxs-lookup"><span data-stu-id="2a0df-157">"Show hand ray"</span></span>
* <span data-ttu-id="2a0df-158">"Hand Strahl ausblenden"</span><span class="sxs-lookup"><span data-stu-id="2a0df-158">"Hide hand ray"</span></span>
* <span data-ttu-id="2a0df-159">"Erhöhen der Helligkeit"</span><span class="sxs-lookup"><span data-stu-id="2a0df-159">"Increase the brightness"</span></span>
* <span data-ttu-id="2a0df-160">"Die Helligkeit verringern"</span><span class="sxs-lookup"><span data-stu-id="2a0df-160">"Decrease the brightness"</span></span>
* <span data-ttu-id="2a0df-161">"Volume vergrößern"</span><span class="sxs-lookup"><span data-stu-id="2a0df-161">"Increase the volume"</span></span>
* <span data-ttu-id="2a0df-162">"Volume verkleinern"</span><span class="sxs-lookup"><span data-stu-id="2a0df-162">"Decrease the volume"</span></span>
* <span data-ttu-id="2a0df-163">"Stumm schalten" oder "unstumm schalten"</span><span class="sxs-lookup"><span data-stu-id="2a0df-163">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="2a0df-164">"Gerät Herunterfahren"</span><span class="sxs-lookup"><span data-stu-id="2a0df-164">"Shut down the device"</span></span>
* <span data-ttu-id="2a0df-165">"Gerät neu starten"</span><span class="sxs-lookup"><span data-stu-id="2a0df-165">"Restart the device"</span></span>
* <span data-ttu-id="2a0df-166">"Gehe zu Standbymodus"</span><span class="sxs-lookup"><span data-stu-id="2a0df-166">"Go to sleep"</span></span>
* <span data-ttu-id="2a0df-167">"Welche Zeit ist es?"</span><span class="sxs-lookup"><span data-stu-id="2a0df-167">"What time is it?"</span></span>
* <span data-ttu-id="2a0df-168">"Wie viel Akku habe ich verbleiben?"</span><span class="sxs-lookup"><span data-stu-id="2a0df-168">"How much battery do I have left?"</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="2a0df-169">"Weitere Informationen"</span><span class="sxs-lookup"><span data-stu-id="2a0df-169">"See It, Say It"</span></span><br>
        <span data-ttu-id="2a0df-170">Hololens hat eine "See it"-Modell für die Spracheingabe, bei der Bezeichnungen auf Schaltflächen den Benutzern mitteilen, welche Sprachbefehle Sie auch sagen können.</span><span class="sxs-lookup"><span data-stu-id="2a0df-170">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="2a0df-171">Wenn Sie z. b. ein App-Fenster in hololens (1st Gen) betrachten, kann ein Benutzer den Befehl "anpassen" festlegen, um die Position der APP auf der Welt anzupassen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-171">For example, when looking at an app window in HoloLens (1st gen), a user can say "Adjust" command to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="2a0df-172">*Image: ein Benutzer kann den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP anzupassen.*</span><span class="sxs-lookup"><span data-stu-id="2a0df-172">*Image: A user can say the "Adjust" command, which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="2a0df-173">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="2a0df-173">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="2a0df-174">![Wenn Sie ein App-Fenster oder Hologram betrachten, kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der ganzen Welt anzupassen.](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="2a0df-174">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="2a0df-175">Wenn apps diese Regel befolgen, können Benutzer leicht erkennen, was zum Steuern des Systems zu sagen ist.</span><span class="sxs-lookup"><span data-stu-id="2a0df-175">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="2a0df-176">Wenn Sie auf einer Schaltfläche in hololens (1st Gen) suchen, sehen Sie eine QuickInfo, die nach einer Sekunde angezeigt wird, wenn die Schaltfläche sprach fähig ist, und zeigt den Befehl an, um zu sprechen, um Sie zu "drücken".</span><span class="sxs-lookup"><span data-stu-id="2a0df-176">While gazing at a button in HoloLens (1st gen), you'll see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="2a0df-177">Um voicemailtipps in hololens 2 anzuzeigen, zeigen Sie den sprach Cursor an, indem Sie "Select" oder "Was kann ich sagen" (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="2a0df-177">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="2a0df-178">*Bild: "sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.*</span><span class="sxs-lookup"><span data-stu-id="2a0df-178">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="2a0df-180">Sprachbefehle für schnelle – Hologramm-Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="2a0df-180">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="2a0df-181">Es gibt viele Sprachbefehle, die Sie bei der Betrachtung bei einem – Hologramm zum schnellen Ausführen von Bearbeitungsaufgaben durchführen können.</span><span class="sxs-lookup"><span data-stu-id="2a0df-181">There are many voice commands you can say while gazing at a hologram to quickly do manipulation tasks.</span></span> <span data-ttu-id="2a0df-182">Diese Sprachbefehle funktionieren für APP-Windows-und 3D-Objekte, die Sie in der Welt abgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="2a0df-182">These voice commands work on app windows and 3D objects you've placed in the world.</span></span>

<span data-ttu-id="2a0df-183">**Hologram-Bearbeitungsbefehle**</span><span class="sxs-lookup"><span data-stu-id="2a0df-183">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="2a0df-184">Gesicht</span><span class="sxs-lookup"><span data-stu-id="2a0df-184">Face me</span></span>
* <span data-ttu-id="2a0df-185">Größer | Verbessern</span><span class="sxs-lookup"><span data-stu-id="2a0df-185">Bigger | Enhance</span></span>
* <span data-ttu-id="2a0df-186">Geringeren</span><span class="sxs-lookup"><span data-stu-id="2a0df-186">Smaller</span></span>

<span data-ttu-id="2a0df-187">Auf hololens 2 können Sie auch natürlichere Interaktionen in Kombination mit Eye-Blick erstellen, die implizit Kontextinformationen über das, auf das Sie verweisen, bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="2a0df-187">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze, which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="2a0df-188">Beispielsweise könnten Sie ein Hologramm betrachten und "put this" ( _diese_) und _dann überprüfen_, wo Sie es platzieren möchten.</span><span class="sxs-lookup"><span data-stu-id="2a0df-188">For example, you could look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="2a0df-189">Oder Sie können sich einen Holographic-Teil auf einem komplexen Computer ansehen und sagen: "Weitere Informationen zu _diesem_".</span><span class="sxs-lookup"><span data-stu-id="2a0df-189">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>

## <a name="discovering-voice-commands"></a><span data-ttu-id="2a0df-190">Erkennen von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="2a0df-190">Discovering voice commands</span></span>

<span data-ttu-id="2a0df-191">Einige Befehle, wie z. b. die Befehle für die schnelle Bearbeitung, können ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-191">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="2a0df-192">Um zu erfahren, welche Befehle Sie verwenden können, schauen Sie sich das Objekt an, und sagen Sie: "Was kann ich sagen?".</span><span class="sxs-lookup"><span data-stu-id="2a0df-192">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="2a0df-193">Eine Liste möglicher Befehle wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2a0df-193">A list of possible commands pops up.</span></span> <span data-ttu-id="2a0df-194">Sie können auch den Cursor Cursor verwenden, um die voicemailtipps für die einzelnen Schaltflächen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-194">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="2a0df-195">Wenn Sie eine vollständige Liste erhalten möchten, sagen Sie einfach "alle Befehle anzeigen".</span><span class="sxs-lookup"><span data-stu-id="2a0df-195">If you want a complete list, just say, "Show all commands" anytime.</span></span> 

## <a name="dictation"></a><span data-ttu-id="2a0df-196">Diktieren</span><span class="sxs-lookup"><span data-stu-id="2a0df-196">Dictation</span></span>

<span data-ttu-id="2a0df-197">Anstatt eine Typisierung mit [Luft](gaze-and-commit.md#composite-gestures)Eingaben durchführen zu können, kann es effizienter sein, Text in eine APP einzugeben.</span><span class="sxs-lookup"><span data-stu-id="2a0df-197">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="2a0df-198">Dadurch kann die Eingabe erheblich beschleunigt werden, sodass der Benutzer weniger Aufwand hat.</span><span class="sxs-lookup"><span data-stu-id="2a0df-198">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="2a0df-199">![Sprach Diktat beginnt mit der Schaltfläche Mikrofon](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="2a0df-199">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="2a0df-200">*Sprach Diktat beginnt mit der Schaltfläche Mikrofon auf der Tastatur*</span><span class="sxs-lookup"><span data-stu-id="2a0df-200">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="2a0df-201">Jedes Mal, wenn die holografische Tastatur aktiv ist, können Sie in den Diktat Modus wechseln, anstatt einzugeben.</span><span class="sxs-lookup"><span data-stu-id="2a0df-201">Anytime the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="2a0df-202">Wählen Sie das Mikrofon auf der Seite des Texteingabe Felds aus, um loszulegen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-202">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="2a0df-203">Hinzufügen von Sprachbefehlen zu Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="2a0df-203">Adding voice commands to your app</span></span>

<span data-ttu-id="2a0df-204">Erwägen Sie, Sprachbefehle zu jeder von Ihnen erstellten Umgebung hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-204">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="2a0df-205">Voice ist eine leistungsstarke Möglichkeit, das System und die apps zu steuern.</span><span class="sxs-lookup"><span data-stu-id="2a0df-205">Voice is a powerful way control the system and apps.</span></span> <span data-ttu-id="2a0df-206">Da Benutzer mit unterschiedlichen Arten von Dialekten und Akzenten sprechen, stellen Sie sicher, dass die Befehle Ihrer Benutzer eindeutig interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-206">Because users speak with different kinds of dialects and accents, proper choice of speech keywords will make sure your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="2a0df-207">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="2a0df-207">Best practices</span></span>

<span data-ttu-id="2a0df-208">Nachfolgend finden Sie einige Methoden aufgeführt, die eine reibungslose Spracherkennung ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-208">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="2a0df-209">**Präzise Befehle verwenden**: Wählen Sie nach Möglichkeit Schlüsselwörter mit zwei oder mehr Silben aus.</span><span class="sxs-lookup"><span data-stu-id="2a0df-209">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="2a0df-210">Einsilbige Wörter neigen dazu, unterschiedliche Vokallaute zu verwenden, wenn sie von Personen mit unterschiedlichen Akzenten gesprochen werden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-210">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="2a0df-211">Beispiel: "Video abspielen" ist besser als "das aktuell ausgewählte Video abspielen"</span><span class="sxs-lookup"><span data-stu-id="2a0df-211">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="2a0df-212">**Verwenden eines einfachen Vokabulars** -Beispiel: "Show Note" ist besser als "Placard anzeigen"</span><span class="sxs-lookup"><span data-stu-id="2a0df-212">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="2a0df-213">Stellen **Sie sicher, dass Befehle nicht destruktiv sind** . Stellen Sie sicher, dass alle sprach Befehls Aktionen nicht destruktiv sind und leicht rückgängig gemacht werden können, wenn eine andere Person, die in der Nähe des Benutzers steht, versehentlich einen Befehl auslöst</span><span class="sxs-lookup"><span data-stu-id="2a0df-213">**Make sure commands are non-destructive** - Make sure any speech command actions are non-destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="2a0df-214">**Vermeiden Sie ähnliche, klingende Befehle** : vermeiden Sie das Registrieren mehrerer Sprachbefehle, die ähnlich klingen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-214">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound similar.</span></span> <span data-ttu-id="2a0df-215">Beispiel: "mehr anzeigen" und "Store anzeigen" kann ähnlich klingen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-215">Example: "Show more" and "Show store" can be similar sounding.</span></span>
* <span data-ttu-id="2a0df-216">Aufheben der Registrierung **Ihrer APP, wenn Sie nicht verwendet** wird: Wenn sich Ihre APP nicht in einem Zustand befindet, in dem ein bestimmter Sprachbefehl gültig ist, sollten Sie die Registrierung aufheben, damit andere Befehle nicht verwechselt werden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-216">**Unregister your app when not it uses** - When your app isn't in a state in which a particular speech command is valid, consider unregistering it so that other commands aren't confused for that one.</span></span>
* <span data-ttu-id="2a0df-217">**Mit verschiedenen Akzenten testen**: Testen Sie Ihre App mit Benutzern, die unterschiedliche Akzente verwenden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-217">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="2a0df-218">**Konsistenz von Sprachbefehlen beibehalten**: Wenn „Zurück“ zur vorherigen Seite wechselt, übernehmen Sie dieses Verhalten in Ihren Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-218">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="2a0df-219">**Vermeiden Sie die Verwendung von System Befehlen** . die folgenden Sprachbefehle sind für das System reserviert. vermeiden Sie daher die Verwendung in Ihren Anwendungen:</span><span class="sxs-lookup"><span data-stu-id="2a0df-219">**Avoid using system commands** - The following voice commands are reserved for the system, so avoid using them in your applications:</span></span>
   * <span data-ttu-id="2a0df-220">„Hey Cortana“</span><span class="sxs-lookup"><span data-stu-id="2a0df-220">"Hey Cortana"</span></span>
   * <span data-ttu-id="2a0df-221">„Auswählen“</span><span class="sxs-lookup"><span data-stu-id="2a0df-221">"Select"</span></span>
   * <span data-ttu-id="2a0df-222">"Gehe zu Start"</span><span class="sxs-lookup"><span data-stu-id="2a0df-222">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="2a0df-223">Vorteile von Spracheingaben</span><span class="sxs-lookup"><span data-stu-id="2a0df-223">Advantages of voice input</span></span>

<span data-ttu-id="2a0df-224">Die Spracheingabe ist eine natürliche Art, unsere Absichten zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="2a0df-224">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="2a0df-225">Voice ist besonders gut für Schnittstellen **Traversale** geeignet, da es Benutzern helfen kann, mehrere Schritte einer Schnittstelle zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-225">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface.</span></span> <span data-ttu-id="2a0df-226">Ein Benutzer könnte bei der Betrachtung einer Webseite auf "zurückkehren" zurückgreifen, anstatt in der APP auf die Schaltfläche "zurück" zu klicken.</span><span class="sxs-lookup"><span data-stu-id="2a0df-226">A user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app.</span></span> <span data-ttu-id="2a0df-227">Diese kleine Zeitersparnis wirkt sich **negativ** auf die Wahrnehmung der Benutzerfreundlichkeit durch den Benutzer aus und bietet Ihnen einen kleinen Wert für die Super Arbeit.</span><span class="sxs-lookup"><span data-stu-id="2a0df-227">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="2a0df-228">Die Spracheingabe ist auch eine bequeme Eingabemethode, wenn unsere Arme nicht frei sind oder wir **mehrere Aufgaben gleichzeitig** erledigen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-228">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="2a0df-229">Auf Geräten, auf denen die Eingabe auf einer Tastatur schwierig ist, kann die **sprach Diktat** -Methode eine effiziente Alternative zum Eingeben von Text sein.</span><span class="sxs-lookup"><span data-stu-id="2a0df-229">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="2a0df-230">In einigen Fällen, in denen der **Genauigkeits Bereich** für den Blick und die Bewegung eingeschränkt ist, kann Voice Ihnen helfen, die Absicht des Benutzers zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-230">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="2a0df-231">**Vorteile der Spracheingabe für den Benutzer**</span><span class="sxs-lookup"><span data-stu-id="2a0df-231">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="2a0df-232">Verkürzt den Zeitaufwand – das Endziel sollte effizienter erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-232">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="2a0df-233">Minimiert den Aufwand – Aufgaben sollten flüssiger und müheloser verlaufen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-233">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="2a0df-234">Reduziert die kognitive Belastung – sie ist intuitiv, leicht zu erlernen und zu merken.</span><span class="sxs-lookup"><span data-stu-id="2a0df-234">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="2a0df-235">Er ist gesellschaftlich akzeptabel und sollte mit den gesellschaftlichen Verhaltensnormen kompatibel sein.</span><span class="sxs-lookup"><span data-stu-id="2a0df-235">It's socially acceptable - it should fit in with societal norms of behavior.</span></span>
* <span data-ttu-id="2a0df-236">Sie stellt eine Routine dar – die Spracheingabe kann leicht zu einem gewohnheitsmäßigen Verhalten werden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-236">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="2a0df-237">Herausforderungen bei der Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="2a0df-237">Challenges for voice input</span></span>

<span data-ttu-id="2a0df-238">Obwohl die Spracheingabe für viele verschiedene Anwendungen großartig ist, stellt Sie auch mehrere Herausforderungen dar.</span><span class="sxs-lookup"><span data-stu-id="2a0df-238">While voice input is great for many different applications, it also faces several challenges.</span></span> <span data-ttu-id="2a0df-239">Wenn Sie sowohl die Vorteile als auch die Herausforderungen von Spracheingaben verstanden haben, können App-Entwickler intelligentere Entscheidungen treffen, wie und wann Spracheingaben verwendet werden sollen und wie Sie Ihre Benutzer gut gestalten können.</span><span class="sxs-lookup"><span data-stu-id="2a0df-239">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="2a0df-240">**Spracheingabe für kontinuierliches Eingabe Steuer** Element Eine differenzierte Steuerung ist eine davon.</span><span class="sxs-lookup"><span data-stu-id="2a0df-240">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="2a0df-241">Beispielsweise kann ein Benutzer sein Volume in der Musik-App ändern.</span><span class="sxs-lookup"><span data-stu-id="2a0df-241">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="2a0df-242">Sie kann "lauter" sagen, aber es ist nicht klar, wie viel lauter das System das Volume machen soll.</span><span class="sxs-lookup"><span data-stu-id="2a0df-242">She can say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="2a0df-243">Der Benutzer könnte sagen: "machen Sie es etwas lauter", aber "ein wenig" ist schwierig zu quantifizieren.</span><span class="sxs-lookup"><span data-stu-id="2a0df-243">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="2a0df-244">Das Verschieben oder Skalieren von holograms mit Stimme ist ähnlich schwierig.</span><span class="sxs-lookup"><span data-stu-id="2a0df-244">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="2a0df-245">**Zuverlässigkeit der Spracheingabe Erkennung** Obwohl Spracheingabe Systeme besser und besser werden, werden Sie möglicherweise fälschlicherweise einen Sprachbefehl hören und interpretieren.</span><span class="sxs-lookup"><span data-stu-id="2a0df-245">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="2a0df-246">Der Schlüssel besteht darin, die Herausforderung in Ihrer Anwendung zu beheben.</span><span class="sxs-lookup"><span data-stu-id="2a0df-246">The key is to address the challenge in your application.</span></span> <span data-ttu-id="2a0df-247">Geben Sie Ihren Benutzern Feedback, wenn das System lauscht, und das, was das System verstanden hat, um potenzielle Probleme zu verdeutlichen, die die Benutzersprache verstehen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-247">Provide feedback to your users when the system is listening and what the system understood clarifies potential issues understanding the users' speech.</span></span>  

<span data-ttu-id="2a0df-248">**Spracheingabe in freigegebenen Leerzeichen** Die Stimme ist möglicherweise nicht in den Bereichen, die Sie für andere Personen freigeben, akzeptabel.</span><span class="sxs-lookup"><span data-stu-id="2a0df-248">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="2a0df-249">Hier sind einige Beispiele:</span><span class="sxs-lookup"><span data-stu-id="2a0df-249">Here are a few examples:</span></span>
* <span data-ttu-id="2a0df-250">Der Benutzer möchte möglicherweise keine anderen Benutzer stören (z. b. in einer stillen Bibliothek oder einem freigegebenen Büro).</span><span class="sxs-lookup"><span data-stu-id="2a0df-250">The user may not want to disturb others (for example, in a quiet library or shared office)</span></span>
* <span data-ttu-id="2a0df-251">Benutzer sind vielleicht nicht in der Öffentlichkeit,</span><span class="sxs-lookup"><span data-stu-id="2a0df-251">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="2a0df-252">Ein Benutzer ist möglicherweise unbequem, wenn er eine persönliche oder vertrauliche Nachricht (einschließlich Kenn Wörtern) einhört, während andere Benutzer lauschen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-252">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="2a0df-253">**Spracheingabe von eindeutigen oder unbekannten Wörtern** Probleme bei der Spracheingabe werden auch angezeigt, wenn Benutzer Wörter diktieren, die dem System möglicherweise unbekannt sind, wie z. b. Spitznamen, bestimmte Textmarken oder Abkürzungen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-253">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words, or abbreviations.</span></span> 

<span data-ttu-id="2a0df-254">**Erlernen von Sprachbefehlen** Das ultimative Ziel ist es, sich auf natürliche Weise mit Ihrem System zu Konversation, aber häufig basieren apps auf bestimmten vordefinierten Sprachbefehlen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-254">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="2a0df-255">Eine Herausforderung, die mit einem großen Satz von Sprachbefehlen verknüpft ist, besteht darin, Sie zu unterstützen, ohne den Benutzer zu überlasten und den Benutzer zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-255">A challenge associated with a significant set of voice commands is how to teach them without overloading the user and how to help the user to keep them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="2a0df-256">Statusangaben für Spracherkennungsfeedback</span><span class="sxs-lookup"><span data-stu-id="2a0df-256">Voice feedback states</span></span>

<span data-ttu-id="2a0df-257">Wenn die Spracherkennung richtig angewendet wird, versteht der Benutzer, **was er sagen kann und er erhält ein eindeutiges Feedback**, das das System **ihn richtig verstanden hat**.</span><span class="sxs-lookup"><span data-stu-id="2a0df-257">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="2a0df-258">Diese beiden Signale geben dem Benutzer das Gefühl, dass er die Spracherkennung als primäre Eingabemethode verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="2a0df-258">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="2a0df-259">Nachfolgend ist in einem Diagramm dargestellt, was mit dem Cursor geschieht, wenn die Spracheingabe erkannt wird und wie dies dem Benutzer vermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="2a0df-259">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="2a0df-260">![1. regulärer Cursor Zustand](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="2a0df-260">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="2a0df-261">**1. regulärer Cursor Zustand**</span><span class="sxs-lookup"><span data-stu-id="2a0df-261">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2a0df-262">![2. kommuniziert Feedback und verschwindet dann](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="2a0df-262">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="2a0df-263">**2. kommuniziert Feedback und verschwindet dann**</span><span class="sxs-lookup"><span data-stu-id="2a0df-263">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2a0df-264">![€.</span><span class="sxs-lookup"><span data-stu-id="2a0df-264">![\*3.</span></span> <span data-ttu-id="2a0df-265">Regulärer Cursor Zustand](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="2a0df-265">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="2a0df-266">**3. zurück zum regulären Cursor Zustand**</span><span class="sxs-lookup"><span data-stu-id="2a0df-266">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="2a0df-267">Wichtige Informationen zur Spracherkennung in Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2a0df-267">Top things users should know about "speech" in mixed reality</span></span>

* <span data-ttu-id="2a0df-268">Sagen Sie **"Select"** , während Sie auf eine Schaltfläche abzielen. (Sie können hier eine Schaltfläche verwenden.)</span><span class="sxs-lookup"><span data-stu-id="2a0df-268">Say **"Select"** while targeting a button (you can use this anywhere to select a button).</span></span>
* <span data-ttu-id="2a0df-269">Sie können in einigen Apps den **Bezeichnungsnamen einer Schaltfläche auf der App-Leiste** sagen, um eine Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-269">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="2a0df-270">Beispielsweise kann ein Benutzer bei der Betrachtung einer APP den Befehl "Remove" (entfernen) aufrufen, um die APP aus der Welt zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-270">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to select it with your hand).</span></span>
* <span data-ttu-id="2a0df-271">Sie können Cortana starten, indem Sie **"Hey Cortana" sagen.**</span><span class="sxs-lookup"><span data-stu-id="2a0df-271">You can start Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="2a0df-272">Sie können ihr Fragen stellen („Hey Cortana, wie hoch ist der Eiffelturm“), sie zum Öffnen einer App auffordern („Hey Cortana, öffne Netflix“) oder ihr sagen, sie soll das Startmenü aufrufen („Hey Cortana, öffne das Startmenü“) und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="2a0df-272">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="2a0df-273">Häufig gestellte Fragen und Bedenken von Benutzern zur Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="2a0df-273">Common questions and concerns users have about voice</span></span>

* <span data-ttu-id="2a0df-274">Was kann ich sagen?</span><span class="sxs-lookup"><span data-stu-id="2a0df-274">What can I say?</span></span>
* <span data-ttu-id="2a0df-275">Woher weiß ich, ob das System mich richtig verstanden hat?</span><span class="sxs-lookup"><span data-stu-id="2a0df-275">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="2a0df-276">Das System versteht meine Sprachbefehle immer wieder falsch.</span><span class="sxs-lookup"><span data-stu-id="2a0df-276">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="2a0df-277">Es reagiert nicht, wenn ich einen Sprachbefehl erteile.</span><span class="sxs-lookup"><span data-stu-id="2a0df-277">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="2a0df-278">Es reagiert falsch, wenn ich einen Sprachbefehl erteile.</span><span class="sxs-lookup"><span data-stu-id="2a0df-278">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="2a0df-279">Wie richte ich meine Stimme auf eine bestimmte App oder einen bestimmten App-Befehl aus?</span><span class="sxs-lookup"><span data-stu-id="2a0df-279">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="2a0df-280">Kann ich Objekte per Sprachbefehl aus dem holografischen Rahmen der HoloLens bewegen?</span><span class="sxs-lookup"><span data-stu-id="2a0df-280">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="2a0df-281">Kommunikation</span><span class="sxs-lookup"><span data-stu-id="2a0df-281">Communication</span></span>

<span data-ttu-id="2a0df-282">Für Anwendungen, die die von hololens bereitgestellten angepassten audioeingabeverarbeitungs-Optionen nutzen möchten, ist es wichtig, die verschiedenen [audiostreamkategorien](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) zu verstehen, die Ihre APP nutzen kann.</span><span class="sxs-lookup"><span data-stu-id="2a0df-282">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it's important to understand the various [audio stream categories](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) your app can consume.</span></span> <span data-ttu-id="2a0df-283">Windows 10 unterstützt mehrere verschiedene streamingkategorien, und hololens nutzt drei dieser Möglichkeiten, um die benutzerdefinierte Verarbeitung zur Optimierung der Mikrofon Audioqualität zu optimieren, die auf Sprache, Kommunikation und andere zugeschnitten ist. diese kann für Umgebungs Umgebungs-audioerfassungs Szenarien (d.h. "Camcorder") verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-283">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication, and other, which can be used for ambient environment audio capture (that is, "camcorder") scenarios.</span></span>
* <span data-ttu-id="2a0df-284">Die AudioCategory_Communications Stream-Kategorie ist für die Sprach-und Erzähl Szenarios angepasst und stellt dem Client einen 16-Bit-Mono-Mono-Audiodatenstrom des Benutzers zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="2a0df-284">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16-kHz 24-bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="2a0df-285">Die AudioCategory_Speech Stream-Kategorie ist für die Sprach-Engine hololens (Windows) angepasst und stellt einen 16-Bit-Mono-Mono-Datenstrom der Stimme des Benutzers bereit.</span><span class="sxs-lookup"><span data-stu-id="2a0df-285">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16-kHz 24-bit mono stream of the user's voice.</span></span> <span data-ttu-id="2a0df-286">Diese Kategorie kann bei Bedarf von Sprachmodulen von Drittanbietern verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2a0df-286">This category can be used by third-party speech engines if needed.</span></span>
* <span data-ttu-id="2a0df-287">Die AudioCategory_Other Stream-Kategorie ist für die Audioaufzeichnung der Umgebungsumgebung angepasst und stellt dem Client einen 48-Bit-Stereo Audiodatenstrom mit einer Größe von-Bit bereit.</span><span class="sxs-lookup"><span data-stu-id="2a0df-287">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48-kHz 24-bit stereo audio stream.</span></span>

<span data-ttu-id="2a0df-288">Die gesamte Audioverarbeitung ist Hardware beschleunigt. Dies bedeutet, dass die Features viel weniger Leistung als bei der Verarbeitung der hololens-CPU benötigen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-288">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="2a0df-289">Vermeiden Sie die Ausführung einer anderen audioeingabeverarbeitung auf der CPU, um die Akku Lebensdauer zu maximieren und die integrierte, offloaded audioeingabeverarbeitung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-289">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built-in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="2a0df-290">Sprachen</span><span class="sxs-lookup"><span data-stu-id="2a0df-290">Languages</span></span>

<span data-ttu-id="2a0df-291">Hololens 2 [unterstützt mehrere Sprachen](/hololens/hololens2-language-support).</span><span class="sxs-lookup"><span data-stu-id="2a0df-291">HoloLens 2 [supports multiple languages](/hololens/hololens2-language-support).</span></span> <span data-ttu-id="2a0df-292">Beachten Sie, dass Sprachbefehle immer in der Anzeige Sprache des Systems ausgeführt werden, auch wenn mehrere Tastaturen installiert sind oder wenn apps versuchen, eine Spracherkennung in einer anderen Sprache zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-292">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="2a0df-293">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="2a0df-293">Troubleshooting</span></span>

<span data-ttu-id="2a0df-294">Wenn Sie Probleme bei der Verwendung von "Select" und "Hey Cortana" haben, versuchen Sie, zu einem ruhigeren Bereich zu wechseln, die Ursache für Rauschen zu machen oder lauter zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-294">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="2a0df-295">Zu diesem Zeitpunkt wird die Spracherkennung in hololens speziell für systemeigene Sprecher von USA Englisch optimiert und optimiert.</span><span class="sxs-lookup"><span data-stu-id="2a0df-295">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="2a0df-296">Für Windows Mixed Reality Developer Edition, Version 2017, funktioniert die audioendpunkt-Verwaltungs Logik problemlos (immer), nachdem Sie sich nach der anfänglichen HMD-Verbindung beim PC-Desktop abgemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="2a0df-296">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="2a0df-297">Vor dem ersten Abmelden/in-Ereignis nach dem Durchlaufen von WMR OOBE könnte der Benutzer verschiedene Probleme mit der Audiofunktionalität aufweisen, von denen kein audiowechsel bis hin zu keinem audiowechsel stattfindet, je nachdem, wie das System eingerichtet wurde, bevor die HMD zum ersten Mal eine Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="2a0df-297">Before that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up before connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="2a0df-298">Spracheingabe in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="2a0df-298">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="2a0df-299">Mit **[mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie den Voice-Befehl problemlos für beliebige Objekte zuweisen.</span><span class="sxs-lookup"><span data-stu-id="2a0df-299">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="2a0df-300">Verwenden Sie das **Spracheingabe Profil** von mrtk, um Ihre Schlüsselwörter zu definieren.</span><span class="sxs-lookup"><span data-stu-id="2a0df-300">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="2a0df-301">Indem Sie das Skript " **speechinputhandler** " zuweisen, können Sie festlegen, dass jedes Objekt auf die im Spracheingabe Profil definierten Schlüsselwörter antwortet.</span><span class="sxs-lookup"><span data-stu-id="2a0df-301">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="2a0df-302">Der speechinputhandler bietet auch eine Bezeichnung für die sprach Bestätigung, um das Vertrauen des Benutzers zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="2a0df-302">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="2a0df-303">Befehl "mrtk-Voice"</span><span class="sxs-lookup"><span data-stu-id="2a0df-303">MRTK - Voice command</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/speech.md)

---

## <a name="see-also"></a><span data-ttu-id="2a0df-304">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2a0df-304">See also</span></span>

* [<span data-ttu-id="2a0df-305">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="2a0df-305">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="2a0df-306">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="2a0df-306">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="2a0df-307">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="2a0df-307">Voice input in DirectX</span></span>](../develop/native/voice-input-in-directx.md)
* [<span data-ttu-id="2a0df-308">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="2a0df-308">Voice input in Unity</span></span>](../develop/unity/voice-input-in-unity.md)