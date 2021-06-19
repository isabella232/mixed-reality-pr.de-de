---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394584"
---
# <a name="openxr"></a>[<span data-ttu-id="f7e97-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f7e97-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="f7e97-102">Installieren Sie das OpenXR-Plug-In mit der neuen Mixed Reality Feature Tool-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="f7e97-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="f7e97-103">Befolgen Sie [die Installations- und Verwendungsanweisungen,](../../welcome-to-mr-feature-tool.md) und wählen Sie **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie Mixed Reality Toolkit aus:</span><span class="sxs-lookup"><span data-stu-id="f7e97-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Mixed Reality fenster feature tool packages with open xr plugin (Öffnen des XR-Plug-Ins hervorgehoben)](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="f7e97-105">Festlegen des Buildziels</span><span class="sxs-lookup"><span data-stu-id="f7e97-105">Setting your build target</span></span>

<span data-ttu-id="f7e97-106">Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="f7e97-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](../../images/wmr-config-img-3.png)

<span data-ttu-id="f7e97-108">Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:</span><span class="sxs-lookup"><span data-stu-id="f7e97-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="f7e97-109">Wählen **Sie Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="f7e97-110">Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="f7e97-111">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-111">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="f7e97-112">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="f7e97-113">Legen Sie **Buildtyp** auf **D3D** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="f7e97-114">Legen Sie **UWP SDK** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-114">Set **UWP SDK** to **Latest installed**</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="f7e97-116">Konfigurieren der XR-Plug-In-Verwaltung für OpenXR</span><span class="sxs-lookup"><span data-stu-id="f7e97-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="f7e97-117">So legen Sie OpenXR als Runtime in Unity fest:</span><span class="sxs-lookup"><span data-stu-id="f7e97-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="f7e97-118">Navigieren Sie im Unity-Editor zu **Bearbeiten > Projekteinstellungen.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="f7e97-119">Wählen Sie in der Liste der Einstellungen **XR-Plug-In-Verwaltung aus.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="f7e97-120">Aktivieren Sie die **Kontrollkästchen XR beim Start initialisieren** und **OpenXR.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-120">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="f7e97-121">Wenn Sie HoloLens 2 auswählen, stellen Sie sicher, dass Sie sich auf der UWP-Plattform sind, und wählen **Sie Microsoft HoloLens Feature Set (Featuresatz) aus.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-121">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot des im Unity-Editor geöffneten Projekteinstellungspanels mit hervorgehobener XR-Plug-In-Verwaltung](../../images/openxr-img-05.png)

### <a name="optimization"></a><span data-ttu-id="f7e97-123">Optimization</span><span class="sxs-lookup"><span data-stu-id="f7e97-123">Optimization</span></span>

<span data-ttu-id="f7e97-124">Wenn Sie für HoloLens 2 entwickeln, navigieren Sie zu Mixed Reality> **OpenXR >** Empfohlene Projekteinstellungen für HoloLens 2 anwenden, um eine bessere App-Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="f7e97-124">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot des geöffneten Mixed Reality-Menüelements mit ausgewählter Option "OpenXR"](../../images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="f7e97-126">Wenn neben Dem OpenXR-Plug-In ein gelbes **Warnsymbol** angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alles korrigieren aus,** bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="f7e97-126">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="f7e97-127">Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="f7e97-127">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot des OpenXR-Projektüberprüfungsfensters](../../images/openxr-img-06.png)

<span data-ttu-id="f7e97-129">Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen.</span><span class="sxs-lookup"><span data-stu-id="f7e97-129">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="f7e97-130">Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="f7e97-130">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="f7e97-131">Unity-Beispielprojekte für OpenXR und HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f7e97-131">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="f7e97-132">Sehen Sie sich das [Repository mit OpenXR](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) Mixed Reality-Beispielen für Unity-Beispielprojekte an, in dem gezeigt wird, wie Sie Unity-Anwendungen für HoloLens 2- oder Mixed Reality-Headsets mithilfe des Mixed Reality OpenXR-Plug-Ins erstellen.</span><span class="sxs-lookup"><span data-stu-id="f7e97-132">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="f7e97-133">Windows XR</span><span class="sxs-lookup"><span data-stu-id="f7e97-133">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="f7e97-134">Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="f7e97-134">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](../../images/wmr-config-img-3.png)

<span data-ttu-id="f7e97-136">Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:</span><span class="sxs-lookup"><span data-stu-id="f7e97-136">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="f7e97-137">Wählen **Sie Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-137">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="f7e97-138">Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-138">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="f7e97-139">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-139">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="f7e97-140">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-140">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="f7e97-141">Legen Sie **Buildtyp** auf **D3D** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-141">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="f7e97-142">Legen Sie **UWP SDK** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-142">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="f7e97-143">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="f7e97-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](../../images/wmr-config-img-4.png)

