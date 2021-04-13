---
title: Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie Ihr Unity-Projekt für das Mixed Reality Toolkit (MRTK) konfigurieren und es in Ihrer HoloLens 2 bereitstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: c9cf580b1123002e9e8cdfd5c3914c3aa39e2825
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003129"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung

In diesem Tutorial erfahren Sie, wie Sie ein neues Unity-Projekt erstellen, es für die Entwicklung mit dem <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> konfigurieren und das MRTK importieren. Außerdem werden Sie durch Konfiguration, Erstellung und Bereitstellung einer einfachen Unity-Szene aus Visual Studio auf Ihrer HoloLens 2 geführt. Nachdem Sie diese auf Ihrer HoloLens 2 bereitgestellt haben, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a>Ziele

* Erfahren, wie Unity für die HoloLens-Entwicklung konfiguriert wird
* Erfahren, wie Ihre App erstellt und in HoloLens bereitgestellt wird
* Kennenlernen des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers auf dem HoloLens 2-Gerät

## <a name="creating-the-unity-project"></a>Erstellen des Unity-Projekts

Starten Sie **Unity Hub**, wählen Sie die Registerkarte **Projects** (Projekte) aus, und klicken Sie auf den **Abwärtspfeil** neben der Schaltfläche **New** (Neu):

![Unity-Hub mit hervorgehobener Schaltfläche „New“](images/mr-learning-base/base-02-section1-step1-1.png)

