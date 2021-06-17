---
title: Verwenden des Mixed Reality OpenXR-Plug-Ins
description: Erfahren Sie, wie Sie das Mixed Reality OpenXR-Plug-In für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, Lernen, Tutorial, Erste Schritte
ms.openlocfilehash: ffec0cbe2ea9fd87cbb5f38010dad2d64e2e82ee
ms.sourcegitcommit: adbe3baa6b1c284ed1c4fd796d8b5612c3ca3f42
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2021
ms.locfileid: "112270435"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="97646-104">Verwenden des Mixed Reality OpenXR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="97646-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="97646-105">Für Entwickler, die Unity 2020 zum Erstellen von HoloLens 2- oder Mixed Reality-Anwendungen verwenden, kann das OpenXR-Plug-In anstelle des WindowsXR-Plug-Ins verwendet werden, um plattformübergreifende Kompatibilität zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="97646-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="97646-106">Das Mixed Reality OpenXR-Plug-In funktioniert auch gut mit dem neuesten [Mixed Reality-Featuretool.](welcome-to-mr-feature-tool.md)</span><span class="sxs-lookup"><span data-stu-id="97646-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="97646-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="97646-107">Prerequisites</span></span>

* <span data-ttu-id="97646-108">Neueste Unity 2020.3 LTS, empfohlen 2020.3.6f1 oder höher.</span><span class="sxs-lookup"><span data-stu-id="97646-108">Latest Unity 2020.3 LTS, recommend 2020.3.6f1 or above.</span></span>
* <span data-ttu-id="97646-109">Neuestes Unity OpenXR-Plug-In, empfohlen 1.2 oder höher</span><span class="sxs-lookup"><span data-stu-id="97646-109">Latest Unity OpenXR plugin, recommend 1.2 or later</span></span>
* <span data-ttu-id="97646-110">Neueste [Tools für HoloLens 2 Entwicklung](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="97646-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="97646-111">Neuestes MRTK (optional), empfehlungsversion 2.6 oder höher</span><span class="sxs-lookup"><span data-stu-id="97646-111">Latest MRTK (optional), recommend version 2.6 or later</span></span>
* <span data-ttu-id="97646-112">Neueste Mixed Reality OpenXR-Plug-In, Version 0.9.5 oder höher empfohlen</span><span class="sxs-lookup"><span data-stu-id="97646-112">Latest Mixed Reality OpenXR Plugin, recommend version 0.9.5 or later</span></span>

> [!NOTE]
> <span data-ttu-id="97646-113">Wenn Sie VR-Anwendungen auf einem Windows-PC erstellen, ist Mixed Reality OpenXR-Plug-In nicht unbedingt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="97646-113">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="97646-114">Sie sollten das Plug-In jedoch installieren, wenn Sie die Controllerzuordnung für HP Reverb G2-Controller anpassen oder Apps erstellen, die sowohl auf HoloLens 2- als auch auf VR-Headsets funktionieren.</span><span class="sxs-lookup"><span data-stu-id="97646-114">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="97646-115">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="97646-115">Setting up your project with MRTK</span></span>

<span data-ttu-id="97646-116">MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="97646-116">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="97646-117">MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="97646-117">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="97646-118">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.</span><span class="sxs-lookup"><span data-stu-id="97646-118">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="97646-119">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="97646-119">Set up your project using MRTK</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="97646-120">Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="97646-120">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="97646-121">Manuelle Einrichtung ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="97646-121">Manual setup without MRTK</span></span>

<span data-ttu-id="97646-122">Installieren Sie das OpenXR-Plug-In mit der neuen Mixed Reality Feature Tool-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="97646-122">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="97646-123">Befolgen Sie [die Installations- und Verwendungsanweisungen,](welcome-to-mr-feature-tool.md) und wählen Sie **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie Mixed Reality Toolkit aus:</span><span class="sxs-lookup"><span data-stu-id="97646-123">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Mixed Reality fenster feature tool packages with open xr plugin (Öffnen des XR-Plug-Ins hervorgehoben)](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="97646-125">Festlegen des Buildziels</span><span class="sxs-lookup"><span data-stu-id="97646-125">Setting your build target</span></span>

<span data-ttu-id="97646-126">Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="97646-126">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](images/wmr-config-img-3.png)

