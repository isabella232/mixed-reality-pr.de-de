---
title: 'Lernprogramme für räumliche Audiodaten: 2. Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten'
description: Fügen Sie dem Projekt eine Schaltfläche hinzu, und räumlichen Sie die Sound der Schaltflächen Interaktion.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer, Prefabs, volumekurve
ms.openlocfilehash: eb550c3127e13926d73428b337abfd7cf9872eb7
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678189"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="47cfd-105">Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten</span><span class="sxs-lookup"><span data-stu-id="47cfd-105">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="47cfd-106">Ziele</span><span class="sxs-lookup"><span data-stu-id="47cfd-106">Objectives</span></span>
<span data-ttu-id="47cfd-107">In diesem zweiten Kapitel des Moduls "Spatial AUDIOMODULE" der hololens 2-Tutorials werden folgende Schritte durchgehen:</span><span class="sxs-lookup"><span data-stu-id="47cfd-107">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="47cfd-108">Hinzufügen einer Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="47cfd-108">Add a button</span></span>
* <span data-ttu-id="47cfd-109">Schaltflächen Klick-Sounds spatialisieren</span><span class="sxs-lookup"><span data-stu-id="47cfd-109">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="47cfd-110">Hinzufügen einer Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="47cfd-110">Add a button</span></span>
<span data-ttu-id="47cfd-111">Wählen Sie im **Projekt** Bereich **Assets** aus, und geben Sie "PressableButtonHoloLens2" in die Suchleiste ein:</span><span class="sxs-lookup"><span data-stu-id="47cfd-111">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![Schaltflächen vorfab in Assets](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="47cfd-113">Bei der Prefab-Schaltfläche handelt es sich um den durch ein blaues Symbol dargestellten Eintrag anstelle eines weißen Symbols.</span><span class="sxs-lookup"><span data-stu-id="47cfd-113">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="47cfd-114">Ziehen Sie das präfab mit dem Namen **PressableButtonHoloLens2** in den Bereich **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="47cfd-114">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="47cfd-115">Legen Sie im **Inspektor** -Bereich für die neue Schaltfläche die **Positions** Eigenschaft auf (0,-0,4, 2) fest, damit Sie vor dem Benutzer angezeigt wird, wenn die Anwendung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="47cfd-115">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="47cfd-116">Die **Transformations** Komponente der Schaltfläche sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="47cfd-116">The **Transform** component of the button will look like this:</span></span>

![Schaltflächen Transformation](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="47cfd-118">Schaltflächen-Feedback spatialisieren</span><span class="sxs-lookup"><span data-stu-id="47cfd-118">Spatialize button feedback</span></span>
<span data-ttu-id="47cfd-119">In diesem Schritt Stufen Sie das Audiofeedback für die Schaltfläche ein.</span><span class="sxs-lookup"><span data-stu-id="47cfd-119">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="47cfd-120">Verwandte Entwurfsvorschläge finden Sie unter [Spatial Sound Design](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="47cfd-120">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="47cfd-121">Im Bereich **Audiomixer** definieren Sie Ziele, die als **mixergruppen** bezeichnet werden, für die Audiowiedergabe aus **audioquellkomponenten** .</span><span class="sxs-lookup"><span data-stu-id="47cfd-121">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="47cfd-122">Öffnen Sie den Bereich **Audiomixer** in der Menüleiste mithilfe von **Windows > Audio> Audiomixer** .</span><span class="sxs-lookup"><span data-stu-id="47cfd-122">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="47cfd-123">Erstellen Sie einen **Mixer** , indem Sie auf "+" neben " **Mixer**" klicken.</span><span class="sxs-lookup"><span data-stu-id="47cfd-123">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="47cfd-124">Der neue Mixer enthält eine Standard **Gruppe** namens **Master**.</span><span class="sxs-lookup"><span data-stu-id="47cfd-124">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="47cfd-125">Ihr **Mischbereich** sieht nun wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="47cfd-125">Your **Mixer** pane will now look like this:</span></span>

![Mischbereich mit dem ersten Mixer](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="47cfd-127">Bis der Reverb in [Kapitel 5](unity-spatial-audio-ch5.md)aktiviert ist, zeigt die Volume-Verbrauchseinheit des Mischers keine Aktivitäten für Sounds an, die über den Microsoft spatializer abgespielt werden.</span><span class="sxs-lookup"><span data-stu-id="47cfd-127">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="47cfd-128">Klicken Sie im Bereich **Hierarchie** auf die **PressableButtonHoloLens2** .</span><span class="sxs-lookup"><span data-stu-id="47cfd-128">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="47cfd-129">Im **Inspektor** -Bereich:</span><span class="sxs-lookup"><span data-stu-id="47cfd-129">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="47cfd-130">Suchen der **audioquellkomponente**</span><span class="sxs-lookup"><span data-stu-id="47cfd-130">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="47cfd-131">Klicken Sie für die **Output** -Eigenschaft auf die Auswahl, und wählen Sie Ihren Mixer aus.</span><span class="sxs-lookup"><span data-stu-id="47cfd-131">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="47cfd-132">Aktivieren Sie das Kontrollkästchen **spatialize** .</span><span class="sxs-lookup"><span data-stu-id="47cfd-132">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="47cfd-133">Verschieben Sie den Schieberegler **räumlicher Blend** in 3D (1).</span><span class="sxs-lookup"><span data-stu-id="47cfd-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="47cfd-134">In Versionen von Unity vor 2019 befindet sich das Kontrollkästchen "spatialize" am unteren Rand des **inspektorbereichs** für die **Audioquelle**.</span><span class="sxs-lookup"><span data-stu-id="47cfd-134">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="47cfd-135">Nachdem diese Änderungen vorgenommen wurden, sieht die **audioquellkomponente** Ihrer **PressableButtonHoloLens2** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="47cfd-135">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![Schaltflächen-Audioquelle](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="47cfd-137">Wenn Sie **räumliche Blend** in 1 (3D) verschieben, ohne das **spatialize** -Kontrollkästchen zu aktivieren, verwendet Unity den Schwenk räumlichen spatializer anstelle von **Microsoft spatializer** mit HRTFs.</span><span class="sxs-lookup"><span data-stu-id="47cfd-137">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="47cfd-138">Anpassen der volumekurve</span><span class="sxs-lookup"><span data-stu-id="47cfd-138">Adjust the Volume curve</span></span>
<span data-ttu-id="47cfd-139">Standardmäßig vermindert Unity spatialisierte Sounds, wenn Sie weiter vom Listener entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="47cfd-139">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="47cfd-140">Wenn diese Dämpfung auf Interaktions Feedback Sounds angewendet wird, kann die Verwendung der Schnittstelle schwieriger werden.</span><span class="sxs-lookup"><span data-stu-id="47cfd-140">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="47cfd-141">Um diese Dämpfung zu deaktivieren, passen Sie die **volumekurve** an.</span><span class="sxs-lookup"><span data-stu-id="47cfd-141">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="47cfd-142">In der Komponente **Audioquelle** des **inspektorbereichs** für den **PressableButtonHoloLens2** gibt es einen Abschnitt mit dem Namen **3D Sound Settings**.</span><span class="sxs-lookup"><span data-stu-id="47cfd-142">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="47cfd-143">In diesem Abschnitt:</span><span class="sxs-lookup"><span data-stu-id="47cfd-143">In that section:</span></span>
1. <span data-ttu-id="47cfd-144">Legen Sie die Eigenschaft **Volume Rolloff** auf Linear fest.</span><span class="sxs-lookup"><span data-stu-id="47cfd-144">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="47cfd-145">Ziehen Sie den Endpunkt der **volumekurve** (die rote Kurve) von "0" auf der y-Achse auf "1".</span><span class="sxs-lookup"><span data-stu-id="47cfd-145">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="47cfd-146">Wenn Sie die Form der **volumekurve** an eine flache Größe anpassen möchten, ziehen Sie das Steuerelement der weißen Kurve auf parallel zur X-Achse.</span><span class="sxs-lookup"><span data-stu-id="47cfd-146">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="47cfd-147">Nachdem diese Änderungen vorgenommen wurden, sieht der Abschnitt **3D-Sound Einstellungen** in den **audioquellgenschaften** der **PressableButtonHoloLens2** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="47cfd-147">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Schaltflächen-3D-Soundeinstellungen](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="47cfd-149">Testen der spatialize-Audiodatei</span><span class="sxs-lookup"><span data-stu-id="47cfd-149">Testing the spatialize audio</span></span>

<span data-ttu-id="47cfd-150">Sie können die neuen räumlichen Schaltflächen-Interaktions Sounds testen:</span><span class="sxs-lookup"><span data-stu-id="47cfd-150">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="47cfd-151">Geben Sie im Unity-Editor den Spielmodus ein, idealerweise mit einem Beispiel für eine Schleife in der Szene.</span><span class="sxs-lookup"><span data-stu-id="47cfd-151">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="47cfd-152">Verschieben Sie das Objekt mit der Audioquelle von links nach rechts, und vergleichen Sie es mit und ohne räumliche Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="47cfd-152">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="47cfd-153">Sie können die Einstellungen für die Audioquelle zum Testen ändern von:</span><span class="sxs-lookup"><span data-stu-id="47cfd-153">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="47cfd-154">Verschieben der Spatial Blend-Eigenschaft zwischen 0-1 (2D, nicht räumlich und 3D-spatialized Sound)</span><span class="sxs-lookup"><span data-stu-id="47cfd-154">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="47cfd-155">Überprüfen und Deaktivieren der spatialize-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="47cfd-155">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="47cfd-156">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="47cfd-156">Next steps</span></span>

<span data-ttu-id="47cfd-157">Testen Sie Ihre APP auf einem hololens 2 oder im Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="47cfd-157">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="47cfd-158">In der App können Sie auf die Schaltfläche tippen und die räumlichen Schaltflächen-Interaktions Sounds hören.</span><span class="sxs-lookup"><span data-stu-id="47cfd-158">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="47cfd-159">Wenn Sie im Unity-Editor testen, drücken Sie die Leertaste, und Scrollen Sie mit dem Mausrad, um die Hand Simulation zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="47cfd-159">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="47cfd-160">Weitere Informationen finden Sie in der [mrtk-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span><span class="sxs-lookup"><span data-stu-id="47cfd-160">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="47cfd-161">Kapitel 3</span><span class="sxs-lookup"><span data-stu-id="47cfd-161">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

