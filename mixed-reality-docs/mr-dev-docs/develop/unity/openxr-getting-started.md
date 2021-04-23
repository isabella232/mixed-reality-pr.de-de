---
title: Verwenden des Mixed Reality OpenXR-Plug-Ins für Unity
description: Erfahren Sie, wie Sie das Mixed Reality OpenXR-Plug-In für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality Headsets, Learn, Tutorial, Erste Schritte
ms.openlocfilehash: 97169507e2b61110d2d16580ba957feff3755258
ms.sourcegitcommit: aca5fddb98fbbd9aa22bdf8174d7fdcdb9d4c08a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2021
ms.locfileid: "107894018"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="51592-104">Verwenden des Mixed Reality OpenXR-Plug-Ins für Unity</span><span class="sxs-lookup"><span data-stu-id="51592-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="51592-105">Ab Unity Version 2020.2 ist das OpenXR-Plug-In-Paket von Microsoft Mixed Reality über die Unity Paket-Manager (UPM) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="51592-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="51592-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="51592-106">Prerequisites</span></span>

* <span data-ttu-id="51592-107">Unity 2020.3 LTS oder höher</span><span class="sxs-lookup"><span data-stu-id="51592-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="51592-108">Unity OpenXR-Plug-In 1.1.1 oder höher</span><span class="sxs-lookup"><span data-stu-id="51592-108">Unity OpenXR plugin 1.1.1 or later</span></span>
* <span data-ttu-id="51592-109">Visual Studio 2019 oder höher</span><span class="sxs-lookup"><span data-stu-id="51592-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="51592-110">Installieren der **UWP-Plattformunterstützung** in Unity für HoloLens 2-Apps</span><span class="sxs-lookup"><span data-stu-id="51592-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="51592-111">Wenn Sie VR-Anwendungen auf einem Windows-PC erstellen, ist das Mixed Reality OpenXR-Plug-In nicht unbedingt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="51592-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="51592-112">Sie sollten das Plug-In jedoch installieren, wenn Sie die Controllerzuordnung für HP Reverb G2-Controller anpassen oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.</span><span class="sxs-lookup"><span data-stu-id="51592-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="51592-113">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="51592-113">Setting up your project with MRTK</span></span>

<span data-ttu-id="51592-114">MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="51592-114">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="51592-115">MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="51592-115">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="51592-116">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.</span><span class="sxs-lookup"><span data-stu-id="51592-116">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="51592-117">Einrichten Ihres Projekts mit mrtk</span><span class="sxs-lookup"><span data-stu-id="51592-117">Set up your project using MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="51592-118">Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="51592-118">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="51592-119">Manuelle Einrichtung ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="51592-119">Manual setup without MRTK</span></span>

<span data-ttu-id="51592-120">Installieren Sie das OpenXR-Plug-In mit der neuen Anwendung Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="51592-120">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="51592-121">Befolgen Sie die [Installations- und Nutzungsanweisungen,](welcome-to-mr-feature-tool.md) und wählen Sie das **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie Mixed Reality Toolkit aus:</span><span class="sxs-lookup"><span data-stu-id="51592-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Mixed Reality Fenster "Featuretoolpakete" mit hervorgehobener Hervorhebung des geöffneten xr-Plug-Ins](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="51592-123">Festlegen des Buildziels</span><span class="sxs-lookup"><span data-stu-id="51592-123">Setting your build target</span></span>

<span data-ttu-id="51592-124">Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="51592-124">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](images/wmr-config-img-3.png)

<span data-ttu-id="51592-126">Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:</span><span class="sxs-lookup"><span data-stu-id="51592-126">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="51592-127">Wählen **Sie Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="51592-127">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="51592-128">Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**</span><span class="sxs-lookup"><span data-stu-id="51592-128">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="51592-129">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="51592-129">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="51592-130">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="51592-130">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="51592-131">Legen Sie **Buildtyp** auf **D3D** fest</span><span class="sxs-lookup"><span data-stu-id="51592-131">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="51592-132">Legen Sie **UWP SDK** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="51592-132">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="51592-133">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="51592-133">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

