---
title: Verwenden des gemischten Reality openxr-Plug-Ins für Unity
description: Erfahren Sie, wie Sie das gemischte Open-Plug-in für Unity für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, Mixed Reality, mrtk, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, erlernen, Tutorial, Getting Started
ms.openlocfilehash: 6e300c6117e04e2a49b060bcd7a6d268204f14da
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105937481"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="88fa1-104">Verwenden des gemischten Reality openxr-Plug-Ins für Unity</span><span class="sxs-lookup"><span data-stu-id="88fa1-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="88fa1-105">Ab Unity, Version 2020,2, ist das gemischte openxr-Plug-in-Paket von Microsoft mit dem Unity-Paket-Manager (UPM) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="88fa1-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88fa1-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="88fa1-106">Prerequisites</span></span>

* <span data-ttu-id="88fa1-107">Unity 2020,3 LTS oder höher</span><span class="sxs-lookup"><span data-stu-id="88fa1-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="88fa1-108">Unity openxr Plugin 1.0.3 oder höher</span><span class="sxs-lookup"><span data-stu-id="88fa1-108">Unity OpenXR plugin 1.0.3 or later</span></span>
* <span data-ttu-id="88fa1-109">Visual Studio 2019 oder höher</span><span class="sxs-lookup"><span data-stu-id="88fa1-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="88fa1-110">Installieren der **UWP** -Platt Form Unterstützung in Unity für hololens 2-apps</span><span class="sxs-lookup"><span data-stu-id="88fa1-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="88fa1-111">Wenn Sie VR-Anwendungen auf einem Windows-PC entwickeln, ist das gemischte openxr-Plug-in für die gemischte Realität nicht unbedingt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="88fa1-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="88fa1-112">Sie sollten das Plug-in jedoch installieren, wenn Sie die Controller Zuordnung für HP-Reverb-G2-Controller anpassen oder apps entwickeln, die sowohl für hololens 2-als auch für VR-Headsets geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="88fa1-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

<!-- ## Setting up your project with MRTK

MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions. MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform. The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.

> [!div class="nextstepaction"]
> [Set up your project using MRTK](tutorials/mr-learning-base-01.md)

Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details. -->

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="88fa1-113">Manuelles Setup ohne mrtk</span><span class="sxs-lookup"><span data-stu-id="88fa1-113">Manual setup without MRTK</span></span>

<span data-ttu-id="88fa1-114">Installieren Sie das openxr-Plug-in mit der neuen Anwendung Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="88fa1-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="88fa1-115">Befolgen Sie die [Installations-und Verwendungs Anweisungen](welcome-to-mr-feature-tool.md) , und wählen Sie das **gemischte openxr-Plug** -in in der Kategorie Mixed Reality-Toolkit aus:</span><span class="sxs-lookup"><span data-stu-id="88fa1-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Fenster "Mixed Reality Feature Tool Packages" mit hervorgehobenem Open XR](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="88fa1-117">Festlegen des Buildziels</span><span class="sxs-lookup"><span data-stu-id="88fa1-117">Setting your build target</span></span>

<span data-ttu-id="88fa1-118">Wenn Sie auf Desktop VR abzielen, empfiehlt es sich, die eigenständige PC-Plattform zu verwenden, die für ein neues Unity-Projekt standardmäßig ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="88fa1-118">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit PC, Mac & eigenständige Plattform hervorgehoben](images/wmr-config-img-3.png)

