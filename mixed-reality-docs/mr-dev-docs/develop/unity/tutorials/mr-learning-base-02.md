---
title: Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie Ihr Unity-Projekt für das Mixed Reality Toolkit (MRTK) konfigurieren und es in Ihrer HoloLens 2 bereitstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 4363d3280036ef2cd93e75233005c00db17eb59b
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088616"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="bc515-104">2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="bc515-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="bc515-105">In diesem Tutorial erfahren Sie, wie Sie ein neues Unity-Projekt erstellen, es für die Entwicklung mit dem <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> konfigurieren und das MRTK importieren.</span><span class="sxs-lookup"><span data-stu-id="bc515-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="bc515-106">Außerdem werden Sie durch Konfiguration, Erstellung und Bereitstellung einer einfachen Unity-Szene aus Visual Studio auf Ihrer HoloLens 2 geführt.</span><span class="sxs-lookup"><span data-stu-id="bc515-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="bc515-107">Nachdem Sie diese auf Ihrer HoloLens 2 bereitgestellt haben, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="bc515-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="bc515-108">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.</span><span class="sxs-lookup"><span data-stu-id="bc515-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a><span data-ttu-id="bc515-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="bc515-110">Objectives</span></span>

* <span data-ttu-id="bc515-111">Erfahren, wie Unity für die HoloLens-Entwicklung konfiguriert wird</span><span class="sxs-lookup"><span data-stu-id="bc515-111">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="bc515-112">Erfahren, wie Ihre App erstellt und in HoloLens bereitgestellt wird</span><span class="sxs-lookup"><span data-stu-id="bc515-112">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="bc515-113">Kennenlernen des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers auf dem HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="bc515-113">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="bc515-114">Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="bc515-114">Creating the Unity project</span></span>

