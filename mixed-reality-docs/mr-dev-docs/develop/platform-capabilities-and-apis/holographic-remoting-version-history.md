---
title: Holographic Remoting Version History
description: Bleiben Sie über den Versionsverlauf des Holographic Remoting-Features für HoloLens 2 auf dem laufenden.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 07/20/2021
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, Versionsverlauf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 21ba89e477872f5dfa41468f1a7f2d7507affd681556d79843c195d7d5839e7b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223554"
---
# <a name="holographic-remoting-version-history"></a>Holographic Remoting Version History

> [!IMPORTANT]
> Dieser Leitfaden gilt speziell für Holographic Remoting auf HoloLens 2.

## <a name="version-261-july-20-2021"></a>Version 2.6.1 (20. Juli 2021) <a name="v2.6.1"></a>
* Die XR_MSFT_holographic_remoting_speech-Erweiterung ermöglicht jetzt die erneute Initialisierung der Spracherkennung mit neuen Parametern während einer laufenden Sitzung.
* Ein Problem wurde behoben, bei dem die Zuverlässigkeit der Spracherkennung über mehrere Verbindungen abgenommen hat.
* Verschiedene Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-260-june-10-2021"></a>Version 2.6.0 (10. Juni 2021) <a name="v2.6.0"></a>
* Holographic Remoting mit der OpenXR-API unterstützt jetzt Folgendes:
  * Die neue XR_MSFT_holographic_remoting_speech-Erweiterung, mit der Anwendungen auf benutzerdefinierte Sprachbefehle in verschiedenen Sprachen lauschen können.
  * Die XR_MSFT_scene_understanding-Erweiterung, die Anwendungen eine strukturierte, auf hoher Ebene dargestellte Darstellung der Ebenen, Gitternetze und Objekte in der Umgebung des Benutzers bereitstellt, wodurch die Entwicklung räumlicher Anwendungen ermöglicht wird. Mit dem Nachteil, dass XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT jedoch die einzige Konsistenz ist, die von xrComputeNewSceneMSFT unterstützt wird.
  * Die XR_MSFT_spatial_graph_bridge-Erweiterung, mit der Anwendungen XrSpace-Handles erstellen können, um die Spatial Graph Nodes anderer Windows Mixed Reality Geräteplattformbibliotheken oder APIs nachzuverfolgen. Allerdings ist XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT der einzige Knotentyp, der von xrCreateSpatialGraphNodeSpaceMSFT unterstützt wird. 
* Holographic Remoting mithilfe der Mixed Reality-API unterstützt jetzt Folgendes:
  * Die SpatialGraphInteropPreview.CreateCoordinateSystemForNode-Überladungen, mit denen Anwendungen statische räumliche Graph Knoten nachverfolgen können, sodass Benutzer über Orte und Dinge in ihrer Umgebung nachdenken können.
* Holographic Remoting mit openXR- und Mixed Reality-APIs unterstützt jetzt Folgendes:
  * Das Microsoft.MixedReality.SceneUnderstanding SDK, mit dem Anwendungen eine Beschreibung der Szene berechnen können, die den Benutzer umgibt (z. B. Wände, Etagen und Oberflächen), die Quader, Gitternetze und Hinweise zur Platzierung von Inhalten bereitstellt.
  * Das Microsoft.MixedReality.QR SDK, mit dem Anwendungen den Speicherort, die Größe und den Inhalt der erkannten QR-Codes nachverfolgen können.
* Das OpenXR-Remotebeispiel wurde aktualisiert, um Folgendes einzuschließen: 
  * Ein Beispiel für die Verwendung der erweiterung XR_MSFT_holographic_remoting_speech.
* Das Mixed Reality Remotebeispiel wurde aktualisiert und umfasst Folgendes:  
  * Ein Beispiel für die Verwendung des Microsoft.MixedReality.SceneUnderstanding SDK.
  * Ein Beispiel für die Verwendung des Microsoft.MixedReality.QR SDK (das den vorherigen Erkennungsmechanismus für QR-Code ersetzt).
* Der Holographic Remoting-Player zeigt jetzt eine Ladeanimation an, während die Verbindung hergestellt wird.
* Es wurden Probleme mit der RenderDoc-Kompatibilität sowohl in der OpenXR-API-Runtime als auch im Mixed Reality-API-Beispiel behoben.
* Verschiedene Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-250-february-12-2021"></a>Version 2.5.0 (12. Februar 2021) <a name="v2.5.0"></a>
* Holographic Remoting mit der [OpenXR-API](../native/openxr.md) unterstützt jetzt Folgendes:
  * XR_MSFT_spatial_anchor Erweiterung. Mit dieser Erweiterung kann eine Anwendung Raumanker erstellen, bei denen es sich um beliebige Freiraumpunkte in der physischen Umgebung des Benutzers handelt, die von der Laufzeit nachverfolgt werden.
  * XR_MSFT_controller_model Erweiterung. Diese Erweiterung bietet einen Mechanismus zum Laden von GLTF-Modellen für Controller.
  * Benutzerdefinierte Datenkanäle als Teil der XR_MSFT_holographic_remoting-Erweiterung. Ein Beispiel für , das im [OpenXR-Remotebeispiel](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)gezeigt wird.
