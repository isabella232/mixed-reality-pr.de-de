---
title: Azure Spatial Anchors für Android und iOS
description: In diesem Kurs lernen Sie, wie Sie ein Unity-Projekt mit dem Mixed Reality Toolkit (MRTK) und Azure Spatial Anchors unter Android und iOS bereitstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Android, iOS, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 6e9ae377a11d74fd9cdfca7ddb0379542d365e3365bdf07319bc8580b2e87420
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215803"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Azure Spatial Anchors für Android und iOS

In diesem Tutorial erfahren Sie, wie Sie Ihr Projekt für Android- und iOS-Geräte mithilfe von AR Foundation, dem ARCore XR-Plug-In und dem ARKit-XR-Plug-In erstellen.

## <a name="objectives"></a>Ziele

* Lernen, wie Sie ein Projekt für Android-Geräte mithilfe von Unity AR Foundation und dem ARCore XR-Plug-In erstellen
* Lernen, wie Sie ein Projekt für iOS-Geräte mithilfe von Unity AR Foundation und dem ARKit XR-Plug-In erstellen

## <a name="installing-inbuilt-unity-packages"></a>Installieren von integrierten Unity-Paketen

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Konfigurieren des MRTK für die AR Foundation Camera

In diesem Abschnitt erfahren Sie, wie Sie das MRTK für die Bereitstellung auf einem mobilen Gerät konfigurieren.

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus. Wählen Sie dann im Inspektorfenster die Registerkarte **Camera** (Kamera) aus, klonen Sie das Kameraprofil, und geben Sie ihm einen passenden Namen, beispielsweise **AzureSpatialAnchors_ARCameraProfile**:

![Unity mit neu erstelltem, ausgewähltem ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der Mixed Reality Toolkit-Profile](mr-learning-base-03.md).

Erweitern Sie bei im Inspektorfenster noch ausgewählter Registerkarte **Camera** (Kamera) die **Camera Setting Providers** (Anbieter von Kameraeinstellungen), und entfernen Sie durch Klicken auf „-“ die **Windows Mixed Reality Camera Setting** (Windows Mixed Reality-Kameraeinstellung) oder die **XR SDK Windows Mixed Reality Camera Setting** (XR SDK Windows Mixed Reality-Kameraeinstellung):

![Unity-ARCameraProfile mit hinzugefügtem neuem Datenanbieter ](images/mr-learning-asa/asa-05-section2-step1-2.png)

und klicken Sie auf die Schaltfläche **+ Add Camera Setting Provider** (Kameraeinstellungsanbieter hinzufügen), und erweitern Sie dann den neu hinzugefügten **New data provider** (Neuer Datenanbieter):

![Für Android hinzugefügte AR-Kamera](images/mr-learning-asa/asa-05-section2-step1-3.png)

Ändern Sie mithilfe der **Type**-Dropdownliste den Typ in **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:

![Unity-ARCameraProfile mit Pfad zur Auswahl des Datenanbietertyps](images/mr-learning-asa/asa-05-section2-step1-4.png)

Aktualisieren Sie die MRTK UnityAR-Skriptdefinitionen, indem Sie das Menüelement aufrufen: „**Mixed Reality** > **Toolkit** > **Utilities (Hilfsprogramme)**  > **UnityAR** > Update Scripting Defines (Skriptdefinitionen aktualisieren)“

## <a name="building-your-application-to-your-android-device"></a>Erstellen Ihrer Anwendung für Ihr Android-Gerät

In diesem Abschnitt erfahren Sie, wie Sie Ihr Projekt so konfigurieren, dass es für ein Android-Gerät erstellt und auf diesem bereitgestellt wird.

Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen, und ändern Sie die Plattform dann in Android:

