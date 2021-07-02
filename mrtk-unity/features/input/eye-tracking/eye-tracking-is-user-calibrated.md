---
title: Kalibrierung der Augen
description: Einrichten der Kalibrierung der Augen des Benutzers in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking, Kalibrierung,
ms.openlocfilehash: a2023a2d7f6a0254e8fef32f4faf09def956e94f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177202"
---
# <a name="eye-calibration"></a><span data-ttu-id="8cfc3-104">Kalibrierung der Augen</span><span class="sxs-lookup"><span data-stu-id="8cfc3-104">Eye calibration</span></span>

![Screenshot der Benachrichtigung zur Kalibrierung der Augen](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="8cfc3-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="8cfc3-106">Overview</span></span>

<span data-ttu-id="8cfc3-107">Wenn eye tracking ein grundlegender Bestandteil Ihrer App-Erfahrung ist, sollten Sie sicherstellen, dass die Kalibrierung der Augen des Benutzers gültig ist.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="8cfc3-108">Der Hauptgrund dafür, dass er ungültig ist, ist, dass sich der Benutzer entschieden hat, die Eyetracking-Kalibrierung zu überspringen, wenn er auf das Gerät setzt.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="8cfc3-109">Auf dieser Seite wird Folgendes behandelt:</span><span class="sxs-lookup"><span data-stu-id="8cfc3-109">This page covers the following:</span></span>

- <span data-ttu-id="8cfc3-110">Beschreibt, wie erkannt wird, dass ein Benutzer mit den Augen kalibriert ist.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="8cfc3-111">Enthält ein Beispiel für das Auslösen einer Benutzerbenachrichtigung, um den Benutzer anweisen zu lassen, die Kalibrierung der Augen zu durchgehen.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="8cfc3-112">Benachrichtigung automatisch verweisen, wenn die Kalibrierung der Augen gültig wird</span><span class="sxs-lookup"><span data-stu-id="8cfc3-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="8cfc3-113">Manuelles Verdren der Benachrichtigung, wenn der Benutzer sich dafür entscheidet, ohne Kalibrierung fortzufahren</span><span class="sxs-lookup"><span data-stu-id="8cfc3-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="8cfc3-114">Erkennen des Kalibrierungszustands der Augen</span><span class="sxs-lookup"><span data-stu-id="8cfc3-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="8cfc3-115">Die Eyetrackingkonfiguration im MRTK wird über die -Schnittstelle [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="8cfc3-116">Die [Verwendung von CoreServices.InputSystem.EyeProvider](eye-tracking-eye-gaze-provider.md) stellt die Standardmäßige Implementierung des Anvierungsanbieters bereit, die zur Laufzeit im Toolkit registriert ist.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-116">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="8cfc3-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` gibt einen zurück, der NULL ist, wenn noch keine Informationen vom `bool?` Eyetracker verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="8cfc3-118">Nachdem die Daten empfangen wurden, wird entweder true oder false zurückgegeben, um anzugeben, dass die Eyetracking-Kalibrierung des Benutzers gültig oder ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="8cfc3-119">Beispielbenachrichtigung zur Kalibrierung der Augen – Schritt für Schritt</span><span class="sxs-lookup"><span data-stu-id="8cfc3-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="8cfc3-120">Öffnen Sie das MRTK-Beispielpaket für die Blickverfolgung (Assets/MRTK/Examples/Demos/EyeTracking).</span><span class="sxs-lookup"><span data-stu-id="8cfc3-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="8cfc3-121">Laden _der EyeTrackingDemo-00-RootScene.unity-Szene_</span><span class="sxs-lookup"><span data-stu-id="8cfc3-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="8cfc3-122">Sehen Sie sich _EyeCalibrationChecker an:_</span><span class="sxs-lookup"><span data-stu-id="8cfc3-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="8cfc3-123">In dieser Szene haben wir bereits ein Beispiel für die Erkennung, ob der aktuelle Benutzer unter dem *_EyeCalibrationChecker-Spielobjekt_ kalibriert ist.*</span><span class="sxs-lookup"><span data-stu-id="8cfc3-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="8cfc3-124">Es werden lediglich einige Textgitternetze über- und verfügt über einige zusätzliche Trigger zum Ein- und Ausblenden der Benachrichtigung. Dies schließt eine langsame Vergrößerung und Deckkraft bei der Aktivierung ein.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="8cfc3-125">Nachdem die Benachrichtigung verworfen wurde, wird sie langsam vergrößert und ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="8cfc3-126">An das *_EyeCalibrationChecker-Spielobjekt_* angefügt ist das [EyeCalibrationChecker-Skript,](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) das zwei Unity-Ereignisse verfügbar macht:</span><span class="sxs-lookup"><span data-stu-id="8cfc3-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="8cfc3-127">Diese Ereignisse werden nur ausgelöst, wenn sich der Kalibrierungsstatus ändert.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="8cfc3-128">Wenn ein Benutzer die Benachrichtigung daher verlässt, wird die Benachrichtigung erst wieder angezeigt, wenn</span><span class="sxs-lookup"><span data-stu-id="8cfc3-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="8cfc3-129">Die App wird neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-129">The app gets restarted</span></span>
      - <span data-ttu-id="8cfc3-130">Ein gültiger Benutzer wurde erkannt, und dann hat ein neuer nicht veralteter Benutzer das Gerät ein-</span><span class="sxs-lookup"><span data-stu-id="8cfc3-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="8cfc3-131">Um zu testen, ob die Animationen und Ereignisse ordnungsgemäß ausgelöst werden, verfügt das EyeCalibrationChecker-Skript über ein `bool editorTestUserIsCalibrated` Flag.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="8cfc3-132">Wenn Sie beispielsweise im Unity-Editor ausführen, können Sie Folgendes testen:</span><span class="sxs-lookup"><span data-stu-id="8cfc3-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="8cfc3-133">Gibt an, ob die Benachrichtigung automatisch angezeigt wird, sobald sich der Kalibrierungsstatus von "true" in "false" ändert.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="8cfc3-134">Gibt an, ob die Benachrichtigung automatisch erneut verworfen wird, sobald der Status von "false" in "true" geändert wird.</span><span class="sxs-lookup"><span data-stu-id="8cfc3-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

```c#
    private bool? prevCalibrationStatus = null;
    ...

   void Update()
   {
      // Get the latest calibration state from the EyeGazeProvider
      bool? calibrationStatus = CoreServices.InputSystem?.EyeGazeProvider?.IsEyeCalibrationValid;

      ...

      if (calibrationStatus != null)
      {
         if (prevCalibrationStatus != calibrationStatus)
         {
            if (calibrationStatus == false)
            {
               OnNoEyeCalibrationDetected.Invoke();
            }
         else
         {
            OnEyeCalibrationDetected.Invoke();
         }

         prevCalibrationStatus = calibrationStatus;
      }
   }
```

## <a name="see-also"></a><span data-ttu-id="8cfc3-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8cfc3-135">See also</span></span>

- [<span data-ttu-id="8cfc3-136">ÜBERSICHT ÜBER MRTK Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="8cfc3-136">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="8cfc3-137">MRTK Eye Tracking-Setup</span><span class="sxs-lookup"><span data-stu-id="8cfc3-137">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="8cfc3-138">MRTK Eye Tracking per Code</span><span class="sxs-lookup"><span data-stu-id="8cfc3-138">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="8cfc3-139">HoloLens 2 EyeTracking-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8cfc3-139">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)
