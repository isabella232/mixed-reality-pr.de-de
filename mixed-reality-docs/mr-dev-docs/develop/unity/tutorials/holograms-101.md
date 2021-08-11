---
title: 'HoloLens (1. Generation) Grundlagen 101: Vollständiges Projekt mit Gerät'
description: Befolgen Sie diese exemplarische Vorgehensweise zum Programmieren mit Unity, Visual Studio und HoloLens, um die Grundlagen der Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Mixed Reality, Windows Mixed Reality, HoloLens, Hologramm, Academy, Tutorial, HoloLens, Mixed Reality Academy, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Windows 10
ms.openlocfilehash: 63219edebeb63dbf4589e8162f8dc1bab83275c38f29b106db9bae234cdabde0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200960"
---
# <a name="hololens-1st-gen-basics-101-complete-project-with-device"></a>HoloLens (1. Generation) Grundlagen 101: Abschließen eines Projekts mit Gerät

<br>

>[!IMPORTANT]
>Die Mixed Reality Academy-Tutorials wurden mit HoloLens (1. Generation), Unity 2017 und Mixed Reality immersive Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen. Diese Tutorials werden **_nicht mit_** den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 und sind möglicherweise nicht mit neueren Versionen von Unity kompatibel.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](mrlearning-base.md) für HoloLens 2 veröffentlicht.

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

Dieses Tutorial führt Sie durch ein [vollständiges,](../../../design/gaze-and-commit.md#composite-gestures)in Unity integriertes Projekt, das grundlegende Windows Mixed Reality-Features auf HoloLens veranschaulicht, einschließlich Anvieren, [](../../../design/gaze-and-commit.md)Gesten, [](../../../design/voice-input.md)Spracheingabe, räumlichem Sound und räumlicher [Zuordnung.](../../../design/spatial-mapping.md) [](../../../design/spatial-sound.md)

Das Tutorial dauert etwa eine Stunde.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR-Grundlagen 101: Vollständiges Projekt mit Gerät</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Vorbereitung

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10 PC, der mit den richtigen [installierten Tools konfiguriert ist.](../../install-the-tools.md)
* Ein HoloLens, [das für die Entwicklung konfiguriert ist.](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Projektdateien

* Laden Sie [die für](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) das Projekt erforderlichen Dateien herunter. Erfordert Unity 2017.2 oder höher.
  * Wenn Sie weiterhin Unity 5.6-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)
  * Wenn Sie weiterhin Unity 5.5-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)
  * Wenn Sie weiterhin Unity 5.4-Unterstützung benötigen, verwenden Sie [dieses Release.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)
* Archivieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht erreichbaren Speicherort. Behalten Sie den Ordnernamen **Origami bei.**

>[!NOTE]
>Wenn Sie den Quellcode vor dem Herunterladen durchschauen möchten, ist er [auf GitHub.](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)

## <a name="chapter-1---holo-world"></a>Kapitel 1 : "Holo"-Welt

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

In diesem Kapitel richten wir unser erstes Unity-Projekt ein und führen den Build- und Bereitstellungsprozess schrittweise durch.

### <a name="objectives"></a>Ziele

* Richten Sie Unity für die holografische Entwicklung ein.
* Machen Sie ein Hologramm.
* Sehen Sie sich ein Hologramm an, das Sie gemacht haben.

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wähle **Öffnen** aus.
* Geben Sie location als **Origami-Ordner** ein, den Sie zuvor nicht archiviert haben.
* Wählen Sie **Origami aus,** und klicken Sie **auf Ordner auswählen.**
* Da das **Origami-Projekt** keine Szene enthält, speichern Sie die leere Standardszene in einer neuen Datei mit: **File**  /  **Save Scene As**.
* Nennen Sie die neue **Szene Origami,** und klicken Sie **auf die Schaltfläche** Speichern.

#### <a name="setup-the-main-virtual-camera"></a>Einrichten der virtuellen Hauptkamera

* Wählen Sie im **Hierarchiebereich** die Option **Hauptkamera** aus.
* Legen Sie **im Inspector** seine Transformationsposition auf **0,0,0 fest.**
* Suchen Sie die **Eigenschaft Flags löschen,** und ändern Sie die Dropdownliste von **Skybox** in **Volltonfarbe.**
* Klicken Sie auf das Feld **Hintergrund**, um eine Farbauswahl zu öffnen.
* Legen Sie **R, G, B und A** auf **0** fest.

#### <a name="setup-the-scene"></a>Einrichten der Szene

