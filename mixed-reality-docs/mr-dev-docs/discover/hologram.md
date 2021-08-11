---
title: Was ist ein Hologramm?
description: HoloLens können Sie dreidimensionale Hologramme, Objekte aus Licht und Sound, die in ihrer Umgebung angezeigt werden, anzeigen und mit ihnen interagieren.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, Hologramme, Design, Interaktion, Mixed Reality-Headset, Windows Mixed Reality-Headset, Was ist Augmented Reality?
ms.openlocfilehash: e028fe6180bded26263fa47feb5acefc94570222e43f10fe85db5adf90307844
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202115"
---
# <a name="what-is-a-hologram"></a>Was ist ein Hologramm?

HoloLens können Sie **Hologramme** anzeigen, bei denen es sich um Objekte aus Licht und Sound handelt, die in der Welt um Sie herum wie echte Objekte angezeigt werden. Hologramme antwortet auf Ihre Befehle [anv,](../design/gaze-and-commit.md) [Gesten](../design/gaze-and-commit.md#composite-gestures) [und Sprache.](../design/voice-input.md) Sie können sogar mit realen [Oberflächen um](../design/spatial-mapping.md) Sie herum interagieren. Hologramme sind digitale Objekte, die Teil Ihrer Welt sind.

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

## <a name="a-hologram-is-made-of-light-and-sound"></a>Ein Hologramm besteht aus Licht und Sound

### <a name="light"></a>Hell

Die Hologramme, HoloLens [gerendert](../develop/platform-capabilities-and-apis/rendering.md) werden, werden im holografischen Rahmen direkt vor den Augen der Benutzer angezeigt. Hologramme Ihrer Welt Licht hinzufügen, was bedeutet, dass Sie sowohl das Licht von der Anzeige als auch das Licht aus Ihrer Umgebung sehen. Da HoloLens eine additive Anzeige verwendet, die Licht hinzufügt, wird die schwarze Farbe transparent gerendert. 

Hologramme können sehr unterschiedliche Darstellungen und Verhaltensweisen haben. Einige sind realistisch und solide, andere sind verleerlich und ässisch. Sie können Hologramme verwenden, um Features in Ihrer Umgebung hervorzuheben, oder sie als Elemente in der Benutzeroberfläche Ihrer App verwenden.

![Hand, die ein Hologramm bearbeiten](images/hologram-hands-940px.jpg)

### <a name="sound"></a>Sound

Hologramme können auch Sounds [erzeugen,](../design/spatial-sound.md)die von einem bestimmten Ort in Ihrer Umgebung stammen. Auf HoloLens sound stammt der Sound von zwei Lautsprechern, die sich direkt über Ihrem Töne befinden. Wie bei den holografischen Displays sind die Sprecher additiv und führen neue Sounds ein, ohne die Töne aus Ihrer Umgebung zu blockieren.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Ein Hologramm kann zusammen mit Ihnen in der Welt platziert oder mit Tags versehen werden.

Wenn Sie über eine feste Position für [](../design/coordinate-systems.md) ein Hologramm verfügen, können Sie es genau an diesem Punkt auf der Welt platzieren. Während Sie durch die Umgebung gehen, erscheint das Hologramm auf Der Welt um Sie herum wie ein physisches Objekt. Wenn Sie einen [Raumanker zum](../design/coordinate-systems.md#spatial-anchors) Anheften des Objekts verwenden, kann sich das System sogar merken, wo Sie es verlassen haben, wenn Sie später wiederkommen.

![Zwei Personen, die Microsoft Dynamics 365 Layout in einem Einzelhandelsbereich verwenden](images/HLS19_retailLayoutHologram_001-940px.jpg)

Einige Hologramme folgen stattdessen dem Benutzer. Sie positionieren sich basierend auf dem Benutzer. Sie können ein Hologramm mitbringen und es dann an der Wand platzieren, sobald Sie in einen anderen Raum kommen.

**bewährten Methoden**

* In einigen Szenarien ist es erforderlich, dass Hologramme während der gesamten Beerfahrung leicht erkennbar oder sichtbar bleiben. Es gibt zwei ansätze auf hoher Ebene für diese Art der Positionierung. Nennen wir sie **anzeigegesperrt und** **textgesperrt.**
   * **Der inhalt mit Anzeigesperrung** ist auf dem Anzeigegerät gesperrt. Diese Art von Inhalt ist aus verschiedenen Gründen schwierig, einschließlich eines unnatürlichen Gefühls der "Klammer", das viele Benutzer frustriert macht und sie "abhaken" möchte. Im Allgemeinen ist es für Designer besser, Das Sperren von Inhalten zu vermeiden.
   * **Textgesperrte** Inhalte können weitaus weniger verzeihend sein. Die Körpersperre ist , wenn Sie ein Hologramm an den Körper oder Anvisierungsvektor des Benutzers im 3D-Raum anschließen. Viele Benutzeroberflächen haben ein Textsperrverhalten übernommen, bei dem das Hologramm dem Anvieren des Benutzers folgt, wodurch der Benutzer seinen Körper drehen und sich durch den Raum bewegen kann, ohne das Hologramm zu verlieren. Durch das Integrieren einer Verzögerung werden die Hologrammbewegungen natürlicher. Einige Kernbenutzeroberflächen des Windows Holographic-Betriebssystems verwenden z. B. eine Variante der Körpersperre, die dem Anvieren des Benutzers mit einer elastischen Verzögerung folgt, während der Benutzer den Kopf dreht.
* Platzieren Sie das Hologramm in einer komfortablen Ansichtsentfernung, die in der Regel etwa 1 bis 2 Meter vom Kopf entfernt ist.
* Lassen Sie zu, dass Elemente driften, wenn sie sich kontinuierlich im holografischen Rahmen bewegen müssen, oder verschieben Sie Ihren Inhalt auf eine Seite der Anzeige, wenn der Benutzer seinen Standpunkt ändert. Weitere Informationen finden Sie unter der [Artilce für](../design/billboarding-and-tag-along.md) Diessing und Tag-Along.

**Platzieren von Hologrammen in der optimalen Zone – zwischen 1,25 m und 5 m**

Zwei Meter sind die optimale Anzeigedistanz. Die Benutzererfahrung wird abgestuft, wenn Sie näher als 1 Meter kommen. Bei Entfernungen von weniger als 1 Meter sind Hologramme, die sich regelmäßig in die Tiefe bewegen, wahrscheinlicher problematisch als stille Hologramme. Ziehen Sie in Betracht, Ihre Inhalte ordnungsgemäß zu beschneiden oder zu verblieben, wenn sie zu nah bei ihnen sind, sodass Sie den Benutzer nicht auf eine benutzerfreundliche Anzeigeerfahrung hindeterminieren.

![Optimaler Abstand zum Platzieren von Hologrammen vom Benutzer.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Ein Hologramm interagiert mit Ihnen und Ihrer Welt.

Hologramme geht es nicht nur um Licht und Sound. sie sind auch ein aktiver Teil Ihrer Welt. Anvieren eines Hologramms und einer Geste mit der Hand, und ein Hologramm kann ihnen folgen. Geben Sie einen Sprachbefehl ein, und das Hologramm kann antworten.

![Gruppe von Behördenmitarbeitern, die Microsoft HoloLens 2 verwenden, um an einem Projekt für die Entwicklung eines Windfarms zusammenzuarbeiten](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Hologramme ermöglichen persönliche Interaktionen, die an anderer Stelle nicht möglich sind. Da der HoloLens weiß, wo er sich auf der Welt befindet, kann ein holografisches Zeichen Sie direkt in den Augen betrachten und eine Konversation mit Ihnen beginnen.

Ein Hologramm kann auch mit Ihrer Umgebung interagieren. Beispielsweise können Sie eine holografische Bouncingkugel über einer Tabelle platzieren. Wenn Sie dann in der Luft [tippen,](../design/gaze-and-commit.md#composite-gestures)beobachten Sie, wie die Kugel springt, und klingt, wenn sie auf die Tabelle trifft.

Hologramme können auch von realen Objekten verblendet werden. Beispielsweise kann ein holografisches Zeichen aus dem Sichtfeld heraus durch eine Tür und hinter einer Wand gehen.

**Tipps integration von Hologrammen und der realen Welt**

* Durch die Ausrichtung an zierlichen Regeln lassen sich Hologramme leichter miteinander in Beziehung bringen und sind leichter verständlich. Beispiel: Platzieren Sie einen holografischen Hund auf dem Boden & eine Vase auf der Tabelle, anstatt sie im Raum gleiten zu lassen.
* Viele Designer haben festgestellt, dass sie besser beholbare Hologramme integrieren können, indem sie einen "negativen Schatten" auf der Oberfläche erstellen, auf der sich das Hologramm befindet. Dazu wird ein weicher Lichtschein auf dem Boden um das Hologramm erstellt und dann der "Schatten" vom Licht subtrahiert. Der weiche Lichtschein lässt sich in das Licht aus der realen Welt integrieren. Der Schatten wird verwendet, um das Hologramm in der Umgebung zu erden.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>Ein Hologramm ist das, was <br>Sie können sich eintraumen.<br>
        Als holografischer Entwickler haben Sie die Kraft, Ihre Kreativität aus 2D-Bildschirmen heraus und in die Welt um Sie herum zu brechen.<br><br>
        Was erstellen *Sie?*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Holografische Imaginärwelt im Zimmer](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>Nächster Erkundungsprüfpunkt

Sie sind auf dem [Weg zur](get-started-with-mr.md) Ermittlung, den wir festgelegt haben, und erkunden die Grundlagen Mixed Reality. Von hier aus können Sie mit dem nächsten grundlegenden Thema fortfahren: 

> [!div class="nextstepaction"]
> [Erweitern Ihres Entwurfsprozesses](case-study-expanding-the-design-process-for-mixed-reality.md)