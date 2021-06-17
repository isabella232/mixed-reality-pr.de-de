---
title: Begrenzungsrahmen und App-Leiste
description: Die App-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Grenzen eines Hologramms angezeigt werden.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, Begrenzungsfeld, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5c437b303ec5462179a1ddf43687aa1653419b08
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110097"
---
# <a name="bounding-box-and-app-bar"></a>Begrenzungsrahmen und App-Leiste
![Bounding ist die Standardschnittstelle für die Objektbearbeitung in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>Was ist das Begrenzungsfeld?

Bounding ist die Standardschnittstelle für die Objektbearbeitung in Mixed Reality. Dieses Feature gibt dem Benutzer einen visuellen Hinweis, dass das Objekt derzeit anpassbar ist. Auf HoloLens 2 arbeitet der Begrenzungsfeld mit direkter Handbearbeitung und reagiert auf die Nähe des Benutzers. Es zeigt visuelles Feedback, das dem Benutzer hilft, den Abstand zum Objekt zu erkennen.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Skalieren eines Objekts<br>
        Die Ecken des Begrenzungsfelds informieren den Benutzer darüber, dass das Objekt skaliert werden kann. Die Handles folgen einem weit verbreiteten Muster zum Anpassen der Skalierung. Dieser visuelle Hinweis zeigt Benutzern den gesamten Bereich des Objekts an – auch wenn er außerhalb eines Anpassungsmodus nicht sichtbar ist. Ohne diese Funktion scheint sich ein Objekt, das an einem anderen Objekt oder einer anderen Oberfläche gezippt ist, so zu verhalten, als ob es sich um ein Objekt herum gab, das nicht dort sein sollte.<br>
        <br>
        *Videoschleife: Skalieren eines Objekts über ein Begrenzungsfeld*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens-Ansicht zum Skalieren eines Objekts über ein Begrenzungsfeld](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Drehen eines Objekts<br>
        Die vertikalen rechteckigen Ränder an den Rändern des Begrenzungsfelds sind Drehungsindikatoren. Dies ermöglicht dem Benutzer eine feiner anpassung an die platzierten Hologramme. Sie können nicht nur anpassen und skalieren, sondern sich jetzt auch drehen.<br>
        <br>
        *Videoschleife: Drehen eines Objekts über ein Begrenzungsfeld*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens-Ansicht zum Drehen eines Objekts über ein Begrenzungsfeld](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Visuelles Feedback zur Nähe zu HoloLens 2<br>
        Auf HoloLens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung der Tiefe des Benutzers unterstützen kann. Ein Ring in der Nähe ihrer Fingerspitze wird angezeigt und skaliert herunter, wenn sich die Fingerspitze dem Objekt nähert. Der Ring konvergiert schließlich zu einem Punkt, wenn der gedrückte Zustand erreicht wird. Dieses visuelle Modell hilft dem Benutzer zu verstehen, wie weit er vom Objekt entfernt ist.<br>
        <br>
        *Videoschleife: Beispiel für visuelles Feedback basierend auf der Nähe zu einem Begrenzungsfeld*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Visuelles Feedback zur Nähe](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Informationen zur Entwicklung von Unity-Apps finden Sie unter [Begrenzungsfeld im Mixed Reality Toolkit-Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**

<br>

---

## <a name="what-is-the-app-bar"></a>Was ist die App-Leiste?

Die App-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Grenzen eines Hologramms angezeigt werden. Dieses Muster wird häufig verwendet, damit Benutzer Hologramme entfernen und anpassen können. Die App-Leiste wurde hauptsächlich als Möglichkeit zum Verwalten platzierter Objekte in der Umgebung eines Benutzers entworfen. In Kombination mit dem Begrenzungsfeld hat ein Benutzer die vollständige Kontrolle darüber, wo und wie Objekte in Mixed Reality ausgerichtet sind.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>Die App-Leiste folgt dem Benutzer.<br>
        Da dieses Muster mit Objekten verwendet wird, die in der Welt gesperrt sind, wird die App-Leiste immer auf der Objektseite angezeigt, die dem Benutzer am nächsten ist, wenn sich ein Benutzer um das Objekt bewegt. Dieses Feature ist technisch gesehen zwar nicht versiert, erzielt aber effektiv das gleiche Ergebnis. Verhindern, dass die Position eines Benutzers Funktionen verdecken oder blockieren kann, die andernfalls an einem anderen Ort in seiner Umgebung verfügbar wären. <br>
        <br>
        *Videoschleife: Wenn Sie ein Hologramm umgehen, folgt die App-Leiste.*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Gehen Sie ein Hologramm um. Die App-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Begrenzungsfeld im MRTK (Mixed Reality Toolkit) für Unity
**[MRTK stellt](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Skripts und Prefabs für das Begrenzungsfeld und die App-Leiste zur Verfügung. Sie können ein Begrenzungsfeld hinzufügen, indem Sie das BoundingBox.cs-Skript einem beliebigen Objekt zuweisen.

* [MRTK – Begrenzungsfeld](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a>Siehe auch

* [Cursor](cursors.md)
* [Handstrahl](point-and-commit.md)
* [Schaltfläche](button.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Begrenzungsrahmen und App-Leiste](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Handmenü](hand-menu.md)
* [Nähemenü](near-menu.md)
* [Objektsammlung](object-collection.md)
* [Sprachbefehl](voice-input.md)
* [Tastatur](keyboard.md)
* [QuickInfo](tooltip.md)
* [Filmklappe](slate.md)
* [Schieberegler](slider.md)
* [Shader](shader.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
* [Anzeigen des Fortschritts](progress.md)
* [Oberflächenmagnetismus](surface-magnetism.md)