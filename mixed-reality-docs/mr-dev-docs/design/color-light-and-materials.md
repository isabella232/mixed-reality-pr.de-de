---
title: Farbe, Licht und Materialien
description: Das Entwerfen von Inhalten für Mixed Reality erfordert eine sorgfältige Berücksichtigung von Farbe, Beleuchtung und Materialien für alle visuellen Objekte.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Farbe, Licht, Materialien, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 2e1626e72d49107c2a83bf1123b306d3ee5c8640
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600359"
---
# <a name="color-light-and-materials"></a>Farbe, Licht und Materialien

![Farbe, Licht und Materialien](images/RemoteRendering.jpg)

Das Entwerfen von Inhalten für Mixed Reality erfordert eine sorgfältige Überlegung von Farbe, Beleuchtung und Materialien für alle Ihre virtuellen Ressourcen. Zu den Beweggründen kann die Verwendung von Licht und Material gehören, um den Ton einer immersiven Umgebung zu setzen, während funktionale Zwecke die Verwendung von Farben umfassen können, um Benutzer vor einer bevorstehenden Aktion zu warnen. Jede dieser Entscheidungen muss gegen die Möglichkeiten und Einschränkungen des Zielgeräts Ihrer Benutzererfahrung abgewogen werden.

Im Folgenden finden Sie Richtlinien für das Rendern von Medienressourcen auf immersiven und holografischen Headsets. Viele davon sind eng mit anderen technischen Bereichen verknüpft, und [](color-light-and-materials.md#see-also) eine Liste verwandter Themen finden Sie im Abschnitt Siehe auch am Ende dieses Artikels.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Rendering auf immersiven und holografischen Geräten

Inhalte, die in immersiven Headsets gerendert werden, werden visuell anders angezeigt als Inhalte, die in holografischen Headsets gerendert werden. Immersive Headsets rendern inhalte zwar in der Regel so, wie Sie es auf einem 2D-Bildschirm erwarten würden, holografische Headsets wie HoloLens verwenden farbkonsquentielle RGB-Anzeigen, um Hologramme zu rendern.

Nehmen Sie sich immer Zeit, ihre holografischen Erfahrungen in einem holografischen Headset zu testen. Die Darstellung des Inhalts, selbst wenn er speziell für holografische Geräte erstellt wurde, unterscheidet sich, wie auf sekundären Monitoren, Momentaufnahmen und in der ansichtsbeobachten Ansicht zu sehen. Denken Sie daran, erfahrungen mit einem Gerät zu gehen, die Beleuchtung von Hologrammen zu testen und von allen Seiten (sowie von oben und unten) zu beobachten, wie Ihre Inhalte gerendert werden. Testen Sie unbedingt mit einer Reihe von Helligkeitseinstellungen auf dem Gerät. Es ist unwahrscheinlich, dass alle Benutzer eine angenommene Standardeinstellung und eine Vielzahl von Beleuchtungsbedingungen gemeinsam verwenden.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Grundlagen des Renderings auf holografischen Geräten

* **Holografische Geräte verfügen über additive** Displays– Hologramme werden durch Hinzufügen von Licht aus der realen Welt zum Licht erstellt– Weiß wird hell und Schwarz transparent angezeigt.

* **Die Auswirkung der Farben variiert je nach** Umgebung des Benutzers: Es gibt viele verschiedene Beleuchtungsbedingungen im Raum eines Benutzers. Erstellen Sie Inhalte mit geeigneten Kontrastebenen, um die Übersichtlichkeit zu verbessern.

* **Vermeiden dynamischer Beleuchtung:** Hologramme, die in holografischen Erfahrungen einheitlich beleuchtet sind, sind am effizientesten. Die Verwendung der erweiterten, dynamischen Beleuchtung wird wahrscheinlich die Funktionen mobiler Geräte überschreiten. Wenn dynamische Beleuchtung erforderlich ist, wird empfohlen, den [Mixed Reality Toolkit Standard-Shader zu verwenden.](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) 

## <a name="designing-with-color"></a>Entwerfen mit Farbe

Aufgrund der Art von additiven Displays können bestimmte Farben auf holografischen Displays unterschiedlich angezeigt werden. Einige Farben werden in Beleuchtungsumgebungen angezeigt, während andere als weniger einflussreich erscheinen. Kalte Farben tendieren dazu, in den Hintergrund zu wechseln, während warme Farben in den Vordergrund springen. Berücksichtigen Sie diese Faktoren, wenn Sie Farben in Ihren Erfahrungen untersuchen:

* **Rendern von hellen Farben:** Weiß erscheint hell und sollte nur wenig verwendet werden. Ziehen Sie in den meisten Fällen einen weißen Wert um R 235 G 235 B 235 in Betracht. Große helle Bereiche können zu Benutzerbeschwerden führen. Für die Hintergrundfarbe des Benutzeroberflächenfensters wird empfohlen, dunkle Farben zu verwenden.

* **Rendern dunkler Farben:** Aufgrund der Art von additiven Displays werden dunkle Farben transparent angezeigt. Ein voll schwarzes Objekt wird sich nicht von der realen Welt unterscheiden. Siehe Alphakanal weiter unten. Probieren Sie einen sehr dunkelgrauen RGB-Wert wie 16,16,16 aus, um das Aussehen von "schwarz" zu erhalten.

* **Farbeinheitlichkeit:** Hologramme werden in der Regel so hell gerendert, dass sie unabhängig vom Hintergrund farblich einheitlich sind. Große Bereiche können zu "Blotlot" werden. Vermeiden Sie große Bereiche mit hellem Vollton.

* **Gamut:** HoloLens profitiert von einem "breiten Farbton", der dem Konzept von Adobe RGB ähnelt. Daher können einige Farben unterschiedliche Qualitäten und Darstellungen auf dem Gerät zeigen.

* **Gamma:** Die Helligkeit und der Kontrast des gerenderten Bilds variieren zwischen immersiven und holografischen Geräten. Diese Geräteunterschiede scheinen oft dunkle Farb- und Schattenbereiche zu machen, die mehr oder weniger hell sind.

* **Farbtrennung:** Die Farbtrennung wird auch als "Farbtrennung" oder "Farbtrennung" bezeichnet und tritt am häufigsten beim Verschieben von Hologrammen (einschließlich Cursor) auf, wenn ein Benutzer Objekte mit den Augen verfolgt.

## <a name="technical-considerations"></a>Technische Überlegungen

* **Aliasing:** Denken Sie an Aliasing, verzoffene oder "100 Schritte", bei denen der Rand der Geometrie eines Hologramms der realen Welt entspricht. Die Verwendung von Texturen mit hohen Details kann diesen Effekt verstärken. Texturen sollten zugeordnet und die Filterung aktiviert werden. Ziehen Sie in Betracht, die Ränder von Hologrammen zu verfingen, oder fügen Sie eine Textur hinzu, die einen schwarzen Randrand um Objekte erstellt. Vermeiden Sie nach Möglichkeit eine schlanke Geometrie.

* **Alphakanal:** Sie müssen ihren Alphakanal für alle Teile, in denen Sie kein Hologramm rendern, vollständig transparent löschen. Wenn Sie das Alpha undefiniert lassen, führt dies zu visuellen Artefakten, wenn Bilder/Videos vom Gerät oder mit Der Bildansicht (Bzw. mit Der Bildansicht) gemacht werden.

* **Texturerweisung:** Da Licht in holografischen Displays additiv ist, ist es am besten, große Bereiche mit hellem Vollton zu vermeiden, da sie häufig nicht den beabsichtigten visuellen Effekt erzeugen.

## <a name="design-guidelines-for-holographic-display"></a>Entwurfsrichtlinien für die holografische Anzeige

![Farbe und Handver occlusion](images/color_handocclusion.jpg)

Beim Entwerfen von Inhalten für holografische Displays gibt es mehrere Elemente, die Sie berücksichtigen müssen, um die beste Erfahrung zu erzielen. Die [Richtlinien und Empfehlungen finden](designing-content-for-holographic-display.md) Sie unter Entwerfen von Inhalten für die holografische Anzeige.

## <a name="storytelling-with-light-and-color"></a>Geschichte mit Licht und Farbe

Licht und Farbe können dazu beitragen, dass Ihre Hologramme in der Umgebung eines Benutzers auf natürliche Weise angezeigt werden und dem Benutzer Anleitungen und Hilfe bieten. Berücksichtigen Sie bei holografischen Erfahrungen die folgenden Faktoren, wenn Sie beleuchtungs- und farblich untersuchen:

:::row:::
    :::column:::
* **Vignetting:** Ein "Effect" zur Verdunkeln von Materialien kann dazu beitragen, die Aufmerksamkeit des Benutzers auf die Mitte des Sichtfelds zu konzentrieren. Durch diesen Effekt wird das Material des Hologramms in einem bestimmten Radius vom Anvisierungsvektor des Benutzers dunkler. Dies ist auch dann effektiv, wenn der Benutzer Hologramme aus einem schrägen oder abblendenden Winkel betrachtet.

* **Hervorhebung:** Ziehen Sie die Aufmerksamkeit auf Objekte oder Interaktionspunkte, indem Sie Farben, Helligkeit und Beleuchtung gegenüberstellen. Einen ausführlicheren Blick auf Beleuchtungsmethoden im Story-Bereich finden Sie unter [Pixelgraphografie – Ein Beleuchtungsansatz für Computergrafiken.](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)<br>
        <br>
        *Bild: Verwendung von Farbe, um die Hervorhebung fürZählelemente zu zeigen, die hier in einer Szene aus [Fragmenten gezeigt wird.](https://www.microsoft.com/p/fragments/9nblggh5ggm8)*
    :::column-end:::
        :::column:::
        ![Verwendung von Farben, um die Hervorhebung für Dienerelemente zu zeigen, die hier in einer Szene aus Fragmenten gezeigt werden.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>Materialien

:::row:::
    :::column:::
Materialien sind wichtige Elemente, um realistische Hologramme zu machen. Indem Sie die richtigen visuellen Merkmale bereitstellen, können Sie überzeugende holografische Objekte erstellen, die sich gut mit der physischen Umgebung verbinden können. Materialien sind auch wichtig, um visuelles Feedback für die verschiedenen Arten von Benutzereingabeinteraktionen zu geben.  

[MRTK stellt](https://github.com/Microsoft/MixedRealityToolkit-Unity) einen MRTK-Standard-Shader mit verschiedenen Optionen für visuelle Effekte zur Verfügung, die für visuelles Feedback verwendet werden können. Beispielsweise können Sie die Eigenschaft "Näherungslicht" verwenden, um einen Beleuchtungseffekt zu erzielen, wenn sich der Finger des Benutzers der Objektoberfläche nähert. Weitere Informationen zum [MRTK-Standard-Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)
    :::column-end:::
        :::column:::
    *Videoschleife: Beispiel für visuelles Feedback basierend auf der Nähe zu einem Begrenzungsfeld* 
     ![ Visuelles Feedback zur Nähe](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>Siehe auch
* [Entwerfen von Inhalten für die holografische Anzeige](designing-content-for-holographic-display.md)
* [Farbtrennung](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [Hologramme](../discover/hologram.md)
* [Microsoft Design Language – Farbe](https://www.microsoft.com/design/color)
* [Universelle Windows-Plattform – Farbe](/windows/uwp/style/color)