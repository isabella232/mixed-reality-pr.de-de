---
title: MRTK-Unity Entwicklerdokumentation
description: Erfahren Sie mehr über Mixed Reality Toolkit für Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK
ms.openlocfilehash: ecd12cb6fbed305f1a2532f0b55a6d0441df43fa537c63d9919ae9bc91a675c0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204657"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>Was ist das Mixed Reality Toolkit?

![Mixed Reality-Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyXHW]

MRTK-Unity ist ein von Microsoft vorangetriebenes Projekt, das einen Satz von Komponenten und Funktionen bereitstellt, die zum Beschleunigen der Entwicklung von plattformübergreifenden MR-Apps in Unity dienen. Dies sind einige der gebotenen Funktionen:

* Stellt das **plattformübergreifende Eingabesystem und Bausteine für räumliche Interaktionen und die Benutzeroberfläche** bereit.
* Ermöglicht **schnelle Prototyperstellung** mithilfe von Simulationen im Editor, die Ihnen die Möglichkeit geben, Änderungen sofort zu sehen.
* Fungiert als **erweiterbares Framework**, das Entwicklern die Möglichkeit zum Austausch von Kernkomponenten bietet.
* **Unterstützt eine große Bandbreite an Plattformen**:

::: moniker range=">= mrtkunity-2021-05"
| Plattform | Unterstützte Geräte |
|---|---|
| OpenXR (Unity 2020.3.8 und höher) | Microsoft HoloLens 2 <br> Windows Mixed Reality-Headsets |
| Windows Mixed Reality | Microsoft HoloLens <br> Microsoft HoloLens 2 <br> Windows Mixed Reality-Headsets  |
| Oculus (Unity 2019.3 oder höher) | Oculus Quest |
| OpenVR |  Windows Mixed Reality-Headsets <br> HTC Vive <br> Oculus Rift |
| Ultraleap Hand-Tracking | Ultraleap Leap Motion-Controller |
| Mobil | iOS und Android |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Plattform | Unterstützte Geräte |
|---|---|
| OpenXR (Vorschauversion in MRTK 2.6, Unity 2020.3.8 und höher) | Microsoft HoloLens 2 <br> Windows Mixed Reality-Headsets |
| Windows Mixed Reality | Microsoft HoloLens <br> Microsoft HoloLens 2 <br> Windows Mixed Reality-Headsets  |
| Oculus (Unity 2019.3 oder höher) | Oculus Quest |
| OpenVR |  Windows Mixed Reality-Headsets <br> HTC Vive <br> Oculus Rift |
| Ultraleap Hand-Tracking | Ultraleap Leap Motion-Controller |
| Mobil | iOS und Android |
::: moniker-end

## <a name="getting-started-with-mrtk"></a>Erste Schritte mit MRTK

Wenn Sie sich erst mit dem MRTK oder der Mixed Reality-Entwicklung in Unity vertraut machen, empfehlen wir Ihnen, die Beispielanwendung „MRTK-Beispiele-Hub“ auf Ihrem Gerät oder [Emulator](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) zu installieren und zu erkunden. 

> [!div class="nextstepaction"]
> [Herunterladen der MRTK-Beispiel-Hub-App](running-examples-hub.md)

Sobald Sie sich ein Bild gemacht haben, was Mixed Reality und MRTK zu bieten haben, installieren Sie die erforderlichen Tools, und folgen Sie unserer Tutorialreihe zur HoloLens 2 für Einsteiger.

