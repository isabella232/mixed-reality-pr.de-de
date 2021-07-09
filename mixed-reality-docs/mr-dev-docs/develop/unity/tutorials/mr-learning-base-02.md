---
title: Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie Ihr Unity-Projekt für das Mixed Reality Toolkit (MRTK) konfigurieren und es in Ihrer HoloLens 2 bereitstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176024"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="d1348-104">2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="d1348-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="d1348-105">In diesem Tutorial erfahren Sie, wie Sie ein neues Unity-Projekt erstellen, es für die Entwicklung mit dem Mixed Reality Toolkit (MRTK) konfigurieren und das MRTK importieren.</span><span class="sxs-lookup"><span data-stu-id="d1348-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="d1348-106">Außerdem werden Sie durch Konfiguration, Erstellung und Bereitstellung einer einfachen Unity-Szene aus Visual Studio auf Ihrer HoloLens 2 geführt.</span><span class="sxs-lookup"><span data-stu-id="d1348-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="d1348-107">Nachdem Sie diese auf Ihrer HoloLens 2 bereitgestellt haben, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="d1348-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="d1348-108">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.</span><span class="sxs-lookup"><span data-stu-id="d1348-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="d1348-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="d1348-109">Objectives</span></span>

* <span data-ttu-id="d1348-110">Erfahren, wie Unity für die HoloLens-Entwicklung konfiguriert wird</span><span class="sxs-lookup"><span data-stu-id="d1348-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="d1348-111">Erfahren, wie Ihre App erstellt und in HoloLens bereitgestellt wird</span><span class="sxs-lookup"><span data-stu-id="d1348-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="d1348-112">Kennenlernen des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers auf dem HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="d1348-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

