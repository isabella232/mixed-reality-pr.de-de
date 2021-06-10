---
title: Leap Motion MRTK
description: Dokumentation zum Konfigurieren von Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Leap Motion,
ms.openlocfilehash: 8ef5d26512d50a93691932789e84c099c6246bc3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543236"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="65ef2-104">Konfigurieren der Handnachverfolgung von Leap Motion (von Ultraleap) im MRTK</span><span class="sxs-lookup"><span data-stu-id="65ef2-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="65ef2-105">Für die Verwendung dieses Datenanbieters ist ein [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="65ef2-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="65ef2-106">Die Leap Motion Datenanbieter ermöglicht die artikulierte Handverfolgung für VR und kann für schnelle Prototyperstellung im Editor nützlich sein.</span><span class="sxs-lookup"><span data-stu-id="65ef2-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="65ef2-107">Der Datenanbieter kann so konfiguriert werden, dass er den Leap Motion Controller verwendet, der auf einem Headset oder auf einem Tisch nach oben angeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="65ef2-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="65ef2-109">Dieser Anbieter kann im Editor und auf dem Gerät auf der eigenständigen Plattform verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="65ef2-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="65ef2-110">Sie kann auch im Editor auf der UWP-Plattform, aber NICHT in einem UWP-Build verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="65ef2-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="65ef2-111">MRTK-Version</span><span class="sxs-lookup"><span data-stu-id="65ef2-111">MRTK Version</span></span> | <span data-ttu-id="65ef2-112">Unterstützte Leap Motion Unity-Modulversionen</span><span class="sxs-lookup"><span data-stu-id="65ef2-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="65ef2-113">2.6.x</span><span class="sxs-lookup"><span data-stu-id="65ef2-113">2.6.x</span></span> | <span data-ttu-id="65ef2-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="65ef2-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="65ef2-115">2.7.x</span><span class="sxs-lookup"><span data-stu-id="65ef2-115">2.7.x</span></span>| <span data-ttu-id="65ef2-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span><span class="sxs-lookup"><span data-stu-id="65ef2-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="65ef2-117">Verwenden der Handnachverfolgung von Leap Motion (von Ultraleap) im MRTK</span><span class="sxs-lookup"><span data-stu-id="65ef2-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="65ef2-118">Importieren von MRTK und den Leap Motion Unity-Modulen</span><span class="sxs-lookup"><span data-stu-id="65ef2-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="65ef2-119">Installieren Sie das neueste [Leap Motion SDK,](https://developer.leapmotion.com/releases/?category=orion) falls es noch nicht installiert ist.</span><span class="sxs-lookup"><span data-stu-id="65ef2-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="65ef2-120">Importieren Sie das **Paket Microsoft.MixedReality.Toolkit.Foundation** in das Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="65ef2-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="65ef2-121">Laden Sie die neueste Version der [Leap Motion Unity-Module](https://developer.leapmotion.com/unity) herunter, und importieren Sie sie in das Projekt.</span><span class="sxs-lookup"><span data-stu-id="65ef2-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="65ef2-122">Importieren Sie nur das **Core-Paket** innerhalb der Unity-Module.</span><span class="sxs-lookup"><span data-stu-id="65ef2-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="65ef2-123">Integrieren der Leap Motion Unity-Module in MRTK</span><span class="sxs-lookup"><span data-stu-id="65ef2-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="65ef2-124">Nachdem sich die Unity-Module im Projekt befinden, navigieren Sie zu **Mixed Reality Toolkit**  >  **Leap Motion** Integrate Leap Motion Unity  >  **Modules**</span><span class="sxs-lookup"><span data-stu-id="65ef2-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="65ef2-125">Durch die Integration der Unity-Module in MRTK werden dem Projekt 10 Assemblydefinitionen und Verweise auf die Assemblydefinition **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="65ef2-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="65ef2-126">Vergewissern Sie sich, dass Visual Studio geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="65ef2-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="65ef2-128">Hinzufügen der Leap Motion-Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="65ef2-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="65ef2-129">Erstellen einer neuen Unity-Szene</span><span class="sxs-lookup"><span data-stu-id="65ef2-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="65ef2-130">Fügen Sie MRTK zur Szene hinzu, indem Sie zu **Mixed Reality Toolkit** Add to Scene  >  **(Zur Szene hinzufügen) navigieren und konfigurieren.**</span><span class="sxs-lookup"><span data-stu-id="65ef2-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="65ef2-131">Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen **Sie Kopieren und anpassen** aus, um das Standardmäßige Mixed Reality-Profil zu klonen.</span><span class="sxs-lookup"><span data-stu-id="65ef2-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="65ef2-133">Auswählen  des Eingabekonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="65ef2-133">Select the **Input** Configuration Profile</span></span>

    ![Eingabekonfigurationsprofil 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="65ef2-135">Wählen Sie im Eingabesystemprofil **Klonen** aus, um die Änderung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="65ef2-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="65ef2-137">Öffnen Sie den Abschnitt **Eingabedatenanbieter,** und wählen Sie oben **Datenanbieter** hinzufügen aus. Am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="65ef2-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="65ef2-138">Öffnen Sie den neuen Datenanbieter, und legen **Sie type** auf **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager** fest.</span><span class="sxs-lookup"><span data-stu-id="65ef2-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Add Datenanbieter](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="65ef2-140">Wählen Sie **Klonen** aus, um die Standardeinstellungen für Leap Motion zu ändern.</span><span class="sxs-lookup"><span data-stu-id="65ef2-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="65ef2-142">Die Leap Motion-Datenanbieter enthält die `LeapControllerOrientation` -Eigenschaft, die die Position des Leap Motion Controller darstellt.</span><span class="sxs-lookup"><span data-stu-id="65ef2-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="65ef2-143">`LeapControllerOrientation.Headset` gibt an, dass der Controller auf einem Headset eingebunden ist.</span><span class="sxs-lookup"><span data-stu-id="65ef2-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="65ef2-144">`LeapControllerOrientation.Desk` gibt an, dass der Controller flach auf dem Arbeitsplatz platziert wird.</span><span class="sxs-lookup"><span data-stu-id="65ef2-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="65ef2-145">Der Standardwert ist auf `LeapControllerOrientation.Headset` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="65ef2-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="65ef2-146">Jede Controllerausrichtung enthält Offseteigenschaften:</span><span class="sxs-lookup"><span data-stu-id="65ef2-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="65ef2-147">Die **Eigenschaften** des Headsetausrichtungsoffsets spiegeln die Offseteigenschaften in der LeapXRServiceProvider-Komponente wider.</span><span class="sxs-lookup"><span data-stu-id="65ef2-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="65ef2-148">Verfügt `LeapVRDeviceOffsetMode` über drei Optionen: Standard, Manueller Kopfoffset und Transformation.</span><span class="sxs-lookup"><span data-stu-id="65ef2-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="65ef2-149">Wenn der Offsetmodus Standard ist, wird kein Offset auf den Schaltbewegungscontroller angewendet.</span><span class="sxs-lookup"><span data-stu-id="65ef2-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="65ef2-150">Der Modus Manueller Kopfoffset ermöglicht die Änderung von drei Eigenschaften: `LeapVRDeviceOffsetY` `LeapVRDeviceOffsetZ` und `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="65ef2-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="65ef2-151">Die Achsenoffset-Eigenschaftswerte werden dann auf die Standardplatzierung des Controllers angewendet.</span><span class="sxs-lookup"><span data-stu-id="65ef2-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="65ef2-152">Der Transformationsoffsetmodus enthält die `LeapVRDeviceOrigin` Transform-Eigenschaft, die einen neuen Ursprung für den Leap Motion Controller angibt.</span><span class="sxs-lookup"><span data-stu-id="65ef2-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="65ef2-153">Die **Desk-Ausrichtung** enthält die `LeapControllerOffset` -Eigenschaft, die die Ankerposition der Schalthand des Desks definiert.</span><span class="sxs-lookup"><span data-stu-id="65ef2-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="65ef2-154">Der Offset wird relativ zur Hauptkameraposition berechnet, und der Standardwert ist (0,-0,2, 0,35), um sicherzustellen, dass die Hände vor und in der Kamera angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="65ef2-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="65ef2-155">Die Offseteigenschaften im Profil werden einmal angewendet, wenn die Anwendung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="65ef2-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="65ef2-156">Um die Werte während der Laufzeit zu ändern, erhalten Sie den Leap Motion Service Provider aus der Leap Motion Geräte-Manager:</span><span class="sxs-lookup"><span data-stu-id="65ef2-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="65ef2-157">`EnterPinchDistance` und `ExitPinchDistance` sind die Entfernungsschwellenwerte für die Gestenerkennung durch Tippen in die Luft.</span><span class="sxs-lookup"><span data-stu-id="65ef2-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="65ef2-158">Die Zusammendrückbewegung wird berechnet, indem der Abstand zwischen der Zeigefingerspitze und der Daumenspitze gemessen wird.</span><span class="sxs-lookup"><span data-stu-id="65ef2-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="65ef2-159">Zum Auslösen eines Bei eingaben-Down-Ereignisses wird der Standardwert `EnterPinchDistance` auf 0,02 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="65ef2-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="65ef2-160">Zum Auslösen eines Eingabe-Up-Ereignisses (zum Beenden des Zusammendrückens) beträgt der Standardabstand zwischen der Zeigefingerspitze und der Daumenspitze 0,05.</span><span class="sxs-lookup"><span data-stu-id="65ef2-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="65ef2-161">`LeapControllerOrientation`: Headset (Standard)</span><span class="sxs-lookup"><span data-stu-id="65ef2-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="65ef2-162">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="65ef2-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="65ef2-167">Testen der Leap Motion-Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="65ef2-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="65ef2-168">Nachdem Leap Motion Datenanbieter dem Eingabesystemprofil hinzugefügt wurde, drücken Sie die Wiedergabe, bewegen Sie Ihre Hand vor den Leap Motion Controller. Daraufhin sollte die gemeinsame Darstellung der Hand angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="65ef2-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="65ef2-169">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="65ef2-169">Building your project</span></span>
    - <span data-ttu-id="65ef2-170">Navigieren Sie zu **Datei > Buildeinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="65ef2-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="65ef2-171">Nur eigenständige Builds werden unterstützt, wenn die Leap Motion-Datenanbieter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="65ef2-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="65ef2-172">Anweisungen zum Verwenden eines Windows Mixed Reality Headsets für eigenständige Builds finden Sie unter [Building and deploying MRTK to WMR Headsets (Standalone) (Erstellen und Bereitstellen von MRTK für WMR-Headsets (eigenständig)).](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)</span><span class="sxs-lookup"><span data-stu-id="65ef2-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK to WMR Headsets (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="65ef2-173">Abrufen der Handverbindungen</span><span class="sxs-lookup"><span data-stu-id="65ef2-173">Getting the hand joints</span></span>

<span data-ttu-id="65ef2-174">Das Abrufen von Fugen mithilfe des Leap Motion-Datenanbieter ist identisch mit dem Hand-Joint-Abruf für eine artikulierte MRTK-Hand.</span><span class="sxs-lookup"><span data-stu-id="65ef2-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="65ef2-175">Weitere Informationen finden Sie unter [Handtracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="65ef2-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="65ef2-176">Wenn MRTK in einer Unity-Szene und die Leap Motion-Datenanbieter als Eingabe-Datenanbieter im Eingabesystemprofil hinzugefügt wurden, erstellen Sie ein leeres Spielobjekt, und fügen Sie das folgende Beispielskript an.</span><span class="sxs-lookup"><span data-stu-id="65ef2-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="65ef2-177">Dieses Skript ist ein einfaches Beispiel für das Abrufen der Posen des Handflächengefährdungs in einer Schaltbewegungshand.</span><span class="sxs-lookup"><span data-stu-id="65ef2-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="65ef2-178">Eine Kugel folgt der linken Schalthand, während ein Würfel der rechten Schalthand folgt.</span><span class="sxs-lookup"><span data-stu-id="65ef2-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="65ef2-179">Workflowtipp des Unity-Editors</span><span class="sxs-lookup"><span data-stu-id="65ef2-179">Unity editor workflow tip</span></span>

<span data-ttu-id="65ef2-180">Für die Verwendung des Leap Motion-Datenanbieter ist kein VR-Headset erforderlich.</span><span class="sxs-lookup"><span data-stu-id="65ef2-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="65ef2-181">Änderungen an einer MRTK-App können im Editor mit den Leap-Händen ohne Headset getestet werden.</span><span class="sxs-lookup"><span data-stu-id="65ef2-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="65ef2-182">Die Leap Motion Hands werden im Editor angezeigt, ohne dass ein VR-Headset angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="65ef2-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="65ef2-183">Wenn auf `LeapControllerOrientation` **Headset** festgelegt ist, muss der Leap Motion-Controller mit der Kamera nach vorn mit einer Hand gehalten werden.</span><span class="sxs-lookup"><span data-stu-id="65ef2-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="65ef2-184">Wenn die Kamera mithilfe von WASD-Schlüsseln im Editor bewegt wird und das `LeapControllerOrientation` **Headset** ist, folgen die Hände nicht der Kamera.</span><span class="sxs-lookup"><span data-stu-id="65ef2-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="65ef2-185">Die Hände folgen nur der Kamerabewegung, wenn ein VR-Headset angeschlossen ist, während das `LeapControllerOrientation` **Headset** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="65ef2-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="65ef2-186">Die Schalthand folgt der Kamerabewegung im Editor, wenn auf `LeapControllerOrientation` **Desk** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="65ef2-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="65ef2-187">Entfernen von Leap Motion aus dem Projekt</span><span class="sxs-lookup"><span data-stu-id="65ef2-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="65ef2-188">Navigieren Sie zu den **Unity-Modulen Mixed Reality Toolkit**  >  **Leap Motion** Separate Leap  >  **Motion**</span><span class="sxs-lookup"><span data-stu-id="65ef2-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="65ef2-189">Lassen Sie Unity aktualisieren, da Verweise in der Datei **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** in diesem Schritt geändert werden.</span><span class="sxs-lookup"><span data-stu-id="65ef2-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="65ef2-190">Schließen von Unity</span><span class="sxs-lookup"><span data-stu-id="65ef2-190">Close Unity</span></span>
1. <span data-ttu-id="65ef2-191">Schließen sie Visual Studio, wenn es geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="65ef2-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="65ef2-192">Öffnen Sie den Datei-Explorer, und navigieren Sie zum Stamm des MRTK-Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="65ef2-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="65ef2-193">Löschen des **UnityProjectName/Library-Verzeichnisses**</span><span class="sxs-lookup"><span data-stu-id="65ef2-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="65ef2-194">Löschen des **Verzeichnisses UnityProjectName/Assets/Plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="65ef2-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="65ef2-195">Löschen Sie die Datei **UnityProjectName/Assets/Plugins/LeapMotion.meta.**</span><span class="sxs-lookup"><span data-stu-id="65ef2-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="65ef2-196">Unity erneut öffnen</span><span class="sxs-lookup"><span data-stu-id="65ef2-196">Reopen Unity</span></span>

<span data-ttu-id="65ef2-197">In Unity 2018.4 können Sie feststellen, dass Fehler nach dem Löschen der Bibliothek und der Leap Motion Core-Objekte weiterhin in der Konsole verbleiben.</span><span class="sxs-lookup"><span data-stu-id="65ef2-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="65ef2-198">Wenn nach dem erneuten Öffnen Fehler protokolliert werden, starten Sie Unity erneut neu.</span><span class="sxs-lookup"><span data-stu-id="65ef2-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="65ef2-199">Häufige Fehler</span><span class="sxs-lookup"><span data-stu-id="65ef2-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="65ef2-200">Leap Motion wurde nicht in MRTK integriert.</span><span class="sxs-lookup"><span data-stu-id="65ef2-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="65ef2-201">So testen Sie, ob die Leap Motion Unity-Module in MRTK integriert sind:</span><span class="sxs-lookup"><span data-stu-id="65ef2-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="65ef2-202">Navigieren Sie **zu Mixed Reality Toolkit > Utilities > Leap Motion> Integrationsstatus überprüfen.**</span><span class="sxs-lookup"><span data-stu-id="65ef2-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="65ef2-203">Dadurch wird ein Popupfenster mit einer Meldung angezeigt, ob die Leap Motion Unity-Module in MRTK integriert sind oder nicht.</span><span class="sxs-lookup"><span data-stu-id="65ef2-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="65ef2-204">Wenn in der Meldung angezeigt wird, dass die Objekte nicht integriert wurden:</span><span class="sxs-lookup"><span data-stu-id="65ef2-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="65ef2-205">Stellen Sie sicher, dass sich die Leap Motion Unity-Module im Projekt befinden.</span><span class="sxs-lookup"><span data-stu-id="65ef2-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="65ef2-206">Stellen Sie sicher, dass die hinzugefügte Version unterstützt wird. Informationen zu den unterstützten Versionen finden Sie in der Tabelle oben auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="65ef2-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="65ef2-207">Testen **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span><span class="sxs-lookup"><span data-stu-id="65ef2-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="65ef2-208">Fehler beim Kopieren der Assembly Multiplayer HLAPI</span><span class="sxs-lookup"><span data-stu-id="65ef2-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="65ef2-209">Beim Import der Leap Motion Unity Core Assets kann dieser Fehler protokolliert werden:</span><span class="sxs-lookup"><span data-stu-id="65ef2-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="65ef2-210">**Lösung**</span><span class="sxs-lookup"><span data-stu-id="65ef2-210">**Solution**</span></span>

- <span data-ttu-id="65ef2-211">Eine kurzfristige Lösung ist der Neustart von Unity.</span><span class="sxs-lookup"><span data-stu-id="65ef2-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="65ef2-212">Weitere Informationen finden Sie unter Issue [7761 (Problem 7761).](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761)</span><span class="sxs-lookup"><span data-stu-id="65ef2-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="65ef2-213">Beispielszene für Schaltbewegung</span><span class="sxs-lookup"><span data-stu-id="65ef2-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="65ef2-214">Die Beispielszene verwendet das Profil DefaultLeapMotionConfiguration und ermittelt, ob das Unity-Projekt ordnungsgemäß für die Verwendung des Leap Motion-Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="65ef2-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="65ef2-215">Die Beispielszene ist im **Paket Microsoft.MixedReality.Toolkit.Examples** im **Verzeichnis MRTK/Examples/Demos/HandTracking/** enthalten.</span><span class="sxs-lookup"><span data-stu-id="65ef2-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="65ef2-216">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="65ef2-216">See also</span></span>

- [<span data-ttu-id="65ef2-217">Eingabeanbieter</span><span class="sxs-lookup"><span data-stu-id="65ef2-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="65ef2-218">Handtracking</span><span class="sxs-lookup"><span data-stu-id="65ef2-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
