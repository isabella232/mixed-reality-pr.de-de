---
title: Eingabe-Animationsdateiformat
description: Dokumentation zur Spezifikation des Binärdateiformats für Eingabeanimationen in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: ba232818c0a49d803ca6fae0b5adbc64e6deefa8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145125"
---
# <a name="input-animation-binary-file-format-specification"></a>Spezifikation des Binärdateiformats für die Eingabeanimation

## <a name="overall-structure"></a>Gesamtstruktur

Die Binärdatei der Eingabeanimation beginnt mit einer magischen 64-Bit-Ganzzahlzahl. Der Wert dieser Zahl in Hexadezimal notation ist `0x6a8faf6e0f9e42c6` und kann verwendet werden, um gültige Eingabeanimationsdateien zu identifizieren.

Die nächsten acht Bytes sind zwei Int32-Werte, die die Haupt- und Nebenversionsnummer der Datei deklarieren.

Der Rest der Datei wird von Animationsdaten übernommen, die sich zwischen Versionsnummern ändern können.

| `Section` | type |
|---------|------|
| Magische Zahl | Int64 |
| Hauptversionsnummer | Int32 |
| Nebenversionsnummer | Int32 |
| Animationsdaten | _Siehe Abschnitt "Version"._ |

## <a name="version-11"></a>Version 1.1

Die Eingabeanimationsdaten bestehen aus drei booleschen Werten, die angeben, ob die Animation Kamera-, Hand- und Eye Gaze-Daten enthält, gefolgt von einer Sequenz von Animationskurven. Die vorhandenen Kurven hängen von den Werten dieser booleschen Werte ab. Jede Kurve kann eine andere Anzahl von Keyframes aufweisen.

