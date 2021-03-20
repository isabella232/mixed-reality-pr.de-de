---
title: Konfigurieren des Projekts ohne mrtk
description: Erfahren Sie, wie Sie ein neues Unity-Projekt für Windows Mixed Reality ohne das Mixed Reality Toolkit konfigurieren.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, gemischte Realität, Entwicklung, Einstieg, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung
ms.openlocfilehash: 8d247a6a5b7c8a3d8b7ea26ebc72e86ada5dc99f
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730167"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="c882a-104">Konfigurieren von Projekten ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="c882a-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="c882a-105">Windows Mixed Reality (WMR) ist eine Microsoft-Plattform, die als Teil des Betriebssystems Windows 10 eingeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c882a-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="c882a-106">Mit der WMR-Plattform können Sie Anwendungen erstellen, mit denen digitale Inhalte auf Holographic-und VR-Geräten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c882a-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="c882a-107">Obwohl Microsoft und die Community Open Source-Tools wie das [Mixed Reality Toolkit (mrtk)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) erstellt haben, das die WMR-Umgebung automatisch einrichten wird, möchten viele Entwickler ihre Erfahrungen von Grund auf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c882a-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="c882a-108">In der folgenden Dokumentation wird veranschaulicht, wie Sie ein Projekt für die Entwicklung mit gemischter Realität ordnungsgemäß einrichten, unabhängig davon, ob Sie mrtk verwenden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="c882a-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="c882a-109">Die Einstellungen, die Sie ändern müssen, werden in zwei Kategorien unterteilt: Einstellungen pro Projekt und Einstellungen pro Szene.</span><span class="sxs-lookup"><span data-stu-id="c882a-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="c882a-110">Sie können mrtk später jederzeit importieren, sodass es für die manuelle Route keinen Nachteil gibt.</span><span class="sxs-lookup"><span data-stu-id="c882a-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="c882a-111">Wenn Sie die manuelle Einrichtung von WMR auswählen, werden die Einstellungen, die Sie ändern müssen, in zwei Kategorien unterteilt: pro Projekt und pro Szene.</span><span class="sxs-lookup"><span data-stu-id="c882a-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="c882a-112">Einstellungen pro Projekt</span><span class="sxs-lookup"><span data-stu-id="c882a-112">Per-project settings</span></span>

<span data-ttu-id="c882a-113">Wenn Sie auf Desktop VR abzielen, empfiehlt es sich, die eigenständige PC-Plattform zu verwenden, die für ein neues Unity-Projekt standardmäßig ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="c882a-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit PC, Mac & eigenständige Plattform hervorgehoben](images/wmr-config-img-3.png)

<span data-ttu-id="c882a-115">Wenn Sie hololens 2 als Ziel verwenden, müssen Sie zum universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="c882a-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="c882a-116">**Datei > Buildeinstellungen auswählen...**</span><span class="sxs-lookup"><span data-stu-id="c882a-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="c882a-117">Wählen Sie in der Platt Form Liste **universelle Windows-Plattform** aus, und wählen Sie **Plattform wechseln**</span><span class="sxs-lookup"><span data-stu-id="c882a-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="c882a-118">**Architektur** auf **Arm 64** festlegen</span><span class="sxs-lookup"><span data-stu-id="c882a-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="c882a-119">**Zielgerät** auf **hololens** festlegen</span><span class="sxs-lookup"><span data-stu-id="c882a-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="c882a-120">**Buildtyp** auf **D3D** festlegen</span><span class="sxs-lookup"><span data-stu-id="c882a-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="c882a-121">**UWP SDK** auf **Letztes installiert** festlegen</span><span class="sxs-lookup"><span data-stu-id="c882a-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="c882a-122">**Buildkonfiguration** auf **Release** festlegen, da beim Debuggen bekannte Leistungsprobleme auftreten</span><span class="sxs-lookup"><span data-stu-id="c882a-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor öffnen mit hervorgehobener universelle Windows-Plattform](images/wmr-config-img-4.png)

<span data-ttu-id="c882a-124">Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass Sie beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellen soll.</span><span class="sxs-lookup"><span data-stu-id="c882a-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="c882a-125">Für xrsdk</span><span class="sxs-lookup"><span data-stu-id="c882a-125">For XRSDK</span></span> 

