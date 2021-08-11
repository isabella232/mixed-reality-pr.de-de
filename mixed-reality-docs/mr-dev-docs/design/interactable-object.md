---
title: Interaktionsfähiges Objekt
description: Erfahren Sie, wie Sie Ereignisse auslösen, visuelle Hinweise bereitstellen und mit Objekten in Ihren Mixed Reality-Anwendungen interagieren.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, Steuerelemente, Interaktion, Hinweise, Ui, UX, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Audio
ms.openlocfilehash: 9ce682de7e400eba6ffbaccbca34065a1f09966f842cffd6853f3a064f146904
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190751"
---
# <a name="interactable-object"></a>Interaktionsfähiges Objekt

![Interagierbare Objekte](images/UX_Hero_Interactable.jpg)

Eine Schaltfläche ist schon lange eine Symbolmetapher, die zum Auslösen eines Ereignisses in der abstrakten 2D-Welt verwendet wird. In der dreidimensionalen Mixed Reality-Welt müssen wir uns nicht mehr auf diese Welt der Abstraktion beschränken. Alles kann ein **interaktionsfähiges Objekt sein,** das ein Ereignis auslöst. Ein interaktionsfähiges Objekt kann von einer Kaffeetasse auf einem Tisch bis zu einem Sprechblasen in der Luft sein. In bestimmten Fällen, z. B. in der Dialogbenutzeroberfläche, werden weiterhin herkömmliche Schaltflächen verwendet. Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>Wichtige Eigenschaften des interagierbaren Objekts

### <a name="visual-cues"></a>Visuelle Hinweise

Visuelle Hinweise sind sensorische Hinweise vom Licht, die vom Auge empfangen und während der visuellen Wahrnehmung vom visuellen System verarbeitet werden. Da das visuelle System in vielen Arten, insbesondere bei Menschen, dominant ist, stellen visuelle Hinweise eine große Informationsquelle für die Wahrnehmung der Welt dar.

Da die holografischen Objekte mit der realen Umgebung in Mixed Reality kombiniert werden, kann es schwierig sein, zu verstehen, mit welchen Objekten Sie interagieren können. Für alle interagierbaren Objekte in Ihrer Erfahrung ist es wichtig, für jeden Eingabezustand differenzierte visuelle Hinweise zu bieten. Dies hilft dem Benutzer zu verstehen, welcher Teil Ihrer Benutzeroberfläche interagierbar ist, und macht den Benutzer mithilfe einer konsistenten Interaktionsmethode sicher.

<br>

---

### <a name="far-interactions"></a>Ferninteraktionen

Für alle Objekte, die der Benutzer mit dem Anvisieren, dem Handstrahl und dem Ray des Bewegungscontrollers interagieren kann, wird empfohlen, für diese drei Eingabezustände unterschiedliche visuelle Hinweise zu verwenden:

:::row:::
    :::column:::
       ![Interagierbares Objekt mit Standardzustand](images/interactibleobject-states-default.jpg)<br>
       **Standardzustand (Beobachtung)**<br>
        Standard leerer Zustand des Objekts.
    Der Cursor befindet sich nicht auf dem -Objekt. Hand wird nicht erkannt.
    :::column-end:::
    :::column:::
       ![Interagierbares Objekt mit Ziel- und Hoverzustand](images/interactibleobject-states-targeted.jpg)<br>
        **Zielzustand (Hover)**<br>
        Wenn das Objekt mit dem Anvitätscursor, der Fingernähe oder dem Bewegungscontrollerzeiger als Ziel verwendet wird.
    Der Cursor befindet sich auf dem -Objekt. Hand ist erkannt, bereit.
    :::column-end:::
    :::column:::
       ![Interagierbares Objekt mit gedrückter Zustand](images/interactibleobject-states-pressed.jpg)<br>
       **Gedrückter Zustand**<br>
        Wenn das Objekt mit einer Tippbewegung in die Luft gedrückt wird, drücken Sie den Finger, oder drücken Sie die Auswahltaste des Bewegungscontrollers.
    Der Cursor befindet sich auf dem -Objekt. Hand wird erkannt, Luft angetippt.
    :::column-end:::
:::row-end:::

<br>

---

Sie können Techniken wie Hervorhebung oder Skalierung verwenden, um visuelle Hinweise für den Eingabezustand des Benutzers zu bieten. In Mixed Reality finden Sie Beispiele für die Visualisierung verschiedener Eingabezustände auf dem Startmenü und mit App-Leistenschaltflächen. 

Diese Zustände sehen auf einer **holografischen Schaltfläche wie hier aus:**

