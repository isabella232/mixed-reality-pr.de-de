---
title: Billboarding und Tag-along
description: Erfahren Sie, wie Sie Objekte mit dem Abgleichen von Objekten verwenden, die sich immer für den Benutzer in gemischten Reality-Anwendungen orientieren.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, fakboardingvorgang, tagparallel, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 92caa1bcd325cefecc6d3820b819cecfce6fc09c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009611"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="d7219-104">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="d7219-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="d7219-105">Was ist die Abrechnung?</span><span class="sxs-lookup"><span data-stu-id="d7219-105">What is billboarding?</span></span>

<span data-ttu-id="d7219-106">Bei der Abrechnung handelt es sich um ein Verhaltens Konzept, das auf Objekte in gemischter Realität angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d7219-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="d7219-107">Objekte mit einem Abrechnungs-Board orientieren sich stets an dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="d7219-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="d7219-108">Text-und Menüsysteme sind gängige Anwendungsfälle, in denen statische Objekte, die in der Umgebung des Benutzers platziert werden (weltweit gesperrt), andernfalls verdeckt oder unlesbar sind, wenn sich die Benutzer bewegen.</span><span class="sxs-lookup"><span data-stu-id="d7219-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="d7219-109">Objekte mit aktiviertem fakboardingvorgang können in der Benutzerumgebung frei rotiert werden.</span><span class="sxs-lookup"><span data-stu-id="d7219-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="d7219-110">Sie können je nach Entwurfs Überlegungen auch auf eine einzelne Achse beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="d7219-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="d7219-111">Beachten Sie, dass die Objekte, die von einem Abbild untergebracht werden, sich selbst durch ein-oder ausgeblendet werden können, wenn Sie sich zu nahe an anderen Objekten befinden oder in hololens zu schließen.</span><span class="sxs-lookup"><span data-stu-id="d7219-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="d7219-112">Um dies zu vermeiden, stellen Sie sich den Gesamt Speicherbedarf vor, der von einem Objekt erzeugt wird, wenn es auf der Achse gedreht wird, die für das</span><span class="sxs-lookup"><span data-stu-id="d7219-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="d7219-113">Was ist ein Tag?</span><span class="sxs-lookup"><span data-stu-id="d7219-113">What is a tag-along?</span></span>

