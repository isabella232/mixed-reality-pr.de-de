---
title: Verwenden des Mixed Reality OpenXR-Plug-Ins für Unity
description: Erfahren Sie, wie Sie das Mixed Reality OpenXR-Plug-In für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte
ms.openlocfilehash: 4c220deeca13c6807857375b71640207823b94ed
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944661"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="66f3d-104">Verwenden des Mixed Reality OpenXR-Plug-Ins für Unity</span><span class="sxs-lookup"><span data-stu-id="66f3d-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="66f3d-105">Ab Unity Version 2020.2 ist das Microsoft Mixed Reality OpenXR-Plug-In-Paket mit dem Mixed Reality [Feature Tool verfügbar.](welcome-to-mr-feature-tool.md)</span><span class="sxs-lookup"><span data-stu-id="66f3d-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="66f3d-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="66f3d-106">Prerequisites</span></span>

* <span data-ttu-id="66f3d-107">Unity 2020.3 LTS oder höher</span><span class="sxs-lookup"><span data-stu-id="66f3d-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="66f3d-108">Unity OpenXR-Plug-In 1.1.1 oder höher</span><span class="sxs-lookup"><span data-stu-id="66f3d-108">Unity OpenXR plugin 1.1.1 or later</span></span>
* <span data-ttu-id="66f3d-109">Visual Studio 2019 oder höher</span><span class="sxs-lookup"><span data-stu-id="66f3d-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="66f3d-110">Installieren **der UWP-Plattformunterstützung** in Unity für HoloLens 2 Apps</span><span class="sxs-lookup"><span data-stu-id="66f3d-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="66f3d-111">Wenn Sie VR-Anwendungen auf einem Windows-PC erstellen, ist Mixed Reality OpenXR-Plug-In nicht unbedingt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66f3d-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="66f3d-112">Sie sollten das Plug-In jedoch installieren, wenn Sie die Controllerzuordnung für HP Reverb G2-Controller anpassen oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.</span><span class="sxs-lookup"><span data-stu-id="66f3d-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="66f3d-113">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="66f3d-113">Setting up your project with MRTK</span></span>

<span data-ttu-id="66f3d-114">MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="66f3d-114">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="66f3d-115">MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="66f3d-115">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="66f3d-116">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.</span><span class="sxs-lookup"><span data-stu-id="66f3d-116">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66f3d-117">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="66f3d-117">Set up your project using MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="66f3d-118">Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="66f3d-118">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="66f3d-119">Manuelle Einrichtung ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="66f3d-119">Manual setup without MRTK</span></span>

<span data-ttu-id="66f3d-120">Installieren Sie das OpenXR-Plug-In mit der neuen Mixed Reality Feature Tool-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="66f3d-120">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="66f3d-121">Befolgen Sie [die Installations- und Verwendungsanweisungen,](welcome-to-mr-feature-tool.md) und wählen Sie **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie Mixed Reality Toolkit aus:</span><span class="sxs-lookup"><span data-stu-id="66f3d-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Mixed Reality fenster feature tool packages with open xr plugin (Öffnen des XR-Plug-Ins hervorgehoben)](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="66f3d-123">Festlegen des Buildziels</span><span class="sxs-lookup"><span data-stu-id="66f3d-123">Setting your build target</span></span>

<span data-ttu-id="66f3d-124">Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="66f3d-124">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](images/wmr-config-img-3.png)

<span data-ttu-id="66f3d-126">Wenn Sie HoloLens 2 als Ziel haben, müssen Sie zum Universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="66f3d-126">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="66f3d-127">Wählen Sie **Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="66f3d-127">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="66f3d-128">Wählen Sie **Universelle Windows-Plattform** in der Liste Plattform und dann **Plattform wechseln** aus.</span><span class="sxs-lookup"><span data-stu-id="66f3d-128">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="66f3d-129">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="66f3d-129">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="66f3d-130">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="66f3d-130">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="66f3d-131">Legen Sie **Buildtyp** auf **D3D** fest</span><span class="sxs-lookup"><span data-stu-id="66f3d-131">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="66f3d-132">Legen Sie **UWP SDK** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="66f3d-132">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="66f3d-133">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="66f3d-133">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot: Fenster "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

