---
title: Lernprogramme für räumliche Audiodaten-1. Hinzufügen räumlicher Audiodaten zu Ihrem Projekt
description: Fügen Sie das Microsoft spatializer-Plug-in zu Ihrem Unity-Projekt hinzu, um auf hololens 2 HRTF Hardware Offload zuzugreifen.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer
ms.openlocfilehash: cc7a4db5a3b4d853f2912a5e8e022fddd372e105
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635388"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="432af-105">1. hinzufügen räumlicher Audiodaten zu Ihrem Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="432af-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="432af-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="432af-106">Overview</span></span>

<span data-ttu-id="432af-107">Willkommen beim Tutorial zu räumlichen Audiodaten für Unity auf HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="432af-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="432af-108">In dieser tutorialreihe erfahren Sie, wie Sie die Start bezogene Übertragungsfunktion (Head-Related Transfer Function, HRTF) auf hololens 2 verwenden und wie Sie den Reverb bei Verwendung der HRTF-Auslagerung aktivieren.</span><span class="sxs-lookup"><span data-stu-id="432af-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="432af-109">Das [GitHub-Repository für Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity) verfügt über ein abgeschlossenes Unity-Projekt für diese tutorialsequenz.</span><span class="sxs-lookup"><span data-stu-id="432af-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="432af-110">Ein Verständnis der Bedeutung von Sounds mithilfe von HRTF-basierten spatialisierungs Technologien und Empfehlungen für den Fall, dass es hilfreich sein kann, finden Sie unter [Spatial Sound Design](/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="432af-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="432af-111">Was ist HRTF Offload?</span><span class="sxs-lookup"><span data-stu-id="432af-111">What is HRTF offload?</span></span>

<span data-ttu-id="432af-112">Die Verarbeitung von Audiodaten mithilfe von HRTF-basierten Algorithmen erfordert eine große Menge an spezieller Berechnung.</span><span class="sxs-lookup"><span data-stu-id="432af-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="432af-113">Hololens 2 umfasst dedizierte Hardware, die verwendet werden kann, um die Belastung des Anwendungs Prozessors zu vermeiden und so die Verarbeitung von HRTF-basierten Algorithmen zu verlagern.</span><span class="sxs-lookup"><span data-stu-id="432af-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="432af-114">Das Microsoft spatializer-Plug-in ist eine einfache Möglichkeit für Ihre Anwendung, die dedizierte HRTF-Hardware zu nutzen, damit Ihre Anwendung mehr Anwendungs Prozessor für andere Vorgänge als räumliche Audiodaten verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="432af-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="432af-115">Ziele</span><span class="sxs-lookup"><span data-stu-id="432af-115">Objectives</span></span>

* <span data-ttu-id="432af-116">Importieren und Aktivieren des Microsoft spatializer-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="432af-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="432af-117">Aktivieren räumlicher Audiodaten auf Ihrer Entwickler Arbeitsstation</span><span class="sxs-lookup"><span data-stu-id="432af-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="432af-118">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="432af-118">Prerequisites</span></span>

