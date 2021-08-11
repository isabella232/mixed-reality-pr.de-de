---
title: Andocken
description: Beschreibung für Dock-Steuerelemente.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 4446dbe3199aab63d7ee85474d3696a45cf4401f1d8100a8d99885a7265c7fe2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226572"
---
# <a name="dock"></a>Andocken

![Andocken](../images/dock/MRTK_UX_Dock_Main.png)

Dieses Steuerelement ermöglicht das Verschieben von Objekten in und aus vordefinierten Positionen, um Paletten, Ablageflächen und Navigationsleisten zu erstellen.

## <a name="features"></a>Funktionen

- Unterstützt eine beliebige Anzahl von Dockpositionen und Layouts (funktioniert hervorragend mit [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) )
- Angedockte Objekte werden automatisch entfernt, um Platz für neue Objekte zu schaffen.
- Objekte werden so skaliert, dass sie an den angedockten Raum passen, und dann die Größe an ihre ursprüngliche Position anpassen, wenn sie herausgezogen werden.

## <a name="getting-started-with-dock"></a>Erste Schritte mit Dock

- Erstellen Sie ein GameObject mit der Dock-Komponente, und fügen Sie ihm einige untergeordnete GameObjects hinzu.
- Fügen Sie jedem untergeordneten Element die DockPosition-Komponente hinzu.
- Fügen Sie die Dockable-Komponente einer beliebigen Anzahl von Objekten in der Szene hinzu, damit sie angedockt werden können. Sie müssen auch über die [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) Komponente und einen Collider verfügen.
- *Optional:* Verwenden Sie ein [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) im Dock, um die DockPositions automatisch zu erstellen.

### <a name="prerequisites"></a>Voraussetzungen

- Jedes andockbare Objekt muss über einen Collider mit einem [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) oder [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) verfügen.
- Wenn ein Objekt beim Laden der Szene angedockt gestartet werden soll, weisen Sie es jeder DockPosition-Eigenschaft für angedockte Objekte zu.

## <a name="how-it-works"></a>Funktionsweise

Die Dockable-Komponente baut auf Manipulationsereignissen auf, damit gezogene Objekte an bestimmten Positionen angedockt und abgedockt werden können. Die Platzierung wird durch die nächstgelegene überlappende ausgelöste DockPosition für das gezogene Objekt bestimmt, sodass beide Objekte über Collider verfügen müssen, damit der Trigger aktiviert werden kann.
