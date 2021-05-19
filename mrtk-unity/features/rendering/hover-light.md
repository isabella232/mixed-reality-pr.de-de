---
title: Schwebelicht
description: Dokumentation zu HoverLight mit Beispielen in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Hover Light,
ms.openlocfilehash: b98dff0dd3ff0312f6ce607a5fb8a26f94959ff2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145176"
---
# <a name="hover-light"></a><span data-ttu-id="b4c2b-104">Schwebelicht</span><span class="sxs-lookup"><span data-stu-id="b4c2b-104">Hover Light</span></span>

<span data-ttu-id="b4c2b-105">Ein ist ein Fluent Design System Paradigma, das ein Punktlicht imitiert, das auf die Oberfläche eines [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) Objekts zeigen soll. [](https://www.microsoft.com/design/fluent/) [](https://docs.unity3d.com/Manual/Lighting.html)</span><span class="sxs-lookup"><span data-stu-id="b4c2b-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="b4c2b-106">Häufig für weit entfernte Interaktionen verwendet, kann die Anwendung die Eigenschaften eines Hoverlichts über die Komponente [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) steuern.</span><span class="sxs-lookup"><span data-stu-id="b4c2b-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="b4c2b-107">Damit ein Material von einem Mixed Reality [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) *Toolkit/Standard-Shader* beeinflusst wird, muss die *Eigenschaft Hover Light* aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="b4c2b-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="b4c2b-108">Der MRTK/Standard-Shader unterstützt standardmäßig bis zu zwei, wird aber skaliert, um vier und dann zehn zu unterstützen, wenn der Szene weitere [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) Beleuchtungen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="b4c2b-108">The MRTK/Standard shader supports up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) by default, but will scale to support four and then ten as more lights are added to the scene.</span></span>

## <a name="examples"></a><span data-ttu-id="b4c2b-109">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b4c2b-109">Examples</span></span>

<span data-ttu-id="b4c2b-110">Die meisten Szenen im MRTK verwenden eine [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) .</span><span class="sxs-lookup"><span data-stu-id="b4c2b-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="b4c2b-111">Den häufigsten Verwendungsfall finden Sie unter MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab.</span><span class="sxs-lookup"><span data-stu-id="b4c2b-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

<span data-ttu-id="b4c2b-112">Die **HoverLightExamples-Szene** veranschaulicht auch die Verwendung von Verhaltensweisen und finden Sie [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) unter: MRTK/Examples/Demos/StandardShader/Scenes/</span><span class="sxs-lookup"><span data-stu-id="b4c2b-112">The **HoverLightExamples** scene also demonstrates usage of [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="b4c2b-113">Erweiterte Nutzung</span><span class="sxs-lookup"><span data-stu-id="b4c2b-113">Advanced Usage</span></span>

<span data-ttu-id="b4c2b-114">Nur zehn [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) können ein Material [gleichzeitig](https://docs.unity3d.com/ScriptReference/Material.html) beleuchten.</span><span class="sxs-lookup"><span data-stu-id="b4c2b-114">Only ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="b4c2b-115">Wenn Ihr Projekt mehr als zehn benötigt, um ein Material zu beeinflussen, veranschaulicht der folgende Beispielcode, [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) wie dies erreicht werden kann. [](https://docs.unity3d.com/ScriptReference/Material.html)</span><span class="sxs-lookup"><span data-stu-id="b4c2b-115">If your project requires more than ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="b4c2b-116">Wenn ein [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) Material mit vielen Farben [belichtet wird,](https://docs.unity3d.com/ScriptReference/Material.html) werden die Anweisungen für Denkpixel-Shader erhöht, was sich auf die Leistung auswirken wird.</span><span class="sxs-lookup"><span data-stu-id="b4c2b-116">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="b4c2b-117">**Erstellen Sie ein Profil für diese Änderungen in Ihrem Projekt.**</span><span class="sxs-lookup"><span data-stu-id="b4c2b-117">**Please profile these changes within your project.**</span></span>

<span data-ttu-id="b4c2b-118">*Erhöhen der Anzahl verfügbarer Daten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) von zehn auf zwölf.*</span><span class="sxs-lookup"><span data-stu-id="b4c2b-118">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from ten to twelve.*</span></span>

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
> <span data-ttu-id="b4c2b-119">Wenn Unity eine Warnung wie unten protokolliert, müssen Sie Unity neu starten, bevor Ihre Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="b4c2b-119">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="b4c2b-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b4c2b-120">See also</span></span>

* [<span data-ttu-id="b4c2b-121">MRTK-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="b4c2b-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
