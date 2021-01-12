---
title: Verwenden des gemischten Reality openxr-Plug-Ins für Unity
description: Erfahren Sie, wie Sie das gemischte Open-Plug-in für Unity für Unity-Projekte aktivieren.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, Mixed Reality, mrtk, Mixed Reality Toolkit, Augmented Reality, Virtual Reality, Mixed Reality-Headsets, erlernen, Tutorial, Getting Started
ms.openlocfilehash: c5d312161b7d0f4f832e8d09dbacf5af700ffd8d
ms.sourcegitcommit: aa29b68603721e909f08f352feed24c65d2e505e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "98108881"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="50cc6-104">Verwenden des gemischten Reality openxr-Plug-Ins für Unity</span><span class="sxs-lookup"><span data-stu-id="50cc6-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="50cc6-105">Ab Unity, Version 2020,2, ist das gemischte openxr-Plug-in-Paket von Microsoft mit dem Unity-Paket-Manager (UPM) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="50cc6-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="50cc6-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="50cc6-106">Prerequisites</span></span>

* <span data-ttu-id="50cc6-107">Unity 2020,2 oder höher</span><span class="sxs-lookup"><span data-stu-id="50cc6-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="50cc6-108">Unity openxr-Plug-in 0.1.2 oder höher</span><span class="sxs-lookup"><span data-stu-id="50cc6-108">Unity OpenXR plugin 0.1.2 or later</span></span>
* <span data-ttu-id="50cc6-109">Visual Studio 2019 oder höher</span><span class="sxs-lookup"><span data-stu-id="50cc6-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="50cc6-110">Installieren der **UWP** -Platt Form Unterstützung in Unity für hololens 2-apps</span><span class="sxs-lookup"><span data-stu-id="50cc6-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="50cc6-111">Wenn Sie VR-Anwendungen auf einem Windows-PC entwickeln, ist das gemischte openxr-Plug-in für die gemischte Realität nicht unbedingt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="50cc6-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="50cc6-112">Sie sollten das Plug-in jedoch installieren, wenn Sie die Controller Zuordnung für HP-Reverb-G2-Controller anpassen oder apps entwickeln, die sowohl für hololens 2-als auch für VR-Headsets geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="50cc6-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="50cc6-113">Installieren des Mixed Reality openxr-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="50cc6-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="50cc6-114">Das Projekt muss das **openxr** -Plug-in und das **Management** Pack für den</span><span class="sxs-lookup"><span data-stu-id="50cc6-114">Your project needs to install the **OpenXR Plugin** and **XR Plugin Management** packages before using the Mixed Reality OpenXR Plugin.</span></span> <span data-ttu-id="50cc6-115">Wenn Sie diese bereits installiert haben, ist es toll!</span><span class="sxs-lookup"><span data-stu-id="50cc6-115">If you've already installed them, great!</span></span> <span data-ttu-id="50cc6-116">Wenn dies nicht der Fall ist, werden Sie beim Installieren des Plug-Ins für gemischte Realität automatisch als Abhängigkeiten installiert:</span><span class="sxs-lookup"><span data-stu-id="50cc6-116">If not, installing the Mixed Reality OpenXR plugin will automatically install them as dependencies:</span></span>

1. <span data-ttu-id="50cc6-117">Navigieren Sie im Unity-Editor zum **Bearbeiten > Projekteinstellungen > Paket-Manager** .</span><span class="sxs-lookup"><span data-stu-id="50cc6-117">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="50cc6-118">Erweitern Sie den Bereich Bereichs bezogene **Registrierungen** , geben Sie die folgenden Informationen ein, und klicken Sie dann auf **Speichern**:</span><span class="sxs-lookup"><span data-stu-id="50cc6-118">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>
    * <span data-ttu-id="50cc6-119">Legen Sie **Name** auf **Microsoft Mixed Reality** fest.</span><span class="sxs-lookup"><span data-stu-id="50cc6-119">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="50cc6-120">**URL** festlegen auf **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="50cc6-120">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="50cc6-121">**Bereich (e)** auf **com. Microsoft. mixedreality** festlegen</span><span class="sxs-lookup"><span data-stu-id="50cc6-121">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="50cc6-122">Wählen Sie unter **Erweiterte Einstellungen** die Option **Vorschau Pakete aktivieren** aus.</span><span class="sxs-lookup"><span data-stu-id="50cc6-122">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![Screenshot des Fensters "Unity-Paket-Manager" in den Projekteinstellungen](images/openxr-img-01.png)

