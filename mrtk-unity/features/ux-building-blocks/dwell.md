---
title: Verweilen
description: Verweilinteraktion
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Verweilen, Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 8ac63ee723cdd524ee7abbad7fd2658b446156adbd5ddee06ae1795edb3b68d1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226906"
---
# <a name="dwell"></a>Verweilen

![Verweilen-Hero](../images/dwell/MRTK_UX_Dwell.png)

Anvieren mit dem Kopf und Verweilen eignen sich hervorragend für Szenarien, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind. Das Feature ist auch nützlich, wenn die Stimme aufgrund von Umgebungs- oder sozialen Einschränkungen nicht zu 100 % zuverlässig oder verfügbar ist.
Die Verweilbeispiele des MRTK veranschaulichen verschiedene Arten von Benutzeroberflächenkomponenten mit konfigurierbarer Antwortzeit und visuellem Feedback.

Die Entwurfsempfehlungen finden Sie auf der Seite Mit dem Kopf anv und [Verweilrichtlinien.](/windows/mixed-reality/design/gaze-and-dwell-head)

## <a name="dwell-scripts"></a>Verweilskripts

- **Verweilhandler:** Fügt dem Benutzeroberflächenziel eine Verweilmodalität hinzu.
- **Verweilzustandstyp:** Die Zustände des Verweilhandlers.
- **VerweilenUnityEvent:** Unity-Ereignis für ein Verweilereignis. Enthält den Zeigerverweis.
- **BaseDwellPressableButton.cs:** Ein Skript, das das OnClick()-Ereignis in `Interactable` der Prefabs PressableButtonHoloLens2 auslöst.
- **ToggleDwellPressableButton.cs:** Dieses Skript ändert `_BorderWidth` die -Eigenschaft von `dwellVisualImage` , die den MRTK-Standard-Shader verwendet.

## <a name="dwell-profiles"></a>Verweilprofile
Verweilprofile werden vom **Verweilhandler** verwendet, um die verschiedenen Schwellenwerte zu konfigurieren.
- **ButtonDwellProfile.asset**
- **InstandDwellProfile.asset**
- **DwellProfileWithDecay.asset**

## <a name="prefabs"></a>Prefabs

Bei diesen Prefabs handelt es sich um Varianten des HoloLens 2 Vorfabs mit gedrückter Schaltfläche, die über zusätzliche Komponenten verfügen, um Verweilinteraktionen zu unterstützen.

- **PressableButtonHoloLens2_Dwell.prefab**
- **PressableButtonHoloLens2_32x96_Dwell.prefab**
- **PressableButtonHoloLens2ToggleDwell.prefab**
- **PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**

Diese Prefabs verfügen über eine zusätzliche Backplate-Komponente **QuadDwellVisual,** um den Verweileingabezustand zu visualisieren. Ihm ist **HolographicBackPlateDwellVisual.mat-Material** zugewiesen. **ToggleDwellPressableButton.cs** aktualisiert die **_BorderWidth-Eigenschaft** des MRTK Standard-Shaders, um die Verweileingabe zu visualisieren.

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>Beispielszene

Beispiele finden Sie in der `DwellExample` Szene. Die Beispielszene zeigt sowohl volumetrische Ui-Beispiele als auch Unity-Benutzeroberflächenbeispiele.

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>Siehe auch

- [**Schaltflächen**](button.md)
- [**Interaktionsfähig**](interactable.md)
