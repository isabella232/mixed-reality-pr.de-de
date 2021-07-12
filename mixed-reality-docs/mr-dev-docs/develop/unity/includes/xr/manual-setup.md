---
ms.openlocfilehash: 639a96785e666cc3f5da3577ec3166f364753ed5
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603716"
---
# <a name="openxr"></a>[<span data-ttu-id="33b63-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="33b63-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="33b63-102">Installieren Sie das OpenXR-Plug-In mit der neuen Mixed Reality Feature Tool-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="33b63-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="33b63-103">Befolgen Sie [die Installations- und Nutzungsanweisungen,](../../welcome-to-mr-feature-tool.md) und wählen Sie **Mixed Reality OpenXR-Plug-In-Paket** in der **Kategorie Plattformunterstützung** aus:</span><span class="sxs-lookup"><span data-stu-id="33b63-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![Mixed Reality fenster feature tool packages with open xr plugin (Öffnen des XR-Plug-Ins hervorgehoben)](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="33b63-105">Festlegen des Buildziels</span><span class="sxs-lookup"><span data-stu-id="33b63-105">Setting your build target</span></span>

<span data-ttu-id="33b63-106">Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="33b63-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener eigenständiger Mac &-Plattform](../../images/wmr-config-img-3.png)

<span data-ttu-id="33b63-108">Wenn Sie auf HoloLens 2 möchten, müssen Sie zur Universellen Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="33b63-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="33b63-109">Wählen **Sie Datei > Build Einstellungen...**</span><span class="sxs-lookup"><span data-stu-id="33b63-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="33b63-110">Wählen **Sie Windows Plattform** in der Liste Plattform aus, und wählen Sie Plattform wechseln **aus.**</span><span class="sxs-lookup"><span data-stu-id="33b63-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="33b63-111">Legen Sie **Architecture** (Architektur) auf **ARM64** fest.</span><span class="sxs-lookup"><span data-stu-id="33b63-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="33b63-112">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="33b63-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="33b63-113">Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.</span><span class="sxs-lookup"><span data-stu-id="33b63-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="33b63-114">Festlegen **der Ziel-SDK-Version** **auf Neueste installiert**</span><span class="sxs-lookup"><span data-stu-id="33b63-114">Set **Target SDK Version** to **Latest installed**</span></span>

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener Windows Plattform](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="33b63-116">Konfigurieren der XR-Plug-In-Verwaltung für OpenXR</span><span class="sxs-lookup"><span data-stu-id="33b63-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="33b63-117">So legen Sie OpenXR als Runtime in Unity fest:</span><span class="sxs-lookup"><span data-stu-id="33b63-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="33b63-118">Navigieren Sie im Unity-Editor zu **Bearbeiten > Project Einstellungen**</span><span class="sxs-lookup"><span data-stu-id="33b63-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="33b63-119">Wählen Sie in Einstellungen Liste der Anwendungen **XR-Plug-In-Verwaltung** aus (sollte bereits installiert sein, wenn Sie das openXR Mixed Reality-Plug-In mit MRFT installiert haben).</span><span class="sxs-lookup"><span data-stu-id="33b63-119">In the list of Settings, select **XR Plugin Management** (should already be installed if you installed the Mixed Reality OpenXR plugin using MRFT)</span></span>
3. <span data-ttu-id="33b63-120">Aktivieren Sie das **Kontrollkästchen XR beim Start initialisieren.**</span><span class="sxs-lookup"><span data-stu-id="33b63-120">Check the **Initialize XR on Startup** box</span></span>
4. <span data-ttu-id="33b63-121">Wenn Sie Desktop VR als Ziel verwenden, bleiben Sie auf der Registerkarte Eigenständiger PC (Monitor) und aktivieren sie die Kontrollkästchen **OpenXR** **und Windows Mixed Reality Featuresatz.**</span><span class="sxs-lookup"><span data-stu-id="33b63-121">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
5. <span data-ttu-id="33b63-122">Wenn Sie HoloLens 2 auswählen, wechseln Sie zur Registerkarte Universelle Windows-Plattform (das Windows-Logo), und wählen Sie die Felder **OpenXR** und Microsoft HoloLens **Featuresatz** aus.</span><span class="sxs-lookup"><span data-stu-id="33b63-122">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![Screenshot des im Unity-Editor geöffneten Projekteinstellungspanels mit hervorgehobener XR-Plug-In-Verwaltung](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="33b63-124">Wenn neben Dem OpenXR-Plug-In ein gelbes **Warnsymbol** angezeigt wird, klicken Sie auf das Symbol, und wählen **Sie Alle korrigieren aus,** bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="33b63-124">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="33b63-125">Der Unity-Editor muss möglicherweise neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="33b63-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot des OpenXR-Projektüberprüfungsfensters](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="33b63-127">Optimization</span><span class="sxs-lookup"><span data-stu-id="33b63-127">Optimization</span></span>

<span data-ttu-id="33b63-128">Wenn Sie für die Entwicklung HoloLens 2,  wählen Sie das Menüelement Mixed Reality > Project > Empfohlene Projekteinstellungen für HoloLens 2 anwenden aus, um eine bessere App-Leistung zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="33b63-128">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![Screenshot des geöffneten Mixed Reality-Menüelements mit ausgewählter Option "OpenXR"](../../images/openxr-img-08.png)

<span data-ttu-id="33b63-130">Sie können nun mit der Entwicklung mit OpenXR in Unity beginnen.</span><span class="sxs-lookup"><span data-stu-id="33b63-130">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="33b63-131">Fahren Sie mit dem nächsten Abschnitt fort, um zu erfahren, wie Sie die OpenXR-Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="33b63-131">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="33b63-132">Unity-Beispielprojekte für OpenXR und HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="33b63-132">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="33b63-133">Sehen Sie sich das [OpenXR Mixed Reality-Beispielre](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) repo für Unity-Beispielprojekte an, in dem gezeigt wird, wie Sie Unity-Anwendungen für HoloLens 2- oder Mixed Reality-Headsets mithilfe des Mixed Reality OpenXR-Plug-Ins erstellen.</span><span class="sxs-lookup"><span data-stu-id="33b63-133">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="33b63-134">Wenn Sie selbst mit einem leeren Projekt beginnen möchten, fahren Sie mit dem Artikel Einrichten der [Kamera](../../camera-in-unity.md) fort.</span><span class="sxs-lookup"><span data-stu-id="33b63-134">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="33b63-135">Windows Xr</span><span class="sxs-lookup"><span data-stu-id="33b63-135">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="33b63-136">Das Windows XR-Plug-In ist in Unity 2021.1 veraltet und wird in Unity 2021.2 entfernt.</span><span class="sxs-lookup"><span data-stu-id="33b63-136">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="33b63-137">Für die Unity 2020-Entwicklung empfiehlt Microsoft stattdessen das OpenXR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="33b63-137">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="33b63-138">Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="33b63-138">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener eigenständiger Mac &-Plattform](../../images/wmr-config-img-3.png)

<span data-ttu-id="33b63-140">Wenn Sie auf HoloLens 2 möchten, müssen Sie zur Universellen Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="33b63-140">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="33b63-141">Wählen **Sie Datei > Build Einstellungen...**</span><span class="sxs-lookup"><span data-stu-id="33b63-141">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="33b63-142">Wählen **Sie Windows Plattform** in der Liste Plattform aus, und wählen Sie Plattform wechseln **aus.**</span><span class="sxs-lookup"><span data-stu-id="33b63-142">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="33b63-143">Legen Sie **Architecture** (Architektur) auf **ARM64** fest.</span><span class="sxs-lookup"><span data-stu-id="33b63-143">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="33b63-144">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="33b63-144">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="33b63-145">Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.</span><span class="sxs-lookup"><span data-stu-id="33b63-145">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="33b63-146">Festlegen **der Ziel-SDK-Version** **auf Neueste installiert**</span><span class="sxs-lookup"><span data-stu-id="33b63-146">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="33b63-147">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="33b63-147">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener Windows Plattform](../../images/wmr-config-img-4.png)

