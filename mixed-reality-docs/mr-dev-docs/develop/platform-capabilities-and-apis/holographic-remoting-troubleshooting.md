---
title: Problembehandlung und Einschränkungen für Holographic Remoting
description: Hier finden Sie Ressourcen zur Problembehandlung und Anweisungen für die Holographic Remoting-Funktion auf hololens 2-Geräten.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, Holographic Remoting, Remote Rendering, Netzwerk Rendering, hololens, Remote holograms, Problembehandlung, Hilfe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: ee1dce72af02374e930de4a1bdff94285c7a84ae
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006450"
---
# <a name="holographic-remoting-troubleshooting"></a>Problembehandlung bei Holographic Remoting

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Von Spectre abgeminderte Bibliotheken wurden nicht gefunden.

Für Holographic Remoting-Beispiel-Apps ist Spectre Entschärfung (/Qspectre) in der Releasekonfiguration aktiviert.

Wenn die Datei " *vccorlib. lib" nicht geöffnet werden kann* , sollten Sie sicherstellen, dass die Visual Studio-Arbeitsauslastung die von [Spectre abgeminderten Bibliotheken](https://aka.ms/Ofhn4c) enthält.

## <a name="speech"></a>Speech

Der Holographic Remoting Player unterstützt ein diagnoseoverlay, das durch das sagen von aktiviert ```Enable Diagnostics``` und deaktiviert werden kann ```Disable Diagnostics``` . Wenn Sie Probleme mit diesen Sprachbefehlen haben, können Sie den Holographic Remoting Player auch über einen Webbrowser starten, indem Sie ```ms-holographic-remoting:?stats``` als URL verwenden.

## <a name="h265-video-codec-not-available"></a>H265-Videocodec nicht verfügbar

Installieren Sie die [hevc-Video Erweiterungen](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) , wenn Sie den H265-Videocodec in Ihrer Remote-app verwenden. Wenn Sie Probleme haben, bei denen der Codec installiert ist, aber nicht verwendet werden kann, finden Sie im Handbuch zur [Problem](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) Behandlung Weitere Informationen.

## <a name="limitations"></a>Einschränkungen

Die folgenden APIs werden zurzeit **nicht** unterstützt, wenn Holographic Remoting für hololens 2 verwendet wird, und es wird ein Fehler ausgegeben, ```ERROR_NOT_SUPPORTED``` sofern nicht anders angegeben:

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Unterstützt ab Version [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Bei früheren Versionen wird immer ein Fehler ausgegeben.
* [HolographicCamera.IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - Bei früheren Versionen schlägt nicht fehl, aber die renderzielgröße wird nicht geändert.
* [Holographiccamerapose. override projectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [Holographiccamerapose. overrideviewport](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [Holographiccamerapose. override viewtransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [Holographiccamer-deringparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Episoden.
  - Unterstützt ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - Beim Abfragen von holographicviewconfigurationkind. photovideocamera wird immer ein zurückgegeben ```nullptr``` .
  - Unterstützt ab Version [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Bei früheren Versionen wird immer ein Fehler ausgegeben.
* [Holographicspace. kreateframepresentationmonitor](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [Holographicdisplay. GetDefault](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Meldet einen Fehler, wenn aufgerufen wird, bevor eine Verbindung hergestellt wurde.


[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [SpatialLocation. absoluteangularacceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. absoluteangularvelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. absolutelinearacceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. absolutelinearvelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [Spatialstageframeofreferenzierungs. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - Bei früheren Versionen wird immer zurückgegeben ```nullptr``` .
* [Spatialstageframeofreferenzierung. requestnewstageasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [Spatialanchor. removedbyuser](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - Bei früheren Versionen wird immer zurückgegeben ```nullptr``` . 
* [SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - In früheren Versionen wurde der Async-Vorgang immer mit abgeschlossen ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [Spatialanchortransfermanager. requestaccessasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - Der Async-Vorgang wird immer mit abgeschlossen ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [Spatialanchortransfermanager. tryexportanchorsasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - Der Async-Vorgang wird immer mit abgeschlossen ```false``` .
* [Spatialanchortransfermanager. tryimportanchorsasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - Der Async-Vorgang wird immer mit abgeschlossen ```nullptr``` .

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [Spatialinteraktionsource. Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Weitere Informationen
* [Holographic Remoting-Versionsverlauf](holographic-remoting-version-history.md)
* [Schreiben einer Holographic Remoting-Remote-app mit Windows Mixed Reality-APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mithilfe von openxr-APIs](holographic-remoting-create-remote-openxr.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
