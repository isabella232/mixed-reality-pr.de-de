---
title: Nähemenü
description: Übersicht über Menütypen in der Nähe in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Menü "Nah",
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175651"
---
# <a name="near-menu"></a><span data-ttu-id="facd4-104">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="facd4-104">Near menu</span></span>

![Nähemenü](../images/near-menu/MRTK_UX_NearMenu.png)

<span data-ttu-id="facd4-106">Near Menu ist ein UX-Steuerelement, das eine Sammlung von Schaltflächen oder anderen Benutzeroberflächenkomponenten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="facd4-106">Near Menu is a UX control which provides a collection of buttons or other UI components.</span></span> <span data-ttu-id="facd4-107">Sie ist im Text des Benutzers unverankert und jederzeit leicht zugänglich.</span><span class="sxs-lookup"><span data-stu-id="facd4-107">It is floating around the user's body and easily accessible anytime.</span></span> <span data-ttu-id="facd4-108">Da sie lose mit dem Benutzer gekoppelt ist, wird die Interaktion des Benutzers mit dem Zielinhalt nicht beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="facd4-108">Since it is loosely coupled with the user, it does not disturb the user's interaction with the target content.</span></span> <span data-ttu-id="facd4-109">Der Benutzer kann die Schaltfläche "Anheften" verwenden, um das Menü zu sperren bzw. zu entsperren.</span><span class="sxs-lookup"><span data-stu-id="facd4-109">The user can use the 'Pin' button to world-lock/unlock the menu.</span></span> <span data-ttu-id="facd4-110">Das Menü kann gepackt und an einer bestimmten Position platziert werden.</span><span class="sxs-lookup"><span data-stu-id="facd4-110">The menu can be grabbed and placed at a specific position.</span></span>

## <a name="interaction-behavior"></a><span data-ttu-id="facd4-111">Interaktionsverhalten</span><span class="sxs-lookup"><span data-stu-id="facd4-111">Interaction behavior</span></span>

- <span data-ttu-id="facd4-112">**Tag-along:** Das Menü folgt Auf Sie und bleibt im Bereich von 30 bis 60 cm vom Benutzer für die Interaktionen in der Nähe.</span><span class="sxs-lookup"><span data-stu-id="facd4-112">**Tag-along**: The menu follows you and stays within 30-60cm range from the user for the near interactions.</span></span>
- <span data-ttu-id="facd4-113">**Anheften:** Mithilfe der Schaltfläche "Anheften" kann das Menü weltweit gesperrt und freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="facd4-113">**Pin**: Using the 'Pin' button, the menu can be world-locked and released.</span></span>
- <span data-ttu-id="facd4-114">**Greifen und verschieben:** Das Menü ist immer ziehbar und verschiebbar.</span><span class="sxs-lookup"><span data-stu-id="facd4-114">**Grab and move**: The menu is always grabbable and movable.</span></span> <span data-ttu-id="facd4-115">Unabhängig vom vorherigen Zustand wird das Menü angeheftet (world-locked), wenn es gepackt und freigegeben wird.</span><span class="sxs-lookup"><span data-stu-id="facd4-115">Regardless of the previous state, the menu will be pinned(world-locked) when grabbed and released.</span></span> <span data-ttu-id="facd4-116">Es gibt visuelle Hinweise für den zu greifenden Bereich.</span><span class="sxs-lookup"><span data-stu-id="facd4-116">There are visual cues for the grabbable area.</span></span> <span data-ttu-id="facd4-117">Sie werden in der Nähe der Hand angezeigt.</span><span class="sxs-lookup"><span data-stu-id="facd4-117">They are revealed on hand proximity.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a><span data-ttu-id="facd4-118">Prefabs</span><span class="sxs-lookup"><span data-stu-id="facd4-118">Prefabs</span></span>

<span data-ttu-id="facd4-119">Prefabs in der Nähe von Menüs veranschaulichen, wie die verschiedenen MRTK-Komponenten verwendet werden, um Menüs für Interaktionen in der Nähe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="facd4-119">Near Menu prefabs are designed to demonstrate how to use MRTK's various components to build menus for near interactions.</span></span>

