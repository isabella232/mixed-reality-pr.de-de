---
title: Bereitstellen unter Android und iOS (AR Foundation) [Experimentell]
description: Dokumentation zum Konfigurieren des MRTK für Android und iOS (ARFoundation) in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: d127b9b39cbaa90f0c8c5a8a6ac7955f33404cbf
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281941"
---
# <a name="deploying-to-android-and-ios-ar-foundation-experimental"></a>Bereitstellen unter Android und iOS (AR Foundation) [Experimentell]

## <a name="install-required-packages"></a>Installieren erforderlicher Pakete

1. Laden Sie das **Paket Microsoft.MixedReality.Toolkit.Unity.Foundation** herunter, und importieren Sie es [aus](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) GitHub [unity Paket-Manager](../configuration/usingupm.md)

1. Installieren Sie im Unity Paket-Manager (UPM) die folgenden Pakete:

    **Unity 2018.4.x**

    | **Android** | **iOS** | Kommentare |
    | --- | --- | --- |
    | AR Foundation  <br/> Version: 1.5.0 – Preview 6 | AR Foundation  <br/> Version: 1.5.0 – Preview 6 | Für Unity 2018.4 ist dieses Paket als Vorschauversion enthalten. So zeigen Sie das Paket an: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | ARCore-XR-Plug-In <br/> Version: 2.1.2 | ARKit XR-Plug-In <br/> Version: 2.1.2 | |

    **Unity 2019.4.x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Version: 2.1.8 |  AR Foundation  <br/> Version: 2.1.8 |
    | ARCore-XR-Plug-In <br/> Version: 2.1.11 | ARKit XR-Plug-In <br/> Version: 2.1.9 |

    **Unity 2020.3.x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Version: 3.1.3 |  AR Foundation  <br/> Version: 4.0.12 |
    | ARCore-XR-Plug-In <br/> Version: 3.1.4 | ARKit XR-Plug-In <br/> Version: 4.1.7 |

1. Aktualisieren Sie die definitionen MRTK UnityAR-Skripts, indem Sie das Menüelement aufrufen: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**

    ![Skripterstellung aktualisieren definiert](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Aktivieren des Unity AR-Kameraeinstellungsanbieters

Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus. Die für andere Dienstregistrierungen erforderlichen Schritte können unterschiedlich sein.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![MRTK– Konfigurierte Szenenhierarchie](../features/images/MRTK_ConfiguredHierarchy.png)

1. Wählen **Sie Kopieren und anpassen aus,** um das MRTK-Profil zu klonen, um die benutzerdefinierte Konfiguration zu aktivieren.

    ![Klonen des MRTK-Profils](../features/images/camera-system/CloneProfileARFoundation.png)

1. Klicken **Sie neben** dem Kameraprofil auf Klonen.

    ![Klonen des MRTK-Kameraprofils](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. Navigieren Sie im Inspektorbereich zum Abschnitt Kamerasystem, und erweitern Sie den Abschnitt **Kamera Einstellungen Anbieter.**

    ![Erweitern von Einstellungsanbietern](../features/images/camera-system/ExpandProviders.png)

1. Klicken **Sie auf Kamera Einstellungen Anbieter hinzufügen,** und erweitern Sie den neu hinzugefügten Eintrag Neue **Kameraeinstellungen.**

    ![Erweitern des neuen Einstellungsanbieters](../features/images/camera-system/ExpandNewProvider.png)

1. Auswählen des Unity-AR-Kameraanbieters Einstellungen

    ![Auswählen des Unity AR-Einstellungsanbieters](../features/images/camera-system/SelectUnityArSettings.png)

    Weitere Informationen zum Konfigurieren des Unity AR-Kameraeinstellungsanbieters: [Unity AR-Kameraeinstellungsanbieter](../features/camera-system/unity-ar-camera-settings.md).

> [!NOTE]
> Diese Installation überprüft (wenn die Anwendung gestartet wird), ob sich die AR Foundation-Komponenten in der Szene befinden. Falls nicht, werden sie automatisch hinzugefügt, damit sie mit ARCore und ARKit funktionieren.
> Wenn Sie ein bestimmtes Verhalten festlegen müssen, sollten Sie die benötigten Komponenten selbst hinzufügen.
> Weitere Informationen zu AR Foundation-Komponenten und zur Installation finden Sie in dieser [Dokumentation.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)

## <a name="building-a-scene-for-android-and-ios-devices"></a>Erstellen einer Szene für Android- und iOS-Geräte

1. Stellen Sie sicher, dass Sie ihrer Szene Einstellungen UnityAR Camera-Anbieter hinzugefügt haben.

1. Wechseln Sie im Unity Build-Gerät zu Android oder iOS Einstellungen

1. Stellen Sie sicher, dass der zugeordnete XR-Plug-In-Verwaltungsanbieter aktiviert ist.

    iOS-XR-Plug-In-Verwaltung:  ![ XR-Plug-In-Verwaltung iOS](../features/images/XRManagementiOS.png)

1. Erstellen und Ausführen der Szene

## <a name="see-also"></a>Weitere Informationen

- [Unity AR Camera Einstellungen](../features/camera-system/unity-ar-camera-settings.md)
