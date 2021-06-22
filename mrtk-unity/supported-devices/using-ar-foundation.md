---
title: Erstellen und Bereitstellen für Android und iOS über AR Foundation
description: Dokumentation zum Konfigurieren des MRTK für Android und iOS (ARFoundation) in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 352afbbc11c7cc6fcd2557395c5dd36d956f396d
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449739"
---
# <a name="building-and-deploying-to-android-and-ios-via-ar-foundation-experimental"></a>Erstellen und Bereitstellen für Android und iOS über AR Foundation [Experimentell]

## <a name="install-required-packages"></a>Installieren erforderlicher Pakete

1. Laden Sie das **Paket Microsoft.MixedReality.Toolkit.Unity.Foundation** von [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) oder dem Unity-Projekt herunter, und [importieren Sie es Paket-Manager](../configuration/usingupm.md)

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

1. Navigieren Sie im Inspektorbereich zum Abschnitt Kamerasystem, und erweitern Sie den Abschnitt **Kameraeinstellungsanbieter.**

    ![Erweitern von Einstellungsanbietern](../features/images/camera-system/ExpandProviders.png)

1. Klicken **Sie auf Kameraeinstellungsanbieter hinzufügen,** und erweitern Sie den neu hinzugefügten Eintrag **Neue Kameraeinstellungen.**

    ![Erweitern des neuen Einstellungsanbieters](../features/images/camera-system/ExpandNewProvider.png)

1. Auswählen des Unity AR-Kameraeinstellungsanbieters

    ![Auswählen des Unity AR-Einstellungsanbieters](../features/images/camera-system/SelectUnityArSettings.png)

    Weitere Informationen zum Konfigurieren des Unity AR-Kameraeinstellungsanbieters: [Unity AR-Kameraeinstellungsanbieter](../features/camera-system/unity-ar-camera-settings.md).

> [!NOTE]
> Diese Installation überprüft (wenn die Anwendung gestartet wird), ob sich die AR Foundation-Komponenten in der Szene befinden. Falls nicht, werden sie automatisch hinzugefügt, damit sie mit ARCore und ARKit funktionieren.
> Wenn Sie ein bestimmtes Verhalten festlegen müssen, sollten Sie die benötigten Komponenten selbst hinzufügen.
> Weitere Informationen zu AR Foundation-Komponenten und zur Installation finden Sie in dieser [Dokumentation.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)

## <a name="building-a-scene-for-android-and-ios-devices"></a>Erstellen einer Szene für Android- und iOS-Geräte

1. Stellen Sie sicher, dass Sie ihrer Szene den UnityAR-Kameraeinstellungsanbieter hinzugefügt haben.

1. Wechseln der Plattform zu Android oder iOS in den Unity-Buildeinstellungen

1. Stellen Sie sicher, dass der zugeordnete XR-Plug-In-Verwaltungsanbieter aktiviert ist.

    iOS-XR-Plug-In-Verwaltung:  ![ XR-Plug-In-Verwaltung iOS](../features/images/XRManagementiOS.png)

1. Erstellen und Ausführen der Szene

## <a name="see-also"></a>Siehe auch

- [Unity-AR-Kameraeinstellungen](../features/camera-system/unity-ar-camera-settings.md)
