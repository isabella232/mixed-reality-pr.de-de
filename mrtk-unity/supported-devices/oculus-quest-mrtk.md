---
title: Oculus Quest MRTK
description: Dokumentation zum Konfigurieren für Oculus Quest im MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Oculus Quest,
ms.openlocfilehash: 6b9c3a8f51388785f685714ef02be680bb98e14c
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908394"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a>Erstellen und Bereitstellen von MRTK für Oculus Quest mithilfe der XR SDK-Pipeline

Eine [Oculus Quest](https://www.oculus.com/quest/) ist erforderlich.

Die MRTK-Unterstützung für Oculus Quest wird über zwei verschiedene Quellen bereitgestellt: die XR SDK-Pipeline von Unity und das Oculus Integration Unity-Paket. Das **Oculus XRSDK Datenanbieter** ermöglicht die Verwendung beider Quellen und muss zum Bereitstellen von MRTK auf der Oculus Quest verwendet werden.

Die [Unity XR SDK-Pipeline](https://docs.unity3d.com/Manual/XR.html) ermöglicht die Verwendung von Oculus Touch-Controllern und head tracking mit oculus Quest.
Diese Pipeline ist der Standard für die Entwicklung von XR-Anwendungen in Unity 2019.3 und darüber hinaus. Um diese Pipeline zu verwenden, stellen Sie sicher, dass **Sie Unity 2019.3 oder eine neuere verwenden.** Dies **ist erforderlich,** um MRTK-Anwendungen in Oculus Quest bereitzustellen.

Das [Unity-Paket für die Oculus-Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) ermöglicht die Verwendung der Handverfolgung **mit** oculus Quest. Dieser Datenanbieter verwendet **NICHT** die **XR SDK-Pipeline** von Unity oder **die Legacy-XR-Pipeline**.

## <a name="setting-up-project-for-the-oculus-quest"></a>Einrichten des Projekts für die Oculus Quest

1. Führen [Sie diese Schritte](https://developer.oculus.com/documentation/unity/book-unity-gsg/) aus, um sicherzustellen, dass Ihr Projekt für die Bereitstellung in Oculus Quest bereit ist.

1. Stellen Sie [sicher, dass der Entwicklermodus](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) auf Ihrem Gerät aktiviert ist. Die Installation der Oculus-ADB-Treiber ist optional.

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a>Einrichten der XR SDK-Pipeline für Oculus Quest

1. Stellen Sie **sicher, dass das Oculus XR-Plug-In** unter **Window --> Paket-Manager**

    ![Oculus XR-Plug-In-Paket](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. Stellen Sie sicher, dass der Oculus-Plug-In-Anbieter in Ihrem Projekt enthalten ist, indem Sie zu Bearbeiten **-->-Projekteinstellungen --> XR-Plug-In-Verwaltung --> Plug-In-Anbieter gehen.**

    ![Oculus-Plug-In-Anbieter](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>Einrichten des Oculus Integration Unity-Pakets zum Aktivieren der Handtracking

1. Laden Sie die [Oculus-Integration aus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) dem Unity Asset Store herunter, und importieren Sie sie. Die neueste getestete Version ist 20.0.0. Ältere Versionen finden Sie in diesem [Archiv.](https://developer.oculus.com/downloads/package/unity-integration-archive/)

1. Navigieren Sie zu Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules(Oculus-Integrations-Unity-Module integrieren). Dadurch werden die Asmdefs mit Definitionen und Verweisen aktualisiert, die erforderlich sind, damit der relevante Oculus Quest-Code funktioniert. Außerdem wird die csc-Datei aktualisiert, um die veralteten Warnungen herausfiltern zu können, die von den Oculus Integration-Ressourcen erzeugt werden. Das MRTK-Repository enthält eine csc-Datei, die Warnungen in Fehler konvertiert. Diese Konvertierung hält den MRTK-Quest an.

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. Im importierten Ordner Oculus (der sich unter Assets/Oculus befindet) befindet sich ein skriptfähiges Objekt namens OculusProjectConfig. In dieser Konfigurationsdatei müssen Sie HandTrackingSupport auf "Controller und Hände" festlegen.

    ![Oculus Integration Controller And Hands](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>Einrichten der Szene

1. Erstellen Sie eine neue Unity-Szene, oder öffnen Sie eine bereits vorhandene Szene wie HandInteractionExamples.
1. Fügen Sie der Szene MRTK hinzu, indem Sie zu Mixed Reality **Toolkit** zur Szene hinzufügen  >  **und konfigurieren.**

## <a name="using-the-oculus-xr-sdk-data-provider"></a>Verwenden des Oculus XR SDK Datenanbieter

::: moniker range=">= mrtkunity-2021-05"

1. Konfigurieren Ihres Profils für die Verwendung **des Oculus XR SDK Datenanbieter**
    - Wenn sie die Konfigurationsprofile nicht ändern möchten
        - Verwenden Sie eines der MRTK-Standardprofile, die alle über die XR-Pipelines von Unity konfiguriert sind. Das vorherige DefaultXRSDKConfigurationProfile ist jetzt als veraltet gekennzeichnet.
        - Wechseln Sie zu Build and deploy your project to Oculus Quest (Erstellen und [Bereitstellen Ihres Projekts in Oculus Quest).](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)
    - Gehen Sie andernfalls wie folgt vor:
        - Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen Sie Kopieren und **Anpassen aus,** um das Mixed Reality-Standardprofil zu klonen.

        ![Profil klonen](../images/cross-platform/CloneProfile.png)

        - Wählen Sie das **Eingabekonfigurationsprofil** aus.

        ![Eingabekonfigurationsprofil](../images/cross-platform/InputConfigurationProfile.png)

        - Wählen **Sie im** Eingabesystemprofil Klonen aus, um die Änderung zu aktivieren.

        ![Klonen des Eingabesystemprofils](../images/cross-platform/CloneInputSystemProfile.png)

        - Öffnen Sie **den Abschnitt Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** Hinzufügen aus, und am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.  Öffnen Sie den neuen Datenanbieter, und legen Sie **type** auf **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager fest.**

        ![Oculus Add XRSDK Datenanbieter](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. Konfigurieren Ihres Profils für die Verwendung **des Oculus XR SDK Datenanbieter**
    - Wenn sie die Konfigurationsprofile nicht ändern möchten
        - Ändern Sie Ihr Profil in DefaultXRSDKConfigurationProfile.
        - Wechseln Sie zu Build and deploy your project to Oculus Quest (Erstellen und [Bereitstellen Ihres Projekts in Oculus Quest).](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)
    - Gehen Sie andernfalls wie folgt vor:
        - Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen Sie Kopieren und **Anpassen aus,** um das Mixed Reality-Standardprofil zu klonen.

        ![Profil klonen](../images/cross-platform/CloneProfile.png)

        - Wählen Sie das **Eingabekonfigurationsprofil** aus.

        ![Eingabekonfigurationsprofil](../images/cross-platform/InputConfigurationProfile.png)

        - Wählen **Sie im** Eingabesystemprofil Klonen aus, um die Änderung zu aktivieren.

        ![Klonen des Eingabesystemprofils](../images/cross-platform/CloneInputSystemProfile.png)

        - Öffnen Sie **den Abschnitt Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** Hinzufügen aus, und am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.  Öffnen Sie den neuen Datenanbieter, und legen Sie **type** auf **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager fest.**

        ![Oculus Add XRSDK Datenanbieter](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. Das Oculus XR SDK Datenanbieter enthält ein OVR Camera Rig Prefab, das das Projekt automatisch mit einem OVR-Kameragerät und OVR-Händen konfiguriert, um Eingaben ordnungsgemäß weiter zu routen. Das manuelle Hinzufügen eines OVR-Kamerageräts zur Szene erfordert eine manuelle Konfiguration von Einstellungen und Eingaben.

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>Erstellen und Bereitstellen Ihres Projekts in Oculus Quest

1. Schließen Sie Oculus Quest über ein USB 3.0-> USB C-Kabel an.
1. Navigieren Sie **zu Datei- > Buildeinstellungen.**
1. Ändern der Bereitstellung in **Android**
1. Stellen Sie sicher, dass Oculus Quest als anwendbares Ausführungsgerät ausgewählt ist.

    ![Oculus Run Device](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. Wählen Sie Erstellen und ausführen aus.
    - Die folgenden Buildfehler treten wahrscheinlich auf, wenn Sie Beim ersten Mal *erstellen und* ausführen auswählen. Sie sollten die Bereitstellung erfolgreich ausführen können, wenn Sie *Erneut erstellen und ausführen* auswählen.

    ![Oculus Erwartete Buildfehler](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. Akzeptieren Sie die _Eingabeaufforderung USB-Debuggen_ zulassen innerhalb der Suche.
1. Sehen Sie sich Ihre Szene innerhalb der Oculus Quest an.

## <a name="removing-oculus-integration-from-the-project"></a>Entfernen der Oculus-Integration aus dem Projekt

1. Navigieren Sie zum Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. Lassen Sie Unity als Verweise in microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef aktualisieren, und andere Dateien werden in diesem Schritt geändert.
1. Schließen von Unity
1. Schließen Visual Studio, wenn sie geöffnet ist
1. Öffnen Sie den Datei-Explorer, und navigieren Sie zum Stamm des MRTK-Unity-Projekts.
1. Löschen des Verzeichnisses UnityProjectName/Library
1. Löschen des Verzeichnisses UnityProjectName/Assets/Oculus
1. Löschen Sie die Datei UnityProjectName/Assets/Oculus.meta.
1. Unity erneut öffnen

## <a name="common-errors"></a>Häufige Fehler

### <a name="quest-not-recognized-by-unity"></a>Quest wird von Unity nicht erkannt

Stellen Sie sicher, dass Ihre Android-Pfade ordnungsgemäß konfiguriert sind. Wenn weiterhin Probleme auftreten, befolgen Sie diese [Anleitung.](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**Bearbeiten > Einstellungen > externen Tools > Android**

![Konfiguration der Android-Tools](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
