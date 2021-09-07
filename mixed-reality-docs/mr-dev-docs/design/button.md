---
title: Schaltfläche
description: Erfahren Sie, wie Sie eine sofortige Aktion mit Schaltflächen auslösen, die eine der grundlegenden Komponenten von Mixed Reality ist.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality, Steuerelemente, Interaktion, Ui, ux, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Schaltfläche
ms.openlocfilehash: 4b3a9bda852c7a83ee603c3f2340d44f4be89f4d
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2021
ms.locfileid: "122682970"
---
# <a name="button"></a>Schaltfläche

![Schaltfläche](images/UX_Hero_Button.jpg)

Eine Schaltfläche ist eines der grundlegenden und wichtigsten Benutzeroberflächenelemente in Mixed Reality. Sie ermöglicht Es Ihren Benutzern, sofortige Aktionen auszulösen. Da es in Mixed Reality kein physisches Feedback gibt, ist es von entscheidender Bedeutung, genügend visuelles und Audiofeedback zu geben, um das Vertrauen des Benutzers in die Interaktion zu erhöhen. 

In HoloLens 2-Schaltflächendesign haben wir basierend auf vielen Designiterationen, Prototypen und Benutzerforschungsstudien mehrere visuelle Bezahlbarkeiten und Audioinformationen integriert, die die Tiefenempfinden und Interaktion des Benutzers in leerem Raum unterstützen. 

## <a name="visual-affordances"></a>Visuelles Bietet

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWJHgW]


