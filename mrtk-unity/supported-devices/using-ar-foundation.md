---
title: UsingARFoundation
description: Dokumentation zur Verwendung von ARFoundation in Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, AR Core, AR Kit
ms.openlocfilehash: d96c5cab2439b581c0de9d59a1a349abccf34fb5
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852366"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>Konfigurieren des MRTK für iOS und Android [Experimentell]

## <a name="install-required-packages"></a>Installieren erforderlicher Pakete

1. Laden Sie das **Paket Microsoft.MixedReality.Toolkit.Unity.Foundation** von [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) oder dem Unity-Projekt herunter, und [importieren Sie es Paket-Manager](../configuration/usingupm.md)

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
    | ARCore XR-Plug-In <br/> Version: 2.1.11 | ARKit XR-Plug-In <br/> Version: 2.1.9 |

    **Unity 2020.1.x (derzeit nicht formal unterstützt, nur zu Informationszwecken enthalten)**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Version: 3.1.3 |  AR Foundation  <br/> Version: 3.1.3 |
    | ARCore XR-Plug-In <br/> Version: 3.1.4 | ARKit XR-Plug-In <br/> Version: 3.1.3 |

1. Aktualisieren Sie die VON UNITYAR definierten MRTK-Skripts, indem Sie das Menüelement **aufrufen: Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**

## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Aktivieren des Unity AR-Kameraeinstellungsanbieters

Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus. Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../features/images/MRTK_ConfiguredHierarchy.png)

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

    Wenn Sie die Plattform wechseln, sollte das MRTK-Projektkonfigurationsfenster mit Einstellungen für die ausgewählte Plattform angezeigt werden.  Klicken Sie auf Übernehmen, um plattformspezifische Einstellungen zu aktivieren.

    iOS-Projektkonfiguratoreinstellungen

    ![iOS-Projektkonfigurator](../features/images/camera-system/MRTKProjectConfigurator.png)

1. Nach dem Wechseln der Plattform für Android sind keine weiteren Schritte erforderlich.

1. Wenn die Plattform iOS ist, deaktivieren Sie > Projekteinstellungen bearbeiten > Player > Andere Einstellungen, und **deaktivieren Sie** unter dem Header Optimierung die Option Strip Engine Code (Engine-Code löschen).

    ![iOS-Einstellungen](../features/images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > Das Deaktivieren von Strip Engine Code ist die kurzfristige Lösung für einen Fehler in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).  Wir arbeiten an einer langfristigen Lösung.

1. Erstellen und Ausführen der Szene

## <a name="see-also"></a>Siehe auch

- [Unity AR-Kameraeinstellungen](../features/camera-system/unity-ar-camera-settings.md)
