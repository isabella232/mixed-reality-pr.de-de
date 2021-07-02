---
title: Verwenden von Leap Motion
description: Dokumentation zum Konfigurieren für Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Leap Motion,
ms.openlocfilehash: 3ddf039f8409022d8aa2e425c46cd4d47ede16a0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176508"
---
# <a name="using-leap-motion"></a><span data-ttu-id="1898d-104">Verwenden von Leap Motion</span><span class="sxs-lookup"><span data-stu-id="1898d-104">Using Leap Motion</span></span>

<span data-ttu-id="1898d-105">Für [die Verwendung dieses Datenanbieters](https://www.ultraleap.com/product/leap-motion-controller/) ist ein Leap Motion Controller erforderlich.</span><span class="sxs-lookup"><span data-stu-id="1898d-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="1898d-106">Der Leap Motion Datenanbieter ermöglicht die artikulierte Handverfolgung für VR und kann für die schnelle Prototyperstellung im Editor nützlich sein.</span><span class="sxs-lookup"><span data-stu-id="1898d-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="1898d-107">Der Datenanbieter kann so konfiguriert werden, dass er den Leap Motion Controller verwendet, der auf einem Headset oder auf einer Desk-Gesichtserkennung installiert ist.</span><span class="sxs-lookup"><span data-stu-id="1898d-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="1898d-109">Dieser Anbieter kann im Editor und auf dem Gerät auf der eigenständigen Plattform verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1898d-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="1898d-110">Sie kann auch im Editor auf der UWP-Plattform, aber NICHT in einem UWP-Build verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1898d-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="1898d-111">MRTK-Version</span><span class="sxs-lookup"><span data-stu-id="1898d-111">MRTK Version</span></span> | <span data-ttu-id="1898d-112">Unterstützte Leap Motion Unity-Modulversionen</span><span class="sxs-lookup"><span data-stu-id="1898d-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="1898d-113">2.6.x</span><span class="sxs-lookup"><span data-stu-id="1898d-113">2.6.x</span></span> | <span data-ttu-id="1898d-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="1898d-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="1898d-115">2.7.x</span><span class="sxs-lookup"><span data-stu-id="1898d-115">2.7.x</span></span>| <span data-ttu-id="1898d-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span><span class="sxs-lookup"><span data-stu-id="1898d-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="1898d-117">Verwenden der Handnachverfolgung von Leap Motion (von Ultraleap) in MRTK</span><span class="sxs-lookup"><span data-stu-id="1898d-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="1898d-118">Importieren von MRTK und unity-Modulen für Leap Motion</span><span class="sxs-lookup"><span data-stu-id="1898d-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="1898d-119">Installieren Sie das neueste [Leap Motion SDK,](https://developer.leapmotion.com/releases/?category=orion) falls es noch nicht installiert ist.</span><span class="sxs-lookup"><span data-stu-id="1898d-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="1898d-120">Importieren Sie **das Paket Microsoft.MixedReality.Toolkit.Foundation** in das Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="1898d-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="1898d-121">Laden Sie die neueste Version der [Leap Motion Unity-Module](https://developer.leapmotion.com/unity) herunter, und importieren Sie sie in das Projekt.</span><span class="sxs-lookup"><span data-stu-id="1898d-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="1898d-122">Importieren Sie nur das **Core-Paket** innerhalb der Unity-Module.</span><span class="sxs-lookup"><span data-stu-id="1898d-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="1898d-123">Integrieren der Leap Motion Unity-Module in MRTK</span><span class="sxs-lookup"><span data-stu-id="1898d-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="1898d-124">Nachdem sich die Unity-Module im Projekt befinden, navigieren Sie zu Mixed Reality **Toolkit**  >  **Leap Motion** Integrate Leap Motion Unity  >  **Modules**</span><span class="sxs-lookup"><span data-stu-id="1898d-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="1898d-125">Durch die Integration der Unity-Module in MRTK werden dem Projekt 10 Assemblydefinitionen und Verweise auf die **Assemblydefinition Microsoft.MixedReality.Toolkit.Providers.LeapMotion** hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="1898d-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="1898d-126">Vergewissern Sie sich, dass Visual Studio geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="1898d-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="1898d-128">Hinzufügen des Leap Motion-Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="1898d-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="1898d-129">Erstellen einer neuen Unity-Szene</span><span class="sxs-lookup"><span data-stu-id="1898d-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="1898d-130">Fügen Sie der Szene MRTK hinzu, indem Sie zu Mixed Reality **Toolkit**  >  **Hinzufügen zur Szene und Konfigurieren navigieren.**</span><span class="sxs-lookup"><span data-stu-id="1898d-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="1898d-131">Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen Sie Kopieren und **Anpassen aus,** um das Mixed Reality-Standardprofil zu klonen.</span><span class="sxs-lookup"><span data-stu-id="1898d-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="1898d-133">Auswählen des **Eingabekonfigurationsprofils**</span><span class="sxs-lookup"><span data-stu-id="1898d-133">Select the **Input** Configuration Profile</span></span>

    ![Eingabekonfigurationsprofil 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="1898d-135">Wählen **Sie im** Eingabesystemprofil Klonen aus, um die Änderung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="1898d-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="1898d-137">Öffnen Sie **den Abschnitt Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** Hinzufügen aus. Am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="1898d-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="1898d-138">Öffnen Sie den neuen Datenanbieter, und legen Sie **type** auf **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager fest.**</span><span class="sxs-lookup"><span data-stu-id="1898d-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Add Datenanbieter](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="1898d-140">Wählen Sie **Klonen** aus, um die Standardeinstellungen für Leap Motion zu ändern.</span><span class="sxs-lookup"><span data-stu-id="1898d-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="1898d-142">Der Leap Motion Datenanbieter enthält die `LeapControllerOrientation` -Eigenschaft, die die Position des Leap Motion-Controllers ist.</span><span class="sxs-lookup"><span data-stu-id="1898d-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="1898d-143">`LeapControllerOrientation.Headset` gibt an, dass der Controller auf einem Headset bereitgestellt ist.</span><span class="sxs-lookup"><span data-stu-id="1898d-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="1898d-144">`LeapControllerOrientation.Desk` gibt an, dass der Controller flach auf dem Desk platziert ist.</span><span class="sxs-lookup"><span data-stu-id="1898d-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="1898d-145">Der Standardwert ist auf `LeapControllerOrientation.Headset` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1898d-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="1898d-146">Jede Controllerausrichtung enthält Offseteigenschaften:</span><span class="sxs-lookup"><span data-stu-id="1898d-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="1898d-147">Die  Headset-Ausrichtungsoffseteigenschaften spiegeln die Offseteigenschaften in der LeapXRServiceProvider-Komponente wieder.</span><span class="sxs-lookup"><span data-stu-id="1898d-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="1898d-148">Die `LeapVRDeviceOffsetMode` verfügt über drei Optionen: Standard, Manueller Kopfoffset und Transformation.</span><span class="sxs-lookup"><span data-stu-id="1898d-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="1898d-149">Wenn der Offsetmodus Standard ist, wird kein Offset auf den Leap Motion Controller angewendet.</span><span class="sxs-lookup"><span data-stu-id="1898d-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="1898d-150">Der Modus "Manueller Kopfoffset" ermöglicht die Änderung von drei Eigenschaften: `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` und `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="1898d-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="1898d-151">Die Eigenschaftswerte des Achsenoffsets werden dann auf die Standardplatzierung des Controllers angewendet.</span><span class="sxs-lookup"><span data-stu-id="1898d-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="1898d-152">Der Transformationsoffsetmodus enthält die `LeapVRDeviceOrigin` Transform-Eigenschaft, die einen neuen Ursprung für den Leap Motion Controller angibt.</span><span class="sxs-lookup"><span data-stu-id="1898d-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="1898d-153">Die **Desk-Ausrichtung** enthält die `LeapControllerOffset` -Eigenschaft, die die Ankerposition der Schaltersprunghands definiert.</span><span class="sxs-lookup"><span data-stu-id="1898d-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="1898d-154">Der Offset wird relativ zur Hauptkameraposition berechnet, und der Standardwert ist (0,-0,2, 0,35), um sicherzustellen, dass die Hände vor und in der Ansicht der Kamera angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1898d-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="1898d-155">Die Offseteigenschaften im Profil werden einmal angewendet, wenn die Anwendung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="1898d-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="1898d-156">Um die Werte während der Laufzeit zu ändern, können Sie den Leap Motion Service Provider aus dem Leap Motion-Geräte-Manager:</span><span class="sxs-lookup"><span data-stu-id="1898d-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="1898d-157">`EnterPinchDistance` und `ExitPinchDistance` sind die Entfernungsschwellenwerte für die Erkennung von Pinch-/Air-Tippbewegungen.</span><span class="sxs-lookup"><span data-stu-id="1898d-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="1898d-158">Die Heftbewegung wird berechnet, indem der Abstand zwischen der Zeigefingerspitze und der Daumenspitze gemessen wird.</span><span class="sxs-lookup"><span data-stu-id="1898d-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="1898d-159">Der Standardwert ist auf 0,02 festgelegt, um ein -Ereignis bei der Eingabe nach `EnterPinchDistance` unten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1898d-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="1898d-160">Der Standardabstand zwischen der Zeigefingerspitze und der Daumenspitze beträgt 0,05, um ein Beim-Eingabe-Nach-oben-Ereignis (beenden des Heftes) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1898d-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="1898d-161">`LeapControllerOrientation`: Headset (Standard)</span><span class="sxs-lookup"><span data-stu-id="1898d-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="1898d-162">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="1898d-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="1898d-167">Testen des Leap Motion Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="1898d-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="1898d-168">Nachdem Leap Motion Datenanbieter dem Eingabesystemprofil hinzugefügt wurde, drücken Sie die Wiedergabe, bewegen Sie Ihre Hand vor dem Leap Motion Controller, und Sie sollten die gemeinsame Darstellung der Hand sehen.</span><span class="sxs-lookup"><span data-stu-id="1898d-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="1898d-169">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="1898d-169">Building your project</span></span>
    - <span data-ttu-id="1898d-170">Navigieren Sie **zu Datei > Build Einstellungen**</span><span class="sxs-lookup"><span data-stu-id="1898d-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="1898d-171">Nur eigenständige Builds werden unterstützt, wenn die Leap Motion-Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="1898d-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="1898d-172">Anweisungen zur Verwendung eines Windows Mixed Reality-Headsets für eigenständige Builds finden Sie unter [Building and deploying MRTK to WMR Headsets (Standalone) (Erstellen und Bereitstellen von MRTK für WMR-Headsets (eigenständig)).](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)</span><span class="sxs-lookup"><span data-stu-id="1898d-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK to WMR Headsets (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="1898d-173">Abrufen der Handgelenke</span><span class="sxs-lookup"><span data-stu-id="1898d-173">Getting the hand joints</span></span>

<span data-ttu-id="1898d-174">Das Abrufen von Fugen mithilfe Datenanbieter Leap Motion ist identisch mit dem Handknüpfabruf für eine MRTK-Artikulierte Hand.</span><span class="sxs-lookup"><span data-stu-id="1898d-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="1898d-175">Weitere Informationen finden Sie unter [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="1898d-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="1898d-176">Erstellen Sie mit DEM MRTK in einer Unity-Szene und dem Leap Motion-Datenanbieter, das als Eingabe-Datenanbieter im Eingabesystemprofil hinzugefügt wurde, ein leeres Spielobjekt, und fügen Sie das folgende Beispielskript an.</span><span class="sxs-lookup"><span data-stu-id="1898d-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="1898d-177">Dieses Skript ist ein einfaches Beispiel dafür, wie sie die Pose des Handgelenks in einer Leap Motion Hand abrufen.</span><span class="sxs-lookup"><span data-stu-id="1898d-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="1898d-178">Eine Kugel folgt der linken Leap-Hand, während ein Würfel der rechten Leap-Hand folgt.</span><span class="sxs-lookup"><span data-stu-id="1898d-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="1898d-179">Workflowtipp für den Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="1898d-179">Unity editor workflow tip</span></span>

<span data-ttu-id="1898d-180">Die Verwendung des Leap Motion Datenanbieter erfordert kein VR-Headset.</span><span class="sxs-lookup"><span data-stu-id="1898d-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="1898d-181">Änderungen an einer MRTK-App können im Editor mit den Leap-Händen ohne Headset getestet werden.</span><span class="sxs-lookup"><span data-stu-id="1898d-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="1898d-182">Die Leap Motion Hands werden im Editor angezeigt, ohne dass ein VR-Headset angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="1898d-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="1898d-183">Wenn der auf Headset festgelegt ist, muss der Leap Motion-Controller um eine Hand mit der nach vorn gerichteten `LeapControllerOrientation` Kamera gehalten werden. </span><span class="sxs-lookup"><span data-stu-id="1898d-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="1898d-184">Wenn die Kamera mithilfe von WASD-Tasten im Editor bewegt wird und headset ist, folgen die Hände `LeapControllerOrientation` nicht der Kamera. </span><span class="sxs-lookup"><span data-stu-id="1898d-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="1898d-185">Die Hände folgen nur der Kamerabewegung, wenn ein VR-Headset angeschlossen ist, während `LeapControllerOrientation` das **Headset festgelegt ist.**</span><span class="sxs-lookup"><span data-stu-id="1898d-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="1898d-186">Die Leap-Hände folgen der Kamerabewegung im Editor, wenn `LeapControllerOrientation` auf **Desk festgelegt ist.**</span><span class="sxs-lookup"><span data-stu-id="1898d-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="1898d-187">Entfernen von Leap Motion aus Project</span><span class="sxs-lookup"><span data-stu-id="1898d-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="1898d-188">Navigieren Sie zu den **Mixed Reality Toolkit**  >  **Leap Motion** Separate Leap Motion Unity  >  **Modules**</span><span class="sxs-lookup"><span data-stu-id="1898d-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="1898d-189">Lassen Sie Unity aktualisieren, wenn Verweise in der **Datei Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** in diesem Schritt geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1898d-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="1898d-190">Schließen von Unity</span><span class="sxs-lookup"><span data-stu-id="1898d-190">Close Unity</span></span>
1. <span data-ttu-id="1898d-191">Schließen Visual Studio, wenn es geöffnet ist</span><span class="sxs-lookup"><span data-stu-id="1898d-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="1898d-192">Öffnen Sie den Datei-Explorer, und navigieren Sie zum Stamm des MRTK-Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="1898d-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="1898d-193">Löschen des **Verzeichnisses UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="1898d-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="1898d-194">Löschen des **Verzeichnisses UnityProjectName/Assets/Plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="1898d-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="1898d-195">Löschen Sie die **Datei UnityProjectName/Assets/Plugins/LeapMotion.meta.**</span><span class="sxs-lookup"><span data-stu-id="1898d-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="1898d-196">Unity erneut öffnen</span><span class="sxs-lookup"><span data-stu-id="1898d-196">Reopen Unity</span></span>

<span data-ttu-id="1898d-197">In Unity 2018.4 werden Sie möglicherweise feststellen, dass nach dem Löschen der Bibliothek und der Leap Motion Core-Objekte weiterhin Fehler in der Konsole verbleiben.</span><span class="sxs-lookup"><span data-stu-id="1898d-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="1898d-198">Wenn Fehler nach dem erneuten Öffnen protokolliert werden, starten Sie Unity erneut.</span><span class="sxs-lookup"><span data-stu-id="1898d-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="1898d-199">Häufige Fehler</span><span class="sxs-lookup"><span data-stu-id="1898d-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="1898d-200">Leap Motion ist nicht in MRTK integriert</span><span class="sxs-lookup"><span data-stu-id="1898d-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="1898d-201">So testen Sie, ob die Leap Motion Unity-Module in MRTK integriert wurden:</span><span class="sxs-lookup"><span data-stu-id="1898d-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="1898d-202">Navigieren Sie zu **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status (Integrationsstatus überprüfen).**</span><span class="sxs-lookup"><span data-stu-id="1898d-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="1898d-203">Dadurch wird ein Popupfenster mit einer Meldung angezeigt, ob die Leap Motion Unity-Module in MRTK integriert wurden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="1898d-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="1898d-204">Wenn die Meldung besagt, dass die Objekte nicht integriert wurden:</span><span class="sxs-lookup"><span data-stu-id="1898d-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="1898d-205">Stellen Sie sicher, dass sich die Leap Motion Unity-Module im Projekt befinden.</span><span class="sxs-lookup"><span data-stu-id="1898d-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="1898d-206">Stellen Sie sicher, dass die hinzugefügte Version unterstützt wird. Informationen zu unterstützten Versionen finden Sie in der Tabelle oben auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="1898d-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="1898d-207">Probieren Sie **Mixed Reality Toolkit > Utilities > Leap Motion > Integrieren von Leap Motion Unity-Modulen** aus.</span><span class="sxs-lookup"><span data-stu-id="1898d-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="1898d-208">Fehler beim Kopieren der Multiplayer-HLAPI-Assembly</span><span class="sxs-lookup"><span data-stu-id="1898d-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="1898d-209">Beim Importieren der Leap Motion Unity Core Assets kann dieser Fehler protokolliert werden:</span><span class="sxs-lookup"><span data-stu-id="1898d-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="1898d-210">**Lösung**</span><span class="sxs-lookup"><span data-stu-id="1898d-210">**Solution**</span></span>

- <span data-ttu-id="1898d-211">Eine kurzfristige Lösung besteht darin, Unity neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="1898d-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="1898d-212">Weitere Informationen finden Sie unter [Problem 7761.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761)</span><span class="sxs-lookup"><span data-stu-id="1898d-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="1898d-213">Leap Motion-Beispielszene</span><span class="sxs-lookup"><span data-stu-id="1898d-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="1898d-214">Die Beispielszene verwendet das Profil DefaultLeapMotionConfiguration und bestimmt, ob das Unity-Projekt ordnungsgemäß für die Verwendung des Leap Motion-Datenanbieter konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="1898d-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="1898d-215">Die Beispielszene ist im Paket **Microsoft.MixedReality.Toolkit.Examples** im Verzeichnis **MRTK/Examples/Demos/HandTracking/** enthalten.</span><span class="sxs-lookup"><span data-stu-id="1898d-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="1898d-216">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1898d-216">See also</span></span>

- [<span data-ttu-id="1898d-217">Eingabeanbieter</span><span class="sxs-lookup"><span data-stu-id="1898d-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="1898d-218">Handtracking</span><span class="sxs-lookup"><span data-stu-id="1898d-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
