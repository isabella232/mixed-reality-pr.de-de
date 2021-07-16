---
title: Konfigurieren von Gitternetzbeobachtern für das Gerät
description: Konfigurieren des out-of-box Spatial Mesh Observer in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281939"
---
# <a name="configuring-mesh-observers-for-device"></a>Konfigurieren von Gitternetzbeobachtern für das Gerät

Dieser Leitfaden führt Sie durch die Konfiguration des vorkonfigurieren Spatial Mesh Observer in MRTK, der die Windows Mixed Reality unterstützt (d. h. HoloLens). Die vom Mixed Reality Toolkit bereitgestellte Standardimplementierung ist die [WindowsMixedRealitySpatialMeshObserver-Klasse.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) Viele der Eigenschaften in diesem Artikel gelten jedoch für andere [benutzerdefinierte Observer-Implementierungen.](create-data-provider.md)

## <a name="profile-settings"></a>Profileinstellungen

Die folgenden beiden Elemente müssen zuerst definiert werden, wenn Sie ein Spatial Mesh Observer-Profil für das [Spatial Awareness-System konfigurieren.](spatial-awareness-getting-started.md)

1. Die konkrete Implementierung des Beobachtertyps
1. Liste der unterstützten Plattformen zum Ausführen dieses Beobachters

> [!NOTE]
> Alle Beobachter müssen die [IMixedRealitySpatialAwarenessObserver-Schnittstelle](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) erweitern.

