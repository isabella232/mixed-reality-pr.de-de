---
title: Cursor
description: Ein Cursor oder Indikator ihres Zielvektors gibt dem Benutzer fortlaufendEs Feedback, um zu verstehen, HoloLens absichten versteht.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1. Generation), HoloLens 2, Mixed Reality, Cursor, Ziel, Anvisiert, Gesten, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Lichtstrahl, Eingabe
ms.openlocfilehash: 46e570328451078586109448bce28a7074bc9c2f791c15a284c85b845441fabe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187057"
---
# <a name="cursors"></a>Cursor

![Cursor](images/UX_Hero_Cursor.jpg)

Ein Cursor liefert kontinuierliches Feedback, je nach dem Ort, an dem das Headset der Meinung ist, dass ein Benutzer zu einem bestimmten Zeitpunkt den aktuellen Fokus hat. Cursorfeedback umfasst, welcher Bereich, Hologramm oder Punkt in der virtuellen Umgebung auf Eingaben reagiert. Obwohl der Cursor eine digitale Darstellung der Stelle ist, an der das Gerät die Aufmerksamkeit des Benutzers versteht, ist dies nicht dasselbe wie das Bestimmen der Absichten des Benutzers. Das Cursorfeedback informiert Benutzer auch darüber, welche Systemantworten zu erwarten sind. Sie können das Feedback verwenden, um ihre Absicht an das Gerät zu übermitteln, wodurch das Vertrauen der Benutzer erhöht wird.

Es gibt drei Arten von Cursorn: **Finger, Strahl** und **Anvistik mit dem Kopf.** Diese zeigenden Cursor funktionieren mit verschiedenen Eingabemodalitäten auf HoloLens, HoloLens 2 und immersiven Headsets. Im Folgenden wird erläutert, welcher Cursortyp für die einzelnen Headset- und Interaktionsmodelltypen verwendet werden soll. Im Mixed Reality Toolkit (MRTK) haben wir Drag & Drop-Cursormodule erstellt, mit deren Hilfe Sie die richtige Pointing-Erfahrung erstellen können.

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
        <td>Fingercursor</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Ray cursor (Raycursor)</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Cursor mit dem Kopf</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Fingercursor

Der Fingercursor ist nur auf dem HoloLens 2, um den Interaktionsmodus "Direkte Bearbeitung[mit Händen"](direct-manipulation.md)zu verbessern. Wir haben Ringe an die Spitzen beider Zeigefinger angefügt, um besser zu verstehen, wo der Finger zeigen soll. Die Ringgröße basiert auf der Nähe des Fingers zur Benutzeroberflächenoberfläche, die auf einen kleinen Punkt verkleinert wird, wenn der Finger die Benutzeroberfläche berührt. Je näher der Finger, desto kleiner der Ring. <br>

![Fingercursor](images/finger-cursor.png)<br>
**Visuelle Feedbackzustände des Fingercursors** 1: Der Ring wird auf einen Punkt verkleinert. 2: Der Ring wird an der Oberfläche ausgerichtet. 3: Der Ring ist senkrecht zum Fingervektor. 4: Kein Ring.

## <a name="ray-cursor"></a>Ray cursor (Raycursor)

Ray cursors attach to the end of far pointing ray to allow manipulation of objects that are out-reach. Bei immersiven Headsets werden die Lichtstrahle von Motion-Controllern entfernt und enden mit Punktcursorn. In HoloLens 2 wenden wir das mentale Modell dieser Motion Controller-Lichtstrahle und entworfenen Handlichtlichter an, die von den Handflächen stammen und in ringförmigen Cursorn enden, die mit Fingercursorn konsistent sind, die bei der direkten Manipulation verwendet werden. <br>
:::row:::
    :::column:::
        ![Ray cursor controller (Raycursorcontroller)](images/ray-cursor-controller.png)<br>
        **Raycursor von Motion-Controllern**<br>
    :::column-end:::
    :::column:::
        ![Ray-Cursorhand](images/ray-cursor-hand.png)<br>
        **Ray cursors of hands (Raycursor der Hände)**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>Cursor mit dem Kopf

