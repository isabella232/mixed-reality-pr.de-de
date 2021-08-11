---
title: Experimentelle Features
description: Dokument zu experimentellen Features im MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 9b7ef7564e0e4f84ba70c034b1bcc33a29498432620a002c8509de518dde479c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228385"
---
# <a name="experimental-features"></a>Experimentelle Features

Einige Features, an der das MRTK-Team arbeitet, scheinen einen großen Anfangswert zu haben, auch wenn wir die Details noch nicht vollständig ausgereift haben. Für diese Arten von Features soll die Community die Möglichkeit erhalten, sie frühzeitig zu sehen. Da sie sich zu einem frühen Zeitpunkt im Zyklus befinden, bezeichnen wir sie als experimentell, um anzugeben, dass sie sich noch weiterentwickeln und sich im Laufe der Zeit ändern können.

## <a name="what-to-expect-from-an-experimental-feature"></a>Was sie von einem experimentellen Feature erwarten können

Wenn eine Komponente als experimentell markiert ist, können Sie Folgendes erwarten:

- Eine Beispielszene, die die Verwendung veranschaulicht, die sich unter dem `MRTK/Examples/Experimental` Unterordner befindet
- Experimentelle Features verfügen möglicherweise nicht über Dokumente.
- Sie verfügen wahrscheinlich nicht über Tests.
- Experimentelle Features können sich ändern.

## <a name="experimental-feature-guidelines"></a>Richtlinien für experimentelle Features

### <a name="experimental-code-should-live-in-a-separate-folder"></a>Experimenteller Code sollte sich in einem separaten Ordner befinden.

Experimenteller Code sollte sich in einem experimentellen Ordner der obersten Ebene befinden, gefolgt vom Namen des experimentellen Features. Wenn Sie beispielsweise versuchen, ein neues Feature FooBar beizusteuern, geben Sie Code in Folgendes ein:

- Beispielszenen, in die Skripts eingehen `MRTK/Examples/Experimental/FooBar/`
- Komponentenskripts, prefabs go into (Komponentenskripts, Prefabs) `MRTK/SDK/Experimental/FooBar/`
- Komponenteninspektoren gehen in `MRTK/SDK/Inspectors/Experimental/FooBar`

Wenn Sie Unterordner unter dem Namen des experimentellen Features verwenden, versuchen Sie, die gleiche Ordnerstruktur von MRTK zu spiegeln.

Solver würden z. B. unter `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`

