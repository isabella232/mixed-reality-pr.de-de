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
# <a name="object-collection"></a>Objektsammlung

![Objektsammlung](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

Objektauflistung ist ein Skript, mit dem ein Array von Objekten in vordefinierten dreidimensionalen Formen erstellt werden kann. Es unterstützt verschiedene Oberflächenstile, einschließlich Ebene, Zylinder, Kugel und Radial. Da es jedes Objekt in Unity unterstützt, kann es zum Layout von 2D- und 3D-Objekten verwendet werden.

## <a name="object-collection-scripts"></a>Objektsammlungsskripts

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) unterstützt Typen von Zylindern, Ebenen, Kugeln und radialen Oberflächen.
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) unterstützt die Sammlung verteilter Stile.  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) stellt einige zusätzliche Optionen für GridObjectCollection bereit. **Hinweis:** TileGridObjectCollection erweitert nicht und weist mehrere Fehler auf [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) (siehe [Problem 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)). Daher wird empfohlen, zu [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) verwenden.

|![Grid-Objektauflistung – Zylinder](../images/object-collection/MRTK_ObjectCollectionCylinder.png) Grid-Objektauflistung – Zylinder | ![Grid Object Collection – Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) Grid Object Collection – Sphere |
|:--- | :--- |
|![Rasterobjektauflistung – Radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) Rasterobjektauflistung – Radial | ![Grid-Objektauflistung – Ebene](../images/object-collection/MRTK_ObjectCollectionPlane.png) Grid-Objektauflistung – Ebene |
|![Sammlung verteilter Objekte](../images/object-collection/MRTK_ObjectCollectionScattered.png) Sammlung verteilter Objekte | ![Tile Grid-Objektauflistung](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) Tile Grid-Objektauflistung |

## <a name="how-to-use-an-object-collection"></a>Verwenden einer Objektsammlung

Um eine Sammlung zu erstellen, erstellen Sie ein leeres GameObject, und weisen Sie ihm eines der Objektsammlungsskripts zu. Alle Objekte können als untergeordnetes Element des GameObject hinzugefügt werden. Nachdem Sie das Hinzufügen untergeordneter Objekte abgeschlossen haben, klicken Sie im Inspektorbereich auf die Schaltfläche *Sammlung aktualisieren,* um die Objektsammlung zu generieren. Die Objekte werden in der Szene entsprechend den Auflistungsparametern angeordnet. Auf die Updatesammlung kann auch über den Code zugegriffen werden.

![Objektsammlungsskript](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` Inhaltsausrichtung

Der Inhalt in einer GridObjectCollection kann so ausgerichtet werden, dass das übergeordnete Objekt oben/mitte/unten und links/mitte/rechts der Auflistung verankert wird. Verwenden  Sie die Anchor-Eigenschaft, um die Inhaltsausrichtung anzugeben.

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` Layoutreihenfolge

Verwenden Sie das Feld **Layout,** um die Zeilen-/Spaltenreihenfolge anzugeben, in der untergeordnete Elemente angeordnet sind:

**Spalte Dann Zeile** – Untergeordnete Elemente werden zuerst horizontal (nach Spalte) und dann vertikal (nach Zeile) angeordnet. Verwenden Sie **Num Columns** (oder Columns-Eigenschaft im Code), um die Anzahl der Spalten im Raster anzugeben.

![Spalten- und Zeilenlayout](../images/object-collection/MRTK_ColumnThenRow.png)

**Row Then Column** – Children werden zuerst vertikal (nach Zeile) und dann horizontal (nach Spalten) angeordnet. Verwenden Sie **zeilenanzahl** (oder Rows-Eigenschaft im Code), um die Anzahl der Zeilen im Raster anzugeben.

![Zeilen- und Spaltenlayout](../images/object-collection/MRTK_RowThenColumn.png)

**Horizontal:** Untergeordnete Elemente werden in einer einzelnen Zeile angeordnet, wobei nur Spalten verwendet werden.

**Vertikal:** Untergeordnete Elemente werden in einer einzelnen Spalte angeordnet, wobei nur Zeilen verwendet werden.

## <a name="object-collection-examples"></a>Beispiele für Objektsammlungen

Die `ObjectCollectionExamples` Beispielszene (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) enthält verschiedene Beispiele für Objektsammlungstypen.

[Die Periodentabelle der Elemente](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Beispiel-App, die die Funktionsweise von Objektauflistungen veranschaulicht. Die Objektauflistung wird verwendet, um die 3D-Elementfelder in verschiedenen Formen zu layouten.

## <a name="object-collection-types"></a>Objektsammlungstypen

**3D-Objekte**

Eine Objektauflistung kann verwendet werden, um importierte 3D-Objekte zu layouten. Das folgende Beispiel zeigt die ebenen- und zylindrischen Layouts von 3D-Sitzungsmodellobjekten mithilfe einer -Auflistung.

![Objektsammlung 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**2D-Objekte**

Eine Objektauflistung kann auch aus 2D-Bildern entnommen werden. Beispielsweise können mehrere Bilder in einem Rasterformat platziert werden.

![Objektsammlung 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
