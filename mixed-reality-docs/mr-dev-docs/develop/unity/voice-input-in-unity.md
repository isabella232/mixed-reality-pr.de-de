---
title: Spracheingabe in Unity
description: Erfahren Sie, wie Unity drei Möglichkeiten zum Hinzufügen von Spracheingaben, sprach erkenfizierung und Diktat für Ihre Windows Mixed Reality-Anwendung bietet.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Spracheingabe, keywordrecognizer, grammarerkenzer, Mikrofon, Diktat, Voice, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 7268a4df9c7fce03029937c72540ed274574067d
ms.sourcegitcommit: 8c3af63fb49494f75c8ab46236fc3dd8533c1e9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99606115"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="2dad5-104">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="2dad5-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="2dad5-105">Bevor Sie beginnen, sollten Sie das Unity-Plug-in für das Cognitive Speech Services SDK verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dad5-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="2dad5-106">Das Plug-in bietet bessere Ergebnisse bei der sprach Genauigkeit und einen einfachen Zugriff auf die Sprache-zu-Text-Decodierung sowie erweiterte sprach Features wie Dialog, Intent-basierte Interaktion, Übersetzung, Text-zu-Sprache-Synthese und Spracherkennung in natürlicher Sprache.</span><span class="sxs-lookup"><span data-stu-id="2dad5-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="2dad5-107">Informationen zu den ersten Schritten finden Sie im [Beispiel und](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity)in der Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="2dad5-107">To get started, check out the [sample and documentation](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="2dad5-108">Unity bietet drei Möglichkeiten zum Hinzufügen von [Spracheingaben](../../design/voice-input.md) zu ihrer Unity-Anwendung, die ersten beiden Typen von phraserecognizer:</span><span class="sxs-lookup"><span data-stu-id="2dad5-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="2dad5-109">Der stellt der `KeywordRecognizer` App ein Array von Zeichen folgen Befehlen zur Verfügung, die überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="2dad5-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="2dad5-110">Der weist `GrammarRecognizer` Ihrer APP eine SRGS-Datei zu, die eine bestimmte Grammatik zum lauschen definiert.</span><span class="sxs-lookup"><span data-stu-id="2dad5-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="2dad5-111">Mit dem kann `DictationRecognizer` Ihre APP auf ein beliebiges Wort lauschen und dem Benutzer einen Hinweis oder eine andere Anzeige seiner Sprache bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2dad5-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="2dad5-112">Diktat-und Ausdrucks Erkennung können nicht gleichzeitig behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="2dad5-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="2dad5-113">Wenn ein Grammatik oder keywordrecognizer aktiv ist, kann ein "diktationerkenzer" nicht aktiv sein und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="2dad5-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="2dad5-114">Aktivieren der Sprachfunktion</span><span class="sxs-lookup"><span data-stu-id="2dad5-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="2dad5-115">Die **Mikrofon** Funktion muss für eine APP deklariert werden, um eine Spracheingabe zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dad5-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="2dad5-116">Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen > Player** .</span><span class="sxs-lookup"><span data-stu-id="2dad5-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="2dad5-117">Registerkarte " **Windows Store** " auswählen</span><span class="sxs-lookup"><span data-stu-id="2dad5-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="2dad5-118">Überprüfen Sie im Abschnitt **Veröffentlichungs Einstellungen > Funktionen** die **Mikrofon** Funktion.</span><span class="sxs-lookup"><span data-stu-id="2dad5-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="2dad5-119">Erteilen von Berechtigungen für die APP für den Mikrofon Zugriff auf Ihrem hololens-Gerät</span><span class="sxs-lookup"><span data-stu-id="2dad5-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="2dad5-120">Sie werden zum Starten des Geräts aufgefordert, aber wenn Sie versehentlich auf "Nein" geklickt haben, können Sie die Berechtigungen in den Geräteeinstellungen ändern.</span><span class="sxs-lookup"><span data-stu-id="2dad5-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="2dad5-121">Ausdrucks Erkennung</span><span class="sxs-lookup"><span data-stu-id="2dad5-121">Phrase Recognition</span></span>

