---
title: Konfigurieren des Projekts ohne mrtk
description: Erfahren Sie, wie Sie ein neues Unity-Projekt für Windows Mixed Reality ohne das Mixed Reality Toolkit konfigurieren.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, gemischte Realität, Entwicklung, Einstieg, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung
ms.openlocfilehash: 6a9bc0d9a565de1d25e1906c439e39773cb99244
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496078"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="f2fa6-104">Konfigurieren von Projekten ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="f2fa6-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="f2fa6-105">Windows Mixed Reality (WMR) ist eine Microsoft-Plattform, die als Teil des Betriebssystems Windows 10 eingeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="f2fa6-106">Mit der WMR-Plattform können Sie Anwendungen erstellen, mit denen digitale Inhalte auf Holographic-und VR-Geräten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="f2fa6-107">Obwohl Microsoft und die Community Open Source-Tools wie das [Mixed Reality Toolkit (mrtk)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) erstellt haben, das die WMR-Umgebung automatisch einrichten wird, möchten viele Entwickler ihre Erfahrungen von Grund auf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="f2fa6-108">In der folgenden Dokumentation wird veranschaulicht, wie Sie ein Projekt für die Entwicklung mit gemischter Realität ordnungsgemäß einrichten, unabhängig davon, ob Sie mrtk verwenden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="f2fa6-109">Die Einstellungen, die Sie ändern müssen, werden in zwei Kategorien unterteilt: Einstellungen pro Projekt und Einstellungen pro Szene.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="f2fa6-110">Sie können mrtk später jederzeit importieren, sodass es für die manuelle Route keinen Nachteil gibt.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="f2fa6-111">Wenn Sie die manuelle Einrichtung von WMR auswählen, werden die Einstellungen, die Sie ändern müssen, in zwei Kategorien unterteilt: pro Projekt und pro Szene.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="f2fa6-112">Einstellungen pro Projekt</span><span class="sxs-lookup"><span data-stu-id="f2fa6-112">Per-project settings</span></span>

<span data-ttu-id="f2fa6-113">Wenn Sie auf Desktop VR abzielen, empfiehlt es sich, die eigenständige PC-Plattform zu verwenden, die für ein neues Unity-Projekt standardmäßig ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="f2fa6-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit PC, Mac & eigenständige Plattform hervorgehoben](images/wmr-config-img-3.png)

<span data-ttu-id="f2fa6-115">Wenn Sie hololens 2 als Ziel verwenden, müssen Sie zum universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="f2fa6-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="f2fa6-116">**Datei > Buildeinstellungen auswählen...**</span><span class="sxs-lookup"><span data-stu-id="f2fa6-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="f2fa6-117">Wählen Sie in der Platt Form Liste **universelle Windows-Plattform** aus, und wählen Sie **Plattform wechseln**</span><span class="sxs-lookup"><span data-stu-id="f2fa6-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="f2fa6-118">**Architektur** auf **Arm 64** festlegen</span><span class="sxs-lookup"><span data-stu-id="f2fa6-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="f2fa6-119">**Zielgerät** auf **hololens** festlegen</span><span class="sxs-lookup"><span data-stu-id="f2fa6-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="f2fa6-120">**Buildtyp** auf **D3D** festlegen</span><span class="sxs-lookup"><span data-stu-id="f2fa6-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="f2fa6-121">**UWP SDK** auf **Letztes installiert** festlegen</span><span class="sxs-lookup"><span data-stu-id="f2fa6-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="f2fa6-122">**Buildkonfiguration** auf **Release** festlegen, da beim Debuggen bekannte Leistungsprobleme auftreten</span><span class="sxs-lookup"><span data-stu-id="f2fa6-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor öffnen mit hervorgehobener universelle Windows-Plattform](images/wmr-config-img-4.png)

<span data-ttu-id="f2fa6-124">Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass Sie beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellen soll.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="f2fa6-125">Für xrsdk</span><span class="sxs-lookup"><span data-stu-id="f2fa6-125">For XRSDK</span></span> 

1. <span data-ttu-id="f2fa6-126">Navigieren Sie im Unity-Editor zu **Edit > Project Settings** , und wählen Sie die **Verwaltung von XR Plugin** aus.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="f2fa6-127">Select </span><span class="sxs-lookup"><span data-stu-id="f2fa6-127">Select **Install XR Plugin Management**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet, mit hervorgehobener Verwaltung von XR](images/wmr-config-img-5.png)

3. <span data-ttu-id="f2fa6-129">Wählen Sie " **XR beim Start** und **Windows Mixed Reality** initialisieren" aus.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet, mit hervorgehobener Verwaltung von XR](images/wmr-config-img-7.png)

