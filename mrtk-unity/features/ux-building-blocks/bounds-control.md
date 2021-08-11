---
title: Begrenzungssteuerelement
description: Übersicht über die Begrenzungssteuerung in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Bounds Control,
ms.openlocfilehash: 3abefd142753c34c9126d71cde77ebca0b40f1f9b7a81b5815777b9e938e172a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217183"
---
# <a name="bounds-control"></a>Begrenzungssteuerelement

![Begrenzungssteuerelement](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl ist* die neue Komponente für manipulationsverhalten, die zuvor in *BoundingBox gefunden wurde.* Die Begrenzungssteuerung führt eine Reihe von Verbesserungen und Vereinfachungen beim Setup durch und fügt neue Features hinzu. Diese Komponente ist ein Ersatz für das Begrenzungsfeld, das veraltet ist.

Das [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) Skript stellt grundlegende Funktionen zum Transformieren von Objekten in Mixed Reality zur Verfügung. Ein Steuerelement für Begrenzungen zeigt ein Feld um das Hologramm an, um anzugeben, dass mit ihm interagiert werden kann. Ziehpunkte an den Ecken und Kanten des Felds ermöglichen das Skalieren, Drehen oder Übersetzen des Objekts. Das Steuerelement bounds reagiert auch auf Benutzereingaben. Auf HoloLens 2 reagiert beispielsweise das Steuerelement bounds auf die Fingernähe und stellt visuelles Feedback zur Verfügung, um den Abstand zum Objekt zu erkennen. Alle Interaktionen und Visuals können einfach angepasst werden.

## <a name="example-scene"></a>Beispielszene

Beispiele für Begrenzungssteuerungskonfigurationen finden Sie in der `BoundsControlExamples` Szene.

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>Inspektoreigenschaften

### <a name="target-object"></a>Zielobjekt

Diese Eigenschaft gibt an, welches Objekt durch die Bearbeitung der Begrenzungssteuerung transformiert wird. Wenn kein Objekt festgelegt ist, wird standardmäßig das Besitzerobjekt verwendet.

### <a name="activation-behavior"></a>Aktivierungsverhalten

Es gibt mehrere Optionen zum Aktivieren der Begrenzungssteuerungsschnittstelle.

* *Beim Start aktivieren:* Das Steuerelement "Begrenzungen" wird sichtbar, sobald die Szene gestartet wird.
* *Durch Näherung aktivieren:* Das Steuerelement "Begrenzungen" wird sichtbar, wenn sich eine artikulierte Hand in der Nähe des Objekts befindet.
* *Durch Zeiger aktivieren:* Das Steuerelement "Begrenzungen" wird sichtbar, wenn es von einem Handstrahlzeiger als Ziel angezeigt wird.
* *Aktivieren durch Näherung* und Zeiger: Das Steuerelement "Begrenzungen" wird sichtbar, wenn es von einem Handstrahlzeiger oder einer artikulierten Hand in der Nähe des Objekts als Ziel verwendet wird.
* *Manuell aktivieren:* Das Steuerelement "Begrenzungen" wird nicht automatisch sichtbar. Sie können sie manuell über ein Skript aktivieren, indem Sie auf die boundsControl.Active-Eigenschaft zugreifen.

### <a name="bounds-override"></a>Begrenzungen überschreiben

Legt einen Feld-Collider aus dem -Objekt für die Berechnung von Begrenzungen fest.

### <a name="box-padding"></a>Feldauf padding

Fügt den Collider-Begrenzungen, die zum Berechnen der Werte des Steuerelements verwendet werden, eine Aufleerung hinzu. Dies wirkt sich nicht nur auf die Interaktion aus, sondern auch auf die visuellen Elemente.

### <a name="flatten-axis"></a>Flache Achse

Gibt an, ob das Steuerelement in einer der Achsen flach ist, wodurch es zweidimensional ist und keine Bearbeitung entlang dieser Achse zu sehen ist. Dieses Feature kann für schlanke Objekte wie Slates verwendet werden.
Wenn flatten axis auf *Flatten Auto* festgelegt ist, wählt das Skript automatisch die Achse mit dem kleinsten Umfang als flache Achse aus.

### <a name="smoothing"></a>Glättung

Der Glättungsabschnitt ermöglicht das Konfigurieren des Glättungsverhaltens zum Skalieren und Drehen des Steuerelements.

### <a name="visuals"></a>Visuals

Die Darstellung des Steuerelements für Begrenzungen kann durch Ändern einer der entsprechenden Visualkonfigurationen konfiguriert werden.
Visuelle Konfigurationen sind verknüpfte oder inline skriptfähige Objekte und werden im Abschnitt konfigurationsobjekt [ausführlicher beschrieben.](#configuration-objects)

## <a name="configuration-objects"></a>Konfigurationsobjekte

Das Steuerelement enthält eine Reihe von Konfigurationsobjekten, die als skriptfähige Objekte gespeichert und von verschiedenen Instanzen oder Prefabs gemeinsam genutzt werden können. Konfigurationen können entweder als einzelne skriptfähige Assetdateien oder als geschachtelte skriptfähige Objekte innerhalb von Prefabs freigegeben und verknüpft werden. Weitere Konfigurationen können auch direkt auf der Instanz definiert werden, ohne eine Verknüpfung mit einem externen oder geschachtelten skriptbaren Asset zu erstellen.

Der Steuerelementinspektor für Begrenzungen gibt an, ob eine Konfiguration als Teil der aktuellen Instanz freigegeben oder inline ist, indem eine Meldung im Eigenschafteninspektor angezeigt wird. Außerdem können freigegebene Instanzen nicht direkt im Eigenschaftenfenster des Steuerelements bounds bearbeitet werden. Stattdessen muss das Objekt, mit dem sie eine Verknüpfung erstellen, direkt geändert werden, um versehentliche Änderungen an freigegebenen Konfigurationen zu vermeiden.

Das Steuerelement "Begrenzungen" bietet derzeit Konfigurationsobjektoptionen für die folgenden Features:

* Ziehpunkte
  * [Skalierungshandles](#scale-handles-configuration)
  * [Drehungshandles](#rotation-handles-configuration)
  * [Übersetzungshandles](#translation-handles-configuration)
* [Links/Wireframe](#links-configuration-wireframe)
* [Feldanzeige](#box-configuration)
* [Näherungseffekt](#proximity-effect-configuration)

### <a name="box-configuration"></a>Box-Konfiguration

Die Feldkonfiguration ist für das Rendern eines Volltonfelds mit Begrenzungen zuständig, die über die Collidergröße und die Feldaufleerung definiert sind. Die folgenden Eigenschaften können eingerichtet werden:

* **Feldmaterial:** Definiert das Material, das auf das gerenderte Feld angewendet wird, wenn keine Interaktion stattfindet. Ein Feld wird nur gerendert, wenn dieses Material festgelegt ist.
* **Schachtelungsmaterial:** Material für den Kasten, wenn der Benutzer mit dem Steuerelement interagiert, indem er über nah oder ferne Interaktion greift.
* **Achsenanzeigeskala abflachen:** Eine Skala, die auf die Feldanzeige angewendet wird, wenn eine der Achsen [flach ist.](#flatten-axis)

### <a name="scale-handles-configuration"></a>Konfiguration von Skalierungshandles

Mit diesem Eigenschaften-Drawer können Sie das Verhalten und die Visualisierung von Skalierungshandles der Begrenzungssteuerung ändern.

* **Material verarbeiten:** Material, das auf die Handles angewendet wird.
* **Handle grabbed material**:material applied to the grabbed handle.
* **Handle prefab:** Optionales Prefab für das Skalierungshand handle. Wenn nicht festgelegt ist, verwendet MRTK standardmäßig einen Cube.
* **Handlegröße:** Größe des Skalierungshandpunkts.
* **Colliderauf padding**: Padding to add to the handle collider.
* **Zeichnen Sie tether beim Bearbeiten** von : Wenn aktiv ist, wird eine tether-Linie vom Anfang der Interaktion bis zur aktuellen Hand- oder Zeigerposition ge ziehen.
* **Handles ignorieren Collider:** Wenn ein Collider hier verknüpft wird, ignorieren Handles alle Kollisionen mit diesem Collider.
* **Handle slate prefab**: Prefab, das für das Handle verwendet werden soll, wenn das Steuerelement flach ist.
* **Skalierungshandles anzeigen:** Steuert die Sichtbarkeit des Handles.
* **Skalierungsverhalten:** Kann auf einheitliche oder nicht einheitliche Skalierung festgelegt werden.

### <a name="rotation-handles-configuration"></a>Konfiguration von Rotationshandles

Diese Konfiguration definiert das Rotationshand handle-Verhalten.

* **Material verarbeiten:** Material, das auf die Handles angewendet wird.
* **Handle grabbed material**:material applied to the grabbed handle.
* **Handle prefab:** Optionales Prefab für das Handle. Wenn nicht festgelegt ist, verwendet MRTK standardmäßig eine Kugel.
* **Handlegröße:** Größe des Handles.
* **Colliderauf padding**: Padding to add to the handle collider.
* **Zeichnen Sie tether beim Bearbeiten** von : Wenn aktiv ist, wird eine tether-Linie vom Anfang der Interaktion bis zur aktuellen Hand- oder Zeigerposition ge ziehen.
* **Handles ignorieren Collider:** Wenn ein Collider hier verknüpft wird, ignorieren Handles alle Kollisionen mit diesem Collider.
* **Handle Prefab-Collidertyp:** Collidertyp, der mit dem erstellten Handle verwendet werden soll.
* **Handle für X anzeigen:** Steuert die Sichtbarkeit des Handles für die X-Achse.
* **Handle für Y anzeigen:** Steuert die Sichtbarkeit des Handles für die Y-Achse.
* **Handle für Z anzeigen:** Steuert die Sichtbarkeit des Handles für die Z-Achse.

### <a name="translation-handles-configuration"></a>Konfiguration von Übersetzungshandles

Ermöglicht das Aktivieren und Konfigurieren von Übersetzungshandles für die Begrenzungssteuerung. Beachten Sie, dass Übersetzungshandles standardmäßig deaktiviert sind.

* **Material verarbeiten:** Material, das auf die Handles angewendet wird.
* **Handle grabbed material**:material applied to the grabbed handle.
* **Handle prefab:** Optionales Prefab für das Handle. Wenn nicht festgelegt ist, verwendet MRTK standardmäßig eine Kugel.
* **Handlegröße:** Größe des Handles.
* **Colliderauf padding**: Padding to add to the handle collider.
* **Zeichnen Sie tether beim Bearbeiten** von : Wenn aktiv ist, wird eine tether-Linie vom Anfang der Interaktion bis zur aktuellen Hand- oder Zeigerposition ge ziehen.
* **Handles ignorieren Collider:** Wenn ein Collider hier verknüpft wird, ignorieren Handles alle Kollisionen mit diesem Collider.
* **Handle Prefab-Collidertyp:** Collidertyp, der mit dem erstellten Handle verwendet werden soll.
* **Handle für X anzeigen:** Steuert die Sichtbarkeit des Handles für die X-Achse.
* **Handle für Y anzeigen:** Steuert die Sichtbarkeit des Handles für die Y-Achse.
* **Handle für Z anzeigen:** Steuert die Sichtbarkeit des Handles für die Z-Achse.

### <a name="links-configuration-wireframe"></a>Linkskonfiguration (Wireframe)

Die Linkkonfiguration aktiviert das Wireframe-Feature der Begrenzungssteuerung. Die folgenden Eigenschaften können konfiguriert werden:

* **Drahtmodellmaterial:** Das Material, das auf das Drahtmodellgitter angewendet wird.
* **Wireframe edge radius**:the thickness of the wireframe.
* **Wireframe-Form:** Die Form des Drahtmodells kann kubisch oder zylindrisch sein.
* **Wireframe anzeigen:** Steuert die Sichtbarkeit des Drahtmodells.

### <a name="proximity-effect-configuration"></a>Näherungseffektkonfiguration

Zeigen Sie die Ziehpunkte mit Animation basierend auf dem Abstand zu den Händen an, und blenden Sie sie aus. Es verfügt über eine animation zur zweistufigen Skalierung. Die Standardwerte werden auf HoloLens 2 festgelegt.

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **Näherungseffekt aktiv:** Aktivierung des näherungsbasierten Handles aktivieren
* **Mittlere Objektnähe:** Abstand für die Skalierung im ersten Schritt
* **Objektnähe schließen:** Entfernung für die Skalierung im zweiten Schritt
* **Fernskala:** Der Standardskalierenwert des Handle-Assets, wenn die Hände sich nicht im Bereich der Steuerungsinteraktion der Begrenzungen befinden (Der Abstand wird oben durch "Mittlere Nähe behandeln" definiert). Verwenden Sie 0, um handle standardmäßig auszublenden.)
* **Mittelmaßstab:** Skalierungswert des Handle-Assets, wenn sich die Hände innerhalb des Bereichs der Begrenzungssteuerungsinteraktion befinden (über "Handle Close Proximity" definierter Abstand). Verwenden Von 1 zum Anzeigen der normalen Größe)
* Close Scale :Scale value of the handle asset when the hands are within range of the grab interaction (Close **Scale:** Skalierungswert des Handle-Assets, wenn sich die Hände innerhalb des Bereichs der Greifinteraktion befinden (Der Abstand wird oben durch "Handle Close Proximity" definiert). Verwenden Von 1.x zum Anzeigen einer größeren Größe)
* **Far Grow Rate**:Rate a proximity scaled object scales scales when the hand moves from medium to far proximity.
* **Mittlere Verkalkungsrate:** Bewerten Sie die Skalierung eines näher skalierten Objekts, wenn die Hand von der mittleren in die nahe Nähe bewegt wird.
* **Close Grow Rate :Rate** a proximity scaled object scales when the hand moves from close proximity to object center.

## <a name="constraint-system"></a>Einschränkungssystem

Das Steuerelement "Begrenzungen" unterstützt die Verwendung des [Einschränkungs-Managers](constraint-manager.md) zum Einschränken oder Ändern des Übersetzungs-, Drehungs- oder Skalierungsverhaltens bei Verwendung von Begrenzungssteuerungshandles.

Der Eigenschafteninspektor zeigt alle verfügbaren Einschränkungs-Manager an, die an dasselbe Spielobjekt angefügt sind, in einer Dropdownliste mit einer Option zum Scrollen und Hervorheben des ausgewählten Einschränkungs-Managers.

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>Ereignisse

Das Bounds-Steuerelement stellt die folgenden Ereignisse zur Verfügung. In diesem Beispiel werden diese Ereignisse verwendet, um Audiofeedback wieder zu geben.

* **Rotate Started**(Gestartet drehen): Wird ausgelöst, wenn die Drehung gestartet wird.
* **Rotate Stopped**: Wird ausgelöst, wenn die Drehung beendet wird.
* **Gestartete Skalierung:** Wird beim Starten der Skalierung gestartet.
* **Skalierung beendet:** Wird beim Ende der Skalierung aus.
* **Translate Started**: Wird beim Starten der Übersetzung gestartet.
* **Translate Stopped**: Wird beim Ende der Übersetzung aus.

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>Elastische Datenbanken (experimentell)

Elastische Datenbanken können beim Bearbeiten von Objekten über die Begrenzungssteuerung verwendet werden. Beachten Sie, [dass sich das Elastiksystem](../experimental/elastic-system.md) noch im experimentellen Zustand befindet. Um elastische Datenbanken zu aktivieren, verknüpfen Sie entweder eine vorhandene Elastics Manager-Komponente, oder erstellen und verknüpfen Sie über die Schaltfläche einen neuen `Add Elastics Manager` Elastik-Manager.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>Behandeln von Stilen

Wenn Sie das Skript nur zuweisen, wird standardmäßig das Handle des Stils HoloLens [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 1. Generation angezeigt. Um die HoloLens 2 verwenden zu können, müssen Sie geeignete Handle-Prefabs und -Materialien zuweisen.

![Begrenzungssteuerpunkt-Handlestile 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

Im Folgenden finden Sie die Prefabs, Materialien und skalierungswerte für die HoloLens 2-Steuerelementhandles. Sie finden dieses Beispiel in der `BoundsControlExamples` Szene.

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

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

## <a name="transformation-changes-with-object-manipulator"></a>Transformationsänderungen mit Objektmanipulator

Ein Bounds-Steuerelement kann in Kombination mit verwendet [`ObjectManipulator.cs`](object-manipulator.md) werden, um bestimmte Manipulationstypen zu ermöglichen (z. B. Verschieben des Objekts) ohne Verwendung von Handles. Der Manipulationshandler unterstützt sowohl ein- als auch zweihändige Interaktionen. [Handtracking](../input/hand-tracking.md) kann verwendet werden, um mit einem Objekt aus der Nähe zu interagieren.

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

Damit sich die Begrenzungssteuerränder beim Verschieben mithilfe der Ferninteraktion von genauso verhalten, wird empfohlen, die Ereignisse für On Manipulation Started On Manipulation Ended mit zu verbinden, wie im obigen Screenshot [`ObjectManipulator`](object-manipulator.md)   /   `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` gezeigt.

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>Hinzufügen und Konfigurieren eines Steuerelements für Begrenzungen mithilfe des Unity-Inspektors

1. Hinzufügen von Box Collider zu einem Objekt
2. Zuweisen `BoundsControl` eines Skripts zu einem Objekt
3. Konfigurieren von Optionen, z. B. Aktivierungsmethoden (siehe [Abschnitt Inspektoreigenschaften](#inspector-properties) weiter unten)
4. (Optional) Zuweisen von Prefabs und Materialien für ein HoloLens 2-Steuerelement für Stile (siehe Abschnitt ["Handlestile"](#handle-styles) weiter unten)

> [!NOTE]
> Verwenden *Sie das Feld Target Object* and Bounds Override (Zielobjekt und *Begrenzungsüberschreibung)* im Inspektor, um bestimmte Objekte und Collider im Objekt mit mehreren untergeordneten Komponenten zu zuweisen.

![Begrenzungssteuerelement](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>Hinzufügen und Konfigurieren eines Steuerelements für Begrenzungen im Code

1. Instanziieren des Cubes "GameObject"

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Zuweisen `BoundsControl` eines Skripts zu einem Objekt mit Collider unter Verwendung von AddComponent<>()

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. Konfigurieren Sie Optionen entweder direkt im Steuerelement oder über eine der skriptierbaren Konfigurationen (siehe [Abschnitt Inspektoreigenschaften](#inspector-properties) und [Konfigurationen](#configuration-objects) weiter unten).

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. (Optional) Weisen Sie Prefabs und Materialien für ein HoloLens 2-Steuerelement zu. Dies erfordert weiterhin Zuweisungen über den Inspektor, da die Materialien und Prefabs dynamisch geladen werden sollten.

> [!NOTE]
> Die Verwendung des Ordners "Resources" von Unity oder [shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) zum dynamischen Laden von Shadern wird nicht empfohlen, da Shader-Permutationen zur Laufzeit möglicherweise fehlen.

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

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>Beispiel: Festlegen der minimalen und maximalen Begrenzungssteuerungsskala mit MinMaxScaleConstraint

Um die minimale und maximale Skalierung zu festlegen, fügen Sie ein [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) an Das Steuerelement an. Da die Begrenzungssteuerung den Einschränkungs-Manager automatisch anfügen und aktiviert, wird MinMaxScaleConstraint automatisch auf die Transformationsänderungen angewendet, sobald sie angefügt und konfiguriert wurden.

Sie können auch MinMaxScaleConstraint verwenden, um die minimale und maximale Skalierung für [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) festlegen.

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a>Beispiel: Hinzufügen einer Begrenzungssteuerung um ein Spielobjekt

Um ein Begrenzungssteuerelement um ein Objekt hinzuzufügen, fügen Sie ihm `BoundsControl` einfach eine Komponente hinzu:

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>Migrieren vom Begrenzungsfeld

Vorhandene Prefabs und [](bounding-box.md) Instanzen mit begrenzungsgebundenem Feld können über [](../tools/migration-window.md) das Migrationsfenster, das Teil des MRTK-Toolspakets ist, auf das neue Begrenzungssteuerfeld aktualisiert werden.

Für das Upgrade einzelner Instanzen des Begrenzungsfelds gibt es auch eine Migrationsoption innerhalb des Eigenschafteninspektors der Komponente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>Siehe auch

* [Objektmanipulator](object-manipulator.md)
* [Einschränkungs-Manager](constraint-manager.md)
* [Migrationszeitfenster](../tools/migration-window.md)
* [Elastisches System (experimentell)](../experimental/elastic-system.md)
