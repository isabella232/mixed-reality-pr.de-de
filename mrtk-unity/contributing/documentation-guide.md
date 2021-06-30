---
title: Dokumentationsleitfaden
description: Dokumentationsrichtlinien und Standards für das MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 37233141bd43f27db47935574bac7630b8bea8d7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121388"
---
# <a name="documentation-guidelines"></a><span data-ttu-id="63137-104">Dokumentationsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="63137-104">Documentation guidelines</span></span>

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

<span data-ttu-id="63137-105">In diesem Dokument werden die Dokumentationsrichtlinien und Standards für das Mixed Reality Toolkit (MRTK) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="63137-105">This document outlines the documentation guidelines and standards for the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="63137-106">Dies bietet eine Einführung in technische Aspekte des Schreibens und Generierens von Dokumentationen, um häufige Fallstricke hervorzuheben und den empfohlenen Schreibstil zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="63137-106">This provides an introduction to technical aspects of documentation writing and generation, to highlight common pitfalls, and to describe the recommended writing style.</span></span>

<span data-ttu-id="63137-107">Die Seite selbst soll als Beispiel dienen und verwendet daher den beabsichtigten Stil und die gängigsten Markupfeatures der Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="63137-107">The page itself is supposed to serve as an example, therefore it uses the intended style and the most common markup features of the documentation.</span></span>

