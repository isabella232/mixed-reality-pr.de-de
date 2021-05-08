---
title: Spracheingabe in Unity
description: Erfahren Sie, wie Unity drei Möglichkeiten zum Hinzufügen von Spracheingabe, Spracherkennung und Diktat zu Ihrer Windows Mixed Reality-Anwendung verfügbar macht.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Spracheingabe, KeywordRecognizer, GrammarRecognizer, Mikrofon, Diktat, Stimme, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 6b040443606e05843f85b2f74f5ea812daafba31
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489200"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="7c956-104">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="7c956-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="7c956-105">Bevor Sie beginnen, sollten Sie das Unity-Plug-In für das Cognitive Speech Services SDK verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c956-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="7c956-106">Das Plug-In bietet bessere Ergebnisse der Sprachgenauigkeit und einfachen Zugriff auf die Spracherkennungsdecodierung sowie erweiterte Sprachfunktionen wie Dialog, absichtsbasierte Interaktion, Übersetzung, Text-zu-Sprache-Synthese und Spracherkennung in natürlicher Sprache.</span><span class="sxs-lookup"><span data-stu-id="7c956-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="7c956-107">Sehen Sie sich zunächst das [Beispiel und](/azure/cognitive-services/speech-service/quickstart-csharp-unity)die Dokumentation an.</span><span class="sxs-lookup"><span data-stu-id="7c956-107">To get started, check out the [sample and documentation](/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="7c956-108">Unity bietet drei Möglichkeiten zum Hinzufügen von [Spracheingaben](../../design/voice-input.md) zu Ihrer Unity-Anwendung, von denen die ersten beiden Arten von PhraseRecognizer sind:</span><span class="sxs-lookup"><span data-stu-id="7c956-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="7c956-109">`KeywordRecognizer`stellt Ihrer App ein Array von Zeichenfolgenbefehlen bereit, auf die gelecht werden soll.</span><span class="sxs-lookup"><span data-stu-id="7c956-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="7c956-110">Gibt `GrammarRecognizer` Ihrer App eine SRGS-Datei, die eine bestimmte Grammatik definiert, auf die gelescht werden soll.</span><span class="sxs-lookup"><span data-stu-id="7c956-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="7c956-111">`DictationRecognizer`Mit kann Ihre App auf jedes Wort lauschen und dem Benutzer eine Notiz oder eine andere Anzeige seiner Sprache bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="7c956-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="7c956-112">Diktat und Ausdruckserkennung können nicht gleichzeitig verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="7c956-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="7c956-113">Wenn ein GrammarRecognizer oder KeywordRecognizer aktiv ist, kann ein DictationRecognizer nicht aktiv sein und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="7c956-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="7c956-114">Aktivieren der Funktion für Voice</span><span class="sxs-lookup"><span data-stu-id="7c956-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="7c956-115">Die **Mikrofonfunktion** muss deklariert werden, damit eine App Spracheingaben verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="7c956-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="7c956-116">Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen > Player.**</span><span class="sxs-lookup"><span data-stu-id="7c956-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="7c956-117">Wählen Sie die Registerkarte **Windows Store** aus.</span><span class="sxs-lookup"><span data-stu-id="7c956-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="7c956-118">Überprüfen Sie im Abschnitt **Veröffentlichungseinstellungen > Funktionen** die **Funktion Mikrofon.**</span><span class="sxs-lookup"><span data-stu-id="7c956-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="7c956-119">Erteilen von Berechtigungen für die App für den Mikrofonzugriff auf Ihrem HoloLens-Gerät</span><span class="sxs-lookup"><span data-stu-id="7c956-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="7c956-120">Sie werden beim Starten des Geräts dazu aufgefordert, aber wenn Sie versehentlich auf "Nein" geklickt haben, können Sie die Berechtigungen in den Geräteeinstellungen ändern.</span><span class="sxs-lookup"><span data-stu-id="7c956-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="7c956-121">Ausdruckserkennung</span><span class="sxs-lookup"><span data-stu-id="7c956-121">Phrase Recognition</span></span>

<span data-ttu-id="7c956-122">Damit Ihre App auf bestimmte Ausdrücke lauscht, die vom Benutzer gesprochen werden, müssen Sie folgende Aktionen ergreifen:</span><span class="sxs-lookup"><span data-stu-id="7c956-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="7c956-123">Geben Sie an, auf welche Ausdrücke mit oder lauschen `KeywordRecognizer` soll. `GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="7c956-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="7c956-124">Behandeln des `OnPhraseRecognized` Ereignisses und Ergreifen von Aktionen entsprechend dem erkannten Ausdruck</span><span class="sxs-lookup"><span data-stu-id="7c956-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="7c956-125">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="7c956-125">KeywordRecognizer</span></span>

