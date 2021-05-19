---
title: Dokumentationsleitfaden
description: Dokumentationsrichtlinien und Standards für das MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: cc5572e65540fa40cb1b8db56afbdd0986c467b9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144801"
---
# <a name="documentation-guidelines"></a>Dokumentationsrichtlinien

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

In diesem Dokument werden die Dokumentationsrichtlinien und Standards für das Mixed Reality Toolkit (MRTK) beschrieben. Dies bietet eine Einführung in technische Aspekte des Schreibens und Generierens von Dokumentationen, um häufige Fallstricke hervorzuheben und den empfohlenen Schreibstil zu beschreiben.

Die Seite selbst soll als Beispiel dienen und verwendet daher den beabsichtigten Stil und die gängigsten Markupfeatures der Dokumentation.

- [Quelle](#source-documentation)
- [Vorgehensweise](#how-to-documentation)
- [Design](#design-documentation)
- [Leistungshinweise](#performance-notes)
- [Wichtige Änderungen](#breaking-changes)

---

## <a name="functionality-and-markup"></a>Funktionalität und Markup

In diesem Abschnitt werden häufig benötigte Features beschrieben. Um zu sehen, wie sie funktionieren, sehen Sie sich den Quellcode der Seite an.

1. Nummerierte Listen
   1. Geschachtelte nummerierte Listen mit mindestens 3 führenden Leerzeichen
   1. Die tatsächliche Zahl im Code ist irrelevant. Bei der Analyse wird die richtige Elementnummer festgelegt.

- Aufzählungszeichenlisten
  - Geschachtelte Aufzählungspunkte
- Fett **formatiertem** Text mit \* \* doppeltem Sternchen\*\*
- _Text_ *mit* \_ Unterstrich \_ oder \* einzelnem Sternchen\*
- Text `highlighted as code` innerhalb eines Satzes mit \` Rückquotes\`
- Links zu dokumentationsseitigen [MRTK-Dokumentationsrichtlinien](documentation-guide.md)
- Links zu [Ankern innerhalb einer Seite](#style); Anker werden gebildet, indem Leerzeichen durch Bindestriche ersetzt und in Kleinbuchstaben konvertiert werden.

Für Codebeispiele verwenden wir die Blöcke mit drei Backticks und geben \` \` \` *csharp* als Sprache für die Syntaxhervorhebung an:

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

Wenn Code in einem Satz erwähnt `use a single backtick` wird.

### <a name="todos"></a>Todos

Vermeiden Sie die Verwendung von TODOs in Dokumentationen, da diese TODOs (z. B. Code-TODOs) im Laufe der Zeit dazu tendieren, sich anzusammeln und Informationen darüber zu erhalten, wie sie aktualisiert werden sollten und warum sie verloren gehen.

Wenn das Hinzufügen eines ToDO unbedingt erforderlich ist, führen Sie die folgenden Schritte aus:

1. Erstellen Sie ein neues Problem auf GitHub, das den Kontext hinter dem TODO beschreibt, und stellen Sie genügend Hintergrund zur Verfügung, damit ein anderer Mitwirkender den ToDO verstehen und dann beheben kann.
2. Verweisen Sie in der Dokumentation auf die Problem-URL in der Todo-Datei.

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>Hervorgehobene Abschnitte

Um bestimmte Punkte für den Reader hervorzuheben, verwenden Sie *> [!NOTE]* , und , um die folgenden *> [!WARNING]* *> [!IMPORTANT]* Stile zu erzeugen. Es wird empfohlen, Hinweise für allgemeine Punkte und Warnungs-/wichtige Punkte nur für spezielle relevante Fälle zu verwenden.

> [!NOTE]
> Beispiel für eine Notiz

> [!WARNING]
> Beispiel für eine Warnung

> [!IMPORTANT]
> Beispiel für einen wichtigen Kommentar

## <a name="page-layout"></a>Seitenlayout

### <a name="introduction"></a>Einführung

Der Teil direkt nach dem Haupttitel des Kapitels sollte als kurze Einführung in das Kapitel dienen. Lassen Sie dies nicht zu lang, sondern fügen Sie untergeordnete Überschriften hinzu. Diese ermöglichen das Verknüpfen mit Abschnitten und können als Lesezeichen gespeichert werden.

### <a name="main-body"></a>Hauptteil

Verwenden Sie Zwei- und Dreiebenen-Überschriften, um den Rest zu strukturieren.

**Miniabschnitte**

Verwenden Sie eine fett formatierten Textzeile für Blöcke, die hervorgehoben werden sollten. Wir könnten dies zu einem bestimmten Zeitpunkt durch Vier-Level-Überschriften ersetzen.

### <a name="see-also-section"></a>Abschnitt "Siehe auch"

Die meisten Seiten sollten mit einem Kapitel namens *Enden. Siehe auch*. Dieses Kapitel ist einfach eine Aufzählung von Links zu Seiten, die sich auf dieses Thema beziehen. Diese Links können ggf. auch innerhalb des Seitentexts angezeigt werden, dies ist jedoch nicht erforderlich. Ebenso kann der Seitentext Links zu Seiten enthalten, die nicht mit dem Hauptthema verknüpft sind. Diese sollten nicht in der Liste *Siehe auch* enthalten sein. Ein Beispiel für die Auswahl von Links finden Sie im [Kapitel "Siehe auch".](#see-also)

## <a name="table-of-contents-toc"></a>Inhaltsverzeichnis (Toc)

Toc-Dateien werden zum Generieren der Navigationsleisten in der MRTK-github.io-Dokumentation verwendet.
Wenn eine neue Dokumentationsdatei hinzugefügt wird, stellen Sie sicher, dass in einer der toc.yml-Dateien des Dokumentationsordners ein Eintrag für diese Datei vorhanden ist. Nur in den Toc-Dateien aufgeführte Artikel werden im Navigationsbereich der Entwicklerdokumentation angezeigt. Es kann eine Toc-Datei für jeden Unterordner im Dokumentationsordner geben, die mit jeder vorhandenen Toc-Datei verknüpft werden kann, um sie dem entsprechenden Teil der Navigation als Unterabschnitt hinzuzufügen.

## <a name="style"></a>Style

### <a name="writing-style"></a>Schreibstil

Allgemeine Faustregel: Versuchen Sie, professional zu **klingen.** Dies bedeutet in der Regel, dass ein "Konversationston" vermieden wird. Versuchen Sie auch, Hyperbole und Hassalismus zu vermeiden.

1. Versuchen Sie nicht, (übermäßig) heiter zu sein.
2. Nie "I" schreiben
3. Vermeiden Sie "we". Dies kann in der Regel einfach mithilfe von "MRTK" umformuliert werden. Beispiel: "Wir unterstützen dieses Feature" -> "MRTK unterstützt dieses Feature" oder "Die folgenden Features werden unterstützt...".
4. Versuchen Sie auf ähnliche Weise, "Sie" zu vermeiden. Beispiel: "Mit dieser einfachen Änderung kann Ihr Shader konfiguriert werden!" -> "Shader können mit geringem Aufwand konfigurierbar gemacht werden."
5. Verwenden Sie keine Diskettenausdrücke.
6. Vermeiden Sie es, übermäßig aufgeregt zu klingen, da wir nichts verkaufen müssen.
7. Vermeiden Sie auf ähnliche Weise, zu drastisch zu sein. Ausrufezeichen sind selten erforderlich.

### <a name="capitalization"></a>Großbuchstaben

- Verwenden Sie **den Satzfall für Überschriften.** Ie. Großschreibung des ersten Buchstabens und der Namen, aber nichts anderes.
- Verwenden Sie reguläres Englisch für alles andere. Dies **bedeutet, dass keine beliebigen Wörter großgeschrieben werden,** auch wenn sie in diesem Kontext eine besondere Bedeutung haben. Bevorzugen Sie *italischen Text* zum Hervorheben bestimmter Wörter, [siehe unten](#emphasis-and-highlighting).
- Wenn ein Link in einen Satz eingebettet ist (dies ist die bevorzugte Methode), verwendet der Standardkapitelname immer Großbuchstaben, wodurch die Regel der nicht willkürlichen Großschreibung innerhalb des Texts bricht. Verwenden Sie daher einen benutzerdefinierten Linknamen, um die Groß-/Großschreibung zu korrigieren. Hier sehen Sie beispielsweise einen Link zur Dokumentation zum [Begrenzungssteuerelement.](../features/ux-building-blocks/bounds-control.md)
- Großschreibung von Namen, z. B. *Unity.*
- Großschreibung von "Editor" beim Schreiben des *Unity-Editors NICHT.*

### <a name="emphasis-and-highlighting"></a>Hervorhebung

Es gibt zwei Möglichkeiten, Wörter hervorzuheben oder hervorzuheben, indem Sie sie fett oder kursiv gestalten. Der Effekt von fett formatiertem Text ist, dass **fetter Text ausfällt** und daher leicht bemerkt werden kann, wenn ein Textteil übersprungen wird oder sogar nur über eine Seite gescrollt wird. Fett ist hervorragend, um Ausdrücke hervorzuheben, die sich Menschen merken sollten. Verwenden Sie jedoch **nur selten fetten Text,** da er im Allgemeinen ablenkend ist.

Häufig möchte man etwas , das logisch zusammengehörig ist, "gruppiert" oder einen bestimmten Begriff hervorheben, da er eine besondere Bedeutung hat. Solche Dinge müssen nicht aus dem gesamten Text herausstehen. Verwenden Sie italischen Text als einfache *Methode, um* etwas hervorzuheben.

Wenn ein Dateiname, ein Pfad oder ein Menüeintrag im Text erwähnt wird, bevorzugen Sie es, es kursalisch zu machen, um ihn logisch zu gruppieren, ohne ablenkend zu sein.

Versuchen Sie im Allgemeinen, unnötige **Texthervorhebungen zu vermeiden.** Spezielle Begriffe können einmal hervorgehoben werden, um den Leser darauf aufmerksam zu machen. Wiederholen Sie diese Hervorhebungen nicht im gesamten Text, wenn sie keinen Zweck mehr erfüllen und nur abgelenkt sind.

### <a name="mentioning-menu-entries"></a>Erwähnen von Menüeinträgen

Wenn ein Benutzer auf einen Menüeintrag klickt, gilt die aktuelle *Konvention: Project > Files > Create > Leaf*

### <a name="links"></a>Links

Fügen Sie so viele nützliche Links wie möglich zu anderen Seiten ein, aber jeder Link nur einmal. Angenommen, ein Leser klickt auf jeden Link auf der Seite und überlegen, wie lästig es wäre, wenn dieselbe Seite 20 Mal geöffnet wird.

Links bevorzugen, die in einen Satz eingebettet sind:

- BAD: Richtlinien sind nützlich. Weitere [Informationen finden Sie](../contributing/documentation-guide.md) in diesem Kapitel.
- GUT: [Richtlinien](documentation-guide.md) sind nützlich.

Vermeiden Sie externe Links. Sie können veraltet sein oder urheberrechtlich geschützte Inhalte enthalten.

Wenn Sie einen Link hinzufügen, überlegen Sie, ob er auch im Abschnitt [Siehe auch aufgeführt werden](#see-also) soll. Überprüfen Sie auf ähnliche Weise, ob ein Link zur neuen Seite der Seite mit Verknüpfter Seite hinzugefügt werden soll.

### <a name="images--screenshots"></a>Bilder/Screenshots

**Verwenden Sie Screenshots mit Sparendem.** Das Verwalten von Bildern in der Dokumentation ist eine menge Arbeit, kleine Änderungen an der Benutzeroberfläche können viele Screenshots veraltet machen. Die folgenden Regeln verringern den Wartungsaufwand:

1. Verwenden Sie keine Screenshots für Dinge, die in Text beschrieben werden können. Erstellen **Sie insbesondere niemals einen Screenshot eines Eigenschaftenrasters,** um nur Eigenschaftennamen und -werte zu zeigen.
2. Schließen Sie keine Dinge in einen Screenshot ein, die für das Angezeigte irrelevant sind. Wenn z. B. ein Renderingeffekt angezeigt wird, erstellen Sie einen Screenshot des Viewports, schließen Sie jedoch alle benutzeroberflächen um ihn herum aus. Wenn Sie eine Benutzeroberfläche anzeigen, versuchen Sie, Fenster so zu verschieben, dass nur dieser wichtige Teil im Bild zu sehen ist.
3. Wenn Sie die Screenshot-Benutzeroberfläche einschließen, zeigen Sie nur die wichtigen Teile an. Wenn Sie z. B. über Schaltflächen in einer Symbolleiste sprechen, erstellen Sie ein kleines Bild, das die wichtigen Symbolleistenschaltflächen anzeigt, aber alles um sie herum ausschließt.
4. Verwenden Sie nur Bilder, die einfach zu reproduzieren sind. Das bedeutet, dass Sie keine Marker oder Hervorhebungen in Screenshots zeichnen. Erstens gibt es keine konsistenten Regeln, wie diese aussehen sollten. Zweitens ist das Reproduzieren eines solchen Screenshots ein zusätzlicher Aufwand. Beschreiben Sie stattdessen die wichtigen Teile im Text. Es gibt Ausnahmen von dieser Regel, aber sie sind selten.
5. Natürlich ist es viel aufwendiger, ein animiertes GIF neu zu erstellen. Erwarten Sie, dass sie bis zum Ende der Zeit neu erstellt werden soll, oder erwarten Sie, dass Personen sie auslösen, wenn sie diese Zeit nicht aufwenden möchten.
6. Halten Sie die Anzahl der Bilder in einem Artikel gering. Häufig ist es eine gute Methode, einen Gesamtscreenshot eines Tools zu erstellen, das alles zeigt, und dann den Rest im Text zu beschreiben. Dies erleichtert das Ersetzen des Screenshots bei Bedarf.

Einige andere Aspekte:

- Die Editor-Benutzeroberfläche für Screenshots sollte den hellgrauen Design-Editor verwenden, da nicht alle Benutzer Zugriff auf das dunkle Design haben und wir die Dinge so konsistent wie möglich halten möchten.
- Die Standardbildbreite beträgt 500 Pixel, da dies auf den meisten Monitoren gut angezeigt wird. Versuchen Sie nicht, zu stark davon zu abweichen. Eine Breite von 800 Pixeln sollte das Maximum sein.
- Verwenden Sie PNGs für Screenshots der Benutzeroberfläche.
- Verwenden Sie PNGs oder JPGs für 3D-Viewport-Screenshots. Qualität gegenüber Komprimierungsverhältnis bevorzugen.

### <a name="list-of-component-properties"></a>Liste der Komponenteneigenschaften

Verwenden Sie beim Dokumentieren einer Liste von Eigenschaften fett formatierten Text, um den Eigenschaftsnamen hervorzuheben, und beschreiben Sie sie dann mit Zeilenumbrüchen und regulärem Text. Verwenden Sie keine Unter- oder Aufzählungszeichen.

Vergessen Sie auch nicht, alle Sätze mit einem Zeitraum zu beenden.

## <a name="page-completion-checklist"></a>Checkliste für den Seitenabschluss

1. Stellen Sie sicher, dass die Richtlinien dieses Dokuments eingehalten wurden.
1. Durchsuchen Sie die Dokumentstruktur, und sehen Sie sich an, ob das neue Dokument im Abschnitt [Siehe auch](#see-also) auf anderen Seiten erwähnt werden könnte.
1. Falls verfügbar, sollten Sie eine Person mit Kenntnissen des Themas "Proof-Read" auf der Seite auf technische Richtigkeit prüfen lassen.
1. Sie müssen die Seite für Stil und Formatierung lesen. Dies kann jemand sein, der mit dem Thema nicht vertraut ist. Dies ist auch eine gute Idee, um Feedback darüber zu erhalten, wie verständlich die Dokumentation ist.

## <a name="source-documentation"></a>Quelldokumentation

Die API-Dokumentation wird automatisch aus den MRTK-Quelldateien generiert. Um dies zu vereinfachen, müssen Quelldateien Folgendes enthalten:

- [Klassen-, Struktur- und Enumerationszusammenfassungsblöcke](#class-struct-enum-summary-blocks)
- [Eigenschaft, Methode, Ereigniszusammenfassungsblöcke](#property-method-event-summary-blocks)
- [Featureeinführungsversion und Abhängigkeiten](#feature-introduction-version-and-dependencies)
- [Serialisierte Felder](#serialized-fields)
- [Enumerationswerte](#enumeration-values)

Darüber hinaus sollte der Code gut kommentiert werden, um Wartung, Fehlerbehebungen und eine einfache Anpassung zu ermöglichen.

### <a name="class-struct-enum-summary-blocks"></a>Klassen-, Struktur- und Enumerationszusammenfassungsblöcke

Wenn dem MRTK eine Klasse, Struktur oder Enumeration hinzugefügt wird, muss ihr Zweck beschrieben werden. Dies erfolgt in Form eines Zusammenfassungsblocks über der -Klasse.

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

Wenn Abhängigkeiten auf Klassenebene vorhanden sind, sollten sie in einem Hinweisblock direkt unterhalb der Zusammenfassung dokumentiert werden.

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

Pull Requests, die ohne Zusammenfassungen für Klassen, Strukturen oder Enumerationen übermittelt werden, werden nicht genehmigt.

### <a name="property-method-event-summary-blocks"></a>Eigenschaften-, Methoden- und Ereigniszusammenfassungsblöcke

Eigenschaften, Methoden und Ereignisse (PMEs) sowie Felder müssen unabhängig von der Codesichtbarkeit (öffentlich, privat, geschützt und intern) mit Zusammenfassungsblöcken dokumentiert werden. Das Tool zur Dokumentationsgenerierung ist für das Herausfiltern und Veröffentlichen nur der öffentlichen und geschützten Features verantwortlich.

HINWEIS: Ein Zusammenfassungsblock ist für Unity-Methoden **nicht** erforderlich (z. B. "Aktualisieren", "Starten", "Aktualisieren").

Die PME-Dokumentation ist **erforderlich,** damit ein Pull Request genehmigt werden kann.

Als Teil eines PME-Zusammenfassungsblocks sind die Bedeutung und der Zweck von Parametern und zurückgegebenen Daten erforderlich.

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>Featureeinführungsversion und Abhängigkeiten

Im Rahmen der API-Zusammenfassungsdokumentation sollten Informationen zur MRTK-Version, in der das Feature eingeführt wurde, und alle Abhängigkeiten in einem Hinweisblock dokumentiert werden.

Abhängigkeiten sollten Erweiterungs- und/oder Plattformabhängigkeiten enthalten.

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>Serialisierte Felder

Es ist eine bewährte Methode, das ToolTip-Attribut von Unity zu verwenden, um Laufzeitdokumentation für die Felder eines Skripts im Inspektor bereitzustellen.

Damit Konfigurationsoptionen in der API-Dokumentation enthalten sind, müssen Skripts *mindestens* den QuickInfo-Inhalt in einen Zusammenfassungsblock einschließen.

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>Enumerationswerte

Beim Definieren und Aufzählen muss code auch die Bedeutung der Enumerationswerte mithilfe eines Zusammenfassungsblocks dokumentieren. Anmerkungsblöcke können optional verwendet werden, um zusätzliche Details bereitzustellen, um das Verständnis zu verbessern.

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>Dokumentation zur Vorgehensweise

Viele Benutzer des Mixed Reality Toolkits müssen die API-Dokumentation möglicherweise nicht verwenden. Diese Benutzer nutzen unsere vorgefertigten, wiederverwendbaren Prefabs und Skripts, um ihre Erfahrungen zu erstellen.

Jeder Featurebereich enthält eine oder mehrere Markdowndateien (MD), die auf einer relativ hohen Ebene beschreiben, was bereitgestellt wird. Abhängig von der Größe und/oder Komplexität eines bestimmten Featurebereichs sind möglicherweise zusätzliche Dateien erforderlich, bis zu einer pro bereitgestellter Funktion.

Wenn ein Feature hinzugefügt wird (oder die Nutzung geändert wird), muss eine Übersichtsdokumentation bereitgestellt werden.

Im Rahmen dieser Dokumentation sollten Anleitungsabschnitte, einschließlich Abbildungen, bereitgestellt werden, um Kunden zu helfen, die noch nicht mit einem Feature oder Konzept bei den ersten Schritte begonnen haben.

## <a name="design-documentation"></a>Entwurfsdokumentation

Mixed Reality bietet die Möglichkeit, völlig neue Welten zu schaffen. Ein Teil davon ist wahrscheinlich die Erstellung von benutzerdefinierten Ressourcen für die Verwendung mit dem MRTK. Damit dies für Kunden so reibungslos wie möglich ist, sollten Komponenten eine Entwurfsdokumentation bereitstellen, in der alle Formatierungs- oder anderen Anforderungen für Diess-Objekte beschrieben werden.

Einige Beispiele, in denen die Entwurfsdokumentation hilfreich sein kann:

- Cursormodelle
- Visualisierungen der räumlichen Zuordnung
- Soundeffektdateien

Diese Art von Dokumentation wird **dringend** empfohlen und **kann** im Rahmen einer Pull Request-Überprüfung angefordert werden.

Dies kann sich von der Entwurfsempfehlung auf der [MS Developer-Website unterscheiden.](/windows/mixed-reality/design)

## <a name="performance-notes"></a>Leistungshinweise

Einige wichtige Features sind mit Leistungskosten ausgestattet. Häufig hängt dieser Code davon ab, wie sie konfiguriert sind.

Beispiel:

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

Leistungshinweise werden für CPU- und/oder  GPU-komponenten empfohlen und können im Rahmen einer Pull Request-Überprüfung angefordert werden. Alle anwendbaren Leistungshinweise müssen in der API- und **Übersichtsdokumentation** enthalten sein.

## <a name="breaking-changes"></a>Aktuelle Änderungen

Die Dokumentation zu Breaking Changes besteht aus einer Datei der obersten [Ebene,](../contributing/breaking-changes.md) die mit den einzelnen Features der einzelnen Breaking-changes.md.

Der Featurebereich breaking-changes.md Dateien enthält die Liste aller bekannten Breaking Changes  für ein bestimmtes Release sowie den Verlauf der Breaking Changes aus früheren Releases.

Beispiel:

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

Die informationen, die in den Breaking-changes.md enthalten sind, werden in den Versionshinweisen für jedes neue MRTK-Release aggregiert.

Alle Breaking Changes, die Teil einer Änderung **sind,** müssen als Teil eines Pull Requests dokumentiert werden.

## <a name="tools-for-editing-markdown"></a>Tools zum Bearbeiten von MarkDown

[Visual Studio Code](https://code.visualstudio.com/) ist ein hervorragendes Tool zum Bearbeiten von Markdowndateien, die Teil der MRTK-Dokumentation sind.

Beim Schreiben der Dokumentation wird auch dringend empfohlen, die folgenden beiden Erweiterungen zu installieren:

- Docs Markdown-Erweiterung für Visual Studio Code: Verwenden Sie ALT+M, um ein Menü mit Dokumenterstellungsoptionen zu öffnen.

- Rechtschreibprüfung für Code: Falsch geschriebene Wörter werden unterstrichen. Klicken Sie mit der rechten Maustaste auf ein falsch geschriebenes Wort, um es zu ändern oder im Wörterbuch zu speichern.

Beides ist im von Microsoft veröffentlichten Docs Authoring Pack enthalten.

## <a name="see-also"></a>Weitere Informationen 

* [Beispiellink](https://www.google.com)