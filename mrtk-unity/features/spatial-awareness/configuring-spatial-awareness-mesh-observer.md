---
title: Konfigurieren von Gittermodell-Beobachtern für ein Gerät
description: Konfigurieren des vordefinierten Spatial Mesh-Beobachters in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 00a3b9afe1970239f52b1ead4f87f930c5826ba75522b99a52cf368249c9fd83
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228457"
---
# <a name="configuring-mesh-observers-for-device"></a>Konfigurieren von Gittermodell-Beobachtern für ein Gerät

Dieser Leitfaden führt Sie durch die Konfiguration des vordefinierten Spatial Mesh Observer in MRTK, der die Windows Mixed Reality Plattform unterstützt (d. h. HoloLens). Die standardimplementierte Vom Mixed Reality Toolkit bereitgestellte Implementierung ist die [WindowsMixedRealitySpatialMeshObserver-Klasse.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) Viele der Eigenschaften in diesem Artikel gelten jedoch für andere [benutzerdefinierte Observer-Implementierungen.](create-data-provider.md)

## <a name="profile-settings"></a>Profileinstellungen

Die folgenden beiden Elemente müssen zuerst definiert werden, wenn sie ein Spatial Mesh Observer-Profil für das [Spatial Awareness-System](spatial-awareness-getting-started.md)konfigurieren.

1. Die konkrete Implementierung des Beobachtertyps
1. Liste der unterstützten Plattformen zum Ausführen dieses Beobachters

> [!NOTE]
> Alle Beobachter müssen die [IMixedRealitySpatialAwarenessObserver-Schnittstelle](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) erweitern.

