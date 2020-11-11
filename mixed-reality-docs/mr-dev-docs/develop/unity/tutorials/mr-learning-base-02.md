---
title: Tutorials zu den ersten Schritten – 2 Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie Ihr Unity-Projekt für das Mixed Reality Toolkit (MRTK) konfigurieren und es in Ihrer HoloLens 2 bereitstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 2fb742f71baef50881a4a3279e7b0a1b969f0306
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353438"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="2f8dc-105">2. Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="2f8dc-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="2f8dc-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="2f8dc-106">Overview</span></span>

<span data-ttu-id="2f8dc-107">In diesem Tutorial erfahren Sie, wie Sie ein neues Unity-Projekt erstellen, es für die Entwicklung mit dem <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> konfigurieren und das MRTK importieren.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="2f8dc-108">Außerdem werden Sie durch Konfiguration, Erstellung und Bereitstellung einer einfachen Unity-Szene aus Visual Studio auf Ihrer HoloLens 2 geführt.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-108">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="2f8dc-109">Nachdem Sie diese auf Ihrer HoloLens 2 bereitgestellt haben, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-109">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="2f8dc-110">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-110">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="2f8dc-111">Ziele</span><span class="sxs-lookup"><span data-stu-id="2f8dc-111">Objectives</span></span>

* <span data-ttu-id="2f8dc-112">Erfahren, wie Unity für die HoloLens-Entwicklung konfiguriert wird</span><span class="sxs-lookup"><span data-stu-id="2f8dc-112">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="2f8dc-113">Erfahren, wie Ihre App erstellt und in HoloLens bereitgestellt wird</span><span class="sxs-lookup"><span data-stu-id="2f8dc-113">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="2f8dc-114">Kennenlernen des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers auf dem HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="2f8dc-114">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="2f8dc-115">Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="2f8dc-115">Creating the Unity project</span></span>

