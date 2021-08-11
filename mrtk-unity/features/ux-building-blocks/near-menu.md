---
title: Nähemenü
description: Übersicht über Near Menu types in MRTK (Übersicht über Near Menu-Typen in MRTK)
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Near Menu,
ms.openlocfilehash: 75e7ee195a5838e88c42b7547e7b75205bfe1ee2fa1c8b1ba0a868b294883347
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190621"
---
# <a name="near-menu"></a>Nähemenü

![Nähemenü](../images/near-menu/MRTK_UX_NearMenu.png)

Near Menu ist ein UX-Steuerelement, das eine Sammlung von Schaltflächen oder anderen Benutzeroberflächenkomponenten bietet. Sie ist im Text des Benutzers unverankert und jederzeit leicht zugänglich. Da sie lose mit dem Benutzer gekoppelt ist, wirkt sich dies nicht auf die Interaktion des Benutzers mit dem Zielinhalt aus. Der Benutzer kann die Schaltfläche "Anheften" verwenden, um das Menü zu sperren/zu entsperren. Das Menü kann an einer bestimmten Position greif- und platziert werden.

## <a name="interaction-behavior"></a>Interaktionsverhalten

- **Tag-along:** Das Menü folgt Ihnen und bleibt innerhalb des Bereichs von 30-60cm vom Benutzer für die nahe Interaktionen.
- **Anheften:** Mithilfe der Schaltfläche "Anheften" kann das Menü gesperrt und freigegeben werden.
- **Greifen und verschieben:** Das Menü ist immer greifbar und verschiebbar. Unabhängig vom vorherigen Zustand wird das Menü angeheftet (weltgesperrt), wenn es greif- und freigegeben wird. Es gibt visuelle Hinweise für den begreifbaren Bereich. Sie werden in der Nähe der Hand angezeigt.

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a>Prefabs

Near Menu-Prefabs sollen veranschaulichen, wie die verschiedenen Komponenten des MRTK verwendet werden, um Menüs für nahezu interaktionen zu erstellen.

- **NearMenu2x4.prefab**
- **NearMenu3x1.prefab**
- **NearMenu3x2.prefab**
- **NearMenu3x3.prefab**
- **NearMenu4x1.prefab**
- **NearMenu4x2.prefab**

## <a name="example-scene"></a>Beispielszene

Beispiele für Near Menu-Prefabs finden Sie in der `NearMenuExamples` Szene.

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a>Struktur

Near Menu-Prefabs werden mit folgenden MRTK-Komponenten hergestellt.

- [**PressableButtonHoloLens2-Prefab**](button.md)
- [**Rasterobjektsammlung:**](object-collection.md)Layout mehrerer Schaltflächen im Raster
- [**Manipulation Handler**](manipulation-handler.md): Greifen Sie das Menü, und verschieben Sie es.
- [**RadialView Solver:**](solvers/solver.md)Verhalten von "Me(tag-along)"

![Near Menu Prefab](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>Vorgehensweise beim Anpassen

**1. Hinzufügen/Entfernen von Schaltflächen**

Fügen `ButtonCollection` Sie unter dem -Objekt Schaltflächen hinzu, oder entfernen Sie sie.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2. Aktualisieren der Grid-Objektsammlung**

Klicken `Update Collection` Sie im Inspektor des Objekts auf die `ButtonCollection` Schaltfläche . Das Rasterlayout wird aktualisiert.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

Sie können die Anzahl der Zeilen mithilfe der `Rows` -Eigenschaft der Grid-Objektsammlung konfigurieren.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

**3. Anpassen der Größe der Hintergrundbausteinen**

Passen Sie die Größe des `Quad` unter-Objekts `Backplate` an. Die Breite und Höhe der Backplate sollte `0.032 * [Number of the buttons + 1]` sein. Wenn Sie beispielsweise über 3 x 2 Schaltflächen verfügen, ist die Breite der Backplate `0.032 * 4` und die Höhe `0.032 * 3` . Sie können diesen Ausdruck direkt in das Feld von Unity eingeben.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- Die Standardgröße der HoloLens 2 ist 3,2 x 3,2 cm (0,032 m).

## <a name="see-also"></a>Siehe auch

- [**Schaltflächen**](button.md)
- [**Bounds-Steuerelement**](bounds-control.md)
- [**Schieberegler**](sliders.md)
- [**Grid-Objektsammlung**](object-collection.md)
- [**Manipulation Handler**](manipulation-handler.md)
- [**RadialView Solver**](solvers/solver.md)
