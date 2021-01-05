---
title: Skalieren
description: Ein wichtiger Aspekt bei der realistischen Wirkung von holografisch dargestellten Inhalten ist das möglichst genaue Nachahmen der visuellen Statistik der echten Welt.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Style, Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, Skalierung, holograms
ms.openlocfilehash: 6711a58fb4dde2aa28272c3003e642c4f4d3e236
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848273"
---
# <a name="scale"></a>Skalieren

Der Schlüssel zum Anzeigen realistischer holografischer Inhalte besteht darin, die visuellen Statistiken der realen Welt so genau wie möglich zu imitieren. Integrieren Sie visuelle Hinweise, um realen Benutzern zu helfen, zu verstehen, wo Objekte sind, wie groß Sie sind und wofür Sie erstellt wurden. Die Skalierung eines Objekts ist eines der wichtigsten visuellen Hinweise, da es dem Viewer einen Eindruck von der Größe und den Hinweisen der Objekte auf seine Position gibt. Außerdem ist das Anzeigen von Objekten in der Praxis eines der wichtigsten Unterschiede in der Praxis im Allgemeinen – was in der vorherigen bildschirmbasierten Anzeige nicht möglich war.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Vorschlagen der Skalierung von Objekten und Umgebungen

Es gibt viele Möglichkeiten, die Skalierung eines Objekts vorzuschlagen, von denen einige mögliche Auswirkungen auf andere perzeptive Faktoren haben. Der Schlüssel besteht darin, Objekte in der Größe "Real" anzuzeigen und diese realistische Größe beizubehalten, wenn die Benutzer verschieben. Holograms beanspruchen den visuellen Winkel eines Benutzers in einer anderen Nähe, wie es bei echten Objekten der Fall ist, wenn Sie näher oder weiter entfernt werden.

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>Verwenden Sie die Entfernung von Objekten, die dem Benutzer angezeigt werden.

Eine gängige Methode ist die Verwendung der Entfernung von Objekten, wie Sie dem Benutzer präsentiert werden. Nehmen Sie beispielsweise an, dass Sie ein großes Familienfahrzeug vor dem Benutzer visualisieren. Wenn das Auto direkt innerhalb der Arm-Länge liegt, wäre es zu groß, um in das Feld des Benutzers zu passen. Close Objects erfordert, dass der Benutzer seine Kopfzeile und den Text verschieben muss, um das gesamte Objekt zu verstehen. Wenn das Fahrzeug weiter entfernt wird (über den Raum), kann der Benutzer einen Sinn der Skalierung einrichten, indem er das gesamte Objekt in der Ansicht sehen kann. Benutzer können sich dann für eine detailliertere Prüfung näher an das Objekt bewegen.

