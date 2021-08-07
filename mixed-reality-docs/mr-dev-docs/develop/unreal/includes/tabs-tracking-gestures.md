---
ms.openlocfilehash: fa21b1a5c3c89cf3c1c63c7ed8ebbdc3d8547661443853987ee3713e50c50e5c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187412"
---
# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![Blueprint of event begin play connected to configure gestures function](../images/unreal-hand-tracking-img-09.png)

Anschließend sollten Sie Code hinzufügen, um die folgenden Ereignisse zu abonnieren:

![Blaupause Windows gesten für die räumliche Eingabe halten, tippen und links manipulation screenshot of Windows spatial input tap ](../images/unreal/key-events.png)
 ![ gesture options in the details panel](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

In OpenXR werden Gestenereignisse über die Eingabepipeline nachverfolgt. Mithilfe der Handinteraktion kann das Gerät Tipp- und Halten-Gesten automatisch erkennen, aber nicht die anderen. Sie werden als OpenXRMsftHandInteraction Select- und Grip-Zuordnungen bezeichnet. Sie müssen das Abonnement nicht aktivieren. Sie sollten die Ereignisse wie Project Einstellungen/Engine/Input deklarieren:

![Screenshot der OpenXR-Aktionszuordnungen](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[4.25](#tab/425)

Sie finden die Blueprint-Funktion in unter **Windows Mixed Reality Spatial Input** und die C++-Funktion, indem Sie in Ihrer `WindowsMixedRealitySpatialInputFunctionLibrary.h` aufrufenden Codedatei hinzufügen.

![Erfassungsgesten](../images/unreal/capture-gestures.png)

### <a name="enum"></a>Enumeration
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Blueprint:

![Gestentyp](../images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Funktion
Sie können die Gestenerfassung mit der -Funktion aktivieren und `CaptureGestures` deaktivieren. Wenn eine aktivierte Geste Eingabeereignisse ausgibt, gibt die Funktion zurück, wenn die Gestenerfassung erfolgreich war und ein `true` `false` Fehler auftritt.

Blueprint:

![Erfassungsgesten (BP)](../images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

Im Folgenden finden Sie wichtige Ereignisse, die Sie in Blaupausen und C++ finden: ![ Wichtige Ereignisse](../images/unreal/key-events.png)

![Wichtige Ereignisse 2](../images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

