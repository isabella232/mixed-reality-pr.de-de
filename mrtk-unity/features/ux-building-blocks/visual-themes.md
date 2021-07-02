---
title: Visuelle Designs
description: 'Übersicht: Visuelle Designs Flexible Steuerung von UX-Ressourcen in MRTK'
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, MRTK-Designs,
ms.openlocfilehash: d97c470bf1d77299c6848990cdc69d886d432ecb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177174"
---
# <a name="visual-themes"></a><span data-ttu-id="2b296-104">Visuelle Designs</span><span class="sxs-lookup"><span data-stu-id="2b296-104">Visual themes</span></span>

<span data-ttu-id="2b296-105">Designs ermöglichen eine flexible Steuerung von UX-Ressourcen als Reaktion auf verschiedene Zustände.</span><span class="sxs-lookup"><span data-stu-id="2b296-105">Themes allow for flexible control of UX assets in response to various states transitions.</span></span> <span data-ttu-id="2b296-106">Dies kann das Ändern der Farbe einer Schaltfläche, das Ändern der Größe eines Elements als Reaktion auf den Fokus usw. umfassen. Das Visual Themes-Framework besteht aus zwei Hauptteilen: 1) Konfiguration und 2) Runtime-Engines.</span><span class="sxs-lookup"><span data-stu-id="2b296-106">This may involve changing a button's color, resizing an element in response to focus, etc. The Visual Themes framework is made up of two key pieces: 1) configuration and 2) runtime engines.</span></span>

