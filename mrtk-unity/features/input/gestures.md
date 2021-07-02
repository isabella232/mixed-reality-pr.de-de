---
title: Gesten
description: Docummentation on Gestures and its events in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Gesten,
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176882"
---
# <a name="gestures"></a>Gesten

Gesten sind Eingabeereignisse, die auf menschlichen Händen basieren. Es gibt zwei Arten von Geräten, die Gesteneingabeereignisse im MRTK auslösen:

- Windows Mixed Reality Geräte wie HoloLens. Dies beschreibt das Eindrüpfen von Bewegungen ("Tippen in die Luft") und tipp-and-hold-Gesten.

  Weitere Informationen zu HoloLens Gesten finden Sie in der [Dokumentation zu Windows Mixed Reality Gesten.](/windows/mixed-reality/gestures)

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)umschließt unity [XR. WSA. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) zum Nutzen der Gestenereignisse von Unity von HoloLens Geräten.

- Touchscreengeräte.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) umschließt die [Unity Touch-Klasse,](https://docs.unity3d.com/ScriptReference/Touch.html) die physische Touchscreens unterstützt.

Beide Eingabequellen verwenden das _Gestenprofil Einstellungen,_ um die Touch- bzw. Gestenereignisse von Unity in die [Eingabeaktionen](input-actions.md)des MRTK zu übersetzen. Dieses Profil finden Sie unter dem _Profil Eingabesystem Einstellungen._

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>Gestikereignisse

Gestenereignisse werden empfangen, indem eine der Gestenhandlerschnittstellen implementiert wird: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) oder [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (siehe Tabelle der [Ereignishandler](input-events.md)).

Eine Beispielimplementierungen eines Gestenereignishandlers finden Sie unter [Beispielszene.](#example-scene)

Beim Implementieren der generischen Version können die Ereignisse *OnGestureCompleted* und *OnGestureUpdated* typisierte Daten der folgenden Typen empfangen:

- `Vector2` – 2D-Positionsgeste. Wird von Touchscreens erstellt, um über ihre zu [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) informieren.
- `Vector3` – 3D-Positionsgeste. Erstellt von HoloLens zur Information über:
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) eines Manipulationsereignisses
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) eines Navigationsereignisses
- `Quaternion` – 3D-Drehbewegung. Verfügbar für benutzerdefinierte Eingabequellen, aber derzeit nicht von vorhandenen Quellen erstellt.
- `MixedRealityPose` – Kombinierte 3D-Geste für Position/Drehung. Verfügbar für benutzerdefinierte Eingabequellen, aber derzeit nicht von vorhandenen Quellen erstellt.

## <a name="order-of-events"></a>Reihenfolge der Ereignisse

Je nach Benutzereingabe gibt es zwei Hauptketten von Ereignissen:

- "Hold":
    1. Halten Sie tippen:
        - Manipulation  starten
    1. Tippen Sie über [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)hinaus:
        - Start _Hold (Halten)_
    1. Tippen Sie auf Release:
        - Complete _Hold_
        - vollständige _Bearbeitung_

- "Move":
    1. Halten Sie tippen:
        - Manipulation  starten
    1. Tippen Sie über [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)hinaus:
        - Start _Hold (Halten)_
    1. Bewegen Sie die Hand über [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)hinaus:
        - _Abbrechen der Zurückhaltung_
        - Navigation  starten
    1. Tippen Sie auf Release:
        - vollständige _Bearbeitung_
        - vollständige _Navigation_

## <a name="example-scene"></a>Beispielszene

Die **Szene HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) zeigt, wie der Zeiger Result verwendet wird, um ein Objekt an der Trefferposition zu erstellen.

Das `GestureTester` Skript (Assets/MRTK/Examples/Demos/HandTracking/Script) ist eine Beispielimplementierung zum Visualisieren von Gestenereignissen über GameObjects. Die Handlerfunktionen ändern die Farbe von Indikatorobjekten und zeigen das letzte aufgezeichnete Ereignis in Textobjekten in der Szene an.
