---
title: 'HoloLens (1. Generation) Eingabe 211: Geste'
description: Befolgen Sie diese exemplarische Vorgehensweise zum Programmieren mit Unity, Visual Studio und HoloLens, um die Details der Gestenkonzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gesture, HoloLens, Mixed Reality Academy, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Windows 10
ms.openlocfilehash: 75cfb836e5a9702c1d949ed57450984081db0c5d6ec14c76cae5148edf637e7e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206424"
---
# <a name="hololens-1st-gen-input-211-gesture"></a>HoloLens (1. Generation) Eingabe 211: Geste

>[!IMPORTANT]
>Die Mixed Reality Academy-Tutorials wurden mit HoloLens (1. Generation), Unity 2017 und Mixed Reality immersive Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen. Diese Tutorials werden **_nicht mit_** den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden, und sind möglicherweise nicht mit neueren Versionen von Unity kompatibel.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](mrlearning-base.md) für HoloLens 2 veröffentlicht.

[Gesten machen](../../../design/gaze-and-commit.md#composite-gestures) die Benutzerabsicht in Aktion. Mithilfe von Gesten können Benutzer mit Hologrammen interagieren. In diesem Kurs erfahren Sie, wie Sie die Hände des Benutzers nachverfolgen, auf Benutzereingaben reagieren und dem Benutzer basierend auf dem Zustand und standort der Hand Feedback geben.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md)haben wir eine einfache Geste zum Tippen in die Luft verwendet, um mit unseren Hologrammen zu interagieren. Nun gehen wir über die Geste zum Tippen in die Luft hinaus und untersuchen neue Konzepte für:

* Erkennen Sie, wann die Hand des Benutzers nachverfolgt wird, und geben Sie dem Benutzer Feedback.
* Verwenden Sie eine Navigationsgeste, um unsere Hologramme zu drehen.
* Geben Sie Feedback, wenn die Hand des Benutzers nicht mehr angezeigt wird.
* Verwenden Sie Manipulationsereignisse, damit Benutzer Hologramme mit ihren Händen bewegen können.

In diesem Kurs werden wir das Unity-Projekt **Modell-Explorer** erneut besuchen, das wir in [MR Input 210 erstellt haben.](holograms-210.md) Unser Astronautenfreund ist wieder dabei, uns bei der Untersuchung dieser neuen Gestenkonzepte zu unterstützen.

>[!IMPORTANT]
>Die in die einzelnen Kapitel unten eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet. Während die Schritt-für-Schritt-Anweisungen genau und aktuell sind, werden möglicherweise Skripts und Visuals in den entsprechenden Videos angezeigt, die veraltet sind. Die Videos bleiben für die Nachwelt enthalten, und da die behandelten Konzepte weiterhin gelten.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR-Eingabe 211: Geste</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Vorbereitung

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10 PC, der mit den richtigen [installierten Tools konfiguriert ist.](../../../develop/install-the-tools.md)
* Einige grundlegende C#-Programmierfähigkeiten.
* Sie sollten die [MR-Grundlagen 101 abgeschlossen haben.](../../../develop/unity/tutorials/holograms-101.md)
* Sie sollten MR [Input 210 abgeschlossen haben.](holograms-210.md)
* Ein HoloLens, [das für die Entwicklung konfiguriert ist.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Projektdateien

* Laden Sie [die für](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) das Projekt erforderlichen Dateien herunter. Erfordert Unity 2017.2 oder höher.
* Archivieren Sie die Dateien auf Ihrem Desktop oder einem anderen leicht erreichbaren Speicherort.

>[!NOTE]
>Wenn Sie den Quellcode vor dem Herunterladen durchschauen möchten, ist er [auf GitHub.](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)

### <a name="errata-and-notes"></a>Errata und Hinweise

* "Enable Nur eigenen Code" muss in Visual Studiounter Tools->Options->Debugging deaktiviert (deaktiviert) werden, um Breakpoints im Code zu finden.

## <a name="chapter-0---unity-setup"></a>Kapitel 0 : Unity-Setup

### <a name="instructions"></a>Anweisungen

1. Starten Sie Unity.
2. Wähle **Öffnen** aus.
3. Navigieren Sie zum **Ordner Gesten,** den Sie zuvor nicht archiviert haben.
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

## <a name="chapter-1---hand-detected-feedback"></a>Kapitel 1: Hand detected feedback (Hand erkanntes Feedback)

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Ziele

* Abonnieren Sie Handtrackingereignisse.
* Verwenden Sie Cursorfeedback, um Benutzern zu zeigen, wann eine Hand nachverfolgt wird.

>[!NOTE]
>Auf HoloLens 2 wird die Hand immer dann gezippt, wenn die Hände sichtbar sind (nicht nur, wenn ein Finger nach oben zeigen).

### <a name="instructions"></a>Anweisungen

* Erweitern Sie **im Bereich** Hierarchie das **InputManager-Objekt.**
* Suchen Sie nach dem **GesturesInput-Objekt, und wählen Sie** es aus.

Das **Skript InteractionInputSource.cs** führt die folgenden Schritte aus:

1. Abonniert die Ereignisse InteractionSourceDetected und InteractionSourceLost.
2. Legt den Zustand HandDetected fest.
3. Kündigen der Ereignisse InteractionSourceDetected und InteractionSourceLost.

Als Nächstes aktualisieren wir den Cursor von [MR Input 210](holograms-210.md) in einen Cursor, der Feedback abhängig von den Aktionen des Benutzers zeigt.

1. Wählen Sie **im Bereich** Hierarchie das **Cursorobjekt aus,** und löschen Sie es.
2. Suchen Sie **im Project** nach **CursorWithFeedback,** und ziehen Sie es in den **Bereich Hierarchie.**
3. Klicken Sie im  Hierarchiebereich auf **InputManager,** und ziehen  Sie dann das **CursorWithFeedback-Objekt** aus der Hierarchie  in das Cursorfeld des InputManager-Objekts **SimpleSinglePointerSelector** am unteren Rand des **Inspectors.**
4. Klicken Sie in der Hierarchie auf **CursorWithFeedback.**
5. Erweitern Sie **im Bereich Inspector** den Bereich Cursor State Data **(Cursorzustandsdaten)** **im Objektcursorskript.**

Die **Cursorzustandsdaten** funktionieren wie die folgenden:

* Jeder **Beobachten-Zustand** bedeutet, dass keine Hand erkannt wird und der Benutzer sich einfach ums sucht.
* Jeder **Interaktionszustand** bedeutet, dass eine Hand oder ein Controller erkannt wird.
* Jeder **Hoverzustand** bedeutet, dass der Benutzer ein Hologramm betrachtet.

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

* Verwenden Sie in Unity **die Datei > Build Einstellungen,** um die Anwendung neu zu erstellen.
* Öffnen Sie den **Ordner App.**
* Wenn es noch nicht geöffnet ist, öffnen Sie die **ModelExplorer-Visual Studio Projektmappe.**
  * (Wenn Sie dieses Projekt bereits während der Visual Studio in Visual Studio erstellt/bereitgestellt haben, können Sie diese Instanz von VS öffnen und auf "Alle neu laden" klicken, wenn Sie dazu aufgefordert werden.)
* Klicken Visual Studio auf **Debuggen -> Ohne Debuggen** starten, oder drücken Sie **STRG+F5.**
* Nachdem die Anwendung in der Anwendung bereitgestellt HoloLens, verdringen Sie die Fitbox mithilfe der Geste zum Tippen in die Luft.
* Bewegen Sie Ihre Hand in die Ansicht, und zeigen Sie den Zeigefinger auf den Himmel, um die Handverfolgung zu starten.
* Bewegen Sie Ihre Hand nach links, rechts, nach oben und unten.
* Beobachten Sie, wie sich der Cursor ändert, wenn Ihre Hand erkannt wird und dann aus der Ansicht verloren geht.
* Wenn Sie ein immersives Headset verwenden, müssen Sie ihren Controller verbinden und trennen. Dieses Feedback wird auf einem immersiven Gerät weniger interessant, da ein verbundener Controller immer "verfügbar" ist.

## <a name="chapter-2---navigation"></a>Kapitel 2: Navigation

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Ziele

* Verwenden Sie Navigationsgestenereignisse, um den Astronauten zu drehen.

### <a name="instructions"></a>Anweisungen

Um Navigationsgesten in unserer App zu verwenden, bearbeiten wir **GestureAction.cs,** um Objekte zu drehen, wenn die Navigationsgeste auftritt. Darüber hinaus fügen wir dem Cursor Feedback hinzu, um anzuzeigen, wenn Navigation verfügbar ist.

1. Erweitern Sie **im Bereich** Hierarchie den Bereich **CursorWithFeedback**.
2. Suchen Sie **Hologramme** ordner nach dem **Objekt ScrollFeedback.**
3. Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.
4. Klicken Sie auf **CursorWithFeedback**.
5. Klicken Sie **im Inspektorbereich** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
6. Geben Sie im Menü in das Suchfeld **CursorFeedback ein.** Wählen Sie das Suchergebnis aus.
7. Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.
8. Wählen Sie **im Bereich** Hierarchie das **Objekt "Steuerungsman"** aus.
9. Klicken Sie **im Inspektorbereich** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
10. Geben Sie im Menü in das Suchfeld **Gestenaktion ein.** Wählen Sie das Suchergebnis aus.

Öffnen Sie als Nächstes **die Datei GestureAction.cs** in Visual Studio. Bearbeiten Sie in der Codierungsübung 2.c das Skript, um Folgendes zu tun:

1. **Drehen Sie das Objekt "Sollman",** wenn eine Navigationsgeste ausgeführt wird.
2. Berechnen Sie den **rotationFactor,** um die Drehungsmenge zu steuern, die auf das Objekt angewendet wird.
3. **Drehen Sie das Objekt um** die y-Achse, wenn der Benutzer seine Hand nach links oder rechts bewegt.

Führen Sie die Codierungsübungen 2.c im Skript durch, oder ersetzen Sie den Code durch die fertige Lösung unten:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

Sie werden feststellen, dass die anderen Navigationsereignisse bereits mit einigen Informationen ausgefüllt sind. Wir pushen das GameObject auf den modalen Stapel InputSystem des Toolkits, damit der Benutzer den Fokus nicht mehr auf den Astronauten behalten muss, sobald die Drehung begonnen hat. Entsprechend wird das GameObject aus dem Stapel geschaltet, sobald die Geste abgeschlossen ist.

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

1. Erstellen Sie die Anwendung in Unity neu, und erstellen Sie sie dann aus Visual Studio, um sie im HoloLens.
2. Anvspricht den Astronauten. Auf beiden Seiten des Cursors sollten zwei Pfeile angezeigt werden. Dieses neue Visual gibt an, dass der Astronaut gedreht werden kann.
3. Platzieren Sie Ihre Hand an der bereiten Position (Zeigefinger zeigt auf den Himmel), damit der HoloLens beginnt, Ihre Hand zu verfolgen.
4. Um den Astronauten zu drehen, senken Sie den Zeigefinger auf eine Heftposition, und bewegen Sie die Hand dann nach links oder rechts, um die NavigationX-Geste auszulösen.

## <a name="chapter-3---hand-guidance"></a>Kapitel 3: Handleitfäden

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Ziele

* Verwenden **Sie eine Handleitfäden-Bewertung,** um vorherzusagen, wann die Handverfolgung verloren geht.
* Geben **Sie Feedback an den Cursor,** um zu zeigen, wann sich die Hand des Benutzers dem Kamerarand nähert.

### <a name="instructions"></a>Anweisungen

1. Wählen Sie **im Bereich** Hierarchie das **Objekt CursorWithFeedback** aus.
2. Klicken Sie **im Inspektorbereich** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
3. Geben Sie im Menü hand guidance in das **Suchfeld Hand Guidance ein.** Wählen Sie das Suchergebnis aus.
4. Suchen Sie **Project** **Im** Hologramme Ordner nach dem **Objekt HandGuidanceFeedback.**
5. Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

* Erstellen Sie die Anwendung in Unity neu, und erstellen Sie sie dann aus Visual Studio, um die App auf dem HoloLens.
* Zeigen Sie Ihre Hand, und heben Sie den Zeigefinger, um nachverfolgt zu werden.
* Beginnen Sie mit dem Drehen des Astronauten mit der Navigationsgeste (heften Sie den Zeigefinger und den Daumen zusammen).
* Bewegen Sie Ihre Hand ganz links, rechts, nach oben und unten.
* Wenn sich Ihre Hand dem Rand des Gestenrahmens nähert, sollte neben dem Cursor ein Pfeil angezeigt werden, um Sie zu warnen, dass die Handverfolgung verloren geht. Der Pfeil gibt an, in welche Richtung die Hand bewegt werden soll, um zu verhindern, dass die Nachverfolgung verloren geht.

## <a name="chapter-4---manipulation"></a>Kapitel 4– Manipulation

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Ziele

* Verwenden Sie Manipulationsereignisse, um den Astronauten mit den Händen zu bewegen.
* Geben Sie Feedback zum Cursor ein, um den Benutzer darüber zu informieren, wann Manipulation verwendet werden kann.

### <a name="instructions"></a>Anweisungen

GestureManager.cs und AstronautManager.cs ermöglichen Folgendes:

1. Verwenden Sie das Sprachschlüsselwort "**Move Astronaut**", um **Manipulationsgesten** zu aktivieren, und "**Rotate Astronaut**", um sie zu deaktivieren.
2. Wechseln Sie zu , um auf die **Manipulationsgestenerkennung zu reagieren.**

Fangen wir also an.

1. Erstellen Sie **im Hierarchiebereich** ein neues leeres GameObject. Nennen Sie es **"AstronautManager".**
2. Klicken Sie **im Inspektorbereich** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
3. Geben Sie im Menü in das Suchfeld **Astronaut Manager ein.** Wählen Sie das Suchergebnis aus.
4. Klicken Sie **im Inspektorbereich** auf **die Schaltfläche Add Component (Komponente** hinzufügen).
5. Geben Sie im Menü in das Suchfeld **Speech Input Source ein.** Wählen Sie das Suchergebnis aus.

Wir fügen nun die Sprachbefehle hinzu, die zum Steuern des Interaktionszustands des Astronauten erforderlich sind.

1. Erweitern Sie **den Abschnitt Schlüsselwörter** im **Inspektor**.
2. Klicken Sie **+** auf der rechten Seite auf , um ein neues Schlüsselwort hinzuzufügen.
3. Geben Sie das Schlüsselwort als **Move Astronaut ein.** Sie können bei Wunsch auch eine Tastenkombination hinzufügen.
4. Klicken Sie **+** auf der rechten Seite auf , um ein neues Schlüsselwort hinzuzufügen.
5. Geben Sie das Schlüsselwort als **Rotate Astronaut ein.** Sie können bei Wunsch auch eine Tastenkombination hinzufügen.
6. Den entsprechenden Handlercode finden Sie in **GestureAction.cs** im **ISpeechHandler.OnSpeechKeywordRecognized-Handler.**

![Einrichten der Spracheingabequelle für Kapitel 4](images/holograms211-speech.png)

Als Nächstes richten wir das Bearbeitungsfeedback für den Cursor ein.

1. Suchen Sie **Project** Im **Hologramme** Ordner nach dem **PathingFeedback-Objekt.**
2. Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.
3. Klicken Sie **im Bereich** Hierarchie auf **CursorWithFeedback**.
4. Ziehen Sie das **PathingFeedback-Objekt** aus der **Hierarchie** auf die Eigenschaft **Pathing Detected Game Object** in der **Cursor Feedback-Komponente** im **Inspector**.

Nun müssen wir **GestureAction.cs** Code hinzufügen, um Folgendes zu aktivieren:

1. Fügen Sie der **IManipulationHandler.OnManipulationUpdated-Funktion** Code hinzu, der den Astronauten bewegt, wenn eine **Manipulationsgeste** erkannt wird.
2. Berechnen Sie den **Bewegungsvektor,** um basierend auf der Handposition zu bestimmen, wohin der Astronaut verschoben werden soll.
3. **Verschieben Sie** den Astronauten an die neue Position.

Schließen Sie die Codierungsübung 4.a in **GestureAction.cs** ab, oder verwenden Sie unsere vollständige Lösung unten:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

* Erstellen Sie in Unity neu, und erstellen Und stellen Sie dann aus Visual Studio bereit, um die App in HoloLens auszuführen.
* Bewegen Sie ihre Hand vor den HoloLens, und heben Sie den Zeigefinger, damit er nachverfolgt werden kann.
* Konzentrieren Sie den Cursor auf den Astronauten.
* Sagen Sie "Move Astronaut", um den Astronauten mit einer Manipulationsgeste zu bewegen.
* Um den Cursor sollten vier Pfeile angezeigt werden, um anzugeben, dass das Programm jetzt auf Manipulationsereignisse reagiert.
* Zeigen Sie mit dem Zeigefinger auf Ihren Daumen, und halten Sie sie zusammen.
* Wenn Sie Ihre Hand bewegen, bewegt sich auch der Astronaut (dies ist Manipulation).
* Heben Sie den Zeigefinger auf, um die Bearbeitung des Astronauten zu beenden.
* Hinweis: Wenn Sie vor dem Bewegen der Hand nicht "Move Astronaut" sagen, wird stattdessen die Navigationsgeste verwendet.
* Sagen Sie "Rotate Astronaut", um in den rotierbaren Zustand zurückzukehren.

## <a name="chapter-5---model-expansion"></a>Kapitel 5: Modellerweiterung

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Ziele

* Erweitern Sie das Astronaut-Modell in mehrere kleinere Teile, mit denen der Benutzer interagieren kann.
* Verschieben Sie jedes Element einzeln mithilfe von Navigations- und Bearbeitungsgesten.

### <a name="instructions"></a>Anweisungen

In diesem Abschnitt werden die folgenden Aufgaben ausgeführt:

1. Fügen Sie das neue Schlüsselwort **"Expand Model" (Modell erweitern)** hinzu, um das Astronautenmodell zu erweitern.
2. Fügen Sie das neue Schlüsselwort **"Reset Model" (Modell zurücksetzen)** hinzu, um das Modell in seine ursprüngliche Form zurückzugeben.

Dazu fügen wir der Spracheingabequelle aus dem vorherigen Kapitel zwei weitere Schlüsselwörter hinzu. Wir zeigen auch eine weitere Möglichkeit zum Behandeln von Erkennungsereignissen.

1. Klicken Sie im **Inspector** zurück auf **AstronautManager,** und erweitern Sie den Abschnitt **Schlüsselwörter** im **Inspector**.
2. Klicken Sie **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.
3. Geben Sie das Schlüsselwort als **Modell erweitern ein.** Sie können bei Bedarf eine Tastenkombination hinzufügen.
4. Klicken Sie **+** auf der rechten Seite, um ein neues Schlüsselwort hinzuzufügen.
5. Geben Sie das Schlüsselwort als **Reset Model (Modell zurücksetzen) ein.** Sie können bei Bedarf eine Tastenkombination hinzufügen.
6. Klicken Sie im Bereich **Inspector (Inspektor)** auf die Schaltfläche **Add Component (Komponente hinzufügen).**
7. Geben Sie im Menü in das Suchfeld **Spracheingabehandler** ein. Wählen Sie das Suchergebnis aus.
8. Aktivieren Sie **Ist globaler Listener,** da diese Befehle unabhängig von dem GameObject funktionieren sollen, auf das wir uns konzentrieren.
9. Klicken Sie auf die **+** Schaltfläche, und wählen Sie in der Dropdownliste Schlüsselwort die Option **Modell erweitern** aus.
10. Klicken Sie unter Antwort auf **+** , und ziehen Sie den **AstronautManager** aus der **Hierarchie** in das Feld **None (Object) (Keine (Objekt)).**
11. Klicken Sie nun auf die Dropdownliste **No Function (Keine Funktion),** wählen Sie **AstronautManager** und dann **ExpandModelCommand aus.**
12. Klicken Sie auf die Schaltfläche des Spracheingabehandlers, **+** und wählen Sie in der Dropdownliste Schlüsselwort die Option Modell **zurücksetzen** aus.
13. Klicken Sie unter Antwort auf **+** , und ziehen Sie den **AstronautManager** aus der **Hierarchie** in das Feld **None (Object) (Keine (Objekt)).**
14. Klicken Sie nun auf die Dropdownliste **No Function (Keine Funktion),** wählen Sie **AstronautManager** und dann **ResetModelCommand aus.**

![Einrichten der Quelle und des Handlers für die Spracheingabe für Kapitel 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Erstellen und Bereitstellen

* Testen Erstellen Sie die App, und stellen Sie sie auf dem HoloLens bereit.
* Sagen **Sie Modell erweitern,** um das erweiterte Astronautenmodell anzuzeigen.
* Verwenden Sie **Navigation,** um einzelne Teile des Astronautenanzugs zu drehen.
* Sagen **Sie Move Astronaut,** und verwenden Sie dann **Manipulation,** um einzelne Teile des Astronautenanzugs zu verschieben.
* Sagen **Sie "Astronaut drehen",** um die Teile erneut zu drehen.
* Sagen Sie **Reset Model (Modell zurücksetzen),** um den Astronauten in seine ursprüngliche Form zurückzusetzen.

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben nun **MR-Eingabe 211: Geste** abgeschlossen.

* Sie wissen, wie Sie Nachverfolgungs-, Navigations- und Bearbeitungsereignisse erkennen und darauf reagieren können.
* Sie kennen den Unterschied zwischen Navigations- und Bearbeitungsgesten.
* Sie wissen, wie Sie den Cursor ändern, um visuelles Feedback zu geben, wann eine Hand erkannt wird, wann eine Hand verloren geht und wann ein Objekt verschiedene Interaktionen unterstützt (Navigation im Vergleich zu Manipulation).