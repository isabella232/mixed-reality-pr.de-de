---
title: Fallstudie – Schauen durch Löcher in Ihrer Realität
description: In dieser Fallstudie wird die Effektimplementierung des "magischen Fensters" auf HoloLens erläutert, sodass der Benutzer hinter Wänden, unter dem Boden und in virtuellen Öffnungen sehen kann.
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, Magic-Fenster, Paralyx
ms.openlocfilehash: 0769d8a7bd2b5bdf1ef1fe50f1bbcd2f284b8503bf66b8fdb09b2206b716ea65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228182"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Fallstudie – Schauen durch Löcher in Ihrer Realität

Wenn Menschen über Mixed Reality nachdenken und was sie mit Microsoft HoloLens können, bleiben sie in der Regel bei Fragen wie "Welche Objekte kann ich meinem Raum hinzufügen?" oder "What can I layer on my space?" Ich möchte einen anderen Bereich hervorheben, den Sie in Betracht ziehen können – im Wesentlichen ein magischer Trick – indem Sie dieselbe Technologie verwenden, um echte physische Objekte um Sie herum zu betrachten oder zu durch sie zu schauen.

## <a name="the-tech"></a>Die Technologie

Wenn Sie beim Durchbrechen Ihrer Wände in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** Bzw. beim Entsperren einer Wandsicherer in **[Fragmenten](case-study-creating-an-immersive-experience-in-fragments.md)** oder beim Sehen des UNSC Infinity-Hangars in der Halo 5-Erfahrung bei E3 im Jahr **[2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)** umgekämpft haben, haben Sie gesehen, worüber ich spricht. Je nach Ihrer Vorstellung kann dieser visuelle Trick verwendet werden, um temporäre Lücken in Ihrer Lücke zu setzen oder Welten unter einem losen Bodenbrett auszublenden.

![RoboRaid fügt dreidimensionale Pipes und andere Strukturen hinter Ihren Wänden hinzu, die nur durch Lücken sichtbar sind, die beim Durchbrechen der Schützer erstellt werden.](../develop/unity/images/roboraid-640px.png)

RoboRaid fügt dreidimensionale Pipes und andere Strukturen hinter Ihren Wänden hinzu, die nur durch Lücken sichtbar sind, die beim Durchbrechen der Schützer erstellt werden.

Mithilfe eines dieser einzigartigen Hologramme auf HoloLens kann eine App die Anzappung von Inhalten hinter Ihren Wänden oder durch Ihren Boden auf die gleiche Weise bereitstellen, wie sich die Realität über ein tatsächliches Fenster präsentiert. Bewegen Sie sich nach links, und Sie können sehen, was sich auf der rechten Seite befindet. Kommen Sie näher, und Sie können ein wenig mehr von allem sehen. Der Hauptunterschied besteht in den echten Lücken, die Sie durch den Boden bewegen können, während Sie sich nicht durch diese magischen holografischen Inhalte bewegen können. (Ich füge dem Backlog eine Aufgabe hinzu.)

## <a name="behind-the-scenes"></a>Abläufe im Hintergrund

Dieser Trick ist eine Kombination aus zwei Effekten. Erstens wird holografischer Inhalt mithilfe von "Raumankern" an die Welt angeheftet. Die Verwendung von Ankern, um diesen Inhalt "weltgesperrt" zu machen, bedeutet, dass sich das, was Sie sich annähern, nicht visuell von den physischen Objekten entfernt, die sich in der Nähe des Inhalts bewegen, selbst wenn Sie sich bewegen oder das zugrunde liegende Raumzuordnungssystem sein 3D-Modell Ihres Raums aktualisiert.

Zweitens ist dieser holografische Inhalt visuell auf einen sehr bestimmten Raum beschränkt, sodass Sie nur durch die Lücke in Ihrer Realität sehen können. Diese Okklusion ist erforderlich, um das Durchsuchen einer logischen Lücke, eines Fensters oder einer Tür zu erfordern, die den Trick verkauft. Ohne etwas, das die meiste Ansicht blockiert, könnte ein Riss im Raum in einer geheimen Dimensionstabelle einfach wie ein schlecht platzierter Uri aussehen.

![Dies ist kein tatsächlicher Screenshot, sondern eine Abbildung der Geheimnis-Unterwelt aus MR Basics 101 auf HoloLens. Das schwarze Gehäuse wird nicht gezeigt, aber Sie können Inhalte über eine virtuelle Lücke sehen. (Wenn Sie ein tatsächliches Gerät durchs augesen, scheint der Boden noch mehr zu verschwinden, da sich Ihre Augen in weiterer Entfernung so konzentrieren, als wäre er nicht einmal dort.)](images/origamiholecomposited-640px.png)

