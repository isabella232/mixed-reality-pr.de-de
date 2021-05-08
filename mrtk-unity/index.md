---
title: MRTK-Unity Entwicklerdokumentation
description: Erfahren Sie mehr über Mixed Reality Toolkit für Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK
ms.openlocfilehash: cb8b95cf9e563e8a277fa0d4b253639a763f5ad5
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489300"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="263d2-104">Was ist das Mixed Reality Toolkit?</span><span class="sxs-lookup"><span data-stu-id="263d2-104">What is the Mixed Reality Toolkit</span></span>

![Mixed Reality-Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="263d2-106">MRTK-Unity ist ein von Microsoft vorangetriebenes Projekt, das einen Satz von Komponenten und Funktionen bereitstellt, die zum Beschleunigen der Entwicklung von plattformübergreifenden MR-Apps in Unity dienen.</span><span class="sxs-lookup"><span data-stu-id="263d2-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="263d2-107">Dies sind einige der gebotenen Funktionen:</span><span class="sxs-lookup"><span data-stu-id="263d2-107">Here are some of its functions:</span></span>

* <span data-ttu-id="263d2-108">Stellt das **plattformübergreifende Eingabesystem und Bausteine für räumliche Interaktionen und die Benutzeroberfläche** bereit.</span><span class="sxs-lookup"><span data-stu-id="263d2-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="263d2-109">Ermöglicht **schnelle Prototyperstellung** mithilfe von Simulationen im Editor, die Ihnen die Möglichkeit geben, Änderungen sofort zu sehen.</span><span class="sxs-lookup"><span data-stu-id="263d2-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="263d2-110">Fungiert als **erweiterbares Framework**, das Entwicklern die Möglichkeit zum Austausch von Kernkomponenten bietet.</span><span class="sxs-lookup"><span data-stu-id="263d2-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="263d2-111">**Unterstützt eine große Bandbreite an Plattformen**:</span><span class="sxs-lookup"><span data-stu-id="263d2-111">**Supports a wide range of platforms**:</span></span>

| <span data-ttu-id="263d2-112">Plattform</span><span class="sxs-lookup"><span data-stu-id="263d2-112">Platform</span></span> | <span data-ttu-id="263d2-113">Unterstützte Geräte</span><span class="sxs-lookup"><span data-stu-id="263d2-113">Supported Devices</span></span> |
|---|---|
| <span data-ttu-id="263d2-114">OpenXR (Unity 2020.2 oder höher)</span><span class="sxs-lookup"><span data-stu-id="263d2-114">OpenXR (Unity 2020.2 or newer)</span></span> | <span data-ttu-id="263d2-115">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="263d2-115">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="263d2-116">Windows Mixed Reality-Headsets</span><span class="sxs-lookup"><span data-stu-id="263d2-116">Windows Mixed Reality headsets</span></span> |
| <span data-ttu-id="263d2-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="263d2-117">Windows Mixed Reality</span></span> | <span data-ttu-id="263d2-118">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="263d2-118">Microsoft HoloLens</span></span> <br> <span data-ttu-id="263d2-119">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="263d2-119">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="263d2-120">Windows Mixed Reality-Headsets</span><span class="sxs-lookup"><span data-stu-id="263d2-120">Windows Mixed Reality headsets</span></span>  |
| <span data-ttu-id="263d2-121">Oculus (Unity 2019.3 oder höher)</span><span class="sxs-lookup"><span data-stu-id="263d2-121">Oculus (Unity 2019.3 or newer)</span></span> | <span data-ttu-id="263d2-122">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="263d2-122">Oculus Quest</span></span> |
| <span data-ttu-id="263d2-123">OpenVR</span><span class="sxs-lookup"><span data-stu-id="263d2-123">OpenVR</span></span> |  <span data-ttu-id="263d2-124">Windows Mixed Reality-Headsets</span><span class="sxs-lookup"><span data-stu-id="263d2-124">Windows Mixed Reality headsets</span></span> <br> <span data-ttu-id="263d2-125">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="263d2-125">HTC Vive</span></span> <br> <span data-ttu-id="263d2-126">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="263d2-126">Oculus Rift</span></span> |
| <span data-ttu-id="263d2-127">Ultraleap Hand-Tracking</span><span class="sxs-lookup"><span data-stu-id="263d2-127">Ultraleap Hand Tracking</span></span> | <span data-ttu-id="263d2-128">Ultraleap Leap Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="263d2-128">Ultraleap Leap Motion controller</span></span> |
| <span data-ttu-id="263d2-129">Mobil</span><span class="sxs-lookup"><span data-stu-id="263d2-129">Mobile</span></span> | <span data-ttu-id="263d2-130">iOS und Android</span><span class="sxs-lookup"><span data-stu-id="263d2-130">iOS and Android</span></span> |

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="263d2-131">Erste Schritte mit MRTK</span><span class="sxs-lookup"><span data-stu-id="263d2-131">Getting started with MRTK</span></span>

<span data-ttu-id="263d2-132">Wenn Sie sich erst mit dem MRTK oder der Mixed Reality-Entwicklung in Unity vertraut machen, empfehlen wir Ihnen, die Beispielanwendung „MRTK-Beispiele-Hub“ auf Ihrem Gerät oder Emulator zu installieren und zu erkunden.</span><span class="sxs-lookup"><span data-stu-id="263d2-132">If you're new to MRTK or Mixed Reality development in Unity, we recommend installing and exploring the MRTK Examples Hub sample application on your device or emulator.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="263d2-133">Herunterladen der MRTK-Beispiel-Hub-App</span><span class="sxs-lookup"><span data-stu-id="263d2-133">Download the MRTK Examples Hub app</span></span>](running-examples-hub.md)

<span data-ttu-id="263d2-134">Sobald Sie sich ein Bild gemacht haben, was Mixed Reality und MRTK zu bieten haben, installieren Sie die erforderlichen Tools, und folgen Sie unserer Tutorialreihe zur HoloLens 2 für Einsteiger.</span><span class="sxs-lookup"><span data-stu-id="263d2-134">Once you've got the hang of what Mixed Reality and MRTK has to offer, install the necessary tools and follow our beginner level HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="263d2-135">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="263d2-135">Install the tools</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [<span data-ttu-id="263d2-136">HoloLens 2-Tutorialreihe</span><span class="sxs-lookup"><span data-stu-id="263d2-136">HoloLens 2 Tutorial Series</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="263d2-137">Möchten Sie wissen, wie es unter der Haube aussieht?</span><span class="sxs-lookup"><span data-stu-id="263d2-137">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="263d2-138">Entdecken Sie das MRTK auf GitHub</span><span class="sxs-lookup"><span data-stu-id="263d2-138">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="263d2-139">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="263d2-139">Documentation</span></span>

| <span data-ttu-id="263d2-140">[![Anmerkungen zu diesem Release](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-140">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="263d2-141">Versionshinweise</span><span class="sxs-lookup"><span data-stu-id="263d2-141">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="263d2-142">[![Übersicht über das MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-142">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="263d2-143">Übersicht über das MRTK</span><span class="sxs-lookup"><span data-stu-id="263d2-143">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="263d2-144">[![API-Referenz ](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="263d2-144">[![API Reference](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="263d2-145">API-Referenz</span><span class="sxs-lookup"><span data-stu-id="263d2-145">API Reference</span></span>](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="263d2-146">Buildstatus</span><span class="sxs-lookup"><span data-stu-id="263d2-146">Build status</span></span>

| <span data-ttu-id="263d2-147">Verzweigung</span><span class="sxs-lookup"><span data-stu-id="263d2-147">Branch</span></span> | <span data-ttu-id="263d2-148">CI-Status</span><span class="sxs-lookup"><span data-stu-id="263d2-148">CI Status</span></span> | <span data-ttu-id="263d2-149">Docs-Status</span><span class="sxs-lookup"><span data-stu-id="263d2-149">Docs Status</span></span> |
|---|---|---|
| `main` |<span data-ttu-id="263d2-150">[![CI-Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="263d2-150">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="263d2-151">[![Docs-Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="263d2-151">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="263d2-152">Featurebereiche</span><span class="sxs-lookup"><span data-stu-id="263d2-152">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="263d2-153">[![Eingabesystem](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-153">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="263d2-154">**[Eingabesystem](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-154">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-155">[![Hand-Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-155">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="263d2-156">**[Hand-Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-156">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-157">[![Eyetracking (Blickverfolgung) (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-157">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="263d2-158">**[Eyetracking (Blickverfolgung) <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-158">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-159">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-159">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="263d2-160">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-160">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-161">[![Hand-Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-161">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="263d2-162">**[Hand-Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-162">**[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-163">[![UI-Steuerelemente](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="263d2-163">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="263d2-164">**[UI-Steuerelemente](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="263d2-164">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-165">[![Solver](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-165">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="263d2-166">**[Solver](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-166">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-167">[![Multiszenen-Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-167">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="263d2-168">**[Multiszenen-<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-168">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-169">[![Räumliche Wahrnehmung](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-169">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="263d2-170">**[Räumliche <br/> Wahrnehmung](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-170">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-171">[![Diagnosetool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-171">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="263d2-172">**[Diagnose- <br/> tool](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-172">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-173">[![Ansicht „MRTK-Standard-Shader“](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="263d2-173">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="263d2-174">**[Beispielansicht „MRTK-Standard-Shader“](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="263d2-174">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-175">[![Sprache und Diktat](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-175">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="263d2-176">**[Sprache](features/input/speech.md)<br/> & [Diktat](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-176">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-177">[![Begrenzungssystem](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-177">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="263d2-178">**[Begrenzungs- <br/>system](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-178">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-179">[![Simulation im Editor](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-179">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="263d2-180">**[Simulation <br/> im Editor](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-180">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-181">[![Experimentelle Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-181">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="263d2-182">**[Experimentelle <br/> Features](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-182">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="263d2-183">UX-Bausteine</span><span class="sxs-lookup"><span data-stu-id="263d2-183">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="263d2-184">[![Schaltfläche](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Schaltfläche](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-184">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="263d2-185">Ein Schaltflächen-Steuerelement, das verschiedene Eingabemethoden unterstützt, einschließlich der artikulierten Hand von HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="263d2-185">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-186">[![Begrenzungssteuerelement](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Begrenzungssteuerelement](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-186">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="263d2-187">Standard Benutzeroberfläche zum Bearbeiten von Objekten im 3D-Raum</span><span class="sxs-lookup"><span data-stu-id="263d2-187">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-188">[![Objektmanipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Objektmanipulator](features/ux-building-blocks/object-manipulator.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-188">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="263d2-189">Skript zum Manipulieren von Objekten mit einer oder zwei Händen.</span><span class="sxs-lookup"><span data-stu-id="263d2-189">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-190">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-190">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="263d2-191">2D-artige Ebene, die Scrollen mit artikulierter Handeingabe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="263d2-191">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-192">[![Systemtastatur](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[Systemtastatur](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-192">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="263d2-193">Beispielskript für die Verwendung der Systemtastatur in Unity</span><span class="sxs-lookup"><span data-stu-id="263d2-193">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-194">[![Interaktionsfähig](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interaktionsfähig](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-194">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="263d2-195">Ein Skript, um Objekte interaktionsfähig zu machen, mit visuellen Zuständen und Designunterstützung.</span><span class="sxs-lookup"><span data-stu-id="263d2-195">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-196">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-196">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="263d2-197">Verschiedene Objektpositionierungsverhalten wie tag-along, body-lock, konstante Ansichtsgröße und Oberflächenmagnetismus.</span><span class="sxs-lookup"><span data-stu-id="263d2-197">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-198">[![Objektsammlung](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Objektsammlung](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-198">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="263d2-199">Skript zum Anordnen eines Arrays von Objekten in einer dreidimensionalen Form.</span><span class="sxs-lookup"><span data-stu-id="263d2-199">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-200">[![QuickInfo](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[QuickInfo](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-200">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="263d2-201">Anmerkungsbenutzeroberfläche mit einem flexiblen Anker-/Pivot-System, das zum Bezeichnen von Motion-Controllern und Objekten verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="263d2-201">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-202">[![Schieberegler](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Schieberegler](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-202">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="263d2-203">Schieberegler-Benutzeroberfläche zum Anpassen von Werten, die direkte Hand-Tracking-Interaktion unterstützen.</span><span class="sxs-lookup"><span data-stu-id="263d2-203">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-204">[![MRTK-Standard-Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK-Standard-Shader](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-204">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="263d2-205">Der Standard-Shader des MRTK unterstützt leistungsstark verschiedene Fluent Design-Elemente.</span><span class="sxs-lookup"><span data-stu-id="263d2-205">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-206">[![Handmenü](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Handmenü](features/ux-building-blocks/hand-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-206">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="263d2-207">Handgesperrte Benutzeroberfläche für Schnellzugriff unter Verwendung des Handeinschränkungs-Solvers.</span><span class="sxs-lookup"><span data-stu-id="263d2-207">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-208">[![App-Leiste](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App-Leiste](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-208">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="263d2-209">Benutzeroberfläche für die manuelle Aktivierung von Begrenzungs-Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="263d2-209">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-210">[![ Zeiger](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Zeiger](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-210">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="263d2-211">Erfahren Sie mehr über verschiedene Typen von Zeigern.</span><span class="sxs-lookup"><span data-stu-id="263d2-211">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-212">[![Fingerspitzenvisualisierung](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingerspitzenvisualisierung](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-212">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="263d2-213">Visuelles Angebot an der Fingerspitze, das das Vertrauen in die direkte Interaktion verbessert.</span><span class="sxs-lookup"><span data-stu-id="263d2-213">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-214">[![Nähemenü](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Nähemenü](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-214">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="263d2-215">Unverankerte Menübenutzeroberfläche für die Näheinteraktionen.</span><span class="sxs-lookup"><span data-stu-id="263d2-215">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-216">[![Räumliche Wahrnehmung: Erste Schritte](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Räumliche Wahrnehmungsansicht](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-216">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="263d2-217">Machen Sie Ihre Holografieobjekte interaktionsfähig für die physischen Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="263d2-217">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-218">[![Sprachbefehl](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Sprachbefehl](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-218">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="263d2-219">Skripts und Beispiele für die Integration von Spracheingaben.</span><span class="sxs-lookup"><span data-stu-id="263d2-219">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-220">[![Statusanzeige](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Statusanzeige](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-220">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="263d2-221">Visueller Indikator zum Kommunizieren eines Datenprozesses oder -vorgangs.</span><span class="sxs-lookup"><span data-stu-id="263d2-221">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-222">[![Dialogfeld](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialogfeld](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-222">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="263d2-223">Benutzeroberfläche zum Anfordern der Bestätigung oder Anerkennung durch den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="263d2-223">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-224">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-224">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="263d2-225">Komponente, die hilft, den Benutzer anzuleiten, wenn die Geste noch nicht vermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="263d2-225">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-226">[![Handphysikdienst](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Handphysikdienst [Experimentell]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-226">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="263d2-227">Der Handphysikdienst ermöglicht Festkörperkollisionsereignisse und -interaktionen mit artikulierten Händen.</span><span class="sxs-lookup"><span data-stu-id="263d2-227">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-228">[![Scrollsammlung](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrollsammlung](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-228">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="263d2-229">Eine Objektsammlung, die nativ 3D-Objekte scrollt.</span><span class="sxs-lookup"><span data-stu-id="263d2-229">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-230">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimentell]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-230">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="263d2-231">Das Dock ermöglicht das Verschieben von Objekten in und aus vordefinierten Positionen.</span><span class="sxs-lookup"><span data-stu-id="263d2-231">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="263d2-232">[![Eyetracking: Zielauswahl](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eyetracking: Zielauswahl](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-232">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="263d2-233">Kombinieren Sie Augen, Sprach- und Handeingaben, um schnell und einfach Hologramme in Ihrer Szene auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="263d2-233">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-234">[![Eyetracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eyetracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="263d2-234">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="263d2-235">Erfahren Sie, wie Sie Text automatisch scrollen oder fließend in Inhalt im Vordergrund zoomen, basierend darauf, was Sie ansehen.</span><span class="sxs-lookup"><span data-stu-id="263d2-235">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="263d2-236">[![Eyetracking: Heatmap](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eyetracking: Heatmap](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="263d2-236">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="263d2-237">Beispiele für das Protokollieren, Laden und Visualisieren dessen, was Benutzer in Ihrer App angesehen haben</span><span class="sxs-lookup"><span data-stu-id="263d2-237">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="263d2-238">Tools</span><span class="sxs-lookup"><span data-stu-id="263d2-238">Tools</span></span>

|  <span data-ttu-id="263d2-239">[![Optimierungsfenster](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimierungsfenster](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-239">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="263d2-240">[![Abhängigkeitsfenster](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Abhängigkeitsfenster](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-240">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![Erstellen-Fenster](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="263d2-242">Erstellen-Fenster</span><span class="sxs-lookup"><span data-stu-id="263d2-242">Build Window</span></span> | <span data-ttu-id="263d2-243">[![Eingabeaufzeichnung](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Eingabeaufzeichnung](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-243">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="263d2-244">Automatisieren der Konfiguration von Mixed Reality-Projekten für Leistungsoptimierungen.</span><span class="sxs-lookup"><span data-stu-id="263d2-244">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="263d2-245">Analysieren von Abhängigkeiten zwischen Ressourcen und Identifizieren nicht verwendeter Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="263d2-245">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="263d2-246">Konfigurieren und Ausführen eines End-to-End-Erstellungsprozesses für Mixed Reality-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="263d2-246">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="263d2-247">Aufzeichnen und Wiedergeben von Kopfbewegungs-und Hand-Tracking-Daten im Editor</span><span class="sxs-lookup"><span data-stu-id="263d2-247">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="263d2-248">Beispielszenen</span><span class="sxs-lookup"><span data-stu-id="263d2-248">Example scenes</span></span>

<span data-ttu-id="263d2-249">Erkunden Sie die verschiedenen Arten von Interaktionen und Benutzeroberflächen-Steuerelementen des MRTK in [dieser Beispielszene](features/example-scenes/hand-interaction-examples.md).</span><span class="sxs-lookup"><span data-stu-id="263d2-249">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="263d2-250">[![Beispielszene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-250">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="263d2-251">MRTK-Beispiele-Hub</span><span class="sxs-lookup"><span data-stu-id="263d2-251">MRTK examples hub</span></span>

<span data-ttu-id="263d2-252">Mit dem MRTK-Beispiele-Hub können Sie verschiedene Beispielszenen im MRTK ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="263d2-252">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="263d2-253">Sie können vorgefertigte App-Pakete für HoloLens(x86), HoloLens 2(ARM) und immersive Windows Mixed Reality-Headsets(x64) herunterladen, indem Sie das Paket „Mixed Reality Toolkit-Beispiel“ im [MR-Featuretool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) auswählen.</span><span class="sxs-lookup"><span data-stu-id="263d2-253">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="263d2-254">Stellen Sie sicher, dass [Sie das Windows-Geräteportal zum Installieren von Apps für HoloLens (1. Generation) verwenden](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span><span class="sxs-lookup"><span data-stu-id="263d2-254">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="263d2-255">Auf HoloLens 2 können Sie den [MRTK-Beispiele-Hub über die Microsoft Store-App](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4) herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="263d2-255">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="263d2-256">Weitere Informationen zu den Details der Erstellung eines Multiszenen-Hubs mit dem Szenensystem und dem Szenenübergangsdienst des MRTK finden Sie auf der [INFO-Seite des Beispiele-Hubs](features/example-scenes/example-hub.md).</span><span class="sxs-lookup"><span data-stu-id="263d2-256">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="263d2-257">[![Beispielszenen-Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="263d2-257">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="263d2-258">Mit dem MRTK erstellte Beispiel-Apps.</span><span class="sxs-lookup"><span data-stu-id="263d2-258">Sample apps made with MRTK</span></span>

| <span data-ttu-id="263d2-259">[![Periodensystem der Elemente](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="263d2-259">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="263d2-260">[![Galaxie-Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="263d2-260">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="263d2-261">[![Oberflächenbeispiel-App](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="263d2-261">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="263d2-262">[Periodensystem der Elemente](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) (Periodic Table of the Elements) ist eine Open-Source-Beispiel-App, die veranschaulicht, wie das Eingabesystem und die Bausteine des MRTK zum Erstellen einer App-Erfahrung für HoloLens und immersive Headsets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="263d2-262">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="263d2-263">Lesen Sie die Portierungsgeschichte: [Einbinden der „Periodic Table of the Elements“-App in HoloLens 2 mit dem MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="263d2-263">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="263d2-264">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) ist eine Open-Source-Beispiel-App, die ursprünglich im März 2016 im Rahmen der Kampagne „Share Your Idea“ (Ideen teilen) von HoloLens entwickelt wurde.</span><span class="sxs-lookup"><span data-stu-id="263d2-264">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="263d2-265">Galaxy Explorer wurde mit den neuen Features für HoloLens 2 mithilfe des MRTK v2 aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="263d2-265">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="263d2-266">Lesen Sie die Geschichte: [Making of Galaxy Explorer für HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="263d2-266">Read the story: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="263d2-267">[Oberflächen](https://github.com/microsoft/MRDL_Unity_Surfaces) (Surfaces) ist eine Open-Source-Beispiel-App für HoloLens 2, die erkundet, wie wir mit visuellen Eindrücken, Audio und vollständig artikuliertem Hand-Tracking ein taktiles Gefühl schaffen können.</span><span class="sxs-lookup"><span data-stu-id="263d2-267">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="263d2-268">Das detaillierte Design und die Entwicklungsgeschichte finden Sie in der Microsoft MR Dev Days-Sitzung [Erfahrungen aus der Surfaces-App](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App).</span><span class="sxs-lookup"><span data-stu-id="263d2-268">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="263d2-269">Sitzungsvideos von den Mixed Reality Dev Days 2020</span><span class="sxs-lookup"><span data-stu-id="263d2-269">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="263d2-270">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="263d2-270">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="263d2-271">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="263d2-271">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="263d2-272">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="263d2-272">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="263d2-273">Tutorial zum Erstellen einer einfachen MRTK-APP von Anfang bis Ende.</span><span class="sxs-lookup"><span data-stu-id="263d2-273">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="263d2-274">Erfahren Sie mehr über Interaktionskonzepte und die plattformübergreifenden Funktionen des MRTK.</span><span class="sxs-lookup"><span data-stu-id="263d2-274">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="263d2-275">Tiefgehende Besprechung der UX-Bausteine des MRTK, die Sie beim Erstellen schöner Mixed Reality-Erfahrungen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="263d2-275">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="263d2-276">Eine Einführung in Leistungstools, sowohl die in MRTK enthaltenen als auch externe, sowie eine Übersicht zum MRTK-Standardshader.</span><span class="sxs-lookup"><span data-stu-id="263d2-276">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="263d2-277">Weitere Sitzungsvideos finden Sie unter [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions).</span><span class="sxs-lookup"><span data-stu-id="263d2-277">See [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="263d2-278">Mit der Community in Kontakt treten</span><span class="sxs-lookup"><span data-stu-id="263d2-278">Engage with the community</span></span>

* <span data-ttu-id="263d2-279">Nehmen Sie an der Unterhaltung über MRTK bei [Slack](https://holodevelopers.slack.com/) teil.</span><span class="sxs-lookup"><span data-stu-id="263d2-279">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="263d2-280">Sie können der Slack-Community über den [automatischen Einladungsversender](https://holodevelopersslack.azurewebsites.net/) beitreten.</span><span class="sxs-lookup"><span data-stu-id="263d2-280">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="263d2-281">Stellen Sie Fragen zur Verwendung des MRTK bei [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) unter Verwendung des Tags **MRTK**.</span><span class="sxs-lookup"><span data-stu-id="263d2-281">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="263d2-282">Suchen Sie nach [bekannten Problemen](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues), oder melden Sie ein [neues Problem](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues), wenn Sie einen Defekt im MRTK-Code finden.</span><span class="sxs-lookup"><span data-stu-id="263d2-282">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="263d2-283">Wenn Sie Fragen zur Mitwirkung am MRTK haben, besuchen Sie den [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858)-Kanal in Slack.</span><span class="sxs-lookup"><span data-stu-id="263d2-283">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="263d2-284">Für dieses Projekt gelten die Microsoft-Verhaltensregeln für Open Source ([Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/)).</span><span class="sxs-lookup"><span data-stu-id="263d2-284">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="263d2-285">Um weitere Informationen zu erhalten, lesen Sie die häufig gestellten Fragen zu den Verhaltensregeln ([Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)), oder wenden Sie sich mit weiteren Fragen und Kommentaren an [opencode@microsoft.com](mailto:opencode@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="263d2-285">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="263d2-286">Nützliche Ressourcen im Mixed Reality Dev Center</span><span class="sxs-lookup"><span data-stu-id="263d2-286">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="263d2-287">![Erkunden](features/images/mrdevcenter/icon-discover.png) [Erkunden](/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="263d2-287">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](/windows/mixed-reality/)</span></span>| <span data-ttu-id="263d2-288">![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="263d2-288">![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)</span></span>| <span data-ttu-id="263d2-289">![Entwicklung](features/images/mrdevcenter/icon-develop.png) [Entwicklung](/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="263d2-289">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](/windows/mixed-reality/development)</span></span>| <span data-ttu-id="263d2-290">![Verteilen](features/images/mrdevcenter/icon-distribute.png) [Verteilen](/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="263d2-290">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="263d2-291">Erfahren Sie, wie Sie Mixed Reality-Erfahrungen für HoloLens und immersive Headsets (VR) entwickeln.</span><span class="sxs-lookup"><span data-stu-id="263d2-291">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="263d2-292">Erhalten Sie Entwurfshandbücher.</span><span class="sxs-lookup"><span data-stu-id="263d2-292">Get design guides.</span></span> <span data-ttu-id="263d2-293">Erstellen von Benutzeroberflächen.</span><span class="sxs-lookup"><span data-stu-id="263d2-293">Build user interface.</span></span> <span data-ttu-id="263d2-294">Erfahren Sie mehr über Interaktionen und Eingaben.</span><span class="sxs-lookup"><span data-stu-id="263d2-294">Learn interactions and input.</span></span>     | <span data-ttu-id="263d2-295">Erhalten Sie Entwicklungshandbücher.</span><span class="sxs-lookup"><span data-stu-id="263d2-295">Get development guides.</span></span> <span data-ttu-id="263d2-296">Lernen Sie die Technologie kennen.</span><span class="sxs-lookup"><span data-stu-id="263d2-296">Learn the technology.</span></span> <span data-ttu-id="263d2-297">Verstehen der wissenschaftlichen Aspekte.</span><span class="sxs-lookup"><span data-stu-id="263d2-297">Understand the science.</span></span>       | <span data-ttu-id="263d2-298">Bereiten Sie Ihre App für andere Benutzer vor, und erstellen Sie ggf. ein 3D-Startprogramm.</span><span class="sxs-lookup"><span data-stu-id="263d2-298">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="263d2-299">Nützliche Ressourcen in Azure</span><span class="sxs-lookup"><span data-stu-id="263d2-299">Useful resources on Azure</span></span>

| <span data-ttu-id="263d2-300">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="263d2-300">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="263d2-301">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="263d2-301">Spatial Anchors</span></span>](/azure/spatial-anchors/)| <span data-ttu-id="263d2-302">![Speech-Dienste](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech-Dienste](/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="263d2-302">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="263d2-303">![Bildverarbeitungsdienste](features/images/mrdevcenter/icon-azurevisionservices.png) [Bildverarbeitungsdienste](/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="263d2-303">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="263d2-304">Spatial Anchors ist ein plattformübergreifender Dienst, mit dem Sie Mixed Reality-Erlebnisse mit Objekten erstellen können, die ihre Positionen auf Geräten im Zeitverlauf beibehalten.</span><span class="sxs-lookup"><span data-stu-id="263d2-304">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="263d2-305">Erforschen Sie Azure-basierte Sprachfunktionen wie Sprache-in-Text, Sprechererkennung und Sprachübersetzung, und integrieren Sie diese in Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="263d2-305">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="263d2-306">Erkennen und analysieren Sie Ihre Bild- oder Videoinhalte mithilfe von Bildverarbeitungsdiensten wie maschinelles Sehen, Gesichtserkennung, Emotionserkennung oder Video-Indexer.</span><span class="sxs-lookup"><span data-stu-id="263d2-306">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="263d2-307">Beitragen</span><span class="sxs-lookup"><span data-stu-id="263d2-307">How to contribute</span></span>

<span data-ttu-id="263d2-308">Erfahren Sie, wie Sie beim MRTK mitwirken können, unter [Mitwirkung](contributing/contributing.md).</span><span class="sxs-lookup"><span data-stu-id="263d2-308">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="263d2-309">Hilfe</span><span class="sxs-lookup"><span data-stu-id="263d2-309">Getting help</span></span>

<span data-ttu-id="263d2-310">Wenn Probleme auftreten, die vom MRTK verursacht wurden, oder wenn Sie anderweitige Fragen zu Vorgehensweisen haben, gibt es einige Ressourcen, die Ihnen helfen können:</span><span class="sxs-lookup"><span data-stu-id="263d2-310">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="263d2-311">Bei Fehlerberichten [melden Sie ein Problem](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) im GitHub-Repository.</span><span class="sxs-lookup"><span data-stu-id="263d2-311">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="263d2-312">Wenn Sie Fragen haben, wenden Sie sich entweder an [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) oder an den [mixed-reality-toolkit-Kanal](https://holodevelopers.slack.com/messages/C2H4HT858) in Slack.</span><span class="sxs-lookup"><span data-stu-id="263d2-312">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="263d2-313">Sie können der Slack-Community über den [automatischen Einladungsversender](https://holodevelopersslack.azurewebsites.net/) beitreten.</span><span class="sxs-lookup"><span data-stu-id="263d2-313">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>