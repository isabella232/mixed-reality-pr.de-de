---
title: Gesten und Motion-Controller in Unity
description: Erfahren Sie, wie Sie mit Handgesten und Bewegungs Controllern mit XR und allgemeinen Schaltflächen-/Axis-APIs Aktionen in Unity durchführen können.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Gesten, Bewegungs Controller, Unity, Blick, Eingabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 3ef3e3d5a1d9171ff6cc04e19fa97bb73768370e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008790"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="7dc2a-104">Gesten und Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="7dc2a-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="7dc2a-105">Es gibt zwei wichtige Möglichkeiten, um Ihre [Blicke in Unity](gaze-in-unity.md), [Handgesten](../../design/gaze-and-commit.md#composite-gestures) und [Bewegungs Controllern](../../design/motion-controllers.md) in hololens und immersiven HMD zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="7dc2a-106">Sie greifen über dieselben APIs in Unity auf die Daten für beide Quellen räumlicher Eingaben zu.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="7dc2a-107">Unity bietet zwei Hauptmethoden für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="7dc2a-108">Die gängigen *Input. getbutton/Input. getaxis-* APIs funktionieren über mehrere Unity-XR-SDK hinweg, während die *interaktionmanager/GestureRecognizer* -API speziell für Windows Mixed Reality den vollständigen Satz räumlicher Eingabedaten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="7dc2a-109">Eingabe-APIs für Unity XR</span><span class="sxs-lookup"><span data-stu-id="7dc2a-109">Unity XR input APIs</span></span>

<span data-ttu-id="7dc2a-110">Bei neuen Projekten wird die Verwendung der neuen XR-Eingabe-APIs von Anfang an empfohlen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="7dc2a-111">Weitere Informationen zu den [XR-APIs](https://docs.unity3d.com/Manual/xr_input.html)finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="7dc2a-112">Unity-Schaltfläche/Achsen Zuordnung (Tabelle)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="7dc2a-113">Der Eingabe-Manager von Unity für Windows Mixed Reality Motion Controllers unterstützt die unten aufgeführten Schaltflächen-und Achsen-IDs über die *Eingabe. getbutton/getaxis-* APIs.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="7dc2a-114">Die Spalte "Windows Mr-spezifisch" bezieht sich auf Eigenschaften, die vom *interaktionsourcestate* -Typ verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="7dc2a-115">Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="7dc2a-116">Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality entsprechen im Allgemeinen den Oculus-Schaltflächen-/Achsen-IDs</span><span class="sxs-lookup"><span data-stu-id="7dc2a-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="7dc2a-117">Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality unterscheiden sich auf zwei Arten von den Zuordnungen von openvr:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="7dc2a-118">Die Zuordnung verwendet Touchpad-IDs, die sich vom Finger Stick unterscheiden, um Controller mit beiden Fingerabdrücken und Touchpads zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="7dc2a-119">Durch die Zuordnung wird vermieden, dass die Schaltflächen-IDs A und X für die Menü Schaltflächen überladen werden, damit Sie für die physischen abxy-Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="7dc2a-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="7dc2a-120">Eingabe</span><span class="sxs-lookup"><span data-stu-id="7dc2a-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="7dc2a-121"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a></span><span class="sxs-lookup"><span data-stu-id="7dc2a-121"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="7dc2a-122">(Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="7dc2a-123"><a href="gestures-and-motion-controllers-in-unity.md#">Windows-spezifische Eingabe-API</a></span><span class="sxs-lookup"><span data-stu-id="7dc2a-123"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="7dc2a-124">XR. WSA. Der</span><span class="sxs-lookup"><span data-stu-id="7dc2a-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="7dc2a-125">Links</span><span class="sxs-lookup"><span data-stu-id="7dc2a-125">Left hand</span></span> </th><th> <span data-ttu-id="7dc2a-126">Rechte Seite</span><span class="sxs-lookup"><span data-stu-id="7dc2a-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7dc2a-127">Select-Taste gedrückt</span><span class="sxs-lookup"><span data-stu-id="7dc2a-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="7dc2a-128">Achse 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="7dc2a-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="7dc2a-129">Achse 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="7dc2a-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="7dc2a-130">selectpressed</span><span class="sxs-lookup"><span data-stu-id="7dc2a-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-131">Auswählen des analogen Auslöse Werts</span><span class="sxs-lookup"><span data-stu-id="7dc2a-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="7dc2a-132">Achse 9</span><span class="sxs-lookup"><span data-stu-id="7dc2a-132">Axis 9</span></span> </td><td> <span data-ttu-id="7dc2a-133">Achse 10</span><span class="sxs-lookup"><span data-stu-id="7dc2a-133">Axis 10</span></span> </td><td> <span data-ttu-id="7dc2a-134">selectpressedamount</span><span class="sxs-lookup"><span data-stu-id="7dc2a-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-135">Select-Taste teilweise gedrückt</span><span class="sxs-lookup"><span data-stu-id="7dc2a-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="7dc2a-136">Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7dc2a-137">Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7dc2a-138">selectpressedamount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="7dc2a-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-139">Menü Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="7dc2a-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="7dc2a-140">Schaltfläche 6 \*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-140">Button 6\*</span></span> </td><td> <span data-ttu-id="7dc2a-141">Schaltfläche 7 \*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-141">Button 7\*</span></span> </td><td> <span data-ttu-id="7dc2a-142">menupressed</span><span class="sxs-lookup"><span data-stu-id="7dc2a-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-143">Zieh Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="7dc2a-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="7dc2a-144">Achse 11 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="7dc2a-145">Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7dc2a-146">Achse 12 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="7dc2a-147">Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7dc2a-148">Schna</span><span class="sxs-lookup"><span data-stu-id="7dc2a-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-149">Thumbstick X <i>(Links:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="7dc2a-150">Achse 1</span><span class="sxs-lookup"><span data-stu-id="7dc2a-150">Axis 1</span></span> </td><td> <span data-ttu-id="7dc2a-151">Achse 4</span><span class="sxs-lookup"><span data-stu-id="7dc2a-151">Axis 4</span></span> </td><td> <span data-ttu-id="7dc2a-152">thumbstickposition. x</span><span class="sxs-lookup"><span data-stu-id="7dc2a-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-153">Thumbstick Y <i>(oben:-1,0, unten: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="7dc2a-154">Achse 2</span><span class="sxs-lookup"><span data-stu-id="7dc2a-154">Axis 2</span></span> </td><td> <span data-ttu-id="7dc2a-155">Achse 5</span><span class="sxs-lookup"><span data-stu-id="7dc2a-155">Axis 5</span></span> </td><td> <span data-ttu-id="7dc2a-156">thumbstickposition. y</span><span class="sxs-lookup"><span data-stu-id="7dc2a-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-157">Thumbstick gedrückt</span><span class="sxs-lookup"><span data-stu-id="7dc2a-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="7dc2a-158">Schaltfläche 8</span><span class="sxs-lookup"><span data-stu-id="7dc2a-158">Button 8</span></span> </td><td> <span data-ttu-id="7dc2a-159">Schaltfläche 9</span><span class="sxs-lookup"><span data-stu-id="7dc2a-159">Button 9</span></span> </td><td> <span data-ttu-id="7dc2a-160">thumbstickpressed</span><span class="sxs-lookup"><span data-stu-id="7dc2a-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-161">Touchpad X <i>(Links:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="7dc2a-162">Achse 17 \*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="7dc2a-163">Achse 19 \*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="7dc2a-164">touchpadposition. x</span><span class="sxs-lookup"><span data-stu-id="7dc2a-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-165">Touchpad Y <i>(oben:-1,0, unten: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="7dc2a-166">Achse 18 \*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="7dc2a-167">Achse 20 \*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="7dc2a-168">touchpadposition. y</span><span class="sxs-lookup"><span data-stu-id="7dc2a-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-169">Touchpad berührt</span><span class="sxs-lookup"><span data-stu-id="7dc2a-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="7dc2a-170">Schaltfläche 18 \*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-170">Button 18\*</span></span> </td><td> <span data-ttu-id="7dc2a-171">Schaltfläche 19 \*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-171">Button 19\*</span></span> </td><td> <span data-ttu-id="7dc2a-172">touchpadtouched</span><span class="sxs-lookup"><span data-stu-id="7dc2a-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-173">Touchpad gedrückt</span><span class="sxs-lookup"><span data-stu-id="7dc2a-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="7dc2a-174">Schaltfläche 16 \*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-174">Button 16\*</span></span> </td><td> <span data-ttu-id="7dc2a-175">Schaltfläche 17 \*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-175">Button 17\*</span></span> </td><td> <span data-ttu-id="7dc2a-176">touchpadpressed</span><span class="sxs-lookup"><span data-stu-id="7dc2a-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-177">6DOF-Zieh Punkt Pose oder Zeiger Pose</span><span class="sxs-lookup"><span data-stu-id="7dc2a-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="7dc2a-178"><i></i> Nur Ziehpunkt: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Inputtracking. getlocalposition</a></span><span class="sxs-lookup"><span data-stu-id="7dc2a-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="7dc2a-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Input Tracking. getlocalrotation</a></span><span class="sxs-lookup"><span data-stu-id="7dc2a-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="7dc2a-180">Pass <i>-</i> oder <i>Zeiger</i> als Argument: SourceState. sourcepose. trygetposition</span><span class="sxs-lookup"><span data-stu-id="7dc2a-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="7dc2a-181">SourceState. sourcepose. trygetrotation</span><span class="sxs-lookup"><span data-stu-id="7dc2a-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-182">Nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="7dc2a-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="7dc2a-183"><i>Die Positionsgenauigkeit und das Risiko von Quell Verlusten sind nur über die Mr-spezifische API verfügbar.</i> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="7dc2a-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">SourceState. sourcepose. positionaccuracy</a></span><span class="sxs-lookup"><span data-stu-id="7dc2a-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="7dc2a-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourcelossrisk</a></span><span class="sxs-lookup"><span data-stu-id="7dc2a-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="7dc2a-186">Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für openvr verwendet, aufgrund von Konflikten in den von Gamepads, oculus Touchscreen und openvr verwendeten Zuordnungen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

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


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="7dc2a-187">Ziehpunkt im Vergleich zu Zeige darstellen</span><span class="sxs-lookup"><span data-stu-id="7dc2a-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="7dc2a-188">Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="7dc2a-189">Der Entwurf eines Controllers unterscheidet sich in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung, die apps zum zeigen beim Rendern des Controllers verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="7dc2a-190">Um diese Controller besser darzustellen, gibt es zwei Arten von Posen, die Sie für jede Interaktions Quelle untersuchen können, die Ziehpunkt- **und die** **Zeiger** Darstellung.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="7dc2a-191">Sowohl die Ziehpunkt-als auch die zeigerpose-Koordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="7dc2a-192">Ziehpunkt darstellen</span><span class="sxs-lookup"><span data-stu-id="7dc2a-192">Grip pose</span></span>

<span data-ttu-id="7dc2a-193">Der Ziehpunkt stellt den Speicherort der Benutzer- **Palm dar,** der entweder von einem hololens oder einem Bewegungs Controller erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="7dc2a-194">Bei immersiven Headsets wird die Zieh Punkt Darstellung am besten zum Rendering **der Benutzer Hand** oder eines Objekts verwendet, das **in der Hand des Benutzers gespeichert** ist.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="7dc2a-195">Die Zieh Punkt Darstellung wird auch bei der Visualisierung eines Bewegungs Controllers verwendet.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="7dc2a-196">Das **zum Rendern-Modell** , das von Windows für einen Motion-Controller bereitgestellt wird, verwendet die Zieh Punkt Pose als Ursprung und Mittelpunkt der Drehung.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="7dc2a-197">Die Ziehpunkt-Pose wird wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="7dc2a-198">Die Zieh **Punktposition**: der Palmen Schwerpunkt bei der natürlichen Aufbewahrung des Controllers, nach links oder rechts, um die Position im Ziehpunkt zu zentrieren.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="7dc2a-199">Auf dem Windows Mixed Reality Motion Controller richtet sich diese Position im Allgemeinen nach der Schaltfläche "verstehen".</span><span class="sxs-lookup"><span data-stu-id="7dc2a-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="7dc2a-200">Die **Rechte Achse** der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist das Strahl-Ray, das normal ist (vorwärts von links nach links, rückwärts von rechter Palme).</span><span class="sxs-lookup"><span data-stu-id="7dc2a-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="7dc2a-201">Die **Forward-Achse** der Ziehpunkt Ausrichtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das durch ihre nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="7dc2a-202">Die **aufwärts Achse** der Ziehpunkt Ausrichtung: die aufwärts Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="7dc2a-203">Sie können auf die Ziehpunkt-Pose über die Anbieter übergreifende Eingabe-API von Unity (XR) zugreifen *[. Inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Getlocalposition/Rotation*) oder über die Windows-spezifische API (*SourceState. sourcepose. trygetposition/Rotation*), die die Daten für den **Zieh Knoten** anfordert.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="7dc2a-204">Zeiger Pose</span><span class="sxs-lookup"><span data-stu-id="7dc2a-204">Pointer pose</span></span>

<span data-ttu-id="7dc2a-205">Die **Zeiger** Darstellung stellt die Spitze des Controllers dar, der vorwärts zeigt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="7dc2a-206">Die vom System bereitgestellte Zeiger Darstellung eignet sich am besten für raycast, wenn Sie **das Controller Modell selbst Rendern**.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="7dc2a-207">Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers (z. b. eine virtuelle Pistole) rendern, sollten Sie auf einen Strahl zeigen, der für das virtuelle Objekt am natürlichsten ist, z. b. ein Strahl, der auf dem Barrel des App-defined Gun-Modells verläuft.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="7dc2a-208">Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das verweisen mit dem virtuellen Objekt für diejenigen, die Ihre APP verwenden, wahrscheinlich natürlicher.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="7dc2a-209">Derzeit ist die Zeiger Pose in Unity nur über die Windows Mr-spezifische API, *SourceState. sourcepose. trygetposition/Rotation* verfügbar, wobei *interaktionsourcenode. Pointer* als Argument übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="7dc2a-210">Controller nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="7dc2a-210">Controller tracking state</span></span>

<span data-ttu-id="7dc2a-211">Wie bei den Headsets ist für Windows Mixed Reality Motion Controller das Einrichten externer nach Verfolgungs Sensoren nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="7dc2a-212">Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="7dc2a-213">Wenn der Benutzer die Controller aus der Ansicht des Dashboards verschiebt, werden die Controller Positionen in den meisten Fällen von Windows weiter abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="7dc2a-214">Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="7dc2a-215">An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="7dc2a-216">Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können normal funktionieren, ohne dass der Benutzer das merkt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="7dc2a-217">Die beste Möglichkeit, dies zu erreichen, besteht darin, es selbst auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-217">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="7dc2a-218">Sehen Sie sich dieses Video mit Beispielen für den immersiven Inhalt an, der mit Motion-Controllern über verschiedene Überwachungs Zustände hinweg funktioniert:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-218">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="7dc2a-219">Grund für die explizite Nachverfolgung des Zustands</span><span class="sxs-lookup"><span data-stu-id="7dc2a-219">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="7dc2a-220">Apps, die Positionen basierend auf dem nach verfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und die Eigenschaften des Controller Zustands überprüfen, z. b. *sourcelossrisk* und *positionaccuracy*:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-220">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="7dc2a-221">Nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="7dc2a-221">Tracking state</span></span> </th><th> <span data-ttu-id="7dc2a-222">Sourcelossrisk</span><span class="sxs-lookup"><span data-stu-id="7dc2a-222">SourceLossRisk</span></span> </th><th> <span data-ttu-id="7dc2a-223">Positionsgenauigkeit</span><span class="sxs-lookup"><span data-stu-id="7dc2a-223">PositionAccuracy</span></span> </th><th> <span data-ttu-id="7dc2a-224">Trygetposition</span><span class="sxs-lookup"><span data-stu-id="7dc2a-224">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7dc2a-225"><b>Hohe Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-225"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="7dc2a-226">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="7dc2a-226">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7dc2a-227">Hoch</span><span class="sxs-lookup"><span data-stu-id="7dc2a-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7dc2a-228">true</span><span class="sxs-lookup"><span data-stu-id="7dc2a-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-229"><b>Hohe Genauigkeit (Risiko eines Verlusts)</b> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-229"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="7dc2a-230">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="7dc2a-230">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7dc2a-231">Hoch</span><span class="sxs-lookup"><span data-stu-id="7dc2a-231">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7dc2a-232">true</span><span class="sxs-lookup"><span data-stu-id="7dc2a-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-233"><b>Ungefähre Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-233"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="7dc2a-234">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="7dc2a-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="7dc2a-235">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="7dc2a-235">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7dc2a-236">true</span><span class="sxs-lookup"><span data-stu-id="7dc2a-236">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7dc2a-237"><b>Keine Position</b> </span><span class="sxs-lookup"><span data-stu-id="7dc2a-237"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="7dc2a-238">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="7dc2a-238">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="7dc2a-239">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="7dc2a-239">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="7dc2a-240">false</span><span class="sxs-lookup"><span data-stu-id="7dc2a-240">false</span></span></td>
</tr>
</table>

<span data-ttu-id="7dc2a-241">Diese Motion Controller-Überwachungs Zustände werden wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-241">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="7dc2a-242">**Hohe Genauigkeit:** Während sich der Motion-Controller in der Ansicht des Dashboards befindet, stellt er im Allgemeinen hohe Genauigkeits Positionen auf der Grundlage der visuellen Nachverfolgung bereit.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-242">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="7dc2a-243">Ein beweglicher Controller, der das Sichtfeld vorübergehend verlässt oder vorübergehend von den Headset-Sensoren (z. b. durch die andere Seite des Benutzers) verdeckt wird, gibt weiterhin hohe Genauigkeit für kurze Zeit zurück, basierend auf der Trägheits Verfolgung des Controllers.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-243">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="7dc2a-244">**Hohe Genauigkeit (Risiko des Verlusts):** Wenn der Benutzer den Bewegungs Controller über den Rand des Felds der Ansicht bewegt, kann das Headset die Position des Controllers in Kürze nicht visuell nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-244">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="7dc2a-245">Die APP weiß, wann der Controller diese FOV-Grenze erreicht hat, indem er den **sourcelossrisk** -REACH-1,0 sieht.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-245">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="7dc2a-246">An diesem Punkt kann die APP die Controller Gesten anhalten, die einen stabilen Stream von qualitativ hochwertigen Posen erfordern.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-246">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="7dc2a-247">**Ungefähre Genauigkeit:** Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-247">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="7dc2a-248">An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-248">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="7dc2a-249">Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können so normal agieren, dass Sie in der ungefähren Genauigkeit nicht bemerkt werden</span><span class="sxs-lookup"><span data-stu-id="7dc2a-249">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="7dc2a-250">Bei apps mit schwereren Eingabe Anforderungen ist es möglicherweise sinnvoll, diesen Löschvorgang von **hoher** Genauigkeit zur **ungefähren** Genauigkeit zu verstehen, indem die **positionaccuracy** -Eigenschaft überprüft wird, z. b. um dem Benutzer während dieses Zeitraums eine eher großzügigere Position in den offscreenzielen zu geben.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-250">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="7dc2a-251">**Keine Position:** Wenngleich der Controller für einen längeren Zeitraum mit der ungefähren Genauigkeit arbeiten kann, weiß das System manchmal, dass auch eine durch den Text gesperrten Position nicht sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-251">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="7dc2a-252">Beispielsweise kann ein Controller, der eingeschaltet wurde, nie visuell beobachtet werden, oder ein Benutzer kann einen Controller ablegen, der dann von einer anderen Person abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-252">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="7dc2a-253">Zu diesen Zeitpunkten stellt das System keine Position für die APP bereit, und *trygetposition* gibt false zurück.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-253">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="7dc2a-254">Allgemeine Unity-APIs (Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-254">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="7dc2a-255">**Namespace:** *unityengine*, *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-255">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="7dc2a-256">**Typen**: *Input*, *XR. Inputtracking*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-256">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="7dc2a-257">Unity verwendet derzeit die allgemeinen *Input. getbutton/Input. getaxis-* APIs, um Eingaben für [das Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [das openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality, einschließlich der Hands-und Motion-Controller, verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-257">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="7dc2a-258">Wenn Ihre APP diese APIs für die Eingabe verwendet, kann Sie Bewegungs Controller über mehrere XR-sdche hinweg unterstützen, einschließlich Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-258">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="7dc2a-259">Der gedrückte Zustand einer logischen Schaltfläche wird erhalten.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-259">Getting a logical button's pressed state</span></span>

<span data-ttu-id="7dc2a-260">Wenn Sie die allgemeinen Unity-Eingabe-APIs verwenden möchten, beginnen Sie in der Regel mit dem Verknüpfen von Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), und binden Sie eine Schaltfläche oder eine Achsen-ID an jeden Namen</span><span class="sxs-lookup"><span data-stu-id="7dc2a-260">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="7dc2a-261">Anschließend können Sie Code schreiben, der auf den Namen der logischen Schaltfläche/Achse verweist.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-261">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="7dc2a-262">Um z. b. die triggerschaltfläche des linken Bewegungs Controllers der Aktion senden zuzuordnen, wechseln Sie zu **Edit > Project Settings > Input** in Unity, und erweitern Sie die Eigenschaften des Abschnitts übermitteln unter Achsen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-262">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="7dc2a-263">Ändern Sie die Schaltfläche **positiv** oder **alt positive Schaltfläche** , um die Schaltfläche "Taste **14**" wie folgt zu lesen:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-263">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="7dc2a-264">![InputManager von Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-264">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="7dc2a-265">*Unity-InputManager*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-265">*Unity InputManager*</span></span>

<span data-ttu-id="7dc2a-266">Das Skript kann dann mithilfe von " *Input. getbutton*" die Aktion "Senden" überprüfen:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-266">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="7dc2a-267">Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **size** -Eigenschaft unter **Achsen** ändern.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-267">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="7dc2a-268">Direktes drücken des gedrückten Zustands einer physischen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="7dc2a-268">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="7dc2a-269">Sie können mithilfe von *Input. GetKey* auch manuell mit dem voll qualifizierten Namen auf Schaltflächen zugreifen:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-269">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="7dc2a-270">Die Pose eines Hand-oder Bewegungs Controllers</span><span class="sxs-lookup"><span data-stu-id="7dc2a-270">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="7dc2a-271">Sie können auf die Position und Drehung des Controllers mithilfe von *XR zugreifen. Inputtracking*:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-271">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="7dc2a-272">Der obige Code stellt die Zieh Punktposition des Controllers dar (in der der Benutzer den Controller hält). Dies ist nützlich, um ein Schwert oder eine Waffe in der Hand des Benutzers oder ein Modell des Controllers selbst zu rendern.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-272">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="7dc2a-273">Die Beziehung zwischen diesem Ziehpunkt und der Zeiger Pose (bei der die Spitze des Controllers zeigt) kann sich zwischen Controllern unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-273">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="7dc2a-274">Zurzeit ist der Zugriff auf die Zeiger-Pose des Controllers nur über die in den folgenden Abschnitten beschriebene Mr-spezifische Eingabe-API möglich.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-274">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="7dc2a-275">Windows-spezifische APIs (XR. WSA. Der</span><span class="sxs-lookup"><span data-stu-id="7dc2a-275">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="7dc2a-276">, Wenn Ihr Projekt einen der XR-verwendet. WSA-APIs werden nach dem XR SDK in zukünftigen Unity-Releases eingestellt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-276">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="7dc2a-277">Für neue Projekte wird empfohlen, das XR SDK von Anfang an zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-277">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="7dc2a-278">Weitere Informationen zum [XR-Eingabe System und](https://docs.unity3d.com/Manual/xr_input.html)zu den APIs finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-278">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="7dc2a-279">**Namespace:** *unityengine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-279">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="7dc2a-280">**Typen**: *interaktionsmanager*, *interaktionsourcestate*, *interaktionsource*, *interaktionsourceproperties*, *interaktionsourcekind*, *interaktionsourcelokation*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-280">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="7dc2a-281">Um ausführlichere Informationen zu Windows Mixed Reality-Hand Eingaben (für hololens) und Bewegungs Controller zu erhalten, können Sie die Windows-spezifischen räumlichen Eingabe-APIs im Namespace *unityengine. XR. WSA. Input* verwenden.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-281">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="7dc2a-282">Auf diese Weise können Sie auf zusätzliche Informationen zugreifen, wie z. b. Die Positionsgenauigkeit oder die quellart, sodass Sie die Hände und Controller voneinander trennen können.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-282">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="7dc2a-283">Abrufen des Zustands von Händen und Bewegungs Controllern</span><span class="sxs-lookup"><span data-stu-id="7dc2a-283">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="7dc2a-284">Sie können den Status dieses Frames für jede Interaktions Quelle (Hand-oder Bewegungs Controller) mithilfe der *getcurrentreading* -Methode abrufen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-284">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="7dc2a-285">Jedes *interaktionsourcestate* , das Sie zurückerhalten, stellt eine Interaktions Quelle zum aktuellen Zeitpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-285">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="7dc2a-286">Das *interaktionsourcestate* macht Informationen wie z. b.:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-286">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="7dc2a-287">Welche [Arten von Druck](../../design/motion-controllers.md) vorgehungen werden auftreten (Select/Menu/grasp/Touchpad/Thumbstick)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-287">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="7dc2a-288">Andere Daten, die für Bewegungs Controller spezifisch sind, z. b. die XY-Koordinaten des Touchpads und/oder Finger Ansichts Status</span><span class="sxs-lookup"><span data-stu-id="7dc2a-288">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="7dc2a-289">Interaktionsourcekind, um zu wissen, ob es sich bei der Quelle um einen Hand-oder Bewegungs Controller handelt</span><span class="sxs-lookup"><span data-stu-id="7dc2a-289">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="7dc2a-290">Abrufen von vorwärts vorhergesagten Renderingvorgängen</span><span class="sxs-lookup"><span data-stu-id="7dc2a-290">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="7dc2a-291">Beim Abrufen von Interaktions Quelldaten von Hand und Controllern sind die von Ihnen abzurufenden Datenquellen für den Zeitpunkt, zu dem die Daten des Bilds den Augen des Benutzers erreichen, von vorne vorhergesagte Posen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-291">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="7dc2a-292">Vorwärts vorhersagende Posen werden am besten zum **Rendern** des Controllers oder eines gehaltenen Objekts in jedem Frame verwendet.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-292">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="7dc2a-293">Wenn Sie ein bestimmtes Press-oder-Release mit dem Controller als Ziel verwenden, wird dies am genauesten sein, wenn Sie die unten beschriebenen Vergangenheits Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-293">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="7dc2a-294">Sie können auch die vorwärts Gesagte Kopfzeile für diesen aktuellen Frame erhalten.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-294">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="7dc2a-295">Wie bei der Quell Darstellung ist dies für das **Rendern** eines Cursors nützlich, obwohl das Ziel einer bestimmten Presse oder Freigabe am genauesten ist, wenn Sie die unten beschriebenen Vergangenheits Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-295">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="7dc2a-296">Behandeln von Interaktions Quell Ereignissen</span><span class="sxs-lookup"><span data-stu-id="7dc2a-296">Handling interaction source events</span></span>

<span data-ttu-id="7dc2a-297">Um Eingabeereignisse zu behandeln, wie Sie mit Ihren exakten Vergangenheits Daten auftreten, können Sie Interaktions Quell Ereignisse behandeln, anstatt Sie abzufragen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-297">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="7dc2a-298">So behandeln Sie Interaktions Quell Ereignisse:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-298">To handle interaction source events:</span></span>
* <span data-ttu-id="7dc2a-299">Registrieren Sie sich für ein *interaktionmanager* -Eingabe Ereignis.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-299">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="7dc2a-300">Für jede Art von Interaktions Ereignis, für das Sie sich interessieren, müssen Sie es abonnieren.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-300">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="7dc2a-301">Behandeln Sie das-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-301">Handle the event.</span></span> <span data-ttu-id="7dc2a-302">Wenn Sie ein Interaktions Ereignis abonniert haben, erhalten Sie gegebenenfalls den Rückruf.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-302">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="7dc2a-303">Im Beispiel " *sourcepressed* " ist dies der Fall, nachdem die Quelle erkannt wurde und bevor Sie freigegeben oder verloren geht.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-303">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="7dc2a-304">Beenden der Behandlung eines Ereignisses</span><span class="sxs-lookup"><span data-stu-id="7dc2a-304">How to stop handling an event</span></span>

<span data-ttu-id="7dc2a-305">Sie müssen die Behandlung eines Ereignisses beenden, wenn Sie nicht mehr an dem Ereignis interessiert sind oder das Objekt zerstören, das das Ereignis abonniert hat.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-305">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="7dc2a-306">Wenn Sie die Verarbeitung des Ereignisses beenden möchten, kündigen Sie das Ereignis an.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-306">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="7dc2a-307">Liste der Interaktions Quell Ereignisse</span><span class="sxs-lookup"><span data-stu-id="7dc2a-307">List of interaction source events</span></span>

<span data-ttu-id="7dc2a-308">Die folgenden Interaktions Quell Ereignisse sind verfügbar:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-308">The available interaction source events are:</span></span>
* <span data-ttu-id="7dc2a-309">*Interaktionsourceerkannt* (Quelle wird aktiv)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-309">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="7dc2a-310">*Interaktionsourcelost* (wird inaktiv)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-310">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="7dc2a-311">*Interaktionsourcepressed* (tippen, drücken der Schaltfläche oder "auswählen")</span><span class="sxs-lookup"><span data-stu-id="7dc2a-311">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="7dc2a-312">*Interaktionsourcereleasing* (Ende einer Tap-Schaltfläche, oder Ende der "Select"-Taste)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-312">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="7dc2a-313">*Interaktionsourceupveraltet* (verschieben oder anderweitig ändern eines Zustands)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-313">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="7dc2a-314">Ereignisse für Vergangenheits Ziele, die mit einem Press oder Release am genauesten zu vergleichen sind</span><span class="sxs-lookup"><span data-stu-id="7dc2a-314">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="7dc2a-315">Die zuvor beschriebenen Abruf-APIs machen Ihre APP-vorhergesagte Posen aus.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-315">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="7dc2a-316">Obwohl die vorhergesagten Posen am besten zum Rendern des Controllers oder eines virtuellen Hand Held Objekts geeignet sind, sind zukünftige Formen für das Ziel nicht optimal, aus zwei wichtigen Gründen:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-316">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="7dc2a-317">Wenn der Benutzer eine Schaltfläche auf einem Controller drückt, kann es ungefähr 20 ms drahtlose Latenz über Bluetooth geben, bevor das System den Druck erhält.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-317">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="7dc2a-318">Wenn Sie dann eine vorwärts Gesagte Pose verwenden, gibt es eine weitere 10-20 MS der Forward-Vorhersage, auf die die Uhrzeit angewendet wird, zu der die Daten des aktuellen Frames die Augen des Benutzers erreichen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-318">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="7dc2a-319">Dies bedeutet, dass bei der Abfrage eine Quell Pose oder eine Kopfzeile angezeigt wird, die 30-40 ms vorwärts ist, von wo aus die Kopfzeile des Benutzers und die Hände wieder zurück waren, als die Taste oder das Release aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="7dc2a-319">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="7dc2a-320">Bei der Eingabe von hololens-Hand Eingaben gibt es eine ähnliche Verarbeitungs Verzögerung, um den Druck zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-320">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="7dc2a-321">Um basierend auf der ursprünglichen Absicht des Benutzers für eine Hand oder einen Controller eine genaue Zielsetzung zu erreichen, sollten Sie die historische Quell Pose oder die Kopfzeile aus dem *interaktionsourcepressed* -oder *interaktionsourcereleasing* -Eingabe Ereignis verwenden.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-321">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="7dc2a-322">Sie können eine Presse oder eine Freigabe mit Verlaufs Daten des Benutzers oder des Controllers als Ziel haben:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-322">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="7dc2a-323">Die Kopfzeile zu dem Zeitpunkt, an dem eine Geste oder eine Controller Bewegung aufgetreten ist, die für die **Ziel** Bestimmung verwendet werden kann, um zu bestimmen, was der [Benutzer untersucht hat:](../../design/gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-323">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="7dc2a-324">Die Quell Pose zu dem Zeitpunkt, zu dem eine Bewegung des Bewegungs Controllers stattgefunden hat. diese kann verwendet werden, **um zu bestimmen** , auf welche Weise der Benutzer den Controller verwiesen hat.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-324">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="7dc2a-325">Dabei handelt es sich um den Zustand des Controllers, der den Druck erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-325">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="7dc2a-326">Wenn Sie den Controller selbst rendern, können Sie die Zeiger Darstellung anstelle der Ziehpunkt-Pose anfordern, um das Ziel-Ray von dem zu überprüfen, was der Benutzer für den natürlichen Tipp des gerenderten Controllers in Erwägung zieht:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-326">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="7dc2a-327">Beispiel für Ereignishandler</span><span class="sxs-lookup"><span data-stu-id="7dc2a-327">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="7dc2a-328">APIs für zusammengesetzte Gesten auf hoher Ebene (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-328">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="7dc2a-329">**Namespace:** *unityengine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-329">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="7dc2a-330">**Typen**: *GestureRecognizer*, *gesturesettings*, *interaktionsourcekind*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-330">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="7dc2a-331">Ihre APP kann auch zusammengesetzte Gesten auf höherer Ebene für räumliche Eingabe Quellen, Tap-, Halt-, Bearbeitungs-und Navigations Gesten erkennen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-331">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation, and Navigation gestures.</span></span> <span data-ttu-id="7dc2a-332">Mit dem GestureRecognizer können Sie diese zusammengesetzten Gesten sowohl in [Hand](../../design/gaze-and-commit.md#composite-gestures) -als auch in [Bewegungs Controllern](../../design/motion-controllers.md) erkennen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-332">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="7dc2a-333">Jedes Gesten Ereignis für den GestureRecognizer stellt sowohl sourcekind für die Eingabe als auch den Ziel-Head-Strahl zum Zeitpunkt des Ereignisses bereit.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-333">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="7dc2a-334">Einige Ereignisse bieten zusätzliche kontextspezifische Informationen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-334">Some events provide additional context-specific information.</span></span>

<span data-ttu-id="7dc2a-335">Es sind nur wenige Schritte erforderlich, um Gesten mithilfe einer Gestenerkennung zu erfassen:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-335">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="7dc2a-336">Erstellen einer neuen Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="7dc2a-336">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="7dc2a-337">Legen Sie fest, welche Gesten überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-337">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="7dc2a-338">Ereignisse für diese Gesten abonnieren</span><span class="sxs-lookup"><span data-stu-id="7dc2a-338">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="7dc2a-339">Erfassungs Gesten starten</span><span class="sxs-lookup"><span data-stu-id="7dc2a-339">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="7dc2a-340">Erstellen einer neuen Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="7dc2a-340">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="7dc2a-341">Wenn Sie den *GestureRecognizer* verwenden möchten, müssen Sie einen *GestureRecognizer* erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-341">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="7dc2a-342">Legen Sie fest, welche Gesten überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-342">Specify which gestures to watch for</span></span>

<span data-ttu-id="7dc2a-343">Geben Sie an, für welche Gesten Sie *sich über "*" in "" von "" "</span><span class="sxs-lookup"><span data-stu-id="7dc2a-343">Specify which gestures you're interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="7dc2a-344">Ereignisse für diese Gesten abonnieren</span><span class="sxs-lookup"><span data-stu-id="7dc2a-344">Subscribe to events for those gestures</span></span>

<span data-ttu-id="7dc2a-345">Abonnieren Sie Ereignisse für die Gesten, an denen Sie interessiert sind.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-345">Subscribe to events for the gestures you're interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="7dc2a-346">Navigations-und Manipulations Gesten schließen sich gegenseitig für eine Instanz eines *GestureRecognizer* aus.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-346">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="7dc2a-347">Erfassungs Gesten starten</span><span class="sxs-lookup"><span data-stu-id="7dc2a-347">Start capturing gestures</span></span>

<span data-ttu-id="7dc2a-348">Standardmäßig überwacht ein *GestureRecognizer* die Eingabe erst, wenn *startcapturinggesten ()* aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-348">By default, a *GestureRecognizer* doesn't monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="7dc2a-349">Möglicherweise wird ein Gesten Ereignis generiert, nachdem *stopcapturinggesten ()* aufgerufen wurde, wenn Eingaben vor dem Frame durchgeführt wurden, in dem *stopcapturinggesten ()* verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-349">It's possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="7dc2a-350">Der *GestureRecognizer* weiß, ob er während des vorherigen Frames, in dem die Geste tatsächlich aufgetreten ist, ein-oder ausgeschaltet war, und daher ist es zuverlässig, die Gesten Überwachung auf der Grundlage der Anzeige Ziele dieses Frames zu starten und zu beenden.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-350">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it's reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="7dc2a-351">Erfassungs Gesten nicht mehr</span><span class="sxs-lookup"><span data-stu-id="7dc2a-351">Stop capturing gestures</span></span>

<span data-ttu-id="7dc2a-352">So verhindern Sie die Gestenerkennung:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-352">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="7dc2a-353">Entfernen einer Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="7dc2a-353">Removing a gesture recognizer</span></span>

<span data-ttu-id="7dc2a-354">Denken Sie daran, abonnierte Ereignisse abzubestellen, bevor Sie ein *GestureRecognizer* -Objekt zerstören.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-354">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="7dc2a-355">Rendern des Motion Controller-Modells in Unity</span><span class="sxs-lookup"><span data-stu-id="7dc2a-355">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="7dc2a-356">![Motion Controller-Modell und-teleportierung](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-356">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="7dc2a-357">*Motion Controller-Modell und-teleportierung*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-357">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="7dc2a-358">Zum Rendering von Bewegungs Controllern in Ihrer APP, die den physischen Controllern entsprechen, die die Benutzer als verschiedene Schaltflächen verwenden, die Sie verwenden, können Sie die **vorfab von "mutioncontroller** " im [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)verwenden.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-358">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="7dc2a-359">Dieser Prefab lädt das korrekte gltf-Modell zur Laufzeit dynamisch aus dem installierten Motion Controller-Treiber des Systems.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-359">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="7dc2a-360">Es ist wichtig, dass diese Modelle dynamisch geladen werden, anstatt Sie manuell in den Editor zu importieren, damit Ihre APP physisch genaue 3D-Modelle für alle aktuellen und zukünftigen Controller anzeigt, die Ihre Benutzer möglicherweise haben.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-360">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="7dc2a-361">Befolgen Sie [die Anweisungen für die ersten](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) Schritte, um das Mixed Reality Toolkit herunterzuladen und es Ihrem Unity-Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-361">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="7dc2a-362">Wenn Sie Ihre Kamera durch das *mixedrealitycameraparent* -präfab im Rahmen der Schritte für die ersten Schritte ersetzt haben, können Sie es tun!</span><span class="sxs-lookup"><span data-stu-id="7dc2a-362">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="7dc2a-363">Dieses präfab umfasst das Rendern von Bewegungs Controllern.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-363">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="7dc2a-364">Andernfalls fügen Sie *Assets/holotoolkit/Input/Prefabs/mutioncontrollers. Prefab* aus dem Projektbereich in die Szene ein.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-364">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="7dc2a-365">Sie sollten diese Prefab als untergeordnetes Element eines beliebigen übergeordneten Objekts hinzufügen, das Sie verwenden, um die Kamera zu bewegen, wenn der Benutzer in der Szene Teleports verwendet, sodass die Controller mit dem Benutzer zusammenkommen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-365">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="7dc2a-366">Wenn Ihre APP keine teleportierung umfasst, fügen Sie einfach die vorfab im Stammverzeichnis Ihrer Szene hinzu.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-366">If your app doesn't involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="7dc2a-367">Auslösen von Objekten</span><span class="sxs-lookup"><span data-stu-id="7dc2a-367">Throwing objects</span></span>

<span data-ttu-id="7dc2a-368">Das Auslösen von Objekten in Virtual Reality ist ein schwierigeres Problem, als es möglicherweise zum ersten Mal erscheint.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-368">Throwing objects in virtual reality is a harder problem than it may at first seem.</span></span> <span data-ttu-id="7dc2a-369">Wie bei den meisten physisch basierenden Interaktionen verhält es sich, wenn das Auslösen im Spiel unerwartet funktioniert, sofort offensichtlich und unterbricht das eintauchen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-369">As with most physically based interactions, when throwing in game acts in an unexpected way, it's immediately obvious and breaks immersion.</span></span> <span data-ttu-id="7dc2a-370">Wir haben einige Zeit damit verbracht, ein physisch korrektes auslösverhalten darzustellen, und haben einige Richtlinien, die über Updates auf unserer Plattform aktiviert wurden, für Sie freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-370">We've spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="7dc2a-371">Ein Beispiel für die Implementierung von "throw" finden Sie [hier](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="7dc2a-371">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="7dc2a-372">Dieses Beispiel befolgt diese vier Richtlinien:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-372">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="7dc2a-373">**Verwenden Sie die *Geschwindigkeit* des Controllers anstelle der Position**.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-373">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="7dc2a-374">Im November-Update für Windows haben wir eine Änderung des Verhaltens eingeführt, wenn der [ungefähre Status der Positionsüberwachung ("ungefähre"](../../design/motion-controllers.md#controller-tracking-state)) ist.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-374">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="7dc2a-375">In diesem Zustand werden Velocity-Informationen über den Controller weiterhin gemeldet, solange wir der hohen Genauigkeit glauben, was häufig länger ist als die Position mit hoher Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-375">When in this state, velocity information about the controller will continue to be reported for as long as we believe its high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="7dc2a-376">**Integrieren Sie die *Winkelgeschwindigkeit* des Controllers**.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-376">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="7dc2a-377">Diese Logik ist in der- `throwing.cs` Datei in der `GetThrownObjectVelAngVel` statischen-Methode innerhalb des oben verknüpften Pakets enthalten:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-377">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="7dc2a-378">Wenn die Angular-Geschwindigkeit beibehalten wird, muss das ausgelöste Objekt dieselbe Angular-Geschwindigkeit wie in der Zeit der throw-Ausnahme beibehalten: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="7dc2a-378">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="7dc2a-379">Da sich der Mittelpunkt der Masse des ausgelösten Objekts wahrscheinlich nicht am Ursprung der Ziehpunkt-Pose befindet, weist es wahrscheinlich eine andere Geschwindigkeit auf als die des Controllers im Frame des Verweises des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-379">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity than that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="7dc2a-380">Der Teil der auf diese Weise beigetragenen Geschwindigkeit des Objekts ist die sofortige tangential Geschwindigkeit des Mittelpunkts der Masse des ausgelösten Objekts um den Controller Ursprung.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-380">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="7dc2a-381">Diese tangential-Geschwindigkeit ist das Kreuz Produkt der Angular-Geschwindigkeit des Controllers mit dem Vektor, der den Abstand zwischen dem Controller Ursprung und dem Mittelpunkt der Masse des ausgelösten Objekts darstellt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-381">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="7dc2a-382">Die Gesamtgeschwindigkeit des ausgelösten Objekts ist die Summe der Geschwindigkeit des Controllers und der tangential Geschwindigkeit: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="7dc2a-382">The total velocity of the thrown object is the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="7dc2a-383">Achten **Sie genau auf die *Zeit* , zu der wir die Geschwindigkeit anwenden**.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-383">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="7dc2a-384">Wenn eine Schaltfläche gedrückt wird, kann es bis zu 20 ms dauern, bis das Ereignis durch Bluetooth bis zum Betriebssystem hochskalieren kann.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-384">When a button is pressed, it can take up to 20 ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="7dc2a-385">Dies bedeutet Folgendes: Wenn Sie eine Änderung des Controller Zustands von gedrückte in nicht gedrückt oder umgekehrt durchführt, werden die Informationen, die Sie mit dem Controller erhalten, tatsächlich vor dieser Zustandsänderung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-385">This means that if you poll for a controller state change from pressed to not pressed or the other way around, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="7dc2a-386">Darüber hinaus wird die von unserer Abruf-API dargestellte Controller Darstellung vorhergesagt, um zu dem Zeitpunkt, zu dem der Rahmen angezeigt wird, eine wahrscheinliche Darstellung darzustellen, die in der Zukunft mehr als 20 ms betragen kann.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-386">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more than 20 ms in the future.</span></span> <span data-ttu-id="7dc2a-387">Dies eignet sich gut für das *Rendern* von gehaltenen Objekten, aber ist unser Zeitproblem für das *Ziel des Objekts* , da wir den Weg für den Zeitpunkt berechnen, zu dem der Benutzer den Throw losgelassen hat.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-387">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released the throw.</span></span> <span data-ttu-id="7dc2a-388">Wenn Sie mit dem November-Update ein Unity-Ereignis wie *interaktionsourcepressed* oder *interaktionsourcereleasing* gesendet haben, enthält der Zustand glücklicherweise die Vergangenheits Daten von hinten, wenn die Schaltfläche gedrückt oder freigegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-388">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was pressed or released.</span></span>  <span data-ttu-id="7dc2a-389">Um das präzisere Controller Rendering und die Zielplattform für das Ausführen von Triggeroptionen zu erhalten, müssen Sie nach Bedarf Abruf-und Ereignis Ereignisse ordnungsgemäß verwenden:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-389">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="7dc2a-390">Für den Controller, der die einzelnen Frames **rendert** , sollte Ihre APP das *gameobject* des Controllers an der vorwärts Gesagten Controller Darstellung für die Photon-Zeit des aktuellen Frames positionieren.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-390">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="7dc2a-391">Sie erhalten diese Daten von Unity-Abruf-APIs wie *[XR. Inputtracking. getlocalposition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oder *[XR. WSA. Input. interaktionmanager. getcurrentreading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-391">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="7dc2a-392">Für den Controller, der auf eine Presse oder ein Release **abzielt** , sollte Ihre APP auf der Grundlage der Verlaufs Controller-Pose für das Press-oder releaseereignis auf der Grundlage der Verlaufs Controller-</span><span class="sxs-lookup"><span data-stu-id="7dc2a-392">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="7dc2a-393">Sie erhalten diese Daten aus den Unity-Ereignis-APIs, wie z. b. *[interaktionmanager. interaktionsourcepressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-393">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="7dc2a-394">**Verwenden Sie die** Ziehpunkt-Pose.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-394">**Use the grip pose**.</span></span> <span data-ttu-id="7dc2a-395">Winkelgeschwindigkeit und-Geschwindigkeit werden relativ zur Zieh Punkt Pose, nicht zum Darstellen von Zeigern, angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-395">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="7dc2a-396">Das auslösen wird mit zukünftigen Windows-Updates weiter verbessern, und Sie können davon ausgehen, dass Sie hier weitere Informationen finden.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-396">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="7dc2a-397">Gesten-und Bewegungs Controller in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="7dc2a-397">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="7dc2a-398">Sie können über den Eingabe-Manager auf Gesten-und Bewegungs Controller zugreifen.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-398">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="7dc2a-399">Geste in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="7dc2a-399">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="7dc2a-400">Motion Controller in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="7dc2a-400">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="7dc2a-401">Immer am Ball mit Tutorials</span><span class="sxs-lookup"><span data-stu-id="7dc2a-401">Follow along with tutorials</span></span>

<span data-ttu-id="7dc2a-402">Schritt-für-Schritt-Tutorials mit ausführlicheren Anpassungs Beispielen sind in der Mixed Reality Academy verfügbar:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-402">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="7dc2a-403">MR-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="7dc2a-403">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="7dc2a-404">MR-Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="7dc2a-404">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="7dc2a-405">[![Mr-Eingabe 213-Motion Controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="7dc2a-405">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="7dc2a-406">*Mr-Eingabe 213-Motion Controller*</span><span class="sxs-lookup"><span data-stu-id="7dc2a-406">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7dc2a-407">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="7dc2a-407">Next Development Checkpoint</span></span>

<span data-ttu-id="7dc2a-408">Wenn Sie der Unity-Entwicklungs Journey folgen, die wir angelegt haben, befinden Sie sich mitten in der Untersuchung der mrtk Core-Bausteine.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-408">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="7dc2a-409">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-409">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7dc2a-410">Hand- und Eye-Tracking</span><span class="sxs-lookup"><span data-stu-id="7dc2a-410">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="7dc2a-411">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="7dc2a-411">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7dc2a-412">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="7dc2a-412">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="7dc2a-413">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="7dc2a-413">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7dc2a-414">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7dc2a-414">See also</span></span>

* [<span data-ttu-id="7dc2a-415">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="7dc2a-415">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="7dc2a-416">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="7dc2a-416">Motion controllers</span></span>](../../design/motion-controllers.md)
