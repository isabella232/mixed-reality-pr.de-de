---
title: Hilfsprogramm zum Austauschen von Medienobjekten
description: Dokumentation zur Verwendung des Hilfsprogramms zum Austauschen von Medienobjekten in MRTK für Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK
ms.openlocfilehash: c277cadffb356b93ffc359233b0b8307f43e8d57
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144138"
---
# <a name="asset-swap-utility"></a>Hilfsprogramm zum Austauschen von Medienobjekten

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
> Es ist möglich, jeden Assettyp wie Audiodateien, Schriftarten, Prefabs usw. zu tauschen. Führt `AssetSwapUtility` einige Überprüfungen der Nität durch, um sicherzustellen, dass Sie auf ähnliche Typen umtauschen.