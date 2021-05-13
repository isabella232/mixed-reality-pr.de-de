---
title: LeapMotionMRTK
description: Dokumentation zum Konfigurieren für Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Leap Motion,
ms.openlocfilehash: ea9e257815116c364fe2f1e37ca3477ec56262cb
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852491"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="1282c-104">Konfigurieren der Handnachverfolgung von Leap Motion (von Ultraleap) im MRTK</span><span class="sxs-lookup"><span data-stu-id="1282c-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="1282c-105">Für [die Verwendung dieses Datenanbieters](https://www.ultraleap.com/product/leap-motion-controller/) ist ein Leap Motion Controller erforderlich.</span><span class="sxs-lookup"><span data-stu-id="1282c-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="1282c-106">Der Leap Motion Datenanbieter ermöglicht die artikulierte Handverfolgung für VR und kann für die schnelle Prototyperstellung im Editor nützlich sein.</span><span class="sxs-lookup"><span data-stu-id="1282c-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="1282c-107">Der Datenanbieter kann so konfiguriert werden, dass er den Leap Motion Controller verwendet, der auf einem Headset oder auf einer Desk-Gesichtserkennung installiert ist.</span><span class="sxs-lookup"><span data-stu-id="1282c-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="1282c-109">Dieser Anbieter kann im Editor und auf dem Gerät auf der eigenständigen Plattform verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1282c-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="1282c-110">Sie kann auch im Editor auf der UWP-Plattform, aber NICHT in einem UWP-Build verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1282c-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

|<span data-ttu-id="1282c-111">Unterstützte Unity-Moduleversionen für Leap Motion</span><span class="sxs-lookup"><span data-stu-id="1282c-111">Leap Motion Unity Modules Versions Supported</span></span>|
|---|
|<span data-ttu-id="1282c-112">4.5.0</span><span class="sxs-lookup"><span data-stu-id="1282c-112">4.5.0</span></span>|
|<span data-ttu-id="1282c-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="1282c-113">4.5.1</span></span>|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="1282c-114">Verwenden der Handnachverfolgung von Leap Motion (von Ultraleap) in MRTK</span><span class="sxs-lookup"><span data-stu-id="1282c-114">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="1282c-115">Importieren von MRTK und unity-Modulen für Leap Motion</span><span class="sxs-lookup"><span data-stu-id="1282c-115">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="1282c-116">Installieren Sie [das Leap Motion SDK 4.0.0,](https://developer.leapmotion.com/releases/?category=orion) falls es noch nicht installiert ist.</span><span class="sxs-lookup"><span data-stu-id="1282c-116">Install the [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="1282c-117">Importieren Sie **das Paket Microsoft.MixedReality.Toolkit.Foundation** in das Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="1282c-117">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="1282c-118">Laden Sie die neueste Version der [Leap Motion Unity-Module](https://developer.leapmotion.com/unity) herunter, und importieren Sie sie in das Projekt.</span><span class="sxs-lookup"><span data-stu-id="1282c-118">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="1282c-119">Importieren Sie nur das **Core-Paket** innerhalb der Unity-Module.</span><span class="sxs-lookup"><span data-stu-id="1282c-119">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="1282c-120">Integrieren der Leap Motion Unity-Module in MRTK</span><span class="sxs-lookup"><span data-stu-id="1282c-120">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="1282c-121">Nachdem sich die Unity-Module im Projekt befinden, navigieren Sie zu Mixed Reality **Toolkit**  >  **Leap Motion** Integrate Leap Motion Unity  >  **Modules**</span><span class="sxs-lookup"><span data-stu-id="1282c-121">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="1282c-122">Durch die Integration der Unity-Module in MRTK werden dem Projekt 10 Assemblydefinitionen und Verweise auf die **Assemblydefinition Microsoft.MixedReality.Toolkit.Providers.LeapMotion** hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="1282c-122">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="1282c-123">Vergewissern Sie sich, dass Visual Studio geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="1282c-123">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="1282c-125">Hinzufügen der Leap Motion-Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="1282c-125">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="1282c-126">Erstellen einer neuen Unity-Szene</span><span class="sxs-lookup"><span data-stu-id="1282c-126">Create a new Unity scene</span></span>
    - <span data-ttu-id="1282c-127">Fügen Sie MRTK zur Szene hinzu, indem Sie zu **Mixed Reality Toolkit** Add to Scene  >  **(Zur Szene hinzufügen) navigieren und konfigurieren.**</span><span class="sxs-lookup"><span data-stu-id="1282c-127">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="1282c-128">Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen **Sie Kopieren und Anpassen** aus, um das Standardmäßige Mixed Reality-Profil zu klonen.</span><span class="sxs-lookup"><span data-stu-id="1282c-128">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="1282c-130">Auswählen  des Eingabekonfigurationsprofils</span><span class="sxs-lookup"><span data-stu-id="1282c-130">Select the **Input** Configuration Profile</span></span>

    ![Eingabekonfigurationsprofil 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="1282c-132">Wählen Sie im Eingabesystemprofil **Klonen** aus, um die Änderung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="1282c-132">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="1282c-134">Öffnen Sie den Abschnitt **Eingabedatenanbieter,** und wählen Sie oben **Datenanbieter** hinzufügen aus. Am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="1282c-134">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="1282c-135">Öffnen Sie den neuen Datenanbieter, und legen **Sie den Typ** auf **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager** fest.</span><span class="sxs-lookup"><span data-stu-id="1282c-135">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Add Datenanbieter](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="1282c-137">Wählen Sie **Klonen** aus, um die Standardeinstellungen für Leap Motion zu ändern.</span><span class="sxs-lookup"><span data-stu-id="1282c-137">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="1282c-139">Die Leap Motion-Datenanbieter enthält die `LeapControllerOrientation` -Eigenschaft, die die Position des Leap Motion Controller darstellt.</span><span class="sxs-lookup"><span data-stu-id="1282c-139">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="1282c-140">`LeapControllerOrientation.Headset` gibt an, dass der Controller auf einem Headset eingebunden ist.</span><span class="sxs-lookup"><span data-stu-id="1282c-140">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="1282c-141">`LeapControllerOrientation.Desk` gibt an, dass der Controller flach auf dem Arbeitsplatz platziert wird.</span><span class="sxs-lookup"><span data-stu-id="1282c-141">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="1282c-142">Der Standardwert ist auf `LeapControllerOrientation.Headset` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1282c-142">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="1282c-143">Jede Controllerausrichtung enthält Offseteigenschaften:</span><span class="sxs-lookup"><span data-stu-id="1282c-143">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="1282c-144">Die  Headset-Ausrichtungsoffseteigenschaften spiegeln die Offseteigenschaften in der LeapXRServiceProvider-Komponente wieder.</span><span class="sxs-lookup"><span data-stu-id="1282c-144">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="1282c-145">Die `LeapVRDeviceOffsetMode` verfügt über drei Optionen: Standard, Manueller Kopfoffset und Transformation.</span><span class="sxs-lookup"><span data-stu-id="1282c-145">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="1282c-146">Wenn der Offsetmodus Standard ist, wird kein Offset auf den Leap Motion Controller angewendet.</span><span class="sxs-lookup"><span data-stu-id="1282c-146">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="1282c-147">Der Modus "Manueller Kopfoffset" ermöglicht die Änderung von drei Eigenschaften: `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` und `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="1282c-147">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="1282c-148">Die Eigenschaftswerte des Achsenoffsets werden dann auf die Standardplatzierung des Controllers angewendet.</span><span class="sxs-lookup"><span data-stu-id="1282c-148">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="1282c-149">Der Transformationsoffsetmodus enthält die `LeapVRDeviceOrigin` Transform-Eigenschaft, die einen neuen Ursprung für den Leap Motion Controller angibt.</span><span class="sxs-lookup"><span data-stu-id="1282c-149">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="1282c-150">Die **Desk-Ausrichtung** enthält die `LeapControllerOffset` -Eigenschaft, die die Ankerposition der Schaltersprunghands definiert.</span><span class="sxs-lookup"><span data-stu-id="1282c-150">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="1282c-151">Der Offset wird relativ zur Hauptkameraposition berechnet, und der Standardwert ist (0,-0,2, 0,35), um sicherzustellen, dass die Hände vor und in der Ansicht der Kamera angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1282c-151">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="1282c-152">Die Offseteigenschaften im Profil werden einmal angewendet, wenn die Anwendung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="1282c-152">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="1282c-153">Um die Werte während der Laufzeit zu ändern, können Sie den Leap Motion Service Provider aus dem Leap Motion-Geräte-Manager:</span><span class="sxs-lookup"><span data-stu-id="1282c-153">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="1282c-154">`EnterPinchDistance` und `ExitPinchDistance` sind die Entfernungsschwellenwerte für die Erkennung von Pinch-/Air-Tippbewegungen.</span><span class="sxs-lookup"><span data-stu-id="1282c-154">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="1282c-155">Die Heftbewegung wird berechnet, indem der Abstand zwischen der Zeigefingerspitze und der Daumenspitze gemessen wird.</span><span class="sxs-lookup"><span data-stu-id="1282c-155">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="1282c-156">Der Standardwert ist auf 0,02 festgelegt, um ein -Ereignis bei der Eingabe nach `EnterPinchDistance` unten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1282c-156">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="1282c-157">Der Standardabstand zwischen der Zeigefingerspitze und der Daumenspitze beträgt 0,05, um ein Beim-Eingabe-Nach-oben-Ereignis (beenden des Heftes) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1282c-157">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="1282c-158">`LeapControllerOrientation`: Headset (Standard)</span><span class="sxs-lookup"><span data-stu-id="1282c-158">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="1282c-159">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="1282c-159">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="1282c-164">Testen der Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="1282c-164">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="1282c-165">Nachdem Leap Motion Datenanbieter dem Eingabesystemprofil hinzugefügt wurde, drücken Sie die Wiedergabe, bewegen Sie Ihre Hand vor den Leap Motion Controller. Daraufhin sollte die gemeinsame Darstellung der Hand angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1282c-165">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="1282c-166">Erstellen Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="1282c-166">Building your project</span></span>
    - <span data-ttu-id="1282c-167">Navigieren Sie zu **Datei > Buildeinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="1282c-167">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="1282c-168">Nur eigenständige Builds werden unterstützt, wenn die Leap Motion-Datenanbieter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1282c-168">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="1282c-169">Anweisungen zum Verwenden eines Windows Mixed Reality Headsets für eigenständige Builds finden Sie unter [Erstellen und Bereitstellen von MRTK (Eigenständig).](wmr-mrtk.md#building-and-deploying-mrtk-standalone)</span><span class="sxs-lookup"><span data-stu-id="1282c-169">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="1282c-170">Abrufen der Handverbindungen</span><span class="sxs-lookup"><span data-stu-id="1282c-170">Getting the hand joints</span></span>

<span data-ttu-id="1282c-171">Das Abrufen von Fugen mithilfe der Schaltbewegungs-Datenanbieter ist identisch mit dem Handverbindungsabruf für eine artikulierte MRTK-Hand.</span><span class="sxs-lookup"><span data-stu-id="1282c-171">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="1282c-172">Weitere Informationen finden Sie unter [Handtracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="1282c-172">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="1282c-173">Wenn MRTK in einer Unity-Szene und die Leap Motion-Datenanbieter als Eingabe-Datenanbieter im Eingabesystemprofil hinzugefügt wurden, erstellen Sie ein leeres Spielobjekt, und fügen Sie das folgende Beispielskript an.</span><span class="sxs-lookup"><span data-stu-id="1282c-173">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="1282c-174">Dieses Skript ist ein einfaches Beispiel für das Abrufen der Posen des Handflächengefährdungs in einer Schaltbewegungshand.</span><span class="sxs-lookup"><span data-stu-id="1282c-174">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="1282c-175">Eine Kugel folgt der linken Schalthand, während ein Würfel der rechten Schalthand folgt.</span><span class="sxs-lookup"><span data-stu-id="1282c-175">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="1282c-176">Workflowtipp des Unity-Editors</span><span class="sxs-lookup"><span data-stu-id="1282c-176">Unity editor workflow tip</span></span>

<span data-ttu-id="1282c-177">Für die Verwendung des Leap Motion-Datenanbieter ist kein VR-Headset erforderlich.</span><span class="sxs-lookup"><span data-stu-id="1282c-177">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="1282c-178">Änderungen an einer MRTK-App können im Editor mit den Leap-Händen ohne Headset getestet werden.</span><span class="sxs-lookup"><span data-stu-id="1282c-178">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="1282c-179">Die Leap Motion Hands werden im Editor angezeigt, ohne dass ein VR-Headset angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="1282c-179">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="1282c-180">Wenn `LeapControllerOrientation` auf **Headset** festgelegt ist, muss der Leap Motion-Controller mit der Kamera nach vorn mit einer Hand gehalten werden.</span><span class="sxs-lookup"><span data-stu-id="1282c-180">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="1282c-181">Wenn die Kamera mithilfe von WASD-Schlüsseln im Editor bewegt wird und das `LeapControllerOrientation` **Headset** ist, folgen die Hände nicht der Kamera.</span><span class="sxs-lookup"><span data-stu-id="1282c-181">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="1282c-182">Die Hände folgen nur der Kamerabewegung, wenn ein VR-Headset angeschlossen ist, während das `LeapControllerOrientation` **Headset** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1282c-182">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="1282c-183">Die Schalthand folgt der Kamerabewegung im Editor, wenn auf `LeapControllerOrientation` **Desk** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1282c-183">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="1282c-184">Entfernen von Leap Motion aus dem Projekt</span><span class="sxs-lookup"><span data-stu-id="1282c-184">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="1282c-185">Navigieren Sie zu den **Mixed Reality Toolkit**  >  **Leap Motion** Separate Leap Motion Unity  >  **Modules**</span><span class="sxs-lookup"><span data-stu-id="1282c-185">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="1282c-186">Lassen Sie Unity aktualisieren, wenn Verweise in der **Datei Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** in diesem Schritt geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1282c-186">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="1282c-187">Schließen von Unity</span><span class="sxs-lookup"><span data-stu-id="1282c-187">Close Unity</span></span>
1. <span data-ttu-id="1282c-188">Schließen Visual Studio, wenn sie geöffnet ist</span><span class="sxs-lookup"><span data-stu-id="1282c-188">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="1282c-189">Öffnen Sie den Datei-Explorer, und navigieren Sie zum Stamm des MRTK-Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="1282c-189">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="1282c-190">Löschen des **Verzeichnisses UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="1282c-190">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="1282c-191">Löschen des **Verzeichnisses UnityProjectName/Assets/Plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="1282c-191">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="1282c-192">Löschen Sie die **Datei UnityProjectName/Assets/Plugins/LeapMotion.meta.**</span><span class="sxs-lookup"><span data-stu-id="1282c-192">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="1282c-193">Unity erneut öffnen</span><span class="sxs-lookup"><span data-stu-id="1282c-193">Reopen Unity</span></span>

<span data-ttu-id="1282c-194">In Unity 2018.4 werden Sie möglicherweise feststellen, dass nach dem Löschen der Bibliothek und der Leap Motion Core-Objekte weiterhin Fehler in der Konsole verbleiben.</span><span class="sxs-lookup"><span data-stu-id="1282c-194">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="1282c-195">Wenn Fehler nach dem erneuten Öffnen protokolliert werden, starten Sie Unity erneut.</span><span class="sxs-lookup"><span data-stu-id="1282c-195">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="1282c-196">Häufige Fehler</span><span class="sxs-lookup"><span data-stu-id="1282c-196">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="1282c-197">Leap Motion wurde nicht in MRTK integriert</span><span class="sxs-lookup"><span data-stu-id="1282c-197">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="1282c-198">So testen Sie, ob die Leap Motion Unity-Module in MRTK integriert sind:</span><span class="sxs-lookup"><span data-stu-id="1282c-198">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="1282c-199">Navigieren Sie **zu Mixed Reality Toolkit > Utilities > Leap Motion> Integrationsstatus überprüfen.**</span><span class="sxs-lookup"><span data-stu-id="1282c-199">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="1282c-200">Dadurch wird ein Popupfenster mit einer Meldung angezeigt, ob die Leap Motion Unity-Module in MRTK integriert sind oder nicht.</span><span class="sxs-lookup"><span data-stu-id="1282c-200">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="1282c-201">Wenn in der Meldung angezeigt wird, dass die Objekte nicht integriert wurden:</span><span class="sxs-lookup"><span data-stu-id="1282c-201">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="1282c-202">Stellen Sie sicher, dass sich die Leap Motion Unity-Module im Projekt befinden.</span><span class="sxs-lookup"><span data-stu-id="1282c-202">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="1282c-203">Stellen Sie sicher, dass die hinzugefügte Version unterstützt wird. Informationen zu den unterstützten Versionen finden Sie in der Tabelle oben auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="1282c-203">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="1282c-204">Testen **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span><span class="sxs-lookup"><span data-stu-id="1282c-204">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="1282c-205">Fehler beim Kopieren der Multiplayer-HLAPI-Assembly</span><span class="sxs-lookup"><span data-stu-id="1282c-205">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="1282c-206">Beim Importieren der Leap Motion Unity Core Assets kann dieser Fehler protokolliert werden:</span><span class="sxs-lookup"><span data-stu-id="1282c-206">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="1282c-207">**Lösung**</span><span class="sxs-lookup"><span data-stu-id="1282c-207">**Solution**</span></span>

- <span data-ttu-id="1282c-208">Eine kurzfristige Lösung besteht darin, Unity neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="1282c-208">A short term solution is to restart Unity.</span></span> <span data-ttu-id="1282c-209">Weitere Informationen finden Sie unter [Problem 7761.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761)</span><span class="sxs-lookup"><span data-stu-id="1282c-209">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="1282c-210">Leap Motion-Beispielszene</span><span class="sxs-lookup"><span data-stu-id="1282c-210">Leap Motion Example Scene</span></span>

<span data-ttu-id="1282c-211">Die Beispielszene verwendet das Profil DefaultLeapMotionConfiguration und bestimmt, ob das Unity-Projekt ordnungsgemäß für die Verwendung des Leap Motion-Datenanbieter konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="1282c-211">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="1282c-212">Die Beispielszene ist im Paket **Microsoft.MixedReality.Toolkit.Examples** im Verzeichnis **MRTK/Examples/Demos/HandTracking/** enthalten.</span><span class="sxs-lookup"><span data-stu-id="1282c-212">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="1282c-213">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1282c-213">See also</span></span>

<span data-ttu-id="1282c-214">-[Eingabeanbieter](../features/input/input-providers.md) 
- [Handtracking](../features/input/hand-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="1282c-214">-[Input Providers](../features/input/input-providers.md)
-[Hand Tracking](../features/input/hand-tracking.md)</span></span>