:::row:::
    :::column:::
        Mit diesem Verfahren wurde von **[Volvo ein Showroom](https://www.youtube.com/watch?v=DilzwF90vec)** für ein neues Auto erstellt, das die Skalierung des Holographic Car auf eine Weise war, die für den Benutzer realistisch und intuitiv war. Die Benutzeroberflächen beginnen mit dem autohologram für eine physische Tabelle, sodass der Benutzer die Gesamtgröße und Form des Modells verstehen kann. Zu einem späteren Zeitpunkt wächst das Auto auf eine Skalierung, die über die Größe des Geräts hinausgeht. Da der Benutzer bereits einen Verweis Rahmen aus dem kleineren Modell abgerufen hat, kann er auf die Features des Fahrzeugs angemessen navigieren.<br>
        <br>
        *Image: Volvo Cars-Darstellung für hololens*
    :::column-end:::
        :::column:::
       ![Volvo Cars-Darstellung für hololens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Verwenden Sie holograms, um den tatsächlichen Bereich des Benutzers zu ändern.

Eine andere Methode ist die Verwendung von holograms, um den tatsächlichen Bereich des Benutzers zu ändern, indem die vorhandenen Wände oder Obergrenzen durch Umgebungen ersetzt werden oder "Holes" oder "Windows" angehängt werden. Dies ermöglicht es Objekten, den physischen Raum scheinbar zu "durchbrechen". Beispielsweise kann eine große Struktur nicht in die meisten Benutzer Räume passen, sondern durch das Platzieren eines virtuellen Himmels auf die virtuelle Oberfläche. Dadurch kann der Benutzer die Basis der virtuellen Struktur durchlaufen und einen Eindruck von der Skalierung und der realen Darstellung gewinnen. Benutzer können dann sehen, dass Sie weit über den physischen Raum des Raums hinaus erweitert ist.

:::row:::
    :::column:::
        **[Minecraft entwickelte](https://minecraft.net/)** mithilfe einer ähnlichen Technik ein Konzept. Durch das Hinzufügen eines virtuellen Fensters zu einer physischen Oberfläche werden die vorhandenen Objekte im Raum im Kontext einer erheblich größeren Umgebung platziert, die über die physischen Skalierungs Beschränkungen des Raums hinausgeht.<br>
        <br>
        *Image: minecraft Concept-Darstellung für hololens*
    :::column-end:::
        :::column:::
       ![Minecraft Concept-Darstellung für hololens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Experimentieren mit der Skala

Designer haben mit der Änderung der Skala experimentieren, indem Sie die angezeigte "reale" Größe des Objekts geändert haben. Gleichzeitig behalten Sie eine einzelne Objektposition bei, um einem Objekt zu nähern, das sich ohne wirkliche Bewegung in den Viewer verschiebt. Dies wurde in einigen Fällen getestet, um die Anzeige von Elementen zu beschleunigen, während gleichzeitig die möglichen Komfort Beschränkungen beim Anzeigen von virtuellen Inhalten, die näher sind als die "Zone der Bequemlichkeit", zu berücksichtigen sind.

Dadurch können einige mögliche Artefakte in der-Darstellung erstellt werden:
* Bei virtuellen Objekten, die ein Objekt mit der "bekannten" Größe des Viewers darstellen, führt das Ändern der Skala ohne Änderung der Position zu in Konflikt stehenden visuellen Hinweisen. Die Augen können das Objekt in gewisser Tiefe aufgrund von Vermerk-hinweisen weiterhin "anzeigen". Weitere Informationen finden Sie im Artikel zu [Komfort](comfort.md) . Die Größe fungiert als monokulärer Hinweis darauf, dass das Objekt möglicherweise näher rückt. Diese Konflikt verursachenden Hinweise führen zu verwirrten Wahrnehmungen – Betrachter sehen das Objekt oft als vorhanden (aufgrund der Konstanten Tiefe), werden jedoch schnell vergrößert.
* In einigen Fällen wird die Skalierungs Änderung stattdessen als "sich abzeichtender" Hinweis betrachtet, wobei das Objekt möglicherweise nicht angezeigt wird, um die Skalierung durch einen Viewer zu ändern, aber anscheinend direkt in den Augenblick des Viewers verschoben wird (was eine unangenehme Sensation sein kann).
* Bei Vergleichs Oberflächen in der realen Welt werden solche Skalierungs Änderungen manchmal als veränderliche Position entlang mehrerer Achsen betrachtet – Objekte scheinen geringer zu werden, anstatt einander näher zu bewegen (ähnlich in einer 2D-Projektion der 3D-Bewegung in einigen Fällen).
* Schließlich kann das Ändern der Skalierung für Objekte ohne bekannte Größe (z. b. beliebige Formen mit beliebigen Größen, Benutzeroberflächen Elementen usw.) funktionell als Möglichkeit agieren, Änderungen in der Entfernung nachzuahmen. Viewer verfügen nicht über so viele bereits vorhandene Top-Down-Hinweise, um die tatsächliche Größe oder Position des Objekts zu verstehen, sodass die Skalierung als wichtiger Hinweis verarbeitet werden kann.

<br>

---

## <a name="see-also"></a>Weitere Informationen
* [Farbe, Licht und Materialien](../color,-light-and-materials.md)
* [Typografie](typography.md)
* [Raumklangentwurf](spatial-sound-design.md)