<span data-ttu-id="2dad5-122">Damit Ihre APP auf bestimmte vom Benutzer gesprochene Ausdrücke lauschen kann, müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="2dad5-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="2dad5-123">Angeben der abzuhörenden Ausdrücke mithilfe von `KeywordRecognizer` oder `GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="2dad5-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="2dad5-124">Behandeln `OnPhraseRecognized` Sie das-Ereignis, und ergreifen Sie entsprechende Aktionen für den erkannten Ausdruck.</span><span class="sxs-lookup"><span data-stu-id="2dad5-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="2dad5-125">Keywordrecognizer</span><span class="sxs-lookup"><span data-stu-id="2dad5-125">KeywordRecognizer</span></span>

<span data-ttu-id="2dad5-126">**Namespace:** *unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="2dad5-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="2dad5-127">**Typen:** *keywordrecognizer*, *phraserecognizedeventargs*, *delegatfehler*, Sprech *Systemstatus*</span><span class="sxs-lookup"><span data-stu-id="2dad5-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="2dad5-128">Zum Speichern einiger Tastatureingaben benötigen wir einige using-Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="2dad5-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="2dad5-129">Fügen Sie der Klasse nun einige Felder hinzu, um das Erkennungs-und Schlüsselwort >Aktions Wörterbuch zu speichern:</span><span class="sxs-lookup"><span data-stu-id="2dad5-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="2dad5-130">Fügen Sie nun dem Wörterbuch ein Schlüsselwort hinzu, z. b. in einer- `Start()` Methode.</span><span class="sxs-lookup"><span data-stu-id="2dad5-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="2dad5-131">Das Schlüsselwort "aktivieren" wird in diesem Beispiel hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="2dad5-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="2dad5-132">Erstellen Sie die Schlüsselwort Erkennung, und teilen Sie Ihnen mit, was wir erkennen möchten:</span><span class="sxs-lookup"><span data-stu-id="2dad5-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="2dad5-133">Registrieren Sie sich jetzt für das `OnPhraseRecognized` Ereignis.</span><span class="sxs-lookup"><span data-stu-id="2dad5-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="2dad5-134">Ein Beispiel Handler ist:</span><span class="sxs-lookup"><span data-stu-id="2dad5-134">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="2dad5-135">Beginnen Sie schließlich mit der Erkennung!</span><span class="sxs-lookup"><span data-stu-id="2dad5-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="2dad5-136">Grammarerkenzer</span><span class="sxs-lookup"><span data-stu-id="2dad5-136">GrammarRecognizer</span></span>

