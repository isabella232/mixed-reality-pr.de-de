---
title: Entwerfen von Hologrammen
description: Erfahren Sie mehr über Mixed Reality durch die neue Anwendung Designing Holograms (Entwerfen von Hologrammen) von Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, Hologramme, Entwerfen von Hologrammen, Lernen, Beispiel-App, Mixed Reality-Headset, Virtual Reality-Headset, Was ist Virtual Reality?
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143638"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="e8a58-104">Erstellen von Hologrammen</span><span class="sxs-lookup"><span data-stu-id="e8a58-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="e8a58-105">Lassen Sie ein kleines Ladefenster zu, um alle coolen GIFs und eingebetteten Videos auf dieser Seite zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="e8a58-106">Das Erlernen des Entwurfs für Mixed Reality kann schwierig sein, da das Medium nicht immer gut in 2D-Entwurfsprozesse übersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="e8a58-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="e8a58-107">Hier bei Microsoft haben wir eine kostenlose App für die HoloLens 2 erstellt, mit der Sie die Grundlagen von Mixed Reality UX Design aus erster Hand kennenlernen können.</span><span class="sxs-lookup"><span data-stu-id="e8a58-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="e8a58-108">Der einzigartige Ansatz der App Designing Holograms (Entwerfen von Hologrammen) geht auf Mixed Reality-Verhalten, Tipps und Empfehlungen ein, um Ihnen zu helfen, ansprechende und beeindruckende HoloLens-Apps selbst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="e8a58-109">Laden Sie die App kostenlos von der Microsoft Store herunter, und lernen Sie vom Mixed Reality DesignTeam von Microsoft!</span><span class="sxs-lookup"><span data-stu-id="e8a58-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e8a58-110">Herunterladen der App "Entwerfen von Hologrammen"</span><span class="sxs-lookup"><span data-stu-id="e8a58-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![Animiertes GIF der Kopfverfolgungsszene im Demoraum des Entwerfens eines Hologramms](images/designing-holograms/demo-room.gif)

<span data-ttu-id="e8a58-112">*Entwerfen des Demoraums des Hologramms (auch als "Haus der Brille" bezeichnet)*</span><span class="sxs-lookup"><span data-stu-id="e8a58-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="e8a58-113">Entwerfen für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e8a58-113">Designing for mixed reality</span></span>

<span data-ttu-id="e8a58-114">Wie viele von Ihnen habe ich mobile Apps entwickelt.</span><span class="sxs-lookup"><span data-stu-id="e8a58-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="e8a58-115">Aus einer 2D-Entwurfsumgebung zu stammen, war der Einstieg in das räumliche Computing, in dem sich jetzt alles in der Welt befindet, eine bedeutende Verschiebung.</span><span class="sxs-lookup"><span data-stu-id="e8a58-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="e8a58-116">In Mixed Reality sind Apps nicht mehr auf einen 2D-Bildschirm beschränkt. Tatsächlich sind sie fast frei, werden in der realen Welt platziert und interagieren mit echten Objekten.</span><span class="sxs-lookup"><span data-stu-id="e8a58-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="e8a58-117">Für mich ist das Verbinden von 3D-Erfahrungen mit herkömmlichen 2D-Entwurfsprozessen der schwierigste Aspekt der Mixed Reality-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="e8a58-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="e8a58-118">In Gesprächen mit Kunden würde ich beispielsweise folgendes hören: "Ich weiß, welche Features einbezogen werden müssen und wie ich sie in Betrieb nehmen kann.</span><span class="sxs-lookup"><span data-stu-id="e8a58-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="e8a58-119">Es ist Code, ich kann die Dokumentationen und Tutorials befolgen, aber die Benutzererfahrung?</span><span class="sxs-lookup"><span data-stu-id="e8a58-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="e8a58-120">So viele Features, unterschiedliche Eingabeoptionen, verschiedene Szenarien und physische Umgebungen, das ist überwältigend."</span><span class="sxs-lookup"><span data-stu-id="e8a58-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="e8a58-121">![Bild vom HoloLens 2 Design Workshop in San Francisco ](images/designing-holograms/workshop.jpeg)
 *Bild vom HoloLens 2 Design Workshop in San Francisco*</span><span class="sxs-lookup"><span data-stu-id="e8a58-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="e8a58-122">Eine Möglichkeit zum Trainieren</span><span class="sxs-lookup"><span data-stu-id="e8a58-122">An opportunity to teach</span></span>

