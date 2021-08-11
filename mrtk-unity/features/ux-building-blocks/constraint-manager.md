---
title: Einschränkungs-Manager
description: Übersicht über den Einschränkungs-Manager in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: f32f7321ec30f337e03d006f47fa92639796a74156483917331304811ea86a45
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198480"
---
# <a name="constraint-manager"></a>Einschränkungs-Manager

Der Einschränkungs-Manager ermöglicht das Anwenden eines Satzes von Einschränkungskomponenten auf eine Transformation. Komponenten vom Typ [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) , die an das Spielobjekt angefügt sind, können berücksichtigt werden.
Standardmäßig erfasst der Einschränkungs-Manager automatisch alle [Einschränkungskomponenten,](#transform-constraints) die an das Spielobjekt angefügt sind, und wendet sie auf verarbeitete Transformationen an.
Benutzer können sich jedoch dafür entscheiden, die Liste der angewendeten Einschränkungen manuell zu konfigurieren und nur eine Teilmenge der angefügten Einschränkungen anzuwenden.

Derzeit unterstützen die folgenden MRTK-UX-Elemente den Einschränkungs-Manager:

- [Begrenzungssteuerelement](bounds-control.md)
- [Objektmanipulator](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>Inspektoreigenschaften und -felder

Der Einschränkungs-Manager kann in zwei Modi betrieben werden:

- Auswahl der automatischen Einschränkung
- Manuelle Einschränkungsauswahl

### <a name="auto-constraint-selection"></a>Auswahl der automatischen Einschränkung

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

Der Standardmodus des Einschränkungs-Managers, die automatische Einschränkungsauswahl, stellt eine Liste aller angefügten [Einschränkungskomponenten](#go-to-component) bereit und wechselt zu Schaltflächen und einer Schaltfläche zum Hinzufügen von [Einschränkungen.](#add-constraint-to-game-object)

#### <a name="add-constraint-to-game-object"></a>Hinzufügen einer Einschränkung zum Spielobjekt

Mit dieser Schaltfläche kann eine Einschränkungskomponente direkt vom Einschränkungs-Manager-Inspektor hinzugefügt werden. Alle Einschränkungstypen in einem Projekt sollten hier sichtbar sein. Weitere Informationen finden Sie unter [Transformationseinschränkungen.](#transform-constraints)

#### <a name="go-to-component"></a>Zur Komponente wechseln

Alle für das Objekt gefundenen Einschränkungen werden hier mit der Schaltfläche *Zu Komponente* wechseln aufgelistet. Diese Schaltfläche bewirkt, dass der Inspektor zur ausgewählten Einschränkungskomponente scrollt, damit sie konfiguriert werden kann.

### <a name="manual-constraint-selection"></a>Manuelle Einschränkungsauswahl

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

Wenn der Einschränkungs-Manager auf den manuellen Modus festgelegt ist, werden nur Einschränkungen verarbeitet und auf die Transformation angewendet, die in der Einschränkungsliste verknüpft sind. In der angezeigten Liste werden nur die vom Benutzer ausgewählten Einschränkungen sowie [Schaltflächen](#go-to-component) oder Optionen zum Entfernen oder Hinzufügen von Einträgen angezeigt.
Beim erstmaligen Aktivieren des manuellen Modus füllt der Einschränkungs-Manager die Liste mit allen verfügbaren Komponenten als Ausgangspunkt für die Auswahl angefügter Einschränkungskomponenten auf.

### <a name="remove-entry"></a>Eintrag entfernen

Dadurch wird der Eintrag aus der manuell ausgewählten Liste entfernt. Beachten Sie, dass diese Option die Einschränkungskomponente nicht aus dem Spielobjekt entfernt. Einschränkungskomponenten müssen immer manuell entfernt werden, um sicherzustellen, dass keine andere Komponente, die auf diese Komponente verweist, versehentlich getrennt wird.

### <a name="add-entry"></a>Eintrag hinzufügen

Eintrag hinzufügen öffnet eine Dropdownliste mit allen verfügbaren Einschränkungskomponenten, die noch nicht in der manuellen Liste enthalten sind. Durch Klicken auf einen der Einträge, die der manuellen Einschränkungsauswahl hinzugefügt werden.

### <a name="add-new-constraint"></a>Hinzufügen einer neuen Einschränkung

Mit dieser Option wird dem Spielobjekt eine Komponente des ausgewählten Typs und die neu erstellte Einschränkungskomponente der Liste manueller Einschränkungen hinzugefügt.

## <a name="transform-constraints"></a>Transformationseinschränkungen

Einschränkungen können verwendet werden, um die Bearbeitung in irgendeiner Weise einzuschränken. Einige Anwendungen erfordern z. B. eine Drehung, erfordern aber auch, dass das Objekt aufrecht bleibt. In diesem Fall kann dem -Objekt ein `RotationAxisConstraint` hinzugefügt und verwendet werden, um die Drehung auf die Drehung der y-Achse zu beschränken. MRTK bietet eine Reihe von Einschränkungen, die alle unten beschrieben werden.

Es ist auch möglich, neue Einschränkungen zu definieren und sie zu verwenden, um ein eindeutiges Bearbeitungsverhalten zu schaffen, das für einige Anwendungen erforderlich sein kann. Erstellen Sie hierzu ein Skript, das von [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) erbt, und implementieren Sie die abstrakte Eigenschaft und die abstrakte `ConstraintType` `ApplyConstraint` Methode. Beim Hinzufügen einer neuen Einschränkung zum -Objekt sollte die Bearbeitung auf die art und Weise eingeschränkt werden, die definiert wurde. Diese neue Einschränkung sollte auch in der Dropdownliste für die [automatische Auswahl](#auto-constraint-selection) des Einschränkungs-Managers oder in der Dropdownliste ["Eintrag"](#add-entry) im manuellen Modus angezeigt werden.

Alle vom MRTK bereitgestellten Einschränkungen haben die folgenden Eigenschaften:

#### <a name="hand-type"></a>Handtyp

Gibt an, ob die Einschränkung für eine handliche, zweihändige oder beide Manipulationsarten verwendet wird. Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.

- *Einhändige*: Die Einschränkung wird während einer Handbearbeitung verwendet, wenn diese ausgewählt ist.
- *Zweihändige*: Die Einschränkung wird während der zweihändigen Bearbeitung verwendet, falls ausgewählt.

#### <a name="proximity-type"></a>Näherungstyp

Gibt an, ob die Einschränkung für nahezu, fern oder beide Bearbeitungsarten verwendet wird. Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.

- *Near*: Die Einschränkung wird während der bearbeitungsnahen Bearbeitung verwendet, wenn diese Option ausgewählt ist.
- *Far:* Die Einschränkung wird während der Fernbearbeitung verwendet, wenn diese Option ausgewählt ist.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

Wenn diese Einschränkung an ein Objekt angefügt ist, wird die Drehung eingeschränkt, sodass das Objekt immer dem Benutzer angezeigt wird. Dies ist nützlich für Schiefer oder Panels. Die Eigenschaften für `FaceUserConstraint` sind wie folgt:

#### <a name="face-away"></a>Gesichtsabsicht

Das Objekt ist vom Benutzer entfernt, wenn "true" ist.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

Diese Einschränkung behebt den Abstand zwischen dem bearbeiteten Objekt und einer anderen Objekttransformation beim Manipulationsstart. Dies ist nützlich für Verhalten wie das Korrigieren des Abstands zwischen dem bearbeiteten Objekt und der Kopftransformation. Die Eigenschaften für `FixedDistanceConstraint` sind wie folgt:

#### <a name="constraint-transform"></a>Einschränkungstransformation

Dies ist die andere Transformation, zu der das bearbeitete Objekt einen festen Abstand hat. Standardmäßig wird die Kameratransformation verwendet.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

Diese Einschränkung behebt die relative Drehung zwischen dem Benutzer und dem bearbeiteten Objekt, während es bearbeitet wird. Dies ist nützlich für Schiefer oder Bereiche, da dadurch sichergestellt wird, dass das bearbeitete Objekt dem Benutzer immer das gleiche Gesicht zeigt wie zu Beginn der Bearbeitung. `FixedRotationToUserConstraint`Der verfügt über keine eindeutigen Eigenschaften.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

Diese Einschränkung behebt die globale Drehung des bearbeiteten Objekts, während es bearbeitet wird. Dies kann in Fällen nützlich sein, in denen keine Drehung durch Manipulation vermittelt werden soll. `FixedRotationToWorldConstraint`Der verfügt über keine eindeutigen Eigenschaften:

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

Wenn diese Einschränkung an ein Objekt angefügt wird, wird unabhängig davon, wie weit das Objekt vom Benutzer entfernt ist, die gleiche offensichtliche Größe für den Benutzer beibehalten (d. h., es nimmt den gleichen Anteil des Sichtfelds des Benutzers in Anspruch). Dies kann verwendet werden, um sicherzustellen, dass ein Slate- oder Textbereich während der Bearbeitung lesbar bleibt. `MaintainApparentSizeConstraint`Der verfügt über keine eindeutigen Eigenschaften:

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

Diese Einschränkung kann verwendet werden, um zu korrigieren, auf welche Achsen ein bearbeitetes Objekt verschoben werden kann. Dies kann nützlich sein, um Objekte über die Oberfläche einer Ebene oder entlang einer Linie zu bearbeiten. Die Eigenschaften für `MoveAxisConstraint` sind wie folgt:

#### <a name="constraint-on-movement"></a>Einschränkung für Die Verschiebung

Gibt an, auf welche Achsen die Verschiebung verhindert werden soll. Standardmäßig sind diese Achsen global und nicht lokal, aber dies kann unten geändert werden. Da diese Eigenschaft ein Flag ist, kann eine beliebige Anzahl von Optionen ausgewählt werden.

- *X-Achse:* Die Bewegung entlang der x-Achse ist eingeschränkt, wenn ausgewählt.
- *Y-Achse:* Die Bewegung entlang der y-Achse wird eingeschränkt, wenn sie ausgewählt ist.
- *Z-Achse:* Die Bewegung entlang der Z-Achse ist bei Auswahl von eingeschränkt.

#### <a name="use-local-space-for-constraint"></a>Verwenden des lokalen Speicherplatzes für Einschränkungen

Schränkt relativ die lokalen Transformationsachsen des bearbeiteten Objekts ein, wenn true ist. Der Standardwert ist gleich „False“.

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

Diese Einschränkung kann verwendet werden, um zu korrigieren, welche Achsen ein bearbeitetes Objekt drehen kann. Dies kann nützlich sein, um ein bearbeitetes Objekt aufrecht zu halten, aber dennoch y-Achsenrotationen zuzulassen, z. B. . Die Eigenschaften für `RotationAxisConstraint` sind wie folgt:

#### <a name="constraint-on-rotation"></a>Einschränkung bei der Drehung

Gibt an, um welche Achsen die Drehung verhindert werden soll. Standardmäßig sind diese Achsen global und nicht lokal, aber dies kann unten geändert werden. Da diese Eigenschaft ein Flag ist, kann eine beliebige Anzahl von Optionen ausgewählt werden.

- *Y-Achse:* Die Drehung um die y-Achse wird eingeschränkt, wenn diese option ausgewählt ist.
- *Z-Achse:* Die Drehung um die Z-Achse wird eingeschränkt, wenn sie ausgewählt ist.
- *X-Achse:* Die Drehung um die x-Achse ist eingeschränkt, wenn diese ausgewählt ist.

#### <a name="use-local-space-for-constraint"></a>Verwenden von lokalem Speicherplatz für Einschränkungen

Schränkt relative lokale Transformationsachsen des bearbeiteten Objekts ein, wenn true. Der Standardwert ist gleich „False“.

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

Diese Einschränkung ermöglicht das Festlegen von Minimal- und Höchstwerten für die Skalierung des bearbeiteten Objekts. Dies ist nützlich, um zu verhindern, dass Benutzer ein Objekt zu klein oder zu groß skalieren. Die Eigenschaften `MinMaxScaleConstraint` für lauten wie folgt:

#### <a name="scale-minimum"></a>Minimal skalieren

Der minimale Skalierungswert während der Bearbeitung.

#### <a name="scale-maximum"></a>Maximale Skalierung

Der maximale Skalierungswert während der Bearbeitung.

#### <a name="relative-to-initial-state"></a>Relativ zum Anfangszustand

True gibt an, dass die oben genannten Werte als relativ zur anfänglichen Skalierung der Objekte interpretiert werden. Andernfalls werden sie als absolute Skalierungswerte interpretiert.
