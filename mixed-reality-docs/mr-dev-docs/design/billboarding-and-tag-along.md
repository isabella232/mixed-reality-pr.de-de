---
title: Billboarding und Tag-along
description: Hier erfahren Sie, wie Sie Objekte mit Demieren verwenden, die sich immer darauf ausrichten, den Benutzer in Mixed Reality-Anwendungen zu sehen.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Gaming, Tag-Along, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0bd1ac2168284d714240c6775468a61ed3e665b8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600339"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="78d3a-104">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="78d3a-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="78d3a-105">Was ist Dies?</span><span class="sxs-lookup"><span data-stu-id="78d3a-105">What is billboarding?</span></span>

<span data-ttu-id="78d3a-106">Das Erstellen von Objekten ist ein Verhaltenskonzept, das auf Objekte in Mixed Reality angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="78d3a-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="78d3a-107">Objekte mit Demieren richten sich immer so aus, dass sie dem Benutzer gegenüber stehen.</span><span class="sxs-lookup"><span data-stu-id="78d3a-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="78d3a-108">Text- und Menüsysteme sind häufige Anwendungsfälle, in denen statische Objekte, die in der Umgebung des Benutzers platziert werden (weltgesperrt), andernfalls verdeckt oder unlesbar sind, wenn sich Benutzer bewegen.</span><span class="sxs-lookup"><span data-stu-id="78d3a-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="78d3a-109">Objekte mit aktivierter Umdrehung können sich in der Umgebung des Benutzers frei drehen.</span><span class="sxs-lookup"><span data-stu-id="78d3a-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="78d3a-110">Sie können je nach Entwurfsüberlegungen auch auf eine einzelne Achse beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="78d3a-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="78d3a-111">Beachten Sie, dass sich objekte, die zu nah an anderen Objekten platziert werden, oder in HoloLens zu nahe gescannte Oberflächen ausschneiden oder verdecken können.</span><span class="sxs-lookup"><span data-stu-id="78d3a-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="78d3a-112">Um dies zu vermeiden, denken Sie an den gesamten Fußabdruck, den ein Objekt erzeugen kann, wenn es auf der Achse gedreht wird, die für das Auffahren aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="78d3a-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="78d3a-113">Was ist ein Tag-Along?</span><span class="sxs-lookup"><span data-stu-id="78d3a-113">What is a tag-along?</span></span>

