---
title: Periodensystem der Elemente
description: Erfahren Sie, wie Sie mithilfe einer Objekt Auflistung mit der periodischen Tabelle der Beispiel-App für Elemente ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen aufstellen.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, Design, Beispiel-APP, Steuerelemente, mrtk, Mixed Reality Toolkit, Unity, Beispiel-apps, Beispiel-apps, Open Source, Microsoft Store, hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: fd525b0d41efa15ff55097456fb6b06dd3d60c25
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009360"
---
# <a name="periodic-table-of-the-elements"></a>Periodensystem der Elemente

>[!NOTE]
>In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Entwurfs Labors für gemischte Realität](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung gemischter Reality-apps teilen. Unsere Entwurfs bezogenen Artikel und Code werden sich weiterentwickeln, wenn wir neue Ermittlungen durchführen.

[Die periodische Tabelle der Elemente](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labs von Microsoft. Erfahren Sie, wie Sie mithilfe einer **[Objekt](../../design/object-collection.md)** Auflistung ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen aufstellen. Außerdem wird beschrieben, wie Sie Objekt übergreifende Objekte erstellen, die auf Standard Eingaben aus hololens reagieren. Sie können die Komponenten dieses Projekts verwenden, um Ihre eigene Benutzeroberflächen Funktion für gemischte Realität zu erstellen.

![Period-Tabelle der Elements-App](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a>Demovideo 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Aufgezeichnet mit hololens 2 mithilfe von Mixed Reality Capture

## <a name="about-the-app"></a>Informationen zur APP

Eine periodische Tabelle der Elemente visualisiert die chemischen Elemente und ihre Eigenschaften in einem 3D-Raum. Es umfasst die grundlegenden Interaktionen von hololens, wie z. b. "Blick" und "Air Tap Benutzer können sich über die Elemente mit animierten 3D-Modellen informieren. Sie können die Elektronen Shell eines Elements und den Kern, der aus den Protonen und den neutralen besteht, visuell verstehen.

## <a name="background"></a>Hintergrund

Nachdem ich die ersten hololens erlebt habe, wusste ich, dass ich mit einer regelmäßigen Tabellen-app in gemischter Realität experimentieren wollte. Da jedes Element viele Datenpunkte enthält, die mit Text angezeigt werden, dachte ich, dass es sich um die Untersuchung der typografischen Komposition in einem 3D-Raum handelt. Den Benutzern die Möglichkeit zu geben, das Elektronen Modell des Elements visuell darzustellen, war ein weiterer interessanter Bestandteil dieses Projekts.

## <a name="design"></a>Entwurf

In der Standardansicht der periodischen Tabelle habe ich dreidimensionale Felder vorgestellt, die das Elektronen Modell der einzelnen Elemente enthalten würden. Die Oberfläche jedes Felds wäre über scheinend, sodass der Benutzer einen groben Überblick über das Volume des Elements erhalten könnte. Mit Blick und Luft tippen könnte der Benutzer eine ausführliche Ansicht der einzelnen Elemente öffnen. Um den Übergang zwischen der Tabellenansicht und der Detailansicht reibungslos und natürlich zu gestalten, habe ich die physische Interaktion eines Box-Öffnens in der Praxis ähnlich gestaltet.

![Entwurfsskizze](images/640px-sketch20170406.jpg)<br>
*Entwurfsskizzen*

In der Detailansicht wollte ich die Informationen jedes Elements mit schön gerendertem Text im 3D-Raum visualisieren. Das animierte 3D-Elektronen Modell wird im mittleren Bereich angezeigt und kann aus unterschiedlichen Winkeln angezeigt werden.

![Interaktion](images/640px-periodictable-interaction.jpg)

![Ty](images/640px-periodictable-prototypes.jpg)<br>
*Interaktions Prototypen*

Der Benutzer kann den Surface-Typ ändern, indem er auf die Schaltflächen am unteren Ende der Tabelle tippt. Sie können Zwischenebene, Zylinder, Kugel und Punkt umschalten.

## <a name="common-controls-and-patterns-used-in-this-app"></a>In dieser APP verwendete allgemeine Steuerelemente und Muster

### <a name="interactable-object-button"></a>Interactable-Objekt (Schaltfläche)

Das [interactable-Objekt](../../design/interactable-object.md) ist ein Objekt, das auf grundlegende hololens-Eingaben reagieren kann. Sie wird als präfab/Skript bereitgestellt, das Sie problemlos auf jedes beliebige Objekt anwenden können. Sie können z. b. einen Kaffeebecher in der Szene in der Szene zusammenstellen und auf Eingaben wie z. b. Blick, Luft tippen, Navigation und Manipulations Gesten reagieren. [Weitere Informationen](../../design/interactable-object.md)

![nteractable-Objekt](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Objektsammlung

Die [Objektsammlung](../../design/object-collection.md) ist ein Objekt, mit dem Sie mehrere Objekte in verschiedenen Formen anordnen können. Es unterstützt Ebene, Zylinder, Kugel und Punkt. Sie können zusätzliche Eigenschaften wie RADIUS, Anzahl der Zeilen und den Abstand konfigurieren. [Weitere Informationen](../../design/object-collection.md)

![Objektsammlung](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Technische Details

Sie finden Skripts und Prefabs für die periodische Tabelle der Elements-App auf dem [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>Portieren von Story für hololens 2

Lesen Sie den Artikel zum Aktualisieren der periodischen Tabelle der Elements-App mit den instanziellen Interaktionen von hololens 2.

[Periodensystem der Elemente 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong-Yoon-Park</b><br>UX-Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch

* [Hub für MRTK-Beispiele](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Oberflächen](sampleapp-surfaces.md) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Periodensystem der Elemente 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)