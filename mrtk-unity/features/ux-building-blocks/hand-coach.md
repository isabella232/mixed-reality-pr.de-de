---
title: README_HandCoach
description: Beschreibung und Beispiele für Handcoach.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 8b4069f25692c4058c912ccd06ae678d67882fcd
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489270"
---
# <a name="hand-coach"></a>Hand Coach

![Menü "Hand Trainer"](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

Handcod ist eine 3D-modellierte Hand, die ausgelöst wird, wenn das System die Hände des Benutzers nicht erkennt. Dies wird als "Teaching"-Komponente implementiert, die dem Benutzer hilft, wenn die Geste nicht trainiert wurde. Wenn Benutzer die angegebene Geste für einen bestimmten Zeitraum nicht ausgeführt haben, werden die Hände mit einer Verzögerung in eine Schleife schleifen. Handwagen können verwendet werden, um das Drücken einer Schaltfläche oder das Aufnehmen eines Hologramms darzustellen.

Das aktuelle Interaktionsmodell stellt eine Vielzahl von Gestensteuerelementen dar, z. B. Scrollen, Fernauswahl und Tippen in der Nähe. Im Folgenden finden Sie eine vollständige Liste der vorhandenen Hand-Trainer-Beispiele:

- Tippen in der Nähe: Wird für Schaltflächen oder das Schließen interaktivierbarer Objekte verwendet.
- Fernauswahl: Wird für Objekte verwendet, die weit entfernt sind
- Verschieben: Wird verwendet, um ein Hologramm im Raum zu verschieben.
- Drehen: Wird verwendet, um zu zeigen, wie Hologramme oder Objekte gedreht werden.
- Skalierung: Wird verwendet, um zu zeigen, wie Hologramme so bearbeitet werden, dass sie größer oder kleiner sind.
- Handkippen: Wird zum Aufrufen eines Startbereichs der Benutzeroberfläche oder von Handmenüs verwendet.
- Handfläche hoch: Wird für die Vor-Und-Uhr-Nutzung verwendet. Ein weiterer Vorschlag könnte sein, einen Startbereich für die Benutzeroberfläche zu starten.
- Scrollen: Wird zum Scrollen einer Liste oder eines langen Dokuments verwendet.

## <a name="example-scene"></a>Beispielszene

Beispiele finden Sie in der **HandCoachExample-Szene** [unter: MixedRealityToolkit.Examples/Experimental/HandCoach/Scenes](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>Hand 3D-Objekte

Sie finden die Objekte unter: [MixedRealityToolkit.SDK/Experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>Qualität

Wenn Sie Verzerrungen im skinnierten Netz bemerken, müssen Sie sicherstellen, dass Ihr Projekt die richtige Menge an Fugen verwendet.
Wechseln Sie zur Unity-Seite Edit > Project Settings > Quality > Other > Blend Weights (Bearbeiten > Projekteinstellungen für > Von Anderen > Blend-Gewichtungen). Stellen Sie sicher, dass "4 4 1000" ausgewählt sind, um Smooth Joints (Smooth Joints) zu sehen.
![Projekteinstellung](../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>Skripts

### <a name="interaction-hint"></a>Interaktionshinweis

Das `InteractionHint.cs` Skript stellt Wrapperfunktionen zum Auslösen von Animationen und Ausblendungen für das Handgerät zur Verfügung.

#### <a name="how-to-set-up-an-interaction-hint"></a>Einrichten eines Interaktionshinweises

Zum Einrichten eines Interaktionshinweises wird empfohlen, die bereitgestellten Prefabs "StaticHandCoachRoot_L.prefab" und "StaticHandCoachRoot_R.prefab" zu verwenden. Dieses Prefab enthält das InteractionHint-Skript und das Handgerät sowie die richtige Hierarchie, um sicherzustellen, dass die bereitgestellten Hinweisanimationen wie vorgesehen funktionieren.
Andernfalls müssen Sie das Skript auf einem gameObject auf einer übergeordneten Ebene von Ihrem Handgerät mit Animator platzieren.

#### <a name="inspector-properties"></a>Inspektoreigenschaften

- **HideIfHandTracked** Dieser boolesche Wert gibt an, ob der Nachverfolgungszustand der Hand verwendet werden soll, um visuelle Elemente auszublenden, wenn die Hände eines Benutzers nachverfolgt werden. Wenn dies auf FALSE festgelegt ist, wird nur die Skripteigenschaft "customShouldHideVisuals" verwendet, um zu bestimmen, ob der Hinweis auszublenden ist.

- **MinDelay** Diese Eigenschaft gibt die minimale Verzögerung für die Anzeige der Visuals an. Standardmäßig werden die Visuals für die Hand nach diesen vielen Sekunden angezeigt, wenn die Hände des Benutzers nicht nachverfolgt werden.

- **MaxDelay** Diese Eigenschaft gibt die maximale Verzögerung für die Anzeige der Visuals an. Standardmäßig werden die Visuellen für die Hand nach diesen vielen Sekunden angezeigt, auch wenn die Hände des Benutzers nachverfolgt werden.

- **UseMaxTimer** Wenn dieser boolesche Wert auf FALSE festgelegt ist, deaktiviert er den maximalen Timer und lässt nur zu, dass der Handhinweis angezeigt wird, wenn die Hände des Benutzers nicht mehr angezeigt werden oder die benutzerdefinierte Bedingung FALSE zurückgibt.

- **Wiederholungen** Diese Eigenschaft steuert, wie oft die Hinweisanimation wiedergegeben wird, wenn der min- oder max-Timer überschritten wurde. Der Hinweis blendet dann erneut die Verzögerung aus und wartet darauf.

- **AutoActivate** Wenn dieser boolesche Wert auf TRUE festgelegt ist, wird der Hinweis automatisch durch die Zeitgeberlogik ausgeführt, wenn das GameObject des Skripts in der Hierarchie aktiv ist und das Skript aktiviert ist. Dies sollte nur auf FALSE festgelegt werden, wenn Sie beabsichtigen, die Darstellung des Hinweises manuell zu steuern und über Code zu verfälschen.

- **AnimationState** Der Name des Animationszustands, der wiedergegeben werden soll, wenn der Hinweis aktiv ist. Dies muss festgelegt werden, bevor die StartHintLoop()-Funktion aufgerufen wird (während OnEnable, wenn AutoActivate aktiviert ist).

#### <a name="controlling-interactionhint-via-script"></a>Steuern der InteraktionHint per Skript

- **StartHintLoop** Diese Funktion startet die Ein-/Ausblenden-Schleife, die andernfalls OnEnable startet, wenn das AutoActivate-Flag auf TRUE festgelegt ist.
- **StopHintLoop** Diese Funktion ruft den Ausblendungsanimationszustand auf, wenn er derzeit nicht wiedergegeben wird. Anschließend deaktiviert sie die Show/Hide-Schleife und legt die Handplattform inaktiv in der Hierarchie fest.
- **AnimationState** Diese Zeichenfolge bestimmt, welcher Animationszustand während der Schleife wiedergegeben wird. Sie können diese Zeichenfolge ändern, um zu ändern, welcher Zustand wiedergegeben wird. Sie müssen dies jedoch nach dem Aufruf von StopHintLoop tun, und Sie müssen StartHintLoop erneut aufrufen, nachdem Sie den Zustand geändert haben.
- **CustomShouldHideVisuals** Sie können dies mit Ihrer eigenen Funktion festlegen, die true zurückgeben sollte, wenn Sie die hand-Visuals ausblenden möchten (beachten Sie minMaxTimer, insbesondere den Max-Parameter).

#### <a name="custom-animation-considerations"></a>Überlegungen zu benutzerdefinierten Animationen

Einblendungen sind standardmäßig auf 0,5 Sekunden festgelegt, sodass alle benutzerdefinierten Animationen, die für die Verwendung mit dem Rig erstellt wurden, mindestens 1,5 Sekunden betragen sollten, damit aussagekräftige Informationen übermittelt werden.

Die bereitgestellten Standardzustände werden ein- und ausgeblendet, Fade_In und Fade_Out können durch Ändern des Zeitstempels des zweiten Keyframes angepasst werden, um die Ausblendlänge festzulegen.

Der Animator und das Skript wurden so eingerichtet, dass die Einrichtung so einfach wie möglich ist. Um neue Animationszustände hinzuzufügen, importieren Sie einfach Ihre FBX-Datei, stellen Sie sicher, dass der Animationsname mit einem eindeutigen Namen festgelegt ist, und ziehen Sie diese Animation in den Animator.

### <a name="movetotarget"></a>MoveToTarget

Das Skript MoveToTarget.cs bietet Funktionen zum Verschieben des Handhinweises von einer Nachverfolgungsposition in eine Zielposition im Laufe der Zeit.

#### <a name="how-to-set-up-movetotarget"></a>Einrichten von MoveToTarget

Die bereitgestellten Prefabs "MovingHandCoachRoot_L.prefab" und "MovingHandCoachRoot_R.prefab" enthalten ein MoveToTarget-Attribut in ihren Hierarchien. Wenn Sie dieses Skript für Ihr eigenes Setup verwenden möchten, müssen Sie es auf dem Stammspielobjekt platzieren, das den Animator für Ihr Gerät enthält.

#### <a name="inspector-properties"></a>Inspektoreigenschaften

- **TrackingObject** Legen Sie dies mit dem Objekt fest, dem das Gerät folgen soll, bevor es seine Bewegung startet. Es wird empfohlen, ein leeres GameObject zu erstellen und an eine bestimmte Position zu verschieben, damit Sie die Nachverfolgung aufspüren können.
- **TargetObject** Legen Sie dies mit dem Objekt fest, zu dem das Gerät während seiner Bewegung bewegt werden soll. Es wird empfohlen, ein leeres GameObject zu erstellen und an eine bestimmte Position zu verschieben, damit Sie die Nachverfolgung aufspüren können.
- **RootObject** Legen Sie dies auf ein freigegebenes übergeordnetes Element zwischen nachverfolgungs- und zielobjekt fest, damit die relativen Positionen richtig berechnet werden können. Das enthaltene Prefab enthält sowohl Nachverfolgungs- als auch Zielobjekte in seiner Hierarchie, aber Sie können das Zielobjekt als gameObject außerhalb des Prefabs festlegen und das Stammobjekt in ein freigegebenes übergeordnetes Element ändern.
- **Dauer** Die Zeit (in Sekunden), die das Verschieben von TrackingObject zu TargetObject in Sekunden dauern soll.
- **TargetOffset** Ein abstimmbarer Offset, damit das GameObject an der richtigen Zielposition eintrifft. Dies ist nützlich, wenn die Animation während der Animation einen Positionsoffset enthält.
- **AnimationCurve** Dies ist standardmäßig eine lineare Kurve, aber Sie können die Kurve ändern, um beim Starten und Beenden des Bewegungspfads eine Beschleunigung zu ermöglichen.

#### <a name="controlling-movetotarget-via-script"></a>Steuern von MoveToTarget per Skript

Rufen Sie in Ihrem benutzerdefinierten Skript Follow() auf, während die Handplattform dem TrackingObject folgt, und rufen Sie dann MoveToTargetPosition() auf, wenn die Handplattform mit der Bewegung zum TargetObject beginnen soll.

#### <a name="controlling-movetotarget-via-animations"></a>Steuern von MoveToTarget über Animationen

Legen Sie in der Animation, die verschoben werden muss, zwei Ereignisse fest: eines mit einem Aufruf von Follow() und eines mit einem Aufruf von MoveToTargetPosition(). Für den ersten Keyframe sollte Follow festgelegt werden, da die Handplattform ihrem TrackingObject folgt. MoveToTargetPosition sollte auf dem Keyframe festgelegt werden, in dem das Ziel gestartet werden soll. Auf diese Weise wird die Skriptfunktion in den bereitgestellten Prefabs verwendet.

### <a name="rotatearoundpoint"></a>RotateParundPoint

Das Skript RotateParundPoint.cs bietet Funktionen zum Drehen des Handhinweises um einen Pivotpunkt im Zeitverlauf.

#### <a name="how-to-set-up-rotatearoundpoint"></a>Einrichten von RotateHowundPoint

Die bereitgestellten Prefabs "RotatingHandCoachRoot_L.prefab" und "RotatingHandCoachRoot_R.prefab" enthalten einen RotateUnderundPoint in ihren Hierarchien. Wenn Sie dieses Skript in Ihrem eigenen Setup verwenden möchten, müssen Sie es auf dem Stammspielobjekt platzieren, das den Animator für Ihre Anlage enthält.

#### <a name="inspector-properties"></a>Inspektoreigenschaften

- **CenteredParent** Legen Sie dies mit dem übergeordneten Objekt fest, um das die Plattform pivotieren soll.
- **InverseParent** Legen Sie dies mit dem übergeordneten Element fest, um inverse Richtung zentriertParent zu drehen, um die Handausrichtung gleich zu halten. Im Allgemeinen ist dies das übergeordnete Objekt mit dem InteractionHint-Skript darauf.
- **PivotPosition** Legen Sie diesen auf einen Punkt fest, an dem der Hinweis mit der Bewegung beginnen soll.
- **Dauer** Die Zeitspanne, die es (in Sekunden) dauern sollte, bis das CenteredParent-Objekt gedreht wird.
- **AnimationCurve** Dies ist standardmäßig eine lineare Kurve, aber Sie können die Kurve ändern, um eine Beschleunigung beim Starten und Beenden des Bewegungspfads bereitzustellen.
- **RotationVector** Wie viele Grad entlang jeder Achse gedreht werden sollen.

#### <a name="controlling-rotatearoundpoint-via-script"></a>Steuern von RotateParundPoint per Skript

Rufen Sie in Ihrem benutzerdefinierten Skript RotateToTarget() auf, wenn die Drehung des Handgeräts um das CenteredParent-Objekt beginnen soll. Wenn Sie möchten, dass die Position auf die ursprüngliche PivotPosition zurückgesetzt wird, rufen Sie ResetAndDeterminePivot() auf.

#### <a name="controlling-rotatearoundpoint-via-animations"></a>Steuern von RotateControlundPoint über Animationen

Legen Sie in der Zu verschiebenden Animation zwei Ereignisse fest: eines mit einem Aufruf von ResetAndDeterminePivot() und eines mit einem Aufruf von RotateToTarget(). ResetAndDeterminePivot sollte für den ersten Keyframe festgelegt werden, da dies dazu führt, dass das Handgerät auf die PivotPosition zurückgesetzt wird. RotateToTarget sollte auf dem Keyframe festgelegt werden, an dem die Drehung des Gittergeräts um den CenteredParent beginnen soll. So wird die Skriptfunktionalität in den bereitgestellten Prefabs verwendet.