<span data-ttu-id="78d3a-114">Tag-Along ist ein Verhaltenskonzept, das Hologrammen hinzugefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="78d3a-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="78d3a-115">Ein Tag-Along-Objekt versucht, in einem Bereich zu bleiben, der dem Benutzer die Interaktion ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="78d3a-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="78d3a-116">![Der HoloLens-Pinbereich ist ein gutes Beispiel für das Tag-Along-Verhalten.](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="78d3a-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="78d3a-117">*Die HoloLens-Startmenü ist ein gutes Beispiel für das Tag-Along-Verhalten.*</span><span class="sxs-lookup"><span data-stu-id="78d3a-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="78d3a-118">Tag-Along-Objekte verfügen über Parameter, die das Verhalten optimieren können.</span><span class="sxs-lookup"><span data-stu-id="78d3a-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="78d3a-119">Inhalte können sich in oder außerhalb der Sichtlinie des Benutzers befinden, während sich der Benutzer in seiner Umgebung bewegt.</span><span class="sxs-lookup"><span data-stu-id="78d3a-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="78d3a-120">Während sie verschoben werden, versucht der Inhalt, innerhalb der Peripherie des Benutzers zu bleiben, indem er zum Rand der Ansicht gleitet.</span><span class="sxs-lookup"><span data-stu-id="78d3a-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="78d3a-121">Der Inhalt ist möglicherweise vorübergehend nicht mehr angezeigt, je nachdem, wie schnell sich der Benutzer bewegt.</span><span class="sxs-lookup"><span data-stu-id="78d3a-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="78d3a-122">Wenn der Benutzer auf das Tag-Along-Objekt anviert, wird es ausführlicher angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78d3a-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="78d3a-123">Denken Sie daran, dass Inhalte immer "einen Blick weg" sind, sodass Benutzer nie vergessen, in welche Richtung sich ihre Inhalte bewegen.</span><span class="sxs-lookup"><span data-stu-id="78d3a-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="78d3a-124">Zusätzliche Parameter können das Tag-Along-Objekt an den Kopf des Benutzers durch ein Blasenband anfügen.</span><span class="sxs-lookup"><span data-stu-id="78d3a-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="78d3a-125">Die beschleunigungs- oder verlangsamungsbeschleunigende Beschleunigung gibt dem Objekt Gewicht, sodass es physisch vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="78d3a-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="78d3a-126">Dieses Spring-Verhalten ist eine Variante, die dem Benutzer hilft, ein genaues mentales Modell für die Funktionsweise von Tag-Along zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="78d3a-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="78d3a-127">Audio hilft, andere Hinweise dafür bereitzustellen, wenn Benutzer Objekte im Tag-Along-Modus haben.</span><span class="sxs-lookup"><span data-stu-id="78d3a-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="78d3a-128">Audio sollte die Geschwindigkeit der Bewegung verstärken. Ein schneller Kopflauf sollte einen wahrnehmbareren Soundeffekt bieten, während das Gehen mit natürlicher Geschwindigkeit minimale oder gar keine Audioeffekte haben sollte.</span><span class="sxs-lookup"><span data-stu-id="78d3a-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="78d3a-129">Genau wie wirklich kopfgesperrte Inhalte können sich Tag-Along-Objekte als überwältigend oder verzehrend erweisen, wenn sie sich wild oder zu stark in der Ansicht des Benutzers bewegen.</span><span class="sxs-lookup"><span data-stu-id="78d3a-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="78d3a-130">Wenn ein Benutzer sich umsieht und dann schnell anhält, teilen seine Sinne ihm mit, dass er beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="78d3a-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="78d3a-131">Ihr Gleichgewicht informiert sie darüber, dass sich der Kopf nicht mehr drehen kann und dass sich die Welt nicht mehr drehen kann.</span><span class="sxs-lookup"><span data-stu-id="78d3a-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="78d3a-132">Wenn sich das Tag-Along jedoch fortbewegt, wenn der Benutzer beendet wurde, kann dies seine Sinne verwirren.</span><span class="sxs-lookup"><span data-stu-id="78d3a-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="78d3a-133">Ausfüllen und Tag-Along im MRTK (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="78d3a-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="78d3a-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts für das Verhalten beim Generieren und Tag-Along bereit.</span><span class="sxs-lookup"><span data-stu-id="78d3a-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="78d3a-135">Weisen Sie jedem Objekt das Skript "Scripts.cs" zu, um das Verhaltensverhalten zu erweitern und das Objekt immer auf Sie zu treffen.</span><span class="sxs-lookup"><span data-stu-id="78d3a-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="78d3a-136">Verwenden Sie das Skript RadialView.cs, um das Tag-Along-Verhalten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="78d3a-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="78d3a-137">Sie können verschiedene Optionen anpassen, z. B. Lerpingzeit, Entfernung und Grad.</span><span class="sxs-lookup"><span data-stu-id="78d3a-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="78d3a-138">MRTK – Radial View Solver</span><span class="sxs-lookup"><span data-stu-id="78d3a-138">MRTK - Radial View Solver</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [<span data-ttu-id="78d3a-139">MRTK – Skript "Scripts"</span><span class="sxs-lookup"><span data-stu-id="78d3a-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="78d3a-140">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="78d3a-140">See also</span></span>

* [<span data-ttu-id="78d3a-141">Cursor</span><span class="sxs-lookup"><span data-stu-id="78d3a-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="78d3a-142">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="78d3a-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="78d3a-143">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="78d3a-143">Button</span></span>](button.md)
* [<span data-ttu-id="78d3a-144">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="78d3a-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="78d3a-145">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="78d3a-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="78d3a-146">Manipulation</span><span class="sxs-lookup"><span data-stu-id="78d3a-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="78d3a-147">Handmenü</span><span class="sxs-lookup"><span data-stu-id="78d3a-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="78d3a-148">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="78d3a-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="78d3a-149">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="78d3a-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="78d3a-150">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="78d3a-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="78d3a-151">Tastatur</span><span class="sxs-lookup"><span data-stu-id="78d3a-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="78d3a-152">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="78d3a-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="78d3a-153">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="78d3a-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="78d3a-154">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="78d3a-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="78d3a-155">Shader</span><span class="sxs-lookup"><span data-stu-id="78d3a-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="78d3a-156">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="78d3a-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="78d3a-157">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="78d3a-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="78d3a-158">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="78d3a-158">Surface magnetism</span></span>](surface-magnetism.md)