---
title: Anvisieren mit dem Kopf und Verweilen
description: Beginnen Sie mit einer Übersicht über das Head-and-Dwell-Eingabe Modell, einschließlich gängiger Szenarien und Entwurfs Prinzipien.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Gemischte Realität, Blick, wohnen, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, UX, Richtlinien, Listenansicht
ms.openlocfilehash: e70536b7247153979b8650ba1f5bcbe1a7cd08af
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582203"
---
# <a name="head-gaze-and-dwell"></a>Anvisieren mit dem Kopf und Verweilen

Wenn die Hände mit Werkzeugen und Gegenständen beschäftigt sind, können Gesten mühsam oder unmöglich sein. Sprachbefehle können wie Gesten in bestimmten Kontexten unzuverlässig sein, z. B. unter zu lauten Umgebungsbedingungen. Darüber hinaus ist der Einsatz der Stimme zur Steuerung von Computern nicht überall üblich, aber seine Bedeutung nimmt sicherlich zu. „Anvisieren mit dem Kopf und Verweilen“ bietet den bekanntesten und einfach zu bedienenden Mechanismus für das freihändige Heads-Up-Arbeiten mit der HoloLens. Darüber hinaus ist das Modell „Anvisieren mit dem Kopf und Verweilen“ unabhängig von Störgeräuschen und Ruheeinschränkungen in der Betriebssystemumgebung zu 100 % zuverlässig.

## <a name="scenarios"></a>Szenarien

In Szenarien, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind, eignet sich der Kopf-und die Ansprechpartner hervorragend. Die Funktion ist auch nützlich, wenn die Stimme aufgrund von Umwelt-oder sozialen Einschränkungen nicht 100% zuverlässig ist oder nicht verfügbar ist. Ein gutes Beispiel ist eine Person, die eine HoloLens trägt, um Referenzinformationen bei der Reparatur eines Fahrzeugmotors zu überlagern. Die Hände sind mit Werkzeugen beschäftigt oder stützen den eigenen Körper, während sich die Person in den Motorraum lehnt. Der Garagenbereich ist laut, mit einem ständigen Klopfen und Knarren der Werkzeuge, wodurch sich die Verwendung von Sprachbefehlen schwierig gestaltet. In der Kopfzeile und im Leben kann die Person, die die hololens verwendet, sicher in Ihrem Referenzmaterial navigieren, ohne den Workflow zu unterbrechen. 

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Eingabemodell</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Anvisieren mit dem Kopf und Verweilen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
    </tr>
</table>


## <a name="design-principles"></a>Entwurfsprinzipien

**Vermeiden Sie „Anvisieren als Waffe“**

„Anvisieren mit dem Kopf und Verweilen“ erfordert ein intuitives visuelles Feedback, aber zu viel Feedback kann beklemmend wirken. Das Feedback sollte einem Benutzer helfen, seine Zielsetzungen zu erkennen, ihn aber nicht automatisch gegen seine Absicht auszuwählen. Beim Lesen von Text, Symbolen und Bezeichnungen müssen Sie den Benutzern Zeit zum Aufnehmen der Informationen geben, bevor Sie diese auswählen.
    
**Informationen zur Geschwindigkeit**
    
Verweilinteraktionen können je nach Auswirkung der Navigation unterschiedliche Timer aufweisen – häufiger verwendete Funktionen profitieren in der Regel von schnelleren Füllzeiten, während konsequentere Funktionen von längeren Füllzeiten profitieren können. Bei der Verwendung eines Fülleffekts zur Darstellung dieser Timer können Animationskurven der Füllfarbe das Gefühl schnellerer Füllzeiten positiv beeinflussen. Es sollte erwogen werden, dem Benutzer die Möglichkeit zu bieten, sich für eine schnelle, mittlere und langsame Füllgeschwindigkeit zu entscheiden.
    
**Vermeiden von Jo-Jo-Effekten**