1. <span data-ttu-id="c882a-126">Navigieren Sie im Unity-Editor zu **Edit > Project Settings** , und wählen Sie die **Verwaltung von XR Plugin** aus.</span><span class="sxs-lookup"><span data-stu-id="c882a-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="c882a-127">Select </span><span class="sxs-lookup"><span data-stu-id="c882a-127">Select **Install XR Plugin Management**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet, mit hervorgehobener Verwaltung von XR](images/wmr-config-img-5.png)

3. <span data-ttu-id="c882a-129">Wählen Sie " **XR beim Start** und **Windows Mixed Reality** initialisieren" aus.</span><span class="sxs-lookup"><span data-stu-id="c882a-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet, mit hervorgehobener Verwaltung von XR](images/wmr-config-img-7.png)

4. <span data-ttu-id="c882a-131">Erweitern Sie den Abschnitt **XR-Plug-in-Verwaltung** , und wählen Sie die Registerkarte **universelle Windows-Plattform**</span><span class="sxs-lookup"><span data-stu-id="c882a-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="c882a-132">Wenn Sie Unity 2020 oder höher verwenden, sehen Sie die Optionen zum Überprüfen von **openxr (Vorschau)** oder **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="c882a-132">If you're using Unity 2020 or later, you'll see the options to check **OpenXR (preview)** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="c882a-133">Sie können beide Laufzeitoptionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="c882a-133">You can choose either runtime.</span></span>  <span data-ttu-id="c882a-134">Wenn Sie speziell für die hololens 2 oder den HP-Reverb-G2 entwickeln und das **openxr (Preview)** testen möchten, wählen Sie das Feld openxr (Vorschau) aus, und überprüfen Sie unsere Anleitung zur [Verwendung des Mixed Reality openxr-Plug-Ins für Unity](openxr-getting-started.md) , um sich vor der Rückkehr zu diesem Tutorial ordnungsgemäß für diese Geräte einzurichten.</span><span class="sxs-lookup"><span data-stu-id="c882a-134">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR (preview)**, select the OpenXR (preview) box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="c882a-135">Ab Unity 2020 LTS geht Microsoft mit der Entwicklung mit openxr um.</span><span class="sxs-lookup"><span data-stu-id="c882a-135">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="c882a-136">Wenn wir zu diesem Pfad migrieren, wird das Windows-XR-Plug-in in Unity 2021,1 als veraltet markiert und 2021,2 entfernt, sodass openxr der einzige unterstützte Pfad ist.</span><span class="sxs-lookup"><span data-stu-id="c882a-136">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="c882a-137">Weitere Informationen finden Sie unter [Verwenden des gemischten Reality openxr-Plug](openxr-getting-started.md)-ins.</span><span class="sxs-lookup"><span data-stu-id="c882a-137">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="c882a-138">Wenn Sie das **Windows Mixed Reality** -Plug-in auswählen, aktivieren Sie alle Kontrollkästchen, und legen Sie den tiefen Übermittlungs **Modus** auf **Tiefe 16 Bit** fest.</span><span class="sxs-lookup"><span data-stu-id="c882a-138">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet mit hervorgehobenem Windows Mixed Reality-Abschnitt](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="c882a-140">Für Legacy-XR</span><span class="sxs-lookup"><span data-stu-id="c882a-140">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="c882a-141">Legacy XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.</span><span class="sxs-lookup"><span data-stu-id="c882a-141">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="c882a-142">**Player Einstellungen** öffnen... aus den **Buildeinstellungen... Fenster** und erweitern Sie die Gruppe " **XR-Einstellungen** ".</span><span class="sxs-lookup"><span data-stu-id="c882a-142">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="c882a-143">Wählen Sie im Abschnitt " **XR-Einstellungen** " die Option **virtuelle Realität unterstützt** aus, um die Liste Virtual Reality-Geräte</span><span class="sxs-lookup"><span data-stu-id="c882a-143">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="c882a-144">Festlegen des **tiefen Formats** auf eine **16-Bit-Tiefe** und Aktivieren der **tiefen Puffer Freigabe**</span><span class="sxs-lookup"><span data-stu-id="c882a-144">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="c882a-145">Festlegen des **Stereo Renderingmodus** auf eine **Einzel Pass Instanz**</span><span class="sxs-lookup"><span data-stu-id="c882a-145">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="c882a-146">Wählen Sie **WSA Holographic Remoting unterstützt** aus, wenn Sie Holographic Remoting verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="c882a-146">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobenem Abschnitt "Player Einstellungen"](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="c882a-148">Aktualisieren des Manifests</span><span class="sxs-lookup"><span data-stu-id="c882a-148">Updating the manifest</span></span>

