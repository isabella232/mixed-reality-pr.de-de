---
title: Zuschnitt-Primitiv
description: Dokumentation zu Clippingprimitiven mit Beispielen in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Clipping primitive,
ms.openlocfilehash: 35b7166045986df34eaf2c23161efc6379160ead
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145206"
---
# <a name="clipping-primitive"></a><span data-ttu-id="03a50-104">Zuschnitt-Primitiv</span><span class="sxs-lookup"><span data-stu-id="03a50-104">Clipping Primitive</span></span>

<span data-ttu-id="03a50-105">Die Verhaltensweisen ermöglichen eine performante , - und -Formausschneidung mit der Möglichkeit, anzugeben, auf welcher Seite des Primitivs (innerhalb oder außerhalb) abgeschnitten werden soll, wenn sie mit [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) MRTK-Shadern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="03a50-105">The [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors allow for performant [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) shape clipping with the ability to specify which side of the primitive to clip against (inside or outside) when used with MRTK shaders.</span></span>

![Primitive Clipping-Klammern](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> <span data-ttu-id="03a50-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Verwenden [Sie Clip/Discard-Anweisungen](https://developer.download.nvidia.com/cg/clip.html) in Shadern, und deaktivieren Sie die Fähigkeit von Unity, beschnittene Renderer als Batch zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="03a50-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [clip/discard](https://developer.download.nvidia.com/cg/clip.html) instructions within shaders and disable Unity's ability to batch clipped renderers.</span></span> <span data-ttu-id="03a50-108">Berücksichtigen Sie diese Auswirkungen auf die Leistung bei der Verwendung von Clippingprimitiven.</span><span class="sxs-lookup"><span data-stu-id="03a50-108">Take these performance implications in mind when utilizing clipping primitives.</span></span>

<span data-ttu-id="03a50-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) und können verwendet [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) werden, um primitive Clippingeigenschaften einfach zu steuern.</span><span class="sxs-lookup"><span data-stu-id="03a50-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) can be used to easily control clipping primitive properties.</span></span> <span data-ttu-id="03a50-110">Verwenden Sie diese Komponenten mit den folgenden Shadern, um Clippingszenarien zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="03a50-110">Use these components with the following shaders to leverage clipping scenarios.</span></span>

- <span data-ttu-id="03a50-111">*Mixed Reality Toolkit/Standard*</span><span class="sxs-lookup"><span data-stu-id="03a50-111">*Mixed Reality Toolkit/Standard*</span></span>
- <span data-ttu-id="03a50-112">*Mixed Reality Toolkit/TextMeshPro*</span><span class="sxs-lookup"><span data-stu-id="03a50-112">*Mixed Reality Toolkit/TextMeshPro*</span></span>
- <span data-ttu-id="03a50-113">*Mixed Reality Toolkit/Text3DShader*</span><span class="sxs-lookup"><span data-stu-id="03a50-113">*Mixed Reality Toolkit/Text3DShader*</span></span>

## <a name="examples"></a><span data-ttu-id="03a50-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="03a50-114">Examples</span></span>

<span data-ttu-id="03a50-115">Die **ClippingExamples-** und **MaterialGallery-Szenen** veranschaulichen die Verwendung des Verhaltens und finden Sie [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) unter: MRTK/Examples/Demos/StandardShader/Scenes/</span><span class="sxs-lookup"><span data-stu-id="03a50-115">The **ClippingExamples** and **MaterialGallery** scenes demonstrate usage of the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="03a50-116">Erweiterte Nutzung</span><span class="sxs-lookup"><span data-stu-id="03a50-116">Advanced Usage</span></span>

<span data-ttu-id="03a50-117">Standardmäßig kann nur ein [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [Renderer gleichzeitig](https://docs.unity3d.com/ScriptReference/Renderer.html) abgeschnitten werden.</span><span class="sxs-lookup"><span data-stu-id="03a50-117">By default only one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) can clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) at a time.</span></span> <span data-ttu-id="03a50-118">Wenn ihr Projekt mehr als einen benötigt, um einen Renderer zu beeinflussen, veranschaulicht der folgende Beispielcode, [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) wie dies erreicht werden kann. [](https://docs.unity3d.com/ScriptReference/Renderer.html)</span><span class="sxs-lookup"><span data-stu-id="03a50-118">If your project requires more than one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) to influence a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="03a50-119">Wenn ein [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Renderer mehrere [Beschneidungen verwendet,](https://docs.unity3d.com/ScriptReference/Renderer.html) werden die Anweisungen für den Pixel-Shader erhöht, und die Leistung wird dadurch verbessert.</span><span class="sxs-lookup"><span data-stu-id="03a50-119">Having multiple [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="03a50-120">Erstellen Sie ein Profil für diese Änderungen in Ihrem Projekt.</span><span class="sxs-lookup"><span data-stu-id="03a50-120">Please profile these changes within your project.</span></span>

<span data-ttu-id="03a50-121">*Es wird dargestellt, wie sie [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) zwei unterschiedliche Clips für ein Rendern haben. Beispiel: [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) und [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) zur gleichen Zeit:*</span><span class="sxs-lookup"><span data-stu-id="03a50-121">*How to have two different [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) and [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> <span data-ttu-id="03a50-122">Durch die obige Änderung kommt es zu einer zusätzlichen Shaderkompilierungszeit.</span><span class="sxs-lookup"><span data-stu-id="03a50-122">The above change will incur additional shader compilation time.</span></span>

<span data-ttu-id="03a50-123">*Es wird dargestellt, wie Zwei desselben [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Clips ein Rendern. Beispiel: zwei [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) gleichzeitig:*</span><span class="sxs-lookup"><span data-stu-id="03a50-123">*How to have two of the same [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example two [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// 1) Add the below MonoBehaviour to your project:

[ExecuteInEditMode]
public class SecondClippingBox : ClippingBox
{
    /// <inheritdoc />
    protected override string Keyword
    {
        get { return "_CLIPPING_BOX2"; }
    }

    /// <inheritdoc />
    protected override string ClippingSideProperty
    {
        get { return "_ClipBoxSide2"; }
    }

    /// <inheritdoc />
    protected override void Initialize()
    {
        base.Initialize();

        clipBoxSizeID = Shader.PropertyToID("_ClipBoxSize2");
        clipBoxInverseTransformID = Shader.PropertyToID("_ClipBoxInverseTransform2");
    }
}

// 2) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) add the following multi_compile pragma:

#pragma multi_compile _ _CLIPPING_BOX2

// 3) In the same shader change:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX)

// to:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX) || defined(_CLIPPING_BOX2)

// 4) In the same shader add the following shader variables:

#if defined(_CLIPPING_BOX2)
    fixed _ClipBoxSide2;
    float4 _ClipBoxSize2;
    float4x4 _ClipBoxInverseTransform2;
#endif

// 5) In the same shader change:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif

// to:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif
#if defined(_CLIPPING_BOX2)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize2.xyz, _ClipBoxInverseTransform2) * _ClipBoxSide2);
#endif
```

<span data-ttu-id="03a50-124">Fügen Sie abschließend ihrer Szene eine - und eine SecondClippingBox-Komponente hinzu, und geben [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) Sie denselben Renderer für beide Felder an.</span><span class="sxs-lookup"><span data-stu-id="03a50-124">Finally, add a [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) and SecondClippingBox component to your scene and specify the same renderer for both boxes.</span></span> <span data-ttu-id="03a50-125">Der Renderer sollte nun von beiden Feldern gleichzeitig abgeschnitten werden.</span><span class="sxs-lookup"><span data-stu-id="03a50-125">The renderer should now be clipped by both boxes simultaneously.</span></span>

## <a name="see-also"></a><span data-ttu-id="03a50-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="03a50-126">See also</span></span>

- [<span data-ttu-id="03a50-127">MRTK-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="03a50-127">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
