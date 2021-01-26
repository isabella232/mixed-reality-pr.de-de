---
title: Ausrichtbare Kamera
description: Allgemeine Informationen zu der hololens-Front-Kamera, ihrer Funktionsweise und den Profilen und Auflösungen, die Entwicklern zur Verfügung stehen.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: Kamera, hololens, Farbkamera, Vorderseite, hololens 2, CV, Maschinelles sehen, Zeichen, Marker, QR-Code, QR, Foto, Video
ms.openlocfilehash: f34973fee56f9469632b320a62dd441ed32e5805
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810154"
---
# <a name="locatable-camera"></a>Ausrichtbare Kamera

Hololens enthält eine weltweit eingebundene Kamera, die auf der Vorderseite des Geräts bereitgestellt wird. Dadurch können apps erkennen, was der Benutzer sieht. Entwickler haben Zugriff auf und die Steuerung der Kamera, ebenso wie bei Farbkameras auf Smartphones, portables oder Desktops. Die gleichen universellen Windows [Media Capture](/uwp/api/Windows.Media.Capture.MediaCapture) -und Windows Media Foundation-APIs, die auf mobilen und Desktop-apps funktionieren, funktionieren in hololens. Unity [hat diese Windows-APIs](../unity/locatable-camera-in-unity.md) in die abstrakten Features der Kamera Verwendung in hololens integriert. Zu den featureaufgaben zählen regelmäßige Fotos und Videos (mit oder ohne Hologramme) und das Auffinden der Position der Kamera in der Szene.

## <a name="device-camera-information"></a>Gerätekamera Informationen

### <a name="hololens-first-generation"></a>Hololens (erste Generation)

* Mit dem automatischen weißen Saldo, dem automatischen verfügbar machen und der vollständigen Bild Verarbeitungs Pipeline wurde eine Foto-und vollständige Bild Verarbeitungs Pipeline korrigiert.
* Die Welt der weißen Datenschutz wird immer dann beleuchtet, wenn die Kamera aktiv ist.
* Die Kamera unterstützt die folgenden Modi (alle Modi sind 16:9-Seitenverhältnis) bei 30, 24, 20, 15 und 5 fps:

  |  Video  |  Vorschau  |  Auch  |  Horizontales Feld der Ansicht (H-FOV) |  Empfohlene Verwendung | 
  |----------|----------|----------|----------|----------|
  |  1.280 x 720 |  1.280 x 720 |  1.280 x 720 |  45 deg  |  (Standardmodus mit Videostabilisierung) | 
  |  Nicht zutreffend |  Nicht zutreffend |  2048x1152 |  67 deg |  Bild mit der höchsten Auflösung | 
  |  1408x792 |  1408x792 |  1408x792 |  48 deg |  Überprüfung (Padding) vor der Videostabilisierung | 
  |  1344x756 |  1344x756 |  1344x756 |  67 deg |  Großer FOV-Videomodus mit Overscan | 
  |  896x504 |  896x504 |  896x504 |  48 deg |  Niedriger Energie-/tieflösungmodus für Abbild Verarbeitungsaufgaben | 

### <a name="hololens-2"></a>HoloLens 2

