---
title: Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie Ihr Unity-Projekt für das Mixed Reality Toolkit (MRTK) konfigurieren und es in Ihrer HoloLens 2 bereitstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 4d82d0974a0a797e7f8d2de2d4943666f7d32a4f
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635502"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung

In diesem Tutorial erfahren Sie, wie Sie ein neues Unity-Projekt erstellen, es für die Entwicklung mit dem <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> konfigurieren und das MRTK importieren. Außerdem werden Sie durch Konfiguration, Erstellung und Bereitstellung einer einfachen Unity-Szene aus Visual Studio auf Ihrer HoloLens 2 geführt. Nachdem Sie diese auf Ihrer HoloLens 2 bereitgestellt haben, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.

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

Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen:

![Unity: Build Settings... Menüpfad](images/mr-learning-base/base-02-section2-step1-1.png)

Wählen Sie im Build Settings-Fenster **Universal Windows Platform** (Universelle Windows-Plattform) aus, und klicken Sie auf die Schaltfläche **Switch Platform** (Plattform wechseln):

![Unity-Fenster „Build Settings“ mit ausgewählter UWP, um von der Plattform „Eigenständig“ zu wechseln](images/mr-learning-base/base-02-section2-step1-2.png)

Warten Sie, bis Unity den Wechsel der Plattform abgeschlossen hat:

![Unity: Wechsel der Plattform in Bearbeitung](images/mr-learning-base/base-02-section2-step1-3.png)

Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das rote **x**-Symbol, um das Build Settings-Fenster zu schließen:

![Unity-Fenster „Build“ mit hervorgehobenem Symbol zum Schließen](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>Importieren der TextMeshPro Essential-Ressourcen

Wählen Sie im Unity-Menü **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Fenster > TextMeshPro > TMP Essential Resources importieren) aus, um das Importfenster für Unity-Pakete zu öffnen:

![Unity: Menüpfad für „Import TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-1.png)

Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:

![Unity-Fenster für Importieren von „TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Die TextMeshPro Essential-Ressourcen sind für die Benutzeroberflächenelemente des MRTK erforderlich. Sie können diesen Schritt überspringen, wenn Sie nicht beabsichtigen, die Benutzeroberflächenelemente des MRTK in Ihrem Projekt zu verwenden.

## <a name="importing-the-mixed-reality-toolkit"></a>Importieren des Mixed Reality-Toolkits

Laden Sie das benutzerdefinierte Unity-Paket herunter:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.5.1/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage)

Wählen Sie im Unity-Menü **Assets** > **Import Package** > **Custom Package...** (Assets > Paket importieren > Benutzerdefiniertes Paket...) aus, um das Fenster zum Importieren von Paketen zu öffnen:

![Unity: Benutzerdefiniertes Paket importieren... Menüpfad](images/mr-learning-base/base-02-section4-step1-1.png)

Wählen Sie im Fenster „Import package...“ (Paket importieren...) das heruntergeladene **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage**-Paket aus, und klicken Sie auf die Schaltfläche **Open** (Öffnen):

![Unity: Benutzerdefiniertes Paket importieren mit Aufforderungsfenster „Open“](images/mr-learning-base/base-02-section4-step1-2.png)

Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:

![Unity-Fenster zum Importieren von MRTK-Grundlagen](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a>Konfigurieren des Unity-Projekts

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Übernehmen der Einstellungen des MRTK-Projektkonfigurators

Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des MRTK-Projektkonfigurators angezeigt werden. Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) wechseln:

![Unity: Menüpfad für „Configure Unity Project“](images/mr-learning-base/base-02-section5-step1-1.png)

Klappen Sie im Projektkonfiguratorfenster des MRTK den Abschnitt **Modify Configurations** (Konfigurationen ändern) auf, vergewissern Sie sich, dass alle Optionen aktiviert sind, und klicken Sie auf die Schaltfläche **Apply** (Übernehmen), um die Einstellungen zu übernehmen:

![Unity MRTK-Projektkonfigurator-Fenster](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> Die Anwendung der MRTK-Standardeinstellungen ist optional, wird aber dringend empfohlen, weil es bei der Konfiguration einiger empfohlener Unity-Einstellungen hilfreich ist:

> * Legen Sie den Single Pass-instanziierten Renderingpfad fest: Verbessert die Grafikleistung, indem die Renderpipeline für beide Augen im selben Zeichnen-Aufruf ausgeführt wird. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Single Pass-instanziiertes Rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) der [Leistung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)sdokumentation von MRTK.
> * Standardebene für Spatial Awareness (räumliche Wahrnehmung) festlegen: Erstellt eine Unity-Ebene namens „Spatial Awareness“ und konfiguriert MRTK für die Verwendung dieser Ebene für das Gittermodell für räumliche Wahrnehmung. Weitere Informationen zu Unity-Ebenen finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.