- <span data-ttu-id="facd4-120">**NearMenu2x4.prefab**</span><span class="sxs-lookup"><span data-stu-id="facd4-120">**NearMenu2x4.prefab**</span></span>
- <span data-ttu-id="facd4-121">**NearMenu3x1.prefab**</span><span class="sxs-lookup"><span data-stu-id="facd4-121">**NearMenu3x1.prefab**</span></span>
- <span data-ttu-id="facd4-122">**NearMenu3x2.prefab**</span><span class="sxs-lookup"><span data-stu-id="facd4-122">**NearMenu3x2.prefab**</span></span>
- <span data-ttu-id="facd4-123">**NearMenu3x3.prefab**</span><span class="sxs-lookup"><span data-stu-id="facd4-123">**NearMenu3x3.prefab**</span></span>
- <span data-ttu-id="facd4-124">**NearMenu4x1.prefab**</span><span class="sxs-lookup"><span data-stu-id="facd4-124">**NearMenu4x1.prefab**</span></span>
- <span data-ttu-id="facd4-125">**NearMenu4x2.prefab**</span><span class="sxs-lookup"><span data-stu-id="facd4-125">**NearMenu4x2.prefab**</span></span>

## <a name="example-scene"></a><span data-ttu-id="facd4-126">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="facd4-126">Example scene</span></span>

<span data-ttu-id="facd4-127">Beispiele für Prefabs in der Nähe von Menüs finden Sie in der `NearMenuExamples` Szene.</span><span class="sxs-lookup"><span data-stu-id="facd4-127">You can find examples of Near Menu prefabs in the `NearMenuExamples` scene.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a><span data-ttu-id="facd4-128">Struktur</span><span class="sxs-lookup"><span data-stu-id="facd4-128">Structure</span></span>

<span data-ttu-id="facd4-129">Prefabs in der Nähe von Menüs werden mit den folgenden MRTK-Komponenten erstellt.</span><span class="sxs-lookup"><span data-stu-id="facd4-129">Near Menu prefabs are made with following MRTK components.</span></span>

