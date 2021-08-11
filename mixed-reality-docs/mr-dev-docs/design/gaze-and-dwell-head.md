---
title: Anvisieren mit dem Kopf und Verweilen
description: Beginnen Sie mit einer Übersicht über das Eingabemodell mit dem Kopf und verweilen, einschließlich gängiger Szenarien und Entwurfsprinzipien.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, Anvisiert, Verweilen, Interaktion, Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, ux, Richtlinien, Listenansicht
ms.openlocfilehash: e069b0815f69848b7632cb7b1b85d85f328441b7156ae22ffe097fedc3ed6fc1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223622"
---
# <a name="head-gaze-and-dwell"></a>Anvisieren mit dem Kopf und Verweilen

Wenn die Hände mit Werkzeugen und Gegenständen beschäftigt sind, können Gesten mühsam oder unmöglich sein. Sprachbefehle können wie Gesten in bestimmten Kontexten unzuverlässig sein, z. B. unter zu lauten Umgebungsbedingungen. Darüber hinaus ist der Einsatz der Stimme zur Steuerung von Computern nicht überall üblich, aber seine Bedeutung nimmt sicherlich zu. „Anvisieren mit dem Kopf und Verweilen“ bietet den bekanntesten und einfach zu bedienenden Mechanismus für das freihändige Heads-Up-Arbeiten mit der HoloLens. Darüber hinaus ist das Modell „Anvisieren mit dem Kopf und Verweilen“ unabhängig von Störgeräuschen und Ruheeinschränkungen in der Betriebssystemumgebung zu 100 % zuverlässig.

## <a name="scenarios"></a>Szenarien

Anvieren mit dem Kopf und Verweilen ist hervorragend in Szenarien, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind. Das Feature ist auch nützlich, wenn die Stimme aufgrund von Umgebungs- oder sozialen Einschränkungen nicht zu 100 % zuverlässig oder verfügbar ist. Ein gutes Beispiel ist eine Person, die eine HoloLens trägt, um Referenzinformationen bei der Reparatur eines Fahrzeugmotors zu überlagern. Die Hände sind mit Werkzeugen beschäftigt oder stützen den eigenen Körper, während sich die Person in den Motorraum lehnt. Der Garagenbereich ist laut, mit einem ständigen Klopfen und Knarren der Werkzeuge, wodurch sich die Verwendung von Sprachbefehlen schwierig gestaltet. Das Anvieren und Verweilen mit dem Kopf ermöglicht es der Person, mithilfe der HoloLens sicher durch ihr Referenzmaterial zu navigieren, ohne den Workflow zu unterbrechen. 

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

„Anvisieren mit dem Kopf und Verweilen“ erfordert ein intuitives visuelles Feedback, aber zu viel Feedback kann beklemmend wirken. Das Feedback sollte einem Benutzer helfen, zu wissen, was er als Ziel verwendet, aber es nicht automatisch für seine Absicht auswählt. Beim Lesen von Text, Symbolen und Bezeichnungen müssen Sie benutzern zeitaufwendige Zeit zum Auffangen der Informationen geben, bevor Sie auswählen.
    
**Informationen zur Geschwindigkeit**
    
Verweilinteraktionen können je nach Auswirkung der Navigation unterschiedliche Timer aufweisen – häufiger verwendete Funktionen profitieren in der Regel von schnelleren Füllzeiten, während konsequentere Funktionen von längeren Füllzeiten profitieren können. Bei der Verwendung eines Fülleffekts zur Darstellung dieser Timer können Animationskurven der Füllfarbe das Gefühl schnellerer Füllzeiten positiv beeinflussen. Es sollte erwogen werden, dem Benutzer die Möglichkeit zu bieten, sich für eine schnelle, mittlere und langsame Füllgeschwindigkeit zu entscheiden.
    
**Vermeiden von Jo-Jo-Effekten**

