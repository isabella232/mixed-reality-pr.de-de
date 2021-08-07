---
title: Bereitstellen in HoloLens und WMR-Headsets
description: Dokumentation zum Erstellen und Bereitstellen von Apps auf verschiedenen Geräten.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Visual Studio
ms.openlocfilehash: 622c7ca4b9c527630b5677fe377d1d3108bdfe08c9dc616bfd4d3256b83b9ab0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209477"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a>Bereitstellen in HoloLens und WMR-Headsets

Es gibt zwei Möglichkeiten, anwendungen, die mit MRTK erstellt wurden, auf Ihrem Windows-Gerät bereitzustellen: die Universelle Windows-Plattform (UWP) und die eigenständige Plattform. Anwendungen, die für HoloLens 1 oder HoloLens 2 erstellt wurden, müssen UWP als Ziel verwenden, während Anwendungen, die für WMR-Headsets erstellt wurden, entweder UWP oder Eigenständig sein können.

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>Erstellen und Bereitstellen von MRTK für HoloLens 1, HoloLens 2 und WMR-Headsets (UWP)

Anweisungen zum Erstellen und Bereitstellen für **HoloLens 1** und **HoloLens 2** (UWP) finden Sie unter [Erstellen Ihrer Anwendung auf dem Gerät.](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device) Mit diesen Schritten können Sie auch auf **WMR-Headsets** bereitstellen.

> [!NOTE]
> Wenn Sie Ihre Anwendung auf Ihrem Gerät in Visual Studio bereitstellen, müssen Sie Visual Studio je nach Gerät etwas anders konfigurieren. Die Konfigurationen sind wie folgt:
>
>| Plattform | Konfiguration | Aufbau | Ziel |
|---|---|---|---|
| HoloLens 2 | Release oder Master | ARM64 | Sicherungsmedium |
| HoloLens 1 | Release oder Master | x86 | Sicherungsmedium |
| WMR-Headsets | Release oder Master | x64 | Lokaler Computer |

**Tipp:** Beim Erstellen für HoloLens 1, HoloLens 2 oder WMR wird empfohlen, dass die Buildeinstellungen "Ziel-SDK-Version" und "Mindestplattformversion" wie in der folgenden Abbildung aussehen:

![Fenster „Build“ (Erstellen)](../features/images/getting-started/BuildWindow.png)

Die anderen Einstellungen können unterschiedlich sein (z. b. Buildkonfiguration/Architektur/Buildtyp, und andere können in der Visual Studio-Projektmappe immer geändert werden).

Stellen Sie sicher, dass in der Dropdownliste „SDK-Zielversion“ die Option „10.0.18362.0“ enthalten ist. Sollte diese fehlen, muss [das neueste Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) installiert werden.

### <a name="unity-20192020-and-hololens"></a>Unity 2019/2020 und HoloLens

Wenn eine HoloLens-App als 2D-Panel auf dem Gerät angezeigt wird, stellen Sie sicher, dass die folgenden Einstellungen in Unity konfiguriert wurden, bevor Sie Ihre UWP-App bereitstellen:

Bei Verwendung der älteren integrierten XR-Unterstützung (nur Unity 2019):

1. Navigieren Sie zu „Bearbeiten > Projekteinstellungen, Player“.
1. Stellen Sie sicher, dass unter **XR-Einstellungen** auf der Registerkarte „UWP“ die Option **Virtuelle Realität unterstützt** aktiviert ist, und dass das **Windows Mixed Reality** SDK zu den SDKs hinzugefügt wurde.
1. Erstellen und Bereitstellen in Visual Studio

Bei Verwendung der OpenXR- oder Windows XR-Plug-Ins:

