---
title: Fingerspitzenvisualisierung
description: Übersicht über die FingerTip-Visualisierung in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Fingertip
ms.openlocfilehash: 1df1740692a2c24213f34ffa6e52c135c7e7d14f96e7d99668feab82f879f756
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193309"
---
# <a name="fingertip-visualization"></a>Fingerspitzenvisualisierung

![Fingerspitzenvisualisierung Main](../images/fingertip/MRTK_FingertipVisualization_Main.png)

Die Fingerspitzenentität hilft dem Benutzer, den Abstand zum Zielobjekt zu erkennen. Das Ringformvisual passt seine Größe basierend auf dem Abstand von der Fingerspitze zum Objekt an. Die Fingerspitzenvisualisierung wird in erster Linie durch die `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab) (und das Skript) gesteuert, die als Cursor-Prefab des Cursor-Prefabs des *Cursors erstellt* wird. Weitere Komponenten der Visualisierung sind das *ProximityLight-Skript* und der *MixedRealityStandard-Shader.*

## <a name="how-to-use-the-fingertip-visualization"></a>Verwenden der Fingerspitzenvisualisierung

Standardmäßig funktioniert die Fingerspitzenvisualisierung in jeder Unity-Szene, die zum Erstellen eines FingerCursor konfiguriert ist. Das Spawning von FingerCursor erfolgt im *DefaultMixedRealityToolkitConfigurationProfile* unter:

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > Von EinemPointer > FingerCursor*

Auf hoher Ebene funktioniert die Visualisierung der Fingerspitzen mithilfe eines Näherungslichts, um einen farbigen Farbverlauf auf allen oberflächen in der Nähe zu pro projectieren, die Näherungslichter akzeptieren. Der Fingercursor sucht dann nach allen in der Nähe interagierenden Oberflächen, die von übergeordneten bestimmt werden, `IMixedRealityNearPointer(s)` um den Fingerring an einer Oberfläche auszurichten, während sich der Finger zu einer Oberfläche bewegt. Wenn sich ein Finger einer Oberfläche nähert, wird der Fingerring auch dynamisch mithilfe der Eigenschaften der runden Ecke des MixedRealityStandard-Shaders animiert.

## <a name="example-scene"></a>Beispielszene

Beispiele für die Fingerspitzenvisualisierung finden Sie in fast jeder Szene, die mit artikulierten Händen arbeitet, aber in der [HandInteractionExample-Szene](../example-scenes/hand-interaction-examples.md)hervorgehoben ist.

![Status der Fingerspitzenvisualisierung](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>Inspektoreigenschaften

**FingerCursor** Viele der Fingercursoreigenschaften werden von der Basiscursorklasse geerbt. Wichtige Eigenschaften sind die Ränder und Breiten der fernen/nahe-Oberfläche, die die Fingerringanimation im MixedRealityStandard-Shader steuern. Für andere Eigenschaften zeigen Sie mit der Maus auf die Tipps des Inspektortools.

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** Die Einstellungen für das Näherungslicht steuern, wie das Licht aussieht, wenn es nah und weit von einer Oberfläche entfernt ist. Die zentrieren, mittleren und äußeren Farben steuern das Farbverlaufs-Aussehen des Lichts und können für die Farbpalette Ihrer Anwendung angepasst werden. Beachten Sie, dass die Farben HDR (High Dynamic Range) sind, damit Benutzer das Näherungslicht auf Werte über 1 erweitern können. Für andere Eigenschaften zeigen Sie mit der Maus auf die Tipps des Inspektortools.

**MixedRealityStandard-Shader** Der MixedRealityStandard-Shader wird für viele Effekte im MRTK verwendet. Die beiden für die Fingerspitzenvisualisierung wichtigen Einstellungen sind "Near Fade" und "Neary Light". Near Fade ermöglicht das Ein- und Ausblenden von Objekten, wenn eine Kamera oder ein Licht sie nähert. Stellen Sie sicher, dass Sie "Light" (Licht) aktivieren, damit Näherungslichter die Einblendung (anstelle der Kamera) steuern können. Sie können die Werte von "Fade Begin" und "Fade Complete" umkehren, um ein Ausblenden umzukehren. Aktivieren Sie "Näherungslicht" für jede Oberfläche, die das Näherungslicht aufleuchten soll. Für andere Eigenschaften zeigen Sie mit der Maus auf die Tipps des Inspektortools.

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