* Auto-Fokus Foto/Video-Kamera (PV) mit automatischem weißen Ausgleich, automatischer Verfügbarkeit und vollständiger Bild Verarbeitungs Pipeline.
* Die Welt der weißen Datenschutz wird immer dann beleuchtet, wenn die Kamera aktiv ist.
* Hololens 2 unterstützt verschiedene Kameraprofile. Erfahren Sie, wie [Sie Kamerafunktionen ermitteln und auswählen](/windows/uwp/audio-video-camera/camera-profiles)können.
* Die Kamera unterstützt die folgenden Profile und Auflösungen (alle Video Modi sind 16:9-Seitenverhältnis):
  
  | Profil                                         | Video     | Vorschau   | Auch     | Frameraten | Horizontales Feld der Ansicht (H-FOV) | Empfohlene Verwendung                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy, 0 balancedvideoandphoto, 100             | 2272x1278 | 2272x1278 |           | 15,30       | 64,69                            | Hochwertige Videoaufzeichnung                |
  | Legacy, 0 balancedvideoandphoto, 100             | 896x504   | 896x504   |           | 15,30       | 64,69                            | Vorschau Datenstrom für hochwertige Foto Erfassung |
  | Legacy, 0 balancedvideoandphoto, 100             |           |           | 3904x2196 |             | 64,69                            | Foto Erfassung mit hoher Qualität                  |
  | Balancedvideoandphoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15,30       | 64,69                            | Szenarios mit langer Laufzeit                     |
  | Balancedvideoandphoto, 120                       | 1504x846  | 1504x846  |           | 15,30       | 64,69                            | Szenarios mit langer Laufzeit                     |
  | Videokonferenzen, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30, 60    | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videokonferenzen, 100                           | 1504x846  | 1504x846  |           | 5, 15, 30, 60  | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 1920x1080 | 1920x1080 | 1920x1080 | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 1.280 x 720  | 1.280 x 720  | 1.280 x 720  | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 1128x636  |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 960 × 540   |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 760x428   |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 640x360   |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 500 x 282   |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |
  | Videoconferencing, 100 balancedvideoandphoto, 120 | 424x240   |           |           | 15, 30       | 64,69                            | Video Konferenzen, Szenarios mit langer Laufzeit |

> [!NOTE]
> Kunden können die [gemischte Reality-Erfassung](/hololens/holographic-photos-and-videos) nutzen, um Videos oder Fotos Ihrer APP zu erstellen, die Hologramme und Videostabilisierung enthalten.
>
>Als Entwickler sollten Sie beim Erstellen Ihrer APP berücksichtigen, dass Sie beim Erfassen von Inhalten so gut wie möglich aussehen sollten. Sie können die gemischte Reality-Erfassung auch direkt in Ihrer APP aktivieren (und anpassen). Weitere Informationen finden Sie unter [Mixed Reality Capture für Entwickler](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Auffinden der Gerätekamera weltweit

Wenn hololens Fotos und Videos aufnimmt, beinhalten die erfassten Frames den Ort der Kamera auf der Welt und das Modell der Kamera. Dies ermöglicht es Anwendungen, die Position der Kamera in der realen Welt für erweiterte Abbild Erstellungs Szenarios zu untersuchen. Entwickler können Ihre eigenen Szenarien mithilfe Ihrer bevorzugten Bildverarbeitung oder Ihrer benutzerdefinierten Maschinelles Sehen-Bibliotheken kreativ gestalten.

"Kamera" an anderer Stelle in der hololens-Dokumentation bezieht sich auf die "virtuelle Spiel Kamera" (die Frustration, in der die APP rendert). Sofern nicht anders angegeben, bezieht sich "Kamera" auf dieser Seite auf die tatsächliche RGB-Farbkamera.

### <a name="using-unity"></a>Verwendung von Unity

Befolgen Sie die Anweisungen im Artikel "cameraintrinsics" und "cameracoordinatesystem [" in Ihr](../unity/locatable-camera-in-unity.md) Anwendungs-/World-Koordinatensystem.  Cameratoworldmatrix wird automatisch von der photocaptureframe-Klasse bereitgestellt, sodass Sie sich keine Gedanken über die unten beschriebenen cameracoordinatesystem-Transformationen machen müssen.

### <a name="using-mediaframereference"></a>Verwenden von mediaframereferenzierung

Diese Anweisungen gelten, wenn Sie mit der [mediaframereferenzierungsklasse](/uwp/api/windows.media.capture.frames.mediaframereference) Bild Frames von der Kamera lesen.

