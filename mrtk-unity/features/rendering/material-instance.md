---
title: Materialinstanz
description: Dokumentation zu Material Instance und deren Verwendung in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, MaterialInstance,
ms.openlocfilehash: 216fa72af6bb6caaf47e30c156f7caf1b1dab71e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145210"
---
# <a name="material-instance"></a><span data-ttu-id="a8148-104">Materialinstanz</span><span class="sxs-lookup"><span data-stu-id="a8148-104">Material instance</span></span>

<span data-ttu-id="a8148-105">Das [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) Verhalten hilft bei der Nachverfolgung der Lebensdauer von Instanzmaterial und zerstört automatisch instanzierte Materialien für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="a8148-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="a8148-106">Diese Hilfsprogrammkomponente kann als Ersatz für [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) oder [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a8148-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).</span></span>

> [!NOTE]
> <span data-ttu-id="a8148-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) werden gegenüber der Materialinstanzierung bevorzugt, sind aber nicht immer in allen Szenarien verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a8148-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="a8148-108">Warum kann die Verwendung von [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ein Problem darstellen?</span><span class="sxs-lookup"><span data-stu-id="a8148-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="a8148-109">Wenn Sie den folgenden Code zu einer Unity-Szene hinzufügen und die Nutzung des Arbeitsspeichers der Trefferwiedergabe fortgesetzt wird, wird dies weiter steigen:</span><span class="sxs-lookup"><span data-stu-id="a8148-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

```c#
public class Leak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // Memory leak, the material allocated is not tracked & destroyed.
        cube.GetComponent<Renderer>().material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

> [!NOTE]
> <span data-ttu-id="a8148-110">Das oben genannte Leak-Verhalten **stürzt Unity ab,** wenn es zu lange ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a8148-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="a8148-111">Alternativ können Sie versuchen, das -Verhalten zu [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) verwenden:</span><span class="sxs-lookup"><span data-stu-id="a8148-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

```c#
public class NoLeak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // No memory leak, the material allocated is tracked & destroyed by MaterialInstance.
        cube.EnsureComponent<MaterialInstance>().Material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

## <a name="usage"></a><span data-ttu-id="a8148-112">Verwendung</span><span class="sxs-lookup"><span data-stu-id="a8148-112">Usage</span></span>

<span data-ttu-id="a8148-113">Beim Aufrufen von [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s) von Unity instanziiert Unity automatisch neue Materialien.</span><span class="sxs-lookup"><span data-stu-id="a8148-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="a8148-114">Es liegt in der Verantwortung des Aufrufers, die Materialien zu zerstören, wenn ein Material nicht mehr benötigt wird oder das Spielobjekt zerstört wird.</span><span class="sxs-lookup"><span data-stu-id="a8148-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="a8148-115">Das [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) Verhalten hilft dabei, Materialverluste zu vermeiden und die Materialzuordnungspfade während der Bearbeitungs- und Laufzeit konsistent zu halten.</span><span class="sxs-lookup"><span data-stu-id="a8148-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="a8148-116">Wenn ein [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) nicht verwendet werden kann und ein Material instanziert werden muss, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) kann wie folgt verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="a8148-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

```c#
public class MyBehaviour : MonoBehaviour
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().Material;
        material.color = Color.red;
        ...
    }
}
```

<span data-ttu-id="a8148-117">Wenn mehrere Objekte den Besitz der Materialinstanz benötigen, ist es am besten, den expliziten Besitz für die Verweisnachverfolgung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="a8148-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="a8148-118">(Eine optionale Schnittstelle namens [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) ist vorhanden, um den Besitz zu unterstützen.) Im Folgenden finden Sie ein Beispiel für die Verwendung:</span><span class="sxs-lookup"><span data-stu-id="a8148-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

```c#
public class MyBehaviour : MonoBehaviour,  IMaterialInstanceOwner
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().AcquireMaterial(this);
        material.color = Color.red;
        ...
    }

    private void OnDisable()
    {
        targetRenderer.GetComponent<MaterialInstance>()?.ReleaseMaterial(this)
    }

    public void OnMaterialChanged(MaterialInstance materialInstance)
    {
        // Optional method for when materials change outside of the MaterialInstance.
        ...
    }
}
```

<span data-ttu-id="a8148-119">Weitere Informationen finden Sie in der Beispielverwendung, die innerhalb des Verhaltens veranschaulicht [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) wird.</span><span class="sxs-lookup"><span data-stu-id="a8148-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8148-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a8148-120">See also</span></span>

* [<span data-ttu-id="a8148-121">MRTK-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="a8148-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
