---
title: Problembehandlung und Einschränkungen bei Holographic Remoting
description: Hier finden Sie Ressourcen zur Problembehandlung und Anweisungen für das Holographic Remoting-Feature auf HoloLens 2 Geräten.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, holografisches Remoting, Remoterendering, Netzwerkrendering, HoloLens, Remote hologramme, Problembehandlung, Hilfe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: fa984e89fb6eb770917d9a1d62ce7c1007d45fab7fbcb2723f9642ac81814054
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223570"
---
# <a name="holographic-remoting-troubleshooting"></a>Problembehandlung bei Holographic Remoting

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic Remoting HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Spectre-entschärften Bibliotheken nicht gefunden.

Für Holographic Remoting-Beispiel-Apps ist die Spectre-Entschärfung (/Qspectre) in der Releasekonfiguration aktiviert.

Wenn sie erhalten, dass *vccorlib.lib* nicht geöffnet werden kann, stellen Sie sicher, dass Ihre Visual Studio-Workload die spectre-entschärften [Bibliotheken enthält.](/cpp/build/reference/qspectre)

## <a name="speech"></a>Spracheingabe/-ausgabe

Der Holographic Remoting Player unterstützt eine Diagnoseüberlagerung, die aktiviert werden kann, indem er sagt ```Enable Diagnostics``` und deaktiviert, indem er ```Disable Diagnostics``` sagt. Wenn Sie Probleme mit diesen Sprachbefehlen haben, können Sie den Holographic Remoting-Player auch über einen Webbrowser starten, der ```ms-holographic-remoting:?stats``` als URL verwendet.

## <a name="h265-video-codec-not-available"></a>H265-Videocodec nicht verfügbar

Installieren Sie [HEVC-Videoerweiterungen,](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) wenn Sie den H265-Videocodec in Ihrer Remote-App verwenden. Wenn Probleme auftreten, bei denen der Codec installiert ist, aber nicht verwendet werden kann, lesen Sie den Leitfaden [zur Problembehandlung.](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available)

## <a name="limitations"></a>Einschränkungen

Die folgenden APIs werden derzeit **nicht** unterstützt, wenn Holographic Remoting für HoloLens 2 wird ein Fehler ausgegeben, sofern ```ERROR_NOT_SUPPORTED``` nicht anders angegeben:

[Windows.Graphics.Holographic](/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Unterstützt ab Version [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Bei früheren Versionen wird immer ein Fehler ausgegeben.
* [HolographicCamera.IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - In früheren Versionen ist kein Fehler möglich, aber die Größe des Renderziels wird nicht geändert.
* [HolographicCameraPose.OverrideProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Doe.
  - Unterstützt ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - Beim Abfragen von HolographicViewConfigurationKind.PhotoVideoCamera wird immer ```nullptr``` zurückgegeben.
  - Unterstützt ab Version [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Bei früheren Versionen wird immer ein Fehler ausgegeben.
* [HolographicSpace.CreateFramePresentationMonitor](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay.GetDefault](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Wird einen Fehler melden, wenn aufgerufen wird, bevor eine Verbindung hergestellt wurde.


[Windows.Perception.Spatial](/uwp/api/windows.perception.spatial)

* [SpatialLocation.AbsoluteAngularAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation.AbsoluteAngularVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation.AbsoluteLinearAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation.AbsoluteLinearVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference.Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - Bei früheren Versionen wird immer ```nullptr``` zurückgeben.
* [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [SpatialAnchor.RemovedByUser](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Wird ab Version [2.0.9 unterstützt.](holographic-remoting-version-history.md#v2.0.9) 
  - Bei früheren Versionen wird immer ```nullptr``` zurückgeben. 
* [SpatialAnchorExporter.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Wird ab Version [2.0.9 unterstützt.](holographic-remoting-version-history.md#v2.0.9) 
  - In früheren Versionen wurde der asynchrone Vorgang immer mit ```SpatialPerceptionAccessStatus.DeniedBySystem``` abgeschlossen.
* [SpatialAnchorTransferManager.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - Der asynchrone Vorgang wird immer mit ```SpatialPerceptionAccessStatus.DeniedBySystem``` abgeschlossen.
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - Der asynchrone Vorgang wird immer mit ```false``` abgeschlossen.
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - Der asynchrone Vorgang wird immer mit ```nullptr``` abgeschlossen.

[Windows.UI.Input.Spatial](/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource.Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Weitere Informationen
* [Holographic Remoting-Versionsverlauf](holographic-remoting-version-history.md)
* [Schreiben einer Holographic Remoting-Remote-App mit Windows Mixed Reality-APIs](holographic-remoting-create-remote-wmr.md)
* [Schreiben einer Holographic Remoting-Remote-App mit OpenXR-APIs](holographic-remoting-create-remote-openxr.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Holographic Remoting-Software – Lizenzbedingungen](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)