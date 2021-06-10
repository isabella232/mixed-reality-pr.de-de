---
title: Erste Schritte mit MRTK und XR SDK
description: Landing Page für MRTK mit XR SDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, XRSDK, XR SDK
ms.openlocfilehash: d3ff4306205cc6548bc5617d727f32a780855439
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647210"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Erste Schritte mit MRTK und XR SDK

Das XR SDK ist die [neue XR-Pipeline von Unity in Unity 2019.3 und darüber hinaus.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) In Unity 2019 bietet es eine Alternative zur vorhandenen XR-Pipeline. In Unity 2020 wird es die einzige XR-Pipeline in Unity.

## <a name="prerequisites"></a>Voraussetzungen

Um mit dem Mixed Reality Toolkit zu beginnen, führen Sie [die angegebenen Schritte](../install-the-tools.md#importing-the-mixed-reality-toolkit) aus, um einem Projekt MRTK hinzuzufügen.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Konfigurieren von Unity für die XR SDK-Pipeline

Die XR SDK-Pipeline unterstützt derzeit drei Plattformen: Windows Mixed Reality, Oculus und OpenXR. In den folgenden Abschnitten werden die Schritte beschrieben, die zum Konfigurieren des XR SDK für jede Plattform erforderlich sind.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Wechseln Sie zu **Unitys Paket-Manager,** und installieren Sie das Windows XR-Plug-In-Paket, das Unterstützung für Windows Mixed Reality im XR SDK hinzufügt. Dadurch werden auch einige Abhängigkeitspakete abgerufen. 

1. Stellen Sie sicher, dass alle folgenden erfolgreich installiert wurden:
   * XR-Plug-In-Verwaltung
   * Windows XR-Plug-In
   * XR Legacy Input Helpers

2. Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).
3. Klicken Sie im Fenster Projekteinstellungen auf die Registerkarte XR-Plug-In-Verwaltung.
4. Wechseln Sie zu den Universelle Windows-Plattform-Einstellungen, und stellen Sie sicher, dass Windows Mixed Reality unter Plug-In-Anbieter aktiviert ist.
5. Stellen Sie sicher, dass XR beim Start initialisieren aktiviert ist.
6. (**_Erforderlich für HoloLens-Remoting im Editor, andernfalls optional)_** Wechseln Sie zu den eigenständigen Einstellungen, und stellen Sie sicher, dass Windows Mixed Reality unter Plug-In-Anbieter aktiviert ist. Stellen Sie außerdem sicher, dass XR beim Start initialisieren aktiviert ist.

![XR-Plug-In-Verwaltung mit ausgewählter Registerkarte "Eigenständig"](images/xr-management-img-02.png)

7. (**_Optional)_** Klicken Sie unter XR-Plug-In-Verwaltung auf die Registerkarte Windows Mixed Reality, und erstellen Sie ein benutzerdefiniertes Einstellungsprofil, um die Standardwerte zu ändern. Wenn die Liste der Einstellungen bereits vorhanden ist, muss kein Profil erstellt werden.

