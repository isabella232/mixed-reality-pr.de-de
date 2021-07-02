---
title: Hilfsprogramm zum Austauschen von Medienobjekten
description: Dokumentation zur Verwendung des Hilfsprogramms zum Austauschen von Medienobjekten in MRTK für Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK
ms.openlocfilehash: 50ef252913575988b5f377dd9ff92f9e9ade3a72
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176167"
---
# <a name="asset-swap-utility"></a>Hilfsprogramm zum Austauschen von Medienobjekten

Suchen und Ersetzen ist bei der Arbeit mit Text- und Inhaltserstellungstools ubiquitlich. Wenn Sie viele Ressourcen innerhalb einer Unity-Szene austauschen müssen, können das [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) und der Editor ihnen helfen. Das Hilfsprogramm ist im `Microsoft.MixedReality.Toolkit.Unity.Tools` Paket enthalten.

`AssetSwapUtility`Speichert alle Such- und Ersetzungsaktionen als ScriptableObject, sodass es trival ist, hin- und herzuwechseln oder "Designs" für die zukünftige Verwendung zu speichern.

## <a name="swapping-assets"></a>Austauschen von Ressourcen

Das Austauschen von Ressourcen ist einfach, nachdem Sie eine erstellt `AssetSwapCollection` haben. Wir veranschaulichen die Verwendung, indem wir zwei rote Würfel mit zwei blauen Kugeln in einer Szene austauschen. Fügen Sie ihrer Szene zunächst zwei rote Würfel hinzu, die den Unity-Standardcube und das `MRTK_Standard_Red` Material verwenden.

Navigieren Sie zum Erstellen eines zu Mixed Reality Toolkit > Utilities > Create Asset Swap Collection (Sammlung zum Austauschen von `AssetSwapCollection` **Medienobjekten erstellen).** Füllen Sie mit dem `AssetSwapCollection` ausgewählten die Eigenschaften aus, wie in der folgenden Abbildung dargestellt:

![Sammlung zum Austauschen von Medienobjekten im Unity-Editor](images/asset-swap-img-01.png)

Wählen Sie als Nächstes in der Dropdownliste "Ausgewähltes Design" die Option "Blue Spheres" aus, und klicken Sie auf "Übernehmen". Alle roten Würfel in Ihrer Szene sollten durch blaue Kugeln ersetzt werden.

![Sammlung zum Austauschen von Medienobjekten im Unity-Editor mit ausgewähltem Design hervorgehoben](images/asset-swap-img-02.png)

In diesem Beispiel haben wir eine vollständige Szenenersetzung durchgeführt, aber Sie können Teile Ihrer Szene ersetzen, indem Sie den Auswahlmodus ändern. Sie können auch wieder zu roten Cubes wechseln, indem Sie in der Dropdownliste "Ausgewähltes Design" die Option "Red Cubes" auswählen und erneut auf "Übernehmen" klicken.

> [!NOTE]
> Es ist möglich, alle Medienobjekttypen wie Audiodateien, Schriftarten, Prefabs usw. auszutauschen. Führt `AssetSwapUtility` einige Überprüfungen der Bereinigung durch, um sicherzustellen, dass Sie einen Austausch zu ähnlichen Typen durchführen.
