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
# <a name="voice-input-in-unity"></a>Spracheingabe in Unity

> [!CAUTION]
> Bevor Sie beginnen, sollten Sie das Unity-Plug-In für das Cognitive Speech Services SDK verwenden. Das Plug-In bietet bessere Ergebnisse der Sprachgenauigkeit und einfachen Zugriff auf die Spracherkennungsdecodierung sowie erweiterte Sprachfunktionen wie Dialog, absichtsbasierte Interaktion, Übersetzung, Text-zu-Sprache-Synthese und Spracherkennung in natürlicher Sprache. Sehen Sie sich zunächst das [Beispiel und](/azure/cognitive-services/speech-service/quickstart-csharp-unity)die Dokumentation an.

Unity bietet drei Möglichkeiten zum Hinzufügen von [Spracheingaben](../../design/voice-input.md) zu Ihrer Unity-Anwendung, von denen die ersten beiden Arten von PhraseRecognizer sind:
* `KeywordRecognizer`stellt Ihrer App ein Array von Zeichenfolgenbefehlen bereit, auf die gelecht werden soll.
* Gibt `GrammarRecognizer` Ihrer App eine SRGS-Datei, die eine bestimmte Grammatik definiert, auf die gelescht werden soll.
* `DictationRecognizer`Mit kann Ihre App auf jedes Wort lauschen und dem Benutzer eine Notiz oder eine andere Anzeige seiner Sprache bereitstellen.

> [!NOTE]
> Diktat und Ausdruckserkennung können nicht gleichzeitig verarbeitet werden. Wenn ein GrammarRecognizer oder KeywordRecognizer aktiv ist, kann ein DictationRecognizer nicht aktiv sein und umgekehrt.

## <a name="enabling-the-capability-for-voice"></a>Aktivieren der Funktion für Voice

Die **Mikrofonfunktion** muss deklariert werden, damit eine App Spracheingaben verwenden kann.
1. Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen > Player.**
2. Wählen Sie die Registerkarte **Windows Store** aus.
3. Überprüfen Sie im Abschnitt **Veröffentlichungseinstellungen > Funktionen** die **Funktion Mikrofon.**
4. Erteilen von Berechtigungen für die App für den Mikrofonzugriff auf Ihrem HoloLens-Gerät
    * Sie werden beim Starten des Geräts dazu aufgefordert, aber wenn Sie versehentlich auf "Nein" geklickt haben, können Sie die Berechtigungen in den Geräteeinstellungen ändern.

## <a name="phrase-recognition"></a>Ausdruckserkennung

Damit Ihre App auf bestimmte Ausdrücke lauscht, die vom Benutzer gesprochen werden, müssen Sie folgende Aktionen ergreifen:
1. Geben Sie an, auf welche Ausdrücke mit oder lauschen `KeywordRecognizer` soll. `GrammarRecognizer`
2. Behandeln des `OnPhraseRecognized` Ereignisses und Ergreifen von Aktionen entsprechend dem erkannten Ausdruck

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Typen:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Wir benötigen einige using-Anweisungen, um einige Tastatureingaben zu speichern:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Fügen Sie ihrer Klasse dann einige Felder hinzu, um die Such- und Schlüsselwort->aktionswörterbuch zu speichern:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Fügen Sie nun dem Wörterbuch ein Schlüsselwort hinzu, z. B. in einer `Start()` -Methode. Wir fügen das Schlüsselwort "activate" in diesem Beispiel hinzu:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Erstellen Sie die Schlüsselwortsuche, und teilen Sie ihr mit, was wir erkennen möchten:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Registrieren Sie sich jetzt für das `OnPhraseRecognized` Ereignis.

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Ein Beispielhandler ist:

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

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Typen:** *GrammarRecognizer,* *PhraseRecognizedEventArgs,* *SpeechError,* *SpeechSystemStatus*

Der GrammarRecognizer wird verwendet, wenn Sie Ihre Erkennungsgrammatik mithilfe von SRGS angeben. Dies kann nützlich sein, wenn Ihre App über mehr als nur einige Schlüsselwörter verfügt, wenn Sie komplexere Ausdrücke erkennen möchten oder wenn Sie befehlssätze einfach aktivieren und deaktivieren möchten. Informationen zum Dateiformat finden Sie unter Erstellen von Grammatiken mit [SRGS XML.](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14))

