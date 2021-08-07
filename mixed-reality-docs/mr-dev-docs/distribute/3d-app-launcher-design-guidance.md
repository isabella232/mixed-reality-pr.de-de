---
title: Entwurfsanleitung für 3D-App-Startprogramm
description: Ein 3D-App-Startfeld ist ein "physisches" Objekt im Mixed Reality-Haus des Benutzers, das er auswählen kann, um eine App zu starten.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, 3D-App-Startfeld, immersives Headset, Livecube, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP, Win32, Beleuchtung, Farbe
ms.openlocfilehash: 2d93930d63b251aa91d77c96b4d5250baba54c51de50388f690b3588b1580761
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188526"
---
# <a name="3d-app-launcher-design-guidance"></a>Entwurfsanleitung für 3D-App-Startprogramm

Wenn Sie ein immersives Headset Windows Mixed Reality (VR) setzen, geben Sie das Windows Mixed Reality ein. Das Haus wird als Haus in einem Von Feldern und Wasser umgebenen Haus visualisiert. Sie können aber auch andere Umgebungen auswählen und sogar [ein eigenes erstellen.](../design/add-custom-home-environments.md) Im Bereich des Heims kann ein Benutzer die 3D-Objekte und -Apps, die für sie wichtig sind, auf beliebige Weise anordnen und organisieren. Ein **3D-App-Startfeld** ist ein "physisches" Objekt im Mixed Reality-Haus des Benutzers, das er auswählen kann, um eine App zu starten.

