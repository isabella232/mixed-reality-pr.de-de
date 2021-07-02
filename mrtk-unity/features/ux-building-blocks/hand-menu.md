---
title: Handmenü
description: Beispielszene im Handmenü in MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, HandMenu,
ms.openlocfilehash: 9bb0276c048912b4f463dd93d3303c9a3af8fe29
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177525"
---
# <a name="hand-menu"></a>Handmenü

![Beispiel für die Benutzererfahrung im Handmenü](../images/solver/MRTK_UX_HandMenu.png)

MitHilfe von Handmenüs können Benutzer schnell eine handverfügte Benutzeroberfläche für häufig verwendete Funktionen aufrufen. Um eine falsche Aktivierung während der Interaktion mit anderen Objekten zu verhindern, bietet das Handmenü Optionen wie "Flache Hand erforderlich" und "Anviertaktivierung verwenden". Es wird empfohlen, diese Optionen zu verwenden, um unerwünschte Aktivierung zu verhindern.

## <a name="hand-menu-examples"></a>Beispiele für Handmenüs

**Die Szene "HandMenuExamples.unity"** befindet sich im ``MRTK/Examples/Demos/HandTracking/Scenes`` Ordner . Wenn sie ausgeführt wird, wird die Szene nur den aktuell ausgewählten Menütyp aktivieren.
<br/><img src="../images/hand-menu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="HandMenu_ExampleScene">

Sie finden diese Prefabs im Handmenü im ``MRTK/Examples/Demos/HandTracking/Prefabs`` Ordner .

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop und HandMenu_Medium_HideOnHandDrop

In diesen beiden Beispielen wird das MenuContent-Objekt einfach aktiviert und deaktiviert, um das Menü im **OnFirstHandDetected()-** und **OnLastHandLost()-Ereignis** anzuzeigen und auszublenden.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example1.png" width="600" alt="HandMenu_ExampleScene 1">
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example2.png" width="600" alt="HandMenu_ExampleScene 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

Für komplexere Menüs, die eine längere Interaktionszeit erfordern, wird empfohlen, das Menü weltweit zu sperren. In diesem Beispiel kann der Benutzer das Menü abrufen und zur Weltsperre ziehen, zusätzlich zum Aktivieren und Deaktivieren der MenuContent-Ereignisse on **OnFirstHandDetected()** und **OnLastHandLost().**
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example3.png" width="600" alt="HandMenu_ExampleScene 3">

Backplate es `ManipulationHandler` macht es greifend und verschiebbar. **Beim Manipulation Started-Ereignis** wird **SolverHandler.UpdateSolvers** deaktiviert, um das Menü weltweit zu sperren. Darüber hinaus wird die **Schaltfläche Schließen** angezeigt, damit der Benutzer das Menü schließen kann, wenn die Aufgabe abgeschlossen ist. **Beim Manipulation Ended-Ereignis** wird **HandConstraintPalmUp.StartWorldLockReattachCheckCoroutine** aufgerufen, damit der Benutzer das Menü wieder zur Hand nehmen kann, indem er die Handfläche anhebt und ansieht.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example4.png" width="600" alt="HandMenu_ExampleScene 4">

Die Schaltfläche **"Schließen"** reaktiviert **SolverHandler.UpdateSolvers** und blendet **menuContent** aus.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example5.png" alt="HandMenu_ExampleScene 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

Dieses Beispiel ähnelt HandMenu_Large_WorldLock_On_GrabAndPull. Der einzige Unterschied besteht darin, dass das Menü beim Handablage automatisch weltversperrt wird. Dies erfolgt, indem das Ereignis MenuContent on **OnLastHandLost()** einfach nicht ausgeblendet wird. Das Pullverhalten von "Greifen &" entspricht HandMenu_Large_WorldLock_On_GrabAndPull Beispiel.

## <a name="scripts"></a>Skripts

Das [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) Verhalten stellt einen Solver bereit, der das nachverfolgte Objekt auf einen Bereich beschränkt, der für eingeschränkten Handinhalt sicher ist (z. B. Die Benutzeroberfläche der Hand, Menüs usw.). Tresor Regionen gelten als Bereiche, die sich nicht mit der Hand überschneiden. Eine abgeleitete Klasse von [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) namens [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) ist ebenfalls enthalten, um ein allgemeines Verhalten der Aktivierung des nachverfolgten Solverobjekts zu veranschaulichen, wenn die Handfläche dem Benutzer gegenübersteht.

Weitere Dokumentation finden Sie in den QuickInfos, die für jede Eigenschaft verfügbar [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) sind. Einige Eigenschaften werden unten ausführlicher definiert.