<span data-ttu-id="d7219-114">Tagparallel ist ein Verhaltens Konzept, das holograms hinzugefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d7219-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="d7219-115">Ein Tag-entlang-Objekt versucht, in einem Bereich zu bleiben, der es dem Benutzer ermöglicht, komfortabel zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="d7219-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="d7219-116">![Das hololens-Pins-Panel ist ein gutes Beispiel dafür, wie sich das Tag-entlang verhält.](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d7219-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="d7219-117">*Das hololens-Startmenü ist ein gutes Beispiel für das tagparallel Verhalten.*</span><span class="sxs-lookup"><span data-stu-id="d7219-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="d7219-118">Tagbasierte Objekte verfügen über Parameter, die die Art und Weise, wie Sie sich Verhalten, optimieren können.</span><span class="sxs-lookup"><span data-stu-id="d7219-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="d7219-119">Der Inhalt kann sich innerhalb oder außerhalb der Sicht des Benutzers befinden, während sich der Benutzer um seine Umgebung bewegt.</span><span class="sxs-lookup"><span data-stu-id="d7219-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="d7219-120">Während des Verschiebens versucht der Inhalt, in der Peripherie des Benutzers zu bleiben, indem er an den Rand der Ansicht bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="d7219-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="d7219-121">Der Inhalt ist möglicherweise vorübergehend außerhalb der Ansicht, je nachdem, wie schnell der Benutzer bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="d7219-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="d7219-122">Wenn der Benutzer in Richtung des tagbasierten Objekts zeigt, wird es vollständig in die Ansicht integriert.</span><span class="sxs-lookup"><span data-stu-id="d7219-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="d7219-123">Stellen Sie sich vor, dass Inhalte immer "auf einen Blick entfernt" werden, damit Benutzer niemals vergessen, welche Richtung ihr Inhalt hat.</span><span class="sxs-lookup"><span data-stu-id="d7219-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="d7219-124">Zusätzliche Parameter können dazu führen, dass das Tag-an-Objekt von einem Gummi Band an den Kopf des Benutzers angefügt wird.</span><span class="sxs-lookup"><span data-stu-id="d7219-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="d7219-125">Durch die Beschleunigung oder Verlangsamung der Dämpfung wird das-Objekt gewichtet, sodass es physisch vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="d7219-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="d7219-126">Dieses Spring Verhalten ist ein kostengünstiger, mit dem der Benutzer ein genaues mentales Modell zur Funktionsweise von Tag-Along erstellen kann.</span><span class="sxs-lookup"><span data-stu-id="d7219-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="d7219-127">Audiodaten helfen bei der Bereitstellung anderer Hinweise, wenn Benutzer Objekte im tagbasierten Modus haben.</span><span class="sxs-lookup"><span data-stu-id="d7219-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="d7219-128">Audiogeschwindigkeit sollte die Geschwindigkeit der Bewegung verstärken. eine schnelle Kopfzeile sollte einen auffälligeren Soundeffekt bereitstellen, während das laufen mit einer natürlichen Geschwindigkeit minimale oder keine Audioeffekte aufweisen sollte.</span><span class="sxs-lookup"><span data-stu-id="d7219-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="d7219-129">Ebenso wie wirklich mit dem Titel gesperrter Inhalt können sich taggingobjekte als überwältigend oder übersichtlich erweisen, wenn Sie in der Ansicht des Benutzers sehr stark verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="d7219-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="d7219-130">Wenn ein Benutzer die Suche durchsucht, werden die zugehörigen Sinne schnell angehalten.</span><span class="sxs-lookup"><span data-stu-id="d7219-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="d7219-131">Ihr Saldo informiert Sie darüber, dass ihre Kopfzeile angehalten wurde, und ihre Vision sieht, dass die Welt nicht mehr schaltet.</span><span class="sxs-lookup"><span data-stu-id="d7219-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="d7219-132">Wenn das Tag-Along jedoch weiterhin verschoben wird, wenn der Benutzer angehalten wurde, kann es seine Sinne verwirren.</span><span class="sxs-lookup"><span data-stu-id="d7219-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="d7219-133">Fakboardingvorgang und tagparallel in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="d7219-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="d7219-134">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts für das fakboardingverhalten und das tagbasierte Verhalten bereit.</span><span class="sxs-lookup"><span data-stu-id="d7219-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="d7219-135">Weisen Sie das Billboard.cs-Skript einem beliebigen Objekt zu, um das Verhalten von Verhaltensweisen hinzuzufügen, und machen Sie das Objekt immer als</span><span class="sxs-lookup"><span data-stu-id="d7219-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="d7219-136">Verwenden Sie das RadialView.cs-Skript, um das tagbasierte Verhalten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="d7219-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="d7219-137">Sie können verschiedene Optionen wie z. b. lerping-Zeit, Entfernung und Grad anpassen.</span><span class="sxs-lookup"><span data-stu-id="d7219-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="d7219-138">-Solver der mrtk-radialen Ansicht</span><span class="sxs-lookup"><span data-stu-id="d7219-138">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="d7219-139">Mrtk-Billboard-Skript</span><span class="sxs-lookup"><span data-stu-id="d7219-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="d7219-140">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d7219-140">See also</span></span>

* [<span data-ttu-id="d7219-141">Cursor</span><span class="sxs-lookup"><span data-stu-id="d7219-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d7219-142">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="d7219-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d7219-143">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="d7219-143">Button</span></span>](button.md)
* [<span data-ttu-id="d7219-144">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="d7219-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d7219-145">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="d7219-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d7219-146">Manipulation</span><span class="sxs-lookup"><span data-stu-id="d7219-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d7219-147">Handmenü</span><span class="sxs-lookup"><span data-stu-id="d7219-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d7219-148">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="d7219-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d7219-149">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="d7219-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d7219-150">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="d7219-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d7219-151">Tastatur</span><span class="sxs-lookup"><span data-stu-id="d7219-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d7219-152">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="d7219-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d7219-153">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="d7219-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="d7219-154">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="d7219-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="d7219-155">Shader</span><span class="sxs-lookup"><span data-stu-id="d7219-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="d7219-156">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="d7219-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d7219-157">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="d7219-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d7219-158">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="d7219-158">Surface magnetism</span></span>](surface-magnetism.md)
