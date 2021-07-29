---
title: Periodensystem der Elemente
description: Erfahren Sie, wie Sie ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen unter Verwendung einer Objektauflistung mit der Periodischen Tabelle der Beispiel-App Elements erstellen.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, Beispiel-App, Steuerelemente, MRTK, Mixed Reality Toolkit, Unity, Beispiel-Apps, Beispiel-Apps, Open Source, Microsoft Store, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 2856d9052f9e1d07b2f796cafeb96fb0cdef63e8
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757306"
---
# <a name="periodic-table-of-the-elements"></a>Periodensystem der Elemente
![Period table of the Elements app (Punkttabelle der Elements-App)](../images/MRDL_PeriodicTable_HL1.jpg)

>[!NOTE]
>In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung von Mixed Reality-Apps teilen. Unsere artikel- und codebezogenen Entwurfsartikel werden sich weiterentwickeln, wenn wir neue Ermittlungen vornehmen.

>[!NOTE]
>Diese Beispiel-App wurde für HoloLens 1. Generation entwickelt. Informationen zu HoloLens 2 Version finden Sie unter [Periodische Tabelle der Elemente 2.0.](periodic-table-of-the-elements-2.md)

[Periodentabelle der Elemente](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Open-Source-Beispiel-App aus den Mixed Reality Design Labs von Microsoft. Erfahren Sie, wie Sie mithilfe einer **[Objektauflistung](../../design/object-collection.md)** ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen layouten. Außerdem erfahren Sie, wie Sie interaktive Objekte erstellen, die auf Standardeingaben aus HoloLens reagieren. Sie können die Komponenten dieses Projekts verwenden, um Ihre eigene Mixed Reality-App-Erfahrung zu erstellen.


## <a name="demo-video"></a>Demovideo 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Aufgezeichnet mit HoloLens 2 mithilfe von Mixed Reality-Aufnahme

## <a name="about-the-app"></a>Informationen zur App

Die Periodentabelle der Elemente visualisiert die physikalischen Elemente und jede ihrer Eigenschaften in einem 3D-Raum. Sie umfasst die grundlegenden Interaktionen von HoloLens wie Anvischen und Tippen in die Luft. Benutzer können sich über die Elemente mit animierten 3D-Modellen informieren. Sie können die Shell eines Elements und deren Atome visuell verstehen, die aus Protonen und Mischungen besteht.

## <a name="background"></a>Hintergrund

Nachdem ich HoloLens kennen gelernt habe, wusste ich, dass ich mit einer Periodentabellen-App in Mixed Reality experimentieren möchte. Da jedes Element über viele Datenpunkte verfügt, die mit Text angezeigt werden, war ich der Meinung, dass es sich um ein hervorragendes Thema für die Untersuchung der typografischen Komposition in einem 3D-Raum handelt. Es war ein weiterer interessanter Teil dieses Projekts, Benutzern die Möglichkeit zu geben, das Modell des Elements zu visualisieren.

## <a name="design"></a>Entwurf

Für die Standardansicht der Periodentabelle habe ich mir dreidimensionale Felder vorgestellt, die das Modell der einzelnen Elemente enthalten würden. Die Oberfläche jedes Felds wäre durchscheinend, sodass der Benutzer eine grobe Vorstellung vom Volume des Elements erhalten kann. Durch Anvischen und Tippen in die Luft kann der Benutzer eine detaillierte Ansicht der einzelnen Elemente öffnen. Um den Übergang zwischen Tabellenansicht und Detailansicht reibungslos und natürlich zu gestalten, ähnelte ich der physischen Interaktion eines Felds, das in der Praxis geöffnet wird.

![Entwurfszeichnung](images/640px-sketch20170406.jpg)<br>
*Entwurfszeichnungen*

In der Detailansicht wollte ich die Informationen der einzelnen Elemente mit visuell gerendertem Text im 3D-Raum visualisieren. Das animierte 3D-Modell wird im mittleren Bereich angezeigt und kann aus verschiedenen Winkeln angezeigt werden.

![Interaktion](images/640px-periodictable-interaction.jpg)

![Prototypen](images/640px-periodictable-prototypes.jpg)<br>
*Interaktionsprototypen*

Der Benutzer kann den Oberflächentyp ändern, indem er auf die Schaltflächen am unteren Rand der Tabelle tippt. Er kann zwischen Ebene, Zylinder, Kugel und Punkt wechseln.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Allgemeine Steuerelemente und Muster, die in dieser App verwendet werden

### <a name="interactable-object-button"></a>Interaktivierbares Objekt (Schaltfläche)

[Interaktivierbares Objekt](../../design/interactable-object.md) ist ein Objekt, das auf einfache HoloLens Eingaben reagieren kann. Sie wird als Prefab/Skript bereitgestellt, das Sie problemlos auf jedes Objekt anwenden können. Beispielsweise können Sie eine Kaffeetasse in Ihrer Szene interaktiv gestalten und auf Eingaben wie Anvieren, Tippen in die Luft, Navigation und Bearbeitungsgesten reagieren. [Weitere Informationen](../../design/interactable-object.md)

![nteractable-Objekt](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Objektsammlung

[Objektauflistung](../../design/object-collection.md) ist ein Objekt, mit dem Sie mehrere Objekte in verschiedenen Formen erstellen können. Sie unterstützt Ebene, Zylinder, Kugel und Punkt. Sie können zusätzliche Eigenschaften wie Radius, Zeilenanzahl und Abstand konfigurieren. [Weitere Informationen](../../design/object-collection.md)

![Objektsammlung](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Technische Details

Skripts und Prefabs für die Periodische Tabelle der Elements-App finden Sie auf der [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>Portieren von Storys für HoloLens 2

Lesen Sie die Geschichte, wie die Periodische Tabelle der Elements-App mit den instinktiven Interaktionen HoloLens 2 aktualisiert wurde.

[Periodensystem der Elemente 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Yoon Park</b></a><br>UX-Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch

* [Hub für MRTK-Beispiele](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Oberflächen](sampleapp-surfaces.md) - [(Aus dem Microsoft Store in HoloLens 2 herunterladen)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Periodensystem der Elemente 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)