<span data-ttu-id="bc515-115">Starten Sie **Unity Hub**, wählen Sie die Registerkarte **Projects** (Projekte) aus, und klicken Sie auf den **Abwärtspfeil** neben der Schaltfläche **New** (Neu):</span><span class="sxs-lookup"><span data-stu-id="bc515-115">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity-Hub mit hervorgehobener Schaltfläche „New“](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="bc515-117">Wählen Sie in der Dropdownliste die Unity-**Version** aus, die oben in den [Voraussetzungen](mr-learning-base-01.md#prerequisites) angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="bc515-117">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity-Hub mit Versionsauswahl-Dropdown „NEW“](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="bc515-119">Wenn diese bestimmte Unity-Version nicht auf dem Unity Hub verfügbar ist, können Sie die Installation aus dem <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Downloadarchiv</a> von Unity einleiten.</span><span class="sxs-lookup"><span data-stu-id="bc515-119">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="bc515-120">Erstellen Sie im Fenster ein neues Projekt:</span><span class="sxs-lookup"><span data-stu-id="bc515-120">In the Create a new project window:</span></span>

* <span data-ttu-id="bc515-121">Vergewissern Sie sich, dass **Templates** (Vorlagen) auf **3D** festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="bc515-121">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="bc515-122">Geben Sie einen passenden **Project Name** (Projektnamen) ein, z. B. _MRTK-Tutorials_</span><span class="sxs-lookup"><span data-stu-id="bc515-122">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="bc515-123">Wählen Sie eine geeignete **Location** (Speicherort) zum Speichern Ihres Projekts, z. B. _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="bc515-123">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="bc515-124">Klicken Sie auf die Schaltfläche **Create** (Erstellen), um das neue Unity-Projekt zu erstellen</span><span class="sxs-lookup"><span data-stu-id="bc515-124">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity-Hub mit ausgefülltem Fenster „Create new project“ (Neues Projekt erstellen)](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="bc515-126">Wenn Sie unter Windows arbeiten, müssen Sie den MAX_PATH-Grenzwert von 255 Zeichen beachten.</span><span class="sxs-lookup"><span data-stu-id="bc515-126">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="bc515-127">Daher sollten Sie das Unity-Projekt in der Nähe des Stammverzeichnisses des Laufwerks speichern.</span><span class="sxs-lookup"><span data-stu-id="bc515-127">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="bc515-128">Warten Sie, bis Unity das Projekt erstellt hat:</span><span class="sxs-lookup"><span data-stu-id="bc515-128">Wait for Unity to create the project:</span></span>

![Unity: Erstellen eines neuen Projekts in Bearbeitung](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="bc515-130">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="bc515-130">Switching the build platform</span></span>

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="bc515-131">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bc515-131">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="bc515-132">Wählen Sie im Unity-Menü **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Fenster > TextMeshPro > TMP Essential Resources importieren) aus, um das Importfenster für Unity-Pakete zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bc515-132">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity: Menüpfad für „Import TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="bc515-134">Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="bc515-134">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity-Fenster für Importieren von „TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="bc515-136">Die TextMeshPro Essential-Ressourcen sind für die Benutzeroberflächenelemente des MRTK erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bc515-136">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="bc515-137">Sie können diesen Schritt überspringen, wenn Sie nicht beabsichtigen, die Benutzeroberflächenelemente des MRTK in Ihrem Projekt zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bc515-137">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="bc515-138">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="bc515-138">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="bc515-139">Zum Importieren des Mixed Reality-Toolkits in das Unity-Projekt müssen Sie das [Mixed Reality-Featuretool verwenden](../welcome-to-mr-feature-tool.md), das Entwicklern das Erkennen, Aktualisieren und Hinzufügen von Mixed Reality-Featurepaketen zu Unity-Projekten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="bc515-139">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="bc515-140">Sie können Pakete vor dem Importieren nach Name oder Kategorie durchsuchen, ihre Abhängigkeiten anzeigen und sogar Änderungsvorschläge für Ihre Projektmanifestdatei anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bc515-140">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="bc515-141">Laden Sie die neueste Version des Mixed Reality-Featuretools aus dem [Microsoft Download Center](https://aka.ms/MRFeatureTool) herunter. Wenn der Download abgeschlossen ist, entpacken Sie die Datei, und speichern Sie sie auf Ihrem Desktop.</span><span class="sxs-lookup"><span data-stu-id="bc515-141">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="bc515-142">Installieren Sie [.NET 5.0 Runtime](https://dotnet.microsoft.com/download/dotnet/5.0), damit Sie das Mixed Reality-Featuretool ausführen können.</span><span class="sxs-lookup"><span data-stu-id="bc515-142">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="bc515-143">Das Mixed Reality-Featuretool kann zurzeit nur unter Windows ausgeführt werden. Wenn Sie MacOS verwenden, befolgen Sie diese [Vorgehensweise](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages), um das Mixed Reality-Toolkit herunterzuladen und in das Unity-Projekt zu importieren.</span><span class="sxs-lookup"><span data-stu-id="bc515-143">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="bc515-144">Öffnen Sie die ausführbare Datei **MixedRealityFeatureTool** aus dem heruntergeladenen Ordner, um das Mixed Reality-Featuretool zu starten.</span><span class="sxs-lookup"><span data-stu-id="bc515-144">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![Öffnen von MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a><span data-ttu-id="bc515-146">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="bc515-146">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="bc515-147">1. Übernehmen der Einstellungen des MRTK-Projektkonfigurators</span><span class="sxs-lookup"><span data-stu-id="bc515-147">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="bc515-148">Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des MRTK-Projektkonfigurators angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bc515-148">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="bc515-149">Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) wechseln:</span><span class="sxs-lookup"><span data-stu-id="bc515-149">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity: Menüpfad für „Configure Unity Project“](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="bc515-151">Klappen Sie im Projektkonfiguratorfenster des MRTK den Abschnitt **Modify Configurations** (Konfigurationen ändern) auf, vergewissern Sie sich, dass alle Optionen aktiviert sind, und klicken Sie auf die Schaltfläche **Apply** (Übernehmen), um die Einstellungen zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="bc515-151">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Unity MRTK-Projektkonfigurator-Fenster](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="bc515-153">Die Anwendung der MRTK-Standardeinstellungen ist optional, wird aber dringend empfohlen, weil es bei der Konfiguration einiger empfohlener Unity-Einstellungen hilfreich ist:</span><span class="sxs-lookup"><span data-stu-id="bc515-153">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="bc515-154">Legen Sie den Single Pass-instanziierten Renderingpfad fest: Verbessert die Grafikleistung, indem die Renderpipeline für beide Augen im selben Zeichnen-Aufruf ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="bc515-154">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="bc515-155">Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Single Pass-instanziiertes Rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) der [Leistung](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)sdokumentation von MRTK.</span><span class="sxs-lookup"><span data-stu-id="bc515-155">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="bc515-156">Standardebene für Spatial Awareness (räumliche Wahrnehmung) festlegen: Erstellt eine Unity-Ebene namens „Spatial Awareness“ und konfiguriert MRTK für die Verwendung dieser Ebene für das Gittermodell für räumliche Wahrnehmung.</span><span class="sxs-lookup"><span data-stu-id="bc515-156">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="bc515-157">Weitere Informationen zu Unity-Ebenen finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.</span><span class="sxs-lookup"><span data-stu-id="bc515-157">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="bc515-158">2. Konfigurieren zusätzlicher Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="bc515-158">2. Configure additional project settings</span></span>

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="bc515-159">Erstellen der Szene und Konfigurieren des MRTK</span><span class="sxs-lookup"><span data-stu-id="bc515-159">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="bc515-160">Wählen Sie im Unity-Menü **File** > **New Scene** (Datei > Neue Szene) aus, um eine neue Szene zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="bc515-160">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity: Menüpfad für „New Scene“](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="bc515-162">Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Mixed Reality-Toolkit > Zu Szene hinzufügen und konfigurieren) aus, um Ihrer aktuellen Szene das MRTK hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="bc515-162">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity: Menüpfad zu „Add to Scene and Configure...“](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

<span data-ttu-id="bc515-164">Wählen Sie im Unity-Menü **File** > **Save As...** (Datei > Speichern unter...) aus, um das Save Scene-Fenster (Szene speichern) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bc515-164">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity: Menüpfad für „Save As...“](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> <span data-ttu-id="bc515-166">Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen.</span><span class="sxs-lookup"><span data-stu-id="bc515-166">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="bc515-167">Weitere Informationen zu diesem Thema finden Sie im Abschnitt <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Tiefenpufferfreigabe (HoloLens)</a> der <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Leistung</a>sdokumentation des MRTK.</span><span class="sxs-lookup"><span data-stu-id="bc515-167">To learn more about this topic, you can refer to the   <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

![Unity: Aufforderungsfenster zum Speichern der Szene](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="bc515-169">Importieren der Tutorialressourcen</span><span class="sxs-lookup"><span data-stu-id="bc515-169">Importing the tutorial assets</span></span>

<span data-ttu-id="bc515-170">Laden Sie das folgende benutzerdefinierte Unity-Paket herunter:</span><span class="sxs-lookup"><span data-stu-id="bc515-170">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="bc515-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="bc515-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="bc515-172">Wählen Sie zum Importieren eines benutzerdefinierten Unity-Pakets im Unity-Menü **Assets** > **Import Package** > **Custom Package...** (Assets > Paket importieren > Benutzerdefiniertes Paket...) aus, um das Fenster zum Importieren von Paketen zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bc515-172">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Importieren eines benutzerdefinierten Pakets](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="bc515-174">Wählen Sie im Fenster „Import package...“ (Paket importieren...) das heruntergeladene Paket **MRTK:HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** aus, und klicken Sie auf die Schaltfläche „Open“ (Öffnen):</span><span class="sxs-lookup"><span data-stu-id="bc515-174">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![Auswählen eines Ressourcenpakets](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="bc515-176">Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche All (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche Import (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="bc515-176">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Auswählen aller zu importierenden Ressourcen](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="bc515-178">Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="bc515-178">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Unity-Projektfenster nach dem Importieren von Ressourcen](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a><span data-ttu-id="bc515-180">Konfigurieren der Szene</span><span class="sxs-lookup"><span data-stu-id="bc515-180">Configuring the Scene</span></span>

<span data-ttu-id="bc515-181">Navigieren Sie im Projektfenster zum Ordner „Assets“ > „MRTK.Tutorials.GettingStarted“ > „Prefabs“:</span><span class="sxs-lookup"><span data-stu-id="bc515-181">In the Project window, navigate to the Assets > MRTK.Tutorials.GettingStarted > Prefabs folder:</span></span>

<span data-ttu-id="bc515-182">Klicken Sie im Projektfenster auf das **Cube**-Prefab, und ziehen Sie es aus dem Projektfenster in das Hierarchiefenster. Konfigurieren Sie dann im Inspektorfenster die Komponente **Transform** (Transformieren) wie folgt:</span><span class="sxs-lookup"><span data-stu-id="bc515-182">From the Project window, click-and-drag the **Cube** prefab on to the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="bc515-183">**Position**: X = 0, Y = 0, Z = 0,5</span><span class="sxs-lookup"><span data-stu-id="bc515-183">**Position**: X = 0, Y = 0, Z = 0.5</span></span>
* <span data-ttu-id="bc515-184">**Drehung**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="bc515-184">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="bc515-185">**Skalierung**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="bc515-185">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Hinzufügen eines Cube-Objekts zur Szene](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="bc515-187">Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **Cube**-Objekt doppelklicken und die Ansicht dann etwas vergrößern:</span><span class="sxs-lookup"><span data-stu-id="bc515-187">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again:</span></span>

<span data-ttu-id="bc515-188">Zum Interagieren und zum Greifen eines Objekts mit Handtracking muss das Objekt über eine Collider-Komponente (etwa eine Komponente vom Typ **Box Collider** (Feld-Collider)), eine Komponente vom Typ **Object Manipulator (Script)** (Objektmanipulator (Skript)) und eine **NearInteractionGrabbable(Script)** -Komponente verfügen.</span><span class="sxs-lookup"><span data-stu-id="bc515-188">To interact and grab an object with tracked hands, the object must have Collider component for example a **Box Collider**,  **Object Manipulator (Script)** component and **NearInteractionGrabbable(Script)** component.</span></span>

<span data-ttu-id="bc515-189">Klicken Sie bei im Hierarchiefenster ausgewähltem **Cube**-Objekt im Inspektorfenster auf die Schaltfläche **Komponente hinzufügen**, suchen Sie nach dem Skript **Objektmanipulator**, und wählen Sie es aus, um das Objektmanipulatorskript dem Cube-Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bc515-189">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![Hinzufügen des Objektmanipulators zum Cube](images/mr-learning-base/base-02-section8-step1-2.png)

<span data-ttu-id="bc515-191">Wiederholen Sie diesen Vorgang, um dem Cube eine Komponente vom Typ **Near Interaction Grabbable (Script)** (Nah-Interaktion, berührbar (Skript)) hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bc515-191">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![Hinzufügen von „Near Interaction Grabbable (Script)“ (Nah-Interaktion, berührbar (Skript)) zum Cube](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> <span data-ttu-id="bc515-193">Wenn Sie einen Objektmanipulator (Skript) hinzufügen, wird in diesem Fall der Einschränkungs-Manager (Skript) automatisch hinzugefügt, weil der Objektmanipulator (Skript) davon abhängt.</span><span class="sxs-lookup"><span data-stu-id="bc515-193">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="bc515-194">Im Rahmen dieses Tutorials wurden dem Cube-Objekt bereits Collider hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="bc515-194">For the purpose of this tutorial, colliders have already been added to the Cube Object.</span></span> <span data-ttu-id="bc515-195">Weitere Informationen zu Collidern finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collidern</a>.</span><span class="sxs-lookup"><span data-stu-id="bc515-195">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

<span data-ttu-id="bc515-196">Zum Testen im Unity-Editor können Sie in den Spielmodus wechseln und die **LeftShift**-Taste oder die **Leertaste** gedrückt halten, um den Controller zu aktivieren. Durch die Mausbewegung wird der Controller bewegt, und mithilfe des Mausrads ist zudem eine Bewegung weiter weg von der Kamera bzw. näher hin zur Kamera möglich.</span><span class="sxs-lookup"><span data-stu-id="bc515-196">To test this in the Unity editor, you can enter the play mode and hold the **LeftShift** or **Space** key to enable the controller, Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="bc515-197">Wenn sich der Zeiger auf dem Cube befindet, halten Sie die **rechte Maustaste** gedrückt, um das Cube-Objekt zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="bc515-197">Once the pointer is on the Cube  press and hold **Right Mouse Button** to move the the Cube object.</span></span>

![Spielmodus](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="bc515-199">Erstellen Ihrer Anwendung auf der HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bc515-199">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="bc515-200">1. Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="bc515-200">1. Build the Unity project</span></span>

<span data-ttu-id="bc515-201">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="bc515-201">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="bc515-202">Klicken Sie im Build Settings-Fenster (Buildeinstellungen) auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um der Liste **Scenes In Build** (Szenen im Build) Ihre aktuelle Szene hinzuzufügen, und klicken Sie dann auf die Schaltfläche **Build** (Erstellen), um das Build Universal Windows Platform-Fenster (Erstellen für Universelle Windows-Plattform) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bc515-202">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Unity-Fenster „Build Settings“ mit ausgewählter UWP](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="bc515-204">Wählen Sie im Build Universal Windows Platform-Fenster einen passenden Speicherort aus, um Ihren Build zu speichern, beispielsweise _D:\MixedRealityLearning\Builds_, erstellen Sie einen neuen Ordner mit einem passenden Namen, z. B. _GettingStarted_, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:</span><span class="sxs-lookup"><span data-stu-id="bc515-204">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Auswählen eines Ordners](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="bc515-206">Warten Sie, bis Unity den Buildvorgang abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="bc515-206">Wait for Unity to finish the build process:</span></span>

![Unity: Buildvorgang wird ausgeführt](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="bc515-208">2. Erstellen und Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="bc515-208">2. Build and deploy the application</span></span>

<span data-ttu-id="bc515-209">Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="bc515-209">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="bc515-210">Navigieren Sie zum Ordner, und doppelklicken Sie auf die Projektmappendatei, um sie in Visual Studio zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="bc515-210">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Windows-Explorer mit neu erstellter, ausgewählter Visual Studio-Projektmappe](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="bc515-212">Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation **[Installieren der Tools](../../install-the-tools.md)** angegeben) installiert sind.</span><span class="sxs-lookup"><span data-stu-id="bc515-212">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="bc515-213">Konfigurieren Sie Visual Studio für HoloLens 2, indem Sie die **Master**- oder **Release**-Konfiguration, die **ARM64**-Architektur und **Gerät** als Ziel auswählen:</span><span class="sxs-lookup"><span data-stu-id="bc515-213">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio, konfiguriert für die Bereitstellung in HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="bc515-215">Wenn Sie auf HoloLens (1. Generation) bereitstellen, wählen Sie die **x86**-Architektur aus.</span><span class="sxs-lookup"><span data-stu-id="bc515-215">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="bc515-216">Für HoloLens erstellen Sie normalerweise für die ARM-Architektur.</span><span class="sxs-lookup"><span data-stu-id="bc515-216">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="bc515-217">Jedoch besteht ein <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>bekanntes Problem</strong></a> in Unity 2019.3, das zu Fehlern führt, wenn ARM in Visual Studio als Buildarchitektur ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="bc515-217">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="bc515-218">Die empfohlene Umgehung besteht darin, Builds für ARM64 zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bc515-218">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="bc515-219">Wenn diese Option nicht in Frage kommt, navigieren Sie zu **Edit > Project Settings > Player > Other Settings** (Bearbeiten > Projekteinstellungen > Player > Weitere Einstellungen), und deaktivieren Sie **Graphics Jobs** (Grafikaufträge).</span><span class="sxs-lookup"><span data-stu-id="bc515-219">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="bc515-220">Wenn „Device“ (Gerät) nicht als Zieloption angezeigt wird, müssen Sie möglicherweise das Startprojekt für die Visual Studio-Projektmappe vom Projekt „IL2CPP“ zum Projekt „UWP“ ändern.</span><span class="sxs-lookup"><span data-stu-id="bc515-220">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="bc515-221">Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf den Namen Ihres Projekts (Universal Windows), und wählen Sie **Set as StartUp Project** (Als Startprojekt festlegen) aus.</span><span class="sxs-lookup"><span data-stu-id="bc515-221">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="bc515-222">Verbinden Sie Ihre HoloLens mit Ihrem Computer, wählen Sie dann **Debug** > **Start Without Debugging** (Debuggen > Ohne Debuggen starten) aus, um zu erstellen und auf Ihrem Gerät bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="bc515-222">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio-Menüpfad für „Ohne Debuggen starten“](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="bc515-224">Bevor Sie den Build für Ihr Gerät erstellen, muss das Gerät in den Entwicklermodus versetzt und mit Ihrem Entwicklungscomputer gekoppelt werden.</span><span class="sxs-lookup"><span data-stu-id="bc515-224">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="bc515-225">Sie können beide Schritte ausführen, indem Sie [diese Anweisungen](../../platform-capabilities-and-apis/using-visual-studio.md) befolgen.</span><span class="sxs-lookup"><span data-stu-id="bc515-225">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="bc515-226">Sie können auch auf dem [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) bereitstellen oder ein [App-Paket](/windows/uwp/packaging/packaging-uwp-apps) zum Querladen erstellen.</span><span class="sxs-lookup"><span data-stu-id="bc515-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="bc515-227">Bei der Option „Start Without Debugging“ (Ohne Debuggen starten) wird die App auf Ihrem Gerät automatisch ohne angefügten Visual Studio-Debugger gestartet.</span><span class="sxs-lookup"><span data-stu-id="bc515-227">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="bc515-228">Wählen Sie **Build > Deploy Solution** (Erstellen > Projektmappe bereitstellen) aus, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="bc515-228">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="bc515-229">Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **Toggle Diagnostics** (Diagnose ein-/ausschalten) ein- und ausblenden.</span><span class="sxs-lookup"><span data-stu-id="bc515-229">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="bc515-230">Es empfiehlt sich, während der Entwicklung den Profiler die meiste Zeit anzuzeigen, um zu verstehen, wann Änderungen an der App die Leistung beeinträchtigen können.</span><span class="sxs-lookup"><span data-stu-id="bc515-230">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="bc515-231">Beispielsweise sollten HoloLens-Apps [durchgängig bei 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bc515-231">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="bc515-232">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="bc515-232">Congratulations</span></span>

<span data-ttu-id="bc515-233">Sie haben jetzt Ihre erste HoloLens-App bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="bc515-233">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="bc515-234">Nach dem Öffnen der App sollte vor Ihnen ein Cube-Objekt angezeigt werden. Sie sollten durch Verschieben mit dem Cube interagieren können, und beim Herumlaufen sollte ein Gittermodell für die Raumzuordnung angezeigt werden, das die von HoloLens erkannten Oberflächen bedeckt.</span><span class="sxs-lookup"><span data-stu-id="bc515-234">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="bc515-235">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.</span><span class="sxs-lookup"><span data-stu-id="bc515-235">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="bc515-236">Diese Features sind nur einige der grundlegenden Bestandteile von MRTK.</span><span class="sxs-lookup"><span data-stu-id="bc515-236">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="bc515-237">In den bevorstehenden Tutorials fügen Sie Ihrer Szene Inhalte hinzu, um die Funktionen von HoloLens und des MRTK kennenzulernen.</span><span class="sxs-lookup"><span data-stu-id="bc515-237">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bc515-238">Nächstes Tutorial: 3. Konfigurieren der MRTK-Profile</span><span class="sxs-lookup"><span data-stu-id="bc515-238">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)