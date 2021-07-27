---
title: Holographic Remoting-Versionsverlauf
description: Bleiben Sie über den Versionsverlauf des Holographic Remoting-Features für HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 07/20/2021
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, Versionsverlauf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: ec810683a556bebfe92615e9085d26bf33cf7f2c
ms.sourcegitcommit: ebc22c5adee0e785e45fb25fade83191e920f92b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2021
ms.locfileid: "114585723"
---
# <a name="holographic-remoting-version-history"></a>Holographic Remoting-Versionsverlauf

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic Remoting HoloLens 2.

## <a name="version-261-july-20-2021"></a>Version 2.6.1 (20. Juli 2021) <a name="v2.6.1"></a>
* Die XR_MSFT_holographic_remoting_speech-Erweiterung ermöglicht jetzt die erneute Initialisierung der Spracherkennung mit neuen Parametern während einer laufenden Sitzung.
* Es wurde ein Problem behoben, bei dem die Zuverlässigkeit der Spracherkennung über mehrere Verbindungen abgenommen hat.
* Verschiedene Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-260-june-10-2021"></a>Version 2.6.0 (10. Juni 2021) <a name="v2.6.0"></a>
* Holographic Remoting mithilfe der OpenXR-API unterstützt jetzt:
  * Die neue XR_MSFT_holographic_remoting_speech, mit der Anwendungen auf benutzerdefinierte Sprachbefehle in verschiedenen Sprachen lauschen können.
  * Die XR_MSFT_scene_understanding-Erweiterung, die Anwendungen eine strukturierte, grundlegende Darstellung der Ebenen, Gitternetze und Objekte in der Umgebung des Benutzers bietet, die die Entwicklung räumlicher Anwendungen ermöglicht. Mit dem Nachteil, dass XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT die einzige Konsistenz ist, die von xrComputeNewSceneMSFT unterstützt wird.
  * Die XR_MSFT_spatial_graph_bridge-Erweiterung, mit der Anwendungen XrSpace-Handles zum Nachverfolgen der Spatial Graph-Knoten anderer Windows Mixed Reality-Geräteplattformbibliotheken oder APIs erstellen können. Mit der Einschränkung, dass XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT knotentyp ist, der von xrCreateSpatialGraphNodeSpaceMSFT unterstützt wird. 
* Holographic Remoting mithilfe der Mixed Reality-API unterstützt jetzt:
  * Die SpatialGraphInteropPreview.CreateCoordinateSystemForNode-Überladungen, mit denen Anwendungen statische Spatial Graph-Knoten nachverfolgen können, damit Benutzer Überblicke über Orte und Dinge in ihrer Umgebung haben.
* Holographic Remoting mit openXR- und Mixed Reality-APIs unterstützt jetzt:
  * Das Microsoft.MixedReality.SceneUnderstanding SDK, mit dem Anwendungen eine Beschreibung der Szene um den Benutzer (z. B. Wände, Boden und Oberflächen) berechnen können, die Quads, Gitter und Hinweise zur Inhaltsplatzierung bereitstellt.
  * Das Microsoft.MixedReality.QR SDK, mit dem Anwendungen den Standort, die Größe und den Inhalt erkannter QR-Codes nachverfolgen können.
* Das OpenXR-Remotebeispiel wurde aktualisiert und umfasst nun Folgendes: 
  * Ein Beispiel für die Verwendung der XR_MSFT_holographic_remoting_speech Erweiterung.
* Das Mixed Reality Remotebeispiel wurde aktualisiert und enthält Folgendes:  
  * Ein Beispiel für die Verwendung des Microsoft.MixedReality.SceneUnderstanding SDK.
  * Ein Beispiel für die Verwendung des Microsoft.MixedReality.QR SDK (das den vorherigen Mechanismus zur Erkennung von QR-Code ersetzt).