<span data-ttu-id="7c956-126">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="7c956-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="7c956-127">**Typen:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="7c956-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="7c956-128">Wir benötigen einige using-Anweisungen, um einige Tastatureingaben zu speichern:</span><span class="sxs-lookup"><span data-stu-id="7c956-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="7c956-129">Fügen Sie ihrer Klasse dann einige Felder hinzu, um die Such- und Schlüsselwort->aktionswörterbuch zu speichern:</span><span class="sxs-lookup"><span data-stu-id="7c956-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="7c956-130">Fügen Sie nun dem Wörterbuch ein Schlüsselwort hinzu, z. B. in einer `Start()` -Methode.</span><span class="sxs-lookup"><span data-stu-id="7c956-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="7c956-131">Wir fügen das Schlüsselwort "activate" in diesem Beispiel hinzu:</span><span class="sxs-lookup"><span data-stu-id="7c956-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="7c956-132">Erstellen Sie die Schlüsselwortsuche, und teilen Sie ihr mit, was wir erkennen möchten:</span><span class="sxs-lookup"><span data-stu-id="7c956-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="7c956-133">Registrieren Sie sich jetzt für das `OnPhraseRecognized` Ereignis.</span><span class="sxs-lookup"><span data-stu-id="7c956-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="7c956-134">Ein Beispielhandler ist:</span><span class="sxs-lookup"><span data-stu-id="7c956-134">An example handler is:</span></span>

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

<span data-ttu-id="7c956-135">Beginnen Sie schließlich mit der Erkennung!</span><span class="sxs-lookup"><span data-stu-id="7c956-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="7c956-136">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="7c956-136">GrammarRecognizer</span></span>

<span data-ttu-id="7c956-137">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="7c956-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="7c956-138">**Typen:** *GrammarRecognizer,* *PhraseRecognizedEventArgs,* *SpeechError,* *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="7c956-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="7c956-139">Der GrammarRecognizer wird verwendet, wenn Sie Ihre Erkennungsgrammatik mithilfe von SRGS angeben.</span><span class="sxs-lookup"><span data-stu-id="7c956-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="7c956-140">Dies kann nützlich sein, wenn Ihre App über mehr als nur einige Schlüsselwörter verfügt, wenn Sie komplexere Ausdrücke erkennen möchten oder wenn Sie befehlssätze einfach aktivieren und deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="7c956-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="7c956-141">Informationen zum Dateiformat finden Sie unter Erstellen von Grammatiken mit [SRGS XML.](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14))</span><span class="sxs-lookup"><span data-stu-id="7c956-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="7c956-142">Sobald Sie über ihre SRGS-Grammatik verfügen, befindet sie sich in Ihrem Projekt in einem [StreamingAssets-Ordner:](https://docs.unity3d.com/Manual/StreamingAssets.html)</span><span class="sxs-lookup"><span data-stu-id="7c956-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="7c956-143">Erstellen Sie eine , `GrammarRecognizer` und übergeben Sie den Pfad an Ihre SRGS-Datei:</span><span class="sxs-lookup"><span data-stu-id="7c956-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="7c956-144">Registrieren Sie sich jetzt für das `OnPhraseRecognized` Ereignis.</span><span class="sxs-lookup"><span data-stu-id="7c956-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="7c956-145">Sie erhalten einen Rückruf mit Informationen, die in Ihrer SRGS-Grammatik angegeben sind und die Sie entsprechend verarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="7c956-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="7c956-146">Die meisten wichtigen Informationen werden im `semanticMeanings` Array bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7c956-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="7c956-147">Beginnen Sie schließlich mit der Erkennung!</span><span class="sxs-lookup"><span data-stu-id="7c956-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="7c956-148">Diktieren</span><span class="sxs-lookup"><span data-stu-id="7c956-148">Dictation</span></span>

