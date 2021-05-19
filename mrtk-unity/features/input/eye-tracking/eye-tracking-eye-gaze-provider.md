---
title: 'Eyetracking (Blickverfolgung): Anbieter für Anvisieren (Gaze)'
description: Dokumentation für den Eye Gaze-Anbieter in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking, EyeTracke,
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144019"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a><span data-ttu-id="98d36-104">Zugreifen auf Eye-Tracking-Daten in Ihrem Unity-Skript</span><span class="sxs-lookup"><span data-stu-id="98d36-104">Accessing eye tracking data in your Unity script</span></span>

<span data-ttu-id="98d36-105">In diesem Artikel wird davon ausgegangen, dass Sie über Kenntnisse zum Einrichten der Eyetracking in einer MRTK-Szene (siehe Grundlegende MRTK-Einrichtung zur Verwendung von [EyeTracking) verfügt.](eye-tracking-basic-setup.md)</span><span class="sxs-lookup"><span data-stu-id="98d36-105">This article assumes one has understanding for setting up eye tracking in an MRTK scene (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)).</span></span>
<span data-ttu-id="98d36-106">Der Zugriff auf Eye-Tracking-Daten in einem MonoBehaviour-Skript ist einfach!</span><span class="sxs-lookup"><span data-stu-id="98d36-106">Accessing eye tracking data in a MonoBehaviour script is easy!</span></span> <span data-ttu-id="98d36-107">Verwenden Sie *einfach CoreServices.InputSystem.EyeAnbieter.*</span><span class="sxs-lookup"><span data-stu-id="98d36-107">Simply use *CoreServices.InputSystem.EyeGazeProvider*.</span></span>

## <a name="imixedrealityeyegazeprovider"></a><span data-ttu-id="98d36-108">IMixedRealityEyeProvider</span><span class="sxs-lookup"><span data-stu-id="98d36-108">IMixedRealityEyeGazeProvider</span></span>

