---
title: Interaktionsfähiges Objekt
description: Erfahren Sie, wie Sie Ereignisse auslösen, visuelle Hinweise bereitstellen und mit Objekten in Ihren Mixed Reality-Anwendungen interagieren.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, Steuerelemente, Interaktion, Hinweise, Ui, ux, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Audio
ms.openlocfilehash: b25c25a6dd48bcc85a556787099734d147d18df2
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110217"
---
# <a name="interactable-object"></a>Interaktionsfähiges Objekt

![Interaktivierbare Objekte](images/UX_Hero_Interactable.jpg)

Eine Schaltfläche ist seit langem eine Metapher zum Auslösen eines Ereignisses in der abstrakten 2D-Welt. In der dreidimensionalen Mixed Reality-Welt müssen wir uns nicht mehr auf diese Abstraktionswelt beschränken. Alles kann ein **interaktionsfähiges Objekt** sein, das ein Ereignis auslöst. Ein interaktives Objekt kann alles sein, von einer Kaffeetasse auf einem Tisch bis hin zu einem Luftblasen in der Luft. In bestimmten Situationen, z. B. auf der Benutzeroberfläche des Dialogfelds, werden weiterhin herkömmliche Schaltflächen verwendet. Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>Wichtige Eigenschaften des interaktivierbaren Objekts

### <a name="visual-cues"></a>Visuelle Hinweise

Visuelle Hinweise sind sensorische Hinweise von Licht, die vom Auge empfangen und während der visuellen Wahrnehmung vom visuellen System verarbeitet werden. Da das visuelle System bei vielen Arten, insbesondere menschen, vorherrschend ist, stellen visuelle Hinweise eine große Informationsquelle für die Wahrnehmung der Welt dar.

Da die holografischen Objekte mit der realen Umgebung in Mixed Reality kombiniert werden, kann es schwierig sein, zu verstehen, mit welchen Objekten Sie interagieren können. Für alle interaktiven Objekte in Ihrer Benutzeroberfläche ist es wichtig, für jeden Eingabezustand differenzierte visuelle Hinweise bereitzustellen. Dies hilft dem Benutzer zu verstehen, welcher Teil Ihrer Benutzeroberfläche interagierbar ist, und macht den Benutzer mithilfe einer konsistenten Interaktionsmethode sicher.

<br>

---

### <a name="far-interactions"></a>Far-Interaktionen

Für alle Objekte, die Der Benutzer mit Anvieren, Handstrahl und Dem Strahl des Bewegungscontrollers interagieren kann, empfiehlt es sich, unterschiedliche visuelle Hinweise für diese drei Eingabezustände zu verwenden:

:::row:::
    :::column:::
       ![Interaktivierbares Objekt mit Standardzustand](images/interactibleobject-states-default.jpg)<br>
       **Standardzustand (Beobachtung)**<br>
        Standardzustand des Objekts im Leerlauf.
    Der Cursor befindet sich nicht im -Objekt. Hand wird nicht erkannt.
    :::column-end:::
    :::column:::
       ![Interaktivierbares Objekt mit Ziel- und Mauszeigerzustand](images/interactibleobject-states-targeted.jpg)<br>
        **Zielzustand (Hover)**<br>
        Wenn das Objekt mit dem Anvisierten cursor, finger proximity oder motion controller es pointer (Zeiger des Bewegungscontrollers) als Ziel verwendet wird.
    Der Cursor befindet sich im -Objekt. Hand wird erkannt, bereit.
    :::column-end:::
    :::column:::
       ![Interaktivierbares Objekt mit gedrücktem Zustand](images/interactibleobject-states-pressed.jpg)<br>
       **Gedrückter Zustand**<br>
        Wenn das Objekt mit einer Geste zum Tippen in die Luft gedrückt wird, drücken Sie den Finger oder die Auswahlschaltfläche des Bewegungscontrollers.
    Der Cursor befindet sich im -Objekt. Die Hand wird erkannt, die Luft wird angetippt.
    :::column-end:::
:::row-end:::

<br>

---

Sie können Techniken wie Hervorhebung oder Skalierung verwenden, um visuelle Hinweise für den Eingabezustand des Benutzers bereitzustellen. In Mixed Reality finden Sie Beispiele für die Visualisierung verschiedener Eingabezustände auf dem Startmenü und mit Schaltflächen auf der App-Leiste. 

Diese Zustände sehen auf einer **holografischen Schaltfläche** wie folgt aus:

:::row:::
    :::column:::
       ![Holografische Schaltfläche im Standardzustand](images/MRTK_InteractableState-default.jpg)<br>
       **Standardzustand (Beobachtung)**<br>
    :::column-end:::
    :::column:::
       ![Holografische Schaltfläche im Ziel- und Mauszeigerzustand](images/MRTK_InteractableState-targeted.jpg)<br>
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

