---
title: Gettingstartedwithmrtkandxrsdk
description: Landing Page für mrtk mit xrsdk
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, hololens, hololens 2, Mixed Reality, Development, mrtk, xrsdk,
ms.openlocfilehash: d5ab9bf51828c84759b72e87e1c41f885c7d6738
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300413"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Einführung in das mrtk-und XR SDK

Das XR SDK ist die [neue Pipeline Pipeline von Unity in Unity 2019,3 und](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)höher. In Unity 2019 bietet es eine Alternative zu der vorhandenen Pipeline Pipeline. In Unity 2020 wird es zur einzigen Pipeline Pipeline in Unity.

## <a name="prerequisites"></a>Voraussetzungen

Um mit dem Mixed Reality Toolkit zu beginnen, führen Sie [die angegebenen Schritte](../install-the-tools.md#importing-the-mixed-reality-toolkit) aus, um mrtk einem Projekt hinzuzufügen.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Konfigurieren von Unity für die XR SDK-Pipeline

Die XR SDK-Pipeline unterstützt derzeit drei Plattformen: Windows Mixed Reality, oculus und openxr. In den folgenden Abschnitten werden die erforderlichen Schritte zum Konfigurieren des XR SDK für jede Plattform behandelt.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Wechseln Sie in **den Paket-Manager von Unity** , und installieren Sie das Windows-XR-Plug-in-Paket, das die Unterstützung für Windows Mixed Reality auf dem Hierdurch werden auch einige Abhängigkeits Pakete abgerufen. 

1. Stellen Sie sicher, dass Folgendes installiert ist:
   * XR-Plug-in
   * Windows-XR-Plugin
   * XR-Legacy-Eingabe Hilfen

2. Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“).
3. Klicken Sie im Fenster "Projekteinstellungen" auf die Registerkarte "XR-Plug-in-Verwaltung".
4. Wechseln Sie zu den universelle Windows-Plattform Einstellungen, und vergewissern Sie sich, dass Windows Mixed Reality unter Plug-in-Anbieter aktiviert ist.
5. Vergewissern Sie sich, dass beim Start die Option XR initialisieren aktiviert ist.
6. (**_Erforderlich für in-Editor-hololens-Remoting, andernfalls optional_**) Wechseln Sie zu den eigenständigen Einstellungen, und stellen Sie sicher, dass Windows Mixed Reality unter Plug-in-Anbieter aktiviert ist Vergewissern Sie sich außerdem, dass beim Start die Option XR initialisieren aktiviert ist.

![Verwaltung von XR-Plug-ins mit ausgewählter Registerkarte](images/xr-management-img-02.png)

7. (**_Optional_**) Klicken Sie unter "XR Plug-in Management" auf die Registerkarte Windows Mixed Reality, und erstellen Sie ein benutzerdefiniertes Einstellungs Profil, um die Standardwerte zu Wenn die Liste der Einstellungen bereits vorhanden ist, muss kein Profil erstellt werden.

