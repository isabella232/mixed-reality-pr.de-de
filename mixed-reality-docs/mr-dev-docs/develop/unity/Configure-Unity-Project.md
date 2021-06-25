---
title: Konfigurieren Ihres Projekts ohne MRTK
description: Erfahren Sie, wie Sie ein neues Unity-Projekt für Windows Mixed Reality ohne das Mixed Reality Toolkit konfigurieren.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, Mixed Reality, Entwicklung, erste Schritte, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung
ms.openlocfilehash: 12c3272708c6375b550d87eac86fe13a60c1f36d
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906886"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="0462e-104">Konfigurieren von Projekten ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="0462e-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="0462e-105">Windows Mixed Reality (WMR) ist eine Microsoft-Plattform, die als Teil des Windows 10 Betriebssystems eingeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="0462e-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="0462e-106">Mit der WMR-Plattform können Sie Anwendungen erstellen, die digitale Inhalte auf holografischen und VR-Anzeigegeräten rendern.</span><span class="sxs-lookup"><span data-stu-id="0462e-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="0462e-107">Während Microsoft und die Community Open Source-Tools wie das [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) erstellt haben, mit denen die WMR-Umgebung automatisch eingerichtet wird, möchten viele Entwickler ihre Erfahrungen von Grund auf erstellen.</span><span class="sxs-lookup"><span data-stu-id="0462e-107">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="0462e-108">In der folgenden Dokumentation wird veranschaulicht, wie Sie ein Projekt ordnungsgemäß für Mixed Reality Entwicklung einrichten, unabhängig davon, ob Sie MRTK verwenden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="0462e-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="0462e-109">Die Einstellungen, die Sie ändern müssen, sind in zwei Kategorien unterteilt: Einstellungen pro Projekt und Einstellungen pro Szene.</span><span class="sxs-lookup"><span data-stu-id="0462e-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="0462e-110">Sie können MRTK später immer importieren, sodass es keineRlei Einbußen beim ersten Durchlaufen der manuellen Route gibt.</span><span class="sxs-lookup"><span data-stu-id="0462e-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="0462e-111">Wenn Sie sich für das manuelle WMR-Setup entscheiden, werden die Einstellungen, die Sie ändern müssen, in zwei Kategorien unterteilt: pro Projekt und pro Szene.</span><span class="sxs-lookup"><span data-stu-id="0462e-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="0462e-112">Projektspezifische Einstellungen</span><span class="sxs-lookup"><span data-stu-id="0462e-112">Per-project settings</span></span>

<span data-ttu-id="0462e-113">Wenn Sie desktop VR als Ziel verwenden möchten, empfehlen wir, die pc Standalone Platform zu verwenden, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="0462e-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen", das im Unity-Editor geöffnet ist, wobei PC, Mac & eigenständige Plattform hervorgehoben ist](images/wmr-config-img-3.png)

<span data-ttu-id="0462e-115">Wenn Sie HoloLens 2 als Ziel haben, müssen Sie zum Universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="0462e-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="0462e-116">Wählen Sie **Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="0462e-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="0462e-117">Wählen Sie **Universelle Windows-Plattform** in der Liste Plattform und dann **Plattform wechseln** aus.</span><span class="sxs-lookup"><span data-stu-id="0462e-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="0462e-118">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="0462e-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="0462e-119">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="0462e-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="0462e-120">Legen Sie **Buildtyp** auf **D3D** fest</span><span class="sxs-lookup"><span data-stu-id="0462e-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="0462e-121">Legen Sie **UWP SDK** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="0462e-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="0462e-122">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="0462e-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

<span data-ttu-id="0462e-124">Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="0462e-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="0462e-125">Für XRSDK</span><span class="sxs-lookup"><span data-stu-id="0462e-125">For XRSDK</span></span> 

1. <span data-ttu-id="0462e-126">Navigieren Sie im Unity-Editor zu **> Projekteinstellungen bearbeiten,** und wählen Sie **XR-Plug-In-Verwaltung** aus.</span><span class="sxs-lookup"><span data-stu-id="0462e-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="0462e-127">Wählen Sie **XR-Plug-In-Verwaltung installieren aus.**</span><span class="sxs-lookup"><span data-stu-id="0462e-127">Select **Install XR Plugin Management**</span></span>

![Screenshot: Geöffnetes Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/wmr-config-img-5.png)

3. <span data-ttu-id="0462e-129">Wählen Sie **XR beim Start initialisieren** und **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="0462e-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot: Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/wmr-config-img-7.png)