| `Section` | type | Notizen |
|---------|------|------|
| Hat Kamerapose | Boolean | |
| Has Hand Data | Boolean | |
| Has Eye Gaze| Boolean | |
| Kamera | [Pose Curves](#pose-curves) | Nur, wenn "Has Camera Pose" (Kamerapose hat) "true" ist |
| Hand Tracked Left | [Boolesche Kurve](#boolean-curve) | Nur wenn Has Hand Data true ist |
| Hand nachverfolgt rechts | [Boolesche Kurve](#boolean-curve) | Nur wenn Has Hand Data true ist |
| Handgekleinerung nach links | [Boolesche Kurve](#boolean-curve) | Nur wenn Has Hand Data true ist |
| Rechtes Anheften mit der Hand | [Boolesche Kurve](#boolean-curve) | Nur wenn Has Hand Data true ist |
| Hand Joints Left | [Kurven der gemeinsamen Pose](#joint-pose-curves) | Nur wenn Has Hand Data true ist |
| Handgelenke rechts | [Kurven der gemeinsamen Pose](#joint-pose-curves) | Nur wenn Has Hand Data true ist |
| Anvingen mit den Augen | [Ray Curves](#ray-curves)] | Nur wenn "Has Eye Gaze" true ist |

## <a name="version-10"></a>Version 1.0

Die Eingabeanimationsdaten bestehen aus einer Sequenz von Animationskurven. Anzahl und Bedeutung von Animationskurven sind fest, aber jede Kurve kann eine andere Anzahl von Keyframes aufweisen.

| `Section` | type |
|---------|------|
| Kamera | [Pose Curves](#pose-curves) |
| Hand Tracked Left | [Boolesche Kurve](#boolean-curve) |
| Hand nach rechts nachverfolgt | [Boolesche Kurve](#boolean-curve) |
| Hand zusammendrücken nach links | [Boolesche Kurve](#boolean-curve) |
| Hand zusammendrücken nach rechts | [Boolesche Kurve](#boolean-curve) |
| Handverbindungen links | [Gemeinsame Posenkurven](#joint-pose-curves) |
| Handverbindungen rechts | [Gemeinsame Posenkurven](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>Gemeinsame Posenkurven

Für jede Hand wird eine Sequenz von gemeinsamen Animationskurven gespeichert. Die Anzahl der Fugen ist fest, und für jedes Joint wird eine Reihe von Posenkurven gespeichert.

| `Section` | type |
|---------|------|
| Keiner | [Pose Curves](#pose-curves) |
| Handgelenk | [Posenkurven](#pose-curves) |
| Palm | [Posenkurven](#pose-curves) |
| ThumbMetacarpalJoint | [Posenkurven](#pose-curves) |
| ThumbProximalJoint | [Posenkurven](#pose-curves) |
| ThumbDistalJoint | [Posenkurven](#pose-curves) |
| ThumbTip | [Posenkurven](#pose-curves) |
| IndexMetacarpal | [Posenkurven](#pose-curves) |
| IndexKnuckle | [Posenkurven](#pose-curves) |
| IndexMiddleJoint | [Posenkurven](#pose-curves) |
| IndexDistalJoint | [Posenkurven](#pose-curves) |
| IndexTip | [Posenkurven](#pose-curves) |
| MiddleMetacarpal | [Posenkurven](#pose-curves) |
| MiddleKnuckle | [Posenkurven](#pose-curves) |
| MiddleMiddleJoint | [Posenkurven](#pose-curves) |
| MiddleDistalJoint | [Posenkurven](#pose-curves) |
| MiddleTip | [Posenkurven](#pose-curves) |
| RingMetacarpal | [Posenkurven](#pose-curves) |
| RingKnuckle | [Posenkurven](#pose-curves) |
| RingMiddleJoint | [Posenkurven](#pose-curves) |
| RingDistalJoint | [Posenkurven](#pose-curves) |
| RingTip | [Posenkurven](#pose-curves) |
| RosayMetacarpal | [Pose Curves](#pose-curves) |
| RosayKnuckle | [Pose Curves](#pose-curves) |
| RosayMiddleJoint | [Pose Curves](#pose-curves) |
| RosayDistalJoint | [Pose Curves](#pose-curves) |
| RosayTip | [Pose Curves](#pose-curves) |

### <a name="pose-curves"></a>Posenkurven

Pose-Kurven sind eine Sequenz von drei Animationskurven für den Positionsvektor, gefolgt von vier Animationskurven für die Drehquaternion.

| `Section` | type |
|---------|------|
| Position X | [Gleitkommakurve](#float-curve) |
| Position Y | [Gleitkommakurve](#float-curve) |
| Position Z | [Gleitkommakurve](#float-curve) |
| Rotation X | [Gleitkommakurve](#float-curve) |
| Drehung Y | [Gleitkommakurve](#float-curve) |
| Drehung Z | [Gleitkommakurve](#float-curve) |
| Drehung W | [Gleitkommakurve](#float-curve) |

### <a name="ray-curves"></a>Ray curves (Raykurven)

Raykurven sind eine Sequenz von 3 Animationskurven für den Ursprungsvektor, gefolgt von 3 Animationskurven für den Richtungsvektor.

| `Section` | type |
|---------|------|
| Ursprung X | [Gleitkommakurve](#float-curve) |
| Ursprung Y | [Gleitkommakurve](#float-curve) |
| Ursprung Z | [Gleitkommakurve](#float-curve) |
| Richtung X | [Gleitkommakurve](#float-curve) |
| Richtung Y | [Gleitkommakurve](#float-curve) |
| Richtung Z | [Gleitkommakurve](#float-curve) |

### <a name="float-curve"></a>Gleitkommakurve

Gleitkommakurven sind vollständig gereifte Bézierkurven mit einer variablen Anzahl von Keyframes. Jeder Keyframe speichert einen Zeit- und einen Kurvenwert sowie Tangenten und Gewichtungen auf der linken und rechten Seite jedes Keyframes.

| `Section` | type |
|---------|------|
| Vorumbruchmodus | Int32, [Umbruchmodus](#wrap-mode) |
| Nach dem Umbruchmodus | Int32, [Umbruchmodus](#wrap-mode) |
| Anzahl der Keyframes | Int32 |
| Keyframes | [Float-Keyframe](#float-keyframe) |

### <a name="float-keyframe"></a>Float-Keyframe

Ein float-Keyframe speichert Tangens- und Gewichtungswerte zusammen mit der Basiszeit und dem Basiswert.

| `Section` | type |
|---------|------|
| Time | Float32 |
| Wert | Float32 |
| InTangent | Float32 |
| OutTangent | Float32 |
| InWeight | Float32 |
| OutWeight | Float32 |
| WeightedMode | Int32, [gewichteter Modus](#weighted-mode) |

### <a name="boolean-curve"></a>Boolesche Kurve

Boolesche Kurven sind einfache Sequenzen von Ein-/Aus-Werten. In jedem Keyframe wird der Wert der Kurve sofort gekippt.

| `Section` | type |
|---------|------|
| Pre-Wrap-Modus | Int32, [Wrap-Modus](#wrap-mode) |
| Post-Wrap-Modus | Int32, [Wrap-Modus](#wrap-mode) |
| Anzahl von Keyframes | Int32 |
| Keyframes | [Boolescher Keyframe](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>Boolescher Keyframe

Ein boolescher Keyframe speichert nur eine Zeit und einen Wert.

| `Section` | type |
|---------|------|
| Time | Float32 |
| Wert | Float32 |

### <a name="wrap-mode"></a>Wrap-Modus

Die Semantik des Pre- und Post Wrap-Modus folgt der [Unity WrapMode-Definition.](https://docs.unity3d.com/ScriptReference/WrapMode.html) Sie sind eine Kombination der folgenden Bits:

| Wert | Bedeutung |
|-------|---------|
| 0 | Standardeinstellung: Liest den standardmäßigen Wiederholungsmodus, der höher eingerichtet ist. |
| 1 | Einmal: Wenn die Zeit das Ende des Animationsclips erreicht, wird die Wiedergabe des Clips automatisch beendet, und die Zeit wird auf den Anfang des Clips zurückgesetzt. |
| 2 | Schleife: Wenn die Zeit das Ende des Animationsclips erreicht, wird die Zeit am Anfang fortgesetzt. |
| 4 | PingPong: Wenn die Zeit das Ende des Animationsclips erreicht, pingt die Zeit Pong zurück zwischen Anfang und Ende. |
| 8 | ClampForever: Gibt die Animation wieder. Wenn es das Ende erreicht, wird der letzte Frame weiter abspielt und nie beendet. |

### <a name="weighted-mode"></a>Gewichteter Modus

Die Semantik des modus Weighted folgt der [Unity WeightedMode-Definition.](https://docs.unity3d.com/ScriptReference/WeightedMode.html)

| Wert | Bedeutung |
|-------|---------|
| 0 | Keine: Schließen Sie sowohl inWeight als auch outWeight aus, wenn Sie Kurvensegmente berechnen. |
| 1 | In: Schließen Sie inWeight ein, wenn Sie das vorherige Kurvensegment berechnen. |
| 2 | Out: Schließen Sie outWeight ein, wenn Sie das nächste Kurvensegment berechnen. |
| 3 | Beides: Schließen Sie inWeight und outWeight ein, wenn Sie Kurvensegmente berechnen. |
