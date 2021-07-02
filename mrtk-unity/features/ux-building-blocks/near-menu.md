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
# <a name="near-menu"></a>Nähemenü

![Nähemenü](../images/near-menu/MRTK_UX_NearMenu.png)

Near Menu ist ein UX-Steuerelement, das eine Sammlung von Schaltflächen oder anderen Benutzeroberflächenkomponenten bereitstellt. Sie ist im Text des Benutzers unverankert und jederzeit leicht zugänglich. Da sie lose mit dem Benutzer gekoppelt ist, wird die Interaktion des Benutzers mit dem Zielinhalt nicht beeinträchtigt. Der Benutzer kann die Schaltfläche "Anheften" verwenden, um das Menü zu sperren bzw. zu entsperren. Das Menü kann gepackt und an einer bestimmten Position platziert werden.

## <a name="interaction-behavior"></a>Interaktionsverhalten

- **Tag-along:** Das Menü folgt Auf Sie und bleibt im Bereich von 30 bis 60 cm vom Benutzer für die Interaktionen in der Nähe.
- **Anheften:** Mithilfe der Schaltfläche "Anheften" kann das Menü weltweit gesperrt und freigegeben werden.
- **Greifen und verschieben:** Das Menü ist immer ziehbar und verschiebbar. Unabhängig vom vorherigen Zustand wird das Menü angeheftet (world-locked), wenn es gepackt und freigegeben wird. Es gibt visuelle Hinweise für den zu greifenden Bereich. Sie werden in der Nähe der Hand angezeigt.

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a>Prefabs

Prefabs in der Nähe von Menüs veranschaulichen, wie die verschiedenen MRTK-Komponenten verwendet werden, um Menüs für Interaktionen in der Nähe zu erstellen.

- **NearMenu2x4.prefab**
- **NearMenu3x1.prefab**
- **NearMenu3x2.prefab**
- **NearMenu3x3.prefab**
- **NearMenu4x1.prefab**
- **NearMenu4x2.prefab**

## <a name="example-scene"></a>Beispielszene

Beispiele für Prefabs in der Nähe von Menüs finden Sie in der `NearMenuExamples` Szene.

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a>Struktur

Prefabs in der Nähe von Menüs werden mit den folgenden MRTK-Komponenten erstellt.

- [**Prefab PressableButtonHoloLens2**](button.md)
- [**Rasterobjektauflistung:**](object-collection.md)Layout mehrerer Schaltflächen im Raster
- [**Bearbeitungshandler:**](manipulation-handler.md)Greifen Sie das Menü an, und verschieben Sie es.
- RadialView Solver: Follow Me(tag-along) behavior (RadialView Solver: Follow Me(tag-along)behavior [**(RadialView-Solver:**](solvers/solver.md)Follow Me(tag-along)

![Prefab im Menü "Near"](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>Vorgehensweise beim Anpassen

**1. Hinzufügen/Entfernen von Schaltflächen**

Fügen Sie unter `ButtonCollection` dem -Objekt Schaltflächen hinzu, oder entfernen Sie sie.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2. Aktualisieren der Grid-Objektauflistung**

Klicken Sie im Inspektor des Objekts auf `Update Collection` die Schaltfläche `ButtonCollection` . Das Rasterlayout wird aktualisiert.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

Sie können die Anzahl der Zeilen mithilfe `Rows` der -Eigenschaft der Grid-Objektauflistung konfigurieren.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

**3. Anpassen der Backplate-Größe**

Passen Sie die Größe des unter dem `Quad` `Backplate` -Objekt an. Die Breite und Höhe der Backplate sollte `0.032 * [Number of the buttons + 1]` sein. Wenn Sie beispielsweise über 3 x 2 Schaltflächen verfügen, ist die Breite der Backplate `0.032 * 4` und die Höhe `0.032 * 3` . Sie können diesen Ausdruck direkt in das -Feld von Unity aufnehmen.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- Die Standardgröße der schaltfläche HoloLens 2 beträgt 3,2 x 3,2 cm (0,032 m).

## <a name="see-also"></a>Siehe auch

- [**Schaltflächen**](button.md)
- [**Begrenzungssteuerelement**](bounds-control.md)
- [**Schieberegler**](sliders.md)
- [**Grid-Objektauflistung**](object-collection.md)
- [**Manipulationshandler**](manipulation-handler.md)
- [**RadialView-Solver**](solvers/solver.md)
