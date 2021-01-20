---
ms.openlocfilehash: 21c29b2c8d540378259200cc834f7a36065f8ab3
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581107"
---
# <a name="426"></a>[<span data-ttu-id="53327-101">4.26</span><span class="sxs-lookup"><span data-stu-id="53327-101">4.26</span></span>](#tab/426)

<span data-ttu-id="53327-102">Die Hierarchie wird von `EHandKeypoint` enum beschrieben:</span><span class="sxs-lookup"><span data-stu-id="53327-102">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![Bild der Hand-Optionen für "keypoint bluprint"](../images/hand-keypoint-bp.png)

<span data-ttu-id="53327-104">Mithilfe der **Get Motion Controller-Daten** Funktion können Sie all diese Daten aus den Händen eines Benutzers erhalten.</span><span class="sxs-lookup"><span data-stu-id="53327-104">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="53327-105">Diese Funktion gibt eine **xrmutioncontrollerdata** -Struktur zurück.</span><span class="sxs-lookup"><span data-stu-id="53327-105">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="53327-106">Im folgenden finden Sie ein Beispielskript für eine Blaupause, das die xrmutioncontrollerdata-Struktur analysiert, um Handgelenk Positionen zu erhalten und ein debugkoordinaten System an den Positionen der einzelnen gemeinsamen Standorte zeichnet.</span><span class="sxs-lookup"><span data-stu-id="53327-106">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![Blaupause der get-Daten Funktion für den Blick an die Zeilen Ablauf Verfolgung nach Kanal Funktion](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="53327-108">Es ist wichtig, zu überprüfen, ob die Struktur gültig ist und dass Sie eine Hand ist.</span><span class="sxs-lookup"><span data-stu-id="53327-108">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="53327-109">Andernfalls erhalten Sie möglicherweise nicht definiertes Verhalten beim Zugriff auf Positionen, Rotationen und Radien-Arrays.</span><span class="sxs-lookup"><span data-stu-id="53327-109">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>

# <a name="425"></a>[<span data-ttu-id="53327-110">4.25</span><span class="sxs-lookup"><span data-stu-id="53327-110">4.25</span></span>](#tab/425)

<span data-ttu-id="53327-111">Die `EWMRHandKeypoint` -Enumeration beschreibt die Knochen Hierarchie der Hand.</span><span class="sxs-lookup"><span data-stu-id="53327-111">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="53327-112">Sie finden jeden Hand-keypoint, der in ihren Blaupausen aufgeführt ist:</span><span class="sxs-lookup"><span data-stu-id="53327-112">You can find each hand keypoint listed in your Blueprints:</span></span>

![Hand-keypoint-BP](../images/hand-keypoint-bp.png)

<span data-ttu-id="53327-114">Die vollständige C++-Aufzählung ist im folgenden aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="53327-114">The full C++ enum is listed below:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

<span data-ttu-id="53327-115">Sie können die numerischen Werte für jeden enumerationsfall in der Tabelle " [Windows. perception. People. handjointkind](/uwp/api/windows.perception.people.handjointkind) " finden.</span><span class="sxs-lookup"><span data-stu-id="53327-115">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="53327-116">Unterstützende Hand Verfolgung</span><span class="sxs-lookup"><span data-stu-id="53327-116">Supporting Hand Tracking</span></span>

<span data-ttu-id="53327-117">Sie können die Hand Verfolgung in Blaupausen verwenden, indem Sie die Hand Verfolgung von Hand Nachverfolgung **> Windows Mixed Reality** **Hinzufügen** :</span><span class="sxs-lookup"><span data-stu-id="53327-117">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![Hand Tracking-BP](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="53327-119">Diese Funktion gibt zurück, `true` Wenn die Hand Verfolgung auf dem Gerät unterstützt wird und die `false` Hand Nachverfolgung nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="53327-119">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![Unterstützt die Hand Überwachung von BP](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="53327-121">C++:</span><span class="sxs-lookup"><span data-stu-id="53327-121">C++:</span></span>

<span data-ttu-id="53327-122">Schließen Sie `WindowsMixedRealityHandTrackingFunctionLibrary.h` ein.</span><span class="sxs-lookup"><span data-stu-id="53327-122">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="53327-123">Erhalten von Hand Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="53327-123">Getting Hand Tracking</span></span>

<span data-ttu-id="53327-124">Mit **gethandjointtransform** können Sie räumliche Daten von Hand zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="53327-124">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="53327-125">Die Daten aktualisieren jeden Frame, aber wenn Sie sich innerhalb eines Frames befinden, werden die zurückgegebenen Werte zwischengespeichert.</span><span class="sxs-lookup"><span data-stu-id="53327-125">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="53327-126">Es wird aus Leistungsgründen nicht empfohlen, in dieser Funktion eine hohe Logik zu haben.</span><span class="sxs-lookup"><span data-stu-id="53327-126">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![Hand Gelenk Transformation](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="53327-128">C++:</span><span class="sxs-lookup"><span data-stu-id="53327-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="53327-129">Im folgenden finden Sie eine Aufschlüsselung der Funktionsparameter von gethandjointtransform:</span><span class="sxs-lookup"><span data-stu-id="53327-129">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="53327-130">**Hand** – kann die Benutzer Links oder rechts sein.</span><span class="sxs-lookup"><span data-stu-id="53327-130">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="53327-131">**Keypoint** – der Knochen der Hand.</span><span class="sxs-lookup"><span data-stu-id="53327-131">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="53327-132">**Transformation** – Koordinaten und Ausrichtung der Basis von Bone.</span><span class="sxs-lookup"><span data-stu-id="53327-132">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="53327-133">Sie können die Basis des nächsten Knochens anfordern, um die Transformations Daten für das Ende eines Knochens zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="53327-133">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="53327-134">Ein spezieller Tip-Bone gibt das Ende der distal-Tabelle an.</span><span class="sxs-lookup"><span data-stu-id="53327-134">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="53327-135">\* \* Radius – Radius der Basis des-Knochens.</span><span class="sxs-lookup"><span data-stu-id="53327-135">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="53327-136">\* \* Rückgabewert – true, wenn der Rahmen dieses Frames nachverfolgt wird, false, wenn der Knochen nicht nachverfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="53327-136">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>