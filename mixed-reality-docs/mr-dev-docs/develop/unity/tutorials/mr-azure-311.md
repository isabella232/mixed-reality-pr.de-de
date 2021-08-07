---
title: 'HoloLens (1. Generation) und Azure 311: Microsoft Graph'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Microsoft Graph nutzen und eine Verbindung mit den Daten herstellen, die die Produktivität innerhalb einer Mixed Reality-Anwendung steigern.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Microsoft Graph, HoloLens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 16fb7853d202c39399b48595a17e7e9b2edf224f18d5e315c5ddcf4a0054d8f7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215262"
---
# <a name="hololens-1st-gen-and-azure-311---microsoft-graph"></a>HoloLens (1. Generation) und Azure 311: Microsoft Graph

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. Es wird eine neue Reihe von Tutorials geben, die in Zukunft veröffentlicht werden, die veranschaulichen, wie sie für HoloLens 2 entwickelt werden.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn sie veröffentlicht werden.

In diesem Kurs erfahren Sie, wie Sie *microsoft Graph* verwenden, um sich mithilfe der sicheren Authentifizierung in einer Mixed Reality-Anwendung bei Ihrem Microsoft-Konto anzumelden. Anschließend rufen Sie Ihre geplanten Besprechungen ab und zeigen sie auf der Anwendungsschnittstelle an.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* ist eine Reihe von APIs, die den Zugriff auf viele Dienste von Microsoft ermöglichen. Microsoft beschreibt Microsoft Graph als Eine Matrix von Ressourcen, die durch Beziehungen verbunden sind, was bedeutet, dass eine Anwendung auf alle Arten von verbundenen Benutzerdaten zugreifen kann. Weitere Informationen finden Sie auf der [Microsoft Graph-Seite](https://developer.microsoft.com/graph).

Die Entwicklung umfasst die Erstellung einer App, bei der der Benutzer angewiesen wird, eine Kugel anzuverweisen und dann zu tippen. Dadurch wird der Benutzer aufgefordert, sich sicher bei einem Microsoft-Konto anzumelden. Nach der Anmeldung bei ihrem Konto kann der Benutzer eine Liste der Besprechungen anzeigen, die für diesen Tag geplant sind.

Nach Abschluss dieses Kurses verfügen Sie über eine Mixed Reality HoloLens Anwendung, die folgende Schritte ausführen kann:

1.  Tippen Sie mithilfe der Geste Tippen auf ein Objekt, das den Benutzer auffordert, sich bei einem Microsoft-Konto anzumelden (um die App zu entfernen, um sich anzumelden, und dann wieder zurück in die App).
2.  Zeigen Sie eine Liste der Besprechungen an, die für den Tag geplant sind. 

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das Wissen, das Sie aus diesem Kurs gewinnen, zu nutzen, um Ihre Mixed Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure 311: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die grundlegende Erfahrung mit Unity und C# haben. Beachten Sie auch, dass die Voraussetzungen und die geschriebenen Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt der Erstellung (Juli 2018) getestet und überprüft wurde. Sie können die neueste Software verwenden, wie im Artikel [installieren der Tools](../../install-the-tools.md) aufgeführt. Es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs perfekt mit dem übereinstimmen, was Sie in neuerer Software finden, als unten aufgeführt.

Für diesen Kurs wird die folgende Hardware und Software empfohlen:

- Ein Entwicklungs-PC
- [Windows 10 Fall Creators Update (oder höher) mit aktivierter Option "Entwicklermodus"](../../install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Ein [Microsoft HoloLens](/hololens/hololens1-hardware) mit aktivierter Option "Entwicklermodus"
- Internetzugriff für Azure-Setup und Microsoft Graph Datenabruf
- Ein gültiges **Microsoft-Konto** (entweder privat oder Arbeits-/Schulkonto)
- Einige Besprechungen, die für den aktuellen Tag geplant sind und das gleiche Microsoft-Konto verwenden

### <a name="before-you-start"></a>Vorbereitung

1.  Um Probleme bei der Erstellung dieses Projekts zu vermeiden, wird dringend empfohlen, das in diesem Tutorial erwähnte Projekt in einem Stammordner oder in einem Ordner in der Nähe des Stammordners zu erstellen (lange Ordnerpfade können zur Buildzeit Probleme verursachen).
2.  Richten Sie Ihre HoloLens ein, und testen Sie sie. Wenn Sie Unterstützung beim Einrichten Ihrer HoloLens benötigen, [besuchen Sie unbedingt den Artikel HoloLens Setup.](/hololens/hololens-setup) 
3.  Es ist eine gute Idee, Kalibrierung und Sensoroptimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen HoloLens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum HoloLens Kalibrierungsartikel](/hololens/hololens-calibration#hololens-2).

Hilfe zur Sensoroptimierung finden Sie unter diesem [Link zum artikel HoloLens Sensoroptimierung.](/hololens/hololens-updates)

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Kapitel 1: Erstellen Ihrer App im Anwendungsregistrierungsportal

Zunächst müssen Sie Ihre Anwendung im **Anwendungsregistrierungsportal** erstellen und registrieren.

In diesem Kapitel finden Sie auch den Dienstschlüssel, mit dem Sie *Microsoft-Graph* aufrufen können, um auf Ihre Kontoinhalte zuzugreifen.

1.  Navigieren Sie zum [Microsoft-Anwendungsregistrierungsportal,](https://apps.dev.microsoft.com) und melden Sie sich mit Ihrem Microsoft-Konto an. Nachdem Sie sich angemeldet haben, werden Sie zum **Anwendungsregistrierungsportal** umgeleitet.

2.  Klicken Sie im Abschnitt **Meine Anwendungen** auf die Schaltfläche **App hinzufügen.**

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > Das **Anwendungsregistrierungsportal** kann unterschiedlich aussehen, je nachdem, ob Sie zuvor mit *Microsoft Graph* gearbeitet haben. Die folgenden Screenshots zeigen diese verschiedenen Versionen.

3.  Fügen Sie einen Namen für Ihre Anwendung hinzu, und klicken Sie auf **Erstellen.**

    ![](images/AzureLabs-Lab311-03.png)

4.  Nachdem die Anwendung erstellt wurde, werden Sie zur Hauptseite der Anwendung umgeleitet. Kopieren Sie die **Anwendungs-ID,** und notieren Sie sich diesen Wert an einem sicheren Ort. Sie werden ihn in Kürze in Ihrem Code verwenden.

    ![](images/AzureLabs-Lab311-04.png)

5.  Stellen Sie im Abschnitt **Plattformen** sicher, dass **native Anwendung** angezeigt wird. Klicken Sie *andernfalls* auf **Plattform hinzufügen,** und wählen Sie **Native Anwendung** aus.

    ![](images/AzureLabs-Lab311-05.png)

6.  Scrollen Sie auf der gleichen Seite nach unten, und fügen Sie im Abschnitt **Microsoft Graph Permissions (Berechtigungen)** zusätzliche Berechtigungen für die Anwendung hinzu. Klicken Sie neben **Delegierte Berechtigungen** auf **Hinzufügen.**

    ![](images/AzureLabs-Lab311-06.png)

7.  Da Ihre Anwendung auf den Kalender des Benutzers zugreifen soll, aktivieren Sie das Kontrollkästchen **Calendars.Read,** und klicken Sie auf **OK.**

    ![](images/AzureLabs-Lab311-07.png)

8.  Scrollen Sie nach unten, und klicken Sie auf die Schaltfläche **Speichern.**

    ![](images/AzureLabs-Lab311-08.png)

9.  Ihr Speicher wird bestätigt, und Sie können sich über das **Anwendungsregistrierungsportal** abmelden.

## <a name="chapter-2---set-up-the-unity-project"></a>Kapitel 2: Einrichten des Unity-Projekts

Im Folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Mixed Reality und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity,* und klicken Sie auf **Neu.**

    ![](images/AzureLabs-Lab311-09.png)

2.  Sie müssen einen Unity-Projektnamen angeben. Fügen Sie **MSGraphMR** ein. Stellen Sie sicher, dass die Projektvorlage auf **3D** festgelegt ist. Legen Sie den **Speicherort** auf einen für Sie geeigneten Speicherort fest (denken Sie daran, dass näher an den Stammverzeichnissen besser ist). Klicken Sie dann auf **Projekt erstellen.**

    ![](images/AzureLabs-Lab311-10.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, ob der **Standardskript-Editor** auf **Visual Studio** festgelegt ist. Navigieren **Sie** zu  >  **Einstellungen** bearbeiten, und navigieren Sie dann im neuen Fenster zu **Externe Tools.** Ändern Sie **den externen Skript-Editor** in **Visual Studio 2017**. Schließen Sie das Fenster **Einstellungen.**

    ![](images/AzureLabs-Lab311-11.png)

4.  Wechseln Sie zu  >  **Dateibuild Einstellungen,** wählen Sie **Universelle Windows Plattform** aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln,** um Ihre Auswahl anzuwenden.

    ![](images/AzureLabs-Lab311-12.png)

5.  Stellen Sie im  >  **Dateibuild Einstellungen** sicher, dass:

    1. **Zielgerät** ist auf **HoloLens**
    2. **Buildtyp** ist auf **D3D** festgelegt
    3. **SDK** ist auf **Latest installed (Neueste Installation)** festgelegt.
    4. **Visual Studio Version** ist auf **Neueste installiert** festgelegt.
    5. **Build und Ausführung** ist auf **Lokaler Computer** festgelegt.
    6. Speichern Sie die Szene, und fügen Sie sie dem Build hinzu.

        1. Wählen Sie hierzu **Öffnende Szenen hinzufügen aus.** Ein Speicherfenster wird angezeigt.

            ![](images/AzureLabs-Lab311-13.png)

        2. Erstellen Sie einen neuen Ordner für diese und jede zukünftige Szene. Wählen Sie die Schaltfläche **Neuer Ordner** aus, um einen neuen Ordner zu erstellen, und nennen Sie ihn **Scenes**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Öffnen Sie den neu erstellten Ordner **Scenes,** und geben Sie dann im Textfeld *Dateiname*: **MR_ComputerVisionScene** ein, und klicken Sie dann auf **Speichern.**

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner *Assets* speichern müssen, da sie dem Unity-Projekt zugeordnet sein müssen. Das Erstellen des Ordners scenes (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.

    7.  Die übrigen Einstellungen in *Build Einstellungen* sollten vorerst als Standard verwendet werden.

6.  Klicken *Sie* im Fenster Build Einstellungen auf die Schaltfläche **Player Einstellungen.** Dadurch wird der zugehörige Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet. 

    ![](images/AzureLabs-Lab311-16.png)

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Auf der Registerkarte **Andere Einstellungen:**

        1.  Die **Skriptruntimeversion** sollte **experimentell** sein (.NET 4.6-Entsprechung), wodurch der Editor neu gestartet werden muss. 

        2. **Das Skript-Back-End** sollte **.NET sein.**

        3. **Der API-Kompatibilitätsgrad** sollte **.NET 4.6 sein.**

            ![](images/AzureLabs-Lab311-17.png)

    2.  Aktivieren Sie **auf Einstellungen** Registerkarte Publishing Einstellungen unter **Capabilities (Funktionen)** Die folgenden Optionen:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Aktivieren Sie weiter unten im Bereich in **XR Einstellungen** (unter Publish **Einstellungen )** **(Virtual Reality** unterstützt), und stellen Sie sicher, dass das Windows Mixed Reality **SDK** hinzugefügt wird.

        ![](images/AzureLabs-Lab311-19.png)

8.  Im *Build-Einstellungen* ist *Unity C#-Projekte* nicht mehr ausgegraut. Aktivieren Sie das Kontrollkästchen neben diesem.

9.  Schließen Sie das Fenster *Buildeinstellungen*.

10.  Speichern Sie Ihre Szene und Ihr Projekt (**FILE**  >  **SAVE SCENES /FILE**  >  **SAVE PROJECT**).

## <a name="chapter-3---import-libraries-in-unity"></a>Kapitel 3: Importieren von Bibliotheken in Unity

> [!IMPORTANT]
> Wenn Sie die *Unity-Komponente* Einrichten dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)herunterladen, als benutzerdefiniertes Paket in Ihr Projekt importieren und dann mit Kapitel [5](#chapter-5---create-meetingsui-class)fortfahren. [](https://docs.unity3d.com/Manual/AssetPackages.html)

Um *Microsoft Graph* Unity verwenden zu können, müssen Sie die **DLL Microsoft.Identity.Client** verwenden. Es ist möglich, das Microsoft Graph SDK zu verwenden, es erfordert jedoch das Addition eines NuGet-Pakets, nachdem Sie das Unity-Projekt erstellt haben (d. h. das Projekt nach dem Build bearbeiten). Es wird als einfacher angesehen, die erforderlichen DLLs direkt in Unity zu importieren.

> [!NOTE]
> Derzeit gibt es ein bekanntes Problem in Unity, bei dem Plug-Ins nach dem Import neu konfiguriert werden müssen. Diese Schritte (4 bis 7 in diesem Abschnitt) sind nicht mehr erforderlich, nachdem der Fehler behoben wurde.

Um *Microsoft Graph* in Ihr eigenes Projekt zu importieren, [laden Sie die MSGraph_LabPlugins.zip herunter.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage) Dieses Paket wurde mit Versionen der bibliotheken erstellt, die getestet wurden.

Wenn Sie mehr über das Hinzufügen benutzerdefinierter DLLs zu Ihrem Unity-Projekt erfahren möchten, folgen [Sie diesem Link.](https://docs.unity3d.com/Manual/UsingDLL.html)

So importieren Sie das Paket:

1.  Fügen Sie Unity das Unity-Paket hinzu, indem Sie **die**  >  **Menüoption Assets Import Package** Custom Package  >  (Benutzerdefiniertes **Paket** importieren) verwenden. Wählen Sie das Paket aus, das Sie gerade heruntergeladen haben.

2.  Vergewissern Sie sich im angezeigten Feld **Unity-Paket** importieren, dass alles unter (und einschließlich) **Plug-Ins** ausgewählt ist.

    ![](images/AzureLabs-Lab311-20.png)

3.  Klicken Sie auf **die Schaltfläche** Importieren, um dem Projekt die Elemente hinzuzufügen.

4.  Wechseln Sie im Bereich  "Project Panel" unter Plug-Ins zum Ordner **MSGraph,** *und* wählen Sie das Plug-In **Microsoft.Identity.Client aus.**

    ![](images/AzureLabs-Lab311-21.png)

5.  Stellen Sie *bei ausgewähltem* Plug-In sicher, dass Alle Plattformen deaktiviert ist, stellen Sie sicher, dass **auch WSAPlayer** deaktiviert ist, und klicken Sie dann auf **Übernehmen.**  Dadurch wird lediglich bestätigt, dass die Dateien ordnungsgemäß konfiguriert sind.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Durch das Markieren dieser Plug-Ins werden sie so konfiguriert, dass sie nur im Unity-Editor verwendet werden. Es gibt einen anderen Satz von DLLs im WSA-Ordner, der verwendet wird, nachdem das Projekt aus Unity als universelle anwendung Windows wurde.

6.  Als Nächstes müssen Sie den **Ordner WSA** im **Ordner MSGraph** öffnen. Sie sehen eine Kopie derselben Datei, die Sie gerade konfiguriert haben. Wählen Sie die Datei und dann im Inspektor aus:

    -   Stellen Sie **sicher, dass Die** Option **Beliebige Plattform deaktiviert** ist und dass **nur** **WSAPlayer** aktiviert **ist.**

    -   Stellen Sie **sicher,** dass das SDK auf **UWP** und **das Skript-Back-End** auf **Dot Net festgelegt ist.**

    -   Stellen Sie **sicher, dass Nicht verarbeiten** **auf überprüft ist.**

        ![](images/AzureLabs-Lab311-23.png)

7.  Klicken Sie auf **Anwenden**.

## <a name="chapter-4---camera-setup"></a>Kapitel 4: Kameraeinrichtung

In diesem Kapitel richten Sie die Hauptkamera Ihrer Szene ein:

1.  Wählen Sie *im Hierarchiebereich* die **Hauptkamera aus.**

2.  Nach der Auswahl können Sie alle Komponenten  der Hauptkamera im *Inspektorbereich* sehen.

    1.  Das **Camera-Objekt** muss den Namen **Hauptkamera haben** (beachten Sie die Schreibweise!)

    2.  Das **Hauptkameratag muss** auf **MainCamera** festgelegt werden (beachten Sie die Schreibweise!)

    3.  Stellen Sie **sicher, dass die Transformationsposition** auf **0, 0, 0 festgelegt ist.**

    4.  Festlegen **von Clear Flags auf** Solid **Color**

    5.  Legen Sie **die Hintergrundfarbe** der Kamerakomponente auf **Schwarz, Alpha 0** **fest (Hexadezimaler Code: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  Die endgültige Objektstruktur im *Hierarchiebereich* sollte der in der folgenden Abbildung gezeigten strukturieren:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Kapitel 5: Erstellen einer MeetingsUI-Klasse

Das erste Skript, das Sie erstellen müssen, ist **MeetingsUI,** das für das Hosten und Aufsenden der Benutzeroberfläche der Anwendung (Begrüßungsnachricht, Anweisungen und Details der Besprechungen) verantwortlich ist.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste **auf den** Ordner Assets im Project *Panel,* und wählen Sie **dann Ordner**  >  **erstellen aus.** Nennen Sie den Ordner **Scripts**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Öffnen Sie den **Ordner Skripts,** und klicken Sie dann in diesem Ordner mit der rechten Maustaste auf   >  **C#-Skript erstellen.** Nennen Sie das **Skript MeetingsUI.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Doppelklicken Sie auf das neue **MeetingsUI-Skript,** um es mit *Visual Studio.*

4.  Fügen Sie die folgenden Namespaces ein:

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  Fügen Sie in der -Klasse die folgenden Variablen ein:

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  Ersetzen Sie dann die **Start()-Methode,** und fügen Sie eine **"Awake()"-Methode** hinzu. Diese werden aufgerufen, wenn die -Klasse initialisiert wird:

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  Fügen Sie die Methoden hinzu, die für das Erstellen der *Benutzeroberfläche für Besprechungen* verantwortlich sind, und füllen Sie sie mit den aktuellen Besprechungen auf, wenn sie angefordert werden:

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **Löschen** Sie die **Update()-Methode,** und speichern Sie **Ihre Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren. 

## <a name="chapter-6---create-the-graph-class"></a>Kapitel 6: Erstellen der Graph-Klasse

Das nächste zu erstellende Skript ist das **Graph** Skript. Dieses Skript ist für die Aufrufe zur Authentifizierung des Benutzers und zum Abrufen der geplanten Besprechungen für den aktuellen Tag aus dem Kalender des Benutzers verantwortlich.

So erstellen Sie diese Klasse:

1.  Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken **Sie auf**  >  **C#-Skript erstellen.** Geben Sie dem Skript **Graph.**

3.  Doppelklicken Sie auf das Skript, um es mit dem Visual Studio.

4.  Fügen Sie die folgenden Namespaces ein:

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > Sie werden feststellen, dass Teile des Codes [](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)in diesem Skript um Vorkompilieren-Direktiven umschlossen sind. Dadurch werden Probleme mit den Bibliotheken beim Erstellen der Visual Studio vermieden.

5.  Löschen Sie **die Methoden Start()** und **Update(),** da sie nicht verwendet werden.

6.  Fügen Sie **Graph-Klasse** die folgenden Objekte ein, die zum Deserialisieren des JSON-Objekts erforderlich sind, das die täglich geplanten Besprechungen darstellt:

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  Fügen Sie **Graph** -Klasse die folgenden Variablen hinzu:

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > Ändern Sie **den appId-Wert** in die **App-ID,** die Sie sich in Kapitel **[1](#chapter-1---create-your-app-in-the-application-registration-portal), Schritt 4 notiert haben.** Dieser Wert sollte mit dem Wert identisch **sein,** der im Anwendungsregistrierungsportal auf der Anwendungsregistrierungsseite angezeigt wird.

8.  Fügen Sie **Graph-Klasse** die Methoden **SignInAsync()** und **AquireTokenAsync()** hinzu, die den Benutzer zum Einfügen der Anmeldeinformationen auffordern.

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successful, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  Fügen Sie die folgenden beiden Methoden hinzu:

    1.  **BuildTodayCalendarEndpoint()**: Erstellt den URI, der den Tag und die Zeitspanne an dem die geplanten Besprechungen abgerufen werden.

    2.  **ListMeetingsAsync()**, die die geplanten Besprechungen von *Microsoft* Graph.

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. Sie haben das Skript **Graph** abgeschlossen. **Speichern Sie Ihre Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren.

## <a name="chapter-7---create-the-gazeinput-script"></a>Kapitel 7: Erstellen des GazeInput-Skripts

Sie erstellen nun den **GazeInput.** Diese Klasse verarbeitet und verfolgt das Anvis des Benutzers mithilfe eines **Raycasts,** der von der **Hauptkamera** kommt und vorwärts wächst.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken **Sie auf**  >  **C#-Skript erstellen.** Nennen Sie das **Skript GazeInput**.

3.  Doppelklicken Sie auf das Skript, um es mit dem Visual Studio.

4.  Ändern Sie den Namespacecode so, dass er dem folgenden Code folgt, und fügen Sie zusätzlich zur **GazeInput-Klasse** das Tag '**\[ System.Serializable \]**' hinzu, damit es serialisiert werden kann:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  Fügen Sie **in der GazeInput-Klasse** die folgenden Variablen hinzu:

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  Fügen Sie **die CreateCursor()-Methode** hinzu, um den HoloLens in der Szene zu erstellen, und rufen Sie die -Methode über die **Start()-Methode** auf:

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  Mit den folgenden Methoden können Sie Raycast anvisieren und die fokussierten Objekte nachverfolgen.

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
                HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **Speichern Sie Ihre Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren.

## <a name="chapter-8---create-the-interactions-class"></a>Kapitel 8: Erstellen der Interactions-Klasse

Sie müssen nun das Skript Interaktionen **erstellen,** das für Folgendes zuständig ist:

-   Behandeln der **Tap-Interaktion** und des **Camera Gaze,wodurch** der Benutzer mit dem Protokoll in der "Schaltfläche" in der Szene interagieren kann.

-   Erstellen des Anmeldeobjekts "button" in der Szene, mit dem der Benutzer interagieren kann.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf den **Ordner Skripts,** um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in **den Ordner Skripts,** und klicken **Sie auf**  >  **C#-Skript erstellen.** Nennen Sie das Skript **Interaktionen**.

3.  Doppelklicken Sie auf das Skript, um es mit Visual Studio zu öffnen.

4.  Fügen Sie die folgenden Namespaces ein:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Ändern Sie die Vererbung der **Interaction-Klasse** von *MonoBehaviour* in **GazeInput**.

    ~~interaktionen der öffentlichen Klasse: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  Fügen Sie in der **Interaction-Klasse** die folgende Variable ein:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Ersetzen  Sie die Start-Methode. Beachten Sie, dass es sich um eine Überschreibungsmethode handelt, die die Gaze-Klassenmethode "base" aufruft. **Start()** wird aufgerufen, wenn die Klasse initialisiert wird, sich für die Eingabeerkennung registriert und die *Anmeldeschaltfläche* in der Szene erstellt:

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  Fügen Sie die **CreateSignInButton()-Methode** hinzu, die die *Anmeldeschaltfläche* in der Szene instanziiert und ihre Eigenschaften festlegt:

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  Fügen Sie die **GestureRecognizer_Tapped()-Methode** hinzu, die auf das *Tap-Benutzerereignis* reagiert.

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **Löschen Sie** die **Update()-Methode,** und **speichern Sie** ihre Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.

## <a name="chapter-9---set-up-the-script-references"></a>Kapitel 9: Einrichten der Skriptverweise

In diesem Kapitel müssen Sie das **Skript Interaktionen** auf der **Hauptkamera** platzieren. Dieses Skript verarbeitet dann das Platzieren der anderen Skripts, wo sie sich befinden müssen.

-  Ziehen Sie aus dem Ordner **Skripts** im *Project Panel* das Skript **Interaktionen** in das **Objekt Hauptkamera,** wie unten dargestellt.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Kapitel 10: Einrichten des Tags

Der Code, der das Anvieren behandelt, verwendet das Tag **SignInButton,** um zu identifizieren, mit welchem Objekt der Benutzer interagieren soll, um sich bei *Microsoft Graph* anzumelden.

So erstellen Sie das Tag:

1.  Klicken Sie im Unity-Editor im *Hierarchiebereich* auf die **Hauptkamera.**

2.  Klicken Sie im *Inspektorbereich* auf das *Tag* **MainCamera,** um eine Dropdownliste zu öffnen. Klicken Sie auf **Tag hinzufügen...**

    ![](images/AzureLabs-Lab311-30.png)

3.  Klicken Sie auf die **+** Schaltfläche.

    ![](images/AzureLabs-Lab311-31.png)

4.  Schreiben Sie den Tagnamen als **SignInButton,** und klicken Sie auf Speichern.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Kapitel 11: Erstellen des Unity-Projekts für die UWP

Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, wurde nun abgeschlossen, daher ist es an der Zeit, es aus Unity zu erstellen.

1.  Navigieren Sie zu *Build Einstellungen* (**Datei* > *Build Einstellungen**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Wenn nicht bereits, aktivieren Sie **Unity \# C-Projekte.**

3.  Klicken Sie auf **Erstellen**. Unity startet ein **Datei-Explorer-Fenster,** in dem Sie erstellen und dann einen Ordner auswählen müssen, in dem die App erstellt werden soll. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn **App**. Klicken Sie dann bei ausgewähltem **App-Ordner** auf **Ordner auswählen.**

4.  Unity beginnt mit dem Erstellen Ihres Projekts im Ordner **App.**

5.  Sobald Unity die Erstellung abgeschlossen hat (es kann einige Zeit dauern), öffnet es ein **Datei-Explorer-Fenster** am Speicherort Ihres Builds (überprüfen Sie die Taskleiste, da sie möglicherweise nicht immer über Ihren Fenstern angezeigt wird, Sie aber über das Hinzufügen eines neuen Fensters benachrichtigt werden).

## <a name="chapter-12---deploy-to-hololens"></a>Kapitel 12: Bereitstellen in HoloLens

So stellen Sie auf HoloLens bereit:

1.  Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote Deploy) und stellen sicher, dass sich Ihre HoloLens im **Entwicklermodus befindet.** Aufgabe:

    1.  Öffnen Sie während der HoloLens die **Einstellungen**.

    2.  Wechseln Sie zu **Network & Internet**  >  **WI-Fi** Advanced  >  **Options (Erweiterte Wlan-Optionen** für Netzwerk & Internet).

    3.  Notieren Sie sich die **IPv4-Adresse.**

    4.  Navigieren Sie als Nächstes zurück zu **Einstellungen** und dann zu Update & Security For Developers **(Sicherheit**  >  **für Entwickler** aktualisieren).

    5.  Legen Sie **den Entwicklermodus auf fest.**

2.  Navigieren Sie zu Ihrem neuen Unity-Build (dem **Ordner App),** und öffnen Sie die Projektmappendatei mit **Visual Studio**.

3.  Wählen Sie in der **Projektmappenkonfiguration** **debuggen** aus.

4.  Wählen Sie in der **Projektmappenplattform** die Option **x86, Remotecomputer aus.** Sie werden aufgefordert, die **IP-Adresse** eines Remotegeräts einzufügen (in diesem Fall die HoloLens, die Sie notiert haben).

    ![](images/AzureLabs-Lab311-34.png)

5.  Wechseln Sie zum Menü **Erstellen,** und klicken Sie auf **Lösung bereitstellen,** um die Anwendung in Ihre HoloLens zu querladen.

6.  Ihre App sollte nun in der Liste der installierten Apps auf Ihrem HoloLens angezeigt werden, damit sie gestartet werden kann.

## <a name="your-microsoft-graph-hololens-application"></a>Ihre Microsoft Graph HoloLens-Anwendung

Herzlichen Glückwunsch! Sie haben eine Mixed Reality-App erstellt, die die Microsoft Graph nutzt, um Kalenderdaten von Benutzern zu lesen und anzuzeigen.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Zusatzübungen

### <a name="exercise-1"></a>Übung 1

Verwenden von Microsoft Graph zum Anzeigen anderer Benutzerinformationen

-   Benutzer-E-Mail-Adresse/Telefonnummer/Profilbild

### <a name="exercise-1"></a>Übung 1

Implementieren Sie die Sprachsteuerung, um auf der Benutzeroberfläche von Microsoft Graph zu navigieren.