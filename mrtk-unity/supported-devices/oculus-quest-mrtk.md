---
title: Oculus Quest MRTK
description: Dokumentation zum Konfigurieren für Oculus Quest im MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Oculus Quest,
ms.openlocfilehash: c0eccd0b366d39529eafc51d23031fc30144b1ae
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143963"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a>Konfigurieren von Oculus Quest in MRTK mithilfe der XR SDK-Pipeline

Eine [Oculus Quest](https://www.oculus.com/quest/) ist erforderlich.

Die MRTK-Unterstützung für Oculus Quest wird über zwei verschiedene Quellen unterstützt: die XR-Pipeline von Unity und das Oculus Integration Unity-Paket. Das **Oculus XRSDK Datenanbieter** ermöglicht die Verwendung beider Quellen und muss für die Verwendung von MRTK in Oculus Quest verwendet werden.

Die [XR-Pipeline von Unity](https://docs.unity3d.com/Manual/XR.html) ermöglicht die Verwendung von Oculus Touch-Controllern und head tracking mit oculus Quest.
Diese Pipeline ist der Standard für die Entwicklung von XR-Anwendungen in Unity 2019.3 und darüber hinaus. Um diese Pipeline zu verwenden, stellen Sie sicher, dass **Sie Unity 2019.3 oder eine neuere verwenden.**

Das [Unity-Paket für die Oculus-Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) ermöglicht die Verwendung der Handverfolgung **mit** oculus Quest.
Dieser Datenanbieter  verwendet NICHT die **XR-Pipeline** von Unity oder die **Legacy-XR-Pipeline.** Da Controller und Die Nachverfolgung jedoch von der XR-Pipeline von Unity verarbeitet werden, müssen die Schritte unter Einrichten des Projekts für **oculus Quest** befolgt werden, um sicherzustellen, dass Sie die **XR-Pipeline** und nicht die veraltete **Legacy-XR-Pipeline verwenden.**

## <a name="setting-up-project-for-the-oculus-quest"></a>Einrichten des Projekts für die Oculus Quest

1. Führen [Sie diese Schritte](https://developer.oculus.com/documentation/unity/book-unity-gsg/) aus, um sicherzustellen, dass Ihr Projekt für die Bereitstellung in Oculus Quest bereit ist.

1. Stellen Sie [sicher, dass der Entwicklermodus](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) auf Ihrem Gerät aktiviert ist. Die Installation der Oculus-ADB-Treiber ist optional.

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a>Einrichten der XR-Pipeline für Oculus Quest

1. Stellen Sie **sicher, dass das Oculus XR-Plug-In** unter **Window --> Paket-Manager**

    ![Oculus XR-Plug-In-Paket](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. Stellen Sie sicher, dass der Oculus-Plug-In-Anbieter in Ihrem Projekt enthalten ist, indem Sie zu Bearbeiten **-->-Projekteinstellungen --> XR-Plug-In-Verwaltung --> Plug-In-Anbieter gehen.**

    ![Oculus-Plug-In-Anbieter](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>Einrichten des Oculus Integration Unity-Pakets zum Aktivieren der Handtracking

1. Laden Sie [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) aus dem Unity Asset Store herunter, und importieren Sie sie. Die neueste Version, die getestet wurde, ist 20.0.0. Ältere Versionen finden Sie in diesem [Archiv.](https://developer.oculus.com/downloads/package/unity-integration-archive/)

1. Navigieren Sie zu Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules(Oculus Integration Unity-Module integrieren). Dadurch werden die asmdefs mit Definitionen und Verweisen aktualisiert, die für die Funktion des relevanten Oculus Quest-Codes erforderlich sind. Außerdem wird die csc-Datei aktualisiert, um die veralteten Warnungen herauszufiltern, die von den Oculus-Integrationsressourcen erzeugt werden. Das MRTK-Repository enthält eine csc-Datei, die Warnungen in Fehler konvertiert. Diese Konvertierung hält den MRTK-Quest Konfigurationsprozess an.

    ![Oculus Integration Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. Im importierten Oculus-Ordner (er sollte sich unter Assets/Oculus befinden) befindet sich ein skriptfähiges Objekt namens OculusProjectConfig. In dieser Konfigurationsdatei müssen Sie HandTrackingSupport auf "Controllers and Hands" festlegen.

    ![Oculus-Integrationscontroller und -Hände](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>Einrichten der Szene

1. Erstellen einer neuen Unity-Szene oder Öffnen einer bereits vorhandenen Szene wie HandInteractionExamples
1. Fügen Sie mrtk zur Szene hinzu, indem Sie zu **Mixed Reality Toolkit** Add to  >  **Scene (Zur Szene hinzufügen) navigieren und konfigurieren.**

## <a name="using-the-oculus-xr-sdk-data-provider"></a>Verwenden des Oculus XR SDK Datenanbieter

1. Konfigurieren Ihres Profils für die Verwendung des **Oculus XR SDK Datenanbieter**
    - Wenn sie nicht beabsichtigen, die Konfigurationsprofile zu ändern
        - Ändern Sie Ihr Profil in DefaultXRSDKConfigurationProfile, und wechseln Sie zu [Erstellen und Bereitstellen Ihres Projekts in Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)

    - Andernfalls gehen Sie wie folgt vor:
        - Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen Sie Kopieren und **Anpassen aus,** um das Mixed Reality-Standardprofil zu klonen.

        ![Profil klonen](../images/cross-platform/CloneProfile.png)

        - Auswählen des **Eingabekonfigurationsprofils**

        ![Eingabekonfigurationsprofil](../images/cross-platform/InputConfigurationProfile.png)

        - Wählen **Sie im** Eingabesystemprofil Klonen aus, um die Änderung zu aktivieren.

        ![Klonen des Eingabesystemprofils](../images/cross-platform/CloneInputSystemProfile.png)

        - Öffnen Sie **den Abschnitt Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** Hinzufügen aus, und am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.  Öffnen Sie den neuen Datenanbieter, und legen Sie **type** auf **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager fest.**

        ![Oculus Add XRSDK Datenanbieter](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. Das Oculus XR SDK Datenanbieter enthält ein OVR Camera Oc Prefab, das das Projekt automatisch mit einem OVR-Kameragerät und OVR-Händen konfiguriert, um Eingaben ordnungsgemäß weiter zu routen. Das manuelle Hinzufügen eines OVR-Kamerageräts zur Szene erfordert eine manuelle Konfiguration von Einstellungen und Eingaben.

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>Erstellen und Bereitstellen Ihres Projekts in Oculus Quest

1. Schließen Sie Oculus Quest über ein USB 3.0-> USB C-Kabel an.
1. Navigieren Sie **zu Datei- > Buildeinstellungen.**
1. Ändern der Bereitstellung in **Android**
1. Stellen Sie sicher, dass Oculus Quest als anwendbares Ausführungsgerät ausgewählt ist.

    ![Oculus Run Device](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. Wählen Sie Erstellen und ausführen aus.
    - Die folgenden Buildfehler treten wahrscheinlich auf, wenn Sie Beim ersten Mal *erstellen und* ausführen auswählen. Sie sollten die Bereitstellung erfolgreich ausführen können, wenn Sie *Erneut erstellen und ausführen* auswählen.

    ![Oculus: Erwartete Buildfehler](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. Akzeptieren Sie die Eingabeaufforderung _USB-Debuggen zulassen_ aus der Aufgabe heraus.
1. Sehen Sie sich Ihre Szene in der Oculus Quest an.

## <a name="removing-oculus-integration-from-the-project"></a>Entfernen der Oculus-Integration aus dem Projekt

1. Navigieren Sie zum Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. Lassen Sie Unity als Verweise in Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef aktualisieren, und andere Dateien werden in diesem Schritt geändert.
1. Schließen von Unity
1. Schließen Sie Visual Studio, wenn es geöffnet ist.
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
