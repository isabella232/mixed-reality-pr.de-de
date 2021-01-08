---
title: Hinzufügen räumlicher Audiodaten zu Ihrem Projekt
description: Fügen Sie das Microsoft spatializer-Plug-in zu Ihrem Unity-Projekt hinzu, um auf hololens 2 HRTF Hardware Offload zuzugreifen.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer
ms.openlocfilehash: 80bf19e8a091bd241e28afff0a42c13ca72e1d45
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007470"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="3a90c-104">Hinzufügen räumlicher Audiodaten zu Ihrem Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="3a90c-104">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="3a90c-105">Willkommen beim Tutorial zu räumlichen Audiodaten für Unity auf HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="3a90c-105">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="3a90c-106">Diese tutorialsequenz zeigt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="3a90c-106">This tutorial sequence shows:</span></span>
* <span data-ttu-id="3a90c-107">Verwenden der Head-Related Transfer Function (HRTF)-Auslagerung auf hololens 2 in Unity</span><span class="sxs-lookup"><span data-stu-id="3a90c-107">How to use head-related transfer function (HRTF) offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="3a90c-108">Aktivieren von "Reverb" bei Verwendung von "HRTF Auslagerung"</span><span class="sxs-lookup"><span data-stu-id="3a90c-108">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="3a90c-109">Das [GitHub-Repository für Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity) verfügt über ein abgeschlossenes Unity-Projekt für diese tutorialsequenz.</span><span class="sxs-lookup"><span data-stu-id="3a90c-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="3a90c-110">Ein Verständnis dafür, wie Sie Sounds mithilfe von HRTF-basierten spatialisierungs Technologien und Empfehlungen für den Fall, dass es hilfreich sein kann, spatialisieren können, finden Sie unter [Spatial Sound Design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="3a90c-110">For an understanding about what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="3a90c-111">Was ist HRTF Offload?</span><span class="sxs-lookup"><span data-stu-id="3a90c-111">What is HRTF offload?</span></span>

<span data-ttu-id="3a90c-112">Die Verarbeitung von Audiodaten mithilfe von HRTF-basierten Algorithmen erfordert eine große Menge an spezieller Berechnung.</span><span class="sxs-lookup"><span data-stu-id="3a90c-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="3a90c-113">Hololens 2 umfasst dedizierte Hardware, die verwendet werden kann, um die Belastung des Anwendungs Prozessors zu vermeiden und so die Verarbeitung von HRTF-basierten Algorithmen zu verlagern.</span><span class="sxs-lookup"><span data-stu-id="3a90c-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="3a90c-114">Das Microsoft spatializer-Plug-in ist eine einfache Möglichkeit für Ihre Anwendung, die dedizierte HRTF-Hardware zu nutzen, damit Ihre Anwendung mehr Anwendungs Prozessor für andere Vorgänge als räumliche Audiodaten verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="3a90c-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="3a90c-115">Ziele</span><span class="sxs-lookup"><span data-stu-id="3a90c-115">Objectives</span></span>

<span data-ttu-id="3a90c-116">In diesem ersten Kapitel gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="3a90c-116">In this first chapter, you'll:</span></span>
* <span data-ttu-id="3a90c-117">Erstellen eines Unity-Projekts und Importieren von mrtk</span><span class="sxs-lookup"><span data-stu-id="3a90c-117">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="3a90c-118">Importieren des Microsoft spatializer-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="3a90c-118">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="3a90c-119">Aktivieren des Microsoft spatializer-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="3a90c-119">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="3a90c-120">Aktivieren räumlicher Audiodaten auf Ihrer Entwickler Arbeitsstation</span><span class="sxs-lookup"><span data-stu-id="3a90c-120">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="3a90c-121">Erstellen eines Projekts und Hinzufügen von nuget für Unity</span><span class="sxs-lookup"><span data-stu-id="3a90c-121">Create a project and add NuGet for Unity</span></span>