- [<span data-ttu-id="63137-108">Quelle</span><span class="sxs-lookup"><span data-stu-id="63137-108">Source</span></span>](#source-documentation)
- [<span data-ttu-id="63137-109">Vorgehensweise</span><span class="sxs-lookup"><span data-stu-id="63137-109">How-to</span></span>](#how-to-documentation)
- [<span data-ttu-id="63137-110">Design</span><span class="sxs-lookup"><span data-stu-id="63137-110">Design</span></span>](#design-documentation)
- [<span data-ttu-id="63137-111">Leistungshinweise</span><span class="sxs-lookup"><span data-stu-id="63137-111">Performance notes</span></span>](#performance-notes)
- [<span data-ttu-id="63137-112">Wichtige Änderungen</span><span class="sxs-lookup"><span data-stu-id="63137-112">Breaking changes</span></span>](#breaking-changes)

---

## <a name="functionality-and-markup"></a><span data-ttu-id="63137-113">Funktionalität und Markup</span><span class="sxs-lookup"><span data-stu-id="63137-113">Functionality and markup</span></span>

<span data-ttu-id="63137-114">In diesem Abschnitt werden häufig benötigte Features beschrieben.</span><span class="sxs-lookup"><span data-stu-id="63137-114">This section describes frequently needed features.</span></span> <span data-ttu-id="63137-115">Um zu sehen, wie sie funktionieren, sehen Sie sich den Quellcode der Seite an.</span><span class="sxs-lookup"><span data-stu-id="63137-115">To see how they work, look at the source code of the page.</span></span>

1. <span data-ttu-id="63137-116">Nummerierte Listen</span><span class="sxs-lookup"><span data-stu-id="63137-116">Numbered lists</span></span>
   1. <span data-ttu-id="63137-117">Geschachtelte nummerierte Listen mit mindestens 3 führenden Leerzeichen</span><span class="sxs-lookup"><span data-stu-id="63137-117">Nested numbered lists with at least 3 leading blank spaces</span></span>
   1. <span data-ttu-id="63137-118">Die tatsächliche Zahl im Code ist irrelevant. Bei der Analyse wird die richtige Elementnummer festgelegt.</span><span class="sxs-lookup"><span data-stu-id="63137-118">The actual number in code is irrelevant; parsing will take care of setting the correct item number.</span></span>

- <span data-ttu-id="63137-119">Aufzählungszeichenlisten</span><span class="sxs-lookup"><span data-stu-id="63137-119">Bullet point lists</span></span>
  - <span data-ttu-id="63137-120">Geschachtelte Aufzählungspunktlisten</span><span class="sxs-lookup"><span data-stu-id="63137-120">Nested bullet point lists</span></span>
- <span data-ttu-id="63137-121">Fett **formatiertes** Text mit \* \* doppeltem Sternchen\*\*</span><span class="sxs-lookup"><span data-stu-id="63137-121">Text in **bold** with \*\*double asterisk\*\*</span></span>
- <span data-ttu-id="63137-122">_Text_ *mit* \_ Unterstrich \_ oder \* einzelnem Sternchen\*</span><span class="sxs-lookup"><span data-stu-id="63137-122">_italic_ *text* with \_underscore\_ or \*single asterisk\*</span></span>
- <span data-ttu-id="63137-123">Text `highlighted as code` innerhalb eines Satzes mit \` Rückquotes\`</span><span class="sxs-lookup"><span data-stu-id="63137-123">Text `highlighted as code` within a sentence \`using backquotes\`</span></span>
- <span data-ttu-id="63137-124">Links zu dokumentationsseitigen [MRTK-Dokumentationsrichtlinien](documentation-guide.md)</span><span class="sxs-lookup"><span data-stu-id="63137-124">Links to docs pages [MRTK documentation guidelines](documentation-guide.md)</span></span>
- <span data-ttu-id="63137-125">Links zu [Ankern innerhalb einer Seite](#style); Anker werden gebildet, indem Leerzeichen durch Bindestriche ersetzt und in Kleinbuchstaben konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="63137-125">Links to [anchors within a page](#style); anchors are formed by replacing spaces with dashes, and converting to lowercase</span></span>

<span data-ttu-id="63137-126">Für Codebeispiele verwenden wir die Blöcke mit drei Backticks \` \` \` und geben *csharp* als Sprache für die Syntaxhervorhebung an:</span><span class="sxs-lookup"><span data-stu-id="63137-126">For code samples we use the blocks with three backticks \`\`\` and specify *csharp* as the language for syntax highlighting:</span></span>

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

<span data-ttu-id="63137-127">Wenn Code innerhalb eines Satzes erwähnt `use a single backtick` wird.</span><span class="sxs-lookup"><span data-stu-id="63137-127">When mentioning code within a sentence `use a single backtick`.</span></span>

### <a name="todos"></a><span data-ttu-id="63137-128">Todos</span><span class="sxs-lookup"><span data-stu-id="63137-128">TODOs</span></span>

<span data-ttu-id="63137-129">Vermeiden Sie die Verwendung von TODOs in der Dokumentation, da diese TODOs (z. B. Code-TODOs) im Laufe der Zeit in der Regel ansammeln und Informationen darüber sammeln, wie sie aktualisiert werden sollten und warum verloren gehen.</span><span class="sxs-lookup"><span data-stu-id="63137-129">Avoid using TODOs in docs, as over time these TODOs (like code TODOs) tend to accumulate and information about how they should be updated and why gets lost.</span></span>

<span data-ttu-id="63137-130">Wenn es unbedingt erforderlich ist, einen Todo hinzuzufügen, führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="63137-130">If it is absolutely necessary to add a TODO, follow these steps:</span></span>

1. <span data-ttu-id="63137-131">Erstellen Sie ein neues Problem auf GitHub, in dem der Kontext hinter dem TODO beschrieben wird, und stellen Sie genügend Hintergrund bereit, den ein anderer Mitwirkender verstehen und dann die TODO-Datei beheben kann.</span><span class="sxs-lookup"><span data-stu-id="63137-131">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span></span>
2. <span data-ttu-id="63137-132">Verweisen Sie in der Dokumentation im Todo auf die Problem-URL.</span><span class="sxs-lookup"><span data-stu-id="63137-132">Reference the issue URL in the todo in the docs.</span></span>

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a><span data-ttu-id="63137-133">Hervorgehobene Abschnitte</span><span class="sxs-lookup"><span data-stu-id="63137-133">Highlighted sections</span></span>

<span data-ttu-id="63137-134">Um bestimmte Punkte für den Reader hervorzuheben, verwenden Sie *> [!NOTE]* , und , um die folgenden *> [!WARNING]* *> [!IMPORTANT]* Stile zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="63137-134">To highlight specific points to the reader, use *> [!NOTE]* , *> [!WARNING]* , and *> [!IMPORTANT]* to produce the following styles.</span></span> <span data-ttu-id="63137-135">Es wird empfohlen, Hinweise für allgemeine Punkte und Warnungen/wichtige Punkte nur für spezielle relevante Fälle zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="63137-135">It is recommended to use notes for general points and warning/important points only for special relevant cases.</span></span>

> [!NOTE]
> <span data-ttu-id="63137-136">Beispiel für eine Notiz</span><span class="sxs-lookup"><span data-stu-id="63137-136">Example of a note</span></span>

> [!WARNING]
> <span data-ttu-id="63137-137">Beispiel für eine Warnung</span><span class="sxs-lookup"><span data-stu-id="63137-137">Example of a warning</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63137-138">Beispiel für einen wichtigen Kommentar</span><span class="sxs-lookup"><span data-stu-id="63137-138">Example of an important comment</span></span>

## <a name="page-layout"></a><span data-ttu-id="63137-139">Seitenlayout</span><span class="sxs-lookup"><span data-stu-id="63137-139">Page layout</span></span>

### <a name="introduction"></a><span data-ttu-id="63137-140">Einführung</span><span class="sxs-lookup"><span data-stu-id="63137-140">Introduction</span></span>

<span data-ttu-id="63137-141">Der Teil direkt nach dem Titel des Hauptkapitels sollte als kurze Einführung dienen, worum es im Kapitel geht.</span><span class="sxs-lookup"><span data-stu-id="63137-141">The part right after the main chapter title should serve as a short introduction what the chapter is about.</span></span> <span data-ttu-id="63137-142">Machen Sie dies nicht zu lang, sondern fügen Sie untergeordnete Überschriften hinzu.</span><span class="sxs-lookup"><span data-stu-id="63137-142">Do not make this too long, instead add sub headlines.</span></span> <span data-ttu-id="63137-143">Diese ermöglichen das Verknüpfen mit Abschnitten und können als Lesezeichen gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="63137-143">These allow to link to sections and can be saved as bookmarks.</span></span>

### <a name="main-body"></a><span data-ttu-id="63137-144">Haupttext</span><span class="sxs-lookup"><span data-stu-id="63137-144">Main body</span></span>

<span data-ttu-id="63137-145">Verwenden Sie Überschriften mit zwei ebenen und drei Ebenen, um den Rest zu strukturiert.</span><span class="sxs-lookup"><span data-stu-id="63137-145">Use two-level and three-level headlines to structure the rest.</span></span>

<span data-ttu-id="63137-146">**Miniabschnitte**</span><span class="sxs-lookup"><span data-stu-id="63137-146">**Mini Sections**</span></span>

<span data-ttu-id="63137-147">Verwenden Sie eine fett formatierte Textzeile für Blöcke, die hervorgehoben werden sollten. Wir könnten dies zu einem bestimmten Zeitpunkt durch Vier-Ebenen-Überschriften ersetzen.</span><span class="sxs-lookup"><span data-stu-id="63137-147">Use a bold line of text for blocks that should stand out. We might replace this by four-level headlines at some point.</span></span>

### <a name="see-also-section"></a><span data-ttu-id="63137-148">Abschnitt "Siehe auch"</span><span class="sxs-lookup"><span data-stu-id="63137-148">'See also' section</span></span>

<span data-ttu-id="63137-149">Die meisten Seiten sollten mit einem Kapitel namens *Enden. Siehe auch*.</span><span class="sxs-lookup"><span data-stu-id="63137-149">Most pages should end with a chapter called *See also*.</span></span> <span data-ttu-id="63137-150">Dieses Kapitel ist einfach eine Aufzählung von Links zu Seiten, die sich auf dieses Thema beziehen.</span><span class="sxs-lookup"><span data-stu-id="63137-150">This chapter is simply a bullet pointed list of links to pages related to this topic.</span></span> <span data-ttu-id="63137-151">Diese Links können ggf. auch innerhalb des Seitentexts angezeigt werden, dies ist jedoch nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="63137-151">These links may also appear within the page text where appropriate, but this is not required.</span></span> <span data-ttu-id="63137-152">Ebenso kann der Seitentext Links zu Seiten enthalten, die nicht mit dem Hauptthema verknüpft sind. Diese sollten nicht in der Liste *Siehe auch* enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="63137-152">Similarly, the page text may contain links to pages that are not related to the main topic, these should not be included in the *See also* list.</span></span> <span data-ttu-id="63137-153">Ein Beispiel für die Auswahl von Links finden Sie im [Kapitel "Siehe auch".](#see-also)</span><span class="sxs-lookup"><span data-stu-id="63137-153">See [this page's ''See also'' chapter](#see-also) as an example for the choice of links.</span></span>

## <a name="table-of-contents-toc"></a><span data-ttu-id="63137-154">Inhaltsverzeichnis (Toc)</span><span class="sxs-lookup"><span data-stu-id="63137-154">Table of Contents (TOC)</span></span>

<span data-ttu-id="63137-155">Toc-Dateien werden zum Generieren der Navigationsleisten in der MRTK-github.io-Dokumentation verwendet.</span><span class="sxs-lookup"><span data-stu-id="63137-155">Toc files are used for generating the navigation bars in the MRTK github.io documentation.</span></span>
<span data-ttu-id="63137-156">Wenn eine neue Dokumentationsdatei hinzugefügt wird, stellen Sie sicher, dass in einer der toc.yml-Dateien des Dokumentationsordners ein Eintrag für diese Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="63137-156">Whenever a new documentation file is added, make sure that there's an entry for that file in one of the toc.yml files of the documentation folder.</span></span> <span data-ttu-id="63137-157">Nur in den Toc-Dateien aufgeführte Artikel werden im Navigationsbereich der Entwicklerdokumentation angezeigt. Es kann eine Toc-Datei für jeden Unterordner im Dokumentationsordner geben, die mit jeder vorhandenen Toc-Datei verknüpft werden kann, um sie dem entsprechenden Teil der Navigation als Unterabschnitt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="63137-157">Only articles listed in the toc files will show up in the navigation of the developer docs. There can be a toc file for every subfolder in the documentation folder which can be linked into any existing toc file to add it as a subsection to the corresponding part of the navigation.</span></span>

## <a name="style"></a><span data-ttu-id="63137-158">Style</span><span class="sxs-lookup"><span data-stu-id="63137-158">Style</span></span>

### <a name="writing-style"></a><span data-ttu-id="63137-159">Schreibstil</span><span class="sxs-lookup"><span data-stu-id="63137-159">Writing style</span></span>

<span data-ttu-id="63137-160">Allgemeine Faustregel: Versuchen Sie, professional zu **klingen.**</span><span class="sxs-lookup"><span data-stu-id="63137-160">General rule of thumb: Try to **sound professional**.</span></span> <span data-ttu-id="63137-161">Dies bedeutet in der Regel, dass ein "Konversationston" vermieden wird.</span><span class="sxs-lookup"><span data-stu-id="63137-161">That usually means to avoid a 'conversational tone'.</span></span> <span data-ttu-id="63137-162">Versuchen Sie auch, Hyperbole und Hassalismus zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="63137-162">Also try to avoid hyperbole and sensationalism.</span></span>

1. <span data-ttu-id="63137-163">Versuchen Sie nicht, (übermäßig) heiter zu sein.</span><span class="sxs-lookup"><span data-stu-id="63137-163">Don't try to be (overly) funny.</span></span>
2. <span data-ttu-id="63137-164">Nie "I" schreiben</span><span class="sxs-lookup"><span data-stu-id="63137-164">Never write 'I'</span></span>
3. <span data-ttu-id="63137-165">Vermeiden Sie "we".</span><span class="sxs-lookup"><span data-stu-id="63137-165">Avoid 'we'.</span></span> <span data-ttu-id="63137-166">Dies kann in der Regel einfach mithilfe von "MRTK" umformuliert werden.</span><span class="sxs-lookup"><span data-stu-id="63137-166">This can usually be rephrased easily, using 'MRTK' instead.</span></span> <span data-ttu-id="63137-167">Beispiel: "Wir unterstützen dieses Feature" -> "MRTK unterstützt dieses Feature" oder "Die folgenden Features werden unterstützt...".</span><span class="sxs-lookup"><span data-stu-id="63137-167">Example: "we support this feature" -> "MRTK supports this feature" or "the following features are supported ...".</span></span>
4. <span data-ttu-id="63137-168">Versuchen Sie auf ähnliche Weise, "Sie" zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="63137-168">Similarly, try to avoid 'you'.</span></span> <span data-ttu-id="63137-169">Beispiel: "Mit dieser einfachen Änderung kann der Shader konfiguriert werden!"</span><span class="sxs-lookup"><span data-stu-id="63137-169">Example: "With this simple change your shader becomes configurable!"</span></span> <span data-ttu-id="63137-170">-> "Shader können mit geringem Aufwand konfigurierbar gemacht werden."</span><span class="sxs-lookup"><span data-stu-id="63137-170">-> "Shaders can be made configurable with little effort."</span></span>
5. <span data-ttu-id="63137-171">Verwenden Sie keine Diskettenausdrücke.</span><span class="sxs-lookup"><span data-stu-id="63137-171">Do not use 'sloppy phrases'.</span></span>
6. <span data-ttu-id="63137-172">Vermeiden Sie es, übermäßig aufgeregt zu klingen, da wir nichts verkaufen müssen.</span><span class="sxs-lookup"><span data-stu-id="63137-172">Avoid sounding overly excited, we do not need to sell anything.</span></span>
7. <span data-ttu-id="63137-173">Vermeiden Sie auf ähnliche Weise, zu drastisch zu sein.</span><span class="sxs-lookup"><span data-stu-id="63137-173">Similarly, avoid being overly dramatic.</span></span> <span data-ttu-id="63137-174">Ausrufezeichen werden selten benötigt.</span><span class="sxs-lookup"><span data-stu-id="63137-174">Exclamation marks are rarely needed.</span></span>

### <a name="capitalization"></a><span data-ttu-id="63137-175">Großbuchstaben</span><span class="sxs-lookup"><span data-stu-id="63137-175">Capitalization</span></span>

- <span data-ttu-id="63137-176">Verwenden Sie **den Satzfall für Überschriften.**</span><span class="sxs-lookup"><span data-stu-id="63137-176">Use **Sentence case for headlines**.</span></span> <span data-ttu-id="63137-177">Ie.</span><span class="sxs-lookup"><span data-stu-id="63137-177">Ie.</span></span> <span data-ttu-id="63137-178">Großschreibung des ersten Buchstabens und der Namen, aber nichts anderes.</span><span class="sxs-lookup"><span data-stu-id="63137-178">capitalize the first letter and names, but nothing else.</span></span>
- <span data-ttu-id="63137-179">Verwenden Sie reguläres Englisch für alles andere.</span><span class="sxs-lookup"><span data-stu-id="63137-179">Use regular English for everything else.</span></span> <span data-ttu-id="63137-180">Dies **bedeutet, dass keine beliebigen Wörter großgeschrieben werden,** auch wenn sie in diesem Kontext eine besondere Bedeutung haben.</span><span class="sxs-lookup"><span data-stu-id="63137-180">That means **do not capitalize arbitrary words**, even if they hold a special meaning in that context.</span></span> <span data-ttu-id="63137-181">Bevorzugen Sie *italischen Text* zum Hervorheben bestimmter Wörter, [siehe unten](#emphasis-and-highlighting).</span><span class="sxs-lookup"><span data-stu-id="63137-181">Prefer *italic text* for highlighting certain words, [see below](#emphasis-and-highlighting).</span></span>
- <span data-ttu-id="63137-182">Wenn ein Link in einen Satz eingebettet ist (dies ist die bevorzugte Methode), verwendet der Standardkapitelname immer Großbuchstaben, wodurch die Regel der nicht willkürlichen Großschreibung innerhalb des Texts bricht.</span><span class="sxs-lookup"><span data-stu-id="63137-182">When a link is embedded in a sentence (which is the preferred method), the standard chapter name always uses capital letters, thus breaking the rule of no arbitrary capitalization inside text.</span></span> <span data-ttu-id="63137-183">Verwenden Sie daher einen benutzerdefinierten Linknamen, um die Groß-/Großschreibung zu korrigieren.</span><span class="sxs-lookup"><span data-stu-id="63137-183">Therefore use a custom link name to fix the capitalization.</span></span> <span data-ttu-id="63137-184">Hier sehen Sie beispielsweise einen Link zur Dokumentation zum [Begrenzungssteuerelement.](../features/ux-building-blocks/bounds-control.md)</span><span class="sxs-lookup"><span data-stu-id="63137-184">As an example, here is a link to the [bounds control](../features/ux-building-blocks/bounds-control.md) documentation.</span></span>
- <span data-ttu-id="63137-185">Großschreibung von Namen, z. B. *Unity.*</span><span class="sxs-lookup"><span data-stu-id="63137-185">Do capitalize names, such as *Unity*.</span></span>
- <span data-ttu-id="63137-186">Großschreibung von "Editor" beim Schreiben des *Unity-Editors NICHT.*</span><span class="sxs-lookup"><span data-stu-id="63137-186">Do NOT capitalize "editor" when writing *Unity editor*.</span></span>

### <a name="emphasis-and-highlighting"></a><span data-ttu-id="63137-187">Hervorhebung</span><span class="sxs-lookup"><span data-stu-id="63137-187">Emphasis and highlighting</span></span>

<span data-ttu-id="63137-188">Es gibt zwei Möglichkeiten, Wörter hervorzuheben oder hervorzuheben, indem Sie sie fett oder kursiv gestalten.</span><span class="sxs-lookup"><span data-stu-id="63137-188">There are two ways to emphasize or highlight words, making them bold or making them italic.</span></span> <span data-ttu-id="63137-189">Der Effekt von fett formatiertem Text besteht darin, dass **fetter Text ausfällt** und daher leicht bemerkt werden kann, wenn ein Textteil übersprungen oder sogar nur über eine Seite gescrollt wird.</span><span class="sxs-lookup"><span data-stu-id="63137-189">The effect of bold text is that **bold text sticks out** and therefore can easily be noticed while skimming a piece of text or even just scrolling over a page.</span></span> <span data-ttu-id="63137-190">Fett ist hervorragend, um Ausdrücke hervorzuheben, die sich Menschen merken sollten.</span><span class="sxs-lookup"><span data-stu-id="63137-190">Bold is great to highlight phrases that people should remember.</span></span> <span data-ttu-id="63137-191">Verwenden Sie jedoch **nur selten fetten Text,** da er im Allgemeinen ablenkend ist.</span><span class="sxs-lookup"><span data-stu-id="63137-191">However, **use bold text rarely**, because it is generally distracting.</span></span>

<span data-ttu-id="63137-192">Häufig möchte man entweder etwas gruppieren, das logisch zusammen gehört, oder einen bestimmten Begriff hervorheben, da er eine besondere Bedeutung hat.</span><span class="sxs-lookup"><span data-stu-id="63137-192">Often one wants to either 'group' something that belongs logically together or highlight a specific term, because it has a special meaning.</span></span> <span data-ttu-id="63137-193">Solche Dinge müssen sich nicht aus dem Gesamttext herausstellen.</span><span class="sxs-lookup"><span data-stu-id="63137-193">Such things do not need to stand out of the overall text.</span></span> <span data-ttu-id="63137-194">Verwenden Sie italischen Text als *einfache Methode,* um etwas hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="63137-194">Use italic text as a *lightweight method* to highlight something.</span></span>

<span data-ttu-id="63137-195">Wenn ein Dateiname, ein Pfad oder ein Menüeintrag im Text erwähnt wird, bevorzugen Sie es, italisch zu machen, um ihn logisch zu gruppieren, ohne ablenkend zu sein.</span><span class="sxs-lookup"><span data-stu-id="63137-195">Similarly, when a filename, a path or a menu-entry is mentioned in text, prefer to make it italic to logically group it, without being distracting.</span></span>

<span data-ttu-id="63137-196">Versuchen Sie im Allgemeinen, **unnötige Texthervorhebungen** zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="63137-196">In general, try to **avoid unnecessary text highlighting**.</span></span> <span data-ttu-id="63137-197">Sonderbegriffe können einmal hervorgehoben werden, um den Leser darauf aufmerksam zu machen. Wiederholen Sie diese Hervorhebung nicht im gesamten Text, wenn sie keinen Zweck mehr erfüllt und nur ablenkt.</span><span class="sxs-lookup"><span data-stu-id="63137-197">Special terms can be highlighted once to make the reader aware, do not repeat such highlighting throughout the text, when it serves no purpose anymore and only distracts.</span></span>

### <a name="mentioning-menu-entries"></a><span data-ttu-id="63137-198">Erwähnen von Menüeinträgen</span><span class="sxs-lookup"><span data-stu-id="63137-198">Mentioning menu entries</span></span>

<span data-ttu-id="63137-199">Wenn sie einen Menüeintrag erwähnen, auf den ein Benutzer klicken soll, lautet die aktuelle Konvention: *Project > Files > Create > Leaf*</span><span class="sxs-lookup"><span data-stu-id="63137-199">When mentioning a menu entry that a user should click, the current convention is: *Project > Files > Create > Leaf*</span></span>

### <a name="links"></a><span data-ttu-id="63137-200">Links</span><span class="sxs-lookup"><span data-stu-id="63137-200">Links</span></span>

<span data-ttu-id="63137-201">Fügen Sie so viele nützliche Links wie möglich zu anderen Seiten ein, jedoch nur einmal.</span><span class="sxs-lookup"><span data-stu-id="63137-201">Insert as many useful links to other pages as possible, but each link only once.</span></span> <span data-ttu-id="63137-202">Angenommen, ein Leser klickt auf jeden Link auf der Seite, und denken Sie darüber nach, wie ängstlich es wäre, wenn dieselbe Seite 20 Mal geöffnet würde.</span><span class="sxs-lookup"><span data-stu-id="63137-202">Assume a reader clicks on every link in the page, and think about how annoying it would be, if the same page opens 20 times.</span></span>

<span data-ttu-id="63137-203">Links bevorzugen, die in einen Satz eingebettet sind:</span><span class="sxs-lookup"><span data-stu-id="63137-203">Prefer links embedded in a sentence:</span></span>

- <span data-ttu-id="63137-204">BAD: Richtlinien sind nützlich.</span><span class="sxs-lookup"><span data-stu-id="63137-204">BAD: Guidelines are useful.</span></span> <span data-ttu-id="63137-205">Weitere Informationen finden Sie [in diesem Kapitel.](../contributing/documentation-guide.md)</span><span class="sxs-lookup"><span data-stu-id="63137-205">See [this chapter](../contributing/documentation-guide.md) for details.</span></span>
- <span data-ttu-id="63137-206">GUT: [Richtlinien](documentation-guide.md) sind nützlich.</span><span class="sxs-lookup"><span data-stu-id="63137-206">GOOD: [Guidelines](documentation-guide.md) are useful.</span></span>

<span data-ttu-id="63137-207">Vermeiden Sie externe Links, da diese veraltet sein oder urheberrechtlich geschützte Inhalte enthalten können.</span><span class="sxs-lookup"><span data-stu-id="63137-207">Avoid external links, they can become outdated or contain copyrighted content.</span></span>

<span data-ttu-id="63137-208">Berücksichtigen Sie beim Hinzufügen eines Links, ob er auch im Abschnitt [Siehe auch](#see-also) aufgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="63137-208">When adding a link, consider whether it should also be listed in the [See also](#see-also) section.</span></span> <span data-ttu-id="63137-209">Überprüfen Sie auf ähnliche Weise, ob der Seite, mit der verknüpft wird, ein Link zur neuen Seite hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="63137-209">Similarly, check whether a link to the new page should be added to the linked-to page.</span></span>

### <a name="images--screenshots"></a><span data-ttu-id="63137-210">Bilder/Screenshots</span><span class="sxs-lookup"><span data-stu-id="63137-210">Images / screenshots</span></span>

<span data-ttu-id="63137-211">**Verwenden Sie Screenshots mit geringem Nutzen.**</span><span class="sxs-lookup"><span data-stu-id="63137-211">**Use screenshots sparingly.**</span></span> <span data-ttu-id="63137-212">Die Verwaltung von Bildern in der Dokumentation ist sehr arbeitsaufwänd, kleine Änderungen an der Benutzeroberfläche können dazu führen, dass viele Screenshots veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="63137-212">Maintaining images in documentation is a lot of work, small UI changes can make a lot of screenshots outdated.</span></span> <span data-ttu-id="63137-213">Die folgenden Regeln verringern den Wartungsaufwand:</span><span class="sxs-lookup"><span data-stu-id="63137-213">The following rules will reduce maintenance effort:</span></span>

1. <span data-ttu-id="63137-214">Verwenden Sie keine Screenshots für Dinge, die in Text beschrieben werden können.</span><span class="sxs-lookup"><span data-stu-id="63137-214">Do not use screenshots for things that can be described in text.</span></span> <span data-ttu-id="63137-215">Erstellen **Sie insbesondere niemals einen Screenshot eines Eigenschaftenrasters,** um ausschließlich Eigenschaftennamen und -werte zu zeigen.</span><span class="sxs-lookup"><span data-stu-id="63137-215">Especially, **never screenshot a property grid** for the sole purpose of showing property names and values.</span></span>
2. <span data-ttu-id="63137-216">Schließen Sie keine Dinge in einen Screenshot ein, die für das Angezeigte irrelevant sind.</span><span class="sxs-lookup"><span data-stu-id="63137-216">Do not include things in a screenshot that are irrelevant to what is shown.</span></span> <span data-ttu-id="63137-217">Wenn z. B. ein Renderingeffekt angezeigt wird, erstellen Sie einen Screenshot des Viewports, schließen Sie jedoch alle benutzeroberflächen um ihn herum aus.</span><span class="sxs-lookup"><span data-stu-id="63137-217">For instance, when a rendering effect is shown, make a screenshot of the viewport, but exclude any UI around it.</span></span> <span data-ttu-id="63137-218">Wenn Sie eine Benutzeroberfläche anzeigen, versuchen Sie, Fenster so zu verschieben, dass nur dieser wichtige Teil im Bild zu sehen ist.</span><span class="sxs-lookup"><span data-stu-id="63137-218">Showing some UI, try to move windows around such that only that important part is in the image.</span></span>
3. <span data-ttu-id="63137-219">Wenn Sie die Screenshot-Benutzeroberfläche einschließen, zeigen Sie nur die wichtigen Teile an.</span><span class="sxs-lookup"><span data-stu-id="63137-219">When including screenshot UI, only show the important parts.</span></span> <span data-ttu-id="63137-220">Wenn Sie z. B. über Schaltflächen in einer Symbolleiste sprechen, erstellen Sie ein kleines Bild, das die wichtigen Symbolleistenschaltflächen anzeigt, aber alles um sich herum ausschließt.</span><span class="sxs-lookup"><span data-stu-id="63137-220">For example, when talking about buttons in a toolbar, make a small image that shows the important toolbar buttons, but exclude everything around it.</span></span>
4. <span data-ttu-id="63137-221">Verwenden Sie nur Bilder, die einfach zu reproduzieren sind.</span><span class="sxs-lookup"><span data-stu-id="63137-221">Only use images that are easy to reproduce.</span></span> <span data-ttu-id="63137-222">Das bedeutet, dass Sie keine Marker oder Hervorhebungen in Screenshots zeichnen.</span><span class="sxs-lookup"><span data-stu-id="63137-222">That means do not paint markers or highlights into screenshots.</span></span> <span data-ttu-id="63137-223">Erstens gibt es keine konsistenten Regeln, wie diese aussehen sollten.</span><span class="sxs-lookup"><span data-stu-id="63137-223">First, there are no consistent rules how these should look, anyway.</span></span> <span data-ttu-id="63137-224">Zweitens ist das Reproduzieren eines solchen Screenshots ein zusätzlicher Aufwand.</span><span class="sxs-lookup"><span data-stu-id="63137-224">Second, reproducing such a screenshot is additional effort.</span></span> <span data-ttu-id="63137-225">Beschreiben Sie stattdessen die wichtigen Teile im Text.</span><span class="sxs-lookup"><span data-stu-id="63137-225">Instead, describe the important parts in text.</span></span> <span data-ttu-id="63137-226">Es gibt Ausnahmen von dieser Regel, aber sie sind selten.</span><span class="sxs-lookup"><span data-stu-id="63137-226">There are exceptions to this rule, but they are rare.</span></span>
5. <span data-ttu-id="63137-227">Natürlich ist es viel aufwendiger, ein animiertes GIF neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="63137-227">Obviously, it is much more effort to recreate an animated GIF.</span></span> <span data-ttu-id="63137-228">Erwarten Sie, dass sie bis zum Ende der Zeit neu erstellt werden soll, oder erwarten Sie, dass Personen sie auslösen, wenn sie diese Zeit nicht aufwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="63137-228">Expect to be responsible to recreate it until the end of time, or expect people to throw it out, if they don't want to spend that time.</span></span>
6. <span data-ttu-id="63137-229">Halten Sie die Anzahl der Bilder in einem Artikel gering.</span><span class="sxs-lookup"><span data-stu-id="63137-229">Keep the number of images in an article low.</span></span> <span data-ttu-id="63137-230">Häufig ist es eine gute Methode, einen Gesamtscreenshot eines Tools zu erstellen, das alles zeigt, und dann den Rest im Text zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="63137-230">Often a good method is to make one overall screenshot of some tool, that shows everything, and then describe the rest in text.</span></span> <span data-ttu-id="63137-231">Dies erleichtert das Ersetzen des Screenshots bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="63137-231">This makes it easy to replace the screenshot when necessary.</span></span>

<span data-ttu-id="63137-232">Einige andere Aspekte:</span><span class="sxs-lookup"><span data-stu-id="63137-232">Some other aspects:</span></span>

- <span data-ttu-id="63137-233">Die Benutzeroberfläche des Editors für Screenshots sollte den Editor für hellgraue Designs verwenden, da nicht alle Benutzer Zugriff auf das dunkle Design haben und wir die Konsistenz so konsistent wie möglich halten möchten.</span><span class="sxs-lookup"><span data-stu-id="63137-233">The editor UI for screenshots should use light gray theme editor as not all users have access to the dark theme and we'd like to keep things as consistent as possible.</span></span>
- <span data-ttu-id="63137-234">Die Standardbildbreite beträgt 500 Pixel, da dies auf den meisten Monitoren gut angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="63137-234">Default image width is 500 pixels, as this displays well on most monitors.</span></span> <span data-ttu-id="63137-235">Versuchen Sie nicht, zu viel davon abzuweichen.</span><span class="sxs-lookup"><span data-stu-id="63137-235">Try not to deviate too much from it.</span></span> <span data-ttu-id="63137-236">Die Breite sollte maximal 800 Pixel betragen.</span><span class="sxs-lookup"><span data-stu-id="63137-236">800 pixels width should be the maximum.</span></span>
- <span data-ttu-id="63137-237">Verwenden Sie PNGs für Screenshots der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="63137-237">Use PNGs for screenshots of UI.</span></span>
- <span data-ttu-id="63137-238">Verwenden Sie PNGs oder JPGs für 3D-Viewport-Screenshots.</span><span class="sxs-lookup"><span data-stu-id="63137-238">Use PNGs or JPGs for 3D viewport screenshots.</span></span> <span data-ttu-id="63137-239">Qualität gegenüber Komprimierungsverhältnis bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="63137-239">Prefer quality over compression ratio.</span></span>

### <a name="list-of-component-properties"></a><span data-ttu-id="63137-240">Liste der Komponenteneigenschaften</span><span class="sxs-lookup"><span data-stu-id="63137-240">List of component properties</span></span>

<span data-ttu-id="63137-241">Verwenden Sie beim Dokumentieren einer Liste von Eigenschaften fetten Text, um den Eigenschaftennamen zu markieren, und verwenden Sie dann Zeilenumbrüche und regulären Text, um sie zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="63137-241">When documenting a list of properties, use bold text to highlight the property name, then line breaks and regular text to describe them.</span></span> <span data-ttu-id="63137-242">Verwenden Sie keine Unterkapitel oder Aufzählungslisten.</span><span class="sxs-lookup"><span data-stu-id="63137-242">Do not use sub-chapters or bullet point lists.</span></span>

<span data-ttu-id="63137-243">Vergessen Sie außerdem nicht, alle Sätze mit einem Punkt fertig zu stellen.</span><span class="sxs-lookup"><span data-stu-id="63137-243">Also, don't forget to finish all sentences with a period.</span></span>

## <a name="page-completion-checklist"></a><span data-ttu-id="63137-244">Prüfliste für seitenseitige Vervollständigung</span><span class="sxs-lookup"><span data-stu-id="63137-244">Page completion checklist</span></span>

1. <span data-ttu-id="63137-245">Stellen Sie sicher, dass die Richtlinien dieses Dokuments eingehalten wurden.</span><span class="sxs-lookup"><span data-stu-id="63137-245">Ensure that this document's guidelines were followed.</span></span>
1. <span data-ttu-id="63137-246">Durchsuchen Sie die Dokumentstruktur, und überprüfen Sie, ob das neue Dokument im Abschnitt [Siehe auch](#see-also) auf anderen Seiten erwähnt werden kann.</span><span class="sxs-lookup"><span data-stu-id="63137-246">Browse the document structure and see if the new document could be mentioned under the [See also](#see-also) section of other pages.</span></span>
1. <span data-ttu-id="63137-247">Falls verfügbar, sollten Sie jemanden mit Kenntnissen zum Thema bitten, die Seite auf technische Richtigkeit zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="63137-247">If available, have someone with knowledge of the topic proof-read the page for technical correctness.</span></span>
1. <span data-ttu-id="63137-248">Bitten Sie jemanden, die Seite für Stil und Formatierung zu lesen.</span><span class="sxs-lookup"><span data-stu-id="63137-248">Have someone proof-read the page for style and formatting.</span></span> <span data-ttu-id="63137-249">Dies kann jemand sein, der mit dem Thema nicht vertraut ist. Dies ist auch eine gute Idee, feedback zu erhalten, wie verständlich die Dokumentation ist.</span><span class="sxs-lookup"><span data-stu-id="63137-249">This can be someone unfamiliar with the topic, which is also a good idea to get feedback about how understandable the documentation is.</span></span>

## <a name="source-documentation"></a><span data-ttu-id="63137-250">Quelldokumentation</span><span class="sxs-lookup"><span data-stu-id="63137-250">Source documentation</span></span>

<span data-ttu-id="63137-251">Die API-Dokumentation wird automatisch aus den MRTK-Quelldateien generiert.</span><span class="sxs-lookup"><span data-stu-id="63137-251">API documentation will be generated automatically from the MRTK source files.</span></span> <span data-ttu-id="63137-252">Um dies zu vereinfachen, müssen Quelldateien Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="63137-252">To facilitate this, source files are required to contain the following:</span></span>

- [<span data-ttu-id="63137-253">Klassen-, Struktur- und Enumerationszusammenfassungsblöcke</span><span class="sxs-lookup"><span data-stu-id="63137-253">Class, struct, enum summary blocks</span></span>](#class-struct-enum-summary-blocks)
- [<span data-ttu-id="63137-254">Eigenschaft, Methode, Ereigniszusammenfassungsblöcke</span><span class="sxs-lookup"><span data-stu-id="63137-254">Property, method, event summary blocks</span></span>](#property-method-event-summary-blocks)
- [<span data-ttu-id="63137-255">Featureeinführungsversion und Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="63137-255">Feature introduction version and dependencies</span></span>](#feature-introduction-version-and-dependencies)
- [<span data-ttu-id="63137-256">Serialisierte Felder</span><span class="sxs-lookup"><span data-stu-id="63137-256">Serialized fields</span></span>](#serialized-fields)
- [<span data-ttu-id="63137-257">Enumerationswerte</span><span class="sxs-lookup"><span data-stu-id="63137-257">Enumeration values</span></span>](#enumeration-values)

<span data-ttu-id="63137-258">Darüber hinaus sollte der Code gut kommentiert werden, um Wartung, Fehlerbehebungen und eine einfache Anpassung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="63137-258">In addition to the above, the code should be well commented to allow for maintenance, bug fixes and ease of customization.</span></span>

### <a name="class-struct-enum-summary-blocks"></a><span data-ttu-id="63137-259">Klassen-, Struktur- und Enumerationszusammenfassungsblöcke</span><span class="sxs-lookup"><span data-stu-id="63137-259">Class, struct, enum summary blocks</span></span>

<span data-ttu-id="63137-260">Wenn dem MRTK eine Klasse, Struktur oder Enumeration hinzugefügt wird, muss ihr Zweck beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="63137-260">If a class, struct or enum is being added to the MRTK, its purpose must be described.</span></span> <span data-ttu-id="63137-261">Dies erfolgt in Form eines Zusammenfassungsblocks über der -Klasse.</span><span class="sxs-lookup"><span data-stu-id="63137-261">This is to take the form of a summary block above the class.</span></span>

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

<span data-ttu-id="63137-262">Wenn Abhängigkeiten auf Klassenebene vorhanden sind, sollten sie in einem Hinweisblock direkt unterhalb der Zusammenfassung dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="63137-262">If there are any class level dependencies, they should be documented in a remarks block, immediately below the summary.</span></span>

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

<span data-ttu-id="63137-263">Pull Requests, die ohne Zusammenfassungen für Klassen, Strukturen oder Enumerationen übermittelt werden, werden nicht genehmigt.</span><span class="sxs-lookup"><span data-stu-id="63137-263">Pull Requests submitted without summaries for classes, structures or enums will not be approved.</span></span>

### <a name="property-method-event-summary-blocks"></a><span data-ttu-id="63137-264">Eigenschaften-, Methoden- und Ereigniszusammenfassungsblöcke</span><span class="sxs-lookup"><span data-stu-id="63137-264">Property, method, event summary blocks</span></span>

<span data-ttu-id="63137-265">Eigenschaften, Methoden und Ereignisse (PMEs) sowie Felder müssen unabhängig von der Codesichtbarkeit (öffentlich, privat, geschützt und intern) mit Zusammenfassungsblöcken dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="63137-265">Properties, methods and events (PMEs) as well as fields are to be documented with summary blocks, regardless of code visibility (public, private, protected and internal).</span></span> <span data-ttu-id="63137-266">Das Tool zur Dokumentationsgenerierung ist dafür verantwortlich, nur die öffentlichen und geschützten Features heraus zu filtern und zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="63137-266">The documentation generation tool is responsible for filtering out and publishing only the public and protected features.</span></span>

<span data-ttu-id="63137-267">HINWEIS: Ein Zusammenfassungsblock ist für Unity-Methoden **nicht** erforderlich (z. B. "Aktualisieren", "Starten", "Aktualisieren").</span><span class="sxs-lookup"><span data-stu-id="63137-267">NOTE: A summary block is **not** required for Unity methods (ex: Awake, Start, Update).</span></span>

<span data-ttu-id="63137-268">Die PME-Dokumentation ist **erforderlich,** damit ein Pull Request genehmigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="63137-268">PME documentation is **required** for a pull request to be approved.</span></span>

<span data-ttu-id="63137-269">Als Teil eines PME-Zusammenfassungsblocks sind die Bedeutung und der Zweck von Parametern und zurückgegebenen Daten erforderlich.</span><span class="sxs-lookup"><span data-stu-id="63137-269">As part of a PME summary block, the meaning and purpose of parameters and returned data is required.</span></span>

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a><span data-ttu-id="63137-270">Featureeinführungsversion und Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="63137-270">Feature introduction version and dependencies</span></span>

<span data-ttu-id="63137-271">Im Rahmen der API-Zusammenfassungsdokumentation sollten Informationen zur MRTK-Version, in der das Feature eingeführt wurde, und alle Abhängigkeiten in einem Hinweisblock dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="63137-271">As part of the API summary documentation, information regarding the MRTK version in which the feature was introduced and any dependencies should be documented in a remarks block.</span></span>

<span data-ttu-id="63137-272">Abhängigkeiten sollten Erweiterungs- und/oder Plattformabhängigkeiten enthalten.</span><span class="sxs-lookup"><span data-stu-id="63137-272">Dependencies should include extension and/or platform dependencies.</span></span>

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a><span data-ttu-id="63137-273">Serialisierte Felder</span><span class="sxs-lookup"><span data-stu-id="63137-273">Serialized fields</span></span>

<span data-ttu-id="63137-274">Es ist eine bewährte Methode, das ToolTip-Attribut von Unity zu verwenden, um Laufzeitdokumentation für die Felder eines Skripts im Inspektor bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="63137-274">It is a good practice to use Unity's tooltip attribute to provide runtime documentation for a script's fields in the inspector.</span></span>

<span data-ttu-id="63137-275">Damit Konfigurationsoptionen in der API-Dokumentation enthalten sind, müssen Skripts *mindestens* den QuickInfo-Inhalt in einen Zusammenfassungsblock einschließen.</span><span class="sxs-lookup"><span data-stu-id="63137-275">So that configuration options are included in the API documentation, scripts are required to include *at least* the tooltip contents in a summary block.</span></span>

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a><span data-ttu-id="63137-276">Enumerationswerte</span><span class="sxs-lookup"><span data-stu-id="63137-276">Enumeration values</span></span>

<span data-ttu-id="63137-277">Beim Definieren und Aufzählen muss code auch die Bedeutung der Enumerationswerte mithilfe eines Zusammenfassungsblocks dokumentieren.</span><span class="sxs-lookup"><span data-stu-id="63137-277">When defining and enumeration, code must also document the meaning of the enum values using a summary block.</span></span> <span data-ttu-id="63137-278">Anmerkungsblöcke können optional verwendet werden, um zusätzliche Details bereitzustellen, um das Verständnis zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="63137-278">Remarks blocks can optionally be used to provide additional details to enhance understanding.</span></span>

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a><span data-ttu-id="63137-279">Dokumentation mit Anleitung</span><span class="sxs-lookup"><span data-stu-id="63137-279">How-to documentation</span></span>

<span data-ttu-id="63137-280">Viele Benutzer des Mixed Reality Toolkits müssen die API-Dokumentation möglicherweise nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="63137-280">Many users of the Mixed Reality Toolkit may not need to use the API documentation.</span></span> <span data-ttu-id="63137-281">Diese Benutzer nutzen unsere vorgefertigten, wiederverwendbaren Prefabs und Skripts, um ihre Erfahrungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="63137-281">These users will take advantage of our pre-made, reusable prefabs and scripts to create their experiences.</span></span>

<span data-ttu-id="63137-282">Jeder Featurebereich enthält eine oder mehrere Markdowndateien (MD), die auf einer relativ hohen Ebene beschreiben, was bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="63137-282">Each feature area will contain one or more markdown (.md) files that describe at a fairly high level, what is provided.</span></span> <span data-ttu-id="63137-283">Abhängig von der Größe und/oder Komplexität eines bestimmten Featurebereichs sind möglicherweise zusätzliche Dateien erforderlich, bis zu einer pro bereitgestellter Funktion.</span><span class="sxs-lookup"><span data-stu-id="63137-283">Depending on the size and/or complexity of a given feature area, there may be a need for additional files, up to one per feature provided.</span></span>

<span data-ttu-id="63137-284">Wenn ein Feature hinzugefügt wird (oder die Nutzung geändert wird), muss eine Übersichtsdokumentation bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="63137-284">When a feature is added (or the usage is changed), overview documentation must be provided.</span></span>

<span data-ttu-id="63137-285">Im Rahmen dieser Dokumentation sollten Anleitungsabschnitte, einschließlich Abbildungen, bereitgestellt werden, um Kunden zu helfen, die noch nicht mit einem Feature oder Konzept bei den ersten Schritte begonnen haben.</span><span class="sxs-lookup"><span data-stu-id="63137-285">As part of this documentation, how-to sections, including illustrations, should be provided to assist customers new to a feature or concept in getting started.</span></span>

## <a name="design-documentation"></a><span data-ttu-id="63137-286">Entwurfsdokumentation</span><span class="sxs-lookup"><span data-stu-id="63137-286">Design documentation</span></span>

<span data-ttu-id="63137-287">Mixed Reality bietet die Möglichkeit, völlig neue Welten zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="63137-287">Mixed Reality provides an opportunity to create entirely new worlds.</span></span> <span data-ttu-id="63137-288">Ein Teil davon ist wahrscheinlich die Erstellung von benutzerdefinierten Ressourcen für die Verwendung mit dem MRTK.</span><span class="sxs-lookup"><span data-stu-id="63137-288">Part of this is likely to involve the creation of custom assets for use with the MRTK.</span></span> <span data-ttu-id="63137-289">Damit dies für Kunden so reibungslos wie möglich ist, sollten Komponenten eine Entwurfsdokumentation bereitstellen, in der alle Formatierungs- oder anderen Anforderungen für Diess-Objekte beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="63137-289">To make this as friction free as possible for customers, components should provide design documentation describing any formatting or other requirements for art assets.</span></span>

<span data-ttu-id="63137-290">Einige Beispiele, in denen die Entwurfsdokumentation hilfreich sein kann:</span><span class="sxs-lookup"><span data-stu-id="63137-290">Some examples where design documentation can be helpful:</span></span>

- <span data-ttu-id="63137-291">Cursormodelle</span><span class="sxs-lookup"><span data-stu-id="63137-291">Cursor models</span></span>
- <span data-ttu-id="63137-292">Visualisierungen der räumlichen Zuordnung</span><span class="sxs-lookup"><span data-stu-id="63137-292">Spatial mapping visualizations</span></span>
- <span data-ttu-id="63137-293">Soundeffektdateien</span><span class="sxs-lookup"><span data-stu-id="63137-293">Sound effect files</span></span>

<span data-ttu-id="63137-294">Diese Art von Dokumentation wird **dringend** empfohlen und **kann** im Rahmen einer Pull Request-Überprüfung angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="63137-294">This type of documentation is **strongly** recommended, and **may** be requested as part of a pull request review.</span></span>

<span data-ttu-id="63137-295">Dies kann sich von der Entwurfsempfehlung auf der [MS Developer-Website](/windows/mixed-reality/design) unterscheiden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="63137-295">This may or may not be different from the design recommendation on the [MS Developer site](/windows/mixed-reality/design)</span></span>

## <a name="performance-notes"></a><span data-ttu-id="63137-296">Leistungshinweise</span><span class="sxs-lookup"><span data-stu-id="63137-296">Performance notes</span></span>

<span data-ttu-id="63137-297">Einige wichtige Features sind mit Leistungskosten verbunden.</span><span class="sxs-lookup"><span data-stu-id="63137-297">Some important features come at a performance cost.</span></span> <span data-ttu-id="63137-298">Dieser Code hängt häufig davon ab, wie sie konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="63137-298">Often this code will very depending how they are configured.</span></span>

<span data-ttu-id="63137-299">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="63137-299">For example:</span></span>

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

<span data-ttu-id="63137-300">Leistungshinweise werden für CPU- und/oder GPU-starke Komponenten empfohlen und **können** im Rahmen einer Pull Request-Überprüfung angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="63137-300">Performance notes are recommended for CPU and/or GPU heavy components and **may** be requested as part of a pull request review.</span></span> <span data-ttu-id="63137-301">Alle anwendbaren Leistungshinweise müssen in der **API- und** Übersichtsdokumentation enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="63137-301">Any applicable performance notes are to be included in API **and** overview documentation.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="63137-302">Aktuelle Änderungen</span><span class="sxs-lookup"><span data-stu-id="63137-302">Breaking changes</span></span>

<span data-ttu-id="63137-303">Die Dokumentation zu Breaking Changes besteht aus einer [Datei](../contributing/breaking-changes.md) der obersten Ebene, die mit den einzelnen breaking-changes.md jedes Featurebereichs verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="63137-303">Breaking changes documentation is to consist of a top level [file](../contributing/breaking-changes.md) which links to each feature area's individual breaking-changes.md.</span></span>

<span data-ttu-id="63137-304">Der Funktionsbereich breaking-changes.md Dateien enthält die Liste aller bekannten Breaking Changes für ein bestimmtes Release **sowie** den Verlauf der Breaking Changes aus früheren Releases.</span><span class="sxs-lookup"><span data-stu-id="63137-304">The feature area breaking-changes.md files are to contain the list of all known breaking changes for a given release **as well as** the history of breaking changes from past releases.</span></span>

<span data-ttu-id="63137-305">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="63137-305">For example:</span></span>

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

<span data-ttu-id="63137-306">Die Informationen auf Featureebene breaking-changes.md Dateien werden in den Versionshinweisen für jedes neue MRTK-Release aggregiert.</span><span class="sxs-lookup"><span data-stu-id="63137-306">The information contained within the feature level breaking-changes.md files will be aggregated to the release notes for each new MRTK release.</span></span>

<span data-ttu-id="63137-307">Alle Breaking Changes, die Teil einer Änderung sind, **müssen** als Teil eines Pull Requests dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="63137-307">Any breaking changes that are part of a change **must** be documented as part of a Pull Request.</span></span>

## <a name="tools-for-editing-markdown"></a><span data-ttu-id="63137-308">Tools zum Bearbeiten von MarkDown</span><span class="sxs-lookup"><span data-stu-id="63137-308">Tools for editing MarkDown</span></span>

<span data-ttu-id="63137-309">[Visual Studio Code](https://code.visualstudio.com/) ist ein hervorragendes Tool zum Bearbeiten von Markdowndateien, die Teil der MRTK-Dokumentation sind.</span><span class="sxs-lookup"><span data-stu-id="63137-309">[Visual Studio Code](https://code.visualstudio.com/) is a great tool for editing markdown files that are part of MRTK's documentation.</span></span>

<span data-ttu-id="63137-310">Beim Schreiben der Dokumentation wird auch dringend empfohlen, die folgenden beiden Erweiterungen zu installieren:</span><span class="sxs-lookup"><span data-stu-id="63137-310">When writing documentation, installing the following two extensions is also highly recommended:</span></span>

- <span data-ttu-id="63137-311">Docs Markdown Extension for Visual Studio Code : Verwenden Sie ALT+M, um ein Menü mit Dokumenterstellungsoptionen aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="63137-311">Docs Markdown Extension for Visual Studio Code - Use Alt+M to bring up a menu of docs authoring options.</span></span>

- <span data-ttu-id="63137-312">Code spell checker ( Rechtschreibprüfung für Code): Falsch geschriebene Wörter werden unterstrichen. Klicken Sie mit der rechten Maustaste auf ein falsch geschriebenes Wort, um es zu ändern oder im Wörterbuch zu speichern.</span><span class="sxs-lookup"><span data-stu-id="63137-312">Code Spell Checker - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

<span data-ttu-id="63137-313">Beides ist im von Microsoft veröffentlichten Docs Authoring Pack enthalten.</span><span class="sxs-lookup"><span data-stu-id="63137-313">Both of these come packaged in the Microsoft published Docs Authoring Pack.</span></span>

## <a name="see-also"></a><span data-ttu-id="63137-314">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="63137-314">See also</span></span> 

* [<span data-ttu-id="63137-315">Beispiellink</span><span class="sxs-lookup"><span data-stu-id="63137-315">Example link</span></span>](https://www.google.com)