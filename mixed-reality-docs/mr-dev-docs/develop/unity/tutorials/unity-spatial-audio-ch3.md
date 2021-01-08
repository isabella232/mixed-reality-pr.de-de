---
title: Versehen des Audiosignals eines Videoclips mit räumlichen Effekten
description: Erfahren Sie, wie Sie ein Video Medienobjekt in Ihr Unity Mixed Reality-Projekt importieren und die Audiodaten aus dem Video eingrenzen.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer, Video Import, Video Player
ms.openlocfilehash: 211d1e32a8137444d0f33d442a60067dcd77ca36
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007411"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="8bd6c-104">Versehen des Audiosignals eines Videoclips mit räumlichen Effekten</span><span class="sxs-lookup"><span data-stu-id="8bd6c-104">Spatializing audio from a video</span></span>

<span data-ttu-id="8bd6c-105">In diesem dritten Kapitel des Moduls Spatial-Audiodaten der Unity-Lernprogramme hololens 2 werden Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-105">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="8bd6c-106">Importieren eines Videos und Hinzufügen eines Video Players</span><span class="sxs-lookup"><span data-stu-id="8bd6c-106">Import a video and add a Video Player</span></span>
* <span data-ttu-id="8bd6c-107">Video auf einem Quadranten abspielen</span><span class="sxs-lookup"><span data-stu-id="8bd6c-107">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="8bd6c-108">Leiten Sie Audiodaten aus dem Video an das Quadrangle weiter, und räumlichen Sie die Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-108">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="8bd6c-109">Importieren eines Videos und Hinzufügen eines Video Players</span><span class="sxs-lookup"><span data-stu-id="8bd6c-109">Import a video and add a Video Player</span></span>

