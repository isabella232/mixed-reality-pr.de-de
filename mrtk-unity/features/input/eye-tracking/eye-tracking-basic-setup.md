---
title: 'Eyetracking (Blickverfolgung): Grundlegende Einrichtung'
description: Einrichten von Eye Tracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Eye Tracking,
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144092"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a><span data-ttu-id="9fea7-104">Erste Schritte mit eye tracking in MRTK</span><span class="sxs-lookup"><span data-stu-id="9fea7-104">Getting started with eye tracking in MRTK</span></span>

<span data-ttu-id="9fea7-105">Auf dieser Seite erfahren Sie, wie Sie Ihre Unity MRTK-Szene für die Verwendung von Eyetracking in Ihrer App einrichten.</span><span class="sxs-lookup"><span data-stu-id="9fea7-105">This page covers how to set up your Unity MRTK scene to use eye tracking in your app.</span></span>
<span data-ttu-id="9fea7-106">Im Folgenden wird davon ausgegangen, dass Sie mit einer neuen Szene beginnen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-106">The following assumes you are starting out with a fresh new scene.</span></span>
<span data-ttu-id="9fea7-107">Alternativ können Sie sich unsere bereits konfigurierten [MRTK-Eyetrackingbeispiele](../../example-scenes/eye-tracking-examples-overview.md) mit vielen großartigen Beispielen, auf denen Sie direkt aufbauen können, informieren.</span><span class="sxs-lookup"><span data-stu-id="9fea7-107">Alternatively, you can check out our already configured [MRTK eye tracking examples](../../example-scenes/eye-tracking-examples-overview.md) with tons of great examples that you can directly build on.</span></span>

## <a name="eye-tracking-requirements-checklist"></a><span data-ttu-id="9fea7-108">Checkliste für Eyetrackinganforderungen</span><span class="sxs-lookup"><span data-stu-id="9fea7-108">Eye tracking requirements checklist</span></span>

<span data-ttu-id="9fea7-109">Damit eye tracking ordnungsgemäß funktioniert, müssen die folgenden Anforderungen erfüllt sein.</span><span class="sxs-lookup"><span data-stu-id="9fea7-109">For eye tracking to work correctly, the following requirements must be met.</span></span>
<span data-ttu-id="9fea7-110">Wenn Sie noch nicht mit der Eyetracking-HoloLens 2 und der Einrichtung von EyeTracking in MRTK noch nicht sehr schnell sind, machen Sie sich keine Sorgen!</span><span class="sxs-lookup"><span data-stu-id="9fea7-110">If you are new to eye tracking on HoloLens 2 and to how eye tracking is set up in MRTK, don't worry!</span></span>
<span data-ttu-id="9fea7-111">Im Folgenden wird ausführlich erläutert, wie sie behandelt werden können.</span><span class="sxs-lookup"><span data-stu-id="9fea7-111">We will go into detail on how to address each of them further below.</span></span>

1. <span data-ttu-id="9fea7-112">Dem _Eingabesystem muss Datenanbieter_ "Eye Gaze" hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="9fea7-112">An _'Eye Gaze Data Provider'_ must be added to the input system.</span></span> <span data-ttu-id="9fea7-113">Dies stellt Eyetrackingdaten von der Plattform zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="9fea7-113">This provides eye tracking data from the platform.</span></span>
2. <span data-ttu-id="9fea7-114">Die _Funktion "GazeInput"_ muss im Anwendungsmanifest aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="9fea7-114">The _'GazeInput'_ capability must be enabled in the application manifest.</span></span>
   <span data-ttu-id="9fea7-115">**Diese Funktion kann in Unity 2019 festgelegt werden, aber in Unity 2018 und früher ist diese Funktion nur in Visual Studio und über das MRTK-Buildtool verfügbar.**</span><span class="sxs-lookup"><span data-stu-id="9fea7-115">**This capability can be set in Unity 2019, but in Unity 2018 and earlier this capability is only available in Visual Studio and through the MRTK build tool**</span></span>
