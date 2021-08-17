---
title: Erste Schritte mit MRTK und XR SDK
description: Landing Page für MRTK mit XR SDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, XRSDK, XR SDK
ms.openlocfilehash: 681352ff854598ab34bd9521b46ae9f4e6f42f02
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905753"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Erste Schritte mit MRTK und XR SDK

Das XR SDK ist die neue [XR-Pipeline von Unity in Unity 2019.3 und darüber hinaus.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) In Unity 2019 bietet es eine Alternative zur vorhandenen XR-Pipeline. In Unity 2020 ist dies die einzige XR-Pipeline in Unity.

## <a name="prerequisites"></a>Voraussetzungen

Um mit dem Mixed Reality Toolkit zu beginnen, führen Sie [die angegebenen](/windows/mixed-reality/develop/install-the-tools#importing-the-mixed-reality-toolkit) Schritte aus, um MRTK zu einem Projekt hinzuzufügen.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Konfigurieren von Unity für die XR SDK-Pipeline

Die XR SDK-Pipeline unterstützt derzeit drei Plattformen: Windows Mixed Reality, Oculus und OpenXR. In den folgenden Abschnitten werden die Schritte beschrieben, die zum Konfigurieren des XR SDK für jede Plattform erforderlich sind.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Wechseln Sie zum **Unity-Paket-Manager,** und installieren Sie das XR-Plug Windows-Plug-In-Paket, das Unterstützung für Windows Mixed Reality XR SDK hinzufügt. Dadurch werden auch einige Abhängigkeitspakete heruntergefahren.

1. Stellen Sie sicher, dass alle folgenden Erfolgreich installiert wurden:
   * XR-Plug-In-Verwaltung
   * Windows XR-Plug-In
   * XR-Legacy-Eingabehilfen

2. Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).
3. Klicken Sie auf die Registerkarte XR-Plug-In-Verwaltung im Project Einstellungen Fenster.
4. Wechseln Sie zu den Einstellungen Windows Universelle Plattform, und stellen Sie sicher, Windows Mixed Reality Unter Plug-In-Anbieter die Einstellung "Plug-In-Anbieter" überprüft ist.
5. Stellen Sie sicher, dass XR beim Start initialisieren überprüft ist.
6. (**_Erforderlich für im Editor HoloLens Remoting, andernfalls optional_**) Wechseln Sie zu den eigenständigen Einstellungen, und vergewissern Windows Mixed Reality unter Plug-In-Anbieter. Stellen Sie außerdem sicher, dass XR beim Start initialisieren überprüft ist.

    ![XR-Plug-In-Verwaltung mit ausgewählter Registerkarte "Eigenständig"](images/xr-management-img-02.png)

