---
title: Sprachbefehle
description: Anvisieren, Gesten und Sprache sind primäre Möglichkeiten zur Interaktion für die HoloLens. Dieser Artikel bietet eine durchdachte Anleitung zum Sprachentwurf.
author: shengkait
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, Interaktion, Sprache
ms.openlocfilehash: 2a988ad50a8b20a256b0d7208187785778447cc08109fbf55d4ae83e820a76ba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225370"
---
# <a name="voice-commanding"></a>Sprachbefehle

Wenn Sie Sprachbefehle verwenden, wird das Anving in der Regel als Zielmechanismus verwendet, sei es als Zeiger ("auswählen") oder um Ihren Befehl an eine Anwendung zu verweisen ("siehe es, sagen Sie es"). Natürlich benötigen einige Sprachbefehle kein Ziel, wie „Zum Startmenü“ oder „Hey Cortana“.


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
        <td>Sprachbefehle</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (mit angeschlossenem Headset)</td>
    </tr>
</table>



## <a name="how-to-use-voice"></a>Verwendung der Spracheingabe

Erwägen Sie, Sprachbefehle zu jeder von Ihnen erstellten Umgebung hinzuzufügen. Sprache ist eine leistungsstarke und praktische Möglichkeit, das System und die Apps zu steuern. Da Benutzer mit einer Vielzahl von Dialekten und Akzenten sprechen, stellt die richtige Auswahl der Schlüsselwörter für die Spracherkennung sicher, dass die Befehle Ihrer Benutzer eindeutig interpretiert werden.

### <a name="best-practices"></a>Bewährte Methoden

Nachfolgend finden Sie einige Methoden aufgeführt, die eine reibungslose Spracherkennung ermöglichen.
* **Präzise Befehle verwenden**: Wählen Sie nach Möglichkeit Schlüsselwörter mit zwei oder mehr Silben aus. Einsilbige Wörter neigen dazu, unterschiedliche Vokallaute zu verwenden, wenn sie von Personen mit unterschiedlichen Akzenten gesprochen werden. Beispiel: "Play video" ist besser als "Play the currently selected video"
* **Verwenden eines einfachen** Vokabulars: Beispiel: "Hinweis anzeigen" ist besser als "Platzhalter anzeigen".
* **Sicherstellen, dass Befehle nicht destruktiv sind**: Stellen Sie sicher, dass alle Aktionen, die von einem Spracherkennungsbefehl ausgeführt werden können, nicht destruktiv sind und leicht rückgängig gemacht werden können, falls eine andere Person, die in der Nähe des Benutzers spricht, versehentlich einen Befehl auslöst.
* **Ähnlich klingende Befehle vermeiden**: Vermeiden Sie es, mehrere Spracherkennungsbefehle zu registrieren, die sehr ähnlich klingen. Beispiel: "Show more" (Mehr anzeigen) und "Show store" (Store anzeigen) können sehr ähnlich klingen.
* **Registrierung der App aufheben, wenn sie nicht verwendet wird**: Wenn sich Ihre Anwendung nicht in einem Zustand befindet, in dem ein bestimmter Sprachbefehl gültig ist, sollten Sie die Registrierung der App aufheben, damit andere Befehle nicht mit diesem verwechselt werden.
* **Mit verschiedenen Akzenten testen**: Testen Sie Ihre App mit Benutzern, die unterschiedliche Akzente verwenden.
* **Konsistenz von Sprachbefehlen beibehalten**: Wenn „Zurück“ zur vorherigen Seite wechselt, übernehmen Sie dieses Verhalten in Ihren Anwendungen.
* **Verwendung von Systembefehlen vermeiden**: Die folgenden Sprachbefehle sind für das System reserviert. Diese sollten nicht von Anwendungen verwendet werden.
   * „Hey Cortana“
   * „Auswählen“

### <a name="select"></a>„Auswählen“

Wenn Sie zu einem beliebigen Zeitpunkt „Auswählen“ sagen, wird das aktiviert, worauf der beim Anvisieren verwendete Cursor zeigt. 

>Hinweis: In HoloLens 2 muss der Anvitätscursor zuerst aufgerufen werden, indem das Wort "select" angegeben wird. Sagen Sie erneut "auswählen", um die Aktivierung zu aktivieren. Um den Anvitätscursor auszublenden, verwenden Sie einfach Ihre Hände, um ein Objekt zu airtapen oder zu berühren. 

### <a name="see-it-say-it"></a>Sehen, sagen

Windows Mixed Reality hat ein „Sehen, sagen“-Sprachmodell eingesetzt, bei dem **Beschriftungen auf Schaltflächen mit den zugehörigen Sprachbefehlen identisch sind**. Da es keine Missverständnisse zwischen Beschriftung und Sprachbefehl gibt, können Benutzer besser verstehen, was sie sagen müssen, um das System zu steuern. Um dies zu verstärken, wird beim Verweilen auf einer Schaltfläche ein **Tipp zum Verweilen** angezeigt, um mitzuteilen, welche Schaltflächen sprachaktiviert sind.


![Sehen, sagen – Beispiel 1](../design/images/voice-seeitsayit1-640px.jpg)

![Sehen, sagen – Beispiel 2](../design/images/voice-seeitsayit2-640px.jpg)<br>
*Beispiele für „Sehen, sagen“*

### <a name="voices-strengths"></a>Vorteile der Spracheingabe

