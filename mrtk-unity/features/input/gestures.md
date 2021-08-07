---
title: Gesten
description: Docummentation on Gestures and its events in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Gesten,
ms.openlocfilehash: db6be5845c11efd5bfb199db9c53c867ea315f65bff0a799cd6bf63b9c50a3d1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209164"
---
# <a name="gestures"></a>Gesten

Gesten sind Eingabeereignisse, die auf menschlichen Händen basieren. Es gibt zwei Arten von Geräten, die Gesteneingabeereignisse im MRTK erstellen:

- Windows Mixed Reality Geräte wie HoloLens. Dies beschreibt das Anheften von Bewegungen ("Tippen in die Luft") und Tipp- und Halten-Gesten.

  Weitere Informationen zu Gesten HoloLens gesten finden Sie in der [Windows Mixed Reality Gestendokumentation.](/windows/mixed-reality/gestures)

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)umschließt [unity XR. WSA. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) zum Nutzen der Gestenereignisse von Unity von HoloLens Geräten.

- Touchscreengeräte.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) umschließt die [Unity Touch-Klasse,](https://docs.unity3d.com/ScriptReference/Touch.html) die physische Touchscreens unterstützt.

Beide Eingabequellen verwenden  das Gesten Einstellungen profil, um die Touch- bzw. Gestenereignisse von Unity in die Eingabeaktionen des MRTK [zu übersetzen.](input-actions.md) Dieses Profil finden Sie unter _dem Eingabesystem-Einstellungen_ Profil.

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>Gestikereignisse

Gestenereignisse werden empfangen, indem eine der Gestenhandlerschnittstellen implementiert [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) wird: oder [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (siehe Tabelle [der Ereignishandler](input-events.md)).

Eine [Beispielimplementierung](#example-scene) eines Gestenereignishandlers finden Sie unter Beispielszene.

Bei der Implementierung der generischen Version können die *Ereignisse OnGestureCompleted* und *OnGestureUpdated* typierte Daten der folgenden Typen empfangen:

- `Vector2` – 2D-Positionsgeste. Wird von Touchscreens erstellt, um über ihre zu [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) informieren.
- `Vector3` – 3D-Positionsgeste. Wird von HoloLens erstellt, um Über:
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) eines Manipulationsereignis
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) eines Navigationsereignis
- `Quaternion` – 3D-Drehbewegung. Verfügbar für benutzerdefinierte Eingabequellen, aber derzeit nicht von einer der vorhandenen Erstellt.
- `MixedRealityPose` – Kombinierte 3D-Position/Drehbewegung. Verfügbar für benutzerdefinierte Eingabequellen, aber derzeit nicht von einer der vorhandenen Erstellt.

## <a name="order-of-events"></a>Reihenfolge der Ereignisse

Je nach Benutzereingabe gibt es zwei Hauptketten von Ereignissen:

- "Hold":
    1. Tippen Sie auf halten:
        - Manipulation _starten_
    1. Tippen Sie über [HoldStartDuration hinaus:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - Start _hold_
    1. Tippen Sie auf das Release:
        - vollständige _Zurückhalten_
        - vollständige _Manipulation_

- "Move":
    1. Tippen Sie auf halten:
        - Manipulation _starten_
    1. Tippen Sie über [HoldStartDuration hinaus:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - Start _hold_
    1. Bewegen Sie hand über [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)hinaus:
        - Abbrechen _von "Hold"_
        - Navigation _starten_
    1. Tippen Sie auf das Release:
        - vollständige _Manipulation_
        - vollständige _Navigation_

## <a name="example-scene"></a>Beispielszene

Die **HandInteractionGestureEventsExample-Szene** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) zeigt, wie das Zeigerergebnis verwendet wird, um ein Objekt an der Trefferposition zu erstellen.

Das Skript (Assets/MRTK/Examples/Demos/HandTracking/Script) ist eine Beispielimplementierung zum Visualisieren von Gestenereignissen über `GestureTester` GameObjects. Die Handlerfunktionen ändern die Farbe von Indikatorobjekten und zeigen das zuletzt aufgezeichnete Ereignis in Textobjekten in der Szene an.
