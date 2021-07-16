---
title: Upgrade von HoloToolkit
description: Migration vom HoloLens Toolkit (HTK) zum Mixed Reality Toolkit (MRTK).
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, HTK,
ms.openlocfilehash: b54445dc5ca7a6c01c968929e243a1fc4ca2d107
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281758"
---
# <a name="upgrading-from-holotoolkit"></a>Upgrade von HoloToolkit

Ein Leitfaden, der Sie bei der Migration vom HoloLens Toolkit (HTK) zum Mixed Reality Toolkit (MRTK) unterstützt.

## <a name="controller-and-hand-input"></a>Controller- und Handeingabe

### <a name="setup-and-configuration"></a>Setup und Konfiguration

|         Methoden                  | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Typ                      | Bestimmte Ereignisse für Schaltflächen mit Eingabetypinformationen, falls relevant. | Aktions-/gestenbasierte Eingabe, die über Ereignisse übergeben wird. |
| Setup                     | Platzieren Sie den InputManager in der Szene. | Aktivieren Sie das Eingabesystem im [Konfigurationsprofil, und](../configuration/mixed-reality-configuration-guide.md) geben Sie einen konkreten Eingabesystemtyp an. |
| Konfiguration             | Konfiguriert im Inspektor für jedes einzelne Skript in der Szene. | Konfiguriert über das Mixed Reality Eingabesystemprofil und das zugehörige Profil, die unten aufgeführt sind. |

Verwandte Profile:

* Mixed Reality Controllerzuordnungsprofil
* Mixed Reality Controllervisualisierungsprofil
* Mixed Reality Gestenprofil
* Mixed Reality Profil für Eingabeaktionen
* Mixed Reality Profil für Eingabeaktionsregeln
* Mixed Reality Zeigerprofil

[Die Einstellungen des](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) Anvitätsanbieters werden für das Hauptkameraobjekt in der Szene geändert.

Plattformunterstützungskomponenten (z. B. Windows Mixed Reality Geräte-Manager) müssen den Entsprechenden Datenanbietern des Diensts hinzugefügt werden.

### <a name="interface-and-event-mappings"></a>Schnittstellen- und Ereigniszuordnungen

Einige Ereignisse verfügen nicht mehr über eindeutige Ereignisse und enthalten jetzt [eine MixedRealityInputAction.](../features/input/input-actions.md) Diese Aktionen werden im Profil Eingabeaktionen angegeben und bestimmten Controllern und Plattformen im Profil Controllerzuordnung zugeordnet. Ereignisse wie `OnInputDown` sollten nun den MixedRealityInputAction-Typ überprüfen.

Verwandte Eingabesysteme:

* [Übersicht über die Eingabe](../features/input/overview.md)
* [Eingabeereignisse](../features/input/input-events.md)
* [Eingabezeker](../features/input/pointers.md)

