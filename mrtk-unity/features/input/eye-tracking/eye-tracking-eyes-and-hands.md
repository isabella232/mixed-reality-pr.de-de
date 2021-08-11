---
title: Augen und Hände
description: Verwenden von Eye targeting als primärer Zeiger in Kombination mit Handbewegungen im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: 37411eb344b4efae03a00bb06a31ce56182cc724d96b2cdcc008f10a66d56011
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224758"
---
# <a name="eyes-and-hands"></a>Augen und Hände

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Unterstützung von _Blick- und Handbewegungen_ (Anvieren mit den Augen & Handgesten)

Auf dieser Seite wird erläutert, wie Sie eye targeting als primären Zeiger in Kombination mit Handbewegungen verwenden.
In unseren [MRTK-Eyetracking-Demos](../../example-scenes/eye-tracking-examples-overview.md)beschreiben wir mehrere Beispiele für die Verwendung von Augen und Händen, z. B.:

- [Auswahl:](eye-tracking-target-selection.md)Betrachten Sie die entfernte holografische Schaltfläche, und führen Sie einfach eine Geste aus, um sie schnell auszuwählen.
- **Positionierung (in diesem Artikel):** Bewegen Sie ein Hologramm in fluently über Ihre Szene, indem Sie es einfach betrachten, indem Sie ihren Zeigefinger und den Daumen zusammendrücken, um es zu greifen und es dann mit der Hand zu bewegen.
- [Navigation:](eye-tracking-navigation.md)Sehen Sie sich einfach eine Position an, an der Sie zoomen möchten, drücken Sie den Zeigefinger und den Daumen zusammen, und _ziehen_ Sie die Hand auf Sie zu, um sie zu vergrößern.

Beachten Sie, dass MRTK derzeit so konzipiert ist, dass Handlichter im Abstand als priorisierte Fokuszeiger fungieren.
Dies bedeutet, dass die Zeiger für das Anvieren mit dem Kopf und den Augen automatisch unterdrückt werden, sobald eine Hand erkannt wird, und wieder sichtbar wird, nachdem sie "Auswählen" gesagt haben.
Dies ist jedoch möglicherweise nicht die Art und Weise, wie Sie in einer Entfernung interagieren möchten, sondern bevorzugen eine einfache Interaktion _mit "Anvisieren und Committen",_ unabhängig davon, ob Die Hände in Ihrer Ansicht vorhanden sind.

### <a name="how-to-disable-the-hand-ray"></a>Deaktivieren des Handstrahls

Um den Handstrahlzeiger zu deaktivieren, entfernen Sie einfach _"DefaultControllerPointer"_ in der MrTK-Konfigurationseinstellung _Input -> Pointer._
Um Augen und Hände wie oben in Ihrer App beschrieben zu verwenden, stellen Sie außerdem sicher, dass Sie alle Anforderungen für die Verwendung von [Eyetracking](eye-tracking-basic-setup.md)erfüllen.

![Entfernen des Handstrahls](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

Sie können sich auch ansehen, wie das Eingabeprofil _EyeTrackingDemoPointerProfile_ aus dem Eye tracking-Beispielpaket als Referenz eingerichtet wird.

### <a name="how-to-keep-gaze-pointer-always-on"></a>So halten Sie den Anvzeiger immer an

Um zu vermeiden, dass kopf- oder anvisierten Zeiger automatisch unterdrückt werden, sobald eine Hand erkannt wird, kann der Anvisierten [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) angegeben werden, um zu steuern, ob sie ein- oder ausgeschaltet werden soll.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Informationen finden Sie unter [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md).

---
[Zurück zu "Eye tracking in the MixedRealityToolkit" (Blickverfolgung im MixedRealityToolkit)](eye-tracking-main.md)
