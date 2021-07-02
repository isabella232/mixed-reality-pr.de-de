---
title: Übersicht über Eyetrackingbeispiele
description: Beispiel zum Erstellen von Eyetracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: 4cdeaa10725e00ac1a041c3692d64c1bd6488854
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175544"
---
# <a name="eye-tracking-examples-overview"></a><span data-ttu-id="57537-104">Übersicht über Eyetrackingbeispiele</span><span class="sxs-lookup"><span data-stu-id="57537-104">Eye tracking examples overview</span></span>

<span data-ttu-id="57537-105">In diesem Thema wird beschrieben, wie Sie schnell mit eye tracking in MRTK beginnen können, indem Sie auf MRTK-Eyetrackingbeispielen (Assets/MRTK/Examples/Demos/EyeTracking) aufbauen.</span><span class="sxs-lookup"><span data-stu-id="57537-105">This topic describes how to quickly get started with eye tracking in MRTK by building on MRTK eye tracking examples (Assets/MRTK/Examples/Demos/EyeTracking).</span></span>
<span data-ttu-id="57537-106">Mit diesen Beispielen können Sie eine unserer neuen magischen Eingabefunktionen erleben: **Eye tracking**!</span><span class="sxs-lookup"><span data-stu-id="57537-106">These samples let you experience one of our new magical input capabilities: **Eye tracking**!</span></span>
<span data-ttu-id="57537-107">Die Demo enthält verschiedene Anwendungsfälle, die von impliziten augenbasierten Aktivierungen bis hin zur nahtlosen Kombination von Informationen zu dem, was Sie betrachten, mit **Sprach-** und **Handeingaben** reichen.</span><span class="sxs-lookup"><span data-stu-id="57537-107">The demo includes various use cases, ranging from implicit eye-based activations to how to seamlessly combine information about what you are looking at with **voice** and **hand** input.</span></span>
<span data-ttu-id="57537-108">Dadurch können Benutzer holografische Inhalte schnell und mühelos auswählen und über ihre Ansicht verschieben, indem sie einfach ein Ziel betrachten und _"Auswählen"_ sagen oder eine Handgeste ausführen.</span><span class="sxs-lookup"><span data-stu-id="57537-108">This enables users to quickly and effortlessly select and move holographic content across their view simply by looking at a target and saying _'Select'_ or performing a hand gesture.</span></span>
<span data-ttu-id="57537-109">Die Demos enthalten auch ein Beispiel für bildlaufgesteuertes Anvieren mit den Augen, Schwenken und Zoomen von Text und Bildern auf einer Schiefer.</span><span class="sxs-lookup"><span data-stu-id="57537-109">The demos also include an example for eye-gaze-directed scroll, pan and zoom of text and images on a slate.</span></span>
<span data-ttu-id="57537-110">Schließlich wird ein Beispiel für die Aufzeichnung und Visualisierung der visuellen Aufmerksamkeit des Benutzers auf einer 2D-Schiefer bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="57537-110">Finally, an example is provided for recording and visualizing the user's visual attention on a 2D slate.</span></span>
<span data-ttu-id="57537-111">Im folgenden Abschnitt finden Sie weitere Details zu den einzelnen Beispielen im MRTK-Beispielpaket zur Blickverfolgung (Assets/MRTK/Examples/Demos/EyeTracking):</span><span class="sxs-lookup"><span data-stu-id="57537-111">In the following section, you will find more details on what each of the different samples in the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking) includes:</span></span>

