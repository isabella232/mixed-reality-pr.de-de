---
title: 'Lernprogramme für räumliche Audiodaten: 3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten'
description: Importieren Sie ein Video Medienobjekt in Ihr Unity-Projekt, und räumlichen Sie die Audiodaten aus dem Video.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens2, räumliche Audiodaten
ms.openlocfilehash: cd684944bdd618dcf435ef91566d6d4f18aa87a3
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91689787"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="e22dc-105">Versehen des Audiosignals eines Videoclips mit räumlichen Effekten</span><span class="sxs-lookup"><span data-stu-id="e22dc-105">Spatializing audio from a video</span></span>
<span data-ttu-id="e22dc-106">In diesem dritten Kapitel des Moduls Spatial-Audiodaten der Unity-Lernprogramme hololens 2 werden Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="e22dc-106">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="e22dc-107">Importieren eines Videos und Hinzufügen eines Video Players</span><span class="sxs-lookup"><span data-stu-id="e22dc-107">Import a video and add a Video Player</span></span>
* <span data-ttu-id="e22dc-108">Video auf einem Quadranten abspielen</span><span class="sxs-lookup"><span data-stu-id="e22dc-108">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="e22dc-109">Leiten Sie Audiodaten aus dem Video an das Quadrangle weiter, und räumlichen Sie die Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="e22dc-109">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="e22dc-110">Importieren eines Videos und Hinzufügen eines Video Players</span><span class="sxs-lookup"><span data-stu-id="e22dc-110">Import a video and add a Video Player</span></span>

