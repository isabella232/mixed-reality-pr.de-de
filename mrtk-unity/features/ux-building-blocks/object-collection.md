---
title: Objektsammlung
description: Übersicht über die Objektsammlung in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Objektsammlung,
ms.openlocfilehash: 8390e9c4a7bd419f99a5c8c4af7e7a2eca1d8f3f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177055"
---
# <a name="object-collection"></a><span data-ttu-id="bf1eb-104">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="bf1eb-104">Object collection</span></span>

![Objektsammlung](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

<span data-ttu-id="bf1eb-106">Objektauflistung ist ein Skript, mit dem ein Array von Objekten in vordefinierten dreidimensionalen Formen erstellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-106">Object collection is a script to help lay out an array of objects in predefined three-dimensional shapes.</span></span> <span data-ttu-id="bf1eb-107">Es unterstützt verschiedene Oberflächenstile, einschließlich Ebene, Zylinder, Kugel und Radial.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-107">It supports various surface styles including plane, cylinder, sphere, and radial.</span></span> <span data-ttu-id="bf1eb-108">Da es jedes Objekt in Unity unterstützt, kann es zum Layout von 2D- und 3D-Objekten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-108">Since it supports any object in Unity, it can be used to layout both 2D and 3D objects.</span></span>

## <a name="object-collection-scripts"></a><span data-ttu-id="bf1eb-109">Objektsammlungsskripts</span><span class="sxs-lookup"><span data-stu-id="bf1eb-109">Object collection scripts</span></span>

- <span data-ttu-id="bf1eb-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) unterstützt Typen von Zylindern, Ebenen, Kugeln und radialen Oberflächen.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supports Cylinder, Plane, Sphere, Radial surface types</span></span>
- <span data-ttu-id="bf1eb-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) unterstützt die Sammlung verteilter Stile.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supports scattered style collection</span></span>  
- <span data-ttu-id="bf1eb-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) stellt einige zusätzliche Optionen für GridObjectCollection bereit.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) provides some additional options to GridObjectCollection.</span></span> <span data-ttu-id="bf1eb-113">**Hinweis:** TileGridObjectCollection erweitert nicht und weist mehrere Fehler auf [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) (siehe [Problem 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span><span class="sxs-lookup"><span data-stu-id="bf1eb-113">**Note:** TileGridObjectCollection does not extend [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection), and has several bugs (see [issue 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span></span> <span data-ttu-id="bf1eb-114">Daher wird empfohlen, zu [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) verwenden.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-114">Therefore, it is recommended to use [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection).</span></span>

|![Grid-Objektauflistung – Zylinder](../images/object-collection/MRTK_ObjectCollectionCylinder.png) <span data-ttu-id="bf1eb-116">Grid-Objektauflistung – Zylinder</span><span class="sxs-lookup"><span data-stu-id="bf1eb-116">Grid Object Collection - Cylinder</span></span> | ![Grid Object Collection – Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) <span data-ttu-id="bf1eb-118">Grid Object Collection – Sphere</span><span class="sxs-lookup"><span data-stu-id="bf1eb-118">Grid Object Collection - Sphere</span></span> |
|:--- | :--- |
|![Rasterobjektauflistung – Radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) <span data-ttu-id="bf1eb-120">Rasterobjektauflistung – Radial</span><span class="sxs-lookup"><span data-stu-id="bf1eb-120">Grid Object Collection - Radial</span></span> | ![Grid-Objektauflistung – Ebene](../images/object-collection/MRTK_ObjectCollectionPlane.png) <span data-ttu-id="bf1eb-122">Grid-Objektauflistung – Ebene</span><span class="sxs-lookup"><span data-stu-id="bf1eb-122">Grid Object Collection - Plane</span></span> |
|![Sammlung verteilter Objekte](../images/object-collection/MRTK_ObjectCollectionScattered.png) <span data-ttu-id="bf1eb-124">Sammlung verteilter Objekte</span><span class="sxs-lookup"><span data-stu-id="bf1eb-124">Scattered Object Collection</span></span> | ![Tile Grid-Objektauflistung](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) <span data-ttu-id="bf1eb-126">Tile Grid-Objektauflistung</span><span class="sxs-lookup"><span data-stu-id="bf1eb-126">Tile Grid Object Collection</span></span> |

## <a name="how-to-use-an-object-collection"></a><span data-ttu-id="bf1eb-127">Verwenden einer Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="bf1eb-127">How to use an object collection</span></span>

<span data-ttu-id="bf1eb-128">Um eine Sammlung zu erstellen, erstellen Sie ein leeres GameObject, und weisen Sie ihm eines der Objektsammlungsskripts zu.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-128">To create a collection, create an empty GameObject and assign one of the Object Collection scripts to it.</span></span> <span data-ttu-id="bf1eb-129">Alle Objekte können als untergeordnetes Element des GameObject hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-129">Any object(s) can be added as a child of the GameObject.</span></span> <span data-ttu-id="bf1eb-130">Nachdem Sie das Hinzufügen untergeordneter Objekte abgeschlossen haben, klicken Sie im Inspektorbereich auf die Schaltfläche *Sammlung aktualisieren,* um die Objektsammlung zu generieren.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-130">Once finished adding child objects, click the *Update Collection* button in the inspector panel to generate the object collection.</span></span> <span data-ttu-id="bf1eb-131">Die Objekte werden in der Szene entsprechend den Auflistungsparametern angeordnet.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-131">The objects will be laid out in the scene according to the collection parameters.</span></span> <span data-ttu-id="bf1eb-132">Auf die Updatesammlung kann auch über den Code zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-132">Update Collection can be accessed through the code too.</span></span>

![Objektsammlungsskript](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a><span data-ttu-id="bf1eb-134">`GridObjectCollection` Inhaltsausrichtung</span><span class="sxs-lookup"><span data-stu-id="bf1eb-134">`GridObjectCollection` content alignment</span></span>

<span data-ttu-id="bf1eb-135">Der Inhalt in einer GridObjectCollection kann so ausgerichtet werden, dass das übergeordnete Objekt oben/mitte/unten und links/mitte/rechts der Auflistung verankert wird.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-135">The content in a GridObjectCollection can be aligned so that the parent object is anchored to the top/middle/bottom and left/center/right of the collection.</span></span> <span data-ttu-id="bf1eb-136">Verwenden  Sie die Anchor-Eigenschaft, um die Inhaltsausrichtung anzugeben.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-136">Use the **anchor** property to specify content alignment.</span></span>

## <a name="gridobjectcollection-layout-order"></a><span data-ttu-id="bf1eb-137">`GridObjectCollection` Layoutreihenfolge</span><span class="sxs-lookup"><span data-stu-id="bf1eb-137">`GridObjectCollection` layout order</span></span>

<span data-ttu-id="bf1eb-138">Verwenden Sie das Feld **Layout,** um die Zeilen-/Spaltenreihenfolge anzugeben, in der untergeordnete Elemente angeordnet sind:</span><span class="sxs-lookup"><span data-stu-id="bf1eb-138">Use the **Layout** field to specify the row / column order that children are laid out:</span></span>

<span data-ttu-id="bf1eb-139">**Spalte Dann Zeile** – Untergeordnete Elemente werden zuerst horizontal (nach Spalte) und dann vertikal (nach Zeile) angeordnet.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-139">**Column Then Row** - Children are first laid out by horizontally (by column), then vertically (by row).</span></span> <span data-ttu-id="bf1eb-140">Verwenden Sie **Num Columns** (oder Columns-Eigenschaft im Code), um die Anzahl der Spalten im Raster anzugeben.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-140">Use **Num Columns** (or Columns property in code) to specify the number of columns in the grid.</span></span>

![Spalten- und Zeilenlayout](../images/object-collection/MRTK_ColumnThenRow.png)

<span data-ttu-id="bf1eb-142">**Row Then Column** – Children werden zuerst vertikal (nach Zeile) und dann horizontal (nach Spalten) angeordnet.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-142">**Row Then Column** - Children are first laid out vertically (by row), then horizontally (by columns).</span></span> <span data-ttu-id="bf1eb-143">Verwenden Sie **zeilenanzahl** (oder Rows-Eigenschaft im Code), um die Anzahl der Zeilen im Raster anzugeben.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-143">Use **Num Rows** (or Rows property in code) to specify the number of rows in the grid.</span></span>

![Zeilen- und Spaltenlayout](../images/object-collection/MRTK_RowThenColumn.png)

<span data-ttu-id="bf1eb-145">**Horizontal:** Untergeordnete Elemente werden in einer einzelnen Zeile angeordnet, wobei nur Spalten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-145">**Horizontal** - Children are laid out in a single row using columns only</span></span>

<span data-ttu-id="bf1eb-146">**Vertikal:** Untergeordnete Elemente werden in einer einzelnen Spalte angeordnet, wobei nur Zeilen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-146">**Vertical** - Children are laid out in a single column using rows only.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="bf1eb-147">Beispiele für Objektsammlungen</span><span class="sxs-lookup"><span data-stu-id="bf1eb-147">Object collection examples</span></span>

<span data-ttu-id="bf1eb-148">Die `ObjectCollectionExamples` Beispielszene (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) enthält verschiedene Beispiele für Objektsammlungstypen.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-148">The `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) example scene contains various examples of object collection types.</span></span>

<span data-ttu-id="bf1eb-149">[Die Periodentabelle der Elemente](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Beispiel-App, die die Funktionsweise von Objektauflistungen veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-149">[Periodic table of the elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an example app that demonstrates how object collections work.</span></span> <span data-ttu-id="bf1eb-150">Die Objektauflistung wird verwendet, um die 3D-Elementfelder in verschiedenen Formen zu layouten.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-150">It uses object collection to layout the 3D element boxes in different shapes.</span></span>

## <a name="object-collection-types"></a><span data-ttu-id="bf1eb-151">Objektsammlungstypen</span><span class="sxs-lookup"><span data-stu-id="bf1eb-151">Object collection types</span></span>

<span data-ttu-id="bf1eb-152">**3D-Objekte**</span><span class="sxs-lookup"><span data-stu-id="bf1eb-152">**3D objects**</span></span>

<span data-ttu-id="bf1eb-153">Eine Objektauflistung kann verwendet werden, um importierte 3D-Objekte zu layouten.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-153">An object collection can be used to layout imported 3D objects.</span></span> <span data-ttu-id="bf1eb-154">Das folgende Beispiel zeigt die ebenen- und zylindrischen Layouts von 3D-Sitzungsmodellobjekten mithilfe einer -Auflistung.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-154">The example below shows the plane and cylindrical layouts of 3D chair model objects using a collection.</span></span>

![Objektsammlung 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

<span data-ttu-id="bf1eb-156">**2D-Objekte**</span><span class="sxs-lookup"><span data-stu-id="bf1eb-156">**2D Objects**</span></span>

<span data-ttu-id="bf1eb-157">Eine Objektauflistung kann auch aus 2D-Bildern entnommen werden.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-157">An object collection can also be crated from 2D images.</span></span> <span data-ttu-id="bf1eb-158">Beispielsweise können mehrere Bilder in einem Rasterformat platziert werden.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-158">For example, multiple images can be placed in a grid style.</span></span>

![Objektsammlung 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