* Verbesserte Synchronisierung zwischen Player und Remoteseite. Dies ermöglicht eine dynamische Änderung der Posen- und Framepufferung, wodurch sichergestellt wird, dass remote gerenderte Inhalte die Anzeigen mit der erwarteten Zielbildfrequenz reibungslos erreichen.
* Verbesserte Leistung des Holographic Remoting-Players, der über die Microsoft Store verfügbar ist. Auf HoloLens 2 wird der Player jetzt mit 60 Frames pro Sekunde solid ausgeführt.
* Optimierte Übertragung von Gitternetzen für räumliche Oberflächen, die über [SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) von einer Remote-App abgefragt werden können.
* Ein Problem wurde behoben, bei dem das Aufrufen von SpatialAnchorManager-Methoden oder das Freigeben von Ankern ausnahmen bei der Trennung verursacht hat.
* Threadingproblem behoben, das beim Schließen von PlayerContext- oder RemoteContext-Instanzen zu Abstürzen führte.
* Holographic Remoting Player auf dem Desktop: Zeigt eine Fehlermeldung an, wenn Windows Mixed Reality nicht installiert ist, anstatt im Hintergrund zu schließen.
* Viele andere Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-241-january-22-2021"></a>Version 2.4.1 (22. Januar 2021) <a name="v2.4.1"></a>

* Ein Problem mit SpatialAnchorManager::RequestStoreAsync wurde behoben, das beim Aufruf während der Verbindungsherstellung nicht zuverlässig funktionierte.
* Ein Problem wurde behoben, bei dem SpatialAnchorManager::TrySave einen Anker nicht ordnungsgemäß speichert, wenn der betreffende Anker nicht veränderbar ist.

## <a name="version-240-december-1-2020"></a>Version 2.4.0 (1. Dezember 2020) <a name="v2.4.0"></a>

* Holographic Remoting unterstützt jetzt das Schreiben von Remote-Apps mithilfe der [OpenXR-API.](../native/openxr.md) Informationen zu den ersten Schritte finden Sie unter [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs.](holographic-remoting-create-remote-openxr.md)
* Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-231-october-10-2020"></a>Version 2.3.1 (10. Oktober 2020) <a name="v2.3.1"></a>

* Regression mit Remoteposenvorhersage korrigiert, die visuelle Jitter verursacht hat.
* PerceptionDeviceSetCreateFactoryOverride wurde implementiert, wodurch sichergestellt wird, dass PerceptionDevice.dll, die mit Holographic Remoting ausgeliefert werden, nicht die version beeinträchtigen, die mit Windows 10 geliefert wird.

## <a name="version-230-october-2-2020"></a>Version 2.3.0 (2. Oktober 2020) <a name="v2.3.0"></a>

* Es wurden Abstürze behoben, die auftreten können, wenn der Holographic Remoting Player angehalten wird.
* Verbesserungen der Stabilität.

## <a name="version-223-august-28-2020"></a>Version 2.2.3 (28. August 2020) <a name="v2.2.3"></a>

* Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-222-july-10-2020"></a>Version 2.2.2 (10. Juli 2020) <a name="v2.2.2"></a>

* Ein Problem wurde behoben, bei dem [HolographicCamera.LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) und [HolographicCamera.RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) beim Streamen von einem Windows Mixed Reality Headset keine verborgenen Bereichsgitternetzvertices zurückgeben.
* Absturz behoben, der bei einer schlechten Netzwerkverbindung auftreten kann.

## <a name="version-221-july-6-2020"></a>Version 2.2.1 (6. Juli 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [Windows App Certification Kit-Überprüfung](https://developer.microsoft.com/windows/downloads/app-certification-kit/) mit Version [2.2.0](holographic-remoting-version-history.md#v2.2.0) schlägt fehl. Falls Sie version [2.2.0](holographic-remoting-version-history.md#v2.2.0) verwenden und Ihre Anwendung an den Microsoft Store p lease übermitteln möchten, der auf mindestens Version 2.2.1 aktualisiert wurde.
* Es wurden [Windows Kompatibilitätsprobleme](https://developer.microsoft.com/windows/downloads/app-certification-kit/) mit dem App Certification Kit behoben.

## <a name="version-220-july-1-2020"></a>Version 2.2.0 (1. Juli 2020) <a name="v2.2.0"></a>

* Der Holographic Remoting-Player kann jetzt auf PCs installiert werden, auf [denen Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)ausgeführt wird, sodass das Streamen an immersive Headsets möglich ist.
* [Motion-Controller](../../design/motion-controllers.md) werden jetzt von Holographic Remoting unterstützt, und controllerspezifische Daten können über [SpatialInteractionSource.Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)abgerufen werden.
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) wird jetzt unterstützt, und die aktuelle Phase kann über [SpatialStageFrameOfReference.Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)abgerufen werden. Darüber hinaus kann eine neue Phase über [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)angefordert werden.
* In früheren Versionen wurde die Posenvorhersage auf der Playerseite vom Holographic Remoting-Player verarbeitet. Ab Version 2.2.0 verfügt Holographic Remoting über eine Zeitsynchronisierung, und die Vorhersage erfolgt vollständig durch die Remoteanwendung. Benutzer sollten auch eine verbesserte Hologrammstabilität in schwierigen Netzwerksituationen erwarten.

