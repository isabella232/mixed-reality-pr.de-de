---
title: Periodensystem der Elemente
description: Erfahren Sie, wie Sie ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen erstellen, indem Sie eine Objektsammlung mit dem Periodensystem der Beispiel-App Elements verwenden.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, Beispiel-App, Steuerelemente, MRTK, Mixed Reality Toolkit, Unity, Beispiel-Apps, Beispiel-Apps, Open Source, Microsoft Store, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: aab6789939823b8c6e200bb5456118002b848e3c2f166abe50d4788ac8e7430d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211885"
---
# <a name="periodic-table-of-the-elements"></a>Periodensystem der Elemente
![Zeitraumtabelle der Elements-App](../images/MRDL_PeriodicTable_HL1.jpg)

>[!NOTE]
>In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erfahrungen und Vorschläge für die Entwicklung von Mixed Reality-Apps teilen. Unsere designbezogenen Artikel und der Code werden weiterentwickelt, wenn wir neue Erkenntnisse machen.

>[!NOTE]
>Diese Beispiel-App wurde für HoloLens 1. Generation entwickelt. Weitere Informationen finden Sie unter Periodic Table of the Elements 2.0 (Periodische Tabelle der Elemente [2.0)](periodic-table-of-the-elements-2.md) HoloLens 2 Version.

[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Open Source-Beispiel-App aus den Mixed Reality Design Labs von Microsoft. Erfahren Sie, wie Sie mithilfe einer Objektsammlung ein Array von Objekten im 3D-Raum mit verschiedenen **[Oberflächentypen erstellen.](../../design/object-collection.md)** Außerdem erfahren Sie, wie Sie interaktionsfähige Objekte erstellen, die auf Standardeingaben von HoloLens. Sie können die Komponenten dieses Projekts verwenden, um Ihre eigene Mixed Reality-App-Erfahrung zu erstellen.


## <a name="demo-video"></a>Demovideo 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Aufgezeichnet mit HoloLens 2 mit Mixed Reality-Aufnahme

## <a name="about-the-app"></a>Informationen zur App

Das Periodensystem der Elemente visualisiert die chemieischen Elemente und jede ihrer Eigenschaften in einem 3D-Raum. Es umfasst die grundlegenden Interaktionen von HoloLens wie Anv basic und Tippen in die Luft. Benutzer können sich mit animierten 3D-Modellen über die Elemente informieren. Sie können die Atomenshell eines Elements und seine Hülle visuell verstehen, die aus Protonen und Protonen besteht.

## <a name="background"></a>Hintergrund

Nachdem ich das erste Mal HoloLens, wusste ich, dass ich mit einer Periodentabellen-App in Mixed Reality experimentieren möchte. Da jedes Element über viele Datenpunkte verfügt, die mit Text angezeigt werden, war ich der Meinung, dass es sich um ein hervorragendes Thema für die Untersuchung der typografischen Komposition in einem 3D-Raum handelt. Es war ein weiterer interessanter Teil dieses Projekts, Benutzern die Möglichkeit zu geben, das Rastermodell des Elements zu visualisieren.

## <a name="design"></a>Entwurf

Für die Standardansicht der Periodentabelle stellt ich mir dreidimensionale Felder vor, die das Rastermodell der einzelnen Elemente enthalten würden. Die Oberfläche jedes Felds wäre durchsichtig, sodass der Benutzer eine grobe Vorstellung vom Volume des Elements erhalten könnte. Mit Anving und Tippen in die Luft kann der Benutzer eine detaillierte Ansicht der einzelnen Elemente öffnen. Um den Übergang zwischen Tabellenansicht und Detailansicht reibungslos und natürlich zu machen, habe ich es ähnlich gemacht wie die physische Interaktion eines Felds, das sich in der realen Umgebung öffnet.

![Entwurfs skizzieren](images/640px-sketch20170406.jpg)<br>
*Entwurfs skizzieren*

In der Detailansicht wollte ich die Informationen der einzelnen Elemente mit einem gerenderten Text im 3D-Raum visualisieren. Das animierte 3D-Rastermodell wird im Mittelpunkt angezeigt und kann aus unterschiedlichen Winkeln angezeigt werden.

![Interaktion](images/640px-periodictable-interaction.jpg)

![Prototypen](images/640px-periodictable-prototypes.jpg)<br>
*Interaktionsprototypen*

Der Benutzer kann den Oberflächentyp ändern, indem er auf die Schaltflächen am unteren Rand der Tabelle tippt. Er kann zwischen Ebene, Zylinder, Kugel und Punkt wechseln.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Allgemeine Steuerelemente und Muster, die in dieser App verwendet werden

### <a name="interactable-object-button"></a>Interagierbares Objekt (Schaltfläche)

[Ein interagierbares](../../design/interactable-object.md) Objekt ist ein Objekt, das auf grundlegende HoloLens reagieren kann. Es wird als Prefab/Skript bereitgestellt, das Sie problemlos auf jedes Objekt anwenden können. Beispielsweise können Sie eine Kaffeetasse in Ihrer Szene interagierbar machen und auf Eingaben wie Anving, Tippen in die Luft, Navigation und Manipulationsgesten reagieren. [Weitere Informationen](../../design/interactable-object.md)

![nteractable-Objekt](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Objektsammlung

[Die Objektsammlung](../../design/object-collection.md) ist ein Objekt, mit dem Sie mehrere Objekte in verschiedenen Formen gestalten können. Sie unterstützt Ebene, Zylinder, Kugel und Punkt. Sie können zusätzliche Eigenschaften konfigurieren, z. B. Radius, Anzahl von Zeilen und Abstand. [Weitere Informationen](../../design/object-collection.md)

![Objektsammlung](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>Technische Details

Skripts und Prefabs für das Periodensystem der Elements-App finden Sie im Mixed Reality [Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="porting-story-for-hololens-2"></a>Portieren der Story für HoloLens 2

Lesen Sie die Geschichte dazu, wie das Periodensystem der Elements-App mit den instinktiven Interaktionen HoloLens 2 aktualisiert wurde.

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