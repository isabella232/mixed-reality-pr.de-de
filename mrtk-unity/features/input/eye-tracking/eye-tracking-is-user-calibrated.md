---
title: Augenkalibrierung
description: Einrichten der Kalibrierung von Benutzerauge in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking, Kalibrierung,
ms.openlocfilehash: d7ae9885b77798b44b3d63bb7f92283658e05411
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144008"
---
# <a name="eye-calibration"></a><span data-ttu-id="b1991-104">Augenkalibrierung</span><span class="sxs-lookup"><span data-stu-id="b1991-104">Eye calibration</span></span>

![Screenshot der Benachrichtigung zur Augenkalibrierung](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="b1991-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="b1991-106">Overview</span></span>

<span data-ttu-id="b1991-107">Wenn eye tracking ein grundlegender Bestandteil Ihrer App-Erfahrung ist, kann es sein, dass Sie sicherstellen möchten, dass die Augenkalibrierung des Benutzers gültig ist.</span><span class="sxs-lookup"><span data-stu-id="b1991-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="b1991-108">Der Hauptgrund für die Ungültigkeit ist, dass der Benutzer die Kalibrierung der Blickverfolgung beim Ansetzen auf dem Gerät übersprungen hat.</span><span class="sxs-lookup"><span data-stu-id="b1991-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="b1991-109">Auf dieser Seite wird Folgendes behandelt:</span><span class="sxs-lookup"><span data-stu-id="b1991-109">This page covers the following:</span></span>

- <span data-ttu-id="b1991-110">Beschreibt, wie erkannt wird, dass ein Benutzer mit dem Auge kalibriert wird.</span><span class="sxs-lookup"><span data-stu-id="b1991-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="b1991-111">Enthält ein Beispiel zum Auslösen einer Benutzerbenachrichtigung, um den Benutzer anzuweisen, die Augenkalibrierung zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="b1991-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="b1991-112">Benachrichtigung automatisch verwerfen, wenn die Augenkalibrierung gültig wird</span><span class="sxs-lookup"><span data-stu-id="b1991-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="b1991-113">Manuelles Verwerfen von Benachrichtigungen, wenn sich der Benutzer dafür entscheidet, ohne Kalibrierung fortzufahren</span><span class="sxs-lookup"><span data-stu-id="b1991-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="b1991-114">Erkennen des Kalibrierungszustands des Auges</span><span class="sxs-lookup"><span data-stu-id="b1991-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="b1991-115">Die Eyetrackingkonfiguration im MRTK wird über die [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) -Schnittstelle konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="b1991-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="b1991-116">Die Verwendung von [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) stellt die Standardmäßige Implementierung des Anvischen-Anbieters bereit, die zur Laufzeit im Toolkit registriert ist.</span><span class="sxs-lookup"><span data-stu-id="b1991-116">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="b1991-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` gibt einen `bool?` zurück, der NULL ist, wenn noch keine Informationen vom Eyetracker verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="b1991-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="b1991-118">Nachdem die Daten empfangen wurden, geben sie entweder true oder false zurück, um anzugeben, dass die Eyetracking-Kalibrierung des Benutzers gültig oder ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="b1991-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="b1991-119">Beispielbenachrichtigung zur Augenkalibrierung – Schritt für Schritt</span><span class="sxs-lookup"><span data-stu-id="b1991-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="b1991-120">Öffnen Sie das MRTK-Eyetracking-Beispielpaket (Assets/MRTK/Examples/Demos/EyeTracking).</span><span class="sxs-lookup"><span data-stu-id="b1991-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="b1991-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span><span class="sxs-lookup"><span data-stu-id="b1991-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="b1991-122">Sehen Sie sich _EyeCalibrationChecker_ an:</span><span class="sxs-lookup"><span data-stu-id="b1991-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="b1991-123">In dieser Szene haben wir bereits ein Beispiel für die Erkennung, ob der aktuelle Benutzer unter dem *_EyeCalibrationChecker-Spielobjekt_* kalibriert wird.</span><span class="sxs-lookup"><span data-stu-id="b1991-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="b1991-124">Es werden einfach ein paar Textgitternetze mit zusätzlichen Triggern für das Ein- und Ausblenden der Benachrichtigung ausgelöst. Dies schließt eine langsame Erhöhung der Größe und Deckkraft bei der Aktivierung ein.</span><span class="sxs-lookup"><span data-stu-id="b1991-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="b1991-125">Nachdem die Benachrichtigung verworfen wurde, wird sie langsam verkleinern und ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="b1991-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="b1991-126">An das *_EyeCalibrationChecker-Spielobjekt_* angefügt ist das [EyeCalibrationChecker-Skript,](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) das zwei Unity-Ereignisse verfügbar macht:</span><span class="sxs-lookup"><span data-stu-id="b1991-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="b1991-127">Diese Ereignisse werden nur ausgelöst, wenn sich der Kalibrierungsstatus ändert.</span><span class="sxs-lookup"><span data-stu-id="b1991-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="b1991-128">Wenn ein Benutzer die Benachrichtigung verwerfen möchte, wird die Benachrichtigung daher erst wieder angezeigt, wenn</span><span class="sxs-lookup"><span data-stu-id="b1991-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="b1991-129">Die App wird neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="b1991-129">The app gets restarted</span></span>
      - <span data-ttu-id="b1991-130">Ein gültiger Benutzer wurde erkannt, und dann hat ein neuer nicht registrierter Benutzer das Gerät eingeschaltet.</span><span class="sxs-lookup"><span data-stu-id="b1991-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="b1991-131">Zum Testen, ob die Animationen und Ereignisse ordnungsgemäß ausgelöst werden, besitzt das EyeCalibrationChecker-Skript ein `bool editorTestUserIsCalibrated` Flag.</span><span class="sxs-lookup"><span data-stu-id="b1991-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="b1991-132">Wenn Sie beispielsweise im Unity-Editor ausführen, können Sie Folgendes testen:</span><span class="sxs-lookup"><span data-stu-id="b1991-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="b1991-133">Gibt an, ob die Benachrichtigung automatisch angezeigt wird, sobald sich der Kalibrierungsstatus von "true" in "false" ändert.</span><span class="sxs-lookup"><span data-stu-id="b1991-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="b1991-134">Gibt an, ob die Benachrichtigung automatisch wieder verworfen wird, sobald sich der Status von FALSE in TRUE ändert.</span><span class="sxs-lookup"><span data-stu-id="b1991-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b1991-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b1991-135">See also</span></span>

- [<span data-ttu-id="b1991-136">MRTK Eye Tracking Overview</span><span class="sxs-lookup"><span data-stu-id="b1991-136">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="b1991-137">MRTK Eye Tracking-Setup</span><span class="sxs-lookup"><span data-stu-id="b1991-137">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="b1991-138">MRTK Eye Tracking per Code</span><span class="sxs-lookup"><span data-stu-id="b1991-138">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="b1991-139">Dokumentation zur HoloLens 2 Eyetracking</span><span class="sxs-lookup"><span data-stu-id="b1991-139">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)