---
title: PullRequests
description: Details im Zusammenhang mit Pull Requests.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, PR,
ms.openlocfilehash: c49934139ae23b714addcb9c015e95377f47900e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693717"
---
# <a name="pull-requests"></a>Pull Requests

## <a name="prerequisites"></a>Voraussetzungen

Wenn Sie zuvor noch nicht an einem Microsoft-Projekt mitgewirkt haben, werden Sie möglicherweise aufgefordert, einen [Lizenzvertrag für Mitwirkende ](https://cla.microsoft.com/) (Contributor License Agreement) zu unterschreiben.
Ein Kommentar in dem PR informiert Sie darüber.

> [!IMPORTANT]
> Wenn Sie Mitarbeiter von Microsoft und kein Mitglied der [Microsoft-Organisation auf GitHub](https://github.com/Microsoft) sind, verknüpfen Sie Ihre Microsoft- und GitHub-Konten auf Corpnet, indem Sie [Open Source bei Microsoft](https://opensource.microsoft.com/) besuchen, bevor Sie mit dem Pull Request beginnen. Es gibt einige Verarbeitungsschritte, die Sie vorab ausführen müssen.

## <a name="creating-a-pull-request"></a>Erstellen eines Pull Requests

Wenn Sie bereit sind, einen Pull Request zu senden, [erstellen Sie einen Pull Request](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1), der auf den Branch [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) abzielt.

Lesen Sie die Richtlinien, und stellen Sie sicher, dass Ihr Pull Request diese erfüllt.

* Stellen Sie sicher, dass Sie auf alle Probleme/Featureanforderungen oder Aufgaben verweisen, auf die sich der PR bezieht.
* Überprüfen Sie, ob der Pull Request nur Dateien/Änderungen enthält, die sich auf den PR beziehen.
* Überprüfen Sie, ob die Dokumentation aktuell und enthalten ist. Überprüfen Sie, ob alle öffentlichen Felder über Kommentare verfügen.
* Wenn Sie ein neues Feature hinzufügen, überprüfen Sie, ob Tests zum Überprüfen des Features enthalten sind (siehe [UnitTests](../contributing/unit-tests.md) (Komponententests)).
* Wenn Sie einen Fehler korrigieren, schreiben Sie einen Test, um die Fehlerbehebung überprüfen zu können.

Die Projektverwalter überprüfen Ihre Änderungen. Unser Anspruch ist es, alle Änderungen innerhalb von drei Werktagen zu überprüfen. Adressieren Sie alle Überprüfungskommentare, pushen Sie in Ihren Themen-Branch, und posten Sie einen Kommentar, um uns zu informieren, dass es etwas Neues zu überprüfen gibt.

> [!NOTE]
> Alle an das Projekt übermittelten PRs werden auch gemäß dem [MRTK-Handbuch für Programmierstandards](../contributing/coding-guidelines.md) überprüft. Überprüfen Sie diese also vor dem Übermitteln Ihres PR, um einen reibungslosen Ablauf zu gewährleisten.

## <a name="pull-request-guidelines"></a>Richtlinien für Pull Requests

Diese Richtlinien basieren auf den [Entwicklungspraktiken von Google](https://google.github.io/eng-practices/review/developer/small-cls.html).

### <a name="keep-pull-requests-small"></a>Halten Sie Pull Requests klein.

Kleinere PRs werden schneller und gründlicher überprüft, führen mit geringerer Wahrscheinlichkeit Fehler ein, ein Rollback ist einfacher, und sie lassen sich einfacher zusammenführen.

Ein Pull Request sollte so klein sein, dass ein Techniker ihn in weniger als 30 Minuten überprüfen kann. Versuchen Sie, lediglich eine minimale Änderung vorzunehmen, die nur eine Aktion behandelt. Wenn Sie einen großen PR erstellen müssen, teilen Sie ihn in mehrere PRs auf, die entweder in Ihren lokalen Branch oder in einen Feature-Branch von MRTK gelangen. Vermeiden Sie das Hinzufügen neuer Objekte (z. B. FBX-, OBJ-Dateien), und versuchen Sie stattdessen, vorhandene Objekte wiederzuverwenden.

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a>Tests sollten mit Ausnahme von Notfällen im selben PR wie Ihr Fix/Feature hinzugefügt werden.

Tests sind die beste Möglichkeit, um sicherzustellen, dass der vorhandene Code von den Änderungen nicht verschlechtert wird. Es ist jedoch auch leicht, bei der Übermittlung von Pull Requests die Tests zu vergessen. Anzufordern, dass Tests in Ihren PR einfließen müssen, ist eine gute Möglichkeit, um sicherzustellen, dass die Tests geschrieben werden.

Allen Features und Fehlerbehebungen sollten Tests zugeordnet sein. Wenn Sie nicht über das Fachwissen oder die Zeit zum Schreiben eines Tests verfügen, erstellen Sie ein Problem, um die Tests zu schreiben, und markieren Sie es mit der Bezeichnung **Für aktuelle Iteration berücksichtigen**.

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a>Die Dokumentation sollte im selben Pull Request hinzugefügt werden wie ein Fix/Feature.

Die meisten Entwickler sehen sich zunächst die Dokumentation und nicht den Code an, wenn sie wissen möchten, wie eine Funktion zu verwenden ist. Die Sicherstellung, dass die Dokumentation auf dem neuesten Stand ist, erleichtert Benutzern die Nutzung von MRTK erheblich.  Die Dokumentation sollte immer mit dem zugehörigen Pull Request gebündelt werden, um sicherzustellen, dass die Elemente aktuell und konsistent bleiben.

Stellen Sie sicher, dass jedes öffentliche Feld sowie jede Methode und Eigenschaft über [Zusammenfassungskommentare mit dreifachen Schrägstrichen](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) verfügt, damit unsere docfx-Site Beschreibungen für Felder/Methoden generieren kann. Aktualisieren Sie bei Bedarf markdown-Dateien im Dokumentationsordner.

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a>Beschreibungen von Pull Requests sollten Änderungen eindeutig und vollständig beschreiben.

Klare und vollständige Beschreibungen von Pull Requests stellen sicher, dass Prüfer verstehen, was Sie überprüfen.

Fügen Sie beim Hinzufügen von Features, die UX enthalten, ein Bild/GIF des Features hinzu, das Sie ändern. [Hier sehen Sie ein gutes Beispiel](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532). Ein anderer Vorschlag besteht darin, eine Vorher-/Nachher-GIF zu haben, z. B. [in diesem Pull Request](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896). Ein Tool, das wir zum Erstellen von GIFs aus Screenshots empfehlen, ist [ScreenToGif](https://www.screentogif.com/).
