---
title: Eingabeanbieter
description: Dokumentation zu verschiedenen Typen von Eingabeanbietern in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: f53932b5e12e60b3638c1d6c31e569016de983ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176752"
---
# <a name="input-providers"></a>Eingabeanbieter

Eingabeanbieter werden im **Profil registrierte Dienstanbieter** in der Komponente Mixed Reality Toolkit registriert:

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

Dies sind die voreindingen verfügbaren Eingabeanbieter zusammen mit den entsprechenden Controllern:

| Eingabeanbieter | Controller |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | Simulierte Hand |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | Maus  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | Generischer Manding  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Unity Touch Controller  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *Keine*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | ARTIkulierte WMR-Hand, WMR-Controller, WMR-GGV-Hand (Anvieren, Geste und Stimme) |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *Keine* |

Diktat- und Sprachanbieter erstellen keine Controller, sie richten ihre eigenen speziellen Eingabeereignisse direkt aus.

Benutzerdefinierte Eingabeanbieter können durch Implementieren der -Schnittstelle erstellt [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) werden.

Weitere Informationen finden Sie unter [Erstellen eines Eingabesystemdatenanbieters.](create-data-provider.md)
