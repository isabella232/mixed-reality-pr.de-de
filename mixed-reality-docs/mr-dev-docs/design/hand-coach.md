---
title: Hand Coach
description: Hier erfahren Sie, wie 3D-Hände mit hand-Hand ausgelöst werden, wenn das System die Hände des Benutzers nicht erkennt, um ihnen zu helfen.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, Design, Handfasching, immersives Headset, MRTK, Hände, Helfende Hände, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0fe0d87e26d06838c0d1b7935573d9bd8ce258ee
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600429"
---
# <a name="hand-coach"></a><span data-ttu-id="28c31-104">Hand Coach</span><span class="sxs-lookup"><span data-stu-id="28c31-104">Hand coach</span></span>

![Beispiel: Handschn.](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="28c31-106">Handauslöser löst 3D-modellierte Hände aus, wenn das System die Hände des Benutzers nicht erkennt.</span><span class="sxs-lookup"><span data-stu-id="28c31-106">Hand coach triggers 3D modeled hands when the system doesn't detect the user’s hands.</span></span> <span data-ttu-id="28c31-107">Dieses Feature ist eine "Unterrichtskomponente", die den Benutzer bei der Anleitung unterstützt, wenn die Geste nicht vermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="28c31-107">This feature is a “teaching” component that helps guide the user when the gesture hasn't been taught.</span></span> <span data-ttu-id="28c31-108">Wenn Benutzer die angegebene Geste für einen Bestimmten nicht durchgeführt haben, werden die Hände mit einer Verzögerung in die Schleife schleife.</span><span class="sxs-lookup"><span data-stu-id="28c31-108">If users haven't done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="28c31-109">Das Hand-Brillen-Paar kann verwendet werden, um das Drücken einer Schaltfläche oder das Aufnehmen eines Hologramms zu darstellen.</span><span class="sxs-lookup"><span data-stu-id="28c31-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="28c31-110">Handhand-2016</span><span class="sxs-lookup"><span data-stu-id="28c31-110">Hand coach provided</span></span>

<span data-ttu-id="28c31-111">Das aktuelle Interaktionsmodell stellt eine Vielzahl von Gestensteuerelementen dar, z. B. Scrollen, Fernauswahl und Tippen in der Nähe.</span><span class="sxs-lookup"><span data-stu-id="28c31-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="28c31-112">Im Folgenden finden Sie eine vollständige Liste der vorhandenen Handgesten, die im<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK bereitgestellt werden:</a></span><span class="sxs-lookup"><span data-stu-id="28c31-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="28c31-113">![Beispiel für Near Select](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="28c31-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="28c31-114">**Beispiel für Near Select – Used zeigt, wie Schaltflächen ausgewählt oder interaktionsfähige Objekte geschlossen werden.**</span><span class="sxs-lookup"><span data-stu-id="28c31-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28c31-115">![Beispiel für Tippen in die Luft](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="28c31-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="28c31-116">**Beispiel für Tippen in die Luft– Wird verwendet, um zu zeigen, wie weit entfernte Objekte ausgewählt werden.**</span><span class="sxs-lookup"><span data-stu-id="28c31-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28c31-117">![Beispiel für "Verschieben"](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="28c31-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="28c31-118">**Beispiel für das Verschieben eines Objekts im Raum: Wird verwendet, um zu zeigen, wie ein Hologramm in den Raum bewegt wird**</span><span class="sxs-lookup"><span data-stu-id="28c31-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28c31-119">![Beispiel für "Rotieren"](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="28c31-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="28c31-120">**Beispiel für Rotate-Used, wie Hologramme oder Objekte gedreht werden**</span><span class="sxs-lookup"><span data-stu-id="28c31-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="28c31-121">![Beispiel für Skalierung](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="28c31-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="28c31-122">**Beispiel für Skalierung: Wird verwendet, um zu zeigen, wie Hologramme so bearbeitet werden, dass sie größer oder kleiner sind**</span><span class="sxs-lookup"><span data-stu-id="28c31-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28c31-123">![Beispiel für "Palm Up"](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="28c31-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="28c31-124">**Beispiel für "Palm up" – Empfohlene Verwendung zum Anzeigen von Handmenüs**</span><span class="sxs-lookup"><span data-stu-id="28c31-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28c31-125">![Beispiel für HandFlip](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="28c31-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="28c31-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span><span class="sxs-lookup"><span data-stu-id="28c31-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="28c31-127">![Beispiel für Scrollen](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="28c31-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="28c31-128">**Beispiel für "Scrollen": Wird zum Scrollen einer Liste oder eines langen Dokuments verwendet**</span><span class="sxs-lookup"><span data-stu-id="28c31-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="28c31-129">Entwurfskonzepte</span><span class="sxs-lookup"><span data-stu-id="28c31-129">Design concepts</span></span>

<span data-ttu-id="28c31-130">Für Hololens2 haben wir Handinteraktionen basierend auf instinktiven und natürlichen Handgesten entworfen.</span><span class="sxs-lookup"><span data-stu-id="28c31-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="28c31-131">Wir sind der Meinung, dass diese für die meisten Benutzer intuitiv sind, sodass wir keine dedizierten Lernmomente für Gesten erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="28c31-131">We believe these to be intuitive to most users, so we didn't create dedicated gesture learning moments.</span></span> <span data-ttu-id="28c31-132">Stattdessen haben wir die Handarbeit erstellt, um Benutzern zu helfen, mehr über diese Gesten zu erfahren, wenn sie hängen bleiben oder mit Hologramminteraktionen nicht vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="28c31-132">Instead, we created the hand coach to help users learn about these gestures if they get stuck or are unfamiliar with hologram interactions.</span></span> <span data-ttu-id="28c31-133">Ohne einen Lernmoment haben wir uns davon aus gefühlt, dass es die beste Option wäre, Benutzern zu zeigen, wie sie eine Aktion ausführen, indem sie demonstriert wird.</span><span class="sxs-lookup"><span data-stu-id="28c31-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="28c31-134">Wir haben festgestellt, dass Benutzer die Geste herausfinden konnten, aber ein wenig Anleitungen benötigten.</span><span class="sxs-lookup"><span data-stu-id="28c31-134">We found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="28c31-135">Wenn wir feststellen, dass ein Benutzer für einen bestimmten Zeitraum nicht mit einem Objekt interagiert, wird ein Hand-2016 ausgelöst, das die richtige Hand- und Fingerplatzierung zeigt.</span><span class="sxs-lookup"><span data-stu-id="28c31-135">If we detect a user doesn't interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="28c31-136">Intuitiv</span><span class="sxs-lookup"><span data-stu-id="28c31-136">Intuitive</span></span>

<span data-ttu-id="28c31-137">Beim Animieren der Hände sollte dies offensichtlich sein und keine Verwirrung verursachen.</span><span class="sxs-lookup"><span data-stu-id="28c31-137">When animating hands, it should be obvious and shouldn't cause any confusion.</span></span> <span data-ttu-id="28c31-138">Die Handanimation ist eine Darstellung der Geste, die Sie dem Benutzer zum Verstehen auffordern möchten.</span><span class="sxs-lookup"><span data-stu-id="28c31-138">The hand animation is a representation of the gesture you're trying to prompt the user to understand.</span></span> 

<span data-ttu-id="28c31-139">Wenn ein Benutzer z. B. eine Schaltfläche drücken soll, wird eine Hand zum Drücken einer Schaltfläche ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="28c31-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="28c31-140">![Beispiel: Handschnippen in der Nähe von Tap](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="28c31-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="28c31-141">*HandGewinde zeigt das Tippen auf ein Gem in der Nähe*</span><span class="sxs-lookup"><span data-stu-id="28c31-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="28c31-142">Handskalieren</span><span class="sxs-lookup"><span data-stu-id="28c31-142">Hand scale</span></span>

<span data-ttu-id="28c31-143">Wir haben verschiedene Handgrößen mit den Benutzeroberflächenmenüs getestet und dabei den Eindruck bekommen, dass die Größe der Hände ein berohendes Gefühl war, wenn die Hände groß sind.</span><span class="sxs-lookup"><span data-stu-id="28c31-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling.</span></span> <span data-ttu-id="28c31-144">Wenn sie zu klein waren, war es schwierig, die Geste zu erkennen und zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="28c31-144">If they were too small, it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="28c31-145">**Sprachüber und Hände**</span><span class="sxs-lookup"><span data-stu-id="28c31-145">**Voice over and hands**</span></span>

<span data-ttu-id="28c31-146">Erwarten Sie nicht, dass Benutzer über Voice over auf eine Reihe von Anweisungen lauschen und unterschiedliche Anweisungen über Handarbeit ansehen können.</span><span class="sxs-lookup"><span data-stu-id="28c31-146">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="28c31-147">Sequenzieren Sie Ihre Anweisungen, um Benutzern zu helfen, sich zu konzentrieren und um ihre Aufmerksamkeit zu konkurrieren, um die sensorische Überlastung zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="28c31-147">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="28c31-148">Kann ich meine eigenen erstellen?</span><span class="sxs-lookup"><span data-stu-id="28c31-148">Can I create my own?</span></span>

<span data-ttu-id="28c31-149">Ja!</span><span class="sxs-lookup"><span data-stu-id="28c31-149">Yes!</span></span> <span data-ttu-id="28c31-150">Wir empfehlen Ihnen, Ihre eigene einzigartige Geste für Ihr Spiel zu erstellen und einen Beitrag zur Community zu leisten!</span><span class="sxs-lookup"><span data-stu-id="28c31-150">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="28c31-151">Wir haben eine Maya-Datei mit einer manipulierten Hand bereitgestellt, die für Ihre App verwendet werden kann. Diese kann hier heruntergeladen <a href="files/HandCoach_MRTK.zip">werden: Download</a> HandCoach_MRTK.zip</span><span class="sxs-lookup"><span data-stu-id="28c31-151">We've provided a Maya file of a Rigged hand that can be used for your app, which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip </a></span></span>

<span data-ttu-id="28c31-152">![Beispiel für animierte Hände in Maya](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="28c31-152">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="28c31-153">*Beispiel für animiertes Hand-Poking eines Felds in Maya*</span><span class="sxs-lookup"><span data-stu-id="28c31-153">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="28c31-154">**Empfohlenes Erstellungstool**</span><span class="sxs-lookup"><span data-stu-id="28c31-154">**Recommended authoring tool**</span></span>

<span data-ttu-id="28c31-155">Unter den 3D-Frauen entscheiden sich viele für die Verwendung der Maya von Autodesk, die [HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) verwenden kann, um die Art und Weise zu transformieren, wie Ressourcen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="28c31-155">Among 3D artists, many choose to use [Autodesk’s Maya, which can use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="28c31-156">Die bereitgestellte Hands-Datei ist eine Maya-Binärdatei, daher wird empfohlen, Maya zum Animieren und Exportieren der Hände zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="28c31-156">The hands file provided is a Maya Binary File, so it's recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="28c31-157">Wenn Sie lieber ein anderes 3D-Programm verwenden möchten, finden Sie hier eine <b>. FBX:</b> <a href="files/HandCoachMRTK_FBX.zip"> Laden Sie HandCoachMRTK_FBX.zip </a> herunter, um Ihr eigenes Controllersetup zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="28c31-157">If you prefer to use another 3D program, here's a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> Download HandCoachMRTK_FBX.zip </a> to create your own controller setup.</span></span> 

<span data-ttu-id="28c31-158">Wenn Sie die heruntergeladene Maya-Handdatei verwenden, wird empfohlen, die Hände in Unity auf 0,6 herunterskalieren.</span><span class="sxs-lookup"><span data-stu-id="28c31-158">If using the downloadable maya Hand File provided, it's suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="28c31-159">![Beispiel: Hand-1-5-5-1-1-4-](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="28c31-159">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="28c31-160">*Verfälschte Hände*</span><span class="sxs-lookup"><span data-stu-id="28c31-160">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="28c31-161">Technische Spezifikationen</span><span class="sxs-lookup"><span data-stu-id="28c31-161">Technical Specs</span></span>

*   <span data-ttu-id="28c31-162">Die zweihändige Datei ist im Maya Ascii-Format verfügbar.</span><span class="sxs-lookup"><span data-stu-id="28c31-162">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="28c31-163">Die rechte und linke Hand ist im Maya-Binärformat verfügbar.</span><span class="sxs-lookup"><span data-stu-id="28c31-163">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="28c31-164">Legen Sie Ihre Maya-Datei auf 24 FPS fest.</span><span class="sxs-lookup"><span data-stu-id="28c31-164">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="28c31-165">In der Datei gibt es eine linke und rechte Hand, die für zwei händige oder einhändige Gesten verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="28c31-165">Within the file, there's a left and right hand, which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="28c31-166">Die rechte Seite ist standardmäßig nur sichtbar.</span><span class="sxs-lookup"><span data-stu-id="28c31-166">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="28c31-167">Es wird empfohlen, einen Puffer von ca. 10 Frames am Anfang und Ende für Einblendungen zu belassen.</span><span class="sxs-lookup"><span data-stu-id="28c31-167">It's suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="28c31-168">Wenn Sie ein Objekt mit einem angegebenen Ziel animieren, wird die bewährte Methode zum Animieren in ein Standardfeld oder NULL verwendet.</span><span class="sxs-lookup"><span data-stu-id="28c31-168">If animating an object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="28c31-169">Wenn die Hand ein physisches Objekt animiert, z. B. ein Feld, ist es eine bewährte Methode, die Übersetzung in Maya nicht zu animieren, sondern darauf zu warten, sie in Unity oder im Code zu animieren.</span><span class="sxs-lookup"><span data-stu-id="28c31-169">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="28c31-170">Die sichtbare Animation sollte 1,5 Sekunden beträgt, damit aussagekräftige Informationen übermittelt werden können.</span><span class="sxs-lookup"><span data-stu-id="28c31-170">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="28c31-171">Wenn Sie mit Ihrer Animation zufrieden sind:</span><span class="sxs-lookup"><span data-stu-id="28c31-171">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="28c31-172">Auswählen aller Fugen und Backen von Keyframes</span><span class="sxs-lookup"><span data-stu-id="28c31-172">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="28c31-173">Löschen der Controller, Auswählen der Fugen und Gitter und Exportieren als FBX</span><span class="sxs-lookup"><span data-stu-id="28c31-173">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="28c31-174">Wenn mehrere Animationen enthalten sind, können Sie den integrierten Game Exporter von Maya verwenden: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="28c31-174">If there are Multiple Animations, you can use Maya’s built-in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="28c31-175">Exportieren aus Maya</span><span class="sxs-lookup"><span data-stu-id="28c31-175">Exporting from Maya</span></span>

<span data-ttu-id="28c31-176">Nachdem Sie mit Ihrer Animation zufrieden sind</span><span class="sxs-lookup"><span data-stu-id="28c31-176">After you're satisfied with your animation</span></span>
* <span data-ttu-id="28c31-177">Alle Fugen auswählen: Wählen Sie > Hierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="28c31-177">Select all joints: Select > Hierarchy</span></span>

     ![Beispiel: Hierarchie im Menü](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="28c31-179">Baking ihrer Animation: Wechseln Sie zu Animation > Key > Bake Animation</span><span class="sxs-lookup"><span data-stu-id="28c31-179">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![Beispiel: Speicherort des Bake-Animationsmenüs](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="28c31-181">Löschen Sie das Controllergerät: Outliner > MainR_Grp oder MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="28c31-181">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![Beispiel: Position des Controllermenüs](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="28c31-183">Als FBX exportieren: Wählen Sie JNT + Mesh: File > Export Selection (Optionsfeld) > Export Selection (Auswahl exportieren) aus.</span><span class="sxs-lookup"><span data-stu-id="28c31-183">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![Beispiel: Exportieren des Menüspeicherorts für die Auswahl](images/HandCoach/OptionBox.png)<br>

     ![Beispiel: Menüposition](images/HandCoach/SelectionExport.png)<br>

     ![Beispiel: Speicherort des Menüs "Optionen exportieren"](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="28c31-187">Wenn Sie als FBX exportieren und in Unity importieren, skalieren Sie die Hände auf 0,6 herunter.</span><span class="sxs-lookup"><span data-stu-id="28c31-187">When exporting as an FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="28c31-188">Wir haben festgestellt, dass dies ein perfektes Gleichgewicht für die Anzeige der Hände war.</span><span class="sxs-lookup"><span data-stu-id="28c31-188">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="28c31-189">![Beispiel: Unity-Einstellungen](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="28c31-189">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="28c31-190">*Unity-Einstellungen für HandCoach_R prefab in MRTK*</span><span class="sxs-lookup"><span data-stu-id="28c31-190">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="28c31-191">Implementieren von Händen in Ihr Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="28c31-191">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="28c31-192">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="28c31-192">Best practices</span></span>

* <span data-ttu-id="28c31-193">Es wird empfohlen, die Hände in Unity auf 0,6 herunterskalieren.</span><span class="sxs-lookup"><span data-stu-id="28c31-193">It's suggested to scale down the hands in unity to 0.6</span></span>
* <span data-ttu-id="28c31-194">Die Hände sollten zweimal abgespielt werden, und wenn sie nicht abgeschlossen sind, wird kontinuierlich eine Schleife durchgeführt, bis die Geste abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="28c31-194">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="28c31-195">Die Hände sollten zweimal in einer Schleife sein, um sicherzustellen, dass der Benutzer Zeit hatte, sich zu registrieren und die Geste zu sehen.</span><span class="sxs-lookup"><span data-stu-id="28c31-195">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="28c31-196">Die Hände sollten zwischen Schleifen ein- und ausblenden.</span><span class="sxs-lookup"><span data-stu-id="28c31-196">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="28c31-197">Wenn die Hände des Benutzers von HL2-Kameras angezeigt werden, benutzer jedoch nicht die für sie benötigte Interaktion tun, werden die Hände nach 10 Sekunden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="28c31-197">If user’s hands are visible by HL2 cameras but users aren't doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="28c31-198">Wenn die Hände des Benutzers für HL2-Kameras NICHT sichtbar sind, werden die Hände nach 5 Sekunden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="28c31-198">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="28c31-199">Wenn die Hände des Benutzers von HL2-Kameras in der Mitte der Animation sichtbar nachverfolgt werden, wird die Animation abgeschlossen und ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="28c31-199">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="28c31-200">Wenn Sie Voice over verwenden, empfehlen wir, dass dies der Geste der Hand entspricht.</span><span class="sxs-lookup"><span data-stu-id="28c31-200">If you're including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="28c31-201">Wenn Sie die Hände mindestens einmal gelernt haben, wiederholen Sie die Geste nur, wenn erkannt wird, dass der Benutzer hängen bleibt.</span><span class="sxs-lookup"><span data-stu-id="28c31-201">If you've taught the hands at least once, only repeat the gesture if it's detected that the user is stuck.</span></span>
*   <span data-ttu-id="28c31-202">Wenn bestimmte Finger-/Handpositionen wichtig sind, stellen Sie sicher, dass Benutzer diese Nuancen in der Animation deutlich erkennen können.</span><span class="sxs-lookup"><span data-stu-id="28c31-202">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="28c31-203">Versuchen Sie, die Hände zu verfingen, damit die wichtigsten Teile deutlich sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="28c31-203">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="28c31-204">Wenn Sie eine Verzerrung an den Händen bemerken, müssen Sie zu Den Qualitätseinstellungen von Unity wechseln, um die Anzahl der Brüche zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="28c31-204">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the number of bones.</span></span> 
 <span data-ttu-id="28c31-205">Wechseln Sie zur Unity-Seite Edit > Project Settings > Quality > Other > Blend Weights (Bearbeiten >-Projekteinstellungen > Andere > Mischungsgewichtungen).</span><span class="sxs-lookup"><span data-stu-id="28c31-205">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="28c31-206">Stellen Sie sicher, dass "4 1000" ausgewählt sind, um Smooth Joints (Smooth Joints) zu sehen.</span><span class="sxs-lookup"><span data-stu-id="28c31-206">Make sure "4 bones" are selected to see Smooth Joints.</span></span>

   ![Beispiel: Fenster "Projekteinstellungen"](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a><span data-ttu-id="28c31-208">Was Sie vermeiden sollten</span><span class="sxs-lookup"><span data-stu-id="28c31-208">What to avoid</span></span>

* <span data-ttu-id="28c31-209">Skalieren der Hände zu groß</span><span class="sxs-lookup"><span data-stu-id="28c31-209">Scaling the Hands too large</span></span>
* <span data-ttu-id="28c31-210">Platzieren der Hände zu nah am Benutzer</span><span class="sxs-lookup"><span data-stu-id="28c31-210">placing the Hands too close to the user</span></span>
* <span data-ttu-id="28c31-211">Die Hände sollten nur einmal gelernt werden.</span><span class="sxs-lookup"><span data-stu-id="28c31-211">Hands should only be taught once.</span></span> <span data-ttu-id="28c31-212">Over teaching can cause confusion and messiness</span><span class="sxs-lookup"><span data-stu-id="28c31-212">Over teaching can cause confusion and messiness</span></span>
* <span data-ttu-id="28c31-213">Laden Sie das neueste MRTK hier herunter, um es in Unity zu installieren: https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="28c31-213">Bringing it into Unity, download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
  * <span data-ttu-id="28c31-214">Material: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="28c31-214">Material: Teaching_Hand2</span></span>
  * <span data-ttu-id="28c31-215">Skripts: Weitere Informationen finden Sie in den MRTK-Richtlinien für <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> MRTK-Handbücher. </a></span><span class="sxs-lookup"><span data-stu-id="28c31-215">Scripts: Refer to MRTK guidelines for <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> MRTK hand coach </a></span></span>
  * <span data-ttu-id="28c31-216">Projektspezifische Einstellung</span><span class="sxs-lookup"><span data-stu-id="28c31-216">Per- project setting</span></span>
    * <span data-ttu-id="28c31-217">Szene auf UWP festgelegt: Anweisungen finden Sie unter [Konfigurieren des Unity-Projekts](../develop/unity/Configure-Unity-Project.md) für Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="28c31-217">Scene set to UWP: Instruction can be found on the [Configure Unity Project](../develop/unity/Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="28c31-218">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="28c31-218">See also</span></span>

* [<span data-ttu-id="28c31-219">Interaktionsprinzipien</span><span class="sxs-lookup"><span data-stu-id="28c31-219">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="28c31-220">Erstellungsprozess für Ressourcen</span><span class="sxs-lookup"><span data-stu-id="28c31-220">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="28c31-221">Gesten</span><span class="sxs-lookup"><span data-stu-id="28c31-221">Gestures</span></span>](./interaction-fundamentals.md)
* [<span data-ttu-id="28c31-222">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="28c31-222">Install the Tools</span></span>](../develop/install-the-tools.md)
* [<span data-ttu-id="28c31-223">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="28c31-223">Configure Unity Project</span></span>](../develop/unity/Configure-Unity-Project.md)
* [<span data-ttu-id="28c31-224">Unity-Entwicklung – Übersicht</span><span class="sxs-lookup"><span data-stu-id="28c31-224">Unity development overview</span></span>](../develop/unity/unity-development-overview.md)
* [<span data-ttu-id="28c31-225">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="28c31-225">MRTK 101</span></span>](/windows/mixed-reality/mrtk-unity/)