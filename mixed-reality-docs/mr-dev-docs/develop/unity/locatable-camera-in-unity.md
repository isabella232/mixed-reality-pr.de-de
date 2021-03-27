---
title: Foto-Video Kamera in Unity
description: Erfahren Sie, wie Sie ein Foto in einer Datei oder einem Texture2D aufzeichnen, wie Sie ein Foto erfassen und mit den Rohdaten Bytes interagieren und wie Sie ein Video erfassen.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: Foto, Video, hololens, Kamera, Unity, loerable, PVC, Foto Videokamera, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Webcam, Foto Erfassung, Video Erfassung
ms.openlocfilehash: 1cae796a793036ed59c1d0805df76cb8ac143027
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636212"
---
# <a name="photo-video-camera-in-unity"></a><span data-ttu-id="81970-104">Foto-Video Kamera in Unity</span><span class="sxs-lookup"><span data-stu-id="81970-104">Photo Video camera in Unity</span></span>

## <a name="enabling-the-capability-for-camera-access"></a><span data-ttu-id="81970-105">Aktivieren der Funktion für den Kamera Zugriff</span><span class="sxs-lookup"><span data-stu-id="81970-105">Enabling the capability for camera access</span></span>

<span data-ttu-id="81970-106">Die "Webcam"-Funktion muss für eine APP deklariert werden, um die [Kamera](../platform-capabilities-and-apis/locatable-camera.md)zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="81970-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>

1. <span data-ttu-id="81970-107">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zur Seite "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="81970-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="81970-108">Wählen Sie die Registerkarte "Windows Store" aus.</span><span class="sxs-lookup"><span data-stu-id="81970-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="81970-109">Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktionen für **Webcam** und **Mikrofon** .</span><span class="sxs-lookup"><span data-stu-id="81970-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="81970-110">Nur ein einzelner Vorgang kann gleichzeitig mit der Kamera erfolgen.</span><span class="sxs-lookup"><span data-stu-id="81970-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="81970-111">Sie können überprüfen, in welchem Modus sich die Kamera derzeit in `UnityEngine.XR.WSA.WebCam.Mode` Unity 2018 und früher oder `UnityEngine.Windows.WebCam.Mode` in Unity 2019 und höher befindet.</span><span class="sxs-lookup"><span data-stu-id="81970-111">You can check which mode the camera is currently in with `UnityEngine.XR.WSA.WebCam.Mode` in Unity 2018 and earlier or `UnityEngine.Windows.WebCam.Mode` in Unity 2019  and later.</span></span> <span data-ttu-id="81970-112">Verfügbare Modi sind Foto, Video oder None.</span><span class="sxs-lookup"><span data-stu-id="81970-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="81970-113">Foto Erfassung</span><span class="sxs-lookup"><span data-stu-id="81970-113">Photo capture</span></span>

<span data-ttu-id="81970-114">**Namespace (vor Unity 2019):** *unityengine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="81970-114">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="81970-115">**Namespace (Unity 2019 und höher):** *unityengine. Windows. Webcam*</span><span class="sxs-lookup"><span data-stu-id="81970-115">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="81970-116">**Typ:** *photocapture*</span><span class="sxs-lookup"><span data-stu-id="81970-116">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="81970-117">Mit dem Typ *photocapture* können Sie weiterhin Fotos mit der Foto Video Kamera aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="81970-117">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="81970-118">Das allgemeine Muster für die Verwendung von *Photo Capture* für die Aufnahme eines Fotos sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="81970-118">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>

1. <span data-ttu-id="81970-119">Erstellen eines *photocapture* -Objekts</span><span class="sxs-lookup"><span data-stu-id="81970-119">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="81970-120">Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="81970-120">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="81970-121">Foto Modus über " *startphotomodeasync* " starten</span><span class="sxs-lookup"><span data-stu-id="81970-121">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="81970-122">Nehmen Sie das gewünschte Foto</span><span class="sxs-lookup"><span data-stu-id="81970-122">Take the photo you want</span></span>
    * <span data-ttu-id="81970-123">optionale Mit diesem Bild interagieren</span><span class="sxs-lookup"><span data-stu-id="81970-123">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="81970-124">Foto Modus abbrechen und Ressourcen bereinigen</span><span class="sxs-lookup"><span data-stu-id="81970-124">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="81970-125">Allgemeine Einrichtung für photocapture</span><span class="sxs-lookup"><span data-stu-id="81970-125">Common set-up for PhotoCapture</span></span>

<span data-ttu-id="81970-126">Beginnen Sie für alle drei Verwendungszwecke mit denselben ersten drei Schritten.</span><span class="sxs-lookup"><span data-stu-id="81970-126">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="81970-127">Beginnen Sie mit dem Erstellen eines *photocapture* -Objekts.</span><span class="sxs-lookup"><span data-stu-id="81970-127">Start by creating a *PhotoCapture* object</span></span>

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

