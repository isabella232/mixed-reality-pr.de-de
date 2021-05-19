---
title: 'Eyetracking (Blickverfolgung): Anbieter für Anvisieren (Gaze)'
description: Dokumentation für den Eye Gaze-Anbieter in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking, EyeTracke,
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144019"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>Zugreifen auf Eye-Tracking-Daten in Ihrem Unity-Skript

In diesem Artikel wird davon ausgegangen, dass Sie über Kenntnisse zum Einrichten der Eyetracking in einer MRTK-Szene (siehe Grundlegende MRTK-Einrichtung zur Verwendung von [EyeTracking) verfügt.](eye-tracking-basic-setup.md)
Der Zugriff auf Eye-Tracking-Daten in einem MonoBehaviour-Skript ist einfach! Verwenden Sie *einfach CoreServices.InputSystem.EyeAnbieter.*

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeProvider

Die Eyetrackingkonfiguration im MRTK wird über die -Schnittstelle [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) konfiguriert. Die [Verwendung von CoreServices.InputSystem.EyeProvider](eye-tracking-eye-gaze-provider.md) stellt die Standardmäßige Implementierung des Anvierungsanbieters bereit, die zur Laufzeit im Toolkit registriert ist.
Im Folgenden werden nützliche `EyeGazeProvider` Eigenschaften von beschrieben.

- **IsEyeTrackingEnabled:** True, wenn der Benutzer ausgewählt hat, eye tracking für das Anvieren zu verwenden.

- **IsEyeCalibrationValid:** Gibt an, ob die Eyetracking-Kalibrierung des Benutzers gültig ist.
Sie gibt "NULL" zurück, wenn der Wert noch keine Daten vom Eyetrackingsystem empfangen hat.
Es kann ungültig sein, da der Benutzer die Eyetracking-Kalibrierung übersprungen hat.

- **IsEyeTrackingEnabledAndValid:** Gibt an, ob die aktuellen Eyetrackingdaten derzeit für anvisiert werden.

- **IsEyeTrackingDataValid:** True, wenn Eyetrackingdaten verfügbar sind.
Sie ist möglicherweise nicht verfügbar, weil ein Timeout überschritten wurde (sollte jedoch robust sein, wenn der Benutzer blinkt) oder aufgrund fehlender Hardware oder Berechtigungen zur Nachverfolgung.
Sehen Sie sich unser [Beispiel zur Benachrichtigung](eye-tracking-is-user-calibrated.md) über fehlende Augen kalibrierung an, in dem erläutert wird, wie Sie erkennen können, ob ein Benutzer mit den Augen kalibriert ist, und um eine entsprechende Benachrichtigung zu zeigen.

- **GazeOrigin:** Ursprung des Anvistikstrahls.
Beachten Sie, dass  dadurch der Ursprung des Anvierens mit dem Kopf zurückgegeben wird, wenn "IsEyeEyeEyeeValid" false ist.

- **GazeDirection:** Richtung des Anvischen-Strahls.
Dadurch wird die Richtung des Anvierens mit dem *Kopf* zurückgegeben, wenn "IsEyeGazeValid" false ist.

- **HitInfo,** **HitPosition,** **HitNormal** usw.: Informationen zum derzeit anvisierten Ziel.
Auch wenn `IsEyeGazeValid` false ist, basiert dies auf dem Anverweisen mit dem *Kopf* des Benutzers.

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

## <a name="see-also"></a>Weitere Informationen

- [MRTK Eye Tracking Overview](eye-tracking-main.md)
- [MRTK Eye Tracking-Setup](eye-tracking-basic-setup.md)
- [MRTK Eye Tracking Calibration](eye-tracking-is-user-calibrated.md)
- [Dokumentation zur HoloLens 2 Eyetracking](/windows/mixed-reality/eye-tracking)