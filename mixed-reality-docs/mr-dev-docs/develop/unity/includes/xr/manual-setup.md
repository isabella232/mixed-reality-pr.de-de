---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "112535698"
---
# <a name="openxr"></a>[<span data-ttu-id="baa22-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="baa22-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="baa22-102">Installieren Sie das OpenXR-Plug-In mit der neuen Anwendung Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="baa22-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="baa22-103">Befolgen Sie die [Installations- und Nutzungsanweisungen,](../../welcome-to-mr-feature-tool.md) und wählen Sie das **Mixed Reality OpenXR-Plug-In-Paket** in der Kategorie **Plattformunterstützung** aus:</span><span class="sxs-lookup"><span data-stu-id="baa22-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Mixed Reality Fenster "Featuretoolpakete" mit hervorgehobener Hervorhebung des geöffneten xr-Plug-Ins](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="baa22-105">Festlegen des Buildziels</span><span class="sxs-lookup"><span data-stu-id="baa22-105">Setting your build target</span></span>

<span data-ttu-id="baa22-106">Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="baa22-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](../../images/wmr-config-img-3.png)

<span data-ttu-id="baa22-108">Wenn Sie HoloLens 2 als Ziel haben, müssen Sie zum Universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="baa22-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="baa22-109">Wählen Sie **Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="baa22-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="baa22-110">Wählen Sie **Universelle Windows-Plattform** in der Liste Plattform und dann **Plattform wechseln** aus.</span><span class="sxs-lookup"><span data-stu-id="baa22-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="baa22-111">Legen Sie **Architecture** (Architektur) auf **ARM64** fest.</span><span class="sxs-lookup"><span data-stu-id="baa22-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="baa22-112">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="baa22-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="baa22-113">Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.</span><span class="sxs-lookup"><span data-stu-id="baa22-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="baa22-114">Festlegen der **Ziel-SDK-Version** auf **"Latest installed" (Neueste Installation)**</span><span class="sxs-lookup"><span data-stu-id="baa22-114">Set **Target SDK Version** to **Latest installed**</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="baa22-116">Konfigurieren der XR-Plug-In-Verwaltung für OpenXR</span><span class="sxs-lookup"><span data-stu-id="baa22-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="baa22-117">So legen Sie OpenXR als Runtime in Unity fest:</span><span class="sxs-lookup"><span data-stu-id="baa22-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="baa22-118">Navigieren Sie im Unity-Editor zu **> Projekteinstellungen bearbeiten.**</span><span class="sxs-lookup"><span data-stu-id="baa22-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="baa22-119">Wählen Sie in der Liste der Einstellungen die Option **XR-Plug-In-Verwaltung** aus.</span><span class="sxs-lookup"><span data-stu-id="baa22-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="baa22-120">Wählen Sie **XR-Plug-In-Verwaltung installieren** aus, wenn das ![ Fenster "Projekteinstellungen" im Unity-Editor geöffnet und die XR-Plug-In-Verwaltung hervorgehoben angezeigt wird.](../../images/wmr-config-img-5.png)</span><span class="sxs-lookup"><span data-stu-id="baa22-120">Select **Install XR Plugin Management** if it appears ![Screenshot of Project Settings window open in unity editor with XR Plugin management highlighted](../../images/wmr-config-img-5.png)</span></span>
4. <span data-ttu-id="baa22-121">Aktivieren Sie das Kontrollkästchen **XR beim Start initialisieren.**</span><span class="sxs-lookup"><span data-stu-id="baa22-121">Check the **Initialize XR on Startup** box</span></span>
5. <span data-ttu-id="baa22-122">Wenn Sie desktop-VR als Ziel verwenden, bleiben Sie auf der Registerkarte PC Standalone (Monitor) und aktivieren Sie die Kontrollkästchen **OpenXR** und **Windows Mixed Reality Featuresatz.**</span><span class="sxs-lookup"><span data-stu-id="baa22-122">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
6. <span data-ttu-id="baa22-123">Wenn HoloLens 2 als Ziel festgelegt ist, wechseln Sie zur Registerkarte Universelle Windows-Plattform (Windows-Logo), und wählen Sie die Felder **OpenXR** und **Microsoft HoloLens Featuresatz** aus.</span><span class="sxs-lookup"><span data-stu-id="baa22-123">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Screenshot des im Unity-Editor geöffneten Bereichs "Projekteinstellungen" mit hervorgehobener XR-Plug-In-Verwaltung](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="baa22-125">Wenn neben **OpenXR-Plug-In** ein gelbes Warnsymbol angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alle korrigieren** aus, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="baa22-125">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="baa22-126">Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="baa22-126">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot des Fensters "OpenXR-Projektvalidierung"](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="baa22-128">Optimization</span><span class="sxs-lookup"><span data-stu-id="baa22-128">Optimization</span></span>

<span data-ttu-id="baa22-129">Wenn Sie für HoloLens 2 entwickeln, wählen Sie das **Mixed Reality > Projekt > Empfohlene Projekteinstellungen für HoloLens 2** Menüelement anwenden aus, um eine bessere App-Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="baa22-129">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Screenshot: Geöffnetes Mixed Reality-Menüelement mit ausgewählter Option "OpenXR"](../../images/openxr-img-08.png)

