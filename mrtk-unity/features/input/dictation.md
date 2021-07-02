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
# <a name="dictation"></a><span data-ttu-id="94c53-104">Diktieren</span><span class="sxs-lookup"><span data-stu-id="94c53-104">Dictation</span></span>

<span data-ttu-id="94c53-105">Mit Diktat können Benutzer Audioclips aufzeichnen und eine Transkription abrufen.</span><span class="sxs-lookup"><span data-stu-id="94c53-105">Dictation allows users to record audio clips and obtain a transcription.</span></span> <span data-ttu-id="94c53-106">Stellen Sie zur Verwendung sicher, dass ein Diktatsystem im *Eingabesystemprofil registriert ist.*</span><span class="sxs-lookup"><span data-stu-id="94c53-106">To use it make sure that a dictation system is registered in the *Input System Profile*.</span></span> <span data-ttu-id="94c53-107">**Windows Diktateingabeanbieter** ist das Diktatsystem, das bereits bereitgestellt wird, aber alternative Diktatsysteme können erstellt werden, die [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) implementieren.</span><span class="sxs-lookup"><span data-stu-id="94c53-107">**Windows Dictation Input Provider** is the dictation system provided out of the box but alternative dictation systems can be created implementing [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem).</span></span>

## <a name="requirements"></a><span data-ttu-id="94c53-108">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="94c53-108">Requirements</span></span>

<span data-ttu-id="94c53-109">Das Diktatsystem verwendet den [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) von Unity, der selbst die zugrunde liegenden Windows-APIs für die Behandlung von Diktaten verwendet.</span><span class="sxs-lookup"><span data-stu-id="94c53-109">The dictation system uses Unity's [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) which itself uses the underlying Windows speech APIs for handling dictation.</span></span> <span data-ttu-id="94c53-110">Beachten Sie, dass dies impliziert, dass dieses Feature nur auf Windows-basierten Plattformen vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="94c53-110">Note that this implies that this feature is only present on Windows-based platforms.</span></span>

<span data-ttu-id="94c53-111">Für die Verwendung des Diktatsystems sind sowohl die Anwendungsfunktionen "Internetclient" als auch "Mikrofon" im [Abschnitt PlayerSettings – Capabilities erforderlich.](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)</span><span class="sxs-lookup"><span data-stu-id="94c53-111">Usage of the Dictation system requires both the "Internet Client" and "Microphone" application capabilities in the [PlayerSettings - Capabilities section](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span></span>
<span data-ttu-id="94c53-112">Weitere [Windows Mixed Reality zur](/windows/mixed-reality/voice-input-in-unity#dictation) Spracheingabe in Unity finden Sie in der Dokumentation zur Spracheingabe.</span><span class="sxs-lookup"><span data-stu-id="94c53-112">See [Windows Mixed Reality Documentation](/windows/mixed-reality/voice-input-in-unity#dictation) for more details on voice input in Unity.</span></span>

## <a name="configuration"></a><span data-ttu-id="94c53-113">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="94c53-113">Configuration</span></span>

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

<span data-ttu-id="94c53-114">Sobald Sie einen Diktatdienst eingerichtet haben, können Sie das Skript verwenden, um Aufzeichnungssitzungen zu starten und zu beenden und die Transkriptionsergebnisse über [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) UnityEvents zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="94c53-114">Once you have a dictation service set up, you can use the [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script to start and stop recording sessions and obtain the transcription results via UnityEvents.</span></span>

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- <span data-ttu-id="94c53-115">**Die Diktathypothese** wird ausgelöst, wenn der Benutzer mit frühen, groben Transkriptionen der bisher erfassten Audiodaten spricht.</span><span class="sxs-lookup"><span data-stu-id="94c53-115">**Dictation Hypothesis** is raised as the user speaks with early, rough transcriptions of the audio captured so far.</span></span>
- <span data-ttu-id="94c53-116">**Das Diktatergebnis** wird am Ende jedes Satzes (d. h. wenn der Benutzer angehalten wird) mit der endgültigen Transkription der bisher erfassten Audiodatei ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="94c53-116">**Dictation Result** is raised at the end of each sentence (i.e. when the user pauses) with the final transcription of the audio captured so far.</span></span>
- <span data-ttu-id="94c53-117">**Dictation Complete** (Diktat abgeschlossen) wird am Ende der Aufzeichnungssitzung mit der vollständigen, endgültigen Transkription der Audiodaten ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="94c53-117">**Dictation Complete** is raised at the end of the recording session with the full, final transcription of the audio.</span></span>
- <span data-ttu-id="94c53-118">**Diktatfehler wird** ausgelöst, um über Fehler im Diktatdienst zu informieren.</span><span class="sxs-lookup"><span data-stu-id="94c53-118">**Dictation Error** is raised to inform of errors in the dictation service.</span></span> <span data-ttu-id="94c53-119">Die Transkription enthält in diesem Fall eine Beschreibung des Fehlers.</span><span class="sxs-lookup"><span data-stu-id="94c53-119">The transcription in this case contains a description of the error.</span></span>

## <a name="example-scene"></a><span data-ttu-id="94c53-120">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="94c53-120">Example scene</span></span>

<span data-ttu-id="94c53-121">**Die Diktatszene** in `MRTK/Examples/Demos/Input/Scenes/Dictation` zeigt das `DictationHandler` verwendete Skript.</span><span class="sxs-lookup"><span data-stu-id="94c53-121">**Dictation** scene in `MRTK/Examples/Demos/Input/Scenes/Dictation` shows the `DictationHandler` script in use.</span></span> <span data-ttu-id="94c53-122">Wenn Sie mehr Kontrolle benötigen, können Sie dieses Skript erweitern oder eine eigene Implementierung erstellen, [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) um Diktatereignisse direkt zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="94c53-122">If you need more control, you can either extend this script or create your own implementing [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) to receive dictation events directly.</span></span>

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
