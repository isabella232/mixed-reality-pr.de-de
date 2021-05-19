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
# <a name="eye-calibration"></a>Augenkalibrierung

![Screenshot der Benachrichtigung zur Augenkalibrierung](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>Übersicht

Wenn eye tracking ein grundlegender Bestandteil Ihrer App-Erfahrung ist, kann es sein, dass Sie sicherstellen möchten, dass die Augenkalibrierung des Benutzers gültig ist.
Der Hauptgrund für die Ungültigkeit ist, dass der Benutzer die Kalibrierung der Blickverfolgung beim Ansetzen auf dem Gerät übersprungen hat.

Auf dieser Seite wird Folgendes behandelt:

- Beschreibt, wie erkannt wird, dass ein Benutzer mit dem Auge kalibriert wird.
- Enthält ein Beispiel zum Auslösen einer Benutzerbenachrichtigung, um den Benutzer anzuweisen, die Augenkalibrierung zu durchlaufen.
  - Benachrichtigung automatisch verwerfen, wenn die Augenkalibrierung gültig wird
  - Manuelles Verwerfen von Benachrichtigungen, wenn sich der Benutzer dafür entscheidet, ohne Kalibrierung fortzufahren

### <a name="how-to-detect-the-eye-calibration-state"></a>Erkennen des Kalibrierungszustands des Auges

Die Eyetrackingkonfiguration im MRTK wird über die [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) -Schnittstelle konfiguriert.

Die Verwendung von [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) stellt die Standardmäßige Implementierung des Anvischen-Anbieters bereit, die zur Laufzeit im Toolkit registriert ist. `IMixedRealityEyeGazeProvider.IsEyeGazeValid` gibt einen `bool?` zurück, der NULL ist, wenn noch keine Informationen vom Eyetracker verfügbar sind.
Nachdem die Daten empfangen wurden, geben sie entweder true oder false zurück, um anzugeben, dass die Eyetracking-Kalibrierung des Benutzers gültig oder ungültig ist.

### <a name="sample-eye-calibration-notification---step-by-step"></a>Beispielbenachrichtigung zur Augenkalibrierung – Schritt für Schritt

1. Öffnen Sie das MRTK-Eyetracking-Beispielpaket (Assets/MRTK/Examples/Demos/EyeTracking).

2. Load _EyeTrackingDemo-00-RootScene.unity_ scene

3. Sehen Sie sich _EyeCalibrationChecker_ an:
   - In dieser Szene haben wir bereits ein Beispiel für die Erkennung, ob der aktuelle Benutzer unter dem *_EyeCalibrationChecker-Spielobjekt_* kalibriert wird.
Es werden einfach ein paar Textgitternetze mit zusätzlichen Triggern für das Ein- und Ausblenden der Benachrichtigung ausgelöst. Dies schließt eine langsame Erhöhung der Größe und Deckkraft bei der Aktivierung ein.
Nachdem die Benachrichtigung verworfen wurde, wird sie langsam verkleinern und ausgeblendet.

   - An das *_EyeCalibrationChecker-Spielobjekt_* angefügt ist das [EyeCalibrationChecker-Skript,](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) das zwei Unity-Ereignisse verfügbar macht:
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - Diese Ereignisse werden nur ausgelöst, wenn sich der Kalibrierungsstatus ändert. Wenn ein Benutzer die Benachrichtigung verwerfen möchte, wird die Benachrichtigung daher erst wieder angezeigt, wenn
      - Die App wird neu gestartet.
      - Ein gültiger Benutzer wurde erkannt, und dann hat ein neuer nicht registrierter Benutzer das Gerät eingeschaltet.

   - Zum Testen, ob die Animationen und Ereignisse ordnungsgemäß ausgelöst werden, besitzt das EyeCalibrationChecker-Skript ein `bool editorTestUserIsCalibrated` Flag. Wenn Sie beispielsweise im Unity-Editor ausführen, können Sie Folgendes testen:
      1. Gibt an, ob die Benachrichtigung automatisch angezeigt wird, sobald sich der Kalibrierungsstatus von "true" in "false" ändert.
      1. Gibt an, ob die Benachrichtigung automatisch wieder verworfen wird, sobald sich der Status von FALSE in TRUE ändert.

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

## <a name="see-also"></a>Weitere Informationen

- [MRTK Eye Tracking Overview](eye-tracking-main.md)
- [MRTK Eye Tracking-Setup](eye-tracking-basic-setup.md)
- [MRTK Eye Tracking per Code](eye-tracking-eye-gaze-provider.md)
- [Dokumentation zur HoloLens 2 Eyetracking](/windows/mixed-reality/eye-tracking)