---
title: Entwerfen von Inhalten für die holografische Anzeige
description: Erfahren Sie mehr über Entwurfsrichtlinien und bewährte Methoden für die holografische Anzeige auf HoloLens-Geräten.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI-Design, holografische Anzeige, Inhaltsdesign, dunkles Design, helles Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Design, Pixel
ms.openlocfilehash: 2c68acb5478bfbd438c8bbb9dd2f8d9686bcefc5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600319"
---
# <a name="designing-content-for-holographic-display"></a>Entwerfen von Inhalten für die holografische Anzeige

![Ulnar-Seitenposition](images/UX_Hero_DarkTheme.jpg)

Beim Entwerfen von Inhalten für holografische Displays gibt es mehrere Elemente, die Sie berücksichtigen müssen, um die beste Erfahrung zu erzielen. Wir haben einige unserer Empfehlungen unten aufgelistet, und Sie können mehr über die Merkmale von holografischen Displays auf der Seite [Farbe, Licht und Materialien](color-light-and-materials.md) erfahren.

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>Herausforderungen mit hellem Farbton auf einer großen Oberfläche 

Basierend auf unseren HoloLens-Erfahrungsforschungen und -Tests haben wir festgestellt, dass die Verwendung von hellen Farben in einem großen Bereich der Anzeige mehrere Probleme verursachen kann: 

**Augenermüdung** 

Da die holografische Anzeige additiv ist, verwenden Hologramme mit hellen Farben mehr Licht. Helle, volltonige Farbe in einem großen Bereich der Anzeige kann für den Benutzer leicht zu Sehmüdigkeit führen. 

**Handverdecken** 

Helle Farben erschweren es dem Benutzer, seine Hände zu sehen, wenn er direkt mit Objekten interagiert. Da der Benutzer seine Hände nicht sehen kann, wird es schwierig, die Tiefe/Entfernung zwischen der Hand/dem Finger und der Zieloberfläche zu erkennen. Der Fingercursor hilft dabei, dieses Problem zu kompensieren, kann aber auf einer weißen Oberfläche immer noch eine Herausforderung darstellen. 

![Farbe und Handver occlusion Schwierig, die Hand auf der farbigen ](images/color_handocclusion.jpg)
 *Inhalts-Hintergrundbaustein zu sehen*

**Farbeinheitlichkeit**

Aufgrund der Merkmale von holografischen Displays kann ein großer, heller Bereich auf der Anzeige zu Blotogramm werden. Mithilfe von dunklen Farbschemas können Sie dieses Problem minimieren. 

## <a name="design-guidelines-for-color-choices"></a>Entwurfsrichtlinien für Farboptionen

**Verwenden der dunklen Farbe für den Ui-Hintergrund**

Mithilfe des dunklen Farbschemas können Sie die Augenmüdigkeit minimieren und die Konfidenz bei direkten Handinteraktionen verbessern. 

![Beispiele für dunkle Farbe, die für den Inhaltshintergrund verwendet wird Beispiele für dunkle ](images/color_dark_examples.jpg)
 *Farbe, die für den Inhaltshintergrund verwendet wird*

**Verwenden der Schriftgewichtung "semibold" oder "bold"**

HoloLens ermöglicht es Ihrer Erfahrung, hochwertigen, hochauflösenden Text zu zeigen. Es wird jedoch empfohlen, schlanke Schriftgewichtungen wie hell oder halb hell zu vermeiden, da die vertikalen Striche in kleinem Schriftgrad jittern können. 

![Fett oder halb fett formatiert (oberer Bereich) verbessert die Lesbarkeit Fett oder halb fett ](images/color_font_examples.jpg)
 *Schriftgrad (oberer Bereich) verbessert die Lesbarkeit.*

**Verwenden des HolographicBackplate-Materials des MRTK**

Das HolographicBackplate-Material wird auf mehrere Benutzeroberflächenpanels in der HoloLens-Shell angewendet. Eines der Features ist ein irideneffekt, der für Benutzer sichtbar ist, wenn sie ihre Position basierend auf dem Panel verschieben. Die Hintergrundfarbe verschiebt sich subtly über ein vordefiniertes Spektrum, wodurch ein ansprechender und dynamischer visueller Effekt ohne Beeinträchtigung der Lesbarkeit von Inhalten erstellt wird. Diese geringfügige Farbverschiebung dient auch dazu, kleinere Farbverschädigte zu kompensieren. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>Herausforderungen bei transparenten oder transparenten UI-Hintergrundbausteinen 

