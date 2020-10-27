---
title: Gesten und Motion-Controller in Unity
description: Erfahren Sie, wie Sie mithilfe von Handgesten und Bewegungs Controllern Maßnahmen für Ihren Blick in Unity durchführen können.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Gesten, Bewegungs Controller, Unity, Blick, Eingabe
ms.openlocfilehash: 6b132e56e5d60e59fda53b95328580ed861ce75c
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638557"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="341d3-104">Gesten und Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="341d3-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="341d3-105">Es gibt zwei wichtige Möglichkeiten, um Ihre [Blicke in Unity](gaze-in-unity.md), [Handgesten](../../design/gaze-and-commit.md#composite-gestures) und [Bewegungs Controllern](../../design/motion-controllers.md) in hololens und immersiven HMD zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="341d3-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="341d3-106">Sie greifen über dieselben APIs in Unity auf die Daten für beide Quellen räumlicher Eingaben zu.</span><span class="sxs-lookup"><span data-stu-id="341d3-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="341d3-107">Unity bietet zwei Hauptmethoden für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality, die gängigen *Input. getbutton/Input. getaxis-* APIs, die über mehrere Unity-XR-sdker hinweg verwendet werden können, sowie eine *interaktionmanager/GestureRecognizer-* API speziell für Windows Mixed Reality, das den vollständigen Satz räumlicher Eingabedaten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="341d3-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="341d3-108">Unity-Schaltfläche/Achsen Zuordnung (Tabelle)</span><span class="sxs-lookup"><span data-stu-id="341d3-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="341d3-109">Die Schaltflächen-und Achsen-IDs in der folgenden Tabelle werden im Unity-Eingabe-Manager für Windows Mixed Reality Motion Controller über die *Eingabe. getbutton/getaxis* -APIs unterstützt, während die Spalte "Windows Mr-spezifisch" auf Eigenschaften verweist, die aus dem *interaktionsourcestate* -Typ verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="341d3-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="341d3-110">Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="341d3-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="341d3-111">Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality entsprechen im Allgemeinen den Oculus-Schaltflächen-/Achsen-IDs</span><span class="sxs-lookup"><span data-stu-id="341d3-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="341d3-112">Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality unterscheiden sich auf zwei Arten von den Zuordnungen von openvr:</span><span class="sxs-lookup"><span data-stu-id="341d3-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="341d3-113">Die Zuordnung verwendet Touchpad-IDs, die sich vom Finger Stick unterscheiden, um Controller mit beiden Fingerabdrücken und Touchpads zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="341d3-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="341d3-114">Durch die Zuordnung wird vermieden, dass die Schaltflächen-IDs A und X für die Menü Schaltflächen überladen werden, damit Sie für physische abxy-Schaltflächen verfügbar</span><span class="sxs-lookup"><span data-stu-id="341d3-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="341d3-115">Eingabe</span><span class="sxs-lookup"><span data-stu-id="341d3-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="341d3-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a></span><span class="sxs-lookup"><span data-stu-id="341d3-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="341d3-117">(Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="341d3-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="341d3-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows-spezifische Eingabe-API</a></span><span class="sxs-lookup"><span data-stu-id="341d3-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="341d3-119">XR. WSA. Der</span><span class="sxs-lookup"><span data-stu-id="341d3-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="341d3-120">Links</span><span class="sxs-lookup"><span data-stu-id="341d3-120">Left hand</span></span> </th><th> <span data-ttu-id="341d3-121">Rechte Seite</span><span class="sxs-lookup"><span data-stu-id="341d3-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="341d3-122">Select-Taste gedrückt</span><span class="sxs-lookup"><span data-stu-id="341d3-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="341d3-123">Achse 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="341d3-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="341d3-124">Achse 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="341d3-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="341d3-125">selectpressed</span><span class="sxs-lookup"><span data-stu-id="341d3-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-126">Auswählen des analogen Auslöse Werts</span><span class="sxs-lookup"><span data-stu-id="341d3-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="341d3-127">Achse 9</span><span class="sxs-lookup"><span data-stu-id="341d3-127">Axis 9</span></span> </td><td> <span data-ttu-id="341d3-128">Achse 10</span><span class="sxs-lookup"><span data-stu-id="341d3-128">Axis 10</span></span> </td><td> <span data-ttu-id="341d3-129">selectpressedamount</span><span class="sxs-lookup"><span data-stu-id="341d3-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-130">Select-Taste teilweise gedrückt</span><span class="sxs-lookup"><span data-stu-id="341d3-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="341d3-131">Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="341d3-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="341d3-132">Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="341d3-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="341d3-133">selectpressedamount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="341d3-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-134">Menü Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="341d3-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="341d3-135">Schaltfläche 6 \*</span><span class="sxs-lookup"><span data-stu-id="341d3-135">Button 6\*</span></span> </td><td> <span data-ttu-id="341d3-136">Schaltfläche 7 \*</span><span class="sxs-lookup"><span data-stu-id="341d3-136">Button 7\*</span></span> </td><td> <span data-ttu-id="341d3-137">menupressed</span><span class="sxs-lookup"><span data-stu-id="341d3-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-138">Zieh Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="341d3-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="341d3-139">Achse 11 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="341d3-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="341d3-140">Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="341d3-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="341d3-141">Achse 12 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="341d3-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="341d3-142">Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="341d3-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="341d3-143">Schna</span><span class="sxs-lookup"><span data-stu-id="341d3-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-144">Thumbstick X <i>(Links:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="341d3-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="341d3-145">Achse 1</span><span class="sxs-lookup"><span data-stu-id="341d3-145">Axis 1</span></span> </td><td> <span data-ttu-id="341d3-146">Achse 4</span><span class="sxs-lookup"><span data-stu-id="341d3-146">Axis 4</span></span> </td><td> <span data-ttu-id="341d3-147">thumbstickposition. x</span><span class="sxs-lookup"><span data-stu-id="341d3-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-148">Thumbstick Y <i>(oben:-1,0, unten: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="341d3-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="341d3-149">Achse 2</span><span class="sxs-lookup"><span data-stu-id="341d3-149">Axis 2</span></span> </td><td> <span data-ttu-id="341d3-150">Achse 5</span><span class="sxs-lookup"><span data-stu-id="341d3-150">Axis 5</span></span> </td><td> <span data-ttu-id="341d3-151">thumbstickposition. y</span><span class="sxs-lookup"><span data-stu-id="341d3-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-152">Thumbstick gedrückt</span><span class="sxs-lookup"><span data-stu-id="341d3-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="341d3-153">Schaltfläche 8</span><span class="sxs-lookup"><span data-stu-id="341d3-153">Button 8</span></span> </td><td> <span data-ttu-id="341d3-154">Schaltfläche 9</span><span class="sxs-lookup"><span data-stu-id="341d3-154">Button 9</span></span> </td><td> <span data-ttu-id="341d3-155">thumbstickpressed</span><span class="sxs-lookup"><span data-stu-id="341d3-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-156">Touchpad X <i>(Links:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="341d3-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="341d3-157">Achse 17 \*</span><span class="sxs-lookup"><span data-stu-id="341d3-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="341d3-158">Achse 19 \*</span><span class="sxs-lookup"><span data-stu-id="341d3-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="341d3-159">touchpadposition. x</span><span class="sxs-lookup"><span data-stu-id="341d3-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-160">Touchpad Y <i>(oben:-1,0, unten: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="341d3-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="341d3-161">Achse 18 \*</span><span class="sxs-lookup"><span data-stu-id="341d3-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="341d3-162">Achse 20 \*</span><span class="sxs-lookup"><span data-stu-id="341d3-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="341d3-163">touchpadposition. y</span><span class="sxs-lookup"><span data-stu-id="341d3-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-164">Touchpad berührt</span><span class="sxs-lookup"><span data-stu-id="341d3-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="341d3-165">Schaltfläche 18 \*</span><span class="sxs-lookup"><span data-stu-id="341d3-165">Button 18\*</span></span> </td><td> <span data-ttu-id="341d3-166">Schaltfläche 19 \*</span><span class="sxs-lookup"><span data-stu-id="341d3-166">Button 19\*</span></span> </td><td> <span data-ttu-id="341d3-167">touchpadtouched</span><span class="sxs-lookup"><span data-stu-id="341d3-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-168">Touchpad gedrückt</span><span class="sxs-lookup"><span data-stu-id="341d3-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="341d3-169">Schaltfläche 16 \*</span><span class="sxs-lookup"><span data-stu-id="341d3-169">Button 16\*</span></span> </td><td> <span data-ttu-id="341d3-170">Schaltfläche 17 \*</span><span class="sxs-lookup"><span data-stu-id="341d3-170">Button 17\*</span></span> </td><td> <span data-ttu-id="341d3-171">touchpadpressed</span><span class="sxs-lookup"><span data-stu-id="341d3-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-172">6DOF-Zieh Punkt Pose oder Zeiger Pose</span><span class="sxs-lookup"><span data-stu-id="341d3-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="341d3-173"><i>Grip</i> Nur Ziehpunkt: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Inputtracking. getlocalposition</a></span><span class="sxs-lookup"><span data-stu-id="341d3-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="341d3-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Input Tracking. getlocalrotation</a></span><span class="sxs-lookup"><span data-stu-id="341d3-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="341d3-175">Pass <i>-</i> oder <i>Zeiger</i> als Argument: SourceState. sourcepose. trygetposition</span><span class="sxs-lookup"><span data-stu-id="341d3-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="341d3-176">SourceState. sourcepose. trygetrotation</span><span class="sxs-lookup"><span data-stu-id="341d3-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="341d3-177">Nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="341d3-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="341d3-178"><i>Die Positionsgenauigkeit und das Risiko von Quell Verlusten sind nur über die Mr-spezifische API verfügbar.</i> </span><span class="sxs-lookup"><span data-stu-id="341d3-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="341d3-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">SourceState. sourcepose. positionaccuracy</a></span><span class="sxs-lookup"><span data-stu-id="341d3-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="341d3-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourcelossrisk</a></span><span class="sxs-lookup"><span data-stu-id="341d3-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="341d3-181">Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für openvr verwendet, aufgrund von Konflikten in den von Gamepads, oculus Touchscreen und openvr verwendeten Zuordnungen.</span><span class="sxs-lookup"><span data-stu-id="341d3-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

### <a name="using-hp-reverb-g2-controllers"></a><span data-ttu-id="341d3-182">Verwenden von HP Reverb G2-Controllern</span><span class="sxs-lookup"><span data-stu-id="341d3-182">Using HP Reverb G2 controllers</span></span>

<span data-ttu-id="341d3-183">Wenn Sie die HP-Reverb-G2-Controller verwenden, finden Sie in der Tabelle unten die Schaltflächen-und Achsen-IDs.</span><span class="sxs-lookup"><span data-stu-id="341d3-183">If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="341d3-184"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Eingabe</span><span class="sxs-lookup"><span data-stu-id="341d3-184"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input</span></span> </th><span data-ttu-id="341d3-185"><th colspan="2">Allgemeine Unity-APIs</span><span class="sxs-lookup"><span data-stu-id="341d3-185"><th colspan="2">Common Unity APIs</span></span></a><br /><span data-ttu-id="341d3-186">(Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="341d3-186">(Input.GetButton/GetAxis)</span></span> </th><span data-ttu-id="341d3-187"><th rowspan="2">HP Reverb G2-Eingabe-API</span><span class="sxs-lookup"><span data-stu-id="341d3-187"><th rowspan="2">HP Reverb G2 Input API</span></span></a></th>
</tr><tr>
<th> <span data-ttu-id="341d3-188">Links</span><span class="sxs-lookup"><span data-stu-id="341d3-188">Left hand</span></span> </th><th> <span data-ttu-id="341d3-189">Rechte Seite</span><span class="sxs-lookup"><span data-stu-id="341d3-189">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="341d3-190">Primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="341d3-190">Primary2DAxis</span></span> </td><td> <span data-ttu-id="341d3-191">Achse 1 (X)/Achse 2 (Y)</span><span class="sxs-lookup"><span data-stu-id="341d3-191">Axis 1 (X) / Axis 2 (Y)</span></span> </td><td> <span data-ttu-id="341d3-192">Achse 4 (X)/Achse 5 (Y)</span><span class="sxs-lookup"><span data-stu-id="341d3-192">Axis 4 (X) / Axis 5(Y)</span></span> </td><td> <span data-ttu-id="341d3-193">Ministick</span><span class="sxs-lookup"><span data-stu-id="341d3-193">Thumbstick</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-194">Ausgerufene Taste</span><span class="sxs-lookup"><span data-stu-id="341d3-194">Trigger pressed</span></span> </td><td> <span data-ttu-id="341d3-195">Achse 9</span><span class="sxs-lookup"><span data-stu-id="341d3-195">Axis 9</span></span> </td><td> <span data-ttu-id="341d3-196">Achse 10</span><span class="sxs-lookup"><span data-stu-id="341d3-196">Axis 10</span></span> </td><td> <span data-ttu-id="341d3-197">Index-Auslösung</span><span class="sxs-lookup"><span data-stu-id="341d3-197">Index trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-198">Hand</span><span class="sxs-lookup"><span data-stu-id="341d3-198">Grip</span></span> </td><td> <span data-ttu-id="341d3-199">Achse 11d</span><span class="sxs-lookup"><span data-stu-id="341d3-199">Axis 11d</span></span> </td><td> <span data-ttu-id="341d3-200">Achse 12</span><span class="sxs-lookup"><span data-stu-id="341d3-200">Axis 12</span></span> </td><td> <span data-ttu-id="341d3-201">Ziehpunkt-auslöst</span><span class="sxs-lookup"><span data-stu-id="341d3-201">Grip trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-202">Primarybutton gedrückt</span><span class="sxs-lookup"><span data-stu-id="341d3-202">PrimaryButton pressed</span></span> </td><td> <span data-ttu-id="341d3-203">Schaltfläche 2</span><span class="sxs-lookup"><span data-stu-id="341d3-203">Button 2</span></span> </td><td> <span data-ttu-id="341d3-204">Schaltfläche 0</span><span class="sxs-lookup"><span data-stu-id="341d3-204">Button 0</span></span> </td><td> <span data-ttu-id="341d3-205">Menü Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="341d3-205">Menu button pressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-206">Secondarybutton gedrückt</span><span class="sxs-lookup"><span data-stu-id="341d3-206">SecondaryButton pressed</span></span> </td><td> <span data-ttu-id="341d3-207">Schaltfläche 3</span><span class="sxs-lookup"><span data-stu-id="341d3-207">Button 3</span></span> </td><td> <span data-ttu-id="341d3-208">Schaltfläche 1</span><span class="sxs-lookup"><span data-stu-id="341d3-208">Button 1</span></span> </td><td> <span data-ttu-id="341d3-209">Schaltfläche "A/X"</span><span class="sxs-lookup"><span data-stu-id="341d3-209">A/X button</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-210">Gripbutton</span><span class="sxs-lookup"><span data-stu-id="341d3-210">GripButton</span></span> </td><td> <span data-ttu-id="341d3-211">Schaltfläche 4</span><span class="sxs-lookup"><span data-stu-id="341d3-211">Button 4</span></span> </td><td> <span data-ttu-id="341d3-212">Schaltfläche 5</span><span class="sxs-lookup"><span data-stu-id="341d3-212">Button 5</span></span> </td><td> <span data-ttu-id="341d3-213">Ziehpunkt-auslöst</span><span class="sxs-lookup"><span data-stu-id="341d3-213">Grip trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-214">Triggerbutton</span><span class="sxs-lookup"><span data-stu-id="341d3-214">TriggerButton</span></span> </td><td> <span data-ttu-id="341d3-215">Schaltfläche 14</span><span class="sxs-lookup"><span data-stu-id="341d3-215">Button 14</span></span> </td><td> <span data-ttu-id="341d3-216">Schaltfläche 15</span><span class="sxs-lookup"><span data-stu-id="341d3-216">Button 15</span></span> </td><td> <span data-ttu-id="341d3-217">Index-Auslösung</span><span class="sxs-lookup"><span data-stu-id="341d3-217">Index trigger</span></span></td>
</tr><tr>
</tr>
</table>


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="341d3-218">Ziehpunkt im Vergleich zu Zeige darstellen</span><span class="sxs-lookup"><span data-stu-id="341d3-218">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="341d3-219">Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren, wobei sich der Entwurf des Controllers in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung unterscheidet, die von den apps beim Rendern des Controllers verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="341d3-219">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="341d3-220">Um diese Controller besser darzustellen, gibt es zwei Arten von Posen, die Sie für jede Interaktions Quelle untersuchen können, die Ziehpunkt- **und die** **Zeiger** Darstellung.</span><span class="sxs-lookup"><span data-stu-id="341d3-220">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose** .</span></span> <span data-ttu-id="341d3-221">Sowohl die Ziehpunkt-als auch die zeigerpose-Koordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="341d3-221">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="341d3-222">Ziehpunkt darstellen</span><span class="sxs-lookup"><span data-stu-id="341d3-222">Grip pose</span></span>

<span data-ttu-id="341d3-223">Die Ziehpunkt- **Pose** stellt die Position der Palme einer Hand dar, die von einem hololens erkannt wird, oder die Palme, die einen Bewegungs Controller enthält.</span><span class="sxs-lookup"><span data-stu-id="341d3-223">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="341d3-224">Bei immersiven Headsets eignet sich die Zieh Punkt Darstellung am besten zum Rendering **der Benutzer Hand** oder **eines Objekts, das in der Hand des Benutzers gehalten** wird, z. b. ein Schwert oder eine Waffe.</span><span class="sxs-lookup"><span data-stu-id="341d3-224">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand** , such as a sword or gun.</span></span> <span data-ttu-id="341d3-225">Die Zieh Punkt Darstellung wird auch bei der Visualisierung eines Bewegungs Controllers verwendet, da das **renderbare Modell** , das von Windows für einen Motion-Controller bereitgestellt wird, die Zieh Punkt Darstellung als Ursprung und Mittelpunkt der Drehung verwendet.</span><span class="sxs-lookup"><span data-stu-id="341d3-225">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="341d3-226">Die Ziehpunkt-Pose wird wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="341d3-226">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="341d3-227">Die Zieh **Punktposition** : der Palmen Schwerpunkt bei der natürlichen Aufbewahrung des Controllers, nach links oder rechts, um die Position im Ziehpunkt zu zentrieren.</span><span class="sxs-lookup"><span data-stu-id="341d3-227">The **grip position** : The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="341d3-228">Auf dem Windows Mixed Reality Motion Controller richtet sich diese Position im Allgemeinen nach der Schaltfläche "verstehen".</span><span class="sxs-lookup"><span data-stu-id="341d3-228">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="341d3-229">Die **Rechte Achse** der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist das Strahl-Ray, das normal ist (vorwärts von links nach links, rückwärts von rechter Palme).</span><span class="sxs-lookup"><span data-stu-id="341d3-229">The **grip orientation's Right axis** : When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="341d3-230">Die **Forward-Achse** der Ziehpunkt Ausrichtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das durch ihre nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.</span><span class="sxs-lookup"><span data-stu-id="341d3-230">The **grip orientation's Forward axis** : When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="341d3-231">Die **aufwärts Achse** der Ziehpunkt Ausrichtung: die aufwärts Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.</span><span class="sxs-lookup"><span data-stu-id="341d3-231">The **grip orientation's Up axis** : The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="341d3-232">Sie können auf die Ziehpunkt-Pose über die Anbieter übergreifende Eingabe-API von Unity (XR) zugreifen *[. Inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Getlocalposition/Rotation* ) oder über die Windows-spezifische API ( *SourceState. sourcepose. trygetposition/Rotation* ), die die Daten für den **Zieh Knoten** anfordert.</span><span class="sxs-lookup"><span data-stu-id="341d3-232">You can access the grip pose through either Unity's cross-vendor input API ( *[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation* ) or through the Windows MR-specific API ( *sourceState.sourcePose.TryGetPosition/Rotation* , requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="341d3-233">Zeiger Pose</span><span class="sxs-lookup"><span data-stu-id="341d3-233">Pointer pose</span></span>

<span data-ttu-id="341d3-234">Die **Zeiger** Darstellung stellt die Spitze des Controllers dar, der vorwärts zeigt.</span><span class="sxs-lookup"><span data-stu-id="341d3-234">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="341d3-235">Die vom System bereitgestellte Zeiger Darstellung eignet sich am besten für raycast, wenn Sie **das Controller Modell selbst Rendern** .</span><span class="sxs-lookup"><span data-stu-id="341d3-235">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself** .</span></span> <span data-ttu-id="341d3-236">Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers (z. b. eine virtuelle Pistole) rendern, sollten Sie auf einen Strahl zeigen, der für dieses virtuelle Objekt am natürlichsten ist, z. b. ein Strahl, der entlang des fassers des App-defined Gun-Modells verläuft.</span><span class="sxs-lookup"><span data-stu-id="341d3-236">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="341d3-237">Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das verweisen mit dem virtuellen Objekt für diejenigen, die Ihre APP verwenden, wahrscheinlich natürlicher.</span><span class="sxs-lookup"><span data-stu-id="341d3-237">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="341d3-238">Derzeit ist die Zeiger Pose in Unity nur über die Windows Mr-spezifische API, *SourceState. sourcepose. trygetposition/Rotation* verfügbar, wobei *interaktionsourcenode. Pointer* als Argument übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="341d3-238">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation* , passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="341d3-239">Controller nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="341d3-239">Controller tracking state</span></span>

<span data-ttu-id="341d3-240">Wie bei den Headsets ist für Windows Mixed Reality Motion Controller das Einrichten externer nach Verfolgungs Sensoren nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="341d3-240">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="341d3-241">Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="341d3-241">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="341d3-242">Wenn der Benutzer die Controller aus dem Feld des endfelds der Ansicht verschiebt, werden in den meisten Fällen die Controller Positionen von Windows weiter abgeleitet und der APP bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="341d3-242">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="341d3-243">Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.</span><span class="sxs-lookup"><span data-stu-id="341d3-243">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="341d3-244">An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="341d3-244">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="341d3-245">Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können normal funktionieren, ohne dass der Benutzer das merkt.</span><span class="sxs-lookup"><span data-stu-id="341d3-245">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="341d3-246">Die beste Möglichkeit, dies zu erreichen, besteht darin, es selbst auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="341d3-246">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="341d3-247">Sehen Sie sich dieses Video mit Beispielen für den immersiven Inhalt an, der mit Motion-Controllern über verschiedene Überwachungs Zustände hinweg funktioniert:</span><span class="sxs-lookup"><span data-stu-id="341d3-247">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="341d3-248">Grund für die explizite Nachverfolgung des Zustands</span><span class="sxs-lookup"><span data-stu-id="341d3-248">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="341d3-249">Apps, die Positionen basierend auf dem nach verfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und die Eigenschaften des Controller Zustands überprüfen, z. b. *sourcelossrisk* und *positionaccuracy* :</span><span class="sxs-lookup"><span data-stu-id="341d3-249">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy* :</span></span>

<table>
<tr>
<th> <span data-ttu-id="341d3-250">Nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="341d3-250">Tracking state</span></span> </th><th> <span data-ttu-id="341d3-251">Sourcelossrisk</span><span class="sxs-lookup"><span data-stu-id="341d3-251">SourceLossRisk</span></span> </th><th> <span data-ttu-id="341d3-252">Positionsgenauigkeit</span><span class="sxs-lookup"><span data-stu-id="341d3-252">PositionAccuracy</span></span> </th><th> <span data-ttu-id="341d3-253">Trygetposition</span><span class="sxs-lookup"><span data-stu-id="341d3-253">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="341d3-254"><b>Hohe Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="341d3-254"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="341d3-255">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="341d3-255">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="341d3-256">High</span><span class="sxs-lookup"><span data-stu-id="341d3-256">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="341d3-257">true</span><span class="sxs-lookup"><span data-stu-id="341d3-257">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-258"><b>Hohe Genauigkeit (Risiko eines Verlusts)</b> </span><span class="sxs-lookup"><span data-stu-id="341d3-258"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="341d3-259">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="341d3-259">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="341d3-260">High</span><span class="sxs-lookup"><span data-stu-id="341d3-260">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="341d3-261">true</span><span class="sxs-lookup"><span data-stu-id="341d3-261">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-262"><b>Ungefähre Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="341d3-262"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="341d3-263">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="341d3-263">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="341d3-264">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="341d3-264">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="341d3-265">true</span><span class="sxs-lookup"><span data-stu-id="341d3-265">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="341d3-266"><b>Keine Position</b> </span><span class="sxs-lookup"><span data-stu-id="341d3-266"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="341d3-267">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="341d3-267">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="341d3-268">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="341d3-268">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="341d3-269">false</span><span class="sxs-lookup"><span data-stu-id="341d3-269">false</span></span></td>
</tr>
</table>

<span data-ttu-id="341d3-270">Diese Motion Controller-Überwachungs Zustände werden wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="341d3-270">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="341d3-271">**Hohe Genauigkeit:** Während sich der Motion-Controller in der Ansicht des Dashboards befindet, stellt er im Allgemeinen hohe Genauigkeits Positionen auf der Grundlage der visuellen Nachverfolgung bereit.</span><span class="sxs-lookup"><span data-stu-id="341d3-271">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="341d3-272">Beachten Sie, dass ein beweglicher Controller, der vorübergehend das Sichtfeld verlässt oder vorübergehend von den Headset-Sensoren (z. b. durch die andere Seite des Benutzers) verdeckt wird, weiterhin hohe Genauigkeit für kurze Zeit zurückgibt, basierend auf der trägheitverfolgung des Controllers.</span><span class="sxs-lookup"><span data-stu-id="341d3-272">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="341d3-273">**Hohe Genauigkeit (Risiko des Verlusts):** Wenn der Benutzer den Bewegungs Controller über den Rand des Felds der Ansicht bewegt, kann das Headset die Position des Controllers in Kürze nicht visuell nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="341d3-273">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="341d3-274">Die APP weiß, wann der Controller diese FOV-Grenze erreicht hat, indem er den **sourcelossrisk** -REACH-1,0 sieht.</span><span class="sxs-lookup"><span data-stu-id="341d3-274">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="341d3-275">An diesem Punkt kann die APP die Controller Gesten anhalten, die einen stabilen Stream von sehr hochwertigen Posen erfordern.</span><span class="sxs-lookup"><span data-stu-id="341d3-275">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="341d3-276">**Ungefähre Genauigkeit:** Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.</span><span class="sxs-lookup"><span data-stu-id="341d3-276">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="341d3-277">An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="341d3-277">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="341d3-278">Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können so normal agieren, dass Sie in der ungefähren Genauigkeit nicht bemerkt werden</span><span class="sxs-lookup"><span data-stu-id="341d3-278">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="341d3-279">Bei apps mit schwereren Eingabe Anforderungen ist es möglicherweise sinnvoll, diesen Löschvorgang von **hoher** Genauigkeit zur **ungefähren** Genauigkeit zu verstehen, indem die **positionaccuracy** -Eigenschaft überprüft wird, z. b. um dem Benutzer während dieses Zeitraums eine eher großzügigere Position in den offscreenzielen zu geben.</span><span class="sxs-lookup"><span data-stu-id="341d3-279">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="341d3-280">**Keine Position:** Obwohl der Controller für einen längeren Zeitraum mit der ungefähren Genauigkeit arbeiten kann, weiß das System manchmal, dass auch eine vom Text gesperrte Position im Moment nicht aussagekräftig ist.</span><span class="sxs-lookup"><span data-stu-id="341d3-280">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="341d3-281">Beispielsweise kann ein Controller, der gerade eingeschaltet war, nie visuell beobachtet werden, oder ein Benutzer kann einen Controller ablegen, der von einer anderen Person abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="341d3-281">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="341d3-282">Zu diesen Zeitpunkten stellt das System keine Position für die APP bereit, und *trygetposition* gibt false zurück.</span><span class="sxs-lookup"><span data-stu-id="341d3-282">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="341d3-283">Allgemeine Unity-APIs (Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="341d3-283">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="341d3-284">**Namespace:** *unityengine* , *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="341d3-284">**Namespace:** *UnityEngine* , *UnityEngine.XR*</span></span><br>
<span data-ttu-id="341d3-285">**Typen** : *Input* , *XR. Inputtracking*</span><span class="sxs-lookup"><span data-stu-id="341d3-285">**Types** : *Input* , *XR.InputTracking*</span></span>

<span data-ttu-id="341d3-286">Unity verwendet derzeit die allgemeinen *Input. getbutton/Input. getaxis-* APIs, um Eingaben für [das Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [das openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality, einschließlich der Hands-und Motion-Controller, verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="341d3-286">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="341d3-287">Wenn Ihre APP diese APIs für die Eingabe verwendet, kann Sie Bewegungs Controller über mehrere XR-sdche hinweg unterstützen, einschließlich Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="341d3-287">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="341d3-288">Der gedrückte Zustand einer logischen Schaltfläche wird erhalten.</span><span class="sxs-lookup"><span data-stu-id="341d3-288">Getting a logical button's pressed state</span></span>

<span data-ttu-id="341d3-289">Wenn Sie die allgemeinen Unity-Eingabe-APIs verwenden möchten, beginnen Sie in der Regel mit dem Verknüpfen von Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), und binden Sie eine Schaltfläche oder eine Achsen-ID an jeden Namen</span><span class="sxs-lookup"><span data-stu-id="341d3-289">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="341d3-290">Anschließend können Sie Code schreiben, der auf den Namen der logischen Schaltfläche/Achse verweist.</span><span class="sxs-lookup"><span data-stu-id="341d3-290">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="341d3-291">Um z. b. die triggerschaltfläche des linken Bewegungs Controllers der Aktion senden zuzuordnen, wechseln Sie zu **Edit > Project Settings > Input** in Unity, und erweitern Sie die Eigenschaften des Abschnitts übermitteln unter Achsen.</span><span class="sxs-lookup"><span data-stu-id="341d3-291">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="341d3-292">Ändern Sie die Schaltfläche **positiv** oder **alt positive Schaltfläche** , um die Schaltfläche "Taste **14** " wie folgt zu lesen:</span><span class="sxs-lookup"><span data-stu-id="341d3-292">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14** , like this:</span></span>

<span data-ttu-id="341d3-293">![InputManager von Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="341d3-293">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="341d3-294">*Unity-InputManager*</span><span class="sxs-lookup"><span data-stu-id="341d3-294">*Unity InputManager*</span></span>

<span data-ttu-id="341d3-295">Das Skript kann dann mithilfe von " *Input. getbutton* " die Aktion "Senden" überprüfen:</span><span class="sxs-lookup"><span data-stu-id="341d3-295">Your script can then check for the Submit action using *Input.GetButton* :</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="341d3-296">Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **size** -Eigenschaft unter **Achsen** ändern.</span><span class="sxs-lookup"><span data-stu-id="341d3-296">You can add more logical buttons by changing the **Size** property under **Axes** .</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="341d3-297">Direktes drücken des gedrückten Zustands einer physischen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="341d3-297">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="341d3-298">Sie können mithilfe von *Input. GetKey* auch manuell über den voll qualifizierten Namen auf Schaltflächen zugreifen:</span><span class="sxs-lookup"><span data-stu-id="341d3-298">You can also access buttons manually by their fully-qualified name, using *Input.GetKey* :</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="341d3-299">Die Pose eines Hand-oder Bewegungs Controllers</span><span class="sxs-lookup"><span data-stu-id="341d3-299">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="341d3-300">Sie können auf die Position und Drehung des Controllers mithilfe von *XR zugreifen. Inputtracking* :</span><span class="sxs-lookup"><span data-stu-id="341d3-300">You can access the position and rotation of the controller, using *XR.InputTracking* :</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="341d3-301">Beachten Sie, dass dies die Zieh Punktposition des Controllers darstellt (in der der Benutzer den Controller hält). Dies ist nützlich, um ein Schwert oder eine Waffe in der Hand des Benutzers oder ein Modell des Controllers selbst zu rendern.</span><span class="sxs-lookup"><span data-stu-id="341d3-301">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="341d3-302">Beachten Sie, dass die Beziehung zwischen diesem Ziehpunkt und der Zeiger Pose (bei der die Spitze des Controllers zeigt) sich zwischen Controllern unterscheiden kann.</span><span class="sxs-lookup"><span data-stu-id="341d3-302">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="341d3-303">Zurzeit ist der Zugriff auf die Zeiger-Pose des Controllers nur über die in den folgenden Abschnitten beschriebene Mr-spezifische Eingabe-API möglich.</span><span class="sxs-lookup"><span data-stu-id="341d3-303">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="341d3-304">Windows-spezifische APIs (XR. WSA. Der</span><span class="sxs-lookup"><span data-stu-id="341d3-304">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="341d3-305">**Namespace:** *unityengine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="341d3-305">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="341d3-306">**Typen** : *interaktionsmanager* , *interaktionsourcestate* , *interaktionsource* , *interaktionsourceproperties* , *interaktionsourcekind* , *interaktionsourcelokation*</span><span class="sxs-lookup"><span data-stu-id="341d3-306">**Types** : *InteractionManager* , *InteractionSourceState* , *InteractionSource* , *InteractionSourceProperties* , *InteractionSourceKind* , *InteractionSourceLocation*</span></span>

<span data-ttu-id="341d3-307">Um ausführlichere Informationen zu Windows Mixed Reality-Hand Eingaben (für hololens) und Bewegungs Controller zu erhalten, können Sie die Windows-spezifischen räumlichen Eingabe-APIs im Namespace *unityengine. XR. WSA. Input* verwenden.</span><span class="sxs-lookup"><span data-stu-id="341d3-307">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="341d3-308">Auf diese Weise können Sie auf zusätzliche Informationen zugreifen, wie z. b. Die Positionsgenauigkeit oder die quellart, sodass Sie die Hände und Controller voneinander trennen können.</span><span class="sxs-lookup"><span data-stu-id="341d3-308">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="341d3-309">Abrufen des Zustands von Händen und Bewegungs Controllern</span><span class="sxs-lookup"><span data-stu-id="341d3-309">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="341d3-310">Sie können den Status dieses Frames für jede Interaktions Quelle (Hand-oder Bewegungs Controller) mithilfe der *getcurrentreading* -Methode abrufen.</span><span class="sxs-lookup"><span data-stu-id="341d3-310">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="341d3-311">Jedes *interaktionsourcestate* , das Sie zurückerhalten, stellt eine Interaktions Quelle zum aktuellen Zeitpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="341d3-311">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="341d3-312">Das *interaktionsourcestate* macht Informationen wie z. b.:</span><span class="sxs-lookup"><span data-stu-id="341d3-312">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="341d3-313">Welche [Arten von Druck](../../design/motion-controllers.md) vorgehungen werden auftreten (Select/Menu/grasp/Touchpad/Thumbstick)</span><span class="sxs-lookup"><span data-stu-id="341d3-313">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="341d3-314">Andere Daten, die für Bewegungs Controller spezifisch sind, z. b. die XY-Koordinaten des Touchpads und/oder Finger Ansichts Status</span><span class="sxs-lookup"><span data-stu-id="341d3-314">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="341d3-315">Interaktionsourcekind, um zu wissen, ob es sich bei der Quelle um einen Hand-oder Bewegungs Controller handelt</span><span class="sxs-lookup"><span data-stu-id="341d3-315">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="341d3-316">Abrufen von vorwärts vorhergesagten Renderingvorgängen</span><span class="sxs-lookup"><span data-stu-id="341d3-316">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="341d3-317">Beim Abrufen von Interaktions Quelldaten von Hand und Controllern sind die von Ihnen abzurufenden Datenquellen für den Zeitpunkt, zu dem die Daten des Bilds den Augen des Benutzers erreichen, von vorne vorhergesagte Posen.</span><span class="sxs-lookup"><span data-stu-id="341d3-317">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="341d3-318">Diese vorwärts Gesagten Posen werden am besten zum **Rendern** des Controllers oder eines gehaltenen Objekts in jedem Frame verwendet.</span><span class="sxs-lookup"><span data-stu-id="341d3-318">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="341d3-319">Wenn Sie ein bestimmtes Press-oder-Release mit dem Controller als Ziel verwenden, wird dies am genauesten sein, wenn Sie die nachstehend beschriebenen Vergangenheits Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="341d3-319">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="341d3-320">Sie können auch die vorwärts Gesagte Kopfzeile für diesen aktuellen Frame erhalten.</span><span class="sxs-lookup"><span data-stu-id="341d3-320">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="341d3-321">Wie bei der Quell Darstellung ist dies für das **Rendern** eines Cursors nützlich, obwohl das Ziel einer bestimmten Presse oder Freigabe am genauesten ist, wenn Sie die unten beschriebenen Vergangenheits Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="341d3-321">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="341d3-322">Behandeln von Interaktions Quell Ereignissen</span><span class="sxs-lookup"><span data-stu-id="341d3-322">Handling interaction source events</span></span>

<span data-ttu-id="341d3-323">Um Eingabeereignisse zu behandeln, wie Sie mit Ihren exakten Vergangenheits Daten auftreten, können Sie Interaktions Quell Ereignisse behandeln, anstatt Sie abzufragen.</span><span class="sxs-lookup"><span data-stu-id="341d3-323">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="341d3-324">So behandeln Sie Interaktions Quell Ereignisse:</span><span class="sxs-lookup"><span data-stu-id="341d3-324">To handle interaction source events:</span></span>
* <span data-ttu-id="341d3-325">Registrieren Sie sich für ein *interaktionmanager* -Eingabe Ereignis.</span><span class="sxs-lookup"><span data-stu-id="341d3-325">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="341d3-326">Für jede Art von Interaktions Ereignis, für das Sie sich interessieren, müssen Sie es abonnieren.</span><span class="sxs-lookup"><span data-stu-id="341d3-326">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="341d3-327">Behandeln Sie das-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="341d3-327">Handle the event.</span></span> <span data-ttu-id="341d3-328">Wenn Sie ein Interaktions Ereignis abonniert haben, erhalten Sie gegebenenfalls den Rückruf.</span><span class="sxs-lookup"><span data-stu-id="341d3-328">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="341d3-329">Im Beispiel " *sourcepressed* " ist dies der Fall, nachdem die Quelle erkannt wurde und bevor Sie freigegeben oder verloren geht.</span><span class="sxs-lookup"><span data-stu-id="341d3-329">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="341d3-330">Beenden der Behandlung eines Ereignisses</span><span class="sxs-lookup"><span data-stu-id="341d3-330">How to stop handling an event</span></span>

<span data-ttu-id="341d3-331">Sie müssen die Verarbeitung eines Ereignisses beenden, wenn Sie nicht mehr an dem Ereignis interessiert sind oder das Objekt zerstören, das das Ereignis abonniert hat.</span><span class="sxs-lookup"><span data-stu-id="341d3-331">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="341d3-332">Wenn Sie die Verarbeitung des Ereignisses beenden möchten, kündigen Sie das Ereignis an.</span><span class="sxs-lookup"><span data-stu-id="341d3-332">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="341d3-333">Liste der Interaktions Quell Ereignisse</span><span class="sxs-lookup"><span data-stu-id="341d3-333">List of interaction source events</span></span>

<span data-ttu-id="341d3-334">Die folgenden Interaktions Quell Ereignisse sind verfügbar:</span><span class="sxs-lookup"><span data-stu-id="341d3-334">The available interaction source events are:</span></span>
* <span data-ttu-id="341d3-335">*Interaktionsourceerkannt* (Quelle wird aktiv)</span><span class="sxs-lookup"><span data-stu-id="341d3-335">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="341d3-336">*Interaktionsourcelost* (wird inaktiv)</span><span class="sxs-lookup"><span data-stu-id="341d3-336">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="341d3-337">*Interaktionsourcepressed* (tippen, drücken der Schaltfläche oder "auswählen")</span><span class="sxs-lookup"><span data-stu-id="341d3-337">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="341d3-338">*Interaktionsourcereleasing* (Ende einer Tap-Schaltfläche, oder Ende der "Select"-Taste)</span><span class="sxs-lookup"><span data-stu-id="341d3-338">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="341d3-339">*Interaktionsourceupveraltet* (verschieben oder anderweitig ändern eines Zustands)</span><span class="sxs-lookup"><span data-stu-id="341d3-339">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="341d3-340">Ereignisse für Vergangenheits Ziele, die mit einem Press oder Release am genauesten zu vergleichen sind</span><span class="sxs-lookup"><span data-stu-id="341d3-340">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="341d3-341">Die zuvor beschriebenen Abruf-APIs machen Ihre APP-vorhergesagte Posen aus.</span><span class="sxs-lookup"><span data-stu-id="341d3-341">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="341d3-342">Obwohl die vorhergesagten Posen am besten zum Rendern des Controllers oder eines virtuellen Hand Held Objekts geeignet sind, sind zukünftige Posen nicht optimal für das Ziel, aus zwei Hauptgründen:</span><span class="sxs-lookup"><span data-stu-id="341d3-342">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="341d3-343">Wenn der Benutzer eine Schaltfläche auf einem Controller drückt, kann es ungefähr 20 ms drahtlose Latenz über Bluetooth geben, bevor das System den Druck erhält.</span><span class="sxs-lookup"><span data-stu-id="341d3-343">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="341d3-344">Wenn Sie dann eine vorwärts Gesagte Pose verwenden, gibt es eine weitere 10-20 MS der Forward-Vorhersage, auf die die Zeit angewendet wird, in der die Daten des aktuellen Frames die Augen des Benutzers erreichen.</span><span class="sxs-lookup"><span data-stu-id="341d3-344">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="341d3-345">Dies bedeutet, dass bei der Abfrage eine Quell Pose oder eine Kopfzeile angezeigt wird, die 30 bis 40 ms vorwärts ist, von wo aus die Kopfzeile des Benutzers und die Hände wieder zurück waren, als die Presse oder das Release aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="341d3-345">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="341d3-346">Bei der Eingabe von hololens-Hand Eingaben kommt es zu einer ähnlichen Verarbeitungs Verzögerung, um den Press zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="341d3-346">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="341d3-347">Um basierend auf der ursprünglichen Absicht des Benutzers für eine Hand oder einen Controller eine genaue Zielsetzung zu erreichen, sollten Sie die historische Quell Pose oder die Kopfzeile aus dem *interaktionsourcepressed* -oder *interaktionsourcereleasing* -Eingabe Ereignis verwenden.</span><span class="sxs-lookup"><span data-stu-id="341d3-347">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="341d3-348">Sie können eine Presse oder eine Freigabe mit Verlaufs Daten des Benutzers oder des Controllers als Ziel haben:</span><span class="sxs-lookup"><span data-stu-id="341d3-348">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="341d3-349">Die Kopfzeile zu dem Zeitpunkt, an dem eine Geste oder eine Controller Bewegung aufgetreten ist, die für die **Ziel** Bestimmung verwendet werden kann, um zu bestimmen, was der [Benutzer untersucht hat:](../../design/gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="341d3-349">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="341d3-350">Die Quell Pose zu dem Zeitpunkt, zu dem eine Bewegung des Bewegungs Controllers stattgefunden hat. diese kann verwendet werden, **um zu bestimmen** , auf welche Weise der Benutzer den Controller verwiesen hat.</span><span class="sxs-lookup"><span data-stu-id="341d3-350">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="341d3-351">Dabei handelt es sich um den Zustand des Controllers, der den Druck erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="341d3-351">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="341d3-352">Wenn Sie den Controller selbst rendern, können Sie die Zeiger Darstellung anstelle der Ziehpunkt-Pose anfordern, um das Ziel-Ray von dem zu überprüfen, was der Benutzer für den natürlichen Tipp des gerenderten Controllers in Erwägung zieht:</span><span class="sxs-lookup"><span data-stu-id="341d3-352">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="341d3-353">Beispiel für Ereignishandler</span><span class="sxs-lookup"><span data-stu-id="341d3-353">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="341d3-354">APIs für zusammengesetzte Gesten auf hoher Ebene (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="341d3-354">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="341d3-355">**Namespace:** *unityengine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="341d3-355">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="341d3-356">**Typen** : *GestureRecognizer* , *gesturesettings* , *interaktionsourcekind*</span><span class="sxs-lookup"><span data-stu-id="341d3-356">**Types** : *GestureRecognizer* , *GestureSettings* , *InteractionSourceKind*</span></span>

<span data-ttu-id="341d3-357">Ihre APP kann auch zusammengesetzte Gesten auf höherer Ebene für räumliche Eingabe Quellen, Tap-, Halt-, Manipulations-und Navigations Gesten erkennen.</span><span class="sxs-lookup"><span data-stu-id="341d3-357">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="341d3-358">Mit dem GestureRecognizer können Sie diese zusammengesetzten Gesten sowohl in [Hand](../../design/gaze-and-commit.md#composite-gestures) -als auch in [Bewegungs Controllern](../../design/motion-controllers.md) erkennen.</span><span class="sxs-lookup"><span data-stu-id="341d3-358">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="341d3-359">Jedes Gesten Ereignis für den GestureRecognizer stellt sowohl sourcekind für die Eingabe als auch den Ziel-Head-Strahl zum Zeitpunkt des Ereignisses bereit.</span><span class="sxs-lookup"><span data-stu-id="341d3-359">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="341d3-360">Einige Ereignisse bieten zusätzliche kontextspezifische Informationen.</span><span class="sxs-lookup"><span data-stu-id="341d3-360">Some events provide additional context specific information.</span></span>

<span data-ttu-id="341d3-361">Es sind nur wenige Schritte erforderlich, um Gesten mithilfe einer Gestenerkennung zu erfassen:</span><span class="sxs-lookup"><span data-stu-id="341d3-361">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="341d3-362">Erstellen einer neuen Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="341d3-362">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="341d3-363">Legen Sie fest, welche Gesten überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="341d3-363">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="341d3-364">Ereignisse für diese Gesten abonnieren</span><span class="sxs-lookup"><span data-stu-id="341d3-364">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="341d3-365">Erfassungs Gesten starten</span><span class="sxs-lookup"><span data-stu-id="341d3-365">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="341d3-366">Erstellen einer neuen Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="341d3-366">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="341d3-367">Wenn Sie den *GestureRecognizer* verwenden möchten, müssen Sie einen *GestureRecognizer* erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="341d3-367">To use the *GestureRecognizer* , you must have created a *GestureRecognizer* :</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="341d3-368">Legen Sie fest, welche Gesten überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="341d3-368">Specify which gestures to watch for</span></span>

<span data-ttu-id="341d3-369">Geben Sie an, welche Gesten Sie über "" mit "" auf "" festgelegt haben *()* :</span><span class="sxs-lookup"><span data-stu-id="341d3-369">Specify which gestures you are interested in via *SetRecognizableGestures()* :</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="341d3-370">Ereignisse für diese Gesten abonnieren</span><span class="sxs-lookup"><span data-stu-id="341d3-370">Subscribe to events for those gestures</span></span>

<span data-ttu-id="341d3-371">Abonnieren Sie Ereignisse für die Gesten, an denen Sie interessiert sind.</span><span class="sxs-lookup"><span data-stu-id="341d3-371">Subscribe to events for the gestures you are interested in.</span></span>

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
><span data-ttu-id="341d3-372">Navigations-und Manipulations Gesten schließen sich gegenseitig für eine Instanz eines *GestureRecognizer* aus.</span><span class="sxs-lookup"><span data-stu-id="341d3-372">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer* .</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="341d3-373">Erfassungs Gesten starten</span><span class="sxs-lookup"><span data-stu-id="341d3-373">Start capturing gestures</span></span>

<span data-ttu-id="341d3-374">Standardmäßig überwacht ein *GestureRecognizer* die Eingabe erst, wenn *startcapturinggesten ()* aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="341d3-374">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="341d3-375">Möglicherweise wird ein Gesten Ereignis generiert, nachdem *stopcapturinggesten ()* aufgerufen wurde, wenn Eingaben vor dem Frame durchgeführt wurden, in dem *stopcapturinggesten ()* verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="341d3-375">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="341d3-376">Der *GestureRecognizer* weiß, ob er während des vorherigen Frames ein-oder ausgeschaltet war, in dem die Geste tatsächlich aufgetreten ist, und daher ist es zuverlässig, die Gesten Überwachung auf der Grundlage der Anzeige Ziele dieses Frames zu starten und zu beenden.</span><span class="sxs-lookup"><span data-stu-id="341d3-376">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="341d3-377">Erfassungs Gesten nicht mehr</span><span class="sxs-lookup"><span data-stu-id="341d3-377">Stop capturing gestures</span></span>

<span data-ttu-id="341d3-378">So verhindern Sie die Gestenerkennung:</span><span class="sxs-lookup"><span data-stu-id="341d3-378">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="341d3-379">Entfernen einer Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="341d3-379">Removing a gesture recognizer</span></span>

<span data-ttu-id="341d3-380">Denken Sie daran, abonnierte Ereignisse abzubestellen, bevor Sie ein *GestureRecognizer* -Objekt zerstören.</span><span class="sxs-lookup"><span data-stu-id="341d3-380">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="341d3-381">Rendern des Motion Controller-Modells in Unity</span><span class="sxs-lookup"><span data-stu-id="341d3-381">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="341d3-382">![Motion Controller-Modell und-teleportierung](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="341d3-382">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="341d3-383">*Motion Controller-Modell und-teleportierung*</span><span class="sxs-lookup"><span data-stu-id="341d3-383">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="341d3-384">Zum Rendering von Bewegungs Controllern in Ihrer APP, die den physischen Controllern entsprechen, die die Benutzer als verschiedene Schaltflächen verwenden, die Sie verwenden, können Sie die **vorfab von "mutioncontroller** " im [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)verwenden.</span><span class="sxs-lookup"><span data-stu-id="341d3-384">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="341d3-385">Dieser Prefab lädt das korrekte gltf-Modell zur Laufzeit dynamisch aus dem installierten Motion Controller-Treiber des Systems.</span><span class="sxs-lookup"><span data-stu-id="341d3-385">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="341d3-386">Es ist wichtig, dass diese Modelle dynamisch geladen werden, anstatt Sie manuell in den Editor zu importieren, damit Ihre APP physisch genaue 3D-Modelle für alle aktuellen und zukünftigen Controller anzeigt, die Ihre Benutzer möglicherweise haben.</span><span class="sxs-lookup"><span data-stu-id="341d3-386">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="341d3-387">Befolgen Sie [die Anweisungen für die ersten](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) Schritte, um das Mixed Reality Toolkit herunterzuladen und es Ihrem Unity-Projekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="341d3-387">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="341d3-388">Wenn Sie Ihre Kamera durch das *mixedrealitycameraparent* -präfab im Rahmen der Schritte für die ersten Schritte ersetzt haben, können Sie es tun!</span><span class="sxs-lookup"><span data-stu-id="341d3-388">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="341d3-389">Dieses präfab umfasst das Rendern von Bewegungs Controllern.</span><span class="sxs-lookup"><span data-stu-id="341d3-389">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="341d3-390">Andernfalls fügen Sie *Assets/holotoolkit/Input/Prefabs/mutioncontrollers. Prefab* aus dem Projektbereich in die Szene ein.</span><span class="sxs-lookup"><span data-stu-id="341d3-390">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="341d3-391">Sie sollten diese Prefab als untergeordnetes Element eines beliebigen übergeordneten Objekts hinzufügen, das Sie verwenden, um die Kamera zu bewegen, wenn der Benutzer in der Szene Teleports verwendet, sodass die Controller mit dem Benutzer zusammenkommen.</span><span class="sxs-lookup"><span data-stu-id="341d3-391">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="341d3-392">Wenn Ihre APP keine teleportierung umfasst, fügen Sie einfach die vorfab im Stammverzeichnis Ihrer Szene hinzu.</span><span class="sxs-lookup"><span data-stu-id="341d3-392">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="341d3-393">Auslösen von Objekten</span><span class="sxs-lookup"><span data-stu-id="341d3-393">Throwing objects</span></span>

<span data-ttu-id="341d3-394">Das Auslösen von Objekten in Virtual Reality ist ein schwierigeres Problem, das möglicherweise zuerst erscheint.</span><span class="sxs-lookup"><span data-stu-id="341d3-394">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="341d3-395">Wie bei den meisten physisch basierenden Interaktionen verhält es sich beim Auslösen im Spiel auf unerwartete Weise, es ist sofort offensichtlich und unterbricht das eintauchen.</span><span class="sxs-lookup"><span data-stu-id="341d3-395">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="341d3-396">Wir haben einige Zeit damit verbracht, ein physisch korrektes auslösverhalten darzustellen, und haben einige Richtlinien, die über Updates auf unserer Plattform aktiviert wurden, für Sie freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="341d3-396">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="341d3-397">Ein Beispiel für die Implementierung von "throw" finden Sie [hier](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="341d3-397">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="341d3-398">Dieses Beispiel befolgt diese vier Richtlinien:</span><span class="sxs-lookup"><span data-stu-id="341d3-398">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="341d3-399">**Verwenden Sie die *Geschwindigkeit* des Controllers anstelle der Position** .</span><span class="sxs-lookup"><span data-stu-id="341d3-399">**Use the controller’s *velocity* instead of position** .</span></span> <span data-ttu-id="341d3-400">Im November-Update für Windows haben wir eine Änderung des Verhaltens eingeführt, wenn der [ungefähre Status der Positionsüberwachung ("ungefähre"](../../design/motion-controllers.md#controller-tracking-state)) ist.</span><span class="sxs-lookup"><span data-stu-id="341d3-400">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="341d3-401">In diesem Zustand werden Velocity-Informationen über den Controller weiterhin angezeigt, solange wir glauben, dass es sich um eine hohe Genauigkeit handelt, die häufig länger ist als die Position mit hoher Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="341d3-401">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="341d3-402">**Integrieren Sie die *Winkelgeschwindigkeit* des Controllers** .</span><span class="sxs-lookup"><span data-stu-id="341d3-402">**Incorporate the *angular velocity* of the controller** .</span></span> <span data-ttu-id="341d3-403">Diese Logik ist in der- `throwing.cs` Datei in der `GetThrownObjectVelAngVel` statischen-Methode innerhalb des oben verknüpften Pakets enthalten:</span><span class="sxs-lookup"><span data-stu-id="341d3-403">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="341d3-404">Wenn die Angular-Geschwindigkeit beibehalten wird, muss das ausgelöste Objekt dieselbe Angular-Geschwindigkeit wie in der Zeit der throw-Ausnahme beibehalten: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="341d3-404">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="341d3-405">Da sich der Mittelpunkt der Masse des ausgelösten Objekts wahrscheinlich nicht am Ursprung der Ziehpunkt-Pose befindet, weist er wahrscheinlich eine andere Geschwindigkeit auf als der Controller im Verweis auf den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="341d3-405">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="341d3-406">Der Teil der auf diese Weise beigetragenen Geschwindigkeit des Objekts ist die sofortige tangential Geschwindigkeit des Mittelpunkts der Masse des ausgelösten Objekts um den Controller Ursprung.</span><span class="sxs-lookup"><span data-stu-id="341d3-406">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="341d3-407">Diese tangential-Geschwindigkeit ist das Kreuz Produkt der Angular-Geschwindigkeit des Controllers mit dem Vektor, der den Abstand zwischen dem Controller Ursprung und dem Mittelpunkt der Masse des ausgelösten Objekts darstellt.</span><span class="sxs-lookup"><span data-stu-id="341d3-407">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="341d3-408">Die Gesamtgeschwindigkeit des ausgelösten Objekts entspricht daher der Summe der Geschwindigkeit des Controllers und der tangential Geschwindigkeit: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="341d3-408">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="341d3-409">Achten **Sie genau auf die *Zeit* , zu der wir die Geschwindigkeit anwenden** .</span><span class="sxs-lookup"><span data-stu-id="341d3-409">**Pay close attention to the *time* at which we apply the velocity** .</span></span> <span data-ttu-id="341d3-410">Wenn eine Schaltfläche gedrückt wird, kann es bis zu 20 ms dauern, bis das Ereignis durch Bluetooth bis zum Betriebssystem hochskalieren kann.</span><span class="sxs-lookup"><span data-stu-id="341d3-410">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="341d3-411">Dies bedeutet Folgendes: Wenn Sie eine Änderung des Controller Zustands von "gedrückt" in "nicht gedrückt" oder umgekehrt abrufen, werden die Informationen, die Sie mit dem Controller erhalten, tatsächlich vor dieser Zustandsänderung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="341d3-411">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="341d3-412">Außerdem wird die von unserer Abruf-API dargestellte Controller Darstellung vorhergesagt, um eine wahrscheinliche Darstellung zum Zeitpunkt der Anzeige des Frames widerzuspiegeln, der in der Zukunft mehr als 20 ms betragen kann.</span><span class="sxs-lookup"><span data-stu-id="341d3-412">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="341d3-413">Dies eignet sich gut für das *Rendern* von gehaltenen Objekten, stellt jedoch unser Zeitproblem für das *Ziel des Objekts* dar</span><span class="sxs-lookup"><span data-stu-id="341d3-413">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="341d3-414">Wenn beim November-Update ein Unity-Ereignis wie *interaktionsourcepressed* oder *interaktionsourcereleasing* gesendet wird, enthält der Zustand die Vergangenheits Daten von hinten, wenn die Schaltfläche tatsächlich gedrückt oder freigegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="341d3-414">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="341d3-415">Um das präzisere Controller Rendering und die Zielplattform für das Ausführen von Triggeroptionen zu erhalten, müssen Sie nach Bedarf Abruf-und Ereignis Ereignisse ordnungsgemäß verwenden:</span><span class="sxs-lookup"><span data-stu-id="341d3-415">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="341d3-416">Für den Controller, der die einzelnen Frames **rendert** , sollte Ihre APP das *gameobject* des Controllers an der vorwärts Gesagten Controller Darstellung für die Photon-Zeit des aktuellen Frames positionieren.</span><span class="sxs-lookup"><span data-stu-id="341d3-416">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="341d3-417">Sie erhalten diese Daten von Unity-Abruf-APIs wie *[XR. Inputtracking. getlocalposition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oder *[XR. WSA. Input. interaktionmanager. getcurrentreading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .</span><span class="sxs-lookup"><span data-stu-id="341d3-417">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .</span></span>
   * <span data-ttu-id="341d3-418">Für den Controller, der auf eine Presse oder ein Release **abzielt** , sollte Ihre APP auf der Grundlage der Verlaufs Controller-Pose für das Press-oder releaseereignis auf der Grundlage der Verlaufs Controller-</span><span class="sxs-lookup"><span data-stu-id="341d3-418">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="341d3-419">Sie erhalten diese Daten aus den Unity-Ereignis-APIs, wie z. b. *[interaktionmanager. interaktionsourcepressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .</span><span class="sxs-lookup"><span data-stu-id="341d3-419">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .</span></span>
* <span data-ttu-id="341d3-420">**Verwenden Sie die** Ziehpunkt-Pose.</span><span class="sxs-lookup"><span data-stu-id="341d3-420">**Use the grip pose** .</span></span> <span data-ttu-id="341d3-421">Winkelgeschwindigkeit und-Geschwindigkeit werden relativ zur Zieh Punkt Pose, nicht zum Darstellen von Zeigern, angezeigt.</span><span class="sxs-lookup"><span data-stu-id="341d3-421">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="341d3-422">Das auslösen wird mit zukünftigen Windows-Updates weiter verbessern, und Sie können davon ausgehen, dass Sie hier weitere Informationen finden.</span><span class="sxs-lookup"><span data-stu-id="341d3-422">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="341d3-423">Gesten-und Bewegungs Controller in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="341d3-423">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="341d3-424">Sie können über den Eingabe-Manager auf Gesten-und Bewegungs Controller zugreifen.</span><span class="sxs-lookup"><span data-stu-id="341d3-424">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="341d3-425">Geste in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="341d3-425">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="341d3-426">Motion Controller in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="341d3-426">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="341d3-427">Immer am Ball mit Tutorials</span><span class="sxs-lookup"><span data-stu-id="341d3-427">Follow along with tutorials</span></span>

<span data-ttu-id="341d3-428">Schritt-für-Schritt-Tutorials mit ausführlicheren Anpassungs Beispielen sind in der Mixed Reality Academy verfügbar:</span><span class="sxs-lookup"><span data-stu-id="341d3-428">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="341d3-429">MR-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="341d3-429">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="341d3-430">MR-Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="341d3-430">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="341d3-431">[![Mr-Eingabe 213-Motion Controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="341d3-431">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="341d3-432">*Mr-Eingabe 213-Motion Controller*</span><span class="sxs-lookup"><span data-stu-id="341d3-432">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="341d3-433">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="341d3-433">Next Development Checkpoint</span></span>

<span data-ttu-id="341d3-434">Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="341d3-434">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="341d3-435">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="341d3-435">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="341d3-436">Hand- und Eye-Tracking</span><span class="sxs-lookup"><span data-stu-id="341d3-436">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="341d3-437">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="341d3-437">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="341d3-438">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="341d3-438">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="341d3-439">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="341d3-439">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="341d3-440">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="341d3-440">See also</span></span>

* [<span data-ttu-id="341d3-441">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="341d3-441">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="341d3-442">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="341d3-442">Motion controllers</span></span>](../../design/motion-controllers.md)
