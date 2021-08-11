---
title: Ausrichtbare Kamera
description: Allgemeine Informationen über die HoloLens kamera, wie sie funktioniert, und die Profile und Auflösungen, die Entwicklern zur Verfügung stehen.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: Kamera, Hololens, Farbkamera, Vorderseite, HoloLens 2, CV, Computer vision, fiducial, markers, qr code, qr, photo, video
ms.openlocfilehash: 33faa4107c6b44041958f422329d8967958a666606a474949184628abcd12544
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217096"
---
# <a name="locatable-camera"></a>Ausrichtbare Kamera

HoloLens enthält eine auf der Vorderseite des Geräts installierte Kamera, mit der Apps sehen können, was dem Benutzer angezeigt wird. Entwickler haben zugriff auf die Kamera und steuern sie genauso wie Farbkameras auf Smartphones, Portablen oder Desktops. Die gleichen universellen Windows [Media Capture-](/uwp/api/Windows.Media.Capture.MediaCapture) und Windows Media Foundation-APIs, die auf mobilgeräten und Desktops funktionieren, funktionieren auf HoloLens. Unity [hat diese Windows-APIs umschlossen,](../unity/locatable-camera-in-unity.md) um Die Verwendungsfunktionen der Kamera auf dem HoloLens. Zu den Funktionsaufgaben gehören das Aufnehmen regelmäßiger Fotos und Videos (mit oder ohne Hologramme) und das Auffinden der Kameraposition in und perspektive auf der Szene.

## <a name="device-camera-information"></a>Gerätekamerainformationen

### <a name="hololens-first-generation"></a>HoloLens (erste Generation)

* Kamera mit foto-/video-Fokus (PV) mit automatischem Weißabgleich, automatischer Belichtung und vollständiger Bildverarbeitungspipeline korrigiert.
* Die weiße Datenschutz-LED mit Blick auf die Welt wird immer dann leuchtet, wenn die Kamera aktiv ist.
* Die Kamera unterstützt die folgenden Modi (alle Modi haben ein Seitenverhältnis von 16:9) bei 30, 24, 20, 15 und 5 Fps:

  |  Video  |  Vorschau  |  Noch  |  Horizontales Sichtfeld (H-FOV) |  Empfohlene Verwendung | 
  |----------|----------|----------|----------|----------|
  |  1280 x 720 |  1280 x 720 |  1280 x 720 |  45 Deg  |  (Standardmodus mit Videostabilisierung) | 
  |  – |  – |  2048x1152 |  67 deg |  Bild mit der höchsten Auflösung | 
  |  1408 x 792 |  1408 x 792 |  1408 x 792 |  48 Deg |  Auflösung des Überscans (Auf padding) vor der Videostabilisierung | 
  |  1344x756 |  1344x756 |  1344x756 |  67 deg |  Großer FOV-Videomodus mit Überscan | 
  |  896x504 |  896x504 |  896x504 |  48 Deg |  Modus mit geringer Leistung/niedriger Auflösung für Bildverarbeitungsaufgaben | 

### <a name="hololens-2"></a>HoloLens 2

* Foto-/Videokamera mit automatischem Weißabgleich, automatischer Belichtung und vollständiger Bildverarbeitungspipeline.
* Die weiße Datenschutz-LED mit Blick auf die Welt wird immer dann leuchtet, wenn die Kamera aktiv ist.
* HoloLens 2 unterstützt verschiedene Kameraprofile. Erfahren Sie, wie [Sie Kamerafunktionen entdecken und auswählen.](/windows/uwp/audio-video-camera/camera-profiles)
* Die Kamera unterstützt die folgenden Profile und Auflösungen (alle Videomodi haben ein Seitenverhältnis von 16:9):
  
  | Profil                                         | Video     | Vorschau   | Noch     | Frameraten | Horizontales Sichtfeld (H-FOV) | Empfohlene Verwendung                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy,0 BalancedVideoAndPhoto,100             | 2272x1278 | 2272x1278 |           | 15.30       | 64.69                            | Qualitativ hochwertige Videoaufzeichnung                |
  | Legacy,0 BalancedVideoAndPhoto,100             | 896x504   | 896x504   |           | 15.30       | 64.69                            | Vorschaustream für hochwertige Fotoaufnahme |
  | Legacy,0 BalancedVideoAndPhoto,100             |           |           | 3904x2196 |             | 64.69                            | Qualitativ hochwertige Fotoaufnahme                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15.30       | 64.69                            | Szenarien mit langer Dauer                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15.30       | 64.69                            | Szenarien mit langer Dauer                     |
  | VideoConferencing,100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | Videokonferenzen, Szenarien mit langer Dauer |
  | Videoconferencing,100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | Videokonferenzen, Szenarien mit langer Dauer |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | Videokonferenzen, Szenarien mit langer Dauer |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | Videokonferenzen, Szenarien mit langer Dauer |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1128 x 636  |           |           | 15,30       | 64.69                            | Videokonferenzen, Szenarien mit langer Dauer |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 960 × 540   |           |           | 15,30       | 64.69                            | Videokonferenzen, Szenarien mit langer Dauer |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 760 x 428   |           |           | 15,30       | 64.69                            | Videokonferenzen, Szenarien mit langer Dauer |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 640 x 360   |           |           | 15,30       | 64.69                            | Videokonferenzen, Szenarien mit langer Dauer |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 500x282   |           |           | 15,30       | 64.69                            | Videokonferenzen, Szenarien mit langer Dauer |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 424 x 240   |           |           | 15,30       | 64.69                            | Videokonferenzen, Szenarien mit langer Dauer |