Dies ist kein tatsächlicher Screenshot, sondern eine Abbildung der Geheimnis-Unterwelt aus [mr Basics 101](../develop/unity/tutorials/holograms-101.md) auf HoloLens. Das schwarze Gehäuse wird nicht gezeigt, aber Sie können Inhalte über eine virtuelle Lücke sehen. (Wenn Sie ein tatsächliches Gerät durchs augesen, scheint der Boden noch mehr zu verschwinden, da sich Ihre Augen in weiterer Entfernung so konzentrieren, als wäre er nicht einmal dort.)

### <a name="world-locking-holographic-content"></a>Weltverriegelung von holografischem Inhalt

In Unity ist das Hinzufügen einer WorldAnchor-Komponente so einfach, dass holografische Inhalte weltweit gesperrt bleiben:

```
myObject.AddComponent<WorldAnchor>();
```

Die WorldAnchor-Komponente passt ständig die Position und Drehung ihres GameObject (und somit aller anderen Objekte unter diesem Objekt in der Hierarchie) an, um sie relativ zu nahe gelegenen physischen Objekten stabil zu halten. Wenn Sie Ihren Inhalt erstellen, erstellen Sie ihn so, dass der Stammpivot Ihres Objekts auf dieser virtuellen Lücke zentriert ist. (Wenn sich der Pivot ihres Objekts tief in der Wand befindet, sind seine geringfügigen Anpassungen an Position und Drehung deutlich deutlicher, und die Lücke sieht möglicherweise nicht sehr stabil aus.)

### <a name="occluding-everything-but-the-virtual-hole"></a>Umschließen von allem bis auf die virtuelle Lücke

Es gibt eine Vielzahl von Möglichkeiten, die Ansicht selektiv auf das zu blockieren, was in Ihren Wänden verborgen ist. Die einfachste nutzt die Tatsache, dass HoloLens additive Anzeige verwendet, was bedeutet, dass vollständig schwarze Objekte unsichtbar erscheinen. Sie können dies in Unity tun, ohne spezielle Shader- oder Materialtricks zu machen. Erstellen Sie einfach ein schwarzes Material, und weisen Sie es einem Objekt zu, das in Ihrem Inhalt feldert. Wenn Sie keine 3D-Modellierung verwenden möchten, verwenden Sie einfach eine Handvoll Standard-Quad-Objekte, und überlappen Sie sie leicht. Es gibt eine Reihe von Nachteilen dieses Ansatzes, aber es ist die schnellste Möglichkeit, etwas zu funktionieren, und ein Proof of Concept mit geringer Genauigkeit funktioniert sehr gut, auch wenn Sie vermuten, dass Sie ihn später umgestalten möchten.

Ein großer Nachteil des oben genannten "Blackbox"-Ansatzes ist, dass er nicht gut fotost. Während Ihr Effekt durch die Anzeige von HoloLens perfekt aussehen kann, zeigen alle Screenshots, die Sie erstellen, ein großes schwarzes Objekt anstelle der Reste Ihrer Wand oder Ihres Bodens. Der Grund dafür ist, dass die physische Hardware und die Screenshots zusammengesetzter Hologramme und Realität unterschiedlich sind. Lassen Sie uns einen Blick auf eine falsche Mathematik werfen...

*Falsche mathematische Warnung! Diese Zahlen und Formeln sollen einen Punkt veranschaulichen und keine genaue Metrik sein!*

Was Sie durch die HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

Dies wird in Screenshots und Videos angezeigt:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

Auf Englisch: Das, was Sie über HoloLens sehen, ist eine einfache Kombination aus dunkler Realität (z. B. durch Sonnenbrillen) und den Hologrammen, die die App anzeigen möchte. Wenn Sie jedoch einen Screenshot erstellen, wird das Bild der Kamera mit den Hologrammen der App gemäß dem Transparenzwert pro Pixel kombiniert.

Eine Möglichkeit, dies zu ändern, besteht in der Änderung des Blackbox-Materials, um nur in den Tiefenpuffer zu schreiben und mit allen anderen nicht transparenten Materialien zu sortieren. Ein Beispiel hierfür finden Sie in der [Datei WindowOcclusion.shader im MixedRealityToolkit auf GitHub.](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader) Die relevanten Zeilen werden hier kopiert:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(Beachten Sie, dass die Zeile "Offset 50, 100" für den Umgang mit nicht verbundenen Problemen steht, daher wäre es wahrscheinlich sinnvoll, dies weg zu lassen.)

