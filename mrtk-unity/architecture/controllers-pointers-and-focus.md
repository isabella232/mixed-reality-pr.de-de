---
title: Controller, Zeiger und Fokus
description: Interaktion mit Controllern, Zeigern und Fokus.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Zeiger, Controller
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121618"
---
# <a name="controllers-pointers-and-focus"></a><span data-ttu-id="3aec7-104">Controller, Zeiger und Fokus</span><span class="sxs-lookup"><span data-stu-id="3aec7-104">Controllers, pointers, and focus</span></span>

<span data-ttu-id="3aec7-105">Controller, Zeiger und Fokus sind übergeordnete Konzepte, die auf der Grundlage des Kerneingabesystems aufbauen.</span><span class="sxs-lookup"><span data-stu-id="3aec7-105">Controllers, pointers, and focus are higher-level concepts that build upon the foundation established by the core input system.</span></span> <span data-ttu-id="3aec7-106">Zusammen stellen sie einen großen Teil des Mechanismus für die Interaktion mit Objekten in der Szene bereit.</span><span class="sxs-lookup"><span data-stu-id="3aec7-106">Together, they provide a large portion of the mechanism for interacting with objects in the scene.</span></span>

## <a name="controllers"></a><span data-ttu-id="3aec7-107">Controller</span><span class="sxs-lookup"><span data-stu-id="3aec7-107">Controllers</span></span>

<span data-ttu-id="3aec7-108">Controller sind Darstellungen eines physischen Controllers (6-Grad an Freiheit, artikulierte Hand usw.).</span><span class="sxs-lookup"><span data-stu-id="3aec7-108">Controllers are representations of a physical controller (6-degrees of freedom, articulated hand, etc).</span></span> <span data-ttu-id="3aec7-109">Sie werden von Geräte-Managern erstellt und sind für die Kommunikation mit dem entsprechenden zugrunde liegenden System und die Übersetzung dieser Daten in MRTK-förmige Daten und Ereignisse verantwortlich.a</span><span class="sxs-lookup"><span data-stu-id="3aec7-109">They are created by device managers and are responsible for communicating with the corresponding underlying system and translating that data into MRTK-shaped data and events.a</span></span>

<span data-ttu-id="3aec7-110">Beispielsweise ist auf der Windows Mixed Reality-Plattform ein Controller, der für die [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) Verknüpfung mit den zugrunde liegenden Windows-APIs zur [Nachverfolgung](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) von Hand verantwortlich ist, um Informationen zu den Fugen, der Pose und anderen Eigenschaften der Hand abzurufen.</span><span class="sxs-lookup"><span data-stu-id="3aec7-110">For example, on the Windows Mixed Reality platform, the [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) is a controller that is responsible for interfacing with the underlying Windows [hand tracking APIs](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) to get information about the joints, pose, and other properties of the hand.</span></span> <span data-ttu-id="3aec7-111">Es ist dafür verantwortlich, diese Daten in relevante MRTK-Ereignisse zu verwandeln (z. B. durch Aufrufen von RaisePoseInputChanged oder RaiseHandJointsUpdated) und indem der interne Zustand aktualisiert wird, sodass Abfragen für [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) die richtigen Daten zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="3aec7-111">It is responsible for turning this data into relevant MRTK events (for example, by calling RaisePoseInputChanged or RaiseHandJointsUpdated) and by updating its own internal state so that queries for [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) will return correct data.</span></span>

<span data-ttu-id="3aec7-112">Im Allgemeinen umfasst der Lebenszyklus eines Controllers:</span><span class="sxs-lookup"><span data-stu-id="3aec7-112">Generally, a controller's lifecycle will involve:</span></span>

1. <span data-ttu-id="3aec7-113">Ein Controller wird von einem Geräte-Manager erstellt, wenn eine neue Quelle erkannt wird (der Geräte-Manager erkennt z. B. eine Hand und beginnt damit, sie nachzuverfolgen).</span><span class="sxs-lookup"><span data-stu-id="3aec7-113">A controller gets created by a device manager upon detection of a new source (for example, the device manager detects and starts tracking a hand).</span></span>

2. <span data-ttu-id="3aec7-114">In der Update()-Schleife des Controllers ruft er das zugrunde liegende API-System auf.</span><span class="sxs-lookup"><span data-stu-id="3aec7-114">In the controller's Update() loop, it calls into its underlying API system.</span></span>

3. <span data-ttu-id="3aec7-115">In derselben Updateschleife löst sie Änderungen an Eingabeereignissen aus, indem direkt in das Kerneingabesystem selbst aufgerufen wird (z. B. durch Auslösen von HandMeshUpdated oder HandJointsUpdated).</span><span class="sxs-lookup"><span data-stu-id="3aec7-115">In the same update loop, it raises input event changes by calling directly into the core input system itself (for example, raising HandMeshUpdated, or HandJointsUpdated).</span></span>

