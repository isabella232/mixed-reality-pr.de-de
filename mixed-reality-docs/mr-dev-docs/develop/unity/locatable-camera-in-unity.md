---
title: Ausrichtbare Kamera in Unity
description: Erfahren Sie, wie Sie ein Foto in einer Datei oder einem Texture2D aufzeichnen, wie Sie ein Foto erfassen und mit den Rohdaten Bytes interagieren und wie Sie ein Video erfassen.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Foto, Video, hololens, Kamera, Unity, loalisierbar
ms.openlocfilehash: dfbbcc21db1247a7250e5049bfd1c4f89976ac15
ms.sourcegitcommit: 8e91ff47ef70e80a41137f80aa1093e711d27bf7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957800"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="34fce-104">Ausrichtbare Kamera in Unity</span><span class="sxs-lookup"><span data-stu-id="34fce-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="34fce-105">Aktivieren der Funktion für Foto-Video Kamera</span><span class="sxs-lookup"><span data-stu-id="34fce-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="34fce-106">Die "Webcam"-Funktion muss für eine APP deklariert werden, um die [Kamera](../platform-capabilities-and-apis/locatable-camera.md)zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fce-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>
1. <span data-ttu-id="34fce-107">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zur Seite "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="34fce-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="34fce-108">Klicken Sie auf die Registerkarte "Windows Store".</span><span class="sxs-lookup"><span data-stu-id="34fce-108">Click the "Windows Store" tab</span></span>
3. <span data-ttu-id="34fce-109">Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktionen für **Webcam** und **Mikrofon** .</span><span class="sxs-lookup"><span data-stu-id="34fce-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="34fce-110">Nur ein einzelner Vorgang kann gleichzeitig mit der Kamera erfolgen.</span><span class="sxs-lookup"><span data-stu-id="34fce-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="34fce-111">Um zu ermitteln, in welchem Modus (Foto, Video oder None) sich die Kamera derzeit befindet, können Sie unityengine. XR. WSA. Webcam. Mode überprüfen.</span><span class="sxs-lookup"><span data-stu-id="34fce-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="34fce-112">Foto Erfassung</span><span class="sxs-lookup"><span data-stu-id="34fce-112">Photo Capture</span></span>

<span data-ttu-id="34fce-113">**Namespace:** *unityengine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="34fce-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="34fce-114">**Typ:** *photocapture*</span><span class="sxs-lookup"><span data-stu-id="34fce-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="34fce-115">Mit dem Typ *photocapture* können Sie weiterhin Fotos mit der Foto Video Kamera aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="34fce-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="34fce-116">Das allgemeine Muster für die Verwendung von *Photo Capture* für die Aufnahme eines Fotos sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="34fce-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="34fce-117">Erstellen eines *photocapture* -Objekts</span><span class="sxs-lookup"><span data-stu-id="34fce-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="34fce-118">Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="34fce-118">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="34fce-119">Foto Modus über " *startphotomodeasync* " starten</span><span class="sxs-lookup"><span data-stu-id="34fce-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="34fce-120">Nehmen Sie das gewünschte Foto</span><span class="sxs-lookup"><span data-stu-id="34fce-120">Take the desired photo</span></span>
    * <span data-ttu-id="34fce-121">optionale Mit diesem Bild interagieren</span><span class="sxs-lookup"><span data-stu-id="34fce-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="34fce-122">Foto Modus abbrechen und Ressourcen bereinigen</span><span class="sxs-lookup"><span data-stu-id="34fce-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="34fce-123">Allgemeine Einrichtung für photocapture</span><span class="sxs-lookup"><span data-stu-id="34fce-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="34fce-124">Beginnen Sie für alle drei Verwendungszwecke mit denselben ersten drei Schritten.</span><span class="sxs-lookup"><span data-stu-id="34fce-124">For all three uses, start with the same first 3 steps above</span></span>