Wenn Sie ein unsichtbares Okklusionsmaterial wie das implementieren, kann Ihre App ein Feld zeichnen, das in der Anzeige und in Mixed Reality-Screenshots korrekt aussieht. Für Bonuspunkte können Sie versuchen, die Leistung dieses Felds noch weiter zu verbessern, indem Sie clevere Dinge tun, um noch weniger unsichtbare Pixel zu zeichnen, aber dies kann tatsächlich in die Undaten kommen und ist in der Regel nicht erforderlich.

![Hier ist die Geheimnis-Unterwelt aus MR Basics 101, während Unity sie zeichnet, mit Ausnahme der äußeren Teile des umschließenden Felds. Beachten Sie, dass sich das Pivot für die Unterwelt in der Mitte des Felds befindet, wodurch die Lücke relativ zum tatsächlichen Boden so stabil wie möglich bleibt.](images/underworld-occluded-640px.png)

Hier ist die Geheimnis-Unterwelt aus [MR Basics 101,](../develop/unity/tutorials/holograms-101.md) während Unity sie zeichnet, mit Ausnahme der äußeren Teile des umschließenden Felds. Beachten Sie, dass sich das Pivot für die Unterwelt in der Mitte des Felds befindet, wodurch die Lücke relativ zum tatsächlichen Boden so stabil wie möglich bleibt.

## <a name="do-it-yourself"></a>Aufzeichnung in Eigenregie

Haben Sie HoloLens und möchten Sie den Effekt selbst ausprobieren? Am einfachsten (ohne Programmieraufwand) können Sie die kostenlose 3D-Viewer-App installieren und dann die [fbx-Datei laden,](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) die ich in GitHub bereitgestellt habe, um ein Blumenmodell in Ihrem Raum zu sehen. Laden Sie es auf HoloLens, und Sie können die Illusion bei der Arbeit sehen. Wenn Sie sich vor dem Modell befindet, können Sie nur in die kleine Lücke sehen– alles andere ist unsichtbar. Sehen Sie sich das Modell von jeder anderen Seite an, und es verschwindet vollständig. Verwenden Sie die Bewegungs-, Dreh- und Skalierungssteuerelemente von 3D-Viewer, um die virtuellen Lücke auf jeder vertikalen Oberfläche zu positionieren, an die Sie sich denken können, um Ideen zu generieren!

![Wenn Sie dieses Modell in Ihrem Unity-Editor anzeigen, wird eine große Blackbox um den Flowerpot angezeigt. Auf HoloLens wird das Feld nicht mehr angezeigt, was einem magischen Fenstereffekt den Weg gibt.](images/magicwindowflowerpotineditor.png)

Wenn Sie dieses Modell in Ihrem Unity-Editor anzeigen, wird eine große Blackbox um den Flowerpot angezeigt. Auf HoloLens wird das Feld nicht mehr angezeigt, was einem magischen Fenstereffekt den Weg gibt.

Wenn Sie eine App erstellen möchten, die diese Technik verwendet, lesen Sie das [Tutorial MR Basics 101 (MR-Grundlagen 101)](../develop/unity/tutorials/holograms-101.md) in den Mixed Reality [Tutorials.](../develop/unity/tutorials.md) Kapitel 7 endet mit einer Explosion in Ihrem Boden, die eine verborgene Unterwelt (wie oben abgebildet) zeigt. Wer, dass Tutorials sehr behend sein mussten?

Im Folgenden finden Sie einige Ideen, wie Sie diese Idee als Nächstes umsetzen können:
* Stellen Sie sich Möglichkeiten vor, den Inhalt innerhalb der virtuellen Lücke interaktiv zu gestalten. Wenn Sie es Ihren Benutzern ermöglichen, auswirkungen auf ihre Grenzen zu haben, kann dies das Gefühl der Verkniffung verbessern, die dieser Trick bieten kann.
* Stellen Sie sich Möglichkeiten vor, objekte wieder in bekannte Bereiche zu sehen. Wie können Sie z. B. ein holografisches Lücke in Ihre Kaffeetabelle setzen und Ihren Boden darunter sehen?

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehierer</b><br>Leitender Softwaretechniker @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [MR-Grundlagen 101: Vollständiges Projekt mit Gerät](../develop/unity/tutorials/holograms-101.md)
* [Koordinatensysteme](../design/coordinate-systems.md)
* [Raumanker](../design/spatial-anchors.md)
* [Räumliche Abbildung](../design/spatial-mapping.md)
