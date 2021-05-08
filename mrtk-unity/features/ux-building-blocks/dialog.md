---
title: Dialog
description: Beschreibung für Dialogsteuerelemente.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 729c3f6a6b9bc63a498c5d76205a0730f52c678a
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489190"
---
# <a name="dialog"></a>Dialog

![Dialog](../images/dialog/MRTK_UX_Dialog_Main.png)

Dialogsteuerelemente sind Benutzeroberflächenüberlagerungen, die kontextbezogene App-Informationen bereitstellen. Sie verlangen häufig eine Aktion vom Benutzer. Verwenden Sie Dialogfelder, um Benutzern wichtige Informationen mitzuteilen oder deren Bestätigung bzw. zusätzliche Informationen anzufordern, bevor eine Aktion abgeschlossen werden kann.

## <a name="example-scene"></a>Beispielszene

Beispiele finden Sie in der **DialogExample-Szene** unter: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)

## <a name="how-to-use-dialog-control"></a>Verwenden des Dialogsteuerelements

MRTK stellt drei Dialogpräfabs bereit:

- DialogSmall_192x96.prefab
- DialogMedium_192x128.prefab
- DialogLarge_192x192.prefab

Verwenden Sie Dialog.Open(), um ein neues Dialogfeld zu öffnen. Geben Sie das Prefab des Dialogfelds, die Anzahl der Schaltflächen, den Titeltext, den Meldungstext, die Platzierungsentfernung (nah oder fern) und zusätzliche Variablen an. Das Dialogfeld enthält die Dialogfeldoptionen "Confirmation(single button)" und "Choice(two-buttons)".

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>Beispiel für das Öffnen eines großen Dialogfelds mit einer einzelnen SCHALTFLÄCHE "OK", die im fernen Interaktionsbereich platziert wird (Anvieren, Handstrahl, Motion Controller)

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a>Beispiel für das Öffnen eines kleinen Dialogfelds, das eine Auswahlnachricht für den Benutzer enthält, die sich in der Nähe des Interaktionsbereichs befindet (direkte Handinteraktion).

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

Weitere Informationen finden Sie `DialogExampleController.cs` in der DialogExample.unity-Szene.
