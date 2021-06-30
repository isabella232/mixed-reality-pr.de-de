---
title: Unity AR-Kameraeinstellungen
description: Dokumentation zur Verwendung der AR-Kamera in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, AR-Kamera,
ms.openlocfilehash: e1c032805bc4b733cfcc51e1ceac5096c73715cf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121198"
---
# <a name="unity-ar-camera-settings-provider"></a>Unity AR-Kameraeinstellungsanbieter

Der Unity AR-Kameraeinstellungsanbieter ist eine experimentelle MRTK-Komponente, mit der Mixed Reality-Anwendungen auf Android- und iOS-Geräten ausgeführt werden können.

## <a name="unity-ar-camera-settings-provider-options"></a>Optionen des Unity AR-Kameraeinstellungsanbieters

![Konfiguration der Unity AR-Kameraeinstellungen](../images/camera-system/UnityArSettingsConfiguration.png)

Eine Anleitung zum Hinzufügen des Anbieters zu Ihrer Szene: [Konfigurieren von MRTK für iOS und Android](../../supported-devices/using-ar-foundation.md)

### <a name="tracking-settings"></a>Nachverfolgungseinstellungen

Der Unity AR-Kameraeinstellungsanbieter ermöglicht Konfigurationsoptionen für die Nachverfolgung. Diese Einstellungen sind spezifisch für die Implementierung des Unity AR-Kameraeinstellungsanbieters.

**Pose-Quelle**

Die Posenquelle definiert die verfügbaren Typen von Augmented Reality-Nachverfolgungsposen. Im Allgemeinen werden diese Werte einer Komponente des Geräts zugeordnet, auf dem die Anwendung ausgeführt wird.

Die verfügbaren Optionen werden in der folgenden Tabelle beschrieben.

| Option | Beschreibung |
| --- | --- |
| Zentrum | Das mittlere Auge eines mit dem Kopf bestückten Geräts. |
| Farbkamera | Die Farbkamera eines mobilen Geräts. |
| Head | Das Kopfauge eines mit dem Kopf bestückten Geräts, häufig etwas über dem mittleren Auge. |
| Linkes Auge | Das linke Auge eines auf dem Kopf installierten Geräts. |
| Linke Pose | Die linke Controllerpose. |
| Rechtes Auge | Das rechte Auge eines am Kopf eingebauten Geräts. |
| Rechte Pose | Die rechte Controllerpose. |

Der Standardwert für die Posenquelle ist **Farbkamera**, um eine transparente Anzeige auf mobilen Geräten wie einem Smartphone oder Tablet zu ermöglichen.

**Überwachungstyp**

Der Nachverfolgungstyp definiert die Teile der Pose, die für die Nachverfolgung verwendet werden.

Die verfügbaren Optionen werden in der folgenden Tabelle beschrieben.

| Option | Beschreibung |
| --- | --- |
| Position | Die Position des Geräts. |
| Drehung | Die Drehung des Geräts. |
| Drehung und Position | Die Position und Drehung des Geräts. |

Der Standardwert für den Nachverfolgungstyp ist **Drehung und Position**, um die größtmögliche Nachverfolgungserfahrung zu ermöglichen.

**Updatetyp**

Der Updatetyp definiert, an welchen Punkten während der Frameverarbeitung die Pose-Daten entnommen werden.

Die verfügbaren Optionen werden in der folgenden Tabelle beschrieben.

| Option | Beschreibung |
| --- | --- |
| Vor dem Rendern | Direkt vor dem Rendern. |
| Aktualisieren | Während der Aktualisierungsphase des Frames. |
| Aktualisieren von und vor dem Rendern | Während der Aktualisierungsphase und direkt vor dem Rendern. |

Der Standardwert für den Nachverfolgungstyp lautet **Update and Before Render**, um die niedrigste Nachverfolgungslatenz zu ermöglichen.

## <a name="see-also"></a>Siehe auch

- [Kamerasystemübersicht](camera-system-overview.md)
- [Erstellen eines Kameraeinstellungsanbieters](create-settings-provider.md)
