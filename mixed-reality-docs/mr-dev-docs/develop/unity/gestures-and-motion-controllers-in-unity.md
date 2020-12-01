---
title: Gesten und Motion-Controller in Unity
description: Erfahren Sie, wie Sie mithilfe von Handgesten und Bewegungs Controllern Maßnahmen für Ihren Blick in Unity durchführen können.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Gesten, Bewegungs Controller, Unity, Blick, Eingabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 122642bb7fc561e505098bca00b8bf65bfd4552e
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443582"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="b7a2c-104">Gesten und Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="b7a2c-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="b7a2c-105">Es gibt zwei wichtige Möglichkeiten, um Ihre [Blicke in Unity](gaze-in-unity.md), [Handgesten](../../design/gaze-and-commit.md#composite-gestures) und [Bewegungs Controllern](../../design/motion-controllers.md) in hololens und immersiven HMD zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="b7a2c-106">Sie greifen über dieselben APIs in Unity auf die Daten für beide Quellen räumlicher Eingaben zu.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="b7a2c-107">Unity bietet zwei Hauptmethoden für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality, die gängigen *Input. getbutton/Input. getaxis-* APIs, die über mehrere Unity-XR-sdker hinweg verwendet werden können, sowie eine *interaktionmanager/GestureRecognizer-* API speziell für Windows Mixed Reality, das den vollständigen Satz räumlicher Eingabedaten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="b7a2c-108">Eingabe-APIs für Unity XR</span><span class="sxs-lookup"><span data-stu-id="b7a2c-108">Unity XR input APIs</span></span>

<span data-ttu-id="b7a2c-109">Bei neuen Projekten wird die Verwendung der neuen XR-Eingabe-APIs von Anfang an empfohlen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-109">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="b7a2c-110">Weitere Informationen zu den [XR-APIs](https://docs.unity3d.com/Manual/xr_input.html)finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-110">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="b7a2c-111">Unity-Schaltfläche/Achsen Zuordnung (Tabelle)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-111">Unity button/axis mapping table</span></span>

<span data-ttu-id="b7a2c-112">Die Schaltflächen-und Achsen-IDs in der folgenden Tabelle werden im Unity-Eingabe-Manager für Windows Mixed Reality Motion Controller über die *Eingabe. getbutton/getaxis* -APIs unterstützt, während die Spalte "Windows Mr-spezifisch" auf Eigenschaften verweist, die aus dem *interaktionsourcestate* -Typ verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-112">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="b7a2c-113">Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-113">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="b7a2c-114">Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality entsprechen im Allgemeinen den Oculus-Schaltflächen-/Achsen-IDs</span><span class="sxs-lookup"><span data-stu-id="b7a2c-114">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="b7a2c-115">Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality unterscheiden sich auf zwei Arten von den Zuordnungen von openvr:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-115">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="b7a2c-116">Die Zuordnung verwendet Touchpad-IDs, die sich vom Finger Stick unterscheiden, um Controller mit beiden Fingerabdrücken und Touchpads zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-116">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="b7a2c-117">Durch die Zuordnung wird vermieden, dass die Schaltflächen-IDs A und X für die Menü Schaltflächen überladen werden, damit Sie für physische abxy-Schaltflächen verfügbar</span><span class="sxs-lookup"><span data-stu-id="b7a2c-117">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="b7a2c-118">Eingabe</span><span class="sxs-lookup"><span data-stu-id="b7a2c-118">Input</span></span> </th><th colspan="2"><span data-ttu-id="b7a2c-119"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a></span><span class="sxs-lookup"><span data-stu-id="b7a2c-119"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="b7a2c-120">(Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-120">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="b7a2c-121"><a href="gestures-and-motion-controllers-in-unity.md#">Windows-spezifische Eingabe-API</a></span><span class="sxs-lookup"><span data-stu-id="b7a2c-121"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="b7a2c-122">XR. WSA. Der</span><span class="sxs-lookup"><span data-stu-id="b7a2c-122">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="b7a2c-123">Links</span><span class="sxs-lookup"><span data-stu-id="b7a2c-123">Left hand</span></span> </th><th> <span data-ttu-id="b7a2c-124">Rechte Seite</span><span class="sxs-lookup"><span data-stu-id="b7a2c-124">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="b7a2c-125">Select-Taste gedrückt</span><span class="sxs-lookup"><span data-stu-id="b7a2c-125">Select trigger pressed</span></span> </td><td> <span data-ttu-id="b7a2c-126">Achse 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="b7a2c-126">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="b7a2c-127">Achse 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="b7a2c-127">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="b7a2c-128">selectpressed</span><span class="sxs-lookup"><span data-stu-id="b7a2c-128">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-129">Auswählen des analogen Auslöse Werts</span><span class="sxs-lookup"><span data-stu-id="b7a2c-129">Select trigger analog value</span></span> </td><td> <span data-ttu-id="b7a2c-130">Achse 9</span><span class="sxs-lookup"><span data-stu-id="b7a2c-130">Axis 9</span></span> </td><td> <span data-ttu-id="b7a2c-131">Achse 10</span><span class="sxs-lookup"><span data-stu-id="b7a2c-131">Axis 10</span></span> </td><td> <span data-ttu-id="b7a2c-132">selectpressedamount</span><span class="sxs-lookup"><span data-stu-id="b7a2c-132">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-133">Select-Taste teilweise gedrückt</span><span class="sxs-lookup"><span data-stu-id="b7a2c-133">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="b7a2c-134">Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-134">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b7a2c-135">Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-135">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b7a2c-136">selectpressedamount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="b7a2c-136">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-137">Menü Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="b7a2c-137">Menu button pressed</span></span> </td><td> <span data-ttu-id="b7a2c-138">Schaltfläche 6 \*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-138">Button 6\*</span></span> </td><td> <span data-ttu-id="b7a2c-139">Schaltfläche 7 \*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-139">Button 7\*</span></span> </td><td> <span data-ttu-id="b7a2c-140">menupressed</span><span class="sxs-lookup"><span data-stu-id="b7a2c-140">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-141">Zieh Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="b7a2c-141">Grip button pressed</span></span> </td><td> <span data-ttu-id="b7a2c-142">Achse 11 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-142">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="b7a2c-143">Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-143">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b7a2c-144">Achse 12 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-144">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="b7a2c-145">Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-145">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b7a2c-146">Schna</span><span class="sxs-lookup"><span data-stu-id="b7a2c-146">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-147">Thumbstick X <i>(Links:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-147">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="b7a2c-148">Achse 1</span><span class="sxs-lookup"><span data-stu-id="b7a2c-148">Axis 1</span></span> </td><td> <span data-ttu-id="b7a2c-149">Achse 4</span><span class="sxs-lookup"><span data-stu-id="b7a2c-149">Axis 4</span></span> </td><td> <span data-ttu-id="b7a2c-150">thumbstickposition. x</span><span class="sxs-lookup"><span data-stu-id="b7a2c-150">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-151">Thumbstick Y <i>(oben:-1,0, unten: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-151">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="b7a2c-152">Achse 2</span><span class="sxs-lookup"><span data-stu-id="b7a2c-152">Axis 2</span></span> </td><td> <span data-ttu-id="b7a2c-153">Achse 5</span><span class="sxs-lookup"><span data-stu-id="b7a2c-153">Axis 5</span></span> </td><td> <span data-ttu-id="b7a2c-154">thumbstickposition. y</span><span class="sxs-lookup"><span data-stu-id="b7a2c-154">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-155">Thumbstick gedrückt</span><span class="sxs-lookup"><span data-stu-id="b7a2c-155">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="b7a2c-156">Schaltfläche 8</span><span class="sxs-lookup"><span data-stu-id="b7a2c-156">Button 8</span></span> </td><td> <span data-ttu-id="b7a2c-157">Schaltfläche 9</span><span class="sxs-lookup"><span data-stu-id="b7a2c-157">Button 9</span></span> </td><td> <span data-ttu-id="b7a2c-158">thumbstickpressed</span><span class="sxs-lookup"><span data-stu-id="b7a2c-158">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-159">Touchpad X <i>(Links:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-159">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="b7a2c-160">Achse 17 \*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-160">Axis 17\*</span></span> </td><td> <span data-ttu-id="b7a2c-161">Achse 19 \*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-161">Axis 19\*</span></span> </td><td> <span data-ttu-id="b7a2c-162">touchpadposition. x</span><span class="sxs-lookup"><span data-stu-id="b7a2c-162">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-163">Touchpad Y <i>(oben:-1,0, unten: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-163">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="b7a2c-164">Achse 18 \*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-164">Axis 18\*</span></span> </td><td> <span data-ttu-id="b7a2c-165">Achse 20 \*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-165">Axis 20\*</span></span> </td><td> <span data-ttu-id="b7a2c-166">touchpadposition. y</span><span class="sxs-lookup"><span data-stu-id="b7a2c-166">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-167">Touchpad berührt</span><span class="sxs-lookup"><span data-stu-id="b7a2c-167">Touchpad touched</span></span> </td><td> <span data-ttu-id="b7a2c-168">Schaltfläche 18 \*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-168">Button 18\*</span></span> </td><td> <span data-ttu-id="b7a2c-169">Schaltfläche 19 \*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-169">Button 19\*</span></span> </td><td> <span data-ttu-id="b7a2c-170">touchpadtouched</span><span class="sxs-lookup"><span data-stu-id="b7a2c-170">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-171">Touchpad gedrückt</span><span class="sxs-lookup"><span data-stu-id="b7a2c-171">Touchpad pressed</span></span> </td><td> <span data-ttu-id="b7a2c-172">Schaltfläche 16 \*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-172">Button 16\*</span></span> </td><td> <span data-ttu-id="b7a2c-173">Schaltfläche 17 \*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-173">Button 17\*</span></span> </td><td> <span data-ttu-id="b7a2c-174">touchpadpressed</span><span class="sxs-lookup"><span data-stu-id="b7a2c-174">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-175">6DOF-Zieh Punkt Pose oder Zeiger Pose</span><span class="sxs-lookup"><span data-stu-id="b7a2c-175">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="b7a2c-176"><i>Grip</i> Nur Ziehpunkt: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Inputtracking. getlocalposition</a></span><span class="sxs-lookup"><span data-stu-id="b7a2c-176"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="b7a2c-177"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Input Tracking. getlocalrotation</a></span><span class="sxs-lookup"><span data-stu-id="b7a2c-177"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="b7a2c-178">Pass <i>-</i> oder <i>Zeiger</i> als Argument: SourceState. sourcepose. trygetposition</span><span class="sxs-lookup"><span data-stu-id="b7a2c-178">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="b7a2c-179">SourceState. sourcepose. trygetrotation</span><span class="sxs-lookup"><span data-stu-id="b7a2c-179">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-180">Nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="b7a2c-180">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="b7a2c-181"><i>Die Positionsgenauigkeit und das Risiko von Quell Verlusten sind nur über die Mr-spezifische API verfügbar.</i> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-181"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="b7a2c-182"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">SourceState. sourcepose. positionaccuracy</a></span><span class="sxs-lookup"><span data-stu-id="b7a2c-182"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="b7a2c-183"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourcelossrisk</a></span><span class="sxs-lookup"><span data-stu-id="b7a2c-183"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="b7a2c-184">Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für openvr verwendet, aufgrund von Konflikten in den von Gamepads, oculus Touchscreen und openvr verwendeten Zuordnungen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-184">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

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


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="b7a2c-185">Ziehpunkt im Vergleich zu Zeige darstellen</span><span class="sxs-lookup"><span data-stu-id="b7a2c-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="b7a2c-186">Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren, wobei sich der Entwurf des Controllers in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung unterscheidet, die von den apps beim Rendern des Controllers verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="b7a2c-187">Um diese Controller besser darzustellen, gibt es zwei Arten von Posen, die Sie für jede Interaktions Quelle untersuchen können, die Ziehpunkt- **und die** **Zeiger** Darstellung.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="b7a2c-188">Sowohl die Ziehpunkt-als auch die zeigerpose-Koordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-188">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="b7a2c-189">Ziehpunkt darstellen</span><span class="sxs-lookup"><span data-stu-id="b7a2c-189">Grip pose</span></span>

<span data-ttu-id="b7a2c-190">Die Ziehpunkt- **Pose** stellt die Position der Palme einer Hand dar, die von einem hololens erkannt wird, oder die Palme, die einen Bewegungs Controller enthält.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-190">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="b7a2c-191">Bei immersiven Headsets eignet sich die Zieh Punkt Darstellung am besten zum Rendering **der Benutzer Hand** oder **eines Objekts, das in der Hand des Benutzers gehalten** wird, z. b. ein Schwert oder eine Waffe.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-191">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="b7a2c-192">Die Zieh Punkt Darstellung wird auch bei der Visualisierung eines Bewegungs Controllers verwendet, da das **renderbare Modell** , das von Windows für einen Motion-Controller bereitgestellt wird, die Zieh Punkt Darstellung als Ursprung und Mittelpunkt der Drehung verwendet.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-192">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="b7a2c-193">Die Ziehpunkt-Pose wird wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-193">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="b7a2c-194">Die Zieh **Punktposition**: der Palmen Schwerpunkt bei der natürlichen Aufbewahrung des Controllers, nach links oder rechts, um die Position im Ziehpunkt zu zentrieren.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-194">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="b7a2c-195">Auf dem Windows Mixed Reality Motion Controller richtet sich diese Position im Allgemeinen nach der Schaltfläche "verstehen".</span><span class="sxs-lookup"><span data-stu-id="b7a2c-195">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="b7a2c-196">Die **Rechte Achse** der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist das Strahl-Ray, das normal ist (vorwärts von links nach links, rückwärts von rechter Palme).</span><span class="sxs-lookup"><span data-stu-id="b7a2c-196">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="b7a2c-197">Die **Forward-Achse** der Ziehpunkt Ausrichtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das durch ihre nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-197">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="b7a2c-198">Die **aufwärts Achse** der Ziehpunkt Ausrichtung: die aufwärts Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-198">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="b7a2c-199">Sie können auf die Ziehpunkt-Pose über die Anbieter übergreifende Eingabe-API von Unity (XR) zugreifen *[. Inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Getlocalposition/Rotation*) oder über die Windows-spezifische API (*SourceState. sourcepose. trygetposition/Rotation*), die die Daten für den **Zieh Knoten** anfordert.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-199">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="b7a2c-200">Zeiger Pose</span><span class="sxs-lookup"><span data-stu-id="b7a2c-200">Pointer pose</span></span>

<span data-ttu-id="b7a2c-201">Die **Zeiger** Darstellung stellt die Spitze des Controllers dar, der vorwärts zeigt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-201">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="b7a2c-202">Die vom System bereitgestellte Zeiger Darstellung eignet sich am besten für raycast, wenn Sie **das Controller Modell selbst Rendern**.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-202">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="b7a2c-203">Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers (z. b. eine virtuelle Pistole) rendern, sollten Sie auf einen Strahl zeigen, der für dieses virtuelle Objekt am natürlichsten ist, z. b. ein Strahl, der entlang des fassers des App-defined Gun-Modells verläuft.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-203">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="b7a2c-204">Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das verweisen mit dem virtuellen Objekt für diejenigen, die Ihre APP verwenden, wahrscheinlich natürlicher.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-204">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="b7a2c-205">Derzeit ist die Zeiger Pose in Unity nur über die Windows Mr-spezifische API, *SourceState. sourcepose. trygetposition/Rotation* verfügbar, wobei *interaktionsourcenode. Pointer* als Argument übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-205">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="b7a2c-206">Controller nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="b7a2c-206">Controller tracking state</span></span>

<span data-ttu-id="b7a2c-207">Wie bei den Headsets ist für Windows Mixed Reality Motion Controller das Einrichten externer nach Verfolgungs Sensoren nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-207">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="b7a2c-208">Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-208">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="b7a2c-209">Wenn der Benutzer die Controller aus dem Feld des endfelds der Ansicht verschiebt, werden in den meisten Fällen die Controller Positionen von Windows weiter abgeleitet und der APP bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-209">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="b7a2c-210">Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-210">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="b7a2c-211">An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-211">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="b7a2c-212">Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können normal funktionieren, ohne dass der Benutzer das merkt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-212">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="b7a2c-213">Die beste Möglichkeit, dies zu erreichen, besteht darin, es selbst auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-213">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="b7a2c-214">Sehen Sie sich dieses Video mit Beispielen für den immersiven Inhalt an, der mit Motion-Controllern über verschiedene Überwachungs Zustände hinweg funktioniert:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-214">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="b7a2c-215">Grund für die explizite Nachverfolgung des Zustands</span><span class="sxs-lookup"><span data-stu-id="b7a2c-215">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="b7a2c-216">Apps, die Positionen basierend auf dem nach verfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und die Eigenschaften des Controller Zustands überprüfen, z. b. *sourcelossrisk* und *positionaccuracy*:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-216">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="b7a2c-217">Nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="b7a2c-217">Tracking state</span></span> </th><th> <span data-ttu-id="b7a2c-218">Sourcelossrisk</span><span class="sxs-lookup"><span data-stu-id="b7a2c-218">SourceLossRisk</span></span> </th><th> <span data-ttu-id="b7a2c-219">Positionsgenauigkeit</span><span class="sxs-lookup"><span data-stu-id="b7a2c-219">PositionAccuracy</span></span> </th><th> <span data-ttu-id="b7a2c-220">Trygetposition</span><span class="sxs-lookup"><span data-stu-id="b7a2c-220">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="b7a2c-221"><b>Hohe Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-221"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="b7a2c-222">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="b7a2c-222">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b7a2c-223">High</span><span class="sxs-lookup"><span data-stu-id="b7a2c-223">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b7a2c-224">true</span><span class="sxs-lookup"><span data-stu-id="b7a2c-224">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-225"><b>Hohe Genauigkeit (Risiko eines Verlusts)</b> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-225"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="b7a2c-226">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="b7a2c-226">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b7a2c-227">High</span><span class="sxs-lookup"><span data-stu-id="b7a2c-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b7a2c-228">true</span><span class="sxs-lookup"><span data-stu-id="b7a2c-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-229"><b>Ungefähre Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-229"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="b7a2c-230">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="b7a2c-230">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="b7a2c-231">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="b7a2c-231">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b7a2c-232">true</span><span class="sxs-lookup"><span data-stu-id="b7a2c-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b7a2c-233"><b>Keine Position</b> </span><span class="sxs-lookup"><span data-stu-id="b7a2c-233"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="b7a2c-234">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="b7a2c-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="b7a2c-235">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="b7a2c-235">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="b7a2c-236">false</span><span class="sxs-lookup"><span data-stu-id="b7a2c-236">false</span></span></td>
</tr>
</table>

<span data-ttu-id="b7a2c-237">Diese Motion Controller-Überwachungs Zustände werden wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-237">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="b7a2c-238">**Hohe Genauigkeit:** Während sich der Motion-Controller in der Ansicht des Dashboards befindet, stellt er im Allgemeinen hohe Genauigkeits Positionen auf der Grundlage der visuellen Nachverfolgung bereit.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-238">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="b7a2c-239">Beachten Sie, dass ein beweglicher Controller, der vorübergehend das Sichtfeld verlässt oder vorübergehend von den Headset-Sensoren (z. b. durch die andere Seite des Benutzers) verdeckt wird, weiterhin hohe Genauigkeit für kurze Zeit zurückgibt, basierend auf der trägheitverfolgung des Controllers.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-239">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="b7a2c-240">**Hohe Genauigkeit (Risiko des Verlusts):** Wenn der Benutzer den Bewegungs Controller über den Rand des Felds der Ansicht bewegt, kann das Headset die Position des Controllers in Kürze nicht visuell nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-240">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="b7a2c-241">Die APP weiß, wann der Controller diese FOV-Grenze erreicht hat, indem er den **sourcelossrisk** -REACH-1,0 sieht.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-241">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="b7a2c-242">An diesem Punkt kann die APP die Controller Gesten anhalten, die einen stabilen Stream von sehr hochwertigen Posen erfordern.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-242">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="b7a2c-243">**Ungefähre Genauigkeit:** Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-243">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="b7a2c-244">An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-244">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="b7a2c-245">Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können so normal agieren, dass Sie in der ungefähren Genauigkeit nicht bemerkt werden</span><span class="sxs-lookup"><span data-stu-id="b7a2c-245">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="b7a2c-246">Bei apps mit schwereren Eingabe Anforderungen ist es möglicherweise sinnvoll, diesen Löschvorgang von **hoher** Genauigkeit zur **ungefähren** Genauigkeit zu verstehen, indem die **positionaccuracy** -Eigenschaft überprüft wird, z. b. um dem Benutzer während dieses Zeitraums eine eher großzügigere Position in den offscreenzielen zu geben.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-246">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="b7a2c-247">**Keine Position:** Obwohl der Controller für einen längeren Zeitraum mit der ungefähren Genauigkeit arbeiten kann, weiß das System manchmal, dass auch eine vom Text gesperrte Position im Moment nicht aussagekräftig ist.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-247">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="b7a2c-248">Beispielsweise kann ein Controller, der gerade eingeschaltet war, nie visuell beobachtet werden, oder ein Benutzer kann einen Controller ablegen, der von einer anderen Person abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-248">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="b7a2c-249">Zu diesen Zeitpunkten stellt das System keine Position für die APP bereit, und *trygetposition* gibt false zurück.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-249">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="b7a2c-250">Allgemeine Unity-APIs (Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-250">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="b7a2c-251">**Namespace:** *unityengine*, *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-251">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b7a2c-252">**Typen**: *Input*, *XR. Inputtracking*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-252">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="b7a2c-253">Unity verwendet derzeit die allgemeinen *Input. getbutton/Input. getaxis-* APIs, um Eingaben für [das Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [das openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality, einschließlich der Hands-und Motion-Controller, verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-253">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="b7a2c-254">Wenn Ihre APP diese APIs für die Eingabe verwendet, kann Sie Bewegungs Controller über mehrere XR-sdche hinweg unterstützen, einschließlich Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-254">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="b7a2c-255">Der gedrückte Zustand einer logischen Schaltfläche wird erhalten.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-255">Getting a logical button's pressed state</span></span>

<span data-ttu-id="b7a2c-256">Wenn Sie die allgemeinen Unity-Eingabe-APIs verwenden möchten, beginnen Sie in der Regel mit dem Verknüpfen von Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), und binden Sie eine Schaltfläche oder eine Achsen-ID an jeden Namen</span><span class="sxs-lookup"><span data-stu-id="b7a2c-256">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="b7a2c-257">Anschließend können Sie Code schreiben, der auf den Namen der logischen Schaltfläche/Achse verweist.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-257">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="b7a2c-258">Um z. b. die triggerschaltfläche des linken Bewegungs Controllers der Aktion senden zuzuordnen, wechseln Sie zu **Edit > Project Settings > Input** in Unity, und erweitern Sie die Eigenschaften des Abschnitts übermitteln unter Achsen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-258">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="b7a2c-259">Ändern Sie die Schaltfläche **positiv** oder **alt positive Schaltfläche** , um die Schaltfläche "Taste **14**" wie folgt zu lesen:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-259">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="b7a2c-260">![InputManager von Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-260">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="b7a2c-261">*Unity-InputManager*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-261">*Unity InputManager*</span></span>

<span data-ttu-id="b7a2c-262">Das Skript kann dann mithilfe von " *Input. getbutton*" die Aktion "Senden" überprüfen:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-262">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="b7a2c-263">Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **size** -Eigenschaft unter **Achsen** ändern.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-263">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="b7a2c-264">Direktes drücken des gedrückten Zustands einer physischen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="b7a2c-264">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="b7a2c-265">Sie können mithilfe von *Input. GetKey* auch manuell über den voll qualifizierten Namen auf Schaltflächen zugreifen:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-265">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="b7a2c-266">Die Pose eines Hand-oder Bewegungs Controllers</span><span class="sxs-lookup"><span data-stu-id="b7a2c-266">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="b7a2c-267">Sie können auf die Position und Drehung des Controllers mithilfe von *XR zugreifen. Inputtracking*:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-267">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="b7a2c-268">Beachten Sie, dass dies die Zieh Punktposition des Controllers darstellt (in der der Benutzer den Controller hält). Dies ist nützlich, um ein Schwert oder eine Waffe in der Hand des Benutzers oder ein Modell des Controllers selbst zu rendern.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-268">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="b7a2c-269">Beachten Sie, dass die Beziehung zwischen diesem Ziehpunkt und der Zeiger Pose (bei der die Spitze des Controllers zeigt) sich zwischen Controllern unterscheiden kann.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-269">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="b7a2c-270">Zurzeit ist der Zugriff auf die Zeiger-Pose des Controllers nur über die in den folgenden Abschnitten beschriebene Mr-spezifische Eingabe-API möglich.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-270">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="b7a2c-271">Windows-spezifische APIs (XR. WSA. Der</span><span class="sxs-lookup"><span data-stu-id="b7a2c-271">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="b7a2c-272">, Wenn Ihr Projekt einen der XR-verwendet. WSA-APIs werden nach dem XR SDK in zukünftigen Unity-Releases eingestellt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-272">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="b7a2c-273">Für neue Projekte wird empfohlen, das XR SDK von Anfang an zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-273">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="b7a2c-274">Weitere Informationen zum [XR-Eingabe System und](https://docs.unity3d.com/Manual/xr_input.html)zu den APIs finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-274">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="b7a2c-275">**Namespace:** *unityengine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-275">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="b7a2c-276">**Typen**: *interaktionsmanager*, *interaktionsourcestate*, *interaktionsource*, *interaktionsourceproperties*, *interaktionsourcekind*, *interaktionsourcelokation*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-276">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="b7a2c-277">Um ausführlichere Informationen zu Windows Mixed Reality-Hand Eingaben (für hololens) und Bewegungs Controller zu erhalten, können Sie die Windows-spezifischen räumlichen Eingabe-APIs im Namespace *unityengine. XR. WSA. Input* verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-277">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="b7a2c-278">Auf diese Weise können Sie auf zusätzliche Informationen zugreifen, wie z. b. Die Positionsgenauigkeit oder die quellart, sodass Sie die Hände und Controller voneinander trennen können.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-278">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="b7a2c-279">Abrufen des Zustands von Händen und Bewegungs Controllern</span><span class="sxs-lookup"><span data-stu-id="b7a2c-279">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="b7a2c-280">Sie können den Status dieses Frames für jede Interaktions Quelle (Hand-oder Bewegungs Controller) mithilfe der *getcurrentreading* -Methode abrufen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-280">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="b7a2c-281">Jedes *interaktionsourcestate* , das Sie zurückerhalten, stellt eine Interaktions Quelle zum aktuellen Zeitpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-281">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="b7a2c-282">Das *interaktionsourcestate* macht Informationen wie z. b.:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-282">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="b7a2c-283">Welche [Arten von Druck](../../design/motion-controllers.md) vorgehungen werden auftreten (Select/Menu/grasp/Touchpad/Thumbstick)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-283">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="b7a2c-284">Andere Daten, die für Bewegungs Controller spezifisch sind, z. b. die XY-Koordinaten des Touchpads und/oder Finger Ansichts Status</span><span class="sxs-lookup"><span data-stu-id="b7a2c-284">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="b7a2c-285">Interaktionsourcekind, um zu wissen, ob es sich bei der Quelle um einen Hand-oder Bewegungs Controller handelt</span><span class="sxs-lookup"><span data-stu-id="b7a2c-285">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="b7a2c-286">Abrufen von vorwärts vorhergesagten Renderingvorgängen</span><span class="sxs-lookup"><span data-stu-id="b7a2c-286">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="b7a2c-287">Beim Abrufen von Interaktions Quelldaten von Hand und Controllern sind die von Ihnen abzurufenden Datenquellen für den Zeitpunkt, zu dem die Daten des Bilds den Augen des Benutzers erreichen, von vorne vorhergesagte Posen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-287">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="b7a2c-288">Diese vorwärts Gesagten Posen werden am besten zum **Rendern** des Controllers oder eines gehaltenen Objekts in jedem Frame verwendet.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-288">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="b7a2c-289">Wenn Sie ein bestimmtes Press-oder-Release mit dem Controller als Ziel verwenden, wird dies am genauesten sein, wenn Sie die nachstehend beschriebenen Vergangenheits Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-289">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="b7a2c-290">Sie können auch die vorwärts Gesagte Kopfzeile für diesen aktuellen Frame erhalten.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-290">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="b7a2c-291">Wie bei der Quell Darstellung ist dies für das **Rendern** eines Cursors nützlich, obwohl das Ziel einer bestimmten Presse oder Freigabe am genauesten ist, wenn Sie die unten beschriebenen Vergangenheits Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-291">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="b7a2c-292">Behandeln von Interaktions Quell Ereignissen</span><span class="sxs-lookup"><span data-stu-id="b7a2c-292">Handling interaction source events</span></span>

<span data-ttu-id="b7a2c-293">Um Eingabeereignisse zu behandeln, wie Sie mit Ihren exakten Vergangenheits Daten auftreten, können Sie Interaktions Quell Ereignisse behandeln, anstatt Sie abzufragen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-293">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="b7a2c-294">So behandeln Sie Interaktions Quell Ereignisse:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-294">To handle interaction source events:</span></span>
* <span data-ttu-id="b7a2c-295">Registrieren Sie sich für ein *interaktionmanager* -Eingabe Ereignis.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-295">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="b7a2c-296">Für jede Art von Interaktions Ereignis, für das Sie sich interessieren, müssen Sie es abonnieren.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-296">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="b7a2c-297">Behandeln Sie das-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-297">Handle the event.</span></span> <span data-ttu-id="b7a2c-298">Wenn Sie ein Interaktions Ereignis abonniert haben, erhalten Sie gegebenenfalls den Rückruf.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-298">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="b7a2c-299">Im Beispiel " *sourcepressed* " ist dies der Fall, nachdem die Quelle erkannt wurde und bevor Sie freigegeben oder verloren geht.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-299">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="b7a2c-300">Beenden der Behandlung eines Ereignisses</span><span class="sxs-lookup"><span data-stu-id="b7a2c-300">How to stop handling an event</span></span>

<span data-ttu-id="b7a2c-301">Sie müssen die Verarbeitung eines Ereignisses beenden, wenn Sie nicht mehr an dem Ereignis interessiert sind oder das Objekt zerstören, das das Ereignis abonniert hat.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-301">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="b7a2c-302">Wenn Sie die Verarbeitung des Ereignisses beenden möchten, kündigen Sie das Ereignis an.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-302">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="b7a2c-303">Liste der Interaktions Quell Ereignisse</span><span class="sxs-lookup"><span data-stu-id="b7a2c-303">List of interaction source events</span></span>

<span data-ttu-id="b7a2c-304">Die folgenden Interaktions Quell Ereignisse sind verfügbar:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-304">The available interaction source events are:</span></span>
* <span data-ttu-id="b7a2c-305">*Interaktionsourceerkannt* (Quelle wird aktiv)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-305">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="b7a2c-306">*Interaktionsourcelost* (wird inaktiv)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-306">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="b7a2c-307">*Interaktionsourcepressed* (tippen, drücken der Schaltfläche oder "auswählen")</span><span class="sxs-lookup"><span data-stu-id="b7a2c-307">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="b7a2c-308">*Interaktionsourcereleasing* (Ende einer Tap-Schaltfläche, oder Ende der "Select"-Taste)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-308">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="b7a2c-309">*Interaktionsourceupveraltet* (verschieben oder anderweitig ändern eines Zustands)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-309">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="b7a2c-310">Ereignisse für Vergangenheits Ziele, die mit einem Press oder Release am genauesten zu vergleichen sind</span><span class="sxs-lookup"><span data-stu-id="b7a2c-310">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="b7a2c-311">Die zuvor beschriebenen Abruf-APIs machen Ihre APP-vorhergesagte Posen aus.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-311">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="b7a2c-312">Obwohl die vorhergesagten Posen am besten zum Rendern des Controllers oder eines virtuellen Hand Held Objekts geeignet sind, sind zukünftige Posen nicht optimal für das Ziel, aus zwei Hauptgründen:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-312">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="b7a2c-313">Wenn der Benutzer eine Schaltfläche auf einem Controller drückt, kann es ungefähr 20 ms drahtlose Latenz über Bluetooth geben, bevor das System den Druck erhält.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-313">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="b7a2c-314">Wenn Sie dann eine vorwärts Gesagte Pose verwenden, gibt es eine weitere 10-20 MS der Forward-Vorhersage, auf die die Zeit angewendet wird, in der die Daten des aktuellen Frames die Augen des Benutzers erreichen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-314">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="b7a2c-315">Dies bedeutet, dass bei der Abfrage eine Quell Pose oder eine Kopfzeile angezeigt wird, die 30 bis 40 ms vorwärts ist, von wo aus die Kopfzeile des Benutzers und die Hände wieder zurück waren, als die Presse oder das Release aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-315">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="b7a2c-316">Bei der Eingabe von hololens-Hand Eingaben kommt es zu einer ähnlichen Verarbeitungs Verzögerung, um den Press zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-316">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="b7a2c-317">Um basierend auf der ursprünglichen Absicht des Benutzers für eine Hand oder einen Controller eine genaue Zielsetzung zu erreichen, sollten Sie die historische Quell Pose oder die Kopfzeile aus dem *interaktionsourcepressed* -oder *interaktionsourcereleasing* -Eingabe Ereignis verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-317">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="b7a2c-318">Sie können eine Presse oder eine Freigabe mit Verlaufs Daten des Benutzers oder des Controllers als Ziel haben:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-318">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="b7a2c-319">Die Kopfzeile zu dem Zeitpunkt, an dem eine Geste oder eine Controller Bewegung aufgetreten ist, die für die **Ziel** Bestimmung verwendet werden kann, um zu bestimmen, was der [Benutzer untersucht hat:](../../design/gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-319">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="b7a2c-320">Die Quell Pose zu dem Zeitpunkt, zu dem eine Bewegung des Bewegungs Controllers stattgefunden hat. diese kann verwendet werden, **um zu bestimmen** , auf welche Weise der Benutzer den Controller verwiesen hat.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-320">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="b7a2c-321">Dabei handelt es sich um den Zustand des Controllers, der den Druck erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-321">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="b7a2c-322">Wenn Sie den Controller selbst rendern, können Sie die Zeiger Darstellung anstelle der Ziehpunkt-Pose anfordern, um das Ziel-Ray von dem zu überprüfen, was der Benutzer für den natürlichen Tipp des gerenderten Controllers in Erwägung zieht:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-322">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="b7a2c-323">Beispiel für Ereignishandler</span><span class="sxs-lookup"><span data-stu-id="b7a2c-323">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="b7a2c-324">APIs für zusammengesetzte Gesten auf hoher Ebene (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-324">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="b7a2c-325">**Namespace:** *unityengine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-325">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="b7a2c-326">**Typen**: *GestureRecognizer*, *gesturesettings*, *interaktionsourcekind*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-326">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="b7a2c-327">Ihre APP kann auch zusammengesetzte Gesten auf höherer Ebene für räumliche Eingabe Quellen, Tap-, Halt-, Manipulations-und Navigations Gesten erkennen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-327">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="b7a2c-328">Mit dem GestureRecognizer können Sie diese zusammengesetzten Gesten sowohl in [Hand](../../design/gaze-and-commit.md#composite-gestures) -als auch in [Bewegungs Controllern](../../design/motion-controllers.md) erkennen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-328">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="b7a2c-329">Jedes Gesten Ereignis für den GestureRecognizer stellt sowohl sourcekind für die Eingabe als auch den Ziel-Head-Strahl zum Zeitpunkt des Ereignisses bereit.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-329">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="b7a2c-330">Einige Ereignisse bieten zusätzliche kontextspezifische Informationen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-330">Some events provide additional context specific information.</span></span>

<span data-ttu-id="b7a2c-331">Es sind nur wenige Schritte erforderlich, um Gesten mithilfe einer Gestenerkennung zu erfassen:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-331">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="b7a2c-332">Erstellen einer neuen Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="b7a2c-332">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="b7a2c-333">Legen Sie fest, welche Gesten überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-333">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="b7a2c-334">Ereignisse für diese Gesten abonnieren</span><span class="sxs-lookup"><span data-stu-id="b7a2c-334">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="b7a2c-335">Erfassungs Gesten starten</span><span class="sxs-lookup"><span data-stu-id="b7a2c-335">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="b7a2c-336">Erstellen einer neuen Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="b7a2c-336">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="b7a2c-337">Wenn Sie den *GestureRecognizer* verwenden möchten, müssen Sie einen *GestureRecognizer* erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-337">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="b7a2c-338">Legen Sie fest, welche Gesten überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-338">Specify which gestures to watch for</span></span>

<span data-ttu-id="b7a2c-339">Geben Sie an, welche Gesten Sie über "" mit "" auf "" festgelegt haben *()*:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-339">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="b7a2c-340">Ereignisse für diese Gesten abonnieren</span><span class="sxs-lookup"><span data-stu-id="b7a2c-340">Subscribe to events for those gestures</span></span>

<span data-ttu-id="b7a2c-341">Abonnieren Sie Ereignisse für die Gesten, an denen Sie interessiert sind.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-341">Subscribe to events for the gestures you are interested in.</span></span>

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
><span data-ttu-id="b7a2c-342">Navigations-und Manipulations Gesten schließen sich gegenseitig für eine Instanz eines *GestureRecognizer* aus.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-342">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="b7a2c-343">Erfassungs Gesten starten</span><span class="sxs-lookup"><span data-stu-id="b7a2c-343">Start capturing gestures</span></span>

<span data-ttu-id="b7a2c-344">Standardmäßig überwacht ein *GestureRecognizer* die Eingabe erst, wenn *startcapturinggesten ()* aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-344">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="b7a2c-345">Möglicherweise wird ein Gesten Ereignis generiert, nachdem *stopcapturinggesten ()* aufgerufen wurde, wenn Eingaben vor dem Frame durchgeführt wurden, in dem *stopcapturinggesten ()* verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-345">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="b7a2c-346">Der *GestureRecognizer* weiß, ob er während des vorherigen Frames ein-oder ausgeschaltet war, in dem die Geste tatsächlich aufgetreten ist, und daher ist es zuverlässig, die Gesten Überwachung auf der Grundlage der Anzeige Ziele dieses Frames zu starten und zu beenden.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-346">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="b7a2c-347">Erfassungs Gesten nicht mehr</span><span class="sxs-lookup"><span data-stu-id="b7a2c-347">Stop capturing gestures</span></span>

<span data-ttu-id="b7a2c-348">So verhindern Sie die Gestenerkennung:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-348">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="b7a2c-349">Entfernen einer Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="b7a2c-349">Removing a gesture recognizer</span></span>

<span data-ttu-id="b7a2c-350">Denken Sie daran, abonnierte Ereignisse abzubestellen, bevor Sie ein *GestureRecognizer* -Objekt zerstören.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-350">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="b7a2c-351">Rendern des Motion Controller-Modells in Unity</span><span class="sxs-lookup"><span data-stu-id="b7a2c-351">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="b7a2c-352">![Motion Controller-Modell und-teleportierung](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-352">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="b7a2c-353">*Motion Controller-Modell und-teleportierung*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-353">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="b7a2c-354">Zum Rendering von Bewegungs Controllern in Ihrer APP, die den physischen Controllern entsprechen, die die Benutzer als verschiedene Schaltflächen verwenden, die Sie verwenden, können Sie die **vorfab von "mutioncontroller** " im [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-354">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="b7a2c-355">Dieser Prefab lädt das korrekte gltf-Modell zur Laufzeit dynamisch aus dem installierten Motion Controller-Treiber des Systems.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-355">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="b7a2c-356">Es ist wichtig, dass diese Modelle dynamisch geladen werden, anstatt Sie manuell in den Editor zu importieren, damit Ihre APP physisch genaue 3D-Modelle für alle aktuellen und zukünftigen Controller anzeigt, die Ihre Benutzer möglicherweise haben.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-356">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="b7a2c-357">Befolgen Sie [die Anweisungen für die ersten](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) Schritte, um das Mixed Reality Toolkit herunterzuladen und es Ihrem Unity-Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-357">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="b7a2c-358">Wenn Sie Ihre Kamera durch das *mixedrealitycameraparent* -präfab im Rahmen der Schritte für die ersten Schritte ersetzt haben, können Sie es tun!</span><span class="sxs-lookup"><span data-stu-id="b7a2c-358">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="b7a2c-359">Dieses präfab umfasst das Rendern von Bewegungs Controllern.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-359">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="b7a2c-360">Andernfalls fügen Sie *Assets/holotoolkit/Input/Prefabs/mutioncontrollers. Prefab* aus dem Projektbereich in die Szene ein.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-360">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="b7a2c-361">Sie sollten diese Prefab als untergeordnetes Element eines beliebigen übergeordneten Objekts hinzufügen, das Sie verwenden, um die Kamera zu bewegen, wenn der Benutzer in der Szene Teleports verwendet, sodass die Controller mit dem Benutzer zusammenkommen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-361">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="b7a2c-362">Wenn Ihre APP keine teleportierung umfasst, fügen Sie einfach die vorfab im Stammverzeichnis Ihrer Szene hinzu.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-362">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="b7a2c-363">Auslösen von Objekten</span><span class="sxs-lookup"><span data-stu-id="b7a2c-363">Throwing objects</span></span>

<span data-ttu-id="b7a2c-364">Das Auslösen von Objekten in Virtual Reality ist ein schwierigeres Problem, das möglicherweise zuerst erscheint.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-364">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="b7a2c-365">Wie bei den meisten physisch basierenden Interaktionen verhält es sich beim Auslösen im Spiel auf unerwartete Weise, es ist sofort offensichtlich und unterbricht das eintauchen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-365">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="b7a2c-366">Wir haben einige Zeit damit verbracht, ein physisch korrektes auslösverhalten darzustellen, und haben einige Richtlinien, die über Updates auf unserer Plattform aktiviert wurden, für Sie freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-366">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="b7a2c-367">Ein Beispiel für die Implementierung von "throw" finden Sie [hier](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="b7a2c-367">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="b7a2c-368">Dieses Beispiel befolgt diese vier Richtlinien:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-368">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="b7a2c-369">**Verwenden Sie die *Geschwindigkeit* des Controllers anstelle der Position**.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-369">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="b7a2c-370">Im November-Update für Windows haben wir eine Änderung des Verhaltens eingeführt, wenn der [ungefähre Status der Positionsüberwachung ("ungefähre"](../../design/motion-controllers.md#controller-tracking-state)) ist.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-370">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="b7a2c-371">In diesem Zustand werden Velocity-Informationen über den Controller weiterhin angezeigt, solange wir glauben, dass es sich um eine hohe Genauigkeit handelt, die häufig länger ist als die Position mit hoher Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-371">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="b7a2c-372">**Integrieren Sie die *Winkelgeschwindigkeit* des Controllers**.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-372">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="b7a2c-373">Diese Logik ist in der- `throwing.cs` Datei in der `GetThrownObjectVelAngVel` statischen-Methode innerhalb des oben verknüpften Pakets enthalten:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-373">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="b7a2c-374">Wenn die Angular-Geschwindigkeit beibehalten wird, muss das ausgelöste Objekt dieselbe Angular-Geschwindigkeit wie in der Zeit der throw-Ausnahme beibehalten: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="b7a2c-374">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="b7a2c-375">Da sich der Mittelpunkt der Masse des ausgelösten Objekts wahrscheinlich nicht am Ursprung der Ziehpunkt-Pose befindet, weist er wahrscheinlich eine andere Geschwindigkeit auf als der Controller im Verweis auf den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-375">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="b7a2c-376">Der Teil der auf diese Weise beigetragenen Geschwindigkeit des Objekts ist die sofortige tangential Geschwindigkeit des Mittelpunkts der Masse des ausgelösten Objekts um den Controller Ursprung.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-376">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="b7a2c-377">Diese tangential-Geschwindigkeit ist das Kreuz Produkt der Angular-Geschwindigkeit des Controllers mit dem Vektor, der den Abstand zwischen dem Controller Ursprung und dem Mittelpunkt der Masse des ausgelösten Objekts darstellt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-377">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="b7a2c-378">Die Gesamtgeschwindigkeit des ausgelösten Objekts entspricht daher der Summe der Geschwindigkeit des Controllers und der tangential Geschwindigkeit: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="b7a2c-378">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="b7a2c-379">Achten **Sie genau auf die *Zeit* , zu der wir die Geschwindigkeit anwenden**.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-379">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="b7a2c-380">Wenn eine Schaltfläche gedrückt wird, kann es bis zu 20 ms dauern, bis das Ereignis durch Bluetooth bis zum Betriebssystem hochskalieren kann.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-380">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="b7a2c-381">Dies bedeutet Folgendes: Wenn Sie eine Änderung des Controller Zustands von "gedrückt" in "nicht gedrückt" oder umgekehrt abrufen, werden die Informationen, die Sie mit dem Controller erhalten, tatsächlich vor dieser Zustandsänderung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-381">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="b7a2c-382">Außerdem wird die von unserer Abruf-API dargestellte Controller Darstellung vorhergesagt, um eine wahrscheinliche Darstellung zum Zeitpunkt der Anzeige des Frames widerzuspiegeln, der in der Zukunft mehr als 20 ms betragen kann.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-382">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="b7a2c-383">Dies eignet sich gut für das *Rendern* von gehaltenen Objekten, stellt jedoch unser Zeitproblem für das *Ziel des Objekts* dar</span><span class="sxs-lookup"><span data-stu-id="b7a2c-383">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="b7a2c-384">Wenn beim November-Update ein Unity-Ereignis wie *interaktionsourcepressed* oder *interaktionsourcereleasing* gesendet wird, enthält der Zustand die Vergangenheits Daten von hinten, wenn die Schaltfläche tatsächlich gedrückt oder freigegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-384">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="b7a2c-385">Um das präzisere Controller Rendering und die Zielplattform für das Ausführen von Triggeroptionen zu erhalten, müssen Sie nach Bedarf Abruf-und Ereignis Ereignisse ordnungsgemäß verwenden:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-385">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="b7a2c-386">Für den Controller, der die einzelnen Frames **rendert** , sollte Ihre APP das *gameobject* des Controllers an der vorwärts Gesagten Controller Darstellung für die Photon-Zeit des aktuellen Frames positionieren.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-386">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="b7a2c-387">Sie erhalten diese Daten von Unity-Abruf-APIs wie *[XR. Inputtracking. getlocalposition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oder *[XR. WSA. Input. interaktionmanager. getcurrentreading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-387">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="b7a2c-388">Für den Controller, der auf eine Presse oder ein Release **abzielt** , sollte Ihre APP auf der Grundlage der Verlaufs Controller-Pose für das Press-oder releaseereignis auf der Grundlage der Verlaufs Controller-</span><span class="sxs-lookup"><span data-stu-id="b7a2c-388">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="b7a2c-389">Sie erhalten diese Daten aus den Unity-Ereignis-APIs, wie z. b. *[interaktionmanager. interaktionsourcepressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-389">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="b7a2c-390">**Verwenden Sie die** Ziehpunkt-Pose.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-390">**Use the grip pose**.</span></span> <span data-ttu-id="b7a2c-391">Winkelgeschwindigkeit und-Geschwindigkeit werden relativ zur Zieh Punkt Pose, nicht zum Darstellen von Zeigern, angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-391">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="b7a2c-392">Das auslösen wird mit zukünftigen Windows-Updates weiter verbessern, und Sie können davon ausgehen, dass Sie hier weitere Informationen finden.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-392">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="b7a2c-393">Gesten-und Bewegungs Controller in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="b7a2c-393">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="b7a2c-394">Sie können über den Eingabe-Manager auf Gesten-und Bewegungs Controller zugreifen.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-394">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="b7a2c-395">Geste in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="b7a2c-395">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="b7a2c-396">Motion Controller in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="b7a2c-396">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="b7a2c-397">Immer am Ball mit Tutorials</span><span class="sxs-lookup"><span data-stu-id="b7a2c-397">Follow along with tutorials</span></span>

<span data-ttu-id="b7a2c-398">Schritt-für-Schritt-Tutorials mit ausführlicheren Anpassungs Beispielen sind in der Mixed Reality Academy verfügbar:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-398">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="b7a2c-399">MR-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="b7a2c-399">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="b7a2c-400">MR-Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="b7a2c-400">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="b7a2c-401">[![Mr-Eingabe 213-Motion Controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="b7a2c-401">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="b7a2c-402">*Mr-Eingabe 213-Motion Controller*</span><span class="sxs-lookup"><span data-stu-id="b7a2c-402">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b7a2c-403">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="b7a2c-403">Next Development Checkpoint</span></span>

<span data-ttu-id="b7a2c-404">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-404">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="b7a2c-405">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-405">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7a2c-406">Hand- und Eye-Tracking</span><span class="sxs-lookup"><span data-stu-id="b7a2c-406">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="b7a2c-407">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="b7a2c-407">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7a2c-408">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="b7a2c-408">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="b7a2c-409">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="b7a2c-409">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7a2c-410">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b7a2c-410">See also</span></span>

* [<span data-ttu-id="b7a2c-411">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="b7a2c-411">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="b7a2c-412">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="b7a2c-412">Motion controllers</span></span>](../../design/motion-controllers.md)
