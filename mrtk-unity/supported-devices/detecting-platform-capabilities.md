---
title: Erkennen von Plattformfunktionen
description: Details zu den verschiedenen Funktionen, die mrtk unterstützt
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Funktionen,
ms.openlocfilehash: 0a3ad248e418e10ad1a7105ca5f9ece3e02c62bd7679cfd22d9c4396016d09a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207608"
---
# <a name="detecting-platform-capabilities"></a>Erkennen von Plattformfunktionen

Eine häufig gestellte Frage des MRTK umfasst das Wissen, welches bestimmte Gerät (z. B. Microsoft HoloLens 2) zum Ausführen einer Anwendung verwendet wird. Das Ermitteln der genauen Hardware kann auf verschiedenen Plattformen eine Herausforderung darstellen. Stattdessen bietet das MRTK eine Möglichkeit, bestimmte Funktionen zur Laufzeit zu identifizieren (z. B. wenn der aktuelle Geräteendpunkt artikulierte Hände unterstützt).

## <a name="capabilities"></a>Funktionen

Das Mixed Reality Toolkit stellt die [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) -Enumeration bereit, die einen Satz von Funktionen definiert, für die eine Anwendung zur Laufzeit Abfragen ausführen kann.

### <a name="input-system-capabilities"></a>Eingabesystemfunktionen

Das STANDARDMÄßIGE MRTK-Eingabesystem unterstützt das Abfragen der folgenden Funktionen:

| Funktion | Beschreibung |
|---|---|
| ArticulatedHand | Artikulierte Handeingabe |
| EyeTracking (Blickverfolgung) | Anvisieren mit den Augen |
| GGVHand | Handeingabe mit Anv-Geste-Stimme |
| MotionController | Motion Controller-Eingabe |
| VoiceCommand | Sprachbefehle mit von der App definierten Schlüsselwörtern |
| VoiceDictation | Sprach-zu-Text-Diktat |

Der folgende Beispielcode überprüft, ob das Eingabesystem einen Datenanbieter mit Unterstützung für formulierte Hände geladen hat.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>Funktionen zur räumlichen Wahrnehmung

Das standardmäßige MRTK Spatial Awareness-System unterstützt das Abfragen der folgenden Funktionen:

| Funktion | Beschreibung |
|---|---|
| SpatialAwarenessMesh | Räumliche Gitternetze |
| SpatialAwarenessPlane | Räumliche Ebenen |
| SpatialAwarenessPoint | Räumliche Punkte |

In diesem Beispiel wird überprüft, ob das System für räumliche Wahrnehmung einen Datenanbieter mit Unterstützung für räumliche Gitternetze geladen hat.

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>Siehe auch

- [IMixedRealityCapabilityCheck-API-Dokumentation](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [MixedRealityCapability-Enumerationsdokumentation](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
