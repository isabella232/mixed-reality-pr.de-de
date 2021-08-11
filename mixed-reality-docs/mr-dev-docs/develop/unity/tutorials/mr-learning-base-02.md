---
title: Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie Ihr Unity-Projekt für das Mixed Reality Toolkit (MRTK) konfigurieren und es in Ihrer HoloLens 2 bereitstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: cab10789bc7ab86a4090a0db46e5445b728c7c8ad2dd904cba530e81f1bab18e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201259"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung

In diesem Tutorial erfahren Sie, wie Sie ein neues Unity-Projekt erstellen, es für die Entwicklung mit dem Mixed Reality Toolkit (MRTK) konfigurieren und das MRTK importieren. Außerdem werden Sie durch Konfiguration, Erstellung und Bereitstellung einer einfachen Unity-Szene aus Visual Studio auf Ihrer HoloLens 2 geführt. Nachdem Sie diese auf Ihrer HoloLens 2 bereitgestellt haben, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.

## <a name="objectives"></a>Ziele

* Erfahren, wie Unity für die HoloLens-Entwicklung konfiguriert wird
* Erfahren, wie Ihre App erstellt und in HoloLens bereitgestellt wird
* Kennenlernen des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers auf dem HoloLens 2-Gerät

### <a name="steps-overview"></a>Übersicht der Schritte
:::row:::
    :::column:::
       ![Übersicht Schritt 1](images/mr-learning-base/base-02-overview-step1.png) **1. Erstellen eines neuen Unity-Projekts**
    :::column-end:::
    :::column:::
       ![Übersicht Schritt 2](images/mr-learning-base/base-02-overview-step2.png) **2. Importieren des MRTK in das Projekt**
    :::column-end:::
    :::column:::
       ![Übersicht Schritt 3](images/mr-learning-base/base-02-overview-step3.png) **3. Konfigurieren einer neuen Szene mit MRTK**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       ![Übersicht Schritt 4](images/mr-learning-base/base-02-overview-step4.png) **4. Erstellen des Unity-Projekts**
    :::column-end:::
    :::column:::
       ![Übersicht Schritt 5](images/mr-learning-base/base-02-overview-step5.png) **5. Erstellen des UWP-Projekts**
    :::column-end:::
    :::column:::
       ![Übersicht Schritt 6](images/mr-learning-base/base-02-overview-step6.png) **6. Ausführen des Projekts auf dem Gerät**
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a>Erstellen des Unity-Projekts

Starten Sie **Unity Hub**, wählen Sie die Registerkarte **Projects** (Projekte) aus, und klicken Sie auf den **Abwärtspfeil** neben der Schaltfläche **New** (Neu):

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

