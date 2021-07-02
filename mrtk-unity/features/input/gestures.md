---
title: Gesten
description: Docummentation on Gestures and its events in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Gesten,
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176882"
---
# <a name="gestures"></a><span data-ttu-id="ff712-104">Gesten</span><span class="sxs-lookup"><span data-stu-id="ff712-104">Gestures</span></span>

<span data-ttu-id="ff712-105">Gesten sind Eingabeereignisse, die auf menschlichen Händen basieren.</span><span class="sxs-lookup"><span data-stu-id="ff712-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="ff712-106">Es gibt zwei Arten von Geräten, die Gesteneingabeereignisse im MRTK auslösen:</span><span class="sxs-lookup"><span data-stu-id="ff712-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="ff712-107">Windows Mixed Reality Geräte wie HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ff712-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="ff712-108">Dies beschreibt das Eindrüpfen von Bewegungen ("Tippen in die Luft") und tipp-and-hold-Gesten.</span><span class="sxs-lookup"><span data-stu-id="ff712-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="ff712-109">Weitere Informationen zu HoloLens Gesten finden Sie in der [Dokumentation zu Windows Mixed Reality Gesten.](/windows/mixed-reality/gestures)</span><span class="sxs-lookup"><span data-stu-id="ff712-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="ff712-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)umschließt unity [XR. WSA. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) zum Nutzen der Gestenereignisse von Unity von HoloLens Geräten.</span><span class="sxs-lookup"><span data-stu-id="ff712-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="ff712-111">Touchscreengeräte.</span><span class="sxs-lookup"><span data-stu-id="ff712-111">Touch screen devices.</span></span>

  <span data-ttu-id="ff712-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) umschließt die [Unity Touch-Klasse,](https://docs.unity3d.com/ScriptReference/Touch.html) die physische Touchscreens unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ff712-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="ff712-113">Beide Eingabequellen verwenden das _Gestenprofil Einstellungen,_ um die Touch- bzw. Gestenereignisse von Unity in die [Eingabeaktionen](input-actions.md)des MRTK zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="ff712-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](input-actions.md).</span></span> <span data-ttu-id="ff712-114">Dieses Profil finden Sie unter dem _Profil Eingabesystem Einstellungen._</span><span class="sxs-lookup"><span data-stu-id="ff712-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a><span data-ttu-id="ff712-115">Gestikereignisse</span><span class="sxs-lookup"><span data-stu-id="ff712-115">Gesture events</span></span>