<span data-ttu-id="3a90c-122">Beginnen Sie mit einem leeren Unity-Projekt, und fügen Sie nuget für Unity hinzu, und konfigurieren Sie es:</span><span class="sxs-lookup"><span data-stu-id="3a90c-122">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="3a90c-123">Herunterladen des neuesten [nugetforunity. unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="3a90c-123">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="3a90c-124">Klicken Sie in der Unity-Menüleiste auf **Assets-> Paket importieren > benutzerdefiniertes Paket...** , und installieren Sie das nugetforunity-Paket:</span><span class="sxs-lookup"><span data-stu-id="3a90c-124">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Benutzerdefiniertes Paket importieren](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="3a90c-126">Hinzufügen des Windows Mixed Reality-Pakets</span><span class="sxs-lookup"><span data-stu-id="3a90c-126">Add the Windows Mixed Reality package</span></span>

<span data-ttu-id="3a90c-127">Die Unterstützung von Windows Mixed Reality in Unity 2019 und höher ist in einem optionalen Paket enthalten.</span><span class="sxs-lookup"><span data-stu-id="3a90c-127">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="3a90c-128">Um Sie dem Projekt hinzuzufügen, öffnen Sie die **Fenster > Paket-Manager** über die Unity-Menüleiste:</span><span class="sxs-lookup"><span data-stu-id="3a90c-128">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Paket-Manager-Menü](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="3a90c-130">Suchen und installieren Sie dann das **Windows Mixed Reality** -Paket:</span><span class="sxs-lookup"><span data-stu-id="3a90c-130">Then find and install the **Windows Mixed Reality** package:</span></span>

![Paket-Manager-Fenster](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="3a90c-132">Installieren von mrtk und Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="3a90c-132">Install MRTK and Microsoft Spatializer</span></span>

<span data-ttu-id="3a90c-133">Installieren Sie mithilfe von nuget für Unity die mrtk-und Microsoft spatializer-Plug-ins:</span><span class="sxs-lookup"><span data-stu-id="3a90c-133">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="3a90c-134">Klicken Sie in der Unity-Menüleiste auf **nuget-> nuget-Pakete verwalten**.</span><span class="sxs-lookup"><span data-stu-id="3a90c-134">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![NuGet-Pakete verwalten](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="3a90c-136">Geben Sie im **Suchfeld** "Microsoft. mixedreality. Toolkit" ein, und installieren Sie das mrtk Core-Paket: **Microsoft. mixedreality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="3a90c-136">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Mrtk-nuget-Paket](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="3a90c-138">Das [mrtk-nuget-Paket](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) hat zusätzlichen Kontext und Details.</span><span class="sxs-lookup"><span data-stu-id="3a90c-138">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="3a90c-139">Geben Sie im **Suchfeld** "Microsoft. spatialaudiodatei" ein, und installieren Sie das Microsoft spatializer-Paket: **Microsoft. spatialaudio. spatializer. unity**</span><span class="sxs-lookup"><span data-stu-id="3a90c-139">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Spatializer-Plug-in nuget](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="3a90c-141">Einrichten von mrtk in Ihrem Projekt</span><span class="sxs-lookup"><span data-stu-id="3a90c-141">Set up MRTK in your project</span></span>

1. <span data-ttu-id="3a90c-142">Öffnen Sie das Fenster mit den Buildeinstellungen, indem Sie zu **Datei > Buildeinstellungen** navigieren.</span><span class="sxs-lookup"><span data-stu-id="3a90c-142">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="3a90c-143">Wählen Sie die _universelle Windows-Plattform_ aus, und klicken Sie auf **Plattform wechseln**</span><span class="sxs-lookup"><span data-stu-id="3a90c-143">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="3a90c-144">Klicken Sie im **Fenster erstellen** auf **Player Einstellungen** , um die Eigenschaften für **Player Einstellungen** im **Inspektor** -Bereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3a90c-144">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="3a90c-145">Aktivieren Sie unter **XR-Einstellungen** das Kontrollkästchen **Virtual Reality supported** .</span><span class="sxs-lookup"><span data-stu-id="3a90c-145">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="3a90c-146">Ändern Sie unter " **XR Settings**" den **Stereo-Renderingmodus** in **Single Pass-instanziierten**.</span><span class="sxs-lookup"><span data-stu-id="3a90c-146">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="3a90c-147">Aktivieren Sie unter **Veröffentlichungs Einstellungen** das Kontrollkästchen **räumliche Wahrnehmung** im Abschnitt " **Funktionen** ".</span><span class="sxs-lookup"><span data-stu-id="3a90c-147">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="3a90c-148">Klicken Sie in der Menüleiste auf **Mixed Reality Toolkit-> zu Szene hinzufügen und konfigurieren.**</span><span class="sxs-lookup"><span data-stu-id="3a90c-148">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="3a90c-149">, um mrtk Ihrer Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="3a90c-149">to add MRTK to your scene.</span></span>

<span data-ttu-id="3a90c-150">Weitere Anleitungen, einschließlich der Erstellung der APP und Bereitstellung auf einem hololens 2, finden Sie in [Kapitel 1 des Lern Basismoduls von Mr](../../../mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="3a90c-150">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](../../../mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="3a90c-151">Aktivieren des Microsoft spatializer-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="3a90c-151">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="3a90c-152">Aktivieren Sie das **Microsoft spatializer** -Plug-in.</span><span class="sxs-lookup"><span data-stu-id="3a90c-152">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="3a90c-153">Öffnen Sie die **Projekteinstellungen bearbeiten-> > Audiodatei**, und ändern Sie das **spatializer-Plug** -in in "Microsoft spatializer".</span><span class="sxs-lookup"><span data-stu-id="3a90c-153">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="3a90c-154">Der **Audioabschnitt** der **Projekteinstellungen** sieht nun wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3a90c-154">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Projekteinstellungen mit dem spatializer-Plug-in](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="3a90c-156">Aktivieren räumlicher Audiodaten auf Ihrer Arbeitsstation</span><span class="sxs-lookup"><span data-stu-id="3a90c-156">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="3a90c-157">Unter Desktop Versionen von Windows ist das räumliche Audioformat standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="3a90c-157">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="3a90c-158">Aktivieren Sie diese Option, indem Sie in der Taskleiste mit der rechten Maustaste auf das Volume-Symbol klicken.</span><span class="sxs-lookup"><span data-stu-id="3a90c-158">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="3a90c-159">Um die beste Darstellung von hololens 2 zu erhalten, wählen Sie **räumliches Sound-> Windows-Sonic für Kopfhörer aus**.</span><span class="sxs-lookup"><span data-stu-id="3a90c-159">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Desktop Einstellungen für räumliche Desktops](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="3a90c-161">Diese Einstellung ist nur erforderlich, wenn Sie Vorhaben, das Projekt im Unity-Editor zu testen.</span><span class="sxs-lookup"><span data-stu-id="3a90c-161">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3a90c-162">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="3a90c-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a90c-163">Räumliche Unity-Audiodaten, Kapitel 2</span><span class="sxs-lookup"><span data-stu-id="3a90c-163">Unity spatial audio chapter 2</span></span>](unity-spatial-audio-ch2.md)

