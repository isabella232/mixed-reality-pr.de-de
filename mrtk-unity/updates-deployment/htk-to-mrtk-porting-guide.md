---
title: Leitfaden zur Portierung von HTK zu MRTK
description: Migration vom HoloLens Toolkit (HTK) zum Mixed Reality Toolkit (MRTK).
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, HTK,
ms.openlocfilehash: fbcb2863c894a4e4c1529e19112b33712f69e99f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143761"
---
# <a name="porting-guide"></a>Portierungsleitfaden

Ein Leitfaden, der Sie bei der Migration vom HoloLens Toolkit (HTK) zum Mixed Reality Toolkit (MRTK) unterstützt.

## <a name="controller-and-hand-input"></a>Controller- und Handeingabe

### <a name="setup-and-configuration"></a>Setup und Konfiguration

|         Methoden                  | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| type                      | Bestimmte Ereignisse für Schaltflächen mit Eingabetypinformationen, falls relevant. | Aktions-/gestenbasierte Eingabe, die über Ereignisse übergeben wird. |
| Einrichten                     | Platzieren Sie den InputManager in der Szene. | Aktivieren Sie das Eingabesystem im [Konfigurationsprofil, und](../configuration/mixed-reality-configuration-guide.md) geben Sie einen konkreten Eingabesystemtyp an. |
| Konfiguration             | Konfiguriert im Inspektor für jedes einzelne Skript in der Szene. | Konfiguriert über das Mixed Reality Eingabesystemprofil und das zugehörige Profil, die unten aufgeführt sind. |

Verwandte Profile:

* Mixed Reality Controllerzuordnungsprofil
* Mixed Reality Controllervisualisierungsprofil
* Mixed Reality Gestenprofil
* Mixed Reality Profil für Eingabeaktionen
* Mixed Reality Profil für Eingabeaktionsregeln
* Mixed Reality Zeigerprofil

Die Einstellungen des [Anvischen-Anbieters](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) werden für das Hauptkameraobjekt in der Szene geändert.

Plattformunterstützungskomponenten (z.B. Windows Mixed Reality Geräte-Manager) müssen den Datenanbietern des entsprechenden Diensts hinzugefügt werden.

### <a name="interface-and-event-mappings"></a>Schnittstellen- und Ereigniszuordnungen

Einige Ereignisse haben keine eindeutigen Ereignisse mehr und enthalten jetzt eine [MixedRealityInputAction](../features/input/input-actions.md). Diese Aktionen werden im Profil Eingabeaktionen angegeben und bestimmten Controllern und Plattformen im Controllerzuordnungsprofil zugeordnet. Ereignisse wie `OnInputDown` sollten jetzt den MixedRealityInputAction-Typ überprüfen.

Verwandte Eingabesysteme:

* [Übersicht über die Eingabe](../features/input/overview.md)
* [Eingabeereignisse](../features/input/input-events.md)
* [Eingabezeiger](../features/input/pointers.md)

