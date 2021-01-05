---
title: Entwurfsanleitung für 3D-App-Startprogramm
description: Ein 3D-App-Startfeld ist ein "physisches" Objekt im gemischten Reality-Haus des Benutzers, das Sie auswählen können, um eine APP zu starten.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, 3D-App-Start Programm, immersives Headset, Live Cube, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, UWP, Win32, Beleuchtung, Farbe
ms.openlocfilehash: 2edb09e47da5bcbae34a37f004853002f3f65cf3
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757728"
---
# <a name="3d-app-launcher-design-guidance"></a>Entwurfsanleitung für 3D-App-Startprogramm

Wenn Sie ein Windows Mixed Reality immersive-Headset (VR) einfügen, geben Sie das Windows Mixed Reality Home ein. Die Startseite wird als Haus auf einer Klippe dargestellt, die von den Bergen und Wasser umgeben ist, aber Sie können [auch andere Umgebungen auswählen und sogar eigene Umgebungen erstellen](../design/add-custom-home-environments.md). Innerhalb des Speicherplatzes kann ein Benutzer die 3D-Objekte und-apps, für die Sie sich interessieren, anordnen und organisieren. Ein **3D-App-** Startfeld ist ein "physisches" Objekt im gemischten Reality-Haus des Benutzers, das Sie auswählen können, um eine APP zu starten.

