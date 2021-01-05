---
title: Entwerfen von Hologrammen
description: Erfahren Sie mehr über die gemischte Realität durch die neue Anwendung zum Entwickeln von holograms von Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: Mrtk, Mixed Reality Toolkit, holograms, Entwerfen von holograms, erlernen, Beispiel-APP, Mixed Reality-Headset, Virtual Reality-Headset, was ist Virtual Reality?
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757758"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="6cee4-104">Das Entwerfen von holograms</span><span class="sxs-lookup"><span data-stu-id="6cee4-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="6cee4-105">Gestatten Sie einem kleinen lade Fenster, alle coolen GIFs und eingebetteten Videos auf dieser Seite zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="6cee4-106">Das Erlernen des Entwurfs für gemischte Realität kann schwierig sein, da das Medium nicht immer gut in 2D-Entwurfs Prozesse übersetzt.</span><span class="sxs-lookup"><span data-stu-id="6cee4-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="6cee4-107">Wir haben hier bei Microsoft eine kostenlose App für die hololens 2 erstellt, um Ihnen das Erlernen der Grundlagen von Mixed Reality UX-Entwurf zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="6cee4-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="6cee4-108">Der einzigartige Ansatz der APP zum Entwerfen von holograms ist in gemischtes Realitäts Verhalten, Tipps und Empfehlungen integriert, um Ihnen die Erstellung ansprechender und verblüffender hololens-apps zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="6cee4-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="6cee4-109">Laden Sie die App kostenlos von der Microsoft Store herunter, und lernen Sie von dem Mixed Reality-Design Team von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6cee4-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6cee4-110">Herunterladen der APP zum Entwerfen von holograms</span><span class="sxs-lookup"><span data-stu-id="6cee4-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![Animiertes GIF der Head Tracking-Szene im Demoraum des Entwurfs holograms](images/designing-holograms/demo-room.gif)

<span data-ttu-id="6cee4-112">*Entwerfen von Hologram als Demoraum (auch als "Puppenhaus" bezeichnet)*</span><span class="sxs-lookup"><span data-stu-id="6cee4-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="6cee4-113">Entwerfen für gemischte Realität</span><span class="sxs-lookup"><span data-stu-id="6cee4-113">Designing for mixed reality</span></span>

<span data-ttu-id="6cee4-114">Wie viele von Ihnen habe ich zum Entwerfen mobiler Apps verwendet.</span><span class="sxs-lookup"><span data-stu-id="6cee4-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="6cee4-115">Aus einer 2D-Entwurfs Welt, die sich vollständig bei räumlichen Computing, wo alles heute auf der Welt ist, befindet, war es eine bedeutende Umstellung.</span><span class="sxs-lookup"><span data-stu-id="6cee4-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="6cee4-116">In gemischter Realität sind apps nicht mehr auf einen 2D-Bildschirm beschränkt. Tatsächlich sind Sie fast kostenlos, werden in der realen Welt platziert und interagieren mit echten Objekten.</span><span class="sxs-lookup"><span data-stu-id="6cee4-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="6cee4-117">Für mich ist das Verbinden von 3D-Erfahrungen mit konventionellen 2D-Entwurfs Prozessen der anspruchsvollste Aspekt der Mixed Reality-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="6cee4-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="6cee4-118">In Konversationen mit Kunden würde ich Folgendes hören: "Ich weiß, welche Features eingeschlossen werden müssen und wie Sie Sie einrichten und ausführen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="6cee4-119">Es handelt sich um Code, ich kann die Dokumentation und Lernprogramme, aber die Benutzer Darstellung befolgen?</span><span class="sxs-lookup"><span data-stu-id="6cee4-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="6cee4-120">Viele Features, verschiedene Eingabeoptionen, verschiedene Szenarien und physische Umgebungen sind überwältigend.</span><span class="sxs-lookup"><span data-stu-id="6cee4-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="6cee4-121">![Bild aus dem Design Workshop hololens 2 im San Francisco- ](images/designing-holograms/workshop.jpeg)
 *Image aus dem hololens 2-Entwurfs Workshop in San Francisco*</span><span class="sxs-lookup"><span data-stu-id="6cee4-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="6cee4-122">Eine Gelegenheit zum vermitteln</span><span class="sxs-lookup"><span data-stu-id="6cee4-122">An opportunity to teach</span></span>