<img src="../images/solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="HandMenu_ExampleScene Palm up">

* **Tresor Zone:** Die sichere Zone gibt an, wo Inhalte eingeschränkt werden sollen. Es wird empfohlen, Inhalte auf der Ulnar-Seite zu platzieren, um Überschneidungen mit der Hand und eine verbesserte Interaktionsqualität zu vermeiden. Tresor Zonen werden berechnet, indem die Ausrichtung der Hände, die in ein Ebenenorthogonal projiziert werden, zur Ansicht der Kamera und zum Raycasting an einem umgebenden Feld um die Hände geleitet wird. Tresor Zonen sind für die Arbeit mit [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) definiert, funktionieren aber auch mit anderen Controllertypen. Es wird empfohlen, zu untersuchen, was jede sichere Zone auf verschiedenen Controllertypen darstellt.

* **Hand folgen bis zur kameraseitigen Kamera** Wenn dieser aktiv ist, folgt der Solver der Handdrehung, bis das Menü ausreichend auf den Anviert ausgerichtet ist, an dem er sich der Kamera gegenübersieht. Dies funktioniert, indem SolverRotationBehavior im HandConstraintSolver von LookAtTrackedObject in LookAtMainCamera geändert wird, da der GazeAlignment-Winkel mit dem Solver variiert.

<img src="../images/solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="HandMenu Safe Zones">

* **Aktivierungsereignisse:** Derzeit [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) löst vier Aktivierungsereignisse aus. Diese Ereignisse können in vielen verschiedenen Kombinationen verwendet werden, um eindeutige Verhaltensweisen zu erstellen. Beispiele für [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) dieses Verhalten finden Sie in der HandBasedMenuExample-Szene unter `MRTK/Examples/Demos/HandTracking/Scenes/` .

  * *OnHandActivate:* wird ausgelöst, wenn eine Hand die IsHandActive-Methode erfüllt.
  * *OnHandDeactivate:* wird ausgelöst, wenn die IsHandActive-Methode nicht mehr erfüllt wird.
  * *OnFirstHandDetected:* tritt auf, wenn sich der Zustand der Handnachverfolgung von keiner Hand in der Ansicht in die erste Hand ändert.
  * *OnLastHandLost:* Tritt auf, wenn sich der Zustand der Handnachverfolgung von mindestens einer Hand in der Ansicht in keine Hände ändert.

* **Aktivierungs-/Deaktivierungslogik des Solvers:** Derzeit wird empfohlen, die Logik zu aktivieren und zu deaktivieren, [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) indem Sie den UpdateSolver-Wert von SolverHandler verwenden, anstatt das Objekt zu deaktivieren/zu aktivieren. Dies ist in der Beispielszene über die editorbasierten Hooks zu sehen, die nach den ManipulationHandler-Ereignissen "OnManipulationStarted/Ended" des angefügten Menüs ausgelöst werden.

  * *Beenden der Handeinschränkungslogik:* Legen Sie UpdateSolver auf False fest, anstatt HandConstraintPalmUp zu deaktivieren, wenn Sie versuchen, das objekt mit Handeinschränkung zu beenden (und die Aktivierungs-/Deaktivierungslogik nicht auszuführen).
    * Wenn Sie die logikbasierte (oder sogar nicht anverfolgte) Neuanvieren-Logik aktivieren möchten, wird anschließend die Funktion HandConstraintPalmUp.StartWorldLockReattachCheckCoroutine() aufgerufen. Dadurch wird eine Coroutine ausgelöst, die dann weiterhin überprüft, ob die IsValidController-Kriterien erfüllt sind, und UpdateSolver auf True festgelegt wird, sobald sie ist (oder das Objekt deaktiviert ist).
  * *Starten der Handeinschränkungslogik:* Legen Sie den UpdateSolver des SolverHandlers auf TRUE fest, wenn Sie versuchen, das handgebundene Objekt so festzulegen, dass es wieder ihrer Hand folgt (je nachdem, ob es die Aktivierungskriterien erfüllt).

* Logik erneut **anfügen:** Derzeit [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) kann das Zielobjekt automatisch erneut an den nachverfolgten Punkt angefügt werden, unabhängig davon, ob der UpdateSolver des SolverHandler true ist oder nicht. Dies erfolgt durch Aufrufen der StartWorldLockReattachCheckCoroutine()-Funktion von HandConstraintPalmUp, nachdem sie weltweit gesperrt wurde (was in diesem Fall den UpdateSolver des SolverHandlers auf False festlegt).

## <a name="see-also"></a>Siehe auch

* [Button](button.md) (Schaltfläche)
* [Menü "In der Nähe"](near-menu.md)