> [!NOTE]
> Kunden können [Mixed Reality-Aufzeichnungen](/hololens/holographic-photos-and-videos) nutzen, um Videos oder Fotos Ihrer App zu erstellen, einschließlich Hologramme und Videoinstabilisierung.
>
>Als Entwickler sollten Sie beim Erstellen Ihrer App Berücksichtigen, wenn Sie möchten, dass sie so gut wie möglich aussieht, wenn ein Kunde Inhalte erfasst. Sie können die Mixed Reality-Erfassung auch direkt in Ihrer App aktivieren (und anpassen). Weitere Informationen finden Sie unter [Mixed Reality-Erfassung für Entwickler.](mixed-reality-capture-for-developers.md)

## <a name="locating-the-device-camera-in-the-world"></a>Suchen der Gerätekamera in der Welt

Wenn HoloLens Fotos und Videos aufnehmen, enthalten die erfassten Frames die Position der Kamera auf der Welt und das Kameramodell. Dies ermöglicht Anwendungen, die Position der Kamera in der realen Welt für erweiterte Bilderstellungsszenarien zu ergründen. Entwickler können ihre eigenen Szenarien mit ihren bevorzugten Bildverarbeitungsbibliotheken oder benutzerdefinierten Bibliotheken für das Bildverarbeitungs-Design erstellen.

"Kamera" an anderer Stelle in HoloLens Dokumentation kann sich auf die "virtuelle Spielkamera" (das Frustum, in dem die App gerendert wird) beziehen. Sofern nicht anders angegeben, bezieht sich "camera" auf dieser Seite auf die rgb-Farbkamera der realen Welt.

### <a name="using-unity"></a>Verwendung von Unity

Um von "CameraIntrinsics" und "CameraCoordinateSystem" zu Ihrem Anwendungs-/Weltkoordinatensystem zu wechseln, befolgen Sie die Anweisungen im Artikel [Locatable camera in Unity (Locatable-Kamera in Unity).](../unity/locatable-camera-in-unity.md)  CameraToWorldMatrix wird automatisch von der PhotoCaptureFrame-Klasse bereitgestellt, sodass Sie sich keine Gedanken über die im Folgenden beschriebenen CameraCoordinateSystem-Transformationen machen müssen.

### <a name="using-mediaframereference"></a>Verwenden von MediaFrameReference

Diese Anweisungen gelten, wenn Sie die [MediaFrameReference-Klasse](/uwp/api/windows.media.capture.frames.mediaframereference) verwenden, um Bildrahmen von der Kamera zu lesen.