![XR-Plugin-Verwaltung mit ausgewählter Windows-Registerkarte](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Befolgen Sie die Anweisungen im Leitfaden zum [Konfigurieren von Oculus Quest in mrtk mithilfe des Pipelines](../features/cross-platform/oculus-quest-mrtk.md) für das XR-SDK. In diesem Leitfaden werden die Schritte beschrieben, die erforderlich sind, um Unity und mrtk für die Verwendung der XR SDK-Pipeline für die Oculus Quest zu konfigurieren.

### <a name="openxr-preview"></a>Openxr (Vorschau)

> [!IMPORTANT]
> Openxr in Unity wird nur in Unity 2020,2 und höher unterstützt.
>
> Derzeit werden nur x64-und ARM64-Builds unterstützt.

1. Befolgen Sie die Anweisungen unter [Verwenden des gemischten Reality openxr-Plug-Ins für Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , einschließlich der Schritte zum Konfigurieren der Verwaltung und Optimierung von XR-Plug-Ins für die Installation des openxr-Plug-Ins für Ihr Projekt Stellen Sie sicher, dass Folgendes erfolgreich installiert wurde:
   1. XR-Plug-in
   1. Openxr-Plugin
   1. Mixed Reality openxr-Plug-in
1. Wechseln Sie zu Edit > Project Settings.
1. Klicken Sie im Fenster "Projekteinstellungen" auf die Registerkarte "XR-Plug-in-Verwaltung".
1. Vergewissern Sie sich, dass beim Start die Option XR initialisieren aktiviert ist.
1. (**_Optional_**) Wenn Sie auf hololens 2 abzielen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform befinden, und wählen Sie "Microsoft hololens Feature

![Plug-in-Management öffnen XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Wenn Sie über ein bereits vorhandenes Projekt verfügen, das mrtk aus UPM verwendet, stellen Sie sicher, dass sich die folgende Zeile in der **link.xml** -Datei befindet, die sich im Ordner "mixedrealitytoolkit. generated" befindet.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Für die erste Version von mrtk und openxr werden nur die "hololens 2"-und Windows Mixed Reality-Bewegungs Controller nativ unterstützt. Unterstützung für zusätzliche Hardware wird in zukünftigen Versionen hinzugefügt.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Konfigurieren von mrtk für die XR SDK-Pipeline

Wenn Sie openxr verwenden, wählen Sie "defaultoperxrconfigurationprofile" als aktives Profil aus, oder Klonen Sie es, um Anpassungen vorzunehmen.

Wenn Sie andere XR-Laufzeiten in der Konfigurations Konfiguration des XR-Plug-Ins verwenden, wie z. b. Windows Mixed Reality oder Oculus, wählen Sie "defaultxrsdkconfigurationprofile" als aktives Profil aus, oder Klonen Sie es, um Anpassungen vorzunehmen.

Diese Profile werden bei Bedarf mit den richtigen Systemen und Anbietern eingerichtet. Weitere Informationen zur Profil-und Beispiel Unterstützung mit dem XR SDK finden Sie in der Dokumentation zu [Profilen](../features/profiles/profiles.md#xr-sdk) .

Um ein vorhandenes Profil zu dem XR SDK zu migrieren, sollten die folgenden Dienste und Datenanbieter aktualisiert werden:

### <a name="camera"></a>Kamera

Von [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Ältere Kameraeinstellungen](../features/images/xrsdk/CameraSystemLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**und**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![XR SDK-Kameraeinstellungen](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Eingabe

Von [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Ältere Eingabeeinstellungen](../features/images/xrsdk/InputSystemWMRLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__Openxr__:

![Openxr-Eingabeeinstellungen](../features/images/xrsdk/InputSystemOpenXR.png)

__Gemischte Windows-Realität__:

![XR SDK-Eingabeeinstellungen](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Grenze

Von [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Legacy Begrenzungs Einstellungen](../features/images/xrsdk/BoundarySystemLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK-Begrenzungs Einstellungen](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Räumliches Bewusstsein

Von [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Legacy Einstellungen für räumliche Informationen](../features/images/xrsdk/SpatialAwarenessLegacy.png)

in

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| In Bearbeitung | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Einstellungen für das XR SDK für räumliche Informationen](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Controller Zuordnungen

Wenn Sie benutzerdefinierte Controller zuordnungsprofile verwenden, öffnen Sie eine von Ihnen, und führen Sie den Menüeintrag Mixed Reality Toolkit-> Utilities-> Update-> Controller Mapping Profiles aus, um sicherzustellen, dass die neuen XR SDK-Controller Typen definiert sind.

## <a name="see-also"></a>Weitere Informationen

* [Ersten Einstieg in die Entwicklung von aren in Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Einstieg in die VR-Entwicklung in Unity](https://docs.unity3d.com/Manual/VROverview.html)