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
# <a name="bounding-box"></a><span data-ttu-id="354d3-104">Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="354d3-104">Bounding box</span></span>

![Begrenzungsrahmen](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> <span data-ttu-id="354d3-106">Begrenzungsfeld ist veraltet und wird durch das [Nachfolger-Begrenzungssteuerfeld ersetzt.](bounds-control.md)</span><span class="sxs-lookup"><span data-stu-id="354d3-106">Bounding box is deprecated and replaced by its successor [bounds control](bounds-control.md).</span></span> <span data-ttu-id="354d3-107">Verwenden [Sie eine der Migrationsoptionen, um](#migrating-to-bounds-control) vorhandene Spielobjekte zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="354d3-107">Use [one of the migration options](#migrating-to-bounds-control) to upgrade existing game objects.</span></span>

<span data-ttu-id="354d3-108">Das [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) Skript stellt grundlegende Funktionen zum Transformieren von Objekten in Mixed Reality zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="354d3-108">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="354d3-109">Ein Begrenzungsfeld zeigt einen Würfel um das Hologramm an, um anzugeben, dass mit ihm interagiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="354d3-109">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="354d3-110">Handles an den Ecken und Kanten des Cubes ermöglichen das Skalieren oder Drehen des Objekts.</span><span class="sxs-lookup"><span data-stu-id="354d3-110">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="354d3-111">Das Begrenzungsfeld reagiert auch auf Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="354d3-111">The bounding box also reacts to user input.</span></span> <span data-ttu-id="354d3-112">Auf HoloLens 2 reagiert der Begrenzungsfeld beispielsweise auf die Fingernähe und gibt visuelles Feedback, um den Abstand zum Objekt zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="354d3-112">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="354d3-113">Alle Interaktionen und Visuals können einfach angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="354d3-113">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="354d3-114">Weitere Informationen finden Sie unter [Begrenzungsfeld und App-Leiste](/windows/mixed-reality/app-bar-and-bounding-box) im Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="354d3-114">For more information, see [Bounding box and App bar](/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="354d3-115">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="354d3-115">Example scene</span></span>

<span data-ttu-id="354d3-116">Beispiele für Begrenzungsfeldkonfigurationen finden Sie in der `BoundingBoxExamples` Szene.</span><span class="sxs-lookup"><span data-stu-id="354d3-116">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="354d3-117">Hinzufügen und Konfigurieren eines Begrenzungsfelds mit dem Unity-Inspektor</span><span class="sxs-lookup"><span data-stu-id="354d3-117">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="354d3-118">Hinzufügen von Box Collider zu einem Objekt</span><span class="sxs-lookup"><span data-stu-id="354d3-118">Add Box Collider to an object</span></span>
2. <span data-ttu-id="354d3-119">Zuweisen `BoundingBox` eines Skripts zu einem Objekt</span><span class="sxs-lookup"><span data-stu-id="354d3-119">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="354d3-120">Konfigurieren von Optionen, z. B. Aktivierungsmethoden (siehe [Abschnitt Inspektoreigenschaften](#inspector-properties) weiter unten)</span><span class="sxs-lookup"><span data-stu-id="354d3-120">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="354d3-121">(Optional) Zuweisen von Prefabs und Materialien für ein HoloLens 2 Umrandungsfeld (siehe Abschnitt ["Handlestile"](#handle-styles) weiter unten)</span><span class="sxs-lookup"><span data-stu-id="354d3-121">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="354d3-122">Verwenden *Sie das Feld Target Object* and Bounds Override (Zielobjekt und *Begrenzungsüberschreibung)* im Inspektor, um bestimmte Objekte und Collider im Objekt mit mehreren untergeordneten Komponenten zu zuweisen.</span><span class="sxs-lookup"><span data-stu-id="354d3-122">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Begrenzungsfeld 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="354d3-124">Hinzufügen und Konfigurieren eines Begrenzungsfelds im Code</span><span class="sxs-lookup"><span data-stu-id="354d3-124">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="354d3-125">Instanziieren des Cubes "GameObject"</span><span class="sxs-lookup"><span data-stu-id="354d3-125">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="354d3-126">Zuweisen `BoundingBox` eines Skripts zu einem Objekt mit Collider mithilfe von AddComponent<>()</span><span class="sxs-lookup"><span data-stu-id="354d3-126">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="354d3-127">Konfigurieren von Optionen (siehe [Abschnitt Inspektoreigenschaften](#inspector-properties) weiter unten)</span><span class="sxs-lookup"><span data-stu-id="354d3-127">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="354d3-128">(Optional) Zuweisen von Prefabs und Materialien für ein HoloLens 2 Umrandungsfeld.</span><span class="sxs-lookup"><span data-stu-id="354d3-128">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="354d3-129">Dies erfordert weiterhin Zuweisungen über den Inspektor, da die Materialien und Prefabs dynamisch geladen werden sollten.</span><span class="sxs-lookup"><span data-stu-id="354d3-129">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="354d3-130">Die Verwendung des Ordners "Resources" von Unity oder [shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) zum dynamischen Laden von Shadern wird nicht empfohlen, da Shader-Permutationen zur Laufzeit möglicherweise fehlen.</span><span class="sxs-lookup"><span data-stu-id="354d3-130">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="354d3-131">Beispiel: Festlegen der minimalen, maximalen Begrenzungsfeldskala mit MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="354d3-131">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="354d3-132">Verwenden Sie zum Festlegen der minimalen und maximalen Skalierung [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) den .</span><span class="sxs-lookup"><span data-stu-id="354d3-132">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="354d3-133">Sie können auch MinMaxScaleConstraint verwenden, um die minimale und maximale Skalierung für [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) festlegen.</span><span class="sxs-lookup"><span data-stu-id="354d3-133">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="354d3-134">Beispiel: Hinzufügen eines Begrenzungsfelds um ein Spielobjekt</span><span class="sxs-lookup"><span data-stu-id="354d3-134">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="354d3-135">Um ein Begrenzungsfeld um ein Objekt hinzuzufügen, fügen Sie ihm einfach `BoundingBox` eine Komponente hinzu:</span><span class="sxs-lookup"><span data-stu-id="354d3-135">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="354d3-136">Inspektoreigenschaften</span><span class="sxs-lookup"><span data-stu-id="354d3-136">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="354d3-137">Zielobjekt</span><span class="sxs-lookup"><span data-stu-id="354d3-137">Target object</span></span>

<span data-ttu-id="354d3-138">Diese Eigenschaft gibt an, welches Objekt durch die Bearbeitung des Begrenzungsfelds transformiert wird.</span><span class="sxs-lookup"><span data-stu-id="354d3-138">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="354d3-139">Wenn kein Objekt festgelegt ist, wird das Begrenzungsfeld standardmäßig auf das Besitzerobjekt festgelegt.</span><span class="sxs-lookup"><span data-stu-id="354d3-139">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="354d3-140">Außerkraftsetzung von Begrenzungen</span><span class="sxs-lookup"><span data-stu-id="354d3-140">Bounds override</span></span>

<span data-ttu-id="354d3-141">Legt einen Feld-Collider aus dem -Objekt für die Berechnung von Begrenzungen fest.</span><span class="sxs-lookup"><span data-stu-id="354d3-141">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="354d3-142">Aktivierungsverhalten</span><span class="sxs-lookup"><span data-stu-id="354d3-142">Activation behavior</span></span>

<span data-ttu-id="354d3-143">Es gibt mehrere Optionen zum Aktivieren der Begrenzungsfeldschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="354d3-143">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="354d3-144">*Beim Start aktivieren:* Das Begrenzungsfeld wird angezeigt, sobald die Szene gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="354d3-144">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="354d3-145">*Durch Näherung aktivieren:* Das Begrenzungsfeld wird sichtbar, wenn sich eine artikulierte Hand in der Nähe des Objekts befindet.</span><span class="sxs-lookup"><span data-stu-id="354d3-145">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="354d3-146">*Durch Zeiger aktivieren:* Das Begrenzungsfeld wird sichtbar, wenn es von einem Handstrahlzeiger als Ziel angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="354d3-146">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="354d3-147">*Manuell aktivieren:* Begrenzungsfeld wird nicht automatisch angezeigt.</span><span class="sxs-lookup"><span data-stu-id="354d3-147">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="354d3-148">Sie können sie manuell über ein Skript aktivieren, indem Sie auf die boundingBox.Active-Eigenschaft zugreifen.</span><span class="sxs-lookup"><span data-stu-id="354d3-148">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="354d3-149">Minimum skalieren</span><span class="sxs-lookup"><span data-stu-id="354d3-149">Scale minimum</span></span>

<span data-ttu-id="354d3-150">Die zulässige Mindestskala.</span><span class="sxs-lookup"><span data-stu-id="354d3-150">The minimum allowed scale.</span></span> <span data-ttu-id="354d3-151">Diese Eigenschaft ist veraltet und es ist vorzuziehen, ein Skript [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="354d3-151">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="354d3-152">Wenn dieses Skript hinzugefügt wird, wird die Mindestskala daraus und nicht aus dem Begrenzungsfeld übernommen.</span><span class="sxs-lookup"><span data-stu-id="354d3-152">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="354d3-153">Maximale Skalierung</span><span class="sxs-lookup"><span data-stu-id="354d3-153">Scale maximum</span></span>

<span data-ttu-id="354d3-154">Die maximal zulässige Skalierung.</span><span class="sxs-lookup"><span data-stu-id="354d3-154">The maximum allowed scale.</span></span> <span data-ttu-id="354d3-155">Diese Eigenschaft ist veraltet und es ist vorzuziehen, ein Skript [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="354d3-155">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="354d3-156">Wenn dieses Skript hinzugefügt wird, wird die maximale Skalierung aus ihm und nicht aus dem Begrenzungsfeld übernommen.</span><span class="sxs-lookup"><span data-stu-id="354d3-156">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="354d3-157">Feldanzeige</span><span class="sxs-lookup"><span data-stu-id="354d3-157">Box display</span></span>

<span data-ttu-id="354d3-158">Verschiedene Optionen für die Begrenzungsfeldvisualisierung.</span><span class="sxs-lookup"><span data-stu-id="354d3-158">Various bounding box visualization options.</span></span>

<span data-ttu-id="354d3-159">Wenn Flatten Axis auf *Flatten Auto* festgelegt ist, wird die Bearbeitung entlang der Achse mit dem kleinsten Umfang vom Skript nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="354d3-159">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="354d3-160">Dies führt zu einem 2D-Begrenzungsfeld, das normalerweise für schlanke Objekte verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="354d3-160">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="354d3-161">Ziehpunkte</span><span class="sxs-lookup"><span data-stu-id="354d3-161">Handles</span></span>

<span data-ttu-id="354d3-162">Sie können das Material und das Prefab zuweisen, um den Handlestil zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="354d3-162">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="354d3-163">Wenn keine Handles zugewiesen sind, werden sie im Standardformat angezeigt.</span><span class="sxs-lookup"><span data-stu-id="354d3-163">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="354d3-164">Ereignisse</span><span class="sxs-lookup"><span data-stu-id="354d3-164">Events</span></span>

<span data-ttu-id="354d3-165">Das Begrenzungsfeld stellt die folgenden Ereignisse zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="354d3-165">Bounding box provides the following events.</span></span> <span data-ttu-id="354d3-166">In diesem Beispiel werden diese Ereignisse verwendet, um Audiofeedback wieder zu geben.</span><span class="sxs-lookup"><span data-stu-id="354d3-166">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="354d3-167">**Rotate Started**(Gestartet drehen): Wird ausgelöst, wenn die Drehung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="354d3-167">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="354d3-168">**Rotate Ended :Wird** ausgelöst, wenn die Drehung endet.</span><span class="sxs-lookup"><span data-stu-id="354d3-168">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="354d3-169">**Gestartete Skalierung:** Wird beim Starten der Skalierung gestartet.</span><span class="sxs-lookup"><span data-stu-id="354d3-169">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="354d3-170">**Skalierung beendet:** Wird beim Ende der Skalierung aus.</span><span class="sxs-lookup"><span data-stu-id="354d3-170">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a><span data-ttu-id="354d3-171">Behandeln von Stilen</span><span class="sxs-lookup"><span data-stu-id="354d3-171">Handle styles</span></span>

<span data-ttu-id="354d3-172">Wenn Sie das Skript nur zuweisen, wird standardmäßig das Handle des Stils HoloLens [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) 1. Generation angezeigt.</span><span class="sxs-lookup"><span data-stu-id="354d3-172">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="354d3-173">Um die HoloLens 2 verwenden zu können, müssen Sie geeignete Handle-Prefabs und -Materialien zuweisen.</span><span class="sxs-lookup"><span data-stu-id="354d3-173">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Begrenzungsfeld-Handlestile](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="354d3-175">Im Folgenden finden Sie die Prefabs, Materialien und skalierungswerte für die HoloLens 2 Umrandungsfeldhandles.</span><span class="sxs-lookup"><span data-stu-id="354d3-175">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="354d3-176">Sie finden dieses Beispiel in der `BoundingBoxExamples` Szene.</span><span class="sxs-lookup"><span data-stu-id="354d3-176">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="354d3-177">Handles (Setup für HoloLens 2 Format)</span><span class="sxs-lookup"><span data-stu-id="354d3-177">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="354d3-178">**Handle Material**: BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="354d3-178">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="354d3-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="354d3-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="354d3-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="354d3-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="354d3-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="354d3-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="354d3-182">**Größe des Skalierungshandpunkts:** 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="354d3-182">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="354d3-183">**Scale Handle Collider Padding**: 0.016 (macht den ziehbaren Collider etwas größer als das Handlevisual)</span><span class="sxs-lookup"><span data-stu-id="354d3-183">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="354d3-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="354d3-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="354d3-185">**Rotationshandpunktgröße:** 0,016</span><span class="sxs-lookup"><span data-stu-id="354d3-185">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="354d3-186">**Rotation Handle Collider Padding**: 0.016 (macht den ziehbaren Collider etwas größer als das Handlevisual)</span><span class="sxs-lookup"><span data-stu-id="354d3-186">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="354d3-187">Näherung (Setup für HoloLens 2 Format)</span><span class="sxs-lookup"><span data-stu-id="354d3-187">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="354d3-188">Zeigen Sie die Ziehpunkte mit Animation basierend auf dem Abstand zu den Händen an, und blenden Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="354d3-188">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="354d3-189">Es verfügt über eine animation zur zweistufigen Skalierung.</span><span class="sxs-lookup"><span data-stu-id="354d3-189">It has two-step scaling animation.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* <span data-ttu-id="354d3-190">**Näherungseffekt aktiv:** Aktivierung des näherungsbasierten Handles aktivieren</span><span class="sxs-lookup"><span data-stu-id="354d3-190">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="354d3-191">**Mittlere Nähe behandeln:** Entfernung für die Skalierung im ersten Schritt</span><span class="sxs-lookup"><span data-stu-id="354d3-191">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="354d3-192">**Handle Close Proximity**:Distance for the 2nd step scaling</span><span class="sxs-lookup"><span data-stu-id="354d3-192">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="354d3-193">**Fernskala:** Der Standardskalierungswert des Handle-Assets, wenn die Hände sich nicht im Bereich der Interaktion des Begrenzungsfelds befinden (Der Abstand wird oben durch "Mittlere Nähe behandeln" definiert).</span><span class="sxs-lookup"><span data-stu-id="354d3-193">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="354d3-194">Verwenden Sie 0, um handle standardmäßig auszublenden.)</span><span class="sxs-lookup"><span data-stu-id="354d3-194">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="354d3-195">**Mittelmaßstab:** Skalierungswert des Handle-Medienwerts, wenn sich die Hände innerhalb des Bereichs der Begrenzungsfeldinteraktion befinden (über "Handle Close Proximity" definierter Abstand).</span><span class="sxs-lookup"><span data-stu-id="354d3-195">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="354d3-196">Verwenden Von 1 zum Anzeigen der normalen Größe)</span><span class="sxs-lookup"><span data-stu-id="354d3-196">Use 1 to show normal size)</span></span>
* <span data-ttu-id="354d3-197">Close Scale :Scale value of the handle asset when the hands are within range of the grab interaction (Close **Scale:** Skalierungswert des Handle-Assets, wenn sich die Hände innerhalb des Bereichs der Greifinteraktion befinden (Der Abstand wird oben durch "Handle Close Proximity" definiert).</span><span class="sxs-lookup"><span data-stu-id="354d3-197">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="354d3-198">Verwenden Von 1.x zum Anzeigen einer größeren Größe)</span><span class="sxs-lookup"><span data-stu-id="354d3-198">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="354d3-199">Bewegbares Objekt mit Manipulationshandler</span><span class="sxs-lookup"><span data-stu-id="354d3-199">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="354d3-200">Ein Begrenzungsfeld kann mit kombiniert werden, um das Objekt mithilfe der [`ManipulationHandler.cs`](manipulation-handler.md) Ferninteraktion verschiebbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="354d3-200">A bounding box can be combined with [`ManipulationHandler.cs`](manipulation-handler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="354d3-201">Der Manipulationshandler unterstützt sowohl ein- als auch zweihändige Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="354d3-201">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="354d3-202">[Die Handverfolgung](../input/hand-tracking.md) kann verwendet werden, um mit einem Objekt in der Nähe zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="354d3-202">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

<span data-ttu-id="354d3-203">Damit sich die Begrenzungsfeldränder beim Verschieben mithilfe der Ferninteraktion von genauso verhalten, wird empfohlen, die Ereignisse für On Manipulation Started On Manipulation Ended (Beim Ende der Bearbeitung gestartet) mit zu verbinden, wie im obigen Screenshot [`ManipulationHandler`](manipulation-handler.md)   /   `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` gezeigt.</span><span class="sxs-lookup"><span data-stu-id="354d3-203">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](manipulation-handler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="migrating-to-bounds-control"></a><span data-ttu-id="354d3-204">Migrieren zur Begrenzungssteuerung</span><span class="sxs-lookup"><span data-stu-id="354d3-204">Migrating to bounds control</span></span>

<span data-ttu-id="354d3-205">Vorhandene Prefabs und [](bounding-box.md) Instanzen mit Begrenzungsfeld können über das Migrationsfenster, das Teil des MRTK-Toolspakets ist, auf das neue Begrenzungssteuerfeld aktualisiert werden. [](../tools/migration-window.md)</span><span class="sxs-lookup"><span data-stu-id="354d3-205">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="354d3-206">Für das Upgrade einzelner Instanzen des Begrenzungsfelds gibt es auch eine Migrationsoption innerhalb des Eigenschafteninspektors der Komponente.</span><span class="sxs-lookup"><span data-stu-id="354d3-206">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
