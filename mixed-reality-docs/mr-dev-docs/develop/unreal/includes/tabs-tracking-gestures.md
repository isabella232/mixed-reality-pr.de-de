---
ms.openlocfilehash: 50b56f6f081f682c3f3655e81aa492d84d254314
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002657"
---
# <a name="425"></a>[<span data-ttu-id="4bc3a-101">4.25</span><span class="sxs-lookup"><span data-stu-id="4bc3a-101">4.25</span></span>](#tab/425)

<span data-ttu-id="4bc3a-102">Sie finden die Blueprint-Funktion in unter **Windows Mixed Reality Spatial Input** und die C++-Funktion, indem Sie `WindowsMixedRealitySpatialInputFunctionLibrary.h` Ihre aufrufende Codedatei hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4bc3a-102">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Erfassungs Gesten](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="4bc3a-104">Enum</span><span class="sxs-lookup"><span data-stu-id="4bc3a-104">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="4bc3a-105">Karte</span><span class="sxs-lookup"><span data-stu-id="4bc3a-105">Blueprint:</span></span>

![Gesten-Typ](../images/unreal/gesture-type.png)

<span data-ttu-id="4bc3a-107">C++:</span><span class="sxs-lookup"><span data-stu-id="4bc3a-107">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="4bc3a-108">Funktion</span><span class="sxs-lookup"><span data-stu-id="4bc3a-108">Function</span></span>
<span data-ttu-id="4bc3a-109">Sie können die Gesten Erfassung mit der-Funktion aktivieren und deaktivieren `CaptureGestures` .</span><span class="sxs-lookup"><span data-stu-id="4bc3a-109">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="4bc3a-110">Wenn eine aktivierte Geste Eingabeereignisse auslöst, gibt die Funktion zurück, `true` Wenn die Gesten Erfassung erfolgreich war, und, `false` Wenn ein Fehler vorliegt.</span><span class="sxs-lookup"><span data-stu-id="4bc3a-110">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="4bc3a-111">Karte</span><span class="sxs-lookup"><span data-stu-id="4bc3a-111">Blueprint:</span></span>

![Erfassungs Gesten BP](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="4bc3a-113">C++:</span><span class="sxs-lookup"><span data-stu-id="4bc3a-113">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="4bc3a-114">Im folgenden finden Sie wichtige Ereignisse, die in Blueprints und C++: Key-Ereignisse zu finden sind. ![](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="4bc3a-114">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

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

# <a name="426"></a>[<span data-ttu-id="4bc3a-116">4.26</span><span class="sxs-lookup"><span data-stu-id="4bc3a-116">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="4bc3a-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4bc3a-117">Windows Mixed Reality</span></span>

![Blaupause für Ereignis BEGIN Play Connected to configure Gesten Function](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="4bc3a-119">Anschließend sollten Sie Code hinzufügen, um die folgenden Ereignisse zu abonnieren:</span><span class="sxs-lookup"><span data-stu-id="4bc3a-119">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="4bc3a-120">![Blaupause von Windows Spatial Input, Tap und Left Manipulation Gesten ](../images/unreal/key-events.png)
 ![ Screenshot der Optionen für die Eingabe von räumlichen Eingaben in Windows im Detail Panel](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="4bc3a-120">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="4bc3a-121">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4bc3a-121">OpenXR</span></span>

<span data-ttu-id="4bc3a-122">In openxr werden Gesten Ereignisse über die Eingabe Pipeline nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="4bc3a-122">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="4bc3a-123">Mithilfe von Hand Interaktion kann das Gerät Tap-und Hold-Gesten automatisch erkennen, aber nicht die anderen.</span><span class="sxs-lookup"><span data-stu-id="4bc3a-123">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="4bc3a-124">Sie werden als openxrmsf thandinteraktion SELECT-und Zieh Zuordnungen benannt.</span><span class="sxs-lookup"><span data-stu-id="4bc3a-124">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="4bc3a-125">Sie müssen das Abonnement nicht aktivieren. Sie sollten die Ereignisse wie folgt in Project Settings/Engine/Input deklarieren:</span><span class="sxs-lookup"><span data-stu-id="4bc3a-125">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![Screenshot der openxr-Aktions Zuordnungen](../images/unreal-hand-tracking-img-12.png)
