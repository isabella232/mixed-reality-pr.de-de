---
title: Farbe, Licht und Materialien
description: Das Entwerfen von Inhalten für gemischte Realität erfordert sorgfältige Überlegung von Farbe, Beleuchtung und Material für alle visuellen Objekte.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows Mixed Reality-, Design-, Color-, Light-, Material-, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 6e5857436b0325537d0ea5d0321d296c58c09eae
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759265"
---
# <a name="color-light-and-materials"></a>Farbe, Licht und Materialien

![Farbe, Licht und Material](images/RemoteRendering.jpg)

Das Entwerfen von Inhalten für gemischte Realität erfordert sorgfältige Überlegung von Farbe, Beleuchtung und Material für alle virtuellen Ressourcen. Zu den ästhetischen Zwecken kann die Verwendung von Licht und Material verwendet werden, um den Ton einer immersiven Umgebung festzulegen, während funktionale Zwecke die Verwendung von markanten Farben zum Benachrichtigen von Benutzern über eine bevorstehende Aktion beinhalten können. Jede dieser Entscheidungen muss gegen die Möglichkeiten und Einschränkungen für das Zielgerät ihrer Arbeit abgewogen werden.

Im folgenden finden Sie Richtlinien, die speziell für das Rendern von Assets auf immersiven und Holographic Viele davon sind eng an andere technische Bereiche gebunden, und eine Liste verwandter Themen finden Sie im Abschnitt " [Siehe auch](color-light-and-materials.md#see-also) " am Ende dieses Artikels.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Rendering auf immersiven und Holographic-Geräten

Inhalte, die in immersiven Headsets gerendert werden, sind im Vergleich zu in Holographic-Headsets gerenderten Inhalten visuell anders. Obwohl immersive Headsets den Inhalt in der Regel so rendern, wie Sie es auf einem 2D-Bildschirm erwarten würden, verwenden Holographic-Headsets wie hololens Farb sequenzielle anzeigen, um Hologramme zu rendern.

Nehmen Sie sich immer Zeit, um Ihre Holographic-Erfahrungen in einem Holographic-Headset zu testen. Die Darstellung von Inhalten, auch wenn Sie speziell für holografische Geräte erstellt wird, unterscheidet sich wie auf sekundären Monitoren, Momentaufnahmen und in der Ansicht "Betrachter". Denken Sie daran, die Erfahrungen mit einem Gerät zu durchlaufen, die Beleuchtung von holograms zu testen und von allen Seiten zu beobachten (sowie von oberhalb und unten), wie Ihre Inhalte gerendert werden. Stellen Sie sicher, dass Sie mit einem Bereich von Einstellungen für die Helligkeit auf dem Gerät testen. Es ist unwahrscheinlich, dass alle Benutzer einen angenommenen Standard und einen unterschiedlichen Satz von Beleuchtungsbedingungen gemeinsam verwenden.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Grundlagen des Renderings auf Holographic-Geräten

* **Holografische Geräte verfügen über Additive Anzeige** – holograms werden durch das Hinzufügen von Licht in der realen Welt erstellt – weiß weiß, während schwarz angezeigt wird.

* **Die Auswirkung von Farben variiert je nach Benutzerumgebung** – es gibt viele verschiedene Beleuchtungsbedingungen im Raum eines Benutzers. Erstellen Sie Inhalte mit angemessenen Kontrast Ebenen, um die Übersichtlichkeit zu unterstützen.

* **Vermeiden Sie dynamische Beleuchtung** – holograms, die in Holographic-Umgebungen einheitlich beleuchtet werden, sind die effizienteste Lösung. Mithilfe von Advanced werden die Funktionen von mobilen Geräten wahrscheinlich durch die dynamische Beleuchtung überschritten. Wenn eine dynamische Beleuchtung erforderlich ist, wird empfohlen, den [Mixed Reality Toolkit Standard-Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)zu verwenden. 

## <a name="designing-with-color"></a>Entwerfen mit Farbe

Aufgrund der Art der additiven Anzeige können einige Farben in Holographic-anzeigen anders erscheinen. Einige Farben werden in Beleuchtungs Umgebungen angezeigt, während andere weniger beeinträchtigt werden. Kalte Farben neigen tendenziell in den Hintergrund, während die warmen Farben in den Vordergrund gerückt werden. Berücksichtigen Sie die folgenden Faktoren, wenn Sie Farben in ihren Erfahrungen erkunden:

* **Rendern von hellen Farben** : weiß ist hell und sollte sparsam verwendet werden. In den meisten Fällen sollten Sie einen weißen Wert um R 235 G 235 B 235 sehen. Große helle Bereiche können Benutzer Unannehmlichkeiten verursachen. Für das Backplate des Benutzeroberflächen Fensters empfiehlt es sich, dunkle Farben zu verwenden.

* **Rendern von dunklen Farben** : aufgrund der Art von Additiven anzeigen werden dunkle Farben transparent angezeigt. Ein solides Schwarzes Objekt wird nicht anders als die reale Welt angezeigt. Siehe Alpha Kanal weiter unten. Um die Darstellung von "Black" anzugeben, probieren Sie einen sehr dunklen RGB-Wert aus, z. b. 16, 16, 16.

* **Farb Einheitlichkeit** : in der Regel werden holograms hell genug gerendert, sodass Sie die Farb Einheitlichkeit behalten, je nach Hintergrund. Große Bereiche können zu einem blotbereich werden. Vermeiden Sie große Bereiche mit heller, voll Tonfarbe.