Sobald Sie über ihre SRGS-Grammatik verfügen, befindet sie sich in Ihrem Projekt in einem [StreamingAssets-Ordner:](https://docs.unity3d.com/Manual/StreamingAssets.html)

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Erstellen Sie eine , `GrammarRecognizer` und übergeben Sie den Pfad an Ihre SRGS-Datei:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Registrieren Sie sich jetzt für das `OnPhraseRecognized` Ereignis.

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Sie erhalten einen Rückruf mit Informationen, die in Ihrer SRGS-Grammatik angegeben sind und die Sie entsprechend verarbeiten können. Die meisten wichtigen Informationen werden im `semanticMeanings` Array bereitgestellt.

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

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Typen:** *DictationRecognizer,* *SpeechError,* *SpeechSystemStatus*

Verwenden Sie `DictationRecognizer` , um die Sprache des Benutzers in Text zu konvertieren. DictationRecognizer macht [Diktatfunktionen](../../design/voice-input.md#dictation) verfügbar und unterstützt das Registrieren und Lauschen auf Hypothesen- und Ausdrucksabschlussereignisse, sodass Sie Feedback an Ihren Benutzer senden können, während er spricht und danach. `Start()` und `Stop()` -Methoden aktivieren bzw. deaktivieren die Diktaterkennung. Sobald die Erkennung abgeschlossen ist, sollte sie mit freigegeben `Dispose()` werden, um die verwendeten Ressourcen freizugeben. Diese Ressourcen werden automatisch während der Garbage Collection zu zusätzlichen Leistungskosten freigegeben, wenn sie vorher nicht freigegeben werden.

Es sind nur wenige Schritte erforderlich, um mit dem Diktieren zu beginnen:
1. Erstellen eines neuen `DictationRecognizer`
2. Behandeln von Diktatereignissen
3. Starten von DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Aktivieren der Funktion für das Diktieren

Die **Internetclient-** und **Mikrofonfunktionen** müssen deklariert werden, damit eine App Diktat verwenden kann:
1. Wechseln Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen > Player.**
2. Wählen Sie auf der Registerkarte **Windows Store** aus.
3. Überprüfen Sie **im Abschnitt > Veröffentlichungseinstellungen** die **InternetClient-Funktion.**
    * Wenn Sie das Mikrofon noch nicht aktiviert haben, aktivieren Sie optional die **Funktion Mikrofon.**
4. Erteilen Sie der App Berechtigungen für den Mikrofonzugriff auf Ihrem HoloLens-Gerät, sofern noch nicht vorhanden.
    * Sie werden beim Starten des Geräts dazu aufgefordert, aber wenn Sie versehentlich auf "Nein" geklickt haben, können Sie die Berechtigungen in den Geräteeinstellungen ändern.

### <a name="dictationrecognizer"></a>DictationRecognizer

Erstellen Sie einen DictationRecognizer wie hier:

```
dictationRecognizer = new DictationRecognizer();
```

Es gibt vier Diktatereignisse, die abonniert und behandelt werden können, um das Diktatverhalten zu implementieren.
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**DictationResult**

Dieses Ereignis wird ausgelöst, nachdem der Benutzer angehalten wurde, in der Regel am Ende eines Satzes. Die vollständige erkannte Zeichenfolge wird hier zurückgegeben.

Abonnieren Sie zunächst das `DictationResult` Ereignis:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Behandeln Sie dann den DictationResult-Rückruf:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Dieses Ereignis wird kontinuierlich ausgelöst, während der Benutzer spricht. Während die Erkennende lausiert, stellt sie Text für das, was sie bisher gehört hat, zurEntspricht.

Abonnieren Sie zunächst das `DictationHypothesis` Ereignis:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Behandeln Sie dann den DictationHypothesis-Rückruf:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Dieses Ereignis wird ausgelöst, wenn die Erkennende beendet wird, unabhängig davon, ob von Stop() aufgerufen wird, ein Timeout auftritt oder ein anderer Fehler auftritt.

Abonnieren Sie zunächst das `DictationComplete` Ereignis:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Verarbeiten Sie dann den DictationComplete-Rückruf:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Dieses Ereignis wird ausgelöst, wenn ein Fehler auftritt.

Abonnieren Sie zunächst das `DictationError` Ereignis:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Behandeln Sie dann den DictationError-Rückruf:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Nachdem Sie die für Sie interessierenden Diktatereignisse abonniert und behandelt haben, starten Sie die Diktaterkennung, um mit dem Empfangen von Ereignissen zu beginnen.

```
dictationRecognizer.Start();
```

Wenn Sie DictationRecognizer nicht mehr beibehalten möchten, müssen Sie das Abonnement der Ereignisse kündigen und DictationRecognizer löschen.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Tipps**
* `Start()` und `Stop()` -Methoden aktivieren bzw. deaktivieren die Diktaterkennung.
* Sobald die Erkennung abgeschlossen ist, muss sie mit freigegeben werden, `Dispose()` um die verwendeten Ressourcen freizugeben. Diese Ressourcen werden automatisch während der Garbage Collection zu zusätzlichen Leistungskosten freigegeben, wenn sie vorher nicht freigegeben werden.
* Timeouts treten nach einem festgelegten Zeitraum auf. Sie können überprüfen, ob diese Timeouts im `DictationComplete` -Ereignis vorliegen. Es gibt zwei Timeouts, die Sie beachten sollten:
   1. Wenn die Erkennung gestartet wird und in den ersten fünf Sekunden keine Audiodaten mehr hören, tritt ein Time out auf.
   2. Wenn die Erkennung ein Ergebnis erhalten hat, aber dann 20 Sekunden still wird, tritt ein Time out auf.

## <a name="using-both-phrase-recognition-and-dictation"></a>Verwenden von Ausdruckserkennung und Diktat

Wenn Sie in Ihrer App sowohl Ausdruckserkennung als auch Diktat verwenden möchten, müssen Sie eines vollständig herunterfahren, bevor Sie den anderen starten können. Wenn mehrere KeywordRecognizers ausgeführt werden, können Sie sie alle gleichzeitig mit herunterfahren:

```
PhraseRecognitionSystem.Shutdown();
```

Sie können `Restart()` aufrufen, um alle Erkennungen in ihrem vorherigen Zustand wiederherzustellen, nachdem DictationRecognizer beendet wurde:

```
PhraseRecognitionSystem.Restart();
```

Sie können auch einfach einen KeywordRecognizer starten, der auch das PhraseRecognitionSystem neu startet.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Spracheingabe im Mixed Reality Toolkit

MrTK-Beispiele für die Spracheingabe finden Sie in den folgenden Demoszenen:
* [Diktieren](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Speech](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der von uns festgelegten Unity-Entwicklungsprüfpunkt-Journey folgen, sind Sie die nächste Aufgabe, die Funktionen und APIs Mixed Reality Plattform zu erkunden:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.