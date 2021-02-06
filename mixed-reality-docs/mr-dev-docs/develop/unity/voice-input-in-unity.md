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
# <a name="voice-input-in-unity"></a>Spracheingabe in Unity

> [!CAUTION]
> Bevor Sie beginnen, sollten Sie das Unity-Plug-in für das Cognitive Speech Services SDK verwenden. Das Plug-in bietet bessere Ergebnisse bei der sprach Genauigkeit und einen einfachen Zugriff auf die Sprache-zu-Text-Decodierung sowie erweiterte sprach Features wie Dialog, Intent-basierte Interaktion, Übersetzung, Text-zu-Sprache-Synthese und Spracherkennung in natürlicher Sprache. Informationen zu den ersten Schritten finden Sie im [Beispiel und](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity)in der Dokumentation.

Unity bietet drei Möglichkeiten zum Hinzufügen von [Spracheingaben](../../design/voice-input.md) zu ihrer Unity-Anwendung, die ersten beiden Typen von phraserecognizer:
* Der stellt der `KeywordRecognizer` App ein Array von Zeichen folgen Befehlen zur Verfügung, die überwacht werden sollen.
* Der weist `GrammarRecognizer` Ihrer APP eine SRGS-Datei zu, die eine bestimmte Grammatik zum lauschen definiert.
* Mit dem kann `DictationRecognizer` Ihre APP auf ein beliebiges Wort lauschen und dem Benutzer einen Hinweis oder eine andere Anzeige seiner Sprache bereitstellen.

> [!NOTE]
> Diktat-und Ausdrucks Erkennung können nicht gleichzeitig behandelt werden. Wenn ein Grammatik oder keywordrecognizer aktiv ist, kann ein "diktationerkenzer" nicht aktiv sein und umgekehrt.

## <a name="enabling-the-capability-for-voice"></a>Aktivieren der Sprachfunktion

Die **Mikrofon** Funktion muss für eine APP deklariert werden, um eine Spracheingabe zu verwenden.
1. Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen > Player** .
2. Registerkarte " **Windows Store** " auswählen
3. Überprüfen Sie im Abschnitt **Veröffentlichungs Einstellungen > Funktionen** die **Mikrofon** Funktion.
4. Erteilen von Berechtigungen für die APP für den Mikrofon Zugriff auf Ihrem hololens-Gerät
    * Sie werden zum Starten des Geräts aufgefordert, aber wenn Sie versehentlich auf "Nein" geklickt haben, können Sie die Berechtigungen in den Geräteeinstellungen ändern.

## <a name="phrase-recognition"></a>Ausdrucks Erkennung

Damit Ihre APP auf bestimmte vom Benutzer gesprochene Ausdrücke lauschen kann, müssen Sie Folgendes tun:
1. Angeben der abzuhörenden Ausdrücke mithilfe von `KeywordRecognizer` oder `GrammarRecognizer`
2. Behandeln `OnPhraseRecognized` Sie das-Ereignis, und ergreifen Sie entsprechende Aktionen für den erkannten Ausdruck.

### <a name="keywordrecognizer"></a>Keywordrecognizer

**Namespace:** *unityengine. Windows. Speech*<br>
**Typen:** *keywordrecognizer*, *phraserecognizedeventargs*, *delegatfehler*, Sprech *Systemstatus*

Zum Speichern einiger Tastatureingaben benötigen wir einige using-Anweisungen:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Fügen Sie der Klasse nun einige Felder hinzu, um das Erkennungs-und Schlüsselwort >Aktions Wörterbuch zu speichern:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Fügen Sie nun dem Wörterbuch ein Schlüsselwort hinzu, z. b. in einer- `Start()` Methode. Das Schlüsselwort "aktivieren" wird in diesem Beispiel hinzugefügt:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Erstellen Sie die Schlüsselwort Erkennung, und teilen Sie Ihnen mit, was wir erkennen möchten:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Registrieren Sie sich jetzt für das `OnPhraseRecognized` Ereignis.

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Ein Beispiel Handler ist:

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

