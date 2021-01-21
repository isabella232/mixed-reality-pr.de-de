---
title: Nachverfolgen von QR-Codes
description: Erfahren Sie, wie Sie QR-Codes erkennen, Webcam-Funktionen hinzufügen und Koordinatensysteme in Mixed Reality-Apps auf HoloLens 2 verwalten.
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: VR, LBE, standortbezogene Unterhaltung, VR-Arcade, Arcade, immersiv, QR, QR-Code, hololens2
ms.openlocfilehash: 0f53b8def268b2d501c6efe3c3e40ea18f9323e0
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635432"
---
# <a name="qr-code-tracking"></a>Nachverfolgen von QR-Codes

HoloLens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der Position jedes Codes in der realen Welt einrichten. Nachdem Sie die Webcam Ihres Geräts aktiviert haben, können Sie QR-Codes in den neuesten Versionen ihrer Unreal-oder Unity-Projekte erkennen. Bevor Sie in die Produktion gehen, empfiehlt es sich, die [bewährten Methoden](#best-practices-for-qr-code-detection) zu befolgen, die wir am Ende des Artikels festgelegt haben.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Funktion</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> QR-Code-Erkennung</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>Die QR-Code Nachverfolgung mit immersiven Windows Mixed Reality-Headsets auf Desktop-PCs wird unter Windows 10, Version 2004 und höher, unterstützt. Verwenden Sie die Microsoft.MixedReality.QRCodeWatcher.IsSupported()-API, um zu bestimmen, ob die Funktion auf dem aktuellen Gerät unterstützt wird.

## <a name="getting-the-qr-package"></a>Abrufen des QR-Pakets

Sie können das NuGet-Paket für die QR-Code-Erkennung [hier](https://nuget.org/Packages/Microsoft.MixedReality.QR) herunterladen.

## <a name="detecting-qr-codes"></a>Erkennen von QR-Codes

### <a name="adding-the-webcam-capability"></a>Hinzufügen der Webcamfunktion

Sie müssen Ihrem Manifest die Funktion `webcam` hinzufügen, um QR-Codes erkennen zu können. Diese Funktion ist erforderlich, da die Daten innerhalb der erkannten Codes in der Umgebung des Benutzers möglicherweise vertrauliche Informationen enthalten.

Die Berechtigung kann durch den Aufruf von `QRCodeWatcher.RequestAccessAsync()` angefordert werden:

_C#:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

Vor dem Erstellen eines QRCodeWatcher-Objekts muss die Berechtigung angefordert werden.

Zwar ist die Funktion `webcam` für die QR-Code-Erkennung erforderlich, die Erkennung erfolgt jedoch mithilfe der Überwachungskameras des Geräts. Dies bietet ein breiteres Sichtfeld für die Erkennung und längere Batterielaufzeiten im Vergleich mit der Erkennung über die Foto/Videokamera (FV) des Geräts.

### <a name="detecting-qr-codes-in-unity"></a>Erkennen von QR-Codes in Unity

Sie können die API zur QR-Code-Erkennung in Unity ohne den Import des MRTK nutzen, wenn Sie das NuGet-Paket mithilfe von [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) installieren. Wenn Sie ein Gefühl für die Funktion erwerben möchten, laden Sie die [Unity-Beispiel-App](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) herunter. Die Beispiel-App enthält Beispiele zum Anzeigen eines holografischen Quadrats über QR-Codes und zugeordneten Daten wie GUID, physischer Größe, Zeitstempel und decodierten Daten.

### <a name="detecting-qr-codes-in-c"></a>Erkennen von QR-Codes in C++

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Abrufen des Koordinatensystems für einen QR-Code

Jeder erkannte QR-Code macht ein [räumliches Koordinatensystem verfügbar](../../design/coordinate-systems.md), das am QR-Code in der linken oberen Ecke des Schnellerkennungsquadrats oben links ausgerichtet ist:  

![QR-Code-Koordinatensystem](images/Qr-coordinatesystem.png) 

Wenn Sie das QR-SDK direkt verwenden, zeigt die Z-Achse zum Papier (nicht dargestellt) – bei der Konvertierung in Unity-Koordinaten zeigt die Z-Achse aus dem Papier heraus und ist linkshändig.

Das SpatialCoordinateSystem eines QR-Codes wird wie dargestellt ausgerichtet. Sie können das Koordinatensystem von der Plattform abrufen, indem Sie <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> aufrufen und die SpatialGraphNodeId des Codes übergeben.

Der unten abgebildete C++-Code zeigt, wie ein Rechteck erstellt und mithilfe des Koordinatensystems des QR-Codes platziert wird:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

Sie können die physische Größe verwenden, um das QR-Rechteck zu erstellen:

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

Das Koordinatensystem kann verwendet werden, um den QR-Code zu zeichnen oder Hologramme an die Position anzufügen:

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

Insgesamt kann Ihr *QRCodeAddedHandler* etwa so aussehen:

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a>Bewährte Methoden für die Erkennung von QR-Codes

### <a name="quiet-zones-around-qr-codes"></a>Stille Zonen um QR-Codes herum

Um ordnungsgemäß gelesen zu werden, erfordern QR-Codes einen Rand, der alle Seiten des Codes umgibt. Dieser Rand darf keine gedruckten Inhalte enthalten und sollte vier Module (ein einzelnes schwarzes Quadrat im Code) breit sein. 

Die [QR-Spezifikation](https://www.qrcode.com/en/howto/code.html) enthält weitere Informationen zu stillen Zonen.

### <a name="lighting-and-backdrop"></a>Beleuchtung und Hintergrund
Die Erkennungsqualität von QR-Code reagiert auf wechselnde Beleuchtungs- und Hintergrundverhältnisse. 

Drucken Sie in einer hell beleuchteten Szene einen schwarzen Code auf einem grauen Hintergrund. Drucken Sie andernfalls einen schwarzen QR-Code auf einem weißen Hintergrund.

Wenn der Hintergrund des Codes dunkel ist, probieren Sie einen schwarzen Code auf Grau,wenn Ihre Erkennungsrate niedrig ist. Wenn der Hintergrund relativ hell ist, sollte ein gewöhnlicher Code gut funktionieren.

### <a name="size-of-qr-codes"></a>Größe von QR-Codes
Windows Mixed Reality-Geräte funktionieren nicht mit QR-Codes, deren Seiten kleiner als jeweils 5 cm sind.

Bei QR-Code mit einer Kantenlänge zwischen 5 und 10 cm müssen Sie recht nah herangehen, um den Code zu erkennen. Die Erkennung von Codes in dieser Größe dauert außerdem länger. 

Die genaue Zeit, die zum Erkennen von Codes benötigt wird, hängt nicht nur von der Größe der QR-Codes ab, sondern auch von der Entfernung des Codes. Näher an den Code heranzugehen, hilft dabei, Größenprobleme zu beheben.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Abstand und Winkelposition gegenüber dem QR-Code
Die Überwachungskameras besitzen eine eingeschränkte Detailauflösung. Bei kleinen Codes – < 10 cm Kantenlänge – müssen Sie recht nah an den Code herangehen. Für einen QR-Code der Version 1 mit einer Breite zwischen 10 und 25 cm liegt der Mindestabstand für die Erkennung zwischen 0,15 und 0,5 m. 

Der Erkennungsabstand steigt mit der Größe linear an. 

Die QR-Erkennung funktioniert in einem Winkelbereich von += 45°, um sicherzustellen, dass die Auflösung zum Erkennen des Codes ausreicht.

### <a name="qr-codes-with-logos"></a>QR-Codes mit Logos
QR-Codes mit Logos wurden nicht getestet und werden zurzeit nicht unterstützt.

### <a name="managing-qr-code-data"></a>Verwalten von QR-Codedaten
Windows Mixed Reality-Geräte erkennen QR-Codes auf der Systemebene im Treiber. Wenn das Gerät neu gestartet wird, sind die erkannten QR-Codes verschwunden und werden beim nächsten Mal wieder als neue Objekte erkannt.

Wir empfehlen, Ihre App so zu konfigurieren, dass QR-Codes, die älter als ein bestimmter Zeitstempel sind, ignoriert werden. Aktuell unterstützt die API das Bereinigen des QR-Codeverlaufs nicht.

### <a name="qr-code-placement-in-a-space"></a>Platzierung von QR-Codes im Raum
Empfehlungen zur Platzierung von QR-Codes finden Sie unter [Umgebungsüberlegungen für HoloLens](/hololens/hololens-environment-considerations).

## <a name="qr-api-reference"></a>QR-API-Referenz

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>Weitere Informationen
* [Koordinatensysteme](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>