<span data-ttu-id="97646-128">Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:</span><span class="sxs-lookup"><span data-stu-id="97646-128">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="97646-129">Wählen **Sie Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="97646-129">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="97646-130">Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**</span><span class="sxs-lookup"><span data-stu-id="97646-130">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="97646-131">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="97646-131">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="97646-132">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="97646-132">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="97646-133">Legen Sie **Buildtyp** auf **D3D** fest</span><span class="sxs-lookup"><span data-stu-id="97646-133">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="97646-134">Legen Sie **UWP SDK** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="97646-134">Set **UWP SDK** to **Latest installed**</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="97646-136">Konfigurieren der XR-Plug-In-Verwaltung für OpenXR</span><span class="sxs-lookup"><span data-stu-id="97646-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="97646-137">So legen Sie OpenXR als Runtime in Unity fest:</span><span class="sxs-lookup"><span data-stu-id="97646-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="97646-138">Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="97646-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="97646-139">Wählen Sie in der Liste der Einstellungen **XR-Plug-In-Verwaltung aus.**</span><span class="sxs-lookup"><span data-stu-id="97646-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="97646-140">Aktivieren Sie die **Kontrollkästchen XR beim Start initialisieren** und **OpenXR.**</span><span class="sxs-lookup"><span data-stu-id="97646-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="97646-141">Wenn Sie HoloLens 2 auswählen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform sind, und wählen **Sie Microsoft HoloLens Feature Set (Featuresatz) aus.**</span><span class="sxs-lookup"><span data-stu-id="97646-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot des im Unity-Editor geöffneten Projekteinstellungspanels mit hervorgehobener XR-Plug-In-Verwaltung](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="97646-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="97646-143">Optimization</span></span>

<span data-ttu-id="97646-144">Wenn Sie für HoloLens 2 entwickeln, navigieren Sie zu Mixed Reality> **OpenXR >** Empfohlene Projekteinstellungen für HoloLens 2 anwenden, um eine bessere App-Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="97646-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot des geöffneten Mixed Reality-Menüelements mit ausgewählter Option "OpenXR"](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="97646-146">Wenn neben Dem OpenXR-Plug-In ein rotes **Warnsymbol** angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alles korrigieren aus,** bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="97646-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="97646-147">Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="97646-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot des OpenXR-Projektüberprüfungsfensters](images/openxr-img-06.png)

<span data-ttu-id="97646-149">Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen.</span><span class="sxs-lookup"><span data-stu-id="97646-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="97646-150">Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="97646-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="97646-151">Unity-Beispielprojekte für OpenXR und HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="97646-151">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="97646-152">Sehen Sie sich das [Repository mit OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) Mixed Reality-Beispielen für Unity-Beispielprojekte an, in dem gezeigt wird, wie Sie Unity-Anwendungen für HoloLens 2- oder Mixed Reality-Headsets mithilfe des Mixed Reality OpenXR-Plug-Ins erstellen.</span><span class="sxs-lookup"><span data-stu-id="97646-152">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="97646-153">Verwenden von MRTK mit OpenXR-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="97646-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="97646-154">MRTK-Unity unterstützt das Mixed Reality OpenXR-Plug-In ab Version 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="97646-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="97646-155">Öffnen Sie [Mixed Reality Featuretool erneut,](welcome-to-mr-feature-tool.md) um das Mixed Reality Toolkit zu installieren, sofern noch nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="97646-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="97646-156">OpenXR-Unterstützung ist im **Foundation-Paket** enthalten.</span><span class="sxs-lookup"><span data-stu-id="97646-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="97646-157">Wechseln Sie im Inspector zum MixedReality Toolkit-Komponentenskript, und wechseln Sie zum **Profil DefaultOpenXRConfigurationProfile:**</span><span class="sxs-lookup"><span data-stu-id="97646-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Screenshot: Wechseln der MRTK-Konfiguration in der Mixed Reality Toolkit-Komponente im Inspektor](images/openxr-img-11.png)

    1. <span data-ttu-id="97646-159">Weitere ausführliche Informationen zur Migration zu OpenXR finden Sie in der [MRTK-Dokumentation.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)</span><span class="sxs-lookup"><span data-stu-id="97646-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="97646-160">Stellen Sie beim Upgrade von einer früheren Version von MRTK sicher, dass sich die folgende Zeile in der Datei **Assets/MixedRealityToolkit.Generated/link.xml** befindet:</span><span class="sxs-lookup"><span data-stu-id="97646-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="97646-161">Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit MRTK 2.5.4 oder neuer begonnen haben.</span><span class="sxs-lookup"><span data-stu-id="97646-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="97646-162">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="97646-162">Next steps</span></span>

<span data-ttu-id="97646-163">Nachdem Sie Ihr Projekt für OpenXR konfiguriert haben und Zugriff [](openxr-supported-features.md) auf Beispiele haben, sehen Sie sich an, welche Features derzeit in unserem OpenXR-Plug-In unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="97646-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="97646-164">Haben Sie Feedback?</span><span class="sxs-lookup"><span data-stu-id="97646-164">Have Feedback?</span></span>

<span data-ttu-id="97646-165">OpenXR ist immer noch experimentell, daher freuen wir uns über jedes Feedback, das Sie uns geben können, um es besser zu machen.</span><span class="sxs-lookup"><span data-stu-id="97646-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="97646-166">Sie finden uns in den [Unity-Foren,](https://aka.ms/unityforums) indem Sie Ihren Forumbeitrag mit **Microsoft**  +  **OpenXR** markieren und **entweder** HoloLens 2 oder **Windows Mixed Reality.**</span><span class="sxs-lookup"><span data-stu-id="97646-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="97646-167">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="97646-167">See also</span></span>

* [<span data-ttu-id="97646-168">Konfigurieren von Projekten ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="97646-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="97646-169">Empfohlene Einstellungen für Unity</span><span class="sxs-lookup"><span data-stu-id="97646-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="97646-170">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="97646-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)