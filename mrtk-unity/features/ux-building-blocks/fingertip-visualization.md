---
title: Fingerspitzenvisualisierung
description: Übersicht über die Fingerspitzenvisualisierung in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Fingerspitze
ms.openlocfilehash: af23fdb9b618e276b7442405e54b7dccd141e4ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177534"
---
# <a name="fingertip-visualization"></a>Fingerspitzenvisualisierung

![Fingerspitzenvisualisierung Main](../images/fingertip/MRTK_FingertipVisualization_Main.png)

Das Fingerspitzen-Affordance hilft dem Benutzer, den Abstand zum Zielobjekt zu erkennen. Das Visuelle Ringform passt seine Größe basierend auf dem Abstand zwischen der Fingerspitze und dem Objekt an. Die Fingerspitzenvisualisierung wird in erster Linie durch `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab) (und Skript) gesteuert, die als Cursor-Prefab des *PokePointer* erstellt wird. Weitere Komponenten der Visualisierung sind das *ProximityLight-Skript* und *der MixedRealityStandard-Shader.*

## <a name="how-to-use-the-fingertip-visualization"></a>Verwenden der Fingerspitzenvisualisierung

Standardmäßig funktioniert die Fingerspitzenvisualisierung in jeder Unity-Szene, die so konfiguriert ist, dass ein FingerCursor erstellt wird. Der FingerCursor wird im *DefaultMixedRealityToolkitConfigurationProfile* unter folgenden Bedingungen erstellt:

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*

Im Großen und Ganz funktioniert die Fingerspitzenvisualisierung mithilfe eines Näherungslichts, um einen farbigen Farbverlauf auf allen nahe gelegenen Oberflächen zu projektieren, die Näherungslichter akzeptieren. Der Fingercursor sucht dann nach allen in der Nähe interagierbaren Oberflächen, die vom übergeordneten -Element bestimmt werden, um den Fingerring mit einer Oberfläche auszurichten, während sich der Finger auf eine `IMixedRealityNearPointer(s)` Oberfläche bewegt. Wenn sich ein Finger einer Oberfläche nähert, wird der Fingerring auch dynamisch mithilfe der Eigenschaften der runden Ecke des MixedRealityStandard-Shaders animiert.

## <a name="example-scene"></a>Beispielszene

Beispiele für die Fingerspitzenvisualisierung finden Sie in fast jeder Szene, die mit artikulierten Händen funktioniert, aber in der [HandInteractionExample-Szene an](../example-scenes/hand-interaction-examples.md)erster Stelle steht.

![Zustände der Fingerspitzenvisualisierung](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>Inspektoreigenschaften

**FingerCursor** Viele der Fingercursoreigenschaften werden von der Basiscursorklasse geerbt. Wichtige Eigenschaften sind die Ränder und Breiten der Fern-/Nahoberfläche, die die Fingerringanimation im MixedRealityStandard-Shader animieren. Für andere Eigenschaften bewegen Sie den Hover auf die Tipps des Inspektortools.

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** Die Näherungslichteinstellungen steuern, wie das Licht in der Nähe und weit von einer Oberfläche aussieht. Die Mittel-, Mittel- und Außenfarben steuern das Farbverlaufs-Aussehen des Lichts und können für die Farbpalette Ihrer Anwendung angepasst werden. Beachten Sie, dass die Farben HDR (High Dynamic Range) sind, damit Benutzer das Näherungslicht zu Werten über 1 aufheitern können. Für andere Eigenschaften bewegen Sie den Hover auf die Tipps des Inspektortools.

**MixedRealityStandard-Shader** Der MixedRealityStandard-Shader wird für viele Effekte im MRTK verwendet. Die beiden einstellungen, die für die Fingerspitzenvisualisierung wichtig sind, sind "Near Fade" und "Near Light". Near Fade ermöglicht es Objekten, ein- bzw. ausblenden, wenn eine Kamera oder ein Licht sich ihnen nähert. Vergewissern Sie sich, dass Sie "Light" (Licht) aktivieren, damit Näherungslichter das Ausblenden (und nicht die Kamera) voranfahren können. Sie können die Werte von "Fade Begin" und "Fade Complete" umkehren, um ein Ausblenden umzukehren. Überprüfen Sie "Näherungslicht" auf jede Oberfläche, die das Näherungslicht aufheitern soll. Für andere Eigenschaften bewegen Sie den Hover auf die Tipps des Inspektortools.

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
