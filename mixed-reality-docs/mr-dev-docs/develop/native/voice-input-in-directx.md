---
title: Spracheingabe in DirectX
description: Erläutert das Implementieren von Sprachbefehlen und der Erkennung kleiner Ausdrücke und Sätze in einer DirectX-App für Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Exemplarische Vorgehensweise, Sprachbefehl, Ausdruck, Erkennung, Sprache, Directx, Plattform, Cortana, Windows Mixed Reality
ms.openlocfilehash: e30d5c2101bed4b613111b6131a3e94d654c3ff5b1e913f4d8e275ffc1a2776a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221840"
---
# <a name="voice-input-in-directx"></a>Spracheingabe in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren nativen WinRT-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API empfohlen.](openxr-getting-started.md)**

In diesem Artikel wird erläutert, wie Sie [Sprachbefehle](../../design/voice-input.md) sowie die Erkennung kleiner Ausdrücke und Sätze in einer DirectX-App für Windows Mixed Reality.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel verwenden C++/CX anstelle von C++17-kompatiblem C++/WinRT, das in der holografischen C++-Projektvorlage [verwendet wird.](creating-a-holographic-directx-project.md)  Die Konzepte sind für ein C++/WinRT-Projekt gleichwertig, aber Sie müssen den Code übersetzen.

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a>Verwenden von SpeechRecognizer für die kontinuierliche Spracherkennung