<span data-ttu-id="34fce-125">Beginnen Sie mit dem Erstellen eines *photocapture* -Objekts.</span><span class="sxs-lookup"><span data-stu-id="34fce-125">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="34fce-126">Speichern Sie anschließend das Objekt, legen Sie die Parameter fest, und starten Sie den Photo-Modus.</span><span class="sxs-lookup"><span data-stu-id="34fce-126">Next, store your object, set your parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="34fce-127">Am Ende verwenden Sie auch denselben Bereinigungs Code, der hier präsentiert wird.</span><span class="sxs-lookup"><span data-stu-id="34fce-127">In the end, you will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="34fce-128">Nachdem Sie diese Schritte ausgeführt haben, können Sie den Typ des zu erfassenden Fotos auswählen.</span><span class="sxs-lookup"><span data-stu-id="34fce-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="34fce-129">Fotos in einer Datei erfassen</span><span class="sxs-lookup"><span data-stu-id="34fce-129">Capture a Photo to a File</span></span>

<span data-ttu-id="34fce-130">Der einfachste Vorgang besteht darin, ein Foto direkt in einer Datei zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="34fce-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="34fce-131">Das Foto kann als jpg oder PNG gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="34fce-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="34fce-132">Wenn Sie den Foto Modus erfolgreich gestartet haben, erstellen Sie ein Foto, und speichern Sie es auf dem Datenträger</span><span class="sxs-lookup"><span data-stu-id="34fce-132">If you successfully started photo mode, take a photo and store it on disk</span></span>

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

<span data-ttu-id="34fce-133">Beenden Sie nach dem Erfassen des Fotos auf dem Datenträger den Photo-Modus, und bereinigen Sie die Objekte.</span><span class="sxs-lookup"><span data-stu-id="34fce-133">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="34fce-134">Fotos für ein Texture2D erfassen</span><span class="sxs-lookup"><span data-stu-id="34fce-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="34fce-135">Beim Erfassen von Daten in einem Texture2D ähnelt der Prozess stark der Erfassung auf dem Datenträger.</span><span class="sxs-lookup"><span data-stu-id="34fce-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="34fce-136">Befolgen Sie den oben beschriebenen Setup Vorgang.</span><span class="sxs-lookup"><span data-stu-id="34fce-136">Follow the set up process above.</span></span>

<span data-ttu-id="34fce-137">Erfassen Sie in *onphotomodestarted* einen Frame im Speicher.</span><span class="sxs-lookup"><span data-stu-id="34fce-137">In *OnPhotoModeStarted* , capture a frame to memory.</span></span>

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

<span data-ttu-id="34fce-138">Anschließend wenden Sie das Ergebnis auf eine Textur an und verwenden den oben aufgeführten allgemeinen Bereinigungs Code.</span><span class="sxs-lookup"><span data-stu-id="34fce-138">You will then apply your result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="34fce-139">Fotos erfassen und mit den Rohdaten Bytes interagieren</span><span class="sxs-lookup"><span data-stu-id="34fce-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="34fce-140">Wenn Sie mit den unformatierten Bytes eines in-Memory-Frames interagieren möchten, befolgen Sie die gleichen Setup Schritte wie oben und *onphotomodestarted* wie bei der Erfassung eines Fotos für eine Texture2D.</span><span class="sxs-lookup"><span data-stu-id="34fce-140">To interact with the raw bytes of an in memory frame, follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="34fce-141">Der Unterschied liegt in *oncapturedphototomemory* , wo Sie die Rohdaten Bytes erhalten und mit ihnen interagieren können.</span><span class="sxs-lookup"><span data-stu-id="34fce-141">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="34fce-142">In diesem Beispiel erstellen Sie eine *Liste <Color>* , die mithilfe von *setPixels ()* weiterverarbeitet oder auf eine Textur angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="34fce-142">In this example, you will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="34fce-143">Video Erfassung</span><span class="sxs-lookup"><span data-stu-id="34fce-143">Video Capture</span></span>

