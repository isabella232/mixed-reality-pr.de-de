---
title: Erstellen eines Eingabesystemdatenanbieters
description: Dokumentation zum Erstellen eines Eingabesystems und Datenanbieters in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 0b6012871a4d4988fdb70336a3c33455f479bcac
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281923"
---
# <a name="creating-an-input-system-data-provider"></a><span data-ttu-id="fe6ce-104">Erstellen eines Eingabesystemdatenanbieters</span><span class="sxs-lookup"><span data-stu-id="fe6ce-104">Creating an input system data provider</span></span>

<span data-ttu-id="fe6ce-105">Das eingabesystem Mixed Reality Toolkit ist ein erweiterbares System zum Aktivieren der Unterstützung von Eingabegeräten.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-105">The Mixed Reality Toolkit input system is an extensible system for enabling input device support.</span></span> <span data-ttu-id="fe6ce-106">Um Unterstützung für eine neue Hardwareplattform hinzuzufügen, ist möglicherweise ein benutzerdefinierter Eingabedatenanbieter erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-106">To add support for a new hardware platform, a custom input data provider may be required.</span></span>

<span data-ttu-id="fe6ce-107">In diesem Artikel wird beschrieben, wie Sie benutzerdefinierte Datenanbieter, auch als Geräte-Manager bezeichnet, für das Eingabesystem erstellen.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-107">This article describes how to create custom data providers, also called device managers, for the input system.</span></span> <span data-ttu-id="fe6ce-108">Der hier gezeigte Beispielcode stammt aus dem [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="fe6ce-108">The example code shown here is from the [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager).</span></span>

> <span data-ttu-id="fe6ce-109">Den vollständigen Code, der in diesem Beispiel verwendet wird, finden Sie im Ordner MRTK/Providers/WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-109">The complete code used in this example can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="fe6ce-110">Namespace- und Ordnerstruktur</span><span class="sxs-lookup"><span data-stu-id="fe6ce-110">Namespace and folder structure</span></span>

<span data-ttu-id="fe6ce-111">Datenanbieter können als Add-On von Drittanbietern oder als Teil des Microsoft Mixed Reality Toolkits verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-111">Data providers can be distributed as a third party add-on or as a part of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="fe6ce-112">Der Genehmigungsprozess für die Übermittlung neuer Datenanbieter an das MRTK variiert von Fall zu Fall und wird zum Zeitpunkt des ursprünglichen Vorschlags kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span>

> [!Important]
> <span data-ttu-id="fe6ce-113">Wenn ein Eingabesystemdatenanbieter an das [Mixed Reality Toolkit-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity)übermittelt wird, **muss** der Namespace mit Microsoft.MixedReality.Toolkit (z.B. Microsoft.MixedReality.Toolkit.WindowsMixedReality) beginnen, und der Code sollte sich in einem Ordner unter MRTK/Providers (z.B. MRTK/Providers/WindowsMixedReality) befinden.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-113">If an input system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: Microsoft.MixedReality.Toolkit.WindowsMixedReality) and the code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/WindowsMixedReality).</span></span>

### <a name="namespace"></a><span data-ttu-id="fe6ce-114">Namespace</span><span class="sxs-lookup"><span data-stu-id="fe6ce-114">Namespace</span></span>

<span data-ttu-id="fe6ce-115">Datenanbieter müssen über einen Namespace verfügen, um potenzielle Namenskonflikte zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-115">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="fe6ce-116">Es wird empfohlen, dass der Namespace die folgenden Komponenten enthält.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-116">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="fe6ce-117">Unternehmensname</span><span class="sxs-lookup"><span data-stu-id="fe6ce-117">Company name</span></span>
- <span data-ttu-id="fe6ce-118">Featurebereich</span><span class="sxs-lookup"><span data-stu-id="fe6ce-118">Feature area</span></span>

<span data-ttu-id="fe6ce-119">Beispielsweise kann ein vom Contoso-Unternehmen erstellter Eingabedatenanbieter "Contoso.MixedReality.Toolkit.Input" sein.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-119">For example, an input data provider created by the Contoso company may be "Contoso.MixedReality.Toolkit.Input".</span></span>

