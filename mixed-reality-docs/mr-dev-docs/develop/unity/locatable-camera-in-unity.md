---
title: Ausrichtbare Kamera in Unity
description: Erfahren Sie, wie Sie ein Foto in einer Datei oder einem Texture2D aufzeichnen, wie Sie ein Foto erfassen und mit den Rohdaten Bytes interagieren und wie Sie ein Video erfassen.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Foto, Video, hololens, Kamera, Unity, loerable, PVC, Foto Videokamera, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Webcam, Foto Erfassung, Video Erfassung
ms.openlocfilehash: 125521206421acbcc4c9ad6e5fb371314ddb48f2
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010101"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="866bb-104">Ausrichtbare Kamera in Unity</span><span class="sxs-lookup"><span data-stu-id="866bb-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="866bb-105">Aktivieren der Funktion für Foto-Video Kamera</span><span class="sxs-lookup"><span data-stu-id="866bb-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="866bb-106">Die "Webcam"-Funktion muss für eine APP deklariert werden, um die [Kamera](../platform-capabilities-and-apis/locatable-camera.md)zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="866bb-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>
1. <span data-ttu-id="866bb-107">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zur Seite "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="866bb-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="866bb-108">Wählen Sie die Registerkarte "Windows Store" aus.</span><span class="sxs-lookup"><span data-stu-id="866bb-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="866bb-109">Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktionen für **Webcam** und **Mikrofon** .</span><span class="sxs-lookup"><span data-stu-id="866bb-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="866bb-110">Nur ein einzelner Vorgang kann gleichzeitig mit der Kamera erfolgen.</span><span class="sxs-lookup"><span data-stu-id="866bb-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="866bb-111">Sie können den Modus, in dem sich die Kamera derzeit befindet, mit unityengine. XR. WSA. Webcam. Mode überprüfen.</span><span class="sxs-lookup"><span data-stu-id="866bb-111">You can check with mode the camera is currently in with UnityEngine.XR.WSA.WebCam.Mode.</span></span> <span data-ttu-id="866bb-112">Verfügbare Modi sind Foto, Video oder None.</span><span class="sxs-lookup"><span data-stu-id="866bb-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="866bb-113">Foto Erfassung</span><span class="sxs-lookup"><span data-stu-id="866bb-113">Photo Capture</span></span>

<span data-ttu-id="866bb-114">**Namespace:** *unityengine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="866bb-114">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="866bb-115">**Typ:** *photocapture*</span><span class="sxs-lookup"><span data-stu-id="866bb-115">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="866bb-116">Mit dem Typ *photocapture* können Sie weiterhin Fotos mit der Foto Video Kamera aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="866bb-116">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="866bb-117">Das allgemeine Muster für die Verwendung von *Photo Capture* für die Aufnahme eines Fotos sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="866bb-117">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="866bb-118">Erstellen eines *photocapture* -Objekts</span><span class="sxs-lookup"><span data-stu-id="866bb-118">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="866bb-119">Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="866bb-119">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="866bb-120">Foto Modus über " *startphotomodeasync* " starten</span><span class="sxs-lookup"><span data-stu-id="866bb-120">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="866bb-121">Nehmen Sie das gewünschte Foto</span><span class="sxs-lookup"><span data-stu-id="866bb-121">Take the photo you want</span></span>
    * <span data-ttu-id="866bb-122">optionale Mit diesem Bild interagieren</span><span class="sxs-lookup"><span data-stu-id="866bb-122">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="866bb-123">Foto Modus abbrechen und Ressourcen bereinigen</span><span class="sxs-lookup"><span data-stu-id="866bb-123">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="866bb-124">Allgemeine Einrichtung für photocapture</span><span class="sxs-lookup"><span data-stu-id="866bb-124">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="866bb-125">Beginnen Sie für alle drei Verwendungszwecke mit denselben ersten drei Schritten.</span><span class="sxs-lookup"><span data-stu-id="866bb-125">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="866bb-126">Beginnen Sie mit dem Erstellen eines *photocapture* -Objekts.</span><span class="sxs-lookup"><span data-stu-id="866bb-126">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="866bb-127">Speichern Sie anschließend das Objekt, legen Sie die Parameter fest, und starten Sie den Photo-Modus.</span><span class="sxs-lookup"><span data-stu-id="866bb-127">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

