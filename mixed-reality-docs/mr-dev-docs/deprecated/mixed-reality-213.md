---
title: MR-Eingabe 213
description: Befolgen Sie dieses Programmiertutorial mit Unity, Visual Studio und immersiven Headsets, um die Details von Motion-Controllern zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, immersive, motion controller, academy, tutorial
ms.openlocfilehash: 1cb53ed619a978e2aef17b5006b6254e5c7d3b9f53a39fbcb5932ebcc44ca98b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210147"
---
# <a name="mr-input-213-motion-controllers"></a>MR-Eingabe 213: Motion-Controller

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](../develop/unity/tutorials/mr-learning-base-01.md) für HoloLens 2 veröffentlicht.

Motion-Controller in der Mixed Reality-Welt fügen eine weitere Ebene der Interaktivität hinzu. Mit [Motion-Controllern](../design/motion-controllers.md)können wir direkt auf natürlichere Weise mit Objekten interagieren, ähnlich wie bei unseren physischen Interaktionen im realen Leben, was das Immersions- und Bewegungserlebnis in Ihrer App erhöht.

In MR Input 213 untersuchen wir die Eingabeereignisse des Bewegungscontrollers, indem wir eine einfache Raumbilderfahrung erstellen. Mit dieser App können Benutzer in einem dreidimensionalen Raum mit verschiedenen Pinsel- und Farbtypen zeichnen.

## <a name="topics-covered-in-this-tutorial"></a>In diesem Tutorial behandelte Themen

