---
title: Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie Ihr Unity-Projekt für das Mixed Reality Toolkit (MRTK) konfigurieren und es in Ihrer HoloLens 2 bereitstellen.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 2ce119e1dd18eacf02088d00e99fb70d06bf956e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008220"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung

In diesem Tutorial erfahren Sie, wie Sie ein neues Unity-Projekt erstellen, es für die Entwicklung mit dem <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> konfigurieren und das MRTK importieren. Außerdem werden Sie durch Konfiguration, Erstellung und Bereitstellung einer einfachen Unity-Szene aus Visual Studio auf Ihrer HoloLens 2 geführt. Nachdem Sie diese auf Ihrer HoloLens 2 bereitgestellt haben, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.

## <a name="objectives"></a>Ziele

* Erfahren, wie Unity für die HoloLens-Entwicklung konfiguriert wird.
* Erfahren, wie Ihre App erstellt und in HoloLens bereitgestellt wird.
* Kennenlernen des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers auf Ihrem HoloLens 2-Gerät.

## <a name="creating-the-unity-project"></a>Erstellen des Unity-Projekts

1. Starten Sie **Unity Hub**, wählen Sie die Registerkarte **Projects** (Projekte) aus, und klicken Sie dann auf den **Abwärtspfeil** neben der Schaltfläche **New** (Neu):

![Unity-Hub mit hervorgehobenem Abwärtspfeil der Schaltfläche „Neu“](images/mr-learning-base/base-02-section1-step1-1.png)