<span data-ttu-id="33b63-149">Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll:</span><span class="sxs-lookup"><span data-stu-id="33b63-149">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="33b63-150">Navigieren Sie im Unity-Editor zu **Edit > Project settings (Einstellungen bearbeiten),** und wählen Sie **XR Plugin Management (XR-Plug-In-Verwaltung) aus.**</span><span class="sxs-lookup"><span data-stu-id="33b63-150">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="33b63-151">Wählen Sie **XR-Plug-In-Verwaltung installieren aus,** wenn es angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="33b63-151">Select **Install XR Plugin Management** if it appears</span></span>

![Screenshot: Project Einstellungen geöffneten Fensters im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="33b63-153">Wählen **Sie XR beim Start initialisieren und Windows Mixed Reality** </span><span class="sxs-lookup"><span data-stu-id="33b63-153">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot: Project Fenster "Einstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="33b63-155">Wählen Sie den **Abschnitt XR Plug-in Management Windows Mixed Reality** aus, aktivieren Sie alle Kontrollkästchen, und legen Sie Tiefenpufferformat auf  >   **Tiefenpuffer 16 Bit fest.** </span><span class="sxs-lookup"><span data-stu-id="33b63-155">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![Screenshot: Project Fenster "Einstellungen" im Unity-Editor mit hervorgehobener Windows Mixed Reality](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="33b63-157">Legacy-XR</span><span class="sxs-lookup"><span data-stu-id="33b63-157">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="33b63-158">Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.</span><span class="sxs-lookup"><span data-stu-id="33b63-158">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="33b63-159">Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="33b63-159">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener eigenständiger Mac &-Plattform](../../images/wmr-config-img-3.png)

<span data-ttu-id="33b63-161">Wenn Sie auf HoloLens 2 möchten, müssen Sie zur Universellen Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="33b63-161">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="33b63-162">Wählen **Sie Datei > Build Einstellungen...**</span><span class="sxs-lookup"><span data-stu-id="33b63-162">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="33b63-163">Wählen **Sie Windows Plattform** in der Liste Plattform aus, und wählen Sie Plattform wechseln **aus.**</span><span class="sxs-lookup"><span data-stu-id="33b63-163">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="33b63-164">Legen Sie **Architecture** (Architektur) auf **ARM64** fest.</span><span class="sxs-lookup"><span data-stu-id="33b63-164">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="33b63-165">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="33b63-165">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="33b63-166">Legen Sie **Build Type** (Buildtyp) auf **D3D Project** (D3D-Projekt) fest.</span><span class="sxs-lookup"><span data-stu-id="33b63-166">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="33b63-167">Festlegen **der Ziel-SDK-Version** **auf Neueste installiert**</span><span class="sxs-lookup"><span data-stu-id="33b63-167">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="33b63-168">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="33b63-168">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot: Fenster "Build Einstellungen" im Unity-Editor mit hervorgehobener Windows Plattform](../../images/wmr-config-img-4.png)