Beginnen Sie schließlich mit der Erkennung!

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>Grammarerkenzer

**Namespace:** *unityengine. Windows. Speech*<br>
**Typen**: *grammarerkenzer*, *phraserecognizedeventargs*, *delegatfehler*, Sprech *Systemstatus*

Die Grammatiken werden verwendet, wenn Sie Ihre Erkennungs Grammatik mithilfe von SRGS angeben. Dies kann hilfreich sein, wenn Ihre APP mehr als nur einige wenige Schlüsselwörter aufweist, wenn Sie komplexere Ausdrücke erkennen möchten, oder wenn Sie Sätze von Befehlen problemlos aktivieren und deaktivieren möchten. Informationen zum Dateiformat finden [Sie unter Erstellen von Grammatiken mithilfe von SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) .

Sobald Sie die SRGS-Grammatik haben und sich in Ihrem Projekt in einem [Ordner "streamingassets](https://docs.unity3d.com/Manual/StreamingAssets.html)" befinden:

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Erstellen `GrammarRecognizer` Sie eine, und übergeben Sie Ihr den Pfad zu ihrer SRGS-Datei:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Registrieren Sie sich jetzt für das `OnPhraseRecognized` Ereignis.

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Sie erhalten einen Rückruf mit Informationen, die in der SRGS-Grammatik angegeben sind, die Sie entsprechend behandeln können. Die meisten wichtigen Informationen werden im-Array bereitgestellt `semanticMeanings` .

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Beginnen Sie schließlich mit der Erkennung!

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Diktieren

**Namespace:** *unityengine. Windows. Speech*<br>
**Typen**: " *diktationerkenzer*", "sprecherfehler", " *Redner Systemstatus* 

Verwenden `DictationRecognizer` Sie, um die Sprache des Benutzers in Text zu konvertieren. Der Diktat-Erkennungs Modul macht [Diktat](../../design/voice-input.md#dictation) Funktionen verfügbar und unterstützt das registrieren und lauschen auf Hypothese und Ausdrucks fertige Ereignisse, sodass Sie Ihrem Benutzer Feedback geben können, während Sie sprechen und danach. `Start()` die `Stop()` Methoden und aktivieren bzw. deaktivieren die Diktat Erkennung. Sobald die Erkennung erfolgt ist, sollte Sie mithilfe von verworfen werden, `Dispose()` um die verwendeten Ressourcen freizugeben. Diese Ressourcen werden während der Garbage Collection automatisch freigegeben, wenn Sie noch nicht freigegeben werden.

Für den Einstieg in das Diktat müssen nur wenige Schritte ausgeführt werden:
1. Erstellen eines neuen `DictationRecognizer`
2. Behandeln von Diktat Ereignissen
3. "Diktationerkenzer" starten

### <a name="enabling-the-capability-for-dictation"></a>Aktivieren der Funktion für das Diktat

Die **Internet Client** -und **Mikrofon** Funktionen müssen für eine APP deklariert werden, um die Diktat Verwendung zu verwenden:
1. Wechseln Sie im Unity-Editor zu **Edit > Project Settings > Player** .
2. Auf der Registerkarte " **Windows Store** " auswählen
3. Überprüfen Sie im Abschnitt **Veröffentlichungs Einstellungen > Funktionen** die Funktion **Internetclient** .
    * Wenn Sie das Mikrofon nicht bereits aktiviert haben, überprüfen Sie optional die **Mikrofon** Funktion.
4. Erteilen von Berechtigungen für die APP für den Zugriff auf das Mikrofon auf Ihrem hololens-Gerät, sofern noch nicht geschehen
    * Sie werden zum Starten des Geräts aufgefordert, aber wenn Sie versehentlich auf "Nein" geklickt haben, können Sie die Berechtigungen in den Geräteeinstellungen ändern.

### <a name="dictationrecognizer"></a>Diktationerkenzer

Erstellen Sie einen "diktationerkenzer" wie folgt:

```
dictationRecognizer = new DictationRecognizer();
```

Es gibt vier Diktat Ereignisse, die abonniert und behandelt werden können, um das Diktat Verhalten zu implementieren.
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**"Ditationresult"**

Dieses Ereignis wird ausgelöst, nachdem der Benutzer angehalten wurde, in der Regel am Ende eines Satzes. Hier wird die vollständig erkannte Zeichenfolge zurückgegeben.

Abonnieren Sie zunächst das- `DictationResult` Ereignis:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Behandeln Sie dann den "-Rückruf":

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**"Ditationhypothese"**

Dieses Ereignis wird fortlaufend ausgelöst, während der Benutzer spricht. Wie die Erkennung hört, bietet Sie Text zu den bisher gehörenden.

Abonnieren Sie zunächst das- `DictationHypothesis` Ereignis:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Behandeln Sie dann den-Rückruf von "ditationhypothese":

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**"Ditationcomplete"**

Dieses Ereignis wird ausgelöst, wenn die Erkennung angehalten wird, und zwar unabhängig davon, ob von "Stopp ()" aufgerufen wird, ein Timeout auftritt oder ein anderer Fehler vorliegt.

Abonnieren Sie zunächst das- `DictationComplete` Ereignis:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Behandeln Sie dann den-Rückruf von "ditationcomplete":

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**"Ditationerror"**

Dieses Ereignis wird ausgelöst, wenn ein Fehler auftritt.

Abonnieren Sie zunächst das- `DictationError` Ereignis:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Behandeln Sie dann den "-Rückruf"-Rückruf:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Nachdem Sie die Diktat Ereignisse abonniert und behandelt haben, die Ihnen wichtig sind, starten Sie die Diktat Erkennung, um mit dem empfangen von Ereignissen zu beginnen.

```
dictationRecognizer.Start();
```

Wenn Sie die "diktationerkenzer" nicht mehr benötigen, müssen Sie die Ereignisse kündigen und den "diktationerkenzer" verwerfen.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Tipps**
* `Start()` die `Stop()` Methoden und aktivieren bzw. deaktivieren die Diktat Erkennung.
* Sobald die Erkennung erfolgt ist, muss Sie mithilfe von verworfen werden, `Dispose()` um die verwendeten Ressourcen freizugeben. Diese Ressourcen werden während der Garbage Collection automatisch freigegeben, wenn Sie noch nicht freigegeben werden.
* Timeouts treten nach einer festgelegten Zeitspanne auf. Sie können diese Timeouts im Ereignis überprüfen `DictationComplete` . Es gibt zwei Timeouts, die Sie beachten sollten:
   1. Wenn die Erkennung gestartet wird und in den ersten fünf Sekunden keine Audiodaten mehr angezeigt werden, tritt ein Timeout auf.
   2. Wenn die Erkennung ein Ergebnis erhalten hat, aber dann 20 Sekunden lang Stillen wird, tritt ein Timeout auf.

## <a name="using-both-phrase-recognition-and-dictation"></a>Verwenden der Ausdrucks Erkennung und-diktierung

Wenn Sie in Ihrer APP sowohl die Erkennung als auch das Diktat von Ausdrücken verwenden möchten, müssen Sie eine vollständige Herunterfahren, bevor Sie die andere starten können. Wenn mehrere keywordrecognizers ausgeführt werden, können Sie Sie mit folgenden Aktionen gleichzeitig Herunterfahren:

```
PhraseRecognitionSystem.Shutdown();
```

Sie können aufzurufen `Restart()` , um alle erkenners in Ihrem vorherigen Zustand wiederherzustellen, nachdem der "diktationerkenzer" angehalten wurde:

```
PhraseRecognitionSystem.Restart();
```

Sie können auch einfach einen keywordrecognizer starten, mit dem auch das phraserecognitionsystem neu gestartet wird.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Spracheingabe im Mixed Reality Toolkit

In den folgenden Demoszenen finden Sie mrtk-Beispiele für die Spracheingabe:
* [Diktieren](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Speech](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Prüf Punkt Journey folgen, haben wir die nächste Aufgabe darin, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.