* Klicken Sie **im Hierarchiebereich** **auf** Create and Create Empty **(Leere erstellen).**
* Klicken Sie mit der rechten Maustaste auf das neue **GameObject,** und wählen Sie Umbenennen aus. Benennen Sie gameObject in **OrigamiCollection um.**
* Erweitern Sie **Hologramme** Ordner im Project-Bereich (erweitern Sie Assets, und wählen Sie Hologramme aus, oder doppelklicken Sie im Project-Bereich auf Hologramme Ordner ):
  * Ziehen **Sie Stage** in die Hierarchie, um ein untergeordnetes Element von **OrigamiCollection zu sein.**
  * Ziehen **Sie Sphere1** in die Hierarchie, um ein untergeordnetes Element von **OrigamiCollection zu sein.**
  * Ziehen **Sie Sphere2** in die Hierarchie, um ein untergeordnetes Element von **OrigamiCollection zu sein.**
* Klicken Sie im Hierarchiebereich mit der rechten Maustaste auf das Objekt **Directional Light,** **und** wählen Sie **Löschen aus.**
* Ziehen Sie **Hologramme** Ordner Lights **in** das Stammverzeichnis des **Hierarchiebereichs.**
* Wählen Sie **in der** Hierarchie die **OrigamiCollection aus.**
* Legen Sie **im Inspektor** die Transformationsposition auf **0, -0,5, 2,0 fest.**
* Klicken Sie in Unity **auf** die Schaltfläche Wiedergabe, um eine Vorschau Ihrer Hologramme anzuzeigen.
* Die Origami-Objekte sollten im Vorschaufenster angezeigt werden.
* Klicken **Sie ein** zweites Mal auf Wiedergabe, um den Vorschaumodus zu beenden.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Exportieren des Projekts aus Unity in Visual Studio

* Wählen Sie in Unity **Datei > Build Einstellungen.**
* Wählen **Sie universelle Windows Plattform** in der **Liste Plattform aus,** und klicken Sie **auf Plattform wechseln.**
* Legen **Sie SDK** auf Universal **10 und** **Buildtyp auf** **D3D fest.**
* Überprüfen Sie **Unity C#-Projekte.**
* Klicken **Sie auf Geöffnete Szenen hinzufügen,** um die Szene hinzuzufügen.
* Klicken Sie auf **Erstellen**.
* Erstellen Sie im angezeigten Datei-Explorer-Fenster einen neuen Ordner mit **dem** Namen "App".
* Klicken Sie mit nur einem Klick **auf den App-Ordner**.
* Klicken Sie **auf Ordner auswählen.**
* Wenn Unity fertig ist, wird ein Datei-Explorer-Fenster angezeigt.
* Öffnen Sie den **Ordner App.**
* Öffnen Sie (doppelklicken Sie auf) **Origami.sln**.
* Ändern Sie in der oberen Symbolleiste Visual Studio Ziel von Debuggen in **Release** und von ARM in **X86.**
* Klicken Sie auf den Pfeil neben der Schaltfläche Gerät, und wählen Sie **Remotecomputer** aus, um die Bereitstellung über WLAN bereitzustellen.
  * Legen Sie **die Adresse** auf den Namen oder die IP-Adresse Ihrer HoloLens. Wenn Sie Ihre Geräte-IP-Adresse nicht kennen, sehen Sie sich die erweiterten Optionen für **Einstellungen > Network & Internet >** an, oder fragen Sie Cortana **"Hey Cortana, What es my IP address?" (Hey Cortana,** Wie lautet meine IP-Adresse?).
  * Wenn der HoloLens USB angeschlossen ist, können Sie stattdessen **Gerät** auswählen, das über USB bereitgestellt werden soll.
  * Lassen Sie den **Authentifizierungsmodus** auf **Universell festgelegt.**
  * Klicken Sie auf **Auswählen**.

* Klicken **Sie auf Debuggen > Starten ohne Debuggen,** oder drücken Sie **STRG+F5.** Wenn Dies die erste Bereitstellung auf Ihrem Gerät ist, müssen Sie es mit [dem Visual Studio.](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)

* Das Origami-Projekt wird nun in Ihrem Projekt HoloLens bereitgestellt und dann ausgeführt.
* Setzen Sie Ihre HoloLens, und sehen Sie sich um, um Ihre neuen Hologramme zu sehen.

## <a name="chapter-2---gaze"></a>Kapitel 2: Anvingen

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

In diesem Kapitel stellen wir die erste von drei Möglichkeiten der Interaktion mit Ihren Hologrammen vor: [anvieren](../../../design/gaze-and-commit.md).