![Beispiel: floaty Bird 3D-App-Startfeld](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Beispiel für floaty Bird 3D-App-Startfeld (fiktive APP)*

## <a name="3d-app-launcher-creation-process"></a>Erstellung eines 3D-App-Start Programms

Zum Erstellen eines 3D-App-Start Programms sind drei Schritte erforderlich:

1. Entwerfen und entwerfen (dieser Artikel)
2. [Modellieren und exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integration in Ihre Anwendung:
    * [UWP-Apps](implementing-3d-app-launchers.md)
    * [Win32-Apps](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Entwurfskonzepte

### <a name="fantastic-yet-familiar"></a>Fantastisch, aber schon vertraut

Die Windows Mixed Reality-Umgebung, in der sich Ihr App-Startfeld befindet, ist Teil vertraut, Teil fantastisch/Sci-Fi. Die besten Launcher befolgen die Regeln dieser Welt. Stellen Sie sich vor, wie Sie ein vertrautes, repräsentatives Objekt von Ihrer APP aus erstellen, aber einige der Regeln der tatsächlichen Realität übernehmen können. Magic führt dazu.

### <a name="intuitive"></a>Intuitiven

Wenn Sie sich Ihr App-Startfeld ansehen, sollte der Zweck zum Starten Ihrer APP offensichtlich sein und keine Verwirrung verursachen. Stellen Sie sich z. b. vor, dass Ihr Start Programm ein offensichtlich-genug repräsentativ für Ihre APP ist, dass Sie nicht mit einem Teil der Einrichtung im Klippe-Haus verwechselt wird. Ihr App-Start Programm sollte Personen einladen, Sie zu berühren bzw. auszuwählen.

![Beispiel: neues Hinweis 3D-App-Startfeld](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Neues Hinweis Beispiel für 3D-App-Start Programm (fiktive APP)*

### <a name="home-scale"></a>Start Skala

3D-App-Launcher Leben im Klippe-Haus, und ihre Standardgröße sollte mit den anderen "physischen" Objekten im Raum Sinn machen. Wenn Sie das Start Programm anordnen, beispielsweise eine Hausanlage oder einige Möbel, sollte es sich in der eigenen Größe fühlen. Ein guter Ausgangspunkt ist, zu sehen, wie es 30 Kubikzentimeter aussieht, aber denken Sie daran, dass Benutzer es bei Bedarf zentral hoch-oder Herunterskalieren können.

### <a name="own-able"></a>Eigen fähig

Das App-Start Programm sollte sich wie ein Objekt erweisen, das eine Person im Raum haben würde. Sie werden sich praktisch durch diese Dinge umgeben, sodass das Start Programm so aussehen sollte, wie etwas, was der Benutzer als wünschenswert erachtet hat

![Beispiel: Astro Warp 3D-App-Startfeld](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Beispiel für ein Beispiel für die Astro Warp 3D-app (fiktive APP)*

### <a name="recognizable"></a>Unerkannt

Ihr 3D-App-Startfeld sollte den Benutzern, die Sie sehen, umgehend die "Marke Ihrer APP" ausdrücken. Wenn Sie in Ihrer APP über ein Sternzeichen oder ein besonders identifizierbares Objekt verfügen, empfiehlt es sich, dieses als wesentlichen Bestandteil des Entwurfs zu verwenden. In einer Mixed Reality-Welt zeichnet ein Objekt von Benutzern mehr Interesse als nur ein Logo allein. Erkennbare Objekte kommunizieren schnell und eindeutig.

### <a name="volumetric"></a>Volumetrische

Ihre APP verdient mehr als nur Ihr Logo auf eine flache Ebene zu bringen und Sie täglich Aufrufs. Das Start Programm sollte sich wie ein spannendes, 3D-Objekt im Bereich des Benutzers fühlen. Eine gute Vorgehensweise besteht darin, sich zu vorstellen, dass Ihre APP in der Tages Parade der Macy-Tage eine Sprechblase enthalten würde. Fragen Sie sich, was wirklich Menschen ist, die sich in der Straße befinden? Was ist für alle Anzeige Winkel großartig?

:::row:::
    :::column:::
        ![Nur Logo nur ](images/20171016-140436-mixedreality-640px.jpg) *Logo*
    :::column-end:::
    :::column:::
        ![Besser erkennbar durch ein Zeichen, das ](images/20171016-140557-mixedreality-640px.jpg) *mit einem Zeichen besser erkennbar* ist
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Flacher Ansatz, nicht überraschend, ist ein flacher ](images/20171016-155101-mixedreality-640px.jpg) *Ansatz, nicht überraschend, ist flach*
    :::column-end:::
    :::column:::
        ![Volumetric-Ansatz zeigt Ihren app- ](images/20171016-161407-mixedreality-640px.jpg) *volumetriansatz besser an und zeigt Ihre APP besser* an
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>Tipps für gute 3D-Modelle

* Wenn Sie Dimensionen für das App-Start Programm planen, sollten Sie ungefähr einen 30 cm-Cube durchsuchen. Also ein Größenverhältnis von 1:1:1.
* Modelle müssen unter 10.000 Polygone liegen. [Weitere Informationen zu Dreiecks Zählungen und Ebenen der Details (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Testen Sie auf einem immersiven Headset.
* Builddetails in der Geometrie des Modells, soweit möglich – verlassen Sie sich nicht auf Texturen.
* Erstellen einer "wasserdichten" geschlossenen Geometrie. Keine Lücken, die nicht in modelliert werden.
* Verwenden Sie natürliche Materialien in Ihrem Objekt. Stellen Sie sich vor, Sie erstellen Sie in der Praxis.
* Stellen Sie sicher, dass Ihr Modell in unterschiedlichen Entfernungen und Größen gut funktioniert.
* Wenn Ihr Modell einsatzbereit ist, lesen Sie die [Richtlinien zum Exportieren von Assets](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![Modell mit geringfügigen Details in der Textur](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modell mit geringfügigen Details in der Textur*

### <a name="what-to-avoid"></a>Was Sie vermeiden sollten

* Verwenden Sie keine kontrastreichen Details oder kleine, ausgelastete Muster und Texturen.
* Verwenden Sie Thin Geometry nicht – es funktioniert nicht gut in einer Entfernung und ist falsch.
* Lassen Sie Teile des Modells nicht zu viel über das Größenverhältnis von 1:1:1 hinaus erweitern. Es werden Skalierungsprobleme entstehen.

![Vermeiden Sie Muster mit hohem Kontrast und geringer Auslastung](images/20171013-143603-mixedreality-640px.jpg)<br>
*Vermeiden Sie große Kontraste, kleine, ausgelastete Muster*

## <a name="how-to-handle-type"></a>Vorgehensweise beim Behandeln von Typen

* Es wird empfohlen, dass Ihr Typ ungefähr 1/3 ihres App-Start Programms (oder mehr) annimmt. Der Typ ist das wichtigste, das den Benutzern eine Vorstellung gibt, dass es sich bei Ihrem Start Programm tatsächlich um ein Start Programm handelt, sodass es sehr schön ist.
* Vermeiden Sie einen Super weiten Typ – versuchen Sie, ihn innerhalb der Grenzen der Kerndimensionen der App-Launcher (mehr oder weniger) zu halten.
* Der flattype kann funktionieren, kann jedoch in bestimmten Winkeln und in bestimmten Umgebungen schwierig angezeigt werden. Möglicherweise sollten Sie ein solides Objekt oder einen Hintergrund dahinter ablegen, um dies zu unterstützen.
* Das Hinzufügen von Dimensionen zu Ihrem Typ ist in 3D gut. Das Schattieren der Seiten des Typs unterscheidet sich durch die Lesbarkeit.

:::row:::
    :::column:::
        ![Ein flacher Typ ohne einen Hintergrund kann in bestimmten Winkeln nicht angezeigt werden, und in bestimmten Umgebungen ](images/flattype-640px.png) *kann der flache Typ ohne einen Hintergrund in bestimmten Winkeln und in bestimmten Umgebungen schwierig angezeigt werden* .
    :::column-end:::
    :::column:::
        ![Der Typ mit einem integrierten Hintergrund kann gut funktionieren, wenn ](images/flattypeandbkg-640px.png) *ein integrierter Hintergrund* funktionsfähig ist.
    :::column-end:::
    :::column:::
        ![Der Typ "extrudiert" kann gut funktionieren, wenn Sie die Seiten mit dem ](images/20171016-160221-mixedreality-640px.jpg) *Typ "extrudiert" gut funktionieren, wenn Sie die Seiten schattieren*
    :::column-end:::
:::row-end:::

**Typfarben, die funktionieren**

* White
* Schwarz
* Helle halb satte Farbe

![Typfarben, die funktionieren.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Typfarben, die funktionieren*

### <a name="colors-to-avoid"></a>Zu vermeide Farben

Typfarben, die Probleme verursachen, sind:

* Mitteltöne
* Grau
* Über satte Farben oder nicht satte Farben

![Typfarben, die Probleme verursachen.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Typfarben, die Probleme verursachen*

## <a name="lighting"></a>Beleuchtung

Die Beleuchtung für das App-Start Programm stammt aus der Umgebung "Klippe House". Stellen Sie sicher, dass Sie das Start Programm an mehreren Stellen im ganzen Haus testen, damit es in Licht und Schatten gut aussieht. Die gute Nachricht ist, dass Sie, wenn Sie den anderen Entwurfs Leit Faden in diesem Dokument befolgt haben, das Start Programm für die meisten Beleuchtung im Klippe-Haus in guter Form aufweisen sollte.

Ein guter Ausgangspunkt, um zu testen, wie das Start Programm in den verschiedenen Lichtern in der Umgebung aussieht, sind Studio, der Medienraum, an einer beliebigen Stelle außerhalb und auf der Rückseite (der konkrete Bereich mit dem Rasen). Ein weiterer guter Test besteht darin, den halblicht-und Halbschatten zu platzieren und zu sehen, wie er aussieht.

![Stellen Sie sicher, dass das Start Programm sowohl in Beleuchtung als auch in Schatten angezeigt wird.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Stellen Sie sicher, dass das Start Programm in Licht und Schatten gut aussieht*

## <a name="texturing"></a>Texturierung

### <a name="authoring-your-textures"></a>Erstellen von Texturen

Das Endformat des 3D-App-Start Programms ist eine. GLB-Datei, die mithilfe der PBR-Pipeline (physisch basiertes Rendering) erstellt wird. Dies kann ein kniffliger Prozess sein. jetzt ist es ein guter Zeitpunkt, einen technischen Künstler zu verwenden, wenn Sie dies noch nicht getan haben. Wenn Sie ein mutiger DIY sind und sich die Zeit nehmen, sich mit der [PBR-Terminologie](https://wiki.polycount.com/wiki/PBR) vertraut zu machen und zu erfahren, was im Hintergrund passiert, bevor Sie beginnen, können Sie häufige Fehler vermeiden. 

![Beispiel: neue Notiz-App](images/pbr-freshnote1-640px-500px.png)<br>
*Neues Hinweis Beispiel für 3D-App-Start Programm (fiktive APP)*

### <a name="recommended-authoring-tool"></a>Empfohlenes Authoring Tool

Es wird empfohlen, den [Substanz Maler](https://www.allegorithmic.com/products/substance-painter) von allethmic zu verwenden, um Ihre endgültige Datei zu verfassen. Wenn Sie nicht mit der Erstellung von PBR-Shadern in der Inhalts Malerin vertraut sind, finden Sie hier ein [Tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).

(Alternativ kann [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/)oder [marthset](https://www.marmoset.co/toolbag/) auch verwendet werden, wenn Sie mit einer der beiden vertraut sind.)

### <a name="best-practices"></a>Bewährte Methoden

* Wenn das App-Start Programmobjekt für PBR erstellt wurde, sollte es einfach sein, es für die Umgebung "Felsen Umgebung" zu konvertieren.
* Unser Shader erwartet einen Metal/roughness-Workflow – der Unreal PBR-Shader ist ein schließende Fax.
* Beachten Sie beim Exportieren der Texturen die [empfohlenen Textur Größen](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) .
* Stellen Sie sicher, dass Sie die Objekte für die Echtzeitbeleuchtung erstellen – Dies bedeutet Folgendes:
  * Vermeiden gebackener Schatten – oder gezeichnete Schatten
  * Vermeiden Sie eine gebackenes Beleuchtung in den Texturen
  * Verwenden Sie eines der Pakete zur Erstellung von PBR-Materialien, um die richtigen Zuordnungen für den Shader zu erhalten.

## <a name="see-also"></a>Weitere Informationen

* [Erstellen von 3D-Modellen für die Verwendung in der Mixed Reality-Startseite](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementieren von 3D-App-Startprogrammen (UWP-Apps)](implementing-3d-app-launchers.md)
* [Implementieren von 3D-App-Startprogrammen (Win32-Apps)](implementing-3d-app-launchers-win32.md)
