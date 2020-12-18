---
title: 'MRTK-Einführung: Verwenden des Mixed Reality-Toolkits Unity für gängige räumliche Interaktionen (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)'
description: Verwenden des Mixed Reality-Toolkits Unity für grundlegende Interaktionen (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality-Toolkit, Windows Mixed Reality, Entwurf, Beispiel-App, Steuerelemente, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.localizationpriority: high
ms.openlocfilehash: 16087b69a45def0f496d2ded434458725474bd25
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010601"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="58f64-104">MRTK-Einführung Verwenden des Mixed Reality-Toolkits Unity für gängige räumliche Interaktionen</span><span class="sxs-lookup"><span data-stu-id="58f64-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="58f64-106">Erfahren Sie, wie Sie das MRTK nutzen, um einige der am häufigsten verwendeten Interaktionsmuster in Mixed Reality umzusetzen.</span><span class="sxs-lookup"><span data-stu-id="58f64-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="58f64-107">Wie lassen sich Eingabeinteraktionen im Unity-Editor simulieren?</span><span class="sxs-lookup"><span data-stu-id="58f64-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="58f64-108">Wie lässt sich ein Objekt greifen und bewegen?</span><span class="sxs-lookup"><span data-stu-id="58f64-108">How to grab and move an object?</span></span>
- <span data-ttu-id="58f64-109">Wie wird die Größe eines Objekts geändert?</span><span class="sxs-lookup"><span data-stu-id="58f64-109">How to resize an object?</span></span>
- <span data-ttu-id="58f64-110">Wie lässt sich ein Objekt präzise bewegen oder drehen?</span><span class="sxs-lookup"><span data-stu-id="58f64-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="58f64-111">Wie lässt man ein Objekt auf Eingabeereignisse reagieren?</span><span class="sxs-lookup"><span data-stu-id="58f64-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="58f64-112">Wie wird visuelles Feedback implementiert?</span><span class="sxs-lookup"><span data-stu-id="58f64-112">How to add visual feedback?</span></span>
- <span data-ttu-id="58f64-113">Wie kann Audiofeedback hinzugefügt werden?</span><span class="sxs-lookup"><span data-stu-id="58f64-113">How to add audio feedback?</span></span>
- <span data-ttu-id="58f64-114">Wie werden Prefabs für Schaltflächen im HoloLens 2-Stil verwendet?</span><span class="sxs-lookup"><span data-stu-id="58f64-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="58f64-115">Wie lässt man sich von einem Objekt folgen?</span><span class="sxs-lookup"><span data-stu-id="58f64-115">How to make an object follow you?</span></span>
- <span data-ttu-id="58f64-116">Wie erreicht man, dass ein Objekt sich einem zuwendet?</span><span class="sxs-lookup"><span data-stu-id="58f64-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="58f64-117">Dieser Artikel wurde mit den Änderungen im [MRTK v2.5.1-Release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1) aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="58f64-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="58f64-118">Alle Inhalte auf dieser Seite können im Unity-Editor mit der Eingabesimulation von MRTK getestet werden.</span><span class="sxs-lookup"><span data-stu-id="58f64-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="58f64-119">Wenn Sie dies noch nicht getan haben, befolgen Sie das [MRTK-Installationshandbuch (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html), um die neueste Version von MRTK zu installieren.</span><span class="sxs-lookup"><span data-stu-id="58f64-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="58f64-120">Wie lassen sich Eingabeinteraktionen im Unity-Editor simulieren?</span><span class="sxs-lookup"><span data-stu-id="58f64-120">How to simulate input interactions in Unity editor?</span></span>

<span data-ttu-id="58f64-121">MRTK unterstützt die Simulation von Eingaben im Editor.</span><span class="sxs-lookup"><span data-stu-id="58f64-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="58f64-122">Starten Sie Ihre Szene, indem Sie auf die Wiedergabeschaltfläche von Unity klicken, und verwenden Sie dann die folgenden Tasten, um Eingaben zu simulieren:</span><span class="sxs-lookup"><span data-stu-id="58f64-122">Run your scene by clicking Unity's play button, then use the following keys to simulate input:</span></span>
- <span data-ttu-id="58f64-123">Drücken Sie die Tasten W, A, S, D, um die Kamera zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="58f64-123">Press W, A, S, D keys to move the camera.</span></span>
- <span data-ttu-id="58f64-124">Halten Sie die rechte Maustaste gedrückt, und bewegen Sie die Maus, um sich umzusehen.</span><span class="sxs-lookup"><span data-stu-id="58f64-124">Hold the right mouse button and move the mouse to look around.</span></span>
- <span data-ttu-id="58f64-125">Drücken Sie die Leertaste (rechte Hand) oder die linke Umschalttaste (linke Hand), um die simulierten Hände aufzurufen</span><span class="sxs-lookup"><span data-stu-id="58f64-125">Press Space bar(Right hand) or left Shift key(Left hand) to bring up the simulated hands</span></span>
- <span data-ttu-id="58f64-126">Drücken Sie die Taste T oder Y, um simulierte Hände in der Ansicht zu halten.</span><span class="sxs-lookup"><span data-stu-id="58f64-126">Press T or Y keys to keep simulated hands in view</span></span>
- <span data-ttu-id="58f64-127">Drücken Sie Q oder E (horizontal) bzw. R oder F (vertikal), um die simulierten Hände zu drehen</span><span class="sxs-lookup"><span data-stu-id="58f64-127">Press Q or E(horizontal) / R or F(vertical) to rotate simulated hands</span></span>

<span data-ttu-id="58f64-128">Weitere Informationen zur Eingabesimulation finden Sie in der [MRTK-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span><span class="sxs-lookup"><span data-stu-id="58f64-128">You can learn more about Input Simulation in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span></span>

## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="58f64-129">Wie lässt sich ein Objekt greifen und bewegen?</span><span class="sxs-lookup"><span data-stu-id="58f64-129">How to grab and move an object?</span></span>

<span data-ttu-id="58f64-130">Fügen Sie die Skripts **ObjectManipulator.cs** und **NearInteractionGrabbable.cs** an, um ein Objekt greifbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="58f64-130">Attach the **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** scripts to make an object grabbable.</span></span> <span data-ttu-id="58f64-131">ObjectManipulator unterstützt sowohl nahe als auch ferne Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="58f64-131">ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="58f64-132">Sie können ein Objekt durch die Eingabe mittels artikuliertem Hand-Tracking (nah), Handstrahl (fern), den Strahl des Motion Controllers (fern), den Anvisier-Cursor von HoloLens 2 und Tippen in die Luft (fern) greifen und bewegen.</span><span class="sxs-lookup"><span data-stu-id="58f64-132">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), and HoloLens gaze cursor and air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="58f64-133">Wie wird die Größe eines Objekts geändert?</span><span class="sxs-lookup"><span data-stu-id="58f64-133">How to resize an object?</span></span>
<span data-ttu-id="58f64-134">**ObjectManipulator.cs** unterstützt die beidhändige Skalierung/Drehung.</span><span class="sxs-lookup"><span data-stu-id="58f64-134">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="58f64-135">Das Skript funktioniert mit verschiedenen Eingabetypen, wie z. B. der Handeingabe von HoloLens 2, der Eingabe durch Anvisieren und Gesten von HoloLens 1 und der Motion Controller-Eingabe des immersiven Headsets für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="58f64-135">The script works with various input types, such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="58f64-136">Weitere Informationen zum Objekt-Manipulator finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="58f64-136">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="58f64-137">Wie lässt sich ein Objekt präzise bewegen oder drehen?</span><span class="sxs-lookup"><span data-stu-id="58f64-137">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="58f64-138">Weisen Sie einem Objekt **BoundsControl.cs** zu, um Bounding Box (Begrenzungsrahmen) zu verwenden, wobei es sich um die Oberfläche zum Skalieren und Drehen von Objekten handelt.</span><span class="sxs-lookup"><span data-stu-id="58f64-138">Assign **BoundsControl.cs** to an object to use Bounding Box, which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="58f64-139">Standardmäßig werden blaue Ziehpunkte und Drahtlinien im Stil von HoloLens 1 angezeigt.</span><span class="sxs-lookup"><span data-stu-id="58f64-139">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="58f64-140">Um näherungsbasierte animierte Ziehpunkte im HoloLens 2-Stil zu verwenden, müssen Sie Prefabs und Materialien zuweisen.</span><span class="sxs-lookup"><span data-stu-id="58f64-140">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="58f64-141">Weitere Informationen zum Bounds-Steuerelement finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="58f64-141">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="58f64-142">Wie lässt man ein Objekt auf Eingabeereignisse reagieren?</span><span class="sxs-lookup"><span data-stu-id="58f64-142">How to make an object respond to input events?</span></span>
<span data-ttu-id="58f64-143">Weisen Sie einem Objekt **PointerHandler.cs** zu.</span><span class="sxs-lookup"><span data-stu-id="58f64-143">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="58f64-144">Im Inspektor können Sie die Ereignisse OnPointerDown(), OnPointerUp(), OnPointerClicked() und OnPointerDragged() verwenden. Um diese Ereignisse in einem Skript zu verwenden, implementieren Sie **IMixedRealityPointerHandler**.</span><span class="sxs-lookup"><span data-stu-id="58f64-144">In the inspector, you can use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="58f64-145">Weitere Informationen zum Eingabesystem finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="58f64-145">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="58f64-146">Wie wird visuelles Feedback implementiert?</span><span class="sxs-lookup"><span data-stu-id="58f64-146">How to add visual feedback?</span></span>
<span data-ttu-id="58f64-147">Weisen Sie einem Objekt **Interactable.cs** zu.</span><span class="sxs-lookup"><span data-stu-id="58f64-147">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="58f64-148">Fügen Sie im Inspektor Zielobjekte hinzu, und erstellen Sie ein neues Design.</span><span class="sxs-lookup"><span data-stu-id="58f64-148">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="58f64-149">Mithilfe der Designprofile von Interactable können Sie allen verfügbaren Interaktionszuständen auf einfache Weise visuelles Feedback hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58f64-149">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="58f64-150">Interactable stellt verschiedene Arten von Designs zur Verfügung, einschließlich des Shader-Designs, mit dem Sie die Eigenschaften des Shaders pro Interaktionszustand steuern können.</span><span class="sxs-lookup"><span data-stu-id="58f64-150">Interactable provides various types of themes including the shader theme, which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="58f64-151">Weitere Informationen zu Interactable finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="58f64-151">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="58f64-152">Ein weiterer wichtiger Baustein für visuelles Feedback ist der **MRTK-Standardshader**.</span><span class="sxs-lookup"><span data-stu-id="58f64-152">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="58f64-153">Mit dem MRTK-Standardshader können Sie auf einfache Weise visuelle Feedbackeffekte hinzufügen, wie das Licht beim Draufzeigen und Näherungslicht.</span><span class="sxs-lookup"><span data-stu-id="58f64-153">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="58f64-154">Da der MRTK-Standardshader weniger Berechnungen als der Unity-Standardshader ausführt, können Sie ein leistungsstarkes Verhalten erreichen.</span><span class="sxs-lookup"><span data-stu-id="58f64-154">Since MRTK Standard shader performs less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="58f64-155">Erstellen Sie ein neues Material, und wählen Sie den Shader „Mixed Reality Toolkit > Standard“ aus.</span><span class="sxs-lookup"><span data-stu-id="58f64-155">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="58f64-156">Alternativ können Sie eins der vorhandenen Materialien auswählen, die den MRTK-Standardshader verwenden.</span><span class="sxs-lookup"><span data-stu-id="58f64-156">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="58f64-157">Weitere Informationen zum MRTK-Standardshader finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="58f64-157">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="58f64-158">Wie kann Audiofeedback hinzugefügt werden?</span><span class="sxs-lookup"><span data-stu-id="58f64-158">How to add audio feedback?</span></span>
<span data-ttu-id="58f64-159">Fügen Sie einem Objekt **AudioSource** hinzu.</span><span class="sxs-lookup"><span data-stu-id="58f64-159">Add **AudioSource** to an object.</span></span> <span data-ttu-id="58f64-160">Weisen Sie dann in den Skripts, die Eingabeereignisse verfügbar machen (z. B. Interactable.cs oder PointerHandler.cs) das Objekt mit AudioSource dem Ereignis zu, und wählen Sie **AudioSource.PlayOneShot()** aus.</span><span class="sxs-lookup"><span data-stu-id="58f64-160">Then, in the scripts that expose input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="58f64-161">Sie können eigene Audioclips verwenden oder einen aus den Audioressourcen des MRTK auswählen.</span><span class="sxs-lookup"><span data-stu-id="58f64-161">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="58f64-162">Wie werden Prefabs für Schaltflächen im HoloLens 2-Stil verwendet?</span><span class="sxs-lookup"><span data-stu-id="58f64-162">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="58f64-163">MRTK bietet verschiedene Arten von Schaltflächen im Shellformat (OS) von HoloLens 2, einschließlich visuellem Feedback wie Näherungslicht, Stauchungsrahmen und einem Ripple-Effekt auf der Schaltflächen-Oberfläche, die das Vertrauen des Benutzers verbessern.</span><span class="sxs-lookup"><span data-stu-id="58f64-163">MRTK provides various types of HoloLens 2's shell (OS) style buttons, including visual feedback like proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="58f64-164">Legen Sie eins der **Prefabs für eine drückbare Schaltfläche im HoloLens 2-Stil** per Drag & Drop in Ihrer Szene ab.</span><span class="sxs-lookup"><span data-stu-id="58f64-164">Drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="58f64-165">Das Prefab verwendet Interactable.cs, das oben vorgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="58f64-165">The prefab uses Interactable.cs introduced above.</span></span> <span data-ttu-id="58f64-166">Sie können in Interactable verfügbar gemachte Ereignisse wie OnClick() verwenden, um Aktionen auszulösen.</span><span class="sxs-lookup"><span data-stu-id="58f64-166">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="58f64-167">Weitere Informationen zu Schaltflächen-Prefabs finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="58f64-167">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="58f64-168">Wie lässt man sich von einem Objekt folgen?</span><span class="sxs-lookup"><span data-stu-id="58f64-168">How to make an object follow you?</span></span>
<span data-ttu-id="58f64-169">Weisem Sie einem Objekt das Skript **RadialView.cs** oder **Follow.cs** zu.</span><span class="sxs-lookup"><span data-stu-id="58f64-169">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="58f64-170">Es ist Teil der Solver-Reihe von Skripts, die Ihnen verschiedene Arten von Objektpositionierung im 3D-Raum ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="58f64-170">It's part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="58f64-171">**SolverHandler.cs** wird automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="58f64-171">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="58f64-172">Unten finden Sie ein Beispiel der RadialView-Konfiguration, um ein „Hinterhertrotten“-Folgeverhalten zu erreichen, ähnlich wie das Startmenü in der HoloLens-Shell.</span><span class="sxs-lookup"><span data-stu-id="58f64-172">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="58f64-173">Sie können die minimale/maximale Entfernung und den minimalen/maximalen Ansichtswinkel angeben.</span><span class="sxs-lookup"><span data-stu-id="58f64-173">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="58f64-174">Im Beispiel unten ist die Positionierung des Objekts zwischen 0,4 m und 0,8 m in einem Bereich von 15 ° dargestellt.</span><span class="sxs-lookup"><span data-stu-id="58f64-174">The example below shows positioning the object between 0.4 m and 0.8-m range within 15°.</span></span> <span data-ttu-id="58f64-175">Passen Sie die Werte für die Lerp-Zeit an, um das Aktualisieren der Position schneller oder langsamer erfolgen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="58f64-175">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="58f64-176">Weitere Informationen zu Solvern finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="58f64-176">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="58f64-177">Wie erreicht man, dass ein Objekt sich einem zuwendet?</span><span class="sxs-lookup"><span data-stu-id="58f64-177">How to make an object face you?</span></span>
<span data-ttu-id="58f64-178">Weisen Sie einem Objekt das **Billboard.cs**-Skript zu.</span><span class="sxs-lookup"><span data-stu-id="58f64-178">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="58f64-179">Das Objekt ist Ihnen immer zugewendet, unabhängig von Ihrer Position.</span><span class="sxs-lookup"><span data-stu-id="58f64-179">It will always face you, whatever your position.</span></span> <span data-ttu-id="58f64-180">Sie können die Pivotachsenoption angeben.</span><span class="sxs-lookup"><span data-stu-id="58f64-180">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="58f64-181">Sind Sie bereit, beeindruckende Erlebnisse für Mixed Reality zu gestalten?</span><span class="sxs-lookup"><span data-stu-id="58f64-181">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="58f64-182">Besuchen Sie die unten angegebenen Seiten, und erfahren Sie mehr über MRTK und Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="58f64-182">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="58f64-183">Informationen zum Autor</span><span class="sxs-lookup"><span data-stu-id="58f64-183">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="58f64-184"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="58f64-184"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="58f64-185">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="58f64-185">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="next-development-checkpoint"></a><span data-ttu-id="58f64-186">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="58f64-186">Next Development Checkpoint</span></span>

<span data-ttu-id="58f64-187">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="58f64-187">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="58f64-188">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="58f64-188">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="58f64-189">Kamera</span><span class="sxs-lookup"><span data-stu-id="58f64-189">Camera</span></span>](camera-in-unity.md)

<span data-ttu-id="58f64-190">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="58f64-190">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="58f64-191">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="58f64-191">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="58f64-192">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="58f64-192">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="58f64-193">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="58f64-193">See also</span></span>
* [<span data-ttu-id="58f64-194">MRTK – Installationshandbuch (GitHub)</span><span class="sxs-lookup"><span data-stu-id="58f64-194">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="58f64-195">Mixed Reality Toolkit-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="58f64-195">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="58f64-196">MRTK-Dokumentationsportal (GitHub)</span><span class="sxs-lookup"><span data-stu-id="58f64-196">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="58f64-197">Portierungsrichtlinie HoloToolkit zu MRTK</span><span class="sxs-lookup"><span data-stu-id="58f64-197">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