<span data-ttu-id="33b63-170">Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="33b63-170">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="33b63-171">Öffnen **Sie player Einstellungen...** im **Build Einstellungen... Und** erweitern Sie die **XR Einstellungen Gruppe.**</span><span class="sxs-lookup"><span data-stu-id="33b63-171">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="33b63-172">Wählen Sie **im Abschnitt XR Einstellungen** Virtual Reality Supported **(Virtual Reality** unterstützt) aus, um die Liste Virtual Reality-Geräte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="33b63-172">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="33b63-173">Legen **Sie tiefenformat auf** **16-Bit-Tiefe fest,** und aktivieren Sie **Tiefenpufferfreigabe aktivieren.**</span><span class="sxs-lookup"><span data-stu-id="33b63-173">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="33b63-174">Legen Sie **Stereo Rendering Mode** (Stereorenderingmodus) auf **Single Pass Instanced** (Einzeldurchlauf instanziiert) fest.</span><span class="sxs-lookup"><span data-stu-id="33b63-174">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="33b63-175">Wählen **Sie WSA Holographic Remoting Supported (WSA Holographic Remoting unterstützt)** aus, wenn Sie remoting im holografischen Wiedergabemodus verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="33b63-175">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![Screenshot: Project Fenster "Einstellungen" im Unity-Editor mit hervorgehobenen Abschnitt "Playereinstellungen"](../../images/wmr-config-img-9.png)
