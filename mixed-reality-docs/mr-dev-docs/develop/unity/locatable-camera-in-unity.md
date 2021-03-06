---
title: Ausrichtbare Kamera in Unity
description: Erfahren Sie, wie Sie ein Foto in einer Datei oder einem Texture2D aufzeichnen, wie Sie ein Foto erfassen und mit den Rohdaten Bytes interagieren und wie Sie ein Video erfassen.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Foto, Video, hololens, Kamera, Unity, loerable, PVC, Foto Videokamera, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Webcam, Foto Erfassung, Video Erfassung
ms.openlocfilehash: ccf0c17a5f419341e64a87fb9ef04ef0a40c2a33
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236901"
---
# <a name="locatable-camera-in-unity"></a>Ausrichtbare Kamera in Unity

## <a name="enabling-the-capability-for-photo-video-camera"></a>Aktivieren der Funktion für Foto-Video Kamera

Die "Webcam"-Funktion muss für eine APP deklariert werden, um die [Kamera](../platform-capabilities-and-apis/locatable-camera.md)zu verwenden.
1. Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zur Seite "> Projekteinstellungen bearbeiten > Player" navigieren.
2. Wählen Sie die Registerkarte "Windows Store" aus.
3. Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktionen für **Webcam** und **Mikrofon** .

Nur ein einzelner Vorgang kann gleichzeitig mit der Kamera erfolgen. Sie können den Modus, in dem sich die Kamera derzeit befindet, mit unityengine. XR. WSA. Webcam. Mode überprüfen. Verfügbare Modi sind Foto, Video oder None.

## <a name="photo-capture"></a>Foto Erfassung

**Namespace:**  
*Unityengine. XR. WSA. Webcam (Unity \~ 2018) unityengine. Windows. Webcam (Unity 2019 \~ )*<br>
**Typ:** *photocapture*

Mit dem Typ *photocapture* können Sie weiterhin Fotos mit der Foto Video Kamera aufnehmen. Das allgemeine Muster für die Verwendung von *Photo Capture* für die Aufnahme eines Fotos sieht wie folgt aus:
1. Erstellen eines *photocapture* -Objekts
2. Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.
3. Foto Modus über " *startphotomodeasync* " starten
4. Nehmen Sie das gewünschte Foto
    * optionale Mit diesem Bild interagieren
5. Foto Modus abbrechen und Ressourcen bereinigen

### <a name="common-set-up-for-photocapture"></a>Allgemeine Einrichtung für photocapture

Beginnen Sie für alle drei Verwendungszwecke mit denselben ersten drei Schritten.

Beginnen Sie mit dem Erstellen eines *photocapture* -Objekts.

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

Speichern Sie anschließend das Objekt, legen Sie die Parameter fest, und starten Sie den Photo-Modus.

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

Am Ende verwenden Sie auch denselben Bereinigungs Code, der hier vorgestellt wird.

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

Nachdem Sie diese Schritte ausgeführt haben, können Sie den Typ des zu erfassenden Fotos auswählen.

### <a name="capture-a-photo-to-a-file"></a>Fotos in einer Datei erfassen

Der einfachste Vorgang besteht darin, ein Foto direkt in einer Datei zu erfassen. Das Foto kann als jpg oder PNG gespeichert werden.

Wenn Sie den Foto Modus erfolgreich gestartet haben, erstellen Sie ein Foto, und speichern Sie es auf dem Datenträger

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

Beenden Sie nach dem Erfassen des Fotos auf dem Datenträger den Photo-Modus, und bereinigen Sie die Objekte.

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

### <a name="capture-a-photo-to-a-texture2d"></a>Fotos für ein Texture2D erfassen

Beim Erfassen von Daten in einem Texture2D ähnelt der Prozess der Erfassung auf dem Datenträger.

Befolgen Sie den obigen Setup Vorgang.

Erfassen Sie in *onphotomodestarted* einen Frame im Speicher.

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

Anschließend wenden Sie das Ergebnis auf eine Textur an und verwenden den oben aufgeführten allgemeinen Bereinigungs Code.

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Fotos erfassen und mit den Rohdaten Bytes interagieren

Wenn Sie mit den unformatierten Bytes eines in-Memory-Frames interagieren möchten, führen Sie die gleichen Einrichtungsschritte wie oben und *onphotomodestarted* aus, wie bei der Erfassung eines Fotos für eine Texture2D. Der Unterschied liegt in *oncapturedphototomemory* , wo Sie die Rohdaten Bytes erhalten und mit ihnen interagieren können.

In diesem Beispiel erstellen Sie eine *Liste <Color>* , die weiterverarbeitet oder über *setPixels ()* auf eine Textur angewendet werden soll.

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

## <a name="video-capture"></a>Video Erfassung

**Namespace:** *unityengine. XR. WSA. Webcam*<br>
**Typ:** *Videocapture*

*Videocapture* funktioniert ähnlich wie bei *photocapture*. Die einzigen beiden Unterschiede sind, dass Sie einen Wert für Frames pro Sekunde (fps) angeben müssen, und Sie können nur direkt auf dem Datenträger als MP4-Datei speichern. Die Schritte für die Verwendung von *Videocapture* lauten wie folgt:
1. Erstellen eines *Videocapture* -Objekts
2. Erstellen Sie ein " *cameraparameters* "-Objekt mit den gewünschten Einstellungen.
3. Starten des Video Modus über *startvideomodeasync*
4. Aufzeichnen des Videos starten
5. Aufzeichnen von Videos anhalten
6. Video Modus abbrechen und Ressourcen bereinigen

Erstellen Sie zunächst das *Videocapture* -Objekt *Videocapture m_VideoCapture = NULL;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

Richten Sie als nächstes die Parameter ein, die Sie für die Aufzeichnung benötigen, und starten Sie Sie.

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

Starten der Aufzeichnung

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

Nachdem die Aufzeichnung gestartet wurde, können Sie die Benutzeroberfläche oder das Verhalten aktualisieren, um das Beenden zu aktivieren. Hier melden Sie sich einfach an.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

Zu einem späteren Zeitpunkt möchten Sie die Aufzeichnung beispielsweise mithilfe eines Timers oder einer Benutzereingabe anhalten.

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

Wenn die Aufzeichnung beendet wurde, beenden Sie den Videomodus, und bereinigen Sie Ihre Ressourcen.

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

## <a name="troubleshooting"></a>Problembehandlung
* Es sind keine Auflösungen verfügbar.
    * Stellen Sie sicher, dass die **Webcam** -Funktion in Ihrem Projekt angegeben wird.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs-Prüfpunkt-Journey folgen, die wir festgelegt haben, sind Sie mitten in der Untersuchung der Funktionen und APIs der Mixed Reality-Plattform. Von hier aus können Sie mit dem nächsten Thema fortfahren:

> [!div class="nextstepaction"]
> [Fokuspunkt](focus-point-in-unity.md)

Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:

> [!div class="nextstepaction"]
> [Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets](../platform-capabilities-and-apis/using-visual-studio.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-advanced-features) zurückkehren.

## <a name="see-also"></a>Weitere Informationen
* [Ausrichtbare Kamera](../platform-capab ilities-and-apis/locatable-camera.md)