### <a name="2-configure-additional-project-settings"></a>2. Konfigurieren zusätzlicher Projekteinstellungen

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:

![Unity: Project Settings... Menüpfad](images/mr-learning-base/base-02-section5-step2-1.png)

Wählen Sie im Fenster „Projekteinstellungen“ **XR-Plug-In-Verwaltung** > **XR-Plug-In-Verwaltung installieren** aus, um die XR-Plug-In-Verwaltung zu installieren:

![Unity: „Publishing Settings“ mit konfiguriertem Paketnamen](images/mr-learning-base/base-02-section5-step2-2.png)

nachdem Unity die Installation der XR-Plug-In-Verwaltung abgeschlossen hat. Stellen Sie sicher, dass Sie sich in den Einstellungen für die Universelle Windows-Plattform befinden, und aktivieren Sie „XR beim Start initialisieren“.

![Unity-Konfiguration der XR-Plug-In-Verwaltung](images/mr-learning-base/base-02-section5-step2-3.png)

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **XR Settings** (Player > XR-Einstellungen) aus, klicken Sie auf das **+** -Symbol, und wählen Sie „Windows Mixed Reality“ aus, um das Windows Mixed Reality SDK hinzuzufügen:

![Unity: XR-Einstellungen mit ausgewähltem „Windows Mixed Reality SDK hinzufügen“](images/mr-learning-base/base-02-section5-step2-4.png)

Nachdem Unity das Importieren des Windows Mixed Reality SDK abgeschlossen hat, sollte wieder das Fenster des MRTK-Projektkonfigurators angezeigt werden. Wenn dies nicht der Fall ist, verwenden Sie das Unity-Menü, um es zu öffnen.

Verwenden Sie im Fenster des MRTK-Projektkonfigurators die Dropdownliste **Audio spatializer** (Räumliche Audiowiedergabe), um den **MS HRTF Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellung zu übernehmen:

![Unity: XR-Einstellungen mit ausgewähltem „Windows Mixed Reality SDK hinzufügen“](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern. Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist. Weitere Informationen zu diesem Thema finden Sie in den <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">Tutorials zur räumlichen Audiowiedergabe</a>.

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **XR Settings** (Player > XR-Einstellungen) aus, und verwenden Sie dann die Dropdownliste **Depth Format** (Tiefenformat), um **16-Bit Tiefe** auszuwählen:

![Unity: Tiefe 16 aktivieren](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen. Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">Leistung</a>sdokumentation des MRTK.

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_:

![Unity: „Publishing Settings“ mit konfiguriertem Paketnamen](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Der Paketname stellt den eindeutigen Bezeichner für die App dar. Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.

> [!TIP]
> Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird. Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.

## <a name="creating-and-configuring-the-scene"></a>Erstellen und Konfigurieren der Szene

Wählen Sie im Unity-Menü **File** > **New Scene** (Datei > Neue Szene) aus, um eine neue Szene zu erstellen:

![Unity: Menüpfad für „New Scene“](images/mr-learning-base/base-02-section6-step1-1.png)

Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Mixed Reality-Toolkit > Zu Szene hinzufügen und konfigurieren) aus, um Ihrer aktuellen Szene das MRTK hinzuzufügen:

![Unity: Menüpfad zu „Add to Scene and Configure...“](images/mr-learning-base/base-02-section6-step1-2.png)

Überprüfen Sie bei im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster, ob das Konfigurationsprofil des **Mixed Reality-Toolkits** auf **DefaultMixedRealityToolkitConfigurationProfile** festgelegt ist:

![MixedRealityToolkit-Komponente von Unity mit ausgewähltem DefaultMixedRealityTookitConfigurationProfile](images/mr-learning-base/base-02-section6-step1-3.png)

Wählen Sie im Unity-Menü **File** > **Save As...** (Datei > Speichern unter...) aus, um das Save Scene-Fenster (Szene speichern) zu öffnen:

![Unity: Menüpfad für „Save As...“](images/mr-learning-base/base-02-section6-step1-4.png)

Navigieren Sie im Save Scene-Fenster zum Ordner **Scenes** (Szenen), geben Sie Ihrer Szene einen passenden Namen, beispielsweise _ErsteSchritte_, und klicken Sie auf die Schaltfläche **Save** (Speichern), um die Szene zu speichern:

![Unity: Aufforderungsfenster zum Speichern der Szene](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>Erstellen Ihrer Anwendung auf der HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Erstellen des Unity-Projekts

Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen.

Klicken Sie im Build Settings-Fenster (Buildeinstellungen) auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um der Liste **Scenes In Build** (Szenen im Build) Ihre aktuelle Szene hinzuzufügen, und klicken Sie dann auf die Schaltfläche **Build** (Erstellen), um das Build Universal Windows Platform-Fenster (Erstellen für Universelle Windows-Plattform) zu öffnen:

![Unity-Fenster „Build Settings“ mit ausgewählter UWP](images/mr-learning-base/base-02-section7-step1-1.png)

Wählen Sie im Build Universal Windows Platform-Fenster einen passenden Speicherort aus, um Ihren Build zu speichern, beispielsweise _D:\MixedRealityLearning\Builds_, erstellen Sie einen neuen Ordner mit einem passenden Namen, z. B. _GettingStarted_, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Auswählen eines Ordners](images/mr-learning-base/base-02-section7-step1-2.png)

Warten Sie, bis Unity den Buildvorgang abgeschlossen hat:

![Unity: Buildvorgang wird ausgeführt](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Erstellen und Bereitstellen der Anwendung

Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben. Navigieren Sie zum Ordner, und doppelklicken Sie auf die Projektmappendatei, um sie in Visual Studio zu öffnen:

![Windows-Explorer mit neu erstellter, ausgewählter Visual Studio-Projektmappe](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation **[Installieren der Tools](../../install-the-tools.md)** angegeben) installiert sind.

Konfigurieren Sie Visual Studio für HoloLens 2, indem Sie die **Master**- oder **Release**-Konfiguration, die **ARM64**-Architektur und **Gerät** als Ziel auswählen:

![Visual Studio, konfiguriert für die Bereitstellung in HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> Wenn Sie auf HoloLens (1. Generation) bereitstellen, wählen Sie die **x86**-Architektur aus.

> [!NOTE]
> Für HoloLens erstellen Sie normalerweise für die ARM-Architektur. Jedoch besteht ein <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>bekanntes Problem</strong></a> in Unity 2019.3, das zu Fehlern führt, wenn ARM in Visual Studio als Buildarchitektur ausgewählt wird. Die empfohlene Umgehung besteht darin, Builds für ARM64 zu erstellen. Wenn diese Option nicht in Frage kommt, navigieren Sie zu **Edit > Project Settings > Player > Other Settings** (Bearbeiten > Projekteinstellungen > Player > Weitere Einstellungen), und deaktivieren Sie **Graphics Jobs** (Grafikaufträge).

> [!NOTE]
> Wenn „Device“ (Gerät) nicht als Zieloption angezeigt wird, müssen Sie möglicherweise das Startprojekt für die Visual Studio-Projektmappe vom Projekt „IL2CPP“ zum Projekt „UWP“ ändern. Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf den Namen Ihres Projekts (Universal Windows), und wählen Sie **Set as StartUp Project** (Als Startprojekt festlegen) aus.

Verbinden Sie Ihre HoloLens mit Ihrem Computer, wählen Sie dann **Debug** > **Start Without Debugging** (Debuggen > Ohne Debuggen starten) aus, um zu erstellen und auf Ihrem Gerät bereitzustellen:

![Visual Studio-Menüpfad für „Ohne Debuggen starten“](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> Bevor Sie den Build für Ihr Gerät erstellen, muss das Gerät in den Entwicklermodus versetzt und mit Ihrem Entwicklungscomputer gekoppelt werden. Sie können beide Schritte ausführen, indem Sie [diese Anweisungen](../../platform-capabilities-and-apis/using-visual-studio.md) befolgen.

> [!TIP]
> Sie können auch auf dem [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) bereitstellen oder ein [App-Paket](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) zum Querladen erstellen.

Bei der Option „Start Without Debugging“ (Ohne Debuggen starten) wird die App auf Ihrem Gerät automatisch ohne angefügten Visual Studio-Debugger gestartet.

Wählen Sie **Build > Deploy Solution** (Erstellen > Projektmappe bereitstellen) aus, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.

> [!NOTE]
>Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **Toggle Diagnostics** (Diagnose ein-/ausschalten) ein- und ausblenden. Es empfiehlt sich, während der Entwicklung den Profiler die meiste Zeit anzuzeigen, um zu verstehen, wann Änderungen an der App die Leistung beeinträchtigen können. Beispielsweise sollten HoloLens-Apps [durchgängig bei 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ausgeführt werden.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben jetzt Ihre erste HoloLens-App bereitgestellt. Während Sie sich in ihr bewegen, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen. Diese Features sind nur einige der grundlegenden Bestandteile von MRTK. In den bevorstehenden Tutorials fügen Sie Ihrer Szene Inhalte hinzu, um die Funktionen von HoloLens und des MRTK kennenzulernen.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 3. Konfigurieren der MRTK-Profile](mr-learning-base-03.md)