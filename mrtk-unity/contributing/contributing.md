---
title: Mitwirken am MRTK
description: Beitragen zum Mixed Reality Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Fehlerbericht,
ms.openlocfilehash: b79f69cbb6dea1201c88d9fd1a354967ce40735e
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282040"
---
# <a name="contributing-to-mrtk"></a>Mitwirken am MRTK

Das Mixed Reality Toolkit (MRTK) empfängt Beiträge aus der Community. Alle Änderungen sind klein oder groß und müssen den [MRTK-Codierungsstandards](coding-guidelines.md)entsprechen. Stellen Sie daher sicher, dass Sie mit diesen beim Entwickeln vertraut sind, um Verzögerungen bei der Überprüfung der Änderung zu vermeiden.

Wenn Sie Fragen haben, wenden Sie sich an den [Mixed Reality-Toolkit-Kanal auf Slack.](https://holodevelopers.slack.com/messages/C2H4HT858)
Sie können der Slack-Community über den [automatischen Einladungsversender](https://holodevelopersslack.azurewebsites.net/) beitreten.

## <a name="submission-process"></a>Einreichungsprozess

Wir bieten verschiedene Pfade, um Entwicklern zu ermöglichen, am Mixed Reality Toolkit mit beizutragen, beginnend mit der [Erstellung eines neuen Issue.](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

Hier können Sie Eine Datei erstellen:

- **Fehlerbericht:** Funktionsproblem mit einer der komponenten des Mixed Reality Toolkits
- **Dokumentationsproblem:** Problem mit der Mixed Reality [Toolkit-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity)
- **Featureanforderung:** Vorschlag für ein neues feature Mixed Reality Toolkit

## <a name="proposing-feature-requests"></a>Vorschlagen von Featureanforderungen

Wenn Sie ein neues Feature Mixed Reality Toolkit anfordern, ist es wichtig, den Kundenvorteil bzw. das zu lösende Problem zu dokumentieren. Nachdem sie übermittelt wurde, wird eine Featureanforderung überprüft und im GitHub. Wir empfehlen eine offene und rege Diskussion der einzelnen Featurevorschlage, um sicherzustellen, dass die Arbeit für ein großes Kundensegment von Vorteil ist.

Um zu vermeiden, dass das Feature überarbeitet werden muss, wird im Allgemeinen empfohlen, dass die Entwicklung des Features nicht während der Überprüfungsphase beginnt. In vielen Fällen werden bei der Überprüfung durch die Community ein oder mehrere Probleme entdeckt, die möglicherweise erhebliche Änderungen an der vorgeschlagenen Implementierung erfordern.

> [!NOTE]
> Wenn Sie an etwas arbeiten möchten, das bereits in unserem Backlog vorhanden ist, können Sie dieses Arbeitselement als Vorschlag verwenden. Kommentieren Sie auch die Aufgabe, um die Betreuer zu benachrichtigen, dass Sie daran arbeiten, sie auszuführen.

## <a name="contribution-process"></a>Beitragsvorgang

Führen Sie zum Einstieg einfach die folgenden Schritte aus:

1. Forken Sie das Repository. Klicken Sie rechts oben auf der Seite auf die Schaltfläche "Fork", und folgen Sie dem Flow.
1. Erstellen Sie eine Verzweigung in [](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) Ihrer Verzweigung (aus dem Hauptzweig), um das Isolieren von Änderungen zu vereinfachen, bis sie zur Übermittlung bereit sind. Um Programmfehlerbehebungen während eines Releasestabilisierungszeitraums zu finden, suchen Sie nach dem neuesten `prerelease/*` Branch. Neue Features sollten immer in berücksichtigt `main` werden.

Wenn Sie noch nicht mit dem Git-Workflow arbeiten, sehen [Sie sich diese Einführung von GitHub an.](https://guides.github.com/activities/hello-world/)

Führen Sie beim Hinzufügen einer Fehlerbehebung oder eines Features die folgenden Schritte aus:

1. Implementieren Sie die Fehlerbehebung oder das Feature . Anweisungen zum Erstellen und Bereitstellen von MRTK finden Sie unter [Bereitstellen auf Hololens- und WMR-Geräten.](../supported-devices/wmr-mrtk.md) Beachten Sie, dass Sie die [Codierungsrichtlinien befolgen.](../contributing/coding-guidelines.md)
1. Wenn Sie ein Feature hinzufügen, fügen Sie auch eine Beispielszene hinzu, die das Feature veranschaulicht.
1. Wenn Sie ein experimentelles Feature hinzufügen, ist das Schreiben von Tests und Dokumentation nicht erforderlich. Befolgen Sie stattdessen [experimentelle Featurerichtlinien.](../contributing/experimental-features.md)
1. Fügen Sie Tests hinzu, um die Fehlerbehebung bzw. das Feature zu überprüfen. Anweisungen zum Schreiben und Ausführen von Tests finden Sie unter [UnitTests.](../contributing/unit-tests.md)
1. Stellen Sie sicher, dass der Code und die Features wie in den Dokumentationsrichtlinien [beschrieben dokumentiert sind.](../contributing/documentation-guide.md)
1. Stellen Sie sicher, dass der Code auf allen Plattformen wie vorgesehen funktioniert. Die Liste [der unterstützten](../release-notes/mrtk-26-release-notes.md) Plattformen finden Sie in den Versionshinweisen. Für Windows UWP-Projekte muss der Code [WACK-kompatibel sein.](https://developer.microsoft.com/windows/develop/app-certification-kit) Generieren Sie hierzu eine projektmappe Visual Studio, klicken Sie mit der rechten Maustaste auf das Projekt. **Store**  >  **Erstellen Sie App-Pakete.** Befolgen Sie die Anweisungen, und führen Sie WACK-Tests aus. Stellen Sie sicher, dass alle erfolgreich sind.
1. Befolgen Sie die Anweisungen [unter Pull Requests,](../contributing/pull-requests.md) wenn Sie einen Pull Request senden.