Der Cursor mit dem Kopf ist ein Punkt, der an das Ende eines unsichtbaren Vektors zum Anvieren mit dem Kopf angefügt wird, der die Position und Drehung des Kopfs verwendet, um zu zeigen. Um Aktionen auszuführen, wird dieser zeigende Cursor mit verschiedenen Commiteingaben gekoppelt, z. B. Tippen in die Luft, Sprachbefehle, Verweildauer und Tastendruck. In HoloLens 2 ist das Anvieren mit dem Kopf am besten mit commit-Eingaben gekoppelt, bei denen es sich nicht um Tippen in die Luft handelt, da es einen Interaktionskonflikt zwischen dem Tippen in die Luft und fernen Handstrahl gibt. <br>
:::row:::
    :::column:::
        ![Cursorhand zum Anvingen mit dem Kopf](images/head-gaze-cursor-hand.png)<br>
        **Cursor mit Dem Kopf mit der Hand**<br>
    :::column-end:::
    :::column:::
        ![Cursorstimme mit dem Kopf](images/head-gaze-cursor-voice.png)<br>
        **Cursor mit Dem Kopf anvauf mit Sprachbefehl**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>Empfehlungen zur Cursoranpassung

Wenn Sie das Verhalten und die Darstellung des Cursorfeedbacks anpassen möchten, finden Sie hier einige Entwurfsempfehlungen:

### <a name="cursor-scale"></a>Cursorskalieren

* Der Cursor sollte nicht größer als die verfügbaren Ziele sein, sodass Benutzer problemlos mit dem Inhalt interagieren und diesen anzeigen können.
* Abhängig von der Umgebung, die Sie erstellen, ist auch das Skalieren des Cursors während des Durchsendens des Benutzers ein wichtiger Aspekt. Wenn der Benutzer z. B. in Ihrer Benutzeroberfläche weiter wegsieht, sollte der Cursor nicht zu klein werden, damit er verloren geht.
* Erwägen Sie beim Skalieren des Cursors, eine weiche Animation darauf zu anwenden, während er skaliert wird, um ihm ein biofarbenes Gefühl zu verleihen.
* Vermeiden Sie das Verhindern von Inhalten. Hologramme die Benutzererfahrung einprägsam machen, und der Cursor sollte sie nicht weg nehmen.

### <a name="directionless-cursor-shape"></a>Richtungslose Cursorform

* Obwohl es keine rechte Cursorform gibt, wird empfohlen, eine richtungslose Form wie einen Torus zu verwenden. Ein Cursor, der in eine bestimmte Richtung zeigt (z. B. ein herkömmlicher Pfeilcursor), kann den Benutzer verwirren, immer so zu suchen.
* Eine Ausnahme ist die Verwendung des Cursors zum Kommunizieren der Interaktionsanweisung an den Benutzer. Wenn Sie beispielsweise Hologramme im Mixed Reality-Betriebssystem skalieren, enthält der Cursor vorübergehend Pfeile, die den Benutzer anweisen, seine Hand zum Skalieren des Hologramms zu bewegen.

### <a name="look-and-feel"></a>Aussehen und Fühl