7. (**_Optional_**) Klicken Sie unter Windows Mixed Reality XR Plug-In Management (XR-Plug-In-Verwaltung) auf die Registerkarte Windows Mixed Reality, und erstellen Sie ein benutzerdefiniertes Einstellungsprofil, um die Standardwerte zu ändern. Wenn die Liste der Einstellungen bereits vorhanden ist, muss kein Profil erstellt werden.

    ![XR-Plug-In-Windows registerkarte ausgewählt](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Befolgen Sie [den Leitfaden Konfigurieren von Oculus Quest in MRTK mithilfe der XR SDK-Pipeline](../supported-devices/oculus-quest-mrtk.md) bis zum Ende. In diesem Leitfaden werden die Schritte beschrieben, die zum Konfigurieren von Unity und MRTK für die Verwendung der XR SDK-Pipeline für Oculus Quest erforderlich sind.

### <a name="openxr"></a>OpenXR

> [!IMPORTANT]
> OpenXR in Unity wird nur unter Unity 2020.2 und höher unterstützt.
> Außerdem werden nur x64-, ARM- und ARM64-Builds unterstützt.

1. Befolgen Sie den Leitfaden Verwenden des [Mixed Reality OpenXR-Plug-Ins](/windows/mixed-reality/develop/unity/openxr-getting-started) für Unity, einschließlich der Schritte zum Konfigurieren der XR-Plug-In-Verwaltung und -Optimierung zum Installieren des OpenXR-Plug-Ins in Ihrem Projekt. Stellen Sie sicher, dass Folgendes erfolgreich installiert wurde:
   1. XR-Plug-In-Verwaltung
   1. OpenXR-Plug-In
   1. Mixed Reality OpenXR-Plug-In
1. Wechseln Sie zu Bearbeiten > Project Einstellungen.
1. Klicken Sie auf die Registerkarte XR-Plug-In-Verwaltung im Project Einstellungen Fenster.
1. Stellen Sie sicher, dass XR beim Start initialisieren überprüft ist.
1. (**_Optional_**) Wenn Sie HoloLens 2 auswählen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform auf dem Featuresatz Microsoft HoloLens.

![Plug-In-Verwaltung: OpenXR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Wenn Sie über ein bereits vorhandenes Projekt verfügen, das MRTK aus UPM verwendet, stellen Sie sicher, dass sich die folgende Zeile in der **link.xml-Datei** befindet, die sich im Ordner MixedRealityToolkit.Generated befindet.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Bei der ersten Veröffentlichung von MRTK und OpenXR werden nur die HoloLens 2 und Windows Mixed Reality Bewegungscontroller nativ unterstützt. Unterstützung für zusätzliche Hardware wird in zukünftigen Releases hinzugefügt.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Konfigurieren des MRTK für die XR SDK-Pipeline

::: moniker range=">= mrtkunity-2021-05"
Verwenden Sie eines der MRTK-Standardprofile, die alle über die XR-Pipelines von Unity konfiguriert sind. Die vorherigen "DefaultOpenXRConfigurationProfile" und "DefaultXRSDKConfigurationProfile" sind jetzt als veraltet gekennzeichnet.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Wenn Sie OpenXR verwenden, wählen Sie "DefaultOpenXRConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vornehmen zu können.

Wenn Sie andere XR-Runtimes in der Konfiguration der XR-Plug-In-Verwaltung wie Windows Mixed Reality oder Oculus verwenden, wählen Sie "DefaultXRSDKConfigurationProfile" als aktives Profil aus, oder klonen Sie es, um Anpassungen vornehmen zu können.

Diese Profile werden bei Bedarf mit den richtigen Systemen und Anbietern eingerichtet. Weitere [Informationen zur Profil-](../features/profiles/profiles.md#xr-sdk) und Beispielunterstützung mit dem XR SDK finden Sie in der Dokumentation zu Profilen.
::: moniker-end

Um ein vorhandenes Profil zum XR SDK zu migrieren, sollten die folgenden Dienste und Datenanbieter aktualisiert werden.
::: moniker range=">= mrtkunity-2021-05"
Sie können die neuen Datenanbieter auf der Registerkarte XR SDK in Unity 2019 oder in der Haupt-/Nur-Ansicht in Unity 2020 oder darüber anzeigen, wo legacy XR nicht vorhanden ist.

![Registerkarte "XR SDK"](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a>Kamera

::: moniker range=">= mrtkunity-2021-05"
Fügen Sie die folgenden Datenanbieter hinzu:
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Von [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Legacykameraeinstellungen](../features/images/xrsdk/CameraSystemLegacy.png)

zu
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| OpenXR-Plug-In | Windows XR-Plug-In |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| OpenXR-Plug-In | Windows XR-Plug-In |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![XR SDK-Kameraeinstellungen](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Eingabe

::: moniker range=">= mrtkunity-2021-05"
Fügen Sie die folgenden Datenanbieter hinzu:
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Von [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Legacyeingabeeinstellungen](../features/images/xrsdk/InputSystemWMRLegacy.png)

zu
::: moniker-end

| OpenXR-Plug-In | Windows XR-Plug-In |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![OpenXR-Eingabeeinstellungen](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![XR SDK-Eingabeeinstellungen](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Grenze

::: moniker range=">= mrtkunity-2021-05"
Fügen Sie die folgenden Datenanbieter hinzu:
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Von [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Legacy-Begrenzungseinstellungen](../features/images/xrsdk/BoundarySystemLegacy.png)

zu
::: moniker-end

| OpenXR-Plug-In | Windows XR-Plug-In |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK-Begrenzungseinstellungen](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Räumliche Wahrnehmung

::: moniker range=">= mrtkunity-2021-05"
Fügen Sie die folgenden Datenanbieter hinzu:
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Von [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Legacyeinstellungen für räumliche Wahrnehmung](../features/images/xrsdk/SpatialAwarenessLegacy.png)

zu
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| OpenXR-Plug-In | Windows XR-Plug-In |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (für UWP) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (für UWP) |
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (für Nicht-UWP) | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| OpenXR-Plug-In | Windows XR-Plug-In |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![Einstellungen für räumliche Wahrnehmung im XR SDK](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Controllerzuordnungen

Wenn Sie benutzerdefinierte Controllerzuordnungsprofile verwenden, öffnen Sie eines davon, und führen Sie das Menüelement Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles aus, um sicherzustellen, dass die neuen XR SDK-Controllertypen definiert sind.

## <a name="see-also"></a>Siehe auch

* [Erste Schritte mit der AR-Entwicklung in Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Erste Schritte mit der VR-Entwicklung in Unity](https://docs.unity3d.com/Manual/VROverview.html)