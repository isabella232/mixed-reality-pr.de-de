---
title: Eingabeaktionen
description: Dokumentation zum Erstellen von Eingabeaktionen in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, InputActions,
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144157"
---
# <a name="input-actions"></a><span data-ttu-id="3e368-104">Eingabeaktionen</span><span class="sxs-lookup"><span data-stu-id="3e368-104">Input actions</span></span>

<span data-ttu-id="3e368-105">[**Eingabeaktionen**](input-actions.md) sind Abstraktionen über unformatierte Eingaben, die dazu dienen sollen, die Anwendungslogik von den spezifischen Eingabequellen zu isolieren, die eine Eingabe erzeugen.</span><span class="sxs-lookup"><span data-stu-id="3e368-105">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="3e368-106">Es kann beispielsweise nützlich sein, eine *Select-Aktion* zu definieren und sie der linken Maustaste, einer Schaltfläche in einem Gamepad und einem Trigger in einem 6-DOF-Controller zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="3e368-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="3e368-107">Sie können ihre Anwendungslogik dann auf Select input action events (Eingabeaktionsereignisse *auswählen)* lauschen lassen, anstatt alle verschiedenen Eingaben kennen zu müssen, die sie erzeugen können.</span><span class="sxs-lookup"><span data-stu-id="3e368-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="3e368-108">Erstellen einer Eingabeaktion</span><span class="sxs-lookup"><span data-stu-id="3e368-108">Creating an input action</span></span>

<span data-ttu-id="3e368-109">Eingabeaktionen werden im **Eingabeaktionsprofil** innerhalb des *Eingabesystemprofils* in der Komponente Mixed Reality Toolkit konfiguriert und geben einen Namen für die Aktion und den Typ der Eingaben *(Achseneinschränkung)* an, denen sie zugeordnet werden kann:</span><span class="sxs-lookup"><span data-stu-id="3e368-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

