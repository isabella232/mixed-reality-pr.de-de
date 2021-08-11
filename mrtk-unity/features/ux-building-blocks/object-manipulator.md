---
title: Objektmanipulator
description: Verwenden des Objektmanipulators in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Objektbearbeitung,
ms.openlocfilehash: 4c43a35e164d3e66e662afc927d28f84463e1586250e9847a2d88c219ba27f23
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191612"
---
# <a name="object-manipulator"></a>Objektmanipulator

![Objektmanipulator](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ObjectManipulator* ist die neue Komponente für manipulationsverhalten, die zuvor in *ManipulationHandler* gefunden wurde. Der Objektmanipulator nimmt eine Reihe von Verbesserungen und Vereinfachungen vor. Diese Komponente ist ein Ersatz für den Manipulationshandler, der veraltet ist.

Das *ObjectManipulator-Skript* macht ein Objekt mit ein oder zwei Händen verschiebbar, skalierbar und drehbar. Der Objektmanipulator kann so konfiguriert werden, dass gesteuert wird, wie das Objekt auf verschiedene Eingaben reagiert. Das Skript sollte mit den meisten Interaktionsformen funktionieren, z. B. HoloLens 2 artikulierte Hand, HoloLens 2 Handlicht, HoloLens 1 Anvisierten und Gesten und immersive Headset-Motion Controller-Eingaben.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a>Verwenden des Objektmanipulators

Um den Objektmanipulator zu verwenden, fügen Sie zunächst die `ObjectManipulator` Skriptkomponente einem GameObject hinzu. Stellen Sie sicher, dass Sie dem Objekt auch einen Collider hinzufügen, der den ziehbaren Grenzen entspricht.

Damit das Objekt auf nahezu artikulierte Handeingaben reagiert, fügen Sie auch das `NearInteractionGrabbable` Skript hinzu.

Physikalisches Verhalten kann für den Objektmanipulator aktiviert werden, indem dem Objekt eine Starrkörperkomponente hinzugefügt wird. Physikalisches Verhalten, das durch Hinzufügen dieser Komponente ermöglicht wird, wird ausführlicher unter [*Physik und Kollisionen*](#physics-and-collisions)erläutert.

Darüber hinaus kann die Bearbeitung eingeschränkt werden, indem dem Objekt [Manipulationseinschränkungskomponenten](constraint-manager.md#transform-constraints) hinzugefügt werden. Dies sind spezielle Komponenten, die mit Manipulationen arbeiten und das Manipulationsverhalten in irgendeiner Weise ändern.

![Verwenden des Manipulationshandlers im Unity-Editor](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>Inspektoreigenschaften und -felder

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>Allgemeine Eigenschaften

#### <a name="host-transform"></a>Hosttransformation

Die Objekttransformation, die bearbeitet wird. Der Standardwert ist das -Objekt der Komponente.

#### <a name="manipulation-type"></a>Manipulationstyp

Gibt an, ob das Objekt mit einer Hand oder zwei Händen bearbeitet werden kann. Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.

- *Einhändige:* Aktiviert eine handhändige Bearbeitung, wenn diese ausgewählt ist.
- *Zweihändige*: Aktiviert zweihändige Bearbeitung, wenn ausgewählt.

#### <a name="allow-far-manipulation"></a>Fernmanipulation zulassen

Gibt an, ob die Bearbeitung mithilfe der fernen Interaktion mit Zeigern erfolgen kann.

### <a name="one-handed-manipulation-properties"></a>Eigenschaften der einhändigen Bearbeitung

#### <a name="one-hand-rotation-mode-near"></a>Ein-Hand-Drehungsmodus in der Nähe

Gibt an, wie sich das Objekt verhält, wenn es mit einer Hand in der Nähe gepackt wird. Diese Optionen funktionieren nur für artikulierte Hände.

- *Drehen um den Objektmittelpunkt:* Das Objekt wird mithilfe der Drehung der Hand gedreht, jedoch um den Objektmittelpunkt. Das Objekt scheint sich bei der Drehung weniger zu bewegen, aber es kann ein Gefühl der Trennung zwischen der Hand und dem Objekt auftreten. Nützlicher für die fernen Interaktionen.
- *Drehen um den Greifenpunkt:* Drehen Sie das Objekt mit der Hand um den Greifenpunkt zwischen dem Daumen und dem Zeigefinger. Es sollte sich so anfühlen, als ob das Objekt von der Hand gehalten wird.

#### <a name="one-hand-rotation-mode-far"></a>One-Hand-Drehungsmodus weit

Gibt an, wie sich das Objekt verhält, wenn es mit einer Hand im Abstand gepackt wird. Diese Optionen funktionieren nur für artikulierte Hände.

- *Drehen um den Objektmittelpunkt:* Drehen Sie das Objekt mithilfe der Drehung der Hand, aber um den Objektmittelpunkt. Nützlich für die Untersuchung in einem Abstand, ohne dass sich der Objektmittelpunkt bewegt, während sich das Objekt dreht.
- *Drehen um den Gierpunkt:* Drehen Sie das Objekt mithilfe der Drehung der Hand, aber um den Zeigerstrahltrefferpunkt. Nützlich für die Überprüfung.

### <a name="two-handed-manipulation-properties"></a>Zweihändige Bearbeitungseigenschaften

#### <a name="two-handed-manipulation-type"></a>Zweihändige Manipulationsart

Gibt an, wie ein Objekt durch zwei Handbearbeitungen transformiert werden kann. Da diese Eigenschaft ein Flag ist, kann eine beliebige Anzahl von Optionen ausgewählt werden.

- *Verschieben:* Verschieben ist zulässig, wenn ausgewählt.
- *Skalierung:* Die Skalierung ist zulässig, wenn diese Option ausgewählt ist.
- *Rotieren:* Die Drehung ist zulässig, wenn diese Option ausgewählt ist.

![Manipulationshandler](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>Einschränkungen

#### <a name="enable-constraints"></a>Aktivieren von Einschränkungen

Diese Einstellung aktiviert den [verknüpften Einschränkungs-Manager.](constraint-manager.md) Transformationsänderungen werden von Einschränkungen verarbeitet, die beim ausgewählten [Einschränkungs-Manager](constraint-manager.md)registriert sind.

#### <a name="constraint-manager"></a>Einschränkungs-Manager

In der Dropdownliste können Sie einen der angefügten [Einschränkungs-Manager](constraint-manager.md)auswählen. Der Objektmanipulator stellt sicher, dass jederzeit ein [Einschränkungs-Manager](constraint-manager.md) angefügt ist.
Beachten Sie, dass mehrere Komponenten desselben Typs in Unity unter demselben Namen angezeigt werden. Um die Unterscheidung zwischen mehreren Einschränkungs-Managern für dasselbe Objekt zu vereinfachen, zeigen die verfügbaren Optionen einen Hinweis auf die Konfiguration des ausgewählten Einschränkungs-Managers an (manuelle oder automatische Einschränkungsauswahl).

#### <a name="go-to-component"></a>Zur Komponente wechseln

Die Auswahl des Einschränkungs-Managers enthält die Schaltfläche *Zu Komponente* wechseln. Diese Schaltfläche bewirkt, dass der Inspektor zur ausgewählten Komponente scrollt, damit sie konfiguriert werden kann.

### <a name="physics"></a>Physische Effekte

Einstellungen in diesem Abschnitt werden nur angezeigt, wenn das Objekt über eine RigidBody-Komponente verfügt.

#### <a name="release-behavior"></a>Releaseverhalten

Geben Sie an, welche physischen Eigenschaften ein bearbeitetes Objekt bei der Freigabe beibehalten soll. Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.

- *Geschwindigkeit beibehalten:* Wenn das Objekt freigegeben wird, bleibt die lineare Geschwindigkeit erhalten, wenn diese Option ausgewählt ist.
- *Keep Angular Velocity (Geschwindigkeit* beibehalten): Wenn das Objekt freigegeben wird, bleibt die Winkelgeschwindigkeit erhalten, wenn diese Option ausgewählt ist.

#### <a name="use-forces-for-near-manipulation"></a>Verwenden von Zwingen zur nahezuen Manipulation

Gibt an, ob physikalische Zwingen verwendet werden, um das Objekt zu verschieben, wenn nah an Bearbeitungen vorzugehen ist. Wenn Sie diese Einstellung auf *FALSE* festlegen, wird das Objekt direkt mit der Hand des Benutzers verbunden. Wenn sie auf *"true"* festgelegt wird, werden die Massen und Trägheit des Objekts berücksichtigt, aber es kann sich so anfühlen, als wäre das Objekt über eine Feder verbunden. Der Standardwert ist *FALSE*.

### <a name="smoothing"></a>Glättung

#### <a name="smoothing-far"></a>Glättung weit entfernt

Gibt an, ob die unabhängige Glättung der Bildfrequenz für fernen Interaktionen aktiviert ist. Die Far Smoothing-Funktion ist standardmäßig aktiviert.

#### <a name="smoothing-near"></a>Glättung in der Nähe

Gibt an, ob die unabhängige Glättung der Bildfrequenz für Interaktionen in der Nähe aktiviert ist. Die nahezue Glättung ist standardmäßig deaktiviert, da der Effekt als "getrennt" von der Hand wahrgenommen werden kann.

#### <a name="smoothing-active"></a>Glättung aktiv

Veraltet und wird in einer zukünftigen Version entfernt. Anwendungen sollten SmoothingFar, SmoothingNear oder eine Kombination aus beiden verwenden.

#### <a name="move-lerp-time"></a>Move lerp time

Umfang der Glättung, die auf die Bewegung angewendet werden soll. Glättung von 0 bedeutet keine Glättung. Max value bedeutet, dass keine Änderung am Wert vorfällt.

#### <a name="rotate-lerp-time"></a>Drehungszeit

Umfang der Glättung, die auf die Drehung angewendet werden soll. Glättung von 0 bedeutet keine Glättung. Max value bedeutet, dass keine Änderung am Wert vorfällt.

#### <a name="scale-lerp-time"></a>Skalieren der Lerp-Zeit

Umfang der Glättung, die auf die Skala angewendet werden soll. Eine Glättung von 0 bedeutet keine Glättung. Der maximale Wert bedeutet, dass kein Wert geändert wird.

### <a name="manipulation-events"></a>Bearbeitungsereignisse

Der Manipulationshandler stellt die folgenden Ereignisse zur Verfügung:

- *OnManipulationStarted:* Wird ausgelöst, wenn die Bearbeitung beginnt.
- *OnManipulationEnded:* Wird beim Ende der Bearbeitung aus.
- *OnHoverStarted:* Wird bei einem Hand-/Controller-Hover auf das manipulatable-, nah- oder fern-Paar aus.
- *OnHoverEnded:* Wird aus, wenn eine Hand/ein Controller das manipulatable in der Nähe oder weit entfernt entlädt.

Die Reihenfolge der Ereignislöschung für die Bearbeitung ist:

*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*

Wenn keine Bearbeitung vorkommt, erhalten Sie immer noch Hoverereignisse mit der folgenden Brandreihen reihenfolge:

*OnHoverStarted*  ->  *OnHoverEnded*

## <a name="physics-and-collisions"></a>Physik und Kollisionen

Physikalisches Verhalten kann aktiviert werden, indem demselben Objekt wie einem Objektmanipulator eine Festkörperkomponente hinzugefügt wird. Dies ermöglicht nicht nur die oben beschriebene Konfiguration des [Releaseverhaltens,](#release-behavior) sondern auch Kollisionen. Ohne eine Festkörperkomponente verhalten sich Kollisionen während der Bearbeitung nicht richtig:

- Kollisionen zwischen einem manipulierten Objekt und einem statischen Collider (d. h. ein Objekt mit einem Collider, aber ohne Festkörper) funktionieren nicht, das bearbeitete Objekt durchläuft den statischen Collider unbeeinflusst.
- Kollisionen zwischen einem manipulierten Objekt und einem Festkörper (d. h. ein Objekt mit einem Collider und einem starren Objekt) dazu führen, dass der Starrer eine Kollisionsantwort hat, aber die Antwort ist sprungig und unnatürlich. Es gibt auch keine Kollisionsantwort für das bearbeitete Objekt.

Wenn ein Festkörper hinzugefügt wird, sollten Kollisionen ordnungsgemäß funktionieren.

### <a name="without-rigidbody"></a>Ohne Festkörper

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>Mit "rigidbody"

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>Elastische Datenbanken (experimentell)

Elastische Datenbanken können beim Bearbeiten von Objekten über objektmanipulator verwendet werden. Beachten Sie, [dass sich das Elastiksystem](../experimental/elastic-system.md) noch im experimentellen Zustand befindet. Um elastische Datenbanken zu aktivieren, verknüpfen Sie entweder eine vorhandene Elastics Manager-Komponente, oder erstellen und verknüpfen Sie über die Schaltfläche einen neuen `Add Elastics Manager` Elastik-Manager.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>Siehe auch

- [Begrenzungssteuerelement](bounds-control.md)
- [Einschränkungs-Manager](constraint-manager.md)
- [Migrationszeitfenster](../tools/migration-window.md)
- [Elastisches System (experimentell)](../experimental/elastic-system.md)