| HTK 2017 |  MRTK v2  | Aktionszuordnung |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Zugeordnet zum Touchpad oder Thumbstick |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Dem Touchpad zugeordnet |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Zugeordnet zum Halten im Gestenprofil |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Zugeordnet zu den Schaltflächen des Controllers oder Tippen mit der Hand |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Der Bearbeitung im Gestenprofil zugeordnet |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Der Navigation im Gestenprofil zugeordnet |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Zugeordnet zur Triggerposition |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) oder [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Zugeordnet zur Zeigerposition oder Klammerposition |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) oder [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Zugeordnet zur Zeigerposition oder Klammerposition |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) und [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Zugeordnet zu den verschiedenen Controllerschaltflächen und -sticks |

## <a name="camera"></a>Kamera

|        Methoden                    | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Einrichten                     | Löschen Sie MainCamera, fügen Sie der Szene das Prefab MixedRealityCameraParent/MixedRealityCamera/HoloLensCamera hinzu, oder verwenden Sie Mixed Reality Toolkit > Configure > Apply Mixed Reality Scene Settings (Mixed Reality-Szeneneinstellungen anwenden).  | MainCamera unter MixedRealityPlayspace über Mixed Reality Toolkit > Zu Szene hinzufügen und konfigurieren... |
| Konfiguration             | Konfiguration der Kameraeinstellungen, die für die Prefab-Instanz ausgeführt wird. | Kameraeinstellungen, die im Profil Mixed Reality-Kamera [konfiguriert sind.](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile) |

## <a name="speech"></a>Spracheingabe/-ausgabe

### <a name="keyword-recognition"></a>Schlüsselworterkennung

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Einrichten                     | Fügen Sie Ihrer Szene eine SpeechInputSource hinzu. | Der Schlüsselwortdienst (z. B. Der Windows Speech-Eingabe-Manager) muss den Datenanbietern des Eingabesystems hinzugefügt werden. |
| Konfiguration             | Erkannte Schlüsselwörter werden im Inspektor von SpeechInputSource konfiguriert. | Schlüsselwörter werden im Mixed Reality [Speech-Befehlsprofil konfiguriert.](../features/input/speech.md) |
| Ereignishandler            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>Diktieren

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Einrichten                     | Fügen Sie Ihrer Szene einen DictationInputManager hinzu. | Für die Unterstützung von Diktaten muss den Datenanbietern des Eingabesystems ein Dienst (z. B. Der Eingabe-Manager für Windows-Diktat) hinzugefügt werden. |
| Ereignishandler            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>Räumliche Wahrnehmung/Zuordnung

### <a name="mesh"></a>Mesh

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Einrichten                     | Fügen Sie der Szene das SpatialMapping-Prefab hinzu. | Aktivieren Sie das Spatial Awareness System im Konfigurationsprofil, und fügen Sie den Datenanbietern des Räumlichen Wahrnehmungssystems einen räumlichen Beobachter (z. B. Windows Mixed Reality Spatial Mesh Observer) hinzu. |
| Konfiguration             | Konfigurieren Sie die Szeneninstanz im Inspektor. | Konfigurieren Sie die Einstellungen für das Profil jedes räumlichen Beobachters. |

### <a name="planes"></a>Flugzeuge

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Einrichten                     | Verwenden Sie das `SurfaceMeshesToPlanes` Skript. | Noch nicht implementiert. |

### <a name="spatial-understanding"></a>Räumliches Verständnis

|       Methoden                      | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Einrichten                     | Fügen Sie der Szene das Prefab SpatialUnderstanding hinzu. | Noch nicht implementiert. |
| Konfiguration             | Konfigurieren Sie die Szeneninstanz im Inspektor. | Noch nicht implementiert. |

## <a name="boundary"></a>Grenze

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Einrichten                     | Fügen Sie das `BoundaryManager` Skript der Szene hinzu. | Aktivieren Sie das Begrenzungssystem im Konfigurationsprofil. |
| Konfiguration             | Konfigurieren Sie die Szeneninstanz im Inspektor. | Konfigurieren Sie die Einstellungen im Profil Begrenzungsvisualisierung. |

## <a name="sharing"></a>Freigabe

|             Methoden               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Einrichten                     | Freigabedienst: Fügen Sie der Szene ein Freigabe-Prefab hinzu. UNet: Verwenden Sie das Beispiel SharingWithUNET. | Wird ausgeführt |
| Konfiguration             | Konfigurieren Sie die Szeneninstanzen im Inspektor. | Wird ausgeführt |

## <a name="ux"></a>UX

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Schaltfläche                     | [Interaktivierbare Objekte](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Button](../features/ux-building-blocks/Button.md) (Schaltfläche) |
| Interaktionsfähig                     | [Interaktivierbare Objekte](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Interaktionsfähig](../features/ux-building-blocks/Interactable.md) |
| Umgebendes Feld             | [Begrenzungsrahmen](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Begrenzungsrahmen](../features/ux-building-blocks/bounding-box.md) |
| App-Leiste             | [App-Leiste](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [App-Leiste](../features/ux-building-blocks/app-bar.md) |
| One-Hand-Manipulation (Grb und Move)   | [HandDraggable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [Manipulationshandler](../features/ux-building-blocks/manipulation-handler.md) |
| Zweihandbearbeitung (Greifen/Verschieben/Drehen/Skalieren)             | [TwoHandManipulatable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [Manipulationshandler](../features/ux-building-blocks/manipulation-handler.md) |
| Tastatur             | [Tastatur-Prefab]() | [Systemtastatur](../features/ux-building-blocks/system-keyboard.md) |
| QuickInfo             | [QuickInfo](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_TooltipExample.md) | [QuickInfo](../features/ux-building-blocks/tooltip.md) |
| Objektsammlung             | [Objektsammlung](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md) | [Objektsammlung](../features/ux-building-blocks/object-collection.md) |
| Solver             | [Solver](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/README_SolverSystem.md) | [Solver](../features/ux-building-blocks/solvers/solver.md) |

## <a name="utilities"></a>Versorgungsunternehmen

Einige Hilfsprogramme wurden als Duplikate mit dem Solver-System abgestimmt. Melden Sie ein Problem, wenn eines der benötigten Skripts fehlt.

| HTK 2017 |  MRTK v2  |
|----------|-----------|
| Billboard | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Tagalong | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) oder [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [Solver](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[Solver](../features/ux-building-blocks/solvers/solver.md) |
| FpsDisplay | [Diagnosesystem](../features/diagnostics/diagnostics-system-getting-started.md) (im Konfigurationsprofil) |
| NearFade | Integriert in Mixed Reality [Toolkit Standard-Shader](../features/rendering/mrtk-standard-shader.md) |
