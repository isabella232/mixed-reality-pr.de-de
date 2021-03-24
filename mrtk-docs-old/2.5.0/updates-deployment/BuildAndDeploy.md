---
title: BuildAndDeploy
description: Dokumentation zum Erstellen und Bereitstellen von Apps auf verschiedenen Geräten.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Visual Studio, Android, iOS
ms.openlocfilehash: cbf17cfd463ee375d285a36aef1705b4d911107f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687430"
---
# <a name="building-and-deploying-mrtk"></a>Erstellen und Bereitstellen von MRTK

Um eine App auf einem Gerät als eigenständige App (für HoloLens, Android, iOS usw.) auszuführen, muss der Schritt zum Erstellen und Bereitstellen im Unity-Projekt ausgeführt werden. Das Entwickeln und Bereitstellen einer App, die MRTK verwendet, ist wie das Entwickeln und Bereitstellen jeder anderen Unity-App. Es gibt keine MRTK-spezifischen Anweisungen. Im Folgenden finden Sie ausführliche Schritte zum Erstellen und Bereitstellen einer Unity-App für HoloLens.  Weitere Informationen zum Erstellen für andere Plattformen finden Sie unter [Veröffentlichen von Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a>Erstellen und Bereitstellen von MRTK für HoloLens 1 und HoloLens 2 (UWP)

Anweisungen zum Erstellen und Bereitstellen für HoloLens 1 und HoloLens 2 (UWP) finden Sie unter [Erstellen Ihrer Anwendung auf dem Gerät](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).

**Tipp:** Beim Erstellen für WMR, HoloLens 1 oder HoloLens 2 wird empfohlen, dass die Buildeinstellungen „SDK-Zielversion“ und „Minimale Plattformversion“ wie in der folgenden Abbildung aussehen:

![Fenster „Build“ (Erstellen)](../features/Images/getting_started/BuildWindow.png)

Die anderen Einstellungen können unterschiedlich sein (z. b. Buildkonfiguration/Architektur/Buildtyp, und andere können in der Visual Studio-Projektmappe immer geändert werden).

Stellen Sie sicher, dass in der Dropdownliste „SDK-Zielversion“ die Option „10.0.18362.0“ enthalten ist. Sollte diese fehlen, muss [das neueste Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) installiert werden.

### <a name="unity-20193-and-hololens"></a>Unity 2019.3 und HoloLens

Wenn eine HoloLens-App als 2D-Bereich auf dem Gerät angezeigt wird, stellen Sie sicher, dass die folgenden Einstellungen in Unity 2019.3.x konfiguriert wurden, bevor Sie Ihre UWP-App bereitstellen:

Bei Verwendung von Legacy-XR:

1. Navigieren Sie zu „Bearbeiten > Projekteinstellungen, Player“.
1. Stellen Sie sicher, dass unter **XR-Einstellungen** auf der Registerkarte „UWP“ die Option **Virtuelle Realität unterstützt** aktiviert ist, und dass das **Windows Mixed Reality** SDK zu den SDKs hinzugefügt wurde.
1. Erstellen und Bereitstellen in Visual Studio

Bei Verwendung des XR-Plug-Ins:

1. Befolgen Sie die Schritte unter [Erste Schritte mit XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md).
1. Stellen Sie sicher, dass das Konfigurationsprofil **DefaultXRSDKConfigurationProfile** ist.
1. Navigieren Sie zu **Bearbeiten > Projekteinstellungen, XR-Plug-In-Verwaltung**, und vergewissern Sie sich, dass **Windows Mixed Reality** aktiviert ist.
1. Erstellen und Bereitstellen in Visual Studio

>[!IMPORTANT]
> Wenn Sie Unity 2019.3.x verwenden, wählen Sie **ARM64** und nicht **ARM** als Buildarchitektur in Visual Studio aus. Mit den Unity-Standardeinstellungen in Unity 2019.3.x wird eine Unity-App nicht auf einer HoloLens bereitgestellt, wenn ARM aufgrund eines Unity-Fehlers ausgewählt ist. Dies kann mit der [Problemverfolgung von Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2) nachverfolgt werden.
>
> Wenn die ARM-Architektur erforderlich ist, navigieren Sie zu **Bearbeiten > Projekteinstellungen, Player**, und deaktivieren Sie im Menü **Weitere Einstellungen** die Option **Grafikaufträge**. Durch das Deaktivieren von **Grafikaufträge** kann die App mithilfe der ARM-Buildarchitektur für Unity 2019.3.x bereitgestellt werden, doch empfohlen wird ARM64.

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a>Entwickeln und Bereitstellen von MRTK für ein Windows Mixed Reality-Headset

Das Windows Mixed Reality-Headset (WMR) kann für universelle Windows-Plattform- (UWP) und eigenständige Builds verwendet werden.  Ein eigenständiger Build für ein WMR-Headset erfordert die folgenden zusätzlichen Schritte:

> [!NOTE]
> Das XR SDK von Unity unterstützt auch native WMR in eigenständigen Builds, erfordert aber kein SteamVR- oder WMR-Plug-In. Diese Schritte sind für die Legacy-XR von Unity erforderlich.

1. Installieren von [Steam](https://store.steampowered.com/about/).
1. Installieren von [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).
1. Installieren des [WMR-Plug-Ins](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).

### <a name="how-to-use-wmr-plugin"></a>Verwenden des WMR-Plug-Ins

1. Öffnen Sie Steam, und suchen Sie nach dem Windows Mixed Reality-Plug-In.
    - Stellen Sie sicher, dass SteamVR geschlossen ist, bevor Sie das WMR-Plug-In starten. Durch das Starten des WMR-Plug-Ins wird auch SteamVR gestartet.
    - Stellen Sie sicher, dass das WMR-Headset angeschlossen ist.

    ![WMR-Plug-In-Suche](../features/Images/BuildDeploy/WMR/SteamSearchWMRPlugin.png)

1. Wählen Sie für das Windows Mixed Reality für SteamVR-Plug-In **Starten** aus.

    ![WMR-Plug-In](../features/Images/BuildDeploy/WMR/WMRPlugin.png)

    - SteamVR und das WMR-Plug-In werden gestartet, und ein neues Fenster mit dem Nachverfolgungsstatus für das WMR-Headset wird angezeigt.
    - Weitere Informationen finden Sie in der [Dokumentation zu Windows Mixed Reality](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality).

        ![Darstellung des WMR-Starts](../features/Images/BuildDeploy/WMR/WMRPluginActive.png)

1. Navigieren Sie in Unity bei geöffneter MRTK-Szene zu **Datei > Buildeinstellungen**.

1. Erstellen der Szene
    - Wählen Sie **Offene Szene hinzufügen** aus.
    - Stellen Sie sicher, dass die Plattform **Eigenständig** ist.
    - Wählen Sie **Build** aus.
    - Wählen Sie den Speicherort für den neuen Build im Datei-Explorer aus.

    ![Einstellungen für eigenständigen Build](../features/Images/BuildDeploy/WMR/BuildSettingsStandaloneUnity.png)

1. Eine neue ausführbare Unity-Datei wird erstellt, um Ihre App zu starten. Wählen Sie die ausführbare Unity-Datei im Datei-Explorer aus.

    ![Unity-Datei-Explorer](../features/Images/BuildDeploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>Siehe auch

- [Android- und iOS-Unterstützung](../features/CrossPlatform/UsingARFoundation.md)
- [Leap Motion-Unterstützung](../features/CrossPlatform/LeapMotionMRTK.md)
- [Erkennen von Plattformfunktionen](../features/DetectingPlatformCapabilities.md)
