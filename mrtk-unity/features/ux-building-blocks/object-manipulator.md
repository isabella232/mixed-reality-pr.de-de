---
title: Objektmanipulator
description: Verwenden des Objektmanipulators in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Objektbearbeitung,
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176657"
---
# <a name="object-manipulator"></a><span data-ttu-id="8b4a3-104">Objektmanipulator</span><span class="sxs-lookup"><span data-stu-id="8b4a3-104">Object manipulator</span></span>

![Objektmanipulator](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="8b4a3-106">*ObjectManipulator ist* die neue Komponente für Manipulationsverhalten, die zuvor in *ManipulationHandler gefunden wurde.*</span><span class="sxs-lookup"><span data-stu-id="8b4a3-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="8b4a3-107">Der Objektmanipulator macht eine Reihe von Verbesserungen und Vereinfachungen.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="8b4a3-108">Diese Komponente ist ein Ersatz für den Manipulationshandler, der veraltet ist.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="8b4a3-109">Das *ObjectManipulator-Skript* macht ein Objekt mit einem oder zwei Händen verschiebbar, skalierbar und drehbar.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="8b4a3-110">Der Objektmanipulator kann konfiguriert werden, um zu steuern, wie das Objekt auf verschiedene Eingaben reagiert.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="8b4a3-111">Das Skript sollte mit den meisten Formen der Interaktion funktionieren, z. B. HoloLens 2 Artikulierte Hand, HoloLens 2 Handlichtlicht, HoloLens 1 Anvisiert und Gesten und immersive Headset-Bewegungscontrollereingabe.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="8b4a3-112">Verwenden des Objektmanipulators</span><span class="sxs-lookup"><span data-stu-id="8b4a3-112">How to use the object manipulator</span></span>

<span data-ttu-id="8b4a3-113">Um den Objektmanipulator zu verwenden, fügen Sie zunächst die `ObjectManipulator` Skriptkomponente einem GameObject hinzu.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="8b4a3-114">Stellen Sie sicher, dass Sie dem Objekt auch einen Collider hinzufügen, der dessen ziehbaren Grenzen anpasst.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="8b4a3-115">Fügen Sie auch das Skript hinzu, damit das Objekt auf Eingaben nahezu `NearInteractionGrabbable` artikulierter Hand reagiert.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="8b4a3-116">Physikalisches Verhalten kann für den Objektmanipulator aktiviert werden, indem dem Objekt eine Festkörperkomponente hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="8b4a3-117">Physikalisches Verhalten, das durch Hinzufügen dieser Komponente aktiviert wird, wird unter [*Physik und Kollisionen ausführlicher erläutert.*](#physics-and-collisions)</span><span class="sxs-lookup"><span data-stu-id="8b4a3-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="8b4a3-118">Ebenso kann die Bearbeitung eingeschränkt werden, indem dem Objekt [Manipulationseinschränkungskomponenten](constraint-manager.md#transform-constraints) hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](constraint-manager.md#transform-constraints) to the object.</span></span> <span data-ttu-id="8b4a3-119">Hierbei handelt es sich um spezielle Komponenten, die mit Manipulation arbeiten und das Manipulationsverhalten in irgendeiner Weise ändern.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![Verwenden des Manipulationshandlers im Unity-Editor](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="8b4a3-121">Inspektoreigenschaften und -felder</span><span class="sxs-lookup"><span data-stu-id="8b4a3-121">Inspector properties and fields</span></span>

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="8b4a3-122">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="8b4a3-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="8b4a3-123">Hosttransformation</span><span class="sxs-lookup"><span data-stu-id="8b4a3-123">Host transform</span></span>

<span data-ttu-id="8b4a3-124">Die Objekttransformation, die bearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="8b4a3-125">Der Standardwert ist das -Objekt der Komponente.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="8b4a3-126">Manipulationstyp</span><span class="sxs-lookup"><span data-stu-id="8b4a3-126">Manipulation type</span></span>

<span data-ttu-id="8b4a3-127">Gibt an, ob das Objekt mit einer Hand oder zwei Händen bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="8b4a3-128">Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="8b4a3-129">*Einhändig:* Aktiviert eine handhändige Bearbeitung, wenn diese ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="8b4a3-130">*Zweihändig:* Aktiviert zweihändige Manipulationen, wenn diese ausgewählt sind.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="8b4a3-131">Fernbearbeitung zulassen</span><span class="sxs-lookup"><span data-stu-id="8b4a3-131">Allow far manipulation</span></span>

<span data-ttu-id="8b4a3-132">Gibt an, ob die Bearbeitung mithilfe der Ferninteraktion mit Zeigern erfolgen kann.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="8b4a3-133">Einhändige Manipulationseigenschaften</span><span class="sxs-lookup"><span data-stu-id="8b4a3-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="8b4a3-134">Drehmodus mit einer Hand in der Nähe</span><span class="sxs-lookup"><span data-stu-id="8b4a3-134">One hand rotation mode near</span></span>

<span data-ttu-id="8b4a3-135">Gibt an, wie sich das Objekt verhält, wenn es mit einer Hand in der Nähe greifst.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="8b4a3-136">Diese Optionen funktionieren nur für artikulierte Hände.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="8b4a3-137">*Drehen um objektzentriert:* Das Objekt dreht sich mithilfe der Drehung der Hand, aber um den Objektzentriertpunkt.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="8b4a3-138">Das Objekt scheint sich während der Drehung weniger zu bewegen, aber es kann ein Gefühl der Trennung zwischen der Hand und dem Objekt auftreten.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="8b4a3-139">Nützlicher für die Ferninteraktion.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-139">More useful for far interaction.</span></span>
- <span data-ttu-id="8b4a3-140">*Drehen um den Greifpunkt:* Drehen Sie das Objekt mit der Hand um den Greifpunkt zwischen dem Greifpunkt und dem Zeigefinger.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="8b4a3-141">Es sollte sich so anfühlen, als würde das Objekt von der Hand gehalten.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="8b4a3-142">One-Hand-Drehungsmodus weit</span><span class="sxs-lookup"><span data-stu-id="8b4a3-142">One hand rotation mode far</span></span>

<span data-ttu-id="8b4a3-143">Gibt an, wie sich das Objekt verhält, wenn es mit einer Hand aus der Entfernung greifst.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="8b4a3-144">Diese Optionen funktionieren nur für artikulierte Hände.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="8b4a3-145">*Drehen um objektzentriert:* Drehen Sie das Objekt mithilfe einer Drehung der Hand, aber um den Objektzentriertpunkt.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="8b4a3-146">Nützlich für die Untersuchung aus der Entfernung, ohne dass sich der Objektzentriert während der Objektdrehung bewegt.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="8b4a3-147">*Drehen um den Greifpunkt:* Drehen Sie das Objekt mithilfe der Drehung der Hand, aber um den Zeigerstrahl-Trefferpunkt.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="8b4a3-148">Nützlich für die Überprüfung.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="8b4a3-149">Zweihändige Manipulationseigenschaften</span><span class="sxs-lookup"><span data-stu-id="8b4a3-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="8b4a3-150">Zweihändiger Manipulationstyp</span><span class="sxs-lookup"><span data-stu-id="8b4a3-150">Two handed manipulation type</span></span>

<span data-ttu-id="8b4a3-151">Gibt an, wie zwei Handmanipulationen ein Objekt transformieren können.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="8b4a3-152">Da diese Eigenschaft ein Flag ist, kann eine beliebige Anzahl von Optionen ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="8b4a3-153">*Verschieben:* Das Verschieben ist zulässig, wenn diese Option ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="8b4a3-154">*Skalierung:* Die Skalierung ist zulässig, wenn diese Option ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="8b4a3-155">*Rotieren:* Die Drehung ist zulässig, wenn diese Option ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-155">*Rotate*: Rotation is allowed if selected.</span></span>

![Manipulationshandler](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="8b4a3-157">Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="8b4a3-157">Constraints</span></span>

#### <a name="enable-constraints"></a><span data-ttu-id="8b4a3-158">Aktivieren von Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="8b4a3-158">Enable constraints</span></span>

<span data-ttu-id="8b4a3-159">Diese Einstellung aktiviert den verknüpften [Einschränkungs-Manager.](constraint-manager.md)</span><span class="sxs-lookup"><span data-stu-id="8b4a3-159">This setting will enable the linked [constraint manager](constraint-manager.md).</span></span> <span data-ttu-id="8b4a3-160">Transformationsänderungen werden von Einschränkungen verarbeitet, die für den ausgewählten Einschränkungs-Manager [registriert sind.](constraint-manager.md)</span><span class="sxs-lookup"><span data-stu-id="8b4a3-160">Transform changes will be processed by constraints registered to the selected [constraint manager](constraint-manager.md).</span></span>

#### <a name="constraint-manager"></a><span data-ttu-id="8b4a3-161">Einschränkungs-Manager</span><span class="sxs-lookup"><span data-stu-id="8b4a3-161">Constraint manager</span></span>

<span data-ttu-id="8b4a3-162">In der Dropdownliste können Sie einen der angefügten [Einschränkungs-Manager auswählen.](constraint-manager.md)</span><span class="sxs-lookup"><span data-stu-id="8b4a3-162">The dropdown allows to select any of the attached [constraint managers](constraint-manager.md).</span></span> <span data-ttu-id="8b4a3-163">Der Objektmanipulator stellt sicher, dass [jederzeit](constraint-manager.md) ein Einschränkungs-Manager angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-163">Object manipulator ensures there's a [constraint manager](constraint-manager.md) attached at all times.</span></span>
<span data-ttu-id="8b4a3-164">Beachten Sie, dass mehrere Komponenten desselben Typs in Unity unter demselben Namen zu sehen sind.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-164">Note that multiple components of the same type will show up under the same name in unity.</span></span> <span data-ttu-id="8b4a3-165">Um die Unterscheidung zwischen mehreren Einschränkungs-Managern für dasselbe Objekt zu vereinfachen, zeigen die verfügbaren Optionen einen Hinweis zur Konfiguration des ausgewählten Einschränkungs-Managers (manuelle oder automatische Einschränkungsauswahl) an.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-165">To make it easier to distinguish between multiple constraint managers on the same object, the available options will show a hint on the configuration of the selected constraint manager (manual or auto constraint selection).</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="8b4a3-166">Zu Komponente wechseln</span><span class="sxs-lookup"><span data-stu-id="8b4a3-166">Go to component</span></span>

<span data-ttu-id="8b4a3-167">Die Einschränkungs-Manager-Auswahl verfügt über die *Schaltfläche Zu Komponente* wechseln.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-167">The constraint manager selection comes with a *Go to component* button.</span></span> <span data-ttu-id="8b4a3-168">Diese Schaltfläche führt dazu, dass der Inspektor zur ausgewählten Komponente scrollt, damit sie konfiguriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-168">This button will cause the inspector to scroll to the selected component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="8b4a3-169">Physische Effekte</span><span class="sxs-lookup"><span data-stu-id="8b4a3-169">Physics</span></span>

<span data-ttu-id="8b4a3-170">Einstellungen in diesem Abschnitt werden nur angezeigt, wenn das Objekt über eine RigidBody-Komponente verfügt.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-170">Settings in this section appear only when the object has a RigidBody component.</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="8b4a3-171">Releaseverhalten</span><span class="sxs-lookup"><span data-stu-id="8b4a3-171">Release behavior</span></span>

<span data-ttu-id="8b4a3-172">Geben Sie an, welche physischen Eigenschaften ein bearbeitetes Objekt bei der Freigabe behalten soll.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-172">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="8b4a3-173">Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-173">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="8b4a3-174">*Geschwindigkeit behalten:* Wenn das Objekt freigegeben wird und diese Option ausgewählt ist, bleibt die lineare Geschwindigkeit erhalten.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-174">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="8b4a3-175">*Geschwindigkeit Angular:* Wenn das Objekt freigegeben wird und diese Option ausgewählt ist, bleibt die Winkelgeschwindigkeit erhalten.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-175">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

#### <a name="use-forces-for-near-manipulation"></a><span data-ttu-id="8b4a3-176">Verwenden von Struppen für die nahezue Manipulation</span><span class="sxs-lookup"><span data-stu-id="8b4a3-176">Use forces for near manipulation</span></span>

<span data-ttu-id="8b4a3-177">Gibt an, ob physikalische Struppen verwendet werden, um das Objekt zu verschieben, wenn nahe Manipulationen angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-177">Whether physics forces are used to move the object when performing near manipulations.</span></span> <span data-ttu-id="8b4a3-178">Wenn sie auf *FALSE festgelegt wird,* wird das Objekt direkter mit der Benutzerhand verbunden.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-178">Setting this to *false* will make the object feel more directly connected to the users hand.</span></span> <span data-ttu-id="8b4a3-179">Wenn Sie diese Einstellung *auf TRUE* festlegen, werden die Massen- und Trägheit des Objekts erfüllt, aber es kann sich so anfühlen, als ob das Objekt über eine Feder verbunden wäre.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-179">Setting this to *true* will honor the mass and inertia of the object, but may feel as though the object is connected through a spring.</span></span> <span data-ttu-id="8b4a3-180">Der Standardwert ist *FALSE*.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-180">The default is *false*.</span></span>

### <a name="smoothing"></a><span data-ttu-id="8b4a3-181">Glättung</span><span class="sxs-lookup"><span data-stu-id="8b4a3-181">Smoothing</span></span>

#### <a name="smoothing-far"></a><span data-ttu-id="8b4a3-182">Glättung weit</span><span class="sxs-lookup"><span data-stu-id="8b4a3-182">Smoothing far</span></span>

<span data-ttu-id="8b4a3-183">Gibt an, ob die bildratenunabhängige Glättung für Ferninteraktionen aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-183">Whether frame-rate independent smoothing is enabled for far interactions.</span></span> <span data-ttu-id="8b4a3-184">Far Smoothing ist standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-184">Far smoothing is enabled by default.</span></span>

#### <a name="smoothing-near"></a><span data-ttu-id="8b4a3-185">Glättung in der Nähe</span><span class="sxs-lookup"><span data-stu-id="8b4a3-185">Smoothing near</span></span>

<span data-ttu-id="8b4a3-186">Gibt an, ob die bildratenunabhängige Glättung für nahezu alle Interaktionen aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-186">Whether frame-rate independent smoothing is enabled for near interactions.</span></span> <span data-ttu-id="8b4a3-187">Die Nahezuglättung ist standardmäßig deaktiviert, da der Effekt möglicherweise als "getrennt" von der Hand wahrgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-187">Near smoothing is disabled by default because the effect may be perceived as being 'disconnected' from the hand.</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="8b4a3-188">Glättung aktiv</span><span class="sxs-lookup"><span data-stu-id="8b4a3-188">Smoothing active</span></span>

<span data-ttu-id="8b4a3-189">Veraltet und werden in einer zukünftigen Version entfernt.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-189">Obsolete and will be removed in a future version.</span></span> <span data-ttu-id="8b4a3-190">Anwendungen sollten SmoothingFar, SmoothingNear oder eine Kombination aus beiden verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-190">Applications should use SmoothingFar, SmoothingNear or a combination of the two.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="8b4a3-191">Lerpzeit verschieben</span><span class="sxs-lookup"><span data-stu-id="8b4a3-191">Move lerp time</span></span>

<span data-ttu-id="8b4a3-192">Der Glättungsbetrag, der auf die Bewegung angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-192">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="8b4a3-193">Eine Glättung von 0 bedeutet keine Glättung.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-193">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="8b4a3-194">Der maximale Wert bedeutet, dass kein Wert geändert wird.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-194">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="8b4a3-195">Rotieren der Lerpzeit</span><span class="sxs-lookup"><span data-stu-id="8b4a3-195">Rotate lerp time</span></span>

<span data-ttu-id="8b4a3-196">Die Glättungsmenge, die auf die Drehung angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-196">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="8b4a3-197">Eine Glättung von 0 bedeutet keine Glättung.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-197">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="8b4a3-198">Der maximale Wert bedeutet, dass kein Wert geändert wird.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-198">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="8b4a3-199">Skalieren der Lerpzeit</span><span class="sxs-lookup"><span data-stu-id="8b4a3-199">Scale lerp time</span></span>

<span data-ttu-id="8b4a3-200">Umfang der Glättung, die auf die Skala angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-200">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="8b4a3-201">Eine Glättung von 0 bedeutet keine Glättung.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-201">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="8b4a3-202">Der maximale Wert bedeutet, dass keine Änderung des Werts vor sich geht.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-202">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="8b4a3-203">Bearbeitungsereignisse</span><span class="sxs-lookup"><span data-stu-id="8b4a3-203">Manipulation events</span></span>

<span data-ttu-id="8b4a3-204">Der Manipulationshandler stellt die folgenden Ereignisse zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="8b4a3-204">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="8b4a3-205">*OnManipulationStarted:* Wird ausgelöst, wenn die Bearbeitung beginnt.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-205">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="8b4a3-206">*OnManipulationEnded:* Wird beim Ende der Bearbeitung aus.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-206">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="8b4a3-207">*OnHoverStarted:* Wird bei einem Hand-/Controller-Hover auf das manipulatable-, nah- oder fern-Paar aus.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-207">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="8b4a3-208">*OnHoverEnded:* Wird aus, wenn eine Hand/ein Controller das manipulatable in der Nähe oder weit entfernt entlädt.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-208">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="8b4a3-209">Die Reihenfolge der Ereignislöschung für die Bearbeitung ist:</span><span class="sxs-lookup"><span data-stu-id="8b4a3-209">The event fire order for manipulation is:</span></span>

<span data-ttu-id="8b4a3-210">*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="8b4a3-210">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="8b4a3-211">Wenn keine Bearbeitung vorkommt, erhalten Sie immer noch Hoverereignisse mit der folgenden Brandreihen reihenfolge:</span><span class="sxs-lookup"><span data-stu-id="8b4a3-211">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="8b4a3-212">*OnHoverStarted*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="8b4a3-212">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="8b4a3-213">Physik und Kollisionen</span><span class="sxs-lookup"><span data-stu-id="8b4a3-213">Physics and collisions</span></span>

<span data-ttu-id="8b4a3-214">Physikalisches Verhalten kann aktiviert werden, indem demselben Objekt wie einem Objektmanipulator eine Festkörperkomponente hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-214">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="8b4a3-215">Dies ermöglicht nicht nur die oben beschriebene Konfiguration des [Releaseverhaltens,](#release-behavior) sondern auch Kollisionen.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-215">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="8b4a3-216">Ohne eine Festkörperkomponente verhalten sich Kollisionen während der Bearbeitung nicht ordnungsgemäß:</span><span class="sxs-lookup"><span data-stu-id="8b4a3-216">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="8b4a3-217">Kollisionen zwischen einem manipulierten Objekt und einem statischen Collider (d. h. ein Objekt mit einem Collider, aber ohne Festkörper) funktionieren nicht, das bearbeitete Objekt durchläuft den statischen Collider unbeeinflusst.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-217">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="8b4a3-218">Kollisionen zwischen einem manipulierten Objekt und einem Festkörper (d. h.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-218">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="8b4a3-219">ein Objekt mit einem Collider und einem starren Objekt) dazu führen, dass der Starrer eine Kollisionsantwort hat, aber die Antwort ist sprungig und unnatürlich.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-219">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="8b4a3-220">Es gibt auch keine Kollisionsantwort für das bearbeitete Objekt.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-220">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="8b4a3-221">Wenn ein Festkörper hinzugefügt wird, sollten Kollisionen ordnungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-221">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="8b4a3-222">Ohne Festkörper</span><span class="sxs-lookup"><span data-stu-id="8b4a3-222">Without rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="8b4a3-223">Mit "rigidbody"</span><span class="sxs-lookup"><span data-stu-id="8b4a3-223">With rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a><span data-ttu-id="8b4a3-224">Elastische Datenbanken (experimentell)</span><span class="sxs-lookup"><span data-stu-id="8b4a3-224">Elastics (Experimental)</span></span>

<span data-ttu-id="8b4a3-225">Elastische Datenbanken können beim Bearbeiten von Objekten über den Objektmanipulator verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-225">Elastics can be used when manipulating objects via object manipulator.</span></span> <span data-ttu-id="8b4a3-226">Beachten Sie, [dass sich das Elastiksystem](../experimental/elastic-system.md) noch im experimentellen Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-226">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="8b4a3-227">Um elastische Datenbanken zu aktivieren, verknüpfen Sie entweder eine vorhandene Elastics Manager-Komponente, oder erstellen und verknüpfen Sie über die Schaltfläche einen neuen `Add Elastics Manager` Elastik-Manager.</span><span class="sxs-lookup"><span data-stu-id="8b4a3-227">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a><span data-ttu-id="8b4a3-228">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8b4a3-228">See also</span></span>

- [<span data-ttu-id="8b4a3-229">Steuerelement "Begrenzungen"</span><span class="sxs-lookup"><span data-stu-id="8b4a3-229">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="8b4a3-230">Einschränkungs-Manager</span><span class="sxs-lookup"><span data-stu-id="8b4a3-230">Constraint manager</span></span>](constraint-manager.md)
- [<span data-ttu-id="8b4a3-231">Migrationszeitfenster</span><span class="sxs-lookup"><span data-stu-id="8b4a3-231">Migration window</span></span>](../tools/migration-window.md)
- [<span data-ttu-id="8b4a3-232">Elastisches System (experimentell)</span><span class="sxs-lookup"><span data-stu-id="8b4a3-232">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)
