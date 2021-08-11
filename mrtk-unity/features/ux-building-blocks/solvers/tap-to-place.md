---
title: Zum Platzieren tippen
description: Dokumentation des TapToPlace MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Zum Platzieren tippen,
ms.openlocfilehash: 98408312ec2637dc3fa137e7d51cce1f37e816f9a21b703ec9216bf90251661f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198318"
---
# <a name="tap-to-place"></a>Zum Platzieren tippen

![TapToPlace](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

„Zum Platzieren tippen“ ist eine Komponente für die Ferninteraktion, die verwendet wird, um ein Spielobjekt auf der Oberfläche zu platzieren. Diese Komponente ist nützlich, um Objekte in einem Raum-Mesh zu platzieren. „Zum Platzieren tippen“ verwendet eine Kombination aus zwei Klicks und einer Kopfbewegung, um ein Objekt zu platzieren. Ein Klick, um die Platzierung zu starten, die Kopfbewegung, um die Position des Objekts zu steuern, und ein Klick, um das Objekt in der Szene zu platzieren.

## <a name="using-tap-to-place"></a>Verwenden von „Zum Platzieren tippen“

1. Einrichten der Szene
    - Erstellen einer neuen Unity-Szene
    - Fügen Sie der Szene das MRTK hinzu, indem Sie zu **Mixed Reality Toolkit** > **Add to Scene and Configure** (Zu Szene hinzufügen und konfigurieren) navigieren.
    > [!NOTE]
    > „Zum Platzieren tippen“ verwendet vom MRTK-Eingabesystem gesteuerte Klicks, kann aber auch ohne Klicks gesteuert werden. Siehe hierzu weiter unten den Abschnitt „Konfigurierbarkeit des ‚Zum Platzieren tippen‘-Codes“.
    - Fügen Sie der Szene einen Würfel hinzu, ändern Sie die Skala in 0.2, und ändern Sie die Position in (0, 0, 0.7).
1. Fügen Sie [Zum Platzieren tippen](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) einem Spielobjekt mit einem Collider an.

    ![TapToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - Wenn die Komponente „Zum Platzieren tippen“ hinzugefügt wird, wird ebenfalls ein Solver-Handler angefügt. „Zum Platzieren tippen“ wird von der [Solver](solver.md)-Klasse abgeleitet, die einen Solver-Handler erfordert. Die Position eines „Zum Platzieren tippen“-Objekts wird relativ zum `TrackedTargetType` innerhalb des Solver-Handlers berechnet. Standardmäßig ist der Kopf der `TrackedTargetType`, d. h., wenn sich der Kopf bewegt, folgt ihm das Objekt, wenn es ausgewählt ist.  Der `TrackedTargetType` kann auch auf „Controller Ray“ (Controllerstrahl) festgelegt werden, bei dem das Objekt dem Controller folgt. Die erste Gruppe von Eigenschaften im „Zum Platzieren tippen“-Inspektor sind die [Allgemeinen Solvereigenschaften](solver.md#common-solver-properties) (Common Solver Properties).  
    > [!IMPORTANT]
    > „Zum Platzieren tippen“ ist ein eigenständiger Solver, der nicht mit anderen Solvern verkettet werden kann. Er kann nicht verkettet werden, weil „SolverHandler.UpdateSolvers“ verwendet wird, um die Position des Objekts während des Platzierens zu aktualisieren.
    - „Zum Platzieren tippen“-Eigenschaften:
        - `Auto Start`: Wenn „true“, beginnt der „Zum Platzieren tippen“-Solver damit, die Position des zu platzierenden Spielobjekts zu steuern. Das Objekt beginnt sofort, dem „TrackedTargetType“ (Kopf oder Controllerstrahl) zu folgen. Dieser Wert muss geändert werden, bevor Start() aufgerufen wird, um einen Effekt zu haben.
        - `Default Placement Distance`: Die Standardentfernung (in Metern), in der ein Objekt relativ zum TrackedTargetType im SolverHandler platziert wird. Das Spielobjekt wird in der Standardplatzierungsentfernung platziert, wenn eine Oberfläche nicht vom Raycast getroffen wird.
        - `Max Raycast Distance`: Die maximale Entfernung (Meter) für den Raycast, basierend auf dem Ursprung von „TrackedTargetType“. Dieser Raycast sucht nach einer Oberfläche, um ein ausgewähltes Objekt zu platzieren.
        - `UseDefaultSurfaceNormalOffset`: Diese Eigenschaft ist standardmäßig „true“ und stellt sicher, dass das Objekt, das platziert wird, an einer Oberfläche ausgerichtet ist. Wenn diese Eigenschaft „true“ ist, wird anstelle eines für die Eigenschaft `SurfaceNormalOffset` angegebenen Werts der Standardoffset der Oberflächennormale angewendet. „false“ gibt an, dass der Wert für `SurfaceNormalOffset` angewendet wird. Der Standardoffset der Oberflächennormale ist die Ausdehnung des Colliders entlang der z-Achse.
        - `Surface Normal Offset`: Die Entfernung zwischen der Mitte des zu platzierenden Spielobjekts und einer Oberfläche entlang der Oberflächennormale, wenn der Raycast auf eine Oberfläche trifft. Diese Eigenschaft wird nur auf ein Objekt angewendet, wenn `UseDefaultSurfaceNormalOffset` „false“ ist.
        - `Keep Orientation Vertical`: „true“ gibt an, dass das zu platzierende Spielobjekt aufrecht und an „Vector3.up“ ausgerichtet bleibt.
        - `Rotate According to Surface`: Bei „false“ ändert das zu platzierende Spielobjekt seine Drehung nicht entsprechend dem Oberflächentreffer.  Das Objekt bleibt der Kamera zugewandt, solange „IsBeingPlaced“ auf „true“ festgelegt ist.
        - `Magnetic Surfaces`: Ein Array von LayerMasks, die von höchster zu niedrigster Priorität hin ausgeführt werden sollen. Die erste Ebenenmaske zum Bereitstellen eines Raycasttreffers wird für Positionsberechnungen verwendet.
        - `Debug Enabled`: Bei „true“ und im Unity-Editor wird die Normale des Raycasttreffers gelb gezeichnet. Das Aktivieren des Debuggens ist nützlich, wenn `RotateAccordingToSurface` auf „true“ festgelegt ist, weil es die Normale des Oberflächentreffers zeichnet, die visuell erklärt, warum das Objekt an seiner aktuellen Ausrichtung platziert wird.
        - `On Placing Started`: Dieses Ereignis wird einmalig ausgelöst, wenn das zu platzierende Spielobjekt ausgewählt wird.
        - `On Placing Stopped`: Dieses Ereignis wird einmalig ausgelöst, wenn das zu platzierende Spielobjekt nicht ausgewählt platziert wird.

1. Testen des „Zum Platzieren tippen“-Verhaltens im Editor
    - Drücken Sie „Wiedergabe“, und halten Sie die Leertaste gedrückt, um eine Eingabesimulationshand anzuzeigen.
    - Bewegen Sie die Hand, bis sich der Würfel im Fokus befindet, und simulieren Sie einen Klick mit der Eingabesimulationshand, indem Sie mit der linken Maustaste klicken.
        - Wenn keine Collider in der Szene vorhanden sind, folgt das Objekt dem `TrackedTargetType` in der definierten `Default Placement Distance`.
    - Das Objekt folgt der Bewegung des `TrackedTargetType` nach der Auswahl. Um eine Kopfbewegung zu simulieren, drücken Sie die Tasten W, A, S, D. Die Kopfdrehung ändern Sie, indem Sie mit der rechten Maustaste klicken und diese gedrückt halten.
    - Um die Platzierung des Objekts zu beenden, klicken Sie erneut.  Das Objekt muss sich für den Klick zum Beenden der Platzierung nicht im Fokus befinden. Der Fokus ist nur für den ersten Klick erforderlich, der den Platzierungsprozess startet.

    `TrackedTargetType`: Kopf (Standard) |  `TrackedTargetType`Controllerstrahl (Controller Ray)
    :-------------------------:|:-------------------------:
    ![Kopf-Controllerstrahl der „Zum Platzieren tippen“-Eingabesimulation](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![Controllerstrahl 2der „Zum Platzieren tippen“-Eingabesimulation](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a>Konfigurierbarkeit des „Zum Platzieren tippen“-Codes

Das Timing der Auswahl des „Zum Platzieren tippen“-Objekts lässt sich auch über `StartPlacement()` und `StopPlacement()` steuern, anstatt ein Klickereignis zu erfordern. Diese Funktion ist nützlich für das Schreiben von Tests und stellt eine alternative Methode zum Platzieren eines Objekts im Editor dar, ohne das MRTK-Eingabesystem zu verwenden.

1. Erstellen eines leeren Spielobjekts
1. Erstellen Sie das folgende Beispielskript, und fügen Sie es an das leere Spielobjekt an.

    ```c#
    using UnityEngine;
    using Microsoft.MixedReality.Toolkit.Utilities.Solvers;

    public class TapToPlaceInputExample : MonoBehaviour
    {
        private GameObject cube;
        private TapToPlace tapToPlace;

        void Start()
        {
            cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
            cube.transform.localScale = Vector3.one * 0.2f;
            cube.transform.position = Vector3.forward * 0.7f;

            tapToPlace = cube.AddComponent<TapToPlace>();
        }

        void Update()
        {
            if (Input.GetKeyDown(KeyCode.U))
            {
                tapToPlace.StartPlacement();
            }
            if (Input.GetKeyDown(KeyCode.I))
            {
                tapToPlace.StopPlacement();
            }
        }
    }
    ```

1. Drücken Sie im Wiedergabemodus die *U-Taste,* , um das Platzieren des Würfels zu beginnen.
1. Drücken Sie die *I-TASTE*, um die Platzierung zu beenden.

## <a name="tap-to-place-example-scene"></a>„Zum Platzieren tippen“-Beispielszene

Die „Zum Platzieren tippen“-Beispielszene besteht aus 4 platzierbaren Objekten, von denen jedes eine andere Konfiguration hat. Die Beispielszene enthält Wände, um das Oberflächenplatzierungsverhalten zu zeigen, die in der Hierarchie standardmäßig deaktiviert sind. Die Beispielszene finden Sie im Unity-Paket „Microsoft.MixedReality.Toolkit.Unity.Examples“ auf der [Releaseseite](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases). Die Szene ist gespeichert unter: *MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*

![„Zum Platzieren tippen“-Beispiel](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a>Siehe auch

- [Solver](solver.md)
- [Räumliche Wahrnehmung](../../spatial-awareness/spatial-awareness-getting-started.md)
- [Eingabesimulation](../../input-simulation/input-simulation-service.md)
- [Hand-Tracking](../../input/hand-tracking.md)
- [Anvisieren](../../input/gaze.md)
