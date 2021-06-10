---
title: 'Tutorials zu räumlichen Audioinhalten: 1. Hinzufügen räumlicher Audiodaten zu Ihrem Projekt'
description: Fügen Sie Ihrem Unity-Projekt das Microsoft Spatializer-Plug-In hinzu, um auf HoloLens 2 HRTF-Hardwareabladung zuzugreifen.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, Hololens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer
ms.openlocfilehash: 112531a3248461a5b380ad4b93de34545a2f2c3f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403361"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="c654d-105">1. Hinzufügen räumlicher Audiodaten zu Ihrem Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="c654d-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="c654d-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="c654d-106">Overview</span></span>

<span data-ttu-id="c654d-107">Willkommen beim Tutorial zu räumlichen Audiodaten für Unity auf HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="c654d-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="c654d-108">In dieser Tutorialreihe erfahren Sie, wie Sie die HRTF-Auslagerung (Head-Related Transfer Function) für HoloLens 2 verwenden und wie Sie hallen, wenn Sie HRTF-Auslagerung verwenden.</span><span class="sxs-lookup"><span data-stu-id="c654d-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="c654d-109">Das [GitHub-Repository Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) verfügt über ein abgeschlossenes Unity-Projekt dieser Tutorialsequenz.</span><span class="sxs-lookup"><span data-stu-id="c654d-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="c654d-110">Ein Verständnis dafür, was es bedeutet, Sounds mit HRTF-basierten Spatialization-Technologien zu spatialisieren, und Empfehlungen dazu, wann es hilfreich sein kann, finden Sie unter [Spatial Sound Design](/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="c654d-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="c654d-111">Was ist HRTF-Auslagerung?</span><span class="sxs-lookup"><span data-stu-id="c654d-111">What is HRTF offload?</span></span>

<span data-ttu-id="c654d-112">Die Verarbeitung von Audio mit HRTF-basierten Algorithmen erfordert eine große Menge spezieller Berechnungen.</span><span class="sxs-lookup"><span data-stu-id="c654d-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="c654d-113">HoloLens 2 enthält dedizierte Hardware, die verwendet werden kann, um eine Belastung des Anwendungsprozessors zu vermeiden und so die Verarbeitung von HRTF-basierten Algorithmen zu "auslagern".</span><span class="sxs-lookup"><span data-stu-id="c654d-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="c654d-114">Das Microsoft Spatializer-Plug-In bietet Eine einfache Möglichkeit für Ihre Anwendung, die dedizierte HRTF-Hardware zu nutzen, sodass Ihre Anwendung einen größeren Teil des Anwendungsprozessors für andere Vorgänge als räumliche Audiodaten verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="c654d-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="c654d-115">Ziele</span><span class="sxs-lookup"><span data-stu-id="c654d-115">Objectives</span></span>

* <span data-ttu-id="c654d-116">Importieren und Aktivieren des Microsoft Spatializer-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="c654d-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="c654d-117">Aktivieren von räumlichem Audio auf Ihrer Entwicklerarbeitsstation</span><span class="sxs-lookup"><span data-stu-id="c654d-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c654d-118">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c654d-118">Prerequisites</span></span>

* <span data-ttu-id="c654d-119">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](../../install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="c654d-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="c654d-120">Gundkenntnisse der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="c654d-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="c654d-121">Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="c654d-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="c654d-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit eingebundener Unity 2020/2019 LTS und hinzugefügtes modul "Universelle Windows-Plattform Buildunterstützung"</span><span class="sxs-lookup"><span data-stu-id="c654d-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="c654d-123">Es **wird dringend empfohlen,** die Reihe [Erste Schritte](mr-learning-base-01.md) mit Tutorials abzuschließen oder einige grundlegende Vorherige Erfahrungen mit Unity und MRTK zu sammeln, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="c654d-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!Important]
> <span data-ttu-id="c654d-124">Diese Tutorialreihe unterstützt Unity 2020 LTS (derzeit 2020.3.x), wenn Sie Open XR oder Das Windows XR-Plug-In sowie Unity 2019 LTS (derzeit 2019.4.x) verwenden, wenn Sie ältere WSA- oder Windows XR-Plug-Ins verwenden.</span><span class="sxs-lookup"><span data-stu-id="c654d-124">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="c654d-125">Diese Information hat Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="c654d-125">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="c654d-126">Erstellen und Vorbereiten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="c654d-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="c654d-127">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="c654d-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="c654d-128">Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="c654d-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="c654d-129">[Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*</span><span class="sxs-lookup"><span data-stu-id="c654d-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="c654d-130">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="c654d-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="c654d-131">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c654d-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="c654d-132">Importieren des Mixed Reality Toolkits und Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="c654d-132">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)

