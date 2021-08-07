---
title: Bereitstellen in Oculus Quest
description: Dokumentation zum Konfigurieren für Oculus Quest in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Oculus Quest
ms.openlocfilehash: c5633af09cca5e8b20eb81e897ca8129fed86174e30a97f7242efde231fb7aa1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186657"
---
# <a name="deploying-to-oculus-quest"></a>Bereitstellen in Oculus Quest

Eine [Oculus Quest](https://www.oculus.com/quest/) ist erforderlich.

Die MRTK-Unterstützung für Oculus Quest erfolgt über zwei verschiedene Quellen: die XR SDK-Pipeline von Unity und das Oculus Integration Unity-Paket. Die **Oculus XRSDK-Datenanbieter** ermöglicht die Verwendung beider Quellen und muss verwendet werden, um MRTK auf der Oculus Quest bereitzustellen.

Die [Unity XR SDK-Pipeline](https://docs.unity3d.com/Manual/XR.html) ermöglicht die Verwendung von Oculus Touch-Controllern und head tracking mit der Oculus Quest.
Diese Pipeline ist der Standard für die Entwicklung von XR-Anwendungen in Unity 2019.3 und darüber hinaus. Um diese Pipeline zu verwenden, stellen Sie sicher, dass Sie **Unity 2019.3 oder neuer** verwenden. Dies ist **erforderlich,** um MRTK-Anwendungen in Oculus Quest bereitzustellen.

Das [Oculus Integration Unity-Paket](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) ermöglicht die Verwendung der **Handverfolgung** mit Oculus Quest. Dieser Datenanbieter verwendet **NICHT** die **XR SDK-Pipeline** oder **die Legacy-XR-Pipeline** von Unity.

## <a name="setting-up-project-for-the-oculus-quest"></a>Einrichten eines Projekts für Oculus Quest

1. Führen Sie [diese Schritte](https://developer.oculus.com/documentation/unity/book-unity-gsg/) aus, um sicherzustellen, dass Ihr Projekt auf Oculus Quest bereitgestellt werden kann.

1. Stellen Sie sicher, dass der [Entwicklermodus](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) auf Ihrem Gerät aktiviert ist. Die Installation der Oculus-ADB-Treiber ist optional.

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a>Einrichten der XR SDK-Pipeline für Oculus Quest

1. Stellen Sie sicher, dass das **Oculus XR-Plug-In** unter **Window --> Paket-Manager** installiert ist.

    ![Oculus XR-Plug-In-Paket](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. Stellen Sie sicher, dass der Oculus-Plug-In-Anbieter in Ihrem Projekt enthalten ist, indem **Sie zu Bearbeiten --> Project Einstellungen --> XR-Plug-In-Verwaltung --> Plug-In-Anbieter** gehen.

    ![Oculus-Plug-In-Anbieter](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>Einrichten des Oculus Integration Unity-Pakets zum Aktivieren der Handtracking

1. Laden Sie [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) aus dem Unity Asset Store herunter, und importieren Sie sie. Die neueste Version, die getestet wurde, ist 20.0.0. Ältere Versionen finden Sie in diesem [Archiv.](https://developer.oculus.com/downloads/package/unity-integration-archive/)

1. Navigieren Sie zu Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules(Oculus Integration Unity-Module integrieren). Dadurch werden die asmdefs mit Definitionen und Verweisen aktualisiert, die für die Funktion des relevanten Oculus Quest-Codes erforderlich sind. Außerdem wird die csc-Datei aktualisiert, um die veralteten Warnungen herauszufiltern, die von den Oculus-Integrationsressourcen erzeugt werden. Das MRTK-Repository enthält eine csc-Datei, die Warnungen in Fehler konvertiert. Diese Konvertierung hält den MRTK-Quest Konfigurationsprozess an.

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. Im importierten Oculus-Ordner (er sollte sich unter Assets/Oculus befinden) befindet sich ein skriptfähiges Objekt namens OculusProjectConfig. In dieser Konfigurationsdatei müssen Sie HandTrackingSupport auf "Controllers and Hands" festlegen.

    ![Oculus-Integrationscontroller und -Hände](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>Einrichten der Szene

1. Erstellen Sie eine neue Unity-Szene, oder öffnen Sie eine bereits vorhandene Szene wie HandInteractionExamples.
1. Fügen Sie MRTK zur Szene hinzu, indem Sie zu **Mixed Reality Toolkit** Zur Szene hinzufügen navigieren  >  **und konfigurieren.**

## <a name="using-the-oculus-xr-sdk-data-provider"></a>Verwenden des Oculus XR SDK Datenanbieter

::: moniker range=">= mrtkunity-2021-05"

1. Konfigurieren Ihres Profils für die Verwendung des **Oculus XR SDK Datenanbieter**
    - Wenn sie nicht beabsichtigen, die Konfigurationsprofile zu ändern
        - Verwenden Sie eines der MRTK-Standardprofile, die alle über die XR-Pipelines von Unity konfiguriert sind. Das vorherige DefaultXRSDKConfigurationProfile wird jetzt als veraltet bezeichnet.
        - Wechseln Sie zu [Build and deploy your project to Oculus Quest (Erstellen und Bereitstellen Ihres Projekts in Oculus Quest).](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)
    - Andernfalls gehen Sie wie folgt vor:
        - Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen **Sie Kopieren und Anpassen** aus, um das Standardmäßige Mixed Reality-Profil zu klonen.

        ![Klonprofil](../images/cross-platform/CloneProfile.png)

        - Wählen  Sie das Eingabekonfigurationsprofil aus.

        ![Eingabekonfigurationsprofil](../images/cross-platform/InputConfigurationProfile.png)

        - Wählen Sie im Eingabesystemprofil **Klonen** aus, um die Änderung zu aktivieren.

        ![Klonen des Eingabesystemprofils](../images/cross-platform/CloneInputSystemProfile.png)

        - Öffnen Sie den Abschnitt **Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** hinzufügen aus, und am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.  Öffnen Sie den neuen Datenanbieter, und legen **Sie den Typ** auf **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager** fest.

        ![Oculus Add XRSDK Datenanbieter](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. Konfigurieren Ihres Profils für die Verwendung des **Oculus XR SDK Datenanbieter**
    - Wenn sie nicht beabsichtigen, die Konfigurationsprofile zu ändern
        - Ändern Sie Ihr Profil in DefaultXRSDKConfigurationProfile.
        - Wechseln Sie zu [Build and deploy your project to Oculus Quest (Erstellen und Bereitstellen Ihres Projekts in Oculus Quest).](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)
    - Andernfalls gehen Sie wie folgt vor:
        - Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen **Sie Kopieren und Anpassen** aus, um das Standardmäßige Mixed Reality-Profil zu klonen.

        ![Klonprofil](../images/cross-platform/CloneProfile.png)

        - Wählen  Sie das Eingabekonfigurationsprofil aus.

        ![Eingabekonfigurationsprofil](../images/cross-platform/InputConfigurationProfile.png)

        - Wählen Sie im Eingabesystemprofil **Klonen** aus, um die Änderung zu aktivieren.

        ![Klonen des Eingabesystemprofils](../images/cross-platform/CloneInputSystemProfile.png)

        - Öffnen Sie den Abschnitt **Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** hinzufügen aus, und am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.  Öffnen Sie den neuen Datenanbieter, und legen **Sie den Typ** auf **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager** fest.

        ![Oculus Add XRSDK Datenanbieter](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. Das Oculus XR SDK Datenanbieter enthält eine OVR Camera Rig Prefab, die das Projekt automatisch mit einem OVR Camera Rig und OVR Hands konfiguriert, um Eingaben ordnungsgemäß weiterzuleiten. Das manuelle Hinzufügen einer OVR Camera Rig zur Szene erfordert eine manuelle Konfiguration von Einstellungen und Eingaben.

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>Erstellen und Bereitstellen Ihres Projekts in Oculus Quest

1. Schließen Sie Oculus Quest über ein USB 3.0-> USB C-Kabel an.
1. Navigieren Sie zu **Datei > Build Einstellungen**
1. Ändern der Bereitstellung in **Android**
1. Stellen Sie sicher, dass Oculus Quest als entsprechendes Ausführungsgerät ausgewählt ist.

    ![Oculus Run Device](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. Wählen Sie Erstellen und ausführen aus.
    - Wenn Sie Beim ersten Mal *Erstellen und Ausführen* auswählen, treten wahrscheinlich die folgenden Buildfehler auf. Sie sollten in der Lage sein, die Bereitstellung erfolgreich durchzuführen, wenn *Sie Erneut erstellen und ausführen* auswählen.

    ![Oculus: Erwartete Buildfehler](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. Akzeptieren Sie die Eingabeaufforderung _USB-Debuggen zulassen_ aus der Aufgabe heraus.
1. Sehen Sie sich Ihre Szene innerhalb der Oculus Quest an.

## <a name="removing-oculus-integration-from-the-project"></a>Entfernen der Oculus-Integration aus dem Project

1. Navigieren Sie zum Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![ Oculus Separation Asmdef.](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. Lassen Sie Unity aktualisieren, da Verweise in Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef und anderen Dateien in diesem Schritt geändert werden.
1. Schließen von Unity
1. Schließen sie Visual Studio, wenn es geöffnet ist.
1. Öffnen Sie den Datei-Explorer, und navigieren Sie zum Stamm des MRTK-Unity-Projekts.
1. Löschen des UnityProjectName/Library-Verzeichnisses
1. Löschen des Verzeichnisses UnityProjectName/Assets/Oculus
1. Löschen sie die Datei UnityProjectName/Assets/Oculus.meta.
1. Unity erneut öffnen

## <a name="common-errors"></a>Häufige Fehler

### <a name="quest-not-recognized-by-unity"></a>Quest wird von Unity nicht erkannt

Stellen Sie sicher, dass Ihre Android-Pfade ordnungsgemäß konfiguriert sind. Wenn weiterhin Probleme auftreten, befolgen Sie diese [Anleitung.](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**Bearbeiten > Einstellungen > externen Tools > Android**

![Android Tools-Konfiguration](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