* <span data-ttu-id="432af-119">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](../../install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="432af-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="432af-120">Gundkenntnisse der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="432af-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="432af-121">Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="432af-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="432af-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019 LTS und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="432af-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="432af-123">Wir **empfehlen Ihnen dringend** , die Reihe "Tutorials für die ersten Schritte" auszuführen oder einige grundlegende Erfahrung mit Unity und mrtk zu [erhalten](mr-learning-base-01.md) , bevor Sie fortfahren</span><span class="sxs-lookup"><span data-stu-id="432af-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="432af-124">Die empfohlene Unity-Version für diese Tutorialserie ist Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="432af-124">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="432af-125">Sie ersetzt alle Anforderungen oder Empfehlungen bezüglich der Unity-Version, die in den oben verknüpften Voraussetzungen genannt werden.</span><span class="sxs-lookup"><span data-stu-id="432af-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="432af-126">Erstellen und Vorbereiten des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="432af-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="432af-127">In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.</span><span class="sxs-lookup"><span data-stu-id="432af-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="432af-128">Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:</span><span class="sxs-lookup"><span data-stu-id="432af-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="432af-129">[Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*</span><span class="sxs-lookup"><span data-stu-id="432af-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="432af-130">Wechseln der Buildplattform</span><span class="sxs-lookup"><span data-stu-id="432af-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="432af-131">Importieren der TextMeshPro Essential-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="432af-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="432af-132">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="432af-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="432af-133">Konfigurieren des Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="432af-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="432af-134">[Erstellen und Festlegen der Szene](mr-learning-base-02.md#creating-and-configuring-the-scene) und versehen eines geeigneten namens für die Szene, z. b. *spatialaudio*</span><span class="sxs-lookup"><span data-stu-id="432af-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="432af-135">Befolgen Sie dann die Anweisungen unter [Ändern der Anzeige Option räumliches Bewusstsein](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) , um sicherzustellen, dass das mrtk-Konfigurations Profil für Ihre Szene **DefaultHoloLens2ConfigurationProfile** ist, und ändern Sie die Anzeigeoptionen für das Mesh Spatial Awareness in **oksion**.</span><span class="sxs-lookup"><span data-stu-id="432af-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="432af-136">Hinzufügen von Microsoft spatializer zum Projekt</span><span class="sxs-lookup"><span data-stu-id="432af-136">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="432af-137">Herunterladen und Importieren von Microsoft spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. spatialaudio. spatializer. Unity. 1.0.18. unitypackage </a></span><span class="sxs-lookup"><span data-stu-id="432af-137">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="432af-138">Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="432af-138">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="432af-139">Aktivieren des Microsoft spatializer-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="432af-139">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="432af-140">Nachdem Sie den **Microsoft spatializer** importiert haben, müssen Sie ihn aktivieren.</span><span class="sxs-lookup"><span data-stu-id="432af-140">After importing the **Microsoft Spatializer** you need to enable it.</span></span> <span data-ttu-id="432af-141">Öffnen Sie die **Projekteinstellungen bearbeiten-> > Audiodatei**, und ändern Sie das **spatializer-Plug** -in in "Microsoft spatializer".</span><span class="sxs-lookup"><span data-stu-id="432af-141">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Projekteinstellungen mit dem spatializer-Plug-in](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="432af-143">Aktivieren räumlicher Audiodaten auf Ihrer Arbeitsstation</span><span class="sxs-lookup"><span data-stu-id="432af-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="432af-144">Unter Desktop Versionen von Windows ist das räumliche Audioformat standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="432af-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="432af-145">Aktivieren Sie diese Option, indem Sie in der Taskleiste mit der rechten Maustaste auf das Volume-Symbol klicken.</span><span class="sxs-lookup"><span data-stu-id="432af-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="432af-146">Um die beste Darstellung von hololens 2 zu erhalten, wählen Sie **räumliches Sound-> Windows-Sonic für Kopfhörer aus**.</span><span class="sxs-lookup"><span data-stu-id="432af-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Desktop Einstellungen für räumliche Desktops](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="432af-148">Diese Einstellung ist nur erforderlich, wenn Sie Vorhaben, das Projekt im Unity-Editor zu testen.</span><span class="sxs-lookup"><span data-stu-id="432af-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="432af-149">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="432af-149">Congratulations</span></span>

<span data-ttu-id="432af-150">In diesem Tutorial haben Sie erfahren, wie Sie das Microsoft spatializer-Plug-in importieren und aktivieren sowie das räumliche Audiomaterial auf Ihrer Arbeitsstation aktivieren.</span><span class="sxs-lookup"><span data-stu-id="432af-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="432af-151">Im nächsten Tutorial erfahren Sie, wie Sie räumliche Audiodaten im Unity-Projekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="432af-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="432af-152">Nächstes Tutorial: 2. spatialisieren von Schaltflächen-Interaktions Sounds</span><span class="sxs-lookup"><span data-stu-id="432af-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