<span data-ttu-id="50cc6-124">Der Unity-Paket-Manager verwendet eine Manifestressource mit dem Namen *manifest.json* , um zu bestimmen, welche Pakete installiert werden müssen und welche Registrierungen Sie installieren können.</span><span class="sxs-lookup"><span data-stu-id="50cc6-124">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50cc6-125">Openxr ist in Unity immer noch experimentell, und dieser Prozess kann sich im Laufe der Zeit ändern, da wir arbeiten, um die Entwickler Oberfläche zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="50cc6-125">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="50cc6-126">Registrieren der Mixed Reality-Abhängigkeit</span><span class="sxs-lookup"><span data-stu-id="50cc6-126">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="50cc6-127">Nachdem die Microsoft Mixed Reality-Bereichs bezogene Registrierung dem Manifest hinzugefügt wurde, kann das openxr-Paket angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="50cc6-127">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="50cc6-128">So fügen Sie das openxr-Paket hinzu:</span><span class="sxs-lookup"><span data-stu-id="50cc6-128">To add the OpenXR package:</span></span>

1. <span data-ttu-id="50cc6-129">Öffnen Sie **[projectroot]/Packages/manifest.js** in einem Text-Editor wie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="50cc6-129">Open **[projectRoot]/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
    1. <span data-ttu-id="50cc6-130">Klicken Sie dazu im linken Bereich des Projekt Fensters mit der rechten Maustaste auf **Pakete** .</span><span class="sxs-lookup"><span data-stu-id="50cc6-130">To get here, right click on **Packages** in the left panel of the Project window.</span></span> <span data-ttu-id="50cc6-131">Klicken Sie dann **auf in Explorer anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="50cc6-131">Then, click **Show in Explorer**.</span></span>
    <span data-ttu-id="50cc6-132">![Screenshot der Paket Auflistung im Projektfenster](images/packages.png)</span><span class="sxs-lookup"><span data-stu-id="50cc6-132">![Screenshot of the packages listing in the Project window](images/packages.png)</span></span>
