---
title: Materialinstanz
description: Dokumentation zu Material Instance und deren Verwendung im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, MaterialInstance,
ms.openlocfilehash: ecd8f9e14564cbd03cb6faa848b06ca55a024207
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176719"
---
# <a name="material-instance"></a><span data-ttu-id="ad0ef-104">Materialinstanz</span><span class="sxs-lookup"><span data-stu-id="ad0ef-104">Material instance</span></span>

<span data-ttu-id="ad0ef-105">Das Verhalten spricht für die Nachverfolgung der Lebensdauer von Instanzmaterial und zerstört automatisch [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) Instanzmaterialien für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="ad0ef-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="ad0ef-106">Diese Hilfsprogrammkomponente kann als Ersatz für [Renderer.material oder](https://docs.unity3d.com/ScriptReference/Renderer-material.html) [Renderer.materials verwendet werden.](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)</span><span class="sxs-lookup"><span data-stu-id="ad0ef-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html).</span></span>

> [!NOTE]
> <span data-ttu-id="ad0ef-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) werden der Materialinstancierung vorgezogen, sind aber nicht immer in allen Szenarien verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ad0ef-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="ad0ef-108">Warum kann die [Verwendung von Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ein Problem sein?</span><span class="sxs-lookup"><span data-stu-id="ad0ef-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="ad0ef-109">Wenn Sie den folgenden Code zu einer Unity-Szene hinzufügen und die Speicherauslastung für Trefferplays weiterhin heiter und tosend ist:</span><span class="sxs-lookup"><span data-stu-id="ad0ef-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

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
> <span data-ttu-id="ad0ef-110">Das oben genannte **Leak-Verhalten stürzt Unity ab,** wenn es zu lange läuft!</span><span class="sxs-lookup"><span data-stu-id="ad0ef-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="ad0ef-111">Alternativ können Sie versuchen, das Verhalten [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="ad0ef-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

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

## <a name="usage"></a><span data-ttu-id="ad0ef-112">Verwendung</span><span class="sxs-lookup"><span data-stu-id="ad0ef-112">Usage</span></span>

<span data-ttu-id="ad0ef-113">Beim Aufrufen von [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s) von Unity instanziiert Unity automatisch neue Materialien.</span><span class="sxs-lookup"><span data-stu-id="ad0ef-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="ad0ef-114">Es liegt in der Verantwortung des Aufrufers, die Materialien zu zerstören, wenn ein Material nicht mehr benötigt wird oder das Spielobjekt zerstört wird.</span><span class="sxs-lookup"><span data-stu-id="ad0ef-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="ad0ef-115">Das [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) Verhalten hilft dabei, Materiallecks zu vermeiden und die Materialzuordnungspfade während der Bearbeitung und Laufzeit konsistent zu halten.</span><span class="sxs-lookup"><span data-stu-id="ad0ef-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="ad0ef-116">Wenn ein [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) nicht verwendet werden kann und ein Material instanziert werden muss, kann wie [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) folgt verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="ad0ef-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

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

<span data-ttu-id="ad0ef-117">Wenn mehrere Objekte den Besitz der Materialinstanz benötigen, ist es am besten, den expliziten Besitz für die Verweisnachverfolgung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="ad0ef-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="ad0ef-118">(Zur Unterstützung des [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) Besitzes ist eine optionale Schnittstelle namens vorhanden.) Im Folgenden finden Sie ein Beispiel für die Verwendung:</span><span class="sxs-lookup"><span data-stu-id="ad0ef-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

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

<span data-ttu-id="ad0ef-119">Weitere Informationen finden Sie in der Beispielverwendung, die innerhalb des Verhaltens demonstriert [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) wird.</span><span class="sxs-lookup"><span data-stu-id="ad0ef-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad0ef-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ad0ef-120">See also</span></span>

* [<span data-ttu-id="ad0ef-121">MRTK-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="ad0ef-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