<span data-ttu-id="7c956-149">**Namespace:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="7c956-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="7c956-150">**Typen:** *DictationRecognizer,* *SpeechError,* *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="7c956-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="7c956-151">Verwenden Sie `DictationRecognizer` , um die Sprache des Benutzers in Text zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="7c956-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="7c956-152">DictationRecognizer macht [Diktatfunktionen](../../design/voice-input.md#dictation) verfügbar und unterstützt das Registrieren und Lauschen auf Hypothesen- und Ausdrucksabschlussereignisse, sodass Sie Feedback an Ihren Benutzer senden können, während er spricht und danach.</span><span class="sxs-lookup"><span data-stu-id="7c956-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="7c956-153">`Start()` und `Stop()` -Methoden aktivieren bzw. deaktivieren die Diktaterkennung.</span><span class="sxs-lookup"><span data-stu-id="7c956-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="7c956-154">Sobald die Erkennung abgeschlossen ist, sollte sie mit freigegeben `Dispose()` werden, um die verwendeten Ressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="7c956-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="7c956-155">Diese Ressourcen werden automatisch während der Garbage Collection zu zusätzlichen Leistungskosten freigegeben, wenn sie vorher nicht freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="7c956-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="7c956-156">Es sind nur wenige Schritte erforderlich, um mit dem Diktieren zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="7c956-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="7c956-157">Erstellen eines neuen `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="7c956-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="7c956-158">Behandeln von Diktatereignissen</span><span class="sxs-lookup"><span data-stu-id="7c956-158">Handle Dictation events</span></span>
3. <span data-ttu-id="7c956-159">Starten von DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="7c956-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="7c956-160">Aktivieren der Funktion für das Diktieren</span><span class="sxs-lookup"><span data-stu-id="7c956-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="7c956-161">Die **Internetclient-** und **Mikrofonfunktionen** müssen deklariert werden, damit eine App Diktat verwenden kann:</span><span class="sxs-lookup"><span data-stu-id="7c956-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="7c956-162">Wechseln Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen > Player.**</span><span class="sxs-lookup"><span data-stu-id="7c956-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="7c956-163">Wählen Sie auf der Registerkarte **Windows Store** aus.</span><span class="sxs-lookup"><span data-stu-id="7c956-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="7c956-164">Überprüfen Sie **im Abschnitt > Veröffentlichungseinstellungen** die **InternetClient-Funktion.**</span><span class="sxs-lookup"><span data-stu-id="7c956-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="7c956-165">Wenn Sie das Mikrofon noch nicht aktiviert haben, aktivieren Sie optional die **Funktion Mikrofon.**</span><span class="sxs-lookup"><span data-stu-id="7c956-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="7c956-166">Erteilen Sie der App Berechtigungen für den Mikrofonzugriff auf Ihrem HoloLens-Gerät, sofern noch nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="7c956-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="7c956-167">Sie werden beim Starten des Geräts dazu aufgefordert, aber wenn Sie versehentlich auf "Nein" geklickt haben, können Sie die Berechtigungen in den Geräteeinstellungen ändern.</span><span class="sxs-lookup"><span data-stu-id="7c956-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="7c956-168">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="7c956-168">DictationRecognizer</span></span>

<span data-ttu-id="7c956-169">Erstellen Sie einen DictationRecognizer wie hier:</span><span class="sxs-lookup"><span data-stu-id="7c956-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="7c956-170">Es gibt vier Diktatereignisse, die abonniert und behandelt werden können, um das Diktatverhalten zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="7c956-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="7c956-171">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="7c956-171">**DictationResult**</span></span>

<span data-ttu-id="7c956-172">Dieses Ereignis wird ausgelöst, nachdem der Benutzer angehalten wurde, in der Regel am Ende eines Satzes.</span><span class="sxs-lookup"><span data-stu-id="7c956-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="7c956-173">Die vollständige erkannte Zeichenfolge wird hier zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7c956-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="7c956-174">Abonnieren Sie zunächst das `DictationResult` Ereignis:</span><span class="sxs-lookup"><span data-stu-id="7c956-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="7c956-175">Behandeln Sie dann den DictationResult-Rückruf:</span><span class="sxs-lookup"><span data-stu-id="7c956-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="7c956-176">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="7c956-176">**DictationHypothesis**</span></span>

<span data-ttu-id="7c956-177">Dieses Ereignis wird kontinuierlich ausgelöst, während der Benutzer spricht.</span><span class="sxs-lookup"><span data-stu-id="7c956-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="7c956-178">Während die Erkennende lausiert, stellt sie Text für das, was sie bisher gehört hat, zurEntspricht.</span><span class="sxs-lookup"><span data-stu-id="7c956-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="7c956-179">Abonnieren Sie zunächst das `DictationHypothesis` Ereignis:</span><span class="sxs-lookup"><span data-stu-id="7c956-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="7c956-180">Behandeln Sie dann den DictationHypothesis-Rückruf:</span><span class="sxs-lookup"><span data-stu-id="7c956-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="7c956-181">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="7c956-181">**DictationComplete**</span></span>

<span data-ttu-id="7c956-182">Dieses Ereignis wird ausgelöst, wenn die Erkennende beendet wird, unabhängig davon, ob von Stop() aufgerufen wird, ein Timeout auftritt oder ein anderer Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="7c956-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="7c956-183">Abonnieren Sie zunächst das `DictationComplete` Ereignis:</span><span class="sxs-lookup"><span data-stu-id="7c956-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="7c956-184">Verarbeiten Sie dann den DictationComplete-Rückruf:</span><span class="sxs-lookup"><span data-stu-id="7c956-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="7c956-185">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="7c956-185">**DictationError**</span></span>

<span data-ttu-id="7c956-186">Dieses Ereignis wird ausgelöst, wenn ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="7c956-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="7c956-187">Abonnieren Sie zunächst das `DictationError` Ereignis:</span><span class="sxs-lookup"><span data-stu-id="7c956-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="7c956-188">Behandeln Sie dann den DictationError-Rückruf:</span><span class="sxs-lookup"><span data-stu-id="7c956-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="7c956-189">Nachdem Sie die für Sie interessierenden Diktatereignisse abonniert und behandelt haben, starten Sie die Diktaterkennung, um mit dem Empfangen von Ereignissen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="7c956-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="7c956-190">Wenn Sie DictationRecognizer nicht mehr beibehalten möchten, müssen Sie das Abonnement der Ereignisse kündigen und DictationRecognizer löschen.</span><span class="sxs-lookup"><span data-stu-id="7c956-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="7c956-191">**Tipps**</span><span class="sxs-lookup"><span data-stu-id="7c956-191">**Tips**</span></span>
* <span data-ttu-id="7c956-192">`Start()` und `Stop()` -Methoden aktivieren bzw. deaktivieren die Diktaterkennung.</span><span class="sxs-lookup"><span data-stu-id="7c956-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="7c956-193">Sobald die Erkennung abgeschlossen ist, muss sie mit freigegeben werden, `Dispose()` um die verwendeten Ressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="7c956-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="7c956-194">Diese Ressourcen werden automatisch während der Garbage Collection zu zusätzlichen Leistungskosten freigegeben, wenn sie vorher nicht freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="7c956-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="7c956-195">Timeouts treten nach einem festgelegten Zeitraum auf.</span><span class="sxs-lookup"><span data-stu-id="7c956-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="7c956-196">Sie können überprüfen, ob diese Timeouts im `DictationComplete` -Ereignis vorliegen.</span><span class="sxs-lookup"><span data-stu-id="7c956-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="7c956-197">Es gibt zwei Timeouts, die Sie beachten sollten:</span><span class="sxs-lookup"><span data-stu-id="7c956-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="7c956-198">Wenn die Erkennung gestartet wird und in den ersten fünf Sekunden keine Audiodaten mehr hören, tritt ein Time out auf.</span><span class="sxs-lookup"><span data-stu-id="7c956-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="7c956-199">Wenn die Erkennung ein Ergebnis erhalten hat, aber dann 20 Sekunden still wird, tritt ein Time out auf.</span><span class="sxs-lookup"><span data-stu-id="7c956-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="7c956-200">Verwenden von Ausdruckserkennung und Diktat</span><span class="sxs-lookup"><span data-stu-id="7c956-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="7c956-201">Wenn Sie in Ihrer App sowohl Ausdruckserkennung als auch Diktat verwenden möchten, müssen Sie eines vollständig herunterfahren, bevor Sie den anderen starten können.</span><span class="sxs-lookup"><span data-stu-id="7c956-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="7c956-202">Wenn mehrere KeywordRecognizers ausgeführt werden, können Sie sie alle gleichzeitig mit herunterfahren:</span><span class="sxs-lookup"><span data-stu-id="7c956-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="7c956-203">Sie können `Restart()` aufrufen, um alle Erkennungen in ihrem vorherigen Zustand wiederherzustellen, nachdem DictationRecognizer beendet wurde:</span><span class="sxs-lookup"><span data-stu-id="7c956-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="7c956-204">Sie können auch einfach einen KeywordRecognizer starten, der auch das PhraseRecognitionSystem neu startet.</span><span class="sxs-lookup"><span data-stu-id="7c956-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="7c956-205">Spracheingabe im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="7c956-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="7c956-206">MrTK-Beispiele für die Spracheingabe finden Sie in den folgenden Demoszenen:</span><span class="sxs-lookup"><span data-stu-id="7c956-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="7c956-207">Diktieren</span><span class="sxs-lookup"><span data-stu-id="7c956-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="7c956-208">Speech</span><span class="sxs-lookup"><span data-stu-id="7c956-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="7c956-209">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="7c956-209">Next Development Checkpoint</span></span>

<span data-ttu-id="7c956-210">Wenn Sie der von uns festgelegten Unity-Entwicklungsprüfpunkt-Journey folgen, sind Sie die nächste Aufgabe, die Funktionen und APIs Mixed Reality Plattform zu erkunden:</span><span class="sxs-lookup"><span data-stu-id="7c956-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c956-211">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="7c956-211">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="7c956-212">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="7c956-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>