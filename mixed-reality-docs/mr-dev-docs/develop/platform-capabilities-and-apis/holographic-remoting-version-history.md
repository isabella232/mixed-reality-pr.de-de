---
title: Holographic Remoting Version History
description: Bleiben Sie über den Versionsverlauf des Holographic Remoting-Features für HoloLens 2 auf dem laufenden.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, Versionsverlauf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 93ab38108d5ad557d61ad366ebb7aebd8cb65ab7
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944702"
---
# <a name="holographic-remoting-version-history"></a>Holographic Remoting Version History

> [!IMPORTANT]
> Dieser Leitfaden gilt speziell für Holographic Remoting auf HoloLens 2.

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
* PerceptionDeviceSetCreateFactoryOverride wurde implementiert, wodurch sichergestellt wird, dass PerceptionDevice.dll, die mit Holographic Remoting ausgeliefert wird, die im Lieferumfang von Windows 10.

## <a name="version-230-october-2-2020"></a>Version 2.3.0 (2. Oktober 2020) <a name="v2.3.0"></a>

* Es wurden Abstürze behoben, die bei angehaltenem Holographic Remoting Player passieren können.
* Verbesserungen der Stabilität.

## <a name="version-223-august-28-2020"></a>Version 2.2.3 (28. August 2020) <a name="v2.2.3"></a>

* Fehlerbehebungen und Stabilitätsverbesserungen.

## <a name="version-222-july-10-2020"></a>Version 2.2.2 (10. Juli 2020) <a name="v2.2.2"></a>

* Ein Problem mit [HolographicCamera.LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) und [HolographicCamera.RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) wurde behoben, bei dem beim Streamen von einem headset keine vertices vertices verdecktes Bereichsgitternetz Windows Mixed Reality wurden.
* Absturz behoben, der bei einer schlechten Netzwerkverbindung passieren kann.

## <a name="version-221-july-6-2020"></a>Version 2.2.1 (6. Juli 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [Zertifizierungskit für Windows-Apps](https://developer.microsoft.com/windows/downloads/app-certification-kit/) Überprüfung mit Version [2.2.0](holographic-remoting-version-history.md#v2.2.0) schlägt fehl. Falls Sie version [2.2.0](holographic-remoting-version-history.md#v2.2.0) verwenden und Ihre Anwendung an den Microsoft Store p lease übermitteln möchten, der auf mindestens Version 2.2.1 aktualisiert wurde.
* [Es wurden Zertifizierungskit für Windows-Apps](https://developer.microsoft.com/windows/downloads/app-certification-kit/) Kompatibilitätsprobleme behoben.

## <a name="version-220-july-1-2020"></a>Version 2.2.0 (1. Juli 2020) <a name="v2.2.0"></a>

* Der Holographic Remoting-Player kann jetzt auf PCs installiert werden, auf denen [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)ausgeführt wird, sodass das Streamen an immersive Headsets möglich ist.
* [Motion-Controller](../../design/motion-controllers.md) werden jetzt von Holographic Remoting unterstützt, und controllerspezifische Daten können über [SpatialInteractionSource.Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)abgerufen werden.
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) wird jetzt unterstützt, und die aktuelle Phase kann über [SpatialStageFrameOfReference.Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)abgerufen werden. Darüber hinaus kann eine neue Phase über [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)angefordert werden.
* In früheren Versionen wurde die Posenvorhersage auf der Playerseite vom Holographic Remoting-Player verarbeitet. Ab Version 2.2.0 verfügt Holographic Remoting über eine Zeitsynchronisierung, und die Vorhersage erfolgt vollständig durch die Remoteanwendung. Benutzer sollten auch eine verbesserte Hologrammstabilität in schwierigen Netzwerksituationen erwarten.

## <a name="version-213-may-25-2020"></a>Version 2.1.3 (25. Mai 2020) <a name="v2.1.3"></a>