![Allgemeine Einstellungen Plattformtypen von Mesh Observer](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>Allgemeine Einstellungen

![Allgemeine Einstellungen Genral-Einstellungen für Mesh Observer](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**Startverhalten**

Das Startverhalten gibt an, ob der Beobachter bei der ersten Instanziierung mit der Ausführung beginnt. Die zwei Optionen sind:

* *Automatischer Start:* Der Standardwert, bei dem der Beobachter den Vorgang nach der Initialisierung startet.
* *Manueller Start:* Der Beobachter wartet darauf, zum Starten weitergeleitet zu werden.

Wenn *Sie manuell starten* verwenden, müssen [sie zur Laufzeit über den Code fortgesetzt und angehalten](usage-guide.md#starting-and-stopping-mesh-observation)werden.

**Aktualisierungsintervall**

Die Zeit in Sekunden zwischen Anforderungen an die Plattform zum Aktualisieren räumlicher Gitternetzdaten. Typische Werte liegen im Bereich von 0,1 und 5,0 Sekunden.

**Ist stationärer Beobachter**

Gibt an, ob der Beobachter stationär bleiben oder mit dem Benutzer verschoben und aktualisiert werden soll. True gibt an, dass die *Beobachterform* mit dem durch *Beobachtungsumfang definierten* Volume beim Start am Ursprung verbleibt. False gibt an, dass der Beobachterbereich dem Kopf des Benutzers als Ursprung der Form folgt.

Es werden keine Gitternetzdaten für einen physischen Bereich außerhalb des Beobachterbereichs berechnet, wie in diesen Eigenschaften definiert: *Is Stationary Observer*, *Observer Shape** und *Observation Extents*.

**Beobachterform**

Die Beobachterform definiert den Volumetyp, den der Gitternetzbeoblicker beim Beobachten von Gitternetzen verwendet. Folgende Optionen werden unterstützt:

* *Achsenbündiger Würfel:* Rechteckige Form, die an den Achsen des Weltkoordinatensystems ausgerichtet bleibt, wie beim Anwendungsstart bestimmt.
* *Vom Benutzer ausgerichteter Cube:* Rechteckige Form, die gedreht wird, um sie an das lokale Koordinatensystem des Benutzers anzupassen.
* *Sphere:* Ein sphärisches Volume mit einem Mittelpunkt am Ursprung des Weltraums. Der X-Wert der *Eigenschaft Observation Extents* wird als Radius der Kugel verwendet.

**Beobachtungsumfang**

Die Beobachtungsumfang definieren den Abstand zum Beobachtungspunkt, der beobachtet wird.

### <a name="physics-settings"></a>Physikalische Einstellungen

![Mesh Observer Einstellungen](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**Physikalische Schicht**

Die physikalische Schicht, auf der räumliche Gittergitterobjekte platziert werden, um mit den Unity-Systemen "Physics" und "RayCast" zu interagieren.

> [!NOTE]
> Das Mixed Reality Toolkit reserviert standardmäßig *Schicht 31* für die Verwendung durch Beobachter der räumlichen Wahrnehmung.

**Neuberechnung von Normalitäten**

Gibt an, ob der Gitternetzbeowacher die Normalitäten des Gitternetzes nach der Beobachtung neu berechnet. Diese Einstellung ist verfügbar, um sicherzustellen, dass Anwendungen Gitternetze empfangen, die gültige Normaldaten auf Plattformen enthalten, die sie nicht mit Gitternetzen zurückgeben.

### <a name="level-of-detail-settings"></a>Ebene der Detaileinstellungen

![Detailebene des Mesh-Beobachters Einstellungen](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**Detailebene**

Gibt die Detailebene (LOD) der räumlichen Gitternetzdaten an. Derzeit definierte Werte sind "Coarse", "Fine" und "Custom".

* *Grob:* Wirkt sich weniger auf die Anwendungsleistung aus und ist eine hervorragende Wahl für die Navigations-/Ebenensuche.

* *Mittel:* Ausgeglichene Einstellung ist häufig nützlich für Umgebungen, die die Umgebung ständig sowohl nach großen Merkmalen, Etagen und Wänden als auch nach Verdeckungsdetails durchsuchen.

* *Gut:* Im Allgemeinen hat dies einen höheren Einfluss auf die Anwendungsleistung und ist eine hervorragende Option für Verdeckungsgitternetze.

* *Benutzerdefiniert:* Erfordert, dass die Anwendung die Eigenschaft *Dreiecke/Kubische Verbrauchsmessung* angibt und Anwendungen ermöglicht, die Genauigkeit im Vergleich zur Leistungsbeeinträchtigung des Beobachters für räumliche Gitternetze zu optimieren.

> [!NOTE]
> Es ist nicht garantiert, dass alle Werte für *Dreiecke/Kubikmeter* von allen Plattformen berücksichtigt werden. Experimente und Profilerstellung werden dringend empfohlen, wenn Sie eine benutzerdefinierte LOD verwenden.

**Dreiecke pro Kubikmeter**

Gültig, wenn die *Benutzerdefinierte* Einstellung für die **Eigenschaft Detailebene** verwendet wird und die Dreiecksdichte für das räumliche Gitternetz angibt.

### <a name="display-settings"></a>Anzeigeeinstellungen

![Mesh Observer Display Einstellungen](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**Anzeigeoption**

Gibt an, wie räumliche Gitternetze vom Beobachter angezeigt werden sollen. Diese Werte werden unterstützt:

* *Keine:* Observer rendert das Gitternetz nicht
* *Sichtbar:* Gitternetzdaten werden mithilfe des *sichtbaren Materials* angezeigt.
* *Verdeckung:* Gitternetzdaten verdecken Elemente in der Szene mithilfe des *Verdeckungsmaterials.*

![Auswählen der Spatial Awareness System-Implementierung](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

Räumliche Beobachter können [zur Laufzeit über Code fortgesetzt/angehalten werden.](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> Wenn *Sie die Anzeigeoption* auf *Keine* festlegen, wird die Ausführung des Beobachters **NICHT** beendet. Wenn Sie alle Beobachter beenden möchten, müssen Anwendungen alle Beobachter über anhalten. [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**Sichtbares Material**

Gibt das Material an, das beim Visualisieren des räumlichen Gitternetzes verwendet werden soll.

**Verdeckungsmaterial**

Gibt das Material an, das verwendet werden soll, damit das räumliche Gitternetz Hologramme verdeckt.

## <a name="see-also"></a>Siehe auch

* [Räumliches Bewusstseinssystem](spatial-awareness-getting-started.md)
* [Konfigurieren des Räumlichen Bewusstseinssystems über Code](usage-guide.md)
* [IMixedRealitySpatialAwarenessObserver-API-Dokumentation](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [Dokumentation zur IMixedRealitySpatialAwarenessMeshObserver-API](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [Dokumentation zur BaseSpatialObserver-API](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
