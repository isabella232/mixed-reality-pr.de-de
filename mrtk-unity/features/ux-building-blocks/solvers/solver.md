---
title: Solver-Übersicht
description: Übersicht über Solver in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, PR, Solver,
ms.openlocfilehash: bf9bbfe578ace576fca8870f038f145037a6838d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176452"
---
# <a name="solver-overview"></a>Solver-Übersicht

![Solver Main](../../images/solver/MRTK_Solver_Main.png)

Solver sind Komponenten, die die Berechnung der Position und Ausrichtung eines Objekts gemäß einem vordefinierten Algorithmus erleichtern. Ein Beispiel hierfür ist das Platzieren eines Objekts auf der Oberfläche, auf die der Raycast des Anvisierens durch den Benutzer aktuell trifft.

Darüber hinaus definiert das Solver-System deterministisch eine Reihenfolge von Vorgängen für diese Transformationsberechnungen, da es keine zuverlässige Möglichkeit gibt, Unity die Aktualisierungsreihenfolge für Komponenten anzugeben.

Solver bieten eine Reihe von Verhaltensweisen zum Anfügen von Objekten an andere Objekte oder Systeme. Ein weiteres Beispiel wäre ein mitwanderndes Objekt, das vor dem Benutzer schwebt (basierend auf der Kamera). Ein Solver könnte auch an einen Controller und ein Objekt angefügt werden, damit das Objekt dem Controller folgt. Alle Solver können sicher gestapelt werden, z. B. ein Folgeverhalten + Oberflächenmagnetismus + Momentum.

## <a name="how-to-use-a-solver"></a>Verwenden eines Solvers

Das Solver-System besteht aus drei Kategorien von Skripts:

* [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver): Die abstrakte Basisklasse, von der alle Solver abgeleitet werden. Sie bietet Zustandsverfolgung, Glättungsparameter und Implementierung, automatische Solver-Systemintegration und Aktualisierungsreihenfolge.
* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler): Legt das zu verfolgende Bezugsobjekt fest (z. B. die Hauptkameratransformation, Handstrahl usw.), verarbeitet das Sammeln von Solver-Komponenten und führt deren Aktualisierung in der richtigen Reihenfolge aus.

Die dritte Kategorie ist der Solver selbst. Die folgenden Solver stellen die Bausteine für das grundlegende Verhalten bereit:

