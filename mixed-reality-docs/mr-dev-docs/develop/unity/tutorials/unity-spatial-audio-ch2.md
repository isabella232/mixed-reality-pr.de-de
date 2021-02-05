---
title: 'Lernprogramme für räumliche Audiodaten: 2. Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten'
description: Fügen Sie dem Projekt eine Schaltfläche hinzu, und räumlichen Sie die Sound der Schaltflächen Interaktion.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer, Prefabs, volumekurve
ms.openlocfilehash: 12d159cb162cbf136483f7be94b0d297319a0737
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590762"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="9168d-105">2. Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten</span><span class="sxs-lookup"><span data-stu-id="9168d-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="9168d-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="9168d-106">Overview</span></span>

<span data-ttu-id="9168d-107">In diesem Tutorial erfahren Sie, wie Sie die schaltflächeninteraktionssounds spatialisieren und außerdem erfahren, wie Sie einen Audioclip verwenden, um eine räumliche Schaltflächen Interaktion zu testen.</span><span class="sxs-lookup"><span data-stu-id="9168d-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="9168d-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="9168d-108">Objectives</span></span>

* <span data-ttu-id="9168d-109">Hinzufügen und spatialisieren der Schaltflächen Klick-Sounds</span><span class="sxs-lookup"><span data-stu-id="9168d-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="9168d-110">Hinzufügen einer Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="9168d-110">Add a button</span></span>

<span data-ttu-id="9168d-111">Wählen Sie zum Hinzufügen der Schaltfläche "Prefab" im **Projekt** Fenster **Pakete** aus, und geben Sie "PressableButtonHoloLens2" in die Suchleiste ein.</span><span class="sxs-lookup"><span data-stu-id="9168d-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![Schaltflächen vorfab in Assets](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

