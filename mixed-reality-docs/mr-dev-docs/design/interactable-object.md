---
title: Interaktionsfähiges Objekt
description: Erfahren Sie, wie Sie Ereignisse Auslösers, visuelle Hinweise bereitstellen und mit Objekten in ihren gemischten Reality-Anwendungen interagieren.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Gemischte Realität, Steuerelemente, Interaktion, Cues, UI, UX, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Audio
ms.openlocfilehash: b93092b597d0267c1169cf823b1a5c1fa03c3c3f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759876"
---
# <a name="interactable-object"></a>Interaktionsfähiges Objekt

![Objekte mit Interaktivität](images/UX_Hero_Interactable.jpg)

Eine Schaltfläche ist lange eine Metapher, die zum Auslösen eines Ereignisses in der 2D-abstrakten Welt verwendet wird. In der dreidimensionalen Mixed Reality-Welt müssen wir nicht mehr auf diese Abstraktions Welt beschränkt werden. Dabei kann es sich um ein Objekt handeln, das ein **Objekt** ist, das ein Ereignis auslöst. Ein Objekt mit Interaktionen kann alles von einem Kaffeebecher in einer Tabelle bis zu einer Sprechblase in Midair sein. Wir verwenden weiterhin herkömmliche Schaltflächen in bestimmten Situationen, z. b. in der Dialogfeld Benutzeroberfläche. Die visuelle Darstellung der Schaltfläche hängt vom Kontext ab.

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>Wichtige Eigenschaften des Interaktionen-Objekts

### <a name="visual-cues"></a>Visuelle Hinweise

Visuelle Hinweise sind Sinnes Hinweise von Licht, die im Auge genommen werden und während der visuellen Wahrnehmung vom visuellen System verarbeitet werden. Da das visuelle System in vielen Arten, insbesondere bei Menschen, dominant ist, stellen visuelle Hinweise eine große Informationsquelle dar, in der die Welt wahrgenommen wird.

Da die Holographic-Objekte in gemischter Realität mit der realen Umgebung kombiniert werden, kann es schwierig sein, die Objekte zu verstehen, mit denen Sie interagieren können. Für alle Objekte, die sich in der Benutzersprache befinden, ist es wichtig, für jeden Eingabe Zustand differenzierte visuelle Hinweise bereitzustellen. Dadurch kann der Benutzer verstehen, welcher Teil ihrer Benutzeroberflächen Interaktionen ist, und der Benutzer wird mit einer konsistenten Interaktions Methode vertraut.

<br>

---

### <a name="far-interactions"></a>Weite Interaktionen

Für alle Objekte, die der Benutzer mit dem Blick auf "Blick", "Hand Strahl" und "Bewegungs Controller" interagieren kann, empfiehlt sich die Verwendung eines anderen visuellen Objekts für diese drei Eingabe Zustände:

:::row:::
    :::column:::
       ![Interactable-Objekt mit Standardzustand](images/interactibleobject-states-default.jpg)<br>
       **Standardzustand (Überwachung)**<br>
        Der standardmäßige Leerlauf Status des Objekts.
    Der Cursor befindet sich nicht im-Objekt. Hand wird nicht erkannt.
    :::column-end:::
    :::column:::
       ![Interactable-Objekt mit Ziel-und Hover-Zustand](images/interactibleobject-states-targeted.jpg)<br>
        **Zielzustand (Hover)**<br>
        , Wenn das Objekt mit dem Cursor Cursor, der fingernähe oder dem Bewegungs Controller Zeiger ausgerichtet ist.
    Der Cursor befindet sich auf dem-Objekt. Hand ist erkannt, bereit.
    :::column-end:::
    :::column:::
       ![Interactable-Objekt mit gedrücktem Zustand](images/interactibleobject-states-pressed.jpg)<br>
       **Gedrückter Zustand**<br>
        Wenn das Objekt mit einer Tastenkombination gedrückt wird, drücken Sie die Schaltfläche "auswählen" von Finger oder Motion Controller.
    Der Cursor befindet sich auf dem-Objekt. Hand ist erkannt, Air tippt.
    :::column-end:::
:::row-end:::

<br>

---

Sie können Techniken wie z. b. Hervorhebung oder Skalierung verwenden, um visuelle Hinweise für den Eingabe Zustand des Benutzers bereitzustellen. In gemischter Realität finden Sie Beispiele für die Visualisierung verschiedener Eingabe Zustände im Startmenü und mit den Schaltflächen der APP-Leiste. 

