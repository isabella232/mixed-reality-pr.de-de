---
title: 'Tutorials zu räumlichen Audioinhalten : 2. Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten'
description: Fügen Sie ihrem Projekt eine Schaltfläche hinzu, und raumisieren Sie die Schaltflächeninteraktionsgeräusche.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer, Prefabs, Volumekurve
ms.openlocfilehash: f3f2faf8220eaebcc674bcf02a45d99d58169076
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712807"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="55a80-105">2. Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten</span><span class="sxs-lookup"><span data-stu-id="55a80-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="55a80-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="55a80-106">Overview</span></span>

<span data-ttu-id="55a80-107">In diesem Tutorial erfahren Sie, wie Sie die Schaltflächeninteraktionsgeräusche raumisieren und wie Sie einen Audioclip verwenden, um die Interaktion mit räumlichen Schaltflächen zu testen.</span><span class="sxs-lookup"><span data-stu-id="55a80-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="55a80-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="55a80-108">Objectives</span></span>

* <span data-ttu-id="55a80-109">Hinzufügen und Raumisieren der Schaltflächenklick-Sounds</span><span class="sxs-lookup"><span data-stu-id="55a80-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="55a80-110">Hinzufügen einer Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="55a80-110">Add a button</span></span>

<span data-ttu-id="55a80-111">Wählen Sie zum Hinzufügen des  Schaltflächen-Prefabs im Fenster Projekt die Option **Pakete** aus, und geben Sie in der Suchleiste "PressableButtonHoloLens2" ein.</span><span class="sxs-lookup"><span data-stu-id="55a80-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![Schaltflächen-Prefab in Assets](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