* Geändertes Verhalten des [HolographicSpace.CameraAdded-Ereignisses.](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) In früheren Versionen war **nicht** garantiert, dass eine hinzugefügte [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) auch über ein gültiges [HolographicCameraPose verfügt,](/uwp/api/windows.graphics.holographic.holographiccamerapose) wenn der nächste Frame über [HolographicSpace.CreateNextFrame](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe)erstellt wird. Ab Version 2.1.3 wird [HolographicSpace.CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) mit Posendaten aus dem Holographic Remoting Player synchronisiert. Benutzer können davon ausgehen, dass beim Hinzufügen einer Kamera auch eine gültige [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) für diese Kamera im nächsten Frame verfügbar ist.
* **Deaktiviert** zu DepthBufferStreamResolution hinzugefügt, das zum Deaktivieren des Tiefenpufferstreamings über RemoteContext.ConfigureDepthVideoStream verwendet werden kann. Beachten Sie, dass bei Verwendung [von HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) ein Fehler *mit* E_ILLEGAL_METHOD_CALL.
* Der Startbildschirm des Holographic Remoting-Players wurde neu gestaltet und blockiert jetzt nicht mehr die Benutzeransicht.
* Stabilitätsverbesserungen und Fehlerbehebungen.

## <a name="version-212-april-5-2020"></a>Version 2.1.2 (5. April 2020) <a name="v2.1.2"></a>

* Es wurde ein Problem mit der Abwärtskompatibilität von Audiodaten zwischen dem neuesten Holographic Remoting-Player und Remote-Apps mit einer niedrigeren Version als 2.1.0 behoben.
* Ein Raumankerproblem wurde behoben, durch das der Holographic Remoting-Player unerwartet geschlossen wurde. Dieses Problem betrifft auch benutzerdefinierte Player.

## <a name="version-211-march-20-2020"></a>Version 2.1.1 (20. März 2020) <a name="v2.1.1"></a>

* Videocodierungsproblem bei Remote-Apps bei Verwendung von AMD-GPUs behoben.
* Leistungsverbesserungen für Holographic Remoting Player.

## <a name="version-210-march-11-2020"></a>Version 2.1.0 (11. März 2020) <a name="v2.1.0"></a>

* Umgeschalteter Netzwerktransport zur Verwendung [von RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) über UDP. Sichere Verbindungen verwenden [jetzt SRTP.](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) Beachten Sie, dass [der Holographic Remoting Player](holographic-remoting-player.md) weiterhin mit allen holografischen Remotingversionen kompatibel ist, die zuvor veröffentlicht wurden. Um sowohl den Holographic Remoting Player als auch die remote-App vom neuen Netzwerktransport zu profitieren, muss Version 2.1.0 verwendet werden.
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

* Absturz bei Verwendung der Triggerschaltfläche von VR-Controllern behoben. Holographic Remoting unterstützt controller nicht vollständig, nur die Triggerschaltfläche und die Windows-Schaltfläche funktionieren, wenn sie mit HoloLens 2 gekoppelt sind.

## <a name="version-209-september-19-2019"></a>Version 2.0.9 (19. September 2019) <a name="v2.0.9"></a>

* Unterstützung für [SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter) hinzugefügt
* Es wurde eine neue Schnittstelle ```IPlayerContext2``` (implementiert von ```PlayerContext``` ) hinzugefügt, die die folgenden Member bereitstellt:
  - [BlitRemoteFrameTimeout-Eigenschaft.](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)
* Mehrwert ```Failed_RemoteFrameTooOld``` zu ```BlitResult```
* Stabilitäts- und Zuverlässigkeitsverbesserungen

## <a name="version-208-august-20-2019"></a>Version 2.0.8 (20. August 2019) <a name="v2.0.8"></a>

* Absturz beim Aufrufen [von HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) mit [idXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) als Parameter behoben.
* Verbesserungen bei Stabilität und Zuverlässigkeit

## <a name="version-207-july-26-2019"></a>Version 2.0.7 (26. Juli 2019) <a name="v2.0.7"></a>

* Erste öffentliche Version von Holographic Remoting für HoloLens 2.

## <a name="see-also"></a>Weitere Informationen

* [Schreiben einer Holographic Remoting-Remote-App mit Windows Mixed Reality APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs](holographic-remoting-create-remote-openxr.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen bei Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)