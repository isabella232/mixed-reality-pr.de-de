---
title: 'Eyetracking (Blickverfolgung): Augen und Hände'
description: Verwenden von Eye targeting als primärer Zeiger in Kombination mit Handbewegungen im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: c9d5f23610d821aa1e50a3217a4be736601dc14d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143996"
---
# <a name="eyes--hand-interaction"></a>Interaktion von Augen und Hand

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Unterstützung von _Blick- und Handbewegungen_ (Anvieren mit den Augen & Handgesten)

Auf dieser Seite wird erläutert, wie Sie eye targeting als primären Zeiger in Kombination mit Handbewegungen verwenden.
In unseren [MRTK-Eyetracking-Demos](../../example-scenes/eye-tracking-examples-overview.md)beschreiben wir mehrere Beispiele für die Verwendung von Augen und Händen, z. B.:

- [Auswahl:](eye-tracking-target-selection.md)Betrachten Sie die entfernte holografische Schaltfläche, und führen Sie einfach eine Geste aus, um sie schnell auszuwählen.
- **Positionierung (in diesem Artikel):** Bewegen Sie ein Hologramm in fluently über Ihre Szene, indem Sie es einfach betrachten, indem Sie ihren Zeigefinger und den Daumen zusammendrücken, um es zu greifen und es dann mit der Hand zu bewegen.
- [Navigation:](eye-tracking-navigation.md)Sehen Sie sich einfach eine Position an, an der Sie zoomen möchten, heften Sie den Zeigefinger und den Daumen zusammen, und _ziehen_ Sie die Hand auf Sie, um sie zu vergrößern.

Beachten Sie, dass MRTK zurzeit so konzipiert ist, dass handgestrahlte Lichtstrahle im Abstand als priorisierte Fokuszeiger fungieren.
Dies bedeutet, dass die Zeiger für den Kopf und das Anvieren mit den Augen automatisch unterdrückt werden, sobald eine Hand erkannt wird, und wieder sichtbar wird, nachdem sie "Auswählen" gesagt haben.
Dies ist jedoch möglicherweise nicht die Art und Weise, wie Sie in einer Entfernung interagieren möchten, und bevorzugen stattdessen eine einfache Interaktion _mit anvisieren und committen,_ unabhängig davon, ob Die Hände in Ihrer Ansicht vorhanden sind.

### <a name="how-to-disable-the-hand-ray"></a>Deaktivieren des Handstrahls

Um den Handstrahlzeiger zu deaktivieren, entfernen Sie einfach _"DefaultControllerPointer"_ in der MrTK-Konfigurationseinstellung _Input -> Pointer._
Um Augen und Hände wie oben in Ihrer App beschrieben zu verwenden, stellen Sie außerdem sicher, dass Sie alle Anforderungen für die Verwendung von [Eyetracking](eye-tracking-basic-setup.md)erfüllen.

![Entfernen des Handstrahls](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

Sie können sich auch ansehen, wie das Eingabeprofil _EyeTrackingDemoPointerProfile_ aus dem Eye tracking-Beispielpaket als Referenz eingerichtet wird.

### <a name="how-to-keep-gaze-pointer-always-on"></a>So halten Sie den Anvzeiger immer an

Um zu vermeiden, dass die Zeiger für den Kopf oder das Anvisierten mit den Augen automatisch unterdrückt werden, sobald eine Hand erkannt wird, kann der Anvisierten [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) angegeben werden, um zu steuern, ob sie ein- oder ausgeschaltet werden soll.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Informationen finden Sie unter [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md).

---
[Zurück zu "Eye tracking in the MixedRealityToolkit" (Blickverfolgung im MixedRealityToolkit)](eye-tracking-main.md)