<span data-ttu-id="f7e97-145">Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll:</span><span class="sxs-lookup"><span data-stu-id="f7e97-145">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="f7e97-146">Navigieren Sie im Unity-Editor zu Bearbeiten > **Projekteinstellungen,** und wählen Sie **XR-Plug-In-Verwaltung aus.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-146">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="f7e97-147">Wählen Sie **XR-Plug-In-Verwaltung installieren aus.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-147">Select **Install XR Plugin Management**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="f7e97-149">Wählen **Sie XR beim Start initialisieren und Windows Mixed Reality** </span><span class="sxs-lookup"><span data-stu-id="f7e97-149">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="f7e97-151">Erweitern Sie den **Abschnitt XR-Plug-In-Verwaltung,** und wählen Sie die Registerkarte **"Einstellungen für die Windows-Plattform"** aus.</span><span class="sxs-lookup"><span data-stu-id="f7e97-151">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="f7e97-152">Wenn Sie Unity 2020 oder höher verwenden, sehen Sie die Optionen zum Überprüfen von **OpenXR** **oder Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="f7e97-152">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="f7e97-153">Sie können eine der beiden Laufzeiten auswählen.</span><span class="sxs-lookup"><span data-stu-id="f7e97-153">You can choose either runtime.</span></span>  <span data-ttu-id="f7e97-154">Wenn Sie speziell für die HoloLens 2 oder HP Reverb G2 entwickeln und sich entschließen, **OpenXR** auszuprobieren, wählen Sie das Feld OpenXR aus, und sehen Sie sich unseren Leitfaden unter Verwenden des Mixed Reality OpenXR-Plug-Ins für [Unity](../../openxr-getting-started.md) an, um sich für diese Geräte richtig einrichten zu lassen, bevor Sie zu diesem Tutorial zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="f7e97-154">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](../../openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="f7e97-155">Ab Unity 2020 LTS geht Microsoft von der Entwicklung mit OpenXR aus.</span><span class="sxs-lookup"><span data-stu-id="f7e97-155">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="f7e97-156">Bei der Migration zu diesem Pfad wird in Unity 2021.1 das Windows XR-Plug-In veraltet sein und in 2021.2 entfernt, wodurch OpenXR der einzige unterstützte Pfad ist.</span><span class="sxs-lookup"><span data-stu-id="f7e97-156">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="f7e97-157">Weitere Informationen finden Sie unter [Verwenden des Mixed Reality OpenXR-Plug-Ins.](../../openxr-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="f7e97-157">You can find more information in [Using the Mixed Reality OpenXR plugin](../../openxr-getting-started.md).</span></span>

6. <span data-ttu-id="f7e97-158">Wenn Sie sich für das **Windows Mixed Reality-Plug-In** entscheiden, aktivieren Sie alle Kontrollkästchen, und legen Sie **Tiefenübermittlungsmodus** auf Tiefe **16 Bit fest.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-158">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener Windows Mixed Reality Abschnitt](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="f7e97-160">Legacy-XR</span><span class="sxs-lookup"><span data-stu-id="f7e97-160">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="f7e97-161">Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="f7e97-161">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](../../images/wmr-config-img-3.png)

<span data-ttu-id="f7e97-163">Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:</span><span class="sxs-lookup"><span data-stu-id="f7e97-163">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="f7e97-164">Wählen **Sie Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-164">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="f7e97-165">Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-165">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="f7e97-166">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-166">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="f7e97-167">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-167">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="f7e97-168">Legen Sie **Buildtyp** auf **D3D** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-168">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="f7e97-169">Legen Sie **UWP SDK** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="f7e97-169">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="f7e97-170">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="f7e97-170">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](../../images/wmr-config-img-4.png)

<span data-ttu-id="f7e97-172">Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="f7e97-172">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="f7e97-173">Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.</span><span class="sxs-lookup"><span data-stu-id="f7e97-173">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="f7e97-174">Öffnen **Sie Playereinstellungen...** aus **den Buildeinstellungen... Und** erweitern Sie die **Gruppe XR-Einstellungen.**</span><span class="sxs-lookup"><span data-stu-id="f7e97-174">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="f7e97-175">Wählen Sie **im Abschnitt XR-Einstellungen** die Option **Virtual Reality Unterstützt aus,** um die Liste Virtual Reality-Geräte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f7e97-175">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="f7e97-176">Festlegen **des Tiefenformats** auf **16-Bit-Tiefe und** Aktivieren der **Tiefenpufferfreigabe**</span><span class="sxs-lookup"><span data-stu-id="f7e97-176">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="f7e97-177">Festlegen des **Stereo-Renderingmodus** auf **eine Einzelpassinstanz**</span><span class="sxs-lookup"><span data-stu-id="f7e97-177">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="f7e97-178">Wählen **Sie WSA Holographic Remoting Supported (WSA Holographic Remoting Unterstützt)** aus, wenn Sie Holographic Remoting verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="f7e97-178">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener Seite "Playereinstellungen"](../../images/wmr-config-img-9.png)