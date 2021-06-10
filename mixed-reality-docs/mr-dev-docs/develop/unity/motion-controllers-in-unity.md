---
title: Motion-Controller in Unity
description: Erfahren Sie, wie Sie mithilfe von XR und allgemeinen Schaltflächen- und Achsen-APIs Aktionen für Ihre Anvis in Unity mit Motion Controller-Eingaben ergreifen.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Motion-Controller, Unity, Eingabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: ff1eedcc337edd2d7edfe8d961bb88bcb859cd23
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743486"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="2dfd2-104">Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="2dfd2-104">Motion controllers in Unity</span></span>

<span data-ttu-id="2dfd2-105">Es gibt zwei wichtige Möglichkeiten, um beim Anvieren [in Unity](gaze-in-unity.md)Aktionen zu [ergreifen:](../../design/gaze-and-commit.md#composite-gestures) Handgesten und [Motion-Controller](../../design/motion-controllers.md) in HoloLens und Immersive HMD.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="2dfd2-106">Sie greifen auf die Daten für beide Quellen räumlicher Eingaben über die gleichen APIs in Unity zu.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="2dfd2-107">Unity bietet zwei primäre Möglichkeiten für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="2dfd2-108">Die allgemeinen *Input.GetButton/Input.GetAxis-APIs* funktionieren über mehrere Unity XR SDKs hinweg, während die für Windows Mixed Reality spezifische *InteractionManager/GestureRecognizer-API* den vollständigen Satz räumlicher Eingabedaten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="2dfd2-109">Unity XR-Eingabe-APIs</span><span class="sxs-lookup"><span data-stu-id="2dfd2-109">Unity XR input APIs</span></span>

<span data-ttu-id="2dfd2-110">Für neue Projekte wird empfohlen, die neuen XR-Eingabe-APIs von Anfang an zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="2dfd2-111">Weitere Informationen zu den [XR-APIs finden Sie hier.](https://docs.unity3d.com/Manual/xr_input.html)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="2dfd2-112">Unity-Schaltflächen-/Achsenzuordnungstabelle</span><span class="sxs-lookup"><span data-stu-id="2dfd2-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="2dfd2-113">Der Eingabe-Manager für Windows Mixed Reality Motion-Controller von Unity unterstützt die unten aufgeführten Schaltflächen- und Achsen-IDs über die *Input.GetButton/GetAxis-APIs.*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="2dfd2-114">Die Spalte "Windows MR-spezifisch" bezieht sich auf Eigenschaften, die vom *Typ InteractionSourceState verfügbar* sind.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="2dfd2-115">Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="2dfd2-116">Die Schaltflächen-/Achsen-ID-Zuordnungen für Windows Mixed Reality im Allgemeinen mit den Oculus-Schaltflächen-/Achsen-IDs übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="2dfd2-117">Die Schaltflächen-/Achsen-ID-Zuordnungen für Windows Mixed Reality unterscheiden sich von den OpenVR-Zuordnungen auf zwei Arten:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="2dfd2-118">Die Zuordnung verwendet Touchpad-IDs, die sich von thumbstick unterscheiden, um Controller mit Thumbsticks und Touchpads zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="2dfd2-119">Die Zuordnung vermeidet das Überladen der A- und X-Schaltflächen-IDs für die Menüschaltflächen, damit sie für die physischen ABXY-Schaltflächen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="2dfd2-120">Eingabe</span><span class="sxs-lookup"><span data-stu-id="2dfd2-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="2dfd2-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a></span><span class="sxs-lookup"><span data-stu-id="2dfd2-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="2dfd2-122">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="2dfd2-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-spezifische Eingabe-API</a></span><span class="sxs-lookup"><span data-stu-id="2dfd2-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="2dfd2-124">(XR. WSA. Eingabe)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="2dfd2-125">Linken</span><span class="sxs-lookup"><span data-stu-id="2dfd2-125">Left hand</span></span> </th><th> <span data-ttu-id="2dfd2-126">Rechte Hand</span><span class="sxs-lookup"><span data-stu-id="2dfd2-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="2dfd2-127">Auswählen des gedrückten Triggers</span><span class="sxs-lookup"><span data-stu-id="2dfd2-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="2dfd2-128">Achse 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="2dfd2-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="2dfd2-129">Achse 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="2dfd2-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="2dfd2-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="2dfd2-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-131">Auswählen des analogen Triggerwerts</span><span class="sxs-lookup"><span data-stu-id="2dfd2-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="2dfd2-132">Achse 9</span><span class="sxs-lookup"><span data-stu-id="2dfd2-132">Axis 9</span></span> </td><td> <span data-ttu-id="2dfd2-133">Achse 10</span><span class="sxs-lookup"><span data-stu-id="2dfd2-133">Axis 10</span></span> </td><td> <span data-ttu-id="2dfd2-134">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="2dfd2-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-135">Select trigger partially pressed (Trigger teilweise gedrückt auswählen)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="2dfd2-136">Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="2dfd2-137">Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="2dfd2-138">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="2dfd2-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-139">Menüschaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="2dfd2-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="2dfd2-140">Schaltfläche 6\*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-140">Button 6\*</span></span> </td><td> <span data-ttu-id="2dfd2-141">Schaltfläche 7\*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-141">Button 7\*</span></span> </td><td> <span data-ttu-id="2dfd2-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="2dfd2-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-143">Greiftaste gedrückt</span><span class="sxs-lookup"><span data-stu-id="2dfd2-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="2dfd2-144">Achse 11 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="2dfd2-145">Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="2dfd2-146">Achse 12 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="2dfd2-147">Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="2dfd2-148">Begriffen</span><span class="sxs-lookup"><span data-stu-id="2dfd2-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="2dfd2-150">Achse 1</span><span class="sxs-lookup"><span data-stu-id="2dfd2-150">Axis 1</span></span> </td><td> <span data-ttu-id="2dfd2-151">Achse 4</span><span class="sxs-lookup"><span data-stu-id="2dfd2-151">Axis 4</span></span> </td><td> <span data-ttu-id="2dfd2-152">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="2dfd2-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="2dfd2-154">Achse 2</span><span class="sxs-lookup"><span data-stu-id="2dfd2-154">Axis 2</span></span> </td><td> <span data-ttu-id="2dfd2-155">Achse 5</span><span class="sxs-lookup"><span data-stu-id="2dfd2-155">Axis 5</span></span> </td><td> <span data-ttu-id="2dfd2-156">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="2dfd2-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-157">Thumbstick pressed (Gedrückter Fingerabdruck)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="2dfd2-158">Schaltfläche 8</span><span class="sxs-lookup"><span data-stu-id="2dfd2-158">Button 8</span></span> </td><td> <span data-ttu-id="2dfd2-159">Schaltfläche 9</span><span class="sxs-lookup"><span data-stu-id="2dfd2-159">Button 9</span></span> </td><td> <span data-ttu-id="2dfd2-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="2dfd2-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-161">Touchpad X <i>(links: -1.0, rechts: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="2dfd2-162">Achse 17\*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="2dfd2-163">Achse 19\*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="2dfd2-164">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="2dfd2-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="2dfd2-166">Achse 18\*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="2dfd2-167">Achse 20\*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="2dfd2-168">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="2dfd2-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-169">Touchpad berührt</span><span class="sxs-lookup"><span data-stu-id="2dfd2-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="2dfd2-170">Schaltfläche 18\*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-170">Button 18\*</span></span> </td><td> <span data-ttu-id="2dfd2-171">Schaltfläche 19\*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-171">Button 19\*</span></span> </td><td> <span data-ttu-id="2dfd2-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="2dfd2-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-173">Touchpad gedrückt</span><span class="sxs-lookup"><span data-stu-id="2dfd2-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="2dfd2-174">Schaltfläche 16\*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-174">Button 16\*</span></span> </td><td> <span data-ttu-id="2dfd2-175">Schaltfläche 17\*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-175">Button 17\*</span></span> </td><td> <span data-ttu-id="2dfd2-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="2dfd2-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-177">6DoF-Greif- oder Zeigerpose</span><span class="sxs-lookup"><span data-stu-id="2dfd2-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="2dfd2-178"><i>Nur</i> Greifpose: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="2dfd2-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="2dfd2-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">Xr. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="2dfd2-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="2dfd2-180">Übergeben <i>Sie "Pointer"</i> oder <i>"Pointer"</i> als Argument: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="2dfd2-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="2dfd2-181">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="2dfd2-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-182">Nachverfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="2dfd2-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="2dfd2-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="2dfd2-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="2dfd2-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="2dfd2-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="2dfd2-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="2dfd2-186">Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für OpenVR verwendet, aufgrund von Kollisionen in den Zuordnungen, die von Gamepads, Oculus Touch und OpenVR verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="2dfd2-187">Greifpose im Vergleich zu zeigenden Posen</span><span class="sxs-lookup"><span data-stu-id="2dfd2-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="2dfd2-188">Windows Mixed Reality unterstützt Bewegungscontroller in einer Vielzahl von Formfaktoren.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="2dfd2-189">Der Entwurf jedes Controllers unterscheidet sich in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen "Vorwärtsrichtung", die Apps verwenden sollten, um beim Rendern des Controllers zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="2dfd2-190">Um diese Controller besser darstellen zu können, gibt es zwei  Arten von Posen, die Sie für jede Interaktionsquelle untersuchen können: die Greifpose und die **Zeigerpose.**</span><span class="sxs-lookup"><span data-stu-id="2dfd2-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="2dfd2-191">Die Greif- und Zeiger-Posenkoordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="2dfd2-192">Greifpose</span><span class="sxs-lookup"><span data-stu-id="2dfd2-192">Grip pose</span></span>

<span data-ttu-id="2dfd2-193">Die **Greifhaltung** stellt die Position der Benutzerfläche dar, die entweder von einer HoloLens erkannt wird oder einen Bewegungscontroller hält.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="2dfd2-194">Bei immersiven Headsets wird die Greifpose am besten verwendet, um die Hand des Benutzers oder ein Objekt in der Hand des **Benutzers zu rendern.** </span><span class="sxs-lookup"><span data-stu-id="2dfd2-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="2dfd2-195">Die Greifpose wird auch beim Visualisieren eines Bewegungscontrollers verwendet.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="2dfd2-196">Das **renderbare Modell, das** von Windows für einen Bewegungscontroller bereitgestellt wird, verwendet die Greifpose als Ursprung und Drehzentrum.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="2dfd2-197">Die Greifpose ist wie folgt speziell definiert:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="2dfd2-198">Die **Greifposition:** Der Handflächenschwerpunkt, wenn der Controller natürlich hält, nach links oder rechts angepasst, um die Position innerhalb des Greifs zu zentriert.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="2dfd2-199">Auf dem Windows Mixed Reality Motion-Controller wird diese Position in der Regel an der Schaltfläche Greiftaste ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="2dfd2-200">Die **rechte** Achse der Greifausrichtung: Wenn Sie Ihre Hand vollständig öffnen, um eine flache 5-Finger-Pose zu bilden, den Strahl, der normal zu Ihrer Handfläche ist (vorwärts von der linken Handfläche, rückwärts von der rechten Handfläche).</span><span class="sxs-lookup"><span data-stu-id="2dfd2-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="2dfd2-201">**Die Vorwärtsachse der Klammerausrichtung:** Wenn Sie Ihre Hand teilweise schließen (so als ob sie den Controller hält), zeigt der Strahl, der "vorwärts" durch die Von den Nichtfingerfingern gebildeten Strahl zeigt.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="2dfd2-202">Die **Nach-oben-Achse der Klammerausrichtung:** Die nach oben-Achse, die durch die Definitionen Rechts und Vorwärts impliziert wird.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="2dfd2-203">Sie können über die anbieterübergreifende Eingabe-API von Unity ( XR) auf die Klammerhaltung *[zugreifen. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) oder über die MR-spezifische Windows-API (*sourceState.sourcePose.TryGetPosition/Rotation*, anfordern von Pose-Daten für den **Klammerknoten).**</span><span class="sxs-lookup"><span data-stu-id="2dfd2-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="2dfd2-204">Zeigerpose</span><span class="sxs-lookup"><span data-stu-id="2dfd2-204">Pointer pose</span></span>

<span data-ttu-id="2dfd2-205">Die **Zeigerpose** stellt die Spitze des Controllers dar, der nach vorn zeigt.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="2dfd2-206">Die vom System bereitgestellte Zeigerpose wird am besten zum Raycasten verwendet, wenn Sie **das Controllermodell selbst rendern.**</span><span class="sxs-lookup"><span data-stu-id="2dfd2-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="2dfd2-207">Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers rendern, z. B. ein virtuelles Geschütz, sollten Sie mit einem Strahl zeigen, der für dieses virtuelle Objekt am natürlichsten ist, z. B. ein Strahl, der entlang des Durchlaufs des von der App definierten Strahlmodells verläuft.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="2dfd2-208">Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das Verweisen auf das virtuelle Objekt wahrscheinlich natürlicher für Benutzer, die Ihre App verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="2dfd2-209">Derzeit ist die Zeigerhaltung in Unity nur über die Windows MR-spezifische API *sourceState.sourcePose.TryGetPosition/Rotation* verfügbar, wobei *InteractionSourceNode.Pointer* als Argument übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="2dfd2-210">Controller-Nachverfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="2dfd2-210">Controller tracking state</span></span>

<span data-ttu-id="2dfd2-211">Wie die Headsets erfordert auch der Windows Mixed Reality Motion Controller keine Einrichtung externer Überwachungssensoren.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="2dfd2-212">Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="2dfd2-213">Wenn der Benutzer die Controller aus dem Ansichtsfeld des Headsets verschiebt, leitet Windows in den meisten Fällen weiterhin Controllerpositionen ab.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="2dfd2-214">Wenn der Controller die visuelle Nachverfolgung lange genug verloren hat, werden die Positionen des Controllers auf Positionen mit ungefährer Genauigkeit abgesenkt.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="2dfd2-215">An diesem Punkt sperrt das System den Controller für den Benutzer, verfolgt die Position des Benutzers, während er sich bewegt, während die tatsächliche Ausrichtung des Controllers weiterhin mit seinen internen Ausrichtungssensoren verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="2dfd2-216">Viele Apps, die Controller verwenden, um auf Benutzeroberflächenelemente zu zeigen und diese zu aktivieren, können normal und mit ungefährer Genauigkeit ausgeführt werden, ohne dass der Benutzer dies feststellen muss.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="2dfd2-217">Explizite Überlegungen zum Nachverfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="2dfd2-217">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="2dfd2-218">Apps, die Positionen basierend auf dem Nachverfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und Eigenschaften für den Zustand des Controllers überprüfen, z. B. *SourceLossRisk* und *PositionAccuracy:*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-218">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="2dfd2-219">Nachverfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="2dfd2-219">Tracking state</span></span> </th><th> <span data-ttu-id="2dfd2-220">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="2dfd2-220">SourceLossRisk</span></span> </th><th> <span data-ttu-id="2dfd2-221">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="2dfd2-221">PositionAccuracy</span></span> </th><th> <span data-ttu-id="2dfd2-222">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="2dfd2-222">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="2dfd2-223"><b>Hohe Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-223"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="2dfd2-224">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="2dfd2-224">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="2dfd2-225">Hoch</span><span class="sxs-lookup"><span data-stu-id="2dfd2-225">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="2dfd2-226">true</span><span class="sxs-lookup"><span data-stu-id="2dfd2-226">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-227"><b>Hohe Genauigkeit (verlustgefahrt)</b> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-227"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="2dfd2-228">== 1.0</span><span class="sxs-lookup"><span data-stu-id="2dfd2-228">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="2dfd2-229">Hoch</span><span class="sxs-lookup"><span data-stu-id="2dfd2-229">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="2dfd2-230">true</span><span class="sxs-lookup"><span data-stu-id="2dfd2-230">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-231"><b>Ungefähre Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-231"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="2dfd2-232">== 1.0</span><span class="sxs-lookup"><span data-stu-id="2dfd2-232">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="2dfd2-233">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="2dfd2-233">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="2dfd2-234">true</span><span class="sxs-lookup"><span data-stu-id="2dfd2-234">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2dfd2-235"><b>Keine Position</b> </span><span class="sxs-lookup"><span data-stu-id="2dfd2-235"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="2dfd2-236">== 1.0</span><span class="sxs-lookup"><span data-stu-id="2dfd2-236">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="2dfd2-237">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="2dfd2-237">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="2dfd2-238">false</span><span class="sxs-lookup"><span data-stu-id="2dfd2-238">false</span></span></td>
</tr>
</table>

<span data-ttu-id="2dfd2-239">Diese Nachverfolgungszustände des Motion-Controllers sind wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-239">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="2dfd2-240">**Hohe Genauigkeit:** Während sich der Bewegungscontroller im Ansichtsfeld des Headsets befindet, bietet er in der Regel basierend auf der visuellen Nachverfolgung positionen mit hoher Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-240">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="2dfd2-241">Ein sich bewegender Controller, der vorübergehend das Sichtfeld verlässt oder kurzzeitig von den Headsetsensoren verdeckt wird (z. B. durch die andere Seite des Benutzers), gibt weiterhin eine kurze Zeit lang hochgenaue Posen zurück, basierend auf der trägen Nachverfolgung des Controllers selbst.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-241">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="2dfd2-242">**Hohe Genauigkeit (verlustgefährdete):** Wenn der Benutzer den Motion-Controller hinter den Rand des Ansichtsfelds des Headsets bewegt, kann das Headset die Position des Controllers bald nicht mehr visuell nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-242">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="2dfd2-243">Die App weiß, wann der Controller diese FOV-Grenze erreicht hat, indem sie den **SourceLossRisk-Wert** 1.0 erreicht.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-243">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="2dfd2-244">An diesem Punkt kann die App Controllergesten anhalten, die einen stabilen Stream von hochwertigen Posen erfordern.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-244">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="2dfd2-245">**Ungefähre Genauigkeit:** Wenn der Controller die visuelle Nachverfolgung lange genug verloren hat, werden die Positionen des Controllers auf Positionen mit ungefährer Genauigkeit abgesenkt.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-245">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="2dfd2-246">An diesem Punkt sperrt das System den Controller für den Benutzer, verfolgt die Position des Benutzers, während er sich bewegt, während die tatsächliche Ausrichtung des Controllers weiterhin mit seinen internen Ausrichtungssensoren verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-246">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="2dfd2-247">Viele Apps, die Controller verwenden, um auf Benutzeroberflächenelemente zu zeigen und diese zu aktivieren, können normal und mit ungefährer Genauigkeit ausgeführt werden, ohne dass der Benutzer darauf hinweist.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-247">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="2dfd2-248">Apps mit größeren Eingabeanforderungen können diesen Abfall von **Hoher** Genauigkeit zu **Ungefähre** Genauigkeit durch Untersuchen der **PositionAccuracy-Eigenschaft** einsehen, um dem Benutzer z. B. während dieser Zeit einen freundlicheren Hitbox-Wert für Ziele außerhalb des Bildschirms zu geben.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-248">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="2dfd2-249">**Keine Position:** Der Controller kann zwar über einen längeren Zeitraum mit ungefährer Genauigkeit arbeiten, manchmal weiß das System jedoch, dass selbst eine durch Körper gesperrte Position im Moment nicht sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-249">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="2dfd2-250">Beispielsweise wurde ein controller, der aktiviert wurde, möglicherweise nie visuell beobachtet, oder ein Benutzer kann einen Controller abstellen, der dann von einer anderen Person übernommen wird.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-250">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="2dfd2-251">Zu diesen Zeiten stellt das System keine Position für die App bereit, und *TryGetPosition* gibt FALSE zurück.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-251">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="2dfd2-252">Allgemeine Unity-APIs (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-252">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="2dfd2-253">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-253">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="2dfd2-254">**Typen:** *Eingabe,* *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-254">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="2dfd2-255">Unity verwendet derzeit die allgemeinen *Input.GetButton/Input.GetAxis-APIs,* um Eingaben für [das Oculus SDK,](https://docs.unity3d.com/Manual/OculusControllers.html) [das OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality verfügbar zu machen, einschließlich Hände und Motion Controller.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-255">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="2dfd2-256">Wenn Ihre App diese APIs für die Eingabe verwendet, kann sie Motion-Controller problemlos über mehrere XR SDKs hinweg unterstützen, einschließlich Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-256">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="2dfd2-257">Abrufen des gedrückten Zustands einer logischen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="2dfd2-257">Getting a logical button's pressed state</span></span>

<span data-ttu-id="2dfd2-258">Um die allgemeinen Unity-Eingabe-APIs zu verwenden, beginnen Sie in der Regel damit, Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html)zu verkabeln und eine Schaltfläche oder Achsen-IDs an jeden Namen zu binden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-258">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="2dfd2-259">Anschließend können Sie Code schreiben, der auf diesen logischen Schaltflächen-/Achsennamen verweist.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-259">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="2dfd2-260">Um z. B. die Triggerschaltfläche des linken Bewegungscontrollers der Aktion Senden zuzuordnen, wechseln Sie zu **Bearbeiten > Projekteinstellungen > Eingabe** in Unity, und erweitern Sie die Eigenschaften des Abschnitts Senden unter Achsen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-260">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="2dfd2-261">Ändern Sie die Eigenschaft **Positive Schaltfläche** oder Alt **Positive Button** wie folgt, um **schaltfläche 14** zu lesen:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-261">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="2dfd2-262">![InputManager von Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-262">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="2dfd2-263&quot;>*Unity InputManager*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2dfd2-263&quot;>*Unity InputManager*</span></span>

<span data-ttu-id=&quot;2dfd2-264&quot;>Ihr Skript kann dann mit *Input.GetButton* nach der Aktion Senden suchen:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2dfd2-264&quot;>Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton(&quot;Submit"))
{
  // ...
}
```
<span data-ttu-id="2dfd2-265">Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **Eigenschaft Größe** unter **Achsen** ändern.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-265">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="2dfd2-266">Direktes Abrufen des gedrückten Zustands einer physischen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="2dfd2-266">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="2dfd2-267">Sie können auch manuell über ihren vollqualifizierten Namen auf Schaltflächen zugreifen, indem *Sie Input.GetKey* verwenden:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-267">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="2dfd2-268">Abrufen der Posen eines Hand- oder Bewegungscontrollers</span><span class="sxs-lookup"><span data-stu-id="2dfd2-268">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="2dfd2-269">Sie können mit XR auf die Position und Drehung des Controllers *zugreifen. InputTracking:*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-269">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="2dfd2-270">Der obige Code stellt die Klammerpose des Controllers dar (in der der Benutzer den Controller hält), die nützlich ist, um eine Schütze in der Hand des Benutzers oder ein Modell des Controllers selbst zu rendern.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-270">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="2dfd2-271">Die Beziehung zwischen dieser Klammerpose und der Zeigerpose (wobei die Spitze des Controllers zeigt) kann sich über controllerübergreifend unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-271">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="2dfd2-272">Derzeit ist der Zugriff auf die Zeigerhaltung des Controllers nur über die MR-spezifische Eingabe-API möglich, die in den folgenden Abschnitten beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-272">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="2dfd2-273">Windows-spezifische APIs (XR. WSA. Eingabe)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-273">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="2dfd2-274">Wenn Ihr Projekt eine der XR-Dateien verwendet. WSA-APIs, die in zukünftigen Unity-Releases zugunsten des XR SDK eingestellt werden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-274">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="2dfd2-275">Für neue Projekte wird empfohlen, das XR SDK von Anfang an zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-275">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="2dfd2-276">Weitere Informationen zum [XR-Eingabesystem und](https://docs.unity3d.com/Manual/xr_input.html)zu den APIs finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-276">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="2dfd2-277">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-277">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="2dfd2-278">**Typen:** *InteractionManager,* *InteractionSourceState,* *InteractionSource,* *InteractionSourceProperties,* *InteractionSourceKind,* *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-278">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="2dfd2-279">Um ausführlichere Informationen zu Windows Mixed Reality Handeingabe (für HoloLens) und Motion-Controllern zu erhalten, können Sie die Windows-spezifischen APIs für räumliche Eingaben unter dem *UnityEngine.XR.WSA.Input-Namespace* verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-279">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="2dfd2-280">Dadurch können Sie auf zusätzliche Informationen wie Positionsgenauigkeit oder Quellart zugreifen, sodass Sie Hände und Controller voneinander unterscheiden können.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-280">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="2dfd2-281">Abfragen des Zustands von Händen und Motion-Controllern</span><span class="sxs-lookup"><span data-stu-id="2dfd2-281">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="2dfd2-282">Sie können den Zustand dieses Frames für jede Interaktionsquelle (Hand oder Motion Controller) mithilfe der *GetCurrentReading-Methode* abfragen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-282">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="2dfd2-283">Jeder *InteractionSourceState,* den Sie zurückerhalten, stellt eine Interaktionsquelle zum aktuellen Zeitpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-283">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="2dfd2-284">*InteractionSourceState* macht Informationen verfügbar, z. B.:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-284">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="2dfd2-285">Welche [Arten von Pressen](../../design/motion-controllers.md) auftreten (Auswählen/Menü/Greifen/Touchpad/Fingerabdruck)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-285">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="2dfd2-286">Andere spezifische Daten für Motion-Controller, z. B. das Touchpad und/oder die XY-Koordinaten und den touchierten Zustand des Sticks</span><span class="sxs-lookup"><span data-stu-id="2dfd2-286">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="2dfd2-287">InteractionSourceKind, um zu wissen, ob es sich bei der Quelle um eine Hand oder einen Motion Controller handelt</span><span class="sxs-lookup"><span data-stu-id="2dfd2-287">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="2dfd2-288">Abfragen von vorwärts vorhergesagten Renderingdarstellungen</span><span class="sxs-lookup"><span data-stu-id="2dfd2-288">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="2dfd2-289">Beim Abfragen von Interaktionsquelldaten von Händen und Controllern sind die Posen, die Sie erhalten, vorwärts vorhergesagte Posen für den Moment, in dem die Photonen dieses Frames die Augen des Benutzers erreichen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-289">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="2dfd2-290">Vorwärtsvorhersagen werden am besten zum **Rendern** des Controllers oder eines gehaltenen Objekts für jeden Frame verwendet.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-290">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="2dfd2-291">Wenn Sie eine bestimmte Veröffentlichung mit dem Controller als Ziel verwenden, ist dies am genauesten, wenn Sie die unten beschriebenen APIs für historische Ereignisse verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-291">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="2dfd2-292">Sie können auch die vorwärts vorhergesagte Kopfpose für diesen aktuellen Frame abrufen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-292">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="2dfd2-293">Wie bei der Quellpose ist dies nützlich für das **Rendern** eines Cursors, obwohl das Ziel einer bestimmten Veröffentlichung am genauesten ist, wenn Sie die unten beschriebenen APIs für historische Ereignisse verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-293">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="2dfd2-294">Behandeln von Interaktionsquellereignissen</span><span class="sxs-lookup"><span data-stu-id="2dfd2-294">Handling interaction source events</span></span>

<span data-ttu-id="2dfd2-295">Um Eingabeereignisse so zu behandeln, wie sie mit ihren genauen Historischen Posendaten auftreten, können Sie Interaktionsquellereignisse behandeln, anstatt abzufragen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-295">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="2dfd2-296">So behandeln Sie Interaktionsquellereignisse:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-296">To handle interaction source events:</span></span>
* <span data-ttu-id="2dfd2-297">Registrieren Sie sich für ein *InteractionManager-Eingabeereignis.*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-297">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="2dfd2-298">Für jede Art von Interaktionsereignis, an dem Sie interessiert sind, müssen Sie es abonnieren.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-298">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="2dfd2-299">Behandeln sie das -Ereignis.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-299">Handle the event.</span></span> <span data-ttu-id="2dfd2-300">Nachdem Sie ein Interaktionsereignis abonniert haben, erhalten Sie ggf. den Rückruf.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-300">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="2dfd2-301">Im *SourcePressed-Beispiel* ist dies, nachdem die Quelle erkannt wurde und bevor sie freigegeben oder verloren geht.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-301">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="2dfd2-302">Beenden der Behandlung eines Ereignisses</span><span class="sxs-lookup"><span data-stu-id="2dfd2-302">How to stop handling an event</span></span>

<span data-ttu-id="2dfd2-303">Sie müssen die Behandlung eines Ereignisses beenden, wenn Sie nicht mehr am Ereignis interessiert sind oder das Objekt zerstören, das das Ereignis abonniert hat.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-303">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="2dfd2-304">Um die Behandlung des Ereignisses zu beenden, kündigen Sie das Ereignis.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-304">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="2dfd2-305">Liste der Interaktionsquelle-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="2dfd2-305">List of interaction source events</span></span>

<span data-ttu-id="2dfd2-306">Die verfügbaren Interaktionsquellenereignisse sind:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-306">The available interaction source events are:</span></span>
* <span data-ttu-id="2dfd2-307">*InteractionSourceDetected* (Quelle wird aktiv)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-307">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="2dfd2-308">*InteractionSourceLost* (wird inaktiv)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-308">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="2dfd2-309">*InteractionSourcePressed* (Tippen, Drücken der Schaltfläche oder Äußerung "Auswählen")</span><span class="sxs-lookup"><span data-stu-id="2dfd2-309">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="2dfd2-310">*InteractionSourceReleased* (Ende eines Tippens, losgelassene Schaltfläche oder Ende der Äußerung "Auswählen")</span><span class="sxs-lookup"><span data-stu-id="2dfd2-310">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="2dfd2-311">*InteractionSourceUpdated* (verschiebt oder ändert einen Zustand auf andere Weise)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-311">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="2dfd2-312">Ereignisse für historische Zielgruppenadressierung stellen eine genaue Übereinstimmung mit einer Veröffentlichung oder einer Veröffentlichung</span><span class="sxs-lookup"><span data-stu-id="2dfd2-312">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="2dfd2-313">Die oben beschriebenen Abruf-APIs geben Ihrer App vorhergesagte Posen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-313">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="2dfd2-314">Die vorhergesagten Posen sind zwar am besten für das Rendern des Controllers oder eines virtuellen Objekts, aber zukünftige Posen sind für die Ausrichtung nicht optimal, aus zwei Wichtigen Gründen:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-314">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="2dfd2-315">Wenn der Benutzer eine Taste auf einem Controller drückt, kann es über Bluetooth zu einer Funklatenz von etwa 20 ms geben, bevor das System die Taste empfängt.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-315">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="2dfd2-316">Wenn Sie dann eine vorausgesagte Pose verwenden, werden weitere 10-20 ms Vorwärtsvorhersage angewendet, um die Zeit als Ziel zu verwenden, zu der die Photonen des aktuellen Frames die Augen des Benutzers erreichen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-316">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="2dfd2-317">Dies bedeutet, dass Sie beim Abruf eine Quell- oder Kopfpose erhalten, die 30 bis 40 ms vor dem Ort liegt, an dem der Kopf und die Hände des Benutzers tatsächlich zurück waren, als das Drücken oder Dies passiert ist.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-317">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="2dfd2-318">Bei HoloLens-Handeingaben gibt es zwar keine Drahtlose Übertragungsverzögerung, es gibt jedoch eine ähnliche Verarbeitungsverzögerung, um den Press zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-318">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="2dfd2-319">Um auf der Grundlage der ursprünglichen Absicht des Benutzers für eine Hand- oder Controllereingabe genau als Ziel zu verwenden, sollten Sie die historische Quellpose oder Kopfpose aus diesem *InteractionSourcePressed-* oder *InteractionSourceReleased-Eingabeereignis* verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-319">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="2dfd2-320">Sie können eine Press- oder Release-Version mit Verlaufsdaten aus dem Kopf des Benutzers oder seinem Controller als Ziel verwenden:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-320">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="2dfd2-321">Die Kopfpose zu dem Zeitpunkt, zu dem eine Geste  oder ein Controller-Press aufgetreten [ist,](../../design/gaze-and-commit.md) die zum Festlegen des Ziels verwendet werden kann, um zu bestimmen, worum es sich beim Benutzer gezaust hat:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-321">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="2dfd2-322">Die Quellpose zu dem Zeitpunkt, zu dem ein Bewegungscontroller gedrückt wurde, der zum Festlegen des Ziels verwendet werden kann, um zu bestimmen, auf was der Benutzer auf den Controller zeigen soll. </span><span class="sxs-lookup"><span data-stu-id="2dfd2-322">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="2dfd2-323">Dies ist der Zustand des Controllers, bei dem das Drücken auft ist.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-323">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="2dfd2-324">Wenn Sie den Controller selbst rendern, können Sie die Zeigerpose anstelle der Greifpose anfordern, um den Zielstrahl von dem zu kippen, was der Benutzer als natürliche Spitze dieses gerenderten Controllers betrachten wird:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-324">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="2dfd2-325">Beispiel für Ereignishandler</span><span class="sxs-lookup"><span data-stu-id="2dfd2-325">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a><span data-ttu-id="2dfd2-326">Motion Controllers in MRTK</span><span class="sxs-lookup"><span data-stu-id="2dfd2-326">Motion Controllers in MRTK</span></span>

<span data-ttu-id="2dfd2-327">Sie können über den [Eingabe-Manager auf gesten-](/windows/mixed-reality/mrtk-unity/features/input/controllers) und bewegungscontroller zugreifen.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-327">You can access [gesture and motion controller](/windows/mixed-reality/mrtk-unity/features/input/controllers) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="2dfd2-328">Immer am Ball mit Tutorials</span><span class="sxs-lookup"><span data-stu-id="2dfd2-328">Follow along with tutorials</span></span>

<span data-ttu-id="2dfd2-329">Ausführliche Tutorials mit ausführlicheren Anpassungsbeispielen finden Sie in der Mixed Reality Academy:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-329">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="2dfd2-330">MR-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="2dfd2-330">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="2dfd2-331">MR-Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="2dfd2-331">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="2dfd2-332">[![MR-Eingabe 213 – Motion-Controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="2dfd2-332">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="2dfd2-333">*MR-Eingabe 213 – Motion-Controller*</span><span class="sxs-lookup"><span data-stu-id="2dfd2-333">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2dfd2-334">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="2dfd2-334">Next Development Checkpoint</span></span>

<span data-ttu-id="2dfd2-335">Wenn Sie den Weg zur Unity-Entwicklung, den wir ihnen auf den Weg geben, folgen, sind Sie gerade dabei, die MRTK-Kernbausteine zu erkunden.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-335">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="2dfd2-336">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-336">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2dfd2-337">Hand- und Eye-Tracking</span><span class="sxs-lookup"><span data-stu-id="2dfd2-337">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="2dfd2-338">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="2dfd2-338">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2dfd2-339">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="2dfd2-339">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="2dfd2-340">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="2dfd2-340">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dfd2-341">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2dfd2-341">See also</span></span>

* [<span data-ttu-id="2dfd2-342">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="2dfd2-342">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="2dfd2-343">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="2dfd2-343">Motion controllers</span></span>](../../design/motion-controllers.md)