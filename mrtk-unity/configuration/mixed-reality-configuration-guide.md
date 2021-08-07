---
title: MRTK-Profilkonfigurations-Leitfaden
description: Dokumentation zum Konfigurieren von MRTK in Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: e18695610b5e07c4f811e7c43bc13607857a9459407f9b16f39d4f7350f354e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214923"
---
# <a name="mrtk-profile-configuration-guide"></a>MRTK-Profilkonfigurations-Leitfaden

Das Mixed Reality Toolkit zentralisiert so viel konfiguration, wie für die Verwaltung des Toolkits erforderlich ist (mit Ausnahme echter Runtime-"Dinge").

Dieser Leitfaden ist eine einfache exemplarische Vorgehensweise für jeden Konfigurationsprofilbildschirm, der derzeit für das Toolkit verfügbar ist.

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>Das Hauptkonfigurationsprofil für Mixed Reality Toolkit

Das Hauptkonfigurationsprofil, das dem *MixedRealityToolkit* GameObject in Ihrer Szene angefügt ist, stellt den Haupteinstiegspunkt für das Toolkit in Ihrem Projekt bereit.

> [!NOTE]
> Das Mixed Reality Toolkit "sperrt" die Standardkonfigurationsbildschirme, um sicherzustellen, dass Sie immer über einen gemeinsamen Startpunkt für Ihr Projekt verfügen, und es wird empfohlen, mit der Definition Ihrer eigenen Einstellungen zu beginnen, wenn sich Ihr Projekt weiterentwickelt. Die MRTK-Konfiguration kann während des Wiedergabemodus nicht bearbeitet werden.