Der "Yo-Yo"-Effekt ist ein unangenehmes Kopf Verschiebungs Muster, das auftritt, wenn die Steuerelemente "Content Placement" und "Head-Do/Dwell" Benutzer immer wieder nach oben und unten suchen Beispielsweise wird in einem Listen Navigationsbereich mit der Schaltfläche "Kopf-und Weitergabe" am unteren Rand eine Schleife von "-Look down" angezeigt, um zu leben, nach Ergebnissen zu suchen, zu verweilen usw. Das resultierende Muster ist nicht sehr unbequem. Daher empfiehlt es sich, Navigations Steuerelemente an einem zentralisierten Speicherort zu platzieren, der weniger hin und her erfordert. Die Platzierung von Schaltflächen, die auf Ihren Effekten basieren, wird für den Komfort wichtig.
s
<br>

---

## <a name="ux-guidelines-and-best-practices"></a>Richtlinien und bewährte Methoden für die Benutzerumgebung

### <a name="target-sizes"></a>Zielgrößen

Um auf einfache Weise zugänglich zu sein, müssen die Haupt-und zielziele groß genug sein, um sich bequem anzusehen, und einen der Kopf-und Endwerte für den vorgesehenen Zeitpunkt auf dem Ziel halten. Wir empfehlen eine minimale Zielgröße von 2 Grad, um die komfortablere Leistung zu erzielen. 

### <a name="visual-feedback"></a>Visuelles Feedback

Wenn Sie eine radiale Füllung zur Darstellung des Timers für das Verweilen verwenden, beginnen Sie in der Mitte der Schaltfläche. Eine konsistente Reaktion ist weniger irritierend als vollständig unterschiedliche Richtungen auf verschiedenen Schaltflächen. 

  * Diese Regel kann jedoch für direktionale Interaktionen (z. b. Navigations nach oben/unten/links/rechts usw.) getrennt werden. Microsoft Dynamics 365-Handbücher machen z. B. eine Ausnahme, wenn WEITER/ZURÜCK von links nach rechts ausgefüllt werden.
  * Denken Sie daran, radiale Füllflächen von außen zu umschließen, für Szenarien wie das Umschalten auf eine Schaltfläche. Das gegenläufige Gefühl beim Drücken einer Schaltfläche ist ein angenehmes visuelles Muster, das beibehalten werden sollte. 

### <a name="progressive-disclosure"></a>Schrittweise Offenlegung

„Schrittweise Offenlegung“ bedeutet, dass nur so viele Details angezeigt werden, wie in den einzelnen Phasen einer Interaktion relevant sind. Für "Dwell" bedeutet dies, dass das "Dwell"-Ziel bei der Hervorhebung (z. b. in einem Listen Steuerelement) offen

 ### <a name="oversized-targets"></a>Überdimensionale Ziele

Der Verweilbereich kann größer als das inaktive Symbol sein, um die Verwendung zu erleichtern, wie die Schaltfläche „Zurück“ in Microsoft Dynamics 365-Handbüchern.

### <a name="prevent-flickering-with-delayed-feedback"></a>Vermeiden von Flimmern durch verzögertes Feedback

Verwenden Sie eine kurze Verzögerung, bevor Sie mit dem visuellen Feedback beginnen, um ein Flimmern zu vermeiden, wenn ein Benutzer ein Verweilziel überquert.
* Halten Sie für Schaltflächen, mit denen häufig interagiert wird, die Verzögerung kurz, damit die Anwendung reaktiv ist.
* Für Schaltflächen, die nur selten behandelt werden, kann eine längere Verzögerung sinnvoll sein, um die Schnittstelle zu vermeiden, die twitlapp ist.

<br>

---

## <a name="ui-patterns"></a>Muster der Benutzeroberfläche

### <a name="high-frequency-buttons"></a>Schaltflächen mit häufiger Interaktion

