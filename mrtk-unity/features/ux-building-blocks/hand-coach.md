---
title: Hand Coach
description: Beschreibung und Beispiele für Handcoach.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 3e5a56f7498288e79963acea6fca223421fee2607004a9a2bae639f81441e0d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209024"
---
# <a name="hand-coach"></a>Hand Coach

![Menü "Hand Trainer"](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

Handcod ist eine 3D-modellierte Hand, die ausgelöst wird, wenn das System die Hände des Benutzers nicht erkennt. Dies wird als "Teaching"-Komponente implementiert, die dem Benutzer hilft, wenn die Geste nicht trainiert wurde. Wenn Benutzer die angegebene Geste für einen bestimmten Zeitraum nicht ausgeführt haben, werden die Hände mit einer Verzögerung in eine Schleife schleifen. Handwagen können verwendet werden, um das Drücken einer Schaltfläche oder das Aufnehmen eines Hologramms darzustellen.

Das aktuelle Interaktionsmodell stellt eine Vielzahl von Gestensteuerelementen dar, z. B. Scrollen, Fernauswahl und Tippen in der Nähe. Im Folgenden finden Sie eine vollständige Liste der vorhandenen Hand-Trainer-Beispiele:

- Tippen in der Nähe: Wird für Schaltflächen oder das Schließen interaktivierbarer Objekte verwendet.
- Fernauswahl: Wird für Objekte verwendet, die weit entfernt sind
- Verschieben: Wird verwendet, um ein Hologramm im Raum zu verschieben.
- Rotieren: Wird verwendet, um zu zeigen, wie Hologramme oder Objekte gedreht werden.
- Skalierung: Wird verwendet, um zu zeigen, wie Hologramme so bearbeitet werden, dass sie größer oder kleiner sind.
- Handkippen: Wird zum Aufrufen eines Startbereichs der Benutzeroberfläche oder von Handmenüs verwendet.
- Handfläche hoch: Wird für die Vor-Und-Uhr-Nutzung verwendet. Ein weiterer Vorschlag könnte sein, einen Startbereich für die Benutzeroberfläche zu starten.
- Scrollen: Wird zum Scrollen einer Liste oder eines langen Dokuments verwendet.

## <a name="example-scene"></a>Beispielszene

Beispiele finden Sie in der **HandCoachExample-Szene** [unter: MixedRealityToolkit.Examples/Experimental/HandCoach/Scenes](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>Hand-3D-Objekte

Sie finden die Ressourcen [unter: MixedRealityToolkit.SDK/Experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>Qualität

Wenn Sie Verzerrungen im skinned Mesh bemerken, müssen Sie sicherstellen, dass Ihr Projekt die richtige Menge an Fugen verwendet.
Wechseln Sie zu Edit > Project Einstellungen > Quality > Other > Blend Weights von Unity. Stellen Sie sicher, dass "4 Gänge" ausgewählt sind, um Smooth Joints anzuzeigen.
![Project Einstellung](../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>Skripts

### <a name="interaction-hint"></a>Interaktionshinweis

Das `InteractionHint.cs` Skript stellt Wrapperfunktionen zum Auslösen von Animationen bereit und verblasst für die Handplattform.

#### <a name="how-to-set-up-an-interaction-hint"></a>Einrichten eines Interaktionshinweises

Zum Einrichten eines Interaktionshinweises wird empfohlen, die bereitgestellten Prefabs "StaticHandCoachRoot_L.prefab" und "StaticHandCoachRoot_R.prefab" zu verwenden. Dieses Prefab enthält das InteractionHint-Skript und das Hand-Rig sowie die richtige Hierarchie, um sicherzustellen, dass die bereitgestellten Hinweisanimationen wie vorgesehen funktionieren.
Andernfalls müssen Sie das Skript auf einem gameObject-Element auf einer übergeordneten Ebene von Ihrer Handplattform mit Animator nach oben platzieren.

#### <a name="inspector-properties"></a>Inspektoreigenschaften

- **HideIfHandTracked** Dieser boolesche Wert gibt an, ob der Nachverfolgungszustand der Hand verwendet werden soll, um visuelle Elemente auszublenden, wenn die Hände eines Benutzers nachverfolgt werden. Wenn diese Einstellung auf FALSE festgelegt ist, wird nur die Skripteigenschaft "customShouldHideVisuals" verwendet, um zu bestimmen, ob der Hinweis ausgeblendet werden soll.

- **MinDelay** Diese Eigenschaft gibt die minimale Verzögerung für die Anzeige der Visuals an. Standardmäßig werden die Visuals für die Hand nach diesen vielen Sekunden angezeigt, wenn die Hände des Benutzers nicht nachverfolgt werden.

- **MaxDelay** Diese Eigenschaft gibt die maximale Verzögerung für die Anzeige der Visuals an. Standardmäßig werden die Visuals für die Hand nach diesen vielen Sekunden angezeigt, auch wenn die Hände des Benutzers nachverfolgt werden.

- **UseMaxTimer** Wenn dieser boolesche Wert auf FALSE festgelegt ist, deaktiviert er den maximalen Timer und lässt nur zu, dass der Handhinweis angezeigt wird, wenn die Hände des Benutzers nicht angezeigt werden oder die benutzerdefinierte Bedingung FALSE zurückgibt.

- **Wiederholungen** Diese Eigenschaft steuert, wie oft die Hinweisanimation wiedergegeben wird, wenn der min- oder max-Timer überschritten wurde. Der Hinweis wird dann ausgeblendet und wartet erneut auf die Verzögerung.

- **AutoActivate** Wenn dieser boolesche Wert auf TRUE festgelegt ist, wird der Hinweis automatisch durch die Zeitgeberlogik ausgeführt, wenn das GameObject des Skripts in der Hierarchie aktiv ist und das Skript aktiviert ist. Dies sollte nur auf FALSE festgelegt werden, wenn Sie beabsichtigen, die Darstellung des Hinweises manuell zu steuern und über Code zu verfälschen.

- **AnimationState** Der Name des Animationszustands, der wiedergegeben werden soll, wenn der Hinweis aktiv ist. Dies muss festgelegt werden, bevor die StartHintLoop()-Funktion aufgerufen wird (während OnEnable, wenn AutoActivate aktiviert ist).

#### <a name="controlling-interactionhint-via-script"></a>Steuern der InteraktionHint per Skript

- **StartHintLoop** Diese Funktion startet die Ein-/Ausblenden-Schleife, die andernfalls OnEnable startet, wenn das AutoActivate-Flag auf TRUE festgelegt ist.
- **StopHintLoop** Diese Funktion ruft den Ausblendungsanimationszustand auf, wenn er derzeit nicht wiedergegeben wird. Anschließend deaktiviert sie die Show/Hide-Schleife und legt die Handplattform inaktiv in der Hierarchie fest.
- **AnimationState** Diese Zeichenfolge bestimmt, welcher Animationszustand während der Schleife wiedergegeben wird. Sie können diese Zeichenfolge ändern, um zu ändern, welcher Zustand wiedergegeben wird. Sie müssen dies jedoch nach dem Aufruf von StopHintLoop tun, und Sie müssen StartHintLoop erneut aufrufen, nachdem Sie den Zustand geändert haben.
- **CustomShouldHideVisuals** Sie können dies mit Ihrer eigenen Funktion festlegen, die true zurückgeben sollte, wenn Sie die Handvisuals ausblenden möchten (beachten Sie minMaxTimer, insbesondere den Max-Parameter).

#### <a name="custom-animation-considerations"></a>Überlegungen zu benutzerdefinierten Animationen

Einblendungen sind standardmäßig auf 0,5 Sekunden festgelegt, sodass alle benutzerdefinierten Animationen, die für die Verwendung mit dem Rig erstellt wurden, mindestens 1,5 Sekunden betragen sollten, damit aussagekräftige Informationen übermittelt werden.

Die bereitgestellten Standardzustände werden ein- und ausgeblendet, Fade_In und Fade_Out können durch Ändern des Zeitstempels des zweiten Keyframes angepasst werden, um die Ausblendlänge festzulegen.

Der Animator und das Skript wurden so eingerichtet, dass die Einrichtung so einfach wie möglich ist. Um neue Animationszustände hinzuzufügen, importieren Sie einfach Ihre FBX-Datei, stellen Sie sicher, dass der Animationsname mit einem eindeutigen Namen festgelegt ist, und ziehen Sie diese Animation in den Animator.

### <a name="movetotarget"></a>MoveToTarget

Das Skript MoveToTarget.cs bietet Funktionen zum Verschieben des Handhinweises von einer Nachverfolgungsposition an eine Zielposition im Zeitverlauf.

#### <a name="how-to-set-up-movetotarget"></a>Einrichten von MoveToTarget

Die bereitgestellten Prefabs "MovingHandCoachRoot_L.prefab" und "MovingHandCoachRoot_R.prefab" enthalten ein MoveToTarget in ihren Hierarchien. Wenn Sie dieses Skript in Ihrem eigenen Setup verwenden möchten, müssen Sie es auf dem Stammspielobjekt platzieren, das den Animator für Ihre Anlage enthält.

#### <a name="inspector-properties"></a>Inspektoreigenschaften

- **TrackingObject** Legen Sie dies mit dem Objekt fest, dem die Plattform folgen soll, bevor die Bewegung gestartet wird. Es wird empfohlen, ein leeres GameObject zu erstellen und es an eine bestimmte Position zu verschieben, damit Sie die Nachverfolgung ermitteln können.
- **TargetObject** Legen Sie dies mit dem Objekt fest, zu dem das Objekt während seiner Bewegung verschoben werden soll. Es wird empfohlen, ein leeres GameObject zu erstellen und es an eine bestimmte Position zu verschieben, damit Sie die Nachverfolgung ermitteln können.
- **RootObject** Legen Sie dies auf ein gemeinsames übergeordnetes Element zwischen Nachverfolgungs- und Zielobjekt fest, damit die relativen Positionen richtig berechnet werden können. Das enthaltene Prefab verfügt sowohl über Nachverfolgungs- als auch über Zielobjekte in seiner Hierarchie. Sie können das Zielobjekt jedoch als gameObject außerhalb des Prefabs festlegen und das Stammobjekt in ein freigegebenes übergeordnetes Element ändern.
- **Dauer** Die Zeitspanne(in Sekunden), die es in Sekunden dauern sollte, von TrackingObject zu TargetObject zu wechseln.
- **TargetOffset** Ein abstimmbarer Offset, um das GameObject an die richtige Zielposition zu bringen. Dies ist nützlich, wenn Ihre Animation während der Animation einen Positionsoffset enthält.
- **AnimationCurve** Dies ist standardmäßig eine lineare Kurve, aber Sie können die Kurve ändern, um eine Beschleunigung beim Starten und Beenden des Bewegungspfads bereitzustellen.

#### <a name="controlling-movetotarget-via-script"></a>Steuern von MoveToTarget per Skript

Rufen Sie in Ihrem benutzerdefinierten Skript Follow() auf, während die Handplattform dem TrackingObject folgt, und rufen Sie dann MoveToTargetPosition() auf, wenn die Handplattform mit der Bewegung zum TargetObject beginnen soll.

#### <a name="controlling-movetotarget-via-animations"></a>Steuern von MoveToTarget über Animationen

Legen Sie in der Animation, die verschoben werden muss, zwei Ereignisse fest: eines mit einem Aufruf von Follow() und eines mit einem Aufruf von MoveToTargetPosition(). Für den ersten Keyframe sollte Follow festgelegt werden, da die Hand-Plattform ihrem TrackingObject folgt. MoveToTargetPosition sollte auf dem Keyframe festgelegt werden, in dem das Ziel gestartet werden soll. Auf diese Weise wird die Skriptfunktion in den bereitgestellten Prefabs verwendet.

### <a name="rotatearoundpoint"></a>RotateParundPoint

Das Skript RotateParundPoint.cs bietet Funktionen zum Drehen des Handhinweises um einen Pivotpunkt im Zeitverlauf.

#### <a name="how-to-set-up-rotatearoundpoint"></a>Einrichten von RotateHowundPoint

Die bereitgestellten Prefabs "RotatingHandCoachRoot_L.prefab" und "RotatingHandCoachRoot_R.prefab" enthalten einen RotateUnderundPoint in ihren Hierarchien. Wenn Sie dieses Skript in Ihrem eigenen Setup verwenden möchten, müssen Sie es auf dem Stammspielobjekt platzieren, das den Animator für Ihre Anlage enthält.

#### <a name="inspector-properties"></a>Inspektoreigenschaften

- **CenteredParent** Legen Sie dies mit dem übergeordneten Objekt fest, um das die Plattform pivotieren soll.
- **InverseParent** Legen Sie dies mit dem übergeordneten Element fest, um inverse Richtung zentriertParent zu drehen, um die Handausrichtung gleich zu halten. Im Allgemeinen ist dies das übergeordnete Objekt mit dem InteractionHint-Skript darauf.
- **PivotPosition** Legen Sie diese auf einen Punkt fest, an dem der Hinweis mit der Bewegung beginnen soll.
- **Dauer** Die Zeitspanne, die es (in Sekunden) dauern sollte, bis das CenteredParent-Objekt gedreht wird.
- **AnimationCurve** Dies ist standardmäßig eine lineare Kurve, aber Sie können die Kurve ändern, um eine Beschleunigung beim Starten und Beenden des Bewegungspfads bereitzustellen.
- **RotationVector** Wie viele Grad entlang jeder Achse gedreht werden sollen.

#### <a name="controlling-rotatearoundpoint-via-script"></a>Steuern von RotateParundPoint per Skript

Rufen Sie in Ihrem benutzerdefinierten Skript RotateToTarget() auf, wenn das Handgerät seine Drehung um centeredParent starten soll. Wenn die Position auf die ursprüngliche PivotPosition zurückgesetzt werden soll, rufen Sie ResetAndDeterminePivot() auf.

#### <a name="controlling-rotatearoundpoint-via-animations"></a>Steuern von RotateControlundPoint über Animationen

Legen Sie in der Zu verschiebenden Animation zwei Ereignisse fest: eines mit einem Aufruf von ResetAndDeterminePivot() und eines mit einem Aufruf von RotateToTarget(). ResetAndDeterminePivot sollte für den ersten Keyframe festgelegt werden, da dies dazu führt, dass das Handgerät auf die PivotPosition zurückgesetzt wird. RotateToTarget sollte für den Keyframe festgelegt werden, an dem die Drehung des Gittermodells um das CenteredParent-Objekt beginnen soll. So wird die Skriptfunktionalität in den bereitgestellten Prefabs verwendet.