In diesem Abschnitt wird beschrieben, wie Sie die kontinuierliche Spracherkennung verwenden, um Sprachbefehle in Ihrer App zu aktivieren. In dieser exemplarischen Vorgehensweise wird Code aus dem [HolographicVoiceInput-Beispiel](https://go.microsoft.com/fwlink/p/?LinkId=844964) verwendet. Wenn das Beispiel ausgeführt wird, sprechen Sie den Namen eines der registrierten Farbbefehle, um die Farbe des sich drehenden Würfels zu ändern.

Erstellen Sie zunächst eine neue *Windows::Media::SpeechRecognition::SpeechRecognizer-Instanz.*

Von *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState:*

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Erstellen Sie eine Liste von Sprachbefehlen, auf die die Recognizer lauschen soll. Hier erstellen wir eine Reihe von Befehlen, um die Farbe eines Hologramms zu ändern. Der Einfachheit halber erstellen wir auch die Daten, die wir später für die Befehle verwenden.

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

Sie können phonetische Wörter verwenden, die möglicherweise nicht in einem Wörterbuch enthalten sind, um Befehle anzugeben.

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Um die Befehlsliste in die Liste der Einschränkungen für die Spracherkennung zu laden, verwenden Sie ein [SpeechRecognitionListConstraint-Objekt.](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint)

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

Abonnieren Sie das [ResultGenerated-Ereignis](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession) für die [SpeechContinuousRecognitionSession der Spracherkennung.](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession) Dieses Ereignis benachrichtigt Ihre App, wenn einer Ihrer Befehle erkannt wurde.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

Ihr *OnResultGenerated-Ereignishandler* empfängt Ereignisdaten in einer [SpeechContinuousRecognitionResultGeneratedEventArgs-Instanz.](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs) Wenn die Konfidenz den von Ihnen definierten Schwellenwert überschreitet, sollte Ihre App beachten, dass das Ereignis passiert ist. Speichern Sie die Ereignisdaten, damit Sie sie in einer späteren Updateschleife verwenden können.

Von *HolographicVoiceInputSampleMain.cpp:*

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

In unserem Beispielcode ändern wir die Farbe des sich drehenden Hologrammcubes gemäß dem Befehl des Benutzers.

Von *HolographicVoiceInputSampleMain::Update:*

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-one-shot-recognition"></a>Verwenden der "einmaligen" Erkennung

Sie können eine Spracherkennung konfigurieren, um auf Ausdrücke oder Sätze zu lauschen, die der Benutzer spricht. In diesem Fall wenden wir eine *SpeechRecognitionTopicConstraint* an, die der Spracherkennung anspricht, welche Art von Eingabe zu erwarten ist. Hier ist ein App-Workflow für dieses Szenario:
1. Ihre App erstellt den SpeechRecognizer, stellt Benutzeroberflächenaufforderungen zur Verfügung und beginnt mit dem Lauschen auf einen gesprochenen Befehl.
2. Der Benutzer spricht einen Ausdruck oder Satz.
3. Die Spracherkennung des Benutzers erfolgt, und ein Ergebnis wird an die App zurückgegeben. An diesem Punkt sollte Ihre App eine Benutzeroberflächenaufforderung bereitstellen, um anzugeben, dass die Erkennung erfolgt ist.
4. Abhängig vom Vertrauensgrad, auf den Sie reagieren möchten, und dem Zuverlässigkeitsgrad des Spracherkennungsergebnis kann Ihre App das Ergebnis verarbeiten und entsprechend reagieren.

In diesem Abschnitt wird beschrieben, wie Sie einen SpeechRecognizer erstellen, die Einschränkung kompilieren und auf Spracheingaben lauschen.

Der folgende Code kompiliert die Themeneinschränkung, die in diesem Fall für die Websuche optimiert ist.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Wenn die Kompilierung erfolgreich ist, können wir mit der Spracherkennung fortfahren.

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

Das Ergebnis wird dann an die App zurückgegeben. Wenn wir im Ergebnis sicher genug sind, können wir den Befehl verarbeiten. In diesem Codebeispiel werden Ergebnisse mit mindestens mittlerer Konfidenz verarbeitet.

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

Achten Sie bei jeder Verwendung der Spracherkennung auf Ausnahmen, die darauf hindeuten können, dass der Benutzer das Mikrofon in den Systemdatenschutzeinstellungen deaktiviert hat. Dies kann während der Initialisierung oder Erkennung geschehen.

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

> [!NOTE]
> Es gibt mehrere vordefinierte [SpeechRecognitionScenarios,](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) mit denen Sie die Spracherkennung optimieren können.

* Verwenden Sie das Diktatszenario, um das Diktat zu optimieren.<br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* Verwenden Sie für Sprachwebsuchen die folgende webspezifische Szenarioeinschränkung.

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* Verwenden Sie die Formulareinschränkung zum Ausfüllen von Formularen. In diesem Fall ist es am besten, ihre eigene Grammatik anzuwenden, die für das Ausfüllen des Formulars optimiert ist.

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* Sie können Ihre eigene Grammatik im SRGS-Format bereitstellen.

## <a name="use-continuous-recognition"></a>Verwenden der kontinuierlichen Erkennung

Informationen zum Szenario des kontinuierlichen Diktats finden Sie im Windows 10 [UWP-Sprachcodebeispiel](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).

## <a name="handle-quality-degradation"></a>Behandeln von Qualitätseinbußen

Umgebungsbedingungen beeinträchtigen manchmal die Spracherkennung. Beispielsweise kann der Raum zu laut sein, oder der Benutzer kann zu laut sprechen. Nach Möglichkeit stellt die Spracherkennungs-API Informationen zu den Bedingungen bereit, die die Qualitätsbeeinträchtigung verursacht haben. Diese Informationen werden über ein WinRT-Ereignis an Ihre App pusht. Das folgende Beispiel zeigt, wie Dieses Ereignis abonniert wird.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

In unserem Codebeispiel schreiben wir die Bedingungeninformationen in die Debugkonsole. Eine App möchte dem Benutzer möglicherweise Über die Benutzeroberfläche, sprachsynthese und eine andere Methode Feedback geben. Oder es muss sich anders verhalten, wenn Sprache durch eine vorübergehende Qualitätsreduzierung unterbrochen wird.

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

Wenn Sie keine Verweisklassen zum Erstellen Ihrer DirectX-App verwenden, müssen Sie das Ereignis kündigen, bevor Sie Ihre Spracherkennung veröffentlichen oder neu erstellen. HolographicSpeechPromptSample verfügt über eine Routine zum Beenden der Erkennung und Zum Kündigen von Ereignissen.

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a>Verwenden der Sprachsynthese zum Bereitstellen akustischer Eingabeaufforderungen

Die holografischen Sprachbeispiele verwenden die Sprachsynthese, um dem Benutzer akustische Anweisungen zu geben. In diesem Abschnitt wird gezeigt, wie Sie ein synthetisiertes Stimmbeispiel erstellen und dann über die HRTF-Audio-APIs wieder geben.

Es wird empfohlen, ihre eigenen Spracheingabeaufforderungen zur Verfügung zu stellen, wenn Sie eine Ausdruckseingabe anfordern. Eingabeaufforderungen können auch angeben, wann Sprachbefehle für ein Szenario mit kontinuierlicher Erkennung gesprochen werden können. Im folgenden Beispiel wird die Verwendung eines Sprachsynthetizers dafür veranschaulicht. Sie können auch einen vorab aufgezeichneten Sprachclip, eine visuelle Benutzeroberfläche oder einen anderen Indikator für die Zu sagenden Elemente verwenden, z. B. in Szenarien, in denen die Eingabeaufforderung nicht dynamisch ist.

Erstellen Sie zunächst das SpeechSynthesizer-Objekt.

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

Sie benötigen auch eine Zeichenfolge, die den zu synthetisierten Text enthält.

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

Sprache wird asynchron über SynthesizeTextToStreamAsync synthetisiert. Hier starten wir eine asynchrone Aufgabe, um die Sprache zu synthetisieren.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

Die Sprachsynthese wird als Bytestream gesendet. Wir können diesen Bytestream verwenden, um eine XAudio2-Stimme zu initialisieren. Für unsere holografischen Codebeispiele geben wir es als HRTF-Audioeffekt wieder.

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

Wie bei der Spracherkennung löst die Sprachsynthese eine Ausnahme aus, wenn etwas schief geht.

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a>Siehe auch
* [Entwurf der Sprach-App](/windows/uwp/design/input/speech-interactions)
* [SpeechRecognitionAndSynthesis-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)