4. <span data-ttu-id="0462e-131">Erweitern Sie den Abschnitt **XR-Plug-In-Verwaltung,** und wählen Sie die Registerkarte **Windows Platform Settings (Windows-Plattformeinstellungen)** aus.</span><span class="sxs-lookup"><span data-stu-id="0462e-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="0462e-132">Wenn Sie Unity 2020 oder höher verwenden, werden die Optionen zum Überprüfen von **OpenXR** oder **Windows Mixed Reality** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0462e-132">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="0462e-133">Sie können eine der beiden Laufzeiten auswählen.</span><span class="sxs-lookup"><span data-stu-id="0462e-133">You can choose either runtime.</span></span>  <span data-ttu-id="0462e-134">Wenn Sie speziell für die HoloLens 2 oder HP Reverb G2 entwickeln und **openXR** ausprobieren möchten, wählen Sie das Feld OpenXR aus, und lesen Sie unseren Leitfaden [zum Verwenden des Mixed Reality OpenXR-Plug-Ins für Unity,](./xr-project-setup.md) um sich für diese Geräte ordnungsgemäß einzurichten, bevor Sie zu diesem Tutorial zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="0462e-134">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](./xr-project-setup.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="0462e-135">Ab Unity 2020 LTS setzt Microsoft auf die Entwicklung mit OpenXR.</span><span class="sxs-lookup"><span data-stu-id="0462e-135">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="0462e-136">Bei der Migration zu diesem Pfad wird in Unity 2021.1 das Windows XR-Plug-In veraltet sein und in 2021.2 entfernt, sodass OpenXR der einzige unterstützte Pfad ist.</span><span class="sxs-lookup"><span data-stu-id="0462e-136">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="0462e-137">Weitere Informationen finden Sie unter [Verwenden des Mixed Reality OpenXR-Plug-Ins.](./xr-project-setup.md)</span><span class="sxs-lookup"><span data-stu-id="0462e-137">You can find more information in [Using the Mixed Reality OpenXR plugin](./xr-project-setup.md).</span></span>

6. <span data-ttu-id="0462e-138">Wenn Sie sich  für das Windows Mixed Reality-Plug-In entscheiden, aktivieren Sie alle Kontrollkästchen, und legen Sie **Den Tiefenübermittlungsmodus** auf **Tiefe 16 Bit** fest.</span><span class="sxs-lookup"><span data-stu-id="0462e-138">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot: Geöffnetes Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobener Windows Mixed Reality Abschnitt](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="0462e-140">Für Legacy-XR</span><span class="sxs-lookup"><span data-stu-id="0462e-140">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="0462e-141">Legacy-XR ist in Unity 2019 veraltet und wurde in Unity 2020 entfernt.</span><span class="sxs-lookup"><span data-stu-id="0462e-141">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="0462e-142">Öffnen **Sie Playereinstellungen...** aus den **Buildeinstellungen... Fenster** und Erweitern der Gruppe **"XR-Einstellungen"**</span><span class="sxs-lookup"><span data-stu-id="0462e-142">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="0462e-143">Wählen Sie im Abschnitt **XR-Einstellungen** die Option **Virtual Reality Unterstützt** aus, um die Liste Virtual Reality-Geräte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0462e-143">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="0462e-144">Festlegen des **Tiefenformats** auf **16-Bit-Tiefe** und Aktivieren der **Tiefenpufferfreigabe**</span><span class="sxs-lookup"><span data-stu-id="0462e-144">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="0462e-145">Festlegen **des Stereorenderingmodus** auf **eine Einzeldurchlaufinstanz**</span><span class="sxs-lookup"><span data-stu-id="0462e-145">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="0462e-146">Wählen Sie **WSA Holographic Remoting Supported (Unterstütztes WSA Holographic Remoting)** aus, wenn Sie Holographic Remoting verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="0462e-146">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Screenshot: Geöffnetes Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobenen Player-Einstellungen](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="0462e-148">Aktualisieren des Manifests</span><span class="sxs-lookup"><span data-stu-id="0462e-148">Updating the manifest</span></span>

<span data-ttu-id="0462e-149">Ihre App kann jetzt holografisches Rendering und räumliche Eingaben verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="0462e-149">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="0462e-150">Ihre App muss jedoch die entsprechenden Funktionen im Manifest deklarieren, um bestimmte Funktionen nutzen zu können.</span><span class="sxs-lookup"><span data-stu-id="0462e-150">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="0462e-151">Sie finden Ihre Projektfunktionen unter **Playereinstellungen > Einstellungen für Universelle Windows-Plattform > Veröffentlichungseinstellungen > Funktionen**.</span><span class="sxs-lookup"><span data-stu-id="0462e-151">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="0462e-152">Es wird empfohlen, die Manifestdeklarationen in Unity zu erstellen, um sie in alle zukünftigen Projekte einzubinden, die Sie exportieren.</span><span class="sxs-lookup"><span data-stu-id="0462e-152">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="0462e-153">Die anwendbaren Funktionen zum Aktivieren häufig verwendeter Unity-APIs für Mixed Reality sind:</span><span class="sxs-lookup"><span data-stu-id="0462e-153">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="0462e-154">Funktion</span><span class="sxs-lookup"><span data-stu-id="0462e-154">Capability</span></span>  |  <span data-ttu-id="0462e-155">APIs, die Funktionen erfordern</span><span class="sxs-lookup"><span data-stu-id="0462e-155">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="0462e-156">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="0462e-156">SpatialPerception</span></span>  |  <span data-ttu-id="0462e-157">SurfaceObserver (Zugriff auf [Raumzuordnungsgitternetze](../../design/spatial-mapping.md) auf HoloLens) &mdash; *Keine Funktion für allgemeine räumliche Nachverfolgung des Headsets erforderlich*</span><span class="sxs-lookup"><span data-stu-id="0462e-157">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="0462e-158">Webcam</span><span class="sxs-lookup"><span data-stu-id="0462e-158">WebCam</span></span>  |  <span data-ttu-id="0462e-159">PhotoCapture und VideoCapture</span><span class="sxs-lookup"><span data-stu-id="0462e-159">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="0462e-160">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="0462e-160">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="0462e-161">PhotoCapture bzw. VideoCapture (beim Speichern des erfassten Inhalts)</span><span class="sxs-lookup"><span data-stu-id="0462e-161">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="0462e-162">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="0462e-162">Microphone</span></span>  |  <span data-ttu-id="0462e-163">VideoCapture (beim Erfassen von Audio), DictationRecognizer, GrammarRecognizer und KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="0462e-163">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="0462e-164">InternetClient</span><span class="sxs-lookup"><span data-stu-id="0462e-164">InternetClient</span></span>  |  <span data-ttu-id="0462e-165">DictationRecognizer (und zur Verwendung des Unity Profilers)</span><span class="sxs-lookup"><span data-stu-id="0462e-165">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="0462e-166">Qualitätseinstellungen</span><span class="sxs-lookup"><span data-stu-id="0462e-166">Quality settings</span></span>

<span data-ttu-id="0462e-167">HoloLens verfügt über eine GPU der Mobilen Klasse.</span><span class="sxs-lookup"><span data-stu-id="0462e-167">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="0462e-168">Wenn Ihre App HoloLens als Ziel verwendet, sollten Sie mit den Qualitätseinstellungen in Ihrer App beginnen, die für die schnellste Leistung optimiert sind, um sicherzustellen, dass sie die vollständige Bildfrequenz beibehält.</span><span class="sxs-lookup"><span data-stu-id="0462e-168">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="0462e-169">Sobald Sie sich weiter in Ihrer Entwicklung befinden, können Sie die Qualitätseinstellungen in Betracht ziehen, um das richtige Gleichgewicht zwischen Qualität und Leistung zu finden:</span><span class="sxs-lookup"><span data-stu-id="0462e-169">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="0462e-170">Wählen Sie **> Projekteinstellungen > Qualität bearbeiten** aus.</span><span class="sxs-lookup"><span data-stu-id="0462e-170">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="0462e-171">Wählen Sie die **Dropdownliste** unter dem  **Windows Store-Logo**   und dann Sehr  **niedrig** aus.</span><span class="sxs-lookup"><span data-stu-id="0462e-171">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="0462e-172">Sie wissen, dass die Einstellung ordnungsgemäß angewendet wird, wenn das Feld in der Windows Store-Spalte und die Zeile "Sehr niedrig" grün sind.</span><span class="sxs-lookup"><span data-stu-id="0462e-172">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="0462e-173">Wählen Sie im Abschnitt **Schatten** die   Option Schatten deaktivieren **aus.**</span><span class="sxs-lookup"><span data-stu-id="0462e-173">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="0462e-174">![Screenshot: Geöffnetes Fenster "Projekteinstellungen" im Unity-Editor mit hervorgehobener Abschnitt "Qualitätseinstellungen"](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="0462e-174">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="0462e-175">*Unity-Qualitätseinstellungen*</span><span class="sxs-lookup"><span data-stu-id="0462e-175">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="0462e-176">Einstellungen pro Szene</span><span class="sxs-lookup"><span data-stu-id="0462e-176">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="0462e-177">Unity-Kameraeinstellungen</span><span class="sxs-lookup"><span data-stu-id="0462e-177">Unity camera settings</span></span>

<span data-ttu-id="0462e-178">Wenn **Virtual Reality Unterstützt aktiviert ist,** verarbeitet die [Unity-Kamerakomponente](camera-in-unity.md) die [Kopfverfolgung und stereoskopisches Rendering.](../platform-capabilities-and-apis/rendering.md)</span><span class="sxs-lookup"><span data-stu-id="0462e-178">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="0462e-179">Das bedeutet, dass Sie das Hauptkameraobjekt nicht durch eine benutzerdefinierte Kamera ersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="0462e-179">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="0462e-180">Wenn Ihre App speziell auf HoloLens ausgerichtet ist, müssen Sie einige Einstellungen ändern, um die Anzeige transparent auf dem Gerät zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="0462e-180">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="0462e-181">Mit diesen Einstellungen können Ihre holografischen Inhalte der physischen Welt angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="0462e-181">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="0462e-182">Wählen Sie in der **Hierarchie** die **Hauptkamera aus.**</span><span class="sxs-lookup"><span data-stu-id="0462e-182">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="0462e-183">Legen Sie im **Inspektorbereich** die **Transformationsposition** auf **0, 0, 0 fest,** damit die Position des Kopfes des Benutzers am Unity-Ursprung beginnt.</span><span class="sxs-lookup"><span data-stu-id="0462e-183">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="0462e-184">Ändern Sie **Clear Flags (Flags** löschen) in **Solid Color (Volltonfarbe).**</span><span class="sxs-lookup"><span data-stu-id="0462e-184">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="0462e-185">Ändern Sie die **Hintergrundfarbe** in **RGBA 0,0,0,0**.</span><span class="sxs-lookup"><span data-stu-id="0462e-185">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="0462e-186">Schwarz wird in HoloLens als transparent gerendert.</span><span class="sxs-lookup"><span data-stu-id="0462e-186">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="0462e-187">Ändern der **Clippingebenen: In** der Nähe der [holoLens empfohlenen](camera-in-unity.md#using-clipping-planes) 0,85 (Meter).</span><span class="sxs-lookup"><span data-stu-id="0462e-187">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#using-clipping-planes) 0.85 (meters).</span></span>

<span data-ttu-id="0462e-188">![Screenshot der geöffneten Inspektorregisterkarte im Unity-Editor](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="0462e-188">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="0462e-189">*Unity-Kameraeinstellungen*</span><span class="sxs-lookup"><span data-stu-id="0462e-189">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0462e-190">Wenn Sie eine neue Kamera löschen und erstellen, stellen Sie sicher, dass Ihre neue Kamera als **MainCamera** gekennzeichnet ist.</span><span class="sxs-lookup"><span data-stu-id="0462e-190">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0462e-191">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="0462e-191">Next steps</span></span>

<span data-ttu-id="0462e-192">Nachdem Ihr Projekt nun bereit ist, können Sie mit der Entwicklung Ihrer Mixed Reality beginnen:</span><span class="sxs-lookup"><span data-stu-id="0462e-192">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="0462e-193">Hinzufügen [von Kernbausteinen](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="0462e-193">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="0462e-194">Sehen Sie sich die verfügbaren [Plattformfunktionen und APIs](unity-development-overview.md#3-advanced-features) an.</span><span class="sxs-lookup"><span data-stu-id="0462e-194">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="0462e-195">Erfahren Sie, wie Sie [Ihre App bereitstellen.](../platform-capabilities-and-apis/using-visual-studio.md#)</span><span class="sxs-lookup"><span data-stu-id="0462e-195">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="0462e-196">Verwenden des [Mixed Reality Simulators](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="0462e-196">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="0462e-197">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0462e-197">See also</span></span>
* [<span data-ttu-id="0462e-198">Installieren der Tools</span><span class="sxs-lookup"><span data-stu-id="0462e-198">Install the tools</span></span>](../install-the-tools.md)