Jeder Bildrahmen (unabhängig davon, ob Foto oder Video) enthält ein [SpatialCoordinateSystem,](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) das zum Zeitpunkt der Erfassung an der Kamera gerootet ist. Auf dieses kann mithilfe der [CoordinateSystem-Eigenschaft](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) Ihres [MediaFrameReference](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)zugegriffen werden. Jeder Frame enthält eine Beschreibung des Kameraobjektivmodells, die in der [CameraIntrinsics-Eigenschaft](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) zu finden ist. Zusammen definieren diese Transformationen für jedes Pixel einen Strahl im 3D-Raum, der den Pfad darstellt, der von den Photonen genommen wird, die das Pixel erzeugt haben. Diese Lichtstrahle können mit anderen Inhalten in der App verknüpft werden, indem die Transformation vom Koordinatensystem des Frames in ein anderes Koordinatensystem (z. B. von einem [stationären Bezugsrahmen)](../../design/coordinate-systems.md#stationary-frame-of-reference)erhalten wird. 

Jeder Bildrahmen bietet Folgendes:
* Pixeldaten (im RGB/NV12/JPEG/etc.-Format)
* [Ein SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) vom Speicherort der Erfassung
* Eine [CameraIntrinsics-Klasse,](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) die den Fokusmodus der Kamera enthält

Das [HolographicFaceTracking-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) zeigt die recht einfache Möglichkeit, die Transformation zwischen dem Koordinatensystem der Kamera und Ihren eigenen Anwendungskoordinatensystemen abzufragen.

### <a name="using-media-foundation"></a>Verwenden von Media Foundation

Wenn Sie Media Foundation direkt verwenden, um Bilderrahmen von der Kamera zu lesen, können Sie das [MFSampleExtension_CameraExtrinsics-Attribut](/windows/win32/medfound/mfsampleextension-cameraextrinsics) jedes Frames und [MFSampleExtension_PinholeCameraIntrinsics Attribut](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) verwenden, um Kamerarahmen relativ zu den anderen Koordinatensystemen Ihrer Anwendung zu suchen, wie in diesem Beispielcode gezeigt:

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>Verzerrungsfehler

Auf HoloLens werden die Video- und Standbildstreams in der Bildverarbeitungspipeline des Systems rückgängig gemacht, bevor die Frames der Anwendung zur Verfügung gestellt werden (der Vorschaudatenstrom enthält die ursprünglichen verzerrten Frames). Da nur die CameraIntrinsics verfügbar gemacht werden, müssen Anwendungen davon ausgehen, dass Bildrahmen eine perfekte Stecknadelkamera darstellen.

Bei HoloLens (erste Generation) kann die Funktion zum Rückgängig machen im Bildprozessor weiterhin einen Fehler von bis zu 10 Pixeln hinterlassen, wenn cameraIntrinsics in den Framemetadaten verwendet wird. In vielen Anwendungsfällen spielt dieser Fehler keine Rolle, aber wenn Sie Hologramme beispielsweise an realen Postern/Markern ausrichten und einen <10-px-Offset bemerken (etwa 11 mm für Hologramme, die 2 Meter entfernt positioniert sind), kann dieser Verzerrungsfehler die Ursache sein. 

## <a name="locatable-camera-usage-scenarios"></a>Szenarien für die Verwendung von Locatable-Kameras

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Ein Foto oder Video in der Welt anzeigen, in der es erfasst wurde

Die Gerätekamerarahmen enthalten eine "Camera To World"-Transformation, die verwendet werden kann, um genau anzuzeigen, wo sich das Gerät befand, als das Bild aufgenommen wurde. Sie können z. B. ein kleines holografisches Symbol an dieser Position positionieren (CameraToWorld.MultiplyPoint(Vector3.zero)) und sogar einen kleinen Pfeil in der Richtung zeichnen, in der sich die Kamera befand (CameraToWorld.MultiplyVector(Vector3.forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Tag/Muster/Poster/Objektnachverfolgung

Viele Mixed Reality-Anwendungen verwenden ein erkennbares Bild- oder visuelles Muster, um einen nachverfolgbaren Punkt im Raum zu erstellen. Dies wird dann verwendet, um Objekte relativ zu diesem Punkt zu rendern oder eine bekannte Position zu erstellen. Einige Verwendungsmöglichkeiten für HoloLens umfassen die Suche nach einem realen Objekt, das mit Fiduzialisierungen markiert ist (z. B. einen TV-Monitor mit einem QR-Code), das Platzieren von Hologrammen über Fiduziale und die visuelle Kopplung mit Nicht-HoloLens Geräten wie Tablets, die für die Kommunikation mit HoloLens über WLAN eingerichtet wurden.

Sie benötigen einige Dinge, um ein visuelles Muster zu erkennen und ein Objekt im Bereich der Anwendungswelt zu platzieren:
1. Ein Bildmustererkennungstoolkit, z. B. QR-Code, AR-Tags, Gesichtssuche, Kreisverfolgungen, OCR usw.
2. Erfassen von Bildframes zur Laufzeit und Übergeben an die Erkennungsebene
3. Entprojektieren Sie ihre Bildstandorte wieder an Weltpositionen oder wahrscheinlich an Lichtstrahl. 
4. Positionieren Ihrer virtuellen Modelle an diesen Standorten weltweit

Einige wichtige Links zur Bildverarbeitung:
* [OpenCV](https://opencv.org/)
* [QR-Tags](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Die Beibehaltung einer interaktiven Bildfrequenz einer Anwendung ist wichtig, insbesondere beim Umgang mit Algorithmen für die Bilderkennung mit langer Ausführungslaufzeit. Aus diesem Grund verwenden wir häufig das folgende Muster:
1. Hauptthread: verwaltet das Kameraobjekt
2. Hauptthread: Fordert neue Frames an (asynchron)
3. Hauptthread: Übergeben neuer Frames an den Nachverfolgungsthread
4. Nachverfolgungsthread: Verarbeitet das Image zum Sammeln von Schlüsselpunkten.
5. Hauptthread: Verschiebt das virtuelle Modell, um gefundene Schlüsselpunkte abzugleichen
6. Hauptthread: Wiederholung aus Schritt 2

Einige Bildmarkierungssysteme bieten nur eine einzelne Pixelposition (andere bieten die vollständige Transformation, in diesem Fall ist dieser Abschnitt nicht erforderlich), was einem Strahl möglicher Positionen entspricht. Um zu einem einzelnen 3D-Standort zu kommen, können wir dann mehrere Lichtstrahle nutzen und das Endergebnis nach ihrer ungefähren Schnittmenge finden. Gehen Sie hierzu wie folgt vor:
1. Erhalten einer Schleife, die mehrere Kamerabilder sammelt
2. Suchen der zugehörigen Merkmalspunkte und deren Lichtstrahl
3. Wenn Sie über ein Wörterbuch mit Merkmalen verfügen, die jeweils mehrere Weltlichtlichter haben, können Sie den folgenden Code verwenden, um die Schnittmenge dieser Lichtstrahle zu beheben:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

Bei zwei oder mehr nachverfolgten Tagpositionen können Sie eine modellierte Szene so positionieren, dass sie dem aktuellen Szenario des Benutzers passt. Wenn Sie schwerkraft nicht annehmen können, benötigen Sie drei Tagpositionen. In vielen Fällen verwenden wir ein Farbschema, bei dem weiße Kugeln In Echtzeit nachverfolgte Tagpositionen darstellen und blaue Kugeln modellierte Tagpositionen darstellen. Dadurch kann der Benutzer die Ausrichtungsqualität visuell messen. Wir gehen von der folgenden Einrichtung in allen Unseren Anwendungen aus:
* Zwei oder mehr modellierte Tagpositionen
* Ein "Kalibrierungsraum", der in der Szene das übergeordnete Element der Tags ist
* Kamerafeaturebezeichner
* Verhalten, das den Kalibrierungsraum verschiebt, um die modellierten Tags an den Echtzeittags auszurichten (wir achten darauf, den übergeordneten Bereich und nicht die modellierten Marker selbst zu verschieben, da andere Verbindungen relativ zu ihnen sind).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Nachverfolgen oder Identifizieren von markierten ortsfesten oder bewegten Objekten/Gesichtern aus der realen Welt mithilfe von LEDs oder anderen Erkennungsbibliotheken

Beispiele:
* Industrieanlagen mit LEDs (oder QR-Codes für langsamer bewegte Objekte)
* Identifizieren und Erkennen von Objekten im Raum
* Identifizieren und Erkennen von Personen im Raum, z. B. Platzieren von holografischen Visitenkarten über Gesichtern

## <a name="see-also"></a>Siehe auch
* [Beispiel für eine verkettete Kamera](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Ausrichtbare Kamera in Unity](../unity/locatable-camera-in-unity.md)
* [Mixed-Reality-Aufnahme](/hololens/holographic-photos-and-videos)
* [Mixed Reality-Aufnahme für Entwickler](mixed-reality-capture-for-developers.md)
* [Einführung in Die Medienerfassung](/windows/uwp/audio-video-camera/)
* [Holographic face tracking sample (Holographic Face Tracking-Beispiel)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)