Diese Zustände sehen auf einer **Holographic-Schaltfläche** wie folgt aus:

:::row:::
    :::column:::
       ![Holographic-Schaltfläche im Standardzustand](images/MRTK_InteractableState-default.jpg)<br>
       **Standardzustand (Überwachung)**<br>
    :::column-end:::
    :::column:::
       ![Holographic-Schaltfläche im Ziel-und Hover-Zustand](images/MRTK_InteractableState-targeted.jpg)<br>
        **Zielzustand (Hover)**<br>
    :::column-end:::
    :::column:::
       ![Holographic-Schaltfläche im gedrückten Zustand](images/MRTK_InteractableState-pressed.jpg)<br>
       **Gedrückter Zustand**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Near Interaktionen (Direct) 

Hololens 2 unterstützt die Eingabe von Handgelenk Nachverfolgung, mit der Sie mit Objekten interagieren können. Ohne haptisches Feedback und eine perfekte Tiefe Wahrnehmung kann es schwierig sein, zu wissen, wie weit die Hand von einem Objekt entfernt ist oder ob Sie es berühren. Es ist wichtig, genügend visuelle Hinweise bereitzustellen, um den Status des Objekts zu übermitteln, insbesondere den Zustand ihrer Hände basierend auf diesem Objekt.

Verwenden Sie visuelles Feedback, um die folgenden Zustände zu kommunizieren:
* **Default (Observation)**: standardmäßiger Leerlauf Status des Objekts.
* **Hover**: Wenn eine Hand sich in der Nähe eines Hologramms befindet, ändern Sie die visuellen Elemente, um zu kommunizieren. 
* **Entfernung und Punkt der Interaktion**: Wenn die Hand ein Hologramm nähert, entwerfen Sie Feedback, um den projizierten Interaktionspunkt zu kommunizieren, und wie weit das Objekt den Finger hat.
* **Kontakt beginnt**: Ändern der visuellen Elemente (hell, Farbe), um zu kommunizieren, dass eine Fingereingabe aufgetreten ist
* **Verstanden**: Ändern von visuellen Elementen (hell, Farbe), wenn das Objekt erfasst wird
* **Kontakt Ende**: Ändern der visuellen Elemente (hell, Farbe), wenn die Fingereingabe beendet wurde

<br>

---