Die Spracheingabe ist eine natürliche Art, unsere Absichten zu kommunizieren. Die Stimme ist  besonders gut für Schnittstellendurchlaufe, da sie Benutzern dabei helfen kann, mehrere Schritte einer Schnittstelle zu durchlaufen (ein Benutzer kann beim Anzeigen einer Webseite "zurück" sagen, anstatt nach oben zu wechseln und in der App auf die Schaltfläche "Zurück" zu klicken). Diese geringe Zeitersparnis hat einen starken **emotionalen** Effekt auf die Wahrnehmung der Benutzererfahrung und bietet ihnen eine geringe Menge an Superleistung. Die Spracheingabe ist auch eine bequeme Eingabemethode, wenn unsere Arme nicht frei sind oder wir **mehrere Aufgaben gleichzeitig** erledigen. Auf Geräten, bei denen die Eingabe auf einer Tastatur schwierig ist, kann das **Sprachdiktat** eine effiziente alternative Möglichkeit zur Eingabe sein. In einigen Fällen, in  denen der Genauigkeitsbereich für Anvität und Gesten begrenzt ist, ist Voice möglicherweise die einzige vertrauenswürdige Eingabemethode eines Benutzers.

**Vorteile der Spracheingabe für den Benutzer**
* Verkürzt den Zeitaufwand – das Endziel sollte effizienter erreicht werden.
* Minimiert den Aufwand – Aufgaben sollten flüssiger und müheloser verlaufen.
* Reduziert die kognitive Belastung – sie ist intuitiv, leicht zu erlernen und zu merken.
* Sie ist sozialverträglich – sie sollte sich in Bezug auf das Verhalten in die gesellschaftlichen Normen einfügen.
* Sie stellt eine Routine dar – die Spracheingabe kann leicht zu einem gewohnheitsmäßigen Verhalten werden.

### <a name="voices-weaknesses"></a>Nachteile der Spracheingabe

Die Spracheingabe weist auch einige Schwächen auf. Eine davon ist die differenzierte Steuerung. (Beispielsweise kann ein Benutzer "lauter" sagen, aber nicht sagen, wie viel. „Etwas“ ist schwer zu quantifizieren. Das Bewegen oder Skalieren von Objekten per Spracheingabe ist ebenfalls schwierig (die Spracheingabe bietet nicht die Genauigkeit bei der Steuerung). Die Spracheingabe kann auch unvollkommen sein. Gelegentlich hört ein Spracheingabesystem einen Befehl falsch oder überhaupt nicht. Die Wiederherstellung nach solchen Fehlern stellt für jede Schnittstelle eine Herausforderung dar. Schließlich ist die Spracheingabe an öffentlichen Orten möglicherweise nicht gesellschaftsfähig. Es gibt einige Dinge, die Benutzer nicht sagen können oder sollten. Diese Hindernisse ermöglichen es, die Spracherkennung dafür zu nutzen, wofür sie am besten geeignet ist.

### <a name="voice-feedback-states"></a>Statusangaben für Spracherkennungsfeedback

Wenn die Spracherkennung richtig angewendet wird, versteht der Benutzer, **was er sagen kann und er erhält ein eindeutiges Feedback**, das das System **ihn richtig verstanden hat**. Diese beiden Signale geben dem Benutzer das Gefühl, dass er die Spracherkennung als primäre Eingabemethode verwenden kann. Nachfolgend ist in einem Diagramm dargestellt, was mit dem Cursor geschieht, wenn die Spracheingabe erkannt wird und wie dies dem Benutzer vermittelt wird.

![Statusangaben für Spracherkennungsfeedback für Cursor](../design/images/voicefeedbackstates.png)<br>
*Statusangaben für Spracherkennungsfeedback für Cursor*

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Wichtige Informationen zur Spracherkennung in Mixed Reality
* Sagen Sie **„Auswählen“**, während Sie eine Schaltfläche anvisieren (Sie können dies überall verwenden, um auf eine Schaltfläche zu klicken).
* Sie können in einigen Apps den **Bezeichnungsnamen einer Schaltfläche auf der App-Leiste** sagen, um eine Aktion auszuführen. Beim Betrachten einer App kann ein Benutzer z. B. den Befehl „Entfernen“ sagen, um die App aus der Umgebung zu entfernen (das spart Zeit, da die App nicht mit der Hand angeklickt werden muss).
* Sie können initiieren, dass Cortana zuhört, indem Sie **„Hey Cortana“** sagen. Sie können ihre Fragen stellen ("Hey Cortana, wie hoch ist der Höhe des Höhepunkts?"), sie auffordern, eine App zu öffnen ("Hey Cortana, open Netflix"), oder sie anbringen, das Startmenü ("Hey Cortana, take me home") und mehr zu öffnen.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Häufig gestellte Fragen und Bedenken von Benutzern zur Spracheingabe
* Was kann ich sagen?
* Woher weiß ich, ob das System mich richtig verstanden hat?
   * Das System versteht meine Sprachbefehle immer wieder falsch.
   * Es reagiert nicht, wenn ich einen Sprachbefehl erteile.
* Es reagiert falsch, wenn ich einen Sprachbefehl erteile.
* Wie richte ich meine Stimme auf eine bestimmte App oder einen bestimmten App-Befehl aus?
* Kann ich Objekte per Sprachbefehl aus dem holografischen Rahmen der HoloLens bewegen?

## <a name="see-also"></a>Siehe auch
* [Gesten](../design/gaze-and-commit.md#composite-gestures)
* [Anvisieren mit dem Kopf und Verweilen](../design/gaze-and-dwell.md)