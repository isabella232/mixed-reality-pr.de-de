---
title: Typografie
description: Erfahren Sie, wie Sie Text als wichtiges Element für die Bereitstellung von Informationen in Ihrer Mixed Reality-App-Erfahrung entwerfen und implementieren.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, Design, Stil, Schriftart, Typografie, Ui, UX, Text, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens
ms.openlocfilehash: 7df2386f3478c0b0b79d198a3342bc9a9a061f6e5a305baedcd91be9c2f09f04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200285"
---
# <a name="typography"></a>Typografie

![Typografiebeispiel in HoloLens](images/typography-cover.png)<br>


Text ist ein wichtiges Element für die Bereitstellung von Informationen in Ihrer App-Erfahrung. Genau wie bei Typografie auf 2D-Bildschirmen ist das Ziel, klar und lesbar zu sein. Mit dem dreidimensionalen Aspekt von Mixed Reality gibt es die Möglichkeit, den Text und die allgemeine Benutzererfahrung noch stärker zu beeinflussen.

Wenn wir über typ in 3D sprechen, denken wir in der Regel an volumetrischen, volumetrischen 3D-Text. Abgesehen von einigen Logotype-Entwürfen und einigen anderen eingeschränkten Anwendungen wird die Lesbarkeit des Texts tendenziell durch den eingelesenen Text beeinträchtigt. Obwohl wir Erfahrungen für 3D entwerfen, verwenden wir 2D für den Typ, da er besser lesbar und leichter zu lesen ist.