### <a name="objectives"></a>Ziele

* Visualisieren Sie Das Anvisieren mithilfe eines weltgesperrten Cursors.

### <a name="instructions"></a>Anweisungen

* Wechseln Sie zurück zu Ihrem Unity-Projekt, und schließen Sie das Fenster Build Einstellungen, wenn es noch geöffnet ist.
* Wählen Sie **Hologramme** Ordner im Project **aus.**
* Ziehen Sie **das Cursor-Objekt** in **den Hierarchiebereich** auf der Stammebene.
* Doppelklicken Sie auf das **Cursorobjekt,** um es genauer zu betrachten.
* Klicken Sie mit der rechten Maustaste auf den Ordner **Skripts** im Project Bereich.
* Klicken Sie **auf das** Untermenü Erstellen.
* Wählen Sie **C#-Skript aus.**
* Nennen Sie das Skript **WorldCursor**. Hinweis: Beim Namen wird die Groß-/Kleinschreibung beachtet. Sie müssen die CS-Erweiterung nicht hinzufügen.
* Wählen Sie im **Hierarchiebereich** das **Cursor-Objekt** aus.
* Drag and drop the **WorldCursor** script into the **Inspector panel**.
* Doppelklicken Sie auf das **WorldCursor-Skript,** um es in Visual Studio zu öffnen.
* Kopieren Sie diesen Code, fügen Sie ihn in **worldCursor.cs** ein, und **speichern Sie alle**.

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* Erstellen Sie die App über **File > Build Einstellungen** neu.
* Kehren Sie zur Visual Studio Lösung zurück, die zuvor für die Bereitstellung auf Ihrem HoloLens verwendet wurde.
* Wählen Sie "Alle erneut laden" aus, wenn Sie dazu aufgefordert werden.
* Klicken Sie auf **Debuggen -> Ohne Debuggen starten,** oder drücken **Sie STRG+F5.**
* Sehen Sie sich nun die Szene an, und beachten Sie, wie der Cursor mit der Form von Objekten interagiert.

## <a name="chapter-3---gestures"></a>Kapitel 3: Gesten

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

