---
title: Holographic Remoting-Versionsverlauf
description: Bleiben Sie auf dem neuesten Stand mit dem Versionsverlauf der Holographic Remoting-Funktion für hololens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting, Versionsverlauf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: e1f80d0d2cbd02b78ed07e3ec60825ffe1059309
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699009"
---
# <a name="holographic-remoting-version-history"></a>Holographic Remoting-Versionsverlauf

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

## <a name="version-241-january-22-2021"></a>Version 2.4.1 (22. Januar 2021) <a name="v2.4.1"></a>

* Behobene Problem mit spatialanchormanager:: requeststoreasync funktioniert nicht zuverlässig, wenn aufgerufen wird, während eine Verbindung hergestellt wurde.
* Behobene Problem mit spatialanchormanager:: TrySave speichert einen Anker nicht ordnungsgemäß, wenn der fragliche Anker nicht zu finden ist.

## <a name="version-240-december-1-2020"></a>Version 2.4.0 (1. Dezember 2020) <a name="v2.4.0"></a>

* Holographic Remoting unterstützt jetzt das Schreiben von Remote-Apps mithilfe der [openxr-API](../native/openxr.md). In den ersten Schritten erfahren Sie, wie Sie [eine Holographic Remoting-Remote-app mit openxr-APIs schreiben](holographic-remoting-create-remote-openxr.md) .
* Fehlerbehebungen und Verbesserungen der Stabilität.

## <a name="version-231-october-10-2020"></a>Version 2.3.1 (10. Oktober 2020) <a name="v2.3.1"></a>

* Korrigiert der Regression mit Remote-Pose-Vorhersage, die den visuellen Jitter verursacht hat.
* "Perzeptiondevicesetkreatefactor" wurde implementiert, wodurch sichergestellt wird, dass PerceptionDevice.dll, die mit Holographic Remoting ausgeliefert wurden, nicht mit der Version von Windows 10 in Konflikt steht.

## <a name="version-230-october-2-2020"></a>Version 2.3.0 (2. Oktober 2020) <a name="v2.3.0"></a>

* Es wurden Abstürze korrigiert, die auftreten können, wenn der Holographic Remoting Player angehalten wird.
* Verbesserungen der Stabilität.

## <a name="version-223-august-28-2020"></a>Version 2.2.3 (28. August 2020) <a name="v2.2.3"></a>

* Fehlerbehebungen und Verbesserungen der Stabilität.

## <a name="version-222-july-10-2020"></a>Version 2.2.2 (10. Juli 2020) <a name="v2.2.2"></a>

* Es wurde ein Problem mit [holographiccamera. leftviewportparameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) und [holographiccamera. rightviewportparameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) behoben, bei dem das Streaming von einem Windows Mixed Reality-Headset keine ausgeblendeten Bereiche zurückgegeben hat.
* Ein Absturz wurde korrigiert, der mit einer schlechten Netzwerkverbindung auftreten kann.