<span data-ttu-id="c882a-149">Ihre APP kann jetzt Holographic-Rendering und räumliche Eingaben verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="c882a-149">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="c882a-150">Ihre APP muss jedoch die entsprechenden Funktionen in ihrem Manifest deklarieren, um von bestimmten Funktionen profitieren zu können.</span><span class="sxs-lookup"><span data-stu-id="c882a-150">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="c882a-151">Sie finden Ihre Projektfunktionen, indem Sie zu den Einstellungen **für Player Einstellungen > Einstellungen für universelle Windows-Plattform > Veröffentlichungs Einstellungen > Funktionen** wechseln.</span><span class="sxs-lookup"><span data-stu-id="c882a-151">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="c882a-152">Es wird empfohlen, dass Sie die Manifest-Deklarationen in Unity vornehmen, um Sie in allen zukünftigen Projekten einzuschließen, die Sie exportieren.</span><span class="sxs-lookup"><span data-stu-id="c882a-152">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="c882a-153">Die anwendbaren Funktionen zum Aktivieren häufig verwendeter Unity-APIs für gemischte Realität sind:</span><span class="sxs-lookup"><span data-stu-id="c882a-153">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="c882a-154">Funktion</span><span class="sxs-lookup"><span data-stu-id="c882a-154">Capability</span></span>  |  <span data-ttu-id="c882a-155">APIs, die Funktionen erfordern</span><span class="sxs-lookup"><span data-stu-id="c882a-155">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="c882a-156">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="c882a-156">SpatialPerception</span></span>  |  <span data-ttu-id="c882a-157">"Surfaceobserver" (Zugriff auf [räumliche](../../design/spatial-mapping.md) zuordnungsnetze in hololens) ist &mdash; *für die allgemeine räumliche Nachverfolgung des Headsets nicht erforderlich* .</span><span class="sxs-lookup"><span data-stu-id="c882a-157">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="c882a-158">Webcam</span><span class="sxs-lookup"><span data-stu-id="c882a-158">WebCam</span></span>  |  <span data-ttu-id="c882a-159">Photocapture und Videocapture</span><span class="sxs-lookup"><span data-stu-id="c882a-159">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="c882a-160">Pictureslibrary/videoslibrary</span><span class="sxs-lookup"><span data-stu-id="c882a-160">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="c882a-161">Photocapture oder Videocapture bzw. (beim Speichern des erfassten Inhalts)</span><span class="sxs-lookup"><span data-stu-id="c882a-161">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="c882a-162">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="c882a-162">Microphone</span></span>  |  <span data-ttu-id="c882a-163">Videocapture (bei der Erfassung von Audiodaten), "diktationerkenzer", "grammarerkenzer" und "keywordrecognizer"</span><span class="sxs-lookup"><span data-stu-id="c882a-163">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="c882a-164">InternetClient</span><span class="sxs-lookup"><span data-stu-id="c882a-164">InternetClient</span></span>  |  <span data-ttu-id="c882a-165">"Diktationerkenzer" (und für die Verwendung des Unity-Profilers)</span><span class="sxs-lookup"><span data-stu-id="c882a-165">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="c882a-166">Qualitätseinstellungen</span><span class="sxs-lookup"><span data-stu-id="c882a-166">Quality settings</span></span>