In diesem Kapitel fügen wir Unterstützung für [Gesten hinzu.](../../../design/gaze-and-commit.md#composite-gestures) Wenn der Benutzer eine Papierkugel auswählt, lassen wir die Kugel fallen, indem wir die Schwerkraft mithilfe der Physikalischen Engine von Unity aktivieren.

### <a name="objectives"></a>Ziele

* Steuern Sie Ihre Hologramme mit der Geste Auswählen.

### <a name="instructions"></a>Anweisungen

Wir beginnen mit der Erstellung eines Skripts und können dann die Select-Geste erkennen.

* Erstellen Sie im Ordner **Skripts** ein Skript mit dem Namen **GazeGestureManager.**
* Ziehen Sie das **GazeGestureManager-Skript** auf das **OrigamiCollection-Objekt** in der Hierarchie.
* Öffnen Sie das **GazeGestureManager-Skript** in Visual Studio, und fügen Sie den folgenden Code hinzu:

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Erstellen Sie im Ordner Skripts ein weiteres Skript mit dem Namen **SphereCommands**.
* Erweitern Sie das **OrigamiCollection-Objekt** in der Hierarchieansicht.
* Ziehen Sie das **SphereCommands-Skript** auf das **Sphere1-Objekt** im Hierarchiebereich.
* Ziehen Sie das **SphereCommands-Skript** auf das **Sphere2-Objekt** im Hierarchiebereich.
* Öffnen Sie das Skript in Visual Studio für die Bearbeitung, und ersetzen Sie den Standardcode durch Folgendes:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* Exportieren, Erstellen und Bereitstellen der App in Ihrem HoloLens.
* Sehen Sie sich eine der Kugeln an.
* Führen Sie die Auswahlgeste aus, und beobachten Sie, wie die Kugel unten auf die Oberfläche fällt.

## <a name="chapter-4---voice"></a>Kapitel 4 – Stimme

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

In diesem Kapitel fügen wir Unterstützung für zwei [Sprachbefehle](../../../design/voice-input.md)hinzu: "Reset world" (Welt zurücksetzen), um die gelöschten Kugeln an ihre ursprüngliche Position zurückzugeben, und "Drop sphere" (Kugel ablegen), damit die Kugel fällt.

### <a name="objectives"></a>Ziele

* Fügen Sie Sprachbefehle hinzu, die immer im Hintergrund lauschen.
* Erstellen Sie ein Hologramm, das auf einen Sprachbefehl reagiert.

### <a name="instructions"></a>Anweisungen

* Erstellen Sie im Ordner **Skripts** ein Skript mit dem Namen **SpeechManager.**
* Ziehen Sie das **SpeechManager-Skript** auf das **OrigamiCollection-Objekt** in der Hierarchie.
* Öffnen Sie das **SpeechManager-Skript** in Visual Studio.
* Kopieren Sie diesen Code, fügen **Sie** ihn in **speechManager.cs** ein, und speichern Sie alle :

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Öffnen Sie das **SphereCommands-Skript** in Visual Studio.
* Aktualisieren Sie das Skript wie folgt, um es zu lesen:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* Exportieren, Erstellen und Bereitstellen der App in Ihrem HoloLens.
* Sehen Sie sich eine der Kugeln an, und sagen Sie "**Drop Sphere**".
* Sagen **Sie**" Reset World ", um sie wieder an ihre anfänglichen Positionen zu bringen.

## <a name="chapter-5---spatial-sound"></a>Kapitel 5: Räumlicher Sound

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

In diesem Kapitel fügen wir der App Musik hinzu und lösen dann Soundeffekte für bestimmte Aktionen aus. Wir verwenden [räumlichen Sound,](../../../design/spatial-sound.md) um Sounds eine bestimmte Position im 3D-Raum zu geben.

### <a name="objectives"></a>Ziele

* Hören Sie Hologramme in Ihrer Welt.

### <a name="instructions"></a>Anweisungen

* Wählen Sie in Unity im oberen Menü **> Project Einstellungen > Audio bearbeiten** aus.
* Suchen Sie im Inspektorbereich auf der rechten Seite die Einstellung **Spatializer-Plug-In,** und wählen Sie **MS HRTF Spatializer** aus.
* Ziehen Sie aus dem **Ordner Hologramme** im bereich Project das **Objekt "Ziehpunkt"** in das **OrigamiCollection-Objekt** im Hierarchiebereich.
* Wählen Sie **OrigamiCollection** aus, und suchen Sie im Bereich Inspector nach der Komponente **Audioquelle.** Ändern Sie diese Eigenschaften:
  * Überprüfen Sie die **Spatialize-Eigenschaft.**
  * Überprüfen Sie **die Play On Awake**-Datei.
  * Ändern Sie **Spatial Blend** in **3D,** indem Sie den Schieberegler ganz nach rechts ziehen. Der Wert sollte sich von 0 in 1 ändern, wenn Sie den Schieberegler verschieben.
  * Überprüfen Sie die **Loop-Eigenschaft.**
  * Erweitern Sie **3D Sound Einstellungen**, und geben Sie **0.1** für **Doppler-Ebene ein.**
  * Legen Sie **Volumerolloff** auf **Logarithmischer Rolloff** fest.
  * Legen Sie **Max Distance** auf **20** fest.
* Erstellen Sie im Ordner **Skripts** ein Skript mit dem Namen **SphereSounds.**
* Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.
* Öffnen **Sie SphereSounds** in Visual Studio, aktualisieren **Sie** den folgenden Code, und speichern Sie alle .

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* Speichern Sie das Skript, und kehren Sie zu Unity zurück.
* Exportieren, Erstellen und Bereitstellen der App in Ihrem HoloLens.
* Bewegen Sie sich näher und weiter von der Phase, und wechseln Sie zur Seite, um die Soundänderungen zu hören.

## <a name="chapter-6---spatial-mapping"></a>Kapitel 6: Räumliche Zuordnung

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

Nun verwenden wir [die räumliche Zuordnung,](../../../design/spatial-mapping.md) um das Spielbrett auf einem echten Objekt in der realen Welt zu platzieren.

### <a name="objectives"></a>Ziele

* Bringen Sie Ihre reale Welt in die virtuelle Welt ein.
* Platzieren Sie Ihre Hologramme dort, wo sie für Sie am wichtigsten sind.

### <a name="instructions"></a>Anweisungen

* Klicken Sie in Unity im **Bereich Project** auf den Ordner Hologramme.
* Ziehen Sie das **Medienobjekt Räumliche Zuordnung** in den Stamm der **Hierarchie**.
* Klicken Sie in der Hierarchie auf das Objekt **Räumliche Zuordnung.**
* Ändern Sie im **Inspektorbereich** die folgenden Eigenschaften:
  * Aktivieren Sie das Kontrollkästchen **Visuelle Gitternetze zeichnen.**
  * Suchen Sie **Nach Draw Material (Material zeichnen),** und klicken Sie auf den Kreis auf der rechten Seite. Geben Sie **"wireframe"** in das Suchfeld oben ein. Klicken Sie auf das Ergebnis, und schließen Sie das Fenster. Wenn Sie dies tun, sollte der Wert für Draw Material (Material zeichnen) auf Wireframe festgelegt werden.
* Exportieren, Erstellen und Bereitstellen der App in Ihrem HoloLens.
* Wenn die App ausgeführt wird, überlagert ein Wireframe-Gittermodell Ihre reale Welt.
* Beobachten Sie, wie eine rollierende Kugel von der Stufe und auf den Boden fällt!

Nun zeigen wir Ihnen, wie Sie die OrigamiCollection an einen neuen Speicherort verschieben:

* Erstellen Sie im Ordner **Skripts** ein Skript mit dem Namen **TapToPlaceParent.**
* Erweitern **Sie** in der Hierarchie die **OrigamiCollection,** und wählen Sie das **Stage-Objekt** aus.
* Ziehen Sie das **TapToPlaceParent-Skript** auf das Stage-Objekt.
* Öffnen Sie das **TapToPlaceParent-Skript** in Visual Studio, und aktualisieren Sie es wie folgt:

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* Exportieren, Erstellen und Bereitstellen der App.
* Nun sollten Sie das Spiel an einem bestimmten Ort platzieren können, indem Sie es mithilfe der Select-Geste an eine neue Position bewegen und die Select-Geste erneut verwenden.

## <a name="chapter-7---holographic-fun"></a>Kapitel 7 : Holografischer Spaß

### <a name="objectives"></a>Ziele

* Zeigen Sie den Eingang einer holografischen Unterwelt an.

### <a name="instructions"></a>Anweisungen

Nun zeigen wir Ihnen, wie Sie die holografische Unterwelt aufdecken:

* Im **ordner Hologramme** im Project Panel:
  * Ziehen Sie **Underworld** in die Hierarchie, um ein untergeordnetes Element von **OrigamiCollection** zu sein.
* Erstellen Sie im Ordner **Skripts** ein Skript mit dem Namen **HitTarget**.
* Erweitern **Sie** in der Hierarchie die **OrigamiCollection**.
* Erweitern Sie das **Stage-Objekt,** und wählen Sie das **Zielobjekt** (blauer Lüfter) aus.
* Ziehen Sie das **HitTarget-Skript** auf das **Target-Objekt.**
* Öffnen Sie das **HitTarget-Skript** in Visual Studio, und aktualisieren Sie es wie folgt:

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* Wählen Sie in Unity das **Zielobjekt** aus.
* Zwei öffentliche Eigenschaften sind jetzt in der **Komponente "Trefferziel"** sichtbar und müssen auf Objekte in unserer Szene verweisen:
  * Ziehen Sie **Underworld** aus dem **Hierarchiebereich** in die **Underworld-Eigenschaft** der **Komponente Ziel erreichen.**
  * Ziehen Sie **Stage** aus dem **Hierarchiebereich** in die **Eigenschaft Object to Hide (Objekt zum Ausblenden)** der **Komponente "Ziel erreichen".**
* Exportieren, Erstellen und Bereitstellen der App.
* Platzieren Sie die Origami-Sammlung auf dem Boden, und verwenden Sie dann die Select-Geste, um einen Kugelablage zu erstellen.
* Wenn die Kugel auf das Ziel (blauer Lüfter) trifft, tritt eine Explosion auf. Die Auflistung wird ausgeblendet, und eine Lücke zur Unterwelt wird angezeigt.

## <a name="the-end"></a>Das Ende

Und das ist das Ende dieses Tutorials!

Sie haben Folgendes gelernt:

* Erstellen einer holografischen App in Unity
* Verwenden von Anvieren, Gesten, Stimme, Sound und räumlicher Zuordnung.
* Erstellen und Bereitstellen einer App mithilfe von Visual Studio

Sie können nun mit der Erstellung Ihrer eigenen holografischen Erfahrung beginnen!

## <a name="see-also"></a>Siehe auch

* [MR-Grundlagen 101E: Vollständiges Projekt mit Emulator](holograms-101e.md)
* [Anvisieren](../../../design/gaze-and-commit.md)
* [Anvisieren mit dem Kopf und Ausführen](../../../design/gaze-and-commit.md)
* [Spracheingabe](../../../design/voice-input.md)
* [Raumklang](../../../design/spatial-sound.md)
* [Räumliche Abbildung](../../../design/spatial-mapping.md)