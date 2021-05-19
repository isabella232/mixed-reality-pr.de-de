---
title: MRTK-Pakete
description: Pakete in MRTK, die Mixed Reality-Hardware und -Plattformen unterstützen.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Unity Paket-Manager,
ms.openlocfilehash: 3c92448d99cd67efa0a06feff9b0c7561a6aea79
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143803"
---
# <a name="mixed-reality-toolkit-packages"></a>Mixed Reality Toolkit-Pakete

Das Mixed Reality Toolkit (MRTK) ist eine Sammlung von Paketen, die die plattformübergreifende Mixed Reality-Anwendungsentwicklung ermöglichen, indem sie Unterstützung für Mixed Reality Und-Plattformen bereitstellen.

MRTK ist als [Assetpakete](#asset-packages) (.unitypackage) und über die [Unity-Paket-Manager.](#unity-package-manager)

## <a name="asset-packages"></a>Bestandspakete

Das MRTK-Asset (.unitypackage) kann von [GitHub heruntergeladen werden.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)

Zu den Vorteilen der Verwendung von Ressourcenpaketen gehören:

- Verfügbar für Unity 2018.4 und neuer
- Einfaches Vornehmen von Änderungen am MRTK
  - MRTK befindet sich im Ordner Assets

Beispiele hierfür sind:

- MRTK ist Teil des Ordners Assets des Projekts, was zu
  - Größere Projekte
  - Langsamere Kompilierungszeiten
- Keine Abhängigkeitsverwaltung
  - Kunden müssen Paketabhängigkeiten manuell auflösen.
- Manueller Updatevorgang
  - Mehrere Schritte
  - Große Quellcodeverwaltungsupdates (mehr als 3000 Dateien)
  - Risiko des Verlusts von Änderungen am MRTK
- Das Importieren des Beispielpakets bedeutet in der Regel, dass alle Beispiele enthalten sind.

Die verfügbaren Pakete sind:

- [Foundation](#foundation-package)
- [Erweiterungen](#extensions-package)
- [Extras](#tools-package)
- [Test-Hilfsprogramme](#test-utilities-package)
- [Beispiele](#examples-package)

Diese Pakete werden von Microsoft aus dem Quellcode im [Branch mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) auf GitHub veröffentlicht und unterstützt.

### <a name="foundation-package"></a>Basispaket

Die Mixed Reality Toolkit Foundation ist ein Codesatz, mit dem Ihre Anwendung allgemeine Funktionen auf Mixed Reality Plattformen nutzen kann.

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<sup>MRTK Foundation Package</sup>

Das MRTK Foundation-Paket enthält Folgendes.

| Ordner | Komponente | Beschreibung |
| --- | --- | --- |
| MRTK/Core | | Schnittstellen- und Typdefinitionen, Basisklassen, Standard-Shader. |
| MRTK/Core/Providers | | Plattformunabhängige Datenanbieter |
| | Hände | Basisklassenunterstützung und -dienste für die Handnachverfolgung. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | Unterstützung für die Aufzeichnung von Kopfbewegungs- und Handnachverfolgungsdaten. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | Unterstützung für die Simulation von Hand- und Augeneingaben im Editor. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | Beobachter für räumliche Wahrnehmung, der ein 3D-Modell als Daten verwendet. |
| | UnityInput | Gängige Eingabegeräte (Maus, Maus usw.), die über die Eingabe-API von Unity implementiert werden. |
| MRTK/Providers | | Plattformspezifische Datenanbieter |
| | LeapMotion | Unterstützung für den UltraLeap Leap Motion-Controller. |
| | OpenVR | Unterstützung für OpenVR-Geräte. |
| | Oculus | Unterstützung für Oculus-Geräte, z. B. Quest. |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) | (Experimentell) Kameraeinstellungsanbieter, der die MRTK-Verwendung mit mobilen AR-Geräten ermöglicht. |
| | WindowsMixedReality | Unterstützung für Windows Mixed Reality Geräte, einschließlich Microsoft HoloLens und immersiven Headsets. |
| | Windows | Unterstützung für Microsoft Windows-spezifische APIs, z. B. Sprache und Diktat. |
| | XR SDK | (Experimentell) Unterstützung für [das neue XR-Framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) von Unity in Unity 2019.3 und neuer. |
| MRTK/SDK | | |
| | Experimentell | Experimentelle Features, einschließlich Shadern, Benutzeroberflächensteuerelementen und einzelnen System-Managern. |
| | Features | Funktionalität, die auf dem Foundation-Paket aufbaut. |
| | Profiles | Standardprofile für die Microsoft Mixed Reality Toolkit-Systeme und -Dienste. |
| | StandardAssets | Allgemeine Ressourcen; Modelle, Texturen, Materialien usw. |
| MRTK/SceneSystemResources | | Ressourcen und Ressourcen, die vom Szenensystem verwendet werden |
| MRTK/Services | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | System, das VR-Begrenzungsunterstützung implementiert. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | System, das die Kamerakonfiguration und -verwaltung implementiert. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | System, das in die Anwendungsdiagnose implementiert, z. B. einen visuellen Profiler. |
| | [InputSystem](../features/input/overview.md) | System, das Unterstützung für den Zugriff auf und die Verarbeitung von Benutzereingaben bereitstellt. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | System, das Unterstützung für Anwendungen mit mehreren Szenen bereitstellt. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | System, das Unterstützung für die Kenntnis der Umgebung des Benutzers bereitstellt. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | System, das Unterstützung für Teleporting bereitstellt (Umstieg auf die Erfahrung bei Sprüngen). |
| MRTK/StandardAssets | | MRTK Standard-Shader, Basismaterialien und andere Standardressourcen für Mixed Reality-Erfahrungen |

### <a name="extensions-package"></a>Erweiterungspaket

Das optionale Paket Microsoft.MixedRealityToolkit.Unity.Extensions enthält zusätzliche Dienste, die die Funktionalität des Microsoft Mixed Reality Toolkits erweitern.

> [!NOTE]
> Das Erweiterungspaket erfordert Microsoft.MixedRealityToolkit.Unity.Foundation.

| Ordner | Komponente | Beschreibung |
| --- | --- | --- |
| MRTK/Erweiterungen | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | Dienst, der den artikulierten Händen physikalische Unterstützung hinzufügt. |
| | LostTrackingService | Dienst, der die Behandlung von Nachverfolgungsverlusten auf Microsoft HoloLens vereinfacht. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | Dienst, der das Hinzufügen reibungsloser Szenenübergänge vereinfacht. |

### <a name="tools-package"></a>Tools-Paket

Das optionale Paket Microsoft.MixedRealityToolkit.Unity.Tools enthält hilfreiche Tools, die die Mixed Reality-Entwicklungserfahrung mit dem Microsoft Mixed Reality Toolkit verbessern.
Diese Tools befinden sich im Menü **Mixed Reality Toolkit > Hilfsprogramme** im Unity-Editor.

> [!NOTE]
> Das Tools-Paket erfordert Microsoft.MixedRealityToolkit.Unity.Foundation.

| Ordner | Komponente | Beschreibung |
| --- | --- | --- |
| MRTK/Tools | |
| | BuildWindow | Tool, das den Prozess der Entwicklung und Bereitstellung von UWP-Anwendungen vereinfacht. |
| | [DependencyWindow](../features/tools/dependency-window.md) | Tool, das ein Abhängigkeitsdiagramm von Ressourcen in einem Projekt erstellt. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | Assistent zur Unterstützung beim Erstellen von Erweiterungsdiensten. |
| | [MigrationWindow](../features/tools/migration-window.md) | Tool, das beim Aktualisieren von Code hilft, der veraltete MRTK-Komponenten verwendet.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Hilfsprogramm zum Automatisieren der Konfiguration eines Mixed Reality-Projekts, um die beste Leistung in Unity zu erzielen. |
| | ReserializeAssetsUtility | Bietet Unterstützung für die Reserialisierung bestimmter Unity-Dateien. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | Hilfsprogramm, mit dem Entwickler Unity-Zuordnungen für Hardwarecontroller schnell bestimmen können. |
| | ScreenshotUtility | Ermöglicht das Erfassen von Anwendungsbildern im Unity-Editor. |
| | TextureCombinerWindow | Hilfsprogramm zum Kombinieren von Grafiktexturen. |
| | [Werkzeugkasten](../features/ux-building-blocks/toolbox.md) | Benutzeroberfläche, die die Ermittlung und Verwendung von MRTK-UX-Komponenten erleichtert. |

### <a name="test-utilities-package"></a>Testen des Hilfsprogrammpakets

Das optionale Paket Microsoft.MixedRealityToolkit.TestUtilities ist eine Sammlung von Hilfsskripts, mit denen Entwickler problemlos [Tests im Wiedergabemodus erstellen](../contributing/unit-tests.md#play-mode-tests)können. Diese Hilfsprogramme sind besonders nützlich für Entwickler, die MRTK-Komponenten erstellen.

| Ordner | Komponente | Beschreibung |
| --- | --- | --- |
| MRTK/Tests | |
| | TestUtilities | Methoden zur Vereinfachung der Erstellung von Playmodustests, einschließlich Handsimulations-Hilfsprogrammen. |

### <a name="examples-package"></a>Beispielpaket

Das Beispielpaket enthält Demos, Beispielskripts und Beispielszenen, in denen funktionen im Basispaket ausgeführt werden. Dieses Paket enthält die [HandInteractionExample-Szene](../features/example-scenes/hand-interaction-examples.md) (unten dargestellt), die Beispielobjekte enthält, die auf verschiedene Arten von Handeingaben (artikuliert und nicht artikuliert) reagieren.

![HandInteractionExample-Szene](../features/images/MRTK_Examples.png)

Dieses Paket enthält auch Eyetracking-Demos, die [hier dokumentiert](../features/example-scenes/eye-tracking-examples-overview.md) sind.

Im Allgemeinen sollte jedes neue Feature im MRTK ein entsprechendes Beispiel im Beispielpaket enthalten, das ungefähr derselben Ordnerstruktur und demselben Speicherort folgt.

> [!NOTE]
> Das Beispielpaket erfordert Microsoft.MixedRealityToolkit.Unity.Foundation.

| Ordner | Komponente | Beschreibung |
| --- | --- | --- |
| MRTK/Beispiele | | |
| | Demos | Einfache Szenen, die ein oder zwei verwandte Features veranschaulichen. |
| | Experimentell | Demoszenen zur Veranschaulichung experimenteller Features. |
| | StandardAssets | Gemeinsame Objekte, die von mehreren Demoszenen gemeinsam genutzt werden. |

## <a name="unity-package-manager"></a>Unity Paket-Manager

Für Erfahrungen, die mit Unity 2019.4 und neuer erstellt werden, ist das MRTK über die [Unity-Paket-Manager](https://docs.unity3d.com/Manual/Packages.html)verfügbar.

Zu den Vorteilen der Verwendung von Ressourcenpaketen zählen:

- Kleinere Projekte
  - Bereinigung Visual Studio Lösungen
  - Weniger Einzucheckende Dateien (MRTK ist ein einfacher Verweis in der `Packages/manifest.json` Datei)
- Schnellere Kompilierung
  - Unity muss MRTK während der Erstellung nicht neu kompilieren.
- Abhängigkeitsauflösung
  - Erforderliche MRTK-Pakete werden automatisch installiert, wenn Pakete mit Abhängigkeiten angegeben werden.
- Einfaches Update auf neue MRTK-Versionen
  - Ändern der Version in der `Packages/manifest.json` Datei

Beispiele hierfür sind:

- MRTK ist unveränderlich
  - Änderungen können nicht vorgenommen werden, ohne dass sie während der Paketauflösung entfernt werden.
- MRTK unterstützt keine UPM-Pakete mit Unity 2018.4

### <a name="foundation-package"></a>Foundation-Paket

Das Basispaket ( `com.microsoft.mixedreality.toolkit.foundation` ) bildet die Grundlage des Mixed Reality Toolkits.

| Ordner | Komponente | Beschreibung |
| --- | --- | --- |
| MRTK/Core | | Schnittstellen- und Typdefinitionen, Basisklassen, Standard-Shader. |
| MRTK/Core/Providers | | Plattformunabhängige Datenanbieter |
| | Hände | Basisklassenunterstützung und Dienste für die Handverfolgung. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | Unterstützung für das Aufzeichnen von Kopfbewegungs- und Handverfolgungsdaten. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | Unterstützung für die In-Editor-Simulation von Hand- und Augeneingaben. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | Beobachter des räumlichen Bewusstseins, der ein 3D-Modell als Daten verwendet. |
| | UnityInput | Allgemeine Eingabegeräte (Mouse, Mouse usw.), die über die Eingabe-API von Unity implementiert werden. |
| MRTK/Providers | | Plattformspezifische Datenanbieter |
| | LeapMotion | Unterstützung für den UltraLeap Leap Motion-Controller. |
| | OpenVR | Unterstützung für OpenVR-Geräte. |
| | Oculus | Unterstützung für Oculus-Geräte, z. B. Quest. |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) | (Experimentell) Anbieter von Kameraeinstellungen, der die MRTK-Verwendung mit mobilen AR-Geräten ermöglicht. |
| | WindowsMixedReality | Unterstützung für Windows Mixed Reality Geräte, einschließlich Microsoft HoloLens und immersiven Headsets. |
| | Windows | Unterstützung für Microsoft Windows-spezifische APIs, z. B. Sprache und Diktat. |
| | XR SDK | (Experimentell) Unterstützung für [das neue XR-Framework von Unity](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in Unity 2019.3 und neuer. |
| MRTK/SDK | | |
| | Experimentell | Experimentelle Features, z. B. Shader, Steuerelemente der Benutzeroberfläche und einzelne System-Manager. |
| | Features | Funktionalität, die auf dem Foundation-Paket aufbaut. |
| | Profiles | Standardprofile für die Microsoft Mixed Reality Toolkit-Systeme und -Dienste. |
| | StandardAssets | Allgemeine Ressourcen; Modelle, Texturen, Materialien usw. |
| MRTK/Services | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | System, das VR-Begrenzungsunterstützung implementieren. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | System, das die Kamerakonfiguration und -verwaltung implementieren. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | System, das in der Anwendungsdiagnose implementieren, z. B. ein visueller Profiler. |
| | [InputSystem](../features/input/overview.md) | System, das Unterstützung für den Zugriff auf und die Verarbeitung von Benutzereingaben bietet. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | System, das Anwendungsunterstützung für mehrere Szenen bietet. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | System, das Unterstützung für das Bewusstsein der Umgebung des Benutzers bietet. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | System, das Unterstützung für das Teleporting bietet (um die Erfahrung bei Springen zu verbessern). |

Abhängigkeiten:

- Standardressourcen ( `com.microsoft.mixedreality.toolkit.standardassets` )

### <a name="standard-assets"></a>Standardressourcen

Das Standardressourcenpaket ( `com.microsoft.mixedreality.toolkit.standardassets)` ist eine Sammlung von Komponenten, die für alle Mixed Reality-Erfahrungen empfohlen werden, einschließlich:

- MRTK Standard-Shader
- Grundlegende Materialien mit dem MRTK Standard-Shader
- Audiodateien
- Schriftarten
- Texturen
- Symbole

> [!Note]
> Um Breaking Changes basierend auf Assemblydefinitionen zu vermeiden, sind die Skripts, die zum Steuern einiger Features des MRTK Standard-Shaders verwendet werden, nicht im Standardressourcenpaket enthalten. Diese Skripts finden Sie im Basispaket im `MRTK/Core/Utilities/StandardShader` Ordner .

Abhängigkeiten: keine

### <a name="extension-packages"></a>Erweiterungspakete

Das optionale Erweiterungspaket ( `com.microsoft.mixedreality.toolkit.extensions)` enthält zusätzliche Komponenten, die die Funktionalität des MRTK erweitern.

| Ordner | Komponente | Beschreibung |
| --- | --- | --- |
| MRTK/Extensions | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | Dienst, der die physikalische Unterstützung für die artikulierten Hände hinzufügt. |
| | LostTrackingService | Dienst, der die Nachverfolgung von Verlusten auf Microsoft HoloLens Geräten vereinfacht. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | Dienst, der das Hinzufügen von reibungslosen Szenenübergängen vereinfacht. |
| | Beispiele~ | Ein ausgeblendeter Ordner (im Unity-Editor), der die Beispielszenen und Objekte enthält. |

Weitere Informationen zum Verwenden von Paketen mit Beispielprojekten finden Sie im Artikel [Mixed Reality Toolkit und Unity Paket-Manager.](../configuration/usingupm.md#using-mixed-reality-toolkit-examples)

Abhängigkeiten:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="tools-package"></a>Tools-Paket

Das optionale Toolspaket ( `com.microsoft.mixedreality.toolkit.tools)` enthält Tools, die zum Erstellen von Mixed Reality-Erfahrungen nützlich sind. Im Allgemeinen handelt es sich bei diesen Tools um Editorkomponenten, und ihr Code wird nicht als Teil einer Anwendung versendet.

| Ordner | Komponente | Beschreibung |
| --- | --- | --- |
| MRTK/Tools | |
| | BuildWindow | Ein Tool, das die Erstellung und Bereitstellung von UWP-Anwendungen vereinfacht. |
| | [DependencyWindow](../features/tools/dependency-window.md) | Tool, das ein Abhängigkeitsdiagramm von Ressourcen in einem Projekt erstellt. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | Assistent zur Unterstützung beim Erstellen von Erweiterungsdiensten. |
| | [MigrationWindow](../features/tools/migration-window.md) | Tool, das beim Aktualisieren von Code hilft, der veraltete MRTK-Komponenten verwendet.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Hilfsprogramm zur Automatisierung der Konfiguration eines Mixed Reality-Projekts für die beste Leistung in Unity. |
| | ReserializeAssetsUtility | Bietet Unterstützung für das erneute Initialisieren bestimmter Unity-Dateien. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | Hilfsprogramm, mit dem Entwickler Unity-Zuordnungen für Hardwarecontroller schnell bestimmen können. |
| | ScreenshotUtility | Ermöglicht das Erfassen von Anwendungsbildern im Unity-Editor. |
| | TextureCombinerWindow | Hilfsprogramm zum Kombinieren von Grafiktexturen. |
| | [Werkzeugkasten](../features/ux-building-blocks/toolbox.md) | Benutzeroberfläche, die es einfach macht, MRTK-UX-Komponenten zu finden und zu verwenden. |

Abhängigkeiten:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="test-utilities-package"></a>Testen des Hilfsprogrammepakets

Das optionale Paket für Testprogramme ( ) enthält eine Sammlung von Hilfsskripts, mit denen Entwickler problemlos Tests `com.microsoft.mixedreality.toolkit.testutilities` im Wiedergabemodus erstellen können. Diese Hilfsprogramme sind besonders nützlich für Entwickler, die MRTK-Komponenten erstellen.

| Ordner | Komponente | Beschreibung |
| --- | --- | --- |
| MRTK/Tests | |
| | TestUtilities | Methoden zur Vereinfachung der Erstellung von Playmodustests, einschließlich Handsimulations-Hilfsprogrammen. |

Abhängigkeiten:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="examples-package"></a>Beispielpaket

Das Beispielpaket ( `com.microsoft.mixedreality.toolkit.examples` ) ist so strukturiert, dass Entwickler nur die beispiele von Interesse importieren können.

Weitere Informationen zum Verwenden von Paketen mit Beispielprojekten finden Sie im Artikel [Mixed Reality Toolkit und Unity Paket-Manager.](../configuration/usingupm.md#using-mixed-reality-toolkit-examples)

| Ordner | Komponente | Beschreibung |
| --- | --- | --- |
| MRTK/Beispiele | | |
| | Beispiele~ | Ein ausgeblendeter Ordner (im Unity-Editor), der die Beispielszenen und Objekte enthält. |
| | StandardAssets | Gemeinsame Objekte, die von mehreren Demoszenen gemeinsam genutzt werden. |

Abhängigkeiten:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )
- Erweiterungen (`com.microsoft.mixedreality.toolkit.extensions`)

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über die Architektur](../architecture/overview.md)
- [Systeme, Erweiterungsdienste und Datenanbieter](../architecture/systems-extensions-providers.md)
- [Mixed Reality Toolkit und Unity Paket-Manager](../configuration/usingupm.md)