## <a name="version-213-may-25-2020"></a>Version 2.1.3 (25. Mai 2020) <a name="v2.1.3"></a>

* Geändertes Verhalten des [HolographicSpace.CameraAdded-Ereignisses.](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) In früheren Versionen war **nicht** garantiert, dass eine hinzugefügte [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) auch über ein gültiges [HolographicCameraPose verfügt,](/uwp/api/windows.graphics.holographic.holographiccamerapose) wenn der nächste Frame über [HolographicSpace.CreateNextFrame](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe)erstellt wird. Ab Version 2.1.3 wird [HolographicSpace.CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) mit Posendaten aus dem Holographic Remoting Player synchronisiert. Benutzer können davon ausgehen, dass beim Hinzufügen einer Kamera auch eine gültige [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) für diese Kamera im nächsten Frame verfügbar ist.
* **Deaktiviert** zu DepthBufferStreamResolution hinzugefügt, die zum Deaktivieren des Tiefenpufferstreamings über RemoteContext.ConfigureDepthVideoStream verwendet werden kann. Beachten Sie, dass bei Verwendung von [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) mit *E_ILLEGAL_METHOD_CALL* fehlschlägt.
* Der Startbildschirm des Holographic Remoting Player wurde neu gestaltet und blockiert jetzt nicht mehr die Benutzeransicht.
* Stabilitätsverbesserungen und Fehlerbehebungen.

## <a name="version-212-april-5-2020"></a>Version 2.1.2 (5. April 2020) <a name="v2.1.2"></a>

* Ein Problem mit der Abwärtskompatibilität von Audiodaten zwischen dem neuesten Holographic Remoting-Player und Remote-Apps mit einer niedrigeren Version als 2.1.0 wurde behoben.
* Ein Raumankerproblem wurde behoben, durch das der Holographic Remoting-Player unerwartet geschlossen wurde. Dieses Problem betrifft auch benutzerdefinierte Player.

## <a name="version-211-march-20-2020"></a>Version 2.1.1 (20. März 2020) <a name="v2.1.1"></a>

* Ein Problem mit der Videocodierung bei Remote-Apps bei Verwendung von AMD-GPUs wurde behoben.
* Leistungsverbesserungen für Holographic Remoting Player.

## <a name="version-210-march-11-2020"></a>Version 2.1.0 (11. März 2020) <a name="v2.1.0"></a>

* Umgeschalteter Netzwerktransport zur Verwendung von [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) über UDP. Sichere Verbindungen verwenden jetzt [SRTP.](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) Beachten Sie, dass der [Holographic Remoting Player](holographic-remoting-player.md) immer noch mit allen holographic Remoting-Versionen kompatibel ist, die zuvor veröffentlicht wurden. Um vom neuen Netzwerktransport zu profitieren, müssen sowohl der Holographic Remoting Player als auch die betreffende Remote-App Version 2.1.0 verwenden.
* Unterstützung für [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)wurde hinzugefügt. 

## <a name="version-2020-february-2-2020"></a>Version 2.0.20 (2. Februar 2020) <a name="v2.0.20"></a>

* Es wurden verschiedene Fehler behoben, die zu Abstürzen geführt haben.

## <a name="version-2018-december-17-2019"></a>Version 2.0.18 (17. Dezember 2019) <a name="v2.0.18"></a>

* Unterstützung für [HolographicViewConfiguration hinzugefügt](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Es wurden verschiedene Fehler behoben, die zu Abstürzen geführt haben.
* Ein Fehler wurde behoben, bei dem ein HolographicSpace.CameraAdded-Rückruf erforderlich war, damit eine HolographicCamera akzeptiert und als hinzugefügte Kamera im HolographicFrame angezeigt wird.

## <a name="version-2016-november-11-2019"></a>Version 2.0.16 (11. November 2019) <a name="2.0.16"></a>

* Deadlock bei der QR-Codenachverfolgung wurde behoben.
* Es wurde eine nicht überwachte Ausnahme aufgrund eines blockierenden Wartezustands im Hauptthread behoben.

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