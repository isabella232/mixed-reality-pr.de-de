---
title: Augen und Hände
description: Verwenden der Blickadressierung als primärer Zeiger in Kombination mit Handbewegungen im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: ff464c6f2381a9df020a9ccf807672d4463d662c
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175114"
---
# <a name="eyes-and-hands"></a>Augen und Hände

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Unterstützung von _Blick- und Handbewegungen_ (anv & Handgesten)

Auf dieser Seite wird erläutert, wie Sie die Blickadressierung als primären Zeiger in Kombination mit Handbewegungen verwenden.
In unseren [MRTK-Eyetracking-Demos](../../example-scenes/eye-tracking-examples-overview.md)beschreiben wir mehrere Beispiele für die Verwendung von Augen und Händen, z. B.:

- [Auswahl:](eye-tracking-target-selection.md)Sehen Sie sich die entfernte holografische Schaltfläche an, und führen Sie einfach eine Heftbewegung aus, um sie schnell auszuwählen.
- **Positionierung (dieser Artikel):** Bewegen Sie ein Hologramm fluently über Ihre Szene, indem Sie es einfach an sehen, den Zeigefinger und den Zeigefinger zusammendrippen, um es zu greifen und es dann mit der Hand zu bewegen.
- [Navigation:](eye-tracking-navigation.md)Sehen Sie sich einfach eine Position an, an der  Sie zoomen möchten, heften Sie den Zeigefinger und den Zeigefinger zusammen, und ziehen Sie Ihre Hand zu Ihnen, um sie zu vergrößern.

Beachten Sie, dass MRTK derzeit so konzipiert ist, dass Handlichtlichter aus der Entfernung als priorisierte Fokuszeder fungieren.
Dies bedeutet, dass die Anvitätszeigen mit dem Kopf und den Augen automatisch unterdrückt werden, sobald eine Hand erkannt wird, und nach dem Sagen von "Auswählen" wieder sichtbar wird.
Dies ist jedoch möglicherweise nicht die Art und Weise, wie  Sie aus der Entfernung interagieren möchten und stattdessen eine einfache "Anvisieren und Commit"-Interaktion bevorzugen, unabhängig vom Vorhandensein der Hände in Ihrer Ansicht.

### <a name="how-to-disable-the-hand-ray"></a>Deaktivieren des Handstrahls

Um den Handstrahlzeiger zu deaktivieren, entfernen Sie einfach _den "DefaultControllerPointer"_ in der _Konfigurationseinstellung Input -> Pointer_ MRTK.
Um Augen und Hände wie oben in Ihrer App beschrieben zu verwenden, stellen Sie außerdem sicher, dass Sie alle Anforderungen für die Verwendung von [Eyetracking erfüllen.](eye-tracking-basic-setup.md)

![Entfernen des Handstrahls](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

Sie können auch überprüfen, wie das Eingabeprofil _EyeTrackingDemoPointerProfile_ aus dem EyeTracking-Beispielpaket als Referenz eingerichtet wird.

### <a name="how-to-keep-gaze-pointer-always-on"></a>So halten Sie den Anvingzeiger immer auf

Um zu vermeiden, dass die Anvitätszeigen mit dem Kopf oder den Augen automatisch unterdrückt werden, sobald eine Hand erkannt wird, kann der Anvitäts-Parameter angegeben werden, um zu steuern, ob er ein- oder [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) ausgeschaltet werden soll.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Informationen finden Sie unter [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md).

---
[Zurück zu "Eye tracking in the MixedRealityToolkit"](eye-tracking-main.md)
