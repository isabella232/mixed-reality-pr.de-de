---
title: Erkennen von Plattformfunktionen
description: Details zu den verschiedenen Funktionen, die vom MRTK unterstützt werden
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Funktionen,
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175525"
---
# <a name="detecting-platform-capabilities"></a>Erkennen von Plattformfunktionen

Eine häufig gestellte Frage zum MRTK besteht darin, zu wissen, welches bestimmte Gerät (z. B. Microsoft HoloLens 2) zum Ausführen einer Anwendung verwendet wird. Das Ermitteln der genauen Hardware kann auf verschiedenen Plattformen eine Herausforderung darstellen. Stattdessen bietet das MRTK eine Möglichkeit, bestimmte Funktionen zur Laufzeit zu identifizieren (z. B. wenn der aktuelle Geräteendpunkt artikulierte Hände unterstützt).

## <a name="capabilities"></a>Funktionen

Das Mixed Reality Toolkit stellt die -Enumeration bereit, die einen Satz von Funktionen definiert, für die eine Anwendung zur Laufzeit [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) Abfragen ausführen kann.

### <a name="input-system-capabilities"></a>Eingabesystemfunktionen

Das MRTK-Standardeingabesystem unterstützt das Abfragen der folgenden Funktionen:

| Funktion | Beschreibung |
|---|---|
| ArticulatedHand | Artikulierte Handeingabe |
| EyeTracking (Blickverfolgung) | Anvschauung mit den Augen |
| GGVHand | Eingabe der Hand "Gaze-Gesture-Voice" |
| MotionController | Eingabe des Bewegungscontrollers |
| VoiceCommand | Sprachbefehle mit app-definierten Schlüsselwörtern |
| VoiceDictation | Sprach-zu-Text-Diktat |

Der folgende Beispielcode überprüft, ob das Eingabesystem einen Datenanbieter mit Unterstützung für artikulierte Hände geladen hat.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>Funktionen des räumlichen Bewusstseins

Das MRTK Spatial Awareness-Standardsystem unterstützt das Abfragen der folgenden Funktionen:

| Funktion | Beschreibung |
|---|---|
| SpatialAwarenessMesh | Räumliche Gitternetze |
| SpatialAwarenessPlane | Räumliche Ebenen |
| SpatialAwarenessPoint | Räumliche Punkte |

In diesem Beispiel wird überprüft, ob das Raumbewusstseinssystem einen Datenanbieter mit Unterstützung für räumliche Gitternetze geladen hat.

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>Siehe auch

- [Dokumentation zur IMixedRealityCapabilityCheck-API](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [MixedRealityCapability-Dokumentation](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