![Beispiel: Floaty Bird 3D-App-Startfeld](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Beispiel für das Floaty Bird 3D-App-Startfeld (fiktive App)*

## <a name="3d-app-launcher-creation-process"></a>Erstellungsprozess für das 3D-App-Startfeld

Es gibt drei Schritte zum Erstellen eines 3D-App-Startfelds:

1. Entwerfen und Entwerfen (dieser Artikel)
2. [Modellierung und Export](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrieren in Ihre Anwendung:
    * [UWP-Apps](implementing-3d-app-launchers.md)
    * [Win32-Apps](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Entwurfskonzepte

### <a name="fantastic-yet-familiar"></a>Vertrauter und vertrauter

Die Windows Mixed Reality Umgebung, in der sich Ihr App-Startfeld befindet, ist teil vertraut, teil zierliche/sci-fi. Die besten Starter folgen den Regeln dieser Welt. Stellen Sie sich vor, wie Sie ein vertrautes, repräsentatives Objekt aus Ihrer App übernehmen können, aber einige der Regeln der tatsächlichen Realität über sich erhingen. Magic führt dazu.

### <a name="intuitive"></a>Intuitiv

Wenn Sie ihr App-Startfeld betrachten, sollte der Zweck , Ihre App zu starten, offensichtlich sein und keine Verwirrung verursachen. Stellen Sie z. B. sicher, dass Ihr Startfeld ein offensichtlicher, ausreichend repräsentativer Mitarbeiter Ihrer App ist, dass es für einen Teil der Käufe in der App nicht verwirrend Haus an den Klippen. Ihr App-Startfeld sollte Personen einladen, es zu berühren bzw. auszuwählen.

![Beispiel: Neues 3D-Hinweis-App-Startfeld](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Beispiel für das 3D-App-Startfeld mit einem neuen Hinweis (fiktive App)*

### <a name="home-scale"></a>Home scale

3D-App-Startobjekte sind im Haus an den Klippen und ihre Standardgröße sollte mit den anderen "physischen" Objekten im Raum sinnvoll sein. Wenn Sie Ihr Startfeld z. B. neben einer Hausanlage oder einer Bestimmten platzieren, sollte es sich größenweise zu Hause anfühlen. Ein guter Ausgangspunkt ist es, zu sehen, wie es bei 30 kubischen Zentimetern aussieht, aber denken Sie daran, dass Benutzer es nach Be willen hoch- oder herunterskalieren können.

### <a name="own-able"></a>Eigenes

Das App-Startfeld sollte sich wie ein Objekt anfühlen, über das sich eine Person in ihrem Raum freuen würde. Sie werden sich virtuell mit diesen Dingen umgeben, sodass sich das Startfeld so anfühlt, als wäre das, was der Benutzer für wünschenswert hält, um in der Nähe zu bleiben.

![Beispiel: 3D-App-Startfeld für Die Warp-App](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Beispiel für ein 3D-App-Startfeld mit Einer Warp-App (fiktive App)*

### <a name="recognizable"></a>Erkennbar

Ihr 3D-App-Startfeld sollte sofort "die Marke Ihrer App" für Personen ausdrücken, die sie sehen. Wenn Sie ein Sternzeichen oder ein besonders identifizierbares Objekt in Ihrer App haben, wird empfohlen, dies als wichtigen Teil Ihres Entwurfs zu verwenden. In einer Mixed Reality-Welt wird ein Objekt von Benutzern mehr Interesse an sich ziehen als nur ein Logo allein. Erkennbare Objekte kommunizieren schnell und eindeutig mit der Marke.

### <a name="volumetric"></a>Volumetrische

Ihre App ist mehr als nur dazu da, Ihr Logo auf einer flachen Ebene zu installieren und es einmal täglich zu aufrufen. Ihr Startfeld sollte sich wie ein interessantes physisches 3D-Objekt im Raum des Benutzers anfühlen. Ein guter Ansatz ist es, sich vorstellbar, dass Ihre App einen Sprechblasen im Thanksgiving Day Von Macy es ( Thanksgiving Day) haben wird. Stellen Sie sich die Frage, was die Menschen wirklich bei der Straßenabklassung überzeugen würde? Was würde in allen Ansichtswinkeln gut aussehen?

:::row:::
    :::column:::
        ![Nur ](images/20171016-140436-mixedreality-640px.jpg)  Logo
    :::column-end:::
    :::column:::
        ![Besser erkennbar mit einem Zeichen ](images/20171016-140557-mixedreality-640px.jpg) *Mehr erkennbar mit einem Zeichen*
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Flacher Ansatz, nicht überraschend, wirkt flacher Ansatz, nicht ](images/20171016-155101-mixedreality-640px.jpg) *überraschend, wirkt flach*
    :::column-end:::
    :::column:::
        ![Volumetrischer Ansatz zeigt Ihren ](images/20171016-161407-mixedreality-640px.jpg) *Volumetrischen App-Ansatz besser als Ihre App*
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>Tipps für gute 3D-Modelle

* Wenn Sie Dimensionen für Ihr App-Startfeld planen, sollten Sie ungefähr einen 30 cm großen Cube verwenden. Also ein Größenverhältnis von 1:1:1.
* Modelle müssen unter 10.000 Polygonen liegen. [Weitere Informationen zu Dreieckszahlen und Detailebenen (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Testen sie auf einem immersiven Headset.
* Erstellen Sie nach Möglichkeit Details in die Geometrie Ihres Modells– verlassen Sie sich nicht auf Texturen für Details.
* Erstellen Einer "wasserdichten" geschlossenen Geometrie. Keine Lücken, die nicht modelliert werden.
* Verwenden Sie natürliche Materialien in Ihrem Objekt. Imagine sie in der realen Welt zu erstellen.
* Stellen Sie sicher, dass Ihr Modell in unterschiedlichen Entfernungen und Größen gut gelesen wird.
* Wenn Ihr Modell einsatzbereit ist, lesen Sie die Richtlinien [zum Exportieren von Ressourcen.](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)

![Modell mit feinen Details in der Textur](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modell mit feinen Details in der Textur*

### <a name="what-to-avoid"></a>Was Sie vermeiden sollten

* Verwenden Sie keine Details mit hohem Kontrast oder kleine, ausgelastete Muster und Texturen.
* Verwenden Sie keine schlanke Geometrie– sie funktioniert aus der Entfernung nicht gut und hat einen schlechten Alias.
* Lassen Sie nicht zu, dass Teile Ihres Modells zu weit über das Größenverhältnis von 1:1:1 hinausgehen. Dies verursacht Skalierungsprobleme.

![Vermeiden von hohem Kontrast und kleinen ausgelasteten Mustern](images/20171013-143603-mixedreality-640px.jpg)<br>
*Vermeiden von mustern mit hohem Kontrast, kleinen, ausgelasteten Mustern*

## <a name="how-to-handle-type"></a>Behandeln des Typs

* Es wird empfohlen, dass Ihr Typ ca. 1/3 Ihres App-Startfelds (oder mehr) benötigt. Typ ist das Wichtigste, was den Menschen eine Vorstellung davon gibt, dass Ihr Startfeld tatsächlich ein Startfeld ist, sodass es gut ist, wenn es erheblich ist.
* Vermeiden Sie es, den Typ sehr breit zu machen. Versuchen Sie, ihn innerhalb der Grenzen der Kerndimensionen der App-Startfunktionen (mehr oder weniger) zu halten.
* Flache Typen können funktionieren, aber es kann schwierig sein, sie aus bestimmten Winkeln und in bestimmten Umgebungen zu sehen. Sie können erwägen, es als solides Objekt oder Hintergrundobjekt zu verwenden, um dies zu unterstützen.
* Das Hinzufügen von Dimensionen zu Ihrem Typ ist in 3D gut. Das Schattieren der Seiten des Typs mit einer anderen dunkleren Farbe kann zur Lesbarkeit beitragen.

:::row:::
    :::column:::
        ![Flacher Typ ohne Eine-Schleife kann aus bestimmten Winkeln schwer zu sehen sein, und in bestimmten Umgebungen kann es schwierig sein, flache Typen ohne Eine-Schleife aus bestimmten Winkeln und in bestimmten Umgebungen zu ](images/flattype-640px.png) *sehen.*
    :::column-end:::
    :::column:::
        ![Typ mit integrierter Kulisse kann gut funktionieren ](images/flattypeandbkg-640px.png) *Typ mit einer integrierten Kulisse kann gut funktionieren*
    :::column-end:::
    :::column:::
        ![Ein typextruierter Typ kann gut funktionieren, wenn Sie die Seiten schattieren, wenn Sie die Seiten ](images/20171016-160221-mixedreality-640px.jpg) *schattieren.*
    :::column-end:::
:::row-end:::

**Typfarben, die funktionieren**

* Weiß
* Schwarz
* Helle halbabgesättigte Farbe

![Geben Sie Farben ein, die funktionieren.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Typfarben, die funktionieren*

### <a name="colors-to-avoid"></a>Zu vermeidende Farben

Folgende Typfarben verursachen Probleme:

* Mittlere Töne
* Grau
* Überschäumte Farben oder nicht versättigte Farben

![Geben Sie Farben ein, die Probleme verursachen.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Geben Sie Farben ein, die Probleme verursachen.*

## <a name="lighting"></a>Beleuchtung

Die Beleuchtung für Ihr App-Startfeld stammt aus Haus an den Klippen Umgebung. Achten Sie darauf, dass Sie Ihr Startfeld an mehreren Stellen im Haus testen, damit es sowohl im Licht als auch im Schatten gut aussieht. Die gute Nachricht ist: Wenn Sie die anderen Entwurfsanleitungen in diesem Dokument befolgt haben, sollte Ihr Startfeld für die meisten Beleuchtungen in der Haus an den Klippen.

Gute Orte, um zu testen, wie Ihr Startfeld in den verschiedenen Beleuchtungen in der Umgebung aussieht, sind Studio, der Medienraum, überall außerhalb und auf der Rückseite (der konkrete Bereich mit dem Rasen). Ein weiterer guter Test ist es, es in halb hellem und halber Schatten zu setzen und zu sehen, wie es aussieht.

![Stellen Sie sicher, dass Ihr Startfeld sowohl im Licht als auch im Schatten gut aussieht.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Stellen Sie sicher, dass Ihr Startfeld sowohl im Licht als auch im Schatten gut aussieht.*

## <a name="texturing"></a>Texturierung

### <a name="authoring-your-textures"></a>Erstellen ihrer Texturen

Das Endformat Ihres 3D-App-Startfelds ist eine GLB-Datei, die mithilfe der PBR-Pipeline (Physically Based Rendering) erstellt wird. Dies kann ein kniffliger Prozess sein. Jetzt ist ein guter Zeitpunkt, um einen technischen Mitarbeiter zu beschäftigen, falls Sie dies noch nicht tun. Wenn Sie ein gängiger DIY-Er sind, können Sie häufige Fehler vermeiden, wenn Sie sich die Zeit nehmen, [pbr-Terminologie](https://wiki.polycount.com/wiki/PBR) zu recherchiert und zu lernen und zu erfahren, was im Laufe der Zeit passiert, bevor Sie beginnen. 

![Beispiel: Fresh Note-App](images/pbr-freshnote1-640px-500px.png)<br>
*Beispiel für das 3D-App-Startfeld mit einem neuen Hinweis (fiktive App)*

### <a name="recommended-authoring-tool"></a>Empfohlenes Erstellungstool

Es wird empfohlen, [für die endgültige Datei](https://www.allegorithmic.com/products/substance-painter) die Verwendung von 10000000000000000000000022222222.0002222 Wenn Sie nicht mit dem Erstellen von PBR-Shadern in "100000" vertraut sind, finden Sie hier ein [Tutorial.](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)

(Alternativ funktionieren [auch 3D-Lack,](https://3dcoat.com/home/) [Quixel Suite 2](https://quixel.se/suite2/)oder [Marmoset Toolbag,](https://www.marmoset.co/toolbag/) wenn Sie mit einem dieser Tools vertrauter sind.)

### <a name="best-practices"></a>Bewährte Methoden

* Wenn Ihr App-Startobjekt für PBR erstellt wurde, sollte es einfach sein, es für die Haus an den Klippen konvertieren.
* Unser Shader erwartet einen Metal/Roughness-Arbeitsfluss– Der Unreal PBR-Shader ist ein nah-Faksimile.
* Berücksichtigen Sie beim Exportieren Ihrer Texturen die [empfohlenen Texturgrößen.](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)
* Stellen Sie sicher, dass Sie Ihre Objekte für echtzeitbasierte Beleuchtung erstellen. Dies bedeutet:
  * Vermeiden Von Bakingschatten – oder gestrichenen Schatten
  * Vermeiden von Bakinglicht in den Texturen
  * Verwenden Sie eines der PBR-Materialerstellungspakete, um die richtigen Karten für unseren Shader zu erstellen.

## <a name="see-also"></a>Weitere Informationen

* [Erstellen von 3D-Modellen zur Verwendung in Mixed Reality Startumgebung](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementieren von 3D-App-Startprogrammen (UWP-Apps)](implementing-3d-app-launchers.md)
* [Implementieren von 3D-App-Startprogrammen (Win32-Apps)](implementing-3d-app-launchers-win32.md)