|![MixedReality213-Thema1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Controllervisualisierung**|**Controllereingabeereignisse**|**Benutzerdefinierter Controller und Benutzeroberfläche**|
|Erfahren Sie, wie Sie Motion Controller-Modelle im Spielmodus und zur Laufzeit von Unity rendern.|Verstehen der verschiedenen Arten von Schaltflächenereignissen und deren Anwendungen.|Erfahren Sie, wie Sie Benutzeroberflächenelemente über dem Controller überlagern oder vollständig anpassen.|

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR-Eingabe 213: Motion-Controller</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Vorbereitung

### <a name="prerequisites"></a>Voraussetzungen

Weitere Informationen finden Sie auf dieser Seite in der Installationsprüfliste [für immersive Headsets.](../develop/install-the-tools.md)

* Für dieses Tutorial [ist Unity 2017.2.1p2 erforderlich.](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>Projektdateien

* [Laden Sie die für](https://github.com/Microsoft/MixedReality213/archive/master.zip) das Projekt erforderlichen Dateien herunter, und extrahieren Sie die Dateien auf dem Desktop.

>[!NOTE]
>Wenn Sie den Quellcode vor dem Herunterladen durchschauen möchten, ist er [auf GitHub.](https://github.com/Microsoft/MixedReality213)

## <a name="unity-setup"></a>Unity-Setup

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Ziele

* Optimieren von Unity für Windows Mixed Reality Entwicklung
* Setup Mixed Reality-Kamera
* Umgebung einrichten

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wähle **Öffnen** aus.
* Navigieren Sie zu Ihrem Desktop, und suchen Sie **den Ordner MixedReality213-master,** den Sie zuvor entarchiviert haben.
* Klicken Sie auf **Ordner auswählen**.
* Sobald Unity das Laden von Projektdateien abgeschlossen hat, können Sie den Unity-Editor sehen.
* Wählen Sie in Unity **Datei > Build Einstellungen.**

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* Wählen **Sie Windows Plattform** in der Liste Plattform **aus,** und klicken Sie **auf die Schaltfläche Plattform** wechseln.
* Festlegen des Zielgeräts auf **Ein beliebiges Gerät**
* Legen Sie Buildtyp auf **D3D** fest
* Festlegen des SDK auf **"Aktuell installiert"**
* Überprüfen **von Unity C#-Projekten**
    * Auf diese Weise können Sie Skriptdateien im Visual Studio ändern, ohne das Unity-Projekt neu zu erstellen.
* Klicken Sie **auf Player Einstellungen**.
* Scrollen **Sie im Inspektorbereich** nach unten nach unten.
* Aktivieren Sie in XR Einstellungen Virtual **Reality Supported (Virtual Reality unterstützt).**
* Wählen Sie unter Virtual Reality SDKs die Option **Windows Mixed Reality**

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* Schließen **Sie build Einstellungen** Fenster.

### <a name="project-structure"></a>Projektstruktur

In diesem Tutorial wird **[Mixed Reality Toolkit – Unity verwendet.](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Die Releases finden Sie auf [dieser Seite.](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Abgeschlossene Szenen für Ihre Referenz**

* Sie finden zwei abgeschlossene Unity-Szenen im **Ordner Szenen.**
    * **MixedReality213:** Abgeschlossene Szene mit einzelnem Pinsel
    * **MixedReality213Erfüllt: Abgeschlossene** Szene für erweitertes Design mit mehreren Pinseln

**Neues Szenensetup für das Tutorial**

* Klicken Sie in Unity **auf Datei > Neue Szene.**
* Löschen **der Hauptkamera** und **des direktionalen Lichts**
* Suchen Sie **Project Bereich , und** ziehen Sie die folgenden Prefabs in den **Hierarchiebereich:**
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Assets/AppPrefabs/Environment

    ![Kamera und Umgebung](images/mr213-cameraenvironment-300px.jpg)

* Es gibt zwei Kameravorfabs im Mixed Reality Toolkit:
    * **MixedRealityCamera.prefab:** Nur Kamera
    * **MixedRealityCameraParent.prefab:** Kamera + Teleportation + Begrenzung
    * In diesem Tutorial verwenden wir **MixedRealityCamera** ohne Teleportierungsfeature. Aus diesem Grund haben wir ein einfaches **Umgebungs-Prefab** hinzugefügt, das eine Grundfläche enthält, damit sich der Benutzer geerdt fühlen kann.
    * Weitere Informationen zur Teleportierung mit **MixedRealityCameraParent** finden Sie unter Advanced design - Teleportation and locomotion (Erweiterter Entwurf [– Teleportation und Locomotion).](#advanced-design---teleportation-and-locomotion)

**Skybox-Setup**

* Klicken **Sie auf > > Einstellungen**
* Klicken Sie rechts im Feld Skybox Material auf **den Kreis.**
* Geben Sie "gray" ein, und wählen **Sie SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat) aus.

    ![Festlegen von skybox](images/mr123-skyboxsetting-400px.jpg)

* Aktivieren **Sie die Skybox-Option,** um die zugewiesene graue Farbverlaufs-Skybox sehen zu können.

    ![Skybox-Option umschalten](images/mr213-skyboxcheck-400px.jpg)

* Die Szene mit MixedRealityCamera, Umgebung und grauem Skybox sieht wie hier aus.

    ![MixedReality213-Umgebung](images/mr213-environment-600px.jpg)

* Klicken Sie **auf Datei> um die Szene unter zu speichern.**
* **Speichern** Sie Ihre Szene unter dem Ordner Scenes (Szenen) mit einem beliebigen Namen.

## <a name="chapter-1---controller-visualization"></a>Kapitel 1: Controllervisualisierung

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie Motion Controller-Modelle im Spielmodus von Unity und zur Laufzeit rendern.

Windows Mixed Reality stellt ein animiertes Controllermodell für die Controllervisualisierung zur Verfügung. Es gibt mehrere Ansätze, die Sie für die Controllervisualisierung in Ihrer App verwenden können:

* Standard– Verwenden des Standardcontrollers ohne Änderungen
* Hybrid: Verwenden des Standardcontrollers, aber Anpassen einiger seiner Elemente oder Überlagern von Benutzeroberflächenkomponenten
* Ersetzung: Verwenden Ihres eigenen benutzerdefinierten 3D-Modells für den Controller

In diesem Kapitel erfahren Sie mehr über die Beispiele für diese Controlleranpassungen.

### <a name="instructions"></a>Anweisungen

* Geben Sie **im Project** Im Suchfeld **MotionControllers** ein. Sie finden sie auch unter Assets/HoloToolkit/Input/Prefabs/.
* Ziehen Sie **das MotionControllers-Prefab** in den **Hierarchiebereich.**
* Klicken Sie im Bereich Hierarchie auf das **MotionControllers-Prefab.** 

**MotionControllers-Prefab**

**Das MotionControllers-Prefab** verfügt über ein **MotionControllerVisualizer-Skript,** das die Slots für alternative Controllermodelle zur Verfügung stellt. Wenn Sie Ihre eigenen benutzerdefinierten 3D-Modelle zuweisen, z. B. eine Hand oder eine Schneide, und "Immer alternatives linkes/rechtes Modell verwenden" aktivieren, werden sie anstelle des Standardmodells angezeigt. Wir verwenden diesen Slot in Kapitel 4, um das Controllermodell durch einen Pinsel zu ersetzen.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Anweisungen**

* Doppelklicken Sie **im Bereich** Inspector auf **MotionControllerVisualizer script (MotionControllerVisualizer-Skript),** um den Code im Visual Studio

**MotionControllerVisualizer-Skript**

Die **Klassen MotionControllerVisualizer** und **MotionControllerInfo** bieten die Möglichkeit, auf & Standardcontrollermodelle zu ändern. **MotionControllerVisualizer** abonniert das **InteractionSourceDetected-Ereignis** von Unity und instanziiert automatisch Controllermodelle, wenn sie gefunden werden.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Die Controllermodelle werden gemäß der [glTF-Spezifikation bereitgestellt.](https://github.com/KhronosGroup/glTF) Dieses Format wurde erstellt, um ein allgemeines Format zu bieten und gleichzeitig den Prozess hinter dem Übertragen und Entpacken von 3D-Ressourcen zu verbessern. In diesem Fall müssen wir die Controllermodelle zur Laufzeit abrufen und laden, da wir die Benutzererfahrung so nahtlos wie möglich gestalten möchten, und es ist nicht garantiert, welche Version der Motion-Controller der Benutzer verwenden könnte. In diesem Kurs wird über das Mixed Reality Toolkit eine Version des [UnityGLTF-Projekts](https://github.com/KhronosGroup/UnityGLTF)der Group Unity verwendet.

Sobald der Controller übermittelt wurde, können Skripts **MotionControllerInfo** verwenden, um die Transformationen für bestimmte Controllerelemente zu finden, damit sie sich richtig positionieren können.

In einem späteren Kapitel erfahren Sie, wie Sie diese Skripts verwenden, um Benutzeroberflächenelemente an die Controller anfügen.

*In einigen Skripts finden Sie Codeblöcke mit **#if ! UNITY_EDITOR** oder **UNITY_WSA**. Diese Codeblöcke werden nur in der UWP-Runtime ausgeführt, wenn Sie die Bereitstellung in Windows. Dies liegt daran, dass sich die vom Unity-Editor und der UWP-App-Runtime verwendeten APIs unterscheiden.*

* **Speichern Sie** die Szene, und klicken Sie **auf die Wiedergabeschaltfläche.**

Sie können die Szene mit Motion-Controllern in Ihrem Headset sehen. Sie können detaillierte Animationen für Schaltflächenklicks, Thumbstickbewegungen und Touchpad-Touchhervorhebungen anzeigen.

![MR213_Controller-Standardvisualisierung](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Kapitel 2: Anfügen von Benutzeroberflächenelementen an den Controller

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Ziele

* Erfahren Sie mehr über die Elemente der Motion-Controller.
* Erfahren Sie, wie Sie Objekte an bestimmte Teile der Controller anfügen.

In diesem Kapitel erfahren Sie, wie Sie dem Controller Benutzeroberflächenelemente hinzufügen, auf die der Benutzer jederzeit problemlos zugreifen und bearbeiten kann. Außerdem erfahren Sie, wie Sie mithilfe der Touchpadeingabe eine einfache Farbauswahl-Benutzeroberfläche hinzufügen.

### <a name="instructions"></a>Anweisungen

* Suchen Sie **im Project** nach dem **Skript MotionControllerInfo.**
* Doppelklicken Sie im Suchergebnis auf **das Skript MotionControllerInfo,** um den Code in der Visual Studio.

**MotionControllerInfo-Skript**

Der erste Schritt besteht im Auswählen des Elements des Controllers, an das die Benutzeroberfläche angefügt werden soll. Diese Elemente werden in **ControllerElementEnum** in **MotionControllerInfo.cs definiert.**

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **Home**
* **Menü**
* **Begreifen**
* **Thumbstick**
* **Auswählen**
* **Touchpad**
* **Zeigende Pose:** Dieses Element stellt die Spitze des Controllers dar, der nach vorn zeigt.

**Anweisungen**

* Suchen Sie **Project** Bereich **AttachToController script (AttachToController-Skript).**
* Doppelklicken Sie im Suchergebnis auf **das Skript AttachToController,** um den Code in der Visual Studio.

**AttachToController-Skript**

Das **AttachToController-Skript** bietet eine einfache Möglichkeit zum Anfügen von Objekten an eine angegebene Controllerhändigkeit und ein angegebenes Element.

In **AttachElementToController()**

* Überprüfen der Übergabe mit **MotionControllerInfo.Handedness**
* Mit **MotionControllerInfo.TryGetElement()** können Sie ein bestimmtes Element des Controllers erhalten.
* Nachdem Sie die Transformation des Elements aus dem Controllermodell abgerufen haben, über- und übergeordnetes Objekt darunter, und legen Sie die lokale Position des Objekts & auf 0 (null) fest.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type &quot; + element + &quot; under controller &quot; + newController.ControllerParent.name + &quot;; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

Die einfachste Möglichkeit, **das AttachToController-Skript** zu verwenden, ist das Erben von diesem Skript, wie dies im Fall von **ColorPickerWheel der Fall ist.** Überschreiben Sie einfach **die Funktionen OnAttachToController** und **OnDetachFromController,** um die Einrichtung/Aufschlüsselung durchzuführen, wenn der Controller erkannt/getrennt wird.

**Anweisungen**

* Geben Sie **Project** Bereich in das Suchfeld **ColorPickerWheel ein.** Sie finden sie auch unter Assets/AppPrefabs/.
* Ziehen **Sie das ColorPickerWheel-Prefab** in den **Hierarchiebereich.**
* Klicken Sie im Bereich Hierarchie auf  das **Prefab ColorPickerWheel.**
* Doppelklicken Sie **im Inspektorbereich** auf **ColorPickerWheel** Script, um den Code in der Visual Studio.

![ColorPickerWheel-Prefab](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel-Skript**

Da **ColorPickerWheel** **AttachToController** erbt, werden  im Inspektorbereich **Handlichkeit** und **Element** angezeigt. Wir fügen die Benutzeroberfläche an das Touchpad-Element auf dem linken Controller an.

![ColorPickerWheel-Skript](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** überschreibt **OnAttachToController** und **OnDetachFromController,** um das Eingabeereignis zu abonnieren, das im nächsten Kapitel für die Farbauswahl mit Touchpadeingabe verwendet wird.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **Speichern Sie** die Szene, und klicken Sie **auf die Wiedergabeschaltfläche.**

**Alternative Methode zum Anfügen von Objekten an die Controller**

Es wird empfohlen, dass Ihre Skripts von **AttachToController erben** und **OnAttachToController überschreiben.** Dies ist jedoch möglicherweise nicht immer möglich. Eine Alternative ist die Verwendung als eigenständige Komponente. Dies kann nützlich sein, wenn Sie ein vorhandenes Prefab an einen Controller anfügen möchten, ohne Ihre Skripts umzugestalten. Warten Sie einfach, bis IsAttached auf TRUE festgelegt ist, bevor Sie ein Setup durchführen. Die einfachste Möglichkeit hierzu ist die Verwendung einer Coroutine für "Start".

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Kapitel 3: Arbeiten mit Touchpadeingaben

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie Touchpad-Eingabedatenereignisse erhalten.
* Erfahren Sie, wie Sie Die Positionsinformationen der Touchpadachse für Ihre App-Erfahrung verwenden.

### <a name="instructions"></a>Anweisungen

* Klicken Sie **im Bereich** Hierarchie auf **ColorPickerWheel.**
* Doppelklicken **Sie im Inspektorbereich** **unter Animator** auf **ColorPickerWheelController.**
* Sie können sehen, dass die **Registerkarte "Animator"** geöffnet ist.

**Anzeigen/Ausblenden der Benutzeroberfläche mit dem Animationscontroller von Unity**

Um die **ColorPickerWheel-Benutzeroberfläche** mit Animation anzuzeigen und auszublenden, verwenden wir [das Animationssystem von Unity.](https://docs.unity3d.com/Manual/AnimationOverview.html) Wenn Sie **die Visible-Eigenschaft von ColorPickerWheel** auf true oder false festlegen, werden **Animationstrigger** ein- **und** ausblenden ausgelöst.  **Die Parameter "Show"** **und "Hide"** werden im **ColorPickerWheelController-Animationscontroller** definiert.

![Unity-Animationscontroller](images/mr123-animationcontroller-550px.jpg)

**Anweisungen**

* Wählen Sie **im Bereich** Hierarchie die **Option ColorPickerWheel-Prefab** aus.
* Doppelklicken Sie **im Inspektorbereich** auf **das Skript ColorPickerWheel,** um den Code im Visual Studio

**ColorPickerWheel-Skript**

**ColorPickerWheel** abonniert das **InteractionSourceUpdated-Ereignis** von Unity, um auf Touchpadereignisse zu lauschen.

In **InteractionSourceUpdated()** überprüft das Skript zunächst, ob Folgendes sichergestellt ist:

* ist tatsächlich ein Touchpadereignis (obj.state.**touchpadTouched**)
* stammt vom linken Controller (obj.state.source.**handedness**)

Wenn beide true sind, die Position des Touchpads (obj.state.**touchpadPosition**) wird **selectorPosition zugewiesen.**

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

In **Update()** werden  basierend auf der sichtbaren Eigenschaft Animationstrigger ein- und ausblenden in der Animatorkomponente der Farbauswahl ausgelöst.

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

In **Update() wird** **selectorPosition** verwendet, um einen Strahl am Gitter-Collider des Farbrads zu werfen, der eine UV-Position zurückgibt. Diese Position kann dann verwendet werden, um die Pixelkoordinate und den Farbwert der Textur des Farbrads zu finden. Auf diesen Wert kann für andere Skripts über die **SelectedColor-Eigenschaft zugegriffen** werden.

![Farbwähler Wheel Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>Kapitel 4: Überschreiben des Controllermodells

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie das Controllermodell mit einem benutzerdefinierten 3D-Modell überschreiben.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Anweisungen

* Klicken Sie im Bereich Hierarchie **auf** **MotionControllers.**
* Klicken Sie rechts im Feld **Alternativer** rechter Controller auf den Kreis.
* Geben Sie **"BrushController" ein,** und wählen Sie das Prefab aus dem Ergebnis aus. Sie finden es unter Assets/AppPrefabs/**BrushController**.
* Aktivieren **Sie Immer alternatives rechtes Modell verwenden.**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

Das **BrushController-Prefab** muss nicht im **Hierarchiebereich enthalten** sein. So sehen Sie sich jedoch die untergeordneten Komponenten an:

* Geben Sie **im Project** Bereich **BrushController ein,** und ziehen Sie **das BrushController-Prefab** in den **Hierarchiebereich.**

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Sie finden die **Tip-Komponente** in **BrushController**. Wir verwenden seine Transformation, um das Zeichnen von Linien zu starten/zu beenden.

* Löschen Sie **brushController aus** dem **Hierarchiebereich.**
* **Speichern Sie** die Szene, und klicken Sie **auf die Wiedergabeschaltfläche.** Sie werden sehen, dass das Pinselmodell den rechten Bewegungscontroller ersetzt hat.

## <a name="chapter-5---painting-with-select-input"></a>Kapitel 5: Painting with Select input

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie das Select-Schaltflächenereignis verwenden, um eine Linienzeichnung zu starten und zu beenden.

### <a name="instructions"></a>Anweisungen

* Suchen **Sie im Project BrushController-Prefab.** 
* Doppelklicken Sie **im Inspektorbereich** auf **BrushController** Script, um den Code in der Visual Studio

**BrushController-Skript**

**BrushController** abonniert die **InteractionSourcePressed-** und **InteractionSourceReleased-Ereignisse des InteractionManager.** Wenn **das InteractionSourcePressed-Ereignis** ausgelöst wird, wird die **Draw-Eigenschaft** des Pinsels auf TRUE festgelegt. Wenn **das InteractionSourceReleased-Ereignis** ausgelöst wird, wird die **Draw-Eigenschaft** des Pinsels auf FALSE festgelegt.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

Während **Draw** auf TRUE festgelegt ist, generiert der Pinsel Punkte in einem instanziierten Unity **LineRenderer.** Ein Verweis auf dieses Prefab wird im Feld Stroke **Prefab** des Pinsels beibehalten.

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

Um die aktuell ausgewählte Farbe auf der Benutzeroberfläche des Farbauswahlrads zu verwenden, benötigt **BrushController** einen Verweis auf das **ColorPickerWheel-Objekt.** Da  das BrushController-Prefab zur Laufzeit als Ersatzcontroller instanziiert wird, müssen alle Verweise auf Objekte in der Szene zur Laufzeit festgelegt werden. In diesem Fall verwenden wir **GameObject.FindObjectOfType,** um **colorPickerWheel zu suchen:**

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **Speichern Sie** die Szene, und klicken Sie **auf die Wiedergabeschaltfläche.** Sie können die Linien zeichnen und zeichnen, indem Sie die Auswahlschaltfläche auf dem rechten Controller verwenden.

## <a name="chapter-6---object-spawning-with-select-input"></a>Kapitel 6: Objektabstand mit Eingabe auswählen

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie Eingabeereignisse der Schaltflächen "Auswählen" und "Erfassen" verwenden.
* Erfahren Sie, wie Sie Objekte instanziieren.

### <a name="instructions"></a>Anweisungen

* Geben Sie **Project** Bereich **ObjectSpawner** in das Suchfeld ein. Sie finden sie auch unter Assets/AppPrefabs/
* Ziehen Sie **das Prefab ObjectSpawner** in den **Bereich Hierarchie.**
* Klicken Sie im Bereich  Hierarchie auf **ObjektSpawner.**
* **ObjectSpawner verfügt** über ein Feld mit dem Namen **Color Source**.
* Ziehen Sie **im Bereich** Hierarchie den **ColorPickerWheel-Verweis** in dieses Feld.

    ![Objekt-Spawner-Inspektor](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* Klicken Sie im Bereich Hierarchie auf das Prefab **ObjectSpawner.** 
* Doppelklicken Sie **im Inspektorbereich** auf **ObjectSpawner** Script, um den Code in der Visual Studio.

**ObjectSpawner-Skript**

Der **ObjectSpawner** instanziiert Kopien eines primitiven Gittermodells (Würfel, Kugel, Zylinder) in den Raum. Wenn eine **InteractionSourcePressed** erkannt wird, wird die Übergabe überprüft, und es handelt sich um ein **InteractionSourcePressType.Grasp-** oder **InteractionSourcePressType.Select-Ereignis.**

Bei einem **Greifereignis** wird der Index des aktuellen Gittertyps (Kugel, Würfel, Zylinder) inkrementiert.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

Für ein **Select-Ereignis** wird in **SpawnObject()** ein neues -Objekt instanziiert, ohne übergeordnetes Element und in der Welt freigegeben.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

Das **ObjectSpawner-Objekt** verwendet **colorPickerWheel,** um die Farbe des Materials des Anzeigeobjekts fest zu legen. Spawned-Objekte erhalten eine Instanz dieses Materials, damit sie ihre Farbe beibehalten.

* **Speichern Sie** die Szene, und klicken Sie **auf die Wiedergabeschaltfläche.**

Sie können die Objekte mit der Schaltfläche Greiftaste ändern und Objekte mit der Schaltfläche Auswählen erstellen.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Erstellen und Bereitstellen einer App Mixed Reality-Portal

* Wählen Sie in Unity **Datei > Build Einstellungen.**
* Klicken **Sie auf Open Scenes hinzufügen,** um die aktuelle Szene zu Scenes In Build **hinzuzufügen.**
* Klicken Sie auf **Erstellen**.
* Erstellen Sie **einen neuen Ordner** mit dem Namen "App".
* Klicken Sie mit nur einem Klick **auf den Ordner App.**
* Klicken Sie auf **Ordner auswählen**.
* Wenn Unity fertig ist, wird ein Datei-Explorer-Fenster angezeigt.
* Öffnen Sie den **Ordner App.**
* Doppelklicken **Sie auf YourSceneName.sln** Visual Studio Projektmappendatei.
* Ändern Sie in der oberen Symbolleiste Visual Studio Ziel von Debuggen in **Release** und von ARM in **X64.**
* Klicken Sie auf den Dropdownpfeil neben der Schaltfläche Gerät, und wählen Sie **Lokaler Computer aus.**
* Klicken **Sie im Menü > Auf Debuggen** -> Starten ohne Debuggen, oder drücken Sie **STRG+F5.**

Nun wird die App erstellt und in der Mixed Reality-Portal. Sie können sie erneut starten, Startmenü in Mixed Reality-Portal.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Erweiterter Entwurf– Pinseltools mit radialem Layout

![MixedReality213 Main](images/mr213-main-600px.jpg)

In diesem Kapitel erfahren Sie, wie Sie das Standardmäßige Motion Controller-Modell durch eine benutzerdefinierte Pinseltoolsammlung ersetzen. Als Referenz finden Sie die fertige **MixedReality213Advanced-Szene im** **Ordner Scenes.**

### <a name="instructions"></a>Anweisungen

* Geben Sie **Project** im Suchfeld **BrushSelector** in das Suchfeld ein. Sie finden sie auch unter Assets/AppPrefabs/
* Ziehen Sie **das BrushSelector-Prefab** in den **Hierarchiebereich.**
* Erstellen Sie für die Organisation ein leeres GameObject namens **Brushes.**
* Ziehen Sie die folgenden Prefabs **aus** dem Project in **Pinsel.**
    * Assets/AppPrefabs/BrushFat
    * Assets/AppPrefabs/BrushThin
    * Assets/AppPrefabs/Eraser
    * Assets/AppPrefabs/MarkerFat
    * Assets/AppPrefabs/MarkerThin
    * Assets/AppPrefabs/Pencil

    ![Pinsel](images/mixedreality213-brushes-250px.png)

* Klicken Sie im Bereich Hierarchie auf **MotionControllers-Prefab.** 
* Deaktivieren Sie **im Bereich Inspector** in der Motion Controller Visualizer die Option Immer **alternatives** rechtes Modell **verwenden.**
* Klicken Sie **im Hierarchiebereich** auf **BrushSelector.**
* **BrushSelector verfügt** über ein Feld namens **ColorPicker.**
* Ziehen Sie **im Bereich** Hierarchie das **ColorPickerWheel-Steuerelement** in **das Feld ColorPicker** im **Inspektorbereich.**

    ![Zuweisen von ColorPickerWheel zum Pinselauswahl](images/mr213-brushselector-500px.jpg)

* Wählen Sie **im Bereich** Hierarchie unter **BrushSelector** prefab das **Objekt Menu** aus.
* Öffnen Sie **im Bereich Inspector** unter der **LineObjectCollection-Komponente** die Dropdownliste Objects array **(Objekte).** Es werden 6 leere Slots sehen.
* Ziehen Sie **im Hierarchiebereich** alle prefabs, die dem **Brushes** GameObject übergeordnet sind, in beliebiger Reihenfolge in diese Slots. (Stellen Sie sicher, dass Sie die Prefabs aus der Szene ziehen, nicht die Prefabs im Projektordner.)

![Pinselauswahl](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector-Prefab**

 Da **brushSelector** **AttachToController** erbt, werden im Inspektorbereich **die Optionen Handlichkeit** und **Element** angezeigt. Wir haben **Rechts und** **Zeigende Pose** ausgewählt, um Pinseltools mit Vorwärtsrichtung an den rechten Controller anfügen zu können.

**BrushSelector** verwendet zwei Hilfsprogramme:

* **Ellipse:** Wird verwendet, um Punkte im Raum entlang einer Ellipseform zu generieren.
* **LineObjectCollection:** Verteilt Objekte mithilfe der Punkte, die von einer beliebigen Line-Klasse (z. B. Ellipse) generiert werden. Dies verwenden wir, um unsere Pinsel entlang der Ellipse-Form zu platzieren.

In Kombination können diese Hilfsprogramme verwendet werden, um ein radiales Menü zu erstellen.

**LineObjectCollection-Skript**

**LineObjectCollection** verfügt über Steuerelemente für die Größe, Position und Drehung von Objekten, die entlang ihrer Linie verteilt sind. Dies ist nützlich, um radiale Menüs wie die Pinselauswahl zu erstellen. Um die Darstellung von Pinseln zu erstellen, die von nichts hochskaliert werden, während sie sich der ausgewählten Mittelpunktposition nähern, wird die **ObjectScale-Kurve** in der Mitte spitzen und an den Rändern abgeknippt.

**BrushSelector-Skript**

Im Fall von **BrushSelector** haben wir uns für die Verwendung prozeduraler Animationen entschieden. Erstens werden Pinselmodelle durch das LineObjectCollection-Skript in einer **Ellipse** verteilt. Anschließend ist jeder Pinsel dafür verantwortlich, seine Position in der Hand des Benutzers basierend auf seinem **DisplayMode-Wert** zu erhalten, der sich basierend auf der Auswahl ändert. Wir haben einen prozeduralen Ansatz gewählt, da die Wahrscheinlichkeit hoch ist, dass Pinselpositionsübergänge unterbrochen werden, wenn der Benutzer Pinsel auswählt. Mecanim-Animationen können Unterbrechungen ordnungsgemäß behandeln, sind aber in der Regel komplizierter als ein einfacher Lerp-Vorgang.

**BrushSelector** verwendet eine Kombination aus beidem. Wenn Touchpadeingaben erkannt werden, werden Pinseloptionen sichtbar und werden über das radiale Menü zentral hochskaliert. Nach einem Timeoutzeitraum (der angibt, dass der Benutzer eine Auswahl getroffen hat) werden die Pinseloptionen erneut herunterskaliert, und es wird nur der ausgewählte Pinsel belässt.

**Visualisieren von Touchpadeingaben**

Auch in Fällen, in denen das Controllermodell vollständig ersetzt wurde, kann es hilfreich sein, Eingaben für die ursprünglichen Modelleingaben zu zeigen. Dies hilft, die Aktionen des Benutzers in der Praxis zu erdingen. Für **brushSelector haben** wir uns dafür entschieden, das Touchpad kurz sichtbar zu machen, wenn die Eingabe empfangen wird. Dazu wurde das Touchpad-Element vom Controller abgerufen, das Material durch ein benutzerdefiniertes Material ersetzt und dann ein Farbverlauf auf die Farbe dieses Materials basierend auf dem letzten Empfang der Touchpadeingaben anwenden.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**Pinseltoolauswahl mit Touchpadeingabe**

Wenn der Pinsel-Selektor die gedrückte Eingabe des Touchpads erkennt, überprüft er die Position der Eingabe, um zu ermitteln, ob sie links oder rechts liegt.

**Strichstärke mit selectPressedAmount**

Anstelle des **InteractionSourcePressType.Select-Ereignisses** in **der InteractionSourcePressed()** können Sie den analogen Wert des gedrückten Betrags über **selectPressedAmount erhalten.** Dieser Wert kann in **InteractionSourceUpdated() abgerufen werden.**

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**Radiererskript**

**Eraser** ist ein spezieller Pinseltyp, der die DrawOverTime()-Basisfunktion des **Pinsels überschreibt.** Während Draw true ist, überprüft der Radierer, ob sich seine Spitze mit vorhandenen Pinselstrichen überschneidet. Wenn dies der Wert ist, werden sie einer Warteschlange hinzugefügt, um sie zu verkleinern und zu löschen.

## <a name="advanced-design---teleportation-and-locomotion"></a>Erweiterter Entwurf – Teleportation und Fortbewegung

Wenn Sie es dem Benutzer ermöglichen möchten, sich mit teleportation mit dem Thumbstick in der Szene zu bewegen, verwenden Sie **MixedRealityCameraParent** anstelle **von MixedRealityCamera**. Sie müssen auch **InputManager und** **DefaultCursor hinzufügen.** Da **MixedRealityCameraParent** **motionControllers** und **Boundary** bereits als untergeordnete Komponenten enthält, sollten Sie vorhandene **MotionControllers** und **Environment-Prefab** entfernen.

### <a name="instructions"></a>Anweisungen

* Löschen Sie **im Hierarchiebereich** **MixedRealityCamera,** **Environment** und **MotionControllers.**
* Suchen Sie **Project Bereich ,** und ziehen Sie die folgenden Prefabs in den **Hierarchiebereich:**
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

    ![Mixed Reality-Kamera übergeordnetes Element](images/mr213-cameraparent-300px.png)

* Klicken Sie **im Bereich** Hierarchie auf **Eingabe-Manager.**
* Scrollen Sie **im Inspektorbereich** nach unten zum Abschnitt Simple Single Pointer Selector (Einfache **Einzelzeigerauswahl).**
* Ziehen Sie **defaultCursor** aus dem Hierarchiebereich in das **Cursorfeld.** 

    ![Zuweisen von DefaultCursor](images/mr213-defaultcursor-500px.png)

* **Speichern Sie** die Szene, und klicken Sie **auf die Wiedergabeschaltfläche.** Sie können den Thumbstick verwenden, um nach links/rechts zu drehen oder einen Teleport zu verwenden.

## <a name="the-end"></a>Das Ende

Und das ist das Ende dieses Tutorials! Sie haben Folgendes gelernt:

* Arbeiten mit Motion Controller-Modellen im Spielmodus und zur Laufzeit von Unity
* Verwenden verschiedener Arten von Schaltflächenereignissen und deren Anwendungen.
* Hier erfahren Sie, wie Sie Benutzeroberflächenelemente über dem Controller überlagern oder vollständig anpassen.

Sie können jetzt damit beginnen, Ihre eigene immersive Erfahrung mit Motion-Controllern zu erstellen!

## <a name="completed-scenes"></a>Abgeschlossene Szenen

* Klicken Sie im **Unity Project bereich** auf den Ordner **Szenen.**
* Sie finden zwei Unity-Szenen **MixedReality213 und** **MixedReality213Erfüllt.**
    * **MixedReality213:** Abgeschlossene Szene mit einzelnem Pinsel
    * **MixedReality213Erfüllt:** Abgeschlossene Szene mit mehreren Pinseln mit dem Beispiel zum Drücken der Schaltfläche "Press Amount" (Menge drücken)

## <a name="see-also"></a>Siehe auch

* [MR Input 213-Projektdateien](https://github.com/Microsoft/MixedReality213)
* [Mixed Reality Toolkit – Motion Controller Test-Szene](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Mixed Reality Toolkit – Greifmechanismen](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Entwicklungsrichtlinien für Motion Controller](../design/motion-controllers.md)