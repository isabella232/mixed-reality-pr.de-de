---
title: Konfigurieren der Begrenzungsvisualisierung
description: Details zum Konfigurieren des Begrenzungssystems im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Boundary System,
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144490"
---
# <a name="configuring-the-boundary-visualization"></a>Konfigurieren der Begrenzungsvisualisierung

Das *Profil für die Begrenzungsvisualisierung* bietet Optionen zum Konfigurieren der visuellen Darstellungen und anderer verwandter Parameter für das Begrenzungssystem. Begrenzungsvisualisierungen werden an Mixed Reality Playspace-Objekt in der Szene angefügt und mit dem Benutzer übertragen.

## <a name="general-settings"></a>Allgemeine Einstellungen

![Allgemeine Einstellungen für die Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>Begrenzungshöhe

Die Begrenzungshöhe gibt den Abstand über der Bodenebene an, an dem die Begrenzungsgrenze gerendert werden soll. Der Standardwert ist 3 Meter.

## <a name="floor-settings"></a>Einstellungen für den Boden

![Begrenzungsvisualisierung – Grundeinstellungen](../images/boundary/BoundaryVisualizationFloorSettings.png)

**Anzeigen**

Gibt an, ob eine Bodenebene erstellt und der Szene hinzugefügt werden soll. Der Standardwert lautet „true“.

**Material**

Gibt das Material an, das beim Erstellen der Bodenebene verwendet werden soll.

**Skalieren**

Gibt die Größe der zu erstellenden Bodenebene in Metern an. Die Standardskala ist ein Quadrat mit 3 x 3 Meter.

**Physikschicht**

Die Ebene, auf der die Bodenebene festgelegt werden soll. Der Standardwert ist die *Standardebene.*

## <a name="play-area-settings"></a>Wiedergabebereichseinstellungen

![Wiedergabebereichseinstellungen für Die Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**Anzeigen**

Gibt an, ob ein Rechteck für den Wiedergabebereich erstellt und der Szene hinzugefügt wird. Der Standardwert lautet „true“.

**Material**

Gibt das Material an, das beim Erstellen des Wiedergabebereichsobjekts verwendet werden soll.

**Physikalische Schicht**

Die Ebene, auf der der Wiedergabebereich festgelegt werden soll. Der Standardwert ist die *Ignore Raycast-Schicht.*

## <a name="tracked-area-settings"></a>Einstellungen für nachverfolgte Bereiche

![Einstellungen für nachverfolgte Bereiche der Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**Anzeigen**

Gibt an, ob der Umriss des nachverfolgten Bereichs erstellt und der Szene hinzugefügt wird. Der Standardwert lautet „true“.

**Material**

Gibt das Material an, das beim Erstellen der nachverfolgten Bereichsgliederung verwendet werden soll.

**Physikalische Schicht**

Die Ebene, auf der der nachverfolgte Bereich festgelegt werden soll. Der Standardwert ist die *Ignore Raycast-Schicht.*

## <a name="boundary-wall-settings"></a>Begrenzungswandeinstellungen

![Begrenzungsvisualisierung – Begrenzungswandeinstellungen](../images/boundary/BoundaryVisualizationWallSettings.png)

**Anzeigen**

Gibt an, ob Begrenzungsebenen erstellt und der Szene hinzugefügt werden sollen. Der Standardwert ist „FALSE“.

**Material**

Gibt das Material an, das beim Erstellen der Begrenzungswandebenen verwendet werden soll.

**Physikalische Schicht**

Die Schicht, auf der die Begrenzungswand festgelegt werden soll. Der Standardwert ist die *Ignore Raycast-Schicht.*

> [!NOTE]
> Das Festlegen der Begrenzungswandkomponente auf eine andere Physikalische Schicht als *Raycast ignorieren* kann Benutzer daran hindern, mit Objekten innerhalb der Szene zu interagieren.

## <a name="boundary-ceiling-settings"></a>Einstellungen für die Begrenzungsobergrenze

![Begrenzungsvisualisierung– Begrenzungsbegrenzungseinstellungen](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**Anzeigen**

Gibt an, ob eine Begrenzungsbegrenzungsebene erstellt und der Szene hinzugefügt werden soll. Der Standardwert ist „FALSE“.

**Material**

Gibt das Material an, das beim Erstellen der Begrenzungsbegrenzungsebene verwendet werden soll.

**Physikschicht**

Die Ebene, auf der die Begrenzungswand festgelegt werden soll. Der Standardwert ist die *Raycastebene ignorieren.*

> [!NOTE]
> Das Festlegen der Begrenzungsbegrenzungskomponente auf eine andere physikalische Ebene als *Raycast ignorieren* kann verhindern, dass Benutzer mit Objekten innerhalb der Szene interagieren.

## <a name="see-also"></a>Weitere Informationen

- [Dokumentation zur Begrenzungs-API](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Begrenzungs- system](boundary-system-getting-started.md)
