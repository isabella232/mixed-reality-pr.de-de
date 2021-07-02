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
# <a name="bounds-control"></a><span data-ttu-id="55559-104">Begrenzungssteuerelement</span><span class="sxs-lookup"><span data-stu-id="55559-104">Bounds control</span></span>

![Begrenzungssteuerelement](../images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="55559-106">*BoundsControl* ist die neue Komponente für das Manipulationsverhalten, die zuvor in *BoundingBox* gefunden wurde.</span><span class="sxs-lookup"><span data-stu-id="55559-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="55559-107">Das Begrenzungssteuerelement führt eine Reihe von Verbesserungen und Vereinfachungen beim Setup durch und fügt neue Features hinzu.</span><span class="sxs-lookup"><span data-stu-id="55559-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="55559-108">Diese Komponente ist ein Ersatz für den Begrenzungsfeld, der veraltet ist.</span><span class="sxs-lookup"><span data-stu-id="55559-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="55559-109">Das [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) Skript bietet grundlegende Funktionen zum Transformieren von Objekten in Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="55559-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="55559-110">Ein Begrenzungssteuerelement zeigt ein Feld um das Hologramm an, um anzugeben, dass es mit ihm interagiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="55559-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="55559-111">Handles an den Ecken und Rändern des Felds ermöglichen das Skalieren, Drehen oder Übersetzen des Objekts.</span><span class="sxs-lookup"><span data-stu-id="55559-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="55559-112">Das Begrenzungssteuerelement reagiert auch auf Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="55559-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="55559-113">Auf HoloLens 2 reagiert das Begrenzungssteuerelement z. B. auf Fingernähe und gibt visuelles Feedback, um die Entfernung zum Objekt zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="55559-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="55559-114">Alle Interaktionen und Visuals können einfach angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="55559-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="55559-115">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="55559-115">Example scene</span></span>

<span data-ttu-id="55559-116">Beispiele für Begrenzungssteuerelementkonfigurationen finden Sie in der `BoundsControlExamples` Szene.</span><span class="sxs-lookup"><span data-stu-id="55559-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a><span data-ttu-id="55559-117">Inspektoreigenschaften</span><span class="sxs-lookup"><span data-stu-id="55559-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="55559-118">Zielobjekt</span><span class="sxs-lookup"><span data-stu-id="55559-118">Target object</span></span>

<span data-ttu-id="55559-119">Diese Eigenschaft gibt an, welches Objekt durch die Bearbeitung des Begrenzungssteuerelements transformiert wird.</span><span class="sxs-lookup"><span data-stu-id="55559-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="55559-120">Wenn kein Objekt festgelegt ist, wird standardmäßig das Besitzerobjekt verwendet.</span><span class="sxs-lookup"><span data-stu-id="55559-120">If no object is set, it defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="55559-121">Aktivierungsverhalten</span><span class="sxs-lookup"><span data-stu-id="55559-121">Activation behavior</span></span>

<span data-ttu-id="55559-122">Es gibt mehrere Optionen zum Aktivieren der Begrenzungssteuerelementschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="55559-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="55559-123">*Bei Start aktivieren:* Das Begrenzungssteuerelement wird nach dem Start der Szene angezeigt.</span><span class="sxs-lookup"><span data-stu-id="55559-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="55559-124">*Activate By Proximity*: Das Steuerelement Bounds wird sichtbar, wenn sich eine artikulierte Hand in der Nähe des Objekts befindet.</span><span class="sxs-lookup"><span data-stu-id="55559-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="55559-125">*Aktivieren nach Zeiger:* Das Steuerelement "Bounds" wird sichtbar, wenn es von einem Handstrahlzeiger als Ziel verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="55559-126">*Activate By Proximity and Pointer (Durch Näherung und Zeiger aktivieren):* Das Steuerelement Bounds wird sichtbar, wenn es von einem Handstrahlzeiger angezielt wird oder sich eine artikulierte Hand in der Nähe des Objekts befindet.</span><span class="sxs-lookup"><span data-stu-id="55559-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="55559-127">*Manuell aktivieren:* Das Steuerelement Bounds wird nicht automatisch angezeigt.</span><span class="sxs-lookup"><span data-stu-id="55559-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="55559-128">Sie können sie manuell über ein Skript aktivieren, indem Sie auf die boundsControl.Active-Eigenschaft zugreifen.</span><span class="sxs-lookup"><span data-stu-id="55559-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="55559-129">Außerkraftsetzung von Begrenzungen</span><span class="sxs-lookup"><span data-stu-id="55559-129">Bounds override</span></span>

<span data-ttu-id="55559-130">Legt einen Feld-Collider aus dem -Objekt für die Berechnung von Begrenzungen fest.</span><span class="sxs-lookup"><span data-stu-id="55559-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="55559-131">Auffüllen von Schachteln</span><span class="sxs-lookup"><span data-stu-id="55559-131">Box padding</span></span>

<span data-ttu-id="55559-132">Fügt den Collidergrenzen, die zum Berechnen der Umfang des Steuerelements verwendet werden, einen Abstand hinzu.</span><span class="sxs-lookup"><span data-stu-id="55559-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="55559-133">Dies wirkt sich nicht nur auf die Interaktion aus, sondern auch auf die Visuals.</span><span class="sxs-lookup"><span data-stu-id="55559-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="55559-134">Flache Achse</span><span class="sxs-lookup"><span data-stu-id="55559-134">Flatten axis</span></span>

<span data-ttu-id="55559-135">Gibt an, ob das Steuerelement in einer der Achsen flach ist, sodass es zweidimensional ist und die Bearbeitung entlang dieser Achse nicht zu lässt.</span><span class="sxs-lookup"><span data-stu-id="55559-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="55559-136">Dieses Feature kann für schlanke Objekte wie Schiefer verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="55559-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="55559-137">Wenn flatten axis auf *Flatten Auto* festgelegt ist, wählt das Skript automatisch die Achse mit dem kleinsten Umfang als flache Achse aus.</span><span class="sxs-lookup"><span data-stu-id="55559-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="55559-138">Glättung</span><span class="sxs-lookup"><span data-stu-id="55559-138">Smoothing</span></span>

<span data-ttu-id="55559-139">Der Glättungsabschnitt ermöglicht das Konfigurieren des Glättungsverhaltens für die Skalierung und Drehung des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="55559-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="55559-140">Visuals</span><span class="sxs-lookup"><span data-stu-id="55559-140">Visuals</span></span>

<span data-ttu-id="55559-141">Die Darstellung des Begrenzungssteuerelements kann durch Ändern einer der entsprechenden Visualkonfigurationen konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="55559-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="55559-142">Visuelle Konfigurationen sind entweder verknüpfte oder inlineskriptfähige Objekte und werden im [Abschnitt Konfigurationsobjekt](#configuration-objects)ausführlicher beschrieben.</span><span class="sxs-lookup"><span data-stu-id="55559-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="55559-143">Konfigurationsobjekte</span><span class="sxs-lookup"><span data-stu-id="55559-143">Configuration Objects</span></span>

<span data-ttu-id="55559-144">Das Steuerelement enthält eine Reihe von Konfigurationsobjekten, die als skriptfähige Objekte gespeichert und von verschiedenen Instanzen oder Prefabs gemeinsam genutzt werden können.</span><span class="sxs-lookup"><span data-stu-id="55559-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="55559-145">Konfigurationen können entweder als einzelne skriptfähige Medienobjektdateien oder als geschachtelte skriptfähige Objekte innerhalb von Prefabs freigegeben und verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="55559-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="55559-146">Weitere Konfigurationen können auch direkt auf der Instanz definiert werden, ohne eine Verknüpfung mit einem externen oder geschachtelten Skriptobjekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="55559-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="55559-147">Der Begrenzungssteuerelementinspektor gibt an, ob eine Konfiguration als Teil der aktuellen Instanz freigegeben oder inline ist, indem eine Meldung im Eigenschafteninspektor angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="55559-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="55559-148">Darüber hinaus können freigegebene Instanzen nicht direkt im Eigenschaftenfenster des Begrenzungssteuerelements selbst bearbeitet werden. Stattdessen muss das Objekt, mit dem die Verknüpfung erfolgt, direkt geändert werden, um versehentliche Änderungen an freigegebenen Konfigurationen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="55559-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="55559-149">Derzeit bietet das Begrenzungssteuerelement Optionen für Konfigurationsobjekte für die folgenden Features:</span><span class="sxs-lookup"><span data-stu-id="55559-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="55559-150">Ziehpunkte</span><span class="sxs-lookup"><span data-stu-id="55559-150">Handles</span></span>
  * [<span data-ttu-id="55559-151">Skalierungshandles</span><span class="sxs-lookup"><span data-stu-id="55559-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="55559-152">Drehungshandles</span><span class="sxs-lookup"><span data-stu-id="55559-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="55559-153">Übersetzungshandles</span><span class="sxs-lookup"><span data-stu-id="55559-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="55559-154">Links/Wireframe</span><span class="sxs-lookup"><span data-stu-id="55559-154">Links / Wireframe</span></span>](#links-configuration-wireframe)
* [<span data-ttu-id="55559-155">Box-Anzeige</span><span class="sxs-lookup"><span data-stu-id="55559-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="55559-156">Näherungseffekt</span><span class="sxs-lookup"><span data-stu-id="55559-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="55559-157">Box-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="55559-157">Box configuration</span></span>

<span data-ttu-id="55559-158">Die Boxkonfiguration ist für das Rendern eines Volltonfelds mit Begrenzungen verantwortlich, die über Collidergröße und Feldauffüllung definiert werden.</span><span class="sxs-lookup"><span data-stu-id="55559-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="55559-159">Die folgenden Eigenschaften können eingerichtet werden:</span><span class="sxs-lookup"><span data-stu-id="55559-159">The following properties can be set up:</span></span>

* <span data-ttu-id="55559-160">**Feldmaterial:** Definiert das Material, das auf das gerenderte Feld angewendet wird, wenn keine Interaktion stattfindet.</span><span class="sxs-lookup"><span data-stu-id="55559-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="55559-161">Ein Feld wird nur gerendert, wenn dieses Material festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="55559-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="55559-162">**Gepacktes Material:** Material für die Box, wenn der Benutzer mit dem Steuerelement interagiert, indem er über nah- oder ferninteraktion greift.</span><span class="sxs-lookup"><span data-stu-id="55559-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="55559-163">**Anzeigeskala für flache Achsen:** Eine Skala, die auf die Feldanzeige angewendet wird, wenn eine der Achsen [flacher](#flatten-axis)wird.</span><span class="sxs-lookup"><span data-stu-id="55559-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="55559-164">Konfiguration von Skalierungshandles</span><span class="sxs-lookup"><span data-stu-id="55559-164">Scale handles configuration</span></span>

<span data-ttu-id="55559-165">Dieser Eigenschaftenschubladen ermöglicht es, das Verhalten und die Visualisierung von Skalierungshandles des Begrenzungssteuerelements zu ändern.</span><span class="sxs-lookup"><span data-stu-id="55559-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="55559-166">**Handlematerial:** Material, das auf die Ziehpunkte angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="55559-167">**Ziehmaterial** verarbeiten: Material, das auf den Ziehpunkt angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="55559-168">**Handle prefab**: optionales Prefab für das Skalierungshandle.</span><span class="sxs-lookup"><span data-stu-id="55559-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="55559-169">Wenn nicht festgelegt ist, verwendet MRTK einen Cube als Standard.</span><span class="sxs-lookup"><span data-stu-id="55559-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="55559-170">**Handlegröße:** Größe des Skalierungshandle.</span><span class="sxs-lookup"><span data-stu-id="55559-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="55559-171">**Colliderauffüllung:** Auffüllung, die dem Handle-Collider hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="55559-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="55559-172">Zeichnen des **Tethers beim Bearbeiten:** Wenn aktiv eine Tetherlinie vom Beginn der Interaktion bis zur aktuellen Hand- oder Zeigerposition zeichnet.</span><span class="sxs-lookup"><span data-stu-id="55559-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="55559-173">**Handles ignorieren Collider:** Wenn ein Collider hier verknüpft wird, ignorieren Handles alle Konflikte mit diesem Collider.</span><span class="sxs-lookup"><span data-stu-id="55559-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="55559-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span><span class="sxs-lookup"><span data-stu-id="55559-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="55559-175">**Skalierungshandles anzeigen:** Steuert die Sichtbarkeit des Handles.</span><span class="sxs-lookup"><span data-stu-id="55559-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="55559-176">**Skalierungsverhalten:** Kann auf einheitliche oder nicht einheitliche Skalierung festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="55559-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="55559-177">Rotation behandelt Konfiguration</span><span class="sxs-lookup"><span data-stu-id="55559-177">Rotation handles configuration</span></span>

<span data-ttu-id="55559-178">Diese Konfiguration definiert das Rotationshandleverhalten.</span><span class="sxs-lookup"><span data-stu-id="55559-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="55559-179">**Handlematerial:** Material, das auf die Ziehpunkte angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="55559-180">**Ziehmaterial** verarbeiten: Material, das auf den Ziehpunkt angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="55559-181">**Handle prefab**: optionales Prefab für das Handle.</span><span class="sxs-lookup"><span data-stu-id="55559-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="55559-182">Wenn nicht festgelegt ist, verwendet MRTK standardmäßig eine Kugel.</span><span class="sxs-lookup"><span data-stu-id="55559-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="55559-183">**Handlegröße:** Größe des Handles.</span><span class="sxs-lookup"><span data-stu-id="55559-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="55559-184">**Colliderauffüllung:** Auffüllung, die dem Handle-Collider hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="55559-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="55559-185">Zeichnen des **Tethers beim Bearbeiten:** Wenn aktiv eine Tetherlinie vom Beginn der Interaktion bis zur aktuellen Hand- oder Zeigerposition zeichnet.</span><span class="sxs-lookup"><span data-stu-id="55559-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="55559-186">**Handles ignorieren Collider:** Wenn ein Collider hier verknüpft wird, ignorieren Handles alle Konflikte mit diesem Collider.</span><span class="sxs-lookup"><span data-stu-id="55559-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="55559-187">**Behandeln des Prefab-Collidertyps:** Collidertyp, der mit dem erstellten Handle verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="55559-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="55559-188">**Handle für X anzeigen:** Steuert die Sichtbarkeit des Handles für die X-Achse.</span><span class="sxs-lookup"><span data-stu-id="55559-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="55559-189">**Handle für Y anzeigen:** Steuert die Sichtbarkeit des Handles für die Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="55559-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="55559-190">**Handle für Z anzeigen:** Steuert die Sichtbarkeit des Handles für die Z-Achse.</span><span class="sxs-lookup"><span data-stu-id="55559-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="55559-191">Konfiguration der Übersetzungshandles</span><span class="sxs-lookup"><span data-stu-id="55559-191">Translation handles configuration</span></span>

<span data-ttu-id="55559-192">Ermöglicht das Aktivieren und Konfigurieren von Übersetzungshandles für das Begrenzungssteuerelement.</span><span class="sxs-lookup"><span data-stu-id="55559-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="55559-193">Beachten Sie, dass Übersetzungshandles standardmäßig deaktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="55559-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="55559-194">**Handlematerial:** Material, das auf die Ziehpunkte angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="55559-195">**Ziehmaterial** verarbeiten: Material, das auf den Ziehpunkt angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="55559-196">**Handle prefab**: optionales Prefab für das Handle.</span><span class="sxs-lookup"><span data-stu-id="55559-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="55559-197">Wenn nicht festgelegt ist, verwendet MRTK standardmäßig eine Kugel.</span><span class="sxs-lookup"><span data-stu-id="55559-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="55559-198">**Handlegröße:** Größe des Handles.</span><span class="sxs-lookup"><span data-stu-id="55559-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="55559-199">**Colliderauffüllung:** Auffüllung, die dem Handle-Collider hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="55559-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="55559-200">Zeichnen des **Tethers beim Bearbeiten:** Wenn aktiv eine Tetherlinie vom Beginn der Interaktion bis zur aktuellen Hand- oder Zeigerposition zeichnet.</span><span class="sxs-lookup"><span data-stu-id="55559-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="55559-201">**Handles ignorieren Collider:** Wenn ein Collider hier verknüpft wird, ignorieren Handles alle Konflikte mit diesem Collider.</span><span class="sxs-lookup"><span data-stu-id="55559-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="55559-202">**Behandeln des Prefab-Collidertyps:** Collidertyp, der mit dem erstellten Handle verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="55559-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="55559-203">**Handle für X anzeigen:** Steuert die Sichtbarkeit des Handles für die X-Achse.</span><span class="sxs-lookup"><span data-stu-id="55559-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="55559-204">**Handle für Y anzeigen:** Steuert die Sichtbarkeit des Handles für die Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="55559-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="55559-205">**Handle für Z anzeigen:** Steuert die Sichtbarkeit des Handles für die Z-Achse.</span><span class="sxs-lookup"><span data-stu-id="55559-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="55559-206">Linkkonfiguration (Wireframe)</span><span class="sxs-lookup"><span data-stu-id="55559-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="55559-207">Die Linkkonfiguration aktiviert das Wireframe-Feature des Begrenzungssteuerelements.</span><span class="sxs-lookup"><span data-stu-id="55559-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="55559-208">Die folgenden Eigenschaften können konfiguriert werden:</span><span class="sxs-lookup"><span data-stu-id="55559-208">The following properties can be configured:</span></span>

* <span data-ttu-id="55559-209">**Wireframe-Material:** das Material, das auf das Wireframe-Gittermodell angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="55559-210">**Wireframe-Edgeradius:** die Stärke des Wireframes.</span><span class="sxs-lookup"><span data-stu-id="55559-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="55559-211">**Wireframe-Form:** Die Form des Wireframes kann entweder kubisch oder zylindrisch sein.</span><span class="sxs-lookup"><span data-stu-id="55559-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="55559-212">**Wireframe anzeigen:** Steuert die Sichtbarkeit des Wireframes.</span><span class="sxs-lookup"><span data-stu-id="55559-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="55559-213">Konfiguration des Näherungseffekts</span><span class="sxs-lookup"><span data-stu-id="55559-213">Proximity effect configuration</span></span>

<span data-ttu-id="55559-214">Zeigen Sie die Handles basierend auf der Entfernung zu den Händen mit Animation an, und blenden Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="55559-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="55559-215">Sie verfügt über zweistufige Skalierungsanimationen.</span><span class="sxs-lookup"><span data-stu-id="55559-215">It has two-step scaling animation.</span></span> <span data-ttu-id="55559-216">Standardwerte werden auf HoloLens 2 Stilverhalten festgelegt.</span><span class="sxs-lookup"><span data-stu-id="55559-216">Defaults are set to HoloLens 2 style behavior.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* <span data-ttu-id="55559-217">**Näherungseffekt aktiv:** Aktivierung des näherungsbasierten Handles aktivieren</span><span class="sxs-lookup"><span data-stu-id="55559-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="55559-218">**Objekt mittlere Nähe:** Entfernung für die Skalierung im ersten Schritt</span><span class="sxs-lookup"><span data-stu-id="55559-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="55559-219">Objekt close proximity :Distance for the 2nd step scaling **(Objektnähe:** Entfernung für die Skalierung im zweiten Schritt)</span><span class="sxs-lookup"><span data-stu-id="55559-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="55559-220">**Far Scale**: Der Standardskalierenwert des Handlemedienobjekts, wenn sich die Hände außerhalb des Bereichs der Begrenzungssteuerungsinteraktion befinden (entfernung oben durch "Mittlere Nähe behandeln" definiert).</span><span class="sxs-lookup"><span data-stu-id="55559-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="55559-221">Verwenden Sie 0, um das Handle standardmäßig auszublenden.)</span><span class="sxs-lookup"><span data-stu-id="55559-221">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="55559-222">**Mittlere Skalierung:** Der Skalierungswert des Handlemedienobjekts, wenn sich die Hände innerhalb des Bereichs der Begrenzungssteuerelementinteraktion befinden (entfernung oben durch "Handle Close Proximity" definiert).</span><span class="sxs-lookup"><span data-stu-id="55559-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="55559-223">Verwenden Sie 1, um die normale Größe anzuzeigen.)</span><span class="sxs-lookup"><span data-stu-id="55559-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="55559-224">**Skala schließen:** Skalierungswert des Handleobjekts, wenn sich die Hände innerhalb des Bereichs der Ziehinteraktion befinden (entfernung oben durch "Handle Close Proximity" definiert).</span><span class="sxs-lookup"><span data-stu-id="55559-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="55559-225">Verwenden Sie 1.x, um eine größere Größe anzuzeigen.)</span><span class="sxs-lookup"><span data-stu-id="55559-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="55559-226">**Far Grow Rate**:Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span><span class="sxs-lookup"><span data-stu-id="55559-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="55559-227">**Mittlere Zuwachsrate:** Raten Sie, dass ein näher skaliertes Objekt skaliert wird, wenn sich die Hand von mittel in nah bewegt.</span><span class="sxs-lookup"><span data-stu-id="55559-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="55559-228">**Close Grow Rate (Zuwachsrate** schließen): Raten Sie, dass ein näher skaliertes Objekt skaliert wird, wenn sich die Hand von der Nähe zum Objektcenter bewegt.</span><span class="sxs-lookup"><span data-stu-id="55559-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="55559-229">Einschränkungssystem</span><span class="sxs-lookup"><span data-stu-id="55559-229">Constraint System</span></span>

<span data-ttu-id="55559-230">Das Begrenzungssteuerelement unterstützt die Verwendung des [Einschränkungs-Managers](constraint-manager.md) zum Einschränken oder Ändern des Übersetzungs-, Drehungs- oder Skalierungsverhaltens bei Verwendung von Begrenzungssteuerelementhandles.</span><span class="sxs-lookup"><span data-stu-id="55559-230">Bounds control supports using the [constraint manager](constraint-manager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="55559-231">Der Eigenschafteninspektor zeigt alle verfügbaren Einschränkungs-Manager, die an dasselbe Spielobjekt angefügt sind, in einer Dropdownliste mit einer Option zum Scrollen und Hervorheben des ausgewählten Einschränkungs-Managers an.</span><span class="sxs-lookup"><span data-stu-id="55559-231">The property inspector will show all available constraint managers attached to the same game object in a dropdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a><span data-ttu-id="55559-232">Ereignisse</span><span class="sxs-lookup"><span data-stu-id="55559-232">Events</span></span>

<span data-ttu-id="55559-233">Das Bounds-Steuerelement stellt die folgenden Ereignisse bereit.</span><span class="sxs-lookup"><span data-stu-id="55559-233">Bounds control provides the following events.</span></span> <span data-ttu-id="55559-234">In diesem Beispiel werden diese Ereignisse verwendet, um Audiofeedback wiederzuspielen.</span><span class="sxs-lookup"><span data-stu-id="55559-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="55559-235">**Rotieren gestartet:** Wird ausgelöst, wenn die Drehung beginnt.</span><span class="sxs-lookup"><span data-stu-id="55559-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="55559-236">**Rotieren beendet:** Wird ausgelöst, wenn die Drehung beendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="55559-237">**Skalierung gestartet:** Wird ausgelöst, wenn die Skalierung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="55559-238">**Skalierung beendet:** Wird ausgelöst, wenn die Skalierung beendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="55559-239">**Translate Started**: Wird ausgelöst, wenn die Übersetzung beginnt.</span><span class="sxs-lookup"><span data-stu-id="55559-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="55559-240">**Translate Stopped**: Wird ausgelöst, wenn die Übersetzung beendet wird.</span><span class="sxs-lookup"><span data-stu-id="55559-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="55559-241">Elastische Datenbanken (experimentell)</span><span class="sxs-lookup"><span data-stu-id="55559-241">Elastics (Experimental)</span></span>

<span data-ttu-id="55559-242">Elastische Datenbanken können verwendet werden, wenn Objekte über das Begrenzungssteuerelement bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="55559-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="55559-243">Beachten Sie, dass sich das [System für elastische Datenbanken](../experimental/elastic-system.md) noch im experimentellen Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="55559-243">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="55559-244">Um elastische Datenbanken zu aktivieren, verknüpfen Sie entweder eine vorhandene Elastics Manager-Komponente, oder erstellen und verknüpfen Sie über die Schaltfläche einen neuen Manager für elastische `Add Elastics Manager` Datenbanken.</span><span class="sxs-lookup"><span data-stu-id="55559-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="55559-245">Handlestile</span><span class="sxs-lookup"><span data-stu-id="55559-245">Handle styles</span></span>

<span data-ttu-id="55559-246">Wenn Sie das Skript nur zuweisen, wird standardmäßig [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) das Handle des HoloLens 1. Generation angezeigt.</span><span class="sxs-lookup"><span data-stu-id="55559-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="55559-247">Um HoloLens 2 Stilhandles verwenden zu können, müssen Sie geeignete Handlepräfabs und Materialien zuweisen.</span><span class="sxs-lookup"><span data-stu-id="55559-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Bounds Control Handle Styles 2 (Steuerelementhandlestile für Begrenzungen 2)](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="55559-249">Im Folgenden finden Sie die Prefabs, Materialien und Skalierungswerte für die Steuerelementhandles HoloLens 2 Stilgrenzen.</span><span class="sxs-lookup"><span data-stu-id="55559-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="55559-250">Sie finden dieses Beispiel in der `BoundsControlExamples` Szene.</span><span class="sxs-lookup"><span data-stu-id="55559-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="55559-251">Handles (Setup für HoloLens 2 Format)</span><span class="sxs-lookup"><span data-stu-id="55559-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="55559-252">**Handle Material**: BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="55559-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="55559-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="55559-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="55559-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="55559-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="55559-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="55559-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="55559-256">**Größe des Skalierungshandle:** 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="55559-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="55559-257">**Scale Handle Collider Padding**: 0.016 (macht den ziehbaren Collider etwas größer als das Handlevisual)</span><span class="sxs-lookup"><span data-stu-id="55559-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="55559-258">**Rotationshandle prefab:** MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="55559-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="55559-259">**Rotationshandlegröße:** 0,016</span><span class="sxs-lookup"><span data-stu-id="55559-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="55559-260">**Rotation Handle Collider Padding**: 0.016 (macht den ziehbaren Collider etwas größer als das Handlevisual)</span><span class="sxs-lookup"><span data-stu-id="55559-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="55559-261">Transformationsänderungen mit Objektmanipulator</span><span class="sxs-lookup"><span data-stu-id="55559-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="55559-262">Ein Begrenzungssteuerelement kann in Kombination mit verwendet [`ObjectManipulator.cs`](object-manipulator.md) werden, um bestimmte Manipulationstypen (z. B.</span><span class="sxs-lookup"><span data-stu-id="55559-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](object-manipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="55559-263">Verschieben des -Objekts), ohne Handles zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="55559-263">moving the object) without using handles.</span></span> <span data-ttu-id="55559-264">Der Manipulationshandler unterstützt sowohl ein- als auch zweihändige Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="55559-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="55559-265">[Die Handnachverfolgung](../input/hand-tracking.md) kann verwendet werden, um mit einem Objekt aus nächster Nähe zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="55559-265">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

<span data-ttu-id="55559-266">Damit sich die Begrenzungssteuerelementränder beim Verschieben mit der fernen Interaktion des Steuerelements auf die gleiche Weise [`ObjectManipulator`](object-manipulator.md) verhalten, wird empfohlen, die Ereignisse für On Manipulation Started On Manipulation Ended *(Bei* Manipulation gestartet  /  *bei Manipulation beendet)* `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` mit zu verbinden, wie im obigen Screenshot gezeigt.</span><span class="sxs-lookup"><span data-stu-id="55559-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](object-manipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="55559-267">Hinzufügen und Konfigurieren eines Begrenzungssteuerelements mithilfe von Unity Inspector</span><span class="sxs-lookup"><span data-stu-id="55559-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="55559-268">Hinzufügen von Box Collider zu einem Objekt</span><span class="sxs-lookup"><span data-stu-id="55559-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="55559-269">Zuweisen `BoundsControl` eines Skripts zu einem Objekt</span><span class="sxs-lookup"><span data-stu-id="55559-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="55559-270">Konfigurieren von Optionen, z. B. Aktivierungsmethoden (siehe Abschnitt [Inspektoreigenschaften](#inspector-properties) unten)</span><span class="sxs-lookup"><span data-stu-id="55559-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="55559-271">(Optional) Zuweisen von Prefabs und Materialien für ein HoloLens 2 Stilbegrenzungssteuerelement (siehe Abschnitt [Handlestile](#handle-styles) weiter unten)</span><span class="sxs-lookup"><span data-stu-id="55559-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="55559-272">Verwenden Sie das Feld *Zielobjekt* und *Begrenzungsüberschreibung* im Inspektor, um ein bestimmtes Objekt und einen Collider im Objekt mit mehreren untergeordneten Komponenten zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="55559-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Begrenzungssteuerelement](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="55559-274">Hinzufügen und Konfigurieren eines Begrenzungssteuerelements im Code</span><span class="sxs-lookup"><span data-stu-id="55559-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="55559-275">Instanziieren des Cubes GameObject</span><span class="sxs-lookup"><span data-stu-id="55559-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="55559-276">Zuweisen `BoundsControl` eines Skripts zu einem Objekt mit Collider mit addComponent<>()</span><span class="sxs-lookup"><span data-stu-id="55559-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="55559-277">Konfigurieren Sie Optionen entweder direkt auf dem Steuerelement oder über eine der skriptfähigen Konfigurationen (siehe Abschnitt [Inspektoreigenschaften](#inspector-properties) und [Konfigurationen](#configuration-objects) weiter unten).</span><span class="sxs-lookup"><span data-stu-id="55559-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="55559-278">(Optional) Weisen Sie Prefabs und Materialien für ein HoloLens 2 Stilbegrenzungssteuerelement zu.</span><span class="sxs-lookup"><span data-stu-id="55559-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="55559-279">Hierfür sind weiterhin Zuweisungen über den Inspektor erforderlich, da die Materialien und Prefabs dynamisch geladen werden sollten.</span><span class="sxs-lookup"><span data-stu-id="55559-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="55559-280">Die Verwendung des Ordners "Resources" von Unity oder [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) zum dynamischen Laden von Shadern wird nicht empfohlen, da Shader-Permutationen zur Laufzeit möglicherweise fehlen.</span><span class="sxs-lookup"><span data-stu-id="55559-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="55559-281">Beispiel: Festlegen der minimalen, maximalen Begrenzungen für die Steuerung der Skalierung mit MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="55559-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="55559-282">Um die minimale und maximale Skalierung festzulegen, fügen Sie eine [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) an Das Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="55559-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your control.</span></span> <span data-ttu-id="55559-283">Da das Bounds-Steuerelement den Einschränkungs-Manager automatisch anfügt und aktiviert, wird MinMaxScaleConstraint automatisch auf die Transformationsänderungen angewendet, sobald sie angefügt und konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="55559-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="55559-284">Sie können auch MinMaxScaleConstraint verwenden, um die minimale und maximale Skalierung für [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) festzulegen.</span><span class="sxs-lookup"><span data-stu-id="55559-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="55559-285">Beispiel: Hinzufügen eines Begrenzungssteuerelements um ein Spielobjekt</span><span class="sxs-lookup"><span data-stu-id="55559-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="55559-286">Um ein Begrenzungssteuerelement um ein Objekt hinzuzufügen, fügen Sie ihm einfach eine `BoundsControl` Komponente hinzu:</span><span class="sxs-lookup"><span data-stu-id="55559-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="55559-287">Migrieren von Bounding Box</span><span class="sxs-lookup"><span data-stu-id="55559-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="55559-288">Vorhandene Prefabs und Instanzen, die [begrenzungsfeld](bounding-box.md) verwenden, können über das [Migrationsfenster,](../tools/migration-window.md) das Teil des MRTK-Toolspakets ist, auf das neue Begrenzungssteuerelement aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="55559-288">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="55559-289">Für das Upgrade einzelner Instanzen des Begrenzungsfelds gibt es auch eine Migrationsoption innerhalb des Eigenschafteninspektors der Komponente.</span><span class="sxs-lookup"><span data-stu-id="55559-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a><span data-ttu-id="55559-290">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="55559-290">See also</span></span>

* [<span data-ttu-id="55559-291">Objektmanipulator</span><span class="sxs-lookup"><span data-stu-id="55559-291">Object manipulator</span></span>](object-manipulator.md)
* [<span data-ttu-id="55559-292">Einschränkungs-Manager</span><span class="sxs-lookup"><span data-stu-id="55559-292">Constraint manager</span></span>](constraint-manager.md)
* [<span data-ttu-id="55559-293">Migrationszeitfenster</span><span class="sxs-lookup"><span data-stu-id="55559-293">Migration window</span></span>](../tools/migration-window.md)
* [<span data-ttu-id="55559-294">Elastics-System (experimentell)</span><span class="sxs-lookup"><span data-stu-id="55559-294">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)