* Ein donut- oder torusförmiger Cursor funktioniert für viele Anwendungen.
* Wählen Sie eine Farbe und Form aus, die die von Ihnen erstellten Erfahrungen am besten darstellt.
* Cursor sind besonders anfällig für die [Farbtrennung.](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* Ein kleiner Cursor mit ausgeglichener Deckkraft sorgt dafür, dass er informativ bleibt, ohne die visuelle Hierarchie zu überbeenden.
* Seien Sie sich über die Verwendung von Schatten oder Highlights hinter dem Cursor auskennend, da sie den Inhalt verhinderen und von der zu bewältigenden Aufgabe ablenken können.
* Cursor sollten sich an den Oberflächen in Ihrer App ausrichten und sie besingen. Benutzer werden das Gefühl haben, dass das System sehen kann, wo sie suchen, aber auch, dass das System seine Umgebung kennt. Beispielsweise richtet sich der Cursor im Mixed Reality-Betriebssystem an den Oberflächen der Welt des Benutzers aus und schafft so ein Gefühl des Bewusstseins über die Welt, auch wenn der Benutzer nicht direkt auf ein Hologramm blickt.
* Das magnetisch sperrende Sperren des Cursors auf ein interaktives Element in der Nähe des Benutzers kann dazu beitragen, die Sicherheit zu erhöhen, dass der Benutzer mit diesem Element interagiert, wenn er eine Auswahlaktion verwendet.

### <a name="visual-cues"></a>Visuelle Hinweise

* Wenn Sich Ihre Erfahrung auf ein einzelnes Hologramm konzentriert, sollte der Cursor nur dieses Hologramm ausrichten und darauf ausrichten und die Form ändern, wenn Sie sich von diesem Hologramm wegschauen. Dies kann dem Benutzer vermitteln, dass das Hologramm umsetzbar ist und mit ihm interagieren kann.
* Wenn Ihre Anwendung die räumliche Zuordnung verwendet, kann der Cursor jede angezeigte Oberfläche ausrichten und besingen. Dies gibt Feedback an die Benutzer, HoloLens und Ihre Anwendung ihren Bereich sehen können. Dies verstärkt die Tatsache, dass Hologramme real und in unserer Welt sind, und hilft dabei, die Lücke zwischen real und virtuell zu schließen.
* Sie sollten wissen, was der Cursor tun soll, wenn keine Hologramme oder Oberflächen angezeigt werden. Die Platzierung in einem vordefinierten Abstand vor dem Benutzer ist eine Option.

### <a name="possible-actions"></a>Mögliche Aktionen

* Der Cursor kann durch verschiedene Symbole dargestellt werden, um mögliche Aktionen zu vermitteln, die ein Hologramm ausführen kann, z. B. Skalierung oder Drehung.
* Fügen Sie dem Cursor nur zusätzliche Informationen hinzu, wenn dies für den Benutzer etwas bedeutet. Andernfalls bemerken Benutzer die Statusänderungen möglicherweise nicht oder werden durch den Cursor verwirrend.

### <a name="input-state"></a>Eingabezustand

* Wir können den Cursor verwenden, um den Eingabezustand oder die Absicht des Benutzers anzuzeigen. Wir könnten z. B. ein Symbol anzeigen, das dem Benutzer den Handzustand zeigt und die Anwendung weiß, dass er bereit ist, Maßnahmen zu ergreifen.
* Wir könnten auch den Cursor verwenden, um Benutzern zu zeigen, dass Sprachbefehle vom System durch eine momentäre Farbänderung gehört wurden.

* Die folgenden Cursorzustände können auf unterschiedliche Weise implementiert werden. Sie können diese verschiedenen Zustände implementieren, indem Sie den Cursor wie einen Zustandscomputer modellieren. Beispiel:
    * Im Leerlaufzustand wird der Standardcursor angezeigt.
    * Der Status Bereit ist , wenn Sie die Hand des Benutzers an der bereiten Position erkannt haben.
    * Der Interaktionszustand ist, wenn der Benutzer eine bestimmte Interaktion vor sich hat.
    * Mögliche Aktionen status or hover state ist, wenn Sie mögliche Aktionen vermitteln, die auf einem Hologramm ausgeführt werden können.

Sie können diese Zustände auch skin-fähig implementieren, um unterschiedliche Artefakte anzuzeigen, wenn Sie unterschiedliche Zustände erkennen.

<br>

---

## <a name="going-cursor-free"></a>Wird "cursorfrei"

Das Entwerfen ohne Cursor wird empfohlen, wenn das Gefühl der Immersion eine wichtige Komponente einer Erfahrung ist und wenn das Zeigen von Interaktionen (durch Anvieren und Gesten) keine hohe Genauigkeit erfordert. Das System muss weiterhin die normalen Anforderungen eines Cursors erfüllen: benutzern kontinuierliches Feedback zum Systemverständnis ihrer Punkte zu geben und sie bei der Kommunikation ihrer Absichten mit dem System zu unterstützen. Dies kann durch andere spürbare Zustandsänderungen erreicht werden.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Cursor im MRTK (Mixed Reality Toolkit) für Unity

Standardmäßig stellt [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) ein Cursor-Prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) mit dem gleichen visuellen Zustand wie der Systemcursor der Shell zurVerfüge. Es wird im Eingabeprofil des MRTK unter „Zeiger“ zugewiesen. Sie können diesen Cursor für Ihre Benutzererfahrung ersetzen bzw. anpassen. Für die Erfahrung mit Eyetrackingeingaben bietet MRTK auch Eye EyeCursor, das über ein subtiles Visuelles verfügt, um die Ableitung zu minimieren.

* [MRTK – Zeigerprofil](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK – Eingabesystem](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK – Zeiger](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>Weitere Informationen

* [Gesten](gaze-and-commit.md#composite-gestures)
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)