<span data-ttu-id="34fce-144">**Namespace:** *unityengine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="34fce-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="34fce-145">**Typ:** *Videocapture*</span><span class="sxs-lookup"><span data-stu-id="34fce-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="34fce-146">*Videocapture* funktioniert sehr ähnlich wie bei *photocapture* .</span><span class="sxs-lookup"><span data-stu-id="34fce-146">*VideoCapture* functions very similarly to *PhotoCapture* .</span></span> <span data-ttu-id="34fce-147">Die einzigen beiden Unterschiede sind, dass Sie einen Wert für Frames pro Sekunde (fps) angeben müssen, und Sie können nur direkt auf dem Datenträger als MP4-Datei speichern.</span><span class="sxs-lookup"><span data-stu-id="34fce-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="34fce-148">Die Schritte für die Verwendung von *Videocapture* lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="34fce-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="34fce-149">Erstellen eines *Videocapture* -Objekts</span><span class="sxs-lookup"><span data-stu-id="34fce-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="34fce-150">Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="34fce-150">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="34fce-151">Starten des Video Modus über *startvideomodeasync*</span><span class="sxs-lookup"><span data-stu-id="34fce-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="34fce-152">Aufzeichnen des Videos starten</span><span class="sxs-lookup"><span data-stu-id="34fce-152">Start recording video</span></span>
5. <span data-ttu-id="34fce-153">Aufzeichnen von Videos anhalten</span><span class="sxs-lookup"><span data-stu-id="34fce-153">Stop recording video</span></span>
6. <span data-ttu-id="34fce-154">Video Modus abbrechen und Ressourcen bereinigen</span><span class="sxs-lookup"><span data-stu-id="34fce-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="34fce-155">Erstellen Sie zunächst das *Videocapture* -Objekt *Videocapture m_VideoCapture = NULL;*</span><span class="sxs-lookup"><span data-stu-id="34fce-155">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="34fce-156">Richten Sie als nächstes die Parameter ein, die für die Aufzeichnung verwendet werden sollen, und starten Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="34fce-156">Next, set up the parameters you will want for the recording and start.</span></span>

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

<span data-ttu-id="34fce-157">Starten der Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="34fce-157">Once started, begin the recording</span></span>

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

<span data-ttu-id="34fce-158">Nachdem die Aufzeichnung gestartet wurde, können Sie die Benutzeroberfläche oder das Verhalten aktualisieren, um das Beenden zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="34fce-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="34fce-159">Hier melden Sie sich einfach an.</span><span class="sxs-lookup"><span data-stu-id="34fce-159">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="34fce-160">Zu einem späteren Zeitpunkt möchten Sie die Aufzeichnung anhalten.</span><span class="sxs-lookup"><span data-stu-id="34fce-160">At a later point, you will want to stop the recording.</span></span> <span data-ttu-id="34fce-161">Dies kann beispielsweise bei einem Timer oder einer Benutzereingabe vorkommen.</span><span class="sxs-lookup"><span data-stu-id="34fce-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="34fce-162">Wenn die Aufzeichnung beendet wurde, beenden Sie den Videomodus, und bereinigen Sie Ihre Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="34fce-162">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="34fce-163">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="34fce-163">Troubleshooting</span></span>
* <span data-ttu-id="34fce-164">Es sind keine Auflösungen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="34fce-164">No resolutions are available</span></span>
    * <span data-ttu-id="34fce-165">Stellen Sie sicher, dass die **Webcam** -Funktion in Ihrem Projekt angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="34fce-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="34fce-166">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="34fce-166">Next Development Checkpoint</span></span>

<span data-ttu-id="34fce-167">Wenn Sie der Unity-Entwicklungs-Prüfpunkt-Journey folgen, die wir festgelegt haben, sind Sie mitten in der Untersuchung der Funktionen und APIs der Mixed Reality-Plattform.</span><span class="sxs-lookup"><span data-stu-id="34fce-167">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="34fce-168">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="34fce-168">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="34fce-169">Fokuspunkt</span><span class="sxs-lookup"><span data-stu-id="34fce-169">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="34fce-170">Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:</span><span class="sxs-lookup"><span data-stu-id="34fce-170">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="34fce-171">Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets</span><span class="sxs-lookup"><span data-stu-id="34fce-171">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="34fce-172">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-platform-capabilities-and-apis) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="34fce-172">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="34fce-173">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="34fce-173">See Also</span></span>
* [<span data-ttu-id="34fce-174">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="34fce-174">Locatable camera</span></span>](../platform-capab ilities-and-apis/locatable-camera.md)