<span data-ttu-id="66f3d-135">Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="66f3d-135">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="66f3d-136">Konfigurieren der XR-Plug-In-Verwaltung für OpenXR</span><span class="sxs-lookup"><span data-stu-id="66f3d-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="66f3d-137">So legen Sie OpenXR als Runtime in Unity fest:</span><span class="sxs-lookup"><span data-stu-id="66f3d-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="66f3d-138">Navigieren Sie im Unity-Editor zu **> Projekteinstellungen bearbeiten.**</span><span class="sxs-lookup"><span data-stu-id="66f3d-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="66f3d-139">Wählen Sie in der Liste der Einstellungen die Option **XR-Plug-In-Verwaltung** aus.</span><span class="sxs-lookup"><span data-stu-id="66f3d-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="66f3d-140">Aktivieren Sie die Felder **XR beim Start initialisieren** und **OpenXR.**</span><span class="sxs-lookup"><span data-stu-id="66f3d-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="66f3d-141">Wenn Sie HoloLens 2 als Ziel verwenden, stellen Sie sicher, dass Sie sich auf der UWP-Plattform befindet, und wählen Sie **Microsoft HoloLens Featuresatz aus.**</span><span class="sxs-lookup"><span data-stu-id="66f3d-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot des im Unity-Editor geöffneten Bereichs "Projekteinstellungen" mit hervorgehobener XR-Plug-In-Verwaltung](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="66f3d-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="66f3d-143">Optimization</span></span>

<span data-ttu-id="66f3d-144">Wenn Sie für HoloLens 2 entwickeln, navigieren Sie zu **Mixed Reality> OpenXR > Empfohlene Projekteinstellungen für HoloLens 2** anwenden, um eine bessere App-Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="66f3d-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot: Geöffnetes Mixed Reality-Menüelement mit ausgewählter Option "OpenXR"](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="66f3d-146">Wenn neben **OpenXR-Plug-In** ein rotes Warnsymbol angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alle korrigieren** aus, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="66f3d-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="66f3d-147">Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="66f3d-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot des Fensters "OpenXR-Projektvalidierung"](images/openxr-img-06.png)

<span data-ttu-id="66f3d-149">Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen!</span><span class="sxs-lookup"><span data-stu-id="66f3d-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="66f3d-150">Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="66f3d-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="66f3d-151">Probieren Sie die Unity-Beispielszenen aus.</span><span class="sxs-lookup"><span data-stu-id="66f3d-151">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="66f3d-152">HoloLens 2 Beispiele</span><span class="sxs-lookup"><span data-stu-id="66f3d-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="66f3d-153">Navigieren Sie im Unity-Editor zu **Fenster > Paket-Manager**</span><span class="sxs-lookup"><span data-stu-id="66f3d-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="66f3d-154">Wählen Sie in der Liste der Pakete Mixed Reality **OpenXR-Plug-In aus.**</span><span class="sxs-lookup"><span data-stu-id="66f3d-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="66f3d-155">Suchen Sie das Beispiel in der Liste **Beispiele,** und wählen Sie **Importieren aus.**</span><span class="sxs-lookup"><span data-stu-id="66f3d-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![Screenshot: Unity-Paket-Manager im Unity-Editor geöffnet, Mixed Reality OpenXR-Plug-In ausgewählt und schaltfläche "Beispiele importieren" hervorgehoben](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="66f3d-157">Wenn ein Paket aktualisiert wird, bietet Unity die Option zum Aktualisieren importierter Beispiele.</span><span class="sxs-lookup"><span data-stu-id="66f3d-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="66f3d-158">Durch das Aktualisieren eines importierten Beispiels werden alle Änderungen überschrieben, die am Beispiel und den zugehörigen Ressourcen vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="66f3d-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="66f3d-159">Verwenden von MRTK mit OpenXR-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="66f3d-159">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="66f3d-160">MRTK-Unity unterstützt das Mixed Reality OpenXR-Plug-In ab Version 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="66f3d-160">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="66f3d-161">Öffnen Sie [Mixed Reality Featuretool erneut,](welcome-to-mr-feature-tool.md) um das Mixed Reality Toolkit zu installieren, sofern noch nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="66f3d-161">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="66f3d-162">OpenXR-Unterstützung ist im **Foundation-Paket** enthalten.</span><span class="sxs-lookup"><span data-stu-id="66f3d-162">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="66f3d-163">Wechseln Sie im Inspector zum MixedReality Toolkit-Komponentenskript, und wechseln Sie zum **Profil DefaultOpenXRConfigurationProfile:**</span><span class="sxs-lookup"><span data-stu-id="66f3d-163">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Screenshot: Wechseln der MRTK-Konfiguration in der Mixed Reality Toolkit-Komponente im Inspektor](images/openxr-img-11.png)

    1. <span data-ttu-id="66f3d-165">Weitere ausführliche Informationen zur Migration zu OpenXR finden Sie in der [MRTK-Dokumentation.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)</span><span class="sxs-lookup"><span data-stu-id="66f3d-165">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="66f3d-166">Stellen Sie beim Upgrade von einer früheren Version von MRTK sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:</span><span class="sxs-lookup"><span data-stu-id="66f3d-166">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="66f3d-167">Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer begonnen haben.</span><span class="sxs-lookup"><span data-stu-id="66f3d-167">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="66f3d-168">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="66f3d-168">Next steps</span></span>

<span data-ttu-id="66f3d-169">Nachdem Sie Ihr Projekt für OpenXR konfiguriert haben und Zugriff [](openxr-supported-features.md) auf Beispiele haben, sehen Sie sich an, welche Features derzeit in unserem OpenXR-Plug-In unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="66f3d-169">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="66f3d-170">Haben Sie Feedback?</span><span class="sxs-lookup"><span data-stu-id="66f3d-170">Have Feedback?</span></span>

<span data-ttu-id="66f3d-171">OpenXR ist immer noch experimentell, daher freuen wir uns über jedes Feedback, das Sie uns geben können, um es besser zu machen.</span><span class="sxs-lookup"><span data-stu-id="66f3d-171">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="66f3d-172">Sie finden uns in den [Unity-Foren,](https://aka.ms/unityforums) indem Sie Ihren Forumbeitrag mit **Microsoft**  +  **OpenXR** markieren und **entweder** HoloLens 2 oder **Windows Mixed Reality.**</span><span class="sxs-lookup"><span data-stu-id="66f3d-172">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="66f3d-173">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="66f3d-173">See also</span></span>

* [<span data-ttu-id="66f3d-174">Konfigurieren von Projekten ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="66f3d-174">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="66f3d-175">Empfohlene Einstellungen für Unity</span><span class="sxs-lookup"><span data-stu-id="66f3d-175">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="66f3d-176">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="66f3d-176">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
