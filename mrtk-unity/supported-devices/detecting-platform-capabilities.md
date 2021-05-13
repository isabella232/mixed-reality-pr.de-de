---
title: Erkennen vonPlatformCapabilities
description: Details zu den verschiedenen Funktionen, die mrtk unterstützt
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Funktionen,
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852371"
---
# <a name="detecting-platform-capabilities"></a>Erkennen von Plattformfunktionen

Eine häufig gestellte Frage des MRTK umfasst das Wissen, welches bestimmte Gerät (z. B. Microsoft HoloLens 2) zum Ausführen einer Anwendung verwendet wird. Das Ermitteln der genauen Hardware kann auf verschiedenen Plattformen eine Herausforderung darstellen. Stattdessen bietet das MRTK eine Möglichkeit, bestimmte Funktionen zur Laufzeit zu identifizieren (z. B. wenn der aktuelle Geräteendpunkt artikulierte Hände unterstützt).

## <a name="capabilities"></a>Funktionen

Das Mixed Reality Toolkit stellt die [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) -Enumeration bereit, die einen Satz von Funktionen definiert, für die eine Anwendung zur Laufzeit Abfragen ausführen kann.

### <a name="input-system-capabilities"></a>Eingabesystemfunktionen

Das MRTK-Standardeingabesystem unterstützt das Abfragen der folgenden Funktionen:

| Funktion | Beschreibung |
|---|---|
| ArticulatedHand | Artikulierte Handeingabe |
| EyeTracking (Blickverfolgung) | Anvisieren mit den Augen |
| GGVHand | Handeingabe mit Anv-Gesten-Stimme |
| MotionController | Motion Controller-Eingabe |
| VoiceCommand | Sprachbefehle mit von der App definierten Schlüsselwörtern |
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