Wählen Sie in der Dropdownliste die Unity-**Version** aus, die oben in den [Voraussetzungen](mr-learning-base-01.md#prerequisites) angegeben ist:

![Unity-Hub mit Versionsauswahl-Dropdown „NEW“](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Wenn diese bestimmte Unity-Version nicht auf dem Unity Hub verfügbar ist, können Sie die Installation aus dem <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Downloadarchiv</a> von Unity einleiten.

Erstellen Sie im Fenster ein neues Projekt:

* Vergewissern Sie sich, dass **Templates** (Vorlagen) auf **3D** festgelegt ist
* Geben Sie einen passenden **Project Name** (Projektnamen) ein, z. B. _MRTK-Tutorials_
* Wählen Sie eine geeignete **Location** (Speicherort) zum Speichern Ihres Projekts, z. B. _D:\MixedRealityLearning_
* Klicken Sie auf die Schaltfläche **Create** (Erstellen), um das neue Unity-Projekt zu erstellen

![Unity-Hub mit ausgefülltem Fenster „Create new project“ (Neues Projekt erstellen)](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> Wenn Sie unter Windows arbeiten, müssen Sie den MAX_PATH-Grenzwert von 255 Zeichen beachten. Daher sollten Sie das Unity-Projekt in der Nähe des Stammverzeichnisses des Laufwerks speichern.

Warten Sie, bis Unity das Projekt erstellt hat:

![Unity: Erstellen eines neuen Projekts in Bearbeitung](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Wechseln der Buildplattform

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a>Importieren der TextMeshPro Essential-Ressourcen

Wählen Sie im Unity-Menü **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Fenster > TextMeshPro > TMP Essential Resources importieren) aus, um das Importfenster für Unity-Pakete zu öffnen:

![Unity: Menüpfad für „Import TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-1.png)

Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:

![Unity-Fenster für Importieren von „TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Die TextMeshPro Essential-Ressourcen sind für die Benutzeroberflächenelemente des MRTK erforderlich. Sie können diesen Schritt überspringen, wenn Sie nicht beabsichtigen, die Benutzeroberflächenelemente des MRTK in Ihrem Projekt zu verwenden.

## <a name="importing-the-mixed-reality-toolkit"></a>Importieren des Mixed Reality-Toolkits

Zum Importieren des Mixed Reality-Toolkits in das Unity-Projekt müssen Sie das [Mixed Reality-Featuretool verwenden](../welcome-to-mr-feature-tool.md), das Entwicklern das Erkennen, Aktualisieren und Hinzufügen von Mixed Reality-Featurepaketen zu Unity-Projekten ermöglicht. Sie können Pakete vor dem Importieren nach Name oder Kategorie durchsuchen, ihre Abhängigkeiten anzeigen und sogar Änderungsvorschläge für Ihre Projektmanifestdatei anzeigen.

Laden Sie die neueste Version des Mixed Reality-Featuretools aus dem [Microsoft Download Center](https://aka.ms/MRFeatureTool) herunter. Wenn der Download abgeschlossen ist, entpacken Sie die Datei, und speichern Sie sie auf Ihrem Desktop.

> [!NOTE]
> Installieren Sie [.NET 5.0 Runtime](https://dotnet.microsoft.com/download/dotnet/5.0), damit Sie das Mixed Reality-Featuretool ausführen können.

> [!NOTE]
> Das Mixed Reality-Featuretool kann zurzeit nur unter Windows ausgeführt werden. Wenn Sie MacOS verwenden, befolgen Sie diese [Vorgehensweise](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages), um das Mixed Reality-Toolkit herunterzuladen und in das Unity-Projekt zu importieren.

Öffnen Sie die ausführbare Datei **MixedRealityFeatureTool** aus dem heruntergeladenen Ordner, um das Mixed Reality-Featuretool zu starten.  

![Öffnen von MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a>Konfigurieren des Unity-Projekts

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Übernehmen der Einstellungen des MRTK-Projektkonfigurators

Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des MRTK-Projektkonfigurators angezeigt werden. Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) wechseln:

![Unity: Menüpfad für „Configure Unity Project“](images/mr-learning-base/base-02-section5-step1-1.png)

Klappen Sie im Projektkonfiguratorfenster des MRTK den Abschnitt **Modify Configurations** (Konfigurationen ändern) auf, vergewissern Sie sich, dass alle Optionen aktiviert sind, und klicken Sie auf die Schaltfläche **Apply** (Übernehmen), um die Einstellungen zu übernehmen:

![Unity MRTK-Projektkonfigurator-Fenster](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> Die Anwendung der MRTK-Standardeinstellungen ist optional, wird aber dringend empfohlen, weil es bei der Konfiguration einiger empfohlener Unity-Einstellungen hilfreich ist:

> * Legen Sie den Single Pass-instanziierten Renderingpfad fest: Verbessert die Grafikleistung, indem die Renderpipeline für beide Augen im selben Zeichnen-Aufruf ausgeführt wird. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Single Pass-instanziiertes Rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) der [Leistung](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)sdokumentation von MRTK.
> * Standardebene für Spatial Awareness (räumliche Wahrnehmung) festlegen: Erstellt eine Unity-Ebene namens „Spatial Awareness“ und konfiguriert MRTK für die Verwendung dieser Ebene für das Gittermodell für räumliche Wahrnehmung. Weitere Informationen zu Unity-Ebenen finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.

### <a name="2-configure-additional-project-settings"></a>2. Konfigurieren zusätzlicher Projekteinstellungen

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Erstellen der Szene und Konfigurieren des MRTK

Wählen Sie im Unity-Menü **File** > **New Scene** (Datei > Neue Szene) aus, um eine neue Szene zu erstellen:

![Unity: Menüpfad für „New Scene“](images/mr-learning-base/base-02-section6-step1-1.png)

Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Mixed Reality-Toolkit > Zu Szene hinzufügen und konfigurieren) aus, um Ihrer aktuellen Szene das MRTK hinzuzufügen:

![Unity: Menüpfad zu „Add to Scene and Configure...“](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

Wählen Sie im Unity-Menü **File** > **Save As...** (Datei > Speichern unter...) aus, um das Save Scene-Fenster (Szene speichern) zu öffnen:

![Unity: Menüpfad für „Save As...“](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen. Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Leistung</a>sdokumentation des MRTK.

![Unity: Aufforderungsfenster zum Speichern der Szene](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a>Importieren der Tutorialressourcen

Laden Sie das folgende benutzerdefinierte Unity-Paket herunter:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

Wählen Sie zum Importieren eines benutzerdefinierten Unity-Pakets im Unity-Menü **Assets** > **Import Package** > **Custom Package...** (Assets > Paket importieren > Benutzerdefiniertes Paket...) aus, um das Fenster zum Importieren von Paketen zu öffnen:

![Importieren eines benutzerdefinierten Pakets](images/mr-learning-base/base-02-section7-step1-1.png)

Wählen Sie im Fenster „Import package...“ (Paket importieren...) das heruntergeladene Paket **MRTK:HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** aus, und klicken Sie auf die Schaltfläche „Open“ (Öffnen):

![Auswählen eines Ressourcenpakets](images/mr-learning-base/base-02-section7-step1-2.png)

Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche All (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche Import (Importieren), um die Assets zu importieren:

![Auswählen aller zu importierenden Ressourcen](images/mr-learning-base/base-02-section7-step1-3.png)

Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:

![Unity-Projektfenster nach dem Importieren von Ressourcen](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a>Konfigurieren der Szene

Navigieren Sie im Projektfenster zum Ordner „Assets“ > „MRTK.Tutorials.GettingStarted“ > „Prefabs“:

Klicken Sie im Projektfenster auf das **Cube**-Prefab, und ziehen Sie es aus dem Projektfenster in das Hierarchiefenster. Konfigurieren Sie dann im Inspektorfenster die Komponente **Transform** (Transformieren) wie folgt:

* **Position**: X = 0, Y = 0, Z = 0,5
* **Drehung**: X = 0, Y = 0, Z = 0
* **Skalierung**: X = 1, Y = 1, Z = 1

![Hinzufügen eines Cube-Objekts zur Szene](images/mr-learning-base/base-02-section8-step1-1.png)

Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **Cube**-Objekt doppelklicken und die Ansicht dann etwas vergrößern:

Zum Interagieren und zum Greifen eines Objekts mit Handtracking muss das Objekt über eine Collider-Komponente (etwa eine Komponente vom Typ **Box Collider** (Feld-Collider)), eine Komponente vom Typ **Object Manipulator (Script)** (Objektmanipulator (Skript)) und eine **NearInteractionGrabbable(Script)** -Komponente verfügen.

Klicken Sie bei im Hierarchiefenster ausgewähltem **Cube**-Objekt im Inspektorfenster auf die Schaltfläche **Komponente hinzufügen**, suchen Sie nach dem Skript **Objektmanipulator**, und wählen Sie es aus, um das Objektmanipulatorskript dem Cube-Objekt hinzuzufügen.

![Hinzufügen des Objektmanipulators zum Cube](images/mr-learning-base/base-02-section8-step1-2.png)

Wiederholen Sie diesen Vorgang, um dem Cube eine Komponente vom Typ **Near Interaction Grabbable (Script)** (Nah-Interaktion, berührbar (Skript)) hinzuzufügen.

![Hinzufügen von „Near Interaction Grabbable (Script)“ (Nah-Interaktion, berührbar (Skript)) zum Cube](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> Wenn Sie einen Objektmanipulator (Skript) hinzufügen, wird in diesem Fall der Einschränkungs-Manager (Skript) automatisch hinzugefügt, weil der Objektmanipulator (Skript) davon abhängt.

> [!NOTE]
> Im Rahmen dieses Tutorials wurden dem Cube-Objekt bereits Collider hinzugefügt. Weitere Informationen zu Collidern finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collidern</a>.

Zum Testen im Unity-Editor können Sie in den Spielmodus wechseln und die **LeftShift**-Taste oder die **Leertaste** gedrückt halten, um den Controller zu aktivieren. Durch die Mausbewegung wird der Controller bewegt, und mithilfe des Mausrads ist zudem eine Bewegung weiter weg von der Kamera bzw. näher hin zur Kamera möglich. Wenn sich der Zeiger auf dem Cube befindet, halten Sie die **rechte Maustaste** gedrückt, um das Cube-Objekt zu verschieben.

![Spielmodus](images/mr-learning-base/base-02-section8-step1-4.png)

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
>Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **Toggle Diagnostics** (Diagnose ein-/ausschalten) ein- und ausblenden. Es empfiehlt sich, während der Entwicklung den Profiler die meiste Zeit anzuzeigen, um zu verstehen, wann Änderungen an der App die Leistung beeinträchtigen können. Beispielsweise sollten HoloLens-Apps [durchgängig bei 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ausgeführt werden.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben jetzt Ihre erste HoloLens-App bereitgestellt. Nach dem Öffnen der App sollte vor Ihnen ein Cube-Objekt angezeigt werden. Sie sollten durch Verschieben mit dem Cube interagieren können, und beim Herumlaufen sollte ein Gittermodell für die Raumzuordnung angezeigt werden, das die von HoloLens erkannten Oberflächen bedeckt. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen. Diese Features sind nur einige der grundlegenden Bestandteile von MRTK. In den bevorstehenden Tutorials fügen Sie Ihrer Szene Inhalte hinzu, um die Funktionen von HoloLens und des MRTK kennenzulernen.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 3. Konfigurieren der MRTK-Profile](mr-learning-base-03.md)
