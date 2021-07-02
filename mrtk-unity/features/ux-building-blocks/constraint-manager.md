---
title: Einschränkungs-Manager
description: Übersicht über den Einschränkungs-Manager in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177549"
---
# <a name="constraint-manager"></a>Einschränkungs-Manager

Der Einschränkungs-Manager ermöglicht das Anwenden einer Gruppe von Einschränkungskomponenten auf eine Transformation. Komponenten vom Typ [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) , die an das Spielobjekt angefügt sind, können berücksichtigt werden.
Standardmäßig erfasst der Einschränkungs-Manager [](#transform-constraints) automatisch alle Einschränkungskomponenten, die an das Spielobjekt angefügt sind, und wenden sie auf verarbeitete Transformationen an.
Benutzer können sich jedoch dafür entscheiden, die Liste der angewendeten Einschränkungen manuell zu konfigurieren und nur eine Teilmenge der angefügten Einschränkungen anzuwenden.

Derzeit unterstützen die folgenden MRTK-UX-Elemente den Einschränkungs-Manager:

- [Steuerelement "Begrenzungen"](bounds-control.md)
- [Objektmanipulator](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>Inspektoreigenschaften und -felder

Der Einschränkungs-Manager kann in zwei Modi betrieben werden:

- Automatische Einschränkungsauswahl
- Manuelle Einschränkungsauswahl

### <a name="auto-constraint-selection"></a>Automatische Einschränkungsauswahl

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

Der Standardmodus des Einschränkungs-Managers, die automatische Einschränkungsauswahl, stellt [](#go-to-component) eine Liste aller angefügten Einschränkungskomponenten sowie Schaltflächen und eine Schaltfläche zum Hinzufügen von [Einschränkungen zur Verfügung.](#add-constraint-to-game-object)

#### <a name="add-constraint-to-game-object"></a>Hinzufügen einer Einschränkung zum Spielobjekt

Mit dieser Schaltfläche kann eine Einschränkungskomponente direkt aus dem Einschränkungs-Manager-Inspektor hinzugefügt werden. Alle Einschränkungstypen in einem Projekt sollten hier angezeigt werden. Weitere [Informationen finden Sie unter Transformationseinschränkungen.](#transform-constraints)

#### <a name="go-to-component"></a>Zu Komponente wechseln

Alle Einschränkungen, die für das Objekt gefunden werden, werden hier mit der Schaltfläche *Zu Komponente wechseln* aufgelistet. Diese Schaltfläche führt dazu, dass der Inspektor zur ausgewählten Einschränkungskomponente scrollt, damit sie konfiguriert werden kann.

### <a name="manual-constraint-selection"></a>Manuelle Einschränkungsauswahl

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

Wenn der Einschränkungs-Manager auf den manuellen Modus festgelegt ist, werden nur Einschränkungen verarbeitet und auf die Transformation angewendet, die in der Einschränkungsliste verknüpft sind. In der angezeigten Liste werden nur die [](#go-to-component) vom Benutzer ausgewählten Einschränkungen angezeigt, und es werden Schaltflächen oder Optionen zum Entfernen oder Hinzufügen von Einträgen angezeigt.
Wenn der manuelle Modus zum ersten Mal aktiviert wird, füllt der Einschränkungs-Manager die Liste mit allen verfügbaren Komponenten als Ausgangspunkt für die Auswahl angefügter Einschränkungskomponenten auf.

### <a name="remove-entry"></a>Eintrag entfernen

Dadurch wird der Eintrag aus der manuell ausgewählten Liste entfernt. Beachten Sie, dass diese Option die Einschränkungskomponente nicht aus dem Spielobjekt entfernt. Einschränkungskomponenten müssen immer manuell entfernt werden, um sicherzustellen, dass keine andere Komponente, die auf diese Komponente verweist, versehentlich unterbricht.

### <a name="add-entry"></a>Eintrag hinzufügen

Durch Hinzufügen eines Eintrags wird eine Dropdownliste mit allen verfügbaren Einschränkungskomponenten geöffnet, die noch nicht in der manuellen Liste enthalten sind. Durch Klicken auf einen der Einträge, die der manuellen Einschränkungsauswahl hinzugefügt werden.

### <a name="add-new-constraint"></a>Hinzufügen einer neuen Einschränkung

Mit dieser Option wird dem Spielobjekt eine Komponente des ausgewählten Typs und die neu erstellte Einschränkungskomponente der Liste der manuellen Einschränkungen hinzugefügt.

## <a name="transform-constraints"></a>Transformieren von Einschränkungen

Einschränkungen können verwendet werden, um die Bearbeitung auf irgendeine Weise zu beschränken. Einige Anwendungen erfordern z. B. möglicherweise eine Drehung, aber auch, dass das Objekt aufrecht bleibt. In diesem Fall kann dem -Objekt ein hinzugefügt und verwendet werden, um die Drehung auf die `RotationAxisConstraint` Drehung der y-Achse zu beschränken. MRTK bietet eine Reihe von Einschränkungen, die alle unten beschrieben werden.

Es ist auch möglich, neue Einschränkungen zu definieren und diese zu verwenden, um ein eindeutiges Manipulationsverhalten zu erstellen, das für einige Anwendungen erforderlich sein kann. Erstellen Sie hierzu ein Skript, das von erbt, [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) und implementieren Sie die abstrakte Eigenschaft und die abstrakte `ConstraintType` `ApplyConstraint` Methode. Beim Hinzufügen einer neuen Einschränkung zum -Objekt sollte die Bearbeitung auf die definierte Weise eingeschränkt werden. Diese neue Einschränkung sollte auch in der automatischen Auswahl des [Einschränkungs-Managers oder](#auto-constraint-selection) in der [Dropdownliste "Eintrag](#add-entry) hinzufügen" im manuellen Modus angezeigt werden.

Alle vom MRTK bereitgestellten Einschränkungen haben die folgenden Eigenschaften:

#### <a name="hand-type"></a>Handtyp

Gibt an, ob die Einschränkung für eine handändige, zweihändige oder beide Manipulationsarten verwendet wird. Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.

- *Einhändig:* Die Einschränkung wird bei einer handhändigen Bearbeitung verwendet, sofern diese ausgewählt ist.
- *Zweihändig:* Die Einschränkung wird während der zweihändigen Bearbeitung verwendet, sofern diese ausgewählt ist.

#### <a name="proximity-type"></a>Näherungstyp

Gibt an, ob die Einschränkung für nahe, fern oder beide Arten von Bearbeitung verwendet wird. Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.

- *Near*: Die Einschränkung wird während der nahezuen Bearbeitung verwendet, sofern diese option ausgewählt ist.
- *Far:* Die Einschränkung wird bei der fernen Bearbeitung verwendet, sofern diese option ausgewählt ist.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

Wenn diese Einschränkung an ein Objekt angefügt wird, wird die Drehung eingeschränkt, sodass das Objekt immer auf den Benutzer zu sehen ist. Dies ist nützlich für Slates oder Panels. Die Eigenschaften `FaceUserConstraint` für lauten wie folgt:

#### <a name="face-away"></a>Gesichtserkennung

Das Objekt ist vom Benutzer entfernt, wenn "true" ist.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

Diese Einschränkung behebt den Abstand zwischen dem bearbeiteten Objekt und einer anderen Objekttransformation beim Start der Bearbeitung. Dies ist nützlich für Verhaltensweisen wie das Korrigieren des Abstands zwischen dem bearbeiteten Objekt und der Kopftransformation. Die Eigenschaften `FixedDistanceConstraint` für lauten wie folgt:

#### <a name="constraint-transform"></a>Einschränkungstransformation

Dies ist die andere Transformation, zu der das bearbeitete Objekt einen festen Abstand hat. Der Standardwert ist die Kameratransformation.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

Diese Einschränkung behebt die relative Drehung zwischen dem Benutzer und dem bearbeiteten Objekt, während es bearbeitet wird. Dies ist für Tafeln oder Bereiche nützlich, da dadurch sichergestellt wird, dass das bearbeitete Objekt dem Benutzer immer das gleiche Gesicht zeigt wie zu Beginn der Bearbeitung. die `FixedRotationToUserConstraint` keine eindeutigen Eigenschaften aufweist.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

Diese Einschränkung behebt die globale Drehung des bearbeiteten Objekts, während es bearbeitet wird. Dies kann in Fällen nützlich sein, in denen keine Drehung durch Manipulationen vermittelt werden soll. die `FixedRotationToWorldConstraint` keine eindeutigen Eigenschaften aufweist:

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

Wenn diese Einschränkung an ein Objekt angefügt wird, behält sie unabhängig davon, wie weit das Objekt vom Benutzer entfernt ist, die gleiche offensichtliche Größe für den Benutzer bei (d. h., es nimmt den gleichen Anteil des Sichtfelds des Benutzers an). Dies kann verwendet werden, um sicherzustellen, dass eine Tafel oder ein Textbereich während der Bearbeitung lesbar bleibt. die `MaintainApparentSizeConstraint` keine eindeutigen Eigenschaften aufweist:

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

Diese Einschränkung kann verwendet werden, um zu korrigieren, auf welchen Achsen ein bearbeitetes Objekt verschoben werden kann. Dies kann nützlich sein, um Objekte über der Oberfläche einer Ebene oder entlang einer Linie zu bearbeiten. Die Eigenschaften `MoveAxisConstraint` für lauten wie folgt:

#### <a name="constraint-on-movement"></a>Einschränkung bei der Bewegung

Gibt an, auf welchen Achsen die Bewegung verhindert werden soll. Standardmäßig sind diese Achsen global und nicht lokal, aber dies kann unten geändert werden. Da diese Eigenschaft ein Flag ist, kann eine beliebige Anzahl von Optionen ausgewählt werden.

- *X-Achse:* Die Bewegung entlang der X-Achse wird eingeschränkt, wenn sie ausgewählt ist.
- *Y-Achse:* Die Bewegung entlang der y-Achse wird eingeschränkt, wenn sie ausgewählt ist.
- *Z-Achse:* Die Bewegung entlang der Z-Achse wird eingeschränkt, wenn sie ausgewählt ist.

#### <a name="use-local-space-for-constraint"></a>Verwenden von lokalem Speicherplatz für Einschränkungen

Schränkt relative lokale Transformationsachsen des bearbeiteten Objekts ein, wenn true. Der Standardwert ist gleich „False“.

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

Diese Einschränkung kann verwendet werden, um zu korrigieren, um welche Achsen ein bearbeitetes Objekt gedreht werden kann. Dies kann nützlich sein, um ein bearbeitetes Objekt aufrecht zu halten, aber dennoch y-Achsenrotation zu ermöglichen, z. B. . Die Eigenschaften `RotationAxisConstraint` für lauten wie folgt:

#### <a name="constraint-on-rotation"></a>Einschränkung bei Drehung

Gibt an, um welche Achsen eine Drehung verhindert werden soll. Standardmäßig sind diese Achsen global und nicht lokal, aber dies kann unten geändert werden. Da diese Eigenschaft ein Flag ist, kann eine beliebige Anzahl von Optionen ausgewählt werden.

- *Y-Achse:* Die Drehung um die y-Achse ist bei Auswahl von eingeschränkt.
- *Z-Achse:* Die Drehung um die Z-Achse ist eingeschränkt, wenn ausgewählt.
- *X-Achse:* Die Drehung um die x-Achse ist eingeschränkt, wenn ausgewählt.

#### <a name="use-local-space-for-constraint"></a>Verwenden des lokalen Speicherplatzes für Einschränkungen

Schränkt relativ die lokalen Transformationsachsen des bearbeiteten Objekts ein, wenn true ist. Der Standardwert ist gleich „False“.

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

Diese Einschränkung ermöglicht das Festlegen von Mindest- und Höchstwerten für die Skalierung des bearbeiteten Objekts. Dies ist nützlich, um zu verhindern, dass Benutzer ein Objekt zu klein oder zu groß skalieren. Die Eigenschaften für `MinMaxScaleConstraint` sind wie folgt:

#### <a name="scale-minimum"></a>Mindestskaliert

Der minimale Skalierungswert während der Bearbeitung.

#### <a name="scale-maximum"></a>Maximale Skalierung

Der maximale Skalierungswert während der Bearbeitung.

#### <a name="relative-to-initial-state"></a>Relativ zum Anfangszustand

True gibt an, dass die oben genannten Werte relativ zur anfänglichen Skalierung der Objekte interpretiert werden. Andernfalls werden sie als absolute Skalierungswerte interpretiert.