| HTK 2017 |  MRTK v2  | Aktionszuordnung |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Dem Touchpad oder Thumbstick zugeordnet |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Dem Touchpad zugeordnet |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Zugeordnet, um im Gestenprofil zu halten |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Zugeordnet zu den Schaltflächen des Controllers oder Tippen mit der Hand |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Zuordnung zur Bearbeitung im Gestenprofil |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Zugeordnet zur Navigation im Gestenprofil |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Der Triggerposition zugeordnet |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) oder [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Zugeordnet zur Zeiger- oder Greifposition |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) oder [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Zugeordnet zur Zeiger- oder Greifposition |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) und [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Zugeordnet zu den verschiedenen Controllerschaltflächen und -sticks |

## <a name="camera"></a>Kamera

|        Methoden                    | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Setup                     | Löschen Sie MainCamera, fügen Sie der Szene das Prefab MixedRealityCameraParent/MixedRealityCamera/HoloLensCamera hinzu, oder verwenden Sie Mixed Reality Toolkit > Configure > Apply Mixed Reality Scene Einstellungen menu item (Konfigurieren von > Apply Mixed Reality Scene Einstellungen).  | MainCamera unter MixedRealityPlayspace über Mixed Reality Toolkit > Zu Szene hinzufügen und konfigurieren... |
| Konfiguration             | Konfiguration der Kameraeinstellungen, die für die Prefab-Instanz ausgeführt wird. | Kameraeinstellungen, die im Profil Mixed Reality-Kamera [konfiguriert sind.](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile) |

## <a name="speech"></a>Spracheingabe/-ausgabe

### <a name="keyword-recognition"></a>Schlüsselworterkennung

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Setup                     | Fügen Sie Ihrer Szene eine SpeechInputSource hinzu. | Der Schlüsselwortdienst (z. B. Windows Speech Input Manager) muss den Datenanbietern des Eingabesystems hinzugefügt werden. |
| Konfiguration             | Erkannte Schlüsselwörter werden im Inspektor von SpeechInputSource konfiguriert. | Schlüsselwörter werden im Profil Mixed Reality [Speech-Befehle konfiguriert.](../features/input/speech.md) |
| Ereignishandler            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>Diktieren

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Setup                     | Fügen Sie Ihrer Szene einen DictationInputManager hinzu. | Die Unterstützung von Diktaten erfordert, dass der Dienst (z. B. Windows Diktateingabe-Manager) den Datenanbietern des Eingabesystems hinzugefügt wird. |
| Ereignishandler            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>Räumliche Wahrnehmung/Zuordnung

### <a name="mesh"></a>Mesh

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Setup                     | Fügen Sie der Szene das Prefab SpatialMapping hinzu. | Aktivieren Sie das Spatial Awareness System im Konfigurationsprofil, und fügen Sie den Datenanbietern des Spatial Awareness Systems einen räumlichen Beobachter (z. B. Windows Mixed Reality Spatial Mesh Observer) hinzu. |
| Konfiguration             | Konfigurieren Sie die Szeneninstanz im Inspektor. | Konfigurieren Sie die Einstellungen für das Profil jedes räumlichen Beobachters. |

### <a name="planes"></a>Flugzeuge

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Setup                     | Verwenden Sie das `SurfaceMeshesToPlanes` Skript. | Noch nicht implementiert. |

### <a name="spatial-understanding"></a>Räumliches Verständnis

|       Methoden                      | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Setup                     | Fügen Sie der Szene das Prefab SpatialUnderstanding hinzu. | Noch nicht implementiert. |
| Konfiguration             | Konfigurieren Sie die Szeneninstanz im Inspektor. | Noch nicht implementiert. |

## <a name="boundary"></a>Grenze

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Setup                     | Fügen Sie `BoundaryManager` das Skript der Szene hinzu. | Aktivieren Sie das Begrenzungssystem im Konfigurationsprofil. |
| Konfiguration             | Konfigurieren Sie die Szeneninstanz im Inspektor. | Konfigurieren Sie die Einstellungen im Profil Begrenzungsvisualisierung. |

## <a name="sharing"></a>Freigabe

|             Methoden               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Setup                     | Freigabedienst: Fügen Sie der Szene Freigabe-Prefab hinzu. UNet: Verwenden Sie das Beispiel SharingWithUNET. | Wird ausgeführt |
| Konfiguration             | Konfigurieren Sie die Szeneninstanzen im Inspektor. | Wird ausgeführt |

## <a name="ux"></a>UX

|         Methoden                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Schaltfläche                     | [Interagierbare Objekte](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Schaltfläche](../features/ux-building-blocks/Button.md) |
| Interaktionsfähig                     | [Interagierbare Objekte](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Interaktionsfähig](../features/ux-building-blocks/Interactable.md) |
| Umgebendes Feld             | [Begrenzungsrahmen](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Begrenzungsrahmen](../features/ux-building-blocks/bounding-box.md) |
| App-Leiste             | [App-Leiste](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [App-Leiste](../features/ux-building-blocks/app-bar.md) |
| One-Hand-Manipulation (Grb und Move)   | [HandDraggable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [Manipulationshandler](../features/ux-building-blocks/manipulation-handler.md) |
| Zwei handige Manipulation (Greifen/Verschieben/Drehen/Skalieren)             | [TwoHandManipulatable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [Manipulationshandler](../features/ux-building-blocks/manipulation-handler.md) |
| Tastatur             | [Tastatur-Prefab]() | [Systemtastatur](../features/ux-building-blocks/system-keyboard.md) |
| QuickInfo             | [QuickInfo](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_TooltipExample.md) | [QuickInfo](../features/ux-building-blocks/tooltip.md) |
| Objektsammlung             | [Objektsammlung](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md) | [Objektsammlung](../features/ux-building-blocks/object-collection.md) |
| Solver             | [Solver](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/README_SolverSystem.md) | [Solver](../features/ux-building-blocks/solvers/solver.md) |

## <a name="utilities"></a>Hilfsprogramme

Einige Hilfsprogramme wurden als Duplikate mit dem Solver-System abgestimmt. Melden Sie ein Problem, wenn eines der benötigten Skripts fehlt.

| HTK 2017 |  MRTK v2  |
|----------|-----------|
| Billboard | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Tagalong | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) oder [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [Solver](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[Solver](../features/ux-building-blocks/solvers/solver.md) |
| FpsDisplay | [Diagnosesystem](../features/diagnostics/diagnostics-system-getting-started.md) (im Konfigurationsprofil) |
| NearFade | Integriert in Mixed Reality [Toolkit Standard-Shader](../features/rendering/mrtk-standard-shader.md) |