## <a name="version-221-july-6-2020"></a>Version 2.2.1 (6. Juli 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> Die Validierung des [Zertifizierungs Kits für Windows-apps](https://developer.microsoft.com/windows/downloads/app-certification-kit/) mit Version [2.2.0](holographic-remoting-version-history.md#v2.2.0) schlägt fehl. Für den Fall, dass Sie die Version [2.2.0](holographic-remoting-version-history.md#v2.2.0) haben und Ihre Anwendung an die Microsoft Store-p-Lease übermitteln möchten, die auf mindestens Version 2.2.1 aktualisiert wurde.
* Kompatibilitätsprobleme beim [zertifizierungskit für Windows App](https://developer.microsoft.com/windows/downloads/app-certification-kit/)

## <a name="version-220-july-1-2020"></a>Version 2.2.0 (1. Juli 2020) <a name="v2.2.0"></a>

* Der Holographic Remoting Player kann nun auf PCs installiert werden, auf denen [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)ausgeführt wird, sodass es möglich ist, zu immersiven Headsets zu streamen.
* [Bewegungs Controller](../../design/motion-controllers.md) werden nun von Holographic Remoting unterstützt, und Controller spezifische Daten können über " [spatialinteraktionsource. Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)" abgerufen werden.
* [Spatialstageframeofreferenwird](/uwp/api/windows.perception.spatial.spatialstageframeofreference) jetzt unterstützt, und die aktuelle Phase kann über [spatialstageframeofreferen. Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)abgerufen werden. Außerdem kann eine neue Stufe über [spatialstageframeofreferen. requestnewstageasync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)angefordert werden.
* In früheren Versionen wurde die Pose-Vorhersage auf der Player Seite vom Holographic Remoting Player behandelt. Ab Version 2.2.0 verfügt Holographic Remoting über eine Zeitsynchronisierung, und die Vorhersage wird von der Remote Anwendung vollständig durchgeführt. Benutzer sollten außerdem eine verbesserte hologrammstabilität in schwierigen Netzwerk Situationen erwarten.

## <a name="version-213-may-25-2020"></a>Version 2.1.3 (dem 25. Mai 2020) <a name="v2.1.3"></a>

* Geändertes Verhalten des [holographicspace. cameraadded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) -Ereignisses. In früheren Versionen war **nicht** sichergestellt, dass ein hinzugefügter [holographiccamera](/uwp/api/windows.graphics.holographic.holographiccamera) auch über eine gültige [holographiccamerapose](/uwp/api/windows.graphics.holographic.holographiccamerapose) verfügt, wenn der nächste Frame über [holographicspace. kreatenextframe](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe)erstellt wird. Ab Version 2.1.3 wird [holographicspace. cameraadded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) mit dem Daten aus dem Holographic Remoting Player synchronisiert. Benutzer können davon ausgehen, dass beim Hinzufügen einer Kamera auch eine gültige [holographiccamerapose](/uwp/api/windows.graphics.holographic.holographiccamerapose) für die Kamera im nächsten Frame verfügbar ist.
* "Depthbufferstreamresolution" wurde **deaktiviert** , sodass das tiefe Puffer Streaming über RemoteContext.Configuredepthvideostream deaktiviert werden kann. Beachten Sie, dass bei Verwendung von [holographiccamerarenderingparameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) mit *E_ILLEGAL_METHOD_CALL* fehlschlägt.
* Der Startbildschirm des Holographic Remoting Player wurde umgestaltet und blockiert nun nicht die Ansicht "Benutzer".
* Verbesserungen der Stabilität und Fehlerbehebungen.

## <a name="version-212-april-5-2020"></a>Version 2.1.2 (5. April 2020) <a name="v2.1.2"></a>

* Es wurde ein Problem mit der audioabwärts Kompatibilität zwischen dem neuesten Holographic Remoting Player und Remote-apps mit einer Version kleiner als 2.1.0 behoben.
* Das Problem mit dem räumlichen Anker wurde behoben, das den Holographic Remoting-Player unerwartet geschlossen hat. Dieses Problem betrifft auch benutzerdefinierte Player.

## <a name="version-211-march-20-2020"></a>Version 2.1.1 (20. März 2020) <a name="v2.1.1"></a>

* Beheben von Video Codierungs Problemen mit Remote-Apps bei Verwendung von AMD-GPUs.
* Leistungsverbesserungen für Holographic Remoting Player.

## <a name="version-210-march-11-2020"></a>Version 2.1.0 (11. März 2020) <a name="v2.1.0"></a>

* Der Netzwerk Transport wurde zum Verwenden von [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) über UDP gewechselt. Sichere Verbindungen verwenden jetzt [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) . Beachten Sie, dass der [Holographic Remoting Player](holographic-remoting-player.md) immer noch mit allen zuvor veröffentlichten Holographic Remoting-Versionen kompatibel ist. Um vom neuen Netzwerk Transport profitieren zu können, müssen der Holographic Remoting Player und die betreffende Remote-app Version 2.1.0 verwenden.
* Unterstützung für [holographiccamer-deringparameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)hinzugefügt. 

## <a name="version-2020-february-2-2020"></a>Version 2.0.20 (2. Februar 2020) <a name="v2.0.20"></a>

* Es wurden verschiedene Fehler behoben, die zu Abstürzen führen.

## <a name="version-2018-december-17-2019"></a>Version 2.0.18 (17. Dezember 2019) <a name="v2.0.18"></a>

* Unterstützung für [holographicviewconfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration) hinzugefügt
* Es wurden verschiedene Fehler behoben, die zu Abstürzen führen.
* Es wurde ein Fehler behoben, bei dem ein holographicspace. cameraadded-Rückruf erforderlich war, damit ein holographiccamera akzeptiert und als hinzugefügte Kamera im holographicframe angezeigt werden konnte.

## <a name="version-2016-november-11-2019"></a>Version 2.0.16 (11. November 2019) <a name="2.0.16"></a>

* Deadlockfehler bei der Überwachung des QR-Codes.
* Eine unhandliche Ausnahme wurde aufgrund einer blockierenden Wartezeit im Haupt Thread korrigiert.

## <a name="version-2014-october-26-2019"></a>Version 2.0.14 (26. Oktober 2019) <a name="v2.0.14"></a>

* Unterstützung für neue "perceptiondevice"-APIs (Windows 10-Update vom November 2019).
* Ein Problem wurde behoben, bei dem das Auslösen von halte Gesten Ereignissen durch spatialgesturerecognizer verhindert wird.
* Das Threading Problem wurde behoben, wenn spatialsurfaceobserver. setboundingvolume verwendet wurde.

## <a name="version-2012-october-18-2019"></a>Version 2.0.12 (18. Oktober 2019) <a name="v2.0.12"></a>

* Absturz in spatialgesturerecognizer bei Verwendung von navigationrail (X/Y/Z) korrigiert.

## <a name="version-2010-october-10-2019"></a>Version 2.0.10 (10. Oktober 2019) <a name="v2.0.10"></a>

* Absturz bei Verwendung der Schaltfläche "-Taste" von VR-Controllern Holographic Remoting unterstützt Controller nicht vollständig. nur die Schaltfläche "Abbrechen" und die Windows-Schaltfläche funktionieren, wenn Sie mit hololens 2 gekoppelt sind.

## <a name="version-209-september-19-2019"></a>Version 2.0.9 (19. September 2019) <a name="v2.0.9"></a>

* Unterstützung für [spatialanchorexporter](/uwp/api/windows.perception.spatial.spatialanchorexporter) hinzugefügt
* Neue Schnittstelle ```IPlayerContext2``` (implementiert von) wurde hinzugefügt, ```PlayerContext``` die die folgenden Member bereitstellt:
  - [Blitremoteframetimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  -Eigenschaft.
* Hinzugefügter ```Failed_RemoteFrameTooOld``` Wert zu ```BlitResult```
* Verbesserungen der Stabilität und Zuverlässigkeit

## <a name="version-208-august-20-2019"></a>Version 2.0.8 (20. August 2019) <a name="v2.0.8"></a>

* Absturz beim Aufrufen von [holographiccamerderingparameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) mit einem [IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as-Parameter korrigiert.
* Verbesserungen der Stabilität und Zuverlässigkeit

## <a name="version-207-july-26-2019"></a>Version 2.0.7 (26. Juli 2019) <a name="v2.0.7"></a>

* Erstes öffentliches Release von Holographic Remoting für hololens 2.

## <a name="see-also"></a>Siehe auch

* [Schreiben einer Holographic Remoting-Remote-app mit Windows Mixed Reality-APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mithilfe von openxr-APIs](holographic-remoting-create-remote-openxr.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)