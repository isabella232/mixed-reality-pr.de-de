---
title: Leap Motion MRTK
description: Dokumentation zum Konfigurieren von Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Leap Motion,
ms.openlocfilehash: 285328b1248f04504f30192f1294e9ae665b3fc9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145196"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="4d577-104">Konfigurieren der Handnachverfolgung von Leap Motion (von Ultraleap) im MRTK</span><span class="sxs-lookup"><span data-stu-id="4d577-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="4d577-105">Ein [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) ist erforderlich, um diesen Datenanbieter zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4d577-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="4d577-106">Die Leap Motion Datenanbieter ermöglicht die artikulierte Handverfolgung für VR und kann für schnelle Prototyperstellung im Editor nützlich sein.</span><span class="sxs-lookup"><span data-stu-id="4d577-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="4d577-107">Der Datenanbieter kann so konfiguriert werden, dass er den Leap Motion Controller verwendet, der auf einem Headset oder auf einem Tisch angeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="4d577-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="4d577-109">Dieser Anbieter kann im Editor und auf dem Gerät auf der eigenständigen Plattform verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4d577-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="4d577-110">Sie kann auch im Editor auf der UWP-Plattform, aber NICHT in einem UWP-Build verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4d577-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

|<span data-ttu-id="4d577-111">Unterstützte Leap Motion Unity-Modulversionen</span><span class="sxs-lookup"><span data-stu-id="4d577-111">Leap Motion Unity Modules Versions Supported</span></span>|
|---|
|<span data-ttu-id="4d577-112">4.5.0</span><span class="sxs-lookup"><span data-stu-id="4d577-112">4.5.0</span></span>|
|<span data-ttu-id="4d577-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="4d577-113">4.5.1</span></span>|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="4d577-114">Verwenden der Handnachverfolgung von Leap Motion (von Ultraleap) im MRTK</span><span class="sxs-lookup"><span data-stu-id="4d577-114">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="4d577-115">Importieren von MRTK und den Leap Motion Unity-Modulen</span><span class="sxs-lookup"><span data-stu-id="4d577-115">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="4d577-116">Installieren Sie das [Leap Motion SDK 4.0.0,](https://developer.leapmotion.com/releases/?category=orion) wenn es noch nicht installiert ist.</span><span class="sxs-lookup"><span data-stu-id="4d577-116">Install the [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="4d577-117">Importieren Sie das **Paket Microsoft.MixedReality.Toolkit.Foundation** in das Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="4d577-117">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="4d577-118">Laden Sie die neueste Version der [Leap Motion Unity-Module](https://developer.leapmotion.com/unity) herunter, und importieren Sie sie in das Projekt.</span><span class="sxs-lookup"><span data-stu-id="4d577-118">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="4d577-119">Importieren Sie nur das **Core-Paket** innerhalb der Unity-Module.</span><span class="sxs-lookup"><span data-stu-id="4d577-119">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="4d577-120">Integrieren der Leap Motion Unity-Module in MRTK</span><span class="sxs-lookup"><span data-stu-id="4d577-120">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="4d577-121">Nachdem sich die Unity-Module im Projekt befinden, navigieren Sie zu **Mixed Reality Toolkit**  >  **Leap Motion** Integrate Leap Motion Unity  >  **Modules**</span><span class="sxs-lookup"><span data-stu-id="4d577-121">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="4d577-122">Durch die Integration der Unity-Module in MRTK werden dem Projekt 10 Assemblydefinitionen und Verweise auf die **Assemblydefinition Microsoft.MixedReality.Toolkit.Providers.LeapMotion** hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4d577-122">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="4d577-123">Vergewissern Sie sich, dass Visual Studio geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="4d577-123">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="4d577-125">Hinzufügen des Leap Motion-Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="4d577-125">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="4d577-126">Erstellen einer neuen Unity-Szene</span><span class="sxs-lookup"><span data-stu-id="4d577-126">Create a new Unity scene</span></span>
    - <span data-ttu-id="4d577-127">Fügen Sie der Szene MRTK hinzu, indem Sie zu Mixed Reality **Toolkit**  >  **Hinzufügen zur Szene und Konfigurieren navigieren.**</span><span class="sxs-lookup"><span data-stu-id="4d577-127">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="4d577-128">Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen Sie Kopieren und **Anpassen aus,** um das Mixed Reality-Standardprofil zu klonen.</span><span class="sxs-lookup"><span data-stu-id="4d577-128">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="4d577-130">Auswählen des **Eingabekonfigurationsprofils**</span><span class="sxs-lookup"><span data-stu-id="4d577-130">Select the **Input** Configuration Profile</span></span>

    ![Eingabekonfigurationsprofil 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="4d577-132">Wählen **Sie im** Eingabesystemprofil Klonen aus, um die Änderung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4d577-132">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="4d577-134">Öffnen Sie den Abschnitt  **Eingabedatenanbieter,** und wählen Datenanbieter oben hinzufügen aus. Am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4d577-134">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="4d577-135">Öffnen Sie den neuen Datenanbieter, und legen Sie **type** auf **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager fest.**</span><span class="sxs-lookup"><span data-stu-id="4d577-135">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Add Datenanbieter](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="4d577-137">Wählen Sie **Klonen** aus, um die Standardeinstellungen für Leap Motion zu ändern.</span><span class="sxs-lookup"><span data-stu-id="4d577-137">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="4d577-139">Der Leap Motion Datenanbieter enthält die `LeapControllerOrientation` -Eigenschaft, die die Position des Leap Motion-Controllers ist.</span><span class="sxs-lookup"><span data-stu-id="4d577-139">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="4d577-140">`LeapControllerOrientation.Headset` gibt an, dass der Controller auf einem Headset bereitgestellt ist.</span><span class="sxs-lookup"><span data-stu-id="4d577-140">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="4d577-141">`LeapControllerOrientation.Desk` gibt an, dass der Controller flach auf dem Desk platziert ist.</span><span class="sxs-lookup"><span data-stu-id="4d577-141">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="4d577-142">Der Standardwert ist auf `LeapControllerOrientation.Headset` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="4d577-142">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="4d577-143">Jede Controllerausrichtung enthält Offseteigenschaften:</span><span class="sxs-lookup"><span data-stu-id="4d577-143">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="4d577-144">Die  Headset-Ausrichtungsoffseteigenschaften spiegeln die Offseteigenschaften in der LeapXRServiceProvider-Komponente wieder.</span><span class="sxs-lookup"><span data-stu-id="4d577-144">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="4d577-145">Verfügt über `LeapVRDeviceOffsetMode` drei Optionen: Standard, Manueller Kopfoffset und Transformation.</span><span class="sxs-lookup"><span data-stu-id="4d577-145">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="4d577-146">Wenn der Offsetmodus Standard ist, wird kein Offset auf den Schaltbewegungscontroller angewendet.</span><span class="sxs-lookup"><span data-stu-id="4d577-146">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="4d577-147">Der Modus Manueller Kopfoffset ermöglicht die Änderung von drei Eigenschaften: `LeapVRDeviceOffsetY` `LeapVRDeviceOffsetZ` und `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="4d577-147">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="4d577-148">Die Achsenoffset-Eigenschaftswerte werden dann auf die Standardcontrollerplatzierung angewendet.</span><span class="sxs-lookup"><span data-stu-id="4d577-148">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="4d577-149">Der Transformationsoffsetmodus enthält die `LeapVRDeviceOrigin` Transform-Eigenschaft, die einen neuen Ursprung für den Leap Motion Controller angibt.</span><span class="sxs-lookup"><span data-stu-id="4d577-149">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="4d577-150">Die **Desk-Ausrichtung** enthält die `LeapControllerOffset` -Eigenschaft, die die Ankerposition der Schalthand des Desks definiert.</span><span class="sxs-lookup"><span data-stu-id="4d577-150">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="4d577-151">Der Offset wird relativ zur Hauptkameraposition berechnet, und der Standardwert ist (0,-0,2, 0,35), um sicherzustellen, dass die Hände vor und in der Kamera angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4d577-151">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="4d577-152">Die Offseteigenschaften im Profil werden einmal angewendet, wenn die Anwendung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="4d577-152">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="4d577-153">Um die Werte während der Laufzeit zu ändern, erhalten Sie den Leap Motion Service Provider aus der Leap Motion Geräte-Manager:</span><span class="sxs-lookup"><span data-stu-id="4d577-153">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="4d577-154">`EnterPinchDistance` und `ExitPinchDistance` sind die Entfernungsschwellenwerte für die Gestenerkennung durch Tippen/Tippen in die Luft.</span><span class="sxs-lookup"><span data-stu-id="4d577-154">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="4d577-155">Die Zusammendrückbewegung wird berechnet, indem der Abstand zwischen der Zeigefingerspitze und der Daumenspitze gemessen wird.</span><span class="sxs-lookup"><span data-stu-id="4d577-155">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="4d577-156">Zum Auslösen eines Bei Eingabe-Down-Ereignisses wird der Standardwert `EnterPinchDistance` auf 0,02 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="4d577-156">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="4d577-157">Zum Auslösen eines Eingabe-Up-Ereignisses (zum Beenden des Zusammendrückens) beträgt der Standardabstand zwischen der Zeigefingerspitze und der Daumenspitze 0,05.</span><span class="sxs-lookup"><span data-stu-id="4d577-157">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="4d577-158">`LeapControllerOrientation`: Headset (Standard)</span><span class="sxs-lookup"><span data-stu-id="4d577-158">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="4d577-159">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="4d577-159">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="4d577-164">Testen der Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="4d577-164">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="4d577-165">Nachdem Leap Motion Datenanbieter dem Eingabesystemprofil hinzugefügt wurde, drücken Sie die Wiedergabe, bewegen Sie Ihre Hand vor dem Leap Motion Controller, und Sie sollten die gemeinsame Darstellung der Hand sehen.</span><span class="sxs-lookup"><span data-stu-id="4d577-165">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="4d577-166">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="4d577-166">Building your project</span></span>
    - <span data-ttu-id="4d577-167">Navigieren Sie **zu Datei- > Buildeinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="4d577-167">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="4d577-168">Nur eigenständige Builds werden unterstützt, wenn die Leap Motion-Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="4d577-168">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="4d577-169">Anweisungen zur Verwendung eines Windows Mixed Reality-Headsets für eigenständige Builds finden Sie unter Erstellen und Bereitstellen [von MRTK (eigenständig).](wmr-mrtk.md#building-and-deploying-mrtk-standalone)</span><span class="sxs-lookup"><span data-stu-id="4d577-169">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="4d577-170">Abrufen der Handgelenke</span><span class="sxs-lookup"><span data-stu-id="4d577-170">Getting the hand joints</span></span>

<span data-ttu-id="4d577-171">Das Abrufen von Fugen mithilfe Datenanbieter Leap Motion ist identisch mit dem Handknüpfabruf für eine MRTK-Artikulierte Hand.</span><span class="sxs-lookup"><span data-stu-id="4d577-171">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="4d577-172">Weitere Informationen finden Sie unter [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="4d577-172">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="4d577-173">Erstellen Sie mit MRTK in einer Unity-Szene und dem Leap Motion-Datenanbieter, das als Eingabe-Datenanbieter im Eingabesystemprofil hinzugefügt wurde, ein leeres Spielobjekt, und fügen Sie das folgende Beispielskript an.</span><span class="sxs-lookup"><span data-stu-id="4d577-173">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="4d577-174">Dieses Skript ist ein einfaches Beispiel dafür, wie die Pose des Handgelenks in einer Leap Motion Hand abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="4d577-174">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="4d577-175">Eine Kugel folgt der linken Leap-Hand, während ein Würfel der rechten Leap-Hand folgt.</span><span class="sxs-lookup"><span data-stu-id="4d577-175">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="4d577-176">Workflowtipp für den Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="4d577-176">Unity editor workflow tip</span></span>

<span data-ttu-id="4d577-177">Die Verwendung des Leap Motion Datenanbieter erfordert kein VR-Headset.</span><span class="sxs-lookup"><span data-stu-id="4d577-177">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="4d577-178">Änderungen an einer MRTK-App können im Editor mit den Leap-Händen ohne Headset getestet werden.</span><span class="sxs-lookup"><span data-stu-id="4d577-178">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="4d577-179">Die Leap Motion Hands werden im Editor angezeigt, ohne dass ein VR-Headset angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="4d577-179">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="4d577-180">Wenn der auf Headset festgelegt ist, muss der Leap Motion-Controller um eine Hand mit der nach vorn gerichteten `LeapControllerOrientation` Kamera gehalten werden. </span><span class="sxs-lookup"><span data-stu-id="4d577-180">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="4d577-181">Wenn die Kamera mithilfe von WASD-Tasten im Editor bewegt wird und headset ist, folgen die Hände `LeapControllerOrientation` nicht der Kamera. </span><span class="sxs-lookup"><span data-stu-id="4d577-181">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="4d577-182">Die Hände folgen nur der Kamerabewegung, wenn ein VR-Headset angeschlossen ist, während `LeapControllerOrientation` das **Headset festgelegt ist.**</span><span class="sxs-lookup"><span data-stu-id="4d577-182">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="4d577-183">Die Leap-Hände folgen der Kamerabewegung im Editor, wenn `LeapControllerOrientation` auf **Desk festgelegt ist.**</span><span class="sxs-lookup"><span data-stu-id="4d577-183">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="4d577-184">Entfernen von Leap Motion aus dem Projekt</span><span class="sxs-lookup"><span data-stu-id="4d577-184">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="4d577-185">Navigieren Sie zu den **Mixed Reality Toolkit**  >  **Leap Motion** Separate Leap Motion Unity  >  **Modules**</span><span class="sxs-lookup"><span data-stu-id="4d577-185">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="4d577-186">Lassen Sie Unity aktualisieren, wenn Verweise in der **Datei Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** in diesem Schritt geändert werden.</span><span class="sxs-lookup"><span data-stu-id="4d577-186">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="4d577-187">Schließen von Unity</span><span class="sxs-lookup"><span data-stu-id="4d577-187">Close Unity</span></span>
1. <span data-ttu-id="4d577-188">Schließen Visual Studio, wenn sie geöffnet ist</span><span class="sxs-lookup"><span data-stu-id="4d577-188">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="4d577-189">Öffnen Sie den Datei-Explorer, und navigieren Sie zum Stamm des MRTK-Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="4d577-189">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="4d577-190">Löschen des **Verzeichnisses UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="4d577-190">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="4d577-191">Löschen des **Verzeichnisses UnityProjectName/Assets/Plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="4d577-191">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="4d577-192">Löschen Sie die **Datei UnityProjectName/Assets/Plugins/LeapMotion.meta.**</span><span class="sxs-lookup"><span data-stu-id="4d577-192">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="4d577-193">Unity erneut öffnen</span><span class="sxs-lookup"><span data-stu-id="4d577-193">Reopen Unity</span></span>

<span data-ttu-id="4d577-194">In Unity 2018.4 werden Sie möglicherweise feststellen, dass nach dem Löschen der Bibliothek und der Leap Motion Core-Objekte weiterhin Fehler in der Konsole verbleiben.</span><span class="sxs-lookup"><span data-stu-id="4d577-194">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="4d577-195">Wenn Fehler nach dem erneuten Öffnen protokolliert werden, starten Sie Unity erneut.</span><span class="sxs-lookup"><span data-stu-id="4d577-195">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="4d577-196">Häufige Fehler</span><span class="sxs-lookup"><span data-stu-id="4d577-196">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="4d577-197">Leap Motion wurde nicht in MRTK integriert</span><span class="sxs-lookup"><span data-stu-id="4d577-197">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="4d577-198">So testen Sie, ob die Leap Motion Unity-Module in MRTK integriert sind:</span><span class="sxs-lookup"><span data-stu-id="4d577-198">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="4d577-199">Navigieren Sie **zu Mixed Reality Toolkit > Utilities > Leap Motion> Integrationsstatus überprüfen.**</span><span class="sxs-lookup"><span data-stu-id="4d577-199">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="4d577-200">Dadurch wird ein Popupfenster mit einer Meldung angezeigt, ob die Leap Motion Unity-Module in MRTK integriert sind oder nicht.</span><span class="sxs-lookup"><span data-stu-id="4d577-200">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="4d577-201">Wenn in der Meldung angezeigt wird, dass die Objekte nicht integriert wurden:</span><span class="sxs-lookup"><span data-stu-id="4d577-201">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="4d577-202">Stellen Sie sicher, dass sich die Leap Motion Unity-Module im Projekt befinden.</span><span class="sxs-lookup"><span data-stu-id="4d577-202">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="4d577-203">Stellen Sie sicher, dass die hinzugefügte Version unterstützt wird. Informationen zu den unterstützten Versionen finden Sie in der Tabelle oben auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="4d577-203">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="4d577-204">Testen **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span><span class="sxs-lookup"><span data-stu-id="4d577-204">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="4d577-205">Fehler beim Kopieren der Assembly "Multiplayer HLAPI"</span><span class="sxs-lookup"><span data-stu-id="4d577-205">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="4d577-206">Beim Importieren der Leap Motion Unity Core Assets kann dieser Fehler protokolliert werden:</span><span class="sxs-lookup"><span data-stu-id="4d577-206">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="4d577-207">**Lösung**</span><span class="sxs-lookup"><span data-stu-id="4d577-207">**Solution**</span></span>

- <span data-ttu-id="4d577-208">Eine kurzfristige Lösung besteht darin, Unity neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="4d577-208">A short term solution is to restart Unity.</span></span> <span data-ttu-id="4d577-209">Weitere Informationen finden Sie unter [Problem 7761.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761)</span><span class="sxs-lookup"><span data-stu-id="4d577-209">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="4d577-210">Leap Motion-Beispielszene</span><span class="sxs-lookup"><span data-stu-id="4d577-210">Leap Motion Example Scene</span></span>

<span data-ttu-id="4d577-211">Die Beispielszene verwendet das Profil DefaultLeapMotionConfiguration und bestimmt, ob das Unity-Projekt ordnungsgemäß für die Verwendung des Leap Motion-Datenanbieter konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="4d577-211">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="4d577-212">Die Beispielszene ist im Paket **Microsoft.MixedReality.Toolkit.Examples** im Verzeichnis **MRTK/Examples/Demos/HandTracking/** enthalten.</span><span class="sxs-lookup"><span data-stu-id="4d577-212">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="4d577-213">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4d577-213">See also</span></span>

<span data-ttu-id="4d577-214">-[Eingabeanbieter](../features/input/input-providers.md) 
- [Handtracking](../features/input/hand-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="4d577-214">-[Input Providers](../features/input/input-providers.md)
-[Hand Tracking](../features/input/hand-tracking.md)</span></span>
