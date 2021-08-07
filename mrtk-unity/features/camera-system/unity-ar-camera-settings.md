---
title: Unity-AR-Kameraeinstellungen
description: Dokumentation zur Verwendung der AR-Kamera in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, AR-Kamera,
ms.openlocfilehash: a2d145823557b473bd7d34170b283e782151c24277b8f16586516ffe78f8e735
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210064"
---
# <a name="unity-ar-camera-settings-provider"></a>Unity AR-Kameraeinstellungsanbieter

Der Unity AR-Kameraeinstellungsanbieter ist eine experimentelle MRTK-Komponente, mit der Mixed Reality-Anwendungen auf Android- und iOS-Geräten ausgeführt werden können.

## <a name="unity-ar-camera-settings-provider-options"></a>Optionen des Unity AR-Kameraeinstellungsanbieters

![Konfiguration der Unity AR-Kameraeinstellungen](../images/camera-system/UnityArSettingsConfiguration.png)

Eine Anleitung zum Hinzufügen des Anbieters zu Ihrer Szene: [Konfigurieren des MRTK für iOS und Android](../../supported-devices/using-ar-foundation.md)

### <a name="tracking-settings"></a>Nachverfolgungseinstellungen

Der Unity AR-Kameraeinstellungsanbieter ermöglicht Konfigurationsoptionen für die Nachverfolgung. Diese Einstellungen gelten speziell für die Implementierung des Unity AR-Kameraeinstellungsanbieters.

**Posenquelle**

Die Posenquelle definiert die verfügbaren Arten von Augmented Reality-Nachverfolgungsposen. Im Allgemeinen werden diese Werte einer Komponente des Geräts, auf dem die Anwendung ausgeführt wird, zuordnen.

Die verfügbaren Optionen werden in der folgenden Tabelle beschrieben.

| Option | Beschreibung |
| --- | --- |
| Zentrum | Das zentrierte Auge eines mit dem Kopf gelagerten Geräts. |
| Farbkamera | Die Farbkamera eines mobilen Geräts. |
| Head | Das Kopf-Auge eines geräts, das mit dem Kopf bereitgestellt wird, häufig etwas über dem zentrierten Auge. |
| Linkes Auge | Das linke Auge eines mit dem Kopf bereitgestellten Geräts. |
| Linke Pose | Die Linke Controller-Pose. |
| Rechtes Auge | Das rechte Auge eines mit dem Kopf gelagerten Geräts. |
| Rechte Pose | Die Rechte Controller-Pose. |

Der Standardwert für die Posenquelle ist **Color Camera**, um eine transparente Anzeige auf mobilen Geräten wie einem Smartphone oder Tablet zu ermöglichen.

**Überwachungstyp**

Der Nachverfolgungstyp definiert die Teile der Pose, die für die Nachverfolgung verwendet werden.

Die verfügbaren Optionen werden in der folgenden Tabelle beschrieben.

| Option | Beschreibung |
| --- | --- |
| Position | Die Position des Geräts. |
| Drehung | Die Drehung des Geräts. |
| Drehung und Position | Die Position und Drehung des Geräts. |

Der Standardwert für den Nachverfolgungstyp ist **Drehung und Position,** um eine umfassende Nachverfolgungserfahrung zu ermöglichen.

**Updatetyp**

Der Updatetyp definiert, an welchen Punkten während der Frameverarbeitung die Posendaten entnommen werden.

Die verfügbaren Optionen werden in der folgenden Tabelle beschrieben.

| Option | Beschreibung |
| --- | --- |
| Vor dem Rendern | Kurz vor dem Rendering. |
| Update | Während der Aktualisierungsphase des Frames. |
| Aktualisieren und vor dem Rendern | Während der Updatephase und kurz vor dem Rendering. |

Der Standardwert für den Nachverfolgungstyp ist **Update und vor dem Rendern,** um die niedrigste Nachverfolgungslatenz zu ermöglichen.

## <a name="see-also"></a>Siehe auch

- [Kamerasystemübersicht](camera-system-overview.md)
- [Erstellen eines Kameraanbieters Einstellungen](create-settings-provider.md)
