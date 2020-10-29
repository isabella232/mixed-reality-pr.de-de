---
title: Entwerfen von Inhalten für die holografische Anzeige
description: Entwurfs Richtlinien und bewährte Methoden für die holografische Anzeige
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Design der Benutzeroberfläche, holografische Anzeige, Inhalts Design, dunkles Design, helles Design
ms.openlocfilehash: 627ffdd0a413ad3140c29e9b1c7bb69c9dc249cf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686110"
---
# <a name="designing-content-for-holographic-display"></a>Entwerfen von Inhalten für die holografische Anzeige

![Ulnar Seitenposition](images/UX_Hero_DarkTheme.jpg)

Beim Entwerfen von Inhalten für Holographic-anzeigen müssen Sie mehrere Elemente beachten, um die bestmögliche Leistung zu erzielen. Wir haben einige unserer unten aufgeführten Empfehlungen aufgelistet, und Sie können mehr über die Merkmale der Holographic-Anzeige auf der Seite [Farbe, hell und Material](color-light-and-materials.md) erfahren.

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>Herausforderungen mit heller Farbe auf hoher Oberfläche 
Basierend auf unserer Recherche und dem Testen verschiedener Arten von hololens-Erfahrungen haben wir festgestellt, dass die Verwendung von hellen Farben in einem großen Bereich der Anzeige verschiedene Probleme verursachen kann: 

**Augen Müdigkeit** 

Da die holografische Anzeige Additiv ist, verwendet die helle Farbe zum Anzeigen von holograms mehr Licht. Eine helle, voll Tonfarbe in einem großen Bereich der Anzeige kann die Augen Müdigkeit für den Benutzer leicht auslösen. 

**Hand Okklusion** 

Durch eine helle Farbe ist es für den Benutzer schwierig, die Hände bei direkter Interaktion mit Objekten zu sehen. Da der Benutzer seine Hände nicht sehen kann, ist es schwierig, die Tiefe/Entfernung zwischen der Hand/dem Finger und der Ziel Oberfläche zu erkennen. Mit dem Finger Cursor kann dieses Problem kompensiert werden, aber es kann auf einer hellen weißen Oberfläche immer noch eine Herausforderung darstellen. 

![Die Farb-und Handzeichen-oksion ist ](images/color_handocclusion.jpg)
 *schwierig, um das Hintergrundbild der hellfarbigen Inhalte anzuzeigen* .

**Farb Einheitlichkeit**

Aufgrund der Merkmale von Holographic-anzeigen kann ein großer heller Bereich in der Anzeige zu einem blobbereich werden. Durch die Verwendung von dunklen Farbschemas können Sie dieses Problem minimieren. 

## <a name="design-guidelines"></a>Entwurfsrichtlinien

**Verwenden Sie die dunkle Farbe für den UI-Hintergrund.**

Mithilfe des dunklen Farbschemas können Sie die Augen Müdigkeit minimieren und die Zuversicht bei direkten Interaktionen verbessern. 

![Beispiele für dunkle Benutzeroberflächen Beispiele für ](images/color_dark_examples.jpg)
 *dunkle Farben, die für den Inhalts Hintergrund verwendet werden*

**Semibold oder Fett formatierte Schrift Breite verwenden**

Hololens ermöglicht Ihnen die Anzeige von schönem Text mit hoher Auflösung. Es wird jedoch empfohlen, schlanke Schriftart Gewichtungen, wie z. b. Light oder semilight, zu vermeiden, da die vertikalen Striche in einem kleinen Schrift Grad Jitter sind. 

![Dunkle UI-Beispiele ](images/color_font_examples.jpg)
 *Fett oder Semibold Schrift Breite (oberer Bereich) verbessert die Lesbarkeit*

**Verwenden des holographicbackplate-Materials von mrtk**

Das holographicbackplate-Material wird auf mehrere Benutzeroberflächen Panels in der hololens-Shell angewendet. Eine seiner Features ist ein Iridescence-Effekt, der für Benutzer sichtbar ist, wenn Sie Ihre Position in Bezug auf den Bereich verschieben. Die Hintergrundfarbe verschiebt sich ganz leicht über ein vordefiniertes Spektrum, sodass ein ansprechender und dynamischer visueller Effekt entsteht, ohne die Lesbarkeit von Inhalten zu beeinträchtigen. Diese feine UMSCHALT Farbe dient auch zur Kompensation geringfügiger Farb Unregelmäßigkeiten. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>Herausforderungen mit transparenten oder durchlässigen UI-Backplate 
![Transparente Benutzeroberflächen Beispiele ](images/color_transparent_examples.jpg)
 *Beispiele für transparente UI-Backplate*

