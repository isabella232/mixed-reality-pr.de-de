---
title: MRTK 2.6 – Anmerkungen zu dieser Version
description: Versionshinweise zur MRTK-Version 2.6
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 4ac82f7e07135e840886fef810844ff00ef1ac1e
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647194"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Versionshinweise Mixed Reality Microsoft Mixed Reality Toolkit 2.6

> [!IMPORTANT]
> Es gibt ein bekanntes Compilerproblem, das anwendungen betrifft, die für Microsoft HoloLens 2 mit ARM64 erstellt wurden. Dieses Problem wird behoben, indem Visual Studio 2019 auf Version 16.8 oder höher aktualisiert wird. Wenn sie nicht aktualisiert werden Visual Studio, importieren Sie das Paket, `com.microsoft.mixedreality.toolkit.tools` um eine Problemumgehung anzuwenden.

## <a name="whats-new-in-262"></a>Neues in 2.6.2

### <a name="corrects-parenting-of-the-spatial-mesh"></a>Korrigieren der übergeordneten Klammer des räumlichen Gitters

Behebt das [Problem,](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) dass räumliche Gitternetze nach dem Mixed Reality Playspace-Objekt nicht ordnungsgemäß gefunden wurden (z. B. über einen Teleport).

## <a name="whats-new-in-261"></a>Neues in 2.6.1

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>Korrekturen von OpenXR, die nicht unter HoloLens 2/UWP ausgeführt werden

Korrigiert eine Regression, die verhindert hat, dass die OpenXR-Unterstützung des MRTK unter UWP ausgeführt wird.

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>Korrektur von Leap Motion-ObjektManipulator wird nicht gedreht

Korrigiert eine Regression, bei der die Drehung einer Leap Motion-Hand vom ObjectManipulator-Skript nicht berücksichtigt wurde.

### <a name="sample-scene-updates"></a>Beispiel für Szenenupdates

Aktualisiert die Szenenverständnis-Beispielszene, um den ausgelieferten Zustand des Unity-Plug-Ins korrekt widerzuzustanden. Aktualisiert außerdem das Beispiel, damit keine Abhängigkeit mehr von der importierten Beispielszene für räumliche Wahrnehmung vor sich geht. Vor dem Update auf 2.6.1 sollten Sie die importierten Szenenverständnis- und räumlichen Wahrnehmungsbeispiele löschen, sofern sie in Ihrem Projekt vorhanden sind, um mögliche Konflikte zu vermeiden. Wenn Sie diese Beispiele nicht entfernt haben und Konflikte im Zusammenhang mit den Beispielen in der Konsole angezeigt werden, entfernen Sie beide Beispiele (oder den Ordner), und versuchen Sie dann erneut, `Assets/Samples/Mixed Reality Toolkit Examples` den Importvorgang zu starten.

Aktualisiert die Dialogbeispielszene, um die aktuellen Dialogszenarien richtig zu beschreiben.

## <a name="whats-new-in-260"></a>Neues in 2.6.0
<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>Unterstützung für OpenXR hinzugefügt

Die erste Unterstützung für das OpenXR-Vorschaupaket von Unity und das OpenXR Mixed Reality Paket von Microsoft wurde hinzugefügt. Weitere Informationen finden Sie auf der Seite [MRTK/XRSDK getting started (Erste Schritte mit MRTK/XRSDK),](../configuration/getting-started-with-mrtk-and-xrsdk.md)im [Unity-Forumbeitrag](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)oder in der [Microsoft-Dokumentation.](/windows/mixed-reality/develop/unity/openxr-getting-started)

> [!IMPORTANT]
> OpenXR in Unity wird nur unter Unity 2020.2 und höher unterstützt.
>
> Derzeit werden auch nur x64- und ARM64-Builds unterstützt.

### <a name="asset-swap-utility"></a>Hilfsprogramm zum Austauschen von Ressourcen

Tauschen Sie mehrere Ressourcen in einer Unity-Szene mit dem neuen [Asset Swap-Hilfsprogramm aus.](../features/tools/asset-swap-utility.md)

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>HP Motion Controllers now supported with MRTK

