---
title: Näherungslicht
description: Dokumentation zu Näherungslicht mit Beispielen in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 1adf4d1d70313c917d63224b91a14d995d1888c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144999"
---
# <a name="proximity-light"></a><span data-ttu-id="19bbe-104">Näherungslicht</span><span class="sxs-lookup"><span data-stu-id="19bbe-104">Proximity Light</span></span>

<span data-ttu-id="19bbe-105">Ein ist ein Fluent Design System Paradigma, das ein [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) "FarbverlaufsinversePunktlicht" imitiert, das auf die Oberfläche eines Objekts [](https://www.microsoft.com/design/fluent/) zeigt.</span><span class="sxs-lookup"><span data-stu-id="19bbe-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="19bbe-106">Die Anwendung wird häufig für Nahinteraktionen verwendet und kann die Eigenschaften eines Näherungslichts über die Komponente [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) steuern.</span><span class="sxs-lookup"><span data-stu-id="19bbe-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="19bbe-107">Damit ein Material von einem Mixed Reality [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *Toolkit/Standard-Shader* beeinflusst wird, muss die *Eigenschaft Näherungslicht* aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="19bbe-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="19bbe-108">Standardmäßig werden [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) bis zu zwei unterstützt.</span><span class="sxs-lookup"><span data-stu-id="19bbe-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="19bbe-109">Beispiele</span><span class="sxs-lookup"><span data-stu-id="19bbe-109">Examples</span></span>

<span data-ttu-id="19bbe-110">Die meisten Szenen im MRTK verwenden eine [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) .</span><span class="sxs-lookup"><span data-stu-id="19bbe-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="19bbe-111">Den häufigsten Einsatzfall finden Sie unter MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab.</span><span class="sxs-lookup"><span data-stu-id="19bbe-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="19bbe-112">Erweiterte Nutzung</span><span class="sxs-lookup"><span data-stu-id="19bbe-112">Advanced Usage</span></span>

<span data-ttu-id="19bbe-113">Standardmäßig können nur [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) zwei ein Material [gleichzeitig](https://docs.unity3d.com/ScriptReference/Material.html) beleuchten.</span><span class="sxs-lookup"><span data-stu-id="19bbe-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="19bbe-114">Wenn ihr Projekt mehr als zwei benötigt, um ein Material zu beeinflussen, veranschaulicht der folgende Beispielcode, [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) wie dies erreicht werden kann. [](https://docs.unity3d.com/ScriptReference/Material.html)</span><span class="sxs-lookup"><span data-stu-id="19bbe-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="19bbe-115">Wenn ein [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) Material mit vielen Farben [belichtet wird,](https://docs.unity3d.com/ScriptReference/Material.html) werden die Anweisungen für Denkpixel-Shader erhöht, was sich auf die Leistung auswirken wird.</span><span class="sxs-lookup"><span data-stu-id="19bbe-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="19bbe-116">Erstellen Sie ein Profil für diese Änderungen in Ihrem Projekt.</span><span class="sxs-lookup"><span data-stu-id="19bbe-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="19bbe-117">*Erhöhen der Anzahl der verfügbaren Daten [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) von zwei auf vier.*</span><span class="sxs-lookup"><span data-stu-id="19bbe-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define PROXIMITY_LIGHT_COUNT 2

// to:

#define PROXIMITY_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/ProximityLight.cs change:

private const int proximityLightCount = 2;

// to:

private const int proximityLightCount = 4;
```

> [!NOTE]
> <span data-ttu-id="19bbe-118">Wenn Unity eine Warnung wie unten protokolliert, müssen Sie Unity neu starten, bevor Ihre Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="19bbe-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="19bbe-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="19bbe-119">See also</span></span>

* [<span data-ttu-id="19bbe-120">MRTK-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="19bbe-120">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
