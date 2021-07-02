---
title: Objektmanipulator
description: Verwenden des Objektmanipulators in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Objektbearbeitung,
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176657"
---
# <a name="object-manipulator"></a>Objektmanipulator

![Objektmanipulator](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ObjectManipulator ist* die neue Komponente für Manipulationsverhalten, die zuvor in *ManipulationHandler gefunden wurde.* Der Objektmanipulator macht eine Reihe von Verbesserungen und Vereinfachungen. Diese Komponente ist ein Ersatz für den Manipulationshandler, der veraltet ist.

Das *ObjectManipulator-Skript* macht ein Objekt mit einem oder zwei Händen verschiebbar, skalierbar und drehbar. Der Objektmanipulator kann konfiguriert werden, um zu steuern, wie das Objekt auf verschiedene Eingaben reagiert. Das Skript sollte mit den meisten Formen der Interaktion funktionieren, z. B. HoloLens 2 Artikulierte Hand, HoloLens 2 Handlichtlicht, HoloLens 1 Anvisiert und Gesten und immersive Headset-Bewegungscontrollereingabe.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a>Verwenden des Objektmanipulators

Um den Objektmanipulator zu verwenden, fügen Sie zunächst die `ObjectManipulator` Skriptkomponente einem GameObject hinzu. Stellen Sie sicher, dass Sie dem Objekt auch einen Collider hinzufügen, der dessen ziehbaren Grenzen anpasst.

Fügen Sie auch das Skript hinzu, damit das Objekt auf Eingaben nahezu `NearInteractionGrabbable` artikulierter Hand reagiert.

Physikalisches Verhalten kann für den Objektmanipulator aktiviert werden, indem dem Objekt eine Festkörperkomponente hinzugefügt wird. Physikalisches Verhalten, das durch Hinzufügen dieser Komponente aktiviert wird, wird unter [*Physik und Kollisionen ausführlicher erläutert.*](#physics-and-collisions)

Ebenso kann die Bearbeitung eingeschränkt werden, indem dem Objekt [Manipulationseinschränkungskomponenten](constraint-manager.md#transform-constraints) hinzugefügt werden. Hierbei handelt es sich um spezielle Komponenten, die mit Manipulation arbeiten und das Manipulationsverhalten in irgendeiner Weise ändern.

![Verwenden des Manipulationshandlers im Unity-Editor](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>Inspektoreigenschaften und -felder

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>Allgemeine Eigenschaften

#### <a name="host-transform"></a>Hosttransformation

Die Objekttransformation, die bearbeitet wird. Der Standardwert ist das -Objekt der Komponente.

#### <a name="manipulation-type"></a>Manipulationstyp

Gibt an, ob das Objekt mit einer Hand oder zwei Händen bearbeitet werden kann. Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.

- *Einhändig:* Aktiviert eine handhändige Bearbeitung, wenn diese ausgewählt ist.
- *Zweihändig:* Aktiviert zweihändige Manipulationen, wenn diese ausgewählt sind.

#### <a name="allow-far-manipulation"></a>Fernbearbeitung zulassen

Gibt an, ob die Bearbeitung mithilfe der Ferninteraktion mit Zeigern erfolgen kann.

### <a name="one-handed-manipulation-properties"></a>Einhändige Manipulationseigenschaften

#### <a name="one-hand-rotation-mode-near"></a>Drehmodus mit einer Hand in der Nähe

Gibt an, wie sich das Objekt verhält, wenn es mit einer Hand in der Nähe greifst. Diese Optionen funktionieren nur für artikulierte Hände.

- *Drehen um objektzentriert:* Das Objekt dreht sich mithilfe der Drehung der Hand, aber um den Objektzentriertpunkt. Das Objekt scheint sich während der Drehung weniger zu bewegen, aber es kann ein Gefühl der Trennung zwischen der Hand und dem Objekt auftreten. Nützlicher für die Ferninteraktion.
- *Drehen um den Greifpunkt:* Drehen Sie das Objekt mit der Hand um den Greifpunkt zwischen dem Greifpunkt und dem Zeigefinger. Es sollte sich so anfühlen, als würde das Objekt von der Hand gehalten.

#### <a name="one-hand-rotation-mode-far"></a>One-Hand-Drehungsmodus weit

Gibt an, wie sich das Objekt verhält, wenn es mit einer Hand aus der Entfernung greifst. Diese Optionen funktionieren nur für artikulierte Hände.

- *Drehen um objektzentriert:* Drehen Sie das Objekt mithilfe einer Drehung der Hand, aber um den Objektzentriertpunkt. Nützlich für die Untersuchung aus der Entfernung, ohne dass sich der Objektzentriert während der Objektdrehung bewegt.
- *Drehen um den Greifpunkt:* Drehen Sie das Objekt mithilfe der Drehung der Hand, aber um den Zeigerstrahl-Trefferpunkt. Nützlich für die Überprüfung.

### <a name="two-handed-manipulation-properties"></a>Zweihändige Manipulationseigenschaften

#### <a name="two-handed-manipulation-type"></a>Zweihändiger Manipulationstyp

Gibt an, wie zwei Handmanipulationen ein Objekt transformieren können. Da diese Eigenschaft ein Flag ist, kann eine beliebige Anzahl von Optionen ausgewählt werden.

- *Verschieben:* Das Verschieben ist zulässig, wenn diese Option ausgewählt ist.
- *Skalierung:* Die Skalierung ist zulässig, wenn diese Option ausgewählt ist.
- *Rotieren:* Die Drehung ist zulässig, wenn diese Option ausgewählt ist.

![Manipulationshandler](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>Einschränkungen

#### <a name="enable-constraints"></a>Aktivieren von Einschränkungen

Diese Einstellung aktiviert den verknüpften [Einschränkungs-Manager.](constraint-manager.md) Transformationsänderungen werden von Einschränkungen verarbeitet, die für den ausgewählten Einschränkungs-Manager [registriert sind.](constraint-manager.md)

#### <a name="constraint-manager"></a>Einschränkungs-Manager

In der Dropdownliste können Sie einen der angefügten [Einschränkungs-Manager auswählen.](constraint-manager.md) Der Objektmanipulator stellt sicher, dass [jederzeit](constraint-manager.md) ein Einschränkungs-Manager angefügt ist.
Beachten Sie, dass mehrere Komponenten desselben Typs in Unity unter demselben Namen zu sehen sind. Um die Unterscheidung zwischen mehreren Einschränkungs-Managern für dasselbe Objekt zu vereinfachen, zeigen die verfügbaren Optionen einen Hinweis zur Konfiguration des ausgewählten Einschränkungs-Managers (manuelle oder automatische Einschränkungsauswahl) an.

#### <a name="go-to-component"></a>Zu Komponente wechseln

Die Einschränkungs-Manager-Auswahl verfügt über die *Schaltfläche Zu Komponente* wechseln. Diese Schaltfläche führt dazu, dass der Inspektor zur ausgewählten Komponente scrollt, damit sie konfiguriert werden kann.

### <a name="physics"></a>Physische Effekte

Einstellungen in diesem Abschnitt werden nur angezeigt, wenn das Objekt über eine RigidBody-Komponente verfügt.

#### <a name="release-behavior"></a>Releaseverhalten

Geben Sie an, welche physischen Eigenschaften ein bearbeitetes Objekt bei der Freigabe behalten soll. Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.

- *Geschwindigkeit behalten:* Wenn das Objekt freigegeben wird und diese Option ausgewählt ist, bleibt die lineare Geschwindigkeit erhalten.
- *Geschwindigkeit Angular:* Wenn das Objekt freigegeben wird und diese Option ausgewählt ist, bleibt die Winkelgeschwindigkeit erhalten.

#### <a name="use-forces-for-near-manipulation"></a>Verwenden von Struppen für die nahezue Manipulation

Gibt an, ob physikalische Struppen verwendet werden, um das Objekt zu verschieben, wenn nahe Manipulationen angewendet werden. Wenn sie auf *FALSE festgelegt wird,* wird das Objekt direkter mit der Benutzerhand verbunden. Wenn Sie diese Einstellung *auf TRUE* festlegen, werden die Massen- und Trägheit des Objekts erfüllt, aber es kann sich so anfühlen, als ob das Objekt über eine Feder verbunden wäre. Der Standardwert ist *FALSE*.

### <a name="smoothing"></a>Glättung

#### <a name="smoothing-far"></a>Glättung weit

Gibt an, ob die bildratenunabhängige Glättung für Ferninteraktionen aktiviert ist. Far Smoothing ist standardmäßig aktiviert.

#### <a name="smoothing-near"></a>Glättung in der Nähe

Gibt an, ob die bildratenunabhängige Glättung für nahezu alle Interaktionen aktiviert ist. Die Nahezuglättung ist standardmäßig deaktiviert, da der Effekt möglicherweise als "getrennt" von der Hand wahrgenommen wird.

#### <a name="smoothing-active"></a>Glättung aktiv

Veraltet und werden in einer zukünftigen Version entfernt. Anwendungen sollten SmoothingFar, SmoothingNear oder eine Kombination aus beiden verwenden.

#### <a name="move-lerp-time"></a>Lerpzeit verschieben

Der Glättungsbetrag, der auf die Bewegung angewendet werden soll. Eine Glättung von 0 bedeutet keine Glättung. Der maximale Wert bedeutet, dass kein Wert geändert wird.

#### <a name="rotate-lerp-time"></a>Rotieren der Lerpzeit

Die Glättungsmenge, die auf die Drehung angewendet werden soll. Eine Glättung von 0 bedeutet keine Glättung. Der maximale Wert bedeutet, dass kein Wert geändert wird.

#### <a name="scale-lerp-time"></a>Skalieren der Lerpzeit

Umfang der Glättung, die auf die Skala angewendet werden soll. Eine Glättung von 0 bedeutet keine Glättung. Der maximale Wert bedeutet, dass keine Änderung des Werts vor sich geht.

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

Physikalisches Verhalten kann aktiviert werden, indem demselben Objekt wie einem Objektmanipulator eine Festkörperkomponente hinzugefügt wird. Dies ermöglicht nicht nur die oben beschriebene Konfiguration des [Releaseverhaltens,](#release-behavior) sondern auch Kollisionen. Ohne eine Festkörperkomponente verhalten sich Kollisionen während der Bearbeitung nicht ordnungsgemäß:

- Kollisionen zwischen einem manipulierten Objekt und einem statischen Collider (d. h. ein Objekt mit einem Collider, aber ohne Festkörper) funktionieren nicht, das bearbeitete Objekt durchläuft den statischen Collider unbeeinflusst.
- Kollisionen zwischen einem manipulierten Objekt und einem Festkörper (d. h. ein Objekt mit einem Collider und einem starren Objekt) dazu führen, dass der Starrer eine Kollisionsantwort hat, aber die Antwort ist sprungig und unnatürlich. Es gibt auch keine Kollisionsantwort für das bearbeitete Objekt.

Wenn ein Festkörper hinzugefügt wird, sollten Kollisionen ordnungsgemäß funktionieren.

### <a name="without-rigidbody"></a>Ohne Festkörper

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>Mit "rigidbody"

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>Elastische Datenbanken (experimentell)

Elastische Datenbanken können beim Bearbeiten von Objekten über den Objektmanipulator verwendet werden. Beachten Sie, [dass sich das Elastiksystem](../experimental/elastic-system.md) noch im experimentellen Zustand befindet. Um elastische Datenbanken zu aktivieren, verknüpfen Sie entweder eine vorhandene Elastics Manager-Komponente, oder erstellen und verknüpfen Sie über die Schaltfläche einen neuen `Add Elastics Manager` Elastik-Manager.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>Siehe auch

- [Steuerelement "Begrenzungen"](bounds-control.md)
- [Einschränkungs-Manager](constraint-manager.md)
- [Migrationszeitfenster](../tools/migration-window.md)
- [Elastisches System (experimentell)](../experimental/elastic-system.md)