1. Befolgen Sie die Schritte unter [Erste Schritte mit XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md).
1. Stellen Sie sicher, dass das Konfigurationsprofil **DefaultXRSDKConfigurationProfile** ist.
1. Navigieren Sie zu **Bearbeiten > Projekteinstellungen, XR-Plug-In-Verwaltung**, und vergewissern Sie sich, dass **Windows Mixed Reality** aktiviert ist.
1. Erstellen und Bereitstellen in Visual Studio

>[!IMPORTANT]
> Wenn Sie Unity 2019.3.x verwenden, wählen Sie **ARM64** und nicht **ARM** als Buildarchitektur in Visual Studio aus. Mit den Unity-Standardeinstellungen in Unity 2019.3.x wird eine Unity-App nicht auf einer HoloLens bereitgestellt, wenn ARM aufgrund eines Unity-Fehlers ausgewählt ist.
>
> Wenn die ARM-Architektur erforderlich ist, navigieren Sie zu **Bearbeiten > Projekteinstellungen, Player**, und deaktivieren Sie im Menü **Weitere Einstellungen** die Option **Grafikaufträge**. Durch das Deaktivieren von **Grafikaufträge** kann die App mithilfe der ARM-Buildarchitektur für Unity 2019.3.x bereitgestellt werden, doch empfohlen wird ARM64.
>
> Dieses Problem wurde in Unity 2019.4 und Unity 2020.3 behoben.

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a>Erstellen und Bereitstellen von MRTK für WMR-Headsets (eigenständig)

Eigenständige Builds von MRTK können auf WMR-Headsets verwendet werden. Ein eigenständiger Build für ein WMR-Headset erfordert die folgenden zusätzlichen Schritte:

> [!NOTE]
> Das XR SDK von Unity unterstützt auch native WMR in eigenständigen Builds, erfordert aber kein SteamVR- oder WMR-Plug-In. Diese Schritte sind für die Legacy-XR von Unity erforderlich.

1. Installieren von [Steam](https://store.steampowered.com/about/).
1. Installieren von [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).
1. Installieren des [WMR-Plug-Ins](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).

### <a name="how-to-use-wmr-plugin"></a>Verwenden des WMR-Plug-Ins

1. Öffnen Sie Steam, und suchen Sie nach dem Windows Mixed Reality-Plug-In.
    - Stellen Sie sicher, dass SteamVR geschlossen ist, bevor Sie das WMR-Plug-In starten. Durch das Starten des WMR-Plug-Ins wird auch SteamVR gestartet.
    - Stellen Sie sicher, dass das WMR-Headset angeschlossen ist.

    ![WMR-Plug-In-Suche](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. Wählen Sie für das Windows Mixed Reality für SteamVR-Plug-In **Starten** aus.

    ![WMR-Plug-In](../features/images/build-deploy/WMR/WMRPlugin.png)

    - SteamVR und das WMR-Plug-In werden gestartet, und ein neues Fenster mit dem Nachverfolgungsstatus für das WMR-Headset wird angezeigt.
    - Weitere Informationen finden Sie in der [Dokumentation zu Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).

        ![Darstellung des WMR-Starts](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. Navigieren Sie in Unity bei geöffneter MRTK-Szene zu **Datei > Buildeinstellungen**.

1. Erstellen der Szene
    - Wählen Sie **Offene Szene hinzufügen** aus.
    - Stellen Sie sicher, dass die Plattform **Eigenständig** ist.
    - Wählen Sie **Build** aus.
    - Wählen Sie den Speicherort für den neuen Build im Datei-Explorer aus.

    ![Einstellungen für eigenständigen Build](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. Eine neue ausführbare Unity-Datei wird erstellt, um Ihre App zu starten. Wählen Sie die ausführbare Unity-Datei im Datei-Explorer aus.

    ![Unity-Datei-Explorer](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>Siehe auch

- [Android- und iOS-Unterstützung](using-ar-foundation.md)
- [Leap Motion-Unterstützung](leap-motion-mrtk.md)
- [Erkennen von Plattformfunktionen](detecting-platform-capabilities.md)