In HoloLens wird typ mit Hologrammen mithilfe von Licht basierend auf dem additiven Farbsystem erstellt. Genau wie andere Hologramme kann der Typ in der tatsächlichen Umgebung platziert werden, in der er von jedem Winkel aus weltweit gesperrt und beobachtet werden kann. Der [Paraparalyxeffekt](https://en.wikipedia.org/wiki/Parallax) zwischen dem Typ und der Umgebung erhöht auch die Tiefe der Erfahrung.

## <a name="typography-in-mixed-reality"></a>Typografie in Mixed Reality

Typografische Regeln in Mixed Reality unterscheiden sich nicht von anderen Regeln. Text muss sowohl in der physischen welt als auch in der virtuellen Welt lesbar und lesbar sein. Text kann sich an einer Wand oder einem physischen Objekt überlagern. Sie kann zusammen mit einer digitalen Benutzeroberfläche unverankert sein. Unabhängig vom Kontext wenden wir die gleichen typografischen Regeln zum Lesen und Erkennen an.

### <a name="create-clear-hierarchy"></a>Erstellen einer klaren Hierarchie

Erstellen Sie Kontrast und Hierarchie mit unterschiedlichen Typgrößen und Gewichtungen. Das Definieren einer Typverlaufs- und -enfolge in der gesamten App-Benutzeroberfläche bietet eine hervorragende Benutzererfahrung mit konsistenter Informationshierarchie.

![Beispiele für Typverlauf](images/typography-ramp-1000px.jpg)<br>
*Definieren Sie Ihre Typverlaufs-App, und befolgen Sie sie während der gesamten App-Befahren.*

### <a name="limit-your-fonts"></a>Einschränken Ihrer Schriftarten

Vermeiden Sie die Verwendung von mehr als zwei verschiedenen Schriftfamilien in einem einzigen Kontext. Zu viele Schriftarten werden die Übereinstimmung und Konsistenz Ihrer Erfahrung und die Nutzung von Informationen erschweren. In HoloLens, da die Informationen über die physische Umgebung überlagert werden, beeinträchtigt die Verwendung zu vieler Schriftschnitte die Benutzererfahrung. Segoe UI ist die Schriftart für alle digitalen Entwürfe von Microsoft. Es wird konsistent in der Windows Mixed Reality verwendet. Sie können die Segoe UI-Schriftartdatei von der [Windows-Toolkitseite herunterladen.](/windows/uwp/design-downloads/)

[Weitere Informationen zur Segoe UI Schriftart](/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Vermeiden von schlanken Schriftgewichtungen

Vermeiden Sie die Verwendung von light- oder semilight-Schriftgraden für Typgrößen unter 42 pt, da dünne vertikale Striche die Lesbarkeit erhöhen und herabsetzen. Moderne Schriftarten mit ausreichender Strichstärke funktionieren gut. Beispielsweise sind "Helvetica" und "Arial" in HoloLens regulären oder fett formatierten Gewichtungen lesbar.

### <a name="color"></a>Color

Da HoloLens hologramme mit einem additiven Lichtsystem erstellt werden, ist weißer Text in der HoloLens äußerst lesbar. Beispiele für weißen Text finden Sie auf der Startmenü und in der App-Leiste. Auch wenn weißer Text ohne hintergrundbildliche Platte auf HoloLens funktioniert, kann ein komplexer physischer Hintergrund das Lesen des Typs erschweren. Wir empfehlen die Verwendung von weißem Text auf einer dunklen oder farbigen Rückseite, um den Fokus des Benutzers zu verbessern und die Ableitung von einem physischen Hintergrund zu minimieren.

<br>


![Wir empfehlen die Verwendung von weißem Text auf einer dunklen oder farbigen Rückseite. ](images/typography-whiteonblack2-1000px.jpg)
 *Beispiele für weißen Text auf einer dunklen oder farbigen Rückseite.*
<br>

Um dunklen Text zu verwenden, sollten Sie eine helle Rückseite verwenden, um ihn lesbar zu machen. In additiven Farbsystemen wird Schwarz als transparent angezeigt. Dies bedeutet, dass der schwarze Text ohne farbiges Hintergrundschild nicht angezeigt wird.

:::row:::
    :::column:::
        ![Beispiele für Weiß auf Schwarz und Schwarz auf weißem Text](images/typography-whiteonblack.png)<br>
        *Beispiele für Weiß auf Schwarz und Schwarz auf weißem Text*<br>
    :::column-end:::
    :::column:::
        ![Beispiele für schwarzen Text in den System-Apps – Store und Einstellungen](images/640px-typography-blackonwhite.jpg)<br>
        *Beispiele für schwarzen Text in den System-Apps – Store und Einstellungen*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>Empfohlener Schriftgrad

Wie Sie erwarten können, sehen Typgrößen, die wir auf einem PC oder tablet-Gerät verwenden (in der Regel zwischen 12 und 32Pt), in einer Entfernung von 2 Metern klein aus. Dies hängt von den Merkmalen der einzelnen Schriftarten ab, aber im Allgemeinen liegen der empfohlene mindeste Anzeigewinkel und die Schrifthöhe für die Lesbarkeit basierend auf unseren Studien zur Benutzerforschung bei etwa 0,35°-0,4°/12,21-13,97 mm. Der Skalierungsfaktor, der auf der Seite [Text in Unity](../develop/unity/text-in-unity.md) eingeführt wurde, beträgt etwa 35-40 pt. 

Für die nahe Interaktion bei 0,45 m (45 cm) sind der Anzeigewinkel und die Höhe der lesbaren Schriftart mindestens 0,4°-0,5° / 3,14–3,9mm. Es ist ungefähr 9-12 pt mit dem Skalierungsfaktor, der in [Text in Unity eingeführt wurde.](../develop/unity/text-in-unity.md)

![Nah- und Ferninteraktionsbereich ](images/typography-distance-1000px.jpg)
 *Inhalt im nah- und fernen Interaktionsbereich*

### <a name="the-minimum-legible-font-size"></a>Der minimale lesbare Schriftgrad

| Entfernung | Betrachtungswinkel | Texthöhe | Schriftgrad** |
|---------|---------|---------|---------|
| 45 cm (Direkter Manipulationsabstand) | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2 m | 0.35°-0.4° | 12,21–13,97mm | 34.63-39.58 pt |

### <a name="the-comfortably-legible-font-size"></a>Der gut lesbare Schriftgrad

| Entfernung | Betrachtungswinkel | Texthöhe | Schriftgrad** |
|---------|---------|---------|---------|
| 45 cm (Direkter Manipulationsabstand) | 0.65°-0.8° | 5,1 bis 6,3 mm | 14.47-17.8 pt |
| 2 m | 0.6°-0.75° | 20,9 bis 26,2 mm | 59.4-74.2 pt |


Segoe UI (die Standardschriftart für Windows) funktioniert in den meisten Fällen gut. Vermeiden Sie die Verwendung von hell- oder halblichten Schriftfamilien in kleiner Größe, da dünne vertikale Striche glühen und die Lesbarkeit herabsetzen. Moderne Schriftarten mit ausreichender Strichstärke funktionieren gut. Beispiel: Helvetica und Arial sehen zierlich aus und sind in HoloLens mit regulären oder fett formatierten Gewichtungen lesbar.

**Ausführlichere Informationen zur Berechnung der Textgröße in Unity finden Sie unter [Text in Unity.](../develop/unity/text-in-unity.md)**

![Anzeigen des ](images/Text_In_Unity_ViewingAngle.jpg)
 *Winkels Anzeigen von Abstand, Winkel und Texthöhe*

<br>

---

## <a name="resources"></a>Ressourcen

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Segoe-Schriftarten](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (ZIP-Datei)<br>
    ### <a name="hololens-fontbr"></a>[HoloLens Schriftart](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (ZIP-Datei)<br>
    <br>
    *Bild: Die HoloLens enthält die Symbolsymbole, die in der Windows Mixed Reality.*
    :::column-end:::
        :::column:::
        ![Die HoloLens enthält die Symbolsymbole, die in der -Windows Mixed Reality](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>Siehe auch

* [Text in Unity](../develop/unity/text-in-unity.md)
* [Farbe, Licht und Materialien](./color-light-and-materials.md)