<span data-ttu-id="51592-135">Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="51592-135">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="51592-136">Konfigurieren der XR-Plug-In-Verwaltung für OpenXR</span><span class="sxs-lookup"><span data-stu-id="51592-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="51592-137">So legen Sie OpenXR als Runtime in Unity fest:</span><span class="sxs-lookup"><span data-stu-id="51592-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="51592-138">Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="51592-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="51592-139">Wählen Sie in der Liste der Einstellungen **XR-Plug-In-Verwaltung aus.**</span><span class="sxs-lookup"><span data-stu-id="51592-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="51592-140">Aktivieren Sie die **Kontrollkästchen XR beim Start initialisieren** und **OpenXR.**</span><span class="sxs-lookup"><span data-stu-id="51592-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="51592-141">Wenn Sie HoloLens 2 auswählen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform sind, und wählen **Sie Microsoft HoloLens Feature Set (Featuresatz) aus.**</span><span class="sxs-lookup"><span data-stu-id="51592-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot des im Unity-Editor geöffneten Projekteinstellungspanels mit hervorgehobener XR-Plug-In-Verwaltung](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="51592-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="51592-143">Optimization</span></span>

<span data-ttu-id="51592-144">Wenn Sie für HoloLens 2 entwickeln, navigieren Sie zu Mixed Reality> **OpenXR >** Empfohlene Projekteinstellungen für HoloLens 2 anwenden, um eine bessere App-Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="51592-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot des geöffneten Mixed Reality-Menüelements mit ausgewählter Option "OpenXR"](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="51592-146">Wenn neben Dem OpenXR-Plug-In ein rotes **Warnsymbol** angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alles korrigieren aus,** bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="51592-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="51592-147">Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="51592-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot des OpenXR-Projektüberprüfungsfensters](images/openxr-img-06.png)

<span data-ttu-id="51592-149">Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen.</span><span class="sxs-lookup"><span data-stu-id="51592-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="51592-150">Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="51592-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="51592-151">Testen der Unity-Beispielszenen</span><span class="sxs-lookup"><span data-stu-id="51592-151">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="51592-152">HoloLens 2 Beispiele</span><span class="sxs-lookup"><span data-stu-id="51592-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="51592-153">Navigieren Sie im Unity-Editor zu **Fenster > Paket-Manager**</span><span class="sxs-lookup"><span data-stu-id="51592-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="51592-154">Wählen Sie in der Liste der Pakete **Mixed Reality OpenXR-Plug-In** aus.</span><span class="sxs-lookup"><span data-stu-id="51592-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="51592-155">Suchen Sie das Beispiel in der Liste **Beispiele,** und wählen Sie **Importieren** aus.</span><span class="sxs-lookup"><span data-stu-id="51592-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![Screenshot: Unity-Paket-Manager im Unity-Editor geöffnet, wobei Mixed Reality OpenXR-Plug-In ausgewählt und die Schaltfläche zum Importieren von Beispielen hervorgehoben ist](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="51592-157">Wenn ein Paket aktualisiert wird, bietet Unity die Option zum Aktualisieren importierter Beispiele.</span><span class="sxs-lookup"><span data-stu-id="51592-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="51592-158">Beim Aktualisieren eines importierten Beispiels werden alle Änderungen überschrieben, die am Beispiel und den zugehörigen Ressourcen vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="51592-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="51592-159">Verwenden von MRTK mit OpenXR-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="51592-159">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="51592-160">MRTK-Unity unterstützt das Mixed Reality OpenXR-Plug-In ab Version 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="51592-160">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="51592-161">Öffnen Sie das [Mixed Reality Feature-Tool](welcome-to-mr-feature-tool.md) erneut, um das Mixed Reality Toolkit zu installieren, sofern noch nicht erfolgt.</span><span class="sxs-lookup"><span data-stu-id="51592-161">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="51592-162">OpenXR-Unterstützung ist im **Foundation-Paket** enthalten.</span><span class="sxs-lookup"><span data-stu-id="51592-162">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="51592-163">Wechseln Sie im Inspector zum MixedReality Toolkit-Komponentenskript, und wechseln Sie zum Profil **DefaultOpenXRConfigurationProfile:**</span><span class="sxs-lookup"><span data-stu-id="51592-163">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Screenshot: Wechseln der MRTK-Konfiguration in der Mixed Reality Toolkit-Komponente im Inspektor](images/openxr-img-11.png)

    1. <span data-ttu-id="51592-165">[Ausführlichere Informationen zur Migration zu OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)finden Sie in der MRTK-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="51592-165">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="51592-166">Stellen Sie beim Upgrade von einer früheren Version von MRTK sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:</span><span class="sxs-lookup"><span data-stu-id="51592-166">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="51592-167">Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer gestartet haben.</span><span class="sxs-lookup"><span data-stu-id="51592-167">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="51592-168">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="51592-168">Next steps</span></span>

<span data-ttu-id="51592-169">Nachdem Sie Ihr Projekt für OpenXR konfiguriert haben und Zugriff auf Beispiele haben, sehen Sie sich an, welche [Features](openxr-supported-features.md) derzeit in unserem OpenXR-Plug-In unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="51592-169">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="51592-170">Haben Sie Feedback?</span><span class="sxs-lookup"><span data-stu-id="51592-170">Have Feedback?</span></span>

<span data-ttu-id="51592-171">OpenXR ist noch experimentell, daher würden wir uns über feedback freuen, das Sie uns geben können, um das Ergebnis zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="51592-171">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="51592-172">Sie finden uns in den [Unity-Foren,](https://aka.ms/unityforums) indem Sie Ihren Forumbeitrag mit **Microsoft**  +  **OpenXR** markieren und entweder **HoloLens 2** oder **Windows Mixed Reality.**</span><span class="sxs-lookup"><span data-stu-id="51592-172">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="51592-173">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="51592-173">See also</span></span>

* [<span data-ttu-id="51592-174">Konfigurieren von Projekten ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="51592-174">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="51592-175">Empfohlene Einstellungen für Unity</span><span class="sxs-lookup"><span data-stu-id="51592-175">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="51592-176">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="51592-176">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
