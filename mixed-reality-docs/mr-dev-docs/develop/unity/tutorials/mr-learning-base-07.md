---
title: Interagieren mit 3D-Objekten
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um mit 3D-Objekten in Mixed Reality-Apps zu interagieren und diese zu manipulieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Objektinteraktionen, Begrenzungssteuerelemente
ms.localizationpriority: high
ms.openlocfilehash: d620e0150510bd7d882036786f90db8f74229e6d139a313dc6f026dc10be8047
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191381"
---
# <a name="7-interacting-with-3d-objects"></a>7. Interagieren mit 3D-Objekten

In diesem Tutorial erfahren Sie, wie Sie die nahe und ferne Manipulation von 3D-Objekten aktivieren und die zulässigen Manipulationsarten einschränken. Darüber hinaus erfahren Sie, wie Sie 3D-Objekte mit Begrenzungssteuerelementen umgeben, um die Steuerung der Objektmanipulation zu vereinfachen.

## <a name="objectives"></a>Ziele

* Erfahren, wie 3D-Objekte so konfiguriert werden, dass Interaktion mit ihnen möglich ist
* Erfahren, wie 3D-Objekte mit Begrenzungssteuerelementen versehen werden

## <a name="manipulating-3d-objects"></a>Manipulieren von 3D-Objekten

In diesem Abschnitt fügen Sie die Funktion zum Manipulieren aller Teile des Rovers hinzu, die Sie im Rahmen des Tutorials [Positionieren von Objekten in der Szene](mr-learning-base-04.md) in der Tabelle angeordnet haben.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Hinzufügen der Komponente „Object Manipulator (Script)“ (Objektmanipulator (Skript)) zu allen Teilobjekten
2. Hinzufügen der Komponente NearInteractionGrabbable zu allen Teilobjekten
3. Konfigurieren der Komponente „Object Manipulator (Script)“ (Objektmanipulator (Skript))

> [!NOTE]
> Damit Sie **ein Objekt manipulieren** können, muss das Objekt die folgenden Komponenten aufweisen:
>
> * **Collider**-Komponente, z. B. ein Feld-Collider
> * **Object Manipulator (Script)** -Komponente
>
> Damit Sie **ein Objekt manipulieren** und **mit nachverfolgten Händen greifen** können, muss das Objekt die folgenden Komponenten aufweisen:
>
> * **Collider**-Komponente, z. B. ein Feld-Collider
> * **Object Manipulator (Script)** -Komponente
> * **NearInteractionGrabbable**-Komponente

Darüber hinaus werden Sie den Rover Explorer so konfigurieren, dass Sie die Rover-Teile auf dem Rover platzieren können, um ihn zu einer vollständigen Rover-Baugruppe zu machen.

Klappen Sie im Hierarchiefenster das Objekt „RoverExplorer > **RoverParts**“ auf, und wählen Sie alle seine untergeordneten Rover-Teilobjekte sowie das **RoverAssembly**-Objekt aus. Verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um allen ausgewählten Objekten die folgenden Komponenten hinzuzufügen:

* **Object Manipulator (Script)** -Komponente
* **NearInteractionGrabbable**-Komponente
* **Part Assembly Controller (Script)** -Komponente (Teilassembly-Controller (Skript))