### <a name="recommended-folder-structure"></a><span data-ttu-id="fe6ce-120">Empfohlene Ordnerstruktur</span><span class="sxs-lookup"><span data-stu-id="fe6ce-120">Recommended folder structure</span></span>

<span data-ttu-id="fe6ce-121">Es wird empfohlen, den Quellcode für Datenanbieter in einer Ordnerhierarchie zu erstellen, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-121">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Beispiel für die Paketordnerstruktur](../images/input/ExampleProviderFolderStructure.png)

<span data-ttu-id="fe6ce-123">Wenn ContosoInput die Implementierung des Datenanbieters enthält, enthält der Ordner Editor den Inspektor (und jeglichen anderen Unity-Editor-spezifischen Code), der Ordner Textures enthält Bilder der unterstützten Controller und Profile ein oder mehrere vorgefertigte Profile.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-123">Where ContosoInput contains the implementation of the data provider, the Editor folder contains the inspector (and any other Unity editor specific code), the Textures folder contains images of the supported controllers, and Profiles contains one or more pre-made profiles.</span></span>

> [!Note]
> <span data-ttu-id="fe6ce-124">Einige gängige Controllerbilder finden Sie im Ordner MixedRealityToolkit\StandardAssets\Textures.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-124">Some common controller images can be found in the MixedRealityToolkit\StandardAssets\Textures folder.</span></span>

## <a name="implement-the-data-provider"></a><span data-ttu-id="fe6ce-125">Implementieren des Datenanbieters</span><span class="sxs-lookup"><span data-stu-id="fe6ce-125">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="fe6ce-126">Angeben der Schnittstellen- und/oder Basisklassenvererbung</span><span class="sxs-lookup"><span data-stu-id="fe6ce-126">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="fe6ce-127">Alle Eingabesystemdatenanbieter müssen die [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) -Schnittstelle implementieren, die die minimal erforderliche Funktionalität des Eingabesystems angibt.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-127">All input system data providers must implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, which specifies the minimum functionality required by the input system.</span></span> <span data-ttu-id="fe6ce-128">Die MRTK-Grundlage enthält die [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) -Klasse, die eine Standardimplementierung dieser erforderlichen Funktionalität bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-128">The MRTK foundation includes the [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) class which provides a default implementation of this required functionality.</span></span> <span data-ttu-id="fe6ce-129">Für Geräte, die auf der UInput-Klasse von Unity aufbauen, kann die [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) -Klasse als Basisklasse verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-129">For devices that build upon Unity's UInput class, the [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) class can be used as a base class.</span></span>

> [!Note]
> <span data-ttu-id="fe6ce-130">Die `BaseInputDeviceManager` Klassen und stellen die erforderliche Implementierung `UnityJoystickManager` `IMixedRealityInputDeviceManager` bereit.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-130">The `BaseInputDeviceManager` and `UnityJoystickManager` classes provide the required `IMixedRealityInputDeviceManager` implementation.</span></span>

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> <span data-ttu-id="fe6ce-131">`IMixedRealityCapabilityCheck` wird von `WindowsMixedRealityDeviceManager` verwendet, um anzugeben, dass es Unterstützung für eine Reihe von Eingabefunktionen bietet, insbesondere artikulierte Hände, Hände mit Anvisieren mit Gesten und Motion-Controller.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-131">`IMixedRealityCapabilityCheck` is used by the `WindowsMixedRealityDeviceManager` to indicate that it provides support for a set of input capabilities, specifically; articulated hands, gaze-gesture-voice hands and motion controllers.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="fe6ce-132">Anwenden des MixedRealityDataProvider-Attributs</span><span class="sxs-lookup"><span data-stu-id="fe6ce-132">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="fe6ce-133">Ein wichtiger Schritt beim Erstellen eines Eingabesystemdatenanbieters ist das Anwenden des [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) -Attributs auf die -Klasse.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-133">A key step of creating an input system data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="fe6ce-134">Dieser Schritt ermöglicht das Festlegen des Standardprofils und der Plattformen für den Anbieter, wenn diese im Eingabesystemprofil ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-134">This step enables setting the default profile and platform(s) for the provider, when selected in the input system profile.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="fe6ce-135">Implementieren der IMixedRealityDataProvider-Methoden</span><span class="sxs-lookup"><span data-stu-id="fe6ce-135">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="fe6ce-136">Nachdem die -Klasse definiert wurde, besteht der nächste Schritt darin, die Implementierung der [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) -Schnittstelle bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-136">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!Note]
> <span data-ttu-id="fe6ce-137">Die `BaseInputDeviceManager` -Klasse stellt über die `BaseService` -Klasse nur leere Implementierungen für `IMixedRealityDataProvider` Methoden bereit.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-137">The `BaseInputDeviceManager` class, via the `BaseService` class, provides only empty implementations for `IMixedRealityDataProvider` methods.</span></span> <span data-ttu-id="fe6ce-138">Die Details dieser Methoden sind im Allgemeinen datenanbieterspezifisch.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-138">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="fe6ce-139">Der Datenanbieter sollte folgende Methoden implementieren:</span><span class="sxs-lookup"><span data-stu-id="fe6ce-139">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="fe6ce-140">Implementieren der Datenanbieterlogik</span><span class="sxs-lookup"><span data-stu-id="fe6ce-140">Implement the data provider logic</span></span>

