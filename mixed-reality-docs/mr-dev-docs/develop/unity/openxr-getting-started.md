---
title: Verwenden des gemischten Reality openxr-Plug-Ins für Unity
description: Erfahren Sie, wie Sie das gemischte Open-Plug-in für Unity für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, Mixed Reality, mrtk, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, erlernen, Tutorial, Getting Started
ms.openlocfilehash: a4606eeb1fa6c8dc0858653a196c1e536ae473d4
ms.sourcegitcommit: e2228b9585302eeff1d853ddb54be8421a21c954
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102189122"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="b2bb8-104">Verwenden des gemischten Reality openxr-Plug-Ins für Unity</span><span class="sxs-lookup"><span data-stu-id="b2bb8-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="b2bb8-105">Ab Unity, Version 2020,2, ist das gemischte openxr-Plug-in-Paket von Microsoft mit dem Unity-Paket-Manager (UPM) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2bb8-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b2bb8-106">Prerequisites</span></span>

* <span data-ttu-id="b2bb8-107">Unity 2020,2 oder höher</span><span class="sxs-lookup"><span data-stu-id="b2bb8-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="b2bb8-108">Unity openxr-Plug-in 0.1.3 oder höher</span><span class="sxs-lookup"><span data-stu-id="b2bb8-108">Unity OpenXR plugin 0.1.3 or later</span></span>
* <span data-ttu-id="b2bb8-109">Visual Studio 2019 oder höher</span><span class="sxs-lookup"><span data-stu-id="b2bb8-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="b2bb8-110">Installieren der **UWP** -Platt Form Unterstützung in Unity für hololens 2-apps</span><span class="sxs-lookup"><span data-stu-id="b2bb8-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="b2bb8-111">Wenn Sie VR-Anwendungen auf einem Windows-PC entwickeln, ist das gemischte openxr-Plug-in für die gemischte Realität nicht unbedingt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="b2bb8-112">Sie sollten das Plug-in jedoch installieren, wenn Sie die Controller Zuordnung für HP-Reverb-G2-Controller anpassen oder apps entwickeln, die sowohl für hololens 2-als auch für VR-Headsets geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="b2bb8-113">Installieren von openxr mit dem Feature-Tool Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b2bb8-113">Installing OpenXR with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="b2bb8-114">Installieren Sie das openxr-Plug-in mit der neuen Anwendung Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="b2bb8-115">Befolgen Sie die [Installations-und Verwendungs Anweisungen](welcome-to-mr-feature-tool.md) , und wählen Sie das **gemischte openxr-Plug** -in in der Kategorie Mixed Reality-Toolkit aus:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Fenster "Mixed Reality Feature Tool Packages" mit hervorgehobenem Open XR](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="b2bb8-117">Konfigurieren der XR-Plug-in-Verwaltung für openxr</span><span class="sxs-lookup"><span data-stu-id="b2bb8-117">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="b2bb8-118">So legen Sie openxr als Lauf Zeit Modul in Unity fest:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-118">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="b2bb8-119">Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen** .</span><span class="sxs-lookup"><span data-stu-id="b2bb8-119">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="b2bb8-120">Wählen Sie in der Liste der Einstellungen die Option " **XR Plugin Management** "</span><span class="sxs-lookup"><span data-stu-id="b2bb8-120">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="b2bb8-121">Aktivieren Sie die Kontrollkästchen " **XR beim Start** " und " **openxr (Vorschau)** initialisieren"</span><span class="sxs-lookup"><span data-stu-id="b2bb8-121">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="b2bb8-122">Wenn Sie auf hololens 2 abzielen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform befinden, und wählen Sie " **Microsoft hololens Feature**</span><span class="sxs-lookup"><span data-stu-id="b2bb8-122">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-in-Verwaltung](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="b2bb8-124">Wenn ein rotes Warnsymbol neben **openxr-Plug-in (Vorschau)** angezeigt wird, klicken Sie auf das Symbol, und wählen Sie **alle korrigieren** , bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-124">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="b2bb8-125">Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot des Fensters "openxr Project Validation"](images/openxr-img-06.png)

<span data-ttu-id="b2bb8-127">Sie sind nun bereit, mit der Entwicklung mit openxr in Unity zu beginnen!</span><span class="sxs-lookup"><span data-stu-id="b2bb8-127">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="b2bb8-128">Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die openxr-Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-128">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="b2bb8-129">Optimization</span><span class="sxs-lookup"><span data-stu-id="b2bb8-129">Optimization</span></span>

<span data-ttu-id="b2bb8-130">Wenn Sie für hololens 2 entwickeln, navigieren Sie zu **gemischte Realität> openxr > die empfohlenen Projekteinstellungen für hololens 2 anwenden** , um eine bessere App-Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-130">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot des Menü Elements mit gemischter Realität geöffnet mit ausgewähltem openxr](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="b2bb8-132">Ausprobieren der Unity-Beispiel Szenen</span><span class="sxs-lookup"><span data-stu-id="b2bb8-132">Try out the Unity sample scenes</span></span>

