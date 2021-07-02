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
# <a name="material-instance"></a>Materialinstanz

Das Verhalten spricht für die Nachverfolgung der Lebensdauer von Instanzmaterial und zerstört automatisch [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) Instanzmaterialien für den Benutzer. Diese Hilfsprogrammkomponente kann als Ersatz für [Renderer.material oder](https://docs.unity3d.com/ScriptReference/Renderer-material.html) [Renderer.materials verwendet werden.](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)

> [!NOTE]
> [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) werden der Materialinstancierung vorgezogen, sind aber nicht immer in allen Szenarien verfügbar.

Warum kann die [Verwendung von Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ein Problem sein? Wenn Sie den folgenden Code zu einer Unity-Szene hinzufügen und die Speicherauslastung für Trefferplays weiterhin heiter und tosend ist:

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
> Das oben genannte **Leak-Verhalten stürzt Unity ab,** wenn es zu lange läuft!

Alternativ können Sie versuchen, das Verhalten [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) zu verwenden:

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

## <a name="usage"></a>Verwendung

Beim Aufrufen von [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s) von Unity instanziiert Unity automatisch neue Materialien. Es liegt in der Verantwortung des Aufrufers, die Materialien zu zerstören, wenn ein Material nicht mehr benötigt wird oder das Spielobjekt zerstört wird. Das [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) Verhalten hilft dabei, Materiallecks zu vermeiden und die Materialzuordnungspfade während der Bearbeitung und Laufzeit konsistent zu halten.

Wenn ein [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) nicht verwendet werden kann und ein Material instanziert werden muss, kann wie [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) folgt verwendet werden:

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

Wenn mehrere Objekte den Besitz der Materialinstanz benötigen, ist es am besten, den expliziten Besitz für die Verweisnachverfolgung zu übernehmen. (Zur Unterstützung des [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) Besitzes ist eine optionale Schnittstelle namens vorhanden.) Im Folgenden finden Sie ein Beispiel für die Verwendung:

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

Weitere Informationen finden Sie in der Beispielverwendung, die innerhalb des Verhaltens demonstriert [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) wird.

## <a name="see-also"></a>Siehe auch

* [MRTK-Standard-Shader](mrtk-standard-shader.md)