<span data-ttu-id="fe6ce-141">Der nächste Schritt besteht darin, die Logik für die Verwaltung der Eingabegeräte hinzuzufügen, einschließlich aller zu unterstützenden Controller.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-141">The next step is to add the logic for managing the input devices, including any controllers to be supported.</span></span>

### <a name="implement-the-controller-classes"></a><span data-ttu-id="fe6ce-142">Implementieren der Controllerklassen</span><span class="sxs-lookup"><span data-stu-id="fe6ce-142">Implement the controller classes</span></span>

 <span data-ttu-id="fe6ce-143">Im Beispiel von `WindowsMixedRealityDeviceManager` werden die folgenden Controllerklassen definiert und implementiert.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-143">The example of the `WindowsMixedRealityDeviceManager` defines and implements the following controller classes.</span></span>

> <span data-ttu-id="fe6ce-144">Den Quellcode für jede dieser Klassen finden Sie im Ordner MRTK/Providers/WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-144">The source code for each of these classes can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

- <span data-ttu-id="fe6ce-145">WindowsMixedRealityArticulatedHand.cs</span><span class="sxs-lookup"><span data-stu-id="fe6ce-145">WindowsMixedRealityArticulatedHand.cs</span></span>
- <span data-ttu-id="fe6ce-146">WindowsMixedRealityController.cs</span><span class="sxs-lookup"><span data-stu-id="fe6ce-146">WindowsMixedRealityController.cs</span></span>
- <span data-ttu-id="fe6ce-147">WindowsMixedRealityGGVHand.cs</span><span class="sxs-lookup"><span data-stu-id="fe6ce-147">WindowsMixedRealityGGVHand.cs</span></span>

> [!Note]
> <span data-ttu-id="fe6ce-148">Nicht alle Geräte-Manager unterstützen mehrere Controllertypen.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-148">Not all device managers will support multiple controller types.</span></span>

#### <a name="apply-the-mixedrealitycontroller-attribute"></a><span data-ttu-id="fe6ce-149">Anwenden des MixedRealityController-Attributs</span><span class="sxs-lookup"><span data-stu-id="fe6ce-149">Apply the MixedRealityController attribute</span></span>

<span data-ttu-id="fe6ce-150">Wenden Sie als Nächstes das [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) -Attribut auf die -Klasse an.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-150">Next, apply the [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribute to the class.</span></span> <span data-ttu-id="fe6ce-151">Dieses Attribut gibt den Typ des Controllers (z. B. artikulierte Hand), die Handkraft (z. B. links oder rechts) und ein optionales Controllerbild an.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-151">This attribute specifies the type of controller (ex: articulated hand), the handedness (ex: left or right) and an optional controller image.</span></span>

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a><span data-ttu-id="fe6ce-152">Konfigurieren der Interaktionszuordnungen</span><span class="sxs-lookup"><span data-stu-id="fe6ce-152">Configure the interaction mappings</span></span>