<span data-ttu-id="866bb-128">Am Ende verwenden Sie auch denselben Bereinigungs Code, der hier vorgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="866bb-128">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="866bb-129">Nachdem Sie diese Schritte ausgeführt haben, können Sie den Typ des zu erfassenden Fotos auswählen.</span><span class="sxs-lookup"><span data-stu-id="866bb-129">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="866bb-130">Fotos in einer Datei erfassen</span><span class="sxs-lookup"><span data-stu-id="866bb-130">Capture a Photo to a File</span></span>

<span data-ttu-id="866bb-131">Der einfachste Vorgang besteht darin, ein Foto direkt in einer Datei zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="866bb-131">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="866bb-132">Das Foto kann als jpg oder PNG gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="866bb-132">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="866bb-133">Wenn Sie den Foto Modus erfolgreich gestartet haben, erstellen Sie ein Foto, und speichern Sie es auf dem Datenträger</span><span class="sxs-lookup"><span data-stu-id="866bb-133">If you successfully started photo mode, take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="866bb-134">Beenden Sie nach dem Erfassen des Fotos auf dem Datenträger den Photo-Modus, und bereinigen Sie die Objekte.</span><span class="sxs-lookup"><span data-stu-id="866bb-134">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="866bb-135">Fotos für ein Texture2D erfassen</span><span class="sxs-lookup"><span data-stu-id="866bb-135">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="866bb-136">Beim Erfassen von Daten in einem Texture2D ähnelt der Prozess der Erfassung auf dem Datenträger.</span><span class="sxs-lookup"><span data-stu-id="866bb-136">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="866bb-137">Befolgen Sie den obigen Setup Vorgang.</span><span class="sxs-lookup"><span data-stu-id="866bb-137">Follow the setup process above.</span></span>

<span data-ttu-id="866bb-138">Erfassen Sie in *onphotomodestarted* einen Frame im Speicher.</span><span class="sxs-lookup"><span data-stu-id="866bb-138">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="866bb-139">Anschließend wenden Sie das Ergebnis auf eine Textur an und verwenden den oben aufgeführten allgemeinen Bereinigungs Code.</span><span class="sxs-lookup"><span data-stu-id="866bb-139">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="866bb-140">Fotos erfassen und mit den Rohdaten Bytes interagieren</span><span class="sxs-lookup"><span data-stu-id="866bb-140">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="866bb-141">Wenn Sie mit den unformatierten Bytes eines in-Memory-Frames interagieren möchten, führen Sie die gleichen Einrichtungsschritte wie oben und *onphotomodestarted* aus, wie bei der Erfassung eines Fotos für eine Texture2D.</span><span class="sxs-lookup"><span data-stu-id="866bb-141">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="866bb-142">Der Unterschied liegt in *oncapturedphototomemory* , wo Sie die Rohdaten Bytes erhalten und mit ihnen interagieren können.</span><span class="sxs-lookup"><span data-stu-id="866bb-142">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="866bb-143">In diesem Beispiel erstellen Sie eine *Liste <Color>* , die weiterverarbeitet oder über *setPixels ()* auf eine Textur angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="866bb-143">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a><span data-ttu-id="866bb-144">Video Erfassung</span><span class="sxs-lookup"><span data-stu-id="866bb-144">Video Capture</span></span>