<span data-ttu-id="3e368-110">Dies sind die am häufigsten verwendeten Werte für **Achseneinschränkung:**</span><span class="sxs-lookup"><span data-stu-id="3e368-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="3e368-111">Achseneinschränkung</span><span class="sxs-lookup"><span data-stu-id="3e368-111">Axis Constraint</span></span> | <span data-ttu-id="3e368-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3e368-112">Description</span></span>
--- | ---
<span data-ttu-id="3e368-113">Digital</span><span class="sxs-lookup"><span data-stu-id="3e368-113">Digital</span></span> | <span data-ttu-id="3e368-114">Ein-/Aus-Eingabe wie eine binäre Schaltfläche in einem Gamepad oder einer Maus.</span><span class="sxs-lookup"><span data-stu-id="3e368-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="3e368-115">Einzelne Achse</span><span class="sxs-lookup"><span data-stu-id="3e368-115">Single Axis</span></span> | <span data-ttu-id="3e368-116">Eingabe für die Einachsenentsprechung wie ein analoger Trigger in einem Gamepad.</span><span class="sxs-lookup"><span data-stu-id="3e368-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="3e368-117">Duale Achse</span><span class="sxs-lookup"><span data-stu-id="3e368-117">Dual Axis</span></span> | <span data-ttu-id="3e368-118">Eingabe der Doppelachsenentsprechung wie ein Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="3e368-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="3e368-119">Sechs Dof</span><span class="sxs-lookup"><span data-stu-id="3e368-119">Six Dof</span></span> | <span data-ttu-id="3e368-120">3D-Posen mit Übersetzung und Drehung wie die von 6 DOF-Controllern erzeugte.</span><span class="sxs-lookup"><span data-stu-id="3e368-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="3e368-121">Die vollständige Liste finden Sie unter [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .</span><span class="sxs-lookup"><span data-stu-id="3e368-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="3e368-122">Zuordnen von Eingaben zu Aktionen</span><span class="sxs-lookup"><span data-stu-id="3e368-122">Mapping input to actions</span></span>

<span data-ttu-id="3e368-123">Die Art und Weise, wie Sie eine Eingabe und eine Aktion zuordnen, hängt vom Typ der Eingabequelle ab:</span><span class="sxs-lookup"><span data-stu-id="3e368-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="3e368-124">Controllereingabe</span><span class="sxs-lookup"><span data-stu-id="3e368-124">Controller input</span></span>

<span data-ttu-id="3e368-125">Wechseln Sie unter **dem Eingabesystemprofil** zum *Controller-Eingabezuordnungsprofil.*</span><span class="sxs-lookup"><span data-stu-id="3e368-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="3e368-126">Dort finden Sie eine Liste aller unterstützten Controller:</span><span class="sxs-lookup"><span data-stu-id="3e368-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

<span data-ttu-id="3e368-127">Wählen Sie das Dialogfeld aus, das Sie konfigurieren möchten, und es wird ein Dialogfeld mit allen Controllereingaben angezeigt, sodass Sie eine Aktion für jede von ihnen festlegen können:</span><span class="sxs-lookup"><span data-stu-id="3e368-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a><span data-ttu-id="3e368-128">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="3e368-128">Speech input</span></span>

<span data-ttu-id="3e368-129">Im **Speech-Befehlsprofil** finden Sie unter dem *Eingabesystemprofil* die Liste der derzeit definierten Sprachbefehle.</span><span class="sxs-lookup"><span data-stu-id="3e368-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="3e368-130">Um einer Aktion eines davon zu zuordnen, wählen Sie es einfach in der *Dropdownliste Aktion* aus.</span><span class="sxs-lookup"><span data-stu-id="3e368-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a><span data-ttu-id="3e368-131">Gesteneingabe</span><span class="sxs-lookup"><span data-stu-id="3e368-131">Gesture input</span></span>

<span data-ttu-id="3e368-132">Das **Gestenprofil** unter dem *Eingabesystemprofil* enthält alle definierten Gesten.</span><span class="sxs-lookup"><span data-stu-id="3e368-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="3e368-133">Sie können sie jeweils einer Aktion zuordnen, indem Sie sie in der *Dropdownliste Aktion* auswählen.</span><span class="sxs-lookup"><span data-stu-id="3e368-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a><span data-ttu-id="3e368-134">Behandeln von Eingabeaktionen</span><span class="sxs-lookup"><span data-stu-id="3e368-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="3e368-135">Derzeit können nur Eingabeaktionen *vom Typ Digital* mithilfe der in diesem Abschnitt beschriebenen Methoden verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="3e368-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="3e368-136">Bei anderen Aktionstypen müssen Sie stattdessen die Ereignisse für die entsprechenden Eingaben direkt behandeln.</span><span class="sxs-lookup"><span data-stu-id="3e368-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="3e368-137">Um beispielsweise eine 6-DOF-Aktion zu verarbeiten, die Controllereingaben zugeordnet ist, müssen Sie mit [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) verwenden.</span><span class="sxs-lookup"><span data-stu-id="3e368-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="3e368-138">Die einfachste Möglichkeit zur Handhabung von Eingabeaktionen besteht in der Verwendung des [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) Skripts.</span><span class="sxs-lookup"><span data-stu-id="3e368-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="3e368-139">Auf diese Weise können Sie die Aktion definieren, auf die Sie mit unity-Ereignissen lauschen und auf gestartete und beendete Ereignisse reagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="3e368-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

<span data-ttu-id="3e368-140">Wenn Sie mehr Kontrolle wünschen, können Sie die -Schnittstelle [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) direkt in Ihrem Skript implementieren.</span><span class="sxs-lookup"><span data-stu-id="3e368-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="3e368-141">Weitere Informationen [**zur Ereignisbehandlung über**](input-events.md) Handlerschnittstellen finden Sie im Abschnitt Eingabeereignisse.</span><span class="sxs-lookup"><span data-stu-id="3e368-141">See the [**Input Events**](input-events.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="3e368-142">Beispiele</span><span class="sxs-lookup"><span data-stu-id="3e368-142">Examples</span></span>

<span data-ttu-id="3e368-143">Sehen `MRTK/Examples/Demos/Input/Scenes/InputActions` Sie sich eine Beispielszene an, die zeigt, wie Sie eine Aktion erstellen, sie Controller-, Sprach- und Gesteneingaben zuordnen und damit ein Objekt auf Befehl drehen.</span><span class="sxs-lookup"><span data-stu-id="3e368-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
