---
title: Eingabeanbieter
description: Dokumentation zu verschiedenen Typen von Eingabeanbietern in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145264"
---
# <a name="input-providers"></a>Eingabeanbieter

Eingabeanbieter werden im Profil **"Registrierte Dienstanbieter"** registriert, das sich in der Mixed Reality Toolkit-Komponente finden:

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

Dies sind die eingabeanbieter, die zusammen mit den entsprechenden Controllern sofort verfügbar sind:

| Eingabeanbieter | Controller |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | Simulierte Hand |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | Maus  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | Generic Joystick  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Unity Touch Controller  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *None*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *None* |

Diktat- und Sprachanbieter erstellen keine Controller, sondern erstellen ihre eigenen speziellen Eingabeereignisse direkt.

Benutzerdefinierte Eingabeanbieter können durch Implementieren der -Schnittstelle erstellt [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) werden.

Weitere Informationen finden Sie unter [Erstellen eines Eingabesystemdatenanbieters.](create-data-provider.md)