:::row:::
    :::column:::
       ![Schaltfläche mit angezeigter Näherungslichteffekt](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **Näherungslicht**<br>
    :::column-end:::
    :::column:::
       ![Ausgewählte Schaltfläche mit fokuss hervorhebungseffekt](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **Hervorhebung des Fokus**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Die Schaltfläche wird gedrückt, und der Komprimierungseffekt wird angezeigt.](images/UX_Button_Affordance_Compression.jpg)<br>
       **Komprimieren von Gittern**<br>
    :::column-end:::
    :::column:::
       ![Schaltfläche, die mit angezeigter Triggerimpressung gedrückt wird](images/UX_Button_Affordance_Pulse.jpg)<br>
        **Pulse on trigger**<br>
    :::column-end:::
:::row-end:::

<br>

## <a name="audio-cues"></a>Audio-Hinweise

Richtiges Audiofeedback kann die Benutzerfreundlichkeit erheblich verbessern. die HoloLens 2-Schaltfläche bietet Audiofeedback, um die folgenden Hinweise zu kommunizieren:
* **Kontakt beginnt:** Sound wiederentspricht, wenn die Berührung beginnt (Nahinteraktion)
* **Kontaktenden:** Sound bei Touch-End wiedererlangen (Nahinteraktion)
* **Zusammendrnung beginnt:** Sound bei zusammendrungener Auswahl wiedererlangen (Ferninteraktion mit Anvisiert oder Lichtstrahl)
* **Zusammendringen:** Sound beim Zusammendringen wiedererlangen (Ferninteraktion mit Anvisiert oder Lichtstrahl)

<br>

---

:::row:::
    :::column:::
        ## <a name="voice-commandingbr"></a>Sprachbefehle<br>
        Für alle Schaltflächen in Mixed Reality ist es wichtig, alternative Interaktionsoptionen zu unterstützen. Standardmäßig wird empfohlen, Sprachbefehle für alle Schaltflächen zu unterstützen. Im HoloLens 2 Schaltflächendesigns stellen wir eine QuickInfo während des Hoverzustands zur Verfügung, um die Aufmittelbarkeit zu verbessern.
    :::column-end:::
        :::column:::
       ![Spracheingabe](images/UX_Hero_VoiceCommand.jpg)<br>
        *Abbildung: QuickInfo für den Sprachbefehl*
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a>Größenempfehlungen

Um sicherzustellen, dass alle interagierbaren Objekte problemlos berührt werden können, empfiehlt es sich, sicherzustellen, dass das interaktionsfähige Objekt basierend auf der Entfernung, die er vom Benutzer platziert wird, eine Mindestgröße erfüllt. Der visuelle Winkel wird häufig in Grad des visuellen Bogens gemessen. Der visuelle Winkel basiert auf dem Abstand zwischen den Augen des Benutzers und dem Objekt und bleibt konstant, während sich die physische Größe des Ziels ändern kann, wenn sich der Abstand zum Benutzer ändert. Um die erforderliche physische Größe eines Objekts basierend auf der Entfernung vom Benutzer zu bestimmen, versuchen Sie, einen visuellen Winkelrechner wie diesen [zu verwenden.](https://elvers.us/perception/visualAngle/)

Im Folgenden finden Sie die Empfehlungen für die Mindestgröße von interaktionsfähigem Inhalt.

### <a name="target-size-for-direct-hand-interaction"></a>Zielgröße für direkte Handinteraktion

| Distance | Betrachtungswinkel | Size |
|---------|---------|---------|
| 45 cm  | nicht kleiner als 2° | 1,6 x 1,6 cm |

![Zielgröße für direkte Handinteraktion](images/TargetSizingNear.jpg)<br>
*Zielgröße für direkte Handinteraktion*

<br>

### <a name="target-size-for-buttons"></a>Zielgröße für Schaltflächen

Beim Erstellen von Schaltflächen für die direkte Interaktion empfehlen wir eine größere Mindestgröße von 3,2 x 3,2 cm, um sicherzustellen, dass ausreichend Platz für ein Symbol und möglicherweise text vorhanden ist.

| Distance | Mindestgröße |
|---------|---------|
| 45 cm  | 3,2 x 3,2 cm |

![Zielgröße für die Schaltflächen](images/TargetSizingButtons.png)<br>
*Zielgröße für die Schaltflächen*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Zielgröße für Handstrahl- oder Anvizeinteraktion
| Distance | Betrachtungswinkel | Size |
|---------|---------|---------|
| 2 m  | nicht kleiner als 1° | 3,5 x 3,5 cm |

![Zielgröße für Handstrahl- oder Anvizeinteraktion](images/TargetSizingFar.jpg)<br>
*Zielgröße für Handstrahl- oder Anvizeinteraktion*

<br>

---

## <a name="design-guidelines"></a>Entwurfsrichtlinien

### <a name="avoid-transparent-backplate"></a>Vermeiden einer transparenten Backplate
Beim Entwerfen der Menübenutzeroberfläche mit Schaltflächen wird die Verwendung einer nicht transparenten Hintergrundbausteins empfohlen. Transparente Backplates werden aus den folgenden Gründen nicht empfohlen:
* Die Interaktion mit ist schwierig, da schwer zu verstehen ist, wie tief die Schaltfläche gedrückt werden muss, um das Ereignis auszulösen.
* Lesbarkeitsproblem in einer komplexen physischen Umgebung
* Hologramme, die über die transparente Platte angezeigt werden, kann bei Verwendung mit der Tiefen-LSR-Stabilitätstechnologie ein Effektproblem zeigen.

Weitere [Informationen zu Farboptionen und](designing-content-for-holographic-display.md) Richtlinien für die holografische Anzeige finden Sie unter Entwerfen von Inhalten für die holografische Anzeige.

![Beispiele für transparente ](images/color_transparent_examples.jpg)
 *Benutzeroberflächenbeispiele für eine transparente Ui-Backplate*

<br>

### <a name="use-shared-backplate"></a>Verwenden einer freigegebenen Backplate
Für mehrere Schaltflächen wird empfohlen, anstelle der Backplate einer einzelnen Schaltfläche freigegebene Backplate zu verwenden.

* Reduzieren des visuellen Rauschens und der Komplexität
* Gruppierung löschen  

![Beispiele für freigegebene ](images/Button_Design_SharedBackplate.png
)
 *Backplates Beispiele für die Backplate der freigegebenen Benutzeroberfläche*

<br>

---

## <a name="button-in-mrtk-mixed-reality-toolkit"></a>Schaltfläche im MRTK (Mixed Reality Toolkit)
**[MRTK für Unity und](/windows/mixed-reality/mrtk-unity/)** **[MRTK für Unreal](/windows/mixed-reality/develop/unreal/unreal-mrtk-introduction)** bieten verschiedene Arten von Schaltflächen-Prefabs, einschließlich HoloLens 2 Formatschaltflächen. Die HoloLens 2-Schaltfläche enthält alle visuellen Feedback- und Interaktionsdetails, die auf dieser Seite eingeführt wurden. Indem Sie sie verwenden, können Sie das Ergebnis vieler Designiterationen und Benutzerforschungen nutzen, die unsere Designer, Entwickler und Forscher durchgeführt haben.

Weitere Anweisungen und benutzerdefinierte Beispiele finden Sie unter [MRTK –](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) Schaltfläche.

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