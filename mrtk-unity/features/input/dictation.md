---
title: Diktieren
description: Anleitung zum Aufzeichnen von Audioclips und Abrufen einer Transkription im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 14061197031282dcc9dd20a141101b65ee92ca2376bdc009fa8790076681a970
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220004"
---
# <a name="dictation"></a>Diktieren

Mit Diktat können Benutzer Audioclips aufzeichnen und eine Transkription abrufen. Stellen Sie zur Verwendung sicher, dass ein Diktatsystem im *Eingabesystemprofil* registriert ist. **Windows Diktateingabeanbieter** ist das voreingestellte Diktatsystem, aber es können alternative Diktatsysteme erstellt werden, die [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) implementieren.

## <a name="requirements"></a>Anforderungen

Das Diktatsystem verwendet unitys [DictationRecognizer,](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) das selbst die zugrunde liegenden Windows Sprach-APIs für die Behandlung von Diktaten verwendet. Beachten Sie, dass dies bedeutet, dass dieses Feature nur auf Windows-basierten Plattformen vorhanden ist.

Für die Verwendung des Diktatsystems sind sowohl die Anwendungsfunktionen "Internetclient" als auch "Mikrofon" im [Abschnitt PlayerSettings – Funktionen](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)erforderlich.
Weitere Informationen zur Spracheingabe in Unity finden Sie in [Windows Mixed Reality-Dokumentation.](/windows/mixed-reality/voice-input-in-unity#dictation)

## <a name="configuration"></a>Konfiguration

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

Nachdem Sie einen Diktatdienst eingerichtet haben, können Sie das Skript verwenden, [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) um Aufzeichnungssitzungen zu starten und zu beenden und die Transkriptionsergebnisse über UnityEvents abzurufen.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **Die Diktathypothese** wird ausgelöst, wenn der Benutzer mit frühen, groben Transkriptionen der bisher erfassten Audiodaten spricht.
- **Das Diktatergebnis** wird am Ende jedes Satzes (d. h. wenn der Benutzer anhält) mit der endgültigen Transkription der bisher erfassten Audiodaten ausgelöst.
- **Dictation Complete** wird am Ende der Aufzeichnungssitzung mit der vollständigen, endgültigen Transkription des Audios ausgelöst.
- **Diktatfehler** wird ausgelöst, um über Fehler im Diktatdienst zu informieren. Die Transkription enthält in diesem Fall eine Beschreibung des Fehlers.

## <a name="example-scene"></a>Beispielszene

**Die Diktatszene** in `MRTK/Examples/Demos/Input/Scenes/Dictation` zeigt das `DictationHandler` verwendete Skript an. Wenn Sie mehr Kontrolle benötigen, können Sie entweder dieses Skript erweitern oder eine eigene Implementierung [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) erstellen, um Diktatereignisse direkt zu empfangen.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
