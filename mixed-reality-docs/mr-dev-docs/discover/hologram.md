---
title: Was ist ein Hologramm?
description: Hololens ermöglicht Ihnen das Anzeigen und interagieren mit dreidimensionalen holograms, Objekten aus Licht und Sound, die auf der ganzen Welt angezeigt werden.
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hololens, holograms, Design, Interaktion, Mixed Reality-Headset, Windows Mixed Reality-Headset, was ist die erweiterte Realität
ms.openlocfilehash: cc6b4a4838e7a275b1ef3a45e54c4b894a04b9c2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583345"
---
# <a name="what-is-a-hologram"></a>Was ist ein Hologramm?

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


Hololens ermöglicht das Erstellen von **holograms**, bei denen es sich um Objekte aus Licht und Sound handelt, die auf der ganzen Welt wie echte Objekte angezeigt werden. Holograms reagieren auf Ihre [Blicke](../design/gaze-and-commit.md), [Gesten](../design/gaze-and-commit.md#composite-gestures)und [Sprachbefehle](../design/voice-input.md). Sie können sogar mit [realen Oberflächen](../design/spatial-mapping.md) für Sie interagieren. Mit Hologrammen können Sie digitale Objekte erstellen, die Teil Ihrer Welt sind.

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
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

## <a name="a-hologram-is-made-of-light-and-sound"></a>Ein – Hologramm besteht aus Licht und Sound.

Die Hologramme, die von [hololens](../develop/platform-capabilities-and-apis/rendering.md) gerendert werden, werden im Holographic-Frame direkt vor den Augen des Benutzers angezeigt. Holograms können ihrer Welt ein Licht hinzufügen, was bedeutet, dass Sie sowohl das Licht aus der Anzeige als auch das Licht aus Ihrer Umgebung sehen. Hololens entfernt das Licht nicht aus den Augen, sodass holograms nicht mit der Farbe schwarz gerendert werden können. Der schwarze Inhalt wird stattdessen als transparent angezeigt.

Holograms können viele verschiedene Erscheinungsformen und Verhaltensweisen aufweisen. Einige sind realistisch und solide, andere sind cartoonhaften und ethereal. Sie können holograms verwenden, um Features in Ihrer Umgebung hervorzuheben oder als Elemente in der Benutzeroberfläche Ihrer APP zu verwenden.

![Hände Bearbeitung eines holograms](images/hologram-hands-940px.jpg)

Holograms können auch [Sounds](../design/spatial-sound.md)erstellen, die von einer bestimmten Stelle in Ihrer Umgebung ausgehen. Bei hololens stammt der Sound von zwei Referenten, die sich direkt über Ihren Ohren befinden, ohne Sie zu decken. Ähnlich wie bei den-Anzeigen sind die Referenten Additiv und stellen neue Sounds vor, ohne die Klänge in Ihrer Umgebung zu blockieren.

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Ein – Hologramm kann zusammen mit Ihnen in der Welt oder im Tag platziert werden.

Wenn Sie über einen bestimmten Ort für ein Hologram verfügen, können Sie ihn genau an diesem Punkt in der Welt [platzieren](../design/coordinate-systems.md) . Wenn Sie das Hologramm durchlaufen, wird es auf der ganzen Welt stabil angezeigt. Wenn Sie ein [räumliches Anker](../design/coordinate-systems.md#spatial-anchors) verwenden, um das Objekt anzuheften, kann sich das System sogar merken, wo Sie es verlassen haben, wenn Sie später zurückkehren.

![Zwei Männer, die das Microsoft Dynamics 365-Layout in einem Einzelhandelsbereich verwenden](images/HLS19_retailLayoutHologram_001-940px.jpg)

Einige Hologramme folgen dem Benutzer und positionieren sich auf der Grundlage des Benutzers, unabhängig davon, wo Sie sich befinden. Sie können sich auch ein – Hologramm für eine Weile mit Ihnen anmelden und dann auf der Wand platzieren, sobald Sie zu einem anderen Raum gelangen.

**bewährten Methoden**
* In einigen Szenarien kann es sinnvoll sein, dass holograms im gesamten Szenario leicht erkennbar oder sichtbar sind. Es gibt zwei allgemeine Vorgehensweisen für diese Art der Positionierung. Wir nennen Sie **"Display-Locked"** und **"Body-Locked"**.
   * Anzeige-gesperrte Inhalte sind auf der Geräte Anzeige Positions bedingt "gesperrt". Diese Art von Inhalt ist aus verschiedenen Gründen schwierig, einschließlich des unnatürlichen Gefühls "clingyness", bei dem viele Benutzer frustriert sind und diese "Schütteln" möchten. Im Allgemeinen haben viele Designer besser festgestellt, dass Inhalte mit der Anzeige nicht gesperrt werden.
   * Der Body-Locked-Ansatz ist weitaus besser verzeihbar. Die Text Sperre ist, wenn Sie ein – Hologramm in den Textkörper oder den Blick Vektor des Benutzers im 3D--Raum. Viele Benutzeroberflächen haben ein Verhalten bei der Text Sperrung übernommen, bei dem das – Hologramm "dem Benutzer angezeigt wird, sodass der Benutzer Ihren Text drehen und durch Leerzeichen bewegen kann, ohne das – Hologramm zu verlieren. Durch die Einbindung einer Verzögerung wird die – Hologramm-Bewegung natürlicher. Beispielsweise verwendet eine zentrale Benutzeroberfläche des Windows Holographic-Betriebssystems eine Variation von Body-Locks, die auf den Blick des Benutzers folgt, mit einer sanften, elastischen, elastischen Verzögerung, während der Benutzer den Kopf schaltet.
* Platzieren Sie das – Hologramm in einer bequemen Anzeige Distanz, die in der Regel ungefähr 1-2 Meter von der Kopfzeile entfernt ist.
* Stellen Sie eine Abweichung für Elemente bereit, die sich kontinuierlich im Holographic-Frame befinden müssen, oder animieren Sie den Inhalt auf einer Seite der Anzeige, wenn der Benutzer seine Sicht ändert.

**Platzieren Sie holograms in der optimalen Zone (zwischen 1,25 m und 5 m).**

Zwei Verbrauchseinheiten sind das beste, und die Leistung ist geringer als bei einer Verbrauchseinheit. Bei Entfernungen, die näher als 1 Meter liegen, ist die Wahrscheinlichkeit, dass Hologramme, die regelmäßig ausführlich verschoben werden, eher problematisch als die stationären holograms. Denken Sie daran, ihre Inhalte zu schließen, wenn Sie zu geschlossen werden, damit der Benutzer nicht zu einem unerwarteten Zeitpunkt kommt.

![Optimale Entfernung zum Platzieren von holograms vom Benutzer.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Ein – Hologramm interagiert mit Ihnen und ihrer Welt.

Holograms sind nicht nur für Light und Sound. Sie sind auch ein aktiver Teil ihrer Welt. Sehen Sie sich ein – Hologramm und eine Geste mit der Hand an, und ein – Hologramm kann Ihnen folgen. Übergeben Sie einen Sprachbefehl an ein Hologram, und lassen Sie sich Antworten.

![Gruppe von Behörden, die Microsoft hololens 2 verwenden, um an einem Wind-Farm-Entwicklungsprojekt zusammenzuarbeiten](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Holograms ermöglichen persönliche Interaktionen, die an anderer Stelle nicht möglich sind. Da hololens weiß, wo es sich auf der Welt befindet, kann ein holografisches Zeichen Sie direkt in den Augen sehen, während Sie den Raum durchlaufen.

Ein – Hologramm kann auch mit Ihrer Umgebung interagieren. Sie können z. b. einen Holographic-Sprung-Ball oberhalb einer Tabelle platzieren. Sehen Sie sich dann mit einem [Luftbild](../design/gaze-and-commit.md#composite-gestures)den Ball Sprung an, und machen Sie einen Sound, wenn er auf die Tabelle trifft.

Holograms können auch durch reale Objekte verdeckt werden. Ein holografisches Zeichen kann z. b. durch eine Tür und hinter einer Wand aus der Sicht laufen.

**Tipps für die Integration von holograms und der realen Welt**
* Durch Ausrichten an Gravitations Regeln ist holograms leichter zu identifizieren und besser zu glauben. Beispiel: Platzieren Sie einen Holographic Dog auf der Basis & eine Vase in der Tabelle, anstatt Sie in den Leerraum zu versetzen.
* Viele Designer haben festgestellt, dass Sie besser glaubwürdigere Hologramme integrieren können, indem Sie auf der Oberfläche, auf der sich das – Hologramm befindet, einen "negativen Schatten" erstellen. Dies geschieht, indem ein weicher Glanz am Ende um das Hologramm erstellt und dann der "Schatten" aus dem Glanz subtrahieren wird. Der weiche Glanz ist in das Licht aus der realen Welt integriert, das den Schatten verwendet, um das Hologramm in der Umgebung zu verwenden.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a>Ein – Hologramm ist was. <br>Sie können einen Traum<br>
        Als Holographic-Entwickler haben Sie die Möglichkeit, ihre Kreativität aus 2D-Bildschirmen heraus und auf der ganzen Welt zu unterbrechen.<br><br>
        Was wird *erstellt* ?
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Holographic imaginärer Welt im Wohnraum](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>Nächster Erkundungsprüfpunkt

Wenn Sie der [Erkundungs-Journey](get-started-with-mr.md) folgen, die wir entworfen haben, befinden Sie sich mitten im Kennenlernen der Grundlagen der Mixed Reality. Von hier aus können Sie mit dem nächsten grundlegenden Thema fortfahren: 

> [!div class="nextstepaction"]
> [Erweitern Ihres Entwurfsprozesses](case-study-expanding-the-design-process-for-mixed-reality.md)