4. <span data-ttu-id="f2fa6-131">Erweitern Sie den Abschnitt " **XR Plug-in-Verwaltung** ", und wählen Sie **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="f2fa6-131">Expand the **XR Plug-in Management** section and select **Windows Mixed Reality**</span></span>
5. <span data-ttu-id="f2fa6-132">Aktivieren Sie alle Felder, und legen Sie den tiefen Übermittlungs **Modus** auf **Tiefe 16 Bit** fest</span><span class="sxs-lookup"><span data-stu-id="f2fa6-132">Check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet mit hervorgehobenem Windows Mixed Reality-Abschnitt](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="f2fa6-134">Für Legacy-XR</span><span class="sxs-lookup"><span data-stu-id="f2fa6-134">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="f2fa6-135">Legacy XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-135">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="f2fa6-136">**Player Einstellungen** öffnen... aus den **Buildeinstellungen... Fenster** und erweitern Sie die Gruppe " **XR-Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="f2fa6-136">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="f2fa6-137">Wählen Sie im Abschnitt " **XR-Einstellungen** " die Option **virtuelle Realität unterstützt** aus, um die Liste Virtual Reality-Geräte</span><span class="sxs-lookup"><span data-stu-id="f2fa6-137">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="f2fa6-138">Festlegen des **tiefen Formats** auf eine **16-Bit-Tiefe** und Aktivieren der **tiefen Puffer Freigabe**</span><span class="sxs-lookup"><span data-stu-id="f2fa6-138">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="f2fa6-139">Festlegen des **Stereo Renderingmodus** auf eine **Einzel Pass Instanz**</span><span class="sxs-lookup"><span data-stu-id="f2fa6-139">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="f2fa6-140">Wählen Sie **WSA Holographic Remoting unterstützt** aus, wenn Sie Holographic Remoting verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-140">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobenem Abschnitt "Player Einstellungen"](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="f2fa6-142">Aktualisieren des Manifests</span><span class="sxs-lookup"><span data-stu-id="f2fa6-142">Updating the manifest</span></span>

<span data-ttu-id="f2fa6-143">Ihre APP kann jetzt Holographic-Rendering und räumliche Eingaben verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-143">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="f2fa6-144">Ihre APP muss jedoch die entsprechenden Funktionen in ihrem Manifest deklarieren, um von bestimmten Funktionen profitieren zu können.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-144">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="f2fa6-145">Sie finden Ihre Projektfunktionen, indem Sie zu den Einstellungen **für Player Einstellungen > Einstellungen für universelle Windows-Plattform > Veröffentlichungs Einstellungen > Funktionen** wechseln.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-145">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="f2fa6-146">Es wird empfohlen, dass Sie die Manifest-Deklarationen in Unity vornehmen, um Sie in allen zukünftigen Projekten einzuschließen, die Sie exportieren.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-146">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="f2fa6-147">Die anwendbaren Funktionen zum Aktivieren häufig verwendeter Unity-APIs für gemischte Realität sind:</span><span class="sxs-lookup"><span data-stu-id="f2fa6-147">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="f2fa6-148">Funktion</span><span class="sxs-lookup"><span data-stu-id="f2fa6-148">Capability</span></span>  |  <span data-ttu-id="f2fa6-149">APIs, die Funktionen erfordern</span><span class="sxs-lookup"><span data-stu-id="f2fa6-149">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="f2fa6-150">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="f2fa6-150">SpatialPerception</span></span>  |  <span data-ttu-id="f2fa6-151">"Surfaceobserver" (Zugriff auf [räumliche](../../design/spatial-mapping.md) zuordnungsnetze in hololens) ist &mdash; *für die allgemeine räumliche Nachverfolgung des Headsets nicht erforderlich* .</span><span class="sxs-lookup"><span data-stu-id="f2fa6-151">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="f2fa6-152">Webcam</span><span class="sxs-lookup"><span data-stu-id="f2fa6-152">WebCam</span></span>  |  <span data-ttu-id="f2fa6-153">Photocapture und Videocapture</span><span class="sxs-lookup"><span data-stu-id="f2fa6-153">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="f2fa6-154">Pictureslibrary/videoslibrary</span><span class="sxs-lookup"><span data-stu-id="f2fa6-154">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="f2fa6-155">Photocapture oder Videocapture bzw. (beim Speichern des erfassten Inhalts)</span><span class="sxs-lookup"><span data-stu-id="f2fa6-155">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="f2fa6-156">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="f2fa6-156">Microphone</span></span>  |  <span data-ttu-id="f2fa6-157">Videocapture (bei der Erfassung von Audiodaten), "diktationerkenzer", "grammarerkenzer" und "keywordrecognizer"</span><span class="sxs-lookup"><span data-stu-id="f2fa6-157">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="f2fa6-158">InternetClient</span><span class="sxs-lookup"><span data-stu-id="f2fa6-158">InternetClient</span></span>  |  <span data-ttu-id="f2fa6-159">"Diktationerkenzer" (und für die Verwendung des Unity-Profilers)</span><span class="sxs-lookup"><span data-stu-id="f2fa6-159">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="f2fa6-160">Qualitätseinstellungen</span><span class="sxs-lookup"><span data-stu-id="f2fa6-160">Quality settings</span></span>

<span data-ttu-id="f2fa6-161">Hololens verfügt über eine GPU mobiler Klasse.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-161">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="f2fa6-162">Wenn Ihre APP auf hololens ausgerichtet ist, sollten Sie die Qualitätseinstellungen in Ihrer APP auf die schnellste Leistung optimieren, um sicherzustellen, dass Sie die vollständige Framerate beibehält:</span><span class="sxs-lookup"><span data-stu-id="f2fa6-162">If your app is targeting HoloLens, you'll want the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate:</span></span>

1. <span data-ttu-id="f2fa6-163">Wählen Sie **> Projekteinstellungen bearbeiten > Qualität** aus.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="f2fa6-164">Wählen Sie im **Windows Store** -Logo die **Dropdown** Liste aus, und wählen Sie **sehr niedrig** aus.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="f2fa6-165">Sie werden feststellen, dass die Einstellung ordnungsgemäß angewendet wird, wenn das Feld in der Windows Store-Spalte und die **sehr niedrige** Zeile grün ist.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-165">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green</span></span>
3. <span data-ttu-id="f2fa6-166">Wählen Sie im Abschnitt **Shadows** die Option **Shadows deaktivieren** aus.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-166">In the **Shadows** section, select **Disable Shadows**</span></span>

<span data-ttu-id="f2fa6-167">![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobenem Abschnitt "Qualitätseinstellungen"](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="f2fa6-167">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="f2fa6-168">*Unity-Qualitätseinstellungen*</span><span class="sxs-lookup"><span data-stu-id="f2fa6-168">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="f2fa6-169">Pro-Szene-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="f2fa6-169">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="f2fa6-170">Unity-Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="f2fa6-170">Unity camera settings</span></span>

<span data-ttu-id="f2fa6-171">Wenn **Virtual Reality** aktiviert ist, behandelt die [Unity-Kamera](camera-in-unity.md) Komponente die [Kopf-und stereorenderingfunktionen](../platform-capabilities-and-apis/rendering.md).</span><span class="sxs-lookup"><span data-stu-id="f2fa6-171">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="f2fa6-172">Dies bedeutet, dass Sie das Hauptkamera Objekt nicht durch eine benutzerdefinierte Kamera ersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-172">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="f2fa6-173">Wenn Ihre APP speziell auf hololens ausgerichtet ist, müssen Sie einige Einstellungen ändern, um die transparente Anzeige des Geräts zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-173">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="f2fa6-174">Mit diesen Einstellungen können Sie Ihre Holographic-Inhalte in der physischen Welt anzeigen:</span><span class="sxs-lookup"><span data-stu-id="f2fa6-174">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="f2fa6-175">Wählen Sie in der **Hierarchie** die **Hauptkamera** aus.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-175">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="f2fa6-176">Legen Sie im **Inspektor** -Panel die Transformations **Position** auf **0, 0, 0** fest, sodass der Speicherort des Benutzer Kopfes am Ursprung der Unity-Welt beginnt.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-176">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="f2fa6-177">Ändern Sie die **Clear-Flags** in eine voll **Tonfarbe**.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-177">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="f2fa6-178">Ändern Sie die **Hintergrund** Farbe in **RGBA 0, 0, 0**, 0.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-178">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="f2fa6-179">Schwarz wird in hololens als transparent gerendert.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-179">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="f2fa6-180">Ändern Sie die **Clippingebenen in der Nähe** der [empfohlenen hololens](camera-in-unity.md#clip-planes) 0,85 (Meter).</span><span class="sxs-lookup"><span data-stu-id="f2fa6-180">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="f2fa6-181">![Screenshot der Registerkarte "Inspektor" im Unity-Editor](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="f2fa6-181">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="f2fa6-182">*Unity-Kameraeinstellungen*</span><span class="sxs-lookup"><span data-stu-id="f2fa6-182">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2fa6-183">Wenn Sie eine neue Kamera löschen und erstellen, stellen Sie sicher, dass die neue Kamera als " **maincamera**" gekennzeichnet ist.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-183">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f2fa6-184">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="f2fa6-184">Next steps</span></span>

<span data-ttu-id="f2fa6-185">Nachdem Ihr Projekt nun bereit ist, können Sie mit der Entwicklung ihrer gemischten Realität beginnen:</span><span class="sxs-lookup"><span data-stu-id="f2fa6-185">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="f2fa6-186">Hinzufügen von [Kern Bausteinen](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="f2fa6-186">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="f2fa6-187">Sehen Sie sich die verfügbaren [Plattformfunktionen und APIs](unity-development-overview.md#3-advanced-features) an</span><span class="sxs-lookup"><span data-stu-id="f2fa6-187">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="f2fa6-188">Erfahren Sie, wie [Sie Ihre APP](../platform-capabilities-and-apis/using-visual-studio.md#) bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f2fa6-188">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="f2fa6-189">Verwenden des [gemischten Reality-Simulators](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="f2fa6-189">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="f2fa6-190">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f2fa6-190">See also</span></span>
* [<span data-ttu-id="f2fa6-191">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="f2fa6-191">Install the tools</span></span>](../install-the-tools.md)