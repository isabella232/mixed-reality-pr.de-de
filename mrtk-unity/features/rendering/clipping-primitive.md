---
title: Zuschnitt-Primitiv
description: Dokumentation zu Clippingprimitiven mit Beispielen in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, Clipping primitive,
ms.openlocfilehash: 1feecbbd51eb80ff6113e66d053f032acb3005b9c7d1debbd5dfd46da0925798
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214412"
---
# <a name="clipping-primitive"></a>Zuschnitt-Primitiv

Die Verhaltensweisen ermöglichen eine performante , - und -Formausschneidung mit der Möglichkeit, anzugeben, auf welcher Seite des Primitivs (innerhalb oder außerhalb) abgeschnitten werden soll, wenn sie mit [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) MRTK-Shadern verwendet wird.

![Primitive Clipping-Klammern](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Verwenden [Sie Clip/Discard-Anweisungen](https://developer.download.nvidia.com/cg/clip.html) in Shadern, und deaktivieren Sie die Fähigkeit von Unity, beschnittene Renderer als Batch zu verwenden. Berücksichtigen Sie diese Auswirkungen auf die Leistung bei der Verwendung von Clippingprimitiven.

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) und können verwendet [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) werden, um primitive Clippingeigenschaften einfach zu steuern. Verwenden Sie diese Komponenten mit den folgenden Shadern, um Clippingszenarien zu nutzen.

- *Mixed Reality Toolkit/Standard*
- *Mixed Reality Toolkit/TextMeshPro*
- *Mixed Reality Toolkit/Text3DShader*

## <a name="examples"></a>Beispiele

Die **ClippingExamples-** und **MaterialGallery-Szenen** veranschaulichen die Verwendung des Verhaltens und finden Sie [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) unter: MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>Erweiterte Nutzung

Standardmäßig kann nur ein [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [Renderer gleichzeitig](https://docs.unity3d.com/ScriptReference/Renderer.html) abgeschnitten werden. Wenn ihr Projekt mehr als eins erfordert, um einen Renderer zu beeinflussen, veranschaulicht der folgende Beispielcode, [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) wie dies erreicht werden kann. [](https://docs.unity3d.com/ScriptReference/Renderer.html)

> [!NOTE]
> Wenn ein [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Renderer mehrere [Beschneidungen verwendet,](https://docs.unity3d.com/ScriptReference/Renderer.html) werden die Anweisungen für den Pixel-Shader erhöht, und die Leistung wird dadurch verbessert. Erstellen Sie ein Profil für diese Änderungen in Ihrem Projekt.

*Es wird dargestellt, wie sie [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) zwei unterschiedliche Clips für ein Rendern haben. Beispiel: [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) und [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) zur gleichen Zeit:*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> Durch die obige Änderung kommt es zu einer zusätzlichen Shaderkompilierungszeit.

*Es wird dargestellt, wie Zwei desselben [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) Clips ein Rendern. Beispiel: zwei [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) gleichzeitig:*

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

Fügen Sie abschließend ihrer Szene eine - und eine SecondClippingBox-Komponente hinzu, und geben [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) Sie denselben Renderer für beide Felder an. Der Renderer sollte nun von beiden Feldern gleichzeitig abgeschnitten werden.

## <a name="see-also"></a>Siehe auch

- [MRTK-Standard-Shader](mrtk-standard-shader.md)