Wählen Sie in der Dropdownliste die Unity-**Version** aus, die oben in den [Voraussetzungen](mr-learning-base-01.md#prerequisites) angegeben ist:

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> Wenn diese bestimmte Unity-Version nicht auf dem Unity Hub verfügbar ist, können Sie die Installation aus dem <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Downloadarchiv</a> von Unity einleiten.

Erstellen Sie im Fenster ein neues Projekt:

* Vergewissern Sie sich, dass **Templates** (Vorlagen) auf **3D** festgelegt ist
* Geben Sie einen passenden **Project Name** (Projektnamen) ein, z. B. _MRTK-Tutorials_
* Wählen Sie eine geeignete **Location** (Speicherort) zum Speichern Ihres Projekts, z. B. _D:\MixedRealityLearning_
* Klicken Sie auf die Schaltfläche **Create** (Erstellen), um das neue Unity-Projekt zu erstellen

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> Wenn Sie unter Windows arbeiten, müssen Sie den MAX_PATH-Grenzwert von 255 Zeichen beachten. Daher sollten Sie das Unity-Projekt in der Nähe des Stammverzeichnisses des Laufwerks speichern.

Warten Sie, bis Unity das Projekt erstellt hat:

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a>Wechseln der Buildplattform

Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen:

![Unity: Build Settings... Menüpfad](images/mr-learning-base/base-02-section2-step1-1.png)

Wählen Sie im Build Settings-Fenster **Universelle Windows-Plattform** aus, und:

1. Legen Sie **Zielgerät** auf **HoloLens** fest
2. Legen Sie **Architektur** auf **ARM 64** fest 
3. Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.
4. Legen Sie **SDK-Zielversion** auf **Zuletzt installiert** fest
5. Legen Sie **Mindestplattformversion** auf **10.0.1024.0** fest
6. Legen Sie **Visual Studio-Version** auf **Zuletzt installiert** fest
7. Legen Sie **Build and Run on** (Erstellen und Ausführen auf) auf **USB-Gerät** fest
8. Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.
9. Klicken Sie auf die Schaltfläche „Plattform wechseln“.

![Unity-Buildeinstellungen mit festgelegten Einstellungen für die Universelle Windows-Plattform](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

Warten Sie, bis Unity den Wechsel der Plattform abgeschlossen hat:

![Unity: Wechsel der Plattform in Bearbeitung](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das **x**-Symbol, um das Fenster mit den Buildeinstellungen zu schließen.

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a>Importieren des Mixed Reality Toolkits und Konfigurieren des Unity-Projekts

Zum Importieren des Mixed Reality-Toolkits in das Unity-Projekt müssen Sie das [Mixed Reality-Featuretool verwenden](../welcome-to-mr-feature-tool.md), das Entwicklern das Erkennen, Aktualisieren und Hinzufügen von Mixed Reality-Featurepaketen zu Unity-Projekten ermöglicht. Sie können Pakete vor dem Importieren nach Name oder Kategorie durchsuchen, ihre Abhängigkeiten anzeigen und sogar Änderungsvorschläge für Ihre Projektmanifestdatei anzeigen.

Laden Sie die neueste Version des Mixed Reality-Featuretools aus dem [Microsoft Download Center](https://aka.ms/MRFeatureTool) herunter. Wenn der Download abgeschlossen ist, entpacken Sie die Datei, und speichern Sie sie auf Ihrem Desktop.

> [!NOTE]
> Installieren Sie [.NET 5.0 Runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer), damit Sie das Mixed Reality-Featuretool ausführen können.

Öffnen Sie die ausführbare Datei **MixedRealityFeatureTool** aus dem heruntergeladenen Ordner, um das Mixed Reality-Featuretool zu starten.  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Erstellen der Szene und Konfigurieren des MRTK

Wählen Sie im Unity-Menü **Datei** > **Neue Szene** aus:

![Unity: Menüpfad für „New Scene“](images/mr-learning-base/base-02-section6-step1-1.png)

Wählen Sie im Fenster **Neue Szene** die Option **Basic (integriert)** aus, und klicken Sie auf **Erstellen**, um eine neue Szene zu erstellen:

![Unity-Fenster „Neue Szene“](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> Der obige Screenshot stammt aus Unity, Version 2020. Wenn Sie Unity 2019 verwenden und auf **Erstellen** klicken, wird eine neue leere Szene erstellt.

Wählen Sie im Unity-Menü **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** (Mixed Reality > Toolkit > Zu Szene hinzufügen und konfigurieren) aus, um Ihrer aktuellen Szene das MRTK hinzuzufügen:

![Unity: Menüpfad zu „Add to Scene and Configure...“](images/mr-learning-base/base-02-section6-step1-2.png)

Überprüfen Sie bei im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster, ob das Konfigurationsprofil des **Mixed Reality-Toolkits** auf **DefaultMixedRealityToolkitConfigurationProfile** festgelegt ist:

![MixedRealityToolkit-Komponente von Unity mit ausgewähltem DefaultMixedRealityTookitConfigurationProfile](images/mr-learning-base/base-02-section6-step1-3.png)

Wählen Sie im Unity-Menü **File** > **Save As...** (Datei > Speichern unter...) aus, um das Save Scene-Fenster (Szene speichern) zu öffnen:

![Unity: Menüpfad für „Save As...“](images/mr-learning-base/base-02-section6-step1-4.png)

Speichern Sie die Szene in Ihrem Projekt unter **Asset** > **Scenes** (Ressourcen > Szenen).

![Unity: Aufforderungsfenster zum Speichern der Szene](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a>Hinzufügen von Handinteraktion zu einem Objekt

Wählen Sie im Unity-Menü **GameObject** > **3D Object** > **Cube** aus, um der Szene ein Cube-Objekt hinzuzufügen.

![Hinzufügen eines Cube-Objekts zur Szene](images/mr-learning-base/base-02-section8-step1-1.png)

Klicken Sie im Hierarchiefenster auf das **Cube**-Objekt, und konfigurieren Sie dann im Inspektorfenster die **Transform**-Komponente (Transformation) wie folgt.

* **Position**: X = 0, Y = -0.1, Z = 0.5
* **Drehung**: X = 0, Y = 0, Z = 0
* **Skalierung:** X = 0.1, Y = 0.1, Z = 0.1

1 Unity-Einheit ist 1 Meter. Wir haben die Größe des Cubes auf 10x10x10 cm aktualisiert und 50 cm von der Headsetposition (0,0,0) entfernt platziert. 10 cm unterhalb der Augenhöhe für eine komfortable Interaktion. 

Wenn Sie die Standardskala (1,1,1) verwenden, ist der Cube zu groß. Wenn Sie die Standardposition (0,0,0) verwenden, wird der Cube an derselben Position wie Ihr Headset platziert, und Sie können ihn erst sehen, wenn Sie sich rückwärts bewegen.

![Anpassen von Transformationsinformationen](images/mr-learning-base/base-02-section8-step1-1b.png)

Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **Cube**-Objekt doppelklicken und die Ansicht dann wieder etwas vergrößern. Oder Sie können die F-Taste verwenden, um das Objekt zu vergrößern und sich darauf zu konzentrieren.

Um mit verfolgten Händen mit einem Objekt zu interagieren und es zu greifen, muss das Objekt folgende Komponenten aufweisen:
 * Collider-Komponente wie **Box Collider** (der Cube von Unity verfügt bereits standardmäßig über einen Box Collider)
 * **Object Manipulator (Script)** -Komponente
 * **NearInteractionGrabbable(Script)-Komponente**

Durch das **ObjectManipulator**-Skript des MRTK wird ein Objekt mit einer oder zwei Händen verschiebbar, skalierbar und drehbar. Dieses Skript unterstützt das Eingabemodell der direkten Manipulation, da das Skript dem Benutzer die Möglichkeit gibt, Hologramme direkt mit den Händen zu berühren.

Klicken Sie bei im Hierarchiefenster ausgewähltem **Cube**-Objekt im Inspektorfenster auf die Schaltfläche **Komponente hinzufügen**, suchen Sie nach dem Skript **Objektmanipulator**, und wählen Sie es aus, um das Objektmanipulatorskript dem Cube-Objekt hinzuzufügen.

![Hinzufügen des Objektmanipulators zum Cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

Wiederholen Sie diesen Vorgang, um dem Cube eine Komponente vom Typ **Near Interaction Grabbable (Script)** (Nah-Interaktion, berührbar (Skript)) hinzuzufügen.

![Hinzufügen von „Near Interaction Grabbable (Script)“ (Nah-Interaktion, berührbar (Skript)) zum Cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> Wenn Sie einen Objektmanipulator (Skript) hinzufügen, wird in diesem Fall der Einschränkungs-Manager (Skript) automatisch hinzugefügt, weil der Objektmanipulator (Skript) davon abhängt.

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a>Testen Ihrer Anwendung im Unity-Editor mit MRTK-Eingabesimulation

Mit der Eingabesimulation des MRTK können Sie verschiedene Arten von Interaktionen im Unity-Editor testen, ohne erstellen und auf einem Gerät bereitstellen zu müssen. Auf diese Weise können Sie Ihre Ideen im Entwurfs- und Entwicklungsprozess schnell iterieren. Verwenden Sie Kombinationen aus Tastatur- und Mauseingaben, um simulierte Eingaben zu steuern.

Klicken Sie auf die Schaltfläche „Wiedergeben“, und wechseln Sie in den Wiedergabemodus. Halten Sie die **linke UMSCHALTTASTE** oder die **LEERTASTE** gedrückt, um den Controller (simulierte Hände) aufzurufen. Der Controller lässt sich per Mausbewegung bewegen, und er kann mit dem Mausrad weiter von der Kamera weg oder näher zur Kamera hin bewegt werden. Wenn sich der Zeiger auf dem Cube befindet, halten Sie die **linke Maustaste** gedrückt, um das Cube-Objekt zu greifen.

* Drücken Sie die Tasten **W, A, S, D, Q, E**, um die Kamera zu bewegen.
* Halten Sie die **rechte Maustaste** gedrückt, und bewegen Sie die Maus, um sich umzusehen.
* Um die simulierten Hände aufzurufen, drücken Sie die **LEERTASTE (rechte Hand)** oder die **linke UMSCHALTTASTE (linke Hand)** .
* Um die simulierten Hände im Blickfeld zu halten, drücken Sie die Taste **T** oder **Y**.
* Um simulierte Hände zu drehen, drücken und halten Sie die **STRG**-TASTE gedrückt, und bewegen Sie die Maus.

![Spielmodus](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a>Erstellen Ihrer Anwendung auf der HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Erstellen des Unity-Projekts

Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen.

Klicken Sie im Build Settings-Fenster (Buildeinstellungen) auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um der Liste **Scenes In Build** (Szenen im Build) Ihre aktuelle Szene hinzuzufügen, und klicken Sie dann auf die Schaltfläche **Build** (Erstellen), um das Build Universal Windows Platform-Fenster (Erstellen für Universelle Windows-Plattform) zu öffnen:

![Unity-Fenster „Build Settings“ mit ausgewählter UWP](images/mr-learning-base/base-02-section9-step1-1.png)

Wählen Sie im Build Universal Windows Platform-Fenster einen passenden Speicherort aus, um Ihren Build zu speichern, beispielsweise _D:\MixedRealityLearning\Builds_, erstellen Sie einen neuen Ordner mit einem passenden Namen, z. B. _GettingStarted_, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Auswählen eines Ordners](images/mr-learning-base/base-02-section9-step1-2.png)

Warten Sie, bis Unity den Buildvorgang abgeschlossen hat:

![Unity: Buildvorgang wird ausgeführt](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Erstellen und Bereitstellen der Anwendung

Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben. Navigieren Sie zum Ordner, und doppelklicken Sie auf die Projektmappendatei, um sie in Visual Studio zu öffnen:

![Windows-Explorer mit neu erstellter, ausgewählter Visual Studio-Projektmappe](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation **[Installieren der Tools](../../install-the-tools.md)** angegeben) installiert sind.

Konfigurieren Sie Visual Studio für HoloLens 2, indem Sie die **Master**- oder **Release**-Konfiguration, die **ARM64**-Architektur und **Gerät** als Ziel auswählen:

![Visual Studio, konfiguriert für die Bereitstellung in HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> Wenn Sie auf HoloLens (1. Generation) bereitstellen, wählen Sie die **x86**-Architektur aus.

> [!NOTE]
> Für HoloLens erstellen Sie normalerweise für die ARM-Architektur. Jedoch besteht ein <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>bekanntes Problem</strong></a> in Unity 2019.3, das zu Fehlern führt, wenn ARM in Visual Studio als Buildarchitektur ausgewählt wird. Die empfohlene Umgehung besteht darin, Builds für ARM64 zu erstellen. Wenn diese Option nicht in Frage kommt, navigieren Sie zu **Edit > Project Settings > Player > Other Settings** (Bearbeiten > Projekteinstellungen > Player > Weitere Einstellungen), und deaktivieren Sie **Graphics Jobs** (Grafikaufträge).

> [!NOTE]
> Wenn „Device“ (Gerät) nicht als Zieloption angezeigt wird, müssen Sie möglicherweise das Startprojekt für die Visual Studio-Projektmappe vom Projekt „IL2CPP“ zum Projekt „UWP“ ändern. Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf den Namen Ihres Projekts (Universal Windows), und wählen Sie **Set as StartUp Project** (Als Startprojekt festlegen) aus.

Verbinden Sie Ihre HoloLens mit Ihrem Computer, wählen Sie dann **Debug** > **Start Without Debugging** (Debuggen > Ohne Debuggen starten) aus, um zu erstellen und auf Ihrem Gerät bereitzustellen:

![Visual Studio-Menüpfad für „Ohne Debuggen starten“](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> Bevor Sie den Build für Ihr Gerät erstellen, muss das Gerät in den Entwicklermodus versetzt und mit Ihrem Entwicklungscomputer gekoppelt werden. Sie können beide Schritte ausführen, indem Sie [diese Anweisungen](../../platform-capabilities-and-apis/using-visual-studio.md) befolgen.

> [!TIP]
> Sie können auch auf dem [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) bereitstellen oder ein [App-Paket](/windows/uwp/packaging/packaging-uwp-apps) zum Querladen erstellen.

Bei der Option „Start Without Debugging“ (Ohne Debuggen starten) wird die App auf Ihrem Gerät automatisch ohne angefügten Visual Studio-Debugger gestartet.

Wählen Sie **Build > Deploy Solution** (Erstellen > Projektmappe bereitstellen) aus, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.

> [!NOTE]
>Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **„Toggle Diagnostics“** (Diagnose umschalten) ein- und ausblenden. Es empfiehlt sich, während der Entwicklung den Profiler die meiste Zeit anzuzeigen, um zu verstehen, wann Änderungen an der App die Leistung beeinträchtigen können. Beispielsweise sollten HoloLens-Apps [durchgängig bei 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ausgeführt werden.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben jetzt Ihre erste HoloLens-App bereitgestellt. Nach dem Öffnen der App sollte vor Ihnen ein Cube-Objekt angezeigt werden. Sie sollten durch Verschieben mit dem Cube interagieren können, und beim Herumlaufen sollte ein Gittermodell für die Raumzuordnung angezeigt werden, das die von HoloLens erkannten Oberflächen bedeckt. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen. Diese Features sind nur einige der grundlegenden Bestandteile von MRTK. In den bevorstehenden Tutorials fügen Sie Ihrer Szene Inhalte hinzu, um die Funktionen von HoloLens und des MRTK kennenzulernen.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 3. Konfigurieren der MRTK-Profile](mr-learning-base-03.md)
