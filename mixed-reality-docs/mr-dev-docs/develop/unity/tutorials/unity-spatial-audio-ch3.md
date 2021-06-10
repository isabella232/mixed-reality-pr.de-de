---
title: 'Tutorials zu räumlichen Audioinhalten : 3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten'
description: Importieren Sie ein Video-Asset in Ihr Unity-Projekt, und raumisieren Sie die Audiodaten aus dem Video.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer, Videoimport, Videoplayer
ms.openlocfilehash: 60b70fc3b7f49f5b39138a218f93c0b37f29b9d9
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712878"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="f3c0e-105">3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten</span><span class="sxs-lookup"><span data-stu-id="f3c0e-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="f3c0e-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f3c0e-106">Overview</span></span>

<span data-ttu-id="f3c0e-107">In diesem Tutorial erfahren Sie, wie Sie Audiodaten aus einer Videoquelle raumisieren und im Unity-Editor und im HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="f3c0e-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="f3c0e-108">Objectives</span></span>

* <span data-ttu-id="f3c0e-109">Importieren eines Videos und Hinzufügen eines Videoplayers</span><span class="sxs-lookup"><span data-stu-id="f3c0e-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="f3c0e-110">Wiedergabe des Videos auf einem Quadrangle</span><span class="sxs-lookup"><span data-stu-id="f3c0e-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="f3c0e-111">Audiodaten aus dem Video an den Quadrangle weiter routen und die Audiodatei raumisieren</span><span class="sxs-lookup"><span data-stu-id="f3c0e-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="f3c0e-112">Importieren eines Videos und Hinzufügen eines Videoplayers zur Szene</span><span class="sxs-lookup"><span data-stu-id="f3c0e-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="f3c0e-113">Verwenden Sie für dieses Tutorial Sie können dieses [Video aus dem](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) Beispielprojekt für räumliche Audioinhalte verwenden.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="f3c0e-114">So importieren Sie Video in das Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-114">To import Video into the unity project.</span></span> <span data-ttu-id="f3c0e-115">Wählen Sie im Unity-Menü **Asset Import** New Asset  >  Importing Asset (Asset **importieren, neues Asset** 
 ![ importieren) aus.](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="f3c0e-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)</span></span>

<span data-ttu-id="f3c0e-116">Wählen Sie im Fenster Neues Asset **importieren...** die heruntergeladene Datei **Microsoft HoloLens – Spatial Sound-PTPvx7mDon4** aus, und klicken Sie auf die Schaltfläche Öffnen, um das Asset in das Projekt zu importieren: </span><span class="sxs-lookup"><span data-stu-id="f3c0e-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![Auswählen des Assets](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

<span data-ttu-id="f3c0e-118">Durch Anpassen der Qualitätseinstellungen für den Videoclip kann eine reibungslose Wiedergabe auf HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="f3c0e-119">Wählen Sie die Videodatei im Fenster **Projekt** **aus,** und überschreiben Sie im Inspektorfenster der Videodatei die Einstellungen für **Windows Store-Apps** und:</span><span class="sxs-lookup"><span data-stu-id="f3c0e-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="f3c0e-120">Aktivieren **von Transcodierung**</span><span class="sxs-lookup"><span data-stu-id="f3c0e-120">Enable **Transcode**</span></span>
* <span data-ttu-id="f3c0e-121">Legen Sie **Codec** auf H264 fest.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="f3c0e-122">Festlegen **des Bitratenmodus auf** "Niedrig"</span><span class="sxs-lookup"><span data-stu-id="f3c0e-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="f3c0e-123">Legen **Sie spatial quality (Räumliche Qualität)** auf Medium Spatial Quality (Mittlere räumliche Qualität) fest.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="f3c0e-124">Klicken Sie nach diesen Anpassungen auf Übernehmen, um die Qualitätseinstellung für den Videoclip zu ändern.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![Änderung der Videoeigenschaft](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

<span data-ttu-id="f3c0e-126">Klicken Sie mit der rechten Maustaste auf die Hierarchie, und wählen **Sie Video** Video  >  **Player aus,** um die Komponente Videoplayer hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![Hinzufügen eines Videoplayers](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="f3c0e-128">Video auf einem Quadrangle wieder abspielen</span><span class="sxs-lookup"><span data-stu-id="f3c0e-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="f3c0e-129">Das **Video Player-Objekt** benötigt ein texturiertes Spielobjekt, um das Video zu rendern.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="f3c0e-130">Klicken Sie mit der rechten Maustaste auf die Hierarchie, wählen Sie **3D Object** Quad aus, um ein Quad zu erstellen, und konfigurieren Sie die  >   **Transformationskomponente** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f3c0e-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="f3c0e-131">**Position:** X = 0, Y = 0, Z = 2</span><span class="sxs-lookup"><span data-stu-id="f3c0e-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="f3c0e-132">**Drehung**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f3c0e-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f3c0e-133">**Skalierung:** X = 1,28, Y = 0,72, Z = 1</span><span class="sxs-lookup"><span data-stu-id="f3c0e-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![Hinzufügen eines Quads](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

<span data-ttu-id="f3c0e-135">Nun müssen Sie das Quad mit dem  Video texturieren. Klicken Sie im Fenster Projekt mit der rechten Maustaste, und wählen Sie Rendertextur erstellen aus, um eine Rendertexturkomponente zu erstellen. Geben Sie einen geeigneten Namen für die Rendertextur ein, z. B. Spatial Audio   >   _Texture_:</span><span class="sxs-lookup"><span data-stu-id="f3c0e-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![Rendertextur erstellen](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

<span data-ttu-id="f3c0e-137">Wählen Sie **die Rendertextur aus,** und legen Sie im Inspektorfenster die **Eigenschaft Größe** so fest, dass sie mit der nativen Auflösung des Videos von 1280 x 720 übereinstimmen soll.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="f3c0e-138">Legen Sie dann die Eigenschaft Tiefenpuffer auf mindestens  **16** Bits fest, um eine gute Renderingleistung für HoloLens 2 sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![Rendertextureigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

<span data-ttu-id="f3c0e-140">Verwenden Sie als Nächstes die erstellte Textur render Texture **Spatial Audio Texture** (Räumliche Audiotextur der Rendertextur) als Textur für **das Quad-Objekt:**</span><span class="sxs-lookup"><span data-stu-id="f3c0e-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="f3c0e-141">Ziehen Sie die **Textur für räumliche Audiodaten** aus dem **Projektfenster** auf das **Quad** in der Hierarchie, um die Rendertextur dem Quad-Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="f3c0e-142">Um eine gute Leistung auf HoloLens 2 sicherzustellen, wählen Sie in der Hierarchie Quad und im Inspektorfenster für Shader den Mixed Reality **Toolkit**  >  **Standard** Shader aus.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![Eigenschaften der Quad-Textur](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

<span data-ttu-id="f3c0e-144">Wählen Sie zum **Festlegen von VideoPlayer** und **Rendertextur**  für die Wiedergabe des Videoclips den **Videoplayer** in der Hierarchie und im **Inspektorfenster** aus.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="f3c0e-145">Legen Sie **die Video Clip-Eigenschaft** auf die heruntergeladene Videodatei "Microsoft HoloLens – Spatial Sound-PTPvx7mDon4" fest.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="f3c0e-146">Aktivieren Sie das **Kontrollkästchen Schleife.**</span><span class="sxs-lookup"><span data-stu-id="f3c0e-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="f3c0e-147">Festlegen **der Zieltextur** auf ihre neue Rendertextur **für räumliche Audiotextur**</span><span class="sxs-lookup"><span data-stu-id="f3c0e-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![Videoplayereigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="f3c0e-149">Raumisieren der Audiodaten aus dem Video</span><span class="sxs-lookup"><span data-stu-id="f3c0e-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="f3c0e-150">Wählen Sie im Hierarchiefenster **Quad** object (Quad-Objekt) aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche Add **Component** (Komponente hinzufügen), um audio **source (Audioquelle)** hinzuzufügen, an die Sie die Audiodaten aus dem Video routen.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="f3c0e-151">In der **Audioquelle:**</span><span class="sxs-lookup"><span data-stu-id="f3c0e-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="f3c0e-152">Festlegen **der Ausgabe** auf den **Raumaudiomixer**</span><span class="sxs-lookup"><span data-stu-id="f3c0e-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="f3c0e-153">Aktivieren des **Kontrollkästchens Spatialize**</span><span class="sxs-lookup"><span data-stu-id="f3c0e-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="f3c0e-154">Verschieben des **Schiebereglers "Spatial Blend"** auf 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="f3c0e-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![Inspektor für Quad-Audioquellen](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

<span data-ttu-id="f3c0e-156">Um den VideoPlayer so zu festlegen, dass seine Audiodaten an die **Audioquelle** geroutet werden, wählen Sie **den Videoplayer** im Hierarchiefenster aus, und nehmen Sie im Videoplayerobjekt im Inspector die folgenden Änderungen vor.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="f3c0e-157">Festlegen des **Audioausgabemodus auf** **Audioquelle**</span><span class="sxs-lookup"><span data-stu-id="f3c0e-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="f3c0e-158">Legen Sie die **Eigenschaft Audioquelle** auf quad **fest.**</span><span class="sxs-lookup"><span data-stu-id="f3c0e-158">Set the **Audio Source** property to the **Quad**</span></span>

![Videoplayer: Festlegen der Audioquelle](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> <span data-ttu-id="f3c0e-160">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="f3c0e-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f3c0e-161">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="f3c0e-161">Congratulations</span></span>

<span data-ttu-id="f3c0e-162">In diesem Tutorial haben Sie gelernt, wie Sie Audiodaten aus einer Videoquelle spatialisieren. Testen Sie Ihre App auf einer HoloLens 2 oder im Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="f3c0e-163">Sie sehen und hören das Video, und die Audiodaten aus dem Video sind räumlich.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="f3c0e-164">Im nächsten Tutorial erfahren Sie, wie Sie die Räumliche Raumung zur Laufzeit aktivieren und deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="f3c0e-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f3c0e-165">Nächstes Tutorial: 4. Aktivieren und Deaktivieren der Räumlichen Anordnung zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="f3c0e-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
