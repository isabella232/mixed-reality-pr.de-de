---
title: Visuelle Designs
description: Übersicht über visuelle Designs flexible Steuerung von UX-Ressourcen in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, MRTK-Designs,
ms.openlocfilehash: f7e0b10f51947884c4d23191fd147315084c5295e9b48953bb5de10b7cbc0d22
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223968"
---
# <a name="visual-themes"></a>Visuelle Designs

Designs ermöglichen eine flexible Steuerung von UX-Ressourcen als Reaktion auf verschiedene Statusübergänge. Dies kann das Ändern der Farbe einer Schaltfläche, das Ändern der Größe eines Elements als Reaktion auf den Fokus usw. umfassen. Das Visual Themes-Framework besteht aus zwei Hauptteilen: 1) Konfiguration und 2) Runtime-Engines.

[Designkonfigurationen](#theme-configuration) sind Definitionen von Eigenschaften und Typen, während [Design-Engines](#theme-engines) Klassen sind, die die Konfigurationen nutzen und die Logik zum Aktualisieren von Transformationen, Materialien und mehr zur Laufzeit implementieren.

## <a name="theme-configuration"></a>Designkonfiguration

Designkonfigurationen sind [ScriptableObjects,](https://docs.unity3d.com/Manual/class-ScriptableObject.html) die definieren, wie Design-Engines zur Laufzeit initialisiert werden. Sie definieren, welche Eigenschaften und Werte als Reaktion auf Eingabe- oder andere Statusänderungen verwendet werden sollen, wenn die App ausgeführt wird. Als [ScriptableObjects-Objekte](https://docs.unity3d.com/Manual/class-ScriptableObject.html) können Designkonfigurationen einmal definiert und dann für verschiedene UX-Komponenten wiederverwendet werden.

So erstellen Sie ein neues [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) Medienobjekt:

1) Rechtsklick im *Project Fenster*
1) Wählen **Sie Create** Mixed Reality Toolkit Theme  >  **(Mixed Reality**  >  **Toolkitdesign erstellen)** aus.

Beispielressourcen für die Designkonfiguration finden Sie unter `MRTK/SDK/Features/UX/Interactable/Themes` .

![ScriptableObject-Designbeispiel im Inspektor](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a>Zustände

Wenn Sie eine neue [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) erstellen, müssen Sie zunächst festlegen, welche Zustände verfügbar sind. Die *States-Eigenschaft* gibt an, wie viele Werte eine Designkonfiguration definieren muss, da es einen Wert pro Zustand gibt. In der obigen Beispielbildansicht sind die [Standardzustände, die für die Interaktionsfähige](interactable.md#general-input-settings) Komponente definiert *sind, Default*, *Focus*, *Pressed* und *Disabled*. Diese werden in der `DefaultInteractableStates` Medienobjektdatei (Assets/MRTK/SDK/Features/UX/Interactable/States) definiert.

So erstellen Sie ein neues [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) Medienobjekt:

1) Rechtsklick im *Project Fenster*
1) Wählen **Sie Create** Mixed Reality Toolkit State  >    >  **(Mixed Reality Toolkitstatus erstellen) aus.**

![StatusskriptableObject-Beispiel im Inspektor](../images/interactable/DefaultInteractableStates.png)