<span data-ttu-id="88fa1-120">Wenn Sie hololens 2 als Ziel verwenden, müssen Sie zum universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="88fa1-120">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="88fa1-121">**Datei > Buildeinstellungen auswählen...**</span><span class="sxs-lookup"><span data-stu-id="88fa1-121">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="88fa1-122">Wählen Sie in der Platt Form Liste **universelle Windows-Plattform** aus, und wählen Sie **Plattform wechseln**</span><span class="sxs-lookup"><span data-stu-id="88fa1-122">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="88fa1-123">**Architektur** auf **Arm 64** festlegen</span><span class="sxs-lookup"><span data-stu-id="88fa1-123">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="88fa1-124">**Zielgerät** auf **hololens** festlegen</span><span class="sxs-lookup"><span data-stu-id="88fa1-124">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="88fa1-125">**Buildtyp** auf **D3D** festlegen</span><span class="sxs-lookup"><span data-stu-id="88fa1-125">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="88fa1-126">**UWP SDK** auf **Letztes installiert** festlegen</span><span class="sxs-lookup"><span data-stu-id="88fa1-126">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="88fa1-127">**Buildkonfiguration** auf **Release** festlegen, da beim Debuggen bekannte Leistungsprobleme auftreten</span><span class="sxs-lookup"><span data-stu-id="88fa1-127">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor öffnen mit hervorgehobener universelle Windows-Plattform](images/wmr-config-img-4.png)

<span data-ttu-id="88fa1-129">Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass Sie beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellen soll.</span><span class="sxs-lookup"><span data-stu-id="88fa1-129">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="88fa1-130">Konfigurieren der XR-Plug-in-Verwaltung für openxr</span><span class="sxs-lookup"><span data-stu-id="88fa1-130">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="88fa1-131">So legen Sie openxr als Lauf Zeit Modul in Unity fest:</span><span class="sxs-lookup"><span data-stu-id="88fa1-131">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="88fa1-132">Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen** .</span><span class="sxs-lookup"><span data-stu-id="88fa1-132">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="88fa1-133">Wählen Sie in der Liste der Einstellungen die Option " **XR Plugin Management** "</span><span class="sxs-lookup"><span data-stu-id="88fa1-133">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="88fa1-134">Aktivieren Sie die Kontrollkästchen " **XR beim Start** " und " **openxr** initialisieren</span><span class="sxs-lookup"><span data-stu-id="88fa1-134">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="88fa1-135">Wenn Sie auf hololens 2 abzielen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform befinden, und wählen Sie " **Microsoft hololens Feature**</span><span class="sxs-lookup"><span data-stu-id="88fa1-135">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-in-Verwaltung](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="88fa1-137">Optimization</span><span class="sxs-lookup"><span data-stu-id="88fa1-137">Optimization</span></span>

<span data-ttu-id="88fa1-138">Wenn Sie für hololens 2 entwickeln, navigieren Sie zu **gemischte Realität> openxr > die empfohlenen Projekteinstellungen für hololens 2 anwenden** , um eine bessere App-Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="88fa1-138">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot des Menü Elements mit gemischter Realität geöffnet mit ausgewähltem openxr](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="88fa1-140">Wenn ein rotes Warnsymbol neben **openxr-Plug-in (Vorschau)** angezeigt wird, klicken Sie auf das Symbol, und wählen Sie **alle korrigieren** , bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="88fa1-140">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="88fa1-141">Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="88fa1-141">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot des Fensters "openxr Project Validation"](images/openxr-img-06.png)

<span data-ttu-id="88fa1-143">Sie sind nun bereit, mit der Entwicklung mit openxr in Unity zu beginnen!</span><span class="sxs-lookup"><span data-stu-id="88fa1-143">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="88fa1-144">Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die openxr-Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="88fa1-144">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="88fa1-145">Ausprobieren der Unity-Beispiel Szenen</span><span class="sxs-lookup"><span data-stu-id="88fa1-145">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="88fa1-146">Hololens 2-Beispiele</span><span class="sxs-lookup"><span data-stu-id="88fa1-146">HoloLens 2 samples</span></span>

1. <span data-ttu-id="88fa1-147">Navigieren Sie im Unity-Editor zu **Fenster > Paket-Manager** .</span><span class="sxs-lookup"><span data-stu-id="88fa1-147">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="88fa1-148">Wählen Sie in der Liste der Pakete **gemischte Realität openxr-Plug** -in aus.</span><span class="sxs-lookup"><span data-stu-id="88fa1-148">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="88fa1-149">Suchen Sie das Beispiel in der Liste **Samples** , und wählen Sie **importieren** aus.</span><span class="sxs-lookup"><span data-stu-id="88fa1-149">Locate the sample in the **Samples** list and select **Import**</span></span>

