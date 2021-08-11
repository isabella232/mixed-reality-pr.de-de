---
title: Dialog
description: Beschreibung für Dialogfeldsteuerelemente.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 5d63fcfe79a1c3b09c78f435cec3c2155b403795993f46628cf0f5743bfd42a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203676"
---
# <a name="dialog"></a>Dialog

![Dialog](../images/dialog/MRTK_UX_Dialog_Main.png)

Dialogsteuerelemente sind Benutzeroberflächenüberlagerungen, die kontextbezogene App-Informationen bereitstellen. Sie verlangen häufig eine Aktion vom Benutzer. Verwenden Sie Dialogfelder, um Benutzern wichtige Informationen mitzuteilen oder deren Bestätigung bzw. zusätzliche Informationen anzufordern, bevor eine Aktion abgeschlossen werden kann.

## <a name="example-scene"></a>Beispielszene

Beispiele finden Sie in der **DialogExample-Szene** unter: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)

## <a name="how-to-use-dialog-control"></a>Verwenden des Dialogfeld-Steuerelements

MRTK bietet drei Dialog-Prefabs:

- DialogSmall_192x96.prefab
- DialogMedium_192x128.prefab
- DialogLarge_192x192.prefab

Verwenden Sie Dialog.Open(), um ein neues Dialogfeld zu öffnen. Geben Sie das Dialogfeld-Prefab, die Anzahl der Schaltflächen, den Titeltext, den Meldungstext, die Platzierungsentfernung (nah oder fern) und zusätzliche Variablen an. Das Dialogfeld enthält die Dialogfeldoptionen "Bestätigung (einzelne Schaltfläche)" und "Auswahl (zwei Schaltflächen)".

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>Beispiel für das Öffnen eines großen Dialogfelds mit einer einzelnen Schaltfläche "OK", platziert im fernen Interaktionsbereich (Anving, Handstrahl, Bewegungscontroller)

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a>Beispiel für das Öffnen eines kleinen Dialogs, der eine Auswahlmeldung für den Benutzer enthält, die sich in einem nahezuen Interaktionsbereich befindet (direkte Handinteraktion)

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

Weitere Informationen finden Sie in `DialogExampleController.cs` der DialogExample.unity-Szene.
