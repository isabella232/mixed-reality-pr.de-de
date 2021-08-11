---
title: Spracheingabe
description: Die Spracheingabe ist eine Kerneingabe für HoloLens und Windows Mixed Reality immersive Headsets. Sprache kann für Befehle, Diktat, Cortana und mehr verwendet werden.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, voice, cortana, speech, input, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit, gaze
ms.openlocfilehash: f7ae7ddd40fff3da660cc747d01d258b9fb0eb31f3b024ec77efd2b560e037d7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223697"
---
# <a name="voice-input"></a>Spracheingabe

![Spracheingabe](images/UX_Hero_VoiceCommand.jpg)

Die Stimme ist eine der wichtigsten Formen der Eingabe für HoloLens. Sie können ein Hologramm direkt befehlen, ohne [Handgesten verwenden zu müssen.](gaze-and-commit.md#composite-gestures) Die Spracheingabe kann eine natürliche Art sein, Ihre Absichten zu kommunizieren. Die Stimme ist besonders gut für das Durchlaufen komplexer Schnittstellen, da benutzer mit einem Befehl geschachtelte Menüs durchschneiden können.

Die Spracheingabe wird von derselben [Engine unterstützt,](/windows/uwp/design/input/speech-recognition) die Sprache in allen universellen Windows _Apps unterstützt._ Auf HoloLens funktioniert die Spracherkennung immer in der Windows Anzeigesprache, die in Ihrem Gerät konfiguriert Einstellungen. 

<br>

## <a name="voice-and-gaze&quot;></a>Sprache und Anving

Wenn Sie Sprachbefehle verwenden, ist das Anvingen mit dem Kopf oder mit den Augen der typische Zielmechanismus, egal ob mit einem Cursor zum &quot;Auswählen&quot; oder zum Kanal des Befehls zu einer Anwendung, die Sie betrachten. Möglicherweise ist es nicht einmal erforderlich, einen Anvingcursor _(&quot;siehe es, say it") zu zeigen._ Einige Sprachbefehle erfordern überhaupt kein Ziel, z. B. "Gehe zu Start" oder "Hey Cortana".

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


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
        <td>Spracheingabe</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (mit Mikrofon)</td>
    </tr>
</table>

## <a name="the-select-command"></a>Der Befehl "select"

**HoloLens (1. Generation)**

Auch wenn Sie Ihrer App keine Sprachunterstützung hinzufügen, können Ihre Benutzer Hologramme aktivieren, indem sie einfach den Systemstimmenbefehl "select" sagen. Dies verhält sich [](gaze-and-commit.md#composite-gestures) wie ein Tippen in die Luft auf HoloLens, das Drücken der Auswahlschaltfläche auf dem [HoloLens-Klicker](/hololens/hololens1-clicker)oder das Drücken des Triggers auf einem Windows Mixed Reality [Motion-Controller](motion-controllers.md). Sie hören einen Sound und sehen eine QuickInfo mit "Auswählen" als Bestätigung. "Auswählen" wird durch einen Low-Power-Schlüsselworterkennungsalgorithmus aktiviert, was bedeutet, dass Sie ihn jederzeit mit minimalen Auswirkungen auf die Akkulebensdauer sagen können. Sie können sogar "Auswählen" mit den Händen an Ihrer Seite sagen.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        Um den Sprachbefehl "select" in HoloLens 2 verwenden zu können, müssen Sie zuerst den Anvitätscursor zum Verwenden als Zeiger auf die Anzeige verwenden. Der Befehl, um es auf die Leiste zu bringen, ist leicht zu merken, z. B. "auswählen".<br><br>
        Um den Modus zu beenden, verwenden Sie ihre Hände erneut, indem Sie auf die Luft tippen, sich einer Schaltfläche mit den Fingern nähern oder die Systemgeste verwenden.<br>
        <br> 
        *Bild: Sagen Sie "auswählen", um den Sprachbefehl für die Auswahl zu verwenden.*
    :::column-end:::
        :::column:::
       ![Ein Benutzer kann "auswählen" sagen, um den Sprachbefehl für eine Auswahl zu verwenden.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a>Hey Cortana

Sie können "Hey Cortana" sagen, um Cortana jederzeit zu erhalten. Sie müssen nicht warten, bis sie angezeigt wird, um ihr weiterhin Ihre Frage zu stellen oder ihr eine Anweisung zu geben. Versuchen Sie beispielsweise, "Hey Cortana, what es the weather?" zu sagen. als einzelner Satz. Wenn Sie weitere Informationen zu Cortana und zu den Ihnen zur Verfügung stellen können, fragen Sie sie! Sagen Sie "Hey Cortana, was kann ich sagen?" und sie wird eine Liste mit funktionierenden und vorgeschlagenen Befehlen erstellen. Wenn Sie sich bereits in der App Cortana, wählen Sie ?  Symbol auf der Randleiste, um das gleiche Menü zu öffnen.

**HoloLens-spezifische Befehle**
* Was kann ich sagen?
* "Gehe zu Start" [](system-gesture.md#bloom) – anstatt zum [Startmenü zu wechseln](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)
* <app>"Launch" (Starten)
* "Hier <app> verschieben"
* "Bild machen"
* "Aufzeichnung starten"
* "Aufzeichnung beenden"
* "Handstrahl anzeigen"
* "Handstrahl ausblenden"
* "Helligkeit erhöhen"
* "Helligkeit verringern"
* "Volume erhöhen"
* "Verringern des Volumes"
* "Mute" oder "Unmute"
* "Gerät herunterfahren"
* "Gerät neu starten"
* "In den Ruhezustand wechseln"
* "What time is it?"
* "Wie viel Akku habe ich noch?"

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"See It, Say It"<br>
        HoloLens verfügt über ein Modell "Sehen Sie es, sagen Sie es" für die Spracheingabe, bei dem Bezeichnungen auf Schaltflächen Benutzern mitteilen, welche Sprachbefehle sie auch sagen können. Wenn beispielsweise ein App-Fenster in HoloLens (1. Generation) angezeigt wird, kann ein Benutzer den Befehl "Anpassen" sagen, um die Position der App in der Welt anzupassen.<br>
        <br>
        *Bild: Ein Benutzer kann den Befehl "Anpassen" sagen, der in der App-Leiste angezeigt wird, um die Position der App anzupassen.*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![Beim Anzeigen eines App-Fensters oder Hologramms kann ein Benutzer den Befehl "Anpassen" sagen, der in der App-Leiste angezeigt wird, um die Position der App in der Welt anzupassen.](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        Wenn Apps dieser Regel folgen, können Benutzer leicht verstehen, was sie sagen müssen, um das System zu steuern. Wenn Sie in HoloLens (1. Generation) auf eine Schaltfläche klicken, wird eine QuickInfo "Sprachverweilung" angezeigt, die nach einer Sekunde angezeigt wird, wenn die Schaltfläche sprachbereit ist und den Befehl anzeigt, um sie zu "drücken". Zeigen Sie den Sprachcursor an, indem Sie "select" (Auswählen) oder "What can I say" (Was kann ich sagen) sagen, um QuickInfos für Die Stimme in der HoloLens 2 anzeigen (siehe Abbildung). <br>
        <br>
        *Abbildung: Befehle "See it, say it" werden unterhalb der Schaltflächen angezeigt.*
    :::column-end:::
        :::column:::
       ![Sehen Sie es, sagen Sie, dass Befehle unter den Schaltflächen angezeigt werden.](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Sprachbefehle für schnelle Hologrammbearbeitung

Es gibt viele Sprachbefehle, die Sie sagen können, während Sie sich an einem Hologramm befinden, um Schnellbearbeitungsaufgaben auszuführen. Diese Sprachbefehle funktionieren in App-Fenstern und 3D-Objekten, die Sie auf der Welt platziert haben.

**Befehle zur Hologrammbearbeitung**
* Zu mir drehen
* Größere | Verbessern
* Kleiner

Auf HoloLens 2 können Sie auch natürlichere Interaktionen in Kombination mit dem Anvisieren mit den Augen erstellen, das implizit Kontextinformationen darüber liefert, worauf Sie verweisen. Sie könnten z. B. ein Hologramm betrachten und "put _this"_ sagen und dann an der Stelle suchen, an der Sie es platzieren möchten, und "over _here"_ sagen.
Oder Sie könnten einen holografischen Teil auf einem komplexen Computer betrachten und sagen: "Geben Sie mir weitere Informationen zu _diesem "._

## <a name="discovering-voice-commands"></a>Entdecken von Sprachbefehlen

Einige Befehle, wie die oben genannten Befehle für die schnelle Bearbeitung, können ausgeblendet werden. Um zu erfahren, welche Befehle Sie verwenden können, sehen Sie sich ein Objekt an, und sagen Sie: "Was kann ich sagen?". Eine Liste der möglichen Befehle wird angezeigt. Sie können auch den Cursor für den Anvanving mit dem Kopf verwenden, um die QuickInfos der Stimme für jede Schaltfläche vor Ihnen zu sehen und zu zeigen. 

Wenn Sie eine vollständige Liste wünschen, sagen Sie einfach immer "Alle Befehle anzeigen". 

## <a name="dictation"></a>Diktieren

Anstatt mit Tippen in die Luft [zu](gaze-and-commit.md#composite-gestures)tippen, kann das Sprachdiktat effizienter sein, um Text in eine App eintippen zu können. Dies kann die Eingabe mit weniger Aufwand für den Benutzer deutlich beschleunigen.

![Sprachdiktat beginnt mit der Auswahl der Mikrofontaste.](images/micbuttonfordictation.png)<br>
*Sprachdiktat beginnt mit dem Auswählen der Mikrofonschaltfläche auf der Tastatur.*

Immer wenn die holografische Tastatur aktiv ist, können Sie in den Diktatmodus wechseln, anstatt zu tippen. Wählen Sie das Mikrofon auf der Seite des Texteingabefelds aus, um loszulegen.

## <a name="adding-voice-commands-to-your-app"></a>Hinzufügen von Sprachbefehlen zu Ihrer App

Erwägen Sie, Sprachbefehle zu jeder von Ihnen erstellten Umgebung hinzuzufügen. Sprache ist eine leistungsstarke Möglichkeit, das System und die Apps zu steuern. Da Benutzer mit verschiedenen Arten von Dialekten und Akzenten sprechen, wird durch die richtige Auswahl von Sprachschlüsselwörtern sichergestellt, dass die Befehle Ihrer Benutzer eindeutig interpretiert werden.

### <a name="best-practices"></a>Bewährte Methoden

Nachfolgend finden Sie einige Methoden aufgeführt, die eine reibungslose Spracherkennung ermöglichen.
* **Präzise Befehle verwenden**: Wählen Sie nach Möglichkeit Schlüsselwörter mit zwei oder mehr Silben aus. Einsilbige Wörter neigen dazu, unterschiedliche Vokallaute zu verwenden, wenn sie von Personen mit unterschiedlichen Akzenten gesprochen werden. Beispiel: "Play video" ist besser als "Play the currently selected video"
* **Verwenden eines einfachen** Vokabulars: Beispiel: "Hinweis anzeigen" ist besser als "Platzhalter anzeigen".
* **Stellen Sie** sicher, dass Befehle nicht destruktiv sind: Stellen Sie sicher, dass alle Sprachbefehlsaktionen nicht destruktiv sind und problemlos rückgängig gemacht werden können, falls eine andere Person, die in der Nähe des Benutzers spricht, versehentlich einen Befehl auslöst.
* **Ähnliche klingende Befehle vermeiden:** Vermeiden Sie die Registrierung mehrerer Sprachbefehle, die ähnlich klingen. Beispiel: "Show more" (Mehr anzeigen) und "Show store" (Store anzeigen) können ähnlich klingen.
* **Aufheben** der Registrierung Ihrer App, wenn sie nicht verwendet wird: Wenn sich Ihre App nicht in einem Zustand befindet, in dem ein bestimmter Sprachbefehl gültig ist, sollten Sie die Registrierung aufheben, damit andere Befehle für diesen Befehl nicht verwirrend sind.
* **Mit verschiedenen Akzenten testen**: Testen Sie Ihre App mit Benutzern, die unterschiedliche Akzente verwenden.
* **Konsistenz von Sprachbefehlen beibehalten**: Wenn „Zurück“ zur vorherigen Seite wechselt, übernehmen Sie dieses Verhalten in Ihren Anwendungen.
* **Vermeiden Sie die Verwendung von** Systembefehlen: Die folgenden Sprachbefehle sind für das System reserviert, daher sollten Sie sie nicht in Ihren Anwendungen verwenden:
   * „Hey Cortana“
   * „Auswählen“
   * "Gehe zu Anfang"

### <a name="advantages-of-voice-input"></a>Vorteile der Spracheingabe

Die Spracheingabe ist eine natürliche Art, unsere Absichten zu kommunizieren. Die Stimme ist besonders gut für **Schnittstellendurchlaufe,** da sie Benutzern dabei helfen kann, mehrere Schritte einer Schnittstelle zu durchlaufen. Ein Benutzer kann beim Anzeigen einer Webseite "Zurück" sagen, anstatt nach oben zu wechseln und in der App auf die Schaltfläche "Zurück" zu klicken. Diese kleine Zeiteinsparung hat einen starken **emotionalen** Effekt auf die Wahrnehmung der Benutzererfahrung und bietet ihnen eine geringe Superkraft. Die Spracheingabe ist auch eine bequeme Eingabemethode, wenn unsere Arme nicht frei sind oder wir **mehrere Aufgaben gleichzeitig** erledigen. Auf Geräten, bei denen die Eingabe auf einer Tastatur schwierig ist, kann das **Sprachdiktat** eine effiziente Alternative zur Eingabe von Text sein. Schließlich kann die Stimme  in einigen Fällen, in denen der Genauigkeitsbereich für Anvität und Gesten begrenzt ist, dazu beitragen, die Absicht des Benutzers zu mehrdeutig zu machen. 

**Vorteile der Spracheingabe für den Benutzer**
* Verkürzt den Zeitaufwand – das Endziel sollte effizienter erreicht werden.
* Minimiert den Aufwand – Aufgaben sollten flüssiger und müheloser verlaufen.
* Reduziert die kognitive Belastung – sie ist intuitiv, leicht zu erlernen und zu merken.
* Sie ist akzeptabel und sollte mit gesellschaftlichen Verhaltensmustern zusammenpassen.
* Sie stellt eine Routine dar – die Spracheingabe kann leicht zu einem gewohnheitsmäßigen Verhalten werden.

### <a name="challenges-for-voice-input"></a>Herausforderungen bei der Spracheingabe

Die Spracheingabe ist zwar für viele verschiedene Anwendungen geeignet, aber sie steht auch vor mehreren Herausforderungen. Wenn Sie sowohl die Vorteile als auch die Herausforderungen der Spracheingabe verstehen, können App-Entwickler intelligentere Entscheidungen treffen, wie und wann sie spracheingaben verwenden sollten, und für ihre Benutzer eine hervorragende Erfahrung schaffen.

**Spracheingabe für die kontinuierliche Eingabesteuerung** Eine davon ist eine fein abgrenzende Steuerung. Beispielsweise kann es sein, dass ein Benutzer sein Volume in seiner Musik-App ändern möchte. Sie kann "lauter" sagen, aber es ist nicht klar, wie viel lauter das System das Volume machen soll. Der Benutzer könnte sagen: "Make it a little lauter", but "a little" is difficult to quantifizieren. Das Verschieben oder Skalieren von Hologrammen mit Sprache ist ähnlich schwierig. 

**Zuverlässigkeit der Spracheingabeerkennung** Während Spracheingabesysteme immer besser werden, können sie einen Sprachbefehl manchmal falsch hören und interpretieren.
Der Schlüssel besteht darin, die Herausforderung in Ihrer Anwendung zu bewältigen. Geben Sie Ihren Benutzern Feedback, wenn das System lausiert und was das System verstanden hat, um potenzielle Probleme beim Verständnis der Sprache der Benutzer zu beheben.  

**Spracheingabe in gemeinsam genutzten Räumen** Die Stimme ist in Räumen, die Sie mit anderen teilen, möglicherweise nicht akzeptabel.
Hier sind einige Beispiele:
* Der Benutzer möchte möglicherweise keine anderen (z. B. in einer stillen Bibliothek oder einem gemeinsam genutzten Büro) stören.
* Benutzer können sich umstauen, wenn sie sehen, wie sie öffentlich mit sich selbst sprechen.
* Ein Benutzer hat möglicherweise das Gefühl, eine persönliche oder vertrauliche Nachricht (einschließlich Kennwörtern) zu diktieren, während andere Benutzer lauschen.

**Spracheingabe von eindeutigen oder unbekannten Wörtern** Schwierigkeiten bei der Spracheingabe kommen auch dann vor, wenn Benutzer Wörter diktieren, die dem System möglicherweise unbekannt sind, z. B. Spitznamen, bestimmte Slangwörter oder Abkürzungen. 

**Learning Sprachbefehle** Das endgültige Ziel besteht zwar in der natürlichen Umkehrung mit Ihrem System, aber häufig basieren Apps immer noch auf bestimmten vordefinierten Sprachbefehlen.
Eine Herausforderung, die mit einer großen Menge von Sprachbefehlen verbunden ist, besteht darin, ihnen beizubringen, ohne den Benutzer zu überlasten, und wie sie dem Benutzer helfen können, sie zu behalten. 

<br>

---

### <a name="voice-feedback-states"></a>Statusangaben für Spracherkennungsfeedback

Wenn die Spracherkennung richtig angewendet wird, versteht der Benutzer, **was er sagen kann und er erhält ein eindeutiges Feedback**, das das System **ihn richtig verstanden hat**. Diese beiden Signale geben dem Benutzer das Gefühl, dass er die Spracherkennung als primäre Eingabemethode verwenden kann. Nachfolgend ist in einem Diagramm dargestellt, was mit dem Cursor geschieht, wenn die Spracheingabe erkannt wird und wie dies dem Benutzer vermittelt wird.


:::row:::
    :::column:::
       ![1. Regulärer Cursorzustand](images/voicefeedbackstates-regular.jpg)<br>
       **1. Regulärer Cursorzustand**<br>
    :::column-end:::
    :::column:::
       ![2. Kommuniziert Sprachfeedback und verschwindet dann](images/voicefeedbackstates-voice.jpg)<br>
        **2. Kommuniziert Sprachfeedback und verschwindet dann**<br>
    :::column-end:::
    :::column:::
       ![*3. Normaler Cursorzustand](images/voicefeedbackstates-regular.jpg)<br>
       **3. Kehrt zum normalen Cursorzustand zurück**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Wichtige Informationen zur Spracherkennung in Mixed Reality

* Sagen **Sie "Auswählen",** während Sie eine Schaltfläche als Ziel verwenden (Sie können diese überall verwenden, um eine Schaltfläche auszuwählen).
* Sie können in einigen Apps den **Bezeichnungsnamen einer Schaltfläche auf der App-Leiste** sagen, um eine Aktion auszuführen. Beispielsweise kann ein Benutzer beim Blick auf eine App den Befehl "Entfernen" sagen, um die App aus der Welt zu entfernen (dies spart Zeit, um sie mit ihrer Hand auswählen zu müssen).
* Sie können beginnen, Cortana zu lauschen, indem **Sie "Hey Cortana" sagen.** Sie können ihr Fragen stellen („Hey Cortana, wie hoch ist der Eiffelturm“), sie zum Öffnen einer App auffordern („Hey Cortana, öffne Netflix“) oder ihr sagen, sie soll das Startmenü aufrufen („Hey Cortana, öffne das Startmenü“) und vieles mehr.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Häufig gestellte Fragen und Bedenken von Benutzern zur Spracheingabe

* Was kann ich sagen?
* Woher weiß ich, ob das System mich richtig verstanden hat?
   * Das System versteht meine Sprachbefehle immer wieder falsch.
   * Es reagiert nicht, wenn ich einen Sprachbefehl erteile.
* Es reagiert falsch, wenn ich einen Sprachbefehl erteile.
* Wie richte ich meine Stimme auf eine bestimmte App oder einen bestimmten App-Befehl aus?
* Kann ich Objekte per Sprachbefehl aus dem holografischen Rahmen der HoloLens bewegen?

## <a name="communication"></a>Kommunikation

Für Anwendungen, die die benutzerdefinierten Audioeingabeverarbeitungsoptionen von HoloLens nutzen möchten, ist es [](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) wichtig, die verschiedenen Audiostreamkategorien zu verstehen, die Ihre App nutzen kann. Windows 10 unterstützt mehrere verschiedene Streamkategorien, und HoloLens verwendet drei davon, um eine benutzerdefinierte Verarbeitung zu ermöglichen, um die Audioqualität des Mikrofons zu optimieren, die auf Sprache, Kommunikation und andere zugeschnitten ist und für Umgebungsaudioerfassungsszenarien (d. h. "Logoen") verwendet werden kann.
* Die AudioCategory_Communications-Streamkategorie ist für Anrufqualitäts- und Spracherkennungsszenarien angepasst und stellt dem Client einen 24-Bit-Mono-Audiostream mit 16 kHz der Stimme des Benutzers zur Verfügung.
* Die AudioCategory_Speech-Streamkategorie ist für die HoloLens-Sprach-Engine (Windows) angepasst und stellt einen 24-Bit-Monostream der Stimme des Benutzers mit 16 kHz zur Verfügung. Diese Kategorie kann bei Bedarf von Sprach-Engines von Drittanbietern verwendet werden.
* Die AudioCategory_Other Streamkategorie ist für die Audioaufzeichnung in der Umgebungsumgebung angepasst und stellt dem Client einen 24-Bit-Stereo-Audiostream mit 48 kHz zur Verfügung.

All diese Audioverarbeitung wird hardwarebeschleunigt, was bedeutet, dass die Features viel weniger Leistung verbrauchen, als wenn die gleiche Verarbeitung auf der HoloLens erfolgt wäre. Vermeiden Sie die Ausführung einer anderen Audioeingabeverarbeitung auf der CPU, um die Akkulaufzeit des Systems zu maximieren und die integrierte, ausgeladene Audioeingabeverarbeitung zu nutzen.

## <a name="languages"></a>Sprachen

HoloLens 2 unterstützt [mehrere Sprachen.](/hololens/hololens2-language-support) Denken Sie daran, dass Sprachbefehle immer in der Anzeigesprache des Systems ausgeführt werden, auch wenn mehrere Tastaturen installiert sind oder Apps versuchen, eine Spracherkennung in einer anderen Sprache zu erstellen.

## <a name="troubleshooting"></a>Problembehandlung

Wenn bei der Verwendung von "select" und "Hey Cortana" Probleme auft sind, versuchen Sie, in einen stilleren Bereich zu fahren, sich von der Quelle des Rauschens zu lösen oder lauter zu sprechen. Zu diesem Zeitpunkt wird die spracherkennung auf HoloLens optimiert und speziell für native Sprecher von USA optimiert.

Für das Windows Mixed Reality Developer Edition-Release 2017 funktioniert die Verwaltungslogik für Audioendpunkte einwandfrei (für immer), nachdem sie sich nach der ersten HMD-Verbindung ab- und wieder beim PC-Desktop angemeldet hat. Vor diesem ersten Abmelde-/Anmeldeereignis nach der WMR OOBE konnte der Benutzer verschiedene Audiofunktionalitätsprobleme haben, die von keinem Audio zu keinem Audiowechsel reichen, je nachdem, wie das System eingerichtet wurde, bevor der HMD zum ersten Mal verbunden wurde.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Spracheingabe im MRTK (Mixed Reality Toolkit) für Unity
Mit **[MRTK können](https://github.com/Microsoft/MixedRealityToolkit-Unity)** Sie sprachbefehle problemlos für beliebige Objekte zuweisen. Verwenden Sie das **Spracheingabeprofil** des MRTK, um Ihre Schlüsselwörter zu definieren. Indem Sie das **SpeechInputHandler-Skript** zuweisen, können Sie jedes Objekt auf die Schlüsselwörter reagieren, die im Spracheingabeprofil definiert sind. SpeechInputHandler stellt auch eine Bezeichnung für die Sprachbestätigung zur Verbesserung der Benutzervertrauenserkennung zur Verbesserung der Sicherheit des Benutzers.

* [MRTK – Sprachbefehl](/windows/mixed-reality/mrtk-unity/features/input/speech)

---

## <a name="see-also"></a>Siehe auch

* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe in DirectX](../develop/native/voice-input-in-directx.md)
* [Spracheingabe in Unity](../develop/unity/voice-input-in-unity.md)