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
# <a name="using-leap-motion"></a>Verwenden von Leap Motion

Für [die Verwendung dieses Datenanbieters](https://www.ultraleap.com/product/leap-motion-controller/) ist ein Leap Motion Controller erforderlich.

Der Leap Motion Datenanbieter ermöglicht die artikulierte Handverfolgung für VR und kann für die schnelle Prototyperstellung im Editor nützlich sein.  Der Datenanbieter kann so konfiguriert werden, dass er den Leap Motion Controller verwendet, der auf einem Headset oder auf einer Desk-Gesichtserkennung installiert ist.

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

Dieser Anbieter kann im Editor und auf dem Gerät auf der eigenständigen Plattform verwendet werden.  Sie kann auch im Editor auf der UWP-Plattform, aber NICHT in einem UWP-Build verwendet werden.

| MRTK-Version | Unterstützte Leap Motion Unity-Modulversionen |
| --- | --- |
|2.6.x | 4.5.0, 4.5.1|
|2.7.x| 4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>Verwenden der Handnachverfolgung von Leap Motion (von Ultraleap) in MRTK

1. Importieren von MRTK und unity-Modulen für Leap Motion
    - Installieren Sie das neueste [Leap Motion SDK,](https://developer.leapmotion.com/releases/?category=orion) falls es noch nicht installiert ist.
    - Importieren Sie **das Paket Microsoft.MixedReality.Toolkit.Foundation** in das Unity-Projekt.
    - Laden Sie die neueste Version der [Leap Motion Unity-Module](https://developer.leapmotion.com/unity) herunter, und importieren Sie sie in das Projekt.
        - Importieren Sie nur das **Core-Paket** innerhalb der Unity-Module.

1. Integrieren der Leap Motion Unity-Module in MRTK
    - Nachdem sich die Unity-Module im Projekt befinden, navigieren Sie zu Mixed Reality **Toolkit**  >  **Leap Motion** Integrate Leap Motion Unity  >  **Modules**
    > [!NOTE]
    > Durch die Integration der Unity-Module in MRTK werden dem Projekt 10 Assemblydefinitionen und Verweise auf die **Assemblydefinition Microsoft.MixedReality.Toolkit.Providers.LeapMotion** hinzufügt. Vergewissern Sie sich, dass Visual Studio geschlossen ist.

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. Hinzufügen des Leap Motion-Datenanbieter
    - Erstellen einer neuen Unity-Szene
    - Fügen Sie der Szene MRTK hinzu, indem Sie zu Mixed Reality **Toolkit**  >  **Hinzufügen zur Szene und Konfigurieren navigieren.**
    - Wählen Sie das MixedRealityToolkit-Spielobjekt in der Hierarchie aus, und wählen Sie Kopieren und **Anpassen aus,** um das Mixed Reality-Standardprofil zu klonen.

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - Auswählen des **Eingabekonfigurationsprofils**

    ![Eingabekonfigurationsprofil 1](../images/cross-platform/InputConfigurationProfile.png)

    - Wählen **Sie im** Eingabesystemprofil Klonen aus, um die Änderung zu aktivieren.

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - Öffnen Sie **den Abschnitt Eingabedatenanbieter,** wählen Sie oben **Datenanbieter** Hinzufügen aus. Am Ende der Liste wird ein neuer Datenanbieter hinzugefügt.  Öffnen Sie den neuen Datenanbieter, und legen Sie **type** auf **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager fest.**

    ![Leap Add Datenanbieter](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - Wählen Sie **Klonen** aus, um die Standardeinstellungen für Leap Motion zu ändern.

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - Der Leap Motion Datenanbieter enthält die `LeapControllerOrientation` -Eigenschaft, die die Position des Leap Motion-Controllers ist. `LeapControllerOrientation.Headset` gibt an, dass der Controller auf einem Headset bereitgestellt ist. `LeapControllerOrientation.Desk` gibt an, dass der Controller flach auf dem Desk platziert ist. Der Standardwert ist auf `LeapControllerOrientation.Headset` festgelegt.
    - Jede Controllerausrichtung enthält Offseteigenschaften:
      - Die  Headset-Ausrichtungsoffseteigenschaften spiegeln die Offseteigenschaften in der LeapXRServiceProvider-Komponente wieder.  Die `LeapVRDeviceOffsetMode` verfügt über drei Optionen: Standard, Manueller Kopfoffset und Transformation.  Wenn der Offsetmodus Standard ist, wird kein Offset auf den Leap Motion Controller angewendet.  Der Modus "Manueller Kopfoffset" ermöglicht die Änderung von drei Eigenschaften: `LeapVRDeviceOffsetY` , `LeapVRDeviceOffsetZ` und `LeapVRDeviceTiltX` .  Die Eigenschaftswerte des Achsenoffsets werden dann auf die Standardplatzierung des Controllers angewendet.  Der Transformationsoffsetmodus enthält die `LeapVRDeviceOrigin` Transform-Eigenschaft, die einen neuen Ursprung für den Leap Motion Controller angibt.
      - Die **Desk-Ausrichtung** enthält die `LeapControllerOffset` -Eigenschaft, die die Ankerposition der Schaltersprunghands definiert.  Der Offset wird relativ zur Hauptkameraposition berechnet, und der Standardwert ist (0,-0,2, 0,35), um sicherzustellen, dass die Hände vor und in der Ansicht der Kamera angezeigt werden.

        > [!NOTE]
        > Die Offseteigenschaften im Profil werden einmal angewendet, wenn die Anwendung gestartet wird.  Um die Werte während der Laufzeit zu ändern, können Sie den Leap Motion Service Provider aus dem Leap Motion-Geräte-Manager:
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` und `ExitPinchDistance` sind die Entfernungsschwellenwerte für die Erkennung von Pinch-/Air-Tippbewegungen.  Die Heftbewegung wird berechnet, indem der Abstand zwischen der Zeigefingerspitze und der Daumenspitze gemessen wird.  Der Standardwert ist auf 0,02 festgelegt, um ein -Ereignis bei der Eingabe nach `EnterPinchDistance` unten zu erhalten.  Der Standardabstand zwischen der Zeigefingerspitze und der Daumenspitze beträgt 0,05, um ein Beim-Eingabe-Nach-oben-Ereignis (beenden des Heftes) zu erstellen.

    `LeapControllerOrientation`: Headset (Standard) |  `LeapControllerOrientation`: Desk
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. Testen des Leap Motion Datenanbieter
    - Nachdem Leap Motion Datenanbieter dem Eingabesystemprofil hinzugefügt wurde, drücken Sie die Wiedergabe, bewegen Sie Ihre Hand vor dem Leap Motion Controller, und Sie sollten die gemeinsame Darstellung der Hand sehen.

1. Erstellen Ihres Projekts
    - Navigieren Sie **zu Datei > Build Einstellungen**
    - Nur eigenständige Builds werden unterstützt, wenn die Leap Motion-Datenanbieter.
    - Anweisungen zur Verwendung eines Windows Mixed Reality-Headsets für eigenständige Builds finden Sie unter [Building and deploying MRTK to WMR Headsets (Standalone) (Erstellen und Bereitstellen von MRTK für WMR-Headsets (eigenständig)).](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)

## <a name="getting-the-hand-joints"></a>Abrufen der Handgelenke

Das Abrufen von Fugen mithilfe Datenanbieter Leap Motion ist identisch mit dem Handknüpfabruf für eine MRTK-Artikulierte Hand.  Weitere Informationen finden Sie unter [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).

Erstellen Sie mit DEM MRTK in einer Unity-Szene und dem Leap Motion-Datenanbieter, das als Eingabe-Datenanbieter im Eingabesystemprofil hinzugefügt wurde, ein leeres Spielobjekt, und fügen Sie das folgende Beispielskript an.

Dieses Skript ist ein einfaches Beispiel dafür, wie sie die Pose des Handgelenks in einer Leap Motion Hand abrufen.  Eine Kugel folgt der linken Leap-Hand, während ein Würfel der rechten Leap-Hand folgt.

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

## <a name="unity-editor-workflow-tip"></a>Workflowtipp für den Unity-Editor

Die Verwendung des Leap Motion Datenanbieter erfordert kein VR-Headset.  Änderungen an einer MRTK-App können im Editor mit den Leap-Händen ohne Headset getestet werden.

Die Leap Motion Hands werden im Editor angezeigt, ohne dass ein VR-Headset angeschlossen ist.  Wenn der auf Headset festgelegt ist, muss der Leap Motion-Controller um eine Hand mit der nach vorn gerichteten `LeapControllerOrientation` Kamera gehalten werden. 

> [!NOTE]
> Wenn die Kamera mithilfe von WASD-Tasten im Editor bewegt wird und headset ist, folgen die Hände `LeapControllerOrientation` nicht der Kamera.  Die Hände folgen nur der Kamerabewegung, wenn ein VR-Headset angeschlossen ist, während `LeapControllerOrientation` das **Headset festgelegt ist.**  Die Leap-Hände folgen der Kamerabewegung im Editor, wenn `LeapControllerOrientation` auf **Desk festgelegt ist.**

## <a name="removing-leap-motion-from-the-project"></a>Entfernen von Leap Motion aus Project

1. Navigieren Sie zu den **Mixed Reality Toolkit**  >  **Leap Motion** Separate Leap Motion Unity  >  **Modules**
    - Lassen Sie Unity aktualisieren, wenn Verweise in der **Datei Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** in diesem Schritt geändert werden.
1. Schließen von Unity
1. Schließen Visual Studio, wenn es geöffnet ist
1. Öffnen Sie den Datei-Explorer, und navigieren Sie zum Stamm des MRTK-Unity-Projekts.
    - Löschen des **Verzeichnisses UnityProjectName/Library**
    - Löschen des **Verzeichnisses UnityProjectName/Assets/Plugins/LeapMotion**
    - Löschen Sie die **Datei UnityProjectName/Assets/Plugins/LeapMotion.meta.**
1. Unity erneut öffnen

In Unity 2018.4 werden Sie möglicherweise feststellen, dass nach dem Löschen der Bibliothek und der Leap Motion Core-Objekte weiterhin Fehler in der Konsole verbleiben.
Wenn Fehler nach dem erneuten Öffnen protokolliert werden, starten Sie Unity erneut.

## <a name="common-errors"></a>Häufige Fehler

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap Motion ist nicht in MRTK integriert

So testen Sie, ob die Leap Motion Unity-Module in MRTK integriert wurden:

- Navigieren Sie zu **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status (Integrationsstatus überprüfen).**
  - Dadurch wird ein Popupfenster mit einer Meldung angezeigt, ob die Leap Motion Unity-Module in MRTK integriert wurden oder nicht.
- Wenn die Meldung besagt, dass die Objekte nicht integriert wurden:
  - Stellen Sie sicher, dass sich die Leap Motion Unity-Module im Projekt befinden.
  - Stellen Sie sicher, dass die hinzugefügte Version unterstützt wird. Informationen zu unterstützten Versionen finden Sie in der Tabelle oben auf der Seite.
  - Probieren Sie **Mixed Reality Toolkit > Utilities > Leap Motion > Integrieren von Leap Motion Unity-Modulen** aus.

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>Fehler beim Kopieren der Multiplayer-HLAPI-Assembly

Beim Importieren der Leap Motion Unity Core Assets kann dieser Fehler protokolliert werden:

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**Lösung**

- Eine kurzfristige Lösung besteht darin, Unity neu zu starten. Weitere Informationen finden Sie unter [Problem 7761.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761)

## <a name="leap-motion-example-scene"></a>Leap Motion-Beispielszene

Die Beispielszene verwendet das Profil DefaultLeapMotionConfiguration und bestimmt, ob das Unity-Projekt ordnungsgemäß für die Verwendung des Leap Motion-Datenanbieter konfiguriert wurde.

Die Beispielszene ist im Paket **Microsoft.MixedReality.Toolkit.Examples** im Verzeichnis **MRTK/Examples/Demos/HandTracking/** enthalten.  

## <a name="see-also"></a>Siehe auch

- [Eingabeanbieter](../features/input/input-providers.md)
- [Handtracking](../features/input/hand-tracking.md)