<span data-ttu-id="81970-128">Speichern Sie anschließend das Objekt, legen Sie die Parameter fest, und starten Sie den Photo-Modus.</span><span class="sxs-lookup"><span data-stu-id="81970-128">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
private PhotoCapture photoCaptureObject = null;

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

<span data-ttu-id="81970-129">Am Ende verwenden Sie auch denselben Bereinigungs Code, der hier vorgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="81970-129">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

<span data-ttu-id="81970-130">Nachdem Sie diese Schritte ausgeführt haben, können Sie den Typ des zu erfassenden Fotos auswählen.</span><span class="sxs-lookup"><span data-stu-id="81970-130">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="81970-131">Aufnehmen eines Fotos in einer Datei</span><span class="sxs-lookup"><span data-stu-id="81970-131">Capture a photo to a file</span></span>

<span data-ttu-id="81970-132">Der einfachste Vorgang besteht darin, ein Foto direkt in einer Datei zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="81970-132">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="81970-133">Das Foto kann als jpg oder PNG gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="81970-133">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="81970-134">Wenn Sie den Foto Modus erfolgreich gestartet haben, erstellen Sie ein Foto, und speichern Sie es auf dem Datenträger</span><span class="sxs-lookup"><span data-stu-id="81970-134">If you successfully started photo mode, take a photo and store it on disk</span></span>

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

<span data-ttu-id="81970-135">Beenden Sie nach dem Erfassen des Fotos auf dem Datenträger den Photo-Modus, und bereinigen Sie die Objekte.</span><span class="sxs-lookup"><span data-stu-id="81970-135">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d-with-location"></a><span data-ttu-id="81970-136">Erfassen eines Fotos für eine Texture2D mit einem Speicherort</span><span class="sxs-lookup"><span data-stu-id="81970-136">Capture a photo to a Texture2D with location</span></span>

<span data-ttu-id="81970-137">Beim Erfassen von Daten in einem Texture2D ähnelt der Prozess der Erfassung auf dem Datenträger.</span><span class="sxs-lookup"><span data-stu-id="81970-137">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="81970-138">Befolgen Sie den obigen Setup Vorgang.</span><span class="sxs-lookup"><span data-stu-id="81970-138">Follow the setup process above.</span></span>

<span data-ttu-id="81970-139">Erfassen Sie in *onphotomodestarted* einen Frame im Speicher.</span><span class="sxs-lookup"><span data-stu-id="81970-139">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

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

<span data-ttu-id="81970-140">Anschließend wenden Sie das Ergebnis auf eine Textur an und verwenden den oben aufgeführten allgemeinen Bereinigungs Code.</span><span class="sxs-lookup"><span data-stu-id="81970-140">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

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

#### <a name="locatable-camera"></a><span data-ttu-id="81970-141">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="81970-141">Locatable camera</span></span>

<span data-ttu-id="81970-142">Um diese Textur in der Szene zu platzieren und mithilfe der abzurufbaren Kamera Matrizen anzuzeigen, fügen Sie in der Überprüfung den folgenden Code zu *oncapturedphototomemory* hinzu `result.success` :</span><span class="sxs-lookup"><span data-stu-id="81970-142">To place this texture in the scene and display it using the locatable camera matrices, add the following code to *OnCapturedPhotoToMemory* in the `result.success` check:</span></span>

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

<span data-ttu-id="81970-143">[Unity hat Beispielcode](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) zum Anwenden der Projektions Matrix auf einen bestimmten Shader in ihren Foren bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="81970-143">[Unity has provided sample code](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) for applying the projection matrix to a specific shader on their forums.</span></span>

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="81970-144">Fotos erfassen und mit den Rohdaten Bytes interagieren</span><span class="sxs-lookup"><span data-stu-id="81970-144">Capture a photo and interact with the raw bytes</span></span>

<span data-ttu-id="81970-145">Wenn Sie mit den unformatierten Bytes eines in-Memory-Frames interagieren möchten, führen Sie die gleichen Einrichtungsschritte wie oben und *onphotomodestarted* aus, wie bei der Erfassung eines Fotos für eine Texture2D.</span><span class="sxs-lookup"><span data-stu-id="81970-145">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="81970-146">Der Unterschied liegt in *oncapturedphototomemory* , wo Sie die Rohdaten Bytes erhalten und mit ihnen interagieren können.</span><span class="sxs-lookup"><span data-stu-id="81970-146">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="81970-147">In diesem Beispiel erstellen Sie eine *Liste <Color>* , die weiterverarbeitet oder über *setPixels ()* auf eine Textur angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="81970-147">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="81970-148">Video Erfassung</span><span class="sxs-lookup"><span data-stu-id="81970-148">Video capture</span></span>