<span data-ttu-id="b2bb8-133">Wenn Sie eines oder mehrere der Beispiele verwenden möchten, installieren Sie [arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) und höher über den **Paket-Manager**:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-133">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Screenshot: Öffnen des Unity-Paket-Managers im Unity-Editor mit hervorgehobener AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="b2bb8-135">Hololens 2-Beispiele</span><span class="sxs-lookup"><span data-stu-id="b2bb8-135">HoloLens 2 samples</span></span>

1. <span data-ttu-id="b2bb8-136">Navigieren Sie im Unity-Editor zu **Fenster > Paket-Manager** .</span><span class="sxs-lookup"><span data-stu-id="b2bb8-136">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="b2bb8-137">Wählen Sie in der Liste der Pakete **gemischte Realität openxr-Plug** -in aus.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-137">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="b2bb8-138">Suchen Sie das Beispiel in der Liste **Samples** , und wählen Sie **importieren** aus.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-138">Locate the sample in the **Samples** list and select **Import**</span></span>

![Screenshot: Öffnen des Unity-Paket-Managers im Unity-Editor mit aktiviertem aktiviertem openxr-Plug-in](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="b2bb8-140">Wenn ein Paket aktualisiert wird, bietet Unity die Option zum Aktualisieren importierter Beispiele.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-140">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="b2bb8-141">Durch das Aktualisieren eines importierten Beispiels werden alle Änderungen überschrieben, die an dem Beispiel und den zugehörigen Assets vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-141">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="b2bb8-142">Verwenden von mrtk mit openxr-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="b2bb8-142">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="b2bb8-143">MRTK-Unity unterstützt das Mixed Reality openxr-Plug-in, beginnend mit der 2.5.3-Version.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-143">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="b2bb8-144">Öffnen Sie das [Mixed Reality-Feature-Tool](welcome-to-mr-feature-tool.md) erneut, um das Mixed Reality Toolkit zu installieren, falls Sie dies noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-144">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="b2bb8-145">Openxr-Unterstützung ist im **Foundation** -Paket.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-145">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="b2bb8-146">Wechseln Sie zum Skript "mixedreality Toolkit-Komponente" im Inspektor, und wechseln Sie zum Profil " **defaultoperxrconfigurationprofile** ":</span><span class="sxs-lookup"><span data-stu-id="b2bb8-146">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Screenshot: Wechseln der mrtk-Konfiguration in der Mixed Reality Toolkit-Komponente im Inspektor](images/openxr-img-11.png)

    1. <span data-ttu-id="b2bb8-148">[Ausführliche Informationen zum Migrieren zu openxr finden Sie in](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)der Dokumentation zu mrtk.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-148">See the MRTK documentation for [more in-depth information on migrating to OpenXR](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="b2bb8-149">Wenn Sie von einer früheren Version von mrtk aktualisieren, stellen Sie sicher, dass sich die folgende Zeile in der Datei **Assets/mixedrealitytoolkit. generated/link.xml** befindet:</span><span class="sxs-lookup"><span data-stu-id="b2bb8-149">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="b2bb8-150">Diese Zeile wird standardmäßig hinzugefügt, wenn Sie mit mrtk 2.5.4 oder höher gestartet haben.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-150">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2bb8-151">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="b2bb8-151">Next steps</span></span>

<span data-ttu-id="b2bb8-152">Nachdem Sie Ihr Projekt für openxr konfiguriert haben und Zugriff auf Beispiele haben, sehen Sie sich an, welche [Features](openxr-supported-features.md) derzeit in unserem openxr-Plug-in unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-152">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="b2bb8-153">Haben Sie Feedback?</span><span class="sxs-lookup"><span data-stu-id="b2bb8-153">Have Feedback?</span></span>

<span data-ttu-id="b2bb8-154">Openxr ist noch immer experimentell. Wir freuen uns über jedes Feedback, das Sie uns zur Verbesserung der IT-Unterstützung bieten können.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-154">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="b2bb8-155">Sie finden uns in den [Unity-Foren](https://aka.ms/unityforums) , indem Sie Ihren Forumsbeitrag mit **Microsoft**  +  **openxr** und entweder **hololens 2** oder **Windows Mixed Reality** markieren.</span><span class="sxs-lookup"><span data-stu-id="b2bb8-155">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2bb8-156">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b2bb8-156">See also</span></span>

* [<span data-ttu-id="b2bb8-157">Konfigurieren von Projekten ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="b2bb8-157">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="b2bb8-158">Empfohlene Einstellungen für Unity</span><span class="sxs-lookup"><span data-stu-id="b2bb8-158">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="b2bb8-159">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="b2bb8-159">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
