---
title: Aktuelle Änderungen
description: Richtlinie zu Breaking Changes im MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 5f48503c4d28316cad49fbdf8bc163399ca9f7ad
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143496"
---
# <a name="breaking-changes"></a>Aktuelle Änderungen

MrTK-Benutzer sind von einer stabilen API-Oberfläche für Release-to-Release abhängig, sodass sie Updates für das MRTK vornehmen können, ohne dass jedes Mal große Breaking Changes vorgenommen werden müssen.

Auf dieser Seite wird unsere aktuelle Richtlinie in Bezug auf Breaking Changes im MRTK sowie einige längerfristige Ziele beschrieben, wie wir den Kompromiss zwischen der Geringhaltung von Breaking Changes und der Möglichkeit, die richtigen langfristigen technischen Änderungen am Code vorzunehmen, besser bewältigen können.

## <a name="what-is-a-breaking-change"></a>Was ist ein Breaking Change?

Eine Änderung ist eine Breaking Change, wenn sie eine der Bedingungen in Liste [A](#list-a) erfüllt und alle Bedingungen in Liste [B erfüllt.](#list-b)

### <a name="list-a"></a>Auflisten von A

- Das Addition, Entfernen oder Aktualisieren von Membern oder Funktionen einer Schnittstelle (oder Entfernen/Umbenennen der gesamten Schnittstelle).
- Das Entfernen, Aktualisieren (Ändern von Typ/Definition, Privates oder Internes) von geschützten oder öffentlichen Membern oder Funktionen der Klasse. (oder Entfernen/Umbenennen der gesamten Klasse).
- Die Änderung in der Reihenfolge der Ereignisse, die von einer Klasse ausgelöst werden.
- Das Umbenennen eines privaten SerializedField (ohne entsprechendes FormerlySerializedAs-Tag) oder einer öffentlichen Eigenschaft für ein ScriptableObject (insbesondere Änderungen an Profilen).
- Ändern des Feldtyps für ein ScriptableObject (insbesondere Änderungen an Profilen).
- Aktualisiert den Namespace oder die Asmdefs einer beliebigen Klasse oder Schnittstelle.
- Entfernen eines Beliebigen Prefabs oder Entfernen eines Skripts auf dem Objekt der obersten Ebene eines Prefabs.

### <a name="list-b"></a>Liste B

- Das objekt in Frage befindet sich im Basispaket (d. h. es befindet sich in einem der folgenden Ordner):

  - MRTK/Core
  - MRTK/Providers/
  - MRTK/Services/
  - MRTK/SDK/
  - MRTK/Extensions

- Das betreffende Objekt gehört nicht zum experimentellen Namespace.

> [!IMPORTANT]
> Alle Ressourcen, die sich im Beispielpaket befinden (d. h. Teil des Ordners MRTK/Examples/), können jederzeit geändert werden, da Ressourcen dort von Consumern als "Verweisimplementierungen" kopiert und angezeigt werden sollen, aber nicht Teil des Kernsatzes von APIs und Ressourcen sind. Ressourcen im experimentellen Namespace (oder allgemeiner gesagt als experimentell bezeichnete Features) werden veröffentlicht, bevor die gesamte due-due-Prüfung durchgeführt wurde (d. h. Tests, UX-Iteration, Dokumentation) und früh veröffentlicht werden, um früher Feedback zu erhalten.  Da sie jedoch keine Tests und Dokumentationen haben und wir wahrscheinlich nicht alle Interaktionen und Entwürfe abgesenkt haben, veröffentlichen wir sie in einem Zustand, in dem die Öffentlichkeit davon ausgehen sollte, dass sie sich ändern können und werden (d. h. geändert, vollständig entfernt usw.).
>
> Weitere Informationen finden Sie unter [Experimentelle Features.](../contributing/experimental-features.md)

Da die Oberfläche für Breaking Changes sehr groß ist, ist es wichtig zu beachten, dass es unmöglich wäre, eine absolute Regel zu haben, die besagt, dass keine Breaking Changes vorhanden sind. Möglicherweise gibt es Probleme, die nur durch eine Breaking Change auf eine angemessene Weise behoben werden können. Anders ausgedrückt: Die einzige Möglichkeit, "keine Breaking Changes" zu erhalten, besteht darin, überhaupt keine Änderungen vorzunehmen.

Unsere ständige Richtlinie besteht darin, wenn möglich breaking changes zu vermeiden. Dies geschieht nur, wenn die Änderung einen erheblichen langfristigen Kunden- oder Frameworkwert ergeben würde.

## <a name="what-to-do-about-breaking-changes"></a>Was sie gegen Breaking Changes tun müssen

Wenn es möglich ist, etwas ohne Breaking Change und ohne Beeinträchtigung der langfristigen Struktur und Verwendbarkeit des Features zu erreichen, sollten Sie die Breaking Change nicht durchführen. Wenn es keine andere Möglichkeit gibt, besteht die aktuelle Richtlinie darin, jede einzelne Breaking Change auszuwerten, um zu verstehen, ob der Nutzen der Änderung die Kosten für den Consumer überwiegt, die die Änderung auffangen. Diskussionen darüber, was sich lohnt und was nicht, werden in der Regel im Pr oder in der Diskussion über das Problem selbst stattfinden.

Was hier passieren kann, kann in mehrere Buckets fallen:

### <a name="the-breaking-change-adds-value-but-could-be-written-in-a-way-that-isnt-breaking"></a>Die breaking change erhöht den Wert, könnte aber auf eine Weise geschrieben werden, die nicht bricht.

Dieser [PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4882) hat z. B. ein neues Feature hinzugefügt, das ursprünglich so geschrieben wurde, dass es unterbrochen wurde – es hat eine vorhandene Schnittstelle geändert –, aber dann neu geschrieben wurde, wo das Feature als eigene Schnittstelle aufgebrochen wurde. Dies ist im Allgemeinen das bestmögliche Ergebnis. Versuchen Sie nicht, eine Änderung in eine nicht bruchfreie Form zu erzwingen, wenn dies die langfristige Rentabilität oder Struktur des Features gefährden würde.

### <a name="the-breaking-change-adds-sufficient-value-to-the-customer-that-its-worth-doing"></a>Die Breaking Change fügt dem Kunden einen ausreichenden Mehrwert hinzu, der sich lohnt.

Dokumentieren Sie die Breaking Changes, und bieten Sie die bestmögliche Lösung (d. h. vorschreibende Schritte zur Migration oder noch bessere Tools, die automatisch für den Kunden migriert werden). Jedes Release kann eine kleine Menge von Änderungen enthalten, die breaking sind. Diese sollten immer in der Dokumentation dokumentiert werden, wie dies in diesem PR der Fall [war.](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4858) Wenn bereits ein Migrationshandbuch zu 2.x.x→2.x+1.x+1 vorhanden ist, fügen Sie diesem Dokument Anweisungen oder Tools hinzu. Wenn sie nicht vorhanden ist, erstellen Sie sie.

### <a name="the-breaking-change-adds-value-but-the-customer-pain-would-be-too-high"></a>Die breaking change erhöht den Wert, aber die Kundenzufriedenheit wäre zu hoch.

Nicht alle Arten von Breaking Changes werden gleich erstellt– einige sind wesentlich schwieriger als andere, basierend auf unserer Erfahrung und den Kundenerfahrungen. Änderungen an Schnittstellen können z. B. unwahrscheinlich sein, aber wenn es sich bei der Breaking Change um eine Änderung handelt, bei der es unwahrscheinlich ist, dass ein Kunde in der Vergangenheit erweitert/implementiert wurde (z. B. das Diagnosevisualisierungssystem), sind die tatsächlichen Kosten wahrscheinlich niedrig bis gar nichts. Wenn es sich bei der Änderung jedoch um den Typ eines Felds für ein ScriptableObject handelt (z. B. in einem der Kernprofile des MRTK), wird dies wahrscheinlich zu großen Kundenbeanstandung führen. Kunden haben das Standardprofil bereits geklont. Das Zusammenführen/Aktualisieren von Profilen kann sehr schwierig sein (d. h. über einen Text-Editor während der Zusammenführungszeit), und das erneute Kopieren des Standardprofils und das manuelle Neukonfigurieren aller Profile führt sehr wahrscheinlich zu schwer zu Debuggen von Regressionen.

Diese Änderungen müssen wieder in das Verkaufsregal gesetzt werden, bis ein Branch vorhanden ist, der erhebliche Breaking Changes zulässt (zusammen mit einem erheblichen Wert, der Kunden einen Grund für das Upgrade gibt). Ein solcher Branch ist derzeit nicht vorhanden. In unseren zukünftigen Iterationsplanungsbesprechungen werden wir den Satz von Änderungen/Problemen überprüfen, die "zu breaking" waren, um festzustellen, ob wir eine kritische Menge erreicht haben, um es sinnvoll zu machen, alle Änderungen gleichzeitig zu verfolgen. Beachten Sie, dass es gefährlich ist, einen Branch "Alles ist zulässig" einzurichten, ohne dass aufgrund der begrenzten engineering-Ressourcen, die wir haben, und der Tatsache, dass wir Tests und Validierungen auf diese beiden verteilen müssten, sorgfältig vorgegangen wird. Es muss einen eindeutigen Zweck und ein gut kommuniziertes Start- und Enddatum eines solchen Branchs geben, wenn er vorhanden ist.

## <a name="long-term-management-of-breaking-changes"></a>Langfristige Verwaltung von Breaking Changes

Langfristig sollten wir versuchen, den Umfang der Breaking Change zu reduzieren, indem wir den Satz von Bedingungen in [Liste B](#list-b)erhöhen. In Zukunft werden die Elemente in [Liste A](#list-a) technisch immer für den Satz von Dateien und Ressourcen, die wir in der "öffentlichen API-Oberfläche" als "öffentliche API-Oberfläche" eingestuft haben, breaking werden. Die Art und Weise, wie wir die Iteration ein wenig vereinfachen können (d. h. die internen Implementierungsdetails zu ändern, ein einfacheres Umgestalten und Freigeben von Code zwischen mehreren Klassen zu ermöglichen usw.), besteht darin, expliziter zu sein, welche Teile des Codes offizielle Oberfläche sind, anstatt Implementierungsdetails.

Wir haben bereits das Konzept eines "experimentellen" Features eingeführt (es gehört zum experimentellen Namespace, verfügt möglicherweise nicht über Tests/Dokumentationen und ist öffentlich dafür bekannt, vorhanden zu sein, kann aber ohne Warnung entfernt und aktualisiert werden). Dies hat die Möglichkeit gegeben, neue Features früher hinzuzufügen, um früher Feedback zu erhalten, aber nicht sofort an die API-Oberfläche gebunden zu sein (da wir die API-Oberfläche möglicherweise nicht vollständig durchdacht haben).

### <a name="other-examples-of-things-that-could-help-in-the-future"></a>Weitere Beispiele für Dinge, die in Zukunft helfen könnten

- Verwendung des internen [Schlüsselworts](/dotnet/csharp/language-reference/keywords/internal).
  Dies würde es uns ermöglichen, freigegebenen Code in unseren eigenen Assemblys (zur Reduzierung der Codeduplizierung) zu verwenden, ohne die Dinge für externe Benutzer öffentlich zu machen.
- Erstellung eines "internen" Namespace (z.B. Microsoft.MixedReality.Toolkit.Internal.Utilities), in dem öffentlich dokumentiert wird, dass alles, was in diesem internen Namespace enthalten ist, jederzeit geändert werden kann und entfernt werden kann usw. Dies ähnelt der Verwendung von ::internal-Namespaces durch C++-Headerbibliotheken, um ihre Implementierungsdetails auszublenden.