3. <span data-ttu-id="9fea7-116">Die HoloLens **muss für** den aktuellen Benutzer mit den Augen kalibriert sein.</span><span class="sxs-lookup"><span data-stu-id="9fea7-116">The HoloLens **must** be eye calibrated for the current user.</span></span> <span data-ttu-id="9fea7-117">Sehen Sie sich unser [Beispiel an, um zu ermitteln, ob ein Benutzer mit](eye-tracking-is-user-calibrated.md)den Augen kalibriert ist oder nicht.</span><span class="sxs-lookup"><span data-stu-id="9fea7-117">Check out our [sample for detecting whether a user is eye calibrated or not](eye-tracking-is-user-calibrated.md).</span></span>

### <a name="a-note-on-the-gazeinput-capability"></a><span data-ttu-id="9fea7-118">Hinweis zur GazeInput-Funktion</span><span class="sxs-lookup"><span data-stu-id="9fea7-118">A note on the GazeInput capability</span></span>

<span data-ttu-id="9fea7-119">Die vom MRTK bereitgestellten Buildtools (d. h. Mixed Reality Toolkit -> Utilities -> Build Window) können die GazeInput-Funktion automatisch für Sie aktivieren.</span><span class="sxs-lookup"><span data-stu-id="9fea7-119">The MRTK-provided build tooling (i.e. Mixed Reality Toolkit -> Utilities -> Build Window) can automatically enable the GazeInput capability for you.</span></span> <span data-ttu-id="9fea7-120">Hierzu müssen Sie sicherstellen, dass auf der Registerkarte "Appx Build Options" (Appx-Buildoptionen) die Option "Gaze Input Capability" (Eingabefunktion zum Anv überprüfen) angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="9fea7-120">In order to do this, you need to make sure that the 'Gaze Input Capability' is checked on the 'Appx Build Options' tab:</span></span>

![MRTK-Buildtools](../../images/eye-tracking/mrtk_et_buildsetup.png)

<span data-ttu-id="9fea7-122">Mit diesen Tools wird das AppX-Manifest nach Abschluss des Unity-Builds gesucht und die GazeInput-Funktion manuell hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="9fea7-122">This tooling will find the AppX manifest after the Unity build is completed and manually add the GazeInput capability.</span></span>
<span data-ttu-id="9fea7-123">**Vor Unity 2019 ist dieses Tool NICHT aktiv, wenn** das integrierte Buildfenster von Unity verwendet wird (d. h. Datei -> Buildeinstellungen).</span><span class="sxs-lookup"><span data-stu-id="9fea7-123">**Prior to Unity 2019, this tooling is NOT active when using Unity's built-in Build Window** (i.e. File -> Build Settings).</span></span>

<span data-ttu-id="9fea7-124">Vor Unity 2019 muss die Funktion bei Verwendung des Unity-Buildfensters nach dem Unity-Build wie folgt manuell hinzugefügt werden:</span><span class="sxs-lookup"><span data-stu-id="9fea7-124">Prior to Unity 2019, when using Unity's build window, the capability will need to be manually added after the Unity build, as follows:</span></span>

1. <span data-ttu-id="9fea7-125">Öffnen Sie das kompilierte Visual Studio-Projekt, und öffnen Sie dann _"Package.appxmanifest"_ in Ihrer Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="9fea7-125">Open your compiled Visual Studio project and then open the _'Package.appxmanifest'_ in your solution.</span></span>
2. <span data-ttu-id="9fea7-126">Aktivieren Sie unter _Funktionen_ das Kontrollkästchen _"GazeInput"._</span><span class="sxs-lookup"><span data-stu-id="9fea7-126">Make sure to tick the _'GazeInput'_ checkbox under _Capabilities_.</span></span> <span data-ttu-id="9fea7-127">Wenn keine _GazeInput-Funktion_ angezeigt wird, überprüfen Sie, ob Ihr System die Voraussetzungen für die [Verwendung von MRTK](/windows/mixed-reality/develop/install-the-tools) erfüllt (insbesondere die Windows SDK Version).</span><span class="sxs-lookup"><span data-stu-id="9fea7-127">If you don't see a _'GazeInput'_ capability, check that your system meets the [prerequisites for using MRTK](/windows/mixed-reality/develop/install-the-tools) (in particular the Windows SDK version).</span></span>