> [!div class="nextstepaction"]
> [Installieren der Tools](/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [HoloLens 2-Tutorialreihe](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

Möchten Sie wissen, wie es unter der Haube aussieht?
> [!div class="nextstepaction"]
> [Entdecken Sie das MRTK auf GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a>Dokumentation

| [![Anmerkungen zu diesem Release](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-27-release-notes.md)<br/>[Versionshinweise](release-notes/mrtk-26-release-notes.md)| [![Übersicht über das MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)<br/>[Übersicht über das MRTK](architecture/overview.md)|[![API-Referenz ](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)<br/>[API-Referenz](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a>Buildstatus

| Verzweigung | CI-Status | Docs-Status |
|---|---|---|
| `main` |[![CI-Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![Docs-Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="feature-areas"></a>Featurebereiche

:::row:::
    :::column:::
       [![Eingabesystem](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)<br>
        **[Eingabesystem](features/input/overview.md)**<br>
    :::column-end:::
    :::column:::
        [![Hand-Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)<br>
        **[Hand-Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**<br>
    :::column-end:::
    :::column:::
        [![Eyetracking (Blickverfolgung) (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)<br>
        **[Eyetracking (Blickverfolgung) <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**<br>
    :::column-end:::
    :::column:::
        [![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)<br>
        **[Profiles](configuration/mixed-reality-configuration-guide.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Hand-Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](supported-devices/leap-motion-mrtk.md)<br>
        **[Hand-Tracking <br/> (Ultraleap)](supported-devices/leap-motion-mrtk.md)**<br>
    :::column-end:::
    :::column:::
        [![UI-Steuerelemente](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)<br>
        **[UI-Steuerelemente](#ux-building-blocks)**<br>
    :::column-end:::
    :::column:::
        [![Solver](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)<br>
        **[Solver](features/ux-building-blocks/solvers/solver.md)**<br>
    :::column-end:::
    :::column:::
        [![Multiszenen-Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[Multiszenen-<br/> Manager](features/scene-system/scene-system-getting-started.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Räumliche Wahrnehmung](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)<br>
        **[Räumliche <br/> Wahrnehmung](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Diagnosetool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[Diagnose- <br/> tool](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Ansicht „MRTK-Standard-Shader“](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)<br>
        **[Beispielansicht „MRTK-Standard-Shader“](features/rendering/mrtk-standard-shader.md?q=shader)**<br>
    :::column-end:::
    :::column:::
        [![Sprache und Diktat](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[Sprache](features/input/speech.md)<br/> & [Diktat](features/input/dictation.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Begrenzungssystem](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)<br>
        **[Begrenzungs- <br/>system](features/boundary/boundary-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Simulation im Editor](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[Simulation <br/> im Editor](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Experimentelle Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)<br>
        **[Experimentelle <br/> Features](contributing/experimental-features.md)**<br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a>UX-Bausteine

:::row:::
    :::column:::
       [![Schaltfläche](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Schaltfläche](features/ux-building-blocks/button.md)**<br>
        Ein Schaltflächen-Steuerelement, das verschiedene Eingabemethoden unterstützt, einschließlich der artikulierten Hand von HoloLens 2.
    :::column-end:::
    :::column:::
        [![Begrenzungssteuerelement](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Begrenzungssteuerelement](features/ux-building-blocks/bounds-control.md)**<br>
        Standard Benutzeroberfläche zum Bearbeiten von Objekten im 3D-Raum
    :::column-end:::
    :::column:::
        [![Objektmanipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Objektmanipulator](features/ux-building-blocks/object-manipulator.md)**<br>
        Skript zum Manipulieren von Objekten mit einer oder zwei Händen.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**<br>
        2D-artige Ebene, die Scrollen mit artikulierter Handeingabe unterstützt.
    :::column-end:::
    :::column:::
        [![Systemtastatur](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[Systemtastatur](features/ux-building-blocks/system-keyboard.md)**<br>
        Beispielskript für die Verwendung der Systemtastatur in Unity
    :::column-end:::
    :::column:::
        [![Interaktionsfähig](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interaktionsfähig](features/ux-building-blocks/interactable.md)**<br>
        Ein Skript, um Objekte interaktionsfähig zu machen, mit visuellen Zuständen und Designunterstützung.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**<br>
        Verschiedene Objektpositionierungsverhalten wie tag-along, body-lock, konstante Ansichtsgröße und Oberflächenmagnetismus.
    :::column-end:::
    :::column:::
        [![Objektsammlung](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Objektsammlung](features/ux-building-blocks/object-collection.md)**<br>
        Skript zum Anordnen eines Arrays von Objekten in einer dreidimensionalen Form.
    :::column-end:::
    :::column:::
        [![QuickInfo](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[QuickInfo](features/ux-building-blocks/tooltip.md)**<br>
        Anmerkungsbenutzeroberfläche mit einem flexiblen Anker-/Pivot-System, das zum Bezeichnen von Motion-Controllern und Objekten verwendet werden kann.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Schieberegler](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Schieberegler](features/ux-building-blocks/sliders.md)**<br>
        Schieberegler-Benutzeroberfläche zum Anpassen von Werten, die direkte Hand-Tracking-Interaktion unterstützen.
    :::column-end:::
    :::column:::
        [![MRTK-Standard-Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK-Standard-Shader](features/rendering/mrtk-standard-shader.md)**<br>
        Der Standard-Shader des MRTK unterstützt leistungsstark verschiedene Fluent Design-Elemente.
    :::column-end:::
    :::column:::
        [![Handmenü](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Handmenü](features/ux-building-blocks/hand-menu.md)**<br>
        Handgesperrte Benutzeroberfläche für Schnellzugriff unter Verwendung des Handeinschränkungs-Solvers.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![App-Leiste](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App-Leiste](features/ux-building-blocks/app-bar.md)**<br>
        Benutzeroberfläche für die manuelle Aktivierung von Begrenzungs-Steuerelementen.
    :::column-end:::
    :::column:::
        [![ Zeiger](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Zeiger](features/input/pointers.md)**<br>
        Erfahren Sie mehr über verschiedene Typen von Zeigern.
    :::column-end:::
    :::column:::
        [![Fingerspitzenvisualisierung](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingerspitzenvisualisierung](features/ux-building-blocks/fingertip-visualization.md)**<br>
        Visuelles Angebot an der Fingerspitze, das das Vertrauen in die direkte Interaktion verbessert.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Nähemenü](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Nähemenü](features/ux-building-blocks/near-menu.md)**<br>
        Unverankerte Menübenutzeroberfläche für die Näheinteraktionen.
    :::column-end:::
    :::column:::
        [![Räumliche Wahrnehmung: Erste Schritte](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Räumliche Wahrnehmungsansicht](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
        Machen Sie Ihre Holografieobjekte interaktionsfähig für die physischen Umgebungen.
    :::column-end:::
    :::column:::
        [![Sprachbefehl](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Sprachbefehl](features/input/speech.md)**<br>
        Skripts und Beispiele für die Integration von Spracheingaben.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Statusanzeige](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Statusanzeige](features/ux-building-blocks/progress-indicator.md)**<br>
        Visueller Indikator zum Kommunizieren eines Datenprozesses oder -vorgangs.
    :::column-end:::
    :::column:::
        [![Dialogfeld](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialogfeld](features/ux-building-blocks/dialog.md)**<br>
        Benutzeroberfläche zum Anfordern der Bestätigung oder Anerkennung durch den Benutzer.
    :::column-end:::
    :::column:::
        [![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**<br>
        Komponente, die hilft, den Benutzer anzuleiten, wenn die Geste noch nicht vermittelt wurde.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Handphysikdienst](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/extensions/hand-physics-service.md) **[Handphysikdienst [Experimentell]](features/extensions/hand-physics-service.md)**<br>
        Der Handphysikdienst ermöglicht Festkörperkollisionsereignisse und -interaktionen mit artikulierten Händen.
    :::column-end:::
    :::column:::
        [![Scrollsammlung](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrollsammlung](features/ux-building-blocks/scrolling-object-collection.md)**<br>
        Eine Objektsammlung, die nativ 3D-Objekte scrollt.
    :::column-end:::
    :::column:::
        [![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimentell]](features/experimental/dock.md)**<br>
        Das Dock ermöglicht das Verschieben von Objekten in und aus vordefinierten Positionen.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Eyetracking: Zielauswahl](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eyetracking: Zielauswahl](features/input/eye-tracking/eye-tracking-target-selection.md)**<br>
        Kombinieren Sie Augen, Sprach- und Handeingaben, um schnell und einfach Hologramme in Ihrer Szene auszuwählen.
    :::column-end:::
    :::column:::
        [![Eyetracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eyetracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**<br>
        Erfahren Sie, wie Sie Text automatisch scrollen oder fließend in Inhalt im Vordergrund zoomen, basierend darauf, was Sie ansehen.
    :::column-end:::
    :::column:::
        [![Eyetracking: Heatmap](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eyetracking: Heatmap](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**<br>
        Beispiele für das Protokollieren, Laden und Visualisieren dessen, was Benutzer in Ihrer App angesehen haben
    :::column-end:::
:::row-end:::

## <a name="tools"></a>Tools

|  [![Optimierungsfenster](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimierungsfenster](features/tools/optimize-window.md) | [![Abhängigkeitsfenster](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Abhängigkeitsfenster](features/tools/dependency-window.md) | [![Buildfenster](features/images/MRTK_Icon_BuildWindow.png)](features/tools/build-window.md) [Buildfenster](features/tools/build-window.md) | [![Eingabeaufzeichnung](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Eingabeaufzeichnung](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| Automatisieren der Konfiguration von Mixed Reality-Projekten für Leistungsoptimierungen. | Analysieren von Abhängigkeiten zwischen Ressourcen und Identifizieren nicht verwendeter Ressourcen. |  Konfigurieren und Ausführen eines End-to-End-Erstellungsprozesses für Mixed Reality-Anwendungen | Aufzeichnen und Wiedergeben von Kopfbewegungs-und Hand-Tracking-Daten im Editor |

## <a name="example-scenes"></a>Beispielszenen

MRTK enthält Beispielszenen, die die Verwendung der MRTK-Features veranschaulichen. Die Beispielszenen finden Sie im Ordner Assets/MRTK/Examples/Demos. Lesen Sie die Seite [Beispielszenen](running-example-scenes.md), um zu erfahren, wie Sie Beispielszenen abrufen und ausführen. Die [Szene mit Beispielen für die Handinteraktion](features/example-scenes/hand-interaction-examples.md) ist ein idealer Ort, um die Bausteine des MRTK für Interaktionen und die Benutzeroberfläche zu erleben.

[![Beispielszene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>MRTK-Beispiele-Hub

Mit dem MRTK-Beispiele-Hub können Sie verschiedene Beispielszenen im MRTK ausprobieren, ohne die einzelnen Szenen erstellen und bereitstellen zu müssen.
Sie können vorgefertigte App-Pakete für HoloLens(x86), HoloLens 2(ARM) und immersive Windows Mixed Reality-Headsets(x64) herunterladen, indem Sie das Paket „Mixed Reality Toolkit-Beispiel“ im [MR-Featuretool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) auswählen. Stellen Sie sicher, dass [Sie das Windows-Geräteportal zum Installieren von Apps für HoloLens (1. Generation) verwenden](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens). Auf HoloLens 2 können Sie den [MRTK-Beispiele-Hub über die Microsoft Store-App](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4) herunterladen und installieren.

Weitere Informationen zu den Details der Erstellung eines Multiszenen-Hubs mit dem Szenensystem und dem Szenenübergangsdienst des MRTK finden Sie auf der [INFO-Seite des Beispiele-Hubs](features/example-scenes/example-hub.md).

[![Beispielszenen-Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>Mit dem MRTK erstellte Beispiel-Apps.

| [![Periodensystem der Elemente](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![Galaxie-Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)| [![Oberflächenbeispiel-App](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)|
|:--- | :--- | :--- |
| [Periodensystem der Elemente](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) (Periodic Table of the Elements) ist eine Open-Source-Beispiel-App, die veranschaulicht, wie das Eingabesystem und die Bausteine des MRTK zum Erstellen einer App-Erfahrung für HoloLens und immersive Headsets verwendet werden. Lesen Sie die Portierungsgeschichte: [Einbinden der „Periodic Table of the Elements“-App in HoloLens 2 mit dem MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) ist eine Open-Source-Beispiel-App, die ursprünglich im März 2016 im Rahmen der Kampagne „Share Your Idea“ (Ideen teilen) von HoloLens entwickelt wurde. Galaxy Explorer wurde mit den neuen Features für HoloLens 2 mithilfe des MRTK v2 aktualisiert. Lesen Sie die Geschichte: [Making of Galaxy Explorer für HoloLens 2](/windows/mixed-reality/galaxy-explorer-update) |[Oberflächen](https://github.com/microsoft/MRDL_Unity_Surfaces) (Surfaces) ist eine Open-Source-Beispiel-App für HoloLens 2, die erkundet, wie wir mit visuellen Eindrücken, Audio und vollständig artikuliertem Hand-Tracking ein taktiles Gefühl schaffen können. Das detaillierte Design und die Entwicklungsgeschichte finden Sie in der Microsoft MR Dev Days-Sitzung [Erfahrungen aus der Surfaces-App](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App). |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Sitzungsvideos von den Mixed Reality Dev Days 2020

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| Tutorial zum Erstellen einer einfachen MRTK-APP von Anfang bis Ende. Erfahren Sie mehr über Interaktionskonzepte und die plattformübergreifenden Funktionen des MRTK. | Tiefgehende Besprechung der UX-Bausteine des MRTK, die Sie beim Erstellen schöner Mixed Reality-Erfahrungen unterstützen. | Eine Einführung in Leistungstools, sowohl die in MRTK enthaltenen als auch externe, sowie eine Übersicht zum MRTK-Standardshader. |

Weitere Sitzungsvideos finden Sie unter [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions).

## <a name="engage-with-the-community"></a>Mit der Community in Kontakt treten

* Nehmen Sie an der Unterhaltung über MRTK bei [Slack](https://holodevelopers.slack.com/) teil. Sie können der Slack-Community über den [automatischen Einladungsversender](https://holodevelopersslack.azurewebsites.net/) beitreten.

* Stellen Sie Fragen zur Verwendung des MRTK bei [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) unter Verwendung des Tags **MRTK**.

* Suchen Sie nach [bekannten Problemen](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues), oder melden Sie ein [neues Problem](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues), wenn Sie einen Defekt im MRTK-Code finden.

* Wenn Sie Fragen zur Mitwirkung am MRTK haben, besuchen Sie den [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858)-Kanal in Slack.

Für dieses Projekt gelten die Microsoft-Verhaltensregeln für Open Source ([Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/)).
Um weitere Informationen zu erhalten, lesen Sie die häufig gestellten Fragen zu den Verhaltensregeln ([Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)), oder wenden Sie sich mit weiteren Fragen und Kommentaren an [opencode@microsoft.com](mailto:opencode@microsoft.com).

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Nützliche Ressourcen im Mixed Reality Dev Center

| ![Erkunden](features/images/mrdevcenter/icon-discover.png) [Erkunden](/windows/mixed-reality/)| ![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)| ![Entwicklung](features/images/mrdevcenter/icon-develop.png) [Entwicklung](/windows/mixed-reality/development)| ![Verteilen](features/images/mrdevcenter/icon-distribute.png) [Verteilen](/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| Erfahren Sie, wie Sie Mixed Reality-Erfahrungen für HoloLens und immersive Headsets (VR) entwickeln.          | Erhalten Sie Entwurfshandbücher. Erstellen von Benutzeroberflächen. Erfahren Sie mehr über Interaktionen und Eingaben.     | Erhalten Sie Entwicklungshandbücher. Lernen Sie die Technologie kennen. Verstehen der wissenschaftlichen Aspekte.       | Bereiten Sie Ihre App für andere Benutzer vor, und erstellen Sie ggf. ein 3D-Startprogramm. |

## <a name="useful-resources-on-azure"></a>Nützliche Ressourcen in Azure

| ![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Spatial Anchors](/azure/spatial-anchors/)| ![Speech-Dienste](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech-Dienste](/azure/cognitive-services/speech-service/)| ![Bildverarbeitungsdienste](features/images/mrdevcenter/icon-azurevisionservices.png) [Bildverarbeitungsdienste](/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Spatial Anchors ist ein plattformübergreifender Dienst, mit dem Sie Mixed Reality-Erlebnisse mit Objekten erstellen können, die ihre Positionen auf Geräten im Zeitverlauf beibehalten.| Erforschen Sie Azure-basierte Sprachfunktionen wie Sprache-in-Text, Sprechererkennung und Sprachübersetzung, und integrieren Sie diese in Ihre Anwendung.| Erkennen und analysieren Sie Ihre Bild- oder Videoinhalte mithilfe von Bildverarbeitungsdiensten wie maschinelles Sehen, Gesichtserkennung, Emotionserkennung oder Video-Indexer. |

## <a name="how-to-contribute"></a>Beitragen

Erfahren Sie, wie Sie beim MRTK mitwirken können, unter [Mitwirkung](contributing/contributing.md).

## <a name="getting-help"></a>Hilfe

Wenn Probleme auftreten, die vom MRTK verursacht wurden, oder wenn Sie anderweitige Fragen zu Vorgehensweisen haben, gibt es einige Ressourcen, die Ihnen helfen können:

* Bei Fehlerberichten [melden Sie ein Problem](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) im GitHub-Repository.
* Wenn Sie Fragen haben, wenden Sie sich entweder an [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) oder an den [mixed-reality-toolkit-Kanal](https://holodevelopers.slack.com/messages/C2H4HT858) in Slack. Sie können der Slack-Community über den [automatischen Einladungsversender](https://holodevelopersslack.azurewebsites.net/) beitreten.