:::row:::
    :::column:::
       ![Holografische Schaltfläche im Standardzustand](images/MRTK_InteractableState-default.jpg)<br>
       **Standardzustand (Beobachtung)**<br>
    :::column-end:::
    :::column:::
       ![Holografische Schaltfläche im Ziel- und Hoverzustand](images/MRTK_InteractableState-targeted.jpg)<br>
        **Zielzustand (Hover)**<br>
    :::column-end:::
    :::column:::
       ![Holografische Schaltfläche im gedrückten Zustand](images/MRTK_InteractableState-pressed.jpg)<br>
       **Gedrückter Zustand**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Nahinteraktionen (direkt) 

HoloLens 2 unterstützt artikulierte Handtrackingeingaben, mit denen Sie mit Objekten interagieren können. Ohne planloses Feedback und perfekte Tiefenempfinden kann es schwierig sein zu erkennen, wie weit Ihre Hand von einem Objekt entfernt ist oder ob Sie es berühren. Es ist wichtig, genügend visuelle Hinweise zu liefern, um den Zustand des Objekts zu kommunizieren, insbesondere den Zustand Ihrer Hände basierend auf diesem Objekt.

Verwenden Sie visuelles Feedback, um die folgenden Zustände zu kommunizieren:
* **Standard (Beobachtung):** Standardmäßiger Leerlaufzustand des Objekts.
* **Hover:** Wenn sich eine Hand in der Nähe eines Hologramms befindet, ändern Sie visuals, um zu kommunizieren, dass die Hand auf Hologramm zielt. 
* **Abstand und Interaktionspunkt:** Wenn sich die Hand einem Hologramm nähert, entwerfen Sie Feedback, um den projizierten Interaktionspunkt und die Entfernung des Fingers zum Objekt zu kommunizieren.
* **Kontakt beginnt:** Visuelle Elemente (Hell, Farbe) ändern, um zu kommunizieren, dass eine Berührung erfolgt ist
* **Verstanden:** Visuelle Elemente (Licht, Farbe) ändern, wenn das Objekt erfasst wird
* **Kontakt endet:** Visuelle Elemente (Hell, Farbe) ändern, wenn die Berührung beendet wurde

<br>

---