* **Gamut** -hololens profitiert von einer "breiten Palette" von Farben, konzeptionell vergleichbar mit Adobe RGB. Folglich können einige Farben verschiedene Qualitäten und Darstellung im Gerät anzeigen.

* **Gamma** : die Helligkeit und der Kontrast des gerenderten Bilds unterscheiden sich zwischen immersiven und holografischen Geräten. Diese Geräte Unterschiede scheinen häufig dunkle Bereiche von Farbe und Schatten zu bilden, die mehr oder weniger hell sind.

* **Farbtrennung** : wird auch als "Farb Aufschlüsselung" oder "farbrandging" bezeichnet. die Farbtrennung tritt am häufigsten bei der Verschiebung von holograms (einschließlich Cursor) auf, wenn ein Benutzer Objekte mit den Augen nachverfolgt.

## <a name="technical-considerations"></a>Technische Überlegungen

* **Aliasing** : Sie können die Aliasing-, Verzweigungs-oder "Treppen Schritte" übernehmen, bei denen der Rand der Geometrie eines holograms der realen Welt entspricht. Durch die Verwendung von Texturen mit hoher Detailgenauigkeit kann dieser Effekt erschwert werden. Texturen sollten zugeordnet und gefiltert werden. Sie sollten die Ränder von holograms ausblenden oder eine Textur hinzufügen, die eine schwarze Rahmen Linie um Objekte erzeugt. Vermeiden Sie nach Möglichkeit schlanke Geometrie.

* **Alphakanal** : Sie müssen den Alphakanal für alle Teile, in denen Sie kein Hologram rendern, vollständig transparent löschen. Das nicht definierte Alpha definierte führt zu visuellen Elementen, wenn Bilder/Videos vom Gerät oder der Ansicht "Betrachter" übernommen werden.

* **Textur Dämpfung** : da Light in Holographic-anzeigen Additiv ist, empfiehlt es sich, große Bereiche von hellen, voll Tonfarben zu vermeiden, da Sie häufig nicht den beabsichtigten visuellen Effekt ergeben.

## <a name="design-guidelines-for-holographic-display"></a>Entwurfs Richtlinien für die holografische Anzeige

![Farb-und Hand oksion](images/color_handocclusion.jpg)

Beim Entwerfen von Inhalten für Holographic-anzeigen müssen Sie mehrere Elemente in Erwägung gezogen, um die bestmögliche Leistung zu erzielen. Die Richtlinien und Empfehlungen finden Sie unter [Entwerfen von Inhalten für die Holographic-Anzeige](designing-content-for-holographic-display.md) .

## <a name="storytelling-with-light-and-color"></a>Storytelling mit Licht und Farbe

"Light" und "Color" können dazu beitragen, dass Ihre Hologramme in der Umgebung eines Benutzers natürlicher erscheinen und Anleitungen und Hilfe für den Benutzer bereitstellen. Berücksichtigen Sie die folgenden Faktoren, um die Beleuchtung und die Farbe zu untersuchen:

:::row:::
    :::column:::
* **Vignetup** : ein "Vignette"-Effekt auf abdunkeln Materialien kann die Aufmerksamkeit des Benutzers auf den Mittelpunkt des Felds der Ansicht konzentrieren. Dadurch wird das Material des Hologramms in einem RADIUS aus dem Blick Vektor des Benutzers dunkel. Dies ist auch wirksam, wenn der Benutzer holograms aus einem schrägen oder ausöffnende Winkel anzeigt.

* **Akzente** : ziehen Sie die Aufmerksamkeit auf Objekte oder Interaktionspunkte durch kontrastreiche Farben, Helligkeit und Beleuchtung. Eine ausführlichere Betrachtung der Beleuchtungs Methoden in Storytelling finden Sie unter [Pixel-kinemgraphy-a-Beleuchtungs Ansatz für Computer Grafiken](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).<br>
        <br>
        *Image: Verwenden von Color zum Anzeigen der Betonung von Storytelling-Elementen, die hier in einer Szene von [Fragmenten](https://www.microsoft.com/p/fragments/9nblggh5ggm8)dargestellt werden.*
    :::column-end:::
        :::column:::
        ![Verwendung von Color zum Anzeigen der Betonung von Storytelling-Elementen, die hier in einer Szene von Fragmenten dargestellt werden.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>Materialien

:::row:::
    :::column:::
Material sind wichtige Elemente zum Treffen realistischer holograms. Durch die Bereitstellung geeigneter visueller Merkmale können Sie überzeugende Holographic-Objekte erstellen, die sich gut mit der physischen Umgebung vermischen. Material ist auch für die Bereitstellung von visuellem Feedback für die verschiedenen Arten von Benutzereingabe Interaktionen wichtig.  

[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) bietet einen mrtk-Standard-Shader mit verschiedenen visuellen Effekt Optionen, die für visuelles Feedback verwendet werden können. Beispielsweise können Sie die Eigenschaft "Near Light" verwenden, um einen Beleuchtungs Effekt bereitzustellen, wenn der Finger des Benutzers die Oberfläche des Objekts nähert. Weitere Informationen zum [mrtk-Standard-Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/rendering/mrtk-standard-shader.md)
    :::column-end:::
        :::column:::
    *Video Schleife: Beispiel für visuelles Feedback basierend auf der Nähe eines* 
     ![ umgebenden Felds Visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>Weitere Informationen
* [Entwerfen von Inhalten für die holografische Anzeige](designing-content-for-holographic-display.md)
* [Farbtrennung](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [Hologramme](../discover/hologram.md)
* [Microsoft Design Language-Farbe](https://www.microsoft.com/design/color)
* [Universelle Windows-Plattform Farbe](/windows/uwp/style/color)