<span data-ttu-id="81970-149">**Namespace (vor Unity 2019):** *unityengine. XR. WSA. Webcam*</span><span class="sxs-lookup"><span data-stu-id="81970-149">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="81970-150">**Namespace (Unity 2019 und höher):** *unityengine. Windows. Webcam*</span><span class="sxs-lookup"><span data-stu-id="81970-150">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="81970-151">**Typ:** *Videocapture*</span><span class="sxs-lookup"><span data-stu-id="81970-151">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="81970-152">*Videocapture* funktioniert ähnlich wie bei *photocapture*.</span><span class="sxs-lookup"><span data-stu-id="81970-152">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="81970-153">Die einzigen beiden Unterschiede sind, dass Sie einen Wert für Frames pro Sekunde (fps) angeben müssen, und Sie können nur direkt auf dem Datenträger als MP4-Datei speichern.</span><span class="sxs-lookup"><span data-stu-id="81970-153">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="81970-154">Die Schritte für die Verwendung von *Videocapture* lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="81970-154">The steps to use *VideoCapture* are as follows:</span></span>

1. <span data-ttu-id="81970-155">Erstellen eines *Videocapture* -Objekts</span><span class="sxs-lookup"><span data-stu-id="81970-155">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="81970-156">Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="81970-156">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="81970-157">Starten des Video Modus über *startvideomodeasync*</span><span class="sxs-lookup"><span data-stu-id="81970-157">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="81970-158">Aufzeichnen des Videos starten</span><span class="sxs-lookup"><span data-stu-id="81970-158">Start recording video</span></span>
5. <span data-ttu-id="81970-159">Aufzeichnen von Videos anhalten</span><span class="sxs-lookup"><span data-stu-id="81970-159">Stop recording video</span></span>
6. <span data-ttu-id="81970-160">Video Modus abbrechen und Ressourcen bereinigen</span><span class="sxs-lookup"><span data-stu-id="81970-160">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="81970-161">Erstellen Sie zunächst das *Videocapture* -Objekt *Videocapture m_VideoCapture = NULL;*</span><span class="sxs-lookup"><span data-stu-id="81970-161">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

<span data-ttu-id="81970-162">Richten Sie als nächstes die Parameter ein, die Sie für die Aufzeichnung benötigen, und starten Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="81970-162">Next, set up the parameters you'll want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated(VideoCapture videoCapture)
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

<span data-ttu-id="81970-163">Starten der Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="81970-163">Once started, begin the recording</span></span>

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

<span data-ttu-id="81970-164">Nachdem die Aufzeichnung gestartet wurde, können Sie die Benutzeroberfläche oder das Verhalten aktualisieren, um das Beenden zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="81970-164">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="81970-165">Hier melden Sie sich einfach an.</span><span class="sxs-lookup"><span data-stu-id="81970-165">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

<span data-ttu-id="81970-166">Zu einem späteren Zeitpunkt möchten Sie die Aufzeichnung beispielsweise mithilfe eines Timers oder einer Benutzereingabe anhalten.</span><span class="sxs-lookup"><span data-stu-id="81970-166">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

<span data-ttu-id="81970-167">Wenn die Aufzeichnung beendet wurde, beenden Sie den Videomodus, und bereinigen Sie Ihre Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="81970-167">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="81970-168">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="81970-168">Troubleshooting</span></span>

* <span data-ttu-id="81970-169">Es sind keine Auflösungen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="81970-169">No resolutions are available</span></span>
  * <span data-ttu-id="81970-170">Stellen Sie sicher, dass die **Webcam** -Funktion in Ihrem Projekt angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="81970-170">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="81970-171">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="81970-171">Next Development Checkpoint</span></span>

<span data-ttu-id="81970-172">Wenn Sie der Unity-Entwicklungs-Prüfpunkt-Journey folgen, die wir festgelegt haben, sind Sie mitten in der Untersuchung der Funktionen und APIs der Mixed Reality-Plattform.</span><span class="sxs-lookup"><span data-stu-id="81970-172">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="81970-173">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="81970-173">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="81970-174">Fokuspunkt</span><span class="sxs-lookup"><span data-stu-id="81970-174">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="81970-175">Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:</span><span class="sxs-lookup"><span data-stu-id="81970-175">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="81970-176">Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets</span><span class="sxs-lookup"><span data-stu-id="81970-176">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="81970-177">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-advanced-features) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="81970-177">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="81970-178">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="81970-178">See Also</span></span>

* [<span data-ttu-id="81970-179">Ausrichtbare Kamera</span><span class="sxs-lookup"><span data-stu-id="81970-179">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)