## <a name="pointers-and-focus"></a><span data-ttu-id="3aec7-116">Zeiger und Fokus</span><span class="sxs-lookup"><span data-stu-id="3aec7-116">Pointers and focus</span></span>

<span data-ttu-id="3aec7-117">Zeiger werden für die Interaktion mit Spielobjekten verwendet.</span><span class="sxs-lookup"><span data-stu-id="3aec7-117">Pointers are used to interact with game objects.</span></span> <span data-ttu-id="3aec7-118">In diesem Abschnitt wird beschrieben, wie Zeiger erstellt werden, wie sie aktualisiert werden und wie sie die Objekte bestimmen, die sich im Fokus befinden.</span><span class="sxs-lookup"><span data-stu-id="3aec7-118">This section describes how pointers are created, how they get updated, and how they determine the object(s) that are in focus.</span></span> <span data-ttu-id="3aec7-119">Außerdem werden die verschiedenen Typen vorhandener Zeiger und die Szenarien behandelt, in denen sie aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="3aec7-119">It will also cover the different types of pointers that exist and the scenarios in which they are active.</span></span>

### <a name="pointer-categories"></a><span data-ttu-id="3aec7-120">Zeigerkategorien</span><span class="sxs-lookup"><span data-stu-id="3aec7-120">Pointer categories</span></span>

<span data-ttu-id="3aec7-121">Zeiger fallen im Allgemeinen in eine der folgenden Kategorien:</span><span class="sxs-lookup"><span data-stu-id="3aec7-121">Pointers generally fall into one of the following categories:</span></span>

- <span data-ttu-id="3aec7-122">**Fernzeiger**</span><span class="sxs-lookup"><span data-stu-id="3aec7-122">**Far pointers**</span></span>

  <span data-ttu-id="3aec7-123">Diese Typen von Zeigern werden verwendet, um mit Objekten zu interagieren, die weit vom Benutzer entfernt sind (weit entfernt wird einfach als "nicht nah" definiert).</span><span class="sxs-lookup"><span data-stu-id="3aec7-123">These types of pointers are used to interact with objects that are far away from the user (far away is defined as simply “not near”).</span></span> <span data-ttu-id="3aec7-124">Diese Zeigertypen geben im Allgemeinen Linien um, die weit in die Welt gehen können und es dem Benutzer ermöglichen, mit Objekten zu interagieren und diese zu bearbeiten, die sich nicht direkt daneben befinden.</span><span class="sxs-lookup"><span data-stu-id="3aec7-124">These types of pointers generally cast lines that can go far into the world and allow the user to interact with and manipulate objects that are not immediately next to them.</span></span>

- <span data-ttu-id="3aec7-125">**Zeiger in der Nähe**</span><span class="sxs-lookup"><span data-stu-id="3aec7-125">**Near pointers**</span></span>

  <span data-ttu-id="3aec7-126">Diese Zeigertypen werden verwendet, um mit Objekten zu interagieren, die dem Benutzer nahe genug sind, um sie zu greifen, zu berühren und zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="3aec7-126">These types of pointers are used to interact with objects that are close enough to the user to grab, touch, and manipulate.</span></span> <span data-ttu-id="3aec7-127">Im Allgemeinen interagieren diese Typen von Zeigern mit Objekten, indem sie nach Objekten in der Nähe suchen (entweder durch Raycasting in kleinen Abständen, durch Sphärische Umwandlung nach Objekten in der Nähe oder durch Auflisten von Listen von Objekten, die als greifbar/berührbar angesehen werden).</span><span class="sxs-lookup"><span data-stu-id="3aec7-127">Generally, these types of pointers interact with objects by looking for objects in the nearby vicinity (either by doing raycasting at small distances, doing spherical casting looking for objects in the vicinity, or enumerating lists of objects that are considered grabbable/touchable).</span></span>

- <span data-ttu-id="3aec7-128">**Teleportzeiger**</span><span class="sxs-lookup"><span data-stu-id="3aec7-128">**Teleport pointers**</span></span>

  <span data-ttu-id="3aec7-129">Diese Typen von Zeigern werden in das Teleportierungssystem integriert, um das Verschieben des Benutzers an die Position des Zeigers zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="3aec7-129">These types of pointers plug into the teleportation system to handle moving the user to the location targeted by the pointer.</span></span>

## <a name="pointer-mediation"></a><span data-ttu-id="3aec7-130">Zeigerzeiger</span><span class="sxs-lookup"><span data-stu-id="3aec7-130">Pointer mediation</span></span>

