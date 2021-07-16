---
title: Was ist Mixed Reality?
description: Diskussion über Mixed Reality, wobei die Verwendung von AR- und VR-Geräten im Mixed Reality-Spektrum demonstriert wird.
author: qianw211
ms.author: v-qianwen
ms.date: 07/01/2021
ms.topic: article
keywords: Mixed Reality, holographic, AR, VR, MR, XR, Augmented Reality, Virtual Reality, Erläuterung, Fallstudie, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, was ist Virtual Reality, was ist Augmented Reality
ms.localizationpriority: high
ms.openlocfilehash: 088bc9a978bd236069ddc1beab40387c607b906e
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634321"
---
# <a name="what-is-mixed-reality"></a>Was ist Mixed Reality?

Mixed Reality ist der nächste Entwicklungsschritt des Computings, gefolgt von Mainframes, PCs und Smartphones. Mixed Reality wird für Consumer und Unternehmen zum Mainstream.  Es befreit uns von bildschirmgebundenen Erfahrungen, indem es instinktive Interaktionen mit Daten in unseren Lebensräumen, mit unseren Dingen und mit unseren Freunden ermöglicht.  Hunderte von Millionen Online-Entdecker auf der ganzen Welt haben Mixed Reality über ihre Handheld-Geräte erlebt.  Mobile AR bietet derzeit die massentauglichsten Mixed Reality-Lösungen in den sozialen Medien. Die Benutzer merken möglicherweise nicht einmal, dass die AR-Filter, die sie auf Instagram verwenden, Mixed Reality-Erfahrungen sind.  Microsoft Mixed Reality soll all diese Benutzererfahrungen auf die nächste Stufe heben – mit einer Kombination aus wirklich atemberaubenden holografischen Darstellungen von Menschen, holografischen High-Fidelity-3D-Modellen und der realen Welt, die sie umgibt.

