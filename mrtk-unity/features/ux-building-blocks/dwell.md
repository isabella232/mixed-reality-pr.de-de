---
title: Wohnen
description: Interaktion zwischen Verweilen
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Dwell, Unity, HoloLens, HoloLens 2, Mixed Reality, development, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647799"
---
# <a name="dwell"></a>Wohnen

![Verweilreiher (Hero)](../images/dwell/MRTK_UX_Dwell.png)

Das Anvieren und Verweilen mit dem Kopf ist gut in Szenarien, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind. Das Feature ist auch nützlich, wenn die Stimme aufgrund von Umgebungs- oder sozialen Einschränkungen nicht zu 100 % zuverlässig oder verfügbar ist.
MrTK-Verweilbeispiele veranschaulichen verschiedene Arten von Benutzeroberflächenkomponenten mit konfigurierbarer Antwortzeit und visuellem Feedback.

Die [Entwurfsempfehlungen finden Sie](/windows/mixed-reality/design/gaze-and-dwell-head) auf der Seite Mit dem Kopf anving und verweilen.

## <a name="dwell-scripts"></a>Verweilskripts

- **DwellHandler:** Fügt dem Benutzeroberflächenziel eine Verweilmodalität hinzu.
- **DwellStateType:** Die Zustände des Verweilhandlers.
- **DwellUnityEvent:** Unity-Ereignis für ein Verweilereignis. Enthält den Zeigerverweis.
- **BaseDwellPressableButton.cs:** Ein Skript, das das OnClick()-Ereignis in der `Interactable` PressableButtonHoloLens2-Prefabs auslöst.
- **ToggleDwellPressableButton.cs:** Dieses Skript ändert die -Eigenschaft von , `_BorderWidth` `dwellVisualImage` die den MRTK-Standard-Shader verwendet.

## <a name="dwell-profiles"></a>Verweilprofile
Verweilprofile werden vom **Verweilhandler verwendet,** um die verschiedenen Schwellenwerte zu konfigurieren.
- **ButtonDwellProfile.asset**
- **InstandDwellProfile.asset**
- **DwellProfileWithDecay.asset**

## <a name="prefabs"></a>Prefabs

Bei diesen Prefabs handelt es sich um Varianten der HoloLens 2- und Drucktasten-Prefabs, die zusätzliche Komponenten zur Unterstützung von Verweilinteraktionen enthalten.

- **PressableButtonHoloLens2_Dwell.prefab**
- **PressableButtonHoloLens2_32x96_Dwell.prefab**
- **PressableButtonHoloLens2ToggleDwell.prefab**
- **PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**

Diese Prefabs verfügen über eine zusätzliche Backplate-Komponente **QuadDwellVisual,** um den Eingabezustand des Verweilzustands zu visualisieren. Ihm ist **HolographicBackPlateDwellVisual.mat-Material** zugewiesen. **ToggleDwellPressableButton.cs** aktualisiert  die _BorderWidth-Eigenschaft des MRTK Standard-Shaders, um die Verweileingabe zu visualisieren.

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>Beispielszene

Beispiele finden Sie in der `DwellExample` Szene. Die Beispielszene zeigt Beispiele für volumetrischen Ui und Unity-Benutzeroberflächenbeispiele.

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>Siehe auch

- [**Schaltflächen**](button.md)
- [**Interaktionsfähig**](interactable.md)