Der Yo-yo-Effekt ist ein unvorhergesehenes Kopfbewegungsmuster, das auftritt, wenn die Inhaltsplatzierung und die Steuerelemente zum Anvucken/Verweilen von Inhalten dazu zwingen, wiederholt nach oben und unten zu suchen. Beispielsweise löst ein Listennavigationsfeld mit der Schaltfläche "Anvieren mit dem Kopf und Verweilen" am unteren Rand eine Schleife von aus: Nach unten bis Verweilen, Nachschlagen der Ergebnisse, Nach unten bis Verweilen usw. Das resultierende Muster ist unwahrscheinlich, daher wird empfohlen, Navigationssteuerelemente an einem zentralen Ort zu platzieren, der weniger Hin und Her erfordert. Die Platzierung von Verweilschaltflächen basierend auf ihren Auswirkungen wird für den Komfort wichtig.
s
<br>

---

## <a name="ux-guidelines-and-best-practices"></a>Richtlinien und bewährte Methoden für die Benutzerumgebung

### <a name="target-sizes"></a>Zielgrößen

Um leicht zugänglich zu sein, müssen Ziele für anvisierten Kopf und Verweilen groß genug sein, um die Empfindlichkeit zu betrachten und den Kopf für die vorgeschriebene Zeit auf dem Ziel stabil zu halten. Es wird eine Mindestzielgröße von 2 Grad empfohlen, um die komfortabelste Erfahrung zu erzielen. 

### <a name="visual-feedback"></a>Visuelles Feedback

Wenn Sie eine radiale Füllung zur Darstellung des Timers für das Verweilen verwenden, beginnen Sie in der Mitte der Schaltfläche. Eine konsistente Reaktion ist weniger irritierend als vollständig unterschiedliche Richtungen auf verschiedenen Schaltflächen. 

  * Diese Regel kann jedoch für richtungsale Interaktionen (z. B. Navigation nach oben/unten/links/rechts usw.) unterbrochen werden. Microsoft Dynamics 365-Handbücher machen z. B. eine Ausnahme, wenn WEITER/ZURÜCK von links nach rechts ausgefüllt werden.
  * Ziehen Sie in Betracht, radiale Füllung von außen in Szenarien wie das Umschalten einer Schaltfläche umzukehren. Das gegenläufige Gefühl beim Drücken einer Schaltfläche ist ein angenehmes visuelles Muster, das beibehalten werden sollte. 

### <a name="progressive-disclosure"></a>Schrittweise Offenlegung

„Schrittweise Offenlegung“ bedeutet, dass nur so viele Details angezeigt werden, wie in den einzelnen Phasen einer Interaktion relevant sind. Für die Verweildauer bedeutet dies, dass das Verweilziel bei hervorhebung (z. B. in einem Listensteuerelement) angezeigt wird.

 ### <a name="oversized-targets"></a>Überdimensionale Ziele

Der Verweilbereich kann größer als das inaktive Symbol sein, um die Verwendung zu erleichtern, wie die Schaltfläche „Zurück“ in Microsoft Dynamics 365-Handbüchern.

### <a name="prevent-flickering-with-delayed-feedback"></a>Vermeiden von Flimmern durch verzögertes Feedback

Verwenden Sie eine kurze Verzögerung, bevor Sie mit dem visuellen Feedback beginnen, um ein Flimmern zu vermeiden, wenn ein Benutzer ein Verweilziel überquert.
* Halten Sie für Schaltflächen, mit der häufig interagiert wurde, die Verzögerung kurz, damit sich die Anwendung reaktiv anfühlt.
* Für Schaltflächen, mit denen selten interagiert wird, kann eine längere Verzögerung sinnvoll sein, um zu vermeiden, dass die Schnittstelle zu twitchy wird.

<br>

---

## <a name="ui-patterns"></a>Muster der Benutzeroberfläche

### <a name="high-frequency-buttons"></a>Schaltflächen mit häufiger Interaktion