<span data-ttu-id="9168d-113">Die Schaltflächen-vorfab ist der durch ein blaues Symbol dargestellte Eintrag.</span><span class="sxs-lookup"><span data-stu-id="9168d-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="9168d-114">Klicken und ziehen Sie die **PressableButtonHoloLens2** -vorfab in die Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="9168d-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="9168d-115">Wenn das **PressableButtonHoloLens2** -Objekt noch ausgewählt ist, konfigurieren Sie die **Transformations** Komponente im Inspektor-Fenster wie folgt:</span><span class="sxs-lookup"><span data-stu-id="9168d-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="9168d-116">**Position**: X = 0, Y =-0,4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="9168d-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="9168d-117">**Drehung**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="9168d-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="9168d-118">**Skalierung**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="9168d-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Schaltflächen Transformation](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

<span data-ttu-id="9168d-120">Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **PressableButtonHoloLens2** -Objekt doppelklicken und anschließend etwas vergrößern:</span><span class="sxs-lookup"><span data-stu-id="9168d-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="9168d-121">Schaltflächen-Feedback spatialisieren</span><span class="sxs-lookup"><span data-stu-id="9168d-121">Spatialize button feedback</span></span>

<span data-ttu-id="9168d-122">In diesem Schritt Stufen Sie das Audiofeedback für die Schaltfläche ein.</span><span class="sxs-lookup"><span data-stu-id="9168d-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="9168d-123">Verwandte Entwurfsvorschläge finden Sie unter [Spatial Sound Design](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="9168d-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="9168d-124">Im Fenster **Audiomixer** definieren Sie Ziele, die als **mischungsgruppen** bezeichnet werden, für die Audiowiedergabe aus **audioquellkomponenten** .</span><span class="sxs-lookup"><span data-stu-id="9168d-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="9168d-125">Um das **audiomischfenster** zu öffnen, klicken Sie im Unity-Menü auf **Fenster**  >    >  **audioaudiomixer**: ![ geöffneten audiomischerfenster.](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="9168d-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span></span>

 <span data-ttu-id="9168d-126">Erstellen Sie einen **Mixer** , indem Sie auf "+" neben " **Mixer** " klicken und einen passenden Namen für den Mixer eingeben, z. b. _räumlicher Audiomixer_.</span><span class="sxs-lookup"><span data-stu-id="9168d-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="9168d-127">Der neue Mixer enthält eine Standard **Gruppe** namens **Master**.</span><span class="sxs-lookup"><span data-stu-id="9168d-127">The new mixer will include a default **Group** called **Master**.</span></span>

![Mischbereich mit dem ersten Mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="9168d-129">Bis das "Reverb" in einem [fünften Kapitel aktiviert ist: das Hinzufügen von Abstand zu räumlichen Audiodaten](unity-spatial-audio-ch5.md)durch die Verwendung von "Hall" wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9168d-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="9168d-130">Wählen Sie im Fenster Hierarchie den **PressableButtonHoloLens2** aus, suchen Sie im Inspektor-Fenster die **audioquellkomponente** , und konfigurieren Sie die audioquellkomponente wie folgt:</span><span class="sxs-lookup"><span data-stu-id="9168d-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="9168d-131">Klicken Sie für die **Output** -Eigenschaft auf die Auswahl, und wählen Sie den von Ihnen erstellten **Mixer** aus.</span><span class="sxs-lookup"><span data-stu-id="9168d-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="9168d-132">Aktivieren Sie das Kontrollkästchen **spatialize** .</span><span class="sxs-lookup"><span data-stu-id="9168d-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="9168d-133">Verschieben Sie den Schieberegler **räumlicher Blend** in 3D (1).</span><span class="sxs-lookup"><span data-stu-id="9168d-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![Schaltflächen-Audioquelle](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="9168d-135">Wenn Sie **räumliche Blend** in 1 (3D) verschieben, ohne das **spatialize** -Kontrollkästchen zu aktivieren, verwendet Unity den Schwenk räumlichen spatializer anstelle von **Microsoft spatializer** mit HRTFs.</span><span class="sxs-lookup"><span data-stu-id="9168d-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="9168d-136">Anpassen der volumekurve</span><span class="sxs-lookup"><span data-stu-id="9168d-136">Adjust the Volume curve</span></span>

<span data-ttu-id="9168d-137">Standardmäßig vermindert Unity spatialisierte Sounds, wenn Sie weiter vom Listener entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="9168d-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="9168d-138">Wenn diese Dämpfung auf Interaktions Feedback Sounds angewendet wird, kann die Verwendung der Schnittstelle schwieriger werden.</span><span class="sxs-lookup"><span data-stu-id="9168d-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="9168d-139">Um diese Dämpfung zu deaktivieren, müssen Sie die **volumekurve** in der **audioquellkomponente** anpassen.</span><span class="sxs-lookup"><span data-stu-id="9168d-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="9168d-140">Wählen Sie im Fenster Hierarchie den **PressableButtonHoloLens2** aus, und navigieren Sie dann im Inspektor-Fenster zu **Audioquelle**  >  **3D Sound Settings** , und konfigurieren Sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="9168d-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="9168d-141">Festlegen der **volumerolloff** -Eigenschaft auf Linear Rolloff</span><span class="sxs-lookup"><span data-stu-id="9168d-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="9168d-142">Ziehen Sie den Endpunkt der **volumekurve** (die rote Kurve) von "0" auf der y-Achse auf "1".</span><span class="sxs-lookup"><span data-stu-id="9168d-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="9168d-143">Wenn Sie die Form der **volumekurve** an eine flache Größe anpassen möchten, ziehen Sie das Steuerelement der weißen Kurve auf parallel zur X-Achse.</span><span class="sxs-lookup"><span data-stu-id="9168d-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![Schaltflächen-3D-Soundeinstellungen](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="9168d-145">Testen der spatialize-Audiodatei</span><span class="sxs-lookup"><span data-stu-id="9168d-145">Testing the spatialize audio</span></span>

<span data-ttu-id="9168d-146">Um die spatialize-Audiodatei im Unity-Editor zu testen, müssen Sie einen Audioclip in der **audioquellkomponente** mit **Schleifen** Option hinzufügen, die für das **PressableButtonHoloLens2** -Objekt aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="9168d-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="9168d-147">Verschieben Sie das **PressableButtonHoloLens2** -Objekt im Wiedergabemodus von links nach rechts, und vergleichen Sie es mit und ohne räumliche Audiodaten auf Ihrer Arbeitsstation.</span><span class="sxs-lookup"><span data-stu-id="9168d-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="9168d-148">Sie können auch die Einstellungen für die Audioquelle zum Testen ändern, indem Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="9168d-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="9168d-149">Verschieben der **Spatial Blend** -Eigenschaft zwischen 0-1 (2D, nicht räumlich und 3D-spatialized Sound)</span><span class="sxs-lookup"><span data-stu-id="9168d-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="9168d-150">Überprüfen und Deaktivieren der **spatialize** -Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9168d-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="9168d-151">Testen Sie die APP auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="9168d-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="9168d-152">In der App können Sie auf die Schaltfläche klicken und die Kontext-Sounds für räumliche Schaltflächen hören.</span><span class="sxs-lookup"><span data-stu-id="9168d-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="9168d-153">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="9168d-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9168d-154">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="9168d-154">Congratulations</span></span>

<span data-ttu-id="9168d-155">In diesem Tutorial haben Sie gelernt, den Schaltflächen-Interaktions Sound zu verräumlichen und einen Audioclip zu verwenden, um eine räumliche Schaltflächen Interaktion zu testen.</span><span class="sxs-lookup"><span data-stu-id="9168d-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="9168d-156">Im nächsten Tutorial erfahren Sie, wie Sie Audiodaten aus einer Videoquelle spatialisieren.</span><span class="sxs-lookup"><span data-stu-id="9168d-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9168d-157">Nächstes Tutorial: 3. spatialisieren von Audiodaten aus einem Video</span><span class="sxs-lookup"><span data-stu-id="9168d-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
