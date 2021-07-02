---
title: Eingabesimulationsdienst
description: Dokumentation zum Eingabesimulationsdienst in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 66b79c14bbd0ea8c188aba684b9bd1034de31bf9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176959"
---
# <a name="input-simulation-service"></a><span data-ttu-id="877fc-104">Eingabesimulationsdienst</span><span class="sxs-lookup"><span data-stu-id="877fc-104">Input simulation service</span></span>

![MRTK-Eingabesimulation](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

<span data-ttu-id="877fc-106">Mit der MrTK-Eingabesimulation können Sie verschiedene Arten von Interaktionen im Unity-Editor testen, ohne ein Gerät erstellen und bereitstellen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="877fc-106">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="877fc-107">Auf diese Weise können Sie Ihre Ideen im Entwurfs- und Entwicklungsprozess schnell iterieren.</span><span class="sxs-lookup"><span data-stu-id="877fc-107">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="877fc-108">Verwenden Sie Tastenkombinationen und Mauskombinationen, um simulierte Eingaben zu steuern.</span><span class="sxs-lookup"><span data-stu-id="877fc-108">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="877fc-109">Der Eingabesimulationsdienst emuliert das Verhalten von Geräten und Plattformen, die möglicherweise nicht im Unity-Editor verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="877fc-109">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="877fc-110">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="877fc-110">Examples include:</span></span>

* <span data-ttu-id="877fc-111">HoloLens oder VR-Gerätekopfverfolgung</span><span class="sxs-lookup"><span data-stu-id="877fc-111">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="877fc-112">HoloLens Handgesten</span><span class="sxs-lookup"><span data-stu-id="877fc-112">HoloLens hand gestures</span></span>
* <span data-ttu-id="877fc-113">HoloLens 2 artikulierte Handverfolgung</span><span class="sxs-lookup"><span data-stu-id="877fc-113">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="877fc-114">HoloLens 2 Eyetracking</span><span class="sxs-lookup"><span data-stu-id="877fc-114">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="877fc-115">VR-Gerätecontroller</span><span class="sxs-lookup"><span data-stu-id="877fc-115">VR device controllers</span></span>

> [!WARNING]
> <span data-ttu-id="877fc-116">Dies funktioniert nicht, wenn die XR Holographic Emulation von Unity > Emulationsmodus = "Simulate in Editor" (Im Editor simulieren) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="877fc-116">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="877fc-117">Die In-Editor-Simulation von Unity wird die Kontrolle über die Eingabesimulation des MRTK übernehmen.</span><span class="sxs-lookup"><span data-stu-id="877fc-117">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="877fc-118">Um den MRTK-Eingabesimulationsdienst verwenden zu können, müssen Sie XR Holographic Emulation auf Emulation Mode = *"None" (Keine) festlegen.*</span><span class="sxs-lookup"><span data-stu-id="877fc-118">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="how-to-use-mrtk-input-simulation"></a><span data-ttu-id="877fc-119">Verwenden der MRTK-Eingabesimulation</span><span class="sxs-lookup"><span data-stu-id="877fc-119">How to use MRTK Input simulation</span></span> 

<span data-ttu-id="877fc-120">Die Eingabesimulation ist in den Profilen, die im MRTK-Versand sind, standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="877fc-120">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span> <span data-ttu-id="877fc-121">Sie können einfach auf die **Schaltfläche Wiedergabe** klicken, um die Szene mit Eingabesimulationsunterstützung ausführen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="877fc-121">You can simply click **Play** button to run the scene with input simulation support.</span></span>

* <span data-ttu-id="877fc-122">Drücken **Sie die Tasten W, A, S, D, Q, E,** um die Kamera zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="877fc-122">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="877fc-123">Halten Sie die **rechte Maustaste gedrückt,** und bewegen Sie die Maus, um nach ihnen zu suchen.</span><span class="sxs-lookup"><span data-stu-id="877fc-123">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="877fc-124">Drücken Sie zum Aufbringen der simulierten Hände die **TASTENTASTE (rechts)** oder NACH-LINKS-TASTE **(Linke Hand).**</span><span class="sxs-lookup"><span data-stu-id="877fc-124">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="877fc-125">Drücken Sie T oder **Y,** um simulierte Hände in der Ansicht zu halten. </span><span class="sxs-lookup"><span data-stu-id="877fc-125">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="877fc-126">Halten Sie zum Drehen simulierter Hände die **STRG-TASTE** gedrückt, und bewegen Sie die Maus.</span><span class="sxs-lookup"><span data-stu-id="877fc-126">To rotate simulated hands, press and hold **Ctrl key** and move mouse</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="877fc-127">Cheat Sheet zur Eingabesimulation im Editor</span><span class="sxs-lookup"><span data-stu-id="877fc-127">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="877fc-128">Drücken Sie in der HandInteractionExamples-Szene nach links **STRG+H,** um ein Cheat Sheet mit Eingabesimulationssteuerelementen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="877fc-128">Press **Left Ctrl + H** in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

> ![MRTK Input Simulation Cheat Sheet](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="877fc-130">Aktivieren des Eingabesimulationsdiensts</span><span class="sxs-lookup"><span data-stu-id="877fc-130">Enabling the input simulation service</span></span>

<span data-ttu-id="877fc-131">Unter der Konfiguration des Eingabesystemdatenanbieters kann der Eingabesimulationsdienst wie folgt konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-131">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="877fc-132">**Typ** muss *Microsoft.MixedReality.Toolkit.Input > InputSimulationService sein.*</span><span class="sxs-lookup"><span data-stu-id="877fc-132">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="877fc-133">**Unterstützte Plattformen umfassen standardmäßig** alle *Editor-Plattformen,* da der Dienst Tastatur- und Mauseingaben verwendet.</span><span class="sxs-lookup"><span data-stu-id="877fc-133">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="877fc-134">Der Eingabesimulationsdienst kann auf anderen Plattformendpunkten verwendet werden, z. B. eigenständig, indem die Eigenschaft Unterstützte **Plattform(en)** geändert wird, um die gewünschten Ziele ein- und einaufnahme.</span><span class="sxs-lookup"><span data-stu-id="877fc-134">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a><span data-ttu-id="877fc-135">Kamerasteuerung</span><span class="sxs-lookup"><span data-stu-id="877fc-135">Camera control</span></span>

<span data-ttu-id="877fc-136">Die Kopfbewegung kann vom Eingabesimulationsdienst emuliert werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-136">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="877fc-137">Drehen der Kamera</span><span class="sxs-lookup"><span data-stu-id="877fc-137">Rotating the camera</span></span>

1. <span data-ttu-id="877fc-138">Zeigen Sie auf das Viewport-Editor-Fenster.</span><span class="sxs-lookup"><span data-stu-id="877fc-138">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="877fc-139">*Möglicherweise müssen Sie auf das Fenster klicken, um ihm den Eingabefokus zu geben, wenn Tastendruck nicht funktioniert.*</span><span class="sxs-lookup"><span data-stu-id="877fc-139">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="877fc-140">Halten Sie die **Maustaste gedrückt** (Standard: Rechte Maustaste).</span><span class="sxs-lookup"><span data-stu-id="877fc-140">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="877fc-141">Bewegen Sie die Maus im Viewportfenster, um die Kamera zu drehen.</span><span class="sxs-lookup"><span data-stu-id="877fc-141">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="877fc-142">Verwenden Sie das Scrollrad, um die Kamera um die Ansichtsrichtung zu drehen.</span><span class="sxs-lookup"><span data-stu-id="877fc-142">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="877fc-143">Die Kameradrehgeschwindigkeit kann durch Ändern der **Einstellung Mouse Look Speed** im Eingabesimulationsprofil konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-143">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="877fc-144">Alternativ können Sie die Vertikale **Look Horizontal** Look-Achsen verwenden, um die Kamera zu drehen /  (Standard: game controller right thumbstick).</span><span class="sxs-lookup"><span data-stu-id="877fc-144">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="877fc-145">Bewegen der Kamera</span><span class="sxs-lookup"><span data-stu-id="877fc-145">Moving the camera</span></span>

<span data-ttu-id="877fc-146">Verwenden Sie **die Achsen "Horizontale** Bewegung vertikal verschieben", um die Kamera zu verschieben /  (Standardeinstellung: WASD-Tasten oder game controller left thumbstick).</span><span class="sxs-lookup"><span data-stu-id="877fc-146">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="877fc-147">Kameraposition und Drehwinkel können auch explizit im Toolsfenster festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-147">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="877fc-148">Die Kamera kann mithilfe der Schaltfläche Zurücksetzen auf den **Standardwert zurückgesetzt** werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-148">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="877fc-149">Controllersimulation</span><span class="sxs-lookup"><span data-stu-id="877fc-149">Controller simulation</span></span>

<span data-ttu-id="877fc-150">Die Eingabesimulation unterstützt emulierte Controllergeräte (d. h. Motion Controller und Hände).</span><span class="sxs-lookup"><span data-stu-id="877fc-150">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="877fc-151">Diese virtuellen Controller können mit jedem Objekt interagieren, das reguläre Controller unterstützt, z. B. Schaltflächen oder greifbare Objekte.</span><span class="sxs-lookup"><span data-stu-id="877fc-151">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="877fc-152">Controllersimulationsmodus</span><span class="sxs-lookup"><span data-stu-id="877fc-152">Controller simulation mode</span></span>

<span data-ttu-id="877fc-153">Im Fenster [der Eingabesimulationstools](#input-simulation-tools-window) wechselt **die Einstellung Standardcontrollersimulationsmodus** zwischen drei unterschiedlichen Eingabemodellen.</span><span class="sxs-lookup"><span data-stu-id="877fc-153">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="877fc-154">Dieser Standardmodus kann auch im Eingabesimulationsprofil festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-154">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="877fc-155">*Artikulierte Hände:* Simuliert ein vollständig artikuliertes Handgerät mit Gemeinsamen Positionsdaten.</span><span class="sxs-lookup"><span data-stu-id="877fc-155">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="877fc-156">Emuliert HoloLens 2 Interaktionsmodell.</span><span class="sxs-lookup"><span data-stu-id="877fc-156">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="877fc-157">Interaktionen, die auf der präzisen Positionierung der Hand oder der Verwendung von Touching basieren, können in diesem Modus simuliert werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-157">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="877fc-158">*Handgesten:* Simuliert ein vereinfachtes Handmodell mit Tippbewegungen in die Luft und grundlegenden Gesten.</span><span class="sxs-lookup"><span data-stu-id="877fc-158">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="877fc-159">Emuliert [HoloLens Interaktionsmodell.](/windows/mixed-reality/gestures)</span><span class="sxs-lookup"><span data-stu-id="877fc-159">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="877fc-160">Der Fokus wird mithilfe des Anvingzeigers gesteuert.</span><span class="sxs-lookup"><span data-stu-id="877fc-160">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="877fc-161">Die *Geste Tippen* in die Luft wird für die Interaktion mit Schaltflächen verwendet.</span><span class="sxs-lookup"><span data-stu-id="877fc-161">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="877fc-162">*Motion Controller*: Simuliert einen Motion Controller, der mit VR-Headsets verwendet wird und ähnlich wie bei fernen Interaktionen mit Artikulierten Händen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="877fc-162">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="877fc-163">Emuliert das VR-Headset mit dem Controllerinteraktionsmodell.</span><span class="sxs-lookup"><span data-stu-id="877fc-163">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="877fc-164">Trigger, Greif- und Menütasten werden per Tastatur- und Mauseingabe simuliert.</span><span class="sxs-lookup"><span data-stu-id="877fc-164">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="877fc-165">Simulieren der Controllerbewegung</span><span class="sxs-lookup"><span data-stu-id="877fc-165">Simulating controller movement</span></span>

<span data-ttu-id="877fc-166">Drücken und halten Sie die Taste für  die Controllerbearbeitung nach **links/rechts** (Standard: Linke UMSCHALTTASTE für den linken Controller und *Leerzeichen* für den rechten Controller), um die Kontrolle über beide Controller zu erlangen.</span><span class="sxs-lookup"><span data-stu-id="877fc-166">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="877fc-167">Während die Manipulationstaste gedrückt wird, wird der Controller im Viewport angezeigt.</span><span class="sxs-lookup"><span data-stu-id="877fc-167">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="877fc-168">Nachdem der Manipulationsschlüssel freigegeben wurde, werden die Controller nach einem kurzen **Timeout für das Ausblenden des Controllers nicht mehr verwendet.**</span><span class="sxs-lookup"><span data-stu-id="877fc-168">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="877fc-169">Controller können ein- und fixiert werden, relativ [](#input-simulation-tools-window) zur Kamera im Fenster der Eingabesimulationstools oder durch Drücken der Umschalttaste **links/rechts** (Standard: *T* für links und *Y* für rechts).</span><span class="sxs-lookup"><span data-stu-id="877fc-169">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="877fc-170">Drücken Sie erneut die Umschalttaste, um die Controller erneut auszublenden.</span><span class="sxs-lookup"><span data-stu-id="877fc-170">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="877fc-171">Um die Controller zu bearbeiten, muss **der Linke/rechte Controllermanipulationsschlüssel** gehalten werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-171">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="877fc-172">Wenn Sie auf den **Bearbeitungsschlüssel für den linken/rechten Controller** tippen, können Sie die Controller auch ein-/ausschalten.</span><span class="sxs-lookup"><span data-stu-id="877fc-172">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="877fc-173">Die Mausbewegung bewegt den Controller in der Ansichtsebene.</span><span class="sxs-lookup"><span data-stu-id="877fc-173">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="877fc-174">Controller können mit dem Mausrad weiter oder näher zur **Kamera bewegt werden.**</span><span class="sxs-lookup"><span data-stu-id="877fc-174">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="877fc-175">Halten Sie zum Drehen von Controllern mit der Maus sowohl die  **Linke/Rechte** Taste zum Ändern des Controllers *(* Linke UMSCHALTTASTE oder Leerzeichen *)* als auch die **Schaltfläche** Controller rotieren (Standard:  Linke STRG-Taste) gedrückt, und bewegen Sie dann die Maus, um den Controller zu drehen.</span><span class="sxs-lookup"><span data-stu-id="877fc-175">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="877fc-176">Die Geschwindigkeit der Controllerrotation kann durch Ändern der **Einstellung Drehgeschwindigkeit** des Mauscontrollers im Eingabesimulationsprofil konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-176">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="877fc-177">Alle Handplatzierungen können auch im Fenster der [Eingabesimulationstools](#input-simulation-tools-window)geändert werden, einschließlich des Zurücksetzens der Hände auf den Standardwert.</span><span class="sxs-lookup"><span data-stu-id="877fc-177">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="877fc-178">Zusätzliche Profileinstellungen</span><span class="sxs-lookup"><span data-stu-id="877fc-178">Additional profile settings</span></span>

* <span data-ttu-id="877fc-179">**Der Controller-Tiefenmultiplikator** steuert die Empfindlichkeit der Tiefenbewegung des Mausscrollrads.</span><span class="sxs-lookup"><span data-stu-id="877fc-179">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="877fc-180">Eine größere Zahl beschleunigt den Controllerzoom.</span><span class="sxs-lookup"><span data-stu-id="877fc-180">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="877fc-181">**Standardcontrollerabstand** ist der anfängliche Abstand der Controller von der Kamera.</span><span class="sxs-lookup"><span data-stu-id="877fc-181">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="877fc-182">Wenn Sie auf die **Schaltfläche Zurücksetzen** klicken, platzieren Sie controller ebenfalls in dieser Entfernung.</span><span class="sxs-lookup"><span data-stu-id="877fc-182">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="877fc-183">**Controller Jitter Amount fügt** Controllern zufällige Bewegungen hinzu.</span><span class="sxs-lookup"><span data-stu-id="877fc-183">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="877fc-184">Dieses Feature kann verwendet werden, um ungenaue Controllernachverfolgung auf dem Gerät zu simulieren und sicherzustellen, dass Interaktionen mit lauten Eingaben gut funktionieren.</span><span class="sxs-lookup"><span data-stu-id="877fc-184">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="877fc-185">Handgesten</span><span class="sxs-lookup"><span data-stu-id="877fc-185">Hand gestures</span></span>

<span data-ttu-id="877fc-186">Handgesten wie Zusammendring, Greifen, Poking usw. können ebenfalls simuliert werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-186">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="877fc-187">Aktivieren der Handsteuerung mithilfe **des Links-/Rechtscontroller-Manipulationsschlüssels** (*Linke Umschalttaste* oder *Leerzeichen*)</span><span class="sxs-lookup"><span data-stu-id="877fc-187">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="877fc-188">Halten Sie beim Bearbeiten eine Maustaste gedrückt, um eine Handbewegung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="877fc-188">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="877fc-189">Jede der Maustasten kann zugeordnet werden, um die Handform in eine andere Geste zu transformieren, indem die Einstellungen *linke/mittlere/rechte Mausbewegung verwendet* werden.</span><span class="sxs-lookup"><span data-stu-id="877fc-189">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="877fc-190">Die *Standardhandgeste* ist die Form der Hand, wenn keine Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="877fc-190">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="877fc-191">Die *Pinch-Geste* ist die einzige Geste, die an dieser Stelle die Aktion "Auswählen" ausführt.</span><span class="sxs-lookup"><span data-stu-id="877fc-191">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="877fc-192">One-Hand-Manipulation</span><span class="sxs-lookup"><span data-stu-id="877fc-192">One-hand manipulation</span></span>

1. <span data-ttu-id="877fc-193">Drücken und halten Sie die Taste für die Controllerbearbeitung nach **links/rechts** (*Linke Umschalttaste* oder *Leerzeichen*)</span><span class="sxs-lookup"><span data-stu-id="877fc-193">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="877fc-194">Punkt auf Objekt</span><span class="sxs-lookup"><span data-stu-id="877fc-194">Point at object</span></span>
3. <span data-ttu-id="877fc-195">Halten Sie die Maustaste gedrückt, um sie zu halten.</span><span class="sxs-lookup"><span data-stu-id="877fc-195">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="877fc-196">Verwenden der Maus zum Verschieben des Objekts</span><span class="sxs-lookup"><span data-stu-id="877fc-196">Use your mouse to move the object</span></span>
5. <span data-ttu-id="877fc-197">Lassen Sie die Maustaste los, um die Interaktion zu beenden.</span><span class="sxs-lookup"><span data-stu-id="877fc-197">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="877fc-198">Zweihandmanipulation</span><span class="sxs-lookup"><span data-stu-id="877fc-198">Two-hand manipulation</span></span>

<span data-ttu-id="877fc-199">Für die gleichzeitige Bearbeitung von Objekten mit zwei Händen wird der persistente Handmodus empfohlen.</span><span class="sxs-lookup"><span data-stu-id="877fc-199">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="877fc-200">Umschalten an beiden Händen durch Drücken der Umschalttasten (*T/Y*).</span><span class="sxs-lookup"><span data-stu-id="877fc-200">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="877fc-201">Bearbeiten Sie eine Hand nach der anderen:</span><span class="sxs-lookup"><span data-stu-id="877fc-201">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="877fc-202">Halten **Sie den Platz,** um die rechte Hand zu steuern.</span><span class="sxs-lookup"><span data-stu-id="877fc-202">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="877fc-203">Bewegen Sie die Hand an den Ort, an dem Sie das Objekt greifen möchten.</span><span class="sxs-lookup"><span data-stu-id="877fc-203">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="877fc-204">Drücken Sie die **linke Maustaste,** um die Stiftbewegung *zu* aktivieren.</span><span class="sxs-lookup"><span data-stu-id="877fc-204">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="877fc-205">**Freigabebereich,** um die Steuerung der rechten Hand zu beenden.</span><span class="sxs-lookup"><span data-stu-id="877fc-205">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="877fc-206">Die Hand wird an Ort und Stelle fixiert und an der *Pinch-Geste* gesperrt, da sie nicht mehr bearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="877fc-206">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="877fc-207">Wiederholen Sie den Vorgang mit der anderen Hand, und greifen Sie dasselbe Objekt an einer zweiten Stelle.</span><span class="sxs-lookup"><span data-stu-id="877fc-207">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="877fc-208">Da nun beide Hände dasselbe Objekt greifen, können Sie beide bewegen, um eine zweihändige Bearbeitung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="877fc-208">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="877fc-209">GGV-Interaktion (Anving, Geste und Stimme)</span><span class="sxs-lookup"><span data-stu-id="877fc-209">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="877fc-210">Standardmäßig ist die GGV-Interaktion im Editor aktiviert, während in der Szene keine artikulierten Hände vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="877fc-210">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="877fc-211">Drehen der Kamera, um den Anvitätscursor auf das interaktionsfähige Objekt zu zeigen (rechte Maustaste)</span><span class="sxs-lookup"><span data-stu-id="877fc-211">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="877fc-212">Klicken und halten Sie **die linke Maustaste gedrückt, um** zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="877fc-212">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="877fc-213">Drehen Sie die Kamera erneut, um das Objekt zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="877fc-213">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="877fc-214">Sie können dies deaktivieren, indem Sie die Option *Is Hand Free Input Enabled* im Eingabesimulationsprofil umschalten.</span><span class="sxs-lookup"><span data-stu-id="877fc-214">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="877fc-215">Darüber hinaus können Sie simulierte Hände für die GGV-Interaktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="877fc-215">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="877fc-216">Aktivieren der GGV-Simulation durch Wechseln **des Handsimulationsmodus** zu Gesten im [Eingabesimulationsprofil](#enabling-the-input-simulation-service) </span><span class="sxs-lookup"><span data-stu-id="877fc-216">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="877fc-217">Drehen der Kamera, um den Anvitätscursor auf das interaktionsfähige Objekt zu zeigen (rechte Maustaste)</span><span class="sxs-lookup"><span data-stu-id="877fc-217">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="877fc-218">Halten **Sie den Platz,** um die rechte Hand zu steuern.</span><span class="sxs-lookup"><span data-stu-id="877fc-218">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="877fc-219">Klicken und halten Sie **die linke Maustaste gedrückt, um** zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="877fc-219">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="877fc-220">Verwenden der Maus zum Verschieben des Objekts</span><span class="sxs-lookup"><span data-stu-id="877fc-220">Use your mouse to move the object</span></span>
1. <span data-ttu-id="877fc-221">Lassen Sie die Maustaste los, um die Interaktion zu beenden.</span><span class="sxs-lookup"><span data-stu-id="877fc-221">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="877fc-222">Ausreihen von Teleportereignissen</span><span class="sxs-lookup"><span data-stu-id="877fc-222">Raising Teleport Events</span></span>

<span data-ttu-id="877fc-223">Um das Teleportereignis in der Eingabesimulation zu starten, konfigurieren Sie die Handgeste Einstellungen im Eingabesimulationsprofil so, dass eine die **Teleport-Startgeste** ausführt, während die andere die **Teleport-Endgeste** ausführt.</span><span class="sxs-lookup"><span data-stu-id="877fc-223">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="877fc-224">Mit **der Teleport-Startgeste** wird der Teleport-Zeiger angezeigt, während die Teleport-End-Benutzeroberfläche die **Teleportaktion** abarbeite und den Benutzer bewegt.</span><span class="sxs-lookup"><span data-stu-id="877fc-224">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="877fc-225">Die y-Position des resultierenden Teleports hängt von der Verschiebung der Kamera entlang der y-Achse ab.</span><span class="sxs-lookup"><span data-stu-id="877fc-225">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="877fc-226">Im Editor ist dies standardmäßig 0. Verwenden Sie daher die **Q-** und **E-Tasten,** um sie an die entsprechende Höhe anzupassen.</span><span class="sxs-lookup"><span data-stu-id="877fc-226">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![Teleport-Einstellungen](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="877fc-228">Interaktion des Bewegungscontrollers</span><span class="sxs-lookup"><span data-stu-id="877fc-228">Motion controller interaction</span></span>

<span data-ttu-id="877fc-229">Die simulierten Bewegungscontroller können auf die gleiche Weise bearbeitet werden wie artikulierte Hände.</span><span class="sxs-lookup"><span data-stu-id="877fc-229">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="877fc-230">Das Interaktionsmodell ähnelt der fernen Interaktion der artikulierten Hand, während der Trigger, die Greiftaste und die Menütaste der linken *Maustaste,* *der G-* bzw. *M-Taste* zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="877fc-230">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="877fc-231">Eyetracking – Blickverfolgung</span><span class="sxs-lookup"><span data-stu-id="877fc-231">Eye tracking</span></span>

<span data-ttu-id="877fc-232">[Die Eyetrackingsimulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) kann aktiviert werden, indem die **Option Augenposition** simulieren im [Eingabesimulationsprofil aktiviert wird.](#enabling-the-input-simulation-service)</span><span class="sxs-lookup"><span data-stu-id="877fc-232">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="877fc-233">Dies sollte nicht mit GGV- oder Motion Controller-Stilinteraktionen verwendet werden (stellen Sie daher sicher, dass **Standardcontrollersimulationsmodus** auf *Artikulierte Hand festgelegt ist).*</span><span class="sxs-lookup"><span data-stu-id="877fc-233">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="877fc-234">Fenster "Eingabesimulationstools"</span><span class="sxs-lookup"><span data-stu-id="877fc-234">Input simulation tools window</span></span>

<span data-ttu-id="877fc-235">Aktivieren Sie das Fenster eingabesimulationstools über das **Menü Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Input Simulation (Eingabesimulation für Toolkit-Hilfsprogramme).**</span><span class="sxs-lookup"><span data-stu-id="877fc-235">Enable the input simulation tools window from the  **Mixed Reality** > **Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="877fc-236">Dieses Fenster ermöglicht den Zugriff auf den Zustand der Eingabesimulation im Wiedergabemodus.</span><span class="sxs-lookup"><span data-stu-id="877fc-236">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons-optional"></a><span data-ttu-id="877fc-237">Viewportschaltflächen (optional)</span><span class="sxs-lookup"><span data-stu-id="877fc-237">Viewport buttons (optional)</span></span>

<span data-ttu-id="877fc-238">Ein Prefab für Schaltflächen im Editor zum Steuern der grundlegenden Handplatzierung kann im Eingabesimulationsprofil unter **Indicators Prefab angegeben werden.**</span><span class="sxs-lookup"><span data-stu-id="877fc-238">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="877fc-239">Dies ist ein optionales Hilfsprogramm. Auf die gleichen Features kann im Eingabesimulationstools-Fenster [zugegriffen werden.](#input-simulation-tools-window)</span><span class="sxs-lookup"><span data-stu-id="877fc-239">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="877fc-240">Die Viewportindikatoren sind standardmäßig deaktiviert, da sie derzeit manchmal Interaktionen der Unity-Benutzeroberfläche beeinträchtigen können.</span><span class="sxs-lookup"><span data-stu-id="877fc-240">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="877fc-241">Siehe Problem [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span><span class="sxs-lookup"><span data-stu-id="877fc-241">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="877fc-242">Fügen Sie zum Aktivieren das Prefab InputSimulationIndicators zu **Indicators Prefab hinzu.**</span><span class="sxs-lookup"><span data-stu-id="877fc-242">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="877fc-243">Handsymbole zeigen den Zustand der simulierten Hände an:</span><span class="sxs-lookup"><span data-stu-id="877fc-243">Hand icons show the state of the simulated hands:</span></span>

* ![Symbol "Nicht vertrackte Hand"](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="877fc-245&quot;>Die Hand wird nicht nachverfolgt.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;877fc-245&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;877fc-246&quot;>Klicken Sie auf diese Schaltfläche, um die Hand zu aktivieren.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;877fc-246&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;877fc-247&quot;>![Symbol &quot;Nachverfolgte Hand&quot;](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;Symbol &quot;Nachverfolgte Hand&quot;") Die Hand wird nachverfolgt, aber nicht vom Benutzer gesteuert.</span><span class="sxs-lookup"><span data-stu-id="877fc-247">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="877fc-248">Klicken Sie auf diese Schaltfläche, um die Hand auszublenden.</span><span class="sxs-lookup"><span data-stu-id="877fc-248">Click to hide the hand.</span></span>
* <span data-ttu-id="877fc-249">![Symbol "Kontrollierte Hand"](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Symbol &quot;Kontrollierte Hand&quot;") Die Hand wird vom Benutzer nachverfolgt und gesteuert.</span><span class="sxs-lookup"><span data-stu-id="877fc-249">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="877fc-250">Klicken Sie auf diese Schaltfläche, um die Hand auszublenden.</span><span class="sxs-lookup"><span data-stu-id="877fc-250">Click to hide the hand.</span></span>
* <span data-ttu-id="877fc-251">![Symbol "Hand zurücksetzen"](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Symbol &quot;Hand zurücksetzen&quot;") Klicken Sie auf diese Option, um die Hand auf die Standardposition zurückzusetzen.</span><span class="sxs-lookup"><span data-stu-id="877fc-251">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>


## <a name="see-also"></a><span data-ttu-id="877fc-252">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="877fc-252">See also</span></span>

* <span data-ttu-id="877fc-253">[Eingabesystemprofil](../input/input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="877fc-253">[Input System profile](../input/input-providers.md).</span></span>