![XR-Plug-In-Verwaltung mit ausgewählter Registerkarte "Windows"](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Folgen Sie dem Leitfaden Konfigurieren von [Oculus Quest in MRTK mithilfe der XR SDK-Pipeline](../supported-devices/oculus-quest-mrtk.md) bis zum Ende. In diesem Leitfaden werden die Schritte beschrieben, die zum Konfigurieren von Unity und MRTK für die Verwendung der XR SDK-Pipeline für Oculus Quest erforderlich sind.

### <a name="openxr-preview"></a>OpenXR (Vorschau)

> [!IMPORTANT]
> OpenXR in Unity wird nur unter Unity 2020.2 und höher unterstützt.
>
> Derzeit werden nur x64- und ARM64-Builds unterstützt.

1. Befolgen Sie den Leitfaden [Verwenden des Mixed Reality OpenXR-Plug-Ins für Unity,](/windows/mixed-reality/develop/unity/openxr-getting-started) einschließlich der Schritte zum Konfigurieren der XR-Plug-In-Verwaltung und -Optimierung, um das OpenXR-Plug-In in Ihrem Projekt zu installieren. Stellen Sie sicher, dass Folgendes erfolgreich installiert wurde:
   1. XR-Plug-In-Verwaltung
   1. OpenXR-Plug-In
   1. Mixed Reality OpenXR-Plug-In
1. Wechseln Sie zu > Projekteinstellungen bearbeiten.
1. Klicken Sie im Fenster Projekteinstellungen auf die Registerkarte XR-Plug-In-Verwaltung.
1. Stellen Sie sicher, dass XR beim Start initialisieren aktiviert ist.
1. (**_Optional)_** Wenn Sie HoloLens 2 als Ziel verwenden, stellen Sie sicher, dass Sie sich auf der UWP-Plattform befindet, und wählen Sie Microsoft HoloLens Featuresatz aus.

![Plug-In-Verwaltung Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Wenn Sie über ein bereits vorhandenes Projekt verfügen, das MRTK von UPM verwendet, stellen Sie sicher, dass sich die folgende Zeile in der **dateilink.xml** befindet, die sich im Ordner MixedRealityToolkit.Generated befindet.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Für die erste Version von MRTK und OpenXR werden nur die HoloLens 2 artikulierten Hände und Windows Mixed Reality Motion-Controller nativ unterstützt. Unterstützung für zusätzliche Hardware wird in zukünftigen Releases hinzugefügt.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Konfigurieren des MRTK für die XR SDK-Pipeline
::: moniker range=">= mrtkunity-2021-05" 
Wenn Sie OpenXR verwenden, wählen Sie "DefaultOpenXRConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vorzunehmen.

Wenn Sie andere XR-Runtimes in der Konfiguration der XR-Plug-In-Verwaltung wie Windows Mixed Reality oder Oculus verwenden, wählen Sie "DefaultXRSDKConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vorzunehmen.

Diese Profile werden bei Bedarf mit den richtigen Systemen und Anbietern eingerichtet. Weitere Informationen zur Profil- und Beispielunterstützung mit dem XR SDK finden Sie in der Dokumentation zu [Profilen.](../features/profiles/profiles.md#xr-sdk)

Um ein vorhandenes Profil zum XR SDK zu migrieren, sollten die folgenden Dienste und Datenanbieter hinzugefügt werden. Die neuen Datenanbieter werden auf der Registerkarte XR SDK angezeigt.

![Registerkarte "XR SDK"](../features/images/xrsdk/XrsdkTabView.png)

### <a name="camera"></a>Kamera

Fügen Sie die folgenden Datenanbieter hinzu: 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**und**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![XR SDK-Kameraeinstellungen](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Eingabe

Fügen Sie die folgenden Datenanbieter hinzu: 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![OpenXR-Eingabeeinstellungen](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![XR SDK-Eingabeeinstellungen](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Grenze

Fügen Sie die folgenden Datenanbieter hinzu: 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK-Begrenzungseinstellungen](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Räumliche Wahrnehmung

Fügen Sie die folgenden Datenanbieter hinzu: 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| In Bearbeitung | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Einstellungen für räumliche Wahrnehmung des XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Controllerzuordnungen

Wenn Sie benutzerdefinierte Controllerzuordnungsprofile verwenden, öffnen Sie eines dieser Profile, und führen Sie das Menüelement Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles aus, um sicherzustellen, dass die neuen XR SDK-Controllertypen definiert sind.

## <a name="see-also"></a>Siehe auch

* [Erste Schritte mit der AR-Entwicklung in Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Erste Schritte mit der VR-Entwicklung in Unity](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Wenn Sie OpenXR verwenden, wählen Sie "DefaultOpenXRConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vorzunehmen.

Wenn Sie andere XR-Runtimes in der Konfiguration der XR-Plug-In-Verwaltung wie Windows Mixed Reality oder Oculus verwenden, wählen Sie "DefaultXRSDKConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vorzunehmen.

Diese Profile werden bei Bedarf mit den richtigen Systemen und Anbietern eingerichtet. Weitere Informationen zur Profil- und Beispielunterstützung mit dem XR SDK finden Sie in der Dokumentation zu [Profilen.](../features/profiles/profiles.md#xr-sdk)

Um ein vorhandenes Profil zum XR SDK zu migrieren, sollten die folgenden Dienste und Datenanbieter aktualisiert werden:

### <a name="camera"></a>Kamera

Von [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Legacykameraeinstellungen](../features/images/xrsdk/CameraSystemLegacy.png)

zu

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**und**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![XR SDK-Kameraeinstellungen](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Eingabe

Von [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Legacyeingabeeinstellungen](../features/images/xrsdk/InputSystemWMRLegacy.png)

zu

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![OpenXR-Eingabeeinstellungen](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![XR SDK-Eingabeeinstellungen](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Grenze

Von [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Legacy-Begrenzungseinstellungen](../features/images/xrsdk/BoundarySystemLegacy.png)

zu

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK-Begrenzungseinstellungen](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Räumliche Wahrnehmung

Von [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Legacyeinstellungen für räumliche Wahrnehmung](../features/images/xrsdk/SpatialAwarenessLegacy.png)

zu

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| In Bearbeitung | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Einstellungen für räumliche Wahrnehmung im XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Controllerzuordnungen

Wenn Sie benutzerdefinierte Controllerzuordnungsprofile verwenden, öffnen Sie eines davon, und führen Sie das Menüelement Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles aus, um sicherzustellen, dass die neuen XR SDK-Controllertypen definiert sind.

## <a name="see-also"></a>Siehe auch

* [Erste Schritte mit der AR-Entwicklung in Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Erste Schritte mit der VR-Entwicklung in Unity](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end