<span data-ttu-id="55a80-113">Das Schaltflächen-Prefab ist der Eintrag, der durch ein blaues Symbol dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="55a80-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="55a80-114">Klicken Sie auf das **Prefab PressableButtonHoloLens2,** und ziehen Sie es in die Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="55a80-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="55a80-115">Wenn das **PressableButtonHoloLens2-Objekt** noch ausgewählt ist, konfigurieren Sie im Inspektorfenster die **Komponente Transformieren** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="55a80-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="55a80-116">**Position:** X = 0, Y = -0,4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="55a80-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="55a80-117">**Drehung**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="55a80-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="55a80-118">**Skalierung**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="55a80-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Schaltflächentransformation](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

<span data-ttu-id="55a80-120">Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **PressableButtonHoloLens2-Objekt** doppelklicken und dann wieder etwas vergrößern:</span><span class="sxs-lookup"><span data-stu-id="55a80-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="55a80-121">Feedback zur Schaltfläche "Spatialize"</span><span class="sxs-lookup"><span data-stu-id="55a80-121">Spatialize button feedback</span></span>

<span data-ttu-id="55a80-122">In diesem Schritt raumisieren Sie das Audiofeedback für die Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="55a80-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="55a80-123">Entsprechende Entwurfsvorschläge finden Sie unter [Entwurf von Raumklang.](../../../design/spatial-sound-design.md)</span><span class="sxs-lookup"><span data-stu-id="55a80-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="55a80-124">Im Fenster **Audiomixer** definieren Sie Ziele namens **Mixergruppen** für die Audiowiedergabe von **Audioquellenkomponenten.**</span><span class="sxs-lookup"><span data-stu-id="55a80-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="55a80-125">Klicken Sie zum Öffnen **des Fensters Audiomixer** im Unity-Menü auf **Window** Audio Audio Mixer : Open Audio Mixer Window (Fensteraudio-Audiomixer:  >    >   ![ Audiomixerfenster öffnen).](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="55a80-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span></span>

 <span data-ttu-id="55a80-126">Erstellen Sie **einen Mixer,** indem Sie auf das "+" neben **Mixer klicken** und einen passenden Namen für den Mixer eingeben, z. B. Spatial _Audio Mixer_.</span><span class="sxs-lookup"><span data-stu-id="55a80-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="55a80-127">Der neue Mixer enthält eine Standardgruppe **namens** **Master**.</span><span class="sxs-lookup"><span data-stu-id="55a80-127">The new mixer will include a default **Group** called **Master**.</span></span>

![Mixerpanel mit erstem Mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> <span data-ttu-id="55a80-129">Bis hall in [5th Chapter: Using reverb](unity-spatial-audio-ch5.md)to add distance to spatial audio ,the mixer es volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="55a80-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="55a80-130">Wählen Sie im Hierarchiefenster **pressableButtonHoloLens2** aus, suchen Sie dann im Inspektorfenster die Komponente **Audioquelle,** und konfigurieren Sie die Komponente Audioquelle wie folgt:</span><span class="sxs-lookup"><span data-stu-id="55a80-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="55a80-131">Klicken Sie **für die Eigenschaft Ausgabe** auf den Selektor, und wählen Sie den von **Ihnen** erstellten Mixer aus.</span><span class="sxs-lookup"><span data-stu-id="55a80-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="55a80-132">Aktivieren Sie **das Kontrollkästchen Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="55a80-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="55a80-133">Verschieben Sie **den Schieberegler Spatial Blend** in 3D (1).</span><span class="sxs-lookup"><span data-stu-id="55a80-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![Schaltflächenaudioquelle](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="55a80-135">Wenn Sie **Spatial Blend** auf 1 (3D) verschieben, ohne das Kontrollkästchen **Spatialize** zu aktivieren, verwendet Unity den schwenkenden Spatializer anstelle des Microsoft **Spatializers** mit HRTFs.</span><span class="sxs-lookup"><span data-stu-id="55a80-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="55a80-136">Anpassen der Volumekurve</span><span class="sxs-lookup"><span data-stu-id="55a80-136">Adjust the Volume curve</span></span>

<span data-ttu-id="55a80-137">Standardmäßig dämpft Unity räumliche Sounds, wenn sie weiter vom Listener entfernt sind.</span><span class="sxs-lookup"><span data-stu-id="55a80-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="55a80-138">Wenn diese Dämpfung auf Interaktionsfeedback-Sounds angewendet wird, kann die Verwendung der Schnittstelle schwieriger werden.</span><span class="sxs-lookup"><span data-stu-id="55a80-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="55a80-139">Um diese Dämpfung zu deaktivieren, müssen Sie die **Volumekurve** in der Komponente **Audioquelle** anpassen.</span><span class="sxs-lookup"><span data-stu-id="55a80-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="55a80-140">Wählen Sie im Hierarchiefenster **pressableButtonHoloLens2** aus, navigieren Sie dann im Inspektorfenster zu **Audio Source**  >  **3D Sound Settings (3D-Soundeinstellungen** für Audioquelle), und konfigurieren Sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="55a80-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="55a80-141">Legen Sie die **Eigenschaft Volumerolloff** auf Linear Rolloff fest.</span><span class="sxs-lookup"><span data-stu-id="55a80-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="55a80-142">Ziehen Sie den Endpunkt auf der **Volumekurve** (die rote Kurve) von "0" auf der y-Achse auf "1".</span><span class="sxs-lookup"><span data-stu-id="55a80-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="55a80-143">Um die Form  der Volumekurve so anzupassen, dass sie flach ist, ziehen Sie das Shape-Steuerelement der weißen Kurve so, dass es parallel zur X-Achse ist.</span><span class="sxs-lookup"><span data-stu-id="55a80-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![3D-Soundeinstellungen der Schaltfläche](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="55a80-145">Testen des Spatialize-Audios</span><span class="sxs-lookup"><span data-stu-id="55a80-145">Testing the spatialize audio</span></span>

<span data-ttu-id="55a80-146">Zum Testen des Spatialize-Audios im Unity-Editor müssen Sie der **Audioquelle-Komponente** einen Audioclip hinzufügen, bei dem die Option **Loop** im **PressableButtonHoloLens2-Objekt eincheckt** ist.</span><span class="sxs-lookup"><span data-stu-id="55a80-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="55a80-147">Verschieben Sie im Wiedergabemodus das **PressableButtonHoloLens2-Objekt** von links nach rechts, und vergleichen Sie es mit und ohne aktiviertes räumliches Audio auf Ihrer Arbeitsstation.</span><span class="sxs-lookup"><span data-stu-id="55a80-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="55a80-148">Sie können die Einstellungen der Audioquelle für Tests auch wie im folgenden Beispiel ändern:</span><span class="sxs-lookup"><span data-stu-id="55a80-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="55a80-149">Verschieben der **Spatial Blend-Eigenschaft** zwischen 0 und 1 (nicht räumlicher 2D- und 3D-Raumklang)</span><span class="sxs-lookup"><span data-stu-id="55a80-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="55a80-150">Überprüfen und Deaktivieren der **Spatialize-Eigenschaft**</span><span class="sxs-lookup"><span data-stu-id="55a80-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="55a80-151">Testen Sie die App auf HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="55a80-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="55a80-152">In der App können Sie auf die Schaltfläche klicken und die Interaktionsgeräusche der räumlichen Schaltfläche hören.</span><span class="sxs-lookup"><span data-stu-id="55a80-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="55a80-153">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="55a80-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="55a80-154">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="55a80-154">Congratulations</span></span>

<span data-ttu-id="55a80-155">In diesem Tutorial haben Sie gelernt, die Schaltflächeninteraktionsgeräusche zu raumisieren und einen Audioclip zu verwenden, um die Interaktion mit räumlichen Schaltflächen zu testen.</span><span class="sxs-lookup"><span data-stu-id="55a80-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="55a80-156">Im nächsten Tutorial erfahren Sie, wie Sie Audiodaten aus einer Videoquelle raumisieren.</span><span class="sxs-lookup"><span data-stu-id="55a80-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55a80-157">Nächstes Tutorial: 3. Räumliches Verwenden von Audiodaten aus einem Video</span><span class="sxs-lookup"><span data-stu-id="55a80-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
