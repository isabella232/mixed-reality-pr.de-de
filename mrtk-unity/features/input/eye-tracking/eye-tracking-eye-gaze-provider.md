---
title: 'Eyetracking (Blickverfolgung): Anbieter für Anvisieren (Gaze)'
description: Dokumentation zum Eye Gaze-Anbieter in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: 9a62bdba0bc4bb2985e6c2ffc4e8e66a8f867681a5e51c9e5f235b29f3baaf50
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193192"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>Zugreifen auf Eyetrackingdaten in Ihrem Unity-Skript

In diesem Artikel wird davon ausgegangen, dass sie über Kenntnisse zum Einrichten der Eyetracking in einer MRTK-Szene verfügt (siehe [Grundlegendes MRTK-Setup für die Verwendung von Eyetracking).](eye-tracking-basic-setup.md)
Der Zugriff auf Eyetrackingdaten in einem MonoBehaviour-Skript ist einfach! Verwenden Sie einfach *CoreServices.InputSystem.EyeGazeProvider*.

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

Die Eyetrackingkonfiguration im MRTK wird über die [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) -Schnittstelle konfiguriert. Die Verwendung von [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) stellt die Standardmäßige Implementierung des Anvischen-Anbieters bereit, die zur Laufzeit im Toolkit registriert ist.
Die nützlichen Eigenschaften von `EyeGazeProvider` sind unten beschrieben.

- **IsEyeTrackingEnabled:** True, wenn der Benutzer die Eyetracking für das Anverfolgen ausgewählt hat.

- **IsEyeCalibrationValid:** Gibt an, ob die Eyetracking-Kalibrierung des Benutzers gültig ist oder nicht.
Sie gibt "NULL" zurück, wenn der Wert noch keine Daten vom Eyetrackingsystem empfangen hat.
Er ist möglicherweise ungültig, da der Benutzer die Eyetracking-Kalibrierung übersprungen hat.

- **IsEyeTrackingEnabledAndValid:** Gibt an, ob die aktuellen Blickverfolgungsdaten derzeit zum Anvisieren verwendet werden.

- **IsEyeTrackingDataValid:** True, wenn Eyetrackingdaten verfügbar sind.
Es ist möglicherweise aufgrund eines überschrittenen Timeouts (sollte für den Benutzer robust sein, wenn er blinkt) oder aufgrund fehlender Nachverfolgungshardware oder -berechtigungen nicht verfügbar.
Sehen Sie sich unser Beispiel für die [Benachrichtigung über fehlende Augenkalibrierung](eye-tracking-is-user-calibrated.md) an, in dem erläutert wird, wie Sie erkennen können, ob ein Benutzer mit dem Auge kalibriert ist, und um eine entsprechende Benachrichtigung anzuzeigen.

- **GazeOrigin:** Ursprung des Anvischer Strahls.
Beachten Sie, dass dadurch der Ursprung des Anvierens mit dem *Kopf* zurückgegeben wird, wenn "IsEyeGazeValid" false ist.

- **GazeDirection:** Richtung des Anvischen-Strahls.
Dadurch wird die Richtung des Anvierens mit dem *Kopf* zurückgegeben, wenn "IsEyeGazeValid" false ist.

- **HitInfo,** **HitPosition,** **HitNormal** usw.: Informationen zum derzeit anvisierten Ziel.
Auch wenn `IsEyeGazeValid` false ist, basiert dies auf dem Anverweisen des Benutzers auf den *Kopf.*

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a>Beispiele für die Verwendung von CoreServices.InputSystem.EyeGazeProvider

Hier sehen Sie ein Beispiel aus [followEyeGaze.cs:](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)

- Abrufen des Punkts eines Hologramms, das der Benutzer ansieht:

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- Anzeigen eines visuellen Medienobjekts in einem festen Abstand von dem Ort, an dem der Benutzer gerade sucht:

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a>Siehe auch

- [MRTK Eye Tracking Overview](eye-tracking-main.md)
- [MRTK Eye Tracking-Setup](eye-tracking-basic-setup.md)
- [MRTK Eye Tracking Calibration](eye-tracking-is-user-calibrated.md)
- [HoloLens 2 EyeTracking-Dokumentation](/windows/mixed-reality/eye-tracking)