:::row:::
    :::column:::
        ![Hover (weit)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Hover (weit)**<br>
        Hervorhebung basierend auf der Nähe der Hand.
    :::column-end:::
    :::column:::
        ![Hover (in der Nähe)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Hover (in der Nähe)**<br>
        Die Größenänderungen werden basierend auf der Entfernung zur Hand hervorgehoben.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Berühren/drücken](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Berühren/drücken**<br>
        Feedback zu Visual Plus-Audiodaten.
    :::column-end:::
    :::column:::
        ![Gespür](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Gespür**<br>
        Feedback zu Visual Plus-Audiodaten.
    :::column-end:::
:::row-end:::

<br>

<br>

---

Eine [Schaltfläche in hololens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) ist ein Beispiel dafür, wie die verschiedenen Eingabe Interaktions Zustände visualisiert werden:

:::row:::
    :::column:::
        ![Standard](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **Standard**<br>
    :::column-end:::
    :::column:::
        ![Darauf zeigen (Hover)](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **Darauf zeigen (Hover)**<br>
        Zeigen Sie einen near-basierten Beleuchtungs Effekt an.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Toucheingabe](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **Toucheingabe**<br>
        Ripple-Effekt anzeigen.
    :::column-end:::
    :::column:::
        ![Tastenkombination](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Tastenkombination**<br>
        Verschieben Sie die Vorderseite.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>Der visuelle Hinweis "Ring" auf hololens 2<br>
        Auf hololens 2 gibt es einen zusätzlichen visuellen Hinweis, der die Wahrnehmung von tiefen durch den Benutzer unterstützen kann. Ein Ring in der Nähe des fingerabbilds wird angezeigt und herunterskaliert, wenn sich der Fingertipp näher an das Objekt anpasst. Der Ring wird schließlich in einen Punkt konvergiert, wenn der gedrückte Zustand erreicht wird. Diese visuelle Visualisierung unterstützt den Benutzer dabei, zu verstehen, wie weit Sie aus dem-Objekt stammen.<br>
        <br>
        *Video Schleife: Beispiel für visuelles Feedback basierend auf der Nähe eines umgebenden Felds*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Visuelles Feedback in der Nähe](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Audiohinweise

Bei direkter Hand Interaktion kann das richtige Audiofeedback die Benutzer Leistung erheblich verbessern. Verwenden Sie Audiofeedback, um die folgenden Hinweise zu kommunizieren:
* **Kontakt beginnt**: Sound abspielen, wenn der Fingerabdruck beginnt
* **Kontakt** Ende: Sound am Touchscreen abspielen
* **Beginn**: Sound abspielen, wenn der Start beginnt
* Aufnahme **Ende**: Sound wiedergeben, wenn der Griff endet

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Sprachbefehle<br>
        Bei allen Objekt übergreifenden Objekten ist es wichtig, Alternative Interaktions Optionen zu unterstützen. Standardmäßig wird empfohlen, dass [sprach](../out-of-scope/voice-design.md) Befehle für alle Objekte unterstützt werden, die interacbar sind. Um die Auffindbarkeit zu verbessern, können Sie auch eine QuickInfo für den Hover-Zustand bereitstellen.<br>
        <br>
        *Bild: QuickInfo für den Voice-Befehl*
    :::column-end:::
        :::column:::
       ![Sprachbefehl](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a>Größenempfehlungen 

Um sicherzustellen, dass alle austauschbaren Objekte problemlos berührt werden können, sollten Sie sicherstellen, dass die Interaktionen eine minimale Größe basierend auf der Entfernung des Benutzers erfüllt. Der visuelle Winkel wird häufig in Grad des visuellen Bogens gemessen. Der visuelle Winkel basiert auf der Entfernung zwischen den Augen des Benutzers und dem Objekt und bleibt konstant, während sich die physische Größe des Ziels möglicherweise ändert, wenn sich der Abstand vom Benutzer ändert. Um die erforderliche physische Größe eines Objekts basierend auf der Entfernung des Benutzers zu bestimmen, versuchen Sie, einen visuellen Winkel Rechner wie [diesen](https://elvers.us/perception/visualAngle/)zu verwenden.

Im folgenden finden Sie die Empfehlungen für die Mindestgröße von Interaktionen-Inhalten.


### <a name="target-size-for-direct-hand-interaction"></a>Zielgröße für direkte Interaktion

| Abstand | Anzeige Winkel | Size |
|---------|---------|---------|
| 45 cm  | nicht kleiner als 2 ° | 1,6 x 1,6 cm |

![Zielgröße für direkte Interaktion](images/TargetSizingNear.jpg)<br>
*Zielgröße für direkte Interaktion*

<br>

### <a name="target-size-for-buttons"></a>Zielgröße für Schaltflächen

Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass ausreichend Speicherplatz vorhanden ist, um ein Symbol und potenziell einen Text zu enthalten.

| Abstand | Mindestgröße |
|---------|---------|
| 45 cm  | 3,2 x 3,2 cm |

![Zielgröße für die Schaltflächen](images/TargetSizingButtons.png)<br>
*Zielgröße für die Schaltflächen*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Zielgröße für die Hand Strahl-oder Blick Interaktion
| Abstand | Anzeige Winkel | Size |
|---------|---------|---------|
| 2 Mio.  | nicht kleiner als 1 ° | 3,5 x 3,5 cm |

![Zielgröße für die Hand Strahl-oder Blick Interaktion](images/TargetSizingFar.jpg)<br>
*Zielgröße für die Hand Strahl-oder Blick Interaktion*


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>Interactable-Objekt in mrtk (Mixed Reality Toolkit) für Unity

In **[mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie das Skript [**interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) verwenden, damit Objekte auf verschiedene Typen von Eingabe Interaktions Zuständen reagieren. Es unterstützt verschiedene Arten von Designs, mit denen Sie visuelle Zustände definieren können, indem Sie Objekteigenschaften wie z. b. Farbe, Größe, Material und Shader steuern.

* [Interaktionen](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md)
* [Schaltfläche](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md)
* [Beispiel Szenen für Hand Interaktion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

Der Standard-Shader von mixedrealitytoolkit bietet verschiedene Optionen, wie z. b. **near Light** , mit denen Sie visuelle und Audiohinweise erstellen können.
* [Mrtk-Standard-Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/rendering/mrtk-standard-shader.md)


<br>

---


## <a name="see-also"></a>Weitere Informationen

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
