---
title: 'MRTK-Tutorials: 2 Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung'
description: In diesem Kurs erfahren Sie, wie Sie Ihr Unity-Projekt für das Mixed Reality Toolkit (MRTK) konfigurieren und es in Ihrer HoloLens 2 bereitstellen.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859529"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="10693-105">2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="10693-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="10693-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="10693-106">Overview</span></span>

<span data-ttu-id="10693-107">In diesem Tutorial erfahren Sie, wie Sie ein neues Unity-Projekt erstellen, es für die Entwicklung mit dem <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> konfigurieren und das MRTK importieren.</span><span class="sxs-lookup"><span data-stu-id="10693-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="10693-108">Außerdem werden Sie durch Konfiguration, Erstellung und Bereitstellung einer einfachen Unity-Szene aus Visual Studio auf Ihrer HoloLens 2 geführt.</span><span class="sxs-lookup"><span data-stu-id="10693-108">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="10693-109">Nachdem Sie diese auf Ihrer HoloLens 2 bereitgestellt haben, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="10693-109">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="10693-110">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.</span><span class="sxs-lookup"><span data-stu-id="10693-110">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="10693-111">Ziele</span><span class="sxs-lookup"><span data-stu-id="10693-111">Objectives</span></span>

* <span data-ttu-id="10693-112">Erfahren, wie Unity für die HoloLens-Entwicklung konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="10693-112">Learn how to configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="10693-113">Erfahren, wie Ihre App erstellt und in HoloLens bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="10693-113">Learn how to build and deploy your app to HoloLens.</span></span>
* <span data-ttu-id="10693-114">Kennenlernen des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers auf Ihrem HoloLens 2-Gerät.</span><span class="sxs-lookup"><span data-stu-id="10693-114">Experience the spatial mapping mesh, hand meshes, and  framerate counter on your HoloLens 2 device.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="10693-115">Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="10693-115">Creating the Unity project</span></span>

1. <span data-ttu-id="10693-116">Starten Sie **Unity Hub**, wählen Sie die Registerkarte **Projects** (Projekte) aus, und klicken Sie dann auf den **Abwärtspfeil** neben der Schaltfläche **New** (Neu):</span><span class="sxs-lookup"><span data-stu-id="10693-116">Launch **Unity Hub**, select the **Projects** tab, and then click the **down arrow** next to the **New** button:</span></span>

![Unity-Hub mit hervorgehobenem Abwärtspfeil der Schaltfläche „Neu“](images/mr-learning-base/base-02-section1-step1-1.png)