![Zeigen und Bestätigen mit den Händen auf HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

Mixed Reality ist eine Mischung aus physischer und digitaler Welt, die die natürliche und intuitive 3D-Interaktion zwischen Menschen, Computern und Umgebung freisetzt. Diese neue Realität wird durch Fortschritte beim maschinellen Sehen, der Grafikverarbeitung, den Anzeigetechnologien, Eingabesystemen und dem Cloud Computing ermöglicht. Der Begriff Mixed Reality wurde 1994 in einer Arbeit von Paul Milgram und Fumio Kishino eingeführt, „[A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)“. In ihrem Artikel wurde das Konzept eines *Virtualitätskontinuums* untersucht und die Taxonomie visueller Displays behandelt. Seitdem hat sich die Anwendung von Mixed Reality über Displays hinaus entwickelt und beinhaltet nun:

* Umgebungsverständnis: räumliche Abbildung und Raumanker.
* Menschliches Verstehen: Handtracking, Eyetracking und Spracheingabe.
* Raumklang.
* Orte und Positionierung in physischen wie in virtuellen Räumen.
* Zusammenarbeit an 3D-Ressourcen in Mixed Reality-Bereichen.

![Abbildung des Mixed Reality-Spektrums](images/mixedrealityspectrum-worlds.png)<br>
*Abbildung: Mixed Reality ist das Ergebnis der Verschmelzung der physischen Welt mit der digitalen Welt.*

<br>

---

## <a name="environmental-input-and-perception"></a>Umgebungseinfluss und Wahrnehmung

In den vergangenen Jahrzehnten hat sich die Beziehung zwischen Mensch und Computer durch die Eingabemethoden immer weiter entwickelt.  Eine neue Disziplin hat sich entwickelt, die als Mensch-Computer-Interaktion oder HCI (Human Computer Interaction) bezeichnet wird. Menschliche Eingaben können nun Tastaturen, Mäuse, Berührung, Freihand, Sprache und Skelettnachverfolgung (Kinect) umfassen.

Fortschritte bei Sensoren und Verarbeitungsleistung erzeugen neue Computerwahrnehmungen von Umgebungen, basierend auf erweiterten Eingabemethoden. Daher werden die Namen von APIs in Windows, die Umgebungsinformationen offenlegen, als [Wahrnehmungs-APIs](/uwp/api/Windows.Perception) bezeichnet. Umgebungseingaben können Folgendes erfassen: 

* Die Körperposition einer Person in der physischen Welt ([Kopf-Tracking (Nachverfolgung)](../design/coordinate-systems.md)) 
* Objekte, Oberflächen und Grenzen ([räumliche Abbildung](../design/spatial-mapping.md) und [Szenenverständnis](../design/scene-understanding.md)) 
* Umgebungslicht und -geräusche
* Objekterkennung
* Physische Orte

<br>

![Venn-Diagramm, das Interaktionen zwischen Computern, Menschen und Umgebungen anzeigt](images/mixed-reality-venn-diagram-300px.png)<br> 
*Abbildung: Die Interaktionen zwischen Computern, Menschen und Umgebungen.*

<br>

Die Kombination der drei wesentlichen Elemente bildet die Grundlage für die Schaffung echter Mixed Reality-Erfahrungen:

* Von der Cloud unterstützte Computerverarbeitung
* Erweiterte Eingabemethoden
* Wahrnehmung der Umgebung

Während wir uns durch die physische Welt bewegen, werden unsere Bewegungen in einer digitalen Realität abgebildet. Physische Grenzen beeinflussen Mixed Reality-Erfahrungen in der digitalen Welt wie Spiele oder aufgabenbasierte Anleitungen in einer Produktionsanlage. Mit Umgebungseingaben und -wahrnehmungen beginnen Erfahrungen physische und digitale Realitäten zu vermischen.

<br>

---

## <a name="the-mixed-reality-spectrum"></a>Das Spektrum von Mixed Reality

Mixed Reality vermischt sowohl physische als auch digitale Welten.  Diese beiden Realitäten markieren die Pole eines Spektrums, das als *Virtualitätskontinuum* bezeichnet wird. Wir bezeichnen dieses Spektrum von Realitäten als *Mixed Reality-Spektrum*.  Am einen Ende des Spektrums liegt die physische Realität, in der wir als Menschen leben. Am anderen Ende des Spektrums befindet sich die entsprechende digitale Realität.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Augmented Reality im Vergleich mit Virtual Reality

Die meisten aktuell auf dem Markt verfügbaren Mobiltelefone haben kaum oder keine Fähigkeiten zur Wahrnehmung der Umgebung. Die von diesen Telefonen angebotenen Erfahrungen können keine Mischung aus physischer und digitaler Realität anbieten. 

Die Benutzererfahrungen, bei denen Grafiken, Videostreams oder Hologramme in der realen Welt überlagert werden, werden als „Augmented Reality“ bezeichnet. Die Benutzererfahrungen, die Ihre Sicht verdecken, um ein vollständig immersives, digitales Erlebnis darzustellen, sind virtuelle Realität („Virtual Reality“). Die Erfahrungen, die Übergänge zwischen Augmented Reality und virtueller Realität ermöglichen können, bilden die „Mixed Reality“, in der Sie folgende Möglichkeiten haben:

* Platzieren eines digitalen Objekts, z. B. eines Hologramms, in der physischen Welt, als ob es physisch vorhanden wäre.
* Persönliche und digitale Anwesenheit des Benutzers in der physischen Welt in Form eines Avatars, um asynchron mit anderen zu unterschiedlichen Zeitpunkten zusammenzuarbeiten.
* In der virtuellen Realität werden physische Grenzen wie Wände und Möbel digital innerhalb der Erfahrung angezeigt, damit Benutzer nicht gegen physische Hindernisse stoßen.

<br>

![Das Spektrum von Mixed Reality](images/mixedrealityspectrum.png)<br>
*Abbildung: Das Spektrum von Mixed Reality*

<br>

Die meisten heute verfügbaren Erfahrungen für Augmented Reality und virtuelle Realität stellen nur eine kleinen Teil des größeren Mixed Reality-Spektrums dar. Windows 10 wurde im Hinblick auf das gesamte Spektrum konzipiert und ermöglicht das Mischen digitaler Darstellungen von Personen, Orten und Gegenständen mit der realen Welt.

## <a name="devices-and-experiences"></a>Geräte und Erlebnisse

Es gibt zwei Hauptarten von Geräten, die Windows Mixed Reality-Erlebnisse bieten:
1. **Holografische Geräte** zeichnen sich durch die Fähigkeit aus, digitale Inhalte so in der realen Welt zu platzieren, als wären sie vorhanden.
2. **Immersive VR-Geräte** zeichnen sich durch deren Fähigkeit aus, einen Eindruck von „Gegenwart“ zu erzeugen, indem die physische Welt komplett ausgeblendet und durch ein vollständig immersives, digitales Erlebnis ersetzt wird.

<table>
<tr>
<th width="30%"> Merkmal</th><th width="35%"> Holografische -Geräte</th><th width="35%"> Immersive Geräte</th>
</tr><tr>
<td><strong>Beispielgerät</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Anzeige</strong></td><td> Transparente Anzeige. Ermöglicht dem Benutzer, die physische Umgebung zu sehen, während er das Headset trägt.</td><td> Opake Anzeige. Sperrt die physische Umgebung während des Tragens des Headsets aus.</td>
</tr><tr>
<td><strong>Movement</strong></td><td> Volle sechs Freiheitsgrade für Bewegung, sowohl Drehung als auch Verschiebung.</td><td> Volle sechs Freiheitsgrade für Bewegung, sowohl Drehung als auch Verschiebung.</td>
</tr>
</table> 

> [!NOTE]
> Ob ein Gerät (per USB-Kabel oder WLAN) mit einem separaten PC verbunden oder nicht verbunden ist, sagt nichts darüber aus, ob das Gerät holografisch oder immersiv ist. Features, die die Mobilität verbessern, bieten häufig bessere Erfahrungen. Holografische und immersive Geräte können entweder verbunden oder nicht verbunden sein.

Mixed Reality-Erfahrungen sind das Ergebnis technologischer Fortschritte. Heutzutage gibt es keine Geräte, die das gesamte Spektrum der Erfahrungen ausführen können. Windows 10 bietet eine gemeinsame Mixed Reality-Plattform für Gerätehersteller und Entwickler. Heutzutage kann jedes Geräte einen bestimmten Bereich innerhalb des Mixed Reality-Spektrums unterstützen. In Zukunft sind neue Geräte mit umfangreicheren Bereichen zu erwarten: holografische Geräte werden stärker immersiv und immersive Geräte werden stärker holografisch.

<br>

![Gerätetypen im Mixed Reality-Spektrum](images/Final_WhatIsMixedReality07.png)<br>
*Abbildung: Der Platz von Geräten im Mixed Reality-Spektrum*

Welche Art von Erfahrungen möchten Sie als Anwendungs- oder Spieleentwickler erstellen? Die Erfahrungen zielen normalerweise auf einen bestimmten Punkt oder Teil des Spektrums ab. Sie müssen die Funktionen von Geräten berücksichtigen, für die Sie entwickeln möchten. Erfahrungen, die auf der physischen Welt basieren, lassen sich optimal in HoloLens ausführen.

* **Mehr links (nahe an der physischen Realität).** Benutzer verbleiben in ihrer physischen Realität, und ihnen wird nicht vermittelt, sie hätten diese Realität verlassen.
* **In der Mitte (vollständige Mixed Reality).** Diese Benutzererfahrungen bestehen aus einer Mischung aus realer Welt und digitaler Welt. Beispielsweise wurde im Film [Jumanji](https://en.wikipedia.org/wiki/Jumanji) die physische Struktur des Hauses, in dem die Geschichte spielt, mit einer Dschungelumgebung gemischt.
* **Mehr rechts (nahe an der digitalen Realität).** Benutzer erleben eine digitale Realität und sind sich der sie umgebenden physischen Realität nicht mehr bewusst.

## <a name="next-discovery-checkpoint"></a>Nächster Erkundungsprüfpunkt

Sie befinden sich am Anfang der [Erkundungs-Journey](get-started-with-mr.md), die wir für Sie entworfen haben, und erkunden gerade die Grundlagen der Mixed Reality. Von hier aus können Sie mit dem nächsten grundlegenden Thema fortfahren: 

> [!div class="nextstepaction"]
> [Was ist ein Hologramm?](hologram.md)