<span data-ttu-id="2dad5-137">**Namespace:** *unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="2dad5-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="2dad5-138">**Typen**: *grammarerkenzer*, *phraserecognizedeventargs*, *delegatfehler*, Sprech *Systemstatus*</span><span class="sxs-lookup"><span data-stu-id="2dad5-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="2dad5-139">Die Grammatiken werden verwendet, wenn Sie Ihre Erkennungs Grammatik mithilfe von SRGS angeben.</span><span class="sxs-lookup"><span data-stu-id="2dad5-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="2dad5-140">Dies kann hilfreich sein, wenn Ihre APP mehr als nur einige wenige Schlüsselwörter aufweist, wenn Sie komplexere Ausdrücke erkennen möchten, oder wenn Sie Sätze von Befehlen problemlos aktivieren und deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="2dad5-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="2dad5-141">Informationen zum Dateiformat finden [Sie unter Erstellen von Grammatiken mithilfe von SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) .</span><span class="sxs-lookup"><span data-stu-id="2dad5-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="2dad5-142">Sobald Sie die SRGS-Grammatik haben und sich in Ihrem Projekt in einem [Ordner "streamingassets](https://docs.unity3d.com/Manual/StreamingAssets.html)" befinden:</span><span class="sxs-lookup"><span data-stu-id="2dad5-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="2dad5-143">Erstellen `GrammarRecognizer` Sie eine, und übergeben Sie Ihr den Pfad zu ihrer SRGS-Datei:</span><span class="sxs-lookup"><span data-stu-id="2dad5-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="2dad5-144">Registrieren Sie sich jetzt für das `OnPhraseRecognized` Ereignis.</span><span class="sxs-lookup"><span data-stu-id="2dad5-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="2dad5-145">Sie erhalten einen Rückruf mit Informationen, die in der SRGS-Grammatik angegeben sind, die Sie entsprechend behandeln können.</span><span class="sxs-lookup"><span data-stu-id="2dad5-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="2dad5-146">Die meisten wichtigen Informationen werden im-Array bereitgestellt `semanticMeanings` .</span><span class="sxs-lookup"><span data-stu-id="2dad5-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="2dad5-147">Beginnen Sie schließlich mit der Erkennung!</span><span class="sxs-lookup"><span data-stu-id="2dad5-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="2dad5-148">Diktieren</span><span class="sxs-lookup"><span data-stu-id="2dad5-148">Dictation</span></span>

<span data-ttu-id="2dad5-149">**Namespace:** *unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="2dad5-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="2dad5-150">**Typen**: " *diktationerkenzer*", "sprecherfehler", " *Redner Systemstatus* </span><span class="sxs-lookup"><span data-stu-id="2dad5-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="2dad5-151">Verwenden `DictationRecognizer` Sie, um die Sprache des Benutzers in Text zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="2dad5-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="2dad5-152">Der Diktat-Erkennungs Modul macht [Diktat](../../design/voice-input.md#dictation) Funktionen verfügbar und unterstützt das registrieren und lauschen auf Hypothese und Ausdrucks fertige Ereignisse, sodass Sie Ihrem Benutzer Feedback geben können, während Sie sprechen und danach.</span><span class="sxs-lookup"><span data-stu-id="2dad5-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="2dad5-153">`Start()` die `Stop()` Methoden und aktivieren bzw. deaktivieren die Diktat Erkennung.</span><span class="sxs-lookup"><span data-stu-id="2dad5-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="2dad5-154">Sobald die Erkennung erfolgt ist, sollte Sie mithilfe von verworfen werden, `Dispose()` um die verwendeten Ressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="2dad5-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="2dad5-155">Diese Ressourcen werden während der Garbage Collection automatisch freigegeben, wenn Sie noch nicht freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="2dad5-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="2dad5-156">Für den Einstieg in das Diktat müssen nur wenige Schritte ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="2dad5-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="2dad5-157">Erstellen eines neuen `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="2dad5-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="2dad5-158">Behandeln von Diktat Ereignissen</span><span class="sxs-lookup"><span data-stu-id="2dad5-158">Handle Dictation events</span></span>
3. <span data-ttu-id="2dad5-159">"Diktationerkenzer" starten</span><span class="sxs-lookup"><span data-stu-id="2dad5-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="2dad5-160">Aktivieren der Funktion für das Diktat</span><span class="sxs-lookup"><span data-stu-id="2dad5-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="2dad5-161">Die **Internet Client** -und **Mikrofon** Funktionen müssen für eine APP deklariert werden, um die Diktat Verwendung zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="2dad5-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="2dad5-162">Wechseln Sie im Unity-Editor zu **Edit > Project Settings > Player** .</span><span class="sxs-lookup"><span data-stu-id="2dad5-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="2dad5-163">Auf der Registerkarte " **Windows Store** " auswählen</span><span class="sxs-lookup"><span data-stu-id="2dad5-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="2dad5-164">Überprüfen Sie im Abschnitt **Veröffentlichungs Einstellungen > Funktionen** die Funktion **Internetclient** .</span><span class="sxs-lookup"><span data-stu-id="2dad5-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="2dad5-165">Wenn Sie das Mikrofon nicht bereits aktiviert haben, überprüfen Sie optional die **Mikrofon** Funktion.</span><span class="sxs-lookup"><span data-stu-id="2dad5-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="2dad5-166">Erteilen von Berechtigungen für die APP für den Zugriff auf das Mikrofon auf Ihrem hololens-Gerät, sofern noch nicht geschehen</span><span class="sxs-lookup"><span data-stu-id="2dad5-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="2dad5-167">Sie werden zum Starten des Geräts aufgefordert, aber wenn Sie versehentlich auf "Nein" geklickt haben, können Sie die Berechtigungen in den Geräteeinstellungen ändern.</span><span class="sxs-lookup"><span data-stu-id="2dad5-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="2dad5-168">Diktationerkenzer</span><span class="sxs-lookup"><span data-stu-id="2dad5-168">DictationRecognizer</span></span>

<span data-ttu-id="2dad5-169">Erstellen Sie einen "diktationerkenzer" wie folgt:</span><span class="sxs-lookup"><span data-stu-id="2dad5-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="2dad5-170">Es gibt vier Diktat Ereignisse, die abonniert und behandelt werden können, um das Diktat Verhalten zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="2dad5-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="2dad5-171">**"Ditationresult"**</span><span class="sxs-lookup"><span data-stu-id="2dad5-171">**DictationResult**</span></span>

<span data-ttu-id="2dad5-172">Dieses Ereignis wird ausgelöst, nachdem der Benutzer angehalten wurde, in der Regel am Ende eines Satzes.</span><span class="sxs-lookup"><span data-stu-id="2dad5-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="2dad5-173">Hier wird die vollständig erkannte Zeichenfolge zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="2dad5-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="2dad5-174">Abonnieren Sie zunächst das- `DictationResult` Ereignis:</span><span class="sxs-lookup"><span data-stu-id="2dad5-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="2dad5-175">Behandeln Sie dann den "-Rückruf":</span><span class="sxs-lookup"><span data-stu-id="2dad5-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="2dad5-176">**"Ditationhypothese"**</span><span class="sxs-lookup"><span data-stu-id="2dad5-176">**DictationHypothesis**</span></span>

<span data-ttu-id="2dad5-177">Dieses Ereignis wird fortlaufend ausgelöst, während der Benutzer spricht.</span><span class="sxs-lookup"><span data-stu-id="2dad5-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="2dad5-178">Wie die Erkennung hört, bietet Sie Text zu den bisher gehörenden.</span><span class="sxs-lookup"><span data-stu-id="2dad5-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="2dad5-179">Abonnieren Sie zunächst das- `DictationHypothesis` Ereignis:</span><span class="sxs-lookup"><span data-stu-id="2dad5-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="2dad5-180">Behandeln Sie dann den-Rückruf von "ditationhypothese":</span><span class="sxs-lookup"><span data-stu-id="2dad5-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="2dad5-181">**"Ditationcomplete"**</span><span class="sxs-lookup"><span data-stu-id="2dad5-181">**DictationComplete**</span></span>

<span data-ttu-id="2dad5-182">Dieses Ereignis wird ausgelöst, wenn die Erkennung angehalten wird, und zwar unabhängig davon, ob von "Stopp ()" aufgerufen wird, ein Timeout auftritt oder ein anderer Fehler vorliegt.</span><span class="sxs-lookup"><span data-stu-id="2dad5-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="2dad5-183">Abonnieren Sie zunächst das- `DictationComplete` Ereignis:</span><span class="sxs-lookup"><span data-stu-id="2dad5-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="2dad5-184">Behandeln Sie dann den-Rückruf von "ditationcomplete":</span><span class="sxs-lookup"><span data-stu-id="2dad5-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="2dad5-185">**"Ditationerror"**</span><span class="sxs-lookup"><span data-stu-id="2dad5-185">**DictationError**</span></span>

<span data-ttu-id="2dad5-186">Dieses Ereignis wird ausgelöst, wenn ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="2dad5-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="2dad5-187">Abonnieren Sie zunächst das- `DictationError` Ereignis:</span><span class="sxs-lookup"><span data-stu-id="2dad5-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="2dad5-188">Behandeln Sie dann den "-Rückruf"-Rückruf:</span><span class="sxs-lookup"><span data-stu-id="2dad5-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="2dad5-189">Nachdem Sie die Diktat Ereignisse abonniert und behandelt haben, die Ihnen wichtig sind, starten Sie die Diktat Erkennung, um mit dem empfangen von Ereignissen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="2dad5-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="2dad5-190">Wenn Sie die "diktationerkenzer" nicht mehr benötigen, müssen Sie die Ereignisse kündigen und den "diktationerkenzer" verwerfen.</span><span class="sxs-lookup"><span data-stu-id="2dad5-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="2dad5-191">**Tipps**</span><span class="sxs-lookup"><span data-stu-id="2dad5-191">**Tips**</span></span>
* <span data-ttu-id="2dad5-192">`Start()` die `Stop()` Methoden und aktivieren bzw. deaktivieren die Diktat Erkennung.</span><span class="sxs-lookup"><span data-stu-id="2dad5-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="2dad5-193">Sobald die Erkennung erfolgt ist, muss Sie mithilfe von verworfen werden, `Dispose()` um die verwendeten Ressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="2dad5-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="2dad5-194">Diese Ressourcen werden während der Garbage Collection automatisch freigegeben, wenn Sie noch nicht freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="2dad5-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="2dad5-195">Timeouts treten nach einer festgelegten Zeitspanne auf.</span><span class="sxs-lookup"><span data-stu-id="2dad5-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="2dad5-196">Sie können diese Timeouts im Ereignis überprüfen `DictationComplete` .</span><span class="sxs-lookup"><span data-stu-id="2dad5-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="2dad5-197">Es gibt zwei Timeouts, die Sie beachten sollten:</span><span class="sxs-lookup"><span data-stu-id="2dad5-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="2dad5-198">Wenn die Erkennung gestartet wird und in den ersten fünf Sekunden keine Audiodaten mehr angezeigt werden, tritt ein Timeout auf.</span><span class="sxs-lookup"><span data-stu-id="2dad5-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="2dad5-199">Wenn die Erkennung ein Ergebnis erhalten hat, aber dann 20 Sekunden lang Stillen wird, tritt ein Timeout auf.</span><span class="sxs-lookup"><span data-stu-id="2dad5-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="2dad5-200">Verwenden der Ausdrucks Erkennung und-diktierung</span><span class="sxs-lookup"><span data-stu-id="2dad5-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="2dad5-201">Wenn Sie in Ihrer APP sowohl die Erkennung als auch das Diktat von Ausdrücken verwenden möchten, müssen Sie eine vollständige Herunterfahren, bevor Sie die andere starten können.</span><span class="sxs-lookup"><span data-stu-id="2dad5-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="2dad5-202">Wenn mehrere keywordrecognizers ausgeführt werden, können Sie Sie mit folgenden Aktionen gleichzeitig Herunterfahren:</span><span class="sxs-lookup"><span data-stu-id="2dad5-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="2dad5-203">Sie können aufzurufen `Restart()` , um alle erkenners in Ihrem vorherigen Zustand wiederherzustellen, nachdem der "diktationerkenzer" angehalten wurde:</span><span class="sxs-lookup"><span data-stu-id="2dad5-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="2dad5-204">Sie können auch einfach einen keywordrecognizer starten, mit dem auch das phraserecognitionsystem neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="2dad5-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="2dad5-205">Spracheingabe im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="2dad5-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="2dad5-206">In den folgenden Demoszenen finden Sie mrtk-Beispiele für die Spracheingabe:</span><span class="sxs-lookup"><span data-stu-id="2dad5-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="2dad5-207">Diktieren</span><span class="sxs-lookup"><span data-stu-id="2dad5-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="2dad5-208">Speech</span><span class="sxs-lookup"><span data-stu-id="2dad5-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="2dad5-209">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="2dad5-209">Next Development Checkpoint</span></span>

<span data-ttu-id="2dad5-210">Wenn Sie der Unity-Entwicklungs Prüf Punkt Journey folgen, haben wir die nächste Aufgabe darin, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen:</span><span class="sxs-lookup"><span data-stu-id="2dad5-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2dad5-211">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="2dad5-211">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="2dad5-212">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="2dad5-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>