<span data-ttu-id="2b296-107">[Designkonfigurationen](#theme-configuration) sind Definitionen von Eigenschaften und Typen, während [Design-Engines](#theme-engines) Klassen sind, die die Konfigurationen nutzen und die Logik implementieren, um Transformationen, Materialien und mehr zur Laufzeit zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="2b296-107">[Theme configurations](#theme-configuration) are definitions of properties and types while [Theme Engines](#theme-engines) are classes that consume the configurations and implement the logic to update transforms, materials, and more at runtime.</span></span>

## <a name="theme-configuration"></a><span data-ttu-id="2b296-108">Designkonfiguration</span><span class="sxs-lookup"><span data-stu-id="2b296-108">Theme configuration</span></span>

<span data-ttu-id="2b296-109">Designkonfigurationen sind [ScriptableObjects,](https://docs.unity3d.com/Manual/class-ScriptableObject.html) die definieren, wie Design-Engines zur Laufzeit initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="2b296-109">Theme configurations are [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) that define how Theme Engines will be initialized at runtime.</span></span> <span data-ttu-id="2b296-110">Sie definieren, welche Eigenschaften und Werte als Reaktion auf Eingabe- oder andere Zustandsänderungen verwendet werden sollen, wenn die App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2b296-110">They define what properties and values to utilize in response to input or other state changes when the app is running.</span></span> <span data-ttu-id="2b296-111">Als [ScriptableObjects-Objekte](https://docs.unity3d.com/Manual/class-ScriptableObject.html) können Designkonfigurationen einmal definiert und dann über verschiedene UX-Komponenten hinweg erneut verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2b296-111">As [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets, theme configurations can be defined once and then re-used across different UX components.</span></span>

<span data-ttu-id="2b296-112">So erstellen Sie ein neues [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) Asset:</span><span class="sxs-lookup"><span data-stu-id="2b296-112">To create a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span></span>

1) <span data-ttu-id="2b296-113">Klicken Sie mit der rechten Maustaste in *Project Fenster.*</span><span class="sxs-lookup"><span data-stu-id="2b296-113">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="2b296-114">Wählen Sie **Create**  >  **Mixed Reality Toolkit Theme (Toolkitdesign**  >  **erstellen) aus.**</span><span class="sxs-lookup"><span data-stu-id="2b296-114">Select **Create** > **Mixed Reality Toolkit** > **Theme**</span></span>

<span data-ttu-id="2b296-115">Beispielressourcen für die Designkonfiguration finden Sie unter `MRTK/SDK/Features/UX/Interactable/Themes` .</span><span class="sxs-lookup"><span data-stu-id="2b296-115">Example Theme configuration assets can be found under `MRTK/SDK/Features/UX/Interactable/Themes`.</span></span>

![Theme ScriptableObject-Beispiel im Inspektor](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a><span data-ttu-id="2b296-117">Zustände</span><span class="sxs-lookup"><span data-stu-id="2b296-117">States</span></span>

<span data-ttu-id="2b296-118">Beim Erstellen eines neuen [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) muss zunächst festgelegt werden, welche Zustände verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="2b296-118">When creating a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme), the first thing to set is what states are available.</span></span> <span data-ttu-id="2b296-119">Die *States-Eigenschaft* gibt an, wie viele Werte eine Designkonfiguration definieren muss, da es einen Wert pro Zustand gibt.</span><span class="sxs-lookup"><span data-stu-id="2b296-119">The *States* property indicates how many values a Theme configuration needs to define as there will be one value per state.</span></span> <span data-ttu-id="2b296-120">In der obigen Beispielbild sind die Standardzustände, die für die [Interactable-Komponente](interactable.md#general-input-settings) definiert *sind, Default*, *Focus*, *Pressed* und *Disabled*.</span><span class="sxs-lookup"><span data-stu-id="2b296-120">In the example image above, the [default states defined for the Interactable](interactable.md#general-input-settings) component are *Default*, *Focus*, *Pressed*, and *Disabled*.</span></span> <span data-ttu-id="2b296-121">Diese werden in der `DefaultInteractableStates` Ressourcendatei (Assets/MRTK/SDK/Features/UX/Interactable/States) definiert.</span><span class="sxs-lookup"><span data-stu-id="2b296-121">These are defined in the `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States) asset file.</span></span>

<span data-ttu-id="2b296-122">So erstellen Sie ein neues [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) Asset:</span><span class="sxs-lookup"><span data-stu-id="2b296-122">To create a new [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span></span>

1) <span data-ttu-id="2b296-123">Klicken Sie mit der rechten Maustaste in *Project Fenster.*</span><span class="sxs-lookup"><span data-stu-id="2b296-123">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="2b296-124">Wählen Sie **Create** Mixed Reality Toolkit State  >  **(Toolkitstatus**  >  **erstellen) aus.**</span><span class="sxs-lookup"><span data-stu-id="2b296-124">Select **Create** > **Mixed Reality Toolkit** > **State**</span></span>

![States ScriptableObject-Beispiel im Inspektor](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="2b296-126">Ein ScriptableObject definiert sowohl die Liste der Status als auch den Typ von [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) *StateModel,* der für diese Zustände erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="2b296-126">A [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject defines both the list of states as well as the type of *StateModel* to create for these states.</span></span> <span data-ttu-id="2b296-127">Ein *StateModel ist* eine Klasse, die die Zustandsautomatenlogik erweitert und implementiert, um den [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) aktuellen Zustand zur Laufzeit zu generieren.</span><span class="sxs-lookup"><span data-stu-id="2b296-127">A *StateModel* is a class that extends [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) and implements the state machine logic to generate the current state at runtime.</span></span> <span data-ttu-id="2b296-128">Der aktuelle Zustand dieser Klasse wird in der Regel von Design-Engines zur Laufzeit verwendet, um vorschreiben, welche Werte für Materialeigenschaften, GameObject-Transformationen und mehr festgelegt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="2b296-128">The current state from this class is generally used by Theme Engines at runtime to dictate what values to set against material properties, GameObject transforms, and more.</span></span>

### <a name="theme-engine-properties"></a><span data-ttu-id="2b296-129">Eigenschaften der Design-Engine</span><span class="sxs-lookup"><span data-stu-id="2b296-129">Theme engine properties</span></span>

<span data-ttu-id="2b296-130">Außerhalb von *Bundesstaaten* definiert [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ein Objekt auch eine Liste von Design-Engines und die zugehörigen Eigenschaften für diese Engines.</span><span class="sxs-lookup"><span data-stu-id="2b296-130">Outside of *States*, a [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset also defines a list of Theme Engines and the associated properties for these engines.</span></span> <span data-ttu-id="2b296-131">Eine [Design-Engine](#theme-engines) definiert erneut die Logik zum Festlegen der richtigen Werte für ein GameObject zur Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="2b296-131">A [Theme engine](#theme-engines) again defines the logic to set the correct values against a GameObject at runtime.</span></span>

<span data-ttu-id="2b296-132">Ein [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) Medienobjekt kann mehrere Design-Engines definieren, um komplexe visuelle Zustände für mehrere GameObject-Eigenschaften zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="2b296-132">A [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset can define multiple Theme Engines to achieve sophisticated visual states transitions targeting multiple GameObject properties.</span></span>

<span data-ttu-id="2b296-133">**Theme Runtime**</span><span class="sxs-lookup"><span data-stu-id="2b296-133">**Theme Runtime**</span></span>

<span data-ttu-id="2b296-134">Definiert den Klassentyp der Design-Engine, die erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="2b296-134">Defines the class type of the Theme engine that will be created</span></span>

<span data-ttu-id="2b296-135">**Lockerung**</span><span class="sxs-lookup"><span data-stu-id="2b296-135">**Easing**</span></span>

<span data-ttu-id="2b296-136">Einige *Design-Engines* unterstützen eine Beschleunigung zwischen Zuzuständen, wenn sie ihre [Eigenschaft IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) als true definieren.</span><span class="sxs-lookup"><span data-stu-id="2b296-136">Some *Theme Engines*, if they define their property [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) as true, support easing between states.</span></span> <span data-ttu-id="2b296-137">Beispiel: Lerping zwischen zwei Farben, wenn eine Zustandsänderung auftritt.</span><span class="sxs-lookup"><span data-stu-id="2b296-137">For example, lerping between two colors when a state change occurs.</span></span> <span data-ttu-id="2b296-138">Die *Dauer* definiert in Sekunden, wie lange vom Startwert zum Endwert gelockert werden soll, und die *Animationskurve* definiert die Änderungsrate während dieses Zeitraums.</span><span class="sxs-lookup"><span data-stu-id="2b296-138">The *Duration* defines in seconds how long to ease from start value to end value and the *Animation Curve* defines the rate of change during that time period.</span></span>

<span data-ttu-id="2b296-139">**Shadereigenschaften**</span><span class="sxs-lookup"><span data-stu-id="2b296-139">**Shader properties**</span></span>

<span data-ttu-id="2b296-140">Einige *Design-Engines* ändern bestimmte Shadereigenschaften zur Laufzeit, wenn sie ihre [Eigenschaft AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) als true definieren.</span><span class="sxs-lookup"><span data-stu-id="2b296-140">Some *Theme Engines*, if they define their property [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) as true, will modify particular shader properties at runtime.</span></span> <span data-ttu-id="2b296-141">Die *Shader-* und *Property-Felder* definieren die shader-Eigenschaft, die als Ziel festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="2b296-141">The *Shader* and *Property* fields define the shader property to target.</span></span>

### <a name="create-a-theme-configuration-via-code"></a><span data-ttu-id="2b296-142">Erstellen einer Designkonfiguration per Code</span><span class="sxs-lookup"><span data-stu-id="2b296-142">Create a theme configuration via code</span></span>

<span data-ttu-id="2b296-143">Im Allgemeinen ist es einfacher, Designkonfigurationen über den Unity-Inspektor zu entwerfen, aber es gibt Fälle, in denen Designs zur Laufzeit dynamisch über Code generiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="2b296-143">In general, it is easier to design Theme configurations via the Unity inspector but there are cases where Themes must be dynamically generated at runtime via code.</span></span> <span data-ttu-id="2b296-144">Der folgende Codeausschnitt enthält ein Beispiel für die Durchführung dieser Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="2b296-144">The code snippet below gives an example of how to accomplish this task.</span></span>

<span data-ttu-id="2b296-145">Um die Entwicklung zu vereinfachen, sind die folgenden Hilfsmethoden nützlich, um das Setup zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="2b296-145">To help expedite development, the following helper methods are useful for simplifying setup.</span></span>

<span data-ttu-id="2b296-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) : Erstellt ein neues States ScriptableObject mit den vier Standardwerten, die in der [Interactable-Komponente verwendet](interactable.md) werden.</span><span class="sxs-lookup"><span data-stu-id="2b296-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - creates a new States ScriptableObject with the four default state values used in the [Interactable](interactable.md) component.</span></span>

<span data-ttu-id="2b296-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) – Jede Design-Engine definiert eine Standardkonfiguration mit den richtigen Eigenschaften, die für diesen Designlaufzeittyp erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="2b296-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Every Theme Engine defines a default configuration with the correct properties needed for that Theme runtime type.</span></span> <span data-ttu-id="2b296-148">Dieses Hilfsmodul erstellt eine Definition für den angegebenen Design-Engine-Typ.</span><span class="sxs-lookup"><span data-stu-id="2b296-148">This helper creates a definition for the given Theme Engine type.</span></span>

```c#
// This code example builds a Theme ScriptableObject that can be used with an Interactable component.
// A random color is selected for the on pressed state every time this code is executed.

// Use the default states utilized in the Interactable component
var defaultStates = Interactable.GetDefaultInteractableStates();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

// Create the Theme configuration asset
Theme testTheme = ScriptableObject.CreateInstance<Theme>();
testTheme.States = defaultStates;
testTheme.Definitions = new List<ThemeDefinition>() { newThemeType };
```

## <a name="theme-engines"></a><span data-ttu-id="2b296-149">Design-Engines</span><span class="sxs-lookup"><span data-stu-id="2b296-149">Theme engines</span></span>

<span data-ttu-id="2b296-150">Eine [Design-Engine](#theme-engines) ist eine Klasse, die von der -Klasse erweitert [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) wird.</span><span class="sxs-lookup"><span data-stu-id="2b296-150">A [Theme Engine](#theme-engines) is a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="2b296-151">Diese Klassen werden zur Laufzeit instanziiert und mit einem -Objekt [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) konfiguriert, wie zuvor beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2b296-151">These classes are instantiated at runtime and configured with a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object as outlined earlier.</span></span>

### <a name="default-theme-engines"></a><span data-ttu-id="2b296-152">Standarddesign-Engines</span><span class="sxs-lookup"><span data-stu-id="2b296-152">Default theme engines</span></span>

<span data-ttu-id="2b296-153">MRTK wird mit einem Standardsatz von Design-Engines ausgestattet, die unten aufgeführt sind:</span><span class="sxs-lookup"><span data-stu-id="2b296-153">MRTK ships with a default set of Theme Engines listed below:</span></span>

- [`InteractableActivateTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableActivateTheme)
- [`InteractableAnimatorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAnimatorTheme)
- [`InteractableAudioTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioTheme)
- [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
- [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
- [`InteractableGrabScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableGrabScaleTheme)
- [`InteractableMaterialTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableMaterialTheme)
- [`InteractableOffsetTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOffsetTheme)
- [`InteractableRotationTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableRotationTheme)
- [`InteractableScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableScaleTheme)
- [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme)
- [`InteractableStringTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStringTheme)
- [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
- [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

<span data-ttu-id="2b296-154">Die Standarddesign-Engines finden Sie unter `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .</span><span class="sxs-lookup"><span data-stu-id="2b296-154">The default Theme Engines can be found under `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines`.</span></span>

### <a name="custom-theme-engines"></a><span data-ttu-id="2b296-155">Benutzerdefinierte Design-Engines</span><span class="sxs-lookup"><span data-stu-id="2b296-155">Custom theme engines</span></span>

<span data-ttu-id="2b296-156">Wie bereits erwähnt, wird eine Design-Engine als Klasse definiert, die von der -Klasse erweitert [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) wird.</span><span class="sxs-lookup"><span data-stu-id="2b296-156">As stated, a Theme Engine is defined as a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="2b296-157">Daher muss die neue Design-Engine diese Klasse nur erweitern und Folgendes implementieren:</span><span class="sxs-lookup"><span data-stu-id="2b296-157">Thus, new Theme Engine need only extend this class and implement the following:</span></span>

#### <a name="mandatory-implementations"></a><span data-ttu-id="2b296-158">Obligatorische Implementierungen</span><span class="sxs-lookup"><span data-stu-id="2b296-158">Mandatory implementations</span></span>

<span data-ttu-id="2b296-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span><span class="sxs-lookup"><span data-stu-id="2b296-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span></span>

<span data-ttu-id="2b296-160">Legen Sie für die gegebene Eigenschaft, die durch identifiziert werden kann, ihren aktuellen Zustandswert auf dem Zielhost von `ThemeStateProperty.Name` GameObject fest (d. h.</span><span class="sxs-lookup"><span data-stu-id="2b296-160">For the given property, which can be identified by `ThemeStateProperty.Name`, set its current state value on the targeted GameObject host (i.e</span></span> <span data-ttu-id="2b296-161">Legen Sie die Materialfarbe usw. fest.</span><span class="sxs-lookup"><span data-stu-id="2b296-161">set the material color, etc).</span></span> <span data-ttu-id="2b296-162">Der *Index* gibt den aktuellen Zustandswert für den Zugriff und den Prozentsatz *(* float zwischen 0 und 1) an, der zur Beschleunigung/Lerping zwischen Werten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2b296-162">The *index* indicates the current state value to access and the *percentage*, a float between 0 and 1, is used for easing/lerping between values.</span></span>

<span data-ttu-id="2b296-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span><span class="sxs-lookup"><span data-stu-id="2b296-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span></span>

<span data-ttu-id="2b296-164">Geben Sie für die gegebene Eigenschaft, die durch identifiziert werden kann, den aktuellen Wert zurück, der für das `ThemeStateProperty.Name` Zielhost-GameObject festgelegt ist (d. h.</span><span class="sxs-lookup"><span data-stu-id="2b296-164">For the given property, which can be identified by `ThemeStateProperty.Name`, return the current value set on the targeted Host  GameObject (i.e</span></span> <span data-ttu-id="2b296-165">die aktuelle Materialfarbe, den aktuellen lokalen Positionsoffset usw.).</span><span class="sxs-lookup"><span data-stu-id="2b296-165">the current material color, the current local position offset, etc).</span></span> <span data-ttu-id="2b296-166">Dies wird in erster Linie zum Zwischenspeichern des Startwerts bei der Beschleunigung zwischen Zuzuständen verwendet.</span><span class="sxs-lookup"><span data-stu-id="2b296-166">This is primarily used for caching the start value when easing between states.</span></span>

<span data-ttu-id="2b296-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span><span class="sxs-lookup"><span data-stu-id="2b296-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span></span>

<span data-ttu-id="2b296-168">Gibt ein [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -Objekt zurück, das die Standardeigenschaften und die Konfiguration definiert, die für das benutzerdefinierte Design erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="2b296-168">Returns a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object that defines the default properties and configuration needed for the custom theme</span></span>

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

<span data-ttu-id="2b296-169">Geschützte Variante der öffentlichen Definition, mit Ausnahme des bereitgestellten ThemePropertyValue, das festgelegt werden soll, anstatt die Index- `SetValue()` und/oder Prozentkonfiguration zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2b296-169">Protected variant of the public `SetValue()` definition, except provided ThemePropertyValue to set instead of directing to use index and/or percentage configuration.</span></span>

#### <a name="recommended-overrides"></a><span data-ttu-id="2b296-170">Empfohlene Außerkraftsetzungen</span><span class="sxs-lookup"><span data-stu-id="2b296-170">Recommended overrides</span></span>

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

<span data-ttu-id="2b296-171">Führen Sie hier alle Initialisierungsschritte aus, die auf den bereitgestellten *GameObject-Parameter* abzielen, und verwenden Sie die Eigenschaften und Konfigurationen, die im *ThemeDefinition-Parameter definiert* sind.</span><span class="sxs-lookup"><span data-stu-id="2b296-171">Perform any initialization steps here targeting the provided *GameObject* parameter and using the properties and configurations defined in the *ThemeDefinition* parameter.</span></span> <span data-ttu-id="2b296-172">Es wird empfohlen, am `base.Init(host, settings)` Anfang einer Außerkraftsetzung auf zu rufen.</span><span class="sxs-lookup"><span data-stu-id="2b296-172">It is recommended to call `base.Init(host, settings)` at the beginning of an override.</span></span>

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

<span data-ttu-id="2b296-173">Wenn die benutzerdefinierte Design-Engine die Beschleunigung zwischen Werten unterstützen kann, die über die -Eigenschaft konfiguriert [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) wird.</span><span class="sxs-lookup"><span data-stu-id="2b296-173">If the custom Theme Engine can support easing between values which is configured via the [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) property.</span></span>

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

<span data-ttu-id="2b296-174">Wenn die benutzerdefinierte Design-Engine die Ausrichtung auf Shadereigenschaften unterstützen kann.</span><span class="sxs-lookup"><span data-stu-id="2b296-174">If the custom Theme Engine can support targeting shader properties.</span></span> <span data-ttu-id="2b296-175">Es wird empfohlen, von zu erweitern, um von der vorhandenen Infrastruktur zu profitieren, um Shadereigenschaften effizient über [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) [MaterialPropertyBlocks zu festlegen/zu erhalten.](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)</span><span class="sxs-lookup"><span data-stu-id="2b296-175">It is recommended to extend from [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) to benefit from the existing infrastructure to efficiently set/get shader properties via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span> <span data-ttu-id="2b296-176">Die Shader-Eigenschaftsinformationen werden in jedem über [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) und [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) gespeichert.</span><span class="sxs-lookup"><span data-stu-id="2b296-176">The shader property information is stored in each [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) and [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName).</span></span>

> [!NOTE]
> <span data-ttu-id="2b296-177">Wenn Sie erweitern, kann es auch nützlich sein, [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) über neue zu *überschreiben.*</span><span class="sxs-lookup"><span data-stu-id="2b296-177">If extending [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme), it can also be useful to override the [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) via *new*.</span></span>
>
> <span data-ttu-id="2b296-178">Beispielcode: `protected new const string DefaultShaderProperty = "_Color";`</span><span class="sxs-lookup"><span data-stu-id="2b296-178">Example code: `protected new const string DefaultShaderProperty = "_Color";`</span></span>
>
> <span data-ttu-id="2b296-179">Darüber hinaus erweitern die folgenden Klassen unten die -Klasse, die [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) [wieder MaterialPropertyBlocks verwendet,](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) um Shader-Eigenschaftswerte zu ändern.</span><span class="sxs-lookup"><span data-stu-id="2b296-179">Furthermore, the following classes below extend the [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) class which again uses [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) to modify shader property values.</span></span> <span data-ttu-id="2b296-180">Dieser Ansatz [hilft bei der Leistung,](https://docs.unity3d.com/Manual/DrawCallBatching.html) *da MaterialPropertyBlocks* keine neuen Instanzmaterialien erstellt, wenn sich Werte ändern.</span><span class="sxs-lookup"><span data-stu-id="2b296-180">This approach [helps performance](https://docs.unity3d.com/Manual/DrawCallBatching.html) because *MaterialPropertyBlocks* do not create new instanced materials when values change.</span></span> <span data-ttu-id="2b296-181">Der Zugriff auf die typischen Eigenschaften der [Material-Klasse](https://docs.unity3d.com/ScriptReference/Material.html) gibt jedoch keine erwarteten Werte zurück.</span><span class="sxs-lookup"><span data-stu-id="2b296-181">However, accessing the typical [Material](https://docs.unity3d.com/ScriptReference/Material.html) class properties will not return expected values.</span></span> <span data-ttu-id="2b296-182">Verwenden *von MaterialPropertyBlocks* zum Erhalten und Überprüfen aktueller Materialeigenschaftswerte (d. h.</span><span class="sxs-lookup"><span data-stu-id="2b296-182">Use *MaterialPropertyBlocks* to get and validate current material property values (i.e</span></span> <span data-ttu-id="2b296-183">*_Color* oder *_MainTex*).</span><span class="sxs-lookup"><span data-stu-id="2b296-183">*_Color* or *_MainTex*).</span></span>
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

<span data-ttu-id="2b296-184">Leitet das Design an, alle geänderten Eigenschaften auf ihre ursprünglichen Werte zurückzusetzen, die auf dem Host GameObject festgelegt wurden, als diese Design-Engine initialisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="2b296-184">Directs the theme to reset any modified properties back to their original values that were set on the host GameObject when this theme engine was initialized.</span></span>  

### <a name="custom-theme-engine-example"></a><span data-ttu-id="2b296-185">Beispiel für benutzerdefinierte Design-Engine</span><span class="sxs-lookup"><span data-stu-id="2b296-185">Custom theme engine example</span></span>

<span data-ttu-id="2b296-186">Die folgende Klasse ist ein Beispiel für eine benutzerdefinierte neue Design-Engine.</span><span class="sxs-lookup"><span data-stu-id="2b296-186">The class below is an example of a custom new Theme Engine.</span></span> <span data-ttu-id="2b296-187">Diese Implementierung findet eine [MeshRenderer-Komponente](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) für das initialisierte Hostobjekt und kontrolliert die Sichtbarkeit basierend auf dem aktuellen Zustand.</span><span class="sxs-lookup"><span data-stu-id="2b296-187">This implementation will find a [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) component on the initialized host object and control its visibility based on the current state.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

// This class demonstrates a custom theme to control a Host's MeshRenderer visibility
public class MeshVisibilityTheme : InteractableThemeBase
{
    // Bool visibility does not make sense for lerping
    public override bool IsEasingSupported => false;

    // No material or shaders are being modified
    public override bool AreShadersSupported => false;

    // Cache reference to the MeshRenderer component on our Host
    private MeshRenderer meshRenderer;

    public MeshVisibilityTheme()
    {
        Types = new Type[] { typeof(MeshRenderer) };
        Name = "Mesh Visibility Theme";
    }

    // Define a default configuration to simplify initialization of this theme engine
    // There is only one state property with a value per available state
    // This state property is a boolean that defines whether the renderer is enabled
    public override ThemeDefinition GetDefaultThemeDefinition()
    {
        return new ThemeDefinition()
        {
            ThemeType = GetType(),
            StateProperties = new List<ThemeStateProperty>()
            {
                new ThemeStateProperty()
                {
                    Name = "Mesh Visible",
                    Type = ThemePropertyTypes.Bool,
                    Values = new List<ThemePropertyValue>(),
                    Default = new ThemePropertyValue() { Bool = true }
                },
            },
            CustomProperties = new List<ThemeProperty>()
        };
    }

    // When initializing, cache a reference to the MeshRenderer component
    public override void Init(GameObject host, ThemeDefinition definition)
    {
        base.Init(host, definition);

        meshRenderer = host.GetComponent<MeshRenderer>();
    }

    // Get the current state of the MeshRenderer visibility
    public override ThemePropertyValue GetProperty(ThemeStateProperty property)
    {
        return new ThemePropertyValue()
        {
            Bool = meshRenderer.enabled
        };
    }

    // Update the MeshRenderer visibility based on the property state value data
    public override void SetValue(ThemeStateProperty property, int index, float percentage)
    {
        meshRenderer.enabled = property.Values[index].Bool;
    }
}
```

## <a name="end-to-end-example"></a><span data-ttu-id="2b296-188">Vollständiges Beispiel</span><span class="sxs-lookup"><span data-stu-id="2b296-188">End-to-end example</span></span>

<span data-ttu-id="2b296-189">Das folgende Codebeispiel erweitert die benutzerdefinierte Design-Engine, die im früheren Abschnitt definiert wurde, und veranschaulicht, wie dieses Design zur Laufzeit kontrolliert wird.</span><span class="sxs-lookup"><span data-stu-id="2b296-189">Extending off of the custom Theme Engine defined in the earlier section, the code example below demonstrates how to control this theme at runtime.</span></span> <span data-ttu-id="2b296-190">Insbesondere wird beschrieben, wie sie den aktuellen Zustand für das Design festlegen, damit die MeshRenderer-Sichtbarkeit entsprechend aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="2b296-190">In particular, how to set the current state on the theme so the MeshRenderer visibility is updated appropriately.</span></span>

> [!NOTE]
> <span data-ttu-id="2b296-191">`theme.OnUpdate(state,force)` sollte in der Regel in der Update()-Methode aufgerufen werden, um Design-Engines zu unterstützen, die Beschleunigung/Lerping zwischen Werten nutzen.</span><span class="sxs-lookup"><span data-stu-id="2b296-191">`theme.OnUpdate(state,force)` should generally be called in the Update() method to support Theme Engines that utilize easing/lerping between values.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

public class MeshVisibilityController : MonoBehaviour
{
    private MeshVisibilityTheme themeEngine;
    private bool hideMesh = false;

    private void Start()
    {
        // Define the default configuration. State 0 will be on while State 1 will be off
        var themeDefinition = ThemeDefinition.GetDefaultThemeDefinition<MeshVisibilityTheme>().Value;
        themeDefinition.StateProperties[0].Values = new List<ThemePropertyValue>()
        {
            new ThemePropertyValue() { Bool = true }, // show state
            new ThemePropertyValue() { Bool = false }, // hide state
        };

        // Create the actual Theme engine and initialize it with the GameObject we are attached to
        themeEngine = (MeshVisibilityTheme)InteractableThemeBase.CreateAndInitTheme(themeDefinition, this.gameObject);
    }

    private void Update()
    {
        // Update the theme engine to set our MeshRenderer visibility
        // based on our current state (i.e the hideMesh variable)
        themeEngine.OnUpdate(Convert.ToInt32(hideMesh));
    }

    public void ToggleVisibility()
    {
        // Alternate state of visibility
        hideMesh = !hideMesh;
    }
}
```

## <a name="see-also"></a><span data-ttu-id="2b296-192">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2b296-192">See also</span></span>

- [<span data-ttu-id="2b296-193">Interaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="2b296-193">Interactable</span></span>](interactable.md)