<span data-ttu-id="e8a58-123">Es war zunächst nicht offensichtlich, aber es wurde eine hervorragende Gelegenheit geboten, Mixed Reality als Medium zu verwenden, um es zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="e8a58-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="e8a58-124">Das Entwerfen von Hologrammen ist ein visuelles Erlebnis, das Mixed Reality-Entwurfskonzepte und -empfehlungen erläutert.</span><span class="sxs-lookup"><span data-stu-id="e8a58-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="e8a58-125">Es sind nur Sie und eine virtuelle Lehrkraft, die Mixed Reality-Entwurfskonzepte demonstrieren.</span><span class="sxs-lookup"><span data-stu-id="e8a58-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="e8a58-126">Alles ist aus der Perspektive einer dritten Person mit der Erfahrung fest in Ihrem eigenen Bereich.</span><span class="sxs-lookup"><span data-stu-id="e8a58-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="e8a58-127">*Video zum Entwerfen von Hologramm-Trailern*</span><span class="sxs-lookup"><span data-stu-id="e8a58-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="e8a58-128">Erkunden des Hauses "House"</span><span class="sxs-lookup"><span data-stu-id="e8a58-128">Exploring the doll house</span></span>

<span data-ttu-id="e8a58-129">Das Haus ist die virtuelle Umgebung, die wir in der gesamten App verwenden.</span><span class="sxs-lookup"><span data-stu-id="e8a58-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="e8a58-130">Die Umgebung ist ein 80 x 60 x 40 cm großer Raum, der die grundlegenden Elemente enthält, die die meisten Räume gemeinsam haben, wie z. B. Wände, Licht, Gäste, einen Tisch und einen Fernseher.</span><span class="sxs-lookup"><span data-stu-id="e8a58-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="e8a58-131">Das Haus ist der Hauptbereich der App-Erfahrung, daher mussten wir sicherstellen, dass es in jeder Umgebung hervorragend funktioniert.</span><span class="sxs-lookup"><span data-stu-id="e8a58-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="e8a58-132">Stellen Sie sich dies als kleinen Demoraum für die Visualisierung aller arten von Mixed Reality-Konzepten vor.</span><span class="sxs-lookup"><span data-stu-id="e8a58-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="e8a58-133">*Video zum Anpassungsverhalten vonHouse*</span><span class="sxs-lookup"><span data-stu-id="e8a58-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="e8a58-134">1:1 vs 1:10 Prototypen</span><span class="sxs-lookup"><span data-stu-id="e8a58-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="e8a58-135">Unsere anfängliche Annahme war, dass 1:1-Demonstrationen unglaublich sein würden, fast wie ein Blick auf einen echten Lehrer.</span><span class="sxs-lookup"><span data-stu-id="e8a58-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="e8a58-136">Der Benutzer sieht alles, was die Lehrkraft in der Praxis sieht.</span><span class="sxs-lookup"><span data-stu-id="e8a58-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="e8a58-137">Wir haben jedoch sofort festgestellt, dass es einige Probleme geben würde:</span><span class="sxs-lookup"><span data-stu-id="e8a58-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="e8a58-138">Die meisten Entwickler führen ihre Apps in Büros oder in Räumen aus, die kleiner als der Demoraum sind, sodass sie nicht passen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="e8a58-139">Anzeigen sind additiv, d. h., die gesamte virtuelle Umgebung wird über dem Raum eines Benutzers überlagert.</span><span class="sxs-lookup"><span data-stu-id="e8a58-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="e8a58-140">Dies kann mit zwei Tabellen verwirrend werden, z. B. doppelten Couchs und Wänden, die nicht ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="e8a58-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="e8a58-141">Und im schlimmsten Fall ist eine virtuelle Umgebung stark durch ein Sichtfeld eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="e8a58-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="e8a58-142">Als wir eine Miniskala von 1:10 ausprobiert haben, war das Ergebnis ein ansprechender Blick auf einen realistischen Raum.</span><span class="sxs-lookup"><span data-stu-id="e8a58-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="e8a58-143">Sie konnten alles, was gerade passierte, aus einem beliebigen Winkel gleichzeitig sehen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="e8a58-144">Am überraschendsten war, dass die meisten Tester es so viel immersiver gefunden haben, eine kleine Version zu sehen, als dass sie nie wieder auf die 1:1-Skalierung umgeschaltet wurden.</span><span class="sxs-lookup"><span data-stu-id="e8a58-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="e8a58-145">Daher haben wir uns entschieden, die Version 1:1 tatsächlich zu nutzen und die zusätzliche Arbeit zu vermeiden, die erforderlich ist, um die Benutzeroberfläche und andere Aspekte der App anzupassen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="e8a58-146">![Ansichtsfeld mit 1:1-Skalierungsfeld ](images/designing-holograms/1-1-scale.png)
 *mit 1:1-Skalierung*</span><span class="sxs-lookup"><span data-stu-id="e8a58-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="e8a58-147">![View Field of View with 1:10 scale ](images/designing-holograms/1-10-scale.png)
 *Field of View with 1:10 scale (Sichtfeld mit 1:10* Skalierung)</span><span class="sxs-lookup"><span data-stu-id="e8a58-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="e8a58-148">Verwenden von Mixed Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="e8a58-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="e8a58-149">Eines der typischen Merkmale dieser App ist die Verwendung von Mixed Reality-Aufnahme zum Trainieren und Demonstrieren von Mixed Reality-Entwurfskonzepten.</span><span class="sxs-lookup"><span data-stu-id="e8a58-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="e8a58-150">Microsoft verfügt über ein Mixed Reality-Aufnahme Studio in San Francisco.</span><span class="sxs-lookup"><span data-stu-id="e8a58-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="e8a58-151">Microsoft lizenziert diese Technologie auch an andere Studios, z.B. Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studio in London, SK Telecom in Seattle und Volucap in London.</span><span class="sxs-lookup"><span data-stu-id="e8a58-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="e8a58-152">Weitere Informationen zu unseren Mixed Reality-Aufnahme Studio finden Sie [hier.](https://www.microsoft.com/mixed-reality/capture-studios)</span><span class="sxs-lookup"><span data-stu-id="e8a58-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="e8a58-153">*Rohmaterial von Daniel Ualdero von einer der 106 Kameras im Mixed Reality-Aufnahme Studio in San Francisco.*</span><span class="sxs-lookup"><span data-stu-id="e8a58-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="e8a58-154">Der Erfassungsprozess generiert ein keyframed-Gittermodell, Normalität und Textur, das als OBJ-/PNG-Dateien für die weitere Postproduktion oder als komprimierte H.264-MP4-Datei zur Wiedergabe bereit sein kann.</span><span class="sxs-lookup"><span data-stu-id="e8a58-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="e8a58-155">Diese Dateien können in Unity-, Unreal-, Native- und WebXR-Projekte importiert werden.</span><span class="sxs-lookup"><span data-stu-id="e8a58-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="e8a58-156">Dateien können unter Windows, iOS, Mac, Android, Magic Leap und Playstation VR ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e8a58-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="e8a58-157">*Der Capture Player zum Analysieren von MP4-Dateien, die Video mit Audio und eingebetteten Gitternetzen enthalten.*</span><span class="sxs-lookup"><span data-stu-id="e8a58-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="e8a58-158">Bearbeiten von Erfassungen und virtuellen Objekten</span><span class="sxs-lookup"><span data-stu-id="e8a58-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="e8a58-159">Mixed Reality Captures erzeugt virtuelle Darstellungen von Menschen oder Haustieren, aber manchmal benötigen Sie diese Zeichen möglicherweise, um mit anderen virtuellen Objekten zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="e8a58-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="e8a58-160">Die folgenden beiden Beispiele zeigen verschiedene Möglichkeiten, wie wir die Szenen bearbeitet haben, um diesen Effekt zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="e8a58-161">Anpassung des Anvings mit dem Kopf</span><span class="sxs-lookup"><span data-stu-id="e8a58-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="e8a58-162">Mit der Kopfkopfanpassung können Sie den Kopf einer erfassten Person zur Laufzeit verschieben, was bedeutet, dass Sie ein Erfassungsgesicht für einen Benutzer haben könnten.</span><span class="sxs-lookup"><span data-stu-id="e8a58-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="e8a58-163">In unserem Fall haben wir es verwendet, um das Sichtfeld und das feld of interest zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="e8a58-164">Unten sehen Sie ein sich bewegendes Spielobjekt, das als Ziel für den Anvschauungs-Blick mit dem Kopf verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e8a58-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="e8a58-165">Wenn wir das Ziel von Seite zu Seite verschieben, folgt der Kopf der Erfassung.</span><span class="sxs-lookup"><span data-stu-id="e8a58-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="e8a58-166">Wir haben diesen Trick verwendet, um sicherzustellen, dass die Aufnahme im Leerlauf immer hologrammen gegenüberstehen würde, die in verschiedenen Teilen des Haus platziert wurden.</span><span class="sxs-lookup"><span data-stu-id="e8a58-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![Der Kopf des Capture-Objekts wird zur Laufzeit nach einem Zielspielobjekt in Unity verschoben.](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="e8a58-168">*Der Kopf des Capture-Objekts wird zur Laufzeit nach einem Zielspielobjekt in Unity verschoben.*</span><span class="sxs-lookup"><span data-stu-id="e8a58-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="e8a58-169">Synchronisieren von animierten Objekten</span><span class="sxs-lookup"><span data-stu-id="e8a58-169">Syncing Animated Objects</span></span>

<span data-ttu-id="e8a58-170">Das zweite war das Animieren von Objekten zur Synchronisierung mit der Bewegung einer Erfassung.</span><span class="sxs-lookup"><span data-stu-id="e8a58-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="e8a58-171">In verschiedenen Teilen der App haben wir sequenzielle OBJs einer bestimmten Erfassung alle fünf Frames importiert.</span><span class="sxs-lookup"><span data-stu-id="e8a58-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="e8a58-172">Die OBJs wurden dann in der Szene animiert, um sicherzustellen, dass sie mit dem entsprechenden Frame der Aufnahme übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="e8a58-173">Es ist ein mühsamer Prozess der Animation und Schlüsselinfrastruktur, aber das Ergebnis ist sehr gut.</span><span class="sxs-lookup"><span data-stu-id="e8a58-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="e8a58-174">Sie können nun sehen, Mixed Reality-Aufnahme mit nicht erfassten Objekten interagiert.</span><span class="sxs-lookup"><span data-stu-id="e8a58-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![Synchronisierte Animation zwischen einem Mixed Reality-Aufnahme und einem Benutzeroberflächenbereich](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="e8a58-176">*Synchronisierte Animation zwischen einem Mixed Reality-Aufnahme und einem Benutzeroberflächenbereich*</span><span class="sxs-lookup"><span data-stu-id="e8a58-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="e8a58-177">Kreativer Prozess der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="e8a58-177">UI creative process</span></span>

<span data-ttu-id="e8a58-178">Als wir mit dem Entwurf der Benutzeroberfläche begonnen haben, wollten wir einige der Magischen und Möglichkeiten zeigen, die Hologramme zu bieten haben.</span><span class="sxs-lookup"><span data-stu-id="e8a58-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="e8a58-179">Das einfache Anzeigen statischer 2D-Fenster und Textfelder ist in der 3D-Welt nicht das richtige.</span><span class="sxs-lookup"><span data-stu-id="e8a58-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="e8a58-180">Viele der möglichkeiten zur Hand werden einfach nicht angezeigt. Daher haben wir uns von Anfang an entschieden, davon abzugehen und den holografischen 3D-Raum voll zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="e8a58-181">Zunächst haben wir mit dem Hinzufügen einiger Stärke zu den Panels, Symbolen und Textinformationen begonnen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="e8a58-182">Als Benutzer wird jedoch ein Textfeld angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e8a58-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="e8a58-183">Textfelder mit Bildern, aber nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="e8a58-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="e8a58-184">Wir haben die Mixed Reality Toolkit-Shader (MRTK) verwendet.</span><span class="sxs-lookup"><span data-stu-id="e8a58-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="e8a58-185">Die MRTK-Shader wurden zu einem leistungsstarken Tool, und wir haben die Schablonenfeatures genutzt, um den Panels negative Tiefe hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="e8a58-186">Das bedeutet, dass die Symbole jetzt hinter einem transparenten Bereich angezeigt werden, anstatt Elemente vor einem Textfeld hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="e8a58-187">Was ich jetzt als Benutzer sehe, ist etwas, das ich in der realen Welt einfach nicht mehr replizieren kann, und an dieser Stelle hat holografische Magic begonnen.</span><span class="sxs-lookup"><span data-stu-id="e8a58-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="e8a58-188">Auch als Benutzer, den ich nicht wirklich lesen möchte, tue ich bereits viel in der physischen Welt.</span><span class="sxs-lookup"><span data-stu-id="e8a58-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="e8a58-189">Symbole funktionieren natürlich viel besser als einfacher Text. Um eine noch leistungsfähigere Anleitung bereitzustellen, habe ich dann damit begonnen, eine Reihe von animierten Objekten und Avataren zu erstellen, von denen jeder eine kleine Geschichte darüber erzählen, was im jeweiligen Szenario geschieht und wie es verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e8a58-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![Animiertes GIF eines interaktiven holografischen Menüsystems](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="e8a58-191">Kernkonzepte</span><span class="sxs-lookup"><span data-stu-id="e8a58-191">Core concepts</span></span>

<span data-ttu-id="e8a58-192">**Head Tracking und Eye Tracking**</span><span class="sxs-lookup"><span data-stu-id="e8a58-192">**Head Tracking and Eye Tracking**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="e8a58-193">**Handtracking**</span><span class="sxs-lookup"><span data-stu-id="e8a58-193">**Hand Tracking**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

<span data-ttu-id="e8a58-194">**Räumliche Wahrnehmung**</span><span class="sxs-lookup"><span data-stu-id="e8a58-194">**Spatial Awareness**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="e8a58-195">**Holografischer Rahmen**</span><span class="sxs-lookup"><span data-stu-id="e8a58-195">**Holographic frame**</span></span>

![Animierte GIF-Datei eines Benutzers, der sich mit hervorgehobener holografischem Rahmen um das Reihenhäuschen kümmert](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="e8a58-197">**Koordinatensysteme**</span><span class="sxs-lookup"><span data-stu-id="e8a58-197">**Coordinate systems**</span></span>

![Animierte GIF-Datei eines Benutzers, der sich mit den hervorgehobenen Koordinatensystemen um das Haus herumschaut](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="e8a58-199">**Eyetracking – Blickverfolgung**</span><span class="sxs-lookup"><span data-stu-id="e8a58-199">**Eye tracking**</span></span>

![Animierte GIF-Datei eines Benutzers, der mit hervorgehobener Strahlaufnahme des Anvierens mit den Augen stationäre Hologramme ansieht](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="e8a58-201">**Raumscanvisualisierung und räumliche Zuordnung**</span><span class="sxs-lookup"><span data-stu-id="e8a58-201">**Room scan visualization and spatial mapping**</span></span>

![Animiertes GIF aller Oberflächen innerhalb des zuzuordnenden Doppelhäuschens](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="e8a58-203">**Grundlegendes zu Szenen**</span><span class="sxs-lookup"><span data-stu-id="e8a58-203">**Scene understanding**</span></span>

![Animiertes GIF von Objekten im Doppelhaus, das erkannt wird](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="e8a58-205">**Zeigen und Committen mit Handstrahl**</span><span class="sxs-lookup"><span data-stu-id="e8a58-205">**Point and commit with hand rays**</span></span>

![Animiertes GIF eines Benutzers, der seine Hand mit einem hervorgehobenen Handstrahl hebt](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="e8a58-207">"Try it out" (Ausprobieren)</span><span class="sxs-lookup"><span data-stu-id="e8a58-207">"Try it out" moments</span></span>

<span data-ttu-id="e8a58-208">Das Entwerfen von Hologrammen vermittelt Mixed Reality-Konzepte, ermöglicht ihnen aber auch, sie in Ihrem Raum auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="e8a58-208">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="e8a58-209">Nach einigen dieser Erklärungen halten wir an, und nehmen Sie aus dem Haus des Schlosses in einen interaktiven Moment.</span><span class="sxs-lookup"><span data-stu-id="e8a58-209">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="e8a58-210">Im Folgenden finden Sie einige Beispiele für diese interaktiven Augenblicke:</span><span class="sxs-lookup"><span data-stu-id="e8a58-210">Here are some examples of those interactive moments:</span></span>

![Animiertes GIF des Handtrackingframes, das anzeigt, wann Hände erkannt werden und wann sie in das Sichtfeld gelangen](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="e8a58-212">*Der Handtrackingrahmen, der anzeigt, wann Hände erkannt werden und wann sie in das Sichtfeld gelangen.*</span><span class="sxs-lookup"><span data-stu-id="e8a58-212">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![Animiertes GIF der Interaktion mit kollidierenden Steine durch fernen Interaktion](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="e8a58-214">*Interaktion mit kollidierenden Steine durch weit entfernte Interaktion*</span><span class="sxs-lookup"><span data-stu-id="e8a58-214">*Interacting with colliding crystals through far interaction*</span></span>

![Animierte GIF-Datei zum Untersuchen von Umgebungsinteraktions-Affordances](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="e8a58-216">*Untersuchen von Nahezu-Interaktionsentitäten*</span><span class="sxs-lookup"><span data-stu-id="e8a58-216">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="e8a58-217">Informationen zum Team</span><span class="sxs-lookup"><span data-stu-id="e8a58-217">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="e8a58-218"><b>Daniel Osodero</b></span><span class="sxs-lookup"><span data-stu-id="e8a58-218"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="e8a58-219"><i>Leitender technischer Designer</i></span><span class="sxs-lookup"><span data-stu-id="e8a58-219"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="e8a58-220">Dan ist Creative Director für das Entwerfen von Hologrammen und arbeitet derzeit als Designleiter für die Mixed Reality Academy von Microsoft in San Francisco und war zuvor Designer in einer der Mixed Reality Studios von Microsoft in London.</span><span class="sxs-lookup"><span data-stu-id="e8a58-220">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="e8a58-221"><b>MartinUngig</b></span><span class="sxs-lookup"><span data-stu-id="e8a58-221"><b>Martin Wettig</b></span></span><br><span data-ttu-id="e8a58-222"><i>Senior 3D-Interpret</i></span><span class="sxs-lookup"><span data-stu-id="e8a58-222"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="e8a58-223">Martin leitet 3D-Grafik und UI-Design beim Entwerfen von Hologrammen und war zuvor Senior 3D-Interpret in einer der Mixed Reality Studio von Microsoft in Konzeption.</span><span class="sxs-lookup"><span data-stu-id="e8a58-223">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="e8a58-224">Ein großer Dank gilt dem Mixed Reality-Entwurfsteam, dass es so viel Wissen geteilt hat, und den beeindruckenden Mitarbeitern der [Objekttheorie,](https://objecttheory.com/) die in jedem Schritt des Projekts wichtige Teampartner sind.</span><span class="sxs-lookup"><span data-stu-id="e8a58-224">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="e8a58-225">Vielen Dank für Ihren großartigen Talent, für Ihre Leidenschaft und ihren besonderen Blick für das Design.</span><span class="sxs-lookup"><span data-stu-id="e8a58-225">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e8a58-226">Herunterladen der App "Entwerfen von Hologrammen"</span><span class="sxs-lookup"><span data-stu-id="e8a58-226">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)