---
title: Beitragen
description: Mitwirken am Mixed Reality Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Fehlerbericht,
ms.openlocfilehash: 525e704ae2f09580c8c19ca7e8a25dad4aed2647
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489260"
---
# <a name="contributing"></a>Mitwirken

Das Mixed Reality Toolkit (MRTK) leistet Beiträge aus der Community. Alle Änderungen, ob klein oder groß, müssen den [MRTK-Codierungsstandards](coding-guidelines.md)entsprechen. Stellen Sie daher sicher, dass Sie mit diesen beim Entwickeln vertraut sind, um Verzögerungen zu vermeiden, wenn die Änderung überprüft wird.

Wenn Sie Fragen haben, wenden Sie sich an den [Mixed Reality-Toolkit-Kanal auf Slack](https://holodevelopers.slack.com/messages/C2H4HT858).
Sie können der Slack-Community über den [automatischen Einladungsversender](https://holodevelopersslack.azurewebsites.net/) beitreten.

## <a name="submission-process"></a>Einreichungsprozess

Wir bieten mehrere Pfade, mit denen Entwickler am Mixed Reality Toolkit mitwirken können, wobei alle mit dem [Erstellen eines neuen Problems](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)beginnen.

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

Hier können Sie folgende Datei erstellen:

- **Fehlerbericht:** Funktionsproblem mit einer der Mixed Reality Toolkit-Komponenten
- **Dokumentationsproblem:** Problem mit der [Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity) zum Mixed Reality Toolkit
- **Featureanforderung:** Vorschlag für eine neue Mixed Reality Toolkit-Funktion

## <a name="proposing-feature-requests"></a>Vorschlagen von Featureanforderungen

Wenn Sie eine neue Mixed Reality Toolkit-Funktion anfordern, ist es wichtig, den Kundenvorteil bzw. das Zu lösende Problem zu dokumentieren. Nach der Übermittlung wird eine Featureanforderung überprüft und auf GitHub erläutert. Wir empfehlen ihnen, jeden Featurevorschlag offen und offen zu diskutieren, um sicherzustellen, dass die Arbeit für ein großes Kundensegment von Vorteil ist.

Um zu vermeiden, dass das Feature überarbeitet werden muss, wird im Allgemeinen empfohlen, dass die Entwicklung des Features nicht während der Überprüfungsphase beginnt. Der Überprüfungsprozess der Community deckt häufig ein oder mehrere Probleme auf, die erhebliche Änderungen an der vorgeschlagenen Implementierung erfordern können.

> [!NOTE]
> Wenn Sie an etwas arbeiten möchten, das bereits in unserem Backlog vorhanden ist, können Sie dieses Arbeitselement als Vorschlag verwenden. Stellen Sie außerdem sicher, dass Sie die Aufgabe kommentieren und die Betreuer darüber benachrichtigen, dass Sie daran arbeiten, sie abzuschließen.

## <a name="contribution-process"></a>Beitragsprozess

Führen Sie zum Einstieg einfach die folgenden Schritte aus:

1. Forken Sie das Repository. Klicken Sie rechts oben auf der Seite auf die Schaltfläche "Fork", und folgen Sie dem Flow.
1. Erstellen Sie eine Verzweigung in [](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) Ihrer Verzweigung (aus dem Hauptzweig), um das Isolieren von Änderungen zu vereinfachen, bis sie zur Übermittlung bereit sind. Um Programmfehlerbehebungen während eines Releasestabilisierungszeitraums zu finden, suchen Sie nach dem neuesten `prerelease/*` Branch. Neue Features sollten immer in berücksichtigt `main` werden.

Wenn Sie noch nicht mit dem Git-Workflow arbeiten, sehen [Sie sich diese Einführung von GitHub an.](https://guides.github.com/activities/hello-world/)

Führen Sie beim Hinzufügen einer Fehlerbehebung oder eines Features die folgenden Schritte aus:

1. Implementieren Sie die Fehlerbehebung oder das Feature . Anweisungen zum Erstellen und Bereitstellen von MRTK finden Sie unter [BuildAndDeploy](../updates-deployment/build-and-deploy.md). Beachten Sie, dass Sie die [Codierungsrichtlinien befolgen.](../contributing/coding-guidelines.md)
1. Wenn Sie ein Feature hinzufügen, fügen Sie auch eine Beispielszene hinzu, die das Feature veranschaulicht.
1. Wenn Sie ein experimentelles Feature hinzufügen, ist das Schreiben von Tests und Dokumentation nicht erforderlich. Befolgen Sie stattdessen [experimentelle Featurerichtlinien.](../contributing/experimental-features.md)
1. Fügen Sie Tests hinzu, um die Fehlerbehebung bzw. das Feature zu überprüfen. Anweisungen zum Schreiben und Ausführen von Tests finden Sie unter [UnitTests.](../contributing/unit-tests.md)
1. Stellen Sie sicher, dass der Code und die Features wie in den Dokumentationsrichtlinien [beschrieben dokumentiert sind.](../contributing/documentation-guide.md)
1. Stellen Sie sicher, dass der Code auf allen Plattformen wie vorgesehen funktioniert. Die Liste [der unterstützten](../release-notes/mrtk-26-release-notes.md) Plattformen finden Sie in den Versionshinweisen. Für Windows-UWP-Projekte muss Code [WACK-kompatibel sein.](https://developer.microsoft.com/windows/develop/app-certification-kit) Generieren Sie hierzu eine projektmappe Visual Studio, klicken Sie mit der rechten Maustaste auf das Projekt. **Store**  >  **Erstellen Sie App-Pakete.** Befolgen Sie die Anweisungen, und führen Sie WACK-Tests aus. Stellen Sie sicher, dass alle erfolgreich sind.
1. Befolgen Sie beim Erstellen eines Pull Requests die Anweisungen unter [Pull Requests.](../contributing/pull-requests.md)
