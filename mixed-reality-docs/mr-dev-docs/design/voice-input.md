---
title: Spracheingabe
description: Die Spracheingabe ist eine Kerneingabe für HoloLens und Windows Mixed Reality immersive Headsets. Voice kann für Befehle, Diktat, Cortana und mehr verwendet werden.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, voice, cortana, speech, input, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit, gaze
ms.openlocfilehash: 6773bb71da7d98b1dd00d2246084d469e5e7c6ba
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600579"
---
# <a name="voice-input"></a>Spracheingabe

![Spracheingabe](images/UX_Hero_VoiceCommand.jpg)

Die Stimme ist eine der wichtigsten Formen der Eingabe für HoloLens. Sie können ein Hologramm direkt befehlen, ohne [Handgesten verwenden zu müssen.](gaze-and-commit.md#composite-gestures) Die Spracheingabe kann eine natürliche Art sein, Ihre Absichten zu kommunizieren. Die Stimme ist besonders gut für das Durchlaufen komplexer Schnittstellen, da benutzer mit einem Befehl geschachtelte Menüs durchschneiden können.

Die Spracheingabe wird von derselben [Engine unterstützt,](/windows/uwp/design/input/speech-recognition) die Sprache in allen _universellen Windows-Apps unterstützt._ Auf HoloLens funktioniert die Spracherkennung immer in der Windows-Anzeigesprache, die in den Einstellungen Ihres Geräts konfiguriert ist. 

<br>

## <a name="voice-and-gaze&quot;></a>Sprache und Anving

Wenn Sie Sprachbefehle verwenden, ist das Anvingen mit dem Kopf oder mit den Augen der typische Zielmechanismus, unabhängig davon, ob Sie den Befehl mit einem Cursor auswählen oder an eine Anwendung senden möchten, die Sie betrachten. Möglicherweise ist es nicht einmal erforderlich, einen Anvingcursor _(&quot;siehe es, say it") zu zeigen._ Einige Sprachbefehle erfordern überhaupt kein Ziel, z. B. "Gehe zu Anfang" oder "Hey Cortana".

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

Auch wenn Sie Ihrer App keine Sprachunterstützung hinzufügen, können Ihre Benutzer Hologramme aktivieren, indem sie einfach den Systemstimmenbefehl "select" sagen. Dies verhält sich [](gaze-and-commit.md#composite-gestures) wie ein Tippen in die Luft auf HoloLens, das Drücken der Auswahlschaltfläche auf dem [HoloLens-Klicker](/hololens/hololens1-clicker)oder das Drücken des Triggers auf einem Windows Mixed Reality [Motion-Controller.](motion-controllers.md) Sie hören einen Sound und sehen eine QuickInfo mit "Auswählen" als Bestätigung. "Auswählen" wird durch einen Low-Power-Schlüsselworterkennungsalgorithmus aktiviert, was bedeutet, dass Sie ihn jederzeit mit minimalen Auswirkungen auf die Akkulebensdauer sagen können. Sie können sogar "auswählen" mit den Händen an Ihrer Seite sagen.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        Um den Sprachbefehl "select" in HoloLens 2 verwenden zu können, müssen Sie zuerst den Anvitätscursor zum Verwenden als Zeiger auf die Anzeige verwenden. Der Befehl, um es auf die Leiste zu bringen, ist leicht zu merken, z. B. "auswählen".<br><br>
        Um den Modus zu beenden, verwenden Sie ihre Hände erneut, indem Sie auf die Luft tippen, sich einer Schaltfläche mit den Fingern nähern oder die Systemgeste verwenden.<br>
        <br> 
        *Bild: Sagen Sie "select", um den Sprachbefehl für die Auswahl zu verwenden.*
    :::column-end:::
        :::column:::
       ![Ein Benutzer kann "auswählen" sagen, um den Sprachbefehl für eine Auswahl zu verwenden.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a>Hey Cortana

Sie können "Hey Cortana" sagen, um Cortana jederzeit zu öffnen. Sie müssen nicht warten, bis sie angezeigt wird, um ihr weiterhin Ihre Frage zu stellen oder ihr eine Anweisung zu geben. Versuchen Sie beispielsweise, "Hey Cortana, wie ist das Wetter?" zu sagen. als einzelner Satz. Wenn Sie weitere Informationen zu Cortana und ihren Funktionen benötigen, fragen Sie sie! Sagen Sie "Hey Cortana, was kann ich sagen?" und sie wird eine Liste mit funktionierenden und vorgeschlagenen Befehlen erstellen. Wenn Sie bereits in der Cortana-App sind, wählen Sie **?** Symbol auf der Randleiste, um das gleiche Menü zu öffnen.

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
        Wenn Apps dieser Regel folgen, können Benutzer leicht verstehen, was sie sagen müssen, um das System zu steuern. Wenn Sie in HoloLens (1. Generation) auf eine Schaltfläche klicken, sehen Sie eine QuickInfo zum "Sprachverweilen", die nach einer Sekunde angezeigt wird, wenn die Schaltfläche sprachbereit ist und den Befehl anzeigt, um sie zu "drücken". Zeigen Sie den Sprachcursor an, HoloLens 2 Sprachcursor mit "select" oder "What can I say" (Siehe Abbildung) angezeigt wird, um QuickInfos für stimmende Benutzer zu HoloLens 2. <br>
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

Einige Befehle, wie die oben genannten Befehle für die schnelle Bearbeitung, können ausgeblendet werden. Um zu erfahren, welche Befehle Sie verwenden können, sehen Sie sich ein Objekt an, und sagen Sie: "Was kann ich sagen?". Eine Liste der möglichen Befehle wird angezeigt. Sie können auch den Cursor für den Anvanv auf den Kopf verwenden, um die QuickInfos der Stimme für jede Schaltfläche vor Ihnen zu sehen und zu zeigen. 

Wenn Sie eine vollständige Liste wünschen, sagen Sie einfach immer "Alle Befehle anzeigen". 

## <a name="dictation"></a>Diktieren

Anstatt mit Tippen in die Luft zu [tippen,](gaze-and-commit.md#composite-gestures)kann das Sprachdiktat effizienter sein, um Text in eine App eintippen zu können. Dies kann die Eingabe mit weniger Aufwand für den Benutzer deutlich beschleunigen.

![Sprachdiktat beginnt mit der Auswahl der Mikrofontaste.](images/micbuttonfordictation.png)<br>
*Sprachdiktat beginnt mit dem Auswählen der Mikrofonschaltfläche auf der Tastatur.*

Jedes Mal, wenn die holografische Tastatur aktiv ist, können Sie in den Diktatmodus wechseln, anstatt einzugeben. Wählen Sie das Mikrofon auf der Seite des Texteingabefelds aus, um zu beginnen.

## <a name="adding-voice-commands-to-your-app"></a>Hinzufügen von Sprachbefehlen zu Ihrer App

Erwägen Sie, Sprachbefehle zu jeder von Ihnen erstellten Umgebung hinzuzufügen. Voice ist eine leistungsstarke Möglichkeit, das System und die Apps zu steuern. Da Benutzer mit unterschiedlichen Arten von Dialekten und Akzenten sprechen, wird durch die richtige Auswahl von Sprachschlüsselwörtern sichergestellt, dass die Befehle Ihrer Benutzer eindeutig interpretiert werden.

### <a name="best-practices"></a>Bewährte Methoden

Nachfolgend finden Sie einige Methoden aufgeführt, die eine reibungslose Spracherkennung ermöglichen.
* **Präzise Befehle verwenden**: Wählen Sie nach Möglichkeit Schlüsselwörter mit zwei oder mehr Silben aus. Einsilbige Wörter neigen dazu, unterschiedliche Vokallaute zu verwenden, wenn sie von Personen mit unterschiedlichen Akzenten gesprochen werden. Beispiel: "Video wiedergeben" ist besser als "Wiedergabe des aktuell ausgewählten Videos"
* **Einfaches Vokabular verwenden** – Beispiel: "Hinweis anzeigen" ist besser als "Show placard" (Platzhalter anzeigen)
* **Stellen Sie sicher, dass Befehle nicht destruktiv sind:** Stellen Sie sicher, dass alle Sprachbefehlsaktionen nicht destruktiv sind und leicht rückgängig machen werden können, falls eine andere Person, die in der Nähe des Benutzers spricht, versehentlich einen Befehl auslöst.
* **Ähnlich klingende Befehle vermeiden:** Vermeiden Sie die Registrierung mehrerer Sprachbefehle, die ähnlich klingen. Beispiel: "Mehr anzeigen" und "Store anzeigen" können ähnlich klingen.
* **Aufheben der Registrierung Ihrer App, wenn sie nicht verwendet** wird: Wenn sich Ihre App nicht in einem Zustand befindet, in dem ein bestimmter Sprachbefehl gültig ist, sollten Sie die Registrierung aufheben, damit andere Befehle für diesen nicht verwechselt werden.
* **Mit verschiedenen Akzenten testen**: Testen Sie Ihre App mit Benutzern, die unterschiedliche Akzente verwenden.
* **Konsistenz von Sprachbefehlen beibehalten**: Wenn „Zurück“ zur vorherigen Seite wechselt, übernehmen Sie dieses Verhalten in Ihren Anwendungen.
* **Vermeiden Sie die Verwendung von Systembefehlen:** Die folgenden Sprachbefehle sind für das System reserviert. Vermeiden Sie es daher, sie in Ihren Anwendungen zu verwenden:
   * „Hey Cortana“
   * „Auswählen“
   * "Gehe zu Anfang"

### <a name="advantages-of-voice-input"></a>Vorteile der Spracheingabe

Die Spracheingabe ist eine natürliche Art, unsere Absichten zu kommunizieren. Die Stimme eignet sich besonders gut für **Schnittstellendurchgänge,** da sie Benutzern helfen kann, mehrere Schritte einer Schnittstelle zu durchlaufen. Ein Benutzer kann beim Betrachten einer Webseite "Zurück" sagen, anstatt in der App auf die Schaltfläche "Zurück" klicken zu müssen. Diese kleine Zeitersparnis hat einen starken **emotionalen Effekt** auf die Wahrnehmung der Benutzererfahrung und bietet ihnen eine geringe Superleistung. Die Spracheingabe ist auch eine bequeme Eingabemethode, wenn unsere Arme nicht frei sind oder wir **mehrere Aufgaben gleichzeitig** erledigen. Auf Geräten, auf denen die Eingabe auf einer Tastatur schwierig ist, kann **das Sprachdiktat** eine effiziente Alternative zur Eingabe von Text sein. Schließlich kann die Stimme in einigen Fällen, in denen der **Genauigkeitsbereich** für Anvieren und Gesten begrenzt ist, dazu beitragen, die Absicht des Benutzers eindeutig zu machen. 

**Vorteile der Spracheingabe für den Benutzer**
* Verkürzt den Zeitaufwand – das Endziel sollte effizienter erreicht werden.
* Minimiert den Aufwand – Aufgaben sollten flüssiger und müheloser verlaufen.
* Reduziert die kognitive Belastung – sie ist intuitiv, leicht zu erlernen und zu merken.
* Es ist akzeptabel, denn es sollte in gesellschaftliche Verhaltensmuster passen.
* Sie stellt eine Routine dar – die Spracheingabe kann leicht zu einem gewohnheitsmäßigen Verhalten werden.

### <a name="challenges-for-voice-input"></a>Herausforderungen bei der Spracheingabe

Die Spracheingabe eignet sich zwar hervorragend für viele verschiedene Anwendungen, sie steht aber auch vor mehreren Herausforderungen. Wenn Sie sowohl die Vorteile als auch die Herausforderungen bei der Spracheingabe verstehen, können App-Entwickler intelligentere Entscheidungen darüber treffen, wie und wann sie Spracheingaben verwenden und eine großartige Erfahrung für ihre Benutzer schaffen.

**Spracheingabe für kontinuierliche Eingabesteuerung** Dazu gehört eine differenzierte Steuerung. Beispielsweise kann ein Benutzer sein Volume in seiner Musik-App ändern. Sie kann "lauter" sagen, aber es ist nicht klar, wie viel lauter das System die Lautstärke machen soll. Der Benutzer könnte sagen: "Make it a little lauter", aber "a little" is difficult to quantifizieren. Das Verschieben oder Skalieren von Hologrammen mit Der Stimme ist ähnlich schwierig. 

**Zuverlässigkeit der Spracheingabeerkennung** Spracheingabesysteme werden zwar immer besser, aber manchmal hören und interpretieren sie einen Sprachbefehl möglicherweise falsch.
Der Schlüssel besteht darin, die Herausforderung in Ihrer Anwendung zu bewältigen. Geben Sie Ihren Benutzern Feedback, wenn das System lauscht, und was das System verstanden hat, verdeutlicht mögliche Probleme beim Verstehen der Sprache der Benutzer.  

**Spracheingabe in freigegebenen Bereichen** Die Stimme ist in Bereichen, die Sie mit anderen teilen, möglicherweise nicht akzeptabel.
Hier sind einige Beispiele:
* Der Benutzer möchte andere Benutzer möglicherweise nicht stören (z. B. in einer stillen Bibliothek oder einem freigegebenen Büro).
* Benutzer haben möglicherweise das Gefühl, dass sie öffentlich mit sich selbst sprechen.
* Ein Benutzer hat möglicherweise das Gefühl, dass er eine persönliche oder vertrauliche Nachricht (einschließlich Kennwörter) diktiert, während andere lauschen.

**Spracheingabe von eindeutigen oder unbekannten Wörtern** Schwierigkeiten bei der Spracheingabe treten auch auf, wenn Benutzer Wörter diktieren, die dem System möglicherweise unbekannt sind, z. B. Spitznamen, bestimmte Slangwörter oder Abkürzungen. 

**Erlernen von Sprachbefehlen** Obwohl das oberste Ziel darin besteht, sich auf natürliche Weise mit Ihrem System zu unterhalten, basieren Apps häufig immer noch auf bestimmten vordefinierten Sprachbefehlen.
Eine Herausforderung, die mit einem erheblichen Satz von Sprachbefehlen verbunden ist, besteht darin, sie zu trainieren, ohne den Benutzer zu überladen, und wie sie dem Benutzer helfen können, sie beizubehalten. 

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
       ![*3. Regulärer Cursorzustand](images/voicefeedbackstates-regular.jpg)<br>
       **3. Kehrt zum regulären Cursorzustand zurück**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Wichtige Informationen zur Spracherkennung in Mixed Reality

* Sagen **Sie "Auswählen",** während Sie auf eine Schaltfläche abzielen (Sie können diese überall verwenden, um eine Schaltfläche auszuwählen).
* Sie können in einigen Apps den **Bezeichnungsnamen einer Schaltfläche auf der App-Leiste** sagen, um eine Aktion auszuführen. Wenn sie sich beispielsweise eine App ansehen, kann ein Benutzer den Befehl "Remove" (Entfernen) verwenden, um die App aus der Welt zu entfernen (dies spart Zeit, sie nicht mit der Hand auswählen zu müssen).
* Sie können cortana lauschen, indem Sie **"Hey Cortana" sagen.** Sie können ihr Fragen stellen („Hey Cortana, wie hoch ist der Eiffelturm“), sie zum Öffnen einer App auffordern („Hey Cortana, öffne Netflix“) oder ihr sagen, sie soll das Startmenü aufrufen („Hey Cortana, öffne das Startmenü“) und vieles mehr.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Häufig gestellte Fragen und Bedenken von Benutzern zur Spracheingabe

* Was kann ich sagen?
* Woher weiß ich, ob das System mich richtig verstanden hat?
   * Das System versteht meine Sprachbefehle immer wieder falsch.
   * Es reagiert nicht, wenn ich einen Sprachbefehl erteile.
* Es reagiert falsch, wenn ich einen Sprachbefehl erteile.
* Wie richte ich meine Stimme auf eine bestimmte App oder einen bestimmten App-Befehl aus?
* Kann ich Objekte per Sprachbefehl aus dem holografischen Rahmen der HoloLens bewegen?

## <a name="communication"></a>Kommunikation

Für Anwendungen, die die von HoloLens bereitgestellten benutzerdefinierten Verarbeitungsoptionen für Audioeingaben nutzen möchten, ist es wichtig, die verschiedenen [Audiostreamkategorien](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) zu verstehen, die Ihre App nutzen kann. Windows 10 unterstützt mehrere verschiedene Streamkategorien, und HoloLens nutzt drei davon, um eine benutzerdefinierte Verarbeitung zu ermöglichen, um die Audioqualität des Mikrofons zu optimieren, die auf Sprache, Kommunikation und andere zugeschnitten ist, die für Umgebungs-Audioerfassungsszenarien (also "Anmeldungen") verwendet werden kann.
* Die AudioCategory_Communications Streamkategorie ist für Anrufqualitäts- und Sprachausgabeszenarien angepasst und stellt dem Client einen 24-Bit-Mono-Audiodatenstrom mit 16 kHz der Stimme des Benutzers bereit.
* Die Kategorie AudioCategory_Speech Stream ist für die HoloLens-Sprach-Engine (Windows) angepasst und bietet einen 24-Bit-Monostream mit 16 kHz der Stimme des Benutzers. Diese Kategorie kann bei Bedarf von Sprach-Engines von Drittanbietern verwendet werden.
* Die Kategorie AudioCategory_Other Datenstroms ist für die Audioaufzeichnung in der Umgebung angepasst und bietet dem Client einen 24-Bit-Stereo-Audiostream mit 48 kHz.

All diese Audioverarbeitung wird hardwarebeschleunigte, was bedeutet, dass die Features deutlich weniger Leistung beanspruchen, als wenn die gleiche Verarbeitung auf der HoloLens-CPU erfolgt wäre. Vermeiden Sie das Ausführen anderer Audioeingaben auf der CPU, um die Akkulaufzeit des Systems zu maximieren und die integrierte, ausgelagerte Audioeingabeverarbeitung zu nutzen.

## <a name="languages"></a>Sprachen

HoloLens 2 unterstützt [mehrere Sprachen.](/hololens/hololens2-language-support) Beachten Sie, dass Sprachbefehle immer in der Anzeigesprache des Systems ausgeführt werden, auch wenn mehrere Tastaturen installiert sind oder wenn Apps versuchen, eine Spracherkennung in einer anderen Sprache zu erstellen.

## <a name="troubleshooting"></a>Problembehandlung

Wenn bei der Verwendung von "select" und "Hey Cortana" Probleme auftreten, versuchen Sie, in einen stilleren Bereich zu wechseln, sich von der Rauschquelle zu lösen oder laut zu sprechen. Zurzeit ist die gesamte Spracherkennung auf HoloLens optimiert und speziell für Native Speakers von USA Englisch optimiert.

Für das Windows Mixed Reality Developer Edition-Release 2017 funktioniert die Logik für die Verwaltung von Audioendpunkten nach dem Abmelden und wieder beim PC-Desktop nach der anfänglichen HMD-Verbindung (für immer). Vor diesem ersten Abmelde-/In-Ereignis nach dem Durchlaufen der WMR-OOBE konnten dem Benutzer verschiedene Probleme mit der Audiofunktionalität auftreten, die von keinem Audio- bis hin zu keinem Audiowechsel reichen, je nachdem, wie das System eingerichtet wurde, bevor er zum ersten Mal eine Verbindung mit der HMD herstellte.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Spracheingabe im MRTK (Mixed Reality Toolkit) für Unity
Mit **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie problemlos Sprachbefehle für beliebige Objekte zuweisen. Verwenden Sie das **Spracheingabeprofil** des MRTK, um Ihre Schlüsselwörter zu definieren. Indem Sie das **SpeechInputHandler-Skript** zuweisen, können Sie jedes Objekt auf die Schlüsselwörter reagieren, die im Spracheingabeprofil definiert sind. SpeechInputHandler stellt auch eine Bezeichnung für die Sprachbestätigung zur Verbesserung der Benutzervertrauenserkennung zur Verbesserung der Sicherheit des Benutzers.

* [MRTK – Sprachbefehl](/windows/mixed-reality/mrtk-unity/features/input/speech)

---

## <a name="see-also"></a>Siehe auch

* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe in DirectX](../develop/native/voice-input-in-directx.md)
* [Spracheingabe in Unity](../develop/unity/voice-input-in-unity.md)