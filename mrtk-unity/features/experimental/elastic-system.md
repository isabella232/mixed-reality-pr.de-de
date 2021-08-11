---
title: Elastisches System
description: Dokumentation zur Simulation elastischer Datenbanken im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, ElasticsSystem,
ms.openlocfilehash: e34b9ea68bfbdc7b7f285686565a1e049ba58ad8677b16e915a2db8272ec1cbe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217902"
---
# <a name="elastic-system"></a>Elastisches System

![Elastisches System](../images/elastics/Elastics_Main1.gif)

MRTK verfügt über ein elastisches Simulationssystem, das eine Vielzahl von erweiterbaren und flexiblen Unterklassen enthält und Bindungen für vierdimensionale Quaternionsmaße, dreidimensionale Volumenmaße und einfache lineare Springsysteme bietet.

Derzeit können die folgenden MRTK-Komponenten, die den [Elastics Manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) unterstützen, die Funktionalität für elastische Datenbanken nutzen:

- [Begrenzungssteuerelement](../ux-building-blocks/bounds-control.md)
- [Objektmanipulator](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>Manager für elastische Datenbanken

![Elastic System2](../images/elastics/Elastics_Main.gif)

Der Elastics Manager verarbeitet übergebene Transformationen und leitet sie in das System für elastische Datenbanken ein.

Das Aktivieren von elastischen Datenbanken für benutzerdefinierte Komponenten kann mit zwei Schritten erreicht werden:

1. Durch Aufrufen der Initialize-Methode beim Manipulationsstart wird das System mit der aktuellen Hosttransformation aktualisiert.
1. Abfragen von ApplyHostTransform, wenn eine Berechnung für elastische Datenbanken für die aktualisierte Zieltransformation durchgeführt werden soll.

Beachten Sie, dass elastische Datenbanken weiterhin simulieren, sobald die Bearbeitung beendet ist (über die Updateschleife des Managers für elastische Datenbanken). Um das Verhalten zu blockieren, kann [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) für elastische Datenbanken automatisch auf FALSE festgelegt werden.

Standardmäßig sind für die Elastics Manager-Komponente beim Hinzufügen zu einem Spielobjekt keine elastischen Datenbanken für jeden Transformationstyp aktiviert.
Das Feld `Manipulation types using elastic feedback` muss für bestimmte Transformationstypen aktiviert werden, um elastische Konfigurationen und Erweiterungen für den ausgewählten Typ zu erstellen.

### <a name="elastics-configurations"></a>Konfigurationen für elastische Datenbanken

Ähnlich wie [bei Begrenzungssteuerelementkonfigurationen](../ux-building-blocks/bounds-control.md#configuration-objects)verfügt der Elastische Manager über eine Reihe von Konfigurationsobjekten, die als skriptfähige Objekte gespeichert und von verschiedenen Instanzen oder Prefabs gemeinsam genutzt werden können. Konfigurationen können entweder als einzelne skriptfähige Medienobjektdateien oder als geschachtelte skriptfähige Objekte innerhalb von Prefabs freigegeben und verknüpft werden. Weitere Konfigurationen können auch direkt auf der Instanz definiert werden, ohne eine Verknüpfung mit einem externen oder geschachtelten Skriptobjekt zu erstellen.

Der Inspektor des Managers für elastische Datenbanken gibt an, ob eine Konfiguration als Teil der aktuellen Instanz freigegeben oder inline ist, indem eine Meldung im Eigenschafteninspektor angezeigt wird. Darüber hinaus können freigegebene Instanzen nicht direkt im Eigenschaftenfenster des Managers für elastische Datenbanken selbst bearbeitet werden. Stattdessen muss die Ressource, mit der sie verknüpft wird, direkt geändert werden, um versehentliche Änderungen an freigegebenen Konfigurationen zu vermeiden.

Der Manager für elastische Datenbanken bietet Konfigurationsoptionen für die folgenden Transformationstypen, die jeweils durch ein [elastisches Konfigurationsobjekt](#elastic-configuration-object)dargestellt werden:

- Elastische Übersetzung
- Elastische Rotation
- Skalieren der elastischen Datenbanken

#### <a name="elastic-configuration-object"></a>Elastisches Konfigurationsobjekt

Eine Konfiguration für elastische Datenbanken definiert Eigenschaften für ein gestuftes differenzielles System mit einem elastischen Oszillationsor.
Die folgenden Eigenschaften können angepasst werden, verfügen aber bereits über einen Satz von Standardwerten im MRTK:

- **Mass:** Die Menge des simulierten Oszillationselements.
- **HandK:** Handspringkonstante.
- **EndK:** Endendeende-Springkonstante.
- **SnapK:** Andockpunkt-Springkonstante.
- **Ziehen Sie**: Zieh-/Ziehfaktor, proportional zur Geschwindigkeit.

### <a name="elastics-extents"></a>Bänder für elastische Datenbanken

Die Einstellungen für elastische Erweiterungen variieren je nach Art der Bearbeitung. Übersetzung und Skalierung werden durch [elastische Volume-Skalen](#volume-elastic-extent) dargestellt, und die Drehung wird durch einen [elastischen Quaternion-Skalar dargestellt.](#quaternion-elastic-extent)

#### <a name="volume-elastic-extent"></a>Elastischer Volumeumfang

Volumendehnungen definieren einen dreidimensionalen Raum, in dem sich der 160-Grad-Oszillatoren frei bewegen kann.

![Elastische Volumedehnungsgrenzen](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds:** Stellt die unteren Grenzen des elastischen Raums dar.
- **UseBounds:** Gibt an, ob die Stretchinggrenzen vom System berücksichtigt werden sollen. True gibt an, dass die Endkraft angewendet wird, wenn sich die aktuelle Iteration der Zielposition außerhalb der Streckungsgrenzen befindet.
- **SnapPoints:** Punkte innerhalb des Leerzeichens, an dem das System ausgerichtet wird.
- **RepeatSnapPoints:** wiederholt die Ausrichtungspunkte auf unendlich. Vorhandene Ausrichtungspunkte dienen als Modulo, bei dem die tatsächlichen Ausrichtungspunkte den nächsten ganzzahligen Vielfachen jedes Ausrichtungspunkts zugeordnet werden.
- **SnapRadius:** Abstand, ab dem Andockpunkte beginnen, die Feder zu erzwingen.

![Snap Grid für elastische Volumes](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>Elastischer Quaternion-Extent

Quaternion-Erweiterungen definieren einen vierdimensionalen Drehungsbereich, in dem der 100-Grad-Oszillatoren frei rotiert werden kann.

![Beispiel für elastische Rotation](../images/elastics/Elastics_Rotation.gif)

- **SnapPoints:** Eulerwinkel, an denen das System ausgerichtet wird.
- **RepeatSnapPoints:** wiederholt die Ausrichtungspunkte. Vorhandene Ausrichtungspunkte dienen als Modulo, bei dem die tatsächlichen Ausrichtungspunkte den nächsten ganzzahligen Vielfachen jedes Ausrichtungspunkts zugeordnet werden.
- **SnapRadius:** Bogenwinkel, an dem Andockpunkte beginnen, die Feder in Eulergraden zu erzwingen.

## <a name="elastics-example-scene"></a>Beispielszene für elastische Datenbanken

Beispiele für Elastische Konfigurationen finden Sie in der `ElasticSystemExample` Szene.

![Beispielszene für elastische Datenbanken](../images/elastics/Elastics_Example_Scene.png)
