---
title: Einschränkungs-Manager
description: Übersicht über den Einschränkungs-Manager in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177549"
---
# <a name="constraint-manager"></a><span data-ttu-id="e3c32-104">Einschränkungs-Manager</span><span class="sxs-lookup"><span data-stu-id="e3c32-104">Constraint manager</span></span>

<span data-ttu-id="e3c32-105">Der Einschränkungs-Manager ermöglicht das Anwenden einer Gruppe von Einschränkungskomponenten auf eine Transformation.</span><span class="sxs-lookup"><span data-stu-id="e3c32-105">The constraint manager allows to apply a set of constraint components to a transform.</span></span> <span data-ttu-id="e3c32-106">Komponenten vom Typ [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) , die an das Spielobjekt angefügt sind, können berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-106">Components of type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) that are attached to the game object can be taken into consideration.</span></span>
<span data-ttu-id="e3c32-107">Standardmäßig erfasst der Einschränkungs-Manager [](#transform-constraints) automatisch alle Einschränkungskomponenten, die an das Spielobjekt angefügt sind, und wenden sie auf verarbeitete Transformationen an.</span><span class="sxs-lookup"><span data-stu-id="e3c32-107">Per default, constraint manager will automatically collect all [constraint components](#transform-constraints) attached to the game object and apply them to processed transforms.</span></span>
<span data-ttu-id="e3c32-108">Benutzer können sich jedoch dafür entscheiden, die Liste der angewendeten Einschränkungen manuell zu konfigurieren und nur eine Teilmenge der angefügten Einschränkungen anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-108">However users can opt for configuring the list of applied constraints manually and allowing only a subset of attached constraints to be applied.</span></span>

<span data-ttu-id="e3c32-109">Derzeit unterstützen die folgenden MRTK-UX-Elemente den Einschränkungs-Manager:</span><span class="sxs-lookup"><span data-stu-id="e3c32-109">Currently the following MRTK UX elements are supporting constraint manager:</span></span>

- [<span data-ttu-id="e3c32-110">Steuerelement "Begrenzungen"</span><span class="sxs-lookup"><span data-stu-id="e3c32-110">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="e3c32-111">Objektmanipulator</span><span class="sxs-lookup"><span data-stu-id="e3c32-111">Object manipulator</span></span>](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="e3c32-112">Inspektoreigenschaften und -felder</span><span class="sxs-lookup"><span data-stu-id="e3c32-112">Inspector properties and fields</span></span>

<span data-ttu-id="e3c32-113">Der Einschränkungs-Manager kann in zwei Modi betrieben werden:</span><span class="sxs-lookup"><span data-stu-id="e3c32-113">Constraint manager can be operated in two modes:</span></span>

- <span data-ttu-id="e3c32-114">Automatische Einschränkungsauswahl</span><span class="sxs-lookup"><span data-stu-id="e3c32-114">Auto constraint selection</span></span>
- <span data-ttu-id="e3c32-115">Manuelle Einschränkungsauswahl</span><span class="sxs-lookup"><span data-stu-id="e3c32-115">Manual constraint selection</span></span>

### <a name="auto-constraint-selection"></a><span data-ttu-id="e3c32-116">Automatische Einschränkungsauswahl</span><span class="sxs-lookup"><span data-stu-id="e3c32-116">Auto constraint selection</span></span>

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

<span data-ttu-id="e3c32-117">Der Standardmodus des Einschränkungs-Managers, die automatische Einschränkungsauswahl, stellt [](#go-to-component) eine Liste aller angefügten Einschränkungskomponenten sowie Schaltflächen und eine Schaltfläche zum Hinzufügen von [Einschränkungen zur Verfügung.](#add-constraint-to-game-object)</span><span class="sxs-lookup"><span data-stu-id="e3c32-117">The default mode of constraint manager, auto constraint selection, will provide a list of all attached constraint components as well as [go to buttons](#go-to-component) and an [add constraint button](#add-constraint-to-game-object).</span></span>

#### <a name="add-constraint-to-game-object"></a><span data-ttu-id="e3c32-118">Hinzufügen einer Einschränkung zum Spielobjekt</span><span class="sxs-lookup"><span data-stu-id="e3c32-118">Add constraint to game object</span></span>

<span data-ttu-id="e3c32-119">Mit dieser Schaltfläche kann eine Einschränkungskomponente direkt aus dem Einschränkungs-Manager-Inspektor hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-119">This button allows a constraint component to be added directly from the constraint manager inspector.</span></span> <span data-ttu-id="e3c32-120">Alle Einschränkungstypen in einem Projekt sollten hier angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-120">All constraint types in a project should be visible here.</span></span> <span data-ttu-id="e3c32-121">Weitere [Informationen finden Sie unter Transformationseinschränkungen.](#transform-constraints)</span><span class="sxs-lookup"><span data-stu-id="e3c32-121">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="e3c32-122">Zu Komponente wechseln</span><span class="sxs-lookup"><span data-stu-id="e3c32-122">Go to component</span></span>

<span data-ttu-id="e3c32-123">Alle Einschränkungen, die für das Objekt gefunden werden, werden hier mit der Schaltfläche *Zu Komponente wechseln* aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="e3c32-123">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="e3c32-124">Diese Schaltfläche führt dazu, dass der Inspektor zur ausgewählten Einschränkungskomponente scrollt, damit sie konfiguriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="e3c32-124">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="manual-constraint-selection"></a><span data-ttu-id="e3c32-125">Manuelle Einschränkungsauswahl</span><span class="sxs-lookup"><span data-stu-id="e3c32-125">Manual constraint selection</span></span>

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

<span data-ttu-id="e3c32-126">Wenn der Einschränkungs-Manager auf den manuellen Modus festgelegt ist, werden nur Einschränkungen verarbeitet und auf die Transformation angewendet, die in der Einschränkungsliste verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="e3c32-126">If constraint manager is set to manual mode, only constraints that are linked in the constraint list are processed and applied to the transform.</span></span> <span data-ttu-id="e3c32-127">In der angezeigten Liste werden nur die [](#go-to-component) vom Benutzer ausgewählten Einschränkungen angezeigt, und es werden Schaltflächen oder Optionen zum Entfernen oder Hinzufügen von Einträgen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e3c32-127">The list displayed will only show the user selected constraints as well as [go to buttons](#go-to-component) or options to remove or add entries.</span></span>
<span data-ttu-id="e3c32-128">Wenn der manuelle Modus zum ersten Mal aktiviert wird, füllt der Einschränkungs-Manager die Liste mit allen verfügbaren Komponenten als Ausgangspunkt für die Auswahl angefügter Einschränkungskomponenten auf.</span><span class="sxs-lookup"><span data-stu-id="e3c32-128">When enabling manual mode for the first time, constraint manager will populate the list will all available components as a starting point for selecting attached constraint components.</span></span>

### <a name="remove-entry"></a><span data-ttu-id="e3c32-129">Eintrag entfernen</span><span class="sxs-lookup"><span data-stu-id="e3c32-129">Remove entry</span></span>

<span data-ttu-id="e3c32-130">Dadurch wird der Eintrag aus der manuell ausgewählten Liste entfernt.</span><span class="sxs-lookup"><span data-stu-id="e3c32-130">This removes the entry from the manually selected list.</span></span> <span data-ttu-id="e3c32-131">Beachten Sie, dass diese Option die Einschränkungskomponente nicht aus dem Spielobjekt entfernt.</span><span class="sxs-lookup"><span data-stu-id="e3c32-131">Note that this option will not remove the constraint component from the game object.</span></span> <span data-ttu-id="e3c32-132">Einschränkungskomponenten müssen immer manuell entfernt werden, um sicherzustellen, dass keine andere Komponente, die auf diese Komponente verweist, versehentlich unterbricht.</span><span class="sxs-lookup"><span data-stu-id="e3c32-132">Constraint components always need to be removed manually to ensure not accidentally breaking any other component referring to this component.</span></span>

### <a name="add-entry"></a><span data-ttu-id="e3c32-133">Eintrag hinzufügen</span><span class="sxs-lookup"><span data-stu-id="e3c32-133">Add entry</span></span>

<span data-ttu-id="e3c32-134">Durch Hinzufügen eines Eintrags wird eine Dropdownliste mit allen verfügbaren Einschränkungskomponenten geöffnet, die noch nicht in der manuellen Liste enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="e3c32-134">Add entry will open a dropdown showing all available constraint components that are not in the manual list yet.</span></span> <span data-ttu-id="e3c32-135">Durch Klicken auf einen der Einträge, die der manuellen Einschränkungsauswahl hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-135">By clicking on any of the entries that component will be added to the manual constraint selection.</span></span>

### <a name="add-new-constraint"></a><span data-ttu-id="e3c32-136">Hinzufügen einer neuen Einschränkung</span><span class="sxs-lookup"><span data-stu-id="e3c32-136">Add new constraint</span></span>

<span data-ttu-id="e3c32-137">Mit dieser Option wird dem Spielobjekt eine Komponente des ausgewählten Typs und die neu erstellte Einschränkungskomponente der Liste der manuellen Einschränkungen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e3c32-137">This option will add a component of the selected type to the game object and add the newly created constraint component to the manual constraint list.</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="e3c32-138">Transformieren von Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="e3c32-138">Transform constraints</span></span>

<span data-ttu-id="e3c32-139">Einschränkungen können verwendet werden, um die Bearbeitung auf irgendeine Weise zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="e3c32-139">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="e3c32-140">Einige Anwendungen erfordern z. B. möglicherweise eine Drehung, aber auch, dass das Objekt aufrecht bleibt.</span><span class="sxs-lookup"><span data-stu-id="e3c32-140">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="e3c32-141">In diesem Fall kann dem -Objekt ein hinzugefügt und verwendet werden, um die Drehung auf die `RotationAxisConstraint` Drehung der y-Achse zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="e3c32-141">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="e3c32-142">MRTK bietet eine Reihe von Einschränkungen, die alle unten beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-142">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="e3c32-143">Es ist auch möglich, neue Einschränkungen zu definieren und diese zu verwenden, um ein eindeutiges Manipulationsverhalten zu erstellen, das für einige Anwendungen erforderlich sein kann.</span><span class="sxs-lookup"><span data-stu-id="e3c32-143">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="e3c32-144">Erstellen Sie hierzu ein Skript, das von erbt, [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) und implementieren Sie die abstrakte Eigenschaft und die abstrakte `ConstraintType` `ApplyConstraint` Methode.</span><span class="sxs-lookup"><span data-stu-id="e3c32-144">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="e3c32-145">Beim Hinzufügen einer neuen Einschränkung zum -Objekt sollte die Bearbeitung auf die definierte Weise eingeschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-145">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="e3c32-146">Diese neue Einschränkung sollte auch in der automatischen Auswahl des [Einschränkungs-Managers oder](#auto-constraint-selection) in der [Dropdownliste "Eintrag](#add-entry) hinzufügen" im manuellen Modus angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-146">This new constraint should also show in the constraint manager [auto selection](#auto-constraint-selection) or [add entry](#add-entry) dropdown in manual mode.</span></span>

<span data-ttu-id="e3c32-147">Alle vom MRTK bereitgestellten Einschränkungen haben die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="e3c32-147">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="hand-type"></a><span data-ttu-id="e3c32-148">Handtyp</span><span class="sxs-lookup"><span data-stu-id="e3c32-148">Hand Type</span></span>

<span data-ttu-id="e3c32-149">Gibt an, ob die Einschränkung für eine handändige, zweihändige oder beide Manipulationsarten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e3c32-149">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="e3c32-150">Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-150">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="e3c32-151">*Einhändig:* Die Einschränkung wird bei einer handhändigen Bearbeitung verwendet, sofern diese ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-151">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="e3c32-152">*Zweihändig:* Die Einschränkung wird während der zweihändigen Bearbeitung verwendet, sofern diese ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-152">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="e3c32-153">Näherungstyp</span><span class="sxs-lookup"><span data-stu-id="e3c32-153">Proximity Type</span></span>

<span data-ttu-id="e3c32-154">Gibt an, ob die Einschränkung für nahe, fern oder beide Arten von Bearbeitung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e3c32-154">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="e3c32-155">Da diese Eigenschaft ein Flag ist, können beide Optionen ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-155">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="e3c32-156">*Near*: Die Einschränkung wird während der nahezuen Bearbeitung verwendet, sofern diese option ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-156">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="e3c32-157">*Far:* Die Einschränkung wird bei der fernen Bearbeitung verwendet, sofern diese option ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-157">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="e3c32-158">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="e3c32-158">FaceUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

<span data-ttu-id="e3c32-159">Wenn diese Einschränkung an ein Objekt angefügt wird, wird die Drehung eingeschränkt, sodass das Objekt immer auf den Benutzer zu sehen ist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-159">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="e3c32-160">Dies ist nützlich für Slates oder Panels.</span><span class="sxs-lookup"><span data-stu-id="e3c32-160">This is useful for slates or panels.</span></span> <span data-ttu-id="e3c32-161">Die Eigenschaften `FaceUserConstraint` für lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e3c32-161">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="e3c32-162">Gesichtserkennung</span><span class="sxs-lookup"><span data-stu-id="e3c32-162">Face away</span></span>

<span data-ttu-id="e3c32-163">Das Objekt ist vom Benutzer entfernt, wenn "true" ist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-163">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="e3c32-164">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="e3c32-164">FixedDistanceConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

<span data-ttu-id="e3c32-165">Diese Einschränkung behebt den Abstand zwischen dem bearbeiteten Objekt und einer anderen Objekttransformation beim Start der Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="e3c32-165">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="e3c32-166">Dies ist nützlich für Verhaltensweisen wie das Korrigieren des Abstands zwischen dem bearbeiteten Objekt und der Kopftransformation.</span><span class="sxs-lookup"><span data-stu-id="e3c32-166">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="e3c32-167">Die Eigenschaften `FixedDistanceConstraint` für lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e3c32-167">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="e3c32-168">Einschränkungstransformation</span><span class="sxs-lookup"><span data-stu-id="e3c32-168">Constraint transform</span></span>

<span data-ttu-id="e3c32-169">Dies ist die andere Transformation, zu der das bearbeitete Objekt einen festen Abstand hat.</span><span class="sxs-lookup"><span data-stu-id="e3c32-169">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="e3c32-170">Der Standardwert ist die Kameratransformation.</span><span class="sxs-lookup"><span data-stu-id="e3c32-170">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="e3c32-171">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="e3c32-171">FixedRotationToUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

<span data-ttu-id="e3c32-172">Diese Einschränkung behebt die relative Drehung zwischen dem Benutzer und dem bearbeiteten Objekt, während es bearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="e3c32-172">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="e3c32-173">Dies ist für Tafeln oder Bereiche nützlich, da dadurch sichergestellt wird, dass das bearbeitete Objekt dem Benutzer immer das gleiche Gesicht zeigt wie zu Beginn der Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="e3c32-173">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="e3c32-174">die `FixedRotationToUserConstraint` keine eindeutigen Eigenschaften aufweist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-174">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="e3c32-175">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="e3c32-175">FixedRotationToWorldConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

<span data-ttu-id="e3c32-176">Diese Einschränkung behebt die globale Drehung des bearbeiteten Objekts, während es bearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="e3c32-176">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="e3c32-177">Dies kann in Fällen nützlich sein, in denen keine Drehung durch Manipulationen vermittelt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e3c32-177">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="e3c32-178">die `FixedRotationToWorldConstraint` keine eindeutigen Eigenschaften aufweist:</span><span class="sxs-lookup"><span data-stu-id="e3c32-178">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="e3c32-179">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="e3c32-179">MaintainApparentSizeConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

<span data-ttu-id="e3c32-180">Wenn diese Einschränkung an ein Objekt angefügt wird, behält sie unabhängig davon, wie weit das Objekt vom Benutzer entfernt ist, die gleiche offensichtliche Größe für den Benutzer bei (d. h., es nimmt den gleichen Anteil des Sichtfelds des Benutzers an).</span><span class="sxs-lookup"><span data-stu-id="e3c32-180">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="e3c32-181">Dies kann verwendet werden, um sicherzustellen, dass eine Tafel oder ein Textbereich während der Bearbeitung lesbar bleibt.</span><span class="sxs-lookup"><span data-stu-id="e3c32-181">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="e3c32-182">die `MaintainApparentSizeConstraint` keine eindeutigen Eigenschaften aufweist:</span><span class="sxs-lookup"><span data-stu-id="e3c32-182">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="e3c32-183">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="e3c32-183">MoveAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="e3c32-184">Diese Einschränkung kann verwendet werden, um zu korrigieren, auf welchen Achsen ein bearbeitetes Objekt verschoben werden kann.</span><span class="sxs-lookup"><span data-stu-id="e3c32-184">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="e3c32-185">Dies kann nützlich sein, um Objekte über der Oberfläche einer Ebene oder entlang einer Linie zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="e3c32-185">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="e3c32-186">Die Eigenschaften `MoveAxisConstraint` für lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e3c32-186">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="e3c32-187">Einschränkung bei der Bewegung</span><span class="sxs-lookup"><span data-stu-id="e3c32-187">Constraint on movement</span></span>

<span data-ttu-id="e3c32-188">Gibt an, auf welchen Achsen die Bewegung verhindert werden soll.</span><span class="sxs-lookup"><span data-stu-id="e3c32-188">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="e3c32-189">Standardmäßig sind diese Achsen global und nicht lokal, aber dies kann unten geändert werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-189">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="e3c32-190">Da diese Eigenschaft ein Flag ist, kann eine beliebige Anzahl von Optionen ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-190">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="e3c32-191">*X-Achse:* Die Bewegung entlang der X-Achse wird eingeschränkt, wenn sie ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-191">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="e3c32-192">*Y-Achse:* Die Bewegung entlang der y-Achse wird eingeschränkt, wenn sie ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-192">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="e3c32-193">*Z-Achse:* Die Bewegung entlang der Z-Achse wird eingeschränkt, wenn sie ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-193">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="e3c32-194">Verwenden von lokalem Speicherplatz für Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="e3c32-194">Use local space for constraint</span></span>

<span data-ttu-id="e3c32-195">Schränkt relative lokale Transformationsachsen des bearbeiteten Objekts ein, wenn true.</span><span class="sxs-lookup"><span data-stu-id="e3c32-195">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="e3c32-196">Der Standardwert ist gleich „False“.</span><span class="sxs-lookup"><span data-stu-id="e3c32-196">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="e3c32-197">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="e3c32-197">RotationAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

<span data-ttu-id="e3c32-198">Diese Einschränkung kann verwendet werden, um zu korrigieren, um welche Achsen ein bearbeitetes Objekt gedreht werden kann.</span><span class="sxs-lookup"><span data-stu-id="e3c32-198">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="e3c32-199">Dies kann nützlich sein, um ein bearbeitetes Objekt aufrecht zu halten, aber dennoch y-Achsenrotation zu ermöglichen, z. B. .</span><span class="sxs-lookup"><span data-stu-id="e3c32-199">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="e3c32-200">Die Eigenschaften `RotationAxisConstraint` für lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e3c32-200">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="e3c32-201">Einschränkung bei Drehung</span><span class="sxs-lookup"><span data-stu-id="e3c32-201">Constraint on rotation</span></span>

<span data-ttu-id="e3c32-202">Gibt an, um welche Achsen eine Drehung verhindert werden soll.</span><span class="sxs-lookup"><span data-stu-id="e3c32-202">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="e3c32-203">Standardmäßig sind diese Achsen global und nicht lokal, aber dies kann unten geändert werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-203">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="e3c32-204">Da diese Eigenschaft ein Flag ist, kann eine beliebige Anzahl von Optionen ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-204">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="e3c32-205">*Y-Achse:* Die Drehung um die y-Achse ist bei Auswahl von eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="e3c32-205">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="e3c32-206">*Z-Achse:* Die Drehung um die Z-Achse ist eingeschränkt, wenn ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="e3c32-206">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="e3c32-207">*X-Achse:* Die Drehung um die x-Achse ist eingeschränkt, wenn ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="e3c32-207">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="e3c32-208">Verwenden des lokalen Speicherplatzes für Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="e3c32-208">Use local space for constraint</span></span>

<span data-ttu-id="e3c32-209">Schränkt relativ die lokalen Transformationsachsen des bearbeiteten Objekts ein, wenn true ist.</span><span class="sxs-lookup"><span data-stu-id="e3c32-209">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="e3c32-210">Der Standardwert ist gleich „False“.</span><span class="sxs-lookup"><span data-stu-id="e3c32-210">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="e3c32-211">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="e3c32-211">MinMaxScaleConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

<span data-ttu-id="e3c32-212">Diese Einschränkung ermöglicht das Festlegen von Mindest- und Höchstwerten für die Skalierung des bearbeiteten Objekts.</span><span class="sxs-lookup"><span data-stu-id="e3c32-212">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="e3c32-213">Dies ist nützlich, um zu verhindern, dass Benutzer ein Objekt zu klein oder zu groß skalieren.</span><span class="sxs-lookup"><span data-stu-id="e3c32-213">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="e3c32-214">Die Eigenschaften für `MinMaxScaleConstraint` sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="e3c32-214">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="e3c32-215">Mindestskaliert</span><span class="sxs-lookup"><span data-stu-id="e3c32-215">Scale minimum</span></span>

<span data-ttu-id="e3c32-216">Der minimale Skalierungswert während der Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="e3c32-216">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="e3c32-217">Maximale Skalierung</span><span class="sxs-lookup"><span data-stu-id="e3c32-217">Scale maximum</span></span>

<span data-ttu-id="e3c32-218">Der maximale Skalierungswert während der Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="e3c32-218">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="e3c32-219">Relativ zum Anfangszustand</span><span class="sxs-lookup"><span data-stu-id="e3c32-219">Relative to initial state</span></span>

<span data-ttu-id="e3c32-220">True gibt an, dass die oben genannten Werte relativ zur anfänglichen Skalierung der Objekte interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="e3c32-220">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="e3c32-221">Andernfalls werden sie als absolute Skalierungswerte interpretiert.</span><span class="sxs-lookup"><span data-stu-id="e3c32-221">Otherwise they will be interpreted as absolute scale values.</span></span>
