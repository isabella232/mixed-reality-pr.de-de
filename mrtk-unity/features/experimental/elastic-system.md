---
title: Elastisches System
description: Dokumentation zur Simulation von elastischen Datenbanken in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, ElasticsSystem,
ms.openlocfilehash: 44110cac9ac5aadb7b5e680f18a5e93f43efce12
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177792"
---
# <a name="elastic-system"></a>Elastisches System

![Elastisches System](../images/elastics/Elastics_Main1.gif)

MRTK verfügt über ein elastisches Simulationssystem, das eine Vielzahl von erweiterbaren und flexiblen Unterklassen umfasst und Bindungen für 4-dimensionale Quaternionsveralbungen, 3-dimensionale Volume-Bänder und einfache lineare Federsysteme bietet.

Derzeit können die folgenden MRTK-Komponenten, die [den Elastics Manager unterstützen,](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) elastische Funktionen nutzen:

- [Steuerelement "Begrenzungen"](../ux-building-blocks/bounds-control.md)
- [Objektmanipulator](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>Manager für elastische Datenbanken

![Elastic System2](../images/elastics/Elastics_Main.gif)

Der Elastics Manager verarbeitet übergebene Transformationen und gibt sie in das Elastiksystem ein.

Die Aktivierung von elastischen Komponenten für benutzerdefinierte Komponenten kann mit zwei Schritten erreicht werden:

1. Durch Aufrufen der Initialize-Methode beim Start der Bearbeitung wird das System mit der aktuellen Hosttransformation aktualisiert.
1. Abfragen von ApplyHostTransform, wenn eine elastische Berechnung für die aktualisierte Zieltransformation durchgeführt werden soll.

Beachten Sie, dass elastische Datenbanken weiterhin simulieren, sobald die Bearbeitung beendet ist (über die Updateschleife des Elastics-Managers). Um das Verhalten zu blockieren, kann [enableElasticsUpdate für elastische](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) Datenbanken auf FALSE festgelegt werden.

Standardmäßig sind für die Elastics Manager-Komponente keine elastischen Datenbanken für transformationstypen aktiviert, wenn sie einem Spielobjekt hinzugefügt werden.
Das Feld muss für bestimmte Transformationstypen aktiviert werden, um elastische Konfigurationen und Extents für `Manipulation types using elastic feedback` den ausgewählten Typ zu erstellen.

### <a name="elastics-configurations"></a>Elastische Konfigurationen

Ähnlich wie [bei Begrenzungssteuerungskonfigurationen](../ux-building-blocks/bounds-control.md#configuration-objects)enthält elastic manager eine Reihe von Konfigurationsobjekten, die als skriptfähige Objekte gespeichert und von verschiedenen Instanzen oder Prefabs gemeinsam genutzt werden können. Konfigurationen können entweder als einzelne skriptfähige Assetdateien oder als geschachtelte skriptfähige Objekte innerhalb von Prefabs freigegeben und verknüpft werden. Weitere Konfigurationen können auch direkt auf der Instanz definiert werden, ohne eine Verknüpfung mit einem externen oder geschachtelten skriptbaren Asset zu erstellen.

Der Elastics Manager-Inspektor gibt an, ob eine Konfiguration als Teil der aktuellen Instanz freigegeben oder inline ist, indem eine Meldung im Eigenschafteninspektor angezeigt wird. Darüber hinaus können freigegebene Instanzen nicht direkt im Eigenschaftenfenster des Elastics-Managers selbst bearbeitet werden. Stattdessen muss das Objekt, mit dem sie eine Verknüpfung erstellen, direkt geändert werden, um versehentliche Änderungen an freigegebenen Konfigurationen zu vermeiden.

Elastics Manager bietet Konfigurationsobjektoptionen für die folgenden Transformationstypen, die jeweils durch ein elastisches [Konfigurationsobjekt dargestellt werden:](#elastic-configuration-object)

- Elastische Übersetzung
- Elastische Rotation
- Elastische Skalierung

#### <a name="elastic-configuration-object"></a>Elastisches Konfigurationsobjekt

Eine konfiguration für elastische Datenbanken definiert Eigenschaften für ein geerbte oszillatorielles Oszillatorsystem.
Die folgenden Eigenschaften können angepasst werden, enthalten jedoch bereits eine Reihe von Standardwerten im MRTK:

- **Massen:** Die Massen des simulierten Oszillatorelements.
- **HandK:** Hand spring-Konstante.
- **EndK:** End cap spring constant.
- **SnapK:** Andockpunkt-Springkonst constant.
- **Ziehen** Sie : Drag/Drop-Faktor, proportional zur Geschwindigkeit.

### <a name="elastics-extents"></a>Elastische Dehnungen

Die Einstellungen für Elastische Bänder variieren je nach Art der Bearbeitung. Übersetzung und Skalierung werden durch [elastische Volumendehnungen](#volume-elastic-extent) dargestellt, und die Drehung wird durch einen [elastischen Quaternionsdehnungs-Extent dargestellt.](#quaternion-elastic-extent)

#### <a name="volume-elastic-extent"></a>Elastischer Volume-Umfang

Volume-Extent definieren einen dreidimensionalen Raum, in dem sich der geerbte Oszillator frei bewegen kann.

![Elastische Volumen-Stretch-Begrenzungen](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds:** Stellt die unteren Grenzen des elastischen Raums dar.
- **UseBounds:** Gibt an, ob die Streckungsgrenze vom System beachtet werden soll. True gibt an, dass die Enderzwingen angewendet werden, wenn die aktuelle Iteration der Zielposition außerhalb der Streckungsgrenze liegt.
- **SnapPoints:** Zeigt innerhalb des Raums, an dem das System ausrichten wird.
- **RepeatSnapPoints:** Wiederholt die Ausrichtungspunkte auf unendlich. Vorhandene Ausrichtungspunkte dienen als Modulo, bei dem die tatsächlichen Andockpunkte den nächsten ganzzahligen Vielfachen jedes Andockpunkts zugeordnet werden.
- **SnapRadius:** Die Entfernung, ab der Andockpunkte die Feder erzwingen.

![Andockraster für elastische Volumes](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>Elastische Quaternion

Quaternionendungen definieren einen vierdimensionalen Drehungsraum, in dem der geerbte Oszillator rotiert werden kann.

![Beispiel für elastische Drehung](../images/elastics/Elastics_Rotation.gif)

- **SnapPoints:** Eulerwinkel, an denen das System ausrichten wird.
- **RepeatSnapPoints:** Wiederholt die Andockpunkte. Vorhandene Ausrichtungspunkte dienen als Modulo, bei dem die tatsächlichen Andockpunkte den nächsten ganzzahligen Vielfachen jedes Andockpunkts zugeordnet werden.
- **SnapRadius:** Bogenwinkel, bei dem Ausrichtungspunkte beginnen, die Feder in Euler-Grad zu erzwingen.

## <a name="elastics-example-scene"></a>Beispielszene für elastische Datenbanken

Beispiele für elastische Konfigurationen finden Sie in der `ElasticSystemExample` Szene.

![Beispielszene für elastische Datenbanken](../images/elastics/Elastics_Example_Scene.png)