<span data-ttu-id="98d36-109">Die Eyetrackingkonfiguration im MRTK wird über die -Schnittstelle [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="98d36-109">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span> <span data-ttu-id="98d36-110">Die [Verwendung von CoreServices.InputSystem.EyeProvider](eye-tracking-eye-gaze-provider.md) stellt die Standardmäßige Implementierung des Anvierungsanbieters bereit, die zur Laufzeit im Toolkit registriert ist.</span><span class="sxs-lookup"><span data-stu-id="98d36-110">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span>
<span data-ttu-id="98d36-111">Im Folgenden werden nützliche `EyeGazeProvider` Eigenschaften von beschrieben.</span><span class="sxs-lookup"><span data-stu-id="98d36-111">Useful properties of the `EyeGazeProvider` is outlined below.</span></span>

- <span data-ttu-id="98d36-112">**IsEyeTrackingEnabled:** True, wenn der Benutzer ausgewählt hat, eye tracking für das Anvieren zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="98d36-112">**IsEyeTrackingEnabled**: True if user has selected to use eye tracking for gaze.</span></span>

- <span data-ttu-id="98d36-113">**IsEyeCalibrationValid:** Gibt an, ob die Eyetracking-Kalibrierung des Benutzers gültig ist.</span><span class="sxs-lookup"><span data-stu-id="98d36-113">**IsEyeCalibrationValid**: Indicates whether the user's eye tracking calibration is valid or not.</span></span>
<span data-ttu-id="98d36-114">Sie gibt "NULL" zurück, wenn der Wert noch keine Daten vom Eyetrackingsystem empfangen hat.</span><span class="sxs-lookup"><span data-stu-id="98d36-114">It returns 'null', if the value has not yet received data from the eye tracking system.</span></span>
<span data-ttu-id="98d36-115">Es kann ungültig sein, da der Benutzer die Eyetracking-Kalibrierung übersprungen hat.</span><span class="sxs-lookup"><span data-stu-id="98d36-115">It may be invalid, because the user skipped the eye tracking calibration.</span></span>

- <span data-ttu-id="98d36-116">**IsEyeTrackingEnabledAndValid:** Gibt an, ob die aktuellen Eyetrackingdaten derzeit für anvisiert werden.</span><span class="sxs-lookup"><span data-stu-id="98d36-116">**IsEyeTrackingEnabledAndValid**: Indicates whether the current eye tracking data is currently been used for gaze.</span></span>

- <span data-ttu-id="98d36-117">**IsEyeTrackingDataValid:** True, wenn Eyetrackingdaten verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="98d36-117">**IsEyeTrackingDataValid**: True if eye tracking data is available.</span></span>
<span data-ttu-id="98d36-118">Sie ist möglicherweise nicht verfügbar, weil ein Timeout überschritten wurde (sollte jedoch robust sein, wenn der Benutzer blinkt) oder aufgrund fehlender Hardware oder Berechtigungen zur Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="98d36-118">It may be unavailable due to exceeded timeout (should be robust to the user blinking though) or lack of tracking hardware or permissions.</span></span>
<span data-ttu-id="98d36-119">Sehen Sie sich unser [Beispiel zur Benachrichtigung](eye-tracking-is-user-calibrated.md) über fehlende Augen kalibrierung an, in dem erläutert wird, wie Sie erkennen können, ob ein Benutzer mit den Augen kalibriert ist, und um eine entsprechende Benachrichtigung zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="98d36-119">Check out our [Missing eye calibration notification sample](eye-tracking-is-user-calibrated.md) that explains how to detect whether a user is eye calibrated and to show an appropriate notification.</span></span>

- <span data-ttu-id="98d36-120">**GazeOrigin:** Ursprung des Anvistikstrahls.</span><span class="sxs-lookup"><span data-stu-id="98d36-120">**GazeOrigin**: Origin of the gaze ray.</span></span>
<span data-ttu-id="98d36-121">Beachten Sie, dass  dadurch der Ursprung des Anvierens mit dem Kopf zurückgegeben wird, wenn "IsEyeEyeEyeeValid" false ist.</span><span class="sxs-lookup"><span data-stu-id="98d36-121">Please note that this will return the *head* gaze origin if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="98d36-122">**GazeDirection:** Richtung des Anvischen-Strahls.</span><span class="sxs-lookup"><span data-stu-id="98d36-122">**GazeDirection**: Direction of the gaze ray.</span></span>
<span data-ttu-id="98d36-123">Dadurch wird die Richtung des Anvierens mit dem *Kopf* zurückgegeben, wenn "IsEyeGazeValid" false ist.</span><span class="sxs-lookup"><span data-stu-id="98d36-123">This will return the *head* gaze direction if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="98d36-124">**HitInfo,** **HitPosition,** **HitNormal** usw.: Informationen zum derzeit anvisierten Ziel.</span><span class="sxs-lookup"><span data-stu-id="98d36-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: Information about the currently gazed at target.</span></span>
<span data-ttu-id="98d36-125">Auch wenn `IsEyeGazeValid` false ist, basiert dies auf dem Anverweisen mit dem *Kopf* des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="98d36-125">Again, if `IsEyeGazeValid` is false, this will be based on the user's *head* gaze.</span></span>

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a><span data-ttu-id="98d36-126">Beispiele für die Verwendung von CoreServices.InputSystem.EyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="98d36-126">Examples for using CoreServices.InputSystem.EyeGazeProvider</span></span>

<span data-ttu-id="98d36-127">Hier sehen Sie ein Beispiel aus [followEyeGaze.cs:](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)</span><span class="sxs-lookup"><span data-stu-id="98d36-127">Here is an example from the [FollowEyeGaze.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span></span>

- <span data-ttu-id="98d36-128">Abrufen des Punkts eines Hologramms, das der Benutzer ansieht:</span><span class="sxs-lookup"><span data-stu-id="98d36-128">Get the point of a hologram that the user is looking at:</span></span>

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- <span data-ttu-id="98d36-129">Anzeigen eines visuellen Medienobjekts in einem festen Abstand von dem Ort, an dem der Benutzer gerade sucht:</span><span class="sxs-lookup"><span data-stu-id="98d36-129">Showing a visual asset at a fixed distance from where the user is currently looking:</span></span>

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a><span data-ttu-id="98d36-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="98d36-130">See also</span></span>

- [<span data-ttu-id="98d36-131">MRTK Eye Tracking Overview</span><span class="sxs-lookup"><span data-stu-id="98d36-131">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="98d36-132">MRTK Eye Tracking-Setup</span><span class="sxs-lookup"><span data-stu-id="98d36-132">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="98d36-133">MRTK Eye Tracking Calibration</span><span class="sxs-lookup"><span data-stu-id="98d36-133">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="98d36-134">Dokumentation zur HoloLens 2 Eyetracking</span><span class="sxs-lookup"><span data-stu-id="98d36-134">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)