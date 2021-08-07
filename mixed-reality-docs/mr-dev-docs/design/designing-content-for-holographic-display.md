---
title: Entwerfen von Inhalten für die holografische Anzeige
description: Erfahren Sie mehr über Entwurfsrichtlinien und bewährte Methoden für die holografische Anzeige auf HoloLens Geräten.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI-Design, holografische Anzeige, Inhaltsdesign, dunkles Design, helles Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Design, Pixel
ms.openlocfilehash: 1fab172f6d737b25e95b10a6dded2a5ab805e0086de8d0fae40c5a6a4ef7d805
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212948"
---
# <a name="designing-content-for-holographic-display"></a>Entwerfen von Inhalten für die holografische Anzeige

![Ulnar side hand location (Ulnar-Seitenposition)](images/UX_Hero_DarkTheme.jpg)

Beim Entwerfen von Inhalten für holografische Displays gibt es mehrere Elemente, die Sie berücksichtigen müssen, um ein optimales Erlebnis zu erzielen. Wir haben unten einige unserer Empfehlungen aufgeführt, und Sie können mehr über die Merkmale holografischer Displays auf der Seite [Farbe, Licht und Materialien](color-light-and-materials.md) erfahren.

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>Herausforderungen mit hellem Farbton auf einer großen Oberfläche 

Basierend auf unseren HoloLens erfahrungsbezogenen Untersuchungen und Tests haben wir festgestellt, dass die Verwendung von hellen Farben in einem großen Bereich der Anzeige mehrere Probleme verursachen kann: 

**Augenmüdigkeit** 

Da die holografische Anzeige additiv ist, verwenden Hologramme mit hellen Farben mehr Licht. Helle Volltonfarbe in einem großen Bereich der Anzeige kann für den Benutzer leicht zu Augenmüdigkeit führen. 

**Handverdeckung** 

Helle Farbe erschwert es dem Benutzer, seine Hände zu sehen, wenn er direkt mit Objekten interagiert. Da der Benutzer seine Hände nicht sehen kann, wird es schwierig, die Tiefe/Entfernung zwischen der Hand/dem Finger und der Zieloberfläche zu erkennen. Der Fingercursor hilft dabei, dieses Problem zu kompensieren, aber es kann auf einer hell weißen Oberfläche immer noch eine Herausforderung darstellen. 

![Farbe und Handverdeckung ](images/color_handocclusion.jpg)
 *Schwierig, die Hand auf der farbigen Hintergrundplattform* für Inhalte zu sehen

**Farbgleichheit**

Aufgrund der Merkmale holografischer Displays kann ein großer, heller Bereich auf der Anzeige zu Blotogrammen werden. Mithilfe von dunklen Farbschemas können Sie dieses Problem minimieren. 

## <a name="design-guidelines-for-color-choices"></a>Entwurfsrichtlinien für Farbauswahl

**Verwenden von dunkler Farbe für den Benutzeroberflächenhintergrund**

Mithilfe des dunklen Farbschemas können Sie die Augenmüdigkeit minimieren und die Zuverlässigkeit bei direkten Handinteraktionen verbessern. 

![Beispiele für dunkle Farbe, die für den Inhaltshintergrund verwendet wird ](images/color_dark_examples.jpg)
 *Beispiele für dunkle Farbe, die für den Inhaltshintergrund verwendet wird*

**Verwenden der Schriftbreite "semibold" oder "bold"**

HoloLens ermöglicht es Ihnen, ansprechenden, hochauflösenden Text anzuzeigen. Es wird jedoch empfohlen, schlanke Schriftbreiten wie Hell oder Halblicht zu vermeiden, da die vertikalen Striche in kleinem Schriftgrad jittern können. 

![Die Schriftbreite fett oder halb fett (oberer Bereich) verbessert die Lesbarkeit ](images/color_font_examples.jpg)
 *fett oder halb fett (oberer Bereich) verbessert die Lesbarkeit.*

**Verwenden des HolographicBackplate-Materials von MRTK**

Das HolographicBackplate-Material wird auf mehrere Benutzeroberflächenpanels in der HoloLens Shell angewendet. Eines der Features ist ein irid überfälliger Effekt, der für Benutzer sichtbar ist, wenn sie ihre Position basierend auf dem Panel verschieben. Die Hintergrundfarbe verschiebt sich subtly über ein vordefiniertes Spektrum und erzeugt einen ansprechenden und dynamischen visuellen Effekt, ohne die Lesbarkeit von Inhalten zu beeinträchtigen. Diese geringfügige Farbverschiebung dient auch dazu, geringfügige Farbstörungen zu kompensieren. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>Herausforderungen bei transparenten oder transparenten Benutzeroberflächen-Backplates 

