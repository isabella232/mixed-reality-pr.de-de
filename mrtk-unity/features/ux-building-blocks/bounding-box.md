---
title: Begrenzungsrahmen
description: Übersicht über Bounding Box in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Bounding Box
ms.openlocfilehash: e8e3587ba871e127590a975b688a70db337daa19
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177543"
---
# <a name="bounding-box"></a>Begrenzungsrahmen

![Begrenzungsrahmen](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> Begrenzungsfeld ist veraltet und wird durch das [Nachfolger-Begrenzungssteuerfeld ersetzt.](bounds-control.md) Verwenden [Sie eine der Migrationsoptionen, um](#migrating-to-bounds-control) vorhandene Spielobjekte zu aktualisieren.

Das [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) Skript stellt grundlegende Funktionen zum Transformieren von Objekten in Mixed Reality zur Verfügung. Ein Begrenzungsfeld zeigt einen Würfel um das Hologramm an, um anzugeben, dass mit ihm interagiert werden kann. Handles an den Ecken und Kanten des Cubes ermöglichen das Skalieren oder Drehen des Objekts. Das Begrenzungsfeld reagiert auch auf Benutzereingaben. Auf HoloLens 2 reagiert der Begrenzungsfeld beispielsweise auf die Fingernähe und gibt visuelles Feedback, um den Abstand zum Objekt zu erkennen. Alle Interaktionen und Visuals können einfach angepasst werden.

Weitere Informationen finden Sie unter [Begrenzungsfeld und App-Leiste](/windows/mixed-reality/app-bar-and-bounding-box) im Windows Dev Center.

## <a name="example-scene"></a>Beispielszene

Beispiele für Begrenzungsfeldkonfigurationen finden Sie in der `BoundingBoxExamples` Szene.

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Hinzufügen und Konfigurieren eines Begrenzungsfelds mit dem Unity-Inspektor

1. Hinzufügen von Box Collider zu einem Objekt
2. Zuweisen `BoundingBox` eines Skripts zu einem Objekt
3. Konfigurieren von Optionen, z. B. Aktivierungsmethoden (siehe [Abschnitt Inspektoreigenschaften](#inspector-properties) weiter unten)
4. (Optional) Zuweisen von Prefabs und Materialien für ein HoloLens 2 Umrandungsfeld (siehe Abschnitt ["Handlestile"](#handle-styles) weiter unten)

> [!NOTE]
> Verwenden *Sie das Feld Target Object* and Bounds Override (Zielobjekt und *Begrenzungsüberschreibung)* im Inspektor, um bestimmte Objekte und Collider im Objekt mit mehreren untergeordneten Komponenten zu zuweisen.

![Begrenzungsfeld 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>Hinzufügen und Konfigurieren eines Begrenzungsfelds im Code

1. Instanziieren des Cubes "GameObject"

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Zuweisen `BoundingBox` eines Skripts zu einem Objekt mit Collider mithilfe von AddComponent<>()

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. Konfigurieren von Optionen (siehe [Abschnitt Inspektoreigenschaften](#inspector-properties) weiter unten)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. (Optional) Zuweisen von Prefabs und Materialien für ein HoloLens 2 Umrandungsfeld. Dies erfordert weiterhin Zuweisungen über den Inspektor, da die Materialien und Prefabs dynamisch geladen werden sollten.

> [!NOTE]
> Die Verwendung des Ordners "Resources" von Unity oder [shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) zum dynamischen Laden von Shadern wird nicht empfohlen, da Shader-Permutationen zur Laufzeit möglicherweise fehlen.

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>Beispiel: Festlegen der minimalen, maximalen Begrenzungsfeldskala mit MinMaxScaleConstraint

Verwenden Sie zum Festlegen der minimalen und maximalen Skalierung [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) den . Sie können auch MinMaxScaleConstraint verwenden, um die minimale und maximale Skalierung für [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) festlegen.

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>Beispiel: Hinzufügen eines Begrenzungsfelds um ein Spielobjekt

Um ein Begrenzungsfeld um ein Objekt hinzuzufügen, fügen Sie ihm einfach `BoundingBox` eine Komponente hinzu:

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>Inspektoreigenschaften

### <a name="target-object"></a>Zielobjekt

Diese Eigenschaft gibt an, welches Objekt durch die Bearbeitung des Begrenzungsfelds transformiert wird. Wenn kein Objekt festgelegt ist, wird das Begrenzungsfeld standardmäßig auf das Besitzerobjekt festgelegt.

### <a name="bounds-override"></a>Außerkraftsetzung von Begrenzungen

Legt einen Feld-Collider aus dem -Objekt für die Berechnung von Begrenzungen fest.

### <a name="activation-behavior"></a>Aktivierungsverhalten

Es gibt mehrere Optionen zum Aktivieren der Begrenzungsfeldschnittstelle.

* *Beim Start aktivieren:* Das Begrenzungsfeld wird angezeigt, sobald die Szene gestartet wurde.
* *Durch Näherung aktivieren:* Das Begrenzungsfeld wird sichtbar, wenn sich eine artikulierte Hand in der Nähe des Objekts befindet.
* *Durch Zeiger aktivieren:* Das Begrenzungsfeld wird sichtbar, wenn es von einem Handstrahlzeiger als Ziel angezeigt wird.
* *Manuell aktivieren:* Begrenzungsfeld wird nicht automatisch angezeigt. Sie können sie manuell über ein Skript aktivieren, indem Sie auf die boundingBox.Active-Eigenschaft zugreifen.

### <a name="scale-minimum"></a>Minimum skalieren

Die zulässige Mindestskala. Diese Eigenschaft ist veraltet und es ist vorzuziehen, ein Skript [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) hinzuzufügen. Wenn dieses Skript hinzugefügt wird, wird die Mindestskala daraus und nicht aus dem Begrenzungsfeld übernommen.

### <a name="scale-maximum"></a>Maximale Skalierung

Die maximal zulässige Skalierung. Diese Eigenschaft ist veraltet und es ist vorzuziehen, ein Skript [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) hinzuzufügen. Wenn dieses Skript hinzugefügt wird, wird die maximale Skalierung aus ihm und nicht aus dem Begrenzungsfeld übernommen.

### <a name="box-display"></a>Feldanzeige

Verschiedene Optionen für die Begrenzungsfeldvisualisierung.

Wenn Flatten Axis auf *Flatten Auto* festgelegt ist, wird die Bearbeitung entlang der Achse mit dem kleinsten Umfang vom Skript nicht zulässig. Dies führt zu einem 2D-Begrenzungsfeld, das normalerweise für schlanke Objekte verwendet wird.

### <a name="handles"></a>Ziehpunkte

Sie können das Material und das Prefab zuweisen, um den Handlestil zu überschreiben. Wenn keine Handles zugewiesen sind, werden sie im Standardformat angezeigt.

## <a name="events"></a>Ereignisse

Das Begrenzungsfeld stellt die folgenden Ereignisse zur Verfügung. In diesem Beispiel werden diese Ereignisse verwendet, um Audiofeedback wieder zu geben.

* **Rotate Started**(Gestartet drehen): Wird ausgelöst, wenn die Drehung gestartet wird.
* **Rotate Ended :Wird** ausgelöst, wenn die Drehung endet.
* **Gestartete Skalierung:** Wird beim Starten der Skalierung gestartet.
* **Skalierung beendet:** Wird beim Ende der Skalierung aus.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>Behandeln von Stilen

Wenn Sie das Skript nur zuweisen, wird standardmäßig das Handle des Stils HoloLens [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) 1. Generation angezeigt. Um die HoloLens 2 verwenden zu können, müssen Sie geeignete Handle-Prefabs und -Materialien zuweisen.

![Begrenzungsfeld-Handlestile](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

Im Folgenden finden Sie die Prefabs, Materialien und skalierungswerte für die HoloLens 2 Umrandungsfeldhandles. Sie finden dieses Beispiel in der `BoundingBoxExamples` Szene.

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a>Handles (Setup für HoloLens 2 Format)

* **Handle Material**: BoundingBoxHandleWhite.mat
* **Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat
* **Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab
* **Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab
* **Größe des Skalierungshandpunkts:** 0,016 (1,6 cm)
* **Scale Handle Collider Padding**: 0.016 (macht den ziehbaren Collider etwas größer als das Handlevisual)
* **Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab
* **Rotationshandpunktgröße:** 0,016
* **Rotation Handle Collider Padding**: 0.016 (macht den ziehbaren Collider etwas größer als das Handlevisual)

### <a name="proximity-setup-for-hololens-2-style"></a>Näherung (Setup für HoloLens 2 Format)

Zeigen Sie die Ziehpunkte mit Animation basierend auf dem Abstand zu den Händen an, und blenden Sie sie aus. Es verfügt über eine animation zur zweistufigen Skalierung.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **Näherungseffekt aktiv:** Aktivierung des näherungsbasierten Handles aktivieren
* **Mittlere Nähe behandeln:** Entfernung für die Skalierung im ersten Schritt
* **Handle Close Proximity**:Distance for the 2nd step scaling
* **Fernskala:** Der Standardskalierungswert des Handle-Assets, wenn die Hände sich nicht im Bereich der Interaktion des Begrenzungsfelds befinden (Der Abstand wird oben durch "Mittlere Nähe behandeln" definiert). Verwenden Sie 0, um handle standardmäßig auszublenden.)
* **Mittelmaßstab:** Skalierungswert des Handle-Medienwerts, wenn sich die Hände innerhalb des Bereichs der Begrenzungsfeldinteraktion befinden (über "Handle Close Proximity" definierter Abstand). Verwenden Von 1 zum Anzeigen der normalen Größe)
* Close Scale :Scale value of the handle asset when the hands are within range of the grab interaction (Close **Scale:** Skalierungswert des Handle-Assets, wenn sich die Hände innerhalb des Bereichs der Greifinteraktion befinden (Der Abstand wird oben durch "Handle Close Proximity" definiert). Verwenden Von 1.x zum Anzeigen einer größeren Größe)

## <a name="making-an-object-movable-with-manipulation-handler"></a>Bewegbares Objekt mit Manipulationshandler

Ein Begrenzungsfeld kann mit kombiniert werden, um das Objekt mithilfe der [`ManipulationHandler.cs`](manipulation-handler.md) Ferninteraktion verschiebbar zu machen. Der Manipulationshandler unterstützt sowohl ein- als auch zweihändige Interaktionen. [Die Handverfolgung](../input/hand-tracking.md) kann verwendet werden, um mit einem Objekt in der Nähe zu interagieren.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

Damit sich die Begrenzungsfeldränder beim Verschieben mithilfe der Ferninteraktion von genauso verhalten, wird empfohlen, die Ereignisse für On Manipulation Started On Manipulation Ended (Beim Ende der Bearbeitung gestartet) mit zu verbinden, wie im obigen Screenshot [`ManipulationHandler`](manipulation-handler.md)   /   `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` gezeigt.

## <a name="migrating-to-bounds-control"></a>Migrieren zur Begrenzungssteuerung

Vorhandene Prefabs und [](bounding-box.md) Instanzen mit Begrenzungsfeld können über das Migrationsfenster, das Teil des MRTK-Toolspakets ist, auf das neue Begrenzungssteuerfeld aktualisiert werden. [](../tools/migration-window.md)

Für das Upgrade einzelner Instanzen des Begrenzungsfelds gibt es auch eine Migrationsoption innerhalb des Eigenschafteninspektors der Komponente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
