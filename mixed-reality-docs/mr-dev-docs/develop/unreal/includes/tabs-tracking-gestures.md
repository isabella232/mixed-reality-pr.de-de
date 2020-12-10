---
ms.openlocfilehash: 50b56f6f081f682c3f3655e81aa492d84d254314
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002657"
---
# <a name="425"></a>[4.25](#tab/425)

Sie finden die Blueprint-Funktion in unter **Windows Mixed Reality Spatial Input** und die C++-Funktion, indem Sie `WindowsMixedRealitySpatialInputFunctionLibrary.h` Ihre aufrufende Codedatei hinzufügen.

![Erfassungs Gesten](../images/unreal/capture-gestures.png)

### <a name="enum"></a>Enum
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Karte

![Gesten-Typ](../images/unreal/gesture-type.png)

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
Sie können die Gesten Erfassung mit der-Funktion aktivieren und deaktivieren `CaptureGestures` . Wenn eine aktivierte Geste Eingabeereignisse auslöst, gibt die Funktion zurück, `true` Wenn die Gesten Erfassung erfolgreich war, und, `false` Wenn ein Fehler vorliegt.

Karte

![Erfassungs Gesten BP](../images/unreal/capture-gestures-bp.png)

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

Im folgenden finden Sie wichtige Ereignisse, die in Blueprints und C++: Key-Ereignisse zu finden sind. ![](../images/unreal/key-events.png)

![Schlüsselereignisse 2](../images/unreal/key-events2.png)
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

# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![Blaupause für Ereignis BEGIN Play Connected to configure Gesten Function](../images/unreal-hand-tracking-img-09.png)

Anschließend sollten Sie Code hinzufügen, um die folgenden Ereignisse zu abonnieren:

![Blaupause von Windows Spatial Input, Tap und Left Manipulation Gesten ](../images/unreal/key-events.png)
 ![ Screenshot der Optionen für die Eingabe von räumlichen Eingaben in Windows im Detail Panel](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

In openxr werden Gesten Ereignisse über die Eingabe Pipeline nachverfolgt. Mithilfe von Hand Interaktion kann das Gerät Tap-und Hold-Gesten automatisch erkennen, aber nicht die anderen. Sie werden als openxrmsf thandinteraktion SELECT-und Zieh Zuordnungen benannt. Sie müssen das Abonnement nicht aktivieren. Sie sollten die Ereignisse wie folgt in Project Settings/Engine/Input deklarieren:

![Screenshot der openxr-Aktions Zuordnungen](../images/unreal-hand-tracking-img-12.png)