* [`Orbital`](#orbital): Wird an einer angegebenen Position und mit einem Offset vom Bezugszobjekt verankert.
* [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize): Wird so skaliert, dass eine konstante Größe relativ zur Ansicht des Bezugsobjekts beibehalten wird.
* [`RadialView`](#radialview): Hält das Objekt innerhalb eines Sichtkegels, der vom Bezugsobjekt geworfen wird.
* [`Follow`](#follow): Hält das Objekt innerhalb einer Gruppe benutzerseitig definierter Grenzen vom Bezugsobjekt.
* [`InBetween`](#inbetween): Hält ein Objekt zwischen zwei verfolgten Objekten.
* [`SurfaceMagnetism`](#surfacemagnetism): Wirft Strahlen auf Oberflächen in der Welt und richtet das Objekt an dieser Oberfläche aus.
* [`DirectionalIndicator`](#directionalindicator): Bestimmt die Position und Ausrichtung eines Objekts als Richtungsindikator. Ab dem Bezugspunkt des vom SolverHandler verfolgten Ziels richtet sich dieser Indikator auf das angegebene DirectionalTarget aus.
* [`Momentum`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Momentum): Wendet Beschleunigung/Geschwindigkeit/Reibung an, um Momentum und Elastizität für ein Objekt zu simulieren, das von anderen Solvern/Komponenten bewegt wird.
* [`HandConstraint`](#hand-menu-with-handconstraint-and-handconstraintpalmup): Schränkt das Objekt auf die Verfolgung von Händen in einem Bereich ein, in dem sich das GameObject nicht mit den Händen überschneidet. Nützlich für auf Hände eingeschränkte interaktive Inhalte wie Menüs usw. Dieser Solver ist für die Verwendung mit [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) vorgesehen, funktioniert aber auch mit [IMixedRealityController](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController).
* [`HandConstraintPalmUp`](#hand-menu-with-handconstraint-and-handconstraintpalmup): Wird von HandConstraint abgeleitet, umfasst aber Logik zum Testen vor der Aktivierung, ob die Handfläche dem Benutzer zugewandt ist. Dieser Solver funktioniert nur mit [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand)-Controllern. Mit anderen Controllertypen verhält sich dieser Solver genau wie seine Basisklasse.

Um das Solver-System zu verwenden, fügen Sie einem GameObject einfach eine der oben aufgeführten Komponenten hinzu. Da alle Solver einen [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) erfordern, wird einer automatisch von Unity erstellt.

> [!NOTE]
> Beispiele für die Verwendung des Solver-Systems finden Sie in der Datei **SolverExamples.scene**.

## <a name="how-to-change-tracking-reference"></a>Ändern des Verfolgungsbezugs

Die Eigenschaft *Tracked Target Type* (Typ des verfolgten Ziels) der [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)-Komponente definiert den Bezugspunkt, den alle Solver verwenden, um ihre Algorithmen zu berechnen. Beispielsweise führt ein Werttyp von [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) mit einer einfachen [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism)-Komponente zu einem Raycast vom Kopf des Benutzers aus und in dessen Anvisierrichtung, um aufzulösen, welche Oberfläche getroffen wird. Potenzielle Werte für die `TrackedTargetType`-Eigenschaft sind:

* *Head* (Kopf): Bezugspunkt ist die Transformation der Hauptkamera.
* *ControllerRay* (Controllerstrahl): Bezugspunkt ist die [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)-Transformation auf einem Controller (d. h. der Zeigerursprung auf einem Motion-Controller oder Handcontroller), der in Richtung des Linienstrahls zeigt.
  * Verwenden Sie die `TrackedHandedness`-Eigenschaft, um die bevorzugte Händigkeit auszuwählen (d. h. links, rechts, beides).
* *HandJoint* (Handgelenk): Bezugspunkt ist die Transformation eines spezifischen Handgelenks.
  * Verwenden Sie die `TrackedHandedness`-Eigenschaft, um die bevorzugte Händigkeit auszuwählen (d. h. links, rechts, beides).
  * Verwenden sie die `TrackedHandJoint`-Eigenschaft, um die zu verwendende Gelenktransformation zu bestimmen.
* *CustomOverride* (benutzerdefinierte Außerkraftsetzung): Bezugspunkt von der zugewiesenen `TransformOverride` aus.

> [!NOTE]
> Für beide Typen, also *ControllerRay* und *HandJoint*, versucht der Solver-Handler zuerst, die linke Controller-/Handtransformation bereitzustellen, und dann die rechte, wenn die erste nicht verfügbar ist, oder wenn die `TrackedHandedness`-Eigenschaft etwas anderes angibt.

![Solver Tracked Object (vom Solver verfolgtes Objekt)](../../images/solver/TrackedObjectType-Example.gif) 
*Beispiel für verschiedene Eigenschaften, die dem jeweiligen TrackedTargetType zugewiesen sind.*

> [!IMPORTANT]
> Die meisten Solver verwenden den Vorwärtsvektor des verfolgten Transformationsziels, das vom `SolverHandler` bereitgestellt wird. Bei Verwendung des Typs *Handgelenk* für ein verfolgtes Ziel kann es sein, dass der Vorwärtsvektor des Hand(flächen)gelenks durch die Finger und nicht durch die Handfläche zeigt. Dies hängt von der Plattform ab, die die Handgelenksdaten liefert. Für die Eingabesimulation und Windows Mixed Reality ist es der *Nach-oben-Vektor*, der durch die Handfläche nach oben zeigt (d. h. grüner Vektor zeigt nach oben, blauer Vektor vorwärts).
>
> ![Vorwärtsvektor](../../images/solver/HandJoint_ForwardUpVectors.png)
>
> Um dies zu umgehen, aktualisieren Sie die Eigenschaft *Additional Rotation* (Zusätzliche Drehung) des `SolverHandler` auf **<90, 0, 0>** . Dadurch wird sichergestellt, dass der an Solver übergebene Vorwärtsvektor durch die Handfläche und nach außen, von der Hand weg verweist.
>
> ![Zusätzliche Drehung](../../images/solver/SolverHandler_AdditionalRotation.png)
>
> Alternativ können Sie den Typ *Controller Ray* (Controllerstrahl) für ein verfolgtes Ziel verwenden, um ein ähnliches Verhalten für das Zeigen mit den Händen zu erhalten.

## <a name="how-to-chain-solvers"></a>Verketten von Solvern

Es ist möglich, dem selben GameObject mehrere `Solver`-Komponenten hinzuzufügen und so deren Algorithmen zu verketten. Die `SolverHandler`-Komponenten aktualisieren alle Solver desselben GameObject. Standardmäßig ruft der `SolverHandler` beim Starten `GetComponents<Solver>()` auf, wodurch die Solver in der Reihenfolge zurückgegeben werden, in der sie im Inspektor vorkommen.

Darüber hinaus weist das Festlegen der Eigenschaft *Updated Linked Transform* (Aktualisierte verknüpfte Transformation) auf „true“ den `Solver` an, seine berechnete Position, Ausrichtung und Skalierung in einer Zwischenvariablen zu speichern, auf die alle Solver zugreifen können (d. h. `GoalPosition`). „false“ gibt an, dass der `Solver` die Transformation des GameObject direkt aktualisiert. Durch das Speichern der Transformationseigenschaften an einem Zwischenspeicherort können andere Solver ihre Berechnungen ab der Zwischenvariablen ausführen. Dies liegt daran, dass Unity nicht zulässt, dass Aktualisierungen von „gameObject.transform“ innerhalb desselben Frames gestapelt werden.

> [!NOTE]
> Entwickler können die Ausführungsreihenfolge von Solvern ändern, indem sie die `SolverHandler.Solvers`-Eigenschaft direkt festlegen.

## <a name="how-to-create-a-new-solver"></a>Erstellen eines neuen Solvers

Alle Solver müssen von der abstrakten Basisklasse [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver) erben. Die primären Anforderungen einer Solver-Erweiterung umfassen das Außerkraftsetzen der `SolverUpdate`-Methode. Bei dieser Methode sollten Entwickler die geerbten Eigenschaften `GoalPosition`, `GoalRotation` und `GoalScale` auf die gewünschten Werte aktualisieren. Darüber hinaus ist es im Allgemeinen nützlich, `SolverHandler.TransformTarget` als Bezugsframe zu nutzen, der vom Consumer gewünscht wird.

Der unten angegebene Code enthält ein Beispiel für eine neue Solver-Komponente namens `InFront`, die das angefügte Objekt 2 m vor dem `SolverHandler.TransformTarget` platziert. Wenn der `SolverHandler.TrackedTargetType` vom Consumer als [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) festgelegt wird, ist `SolverHandler.TransformTarget` die Kameratransformation, weshalb dieser Solver dann das angefügte GameObject in jedem Frame 2 m vor dem Anvisieren des Benutzers platziert.

```c#
/// <summary>
/// InFront solver positions an object 2m in front of the tracked transform target
/// </summary>
public class InFront : Solver
{
    ...

    public override void SolverUpdate()
    {
        if (SolverHandler != null && SolverHandler.TransformTarget != null)
        {
            var target = SolverHandler.TransformTarget;
            GoalPosition = target.position + target.forward * 2.0f;
        }
    }
}
```

## <a name="solver-implementation-guides"></a>Richtlinien für die Solver-Implementierung

### <a name="common-solver-properties"></a>Allgemeine Solver-Eigenschaften

Jede Solver-Komponente verfügt über einen Kernsatz identischer Eigenschaften, die das Kernverhalten des Solvers steuern.

Wenn *Smoothing* (Glättung) aktiviert ist, aktualisiert der Solver die Transformation des GameObject im Laufe der Zeit schrittweise auf die berechneten Werte. Die Geschwindigkeit dieser Änderung wird durch die Eigenschaft *LerpTime* der jeweiligen Transformationskomponente bestimmt. Ein höherer *MoveLerpTime*-Wert führt beispielsweise zu langsameren Inkrementen bei der Bewegung zwischen Frames.

Wenn *MaintainScale* aktiviert ist, verwendet der Solver die lokale Standardskalierung des GameObject.

![Solver-Kerneigenschaften](../../images/solver/GeneralSolverProperties.png)  
*Allgemeine Eigenschaften, die von allen Solver-Komponenten geerbt werden*

### <a name="orbital"></a>Orbital

Die [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital)-Klasse ist eine Komponente mit Folgeverhalten, die sich wie Planeten in einem Sonnensystem verhält. Dieser Solver stellt sicher, dass das angefügte GameObject die verfolgte Transformation umkreist. Wenn also der *Tracked Target Type* (Typ des verfolgten Ziels) des [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) auf [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) festgelegt ist, umkreist das GameObject den Kopf des Benutzers mit einem festen Offset.

Entwickler können diesen festen Offset ändern, um Menüs oder andere Szenenkomponenten auf Augen- oder Hüfthöhe usw. um einen Benutzer herum zu halten. Dies erfolgt durch Ändern der Eigenschaften *Local Offset* (Lokaler Offset) und *World Offset* (Weltoffset). Die Eigenschaft *Orientation Type* (Ausrichtungstyp) bestimmt auf das Objekt angewendete Drehung, ob es seine ursprüngliche Drehung beibehalten oder immer der Kamera oder dem Gesicht zugewandt sein soll, egal welche Transformation seine Position bestimmt usw.

![Orbital-Beispiel](../../images/solver/OrbitalExample.png)  
*Orbital-Beispiel*

### <a name="radialview"></a>RadialView

[`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) ist eine weitere Komponente mit Folgeverhalten, die einen bestimmten Teil eines GameObject im Frustum des Sichtfelds des Benutzers hält.

Die Eigenschaften *Min & Max View Degrees* (Mindest-/Maximalsichtgrad) bestimmen die Größe des Teils des GameObject, der immer im Sichtfeld sein muss.

Die Eigenschaften *Min & Max Distance* (Mindest-/Maximalabstand) bestimmen, wie weit das GameObject vom Benutzer entfernt bleiben soll. Wenn Sie beispielsweise mit einer *Min Distance* (Mindestabstand) von 1 m auf das GameObject zugehen, wird das GameObject weggestoßen, um sicherzustellen, dass es dem Benutzer nie näher als 1 m kommt.

Im Allgemeinen wird die [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) in Verbindung mit dem auf [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) festgelegten *Tracked Target Type* (Typ des verfolgten Ziels) verwendet, damit die Komponente dem Anvisieren des Benutzers folgt. Diese Komponente kann jedoch so funktionieren, dass sie immer im *"Sichtfeld"* jedes *Tracked Target Type* (Typ des verfolgten Ziels) gehalten wird.

![RadialView-Beispiel](../../images/solver/RadialViewExample.png)  
*RadialView-Beispiel*

### <a name="follow"></a>Follow

Die [`Follow`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Follow)-Klasse positioniert ein Element vor dem verfolgten Ziel, relativ zu seiner lokalen Vorwärtsachse. Das Element kann lose eingeschränkt werden (auch als Folgeverhalten („tag-along“) bezeichnet), sodass es erst dann folgt, wenn das verfolgte Ziel benutzerdefinierte Grenzen überschreitet.

Es funktioniert ähnlich wie der RadialView-Solver mit zusätzlichen Steuerelementen zum Verwalten von *Max Horizontal & Vertical View Degrees* (Max. horizontale/vertikaler Sichtgrad) und Mechanismen zum Ändern der *Ausrichtung* des Objekts.

![Follow-Eigenschaften](../../images/solver/FollowExample.png)  
*Follow-Eigenschaften*

![Follow-Beispielszene](../../images/solver/FollowExampleScene.gif)  
*Follow-Beispielszene (Assets/MRTK/Examples/Demos/Solvers/Scenes/FollowSolverExample.unity)*

### <a name="inbetween"></a>InBetween

Die [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween)-Klasse hält das angefügte GameObject zwischen zwei Transformationen. Diese zwei Transformationsendpunkte werden durch den eigenen *Tracked Target Type* (Typ des verfolgten Ziels) [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) des GameObject und die Eigenschaft *Second Tracked Target Type* (Zweiter Typ des verfolgten Ziels) der [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween)-Komponente definiert. Im Allgemeinen werden beide Typen auf [`CustomOverride`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.CustomOverride) und die resultierenden `SolverHandler.TransformOverride`- und `InBetween.SecondTransformOverride`-Werte auf die zwei verfolgten Endpunkte festgelegt.

Zur Laufzeit erstellt die [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween)-Komponente eine weitere [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)-Komponente, die auf den Eigenschaften *Second Tracked Target Type* (Zweiter Typ des verfolgten Ziels) und *Second Transform Override*(Zweite Transformationsaußerkraftsetzung) basiert.

Der `PartwayOffset` definiert, wo entlang der Linie zwischen zwei Transformationen das Objekt platziert werden soll, wobei 0,5 auf halber Strecke, 1,0 bei der ersten Transformation und 0,0 bei der zweiten Transformation ist.

![InBetween-Beispiel](../../images/solver/InBetweenExample.png)  
*Beispiel für die Verwendung des InBetween-Solvers, um ein Objekt zwischen zwei Transformationen zu halten*

### <a name="surfacemagnetism"></a>SurfaceMagnetism

[`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) funktioniert, indem ein Raycast auf eine festgelegte LayerMask von Oberflächen ausgeführt und das GameObject an diesem Kontaktpunkt platziert wird.

Der *Surface Normal Offset* (Offset zur Oberflächennormale) platziert das GameObject in einem festgelegten Abstand in Metern von der Oberfläche in Richtung der Normalen am Punkt des Auftreffens auf der Oberfläche.

Umgekehrt platziert der *Surface Ray Offset* (Offset zum Oberflächenstrahl) das GameObject in einem festgelegten Abstand in Metern von der Oberfläche weg, aber in entgegengesetzter Richtung des ausgeführten Raycasts. Wenn der Raycast also das Anvisieren des Benutzers ist, bewegt sich das GameObject näher entlang der Linie vom Punkt des Auftreffens auf der Oberfläche zur Kamera.

Der *Orientation Mode* (Ausrichtungsmodus) bestimmt den Typ der Drehung, die in Bezug auf die Normale auf der Oberfläche angewendet werden soll.

* *None* (Keine): Keine Drehung angewendet.
* *TrackedTarget* (Verfolgtes Ziel): Das Objekt wird der verfolgten Transformation, die den Raycast steuert, zugewandt.
* *SurfaceNormal* (Oberflächennormale): Das Objekt wird auf Grundlage der Normalen am Punkt des Auftreffens auf der Oberfläche ausgerichtet.
* *Blended* (Gemischt): Das Objekt wird basierend auf der Normalen am Punkt des Auftreffens auf der Oberfläche UND der verfolgten Transformation zugewandt ausgerichtet.

Um zu erzwingen, dass das zugeordnete GameObject in jedem anderen Modus als *None* vertikal bleibt, aktivieren Sie *Keep Orientation Vertical* (Ausrichtung vertikal halten).

> [!NOTE]
> Verwenden Sie die Eigenschaft *Orientation Blend* (Gemischte Ausrichtung), um das Gleichgewicht zwischen Drehfaktoren zu steuern, wenn der *Orientation Mode* (Ausrichtungsmodus) auf *Blended* (Gemischt) festgelegt ist. Beim Wert 0,0 wird die Ausrichtung vollständig vom *TrackedTarget*-Modus gesteuert, und beim Wert 1,0 wird die Ausrichtung vollständig von *SurfaceNormal* gesteuert.

![SurfaceMagnetism-Beispiel](../../images/solver/SurfaceMagExample.png)

#### <a name="determining-what-surfaces-can-be-hit"></a>Bestimmen, welche Oberflächen erreicht werden können

Beim Hinzufügen einer [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism)-Komponente zu einem GameObject ist es wichtig, die Ebene des GameObject und seine untergeordneten Elemente zu berücksichtigen, sofern diese Collider aufweisen. Die Komponente funktioniert so, dass sie verschiedene Arten von Raycasts ausführt, um zu bestimmen, an welcher Oberfläche sie sich selbst „magnetisch anheften“ soll. Wenn das Solver GameObject über einen Collider auf einer der Ebenen verfügt, die in der `MagneticSurfaces`-Eigenschaft von `SurfaceMagnetism` aufgeführt sind, trifft sich der Raycast wahrscheinlich selbst, was dazu führt, dass das GameObject an seinen eigenen Colliderpunkt angefügt wird. Dieses seltsame Verhalten kann vermieden werden, indem das Haupt-GameObject und alle seine untergeordneten Elemente auf die *Ignore Raycast*-Eben (Raycast ignorieren) festgelegt werden oder das `MagneticSurfaces` LayerMask-Array entsprechend geändert wird.

Umgekehrt wird ein [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) GameObject nicht mit Oberflächen auf einer Ebene kollidieren, die nicht in der `MagneticSurfaces`-Eigenschaft aufgeführt ist. Es wird generell empfohlen, alle gewünschten Oberflächen auf einer dedizierten Ebene zu platzieren (d. h. *Surfaces* (Oberflächen)) und die Eigenschaft `MagneticSurfaces` nur auf diese Ebene festzulegen.  Die Verwendung von *default* (Standard) oder *everything* (alles) kann dazu führen, dass Benutzeroberflächenkomponenten oder Cursor zum Solver beitragen.

Schließlich werden Oberflächen, die weiter als die Einstellung der Eigenschaft `MaxRaycastDistance` entfernt liegen, von den `SurfaceMagnetism`-Raycasts ignoriert.

### <a name="directionalindicator"></a>DirectionalIndicator

Die [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator)-Klasse ist eine Komponente mit Folgeverhalten, die sich selbst an der Richtung eines gewünschten Punkts im Raum orientiert.

Wird am häufigsten verwendet, wenn der *Tracked Target Type* (Typ des verfolgten Ziels) des [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) auf [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) festgelegt ist. Auf diese Weise weist eine UX-Komponente einen Benutzer mit dem [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator)-Solver an, auf den gewünschten Punkt im Raum zu sehen.

Der gewünschte Punkt im Raum wird über die Eigenschaft *Directional Target* (Gerichtetes Ziel) bestimmt.

Wenn das gerichtete Ziel für den Benutzer sichtbar ist, oder egal welcher Bezugsframe im [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) festgelegt ist, deaktiviert dieser Solver alle darunter liegenden [`Renderer`](https://docs.unity3d.com/ScriptReference/Renderer.html)-Komponenten. Wenn es nicht sichtbar ist, wird alles für den Indikator aktiviert.

Der Indikator wird immer kleiner, je näher der Benutzer dem Erfassen des *Directional Target* in seinem Sichtfeld (FOV) kommt.

* *Min Indicator Scale* (Minimale Indikatorskala): Die minimale Skalierung für das Indikatorobjekt.
* *Max Indicator Scale* (Maximale Indikatorskala): Die maximale Skalierung für das Indikatorobjekt.

* *Visibility Scale Factor* (Skalierungsfaktor für Sichtbarkeit): Multiplikator zum Erhöhen oder Verringern des Sichtfelds, der bestimmt, ob der Punkt des *Directional Target* sichtbar ist oder nicht.
* *View Offset* (Sichtoffset): Aus der Sicht des Bezugsframes (d. h. möglicherweise Kamera) definiert diese Eigenschaft, wie weit sich das Objekt in Indikatorrichtung von der Mitte des Viewports entfernt befinden soll.

![Directional Indicator-Eigenschaften (Richtungsindikator)](../../images/solver/DirectionalIndicatorExample.png)  
*Directional Indicator-Eigenschaften (Richtungsindikator)*

![Directional Indicator-Beispielszene (Richtungsindikator)](../../images/solver/DirectionalIndicatorExampleScene.gif)  
*Directional Indicator-Beispielszene (Richtungsindikator) (Assets/MRTK/Examples/Demos/Solvers/Scenes/DirectionalIndicatorSolverExample.unity)*

### <a name="hand-menu-with-handconstraint-and-handconstraintpalmup"></a>Handmenü mit HandConstraint und HandConstraintPalmUp

![UX-Beispiel für ein Handmenü](../../images/solver/MRTK_UX_HandMenu.png)

Das [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint)-Verhalten stellt einen Solver bereit, der das verfolgte Objekt auf einen Bereich beschränkt, der für auf Hand eingeschränkte Inhalte sicher ist (z. B. Handbenutzeroberfläche, Menüs usw.). Als sichere Regionen gelten Bereiche, die sich nicht mit der Hand überschneiden. Eine abgeleitete Klasse von [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) namens [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) ist ebenfalls enthalten, um ein allgemeines Verhalten der Aktivierung des vom Solver verfolgten Objekts zu veranschaulichen, wenn die Handfläche dem Benutzer zugewandt ist.

Die Beispiele für die Verwendung des Handeinschränkungs-Solvers zum Erstellen von Handmenüs [finden Sie auf der Seite „Handmenü“](../hand-menu.md).

## <a name="see-also"></a>Siehe auch

* [Hand-Tracking](../../input/hand-tracking.md)
* [Anvisieren](../../input/gaze.md)
