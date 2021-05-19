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
# <a name="asset-swap-utility"></a><span data-ttu-id="d8e04-104">Hilfsprogramm zum Austauschen von Medienobjekten</span><span class="sxs-lookup"><span data-stu-id="d8e04-104">Asset swap utility</span></span>

<span data-ttu-id="d8e04-105">Suchen und Ersetzen ist bei der Arbeit mit Text- und Inhaltserstellungstools ubiquitlich.</span><span class="sxs-lookup"><span data-stu-id="d8e04-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="d8e04-106">Wenn Sie viele Ressourcen innerhalb einer Unity-Szene austauschen müssen, können das [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) und der Editor ihnen helfen.</span><span class="sxs-lookup"><span data-stu-id="d8e04-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="d8e04-107">Das Hilfsprogramm ist im `Microsoft.MixedReality.Toolkit.Unity.Tools` Paket enthalten.</span><span class="sxs-lookup"><span data-stu-id="d8e04-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="d8e04-108">`AssetSwapUtility`Speichert alle Such- und Ersetzungsaktionen als ScriptableObject, sodass es trival ist, hin- und herzuwechseln oder "Designs" für die zukünftige Verwendung zu speichern.</span><span class="sxs-lookup"><span data-stu-id="d8e04-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="d8e04-109">Austauschen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d8e04-109">Swapping assets</span></span>

<span data-ttu-id="d8e04-110">Das Austauschen von Ressourcen ist einfach, nachdem Sie eine erstellt `AssetSwapCollection` haben.</span><span class="sxs-lookup"><span data-stu-id="d8e04-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="d8e04-111">Wir veranschaulichen die Verwendung, indem wir zwei rote Würfel mit zwei blauen Kugeln in einer Szene austauschen.</span><span class="sxs-lookup"><span data-stu-id="d8e04-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="d8e04-112">Fügen Sie ihrer Szene zunächst zwei rote Würfel hinzu, die den Unity-Standardcube und das `MRTK_Standard_Red` Material verwenden.</span><span class="sxs-lookup"><span data-stu-id="d8e04-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="d8e04-113">Navigieren Sie zum Erstellen eines `AssetSwapCollection` zu Mixed Reality Toolkit > Utilities > Create Asset Swap **Collection**.</span><span class="sxs-lookup"><span data-stu-id="d8e04-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="d8e04-114">Füllen Sie mit dem `AssetSwapCollection` ausgewählten die Eigenschaften aus, wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="d8e04-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Sammlung zum Austauschen von Medienobjekten im Unity-Editor](images/asset-swap-img-01.png)

<span data-ttu-id="d8e04-116">Wählen Sie als Nächstes in der Dropdownliste "Ausgewähltes Design" die Option "Blue Spheres" aus, und klicken Sie auf "Übernehmen".</span><span class="sxs-lookup"><span data-stu-id="d8e04-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="d8e04-117">Alle roten Würfel in Ihrer Szene sollten durch blaue Kugeln ersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="d8e04-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Sammlung zum Austauschen von Medienobjekten im Unity-Editor mit ausgewähltem Design hervorgehoben](images/asset-swap-img-02.png)

<span data-ttu-id="d8e04-119">In diesem Beispiel haben wir eine vollständige Szenenersetzung durchgeführt, aber Sie können Teile Ihrer Szene ersetzen, indem Sie den Auswahlmodus ändern.</span><span class="sxs-lookup"><span data-stu-id="d8e04-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="d8e04-120">Sie können auch wieder zu roten Cubes wechseln, indem Sie in der Dropdownliste "Ausgewähltes Design" "Red Cubes" auswählen und erneut auf "Übernehmen" klicken.</span><span class="sxs-lookup"><span data-stu-id="d8e04-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="d8e04-121">Es ist möglich, jeden Assettyp wie Audiodateien, Schriftarten, Prefabs usw. zu tauschen. Führt `AssetSwapUtility` einige Überprüfungen der Nität durch, um sicherzustellen, dass Sie auf ähnliche Typen umtauschen.</span><span class="sxs-lookup"><span data-stu-id="d8e04-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>