<span data-ttu-id="fe6ce-153">Der nächste Schritt besteht darin, den Satz von Interaktionszuordnungen zu definieren, die vom Controller unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-153">The next step is to define the set of interaction mappings supported by the controller.</span></span> <span data-ttu-id="fe6ce-154">Für Geräte, die ihre Daten über die Input-Klasse von Unity empfangen, ist das [Controllerzuordnungstool](../tools/controller-mapping-tool.md) eine hilfreiche Ressource zum Bestätigen der richtigen Achsen- und Schaltflächenzuordnungen, die Interaktionen zugewiesen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-154">For devices that receive their data via Unity's Input class, the [controller mapping tool](../tools/controller-mapping-tool.md) is a helpful resource to confirm the correct axis and button mappings to assign to interactions.</span></span>

<span data-ttu-id="fe6ce-155">Das folgende Beispiel wird von der -Klasse abgekürzt, `GenericOpenVRController` die sich im Ordner MRTK/Providers/OpenVR befindet.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-155">The following example is abbreviated from the `GenericOpenVRController` class, located in the MRTK/Providers/OpenVR folder.</span></span>

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
><span data-ttu-id="fe6ce-156">Die [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) -Klasse stellt symbolische Konstanten für die Unity-Eingabeachse und Schaltflächendefinitionen bereit.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-156">The [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) class provides symbolic constants for the Unity input axis and button definitions.</span></span>

### <a name="raise-notification-events"></a><span data-ttu-id="fe6ce-157">Auslösen von Benachrichtigungsereignissen</span><span class="sxs-lookup"><span data-stu-id="fe6ce-157">Raise notification events</span></span>