:::row:::
    :::column:::
        ![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Hover (Far)**<br>
        Hervorhebung basierend auf der Nähe der Hand.
    :::column-end:::
    :::column:::
        ![Hover (Near) (Hover (Nah))](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Hover (Near) (Hover (Nah))**<br>
        Hervorheben von Größenänderungen basierend auf dem Abstand zur Hand.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Touch/Drücken](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Touch/Drücken**<br>
        Visuelles Feedback und Audiofeedback.
    :::column-end:::
    :::column:::
        ![Begreifen](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Begreifen**<br>
        Visuelles Feedback und Audiofeedback.
    :::column-end:::
:::row-end:::

<br>

<br>

---

Eine [Schaltfläche auf HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) ist ein Beispiel dafür, wie die verschiedenen Eingabeinteraktionszustände visualisiert werden:

:::row:::
    :::column:::
        ![Standard](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **Standard**<br>
    :::column-end:::
    :::column:::
        ![Darauf zeigen (Hover)](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **Darauf zeigen (Hover)**<br>
        Zeigen Sie einen näherungsbasierten Beleuchtungseffekt an.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Toucheingabe](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **Toucheingabe**<br>
        Anzeigen des Effekts "Show".
    :::column-end:::
    :::column:::
        ![Tastenkombination](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Tastenkombination**<br>
        Verschieben Sie die vordere Platte.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>Der visuelle Hinweis "ring" auf HoloLens 2<br>
        Auf HoloLens 2 gibt es einen zusätzlichen visuellen Hinweis, der den Benutzer bei der Wahrnehmung der Tiefe unterstützen kann. Ein Ring in der Nähe der Fingerspitze wird angezeigt und skaliert herunter, wenn sich die Fingerspitze dem Objekt nähert. Der Ring konvergiert schließlich zu einem Punkt, wenn der gedrückte Zustand erreicht wird. Dieses visuelle Modell hilft dem Benutzer zu verstehen, wie weit er vom Objekt entfernt ist.<br>
        <br>
        *Videoschleife: Beispiel für visuelles Feedback basierend auf der Nähe zu einem Begrenzungsfeld*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Visuelles Feedback zur Nähe](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Audio-Hinweise

Bei direkten Handinteraktionen kann das richtige Audiofeedback die Benutzerfreundlichkeit erheblich verbessern. Verwenden Sie Audiofeedback, um die folgenden Hinweise zu kommunizieren:
* **Kontakt beginnt:** Sound wiedererlangen, wenn die Berührung beginnt
* **Kontakt endet:** Sound auf Touch-End wiedererlangen
* **Grab beginnt:** Sound beim Starten des Greifs wiedererlangen
* **Enden des Greifs:** Sound wiedererlangen, wenn der Greif beendet wird

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Sprachbefehle<br>
        Für alle interagierbaren Objekte ist es wichtig, alternative Interaktionsoptionen zu unterstützen. Standardmäßig wird empfohlen, [Sprachbefehle](../out-of-scope/voice-design.md) für alle Objekte zu unterstützen, die interagierbar sind. Um die Aufmittelbarkeit zu verbessern, können Sie auch eine QuickInfo während des Hoverzustands bereitstellen.<br>
        <br>
        *Abbildung: QuickInfo für den Sprachbefehl*
    :::column-end:::
        :::column:::
       ![Sprachbefehle](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a>Größenempfehlungen

Um sicherzustellen, dass alle interagierbaren Objekte problemlos berührt werden können, empfiehlt es sich, sicherzustellen, dass das interaktionsfähige Objekt basierend auf der Entfernung, die er vom Benutzer platziert wird, eine Mindestgröße erfüllt. Der visuelle Winkel wird häufig in Grad des visuellen Bogens gemessen. Der visuelle Winkel basiert auf dem Abstand zwischen den Augen des Benutzers und dem Objekt und bleibt konstant, während sich die physische Größe des Ziels ändern kann, wenn sich der Abstand zum Benutzer ändert. Um die erforderliche physische Größe eines Objekts basierend auf der Entfernung vom Benutzer zu bestimmen, versuchen Sie, einen visuellen Winkelrechner wie diesen [zu verwenden.](https://elvers.us/perception/visualAngle/)

Im Folgenden finden Sie die Empfehlungen für die Mindestgröße von interaktionsfähigem Inhalt.

### <a name="target-size-for-direct-hand-interaction"></a>Zielgröße für direkte Handinteraktion

| Entfernung | Betrachtungswinkel | Size |
|---------|---------|---------|
| 45 cm  | nicht kleiner als 2° | 1,6 x 1,6 cm |

![Zielgröße für direkte Handinteraktion](images/TargetSizingNear.jpg)<br>
*Zielgröße für direkte Handinteraktion*

<br>

### <a name="target-size-for-buttons"></a>Zielgröße für Schaltflächen

Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass ausreichend Platz für ein Symbol und möglicherweise Text vorhanden ist.

| Entfernung | Mindestgröße |
|---------|---------|
| 45 cm  | 3,2 x 3,2 cm |

![Zielgröße für die Schaltflächen](images/TargetSizingButtons.png)<br>
*Zielgröße für die Schaltflächen*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Zielgröße für Handstrahl- oder Anvizeinteraktion
| Entfernung | Betrachtungswinkel | Size |
|---------|---------|---------|
| 2 m  | nicht kleiner als 1° | 3,5 x 3,5 cm |

![Zielgröße für Handstrahl- oder Anvizeinteraktion](images/TargetSizingFar.jpg)<br>
*Zielgröße für Handstrahl- oder Anvizeinteraktion*

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>Interagierbares Objekt im MRTK (Mixed Reality Toolkit) für Unity

In **[MRTK können](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Sie das Skript [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) verwenden, damit Objekte auf verschiedene Typen von Eingabeinteraktionszuständen reagieren. Es unterstützt verschiedene Arten von Designs, mit denen Sie visuelle Zustände definieren können, indem Sie Objekteigenschaften wie Farbe, Größe, Material und Shader steuern.

* [Interaktionsfähig](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [Schaltfläche](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [Szene mit Beispielen für die Handinteraktion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

Der Standard-Shader von MixedRealityToolkit  bietet verschiedene Optionen, z. B. näherungslicht, das Ihnen hilft, visuelle und Audio-Hinweise zu erstellen.

* [MRTK-Standard-Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a>Siehe auch

* [Cursor](cursors.md)
* [Handstrahl](point-and-commit.md)
* [Schaltfläche](button.md)
* [Interaktionsfähiges Objekt](interactable-object.md)
* [Begrenzungsrahmen und App-Leiste](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Handmenü](hand-menu.md)
* [Nähemenü](near-menu.md)
* [Objektsammlung](object-collection.md)
* [Sprachbefehl](voice-input.md)
* [Tastatur](keyboard.md)
* [QuickInfo](tooltip.md)
* [Filmklappe](slate.md)
* [Schieberegler](slider.md)
* [Shader](shader.md)
* [Billboarding und Tag-along](billboarding-and-tag-along.md)
* [Anzeigen des Fortschritts](progress.md)
* [Oberflächenmagnetismus](surface-magnetism.md)