<span data-ttu-id="9fea7-128">_Beachten Sie:_ Sie müssen dies nur tun, wenn Sie einen neuen Buildordner erstellen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-128">_Please note:_ You only have to do this if you build into a new build folder.</span></span>
<span data-ttu-id="9fea7-129">Dies bedeutet, dass Sie Ihre Änderungen nicht erneut übernehmen müssen, wenn Sie ihr Unity-Projekt bereits erstellt und das appxmanifest vor eingerichtet haben und jetzt wieder auf denselben Ordner abzielen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-129">This means that if you had already built your Unity project and set up the appxmanifest before and now target the same folder again, you will not need to reapply your changes.</span></span>

## <a name="setting-up-eye-tracking-step-by-step"></a><span data-ttu-id="9fea7-130">Einrichten der Eyetracking schritt für Schritt</span><span class="sxs-lookup"><span data-stu-id="9fea7-130">Setting up eye tracking step-by-step</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="9fea7-131">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="9fea7-131">Setting up the scene</span></span>

<span data-ttu-id="9fea7-132">Richten Sie _das MixedRealityToolkit_ ein, indem Sie einfach auf _"Mixed Reality Toolkit -> Configure..." klicken._</span><span class="sxs-lookup"><span data-stu-id="9fea7-132">Set up the _MixedRealityToolkit_ by simply clicking _'Mixed Reality Toolkit -> Configure…'_</span></span> <span data-ttu-id="9fea7-133">in der Menüleiste.</span><span class="sxs-lookup"><span data-stu-id="9fea7-133">in the menu bar.</span></span>