<span data-ttu-id="6cee4-123">Zuerst war es nicht offensichtlich, aber es wurde eine hervorragende Gelegenheit geboten, gemischte Realität als Mittel zu verwenden, um es zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="6cee4-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="6cee4-124">Das Entwerfen von holograms ist eine visuelle Darstellung, in der gemischte Entwurfskonzepte und-Empfehlungen erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="6cee4-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="6cee4-125">Es handelt sich lediglich um einen virtuellen Lehrer, der gemischte Realitäts Entwurfskonzepte demonstriert.</span><span class="sxs-lookup"><span data-stu-id="6cee4-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="6cee4-126">Alles ist von einer dritten Person, die die benutzerfreundliche Darstellung in Ihrem eigenen Bereich hat.</span><span class="sxs-lookup"><span data-stu-id="6cee4-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="6cee4-127">*Entwerfen von holograms-Nachspann Videos*</span><span class="sxs-lookup"><span data-stu-id="6cee4-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="6cee4-128">Erkunden des Puppenhauses</span><span class="sxs-lookup"><span data-stu-id="6cee4-128">Exploring the doll house</span></span>

<span data-ttu-id="6cee4-129">Das Puppenhaus ist die virtuelle Umgebung, die in der gesamten App verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6cee4-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="6cee4-130">Bei der Umgebung handelt es sich um einen 80 x 60 x 40-cm-Miniatur Raum, der die grundlegenden Elemente enthält, die die meisten Räume gemeinsam haben, wie z. b. Wände, Lampen, Möbel, eine Tabelle und ein TV.</span><span class="sxs-lookup"><span data-stu-id="6cee4-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="6cee4-131">Das Puppenhaus ist der Hauptprotagonist der APP-Umgebung, daher mussten wir sicherstellen, dass es in jeder Umgebung gut funktioniert.</span><span class="sxs-lookup"><span data-stu-id="6cee4-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="6cee4-132">Sehen Sie sich dies als kleinen Demo Raum an, in dem Sie alle Arten gemischter Realitäts Konzepte visualisieren.</span><span class="sxs-lookup"><span data-stu-id="6cee4-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="6cee4-133">*Video zum Anpassungs Verhalten von Dollhouse*</span><span class="sxs-lookup"><span data-stu-id="6cee4-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="6cee4-134">1:1 vs 1:10-Prototypen</span><span class="sxs-lookup"><span data-stu-id="6cee4-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="6cee4-135">Unsere anfängliche Annahme war, dass 1:1 Demonstrationen erstaunlich waren, fast wie man sich einen echten Lehrer ansieht.</span><span class="sxs-lookup"><span data-stu-id="6cee4-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="6cee4-136">Dem Benutzer werden alle Elemente angezeigt, die der Lehrer in einer realen lebensskala sieht.</span><span class="sxs-lookup"><span data-stu-id="6cee4-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="6cee4-137">Wir haben jedoch sofort erkannt, dass es einige Probleme gibt:</span><span class="sxs-lookup"><span data-stu-id="6cee4-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="6cee4-138">Die meisten Entwickler führen Ihre apps in Büros oder Räumen aus, die kleiner sind als der Demoraum, sodass es nicht passt.</span><span class="sxs-lookup"><span data-stu-id="6cee4-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="6cee4-139">Anzeigen sind additiv, was bedeutet, dass die gesamte virtuelle Umgebung über dem Raum eines Benutzers überlagert wird.</span><span class="sxs-lookup"><span data-stu-id="6cee4-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="6cee4-140">Dies kann mit zwei Tabellen verwirrend werden, möglicherweise mit doppelten Couches und Wänden, die nicht ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="6cee4-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="6cee4-141">Und das schlechteste aus einer virtuellen Umgebung, die stark durch ein Sichtfeld eingeschränkt ist.</span><span class="sxs-lookup"><span data-stu-id="6cee4-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="6cee4-142">Als wir eine Mini-1:10-Skala ausprobiert haben, war das Ergebnis eine fantastische Vogelperspektive in einem realistischen Raum.</span><span class="sxs-lookup"><span data-stu-id="6cee4-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="6cee4-143">Sie können alles, was in jedem beliebigen Winkel passiert ist, gleichzeitig sehen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="6cee4-144">Was am offensichtlichsten war, ist, dass die meisten Tester es so viel mehr einsehen, dass Sie eine kleine Version sehen konnten, und dann nie wieder zur 1:1-Skala gewechselt.</span><span class="sxs-lookup"><span data-stu-id="6cee4-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="6cee4-145">Wir haben uns entschieden, die Version 1:1 zu bereinigen und die zusätzliche Arbeit zu vermeiden, die zum Anpassen der Benutzeroberfläche und anderer Aspekte der APP erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="6cee4-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="6cee4-146">![Sichtfeld mit 1:1-Skalierungs ](images/designing-holograms/1-1-scale.png)
 *Feld Ansicht mit 1:1-Skala*</span><span class="sxs-lookup"><span data-stu-id="6cee4-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="6cee4-147">![Sichtfeld mit 1:10-Skalierungs ](images/designing-holograms/1-10-scale.png)
 *Feld Ansicht mit 1:10-Skala*</span><span class="sxs-lookup"><span data-stu-id="6cee4-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="6cee4-148">Verwenden der Mixed Reality-Erfassung</span><span class="sxs-lookup"><span data-stu-id="6cee4-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="6cee4-149">Eines der charakterischsten Features dieser APP ist die Verwendung der gemischten Reality-Erfassung, um gemischte Entwurfskonzepte für die Realität zu vermitteln und zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="6cee4-150">Microsoft verfügt über eine Mixed Reality Capture Studio in San Francisco.</span><span class="sxs-lookup"><span data-stu-id="6cee4-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="6cee4-151">Microsoft lizenziert diese Technologie auch an andere Studio, die eine Avatar-Dimension in Washington D.C., metastage in Los Angeles, Dimensions-Studios in London, SK Telecom in Seoul und volucap in Berlin enthalten.</span><span class="sxs-lookup"><span data-stu-id="6cee4-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="6cee4-152">Weitere Informationen zu unseren [Mixed Reality Capture-Studios](https://www.microsoft.com/mixed-reality/capture-studios)finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="6cee4-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="6cee4-153">*Unformatierte Text Aufnahmen von Daniel Escudero von einer der 106-Kameras im Mixed Reality Capture Studio in San Francisco.*</span><span class="sxs-lookup"><span data-stu-id="6cee4-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="6cee4-154">Der Erfassungsprozess generiert ein keyframed Mesh, Normals und eine Textur, die als obj/PNG-Dateien zur weiteren Nachbereitung bereitgestellt werden können, oder zur Wiedergabe als H. 264-komprimierte MP4-Datei.</span><span class="sxs-lookup"><span data-stu-id="6cee4-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="6cee4-155">Diese Dateien können in Unity-, Unreal-, Native-und webxr-Projekte importiert werden.</span><span class="sxs-lookup"><span data-stu-id="6cee4-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="6cee4-156">Dateien können unter Windows, Ios, Mac, Android, Magic Leap und Play Play VR ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6cee4-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="6cee4-157">*Der Erfassungs Player, der zum Analysieren von MP4 Bitrate bereitgestellt wird, die Videos mit Audiodaten und eingebetteten Meshes enthalten*</span><span class="sxs-lookup"><span data-stu-id="6cee4-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="6cee4-158">Bearbeiten von Erfassungen und virtuellen Objekten</span><span class="sxs-lookup"><span data-stu-id="6cee4-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="6cee4-159">Gemischte Reality-Erfassungen führen zu virtuellen Darstellungen von Personen oder Tieren. Manchmal benötigen Sie diese Zeichen jedoch möglicherweise, um mit anderen virtuellen Objekten zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="6cee4-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="6cee4-160">In den folgenden beiden Beispielen werden verschiedene Möglichkeiten veranschaulicht, wie die Kulissen bearbeitet wurden, um diesen Effekt zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="6cee4-161">Anpassung des Head-Blicks</span><span class="sxs-lookup"><span data-stu-id="6cee4-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="6cee4-162">Durch die Anpassung von headblick können Sie den Kopf einer erfassten Person zur Laufzeit verschieben, was bedeutet, dass Sie für einen Benutzer ein Erfassungs Gesicht haben könnten.</span><span class="sxs-lookup"><span data-stu-id="6cee4-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="6cee4-163">In unserem Fall haben wir Sie verwendet, um das Feld für die Ansicht und das gewünschte Feld anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="6cee4-164">Im folgenden sehen Sie ein bewegliches gameobject, das als Ziel für den Haupt Blick fungiert.</span><span class="sxs-lookup"><span data-stu-id="6cee4-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="6cee4-165">Wenn das Ziel von Seite zu Seite verschoben wird, wird der Anfang der Erfassung befolgt.</span><span class="sxs-lookup"><span data-stu-id="6cee4-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="6cee4-166">Wir haben diesen Trick verwendet, um sicherzustellen, dass die im Leerlauf befindliche Erfassung stets mit holograms in unterschiedlichen Teilen des Puppenhauses konfrontiert wird.</span><span class="sxs-lookup"><span data-stu-id="6cee4-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![Der Kopf der Erfassung, der zur Laufzeit nach einem Ziel-gameobject in Unity verschoben wird](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="6cee4-168">*Der Kopf der Erfassung, der zur Laufzeit nach einem Ziel-gameobject in Unity verschoben wird.*</span><span class="sxs-lookup"><span data-stu-id="6cee4-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="6cee4-169">Synchronisieren von animierten Objekten</span><span class="sxs-lookup"><span data-stu-id="6cee4-169">Syncing Animated Objects</span></span>

<span data-ttu-id="6cee4-170">Die zweite war das Animieren von Objekten, die mit einer Erfassungs Bewegung synchronisiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="6cee4-171">In unterschiedlichen Teilen der APP haben wir alle fünf Frames das sequenzielle OBJS einer bestimmten Erfassung importiert.</span><span class="sxs-lookup"><span data-stu-id="6cee4-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="6cee4-172">Die OBJS wurde dann in der Szene animiert, um sicherzustellen, dass Sie mit dem entsprechenden Frame der Erfassung übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="6cee4-173">Es ist ein mühsamer Prozess der Animation und der Keyframes, aber das Ergebnis ist hervorragend.</span><span class="sxs-lookup"><span data-stu-id="6cee4-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="6cee4-174">Sie können jetzt eine gemischte Reality-Erfassung sehen, die mit nicht erfassten Objekten interagiert.</span><span class="sxs-lookup"><span data-stu-id="6cee4-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![Synchronisierungs Animation zwischen einem gemischten Reality-Erfassungs-und UI-Panel](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="6cee4-176">*Synchronisierungs Animation zwischen einem gemischten Reality-Erfassungs-und UI-Panel*</span><span class="sxs-lookup"><span data-stu-id="6cee4-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="6cee4-177">Kreativer UI-Prozess</span><span class="sxs-lookup"><span data-stu-id="6cee4-177">UI creative process</span></span>

<span data-ttu-id="6cee4-178">Als wir das Design der Benutzeroberfläche gestartet haben, wollten wir einige der magischen und möglichen Möglichkeiten zeigen, die holograms anbieten müssen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="6cee4-179">Das einfache darstellen von statischen 2D-Fenstern und Textfeldern ist in der 3D-Welt nicht richtig.</span><span class="sxs-lookup"><span data-stu-id="6cee4-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="6cee4-180">Viele der Möglichkeiten werden nicht angezeigt. Wir haben also von Anfang an entschieden, von diesem Weg zu kommen, und machen den Holographic 3D-Raum vollständig zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="6cee4-181">Zunächst haben wir begonnen, den Bereichen, Symbolen und Textinformationen eine gewisse Stärke hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="6cee4-182">Als Benutzer sehen Sie das Textfeld.</span><span class="sxs-lookup"><span data-stu-id="6cee4-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="6cee4-183">Text Felder mit Bildern, aber wir sind nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="6cee4-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="6cee4-184">Wir haben mit den Shader von Mixed Reality Toolkit (mrtk) fortgefahren.</span><span class="sxs-lookup"><span data-stu-id="6cee4-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="6cee4-185">Die mrtk-Shader wurden zu einem leistungsfähigen Tool, und wir nutzten unsere Schablonen Features, um den Bereichen negative Tiefe hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="6cee4-186">Das heißt, anstatt Elemente vor einem Textfeld hinzuzufügen, werden die Symbole jetzt hinter einem transparenten Panel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6cee4-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="6cee4-187">Ich sehe jetzt als Benutzer etwas, das ich einfach nicht mehr in der realen Welt replizieren kann. an dieser Stelle begann Holographic Magic.</span><span class="sxs-lookup"><span data-stu-id="6cee4-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="6cee4-188">Auch als Benutzer, den ich nicht gerne lesen möchte, mache ich noch viel in der physischen Welt.</span><span class="sxs-lookup"><span data-stu-id="6cee4-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="6cee4-189">Natürlich funktionieren Symbole viel besser als der einfache Text, um eine noch leistungsfähigere Anleitung bereitzustellen. Anschließend begann ich mit der Erstellung eines Satzes von animierten Objekten und Avatars, von denen jeder eine kleine Story darüber erzählt, was im jeweiligen Szenario passiert und wie es verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6cee4-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![Animiertes GIF eines interaktiven Holographic-Menüsystems](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="6cee4-191">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="6cee4-191">Core concepts</span></span>

<span data-ttu-id="6cee4-192">**Holografischer Rahmen**</span><span class="sxs-lookup"><span data-stu-id="6cee4-192">**Holographic frame**</span></span>

![Animiertes GIF eines Benutzers, der das "Dollhouse" durchsucht, wobei der Holographic Frame hervorgehoben ist](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="6cee4-194">**Koordinatensysteme**</span><span class="sxs-lookup"><span data-stu-id="6cee4-194">**Coordinate systems**</span></span>

![Animiertes GIF eines Benutzers, der das Dollhouse mit hervorgehobenen Koordinatensystemen ansieht](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="6cee4-196">**Eyetracking – Blickverfolgung**</span><span class="sxs-lookup"><span data-stu-id="6cee4-196">**Eye tracking**</span></span>

![Animiertes GIF eines Benutzers, der stationär holograms mit hervorgehobenem Eye Eye-Ray ansieht](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="6cee4-198">**Raum Scan Visualisierung und räumliche Zuordnung**</span><span class="sxs-lookup"><span data-stu-id="6cee4-198">**Room scan visualization and spatial mapping**</span></span>

![Animiertes GIF aller Oberflächen innerhalb des zu zugeordneten Dollhouse](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="6cee4-200">**Grundlegendes zu Szenen**</span><span class="sxs-lookup"><span data-stu-id="6cee4-200">**Scene understanding**</span></span>

![Animiertes GIF von Objekten im "Dollhouse" erkannt](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="6cee4-202">**Punkt und Commit mit Hand Strahlen**</span><span class="sxs-lookup"><span data-stu-id="6cee4-202">**Point and commit with hand rays**</span></span>

![Animiertes GIF eines Benutzers mit hervorgehobenem Hand Strahl](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="6cee4-204">Augenblicke ausprobieren</span><span class="sxs-lookup"><span data-stu-id="6cee4-204">"Try it out" moments</span></span>

<span data-ttu-id="6cee4-205">Der Entwurf von holograms vermittelt gemischte Reality-Konzepte, aber Sie können Sie auch in Ihrem Raum ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="6cee4-205">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="6cee4-206">Nach einigen dieser Erläuterungen halten wir Sie an der Puppenstube und werden in einen interaktiven Moment einsteigen.</span><span class="sxs-lookup"><span data-stu-id="6cee4-206">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="6cee4-207">Im folgenden sind einige Beispiele für diese interaktiven Momente aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="6cee4-207">Here are some examples of those interactive moments:</span></span>

![Animiertes GIF des Hand Verfolgungs Rahmens, der angezeigt wird, wenn die Hände erkannt werden, und wenn Sie das Sichtfeld eingeben.](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="6cee4-209">*Der handverfolgungsframe, der angezeigt wird, wenn die Hände erkannt werden, und wenn Sie das Feld der Ansicht eingeben.*</span><span class="sxs-lookup"><span data-stu-id="6cee4-209">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![Animiertes GIF der Interaktion mit kollidierenden Kristallen durch die weite Interaktion](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="6cee4-211">*Interagieren mit kollidierenden Kristallen durch die weite Interaktion*</span><span class="sxs-lookup"><span data-stu-id="6cee4-211">*Interacting with colliding crystals through far interaction*</span></span>

![Animiertes GIF zum Durchsuchen von Near Interaktionen](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="6cee4-213">*Erkunden von Near Interaktion-auffortungen*</span><span class="sxs-lookup"><span data-stu-id="6cee4-213">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="6cee4-214">Informationen zum Team</span><span class="sxs-lookup"><span data-stu-id="6cee4-214">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="6cee4-215"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="6cee4-215"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="6cee4-216"><i>Leitender technischer Designer</i></span><span class="sxs-lookup"><span data-stu-id="6cee4-216"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="6cee4-217">Dan ist der Creative Director zum Entwerfen von holograms und funktioniert zurzeit als Entwurfs Leiter für die gemischte Reality Academy von Microsoft in San Francisco und war zuvor ein Designer in einem der Mixed Reality-Studio von Microsoft in London.</span><span class="sxs-lookup"><span data-stu-id="6cee4-217">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="6cee4-218"><b>Martin-Wettig</b></span><span class="sxs-lookup"><span data-stu-id="6cee4-218"><b>Martin Wettig</b></span></span><br><span data-ttu-id="6cee4-219"><i>Senior 3D-Künstler</i></span><span class="sxs-lookup"><span data-stu-id="6cee4-219"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="6cee4-220">Martin leitet 3D-Grafiken und UI-Design für das Entwerfen von holograms ein und war zuvor Senior 3D-Artist in einem der Mixed Reality-Studio von Microsoft in Berlin.</span><span class="sxs-lookup"><span data-stu-id="6cee4-220">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="6cee4-221">Ein großer Dank für das Mixed Reality-Entwurfs Team für die gemeinsame Nutzung von Kenntnissen und für die erstaunlichen Menschen in der [Objekt Theorie](https://objecttheory.com/) , dass Sie in jedem Schritt des Projekts wesentliche Teammitglieder sind.</span><span class="sxs-lookup"><span data-stu-id="6cee4-221">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="6cee4-222">Vielen Dank für ihre faszinierenden Talente, für Ihre Leidenschaft und das besondere Design.</span><span class="sxs-lookup"><span data-stu-id="6cee4-222">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6cee4-223">Herunterladen der APP zum Entwerfen von holograms</span><span class="sxs-lookup"><span data-stu-id="6cee4-223">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)