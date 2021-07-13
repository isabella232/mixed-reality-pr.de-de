---
title: Was ist ein Hologramm?
description: HoloLens können Sie dreidimensionale Hologramme und Objekte aus Licht und Sound anzeigen und mit ihnen interagieren, die in ihrer Umgebung erscheinen.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, Hologramme, Design, Interaktion, Mixed Reality-Headset, Windows Mixed Reality-Headset, Was ist Augmented Reality?
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634331"
---
# <a name="what-is-a-hologram"></a>Was ist ein Hologramm?

HoloLens können Sie **Hologramme** anzeigen, bei denen es sich um Objekte aus Licht und Sound handelt, die in der Welt um Sie herum wie echte Objekte erscheinen. Hologramme können auf Ihre [Anverweise,](../design/gaze-and-commit.md) [Gesten](../design/gaze-and-commit.md#composite-gestures)und [Sprachbefehle](../design/voice-input.md)reagieren. Sie können sogar mit [realen Oberflächen](../design/spatial-mapping.md) um Sie herum interagieren. Hologramme sind digitale Objekte, die Teil Ihrer Welt sind.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Holograms</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>Ein Hologramm besteht aus Licht und Sound.

### <a name="light"></a>Hell

Die Hologramme, die HoloLens [gerendert](../develop/platform-capabilities-and-apis/rendering.md) werden, werden im holografischen Frame direkt vor den Augen der Benutzer angezeigt. Hologramme Ihrer Welt Licht hinzufügen, was bedeutet, dass Sie sowohl das Licht von der Anzeige als auch das Licht aus Ihrer Umgebung sehen. Da HoloLens eine additive Anzeige verwendet, die Licht hinzufügt, wird die schwarze Farbe transparent gerendert. 

Hologramme können sehr unterschiedliche Darstellungen und Verhaltensweisen aufweisen. Einige sind realistisch und solide, während andere zierlich und ätherisch sind. Sie können Hologramme verwenden, um Features in Ihrer Umgebung hervorzuheben oder als Elemente in der Benutzeroberfläche Ihrer App zu verwenden.

![Hände, die ein Hologramm bearbeiten](images/hologram-hands-940px.jpg)

### <a name="sound"></a>Sound

Hologramme können auch [Sounds](../design/spatial-sound.md)erzeugen, die von einem bestimmten Ort in Ihrer Umgebung stammen. Bei HoloLens kommt der Sound von zwei Lautsprechern, die sich direkt über Ihrem Gerät befinden. Wie die holografischen Displays sind die Lautsprecher additiv, was neue Sounds einführt, ohne die Sounds aus Ihrer Umgebung zu blockieren.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Ein Hologramm kann in der Welt platziert oder zusammen mit Ihnen versehen werden.

Wenn Sie über eine feste Position für ein Hologramm verfügen, können Sie es genau an diesem Punkt auf der Welt [platzieren.](../design/coordinate-systems.md) Während Sie sich bewegen, erscheint das Hologramm wie ein physisches Objekt, basierend auf der Welt um Sie herum, stationär. Wenn Sie einen [Raumanker](../design/coordinate-systems.md#spatial-anchors) verwenden, um das Objekt anzuheften, kann sich das System sogar merken, wo Sie es verlassen haben, wenn Sie später zurückkehren.

![Zwei Personen, die Microsoft Dynamics 365 Layout in einem Einzelhandelsbereich verwenden](images/HLS19_retailLayoutHologram_001-940px.jpg)

Einige Hologramme folgen stattdessen dem Benutzer. Sie positionieren sich basierend auf dem Benutzer. Sie können ein Hologramm mit sich bringen und es dann an der Wand platzieren, sobald Sie in einen anderen Raum gelangen.

**Empfohlene Methoden**

* Einige Szenarien erfordern, dass Hologramme während der gesamten Benutzeroberfläche leicht erkennbar oder sichtbar bleiben. Es gibt zwei übergeordnete Ansätze für diese Art der Positionierung. Wir nennen sie **display-locked** und **body-locked**.
   * **Anzeigesperren von Inhalten** sind für das Anzeigegerät gesperrt. Diese Art von Inhalt ist aus verschiedenen Gründen schwierig, einschließlich eines unnatürlichen Gefühls der "Klammerfähigkeit", das viele Benutzer frustriert macht und sie "abwaschen" möchte. Im Allgemeinen haben Designer es besser gefunden, Anzeigesperren von Inhalten zu vermeiden.
   * **Textgesperrte** Inhalte können weitaus verzeihlicher sein. Body-Locking ist, wenn Sie ein Hologramm an den Körper oder anvisierungsvektor des Benutzers im 3D-Raum anbinden. Viele Erfahrungen haben ein Körpersperrverhalten eingeführt, bei dem das Hologramm dem Anvieren des Benutzers folgt, wodurch der Benutzer seinen Körper drehen und sich durch den Raum bewegen kann, ohne das Hologramm zu verlieren. Das Integrieren einer Verzögerung hilft den Hologrammbewegungen, sich natürlicher zu fühlen. Einige kernige Benutzeroberflächen des Windows Holographic OS verwenden z. B. eine Variation der Körpersperrung, die dem Anvieren des Benutzers mit einer elastischen Verzögerung folgt, während der Benutzer den Kopf umdreht.
* Platzieren Sie das Hologramm in einer komfortablen Entfernung von etwa 1 bis 2 Metern vom Kopf.
* Lassen Sie zu, dass Elemente driften, wenn sie sich ständig im holografischen Frame bewegen müssen, oder ziehen Sie in Betracht, Ihren Inhalt auf eine Seite der Anzeige zu verschieben, wenn der Benutzer seine Ansicht ändert. Weitere Informationen finden Sie in der [Markierungs- und](../design/billboarding-and-tag-along.md) Markierungsartilce.

**Platzieren von Hologrammen in der optimalen Zone – zwischen 1,25 m und 5 m**

Zwei Meter sind die optimale Sichtdistanz. Die Benutzeroberfläche wird beeinträchtigt, wenn Sie näher als 1 Meter kommen. Bei Entfernungen von weniger als 1 Meter sind Hologramme, die sich regelmäßig in die Tiefe bewegen, wahrscheinlich problematischer als hologramme. Ziehen Sie in Betracht, Ihre Inhalte ordnungsgemäß zu beschneiden oder auszublenden, wenn sie sich zu nah kommen, damit Sie den Benutzer nicht in eine benutzerfreundliche Ansichtserfahrung eindrücken.

![Optimaler Abstand zum Platzieren von Hologrammen vom Benutzer.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Ein Hologramm interagiert mit Ihnen und Ihrer Welt.

Hologramme geht es nicht nur um Licht und Sound. Sie sind auch ein aktiver Teil Ihrer Welt. Sehen Sie sich ein Hologramm und eine Geste mit der Hand an, und ein Hologramm kann Ihnen folgen. Geben Sie einen Sprachbefehl, und das Hologramm kann antworten.

![Gruppe von Behördenhilfsmitarbeitern, die Microsoft HoloLens 2 verwenden, um an einem Windfarmentwicklungsprojekt zusammenzuarbeiten](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Hologramme persönliche Interaktionen zu ermöglichen, die an anderer Stelle nicht möglich sind. Da der HoloLens weiß, wo er sich auf der Welt befindet, kann ein holografisches Zeichen Sie direkt in den Augen betrachten und eine Konversation mit Ihnen beginnen.

Ein Hologramm kann auch mit Ihrer Umgebung interagieren. Beispielsweise können Sie eine holografische Hüpfkugel über einer Tabelle platzieren. Beobachten Sie dann mit einem [Tippen in](../design/gaze-and-commit.md#composite-gestures)die Luft, wie der Ball abprallt, und machen Sie einen Sound, wenn er auf den Tisch trifft.

Hologramme können auch von realen Objekten verdeckt werden. Beispielsweise kann ein holografisches Zeichen durch eine Tür und hinter einer Wand außerhalb ihrer Sicht gehen.

**Tipps für die Integration von Hologrammen und der realen Welt**

* Durch die Ausrichtung an den Gewichtungsregeln können Hologramme leichter aufeinander bezogen werden und sind leichter zu glauben. Beispiel: Platzieren Sie einen holografischen Hund auf dem Boden & eine Vase auf dem Tisch, anstatt sie im Raum zu gleiten.
* Viele Designer haben festgestellt, dass sie zuverlässigere Hologramme integrieren können, indem sie einen "negativen Schatten" auf der Oberfläche erstellen, auf der sich das Hologramm befindet. Hierzu erstellen sie ein weiches Leuchtlicht auf dem Boden um das Hologramm und subtrahieren dann den "Schatten" vom Leuchtlicht. Das weiche Leuchten lässt sich in das Licht aus der realen Welt integrieren. Der Schatten wird verwendet, um das Hologramm in der Umgebung zu vererbt.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>Ein Hologramm ist das, was <br>Sie können sich einträumen.<br>
        Als holografischer Entwickler haben Sie die Möglichkeit, Ihre Kreativität aus 2D-Bildschirmen herauszubrechen und in die Welt um Sie herum zu gelangen.<br><br>
        Was erstellen *Sie?*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Holografische imaginäre Welt im Leben](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>Nächster Erkundungsprüfpunkt

Sie sind auf der [Ermittlungsreise,](get-started-with-mr.md) die wir festgelegt haben, und erkunden die Grundlagen der Mixed Reality. Von hier aus können Sie mit dem nächsten grundlegenden Thema fortfahren: 

> [!div class="nextstepaction"]
> [Erweitern Ihres Entwurfsprozesses](case-study-expanding-the-design-process-for-mixed-reality.md)