![MRTK-Konfiguration](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a><span data-ttu-id="9fea7-135">Einrichten der MRTK-Profile, die für eye tracking erforderlich sind</span><span class="sxs-lookup"><span data-stu-id="9fea7-135">Setting up the MRTK profiles required for eye tracking</span></span>

<span data-ttu-id="9fea7-136">Nachdem Sie Ihre MRTK-Szene eingerichtet haben, werden Sie aufgefordert, ein Profil für MRTK auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-136">After setting up your MRTK scene, you will be asked to choose a profile for MRTK.</span></span>
<span data-ttu-id="9fea7-137">Sie können einfach _DefaultMixedRealityToolkitConfigurationProfile_ und dann die Option _"Kopieren & Anpassen"_ auswählen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-137">You can simply select _DefaultMixedRealityToolkitConfigurationProfile_ and then select the _'Copy & Customize'_ option.</span></span>

![MRTK-Profil](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a><span data-ttu-id="9fea7-139">Erstellen eines Datenanbieters zum Anvieren mit den Augen</span><span class="sxs-lookup"><span data-stu-id="9fea7-139">Create an "eye gaze data provider"</span></span>

- <span data-ttu-id="9fea7-140">Klicken Sie in Ihrem MRTK-Profil auf die Registerkarte _"Eingabe"._</span><span class="sxs-lookup"><span data-stu-id="9fea7-140">Click on the _'Input'_ tab in your MRTK profile.</span></span>
- <span data-ttu-id="9fea7-141">Klicken Sie auf die Schaltfläche _"Klonen",_ um die Standardeinstellung _(DefaultMixedRealityInputSystemProfile)_ zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="9fea7-141">To edit the default one ( _'DefaultMixedRealityInputSystemProfile'_ ), click the _'Clone'_ button next to it.</span></span> <span data-ttu-id="9fea7-142">Das _Menü "Profil klonen"_ wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9fea7-142">A _'Clone Profile'_ menu appears.</span></span> <span data-ttu-id="9fea7-143">Klicken Sie einfach _am unteren_ Rand dieses Menüs auf "Klonen".</span><span class="sxs-lookup"><span data-stu-id="9fea7-143">Simply click on _'Clone'_ at the bottom of that menu.</span></span>
- <span data-ttu-id="9fea7-144">Doppelklicken Sie auf Ihr neues Eingabeprofil, erweitern Sie _"Eingabedatenanbieter",_ und wählen Sie _"+ Hinzufügen Datenanbieter" aus._</span><span class="sxs-lookup"><span data-stu-id="9fea7-144">Double click on your new input profile, expand _'Input Data Providers'_, and select _'+ Add Data Provider'_.</span></span>
- <span data-ttu-id="9fea7-145">Erstellen Sie einen neuen Datenanbieter:</span><span class="sxs-lookup"><span data-stu-id="9fea7-145">Create a new data provider:</span></span>
  - <span data-ttu-id="9fea7-146">Wählen **Sie** unter Typ _die Option "Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input"_  ->  _"WindowsMixedRealityEye DateitypDataProvider" aus._</span><span class="sxs-lookup"><span data-stu-id="9fea7-146">Under **Type** select _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_ -> _'WindowsMixedRealityEyeGazeDataProvider'_</span></span>
  - <span data-ttu-id="9fea7-147">Wählen **Sie für Plattform(en)** _die Option "Windows Universal" aus._</span><span class="sxs-lookup"><span data-stu-id="9fea7-147">For **Platform(s)** select _'Windows Universal'_.</span></span>

![MRTK-Datenanbieter](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a><span data-ttu-id="9fea7-149">Simulieren von Eyetracking im Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="9fea7-149">Simulating eye tracking in the Unity Editor</span></span>

<span data-ttu-id="9fea7-150">Sie können eye tracking-Eingaben im Unity-Editor simulieren, um sicherzustellen, dass Ereignisse ordnungsgemäß ausgelöst werden, bevor Sie die App in Ihrem HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9fea7-150">You can simulate eye tracking input in the Unity Editor to ensure that events are correctly triggered before deploying the app to your HoloLens 2.</span></span>
<span data-ttu-id="9fea7-151">Das Anvisieren mit den Augen wird simuliert, indem einfach die Position der Kamera als Ursprung des Anvisierens mit den Augen und der Vorwärtsvektor der Kamera als Blickrichtung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9fea7-151">The eye gaze signal is simulated by simply using the camera's location as eye gaze origin and the camera's forward vector as eye gaze direction.</span></span>
<span data-ttu-id="9fea7-152">Obwohl dies für erste Tests ideal ist, beachten Sie, dass es sich nicht um eine gute Imitation für schnelle Augenbewegungen handelt.</span><span class="sxs-lookup"><span data-stu-id="9fea7-152">While this is great for initial testing, please note that it is not a good imitation for rapid eye movements.</span></span>
<span data-ttu-id="9fea7-153">Dafür ist es besser, häufige Tests Ihrer augenbasierten Interaktionen mit dem HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9fea7-153">For this, it is better to ensure frequent tests of your eye-based interactions on the HoloLens 2.</span></span>

1. <span data-ttu-id="9fea7-154">**Aktivieren sie simuliertes Eyetracking:**</span><span class="sxs-lookup"><span data-stu-id="9fea7-154">**Enable simulated eye tracking**:</span></span>
    - <span data-ttu-id="9fea7-155">Klicken Sie _in_ Ihrem MRTK-Konfigurationsprofil auf die Registerkarte "Eingabe".</span><span class="sxs-lookup"><span data-stu-id="9fea7-155">Click on the _'Input'_ tab in your MRTK configuration profile.</span></span>
    - <span data-ttu-id="9fea7-156">Navigieren Sie von dort zu _"Eingabedatenanbieter"_  ->  _"Eingabesimulationsdienst"._</span><span class="sxs-lookup"><span data-stu-id="9fea7-156">From there, navigate to _'Input Data Providers'_ -> _'Input Simulation Service'_.</span></span>
    - <span data-ttu-id="9fea7-157">_Klonen Sie "DefaultMixedRealityInputSimpulationProfile",_ um Änderungen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-157">Clone the _'DefaultMixedRealityInputSimpulationProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="9fea7-158">Aktivieren Sie _das Kontrollkästchen "Simulate Eye Position"_ (Augenposition simulieren).</span><span class="sxs-lookup"><span data-stu-id="9fea7-158">Check the _'Simulate Eye Position'_ checkbox.</span></span>

    ![MRTK-Augen simulieren](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. <span data-ttu-id="9fea7-160">**Standardcursor für** den Anvanvitätszeiger mit dem Kopf deaktivieren: Im Allgemeinen wird empfohlen, die Anzeige eines Cursors mit dem Anvitätszeiger mit den Augen zu vermeiden oder wenn dies unbedingt erforderlich ist, um ihn sehr dezent _zu_ machen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-160">**Disable default head gaze cursor**: In general, it is recommended to avoid showing an eye gaze cursor or if absolutely required to make it _very_ subtle.</span></span>
<span data-ttu-id="9fea7-161">Es wird empfohlen, den Standardmäßigen Cursor zum Anvieren mit dem Kopf auszublenden, der standardmäßig an das MRTK-Blickzeigerprofil angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="9fea7-161">We do recommend to hide the default head gaze cursor that is attached to the MRTK gaze pointer profile by default.</span></span>
    - <span data-ttu-id="9fea7-162">Navigieren Sie zu Ihrem MRTK-Konfigurationsprofil, und > _"Eingabe"_  ->  _"Zeiger"_</span><span class="sxs-lookup"><span data-stu-id="9fea7-162">Navigate to your MRTK configuration profile -> _'Input'_ -> _'Pointers'_</span></span>
    - <span data-ttu-id="9fea7-163">_Klonen Sie das "DefaultMixedRealityInputPointerProfile",_ um Änderungen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-163">Clone the _'DefaultMixedRealityInputPointerProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="9fea7-164">Am oberen Ende der _Zeigereinstellungen_ sollten Sie dem _"GazeCursor"_ ein unsichtbares Cursor-Prefab zuweisen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-164">At the top of the _'Pointer Settings'_, you should assign an invisible cursor prefab to the _'GazeCursor'_.</span></span> <span data-ttu-id="9fea7-165">Wählen Sie hierzu in der MRTK Foundation das _Prefab "Eye Eye EyeeCursor"_ aus.</span><span class="sxs-lookup"><span data-stu-id="9fea7-165">You can do this by selecting the _'EyeGazeCursor'_ prefab from the MRTK Foundation.</span></span>

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="9fea7-166">Aktivieren des blickbasierten Anvierens im Anvierungsanbieter</span><span class="sxs-lookup"><span data-stu-id="9fea7-166">Enabling eye-based gaze in the gaze provider</span></span>

<span data-ttu-id="9fea7-167">In HoloLens v1 wurde das Anvieren mit dem Kopf als primäres Zeigerverfahren verwendet.</span><span class="sxs-lookup"><span data-stu-id="9fea7-167">In HoloLens v1, head gaze was used as primary pointing technique.</span></span>
<span data-ttu-id="9fea7-168">Während das Anvieren mit dem Kopf weiterhin über _den GazeProvider_ im MRTK verfügbar ist, der an Ihre Kamera angefügt [ist,](https://docs.unity3d.com/ScriptReference/Camera.html)können Sie überprüfen, ob Sie stattdessen das Anvieren mit den Augen verwenden, indem Sie das Kontrollkästchen _"IsEyeTrackingEnabled"_ in den Anvitierungseinstellungen des Eingabezeigerprofils aktivieren.</span><span class="sxs-lookup"><span data-stu-id="9fea7-168">While head gaze is still available via the _GazeProvider_ in MRTK which is attached to your [Camera](https://docs.unity3d.com/ScriptReference/Camera.html), you can check to use eye gaze instead by ticking the _'IsEyeTrackingEnabled'_ checkbox in the gaze settings of the input pointer profile.</span></span>

>[!NOTE]
><span data-ttu-id="9fea7-169">Entwickler können zwischen dem blickbasierten Anvieren und dem kopfbasierten Anvieren im Code wechseln, indem sie die _Eigenschaft "IsEyeTrackingEnabled"_ von _"GazeProvider" ändern._</span><span class="sxs-lookup"><span data-stu-id="9fea7-169">Developers can toggle between eye-based gaze and head-based gaze in code by changing the _'IsEyeTrackingEnabled'_ property of _'GazeProvider'_.</span></span>  

>[!IMPORTANT]
><span data-ttu-id="9fea7-170">Wenn eine der Eyetrackinganforderungen nicht erfüllt wird, wird die Anwendung automatisch auf das kopfbasierte Anving zurückfallen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-170">If any of the eye tracking requirements are not met, the application will automatically fall back to head-based gaze.</span></span>

### <a name="accessing-eye-gaze-data"></a><span data-ttu-id="9fea7-171">Zugreifen auf Daten zum Anvieren mit den Augen</span><span class="sxs-lookup"><span data-stu-id="9fea7-171">Accessing eye gaze data</span></span>

<span data-ttu-id="9fea7-172">Nachdem Ihre Szene nun für die Verwendung der Eyetracking eingerichtet ist, sehen wir uns an, wie Sie in Ihren [Skripts](eye-tracking-target-selection.md)darauf zugreifen: Zugreifen auf Eyetrackingdaten über [EyeTrackeProvider](eye-tracking-eye-gaze-provider.md) und von den Augen unterstützte Zielauswahlen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-172">Now that your scene is set up to use eye tracking, let's take a look at how to access it in your scripts: [Accessing eye tracking data via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) and [eye-supported target selections](eye-tracking-target-selection.md).</span></span>

### <a name="testing-your-unity-app-on-a-hololens-2"></a><span data-ttu-id="9fea7-173">Testen Ihrer Unity-App auf HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9fea7-173">Testing your Unity app on a HoloLens 2</span></span>

<span data-ttu-id="9fea7-174">Das Erstellen Ihrer App mit Eyetracking sollte mit der Kompilierung anderer mrtk HoloLens 2-Apps vergleichbar sein.</span><span class="sxs-lookup"><span data-stu-id="9fea7-174">Building your app with eye tracking should be similar to how you would compile other HoloLens 2 MRTK apps.</span></span> <span data-ttu-id="9fea7-175">Stellen Sie sicher, dass Sie die Funktion *"Eingabe* anvizieren" aktiviert haben, wie oben im Abschnitt [*A note on the GazeInput capability (Hinweis zur GazeInput-Funktion) beschrieben.*](#a-note-on-the-gazeinput-capability)</span><span class="sxs-lookup"><span data-stu-id="9fea7-175">Be sure that you have enabled the *'Gaze Input'* capability as described above in the section [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability).</span></span>

#### <a name="eye-calibration"></a><span data-ttu-id="9fea7-176">Kalibrierung der Augen</span><span class="sxs-lookup"><span data-stu-id="9fea7-176">Eye calibration</span></span>

<span data-ttu-id="9fea7-177">Vergessen Sie abschließend nicht, die Kalibrierung der Augen auf Ihrem Gerät HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9fea7-177">Finally, please don't forget to run through the eye calibration on your HoloLens 2.</span></span>
<span data-ttu-id="9fea7-178">Das Eyetrackingsystem gibt keine Eingaben zurück, wenn der Benutzer nicht kalibriert ist.</span><span class="sxs-lookup"><span data-stu-id="9fea7-178">The eye tracking system will not return any input if the user is not calibrated.</span></span>
<span data-ttu-id="9fea7-179">Am einfachsten erreichen Sie die Kalibrierung, indem Sie das Visor nach oben und wieder nach unten kippen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-179">Easiest way to get to the calibration is by flipping up the visor and back down.</span></span>
<span data-ttu-id="9fea7-180">Eine Systembenachrichtigung sollte Sie als neuen Benutzer einladen und Sie bitten, die Kalibrierung der Augen zu durchgehen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-180">A system notification should appear welcoming you as a new user and asking you to go through the eye calibration.</span></span>
<span data-ttu-id="9fea7-181">Alternativ finden Sie die Augenkalibrierung in den Systemeinstellungen: Einstellungen > System > Kalibrierung > Kalibrierung der Augen ausführen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-181">Alternatively you can find the eye calibration in the system settings: Settings > System > Calibration > Run eye calibration.</span></span>

#### <a name="eye-tracking-permission"></a><span data-ttu-id="9fea7-182">Eyetrackingberechtigung</span><span class="sxs-lookup"><span data-stu-id="9fea7-182">Eye tracking permission</span></span>

<span data-ttu-id="9fea7-183">Wenn Sie die App auf Ihrem HoloLens 2 zum ersten Mal starten, sollte eine Eingabeaufforderung angezeigt werden, in der der Benutzer um die Berechtigung zur Verwendung der Eyetracking gebeten wird.</span><span class="sxs-lookup"><span data-stu-id="9fea7-183">When starting the app on your HoloLens 2 for the first time, a prompt should pop up asking the user for permission to use eye tracking.</span></span>
<span data-ttu-id="9fea7-184">Wenn sie nicht angezeigt wird, ist dies in der Regel ein Hinweis darauf, dass die _GazeInput-Funktion_ nicht festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="9fea7-184">If it is not showing up, then that is usually an indication that the _'GazeInput'_ capability was not set.</span></span>

<span data-ttu-id="9fea7-185">Nachdem die Berechtigungsaufforderung einmal angezeigt wurde, wird sie nicht automatisch erneut angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9fea7-185">After the permission prompt showed up once, it will not show up automatically again.</span></span>
<span data-ttu-id="9fea7-186">Wenn Sie _die Eyetrackingberechtigung verweigert_ haben, können Sie dies unter Einstellungen -> Datenschutz -> Apps zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-186">If you _"denied eye tracking permission"_, you can reset this in Settings -> Privacy -> Apps.</span></span>

---

<span data-ttu-id="9fea7-187">Dies sollte Ihnen den Einstieg in die Verwendung von Eyetracking in Ihrer MRTK Unity-App bringen.</span><span class="sxs-lookup"><span data-stu-id="9fea7-187">This should get you started with using eye tracking in your MRTK Unity app.</span></span>
<span data-ttu-id="9fea7-188">Vergessen Sie nicht, [unsere MRTK-Eyetracking-Tutorials und -Beispiele](../../example-scenes/eye-tracking-examples-overview.md) zu lesen, die veranschaulichen, wie Sie Eyetrackingeingaben verwenden und skripts bereitstellen, die Sie in Ihren Projekten wiederverwenden können.</span><span class="sxs-lookup"><span data-stu-id="9fea7-188">Don't forget to check out [our MRTK eye tracking tutorials and samples](../../example-scenes/eye-tracking-examples-overview.md) demonstrating how to use eye tracking input and conveniently providing scripts that you can reuse in your projects.</span></span>

---
[<span data-ttu-id="9fea7-189">Zurück zu "Eye tracking in the MixedRealityToolkit" (Blickverfolgung im MixedRealityToolkit)</span><span class="sxs-lookup"><span data-stu-id="9fea7-189">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)