![Unity-Fenster „Build Settings“ mit ausgewählter Android-Plattform](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Falls Sie eine Auffrischung zum Wechseln der Buildplattform benötigen, lesen Sie die Anweisungen zum [Wechseln der Buildplattform](mr-learning-base-02.md#switching-the-build-platform).

Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).

Wählen Sie im Unity-Menü **Mixed Reality** > **Toolkit** > **Utilities** >  **Configure Project for MRTK** (Mixed Reality > Toolkit > Hilfsprogramme > Projekt für MRTK konfigurieren) aus, um das **MRTK Project Configurator**-Fenster (MRTK-Projektkonfigurator) zu öffnen, vergewissern Sie sich, dass alle Optionen ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Apply** (Übernehmen), um die Einstellungen zu übernehmen:

![Unity MRTK-Projektkonfigurator 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Playereinstellungen zu öffnen, suchen Sie dann den Abschnitt **Player** >  **Other Settings** (Player > Weitere Einstellungen), wählen Sie **Vulkan** aus, und entfernen Sie die Einstellung, indem Sie auf das **„-“** -Symbol klicken:

![„Weitere Einstellungen“ von Unity mit ausgewähltem „Vulcan“](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um Ihre aktuelle Szene zur Liste **Scenes In Build** (Szenen im Build) hinzuzufügen. Verwenden Sie dann ein USB-Kabel, um Ihr Android-Gerät mit Ihrem Computer zu verbinden, und wählen Sie es in der Dropdownliste **Run Device** (Ausführendes Gerät) aus:

![Unity-Fenster „Build Settings“ mit hinzugefügter Szene und ausgewähltem „Run Device“](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Wenn Ihr Gerät nicht in der Dropdownliste „Run Device“ angezeigt wird, müssen Sie möglicherweise auf die Aktualisieren-Schaltfläche neben der Dropdownliste klicken.

Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Build And Run** (Erstellen und ausführen), um das Fenster „Build Android“ (Für Android erstellen) zu öffnen.

Wählen Sie einen geeigneten Speicherplatz zum Speichern Ihres Builds, beispielsweise _D:\MixedRealityLearning\Builds_, geben Sie dann dem APK einen passenden Namen, beispielsweise _MRTKTutorials-AzureSpatialAnchors_, und klicken Sie auf die **Speichern**-Schaltfläche, um den Buildprozess zu starten:

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Speichern Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> Wenn im Fenster der Unity-Konsole irgendwelche Fehler im Zusammenhang mit Android SDK-, NDK- oder JDK-Modulen angezeigt werden, müssen Sie den Unity Hub öffnen und die zugehörigen Module für die Android-Buildunterstützung installieren.

Wenn der Buildvorgang abgeschlossen ist, sollten Ihre Apps automatisch auf dem Android-Gerät geladen werden.

## <a name="building-your-application-to-your-ios-device"></a>Erstellen Ihrer Anwendung für Ihr iOS-Gerät

In diesem Abschnitt erfahren Sie, wie Sie Ihr Projekt so konfigurieren, dass es für ein iOS-Gerät erstellt und auf diesem bereitgestellt wird.

Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen, und ändern Sie die Plattform in iOS:

![Unity-Fenster „Build Settings“ mit ausgewähltem iOS](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Falls Sie eine Auffrischung zum Wechseln der Buildplattform benötigen, lesen Sie die Anweisungen zum [Wechseln der Buildplattform](mr-learning-base-02.md#switching-the-build-platform).

Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).

Wählen Sie im Unity-Menü **Mixed Reality** > **Toolkit** > **Utilities** >  **Configure Project for MRTK** (Mixed Reality > Toolkit > Hilfsprogramme > Projekt für MRTK konfigurieren) aus, um das **MRTK Project Configurator**-Fenster (MRTK-Projektkonfigurator) zu öffnen, vergewissern Sie sich, dass alle Optionen ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Apply** (Übernehmen), um die Einstellungen zu übernehmen:

![Unity MRTK-Projektkonfigurator-Fenster iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Playereinstellungen zu öffnen, suchen Sie dann den Abschnitt **Player** >  **Other Settings** (Player > Weitere Einstellungen), und deaktivieren Sie das Kontrollkästchen **Strip Engine Code** (Engine-Code entfernen), um es zu deaktivieren:

![„Weitere Einstellungen“ von Unity mit deaktiviertem Strip Engine Code](images/mr-learning-asa/asa-05-section4-step1-3.png)

Schließen Sie das Fenster „Player Settings“ (Playereinstellungen), und öffnen Sie das Fenster **Build Settings** (Buildeinstellungen) erneut.

Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um Ihre aktuelle Szene der Liste **Scenes In Build** (Szenen im Build) hinzuzufügen:

![Unity-Fenster „Build Settings“ mit hinzugefügter Szene](images/mr-learning-asa/asa-05-section4-step1-4.png)

Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Erstellen**, um das Fenster „Build iOS“ (Für iOS erstellen) zu öffnen.

Wählen Sie einen geeigneten Speicherplatz zum Speichern Ihres Xcode-Projekts, beispielsweise _D:\MixedRealityLearning\Builds_, erstellen Sie einen neuen Ordner, geben Sie ihm einen passenden Namen, beispielsweise _MRTKTutorials-AzureSpatialAnchors_, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Speichern iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

Wenn der Buildvorgang abgeschlossen ist, befolgen Sie die Anweisungen in [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) (Xcode-Projekt exportieren), um Ihr Xcode-Projekt auf Ihrem iOS-Gerät bereitzustellen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie Ihr Projekt für Android- und iOS-Geräte mithilfe von AR Foundation, dem ARCore XR-Plug-In und dem ARKit-XR-Plug-In erstellen.