2. Wählen Sie im Dropdownmenü die Unity-Version aus, die in den [Voraussetzungen](mr-learning-base-01.md#prerequisites) angegeben ist:

![Auswählen der Unity-Version](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Wenn diese bestimmte Unity-Version nicht auf dem Unity Hub verfügbar ist, können Sie die Installation aus dem <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Downloadarchiv</a> von Unity einleiten.

3. Führen Sie im Fenster **Create a new project** (Neues Projekt erstellen) Folgendes aus:

    * Vergewissern Sie sich, dass **Templates** (Vorlagen) auf **3D** festgelegt ist.
    * Geben Sie im Feld **Project Name** (Projektname) einen passenden Namen für Ihr Projekt ein (beispielsweise „MRTK-Tutorials“).
    * Klicken Sie auf die Schaltfläche mit den drei Punkten neben **Location** (Speicherort), und navigieren Sie dann zu dem Ordner, in dem Sie Ihr Projekt speichern möchten.

> [!CAUTION]
> Wenn Sie unter Windows arbeiten, müssen Sie den MAX_PATH-Grenzwert von 255 Zeichen beachten. Daher sollten Sie das Unity-Projekt in der Nähe des Stammverzeichnisses des Laufwerks speichern.

    * Klicken Sie auf die Schaltfläche **Erstellen** . Dadurch wird das neue Unity-Projekt erstellt und gestartet.

![Unity Hub mit ausgefülltem Fenster „Create a new project“ (Neues Projekt erstellen)](images/mr-learning-base/base-02-section1-step1-3.png)

Die Statusleiste hält Sie über Ihren Fortschritt auf dem Laufenden.

![Die Unity-Statusleiste hält Sie über den Status Ihrer Projekterstellung auf dem Laufenden](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Wechseln der Buildplattform

1. Wählen Sie in der Menüleiste **File** > **Build Settings...** (Datei > Buildeinstellungen) aus

![Unity: Build Settings... Menüpfad](images/mr-learning-base/base-02-section2-step1-1.png)

2. Wählen Sie im Fenster **Build Settings** (Buildeinstellungen) **Universal Windows Platform** (Universelle Windows-Plattform) aus, und klicken Sie dann auf die Schaltfläche **Switch Platform** (Plattform wechseln):

![Unity-Fenster „Build Settings“ mit ausgewählter UWP, um von der Plattform „Eigenständig“ zu wechseln](images/mr-learning-base/base-02-section2-step1-2.png)

3. Warten Sie, bis Unity den Plattformwechsel abgeschlossen hat, und schließen Sie dann das Fenster **Build Settings** (Buildeinstellungen).

## <a name="importing-the-textmeshpro-essential-resources"></a>Importieren der TextMeshPro Essential-Ressourcen

Die TextMeshPro Essential-Ressourcen sind für die Benutzeroberflächenelemente des MRTK erforderlich. Wenn Sie nicht beabsichtigen, die Benutzeroberflächenelemente des MRTK in Ihrem Projekt zu verwenden, können Sie diesen Schritt überspringen.

1. Wählen Sie in der Menüleiste **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Fenster > TextMeshPro > TMP Essential Resources importieren) aus.

![Unity: Menüpfad für „Import TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-1.png)

2. Klicken Sie im **Import Unity Package**-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:

![Unity-Fenster für Importieren von „TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a>Importieren des Mixed Reality-Toolkits

1. Laden Sie das benutzerdefinierte Unity-Paket herunter:

    [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. Wählen Sie in der Menüleiste **Assets** > **Import Package** > **Custom Package...** (Assets > Paket importieren > Benutzerdefiniertes Paket...) aus.
3. Navigieren Sie im Dialogfeld **Import package...** (Paket importieren...) zum Speicherort des Pakets, das Sie soeben heruntergeladen haben, und klicken Sie dann auf die Schaltfläche **Open** (Öffnen).
4. Klicken Sie im **Import Unity Package**-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren.

## <a name="selecting-mrtk-and-project-settings"></a>Auswählen von MRTK- und Projekteinstellungen

Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des **MRTK-Projektkonfigurators** angezeigt werden. Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) wechseln:

![Unity: Menüpfad für „Configure Unity Project“](images/mr-learning-base/base-02-section5-step1-1.png)

1. Klappen Sie im Fenster des **MRTK-Projektkonfigurators** falls erforderlich **Modify Configurations** (Konfigurationen ändern) auf, und vergewissern Sie sich dann, dass alle Optionen aktiviert sind.

![Fenster des Unity MRTK-Projektkonfigurators mit angezeigter Option „Modify Configurations“](images/mr-learning-base/base-02-section5-step1-2.png)

2. Klicken Sie auf die Schaltfläche **Apply** (Übernehmen), um die Änderungen zu übernehmen.

![Schaltfläche „Übernehmen“ im MRTK](images/mr-learning-base/apply.png)

> [!NOTE]
> Sie verwenden die integrierte Legacy-XR von Unity anstelle des neuen XR-Plug-In-Systems, weil das neue System mit den für diese Tutorialreihe [empfohlenen Unity- und MRTK-Versionen](mr-learning-base-01.md#prerequisites) nicht vollständig kompatibel ist. Sollten Warnungen zu einer veralteten Version des integrierten XR-Plug-Ins angezeigt werden, können Sie diese ignorieren.

> [!TIP]
> Die Anwendung der MRTK-Standardeinstellungen ist optional, wird aber dringend empfohlen, weil es bei der Konfiguration einiger empfohlener Unity-Einstellungen hilfreich ist:
>
> * Legacy-XR aktivieren: Aktiviert VR für das Projekt.
> * Legen Sie den Single Pass-instanziierten Renderingpfad fest: Verbessert die Grafikleistung, indem die Renderpipeline für beide Augen im selben Zeichnen-Aufruf ausgeführt wird. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Single Pass-instanziiertes Rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) der [Leistung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)sdokumentation von MRTK.
> * Standardebene für Spatial Awareness (räumliche Wahrnehmung) festlegen: Erstellt eine Unity-Ebene namens „Spatial Awareness“ und konfiguriert MRTK für die Verwendung dieser Ebene für das Gittermodell für räumliche Wahrnehmung. Weitere Informationen zu Unity-Ebenen finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.

3. Wählen Sie in der Menüleiste **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus.

4. Wählen Sie im Fenster **Project Settings** (Projekteinstellungen) **Player** aus, klicken Sie auf das Dropdownmenü **XR Settings** (XR-Einstellungen), und aktivieren Sie dann das Kontrollkästchen neben **Virtual Reality Supported** (Virtual Reality unterstützt):

![Unity-XR-Einstellungen mit angezeigter Option „Virtual Reality unterstützt“](images/mr-learning-base/base-02-section5-step2-2.png)

Dadurch wird das Windows Mixed Reality SDK importiert:

![Unity XR-Einstellungen mit angezeigten Virtual Reality SDKs](images/mr-learning-base/mixed-reality-sdk.png)

Nachdem Unity das Importieren des Windows Mixed Reality SDK abgeschlossen hat, sollte wieder das Fenster des **MRTK-Projektkonfigurators** angezeigt werden. Wenn das nicht der Fall ist, wählen Sie **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um es zu öffnen:

5. Klicken Sie im Fenster des **MRTK-Projektkonfigurators** auf das Dropdownmenü **Audio spatializer** (Räumliche Audiowiedergabe), und wählen Sie dann **MS HRTF Spatializer** aus.

![Projekteinstellungen mit angezeigten Optionen für die räumliche Audiowiedergabe](images/mr-learning-base/base-02-section5-step2-3.png)

6. Klicken Sie auf die Schaltfläche **Übernehmen**. Dadurch wird das Fenster des **MRTK-Projektkonfigurators** geschlossen.

    > [!TIP]
    > Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern. Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist. Weitere Informationen zu diesem Thema finden Sie in den Tutorials zur räumlichen Audiowiedergabe.

7. Klicken Sie im Fenster **Project Settings** (Projekteinstellungen) auf das Fenster **Depth Format** (Tiefenformat), und wählen Sie dann **16-bit depth** (16-Bit Tiefe) aus:

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Unity XR-Einstellungen mit ausgewählter Option „16-Bit Tiefe“.":::

    > [!TIP]
    > Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Tiefenpufferfreigabe (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) der [Leistung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)sdokumentation von MRTK.

8. Klicken Sie auf das Dropdownmenü **Publishing Settings** (Veröffentlichungseinstellungen), dann in das Feld **Package name** (Paketname), und geben Sie einen passenden Namen ein (beispielsweise „MRTK-Tutorials-Erste-Schritte“).

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Veröffentlichungseinstellungen in Unity mit konfiguriertem Paketnamen.":::

    **Paketname und Produktname**

    - Der Paketname stellt den eindeutigen Bezeichner für die App dar. Sie sollten diesen Bezeichner erstellen, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.
    - Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird. Um das Auffinden der App während der Entwicklung zu erleichtern, können Sie vor dem Namen einen Unterstrich hinzufügen, sodass sie in Listen oben einsortiert wird.

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Unity-Projekteinstellungen mit konfiguriertem Produktnamen.":::

9. Schließen Sie das Fenster **Project Settings** (Projekteinstellungen).

## <a name="creating-and-configuring-the-scene"></a>Erstellen und Konfigurieren der Szene

1. Wählen Sie in der Menüleiste **File** > **New Scene** (Datei > Neue Szene) aus.
2. Sie fügen der Szene das MRTK hinzu, indem Sie in der Menüleiste **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Mixed Reality Toolkit > Zu Szene hinzufügen und konfigurieren) auswählen.

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity-Menüpfad „Zu Szene hinzufügen und konfigurieren“.":::

3. Achten Sie darauf, dass im Fenster **Hierarchy** (Hierarchie) das **MixedRealityToolkit** ausgewählt ist.

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Vergewissern Sie sich, dass „MixedRealityTookit“ ausgewählt ist.":::

4. Überprüfen Sie im Abschnitt **MixedRealityToolkit** des **Inspektorfensters**, dass das Konfigurationsprofil auf **DefaultMixedRealityToolkitConfigurationProfile** festgelegt ist:

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Unity MixedRealityToolkit-Komponente mit ausgewähltem DefaultMixedRealityTookitConfigurationProfile.":::

    > [!IMPORTANT]
    > Normalerweise verwenden Sie zum Entwickeln für HoloLens das DefaultHoloLens2ConfigurationProfile-Profil. Im Rahmen dieses Tutorials verwenden Sie jedoch das DefaultMixedRealityToolkitConfigurationProfile. Im nächsten Tutorial, [Konfigurieren der MRTK-Profile](mr-learning-base-03.md), wechseln Sie dann zum DefaultHoloLens2ConfigurationProfile.

5. Wählen Sie in der Menüleiste **File** > **Save As...** (Datei > Speichern unter) aus.
6. Navigieren Sie im Dialogfeld **Save Scene** (Szene speichern) zum Ordner **Scenes** (Szenen) Ihres Projekts. Geben Sie im Feld **File name** (Dateiname) Ihrer Szene einen passenden Namen (beispielsweise „\_ErsteSchritte\_“), und klicken Sie dann auf die Schaltfläche **Save** (Speichern).

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Speichern-Bestätigungsfenster beim Speichern von Szenen in Unity.":::

## <a name="building-and-deploying-to-your-hololens-2"></a>Entwickeln und Bereitstellen auf Ihrer HoloLens 2

> Bevor Sie auf Ihrem Gerät erstellen, bestätigen Sie die folgenden Punkte:
- Ihr Gerät befindet sich im Entwicklermodus.
- Ihr Gerät ist mit Ihrem Entwicklungscomputer gekoppelt. Andernfalls wird in Visual Studio während des Erstellungsvorgangs das folgende Dialogfeld angezeigt:

![Entering PIN for pairing devices (PIN für Gerätekopplung eingeben)](images/mr-learning-base/pin-request.png)

 Weitere Informationen zu diesen beiden Schritten finden Sie unter [Verwenden von Visual Studio zum Bereitstellen und Debuggen](../../platform-capabilities-and-apis/using-visual-studio.md).

1. Wählen Sie in der Menüleiste **File** > **Build Settings...** (Datei > Buildeinstellungen) aus.
2. Klicken Sie im Fenster **Build Settings** (Buildeinstellungen) auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um der Liste **Scenes In Build** (Szenen im Build) Ihre aktuelle Szene hinzuzufügen.

![Hinzufügen Ihrer aktuellen Szene zur Liste „Szenen im Build“](images/mr-learning-base/base-02-section7-step1-1.png)

3. Klicken Sie auf die Schaltfläche **Build**.

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Klicken Sie auf die Schaltfläche Build.":::

4. Wählen Sie im Dialogfeld **Build Universal Windows Platform** (Universelle Windows-Plattform erstellen) einen passenden Speicherort zum Speichern Ihres Builds aus (beispielsweise kann es sinnvoll sein, einen Ordner „Builds“ in Ihrem Ordner „MRTK-Tutorials“ zu erstellen). Erstellen Sie einen neuen Ordner, und geben Sie ihm einen passenden Namen (beispielsweise „Erste Schritte“), wählen Sie den Ordner aus, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Unity Build-Fenster mit Ihrem angezeigten Buildordner.":::

    Es wird eine Statusleiste angezeigt, die Sie über den Fortschritt Ihres Builds auf dem Laufenden hält.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Unity-Buildvorgang wird ausgeführt.":::

    > [!TIP]
    > Sie können auch auf dem [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) bereitstellen oder ein [App-Paket](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) zum Querladen erstellen.

5. Wenn der Buildvorgang abgeschlossen ist, navigieren Sie im Datei-Explorer zu dem Speicherort, an dem Sie den Build gespeichert haben, und doppelklicken Sie dann auf die Projektmappendatei, um sie in Visual Studio zu öffnen:

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Windows Explorer mit der ausgewählten, neu erstellten Visual Studio-Projektmappendatei.":::

    > [!NOTE]
    > Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation **[Installieren der Tools](../../install-the-tools.md)** angegeben) installiert sind.

6. Konfigurieren Sie Visual Studio für HoloLens 2, indem Sie die **Master**- oder **Release**-Konfiguration, die **ARM64**-Architektur und **Gerät** als Ziel auswählen.

    > [!TIP]
    > Wenn Sie auf HoloLens (1. Generation) bereitstellen, wählen Sie die **x86**-Architektur aus.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Visual Studio, konfiguriert für die Bereitstellung in HoloLens 2":::.

    > [!NOTE]
    > Für HoloLens erstellen Sie normalerweise für die ARM-Architektur. Jedoch besteht ein <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>bekanntes Problem</strong></a> in Unity 2019.3, das zu Fehlern führt, wenn ARM in Visual Studio als Buildarchitektur ausgewählt wird. Die empfohlene Umgehung besteht darin, Builds für ARM64 zu erstellen. Wenn diese Option nicht in Frage kommt, navigieren Sie zu **Edit > Project Settings > Player > Other Settings** (Bearbeiten > Projekteinstellungen > Player > Weitere Einstellungen), und deaktivieren Sie **Graphics Jobs** (Grafikaufträge).

    > [!NOTE]
    > Wenn „Device“ (Gerät) nicht als Zieloption angezeigt wird, müssen Sie möglicherweise das Startprojekt für die Visual Studio-Projektmappe vom Projekt „IL2CPP“ zum Projekt „UWP“ ändern. Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf den Namen Ihres Projekts (Universal Windows), und wählen Sie dann **Set as StartUp Project** (Als Startprojekt festlegen) aus.

7. Verbinden Sie Ihre HoloLens mit Ihrem Computer, und führen Sie dann eine der folgenden Aktionen aus:
- Wenn Sie die App erstellen, sie auf Ihrer HoloLens bereitstellen und automatisch ohne angefügten Debugger starten möchten, wählen Sie in der Menüleiste **Debuggen** > **Starten ohne Debuggen** aus.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Menüpfad „Starten ohne Debuggen“ in Visual Studio.":::

- Wenn Sie die App erstellen und auf Ihrer HoloLens bereitstellen, sie jedoch nicht automatisch starten möchten, wählen Sie in der Menüleiste **Erstellen > Projektmappe bereitstellen** aus.

    > [!NOTE]
    >Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **Toggle Diagnostics** (Diagnose ein-/ausschalten) ein- und ausblenden. Es empfiehlt sich, während der Entwicklung den Profiler die meiste Zeit anzuzeigen, um zu verstehen, wann Änderungen an der App die Leistung beeinträchtigen können. Beispielsweise sollten HoloLens-Apps [durchgängig bei 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ausgeführt werden.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben jetzt Ihre erste HoloLens-App bereitgestellt. Während Sie sich in ihr bewegen, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen. Diese Features sind nur einige der grundlegenden Bestandteile von MRTK. In den bevorstehenden Tutorials fügen Sie Ihrer Szene Inhalte hinzu, um die Funktionen von HoloLens und des MRTK kennenzulernen.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 3. Konfigurieren der MRTK-Profile](mr-learning-base-03.md)
