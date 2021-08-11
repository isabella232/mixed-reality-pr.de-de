---
title: 'HoloLens (1. Generation) Eingabe 212: Sprache'
description: Befolgen Sie diese exemplarische Vorgehensweise zum Programmieren mit Unity, Visual Studio und HoloLens, um die Details der Sprachkonzepte zu erfahren.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, voice, HoloLens, Mixed Reality Academy, unity, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset, Windows 10
ms.openlocfilehash: 75a1d32ae72a07b68fc65c40035109c468adb1080070240827eeb253eb4a03f4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207366"
---
# <a name="hololens-1st-gen-input-212-voice"></a>HoloLens (1. Generation) Eingabe 212: Stimme

>[!IMPORTANT]
>Die Mixed Reality Academy-Tutorials wurden mit HoloLens (1. Generation), Unity 2017 und Mixed Reality immersive Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen. Diese Tutorials werden **_nicht mit_** den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden, und sind möglicherweise nicht mit neueren Versionen von Unity kompatibel.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](mrlearning-base.md) für HoloLens 2 veröffentlicht.

[Die Spracheingabe](../../../design/voice-input.md) bietet uns eine weitere Möglichkeit, mit unseren Hologrammen zu interagieren. Sprachbefehle funktionieren auf sehr natürliche und einfache Weise. Entwerfen Sie Ihre Sprachbefehle so, dass sie:

* Natural
* Leicht zu merken
* Kontext angemessen
* Ausreichend unterschiedlich von anderen Optionen innerhalb desselben Kontexts

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md)haben wir den KeywordRecognizer verwendet, um zwei einfache Sprachbefehle zu erstellen. In MR Input 212 werden wir tiefer in die Tiefe gehen und erfahren, wie Sie:

* Entwerfen Sie Sprachbefehle, die für die sprachoptimierte HoloLens sind.
* Machen Sie den Benutzer darauf aufmerksam, welche Sprachbefehle verfügbar sind.
* Bestätigen Sie, dass wir den Sprachbefehl des Benutzers gehört haben.
* Verstehen Sie, was der Benutzer sagt, indem Sie eine Diktat-Recognizer verwenden.
* Verwenden Sie eine Grammatikerkennung, um auf Befehlen zu lauschen, die auf einer SRGS-Datei oder einer Spracherkennungsgrammatikspezifikation basieren.

In diesem Kurs werden wir den Modell-Explorer erneut besuchen, den wir in [MR Input 210](holograms-210.md) und [MR Input 211 erstellt haben.](holograms-211.md)

>[!IMPORTANT]
>Die in die einzelnen Kapitel unten eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet. Während die Schritt-für-Schritt-Anweisungen genau und aktuell sind, werden möglicherweise Skripts und Visuals in den entsprechenden Videos angezeigt, die veraltet sind. Die Videos bleiben für die Nachwelt enthalten, und da die behandelten Konzepte weiterhin gelten.


## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR-Eingabe 212: Sprache</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Vorbereitung

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10 PC, der mit den richtigen [installierten Tools konfiguriert ist.](../../../develop/install-the-tools.md)
* Einige grundlegende C#-Programmierfähigkeiten.
* Sie sollten die [MR-Grundlagen 101 abgeschlossen haben.](../../../develop/unity/tutorials/holograms-101.md)
* Sie sollten MR [Input 210 abgeschlossen haben.](holograms-210.md)
* Sie sollten [MR-Eingabe 211 abgeschlossen haben.](holograms-211.md)
* Ein HoloLens, [das für die Entwicklung konfiguriert ist.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Projektdateien

* Laden Sie [die für](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) das Projekt erforderlichen Dateien herunter. Erfordert Unity 2017.2 oder höher.
* Archivieren Sie die Dateien auf Ihrem Desktop oder einem anderen leicht erreichbaren Speicherort.

>[!NOTE]
>Wenn Sie den Quellcode vor dem Herunterladen durchschauen möchten, ist er [auf GitHub.](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)

### <a name="errata-and-notes"></a>Errata und Hinweise

* "Enable Nur eigenen Code" muss in Visual Studiounter Tools->Options->Debugging deaktiviert (deaktiviert) werden, um Breakpoints im Code zu finden.

## <a name="unity-setup"></a>Unity-Setup

### <a name="instructions"></a>Anweisungen

1. Starten Sie Unity.
2. Wähle **Öffnen** aus.
3. Navigieren Sie zum **Ordner HolographicAcademy-Hologramme-212-Voice,** den Sie zuvor nicht archiviert haben.
4. Suchen Sie den Ordner **Modell-Explorer** / **starten, und wählen Sie diesen** aus.
5. Klicken Sie auf **die Schaltfläche Ordner** auswählen.
6. Erweitern Sie **Project** Bereich Den Ordner **Szenen.**
7. Doppelklicken Sie auf **ModelExplorer-Szene,** um sie in Unity zu laden.

### <a name="building"></a>Erstellen

1. Wählen Sie in Unity **Datei > Build Einstellungen.**
2. Wenn **Scenes/ModelExplorer** unter Scenes In Build (Szenen **im Build)** nicht aufgeführt ist, klicken Sie auf Add Open Scenes (Geöffnete Szenen **hinzufügen),** um die Szene hinzuzufügen.
3. Wenn Sie speziell für die Entwicklung HoloLens, legen Sie **Zielgerät** auf **HoloLens.** Andernfalls belasse es auf **Beliebiges Gerät.**
4. Stellen **Sie sicher,** dass build type (Buildtyp) auf **D3D** und **SDK** auf **Latest installed** (SDK 16299 oder neuer) festgelegt ist.
5. Klicken Sie auf **Erstellen**.
6. Erstellen Sie **einen neuen Ordner** mit dem Namen "App".
7. Klicken Sie mit nur einem Klick **auf den Ordner App.**
8. Klicken **Sie auf Ordner** auswählen, und Unity beginnt mit dem Erstellen des Projekts für Visual Studio.

Wenn Unity fertig ist, wird ein Datei-Explorer-Fenster angezeigt.

1. Öffnen Sie den **Ordner App.**
2. Öffnen Sie **modelExplorer Visual Studio Solution**.

Bei der Bereitstellung in HoloLens:

1. Ändern Sie das Ziel über Visual Studio symbolleiste von Debuggen in **Release** und von ARM in **x86.**
2. Klicken Sie auf den Dropdownpfeil neben der Schaltfläche Lokaler Computer, und wählen Sie **Remotecomputer aus.**
3. Geben **Sie ihre HoloLens-IP-Adresse ein,** und legen Sie den Authentifizierungsmodus auf **Universell (unverschlüsselte Protokoll) fest.** Klicken Sie auf **Auswählen**. Wenn Sie Die IP-Adresse Ihres Geräts nicht kennen, finden Sie weitere Informationen unter Einstellungen > Network & Internet > Advanced Options ( Erweiterte **Optionen).**
4. Klicken Sie in der oberen Menüleiste **auf Debuggen -> Ohne Debuggen** starten, oder drücken Sie **STRG+F5.** Wenn Dies die erste Bereitstellung auf Ihrem Gerät ist, müssen Sie es mit [einem Visual Studio.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)
5. Wenn die App bereitgestellt wurde, verknappen Sie **die Fitbox** mit einer **Auswahlgeste.**

Bei der Bereitstellung auf einem immersiven Headset:

1. Ändern Sie über die obere Symbolleiste in Visual Studio Ziel von Debuggen in **Release** und von ARM in **x64.**
2. Stellen Sie sicher, dass das Bereitstellungsziel auf Lokaler **Computer festgelegt ist.**
3. Klicken Sie in der oberen Menüleiste **auf Debuggen -> Ohne Debuggen** starten, oder drücken Sie **STRG+F5.**
4. Wenn die App bereitgestellt wurde, verdringen Sie **die Fitbox,** indem Sie den Trigger auf einen Motion-Controller ziehen.

>[!NOTE]
>Möglicherweise werden einige rote Fehler im Bereich Visual Studio Fehler angezeigt. Es ist sicher, sie zu ignorieren. Wechseln Sie zum Bereich Ausgabe, um den tatsächlichen Buildfortschritt zu sehen. Fehler im Ausgabebereich erfordern, dass Sie eine Korrektur ausführen (meistens werden sie durch einen Fehler in einem Skript verursacht).

## <a name="chapter-1---awareness"></a>Kapitel 1: Bewusstsein

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Ziele

* Lernen Sie **die Dos and Don'ts** des Sprachbefehlsentwurfs kennen.
* Verwenden **Sie KeywordRecognizer,** um Anvisierungs-basierte Sprachbefehle hinzuzufügen.
* Machen Sie Benutzer mithilfe von Cursorfeedback auf **Sprachbefehle aufmerksam.**

### <a name="voice-command-design"></a>Voice Command Design

In diesem Kapitel erfahren Sie mehr über das Entwerfen von Sprachbefehlen. Beim Erstellen von Sprachbefehlen:

#### <a name="do"></a>DO

* Erstellen Sie präzise Befehle. Sie möchten nicht *"Play the currently selected video"* verwenden, da dieser Befehl nicht präzise ist und vom Benutzer leicht vergessen werden würde. Verwenden Sie stattdessen *"Play Video",* da es präzise ist und über mehrere Silben verfügt.
* Verwenden Sie ein einfaches Vokabular. Versuchen Sie immer, allgemeine Wörter und Ausdrücke zu verwenden, die für den Benutzer leicht zu finden und zu merken sind. Wenn Ihre Anwendung beispielsweise ein Hinweisobjekt hätte, das angezeigt oder ausgeblendet werden konnte, würden Sie nicht den Befehl *"Show Placard"* verwenden, da "placard" ein selten verwendeter Begriff ist. Stattdessen würden Sie den Befehl *"Hinweis anzeigen"* verwenden, um den Hinweis in Ihrer Anwendung zu zeigen.
* Achten Sie auf Einheitlichkeit. Sprachbefehle sollten anwendungsübergreifend konsistent bleiben. Imagine, dass Ihre Anwendung zwei Szenen enthält und beide Szenen eine Schaltfläche zum Schließen der Anwendung enthalten. Wenn die erste Szene den Befehl *"Exit"* verwendet hat, um die Schaltfläche auszulösen, aber die zweite Szene den Befehl *"Close App"*(App schließen) verwendet hat, wird der Benutzer sehr verwirrend. Wenn dieselbe Funktionalität über mehrere Szenen hinweg beibehalten wird, sollte derselbe Sprachbefehl verwendet werden, um sie auszulösen.

#### <a name="dont"></a>Tue nicht

* Verwenden Sie einzelne sillierbare Befehle. Wenn Sie beispielsweise einen Sprachbefehl zum Wiederspielen eines Videos erstellen, sollten Sie die Verwendung des einfachen Befehls *"Play"* vermeiden, da es sich nur um ein einzelnes Silbenable handelt und vom System leicht übersehen werden kann. Verwenden Sie stattdessen *"Play Video",* da es präzise ist und über mehrere Silben verfügt.
* Verwenden Sie Systembefehle. Der *Befehl "Select"* ist vom System reserviert, um ein Tap-Ereignis für das aktuell fokussierte Objekt auszulösen. Verwenden Sie den Befehl *"Select"* nicht erneut in einem Schlüsselwort oder Ausdruck, da er möglicherweise nicht wie erwartet funktioniert. Wenn der Sprachbefehl zum Auswählen eines Würfels in Ihrer Anwendung beispielsweise *"Cube auswählen"* war, der Benutzer aber beim Äußerung des Befehls eine Kugel betrachtet hat, wird stattdessen die Kugel ausgewählt. Ebenso sind App-Leistenbefehle sprach aktiviert. Verwenden Sie in der CoreWindow-Ansicht nicht die folgenden Sprachbefehle:
    1. Zurück
    2. Bildlauftool
    3. Zoomtool
    4. Drag Tool
    5. Anpassen
    6. Entfernen
* Verwenden Sie ähnliche Sounds. Versuchen Sie, die Verwendung von Sprachbefehlen zu vermeiden, die sich wiederholen. Wenn Sie über eine Einkaufsanwendung verfügten, die *"Show Store"* und *"Show More"* als Sprachbefehle unterstützt, sollten Sie einen der Befehle deaktivieren, während der andere verwendet wurde. Sie können beispielsweise die Schaltfläche *"Show Store"* (Store anzeigen) verwenden, um den Store zu öffnen, und diesen Befehl dann deaktivieren, wenn der Speicher angezeigt wurde, sodass der Befehl *"Show More"* zum Durchsuchen verwendet werden kann.

### <a name="instructions"></a>Anweisungen

* Verwenden Sie im **Unity-Bereich Hierarchie** das Suchtool, um das Objekt **holoComm_screen_mesh** suchen.
* Doppelklicken Sie auf das **holoComm_screen_mesh,** um es in der **Szene zu sehen.** Dies ist die Uhr des Astronauten, die auf unsere Sprachbefehle reagiert.
* Suchen Sie **im Bereich** Inspector die Komponente Speech Input **Source (Script).**
* Erweitern Sie den **Abschnitt Schlüsselwörter,** um den unterstützten Sprachbefehl zu sehen: **Öffnen Communicator**.
* Klicken Sie rechts auf das Zahnrad, und wählen Sie **dann Skript bearbeiten aus.**
* Erkunden **Sie SpeechInputSource.cs,** um zu verstehen, wie **das KeywordRecognizer-Objekt** verwendet wird, um Sprachbefehle hinzuzufügen.

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

* Verwenden Sie in Unity **die Datei > Build Einstellungen,** um die Anwendung neu zu erstellen.
* Öffnen Sie den **Ordner App.**
* Öffnen Sie **modelExplorer Visual Studio Solution**.

(Wenn Sie dieses Projekt bereits in Visual Studio während der Einrichtung erstellt/bereitgestellt haben, können Sie diese Instanz von VS öffnen und auf "Alle erneut laden" klicken, wenn Sie dazu aufgefordert werden.)

* Klicken Visual Studio auf **Debuggen -> Ohne Debuggen** starten, oder drücken Sie **STRG+F5.**
* Nachdem die Anwendung in der Anwendung bereitgestellt HoloLens, schließen Sie das Anpassfeld mithilfe der Geste [zum Tippen in die](../../../design/gaze-and-commit.md#composite-gestures) Luft.
* Sehen Sie sich die Uhr des Astronauten an.
* Wenn die Uhr den Fokus besitzt, überprüfen Sie, ob sich der Cursor in ein Mikrofon ändert. Dadurch erhalten Sie Feedback dazu, dass die Anwendung auf Sprachbefehle lauss.
* Stellen Sie sicher, dass auf der Uhr eine QuickInfo angezeigt wird. Dadurch können Benutzer den Befehl *"Open Communicator" (Öffnen Communicator)* finden.
* Wenn Sie sich an der Uhr ansehen, sagen Sie *"Open Communicator",* um den Kommunikationsbereich zu öffnen.

## <a name="chapter-2---acknowledgement"></a>Kapitel 2: Bestätigung

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Ziele

* Zeichnen Sie eine Nachricht mithilfe der Mikrofoneingabe auf.
* Geben Sie dem Benutzer Feedback, dass die Anwendung auf seine Stimme lauss.

>[!NOTE]
>Die **Mikrofonfunktion** muss deklariert werden, damit eine App über das Mikrofon aufzeichnen kann. Dies erfolgt bereits in MR Input 212 für Sie, aber beachten Sie dies für Ihre eigenen Projekte.
>
>1. Navigieren Sie im Unity-Editor zu den Playereinstellungen, indem Sie zu "Bearbeiten > Project Einstellungen > Player" navigieren.
>2. Klicken Sie auf die Registerkarte "Universelle Windows Plattform".
>3. Überprüfen Sie im Abschnitt "Einstellungen > Funktionen" die **Funktion Mikrofon.**

### <a name="instructions"></a>Anweisungen

* Überprüfen Sie im **Unity-Bereich** Hierarchie, ob **holoComm_screen_mesh** Objekt ausgewählt ist.
* Suchen Sie **im Inspektorbereich** nach der **Komponente Astronaut Watch (Script).**
* Klicken Sie auf den kleinen, blauen Cube, der als Wert der **Prefab Communicator eigenschaft festgelegt** ist.
* Im **Project** sollte das **Communicator** jetzt den Fokus haben.
* Klicken Sie im **Communicator** auf das Communicator Pref **Project ab,** um dessen Komponenten im **Inspektor anzeigen zu können.**
* Sehen Sie sich die **Komponente Mikrofon-Manager (Skript)** an. Dadurch können wir die Stimme des Benutzers aufzeichnen.
* Beachten Sie, **dass Communicator-Objekt** über eine **Speech Input Handler (Script)-Komponente** für die Reaktion auf den Befehl **Nachricht senden** verfügt.
* Sehen Sie sich die **Communicator (Skript)-Komponente** an, und doppelklicken Sie auf das Skript, um es in der Visual Studio.

Communicator.cs ist für das Festlegen der richtigen Schaltflächenzustände auf dem Kommunikationsgerät verantwortlich. Dadurch können unsere Benutzer eine Nachricht aufzeichnen, wieder aufspielen und die Nachricht an den Astronauten senden. Außerdem wird eine animierte Wellenform gestartet und animiert, um dem Benutzer zu bestätigen, dass seine Stimme gehört wurde.

* Löschen **Communicator.cs** die folgenden Zeilen (81 und 82) aus der **Start-Methode.** Dadurch wird die Schaltfläche "Datensatz" auf der Kommunikation aktiviert.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

* Erstellen Visual Studio Anwendung neu, und stellen Sie sie auf dem Gerät zur Anwendung.
* Sehen Sie sich die Uhr des Astronauten an, und sagen Sie *"Open Communicator",* um die Kommunikation zu zeigen.
* Drücken  Sie die Aufzeichnungsschaltfläche (Mikrofon), um mit der Aufzeichnung einer Meldung für den Astronauten zu beginnen.
* Beginnen Sie mit dem Sprechen, und überprüfen Sie, ob die Wellenanimation auf der Kommunikation abspielt, die dem Benutzer Feedback gibt, dass seine Stimme gehört wird.
* Klicken Sie auf **die Schaltfläche** Beenden (linkes Quadrat), und vergewissern Sie sich, dass die Wellenanimation nicht mehr ausgeführt wird.
* Drücken Sie die **Wiedergabeschaltfläche** (rechtes Dreieck), um die aufgezeichnete Nachricht wiedergespielt und auf dem Gerät zu hören.
* Klicken Sie auf **die Schaltfläche** Beenden (rechtes Quadrat), um die Wiedergabe der aufgezeichneten Nachricht zu beenden.
* Sagen *Sie "Nachricht senden",* um die Kommunikation zu schließen und eine "Message Received"-Antwort vom Astronauten zu erhalten.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Kapitel 3: Grundlegendes zur Diktat-Erkennen

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Ziele

* Verwenden Sie die Diktaterkennung, um die Sprache des Benutzers in Text zu konvertieren.
* Zeigen Sie die hypothetischen und endgültigen Ergebnisse der Diktat erkennen in der Kommunikation an.

In diesem Kapitel verwenden wir die Diktat-Erkennen, um eine Nachricht für den Astronauten zu erstellen. Beachten Sie bei Verwendung der Diktat-Recognizer-Diktat-

* Sie müssen mit wlan verbunden sein, damit die Diktat-Erkennen funktioniert.
* Timeouts treten nach einem festgelegten Zeitraum auf. Es gibt zwei Timeouts, die Sie beachten sollten:
  * Wenn die Erkannten gestartet werden und in den ersten fünf Sekunden keine Audiodaten hören, kommt es zu einem Timeout.
  * Wenn die Erkennende ein Ergebnis gegeben hat, dann aber 20 Sekunden stille hören, wird ein Timeout entstehen.
* Es kann nur ein Typ der Erkannten (Schlüsselwort oder Diktat) gleichzeitig ausgeführt werden.

>[!NOTE]
>Die **Mikrofonfunktion** muss deklariert werden, damit eine App über das Mikrofon aufzeichnen kann. Dies erfolgt bereits in MR Input 212 für Sie, aber beachten Sie dies für Ihre eigenen Projekte.
>
>1. Navigieren Sie im Unity-Editor zu den Playereinstellungen, indem Sie zu "Bearbeiten > Project Einstellungen > Player" navigieren.
>2. Klicken Sie auf die Registerkarte "Universelle Windows Plattform".
>3. Überprüfen Sie im Abschnitt "Einstellungen > Funktionen" die **Funktion Mikrofon.**

### <a name="instructions"></a>Anweisungen

Wir werden **microphoneManager.cs** bearbeiten, um die Diktaterkennung zu verwenden. Dies fügen wir hinzu:

1. Wenn die **Schaltfläche Datensatz** gedrückt wird, **wird DictationRecognizer gestartet.**
2. Zeigen Sie die **Hypothese,** was DictationRecognizer verstanden hat.
3. Sperren Sie die **Ergebnisse** der DictationRecognizer-Werte.
4. Überprüfen Sie im DictationRecognizer auf Timeouts.
5. Wenn die **Schaltfläche Beenden** gedrückt wird oder die Mikrofonsitzung zu einem Zeitpunkt führt, beenden **Sie DictationRecognizer.**
6. Starten Sie **das SchlüsselwortRecognizer** neu, das auf den Befehl **Nachricht senden** lauscht.

Fangen wir also an. Führen Sie alle Codierungsübungen für 3.a in **MicrophoneManager.cs** aus, oder kopieren Sie den fertig gestellten Code, den Sie unten finden:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

* Erstellen Sie in Visual Studio neu, und stellen Sie sie auf Ihrem Gerät bereit.
* Schließen Sie das Anpassfeld mit einer Tippbewegung in die Luft.
* Sehen Sie sich die Uhr des Astronauten an, und sagen Sie *"Open Communicator".*
* Wählen Sie die Schaltfläche **Aufzeichnen** (Mikrofon) aus, um Ihre Nachricht aufzuzeichnen.
* Beginnen Sie mit dem Sprechen. Die **Diktaterkennung** interpretiert Ihre Sprache und zeigt den hypothesierten Text im Communicator an.
* Versuchen Sie, *"Nachricht senden"* zu sagen, während Sie eine Nachricht aufzeichnen. Beachten Sie, dass die **Schlüsselworterkennung** nicht reagiert, da die **Diktaterkennung** noch aktiv ist.
* Sprechen Sie einige Sekunden lang nicht mehr. Beobachten Sie, wie die Diktaterkennung ihre Hypothese abschließt und das Endergebnis anzeigt.
* Beginnen Sie mit dem Sprechen, und halten Sie dann 20 Sekunden an. Dadurch tritt bei der **Diktaterkennung** ein Timeout auf.
* Beachten Sie, dass die **Schlüsselworterkennung** nach dem obigen Timeout erneut aktiviert wird. Der Kommunikationsor antwortet nun auf Sprachbefehle.
* Sagen *Sie "Nachricht senden",* um die Nachricht an den Astronauten zu senden.

## <a name="chapter-4---grammar-recognizer"></a>Kapitel 4: Grammatikerkennung

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Ziele

* Verwenden Sie die Grammatikerkennung, um die Sprache des Benutzers gemäß einer SRGS- oder Speech Recognition Grammar Specification-Datei zu erkennen.

>[!NOTE]
>Die **Mikrofonfunktion** muss deklariert werden, damit eine App über das Mikrofon aufzeichnen kann. Dies geschieht für Sie bereits in MR Input 212, aber bedenken Sie dies für Ihre eigenen Projekte.
>
>1. Navigieren Sie im Unity-Editor zu den Playereinstellungen, indem Sie zu "> Project Einstellungen > Player bearbeiten" navigieren.
>2. Klicken Sie auf die Registerkarte "Universelle Windows Plattform".
>3. Überprüfen Sie im Abschnitt "Veröffentlichung Einstellungen > Funktionen" die **Funktion Mikrofon.**

### <a name="instructions"></a>Anweisungen

1. Suchen Sie im **Hierarchiebereich** **nach Jetpack_Center,** und wählen Sie sie aus.
2. Suchen Sie im Bereich **Inspector** nach dem **Tagalong** Action-Skript.
3. Klicken Sie rechts neben dem Feld **Object To Tag Along** auf den kleinen Kreis.
4. Suchen Sie im daraufhin angezeigten Fenster nach **SRGSToolbox,** und wählen Sie es aus der Liste aus.
5. Sehen Sie sich die **dateiSRGSColor.xml** im Ordner **StreamingAssets** an.
    1. Die SRGS-Entwurfsspezifikation finden Sie auf der [W3C-Website hier.](https://www.w3.org/TR/speech-grammar/)

In unserer SRGS-Datei gibt es drei Arten von Regeln:

* Eine Regel, mit der Sie eine Farbe aus einer Liste von zwölf Farben sagen können.
* Drei Regeln, die auf eine Kombination der Farbregel und einer der drei Formen lauschen.
* Die Stammregel colorChooser, die auf eine beliebige Kombination der drei Regeln "Farbe und Form" lauscht. Die Formen können in beliebiger Reihenfolge und in beliebiger Menge von nur einem bis zu allen drei Formen gesagt werden. Dies ist die einzige Regel, die überwacht wird, da sie als Stammregel am Anfang der Datei im anfänglichen Grammatiktag angegeben &lt; &gt; wird.

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

* Erstellen Sie die Anwendung in Unity neu, und erstellen Sie sie dann aus Visual Studio, und stellen Sie sie bereit, um die App auf HoloLens zu erleben.
* Schließen Sie das Anpassfeld mit einer Tippbewegung in die Luft.
* Sehen Sie sich das Jetpack des Astronauten an, und führen Sie eine Geste zum Tippen in die Luft aus.
* Beginnen Sie mit dem Sprechen. Die **Grammatikerkennung** interpretiert Ihre Sprache und ändert die Farben der Formen basierend auf der Erkennung. Ein Beispielbefehl ist "blauer Kreis, gelbes Quadrat".
* Führen Sie eine weitere Tippbewegung aus, um die Toolbox zu schließen.

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben nun **MR Input 212: Voice** abgeschlossen.

* Sie kennen die Dos- und Don'ts-Befehle von Sprachbefehlen.
* Sie haben gesehen, wie QuickInfos verwendet wurden, um Benutzer auf Sprachbefehle aufmerksam zu machen.
* Sie haben verschiedene Arten von Feedback gesehen, um zu bestätigen, dass die Stimme des Benutzers gehört wurde.
* Sie wissen, wie Sie zwischen der Schlüsselworterkennung und der Diktaterkennung wechseln und wie diese beiden Features Ihre Stimme verstehen und interpretieren.
* Sie haben gelernt, wie Sie eine SRGS-Datei und die Grammatikerkennung für die Spracherkennung in Ihrer Anwendung verwenden.