![Liste der Blickverfolgungsszenen](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

<span data-ttu-id="57537-113">Der folgende Abschnitt enthält eine kurze Übersicht über die einzelnen Eyetracking-Demoszenen.</span><span class="sxs-lookup"><span data-stu-id="57537-113">The following section is a quick overview of what the individual eye tracking demo scenes are about.</span></span>
<span data-ttu-id="57537-114">Die MRTK-Blickverfolgungs-Demoszenen werden [additiv geladen,](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)was im Folgenden erläutert wird, wie sie eingerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="57537-114">The MRTK eye tracking demo scenes are [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), which we will explain below how to set up.</span></span>

## <a name="overview-of-the-eye-tracking-demo-samples"></a><span data-ttu-id="57537-115">Übersicht über die Eyetracking-Demobeispiele</span><span class="sxs-lookup"><span data-stu-id="57537-115">Overview of the eye tracking demo samples</span></span>

### <a name="eye-supported-target-selection"></a>[<span data-ttu-id="57537-116">**Durch die Augen unterstützte Zielauswahl**</span><span class="sxs-lookup"><span data-stu-id="57537-116">**Eye-Supported Target Selection**</span></span>](../input/eye-tracking/eye-tracking-target-selection.md)

<span data-ttu-id="57537-117">In diesem Tutorial wird veranschaulicht, wie einfach der Zugriff auf Daten zum Anvisierten der Augen zum Auswählen von Zielen ist.</span><span class="sxs-lookup"><span data-stu-id="57537-117">This tutorial showcases the ease of accessing eye gaze data to select targets.</span></span>
<span data-ttu-id="57537-118">Es enthält ein Beispiel für ein dezentes, aber leistungsstarkes Feedback, um dem Benutzer das Vertrauen zu geben, dass ein Ziel fokussiert ist, ohne überwältigend zu sein.</span><span class="sxs-lookup"><span data-stu-id="57537-118">It includes an example for subtle yet powerful feedback to provide the user with the confidence that a target is focused without being overwhelming.</span></span>
<span data-ttu-id="57537-119">Darüber hinaus gibt es ein einfaches Beispiel für intelligente Benachrichtigungen, die nach dem Lesen automatisch ausgeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="57537-119">In addition, there is a simple example of smart notifications that automatically disappear after being read.</span></span>

<span data-ttu-id="57537-120">**Zusammenfassung:** Schnelle und mühelose Zielauswahl mithilfe einer Kombination aus Augen, Stimme und Handeingabe.</span><span class="sxs-lookup"><span data-stu-id="57537-120">**Summary**: Fast and effortless target selections using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-navigation"></a>[<span data-ttu-id="57537-121">**Durch die Augen unterstützte Navigation**</span><span class="sxs-lookup"><span data-stu-id="57537-121">**Eye-Supported Navigation**</span></span>](../input/eye-tracking/eye-tracking-navigation.md)

<span data-ttu-id="57537-122">Imagine, dass Sie einige Informationen auf einer entfernten Anzeige oder ihrem E-Reader lesen und wenn Sie das Ende des angezeigten Texts erreichen, scrollt der Text automatisch nach oben, um weitere Inhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="57537-122">Imagine that you are reading some information on a distant display or your e-reader and when you reach the end of the displayed text, the text automatically scrolls up to reveal more content.</span></span>
<span data-ttu-id="57537-123">Oder wie sieht es mit dem magischen Zoomen direkt an dem Ort aus, an dem Sie sich befanden?</span><span class="sxs-lookup"><span data-stu-id="57537-123">Or how about magically zooming directly toward where you were looking at?</span></span>
<span data-ttu-id="57537-124">Dies sind einige der Beispiele, die in diesem Tutorial zur durch die Augen unterstützten Navigation vorgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="57537-124">These are some of the examples showcased in this tutorial regarding eye-supported navigation.</span></span>
<span data-ttu-id="57537-125">Darüber hinaus gibt es ein Beispiel für die freihändige Drehung von 3D-Hologrammen, indem sie basierend auf Ihrem aktuellen Fokus automatisch gedreht werden.</span><span class="sxs-lookup"><span data-stu-id="57537-125">In addition, there is an example for hands-free rotation of 3D holograms by making them automatically rotate based on your current focus.</span></span>

<span data-ttu-id="57537-126">**Zusammenfassung: Scrollen,** Schwenken, Zoomen, 3D-Drehung mithilfe einer Kombination aus Augen, Stimme und Handeingabe.</span><span class="sxs-lookup"><span data-stu-id="57537-126">**Summary**: Scroll, pan, zoom, 3D rotation using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-positioning"></a>[<span data-ttu-id="57537-127">**Durch die Augen unterstützte Positionierung**</span><span class="sxs-lookup"><span data-stu-id="57537-127">**Eye-Supported Positioning**</span></span>](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

<span data-ttu-id="57537-128">In diesem Tutorial wird ein Eingabeszenario mit dem Namen [Put-That-There](https://youtu.be/CbIn8p4_4CQ) gezeigt, das anfang der 1980er Jahre mit Augen-, Hand- und Spracheingaben auf die Forschung vom MIT Media Lab zurückgeht.</span><span class="sxs-lookup"><span data-stu-id="57537-128">This tutorial shows an input scenario called [Put-That-There](https://youtu.be/CbIn8p4_4CQ) dating back to research from the MIT Media Lab in the early 1980's with eye, hand and voice input.</span></span>
<span data-ttu-id="57537-129">Die Idee ist einfach: Profitieren Sie von Ihren Augen für eine schnelle Zielauswahl und Positionierung.</span><span class="sxs-lookup"><span data-stu-id="57537-129">The idea is simple: Benefit from your eyes for fast target selection and positioning.</span></span>
<span data-ttu-id="57537-130">Sehen Sie sich einfach ein Hologramm an, und sagen _Sie "Put this",_ und sehen Sie sich an, wo Sie es platzieren möchten, und sagen _Sie "There!"._</span><span class="sxs-lookup"><span data-stu-id="57537-130">Simply look at a hologram and say _'put this'_, look over where you want to place it and say _'there!'_.</span></span>
<span data-ttu-id="57537-131">Um Ihr Hologramm genauer zu positionieren, können Sie zusätzliche Eingaben von Den Händen, Stimmen oder Controllern verwenden.</span><span class="sxs-lookup"><span data-stu-id="57537-131">For more precisely positioning your hologram, you can use additional input from your hands, voice or controllers.</span></span>

<span data-ttu-id="57537-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span><span class="sxs-lookup"><span data-stu-id="57537-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span></span> <span data-ttu-id="57537-133">Von den Augen unterstützte Schieberegler mit Augen und Händen.</span><span class="sxs-lookup"><span data-stu-id="57537-133">Eye-supported sliders using eyes + hands.</span></span>

### <a name="visualization-of-visual-attention"></a><span data-ttu-id="57537-134">**Visualisierung der visuellen Aufmerksamkeit**</span><span class="sxs-lookup"><span data-stu-id="57537-134">**Visualization of visual attention**</span></span>

<span data-ttu-id="57537-135">Daten, die auf dem Blick der Benutzer basieren, sind ein äußerst leistungsfähiges Tool, um die Nutzbarkeit eines Entwurfs zu bewerten und Probleme in effizienten Arbeitsströmen zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="57537-135">Data based on where users look makes an immensely powerful tool to assess usability of a design and to identify problems in efficient work streams.</span></span>
<span data-ttu-id="57537-136">In diesem Tutorial werden verschiedene Visualisierungen für die Blickverfolgung erläutert, und es wird erläutert, wie sie unterschiedliche Anforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="57537-136">This tutorial discusses different eye tracking visualizations and how they fit different needs.</span></span>
<span data-ttu-id="57537-137">Wir stellen grundlegende Beispiele für das Protokollieren und Laden von Eyetrackingdaten sowie Beispiele für deren Visualisierung bereit.</span><span class="sxs-lookup"><span data-stu-id="57537-137">We provide basic examples for logging and loading eye tracking data and examples for how to visualize them.</span></span>

<span data-ttu-id="57537-138">**Zusammenfassung:** Karte mit zweidimensionaler Aufmerksamkeit (Wärmebild) auf Schiefern.</span><span class="sxs-lookup"><span data-stu-id="57537-138">**Summary**: Two-dimensional attention map (heatmaps) on slates.</span></span> <span data-ttu-id="57537-139">Aufzeichnen & Wiedergeben von Eyetrackingdaten.</span><span class="sxs-lookup"><span data-stu-id="57537-139">Recording & replaying eye tracking data.</span></span>

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a><span data-ttu-id="57537-140">Einrichten der MRTK-Eyetrackingbeispiele</span><span class="sxs-lookup"><span data-stu-id="57537-140">Setting up the MRTK eye tracking samples</span></span>

### <a name="prerequisites"></a><span data-ttu-id="57537-141">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="57537-141">Prerequisites</span></span>

<span data-ttu-id="57537-142">Beachten Sie, dass für die Verwendung der Eyetrackingbeispiele auf dem Gerät ein HoloLens 2 und ein Beispiel-App-Paket erforderlich sind, das mit der Funktion "Gaze Input" auf dem AppXManifest des Pakets erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="57537-142">Note that using the eye tracking samples on device requires a HoloLens 2 and a sample app package that is built with the "Gaze Input" capability on the package's AppXManifest.</span></span>

<span data-ttu-id="57537-143">Um diese Eyetrackingbeispiele auf dem Gerät zu verwenden, müssen Sie [diese Schritte](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) ausführen, bevor Sie die App in Visual Studio erstellen.</span><span class="sxs-lookup"><span data-stu-id="57537-143">In order to use these eye tracking samples on device, make sure to follow [these steps](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) prior to building the app in Visual Studio.</span></span>

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a><span data-ttu-id="57537-144">1. Laden von EyeTrackingDemo-00-RootScene.unity</span><span class="sxs-lookup"><span data-stu-id="57537-144">1. Load EyeTrackingDemo-00-RootScene.unity</span></span>

<span data-ttu-id="57537-145">*EyeTrackingDemo-00-RootScene* ist die Basisszene _(Root),_ in der alle MRTK-Kernkomponenten enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="57537-145">The *EyeTrackingDemo-00-RootScene* is the base (_root_) scene that has all the core MRTK components included.</span></span>
<span data-ttu-id="57537-146">Dies ist die Szene, die Sie zuerst laden müssen und aus der Sie die Eyetracking-Demos ausführen.</span><span class="sxs-lookup"><span data-stu-id="57537-146">This is the scene that you need to load first and from which you will run the eye tracking demos.</span></span>
<span data-ttu-id="57537-147">Es verfügt über ein grafisches Szenenmenü, mit dem Sie problemlos zwischen den verschiedenen Eyetrackingbeispielen wechseln können, die [additiv geladen](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)werden.</span><span class="sxs-lookup"><span data-stu-id="57537-147">It features a graphical scene menu that allows you to easily switch between the different eye tracking samples which will be [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span></span>

![Szenenmenü im Eyetrackingbeispiel](../images/eye-tracking/mrtk_et_scenemenu.jpg)

<span data-ttu-id="57537-149">Die Stammszene enthält einige Kernkomponenten, die über die additiv geladenen Szenen hinweg beibehalten werden, z. B. die von MRTK konfigurierten Profile und die Szenenkamera.</span><span class="sxs-lookup"><span data-stu-id="57537-149">The root scene includes a few core components that will persist across the additively loaded scenes, such as the MRTK configured profiles and scene camera.</span></span>
<span data-ttu-id="57537-150">_MixedRealityBasicSceneSetup_ (siehe Screenshot unten) enthält ein Skript, das die Referenzszene beim Start automatisch lädt.</span><span class="sxs-lookup"><span data-stu-id="57537-150">The _MixedRealityBasicSceneSetup_ (see screenshot below) includes a script that will automatically load the referenced scene on startup.</span></span>
<span data-ttu-id="57537-151">Standardmäßig ist dies _EyeTrackingDemo-02-TargetSelection_.</span><span class="sxs-lookup"><span data-stu-id="57537-151">By default, this is _EyeTrackingDemo-02-TargetSelection_.</span></span>  

![Beispiel für das OnLoadStartScene-Skript](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a><span data-ttu-id="57537-153">2. Hinzufügen von Szenen zum Buildmenü</span><span class="sxs-lookup"><span data-stu-id="57537-153">2. Adding scenes to the build menu</span></span>

<span data-ttu-id="57537-154">Um additive Szenen während der Laufzeit zu laden, müssen Sie diese Szenen zuerst dem Menü _Build Einstellungen -> Scenes in Build_ hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="57537-154">To load additive scenes during runtime, you must add these scenes to your _Build Settings -> Scenes in Build_ menu first.</span></span>
<span data-ttu-id="57537-155">Es ist wichtig, dass die Stammszene als erste Szene in der Liste angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="57537-155">It is important that the root scene is shown as the first scene in the list:</span></span>

![Erstellen Einstellungen Szenenmenüs für Eyetrackingbeispiele](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a><span data-ttu-id="57537-157">3. Wiedergeben der Eyetrackingbeispiele im Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="57537-157">3. Play the eye tracking samples in the Unity editor</span></span>

<span data-ttu-id="57537-158">Nachdem Sie dem Build Einstellungen die Blickverfolgungsszenen hinzugefügt und das _EyeTrackingDemo-00-RootScene_ geladen haben, sollten Sie als Letztes überprüfen: Ist das Skript _"OnLoadStartScene"_ aktiviert, das an _das MixedRealityBasicSceneSetup_ GameObject angefügt ist?</span><span class="sxs-lookup"><span data-stu-id="57537-158">After adding the eye tracking scenes to the Build Settings and loading the _EyeTrackingDemo-00-RootScene_, there is one last thing you may want to check: Is the _'OnLoadStartScene'_ script that is attached to the _MixedRealityBasicSceneSetup_ GameObject enabled?</span></span> <span data-ttu-id="57537-159">Dies soll der Stammszene mitteilen, welche Demoszene zuerst geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="57537-159">This is to let the root scene know which demo scene to load first.</span></span>

![Beispiel für das OnLoad_StartScene-Skript](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

<span data-ttu-id="57537-161">Jetzt geht es los!</span><span class="sxs-lookup"><span data-stu-id="57537-161">Let's roll!</span></span> <span data-ttu-id="57537-162">Klicken Sie auf _"Play"_!</span><span class="sxs-lookup"><span data-stu-id="57537-162">Hit _"Play"_!</span></span>
<span data-ttu-id="57537-163">Es sollten mehrere Gems und das Szenenmenü oben angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="57537-163">You should see several gems appear and the scene menu at the top.</span></span>

![Beispielscreenshot der Et-Zielauswahl-Szene](../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="57537-165">Sie sollten auch einen kleinen halbtransparenten Kreis in der Mitte Ihrer Spielansicht bemerken.</span><span class="sxs-lookup"><span data-stu-id="57537-165">You should also notice a small semitransparent circle at the center of your game view.</span></span>
<span data-ttu-id="57537-166">Dies fungiert als Indikator (Cursor) des _simulierten Anvierens_ der Augen: Drücken Sie einfach die _rechte Maustaste_ nach unten, und bewegen Sie die Maus, um ihre Position zu ändern.</span><span class="sxs-lookup"><span data-stu-id="57537-166">This acts as an indicator (cursor) of your _simulated eye gaze_: Simply press down the _right mouse button_ and move the mouse to change its position.</span></span>
<span data-ttu-id="57537-167">Wenn der Cursor auf die Gems zeigen, werden Sie feststellen, dass er an der Mitte des aktuell angezeigten Gems ausgerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="57537-167">When the cursor is hovering over the gems, you will notice that it will snap to the center of the currently viewed gem.</span></span>
<span data-ttu-id="57537-168">Dies ist eine hervorragende Möglichkeit, um zu testen, ob Ereignisse wie erwartet ausgelöst werden, wenn ein Ziel _"betrachtet"_ wird.</span><span class="sxs-lookup"><span data-stu-id="57537-168">This is a great way to test if events are triggered as expected when _"looking"_ at a target.</span></span>
<span data-ttu-id="57537-169">Beachten Sie, dass das _simulierte Anvisierten_ der Augen über das Maussteuerelement eine eher schlechte Ergänzung unserer schnellen und unbeabsichtigten Augenbewegungen ist.</span><span class="sxs-lookup"><span data-stu-id="57537-169">Be aware that the _simulated eye gaze_ via mouse control is a rather poor supplement to our rapid and unintentional eye movements.</span></span>
<span data-ttu-id="57537-170">Sie eignet sich jedoch hervorragend zum Testen der grundlegenden Funktionalität, bevor Sie den Entwurf durch Bereitstellung auf dem HoloLens 2 Gerät iterieren.</span><span class="sxs-lookup"><span data-stu-id="57537-170">However, it is great for testing the basic functionality before iterating on the design by deploying it to the HoloLens 2 device.</span></span>
<span data-ttu-id="57537-171">Zurück zur Blickverfolgungs-Beispielszene: Das Gem wird gedreht, solange es betrachtet wird und zerstört werden kann, indem es sich ansieht und ...</span><span class="sxs-lookup"><span data-stu-id="57537-171">Returning to our eye tracking sample scene: The gem rotates as long as being looked at and can be destroyed by "looking" at it and ...</span></span>

- <span data-ttu-id="57537-172">Drücken _der EINGABETASTE_ (wodurch "Select" simuliert wird)</span><span class="sxs-lookup"><span data-stu-id="57537-172">Pressing _Enter_ (which simulates saying "select")</span></span>
- <span data-ttu-id="57537-173">_"Auswählen"_ ins Mikrofon</span><span class="sxs-lookup"><span data-stu-id="57537-173">Saying _"select"_ into your microphone</span></span>
- <span data-ttu-id="57537-174">Klicken Sie beim Drücken von _Leertaste_ zum Anzeigen der simulierten Handeingabe auf die linke Maustaste, um eine simulierte Zusammendrückung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="57537-174">While pressing _Space_ to show the simulated hand input, click the left mouse button to perform a simulated pinch</span></span>

<span data-ttu-id="57537-175">In unserem Tutorial [**Eye-Supported Target Selection (Eye-Supported Target Selection)**](../input/eye-tracking/eye-tracking-target-selection.md) wird ausführlicher beschrieben, wie Sie diese Interaktionen erreichen können.</span><span class="sxs-lookup"><span data-stu-id="57537-175">We describe in more detail how you can achieve these interactions in our [**Eye-Supported Target Selection**](../input/eye-tracking/eye-tracking-target-selection.md) tutorial.</span></span>

<span data-ttu-id="57537-176">Wenn Sie den Cursor auf die obere Menüleiste in der Szene bewegen, werden Sie feststellen, dass das aktuell gezeigte Element subtly hervorgehoben wird.</span><span class="sxs-lookup"><span data-stu-id="57537-176">When moving the cursor up to the top menu bar in the scene, you will notice that the currently hovered item will highlight subtly.</span></span>
<span data-ttu-id="57537-177">Sie können das aktuell hervorgehobene Element auswählen, indem Sie eine der oben beschriebenen Commitmethoden verwenden (z. B. drücken Sie die _EINGABETASTE)._</span><span class="sxs-lookup"><span data-stu-id="57537-177">You can select the currently highlighted item by using one of the above described commit methods (e.g., pressing _Enter_).</span></span>
<span data-ttu-id="57537-178">Auf diese Weise können Sie zwischen den verschiedenen Eyetracking-Beispielszenen wechseln.</span><span class="sxs-lookup"><span data-stu-id="57537-178">This way you can switch between the different eye tracking sample scenes.</span></span>

### <a name="4-how-to-test-specific-sub-scenes"></a><span data-ttu-id="57537-179">4. Testen bestimmter Teilszenen</span><span class="sxs-lookup"><span data-stu-id="57537-179">4. How to test specific sub scenes</span></span>

<span data-ttu-id="57537-180">Wenn Sie an einem bestimmten Szenario arbeiten, möchten Sie das Szenenmenü möglicherweise nicht jedes Mal durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="57537-180">When working on a specific scenario, you may not want to go through the scene menu every time.</span></span>
<span data-ttu-id="57537-181">Stattdessen sollten Sie direkt von der Szene aus beginnen, an der Sie gerade arbeiten, wenn Sie auf die Schaltfläche _Wiedergabe_ klicken.</span><span class="sxs-lookup"><span data-stu-id="57537-181">Instead, you may want to start directly from the scene that you are currently working on when pressing the _Play_ button.</span></span>
<span data-ttu-id="57537-182">Kein Problem.</span><span class="sxs-lookup"><span data-stu-id="57537-182">No problem!</span></span> <span data-ttu-id="57537-183">Folgendes können Sie tun:</span><span class="sxs-lookup"><span data-stu-id="57537-183">Here is what you can do:</span></span>

1. <span data-ttu-id="57537-184">Laden der _Stammszene_</span><span class="sxs-lookup"><span data-stu-id="57537-184">Load the _root_ scene</span></span>
2. <span data-ttu-id="57537-185">Deaktivieren Sie in der _Stammszene_ das Skript _"OnLoadStartScene"._</span><span class="sxs-lookup"><span data-stu-id="57537-185">In the _root_ scene, disable the _'OnLoadStartScene'_ script</span></span>
3. <span data-ttu-id="57537-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span><span class="sxs-lookup"><span data-stu-id="57537-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span></span>

    ![Beispiel für additive Szene](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. <span data-ttu-id="57537-188">Klicken Sie auf _Wiedergabe._</span><span class="sxs-lookup"><span data-stu-id="57537-188">Press _Play_</span></span>

<span data-ttu-id="57537-189">Beachten Sie, dass das Laden der untergeordneten Szene wie folgt nicht persistent ist: Wenn Sie Ihre App auf dem HoloLens 2 Gerät bereitstellen, wird nur die Stammszene geladen (vorausgesetzt, sie wird oben im Build Einstellungen angezeigt).</span><span class="sxs-lookup"><span data-stu-id="57537-189">Please note that loading the sub scene like this is not persistent: This means that if you deploy your app to the HoloLens 2 device, it will only load the root scene (assuming it appears at the top of your Build Settings).</span></span>
<span data-ttu-id="57537-190">Wenn Sie Ihr Projekt für andere freigeben, werden die Untergeordneten Szenen nicht automatisch geladen.</span><span class="sxs-lookup"><span data-stu-id="57537-190">Also, when you share your project with others, the sub scenes are not automatically loaded.</span></span>

---

<span data-ttu-id="57537-191">Nachdem Sie nun wissen, wie Sie die MRTK-Eyetracking-Beispielszenen umsetzen können, fahren wir mit dem Tiefergehen der Auswahl von Hologrammen mit Ihren Augen fort: [Eye-supported target selection](../input/eye-tracking/eye-tracking-target-selection.md).</span><span class="sxs-lookup"><span data-stu-id="57537-191">Now that you know how to get the MRTK eye tracking example scenes to work, let's continue with diving deeper into how to select holograms with your eyes: [Eye-supported target selection](../input/eye-tracking/eye-tracking-target-selection.md).</span></span>

---
[<span data-ttu-id="57537-192">Zurück zu "Eye tracking in the MixedRealityToolkit" (Blickverfolgung im MixedRealityToolkit)</span><span class="sxs-lookup"><span data-stu-id="57537-192">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](../input/eye-tracking/eye-tracking-Main.md)
