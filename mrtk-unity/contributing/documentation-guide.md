---
title: Dokumentationsrichtlinien
description: Dokumentationsrichtlinien und -standards für das MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: aa583876d4ca9e115d4ea4507638eebab838207230693cb7c24b781d8f0b020b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210720"
---
# <a name="documentation-guidelines"></a>Dokumentationsrichtlinien

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

In diesem Dokument werden die Dokumentationsrichtlinien und -standards für das Mixed Reality Toolkit (MRTK) beschrieben. Dies bietet eine Einführung in technische Aspekte des Schreibens und Erstellens von Dokumentation, um häufige Fallstricke hervorzuheben und den empfohlenen Schreibstil zu beschreiben.

Die Seite selbst sollte als Beispiel dienen, daher verwendet sie den beabsichtigten Stil und die gängigsten Markupfeatures der Dokumentation.

- [Quelle](#source-documentation)
- [How-to](#how-to-documentation)
- [Design](#design-documentation)
- [Leistungshinweise](#performance-notes)
- [Wichtige Änderungen](#breaking-changes)

---

## <a name="functionality-and-markup"></a>Funktionalität und Markup

In diesem Abschnitt werden häufig benötigte Features beschrieben. Sehen Sie sich den Quellcode der Seite an, um zu sehen, wie sie funktionieren.

1. Nummerierte Listen
   1. Geschachtelte nummerierte Listen mit mindestens drei führenden Leerzeichen
   1. Die tatsächliche Zahl im Code ist irrelevant. Die Analyse sorgt für das Festlegen der richtigen Elementnummer.

- Aufzählungen
  - Geschachtelte Aufzählungen
- Fett **formatierten** Text \* \* mit doppeltem Sternchen\*\*
- _Italischer Text_ *mit* \_ Unterstrich oder \_ \* einzelnem Sternchen\*
- Text `highlighted as code` innerhalb eines Satzes \` mitHilfe von Backquotes\`
- Links zu Dokumentationsseiten [MRTK-Dokumentationsrichtlinien](documentation-guide.md)
- Links zu [Ankern innerhalb einer Seite;](#style) Anker werden gebildet, indem Leerzeichen durch Bindestriche ersetzt und in Kleinbuchstaben konvertiert werden.

Für Codebeispiele verwenden wir die Blöcke mit drei Backticks und geben \` \` \` *csharp* als Sprache für die Syntaxhervorhebung an:

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

Wenn Code in einem Satz erwähnt `use a single backtick` wird.

### <a name="todos"></a>Todos

Vermeiden Sie die Verwendung von TODOs in Dokumentationen, da diese TODOs (z. B. Code-TODOs) im Laufe der Zeit dazu tendieren, sich anzusammeln und Informationen darüber zu erhalten, wie sie aktualisiert werden sollten und warum verloren geht.

Wenn das Hinzufügen eines ToDO unbedingt erforderlich ist, führen Sie die folgenden Schritte aus:

1. Erstellen Sie auf Github ein neues Problem, in dem der Kontext hinter dem TODO beschrieben wird, und stellen Sie genügend Hintergrundinformationen zur Verfügung, die ein anderer Mitwirkender verstehen und dann das TODO beheben kann.
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

Die meisten Seiten sollten mit einem Kapitel namens *Siehe auch enden.* Dieses Kapitel ist einfach eine Aufzählung von Links zu Seiten, die sich auf dieses Thema bezieht. Diese Links werden möglicherweise auch im Seitentext angezeigt, dies ist jedoch nicht erforderlich. Ebenso kann der Seitentext Links zu Seiten enthalten, die nicht mit dem Hauptthema verknüpft sind. Diese sollten nicht in der Liste *Siehe auch enthalten* sein. Im [Kapitel "Siehe auch"](#see-also) dieser Seite finden Sie ein Beispiel für die Auswahl von Links.

## <a name="table-of-contents-toc"></a>Inhaltsverzeichnis (Inhaltsverzeichnis)

Toc-Dateien werden zum Generieren der Navigationsleisten in der MRTK-Dokumentation github.io verwendet.
Wenn eine neue Dokumentationsdatei hinzugefügt wird, stellen Sie sicher, dass in einer der dateien toc.yml des Dokumentationsordners ein Eintrag für diese Datei enthalten ist. Nur Artikel, die in den Toc-Dateien aufgeführt sind, werden in der Navigation der Entwickler-Dokumentation angezeigt. Es kann eine Toc-Datei für jeden Unterordner im Dokumentationsordner vorhanden sein, die mit einer vorhandenen Toc-Datei verknüpft werden kann, um sie als Unterabschnitt zum entsprechenden Teil der Navigation hinzuzufügen.

## <a name="style"></a>Style

### <a name="writing-style"></a>Schreibstil

Allgemeine Faustregel: Versuchen Sie, professionelle **zu klingt.** Dies bedeutet in der Regel, einen "Konversationston" zu vermeiden. Versuchen Sie auch, Hyperbole und Zierlichkeiten zu vermeiden.

1. Versuchen Sie nicht, (zu viel) zu sein.
2. Schreiben Sie nie "I".
3. Vermeiden Sie "we". Dies kann in der Regel einfach mithilfe von "MRTK" umformuliert werden. Beispiel: "Wir unterstützen dieses Feature" -> "MRTK unterstützt dieses Feature" oder "die folgenden Features werden unterstützt...".
4. Versuchen Sie auf ähnliche Weise, "Sie" zu vermeiden. Beispiel: "Mit dieser einfachen Änderung wird Ihr Shader konfigurierbar!" -> "Shader können mit wenig Aufwand konfigurierbar gemacht werden."
5. Verwenden Sie keine "schrägen Ausdrücke".
6. Vermeiden Sie es, zu aufgeregt zu klingen, da wir nichts verkaufen müssen.
7. Vermeiden Sie ebenso, zu drastisch zu sein. Ausrufezeichen werden selten benötigt.

### <a name="capitalization"></a>Großbuchstaben

- Verwenden **Sie satzfall für Überschriften.** Ie. Großbuchstaben und Namen, aber nichts anderes.
- Verwenden Sie für alles andere reguläres Englisch. Das **bedeutet, dass sie keine beliebigen Wörter groß** machen, auch wenn sie in diesem Kontext eine besondere Bedeutung haben. Bevorzugen *Sie italischen Text zum* Hervorheben bestimmter Wörter, siehe [unten.](#emphasis-and-highlighting)
- Wenn ein Link in einen Satz eingebettet ist (dies ist die bevorzugte Methode), verwendet der Standardname des Kapitels immer Großbuchstaben, wodurch die Regel der nicht willkürlichen Groß-/Kleinbuchstaben im Text verletzt wird. Verwenden Sie daher einen benutzerdefinierten Linknamen, um die Groß-/A-Groß-/Groß-/A-Setzung zu korrigieren. Hier finden Sie beispielsweise einen Link zur Dokumentation [zur Begrenzungssteuerung.](../features/ux-building-blocks/bounds-control.md)
- Groß-/Groß-/Großnamen, z. *B. Unity.*
- Großschreiben Sie "Editor" NICHT, wenn Sie *den Unity-Editor schreiben.*

### <a name="emphasis-and-highlighting"></a>Hervorhebung und Hervorhebung

Es gibt zwei Möglichkeiten, Wörter hervorzuheben oder hervorzuheben, um sie fett zu formatieren oder sie italisch zu machen. Der Effekt von fett  formatiertem Text ist, dass fetter Text nicht angezeigt wird und daher leicht bemerkt werden kann, wenn ein Textteil übersprungen oder sogar einfach über eine Seite gescrollt wird. Fett ist sehr gut, um Ausdrücke hervorzuheben, die sich die Menschen merken sollten. Verwenden Sie **fett formatierten Text jedoch selten,** da dies im Allgemeinen abgelenkt ist.

Häufig möchte man etwas , das logisch zusammengehörig ist, "gruppiert" oder einen bestimmten Begriff hervorheben, da er eine besondere Bedeutung hat. Solche Dinge müssen sich nicht vom gesamten Text abhingen. Verwenden Sie italischen Text als einfache *Methode, um* etwas hervorzuheben.

Wenn ein Dateiname, ein Pfad oder ein Menüeintrag im Text erwähnt wird, bevorzugen Sie es, es kursalisch zu machen, um ihn logisch zu gruppieren, ohne ablenkend zu sein.

Versuchen Sie im Allgemeinen, unnötige **Texthervorhebungen zu vermeiden.** Spezielle Begriffe können einmal hervorgehoben werden, um den Leser darauf aufmerksam zu machen. Wiederholen Sie diese Hervorhebung nicht im gesamten Text, wenn sie keinen Zweck mehr erfüllt und nur abgelenkt ist.

### <a name="mentioning-menu-entries"></a>Erwähnen von Menüeinträgen

Wenn ein Benutzer auf einen Menüeintrag klickt, gilt die aktuelle *Konvention:* Project > Files > Create > Leaf

### <a name="links"></a>Links

Fügen Sie so viele nützliche Links wie möglich zu anderen Seiten ein, aber jeder Link nur einmal. Angenommen, ein Leser klickt auf jeden Link auf der Seite und überlegen, wie lästig es wäre, wenn dieselbe Seite 20 Mal geöffnet wird.

Links bevorzugen, die in einen Satz eingebettet sind:

- BAD: Richtlinien sind nützlich. Weitere [Informationen finden Sie](../contributing/documentation-guide.md) in diesem Kapitel.
- GUT: [Richtlinien](documentation-guide.md) sind nützlich.

Vermeiden Sie externe Links. Sie können veraltet sein oder urheberrechtlich geschützte Inhalte enthalten.

Wenn Sie einen Link hinzufügen, überlegen Sie, ob er auch im Abschnitt [Siehe auch aufgeführt werden](#see-also) soll. Überprüfen Sie auf ähnliche Weise, ob ein Link zur neuen Seite zur Verknüpften Seite hinzugefügt werden soll.

### <a name="images--screenshots"></a>Bilder/Screenshots

**Verwenden Sie Screenshots mit Sparendem.** Das Verwalten von Bildern in der Dokumentation ist eine menge Arbeit, kleine Änderungen an der Benutzeroberfläche können viele Screenshots veraltet machen. Die folgenden Regeln verringern den Wartungsaufwand:

1. Verwenden Sie keine Screenshots für Dinge, die im Text beschrieben werden können. Insbesondere sollten **Sie niemals einen Screenshot eines Eigenschaftenrasters** erstellen, um nur Eigenschaftsnamen und -werte zu zeigen.
2. Schließen Sie keine Dinge in einen Screenshot ein, die für das Angezeigte irrelevant sind. Wenn z. B. ein Renderingeffekt angezeigt wird, erstellen Sie einen Screenshot des Viewports, aber schließen Sie alle benutzeroberflächen um ihn herum aus. Wenn Sie einige Benutzeroberflächen anzeigen, versuchen Sie, Fenster so zu verschieben, dass nur dieser wichtige Teil im Bild zu finden ist.
3. Wenn Sie die Screenshotbenutzeroberfläche verwenden, zeigen Sie nur die wichtigen Teile an. Wenn Sie beispielsweise über Schaltflächen in einer Symbolleiste sprechen, erstellen Sie ein kleines Bild, das die wichtigen Symbolleistenschaltflächen zeigt, aber schließen Sie alles um sie herum aus.
4. Verwenden Sie nur Bilder, die leicht zu reproduzieren sind. Das bedeutet, dass Sie keine Marker oder Highlights in Screenshots zeichnen. Erstens gibt es keine konsistenten Regeln, wie diese ohnehin aussehen sollten. Zweitens ist die Reproduktion eines solchen Screenshots ein zusätzlicher Aufwand. Beschreiben Sie stattdessen die wichtigen Teile im Text. Es gibt Ausnahmen von dieser Regel, aber sie sind selten.
5. Natürlich ist es viel schwieriger, ein animiertes GIF neu zu erstellen. Erwarten Sie, dass Sie dafür verantwortlich sind, sie bis zum Ende der Zeit neu zu erstellen, oder erwarten Sie, dass Dies von Denkverlangen wird, wenn sie diese Zeit nicht verbringen möchten.
6. Halten Sie die Anzahl der Bilder in einem Artikel niedrig. Häufig ist es eine gute Methode, einen allgemeinen Screenshot eines Tools zu erstellen, das alles zeigt, und dann den Rest im Text zu beschreiben. Dadurch kann der Screenshot bei Bedarf problemlos ersetzt werden.

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
1. Sie müssen die Seite für Stil und Formatierung lesen. Dies kann jemand sein, der mit dem Thema nicht vertraut ist. Dies ist auch eine gute Idee, feedback zu erhalten, wie verständlich die Dokumentation ist.

## <a name="source-documentation"></a>Quelldokumentation

Die API-Dokumentation wird automatisch aus den MRTK-Quelldateien generiert. Um dies zu vereinfachen, müssen Quelldateien Folgendes enthalten:

- [Klassen-, Struktur- und Aufzählzusammenfassungsblöcke](#class-struct-enum-summary-blocks)
- [Eigenschaften-, Methoden- und Ereigniszusammenfassungsblöcke](#property-method-event-summary-blocks)
- [Einführungsversion und Abhängigkeiten von Features](#feature-introduction-version-and-dependencies)
- [Serialisierte Felder](#serialized-fields)
- [Enumerationswerte](#enumeration-values)

Darüber hinaus sollte der Code gut kommentiert werden, um Wartung, Fehlerbehebungen und einfache Anpassungen zu ermöglichen.

### <a name="class-struct-enum-summary-blocks"></a>Klassen-, Struktur- und Aufzählzusammenfassungsblöcke

Wenn eine Klasse, Struktur oder Enum dem MRTK hinzugefügt wird, muss ihr Zweck beschrieben werden. Dies ist in Form eines Zusammenfassungsblocks oberhalb der -Klasse.

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

Wenn Abhängigkeiten auf Klassenebene vorhanden sind, sollten sie in einem Hinweiseblock unmittelbar unterhalb der Zusammenfassung dokumentiert werden.

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

Pull Requests, die ohne Zusammenfassungen für Klassen, Strukturen oder Aufzählen übermittelt werden, werden nicht genehmigt.

### <a name="property-method-event-summary-blocks"></a>Eigenschaften-, Methoden- und Ereigniszusammenfassungsblöcke

Eigenschaften, Methoden und Ereignisse (PMEs) sowie Felder müssen mit Zusammenfassungsblöcken dokumentiert werden, unabhängig von der Codesichtbarkeit (öffentlich, privat, geschützt und intern). Das Tool zur Dokumentationsgenerierung ist für das Herausfiltern und Veröffentlichen nur der öffentlichen und geschützten Features verantwortlich.

HINWEIS: Ein Zusammenfassungsblock ist **für** Unity-Methoden nicht erforderlich (z. B. "Weck", "Start", "Aktualisieren").

Die PME-Dokumentation **ist erforderlich,** damit ein Pull Request genehmigt wird.

Im Rahmen eines PME-Zusammenfassungsblocks ist die Bedeutung und der Zweck von Parametern und zurückgegebenen Daten erforderlich.

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>Einführungsversion und Abhängigkeiten von Features

Als Teil der API-Zusammenfassungsdokumentation sollten Informationen zur MRTK-Version, in der das Feature eingeführt wurde, und alle Abhängigkeiten in einem Hinweiseblock dokumentiert werden.

Abhängigkeiten sollten Erweiterungs- und/oder Plattformabhängigkeiten umfassen.

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>Serialisierte Felder

Es ist eine bewährte Methode, das Tooltip-Attribut von Unity zu verwenden, um Laufzeitdokumentation für die Felder eines Skripts im Inspektor zur Verfügung zu stellen.

Damit Konfigurationsoptionen in der API-Dokumentation enthalten sind, müssen Skripts mindestens den QuickInfo-Inhalt in einem Zusammenfassungsblock enthalten. 

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>Enumerationswerte

Beim Definieren von und Enumeration muss der Code auch die Bedeutung der Enumerationswerte mithilfe eines Zusammenfassungsblocks dokumentieren. Hinweiseblöcke können optional verwendet werden, um zusätzliche Details zur Verbesserung des Verständnisses zur Verfügung zu stellen.

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>Dokumentation mit Anleitung

Viele Benutzer des Mixed Reality Toolkits müssen die API-Dokumentation möglicherweise nicht verwenden. Diese Benutzer nutzen unsere vorgefertigten, wiederverwendbaren Prefabs und Skripts, um ihre Erfahrungen zu erstellen.

Jeder Funktionsbereich enthält eine oder mehrere Markdowndateien (MD), die auf relativ hoher Ebene beschreiben, was bereitgestellt wird. Je nach Größe und/oder Komplexität eines bestimmten Funktionsbereichs kann es notwendig sein, zusätzliche Dateien bis zu einer pro bereitgestellten Funktion zu benötigen.

Wenn ein Feature hinzugefügt wird (oder die Nutzung geändert wird), muss eine Übersichtsdokumentation bereitgestellt werden.

Im Rahmen dieser Dokumentation sollten Abschnitte mit Einer-Hilfe,einschließlich Abbildungen, bereitgestellt werden, um Kunden bei den ersten Schritte mit einem Feature oder Konzept zu unterstützen.

## <a name="design-documentation"></a>Entwurfsdokumentation

Mixed Reality bietet die Möglichkeit, völlig neue Welten zu erstellen. Ein Teil davon ist wahrscheinlich die Erstellung benutzerdefinierter Ressourcen für die Verwendung mit dem MRTK. Um dies für Kunden so reibungslos wie möglich zu gestalten, sollten Komponenten eine Entwurfsdokumentation bereitstellen, in der formatierungs- oder andere Anforderungen an Diesartwerte beschrieben werden.

Einige Beispiele, in denen die Entwurfsdokumentation hilfreich sein kann:

- Cursormodelle
- Visualisierungen der räumlichen Zuordnung
- Soundeffektdateien

Diese Art von Dokumentation wird **dringend** empfohlen und **kann im** Rahmen einer Pull Request-Überprüfung angefordert werden.

Dies kann sich von der Entwurfsempfehlung auf der [MS Developer-Website unterscheiden.](/windows/mixed-reality/design)

## <a name="performance-notes"></a>Leistungshinweise

Einige wichtige Features sind mit Leistungskosten ausgestattet. Häufig hängt dieser Code davon ab, wie er konfiguriert ist.

Beispiel:

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

Leistungshinweise werden für CPU- und/oder  GPU-komponenten empfohlen und können im Rahmen einer Pull Request-Überprüfung angefordert werden. Alle anwendbaren Leistungshinweise müssen in der **API- und** Übersichtsdokumentation enthalten sein.

## <a name="breaking-changes"></a>Aktuelle Änderungen

Die Dokumentation zu Breaking Changes besteht aus einer [Datei](../contributing/breaking-changes.md) der obersten Ebene, die mit den einzelnen breaking-changes.md jedes Featurebereichs verknüpft ist.

Der Funktionsbereich breaking-changes.md Dateien enthält die Liste aller bekannten Breaking Changes für ein bestimmtes Release **sowie** den Verlauf der Breaking Changes aus früheren Releases.

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

Die Informationen auf Featureebene breaking-changes.md Dateien werden in den Versionshinweisen für jedes neue MRTK-Release aggregiert.

Alle Breaking Changes, die Teil einer Änderung sind, **müssen** als Teil eines Pull Requests dokumentiert werden.

## <a name="tools-for-editing-markdown"></a>Tools zum Bearbeiten von MarkDown

[Visual Studio Code](https://code.visualstudio.com/) ist ein hervorragendes Tool zum Bearbeiten von Markdowndateien, die Teil der MRTK-Dokumentation sind.

Beim Schreiben der Dokumentation wird auch dringend empfohlen, die folgenden beiden Erweiterungen zu installieren:

- Docs Markdown Extension for Visual Studio Code : Verwenden Sie ALT+M, um ein Menü mit Dokumenterstellungsoptionen anzuzeigen.

- Code-Rechtschreibprüfung: Falsch geschriebene Wörter werden unterstrichen. Klicken Sie mit der rechten Maustaste auf ein falsch geschriebenes Wort, um es zu ändern oder im Wörterbuch zu speichern.

Beides ist im von Microsoft veröffentlichten Docs Authoring Pack enthalten.

## <a name="see-also"></a>Siehe auch

- [Beispiellink "siehe auch" für die Dokumentation](https://www.microsoft.com)