![Beispiele für transparente ](images/color_transparent_examples.jpg)
 *BenutzeroberflächenBeispiele für eine transparente Ui-Backplate*

**Visuelle Komplexität und Barrierefreiheit**

Da holografische Objekte mit der physischen Umgebung kombiniert werden, kann der Inhalt oder die Lesbarkeit der Benutzeroberfläche in transparenten oder transparenten Fenstern beeinträchtigt werden. Wenn transparente holografische Objekte übereinander überlagert werden, kann dies außerdem die Interaktion des Benutzers aufgrund der verwirrenden Tiefe erschweren.

**Leistung**

Damit transparente oder transparente Objekte ordnungsgemäß gerendert werden können, müssen sie sortiert und mit allen Objekten kombiniert werden, die im Hintergrund vorhanden sind. Das Sortieren von transparenten Objekten hat geringfügige CPU-Kosten, und das Mischen hat erhebliche GPU-Kosten, da die GPU die Entfernung verborgener Oberflächen nicht über Z-Culling (d. h. Tiefentests). Wenn das Entfernen ausgeblendeter Oberflächen nicht erlaubt wird, erhöht sich die Anzahl der Vorgänge, die für das endgültige gerenderte Pixel erforderlich sind. Dies führt zu einer stärkeren Einschränkung der Druckfüllrate.

**Hologrammstabilitätsproblem mit Tiefen-LSR-Technologie**

Um die holografische Neuprojektion oder Hologrammstabilität zu verbessern, kann eine Anwendung für jeden gerenderten Frame einen Tiefenpuffer an das System übermitteln. Wenn Sie den Tiefenpuffer für die Neuprojektion verwenden, müssen Sie einen Tiefenpuffer für jedes gerenderte Farbpixel in einer entsprechenden Tiefe schreiben. Jedes Pixel mit einem Tiefenwert sollte auch einen Farbwert haben. Wenn die obige Anleitung nicht befolgt wird, können Bereiche des gerenderten Bilds, die keine gültigen Tiefeninformationen enthalten, auf eine Weise neu projiziert werden, die Artefakte erzeugt, die häufig als wellenbasierte Verzerrung sichtbar sind.


## <a name="design-guidelines-for-transparent-elements"></a>Entwurfsrichtlinien für transparente Elemente

**Verwenden des Hintergrunds der nicht transparenten Benutzeroberfläche**

Standardmäßig schreiben transparente oder durchsichtige Objekte keine Tiefe, um eine ordnungsgemäße Mischung zu ermöglichen. Zu den Möglichkeiten, dieses Problem zu beheben, gehören die Verwendung von nicht transparenten Objekten, das Sicherstellen, dass durchsichtige Objekte in der Nähe von nicht transparenten Objekten angezeigt werden (z. B. eine durchscheinende Schaltfläche vor einer nicht transparenten Hintergrundbaustein), das Erzwingen der Schreibtiefe durchscheinender Objekte (nicht in allen Szenarien anwendbar) oder das Rendern von Proxyobjekten, die nur tiefen Werte am Ende des Rahmens beitragen.

Lösungen in MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity  

Durch die Verwendung einer soliden und nicht transparenten Backplate können wir Lesbarkeit und Interaktionsvertrauen sichern.

**Minimieren der Anzahl der betroffenen Pixel**

Wenn Ihr Projekt transparente Objekte verwenden muss, versuchen Sie, die Anzahl der betroffenen Pixel zu minimieren. Wenn ein Objekt beispielsweise nur unter bestimmten Bedingungen (z. B. einem additiven Leuchteffekt) sichtbar ist, deaktivieren Sie das Objekt, wenn es vollständig unsichtbar ist (anstatt die additive Farbe auf Schwarz zu setzen). Für einfache 2D-Formen, die mit einem Quad mit einer Alphamaske erstellt werden, sollten Sie stattdessen eine Gitternetzdarstellung der Form mit einem nicht transparenten Shader erstellen. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Beispiele für dunkle Benutzeroberflächen im MRTK (Mixed Reality Toolkit) für Unity

**[MRTK bietet](https://github.com/Microsoft/MixedRealityToolkit-Unity)** viele Beispiele für Benutzeroberflächenbausteinen, die auf den dunklen Farbschemas basieren.

* [Menü "Nah"](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
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