1. <span data-ttu-id="50cc6-133">Ändern Sie den Abschnitt "Abhängigkeiten" der *Pakete/manifest.jsin* der Datei wie folgt:</span><span class="sxs-lookup"><span data-stu-id="50cc6-133">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="50cc6-134">In ihrer Manifest-Datei sind möglicherweise weitere Abhängigkeiten vorhanden, die hier nicht aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="50cc6-134">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="50cc6-135">Löschen Sie keines dieser Elemente, und fügen Sie der Liste einfach die openxr-Abhängigkeit hinzu.</span><span class="sxs-lookup"><span data-stu-id="50cc6-135">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.2",
      }
    ```

1. <span data-ttu-id="50cc6-136">Speichern Sie die Datei, wechseln Sie zurück zum Unity-Editor, und öffnen Sie den **Paket-Manager** , um die Installation des Plug-ins zu bestätigen:</span><span class="sxs-lookup"><span data-stu-id="50cc6-136">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span>

    ![Screenshot des Unity-Paket-Managers, geöffnet im Unity-Editor mit hervorgehobenem gemischtes openxr-Plug-in](images/openxr-img-03.png)

    > [!Note]
    > <span data-ttu-id="50cc6-138">Wenn das openxr-Paket mit dem Unity-Paket-Manager entfernt wird, müssen Sie es mithilfe der zuvor beschriebenen Schritte erneut hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="50cc6-138">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="50cc6-139">Konfigurieren der XR-Plug-in-Verwaltung für openxr</span><span class="sxs-lookup"><span data-stu-id="50cc6-139">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="50cc6-140">So legen Sie openxr als Lauf Zeit Modul in Unity fest:</span><span class="sxs-lookup"><span data-stu-id="50cc6-140">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="50cc6-141">Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen** .</span><span class="sxs-lookup"><span data-stu-id="50cc6-141">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="50cc6-142">Wählen Sie in der Liste der Einstellungen die Option " **XR Plugin Management** "</span><span class="sxs-lookup"><span data-stu-id="50cc6-142">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="50cc6-143">Aktivieren Sie die Kontrollkästchen " **XR beim Start** " und " **openxr (Vorschau)** initialisieren"</span><span class="sxs-lookup"><span data-stu-id="50cc6-143">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="50cc6-144">Wenn Sie auf hololens 2 abzielen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform befinden, und wählen Sie " **Microsoft hololens Feature**</span><span class="sxs-lookup"><span data-stu-id="50cc6-144">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot des Bereichs "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-in-Verwaltung](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="50cc6-146">Wenn ein rotes Warnsymbol neben **openxr-Plug-in (Vorschau)** angezeigt wird, klicken Sie auf das Symbol, und wählen Sie **alle korrigieren** , bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="50cc6-146">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="50cc6-147">Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="50cc6-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot des Fensters "openxr Project Validation"](images/openxr-img-06.png)

<span data-ttu-id="50cc6-149">Sie sind nun bereit, mit der Entwicklung mit openxr in Unity zu beginnen!</span><span class="sxs-lookup"><span data-stu-id="50cc6-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="50cc6-150">Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die openxr-Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="50cc6-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="50cc6-151">Optimization</span><span class="sxs-lookup"><span data-stu-id="50cc6-151">Optimization</span></span>

<span data-ttu-id="50cc6-152">Wenn Sie für hololens 2 entwickeln, navigieren Sie zu **gemischte Realität> openxr > die empfohlenen Projekteinstellungen für hololens 2 anwenden** , um eine bessere App-Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="50cc6-152">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot des Menü Elements mit gemischter Realität geöffnet mit ausgewähltem openxr](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="50cc6-154">Ausprobieren der Unity-Beispiel Szenen</span><span class="sxs-lookup"><span data-stu-id="50cc6-154">Try out the Unity sample scenes</span></span>

<span data-ttu-id="50cc6-155">Wenn Sie eines oder mehrere der Beispiele verwenden möchten, installieren Sie [arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) und höher über den **Paket-Manager**:</span><span class="sxs-lookup"><span data-stu-id="50cc6-155">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Screenshot: Öffnen des Unity-Paket-Managers im Unity-Editor mit hervorgehobener AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="50cc6-157">Hololens 2-Beispiele</span><span class="sxs-lookup"><span data-stu-id="50cc6-157">HoloLens 2 samples</span></span>

1. <span data-ttu-id="50cc6-158">Navigieren Sie im Unity-Editor zu **Fenster > Paket-Manager** .</span><span class="sxs-lookup"><span data-stu-id="50cc6-158">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="50cc6-159">Wählen Sie in der Liste der Pakete **gemischte Realität openxr-Plug** -in aus.</span><span class="sxs-lookup"><span data-stu-id="50cc6-159">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="50cc6-160">Suchen Sie das Beispiel in der Liste **Samples** , und wählen Sie **importieren** aus.</span><span class="sxs-lookup"><span data-stu-id="50cc6-160">Locate the sample in the **Samples** list and select **Import**</span></span>

![Screenshot: Öffnen des Unity-Paket-Managers im Unity-Editor mit aktiviertem aktiviertem openxr-Plug-in](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="50cc6-162">Wenn ein Paket aktualisiert wird, bietet Unity die Option zum Aktualisieren importierter Beispiele.</span><span class="sxs-lookup"><span data-stu-id="50cc6-162">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="50cc6-163">Durch das Aktualisieren eines importierten Beispiels werden alle Änderungen überschrieben, die an dem Beispiel und den zugehörigen Assets vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="50cc6-163">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="50cc6-164">Verwenden von mrtk mit openxr-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="50cc6-164">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="50cc6-165">Mrtk Unity unterstützt das Mixed Reality openxr-Plug-in, beginnend mit der 2.5.3-Version.</span><span class="sxs-lookup"><span data-stu-id="50cc6-165">MRTK Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>  <span data-ttu-id="50cc6-166">Mrtk-Plug-Ins können aus den gleichen Bereichs bezogenen Registrierungen installiert werden, die Sie bei [der Installation des Mixed Reality openxr-Plug](#installing-the-mixed-reality-openxr-plugin)-ins eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="50cc6-166">MRTK plugins can be installed from the same scoped registries as you set up when [installing the Mixed Reality OpenXR plugin](#installing-the-mixed-reality-openxr-plugin).</span></span> <span data-ttu-id="50cc6-167">Ausführlichere Informationen finden Sie in der [Dokumentation zu mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server).</span><span class="sxs-lookup"><span data-stu-id="50cc6-167">You can find more detailed information in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server).</span></span>

1. <span data-ttu-id="50cc6-168">Fügen Sie die folgenden Pakete in Ihrem **[projectroot]/Packages/-manifest.jsfür** die Datei hinzu:</span><span class="sxs-lookup"><span data-stu-id="50cc6-168">Add following packages in your **[projectRoot]/Packages/manifest.json** file:</span></span>

```json
"dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.3",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.3",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.3",
    …
}
```

2. <span data-ttu-id="50cc6-169">Wechseln Sie zum Skript "mixedreality Toolkit-Komponente" im Inspektor, und wechseln Sie zum Profil " **defaultoperxrconfigurationprofile** ":</span><span class="sxs-lookup"><span data-stu-id="50cc6-169">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

![Screenshot: Wechseln der mrtk-Konfiguration in der Mixed Reality Toolkit-Komponente im Inspektor](images/openxr-img-11.png)

### <a name="known-issues"></a><span data-ttu-id="50cc6-171">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="50cc6-171">Known issues</span></span> 

<span data-ttu-id="50cc6-172">Fügen Sie in der Datei **Assets/mixedrealitytoolkit. generated/link.xml** die folgende Zeile hinzu, wenn Sie das Hand Verfolgungs Feature verwenden:</span><span class="sxs-lookup"><span data-stu-id="50cc6-172">When using the Hand Tracking feature, add following line in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a><span data-ttu-id="50cc6-173">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="50cc6-173">Next steps</span></span>

<span data-ttu-id="50cc6-174">Nachdem Sie Ihr Projekt für openxr konfiguriert haben und Zugriff auf Beispiele haben, sehen Sie sich an, welche [Features](openxr-supported-features.md) derzeit in unserem openxr-Plug-in unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="50cc6-174">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="50cc6-175">Haben Sie Feedback?</span><span class="sxs-lookup"><span data-stu-id="50cc6-175">Have Feedback?</span></span>

<span data-ttu-id="50cc6-176">Openxr ist noch immer experimentell. Wir freuen uns über jedes Feedback, das Sie uns zur Verbesserung der IT-Unterstützung bieten können.</span><span class="sxs-lookup"><span data-stu-id="50cc6-176">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="50cc6-177">Sie finden uns in den [Unity-Foren](https://aka.ms/unityforums) , indem Sie Ihren Forumsbeitrag mit **Microsoft**  +  **openxr** und entweder **hololens 2** oder **Windows Mixed Reality** markieren.</span><span class="sxs-lookup"><span data-stu-id="50cc6-177">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="50cc6-178">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="50cc6-178">See also</span></span>

* [<span data-ttu-id="50cc6-179">Konfigurieren von Projekten ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="50cc6-179">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="50cc6-180">Empfohlene Einstellungen für Unity</span><span class="sxs-lookup"><span data-stu-id="50cc6-180">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="50cc6-181">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="50cc6-181">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