<span data-ttu-id="c882a-167">Hololens verfügt über eine GPU mobiler Klasse.</span><span class="sxs-lookup"><span data-stu-id="c882a-167">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="c882a-168">Wenn Ihre APP auf hololens ausgerichtet ist, sollten Sie mit den Qualitätseinstellungen Ihrer APP beginnen, die für die schnellste Leistung optimiert ist, um sicherzustellen, dass Sie die vollständige Framerate beibehält.</span><span class="sxs-lookup"><span data-stu-id="c882a-168">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="c882a-169">Nachdem Sie Ihre Entwicklung weiterentwickelt haben, können Sie die Qualitätseinstellungen in Erwägung gezogen, um das richtige Gleichgewicht der Qualität und Leistung zu finden:</span><span class="sxs-lookup"><span data-stu-id="c882a-169">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="c882a-170">Wählen Sie **> Projekteinstellungen bearbeiten > Qualität** aus.</span><span class="sxs-lookup"><span data-stu-id="c882a-170">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="c882a-171">Wählen Sie im  **Windows Store**-Logo die **Dropdown** Liste aus,   und wählen Sie  **sehr niedrig** aus.</span><span class="sxs-lookup"><span data-stu-id="c882a-171">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="c882a-172">Sie werden feststellen, dass die Einstellung ordnungsgemäß angewendet wird, wenn das Feld in der Windows Store-Spalte und die sehr niedrige Zeile grün ist.</span><span class="sxs-lookup"><span data-stu-id="c882a-172">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="c882a-173">Wählen Sie im Abschnitt **Shadows** die Option    **Shadows deaktivieren** aus.</span><span class="sxs-lookup"><span data-stu-id="c882a-173">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="c882a-174">![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobenem Abschnitt "Qualitätseinstellungen"](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="c882a-174">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="c882a-175">*Unity-Qualitätseinstellungen*</span><span class="sxs-lookup"><span data-stu-id="c882a-175">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="c882a-176">Pro-Szene-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="c882a-176">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="c882a-177">Unity-Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="c882a-177">Unity camera settings</span></span>

<span data-ttu-id="c882a-178">Wenn **Virtual Reality** aktiviert ist, behandelt die [Unity-Kamera](camera-in-unity.md) Komponente die [Kopf-und stereorenderingfunktionen](../platform-capabilities-and-apis/rendering.md).</span><span class="sxs-lookup"><span data-stu-id="c882a-178">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="c882a-179">Dies bedeutet, dass Sie das Hauptkamera Objekt nicht durch eine benutzerdefinierte Kamera ersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="c882a-179">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="c882a-180">Wenn Ihre APP speziell auf hololens ausgerichtet ist, müssen Sie einige Einstellungen ändern, um die transparente Anzeige des Geräts zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="c882a-180">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="c882a-181">Mit diesen Einstellungen können Sie Ihre Holographic-Inhalte in der physischen Welt anzeigen:</span><span class="sxs-lookup"><span data-stu-id="c882a-181">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="c882a-182">Wählen Sie in der **Hierarchie** die **Hauptkamera** aus.</span><span class="sxs-lookup"><span data-stu-id="c882a-182">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="c882a-183">Legen Sie im **Inspektor** -Panel die Transformations **Position** auf **0, 0, 0** fest, sodass der Speicherort des Benutzer Kopfes am Ursprung der Unity-Welt beginnt.</span><span class="sxs-lookup"><span data-stu-id="c882a-183">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="c882a-184">Ändern Sie die **Clear-Flags** in eine voll **Tonfarbe**.</span><span class="sxs-lookup"><span data-stu-id="c882a-184">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="c882a-185">Ändern Sie die **Hintergrund** Farbe in **RGBA 0, 0, 0**, 0.</span><span class="sxs-lookup"><span data-stu-id="c882a-185">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="c882a-186">Schwarz wird in hololens als transparent gerendert.</span><span class="sxs-lookup"><span data-stu-id="c882a-186">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="c882a-187">Ändern Sie die **Clippingebenen in der Nähe** der [empfohlenen hololens](camera-in-unity.md#clip-planes) 0,85 (Meter).</span><span class="sxs-lookup"><span data-stu-id="c882a-187">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="c882a-188">![Screenshot der Registerkarte "Inspektor" im Unity-Editor](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="c882a-188">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="c882a-189">*Unity-Kameraeinstellungen*</span><span class="sxs-lookup"><span data-stu-id="c882a-189">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c882a-190">Wenn Sie eine neue Kamera löschen und erstellen, stellen Sie sicher, dass die neue Kamera als " **maincamera**" gekennzeichnet ist.</span><span class="sxs-lookup"><span data-stu-id="c882a-190">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c882a-191">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="c882a-191">Next steps</span></span>

<span data-ttu-id="c882a-192">Nachdem Ihr Projekt nun bereit ist, können Sie mit der Entwicklung ihrer gemischten Realität beginnen:</span><span class="sxs-lookup"><span data-stu-id="c882a-192">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="c882a-193">Hinzufügen von [Kern Bausteinen](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="c882a-193">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="c882a-194">Sehen Sie sich die verfügbaren [Plattformfunktionen und APIs](unity-development-overview.md#3-advanced-features) an</span><span class="sxs-lookup"><span data-stu-id="c882a-194">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="c882a-195">Erfahren Sie, wie [Sie Ihre APP](../platform-capabilities-and-apis/using-visual-studio.md#) bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c882a-195">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="c882a-196">Verwenden des [gemischten Reality-Simulators](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="c882a-196">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="c882a-197">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c882a-197">See also</span></span>
* [<span data-ttu-id="c882a-198">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="c882a-198">Install the tools</span></span>](../install-the-tools.md)