**Visuelle Komplexität und Barrierefreiheit**

Da Holographic-Objekte mit der physischen Umgebung kombiniert werden, kann die Lesbarkeit des Inhalts oder der Benutzeroberfläche im transparenten oder durchlässigen Fenster beeinträchtigt werden. Darüber hinaus kann es bei der Überlagerung transparenter Holographic-Objekte aufgrund der verwirrenden Tiefe schwierig sein, eine Interaktion zwischen den Benutzern zu ermöglichen.

**Leistung**

Damit transparente oder über lässiges Objekte ordnungsgemäß dargestellt werden, müssen Sie sortiert und mit allen Objekten kombiniert werden, die im Hintergrund vorhanden sind. Das Sortieren von transparenten Objekten hat eine geringe Anzahl von CPU-Kosten. die Kombination hat beträchtliche GPU-Kosten, da die GPU die ausgeblendete Oberflächen Entfernung durch z-Culling (d. h. tiefen Tests). Wenn Sie das Entfernen ausgeblendeter Oberflächen nicht zulassen, erhöht sich die Anzahl der Vorgänge, die für das endgültige gerenderte Pixel berechnet werden müssen, und erhöht somit den Druck von Füll Raten Einschränkungen.

**Hologram-Stabilitätsproblem mit der tiefen LSR-Technologie**

Um die Holographic-neuprojektion bzw. – Hologramm-Stabilität zu verbessern, kann eine Anwendung für jeden gerenderten Frame einen tiefen Puffer an das System übermitteln. Bei der Verwendung des tiefen Puffers für die neuprojektion besteht eine Regel darin, dass für jedes dargestellte Farbpixel ein entsprechender tiefen Wert in den tiefen Puffer geschrieben werden muss (und jedes Pixel mit einem tiefen Wert auch einen Farbwert aufweisen sollte). Wenn die oben genannten Anleitungen nicht befolgt werden, können Bereiche des gerenderten Bilds, die keine gültigen Tiefeninformationen aufweisen, auf eine Weise neu projiziert werden, die Artefakte erzeugt (häufig als Wellen ähnliche Verzerrung sichtbar).


## <a name="design-guidelines"></a>Entwurfsrichtlinien
**Verwenden von undurchsichtigem UI-Hintergrund**

Standardmäßig werden von transparenten oder durchlässigen Objekten keine tiefen geschrieben, um eine ordnungsgemäße Mischung zu ermöglichen. Zu den Möglichkeiten, dieses Problem zu beheben, gehören die Verwendung von nicht transparenten Objekten, das sicherstellen, dass die übergreifenden Objekte nahe bei nicht transparenten Objekten angezeigt werden (z. b. eine durchlässige Schaltfläche vor einem nicht transparenten Backplate), das Erzwingen von durchlässigen Objekten, um Tiefe zu schreiben (in allen Szenarien nicht zutreffend), oder das Rendern von Proxy Objekten

Lösungen in mrtk-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity  

Durch die Verwendung eines soliden und nicht transparenten Backplate können wir die Zuverlässigkeit und Interaktion gewährleisten.

**Minimieren der Anzahl der betroffenen Pixel**

Wenn das Projekt transparente Objekte verwenden muss, versuchen Sie, die Anzahl der betroffenen Pixel zu minimieren. Wenn ein Objekt z. b. nur unter bestimmten Bedingungen (wie z. b. einem Additiven Glanzeffekt) sichtbar ist, deaktivieren Sie das Objekt, wenn es vollständig unsichtbar ist (anstatt die Additiv Farbe auf schwarz festzulegen). Für einfache 2D-Formen, die mit einem Quad mit einer Alpha Maske erstellt wurden, sollten Sie stattdessen eine Gitterdarstellung der Form mit einem nicht transparenten Shader erstellen. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Beispiele für dunkle Benutzeroberflächen in mrtk (Mixed Reality Toolkit) für Unity
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** bietet viele Beispiele für Benutzeroberflächen Bausteine, die auf den dunklen Farbschemas basieren.

* [Near-Menü](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [Dialogfeld](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [Hand Menü](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a>Weitere Informationen
* [Farbe, Licht und Materialien](color-light-and-materials.md)
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