![MRTK-Konfigurationsprofil](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

Alle Standardprofile für das Mixed Reality Toolkit finden Sie im SDK-Projekt im Ordner Assets/MRTK/SDK/Profiles.

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile ist für HoloLens 2 optimiert. Weitere Informationen finden Sie unter [Profile.](../features/profiles/profiles.md)

Wenn Sie den Haupt-Mixed Reality Toolkit-Konfigurationsprofil öffnen, wird der folgende Bildschirm im Inspektor angezeigt:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

Wenn Sie ein MixedRealityToolkitConfigurationProfile-Medienobjekt ohne mixedRealityToolkit in der Szene auswählen, werden Sie gefragt, ob das MRTK die Szene automatisch für Sie einrichten soll. Dies ist optional. Es muss jedoch ein aktives MixedRealityToolkit-Objekt in der Szene vorhanden sein, um auf alle Konfigurationsbildschirme zugreifen zu können.

Hier ist die aktuelle aktive Laufzeitkonfiguration für das Projekt angegeben.

Von hier aus können Sie zu allen Konfigurationsprofilen für das MRTK navigieren, einschließlich:

- [Konfigurationsleitfaden für Mixed Reality Toolkit-Profile](#mrtk-profile-configuration-guide)
  - [Das Hauptkonfigurationsprofil für Mixed Reality Toolkit](#the-main-mixed-reality-toolkit-configuration-profile)
  - [Einstellungen für die Benutzererfahrung](#experience-settings)
  - [Kameraeinstellungen](#camera-settings)
  - [Einstellungen des Eingabesystems](#input-system-settings)
  - [Einstellungen für die Begrenzungsvisualisierung](#boundary-visualization-settings)
  - [Teleportation-Systemauswahl](#teleportation-system-selection)
  - [Einstellungen für räumliche Wahrnehmung](#spatial-awareness-settings)
  - [Diagnoseeinstellungen](#diagnostics-settings)
  - [Einstellungen des Szenensystems](#scene-system-settings)
  - [Zusätzliche Diensteinstellungen](#additional-services-settings)
  - [Einstellungen für Eingabeaktionen](#input-actions-settings)
  - [Regeln für Eingabeaktionen](#input-actions-rules)
  - [Zeigerkonfiguration](#pointer-configuration)
  - [Gestenkonfiguration](#gestures-configuration)
  - [Sprachbefehle](#speech-commands)
  - [Konfiguration der Controllerzuordnung](#controller-mapping-configuration)
  - [Controllervisualisierungseinstellungen](#controller-visualization-settings)
  - [Editor-Hilfsprogramme](#editor-utilities)
    - [Dienstinspektoren](#service-inspectors)
    - [Tiefenpufferrenderer](#depth-buffer-renderer)
  - [Ändern von Profilen zur Laufzeit](#changing-profiles-at-runtime)
    - [Pre MRTK initialization profile switch (Prä-MRTK-Initialisierungsprofilschalter)](#pre-mrtk-initialization-profile-switch)
    - [Aktiver Profilschalter](#active-profile-switch)
  - [Weitere Informationen](#see-also)

Diese Konfigurationsprofile werden unten in den entsprechenden Abschnitten ausführlich beschrieben:

---
<a name="experience"></a>

## <a name="experience-settings"></a>Einstellungen für die Benutzererfahrung

Auf der Hauptseite Mixed Reality Toolkit-Konfiguration definiert diese Einstellung den Standardvorgang der [Mixed Reality Umgebungsskalierung](/windows/mixed-reality/coordinate-systems-in-unity) für Ihr Projekt.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>Kameraeinstellungen

Die Kameraeinstellungen definieren, wie die Kamera für Ihr Mixed Reality Projekt eingerichtet wird, und definieren die generischen Einstellungen für Clipping, Qualität und Transparenz.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>Einstellungen des Eingabesystems

Die Mixed Reality Project bietet ein robustes und gut trainiertes Eingabesystem zum Weiterleiten aller Eingabeereignisse um das Projekt, das standardmäßig ausgewählt ist.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

Hinter dem vom MRTK bereitgestellten Eingabesystem befinden sich mehrere andere Systeme, die dazu beitragen, die komplexen Verschränkungen zu steuern und zu verwalten, die erforderlich sind, um die Komplexität eines Multiplattform-/Mixed Reality-Frameworks zu abstrahieren.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

Jedes der einzelnen Profile wird im Folgenden ausführlich beschrieben:

- Fokus Einstellungen
- [Einstellungen für Eingabeaktionen](#input-actions-settings)
- [Regeln für Eingabeaktionen](#input-actions-rules)
- [Zeigerkonfiguration](#pointer-configuration)
- [Gestenkonfiguration](#gestures-configuration)
- [Sprachbefehle](#speech-commands)
- [Konfiguration der Controllerzuordnung](#controller-mapping-configuration)
- [Controllervisualisierungseinstellungen](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>Einstellungen für die Begrenzungsvisualisierung

Das Begrenzungssystem übersetzt die erkannte Grenze, die vom zugrunde liegenden Plattformbegrenzungs-/Wächtersystem gemeldet wird. Die Konfiguration der Begrenzungsschnellansicht bietet Ihnen die Möglichkeit, die aufgezeichnete Grenze in Ihrer Szene relativ zur Position des Benutzers automatisch anzuzeigen. Die Grenze reagiert/aktualisiert auch basierend darauf, wo der Benutzer in der Szene teleportiert.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>Teleportation-Systemauswahl

Die Mixed Reality Project bietet ein voll funktionsfähiges Teleportation-System für die Verwaltung von Teleportierungsereignissen im Projekt, das standardmäßig ausgewählt ist.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>Einstellungen für räumliche Wahrnehmung

Der Mixed Reality Project stellt ein neu erstelltes Räumliches Wahrnehmungssystem für die Arbeit mit räumlichen Scansystemen im Projekt bereit, das standardmäßig ausgewählt ist.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

Mit der Mixed Reality Toolkit-Konfiguration für räumliche Wahrnehmung können Sie anpassen, wie das System gestartet wird, unabhängig davon, ob es automatisch beim programmgesteuerten Start der Anwendung oder später erfolgt, sowie die Erweiterungen für das Sichtfeld festlegen.

Außerdem können Sie die Gitternetz- und Oberflächeneinstellungen konfigurieren und so weiter anpassen, wie Ihr Projekt die Umgebung um Sie herum versteht.

Dies gilt nur für Geräte, die eine gescannte Umgebung bereitstellen können.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>Diagnoseeinstellungen

Ein optionales, aber äußerst nützliches Feature des MRTK ist die Plug-In-Diagnosefunktion.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

Das Diagnoseprofil bietet mehrere einfache Systeme, die überwacht werden können, während das Projekt ausgeführt wird, einschließlich eines praktischen Ein/Aus-Schalters zum Aktivieren/Deaktivieren des Anzeigebereichs in der Szene.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>Einstellungen des Szenensystems

Das MRTK bietet diesen optionalen Dienst, mit dem Sie komplexes Laden/Entladen von additiven Szenen verwalten können. Wenn Sie entscheiden möchten, ob das Szenensystem für Ihr Projekt geeignet ist, lesen Sie scene [system Erste Schritte Guide (Scene System Erste Schritte Guide).](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>Zusätzliche Diensteinstellungen

Einer der fortgeschritteneren Bereiche des Mixed Reality Toolkits ist die Implementierung des [Dienstlocatormusters,](https://en.wikipedia.org/wiki/Service_locator_pattern) die die Registrierung eines beliebigen "Diensts" beim Framework ermöglicht. Dadurch kann das Framework problemlos um neue Features/Systeme erweitert werden, aber projekte können diese Funktionen auch nutzen, um ihre eigenen Laufzeitkomponenten zu registrieren.

Jeder registrierte Dienst erhält weiterhin den vollständigen Vorteil aller Unity-Ereignisse, ohne den Aufwand und die Kosten für die Implementierung eines MonoBehaviour- oder clunky-Singletonmusters. Dies ermöglicht reine C#-Komponenten ohne Szenenaufwand für die Ausführung von Vordergrund- und Hintergrundprozessen, z. B. Spawningsysteme, Laufzeitspiellogik oder praktisch alles andere.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>Einstellungen für Eingabeaktionen

Eingabeaktionen bieten eine Möglichkeit, physische Interaktionen und Eingaben aus einem Laufzeitprojekt zu abstrahieren. Alle physischen Eingaben (von Controllern/ Händen / Maus usw.) werden in eine logische Eingabeaktion übersetzt, um sie in Ihrem Laufzeitprojekt zu verwenden. Dadurch wird sichergestellt, dass Ihr Projekt unabhängig davon, woher die Eingabe stammt, diese Aktionen einfach als "Dinge zu tun" oder "Interagieren mit" in Ihren Szenen implementiert.

Um eine neue Eingabeaktion zu erstellen, klicken Sie einfach auf die Schaltfläche "Neue Aktion hinzufügen", und geben Sie einen Anzeigetextnamen für das ein, was sie darstellt. Sie müssen dann nur eine Achse (den Typ der Daten) auswählen, die die Aktion vermitteln soll, oder im Fall von physischen Controllern den physischen Eingabetyp, an den sie angefügt werden kann, z. B.:

| Achseneinschränkung | Datentyp | Beschreibung | Beispielverwendung |
| :--- | :--- | :--- | :--- |
| Keine | Keine Daten | Wird für eine leere Aktion oder ein leeres Ereignis verwendet. | Ereignistrigger |
| Rohdaten (reserviert) | Objekt (object) | Für die zukünftige Verwendung reserviert | – |
| Digital | bool | Ein boolescher Wert für Daten vom Typ "On" oder "Off" | Schaltfläche "Controller" |
| Einzelne Achse | float | Ein einzelner Genauigkeitsdatenwert | Eine Bereichseingabe, z. B. ein Trigger |
| Duale Achse | Vector2 | Ein duales Float-Typdatum für mehrere Achsen | Ein Dpad oder Thumbstick |
| Drei Dof-Positionen | Vector3 | Positionstypdaten von mit 3 Gleitkommaachsen | Nur 3D-Positionsformatcontroller |
| Drei Dof-Drehungen | Quaternion | Nur Drehungseingabe mit 4 Gleitkommaachsen | Ein Controller im Stil von drei Grad, z. B. Oculus Go-Controller |
| Sechs Dof | Mixed Reality Pose (Vector3, Quaternion) | Eingabe im Stil "Position" und "Drehung" mit Vector3- und Quaternion-Komponenten | Ein Bewegungscontroller oder Zeiger |

Ereignisse, die Eingabeaktionen verwenden, sind nicht auf physische Controller beschränkt und können weiterhin innerhalb des Projekts verwendet werden, damit Laufzeiteffekte neue Aktionen generieren.

> [!NOTE]
> Eingabeaktionen sind eine der wenigen Komponenten, die zur Laufzeit nicht bearbeitet werden können, sondern nur eine Entwurfszeitkonfiguration. Dieses Profil sollte nicht ausgetauscht werden, während das Projekt ausgeführt wird, da das Framework (und Ihre Projekte) von den für jede Aktion generierten IDs abhängig sind.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>Regeln für Eingabeaktionen

Eingabeaktionsregeln bieten eine Möglichkeit, ein Ereignis, das für eine Eingabeaktion in ausgelöst wird, basierend auf seinem Datenwert automatisch in verschiedene Aktionen zu übersetzen. Diese werden nahtlos innerhalb des Frameworks verwaltet und verursachen keine Leistungskosten.

Beispiel: Konvertieren des Eingabeereignisses mit einer einzelnen Doppelachse von einem DPad in die 4 entsprechenden Aktionen "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" (wie in der folgenden Abbildung dargestellt).

Dies kann auch in Ihrem eigenen Code erfolgen. Da dies jedoch ein sehr gängiges Muster war, stellt das Framework einen Mechanismus bereit, um dies "sofort zu erledigen".

EingabeaktionSregeln können für jede verfügbare Eingabeachse konfiguriert werden. Eingabeaktionen eines Achsentyps können jedoch in eine andere Eingabeaktion desselben Achsentyps übersetzt werden. Sie können eine Aktion mit zwei Achsen einer anderen Aktion mit zwei Achsen zuordnen, aber nicht einer digitalen oder keiner Aktion.

![Profil für Eingabeaktionsregeln](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>Zeigerkonfiguration

Zeiger werden verwendet, um interaktivität in der Szene von einem beliebigen Eingabegerät aus zu steuern, wodurch sowohl ein Richtungs- als auch ein Treffertest mit jedem Objekt in einer Szene (das einen Collider angefügt hat oder eine Benutzeroberflächenkomponente ist) gibt. Zeiger werden standardmäßig automatisch für Controller, Headsets (Anvieren/Fokus) und Maus-/Toucheingaben konfiguriert.

Zeiger können auch innerhalb der aktiven Szene mithilfe einer der vielen vom Mixed Reality Toolkit bereitgestellten Linienkomponenten visualisiert werden, oder mit einer eigenen, wenn sie die MRTK IMixedRealityPointer-Schnittstelle implementieren.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- Zeigendes Ausmaß: Bestimmt den globalen Zeigendpunkt für alle Zeiger, einschließlich anvisierter Blicke.
- Verweisen auf Raycastebenenmasken: Bestimmt, für welche Ebenen Zeiger raycasting ausgeführt werden.
- Debuggen von Draw Pointing Rays: Ein Debughilfsgerät zum Visualisieren des Lichtstrahls, der für raycasting verwendet wird.
- Debuggen von Zeichnen zeigender Lichtstrahlfarben: Eine Gruppe von Farben, die zum Visualisieren verwendet werden sollen.
- Prefab des Anvisierenscursors: Erleichtert die Angabe eines globalen Anvisierenscursors für jede Szene.

Es gibt eine zusätzliche Hilfsschaltfläche, mit der Sie schnell zum Gaze-Anbieter springen können, um bei Bedarf bestimmte Werte für Gaze zu überschreiben.

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>Gestenkonfiguration

Gesten sind eine systemspezifische Implementierung, mit der Sie Eingabeaktionen den verschiedenen Eingabemethoden "Gesten" zuweisen können, die von verschiedenen SDKs (z. B. HoloLens) bereitgestellt werden.

> [!NOTE]
> Die aktuelle Gestenimplementierungen gelten nur für die HoloLens und werden für andere Systeme verbessert, da sie dem Toolkit in Zukunft hinzugefügt werden (noch keine Datumsangaben).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>Sprachbefehle

Wie Gesten bieten auch einige Laufzeitplattformen intelligente "Spracherkennung"-Funktionen mit der Möglichkeit, Befehle zu generieren, die von einem Unity-Projekt empfangen werden können. Mit diesem Konfigurationsprofil können Sie Folgendes konfigurieren:

1. Allgemeine Einstellungen: "Startverhalten", das auf Automatischer Start oder manueller Start festgelegt ist, bestimmt, ob KeywordRecognizer beim Start des Eingabesystems initialisiert werden soll oder ob das Projekt entscheiden soll, wann keywordRecognizer initialisiert werden soll. "Recognition Confidence Level" wird verwendet, um die [KeywordRecognizer-API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) von Unity zu initialisieren.
2. Sprachbefehle: Registriert "Wörter" und übersetzt sie in Eingabeaktionen, die von Ihrem Projekt empfangen werden können. Sie können bei Bedarf auch an Tastaturaktionen angefügt werden.

> [!IMPORTANT]
> Das System unterstützt sprache derzeit nur bei der Ausführung auf Windows 10 Plattformen, z. B. HoloLens und Windows 10 Desktop, und wird für andere Systeme erweitert, da sie in Zukunft dem MRTK hinzugefügt werden (noch keine Datumsangaben).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>Konfiguration der Controllerzuordnung

Einer der Hauptkonfigurationsbildschirme für das Mixed Reality Toolkit ist die Möglichkeit, die verschiedenen Controllertypen zu konfigurieren und zuzuordnen, die von Ihrem Projekt verwendet werden können.

Auf dem folgenden Konfigurationsbildschirm können Sie alle Controller konfigurieren, die derzeit vom Toolkit erkannt werden.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

Das MRTK stellt eine Standardkonfiguration für die folgenden Controller/Systeme bereit:

- Maus (einschließlich 3D-Unterstützung für räumliche Maus)
- Touch Screen
- Xbox-Controller
- Windows Mixed Reality Controller
- HoloLens Gesten
- ICE Vive-Reglercontroller
- Oculus Touch-Controller
- Oculus-Remotecontroller
- Generische OpenVR-Geräte (nur fortgeschrittene Benutzer)

Wenn Sie für eines der vordefinierten Controllersysteme auf das Image klicken, können Sie eine einzelne Eingabeaktion für alle zugehörigen Eingaben konfigurieren. Sehen Sie sich beispielsweise den Konfigurationsbildschirm oculus touch controller unten an:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

Es gibt auch einen erweiterten Bildschirm zum Konfigurieren anderer OpenVR- oder Unity-Eingabecontroller, die oben nicht identifiziert wurden.

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>Controllervisualisierungseinstellungen

Zusätzlich zur Controllerzuordnung wird ein separates Konfigurationsprofil bereitgestellt, um anzupassen, wie Ihre Controller in Ihren Szenen dargestellt werden.

Dies kann auf einem "Globalen" (alle Instanzen eines Controllers für eine bestimmte Hand) oder spezifisch für einen einzelnen Controllertyp/eine einzelne Hand konfiguriert werden.

Das MRTK unterstützt auch native SDK-Controllermodelle für Windows Mixed Reality und OpenVR. Diese werden als GameObjects in Ihre Szene geladen und mithilfe der Controllernachverfolgung der Plattform positioniert.

Wenn Ihre Controllerdarstellung in der Szene von der physischen Controllerposition versetzt werden muss, legen Sie diesen Offset einfach auf das Prefab des Controllermodells fest (z. B. festlegen der Transformationsposition des Controller-Prefabs mit einer Offsetposition).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>Editor-Hilfsprogramme

Die folgenden Hilfsprogramme funktionieren nur im Editor und sind nützlich, um die Entwicklungsproduktivität zu verbessern.

![MRTK-Editor- Konfigurations-Hilfsprogramme](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>Dienstinspektoren

Dienstinspektoren sind ein Nur-Editor-Feature, das Objekte in der Szene generiert, die aktive Dienste darstellen. Wenn Sie diese Objekte auswählen, werden Inspektoren angezeigt, die Dokumentationslinks, Die Kontrolle über Editorvisualisierungen und Einblicke in den Status des Diensts bieten.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

Sie können Dienstinspektoren aktivieren, indem *Sie dienstinspektoren verwenden* unter *Editor Einstellungen* im Konfigurationsprofil aktivieren.

### <a name="depth-buffer-renderer"></a>Tiefenpufferrenderer

Die Gemeinsame Nutzung des Tiefenpuffers mit einigen Mixed Reality-Plattformen kann die [Hologrammunterdärkung](../performance/hologram-stabilization.md)verbessern. Beispielsweise kann die Windows Mixed Reality Plattform die gerenderte Szene pro Pixel ändern, um geringfügige Kopfbewegungen während der Zeit zu berücksichtigen, die zum Rendern eines Frames gedauert hat. Diese Techniken erfordern jedoch Tiefenpuffer mit genauen Daten, um zu wissen, wo und wie weit die Geometrie vom Benutzer entfernt ist.

Um sicherzustellen, dass eine Szene alle erforderlichen Daten im Tiefenpuffer rendert, können Entwickler die Funktion *Tiefenpuffer rendern* unter *Editor Einstellungen* im Konfigurationsprofil umschalten. Dadurch wird der aktuelle Tiefenpuffer als Farbe für die Szenenansicht gerendert, indem der Nachbearbeitungseffekt auf die Hauptkamera angewendet [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) wird.

![Hilfsprogramm für Rendertiefepuffer ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>Der blaue Zylinder in der Szene weist ein Material mit ZWrite auf, sodass keine Tiefendaten geschrieben werden.</sup>

## <a name="changing-profiles-at-runtime"></a>Ändern von Profilen zur Laufzeit

Es ist möglich, Profile zur Laufzeit zu aktualisieren, und es gibt im Allgemeinen zwei verschiedene Szenarien und Zeiten, in denen dies hilfreich ist:

1. **Pre MRTK initialization profile switch (Prä-MRTK-Initialisierungsprofilwechsel):** Beim Start, bevor das MRTK initialisiert wird und das Profil aktiv wird. Ersetzen Sie dabei das noch nicht genutzte Profil, um verschiedene Features basierend auf den Gerätefunktionen zu aktivieren/deaktivieren. Wenn die Umgebung beispielsweise in VR ausgeführt wird, die keine Hardware für räumliche Zuordnungen hat, ist es wahrscheinlich nicht sinnvoll, die Komponente für die räumliche Zuordnung zu aktivieren.
1. **Aktiver Profilwechsel:** Nachdem das MRTK initialisiert wurde und ein Profil aktiv wurde, tauschen Sie das aktuell verwendete Profil aus, um das Verhalten bestimmter Features zu ändern. Es kann z. B. eine bestimmte untergeordnete Benutzeroberfläche in der Anwendung geben, die entfernte Fernzeiger vollständig entfernen möchte.

### <a name="pre-mrtk-initialization-profile-switch"></a>Pre MRTK initialization profile switch (Prä-MRTK-Initialisierungsprofilschalter)

Dies kann durch Anfügen eines MonoBehaviour (Beispiel unten) erreicht werden, das vor der MRTK-Initialisierung (d. h. "Awake()") ausgeführt wird. Beachten Sie, dass das Skript (d. h. der Aufruf von ) vor dem Skript ausgeführt werden muss. Dies kann durch Festlegen der Einstellungen für die `SetProfileBeforeInitialization` `MixedRealityToolkit` Skriptausführungs reihenfolge erreicht [werden.](https://docs.unity3d.com/Manual/class-MonoManager.html)

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

Anstelle von "profileToUse" ist es möglich, einen beliebigen Satz von Profilen zu verwenden, die für bestimmte Plattformen gelten (z. B. eines für HoloLens 1, eines für VR, eines für HoloLens 2 usw.). Es ist möglich, verschiedene andere Indikatoren (z. B. oder ob die Kamera nicht transparent ist) zu verwenden, um herauszufinden, welches Profil https://docs.unity3d.com/ScriptReference/SystemInfo.html geladen werden soll.

### <a name="active-profile-switch"></a>Aktiver Profilschalter

Dies kann durch Festlegen der -Eigenschaft `MixedRealityToolkit.Instance.ActiveProfile` auf ein neues Profil erreicht werden, das das aktive Profil ersetzt.

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

Beachten Sie, dass beim Festlegen während der Laufzeit die Zerstörung der derzeit ausgeführten Dienste nach dem letzten LateUpdate() aller Dienste und die Instanziierung und Initialisierung der Dienste, die dem neuen Profil zugeordnet sind, vor dem ersten Update() aller Dienste ausgeführt `ActiveProfile` wird.

Während dieses Prozesses kann eine spürbare Anwendungshregung auftreten. Außerdem kann jedes Skript mit einer höheren Priorität als das Skript das Update eingeben, `MixedRealityToolkit` bevor das neue Profil ordnungsgemäß eingerichtet wird. Weitere [Informationen zur Skriptpriorität](https://docs.unity3d.com/Manual/class-MonoManager.html) finden Sie unter Skriptausführungsauftragseinstellungen.

Während des Profilwechselprozesses bleibt die vorhandene UI-Kamera unverändert, um sicherzustellen, dass Unity UI-Komponenten, die Canvas erfordern, auch nach dem Wechsel weiterhin funktionieren.

## <a name="see-also"></a>Siehe auch

- [Hologramm-Stabilität](../performance/hologram-stabilization.md)
