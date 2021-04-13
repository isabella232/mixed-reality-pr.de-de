---
title: Cursor
description: Ein Cursor oder Indikator Ihres Ziel Vektor bietet fortlaufendes Feedback für den Benutzer, um zu verstehen, was hololens über seine Absichten versteht.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Hololens (1st Gen), hololens 2, Mixed Reality, Cursors, Zielplattform, Blick, Gesten, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Rays, Input
ms.openlocfilehash: 744e75f4212046b7c237a6c6634a4980e9148b0e
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300085"
---
# <a name="cursors"></a>Cursor

![Cursor](images/UX_Hero_Cursor.jpg)

Ein Cursor liefert Kontinuierliches Feedback, das darauf basiert, dass der Benutzer den aktuellen Fokus an einem bestimmten Zeitpunkt hat. Cursor Feedback beinhaltet, welche Bereiche, holograms oder Punkte in der virtuellen Umgebung auf die Eingabe Antworten. Obwohl es sich bei dem Cursor um eine digitale Darstellung von handelt, in der das Gerät die Aufmerksamkeit des Benutzers versteht, ist dies nicht dasselbe wie das Ermitteln der Absichten des Benutzers. Mit dem Cursor Feedback können Benutzer auch wissen, welche System Antworten erwartet werden. Sie können das Feedback verwenden, um seine Absicht an das Gerät zu senden, was die Benutzer Zuverlässigkeit steigert.

Es gibt drei Arten von Cursorn: **Finger, Ray** und **Head-Gaze**. Diese zeigenden Cursor funktionieren mit unterschiedlichen Eingabe Modalitäten für hololens, hololens 2 und immersive Headsets. Im folgenden finden Sie Anleitungen dazu, welche Art von Cursor für die einzelnen Typen von Headset-und Interaktions Modellen verwendet werden kann. Im Mixed Reality Toolkit (mrtk) haben wir Drag & amp; Drop-cursormodule erstellt, um Sie bei der Erstellung der richtigen Zeige Erfahrung zu unterstützen.

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
        <td>Finger Cursor</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Strahl Cursor</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Cursor Cursor</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Finger Cursor

Der Finger Cursor ist nur auf den hololens 2 verfügbar, um den Interaktionsmodus "[direkte Bearbeitung von Hand](direct-manipulation.md)" zu verbessern. Wir haben Ringe an die Tipps beider Index Finger angehängt, um besser zu verstehen, wo der Finger zeigt. Die Ring Größe basiert auf der Nähe des Fingers und der UI-Oberfläche, die auf einen kleinen Punkt verkleinert wird, wenn der Finger die Benutzeroberfläche berührt. Je näher der Finger, desto kleiner der Ring. <br>

![Finger Cursor](images/finger-cursor.png)<br>
**Visuelle Feedback Zustände von Finger Cursor** 1: der Ring wird auf einen Punkt verkleinert. 2: der Ring richtet sich nach der Oberfläche. 3: der Ring ist senkrecht zum Finger Vektor. 4: kein Ring.

## <a name="ray-cursor"></a>Strahl Cursor

Ray-Cursors werden an das Ende von weit zeigenden Strahlen angehängt, um die Bearbeitung von Objekten zu ermöglichen, die nicht in der Hand reich sind. In immersiven Headsets werden die Strahlen von Bewegungs Controllern abgeraten und mit Punkt Cursorn enden. In hololens 2 wenden wir das geistige Modell dieser Motion Controller-Strahlen und entworfenen Hand Striche an, die aus den Palmen stammen und in ringförmigen Cursorn enden, die mit fingercursorn konsistent sind, die bei direkter Bearbeitung verwendet werden. <br>
:::row:::
    :::column:::
        ![Strahl Cursor Controller](images/ray-cursor-controller.png)<br>
        **Strahl Cursor von Bewegungs Controllern**<br>
    :::column-end:::
    :::column:::
        ![Strahl Cursor Hand](images/ray-cursor-hand.png)<br>
        **Strahl Cursor von Händen**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>Cursor Cursor