Controller für HP Reverb G2 funktionieren jetzt nativ mit MRTK.

### <a name="experimental-interactive-element--state-visualizer"></a>Experimentelles interaktives Element und Zustandsvis visualisieren

Interactive Element ist ein vereinfachter zentralisierter Einstiegspunkt für das MRTK-Eingabesystem. Sie enthält Zustandsverwaltungsmethoden, Ereignisverwaltung und die Zustandseinstellungslogik für Kerninteraktionszustände. Weitere Informationen finden Sie in der [Interactive-Elementdokumentation.](../features/experimental/interactive-element.md)

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

Die Zustands-Schnellansicht ist eine Animationskomponente, die vom Interactive-Element abhängt.  Diese Komponente erstellt Animationsclips, legt Keyframes fest und generiert einen Animatorzustandscomputer. Weitere Informationen finden Sie in [der Dokumentation zur Zustands schnellansicht.](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>Teleportierung mit der Teleportgeste wird jetzt auf allen Plattformen unterstützt

Benutzer können nun die Teleportgeste verwenden, um ihren Spielbereich auf allen Plattformen zu bewegen. Verwenden Sie zum Teleportieren mit einem Controller auf MR-Geräten mit Standardkonfigurationen den Fingerabdruck. Um mit artikulierten Händen zu teleportieren, erstellen Sie eine Geste, bei der die Handfläche nach oben mit dem Index und dem Daumen nach außen gerichtet ist, und den Teleport durch Krümmen des Zeigefingers abschließen. Informationen zum Teleportieren mit der Eingabesimulation finden Sie in unserer aktualisierten [Dokumentation zum Eingabesimulationsdienst.](../features/input-simulation/input-simulation-service.md)

  ![Teleportgeste](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>Scene Understanding jetzt im MRTK als experimenteller Beobachter für räumliche Wahrnehmung verfügbar

Experimentelle Unterstützung von [Scene Understanding](/windows/mixed-reality/scene-understanding) wird in MRTK 2.6 eingeführt. Benutzer können die Szenenverständnisfunktionen von HoloLens 2 als Beobachter des räumlichen Bewusstseins in MRTK-basierte Projekte integrieren. Weitere Informationen finden [Sie in der Scene Understanding-Dokumentation.](../features/spatial-awareness/scene-understanding.md)

> [!IMPORTANT]
> Scene Understanding wird nur unter HoloLens 2 und Unity 2019.4 und höher unterstützt.
>
> Für dieses Feature ist das Scene Understanding-Paket erforderlich, das jetzt über das Mixed Reality [Featuretool verfügbar ist.](https://aka.ms/MRFeatureTool)
> Wenn Sie das Mixed Reality Feature Tool verwenden oder anderweitig über UPM importieren, importieren Sie das Beispiel Demos – SpatialAwareness, bevor Sie das Beispiel Experimental – SceneUnderstanding aufgrund eines Abhängigkeitsproblems importieren. Weitere Informationen [finden Sie in diesem GitHub-Problem.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)

  ![Szenenverständnis](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>Unterstützung für Laufzeitprofilwechsel

MRTK ermöglicht jetzt den Profilwechsel sowohl vor der Initialisierung der MRTK-Instanz (d. h. vor dem MRTK-Initialisierungsprofilwechsel) als auch nach der aktiven Verwendung eines Profils (d. h. aktive Profilwechsel). Der erste Switch kann verwendet werden, um ausgewählte Komponenten basierend auf den Funktionen der Hardware zu aktivieren, während letzteres verwendet werden kann, um die Benutzererfahrung zu ändern, wenn der Benutzer einen Unterteil der Anwendung eintritt. Weitere Informationen und [Codebeispiele finden Sie](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) in der Dokumentation zum Profilwechsel.

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>Direktionaler Indikator und Folgen von Solvern, die von experimentell geerbt wurden

Zwei neue Solver sind für die Verwendung mit dem HAUPTLINIEN-MRTK bereit.

  ![Solver für Richtungsindikatoren](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>Hand Von Experimentellem geerbt

Das Hand Features kann jetzt mit dem MRTK-Hauptfunktionsfeature verwendet werden.
  ![Hand-Hand-Hand-Beispiel](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>Dialogsteuerelemente, die von experimentell abgestuft wurden

Dialogsteuerelemente sind jetzt für die Verwendung mit dem HAUPT-MRTK bereit.

  ![Dialogsteuerelemente](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>Pulse-Shader aus experimentellem Shader geerbt

Die Pulse-Shaderskripts wurden von experimentell geerbt. Weitere Informationen finden Sie in der [Dokumentation zu Pulse Shader.](../features/rendering/pulse-shader.md)

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>Verbesserungen des Eingabeaufzeichnungsdiensts

`InputRecordingService` und `InputPlaybackService` können jetzt Eingaben zum Anvingen mit den Augen aufzeichnen und wiedererlangen. Die Aufzeichnung wurde optimiert, um eine konsistente Framerate während des gesamten Aufzeichnungszeitraums sicherzustellen, während die Größe der Aufzeichnungsdatei und die Spartenzeit ebenfalls um ca. 50 % reduziert werden. Das Speichern und Laden von Aufzeichnungsdateien kann jetzt asynchron ausgeführt werden. Beachten Sie, dass sich das Dateiformat der Aufzeichnung in [](../features/input-simulation/input-animation-file-format.md) dieser MRTK-Version geändert hat. Weitere Informationen zu den neuen Spezifikationen für Version 1.1 finden Sie hier.

### <a name="reading-mode"></a>Lesemodus

Unterstützung für den [Lesemodus auf](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) HoloLens 2. Der Lesemodus reduziert das Sichtfeld des Systems, beseitigt aber eine Skalierung der Unity-Ausgabe. Ein von Unity gerenderter Pixel entspricht einem projizierten Pixel auf HoloLens 2. Anwendungsautoren sollten Tests mit mehreren Personen durchführen, um sicherzustellen, dass dies ein Kompromiss ist, den sie in ihrer App wünschen.

  ![Windows Mixed Reality Lesemodus](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>Unterstützung für 3D-App-Starter auf UWP

Fügt die Möglichkeit zum Festlegen eines [3D-App-Startfelds für](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) UWP hinzu. Diese Einstellung wird sowohl im MRTK-Buildfenster als auch in den MRTK-Projekteinstellungen unter Buildeinstellungen verfügbar gemacht. Sie wird während des Build in Unity automatisch in das Projekt geschrieben.

  ![Buildeinstellungen](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>Aktuelle Änderungen

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>Bestimmte Felder importierter GLTF-Objekte werden jetzt groß formatiert.

Aufgrund von Problemen mit der Deserialisierung beginnen einige Felder importierter GLTF-Objekte jetzt mit Großbuchstaben. Die betroffenen Felder sind (in ihren neuen Namen): `ComponentType` , , , , , , , , , `Path` , , `Interpolation` `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` .

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>Die Eingabeanimation-Binärdatei hat ein aktualisiertes Format der Version 1.1.

Die eingabeanimierte Binärdatei, die von und verwendet wird, verfügt jetzt über ein aktualisiertes Dateiformat, um die Optimierungen für `InputRecordingService` diese beiden Dienste zu `InputPlaybackService` ermöglichen. Weitere Informationen [zu](../features/input-simulation/input-animation-file-format.md) den neuen Spezifikationen für Version 1.1 finden Sie hier.

### <a name="msbuild-for-unity-support"></a>Unterstützung von MSBuild für Unity

Die Unterstützung für MSBuild für Unity wurde ab Version 2.5.2 entfernt, um sie an den neuen Paketleitfaden von [Unity auszurichten.](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)

## <a name="known-issues"></a>Bekannte Probleme

### <a name="openxr"></a>OpenXR

Es gibt derzeit ein bekanntes Problem mit Holographic Remoting und OpenXR, bei dem Handgelenke nicht konsistent verfügbar sind.
Darüber hinaus sind die Eyetracking-Beispielszenen derzeit nicht kompatibel, obwohl eye tracking *funktioniert.*

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>Einige Mixed Reality-Shader-Standardfeatures des Toolkits erfordern das Foundation-Paket.

Beim Importieren über den Unity Paket-Manager befinden sich die MRTK-Standard-Shader-Hilfsskripts (z.B. HoverLight.cs) nicht zusammen mit dem Shader im Paket Standardressourcen. Um auf diese Funktionalität zugreifen zu können, müssen Anwendungen das Foundation-Paket importieren.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache erstellt beim Herunterfahren möglicherweise eine neue Kamera

In einigen Situationen (z. B. bei Verwendung des LeapMotion-Anbieters im Unity-Editor) ist es möglich, dass CameraCache die MainCamera beim Herunterfahren neu erstellt. Weitere Informationen [finden Sie in](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) diesem Problem.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException beim Importieren von Beispielen über Unity Paket-Manager

Je nach Länge des Projektpfads können beim Importieren von Beispielen über Unity Paket-Manager FileNotFoundException-Meldungen in der Unity-Konsole generiert werden. Die Ursache dafür ist, dass der Pfad zur fehlenden Datei länger als MAX_PATH (256 Zeichen) ist. Um das Problem zu beheben, kürzen Sie die Länge des Projektpfads.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Es wurde kein Spatializer angegeben. Die Anwendung unterstützt räumlichen Sound nicht.

Wenn kein Audioraumisierer konfiguriert ist, wird die Warnung "No spatializer was specified" (Es wurde kein Spatializer angegeben) angezeigt. Dies kann auftreten, wenn kein XR-Paket installiert ist, da Unity Spatializer in diese Pakete einfing.

Stellen Sie zum Beheben dieses Problems Sicher, dass:

- **Fenster**  >  **Paket-Manager** mindestens ein XR-Paket installiert ist
- **Mixed Reality Toolkit**  >  **Hilfsprogramme**  >  **Konfigurieren des Unity-Projekts** und Treffen einer Auswahl für **Audio Spatializer**

  ![Auswählen von Audio Spatializer](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: Objektverweis ist nicht auf eine Instanz eines Objekts festgelegt (SceneTransitionService.Iniinitialisieren)

In einigen Situationen kann das `EyeTrackingDemo-00-RootScene` Öffnen eine NullReferenceException in der Initialize-Methode der SceneTransitionService-Klasse verursachen.
Dieser Fehler liegt daran, dass das Konfigurationsprofil des Scene Transition Service nicht konfiguriert ist. Führen Sie die folgenden Schritte aus, um das Problem zu beheben:

- Navigieren Sie zum `MixedRealityToolkit` -Objekt in der Hierarchie.
- Wählen Sie im Inspektorfenster die Option aus. `Extensions`
- Wenn sie nicht erweitert ist, erweitern Sie `Scene Transition Service`
- Legen Sie den Wert von `Configuration Profile` auf **MRTKExamplesHubSceneTransitionServiceProfile fest.**

![Korrektur des Szenenübergangsprofils](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

Derzeit gibt es ein bekanntes Problem bei der Verwendung des [Oculus XR-Plug-Ins mit für eigenständige Plattformen.](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)  Informationen zu Updates finden Sie unter Oculus bug tracker/forums/release notes (Oculus-Fehlerverfolgung/Foren/Versionshinweise).

Der Fehler wird mit dem folgenden Satz von drei Fehlern bezeichnet:

![Oculus XR-Plug-In-Fehler](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI und TextMeshPro

Es gibt ein bekanntes Problem für neuere Versionen von TextMeshPro (1.5.0+ oder 2.1.1+), bei dem der Standardschriftgrad für Dropdownlisten und fett formatierten Schriftzeichenabstand geändert wurde.

![TMP-Image](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Dies kann durch ein Downgrade auf eine frühere Version von TextMeshPro umbehind werden. Weitere [Informationen finden #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) Probleminformationen.