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
# <a name="proximity-light"></a>Näherungslicht

Ein ist ein Fluent Design System Paradigma, das ein [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) "FarbverlaufsinversePunktlicht" imitiert, das auf die Oberfläche eines Objekts [](https://www.microsoft.com/design/fluent/) zeigt. Die Anwendung wird häufig für Nahinteraktionen verwendet und kann die Eigenschaften eines Näherungslichts über die Komponente [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) steuern.

Damit ein Material von einem Mixed Reality [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *Toolkit/Standard-Shader* beeinflusst wird, muss die *Eigenschaft Näherungslicht* aktiviert werden.

> [!NOTE]
> Standardmäßig werden [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) bis zu zwei unterstützt.

## <a name="examples"></a>Beispiele

Die meisten Szenen im MRTK verwenden eine [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) . Den häufigsten Einsatzfall finden Sie unter MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab.

## <a name="advanced-usage"></a>Erweiterte Nutzung

Standardmäßig können nur [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) zwei ein Material [gleichzeitig](https://docs.unity3d.com/ScriptReference/Material.html) beleuchten. Wenn ihr Projekt mehr als zwei benötigt, um ein Material zu beeinflussen, veranschaulicht der folgende Beispielcode, [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) wie dies erreicht werden kann. [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!NOTE]
> Wenn ein [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) Material mit vielen Farben [belichtet wird,](https://docs.unity3d.com/ScriptReference/Material.html) werden die Anweisungen für Denkpixel-Shader erhöht, was sich auf die Leistung auswirken wird. Erstellen Sie ein Profil für diese Änderungen in Ihrem Projekt.

*Erhöhen der Anzahl der verfügbaren Daten [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) von zwei auf vier.*

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
> Wenn Unity eine Warnung wie unten protokolliert, müssen Sie Unity neu starten, bevor Ihre Änderungen wirksam werden.
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>Weitere Informationen

* [MRTK-Standard-Shader](mrtk-standard-shader.md)