Der Head-Gaze-Cursor ist ein Punkt, der an das Ende eines unsichtbaren Kopf Zeigers angefügt wird, der die Position und Drehung des Kopfes verwendet, um zu zeigen. Zum Ausführen von Aktionen wird dieser Zeige Cursor mit verschiedenen Commit-Eingaben gekoppelt, wie z. b. Air Tap, Voice Commands, Dwell und Button Press. In hololens 2 ist die Kopfzeile am besten mit allen Commit-Eingaben gekoppelt, bei denen es sich nicht um Luft tippen handelt, da es zu Interaktions Konflikten zwischen Luft tippen und fern Strahlen kommt. <br>
:::row:::
    :::column:::
        ![Cursor Hand des Kopf Zeigers](images/head-gaze-cursor-hand.png)<br>
        **Cursor Cursor mit Handbewegung**<br>
    :::column-end:::
    :::column:::
        ![Cursor Stimme für Head-Gaze](images/head-gaze-cursor-voice.png)<br>
        **Kopf zeiligen Cursor mit Sprachbefehl**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>Empfehlungen für die Cursor Anpassung

Wenn Sie das Verhalten und den Anschein von Cursor Feedback anpassen möchten, finden Sie hier einige Entwurfs Empfehlungen:

### <a name="cursor-scale"></a>Cursor Skala

* Der Cursor sollte nicht größer sein als die verfügbaren Ziele, sodass Benutzer problemlos mit dem Inhalt interagieren und ihn anzeigen können.
* Abhängig von der Umgebung, die Sie erstellen, ist das Skalieren des Cursors, wie der Benutzer aussieht, auch ein wichtiger Aspekt. Beispielsweise sollte der Cursor nicht zu klein werden, da der Benutzer nicht mehr zu klein aussieht, sodass er verloren geht.
* Beim Skalieren des Cursors sollten Sie eine weiche Animation darauf anwenden, während Sie skaliert wird, um ihr ein organisches Gefühl zu vermitteln.
* Vermeiden Sie das Blockieren von Inhalt. Holograms machen das Erlebnis als unvergesslich, und der Cursor sollte nicht davon entfernt werden.

### <a name="directionless-cursor-shape"></a>Direktionlose Cursor Form

* Obwohl es keine Rechte Cursor Form gibt, empfiehlt es sich, eine direktionale Form wie einen "Tor" zu verwenden. Ein Cursor, der in einer Richtung zeigt (z. b. ein herkömmlicher Pfeilcursor), kann den Benutzer so verwechseln, dass er immer auf diese Weise aussieht.
* Eine Ausnahme besteht darin, dass der Cursor verwendet wird, um dem Benutzer Interaktions Anweisungen mitzuteilen. Wenn z. b. Hologramme im Mixed Reality-Betriebssystem skaliert werden, schließt der Cursor temporär Pfeile ein, die den Benutzer darüber informiert, wie Sie seine Hand verschieben, um das Hologram zu skalieren.

### <a name="look-and-feel"></a>Aussehen und Gefühl

* Ein Ring Diagramm oder ein mit einem Tor gegeformter Cursor funktioniert für viele Anwendungen.
* Wählen Sie eine Farbe und eine Form aus, die die von Ihnen erstellten Funktionen am besten repräsentiert.
* Cursor sind besonders anfällig für die [Trennung von Farben](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).
* Ein kleiner Cursor mit ausgewogener Deckkraft sorgt dafür, dass er informativ ist, ohne die visuelle Hierarchie zu dominieren.
* Sie sollten die Verwendung von Shadowing oder Highlights hinter dem Cursor erkennen, da Sie Inhalte behindern und von der Aufgabe ablendieren können.
* Cursor sollten sich an den Oberflächen in der APP ausrichten und diese umarmen. Benutzer haben das Gefühl, dass Sie sehen können, wo Sie aussehen, aber auch, dass das System von Ihrer Umgebung weiß. Der Cursor im Mixed Reality-Betriebssystem richtet sich z. b. an den Oberflächen der Benutzer Welt und sorgt so für das Bewusstsein der Welt, auch wenn der Benutzer nicht direkt auf ein Hologram zuschaut.
* Das magnetisch Sperren des Cursors für ein interaktives Element, wenn es dem Benutzer nahe liegt, kann das Vertrauen verbessern, dass der Benutzer mit diesem Element interagiert, wenn eine Auswahl Aktion verwendet wird.

### <a name="visual-cues"></a>Visuelle Hinweise