<span data-ttu-id="866bb-145">**Namespace:** *unityengine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="866bb-145">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="866bb-146">**Typ:** *Videocapture*</span><span class="sxs-lookup"><span data-stu-id="866bb-146">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="866bb-147">*Videocapture* funktioniert ähnlich wie bei *photocapture*.</span><span class="sxs-lookup"><span data-stu-id="866bb-147">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="866bb-148">Die einzigen beiden Unterschiede sind, dass Sie einen Wert für Frames pro Sekunde (fps) angeben müssen, und Sie können nur direkt auf dem Datenträger als MP4-Datei speichern.</span><span class="sxs-lookup"><span data-stu-id="866bb-148">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="866bb-149">Die Schritte für die Verwendung von *Videocapture* lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="866bb-149">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="866bb-150">Erstellen eines *Videocapture* -Objekts</span><span class="sxs-lookup"><span data-stu-id="866bb-150">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="866bb-151">Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="866bb-151">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="866bb-152">Starten des Video Modus über *startvideomodeasync*</span><span class="sxs-lookup"><span data-stu-id="866bb-152">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="866bb-153">Aufzeichnen des Videos starten</span><span class="sxs-lookup"><span data-stu-id="866bb-153">Start recording video</span></span>
5. <span data-ttu-id="866bb-154">Aufzeichnen von Videos anhalten</span><span class="sxs-lookup"><span data-stu-id="866bb-154">Stop recording video</span></span>
6. <span data-ttu-id="866bb-155">Video Modus abbrechen und Ressourcen bereinigen</span><span class="sxs-lookup"><span data-stu-id="866bb-155">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="866bb-156">Erstellen Sie zunächst das *Videocapture* -Objekt *Videocapture m_VideoCapture = NULL;*</span><span class="sxs-lookup"><span data-stu-id="866bb-156">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="866bb-157">Richten Sie als nächstes die Parameter ein, die Sie für die Aufzeichnung benötigen, und starten Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="866bb-157">Next, set up the parameters you'll want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

<span data-ttu-id="866bb-158">Starten der Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="866bb-158">Once started, begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

<span data-ttu-id="866bb-159">Nachdem die Aufzeichnung gestartet wurde, können Sie die Benutzeroberfläche oder das Verhalten aktualisieren, um das Beenden zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="866bb-159">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="866bb-160">Hier melden Sie sich einfach an.</span><span class="sxs-lookup"><span data-stu-id="866bb-160">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="866bb-161">Zu einem späteren Zeitpunkt möchten Sie die Aufzeichnung beispielsweise mithilfe eines Timers oder einer Benutzereingabe anhalten.</span><span class="sxs-lookup"><span data-stu-id="866bb-161">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="866bb-162">Wenn die Aufzeichnung beendet wurde, beenden Sie den Videomodus, und bereinigen Sie Ihre Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="866bb-162">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a><span data-ttu-id="866bb-163">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="866bb-163">Troubleshooting</span></span>
* <span data-ttu-id="866bb-164">Es sind keine Auflösungen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="866bb-164">No resolutions are available</span></span>
    * <span data-ttu-id="866bb-165">Stellen Sie sicher, dass die **Webcam** -Funktion in Ihrem Projekt angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="866bb-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="866bb-166">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="866bb-166">Next Development Checkpoint</span></span>

<span data-ttu-id="866bb-167">Wenn Sie der Unity-Entwicklungs-Prüfpunkt-Journey folgen, die wir festgelegt haben, sind Sie mitten in der Untersuchung der Funktionen und APIs der Mixed Reality-Plattform.</span><span class="sxs-lookup"><span data-stu-id="866bb-167">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="866bb-168">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="866bb-168">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="866bb-169">Fokuspunkt</span><span class="sxs-lookup"><span data-stu-id="866bb-169">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="866bb-170">Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:</span><span class="sxs-lookup"><span data-stu-id="866bb-170">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="866bb-171">Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets</span><span class="sxs-lookup"><span data-stu-id="866bb-171">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="866bb-172">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-platform-capabilities-and-apis) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="866bb-172">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="866bb-173">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="866bb-173">See Also</span></span>
* [<span data-ttu-id="866bb-174">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="866bb-174">Locatable camera</span></span>](../platform-capab ilities-and-apis/locatable-camera.md)
