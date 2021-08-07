---
title: Mitwirken am MRTK
description: Mitwirken am Mixed Reality Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Fehlerbericht,
ms.openlocfilehash: e24ef1c568f9d6fa84fdd49dac17581f71dfc466018929e045de43d58549c09b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210750"
---
# <a name="contributing-to-mrtk"></a>Mitwirken am MRTK

Das Mixed Reality Toolkit (MRTK) leistet Beiträge aus der Community. Alle Änderungen, ob klein oder groß, müssen den [MRTK-Codierungsstandards](coding-guidelines.md)entsprechen. Stellen Sie daher sicher, dass Sie mit diesen beim Entwickeln vertraut sind, um Verzögerungen bei der Überprüfung der Änderung zu vermeiden.

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

1. Forken Sie das Repository. Klicken Sie oben rechts auf der Seite auf die Schaltfläche "Fork", und folgen Sie dem Flow.
1. Erstellen Sie einen Branch in Ihrer [](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) Verzweigung (außerhalb des Hauptverzweigungs), um das Isolieren von Änderungen zu vereinfachen, bis sie zur Übermittlung bereit sind. Suchen Sie nach der neuesten Verzweigung, um Fehlerkorrekturen während einer Release-Stabilisierungsphase zu `prerelease/*` suchen. Neue Features sollten immer in aufgenommen `main` werden.

Wenn Sie noch keine Informationen zum Git-Workflow haben, [sehen Sie sich diese Einführung auf GitHub an.](https://guides.github.com/activities/hello-world/)

Führen Sie beim Hinzufügen einer Fehlerbehebung oder eines Features die folgenden Schritte aus:

1. Implementieren Sie die Fehlerbehebung oder das Feature. Anweisungen zum Erstellen und Bereitstellen von MRTK finden Sie unter [Deploying to Hololens and WMR devices (Bereitstellen auf Hololens- und WMR-Geräten).](../supported-devices/wmr-mrtk.md) Denken Sie daran, die [Codierungsrichtlinien](../contributing/coding-guidelines.md)zu befolgen.
1. Wenn Sie ein Feature hinzufügen, fügen Sie auch eine Beispielszene hinzu, die das Feature veranschaulicht.
1. Wenn Sie ein experimentelles Feature hinzufügen, sind das Schreiben von Tests und Dokumentationen nicht erforderlich. Befolgen Sie stattdessen [die Experimentellen Featurerichtlinien.](../contributing/experimental-features.md)
1. Fügen Sie Tests hinzu, um die Fehlerbehebung bzw. das Feature zu überprüfen. Anweisungen zum Schreiben und Ausführen von Tests finden Sie unter [UnitTests](../contributing/unit-tests.md).
1. Stellen Sie sicher, dass der Code und die Features wie in den [Dokumentationsrichtlinien](../contributing/documentation-guide.md)beschrieben dokumentiert sind.
1. Stellen Sie sicher, dass der Code auf allen Plattformen wie vorgesehen funktioniert. Die Liste der unterstützten Plattformen finden Sie in den [Versionshinweisen.](../release-notes/mrtk-26-release-notes.md) Für Windows UWP-Projekte muss Code [WACK-konform](https://developer.microsoft.com/windows/develop/app-certification-kit)sein. Generieren Sie hierzu eine Visual Studio Projektmappe, klicken Sie mit der rechten Maustaste auf das Projekt. **Store**  >  **Erstellen Sie App-Pakete.** Befolgen Sie die Anweisungen, und führen Sie WACK-Tests aus. Stellen Sie sicher, dass alle erfolgreich sind.
1. Befolgen Sie beim Erstellen eines Pull Requests die Anweisungen unter [Pull Requests.](../contributing/pull-requests.md)
