---
title: Foto-/Videokamera in Unity
description: Erfahren Sie, wie Sie ein Foto in einer Datei oder in einer Texture2D erfassen, wie Sie ein Foto erfassen und mit den unformatierten Bytes interagieren und wie Sie ein Video aufnehmen.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: Foto, Video, Hololens, Kamera, Unity, Locatable, PVC, Fotovideokamera, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Webcam, Fotoaufnahme, Videoaufnahme
ms.openlocfilehash: 4fdf895e6b2b7ed1fc051b45b07ce49052f8a95587178caddfc71a0cfd364eee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193504"
---
# <a name="photo-video-camera-in-unity"></a>Foto-/Videokamera in Unity

## <a name="enabling-the-capability-for-camera-access"></a>Aktivieren der Funktion für den Kamerazugriff

Die Funktion "WebCam" muss deklariert werden, damit eine App die [Kamera](../platform-capabilities-and-apis/locatable-camera.md)verwenden kann.

1. Navigieren Sie im Unity-Editor zu den Playereinstellungen, indem Sie zur Seite "> Project Einstellungen > Player bearbeiten" navigieren.
2. Wählen Sie die Registerkarte "Windows Store" aus.
3. Überprüfen Sie im Abschnitt "Veröffentlichung Einstellungen > Funktionen" die Funktionen **WebCam** und **Mikrofon.**

Es kann nur ein einzelner Vorgang gleichzeitig mit der Kamera ausgeführt werden. Sie können überprüfen, in welchem Modus sich die Kamera derzeit `UnityEngine.XR.WSA.WebCam.Mode` in Unity 2018 und früher oder `UnityEngine.Windows.WebCam.Mode` in Unity 2019 und höher befindet. Verfügbare Modi sind Foto, Video oder keine.

## <a name="photo-capture"></a>Fotoaufnahme

**Namespace (vor Unity 2019):** *UnityEngine.XR.WSA.WebCam*<br>
**Namespace (Unity 2019 und höher):** *UnityEngine.Windows. WebCam*<br>
**Typ:** *PhotoCapture*

Mit dem *PhotoCapture-Typ* können Sie noch Fotos mit der Fotovideokamera aufnehmen. Das allgemeine Muster für die Verwendung von *PhotoCapture* zum Aufnehmen eines Fotos lautet wie folgt:

1. Erstellen eines *PhotoCapture-Objekts*
2. Erstellen eines *CameraParameters-Objekts* mit den gewünschten Einstellungen
3. Starten des Fotomodus über *StartPhotoModeAsync*
4. Aufnehmen des gewünschten Fotos
    * (optional) Interagieren mit diesem Bild
5. Beenden des Fotomodus und Bereinigen von Ressourcen

### <a name="common-set-up-for-photocapture"></a>Allgemeine Einrichtung für PhotoCapture

Beginnen Sie für alle drei Verwendungen mit den gleichen ersten drei Schritten oben.

Erstellen Sie zunächst ein *PhotoCapture-Objekt.*

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

Speichern Sie als Nächstes Ihr Objekt, legen Sie Ihre Parameter fest, und starten Sie den Fotomodus.

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

Am Ende verwenden Sie auch den gleichen Bereinigungscode, der hier dargestellt wird.

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

Nach diesen Schritten können Sie auswählen, welche Art von Foto aufgenommen werden soll.

### <a name="capture-a-photo-to-a-file"></a>Aufnehmen eines Fotos in einer Datei

Der einfachste Vorgang besteht darin, ein Foto direkt in einer Datei zu erfassen. Das Foto kann als JPG oder PNG gespeichert werden.

Wenn Sie den Fotomodus erfolgreich gestartet haben, nehmen Sie ein Foto auf, und speichern Sie es auf dem Datenträger.

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

Nachdem Sie das Foto auf dem Datenträger erfasst haben, beenden Sie den Fotomodus, und bereinigen Sie ihre Objekte.

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

### <a name="capture-a-photo-to-a-texture2d-with-location"></a>Aufnahme eines Fotos in einer Texture2D mit Position

Beim Erfassen von Daten in einer Texture2D ähnelt der Vorgang der Erfassung auf dem Datenträger.