- <span data-ttu-id="facd4-130">[**Prefab PressableButtonHoloLens2**](button.md)</span><span class="sxs-lookup"><span data-stu-id="facd4-130">[**PressableButtonHoloLens2**](button.md) prefab</span></span>
- <span data-ttu-id="facd4-131">[**Rasterobjektauflistung:**](object-collection.md)Layout mehrerer Schaltflächen im Raster</span><span class="sxs-lookup"><span data-stu-id="facd4-131">[**Grid Object Collection**](object-collection.md): Multiple button layout in grid</span></span>
- <span data-ttu-id="facd4-132">[**Bearbeitungshandler:**](manipulation-handler.md)Greifen Sie das Menü an, und verschieben Sie es.</span><span class="sxs-lookup"><span data-stu-id="facd4-132">[**Manipulation Handler**](manipulation-handler.md): Grab and move the menu</span></span>
- <span data-ttu-id="facd4-133">RadialView Solver: Follow Me(tag-along) behavior (RadialView Solver: Follow Me(tag-along)behavior [**(RadialView-Solver:**](solvers/solver.md)Follow Me(tag-along)</span><span class="sxs-lookup"><span data-stu-id="facd4-133">[**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior</span></span>

![Prefab im Menü "Near"](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a><span data-ttu-id="facd4-135">Vorgehensweise beim Anpassen</span><span class="sxs-lookup"><span data-stu-id="facd4-135">How to customize</span></span>

<span data-ttu-id="facd4-136">**1. Hinzufügen/Entfernen von Schaltflächen**</span><span class="sxs-lookup"><span data-stu-id="facd4-136">**1. Add/Remove Buttons**</span></span>

<span data-ttu-id="facd4-137">Fügen Sie unter `ButtonCollection` dem -Objekt Schaltflächen hinzu, oder entfernen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="facd4-137">Under `ButtonCollection` object, add or remove buttons.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

<span data-ttu-id="facd4-138">**2. Aktualisieren der Grid-Objektauflistung**</span><span class="sxs-lookup"><span data-stu-id="facd4-138">**2. Update the Grid Object Collection**</span></span>

<span data-ttu-id="facd4-139">Klicken Sie im Inspektor des Objekts auf `Update Collection` die Schaltfläche `ButtonCollection` .</span><span class="sxs-lookup"><span data-stu-id="facd4-139">Click `Update Collection` button in the Inspector of the `ButtonCollection` object.</span></span> <span data-ttu-id="facd4-140">Das Rasterlayout wird aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="facd4-140">It will update the grid layout.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

<span data-ttu-id="facd4-141">Sie können die Anzahl der Zeilen mithilfe `Rows` der -Eigenschaft der Grid-Objektauflistung konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="facd4-141">You can configure the number of rows using `Rows` property of the Grid Object Collection.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

<span data-ttu-id="facd4-142">**3. Anpassen der Backplate-Größe**</span><span class="sxs-lookup"><span data-stu-id="facd4-142">**3. Adjust the backplate size**</span></span>

<span data-ttu-id="facd4-143">Passen Sie die Größe des unter dem `Quad` `Backplate` -Objekt an.</span><span class="sxs-lookup"><span data-stu-id="facd4-143">Adjust the size of the `Quad` under `Backplate` object.</span></span> <span data-ttu-id="facd4-144">Die Breite und Höhe der Backplate sollte `0.032 * [Number of the buttons + 1]` sein.</span><span class="sxs-lookup"><span data-stu-id="facd4-144">The width and height of the backplate should be `0.032 * [Number of the buttons + 1]`.</span></span> <span data-ttu-id="facd4-145">Wenn Sie beispielsweise über 3 x 2 Schaltflächen verfügen, ist die Breite der Backplate `0.032 * 4` und die Höhe `0.032 * 3` .</span><span class="sxs-lookup"><span data-stu-id="facd4-145">For example, if you have 3 x 2 buttons, the width of the backplate is `0.032 * 4` and the height is `0.032 * 3`.</span></span> <span data-ttu-id="facd4-146">Sie können diesen Ausdruck direkt in das -Feld von Unity aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="facd4-146">You can directly put this expression into the Unity's field.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- <span data-ttu-id="facd4-147">Die Standardgröße der schaltfläche HoloLens 2 beträgt 3,2 x 3,2 cm (0,032 m).</span><span class="sxs-lookup"><span data-stu-id="facd4-147">Default size of the HoloLens 2 button is 3.2x3.2 cm (0.032m)</span></span>

## <a name="see-also"></a><span data-ttu-id="facd4-148">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="facd4-148">See also</span></span>

- [<span data-ttu-id="facd4-149">**Schaltflächen**</span><span class="sxs-lookup"><span data-stu-id="facd4-149">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="facd4-150">**Begrenzungssteuerelement**</span><span class="sxs-lookup"><span data-stu-id="facd4-150">**Bounds Control**</span></span>](bounds-control.md)
- [<span data-ttu-id="facd4-151">**Schieberegler**</span><span class="sxs-lookup"><span data-stu-id="facd4-151">**Slider**</span></span>](sliders.md)
- [<span data-ttu-id="facd4-152">**Grid-Objektauflistung**</span><span class="sxs-lookup"><span data-stu-id="facd4-152">**Grid Object Collection**</span></span>](object-collection.md)
- [<span data-ttu-id="facd4-153">**Manipulationshandler**</span><span class="sxs-lookup"><span data-stu-id="facd4-153">**Manipulation Handler**</span></span>](manipulation-handler.md)
- [<span data-ttu-id="facd4-154">**RadialView-Solver**</span><span class="sxs-lookup"><span data-stu-id="facd4-154">**RadialView Solver**</span></span>](solvers/solver.md)