<span data-ttu-id="baa22-131">Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen!</span><span class="sxs-lookup"><span data-stu-id="baa22-131">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="baa22-132">Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="baa22-132">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="baa22-133">Unity-Beispielprojekte für OpenXR und HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="baa22-133">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="baa22-134">Sehen Sie sich das Repository mit [OpenXR-Mixed Reality-Beispielen](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) für Unity-Beispielprojekte an, in dem veranschaulicht wird, wie Unity-Anwendungen für HoloLens 2 oder Mixed Reality Headsets mithilfe des Mixed Reality OpenXR-Plug-Ins erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="baa22-134">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="baa22-135">Wenn Sie bereit sind, selbst mit einem leeren Projekt zu beginnen, fahren Sie mit dem Artikel [Kameraeinrichtung](../../camera-in-unity.md) fort.</span><span class="sxs-lookup"><span data-stu-id="baa22-135">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="baa22-136">Windows XR</span><span class="sxs-lookup"><span data-stu-id="baa22-136">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="baa22-137">Das Windows XR-Plug-In ist in Unity 2021.1 veraltet und wird in Unity 2021.2 entfernt.</span><span class="sxs-lookup"><span data-stu-id="baa22-137">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="baa22-138">Für die Unity 2020-Entwicklung empfiehlt Microsoft stattdessen das OpenXR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="baa22-138">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="baa22-139">Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="baa22-139">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](../../images/wmr-config-img-3.png)

<span data-ttu-id="baa22-141">Wenn Sie HoloLens 2 als Ziel haben, müssen Sie zum Universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="baa22-141">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="baa22-142">Wählen Sie **Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="baa22-142">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="baa22-143">Wählen Sie **Universelle Windows-Plattform** in der Liste Plattform und dann **Plattform wechseln** aus.</span><span class="sxs-lookup"><span data-stu-id="baa22-143">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="baa22-144">Legen Sie **Architecture** (Architektur) auf **ARM64** fest.</span><span class="sxs-lookup"><span data-stu-id="baa22-144">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="baa22-145">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="baa22-145">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="baa22-146">Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.</span><span class="sxs-lookup"><span data-stu-id="baa22-146">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="baa22-147">Festlegen der **Ziel-SDK-Version** auf **"Latest installed" (Neueste Installation)**</span><span class="sxs-lookup"><span data-stu-id="baa22-147">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="baa22-148">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="baa22-148">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](../../images/wmr-config-img-4.png)

<span data-ttu-id="baa22-150">Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll:</span><span class="sxs-lookup"><span data-stu-id="baa22-150">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="baa22-151">Navigieren Sie im Unity-Editor zu **> Projekteinstellungen bearbeiten,** und wählen Sie **XR-Plug-In-Verwaltung** aus.</span><span class="sxs-lookup"><span data-stu-id="baa22-151">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="baa22-152">Wählen Sie **XR-Plug-In-Verwaltung installieren** aus, wenn es angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="baa22-152">Select **Install XR Plugin Management** if it appears</span></span>

![Screenshot: Geöffnetes Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="baa22-154">Wählen Sie **XR beim Start initialisieren** und **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="baa22-154">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot: Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="baa22-156">Wählen Sie den Abschnitt **XR-Plug-In-Verwaltung**  >  **Windows Mixed Reality** aus, aktivieren Sie alle Kontrollkästchen, und legen Sie **Tiefenpufferformat** auf **Tiefenpuffer 16 Bit** fest.</span><span class="sxs-lookup"><span data-stu-id="baa22-156">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener Windows Mixed Reality Abschnitt](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="baa22-158">Legacy-XR</span><span class="sxs-lookup"><span data-stu-id="baa22-158">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="baa22-159">Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.</span><span class="sxs-lookup"><span data-stu-id="baa22-159">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="baa22-160">Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="baa22-160">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](../../images/wmr-config-img-3.png)

<span data-ttu-id="baa22-162">Wenn Sie HoloLens 2 als Ziel haben, müssen Sie zum Universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="baa22-162">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="baa22-163">Wählen Sie **Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="baa22-163">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="baa22-164">Wählen Sie **Universelle Windows-Plattform** in der Liste Plattform und dann **Plattform wechseln** aus.</span><span class="sxs-lookup"><span data-stu-id="baa22-164">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="baa22-165">Legen Sie **Architecture** (Architektur) auf **ARM64** fest.</span><span class="sxs-lookup"><span data-stu-id="baa22-165">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="baa22-166">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="baa22-166">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="baa22-167">Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.</span><span class="sxs-lookup"><span data-stu-id="baa22-167">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="baa22-168">Festlegen der **Ziel-SDK-Version** auf **"Latest installed" (Neueste Installation)**</span><span class="sxs-lookup"><span data-stu-id="baa22-168">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="baa22-169">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="baa22-169">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](../../images/wmr-config-img-4.png)

<span data-ttu-id="baa22-171">Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="baa22-171">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="baa22-172">Öffnen **Sie Playereinstellungen...** aus den **Buildeinstellungen... Fenster** und Erweitern der Gruppe **"XR-Einstellungen"**</span><span class="sxs-lookup"><span data-stu-id="baa22-172">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="baa22-173">Wählen Sie im Abschnitt **XR-Einstellungen** die Option **Virtual Reality Unterstützt** aus, um die Liste Virtual Reality-Geräte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="baa22-173">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="baa22-174">Legen Sie **das Tiefenformat** auf **16-Bit-Tiefe** fest, und aktivieren **Sie Die Tiefenpufferfreigabe aktivieren.**</span><span class="sxs-lookup"><span data-stu-id="baa22-174">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="baa22-175">Legen Sie **Stereo Rendering Mode** (Stereorenderingmodus) auf **Single Pass Instanced** (Einzeldurchlauf instanziiert) fest.</span><span class="sxs-lookup"><span data-stu-id="baa22-175">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="baa22-176">Wählen Sie **WSA Holographic Remoting Supported (WSA Holographic Remoting unterstützt)** aus, wenn Sie Remoting im holografischen Wiedergabemodus verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="baa22-176">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![Screenshot: Geöffnetes Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobenen Player-Einstellungen](../../images/wmr-config-img-9.png)