<span data-ttu-id="3aec7-131">Da ein einzelner Controller über mehrere Zeiger verfügen kann (z. B. kann die artikulierte Hand sowohl nah als auch fern Interaktionszeiger aufweisen), gibt es eine Komponente, die für die Vermittlung des aktiven Zeigers verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="3aec7-131">Because a single controller can have multiple pointers (for example, the articulated hand can have both near and far interaction pointers), there exists a component that is responsible for mediating which pointer should be active.</span></span>

<span data-ttu-id="3aec7-132">Wenn sich die Hand des Benutzers beispielsweise einer betätigbaren Schaltfläche nähert, [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) sollte die angezeigt werden, und die sollte [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) eingeschaltet werden.</span><span class="sxs-lookup"><span data-stu-id="3aec7-132">For example, as the user’s hand approaches a pressable button, the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) should stop showing, and the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) should be engaged.</span></span>

<span data-ttu-id="3aec7-133">Dies wird von der [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) behandelt, die basierend auf dem Zustand aller Zeiger bestimmt, welche Zeiger aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="3aec7-133">This is handled by the [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator), which is responsible for determining which pointers are active, based on the state of all pointers.</span></span> <span data-ttu-id="3aec7-134">Einer der wichtigsten Dinge, die dies macht, ist das Deaktivieren von Fernzeigern, wenn sich ein Zeiger in der Nähe eines Objekts befindet (siehe [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).</span><span class="sxs-lookup"><span data-stu-id="3aec7-134">One of the key things this does is disable far pointers when a near pointer is close to an object (please see [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)).</span></span>

<span data-ttu-id="3aec7-135">Es ist möglich, eine alternative Implementierung des Zeigermediators bereitzustellen, indem Sie die [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) -Eigenschaft im Zeigerprofil ändern.</span><span class="sxs-lookup"><span data-stu-id="3aec7-135">It's possible to provide an alternate implementation of the pointer mediator by changing the [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) property on the pointer profile.</span></span>

### <a name="how-to-disable-pointers"></a><span data-ttu-id="3aec7-136">Deaktivieren von Zeigern</span><span class="sxs-lookup"><span data-stu-id="3aec7-136">How to disable pointers</span></span>

<span data-ttu-id="3aec7-137">Da der Zeigermediator jeden Frame ausführt, steuert er am Ende den aktiven/inaktiven Zustand aller Zeiger.</span><span class="sxs-lookup"><span data-stu-id="3aec7-137">Because the pointer mediator runs every frame, it ends up controlling the active / inactive state of all pointers.</span></span> <span data-ttu-id="3aec7-138">Wenn Sie daher die IsInteractionEnabled-Eigenschaft eines Zeigers im Code festlegen, wird sie vom Zeigermediator in jedem Frame überschrieben.</span><span class="sxs-lookup"><span data-stu-id="3aec7-138">Therefore, if you set a pointer's IsInteractionEnabled property in code, it will get overwritten by the pointer mediator every frame.</span></span> <span data-ttu-id="3aec7-139">Stattdessen können Sie den angeben, [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) um zu steuern, ob Zeiger selbst ein- oder ausgeschaltet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="3aec7-139">Instead, you can specify the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) to control whether pointers should be on or off yourself.</span></span> <span data-ttu-id="3aec7-140">Beachten Sie, dass dies nur funktioniert, wenn Sie die Standardeinstellung [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) und [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK verwenden.</span><span class="sxs-lookup"><span data-stu-id="3aec7-140">Note that this will only work if you are using the default [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) and [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span></span>

#### <a name="example-disable-hand-rays-in-mrtk"></a><span data-ttu-id="3aec7-141">Beispiel: Deaktivieren von Handlichtlicht im MRTK</span><span class="sxs-lookup"><span data-stu-id="3aec7-141">Example: Disable hand rays in MRTK</span></span>

<span data-ttu-id="3aec7-142">Mit dem folgenden Code wird der Handstrahl im MRTK deaktiviert:</span><span class="sxs-lookup"><span data-stu-id="3aec7-142">The following code will turn off the hand rays in MRTK:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

<span data-ttu-id="3aec7-143">Der folgende Code gibt Handlichter an ihr Standardverhalten im MRTK zurück:</span><span class="sxs-lookup"><span data-stu-id="3aec7-143">The following code will return hand rays to their default behavior in MRTK:</span></span>

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

<span data-ttu-id="3aec7-144">Der folgende Code zwingt den Handlichtstrahl, unabhängig davon, ob er sich in der Nähe eines Greifens befindet:</span><span class="sxs-lookup"><span data-stu-id="3aec7-144">The following code will force hand rays to be on, regardless if near a grabbable:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="3aec7-145">Weitere Beispiele finden Sie unter [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) und [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) .</span><span class="sxs-lookup"><span data-stu-id="3aec7-145">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

### <a name="focusprovider"></a><span data-ttu-id="3aec7-146">FocusProvider</span><span class="sxs-lookup"><span data-stu-id="3aec7-146">FocusProvider</span></span>

<span data-ttu-id="3aec7-147">[`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)ist das Arbeitstier, das für das Iterieren der Liste aller Zeiger und das Herausfinden, was das fokussierte Objekt für jeden Zeiger ist, verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="3aec7-147">The [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) is the workhorse that is responsible for iterating over the list of all pointers and figuring out what the focused object is for each pointer.</span></span>

<span data-ttu-id="3aec7-148">Bei jedem `Update()` Aufruf geschieht Dies:</span><span class="sxs-lookup"><span data-stu-id="3aec7-148">In each `Update()` call, this will:</span></span>

1. <span data-ttu-id="3aec7-149">Aktualisieren Sie alle Zeiger, indem Sie Raycasting durchführen und die Treffererkennung wie vom Zeiger selbst konfiguriert durchführen (beispielsweise könnte der Kugelzeiger den SphereOverlap-RaycastMode angeben, sodass FocusProvider einen kugelbasierten Konflikt erzeugt).</span><span class="sxs-lookup"><span data-stu-id="3aec7-149">Update all of the pointers, by raycasting and doing hit detection as-configured by the pointer itself (for example, the sphere pointer could specify the SphereOverlap raycastMode, so FocusProvider will do a sphere-based collision)</span></span>

2. <span data-ttu-id="3aec7-150">Aktualisieren Sie das fokussierte Objekt auf Zeigerbasis (d. h., wenn ein Objekt den Fokus erhält, löst es auch Ereignisse für dieses Objekt aus, wenn ein Objekt den Fokus verliert, würde es den Fokus verlieren usw.).</span><span class="sxs-lookup"><span data-stu-id="3aec7-150">Update the focused object on a per-pointer basis (i.e. if an object gained focus, it would also trigger events to those object, if an object lost focus, it would trigger focus lost, etc).</span></span>

### <a name="pointer-configuration-and-lifecycle"></a><span data-ttu-id="3aec7-151">Zeigerkonfiguration und -lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="3aec7-151">Pointer configuration and lifecycle</span></span>

<span data-ttu-id="3aec7-152">Zeiger können im Abschnitt *Zeiger* des Eingabesystemprofils [konfiguriert werden.](../features/input/pointers.md)</span><span class="sxs-lookup"><span data-stu-id="3aec7-152">[Pointers can be configured](../features/input/pointers.md) in the *Pointers* section of the input system profile.</span></span>

<span data-ttu-id="3aec7-153">Die Lebensdauer eines Zeigers sieht im Allgemeinen wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3aec7-153">The lifetime of a pointer is generally the following:</span></span>

1. <span data-ttu-id="3aec7-154">Ein Geräte-Manager erkennt das Vorhandensein eines Controllers.</span><span class="sxs-lookup"><span data-stu-id="3aec7-154">A device manager will detect the presence of a controller.</span></span> <span data-ttu-id="3aec7-155">Dieser Geräte-Manager erstellt dann den Satz von Zeigern, die dem Controller zugeordnet sind, über einen Aufruf von [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="3aec7-155">This device manager will then create the set of pointers associated with the controller via a call to [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager).</span></span>

2. <span data-ttu-id="3aec7-156">Der FocusProvider durchläuft in seiner Update()-Schleife alle gültigen Zeiger und führt die zugeordnete Raycast- oder Treffererkennungslogik aus.</span><span class="sxs-lookup"><span data-stu-id="3aec7-156">The FocusProvider, in its Update() loop, will iterate over all of the valid pointers and do the associated raycast or hit detection logic.</span></span> <span data-ttu-id="3aec7-157">Dies wird verwendet, um das Objekt zu bestimmen, das von jedem bestimmten Zeiger fokussiert wird.</span><span class="sxs-lookup"><span data-stu-id="3aec7-157">This is used to determine the object that is focused by each particular pointer.</span></span>

    - <span data-ttu-id="3aec7-158">Da mehrere Eingabequellen gleichzeitig aktiv sein können (z. B. zwei aktive Hände), ist es auch möglich, mehrere Objekte zu haben, die gleichzeitig den Fokus haben.</span><span class="sxs-lookup"><span data-stu-id="3aec7-158">Because it's possible to have multiple sources of input active at the same time (for example, two hands active present), it's also possible to have multiple objects that have focus at the same time.</span></span>

3. <span data-ttu-id="3aec7-159">Wenn der Geräte-Manager erkennt, dass eine Controllerquelle verloren gegangen ist, werden die Zeiger, die dem verlorenen Controller zugeordnet sind, abgeschaltet.</span><span class="sxs-lookup"><span data-stu-id="3aec7-159">The device manager, upon discovering that a controller source was lost, will tear down the pointers associated with the lost controller.</span></span>