<span data-ttu-id="2f8dc-116">Starten Sie **Unity Hub** , wählen Sie die Registerkarte **Projects** (Projekte) aus, und klicken Sie auf den **Abwärtspfeil** neben der Schaltfläche **New** (Neu):</span><span class="sxs-lookup"><span data-stu-id="2f8dc-116">Launch **Unity Hub** , select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity-Hub mit hervorgehobener Schaltfläche „New“](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="2f8dc-118">Wählen Sie in der Dropdownliste die Unity- **Version** aus, die oben in den [Voraussetzungen](mr-learning-base-01.md#prerequisites) angegeben ist:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-118">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity-Hub mit Versionsauswahl-Dropdown „NEW“](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="2f8dc-120">Wenn diese bestimmte Unity-Version nicht auf dem Unity Hub verfügbar ist, können Sie die Installation aus dem <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Downloadarchiv</a> von Unity einleiten.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-120">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="2f8dc-121">Erstellen Sie im Fenster ein neues Projekt:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-121">In the Create a new project window:</span></span>

* <span data-ttu-id="2f8dc-122">Vergewissern Sie sich, dass **Templates** (Vorlagen) auf **3D** festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="2f8dc-122">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="2f8dc-123">Geben Sie einen passenden **Project Name** (Projektnamen) ein, z. B. _MRTK-Tutorials_</span><span class="sxs-lookup"><span data-stu-id="2f8dc-123">Enter a suitable **Project Name** , for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="2f8dc-124">Wählen Sie eine geeignete **Location** (Speicherort) zum Speichern Ihres Projekts, z. B. _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="2f8dc-124">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="2f8dc-125">Klicken Sie auf die Schaltfläche **Create** (Erstellen), um das neue Unity-Projekt zu erstellen</span><span class="sxs-lookup"><span data-stu-id="2f8dc-125">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity-Hub mit ausgefülltem Fenster „Create new project“ (Neues Projekt erstellen)](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="2f8dc-127">Wenn Sie unter Windows arbeiten, müssen Sie den MAX_PATH-Grenzwert von 255 Zeichen beachten.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-127">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="2f8dc-128">Daher sollten Sie das Unity-Projekt in der Nähe des Stammverzeichnisses des Laufwerks speichern.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-128">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="2f8dc-129">Warten Sie, bis Unity das Projekt erstellt hat:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-129">Wait for Unity to create the project:</span></span>

![Unity: Erstellen eines neuen Projekts in Bearbeitung](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="2f8dc-131">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="2f8dc-131">Switching the build platform</span></span>

<span data-ttu-id="2f8dc-132">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-132">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity: Build Settings... Menüpfad](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="2f8dc-134">Wählen Sie im Build Settings-Fenster **Universal Windows Platform** (Universelle Windows-Plattform) aus, und klicken Sie auf die Schaltfläche **Switch Platform** (Plattform wechseln):</span><span class="sxs-lookup"><span data-stu-id="2f8dc-134">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Unity-Fenster „Build Settings“ mit ausgewählter UWP, um von der Plattform „Eigenständig“ zu wechseln](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="2f8dc-136">Warten Sie, bis Unity den Wechsel der Plattform abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-136">Wait for Unity to finish switching the platform:</span></span>

![Unity: Wechsel der Plattform in Bearbeitung](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="2f8dc-138">Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das rote **x** -Symbol, um das Build Settings-Fenster zu schließen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-138">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Unity-Fenster „Build“ mit hervorgehobenem Symbol zum Schließen](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="2f8dc-140">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="2f8dc-140">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="2f8dc-141">Wählen Sie im Unity-Menü **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Fenster > TextMeshPro > TMP Essential Resources importieren) aus, um das Importfenster für Unity-Pakete zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-141">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity: Menüpfad für „Import TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="2f8dc-143">Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-143">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity-Fenster für Importieren von „TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="2f8dc-145">Die TextMeshPro Essential-Ressourcen sind für die Benutzeroberflächenelemente des MRTK erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-145">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="2f8dc-146">Sie können diesen Schritt überspringen, wenn Sie nicht beabsichtigen, die Benutzeroberflächenelemente des MRTK in Ihrem Projekt zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-146">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="2f8dc-147">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="2f8dc-147">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="2f8dc-148">Laden Sie das benutzerdefinierte Unity-Paket herunter:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-148">Download the Unity custom package:</span></span>

* [<span data-ttu-id="2f8dc-149">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="2f8dc-149">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

<span data-ttu-id="2f8dc-150">Wählen Sie im Unity-Menü **Assets** > **Import Package** > **Custom Package...** (Assets > Paket importieren > Benutzerdefiniertes Paket...) aus, um das Fenster zum Importieren von Paketen zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-150">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Unity: Benutzerdefiniertes Paket importieren... Menüpfad](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="2f8dc-152">Wählen Sie im Fenster „Import package...“ (Paket importieren...) das heruntergeladene **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** -Paket aus, und klicken Sie auf die Schaltfläche **Open** (Öffnen):</span><span class="sxs-lookup"><span data-stu-id="2f8dc-152">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![Unity: Benutzerdefiniertes Paket importieren mit Aufforderungsfenster „Open“](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="2f8dc-154">Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-154">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity-Fenster zum Importieren von MRTK-Grundlagen](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="2f8dc-156">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="2f8dc-156">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="2f8dc-157">1. Übernehmen der Einstellungen des MRTK-Projektkonfigurators</span><span class="sxs-lookup"><span data-stu-id="2f8dc-157">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="2f8dc-158">Nachdem Unity das Importieren des Pakets aus dem vorherigen Abschnitt abgeschlossen hat, sollte das Fenster des MRTK-Projektkonfigurators angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-158">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="2f8dc-159">Wenn das nicht der Fall ist, öffnen Sie es, indem Sie zu **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) wechseln:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-159">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** :</span></span>

![Unity: Menüpfad für „Configure Unity Project“](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="2f8dc-161">Klappen Sie im Projektkonfiguratorfenster des MRTK den Abschnitt **Modify Configurations** (Konfigurationen ändern) auf, vergewissern Sie sich, dass alle Optionen aktiviert sind, und klicken Sie auf die Schaltfläche **Apply** (Übernehmen), um die Einstellungen zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-161">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Unity MRTK-Projektkonfigurator-Fenster](images/mr-learning-base/base-02-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="2f8dc-163">Sie verwenden die integrierte Legacy-XR von Unity anstelle des neuen XR-Plug-In-Systems, weil das neue System mit den für diese Tutorialreihe [empfohlenen Unity- und MRTK-Versionen](mr-learning-base-01.md#prerequisites) nicht vollständig kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-163">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="2f8dc-164">Folglich können Sie alle Informationen oder Warnungen hinsichtlich der Einstellung der integrierten XR ignorieren.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-164">Consequently, you can ignore any information or warnings regarding built-in XR being deprecated.</span></span>

> [!TIP]
> <span data-ttu-id="2f8dc-165">Die Anwendung der MRTK-Standardeinstellungen ist optional, wird aber dringend empfohlen, weil es bei der Konfiguration einiger empfohlener Unity-Einstellungen hilfreich ist:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-165">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="2f8dc-166">Legacy-XR aktivieren: Aktiviert VR für das Projekt.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-166">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="2f8dc-167">Legen Sie den Single Pass-instanziierten Renderingpfad fest: Verbessert die Grafikleistung, indem die Renderpipeline für beide Augen im selben Zeichnen-Aufruf ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-167">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="2f8dc-168">Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Single Pass-instanziiertes Rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) der [Leistung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)sdokumentation von MRTK.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-168">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="2f8dc-169">Standardebene für Spatial Awareness (räumliche Wahrnehmung) festlegen: Erstellt eine Unity-Ebene namens „Spatial Awareness“ und konfiguriert MRTK für die Verwendung dieser Ebene für das Gittermodell für räumliche Wahrnehmung.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-169">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="2f8dc-170">Weitere Informationen zu Unity-Ebenen finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-170">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="2f8dc-171">2. Konfigurieren zusätzlicher Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="2f8dc-171">2. Configure additional project settings</span></span>

<span data-ttu-id="2f8dc-172">Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-172">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity: Project Settings... Menüpfad](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="2f8dc-174">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **XR Settings** (Player > XR-Einstellungen) aus, klicken Sie auf das **+** -Symbol, und wählen Sie „Windows Mixed Reality“ aus, um das Windows Mixed Reality SDK hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-174">In the Project Settings window, select **Player** > **XR Settings** , click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Unity: XR-Einstellungen mit ausgewähltem „Windows Mixed Reality SDK hinzufügen“](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="2f8dc-176">Nachdem Unity das Importieren des Windows Mixed Reality SDK abgeschlossen hat, sollte wieder das Fenster des MRTK-Projektkonfigurators angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-176">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="2f8dc-177">Wenn dies nicht der Fall ist, verwenden Sie das Unity-Menü, um es zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-177">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="2f8dc-178">Verwenden Sie im Fenster des MRTK-Projektkonfigurators die Dropdownliste **Audio spatializer** (Räumliche Audiowiedergabe), um den **MS HRTF Spatializer** auszuwählen, und klicken Sie dann auf die Schaltfläche **Übernehmen** , um die Einstellung zu übernehmen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-178">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer** , then click the **Apply** button to apply the setting:</span></span>

![Unity MRTK-Projektkonfigurator mit ausgewähltem MS HRTF Spatializer](images/mr-learning-base/base-02-section5-step2-3.png)

> [!TIP]
> <span data-ttu-id="2f8dc-180">Das Festlegen der „Audio Spatializer“-Eigenschaft ist optional, kann aber die Audioerfahrung in Ihrem Projekt verbessern.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-180">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="2f8dc-181">Wenn Sie sie auf „MS HRTF Spatializer“ festlegen, wird dieses Spatializer-Plug-In verwendet, wenn die Eigenschaft „AudioSource.spatialize“ von Unity aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-181">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="2f8dc-182">Weitere Informationen zu diesem Thema finden Sie in den [Tutorials zur räumlichen Audiowiedergabe](unity-spatial-audio-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="2f8dc-182">To learn more about this topic, you can refer to the [Spatial audio tutorials](unity-spatial-audio-ch1.md).</span></span>

<span data-ttu-id="2f8dc-183">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **XR Settings** (Player > XR-Einstellungen) aus, und verwenden Sie dann die Dropdownliste **Depth Format** (Tiefenformat), um **16-Bit Tiefe** auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-183">In the Project Settings window, select **Player** > **XR Settings** , then use the **Depth Format** dropdown to select **16-bit depth** :</span></span>

![Unity: XR-Einstellungen mit ausgewählter 16-Bit-Tiefe](images/mr-learning-base/base-02-section5-step2-4.png)

> [!TIP]
> <span data-ttu-id="2f8dc-185">Das Verringern des Tiefenformats auf 16 Bit ist optional, kann aber bei der Verbesserung der Grafikleistung in Ihrem Projekt helfen.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-185">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="2f8dc-186">Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Tiefenpufferfreigabe (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) der [Leistung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)sdokumentation von MRTK.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-186">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

<span data-ttu-id="2f8dc-187">Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, geben Sie dann im Feld **Package name** (Paketname) einen passenden Namen ein, beispielsweise _MRTKTutorials-GettingStarted_ :</span><span class="sxs-lookup"><span data-stu-id="2f8dc-187">In the Project Settings window, select **Player** > **Publishing Settings** , then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_ :</span></span>

![Unity: „Publishing Settings“ mit konfiguriertem Paketnamen](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> <span data-ttu-id="2f8dc-189">Der Paketname stellt den eindeutigen Bezeichner für die App dar.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-189">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="2f8dc-190">Sie sollten diesen Bezeichner ändern, bevor Sie die App bereitstellen, um das Überschreiben zuvor installierter Apps zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-190">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="2f8dc-191">Der „Product Name“ (Produktname) ist der Name, der im HoloLens-Startmenü angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-191">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="2f8dc-192">Um das Auffinden der App während der Entwicklung zu erleichtern, fügen Sie vor dem Namen einen Unterstrich hinzu, sodass sie in Listen oben einsortiert wird.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-192">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="2f8dc-193">Erstellen und Konfigurieren der Szene</span><span class="sxs-lookup"><span data-stu-id="2f8dc-193">Creating and configuring the scene</span></span>

<span data-ttu-id="2f8dc-194">Wählen Sie im Unity-Menü **File** > **New Scene** (Datei > Neue Szene) aus, um eine neue Szene zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-194">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity: Menüpfad für „New Scene“](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="2f8dc-196">Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Mixed Reality-Toolkit > Zu Szene hinzufügen und konfigurieren) aus, um Ihrer aktuellen Szene das MRTK hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-196">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity: Menüpfad zu „Add to Scene and Configure...“](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="2f8dc-198">Überprüfen Sie bei im Hierarchiefenster ausgewähltem **MixedRealityToolkit** -Objekt im Inspektorfenster, ob das Konfigurationsprofil des **Mixed Reality-Toolkits** auf **DefaultMixedRealityToolkitConfigurationProfile** festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-198">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile** :</span></span>

![MixedRealityToolkit-Komponente von Unity mit ausgewähltem DefaultMixedRealityTookitConfigurationProfile](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="2f8dc-200">Normalerweise verwenden Sie zum Entwickeln für HoloLens das DefaultHoloLens2ConfigurationProfile-Profil.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-200">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="2f8dc-201">Im Rahmen dieses Tutorials verwenden Sie jedoch das DefaultMixedRealityToolkitConfigurationProfile-Profil und wechseln dann im nächsten Tutorial [Konfigurieren der MRTK-Profile](mr-learning-base-03.md) zum DefaultHoloLens2ConfigurationProfile-Profil.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-201">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="2f8dc-202">Wählen Sie im Unity-Menü **File** > **Save As...** (Datei > Speichern unter...) aus, um das Save Scene-Fenster (Szene speichern) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-202">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity: Menüpfad für „Save As...“](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="2f8dc-204">Navigieren Sie im Save Scene-Fenster zum Ordner **Scenes** (Szenen), geben Sie Ihrer Szene einen passenden Namen, beispielsweise _ErsteSchritte_ , und klicken Sie auf die Schaltfläche **Save** (Speichern), um die Szene zu speichern:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-204">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_ , and click the **Save** button to save the scene:</span></span>

![Unity: Aufforderungsfenster zum Speichern der Szene](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="2f8dc-206">Erstellen Ihrer Anwendung auf der HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2f8dc-206">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="2f8dc-207">1. Erstellen des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="2f8dc-207">1. Build the Unity project</span></span>

<span data-ttu-id="2f8dc-208">Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-208">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="2f8dc-209">Klicken Sie im Build Settings-Fenster (Buildeinstellungen) auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um der Liste **Scenes In Build** (Szenen im Build) Ihre aktuelle Szene hinzuzufügen, und klicken Sie dann auf die Schaltfläche **Build** (Erstellen), um das Build Universal Windows Platform-Fenster (Erstellen für Universelle Windows-Plattform) zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-209">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Unity-Fenster „Build Settings“ mit ausgewählter UWP](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="2f8dc-211">Wählen Sie im Build Universal Windows Platform-Fenster einen passenden Speicherort aus, um Ihren Build zu speichern, beispielsweise _D:\MixedRealityLearning\Builds_ , erstellen Sie einen neuen Ordner mit einem passenden Namen, z. B. _GettingStarted_ , und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-211">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_ , create a new folder and give it a suitable name, for example, _GettingStarted_ , and then click the **Select Folder** button to start the build process:</span></span>

![Unity-Fenster „Build Settings“ mit Aufforderungsfenster zum Auswählen eines Ordners](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="2f8dc-213">Warten Sie, bis Unity den Buildvorgang abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-213">Wait for Unity to finish the build process:</span></span>

![Unity: Buildvorgang wird ausgeführt](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="2f8dc-215">2. Erstellen und Bereitstellen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="2f8dc-215">2. Build and deploy the application</span></span>

<span data-ttu-id="2f8dc-216">Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-216">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="2f8dc-217">Navigieren Sie zum Ordner, und doppelklicken Sie auf die Projektmappendatei, um sie in Visual Studio zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-217">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Windows-Explorer mit neu erstellter, ausgewählter Visual Studio-Projektmappe](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2f8dc-219">Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation **[Installieren der Tools](../../install-the-tools.md)** angegeben) installiert sind.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-219">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="2f8dc-220">Konfigurieren Sie Visual Studio für HoloLens 2, indem Sie die **Master** - oder **Release** -Konfiguration, die **ARM64** -Architektur und **Gerät** als Ziel auswählen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-220">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio, konfiguriert für die Bereitstellung in HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="2f8dc-222">Wenn Sie auf HoloLens (1. Generation) bereitstellen, wählen Sie die **x86** -Architektur aus.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-222">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="2f8dc-223">Für HoloLens erstellen Sie normalerweise für die ARM-Architektur.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-223">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="2f8dc-224">Jedoch besteht ein <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>bekanntes Problem</strong></a> in Unity 2019.3, das zu Fehlern führt, wenn ARM in Visual Studio als Buildarchitektur ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-224">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="2f8dc-225">Die empfohlene Umgehung besteht darin, Builds für ARM64 zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-225">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="2f8dc-226">Wenn diese Option nicht in Frage kommt, navigieren Sie zu **Edit > Project Settings > Player > Other Settings** (Bearbeiten > Projekteinstellungen > Player > Weitere Einstellungen), und deaktivieren Sie **Graphics Jobs** (Grafikaufträge).</span><span class="sxs-lookup"><span data-stu-id="2f8dc-226">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="2f8dc-227">Wenn „Device“ (Gerät) nicht als Zieloption angezeigt wird, müssen Sie möglicherweise das Startprojekt für die Visual Studio-Projektmappe vom Projekt „IL2CPP“ zum Projekt „UWP“ ändern.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-227">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="2f8dc-228">Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf den Namen Ihres Projekts (Universal Windows), und wählen Sie **Set as StartUp Project** (Als Startprojekt festlegen) aus.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-228">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="2f8dc-229">Verbinden Sie Ihre HoloLens mit Ihrem Computer, wählen Sie dann **Debug** > **Start Without Debugging** (Debuggen > Ohne Debuggen starten) aus, um zu erstellen und auf Ihrem Gerät bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="2f8dc-229">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio-Menüpfad für „Ohne Debuggen starten“](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="2f8dc-231">Bevor Sie den Build für Ihr Gerät erstellen, muss das Gerät in den Entwicklermodus versetzt und mit Ihrem Entwicklungscomputer gekoppelt werden.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-231">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="2f8dc-232">Sie können beide Schritte ausführen, indem Sie [diese Anweisungen](../../platform-capabilities-and-apis/using-visual-studio.md) befolgen.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-232">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="2f8dc-233">Sie können auch auf dem [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) bereitstellen oder ein [App-Paket](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) zum Querladen erstellen.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-233">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="2f8dc-234">Bei der Option „Start Without Debugging“ (Ohne Debuggen starten) wird die App auf Ihrem Gerät automatisch ohne angefügten Visual Studio-Debugger gestartet.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-234">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="2f8dc-235">Wählen Sie **Build > Deploy Solution** (Erstellen > Projektmappe bereitstellen) aus, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-235">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="2f8dc-236">Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **Toggle Diagnostics** (Diagnose ein-/ausschalten) ein- und ausblenden.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-236">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="2f8dc-237">Es empfiehlt sich, während der Entwicklung den Profiler die meiste Zeit anzuzeigen, um zu verstehen, wann Änderungen an der App die Leistung beeinträchtigen können.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-237">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="2f8dc-238">Beispielsweise sollten HoloLens-Apps [durchgängig bei 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-238">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="2f8dc-239">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="2f8dc-239">Congratulations</span></span>

<span data-ttu-id="2f8dc-240">Sie haben jetzt Ihre erste HoloLens-App bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-240">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="2f8dc-241">Während Sie sich in ihr bewegen, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das die Oberflächen bedeckt, die von der HoloLens erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-241">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="2f8dc-242">Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-242">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="2f8dc-243">Diese Features sind nur einige der grundlegenden Bestandteile von MRTK.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-243">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="2f8dc-244">In den bevorstehenden Tutorials fügen Sie Ihrer Szene Inhalte hinzu, um die Funktionen von HoloLens und des MRTK kennenzulernen.</span><span class="sxs-lookup"><span data-stu-id="2f8dc-244">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f8dc-245">Nächstes Tutorial: 3. Konfigurieren der MRTK-Profile</span><span class="sxs-lookup"><span data-stu-id="2f8dc-245">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
