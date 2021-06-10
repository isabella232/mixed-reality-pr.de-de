---
title: Verwenden des Mixed Reality OpenXR-Plug-Ins
description: Erfahren Sie, wie Sie das Mixed Reality OpenXR-Plug-In für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte
ms.openlocfilehash: 65b79aadeb52db6be61edcc90a5d4a44c12384a1
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547038"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="299ce-104">Verwenden des Mixed Reality OpenXR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="299ce-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="299ce-105">Für Entwickler, die Unity 2020 zum Erstellen von HoloLens 2- oder Mixed Reality-Anwendungen verwenden, kann das OpenXR-Plug-In anstelle des WindowsXR-Plug-Ins verwendet werden, um plattformübergreifende Kompatibilität zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="299ce-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="299ce-106">Das Mixed Reality OpenXR-Plug-In funktioniert auch gut mit dem neuesten Mixed Reality [Toolkit 2.7.](/windows/mixed-reality/mrtk-unity)</span><span class="sxs-lookup"><span data-stu-id="299ce-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Toolkit 2.7](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="299ce-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="299ce-107">Prerequisites</span></span>

* <span data-ttu-id="299ce-108">Neueste Version von Unity 2020.3 LTS (wir empfehlen 2020.3.8f1 oder höher)</span><span class="sxs-lookup"><span data-stu-id="299ce-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>
* <span data-ttu-id="299ce-109">Neuestes Unity OpenXR-Plug-In (wir empfehlen 1.2 oder höher)</span><span class="sxs-lookup"><span data-stu-id="299ce-109">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="299ce-110">Neueste [Tools für HoloLens 2 Entwicklung](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="299ce-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="299ce-111">Neuestes MRTK (optional), (wir empfehlen Version 2.7 oder höher)</span><span class="sxs-lookup"><span data-stu-id="299ce-111">Latest MRTK (optional), (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="299ce-112">Neueste Mixed Reality OpenXR-Plug-In, (wir empfehlen Version 1.0.0-preview.1 oder höher)</span><span class="sxs-lookup"><span data-stu-id="299ce-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0-preview.1 or later)</span></span>

![Screenshot des offenen xr unity basic-Beispiels, das auf einer HoloLens ausgeführt wird](images/openxr-example.png)

> [!NOTE]
> <span data-ttu-id="299ce-114">Wenn Sie VR-Anwendungen auf einem Windows-PC erstellen, ist Mixed Reality OpenXR-Plug-In nicht unbedingt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="299ce-114">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="299ce-115">Sie sollten das Plug-In jedoch installieren, wenn Sie die Controllerzuordnung für HP Reverb G2-Controller anpassen oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.</span><span class="sxs-lookup"><span data-stu-id="299ce-115">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="299ce-116">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="299ce-116">Setting up your project with MRTK</span></span>

<span data-ttu-id="299ce-117">MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="299ce-117">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="299ce-118">MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="299ce-118">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="299ce-119">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.</span><span class="sxs-lookup"><span data-stu-id="299ce-119">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="299ce-120">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="299ce-120">Set up your project using MRTK</span></span>](./tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="299ce-121">Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="299ce-121">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="299ce-122">Manuelle Einrichtung ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="299ce-122">Manual setup without MRTK</span></span>

<span data-ttu-id="299ce-123">Installieren Sie das OpenXR-Plug-In mit der neuen Mixed Reality-Featuretoolanwendung.</span><span class="sxs-lookup"><span data-stu-id="299ce-123">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="299ce-124">Befolgen Sie [die Installations- und Nutzungsanweisungen,](welcome-to-mr-feature-tool.md) und wählen Sie **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie Mixed Reality Toolkit aus:</span><span class="sxs-lookup"><span data-stu-id="299ce-124">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Mixed Reality fenster feature tool packages with open xr plugin (Öffnen des XR-Plug-Ins hervorgehoben)](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="299ce-126">Festlegen des Buildziels</span><span class="sxs-lookup"><span data-stu-id="299ce-126">Setting your build target</span></span>

<span data-ttu-id="299ce-127">Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="299ce-127">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](images/wmr-config-img-3.png)

