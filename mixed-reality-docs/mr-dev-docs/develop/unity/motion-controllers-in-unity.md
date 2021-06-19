---
title: Motion-Controller in Unity
description: Erfahren Sie, wie Sie Mithilfe von XR und gängigen Schaltflächen- und Achsen-APIs Aktionen beim Anvieren in Unity mit Motion Controller-Eingaben ergreifen.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Motion-Controller, Unity, Eingabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d8f9ce292c0ab1cfa89faf58f0e5b90322192b35
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394514"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="a44ca-104">Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="a44ca-104">Motion controllers in Unity</span></span>

<span data-ttu-id="a44ca-105">Es gibt zwei wichtige Möglichkeiten, um beim Anvieren [in Unity](gaze-in-unity.md)Aktionen zu [ergreifen:](../../design/gaze-and-commit.md#composite-gestures) Handgesten und [Motion-Controller](../../design/motion-controllers.md) in HoloLens und Immersive HMD.</span><span class="sxs-lookup"><span data-stu-id="a44ca-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="a44ca-106">Sie greifen auf die Daten für beide Quellen räumlicher Eingaben über die gleichen APIs in Unity zu.</span><span class="sxs-lookup"><span data-stu-id="a44ca-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="a44ca-107">Unity bietet zwei primäre Möglichkeiten für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a44ca-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="a44ca-108">Die allgemeinen *Input.GetButton/Input.GetAxis-APIs* funktionieren über mehrere Unity XR SDKs hinweg, während die für Windows Mixed Reality spezifische *InteractionManager/GestureRecognizer-API* den vollständigen Satz räumlicher Eingabedaten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="a44ca-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="a44ca-109">Unity XR-Eingabe-APIs</span><span class="sxs-lookup"><span data-stu-id="a44ca-109">Unity XR input APIs</span></span>

<span data-ttu-id="a44ca-110">Für neue Projekte wird empfohlen, die neuen XR-Eingabe-APIs von Anfang an zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a44ca-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="a44ca-111">Weitere Informationen zu den [XR-APIs finden Sie hier.](https://docs.unity3d.com/Manual/xr_input.html)</span><span class="sxs-lookup"><span data-stu-id="a44ca-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="a44ca-112">Unity-Schaltflächen-/Achsenzuordnungstabelle</span><span class="sxs-lookup"><span data-stu-id="a44ca-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="a44ca-113">Der Eingabe-Manager für Windows Mixed Reality Motion-Controller von Unity unterstützt die unten aufgeführten Schaltflächen- und Achsen-IDs über die *Input.GetButton/GetAxis-APIs.*</span><span class="sxs-lookup"><span data-stu-id="a44ca-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="a44ca-114">Die Spalte "Windows MR-spezifisch" bezieht sich auf Eigenschaften, die vom *Typ InteractionSourceState verfügbar* sind.</span><span class="sxs-lookup"><span data-stu-id="a44ca-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="a44ca-115">Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a44ca-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="a44ca-116">Die Schaltflächen-/Achsen-ID-Zuordnungen für Windows Mixed Reality im Allgemeinen mit den Oculus-Schaltflächen-/Achsen-IDs übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="a44ca-117">Die Schaltflächen-/Achsen-ID-Zuordnungen für Windows Mixed Reality unterscheiden sich von den OpenVR-Zuordnungen auf zwei Arten:</span><span class="sxs-lookup"><span data-stu-id="a44ca-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="a44ca-118">Die Zuordnung verwendet Touchpad-IDs, die sich von thumbstick unterscheiden, um Controller mit Thumbsticks und Touchpads zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="a44ca-119">Die Zuordnung vermeidet das Überladen der A- und X-Schaltflächen-IDs für die Menüschaltflächen, damit sie für die physischen ABXY-Schaltflächen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="a44ca-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="a44ca-120">Eingabe</span><span class="sxs-lookup"><span data-stu-id="a44ca-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="a44ca-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a></span><span class="sxs-lookup"><span data-stu-id="a44ca-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="a44ca-122">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="a44ca-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="a44ca-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-spezifische Eingabe-API</a></span><span class="sxs-lookup"><span data-stu-id="a44ca-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="a44ca-124">(XR. WSA. Eingabe)</span><span class="sxs-lookup"><span data-stu-id="a44ca-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="a44ca-125">Linken</span><span class="sxs-lookup"><span data-stu-id="a44ca-125">Left hand</span></span> </th><th> <span data-ttu-id="a44ca-126">Rechte Hand</span><span class="sxs-lookup"><span data-stu-id="a44ca-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="a44ca-127">Auswählen des gedrückten Triggers</span><span class="sxs-lookup"><span data-stu-id="a44ca-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="a44ca-128">Achse 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="a44ca-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="a44ca-129">Achse 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="a44ca-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="a44ca-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="a44ca-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-131">Auswählen des analogen Triggerwerts</span><span class="sxs-lookup"><span data-stu-id="a44ca-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="a44ca-132">Achse 9</span><span class="sxs-lookup"><span data-stu-id="a44ca-132">Axis 9</span></span> </td><td> <span data-ttu-id="a44ca-133">Achse 10</span><span class="sxs-lookup"><span data-stu-id="a44ca-133">Axis 10</span></span> </td><td> <span data-ttu-id="a44ca-134">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="a44ca-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-135">Select trigger partially pressed (Trigger teilweise gedrückt auswählen)</span><span class="sxs-lookup"><span data-stu-id="a44ca-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="a44ca-136">Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="a44ca-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a44ca-137">Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="a44ca-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a44ca-138">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="a44ca-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-139">Menüschaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="a44ca-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="a44ca-140">Schaltfläche 6\*</span><span class="sxs-lookup"><span data-stu-id="a44ca-140">Button 6\*</span></span> </td><td> <span data-ttu-id="a44ca-141">Schaltfläche 7\*</span><span class="sxs-lookup"><span data-stu-id="a44ca-141">Button 7\*</span></span> </td><td> <span data-ttu-id="a44ca-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="a44ca-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-143">Greiftaste gedrückt</span><span class="sxs-lookup"><span data-stu-id="a44ca-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="a44ca-144">Achse 11 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="a44ca-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="a44ca-145">Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="a44ca-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a44ca-146">Achse 12 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="a44ca-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="a44ca-147">Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="a44ca-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a44ca-148">Begriffen</span><span class="sxs-lookup"><span data-stu-id="a44ca-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="a44ca-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="a44ca-150">Achse 1</span><span class="sxs-lookup"><span data-stu-id="a44ca-150">Axis 1</span></span> </td><td> <span data-ttu-id="a44ca-151">Achse 4</span><span class="sxs-lookup"><span data-stu-id="a44ca-151">Axis 4</span></span> </td><td> <span data-ttu-id="a44ca-152">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="a44ca-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="a44ca-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="a44ca-154">Achse 2</span><span class="sxs-lookup"><span data-stu-id="a44ca-154">Axis 2</span></span> </td><td> <span data-ttu-id="a44ca-155">Achse 5</span><span class="sxs-lookup"><span data-stu-id="a44ca-155">Axis 5</span></span> </td><td> <span data-ttu-id="a44ca-156">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="a44ca-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-157">Thumbstick pressed (Gedrückter Fingerabdruck)</span><span class="sxs-lookup"><span data-stu-id="a44ca-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="a44ca-158">Schaltfläche 8</span><span class="sxs-lookup"><span data-stu-id="a44ca-158">Button 8</span></span> </td><td> <span data-ttu-id="a44ca-159">Schaltfläche 9</span><span class="sxs-lookup"><span data-stu-id="a44ca-159">Button 9</span></span> </td><td> <span data-ttu-id="a44ca-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="a44ca-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-161">Touchpad X <i>(links: -1.0, rechts: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="a44ca-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="a44ca-162">Achse 17\*</span><span class="sxs-lookup"><span data-stu-id="a44ca-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="a44ca-163">Achse 19\*</span><span class="sxs-lookup"><span data-stu-id="a44ca-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="a44ca-164">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="a44ca-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="a44ca-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="a44ca-166">Achse 18\*</span><span class="sxs-lookup"><span data-stu-id="a44ca-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="a44ca-167">Achse 20\*</span><span class="sxs-lookup"><span data-stu-id="a44ca-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="a44ca-168">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="a44ca-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-169">Touchpad berührt</span><span class="sxs-lookup"><span data-stu-id="a44ca-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="a44ca-170">Schaltfläche 18\*</span><span class="sxs-lookup"><span data-stu-id="a44ca-170">Button 18\*</span></span> </td><td> <span data-ttu-id="a44ca-171">Schaltfläche 19\*</span><span class="sxs-lookup"><span data-stu-id="a44ca-171">Button 19\*</span></span> </td><td> <span data-ttu-id="a44ca-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="a44ca-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-173">Touchpad gedrückt</span><span class="sxs-lookup"><span data-stu-id="a44ca-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="a44ca-174">Schaltfläche 16\*</span><span class="sxs-lookup"><span data-stu-id="a44ca-174">Button 16\*</span></span> </td><td> <span data-ttu-id="a44ca-175">Schaltfläche 17\*</span><span class="sxs-lookup"><span data-stu-id="a44ca-175">Button 17\*</span></span> </td><td> <span data-ttu-id="a44ca-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="a44ca-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-177">6DoF-Greif- oder Zeigerpose</span><span class="sxs-lookup"><span data-stu-id="a44ca-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="a44ca-178"><i>Nur</i> Greifpose: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="a44ca-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="a44ca-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">Xr. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="a44ca-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="a44ca-180">Übergeben <i>Sie "Pointer"</i> oder <i>"Pointer"</i> als Argument: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="a44ca-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="a44ca-181">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="a44ca-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-182">Nachverfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="a44ca-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="a44ca-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span><span class="sxs-lookup"><span data-stu-id="a44ca-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="a44ca-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="a44ca-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="a44ca-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="a44ca-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="a44ca-186">Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für OpenVR verwendet, aufgrund von Kollisionen in den Zuordnungen, die von Gamepads, Oculus Touch und OpenVR verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a44ca-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

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

### <a name="openxr"></a><span data-ttu-id="a44ca-187">OpenXR</span><span class="sxs-lookup"><span data-stu-id="a44ca-187">OpenXR</span></span>

<span data-ttu-id="a44ca-188">Informationen zu den Grundlagen zu Mixed Reality-Interaktionen in Unity finden Sie im [Unity-Handbuch für Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="a44ca-188">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="a44ca-189">Diese Unity-Dokumentation behandelt die Zuordnungen von controllerspezifischen Eingaben zu allgemeineren **InputFeatureUsage-s,** wie verfügbare XR-Eingaben identifiziert und kategorisiert werden können, wie Daten aus diesen Eingaben gelesen werden und mehr.</span><span class="sxs-lookup"><span data-stu-id="a44ca-189">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="a44ca-190">Das Mixed Reality OpenXR-Plug-In stellt zusätzliche Eingabeinteraktionsprofile zur Verfügung, die standard **InputFeatureUsage** s wie unten beschrieben zugeordnet sind:</span><span class="sxs-lookup"><span data-stu-id="a44ca-190">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="a44ca-191">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="a44ca-191">InputFeatureUsage</span></span> | <span data-ttu-id="a44ca-192">HP Reverb G2 Controller (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="a44ca-192">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="a44ca-193">HoloLens Hand (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="a44ca-193">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="a44ca-194">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="a44ca-194">primary2DAxis</span></span> | <span data-ttu-id="a44ca-195">Joystick</span><span class="sxs-lookup"><span data-stu-id="a44ca-195">Joystick</span></span> | |
| <span data-ttu-id="a44ca-196">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="a44ca-196">primary2DAxisClick</span></span> | <span data-ttu-id="a44ca-197">Gegenklicken</span><span class="sxs-lookup"><span data-stu-id="a44ca-197">Joystick - Click</span></span> | |
| <span data-ttu-id="a44ca-198">Trigger (trigger)</span><span class="sxs-lookup"><span data-stu-id="a44ca-198">trigger</span></span> | <span data-ttu-id="a44ca-199">Trigger</span><span class="sxs-lookup"><span data-stu-id="a44ca-199">Trigger</span></span>  | |
| <span data-ttu-id="a44ca-200">Griff</span><span class="sxs-lookup"><span data-stu-id="a44ca-200">grip</span></span> | <span data-ttu-id="a44ca-201">Griff</span><span class="sxs-lookup"><span data-stu-id="a44ca-201">Grip</span></span> | <span data-ttu-id="a44ca-202">Tippen oder Drücken in die Luft</span><span class="sxs-lookup"><span data-stu-id="a44ca-202">Air tap or squeeze</span></span> |
| <span data-ttu-id="a44ca-203">primaryButton</span><span class="sxs-lookup"><span data-stu-id="a44ca-203">primaryButton</span></span> | <span data-ttu-id="a44ca-204">[X/A] – Drücken</span><span class="sxs-lookup"><span data-stu-id="a44ca-204">[X/A] - Press</span></span> | <span data-ttu-id="a44ca-205">In die Luft tippen</span><span class="sxs-lookup"><span data-stu-id="a44ca-205">Air tap</span></span> |
| <span data-ttu-id="a44ca-206">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="a44ca-206">secondaryButton</span></span> | <span data-ttu-id="a44ca-207">[Y/B] – Drücken</span><span class="sxs-lookup"><span data-stu-id="a44ca-207">[Y/B] - Press</span></span> | |
| <span data-ttu-id="a44ca-208">gripButton</span><span class="sxs-lookup"><span data-stu-id="a44ca-208">gripButton</span></span> | <span data-ttu-id="a44ca-209">Klammer : Drücken</span><span class="sxs-lookup"><span data-stu-id="a44ca-209">Grip - Press</span></span> | |
| <span data-ttu-id="a44ca-210">triggerButton</span><span class="sxs-lookup"><span data-stu-id="a44ca-210">triggerButton</span></span> | <span data-ttu-id="a44ca-211">Trigger – Drücken</span><span class="sxs-lookup"><span data-stu-id="a44ca-211">Trigger - Press</span></span> | |
| <span data-ttu-id="a44ca-212">menuButton</span><span class="sxs-lookup"><span data-stu-id="a44ca-212">menuButton</span></span> | <span data-ttu-id="a44ca-213">Menü</span><span class="sxs-lookup"><span data-stu-id="a44ca-213">Menu</span></span> | |

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="a44ca-214">Klammerpose im Vergleich zu zeigender Pose</span><span class="sxs-lookup"><span data-stu-id="a44ca-214">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="a44ca-215">Windows Mixed Reality unterstützt Motion-Controller in einer Vielzahl von Formfaktoren.</span><span class="sxs-lookup"><span data-stu-id="a44ca-215">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="a44ca-216">Der Entwurf jedes Controllers unterscheidet sich in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung, die Apps beim Rendern des Controllers verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="a44ca-216">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="a44ca-217">Um diese Controller besser darzustellen, gibt es zwei Arten von Posen, die Sie für jede Interaktionsquelle untersuchen können: die **Klammerhaltung** und die **Zeigerhaltung.**</span><span class="sxs-lookup"><span data-stu-id="a44ca-217">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="a44ca-218">Sowohl die Klammerpose als auch die Zeigerposenkoordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="a44ca-218">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="a44ca-219">Klammerpose</span><span class="sxs-lookup"><span data-stu-id="a44ca-219">Grip pose</span></span>

<span data-ttu-id="a44ca-220">Die **Klammerhaltung** stellt die Position der Benutzerfläche dar, die entweder von einer HoloLens erkannt wird oder einen Motion Controller hält.</span><span class="sxs-lookup"><span data-stu-id="a44ca-220">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="a44ca-221">Bei immersiven Headsets wird die Klammerpose am besten verwendet, um **die Hand des Benutzers** oder ein Objekt in der Hand des Benutzers zu **rendern.**</span><span class="sxs-lookup"><span data-stu-id="a44ca-221">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="a44ca-222">Die Klammerpose wird auch beim Visualisieren eines Motion-Controllers verwendet.</span><span class="sxs-lookup"><span data-stu-id="a44ca-222">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="a44ca-223">Das **renderbare Modell, das** von Windows für einen Bewegungscontroller bereitgestellt wird, verwendet die Klammerpose als Ursprung und Drehmittelpunkt.</span><span class="sxs-lookup"><span data-stu-id="a44ca-223">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="a44ca-224">Die Klammerpose ist speziell wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="a44ca-224">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="a44ca-225">Die **Klammerposition:** Der Schwerpunkt der Handfläche, wenn der Controller auf natürliche Weise gehalten wird, wird nach links oder rechts angepasst, um die Position innerhalb des Reglers zu zentriert.</span><span class="sxs-lookup"><span data-stu-id="a44ca-225">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="a44ca-226">Auf dem Windows Mixed Reality Motion-Controller ist diese Position in der Regel an der Schaltfläche Greifen ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="a44ca-226">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="a44ca-227">**Die rechte Achse der Ziehrichtung:** Wenn Sie Ihre Hand vollständig öffnen, um eine flache 5-Finger-Pose zu bilden, ist der Strahl, der für Ihre Handfläche normal ist (vorwärts von der linken Handfläche, rückwärts von der rechten Handfläche)</span><span class="sxs-lookup"><span data-stu-id="a44ca-227">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="a44ca-228">**Die Vorwärtsachse der Klammerausrichtung:** Wenn Sie Ihre Hand teilweise schließen (so als ob sie den Controller hält), zeigt der Strahl, der "vorwärts" durch die Von den Nichtfingerfingern gebildeten Strahl zeigt.</span><span class="sxs-lookup"><span data-stu-id="a44ca-228">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="a44ca-229">Die **Nach-oben-Achse der Klammerausrichtung:** Die nach oben-Achse, die durch die Definitionen Rechts und Vorwärts impliziert wird.</span><span class="sxs-lookup"><span data-stu-id="a44ca-229">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="a44ca-230">Sie können über die anbieterübergreifende Eingabe-API von Unity ( XR) auf die Klammerhaltung *[zugreifen. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) oder über die MR-spezifische Windows-API (*sourceState.sourcePose.TryGetPosition/Rotation*, anfordern von Pose-Daten für den **Klammerknoten).**</span><span class="sxs-lookup"><span data-stu-id="a44ca-230">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="a44ca-231">Zeigerpose</span><span class="sxs-lookup"><span data-stu-id="a44ca-231">Pointer pose</span></span>

<span data-ttu-id="a44ca-232">Die **Zeigerpose** stellt die Spitze des Controllers dar, der nach vorn zeigt.</span><span class="sxs-lookup"><span data-stu-id="a44ca-232">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="a44ca-233">Die vom System bereitgestellte Zeigerpose wird am besten zum Raycasten verwendet, wenn Sie **das Controllermodell selbst rendern.**</span><span class="sxs-lookup"><span data-stu-id="a44ca-233">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="a44ca-234">Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers rendern, z. B. ein virtuelles Geschütz, sollten Sie mit einem Strahl zeigen, der für dieses virtuelle Objekt am natürlichsten ist, z. B. ein Strahl, der entlang des Von der App definierten Strahlmodells verläuft.</span><span class="sxs-lookup"><span data-stu-id="a44ca-234">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="a44ca-235">Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das Verweisen auf das virtuelle Objekt für Benutzer, die Ihre App verwenden, wahrscheinlich natürlicher.</span><span class="sxs-lookup"><span data-stu-id="a44ca-235">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="a44ca-236">Derzeit ist die Zeigerhaltung in Unity nur über die Windows MR-spezifische API *sourceState.sourcePose.TryGetPosition/Rotation* verfügbar, wobei *InteractionSourceNode.Pointer* als Argument übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="a44ca-236">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

### <a name="openxr"></a><span data-ttu-id="a44ca-237">OpenXR</span><span class="sxs-lookup"><span data-stu-id="a44ca-237">OpenXR</span></span> 

<span data-ttu-id="a44ca-238">Sie haben Zugriff auf zwei Sätze von Posen über OpenXR-Eingabeinteraktionen:</span><span class="sxs-lookup"><span data-stu-id="a44ca-238">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="a44ca-239">Die Klammer zum Rendern von Objekten in der Hand</span><span class="sxs-lookup"><span data-stu-id="a44ca-239">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="a44ca-240">Das Ziel ist es, auf die Welt zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-240">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="a44ca-241">Weitere Informationen zu diesem Entwurf und den Unterschieden zwischen den beiden Posen finden Sie in der [OpenXR-Spezifikation – Eingabeunterpfade.](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)</span><span class="sxs-lookup"><span data-stu-id="a44ca-241">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="a44ca-242">Posen, die von inputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** und **DeviceAngularVelocity** bereitgestellt werden, stellen alle die OpenXR-Schiebehaltung dar. </span><span class="sxs-lookup"><span data-stu-id="a44ca-242">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="a44ca-243">InputFeatureUsages im Zusammenhang mit Klammern wird in [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)von Unity definiert.</span><span class="sxs-lookup"><span data-stu-id="a44ca-243">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="a44ca-244">Posen, die von inputFeatureUsages **PointerPosition,** **PointerRotation,** **PointerVelocity** und **PointerAngularVelocity** bereitgestellt werden, stellen alle die OpenXR-Zielhaltung dar. </span><span class="sxs-lookup"><span data-stu-id="a44ca-244">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="a44ca-245">Diese InputFeatureUsages sind nicht in enthaltenen C#-Dateien definiert. Daher müssen Sie Ihre eigenen InputFeatureUsages wie folgt definieren:</span><span class="sxs-lookup"><span data-stu-id="a44ca-245">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a><span data-ttu-id="a44ca-246">Haptik</span><span class="sxs-lookup"><span data-stu-id="a44ca-246">Haptics</span></span>

<span data-ttu-id="a44ca-247">Informationen zur Verwendung von Haptik im XR-Eingabesystem von Unity finden Sie im [Unity-Handbuch für Unity XR Input – Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="a44ca-247">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="a44ca-248">Controller-Nachverfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="a44ca-248">Controller tracking state</span></span>

<span data-ttu-id="a44ca-249">Wie die Headsets erfordert auch der Windows Mixed Reality Motion Controller keine Einrichtung externer Überwachungssensoren.</span><span class="sxs-lookup"><span data-stu-id="a44ca-249">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="a44ca-250">Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="a44ca-250">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="a44ca-251">Wenn der Benutzer die Controller aus dem Ansichtsfeld des Headsets verschiebt, leitet Windows in den meisten Fällen weiterhin Controllerpositionen ab.</span><span class="sxs-lookup"><span data-stu-id="a44ca-251">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="a44ca-252">Wenn der Controller die visuelle Nachverfolgung lange genug verloren hat, werden die Positionen des Controllers auf Positionen mit ungefährer Genauigkeit abgesenkt.</span><span class="sxs-lookup"><span data-stu-id="a44ca-252">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="a44ca-253">An diesem Punkt sperrt das System den Controller für den Benutzer, verfolgt die Position des Benutzers, während er sich bewegt, während die tatsächliche Ausrichtung des Controllers weiterhin mit seinen internen Ausrichtungssensoren verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="a44ca-253">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="a44ca-254">Viele Apps, die Controller verwenden, um auf Benutzeroberflächenelemente zu zeigen und diese zu aktivieren, können normal und mit ungefährer Genauigkeit ausgeführt werden, ohne dass der Benutzer darauf hinweist.</span><span class="sxs-lookup"><span data-stu-id="a44ca-254">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="a44ca-255">Explizite Überlegungen zum Nachverfolgungszustand</span><span class="sxs-lookup"><span data-stu-id="a44ca-255">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="a44ca-256">Apps, die Positionen basierend auf dem Nachverfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und Eigenschaften für den Zustand des Controllers überprüfen, z. B. *SourceLossRisk* und *PositionAccuracy:*</span><span class="sxs-lookup"><span data-stu-id="a44ca-256">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="a44ca-257">Nachverfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="a44ca-257">Tracking state</span></span> </th><th> <span data-ttu-id="a44ca-258">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="a44ca-258">SourceLossRisk</span></span> </th><th> <span data-ttu-id="a44ca-259">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="a44ca-259">PositionAccuracy</span></span> </th><th> <span data-ttu-id="a44ca-260">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="a44ca-260">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="a44ca-261"><b>Hohe Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="a44ca-261"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="a44ca-262">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="a44ca-262">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a44ca-263">Hoch</span><span class="sxs-lookup"><span data-stu-id="a44ca-263">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a44ca-264">true</span><span class="sxs-lookup"><span data-stu-id="a44ca-264">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-265"><b>Hohe Genauigkeit (verlustgefahrt)</b> </span><span class="sxs-lookup"><span data-stu-id="a44ca-265"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a44ca-266">== 1.0</span><span class="sxs-lookup"><span data-stu-id="a44ca-266">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a44ca-267">Hoch</span><span class="sxs-lookup"><span data-stu-id="a44ca-267">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a44ca-268">true</span><span class="sxs-lookup"><span data-stu-id="a44ca-268">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-269"><b>Ungefähre Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="a44ca-269"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a44ca-270">== 1.0</span><span class="sxs-lookup"><span data-stu-id="a44ca-270">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a44ca-271">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="a44ca-271">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a44ca-272">true</span><span class="sxs-lookup"><span data-stu-id="a44ca-272">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a44ca-273"><b>Keine Position</b> </span><span class="sxs-lookup"><span data-stu-id="a44ca-273"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a44ca-274">== 1.0</span><span class="sxs-lookup"><span data-stu-id="a44ca-274">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a44ca-275">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="a44ca-275">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a44ca-276">false</span><span class="sxs-lookup"><span data-stu-id="a44ca-276">false</span></span></td>
</tr>
</table>

<span data-ttu-id="a44ca-277">Diese Nachverfolgungszustände des Motion-Controllers sind wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="a44ca-277">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="a44ca-278">**Hohe Genauigkeit:** Während sich der Motion-Controller im Ansichtsfeld des Headsets befindet, bietet er in der Regel basierend auf der visuellen Nachverfolgung positionen mit hoher Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="a44ca-278">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="a44ca-279">Ein sich bewegender Controller, der vorübergehend das Sichtfeld verlässt oder kurzzeitig von den Headsetsensoren verdeckt wird (z. B. durch die andere Seite des Benutzers), gibt weiterhin eine kurze Zeit lang hochgenaue Posen zurück, basierend auf der trägen Nachverfolgung des Controllers selbst.</span><span class="sxs-lookup"><span data-stu-id="a44ca-279">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="a44ca-280">**Hohe Genauigkeit (verlustgefährdete):** Wenn der Benutzer den Motion-Controller hinter den Rand des Ansichtsfelds des Headsets bewegt, kann das Headset die Position des Controllers bald nicht mehr visuell nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-280">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="a44ca-281">Die App weiß, wann der Controller diese FOV-Grenze erreicht hat, indem sie den **SourceLossRisk-Wert** 1.0 erreicht.</span><span class="sxs-lookup"><span data-stu-id="a44ca-281">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="a44ca-282">An diesem Punkt kann die App Controllergesten anhalten, die einen stabilen Stream von hochwertigen Posen erfordern.</span><span class="sxs-lookup"><span data-stu-id="a44ca-282">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="a44ca-283">**Ungefähre Genauigkeit:** Wenn der Controller die visuelle Nachverfolgung lange genug verloren hat, werden die Positionen des Controllers auf Positionen mit ungefährer Genauigkeit abgesenkt.</span><span class="sxs-lookup"><span data-stu-id="a44ca-283">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="a44ca-284">An diesem Punkt sperrt das System den Controller für den Benutzer, verfolgt die Position des Benutzers, während er sich bewegt, während die tatsächliche Ausrichtung des Controllers weiterhin mit seinen internen Ausrichtungssensoren verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="a44ca-284">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="a44ca-285">Viele Apps, die Controller verwenden, um auf Benutzeroberflächenelemente zu zeigen und diese zu aktivieren, können normal und mit ungefährer Genauigkeit ausgeführt werden, ohne dass der Benutzer darauf hinweist.</span><span class="sxs-lookup"><span data-stu-id="a44ca-285">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="a44ca-286">Apps mit größeren Eingabeanforderungen können diesen Abstieg von **Hoher** Genauigkeit auf **Ungefähre** Genauigkeit durch Untersuchen der **PositionAccuracy-Eigenschaft** einsehen, um dem Benutzer z. B. während dieser Zeit eine ausführlichere Trefferbox auf Off-Screen-Zielen zu geben.</span><span class="sxs-lookup"><span data-stu-id="a44ca-286">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="a44ca-287">**Keine Position:** Während der Controller lange Zeit mit ungefährer Genauigkeit arbeiten kann, weiß das System manchmal, dass selbst eine durch Körper gesperrte Position im Moment nicht sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="a44ca-287">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="a44ca-288">Beispielsweise wurde ein controller, der aktiviert wurde, möglicherweise nie visuell beobachtet, oder ein Benutzer kann einen Controller abstellen, der dann von einer anderen Person übernommen wird.</span><span class="sxs-lookup"><span data-stu-id="a44ca-288">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="a44ca-289">Zu diesen Zeiten stellt das System keine Position für die App bereit, und *TryGetPosition* gibt FALSE zurück.</span><span class="sxs-lookup"><span data-stu-id="a44ca-289">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="a44ca-290">Allgemeine Unity-APIs (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="a44ca-290">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="a44ca-291">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="a44ca-291">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="a44ca-292">**Typen:** *Eingabe,* *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="a44ca-292">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="a44ca-293">Unity verwendet derzeit die allgemeinen *Input.GetButton/Input.GetAxis-APIs,* um Eingaben für [das Oculus SDK,](https://docs.unity3d.com/Manual/OculusControllers.html) [das OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality verfügbar zu machen, einschließlich Hände und Motion Controller.</span><span class="sxs-lookup"><span data-stu-id="a44ca-293">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="a44ca-294">Wenn Ihre App diese APIs für die Eingabe verwendet, kann sie Motion-Controller problemlos über mehrere XR SDKs hinweg unterstützen, einschließlich Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a44ca-294">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="a44ca-295">Abrufen des gedrückten Zustands einer logischen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="a44ca-295">Getting a logical button's pressed state</span></span>

<span data-ttu-id="a44ca-296">Um die allgemeinen Unity-Eingabe-APIs zu verwenden, beginnen Sie in der Regel damit, Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html)zu verbinden und eine Schaltfläche oder Achsen-IDs an jeden Namen zu binden.</span><span class="sxs-lookup"><span data-stu-id="a44ca-296">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="a44ca-297">Anschließend können Sie Code schreiben, der auf diesen logischen Schaltflächen-/Achsennamen verweist.</span><span class="sxs-lookup"><span data-stu-id="a44ca-297">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="a44ca-298">Um z. B. die Triggerschaltfläche des linken Bewegungscontrollers der Aktion Senden zuzuordnen, wechseln Sie zu **Bearbeiten > Projekteinstellungen > Eingabe** in Unity, und erweitern Sie die Eigenschaften des Abschnitts Senden unter Achsen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-298">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="a44ca-299">Ändern Sie die Eigenschaft **Positive Schaltfläche** oder Alt **Positive Button** wie folgt, um **schaltfläche 14** zu lesen:</span><span class="sxs-lookup"><span data-stu-id="a44ca-299">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="a44ca-300">![InputManager von Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="a44ca-300">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="a44ca-301&quot;>*Unity InputManager*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a44ca-301&quot;>*Unity InputManager*</span></span>

<span data-ttu-id=&quot;a44ca-302&quot;>Ihr Skript kann dann mit *Input.GetButton* nach der Aktion Senden suchen:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;a44ca-302&quot;>Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton(&quot;Submit"))
{
  // ...
}
```
<span data-ttu-id="a44ca-303">Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **Eigenschaft Größe** unter **Achsen** ändern.</span><span class="sxs-lookup"><span data-stu-id="a44ca-303">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="a44ca-304">Direktes Abrufen des gedrückten Zustands einer physischen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="a44ca-304">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="a44ca-305">Sie können auch manuell über ihren vollqualifizierten Namen auf Schaltflächen zugreifen, indem *Sie Input.GetKey* verwenden:</span><span class="sxs-lookup"><span data-stu-id="a44ca-305">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="a44ca-306">Abrufen der Posen eines Hand- oder Bewegungscontrollers</span><span class="sxs-lookup"><span data-stu-id="a44ca-306">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="a44ca-307">Sie können mit XR auf die Position und Drehung des Controllers *zugreifen. InputTracking:*</span><span class="sxs-lookup"><span data-stu-id="a44ca-307">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="a44ca-308">Der obige Code stellt die Klammerpose des Controllers dar (in der der Benutzer den Controller hält), die nützlich ist, um eine Schütze in der Hand des Benutzers oder ein Modell des Controllers selbst zu rendern.</span><span class="sxs-lookup"><span data-stu-id="a44ca-308">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="a44ca-309">Die Beziehung zwischen dieser Klammerpose und der Zeigerpose (wobei die Spitze des Controllers zeigt) kann sich über controllerübergreifend unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="a44ca-309">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="a44ca-310">Derzeit ist der Zugriff auf die Zeigerhaltung des Controllers nur über die MR-spezifische Eingabe-API möglich, die in den folgenden Abschnitten beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="a44ca-310">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="a44ca-311">Windows-spezifische APIs (XR. WSA. Eingabe)</span><span class="sxs-lookup"><span data-stu-id="a44ca-311">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="a44ca-312">Wenn Ihr Projekt eine der XR-Dateien verwendet. WSA-APIs, die in zukünftigen Unity-Releases zugunsten des XR SDK eingestellt werden.</span><span class="sxs-lookup"><span data-stu-id="a44ca-312">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="a44ca-313">Für neue Projekte wird empfohlen, das XR SDK von Anfang an zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a44ca-313">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="a44ca-314">Weitere Informationen zum [XR-Eingabesystem und](https://docs.unity3d.com/Manual/xr_input.html)zu den APIs finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="a44ca-314">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="a44ca-315">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="a44ca-315">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="a44ca-316">**Typen:** *InteractionManager,* *InteractionSourceState,* *InteractionSource,* *InteractionSourceProperties,* *InteractionSourceKind,* *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="a44ca-316">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="a44ca-317">Um ausführlichere Informationen zu Windows Mixed Reality Handeingabe (für HoloLens) und Motion Controller zu erhalten, können Sie die Windows-spezifischen räumlichen Eingabe-APIs unter dem *UnityEngine.XR.WSA.Input-Namespace* verwenden.</span><span class="sxs-lookup"><span data-stu-id="a44ca-317">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="a44ca-318">Dadurch können Sie auf zusätzliche Informationen wie Positionsgenauigkeit oder Quellart zugreifen, sodass Sie Hände und Controller voneinander unterscheiden können.</span><span class="sxs-lookup"><span data-stu-id="a44ca-318">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="a44ca-319">Abfragen des Zustands von Händen und Motion-Controllern</span><span class="sxs-lookup"><span data-stu-id="a44ca-319">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="a44ca-320">Sie können den Zustand dieses Frames für jede Interaktionsquelle (Hand oder Motion Controller) mithilfe der *GetCurrentReading-Methode* abfragen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-320">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="a44ca-321">Jeder *InteractionSourceState, den* Sie zurückerhalten, stellt eine Interaktionsquelle zum aktuellen Zeitpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="a44ca-321">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="a44ca-322">*InteractionSourceState* macht Informationen verfügbar, z. B.:</span><span class="sxs-lookup"><span data-stu-id="a44ca-322">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="a44ca-323">Welche [Arten von Pressen](../../design/motion-controllers.md) auftreten (Auswählen/Menü/Greifen/Touchpad/Fingerabdruck)</span><span class="sxs-lookup"><span data-stu-id="a44ca-323">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="a44ca-324">Andere spezifische Daten für Motion-Controller, z. B. das Touchpad und/oder die XY-Koordinaten und den berührten Zustand des Sticks</span><span class="sxs-lookup"><span data-stu-id="a44ca-324">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="a44ca-325">InteractionSourceKind, um zu wissen, ob es sich bei der Quelle um eine Hand oder einen Bewegungscontroller handelt</span><span class="sxs-lookup"><span data-stu-id="a44ca-325">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="a44ca-326">Abfragen für vorwärts vorhergesagte Renderingdarstellungen</span><span class="sxs-lookup"><span data-stu-id="a44ca-326">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="a44ca-327">Beim Abfragen von Interaktionsquelldaten von Händen und Controllern sind die Posen, die Sie erhalten, vorwärts vorhergesagte Posen für den Moment, in dem die Photonen dieses Frames die Augen des Benutzers erreichen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-327">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="a44ca-328">Vorwärts vorhergesagte Posen eignen sich am besten zum **Rendern** des Controllers oder eines gehaltenen Objekts für jeden Frame.</span><span class="sxs-lookup"><span data-stu-id="a44ca-328">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="a44ca-329">Wenn Sie eine bestimmte Veröffentlichung mit dem Controller als Ziel verwenden, ist dies am genauesten, wenn Sie die unten beschriebenen APIs für historische Ereignisse verwenden.</span><span class="sxs-lookup"><span data-stu-id="a44ca-329">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="a44ca-330">Sie können auch die vorwärts vorhergesagte Kopfpose für diesen aktuellen Frame abrufen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-330">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="a44ca-331">Wie bei der Quellposition ist dies nützlich für das **Rendern** eines Cursors, obwohl das Ziel einer bestimmten Veröffentlichung am genauesten ist, wenn Sie die unten beschriebenen Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="a44ca-331">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="a44ca-332">Behandeln von Interaktionsquellereignissen</span><span class="sxs-lookup"><span data-stu-id="a44ca-332">Handling interaction source events</span></span>

<span data-ttu-id="a44ca-333">Um Eingabeereignisse so zu behandeln, wie sie mit ihren genauen Historischen Posendaten auftreten, können Sie Interaktionsquellereignisse behandeln, anstatt abzufragen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-333">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="a44ca-334">So behandeln Sie Interaktionsquellereignisse:</span><span class="sxs-lookup"><span data-stu-id="a44ca-334">To handle interaction source events:</span></span>
* <span data-ttu-id="a44ca-335">Registrieren Sie sich für ein *InteractionManager-Eingabeereignis.*</span><span class="sxs-lookup"><span data-stu-id="a44ca-335">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="a44ca-336">Für jeden Typ von Interaktionsereignis, an dem Sie interessiert sind, müssen Sie es abonnieren.</span><span class="sxs-lookup"><span data-stu-id="a44ca-336">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="a44ca-337">Behandeln Sie das Ereignis.</span><span class="sxs-lookup"><span data-stu-id="a44ca-337">Handle the event.</span></span> <span data-ttu-id="a44ca-338">Nachdem Sie ein Interaktionsereignis abonniert haben, erhalten Sie ggf. den Rückruf.</span><span class="sxs-lookup"><span data-stu-id="a44ca-338">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="a44ca-339">Im *SourcePressed-Beispiel* ist dies, nachdem die Quelle erkannt wurde und bevor sie freigegeben oder verloren geht.</span><span class="sxs-lookup"><span data-stu-id="a44ca-339">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="a44ca-340">Beenden der Behandlung eines Ereignisses</span><span class="sxs-lookup"><span data-stu-id="a44ca-340">How to stop handling an event</span></span>

<span data-ttu-id="a44ca-341">Sie müssen die Behandlung eines Ereignisses beenden, wenn Sie nicht mehr an dem Ereignis interessiert sind oder das Objekt zerstören, das das Ereignis abonniert hat.</span><span class="sxs-lookup"><span data-stu-id="a44ca-341">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="a44ca-342">Um die Behandlung des Ereignisses zu beenden, kündigen Sie das Abonnement des Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="a44ca-342">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="a44ca-343">Liste der Interaktionsquellereignisse</span><span class="sxs-lookup"><span data-stu-id="a44ca-343">List of interaction source events</span></span>

<span data-ttu-id="a44ca-344">Die verfügbaren Interaktionsquellereignisse sind:</span><span class="sxs-lookup"><span data-stu-id="a44ca-344">The available interaction source events are:</span></span>
* <span data-ttu-id="a44ca-345">*InteractionSourceDetected* (Quelle wird aktiv)</span><span class="sxs-lookup"><span data-stu-id="a44ca-345">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="a44ca-346">*InteractionSourceLost* (wird inaktiv)</span><span class="sxs-lookup"><span data-stu-id="a44ca-346">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="a44ca-347">*InteractionSourcePressed (tippen,* Schaltfläche drücken oder "Select" äußerungen)</span><span class="sxs-lookup"><span data-stu-id="a44ca-347">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="a44ca-348">*InteractionSourceReleased* (Ende eines Tippens, losgelassene Schaltfläche oder Ende der Äußerung "Auswählen")</span><span class="sxs-lookup"><span data-stu-id="a44ca-348">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="a44ca-349">*InteractionSourceUpdated* (verschiebt oder ändert auf andere Weise einen Zustand)</span><span class="sxs-lookup"><span data-stu-id="a44ca-349">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="a44ca-350">Ereignisse für historische Zielgruppenadressierung stellen dar, die einer Veröffentlichung am genauesten entsprechen</span><span class="sxs-lookup"><span data-stu-id="a44ca-350">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="a44ca-351">Die zuvor beschriebenen Abruf-APIs geben Ihrer App vorwärts vorhergesagte Posen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-351">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="a44ca-352">Diese vorhergesagten Posen eignen sich zwar am besten zum Rendern des Controllers oder eines virtuellen Objekts, aber zukünftige Posen sind aus zwei wichtigen Gründen nicht optimal für die Zielbestimmung:</span><span class="sxs-lookup"><span data-stu-id="a44ca-352">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="a44ca-353">Wenn der Benutzer eine Schaltfläche auf einem Controller drückt, kann es ca. 20 ms drahtlose Latenz über Bluetooth geben, bevor das System die Taste empfängt.</span><span class="sxs-lookup"><span data-stu-id="a44ca-353">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="a44ca-354">Wenn Sie dann eine vorwärts vorhergesagte Pose verwenden, werden weitere 10 bis 20 ms Vorwärtsvorhersage angewendet, um die Zeit als Ziel zu verwenden, zu der die Photonen des aktuellen Frames die Augen des Benutzers erreichen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-354">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="a44ca-355">Dies bedeutet, dass Sie beim Abruf eine Quellpose oder Kopfpose erhalten, die zwischen 30 und 40 ms vor dem Ort liegt, an dem der Kopf und die Hände des Benutzers tatsächlich zurück waren, als die Sprech- oder Veröffentlichung erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="a44ca-355">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="a44ca-356">Bei HoloLens-Handeingaben gibt es zwar keine drahtlose Übertragungsverzögerung, es gibt jedoch eine ähnliche Verarbeitungsverzögerung, um die Drückende zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-356">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="a44ca-357">Verwenden Sie die historische Quellpose oder Kopfpose aus dem *Eingabeereignis InteractionSourcePressed* oder *InteractionSourceReleased,* um das Ziel genau basierend auf der ursprünglichen Absicht des Benutzers für eine Hand- oder Controllereingabe festzulegen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-357">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="a44ca-358">Sie können eine Veröffentlichung mit historischen Posendaten vom Kopf des Benutzers oder dessen Controller als Ziel verwenden:</span><span class="sxs-lookup"><span data-stu-id="a44ca-358">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="a44ca-359">Die Kopfpose zu dem Zeitpunkt, zu dem eine Geste oder Eindrückbewegung auf dem Controller aufgetreten ist, die **verwendet** werden kann, um zu bestimmen, wofür der Benutzer 2016 000 Benutzer angezeigt [hat:](../../design/gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="a44ca-359">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="a44ca-360">Die Quellpose zu dem Zeitpunkt, zu dem ein Bewegungscontroller gedrückt wurde, der zum **Festlegen** des Ziels verwendet werden kann, um zu bestimmen, auf was der Benutzer auf den Controller verweist.</span><span class="sxs-lookup"><span data-stu-id="a44ca-360">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="a44ca-361">Dies ist der Zustand des Controllers, auf dem die Taste gedrückt wurde.</span><span class="sxs-lookup"><span data-stu-id="a44ca-361">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="a44ca-362">Wenn Sie den Controller selbst rendern, können Sie die Zeigerpose anstelle der Klammerpose anfordern, um den Zielstrahl von dem abzuzielen, was der Benutzer als natürliche Spitze dieses gerenderten Controllers betrachtet:</span><span class="sxs-lookup"><span data-stu-id="a44ca-362">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="a44ca-363">Beispiel für Ereignishandler</span><span class="sxs-lookup"><span data-stu-id="a44ca-363">Event handlers example</span></span>

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

## <a name="motion-controllers-in-mrtk"></a><span data-ttu-id="a44ca-364">Motion Controllers in MRTK</span><span class="sxs-lookup"><span data-stu-id="a44ca-364">Motion Controllers in MRTK</span></span>

<span data-ttu-id="a44ca-365">Sie können über den Eingabe-Manager auf [Gesten- und Bewegungscontroller](/windows/mixed-reality/mrtk-unity/features/input/controllers) zugreifen.</span><span class="sxs-lookup"><span data-stu-id="a44ca-365">You can access [gesture and motion controller](/windows/mixed-reality/mrtk-unity/features/input/controllers) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="a44ca-366">Immer am Ball mit Tutorials</span><span class="sxs-lookup"><span data-stu-id="a44ca-366">Follow along with tutorials</span></span>

<span data-ttu-id="a44ca-367">Ausführliche Tutorials mit detaillierteren Anpassungsbeispielen finden Sie in der Mixed Reality Academy:</span><span class="sxs-lookup"><span data-stu-id="a44ca-367">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="a44ca-368">MR-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="a44ca-368">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="a44ca-369">MR-Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="a44ca-369">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="a44ca-370">[![MR-Eingabe 213 – Motion-Controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="a44ca-370">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="a44ca-371">*MR-Eingabe 213 – Motion-Controller*</span><span class="sxs-lookup"><span data-stu-id="a44ca-371">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="a44ca-372">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="a44ca-372">Next Development Checkpoint</span></span>

<span data-ttu-id="a44ca-373">Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, befinden Sie sich in der Mitte der MRTK-Kernbausteine.</span><span class="sxs-lookup"><span data-stu-id="a44ca-373">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="a44ca-374">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="a44ca-374">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a44ca-375">Hand- und Eye-Tracking</span><span class="sxs-lookup"><span data-stu-id="a44ca-375">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="a44ca-376">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="a44ca-376">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a44ca-377">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="a44ca-377">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="a44ca-378">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a44ca-378">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="a44ca-379">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a44ca-379">See also</span></span>

* [<span data-ttu-id="a44ca-380">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="a44ca-380">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="a44ca-381">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="a44ca-381">Motion controllers</span></span>](../../design/motion-controllers.md)