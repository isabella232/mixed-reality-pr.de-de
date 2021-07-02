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
# <a name="eye-calibration"></a>Kalibrierung der Augen

![Screenshot der Benachrichtigung zur Kalibrierung der Augen](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>Übersicht

Wenn eye tracking ein grundlegender Bestandteil Ihrer App-Erfahrung ist, sollten Sie sicherstellen, dass die Kalibrierung der Augen des Benutzers gültig ist.
Der Hauptgrund dafür, dass er ungültig ist, ist, dass sich der Benutzer entschieden hat, die Eyetracking-Kalibrierung zu überspringen, wenn er auf das Gerät setzt.

Auf dieser Seite wird Folgendes behandelt:

- Beschreibt, wie erkannt wird, dass ein Benutzer mit den Augen kalibriert ist.
- Enthält ein Beispiel für das Auslösen einer Benutzerbenachrichtigung, um den Benutzer anweisen zu lassen, die Kalibrierung der Augen zu durchgehen.
  - Benachrichtigung automatisch verweisen, wenn die Kalibrierung der Augen gültig wird
  - Manuelles Verdren der Benachrichtigung, wenn der Benutzer sich dafür entscheidet, ohne Kalibrierung fortzufahren

### <a name="how-to-detect-the-eye-calibration-state"></a>Erkennen des Kalibrierungszustands der Augen

Die Eyetrackingkonfiguration im MRTK wird über die -Schnittstelle [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) konfiguriert.

Die [Verwendung von CoreServices.InputSystem.EyeProvider](eye-tracking-eye-gaze-provider.md) stellt die Standardmäßige Implementierung des Anvierungsanbieters bereit, die zur Laufzeit im Toolkit registriert ist. `IMixedRealityEyeGazeProvider.IsEyeGazeValid` gibt einen zurück, der NULL ist, wenn noch keine Informationen vom `bool?` Eyetracker verfügbar sind.
Nachdem die Daten empfangen wurden, wird entweder true oder false zurückgegeben, um anzugeben, dass die Eyetracking-Kalibrierung des Benutzers gültig oder ungültig ist.

### <a name="sample-eye-calibration-notification---step-by-step"></a>Beispielbenachrichtigung zur Kalibrierung der Augen – Schritt für Schritt

1. Öffnen Sie das MRTK-Beispielpaket für die Blickverfolgung (Assets/MRTK/Examples/Demos/EyeTracking).

2. Laden _der EyeTrackingDemo-00-RootScene.unity-Szene_

3. Sehen Sie sich _EyeCalibrationChecker an:_
   - In dieser Szene haben wir bereits ein Beispiel für die Erkennung, ob der aktuelle Benutzer unter dem *_EyeCalibrationChecker-Spielobjekt_ kalibriert ist.*
Es werden lediglich einige Textgitternetze über- und verfügt über einige zusätzliche Trigger zum Ein- und Ausblenden der Benachrichtigung. Dies schließt eine langsame Vergrößerung und Deckkraft bei der Aktivierung ein.
Nachdem die Benachrichtigung verworfen wurde, wird sie langsam vergrößert und ausgeblendet.

   - An das *_EyeCalibrationChecker-Spielobjekt_* angefügt ist das [EyeCalibrationChecker-Skript,](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) das zwei Unity-Ereignisse verfügbar macht:
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - Diese Ereignisse werden nur ausgelöst, wenn sich der Kalibrierungsstatus ändert. Wenn ein Benutzer die Benachrichtigung daher verlässt, wird die Benachrichtigung erst wieder angezeigt, wenn
      - Die App wird neu gestartet.
      - Ein gültiger Benutzer wurde erkannt, und dann hat ein neuer nicht veralteter Benutzer das Gerät ein-

   - Um zu testen, ob die Animationen und Ereignisse ordnungsgemäß ausgelöst werden, verfügt das EyeCalibrationChecker-Skript über ein `bool editorTestUserIsCalibrated` Flag. Wenn Sie beispielsweise im Unity-Editor ausführen, können Sie Folgendes testen:
      1. Gibt an, ob die Benachrichtigung automatisch angezeigt wird, sobald sich der Kalibrierungsstatus von "true" in "false" ändert.
      1. Gibt an, ob die Benachrichtigung automatisch erneut verworfen wird, sobald der Status von "false" in "true" geändert wird.

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

## <a name="see-also"></a>Siehe auch

- [ÜBERSICHT ÜBER MRTK Eye Tracking](eye-tracking-main.md)
- [MRTK Eye Tracking-Setup](eye-tracking-basic-setup.md)
- [MRTK Eye Tracking per Code](eye-tracking-eye-gaze-provider.md)
- [HoloLens 2 EyeTracking-Dokumentation](/windows/mixed-reality/eye-tracking)
