---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717725"
---
# <a name="426"></a>[<span data-ttu-id="46056-101">4.26</span><span class="sxs-lookup"><span data-stu-id="46056-101">4.26</span></span>](#tab/426)

<span data-ttu-id="46056-102">Um die Daten für die Hand-Strahlen zu erhalten, sollten Sie die Get Motion Controller-Daten Funktion aus dem vorherigen Abschnitt verwenden.</span><span class="sxs-lookup"><span data-stu-id="46056-102">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="46056-103">Die zurückgegebene Struktur enthält zwei Parameter, die Sie verwenden können, um eine Hand Strahl-– **Ziel Position** und **Ziel Drehung** zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="46056-103">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="46056-104">Diese Parameter bilden einen Strahl, der von Ihrem Bogen gesteuert wird.</span><span class="sxs-lookup"><span data-stu-id="46056-104">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="46056-105">Sie sollten diese übernehmen und ein – Hologramm finden, auf das verweist.</span><span class="sxs-lookup"><span data-stu-id="46056-105">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="46056-106">Im folgenden finden Sie ein Beispiel für die Bestimmung, ob ein Hand Strahl auf ein Widget trifft und ein benutzerdefiniertes Treffer Ergebnis festlegt:</span><span class="sxs-lookup"><span data-stu-id="46056-106">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![Blaupause der Get Motion Controller-Daten Funktion](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[<span data-ttu-id="46056-108">4.25</span><span class="sxs-lookup"><span data-stu-id="46056-108">4.25</span></span>](#tab/425)

<span data-ttu-id="46056-109">Um Hand Abdrücke in Blaupausen zu verwenden, suchen Sie nach den Aktionen unter **Windows Mixed Reality HMD**:</span><span class="sxs-lookup"><span data-stu-id="46056-109">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Hand Strahlen-BP](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="46056-111">Wenn Sie in C++ auf Sie zugreifen möchten, schließen Sie am `WindowsMixedRealityFunctionLibrary.h` Anfang der aufrufenden Codedatei ein.</span><span class="sxs-lookup"><span data-stu-id="46056-111">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="46056-112">Enumeration</span><span class="sxs-lookup"><span data-stu-id="46056-112">Enum</span></span>

<span data-ttu-id="46056-113">Sie haben auch Zugriff auf die Eingabe Fälle unter **ehmdinputcontrollerbuttons**, die in Blaupausen verwendet werden können:</span><span class="sxs-lookup"><span data-stu-id="46056-113">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Eingabe Controller-Schaltflächen](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="46056-115">Verwenden Sie für den Zugriff in C++ die `EHMDInputControllerButtons` Enumerationsklasse:</span><span class="sxs-lookup"><span data-stu-id="46056-115">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="46056-116">Im folgenden finden Sie eine Aufschlüsselung der beiden anwendbaren Aufzählungs Fälle:</span><span class="sxs-lookup"><span data-stu-id="46056-116">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="46056-117">**Select** -User hat Select-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="46056-117">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="46056-118">Ausgelöst in hololens 2 durch Luft tippen, Überblicks und Commit oder durch "Select" mit aktivierter [Spracheingabe](../unreal-voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="46056-118">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="46056-119">Das von Benutzern ausgelöste Ereignis **zum Erfassen von** Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="46056-119">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="46056-120">Wird in hololens 2 ausgelöst, indem die Finger des Benutzers in einem Hologram geschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="46056-120">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="46056-121">Sie können auf den Überwachungs Status Ihres Hand Netzes in C++ über die unten gezeigte Aufzählung zugreifen `EHMDTrackingStatus` :</span><span class="sxs-lookup"><span data-stu-id="46056-121">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="46056-122">Im folgenden finden Sie eine Aufschlüsselung der beiden anwendbaren Aufzählungs Fälle:</span><span class="sxs-lookup"><span data-stu-id="46056-122">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="46056-123">**Notverfolgt** – die Hand ist nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="46056-123">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="46056-124">Nach **verfolgte** –: die Hand ist vollständig nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="46056-124">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="46056-125">Struktur</span><span class="sxs-lookup"><span data-stu-id="46056-125">Struct</span></span>

<span data-ttu-id="46056-126">Die pointerposeinfo-Struktur kann Ihnen Informationen zu den folgenden Daten liefern:</span><span class="sxs-lookup"><span data-stu-id="46056-126">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="46056-127">**Ursprung** – Ursprung der Hand</span><span class="sxs-lookup"><span data-stu-id="46056-127">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="46056-128">**Richtung** – Richtung der Hand</span><span class="sxs-lookup"><span data-stu-id="46056-128">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="46056-129">**Up** – Up Vector of the Hand</span><span class="sxs-lookup"><span data-stu-id="46056-129">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="46056-130">**Ausrichtung** – Ausrichtung Quaternion</span><span class="sxs-lookup"><span data-stu-id="46056-130">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="46056-131">**Überwachungs Status** – aktueller Überwachungs Status</span><span class="sxs-lookup"><span data-stu-id="46056-131">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="46056-132">Sie können auf die pointerposeinfo-Struktur über Blaupausen zugreifen, wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="46056-132">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![Zeiger stellen Informationen BP dar](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="46056-134">Oder mit C++:</span><span class="sxs-lookup"><span data-stu-id="46056-134">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="46056-135">Functions</span><span class="sxs-lookup"><span data-stu-id="46056-135">Functions</span></span>

<span data-ttu-id="46056-136">Alle unten aufgeführten Funktionen können für jeden Frame aufgerufen werden, der eine kontinuierliche Überwachung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="46056-136">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="46056-137">**Get Pointer Pose Info** gibt alle Informationen über die Richtung des Hand Gers im aktuellen Frame zurück.</span><span class="sxs-lookup"><span data-stu-id="46056-137">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="46056-138">Karte</span><span class="sxs-lookup"><span data-stu-id="46056-138">Blueprint:</span></span>

![Informationen zum Darstellen von Zeigern](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="46056-140">C++:</span><span class="sxs-lookup"><span data-stu-id="46056-140">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="46056-141">**Ist** "-Wert" gibt "true" zurück, wenn die Hand im aktuellen Frame erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="46056-141">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="46056-142">Karte</span><span class="sxs-lookup"><span data-stu-id="46056-142">Blueprint:</span></span>

![Erfasste BP](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="46056-144">C++:</span><span class="sxs-lookup"><span data-stu-id="46056-144">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="46056-145">**Ist SELECT gedrückt** gibt true zurück, wenn der Benutzer SELECT im aktuellen Frame ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="46056-145">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="46056-146">Karte</span><span class="sxs-lookup"><span data-stu-id="46056-146">Blueprint:</span></span>

![Ist SELECT-Taste für BP](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="46056-148">C++:</span><span class="sxs-lookup"><span data-stu-id="46056-148">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="46056-149">**Wird auf die Schaltfläche "wird geklickt** " zurückgegeben, wenn das Ereignis oder die Schaltfläche im aktuellen Frame ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="46056-149">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="46056-150">Karte</span><span class="sxs-lookup"><span data-stu-id="46056-150">Blueprint:</span></span>

![Ist Schaltfläche, auf die ein](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="46056-152">C++:</span><span class="sxs-lookup"><span data-stu-id="46056-152">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="46056-153">**Get Controller Tracking Status** gibt den verfolgungsstatus im aktuellen Frame zurück.</span><span class="sxs-lookup"><span data-stu-id="46056-153">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="46056-154">Karte</span><span class="sxs-lookup"><span data-stu-id="46056-154">Blueprint:</span></span>

![Controller-Überwachungs Status-BP erhalten](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="46056-156">C++:</span><span class="sxs-lookup"><span data-stu-id="46056-156">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```