<span data-ttu-id="ff712-116">Gestenereignisse werden empfangen, indem eine der Gestenhandlerschnittstellen implementiert wird: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) oder [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (siehe Tabelle der [Ereignishandler](input-events.md)).</span><span class="sxs-lookup"><span data-stu-id="ff712-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](input-events.md)).</span></span>

<span data-ttu-id="ff712-117">Eine Beispielimplementierungen eines Gestenereignishandlers finden Sie unter [Beispielszene.](#example-scene)</span><span class="sxs-lookup"><span data-stu-id="ff712-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="ff712-118">Beim Implementieren der generischen Version können die Ereignisse *OnGestureCompleted* und *OnGestureUpdated* typisierte Daten der folgenden Typen empfangen:</span><span class="sxs-lookup"><span data-stu-id="ff712-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="ff712-119">`Vector2` – 2D-Positionsgeste.</span><span class="sxs-lookup"><span data-stu-id="ff712-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="ff712-120">Wird von Touchscreens erstellt, um über ihre zu [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) informieren.</span><span class="sxs-lookup"><span data-stu-id="ff712-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="ff712-121">`Vector3` – 3D-Positionsgeste.</span><span class="sxs-lookup"><span data-stu-id="ff712-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="ff712-122">Erstellt von HoloLens zur Information über:</span><span class="sxs-lookup"><span data-stu-id="ff712-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="ff712-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) eines Manipulationsereignisses</span><span class="sxs-lookup"><span data-stu-id="ff712-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="ff712-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) eines Navigationsereignisses</span><span class="sxs-lookup"><span data-stu-id="ff712-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="ff712-125">`Quaternion` – 3D-Drehbewegung.</span><span class="sxs-lookup"><span data-stu-id="ff712-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="ff712-126">Verfügbar für benutzerdefinierte Eingabequellen, aber derzeit nicht von vorhandenen Quellen erstellt.</span><span class="sxs-lookup"><span data-stu-id="ff712-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="ff712-127">`MixedRealityPose` – Kombinierte 3D-Geste für Position/Drehung.</span><span class="sxs-lookup"><span data-stu-id="ff712-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="ff712-128">Verfügbar für benutzerdefinierte Eingabequellen, aber derzeit nicht von vorhandenen Quellen erstellt.</span><span class="sxs-lookup"><span data-stu-id="ff712-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="ff712-129">Reihenfolge der Ereignisse</span><span class="sxs-lookup"><span data-stu-id="ff712-129">Order of events</span></span>

<span data-ttu-id="ff712-130">Je nach Benutzereingabe gibt es zwei Hauptketten von Ereignissen:</span><span class="sxs-lookup"><span data-stu-id="ff712-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="ff712-131">"Hold":</span><span class="sxs-lookup"><span data-stu-id="ff712-131">"Hold":</span></span>
    1. <span data-ttu-id="ff712-132">Halten Sie tippen:</span><span class="sxs-lookup"><span data-stu-id="ff712-132">Hold tap:</span></span>
        - <span data-ttu-id="ff712-133">Manipulation  starten</span><span class="sxs-lookup"><span data-stu-id="ff712-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="ff712-134">Tippen Sie über [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)hinaus:</span><span class="sxs-lookup"><span data-stu-id="ff712-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="ff712-135">Start _Hold (Halten)_</span><span class="sxs-lookup"><span data-stu-id="ff712-135">start _Hold_</span></span>
    1. <span data-ttu-id="ff712-136">Tippen Sie auf Release:</span><span class="sxs-lookup"><span data-stu-id="ff712-136">Release tap:</span></span>
        - <span data-ttu-id="ff712-137">Complete _Hold_</span><span class="sxs-lookup"><span data-stu-id="ff712-137">complete _Hold_</span></span>
        - <span data-ttu-id="ff712-138">vollständige _Bearbeitung_</span><span class="sxs-lookup"><span data-stu-id="ff712-138">complete _Manipulation_</span></span>

- <span data-ttu-id="ff712-139">"Move":</span><span class="sxs-lookup"><span data-stu-id="ff712-139">"Move":</span></span>
    1. <span data-ttu-id="ff712-140">Halten Sie tippen:</span><span class="sxs-lookup"><span data-stu-id="ff712-140">Hold tap:</span></span>
        - <span data-ttu-id="ff712-141">Manipulation  starten</span><span class="sxs-lookup"><span data-stu-id="ff712-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="ff712-142">Tippen Sie über [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)hinaus:</span><span class="sxs-lookup"><span data-stu-id="ff712-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="ff712-143">Start _Hold (Halten)_</span><span class="sxs-lookup"><span data-stu-id="ff712-143">start _Hold_</span></span>
    1. <span data-ttu-id="ff712-144">Bewegen Sie die Hand über [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)hinaus:</span><span class="sxs-lookup"><span data-stu-id="ff712-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="ff712-145">_Abbrechen der Zurückhaltung_</span><span class="sxs-lookup"><span data-stu-id="ff712-145">cancel _Hold_</span></span>
        - <span data-ttu-id="ff712-146">Navigation  starten</span><span class="sxs-lookup"><span data-stu-id="ff712-146">start _Navigation_</span></span>
    1. <span data-ttu-id="ff712-147">Tippen Sie auf Release:</span><span class="sxs-lookup"><span data-stu-id="ff712-147">Release tap:</span></span>
        - <span data-ttu-id="ff712-148">vollständige _Bearbeitung_</span><span class="sxs-lookup"><span data-stu-id="ff712-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="ff712-149">vollständige _Navigation_</span><span class="sxs-lookup"><span data-stu-id="ff712-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="ff712-150">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="ff712-150">Example scene</span></span>

<span data-ttu-id="ff712-151">Die **Szene HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) zeigt, wie der Zeiger Result verwendet wird, um ein Objekt an der Trefferposition zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ff712-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="ff712-152">Das `GestureTester` Skript (Assets/MRTK/Examples/Demos/HandTracking/Script) ist eine Beispielimplementierung zum Visualisieren von Gestenereignissen über GameObjects.</span><span class="sxs-lookup"><span data-stu-id="ff712-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="ff712-153">Die Handlerfunktionen ändern die Farbe von Indikatorobjekten und zeigen das letzte aufgezeichnete Ereignis in Textobjekten in der Szene an.</span><span class="sxs-lookup"><span data-stu-id="ff712-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>