* Der Holographic Remoting-Player zeigt jetzt eine Ladeanimation an, während die Verbindung hergestellt wird.
* Es wurden Probleme mit der RenderDoc-Kompatibilität sowohl in der OpenXR-API-Runtime als auch im Mixed Reality-API-Beispiel behoben.
* Verschiedene Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-250-february-12-2021"></a>Version 2.5.0 (12. Februar 2021) <a name="v2.5.0"></a>
* Holographic Remoting mithilfe der [OpenXR-API unterstützt](../native/openxr.md) jetzt:
  * XR_MSFT_spatial_anchor Erweiterung. Mit dieser Erweiterung kann eine Anwendung Raumanker erstellen, bei denen es sich um beliebige Freiraumpunkte in der physischen Umgebung des Benutzers handelt, die von der Laufzeit nachverfolgt werden.
  * XR_MSFT_controller_model Erweiterung. Diese Erweiterung bietet einen Mechanismus zum Laden von GLTF-Modellen für Controller.
  * Benutzerdefinierte Datenkanäle als Teil der XR_MSFT_holographic_remoting Erweiterung. Ein Beispiel für , das im [OpenXR-Remotebeispiel gezeigt wird.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)
* Verbesserte Synchronisierung zwischen Player und Remoteseite. Dies ermöglicht eine dynamisch ändernde Posen- und Framepufferung, wodurch sichergestellt wird, dass remote gerenderter Inhalt die Displays reibungslos mit der erwarteten Zielbildrate erreicht.
* Verbesserte Leistung des Holographic Remoting-Players, der über die -Microsoft Store. Auf HoloLens 2 wird der Player jetzt mit 60 Frames pro Sekunde solide ausgeführt.
* Optimierte Übertragung räumlicher Oberflächengitter, die über [SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) von einer Remote-App abgefragt werden können.
* Ein Problem wurde behoben, bei dem das Aufrufen von SpatialAnchorManager-Methoden oder das Freigeben von Ankern Ausnahmen beim Trennen der Verbindung verursachte.
* Threadingproblem wurde behoben, das beim Schließen von PlayerContext- oder RemoteContext-Instanzen zu Abstürzen führt.
* Holographic Remoting Player on Desktop (Holographic Remoting Player auf Desktop): Zeigt eine Fehlermeldung an, wenn Windows Mixed Reality nicht installiert ist, anstatt automatisch zu schließen.
* Viele andere Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-241-january-22-2021"></a>Version 2.4.1 (22. Januar 2021) <a name="v2.4.1"></a>

* Ein Problem wurde behoben, bei dem SpatialAnchorManager::RequestStoreAsync beim Aufrufen während der Verbindung nicht zuverlässig funktionierte.
* Ein Problem wurde behoben, bei dem SpatialAnchorManager::TrySave einen Anker nicht ordnungsgemäß speichern konnte, wenn der an diesem Anker nicht verkettet werden kann.

## <a name="version-240-december-1-2020"></a>Version 2.4.0 (1. Dezember 2020) <a name="v2.4.0"></a>

* Holographic Remoting unterstützt jetzt das Schreiben von Remote-Apps mithilfe der [OpenXR-API](../native/openxr.md). Informationen zu den ersten Schritte finden Sie unter Schreiben einer [Holographic Remoting-Remote-App mithilfe von OpenXR-APIs.](holographic-remoting-create-remote-openxr.md)
* Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-231-october-10-2020"></a>Version 2.3.1 (10. Oktober 2020) <a name="v2.3.1"></a>

* Regression mit Vorhersage von Remoteposen korrigiert, was zu visuellem Jitter führte.
* PerceptionDeviceSetCreateFactoryOverride wurde implementiert, wodurch sichergestellt wird, dass PerceptionDevice.dll im Lieferumfang von Holographic Remoting gelieferte Version nicht mit der im Lieferumfang Windows 10.

## <a name="version-230-october-2-2020"></a>Version 2.3.0 (2. Oktober 2020) <a name="v2.3.0"></a>

* Es wurden Abstürze behoben, die bei angehaltenem Holographic Remoting Player passieren können.
* Verbesserungen der Stabilität.

## <a name="version-223-august-28-2020"></a>Version 2.2.3 (28. August 2020) <a name="v2.2.3"></a>

* Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-222-july-10-2020"></a>Version 2.2.2 (10. Juli 2020) <a name="v2.2.2"></a>

* Es wurde ein Problem behoben, bei dem [HolographicCamera.LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) und [HolographicCamera.RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) beim Streamen von einem Headset keine vertices vertices verdecktes Bereichsgitternetz Windows Mixed Reality zurückgeben.
* Absturz behoben, der bei einer schlechten Netzwerkverbindung passieren kann.