:::row:::
    :::column:::
        Schaltflächen mit hoher Frequenz sind Schaltflächen, die häufig in einer Anwendung verwendet werden. Ein gutes Beispiel hierfür sind die Schaltflächen „Weiter“ und „Zurück“ in Microsoft Dynamics 365-Handbüchern.<br>
        <br>
        **Empfehlungen**<br>
  * Schaltflächen mit hoher Frequenz sollten groß sein und beim Anverfolgen mit dem Kopf einfacher zu treffen sein.
  * Halten Sie sich in der Nähe der Augenhöhe, um belastungsbelastend zu vermeiden.<br>
        <br>
*Abbildung: Schaltfläche "Weiter" von Microsoft Dynamics 365 Guides*
    :::column-end:::
        :::column:::
       ![Schaltfläche "Weiter" von Microsoft Dynamics 365 Guides](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Schaltflächen mit seltener Interaktion

Schaltflächen mit niedriger Frequenz sind Schaltflächen, mit denen in der gesamten Anwendung nicht wie regelmäßig interagiert wird. Ein gutes Beispiel könnte eine Schaltfläche für den Zugriff auf das Einstellungsmenü oder eine Schaltfläche zum Löschen der gesamten Arbeit sein.

* Versuchen Sie, diese Schaltflächen von häufig genutzten Pfaden zum Anvisieren mit dem Kopf fernzuhalten, um eine versehentliche Aktivierung zu vermeiden. 

<br>

---

### <a name="confirmations"></a>Bestätigungen

:::row:::
    :::column:::
        Wenn eine Aktion erhebliche Auswirkungen hat, z. B. das Aufladen von Geld, das Löschen von Arbeit oder das Starten eines langen Prozesses, ist es hilfreich, zu bestätigen, dass eine Person eine Schaltfläche auswählen wollte.<br>
        <br>
        **Empfehlungen**<br>
  * Auswahlhervorhebung auf Hauptschaltfläche anzeigen.
  * Verweilziel gleichzeitig mit der Auswahlhervorhebung anzeigen.
  * Verweilziel für die sekundäre Schaltfläche beim Anvisieren mit dem Kopf anzeigen.<br>
        <br>
*Abbildung: Bestätigungsdialogfeld für Microsoft Dynamics 365 Guides*
    :::column-end:::
        :::column:::
       ![Bestätigungsdialogfeld für Microsoft Dynamics 365 Guides](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Umschalter

Umschalter erfordern eine differenzierte Logik, um ordnungsgemäß zu funktionieren. Wenn eine Person auf einer Umschaltfläche verweilt und diese aktiviert, muss sie die Schaltfläche beenden und dann zurückkehren, um die Verweillogik neu zu starten. Es ist wichtig, dass vermeidbare Schaltflächen einen eindeutigen aktiven bzw. inaktiven Zustand aufweisen. 

<br>

---

### <a name="list-views"></a>Listenansichten

:::row:::
    :::column:::
        Listenansichten stellen eine besondere Herausforderung für die Eingabe des Anvschens mit dem Kopf und verweilen dar. Personen können den Inhalt scannen, ohne sich so zu fühlen, als müssten sie die Verweilziele umkippen.<br>
        <br>
**Empfehlungen**<br>
  * Die gesamte Zeilenhervorhebung, wenn mit dem Kopf anviert wird, aber nicht mit dem Verweilen beginnt, es sei denn, das Anviert mit dem Kopf befindet sich auf dem spezifischen Verweilziel.
  * Zeigt das Verweilziel nur an, wenn die Zeile hervorgehoben ist, um visuelles Rauschen zu reduzieren.
  * Seien Sie klar und konsistent mit der Position der Verweilziele.
  * Zeigen Sie nicht alle Verweilziele gleichzeitig an, um sich wiederholende Benutzeroberflächen zu vermeiden.
  * Verwenden Sie das gleiche Muster so oft wie möglich, um vertraute Benutzerfreundlichkeit zu schaffen.<br>
        <br>
*Abbildung: Microsoft Dynamics 365 Guides-Liste*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 Guides-Liste](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>Siehe auch

* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)