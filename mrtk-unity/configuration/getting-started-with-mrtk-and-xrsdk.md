---
title: Erste Schritte mit MRTK und XRSDK
description: Landing Page für MRTK mit XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, XRSDK,
ms.openlocfilehash: ef6d8c9205a9d801e8cb0ec2690d77b74c72b5fb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143522"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Erste Schritte mit MRTK und XR SDK

Das XR SDK ist die neue [XR-Pipeline von Unity in Unity 2019.3 und darüber hinaus.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) In Unity 2019 bietet es eine Alternative zur vorhandenen XR-Pipeline. In Unity 2020 wird es die einzige XR-Pipeline in Unity.

## <a name="prerequisites"></a>Voraussetzungen

Um mit dem Mixed Reality Toolkit zu beginnen, führen Sie [die angegebenen](../install-the-tools.md#importing-the-mixed-reality-toolkit) Schritte aus, um MRTK zu einem Projekt hinzuzufügen.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Konfigurieren von Unity für die XR SDK-Pipeline

Die XR SDK-Pipeline unterstützt derzeit drei Plattformen: Windows Mixed Reality, Oculus und OpenXR. In den folgenden Abschnitten werden die Schritte beschrieben, die zum Konfigurieren des XR SDK für jede Plattform erforderlich sind.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Wechseln Sie zum **Unity-Paket-Manager,** und installieren Sie das Windows XR-Plug-In-Paket, das Unterstützung für Windows Mixed Reality XR SDK hinzufügt. Dadurch werden auch einige Abhängigkeitspakete heruntergefahren. 

1. Stellen Sie sicher, dass die folgenden Installationen erfolgreich sind:
   * XR-Plug-In-Verwaltung
   * Windows XR-Plug-In
   * XR-Legacy-Eingabehilfen

2. Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).
3. Klicken Sie im Fenster Projekteinstellungen auf die Registerkarte XR-Plug-In-Verwaltung.
4. Wechseln Sie zu den Universelle Windows-Plattform, und vergewissern Sie sich, Windows Mixed Reality Unter Plug-In-Anbieter die Einstellung "Plug-In-Anbieter" (Plug-In-Anbieter) überprüft ist.
5. Stellen Sie sicher, dass XR beim Start initialisieren überprüft ist.
6. (**_Erforderlich für HoloLens-Remoting im Editor, andernfalls optional)_** Wechseln Sie zu den eigenständigen Einstellungen, und stellen Sie sicher, dass Windows Mixed Reality unter Plug-In-Anbieter aktiviert ist. Stellen Sie außerdem sicher, dass XR beim Start initialisieren aktiviert ist.

![XR-Plug-In-Verwaltung mit ausgewählter Registerkarte "Eigenständig"](images/xr-management-img-02.png)

7. (**_Optional_**) Klicken Sie auf die Registerkarte Windows Mixed Reality unter XR-Plug-In-Verwaltung, und erstellen Sie ein benutzerdefiniertes Einstellungsprofil, um die Standardwerte zu ändern. Wenn die Liste der Einstellungen bereits vorhanden ist, muss kein Profil erstellt werden.

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
1. Wechseln Sie zu Bearbeiten > Projekteinstellungen.
1. Klicken Sie im Fenster Projekteinstellungen auf die Registerkarte XR-Plug-In-Verwaltung.
1. Stellen Sie sicher, dass XR beim Start initialisieren aktiviert ist.
1. (**_Optional_**) Wenn Sie HoloLens 2 auswählen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform auf dem Featuresatz Microsoft HoloLens sind.

![Plug-In-Verwaltung Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Wenn Sie über ein bereits vorhandenes Projekt verfügen, das MRTK aus UPM verwendet, stellen Sie sicher, dass sich die folgende Zeile in der **link.xml-Datei** befindet, die sich im Ordner MixedRealityToolkit.Generated befindet.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Bei der ersten Veröffentlichung von MRTK und OpenXR werden nur die HoloLens 2 und Windows Mixed Reality Bewegungscontroller nativ unterstützt. Unterstützung für zusätzliche Hardware wird in zukünftigen Releases hinzugefügt.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Konfigurieren des MRTK für die XR SDK-Pipeline

Wenn Sie OpenXR verwenden, wählen Sie "DefaultOpenXRConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vornehmen zu können.

Wenn Sie andere XR-Runtimes in der Konfiguration der XR-Plug-In-Verwaltung wie Windows Mixed Reality oder Oculus verwenden, wählen Sie "DefaultXRSDKConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vornehmen zu können.

Diese Profile werden bei Bedarf mit den richtigen Systemen und Anbietern eingerichtet. Weitere [Informationen zur Profil-](../features/profiles/profiles.md#xr-sdk) und Beispielunterstützung mit dem XR SDK finden Sie in der Dokumentation zu Profilen.

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

## <a name="see-also"></a>Weitere Informationen

* [Erste Schritte mit der AR-Entwicklung in Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Erste Schritte mit der VR-Entwicklung in Unity](https://docs.unity3d.com/Manual/VROverview.html)