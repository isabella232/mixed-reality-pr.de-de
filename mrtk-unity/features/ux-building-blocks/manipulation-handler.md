---
title: Manipulationshandler
description: Dokumentation zum Manipulationshandler in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Manipulation,
ms.openlocfilehash: 24034c43bf8ce1f1ef463e894e9ca5293c2b0d2a146284535b161f8b4277dfa9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190210"
---
# <a name="manipulation-handler"></a>Manipulationshandler

![Manipulationshandler](../images/manipulation-handler/MRTK_Manipulation_Main.png)

Mit dem *ManipulationHandler-Skript* kann ein Objekt mit ein oder zwei Händen verschiebbar, skalierbar und rotierbar gemacht werden. Die Bearbeitung kann so eingeschränkt werden, dass nur bestimmte Arten von Transformationen zulässig sind. Das Skript arbeitet mit verschiedenen Eingabetypen, einschließlich HoloLens 2 artikulierten Handeingaben, Handlichtlicht, HoloLens Gesteneingabe (1. Generation) und immersiver Headset-Motion Controller-Eingabe.

## <a name="how-to-use-the-manipulation-handler"></a>Verwenden des Manipulationshandlers

Fügen Sie die `ManipulationHandler` Skriptkomponente einem GameObject hinzu. Stellen Sie sicher, dass Sie dem Objekt auch einen Collider hinzufügen, der den ziehbaren Grenzen entspricht.

Damit das Objekt auf nahezu artikulierte Handeingaben reagiert, fügen Sie auch das `NearInteractionGrabbable` Skript hinzu.

![Verwenden des Manipulationshandlers im Unity-Editor](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a>Inspektoreigenschaften

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

**Hosttransformation** Transformation, die gezogen wird. Der Standardwert ist das -Objekt der Komponente.

**Manipulationstyp** Gibt an, ob das Objekt mit einer Hand, zwei Händen oder beidem bearbeitet werden kann.

* *Nur einhändige*
* *Nur zweihändige*
* *Ein- und Zweihändige*

**Zweihändige Manipulationsart**

* *Skalierung:* Es ist nur die Skalierung zulässig.
* *Rotieren:* Es ist nur die Drehung zulässig.
* *Skalierung verschieben:* Verschieben und Skalieren ist zulässig.
* *Move Rotate*:Verschieben und Drehen ist zulässig.
* *Skalierung drehen:* Rotieren und Skalieren ist zulässig.
* *Skalierung verschieben:* Verschieben, Drehen und Skalieren ist zulässig.

![Manipulationshandler](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

**Far Manipulation zulassen** Gibt an, ob die Bearbeitung mithilfe der fernen Interaktion mit Zeigern erfolgen kann.

**One-Hand-Drehungsmodus in der Nähe** Gibt an, wie sich das Objekt verhält, wenn es mit einer Hand oder einem Controller in der Nähe gepackt wird.

**One Hand Rotation Mode Far** Gibt an, wie sich das Objekt verhält, wenn es mit einer Hand/einem Controller im Abstand gepackt wird.

**Optionen für den One-Hand-Drehungsmodus** Gibt an, wie das Objekt gedreht wird, wenn es mit einer Hand gepackt wird.

* *Ursprüngliche Drehung beibehalten:* Das Objekt wird beim Verschieben nicht gedreht.
* *Rotation zum Benutzer beibehalten:* Behält die ursprüngliche Drehung des Objekts für die X/Y-Achse für den Benutzer bei.
* Die ausrichtung der *Schwerkraft behält die Drehung zum Benutzer* bei: Behält die ursprüngliche Drehung des Objekts zum Benutzer bei, macht das Objekt jedoch vertikal. Nützlich für Objekte mit einem Begrenzungssteuerelement.
* *Gesichtsbenutzer:* Stellt sicher, dass das Objekt dem Benutzer immer gegenübersteht. Nützlich für Slates/Panels.
* *Face away from user (Gesichtsabsicht vom Benutzer):* Stellt sicher, dass das Objekt immer vom Benutzer entfernt ist. Nützlich für Slates/Panels, die rückwärts konfiguriert sind.
* *Drehen um den Objektmittelpunkt:* Funktioniert nur für artikulierte Hände/Controller. Drehen Sie das Objekt mithilfe der Drehung der Hand/des Controllers, aber um den Objektmittelpunkt. Nützlich für die Untersuchung in einer Entfernung.
* *Drehen um Denkpunkt:* Funktioniert nur für artikulierte Hände/Controller. Drehen Sie das Objekt so, als ob es von Hand/Controller gehalten würde. Nützlich für die Überprüfung.

**Releaseverhalten** Wenn ein Objekt freigegeben wird, geben Sie sein physisches Bewegungsverhalten an. Erfordert, dass sich eine starre Komponente auf diesem Objekt befindet.

* *Nichts*
* *Alles*
* *Keep Velocity*
* *Keep Angular Velocity (Geschwindigkeit beibehalten)*

**Einschränkungen bei der Drehung** Gibt an, auf welcher Achse das Objekt gedreht wird, wenn es mit interagiert.

* *Keine*
* *Nur X-Achse*
* *Nur Y-Achse*
* *Nur Z-Achse*

**Verwenden des lokalen Speicherplatzes für Einschränkungen** Ein Umschalter zwischen der Anwendung von Einschränkungen in Bezug auf die Weltraumachse oder der lokalen Raumachse.

**Einschränkungen bei Der Verschiebung**

* *Keine*
* *Korrigieren der Entfernung vom Kopf*

**Glättung aktiv** Gibt an, ob die Glättung aktiv ist.

**Smoothing Amount One Hand** Umfang der Glättung, die auf Die Bewegung, Skalierung und Drehung angewendet werden soll. Glättung von 0 bedeutet keine Glättung. Max value bedeutet, dass keine Änderung am Wert vorfällt.

## <a name="events"></a>Ereignisse

Der Manipulationshandler stellt die folgenden Ereignisse bereit:

* *OnManipulationStarted:* Wird ausgelöst, wenn die Bearbeitung gestartet wird.
* *OnManipulationEnded:* Wird ausgelöst, wenn die Bearbeitung beendet wird.
* *OnHoverStarted:* Wird ausgelöst, wenn eine Hand/ein Controller auf das manipulatierbare ,nahe oder fernen' zusteuert.
* *OnHoverEnded:* Wird ausgelöst, wenn ein Hand/Controller den Mauszeiger auf den manipulatierbaren , nahe oder fernen ziehbar hält.
