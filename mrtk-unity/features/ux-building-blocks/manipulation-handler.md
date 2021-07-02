---
title: Manipulationshandler
description: Dokumentation zum Manipulationshandler in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Manipulation,
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176637"
---
# <a name="manipulation-handler"></a><span data-ttu-id="34c0e-104">Manipulationshandler</span><span class="sxs-lookup"><span data-stu-id="34c0e-104">Manipulation handler</span></span>

![Manipulationshandler](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="34c0e-106">Mit dem *ManipulationHandler-Skript* kann ein Objekt mit ein oder zwei Händen verschiebbar, skalierbar und rotierbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="34c0e-106">The *ManipulationHandler* script allows for an object to be made movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="34c0e-107">Die Bearbeitung kann so eingeschränkt werden, dass nur bestimmte Arten von Transformationen zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="34c0e-107">Manipulation can be restricted so that it only allows certain kinds of transformation.</span></span> <span data-ttu-id="34c0e-108">Das Skript arbeitet mit verschiedenen Eingabetypen, einschließlich HoloLens 2 artikulierten Handeingaben, Handlichtlicht, HoloLens Gesteneingabe (1. Generation) und immersiver Headset-Motion Controller-Eingabe.</span><span class="sxs-lookup"><span data-stu-id="34c0e-108">The script works with various types of inputs including HoloLens 2 articulated hand input, hand-rays, HoloLens (1st gen) gesture input, and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-manipulation-handler"></a><span data-ttu-id="34c0e-109">Verwenden des Manipulationshandlers</span><span class="sxs-lookup"><span data-stu-id="34c0e-109">How to use the manipulation handler</span></span>

<span data-ttu-id="34c0e-110">Fügen Sie die `ManipulationHandler` Skriptkomponente einem GameObject hinzu.</span><span class="sxs-lookup"><span data-stu-id="34c0e-110">Add the `ManipulationHandler` script component to a GameObject.</span></span> <span data-ttu-id="34c0e-111">Stellen Sie sicher, dass Sie dem Objekt auch einen Collider hinzufügen, der den ziehbaren Grenzen entspricht.</span><span class="sxs-lookup"><span data-stu-id="34c0e-111">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="34c0e-112">Damit das Objekt auf nahezu artikulierte Handeingaben reagiert, fügen Sie auch das `NearInteractionGrabbable` Skript hinzu.</span><span class="sxs-lookup"><span data-stu-id="34c0e-112">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

![Verwenden des Manipulationshandlers im Unity-Editor](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a><span data-ttu-id="34c0e-114">Inspektoreigenschaften</span><span class="sxs-lookup"><span data-stu-id="34c0e-114">Inspector properties</span></span>

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

<span data-ttu-id="34c0e-115">**Hosttransformation** Transformation, die gezogen wird.</span><span class="sxs-lookup"><span data-stu-id="34c0e-115">**Host Transform** Transform that will be dragged.</span></span> <span data-ttu-id="34c0e-116">Der Standardwert ist das -Objekt der Komponente.</span><span class="sxs-lookup"><span data-stu-id="34c0e-116">Defaults to the object of the component.</span></span>

<span data-ttu-id="34c0e-117">**Manipulationstyp** Gibt an, ob das Objekt mit einer Hand, zwei Händen oder beidem bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="34c0e-117">**Manipulation Type** Specifies whether the object can be manipulated using one hand, two hands, or both.</span></span>

* <span data-ttu-id="34c0e-118">*Nur einhändige*</span><span class="sxs-lookup"><span data-stu-id="34c0e-118">*One handed only*</span></span>
* <span data-ttu-id="34c0e-119">*Nur zweihändige*</span><span class="sxs-lookup"><span data-stu-id="34c0e-119">*Two handed only*</span></span>
* <span data-ttu-id="34c0e-120">*Ein- und Zweihändige*</span><span class="sxs-lookup"><span data-stu-id="34c0e-120">*One and Two handed*</span></span>

<span data-ttu-id="34c0e-121">**Zweihändige Manipulationstypen**</span><span class="sxs-lookup"><span data-stu-id="34c0e-121">**Two Handed Manipulation Type**</span></span>

* <span data-ttu-id="34c0e-122">*Skalierung:* Es ist nur die Skalierung zulässig.</span><span class="sxs-lookup"><span data-stu-id="34c0e-122">*Scale*: Only scaling is allowed.</span></span>
* <span data-ttu-id="34c0e-123">*Rotieren:* Es ist nur die Drehung zulässig.</span><span class="sxs-lookup"><span data-stu-id="34c0e-123">*Rotate*: Only rotation is allowed.</span></span>
* <span data-ttu-id="34c0e-124">*Skalierung verschieben:* Verschieben und Skalieren ist zulässig.</span><span class="sxs-lookup"><span data-stu-id="34c0e-124">*Move Scale*: Moving and scaling is allowed.</span></span>
* <span data-ttu-id="34c0e-125">*Move Rotate*:Verschieben und Drehen ist zulässig.</span><span class="sxs-lookup"><span data-stu-id="34c0e-125">*Move Rotate*: Moving and rotating is allowed.</span></span>
* <span data-ttu-id="34c0e-126">*Skalierung drehen:* Rotieren und Skalieren ist zulässig.</span><span class="sxs-lookup"><span data-stu-id="34c0e-126">*Rotate Scale*: Rotating and scaling is allowed.</span></span>
* <span data-ttu-id="34c0e-127">*Skalierung verschieben:* Verschieben, Drehen und Skalieren ist zulässig.</span><span class="sxs-lookup"><span data-stu-id="34c0e-127">*Move Rotate Scale*: Moving, rotating and scaling is allowed.</span></span>

![Manipulationshandler](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

<span data-ttu-id="34c0e-129">**Far Manipulation zulassen** Gibt an, ob die Bearbeitung mithilfe der fernen Interaktion mit Zeigern erfolgen kann.</span><span class="sxs-lookup"><span data-stu-id="34c0e-129">**Allow Far Manipulation** Specifies whether manipulation can be done using far interaction with pointers.</span></span>

<span data-ttu-id="34c0e-130">**One-Hand-Drehungsmodus in der Nähe** Gibt an, wie sich das Objekt verhält, wenn es mit einer Hand oder einem Controller in der Nähe gepackt wird.</span><span class="sxs-lookup"><span data-stu-id="34c0e-130">**One Hand Rotation Mode Near** Specifies how the object will behave when it is being grabbed with one hand / controller near.</span></span>

<span data-ttu-id="34c0e-131">**One Hand Rotation Mode Far** Gibt an, wie sich das Objekt verhält, wenn es mit einer Hand/einem Controller im Abstand gepackt wird.</span><span class="sxs-lookup"><span data-stu-id="34c0e-131">**One Hand Rotation Mode Far** Specifies how the object will behave when it is being grabbed with one hand / controller at distance.</span></span>

<span data-ttu-id="34c0e-132">**Optionen für den One-Hand-Drehungsmodus** Gibt an, wie das Objekt gedreht wird, wenn es mit einer Hand gepackt wird.</span><span class="sxs-lookup"><span data-stu-id="34c0e-132">**One Hand Rotation Mode Options** Specifies how the object will rotate when it is being grabbed with one hand.</span></span>

* <span data-ttu-id="34c0e-133">*Ursprüngliche Drehung beibehalten:* Das Objekt wird beim Verschieben nicht gedreht.</span><span class="sxs-lookup"><span data-stu-id="34c0e-133">*Maintain original rotation*: Does not rotate object as it is being moved</span></span>
* <span data-ttu-id="34c0e-134">*Rotation zum Benutzer beibehalten:* Behält die ursprüngliche Drehung des Objekts für die X/Y-Achse für den Benutzer bei.</span><span class="sxs-lookup"><span data-stu-id="34c0e-134">*Maintain rotation to user*: Maintains the object's original rotation for X/Y axis to the user</span></span>
* <span data-ttu-id="34c0e-135">Die ausrichtung der *Schwerkraft behält die Rotation zum Benutzer* bei: Behält die ursprüngliche Drehung des Objekts zum Benutzer bei, macht das Objekt jedoch vertikal.</span><span class="sxs-lookup"><span data-stu-id="34c0e-135">*Gravity aligned maintain rotation to user*: Maintains object's original rotation to user, but makes the object vertical.</span></span> <span data-ttu-id="34c0e-136">Nützlich für Objekte mit einem Begrenzungssteuerelement.</span><span class="sxs-lookup"><span data-stu-id="34c0e-136">Useful for objects with a bounds control.</span></span>
* <span data-ttu-id="34c0e-137">*Gesichtsbenutzer:* Stellt sicher, dass das Objekt dem Benutzer immer gegenübersteht.</span><span class="sxs-lookup"><span data-stu-id="34c0e-137">*Face user*: Ensures object always faces the user.</span></span> <span data-ttu-id="34c0e-138">Nützlich für Slates/Panels.</span><span class="sxs-lookup"><span data-stu-id="34c0e-138">Useful for slates/panels.</span></span>
* <span data-ttu-id="34c0e-139">*Gesichtsabsicht vom Benutzer:* Stellt sicher, dass das Objekt immer vom Benutzer entfernt ist.</span><span class="sxs-lookup"><span data-stu-id="34c0e-139">*Face away from user*: Ensures object always faces away from user.</span></span> <span data-ttu-id="34c0e-140">Nützlich für Slates/Panels, die rückwärts konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="34c0e-140">Useful for slates/panels that are configured backwards.</span></span>
* <span data-ttu-id="34c0e-141">*Drehen um den Objektmittelpunkt:* Funktioniert nur für artikulierte Hände/Controller.</span><span class="sxs-lookup"><span data-stu-id="34c0e-141">*Rotate about object center*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="34c0e-142">Drehen Sie das Objekt mithilfe der Drehung der Hand/des Controllers, aber um den Objektmittelpunkt.</span><span class="sxs-lookup"><span data-stu-id="34c0e-142">Rotate object using rotation of the hand/controller, but about the object center point.</span></span> <span data-ttu-id="34c0e-143">Nützlich für die Untersuchung in einer Entfernung.</span><span class="sxs-lookup"><span data-stu-id="34c0e-143">Useful for inspecting at a distance.</span></span>
* <span data-ttu-id="34c0e-144">*Drehen um Denkpunkt:* Funktioniert nur für artikulierte Hände/Controller.</span><span class="sxs-lookup"><span data-stu-id="34c0e-144">*Rotate about grab point*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="34c0e-145">Drehen Sie das Objekt so, als ob es von Hand/Controller gehalten würde.</span><span class="sxs-lookup"><span data-stu-id="34c0e-145">Rotate object as if it was being held by hand/controller.</span></span> <span data-ttu-id="34c0e-146">Nützlich für die Überprüfung.</span><span class="sxs-lookup"><span data-stu-id="34c0e-146">Useful for inspection.</span></span>

<span data-ttu-id="34c0e-147">**Releaseverhalten** Wenn ein Objekt freigegeben wird, geben Sie sein physisches Bewegungsverhalten an.</span><span class="sxs-lookup"><span data-stu-id="34c0e-147">**Release Behavior** When an object is released, specify its physical movement behavior.</span></span> <span data-ttu-id="34c0e-148">Erfordert, dass sich eine starre Komponente auf diesem Objekt befindet.</span><span class="sxs-lookup"><span data-stu-id="34c0e-148">Requires a rigidbody component to be on that object.</span></span>

* <span data-ttu-id="34c0e-149">*Nichts*</span><span class="sxs-lookup"><span data-stu-id="34c0e-149">*Nothing*</span></span>
* <span data-ttu-id="34c0e-150">*Alles*</span><span class="sxs-lookup"><span data-stu-id="34c0e-150">*Everything*</span></span>
* <span data-ttu-id="34c0e-151">*Keep Velocity*</span><span class="sxs-lookup"><span data-stu-id="34c0e-151">*Keep Velocity*</span></span>
* <span data-ttu-id="34c0e-152">*Angular Geschwindigkeit beibehalten*</span><span class="sxs-lookup"><span data-stu-id="34c0e-152">*Keep Angular Velocity*</span></span>

<span data-ttu-id="34c0e-153">**Einschränkungen bei der Drehung** Gibt an, auf welcher Achse das Objekt gedreht wird, wenn es mit interagiert.</span><span class="sxs-lookup"><span data-stu-id="34c0e-153">**Constraints on Rotation** Specifies on which axis the object will rotate when interacted with.</span></span>

* <span data-ttu-id="34c0e-154">*Keine*</span><span class="sxs-lookup"><span data-stu-id="34c0e-154">*None*</span></span>
* <span data-ttu-id="34c0e-155">*Nur X-Achse*</span><span class="sxs-lookup"><span data-stu-id="34c0e-155">*X-Axis Only*</span></span>
* <span data-ttu-id="34c0e-156">*Nur Y-Achse*</span><span class="sxs-lookup"><span data-stu-id="34c0e-156">*Y-Axis Only*</span></span>
* <span data-ttu-id="34c0e-157">*Nur Z-Achse*</span><span class="sxs-lookup"><span data-stu-id="34c0e-157">*Z-Axis Only*</span></span>

<span data-ttu-id="34c0e-158">**Verwenden des lokalen Speicherplatzes für Einschränkungen** Ein Umschalter zwischen der Anwendung von Einschränkungen in Bezug auf die Weltraumachse oder der lokalen Raumachse.</span><span class="sxs-lookup"><span data-stu-id="34c0e-158">**Use Local Space For Constraint** A toggle to switch between applying constraints in respect to world-space axis, or local space axis.</span></span>

<span data-ttu-id="34c0e-159">**Einschränkungen bei Der Verschiebung**</span><span class="sxs-lookup"><span data-stu-id="34c0e-159">**Constraints on Movement**</span></span>

* <span data-ttu-id="34c0e-160">*Keine*</span><span class="sxs-lookup"><span data-stu-id="34c0e-160">*None*</span></span>
* <span data-ttu-id="34c0e-161">*Korrigieren der Entfernung vom Kopf*</span><span class="sxs-lookup"><span data-stu-id="34c0e-161">*Fix distance from head*</span></span>

<span data-ttu-id="34c0e-162">**Glättung aktiv** Gibt an, ob die Glättung aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="34c0e-162">**Smoothing Active** Specifies whether smoothing is active.</span></span>

<span data-ttu-id="34c0e-163">**Smoothing Amount One Hand** Umfang der Glättung, die auf Die Bewegung, Skalierung und Drehung angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="34c0e-163">**Smoothing Amount One Hand** Amount of smoothing to apply to the movement, scale, rotation.</span></span> <span data-ttu-id="34c0e-164">Glättung von 0 bedeutet keine Glättung.</span><span class="sxs-lookup"><span data-stu-id="34c0e-164">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="34c0e-165">Max value bedeutet, dass keine Änderung am Wert vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="34c0e-165">Max value means no change to value.</span></span>

## <a name="events"></a><span data-ttu-id="34c0e-166">Ereignisse</span><span class="sxs-lookup"><span data-stu-id="34c0e-166">Events</span></span>

<span data-ttu-id="34c0e-167">Der Manipulationshandler stellt die folgenden Ereignisse bereit:</span><span class="sxs-lookup"><span data-stu-id="34c0e-167">Manipulation handler provides the following events:</span></span>

* <span data-ttu-id="34c0e-168">*OnManipulationStarted:* Wird ausgelöst, wenn die Bearbeitung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="34c0e-168">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
* <span data-ttu-id="34c0e-169">*OnManipulationEnded:* Wird ausgelöst, wenn die Bearbeitung beendet wird.</span><span class="sxs-lookup"><span data-stu-id="34c0e-169">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
* <span data-ttu-id="34c0e-170">*OnHoverStarted:* Wird ausgelöst, wenn eine Hand bzw. ein Controller auf das manipulatierbare ,nah oder fern' zusteuert.</span><span class="sxs-lookup"><span data-stu-id="34c0e-170">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
* <span data-ttu-id="34c0e-171">*OnHoverEnded:* Wird ausgelöst, wenn ein Hand/Controller den Mauszeiger auf den manipulatierbaren , nahe oder fernen ziehbar hält.</span><span class="sxs-lookup"><span data-stu-id="34c0e-171">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>