![Beispiele für transparente Ui ](images/color_transparent_examples.jpg)
 *Beispiele für eine transparente Benutzeroberflächen-Backplate*

**Visuelle Komplexität und Barrierefreiheit**

Da holografische Objekte mit der physischen Umgebung kombiniert werden, kann die Lesbarkeit von Inhalten oder Benutzeroberflächen in transparenten oder durchscheinenden Fenstern beeinträchtigt werden. Wenn transparente holografische Objekte übereinander überlagert werden, kann dies die Interaktion des Benutzers aufgrund der verwirrenden Tiefe erschweren.

**Leistung**

Damit transparente oder durchscheinende Objekte ordnungsgemäß gerendert werden können, müssen sie sortiert und mit allen Objekten kombiniert werden, die im Hintergrund vorhanden sind. Das Sortieren von transparenten Objekten hat geringfügige CPU-Kosten, und das Mischen hat erhebliche GPU-Kosten, da die GPU nicht in der Lage ist, ausgeblendete Oberflächen per Z-Culling zu entfernen (d.h. Tiefentests). Wenn das Entfernen ausgeblendeter Oberflächen nicht zugelassen wird, erhöht sich die Anzahl der Vorgänge, die für das endgültige gerenderte Pixel erforderlich sind. Dies führt zu mehr Einschränkungen bei der Füllrate für Druck.

**Hologrammstabilitätsproblem bei der Tiefen-LSR-Technologie**

Um die holografische Neuprojektion oder Hologrammstabilität zu verbessern, kann eine Anwendung für jeden gerenderten Frame einen Tiefenpuffer an das System übermitteln. Wenn Sie den Tiefenpuffer für die Neuprojektion verwenden, müssen Sie einen Tiefenpuffer für jedes farblich gerenderte Pixel mit einer entsprechenden Tiefe schreiben. Jedes Pixel mit einem Tiefenwert sollte ebenfalls einen Farbwert aufweisen. Wenn die obige Anleitung nicht befolgt wird, können Bereiche des gerenderten Bilds, für die keine gültigen Tiefeninformationen vorliegen, auf eine Weise neu projiziert werden, die Artefakte erzeugt, die häufig als wellenähnliche Verzerrung sichtbar sind.


## <a name="design-guidelines-for-transparent-elements"></a>Entwurfsrichtlinien für transparente Elemente

**Verwenden eines nicht transparenten Ui-Hintergrunds**

Standardmäßig schreiben transparente oder durchscheinende Objekte keine Tiefe, um eine ordnungsgemäße Mischung zu ermöglichen. Zu den Möglichkeiten, dieses Problem zu beheben, gehören die Verwendung von nicht transparenten Objekten, die Sicherstellung, dass durchscheinende Objekte in der Nähe von nicht transparenten Objekten erscheinen (z. B. eine durchscheinende Schaltfläche vor einer nicht transparenten Backplate), das Erzwingen der Schreibtiefe durchscheinender Objekte (nicht in allen Szenarien anwendbar) oder das Rendern von Proxyobjekten, die nur tiefenwerte am Ende des Frames beitragen.

Lösungen innerhalb von MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity  

Mithilfe einer soliden und nicht transparenten Backplate können wir die Lesbarkeit und Interaktionssicherheit sichern.

**Minimieren der Anzahl der betroffenen Pixel**

Wenn ihr Projekt transparente Objekte verwenden muss, versuchen Sie, die Anzahl der betroffenen Pixel zu minimieren. Wenn ein Objekt beispielsweise nur unter bestimmten Bedingungen (z. B. einem additiven Leuchteffekt) sichtbar ist, deaktivieren Sie das Objekt, wenn es vollständig unsichtbar ist (anstatt die additive Farbe auf Schwarz festzulegen). Für einfache 2D-Formen, die mit einem Quader mit einer Alphamaske erstellt wurden, sollten Sie stattdessen eine Gitternetzdarstellung der Form mit einem deckenden Shader erstellen. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Beispiele für dunkle Ui im MRTK (Mixed Reality Toolkit) für Unity

**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** bietet viele Beispiele für Ui-Bausteine, die auf den dunklen Farbschemas basieren.

* [Menü "In der Nähe"](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [Dialogfeld](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [Handmenü](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a>Siehe auch

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