<span data-ttu-id="299ce-129">Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:</span><span class="sxs-lookup"><span data-stu-id="299ce-129">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="299ce-130">Wählen **Sie Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="299ce-130">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="299ce-131">Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**</span><span class="sxs-lookup"><span data-stu-id="299ce-131">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="299ce-132">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="299ce-132">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="299ce-133">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="299ce-133">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="299ce-134">Legen Sie **Buildtyp** auf **D3D** fest</span><span class="sxs-lookup"><span data-stu-id="299ce-134">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="299ce-135">Legen Sie **UWP SDK** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="299ce-135">Set **UWP SDK** to **Latest installed**</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="299ce-137">Konfigurieren der XR-Plug-In-Verwaltung für OpenXR</span><span class="sxs-lookup"><span data-stu-id="299ce-137">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="299ce-138">So legen Sie OpenXR als Runtime in Unity fest:</span><span class="sxs-lookup"><span data-stu-id="299ce-138">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="299ce-139">Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="299ce-139">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="299ce-140">Wählen Sie in der Liste der Einstellungen **XR-Plug-In-Verwaltung aus.**</span><span class="sxs-lookup"><span data-stu-id="299ce-140">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="299ce-141">Aktivieren Sie die **Kontrollkästchen XR beim Start initialisieren** und **OpenXR.**</span><span class="sxs-lookup"><span data-stu-id="299ce-141">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="299ce-142">Wenn Sie HoloLens 2 auswählen, stellen Sie sicher, dass Sie auf der UWP-Plattform sind, und wählen **Sie Microsoft HoloLens Feature Set (Featuresatz) aus.**</span><span class="sxs-lookup"><span data-stu-id="299ce-142">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot des im Unity-Editor geöffneten Projekteinstellungspanels mit hervorgehobener XR-Plug-In-Verwaltung](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="299ce-144">Optimization</span><span class="sxs-lookup"><span data-stu-id="299ce-144">Optimization</span></span>

<span data-ttu-id="299ce-145">Wenn Sie für HoloLens 2 entwickeln, navigieren Sie zu Mixed Reality> **OpenXR >** Empfohlene Projekteinstellungen für HoloLens 2 anwenden, um eine bessere App-Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="299ce-145">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot des geöffneten Mixed Reality-Menüelements mit ausgewählter Option "OpenXR"](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="299ce-147">Wenn neben Dem OpenXR-Plug-In ein rotes **Warnsymbol** angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alles korrigieren aus,** bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="299ce-147">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="299ce-148">Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="299ce-148">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot des OpenXR-Projektüberprüfungsfensters](images/openxr-img-06.png)

<span data-ttu-id="299ce-150">Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen.</span><span class="sxs-lookup"><span data-stu-id="299ce-150">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="299ce-151">Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="299ce-151">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="299ce-152">Unity-Beispielprojekte für OpenXR und HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="299ce-152">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="299ce-153">Sehen Sie sich das [Repository mit OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) Mixed Reality-Beispielen für Unity-Beispielprojekte an, in dem gezeigt wird, wie Sie Unity-Anwendungen für HoloLens 2- oder Mixed Reality-Headsets mithilfe des Mixed Reality OpenXR-Plug-Ins erstellen.</span><span class="sxs-lookup"><span data-stu-id="299ce-153">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="299ce-154">Verwenden von MRTK mit OpenXR-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="299ce-154">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="299ce-155">MRTK für Unity Version 2.7 unterstützt jetzt offiziell das Mixed Reality OpenXR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="299ce-155">MRTK for Unity version 2.7 now officially supports the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="299ce-156">Öffnen Sie [Mixed Reality Featuretool erneut,](welcome-to-mr-feature-tool.md) um das Mixed Reality Toolkit zu installieren, sofern noch nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="299ce-156">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="299ce-157">OpenXR-Unterstützung ist im **Foundation-Paket** enthalten.</span><span class="sxs-lookup"><span data-stu-id="299ce-157">OpenXR support is in the **Foundation** package.</span></span>

![Featuretool "Mixed Reality" – Fenster "Features entdecken" mit hervorgehobenen Standardressourcen](images/mrft-install-openxr.png)

> [!NOTE]
> <span data-ttu-id="299ce-159">Stellen Sie beim Upgrade von einer früheren Version von MRTK sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:</span><span class="sxs-lookup"><span data-stu-id="299ce-159">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="299ce-160">Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer begonnen haben.</span><span class="sxs-lookup"><span data-stu-id="299ce-160">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="299ce-161">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="299ce-161">Next steps</span></span>

<span data-ttu-id="299ce-162">Nachdem Sie Ihr Projekt für OpenXR konfiguriert haben und Zugriff [](openxr-supported-features.md) auf Beispiele haben, sehen Sie sich an, welche Features derzeit in unserem OpenXR-Plug-In unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="299ce-162">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="299ce-163">Haben Sie Feedback?</span><span class="sxs-lookup"><span data-stu-id="299ce-163">Have Feedback?</span></span>

<span data-ttu-id="299ce-164">OpenXR ist immer noch experimentell, daher freuen wir uns über jedes Feedback, das Sie uns geben können, um es besser zu machen.</span><span class="sxs-lookup"><span data-stu-id="299ce-164">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="299ce-165">Sie finden uns in den [Unity-Foren,](https://aka.ms/unityforums) indem Sie Ihren Forumbeitrag mit **Microsoft**  +  **OpenXR** markieren und **entweder** HoloLens 2 oder **Windows Mixed Reality.**</span><span class="sxs-lookup"><span data-stu-id="299ce-165">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="299ce-166">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="299ce-166">See also</span></span>

* [<span data-ttu-id="299ce-167">Konfigurieren von Projekten ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="299ce-167">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="299ce-168">Empfohlene Einstellungen für Unity</span><span class="sxs-lookup"><span data-stu-id="299ce-168">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="299ce-169">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="299ce-169">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