Jeder Bild Rahmen (egal ob Foto oder Video) enthält ein [spatialcoordinatesystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , das zum Zeitpunkt der Erfassung auf der Kamera verankert ist, auf die mit der [CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) -Eigenschaft von [mediaframereferenziert](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)werden kann. Jeder Frame enthält eine Beschreibung des Kamera-Lens-Modells, das in der Eigenschaft [cameraintrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) zu finden ist. In der Regel definieren diese Transformationen für jedes Pixel einen Strahl in 3D-Raum, der den Pfad darstellt, der von den Photonen, die das Pixel erzeugt haben, übernommen wird. Diese Strahlen können mit anderem Inhalt in der APP verknüpft werden, indem die Transformation aus dem Koordinatensystem des Frames in ein anderes Koordinatensystem (z. b. aus einem [stationären Verweis Rahmen](../../design/coordinate-systems.md#stationary-frame-of-reference)) bezogen wird. 

Jeder Bild Rahmen stellt Folgendes bereit:
* Pixel Daten (im Format RGB/NV12/JPEG/usw.)
* Ein [spatialcoordinatesystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) vom Speicherort der Erfassung
* Eine [cameraintrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) -Klasse, die den Linsen Modus der Kamera enthält.

Das [holographicfacetracking-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) zeigt die relativ unkomplizierte Methode zum Abfragen der Transformation zwischen dem Koordinatensystem der Kamera und ihren eigenen Anwendungs Koordinatensystemen.

### <a name="using-media-foundation"></a>Verwenden von Media Foundation

Wenn Sie Media Foundation direkt zum Lesen von Bildframes von der Kamera verwenden, können Sie das [MFSampleExtension_CameraExtrinsics-Attribut](/windows/win32/medfound/mfsampleextension-cameraextrinsics) jedes Frames und [MFSampleExtension_PinholeCameraIntrinsics-Attribut](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) verwenden, um die Kamera Rahmen in Bezug auf die anderen Koordinatensysteme Ihrer Anwendung zu lokalisieren, wie im folgenden Beispielcode gezeigt:

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

### <a name="distortion-error"></a>Verzerrungs Fehler

Bei hololens sind das Video und die bildstreams in der Bild Verarbeitungs Pipeline des Systems unverzerrt, bevor die Frames der Anwendung zur Verfügung gestellt werden (der vorschaustream enthält die ursprünglichen verzerrten Frames). Da nur die cameraintrinsics verfügbar gemacht werden, müssen Anwendungen davon ausgehen, dass Bild Rahmen eine perfekte Kamera darstellen.

Bei hololens (First-Generation) kann die unzerungs Funktion im Bildprozessor bei Verwendung von "cameraintrinsics" in den Frame-Metadaten weiterhin einen Fehler von bis zu 10 Pixeln hinterlassen. In vielen Anwendungsfällen ist dieser Fehler nicht von Bedeutung. Wenn Sie z. b. Hologramme an realen Poster/Markierungen ausrichten, sehen Sie sich beispielsweise einen <10-px-Offset an (ungefähr 11 mm für holograms, der 2 Meter entfernt ist), könnte dieser Verzerrungs Fehler die Ursache sein. 

## <a name="locatable-camera-usage-scenarios"></a>Szenarios für die verwendbare Verwendung von Kameras

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Foto oder Video in der Welt anzeigen, in der es aufgezeichnet wurde

Die Gerätekamera Rahmen verfügen über eine "Kamera-an-Welt"-Transformation, die verwendet werden kann, um genau anzuzeigen, wo das Gerät war, als das Abbild erstellt wurde. Beispielsweise können Sie an dieser Stelle ein kleines Holographic-Symbol positionieren (cameratoworld. multiplypoint (Vector3. Zero)) und sogar einen kleinen Pfeil in der Richtung zeichnen, in der die Kamera angezeigt wurde (cameratoworld. multiplyvector (Vector3. Forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Tag/Muster/Poster/Objektverfolgung

Viele Mixed Reality-Anwendungen verwenden ein erkennbares Bild oder visuelles Muster, um einen standbybaren Punkt im Raum zu schaffen. Diese wird dann zum Rendering von Objekten in Relation zu diesem Punkt oder zum Erstellen eines bekannten Speicher Orts verwendet. Einige Verwendungen von hololens beinhalten das Auffinden eines realen Objekts, das mit einem-Objekt (z. b. einem TV-Monitor mit einem QR-Code) gekennzeichnet ist, das Platzieren von holograms über das Produkt und das visuelle koppeln mit Geräten, die nicht hololens über Wi-Fi eingerichtet wurden.

Sie benötigen einige Dinge, um ein visuelles Muster zu erkennen und ein Objekt im Raum der Anwendungen zu platzieren:
1. Ein Bildmuster Erkennungs-Toolkit, z. b. QR-Code, AR-Tags, Gesichts Finder, Zirkel Tracker, OCR usw.
2. Bild Rahmen zur Laufzeit erfassen und an die Erkennungs Schicht übergeben
3. Entprojizieren Sie Ihre Image Positionen wieder in die Welt Positionen oder wahrscheinlich weltweit. 
4. Positionieren Sie Ihre virtuellen Modelle an den Standorten der Welt.

Einige wichtige Links zur Bildverarbeitung:
* [OpenCV](https://opencv.org/)
* [QR-Tags](https://en.wikipedia.org/wiki/QR_code)
* [Fakesdk](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Die Beibehaltung einer interaktiven Anwendungsframe-Rate ist wichtig, insbesondere beim Umgang mit Bild Erkennungsalgorithmen mit langer Laufzeit. Aus diesem Grund verwenden wir in der Regel das folgende Muster:
1. Haupt Thread: verwaltet das Kamera Objekt.
2. Haupt Thread: neue Frames anfordern (Async)
3. Haupt Thread: neue Frames an nach Verfolgungs Thread übergeben
4. Überwachungs Thread: verarbeitet das Image zum Erfassen von Schlüsselpunkten.
5. Haupt Thread: verschiebt das virtuelle Modell entsprechend der gefundenen wichtigen Punkte.
6. Haupt Thread: Wiederholen aus Schritt 2

Einige Abbild Markersysteme stellen nur einen einzelnen Pixel Speicherort bereit (andere stellen die vollständige Transformation bereit, in dem dieser Abschnitt nicht benötigt wird), was einem Ray möglicher Standorte entspricht. Um zu einem einzelnen 3D--Speicherort zu gelangen, können wir mehrere Strahlen nutzen und das Endergebnis nach dem ungefähren Schnittpunkt suchen. Gehen Sie hierzu wie folgt vor:
1. Schleife zum Erfassen mehrerer Kamerabilder
2. Suchen der zugehörigen featurepunkte und ihrer weltweiten Strahlen
3. Wenn Sie ein Wörterbuch mit Features haben, die jeweils über mehrere Welt Strahlen verfügen, können Sie den folgenden Code verwenden, um die Schnittmenge dieser Strahlen zu lösen:

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

Bei zwei oder mehr nach verfolgten tagstandorten können Sie eine modellierte Szene so positionieren, dass Sie dem aktuellen Szenario des Benutzers entspricht. Wenn Sie die Schwerkraft nicht annehmen können, benötigen Sie drei Tag-Orte. In vielen Fällen verwenden wir ein Farbschema, bei dem weiße Bereiche in Echtzeit überwachte tagspeicher Orte darstellen und blaue Bereiche modellierte tagspeicher Orte darstellen. Dadurch kann der Benutzer die ausrichtungsqualität visuell einschätzen. Wir gehen davon aus, dass Sie das folgende Setup in allen Anwendungen ausführen:
* Zwei oder mehr modellierte tagspeicher Orte
* Ein "Kalibrierungs Raum", bei dem es sich in der Szene um das übergeordnete Element der Tags handelt.
* Kamera Funktions Bezeichner
* Das Verhalten, bei dem der Kalibrierungsbereich verschoben wird, um die modellierten Tags mit den Echt Zeit Tags auszurichten (wir sind vorsichtig, um den übergeordneten Bereich und nicht die modellierten Marker selbst zu verschieben, weil eine andere Verbindung relativ zu diesen Tags ist).

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

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Mithilfe von LEDs oder anderen Erkennungs Bibliotheken nachverfolgen oder identifizieren Sie in der Praxis markierte Objekte/Gesichter in der Praxis

Beispiele:
* Industrieroboter mit LEDs (oder QR-Codes zum langsameren Verschieben von Objekten)
* Identifizieren und erkennen von Objekten im Raum
* Identifizieren und erkennen von Personen im Raum, z. b. Platzieren von Holographic Contact Cards über Gesichter

## <a name="see-also"></a>Siehe auch
* [Beispiel für eine abrechenbare Kamera](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Ausrichtbare Kamera in Unity](../unity/locatable-camera-in-unity.md)
* [Mixed-Reality-Aufnahme](/hololens/holographic-photos-and-videos)
* [Mixed Reality-Aufnahme für Entwickler](mixed-reality-capture-for-developers.md)
* [Einführung in Media Capture](/windows/uwp/audio-video-camera/)
* [Beispiel für die holografische Gesichts Verfolgung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)