Führen Sie den oben beschriebenen Setupprozess aus.

Erfassen Sie in *OnPhotoModeStarted* einen Frame im Arbeitsspeicher.

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

Anschließend wenden Sie Ihr Ergebnis auf eine Textur an und verwenden den oben aufgeführten allgemeinen Bereinigungscode.

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

#### <a name="locatable-camera"></a>Ausrichtbare Kamera

Um diese Textur in der Szene zu platzieren und mithilfe der locatable-Kameramatrizen anzuzeigen, fügen Sie *onCapturedPhotoToMemory* in der Überprüfung den folgenden Code `result.success` hinzu:

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

[Unity hat Beispielcode](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) zum Anwenden der Projektionsmatrix auf einen bestimmten Shader in ihren Foren bereitgestellt.

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Aufnehmen eines Fotos und Interagieren mit den unformatierten Bytes

Um mit den unformatierten Bytes eines im Speicherrahmen zu interagieren, führen Sie die gleichen Einrichtungsschritte wie oben und *OnPhotoModeStarted* wie beim Erfassen eines Fotos in einer Texture2D aus. Der Unterschied besteht in *OnCapturedPhotoToMemory,* wo Sie die unformatierten Bytes abrufen und mit ihnen interagieren können.

In diesem Beispiel erstellen Sie über *SetPixels()* eine *Liste, <Color>* die weiter verarbeitet oder auf eine Textur angewendet werden soll.

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

## <a name="video-capture"></a>Videoaufnahme

**Namespace (vor Unity 2019):** *UnityEngine.XR.WSA.WebCam*<br>
**Namespace (Unity 2019 und höher):** *UnityEngine.Windows. WebCam*<br>
**Typ:** *VideoCapture*

*VideoCapture-Funktionen* ähnlich wie *PhotoCapture*. Die einzigen beiden Unterschiede bestehen darin, dass Sie einen FPS-Wert (Frames Per Second) angeben müssen und sie nur direkt als .mp4 Datei auf dem Datenträger speichern können. Die Schritte zur Verwendung von *VideoCapture* lauten wie folgt:

1. Erstellen eines *VideoCapture-Objekts*
2. Erstellen eines *CameraParameters-Objekts* mit den gewünschten Einstellungen
3. Starten des Videomodus über *StartVideoModeAsync*
4. Videoaufzeichnung starten
5. Aufzeichnung des Videos beenden
6. Beenden des Videomodus und Bereinigen von Ressourcen

Erstellen Sie zunächst unser *VideoCapture-Objekt* *VideoCapture m_VideoCapture = NULL;*

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

Richten Sie als Nächstes die Gewünschten Parameter für die Aufzeichnung ein, und starten Sie sie.

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

Starten Sie nach dem Starten die Aufzeichnung.

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

Nachdem die Aufzeichnung gestartet wurde, können Sie Die Benutzeroberfläche oder das Verhalten aktualisieren, um das Beenden zu aktivieren. Hier melden Sie sich einfach an.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

Zu einem späteren Zeitpunkt möchten Sie die Aufzeichnung beispielsweise mithilfe eines Timers oder einer Benutzereingabe beenden.

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

Nachdem die Aufzeichnung beendet wurde, beenden Sie den Videomodus, und bereinigen Sie Ihre Ressourcen.

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

* Es sind keine Lösungen verfügbar.
  * Stellen Sie sicher, dass die **WebCam-Funktion** in Ihrem Projekt angegeben ist.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsprüfpunkt-Journey verfolgen, können Sie sich mit den Mixed Reality Plattformfunktionen und APIs beschäftigen. Von hier aus können Sie mit dem nächsten Thema fortfahren:

> [!div class="nextstepaction"]
> [Fokuspunkt](focus-point-in-unity.md)

Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:

> [!div class="nextstepaction"]
> [Bereitstellen auf HoloLens oder Windows Mixed Reality immersiven Headsets](../platform-capabilities-and-apis/using-visual-studio.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-advanced-features) zurückkehren.

## <a name="see-also"></a>Weitere Informationen

* [Ausrichtbare Kamera](../platform-capabilities-and-apis/locatable-camera.md)