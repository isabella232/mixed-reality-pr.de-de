---
ms.openlocfilehash: 23bba22801f61f6b4814991c8b3bde68d2c5f6b7
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002697"
---
# <a name="425"></a>[<span data-ttu-id="4b159-101">4.25</span><span class="sxs-lookup"><span data-stu-id="4b159-101">4.25</span></span>](#tab/425)

<span data-ttu-id="4b159-102">Um Hand Abdrücke in Blaupausen zu verwenden, suchen Sie nach den Aktionen unter **Windows Mixed Reality HMD**:</span><span class="sxs-lookup"><span data-stu-id="4b159-102">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Hand Strahlen-BP](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="4b159-104">Wenn Sie in C++ auf Sie zugreifen möchten, schließen Sie am `WindowsMixedRealityFunctionLibrary.h` Anfang der aufrufenden Codedatei ein.</span><span class="sxs-lookup"><span data-stu-id="4b159-104">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="4b159-105">Enum</span><span class="sxs-lookup"><span data-stu-id="4b159-105">Enum</span></span>

<span data-ttu-id="4b159-106">Sie haben auch Zugriff auf die Eingabe Fälle unter **ehmdinputcontrollerbuttons**, die in Blaupausen verwendet werden können:</span><span class="sxs-lookup"><span data-stu-id="4b159-106">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Eingabe Controller-Schaltflächen](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="4b159-108">Verwenden Sie für den Zugriff in C++ die `EHMDInputControllerButtons` Enumerationsklasse:</span><span class="sxs-lookup"><span data-stu-id="4b159-108">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="4b159-109">Im folgenden finden Sie eine Aufschlüsselung der beiden anwendbaren Aufzählungs Fälle:</span><span class="sxs-lookup"><span data-stu-id="4b159-109">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="4b159-110">**Select** -User hat Select-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="4b159-110">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="4b159-111">Ausgelöst in hololens 2 durch Luft tippen, Überblicks und Commit oder durch "Select" mit aktivierter [Spracheingabe](../unreal-voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="4b159-111">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="4b159-112">Das von Benutzern ausgelöste Ereignis **zum Erfassen von** Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="4b159-112">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="4b159-113">Wird in hololens 2 ausgelöst, indem die Finger des Benutzers in einem Hologram geschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="4b159-113">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="4b159-114">Sie können auf den Überwachungs Status Ihres Hand Netzes in C++ über die unten gezeigte Aufzählung zugreifen `EHMDTrackingStatus` :</span><span class="sxs-lookup"><span data-stu-id="4b159-114">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="4b159-115">Im folgenden finden Sie eine Aufschlüsselung der beiden anwendbaren Aufzählungs Fälle:</span><span class="sxs-lookup"><span data-stu-id="4b159-115">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="4b159-116">**Notverfolgt** – die Hand ist nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="4b159-116">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="4b159-117">Nach **verfolgte** –: die Hand ist vollständig nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="4b159-117">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="4b159-118">Struktur</span><span class="sxs-lookup"><span data-stu-id="4b159-118">Struct</span></span>

<span data-ttu-id="4b159-119">Die pointerposeinfo-Struktur kann Ihnen Informationen zu den folgenden Daten liefern:</span><span class="sxs-lookup"><span data-stu-id="4b159-119">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="4b159-120">**Ursprung** – Ursprung der Hand</span><span class="sxs-lookup"><span data-stu-id="4b159-120">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="4b159-121">**Richtung** – Richtung der Hand</span><span class="sxs-lookup"><span data-stu-id="4b159-121">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="4b159-122">**Up** – Up Vector of the Hand</span><span class="sxs-lookup"><span data-stu-id="4b159-122">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="4b159-123">**Ausrichtung** – Ausrichtung Quaternion</span><span class="sxs-lookup"><span data-stu-id="4b159-123">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="4b159-124">**Überwachungs Status** – aktueller Überwachungs Status</span><span class="sxs-lookup"><span data-stu-id="4b159-124">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="4b159-125">Sie können auf die pointerposeinfo-Struktur über Blaupausen zugreifen, wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="4b159-125">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![Zeiger stellen Informationen BP dar](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="4b159-127">Oder mit C++:</span><span class="sxs-lookup"><span data-stu-id="4b159-127">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="4b159-128">Functions</span><span class="sxs-lookup"><span data-stu-id="4b159-128">Functions</span></span>

<span data-ttu-id="4b159-129">Alle unten aufgeführten Funktionen können für jeden Frame aufgerufen werden, der eine kontinuierliche Überwachung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="4b159-129">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="4b159-130">**Get Pointer Pose Info** gibt alle Informationen über die Richtung des Hand Gers im aktuellen Frame zurück.</span><span class="sxs-lookup"><span data-stu-id="4b159-130">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="4b159-131">Karte</span><span class="sxs-lookup"><span data-stu-id="4b159-131">Blueprint:</span></span>

![Informationen zum Darstellen von Zeigern](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="4b159-133">C++:</span><span class="sxs-lookup"><span data-stu-id="4b159-133">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="4b159-134">**Ist** "-Wert" gibt "true" zurück, wenn die Hand im aktuellen Frame erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="4b159-134">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="4b159-135">Karte</span><span class="sxs-lookup"><span data-stu-id="4b159-135">Blueprint:</span></span>

![Erfasste BP](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="4b159-137">C++:</span><span class="sxs-lookup"><span data-stu-id="4b159-137">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="4b159-138">**Ist SELECT gedrückt** gibt true zurück, wenn der Benutzer SELECT im aktuellen Frame ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="4b159-138">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="4b159-139">Karte</span><span class="sxs-lookup"><span data-stu-id="4b159-139">Blueprint:</span></span>

![Ist SELECT-Taste für BP](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="4b159-141">C++:</span><span class="sxs-lookup"><span data-stu-id="4b159-141">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="4b159-142">**Wird auf die Schaltfläche "wird geklickt** " zurückgegeben, wenn das Ereignis oder die Schaltfläche im aktuellen Frame ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="4b159-142">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="4b159-143">Karte</span><span class="sxs-lookup"><span data-stu-id="4b159-143">Blueprint:</span></span>

![Ist Schaltfläche, auf die ein](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="4b159-145">C++:</span><span class="sxs-lookup"><span data-stu-id="4b159-145">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="4b159-146">**Get Controller Tracking Status** gibt den verfolgungsstatus im aktuellen Frame zurück.</span><span class="sxs-lookup"><span data-stu-id="4b159-146">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="4b159-147">Karte</span><span class="sxs-lookup"><span data-stu-id="4b159-147">Blueprint:</span></span>

![Controller-Überwachungs Status-BP erhalten](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="4b159-149">C++:</span><span class="sxs-lookup"><span data-stu-id="4b159-149">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
# <a name="426"></a>[<span data-ttu-id="4b159-150">4.26</span><span class="sxs-lookup"><span data-stu-id="4b159-150">4.26</span></span>](#tab/426)

<span data-ttu-id="4b159-151">Um die Daten für die Hand-Strahlen zu erhalten, sollten Sie die Get Motion Controller-Daten Funktion aus dem vorherigen Abschnitt verwenden.</span><span class="sxs-lookup"><span data-stu-id="4b159-151">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="4b159-152">Die zurückgegebene Struktur enthält zwei Parameter, die Sie verwenden können, um eine Hand Strahl-– **Ziel Position** und **Ziel Drehung** zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4b159-152">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="4b159-153">Diese Parameter bilden einen Strahl, der von Ihrem Bogen gesteuert wird.</span><span class="sxs-lookup"><span data-stu-id="4b159-153">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="4b159-154">Sie sollten diese übernehmen und ein – Hologramm finden, auf das verweist.</span><span class="sxs-lookup"><span data-stu-id="4b159-154">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="4b159-155">Im folgenden finden Sie ein Beispiel für die Bestimmung, ob ein Hand Strahl auf ein Widget trifft und ein benutzerdefiniertes Treffer Ergebnis festlegt:</span><span class="sxs-lookup"><span data-stu-id="4b159-155">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![Blaupause der Get Motion Controller-Daten Funktion](../images/unreal-hand-tracking-img-04.png) 