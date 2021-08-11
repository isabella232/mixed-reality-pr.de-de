---
title: Eingabezustand
description: Dokumentation zu Eingabezuständen im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, InputState,
ms.openlocfilehash: 7d5e008ae3e43d227b90a563dd74e65a89527bd7ddf1720e26577042ce0d545f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228360"
---
# <a name="accessing-input-state-in-mrtk"></a>Zugreifen auf den Eingabezustand im MRTK

Es ist möglich, den Status aller Eingaben im MRTK direkt durch Iterieren der Controller zu abfragen, die an die Eingabequellen angefügt sind. MRTK bietet auch praktische Methoden für den Zugriff auf die Position und Drehung der Augen, Hände, des Kopfs und des Bewegungscontrollers.

In der InputDataExample-Szene finden Sie ein Beispiel für das Abfragen von Eingaben sowohl über das Iterieren von Controllern als auch mithilfe der [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) -Klasse.

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>Beispiel: Zugriffsposition, Drehung von Kopf, Händen, Augen im MRTK

Die MRTK-Klasse bietet Benutzerfreundlichkeitsmethoden für den Zugriff auf den Handstrahl, den Kopfstrahl, den Strahl des Anvierens der Augen und die [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) Motion Controller-Lichtstrahl.

```c#
// Get the head ray
var headRay = InputRayUtils.GetHeadGazeRay();

// Get the right hand ray
Ray rightHandRay;
if(InputRayUtils.TryGetHandRay(Handedness.right, rightHandRay))
{
    // Right hand ray is available
}
else
{
    // Right hand ray is not available
}
```

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>Beispiel: Zugriffsposition, Drehung aller in der Szene aktiven 6DOF-Controller

```c#
foreach(var controller in CoreServices.InputSystem.DetectedControllers)
{
    // Interactions for a controller is the list of inputs that this controller exposes
    foreach(MixedRealityInteractionMapping inputMapping in controller.Interactions)
    {
        // 6DOF controllers support the "SpatialPointer" type (pointing direction)
        // or "GripPointer" type (direction of the 6DOF controller)
        if (inputMapping.InputType == DeviceInputType.SpatialPointer)
        {
            Debug.Log("spatial pointer PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial pointer RotationData: " + inputMapping.RotationData);
        }

        if (inputMapping.InputType == DeviceInputType.SpatialGrip)
        {
            Debug.Log("spatial grip PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial grip RotationData: " + inputMapping.RotationData);
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

- [InputEvents](input-events.md)
- [Zeiger](pointers.md)
- [HandTracking](hand-tracking.md)