2. <span data-ttu-id="10693-118">Wählen Sie im Dropdownmenü die Unity-Version aus, die in den [Voraussetzungen](mr-learning-base-01.md#prerequisites) angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="10693-118">In the dropdown menu, select the Unity version specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Auswählen der Unity-Version](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="10693-120">Wenn diese bestimmte Unity-Version nicht auf dem Unity Hub verfügbar ist, können Sie die Installation aus dem <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Downloadarchiv</a> von Unity einleiten.</span><span class="sxs-lookup"><span data-stu-id="10693-120">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

3. <span data-ttu-id="10693-121">Führen Sie im Fenster **Create a new project** (Neues Projekt erstellen) Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="10693-121">In the **Create a new project** window, do the following:</span></span>

    * <span data-ttu-id="10693-122">Vergewissern Sie sich, dass **Templates** (Vorlagen) auf **3D** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="10693-122">Ensure **Templates** is set to **3D**.</span></span>
    * <span data-ttu-id="10693-123">Geben Sie im Feld **Project Name** (Projektname) einen passenden Namen für Ihr Projekt ein (beispielsweise „MRTK-Tutorials“).</span><span class="sxs-lookup"><span data-stu-id="10693-123">In the **Project Name** box, enter a suitable name for your project (for example, "MRTK Tutorials").</span></span>
    * <span data-ttu-id="10693-124">Klicken Sie auf die Schaltfläche mit den drei Punkten neben **Location** (Speicherort), und navigieren Sie dann zu dem Ordner, in dem Sie Ihr Projekt speichern möchten.</span><span class="sxs-lookup"><span data-stu-id="10693-124">Click the three-dot button next to **Location**, and then navigate to the folder where you want to save your project.</span></span>

> [!CAUTION]
> <span data-ttu-id="10693-125">Wenn Sie unter Windows arbeiten, müssen Sie den MAX_PATH-Grenzwert von 255 Zeichen beachten.</span><span class="sxs-lookup"><span data-stu-id="10693-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="10693-126">Daher sollten Sie das Unity-Projekt in der Nähe des Stammverzeichnisses des Laufwerks speichern.</span><span class="sxs-lookup"><span data-stu-id="10693-126">Because of this, you should save the Unity project close to the root of the drive.</span></span>

    * <span data-ttu-id="10693-127">Klicken Sie auf die Schaltfläche **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="10693-127">Click the **Create** button.</span></span> <span data-ttu-id="10693-128">Dadurch wird das neue Unity-Projekt erstellt und gestartet.</span><span class="sxs-lookup"><span data-stu-id="10693-128">This creates and launches your new Unity project.</span></span>

![Unity Hub mit ausgefülltem Fenster „Create a new project“ (Neues Projekt erstellen)](images/mr-learning-base/base-02-section1-step1-3.png)

<span data-ttu-id="10693-130">Die Statusleiste hält Sie über Ihren Fortschritt auf dem Laufenden.</span><span class="sxs-lookup"><span data-stu-id="10693-130">The status bar keeps you updated on your progress.</span></span>

![Die Unity-Statusleiste hält Sie über den Status Ihrer Projekterstellung auf dem Laufenden](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="10693-132">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="10693-132">Switching the build platform</span></span>

1. <span data-ttu-id="10693-133">Wählen Sie in der Menüleiste **File** > **Build Settings...** (Datei > Buildeinstellungen) aus</span><span class="sxs-lookup"><span data-stu-id="10693-133">On the menu bar, select **File** > **Build Settings...**</span></span>

![Unity: Build Settings... Menüpfad](images/mr-learning-base/base-02-section2-step1-1.png)

2. <span data-ttu-id="10693-135">Wählen Sie im Fenster **Build Settings** (Buildeinstellungen) **Universal Windows Platform** (Universelle Windows-Plattform) aus, und klicken Sie dann auf die Schaltfläche **Switch Platform** (Plattform wechseln):</span><span class="sxs-lookup"><span data-stu-id="10693-135">In the **Build Settings** window, select **Universal Windows Platform** and then click the **Switch Platform** button:</span></span>

![Unity-Fenster „Build Settings“ mit ausgewählter UWP, um von der Plattform „Eigenständig“ zu wechseln](images/mr-learning-base/base-02-section2-step1-2.png)

3. <span data-ttu-id="10693-137">Warten Sie, bis Unity den Plattformwechsel abgeschlossen hat, und schließen Sie dann das Fenster **Build Settings** (Buildeinstellungen).</span><span class="sxs-lookup"><span data-stu-id="10693-137">Wait for Unity to finish switching the platform, and then close the **Build Settings** window.</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="10693-138">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="10693-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="10693-139">Die TextMeshPro Essential-Ressourcen sind für die Benutzeroberflächenelemente des MRTK erforderlich.</span><span class="sxs-lookup"><span data-stu-id="10693-139">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="10693-140">Wenn Sie nicht beabsichtigen, die Benutzeroberflächenelemente des MRTK in Ihrem Projekt zu verwenden, können Sie diesen Schritt überspringen.</span><span class="sxs-lookup"><span data-stu-id="10693-140">If you are not planning to use MRTK's UI elements in your project, you can skip this step.</span></span>

1. <span data-ttu-id="10693-141">Wählen Sie in der Menüleiste **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Fenster > TextMeshPro > TMP Essential Resources importieren) aus.</span><span class="sxs-lookup"><span data-stu-id="10693-141">On the menu bar, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

![Unity: Menüpfad für „Import TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-1.png)

2. <span data-ttu-id="10693-143">Klicken Sie im **Import Unity Package**-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="10693-143">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets:</span></span>

![Unity-Fenster für Importieren von „TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="10693-145">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="10693-145">Importing the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="10693-146">Laden Sie das benutzerdefinierte Unity-Paket herunter:</span><span class="sxs-lookup"><span data-stu-id="10693-146">Download the Unity custom package:</span></span>

    [<span data-ttu-id="10693-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="10693-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. <span data-ttu-id="10693-148">Wählen Sie in der Menüleiste **Assets** > **Import Package** > **Custom Package...** (Assets > Paket importieren > Benutzerdefiniertes Paket...) aus.</span><span class="sxs-lookup"><span data-stu-id="10693-148">On the menu bar, select **Assets** > **Import Package** > **Custom Package...**.</span></span>
3. <span data-ttu-id="10693-149">Navigieren Sie im Dialogfeld **Import package...** (Paket importieren...) zum Speicherort des Pakets, das Sie soeben heruntergeladen haben, und klicken Sie dann auf die Schaltfläche **Open** (Öffnen).</span><span class="sxs-lookup"><span data-stu-id="10693-149">In the **Import package...** dialog, navigate to the location of the package you just downloaded, then select it, and then click the **Open** button.</span></span>
4. <span data-ttu-id="10693-150">Klicken Sie im **Import Unity Package**-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren.</span><span class="sxs-lookup"><span data-stu-id="10693-150">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets.</span></span>

## <a name="selecting-mrtk-and-project-settings"></a><span data-ttu-id="10693-151">Auswählen von MRTK- und Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="10693-151">Selecting MRTK and project settings</span></span>

<span data-ttu-id="10693-152">Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des **MRTK-Projektkonfigurators** angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="10693-152">After Unity has finished importing the package from the previous section, the **MRTK Project Configurator** window should appear.</span></span> <span data-ttu-id="10693-153">Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) wechseln:</span><span class="sxs-lookup"><span data-stu-id="10693-153">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity: Menüpfad für „Configure Unity Project“](images/mr-learning-base/base-02-section5-step1-1.png)

1. <span data-ttu-id="10693-155">Klappen Sie im Fenster des **MRTK-Projektkonfigurators** falls erforderlich **Modify Configurations** (Konfigurationen ändern) auf, und vergewissern Sie sich dann, dass alle Optionen aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="10693-155">In the **MRTK Project Configurator** window, expand the **Modify Configurations** section, if necessary, and then ensure that all options are selected.</span></span>

![Fenster des Unity MRTK-Projektkonfigurators mit angezeigter Option „Modify Configurations“](images/mr-learning-base/base-02-section5-step1-2.png)

2. <span data-ttu-id="10693-157">Klicken Sie auf die Schaltfläche **Apply** (Übernehmen), um die Änderungen zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="10693-157">To apply the settings, click the **Apply** button.</span></span>

![Schaltfläche „Übernehmen“ im MRTK](images/mr-learning-base/apply.png)

> [!NOTE]
> <span data-ttu-id="10693-159">Sie verwenden die integrierte Legacy-XR von Unity anstelle des neuen XR-Plug-In-Systems, weil das neue System mit den für diese Tutorialreihe [empfohlenen Unity- und MRTK-Versionen](mr-learning-base-01.md#prerequisites) nicht vollständig kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="10693-159">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="10693-160">Sollten Warnungen zu einer veralteten Version des integrierten XR-Plug-Ins angezeigt werden, können Sie diese ignorieren.</span><span class="sxs-lookup"><span data-stu-id="10693-160">If you see any warnings about built-in XR being deprecated, you can ignore them.</span></span>

> [!TIP]
> <span data-ttu-id="10693-161">Die Anwendung der MRTK-Standardeinstellungen ist optional, wird aber dringend empfohlen, weil es bei der Konfiguration einiger empfohlener Unity-Einstellungen hilfreich ist:</span><span class="sxs-lookup"><span data-stu-id="10693-161">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="10693-162">Legacy-XR aktivieren: Aktiviert VR für das Projekt.</span><span class="sxs-lookup"><span data-stu-id="10693-162">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="10693-163">Legen Sie den Single Pass-instanziierten Renderingpfad fest: Verbessert die Grafikleistung, indem die Renderpipeline für beide Augen im selben Zeichnen-Aufruf ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="10693-163">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="10693-164">Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Single Pass-instanziiertes Rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) der [Leistung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)sdokumentation von MRTK.</span><span class="sxs-lookup"><span data-stu-id="10693-164">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="10693-165">Standardebene für Spatial Awareness (räumliche Wahrnehmung) festlegen: Erstellt eine Unity-Ebene namens „Spatial Awareness“ und konfiguriert MRTK für die Verwendung dieser Ebene für das Gittermodell für räumliche Wahrnehmung.</span><span class="sxs-lookup"><span data-stu-id="10693-165">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="10693-166">Weitere Informationen zu Unity-Ebenen finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.</span><span class="sxs-lookup"><span data-stu-id="10693-166">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

3. <span data-ttu-id="10693-167">Wählen Sie in der Menüleiste **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus.</span><span class="sxs-lookup"><span data-stu-id="10693-167">On the menu bar, select **Edit** > **Project Settings...** .</span></span>

4. <span data-ttu-id="10693-168">Wählen Sie im Fenster **Project Settings** (Projekteinstellungen) **Player** aus, klicken Sie auf das Dropdownmenü **XR Settings** (XR-Einstellungen), und aktivieren Sie dann das Kontrollkästchen neben **Virtual Reality Supported** (Virtual Reality unterstützt):</span><span class="sxs-lookup"><span data-stu-id="10693-168">In the **Project Settings** window, select **Player**, then click the **XR Settings** dropdown, and then select the box next to **Virtual Reality Supported**:</span></span>

![Unity-XR-Einstellungen mit angezeigter Option „Virtual Reality unterstützt“](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="10693-170">Dadurch wird das Windows Mixed Reality SDK importiert:</span><span class="sxs-lookup"><span data-stu-id="10693-170">This imports the Windows Mixed Reality SDK:</span></span>

![Unity XR-Einstellungen mit angezeigten Virtual Reality SDKs](images/mr-learning-base/mixed-reality-sdk.png)

<span data-ttu-id="10693-172">Nachdem Unity das Importieren des Windows Mixed Reality SDK abgeschlossen hat, sollte wieder das Fenster des **MRTK-Projektkonfigurators** angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="10693-172">After Unity has finished importing the Windows Mixed Reality SDK, the **MRTK Project Configurator** window should appear again.</span></span> <span data-ttu-id="10693-173">Wenn das nicht der Fall ist, wählen Sie **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um es zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="10693-173">If it doesn't, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open it.</span></span>

5. <span data-ttu-id="10693-174">Klicken Sie im Fenster des **MRTK-Projektkonfigurators** auf das Dropdownmenü **Audio spatializer** (Räumliche Audiowiedergabe), und wählen Sie dann **MS HRTF Spatializer** aus.</span><span class="sxs-lookup"><span data-stu-id="10693-174">In the **MRTK Project Configurator** window, click the **Audio spatializer** dropdown, and then select **MS HRTF Spatializer**.</span></span>

![Projekteinstellungen mit angezeigten Optionen für die räumliche Audiowiedergabe](images/mr-learning-base/base-02-section5-step2-3.png)

6. <span data-ttu-id="10693-176">Klicken Sie auf die Schaltfläche **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="10693-176">Click the **Apply** button.</span></span> <span data-ttu-id="10693-177">Dadurch wird das Fenster des **MRTK-Projektkonfigurators** geschlossen.</span><span class="sxs-lookup"><span data-stu-id="10693-177">This closes the **MRTK Project Configurator** window.</span></span>

    > [!TIP]
    > <span data-ttu-id="10693-178">Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern.</span><span class="sxs-lookup"><span data-stu-id="10693-178">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="10693-179">Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="10693-179">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="10693-180">Weitere Informationen zu diesem Thema finden Sie in den Tutorials zur räumlichen Audiowiedergabe.</span><span class="sxs-lookup"><span data-stu-id="10693-180">To learn more about this topic, you can refer to the Spatial audio tutorials.</span></span>

7. <span data-ttu-id="10693-181">Klicken Sie im Fenster **Project Settings** (Projekteinstellungen) auf das Fenster **Depth Format** (Tiefenformat), und wählen Sie dann **16-bit depth** (16-Bit Tiefe) aus:</span><span class="sxs-lookup"><span data-stu-id="10693-181">In the **Project Settings** window, click the **Depth Format** dropdown, and then select **16-bit depth**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Unity XR-Einstellungen mit ausgewählter Option „16-Bit Tiefe“.":::

    > [!TIP]
    > <span data-ttu-id="10693-183">Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen.</span><span class="sxs-lookup"><span data-stu-id="10693-183">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="10693-184">Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Tiefenpufferfreigabe (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) der [Leistung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)sdokumentation von MRTK.</span><span class="sxs-lookup"><span data-stu-id="10693-184">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

8. <span data-ttu-id="10693-185">Klicken Sie auf das Dropdownmenü **Publishing Settings** (Veröffentlichungseinstellungen), dann in das Feld **Package name** (Paketname), und geben Sie einen passenden Namen ein (beispielsweise „MRTK-Tutorials-Erste-Schritte“).</span><span class="sxs-lookup"><span data-stu-id="10693-185">Click the **Publishing Settings** drop-down, and then in the **Package name** box, enter a suitable name (for example, "MRTK-Tutorials-Getting-Started").</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Veröffentlichungseinstellungen in Unity mit konfiguriertem Paketnamen.":::

    <span data-ttu-id="10693-187">**Paketname und Produktname**</span><span class="sxs-lookup"><span data-stu-id="10693-187">**Package Name and Product Name**</span></span>

    - <span data-ttu-id="10693-188">Der Paketname stellt den eindeutigen Bezeichner für die App dar.</span><span class="sxs-lookup"><span data-stu-id="10693-188">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="10693-189">Sie sollten diesen Bezeichner erstellen, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="10693-189">You should create this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>
    - <span data-ttu-id="10693-190">Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="10693-190">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="10693-191">Um das Auffinden der App während der Entwicklung zu erleichtern, können Sie vor dem Namen einen Unterstrich hinzufügen, sodass sie in Listen oben einsortiert wird.</span><span class="sxs-lookup"><span data-stu-id="10693-191">To make the app easier to locate during development, you can add an underscore in front of the name to sort it to the top.</span></span>

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Unity-Projekteinstellungen mit konfiguriertem Produktnamen.":::

9. <span data-ttu-id="10693-193">Schließen Sie das Fenster **Project Settings** (Projekteinstellungen).</span><span class="sxs-lookup"><span data-stu-id="10693-193">Close the **Project Settings** window.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="10693-194">Erstellen und Konfigurieren der Szene</span><span class="sxs-lookup"><span data-stu-id="10693-194">Creating and configuring the scene</span></span>

1. <span data-ttu-id="10693-195">Wählen Sie in der Menüleiste **File** > **New Scene** (Datei > Neue Szene) aus.</span><span class="sxs-lookup"><span data-stu-id="10693-195">On the menu bar, select **File** > **New Scene**.</span></span>
2. <span data-ttu-id="10693-196">Sie fügen der Szene das MRTK hinzu, indem Sie in der Menüleiste **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Mixed Reality Toolkit > Zu Szene hinzufügen und konfigurieren) auswählen.</span><span class="sxs-lookup"><span data-stu-id="10693-196">To add the MRTK to the scene, on the menu bar, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity-Menüpfad „Zu Szene hinzufügen und konfigurieren“.":::

3. <span data-ttu-id="10693-198">Achten Sie darauf, dass im Fenster **Hierarchy** (Hierarchie) das **MixedRealityToolkit** ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="10693-198">In the **Hierarchy** window, ensure that **MixedRealityToolkit** is selected.</span></span>

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Vergewissern Sie sich, dass „MixedRealityTookit“ ausgewählt ist.":::

4. <span data-ttu-id="10693-200">Überprüfen Sie im Abschnitt **MixedRealityToolkit** des **Inspektorfensters**, dass das Konfigurationsprofil auf **DefaultMixedRealityToolkitConfigurationProfile** festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="10693-200">In the **Inspector** window's **MixedRealityToolkit** section, verify that the configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Unity MixedRealityToolkit-Komponente mit ausgewähltem DefaultMixedRealityTookitConfigurationProfile.":::

    > [!IMPORTANT]
    > <span data-ttu-id="10693-202">Normalerweise verwenden Sie zum Entwickeln für HoloLens das DefaultHoloLens2ConfigurationProfile-Profil.</span><span class="sxs-lookup"><span data-stu-id="10693-202">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="10693-203">Im Rahmen dieses Tutorials verwenden Sie jedoch das DefaultMixedRealityToolkitConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="10693-203">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile.</span></span> <span data-ttu-id="10693-204">Im nächsten Tutorial, [Konfigurieren der MRTK-Profile](mr-learning-base-03.md), wechseln Sie dann zum DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="10693-204">In the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

5. <span data-ttu-id="10693-205">Wählen Sie in der Menüleiste **File** > **Save As...** (Datei > Speichern unter) aus.</span><span class="sxs-lookup"><span data-stu-id="10693-205">On the menu bar, select **File** > **Save As...**</span></span>
6. <span data-ttu-id="10693-206">Navigieren Sie im Dialogfeld **Save Scene** (Szene speichern) zum Ordner **Scenes** (Szenen) Ihres Projekts.</span><span class="sxs-lookup"><span data-stu-id="10693-206">In the **Save Scene** dialog, navigate to your project's **Scenes** folder.</span></span> <span data-ttu-id="10693-207">Geben Sie im Feld **File name** (Dateiname) Ihrer Szene einen passenden Namen (beispielsweise „\_ErsteSchritte\_“), und klicken Sie dann auf die Schaltfläche **Save** (Speichern).</span><span class="sxs-lookup"><span data-stu-id="10693-207">In the **File name** box, give your scene a suitable name (for example, "\_GettingStarted\_"), and then click the **Save** button.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Speichern-Bestätigungsfenster beim Speichern von Szenen in Unity.":::

## <a name="building-and-deploying-to-your-hololens-2"></a><span data-ttu-id="10693-209">Entwickeln und Bereitstellen auf Ihrer HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="10693-209">Building and deploying to your HoloLens 2</span></span>

> <span data-ttu-id="10693-210">Bevor Sie auf Ihrem Gerät erstellen, bestätigen Sie die folgenden Punkte:</span><span class="sxs-lookup"><span data-stu-id="10693-210">Before building to your device, confirm the following:</span></span>
- <span data-ttu-id="10693-211">Ihr Gerät befindet sich im Entwicklermodus.</span><span class="sxs-lookup"><span data-stu-id="10693-211">Your device is in Developer Mode.</span></span>
- <span data-ttu-id="10693-212">Ihr Gerät ist mit Ihrem Entwicklungscomputer gekoppelt.</span><span class="sxs-lookup"><span data-stu-id="10693-212">Your device is paired with your development computer.</span></span> <span data-ttu-id="10693-213">Andernfalls wird in Visual Studio während des Erstellungsvorgangs das folgende Dialogfeld angezeigt:</span><span class="sxs-lookup"><span data-stu-id="10693-213">If it's not, you will see the following dialog box in Visual Studio during the build process:</span></span>

![Entering PIN for pairing devices (PIN für Gerätekopplung eingeben)](images/mr-learning-base/pin-request.png)

 <span data-ttu-id="10693-215">Weitere Informationen zu diesen beiden Schritten finden Sie unter [Verwenden von Visual Studio zum Bereitstellen und Debuggen](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="10693-215">To learn more about both of these steps, see [Using Visual Studio to deploy and debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

1. <span data-ttu-id="10693-216">Wählen Sie in der Menüleiste **File** > **Build Settings...** (Datei > Buildeinstellungen) aus.</span><span class="sxs-lookup"><span data-stu-id="10693-216">On the menu bar, select **File** > **Build Settings...**.</span></span>
2. <span data-ttu-id="10693-217">Klicken Sie im Fenster **Build Settings** (Buildeinstellungen) auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um der Liste **Scenes In Build** (Szenen im Build) Ihre aktuelle Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="10693-217">In the **Build Settings** window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span>

![Hinzufügen Ihrer aktuellen Szene zur Liste „Szenen im Build“](images/mr-learning-base/base-02-section7-step1-1.png)

3. <span data-ttu-id="10693-219">Klicken Sie auf die Schaltfläche **Build**.</span><span class="sxs-lookup"><span data-stu-id="10693-219">Click the **Build** button.</span></span>

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Klicken Sie auf die Schaltfläche Build.":::

4. <span data-ttu-id="10693-221">Wählen Sie im Dialogfeld **Build Universal Windows Platform** (Universelle Windows-Plattform erstellen) einen passenden Speicherort zum Speichern Ihres Builds aus (beispielsweise kann es sinnvoll sein, einen Ordner „Builds“ in Ihrem Ordner „MRTK-Tutorials“ zu erstellen).</span><span class="sxs-lookup"><span data-stu-id="10693-221">In the **Build Universal Windows Platform** dialog, choose a suitable location to store your build (for example, you may want to create a "Builds" folder in your "MRTK Tutorials" folder).</span></span> <span data-ttu-id="10693-222">Erstellen Sie einen neuen Ordner, und geben Sie ihm einen passenden Namen (beispielsweise „Erste Schritte“), wählen Sie den Ordner aus, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="10693-222">Create a new folder and give it a suitable name (for example, "GettingStarted"), then select the folder, and then click the **Select Folder** button to start the build process.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Unity Build-Fenster mit Ihrem angezeigten Buildordner.":::

    <span data-ttu-id="10693-224">Es wird eine Statusleiste angezeigt, die Sie über den Fortschritt Ihres Builds auf dem Laufenden hält.</span><span class="sxs-lookup"><span data-stu-id="10693-224">A status bar appears and keeps you updated on your build progress.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Unity-Buildvorgang wird ausgeführt.":::

    > [!TIP]
    > <span data-ttu-id="10693-226">Sie können auch auf dem [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) bereitstellen oder ein [App-Paket](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) zum Querladen erstellen.</span><span class="sxs-lookup"><span data-stu-id="10693-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

5. <span data-ttu-id="10693-227">Wenn der Buildvorgang abgeschlossen ist, navigieren Sie im Datei-Explorer zu dem Speicherort, an dem Sie den Build gespeichert haben, und doppelklicken Sie dann auf die Projektmappendatei, um sie in Visual Studio zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="10693-227">When the build process has completed, in File Explorer, navigate to the location where you stored the build, and then double-click the solution file to open it in Visual Studio:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Windows Explorer mit der ausgewählten, neu erstellten Visual Studio-Projektmappendatei.":::

    > [!NOTE]
    > <span data-ttu-id="10693-229">Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation **[Installieren der Tools](../../install-the-tools.md)** angegeben) installiert sind.</span><span class="sxs-lookup"><span data-stu-id="10693-229">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

6. <span data-ttu-id="10693-230">Konfigurieren Sie Visual Studio für HoloLens 2, indem Sie die **Master**- oder **Release**-Konfiguration, die **ARM64**-Architektur und **Gerät** als Ziel auswählen.</span><span class="sxs-lookup"><span data-stu-id="10693-230">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as the target.</span></span>

    > [!TIP]
    > <span data-ttu-id="10693-231">Wenn Sie auf HoloLens (1. Generation) bereitstellen, wählen Sie die **x86**-Architektur aus.</span><span class="sxs-lookup"><span data-stu-id="10693-231">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Visual Studio, konfiguriert für die Bereitstellung in HoloLens 2":::.

    > [!NOTE]
    > <span data-ttu-id="10693-233">Für HoloLens erstellen Sie normalerweise für die ARM-Architektur.</span><span class="sxs-lookup"><span data-stu-id="10693-233">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="10693-234">Jedoch besteht ein <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>bekanntes Problem</strong></a> in Unity 2019.3, das zu Fehlern führt, wenn ARM in Visual Studio als Buildarchitektur ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="10693-234">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="10693-235">Die empfohlene Umgehung besteht darin, Builds für ARM64 zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="10693-235">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="10693-236">Wenn diese Option nicht in Frage kommt, navigieren Sie zu **Edit > Project Settings > Player > Other Settings** (Bearbeiten > Projekteinstellungen > Player > Weitere Einstellungen), und deaktivieren Sie **Graphics Jobs** (Grafikaufträge).</span><span class="sxs-lookup"><span data-stu-id="10693-236">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="10693-237">Wenn „Device“ (Gerät) nicht als Zieloption angezeigt wird, müssen Sie möglicherweise das Startprojekt für die Visual Studio-Projektmappe vom Projekt „IL2CPP“ zum Projekt „UWP“ ändern.</span><span class="sxs-lookup"><span data-stu-id="10693-237">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="10693-238">Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf den Namen Ihres Projekts (Universal Windows), und wählen Sie dann **Set as StartUp Project** (Als Startprojekt festlegen) aus.</span><span class="sxs-lookup"><span data-stu-id="10693-238">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows), and then select **Set as StartUp Project**.</span></span>

7. <span data-ttu-id="10693-239">Verbinden Sie Ihre HoloLens mit Ihrem Computer, und führen Sie dann eine der folgenden Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="10693-239">Connect your HoloLens to your computer, and then do one of the following:</span></span>
- <span data-ttu-id="10693-240">Wenn Sie die App erstellen, sie auf Ihrer HoloLens bereitstellen und automatisch ohne angefügten Debugger starten möchten, wählen Sie in der Menüleiste **Debuggen** > **Starten ohne Debuggen** aus.</span><span class="sxs-lookup"><span data-stu-id="10693-240">To build the app, deploy it to your HoloLens, and start it automatically without the Visual Studio debugger attached, on the menu bar, select **Debug** > **Start Without Debugging**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Menüpfad „Starten ohne Debuggen“ in Visual Studio.":::

- <span data-ttu-id="10693-242">Wenn Sie die App erstellen und auf Ihrer HoloLens bereitstellen, sie jedoch nicht automatisch starten möchten, wählen Sie in der Menüleiste **Erstellen > Projektmappe bereitstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="10693-242">To build and deploy the app to your HoloLens but not have it start automatically, on the menu bar, select **Build > Deploy Solution**.</span></span>

    > [!NOTE]
    ><span data-ttu-id="10693-243">Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **Toggle Diagnostics** (Diagnose ein-/ausschalten) ein- und ausblenden.</span><span class="sxs-lookup"><span data-stu-id="10693-243">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="10693-244">Es empfiehlt sich, während der Entwicklung den Profiler die meiste Zeit anzuzeigen, um zu verstehen, wann Änderungen an der App die Leistung beeinträchtigen können.</span><span class="sxs-lookup"><span data-stu-id="10693-244">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="10693-245">Beispielsweise sollten HoloLens-Apps [durchgängig bei 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="10693-245">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="10693-246">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="10693-246">Congratulations</span></span>

<span data-ttu-id="10693-247">Sie haben jetzt Ihre erste HoloLens-App bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="10693-247">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="10693-248">Während Sie sich in ihr bewegen, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="10693-248">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="10693-249">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.</span><span class="sxs-lookup"><span data-stu-id="10693-249">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="10693-250">Diese Features sind nur einige der grundlegenden Bestandteile von MRTK.</span><span class="sxs-lookup"><span data-stu-id="10693-250">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="10693-251">In den bevorstehenden Tutorials fügen Sie Ihrer Szene Inhalte hinzu, um die Funktionen von HoloLens und des MRTK kennenzulernen.</span><span class="sxs-lookup"><span data-stu-id="10693-251">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10693-252">Nächstes Tutorial: 3. Konfigurieren der MRTK-Profile</span><span class="sxs-lookup"><span data-stu-id="10693-252">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