![Mesh Observer– allgemeine Einstellungen Plattformtypen](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>Allgemeine Einstellungen

![Allgemeine Einstellungen für Mesh Observer Einstellungen Genral](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**Startverhalten**

Das Startverhalten gibt an, ob die Ausführung des Beobachters beginnt, wenn er zum ersten Mal instanziiert wird. Die zwei Optionen sind:

* *Automatischer Start:* Der Standardwert, bei dem der Beobachter den Vorgang nach der Initialisierung startet.
* *Manueller Start:* Der Beobachter wartet darauf, dass er zum Starten geleitet wird.

Wenn Sie *den manuellen Start verwenden,* müssen sie zur Laufzeit über den Code fortgesetzt [und angehalten werden.](usage-guide.md#starting-and-stopping-mesh-observation)

**Updateintervall**

Die Zeit in Sekunden zwischen Anforderungen an die Plattform zum Aktualisieren der Räumlichen Gitternetzdaten. Typische Werte liegen im Bereich von 0,1 und 5,0 Sekunden.

**Is Stationärer Beobachter**

Gibt an, ob der Beobachter unverändert bleiben oder mit dem Benutzer verschieben und aktualisieren soll. True gibt an, dass *die Observer-Form* mit durch *Observation Extents definiertem* Volume beim Start am Ursprung verbleibt. False gibt an, dass der Beobachterbereich dem Kopf des Benutzers als Ursprung der Form folgt.

Es werden keine Gitternetzdaten für einen physischen Bereich außerhalb des Beobachterbereichs berechnet, wie durch diese Eigenschaften definiert: *Is Stationary Observer,**Observer Shape** und *Observation Extents*.

**Observer-Form**

Die Beobachterform definiert den Volumetyp, den der Gitternetzbeobachter beim Beobachten von Gittern verwendet. Die folgenden Optionen werden unterstützt:

* *Achsenbündiger Würfel:* Rechteckige Form, die an den Achsen des Weltkoordinatensystems ausgerichtet bleibt, wie beim Anwendungsstart festgelegt.
* *Vom Benutzer ausgerichteter Würfel:* Rechteckige Form, die gedreht wird, um sie am lokalen Koordinatensystem des Benutzers auszurichten.
* *Kugel:* Ein pherisches Volume mit einem Mittelpunkt am Ursprung des Weltraums. Der X-Wert der *Eigenschaft Observation Extents* wird als Radius der Kugel verwendet.

**Beobachtungs-Extents**

Die Beobachtungsdweite definiert den Abstand vom Beobachtungspunkt, an dem Gitternetze beobachtet werden.

### <a name="physics-settings"></a>Physikalische Einstellungen

![Mesh Observer Physics Einstellungen](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**Physikschicht**

Die physikalische Schicht, auf der räumliche Gitternetzobjekte platziert werden, um mit den Unity-Systemen Für Physik und RayCast zu interagieren.

> [!NOTE]
> Das Mixed Reality Toolkit reserviert *standardmäßig Ebene 31* für die Verwendung durch Beobachter des räumlichen Bewusstseins.

**Neuberechnung von Normals**

Gibt an, ob der Gitternetzbeobachter die Normalen des Gitters nach der Beobachtung neu berechnet. Diese Einstellung ist verfügbar, um sicherzustellen, dass Anwendungen Gitternetze empfangen, die gültige Normaldaten auf Plattformen enthalten, die sie nicht mit Gittern zurückgeben.

### <a name="level-of-detail-settings"></a>Detailebeneneinstellungen

![Mesh Observer Level of Detail Einstellungen](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**Detailebene**

Gibt die Detailebene (LEVEL of Detail, LOD) der räumlichen Gitterdaten an. Aktuell definierte Werte sind "Coarse", "Fine" und "Custom".

* *Grob:* Wirkt sich weniger auf die Anwendungsleistung aus und ist eine hervorragende Wahl für die Navigations-/Ebenensuche.

* *Mittel:* Eine ausgeglichene Einstellung ist häufig nützlich für Erfahrungen, bei denen die Umgebung ständig sowohl nach großen Merkmalen, Bodenbelägen und Wänden als auch nach Verschlussdetails durchsucht wird.

* *Fein:* In der Regel wird eine höhere Auswirkung auf die Anwendungsleistung abverfolgen und ist eine hervorragende Option für Okklusionsgitter.

* *Benutzerdefiniert:* Erfordert, dass die Anwendung die *Eigenschaft Dreiecke/kubische* Verbrauchsmessung anknt und Anwendungen ermöglicht, die Genauigkeit im Vergleich zu den Leistungseinwirkungen des Raumgitterbeobachters zu optimieren.

> [!NOTE]
> Es ist nicht garantiert, dass alle *Werte für Dreiecke/kubische* Zähler von allen Plattformen verwendet werden. Experimentieren und Profilerstellung wird dringend empfohlen, wenn Sie eine benutzerdefinierte LOD verwenden.

**Dreiecke pro kubischer Verbrauchsmessung**

Gültig, wenn die *Einstellung Benutzerdefiniert* für die **Eigenschaft Detailebene verwendet** wird, und gibt die Dreiecksdichte für das räumliche Netz an.

### <a name="display-settings"></a>Anzeigeeinstellungen

![Gitternetzbeobachteranzeige Einstellungen](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**Anzeigeoption**

Gibt an, wie räumliche Gitternetze vom Beobachter angezeigt werden sollen. Diese Werte werden unterstützt:

* *Keine:* Observer rendert das Gitternetz nicht
* *Sichtbar:* Gitternetzdaten werden mithilfe des sichtbaren *Materials angezeigt.*
* *Okklusion:* Gitternetzdaten verdecken Elemente in der Szene mithilfe des *Okklusionsmaterials.*

![Auswählen der Spatial Awareness-Systemimplementierung](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

Raumbeobachter [können zur Laufzeit über Code fortgesetzt/angehalten werden.](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> Wenn *Sie die Anzeigeoption* auf *Keine festlegen,* **wird die** Ausführung des Beobachters NICHT verhindern. Wenn Sie alle Beobachter beenden möchten, müssen Anwendungen alle Beobachter über anhalten. [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**Sichtbares Material**

Gibt das Material an, das beim Visualisieren des räumlichen Gitters verwendet werden soll.

**Okklusionsmaterial**

Gibt das Material an, das verwendet werden soll, damit das räumliche Netz Hologramme verdecken kann.

## <a name="see-also"></a>Weitere Informationen

* [Spatial Awareness System](spatial-awareness-getting-started.md)
* [Konfigurieren des Systems für räumliche Wahrnehmung über Code](usage-guide.md)
* [Dokumentation zur IMixedRealitySpatialAwarenessObserver-API](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [IMixedRealitySpatialAwarenessMeshObserver-API-Dokumentation](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [BaseSpatialObserver-API-Dokumentation](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
