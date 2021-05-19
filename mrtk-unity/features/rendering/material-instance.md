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
# <a name="material-instance"></a>Materialinstanz

Das [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) Verhalten hilft bei der Nachverfolgung der Lebensdauer von Instanzmaterial und zerstört automatisch instanzierte Materialien für den Benutzer. Diese Hilfsprogrammkomponente kann als Ersatz für [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) oder [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)verwendet werden.

> [!NOTE]
> [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) werden gegenüber der Materialinstanzierung bevorzugt, sind aber nicht immer in allen Szenarien verfügbar.

Warum kann die Verwendung von [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) ein Problem darstellen? Wenn Sie den folgenden Code zu einer Unity-Szene hinzufügen und die Nutzung des Arbeitsspeichers der Trefferwiedergabe fortgesetzt wird, wird dies weiter steigen:

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
> Das oben genannte Leak-Verhalten **stürzt Unity ab,** wenn es zu lange ausgeführt wird.

Alternativ können Sie versuchen, das -Verhalten zu [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) verwenden:

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

Beim Aufrufen von [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s) von Unity instanziiert Unity automatisch neue Materialien. Es liegt in der Verantwortung des Aufrufers, die Materialien zu zerstören, wenn ein Material nicht mehr benötigt wird oder das Spielobjekt zerstört wird. Das [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) Verhalten hilft dabei, Materialverluste zu vermeiden und die Materialzuordnungspfade während der Bearbeitungs- und Laufzeit konsistent zu halten.

Wenn ein [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) nicht verwendet werden kann und ein Material instanziert werden muss, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) kann wie folgt verwendet werden:

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

Wenn mehrere Objekte den Besitz der Materialinstanz benötigen, ist es am besten, den expliziten Besitz für die Verweisnachverfolgung zu übernehmen. (Eine optionale Schnittstelle namens [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) ist vorhanden, um den Besitz zu unterstützen.) Im Folgenden finden Sie ein Beispiel für die Verwendung:

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

Weitere Informationen finden Sie in der Beispielverwendung, die innerhalb des Verhaltens veranschaulicht [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) wird.

## <a name="see-also"></a>Weitere Informationen

* [MRTK-Standard-Shader](mrtk-standard-shader.md)