<span data-ttu-id="fe6ce-158">Damit Anwendungen auf Eingaben des Benutzers reagieren können, löst der Datenanbieter Benachrichtigungsereignisse aus, die den in den Schnittstellen und definierten Controllerzustandsänderungen [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-158">To enable applications to respond to input from the user, the data provider raises notification events corresponding to controller state changes as defined in the [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) and [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces.</span></span>

<span data-ttu-id="fe6ce-159">Für digitale Typsteuerelemente (Schaltflächen) können Sie die Ereignisse OnInputDown und OnInputUp auslösen.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-159">For digital (button) type controls, raise the OnInputDown and OnInputUp events.</span></span>

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

<span data-ttu-id="fe6ce-160">Für analoge Steuerelemente (z. B. Touchpadposition) sollte das InputChanged-Ereignis ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-160">For analog controls (ex: touchpad position) the InputChanged event should be raised.</span></span>

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="fe6ce-161">Hinzufügen der Unity Profiler-Instrumentierung</span><span class="sxs-lookup"><span data-stu-id="fe6ce-161">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="fe6ce-162">Leistung ist in Mixed Reality-Anwendungen von entscheidender Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-162">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="fe6ce-163">Jede Komponente erhöht den Mehraufwand, den Anwendungen berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-163">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="fe6ce-164">Zu diesem Zweck ist es wichtig, dass alle Eingabedatenanbieter die Unity Profiler-Instrumentierung in einer inneren Schleife und häufig verwendeten Codepfaden enthalten.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-164">To this end, it is important that all input data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="fe6ce-165">Es wird empfohlen, das Muster zu implementieren, das vom MRTK beim Instrumentieren benutzerdefinierter Anbieter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-165">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="fe6ce-166">Der Name, der zum Identifizieren des Profilermarkers verwendet wird, ist willkürlich.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-166">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="fe6ce-167">Das MRTK verwendet das folgende Muster.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-167">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="fe6ce-168">"[product] className.methodName – optionaler Hinweis"</span><span class="sxs-lookup"><span data-stu-id="fe6ce-168">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="fe6ce-169">Es wird empfohlen, dass benutzerdefinierte Datenanbieter ein ähnliches Muster befolgen, um die Identifizierung bestimmter Komponenten und Methoden bei der Analyse von Ablaufverfolgungen zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-169">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="fe6ce-170">Erstellen des Profils und des Inspektors</span><span class="sxs-lookup"><span data-stu-id="fe6ce-170">Create the profile and inspector</span></span>

<span data-ttu-id="fe6ce-171">Im Mixed Reality Toolkit werden Datenanbieter mithilfe von [Profilen](../profiles/profiles.md)konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-171">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

<span data-ttu-id="fe6ce-172">Datenanbieter mit zusätzlichen Konfigurationsoptionen (z. B. [InputSimulationService](../input-simulation/input-simulation-service.md)) sollten ein Profil und einen Inspektor erstellen, damit Kunden das Verhalten so ändern können, dass es den Anforderungen der Anwendung am besten entspricht.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-172">Data providers with additional configuration options (ex: [InputSimulationService](../input-simulation/input-simulation-service.md)) should create a profile and inspector to allow customers to modify the behavior to best suit the needs of the application.</span></span>

> <span data-ttu-id="fe6ce-173">Den vollständigen Code für das Beispiel in diesem Abschnitt finden Sie im MRTK. Ordner "Services/InputSimulation".</span><span class="sxs-lookup"><span data-stu-id="fe6ce-173">The complete code for the example in this section can be found in the MRTK.Services/InputSimulation folder.</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="fe6ce-174">Definieren des Profils</span><span class="sxs-lookup"><span data-stu-id="fe6ce-174">Define the profile</span></span>

<span data-ttu-id="fe6ce-175">Profilinhalte sollten die zugänglichen Eigenschaften des Beobachters spiegeln (z. B. Aktualisierungsintervall).</span><span class="sxs-lookup"><span data-stu-id="fe6ce-175">Profile contents should mirror the accessible properties of the observer (ex: update interval).</span></span> <span data-ttu-id="fe6ce-176">Alle vom Benutzer konfigurierbaren Eigenschaften, die in jeder Schnittstelle definiert sind, sollten im Profil enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-176">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

<span data-ttu-id="fe6ce-177">Das `CreateAssetMenu` -Attribut kann auf die Profilklasse angewendet werden, damit Kunden mithilfe des Menüs **Create > Assets > Mixed Reality Toolkit > Profiles** eine Profilinstanz erstellen können.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-177">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create > Assets > Mixed Reality Toolkit > Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="fe6ce-178">Implementieren des Inspektors</span><span class="sxs-lookup"><span data-stu-id="fe6ce-178">Implement the inspector</span></span>

<span data-ttu-id="fe6ce-179">Profilinspektoren sind die Benutzeroberfläche zum Konfigurieren und Anzeigen von Profilinhalten.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-179">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="fe6ce-180">Jeder Profilinspektor sollte die [Klasse "BaseMixedRealityToolkitConfigurationProfileInspector"](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) erweitern.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-180">Each profile inspector should extend the [\`BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

<span data-ttu-id="fe6ce-181">Das `CustomEditor` -Attribut informiert Unity über den Typ des Medienobjekts, für das der Inspektor gilt.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-181">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

## <a name="create-assembly-definitions"></a><span data-ttu-id="fe6ce-182">Erstellen von Assemblydefinitionen</span><span class="sxs-lookup"><span data-stu-id="fe6ce-182">Create assembly definition(s)</span></span>

<span data-ttu-id="fe6ce-183">Das Mixed Reality Toolkit verwendet Assemblydefinitionsdateien[(ASMDEF-Dateien),](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)um Abhängigkeiten zwischen Komponenten anzugeben und Unity bei der Reduzierung der Kompilierungszeit zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-183">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="fe6ce-184">Es wird empfohlen, Assemblydefinitionsdateien für alle Datenanbieter und deren Editorkomponenten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-184">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="fe6ce-185">Wenn Sie die [Ordnerstruktur](#recommended-folder-structure) im vorherigen Beispiel verwenden, gibt es zwei ASMDEF-Dateien für den ContosoInput-Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-185">Using the [folder structure](#recommended-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoInput data provider.</span></span>

<span data-ttu-id="fe6ce-186">Die erste Assemblydefinition ist für den Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-186">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="fe6ce-187">In diesem Beispiel heißt sie ContosoInput und befindet sich im Ordner ContosoInput des Beispiels.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-187">For this example, it will be called ContosoInput and will be located in the example's ContosoInput folder.</span></span>
<span data-ttu-id="fe6ce-188">Diese Assemblydefinition muss eine Abhängigkeit von Microsoft.MixedReality.Toolkit und allen anderen Assemblys angeben, von denen sie abhängt.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-188">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="fe6ce-189">Die Assemblydefinition ContosoInputEditor gibt den Profilinspektor und jeden editorspezifischen Code an.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-189">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="fe6ce-190">Diese Datei muss sich im Stammordner des Editorcodes befinden.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-190">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="fe6ce-191">In diesem Beispiel befindet sich die Datei im Ordner ContosoInput\Editor.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-191">In this example, the file will be located in the ContosoInput\Editor folder.</span></span> <span data-ttu-id="fe6ce-192">Diese Assemblydefinition enthält einen Verweis auf die ContosoInput-Assembly sowie:</span><span class="sxs-lookup"><span data-stu-id="fe6ce-192">This assembly definition will contain a reference to the ContosoInput assembly as well as:</span></span>

- <span data-ttu-id="fe6ce-193">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="fe6ce-193">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="fe6ce-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="fe6ce-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="fe6ce-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="fe6ce-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="fe6ce-196">Registrieren des Datenanbieters</span><span class="sxs-lookup"><span data-stu-id="fe6ce-196">Register the data provider</span></span>

<span data-ttu-id="fe6ce-197">Nach der Erstellung kann der Datenanbieter beim Eingabesystem registriert und in der Anwendung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-197">Once created, the data provider can be registered with the input system and be used in the application.</span></span>

![Registrierte Eingabesystemdatenanbieter](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a><span data-ttu-id="fe6ce-199">Verpacken und Verteilen</span><span class="sxs-lookup"><span data-stu-id="fe6ce-199">Packaging and distribution</span></span>

<span data-ttu-id="fe6ce-200">Datenanbieter, die als Drittanbieterkomponenten verteilt werden, verfügen über die spezifischen Details der Paketierung und Verteilung, die dem Entwickler überlassen werden.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-200">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="fe6ce-201">Wahrscheinlich ist die gängigste Lösung die Generierung eines UNITYPACKAGE-Pakets und das Verteilen über das Unity-Medienobjekt Store.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-201">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="fe6ce-202">Wenn ein Datenanbieter als Teil des Microsoft Mixed Reality Toolkit-Pakets übermittelt und akzeptiert wird, packt und verteilt das Microsoft MRTK-Team ihn im Rahmen der MRTK-Angebote.</span><span class="sxs-lookup"><span data-stu-id="fe6ce-202">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe6ce-203">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fe6ce-203">See also</span></span>

- [<span data-ttu-id="fe6ce-204">Eingabesystem</span><span class="sxs-lookup"><span data-stu-id="fe6ce-204">Input system</span></span>](overview.md)
- [<span data-ttu-id="fe6ce-205">`BaseInputDeviceManager`-Klasse</span><span class="sxs-lookup"><span data-stu-id="fe6ce-205">`BaseInputDeviceManager` class</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [<span data-ttu-id="fe6ce-206">`IMixedRealityInputDeviceManager` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="fe6ce-206">`IMixedRealityInputDeviceManager` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [<span data-ttu-id="fe6ce-207">`IMixedRealityInputHandler` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="fe6ce-207">`IMixedRealityInputHandler` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [<span data-ttu-id="fe6ce-208">`IMixedRealityInputHandler<T>` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="fe6ce-208">`IMixedRealityInputHandler<T>` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [<span data-ttu-id="fe6ce-209">`IMixedRealityDataProvider` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="fe6ce-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="fe6ce-210">`IMixedRealityCapabilityCheck` Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="fe6ce-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="fe6ce-211">Controllerzuordnungstool</span><span class="sxs-lookup"><span data-stu-id="fe6ce-211">Controller Mapping Tool</span></span>](../tools/controller-mapping-tool.md)
