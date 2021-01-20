---
title: Motion-Controller in Unity
description: Erfahren Sie, wie Sie mit der Motion Controller-Eingabe mithilfe von XR und allgemeinen Schaltflächen-und Achsen-APIs Maßnahmen für Ihren Blick in Unity durchführen.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Motion Controllers, Unity, Input, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: db103e674a369f13e62aac5e8c0513b2c2c17f9e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583508"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="83252-104">Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="83252-104">Motion controllers in Unity</span></span>

<span data-ttu-id="83252-105">Es gibt zwei wichtige Möglichkeiten, um Ihre [Blicke in Unity](gaze-in-unity.md), [Handgesten](../../design/gaze-and-commit.md#composite-gestures) und [Bewegungs Controllern](../../design/motion-controllers.md) in hololens und immersiven HMD zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="83252-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="83252-106">Sie greifen über dieselben APIs in Unity auf die Daten für beide Quellen räumlicher Eingaben zu.</span><span class="sxs-lookup"><span data-stu-id="83252-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="83252-107">Unity bietet zwei Hauptmethoden für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="83252-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="83252-108">Die gängigen *Input. getbutton/Input. getaxis-* APIs funktionieren über mehrere Unity-XR-SDK hinweg, während die *interaktionmanager/GestureRecognizer* -API speziell für Windows Mixed Reality den vollständigen Satz räumlicher Eingabedaten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="83252-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="83252-109">Eingabe-APIs für Unity XR</span><span class="sxs-lookup"><span data-stu-id="83252-109">Unity XR input APIs</span></span>

<span data-ttu-id="83252-110">Bei neuen Projekten wird die Verwendung der neuen XR-Eingabe-APIs von Anfang an empfohlen.</span><span class="sxs-lookup"><span data-stu-id="83252-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="83252-111">Weitere Informationen zu den [XR-APIs](https://docs.unity3d.com/Manual/xr_input.html)finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="83252-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="83252-112">Unity-Schaltfläche/Achsen Zuordnung (Tabelle)</span><span class="sxs-lookup"><span data-stu-id="83252-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="83252-113">Der Eingabe-Manager von Unity für Windows Mixed Reality Motion Controllers unterstützt die unten aufgeführten Schaltflächen-und Achsen-IDs über die *Eingabe. getbutton/getaxis-* APIs.</span><span class="sxs-lookup"><span data-stu-id="83252-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="83252-114">Die Spalte "Windows Mr-spezifisch" bezieht sich auf Eigenschaften, die vom *interaktionsourcestate* -Typ verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="83252-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="83252-115">Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="83252-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="83252-116">Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality entsprechen im Allgemeinen den Oculus-Schaltflächen-/Achsen-IDs</span><span class="sxs-lookup"><span data-stu-id="83252-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="83252-117">Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality unterscheiden sich auf zwei Arten von den Zuordnungen von openvr:</span><span class="sxs-lookup"><span data-stu-id="83252-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="83252-118">Die Zuordnung verwendet Touchpad-IDs, die sich vom Finger Stick unterscheiden, um Controller mit beiden Fingerabdrücken und Touchpads zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="83252-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="83252-119">Durch die Zuordnung wird vermieden, dass die Schaltflächen-IDs A und X für die Menü Schaltflächen überladen werden, damit Sie für die physischen abxy-Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="83252-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="83252-120">Eingabe</span><span class="sxs-lookup"><span data-stu-id="83252-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="83252-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a></span><span class="sxs-lookup"><span data-stu-id="83252-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="83252-122">(Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="83252-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="83252-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows-spezifische Eingabe-API</a></span><span class="sxs-lookup"><span data-stu-id="83252-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="83252-124">XR. WSA. Der</span><span class="sxs-lookup"><span data-stu-id="83252-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="83252-125">Links</span><span class="sxs-lookup"><span data-stu-id="83252-125">Left hand</span></span> </th><th> <span data-ttu-id="83252-126">Rechte Seite</span><span class="sxs-lookup"><span data-stu-id="83252-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="83252-127">Select-Taste gedrückt</span><span class="sxs-lookup"><span data-stu-id="83252-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="83252-128">Achse 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="83252-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="83252-129">Achse 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="83252-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="83252-130">selectpressed</span><span class="sxs-lookup"><span data-stu-id="83252-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-131">Auswählen des analogen Auslöse Werts</span><span class="sxs-lookup"><span data-stu-id="83252-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="83252-132">Achse 9</span><span class="sxs-lookup"><span data-stu-id="83252-132">Axis 9</span></span> </td><td> <span data-ttu-id="83252-133">Achse 10</span><span class="sxs-lookup"><span data-stu-id="83252-133">Axis 10</span></span> </td><td> <span data-ttu-id="83252-134">selectpressedamount</span><span class="sxs-lookup"><span data-stu-id="83252-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-135">Select-Taste teilweise gedrückt</span><span class="sxs-lookup"><span data-stu-id="83252-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="83252-136">Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="83252-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="83252-137">Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="83252-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="83252-138">selectpressedamount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="83252-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-139">Menü Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="83252-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="83252-140">Schaltfläche 6 \*</span><span class="sxs-lookup"><span data-stu-id="83252-140">Button 6\*</span></span> </td><td> <span data-ttu-id="83252-141">Schaltfläche 7 \*</span><span class="sxs-lookup"><span data-stu-id="83252-141">Button 7\*</span></span> </td><td> <span data-ttu-id="83252-142">menupressed</span><span class="sxs-lookup"><span data-stu-id="83252-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-143">Zieh Schaltfläche gedrückt</span><span class="sxs-lookup"><span data-stu-id="83252-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="83252-144">Achse 11 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="83252-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="83252-145">Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="83252-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="83252-146">Achse 12 = 1,0 (keine analogen Werte)</span><span class="sxs-lookup"><span data-stu-id="83252-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="83252-147">Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </span><span class="sxs-lookup"><span data-stu-id="83252-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="83252-148">Schna</span><span class="sxs-lookup"><span data-stu-id="83252-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-149">Thumbstick X <i>(Links:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="83252-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="83252-150">Achse 1</span><span class="sxs-lookup"><span data-stu-id="83252-150">Axis 1</span></span> </td><td> <span data-ttu-id="83252-151">Achse 4</span><span class="sxs-lookup"><span data-stu-id="83252-151">Axis 4</span></span> </td><td> <span data-ttu-id="83252-152">thumbstickposition. x</span><span class="sxs-lookup"><span data-stu-id="83252-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-153">Thumbstick Y <i>(oben:-1,0, unten: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="83252-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="83252-154">Achse 2</span><span class="sxs-lookup"><span data-stu-id="83252-154">Axis 2</span></span> </td><td> <span data-ttu-id="83252-155">Achse 5</span><span class="sxs-lookup"><span data-stu-id="83252-155">Axis 5</span></span> </td><td> <span data-ttu-id="83252-156">thumbstickposition. y</span><span class="sxs-lookup"><span data-stu-id="83252-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-157">Thumbstick gedrückt</span><span class="sxs-lookup"><span data-stu-id="83252-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="83252-158">Schaltfläche 8</span><span class="sxs-lookup"><span data-stu-id="83252-158">Button 8</span></span> </td><td> <span data-ttu-id="83252-159">Schaltfläche 9</span><span class="sxs-lookup"><span data-stu-id="83252-159">Button 9</span></span> </td><td> <span data-ttu-id="83252-160">thumbstickpressed</span><span class="sxs-lookup"><span data-stu-id="83252-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-161">Touchpad X <i>(Links:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="83252-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="83252-162">Achse 17 \*</span><span class="sxs-lookup"><span data-stu-id="83252-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="83252-163">Achse 19 \*</span><span class="sxs-lookup"><span data-stu-id="83252-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="83252-164">touchpadposition. x</span><span class="sxs-lookup"><span data-stu-id="83252-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-165">Touchpad Y <i>(oben:-1,0, unten: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="83252-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="83252-166">Achse 18 \*</span><span class="sxs-lookup"><span data-stu-id="83252-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="83252-167">Achse 20 \*</span><span class="sxs-lookup"><span data-stu-id="83252-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="83252-168">touchpadposition. y</span><span class="sxs-lookup"><span data-stu-id="83252-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-169">Touchpad berührt</span><span class="sxs-lookup"><span data-stu-id="83252-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="83252-170">Schaltfläche 18 \*</span><span class="sxs-lookup"><span data-stu-id="83252-170">Button 18\*</span></span> </td><td> <span data-ttu-id="83252-171">Schaltfläche 19 \*</span><span class="sxs-lookup"><span data-stu-id="83252-171">Button 19\*</span></span> </td><td> <span data-ttu-id="83252-172">touchpadtouched</span><span class="sxs-lookup"><span data-stu-id="83252-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-173">Touchpad gedrückt</span><span class="sxs-lookup"><span data-stu-id="83252-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="83252-174">Schaltfläche 16 \*</span><span class="sxs-lookup"><span data-stu-id="83252-174">Button 16\*</span></span> </td><td> <span data-ttu-id="83252-175">Schaltfläche 17 \*</span><span class="sxs-lookup"><span data-stu-id="83252-175">Button 17\*</span></span> </td><td> <span data-ttu-id="83252-176">touchpadpressed</span><span class="sxs-lookup"><span data-stu-id="83252-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-177">6DOF-Zieh Punkt Pose oder Zeiger Pose</span><span class="sxs-lookup"><span data-stu-id="83252-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="83252-178"><i></i> Nur Ziehpunkt: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Inputtracking. getlocalposition</a></span><span class="sxs-lookup"><span data-stu-id="83252-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="83252-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Input Tracking. getlocalrotation</a></span><span class="sxs-lookup"><span data-stu-id="83252-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="83252-180">Pass <i>-</i> oder <i>Zeiger</i> als Argument: SourceState. sourcepose. trygetposition</span><span class="sxs-lookup"><span data-stu-id="83252-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="83252-181">SourceState. sourcepose. trygetrotation</span><span class="sxs-lookup"><span data-stu-id="83252-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="83252-182">Nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="83252-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="83252-183"><i>Die Positionsgenauigkeit und das Risiko von Quell Verlusten sind nur über die Mr-spezifische API verfügbar.</i> </span><span class="sxs-lookup"><span data-stu-id="83252-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="83252-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">SourceState. sourcepose. positionaccuracy</a></span><span class="sxs-lookup"><span data-stu-id="83252-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="83252-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourcelossrisk</a></span><span class="sxs-lookup"><span data-stu-id="83252-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="83252-186">Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für openvr verwendet, aufgrund von Konflikten in den von Gamepads, oculus Touchscreen und openvr verwendeten Zuordnungen.</span><span class="sxs-lookup"><span data-stu-id="83252-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

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


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="83252-187">Ziehpunkt im Vergleich zu Zeige darstellen</span><span class="sxs-lookup"><span data-stu-id="83252-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="83252-188">Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren.</span><span class="sxs-lookup"><span data-stu-id="83252-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="83252-189">Der Entwurf eines Controllers unterscheidet sich in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung, die apps zum zeigen beim Rendern des Controllers verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="83252-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="83252-190">Um diese Controller besser darzustellen, gibt es zwei Arten von Posen, die Sie für jede Interaktions Quelle untersuchen können, die Ziehpunkt- **und die** **Zeiger** Darstellung.</span><span class="sxs-lookup"><span data-stu-id="83252-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="83252-191">Sowohl die Ziehpunkt-als auch die zeigerpose-Koordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="83252-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="83252-192">Ziehpunkt darstellen</span><span class="sxs-lookup"><span data-stu-id="83252-192">Grip pose</span></span>

<span data-ttu-id="83252-193">Der Ziehpunkt stellt den Speicherort der Benutzer- **Palm dar,** der entweder von einem hololens oder einem Bewegungs Controller erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="83252-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="83252-194">Bei immersiven Headsets wird die Zieh Punkt Darstellung am besten zum Rendering **der Benutzer Hand** oder eines Objekts verwendet, das **in der Hand des Benutzers gespeichert** ist.</span><span class="sxs-lookup"><span data-stu-id="83252-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="83252-195">Die Zieh Punkt Darstellung wird auch bei der Visualisierung eines Bewegungs Controllers verwendet.</span><span class="sxs-lookup"><span data-stu-id="83252-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="83252-196">Das **zum Rendern-Modell** , das von Windows für einen Motion-Controller bereitgestellt wird, verwendet die Zieh Punkt Pose als Ursprung und Mittelpunkt der Drehung.</span><span class="sxs-lookup"><span data-stu-id="83252-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="83252-197">Die Ziehpunkt-Pose wird wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="83252-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="83252-198">Die Zieh **Punktposition**: der Palmen Schwerpunkt bei der natürlichen Aufbewahrung des Controllers, nach links oder rechts, um die Position im Ziehpunkt zu zentrieren.</span><span class="sxs-lookup"><span data-stu-id="83252-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="83252-199">Auf dem Windows Mixed Reality Motion Controller richtet sich diese Position im Allgemeinen nach der Schaltfläche "verstehen".</span><span class="sxs-lookup"><span data-stu-id="83252-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="83252-200">Die **Rechte Achse** der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist das Strahl-Ray, das normal ist (vorwärts von links nach links, rückwärts von rechter Palme).</span><span class="sxs-lookup"><span data-stu-id="83252-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="83252-201">Die **Forward-Achse** der Ziehpunkt Ausrichtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das durch ihre nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.</span><span class="sxs-lookup"><span data-stu-id="83252-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="83252-202">Die **aufwärts Achse** der Ziehpunkt Ausrichtung: die aufwärts Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.</span><span class="sxs-lookup"><span data-stu-id="83252-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="83252-203">Sie können auf die Ziehpunkt-Pose über die Anbieter übergreifende Eingabe-API von Unity (XR) zugreifen *[. Inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Getlocalposition/Rotation*) oder über die Windows-spezifische API (*SourceState. sourcepose. trygetposition/Rotation*), die die Daten für den **Zieh Knoten** anfordert.</span><span class="sxs-lookup"><span data-stu-id="83252-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="83252-204">Zeiger Pose</span><span class="sxs-lookup"><span data-stu-id="83252-204">Pointer pose</span></span>

<span data-ttu-id="83252-205">Die **Zeiger** Darstellung stellt die Spitze des Controllers dar, der vorwärts zeigt.</span><span class="sxs-lookup"><span data-stu-id="83252-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="83252-206">Die vom System bereitgestellte Zeiger Darstellung eignet sich am besten für raycast, wenn Sie **das Controller Modell selbst Rendern**.</span><span class="sxs-lookup"><span data-stu-id="83252-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="83252-207">Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers (z. b. eine virtuelle Pistole) rendern, sollten Sie auf einen Strahl zeigen, der für das virtuelle Objekt am natürlichsten ist, z. b. ein Strahl, der auf dem Barrel des App-defined Gun-Modells verläuft.</span><span class="sxs-lookup"><span data-stu-id="83252-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="83252-208">Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das verweisen mit dem virtuellen Objekt für diejenigen, die Ihre APP verwenden, wahrscheinlich natürlicher.</span><span class="sxs-lookup"><span data-stu-id="83252-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="83252-209">Derzeit ist die Zeiger Pose in Unity nur über die Windows Mr-spezifische API, *SourceState. sourcepose. trygetposition/Rotation* verfügbar, wobei *interaktionsourcenode. Pointer* als Argument übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="83252-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="83252-210">Controller nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="83252-210">Controller tracking state</span></span>

<span data-ttu-id="83252-211">Wie bei den Headsets ist für Windows Mixed Reality Motion Controller das Einrichten externer nach Verfolgungs Sensoren nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="83252-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="83252-212">Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="83252-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="83252-213">Wenn der Benutzer die Controller aus der Ansicht des Dashboards verschiebt, werden die Controller Positionen in den meisten Fällen von Windows weiter abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="83252-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="83252-214">Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.</span><span class="sxs-lookup"><span data-stu-id="83252-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="83252-215">An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="83252-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="83252-216">Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können normal funktionieren, ohne dass der Benutzer das merkt.</span><span class="sxs-lookup"><span data-stu-id="83252-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="83252-217">Die beste Möglichkeit, dies zu erreichen, besteht darin, es selbst auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="83252-217">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="83252-218">Sehen Sie sich dieses Video mit Beispielen für den immersiven Inhalt an, der mit Motion-Controllern über verschiedene Überwachungs Zustände hinweg funktioniert:</span><span class="sxs-lookup"><span data-stu-id="83252-218">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="83252-219">Grund für die explizite Nachverfolgung des Zustands</span><span class="sxs-lookup"><span data-stu-id="83252-219">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="83252-220">Apps, die Positionen basierend auf dem nach verfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und die Eigenschaften des Controller Zustands überprüfen, z. b. *sourcelossrisk* und *positionaccuracy*:</span><span class="sxs-lookup"><span data-stu-id="83252-220">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="83252-221">Nach verfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="83252-221">Tracking state</span></span> </th><th> <span data-ttu-id="83252-222">Sourcelossrisk</span><span class="sxs-lookup"><span data-stu-id="83252-222">SourceLossRisk</span></span> </th><th> <span data-ttu-id="83252-223">Positionsgenauigkeit</span><span class="sxs-lookup"><span data-stu-id="83252-223">PositionAccuracy</span></span> </th><th> <span data-ttu-id="83252-224">Trygetposition</span><span class="sxs-lookup"><span data-stu-id="83252-224">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="83252-225"><b>Hohe Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="83252-225"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="83252-226">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="83252-226">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="83252-227">High</span><span class="sxs-lookup"><span data-stu-id="83252-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="83252-228">true</span><span class="sxs-lookup"><span data-stu-id="83252-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-229"><b>Hohe Genauigkeit (Risiko eines Verlusts)</b> </span><span class="sxs-lookup"><span data-stu-id="83252-229"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="83252-230">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="83252-230">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="83252-231">High</span><span class="sxs-lookup"><span data-stu-id="83252-231">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="83252-232">true</span><span class="sxs-lookup"><span data-stu-id="83252-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-233"><b>Ungefähre Genauigkeit</b> </span><span class="sxs-lookup"><span data-stu-id="83252-233"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="83252-234">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="83252-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="83252-235">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="83252-235">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="83252-236">true</span><span class="sxs-lookup"><span data-stu-id="83252-236">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="83252-237"><b>Keine Position</b> </span><span class="sxs-lookup"><span data-stu-id="83252-237"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="83252-238">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="83252-238">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="83252-239">Ungefähr</span><span class="sxs-lookup"><span data-stu-id="83252-239">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="83252-240">false</span><span class="sxs-lookup"><span data-stu-id="83252-240">false</span></span></td>
</tr>
</table>

<span data-ttu-id="83252-241">Diese Motion Controller-Überwachungs Zustände werden wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="83252-241">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="83252-242">**Hohe Genauigkeit:** Während sich der Motion-Controller in der Ansicht des Dashboards befindet, stellt er im Allgemeinen hohe Genauigkeits Positionen auf der Grundlage der visuellen Nachverfolgung bereit.</span><span class="sxs-lookup"><span data-stu-id="83252-242">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="83252-243">Ein beweglicher Controller, der das Sichtfeld vorübergehend verlässt oder vorübergehend von den Headset-Sensoren (z. b. durch die andere Seite des Benutzers) verdeckt wird, gibt weiterhin hohe Genauigkeit für kurze Zeit zurück, basierend auf der Trägheits Verfolgung des Controllers.</span><span class="sxs-lookup"><span data-stu-id="83252-243">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="83252-244">**Hohe Genauigkeit (Risiko des Verlusts):** Wenn der Benutzer den Bewegungs Controller über den Rand des Felds der Ansicht bewegt, kann das Headset die Position des Controllers in Kürze nicht visuell nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="83252-244">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="83252-245">Die APP weiß, wann der Controller diese FOV-Grenze erreicht hat, indem er den **sourcelossrisk** -REACH-1,0 sieht.</span><span class="sxs-lookup"><span data-stu-id="83252-245">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="83252-246">An diesem Punkt kann die APP die Controller Gesten anhalten, die einen stabilen Stream von qualitativ hochwertigen Posen erfordern.</span><span class="sxs-lookup"><span data-stu-id="83252-246">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="83252-247">**Ungefähre Genauigkeit:** Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.</span><span class="sxs-lookup"><span data-stu-id="83252-247">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="83252-248">An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="83252-248">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="83252-249">Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können so normal agieren, dass Sie in der ungefähren Genauigkeit nicht bemerkt werden</span><span class="sxs-lookup"><span data-stu-id="83252-249">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="83252-250">Bei apps mit schwereren Eingabe Anforderungen ist es möglicherweise sinnvoll, diesen Löschvorgang von **hoher** Genauigkeit zur **ungefähren** Genauigkeit zu verstehen, indem die **positionaccuracy** -Eigenschaft überprüft wird, z. b. um dem Benutzer während dieses Zeitraums eine eher großzügigere Position in den offscreenzielen zu geben.</span><span class="sxs-lookup"><span data-stu-id="83252-250">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="83252-251">**Keine Position:** Wenngleich der Controller für einen längeren Zeitraum mit der ungefähren Genauigkeit arbeiten kann, weiß das System manchmal, dass auch eine durch den Text gesperrten Position nicht sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="83252-251">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="83252-252">Beispielsweise kann ein Controller, der eingeschaltet wurde, nie visuell beobachtet werden, oder ein Benutzer kann einen Controller ablegen, der dann von einer anderen Person abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="83252-252">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="83252-253">Zu diesen Zeitpunkten stellt das System keine Position für die APP bereit, und *trygetposition* gibt false zurück.</span><span class="sxs-lookup"><span data-stu-id="83252-253">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="83252-254">Allgemeine Unity-APIs (Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="83252-254">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="83252-255">**Namespace:** *unityengine*, *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="83252-255">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="83252-256">**Typen**: *Input*, *XR. Inputtracking*</span><span class="sxs-lookup"><span data-stu-id="83252-256">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="83252-257">Unity verwendet derzeit die allgemeinen *Input. getbutton/Input. getaxis-* APIs, um Eingaben für [das Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [das openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality, einschließlich der Hands-und Motion-Controller, verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="83252-257">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="83252-258">Wenn Ihre APP diese APIs für die Eingabe verwendet, kann Sie Bewegungs Controller über mehrere XR-sdche hinweg unterstützen, einschließlich Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="83252-258">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="83252-259">Der gedrückte Zustand einer logischen Schaltfläche wird erhalten.</span><span class="sxs-lookup"><span data-stu-id="83252-259">Getting a logical button's pressed state</span></span>

<span data-ttu-id="83252-260">Wenn Sie die allgemeinen Unity-Eingabe-APIs verwenden möchten, beginnen Sie in der Regel mit dem Verknüpfen von Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), und binden Sie eine Schaltfläche oder eine Achsen-ID an jeden Namen</span><span class="sxs-lookup"><span data-stu-id="83252-260">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="83252-261">Anschließend können Sie Code schreiben, der auf den Namen der logischen Schaltfläche/Achse verweist.</span><span class="sxs-lookup"><span data-stu-id="83252-261">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="83252-262">Um z. b. die triggerschaltfläche des linken Bewegungs Controllers der Aktion senden zuzuordnen, wechseln Sie zu **Edit > Project Settings > Input** in Unity, und erweitern Sie die Eigenschaften des Abschnitts übermitteln unter Achsen.</span><span class="sxs-lookup"><span data-stu-id="83252-262">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="83252-263">Ändern Sie die Schaltfläche **positiv** oder **alt positive Schaltfläche** , um die Schaltfläche "Taste **14**" wie folgt zu lesen:</span><span class="sxs-lookup"><span data-stu-id="83252-263">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="83252-264">![InputManager von Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="83252-264">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="83252-265">*Unity-InputManager*</span><span class="sxs-lookup"><span data-stu-id="83252-265">*Unity InputManager*</span></span>

<span data-ttu-id="83252-266">Das Skript kann dann mithilfe von " *Input. getbutton*" die Aktion "Senden" überprüfen:</span><span class="sxs-lookup"><span data-stu-id="83252-266">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="83252-267">Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **size** -Eigenschaft unter **Achsen** ändern.</span><span class="sxs-lookup"><span data-stu-id="83252-267">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="83252-268">Direktes drücken des gedrückten Zustands einer physischen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="83252-268">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="83252-269">Sie können mithilfe von *Input. GetKey* auch manuell mit dem voll qualifizierten Namen auf Schaltflächen zugreifen:</span><span class="sxs-lookup"><span data-stu-id="83252-269">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="83252-270">Die Pose eines Hand-oder Bewegungs Controllers</span><span class="sxs-lookup"><span data-stu-id="83252-270">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="83252-271">Sie können auf die Position und Drehung des Controllers mithilfe von *XR zugreifen. Inputtracking*:</span><span class="sxs-lookup"><span data-stu-id="83252-271">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="83252-272">Der obige Code stellt die Zieh Punktposition des Controllers dar (in der der Benutzer den Controller hält). Dies ist nützlich, um ein Schwert oder eine Waffe in der Hand des Benutzers oder ein Modell des Controllers selbst zu rendern.</span><span class="sxs-lookup"><span data-stu-id="83252-272">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="83252-273">Die Beziehung zwischen diesem Ziehpunkt und der Zeiger Pose (bei der die Spitze des Controllers zeigt) kann sich zwischen Controllern unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="83252-273">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="83252-274">Zurzeit ist der Zugriff auf die Zeiger-Pose des Controllers nur über die in den folgenden Abschnitten beschriebene Mr-spezifische Eingabe-API möglich.</span><span class="sxs-lookup"><span data-stu-id="83252-274">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="83252-275">Windows-spezifische APIs (XR. WSA. Der</span><span class="sxs-lookup"><span data-stu-id="83252-275">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="83252-276">, Wenn Ihr Projekt einen der XR-verwendet. WSA-APIs werden nach dem XR SDK in zukünftigen Unity-Releases eingestellt.</span><span class="sxs-lookup"><span data-stu-id="83252-276">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="83252-277">Für neue Projekte wird empfohlen, das XR SDK von Anfang an zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="83252-277">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="83252-278">Weitere Informationen zum [XR-Eingabe System und](https://docs.unity3d.com/Manual/xr_input.html)zu den APIs finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="83252-278">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="83252-279">**Namespace:** *unityengine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="83252-279">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="83252-280">**Typen**: *interaktionsmanager*, *interaktionsourcestate*, *interaktionsource*, *interaktionsourceproperties*, *interaktionsourcekind*, *interaktionsourcelokation*</span><span class="sxs-lookup"><span data-stu-id="83252-280">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="83252-281">Um ausführlichere Informationen zu Windows Mixed Reality-Hand Eingaben (für hololens) und Bewegungs Controller zu erhalten, können Sie die Windows-spezifischen räumlichen Eingabe-APIs im Namespace *unityengine. XR. WSA. Input* verwenden.</span><span class="sxs-lookup"><span data-stu-id="83252-281">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="83252-282">Auf diese Weise können Sie auf zusätzliche Informationen zugreifen, wie z. b. Die Positionsgenauigkeit oder die quellart, sodass Sie die Hände und Controller voneinander trennen können.</span><span class="sxs-lookup"><span data-stu-id="83252-282">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="83252-283">Abrufen des Zustands von Händen und Bewegungs Controllern</span><span class="sxs-lookup"><span data-stu-id="83252-283">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="83252-284">Sie können den Status dieses Frames für jede Interaktions Quelle (Hand-oder Bewegungs Controller) mithilfe der *getcurrentreading* -Methode abrufen.</span><span class="sxs-lookup"><span data-stu-id="83252-284">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="83252-285">Jedes *interaktionsourcestate* , das Sie zurückerhalten, stellt eine Interaktions Quelle zum aktuellen Zeitpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="83252-285">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="83252-286">Das *interaktionsourcestate* macht Informationen wie z. b.:</span><span class="sxs-lookup"><span data-stu-id="83252-286">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="83252-287">Welche [Arten von Druck](../../design/motion-controllers.md) vorgehungen werden auftreten (Select/Menu/grasp/Touchpad/Thumbstick)</span><span class="sxs-lookup"><span data-stu-id="83252-287">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="83252-288">Andere Daten, die für Bewegungs Controller spezifisch sind, z. b. die XY-Koordinaten des Touchpads und/oder Finger Ansichts Status</span><span class="sxs-lookup"><span data-stu-id="83252-288">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="83252-289">Interaktionsourcekind, um zu wissen, ob es sich bei der Quelle um einen Hand-oder Bewegungs Controller handelt</span><span class="sxs-lookup"><span data-stu-id="83252-289">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="83252-290">Abrufen von vorwärts vorhergesagten Renderingvorgängen</span><span class="sxs-lookup"><span data-stu-id="83252-290">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="83252-291">Beim Abrufen von Interaktions Quelldaten von Hand und Controllern sind die von Ihnen abzurufenden Datenquellen für den Zeitpunkt, zu dem die Daten des Bilds den Augen des Benutzers erreichen, von vorne vorhergesagte Posen.</span><span class="sxs-lookup"><span data-stu-id="83252-291">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="83252-292">Vorwärts vorhersagende Posen werden am besten zum **Rendern** des Controllers oder eines gehaltenen Objekts in jedem Frame verwendet.</span><span class="sxs-lookup"><span data-stu-id="83252-292">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="83252-293">Wenn Sie ein bestimmtes Press-oder-Release mit dem Controller als Ziel verwenden, wird dies am genauesten sein, wenn Sie die unten beschriebenen Vergangenheits Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="83252-293">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="83252-294">Sie können auch die vorwärts Gesagte Kopfzeile für diesen aktuellen Frame erhalten.</span><span class="sxs-lookup"><span data-stu-id="83252-294">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="83252-295">Wie bei der Quell Darstellung ist dies für das **Rendern** eines Cursors nützlich, obwohl das Ziel einer bestimmten Presse oder Freigabe am genauesten ist, wenn Sie die unten beschriebenen Vergangenheits Ereignis-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="83252-295">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="83252-296">Behandeln von Interaktions Quell Ereignissen</span><span class="sxs-lookup"><span data-stu-id="83252-296">Handling interaction source events</span></span>

<span data-ttu-id="83252-297">Um Eingabeereignisse zu behandeln, wie Sie mit Ihren exakten Vergangenheits Daten auftreten, können Sie Interaktions Quell Ereignisse behandeln, anstatt Sie abzufragen.</span><span class="sxs-lookup"><span data-stu-id="83252-297">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="83252-298">So behandeln Sie Interaktions Quell Ereignisse:</span><span class="sxs-lookup"><span data-stu-id="83252-298">To handle interaction source events:</span></span>
* <span data-ttu-id="83252-299">Registrieren Sie sich für ein *interaktionmanager* -Eingabe Ereignis.</span><span class="sxs-lookup"><span data-stu-id="83252-299">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="83252-300">Für jede Art von Interaktions Ereignis, für das Sie sich interessieren, müssen Sie es abonnieren.</span><span class="sxs-lookup"><span data-stu-id="83252-300">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="83252-301">Behandeln Sie das-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="83252-301">Handle the event.</span></span> <span data-ttu-id="83252-302">Wenn Sie ein Interaktions Ereignis abonniert haben, erhalten Sie gegebenenfalls den Rückruf.</span><span class="sxs-lookup"><span data-stu-id="83252-302">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="83252-303">Im Beispiel " *sourcepressed* " ist dies der Fall, nachdem die Quelle erkannt wurde und bevor Sie freigegeben oder verloren geht.</span><span class="sxs-lookup"><span data-stu-id="83252-303">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="83252-304">Beenden der Behandlung eines Ereignisses</span><span class="sxs-lookup"><span data-stu-id="83252-304">How to stop handling an event</span></span>

<span data-ttu-id="83252-305">Sie müssen die Behandlung eines Ereignisses beenden, wenn Sie nicht mehr an dem Ereignis interessiert sind oder das Objekt zerstören, das das Ereignis abonniert hat.</span><span class="sxs-lookup"><span data-stu-id="83252-305">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="83252-306">Wenn Sie die Verarbeitung des Ereignisses beenden möchten, kündigen Sie das Ereignis an.</span><span class="sxs-lookup"><span data-stu-id="83252-306">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="83252-307">Liste der Interaktions Quell Ereignisse</span><span class="sxs-lookup"><span data-stu-id="83252-307">List of interaction source events</span></span>

<span data-ttu-id="83252-308">Die folgenden Interaktions Quell Ereignisse sind verfügbar:</span><span class="sxs-lookup"><span data-stu-id="83252-308">The available interaction source events are:</span></span>
* <span data-ttu-id="83252-309">*Interaktionsourceerkannt* (Quelle wird aktiv)</span><span class="sxs-lookup"><span data-stu-id="83252-309">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="83252-310">*Interaktionsourcelost* (wird inaktiv)</span><span class="sxs-lookup"><span data-stu-id="83252-310">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="83252-311">*Interaktionsourcepressed* (tippen, drücken der Schaltfläche oder "auswählen")</span><span class="sxs-lookup"><span data-stu-id="83252-311">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="83252-312">*Interaktionsourcereleasing* (Ende einer Tap-Schaltfläche, oder Ende der "Select"-Taste)</span><span class="sxs-lookup"><span data-stu-id="83252-312">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="83252-313">*Interaktionsourceupveraltet* (verschieben oder anderweitig ändern eines Zustands)</span><span class="sxs-lookup"><span data-stu-id="83252-313">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="83252-314">Ereignisse für Vergangenheits Ziele, die mit einem Press oder Release am genauesten zu vergleichen sind</span><span class="sxs-lookup"><span data-stu-id="83252-314">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="83252-315">Die zuvor beschriebenen Abruf-APIs machen Ihre APP-vorhergesagte Posen aus.</span><span class="sxs-lookup"><span data-stu-id="83252-315">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="83252-316">Obwohl die vorhergesagten Posen am besten zum Rendern des Controllers oder eines virtuellen Hand Held Objekts geeignet sind, sind zukünftige Formen für das Ziel nicht optimal, aus zwei wichtigen Gründen:</span><span class="sxs-lookup"><span data-stu-id="83252-316">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="83252-317">Wenn der Benutzer eine Schaltfläche auf einem Controller drückt, kann es ungefähr 20 ms drahtlose Latenz über Bluetooth geben, bevor das System den Druck erhält.</span><span class="sxs-lookup"><span data-stu-id="83252-317">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="83252-318">Wenn Sie dann eine vorwärts Gesagte Pose verwenden, gibt es eine weitere 10-20 MS der Forward-Vorhersage, auf die die Uhrzeit angewendet wird, zu der die Daten des aktuellen Frames die Augen des Benutzers erreichen.</span><span class="sxs-lookup"><span data-stu-id="83252-318">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="83252-319">Dies bedeutet, dass bei der Abfrage eine Quell Pose oder eine Kopfzeile angezeigt wird, die 30-40 ms vorwärts ist, von wo aus die Kopfzeile des Benutzers und die Hände wieder zurück waren, als die Taste oder das Release aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="83252-319">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="83252-320">Bei der Eingabe von hololens-Hand Eingaben gibt es eine ähnliche Verarbeitungs Verzögerung, um den Druck zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="83252-320">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="83252-321">Um basierend auf der ursprünglichen Absicht des Benutzers für eine Hand oder einen Controller eine genaue Zielsetzung zu erreichen, sollten Sie die historische Quell Pose oder die Kopfzeile aus dem *interaktionsourcepressed* -oder *interaktionsourcereleasing* -Eingabe Ereignis verwenden.</span><span class="sxs-lookup"><span data-stu-id="83252-321">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="83252-322">Sie können eine Presse oder eine Freigabe mit Verlaufs Daten des Benutzers oder des Controllers als Ziel haben:</span><span class="sxs-lookup"><span data-stu-id="83252-322">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="83252-323">Die Kopfzeile zu dem Zeitpunkt, an dem eine Geste oder eine Controller Bewegung aufgetreten ist, die für die **Ziel** Bestimmung verwendet werden kann, um zu bestimmen, was der [Benutzer untersucht hat:](../../design/gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="83252-323">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="83252-324">Die Quell Pose zu dem Zeitpunkt, zu dem eine Bewegung des Bewegungs Controllers stattgefunden hat. diese kann verwendet werden, **um zu bestimmen** , auf welche Weise der Benutzer den Controller verwiesen hat.</span><span class="sxs-lookup"><span data-stu-id="83252-324">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="83252-325">Dabei handelt es sich um den Zustand des Controllers, der den Druck erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="83252-325">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="83252-326">Wenn Sie den Controller selbst rendern, können Sie die Zeiger Darstellung anstelle der Ziehpunkt-Pose anfordern, um das Ziel-Ray von dem zu überprüfen, was der Benutzer für den natürlichen Tipp des gerenderten Controllers in Erwägung zieht:</span><span class="sxs-lookup"><span data-stu-id="83252-326">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="83252-327">Beispiel für Ereignishandler</span><span class="sxs-lookup"><span data-stu-id="83252-327">Event handlers example</span></span>

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

## <a name="motion-controllers-in-mrtk-v2"></a><span data-ttu-id="83252-328">Motion-Controller in mrtk v2</span><span class="sxs-lookup"><span data-stu-id="83252-328">Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="83252-329">Sie können über den Eingabe-Manager auf [Gesten-und Bewegungs Controller](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) zugreifen.</span><span class="sxs-lookup"><span data-stu-id="83252-329">You can access [gesture and motion controller](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="83252-330">Immer am Ball mit Tutorials</span><span class="sxs-lookup"><span data-stu-id="83252-330">Follow along with tutorials</span></span>

<span data-ttu-id="83252-331">Schritt-für-Schritt-Tutorials mit ausführlicheren Anpassungs Beispielen sind in der Mixed Reality Academy verfügbar:</span><span class="sxs-lookup"><span data-stu-id="83252-331">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="83252-332">MR-Eingabe 211: Geste</span><span class="sxs-lookup"><span data-stu-id="83252-332">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="83252-333">MR-Eingabe 213: Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="83252-333">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="83252-334">[![Mr-Eingabe 213-Motion Controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="83252-334">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="83252-335">*Mr-Eingabe 213-Motion Controller*</span><span class="sxs-lookup"><span data-stu-id="83252-335">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="83252-336">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="83252-336">Next Development Checkpoint</span></span>

<span data-ttu-id="83252-337">Wenn Sie der Unity-Entwicklungs Journey folgen, die wir angelegt haben, befinden Sie sich mitten in der Untersuchung der mrtk Core-Bausteine.</span><span class="sxs-lookup"><span data-stu-id="83252-337">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="83252-338">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="83252-338">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="83252-339">Hand- und Eye-Tracking</span><span class="sxs-lookup"><span data-stu-id="83252-339">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="83252-340">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="83252-340">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="83252-341">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="83252-341">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="83252-342">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="83252-342">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="83252-343">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="83252-343">See also</span></span>

* [<span data-ttu-id="83252-344">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="83252-344">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="83252-345">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="83252-345">Motion controllers</span></span>](../../design/motion-controllers.md)