![Unity mit ausgewählter RoverAssembly und allen Rover-Teil-Objekten ausgewählt sowie hinzugefügten Komponenten](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> Um mehrere Objekte auszuwählen, die sich nicht nebeneinander befinden, drücken und halten Sie die STRG-Taste, während Sie die Maus verwenden, um ein beliebiges Objekt auszuwählen.

> [!NOTE]
> Wenn Sie einen Objektmanipulator (Skript) hinzufügen, wird in diesem Fall der Einschränkungs-Manager (Skript) automatisch hinzugefügt, weil der Objektmanipulator (Skript) davon abhängt.

> [!NOTE]
> Im Rahmen dieses Tutorials wurden den Rover-Teilen bereits Collider hinzugefügt. Weitere Informationen zu Collidern finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collidern</a>.

> [!NOTE]
> Der Part Assembly-Controller (Script) ist nicht Teil des MRTK sondern ist in den Medienobjekten des Tutorials enthalten.

Konfigurieren Sie im Inspektorfenster, während alle Rover-Teilobjekte und das RoverAssembly-Objekt noch ausgewählt sind, die Komponente **Object Manipulator (Script)** (Objektmanipulator (Skript)) wie folgt:

* Deaktivieren Sie in der Dropdownliste **Two Handed Manipulation Type** (Zweihändiger Manipulationstyp) die Skalierung, sodass nur **Move** (Verschieben) und **Rotate** (Drehen) aktiviert sind

![Unity mit konfiguriertem Two Handed Manipulation-Typ](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> An diesem Punkt haben Sie die Objektmanipulation für alle Rover-Teilobjekte und das RoverAssembly-Objekt aktiviert.

Navigieren Sie im Projektfenster zum Ordner **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** (Pakete > Mixed Reality Toolkit Standard Assets > Audio), um die Audioclips zu finden:

![Unity-Projektfenster mit ausgewähltem Ordner „Audio“](images/mr-learning-base/base-07-section1-step1-3.png)

Wählen Sie im Hierarchiefenster erneut alle **Rover-Teilobjekte** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **Audio Sources** (Audioquellen) hinzuzufügen, und konfigurieren Sie sie wie folgt:

* Weisen Sie den Audioclip **MRTK_Scale_Start** dem Feld **AudioClip** zu
* Deaktivieren Sie das Kontrollkästchen **Play On Awake** (Nach Laden wiedergeben)
* Ändern Sie **Spatial Blend** (Räumliche Mischung) in 1

![Unity mit allen Rover-Teilen ausgewählt und hinzugefügter und konfigurierter Audio Source-Komponente](images/mr-learning-base/base-07-section1-step1-4.png)

Klappen Sie im Hierarchiefenster das Objekt „RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints**“ auf, um alle Platzierungshinweisobjekte anzuzeigen, wählen Sie dann das Rover-Teil „Camera_part“ aus („RoverParts > **Camera_Part**“), und konfigurieren Sie die Komponente **Part Assembly Controller (Script)** wie folgt:

* Weisen Sie das Objekt **Camera_PlacementHint** dem Feld **Location To Place** zu

![Unity mit konfigurierter Camera_Part PartAssemblyController-Komponente](images/mr-learning-base/base-07-section1-step1-5.png)

**Wiederholen** Sie diesen Schritt für alle verbleibenden Rover-Teilobjekte und das RoverAssembly-Objekt, um die Komponente **Part Assembly Controller (Script)** wie folgt zu konfigurieren:

* Weisen Sie für das **Generator_Part** das **Generator_PlacementHint**-Objekt dem Feld **Location To Place** zu
* Weisen Sie für das **Lights_Part** das **Lights_PlacementHint**-Objekt dem Feld **Location To Place** zu
* Weisen Sie für das **UHFAntenna_Part** das **UHFAntenna_PlacementHint**-Objekt dem Feld **Location To Place** zu
* Weisen Sie für das **Spectrometer_Part** das **Spectrometer_PlacementHint**-Objekt dem Feld **Location To Place** zu
* Weisen Sie für die **RoverAssembly** das Objekt selbst, d. h. eben dieses **RoverAssembly**-Objekt, dem Feld **Location To Place** zu

Wählen Sie im Hierarchiefenster das Schaltflächenobjekt „RoverExplorer > Buttons > **Reset** (RoverExplorer > Schaltflächen > Zurücksetzen) aus, und konfigurieren Sie dann im Inspektorfenster das **OnClick ()** -Interaktionsereignis wie folgt:

* Weisen Sie das **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **PartAssemblyController** > **ResetPlacement ()** aus, um diese Funktion als Aktion festzulegen, die beim Auslösen des Ereignisses ausgeführt wird

![Unity mit konfiguriertem OnClick-Ereignis für das Reset-Schaltflächenobjekt](images/mr-learning-base/base-07-section1-step1-6.png)

Wenn Sie jetzt in den Spielmodus wechseln, können Sie nahe oder ferne Interaktion verwenden, um die Rover-Teile auf dem Rover zu platzieren. Sobald sich das Teil nahe am entsprechenden Platzierungshinweis befindet, rastet es an der vorgesehenen Position ein und wird zu einem Teil des Rovers. Zum Zurücksetzen der Platzierungen können Sie auf die Schaltfläche „Zurücksetzen“ klicken:

![Geteilte Ansicht des Unity-Wiedergabemodus mit gedrückter Schaltfläche „Reset“](images/mr-learning-base/base-07-section1-step1-7.png)

Weitere Informationen über die Objektmanipulator-Komponente und die ihr zugeordneten Eigenschaften finden Sie in der Anleitung zum [Objektmanipulator](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator) im [MRTK-Dokumentationsportal](/windows/mixed-reality/mrtk-unity/).

## <a name="adding-bounds-control"></a>Hinzufügen des Begrenzungssteuerelements

Das Begrenzungssteuerelement macht das einhändige Manipulieren von Objekten sowohl für die Nah- als auch für die Ferninteraktion komfortabler und intuitiver, indem es Ziehpunkte bereitstellt, die für die Änderung der Größe und zum Rotieren verwendet werden können.

In diesem Beispiel fügen Sie dem RoverExplorer-Objekt ein Begrenzungssteuerelement hinzu, damit die gesamte Erfahrung komfortabel bewegt, gedreht und skaliert werden kann. Darüber hinaus werden Sie das Menü so konfigurieren, dass das Begrenzungssteuerelement ein- und ausgeschaltet werden kann.

Wählen Sie im Hierarchiefenster das **RoverExplorer**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die folgenden Komponenten hinzuzufügen:

* **BoundsControl**-Komponente
* **Object Manipulator (Script)** -Komponente

**Deaktivieren** Sie dann das Kontrollkästchen neben allen Komponenten, um sie als standardmäßig **deaktiviert** festzulegen:

![Unity mit ausgewähltem RoverExplorer-Objekt und hinzugefügten und deaktivierten Komponenten](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> Die Visualisierung des Begrenzungssteuerelements wird zur Laufzeit erstellt und ist daher erst sichtbar, wenn Sie in den Spielmodus wechseln.

> [!NOTE]
> Der Objektmanipulator (Skript) fügt automatisch den Einschränkungs-Manager (Skript) hinzu.

Klappen Sie im Hierarchiefenster das Objekt „Menu > **ButtonCollection**“ (Menü > Schaltflächensammlung) auf, um die vier Schaltflächen anzuzeigen, benennen Sie die dritte Schaltfläche in **BoundsControl_Enable** um, und konfigurieren Sie dann im Inspektorfenster die Komponente **Button Config Helper (Script)** wie folgt:

* Ändern Sie den **Main Label Text** (Hauptbezeichnungstext) in **Enable** (Aktivieren)
* Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundsControl** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Überprüfen Sie, ob das Argumentkontrollkästchen **aktiviert** ist
* Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen
* Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Überprüfen Sie, ob das Argumentkontrollkästchen **aktiviert** ist
* Belassen Sie das **Symbol** als Symbol „Cube mit Begrenzungssteuerelement“.

![Unity mit ausgewähltem BoundsControl_Enable-Schaltflächenobjekt und konfigurierter Button Config Helper-Komponente](images/mr-learning-base/base-07-section2-step1-2.png)

Benennen Sie die vierte und letzte Schaltfläche in **BoundsControl_Disable** um, und konfigurieren Sie dann im Inspektorfenster die Komponente **Button Config Helper (Script)** wie folgt:

* Ändern Sie den **Main Label Text** (Hauptbezeichnungstext) in **Disable** (Deaktivieren)
* Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundsControl** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist
* Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen
* Weisen Sie das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist
* Ändern Sie das **Symbol** in das Symbol „Cube mit Begrenzungssteuerelement“.

![Unity mit ausgewähltem BoundsControl_Disable-Schaltflächenobjekt und konfigurierter Button Config Helper-Komponente](images/mr-learning-base/base-07-section2-step1-3.png)

Wenn Sie jetzt in den Spielmodus wechseln und das Begrenzungssteuerelement aktivieren, indem Sie auf die Schaltfläche „Aktivieren“ klicken, können Sie nahe oder ferne Interaktion verwenden, um das Begrenzungssteuerelement zu bewegen, drehen und skalieren, und die Schaltfläche „Deaktivieren“ verwenden, um das Begrenzungssteuerelement wieder zu deaktivieren:

![Geteilte Ansicht des Unity-Wiedergabemodus mit manipuliertem Begrenzungssteuerelement](images/mr-learning-base/base-07-section2-step1-4.png)

Weitere Informationen über die Bounds Control-Komponente und die ihr zugeordneten Eigenschaften finden Sie in der Anleitung zum [Bounds Control](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounds-control) im [MRTK-Dokumentationsportal](/windows/mixed-reality/mrtk-unity/).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie die nahe und ferne Manipulation für 3D-Objekte aktivieren und die zulässigen Manipulationsarten einschränken. Darüber hinaus haben Sie gelernt, wie Sie 3D-Objekte mit Begrenzungssteuerelementen umgeben, um die Steuerung der Objektmanipulation zu vereinfachen.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 8. Verwenden von Eye Tracking](mr-learning-base-08.md)