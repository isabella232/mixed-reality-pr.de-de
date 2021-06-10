---
title: Begrenzungsrahmen und App-Leiste
description: Die App-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines Hologramms angezeigt werden.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, App-Leiste, Begrenzungsbox, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 750fb238e5b7f22998a86f71607498c8f6982076
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600519"
---
# <a name="bounding-box-and-app-bar"></a>Begrenzungsrahmen und App-Leiste
![Die Begrenzung ist die Standardschnittstelle für die Objektbearbeitung in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>Was ist der Begrenzungsfeld?

Die Begrenzung ist die Standardschnittstelle für die Objektbearbeitung in Mixed Reality. Dieses Feature bietet dem Benutzer einen visuellen Hinweis, dass das Objekt derzeit angepasst werden kann. Auf HoloLens 2 arbeitet der Begrenzungsfeld mit direkter Handbearbeitung und reagiert auf die Nähe des Benutzers. Es zeigt visuelles Feedback, damit der Benutzer den Abstand zum Objekt erkennen kann.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Skalieren eines Objekts<br>
        Die Ecken des begrenzungsfelds weisen den Benutzer an, dass das Objekt skaliert werden kann. Die Handles folgen einem allgemein verständlichen Muster zum Anpassen der Skala. Dieser visuelle Hinweis zeigt Benutzern den Gesamtbereich des Objekts – auch wenn es außerhalb eines Anpassungsmodus nicht sichtbar ist. Ohne dieses Feature verhält sich ein Objekt, das an einem anderen Objekt oder an einer anderen Oberfläche ausgerichtet wurde, möglicherweise so, als wäre ein Bereich um dieses Objekt herum vorhanden, der nicht vorhanden sein sollte.<br>
        <br>
        *Videoschleife: Skalieren eines Objekts über begrenzungsfeld*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens-Sicht der Skalierung eines Objekts über begrenzungsfeld](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Drehen eines Objekts<br>
        Die vertikalen rechteckigen Affordances an den Rändern des begrenzungsfelds sind Drehungsindikatoren. Dadurch kann der Benutzer seine platzierten Hologramme genauer anpassen. Sie können nicht nur anpassen und skalieren, sondern jetzt auch rotieren.<br>
        <br>
        *Videoschleife: Drehen eines Objekts über begrenzungsfeld*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens-Sicht der Drehung eines Objekts über begrenzungsfeld](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Visuelles Feedback zur Handnähe auf HoloLens 2<br>
        Auf HoloLens 2 gibt es einen zusätzlichen visuellen Hinweis, der dem Benutzer bei der Wahrnehmung der Tiefe helfen kann. Ein Ring in der Nähe der Fingerspitze wird nach oben angezeigt und herunterskaliert, wenn sich die Fingerspitze dem Objekt nähert. Der Ring konvergiert schließlich zu einem Punkt, wenn der gedrückte Zustand erreicht wird. Dieses visuelle Erscheinungsbild hilft dem Benutzer zu verstehen, wie weit er vom Objekt entfernt ist.<br>
        <br>
        *Videoschleife: Beispiel für visuelles Feedback basierend auf der Nähe zu einem Begrenzungsfeld*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Visuelles Feedback zur Handnähe](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Informationen zur Entwicklung von Unity-Apps finden Sie [unter Begrenzungsfeld im Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>Was ist die App-Leiste?

Die App-Leiste ist ein Menü auf Objektebene, das eine Reihe von Schaltflächen enthält, die am unteren Rand der Begrenzungen eines Hologramms angezeigt werden. Dieses Muster wird häufig verwendet, um Benutzern das Entfernen und Anpassen von Hologrammen zu ermöglichen. Die App-Leiste wurde in erster Linie als Möglichkeit zum Verwalten platzierter Objekte in der Umgebung eines Benutzers entworfen. In Verbindung mit dem Begrenzungsfeld hat ein Benutzer vollständige Kontrolle darüber, wo und wie Objekte in Mixed Reality ausgerichtet sind.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>Die App-Leiste folgt dem Benutzer.<br>
        Da dieses Muster mit objekten verwendet wird, die weltweit gesperrt sind, wird die App-Leiste immer auf der Objektseite angezeigt, die dem Benutzer am nächsten ist, wenn sich ein Benutzer um das Objekt bewegt. Technisch gesehen ist es zwar nicht sinnvoll, aber dieses Feature erzielt effektiv das gleiche Ergebnis. Verhindern, dass die Position eines Benutzers Funktionen verdeckt oder blockiert, die andernfalls von einem anderen Ort in seiner Umgebung verfügbar wären. <br>
        <br>
        *Videoschleife: Wenn Sie ein Hologramm durchlaufen, folgt die App-Leiste.*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Durchgehen eines Hologramms. Die App-Leiste folgt.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Begrenzungsfeld im MRTK (Mixed Reality Toolkit) für Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts und Prefabs für den Begrenzungsfeld und die App-Leiste bereit. Sie können ein Begrenzungsfeld hinzufügen, indem Sie das BoundingBox.cs-Skript jedem Objekt zuweisen.

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