<span data-ttu-id="8bd6c-110">Ziehen Sie eine Videodatei in das **Projekt** Bereich Ihres Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-110">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="8bd6c-111">Sie können [dieses Video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) aus dem Beispiel Projekt für räumliche Audiodaten verwenden.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-111">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![Ordner "Assets" mit Video](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="8bd6c-113">Durch das Anpassen der Qualitätseinstellungen für den Videoclip kann die reibungslose Wiedergabe auf hololens 2 sichergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-113">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="8bd6c-114">Klicken Sie im **Projekt** Bereich auf die Videodatei.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-114">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="8bd6c-115">Überschreiben Sie im **Inspektor** -Bereich der Videodatei die Einstellungen für Windows Store-Apps und:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-115">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="8bd6c-116">**Transcode** aktivieren</span><span class="sxs-lookup"><span data-stu-id="8bd6c-116">Enable **Transcode**</span></span>
* <span data-ttu-id="8bd6c-117">Legen Sie **Codec** auf H264 fest.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-117">Set **Codec** to H264</span></span>
* <span data-ttu-id="8bd6c-118">**Modus "Bitrate** " auf "niedrig" festlegen</span><span class="sxs-lookup"><span data-stu-id="8bd6c-118">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="8bd6c-119">Legen Sie **räumliche Qualität** auf mittlere räumliche Qualität fest.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-119">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="8bd6c-120">Nach diesen Anpassungen sieht der **Inspektor** -Bereich für die Videodatei wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-120">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![Video-Eigenschaften Bereich](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="8bd6c-122">Fügen Sie als nächstes der **Hierarchie** ein **Video Player** -Objekt hinzu, indem Sie mit der rechten Maustaste auf den Bereich **Hierarchie** klicken und **Video > Video Player** auswählen:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-122">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![Video Player in der Hierarchie](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="8bd6c-124">Abspielen von Videos auf einem Quadranten</span><span class="sxs-lookup"><span data-stu-id="8bd6c-124">Play video onto a quadrangle</span></span>

<span data-ttu-id="8bd6c-125">Das **Video Player** -Objekt benötigt ein texturiertes Spielobjekt, auf dem das Video dargestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-125">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="8bd6c-126">Fügen Sie zunächst der **Hierarchie** ein **Quad** hinzu, indem Sie mit der rechten Maustaste auf den Bereich **Hierarchie** klicken und **3D-Objekt-> Quad**:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-126">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![Quad zur Hierarchie hinzufügen](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="8bd6c-128">Um sicherzustellen, dass das **Quad** vor dem Benutzer angezeigt wird, wenn die Anwendung gestartet wird, legen Sie die **Positions** -Eigenschaft des **Quad** auf (0, 0, 2) und die **Scale** -Eigenschaft auf (1,28, 0,72, 1) fest.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-128">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="8bd6c-129">Nachdem diese Änderungen vorgenommen wurden, sieht die **Transformations** Komponente im **Inspektor** -Bereich für das **Quad** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-129">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Quad-Transformation](images/spatial-audio/quad-transform.png)

<span data-ttu-id="8bd6c-131">Um das Vierfache mit **Video zu strukturieren** , erstellen Sie eine neue **Rendering-Textur**.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-131">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="8bd6c-132">Klicken Sie im **Projekt** Bereich mit der rechten Maustaste, und wählen Sie **Create-> Rendering Texture** aus:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-132">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![Rendering-Textur erstellen](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="8bd6c-134">Legen Sie im **inspektorbereich** der **Rendering-Textur** die **size** -Eigenschaft so fest, dass Sie mit der nativen Auflösung des Videos in Auflösung von 1280X720 identisch ist</span><span class="sxs-lookup"><span data-stu-id="8bd6c-134">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="8bd6c-135">Um dann eine gute Renderingleistung auf hololens 2 sicherzustellen, legen Sie die **Tiefe Puffer** Eigenschaft auf **mindestens 16 Bits** fest.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-135">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="8bd6c-136">Nach diesen Einstellungen sieht der **Inspektor** -Bereich für die **Rendering-Textur** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-136">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![Rendering-Textur Eigenschaften](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="8bd6c-138">Verwenden Sie als **nächstes die neue** Rendering- **Textur** als Textur für das Vierfache:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-138">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="8bd6c-139">Ziehen Sie **die Rendering-Textur** aus dem **Projekt** Bereich **auf das Vierfache in der** **Hierarchie** .</span><span class="sxs-lookup"><span data-stu-id="8bd6c-139">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="8bd6c-140">Um eine gute Leistung bei hololens 2 sicherzustellen, wählen Sie im **Inspektor** -Bereich für den **Quad** den **Standard-Shader von Mixed Reality Toolkit** aus.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-140">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="8bd6c-141">Mit diesen Einstellungen sieht die **Textur** Komponente im **Inspektor** -Bereich für das **Quad** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-141">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Vier Textur Eigenschaften](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="8bd6c-143">Öffnen Sie den **Inspektor** -Bereich für den **Video Player** , und legen Sie Folgendes fest, um den neuen **Video Player** und die **Rendering-Textur** für die Wiedergabe des Videoclips</span><span class="sxs-lookup"><span data-stu-id="8bd6c-143">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="8bd6c-144">Legen Sie die Eigenschaft " **Video Clip** " auf Ihre Videodatei fest.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-144">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="8bd6c-145">Aktivieren Sie das Kontrollkästchen **Schleife** .</span><span class="sxs-lookup"><span data-stu-id="8bd6c-145">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="8bd6c-146">Festlegen der **Ziel Textur** auf die neue rendertextur</span><span class="sxs-lookup"><span data-stu-id="8bd6c-146">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="8bd6c-147">Der **Inspektor** -Bereich für den **Video Player** sieht nun wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-147">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![Video Player-Eigenschaften](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="8bd6c-149">Spatialisieren der Audiodaten aus dem Video</span><span class="sxs-lookup"><span data-stu-id="8bd6c-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="8bd6c-150">Erstellen Sie im **Inspektor** -Bereich **für das** vierfache eine **Audioquelle** , an die Sie die Audiodatei aus dem Video weiterleiten:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-150">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="8bd6c-151">Klicken Sie am unteren Rand des Bereichs auf **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="8bd6c-151">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="8bd6c-152">Hinzufügen einer **Audioquelle**</span><span class="sxs-lookup"><span data-stu-id="8bd6c-152">Add an **Audio Source**</span></span>

<span data-ttu-id="8bd6c-153">Dann in der **Audioquelle**:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-153">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="8bd6c-154">**Ausgabe** auf Ihren Mixer festlegen</span><span class="sxs-lookup"><span data-stu-id="8bd6c-154">Set **Output** to your mixer</span></span>
* <span data-ttu-id="8bd6c-155">Aktivieren Sie das Feld **spatialize** .</span><span class="sxs-lookup"><span data-stu-id="8bd6c-155">Check the **Spatialize** box</span></span>
* <span data-ttu-id="8bd6c-156">Verschieben Sie den Schieberegler für **räumliche Blend** auf 1 (3D).</span><span class="sxs-lookup"><span data-stu-id="8bd6c-156">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="8bd6c-157">Nachdem diese Änderungen vorgenommen wurden, sieht die **audioquellkomponente** im **Inspektor** -Bereich für das **Quad** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-157">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Quad-audioquellinspektor](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="8bd6c-159">Um den **Video Player** so festzulegen, dass seine Audiodaten an die **Audioquelle** auf dem **Quad** weitergeleitet werden, öffnen Sie den **Inspektor** -Bereich für den **Video Player** und:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-159">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="8bd6c-160">Legen Sie den **Audioausgabemodus** auf "Audioquelle" fest.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-160">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="8bd6c-161">Legen Sie die Eigenschaft **Audioquelle** auf Quad fest.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-161">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="8bd6c-162">Nachdem diese Änderungen vorgenommen wurden, sieht der Bereich **Inspector** für den **Video Player** wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8bd6c-162">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![Video Player-Audioquelle festlegen](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="8bd6c-164">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="8bd6c-164">Next steps</span></span>

<span data-ttu-id="8bd6c-165">Testen Sie Ihre APP auf einem hololens 2 oder im Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-165">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="8bd6c-166">Sie sehen und hören das Video, und die Audiodaten aus dem Video werden räumlich.</span><span class="sxs-lookup"><span data-stu-id="8bd6c-166">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8bd6c-167">Kapitel 4</span><span class="sxs-lookup"><span data-stu-id="8bd6c-167">Chapter 4</span></span>](unity-spatial-audio-ch4.md) 

