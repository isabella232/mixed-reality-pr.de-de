---
title: QuickInfo
description: Übersicht über Tooltipps im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, QuickInfo,
ms.openlocfilehash: af848db0962948b1f2ada73066c4ae90730b09a99dea231ebf468a05441b85ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193254"
---
# <a name="tooltip"></a>QuickInfo

![QuickInfo–Haupt](../images/tooltip/MRTK_Tooltip_Main.png)

QuickInfos werden in der Regel verwendet, um einen Hinweis oder zusätzliche Informationen bei näherer Untersuchung eines Objekts zu übermitteln. QuickInfos können verwendet werden, um Objekte in der physischen Umgebung mit Anmerkungen zu kommentieren.

## <a name="how-to-use-a-tooltip"></a>Verwenden einer QuickInfo

Eine QuickInfo kann direkt zur Hierarchie hinzugefügt und auf ein Objekt ausgerichtet werden.

Um diese Methode zu verwenden, fügen Sie der Szenenhierarchie einfach ein Spielobjekt und eine der QuickInfo-Prefabs (Assets/MRTK/SDK/Features/UX/Prefabs/QuickInfos) hinzu. Erweitern Sie im Inspektorbereich des Prefabs das [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) Skript. Wählen Sie einen Trinkgeldstatus aus, und konfigurieren Sie die QuickInfo.  Geben Sie den entsprechenden Text für den Tipp in das Textfeld ein. Erweitern Sie das Skript, und ziehen Sie das Objekt, das die QuickInfo aus der Hierarchie erhalten soll, in das [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) Feld Target ( Ziel *).* Dadurch wird die QuickInfo an das -Objekt angefügt.
![QuickInfo-Connector](../images/tooltip/MRTK_Tooltip_Connector.png)

Bei dieser Verwendung wird von einer QuickInfo ausgegangen, die immer angezeigt wird oder die per Skript angezeigt/ausgeblendet wird, indem die QuickInfo-Statuseigenschaft der QuickInfo-Komponente geändert wird.

## <a name="dynamically-spawning-tooltips"></a>Dynamisches Erstellen von QuickInfos

Eine QuickInfo kann einem Objekt zur Laufzeit dynamisch hinzugefügt und vorab festgelegt werden, um tippen oder den Fokus auszublenden. Fügen Sie einfach [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) das Skript einem beliebigen Spielobjekt hinzu. Verzögerungen beim Erscheinen und Verschwinden können im Skriptinspektor sowie eine Lebensdauer festgelegt werden, sodass die QuickInfo nach einer festgelegten Dauer nicht mehr angezeigt wird. QuickInfos enthalten auch Stileigenschaften wie visuelle Hintergrundvisutiken im Spawnerskript. Standardmäßig wird die QuickInfo mit dem Spawnerskript im Objekt verankert. Dies kann geändert werden, indem dem Ankerfeld ein GameObject zugewiesen wird.

## <a name="example-scene"></a>Beispielszene

In den Beispielszenen (Assets/MRTK/Examples/Demos/UX/QuickInfos/Scenes) finden Sie verschiedene Beispiele für QuickInfos.

![QuickInfo-Beispiele](../images/tooltip/MRTK_Tooltip_Examples.png)