<span data-ttu-id="e22dc-111">Ziehen Sie eine Videodatei in das **Projekt** Bereich Ihres Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="e22dc-111">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="e22dc-112">Sie können [dieses Video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) aus dem Beispiel Projekt für räumliche Audiodaten verwenden.</span><span class="sxs-lookup"><span data-stu-id="e22dc-112">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![Ordner "Assets" mit Video](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="e22dc-114">Durch das Anpassen der Qualitätseinstellungen für den Videoclip kann die reibungslose Wiedergabe auf hololens 2 sichergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="e22dc-114">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="e22dc-115">Klicken Sie im **Projekt** Bereich auf die Videodatei.</span><span class="sxs-lookup"><span data-stu-id="e22dc-115">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="e22dc-116">Überschreiben Sie im **Inspektor** -Bereich der Videodatei die Einstellungen für Windows Store-Apps und:</span><span class="sxs-lookup"><span data-stu-id="e22dc-116">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="e22dc-117">**Transcode** aktivieren</span><span class="sxs-lookup"><span data-stu-id="e22dc-117">Enable **Transcode**</span></span>
* <span data-ttu-id="e22dc-118">Legen Sie **Codec** auf H264 fest.</span><span class="sxs-lookup"><span data-stu-id="e22dc-118">Set **Codec** to H264</span></span>
* <span data-ttu-id="e22dc-119">**Modus "Bitrate** " auf "niedrig" festlegen</span><span class="sxs-lookup"><span data-stu-id="e22dc-119">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="e22dc-120">Legen Sie **räumliche Qualität** auf mittlere räumliche Qualität fest.</span><span class="sxs-lookup"><span data-stu-id="e22dc-120">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="e22dc-121">Nach diesen Anpassungen sieht der **Inspektor** -Bereich für die Videodatei wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e22dc-121">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![Video-Eigenschaften Bereich](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="e22dc-123">Fügen Sie als nächstes der **Hierarchie** ein **Video Player** -Objekt hinzu, indem Sie mit der rechten Maustaste auf den Bereich **Hierarchie** klicken und **Video > Video Player** auswählen:</span><span class="sxs-lookup"><span data-stu-id="e22dc-123">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player** :</span></span>

![Video Player in der Hierarchie](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="e22dc-125">Abspielen von Videos auf einem Quadranten</span><span class="sxs-lookup"><span data-stu-id="e22dc-125">Play video onto a quadrangle</span></span>
<span data-ttu-id="e22dc-126">Das **Video Player** -Objekt benötigt ein texturiertes Spielobjekt, auf dem das Video dargestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e22dc-126">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="e22dc-127">Fügen Sie zunächst der **Hierarchie** ein **Quad** hinzu, indem Sie mit der rechten Maustaste auf den Bereich **Hierarchie** klicken und **3D-Objekt-> Quad** :</span><span class="sxs-lookup"><span data-stu-id="e22dc-127">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad** :</span></span>

![Quad zur Hierarchie hinzufügen](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="e22dc-129">Um sicherzustellen, dass das **Quad** vor dem Benutzer angezeigt wird, wenn die Anwendung gestartet wird, legen Sie die **Positions** -Eigenschaft des **Quad** auf (0, 0, 2) und die **Scale** -Eigenschaft auf (1,28, 0,72, 1) fest.</span><span class="sxs-lookup"><span data-stu-id="e22dc-129">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="e22dc-130">Nachdem diese Änderungen vorgenommen wurden, sieht die **Transformations** Komponente im **Inspektor** -Bereich für das **Quad** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e22dc-130">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Quad-Transformation](images/spatial-audio/quad-transform.png)

<span data-ttu-id="e22dc-132">Um das Vierfache mit **Video zu strukturieren** , erstellen Sie eine neue **Rendering-Textur** .</span><span class="sxs-lookup"><span data-stu-id="e22dc-132">To texture the **Quad** with video, create a new **Render Texture** .</span></span> <span data-ttu-id="e22dc-133">Klicken Sie im **Projekt** Bereich mit der rechten Maustaste, und wählen Sie **Create-> Rendering Texture** aus:</span><span class="sxs-lookup"><span data-stu-id="e22dc-133">In the **Project** pane, right-click and choose **Create -> Render Texture** :</span></span>

![Rendering-Textur erstellen](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="e22dc-135">Legen Sie im **inspektorbereich** der **Rendering-Textur** die **size** -Eigenschaft so fest, dass Sie mit der nativen Auflösung des Videos in Auflösung von 1280X720 identisch ist</span><span class="sxs-lookup"><span data-stu-id="e22dc-135">On the **Inspector** pane of the **Render Texture** , set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="e22dc-136">Um dann eine gute Renderingleistung auf hololens 2 sicherzustellen, legen Sie die **Tiefe Puffer** Eigenschaft auf **mindestens 16 Bits** fest.</span><span class="sxs-lookup"><span data-stu-id="e22dc-136">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth** .</span></span> <span data-ttu-id="e22dc-137">Nach diesen Einstellungen sieht der **Inspektor** -Bereich für die **Rendering-Textur** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e22dc-137">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![Rendering-Textur Eigenschaften](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="e22dc-139">Verwenden Sie als **nächstes die neue** Rendering- **Textur** als Textur für das Vierfache:</span><span class="sxs-lookup"><span data-stu-id="e22dc-139">Next, use your new **Render Texture** as the texture for the **Quad** :</span></span>
1. <span data-ttu-id="e22dc-140">Ziehen Sie **die Rendering-Textur** aus dem **Projekt** Bereich **auf das Vierfache in der** **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="e22dc-140">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="e22dc-141">Um eine gute Leistung bei hololens 2 sicherzustellen, wählen Sie im **Inspektor** -Bereich für den **Quad** den **Standard-Shader von Mixed Reality Toolkit** aus.</span><span class="sxs-lookup"><span data-stu-id="e22dc-141">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad** , select the **Mixed Reality Toolkit Standard Shader** .</span></span>

<span data-ttu-id="e22dc-142">Mit diesen Einstellungen sieht die **Textur** Komponente im **Inspektor** -Bereich für das **Quad** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e22dc-142">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Vier Textur Eigenschaften](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="e22dc-144">Öffnen Sie den **Inspektor** -Bereich für den **Video Player** , und legen Sie Folgendes fest, um den neuen **Video Player** und die **Rendering-Textur** für die Wiedergabe des Videoclips</span><span class="sxs-lookup"><span data-stu-id="e22dc-144">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="e22dc-145">Legen Sie die Eigenschaft " **Video Clip** " auf Ihre Videodatei fest.</span><span class="sxs-lookup"><span data-stu-id="e22dc-145">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="e22dc-146">Aktivieren Sie das Kontrollkästchen **Schleife** .</span><span class="sxs-lookup"><span data-stu-id="e22dc-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="e22dc-147">Festlegen der **Ziel Textur** auf die neue rendertextur</span><span class="sxs-lookup"><span data-stu-id="e22dc-147">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="e22dc-148">Der **Inspektor** -Bereich für den **Video Player** sieht nun wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e22dc-148">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![Video Player-Eigenschaften](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="e22dc-150">Spatialisieren der Audiodaten aus dem Video</span><span class="sxs-lookup"><span data-stu-id="e22dc-150">Spatialize the audio from the video</span></span>
<span data-ttu-id="e22dc-151">Erstellen Sie im **Inspektor** -Bereich **für das** vierfache eine **Audioquelle** , an die Sie die Audiodatei aus dem Video weiterleiten:</span><span class="sxs-lookup"><span data-stu-id="e22dc-151">In the **Inspector** pane for the **Quad** , create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="e22dc-152">Klicken Sie am unteren Rand des Bereichs auf **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="e22dc-152">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="e22dc-153">Hinzufügen einer **Audioquelle**</span><span class="sxs-lookup"><span data-stu-id="e22dc-153">Add an **Audio Source**</span></span>

<span data-ttu-id="e22dc-154">Dann in der **Audioquelle** :</span><span class="sxs-lookup"><span data-stu-id="e22dc-154">Then, on the **Audio Source** :</span></span>
* <span data-ttu-id="e22dc-155">**Ausgabe** auf Ihren Mixer festlegen</span><span class="sxs-lookup"><span data-stu-id="e22dc-155">Set **Output** to your mixer</span></span>
* <span data-ttu-id="e22dc-156">Aktivieren Sie das Feld **spatialize** .</span><span class="sxs-lookup"><span data-stu-id="e22dc-156">Check the **Spatialize** box</span></span>
* <span data-ttu-id="e22dc-157">Verschieben Sie den Schieberegler für **räumliche Blend** auf 1 (3D).</span><span class="sxs-lookup"><span data-stu-id="e22dc-157">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="e22dc-158">Nachdem diese Änderungen vorgenommen wurden, sieht die **audioquellkomponente** im **Inspektor** -Bereich für das **Quad** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e22dc-158">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Quad-audioquellinspektor](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="e22dc-160">Um den **Video Player** so festzulegen, dass seine Audiodaten an die **Audioquelle** auf dem **Quad** weitergeleitet werden, öffnen Sie den **Inspektor** -Bereich für den **Video Player** und:</span><span class="sxs-lookup"><span data-stu-id="e22dc-160">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad** , open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="e22dc-161">Legen Sie den **Audioausgabemodus** auf "Audioquelle" fest.</span><span class="sxs-lookup"><span data-stu-id="e22dc-161">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="e22dc-162">Legen Sie die Eigenschaft **Audioquelle** auf Quad fest.</span><span class="sxs-lookup"><span data-stu-id="e22dc-162">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="e22dc-163">Nachdem diese Änderungen vorgenommen wurden, sieht der Bereich **Inspector** für den **Video Player** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e22dc-163">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![Video Player-Audioquelle festlegen](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="e22dc-165">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="e22dc-165">Next steps</span></span>
<span data-ttu-id="e22dc-166">Testen Sie Ihre APP auf einem hololens 2 oder im Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="e22dc-166">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="e22dc-167">Sie sehen und hören das Video, und die Audiodaten aus dem Video werden räumlich.</span><span class="sxs-lookup"><span data-stu-id="e22dc-167">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e22dc-168">Kapitel 4</span><span class="sxs-lookup"><span data-stu-id="e22dc-168">Chapter 4</span></span>](unity-spatial-audio-ch4.md) 