1. <span data-ttu-id="c654d-133">[Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) und Benennen der Szene, z. B. *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="c654d-133">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="c654d-134">Befolgen Sie dann die Anweisungen [unter Ändern der Anzeigeoption](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) für räumliche Wahrnehmung, um sicherzustellen, dass das MRTK-Konfigurationsprofil für Ihre Szene **DefaultHoloLens2ConfigurationProfile** lautet, und ändern Sie die Anzeigeoptionen für das Gitternetz für räumliche Wahrnehmung in **Verdeckung.**</span><span class="sxs-lookup"><span data-stu-id="c654d-134">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="c654d-135">Hinzufügen von Microsoft Spatializer zum Projekt</span><span class="sxs-lookup"><span data-stu-id="c654d-135">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="c654d-136">Laden Sie Microsoft Spatializer <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage</a> herunter, und importieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="c654d-136">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="c654d-137">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren der Tutorialressourcen](mr-learning-base-02.md#importing-the-tutorial-assets).</span><span class="sxs-lookup"><span data-stu-id="c654d-137">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="c654d-138">Aktivieren des Microsoft Spatializer-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="c654d-138">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="c654d-139">Nachdem Sie Microsoft Spatializer in Ihr Unity-Projekt importiert haben, wird das Fenster **MRTK Project Configurator** angezeigt. Wählen Sie in der Dropdownliste **Audio spatializer** den **Microsoft Spatializer** aus, und klicken Sie dann auf die Schaltfläche Übernehmen, um die Einstellung anzuwenden:</span><span class="sxs-lookup"><span data-stu-id="c654d-139">Once you import the Microsoft Spatializer into your unity project, **MRTK Project Configurator** window will appear, use the **Audio spatializer** dropdown to select the **Microsoft Spatializer**, then click the Apply button to apply the setting:</span></span>

![MRTK-Projektkonfigurator](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

<span data-ttu-id="c654d-141">Sie können den Microsoft Spatializer auch manuell aktivieren: **Bearbeiten -> Projekteinstellungen -> Audio** öffnen und **das Spatializer-Plug-In** in "Microsoft Spatializer" ändern.</span><span class="sxs-lookup"><span data-stu-id="c654d-141">you can also manually enable the Microsoft Spatializer: Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Projekteinstellungen mit Spatializer-Plug-In](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="c654d-143">Aktivieren von räumlichem Audio auf Ihrer Arbeitsstation</span><span class="sxs-lookup"><span data-stu-id="c654d-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="c654d-144">In Desktopversionen von Windows ist räumliches Audio standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="c654d-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="c654d-145">Aktivieren Sie es, indem Sie mit der rechten Maustaste auf das Volumesymbol in der Taskleiste klicken.</span><span class="sxs-lookup"><span data-stu-id="c654d-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="c654d-146">Wählen Sie **Räumlicher Sound -> Windows Sonic für Kopfhörer** aus, um die beste Darstellung des Hörens auf HoloLens 2 zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c654d-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Desktopeinstellungen für räumliche Audiodaten](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="c654d-148">Diese Einstellung ist nur erforderlich, wenn Sie das Projekt im Unity-Editor testen möchten.</span><span class="sxs-lookup"><span data-stu-id="c654d-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="c654d-149">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="c654d-149">Congratulations</span></span>

<span data-ttu-id="c654d-150">In diesem Tutorial haben Sie erfahren, wie Sie das Microsoft Spatializer-Plug-In importieren und aktivieren sowie das räumliche Audio auf Ihrer Arbeitsstation aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c654d-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="c654d-151">Im nächsten Tutorial erfahren Sie, wie Sie räumliche Audiodaten im Unity-Projekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c654d-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c654d-152">Nächstes Tutorial: 2. Spatializing button interaction sounds</span><span class="sxs-lookup"><span data-stu-id="c654d-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