* Wenn Sie sich auf ein einzelnes Hologramm konzentrieren, sollte Ihr Cursor nur dieses – Hologramm ausrichten und die Form ändern, wenn Sie von diesem – Hologramm Weg gehen. Dies kann dem Benutzer vermitteln, dass das – Hologramm handlungsfähig ist und mit ihm interagieren kann.
* Wenn Ihre Anwendung eine räumliche Zuordnung verwendet, könnte der Cursor jede sichtbare Oberfläche ausrichten und umarmen. Dadurch erhalten die Benutzer Feedback, dass hololens und Ihre Anwendung Ihren Speicherplatz sehen können. Dadurch wird die Tatsache verstärkt, dass holograms Real und in unserer Welt sind und die Lücke zwischen Real und Virtual überbrücken.
* Sehen Sie sich an, was der Cursor tun soll, wenn keine holograms oder Oberflächen in der Ansicht vorhanden sind. Eine Möglichkeit besteht darin, den Benutzer in einem vordefinierten Abstand vor dem Benutzer zu platzieren.

### <a name="possible-actions"></a>Mögliche Aktionen

* Der Cursor kann durch verschiedene Symbole dargestellt werden, um mögliche Aktionen zu vermitteln, die ein Hologramm ausführen kann, z. b. Skalierung oder Drehung.
* Fügen Sie dem Cursor nur dann zusätzliche Informationen hinzu, wenn er etwas für den Benutzer bedeutet. Andernfalls bemerken die Benutzer möglicherweise nicht, dass sich der Status ändert, oder Sie werden durch den Cursor verwirrt.

### <a name="input-state"></a>Eingabe Status

* Der Cursor kann verwendet werden, um den Eingabe Zustand oder die Absicht des Benutzers anzuzeigen. Beispielsweise könnte ein Symbol angezeigt werden, das dem Benutzer mitteilt, dass das System seinen Hand Zustand hat und die Anwendung weiß, dass Sie bereit sind, Maßnahmen zu ergreifen.
* Wir könnten auch den Cursor verwenden, um Benutzern anzuzeigen, dass Sprachbefehle vom System über eine Änderung der momentanen Farbe gehört wurden.

* Die folgenden Cursor Zustände können auf unterschiedliche Weise implementiert werden. Sie können diese verschiedenen Zustände implementieren, indem Sie den Cursor wie einen Zustands Automat modellieren. Beispiel:
    * Im Leerlaufzustand wird der Standard Cursor angezeigt.
    * Der Status "bereit" ist, wenn Sie festgestellt haben, dass der Benutzer die Hand hat.
    * Der Interaktions Zustand ist, wenn der Benutzer eine bestimmte Interaktion durch nimmt.
    * Der Status "mögliche Aktionen" oder "Hover" ist, wenn Sie mögliche Aktionen übermitteln, die für ein Hologram ausgeführt werden können.

Sie können diese Zustände auch in einer auf der Skin-Sicht basierenden Weise implementieren, um verschiedene Kunst Ressourcen anzuzeigen, wenn Sie verschiedene Zustände erkennen.

<br>

---

## <a name="going-cursor-free"></a>"Cursor frei"

Das Entwerfen ohne Cursor wird empfohlen, wenn das Eintauchen eine wichtige Komponente einer-Funktion ist und wenn die Zeige Interaktionen (durchschauen und Gesten) keine hohe Genauigkeit erfordern. Das System muss immer noch die normalen Anforderungen eines Cursors erfüllen: die Benutzer erhalten fortlaufend Feedback zum System, das sich auf das Verständnis des Systems hinweist, und unterstützen Sie bei der Kommunikation mit dem System. Dies kann durch andere spürbare Zustandsänderungen erreicht werden.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Cursor im mrtk (Mixed Reality Toolkit) für Unity

Standardmäßig stellt [mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) eine Cursor-vorfab ([DefaultCursor. Prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) bereit, die denselben visuellen Zustand aufweist wie der System Cursor der Shell. Es wird im Eingabeprofil des MRTK unter „Zeiger“ zugewiesen. Sie können diesen Cursor für Ihre Benutzeroberflächen ersetzen/anpassen. Für die Verwendung von Eye-Tracking-Eingaben bietet mrtk auch den "eyegazecursor", der über eine feine Visualisierung verfügt, um die Ablenkung zu minimieren.

* [MRTK – Zeigerprofil](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK – Eingabesystem](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK – Zeiger](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>Weitere Informationen

* [Gesten](gaze-and-commit.md#composite-gestures)
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)