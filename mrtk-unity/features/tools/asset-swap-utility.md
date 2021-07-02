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
# <a name="asset-swap-utility"></a><span data-ttu-id="09138-104">Hilfsprogramm zum Austauschen von Medienobjekten</span><span class="sxs-lookup"><span data-stu-id="09138-104">Asset swap utility</span></span>

<span data-ttu-id="09138-105">Suchen und Ersetzen ist bei der Arbeit mit Text- und Inhaltserstellungstools ubiquitlich.</span><span class="sxs-lookup"><span data-stu-id="09138-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="09138-106">Wenn Sie viele Ressourcen innerhalb einer Unity-Szene austauschen müssen, können das [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) und der Editor ihnen helfen.</span><span class="sxs-lookup"><span data-stu-id="09138-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="09138-107">Das Hilfsprogramm ist im `Microsoft.MixedReality.Toolkit.Unity.Tools` Paket enthalten.</span><span class="sxs-lookup"><span data-stu-id="09138-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="09138-108">`AssetSwapUtility`Speichert alle Such- und Ersetzungsaktionen als ScriptableObject, sodass es trival ist, hin- und herzuwechseln oder "Designs" für die zukünftige Verwendung zu speichern.</span><span class="sxs-lookup"><span data-stu-id="09138-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="09138-109">Austauschen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="09138-109">Swapping assets</span></span>

<span data-ttu-id="09138-110">Das Austauschen von Ressourcen ist einfach, nachdem Sie eine erstellt `AssetSwapCollection` haben.</span><span class="sxs-lookup"><span data-stu-id="09138-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="09138-111">Wir veranschaulichen die Verwendung, indem wir zwei rote Würfel mit zwei blauen Kugeln in einer Szene austauschen.</span><span class="sxs-lookup"><span data-stu-id="09138-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="09138-112">Fügen Sie ihrer Szene zunächst zwei rote Würfel hinzu, die den Unity-Standardcube und das `MRTK_Standard_Red` Material verwenden.</span><span class="sxs-lookup"><span data-stu-id="09138-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="09138-113">Navigieren Sie zum Erstellen eines zu Mixed Reality Toolkit > Utilities > Create Asset Swap Collection (Sammlung zum Austauschen von `AssetSwapCollection` **Medienobjekten erstellen).**</span><span class="sxs-lookup"><span data-stu-id="09138-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="09138-114">Füllen Sie mit dem `AssetSwapCollection` ausgewählten die Eigenschaften aus, wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="09138-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Sammlung zum Austauschen von Medienobjekten im Unity-Editor](images/asset-swap-img-01.png)

<span data-ttu-id="09138-116">Wählen Sie als Nächstes in der Dropdownliste "Ausgewähltes Design" die Option "Blue Spheres" aus, und klicken Sie auf "Übernehmen".</span><span class="sxs-lookup"><span data-stu-id="09138-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="09138-117">Alle roten Würfel in Ihrer Szene sollten durch blaue Kugeln ersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="09138-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Sammlung zum Austauschen von Medienobjekten im Unity-Editor mit ausgewähltem Design hervorgehoben](images/asset-swap-img-02.png)

<span data-ttu-id="09138-119">In diesem Beispiel haben wir eine vollständige Szenenersetzung durchgeführt, aber Sie können Teile Ihrer Szene ersetzen, indem Sie den Auswahlmodus ändern.</span><span class="sxs-lookup"><span data-stu-id="09138-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="09138-120">Sie können auch wieder zu roten Cubes wechseln, indem Sie in der Dropdownliste "Ausgewähltes Design" die Option "Red Cubes" auswählen und erneut auf "Übernehmen" klicken.</span><span class="sxs-lookup"><span data-stu-id="09138-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="09138-121">Es ist möglich, alle Medienobjekttypen wie Audiodateien, Schriftarten, Prefabs usw. auszutauschen. Führt `AssetSwapUtility` einige Überprüfungen der Bereinigung durch, um sicherzustellen, dass Sie einen Austausch zu ähnlichen Typen durchführen.</span><span class="sxs-lookup"><span data-stu-id="09138-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>