Behalten Sie Szenen in einem Szenenordner im oberen Bereich bei: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`

> [!NOTE]
> Es wurde davon ausgegangen, dass kein einzelner experimenteller Stammordner vorhanden ist und stattdessen Experimental unter `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` z. B. abgelegt wird. Wir haben uns entschieden, Ordner an der Basis zu nutzen, um die experimentellen Features einfacher zu ermitteln.

### <a name="experimental-code-should-be-in-a-special-namespace"></a>Experimenteller Code sollte sich in einem speziellen Namespace befinden.

Stellen Sie sicher, dass sich der experimentelle Code in einem experimentellen Namespace befindet, der dem nicht experimentellen Speicherort entspricht. Wenn Ihre Komponente beispielsweise Teil von Solvern unter `Microsoft.MixedReality.Toolkit.Utilities.Solvers` ist, sollte ihr Namespace `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` sein.

Ein Beispiel finden Sie [in diesem PR.](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532)

### <a name="experimental-features-should-have-an-experimental-attribute"></a>Experimentelle Features sollten über ein [experimentelles] Attribut verfügen.

Fügen Sie `[Experimental]` ein Attribut über einem Ihrer Felder hinzu, damit ein kleines Dialogfeld im Komponenten-Editor angezeigt wird, in dem erwähnt wird, dass Ihr Feature experimentell ist und erheblichen Änderungen unterliegt.

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a>Menüs für experimentelle Features sollten im Untermenü "Experimentell" angezeigt werden.

Stellen Sie sicher, dass sich experimentelle Features unter "experimentellen" Untermenüs befinden, wenn Sie Menüs im Editor Befehle hinzufügen. Hier sind einige Beispiele:

Hinzufügen eines Menübefehls der obersten Ebene:

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

Hinzufügen eines Komponentenmenüs:

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a>Dokumentation

Führen Sie die folgenden Schritte aus, um Dokumentation für Ihr experimentelles Feature hinzuzufügen:

1. Jede Dokumentation für ein experimentelles Feature sollte in einer `readme.md` Datei im experimentellen Ordner abgelegt werden. Beispiel: MRTK/SDK/Experimental/PulseShader/readme.md.

1. Fügen Sie unter *Featureübersichten* im Abschnitt *Experimentell* unter einen Link [`Documentation/toc.yml`](../toc.yml) hinzu.

### <a name="minimize-impact-to-mrtk-code"></a>Minimieren der Auswirkungen auf MRTK-Code

Ihre MRTK-Änderung kann zwar dazu bringen, dass Ihr Experiment funktioniert, dies kann sich jedoch auf andere Personen auswirken, die Sie nicht erwarten.
Alle Regressionen, die Sie am MRTK-Kerncode vornehmen, führen dazu, dass Ihr Pull Request zurückgesetzt wird.

Zielen Sie darauf ab, keine Änderungen in anderen Ordnern als experimentellen Ordnern vorzunehmen. Im Folgenden finden Sie eine Liste der Ordner, die experimentelle Änderungen aufweisen können:

- MRTK/SDK/Experimentell
- MRTK/SDK/Inspectors/Experimental
- MRTK/Examples/Experimental

Änderungen außerhalb dieser Ordner sollten sehr sorgfältig behandelt werden. Wenn Ihr experimentelles Feature Änderungen am MRTK-Kerncode enthalten muss, sollten Sie die MRTK-Änderungen in einen separaten Pull Request aufteilen, der Tests und Dokumentation enthält.

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a>Die Verwendung Ihres experimentellen Features sollte sich nicht auf die Fähigkeit von Personen auswirken, Kernsteuerelemente zu verwenden.

Die meisten Benutzer verwenden kernige UX-Komponenten wie die Schaltfläche, ManipulationHandler und Interactable sehr häufig. Sie verwenden ihr experimentelles Feature wahrscheinlich nicht, wenn es sie daran hindert, Schaltflächen zu verwenden.

Wenn Sie Ihre Komponente verwenden, sollten Sie schaltflächen, ManipulationHandler, BoundingBox oder interaktiv nicht unterbrechen.

Beispielsweise hat das Hinzufügen einer ScrollableObjectCollection in [diesem ScrollableObjectCollection-PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)dazu geführt, dass Benutzer die Prefabs der HoloLens Schaltfläche nicht verwenden konnten. Obwohl dies nicht durch einen Fehler im PR verursacht wurde (sondern stattdessen einen vorhandenen Fehler verfügbar gemacht hat), verhinderte dies, dass der PR eingecheckt wurde.

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a>Bereitstellen einer Beispielszene, die die Verwendung des Features veranschaulicht

Die Benutzer müssen wissen, wie Sie Ihr Feature verwenden und testen können.

Geben Sie unter MRTK/Examples/Experimental/YOUR_FEATURE ein Beispiel an.

### <a name="minimize-user-visible-flaws-in-experimental-features"></a>Minimieren sichtbarer Benutzerfehler in experimentellen Features

Andere verwenden das experimentelle Feature nicht, wenn es nicht funktioniert, es wird nicht zu einem Feature.

Testen Sie Ihre Beispielszene auf Ihrer Zielplattform, und stellen Sie sicher, dass sie wie erwartet funktioniert. Stellen Sie sicher, dass Ihr Feature auch im Editor funktioniert, damit Benutzer Ihr Feature schnell iterieren und anzeigen können, auch wenn sie nicht über die Zielplattform verfügen.

## <a name="graduating-experimental-code-into-mrtk-code"></a>Verzweigen von experimentellem Code in MRTK-Code

Wenn ein Feature am Ende sehr häufig verwendet wird, sollten wir es in kernen MRTK-Code umgliedern. Dazu sollte das Feature Tests, Dokumentation und eine Beispielszene enthalten.

Wenn Sie bereit sind, das Feature MRTK zu erstellen, erstellen Sie ein Problem, gegen das Sie Ihren PR überprüfen können. Der PR sollte alle Erforderlichen enthalten, um dies zu einem kernigen Feature zu machen: Tests, Dokumentation und eine Beispielszene für die Verwendung.

Vergessen Sie außerdem nicht, die Namespaces zu aktualisieren, um den Unterbereich "Experimentell" zu entfernen.