HoloLens 2 unterstützt artikulierte Eingaben zur Handnachverfolgung, mit denen Sie mit Objekten interagieren können. Ohne haptisches Feedback und perfekte Tiefenerkennung kann es schwierig sein zu erkennen, wie weit ihre Hand von einem Objekt entfernt ist oder ob Sie es berühren. Es ist wichtig, genügend visuelle Hinweise bereitzustellen, um den Zustand des Objekts zu kommunizieren, insbesondere den Zustand Ihrer Hände basierend auf diesem Objekt.

Verwenden Sie visuelles Feedback, um die folgenden Zustände zu kommunizieren:
* **Standard (Beobachtung):** Standard-Leerlaufzustand des Objekts.
* **Zeigen** Sie auf : Wenn sich eine Hand in der Nähe eines Hologramms befindet, ändern Sie visuals, um zu kommunizieren, dass die Hand hologrammadressiert ist. 
* **Abstand und Interaktionspunkt:** Wenn sich die Hand einem Hologramm nähert, entwerfen Sie Feedback, um den projizierten Interaktionspunkt zu kommunizieren und wie weit der Finger vom Objekt entfernt ist.
* **Kontakt beginnt:** Ändern von Visuals (Hell, Farbe), um zu kommunizieren, dass eine Berührung aufgetreten ist
* **Verstanden:** Visuals (Hell, Farbe) ändern, wenn das Objekt erfasst wird
* **Kontakt endet:** Visuals ändern (Hell, Farbe), wenn die Berührung beendet wurde

<br>

---

:::row:::
    :::column:::
        ![Zeigen mit dem Mauszeiger (weit)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Zeigen mit dem Mauszeiger (weit)**<br>
        Hervorhebung basierend auf der Nähe der Hand.
    :::column-end:::
    :::column:::
        ![Bewegen des Mauszeigers (nah)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Bewegen des Mauszeigers (nah)**<br>
        Heben Sie Größenänderungen basierend auf dem Abstand zur Hand hervor.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Toucheingabe/Drücken](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Toucheingabe/Drücken**<br>
        Visuelles und Audiofeedback.
    :::column-end:::
    :::column:::
        ![Begreifen](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Begreifen**<br>
        Visuelles und Audiofeedback.
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
        Show effect (Effekt "Welleneffekt anzeigen").
    :::column-end:::
    :::column:::
        ![Tastenkombination](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Presse**<br>
        Verschieben Sie die Vorderseite.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>Der visuelle Hinweis "Ring" auf HoloLens 2<br>
        Auf HoloLens 2 gibt es einen zusätzlichen visuellen Hinweis, der dem Benutzer bei der Wahrnehmung der Tiefe helfen kann. Ein Ring in der Nähe der Fingerspitze wird nach oben angezeigt und herunterskaliert, wenn sich die Fingerspitze dem Objekt nähert. Der Ring konvergiert schließlich zu einem Punkt, wenn der gedrückte Zustand erreicht wird. Dieses visuelle Erscheinungsbild hilft dem Benutzer zu verstehen, wie weit er vom Objekt entfernt ist.<br>
        <br>
        *Videoschleife: Beispiel für visuelles Feedback basierend auf der Nähe zu einem Begrenzungsfeld*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Visuelles Feedback zur Handnähe](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Audiohinweise

Bei direkten Handinteraktionen kann das richtige Audiofeedback die Benutzerfreundlichkeit erheblich verbessern. Verwenden Sie Audiofeedback, um die folgenden Hinweise zu kommunizieren:
* **Kontakt beginnt:** Sound wiedergeben, wenn die Berührung beginnt
* **Kontakt endet:** Sound auf Touch-Ende wiedergeben
* **Greifen beginnt:** Sound wiedergeben, wenn der Grabbing gestartet wird
* **Ende der Nahme:** Sound wiedergeben, wenn die Grabbing-Klammer endet

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Sprachbefehle<br>
        Für alle interaktivierbaren Objekte ist es wichtig, alternative Interaktionsoptionen zu unterstützen. Standardmäßig wird empfohlen, [sprachgesteuerte Befehle](../out-of-scope/voice-design.md) für alle Objekte zu unterstützen, die interaktiv sind. Um die Auffindbarkeit zu verbessern, können Sie auch während des Mauszeigerzustands eine QuickInfo bereitstellen.<br>
        <br>
        *Bild: QuickInfo für den Sprachbefehl*
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

Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass ausreichend Platz für ein Symbol und möglicherweise text vorhanden ist.

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

In **[MRTK können](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Sie das Skript [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) verwenden, um Objekte auf verschiedene Typen von Eingabeinteraktionszuständen reagieren zu lassen. Es unterstützt verschiedene Arten von Designs, mit denen Sie visuelle Zustände definieren können, indem Sie Objekteigenschaften wie Farbe, Größe, Material und Shader steuern.

* [Interaktionsfähig](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) (Schaltfläche)
* [Handinteraktionsbeispiele (Szene)](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

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