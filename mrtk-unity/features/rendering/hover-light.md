---
title: Licht mit Dem Hover
description: Dokumentation zu HoverLight mit Beispielen in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Hover Light,
ms.openlocfilehash: ed45d3345931376283cfca2372ac57459c777f6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176736"
---
# <a name="hover-light"></a>Licht mit Dem Hover

Ein ist ein Fluent Design System Paradigma, das ein Punktlicht imitiert, das auf die Oberfläche eines [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) Objekts zeigen soll. [](https://www.microsoft.com/design/fluent/) [](https://docs.unity3d.com/Manual/Lighting.html) Häufig für weit entfernte Interaktionen verwendet, kann die Anwendung die Eigenschaften eines Hoverlichts über die Komponente [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) steuern.

Damit ein Material von einem Mixed Reality [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) *Toolkit/Standard-Shader* beeinflusst wird, muss die *Eigenschaft Hover Light* aktiviert werden.

> [!Note]
> Der MRTK/Standard-Shader unterstützt standardmäßig bis zu zwei, wird aber skaliert, um vier und dann zehn zu unterstützen, wenn der Szene weitere [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) Beleuchtungen hinzugefügt werden.

## <a name="examples"></a>Beispiele

Die meisten Szenen im MRTK verwenden eine [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) . Den häufigsten Verwendungsfall finden Sie unter MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab.

Die **HoverLightExamples-Szene** veranschaulicht auch die Verwendung von Verhaltensweisen und finden Sie [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) unter: MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>Erweiterte Nutzung

Nur zehn [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) können ein Material [gleichzeitig](https://docs.unity3d.com/ScriptReference/Material.html) beleuchten. Wenn Ihr Projekt mehr als zehn benötigt, um ein Material zu beeinflussen, zeigt der folgende Beispielcode, [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) wie dies erreicht werden kann. [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!Note]
> Wenn ein [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) Material mit vielen Farben [belichtet wird,](https://docs.unity3d.com/ScriptReference/Material.html) werden die Anweisungen für Denkpixel-Shader erhöht, was sich auf die Leistung auswirken wird. **Erstellen Sie ein Profil für diese Änderungen in Ihrem Projekt.**

*Erhöhen der Anzahl verfügbarer Daten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) von zehn auf zwölf.*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 10

// to:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 12

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCountHigh = 10;

// to:

private const int hoverLightCountHigh = 12;
```

> [!NOTE]
> Wenn Unity eine Warnung wie unten protokolliert, müssen Sie Unity neu starten, bevor Ihre Änderungen wirksam werden.
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>Siehe auch

* [MRTK-Standard-Shader](mrtk-standard-shader.md)
