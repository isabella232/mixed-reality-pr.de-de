---
title: Diktieren
description: Docummentation zum Aufzeichnen von Audioclips und Abrufen einer Transkription in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 520a667cc4b41f5e8f4373a7c901eb2458cd2d17
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176468"
---
# <a name="dictation"></a>Diktieren

Mit Diktat können Benutzer Audioclips aufzeichnen und eine Transkription abrufen. Stellen Sie zur Verwendung sicher, dass ein Diktatsystem im *Eingabesystemprofil registriert ist.* **Windows Diktateingabeanbieter** ist das Diktatsystem, das bereits bereitgestellt wird, aber alternative Diktatsysteme können erstellt werden, die [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) implementieren.

## <a name="requirements"></a>Requirements (Anforderungen)

Das Diktatsystem verwendet den [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) von Unity, der selbst die zugrunde liegenden Windows-APIs für die Behandlung von Diktaten verwendet. Beachten Sie, dass dies impliziert, dass dieses Feature nur auf Windows-basierten Plattformen vorhanden ist.

Für die Verwendung des Diktatsystems sind sowohl die Anwendungsfunktionen "Internetclient" als auch "Mikrofon" im [Abschnitt PlayerSettings – Capabilities erforderlich.](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)
Weitere [Windows Mixed Reality zur](/windows/mixed-reality/voice-input-in-unity#dictation) Spracheingabe in Unity finden Sie in der Dokumentation zur Spracheingabe.

## <a name="configuration"></a>Konfiguration

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

Sobald Sie einen Diktatdienst eingerichtet haben, können Sie das Skript verwenden, um Aufzeichnungssitzungen zu starten und zu beenden und die Transkriptionsergebnisse über [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) UnityEvents zu erhalten.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **Die Diktathypothese** wird ausgelöst, wenn der Benutzer mit frühen, groben Transkriptionen der bisher erfassten Audiodaten spricht.
- **Das Diktatergebnis** wird am Ende jedes Satzes (d. h. wenn der Benutzer angehalten wird) mit der endgültigen Transkription der bisher erfassten Audiodatei ausgelöst.
- **Dictation Complete** (Diktat abgeschlossen) wird am Ende der Aufzeichnungssitzung mit der vollständigen, endgültigen Transkription der Audiodaten ausgelöst.
- **Diktatfehler wird** ausgelöst, um über Fehler im Diktatdienst zu informieren. Die Transkription enthält in diesem Fall eine Beschreibung des Fehlers.

## <a name="example-scene"></a>Beispielszene

**Die Diktatszene** in `MRTK/Examples/Demos/Input/Scenes/Dictation` zeigt das `DictationHandler` verwendete Skript. Wenn Sie mehr Kontrolle benötigen, können Sie dieses Skript erweitern oder eine eigene Implementierung erstellen, [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) um Diktatereignisse direkt zu empfangen.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