Ein [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject definiert sowohl die Liste der Status als auch den Typ von *StateModel,* der für diese Zustände erstellt werden soll. Ein *StateModel* ist eine Klasse, die [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) die Zustandsautomatenlogik erweitert und implementiert, um den aktuellen Zustand zur Laufzeit zu generieren. Der aktuelle Zustand dieser Klasse wird von Design-Engines zur Laufzeit in der Regel verwendet, um zu bestimmen, welche Werte für Materialeigenschaften, GameObject-Transformationen und vieles mehr festgelegt werden sollen.

### <a name="theme-engine-properties"></a>Eigenschaften der Design-Engine

Außerhalb von *States* definiert ein [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) Medienobjekt auch eine Liste von Design-Engines und die zugehörigen Eigenschaften für diese Engines. Eine [Design-Engine](#theme-engines) definiert erneut die Logik zum Festlegen der richtigen Werte für ein GameObject zur Laufzeit.

Ein [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) Medienobjekt kann mehrere Design-Engines definieren, um anspruchsvolle visuelle Statusübergänge für mehrere GameObject-Eigenschaften zu erreichen.

**Designlaufzeit**

Definiert den Klassentyp der Design-Engine, die erstellt wird.

**Lockerung**

Einige *Design-Engines* unterstützen die Beschleunigung zwischen Zuständen, wenn sie ihre Eigenschaft [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) als true definieren. Beispiel: Lerping zwischen zwei Farben, wenn eine Zustandsänderung auftritt. *Die Dauer* definiert in Sekunden, wie lange vom Startwert zum Endwert gelockert werden soll, und die *Animationskurve* definiert die Änderungsrate während dieses Zeitraums.

**Shadereigenschaften**

Einige *Design-Engines* ändern bestimmte Shadereigenschaften zur Laufzeit, wenn sie ihre Eigenschaft [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) als true definieren. Die Felder *Shader* und *Eigenschaft* definieren die Shadereigenschaft, die als Ziel festgelegt werden soll.

### <a name="create-a-theme-configuration-via-code"></a>Erstellen einer Designkonfiguration über Code

Im Allgemeinen ist es einfacher, Designkonfigurationen über den Unity-Inspektor zu entwerfen, aber es gibt Fälle, in denen Designs zur Laufzeit dynamisch über Code generiert werden müssen. Der folgende Codeausschnitt enthält ein Beispiel für die Durchführung dieser Aufgabe.

Um die Entwicklung zu beschleunigen, sind die folgenden Hilfsmethoden nützlich, um das Setup zu vereinfachen.

[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) – erstellt ein neues States ScriptableObject mit den vier Standardzustandswerten, die in der [Interactable-Komponente](interactable.md) verwendet werden.

[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) – Jede Design-Engine definiert eine Standardkonfiguration mit den richtigen Eigenschaften, die für diesen Designruntimetyp erforderlich sind. Dieses Hilfssystem erstellt eine Definition für den angegebenen Design-Engine-Typ.

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

## <a name="theme-engines"></a>Design-Engines

Eine [Design-Engine](#theme-engines) ist eine Klasse, die sich von der [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) -Klasse erstreckt. Diese Klassen werden zur Laufzeit instanziiert und mit einem -Objekt konfiguriert, [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) wie zuvor beschrieben.

### <a name="default-theme-engines"></a>Standarddesign-Engines

MRTK wird mit einem Standardsatz von Design-Engines ausgeliefert, die unten aufgeführt sind:

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

Die Standarddesign-Engines finden Sie unter `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .

### <a name="custom-theme-engines"></a>Benutzerdefinierte Design-Engines

Wie bereits erwähnt, wird eine Design-Engine als klasse definiert, die sich von der [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) -Klasse erstreckt. Daher muss die neue Design-Engine nur diese Klasse erweitern und Folgendes implementieren:

#### <a name="mandatory-implementations"></a>Obligatorische Implementierungen

`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)

Legen Sie für die angegebene Eigenschaft, die durch identifiziert werden `ThemeStateProperty.Name` kann, ihren aktuellen Zustandswert auf dem GameObject-Zielhost fest (d. h. legen Sie die Materialfarbe fest, usw.). Der *Index* gibt den aktuellen Zustandswert an, auf den zugegriffen werden soll, und der *Prozentsatz*, ein Gleitkommawert zwischen 0 und 1, wird für die Beschleunigung/Lerping zwischen Werten verwendet.

`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)

Geben Sie für die angegebene Eigenschaft, die durch identifiziert werden `ThemeStateProperty.Name` kann, den aktuellen Wert zurück, der für das Zielhost-GameObject festgelegt ist (d.h. die aktuelle Materialfarbe, der aktuelle lokale Positionsoffset usw.). Dies wird in erster Linie zum Zwischenspeichern des Startwerts bei der Beschleunigung zwischen Zuständen verwendet.

`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)

Gibt ein [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -Objekt zurück, das die Standardeigenschaften und die Konfiguration definiert, die für das benutzerdefinierte Design erforderlich sind.

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

Geschützte Variante der öffentlichen Definition, mit Ausnahme der `SetValue()` bereitgestellten ThemePropertyValue, die festgelegt werden soll, anstatt an die Verwendung der Index- und/oder Prozentkonfiguration weiterzuleiten.

#### <a name="recommended-overrides"></a>Empfohlene Außerkraftsetzungen

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

Führen Sie hier alle Initialisierungsschritte für den bereitgestellten *GameObject-Parameter* aus, und verwenden Sie dabei die im *ThemeDefinition-Parameter* definierten Eigenschaften und Konfigurationen. Es wird empfohlen, `base.Init(host, settings)` am Anfang einer Außerkraftsetzung aufzurufen.

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

Wenn die benutzerdefinierte Design-Engine die Beschleunigung zwischen Werten unterstützen kann, die über die -Eigenschaft konfiguriert [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) werden.

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

Wenn die benutzerdefinierte Design-Engine Shadereigenschaften unterstützen kann. Es wird empfohlen, von zu [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) erweitern, um von der vorhandenen Infrastruktur zu profitieren, um Shadereigenschaften effizient über [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)festzulegen bzw. abzurufen. Die Shadereigenschafteninformationen werden jeweils über und in [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) gespeichert.

> [!NOTE]
> Beim Erweitern [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) von kann es auch nützlich sein, [interactableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) über *neue* zu überschreiben.
>
> Beispielcode: `protected new const string DefaultShaderProperty = "_Color";`
>
> Darüber hinaus erweitern die folgenden Klassen die [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) -Klasse, die erneut [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) verwendet, um shader-Eigenschaftswerte zu ändern. Dieser Ansatz [hilft bei](https://docs.unity3d.com/Manual/DrawCallBatching.html) der Leistung, da *MaterialPropertyBlocks* keine neuen instanzierten Materialien erstellt, wenn sich Werte ändern. Beim Zugriff auf die typischen Eigenschaften der [Material-Klasse](https://docs.unity3d.com/ScriptReference/Material.html) werden jedoch keine erwarteten Werte zurückgegeben. Verwenden von *MaterialPropertyBlocks* zum Abrufen und Überprüfen aktueller Materialeigenschaftswerte (d. h. *_Color* oder *_MainTex*).
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

Weist das Design an, alle geänderten Eigenschaften auf ihre ursprünglichen Werte zurückzusetzen, die auf dem Host gameObject festgelegt wurden, als diese Design-Engine initialisiert wurde.  

### <a name="custom-theme-engine-example"></a>Beispiel für eine benutzerdefinierte Design-Engine

Die folgende Klasse ist ein Beispiel für eine benutzerdefinierte neue Design-Engine. Diese Implementierung findet eine [MeshRenderer-Komponente](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) im initialisierten Hostobjekt und steuert die Sichtbarkeit basierend auf dem aktuellen Zustand.

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

## <a name="end-to-end-example"></a>Vollständiges Beispiel

Das folgende Codebeispiel erweitert die benutzerdefinierte Design-Engine, die im vorherigen Abschnitt definiert wurde, und veranschaulicht, wie dieses Design zur Laufzeit gesteuert wird. Insbesondere erfahren Sie, wie Sie den aktuellen Zustand für das Design festlegen, damit die Sichtbarkeit von MeshRenderer entsprechend aktualisiert wird.

> [!NOTE]
> `theme.OnUpdate(state,force)` sollte in der Regel in der Update()-Methode aufgerufen werden, um Design-Engines zu unterstützen, die Beschleunigung/Toleranz zwischen Werten verwenden.

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

## <a name="see-also"></a>Siehe auch

- [Interaktionsfähig](interactable.md)