### <a name="steps-overview"></a><span data-ttu-id="d1348-113">Übersicht der Schritte</span><span class="sxs-lookup"><span data-stu-id="d1348-113">Steps overview</span></span>
:::row:::
    :::column:::
       <span data-ttu-id="d1348-114">![Übersicht Schritt 1](images/mr-learning-base/base-02-overview-step1.png) **1. Erstellen eines neuen Unity-Projekts**</span><span class="sxs-lookup"><span data-stu-id="d1348-114">![Overview Step 1](images/mr-learning-base/base-02-overview-step1.png) **1. Create a new Unity project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d1348-115">![Übersicht Schritt 2](images/mr-learning-base/base-02-overview-step2.png) **2. Importieren des MRTK in das Projekt**</span><span class="sxs-lookup"><span data-stu-id="d1348-115">![Overview Step 2](images/mr-learning-base/base-02-overview-step2.png) **2. Import MRTK into the project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d1348-116">![Übersicht Schritt 3](images/mr-learning-base/base-02-overview-step3.png) **3. Konfigurieren einer neuen Szene mit MRTK**</span><span class="sxs-lookup"><span data-stu-id="d1348-116">![Overview Step 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configure a new scene with MRTK**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       <span data-ttu-id="d1348-117">![Übersicht Schritt 4](images/mr-learning-base/base-02-overview-step4.png) **4. Erstellen des Unity-Projekts**</span><span class="sxs-lookup"><span data-stu-id="d1348-117">![Overview Step 4](images/mr-learning-base/base-02-overview-step4.png) **4. Build Unity Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d1348-118">![Übersicht Schritt 5](images/mr-learning-base/base-02-overview-step5.png) **5. Erstellen des UWP-Projekts**</span><span class="sxs-lookup"><span data-stu-id="d1348-118">![Overview Step 5](images/mr-learning-base/base-02-overview-step5.png) **5. Build UWP Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d1348-119">![Übersicht Schritt 6](images/mr-learning-base/base-02-overview-step6.png) **6. Ausführen des Projekts auf dem Gerät**</span><span class="sxs-lookup"><span data-stu-id="d1348-119">![Overview Step 6](images/mr-learning-base/base-02-overview-step6.png) **6. Run Project on the Device**</span></span>
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a><span data-ttu-id="d1348-120">Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="d1348-120">Creating the Unity project</span></span>

<span data-ttu-id="d1348-121">Starten Sie **Unity Hub**, wählen Sie die Registerkarte **Projects** (Projekte) aus, und klicken Sie auf den **Abwärtspfeil** neben der Schaltfläche **New** (Neu):</span><span class="sxs-lookup"><span data-stu-id="d1348-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

<span data-ttu-id="d1348-122">Wählen Sie in der Dropdownliste die Unity-**Version** aus, die oben in den [Voraussetzungen](mr-learning-base-01.md#prerequisites) angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="d1348-122">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> <span data-ttu-id="d1348-123">Wenn diese bestimmte Unity-Version nicht auf dem Unity Hub verfügbar ist, können Sie die Installation aus dem <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Downloadarchiv</a> von Unity einleiten.</span><span class="sxs-lookup"><span data-stu-id="d1348-123">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="d1348-124">Erstellen Sie im Fenster ein neues Projekt:</span><span class="sxs-lookup"><span data-stu-id="d1348-124">In the Create a new project window:</span></span>

* <span data-ttu-id="d1348-125">Vergewissern Sie sich, dass **Templates** (Vorlagen) auf **3D** festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="d1348-125">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="d1348-126">Geben Sie einen passenden **Project Name** (Projektnamen) ein, z. B. _MRTK-Tutorials_</span><span class="sxs-lookup"><span data-stu-id="d1348-126">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="d1348-127">Wählen Sie eine geeignete **Location** (Speicherort) zum Speichern Ihres Projekts, z. B. _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="d1348-127">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="d1348-128">Klicken Sie auf die Schaltfläche **Create** (Erstellen), um das neue Unity-Projekt zu erstellen</span><span class="sxs-lookup"><span data-stu-id="d1348-128">Click the **Create** button to create and launch your new Unity project</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> <span data-ttu-id="d1348-129">Wenn Sie unter Windows arbeiten, müssen Sie den MAX_PATH-Grenzwert von 255 Zeichen beachten.</span><span class="sxs-lookup"><span data-stu-id="d1348-129">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="d1348-130">Daher sollten Sie das Unity-Projekt in der Nähe des Stammverzeichnisses des Laufwerks speichern.</span><span class="sxs-lookup"><span data-stu-id="d1348-130">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="d1348-131">Warten Sie, bis Unity das Projekt erstellt hat:</span><span class="sxs-lookup"><span data-stu-id="d1348-131">Wait for Unity to create the project:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a><span data-ttu-id="d1348-132">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="d1348-132">Switching the build platform</span></span>

<span data-ttu-id="d1348-133">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="d1348-133">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity: Build Settings... Menüpfad](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="d1348-135">Wählen Sie im Build Settings-Fenster **Universelle Windows-Plattform** aus, und:</span><span class="sxs-lookup"><span data-stu-id="d1348-135">In the Build Settings window, select **Universal Windows Platform** and:</span></span>

1. <span data-ttu-id="d1348-136">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="d1348-136">Set **Target device** to **HoloLens**</span></span>
2. <span data-ttu-id="d1348-137">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="d1348-137">Set **Architecture** to **ARM 64**</span></span> 
3. <span data-ttu-id="d1348-138">Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.</span><span class="sxs-lookup"><span data-stu-id="d1348-138">Set **Build Type** to **D3D Project**</span></span>
4. <span data-ttu-id="d1348-139">Legen Sie **SDK-Zielversion** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="d1348-139">Set **Target SDK Version** to **Latest Installed**</span></span>
5. <span data-ttu-id="d1348-140">Legen Sie **Mindestplattformversion** auf **10.0.1024.0** fest</span><span class="sxs-lookup"><span data-stu-id="d1348-140">Set **Minimum Platform Version** to **10.0.1024.0**</span></span>
6. <span data-ttu-id="d1348-141">Legen Sie **Visual Studio-Version** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="d1348-141">Set **Visual Studio Version** to **Latest installed**</span></span>
7. <span data-ttu-id="d1348-142">Legen Sie **Build and Run on** (Erstellen und Ausführen auf) auf **USB-Gerät** fest</span><span class="sxs-lookup"><span data-stu-id="d1348-142">Set **Build and Run on** to **USB Device**</span></span>
8. <span data-ttu-id="d1348-143">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="d1348-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9. <span data-ttu-id="d1348-144">Klicken Sie auf die Schaltfläche „Plattform wechseln“.</span><span class="sxs-lookup"><span data-stu-id="d1348-144">Click the Switch Platform button</span></span>

![Unity-Buildeinstellungen mit festgelegten Einstellungen für die Universelle Windows-Plattform](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="d1348-146">Warten Sie, bis Unity den Wechsel der Plattform abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="d1348-146">Wait for Unity to finish switching the platform:</span></span>

![Unity: Wechsel der Plattform in Bearbeitung](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

<span data-ttu-id="d1348-148">Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das **x**-Symbol, um das Fenster mit den Buildeinstellungen zu schließen.</span><span class="sxs-lookup"><span data-stu-id="d1348-148">When Unity has finished switching the platform, click the  **x** icon to close the Build Settings window.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="d1348-149">Importieren des Mixed Reality Toolkits und Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="d1348-149">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="d1348-150">Zum Importieren des Mixed Reality-Toolkits in das Unity-Projekt müssen Sie das [Mixed Reality-Featuretool verwenden](../welcome-to-mr-feature-tool.md), das Entwicklern das Erkennen, Aktualisieren und Hinzufügen von Mixed Reality-Featurepaketen zu Unity-Projekten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="d1348-150">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="d1348-151">Sie können Pakete vor dem Importieren nach Name oder Kategorie durchsuchen, ihre Abhängigkeiten anzeigen und sogar Änderungsvorschläge für Ihre Projektmanifestdatei anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d1348-151">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="d1348-152">Laden Sie die neueste Version des Mixed Reality-Featuretools aus dem [Microsoft Download Center](https://aka.ms/MRFeatureTool) herunter. Wenn der Download abgeschlossen ist, entpacken Sie die Datei, und speichern Sie sie auf Ihrem Desktop.</span><span class="sxs-lookup"><span data-stu-id="d1348-152">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="d1348-153">Installieren Sie [.NET 5.0 Runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer), damit Sie das Mixed Reality-Featuretool ausführen können.</span><span class="sxs-lookup"><span data-stu-id="d1348-153">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span></span>

<span data-ttu-id="d1348-154">Öffnen Sie die ausführbare Datei **MixedRealityFeatureTool** aus dem heruntergeladenen Ordner, um das Mixed Reality-Featuretool zu starten.</span><span class="sxs-lookup"><span data-stu-id="d1348-154">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="d1348-155">Erstellen der Szene und Konfigurieren des MRTK</span><span class="sxs-lookup"><span data-stu-id="d1348-155">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="d1348-156">Wählen Sie im Unity-Menü **Datei** > **Neue Szene** aus:</span><span class="sxs-lookup"><span data-stu-id="d1348-156">In the Unity menu, select **File** > **New Scene**:</span></span>

![Unity: Menüpfad für „New Scene“](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="d1348-158">Wählen Sie im Fenster **Neue Szene** die Option **Basic (integriert)** aus, und klicken Sie auf **Erstellen**, um eine neue Szene zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="d1348-158">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Unity-Fenster „Neue Szene“](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="d1348-160">Der obige Screenshot stammt aus Unity, Version 2020. Wenn Sie Unity 2019 verwenden und auf **Erstellen** klicken, wird eine neue leere Szene erstellt.</span><span class="sxs-lookup"><span data-stu-id="d1348-160">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="d1348-161">Wählen Sie im Unity-Menü **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** (Mixed Reality > Toolkit > Zu Szene hinzufügen und konfigurieren) aus, um Ihrer aktuellen Szene das MRTK hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="d1348-161">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity: Menüpfad zu „Add to Scene and Configure...“](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="d1348-163">Überprüfen Sie bei im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster, ob das Konfigurationsprofil des **Mixed Reality-Toolkits** auf **DefaultMixedRealityToolkitConfigurationProfile** festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="d1348-163">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![MixedRealityToolkit-Komponente von Unity mit ausgewähltem DefaultMixedRealityTookitConfigurationProfile](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="d1348-165">Wählen Sie im Unity-Menü **File** > **Save As...** (Datei > Speichern unter...) aus, um das Save Scene-Fenster (Szene speichern) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="d1348-165">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity: Menüpfad für „Save As...“](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="d1348-167">Speichern Sie die Szene in Ihrem Projekt unter **Asset** > **Scenes** (Ressourcen > Szenen).</span><span class="sxs-lookup"><span data-stu-id="d1348-167">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Unity: Aufforderungsfenster zum Speichern der Szene](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a><span data-ttu-id="d1348-169">Hinzufügen von Handinteraktion zu einem Objekt</span><span class="sxs-lookup"><span data-stu-id="d1348-169">Adding hand interaction to an object</span></span>

<span data-ttu-id="d1348-170">Wählen Sie im Unity-Menü **GameObject** > **3D Object** > **Cube** aus, um der Szene ein Cube-Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="d1348-170">In the Unity menu, select **GameObject** > **3D Object** > **Cube** to add a cube object to the scene.</span></span>

![Hinzufügen eines Cube-Objekts zur Szene](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="d1348-172">Klicken Sie im Hierarchiefenster auf das **Cube**-Objekt, und konfigurieren Sie dann im Inspektorfenster die **Transform**-Komponente (Transformation) wie folgt.</span><span class="sxs-lookup"><span data-stu-id="d1348-172">Click the **Cube** object in the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="d1348-173">**Position**: X = 0, Y = -0.1, Z = 0.5</span><span class="sxs-lookup"><span data-stu-id="d1348-173">**Position**: X = 0, Y = -0.1, Z = 0.5</span></span>
* <span data-ttu-id="d1348-174">**Drehung**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="d1348-174">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="d1348-175">**Skalierung:** X = 0.1, Y = 0.1, Z = 0.1</span><span class="sxs-lookup"><span data-stu-id="d1348-175">**Scale**: X = 0.1, Y = 0.1, Z = 0.1</span></span>

<span data-ttu-id="d1348-176">1 Unity-Einheit ist 1 Meter.</span><span class="sxs-lookup"><span data-stu-id="d1348-176">1 Unity unit is 1 meter.</span></span> <span data-ttu-id="d1348-177">Wir haben die Größe des Cubes auf 10x10x10 cm aktualisiert und 50 cm von der Headsetposition (0,0,0) entfernt platziert.</span><span class="sxs-lookup"><span data-stu-id="d1348-177">We have updated cube's size to 10x10x10 cm, placed at 50cm from the headset position (0,0,0).</span></span> <span data-ttu-id="d1348-178">10 cm unterhalb der Augenhöhe für eine komfortable Interaktion.</span><span class="sxs-lookup"><span data-stu-id="d1348-178">10cm below the eye level for comfortable interaction.</span></span> 

<span data-ttu-id="d1348-179">Wenn Sie die Standardskala (1,1,1) verwenden, ist der Cube zu groß.</span><span class="sxs-lookup"><span data-stu-id="d1348-179">If you use the default scale (1,1,1), the cube will be too big.</span></span> <span data-ttu-id="d1348-180">Wenn Sie die Standardposition (0,0,0) verwenden, wird der Cube an derselben Position wie Ihr Headset platziert, und Sie können ihn erst sehen, wenn Sie sich rückwärts bewegen.</span><span class="sxs-lookup"><span data-stu-id="d1348-180">If you use the default position (0,0,0), the cube will be placed at the same position as your headset and you won't be able to see it until you move backward.</span></span>

![Anpassen von Transformationsinformationen](images/mr-learning-base/base-02-section8-step1-1b.png)

<span data-ttu-id="d1348-182">Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **Cube**-Objekt doppelklicken und die Ansicht dann wieder etwas vergrößern.</span><span class="sxs-lookup"><span data-stu-id="d1348-182">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again.</span></span> <span data-ttu-id="d1348-183">Oder Sie können die F-Taste verwenden, um das Objekt zu vergrößern und sich darauf zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="d1348-183">Or you can use F key to zoom and focus on the object.</span></span>

<span data-ttu-id="d1348-184">Um mit verfolgten Händen mit einem Objekt zu interagieren und es zu greifen, muss das Objekt folgende Komponenten aufweisen:</span><span class="sxs-lookup"><span data-stu-id="d1348-184">To interact and grab an object with tracked hands, the object must have:</span></span>
 * <span data-ttu-id="d1348-185">Collider-Komponente wie **Box Collider** (der Cube von Unity verfügt bereits standardmäßig über einen Box Collider)</span><span class="sxs-lookup"><span data-stu-id="d1348-185">Collider component such as **Box Collider** (Unity's cube already has a Box Collider by default)</span></span>
 * <span data-ttu-id="d1348-186">**Object Manipulator (Script)** -Komponente</span><span class="sxs-lookup"><span data-stu-id="d1348-186">**Object Manipulator (Script)** component</span></span>
 * <span data-ttu-id="d1348-187">**NearInteractionGrabbable(Script)-Komponente**</span><span class="sxs-lookup"><span data-stu-id="d1348-187">**NearInteractionGrabbable(Script)** component</span></span>

<span data-ttu-id="d1348-188">Durch das **ObjectManipulator**-Skript des MRTK wird ein Objekt mit einer oder zwei Händen verschiebbar, skalierbar und drehbar.</span><span class="sxs-lookup"><span data-stu-id="d1348-188">MRTK's **ObjectManipulator** script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="d1348-189">Dieses Skript unterstützt das Eingabemodell der direkten Manipulation, da das Skript dem Benutzer die Möglichkeit gibt, Hologramme direkt mit den Händen zu berühren.</span><span class="sxs-lookup"><span data-stu-id="d1348-189">This script supports the direct manipulation input model as the script enables the user to touch holograms directly with their hands.</span></span>

<span data-ttu-id="d1348-190">Klicken Sie bei im Hierarchiefenster ausgewähltem **Cube**-Objekt im Inspektorfenster auf die Schaltfläche **Komponente hinzufügen**, suchen Sie nach dem Skript **Objektmanipulator**, und wählen Sie es aus, um das Objektmanipulatorskript dem Cube-Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="d1348-190">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![Hinzufügen des Objektmanipulators zum Cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="d1348-192">Wiederholen Sie diesen Vorgang, um dem Cube eine Komponente vom Typ **Near Interaction Grabbable (Script)** (Nah-Interaktion, berührbar (Skript)) hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="d1348-192">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![Hinzufügen von „Near Interaction Grabbable (Script)“ (Nah-Interaktion, berührbar (Skript)) zum Cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="d1348-194">Wenn Sie einen Objektmanipulator (Skript) hinzufügen, wird in diesem Fall der Einschränkungs-Manager (Skript) automatisch hinzugefügt, weil der Objektmanipulator (Skript) davon abhängt.</span><span class="sxs-lookup"><span data-stu-id="d1348-194">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a><span data-ttu-id="d1348-195">Testen Ihrer Anwendung im Unity-Editor mit MRTK-Eingabesimulation</span><span class="sxs-lookup"><span data-stu-id="d1348-195">Testing your application in Unity editor with MRTK input simulation</span></span>

<span data-ttu-id="d1348-196">Mit der Eingabesimulation des MRTK können Sie verschiedene Arten von Interaktionen im Unity-Editor testen, ohne erstellen und auf einem Gerät bereitstellen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="d1348-196">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="d1348-197">Auf diese Weise können Sie Ihre Ideen im Entwurfs- und Entwicklungsprozess schnell iterieren.</span><span class="sxs-lookup"><span data-stu-id="d1348-197">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="d1348-198">Verwenden Sie Kombinationen aus Tastatur- und Mauseingaben, um simulierte Eingaben zu steuern.</span><span class="sxs-lookup"><span data-stu-id="d1348-198">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="d1348-199">Klicken Sie auf die Schaltfläche „Wiedergeben“, und wechseln Sie in den Wiedergabemodus.</span><span class="sxs-lookup"><span data-stu-id="d1348-199">Click the play button and enter the play mode.</span></span> <span data-ttu-id="d1348-200">Halten Sie die **linke UMSCHALTTASTE** oder die **LEERTASTE** gedrückt, um den Controller (simulierte Hände) aufzurufen. Der Controller lässt sich per Mausbewegung bewegen, und er kann mit dem Mausrad weiter von der Kamera weg oder näher zur Kamera hin bewegt werden.</span><span class="sxs-lookup"><span data-stu-id="d1348-200">Hold the **Left Shift** or **Space** key to bring up the controller (simulated hands), Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="d1348-201">Wenn sich der Zeiger auf dem Cube befindet, halten Sie die **linke Maustaste** gedrückt, um das Cube-Objekt zu greifen.</span><span class="sxs-lookup"><span data-stu-id="d1348-201">Once the pointer is on the Cube press and hold **Left Mouse Button** to grab the Cube object.</span></span>

* <span data-ttu-id="d1348-202">Drücken Sie die Tasten **W, A, S, D, Q, E**, um die Kamera zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="d1348-202">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="d1348-203">Halten Sie die **rechte Maustaste** gedrückt, und bewegen Sie die Maus, um sich umzusehen.</span><span class="sxs-lookup"><span data-stu-id="d1348-203">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="d1348-204">Um die simulierten Hände aufzurufen, drücken Sie die **LEERTASTE (rechte Hand)** oder die **linke UMSCHALTTASTE (linke Hand)** .</span><span class="sxs-lookup"><span data-stu-id="d1348-204">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="d1348-205">Um die simulierten Hände im Blickfeld zu halten, drücken Sie die Taste **T** oder **Y**.</span><span class="sxs-lookup"><span data-stu-id="d1348-205">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="d1348-206">Um simulierte Hände zu drehen, drücken und halten Sie die **STRG**-TASTE gedrückt, und bewegen Sie die Maus.</span><span class="sxs-lookup"><span data-stu-id="d1348-206">To rotate simulated hands, press and hold **Ctrl** key and move mouse</span></span>

![Spielmodus](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="d1348-208">Erstellen Ihrer Anwendung auf der HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d1348-208">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="d1348-209">1. Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="d1348-209">1. Build the Unity project</span></span>

<span data-ttu-id="d1348-210">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d1348-210">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="d1348-211">Klicken Sie im Build Settings-Fenster (Buildeinstellungen) auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um der Liste **Scenes In Build** (Szenen im Build) Ihre aktuelle Szene hinzuzufügen, und klicken Sie dann auf die Schaltfläche **Build** (Erstellen), um das Build Universal Windows Platform-Fenster (Erstellen für Universelle Windows-Plattform) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="d1348-211">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Unity-Fenster „Build Settings“ mit ausgewählter UWP](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="d1348-213">Wählen Sie im Build Universal Windows Platform-Fenster einen passenden Speicherort aus, um Ihren Build zu speichern, beispielsweise _D:\MixedRealityLearning\Builds_, erstellen Sie einen neuen Ordner mit einem passenden Namen, z. B. _GettingStarted_, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:</span><span class="sxs-lookup"><span data-stu-id="d1348-213">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Auswählen eines Ordners](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="d1348-215">Warten Sie, bis Unity den Buildvorgang abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="d1348-215">Wait for Unity to finish the build process:</span></span>

![Unity: Buildvorgang wird ausgeführt](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="d1348-217">2. Erstellen und Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="d1348-217">2. Build and deploy the application</span></span>

<span data-ttu-id="d1348-218">Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="d1348-218">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="d1348-219">Navigieren Sie zum Ordner, und doppelklicken Sie auf die Projektmappendatei, um sie in Visual Studio zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="d1348-219">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Windows-Explorer mit neu erstellter, ausgewählter Visual Studio-Projektmappe](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d1348-221">Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation **[Installieren der Tools](../../install-the-tools.md)** angegeben) installiert sind.</span><span class="sxs-lookup"><span data-stu-id="d1348-221">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="d1348-222">Konfigurieren Sie Visual Studio für HoloLens 2, indem Sie die **Master**- oder **Release**-Konfiguration, die **ARM64**-Architektur und **Gerät** als Ziel auswählen:</span><span class="sxs-lookup"><span data-stu-id="d1348-222">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio, konfiguriert für die Bereitstellung in HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="d1348-224">Wenn Sie auf HoloLens (1. Generation) bereitstellen, wählen Sie die **x86**-Architektur aus.</span><span class="sxs-lookup"><span data-stu-id="d1348-224">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="d1348-225">Für HoloLens erstellen Sie normalerweise für die ARM-Architektur.</span><span class="sxs-lookup"><span data-stu-id="d1348-225">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="d1348-226">Jedoch besteht ein <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>bekanntes Problem</strong></a> in Unity 2019.3, das zu Fehlern führt, wenn ARM in Visual Studio als Buildarchitektur ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="d1348-226">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="d1348-227">Die empfohlene Umgehung besteht darin, Builds für ARM64 zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d1348-227">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="d1348-228">Wenn diese Option nicht in Frage kommt, navigieren Sie zu **Edit > Project Settings > Player > Other Settings** (Bearbeiten > Projekteinstellungen > Player > Weitere Einstellungen), und deaktivieren Sie **Graphics Jobs** (Grafikaufträge).</span><span class="sxs-lookup"><span data-stu-id="d1348-228">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="d1348-229">Wenn „Device“ (Gerät) nicht als Zieloption angezeigt wird, müssen Sie möglicherweise das Startprojekt für die Visual Studio-Projektmappe vom Projekt „IL2CPP“ zum Projekt „UWP“ ändern.</span><span class="sxs-lookup"><span data-stu-id="d1348-229">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="d1348-230">Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf den Namen Ihres Projekts (Universal Windows), und wählen Sie **Set as StartUp Project** (Als Startprojekt festlegen) aus.</span><span class="sxs-lookup"><span data-stu-id="d1348-230">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="d1348-231">Verbinden Sie Ihre HoloLens mit Ihrem Computer, wählen Sie dann **Debug** > **Start Without Debugging** (Debuggen > Ohne Debuggen starten) aus, um zu erstellen und auf Ihrem Gerät bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="d1348-231">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio-Menüpfad für „Ohne Debuggen starten“](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="d1348-233">Bevor Sie den Build für Ihr Gerät erstellen, muss das Gerät in den Entwicklermodus versetzt und mit Ihrem Entwicklungscomputer gekoppelt werden.</span><span class="sxs-lookup"><span data-stu-id="d1348-233">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="d1348-234">Sie können beide Schritte ausführen, indem Sie [diese Anweisungen](../../platform-capabilities-and-apis/using-visual-studio.md) befolgen.</span><span class="sxs-lookup"><span data-stu-id="d1348-234">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="d1348-235">Sie können auch auf dem [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) bereitstellen oder ein [App-Paket](/windows/uwp/packaging/packaging-uwp-apps) zum Querladen erstellen.</span><span class="sxs-lookup"><span data-stu-id="d1348-235">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="d1348-236">Bei der Option „Start Without Debugging“ (Ohne Debuggen starten) wird die App auf Ihrem Gerät automatisch ohne angefügten Visual Studio-Debugger gestartet.</span><span class="sxs-lookup"><span data-stu-id="d1348-236">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="d1348-237">Wählen Sie **Build > Deploy Solution** (Erstellen > Projektmappe bereitstellen) aus, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="d1348-237">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="d1348-238">Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **„Toggle Diagnostics“** (Diagnose umschalten) ein- und ausblenden.</span><span class="sxs-lookup"><span data-stu-id="d1348-238">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **"Toggle Diagnostics"**.</span></span> <span data-ttu-id="d1348-239">Es empfiehlt sich, während der Entwicklung den Profiler die meiste Zeit anzuzeigen, um zu verstehen, wann Änderungen an der App die Leistung beeinträchtigen können.</span><span class="sxs-lookup"><span data-stu-id="d1348-239">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="d1348-240">Beispielsweise sollten HoloLens-Apps [durchgängig bei 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d1348-240">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="d1348-241">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="d1348-241">Congratulations</span></span>

<span data-ttu-id="d1348-242">Sie haben jetzt Ihre erste HoloLens-App bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="d1348-242">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="d1348-243">Nach dem Öffnen der App sollte vor Ihnen ein Cube-Objekt angezeigt werden. Sie sollten durch Verschieben mit dem Cube interagieren können, und beim Herumlaufen sollte ein Gittermodell für die Raumzuordnung angezeigt werden, das die von HoloLens erkannten Oberflächen bedeckt.</span><span class="sxs-lookup"><span data-stu-id="d1348-243">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="d1348-244">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.</span><span class="sxs-lookup"><span data-stu-id="d1348-244">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="d1348-245">Diese Features sind nur einige der grundlegenden Bestandteile von MRTK.</span><span class="sxs-lookup"><span data-stu-id="d1348-245">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="d1348-246">In den bevorstehenden Tutorials fügen Sie Ihrer Szene Inhalte hinzu, um die Funktionen von HoloLens und des MRTK kennenzulernen.</span><span class="sxs-lookup"><span data-stu-id="d1348-246">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d1348-247">Nächstes Tutorial: 3. Konfigurieren der MRTK-Profile</span><span class="sxs-lookup"><span data-stu-id="d1348-247">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
