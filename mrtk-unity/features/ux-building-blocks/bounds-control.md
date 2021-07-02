---
title: Begrenzungssteuerelement
description: Übersicht über das Begrenzungssteuerelement in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Bounds Control,
ms.openlocfilehash: f5f5e1f463f741eb23f75c9826034b8974baf947
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176463"
---
# <a name="bounds-control"></a>Begrenzungssteuerelement

![Begrenzungssteuerelement](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl* ist die neue Komponente für das Manipulationsverhalten, die zuvor in *BoundingBox* gefunden wurde. Das Begrenzungssteuerelement führt eine Reihe von Verbesserungen und Vereinfachungen beim Setup durch und fügt neue Features hinzu. Diese Komponente ist ein Ersatz für den Begrenzungsfeld, der veraltet ist.

Das [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) Skript bietet grundlegende Funktionen zum Transformieren von Objekten in Mixed Reality. Ein Begrenzungssteuerelement zeigt ein Feld um das Hologramm an, um anzugeben, dass es mit ihm interagiert werden kann. Handles an den Ecken und Rändern des Felds ermöglichen das Skalieren, Drehen oder Übersetzen des Objekts. Das Begrenzungssteuerelement reagiert auch auf Benutzereingaben. Auf HoloLens 2 reagiert das Begrenzungssteuerelement z. B. auf Fingernähe und gibt visuelles Feedback, um die Entfernung zum Objekt zu erkennen. Alle Interaktionen und Visuals können einfach angepasst werden.

## <a name="example-scene"></a>Beispielszene

Beispiele für Begrenzungssteuerelementkonfigurationen finden Sie in der `BoundsControlExamples` Szene.

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>Inspektoreigenschaften

### <a name="target-object"></a>Zielobjekt

Diese Eigenschaft gibt an, welches Objekt durch die Bearbeitung des Begrenzungssteuerelements transformiert wird. Wenn kein Objekt festgelegt ist, wird standardmäßig das Besitzerobjekt verwendet.

### <a name="activation-behavior"></a>Aktivierungsverhalten

Es gibt mehrere Optionen zum Aktivieren der Begrenzungssteuerelementschnittstelle.

* *Bei Start aktivieren:* Das Begrenzungssteuerelement wird nach dem Start der Szene angezeigt.
* *Activate By Proximity*: Das Steuerelement Bounds wird sichtbar, wenn sich eine artikulierte Hand in der Nähe des Objekts befindet.
* *Aktivieren nach Zeiger:* Das Steuerelement "Bounds" wird sichtbar, wenn es von einem Handstrahlzeiger als Ziel verwendet wird.
* *Activate By Proximity and Pointer (Durch Näherung und Zeiger aktivieren):* Das Steuerelement Bounds wird sichtbar, wenn es von einem Handstrahlzeiger angezielt wird oder sich eine artikulierte Hand in der Nähe des Objekts befindet.
* *Manuell aktivieren:* Das Steuerelement Bounds wird nicht automatisch angezeigt. Sie können sie manuell über ein Skript aktivieren, indem Sie auf die boundsControl.Active-Eigenschaft zugreifen.

### <a name="bounds-override"></a>Außerkraftsetzung von Begrenzungen

Legt einen Feld-Collider aus dem -Objekt für die Berechnung von Begrenzungen fest.

### <a name="box-padding"></a>Auffüllen von Schachteln

Fügt den Collidergrenzen, die zum Berechnen der Umfang des Steuerelements verwendet werden, einen Abstand hinzu. Dies wirkt sich nicht nur auf die Interaktion aus, sondern auch auf die Visuals.

### <a name="flatten-axis"></a>Flache Achse

Gibt an, ob das Steuerelement in einer der Achsen flach ist, sodass es zweidimensional ist und die Bearbeitung entlang dieser Achse nicht zu lässt. Dieses Feature kann für schlanke Objekte wie Schiefer verwendet werden.
Wenn flatten axis auf *Flatten Auto* festgelegt ist, wählt das Skript automatisch die Achse mit dem kleinsten Umfang als flache Achse aus.

### <a name="smoothing"></a>Glättung

Der Glättungsabschnitt ermöglicht das Konfigurieren des Glättungsverhaltens für die Skalierung und Drehung des Steuerelements.

### <a name="visuals"></a>Visuals

Die Darstellung des Begrenzungssteuerelements kann durch Ändern einer der entsprechenden Visualkonfigurationen konfiguriert werden.
Visuelle Konfigurationen sind entweder verknüpfte oder inlineskriptfähige Objekte und werden im [Abschnitt Konfigurationsobjekt](#configuration-objects)ausführlicher beschrieben.

## <a name="configuration-objects"></a>Konfigurationsobjekte

Das Steuerelement enthält eine Reihe von Konfigurationsobjekten, die als skriptfähige Objekte gespeichert und von verschiedenen Instanzen oder Prefabs gemeinsam genutzt werden können. Konfigurationen können entweder als einzelne skriptfähige Medienobjektdateien oder als geschachtelte skriptfähige Objekte innerhalb von Prefabs freigegeben und verknüpft werden. Weitere Konfigurationen können auch direkt auf der Instanz definiert werden, ohne eine Verknüpfung mit einem externen oder geschachtelten Skriptobjekt zu erstellen.

Der Begrenzungssteuerelementinspektor gibt an, ob eine Konfiguration als Teil der aktuellen Instanz freigegeben oder inline ist, indem eine Meldung im Eigenschafteninspektor angezeigt wird. Darüber hinaus können freigegebene Instanzen nicht direkt im Eigenschaftenfenster des Begrenzungssteuerelements selbst bearbeitet werden. Stattdessen muss das Objekt, mit dem die Verknüpfung erfolgt, direkt geändert werden, um versehentliche Änderungen an freigegebenen Konfigurationen zu vermeiden.

Derzeit bietet das Begrenzungssteuerelement Optionen für Konfigurationsobjekte für die folgenden Features:

* Ziehpunkte
  * [Skalierungshandles](#scale-handles-configuration)
  * [Drehungshandles](#rotation-handles-configuration)
  * [Übersetzungshandles](#translation-handles-configuration)
* [Links/Wireframe](#links-configuration-wireframe)
* [Box-Anzeige](#box-configuration)
* [Näherungseffekt](#proximity-effect-configuration)

### <a name="box-configuration"></a>Box-Konfiguration

Die Boxkonfiguration ist für das Rendern eines Volltonfelds mit Begrenzungen verantwortlich, die über Collidergröße und Feldauffüllung definiert werden. Die folgenden Eigenschaften können eingerichtet werden:

* **Feldmaterial:** Definiert das Material, das auf das gerenderte Feld angewendet wird, wenn keine Interaktion stattfindet. Ein Feld wird nur gerendert, wenn dieses Material festgelegt ist.
* **Gepacktes Material:** Material für die Box, wenn der Benutzer mit dem Steuerelement interagiert, indem er über nah- oder ferninteraktion greift.
* **Anzeigeskala für flache Achsen:** Eine Skala, die auf die Feldanzeige angewendet wird, wenn eine der Achsen [flacher](#flatten-axis)wird.

### <a name="scale-handles-configuration"></a>Konfiguration von Skalierungshandles

Dieser Eigenschaftenschubladen ermöglicht es, das Verhalten und die Visualisierung von Skalierungshandles des Begrenzungssteuerelements zu ändern.

* **Handlematerial:** Material, das auf die Ziehpunkte angewendet wird.
* **Ziehmaterial** verarbeiten: Material, das auf den Ziehpunkt angewendet wird.
* **Handle prefab**: optionales Prefab für das Skalierungshandle. Wenn nicht festgelegt ist, verwendet MRTK einen Cube als Standard.
* **Handlegröße:** Größe des Skalierungshandle.
* **Colliderauffüllung:** Auffüllung, die dem Handle-Collider hinzugefügt werden soll.
* Zeichnen des **Tethers beim Bearbeiten:** Wenn aktiv eine Tetherlinie vom Beginn der Interaktion bis zur aktuellen Hand- oder Zeigerposition zeichnet.
* **Handles ignorieren Collider:** Wenn ein Collider hier verknüpft wird, ignorieren Handles alle Konflikte mit diesem Collider.
* **Handle slate prefab**: prefab to use for the handle when the control is flattened.
* **Skalierungshandles anzeigen:** Steuert die Sichtbarkeit des Handles.
* **Skalierungsverhalten:** Kann auf einheitliche oder nicht einheitliche Skalierung festgelegt werden.

### <a name="rotation-handles-configuration"></a>Rotation behandelt Konfiguration

Diese Konfiguration definiert das Rotationshandleverhalten.

* **Handlematerial:** Material, das auf die Ziehpunkte angewendet wird.
* **Ziehmaterial** verarbeiten: Material, das auf den Ziehpunkt angewendet wird.
* **Handle prefab**: optionales Prefab für das Handle. Wenn nicht festgelegt ist, verwendet MRTK standardmäßig eine Kugel.
* **Handlegröße:** Größe des Handles.
* **Colliderauffüllung:** Auffüllung, die dem Handle-Collider hinzugefügt werden soll.
* Zeichnen des **Tethers beim Bearbeiten:** Wenn aktiv eine Tetherlinie vom Beginn der Interaktion bis zur aktuellen Hand- oder Zeigerposition zeichnet.
* **Handles ignorieren Collider:** Wenn ein Collider hier verknüpft wird, ignorieren Handles alle Konflikte mit diesem Collider.
* **Behandeln des Prefab-Collidertyps:** Collidertyp, der mit dem erstellten Handle verwendet werden soll.
* **Handle für X anzeigen:** Steuert die Sichtbarkeit des Handles für die X-Achse.
* **Handle für Y anzeigen:** Steuert die Sichtbarkeit des Handles für die Y-Achse.
* **Handle für Z anzeigen:** Steuert die Sichtbarkeit des Handles für die Z-Achse.

### <a name="translation-handles-configuration"></a>Konfiguration der Übersetzungshandles

Ermöglicht das Aktivieren und Konfigurieren von Übersetzungshandles für das Begrenzungssteuerelement. Beachten Sie, dass Übersetzungshandles standardmäßig deaktiviert sind.

* **Handlematerial:** Material, das auf die Ziehpunkte angewendet wird.
* **Ziehmaterial** verarbeiten: Material, das auf den Ziehpunkt angewendet wird.
* **Handle prefab**: optionales Prefab für das Handle. Wenn nicht festgelegt ist, verwendet MRTK standardmäßig eine Kugel.
* **Handlegröße:** Größe des Handles.
* **Colliderauffüllung:** Auffüllung, die dem Handle-Collider hinzugefügt werden soll.
* Zeichnen des **Tethers beim Bearbeiten:** Wenn aktiv eine Tetherlinie vom Beginn der Interaktion bis zur aktuellen Hand- oder Zeigerposition zeichnet.
* **Handles ignorieren Collider:** Wenn ein Collider hier verknüpft wird, ignorieren Handles alle Konflikte mit diesem Collider.
* **Behandeln des Prefab-Collidertyps:** Collidertyp, der mit dem erstellten Handle verwendet werden soll.
* **Handle für X anzeigen:** Steuert die Sichtbarkeit des Handles für die X-Achse.
* **Handle für Y anzeigen:** Steuert die Sichtbarkeit des Handles für die Y-Achse.
* **Handle für Z anzeigen:** Steuert die Sichtbarkeit des Handles für die Z-Achse.

### <a name="links-configuration-wireframe"></a>Linkkonfiguration (Wireframe)

Die Linkkonfiguration aktiviert das Wireframe-Feature des Begrenzungssteuerelements. Die folgenden Eigenschaften können konfiguriert werden:

* **Wireframe-Material:** das Material, das auf das Wireframe-Gittermodell angewendet wird.
* **Wireframe-Edgeradius:** die Stärke des Wireframes.
* **Wireframe-Form:** Die Form des Wireframes kann entweder kubisch oder zylindrisch sein.
* **Wireframe anzeigen:** Steuert die Sichtbarkeit des Wireframes.

### <a name="proximity-effect-configuration"></a>Konfiguration des Näherungseffekts

Zeigen Sie die Handles basierend auf der Entfernung zu den Händen mit Animation an, und blenden Sie sie aus. Sie verfügt über zweistufige Skalierungsanimationen. Standardwerte werden auf HoloLens 2 Stilverhalten festgelegt.

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **Näherungseffekt aktiv:** Aktivierung des näherungsbasierten Handles aktivieren
* **Objekt mittlere Nähe:** Entfernung für die Skalierung im ersten Schritt
* Objekt close proximity :Distance for the 2nd step scaling **(Objektnähe:** Entfernung für die Skalierung im zweiten Schritt)
* **Far Scale**: Der Standardskalierenwert des Handlemedienobjekts, wenn sich die Hände außerhalb des Bereichs der Begrenzungssteuerungsinteraktion befinden (entfernung oben durch "Mittlere Nähe behandeln" definiert). Verwenden Sie 0, um das Handle standardmäßig auszublenden.)
* **Mittlere Skalierung:** Der Skalierungswert des Handlemedienobjekts, wenn sich die Hände innerhalb des Bereichs der Begrenzungssteuerelementinteraktion befinden (entfernung oben durch "Handle Close Proximity" definiert). Verwenden Sie 1, um die normale Größe anzuzeigen.)
* **Skala schließen:** Skalierungswert des Handleobjekts, wenn sich die Hände innerhalb des Bereichs der Ziehinteraktion befinden (entfernung oben durch "Handle Close Proximity" definiert). Verwenden Sie 1.x, um eine größere Größe anzuzeigen.)
* **Far Grow Rate**:Rate a proximity scaled object scales when the hand moves from medium to far proximity.
* **Mittlere Zuwachsrate:** Raten Sie, dass ein näher skaliertes Objekt skaliert wird, wenn sich die Hand von mittel in nah bewegt.
* **Close Grow Rate (Zuwachsrate** schließen): Raten Sie, dass ein näher skaliertes Objekt skaliert wird, wenn sich die Hand von der Nähe zum Objektcenter bewegt.

## <a name="constraint-system"></a>Einschränkungssystem

Das Begrenzungssteuerelement unterstützt die Verwendung des [Einschränkungs-Managers](constraint-manager.md) zum Einschränken oder Ändern des Übersetzungs-, Drehungs- oder Skalierungsverhaltens bei Verwendung von Begrenzungssteuerelementhandles.

Der Eigenschafteninspektor zeigt alle verfügbaren Einschränkungs-Manager, die an dasselbe Spielobjekt angefügt sind, in einer Dropdownliste mit einer Option zum Scrollen und Hervorheben des ausgewählten Einschränkungs-Managers an.

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>Ereignisse

Das Bounds-Steuerelement stellt die folgenden Ereignisse bereit. In diesem Beispiel werden diese Ereignisse verwendet, um Audiofeedback wiederzuspielen.

* **Rotieren gestartet:** Wird ausgelöst, wenn die Drehung beginnt.
* **Rotieren beendet:** Wird ausgelöst, wenn die Drehung beendet wird.
* **Skalierung gestartet:** Wird ausgelöst, wenn die Skalierung gestartet wird.
* **Skalierung beendet:** Wird ausgelöst, wenn die Skalierung beendet wird.
* **Translate Started**: Wird ausgelöst, wenn die Übersetzung beginnt.
* **Translate Stopped**: Wird ausgelöst, wenn die Übersetzung beendet wird.

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>Elastische Datenbanken (experimentell)

Elastische Datenbanken können verwendet werden, wenn Objekte über das Begrenzungssteuerelement bearbeitet werden. Beachten Sie, dass sich das [System für elastische Datenbanken](../experimental/elastic-system.md) noch im experimentellen Zustand befindet. Um elastische Datenbanken zu aktivieren, verknüpfen Sie entweder eine vorhandene Elastics Manager-Komponente, oder erstellen und verknüpfen Sie über die Schaltfläche einen neuen Manager für elastische `Add Elastics Manager` Datenbanken.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>Handlestile

Wenn Sie das Skript nur zuweisen, wird standardmäßig [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) das Handle des HoloLens 1. Generation angezeigt. Um HoloLens 2 Stilhandles verwenden zu können, müssen Sie geeignete Handlepräfabs und Materialien zuweisen.

![Bounds Control Handle Styles 2 (Steuerelementhandlestile für Begrenzungen 2)](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

Im Folgenden finden Sie die Prefabs, Materialien und Skalierungswerte für die Steuerelementhandles HoloLens 2 Stilgrenzen. Sie finden dieses Beispiel in der `BoundsControlExamples` Szene.

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a>Handles (Setup für HoloLens 2 Format)

* **Handle Material**: BoundingBoxHandleWhite.mat
* **Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat
* **Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab
* **Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab
* **Größe des Skalierungshandle:** 0,016 (1,6 cm)
* **Scale Handle Collider Padding**: 0.016 (macht den ziehbaren Collider etwas größer als das Handlevisual)
* **Rotationshandle prefab:** MRTK_BoundingBox_RotateHandle.prefab
* **Rotationshandlegröße:** 0,016
* **Rotation Handle Collider Padding**: 0.016 (macht den ziehbaren Collider etwas größer als das Handlevisual)

## <a name="transformation-changes-with-object-manipulator"></a>Transformationsänderungen mit Objektmanipulator

Ein Begrenzungssteuerelement kann in Kombination mit verwendet [`ObjectManipulator.cs`](object-manipulator.md) werden, um bestimmte Manipulationstypen (z. B. Verschieben des -Objekts), ohne Handles zu verwenden. Der Manipulationshandler unterstützt sowohl ein- als auch zweihändige Interaktionen. [Die Handnachverfolgung](../input/hand-tracking.md) kann verwendet werden, um mit einem Objekt aus nächster Nähe zu interagieren.

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

Damit sich die Begrenzungssteuerelementränder beim Verschieben mit der fernen Interaktion des Steuerelements auf die gleiche Weise [`ObjectManipulator`](object-manipulator.md) verhalten, wird empfohlen, die Ereignisse für On Manipulation Started On Manipulation Ended *(Bei* Manipulation gestartet  /  *bei Manipulation beendet)* `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` mit zu verbinden, wie im obigen Screenshot gezeigt.

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>Hinzufügen und Konfigurieren eines Begrenzungssteuerelements mithilfe von Unity Inspector

1. Hinzufügen von Box Collider zu einem Objekt
2. Zuweisen `BoundsControl` eines Skripts zu einem Objekt
3. Konfigurieren von Optionen, z. B. Aktivierungsmethoden (siehe Abschnitt [Inspektoreigenschaften](#inspector-properties) unten)
4. (Optional) Zuweisen von Prefabs und Materialien für ein HoloLens 2 Stilbegrenzungssteuerelement (siehe Abschnitt [Handlestile](#handle-styles) weiter unten)

> [!NOTE]
> Verwenden Sie das Feld *Zielobjekt* und *Begrenzungsüberschreibung* im Inspektor, um ein bestimmtes Objekt und einen Collider im Objekt mit mehreren untergeordneten Komponenten zuzuweisen.

![Begrenzungssteuerelement](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>Hinzufügen und Konfigurieren eines Begrenzungssteuerelements im Code

1. Instanziieren des Cubes GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Zuweisen `BoundsControl` eines Skripts zu einem Objekt mit Collider mit addComponent<>()

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. Konfigurieren Sie Optionen entweder direkt auf dem Steuerelement oder über eine der skriptfähigen Konfigurationen (siehe Abschnitt [Inspektoreigenschaften](#inspector-properties) und [Konfigurationen](#configuration-objects) weiter unten).

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. (Optional) Weisen Sie Prefabs und Materialien für ein HoloLens 2 Stilbegrenzungssteuerelement zu. Hierfür sind weiterhin Zuweisungen über den Inspektor erforderlich, da die Materialien und Prefabs dynamisch geladen werden sollten.

> [!NOTE]
> Die Verwendung des Ordners "Resources" von Unity oder [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) zum dynamischen Laden von Shadern wird nicht empfohlen, da Shader-Permutationen zur Laufzeit möglicherweise fehlen.

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>Beispiel: Festlegen der minimalen, maximalen Begrenzungen für die Steuerung der Skalierung mit MinMaxScaleConstraint

Um die minimale und maximale Skalierung festzulegen, fügen Sie eine [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) an Das Steuerelement an. Da das Bounds-Steuerelement den Einschränkungs-Manager automatisch anfügt und aktiviert, wird MinMaxScaleConstraint automatisch auf die Transformationsänderungen angewendet, sobald sie angefügt und konfiguriert wurde.

Sie können auch MinMaxScaleConstraint verwenden, um die minimale und maximale Skalierung für [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) festzulegen.

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a>Beispiel: Hinzufügen eines Begrenzungssteuerelements um ein Spielobjekt

Um ein Begrenzungssteuerelement um ein Objekt hinzuzufügen, fügen Sie ihm einfach eine `BoundsControl` Komponente hinzu:

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>Migrieren von Bounding Box

Vorhandene Prefabs und Instanzen, die [begrenzungsfeld](bounding-box.md) verwenden, können über das [Migrationsfenster,](../tools/migration-window.md) das Teil des MRTK-Toolspakets ist, auf das neue Begrenzungssteuerelement aktualisiert werden.

Für das Upgrade einzelner Instanzen des Begrenzungsfelds gibt es auch eine Migrationsoption innerhalb des Eigenschafteninspektors der Komponente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>Siehe auch

* [Objektmanipulator](object-manipulator.md)
* [Einschränkungs-Manager](constraint-manager.md)
* [Migrationszeitfenster](../tools/migration-window.md)
* [Elastics-System (experimentell)](../experimental/elastic-system.md)