:::row:::
    :::column:::
        Schaltflächen mit hoher Frequenz sind Schaltflächen, die in der Regel in einer Anwendung verwendet werden. Ein gutes Beispiel hierfür sind die Schaltflächen „Weiter“ und „Zurück“ in Microsoft Dynamics 365-Handbüchern.<br>
        <br>
        **Empfehlungen**<br>
  * Die Schaltflächen mit hoher Frequenz sollten groß sein, und es ist einfacher, mit dem Kopf zu erreichen
  * Bleiben Sie in der Nähe der Augen, um eine ergonomische Überlastung zu vermeiden.<br>
        <br>
*Bild: Microsoft Dynamics 365 Guides Schaltfläche "weiter"*
    :::column-end:::
        :::column:::
       ![Schaltfläche "Microsoft Dynamics 365 Guides Next"](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Schaltflächen mit seltener Interaktion

Schaltflächen mit niedriger Frequenz sind Schaltflächen, die in der gesamten Anwendung nicht so häufig behandelt werden. Ein gutes Beispiel könnte eine Schaltfläche für den Zugriff auf das Einstellungsmenü oder eine Schaltfläche zum Löschen der gesamten Arbeit sein.

* Versuchen Sie, diese Schaltflächen von häufig genutzten Pfaden zum Anvisieren mit dem Kopf fernzuhalten, um eine versehentliche Aktivierung zu vermeiden. 

<br>

---

### <a name="confirmations"></a>Bestätigungen

:::row:::
    :::column:::
        Wenn eine Aktion erhebliche Auswirkungen hat, z. b. das Berechnen von Geld, das Löschen von Arbeit oder das Starten eines langen Prozesses, ist es hilfreich, sicherzustellen, dass eine Person eine Schaltfläche auswählen wollte.<br>
        <br>
        **Empfehlungen**<br>
  * Auswahlhervorhebung auf Hauptschaltfläche anzeigen.
  * Verweilziel gleichzeitig mit der Auswahlhervorhebung anzeigen.
  * Verweilziel für die sekundäre Schaltfläche beim Anvisieren mit dem Kopf anzeigen.<br>
        <br>
*Bild: Microsoft Dynamics 365-Führungslinien Bestätigungs Dialogfeld*
    :::column-end:::
        :::column:::
       ![Bestätigungs Dialogfeld für Microsoft Dynamics 365-Anleitungen](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Umschalter

Umschalter erfordern eine differenzierte Logik, um ordnungsgemäß zu funktionieren. Wenn eine Person auf eine UMSCHALT Fläche klickt und Sie aktiviert, muss Sie die Schaltfläche Beenden und dann zurückkehren, um die vergabelogik neu zu starten. Es ist wichtig, dass umschaltbare Schaltflächen den Zustand "aktiv" und "inaktiv" aufweisen. 

<br>

---

### <a name="list-views"></a>Listenansichten

:::row:::
    :::column:::
        Listenansichten stellen eine besondere Herausforderung für Kopf-und eingabeeingaben dar. Personen können den Inhalt scannen, ohne dass Sie sich so fühlen müssen, dass Sie die zielziele kippen müssen.<br>
        <br>
**Empfehlungen**<br>
  * Lassen Sie die ganze Zeile hervorheben, wenn Sie in den Kopf-und Ausgangspunkt steht
  * Zeigt nur das Ziel an, wenn die Zeile hervorgehoben wird, um das visuelle Rauschen zu verringern.
  * Sie sollten klar und konsistent mit der Position von "Dwell Targets" sein.
  * Zeigen Sie nicht alle Ziele auf einmal an, um sich wiederholende Benutzeroberflächen zu vermeiden.
  * Verwenden Sie das gleiche Muster so oft wie möglich, um die Benutzerfreundlichkeit der UX zu schaffen.<br>
        <br>
*Abbildung: Liste der Microsoft Dynamics 365-Leitfäden*
    :::column-end:::
        :::column:::
       ![Liste der Microsoft Dynamics 365-Leitfäden](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>Weitere Informationen

* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)