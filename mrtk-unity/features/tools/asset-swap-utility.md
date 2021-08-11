---
title: Asset Swap-Hilfsprogramm
description: Dokumentation zur Verwendung des Hilfsprogramms zum Austauschen von Medienobjekten in MRTK für Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK
ms.openlocfilehash: 3322087f9027f46b39be07f5368cd8ae4ca875f206984fb823f9b1c8590f86f6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196268"
---
# <a name="asset-swap-utility"></a>Asset Swap-Hilfsprogramm

Suchen und Ersetzen ist bei der Arbeit mit Text- und Inhaltserstellungstools ubiquitlich. Wenn Sie viele Ressourcen innerhalb einer Unity-Szene austauschen müssen, können das [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) und der Editor ihnen helfen. Das Hilfsprogramm ist im `Microsoft.MixedReality.Toolkit.Unity.Tools` Paket enthalten.

`AssetSwapUtility`Speichert alle Such- und Ersetzungsaktionen als ScriptableObject, sodass es trival ist, hin- und herzuwechseln oder "Designs" für die zukünftige Verwendung zu speichern.

## <a name="swapping-assets"></a>Austauschen von Ressourcen

Das Austauschen von Ressourcen ist einfach, nachdem Sie eine erstellt `AssetSwapCollection` haben. Wir veranschaulichen die Verwendung, indem wir zwei rote Würfel mit zwei blauen Kugeln in einer Szene austauschen. Fügen Sie ihrer Szene zunächst zwei rote Würfel hinzu, die den Unity-Standardcube und das `MRTK_Standard_Red` Material verwenden.

Navigieren Sie zum Erstellen eines `AssetSwapCollection` zu Mixed Reality Toolkit > Utilities > Create Asset Swap **Collection**. Füllen Sie mit dem `AssetSwapCollection` ausgewählten die Eigenschaften aus, wie in der folgenden Abbildung dargestellt:

![Sammlung zum Austauschen von Medienobjekten im Unity-Editor](images/asset-swap-img-01.png)

Wählen Sie als Nächstes in der Dropdownliste "Ausgewähltes Design" die Option "Blue Spheres" aus, und klicken Sie auf "Übernehmen". Alle roten Würfel in Ihrer Szene sollten durch blaue Kugeln ersetzt werden.

![Sammlung zum Austauschen von Medienobjekten im Unity-Editor mit ausgewähltem Design hervorgehoben](images/asset-swap-img-02.png)

In diesem Beispiel haben wir eine vollständige Szenenersetzung durchgeführt, aber Sie können Teile Ihrer Szene ersetzen, indem Sie den Auswahlmodus ändern. Sie können auch wieder zu roten Cubes wechseln, indem Sie in der Dropdownliste "Ausgewähltes Design" "Red Cubes" auswählen und erneut auf "Übernehmen" klicken.

> [!NOTE]
> Es ist möglich, alle Medienobjekttypen wie Audiodateien, Schriftarten, Prefabs usw. auszutauschen. Führt `AssetSwapUtility` einige Überprüfungen der Bereinigung durch, um sicherzustellen, dass Sie einen Austausch zu ähnlichen Typen durchführen.