![Screenshot: Öffnen des Unity-Paket-Managers im Unity-Editor mit aktiviertem aktiviertem openxr-Plug-in](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="88fa1-151">Wenn ein Paket aktualisiert wird, bietet Unity die Option zum Aktualisieren importierter Beispiele.</span><span class="sxs-lookup"><span data-stu-id="88fa1-151">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="88fa1-152">Durch das Aktualisieren eines importierten Beispiels werden alle Änderungen überschrieben, die an dem Beispiel und den zugehörigen Assets vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="88fa1-152">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="88fa1-153">Verwenden von mrtk mit openxr-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="88fa1-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="88fa1-154">MRTK-Unity unterstützt das Mixed Reality openxr-Plug-in, beginnend mit der 2.5.3-Version.</span><span class="sxs-lookup"><span data-stu-id="88fa1-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="88fa1-155">Öffnen Sie das [Mixed Reality-Feature-Tool](welcome-to-mr-feature-tool.md) erneut, um das Mixed Reality Toolkit zu installieren, falls Sie dies noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="88fa1-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="88fa1-156">Openxr-Unterstützung ist im **Foundation** -Paket.</span><span class="sxs-lookup"><span data-stu-id="88fa1-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="88fa1-157">Wechseln Sie zum Skript "mixedreality Toolkit-Komponente" im Inspektor, und wechseln Sie zum Profil " **defaultoperxrconfigurationprofile** ":</span><span class="sxs-lookup"><span data-stu-id="88fa1-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Screenshot: Wechseln der mrtk-Konfiguration in der Mixed Reality Toolkit-Komponente im Inspektor](images/openxr-img-11.png)

    1. <span data-ttu-id="88fa1-159">[Ausführliche Informationen zum Migrieren zu openxr finden Sie in](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)der Dokumentation zu mrtk.</span><span class="sxs-lookup"><span data-stu-id="88fa1-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="88fa1-160">Wenn Sie von einer früheren Version von mrtk aktualisieren, stellen Sie sicher, dass sich die folgende Zeile in der Datei **Assets/mixedrealitytoolkit. generated/link.xml** befindet:</span><span class="sxs-lookup"><span data-stu-id="88fa1-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="88fa1-161">Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit mrtk 2.5.4 oder höher gestartet haben.</span><span class="sxs-lookup"><span data-stu-id="88fa1-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="88fa1-162">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="88fa1-162">Next steps</span></span>

<span data-ttu-id="88fa1-163">Nachdem Sie Ihr Projekt für openxr konfiguriert haben und Zugriff auf Beispiele haben, sehen Sie sich an, welche [Features](openxr-supported-features.md) derzeit in unserem openxr-Plug-in unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="88fa1-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="88fa1-164">Haben Sie Feedback?</span><span class="sxs-lookup"><span data-stu-id="88fa1-164">Have Feedback?</span></span>

<span data-ttu-id="88fa1-165">Openxr ist noch immer experimentell. Wir freuen uns über jedes Feedback, das Sie uns zur Verbesserung der IT-Unterstützung bieten können.</span><span class="sxs-lookup"><span data-stu-id="88fa1-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="88fa1-166">Sie finden uns in den [Unity-Foren](https://aka.ms/unityforums) , indem Sie Ihren Forumsbeitrag mit **Microsoft**  +  **openxr** und entweder **hololens 2** oder **Windows Mixed Reality** markieren.</span><span class="sxs-lookup"><span data-stu-id="88fa1-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="88fa1-167">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88fa1-167">See also</span></span>

* [<span data-ttu-id="88fa1-168">Konfigurieren von Projekten ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="88fa1-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="88fa1-169">Empfohlene Einstellungen für Unity</span><span class="sxs-lookup"><span data-stu-id="88fa1-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="88fa1-170">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="88fa1-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