## <a name="version-221-july-6-2020"></a>Version 2.2.1 (6. Juli 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [Windows App Certification Kit-Überprüfung](https://developer.microsoft.com/windows/downloads/app-certification-kit/) mit Version [2.2.0 ist](holographic-remoting-version-history.md#v2.2.0) nicht erfolgreich. Falls Sie Version [2.2.0](holographic-remoting-version-history.md#v2.2.0) verwenden und Ihre Anwendung an den Microsoft Store p lease übermitteln möchten, der mindestens auf Version 2.2.1 aktualisiert wurde.
* Es [wurden Windows App Certification Kit-Kompatibilitätsprobleme](https://developer.microsoft.com/windows/downloads/app-certification-kit/) behoben.

## <a name="version-220-july-1-2020"></a>Version 2.2.0 (1. Juli 2020) <a name="v2.2.0"></a>

* Der Holographic Remoting-Player kann jetzt auf [](../../discover/navigating-the-windows-mixed-reality-home.md)PCs installiert werden, auf denen Windows Mixed Reality ausgeführt wird, wodurch das Streamen an immersive Headsets möglich ist.
* [Motion-Controller](../../design/motion-controllers.md) werden jetzt von Holographic Remoting unterstützt, und controllerspezifische Daten können über [SpatialInteractionSource.Controller abgerufen werden.](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) wird jetzt unterstützt, und die aktuelle Phase kann über [SpatialStageFrameOfReference.Current abgerufen werden.](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) Darüber hinaus kann eine neue Phase über [SpatialStageFrameOfReference.RequestNewStageAsync angefordert werden.](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* In früheren Versionen wurde die Vorhersage von Posen auf Spielerseite vom Holographic Remoting-Player verarbeitet. Ab Version 2.2.0 verfügt Holographic Remoting über eine Zeitsynchronisierung, und die Vorhersage wird vollständig von der Remoteanwendung durchgeführt. Benutzer sollten auch in schwierigeren Netzwerksituationen eine verbesserte Hologrammstabilität erwarten.

## <a name="version-213-may-25-2020"></a>Version 2.1.3 (25. Mai 2020) <a name="v2.1.3"></a>

* Das Verhalten des [HolographicSpace.CameraAdded-Ereignisses wurde](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) geändert. In früheren Versionen  war nicht garantiert, dass eine hinzugefügte [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) auch über ein gültiges [HolographicCameraPose verfügte,](/uwp/api/windows.graphics.holographic.holographiccamerapose) wenn der nächste Frame über [HolographicSpace.CreateNextFrame erstellt wurde.](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe) Ab Version 2.1.3 wird [HolographicSpace.CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) mit Posendaten aus dem Holographic Remoting Player synchronisiert. Benutzer können davon ausgehen, dass beim Hinzugefügten einer Kamera auch ein gültiges [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) für diese Kamera auf dem nächsten Frame verfügbar ist.
* Deaktiviert **zu** DepthBufferStreamResolution hinzugefügt, das zum Deaktivieren des Tiefenpufferstreamings über RemoteContext.ConfigureDepthVideoStream verwendet werden kann. Beachten Sie, dass bei Verwendung [von HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) ein Fehler *mit* E_ILLEGAL_METHOD_CALL.
* Der Startbildschirm des Holographic Remoting-Players wurde neu gestaltet und blockiert jetzt nicht mehr die Benutzeransicht.
* Stabilitätsverbesserungen und Fehlerbehebungen.

## <a name="version-212-april-5-2020"></a>Version 2.1.2 (5. April 2020) <a name="v2.1.2"></a>

* Es wurde ein Problem mit der Abwärtskompatibilität von Audiodaten zwischen dem neuesten Holographic Remoting-Player und Remote-Apps mit einer niedrigeren Version als 2.1.0 behoben.
* Ein Raumankerproblem wurde behoben, durch das der Holographic Remoting-Player unerwartet geschlossen wurde. Dieses Problem betrifft auch benutzerdefinierte Player.

## <a name="version-211-march-20-2020"></a>Version 2.1.1 (20. März 2020) <a name="v2.1.1"></a>

* Videocodierungsproblem bei Remote-Apps bei Verwendung von AMD-GPUs behoben.
* Leistungsverbesserungen für Holographic Remoting Player.

## <a name="version-210-march-11-2020"></a>Version 2.1.0 (11. März 2020) <a name="v2.1.0"></a>

* Umgeschalteter Netzwerktransport zur Verwendung [von RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) über UDP. Sichere Verbindungen verwenden [jetzt SRTP.](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) Beachten Sie, dass [der Holographic Remoting Player](holographic-remoting-player.md) weiterhin mit allen holografischen Remotingversionen kompatibel ist, die zuvor veröffentlicht wurden. Um vom neuen Netzwerktransport zu profitieren, müssen sowohl der Holographic Remoting Player als auch die remote app in Frage Version 2.1.0 verwenden.
* Unterstützung für [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer wurde hinzugefügt.](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 

## <a name="version-2020-february-2-2020"></a>Version 2.0.20 (2. Februar 2020) <a name="v2.0.20"></a>

* Verschiedene Fehler, die zu Abstürzen führen, wurden behoben.

## <a name="version-2018-december-17-2019"></a>Version 2.0.18 (17. Dezember 2019) <a name="v2.0.18"></a>

* Unterstützung für [HolographicViewConfiguration hinzugefügt](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Es wurden verschiedene Fehler behoben, die zu Abstürzen geführt haben.
* Ein Fehler wurde behoben, bei dem ein HolographicSpace.CameraAdded-Rückruf erforderlich war, damit eine HolographicCamera akzeptiert und als hinzugefügte Kamera im HolographicFrame angezeigt wird.

## <a name="version-2016-november-11-2019"></a>Version 2.0.16 (11. November 2019) <a name="2.0.16"></a>

* Deadlock bei der QR-Codenachverfolgung wurde behoben.
* Nicht überwachte Ausnahme aufgrund eines blockierenden Wartezustands im Hauptthread behoben.

## <a name="version-2014-october-26-2019"></a>Version 2.0.14 (26. Oktober 2019) <a name="v2.0.14"></a>

* Unterstützung für neue PerceptionDevice-APIs (Windows 10 Update vom November 2019).
* Es wurde ein Problem behoben, das verhinderte, dass Hold-Gestenereignisse von SpatialGestureRecognizer ausgelöst werden.
* Threadingproblem bei Verwendung von SpatialSurfaceObserver.SetBoundingVolume wurde behoben.

## <a name="version-2012-october-18-2019"></a>Version 2.0.12 (18. Oktober 2019) <a name="v2.0.12"></a>

* Absturz in SpatialGestureRecognizer bei Verwendung von NavigationRail(X/Y/Z) wurde behoben.

## <a name="version-2010-october-10-2019"></a>Version 2.0.10 (10. Oktober 2019) <a name="v2.0.10"></a>

* Absturz bei Verwendung der Triggerschaltfläche von VR-Controllern behoben. Holographic Remoting unterstützt controller nicht vollständig, nur die Triggerschaltfläche und die schaltfläche Windows funktionieren, wenn sie mit HoloLens 2 gekoppelt sind.

## <a name="version-209-september-19-2019"></a>Version 2.0.9 (19. September 2019) <a name="v2.0.9"></a>

* Unterstützung für [SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter) hinzugefügt
* Es wurde eine neue Schnittstelle ```IPlayerContext2``` (implementiert von ```PlayerContext``` ) hinzugefügt, die die folgenden Member bereitstellt:
  - [BlitRemoteFrameTimeout-Eigenschaft.](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)
* Mehrwert ```Failed_RemoteFrameTooOld``` zu ```BlitResult```
* Stabilitäts- und Zuverlässigkeitsverbesserungen

## <a name="version-208-august-20-2019"></a>Version 2.0.8 (20. August 2019) <a name="v2.0.8"></a>

* Absturz beim Aufrufen von [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) mit einem [IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) als Parameter behoben.
* Stabilitäts- und Zuverlässigkeitsverbesserungen

## <a name="version-207-july-26-2019"></a>Version 2.0.7 (26. Juli 2019) <a name="v2.0.7"></a>

* Erste öffentliche Version von Holographic Remoting für HoloLens 2.

## <a name="see-also"></a>Weitere Informationen

* [Schreiben einer Holographic Remoting-Remote-App mit Windows Mixed Reality-APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs](holographic-remoting-create-remote-openxr.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)