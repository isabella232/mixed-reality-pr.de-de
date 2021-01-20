---
title: 'Lernprogramme für räumliche Audiodaten: 3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten'
description: Importieren Sie ein Video Medienobjekt in Ihr Unity-Projekt, und räumlichen Sie die Audiodaten aus dem Video.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer, Video Import, Video Player
ms.openlocfilehash: 6474da522e650d23349a21c3deeac00222b8ce93
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578572"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="4b001-105">3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten</span><span class="sxs-lookup"><span data-stu-id="4b001-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="4b001-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="4b001-106">Overview</span></span>

<span data-ttu-id="4b001-107">In diesem Tutorial erfahren Sie, wie Sie Audiodaten aus einer Videoquelle spatialisieren und diese im Unity-Editor und in hololens 2 testen.</span><span class="sxs-lookup"><span data-stu-id="4b001-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="4b001-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="4b001-108">Objectives</span></span>

* <span data-ttu-id="4b001-109">Importieren eines Videos und Hinzufügen eines Video Players</span><span class="sxs-lookup"><span data-stu-id="4b001-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="4b001-110">Video auf einem Quadranten abspielen</span><span class="sxs-lookup"><span data-stu-id="4b001-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="4b001-111">Leiten Sie Audiodaten aus dem Video an das Quadrangle weiter, und räumlichen Sie die Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="4b001-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="4b001-112">Importieren eines Videos und Hinzufügen eines Video Players zur Szene</span><span class="sxs-lookup"><span data-stu-id="4b001-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="4b001-113">In diesem Tutorial verwenden Sie [dieses Video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) aus dem Beispiel Projekt für räumliche Audiodateien.</span><span class="sxs-lookup"><span data-stu-id="4b001-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="4b001-114">Zum Importieren von Videos in das Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="4b001-114">To import Video into the unity project.</span></span> <span data-ttu-id="4b001-115">Wählen Sie im Unity-Menü **Asset**  >  **Import New Asset** Import 
 ![ Asset aus.](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="4b001-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span></span>

<span data-ttu-id="4b001-116">Wählen Sie im Fenster **Neues Asset importieren...** die heruntergeladene **Microsoft hololens-Spatial Sound-PTPvx7mDon4-** Datei aus, und klicken Sie auf die Schaltfläche **Öffnen** , um das Objekt in das Projekt zu importieren:</span><span class="sxs-lookup"><span data-stu-id="4b001-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![Medienobjekt auswählen](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

<span data-ttu-id="4b001-118">Durch das Anpassen der Qualitätseinstellungen für den Videoclip kann die reibungslose Wiedergabe auf hololens 2 sichergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="4b001-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="4b001-119">Wählen Sie die Videodatei im **Projekt** Fenster und im Inspektor-Fenster der Videodatei aus, und über **Schreiben** Sie die Einstellungen für **Windows Store-Apps** und:</span><span class="sxs-lookup"><span data-stu-id="4b001-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="4b001-120">**Transcode** aktivieren</span><span class="sxs-lookup"><span data-stu-id="4b001-120">Enable **Transcode**</span></span>
* <span data-ttu-id="4b001-121">Legen Sie **Codec** auf H264 fest.</span><span class="sxs-lookup"><span data-stu-id="4b001-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="4b001-122">**Modus "Bitrate** " auf "niedrig" festlegen</span><span class="sxs-lookup"><span data-stu-id="4b001-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="4b001-123">Legen Sie **räumliche Qualität** auf mittlere räumliche Qualität fest.</span><span class="sxs-lookup"><span data-stu-id="4b001-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="4b001-124">Nachdem Sie diese Anpassungen vorgenommen haben, klicken Sie auf übernehmen, um die Qualitätseinstellung für den Videoclip zu ändern.</span><span class="sxs-lookup"><span data-stu-id="4b001-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![Video-Eigenschaften Änderung](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

<span data-ttu-id="4b001-126">Klicken Sie mit der rechten Maustaste auf die Hierarchie, und wählen Sie **Video**  >  **Video Player** , um die Video Player Komponente</span><span class="sxs-lookup"><span data-stu-id="4b001-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![Video Player hinzufügen](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="4b001-128">Abspielen von Videos auf einem Quadranten</span><span class="sxs-lookup"><span data-stu-id="4b001-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="4b001-129">Das **Video Player** -Objekt benötigt ein texturiertes Spielobjekt zum Rendering des Videos.</span><span class="sxs-lookup"><span data-stu-id="4b001-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="4b001-130">Klicken Sie mit der rechten Maustaste auf die Hierarchie, wählen Sie **3D-Objekt**  >  **Quad** aus, um ein Quad zu erstellen, und konfigurieren Sie die </span><span class="sxs-lookup"><span data-stu-id="4b001-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="4b001-131">**Position**: X = 0, Y = 0, Z = 2</span><span class="sxs-lookup"><span data-stu-id="4b001-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="4b001-132">**Drehung**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="4b001-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="4b001-133">**Skalierung**: X = 1,28, Y = 0,72, Z = 1</span><span class="sxs-lookup"><span data-stu-id="4b001-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![Hinzufügen eines Quad-](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

<span data-ttu-id="4b001-135">Nun müssen Sie das Vierfache **mit dem** Video strukturieren. Klicken Sie dazu im **Projekt** Fenster mit der rechten Maustaste, und wählen Sie   >  **Rendering-Textur** erstellen aus, um eine Rendering-Textur Komponente zu erstellen, und geben Sie einen passenden Namen für die Rendering-Textur ein, z.b. _räumliche audiotextur_:</span><span class="sxs-lookup"><span data-stu-id="4b001-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![Rendering-Textur erstellen](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

<span data-ttu-id="4b001-137">Wählen Sie die **Rendering-Textur** aus, und legen Sie im Inspektor-Fenster die **size** -Eigenschaft so fest, dass Sie mit der nativen Auflösung des Videos in der Auflösung</span><span class="sxs-lookup"><span data-stu-id="4b001-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="4b001-138">Um dann eine gute Renderingleistung auf hololens 2 sicherzustellen, legen Sie die **Tiefe Puffer** Eigenschaft auf **mindestens 16 Bits** fest.</span><span class="sxs-lookup"><span data-stu-id="4b001-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![Rendering-Textur Eigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

<span data-ttu-id="4b001-140">Verwenden Sie als nächstes die erstellte **Darstellung der Struktur** für das **räumliche** Rendering als Textur für das Vierfache:</span><span class="sxs-lookup"><span data-stu-id="4b001-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="4b001-141">Ziehen Sie die **räumliche audiotextur** aus dem **Projekt** Fenster auf **das Vierfache in der hier** Archie, um die Rendering-Textur dem Quad hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="4b001-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="4b001-142">Um eine gute Leistung bei hololens 2 sicherzustellen, wählen Sie Quad in der Hierarchie aus, und wählen Sie im Inspektor-Fenster für Shader das **Mixed Reality Toolkit**  >  **Standard** -Shader aus.</span><span class="sxs-lookup"><span data-stu-id="4b001-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![Vier Textur Eigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

<span data-ttu-id="4b001-144">Wählen Sie den **Video Player** in der **Hierarchie** aus **, und klicken** Sie im **Inspektor** - **Fenster auf**</span><span class="sxs-lookup"><span data-stu-id="4b001-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="4b001-145">Legen Sie die Eigenschaft " **Video Clip** " auf die heruntergeladene Videodatei "Microsoft hololens-Spatial Sound-PTPvx7mDon4" fest.</span><span class="sxs-lookup"><span data-stu-id="4b001-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="4b001-146">Aktivieren Sie das Kontrollkästchen **Schleife** .</span><span class="sxs-lookup"><span data-stu-id="4b001-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="4b001-147">Legen Sie die **Ziel Textur** auf die neue Darstellung der gentexgenräumlichen Darstellung fest </span><span class="sxs-lookup"><span data-stu-id="4b001-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![Video Player-Eigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="4b001-149">Spatialisieren der Audiodaten aus dem Video</span><span class="sxs-lookup"><span data-stu-id="4b001-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="4b001-150">Wählen Sie im Fenster Hierarchie die Option **Quad** Object aus, und verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um **Audioquelle** hinzuzufügen, an die Sie die Audiodaten aus dem Video weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="4b001-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="4b001-151">In der **Audioquelle**:</span><span class="sxs-lookup"><span data-stu-id="4b001-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="4b001-152">Festlegen der **Ausgabe** auf den **räumlichen Audiomixer**</span><span class="sxs-lookup"><span data-stu-id="4b001-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="4b001-153">Aktivieren Sie das Feld **spatialize** .</span><span class="sxs-lookup"><span data-stu-id="4b001-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="4b001-154">Verschieben Sie den Schieberegler für **räumliche Blend** auf 1 (3D).</span><span class="sxs-lookup"><span data-stu-id="4b001-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![Quad-audioquellinspektor](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

<span data-ttu-id="4b001-156">Um den Video Player so festzulegen, dass seine Audiodaten an die **Audioquelle** weitergeleitet werden, wählen Sie im Fenster Hierarchie den **Video Player** aus, und führen Sie im inspektorobjekt im Inspektor die folgenden Änderungen aus.</span><span class="sxs-lookup"><span data-stu-id="4b001-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="4b001-157">Festlegen des **Audioausgabemodus** auf **Audioquelle**</span><span class="sxs-lookup"><span data-stu-id="4b001-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="4b001-158">Legen Sie die Eigenschaft **Audioquelle** auf **Quad** fest.</span><span class="sxs-lookup"><span data-stu-id="4b001-158">Set the **Audio Source** property to the **Quad**</span></span>

![Video Player-Audioquelle festlegen](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="4b001-160">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="4b001-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4b001-161">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="4b001-161">Congratulations</span></span>

<span data-ttu-id="4b001-162">In diesem Tutorial haben Sie gelernt, wie Sie Audiodaten aus einer Videoquelle eingrenzen, indem Sie Ihre APP auf einem hololens 2 oder im Unity-Editor testen.</span><span class="sxs-lookup"><span data-stu-id="4b001-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="4b001-163">Sie sehen und hören das Video, und die Audiodaten aus dem Video sind räumlich.</span><span class="sxs-lookup"><span data-stu-id="4b001-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="4b001-164">Im nächsten Tutorial erfahren Sie, wie Sie die Spatialisierung zur Laufzeit aktivieren und deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="4b001-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b001-165">Nächstes Tutorial: 4. aktivieren und Deaktivieren der Spatialisierung zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="4b001-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
